---
title: Basic Elements, Primitive Data Types, and Operators
parent: Java Interview
nav_order: 1
---

# Basic Elements, Primitive Data Types, and Operators

1. **Which of the following is not a legal comment in Java?Select the one correct answer.**{: .label .label-red }

   (a) /* // */

   (b) /* */ //

   (c) // /* */

   (d) /* /* */

   (e) /* /* */ */

   (f) // //


    <details markdown="block">
    <summary>Answer</summary>
    (e) 
    
    Everything from the start sequence (/*) of a multiple-line comment to the first occurrence of the end sequence (*/) of a multiple-line comment is ignored by the compiler. 
    
    Everything from the start sequence (//) of a single-line comment to the
    end of the line is ignored by the compiler. 
    
    In (e), the multiple-line comment ends with the first occurrence of the end sequence (*/), leaving the second occurrence of the end sequence (*/) unmatched.
    </details>
2. **What will be the result of compiling and running the following program?**{: .label .label-red }
   
    ```java
    public class Assignment {
    public static void main(String[] args) {
    int a, b, c;
    b = 10;
    a = b = c = 20;
    System.out.println(a);
    }
    }
    ```
    Select the one correct answer.
    
    (a) The code will fail to compile because the compiler will report that the variable
    c in the multiple assignment statement a = b = c = 20; has not been
    initialized.

    (b) The code will fail to compile because the multiple assignment statement a = b
    = c = 20; is illegal.

    (c) The code will compile and print 10 at runtime.

    (d) The code will compile and print 20 at runtime.


    <details markdown="block">
    <summary>Answer</summary>
    (d) 
    
    An assignment statement is an expression statement. The value of the expression statement is the value of the expression on the right-hand side. Since the assignment operator is right associative, the statement a = b = c = 20 is evaluated as follows:
     
    (a = (b = (c = 20))). This results in the value 20 being assigned to c, then the same value being assigned to b and finally to a. The program will compile and print 20 at runtime.
    
    </details>
3. **What will be the result of compiling and running the following program?**{: .label .label-red }
   ```java
    public class MyClass {
    public static void main(String[] args) {
    String a, b, c;
    c = new String("mouse");
    a = new String("cat");
    b = a;
    a = new String("dog");
    c = b;
    System.out.println(c);
    }
    }
   ```
    Select the one correct answer.

    (a) The program will fail to compile.

    (b) The program will print mouse at runtime.

    (c) The program will print cat at runtime.

    (d) The program will print dog at runtime.

    (e) The program will randomly print either cat or dog at runtime.


    <details markdown="block">
    <summary>Answer</summary>
    (c) 
    
    In an assignment statement, the reference value of the source reference is assigned
    to the destination reference. Assignment does not create a copy of the object
    denoted by the source reference. After the assignment, both references denote the
    same object—that is, they are aliases.
    The variables a, b, and c are references of type String. The reference value of the
    "cat" object is first assigned to a, then to b, and later to c. Just before the print state-
    ment, a denotes "dog", whereas both b and c denote "cat". The program prints > the
    string denoted by c—that is, "cat".    </details>
4. **Which of the following expressions evaluate to a floating-point value?**{: .label .label-red }
    
    Select the three correct answers.

    (a) 2.0 * 3

    (b) 2 * 3

    (c) 2/3 + 5/7

    (d) 2.4 + 1.6

    (e) 0x10 * 1L * 300.0

    <details markdown="block">
    <summary>Answer</summary>
    (a), (d), and (e)
    
    A binary expression with any floating-point operand will be evaluated using
    floating-point arithmetic. Expressions such as 2/3, where both operands are inte-
    gers, will use integer arithmetic and evaluate to an integer value. In (e), the result
    of (0x10 * 1L) is promoted to a floating-point value.
   
    </details>
5. **What is the value of the expression (1 / 2 + 3 / 2 + 0.1)?**{: .label .label-red }
    
    Select the one correct answer.

    (a) 1

    (b) 1.1

    (c) 1.6

    (d) 2

    (e) 2.1
    <details markdown="block">
    <summary>Answer</summary>
    (b)
    
    The / operator has higher precedence than the + operator. This means that the expression is evaluated as ((1/2) + (3/2) + 0.1). The associativity of the binary operators is from left to right, giving (((1/2) + (3/2)) + 0.1). Integer division results in ((0 + 1) + 0.1), which evaluates to 1.1.
    </details>
6. **What is the value of evaluating the following expression: (- -1-3 * 10 / 5-1)?**{: .label .label-red }
    
    Select the one correct answer.

    (a) –8

    (b) –6

    (c) 7

    (d) 8

    (e) 10

    (f) None of the above

    <details markdown="block">
    <summary>Answer</summary>
    (b)
    The expression evaluates to -6. The whole expression is evaluated as (((-(-1)) -
    ((3 * 10) / 5)) - 1) according to the precedence and associativity rules.
    </details>
7. **What is the result of compiling and running the following program?**{: .label .label-red }
   ```java
    public class Prog1 {
    public static void main(String[] args) {
    int k = 1;
    int i = ++k + k++ + + k; // (1)
    System.out.println(i);
    }
    }
   ```
    Select the one correct answer.

    (a) The program will fail to compile because of errors in the expression at (1).

    (b) The program will print the value 3 at runtime.

    (c) The program will print the value 4 at runtime.

    (d) The program will print the value 7 at runtime.

    (e) The program will print the value 8 at runtime.

    <details markdown="block">
    <summary>Answer</summary>
    (d) 
    
    The expression ++k + k++ + + k is evaluated as ((++k) + (k++)) + (+k) → ((2) +(2) + (3)), resulting in the value 7.
    </details>
8. **Which is the first line that will cause a compile-time error in the following program?**{: .label .label-red }
    ```java
    public class MyClass {
    public static void main(String[] args) {
    char c;
    int i;
    c = 'a'; // (1)
    i = c; // (2)
    i++; // (3)
    c = i; // (4)
    c++; // (5)
    }
    }
    ```
    Select the one correct answer.

    (a) (1)

    (b) (2)

    (c) (3)

    (d) (4)

    (e) (5)

    (f) None of the above. The compiler will not report any errors.

    <details markdown="block">
    <summary>Answer</summary>
    (d) 
    
    The types char and int are both integral. A char value can be assigned to an int variable since the int type is wider than the char type and an implicit widening conversion will be done. An int type cannot be assigned to a char variable because the char type is narrower than the int type. The compiler will report an error about a possible loss of precision at (4).
    </details>
9. **What will be the result of compiling and running the following program?**{: .label .label-red }
    ```java
    public class EvaluationOrder {
    public static void main(String[] args) {
    int[] array = { 4, 8, 16 };
    int i = 1;
    array[++i] = --i;
    System.out.println(array[0] + array[1] + array[2]);
    }
    }
    ```
    Select the one correct answer.

    (a) 13

    (b) 14

    (c) 20

    (d) 21

    (e) 24

    <details markdown="block">
    <summary>Answer</summary>
    (a) 
    First, the expression ++i is evaluated, resulting in the value 2. Now the variable i also has the value 2. The target of the assignment is now determined to be the element array[2]. Evaluation of the right-hand expression, --i, results in the value 1.
    
    The variable i now has the value 1. The value of the right-hand expression 1 is then assigned to the array element array[2], resulting in the array contents to become {4, 8, 1}. The program computes and prints the sum of these values—that is, 13.
    </details>
10. **Which of the following statements are true?**{: .label .label-red }
    
    Select the two correct answers.

    (a) The remainder operator % can be used only with integral operands.
    
    (b) Short-circuit evaluation occurs with boolean logical operators.
    
    (c) The arithmetic operators *, /, and % have the same level of precedence.
    
    (d) A short value ranges from -128 to +127, inclusive.
    
    (e) (+15) is a legal expression.

    <details markdown="block">
    <summary>Answer</summary>
    (c) and (e) 
    
    The remainder operator is not limited to integral values, but can also be applied to floating-point operands. Short-circuit evaluation occurs with the conditional operators (&&, \|\|). The operators *, /, and % have the same level of precedence. The data type short is a 16-bit signed two’s complement integer, thus the range of values is from -32768 to +32767, inclusive. (+15) is a legal expression using the unary + operator.
    </details>
11. **Which of the following statements are true about the lines of output printed by the following program?**{: .label .label-red }
    ```java
    public class BoolOp {
    static void op(boolean a, boolean b) {
    boolean c = a != b;
    boolean d = a ^ b;
    boolean e = c == d;
    System.out.println(e);
    }
    public static void main(String[] args) {
    op(false, false);
    op(true, false);
    op(false, true);
    op(true, true);
    }
    }
    ```
    Select the three correct answers.
    
    (a) All lines printed are the same.
    
    (b) At least one line contains false.
    
    (c) At least one line contains true.
    
    (d) The first line contains false.
    
    (e) The last line contains true.

    <details markdown="block">
    <summary>Answer</summary>
    (a), (c), and (e)
    
    The != and ^ operators, when used on boolean operands, will return true if and only if one operand is true, and false otherwise. This means that d and e in the program will always be assigned the same value, given any combination of truth values in a and b. The program will, therefore, print true four times.    </details>
12. **What is the result of running the following program?**{: .label .label-red }
   ```java
    public class OperandOrder {
    public static void main(String[] args) {
    int i = 0;
    int[] a = {3, 6};
    a[i] = i = 9;
    System.out.println(i + " " + a[0] + " " + a[1]);
    }
    }
   ```
    Select the one correct answer.
    
    (a) When run, the program throws an ArrayIndexOutOfBoundsException.
    
    (b) When run, the program will print 9 9 6.
    
    (c) When run, the program will print 9 0 6.
    
    (d) When run, the program will print 9 3 6.
    
    (e) When run, the program will print 9 3 9.

    <details markdown="block">
    <summary>Answer</summary>
    (b) 
    
    The element referenced by a[i] is determined based on the current value of i,which is 0—that is, the element a[0]. The expression i = 9 will evaluate to the value 9, which will be assigned to the variable i. The value 9 is also assigned to the array element a[0]. After execution of the statement, the variable i will contain the value 9, and the array a will contain the values 9 and 6. The program will print 996 when run.    </details>
13. **Which of the following statements are true about the output from the following program?**{: .label .label-red }
   ```java
    public class Logic {
    public static void main(String[] args) {
    int i = 0;
    int j = 0;
    boolean t = true;
    boolean r;
    r = (t & 0 < (i+=1));
    r = (t && 0 < (i+=2));
    r = (t | 0 < (j+=1));
    r = (t || 0 < (j+=2));
    System.out.println(i + " " + j);
    }
    }
   ```
    Select the two correct answers.
    
    (a) The first digit printed is 1.
    
    (b) The first digit printed is 2.
    
    (c) The first digit printed is 3.
    
    (d) The second digit printed is 1.
    
    (e) The second digit printed is 2.
    
    (f) The second digit printed is 3.

    <details markdown="block">
    <summary>Answer</summary>
    (c) and (d) 
    
    Note that the logical and conditional operators have lower precedence than the relational operators. Unlike the & and \| operators, the && and \|\| operators shortcircuit the evaluation of their operands if the result of the operation can be determined from the value of the first operand. The second operand of the \|\| operator in the program is never evaluated because the value of t remains true. All the operands of the other operators are evaluated. Variable i ends up with the value 3, which is the first digit printed, and j ends up with the value 1, which is the second digit printed.    </details>
14. **Given the following code:**{: .label .label-red }
    ```java
    int x = 1, y = 2, z = 3;
    if (x < y || ++z > 4) {
    System.out.println("a" + x + y + z);
    }
    if (x < y && ++z > 4) {
    System.out.println("b" + x + y + z);
    }
    ```
    What will be the output? Select the one correct answer.
    
    (a) a124
        b125
    
    (b) a123
    
    (c) a123
        b124

    <details markdown="block">
    <summary>Answer</summary>
    (b)
    
    Both \|\| and && are short-circuit conditional operators. In the conditional expression (x < y \|\| ++z > 4) of the first if statement, since the first operand x < y evaluates to true, the second operand ++z > 4 is not evaluated, as the conditional operator is \|\|. The if condition is true and the if block is executed, printing a123. 
    
    In the conditional expression (x < y \|\| ++z > 4) of the second if statement, since the first operand x < y evaluates to true, the second operand ++z > 4 is evaluated, as the conditional operator is &&. The second operand is false (4 > 4); therefore, the if condition is false and the if block is not executed.    </details>
15. **Which of the following statements when inserted at (1) will not result in a compile-time error?**{: .label .label-red }
   ```java
    public class RQ05A200 {
    public static void main(String[] args) {
    int i = 20;
    int j = 30;
    // (1) INSERT STATEMENT HERE
    }
    }
   ```
    Select the three correct answers.
    
    (a) int result1 = i < j ? i : j * 10d;
    
    (b) int result2 = i < j ? { ++i } : { ++j };
    
    (c) Number number = i < j ? i : j * 10D;
    
    (d) System.out.println(i < j ? i);
    
    (e) System.out.println(i < j ? ++i : ++j);
    
    (f) System.out.println(i == j ? i == j : "i not equal to j");

    <details markdown="block">
    <summary>Answer</summary>
    (c), (e), and (f)
    
    In (a), the third operand has the type double, which is not assignment compatible with the type int of the variable result1. Blocks are not legal operands in the conditional operator, as in (b). In (c), the last two operands result in wrapper objects with type Integer and Double, respectively, which are assignment compatible with the type Number of the variable number. The evaluation of the conditional expression results in the reference value of an Integer object with value 20 being assigned to the number variable. All three operands of the operator are mandatory, which is not the case in (d). In (e), the last two operands are of type int, and the evaluation of the conditional expression results in an int value (21), whose text representation is printed. In (f), the value of the second operand is boxed into a Boolean. The evaluation of the conditional expression results in a string literal ("i not equal to j"),which is printed. The println() method creates and prints a text representation of any object whose reference value is passed as a parameter.    </details>
16. **Which of the following statements are true about the following code?**{: .label .label-red }
   ```java
    public class RQ05A100 {
    public static void main(String[] args) {
    int n1 = 10, n2 = 10;
    int m1 = 20, m2 = 30;
    int result = n1 != n2? n1 : m1 != m2? m1 : m2;
    System.out.println(result);
    }
    }
   ```
    Select the one correct answer.
    
    (a) The program will fail to compile.
    
    (b) The program will throw an ArithmeticException at runtime.
    
    (c) The program will compile and print 10 when run.
   
    (d) The program will compile and print 20 when run.
    
    (e) The program will compile and print 30 when run.

    <details markdown="block">
    <summary>Answer</summary>
    (d) 
    
    The condition in the outer conditional expression is false. The condition in the nested conditional expression is true, resulting in the value of m1 (i.e., 20) being printed.
    </details>