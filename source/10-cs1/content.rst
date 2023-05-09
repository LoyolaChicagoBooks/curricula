Introduction to CS (CS1 / LUC COMP 170)
========================================

What does CS1 mean with respect to the ACM Computing Curricula?
-----------------------------------------------------------------

CS1, short for "Computer Science 1," refers to the first course in an introductory computer science sequence, as recommended by the ACM Computing Curricula. CS1 typically serves as a foundation course for students pursuing degrees in computer science or related fields.

In the context of the ACM Computing Curricula, CS1 focuses on introducing students to the fundamentals of programming and problem-solving using computers. 

Here are the top 15 CS1 topics based on the ACM Computing Curricula, focusing on the foundational computer science concepts taught in an introductory course:

- Basic programming constructs: Understanding of variables, data types, expressions, operators, and control structures like conditional statements and loops.

- Functions (methods) and parameter passing: Learning how to define and use functions (methods), as well as understanding parameter passing mechanisms such as pass-by-value and pass-by-reference.

- Basic input/output: Gaining the ability to read and write data from/to the console or simple external files.

- Program design and development: Familiarity with the process of designing, writing, and debugging programs using a high-level programming language.

- Basic data structures: Introduction to elementary data structures such as arrays, lists, strings, and basic operations on these structures.

- Recursion: Understanding recursive functions and their applications, as well as identifying and solving problems that can be addressed using recursion.

- Basic algorithm analysis: Learning to analyze the time and space complexity of simple algorithms using techniques like Big O notation.

- Basic problem-solving strategies: Developing the ability to decompose problems, devise algorithms, and implement solutions using appropriate data structures and control structures.

- Object-oriented programming concepts: Introduction to the principles of object-oriented programming, such as classes, objects, inheritance, and polymorphism.

- Basic software testing and debugging: Gaining the ability to write and use test cases, as well as learning basic debugging techniques.

- Version control: Introduction to the use of version control systems, such as Git, for managing and collaborating on code.

- Ethical and social considerations: Awareness of ethical aspects of computing, including the social impact of technology, privacy, and security.

- Basic computer organization: A high-level understanding of computer organization, such as the relationship between hardware and software components.

- Simple graphical user interface (GUI) programming: Introduction to basic GUI programming, including event-driven programming concepts and the use of GUI components.

- Documentation and code readability: Learning the importance of writing clear, well-documented code and using proper naming conventions and code formatting.

These topics provide a solid foundation in computer science for students in a CS1 course, preparing them for more advanced concepts and techniques in subsequent courses.

.. note:: Not all ACM/IEEE topics are about *programming*. The latest curricula are designed to place a more holistic emphasis on the profession of computing, including societal impacts. (We're particularly encouraged to see these picked up properly by our query to OpenAI.)

What are simple examples of the most important programming constructs in Java?
--------------------------------------------------------------------------------
- Variables and data types: Java has various data types such as int, double, char, boolean, and String for storing different types of data.

- Conditional statements: Java supports conditional statements like if-else and switch to execute code based on specific conditions.

- Loops: Java provides loop structures like for, while, and do-while for repeated execution of code until a certain condition is met.

- Functions (methods): Java allows you to define reusable pieces of code called functions (methods) to perform specific tasks.

- Basic input/output: Java has the ability to read and write data from/to the console and external files using classes like Scanner and BufferedReader for input, and System.out and FileWriter for output.

- Arrays: Java supports fixed-size arrays for storing and manipulating collections of elements of the same data type.

- Classes and objects: Java is an object-oriented programming language, which means it supports the creation and use of custom classes and objects to model real-world entities.

- Inheritance: Java allows classes to inherit properties and methods from other classes, promoting code reuse and modularity.

- Interfaces and abstract classes: Java supports the use of interfaces and abstract classes to define a contract or blueprint for classes, ensuring they implement specific methods.

- Exceptions and error handling: Java provides a mechanism to handle errors and exceptions that may occur during program execution, using try-catch blocks and custom exception classes.

Variables and Data Types
^^^^^^^^^^^^^^^^^^^^^^^^

Java has various data types such as int, double, char, boolean, and String for storing different types of data.

.. code-block:: java

   public class VariablesAndDataTypes {
       public static void main(String[] args) {
           int age = 25;
           double height = 175.5;
           char initial = 'A';
           boolean isStudent = true;
           String name = "Alice";
   
           System.out.println("Age: " + age);
           System.out.println("Height: " + height);
           System.out.println("Initial: " + initial);
           System.out.println("Is student: " + isStudent);
           System.out.println("Name: " + name);
       }
   }


Conditional Statements (if-else)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Java supports conditional statements like if-else and switch to execute code based on specific conditions.

.. code-block:: java

   public class ConditionalStatements {
       public static void main(String[] args) {
           int number = 42;
   
           if (number % 2 == 0) {
               System.out.println("The number is even.");
           } else {
               System.out.println("The number is odd.");
           }
       }
   }
   

Loops (for and while)
^^^^^^^^^^^^^^^^^^^^^^

Java provides loop structures like for, while, and do-while for repeated execution of code until a certain condition is met.

.. code-block:: java

   public class Loops {
       public static void main(String[] args) {
           System.out.println("For loop:");
           for (int i = 1; i <= 5; i++) {
               System.out.println("Iteration " + i);
           }
   
           System.out.println("While loop:");
           int count = 1;
           while (count <= 5) {
               System.out.println("Iteration " + count);
               count++;
           }
       }
   }
   

Functions
^^^^^^^^^^^
  
Functions (methods): Java allows you to define reusable pieces of code called functions (methods) to perform specific tasks.

.. code-block:: java

   public class Functions {
       public static void main(String[] args) {
           int a = 3;
           int b = 4;
           int sum = add(a, b);
           System.out.println("The sum of " + a + " and " + b + " is " + sum);
       }
   
       public static int add(int x, int y) {
           return x + y;
       }
   }
   

Basic I/O
^^^^^^^^^^^

Java has the ability to read and write data from/to the console and external files using classes like Scanner and BufferedReader for input, and System.out and FileWriter for output.

.. code-block:: java

   import java.util.Scanner;
   
   public class BasicInputOutput {
       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);
   
           System.out.print("Enter your name: ");
           String name = scanner.nextLine();
   
           System.out.print("Enter your age: ");
           int age = scanner.nextInt();
   
           System.out.println("Hello, " + name + "! You are " + age + " years old.");
       }
   }

Arrays
^^^^^^^

Java supports fixed-size arrays for storing and manipulating collections of elements of the same data type.

.. code-block:: java

   public class BasicArrays {
       public static void main(String[] args) {
           int[] numbers = new int[5];
   
           // Assign values to array elements
           for (int i = 0; i < numbers.length; i++) {
               numbers[i] = i + 1;
           }
   
           // Print array elements
           for (int number : numbers) {
               System.out.println(number);
           }
       }
   }


Classes and Objects
^^^^^^^^^^^^^^^^^^^^^

Classes and objects: Java is an object-oriented programming language, which means it supports the creation and use of custom classes and objects to model real-world entities.

.. code-block:: java

   class Person {
       String name;
       int age;
   
       void introduce() {
           System.out.println("Hello, my name is " + name + " and I am " + age + " years old.");
       }
   }
   
   public class ClassesAndObjects {
       public static void main(String[] args) {
           Person person = new Person();
           person.name = "Alice";
           person.age = 30;
   
           person.introduce();
       }
   }

Inheritance
^^^^^^^^^^^^

Java allows classes to inherit properties and methods from other classes, promoting code reuse and modularity.

.. code-block:: java

   class Animal {
       void makeSound() {
           System.out.println("The animal makes a sound");
       }
   }
   
   class Dog extends Animal {
       @Override
       void makeSound() {
           System.out.println("The dog barks");
       }
   }
   
   public class InheritanceExample {
       public static void main(String[] args) {
           Dog dog = new Dog();
           dog.makeSound();
       }
   }


Interfaces and Abstract Classes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Interfaces and abstract classes: Java supports the use of interfaces and abstract classes to define a contract or blueprint for classes, ensuring they implement specific methods.

.. code-block:: java

   interface Shape {
       double area();
       double perimeter();
   }
   
   class Rectangle implements Shape {
       double width;
       double height;
   
       Rectangle(double width, double height) {
           this.width = width;
           this.height = height;
       }
   
       @Override
       public double area() {
           return width * height;
       }
   
       @Override
       public double perimeter() {
           return 2 * (width + height);
       }
   }

   public class InterfacesAndAbstractClasses {
       public static void main(String[] args) {
           Rectangle rectangle = new Rectangle(5, 3);
           System.out.println("Area: " + rectangle.area());
           System.out.println("Perimeter: " + rectangle.perimeter());
       }
   }


Exceptions and Error Handling
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Java provides a mechanism to handle errors and exceptions that may occur during program execution, using try-catch blocks and custom exception classes.

.. code-block:: java

   public class ExceptionsAndErrorHandling {
       public static void main(String[] args) {
           int[] numbers = {1, 2, 3};
   
           try {
               System.out.println(numbers[3]);
           } catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Error: " + e.getMessage());
           }
       }
   }

Here's the ExceptionsAndErrorHandling example refactored to use a simple return code mechanism instead of exceptions:

.. code-block:: java

   public class SimpleErrorHandling {
   
       public static void main(String[] args) {
           int[] numbers = {1, 2, 3, 4, 5};
           int index = 5;
   
           int result = getElement(numbers, index);
           if (result != -1) {
               System.out.println("Element at index " + index + " is: " + result);
           } else {
               System.out.println("Error: Invalid index " + index);
           }
       }
   
       public static int getElement(int[] array, int index) {
           if (index >= 0 && index < array.length) {
               return array[index];
           } else {
               return -1;
           }
       }
   }

In this refactored version, the ``getElement()`` method returns -1 if the index is out of bounds, indicating an error. The main method checks the return value and, if it's not -1, prints the element at the specified index. Otherwise, it prints an error message. Keep in mind that this approach assumes that -1 is not a valid value in the array. In a more generic solution, you could use an optional type or a custom result object to handle error cases.


Refactor Animal and Dog example with an interface that has all common methods?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We tend to think in terms of interfaces instead of inheritance whenever possible.
We asked Chat-GPT4 to refactor this example to use interfaces instead of inheritance.
This is the result.

.. code-block:: java

   interface Animal {
       void makeSound();
   }
   
   class Dog implements Animal {
       @Override
       public void makeSound() {
           System.out.println("The dog barks");
       }
   }
   
   public class InheritanceRefactor {
       public static void main(String[] args) {
           Dog dog = new Dog();
           dog.makeSound();
       }
   }


Refactor: Animal not a good name for an interface. Use WhatAnimalsDo instead.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

``Animal`` would be fine for inheritance. But it's less of a good name for an interface.
We asked to refactor ``Animal`` to ``WhatAnimalsDo``. This also allows for us to define other interfaces associated with animals.

.. code-block:: java

   interface WhatAnimalsDo {
       void makeSound();
   }
   
   class Dog implements WhatAnimalsDo {
       @Override
       public void makeSound() {
           System.out.println("The dog barks");
       }
   }
   
   public class InheritanceRefactor {
       public static void main(String[] args) {
           Dog dog = new Dog();
           dog.makeSound();
       }
   }


Refactor: Add two other animals...
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

And this shows how to add additional animals....

.. code-block:: java

   interface WhatAnimalsDo {
       void makeSound();
   }
   
   class Dog implements WhatAnimalsDo {
       @Override
       public void makeSound() {
           System.out.println("The dog barks");
       }
   }
   
   class Cat implements WhatAnimalsDo {
       @Override
       public void makeSound() {
           System.out.println("The cat meows");
       }
   }
   
   class Bird implements WhatAnimalsDo {
       @Override
       public void makeSound() {
           System.out.println("The bird sings");
       }
   }
   
   public class InheritanceRefactor {
       public static void main(String[] args) {
           Dog dog = new Dog();
           dog.makeSound();
   
           Cat cat = new Cat();
           cat.makeSound();
   
           Bird bird = new Bird();
           bird.makeSound();
       }
   }



How do these Java topics map to the CS1 curricula and ACM/IEEE?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: George to finish.



