CS1 - Introduction to CS
=========================

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

In the context of the ACM Computing Curricula, CS1 focuses on introducing students to the fundamentals of programming and problem-solving using computers. Key topics often covered in a CS1 course include:

- Basic programming constructs: Students learn programming concepts such as variables, data types, loops, conditionals, functions, and basic input/output.

- Algorithms and problem-solving: Students are introduced to algorithmic thinking and develop problem-solving skills to design, implement, and test solutions for various computing problems.

- Program design and development: Students learn the process of designing, writing, and debugging programs using a high-level programming language, often Python, Java, or C++.

- Basic data structures: Students get introduced to elementary data structures such as arrays, lists, and strings, which help them manipulate and store data efficiently.

- Ethical and social considerations: The course may touch upon ethical aspects of computing, including the social impact of technology, privacy, and security.

CS1 is typically followed by CS2, another foundational course that delves deeper into data structures, algorithms, and more advanced programming concepts. The ACM Computing Curricula provide guidelines for both CS1 and CS2 courses to ensure students receive a strong foundation in computer science fundamentals.

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

.. note:: More to come. These are just the top 5.

