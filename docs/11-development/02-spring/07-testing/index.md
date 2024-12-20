---
title: Spring Testing
parent: Spring Framework
grand_parent: Development
nav_order: 7
---

# Spring Testing
In Spring, unit tests aren’t required to load the Spring application context, and
they don’t rely on any Spring library. On the other hand, integration tests need a
Spring application context to run. 

## Unit tests
Unit tests are not aware of Spring and don’t rely on any Spring library. They are
intended to test the behavior of single components as isolated units. Any dependency
at the edge of the unit is mocked to keep the test shielded from external components.

Writing unit tests for Spring applications is no different from writing them for any
other Java application. By default, any Spring
project created from Spring Initializr contains the spring-boot-starter-test depen-
dency, which imports testing libraries like JUnit 5, Mockito, and AssertJ into the project. So we’re all set for writing unit tests.

## Integration tests
Integration tests cover the interactions among software components, and in Spring
they require an application context to be defined. The **spring-boot-starter-test**
dependency also imports the test utilities from Spring Framework and Spring Boot.

Integration tests need a Spring application context to run. A full application
context, including an optional embedded server, can be initialized for testing
using the @SpringBootTest annotation.

When tests are focused only on a “slice” of the application and only need a part of
the configuration, Spring Boot provides several annotations for more targeted
integration tests. When you use those annotations, a Spring application context is initialized, but only the components and configuration parts used by the
specific functionality slice are loaded.

* @WebMvcTest is for testing Spring MVC components.
* @JsonTest is for testing JSON serialization and deserialization.

### SpringBootTest
Spring Boot offers a **@SpringBootTest** annotation that you can use on a
test class to bootstrap an application context automatically when running tests. The
configuration used to create the context can be customized if needed. Otherwise, the
class annotated with @SpringBootApplication will become the configuration source
for component scanning and properties, including the usual auto-configuration pro-
vided by Spring Boot.

When working with web applications, you can run tests on 
* a mock web environment
* or a running server. You can configure that by defining a value for the webEnvironment attribute that the @SpringBootTest annotation provides

When using a mock web environment, you can rely on the **MockMvc** object to send
HTTP requests to the application and check their results. For environments with a
running server, the TestRestTemplate utility lets you perform REST calls to an application running on an actual server. By inspecting the HTTP responses, you can verify that he API works as intended.
|Web environment option| Description|
|:---------------------|:-----------|
|MOCK                  |Creates a web application context with a mock Servlet container. This is the default option.|
|RANDOM_PORT           | Creates a web application context with a Servlet container listening on a random port.|
|DEFINED_PORT          | Creates a web application context with a Servlet container listening on the port defined through the server.port property.|
|NONE                  | Creates an application context without a Servlet container.|
|                      |            |

// Loads a full Spring web application context and a Servlet container listening on a random port
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
class CatalogServiceApplicationTests {

	@Autowired
	private WebTestClient webTestClient;
}
```
### WebTestClient
You can use the **WebTestClient** class to test REST APIs
both on mock environments and running servers. Compared to MockMvc and
TestRestTemplate, WebTestClient provides a modern and fluent API and additional
features. Furthermore, you can use it for both imperative (e.g., Catalog Service) and
reactive applications, optimizing learning and productivity.

WebTestClient is part of the Spring WebFlux project, you’ll need to add a
new dependency in your project(org.springframework.boot:spring-boot-starter-webflux)
```java
@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
class CatalogServiceApplicationTests {

	@Autowired
	private WebTestClient webTestClient;

	@Test
	void whenGetRequestWithIdThenBookReturned() {
		var bookIsbn = "1231231230";
		var bookToCreate = new Book(bookIsbn, "Title", "Author", 9.90);
		Book expectedBook = webTestClient
				.post()
				.uri("/books")
				.bodyValue(bookToCreate)
				.exchange()
				.expectStatus().isCreated()
				.expectBody(Book.class).value(book -> assertThat(book).isNotNull())
				.returnResult().getResponseBody();

		webTestClient
				.get()
				.uri("/books/" + bookIsbn)
				.exchange()
				.expectStatus().is2xxSuccessful()
				.expectBody(Book.class).value(actualBook -> {
					assertThat(actualBook).isNotNull();
					assertThat(actualBook.isbn()).isEqualTo(expectedBook.isbn());
				});
	}
}
```
Test execution time matters, so Spring Boot is fully equipped to run integration tests by loading only the parts of the application that are needed. 

Some integration tests might not need a fully initialized application context. For example, there’s no need to load the web components when you’re testing the data persistence layer. If you’re testing the web components, you don’t need to load the data persistence layer.

Spring Boot allows you to use contexts initialized only with a subgroup of components (beans), targeting a specific application slice. Slice tests don’t use the @SpringBootTest annotation, but one of a set of annotations dedicated to particular parts of
an application: Web MVC, Web Flux, REST client, JDBC, JPA, Mongo, Redis, JSON,
and others. Each of those annotations initializes an application context, filtering out all the beans outside that slice.

### @WebMvcTest
We can test that Spring MVC controllers work as intended by using the @WebMvcTest annotation, which loads a Spring application context in a mock web environment (no running server), configures the Spring MVC infrastructure, and includes only the beans used by the MVC layer, like @RestController and @RestControllerAdvice. It’s also a good idea to limit the context to the beans used by the specific controller under test. We can do so by providing the controller class as an argument to the @WebMvcTest annotation in a new BookControllerMvcTests class.

**MockMvc** is a utility class that lets you test web endpoints without loading a server like Tomcat. Such a test is naturally lighter than the one in SpringBootTest, where an embedded server was needed to run the test.

Slice tests run against an application context containing only the parts of the configuration requested by that application slice. In the case of collaborating beans outside the slice, such as the BookService class, we use mocks.

Mocks created with the @MockBean annotation are different from standard mocks
(for example, those created with Mockito) since the class is not only mocked, but the mock is also included in the application context. Whenever the context is asked to autowire that bean, it automatically injects the mock rather than the actual implementation. 

```java
// Identifies a test class that focuses on Spring MVC components, explicitly targeting BookController
@WebMvcTest(BookController.class)
class BookControllerMvcTests {

    // Utility class to test the web layer in a mock environment
    @Autowired
    private MockMvc mockMvc;
    // Adds a mock of BookService to the Spring application context
    @MockBean
    private BookService bookService;

    @Test
    void whenGetBookNotExistingThenShouldReturn404() throws Exception {
        String isbn = "73737313940";

        // Defines the expected behavior for the BookService mock bean
        given(bookService.viewBookDetails(isbn))
                .willThrow(BookNotFoundException.class);

        // MockMvc is used to perform an HTTP GET request and verify the result.
        // and Expects the response to have a “404 Not Found” status
        mockMvc.perform(get("/books/" + isbn))
                .andExpect(status().isNotFound());
    }

}
```
### @JsonTest
Using the @JsonTest annotation, you can test JSON serialization and deserialization for your domain objects. @JsonTest loads a Spring application context and autoconfigures the JSON mappers for the specific library in use (by default, it’s Jackson).
Furthermore, it configures the JacksonTester utility, which you can use to check that the JSON mapping works as expected, relying on the JsonPath and JSONAssert libraries.
```java
// Identifies a test class that focuses on JSON serialization
@JsonTest
class BookJsonTests {

    // Utility class to assert JSON serialization and deserialization
    @Autowired
    private JacksonTester<Book> json;

    @Test
    void testSerialize() throws Exception {
        var book = new Book("1234567890", "Title", "Author", 9.90);
        var jsonContent = json.write(book);
        // Verifying the parsing from Java to JSON, using the JsonPath format to
        // navigate the JSON object
        assertThat(jsonContent).extractingJsonPathStringValue("@.isbn")
                .isEqualTo(book.isbn());
        assertThat(jsonContent).extractingJsonPathStringValue("@.title")
                .isEqualTo(book.title());
        assertThat(jsonContent).extractingJsonPathStringValue("@.author")
                .isEqualTo(book.author());
        assertThat(jsonContent).extractingJsonPathNumberValue("@.price")
                .isEqualTo(book.price());
    }

    @Test
    void testDeserialize() throws Exception {
        // Defines a JSON object using the Java text block feature
        var content = """
                {
                    "isbn": "1234567890",
                    "title": "Title",
                    "author": "Author",
                    "price": 9.90
                }
                """;
        // Verifies the parsing from JSON to Java
        assertThat(json.parse(content))
                .usingRecursiveComparison()
                .isEqualTo(new Book("1234567890", "Title", "Author", 9.90));
    }

}
```
### @DataJdbcTest
You can run integration tests for the Spring Data JDBC slice using the @DataJdbcTest annotation.
```java
@DataJdbcTest
@Import(DataConfig.class)
@AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
@ActiveProfiles("integration")
class BookRepositoryJdbcTests {

    @Autowired
    private BookRepository bookRepository;

    @Autowired
    private JdbcAggregateTemplate jdbcAggregateTemplate;

    @Test
    void findAllBooks() {
        var book1 = Book.of("1234561235", "Title", "Author", 12.90, "Polarsophia");
        var book2 = Book.of("1234561236", "Another Title", "Author", 12.90, "Polarsophia");
        jdbcAggregateTemplate.insert(book1);
        jdbcAggregateTemplate.insert(book2);

        Iterable<Book> actualBooks = bookRepository.findAll();

        assertThat(StreamSupport.stream(actualBooks.spliterator(), true)
                .filter(book -> book.isbn().equals(book1.isbn()) || book.isbn().equals(book2.isbn()))
                .collect(Collectors.toList())).hasSize(2);
    }

    @Test
}
```