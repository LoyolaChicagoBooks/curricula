Review of basic programming concepts
------------------------------------

When reviewing basic programming concepts, it's important to cover the following essential subtopics to ensure a solid foundation for the rest of the CS2 course:

1. **Variables and Data Types:** Review the use of variables, constants, and basic data types, including integers, floating-point numbers, booleans, and strings. Discuss the type system of the language being used.

2. **Control Structures:** Review the basic control structures, including conditional statements (like `if`, `else`, `switch`), loops (like `for`, `while`, `do-while`), and how to use `break` and `continue`.

3. **Functions/Methods:** Discuss the declaration and definition of functions/methods, parameters, return types, and the call stack. Review the concept of recursion.

4. **Arrays and Strings:** Review the declaration, initialization, and manipulation of arrays and strings. Discuss multi-dimensional arrays if relevant.

5. **Object-Oriented Programming:** Review the basics of OOP, including classes, objects, methods, and instance variables. Discuss encapsulation, inheritance, and polymorphism.

6. **Exception Handling:** Discuss the concept of exceptions and how they're handled in the language being used.

7. **Input/Output (I/O):** Review basic I/O operations, including reading from and writing to the console and file I/O.

8. **Memory Management:** Discuss concepts like stack and heap, reference types and value types, and garbage collection (if relevant to the language being used).

9. **Basic Data Structures:** Discuss the use of basic data structures provided by the language's standard library, such as arrays, strings, lists, and dictionaries/maps.

10. **Programming Style and Documentation:** Discuss best practices for writing clean, readable code and for documenting code effectively.

Remember that the exact subtopics will depend on what programming language is being used and what the students have covered in their previous courses. The goal is to ensure that all students have a solid understanding of these fundamental concepts before moving on to more advanced topics.


Simple example illustrating conditionals, loops, arrays, and unit testing
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here is a simple example that incorporates conditionals, loops, arrays, and unit testing in Java. 

.. code-block:: java

    import org.junit.jupiter.api.Test;
    import static org.junit.jupiter.api.Assertions.*;

    public class ArrayProcessor {

        public int findMax(final int[] arr) {
            if (arr == null || arr.length == 0) {
                throw new IllegalArgumentException("Array must not be null or empty");
            }

            var max = arr[0];

            for (final var num : arr) {
                if (num > max) {
                    max = num;
                }
            }

            return max;
        }

        @Test
        public void testFindMax() {
            final var arrayProcessor = new ArrayProcessor();

            final var array = new int[] { 1, 5, 3, 7, 4 };
            assertEquals(7, arrayProcessor.findMax(array));

            final var array2 = new int[] { -1, -5, -3, -7, -4 };
            assertEquals(-1, arrayProcessor.findMax(array2));

            assertThrows(IllegalArgumentException.class, () -> arrayProcessor.findMax(new int[] {}));
            assertThrows(IllegalArgumentException.class, () -> arrayProcessor.findMax(null));
        }
    }


Here's how the code works:

- The `findMax` method takes an array and finds the maximum value in it. It throws an `IllegalArgumentException` if the array is `null` or empty (this is the conditional part).

- It uses a `for` loop to iterate through each element in the array.

- It uses a conditional `if` statement to check whether each number is greater than the current maximum.

- The `testFindMax` method is a unit test for the `findMax` method. It tests the method with an array of positive numbers, an array of negative numbers, an empty array, and `null`. It uses assertions to verify that the method returns the expected results.

Note: This code uses JUnit 5 for unit testing. If you're using a different version of JUnit or a different testing framework, the code for the test may need to be adjusted accordingly. Also, remember that `var` can't be used with array in Java, as the language doesn't support this style yet.
