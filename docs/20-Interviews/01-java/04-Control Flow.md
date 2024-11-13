---
title: Control Flow
parent: Java Interview
nav_order: 4
---

# Control Flow

1. **What will be the result of attempting to compile and run the following class?**{: .label .label-red }

    ```java
    public class IfTest {
        public static void main(String[] args) {
            if (true)
            if (false)
            System.out.println("a");
            else
            System.out.println("b");
        }
    }
    ```

    Select the one correct answer.

    (a) The code will fail to compile because the syntax of the if statement is
    incorrect.

    (b) The code will fail to compile because the compiler will not be able to determine which if statement the else clause belongs to.

    (c) The code will compile correctly and will display the letter a at runtime.

    (d) The code will compile correctly and will display the letter b at runtime.

    (e) The code will compile correctly but will not display any output.

    <details markdown="block">
    <summary>Answer</summary>
    (d) 
    
    The program will display the letter b when run. The second if statement is evaluated since the boolean expression of the first if statement is true. The else clause belongs to the second if statement. Since the boolean expression of the second if statement is false, the if block is skipped and the else clause is executed.

1. **What will be the result of attempting to compile and run the following program?**{: .label .label-red }
    ```java
    public class Switching {
    public static void main(String[] args) {
    final int iLoc = 3;
    switch (6) {
    case 1:
    case iLoc:
    case 2 * iLoc:
    System.out.println("I am not OK.");
    default:
    System.out.println("You are OK.");
    case 4:
    System.out.println("It's OK.");
    }
    }
    }
    ```
    Select the one correct answer.

    (a) The code will fail to compile because of the case label value 2 * iLoc.

    (b) The code will fail to compile because the default label is not specified last in the switch statement.

    (c) The code will compile correctly and will print the following at runtime:

    I am not OK.

    You are OK.

    It's OK.

    d) The code will compile correctly and will print the following at runtime:

    You are OK.

    It's OK.

    (e) The code will compile correctly and will print the following at runtime:

    It's OK.
    <details markdown="block">
    <summary>Answer</summary>
    (c)  
    
    The case label value 2 * iLoc is a constant expression whose value is 6, the same
    as the switch expression. Fall-through results in the program output shown in (c).


1. **Which code option will print the string "Prime"?**{: .label .label-red }

    Select the one correct answer.

    (a) 
   ```java
    char value = 3;
    String result = "Unknown";
    switch (value) {
    case 2,3,5,7: result = "Prime";
    case 1,4,6,8,9: result = "Composite";
    }
    System.out.println(result);
   ```

    (b) 
    ```java
    char value = 3;
    String result =
    switch (value) {
    case 2,3,5,7: yield "Prime";
    case 1,4,6,8,9: yield "Composite";
    };
    System.out.println(result);
    ```

    (c) 
    ```java
    char value = 3;
    String yield =
    switch (value) {
    case 2,3,5,7: yield "Prime";
    case 1,4,6,8,9: yield "Composite";
    default: yield "Unknown";
    };
    System.out.println(yield);
    ```

    (d) 
    ```java
    char value = 3;
    String result =
    switch (value) {
    case 2,3,5,7 -> "Prime";
    case 1,4,6,8,9 -> "Composite";
    default: { yield "Unknown"; }
    };
    System.out.println(result);
    ```
    <details markdown="block">
    <summary>Answer</summary>
    (c)    
    
    (a) contains a switch statement. Note that there is no break statement associated with the first case label, thus execution falls through to the second case label and assigns the string "Composite" to the reference result, which is then printed. 
    
    (b) uses a switch expression to yield a result. However, it does not provide an exhaustive set of case labels and will fail to compile without the default label. 
    >
    (c) uses the identifier yield as both a variable name and a contextual keyword in the yield statement. There is no fall-through, and the switch expression yields the string "Prime" which is printed.
    >
    (d) is mixing two different types of notations for the switch constructs: the arrow notation and the colon notation, which is not permitted.

    </details>
1. **Given the following code:**{: .label .label-red }

    ```java
    public class RQ462 {
    public static void main(String[] args) {
    int price = 1;
    int discount = switch (price) {
    case 5, 1, 2 -> price - 1;
    case 4, 3, 6 -> price - 2;
    default -> 0;
    };
    System.out.println(discount);
    }
    }
    ```
    What is the result?

    Select the one correct answer.

    (a) 0

    (b) 1

    (c) -1

    (d) -2

    (e) The program will throw an exception at runtime.

    (f) The program will fail to compile.
    <details markdown="block">
    <summary>Answer</summary>
    (a)

    The value 1 of the price variable matches the case constant 1 in the first case label,and in this case the discount is calculated by subtracting 1 from the value of price,which results in the value of 0. This code uses a switch expression with the arrow notation, so no fall-through to the next case label can occur. Case labels do not need to be listed in any particular order. The switch expression is exhaustive, because the case labels and the default label cover the range of int values. Code will compile and when executed will yield the value 0.

    </details>
2. **What will be the result of attempting to compile and run the following code?**{: .label .label-red }
    ```java
    class MyClass {
    public static void main(String[] args) {
    boolean b = false;
    int i = 1;
    do {
    i++;
    b = ! b;
    } while (b);
    System.out.println(i);
    }
    }
    ```
    Select the one correct answer.

    (a) The code will fail to compile because b is an invalid condition for the do-while statement.

    (b) The code will fail to compile because the assignment b = ! b is not allowed.

    (c) The code will compile without error and will print 1 at runtime.

    (d) The code will compile without error and will print 2 at runtime.

    (e) The code will compile without error and will print 3 at runtime.
    <details markdown="block">
    <summary>Answer</summary>
    (e)
    
    The loop body is executed twice and the program will print 3. The first time the
    loop is executed, the variable i changes value from 1 to 2 and the variable b changes
    value from false to true. Then the loop condition is evaluated. Since b is true, the
    loop body is executed again. This time the variable i changes value from 2 to 3 and
    the variable b changes value from true to false. The loop condition is now evaluated
    again. Since b is now false, the loop terminates and the current value of i is printed.

    </details>
3. **What will be the output when running the following program?**{: .label .label-red }
    ```java
    public class StillMyClass {
    public static void main(String[] args) {
    int i = 0;
    int j;
    for (j = 0; j < 10; ++j) { i++; }
    System.out.println(i + " " + j);
    }
    }
    ```
    Select the two correct answers.

    (a) The first number printed will be 9.

    (b) The first number printed will be 10.

    (c) The first number printed will be 11.

    (d) The second number printed will be 9.

    (e) The second number printed will be 10.

    (f) The second number printed will be 11.
    <details markdown="block">
    <summary>Answer</summary>
    (b) and (e)

    Both the first and the second numbers printed will be 10. Both the loop body and
    the update expression will be executed exactly 10 times. Each execution of the loop
    body will be directly followed by an execution of the update expression. After-
    wards, the condition j < 10 is evaluated to see whether the loop body should be
    executed again.
    </details>
4. **What will be the result of attempting to compile and run the following program?**{: .label .label-red }
    ```java
        class AnotherClass {
        public static void main(String[] args) {
        int i = 0;
        for (; i < 10; i++) ; // (1)
        for (i = 0;; i++) break; // (2)
        for (i = 0; i < 10;) i++; // (3)
        for (;;) ; // (4)
        }
        }
    ```
    Select the one correct answer.

    (a) The code will fail to compile because of errors in the for loop at (1).

    (b) The code will fail to compile because of errors in the for loop at (2).

    (c) The code will fail to compile because of errors in the for loop at (3).

    (d) The code will fail to compile because of errors in the for loop at (4).

    (e) The code will compile without error, and the program will run and terminate
    without any output.

    (f) The code will compile without error, but will never terminate when run.
    <details markdown="block">
    <summary>Answer</summary>
    (f) 

    The code will compile without error, but will never terminate when run. All the
    sections in the for header are optional and can be omitted (but not the semicolons).
    An omitted loop condition is interpreted as being true. Thus a for(;;) loop with
    an omitted loop condition will never terminate, unless an appropriate control
    transfer statement is encountered in the loop body. The program will enter an infi-
    nite loop at (4).
    </details>
5. **Given the following code fragment, which of the following lines will be a part of the output?**{: .label .label-red }
    ```java
    outer:
    for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 2; j++) {
    if (i == j) {
    continue outer;
    }
    System.out.println("i=" + i + ", j=" + j);
    }
    }
    ```
    Select the two correct answers.

    (a) i=1, j=0

    (b) i=0, j=1

    (c) i=1, j=2

    (d) i=2, j=1

    (e) i=2, j=2

    (f) i=3, j=3

    (g) i=3, j=2
    <details markdown="block">
    <summary>Answer</summary>
    (a) and (d)

    "i=1, j=0" and "i=2, j=1" are part of the output. The variable i iterates through the values 0, 1, and 2 in the outer loop, while j toggles between the values 0 and 1 in the inner loop. If the values of i and j are equal, the printing of the values is
    skipped and the execution continues with the next iteration of the outer loop. The
    following can be deduced when the program is run: variables i and j are both 0
    and the execution continues with the update expression of the outer loop. "i=1,
    j=0" is printed and the next iteration of the inner loop starts. Variables i and j are
    both 1 and the execution continues with the update expression of the outer loop.
    "i=2, j=0" is printed and the next iteration of the inner loop starts. "i=2, j=1" is
    printed, j is incremented, j < 2 is false, and the inner loop ends. Variable i is incremented, i < 3 is false, and the outer loop ends.

    </details>
6. **Which declarations, when inserted at (1), will result in the program compiling and printing 90 at runtime?**{: .label .label-red }
   ```java
    public class RQ400A10 {
    public static void main(String[] args) {
    // (1) INSERT DECLARATION HERE
    int sum = 0;
    for (int i : nums)
    sum += i;
    System.out.println(sum);
    }
    }
   ```
    Select the two correct answers.
    
    (a) Object[] nums = {20, 30, 40};
    
    (b) Number[] nums = {20, 30, 40};
    
    (c) Integer[] nums = {20, 30, 40};
    
    (d) int[] nums = {20, 30, 40};
    
    (e) None of the above
    <details markdown="block">
    <summary>Answer</summary>
    (c) and (d) 

    The element type of the array nums must be assignment compatible with the type
    of the loop variable (i.e., int). Only the element type in (c), Integer, can be automatically unboxed to an int. The element type in (d) is int.

    </details>
7. **Which method declarations, when inserted at (1), will result in the program compiling and printing 90 when run?**{: .label .label-red }
    ```java
    public class RQ400A30 {
    public static void main(String[] args) {
    doIt();
    }
    // (1) INSERT METHOD DECLARATION HERE
    }
    ```
    Select the two correct answers.
    
    (a)  
    ```java
    public static void doIt() {
    int[] nums = {20, 30, 40};
    for (int sum = 0, i : nums)
    sum += i;
    System.out.println(sum);
    }
    ```
    (b)  
    ```java
    public static void doIt() {
    for (int sum = 0, i : {20, 30, 40})
    sum += i;
    System.out.println(sum);
    }
    ```
    
    (c)  
    ```java
    public static void doIt() {
    int sum = 0;
    for (int i : {20, 30, 40})
    sum += i;
    System.out.println(sum);
    }
    ```
    
    (d)  
    ```java
    public static void doIt() {
    int sum = 0;
    for (int i : new int[] {20, 30, 40})
    sum += i;
    System.out.println(sum);
    }
    ```
    
    (e) 
    ```java
    public static void doIt() {
    int[] nums = {20, 30, 40};
    int sum = 0;
    for (int i : nums)
    sum += i;
    System.out.println(sum);
    }
    ```
    <details markdown="block">
    <summary>Answer</summary>
    (d) and (e)

    In the header of a for(:) loop, we can only declare one local variable. This rules out (a) and (b), as they specify two local variables. Also, the array expression in (a), (b), and (c) is not valid. Only (d) and (e) specify a legal for(:) header. 

    </details>
8. **Which of the following statements are true about the following for(:) loop?**{: .label .label-red }
    for (type variable : expression) statement

    Select the three correct answers.

    (a) The variable is only accessible in the for(:) loop body.

    (b) The expression is only evaluated once.

    (c) The type of the expression must be java.lang.Iterable<E> or an array type.

    (d) Changing the value of the variable in the loop body affects the data structure
    represented by the expression.

    (e) The loop runs backward if the expression is negated as follows: !expression.

    (f) We can iterate over several data structures simultaneously in a for(:) loop.
    <details markdown="block">
    <summary>Answer</summary>
    (a), (b), and (c) 

    Changing the value of the variable does not affect the data structure being iterated
    over. The for(:) loop cannot run backwards. We cannot iterate over several data
    structures simultaneously in a for(:) loop, as the syntax does not allow it.
    </details>