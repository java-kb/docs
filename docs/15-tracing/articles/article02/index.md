---
title: Microservices Distributed Tracing Pattern Enhancing Visibility in Service Communication
parent: Tracing Articles
nav_order: 2
---
Microservices Distributed Tracing Pattern: Enhancing Visibility in Service Communication
========================================================================================
> source: https://java-design-patterns.com/patterns/microservices-distributed-tracing/

[Intent of Microservices Distributed Tracing Design Pattern](#intent-of-microservices-distributed-tracing-design-pattern)
-------------------------------------------------------------------------------------------------------------------------

Distributed tracing aims to monitor and track requests as they flow through different services in a microservices architecture, providing insights into performance, dependencies, and failures.

[Also known as](#also-known-as)
-------------------------------

*   Distributed Request Tracing
*   End-to-End Tracing

[Detailed Explanation of Microservices Distributed Tracing Pattern with Real-World Examples](#detailed-explanation-of-microservices-distributed-tracing-pattern-with-real-world-examples)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Real-world example

> In an e-commerce platform, distributed tracing is used to track a customer's request from the moment they add an item to the cart until the order is processed and shipped. This helps in identifying bottlenecks, errors, and latency issues across different services.

In plain words

> Distributed tracing allows you to follow a request's journey through all the services it interacts with, providing insights into system performance and aiding in debugging.

Wikipedia says

> Tracing in software engineering refers to the process of capturing and recording information about the execution of a software program. This information is typically used by programmers for debugging purposes, and additionally, depending on the type and detail of information contained in a trace log, by experienced system administrators or technical-support personnel and by software monitoring tools to diagnose common problems with software.

[Programmatic Example of Microservices Distributed Tracing in Java](#programmatic-example-of-microservices-distributed-tracing-in-java)
---------------------------------------------------------------------------------------------------------------------------------------

This implementation shows how an e-commerce platform's `OrderService` interacts with both `PaymentService` and `ProductService`. When a customer places an order, the `OrderService` calls the `PaymentService` to process the payment and the `ProductService` to check the product inventory. Distributed tracing logs are generated for each of these interactions and can be viewed in the Zipkin interface to monitor the flow and performance of requests across these services.

Here's the `Order microservice` implementation.

    @Slf4j
    @RestController
    public class OrderController {
    
        private final OrderService orderService;
    
        public OrderController(final OrderService orderService) {
            this.orderService = orderService;
        }
        
        @PostMapping("/order")
        public ResponseEntity<String> processOrder(@RequestBody(required = false) String request) {
            LOGGER.info("Received order request: {}", request);
            var result = orderService.processOrder();
            LOGGER.info("Order processed result: {}", result);
            return ResponseEntity.ok(result);
        }
    }

    @Slf4j
    @Service
    public class OrderService {
    
        private final RestTemplateBuilder restTemplateBuilder;
    
        public OrderService(final RestTemplateBuilder restTemplateBuilder) {
            this.restTemplateBuilder = restTemplateBuilder;
        }
    
        public String processOrder() {
            if (validateProduct() && processPayment()) {
                return "Order processed successfully";
            }
            return "Order processing failed";
        }
        
        Boolean validateProduct() {
            try {
                ResponseEntity<Boolean> productValidationResult = restTemplateBuilder
                        .build()
                        .postForEntity("http://localhost:30302/product/validate", "validating product",
                                Boolean.class);
                LOGGER.info("Product validation result: {}", productValidationResult.getBody());
                return productValidationResult.getBody();
            } catch (ResourceAccessException | HttpClientErrorException e) {
                LOGGER.error("Error communicating with product service: {}", e.getMessage());
                return false;
            }
        }
    
        Boolean processPayment() {
            try {
                ResponseEntity<Boolean> paymentProcessResult = restTemplateBuilder
                        .build()
                        .postForEntity("http://localhost:30301/payment/process", "processing payment",
                                Boolean.class);
                LOGGER.info("Payment processing result: {}", paymentProcessResult.getBody());
                return paymentProcessResult.getBody();
            } catch (ResourceAccessException | HttpClientErrorException e) {
                LOGGER.error("Error communicating with payment service: {}", e.getMessage());
                return false;
            }
        }
    }

Here's the `Payment microservice` implementation.

    
    @Slf4j
    @RestController
    public class PaymentController {
    
        @PostMapping("/payment/process")
        public ResponseEntity<Boolean> payment(@RequestBody(required = false) String request) {
            LOGGER.info("Received payment request: {}", request);
            boolean result = true;
            LOGGER.info("Payment result: {}", result);
            return ResponseEntity.ok(result);
        }
    }

Here's the `Product microservice` implementation.

    /**
     * Controller for handling product validation requests.
     */
    @Slf4j
    @RestController
    public class ProductController {
    
        /**
         * Validates the product based on the request.
         *
         * @param request the request body containing product information (can be null)
         * @return ResponseEntity containing the validation result (true)
         */
        @PostMapping("/product/validate")
        public ResponseEntity<Boolean> validateProduct(@RequestBody(required = false) String request) {
            LOGGER.info("Received product validation request: {}", request);
            boolean result = true;
            LOGGER.info("Product validation result: {}", result);
            return ResponseEntity.ok(result);
        }
    }

[When to Use the Microservices Distributed Tracing Pattern in Java](#when-to-use-the-microservices-distributed-tracing-pattern-in-java)
---------------------------------------------------------------------------------------------------------------------------------------

*   When you have a microservices architecture and need to monitor the flow of requests across multiple services.
*   When troubleshooting performance issues or errors in a distributed system.
*   When you need to gain insights into system bottlenecks and optimize overall performance.

[Microservices Distributed Tracing Pattern Java Tutorials](#microservices-distributed-tracing-pattern-java-tutorials)
---------------------------------------------------------------------------------------------------------------------

*   [Spring Boot - Tracing (Spring)](https://docs.spring.io/spring-boot/reference/actuator/tracing.html)
*   [Reactive Observability (Spring Academy)](https://spring.academy/guides/microservices-observability-reactive-spring-boot-3)
*   [Spring Cloud – Tracing Services with Zipkin (Baeldung)](https://dzone.com/articles/getting-started-with-spring-cloud-gateway)

[Benefits and Trade-offs of Microservices Distributed Tracing Pattern](#benefits-and-trade-offs-of-microservices-distributed-tracing-pattern)
---------------------------------------------------------------------------------------------------------------------------------------------

Benefits:

*   Provides end-to-end visibility into requests.
*   Helps in identifying performance bottlenecks.
*   Aids in debugging and troubleshooting complex systems.

Trade-offs:

*   Adds overhead to each request due to tracing data.
*   Requires additional infrastructure (e.g., Zipkin, Jaeger) for collecting and visualizing traces.
*   Can become complex to manage in large-scale systems.

[Real-World Applications of Microservices Distributed Tracing Pattern in Java](#real-world-applications-of-microservices-distributed-tracing-pattern-in-java)
-------------------------------------------------------------------------------------------------------------------------------------------------------------

*   Monitoring and troubleshooting e-commerce platforms.
*   Performance monitoring in financial transaction systems.
*   Observability in large-scale SaaS applications.

[Related Java Design Patterns](#related-java-design-patterns)
-------------------------------------------------------------

*   [Log Aggregation Microservice](https://java-design-patterns.com/patterns/microservices-log-aggregation/) - Distributed tracing works well in conjunction with log aggregation to provide comprehensive observability and troubleshooting capabilities.
*   [Circuit Breaker](https://java-design-patterns.com/patterns/circuit-breaker/) - Distributed tracing can be used alongside the Circuit Breaker pattern to monitor and handle failures gracefully, preventing cascading failures in microservices.
*   [API Gateway Microservice](https://java-design-patterns.com/patterns/microservices-api-gateway/) - The API Gateway pattern can be integrated with distributed tracing to provide a single entry point for tracing requests across multiple microservices.

[References and Credits](#references-and-credits)
-------------------------------------------------

*   [Building Microservices](https://amzn.to/3UACtrU)
*   [OpenTelemetry Documentation](https://opentelemetry.io/docs/)
*   [Distributed tracing (microservices.io)](https://microservices.io/patterns/observability/distributed-tracing.html)roservices Log Aggregation Pattern with Real-World Examples](#detailed-explanation-of-microservices-log-aggregation-pattern-with-real-world-examples)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Real-world example

> Imagine an e-commerce platform using a microservices architecture, where each service generates logs. A log aggregation system, utilizing tools like the ELK Stack (Elasticsearch, Logstash, Kibana), centralizes these logs. This setup allows administrators to effectively monitor and analyze the entire platform's activity in real-time. By collecting logs from each microservice and centralizing them, the system provides a unified view, enabling quick troubleshooting and comprehensive analysis of user behavior and system performance.

In plain words

> The Log Aggregation design pattern centralizes the collection and analysis of log data from multiple applications or services to simplify monitoring and troubleshooting.

Wikipedia says

> You have applied the Microservice architecture pattern. The application consists of multiple services and service instances that are running on multiple machines. Requests often span multiple service instances. Each service instance generates writes information about what it is doing to a log file in a standardized format. The log file contains errors, warnings, information and debug messages.

[Programmatic Example of Microservices Log Aggregation Pattern in Java](#programmatic-example-of-microservices-log-aggregation-pattern-in-java)
-----------------------------------------------------------------------------------------------------------------------------------------------

Log Aggregation is a pattern that centralizes the collection, storage, and analysis of logs from multiple sources to facilitate monitoring, debugging, and operational intelligence. It is particularly useful in distributed systems where logs from various components need to be centralized for better management and analysis.

In this example, we will demonstrate the Log Aggregation pattern using a simple Java application. The application consists of multiple services that generate logs. These logs are collected by a log aggregator and stored in a central log store.

The `CentralLogStore` is responsible for storing the logs collected from various services. In this example, we are using an in-memory store for simplicity.

    public class CentralLogStore {
    
      private final List<LogEntry> logs = new ArrayList<>();
    
      public void storeLog(LogEntry logEntry) {
        logs.add(logEntry);
      }
    
      public void displayLogs() {
        logs.forEach(System.out::println);
      }
    }

The `LogAggregator` collects logs from various services and stores them in the `CentralLogStore`. It filters logs based on their log level.

    public class LogAggregator {
    
      private final CentralLogStore centralLogStore;
      private final LogLevel minimumLogLevel;
    
      public LogAggregator(CentralLogStore centralLogStore, LogLevel minimumLogLevel) {
        this.centralLogStore = centralLogStore;
        this.minimumLogLevel = minimumLogLevel;
      }
    
      public void collectLog(LogEntry logEntry) {
        if (logEntry.getLogLevel().compareTo(minimumLogLevel) >= 0) {
          centralLogStore.storeLog(logEntry);
        }
      }
    }

The `LogProducer` represents a service that generates logs. It sends the logs to the `LogAggregator`.

    public class LogProducer {
    
      private final String serviceName;
      private final LogAggregator logAggregator;
    
      public LogProducer(String serviceName, LogAggregator logAggregator) {
        this.serviceName = serviceName;
        this.logAggregator = logAggregator;
      }
    
      public void generateLog(LogLevel logLevel, String message) {
        LogEntry logEntry = new LogEntry(serviceName, logLevel, message, LocalDateTime.now());
        logAggregator.collectLog(logEntry);
      }
    }

The `main` application creates services, generates logs, aggregates, and finally displays the logs.

    public class App {
    
      public static void main(String[] args) throws InterruptedException {
        final CentralLogStore centralLogStore = new CentralLogStore();
        final LogAggregator aggregator = new LogAggregator(centralLogStore, LogLevel.INFO);
    
        final LogProducer serviceA = new LogProducer("ServiceA", aggregator);
        final LogProducer serviceB = new LogProducer("ServiceB", aggregator);
    
        serviceA.generateLog(LogLevel.INFO, "This is an INFO log from ServiceA");
        serviceB.generateLog(LogLevel.ERROR, "This is an ERROR log from ServiceB");
        serviceA.generateLog(LogLevel.DEBUG, "This is a DEBUG log from ServiceA");
    
        centralLogStore.displayLogs();
      }
    }

In this example, the `LogProducer` services generate logs of different levels. The `LogAggregator` collects these logs and stores them in the `CentralLogStore` if they meet the minimum log level requirement. Finally, the logs are displayed by the `CentralLogStore`.

[When to Use the Microservices Log Aggregation Pattern in Java](#when-to-use-the-microservices-log-aggregation-pattern-in-java)
-------------------------------------------------------------------------------------------------------------------------------

*   Microservices log aggregation is essential in distributed systems for better management and analysis of log data.
*   Applicable in environments where compliance and auditing require consolidated log data.
*   Beneficial in systems that require high availability and resilience, ensuring that log data is preserved and accessible despite individual component failures.

[Real-World Applications of Microservices Log Aggregation Pattern in Java](#real-world-applications-of-microservices-log-aggregation-pattern-in-java)
-----------------------------------------------------------------------------------------------------------------------------------------------------

*   ava applications using frameworks like Log4j2 or SLF4J with centralized log management tools such as the ELK stack or Splunk benefit from microservices log aggregation.
*   Microservices architectures where each service outputs logs that are aggregated into a single system to provide a unified view of the system’s health and behavior.

[Benefits and Trade-offs of Microservices Log Aggregation Pattern](#benefits-and-trade-offs-of-microservices-log-aggregation-pattern)
-------------------------------------------------------------------------------------------------------------------------------------

Benefits:

*   Centralizing logs in a microservices environment improves debuggability and traceability across multiple services.
*   Enhances monitoring capabilities by providing a centralized platform for log analysis.
*   Facilitates compliance with regulatory requirements for log retention and auditability.

Trade-offs:

*   Introduces a potential single point of failure if the log aggregation system is not adequately resilient.
*   Can lead to high data volumes requiring significant storage and processing resources.

[Related Java Design Patterns](#related-java-design-patterns)
-------------------------------------------------------------

*   Messaging Patterns: Log Aggregation often utilizes messaging systems to transport log data, facilitating decoupling and asynchronous data processing.
*   Microservices: Often employed in microservice architectures to handle logs from various services efficiently.
*   Publish/Subscribe: Utilizes a pub/sub model for log data collection where components publish logs and the aggregation system subscribes to them.

[References and Credits](#references-and-credits)
-------------------------------------------------

*   [Cloud Native Java: Designing Resilient Systems with Spring Boot, Spring Cloud, and Cloud Foundry](https://amzn.to/44vDTat)
*   [Logging in Action: With Fluentd, Kubernetes and more](https://amzn.to/3JQLzdT)
*   [Release It! Design and Deploy Production-Ready Software](https://amzn.to/3Uul4kF)
*   [Pattern: Log aggregation (microservices.io)](https://microservices.io/patterns/observability/application-logging.html)
