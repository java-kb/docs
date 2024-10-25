---
title: Control Flow
parent: Java Interview
nav_order: 1
---

# Control Flow
1. **What will be the result of attempting to compile and run the following class?**{: .label-red }

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


    {: .answer }
    >  (d) 
    > 
    > The program will display the letter b when run. The second if statement is evaluated since the boolean expression of the first if statement is true. The else clause belongs to the second if statement. Since the boolean expression of the second if statement is false, the if block is skipped and the else clause is executed.

2. **What will be the result of attempting to compile and run the following program?**{: .label-red }
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

    {: .answer }
    > (c)  
    > 
    > The case label value 2 * iLoc is a constant expression whose value is 6, the same
    > as the switch expression. Fall-through results in the program output shown in (c).


3. **Which code option will print the string "Prime"?**{: .label-red }

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
    {: .answer }
    > (c)    
    > 
    > (a) contains a switch statement. Note that there is no break statement associated with the first case label, thus execution falls through to the second case label and assigns the string "Composite" to the reference result, which is then printed. 
    > 
    > (b) uses a switch expression to yield a result. However, it does not provide an exhaustive set of case labels and will fail to compile without the default label. 
    >
    > (c) uses the identifier yield as both a variable name and a contextual keyword in the yield statement. There is no fall-through, and the switch expression yields the string "Prime" which is printed.
    >
    > (d) is mixing two different types of notations for the switch constructs: the arrow notation and the colon notation, which is not permitted.

1. **Given the following code:**{: .label-red }

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

    {: .answer }
    > (a)
    >
    > The value 1 of the price variable matches the case constant 1 in the first case label,and in this case the discount is calculated by subtracting 1 from the value of price,which results in the value of 0. This code uses a switch expression with the arrow notation, so no fall-through to the next case label can occur. Case labels do not need to be listed in any particular order. The switch expression is exhaustive, because the case labels and the default label cover the range of int values. Code will compile and when executed will yield the value 0.