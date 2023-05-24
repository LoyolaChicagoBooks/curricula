Data Structures 1
==================

Historical Term
   CS2

Loyola University Chicago
  `COMP 271 <https://academics.cs.luc.edu/courses/comp271.html>`__


Top 15 topics in CS2 curricula?
-------------------------------

In a typical CS2 course, you may expect to find the following topics covered, although the order and emphasis may vary depending on the particular curriculum and instructor:

- Data Structures

  - Stacks
  - Queues
  - Linked Lists
  - Trees
  - Graphs
  - Hash Tables

- Algorithms

  - Sorting (e.g., QuickSort, MergeSort)
  - Searching (e.g., Binary Search)
  - Graph traversal (e.g., Breadth-First Search, Depth-First Search)
  - Shortest path algorithms (e.g., Dijkstra's Algorithm)

- Object-Oriented Programming

  - Inheritance
  - Polymorphism
  - Abstraction
  - Encapsulation
  
- Recursion
- Algorithm Complexity Analysis
- File I/O and Serialization
- Memory Management
- Error Handling and Exceptions
- Introduction to Concurrency
- Software Engineering Principles
- Basic Design Patterns
- Unit Testing and Test-Driven Development
- Debugging Techniques
- Version Control Systems (e.g., Git)
- Introduction to GUI Programming

Please note that this list is not exhaustive, and the topics covered in a specific CS2 course may vary depending on the institution, curriculum, and instructor.

.. note:: Konstantin will take it from here.


The curated short list of top 15 main topics in order
-----------------------------------------------------

In the Data Structures 1 course, we will focus on the following main topics:

1. Transition from CS1
2. Programmer-defined types
3. Array-based lists
4. Maps
5. Sets
6. Stacks
7. Queues
8. Recursion
9. Searching
10. Sorting
11. Linked lists
12. Trees
13. Search trees
14. Hash tables

In addition, we will incorporate elements of the following cross-cutting topics throughout our coverage of the main topics:

- Problem solving and program correctness
- Algorithm analysis and performance
- Design principles and patterns
- Advanced programming techniques
- Tools


Overview of cross-cutting topics
--------------------------------

Cross-cutting topics in a curriculum are those that span multiple areas of study or are applicable to a variety of specific topics. In the context of a CS2 course focused on data structures, these topics often include general principles and methodologies rather than specific technologies or structures. 

Certainly! Here are summaries for each of the cross-cutting topics:

1. **Problem Solving and Program Correctness**: Problem solving and program correctness encompass techniques and approaches to effectively analyze and solve problems in programming. It involves understanding the problem domain, breaking down complex problems into manageable components, designing appropriate algorithms, and ensuring the correctness of program logic. Emphasizing problem-solving skills and program correctness helps students develop systematic thinking, error prevention, and the ability to write robust and reliable code.

2. **Algorithm Analysis and Performance**: Algorithm analysis and performance focus on evaluating the efficiency and performance characteristics of algorithms. Students learn techniques to measure and analyze the time complexity, space complexity, and other performance metrics of algorithms. Understanding algorithm analysis enables students to make informed decisions about choosing the most efficient algorithms for specific tasks and provides a foundation for optimizing code performance.

3. **Design Principles and Patterns**: Design principles and patterns introduce students to fundamental principles of software design and commonly used design patterns. They emphasize concepts like encapsulation, modularity, reusability, and maintainability. By learning design principles and patterns, students gain insights into designing flexible, modular, and extensible software systems. They also learn how to apply proven solutions to recurring design problems, promoting code organization, and facilitating better software architecture.

4. **Advanced Programming Techniques**: Advanced programming techniques encompass a range of advanced concepts and techniques that go beyond the basics of programming. This may include topics such as exception handling, input/output operations, concurrency, multithreading, generics, functional programming concepts, and more. Covering advanced programming techniques helps students expand their programming repertoire, enabling them to tackle complex problems, write more efficient code, and leverage language features and tools effectively.

5. **Tools**: Tools refer to the software development tools that aid programmers in various aspects of the development process. This includes integrated development environments (IDEs), version control systems (e.g., Git), build tools (e.g., Gradle, Maven), debugging tools, testing frameworks, and other software development utilities. Teaching students about relevant tools equips them with the necessary skills to efficiently write, test, debug, and maintain code, enhancing their productivity and collaboration capabilities.

By incorporating these cross-cutting topics into the curriculum, students gain a well-rounded understanding of programming principles, best practices, and techniques that can be applied across different programming domains. This broadens their skill set, fosters better code quality, and prepares them to tackle real-world programming challenges.

While it's important to study specific data structures like those listed above, these cross-cutting topics provide a framework for understanding how to use those structures effectively and efficiently. They will be revisited and applied repeatedly throughout both this course and subsequent computer science courses.


Transition from CS1: conditionals, loops, arrays, and unit testing
------------------------------------------------------------------

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

.. note::
    This code uses JUnit 5 for unit testing. If you're using a different version of JUnit or a different testing framework, the code for the test may need to be adjusted accordingly. Also, remember that `var` can't be used with array in Java, as the language doesn't support this style yet.


Programmer-defined types
------------------------

Limitations of primitive types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

So far, we have developed some familiarity with primitive types, such as ``int``, ``float``, ``boolean``, etc.
In addition, we've used ``String``, which is not technically a primitive type but is a predefined type we mostly think of as a primitive.
These types are useful in solving a great variety of problems but do not reflect specific problem domains for which we may want to develop software.

If you were to represent cardinal directions using primitive types in Java, one approach might be to use integer constants. Here is a simple example:

.. code-block:: java

    public final class CardinalDirection {
        public static final int NORTH = 0;
        public static final int EAST = 1;
        public static final int SOUTH = 2;
        public static final int WEST = 3;
    }


Then, you could define the operations on these directions in a utility class, similarly to the enum example:

.. code-block:: java

    public final class CardinalDirectionOperations {

        public static int turnRight(final int direction) {
            return (direction + 1) % 4;
        }

        public static int turnLeft(final int direction) {
            return (direction + 3) % 4;  // +3 is equivalent to -1 in modulo 4 arithmetic
        }

        public static int opposite(final int direction) {
            return (direction + 2) % 4;
        }
    }


This approach works, but it has several disadvantages compared to the alternative we are about to discuss.
In particular, it's not clear without looking at the documentation or the implementation what kinds of values are expected.
Also, if you need to add a new direction (like northeast, for example), you would need to update every switch statement or if-else chain that operates on directions.


Finite enumeration types
^^^^^^^^^^^^^^^^^^^^^^^^

Enumeration types (enums) enable the creation of user-defined data types consisting of a fixed set of named values. Enums provide better type safety and clarity compared to using plain integers or strings to represent a set of related values.

Many programming languages have the abililty to define new types to help us model our specific domain problems more effectively. 
For example, we might want to model the cardinal directions (North, East, South, West).

In Java, we can define a new ``enum`` type for this purpose.

.. code-block:: java

    public enum CardinalDirection {
        NORTH, EAST, SOUTH, WEST;
    }

We can also define behaviors on our new type:

.. code-block:: java

    public final class CardinalDirectionOperations {

        public static CardinalDirection opposite(final CardinalDirection direction) {
            return switch (direction) {
                case NORTH -> CardinalDirection.SOUTH;
                case SOUTH -> CardinalDirection.NORTH;
                case EAST -> CardinalDirection.WEST;
                case WEST -> CardinalDirection.EAST;
            };
        }

        public static CardinalDirection turnRight(final CardinalDirection direction) {
            return switch (direction) {
                case NORTH -> CardinalDirection.EAST;
                case EAST -> CardinalDirection.SOUTH;
                case SOUTH -> CardinalDirection.WEST;
                case WEST -> CardinalDirection.NORTH;
            };
        }

        public static CardinalDirection turnLeft(final CardinalDirection direction) {
            return switch (direction) {
                case NORTH -> CardinalDirection.WEST;
                case WEST -> CardinalDirection.SOUTH;
                case SOUTH -> CardinalDirection.EAST;
                case EAST -> CardinalDirection.NORTH;
            };
        }
    }

Now, you can use this type and these behaviors in your code:    

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            var direction = CardinalDirection.NORTH;
            System.out.println("Turn right from " + direction + " to get " + CardinalDirectionOperations.turnRight(direction));
            System.out.println("Turn left from " + direction + " to get " + CardinalDirectionOperations.turnLeft(direction));
        }
    }

Alternatively, the object-oriented approach supports the idea that these behaviors are closely associated with the values themselves.
Therefore, object-oriented languages, such as Java, allow us to declare and implement these behaviors within the definition of the ``enum`` type:

.. code-block:: java

    public enum CardinalDirection {
        NORTH, EAST, SOUTH, WEST;

        public CardinalDirection opposite() {
            return switch (this) {
                case NORTH -> SOUTH;
                case SOUTH -> NORTH;
                case EAST -> WEST;
                case WEST -> EAST;
            };
        }

        public CardinalDirection turnRight() {
            return switch (this) {
                case NORTH -> EAST;
                case EAST -> SOUTH;
                case SOUTH -> WEST;
                case WEST -> NORTH;
            };
        }

        public CardinalDirection turnLeft() {
            return switch (this) {
                case NORTH -> WEST;
                case WEST -> SOUTH;
                case SOUTH -> EAST;
                case EAST -> NORTH;
            };
        }
    }

Now, you can use these methods in your code:

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            final var direction = CardinalDirection.NORTH;
            System.out.println("The opposite of " + direction + " is " + direction.opposite());
            System.out.println("Turn right from " + direction + " to get " + direction.turnRight());
            System.out.println("Turn left from " + direction + " to get " + direction.turnLeft());
        }
    }

This demonstrates how enums in Java can be used to represent a set of related constants, and how they can also include behavior. 
This makes them a powerful tool for writing more expressive and self-documenting code.


Java `enum` types provide several advantages over using `int` constants:

1. **Type Safety**: Enums provide compile-time type safety. If you try to assign or pass an invalid value, the compiler will give an error. This is not the case with `int` constants, where any integer value is valid from the compiler's perspective.

2. **Code Clarity**: Enum values have meaningful names, which makes your code easier to read and understand. With `int` constants, you need to remember what each integer value represents.

3. **Enumerated Values**: The `values()` method on an enum type returns an array of its values in the order they're declared. This can be useful in many situations, such as looping over all possible values.

4. **Methods and Fields**: Enums in Java are more powerful than in many other languages. You can define methods and fields on an enum type, which can provide functionality related to each enum value.

5. **Singleton**: Each enum value is a singleton, meaning there is only one instance of that value in the JVM. This can be useful in certain design scenarios.

6. **Use in Switch Statements**: Enum values can be used in `switch` statements, providing a more readable alternative to `if-else` chains.

7. **Built-in Methods**: Java provides automatic implementations of `equals()`, `hashCode()`, and `toString()` for enum types, as well as a `valueOf(String)` method that converts a string to an enum value.

8. **Support in Java Libraries**: Many Java libraries and features have built-in support for enums. For example, the `java.util.EnumSet` and `java.util.EnumMap` classes provide high-performance, enum-based set and map implementations.

Overall, while `int` constants can be simpler and use less memory, enums provide many powerful features that make your code safer, more readable, and easier to maintain.


Aggregating values using records
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Most of the types we've worked with so far represent single values.
As we are solving increasingly complex problems, we'll want to define types to represent bigger things we build from smaller ones, starting with single values.
Java's ``record`` types will help us to do exactly that. 

For example, Turtle graphics is a popular way of introducing programming to kids. It was part of the original Logo programming language, which was developed by Wally Feurzeig, Seymour Papert, and Cynthia Solomon in 1967.

The idea is simple and based on a metaphor of a turtle moving around in a 2D space. The turtle holds a pen in one of two positions, up or down. When the pen is down, the turtle draws a line on the plane as it moves. When the pen is up, the turtle moves but doesn't draw anything.

Here are the basic commands in turtle graphics:

1. `FORWARD x` (or `FD x`): Moves the turtle forward in the direction it is currently facing by `x` units.
2. `BACKWARD x` (or `BK x`): Moves the turtle backward (opposite to the direction it is currently facing) by `x` units.
3. `RIGHT x` (or `RT x`): Rotates the turtle clockwise by `x` degrees.
4. `LEFT x` (or `LT x`): Rotates the turtle counterclockwise by `x` degrees.
5. `PENDOWN` (or `PD`): Puts the pen down so that the turtle will draw as it moves.
6. `PENUP` (or `PU`): Lifts the pen up so that the turtle will move without drawing.
7. `SETPOS x y`: Moves the turtle to the specified coordinates.
8. `SETPENCOLOR x`: Sets the pen color.

The turtle has a position on a plane and an orientation (the direction it is facing). By combining these basic commands, you can create complex drawings. It's a great way to understand the basics of programming, geometry, and the Cartesian coordinate system.

*To explore turtle graphics in modern Java, can you define the relevant enum and record types to represent the position of the turtle?*

We can create a `Position` record to represent the coordinates of the turtle on the plane and a `Direction` enum to represent the direction the turtle is facing. Let's also create a `Turtle` record which has a position and a direction.

Here's how you might do that:

.. code-block:: java

    public record Position(int x, int y) {}

    public record Turtle(Position position, Direction direction) {}


This is a simple setup. The `Turtle` has a `Position` and a `Direction`. The `Direction` enum has `turnRight()` and `turnLeft()` methods which return a new `Direction` representing a 90-degree turn in the respective direction.

To move the turtle around the plane, you would create methods that create a new `Position` based on the current `Position` and `Direction`. You would also create methods to turn the turtle by changing its `Direction`. This would maintain the immutability of `Position`, `Direction`, and `Turtle` instances.

We can also add enums to represent pen color and pen state (up/down) to our `Turtle` record:

.. code-block:: java

    public enum PenColor {
        BLACK, RED, GREEN, BLUE, YELLOW, PURPLE;  // Add more as necessary.
    }
    public enum PenState {
        UP, DOWN;
    }

Now we can add these to our `Turtle` record:

.. code-block:: java

    public record Turtle(Position position, Direction direction, PenColor penColor, PenState penState) {}


This `Turtle` record now contains all necessary information to represent the state of a turtle in a turtle graphics system: its position, the direction it's facing, the color of its pen, and whether the pen is up or down.

.. note:: 
    Remember that records in Java are immutable, which means that when you want to change the state of the turtle, you'll need to create a new `Turtle` instance with the updated state. This might seem a bit unusual if you're used to working with mutable objects, but it can help make your programs easier to reason about, since you don't have to worry about the state of an object changing over time.

To summarize, Java records are designed to be simple, transparent carriers for immutable data. This is accomplished in the following ways:

1. **Final by Default**: A record class is implicitly final, meaning it cannot be subclassed.

2. **Final Fields**: All fields in a record class are implicitly final. When a record is constructed, its fields are set, and they cannot be changed afterwards.

3. **No Mutable Methods**: There is no way to add methods to a record class that modify its fields, because all fields are final.

4. **Automatic Accessors**: The compiler automatically generates public accessor methods for all fields in a record. These methods simply return the value of the field; they do not allow the field to be changed.

This design makes records a good fit for use cases where you need a class to simply hold a set of values and don't need to change them after the object is created. They are particularly useful in "data-centric" applications where classes often serve as simple data containers. 

.. note:: 
    It's worth noting that while the fields of a record are immutable, if the fields are references to mutable objects, those objects themselves can still be mutated. This is a common pitfall when dealing with immutability in Java. To avoid this, you might need to make defensive copies of mutable objects, or use immutable objects whenever possible.


Classes with mutable state
^^^^^^^^^^^^^^^^^^^^^^^^^^

Java records are indeed a powerful feature that help reduce boilerplate code when defining classes that are meant to be simple "data carriers". However, there are certain situations where using traditional classes can be more appropriate:

1. **Mutable State**: Records are implicitly final and all their fields are final too, meaning once a record is created, it cannot be changed. This immutability is great for many scenarios, but there are situations where mutable state is necessary or more efficient. In such cases, a traditional class would be more suitable.

2. **Inheritance**: Records cannot extend other classes, although they can implement interfaces. If you need inheritance, you'll need to use a traditional class.

3. **Complex Behavior**: If a class needs to encapsulate complex behavior and not just data, a traditional class could be a better fit. The purpose of a record is to be a simple, transparent holder for its data, and to derive all of its semantics directly from that data.

4. **Customization**: Records come with automatically derived implementations of `equals()`, `hashCode()`, and `toString()`. If you need to provide a custom implementation of these methods, you might consider using a traditional class. However, note that you can still customize these methods in a record; the automatically derived implementations are just defaults.

5. **Encapsulation**: If you need to enforce strict control over the access and/or mutation of your class's fields beyond what public, private, and protected access modifiers provide, a traditional class can provide this. Records expose their state as public final fields.

Remember that while records are a great feature, they aren't designed to replace traditional classes in all situations. They are another tool in your toolbox, to be used where they make the most sense.

*How would we represent the 2d draw(r)ing area for the turtle?*

In turtle graphics, the 2D drawing area is often referred to as a "canvas". The canvas can be represented as a 2D array of pixels. Each pixel can have a color, which would be set when the turtle moves with its pen down.

First, we can define a `Pixel` record to represent a pixel on the canvas:

.. code-block:: java

    public record Pixel(PenColor color) {}


A pixel has a color, which can be set by the turtle's pen. If the pixel has not been drawn on, its color could be `null` or some default color like `WHITE`.

*How important is it to represent Pixel separate from PenColor?*

Pros:

- Flexibility: If you decide to add more properties to a pixel in the future (like transparency, brightness, etc.), it would be easier with a separate Pixel class.
- Clarity: It makes the code more self-explanatory, as it's clear that the canvas is made up of pixels, not colors.
- Abstraction: Pixel can encapsulate behavior related to a pixel, such as changing its properties or computing derived properties.

Cons:

- Overhead: It introduces additional complexity into the code, especially if each Pixel instance is its own object.
- Memory Usage: If there are many Pixel objects, this could take up more memory compared to just storing the PenColor values directly.
- Performance: Accessing and manipulating Pixel objects could be slower compared to working with PenColor values directly.


Then, we can define a `Canvas` class to represent the 2D drawing area:

.. code-block:: java

    public final class Canvas {
        private final Pixel[][] pixels;

        public Canvas(final int width, final int height) {
            pixels = new Pixel[height][width];
            // Initialize all pixels to white.
            for (final var row : pixels) {
                Arrays.fill(row, new Pixel(PenColor.WHITE));
            }
        }

        public Pixel getPixel(final int x, final int y) {
            return pixels[y][x];
        }

        public void setPixel(final int x, final int y, final Pixel pixel) {
            pixels[y][x] = pixel;
        }
    }


The `Canvas` class contains a 2D array of `Pixel` objects. The `getPixel` method returns the `Pixel` at a specific position, and the `setPixel` method sets the `Pixel` at a specific position.

This is a very basic representation of a canvas for turtle graphics. In a real implementation, you would likely want to add more features and error-checking. For example, you might want to add methods to draw lines or shapes, check if a position is within the bounds of the canvas, etc.

.. note:: 
    In Java, final parameters are often used to clarify that an input parameter value will not be changed within the method. This can make the code easier to understand, because it's clear from the method signature that the method does not modify the input parameters.

    The final keyword in the enhanced for loop ensures that the loop variable row cannot be reassigned within the loop. This can help prevent bugs, because it makes it clear that the loop variable is not supposed to change after it has been initialized.


To draw letters on the canvas using turtle graphics, we first need to define some movements for our `Turtle` that correspond to drawing each letter. This can get quite complex, so for simplicity, let's define some basic movements that can be used to draw a very simplified version of the letters "L", "U", and "C". We'll use an 8x8 grid for each letter.

Let's assume that we start at the bottom left corner of the 'L', move up to draw the vertical line, then move right to draw the horizontal line. Then we'll lift the pen, move to the starting position for the 'U' and so on.

Here's a very basic main method illustrating this:

.. code-block:: java

    public static void main(final String[] args) {
        final var canvas = new Canvas(24, 8);
        final var turtle = new Turtle(new Position(0, 0), CardinalDirection.NORTH, Pen.UP, PenColor.BLACK);

        // Draw 'L'
        turtle.setPen(Pen.DOWN);
        turtle.move(6, canvas); // Vertical line
        turtle.setDirection(CardinalDirection.WEST);
        turtle.move(6, canvas); // Horizontal line

        // Lift pen and move to start of 'U'
        turtle.setPen(Pen.UP);
        turtle.setDirection(CardinalDirection.EAST);
        turtle.move(8, canvas); // Space between letters
        turtle.setDirection(CardinalDirection.NORTH);
        turtle.move(6, canvas); // Move to top of next letter

        // Draw 'U'
        turtle.setPen(Pen.DOWN);
        turtle.setDirection(CardinalDirection.SOUTH);
        turtle.move(6, canvas); // First vertical line
        turtle.setDirection(CardinalDirection.EAST);
        turtle.move(6, canvas); // Horizontal line
        turtle.setDirection(CardinalDirection.NORTH);
        turtle.move(6, canvas); // Second vertical line

        // Lift pen and move to start of 'C'
        turtle.setPen(Pen.UP);
        turtle.setDirection(CardinalDirection.EAST);
        turtle.move(8, canvas); // Space between letters

        // Draw 'C'
        turtle.setPen(Pen.DOWN);
        turtle.setDirection(CardinalDirection.SOUTH);
        turtle.move(6, canvas); // First vertical line
        turtle.setDirection(CardinalDirection.EAST);
        turtle.move(6, canvas); // Horizontal line at the bottom
        turtle.setDirection(CardinalDirection.NORTH);
        turtle.move(6, canvas); // Second vertical line
        turtle.setDirection(CardinalDirection.WEST);
        turtle.move(6, canvas); // Horizontal line at the top

        // Print the canvas (for demonstration purposes, represent black pixels with 'X' and white pixels with ' ')
        for (final var row : canvas.getPixels()) {
            for (final var pixel : row) {
                System.out.print(pixel.getColor() == PenColor.BLACK ? 'X' : ' ');
            }
            System.out.println();
        }
    }


This is a very simplified example, and the letters won't look very good, especially the 'U' and 'C' which are supposed to have curves. In a real-world turtle graphics system, you would have commands to draw curves and diagonal lines, and you would probably use a much larger grid for better resolution.

.. warning:: Even ChatGPT-4 has real trouble coming up with and/or interpreting the code for drawing the letters. Manual review required!


Abstract data types (ADTs)
^^^^^^^^^^^^^^^^^^^^^^^^^^

An Abstract Data Type (ADT) is a high-level description of a collection of data and the operations that can be performed on that data. It is "abstract" because it provides an interface that hides the specific implementation details. This means that the same ADT could be implemented in many different ways, but as long as the data and operations are consistent, those different implementations are equivalent from the perspective of a client using the ADT.

An ADT encapsulates data and methods together and focuses on what is to be done rather than how it is done. The "what" are the operations or methods, and the "how" is the internal working or implementation, which is hidden from the user. 

For example, consider the ADT of a List. A List ADT might specify operations such as `add(item)`, `remove(item)`, `get(index)`, `size()`, and so on. However, it doesn't specify how these operations are implemented. This allows a List to be implemented in various ways (for instance, as an ArrayList or a LinkedList in Java) while still providing the same interface to the user. 

The main advantage of using ADTs is that they provide a way to separate the concerns of what data a program is working with and how that data is stored and manipulated. This makes programs easier to understand, write, and debug. It also enables greater reusability of code, as the same ADT can be used in multiple different programs or parts of a program.


Key takeaways
^^^^^^^^^^^^^

The key takeaways from a discussion of programmer-defined types, including enums, records, classes, and abstract data types (ADTs), are as follows:

1. **Enums**: Enums are used to represent a fixed set of values or constants. They provide a way to define a specific type with a limited number of valid values. Enums are useful for modeling concepts that have a finite set of options, such as days of the week or status codes. They enhance code clarity, readability, and type safety by providing named values.

2. **Records**: Records are a newer addition to Java (introduced in Java 14) and provide a concise way to define classes that primarily store data. They automatically generate appropriate constructors, accessors, and `equals()`, `hashCode()`, and `toString()` methods based on the fields defined in the record. Records are a convenient choice when creating data-centric classes with minimal behavior.

3. **Classes**: Classes are the fundamental building blocks of object-oriented programming. They encapsulate data and behavior within a single unit. Classes allow for the definition of fields (data) and methods (behavior) and support concepts like inheritance, polymorphism, and encapsulation. They provide a flexible way to model real-world entities and implement complex functionality.

4. **Abstract Data Types (ADTs)**: ADTs represent a higher-level concept that focuses on the behavior and operations of a data structure rather than its implementation details. ADTs define a set of operations that can be performed on a data structure without exposing its internal representation. They abstract away the implementation and allow users to interact with the data structure through well-defined interfaces. ADTs can be implemented using classes or interfaces, providing a level of abstraction and modularity in software design.

Key takeaways include understanding the different types available for defining and modeling data structures and concepts, as well as their specific use cases. Enums provide a way to represent fixed sets of values, records offer a concise way to define data-centric classes, classes provide the foundation for object-oriented programming, and ADTs enable abstraction and modularity in software design. Utilizing these types appropriately can lead to more expressive, maintainable, and efficient code.


Lists
-----

A list can be defined as an ordered collection of elements, where each element has a specific position or index within the collection. The list ADT allows operations for adding, removing, and accessing elements based on their position in the list. It provides functionality to manipulate and retrieve elements in a sequential manner.

The key characteristics of a list ADT typically include:

1. **Ordering**: The elements in a list have a specific order or sequence. The order is maintained as elements are added or removed from the list.

2. **Indexing**: Each element in the list is associated with a unique index, starting from 0 for the first element, and incrementing by one for each subsequent element. This allows for efficient random access to elements based on their index.

3. **Dynamic Size**: A list can dynamically adjust its size to accommodate the addition or removal of elements. It can grow or shrink as needed to hold the elements.

4. **Element Manipulation**: A list allows for various operations, such as inserting elements at specific positions, removing elements from specific positions, retrieving elements by index, searching for elements, and modifying elements at specific positions.

It's important to note that the list ADT is an abstract concept and does not specify the underlying implementation. Depending on the programming language or specific requirements, there can be different implementations of lists, such as arrays, linked lists, or other data structures.

The list ADT serves as a fundamental data structure, and students learn about the essential operations and characteristics associated with lists. They explore different implementations and gain an understanding of the trade-offs and performance implications of each implementation choice.


Immutable lists
^^^^^^^^^^^^^^^

The `List.of` factory method provides a convenient way to create immutable lists. It returns an immutable `List` instance that cannot be modified, making it useful for scenarios where you want to ensure immutability or create a fixed set of elements.

To use the `List.of` factory method, you can directly call it and provide the elements as arguments. Here's an example:

.. code-block:: java

    import java.util.List;

    final List<String> fruits = List.of("Apple", "Banana", "Orange");

In this example, the `List.of` factory method creates an immutable `List` containing the specified elements `"Apple"`, `"Banana"`, and `"Orange"`. The returned list cannot be modified, so any attempts to add, remove, or modify elements will result in an `UnsupportedOperationException`.

It's important to note that the `List.of` factory method creates an immutable list, meaning you cannot modify its contents after creation. If you need a mutable list that allows modifications, you should use one of the implementations I mentioned earlier, such as `ArrayList`, `LinkedList`, or `CopyOnWriteArrayList`.

The `List.of` factory method provides a concise and readable way to create immutable lists in Java, promoting immutability and ensuring data integrity in scenarios where you don't need to modify the list once it's created.


Unit tests for unmodifiable lists
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The `List.of()` method returns an unmodifiable list that does not support the `add` and `remove` operations. Here's an example of unit tests using the `List.of()` factory method to demonstrate the behavior of other methods in the List API:

.. code-block:: java

    import java.util.List;
    import java.util.Arrays;

    import static org.junit.Assert.*;
    import org.junit.Test;

    public class ListApiTest {

        @Test
        public void testGet() {
            final List<String> list = List.of("Apple", "Banana", "Orange");
            assertEquals("Banana", list.get(1));
        }

        @Test
        public void testContains() {
            final List<String> list = List.of("Apple", "Banana", "Orange");
            assertTrue(list.contains("Apple"));
            assertFalse(list.contains("Mango"));
        }

        @Test
        public void testSize() {
            final List<String> list = List.of("Apple", "Banana", "Orange");
            assertEquals(3, list.size());
        }
    }

These unit tests focus on the methods that are supported by the `List.of()` factory method, such as `get`, `contains`, and `size`. These tests verify the expected behavior of these methods with an immutable list returned by `List.of()`. The tests ensure that the elements can be retrieved by index, the presence of specific elements can be checked, and the size of the list is correct.

It's important to note that the `List.of()` method returns an unmodifiable list, which limits the ability to perform certain operations like adding or removing elements.


Main methods of the List ADT
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. What are the top 10 methods for using the list interface in Java 17?

Here are the top 10 methods that you will commonly use when working more generally with a mutable List implementation in Java:

1. `boolean add(E e)`: Appends the specified element to the end of the list. This method returns `true` if the element was added successfully.

2. `void add(int index, E element)`: Inserts the specified element at the specified position in the list.

3. `E get(int index)`: Returns the element at the specified position in the list.

4. `E remove(int index)`: Removes the element at the specified position in the list, and returns the element that was removed.

5. `boolean remove(Object o)`: Removes the first occurrence of the specified element from the list, if it is present.

6. `E set(int index, E element)`: Replaces the element at the specified position in the list with the specified element.

7. `int size()`: Returns the number of elements in the list.

8. `boolean isEmpty()`: Returns `true` if the list contains no elements.

9. `void clear()`: Removes all of the elements from the list.

10. `boolean contains(Object o)`: Returns `true` if the list contains the specified element.

These methods cover the most common operations you'll perform on a List: adding elements, removing elements, getting or setting the value of an element, checking the size, and checking if an element is present in the List.


.. todo:: Introduce correctness at the API level: preconditions and postconditions


How to create mutable List instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In Java, the `List` interface is an interface and cannot be directly instantiated. However, you can create an instance of a class that implements the `List` interface. Here are a few examples of commonly used implementations of the `List` interface and how to instantiate them:

1. **ArrayList**:

.. code-block:: java

    import java.util.List;
    import java.util.ArrayList;

    final List<String> arrayList = new ArrayList<>();

In this example, an instance of `ArrayList` is created and assigned to the `List<String>` variable `arrayList`. `ArrayList` is a resizable array-based implementation of the `List` interface.

2. **LinkedList**:

.. code-block:: java

    import java.util.List;
    import java.util.LinkedList;

    final List<String> linkedList = new LinkedList<>();

Here, an instance of `LinkedList` is created and assigned to the `List<String>` variable `linkedList`. `LinkedList` is a doubly-linked list implementation of the `List` interface.

3. **Vector**:

.. code-block:: java

    import java.util.List;
    import java.util.Vector;

    final List<String> vector = new Vector<>();

In this example, an instance of `Vector` is created and assigned to the `List<String>` variable `vector`. `Vector` is a synchronized array-based implementation of the `List` interface.

4. **CopyOnWriteArrayList**:

.. code-block:: java

    import java.util.List;
    import java.util.concurrent.CopyOnWriteArrayList;

    final List<String> copyOnWriteArrayList = new CopyOnWriteArrayList<>();

Here, an instance of `CopyOnWriteArrayList` is created and assigned to the `List<String>` variable `copyOnWriteArrayList`. `CopyOnWriteArrayList` is a thread-safe implementation of the `List` interface that provides enhanced concurrency support.

These are just a few examples of classes that implement the `List` interface, and we will discuss mostly `ArrayList` and `LinkedList` in this course. The choice of implementation depends on the specific requirements of your application, considering factors like performance, concurrency, and usage patterns. By instantiating classes that implement the `List` interface, you can utilize the methods and functionality provided by the `List` interface to work with collections of elements in a flexible and consistent manner.


Unit tests for the full List API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. Can you write unit tests to show that each method does what is intended?

Here is an example of using JUnit 5 to write unit tests for the `List` methods:

.. code-block:: java

    import org.junit.jupiter.api.*;
    import java.util.*;

    import static org.junit.jupiter.api.Assertions.*;

    public class ListTest {
        private List<Integer> list;
        private static final int SIZE = 10;

        @BeforeEach
        public void setup() {
            list = new ArrayList<>();
            for (var i = 0; i < SIZE; i++) {
                list.add(i);
            }
        }

        @Test
        public void testAdd() {
            assertTrue(list.add(SIZE + 1));
            assertEquals(SIZE + 1, list.size());
        }

        @Test
        public void testAddAtIndex() {
            list.add(5, SIZE + 1);
            assertEquals(SIZE + 1, list.get(5));
        }

        @Test
        public void testGet() {
            assertEquals(0, list.get(0));
        }

        @Test
        public void testRemoveByIndex() {
            assertEquals(0, list.remove(0));
            assertEquals(SIZE - 1, list.size());
        }

        @Test
        public void testRemoveByObject() {
            assertTrue(list.remove(Integer.valueOf(0)));
            assertEquals(SIZE - 1, list.size());
        }

        @Test
        public void testSet() {
            assertEquals(0, list.set(0, SIZE + 1));
            assertEquals(SIZE + 1, list.get(0));
        }

        @Test
        public void testSize() {
            assertEquals(SIZE, list.size());
        }

        @Test
        public void testIsEmpty() {
            assertFalse(list.isEmpty());
            list.clear();
            assertTrue(list.isEmpty());
        }

        @Test
        public void testContains() {
            assertTrue(list.contains(0));
            assertFalse(list.contains(SIZE + 1));
        }
    }

Each of these test methods uses assertions to ensure that the list behaves as expected when its methods are called. For example, `testAdd` verifies that `add` returns true and increases the size of the list by one, and `testGet` verifies that `get` returns the expected element.


Performance of List ADT implementations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here's a table summarizing the average time complexity of the main List API methods for ArrayList and LinkedList:

.. csv-table:: 
    :header: "Method", "ArrayList", "LinkedList"
    :widths: 20, 20, 20

    "add(E e)", "O(1)*", "O(1)"
    "add(int index, E element)", "O(n)", "O(n)"
    "remove(int index)", "O(n)", "O(n)"
    "get(int index)", "O(1)", "O(n)"
    "set(int index, E element)", "O(1)", "O(n)"
    "size()", "O(1)", "O(1)"
    "isEmpty()", "O(1)", "O(1)"
    "contains(Object o)", "O(n)", "O(n)"

(*) Amortized time is O(1)

We will discuss later when and why one would want to choose one list implementation over another.


Key takeaways
^^^^^^^^^^^^^

The List ADT is a fundamental data structure in computer science, allowing for flexible and ordered storage of elements. Java's List interface provides a number of methods for manipulating lists, such as adding, removing, and retrieving elements. Different list implementations (like ArrayList and LinkedList) offer different performance characteristics. Understanding these can help you choose the right implementation for your specific needs. Testing ensures the correct behavior of your list operations, and implementation helps deepen understanding of the underlying mechanics.


Array-based lists
-----------------

In Java, `ArrayList` is a class that implements the `List` interface.

The `List` interface is a part of Java's Collection Framework and extends the `Collection` interface. It is an ordered collection (also known as a sequence), and it can contain duplicate elements. The user has precise control over where in the list each element is inserted, and can access elements by their integer index (position in the list). The `List` interface provides a contract for common list operations, such as add, get, remove, indexOf, and others.

`ArrayList` is one of the several implementations of the `List` interface provided with Java's standard library. It's backed by a dynamic array, which means the size of the `ArrayList` can grow or shrink as needed. 

`ArrayList` provides fast random read access (i.e., fast access to elements by index) because it's backed by an array. However, adding elements to the middle of the `ArrayList` or removing elements from the middle is slower because elements need to be shifted.


Example
^^^^^^^

Here's how you might use `ArrayList` as a `List`:

.. code-block:: java

    List<String> names = new ArrayList<>();
    names.add("Alice");
    names.add("Bob");
    names.add("Charlie");
    final var firstPerson = names.get(0);  // Alice

In this code, we're declaring a variable `names` of type `List<String>`, but we're initializing it with an instance of `ArrayList<String>`. This means that we can use any class that implements `List<String>` to initialize `names`. This is a common example of programming to an interface in Java, which makes code more flexible and modifiable.


Arrays vs. array-based lists
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. Let's move on to the next major CS2 topic, Array and ArrayList: Please describe these structures and provide an example of each to help me gain an Understanding of these basic data structures, their uses, and limitations.

Let's explore the Array and ArrayList data structures.

**Array:**
An array is a fixed-size data structure that stores elements of the same type in contiguous memory locations. It provides random access to its elements using indices. Arrays have a predetermined length that is defined at the time of declaration, and this length cannot be changed once the array is created.

Here's an example of creating and using an array in Java:

.. code-block:: java

    final var numbers = new int[5]; // Creating an array of integers with a length of 5

    numbers[0] = 10; // Assigning a value to the first element
    numbers[1] = 20; // Assigning a value to the second element

    System.out.println(numbers[0]); // Accessing and printing the value of the first element
    System.out.println(numbers[1]); // Accessing and printing the value of the second element

In this example, we create an array called `numbers` with a length of 5. We can assign values to specific elements using index notation (`numbers[index] = value`) and access the values using the same notation (`numbers[index]`). Arrays provide constant-time access to any element, making it efficient to retrieve or modify elements by their index.

Arrays have a fixed size, so adding or removing elements requires creating a new array with the desired size and copying the existing elements. This can be cumbersome and inefficient if the size of the array needs to change frequently.

**ArrayList:**
The ArrayList is a dynamic data structure provided by the Java Collections Framework. It is implemented as an array internally, but it automatically manages the resizing and reallocation of memory as elements are added or removed. Unlike regular arrays, ArrayLists can grow or shrink dynamically to accommodate the number of elements.

Here's an example of creating and using an ArrayList in Java:

.. code-block:: java

    import java.util.ArrayList;

    final var numbersList = new ArrayList<Integer>(); // Creating an ArrayList of integers

    numbersList.add(10); // Adding an element to the ArrayList
    numbersList.add(20); // Adding another element to the ArrayList

    System.out.println(numbersList.get(0)); // Accessing and printing the value of the first element
    System.out.println(numbersList.get(1)); // Accessing and printing the value of the second element

In this example, we create an ArrayList called `numbersList` to store integers. We can add elements to the ArrayList using the `add` method and access the elements using the `get` method. ArrayLists provide similar functionality as arrays but with the added benefit of dynamic resizing.

ArrayLists automatically handle memory allocation and resizing behind the scenes. When the ArrayList reaches its initial capacity, it automatically increases its size by allocating a new array and copying the elements from the old array to the new one. This dynamic resizing makes ArrayLists more flexible than regular arrays when it comes to adding or removing elements.

It's important to note that ArrayLists have a small performance overhead compared to regular arrays due to the dynamic resizing and memory management operations. If you need constant-time access to elements by index and the size of the collection is fixed, arrays may be more suitable. However, if you require a flexible and resizable collection, ArrayLists provide a convenient solution.

Both arrays and ArrayLists have their own use cases and limitations, and the choice between them depends on the specific requirements of the problem you are solving.

While ArrayLists offer flexibility and convenience, there are a few disadvantages to consider:

1. **Memory Overhead**: ArrayLists have a higher memory overhead compared to arrays. In addition to storing the actual elements, ArrayLists also maintain internal bookkeeping information such as the array capacity and size. This extra memory usage can be a concern if memory efficiency is critical in your application.

2. **Insertion and Deletion in the Middle**: Inserting or removing elements in the middle of an ArrayList can be less efficient compared to appending elements at the end. When an element is inserted or removed in the middle, the ArrayList needs to shift subsequent elements, which requires additional time. If you frequently perform operations that involve insertion or deletion in the middle, a different data structure like a linked list may be more suitable.

3. **Primitive Types Boxing/Unboxing**: ArrayLists in Java can only store objects, so when working with primitive types (e.g., `int`, `char`, etc.), they are automatically boxed into their corresponding wrapper classes (e.g., `Integer`, `Character`, etc.). This process of autoboxing and unboxing can lead to a slight performance overhead and increased memory usage.

4. **Synchronized Access**: ArrayLists are not inherently thread-safe. If you need to use ArrayLists in a multi-threaded environment, you must ensure proper synchronization to avoid concurrent modification issues. This can add complexity and potential overhead in terms of performance.

5. **Resizing Impact**: When an ArrayList needs to resize its internal array, it creates a new array with a larger size and copies the elements from the old array to the new one. This resizing operation can be time-consuming, especially if the ArrayList contains a large number of elements. If you know the approximate size requirements in advance, initializing the ArrayList with an initial capacity can help mitigate frequent resizing.

Despite these disadvantages, ArrayLists remain a widely used data structure due to their flexibility, ease of use, and the convenience provided by the Java Collections Framework. Understanding the limitations and trade-offs of ArrayLists can help you make informed decisions when selecting the appropriate data structure for your specific needs.


Example
^^^^^^^

Here is an example of using each of the List methods with an ArrayList implementation and randomly generated data:

.. code-block:: java

    import java.util.*;

    public class Main {
        public static void main(final String[] args) {
            final var list = new ArrayList<Integer>();
            final var random = new Random();

            // 1. add(E e)
            for (var i = 0; i < 10; i++) {
                final var numberToAdd = random.nextInt(100);
                list.add(numberToAdd);
                System.out.println("Added " + numberToAdd);
            }

            // 2. add(int index, E element)
            final var indexToAddAt = random.nextInt(list.size());
            final var numberToAddAtIndex = random.nextInt(100);
            list.add(indexToAddAt, numberToAddAtIndex);
            System.out.println("Added " + numberToAddAtIndex + " at index " + indexToAddAt);

            // 3. get(int index)
            final var indexToGet = random.nextInt(list.size());
            System.out.println("Element at index " + indexToGet + " is " + list.get(indexToGet));

            // 4. remove(int index)
            final var indexToRemove = random.nextInt(list.size());
            System.out.println("Removed element " + list.remove(indexToRemove) + " at index " + indexToRemove);

            // 5. remove(Object o)
            final var numberToRemove = list.get(random.nextInt(list.size()));
            final var removalSuccessful = list.remove(Integer.valueOf(numberToRemove));
            if (removalSuccessful) {
                System.out.println("Successfully removed " + numberToRemove);
            } else {
                System.out.println("Failed to remove " + numberToRemove);
            }

            // 6. set(int index, E element)
            final var indexToSet = random.nextInt(list.size());
            final var numberToSetAtIndex = random.nextInt(100);
            System.out.println("Set element at index " + indexToSet + " to " + list.set(indexToSet, numberToSetAtIndex));

            // 7. size()
            System.out.println("List size is " + list.size());

            // 8. isEmpty()
            System.out.println("Is list empty? " + list.isEmpty());

            // 9. clear()
            list.clear();
            System.out.println("List cleared.");

            // Check if list is empty after clearing.
            System.out.println("Is list empty after clear? " + list.isEmpty());

            // 10. contains(Object o)
            // As list is empty after clear, it will not contain the number
            final var doesListContain = list.contains(random.nextInt(100));
            System.out.println("Does list contain random number? " + doesListContain);
        }
    }

In this program, a new ArrayList of integers is created. The program then randomly adds integers, gets and removes integers at random indices, checks the size, and checks if the list is empty. The list is then cleared, and finally checks if the list contains a random number. Each operation is output to the console using `System.out.println()`.


.. todo:: Introduce algorithm analysis at a very basic level - big-O notation for constant-time and linear-time performance.


Performance of ArrayList methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. What are time and space complexity of the main ArrayList methods?

The time and space complexity of the main ArrayList methods are as follows:

1. **Add (Append)**: The `add` method in ArrayList adds an element to the end of the list. If the underlying array needs to be resized to accommodate the new element, the time complexity is amortized O(1) on average. In the worst case, when the array needs to be resized, the time complexity becomes O(n), where n is the number of elements in the list. The space complexity is O(n), as the underlying array may need to be resized.

2. **Add (Insert)**: The `add` method can also be used to insert an element at a specific index in the list. If the element is inserted at the beginning or middle of the list, it requires shifting subsequent elements, resulting in a time complexity of O(n), where n is the number of elements in the list. The space complexity is O(n) in the worst case if the underlying array needs to be resized.

3. **Get**: The `get` method retrieves an element from the list based on its index. It has a time complexity of O(1) as accessing elements by index in an ArrayList is a constant-time operation. The space complexity is O(1) as it does not require any additional memory allocation.

4. **Remove**: The `remove` method removes an element from the list based on its index. If the element is removed from the beginning or middle of the list, it requires shifting subsequent elements, resulting in a time complexity of O(n), where n is the number of elements in the list. The space complexity is O(n) in the worst case if the underlying array needs to be resized.

5. **Contains**: The `contains` method checks whether an element is present in the list. It performs a linear search through the elements, resulting in a time complexity of O(n), where n is the number of elements in the list. The space complexity is O(1) as it does not require any additional memory allocation.

6. **Size**: The `size` method returns the number of elements in the list. It has a time complexity of O(1) as the size of the ArrayList is maintained as a separate variable. The space complexity is O(1) as it does not require any additional memory allocation.

It's important to note that the time and space complexities mentioned here are based on the typical implementation of ArrayList in Java. Different programming languages or specific ArrayList implementations may have variations in their complexity characteristics, so it's always advisable to refer to the documentation or implementation details of the specific ArrayList you are working with.


How to create ArrayList instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. I believe arraylist implements the methods of list, but what constructors does arraylist have?

The `ArrayList` class in Java provides several constructors for creating a new `ArrayList`. As of Java 17, these constructors include:

1. `ArrayList()`: This constructor is used to create an empty list with an initial capacity sufficient to hold 10 elements (by default). If the list grows beyond this capacity, it is automatically resized.

.. code-block:: java

    List<String> list = new ArrayList<>();

2. `ArrayList(int initialCapacity)`: This constructor is used to create an empty list with a specified initial capacity. If the list grows beyond this capacity, it is automatically resized.

.. code-block:: java

    List<String> list = new ArrayList<>(50);

3. `ArrayList(Collection<? extends E> c)`: This constructor is used to create a list containing the elements of the specified collection, in the order they are returned by the collection's iterator.

.. code-block:: java

    List<String> otherList = new ArrayList<>();
    otherList.add("Alice");
    otherList.add("Bob");

    List<String> list = new ArrayList<>(otherList);  // list now contains "Alice" and "Bob"

Each of these constructors provides a different way to initialize an `ArrayList`, depending on your specific needs.


Sample implementation
^^^^^^^^^^^^^^^^^^^^^

.. Can you show a simple yet modern Java implementation class of the Map interface, pedagogically suitable for a CS2 audience (second computer science course)? The implementation doesn't have to be complete but should include the handful or so of essential methods.

.. todo:: Introduce correctness at the implementation level: class invariants (data invariants) and their relationship with pre- and postconditions.

An implementation of a basic `ArrayList` in Java might look like this:

.. code-block:: java

    import java.util.Arrays;

    public class SimpleArrayList<E> {
        private static final int INITIAL_CAPACITY = 10;
        private Object[] elementData;
        private int size = 0;

        public SimpleArrayList() {
            elementData = new Object[INITIAL_CAPACITY];
        }

        public void add(E e) {
            ensureCapacity();
            elementData[size++] = e;
        }

        @SuppressWarnings("unchecked")
        public E get(final int index) {
            if (index < 0 || index >= size) {
                throw new IndexOutOfBoundsException("Index: " + index + ", Size: " + size);
            }
            return (E) elementData[index];
        }

        public int size() {
            return size;
        }

        private void ensureCapacity() {
            int currentCapacity = elementData.length;
            if (size + 1 > currentCapacity) {
                int newCapacity = currentCapacity * 2;
                elementData = Arrays.copyOf(elementData, newCapacity);
            }
        }
    }

This `SimpleArrayList` class is a very simplified implementation of an `ArrayList` in Java. It starts with an initial capacity (10, in this case), and when that capacity is exceeded, it creates a new array with double the previous capacity and copies the old elements into the new array. This ensures that there's always room to add new elements.

The `add` method is used to add elements to the list. If the capacity of the list is exceeded, the `ensureCapacity` method is called to increase the capacity of the list.

The `get` method is used to retrieve an element from the list at a specific index. If the index is invalid (negative, or greater than or equal to the size of the list), it throws an `IndexOutOfBoundsException`.

The `size` method returns the number of elements currently in the list.

Note that this is a very basic implementation and lacks many features and optimizations of the actual `ArrayList` class in the Java Collections Framework. It's intended to be an illustrative example of how you might start to implement such a data structure.    


Key takeaways
^^^^^^^^^^^^^

The key takeaways from a discussion of ArrayList and its comparison with basic arrays are as follows:

Certainly! Here's a revised order of the key takeaways based on your request:

1. **Efficiency and Performance**: `ArrayList` provides efficient random access to elements by their index, allowing for quick retrieval and modification operations. It offers similar performance characteristics to basic arrays in terms of accessing elements.

2. **Convenience and Abstraction**: `ArrayList` abstracts away the complexity of managing array resizing and provides built-in methods for adding, removing, and accessing elements. It offers a higher-level interface compared to basic arrays, making it more convenient to work with collections of data.

3. **Type Safety and Compile-Time Checks**: `ArrayList` ensures type safety by allowing only elements of the specified type to be added to the list. This helps prevent type-related errors and provides compile-time checks, reducing the risk of runtime exceptions.

4. **Dynamic Size and Flexibility**: `ArrayList` dynamically adjusts its size as elements are added or removed, providing flexibility for handling varying amounts of data. It offers a resizable alternative to basic arrays, which have a fixed length.

5. **Overhead and Additional Complexity**: `ArrayList` incurs additional overhead compared to basic arrays due to resizing operations and maintaining extra metadata. This overhead includes increased memory usage and computational cost.

Key takeaways include understanding that ArrayList offers dynamic size, convenient methods, efficient random access, and automatic memory management. However, it also incurs additional overhead compared to basic arrays. Choosing between ArrayList and basic arrays depends on the specific requirements of the application. If dynamic resizing, convenience methods, and type safety are important, ArrayList is a suitable choice. On the other hand, basic arrays may be preferred when a fixed-size collection or minimal overhead is required.


Maps
----

A map data structure, also known as a dictionary or associative array, is an extremely useful data structure that allows you to store and retrieve values based on a unique key. Here are a few reasons why you might use a map data structure in the context of a Computer Science 2 (CS2) course:

Efficient Lookup: The most compelling reason to use a map is the ability to efficiently look up values using a key. Maps usually provide O(1) lookup time, which means it takes the same amount of time to find a value regardless of the number of items in the map. This is significantly faster than looking up a value in a list or array, which generally requires O(n) time.

Data Organization: Maps can be very useful for organizing data. You can use the key-value structure of a map to associate related data. For example, if you were creating a program to manage a library, you might use a map to associate book titles with information about each book, such as its author and publication date.

Counting and Grouping: Maps are ideal for counting occurrences of items or grouping items by a certain property. For example, you could use a map to count the number of times each word appears in a document. The words would be the keys and the counts would be the values.

Implementing Abstract Data Types: Maps can be used to implement various abstract data types (ADTs) such as caches, indexes, symbol tables in compilers, or in representing adjacency lists in graphs. These applications are central to many areas of computer science.

Programming Language Support: Many programming languages have built-in support for map data structures, making them a convenient choice for many tasks.

In summary, maps are a powerful tool that can greatly simplify your code and improve its performance. They're an essential part of a computer science student's toolkit, and learning how to use them effectively can greatly benefit your problem-solving abilities.


Example
^^^^^^^

Here is an example of counting the occurrences of words in a sentence. This is a classic problem that maps solve very efficiently. I will use the java.util.Map interface along with its implementing class java.util.HashMap:

.. code-block:: java

    import java.util.HashMap;
    import java.util.Map;

    public class WordCount {
        public static void main(final String[] args) {
            final var sentence = "If it is to be, it is up to me to delegate";
            final var words = sentence.split("\\s+");
            final var wordCount = new HashMap<String, Integer>();

            for (final var word : words) {
                // Compute is a nice method which lets you update a key's value in a map based on its old value.
                // Here, we're saying "increase the count by 1 if the word is present, otherwise start the count at 1"
                wordCount.compute(word, (key, oldValue) -> oldValue == null ? 1 : oldValue + 1);
            }

            // Print the count of each word
            for (final var entry : wordCount.entrySet()) {
                System.out.println(entry.getKey() + ": " + entry.getValue());
            }
        }
    }

In this program, we start by splitting a sentence into individual words. We then iterate over these words. For each word, we use the Map.compute method to either set its count to 1 if it's not already in the map, or increase its count by 1 if it is.

After counting all the words, we print out the count of each word.

This example shows the core of what makes maps useful: associating one value (the word) with another (its count), and allowing you to quickly and efficiently update that association. It's a simple example, but the principle extends to much more complex and powerful uses.

.. warning:: Discuss whether to include these Map API's higher-order methods


The Java Map API
^^^^^^^^^^^^^^^^

.. todo:: add thoughts on map as a generalization of array/ArrayList

The `java.util.Map` interface provides many powerful operations for working with key-value data. As of Java 17, here are some of the main methods available:

1. **put(K key, V value):** Inserts a key-value pair into the map. If the map already contains a mapping for the key, the old value is replaced with the specified value.

2. **get(Object key):** Returns the value to which the specified key is mapped, or null if the map contains no mapping for the key.

3. **remove(Object key):** Removes the mapping for a key from this map if it is present.

4. **containsKey(Object key):** Returns true if this map contains a mapping for the specified key.

5. **containsValue(Object value):** Returns true if this map maps one or more keys to the specified value.

6. **keySet():** Returns a `Set` view of the keys contained in this map.

7. **values():** Returns a `Collection` view of the values contained in this map.

8. **entrySet():** Returns a `Set` view of the mappings contained in this map. Each element in the returned set is a `Map.Entry` object.

9. **isEmpty():** Returns true if this map contains no key-value mappings.

10. **size():** Returns the number of key-value mappings in this map.

11. **clear():** Removes all of the mappings from this map.

12. **putAll(Map<? extends K, ? extends V> m):** Copies all of the mappings from the specified map to this map.

13. **getOrDefault(Object key, V defaultValue):** Returns the value to which the specified key is mapped, or defaultValue if this map contains no mapping for the key.

14. **forEach(BiConsumer<? super K, ? super V> action):** Performs the given action for each entry in this map until all entries have been processed or the action throws an exception.

15. **replace(K key, V value):** Replaces the entry for the specified key only if it is currently mapped to some value.

16. **compute(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction):** Attempts to compute a mapping for the specified key and its current mapped value (or null if there is no current mapping).

17. **computeIfAbsent(K key, Function<? super K, ? extends V> mappingFunction):** If the specified key is not already associated with a value (or is mapped to null), attempts to compute its value using the given mapping function and enters it into this map unless null.

18. **computeIfPresent(K key, BiFunction<? super K, ? super V, ? extends V> remappingFunction):** If the value for the specified key is present and non-null, attempts to compute a new mapping given the key and its current mapped value.

The `Map` interface is a cornerstone of Java's Collections Framework, and its methods provide a wide variety of operations to manipulate and interact with key-value data.

In addition to the methods mentioned previously, the `java.util.Map` interface also provides a few more methods for dealing with optional and default values, as well as methods for dealing with atomic operations:

19. **putIfAbsent(K key, V value):** If the specified key is not already associated with a value (or is mapped to null) associates it with the given value.

20. **remove(Object key, Object value):** Removes the entry for the specified key only if it is currently mapped to the specified value.

21. **replace(K key, V oldValue, V newValue):** Replaces the entry for the specified key only if currently mapped to the specified value.

22. **replaceAll(BiFunction<? super K, ? super V, ? extends V> function):** Replaces each entry's value with the result of invoking the given function on that entry until all entries have been processed or the function throws an exception.

These methods provide more control over how and when entries are added, updated, and removed from the map, and are especially useful in concurrent programming contexts, where they can be used to prevent race conditions.

Moreover, the `java.util.Map` interface has two nested interfaces:

1. **Entry<K,V>:** A map entry (key-value pair). The `Map.entrySet` method returns a collection-view of the map, whose elements are of this class.

2. **Entry<K,V>.comparingByKey():** Returns a comparator that compares `Map.Entry` in natural order on key.

3. **Entry<K,V>.comparingByValue():** Returns a comparator that compares `Map.Entry` in natural order on value.

The `Map.Entry` interface provides methods to access the key and value of an entry, as well as to set the value. Additionally, it has methods to compare entries by key or value, which can be useful for sorting and other operations.

Understanding these methods and how they interact with the `Map` interface can greatly enhance your ability to effectively and efficiently manipulate key-value data in Java.


How to create Map instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. How to create Map instances? Include the Map.of() factory method first.

Here's an overview of how to create `Map` instances, including the `Map.of()` factory method:

1. **Using `Map.of()` Factory Method (Java 9+)**:
   The `Map` interface provides a factory method called `of()` that allows you to create an immutable `Map` with a fixed number of entries. Here's an example:

   .. code-block:: java

        import java.util.Map;

        Map<String, Integer> map = Map.of("Apple", 1, "Banana", 2, "Orange", 3);

   In this example, a `Map` instance is created using the `Map.of()` factory method. It takes a sequence of key-value pairs as arguments and returns an immutable `Map` containing those entries.

2. **Using `HashMap`**:
   The `HashMap` class is a commonly used implementation of the `Map` interface. It provides a dynamic and unordered collection of key-value pairs. Here's an example:

   .. code-block:: java

        import java.util.Map;
        import java.util.HashMap;

        Map<String, Integer> map = new HashMap<>();
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Orange", 3);


   In this example, a `HashMap` instance is created by instantiating the `HashMap` class. Key-value pairs are added using the `put()` method, allowing for dynamic modification of the map.

3. **Using Other Map Implementations**:
   Java provides several other implementations of the `Map` interface, such as `TreeMap`, `LinkedHashMap`, and `ConcurrentHashMap`. Each implementation has unique characteristics and is suitable for specific use cases. Here's an example using `TreeMap`:

   .. code-block:: java

        import java.util.Map;
        import java.util.TreeMap;

        Map<String, Integer> map = new TreeMap<>();
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Orange", 3);

   In this example, a `TreeMap` instance is created by instantiating the `TreeMap` class. The `TreeMap` implementation provides a sorted map based on the natural ordering of the keys. These examples demonstrate different approaches to creating `Map` instances. You can use the `Map.of()` factory method for creating small immutable maps, or instantiate specific implementations like `HashMap`, `TreeMap`, or others based on your requirements.

4. **How use Map.of() or equivalent with pairs**:
   Note that `Map.of()` method can be error-prone because of the way it takes key-value pairs. A safer alternative is to use `Map.entry()` method which creates a single key-value pair. Then you can use `Map.ofEntries()` method to create a map from these entries.  Here is how you can use it:

   .. code-block:: java

        import java.util.Map;
        Map<String, Integer> map = Map.ofEntries(
            Map.entry("Apple", 1),
            Map.entry("Banana", 2),
            Map.entry("Orange", 3)
        );

   This approach is safer because you are grouping the key and its corresponding value together. It's clearer to see which keys are associated with which values, and it's harder to accidentally leave out a key or value.

Unit tests for the Map API
^^^^^^^^^^^^^^^^^^^^^^^^^^

Unit tests help validate the behavior of individual methods. Here's an example of how you might test the key methods of the `Map` interface using a `HashMap` as the implementing class. This example uses JUnit 5:

.. code-block:: java

    import org.junit.jupiter.api.Test;
    import java.util.HashMap;
    import java.util.Map;

    import static org.junit.jupiter.api.Assertions.*;

    class MapTest {

        @Test
        void testPut() {
            final Map<String, Integer> map = new HashMap<>();
            final var result = map.put("One", 1);
            assertNull(result);
            assertEquals(1, map.size());
        }

        @Test
        void testGet() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            final var result = map.get("One");
            assertNotNull(result);
            assertEquals(1, result);
        }

        @Test
        void testRemove() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            final var removed = map.remove("One");
            assertEquals(1, removed);
            assertTrue(map.isEmpty());
        }

        @Test
        void testClear() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            map.put("Two", 2);
            map.clear();
            assertTrue(map.isEmpty());
        }

        @Test
        void testSize() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            map.put("Two", 2);
            assertEquals(2, map.size());
        }

        @Test
        void testContainsKey() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            assertTrue(map.containsKey("One"));
            assertFalse(map.containsKey("Two"));
        }

        @Test
        void testContainsValue() {
            final Map<String, Integer> map = new HashMap<>();
            map.put("One", 1);
            assertTrue(map.containsValue(1));
            assertFalse(map.containsValue(2));
        }

        @Test
        void testIsEmpty() {
            final Map<String, Integer> map = new HashMap<>();
            assertTrue(map.isEmpty());
            map.put("One", 1);
            assertFalse(map.isEmpty());
        }

        // More tests should be written to cover other methods and edge cases
    }

Each of these tests instantiates a new `HashMap`, performs some operations on it, and then checks that the state of the map is as expected. These checks use methods like `assertEquals`, `assertTrue`, and `assertFalse` from JUnit to assert expected outcomes. If an assertion fails, JUnit will report a failure for that test, indicating that there's a bug in the code under test.

Note that unit tests should generally be written for each method in isolation and for interaction of methods, and should cover both common cases and edge cases. A full test suite for a `Map` implementation would have more tests than what's included here.


.. todo:: Briefly discuss O(log n) and give overview of the complexity classes familiar at this point.


Performance of Map API methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following table showcases the time and space complexity of the main methods in TreeMap, HashMap, and LinkedHashMap:

+----------------------+---------------+--------------+-------------------+
| Method               | TreeMap       | HashMap      | LinkedHashMap     |
+======================+===============+==============+===================+
| get(key)             | O(log n)      | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+
| put(key, value)      | O(log n)      | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+
| remove(key)          | O(log n)      | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+
| containsKey(key)     | O(log n)      | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+
| containsValue(value) | O(n)          | O(n)         | O(n)              |
+----------------------+---------------+--------------+-------------------+
| size()               | O(1)          | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+
| clear()              | O(1)          | O(1)         | O(1)              |
+----------------------+---------------+--------------+-------------------+

In this table, the time complexity of each method is represented using Big O notation, while the space complexity is notated as O(1) since the space required remains constant regardless of the input size.

Please note that the complexities provided here are general average case complexities. In some specific scenarios, the performance may deviate due to factors such as hash collisions or tree rebalancing in TreeMap. Additionally, the performance characteristics may vary depending on the specific usage patterns and the size of the map.

It's important to choose the appropriate map implementation based on the specific requirements and performance characteristics needed for your application.


Sample implementation
^^^^^^^^^^^^^^^^^^^^^

*Can you show a simple yet modern Java implementation class of the Map interface, pedagogically suitable for a CS2 audience (second computer science course)? The implementation doesn't have to be complete but should include the handful or so of essential methods.*

Absolutely, here's a simple pedagogically-oriented implementation of a Map using a backing array, suitable for a CS2 level audience. Note that this implementation doesn't handle resizing, hashing, or collision resolution - it's essentially a glorified associative list. This example uses local type inference (introduced in Java 10) and other modern Java features as per your request:

.. code-block:: java

    import java.util.Arrays;

    public class SimpleMap<K, V> {
        private static final int SIZE = 10;

        private static record Entry<K, V>(K key, V value) {}

        private final Entry<K, V>[] entries;
        private int count = 0;

        public SimpleMap() {
            @SuppressWarnings("unchecked")
            final var tmpEntries = (Entry<K, V>[]) new Entry[SIZE];
            this.entries = tmpEntries;
        }

        public V get(final K key) {
            for (final var entry : entries) {
                if (entry != null && entry.key().equals(key)) {
                    return entry.value();
                }
            }
            return null;
        }

        public void put(final K key, final V value) {
            if (count >= SIZE) {
                throw new IllegalStateException("Map is full");
            }
            for (var i = 0; i < count; i++) {
                if (entries[i].key().equals(key)) {
                    entries[i] = new Entry<>(key, value);
                    return;
                }
            }
            entries[count++] = new Entry<>(key, value);
        }

        public boolean containsKey(final K key) {
            for (final var entry : entries) {
                if (entry != null && entry.key().equals(key)) {
                    return true;
                }
            }
            return false;
        }

        @Override
        public String toString() {
            return Arrays.toString(entries);
        }
    }

The `SimpleMap` class maintains an array of `Entry` records, each of which holds a key-value pair. The `put()` method adds a new key-value pair to the map, or updates the value if the key is already present. The `get()` method retrieves a value by its key, and the `containsKey()` method checks if a key is in the map. 

This class provides a simple, tangible implementation of the Map interface, making it a great starting point for CS2 students. They could enhance this implementation by adding methods like `remove()`, `size()`, or `isEmpty()`. Later on, they could learn about more sophisticated implementations using hashing, linked lists (for collision resolution), and dynamic resizing.


Key takeaways
^^^^^^^^^^^^^

.. *Lists have a similarly limited key type (index range) as arrays. Can you think about a similar but more general structure?*

.. Apologies for the oversight. If you're looking for a more generalized data structure that can handle a wider range of key types beyond the index range of lists and arrays, a suitable option is the "Map" data structure.

Maps, also known as dictionaries or associative arrays, provide a key-value mapping, allowing you to associate values with unique keys. Unlike arrays and lists, which use integer indices, maps allow for a more diverse range of key types, including strings, objects, and custom types. This makes maps highly versatile and widely usable.

Here are some reasons why maps are a more general structure:

1. Key-Value Pairing: Maps store elements as key-value pairs, where each key is unique within the map. This allows for efficient retrieval and modification of values based on their corresponding keys.

2. Flexible Key Types: Maps support a wide range of key types, providing flexibility in choosing the most appropriate key type for your specific needs. Keys can be integers, strings, objects, or custom types.

3. Dynamic Size: Like lists, maps can dynamically grow or shrink as elements are added or removed. This makes them suitable for scenarios where the number of elements and their associated keys can change over time.

4. Efficient Retrieval: Maps provide fast lookup and retrieval of values based on their keys. The underlying implementation of maps utilizes hashing or other efficient lookup mechanisms, making them highly efficient for key-based operations.

5. Key-Value Association: Maps establish a direct association between keys and values, allowing you to easily retrieve, update, or remove values based on their corresponding keys.

6. Widely Supported: Maps are widely supported in programming languages and are available in various implementations with different features and performance characteristics.

By utilizing maps, you can store and access values based on a wide range of key types, offering greater flexibility and generality compared to structures like arrays or lists.


Sets
----

.. In the context of an ACM CS2 course (not including advanced CS7 topics), how would you describe a Set data structure, and what would be the motivation to use one?

A Set is a type of collection that stores unique elements - that is, no duplicates are allowed. It's akin to a mathematical set, which is an unordered collection of distinct objects. In many programming languages, including Java, the `Set` is a standard data structure, often provided as part of the language's standard library.

A Set can be used whenever you want to keep track of a group of items, but you don't care about their order, and you don't want any duplicates. This can be useful in a variety of circumstances. For example, imagine you're writing a program to analyze a document, and you want to know which unique words appear in the text. You could use a `Set` to store those words. Every time you encounter a new word, you add it to the `Set`. If the word is already in the `Set`, the `Set` remains unchanged - hence, no duplicates.

Another common use for a `Set` is to efficiently check for the presence of an item. For instance, you might have a `Set` of banned usernames for a forum, and you want to quickly check if a given username is in that `Set`. Since many Set implementations (like HashSet in Java) can check for the presence of an item in constant time, this operation is very efficient.

Also, a `Set` can be used to perform mathematical set operations, such as union (addition of two sets), intersection (common elements in two sets), and difference (elements present in one set but not the other).

Overall, a `Set` is a very handy data structure, especially when dealing with collections of unique elements where order is not significant.

.. Using modern Java, can you give a simple yet engaging and compelling example of using Set to solve an simple but interesting problem?

Example
^^^^^^^

Here's an example of how you might use a `Set` in Java to solve a simple problem: finding duplicate words in a sentence. This is an interesting use case because it shows off the unique-element property of the `Set`.

.. code-block:: java

    import java.util.HashSet;
    import java.util.Set;

    public class DuplicateWordsFinder {
        public static void main(final String[] args) {
            final var sentence = "Big big cats and little little dogs are great pets.";
            final var words = sentence.split("\\s+");
            final var uniqueWords = new HashSet<String>();
            final var duplicateWords = new HashSet<String>();

            for (final var word : words) {
                // Normalize word to ignore case of words while checking duplicates
                final var lowerCaseWord = word.toLowerCase();
                if (!uniqueWords.add(lowerCaseWord)) {
                    duplicateWords.add(lowerCaseWord);
                }
            }

            System.out.println("Duplicate words: " + duplicateWords);
        }
    }

In this example, we first split a sentence into individual words. We then iterate over these words, attempting to add each to the `uniqueWords` set. The `Set.add()` method returns `false` if the element was already in the set. Thus, if `add()` returns `false`, we know we've found a duplicate, and we add the word to the `duplicateWords` set. Finally, we print out the set of duplicate words.

The key advantage of using a `Set` in this situation is that it automatically handles the task of checking for duplicates. We don't need to write any code to compare each word to every other word - the `Set` does that for us. This makes the code simpler and more efficient.

The Java Set API
^^^^^^^^^^^^^^^^
.. What are the main methods of the Set interface in the Java API (version 17)?

The `java.util.Set` interface in Java provides a number of methods for working with collections of unique elements. As of Java 17, here are some of the key methods available:

1. **add(E e):** Adds the specified element to this set if it is not already present.

2. **remove(Object o):** Removes the specified element from this set if it is present.

3. **contains(Object o):** Returns true if this set contains the specified element.

4. **isEmpty():** Returns true if this set contains no elements.

5. **size():** Returns the number of elements in this set.

6. **clear():** Removes all of the elements from this set.

7. **iterator():** Returns an iterator over the elements in this set.

8. **toArray():** Returns an array containing all of the elements in this set.

9. **containsAll(Collection<?> c):** Returns true if this set contains all of the elements of the specified collection.

10. **addAll(Collection<? extends E> c):** Adds all of the elements in the specified collection to this set.

11. **removeAll(Collection<?> c):** Removes from this set all of its elements that are contained in the specified collection.

12. **retainAll(Collection<?> c):** Retains only the elements in this set that are contained in the specified collection.

In addition to these, the `Set` interface also inherits methods from the `Collection` interface, such as `stream()`, which returns a sequential `Stream` with this collection as its source, and `forEach(Consumer<? super E> action)`, which performs the given action for each element of the `Iterable` until all elements have been processed or the action throws an exception.

These methods provide a variety of ways to manipulate and interact with sets of unique data in Java, and understanding them is essential for effective use of the `Set` interface.

In addition to the methods previously described, `java.util.Set` inherits some important methods from the `java.util.Collection` interface, which include:

13. **equals(Object o):** Compares the specified object with this collection for equality. In other words, two sets are defined to be equal if they contain the same elements.

14. **hashCode():** Returns the hash code value for this collection. The hash code of a set is defined to be the sum of the hash codes of the elements in the set.

15. **removeIf(Predicate<? super E> filter):** Removes all of the elements of this collection that satisfy the given predicate. This can be used to remove elements based on a condition.

16. **parallelStream():** Returns a possibly parallel Stream with this collection as its source. This can be used for operations that can be executed concurrently to improve performance.

17. **spliterator():** Creates a Spliterator over the elements in this collection. A Spliterator can be used to partition off some of its elements as another Spliterator, supporting efficient parallel operations.

The `Set` interface doesn't have any methods specifically for accessing elements based on their position in the set because sets, unlike lists, are not inherently ordered collections. 

Some implementations, like `LinkedHashSet`, do maintain an order (insertion-order in this case), but this is not a contractual characteristic of the `Set` interface itself.

Also, the Set interface has three main implementation classes in the Java Collections Framework: `HashSet`, `LinkedHashSet`, and `TreeSet`, each with its own characteristics in terms of order, performance and allowing null elements.


How to create Set instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. How to create Set instances? Include the Set.of() factory method first.

Certainly! Here's an overview of how to create `Set` instances, including the `Set.of()` factory method:

1. **Using `Set.of()` Factory Method (Java 9+)**:
   The `Set` interface provides a factory method called `of()` that allows you to create an immutable `Set` with a fixed number of elements. Here's an example:

   .. code-block:: java

        import java.util.Set;

        Set<String> set = Set.of("Apple", "Banana", "Orange");

   In this example, a `Set` instance is created using the `Set.of()` factory method. It takes a sequence of elements as arguments and returns an immutable `Set` containing those elements.

2. **Using `HashSet`**:
   The `HashSet` class is a commonly used implementation of the `Set` interface. It provides a dynamic and unordered collection of unique elements. Here's an example:

   .. code-block:: java

        import java.util.Set;
        import java.util.HashSet;

        Set<String> set = new HashSet<>();
        set.add("Apple");
        set.add("Banana");
        set.add("Orange");

   In this example, a `HashSet` instance is created by instantiating the `HashSet` class. Elements are added using the `add()` method, allowing for dynamic modification of the set.

3. **Using Other Set Implementations**:
   Java provides several other implementations of the `Set` interface, such as `TreeSet`, `LinkedHashSet`, and `EnumSet`. Each implementation has unique characteristics and is suitable for specific use cases. Here's an example using `TreeSet`:

   .. code-block:: java

        import java.util.Set;
        import java.util.TreeSet;

        Set<String> set = new TreeSet<>();
        set.add("Apple");
        set.add("Banana");
        set.add("Orange");

   In this example, a `TreeSet` instance is created by instantiating the `TreeSet` class. The `TreeSet` implementation provides a sorted set based on the natural ordering of the elements.

These examples demonstrate different approaches to creating `Set` instances. You can use the `Set.of()` factory method for creating small immutable sets, or instantiate specific implementations like `HashSet`, `TreeSet`, or others based on your requirements.


Unit tests for the Set API
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. Can you write unit tests to show that each method of the Java 17 java.util.Set API does what is intended?

Here's how you could write unit tests for the `Set` interface using `HashSet` as the implementing class. We'll use JUnit 5 for these tests.

.. code-block:: java

    import org.junit.jupiter.api.Test;

    import java.util.HashSet;
    import java.util.Set;

    import static org.junit.jupiter.api.Assertions.*;

    class SetTest {
        @Test
        void testAdd() {
            final Set<String> set = new HashSet<>();
            final boolean result = set.add("One");
            assertTrue(result);
            assertEquals(1, set.size());
        }

        @Test
        void testAddDuplicate() {
            final Set<String> set = new HashSet<>();
            set.add("One");
            final boolean result = set.add("One");  // should not add duplicate
            assertFalse(result);
            assertEquals(1, set.size());
        }

        @Test
        void testRemove() {
            final Set<String> set = new HashSet<>();
            set.add("One");
            final boolean result = set.remove("One");
            assertTrue(result);
            assertTrue(set.isEmpty());
        }

        @Test
        void testClear() {
            final Set<String> set = new HashSet<>();
            set.add("One");
            set.add("Two");
            set.clear();
            assertTrue(set.isEmpty());
        }

        @Test
        void testSize() {
            final Set<String> set = new HashSet<>();
            set.add("One");
            set.add("Two");
            assertEquals(2, set.size());
        }

        @Test
        void testContains() {
            final Set<String> set = new HashSet<>();
            set.add("One");
            assertTrue(set.contains("One"));
            assertFalse(set.contains("Two"));
        }

        @Test
        void testIsEmpty() {
            final Set<String> set = new HashSet<>();
            assertTrue(set.isEmpty());
            set.add("One");
            assertFalse(set.isEmpty());
        }
        
        // More tests should be written to cover other methods and edge cases
    }

In these tests, we're checking that each of the methods works as expected: `add` adds an item and returns `true` if it wasn't already present, `remove` removes an item and returns `true` if it was present, `clear` removes all items, `size` returns the number of items, `contains` checks for the presence of an item, and `isEmpty` checks if the set is empty.

Note that for a complete set of tests, you would want to test other methods in the `Set` interface, and you would want to test edge cases and interactions between methods. These tests are intended to be a starting point and an illustrative example.


Performance of Set API methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following table showcases the time and space complexity of the main methods in TreeSet, HashSet, and LinkedHashSet:

+----------------------+--------------+--------------+-------------------+
| Method               | TreeSet      | HashSet      | LinkedHashSet     |
+======================+==============+==============+===================+
| add(element)         | O(log n)     | O(1)         | O(1)              |
+----------------------+--------------+--------------+-------------------+
| remove(element)      | O(log n)     | O(1)         | O(1)              |
+----------------------+--------------+--------------+-------------------+
| contains(element)    | O(log n)     | O(1)         | O(1)              |
+----------------------+--------------+--------------+-------------------+
| size()               | O(1)         | O(1)         | O(1)              |
+----------------------+--------------+--------------+-------------------+
| clear()              | O(1)         | O(1)         | O(1)              |
+----------------------+--------------+--------------+-------------------+

In this table, the time complexity of each method is represented using Big O notation, while the space complexity is notated as O(1) since the space required remains constant regardless of the input size.

Please note that the complexities provided here are general average case complexities. In some specific scenarios, the performance may deviate due to factors such as hash collisions or tree rebalancing in TreeSet.

When choosing a specific set implementation, consider the specific requirements of your application and the performance characteristics needed. TreeSet is suitable when you need elements to be sorted in a specific order. HashSet is ideal for general-purpose sets with constant-time operations. LinkedHashSet maintains insertion order while providing constant-time operations.


Sample implementation
^^^^^^^^^^^^^^^^^^^^^

.. Can you show a simple yet modern Java implementation class of the Map interface, pedagogically suitable for a CS2 audience (second computer science course)? The implementation doesn't have to be complete but should include the handful or so of essential methods.

Sure, here is a simple pedagogically-oriented implementation of a Set using a backing array. This implementation uses local type inference (introduced in Java 10) and other modern Java features. Please note that this implementation is for learning purposes and doesn't handle resizing, nor does it provide the performance benefits of a true `HashSet` or `TreeSet`:

.. code-block:: java

    import java.util.Arrays;
    import java.util.Iterator;
    import java.util.NoSuchElementException;

    public class SimpleSet<E> implements Iterable<E> {
        private static final int SIZE = 10;

        private final E[] elements;
        private int count = 0;

        @SuppressWarnings("unchecked")
        public SimpleSet() {
            this.elements = (E[]) new Object[SIZE];
        }

        public void add(final E e) {
            if (count >= SIZE) {
                throw new IllegalStateException("Set is full");
            }
            if (contains(e)) {
                return; // No duplicates allowed in a Set
            }
            elements[count++] = e;
        }

        public boolean contains(final E e) {
            for (final var element : elements) {
                if (e.equals(element)) {
                    return true;
                }
            }
            return false;
        }

        @Override
        public Iterator<E> iterator() {
            return new Iterator<>() {
                private int currentIndex = 0;

                @Override
                public boolean hasNext() {
                    return currentIndex < count;
                }

                @Override
                public E next() {
                    if (!hasNext()) {
                        throw new NoSuchElementException();
                    }
                    return elements[currentIndex++];
                }
            };
        }

        @Override
        public String toString() {
            final var presentElements = Arrays.copyOf(elements, count);
            return Arrays.toString(presentElements);
        }
    }

The `SimpleSet` class maintains an array of elements. The `add(E e)` method adds a new element to the set only if it is not already present. The `contains(E e)` method checks if an element is present in the set. The class also implements the `Iterable<E>` interface, allowing for enhanced for-loop iteration over the elements. Note the use of the `iterator()` method to provide a custom iterator for the set.

While useful for pedagogical purposes, this implementation lacks the performance characteristics of the standard Java Set implementations (e.g., `HashSet` and `TreeSet`). As the collection grows, operations can become slower because each operation needs to iterate over every element in the array. A more complex data structure, such as a hash table or a tree, can provide better performance by organizing the data in a way that allows operations to complete more quickly.


Bitsets
^^^^^^^

.. In a way that is suitable for a CS2 audience, please describe and motivate the use of Java 17's BitSet, provide a simple example, and briefly describe the essential elements of its implementation.

A `BitSet` in Java is a special kind of array that holds bit values. That is, each element in a `BitSet` is either a 0 or a 1. This can be incredibly useful and efficient when you need to store large sets of boolean values because a `BitSet` is more memory-efficient than other data structures, such as arrays or `ArrayList<Boolean>`, for instance.

`BitSet` is also useful when you need to perform bitwise operations (AND, OR, XOR, etc.) on a set of binary values. This can be beneficial in certain types of problems such as data compression, graphics, and searching algorithms.

Here's a simple example of a `BitSet` in action:

.. code-block:: java

    import java.util.BitSet;

    public class BitSetExample {
        public static void main(final String[] args) {
            final var bits = new BitSet(5);

            // Set bits at index 0 and 2
            bits.set(0);
            bits.set(2);

            System.out.println("BitSet: " + bits);
            System.out.println("Bit at index 2: " + bits.get(2));
            System.out.println("Bit at index 1: " + bits.get(1));
            System.out.println("Size of BitSet: " + bits.size());
        }
    }

When you run this code, it prints:

.. code-block:: java

    BitSet: {0, 2}
    Bit at index 2: true
    Bit at index 1: false
    Size of BitSet: 64

This example creates a `BitSet` and sets the bits at indices 0 and 2. The `BitSet`'s `toString()` method shows which indices are set to true. We also demonstrate the use of the `get(int index)` method to check the value of a specific bit.

One important thing to note is that the `size()` method returns the "logical size" of the `BitSet` which is "the index of the highest set bit plus one". So, in this case, despite initializing the `BitSet` with a size of 5, the size returned is 64 as the `BitSet` internally allocates memory in multiples of 64 bits (the size of a `long`).

Regarding its implementation, a `BitSet` internally uses a dynamic array (`long[]`) to hold the bits, which are represented as long integers (64-bit). Each `long` value represents 64 bits, with the 0th bit referring to the least significant bit of the `long` and the 63rd bit referring to the most significant bit. The `long[]` array is expanded as needed, ensuring the `BitSet` can grow to accommodate any bit index. The `BitSet` class also provides many methods for performing bitwise operations on the bits. This, combined with its dynamic size, makes `BitSet` a flexible tool for efficient bit manipulation.


Key takeaways
^^^^^^^^^^^^^

From a discussion of `Set`, `BitSet`, and the comparison of `Set` with `Map`, here are the key takeaways:

1. **Uniqueness and Element-based Operations**: Both `Set` and `BitSet` are used to store a collection of unique elements. The primary purpose of a `Set` is to ensure that each element is unique within the set, while a `BitSet` is a specialized implementation that represents a set of bits, typically used for efficient storage and manipulation of binary data. Both data structures provide operations for adding, removing, and querying elements.

2. **Set vs. Map**: The main difference between a `Set` and a `Map` is that a `Set` stores only the unique elements, while a `Map` stores key-value pairs. In other words, a `Set` is a collection of distinct elements, whereas a `Map` associates each element with a unique key. `Set` is useful when you only need to store and query unique elements, while `Map` is suitable for scenarios where you need to store and access values associated with specific keys.

3. **Membership Testing and Efficient Operations**: Both `Set` and `BitSet` offer efficient membership testing operations. They allow you to check whether an element is present in the set or not, providing a quick way to determine membership without iterating through the entire collection. `BitSet` offers additional capabilities for performing bitwise operations, making it particularly useful when dealing with binary data and bit-level manipulation.

4. **Performance and Space Efficiency**: `BitSet` can be more space-efficient than `Set`, especially when dealing with a large number of elements. It uses a compact internal representation of bits, which can save memory compared to storing individual objects in a `Set`. However, this space efficiency comes at the cost of increased complexity and limited support for non-integer elements.

These key takeaways highlight the uniqueness and element-based operations provided by `Set` and `BitSet`. They also emphasize the difference between `Set` and `Map`, with `Set` focusing on unique elements and `Map` associating elements with unique keys. Furthermore, the efficient membership testing and space efficiency of `BitSet` are mentioned as distinguishing factors.


Stacks
------

.. Can you write a complete CS2 textbook chapter on the Stack ADT with the following elements?

.. Chapter 7: The Stack Abstract Data Type - Lifting the Weight off Your Programming Shoulders

The Stack Abstract Data Type (ADT) is a collection that follows the Last-In-First-Out (LIFO) principle. It represents a stack of elements, where the most recently added element is the first one to be removed. The Stack ADT is widely used in various applications, offering an intuitive and efficient way to manage data.

Imagine you're working on a text editor, and you want to implement an "Undo" functionality that allows users to revert their recent changes. A stack can be the perfect solution. As users perform actions, such as typing, deleting, or formatting, each action can be pushed onto the stack. When the user triggers the "Undo" command, the most recent action is popped from the stack, undoing the corresponding change.


Example: Text Editor Undo Functionality
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let's consider a simple example of implementing the "Undo" functionality using a stack:

.. code-block:: java

    Deque<String> undoStack = new ArrayStack<>();

    // User performs actions
    undoStack.push("Formatting change");
    undoStack.push("Deletion");
    undoStack.push("Typing");

    // User triggers "Undo"
    final var lastAction = undoStack.pop();

In this example, we create a stack called `undoStack` using the `ArrayStack` implementation. As the user performs actions, such as formatting changes, deletions, and typing, each action is pushed onto the stack. When the "Undo" command is triggered, the most recent action is popped from the stack, allowing for the undoing of changes.


Example: Balancing Parentheses
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Let's explore a practical example where the Stack ADT proves its usefulness. Consider the task of checking whether a given string containing parentheses is balanced or not. We can use a stack to solve this problem efficiently by tracking the opening and closing parentheses.

.. code-block:: java

    public boolean isBalanced(String input) {
        Deque<Character> stack = new ArrayDeque<>();

        for (final var c : input.toCharArray()) {
            if (c == '(') {
                stack.push(c);
            } else if (c == ')') {
                if (stack.isEmpty() || stack.pop() != '(') {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }

In this example, we use a stack to check the balance of parentheses in the `isBalanced` method. The method iterates over each character in the input string. If an opening parenthesis is encountered, it is pushed onto the stack. If a closing parenthesis is encountered, it is matched with the corresponding opening parenthesis from the stack. If the parentheses are balanced, the stack should be empty by the end.


Main Stack API Methods
^^^^^^^^^^^^^^^^^^^^^^

The Stack ADT provides several essential methods to manipulate the stack:

- `push(element)`: Adds the specified element to the top of the stack.
- `pop()`: Removes and returns the element at the top of the stack.
- `peek()`: Returns the element at the top of the stack without removing it.
- `isEmpty()`: Checks if the stack is empty.
- `size()`: Returns the number of elements in the stack.
- `clear()`: Removes all elements from the stack.


How to Instantiate a Stack
^^^^^^^^^^^^^^^^^^^^^^^^^^

In Java 17, you can instantiate a stack by utilizing the specific interfaces and implementations available in the `java.util` package. Here are a few common approaches:

1. Using `Deque` Interface with `ArrayDeque` Implementation:
   
   .. code-block:: java

       Deque<String> stack = new ArrayDeque<>();

2. Using `LinkedList` Class:

   .. code-block:: java

       Deque<String> stack = new LinkedList<>();


In these examples, we use the `Deque` interface, which stands for "double-ended queue," to represent a stack. Both `ArrayDeque` and `LinkedList` implement the `Deque` interface and can be used interchangeably as stack implementations.

By utilizing the `Deque` interface, you can leverage the stack-specific methods such as `push`, `pop`, and `peek`, while also having access to additional functionality provided by the `Deque` interface, such as queue-like operations.

Choosing between `ArrayDeque` and `LinkedList` depends on specific requirements. `ArrayDeque` typically provides better performance for most stack operations due to its array-based implementation, while `LinkedList` might be more suitable if you need efficient insertion and removal at both ends.

Using the appropriate stack implementation ensures compatibility with the Java 17 API and enables you to benefit from the standardized stack behavior and functionality provided by the `Deque` interface.


Unit Tests for the Stack API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To ensure the correctness of your stack implementation, it is crucial to write comprehensive unit tests for each of the main API methods. Let's explore how you can effectively test these methods:

Testing `push(element)`
"""""""""""""""""""""""

.. code-block:: java

    @Test
    void testPush() {
        Deque<Integer> stack = new ArrayDeque<>();
        
        stack.push(10);
        stack.push(20);
        stack.push(30);

        assertEquals(30, stack.peek());
        assertFalse(stack.isEmpty());
        assertEquals(3, stack.size());
    }

In this test, we create a stack and push three elements onto it. We then assert that the top element is 30, the stack is not empty, and its size is 3.

Testing `pop()`
"""""""""""""""

.. code-block:: java

    @Test
    void testPop() {
        Deque<String> stack = new ArrayDeque<>();

        stack.push("Apple");
        stack.push("Banana");
        stack.push("Orange");

        var poppedElement = stack.pop();

        assertEquals("Orange", poppedElement);
        assertEquals("Banana", stack.peek());
        assertEquals(2, stack.size());
    }

In this test, we create a stack, push three elements onto it, and then pop the top element. We assert that the popped element is "Orange", the new top element is "Banana", and the stack size is reduced to 2.

Testing `peek()`
""""""""""""""""

.. code-block:: java

    @Test
    void testPeek() {
        Deque<Double> stack = new ArrayDeque<>();

        stack.push(3.14);
        stack.push(2.71);
        stack.push(1.618);

        assertEquals(1.618, stack.peek());
        assertEquals(3, stack.size());
    }

In this test, we create a stack, push three elements onto it, and then peek at the top element. We assert that the peeked element is 1.618 and that the stack size remains unchanged.


Testing `isEmpty()`
"""""""""""""""""""

.. code-block:: java

    @Test
    void testIsEmpty() {
        Deque<String> stack = new ArrayDeque<>();

        assertTrue(stack.isEmpty());

        stack.push("Java");
        assertFalse(stack.isEmpty());

        stack.pop();
        assertTrue(stack.isEmpty());
    }

In this test, we create a stack and verify its empty state at different stages. We assert that the stack is initially empty, becomes non-empty after pushing an element, and becomes empty again after popping all elements.


Testing `size()`
""""""""""""""""

.. code-block:: java

    @Test
    void testSize() {
        Deque<Integer> stack = new ArrayDeque<>();

        assertEquals(0, stack.size());

        stack.push(5);
        stack.push(10);
        stack.push(15);

        assertEquals(3, stack.size());

        stack.pop();
        stack.pop();

        assertEquals(1, stack.size());
    }

In this test, we create a stack, add elements to it, and verify the size at different stages. We assert that the initial size is 0, increases as elements are pushed, and decreases as elements are popped.

By writing comprehensive unit tests for each of the main stack API methods, you can ensure that your implementation behaves as expected and handles different scenarios correctly.


Performance of Stack API methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The time and space complexity of the main methods in the standard Java 17 implementation of a Stack (utilizing an `ArrayDeque` or `LinkedList`) is as follows:

- `push(element)`: O(1) time complexity on average. Amortized constant time complexity is achieved when the underlying array doesn't require resizing. The space complexity is O(1) since it only requires adding an element to the internal array.
- `pop()`: O(1) time complexity. Removing an element from the top of the stack takes constant time, regardless of the size of the stack. The space complexity is O(1) since it only requires removing an element from the internal array.
- `peek()`: O(1) time complexity. Accessing the top element of the stack is a constant time operation. The space complexity is O(1) since it does not modify the internal array.
- `isEmpty()`: O(1) time complexity. Checking if the stack is empty takes constant time. The space complexity is O(1) since it does not modify the internal array.
- `size()`: O(1) time complexity. Determining the size of the stack takes constant time. The space complexity is O(1) since it does not modify the internal array.

It's important to note that the time complexity provided here represents the average and amortized case complexities. In rare cases, certain operations might require resizing the underlying array, resulting in a higher time complexity.

The space complexity of the standard Java 17 implementation is O(n), where n is the number of elements in the stack. However, since we are analyzing the complexity of individual methods, we consider the space complexity as O(1) since these methods do not consume additional space proportional to the input size.

Please keep in mind that these complexities apply to the standard Java 17 implementation of the Stack, specifically utilizing the `ArrayDeque` or `LinkedList` class. Other custom implementations or variations may have different complexities.


Sample implementation
^^^^^^^^^^^^^^^^^^^^^

Here's a simple implementation of the Stack ADT as a generic class based on arrays:

.. code-block:: java

    public class Stack<E> {
        private Object[] stack;
        private int top;
        private static final int DEFAULT_CAPACITY = 10;

        public Stack() {
            stack = new Object[DEFAULT_CAPACITY];
            top = -1;
        }

        public boolean isEmpty() {
            return top == -1;
        }

        public boolean isFull() {
            return top == stack.length - 1;
        }

        public void push(E element) {
            if (isFull()) {
                resizeStack();
            }
            stack[++top] = element;
        }

        public E pop() {
            if (isEmpty()) {
                throw new RuntimeException("Stack is empty");
            }
            return (E) stack[top--];
        }

        public E peek() {
            if (isEmpty()) {
                throw new RuntimeException("Stack is empty");
            }
            return (E) stack[top];
        }

        public int size() {
            return top + 1;
        }

        private void resizeStack() {
            int newCapacity = stack.length * 2;
            Object[] newStack = new Object[newCapacity];
            System.arraycopy(stack, 0, newStack, 0, stack.length);
            stack = newStack;
        }
    }

In this revised implementation, the `Stack` class is now a generic class, allowing you to create stacks of any type. The key methods and functionalities remain the same as in the previous implementation.

Note that when accessing elements from the stack array, we cast them to the generic type `E` using `(E)` to ensure type safety. Additionally, the stack array is initially created with a default capacity, but it dynamically resizes when it becomes full using the `resizeStack()` method.

This updated implementation allows you to create stacks of various types and provides a more flexible and reusable stack ADT.


Key takeaways
^^^^^^^^^^^^^

- The Stack ADT follows the Last-In-First-Out (LIFO) principle.
- It is commonly used for managing undo functionality, function call tracking, expression evaluation, and more.
- Important methods of the Stack ADT include `push`, `pop`, `peek`, `isEmpty`, `size`, and `clear`.
- Stacks can be instantiated using array-based or linked list-based implementations.
- The Stack ADT offers an intuitive way to manage data and solve various programming problems efficiently.

Understanding the Stack ADT and its key properties empowers programmers to leverage its benefits in different applications, simplifying complex operations and improving overall code organization.


Queues
------

.. Hi, do you know anything about queues in the context of an ACM CS2 introductory data structures course focusing on linear data structures.

.. Yes, definitely. 

A queue is a type of linear data structure that follows a specific order in which the operations are performed. The order is First In First Out (FIFO). This means that the data item that's been in the queue the longest is the first one to be removed, and when a new data item is added, it goes to the end of the queue.

This is analogous to a real-life queue of people – people join the end of the queue and leave from the front. For example, in a line at a coffee shop, the first person who gets in line is the first person to get served and leave the line.


Example
^^^^^^^

Consider a scenario where you are building a ticketing system for an event. Users line up to purchase tickets, and you need to manage their requests in the order they arrive. A queue can be an excellent solution. As users join the line, their requests are enqueued. When it's time to process the requests, each user is dequeued, ensuring fairness and maintaining the order of requests.

.. code-block:: java

    Queue<String> ticketQueue = new LinkedList<>();

    // Users join the line
    ticketQueue.add("User1");
    ticketQueue.add("User2");
    ticketQueue.add("User3");

    // Processing requests
    var firstUser = ticketQueue.remove();

In this example, we create a queue called ticketQueue using the LinkedList implementation. As users join the ticket line, their names are added to the queue using the add() method. When it's time to process the ticket requests, the first user is dequeued from the queue using the remove() method, ensuring that the requests are handled in the order they arrived.


Main Queue API Methods
^^^^^^^^^^^^^^^^^^^^^^

The Queue ADT provides several essential methods to manipulate the queue:

- `add(element)`: Adds the specified element to the end of the queue.
- `remove()`: Removes and returns the element at the front of the queue.
- `element()`: Returns the element at the front of the queue without removing it.
- `offer(element)`: Adds the specified element to the end of the queue (returns true if successful).
- `poll()`: Removes and returns the element at the front of the queue (returns null if empty).
- `peek()`: Returns the element at the front of the queue without removing it (returns null if empty).
- `isEmpty()`: Checks if the queue is empty.
- `size()`: Returns the number of elements in the queue.
- `clear()`: Removes all elements from the queue.


How to Instantiate a Queue
^^^^^^^^^^^^^^^^^^^^^^^^^^

In Java 17, you can instantiate a queue using specific interfaces and implementations from the `java.util` package. Here are a few common approaches:

1. Using `Queue` Interface with `LinkedList` Implementation:
   ```java
   Queue<String> queue = new LinkedList<>();
   ```

2. Using `ArrayDeque` Class:
   ```java
   Queue<String> queue = new ArrayDeque<>();
   ```

3. Using `PriorityQueue` Class (for priority-based queues):
   ```java
   Queue<String> queue = new PriorityQueue<>();
   ```

In these examples, we use the `Queue` interface to represent a queue. Both `LinkedList` and `ArrayDeque` implement the `Queue` interface and can be used interchangeably as queue implementations. The `PriorityQueue` class provides additional functionality for priority-based queues, where elements are ordered based on a specified priority.

Using the appropriate queue implementation ensures compatibility with the Java 17 API and enables you to benefit from the standardized queue behavior and functionality provided by the `Queue` interface.


Unit tests for the Queue API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. Can you show me how to use each of the main operations in isolation?  Use random number/data generation instead of hard-coding values.

.. response: longer example that didn't seem to add much to the one above

.. Can you write unit tests to show that each of the main queue operations does what is intended?

Sure, I can provide a simple example using JUnit, which is the most common framework for writing unit tests in Java. In this example, we will test each of the main operations of a `Queue` using a `LinkedList`, which is one of Java's built-in `Queue` implementations. Each test method corresponds to one of the operations we discussed:

.. code-block:: java

    import org.junit.jupiter.api.*;
    import java.util.*;

    import static org.junit.jupiter.api.Assertions.*;

    public class QueueTest {
        private Queue<Integer> queue;
        private static final int SIZE = 10;

        @BeforeEach
        public void setup() {
            queue = new LinkedList<>();
            for (var i = 0; i < SIZE; i++) {
                queue.add(i);
            }
        }

        @Test
        public void testAdd() {
            assertTrue(queue.add(SIZE + 1));
            assertEquals(SIZE + 1, queue.size());
        }

        @Test
        public void testOffer() {
            assertTrue(queue.offer(SIZE + 1));
            assertEquals(SIZE + 1, queue.size());
        }

        @Test
        public void testRemove() {
            for (var i = 0; i < SIZE; i++) {
                assertEquals(i, queue.remove());
            }
            assertThrows(NoSuchElementException.class, () -> queue.remove());
        }

        @Test
        public void testPoll() {
            for (var i = 0; i < SIZE; i++) {
                assertEquals(i, queue.poll());
            }
            assertNull(queue.poll());
        }

        @Test
        public void testElement() {
            assertEquals(0, queue.element());
            queue.clear();
            assertThrows(NoSuchElementException.class, () -> queue.element());
        }

        @Test
        public void testPeek() {
            assertEquals(0, queue.peek());
            queue.clear();
            assertNull(queue.peek());
        }

        @Test
        public void testSize() {
            assertEquals(SIZE, queue.size());
        }

        @Test
        public void testIsEmpty() {
            assertFalse(queue.isEmpty());
            queue.clear();
            assertTrue(queue.isEmpty());
        }

        @Test
        public void testClear() {
            queue.clear();
            assertTrue(queue.isEmpty());
        }

        @Test
        public void testContains() {
            assertTrue(queue.contains(0));
            assertFalse(queue.contains(SIZE + 1));
        }
    }

Each test method uses assertions to check that the operation being tested has the expected effect. For example, the `testAdd` method adds an element to the queue and then checks that the size of the queue has increased by 1. The `testRemove` method removes elements from the queue and then checks that the removed elements are what we expect, and that trying to remove from an empty queue throws a `NoSuchElementException`.

In order to set up the state before each test, I've used the `@BeforeEach` annotation, which runs the setup method before each individual test. In this case, the setup method initializes a queue with the numbers 0 to 9.

Remember that you'll need to have JUnit in your project classpath to run these tests. If you're using a build tool like Maven or Gradle, you can add JUnit as a dependency in your build file. If you're not using a build tool, you can download JUnit and add it to your project classpath manually.


Performance of the main Queue API methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here are the time and space complexities for the main methods in the standard Java 17 implementations of Queue (`ArrayDeque` and `LinkedList`), along with a brief rationale for each method's time complexity:

- `add(element)` / `offer(element)`: O(1) time complexity. Adding an element to the end of the queue takes constant time as it involves inserting the element into the underlying data structure. The space complexity is O(1).

- `remove()` / `poll()`: O(1) time complexity. Removing and returning the element from the front of the queue takes constant time. The space complexity is O(1).

- `element()` / `peek()`: O(1) time complexity. Accessing the element at the front of the queue without removing it takes constant time. The space complexity is O(1).

- `isEmpty()`: O(1) time complexity. Checking if the queue is empty takes constant time. The space complexity is O(1).

- `size()`: O(1) time complexity. Determining the size of the queue takes constant time. The space complexity is O(1).

These complexities are applicable to the standard Java 17 implementations of `ArrayDeque` and `LinkedList`. The time complexities are derived from the inherent design and data structures used in the implementations, ensuring efficient operations for these methods. The space complexities are considered O(1) as they do not consume additional space proportional to the input size.

It's important to note that these complexities represent the average case complexities. Certain edge cases or specific usage scenarios may exhibit different performance characteristics.


Sample implementation
^^^^^^^^^^^^^^^^^^^^^

Here is a simple Queue implementation using arrays. This version has a fixed capacity and implements the essential methods: `add`, `remove`, `peek`, and `size`.

.. code-block:: java

    public class ArrayQueue<E> {
        private Object[] elements;
        private int front;
        private int back;
        private int size;
        private static final int DEFAULT_CAPACITY = 10;

        public ArrayQueue() {
            elements = new Object[DEFAULT_CAPACITY];
            front = 0;
            back = -1;
            size = 0;
        }

        public void add(final E element) {
            if (size == elements.length) {
                throw new IllegalStateException("Queue is full");
            }
            back = (back + 1) % elements.length;
            elements[back] = element;
            size++;
        }

        public E remove() {
            if (size == 0) {
                throw new IllegalStateException("Queue is empty");
            }
            final var element = (E) elements[front];
            elements[front] = null; // to help garbage collector
            front = (front + 1) % elements.length;
            size--;
            return element;
        }

        public E peek() {
            if (size == 0) {
                throw new IllegalStateException("Queue is empty");
            }
            return (E) elements[front];
        }

        public int size() {
            return size;
        }

        public boolean isEmpty() {
            return size == 0;
        }
    }

This `ArrayQueue` class uses a circular array to store its elements. The `front` and `back` indices keep track of where to dequeue and enqueue elements, and they wrap around to the start of the array when they reach the end. The `size` field keeps track of the number of elements currently in the queue.

This implementation throws an exception if you try to enqueue an element into a full queue or dequeue an element from an empty queue. In a real-world application, you might want to have the queue automatically expand its capacity when it gets full, but that's a bit more complicated and might be better suited for a more advanced course.


Key takeaways
^^^^^^^^^^^^^

.. Please summarize the key takeaways of our discussion of the queue ADT.

- The Queue ADT follows the First-In-First-Out (FIFO) principle.
- It is commonly used for managing tasks, message processing, event handling, and more.
- Important methods of the Queue ADT include `add`, `remove`, `element`, `offer`, `poll`, `peek`, `isEmpty`, `size`, and `clear`.
- Queues can be instantiated using `LinkedList`, `ArrayDeque`, or `PriorityQueue` based on specific requirements.
- The Queue ADT ensures fairness, preserves order, and provides efficient data management capabilities.

Understanding the Queue ADT and its key properties empowers programmers to utilize queues effectively in various applications, ensuring proper order and efficient processing of elements.


A unified view of restricted-access data structures
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you specifically want to refer to data structures like stacks and queues which follow particular kinds of insertion and removal patterns (Last-In-First-Out for stacks and First-In-First-Out for queues), a term often used is "Restricted Access Data Structures". These structures restrict access to their elements based on specific rules, unlike arrays or lists which allow access to any element at any time. 

But keep in mind that the term "Restricted Access Data Structures" isn't a widely recognized standard term, and its meaning could vary depending on the context or source. The usage and understanding of these terminologies can differ slightly between different textbooks, resources, or educators.

The `Collections.asLifoQueue` method is used to create a view of a `Deque` (double-ended queue) as a Last-In-First-Out (LIFO) `Queue`. It means that you can use a `Deque` like a `Stack`, but still treat it as a `Queue`. The `Deque` interface, among other things, provides methods for inserting, removing, and inspecting elements at both ends of the `Deque`.

The `asLifoQueue` method is often used in algorithms and data structures where you want a stack-like behavior but need to use the `Queue` interface. One common use-case might be a depth-first search algorithm, where you want to explore the "deepest" nodes in a tree or graph first, which can be implemented by adding new nodes to the front of the `Deque` and always processing the first node in the `Deque`.

Here's a simple example of using `Collections.asLifoQueue`:

.. code-block:: java

    import java.util.ArrayDeque;
    import java.util.Collections;
    import java.util.Queue;

    public class LifoQueueExample {
        public static void main(final String[] args) {
            final ArrayDeque<Integer> deque = new ArrayDeque<>();
            final Queue<Integer> queue = Collections.asLifoQueue(deque);

            queue.add(1);
            queue.add(2);
            queue.add(3);
            
            while (!queue.isEmpty()) {
                System.out.println(queue.remove());
            }
        }
    }

When you run this code, it will print:

.. code-block:: 

    3
    2
    1

This demonstrates that the `Queue` is acting like a stack, with elements being removed in last-in, first-out order.

The `Collections.asLifoQueue` method is useful when you have an existing `Deque` implementation and need to work with it as a LIFO queue. It provides a convenient way to adapt the `Deque` interface to the `Queue` interface with LIFO behavior. This can be beneficial in scenarios where you need LIFO functionality, such as implementing a stack or handling undo/redo operations.


Putting everything together: maze solver
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. todo:: extended example


Recursion
---------

.. User: Hi, assuming you’re familiar with recursion in the context of an ACM CS2 course, could you please motivate and introduce me to the concept, provide a succinct definition?

Recursion is a fundamental concept in computer science that provides a powerful and versatile way of solving problems. 
It’s a method of solving a problem where the solution depends on solutions to smaller instances of the same problem.

Recursion can make code cleaner and easier to understand by reducing complex problems into simpler sub-problems. In many cases, recursive approaches can be more intuitive than their iterative counterparts.

For example, consider a file system on a computer. 
If you wanted to find all files in a directory and all of its subdirectories, a recursive approach would be very natural: if the current “item” is a file, you can add it to your list, but if it’s a directory, you need to look at each
item in the directory (which could in turn be another directory to look
inside).

Recursion is also the natural choice for problems based on nested or
hierarchical data structures, such as trees and graphs, where data can
be processed in a “divide-and-conquer” approach. 

**Definition:** In computer programming, recursion is a method of problem-solving where the solution to a problem depends on solutions to smaller instances of the same problem. 
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function.

Recursion involves several key aspects:

1. Base Case(s): The simplest instance of the problem that can be solved    directly. It’s the condition that allows the recursion to stop.

2. Recursive Case(s): A more complex instance of the problem that’s solved by breaking it down, and calling the same function with the simpler version of the original problem.

3. Recursive Call: The process of a function invoking itself with a different argument.

Remember that each recursive call must make progress towards a base case
to ensure that the recursion ends. Failing to do so can result in an
infinite recursion, leading to a stack overflow error.


Example: Factorial
^^^^^^^^^^^^^^^^^^

.. _user-58: Can you provide a simple, complete, real-world code example of recursion in Java?


.. todo:: add non-recursive, stack-based versions of the non-tail-recursive examples


One of the classic examples of recursion is implementing a
method to compute the factorial of a number.

Factorial of a non-negative integer n, denoted by n!, is the product of
all positive integers less than or equal to n. It's defined recursively
in mathematical terms as follows:

-  0! = 1 (base case)
-  n! = n \* (n-1)! for n > 0 (recursive case)

Here’s how this can be implemented in Java:

.. code-block:: java

   public class Main {
       public static void main(final String[] args) {
           var n = 5;
           System.out.printf("The factorial of %d is: %d%n", n, factorial(n));
       }

       public static long factorial(final int n) {
           // Base Case
           if (n == 0) {
               return 1;
           }
           // Recursive Case
           else {
               return n * factorial(n-1);
           }
       }
   }

When you run this program, it will output:

.. code-block:: 

   The factorial of 5 is: 120

This is a recursive solution because the ``factorial`` method calls
itself to compute the factorial of a smaller number. The recursion
continues to “unroll” until it hits the base case (when n is 0), at
which point it starts “rolling up” again to compute and return the final
result.

Although recursion can make code easier to read and understand, it’s
important to note that it can be less efficient than iterative solutions
due to the overhead of function calls and can lead to stack overflow
errors if the recursion depth becomes too large. These factors should be
taken into consideration when deciding whether to use recursion to solve
a problem.


The call stack
^^^^^^^^^^^^^^

.. _user-59: Can you ASCII-draw the call stack during each step in the evaluation of factorial(5)?

Below is an ASCII representation of the call stack at each
step in the computation of ``factorial(5)``. It’s important to note that
the top of the stack is at the bottom of each illustration since new
stack frames are added “on top” of previous ones. The direction of
computation is from the top to the bottom, reflecting that the last
called function is the first one to finish.

.. code-block::

   Step 1: Call factorial(5)
   ----------------
   | factorial(5) |
   ----------------

   Step 2: 5 * factorial(4)
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 3: 4 * factorial(3)
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 4: 3 * factorial(2)
   ----------------
   | factorial(2) |
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 5: 2 * factorial(1)
   ----------------
   | factorial(1) |
   ----------------
   | factorial(2) |
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 6: 1 * factorial(0)
   ----------------
   | factorial(0) |
   ----------------
   | factorial(1) |
   ----------------
   | factorial(2) |
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 7: Return 1 (Base case)
   ----------------
   | factorial(1) |
   ----------------
   | factorial(2) |
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 8: Return 1 * 1
   ----------------
   | factorial(2) |
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 9: Return 2 * 1
   ----------------
   | factorial(3) |
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 10: Return 3 * 2
   ----------------
   | factorial(4) |
   ----------------
   | factorial(5) |
   ----------------

   Step 11: Return 4 * 6
   ----------------
   | factorial(5) |
   ----------------

   Step 12: Return 5 * 24
   ----------------

At this point, the entire stack has been unwound and the result, 120, is returned.

Each step represents the addition or removal of a stack frame in the
computation of ``factorial(5)``. As you can see, as the recursion
deepens (steps 1 to 6), stack frames are added. Once the base case is
hit (step 7), the recursion starts to unwind, and the stack frames are
removed one by one, each contributing to the final result (steps 8 to
12).


Equivalent iterative version: Factorial
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _user-60: Can you show me an equivalent iterative implementation of the factorial function?

Here’s how you can implement the factorial function iteratively
using a for loop in Java:

.. code-block::

   public class Main {
       public static void main(final String[] args) {
           var n = 5;
           System.out.printf("The factorial of %d is: %d%n", n, factorial(n));
       }

       public static long factorial(final int n) {
           var result = 1L;
           for (var i = 1; i <= n; i++) {
               result *= i;
           }
           return result;
       }
   }

In this version of the factorial function, we start with a ``result``
variable set to 1. We then multiply ``result`` by each integer from 1 to
``n`` inclusive. The result of each multiplication is stored back into
``result``, so by the end of the loop, ``result`` contains the factorial
of ``n``.

This code will output the same result as the recursive version:

::

   The factorial of 5 is: 120

Iterative solutions can be more efficient than recursive ones because
they avoid the overhead of function call stack frames. However, they can
sometimes be harder to understand or write, especially for problems that
have a naturally recursive structure.


Space complexity, stack safety, and tail recursion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _user-61: Weird that the stack would grow so much for the recursive version, given that it is functionally/observationally equivalent to the iterative one. Can you rewrite the recursive version in such a way that it would run in constant space IF Java were able to perform tail call elimination or even just elimination of tail recursion?

.. todo:: discuss time vs. space complexity - mention that time complexity is still linear but space complexity is our concern


In a language that supports tail call optimization, you would write the
recursive factorial function in a tail-recursive manner. Here’s what it
might look like in Java, although please note that as of Java 17, the
Java programming language does not support tail call optimization:

.. code-block:: java

   public class Main {
       public static void main(final String[] args) {
           var n = 5;
           System.out.printf("The factorial of %d is: %d%n", n, factorial(n, 1));
       }

       public static long factorial(final int n, final long acc) {
           if (n == 0) {
               return acc;
           } else {
               return factorial(n - 1, n * acc);
           }
       }
   }

In this version of ``factorial``, the function takes an additional
parameter ``acc`` which accumulates the factorial as the recursion
progresses. This parameter is multiplied by ``n`` in each recursive
call.

The critical change here is that the last thing each call does is to
make a recursive call to ``factorial(n - 1, n * acc)``. There’s no need
to wait for the recursive call to return before performing the
multiplication operation. This is what allows a tail call optimizing
compiler to reuse the same stack frame for each recursive call,
achieving constant space complexity.

However, as I mentioned before, Java does not support tail call
optimization as of version 17, so this version of ``factorial`` would
still use O(n) stack space in Java. It’s written this way to illustrate
the concept of tail recursion.


Tail recursion vs. iteration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _user-62: Can we convert any tail-recursive method to an iterative one?

Any tail-recursive method can be transformed into an iterative one.
Tail-recursive methods have a single recursive call as their last
operation. This feature makes it easy to convert them into iterative
methods, using loops.

The rationale behind this is that tail-recursive methods don’t need to
perform any additional computations after the recursive call, and this
directly translates to the body of a loop in the iterative version. In
the loop, the computation is performed at each iteration, then the loop
repeats until the base condition is satisfied, just like the base case
in recursion.

It’s important to note that while all tail-recursive methods can be
converted into iterative ones, not all recursive methods can be easily
converted into tail-recursive or iterative methods. Some recursive
problems involve multiple recursive calls or need to perform operations
after a recursive call, making them trickier to translate into an
iterative form.

Also, while converting tail-recursive methods to iterative ones can be
beneficial from a performance standpoint (since it eliminates the
function call overhead and the need for stack space), the resulting
iterative code can sometimes be more difficult to read and understand,
especially for problems that have a naturally recursive structure.


Example: Fibonacci numbers
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _user-63: Can you give me an example of an algorithm or method that cannot be converted to a tail recursive version?

A classic example of a recursive algorithm that can’t be converted into
a tail-recursive version in an obvious way is the computation of the Fibonacci sequence.
The Fibonacci sequence is defined recursively as follows:

-  fib(0) = 0
-  fib(1) = 1
-  fib(n) = fib(n-1) + fib(n-2) for n > 1

In Java, the function might be implemented like this:

::

   public static int fib(final int n) {
       if (n <= 1) {
           return n;
       } else {
           return fib(n - 1) + fib(n - 2);
       }
   }

The reason this can’t be converted into a tail-recursive version is that
there are two recursive calls in the function and these calls are not
the last operation. After the two recursive calls return, their results
must be added together.

That said, even though the Fibonacci sequence can’t be computed with a
tail-recursive algorithm, it can still be computed with an iterative
algorithm or a recursive algorithm that uses memoization to avoid
redundant computations. This is a common example of how different
techniques can be used to implement the same algorithm, depending on the
requirements and constraints of the problem.

.. _user-64: Can’t you write a tail-recursive version of fib with multiple accumulators?

.. Yes, absolutely! You’re correct, and that’s a good insight. 

Even though this is not obvious, it is
possible to compute Fibonacci numbers in a tail-recursive manner by
using more than one accumulator. In this case, we’ll use two
accumulators to keep track of the last two numbers in the Fibonacci
sequence. This way, each recursive call can be made with these two
numbers updated appropriately.

Here is how it could be implemented:

.. code-block:: java

   public class Main {
       public static void main(final String[] args) {
           final var n = 10;
           System.out.printf("The %dth number in Fibonacci sequence is: %d%n", n, fib(n));
       }

       public static int fib(final int n) {
           return fibHelper(n, 0, 1);
       }

       private static int fibHelper(final int n, final int a, final int b) {
           if (n == 0) {
               return a;
           } else {
               return fibHelper(n - 1, b, a + b);
           }
       }
   }

In this example, ``fibHelper`` is the tail-recursive helper function.
``a`` and ``b`` are accumulators that keep track of the last two numbers
in the sequence. At each step, we shift ``b`` to ``a`` and ``a + b`` to
``b``, which corresponds to moving one step forward in the Fibonacci
sequence.

However, it’s important to note that despite this function being
tail-recursive, Java does not perform tail call optimization, so the
space complexity is still O(n) due to the stack depth. This code is
mainly for illustrative purposes and to demonstrate the principle of
transforming standard recursion into tail recursion.

Multiple or tree recursion: Towers of Hanoi
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _user-65: Can you give another classic example of a problem with a straightforward, natural recursive solution that cannot easily be converted to an iterative solution (without introducing an additional data structure)?

.. _user-66: Very nice, but suppose students haven’t seen trees yet, can you think of something simpler, perhaps some easy to grasp puzzle?

There are problems with straightforward, natural, recursive solutions that cannot easily be converted to an iterative solution (without introducing an additional data structure)?

An example of such a problem is the puzzle game of Towers of Hanoi. The game
consists of three rods and a number of disks of different sizes which
can slide onto any rod. The puzzle starts with the disks neatly stacked
in ascending order of size on one rod, the smallest at the top.

The objective of the puzzle is to move the entire stack to another rod,
obeying the following rules:

1. Only one disk may be moved at a time.
2. Each move consists of taking the upper disk from one of the rods and
   sliding it onto another rod, on top of the other disks that may
   already be present on that rod.
3. No disk may be placed on top of a smaller disk.

Here’s a simple recursive solution in Java:

.. code-block:: java

   public class Main {
       public static void main(final String[] args) {
           hanoi(3, "A", "B", "C");
       }

       public static void hanoi(final int n, final String from, final String to, final String aux) {
           if (n == 1) {
               System.out.printf("Move disk 1 from rod %s to rod %s%n", from, to);
           } else {
               hanoi(n - 1, from, aux, to);
               System.out.printf("Move disk %d from rod %s to rod %s%n", n, from, to);
               hanoi(n - 1, aux, to, from);
           }
       }
   }

The recursive solution to the problem is intuitive and easy to
understand: if we want to move ``n`` disks from rod ``from`` to rod
``to``, we first move ``n-1`` disks from ``from`` to the auxiliary rod
``aux``, then move the ``n``\ th disk from ``from`` to ``to``, and
finally move the ``n-1`` disks from ``aux`` to ``to``. The base case is
when we only have one disk left to move.

However, implementing this iteratively is not straightforward. We would
need to simulate the program stack ourselves to keep track of the state
of each recursive call, which would be significantly more complicated,
and usually requires an explicit stack. So, this is an example of a
problem where a recursive solution is more intuitive and easier to
implement than an iterative solution.


Terminology
^^^^^^^^^^^

.. _user-67: Are there terms for methods that make at most one recursive call per branch, as opposed to those that have at least one branch that makes more than one recursive call?

.. _chatgpt-67:

There are specific terms to describe the various types of recursion:

1. Single Recursion or Linear Recursion: In this type of recursion, a
   function makes at most one recursive call in each branch, meaning it
   calls itself only once. Examples include the factorial function and
   the Fibonacci sequence function (although the Fibonacci function has
   two recursive branches, each branch only makes one recursive call).
   These types of problems can often be solved iteratively quite easily.

2. Multiple Recursion or Tree Recursion: This refers to functions that
   call themselves more than once in at least one branch, leading to a
   tree-like structure of subproblems. An example is the Towers of Hanoi
   problem, where the function calls itself twice in the non-base case.
   Problems with multiple recursion often involve a branching of
   possibilities and are typically harder to solve iteratively without
   introducing an additional data structure, like an explicit stack, to
   maintain state information.

Remember, the terms “single recursion” and “multiple recursion” aren’t
universally standardized, but are commonly used to describe these types
of recursion.


Performance analysis: Towers of Hanoi
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. In the Hanoi puzzle, if every move is considered one step, can you come up with a recurrence relation T(n) for the number of moves required to solve the puzzle for n disks? And then explain step by step how to come up with a closed form solution of the recurrence relation?

The Towers of Hanoi puzzle is a classic example of a problem that can be
solved using recursion, and the time complexity of the solution can be
expressed using a recurrence relation.

For ``n`` disks, the number of moves ``T(n)`` required to solve the
puzzle can be described by the recurrence relation:

``T(n) = 2*T(n-1) + 1``

The intuition behind this recurrence is as follows:

-  To move ``n`` disks from the source peg to the destination peg, we
   first need to move ``n-1`` disks from the source peg to the auxiliary
   peg. This requires ``T(n-1)`` moves.
-  Then, we move the remaining disk (the largest one) from the source
   peg to the destination peg. This requires one move.
-  Finally, we need to move the ``n-1`` disks from the auxiliary peg to
   the destination peg. This again requires ``T(n-1)`` moves.

Thus, the total number of moves is ``T(n) = 2*T(n-1) + 1``.

To solve this recurrence relation, we can use a method called
“unrolling” or “iteration”. Here’s how it works:

1. Start with the equation ``T(n) = 2*T(n-1) + 1``
2. Substitute ``T(n-1) = 2*T(n-2) + 1`` into the equation to get
   ``T(n) = 2*(2*T(n-2) + 1) + 1 = 2^2*T(n-2) + 2 + 1``
3. Continue unrolling, until you reach ``T(1) = 1`` (since it takes one
   move to move a single disk). After ``k`` steps, you get
   ``T(n) = 2^k*T(n-k) + 2^k - 1``.
4. Stop when ``n - k = 1``, i.e., ``k = n - 1``. Thus,
   ``T(n) = 2^(n-1)*T(1) + 2^(n-1) - 1 = 2^(n-1) + 2^(n-1) - 1``.
5. Since ``2^(n-1) + 2^(n-1) = 2^n``, we finally get ``T(n) = 2^n - 1``.

So, the solution to the recurrence is ``T(n) = 2^n - 1``, which means
the number of moves required to solve the Towers of Hanoi puzzle with
``n`` disks is ``2^n - 1``. This is an exponential time complexity.


.. todo:: recursive version of the maze solver


******************************************

*CONTENT BELOW HERE TO BE ORGANIZED LATER*
------------------------------------------


Top 15 CS2 topics as opposed to CS7
-----------------------------------

*Let's consider the ACM 2020 curriculum guidelines. If we split topics in such a way that CS2 focuses on an introduction to data structures and CS7 on more advanced data structures, what should the top 15 CS2-specific topics be? (GPT-4)*

.. warning:: The ACM 2020 curriculum guidelines are not specifically available to me at my last training cut-off in September 2021. 

However, I can provide an example list of topics that are often covered in a typical second course in computer science (CS2), focusing on an introduction to data structures. These topics build upon the basics learned in a CS1 course, such as basic programming constructs, control structures, and introductory object-oriented programming.

Here is a general list of 15 topics:

1. **Review of Basic Programming Concepts:** This might include basic data types, control structures, functions, and classes.

2. **Array and ArrayList:** Understanding of these basic data structures, their uses, and limitations.

3. **Stacks:** Introduction to stack data structures, their uses, and basic operations like push and pop.

4. **Queues:** Similar to stacks, this would cover the concept, uses, and operations of queues.

5. **Linked Lists:** Covers singly-linked and doubly-linked lists, their operations, and use cases.

6. **Recursion:** Understanding of recursive functions and their applications, and the relationship to data structures.

7. **Trees:** Introduction to basic tree structures, tree traversals, and binary trees.

8. **Binary Search Trees:** A more specific tree structure with ordering properties, including operations like insertion and deletion.

9. **Hashing:** Introduction to hash tables, hash functions, collision strategies, and their applications.

10. **Heaps:** Understanding of heap data structures, and algorithms like heap sort.

11. **Graphs:** Introduction to basic graph concepts, representation, and traversals (DFS, BFS).

12. **Sorting Algorithms:** Covers basic sorting algorithms like selection sort, insertion sort, bubble sort, quicksort, mergesort, and heapsort.

13. **Search Algorithms:** Covers linear search and binary search on various data structures.

14. **Algorithm Analysis:** Understanding Big O notation, time complexity, and space complexity.

15. **Software Engineering Principles:** Introduction to basic principles such as code readability, modularity, and debugging techniques.

The exact order and selection of these topics may vary depending on the specific course and curriculum guidelines. Also, real-life examples and problem-solving exercises should be included to apply these data structures and concepts. The complexity and depth of these topics will increase when students move on to more advanced courses like CS7.


CS2 at Loyola: Current topics and learning outcomes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
	  
.. todo:: Update as needed.

Here's a version of the list of current topics and learning outcomes of the CS2 course at Loyola, COMP 271.

1. Basics of Object-Oriented Programming: Students will be able to create, use, and understand properly constructed OOP classes with public and private members, constructors, accessors, and mutators. They will also learn how to use method overloading appropriately and create classes with proper encapsulation. Additionally, they will be able to use existing classes and access documentation to find and understand components of classes to create new programs.

2. More Object-Oriented Programming: Building on the basics, students will learn how to create solutions with multiple cooperating OOP classes. They will understand and use basic inheritance and interfaces, apply them to problem-solving, and create well-structured solutions. Students will also know how to use overriding of methods, abstract classes and methods, and interfaces. They will be able to implement common methods appropriately (toString, equals, compareTo, hashCode.) and understand and apply the substitution rule in inheritance. Finally, they will be familiar with boxing and unboxing of primitive types.

3. Sequential Structures: Students will learn to select and use appropriate sequential data structures in problem-solving, including ArrayList, List, Linked List, Queue, Dequeue, and Stack. They will use iterators with sequential data structures, understand how these implementations impact performance (Big-Oh), and learn the implementation of array-based and list-based data structures. They will also be able to create medium scale applications and identify limits when picking appropriate data structures for unfamiliar problems.

4. Algorithms and Recursion: Students will gain an introduction to recursion, its uses and pitfalls, and understand the appropriate uses of recursion and which algorithms using it are likely to perform acceptably. They will be able to analyze when recursion is and is not necessary and appropriate. Students will also extend their ability to predict and compare Big-Oh performance of programs and knowledge of algorithms with an understanding of backtracking and recursion.

5. Sorting and Searching: Students will understand sorting and searching techniques and how they are implemented in linear data structures. They will iterate through information using linear and binary searches, and be able to compare the performance of array-based and linked list sorting and searching.

6. Problem Solving, Testing, Debugging: Students will be able to apply problem-solving techniques to new computing problems, evaluate and select approaches including step-wise refinement, divide and conquer, etc. They will gain introductory experience with test-driven development, be able to define and evaluate test cases appropriate to the problem at hand, and become proficient at applying debugging principles including breakpoints and tracking of variables when code does not work as intended. Students will also understand and apply JUnit for creating and analyzing problems and selecting appropriate techniques.

7. Tools, Organization, Professional Development: Students will become fully proficient at creating, editing, compiling, and running programs using both an Integrated Development Environment and the command line. They will also be able to install and update programming tools on their own computers. Additionally, students will create, grow, and maintain a GitHub account and use it as a repository for class work and projects throughout their continued education at Loyola University Chicago. They will be prepared to use it to demonstrate their experience and non-text materials to be supplied.

8. Code Reading and Inspections, Java Documentation, Programming Style: Students will learn how to effectively read code produced by others, either for learning or finding defects. They will develop a professional-looking programming style, learn to create and use Java doc when reading and writing code, and gain experience interacting with others by doing code reading and inspections. Students will also understand the concept of defects in programs and apply their skills to their own work and the work of others.

9. Introduction to Non-Linear Data Structures: Students will gain an introduction to advanced data structures, including trees, binary trees, and graphs. They will be able to compare these data structures with linear data structures and understand when they may be useful in implementations.


.. warning:: Our list is missing Map and Set, and so are ChatGPT's recommendations.


*How would you reconcile your earlier list with our own current set of topics and learning outcomes?*

The list you provided for Loyola's COMP 271 is quite comprehensive and aligns well with the general introductory data structures course topics I initially suggested. I'll try to reconcile the two lists by mapping the suggested topics to your current ones and identifying potential areas of expansion.

1. **Review of Basic Programming Concepts:** This is covered in your "Basics of Object-Oriented Programming" and "More Object-Oriented Programming" sections. Students already learn about the fundamentals of OOP, which is a good foundation for the course.

2. **Array and ArrayList:** This is included in your "Sequential Structures" section where students learn about ArrayList and other linear data structures.

3. **Stacks and Queues:** These topics are also part of your "Sequential Structures" section.

4. **Linked Lists:** Again, part of your "Sequential Structures" section.

5. **Recursion:** This is covered in your "Algorithms and Recursion" section.

6. **Trees:** The basics of tree data structures seem to be covered in the "Introduction to Non-Linear Data Structures" section.

7. **Binary Search Trees:** This is an area where you could consider expanding your "Introduction to Non-Linear Data Structures" section. While you currently introduce trees and binary trees, binary search trees are a specific kind of binary tree with unique properties and operations that might be worth covering.

8. **Hashing:** This topic isn't explicitly mentioned in your current topics. It could be a valuable addition to your course, as hash tables are a commonly used data structure in software development.

9. **Heaps:** This is another topic that could be added to your "Introduction to Non-Linear Data Structures" section. Heaps are a useful type of tree-based data structure.

10. **Graphs:** These are included in your "Introduction to Non-Linear Data Structures" section.

11. **Sorting Algorithms:** This is covered in your "Sorting and Searching" section.

12. **Search Algorithms:** This is also covered in your "Sorting and Searching" section.

13. **Algorithm Analysis:** This is part of your "Algorithms and Recursion" section where students learn about Big-Oh notation and algorithm performance.

14. **Software Engineering Principles:** Your "Problem Solving, Testing, Debugging", "Tools, Organization, Professional Development", and "Code Reading and Inspections, Java Documentation, Programming Style" sections cover various aspects of software engineering principles, such as testing, debugging, and code style.

15. **Advanced Concepts (Optional):** Depending on the pace of the class and the preparedness of the students, more advanced topics such as dynamic programming, greedy algorithms, and understanding of data structures like tries, AVL trees, red-black trees, and disjoint sets could be introduced.

Overall, the Loyola COMP 271 course seems comprehensive and well-structured. Adding a few more topics like hashing, heaps, and binary search trees could make it even more robust.


*Thanks, though we want to cover the most essential topics in depth during our 15-week semester, and we have the opportunity to defer the most advanced topics to our subsequent CS7 course. Which three to five topics do you think would be good candidates for coverage in CS7 instead of CS2?*

Certainly, it's crucial to ensure students have a thorough understanding of fundamental topics before introducing more advanced ones. Here are a few topics that could be deferred to a CS7 course:

1. **Advanced Trees (AVL Trees, Red-Black Trees, B-Trees, etc.):** While CS2 covers basic tree structures and binary search trees, advanced trees like AVL trees, Red-Black trees, and B-trees have more complex balancing algorithms that might be better suited for a more advanced course.

2. **Graph Algorithms:** CS2 introduces basic graph concepts, but more advanced graph algorithms like Dijkstra's, Bellman-Ford, Floyd-Warshall, and algorithms for minimum spanning trees (Kruskal's and Prim's), along with topics like topological sorting, strongly connected components, etc., could be reserved for CS7.

3. **Advanced Data Structures (Hashing, Heaps, Disjoint Sets, Tries):** While basic hashing can be covered in CS2, more advanced topics like open addressing, perfect hashing, universal hashing, and advanced data structures like disjoint set union and tries could be deferred to CS7.

4. **Dynamic Programming and Greedy Algorithms:** These topics involve a higher level of problem-solving skills and a deep understanding of recursion and optimization. They are typically introduced in more advanced algorithms courses.

5. **NP-Completeness and Computational Intractability:** This is a more theoretical aspect of computer science and requires a good understanding of algorithms and their complexities. This would be more suitable for an advanced course.

These topics would provide a solid foundation for a CS7 course and would build nicely on the topics covered in CS2. The exact division of topics will depend on the pace and depth at which the material is covered in CS2, as well as the specific goals of the CS7 course.


*What's your recommended order of the remaining CS2 topics?*

Here's a recommended order for these CS2 topics, with the understanding that some topics will naturally overlap and interweave:

1. **Review of Basic Programming Concepts:** This is a natural starting point, reinforcing the foundations of Object-Oriented Programming (OOP).

2. **Array and ArrayList:** Introduce these fundamental data structures early on, as they're the backbone of many other structures and algorithms.

3. **Stacks and Queues:** These are simple, yet powerful, data structures that can be understood with the foundation of Arrays/ArrayLists.

4. **Linked Lists:** This introduces another way to structure data sequentially, with different performance implications. It's a good lead-in to more complex structures.

5. **Recursion:** Recursion can be a challenging concept for many students, so introducing it relatively early allows more time for practice and reinforcement throughout the course.

6. **Algorithm Analysis:** Once students have seen a few different algorithms (in the form of data structure operations), it's a good time to introduce Big-Oh notation and the concept of time complexity.

7. **Sorting and Searching Algorithms:** With a basic understanding of algorithm analysis, students can start exploring more complex algorithms and comparing their performance.

8. **Trees and Binary Search Trees:** Trees are a key non-linear data structure. Understanding them leads naturally to binary search trees, which are a practical application with important efficiency characteristics.

9. **Hashing:** This is a good point to introduce hashing, which underlies a very efficient (on average) data structure: the hash table.

10. **Software Engineering Principles:** These principles can be introduced and then reinforced throughout the course. However, students will appreciate them more once they've dealt with more complex code.

Remember, this order isn't rigid. Many of these topics naturally overlap, and teaching them isn't necessarily a linear process. For instance, basic algorithm analysis can be introduced as soon as you're discussing different operations on data structures, and then reinforced throughout the course as you introduce more complex algorithms. Similarly, software engineering principles can be woven throughout the course as students write more and more complex code.


*Which of these topics would you consider cross-cutting?*

Cross-cutting topics in a curriculum are those that span multiple areas of study or are applicable to a variety of specific topics. In the context of a CS2 course focused on data structures, these topics often include general principles and methodologies rather than specific technologies or structures. 

Here are the cross-cutting topics from your list:

1. **Review of Basic Programming Concepts:** The principles of object-oriented programming, such as encapsulation, inheritance, and polymorphism, are applicable across a wide range of topics in computer science.

2. **Algorithm Analysis:** Understanding how to analyze the efficiency of algorithms, particularly with Big-O notation, is critical when studying various data structures and algorithms.

3. **Recursion:** This is a fundamental concept that applies to many different data structures and algorithms, such as tree traversals, searching algorithms, and sorting algorithms.

4. **Sorting and Searching Algorithms:** The concepts behind these algorithms are universal and will apply to different data structures. Understanding how to sort and search efficiently is important across a wide range of problem domains.

5. **Software Engineering Principles:** Principles like code readability, modularity, testing, and debugging apply to all areas of software development, not just to data structures and algorithms. These are skills that students will use continuously, no matter what specific topic they're studying.

While it's important to study specific data structures like arrays, trees, and hash tables, these cross-cutting topics provide a framework for understanding how to use those structures effectively and efficiently. They will be revisited and applied repeatedly throughout both this course and subsequent computer science courses.



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



Basic object-oriented programming
---------------------------------


In the context of CS2, what are the essential elements of OOP?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the context of CS2 (second course in computer science), the essential elements of Object-Oriented Programming (OOP) include the following:  
 
1. Classes: Classes are the fundamental building blocks of object-oriented programming. They define the blueprint or template for creating objects. A class encapsulates data (attributes) and behavior (methods) related to a specific concept or entity.

2. Objects: Objects are instances of classes. They represent specific occurrences of the concepts defined by the class. Objects have their own unique state (attribute values) and can perform actions (methods) defined by the class.

3. Encapsulation: Encapsulation is the principle of bundling data and methods within a single entity (class) and restricting direct access to internal implementation details. It promotes information hiding and allows for the abstraction and modular organization of code.

4. Inheritance: Inheritance allows for the creation of new classes (child or derived classes) based on existing classes (parent or base classes). It facilitates code reuse by inheriting attributes and behaviors from the parent class, enabling hierarchical relationships and polymorphism.

5. Polymorphism: Polymorphism allows objects of different classes to be treated as objects of a common parent class, enabling objects to respond to the same messages (method calls) in different ways. It promotes code flexibility, extensibility, and the ability to write generic code.

6. Abstraction: Abstraction involves representing essential features and behaviors of a concept while hiding unnecessary details. It allows for the creation of abstract classes and interfaces that define common characteristics and behaviors shared by multiple classes.

7. Modularity: Modularity emphasizes organizing code into separate, self-contained modules (classes) that focus on specific aspects of the problem domain. It promotes code organization, reusability, and maintainability.


Enums, classes, and records
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Here is a simple example in Java that covers classes, records (introduced in Java 14), enums, constructors, accessors, mutators, and the use of `public` and `private` members:

First, we'll create an `enum` to represent a type of a pet:

.. code-block:: java

    public enum PetType {
        DOG,
        CAT,
        BIRD
    }


Next, we'll create a `class` to represent a Pet with fields, constructors, accessors, and mutators:

.. code-block:: java

    public class Pet {
        private String name;
        private PetType type;

        public Pet(final String name, final PetType type) {
            this.name = name;
            this.type = type;
        }

        public String getName() {
            return this.name;
        }

        public void setName(final String name) {
            this.name = name;
        }

        public PetType getType() {
            return this.type;
        }

        public void setType(final PetType type) {
            this.type = type;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", type=" + type +
                    '}';
        }
    }


Next, we'll create a `record` to represent an Owner. Records are a compact way to declare classes which are transparent holders for shallowly immutable data:

.. code-block:: java

    public record Owner(String name, String address) { }


Finally, we can create instances of our classes and manipulate them:

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            final var pet = new Pet("Fido", PetType.DOG);
            final var owner = new Owner("John Doe", "123 Main St");

            System.out.println(pet);
            System.out.println(owner);

            pet.setName("Spot");
            System.out.println(pet);
        }
    }


This example demonstrates encapsulation: the `Pet` class's `name` and `type` fields are `private`, so they can't be accessed directly from outside the class. Instead, they are accessed and modified through `public` accessor (getter) and mutator (setter) methods. The `Owner` record also demonstrates encapsulation, though in a different way: its fields are `public`, but they are `final` and can't be modified after the record is created. The `PetType` enum demonstrates a basic use of enums to represent a fixed set of values.


*Very nice and comprehensive. But why does Pet have a setType method? Can Fido become a cat?!?*

Great observation! In many real-world scenarios, some properties of an object might not change after its creation. In the case of a `Pet`, the `type` (whether it's a dog, cat, or bird) would realistically never change. Therefore, it would make more sense to omit the `setType` method to ensure the `type` field remains constant after the `Pet` object is created, which represents the concept of immutability.

Here's the adjusted `Pet` class:

.. code-block:: java

    public class Pet {
        private String name;
        private final PetType type;

        public Pet(final String name, final PetType type) {
            this.name = name;
            this.type = type;
        }

        public String getName() {
            return this.name;
        }

        public void setName(final String name) {
            this.name = name;
        }

        public PetType getType() {
            return this.type;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", type=" + type +
                    '}';
        }
    }


Now the `type` is marked as `final` and there's no `setType` method, meaning the `type` can't be changed after a `Pet` object is created. If you want to create a pet of a different type, you would need to create a new `Pet` object. This is more representative of the real world, where a pet's species can't change.

Associations between classes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. warning:: Ran out of GPT-4 queries here.


The relationship between pets and owners can be represented using an association or aggregation relationship. Let's consider the `Pet` class and the `Owner` record.

In this scenario, an `Owner` can have one or more `Pet` objects, and a `Pet` can belong to a single `Owner`. This relationship can be represented by adding a reference to the `Owner` class in the `Pet` class.

Here's an updated version of the code to illustrate the relationship:

.. code-block:: java

    public class Pet {
        private String name;
        private PetType type;
        private Owner owner;

        public Pet(final String name, final PetType type, final Owner owner) {
            this.name = name;
            this.type = type;
            this.owner = owner;
        }

        // Getter and setter methods for name, type, and owner

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", type=" + type +
                    ", owner=" + owner +
                    '}';
        }
    }

    public record Owner(String name, String address) {
    }


In the updated `Pet` class, we added a field `owner` of type `Owner` to represent the owner of the pet. The `Owner` class remains unchanged.

With this association, you can now create `Pet` objects and assign them to an `Owner`. Here's an example:

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            final var owner = new Owner("John Doe", "123 Main St");

            final var pet1 = new Pet("Fido", PetType.DOG, owner);
            final var pet2 = new Pet("Whiskers", PetType.CAT, owner);

            System.out.println(pet1);
            System.out.println(pet2);
        }
    }


This will output:

.. code-block:: 

    Pet{name='Fido', type=DOG, owner=Owner[name=John Doe, address=123 Main St]}
    Pet{name='Whiskers', type=CAT, owner=Owner[name=John Doe, address=123 Main St]}


Now, each `Pet` object has a reference to its respective `Owner`. This allows you to establish the relationship between pets and owners and retrieve the owner information when needed.

It's important to note that this example illustrates a simplified association relationship. In more complex scenarios, you might encounter different types of relationships like composition or bidirectional associations. The choice of the appropriate relationship type depends on the specific requirements and design of the system.


Subtype polymorphism
^^^^^^^^^^^^^^^^^^^^

*For this Pet class, how would you define behaviors that are specific to a type of pet, such as a dog barking and a cat meowing?*

To represent behaviors specific to different types of pets, you can use polymorphism and inheritance in object-oriented programming. You could define a base class or interface `Pet` and then create subclasses for each specific type of pet. Each subclass can then implement its own version of the behavior methods. Here's an example:

First, we'll define the base class `Pet`:

.. code-block:: java

    public abstract class Pet {
        private String name;

        public Pet(final String name) {
            this.name = name;
        }

        public String getName() {
            return this.name;
        }

        public void setName(final String name) {
            this.name = name;
        }

        // abstract method for the pet to make a sound
        public abstract String makeSound();
    }


Then, we'll create `Dog` and `Cat` classes that extend `Pet` and implement the `makeSound` method:

.. code-block:: java

    public class Dog extends Pet {
        public Dog(final String name) {
            super(name);
        }

        @Override
        public String makeSound() {
            return "Bark!";
        }
    }

    public class Cat extends Pet {
        public Cat(final String name) {
            super(name);
        }

        @Override
        public String makeSound() {
            return "Meow!";
        }
    }


Finally, we can create `Dog` and `Cat` objects and call their `makeSound` methods:

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            final var dog = new Dog("Fido");
            final var cat = new Cat("Whiskers");

            System.out.println(dog.getName() + " says: " + dog.makeSound());
            System.out.println(cat.getName() + " says: " + cat.makeSound());
        }
    }


This will output:

.. code-block:: 

    Fido says: Bark!
    Whiskers says: Meow!


In this way, we've represented behaviors specific to different types of pets. Each type of pet can have its own unique behaviors, while still sharing common attributes and behaviors through the `Pet` base class.


Subclasses and method overriding
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*Aren't there some dogs that howl rather than bark? Can we enhance our class hierarchy accordingly?*

To handle this, we can introduce another layer in our class hierarchy. Let's create a `Dog` subclass called `Husky`, which overrides the `makeSound` method to return "Howl!" instead of "Bark!". Here's how you can do it:

.. code-block:: java

    public class Husky extends Dog {
        public Husky(final String name) {
            super(name);
        }

        @Override
        public String makeSound() {
            return "Howl!";
        }
    }


Now you can create a `Husky` object, add it to the `pets` list, and see that it howls instead of barks:

.. code-block:: java

    public class Main {
        public static void main(final String[] args) {
            // Create a list of pets
            final var pets = new ArrayList<Pet>();
            pets.add(new Dog("Fido"));
            pets.add(new Cat("Whiskers"));
            pets.add(new Husky("Balto"));

            // Make each pet make its sound
            for (final var pet : pets) {
                System.out.println(pet.getName() + " says: " + pet.makeSound());
            }
        }
    }


This will output:

.. code-block:: 

    Fido says: Bark!
    Whiskers says: Meow!
    Balto says: Howl!


This demonstrates the flexibility of object-oriented programming. By creating a subclass and overriding methods, you can create variations of a base class that behave differently. And thanks to polymorphism, you can handle objects of the base class and its subclasses in a unified way.


Interfaces
^^^^^^^^^^

Interfaces provide a way to define common behavior and can be utilized in this example to further enhance the design. Let's introduce an interface called `Soundable` to represent pets that can make sounds. Here's an updated version that incorporates interfaces:

.. code-block:: java

    import java.util.ArrayList;
    import java.util.List;

    public interface Soundable {
        String makeSound();
    }

    public abstract class Pet {
        private String name;
        private Owner owner;

        public Pet(final String name, final Owner owner) {
            this.name = name;
            this.owner = owner;
        }

        public String getName() {
            return name;
        }

        public Owner getOwner() {
            return owner;
        }

        public void setOwner(final Owner owner) {
            this.owner = owner;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", owner=" + owner +
                    '}';
        }
    }

    public class Dog extends Pet implements Soundable {
        public Dog(final String name, final Owner owner) {
            super(name, owner);
        }

        @Override
        public String makeSound() {
            return "Bark!";
        }
    }

    public class Cat extends Pet implements Soundable {
        public Cat(final String name, final Owner owner) {
            super(name, owner);
        }

        @Override
        public String makeSound() {
            return "Meow!";
        }
    }

    public record Owner(String name, String address) {
    }

    public class Main {
        public static void main(final String[] args) {
            final var owner = new Owner("John Doe", "123 Main St");

            final var pets = new ArrayList<Soundable>();
            pets.add(new Dog("Fido", owner));
            pets.add(new Cat("Whiskers", owner));

            for (final var pet : pets) {
                System.out.println(pet.getName() + " says: " + pet.makeSound());
            }
        }
    }


In this updated version, we introduce the `Soundable` interface, which declares the `makeSound` method. Both `Dog` and `Cat` classes implement this interface, indicating that they can make sounds.

The `ArrayList` is now defined as `ArrayList<Soundable>`, allowing it to hold objects that implement the `Soundable` interface. This way, we can ensure that all pets in the list can make sounds.

By iterating over the `pets` list and treating each pet as a `Soundable`, we can call the `getName` and `makeSound` methods for each pet.

The output will remain the same:

.. code-block:: 

    Fido says: Bark!
    Whiskers says: Meow!


This updated version showcases the usage of interfaces to define common behavior and achieve a higher level of abstraction. By utilizing the `Soundable` interface, we can easily manage a list of pets that can make sounds, regardless of their specific pet type.


*Finally, can you add back the husky?*

Certainly! Here's the updated version that includes the `Husky` class back into the example, leveraging interfaces and inheritance:

.. code-block:: java

    import java.util.ArrayList;
    import java.util.List;

    public interface Soundable {
        String makeSound();
    }

    public abstract class Pet {
        private String name;
        private Owner owner;

        public Pet(final String name, final Owner owner) {
            this.name = name;
            this.owner = owner;
        }

        public String getName() {
            return name;
        }

        public Owner getOwner() {
            return owner;
        }

        public void setOwner(final Owner owner) {
            this.owner = owner;
        }

        @Override
        public String toString() {
            return "Pet{" +
                    "name='" + name + '\'' +
                    ", owner=" + owner +
                    '}';
        }
    }

    public class Dog extends Pet implements Soundable {
        public Dog(final String name, final Owner owner) {
            super(name, owner);
        }

        @Override
        public String makeSound() {
            return "Bark!";
        }
    }

    public class Cat extends Pet implements Soundable {
        public Cat(final String name, final Owner owner) {
            super(name, owner);
        }

        @Override
        public String makeSound() {
            return "Meow!";
        }
    }

    public class Husky extends Dog {
        public Husky(final String name, final Owner owner) {
            super(name, owner);
        }

        @Override
        public String makeSound() {
            return "Howl!";
        }
    }

    public record Owner(String name, String address) {
    }

    public class Main {
        public static void main(final String[] args) {
            final var owner = new Owner("John Doe", "123 Main St");

            final var pets = new ArrayList<Soundable>();
            pets.add(new Dog("Fido", owner));
            pets.add(new Cat("Whiskers", owner));
            pets.add(new Husky("Balto", owner));

            for (final var pet : pets) {
                System.out.println(pet.getName() + " says: " + pet.makeSound());
            }
        }
    }


In this updated version, we reintroduce the `Husky` class, which extends the `Dog` class and implements the `Soundable` interface. The `Husky` class overrides the `makeSound` method to return "Howl!".

We include an instance of `Husky` in the `pets` list alongside the `Dog` and `Cat` instances. As all three classes implement the `Soundable` interface, they can be added to the list.

When iterating over the `pets` list, each pet's `makeSound` method is called based on its actual type, producing the appropriate sound for each pet.

The output will be:

.. code-block:: 

    Fido says: Bark!
    Whiskers says: Meow!
    Balto says: Howl!


This updated version demonstrates the utilization of interfaces, inheritance, and polymorphism to handle different types of pets with varying behaviors in a unified way.


Where does subtyping fit in?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Subtyping is an important concept in object-oriented programming and is closely related to inheritance. It allows for the substitution of objects of one class with objects of another class that is derived from or related to the former class. 

Subtyping enables polymorphism and supports the "is-a" relationship between classes. It allows objects of a derived class to be treated as objects of their parent class, providing flexibility and extensibility in program design. By leveraging subtyping, code can be written in a way that is more generic and adaptable to different types of objects.

In the context of CS2, subtyping is a significant aspect of understanding inheritance and polymorphism. It enables students to create class hierarchies, define relationships between classes, and utilize the principles of code reuse and abstraction. By grasping the concept of subtyping, students can effectively design and implement object-oriented programs that utilize inheritance and polymorphism to their full potential.


.. csv-table:: Comparison between type hierarchy relationships
    :header: "Feature", "Subtyping", "Inheritance"
    :widths: 25, 25, 25

    "Relationship", "Is-a relationship between types", "Mechanism for code reuse and specialization"
    "Nature", "Defines a subtype-supertype relationship", "Defines a relationship for inheriting attributes and behaviors"
    "Polymorphism", "Enables substitution of subtypes for supertypes", "Enables runtime polymorphism and method overriding"
    "Extensibility", "Allows adding new subtypes to the hierarchy", "Supports extension of existing classes through subclassing"
    "Code Reuse", "Facilitates reuse of behavior and interface from supertype", "Allows inheriting methods and fields from superclass"
    "Method Overriding", "Enables subclass to provide its own implementation of inherited methods", "Provides the ability to override superclass methods"
    "Specialization", "Refines and specializes behavior and characteristics of supertype", "Allows creating specialized versions of a generalized superclass"
    "Hierarchy Structure", "Forms a hierarchy of related types based on subtyping", "Organizes classes in a hierarchical structure based on inheritance"
    "Example", "Animal and Dog (A dog is an animal)", "Vehicle and Car (A car inherits attributes and behaviors from the vehicle)"


Where would you put delegation?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Delegation is a concept that can be closely related to both composition and inheritance in object-oriented programming. It involves one object (delegate) handing off a specific task or responsibility to another object (delegator). 

In terms of its placement, delegation can be seen as a design pattern or technique that can be applied in various parts of an object-oriented program. It is not necessarily a core element of OOP like classes, objects, inheritance, or polymorphism, but rather a flexible approach to achieve code reuse and modularity.

Delegation can be utilized within the methods or behaviors of a class, where a specific task or functionality is delegated to another object responsible for performing that task. This allows the delegator object to rely on the expertise or specialized behavior of the delegate object without inheriting from it.

Additionally, delegation can also be used at a higher level in the design of a system, where an object delegates certain responsibilities or operations to other objects to achieve a more modular and loosely coupled architecture. This promotes the separation of concerns and enhances code maintainability and flexibility.

In summary, delegation is a technique that can be applied within the methods of a class or at a higher level in the system design. It is a flexible approach that allows objects to delegate specific tasks to other objects, promoting code reuse, modularity, and separation of concerns.


8. Delegation: Delegation is a technique where one object (delegator) hands off a specific task or responsibility to another object (delegate). It allows objects to rely on the specialized behavior of other objects without directly inheriting from them, promoting code reuse and modular design.


In practice, shouldn't delegation be on par with inheritance?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In practice, both delegation and inheritance are important concepts in object-oriented programming, but they serve different purposes and have distinct advantages and use cases. While inheritance is a mechanism for creating class hierarchies and sharing behavior and attributes between classes, delegation is a technique for achieving code reuse and modularity by handing off specific tasks or responsibilities to other objects.

The choice between delegation and inheritance depends on the specific requirements and design goals of the program. In some cases, inheritance may be more appropriate when there is a clear "is-a" relationship between classes and a need to share common behavior and attributes. Inheritance can provide a convenient way to define and organize class hierarchies, promote code reuse, and enable polymorphism.

On the other hand, delegation can be preferred when there is a need for more flexible and modular design. Delegation allows objects to delegate specific tasks to other objects that specialize in those tasks, enabling composition and separation of concerns. It promotes code reuse without requiring a rigid class hierarchy and allows objects to rely on the behavior of other objects without inheriting from them directly.

In practice, both inheritance and delegation are used together or in combination to achieve desired design goals. They are not mutually exclusive, and the choice between them often depends on the specific problem domain, the relationships between objects, and the desired flexibility and extensibility of the system.

So, while delegation is indeed an important technique in practice and can be used on par with inheritance in certain scenarios, it's important to consider the specific requirements and design goals to determine the most appropriate approach for a given situation.



Where do composition, aggregation, and association fit into this list?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

9. Composition: Composition is a strong "whole-part" relationship where the lifetime of the parts is tightly coupled with the lifetime of the whole. The whole object is responsible for creating and managing its component objects. If the whole object is destroyed, its parts are also destroyed. Composition is often represented by a class having one or more member variables of another class type.

10. Aggregation: Aggregation is a weaker form of composition, representing a relationship where one object (the aggregate) contains or is associated with other objects (the components). The components can exist independently of the aggregate, and their lifetimes are not necessarily tied to the aggregate's lifetime. Aggregation is often represented by a class having member variables that are references or pointers to other objects.

11. Association: Association represents a relationship between two or more objects, indicating that they are somehow connected or interact with each other. Unlike composition and aggregation, association doesn't imply ownership or lifetime dependencies between the associated objects. Associations can be represented through member variables, method parameters, or return values.
   
By understanding and effectively utilizing these essential elements of OOP, including delegation, students in CS2 can develop a strong foundation in object-oriented programming principles and apply them to create robust, maintainable, and flexible software solutions.

Composition, aggregation, and association are relationship types that expand the ways in which objects can interact and collaborate in an object-oriented system. They provide additional flexibility in designing object relationships, capturing different levels of ownership and dependency.

By understanding and utilizing composition, aggregation, and association, students in CS2 can create more expressive and accurate models of real-world systems, enabling them to design and implement object-oriented programs that accurately reflect the relationships and interactions between objects.


Is association related to delegation?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Association and delegation are distinct concepts in object-oriented programming, but they can be related in certain scenarios.

Association represents a relationship between two or more objects, indicating that they are somehow connected or interact with each other. It captures the concept of objects being aware of each other and potentially collaborating, but it does not imply any specific behavior or responsibility transfer.

Delegation, on the other hand, is a technique where one object (delegator) hands off a specific task or responsibility to another object (delegate). It involves one object relying on the specialized behavior of another object to fulfill a specific aspect of its functionality.

While association and delegation are separate concepts, they can coexist in a system. In some cases, an object involved in an association may delegate a specific task to another object. The object responsible for the delegated task can be considered the delegate in the context of delegation, even though there is an association between the delegator and the delegate.

The association between objects can provide the context or mechanism through which delegation occurs. The delegating object can access and interact with the delegate through the association. The association relationship can establish the connection necessary for delegation to take place.

In summary, association and delegation are related in the sense that delegation can occur within the context of an association. The association provides the linkage between objects, and the delegation allows one object to delegate specific responsibilities to another object, leveraging their specialized behavior.


Is composition related to delegation?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Composition and delegation are distinct concepts in object-oriented programming, but they can be related and often coexist in system design.

Composition refers to a strong "whole-part" relationship between objects, where the lifetime of the parts is tightly coupled with the lifetime of the whole. In composition, an object is composed of one or more component objects, and the components cannot exist independently outside of the composite object. The composite object takes responsibility for creating, managing, and coordinating the behavior of its component objects.

Delegation, on the other hand, is a technique where an object (delegator) hands off a specific task or responsibility to another object (delegate). The delegating object relies on the specialized behavior of the delegate object to perform that task.

In practice, delegation is often used within the context of composition. A composite object may delegate certain tasks or responsibilities to its component objects, allowing the components to handle specific aspects of functionality while the composite object orchestrates their collaboration. This delegation of tasks promotes modularity, code reuse, and separation of concerns.

By combining composition and delegation, complex behaviors can be achieved through a hierarchical organization of objects, where a composite object delegates tasks to its component objects, each responsible for a specific aspect of functionality.

For example, consider a composite object representing a car. The car object may internally contain component objects such as an engine, wheels, and a steering system. The car object, acting as the delegator, can delegate tasks like accelerating, turning, or braking to its component objects (delegate), which are specialized to handle those specific tasks. The delegation allows the car object to coordinate the overall behavior of the car while leveraging the specific functionalities provided by its components.

In summary, composition and delegation are related in the sense that delegation can occur within the context of composition. Composition establishes the strong whole-part relationship between objects, while delegation allows the composite object to delegate specific responsibilities to its component objects to achieve modular and specialized behavior.


What's the difference, if any, between composition and aggregation?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Composition and aggregation are both forms of object relationships in object-oriented programming, but they differ in terms of the strength of the relationship and the lifecycle dependency between the objects involved. Here's a breakdown of the differences:

Composition:

1. Strong Relationship: Composition represents a strong relationship between objects, where one object (the whole) is composed of other objects (the parts). The parts are owned by the whole, and their existence is tightly coupled with the existence of the whole.
2. Exclusive Ownership: In composition, the whole object takes ownership and responsibility for creating, managing, and destroying its component objects. The lifetime of the parts is dependent on the lifetime of the whole.
3. No Independent Existence: The parts typically do not have an independent existence outside of the whole object. They are created and destroyed as part of the whole, and their behavior is often tightly integrated with the overall behavior of the whole object.
4. Strong Encapsulation: Composition enforces strong encapsulation, as the internal structure and implementation details of the parts are typically not exposed to the external world. The whole object controls and encapsulates the behavior of its parts.

Aggregation:

1. Weaker Relationship: Aggregation represents a weaker relationship between objects, where one object (the aggregate) contains or is associated with other objects (the components). The components can exist independently of the aggregate object.
2. Shared Ownership: In aggregation, the components are not owned by the aggregate object. They may have their own independent lifecycles and can be shared between multiple aggregate objects.
3. Independent Existence: The components can exist outside of the aggregate object and can be associated with multiple aggregates or exist on their own.
4. Shared Responsibility: Unlike in composition, the components in aggregation can have their own behavior and responsibilities that are not solely governed by the aggregate object.
5. Weaker Encapsulation: Aggregation allows for looser encapsulation, as the components may have their own interfaces and can be accessed directly by external objects, independent of the aggregate object.

In summary, composition and aggregation differ in the strength of the relationship, ownership, lifecycle dependency, and encapsulation. Composition represents a strong ownership relationship with exclusive ownership and tight lifecycle dependency, while aggregation represents a looser relationship with shared ownership and independent existence of the components.

Here's an example that illustrates the concept of aggregation:

Consider a university system where a Department object represents a department within the university, and a Professor object represents a faculty member. In this scenario:

- Aggregation: The Department aggregates Professor objects as its faculty members. Multiple professors can be associated with a department, and they can exist independently outside of the department.

Example:

.. code-block:: java

   public class Professor {
       private String name;
       private String specialization;

       // Constructor, getters, and setters
   }

   public class Department {
       private String name;
       private List<Professor> faculty;

       // Constructor, getters, and setters
       public void addProfessor(final Professor professor) {
	   faculty.add(professor);
       }

       public void removeProfessor(final Professor professor) {
	   faculty.remove(professor);
       }
   }


In this example, the Department class has an aggregation relationship with the Professor class. Each Department object maintains a list of Professor objects as its faculty members. Professors can exist independently and can be associated with multiple departments or even exist without any department affiliation.

The Department class aggregates Professor objects by providing methods to add or remove professors from its faculty list. This allows the Department object to associate and interact with multiple Professor objects while maintaining their independent existence.

This aggregation relationship provides flexibility in terms of professors being able to switch departments or be associated with multiple departments without being tightly coupled to any specific department.

In summary, the aggregation relationship allows for the association of multiple objects while maintaining their independent existence and provides a looser relationship compared to composition.


 Here's an example of composition using the car analogy:

.. code-block:: java

   public class Engine {
       public void start() {
	       // Code to start the engine
	       System.out.println("Engine started.");
       }

       public void stop() {
	       // Code to stop the engine
	       System.out.println("Engine stopped.");
       }
   }

   public record Wheel(int size) {
       public void rotate() {
	   // Code to rotate the wheel
	       System.out.println("Wheel rotating.");
       }
   }

   public class Car {
       private Engine engine;
       private List<Wheel> wheels;

       public Car() {
	       engine = new Engine();
           wheels = List.of(new Wheel(18), new Wheel(18), new Wheel(18), new Wheel(18));
       }

       public void startCar() {
           engine.start();
           System.out.println("Car started.");
       }

       public void stopCar() {
	       engine.stop();
	       System.out.println("Car stopped.");
       }

       public void drive() {
	   for (final var wheel : wheels) {
	       wheel.rotate();
	   }
	   System.out.println("Car is driving.");
       }
   }

   public class Main {
       public static void main(final String[] args) {
	       final var car = new Car();
	       car.startCar();
	       car.drive();
	       car.stopCar();
       }
   }


In this example, we have three classes: `Engine`, `Wheel`, and `Car`. The `Car` class composes an `Engine` object and a list of `Wheel` objects. The `Car` class creates and owns these objects, and their lifetimes are tied to the lifetime of the `Car` object.

When the `Car` object is created, it initializes its `Engine` and creates four `Wheel` objects. The `Car` class encapsulates the behavior of the engine and wheels and provides methods to start the car, stop the car, and drive the car.

In the `Main` class, we create a `Car` object and invoke the `startCar()`, `drive()`, and `stopCar()` methods to demonstrate the composition relationship. The `Car` object delegates the responsibility of starting the engine and rotating the wheels to its composed objects, providing the functionality of a fully functioning car.

Executing the code will produce the following output:


.. code-block::
   
   Engine started.
   Car started.
   Wheel rotating.
   Wheel rotating.
   Wheel rotating.
   Wheel rotating.
   Car is driving.
   Engine stopped.
   Car stopped.


This example demonstrates how the `Car` object composes the `Engine` and `Wheel` objects, utilizing their behaviors and encapsulating them within its own functionality.


.. csv-table:: Comparison among object relationships
    :header: "Feature", "Composition", "Aggregation", "Association"
    :widths: 25, 25, 25, 25

    "Relationship", "Strong 'whole-part' relationship", "Weak 'whole-part' relationship", "Semantically related but independent"
    "Dependency", "Strong", "Weak", "Weak"
    "Lifespan", "Contained object depends on the container object", "Independent object can exist independently", "Independent object can exist independently"
    "Navigation", "Unidirectional (one-way)", "Unidirectional (one-way)", "Bidirectional (two-way)"
    "Ownership", "Owner has full ownership of the contained objects", "No ownership relationship, objects can exist independently", "No ownership relationship, objects can exist independently"
    "Responsibility", "Owner is responsible for the existence and behavior of the contained objects", "No specific responsibility for the lifecycle of the aggregated objects", "No specific responsibility for the associated objects"
    "Encapsulation", "Strong encapsulation, contained objects are encapsulated within the owner", "Loose encapsulation, aggregated objects are not encapsulated within the owner", "Loose encapsulation, associated objects are not encapsulated within each other"
    "Cardinality", "Typically one-to-one or one-to-many", "Typically one-to-many or many-to-many", "Can be one-to-one, one-to-many, or many-to-many"
    "Example", "Car and Engine", "University and Student", "Teacher and Student"



.. csv-table::
   :header: "Feature", "Composition", "Aggregation", "Association", "Method Parameter Dependency"
   :widths: 25, 25, 25, 25, 25

   "Relationship", "Strong 'whole-part' relationship", "Weak 'whole-part' relationship", "Semantically related but independent", "Method relies on objects passed as parameters"
   "Common Name", "Contains relationship", "Uses relationship", "Related-to relationship", "Parameter dependency"
   "Dependency", "Strong", "Weak", "Weak", "Strong"
   "Lifespan", "Contained object depends on the container object", "Independent object can exist independently", "Independent object can exist independently", "Dependent on parameter objects"
   "Navigation", "Unidirectional (one-way)", "Unidirectional (one-way)", "Bidirectional (two-way)", "Unidirectional (one-way)"
   "Ownership", "Owner has full ownership of the contained objects", "No ownership relationship, objects can exist independently", "No ownership relationship, objects can exist independently", "No ownership relationship, objects can exist independently"
   "Responsibility", "Owner is responsible for the existence and behavior of the contained objects", "No specific responsibility for the lifecycle of the aggregated objects", "No specific responsibility for the associated objects", "Method has responsibility for handling the parameter objects"
   "Encapsulation", "Strong encapsulation, contained objects are encapsulated within the owner", "Loose encapsulation, aggregated objects are not encapsulated within the owner", "Loose encapsulation, associated objects are not encapsulated within each other", "No encapsulation relationship"
   "Cardinality", "Typically one-to-one or one-to-many", "Typically one-to-many or many-to-many", "Can be one-to-one, one-to-many, or many-to-many", "N/A"
   "Example", "Car and Engine", "University and Student", "Teacher and Student", "Method that calculates the sum of numbers"


.. You can copy this ReST table code and include it in your Sphinx document. Feel free to adjust the table headers, widths, or content as needed.

Only observable relationships matter
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


*If a relationship between class and another class is purely internal, without public members to observe the relationship, it's as if it didn't exist, right? For example, if class A has a private field of class B but class B doesn't occur in any constructor or method parameters or return types, we shouldn't say A has-a B, should we?*

Yes, you are correct. If a relationship between two classes is purely internal and not observable from outside the class, it can be considered as if it doesn't exist in terms of the class's public interface. In the scenario you described, where class A has a private field of class B but class B doesn't occur in any constructor or method parameters or return types, we wouldn't typically say that class A "has-a" relationship with class B.

The concept of "has-a" relationship usually implies that a class directly incorporates or contains another class as a part of its public interface, visible to external entities. It signifies a stronger association where the presence of the associated class is observable and relevant to the class's behavior and interactions.

In your example, since class B is not part of class A's public interface and is purely internal, it wouldn't be accurate to describe it as a "has-a" relationship. The internal usage of class B within class A is an implementation detail, and class B's existence is not visible or relevant to external entities interacting with class A.

However, it's worth noting that the internal usage of class B can still be important for the implementation and internal functioning of class A. It helps encapsulate the necessary behavior and state within class A without exposing the details of class B to external entities.

In summary, if a relationship between two classes is purely internal and not observable from outside the class, it is not typically described as a "has-a" relationship in terms of the class's public interface.

If you have any further questions or need additional clarification, please let me know!

Maps
-----

*Which is the Swiss army knife of data structures?*

The "Swiss army knife" of data structures is often considered to be the "Array." Arrays are versatile and widely used data structures that offer flexibility in storing and accessing elements.

Here are some reasons why arrays can be considered the Swiss army knife of data structures:

1. Random Access: Arrays allow direct access to elements using their index. This enables efficient and fast retrieval of elements, making arrays suitable for various operations.

2. Sequential Storage: Arrays store elements in contiguous memory locations, allowing efficient traversal and processing of elements in a sequential manner.

3. Simple and Efficient: Arrays have a straightforward structure and memory representation, making them efficient in terms of memory usage and access time.

4. Support for Various Data Types: Arrays can store elements of any data type, including primitive types and objects. They provide a uniform approach to handling different types of data.

5. Flexibility in Size: Arrays can be dynamically resized or resized at runtime, allowing for flexibility in accommodating changing data requirements.

6. Support for Multidimensionality: Arrays can be multidimensional, enabling the organization and manipulation of data in multiple dimensions or matrices.

7. Wide Language Support: Arrays are supported by most programming languages, making them a universal data structure for developers.

While arrays have numerous benefits, it's important to note that they also have limitations. They have a fixed size once created, which can cause issues when needing to resize frequently. Additionally, inserting or deleting elements in the middle of an array can be inefficient due to the need for shifting elements.

Overall, arrays provide a powerful and widely applicable data structure that can serve various purposes, making them often referred to as the Swiss army knife of data structures.

If you have any further questions, feel free to ask!


*But arrays are so limited in terms of their key type. Can you think of a generalization of array that is very widely usable?*

Yes, arrays have limitations in terms of their fixed size and the requirement for elements to have consecutive indices. If you're looking for a more generalized and widely usable data structure, one option is the "List" data structure.

Lists are a more flexible and dynamic alternative to arrays. They provide a collection of elements that can grow or shrink dynamically as needed. Lists can handle various types of elements and offer extensive functionality for adding, removing, and accessing elements.

Here are some reasons why lists can be considered a widely usable data structure:

1. Dynamic Size: Lists can dynamically adjust their size to accommodate new elements or remove existing ones. This flexibility makes lists suitable for scenarios where the number of elements can change over time.

2. Insertion and Removal: Lists provide efficient insertion and removal operations, including inserting elements at specific positions or removing elements from any location. These operations can be performed without the need to shift or rearrange other elements.

3. Random Access: Lists typically provide random access to elements using their index, similar to arrays. This enables efficient element retrieval based on their position.

4. Various Implementations: Lists have different implementations, such as ArrayList, LinkedList, and more, each offering specific trade-offs in terms of access time, memory usage, and specific operations.

5. Widely Supported: Lists are available in most programming languages and are widely supported by libraries and frameworks.

By utilizing lists, you gain the advantages of a dynamic and flexible data structure that can handle a wide range of element types and provide efficient operations for adding, removing, and accessing elements.

If you have any further questions or need additional information, feel free to ask!


.. todo:: move to SE course?


Software engineering principles
-------------------------------


What does beautiful code look like in the context of a CS2 course?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Beautiful code in the context of a CS2 course can be described as code that is well-organized, easy to read, and easy to understand. Here are a few characteristics of beautiful code:

1. Clarity: Beautiful code should be easy to understand and should clearly convey its purpose and functionality. This includes using meaningful variable and function names, writing comments when necessary, and organizing the code into logical blocks.

2. Simplicity: Beautiful code should be simple and straightforward. This means avoiding unnecessary complexity and using the simplest possible solution to achieve the desired functionality.

3. Modularity: Beautiful code should be modular, with each piece of code serving a specific purpose and being easily reusable in other parts of the program. This includes using functions and classes to organize code into logical modules.

4. Consistency: Beautiful code should be consistent in its style and formatting. This includes using consistent indentation, spacing, and naming conventions throughout the program.

5. Efficiency: Beautiful code should be efficient and optimized for performance. This includes using appropriate data structures and algorithms to minimize time and space complexity.

6. Error-handling: Beautiful code should handle errors gracefully, with appropriate error messages and error handling code that does not cause the program to crash or behave unexpectedly.

Overall, beautiful code in the context of a CS2 course should prioritize readability, simplicity, modularity, consistency, efficiency, and error-handling. By following these principles, students can create code that is not only functional, but also aesthetically pleasing and easy to work with.
