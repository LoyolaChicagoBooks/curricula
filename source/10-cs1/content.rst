CS1 - Introduction to CS (LUC COMP 170)
=========================================

About the Curriculum
---------------------

The Association for Computing Machinery (ACM) is a leading international organization for computing professionals, and they periodically release guidelines for computing curricula to help educational institutions design their programs.

The ACM curriculum guidelines cover various aspects of computing education, including computer science, information systems, information technology, software engineering, and cybersecurity. These guidelines aim to provide a framework for colleges and universities to develop comprehensive, relevant, and up-to-date computing programs.

Here are some key components of the ACM computing curriculum:

- Core knowledge areas: The curriculum is divided into several knowledge areas, such as algorithms and complexity, programming languages, software development fundamentals, systems, and computer organization and architecture.

- Elective knowledge areas: In addition to the core knowledge areas, the ACM curriculum also offers elective areas to allow students to specialize in specific topics, such as artificial intelligence, human-computer interaction, and data science.

- Skill development: The curriculum emphasizes the development of skills such as problem-solving, critical thinking, communication, and teamwork.

- Ethical considerations: The ACM curriculum incorporates ethical considerations in computing, such as understanding the social impact of technology, privacy issues, and professional responsibility.

- Project-based learning: The curriculum encourages hands-on, project-based learning to help students apply their knowledge in real-world situations.

- Continuous improvement: The ACM regularly updates its curriculum guidelines to keep up with the rapidly evolving field of computing.

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

Variables and Data Types
^^^^^^^^^^^^^^^^^^^^^^^^

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


Refactor Animal and Dog example with an interface that has all common methods?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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


.. note:: More of the top 15 coming...
