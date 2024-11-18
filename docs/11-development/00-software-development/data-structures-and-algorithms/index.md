---
title: Data structures and Algorithms
parent: Development
has_children: true
nav_order: 1
---

# Data structures and Algorithms
## Algorithms
An algorithm is a set of logical instructions to perform a particular task. 

An algorithm can be seen as a roadmap or a set of instructions to accomplish a well-defined task. 

The common examples of algorithms include traffic lights
regulating congestion on the streets, face recognition software on
smartphones, recommendation technologies, and so on.
It's important for you to understand that an algorithm is just a small part
of an application used to solve a well-defined problem. Examples such
as sorting a list of numbers, finding the shortest route, or word prediction
are all correct. Big software applications, such as email clients or an
operating system are improper examples.

### Complexities
------------------------- 
Algorithmic complexity is a way to describe the efficiency of an algorithm as a relation of its input. It can be used to describe various properties of our code, such as runtime speed or memory requirements. It's also a very important tool programmers should understand to write efficient software. 

When calculating the space complexity, the memory consumed for the
input arguments should be ignored. Only memory allocated inside the
algorithms should be considered.

#### Identifying the Best and Worst Performance of an Algorithm While Checking for Duplicates in an Array
------------------------- 
Assume that the inner loop results in eight operations every time it executes.
For the outer loop, assume four operations:
```java
public boolean containsDuplicates(int[] numbers) {
    for (int i=0; i<numbers.length; i++) {
        for (int j=0; j<numbers.length; j++) {
            if (i != j && numbers[i] == numbers[j]) return true;
        }
    }
    return false;
}
```
**Outer lopp operations**
|Operation name |Code| Count|
|:--------------|:---|:------|
|Reading array length and comparing to pointer |i<numbers.length|2|
|Array pointer increment and assignment|i++(i = i + 1)|2|
|Total||8|

**Inner lopp operations**
|Operation name |Code| Count|
|:--------------|:---|:------|
|Reading array length and comparing to pointer |j<numbers.length|2|
|Array pointer increment and assignment|j++(j = j + 1)|2|
|int equality |i != j|1|
|Array access and equality|numbers[i] == numbers[j])|3|
|Total||8|

To do this, we should perform the following steps:
1. In the worst- case, we execute the inner loop n times (array length).
2. In the best case, we only execute the inner loop only twice.
3. The best case is when the duplicate numbers are in the front of the input array.
The worst is when the array doesn't contain any duplicates.
4. The worst case is when the array doesn't contain duplicates and is of size n:
    * For the outer loop, we have 4*n operations
    * For the inner loop, we have n*(n*8) operations
    * In total, we have 4n + 8n2 operations
5. In the best case, the duplicates are the first two items in the array:
    * For the outer loop, we have 4 operations
    * For the inner loop, we have 2*8 operations as the inner loop executes twice to get to the second item in the array where the duplicate is located
    * In total, we have 20 operations
#### Big O Notation
------------------------- 
There are two simple rules to follow when we want to express an algorithm using the big O notation.

There are two simple rules to follow when we want to express an algorithm using the big O notation. 
1. drop any constants
   
    n + 4 becomes n
    
    5 becomes 1 -> O(1), also known as constant time complexity.
2. drop everything except the highest order 

     n + n2 + n3 becomes n3 -> O(n3)

|Expression   |First Rule|Second Rule|big O notation|
|:------------|:---------|:----------|:-------------|
|3mn          |3mn       |mn         |O(mn)         |
|5n + 44n2+ 4 |5n + 44n2 |n2         |O(n2)         |
|4 + 5 log n  |5 log n   |log n      |O(log n)      |
|3^n + 5n2 + 8|3^n + 5n2 |3^n        |O(3^n)        |

#### Linear Complexity
------------------------- 
Linear algorithms are the ones where the work done varies in direct proportion with the input size, that is, if you double the input size, you double the work done. These typically involve a single pass through the input and thus scale proportionally with the input size.

**Exampeles**

1. counting the number of occurrences of a particular character in a string.

    The algorithm is linear because its runtime is directly proportional to the
    string length. If we take the string length to be n, the runtime complexity
    of this Java method is O(n). Notice the single loop varying according to
    the input size. This is very typical of linear runtime complexity
    algorithms, where a constant number of operations are performed for
    each input unit. The input unit in this example is each character in the
    string.
    ```java
    public static int algorithm1(char c, String str) {
        int count = 0;
        for (int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == c)
                count++;
        }
        return count;
    }
    ```
#### Quadratic Complexity
-------------------------  
Quadratic complexity algorithms are not very performant for large input sizes. The work done increases following a quadratic proportion as we increase our input size.  
**Exampeles**

1. finding the common elements contained in two arrays (assuming no 
duplicate values exist in each array), producing the intersection of the two inputs

    This results in a runtime complexity of O(mn), where m and n are the sizes of the first and second input arrays. If the input arrays are the same size as n elements, this results in a runtime of O(n2). 
    ```java
    public static List<Integer> algorithm1(int[] a, int[] b) {
        List<Integer> result = new ArrayList<>(a.length);
        for (int x : a) {
            for (int y : b) {
                if (x == y)
                    result.add(x);
            }
        }
        return result;
    }
    ```
    The amount of memory we use is dictated by the size of our result listed in our method.
    The bigger this list, the more memory we're using.
    
    The best case is when we use the least amount of memory. This is when the list is empty, that is, when we have no common elements between the two arrays. Thus, this method has a best case space complexity of O(1), when there is no intersection.
    
    The worst case is just the opposite, when we have all the elements in both arrays. This can happen when the arrays are equal to each other, although the numbers may be in a different order. The memory in this case is equal to the size of one of our input arrays. In short, the worst space complexity of the method is O(n).

1. bubble  sorting
2. selection sorting
## Data structures
------------------------- 
A data structure is a way of organizing data so that it can be accessed and/or modified efficiently.