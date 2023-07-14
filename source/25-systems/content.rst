Computer Systems
==================

Historical Term
   Computer Organization?

Loyola University Chicago
  `COMP 264 <https://academics.cs.luc.edu/courses/comp264.html>`__

.. note:: George


Systems Curriculum via ACM/IEEE
--------------------------------

Here's the mapping to the ACM/IEEE Computer Science Curricula 2013 (CS2013) Knowledge Area and Knowledge Unit codes, which is the latest available version as of my training cut-off in September 2021.

#. **Introduction to Computer Systems**: 
    - [PL/Intro] Programming Languages: Introduction
    - [CN/Intro] Information and Communication Technology Literacy: Foundations

#. **Number Systems**: 
    - [DS/BasicLogic] Discrete Structures: Basic Logic
    - [DS/NumberTheory] Discrete Structures: Number Theory

#. **Computer Hardware**: 
    - [AR/Overview] Architecture and Organization: Overview
    - [AR/MachineLevel] Architecture and Organization: Machine Level Representation of Data

#. **Data Representation**: 
    - [AR/MachineLevel] Architecture and Organization: Machine Level Representation of Data
    - [DS/Data] Discrete Structures: Data Representation

#. **Instruction Set Architecture (ISA)**: 
    - [AR/ISA] Architecture and Organization: Instruction Set Architectures
    - [AR/MemoryArch] Architecture and Organization: Memory Architectures

#. **Assembly Language**: 
    - [PL/Languages] Programming Languages: Language Translation and Execution

#. **Computer Arithmetic**: 
    - [AR/ALU] Architecture and Organization: Digital Logic and Digital Systems
    - [AR/MemoryArch] Architecture and Organization: Memory Architectures

#. **Central Processing Unit (CPU)**: 
    - [AR/FunctionalOrg] Architecture and Organization: Functional Organization
    - [AR/MultiLevel] Architecture and Organization: Multi-Level Machine Organization

#. **Memory Hierarchy**: 
    - [AR/MemoryArch] Architecture and Organization: Memory Architectures
    - [AR/MultiLevel] Architecture and Organization: Multi-Level Machine Organization

#. **Input/Output Systems**: 
    - [AR/IOFund] Architecture and Organization: Interfacing and Communication
    - [AR/Dependability] Architecture and Organization: Dependability

#. **Operating Systems**: 
    - [OS/Overview] Operating Systems: Overview
    - [OS/Concurrency] Operating Systems: Concurrency

#. **Computer Networks**: 
    - [CN/Overview] Networking and Communication: Introduction
    - [CN/Architecture] Networking and Communication: Network Architecture

Remember that the mapping might not be 100% precise because some universities and colleges may choose to emphasize different topics or structure their courses slightly differently based on local circumstances or unique academic perspectives. Also, ACM/IEEE curriculum is periodically updated, and you should refer to the latest version for the most accurate information.

Programming Languages for Systems
-----------------------------------

What are the most commonly used programming languages in systems programming, e.g. embedded systems and operating systems?

C
^^
Developed in the early 1970s, C is a low-level language that provides a high degree of control over system hardware. It's used to write everything from operating systems (the most notable being Unix) to embedded systems.

C++
^^^
An extension of the C language, C++ includes everything C has but also adds support for object-oriented programming. It is used extensively in systems programming, game development, and real-time systems.

Rust
^^^^
Rust is a newer system programming language that aims to provide the low-level access of C and C++ but with a greater emphasis on safety, particularly memory safety. It's gaining popularity for system-level tasks, including being used in the development of new components for the Microsoft Windows operating system, Firefox web browser and more.

Assembly
^^^^^^^^
Assembly language is used when absolute control over the system is required, or in time or space-constrained environments like bootloaders or firmware. It is specific to individual CPU architectures.

Ada
^^^
Ada is a statically typed, structured, imperative, and object-oriented high-level language, extended from Pascal and other languages. It was developed by the U.S. Department of Defense for use in embedded systems and is common in safety- and mission-critical systems such as avionics and defense.

Go
^^
While Go is a higher-level language, its efficiency and simplicity have made it popular for certain system-level programming tasks, particularly in networking and infrastructure.

Information and Communication Technology Literacy: Foundations
-----------------------------------------------------------------

- **Fundamental Concepts**: Understanding the basic concepts related to ICT, including hardware, software, networks, and the internet.

- **ICT Literacy**: Understanding the capabilities and limitations of ICT. It involves recognizing when information is needed and possessing the ability to locate, evaluate, and use the needed information effectively.

- **Basic Operational Skills**: Being able to operate common software tools (e.g., word processors, spreadsheets, browsers), managing files and folders, and understanding operating systems.

- **Online Communication**: Understanding the various modes of online communication, such as email, social networking, forums, online collaboration tools, etc., and their appropriate use.

- **Digital Citizenship**: Understanding the ethical, cultural, and societal issues related to ICT, including information privacy, intellectual property rights, and cyberbullying.

- **Online Safety and Security**: Understanding basic principles of online safety, including secure passwords, two-factor authentication, recognizing phishing attempts, and safe web browsing habits.

- **Basic Problem-Solving with ICT**: Understanding how to use ICT to solve simple problems, including searching for information, using software tools, and troubleshooting basic hardware and software issues.

The "Information and Communication Technology (ICT) Literacy: Foundations" component within the ACM/IEEE computer science curricula is about understanding the foundational concepts and competencies for using computer-based technologies. It includes, but is not limited to, the following topics:


Basic Logic
--------------

Here are 15 key Basic Logic ideas shown in the Go Language:

Conjunction (AND)
^^^^^^^^^^^^^^^^^^^

The AND operation returns true if both of its operands are true.

.. code-block:: go

    a := true
    b := false
    result := a && b
    fmt.Println(result) // Prints: false

Disjunction (OR)
^^^^^^^^^^^^^^^^^

The OR operation returns true if at least one of its operands is true.

.. code-block:: go

    a := true
    b := false
    result := a || b
    fmt.Println(result) // Prints: true

Negation (NOT)
^^^^^^^^^^^^^^^

The NOT operation returns the inverse of its operand.

.. code-block:: go

    a := true
    result := !a
    fmt.Println(result) // Prints: false

Conditional (IF-THEN)
^^^^^^^^^^^^^^^^^^^^^^

In programming, this is represented by an if statement. The code inside the if block runs only if the condition is true.

.. code-block:: go

    a := true
    if a {
        fmt.Println("The condition is true.") // Prints: The condition is true.
    }

Biconditional (IF AND ONLY IF)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This is similar to a conditional, but the code also runs if both the condition and the result are false.

.. code-block:: go

    a := true
    b := true
    if a == b {
        fmt.Println("Both are true or both are false.") // Prints: Both are true or both are false.
    }


Truth Tables
^^^^^^^^^^^^^^

A truth table is a mathematical table used in logic to compute the functional values of logical expressions for each possible value of their variables.

.. code-block:: go

    fmt.Println("AND Truth Table")
    fmt.Println("true AND true =", true && true)
    fmt.Println("true AND false =", true && false)
    fmt.Println("false AND true =", false && true)
    fmt.Println("false AND false =", false && false)

Logical Equivalence
^^^^^^^^^^^^^^^^^^^^^

Two statements are logically equivalent if they have the same truth value in all cases. We can demonstrate this with Go code, comparing the truth values of two expressions.

.. code-block:: go

    a := true
    b := false
    fmt.Println((a && b) == (b && a)) // Logical equivalence of AND operation, prints: true

De Morgan's Laws
^^^^^^^^^^^^^^^^^^

These are two transformation rules that are both valid for sets and logic. In Go, we can demonstrate De Morgan's laws as follows.

.. code-block:: go

    a := true
    b := false
    fmt.Println(!a || !b == !(a && b)) // Verifies the first De Morgan's law, prints: true
    fmt.Println(!a && !b == !(a || b)) // Verifies the second De Morgan's law, prints: true

Conditional Statements
^^^^^^^^^^^^^^^^^^^^^^^^

A conditional statement, symbolized by P Q, is an if-then statement in which P is a hypothesis and Q is a conclusion. In Go, we can represent a simple conditional statement as follows.

.. code-block:: go

    p := true // Hypothesis
    q := false // Conclusion
    if p {
        fmt.Println(q) // If p (hypothesis) is true, prints the value of q (conclusion)
    }

Biconditional Statements
^^^^^^^^^^^^^^^^^^^^^^^^^^^

A biconditional statement is defined to be true whenever both parts have the same truth value. In Go, we can demonstrate a simple biconditional statement as follows.


.. code-block:: go

    p := true // Part 1
    q := true // Part 2
    fmt.Println((p && q) || (!p && !q)) // Prints: true, because both p and q are true

Logical Implication
^^^^^^^^^^^^^^^^^^^^^
Logical implication is a type of logical operation that results in true whenever the premise is false, or the premise and the conclusion are both true. In Go, we can demonstrate this operation as follows.

.. code-block:: go

    p := false // Premise
    q := true // Conclusion
    fmt.Println(!p || q) // Prints: true, because the premise is false

Exclusive OR (XOR)
^^^^^^^^^^^^^^^^^^^^^

The XOR operation (also known as "exclusive disjunction") returns true if exactly one of its operands (but not both) is true. In Go, we can demonstrate this operation as follows.

.. code-block:: go

    a := true
    b := false
    fmt.Println((a || b) && !(a && b)) // Prints: true, because exactly one of a and b is true

NAND and NOR Operations
^^^^^^^^^^^^^^^^^^^^^^^^^^

NAND (NOT AND) and NOR (NOT OR) are logical operations that are the inverse of the AND and OR operations, respectively. In Go, we can demonstrate these operations as follows.

.. code-block:: go

    a := true
    b := false
    fmt.Println(!(a && b)) // NAND operation, prints: true
    fmt.Println(!(a || b)) // NOR operation, prints: false

Logical Operators with Non-Boolean Values
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In many programming languages, logical operators can be used with non-boolean values, and the language's truthy and falsy values will be used to determine the result. In Go, we can demonstrate this concept as follows.

.. code-block:: go

    var a error = nil // A nil error is considered "falsy"
    var b error = errors.New("error") // A non-nil error is considered "truthy"
    fmt.Println(a == nil || b != nil) // Prints: true, because a is falsy and b is truthy

Short-Circuit Evaluation
^^^^^^^^^^^^^^^^^^^^^^^^^^

Many programming languages, including Go, use short-circuit evaluation for logical operations, meaning the second argument is only evaluated if the first argument does not determine the result. This is an important concept in preventing errors from invalid operations in logical expressions.

.. code-block:: go

    a := true
    b := false
    fmt.Println(a || b) // Prints: true, and b is never evaluated because a is true


ARM Assembly Language Versions
---------------------------------

Truth Tables
^^^^^^^^^^^^

Truth tables show the outcome of all possible inputs of a logic gate. While ARM assembly does not directly support the creation of truth tables, the results of logic gates can be computed and stored in registers.

Logical Equivalence
^^^^^^^^^^^^^^^^^^^

ARM assembly can compare two values and set the condition codes based on the result, which can be used to test logical equivalence. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    MOV R1, #1      ; Load 1 into R1
    CMP R0, R1      ; Compare R0 with R1
    BEQ equivalent  ; If R0 equals R1, branch to 'equivalent'

De Morgan's Laws
^^^^^^^^^^^^^^^^

De Morgan's laws state that the negation of a conjunction is the disjunction of the negations, and the negation of a disjunction is the conjunction of the negations. This can be demonstrated using bitwise operations in ARM assembly, but the implementation is nontrivial.

Conditional Statements
^^^^^^^^^^^^^^^^^^^^^^

Conditional execution in ARM assembly is handled by condition codes. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    CMP R0, #1      ; Compare R0 with 1
    BEQ true_branch ; If R0 equals 1, branch to 'true_branch'
    B false_branch  ; Otherwise, branch to 'false_branch'

Biconditional Statements
^^^^^^^^^^^^^^^^^^^^^^^^

A biconditional statement in ARM assembly can be represented as two conditional branches. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    MOV R1, #1      ; Load 1 into R1
    CMP R0, R1      ; Compare R0 with R1
    BEQ true_branch ; If R0 equals R1, branch to 'true_branch'
    B false_branch  ; Otherwise, branch to 'false_branch'


Alright, here are the remaining 10 logic concepts, along with brief explanations of how they might be implemented in ARM Assembly. 

Logical Implication
^^^^^^^^^^^^^^^^^^^

Logical implication can be expressed using conditional execution. Here is an example where if R0 is true, R1 is checked. 

.. code-block:: asm

    CMP R0, #1
    BEQ check_R1
    B end
    check_R1:
    CMP R1, #1
    BNE not_implied
    end:
    ; R0 implies R1

Exclusive OR (XOR)
^^^^^^^^^^^^^^^^^^

The XOR operation can be performed using the EOR instruction.

.. code-block:: asm

    MOV R0, #1
    MOV R1, #0
    EOR R2, R0, R1  ; R2 = R0 XOR R1

NAND and NOR Operations
^^^^^^^^^^^^^^^^^^^^^^^

NAND and NOR are not directly supported, but can be implemented using AND/OR and NOT.

.. code-block:: asm

    AND R2, R0, R1  ; R2 = R0 AND R1
    MVN R2, R2      ; R2 = NOT R2 (NAND)

    ORR R2, R0, R1  ; R2 = R0 OR R1
    MVN R2, R2      ; R2 = NOT R2 (NOR)

Logical Operators with Non-Boolean Values
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In assembly, non-zero values are often treated as true and zero as false. So, you might see code that uses non-boolean values with logical operators.

.. code-block:: asm

    CMP R0, #0   ; Compare R0 with 0
    BNE true_branch ; If R0 is not zero, branch to 'true_branch'

Short-Circuit Evaluation
^^^^^^^^^^^^^^^^^^^^^^^^

There's no direct equivalent of short-circuit evaluation in assembly. However, the behavior can be emulated through the use of conditional branching.

.. code-block:: asm

    CMP R0, #1   ; Compare R0 with 1
    BEQ end      ; If R0 is 1, branch to 'end' (skip the next instruction)
    CMP R1, #1   ; Compare R1 with 1 (only executed if R0 is not 1)
    end:

Truth Tables
^^^^^^^^^^^^

As an assembly language, ARM does not directly support data structures like tables. However, you could use an array of values to represent a truth table, and then loop through the array to perform operations.

Logical Equivalence
^^^^^^^^^^^^^^^^^^^

Logical equivalence can be demonstrated by comparing two values.

.. code-block:: asm

    CMP R0, R1  ; Compare R0 and R1
    BEQ equivalent ; If they are equal, branch to 'equivalent'

De Morgan's Laws
^^^^^^^^^^^^^^^^

De Morgan's laws are not directly supported in assembly. However, they could be implemented using a combination of AND, OR, and NOT operations, along with appropriate branching.

Conditional Statements
^^^^^^^^^^^^^^^^^^^^^^

Conditional statements can be represented with conditional branches in assembly.

.. code-block:: asm

    CMP R0, #1   ; Compare R0 with 1
    BEQ true_branch ; If R0 is 1, branch to 'true_branch'

Biconditional Statements
^^^^^^^^^^^^^^^^^^^^^^^^

Biconditional statements could be implemented with a sequence of conditional branches.

.. code-block:: asm

    CMP R0, R1   ; Compare R0 with R1
    BEQ true_branch ; If they are equal, branch to 'true_branch'
    B false_branch ; If they are not equal, branch to 'false_branch'


Please note that Assembly is a very low-level language and these concepts are quite abstract for such a language. Most of these tasks would be much easier and more intuitively performed in a higher-level language.

Here is a brief explanation of the ARM assembler instructions used in the above examples:

.. csv-table::
   :header: "Instruction", "Inputs", "Result"
   :widths: 20, 30, 50

   "MOV", "Source, Target", "Copies the value from Source into Target register."
   "CMP", "Operand1, Operand2", "Compares Operand1 with Operand2 and sets condition flags."
   "BEQ", "Label", "Branches to the specified Label if the result of the previous comparison was equal."
   "BNE", "Label", "Branches to the specified Label if the result of the previous comparison was not equal."
   "B", "Label", "Unconditionally branches to the specified Label."
   "AND", "Source, Target", "Performs a bitwise AND operation between the Source and Target, storing the result in the Target."
   "ORR", "Source, Target", "Performs a bitwise OR operation between the Source and Target, storing the result in the Target."
   "EOR", "Source, Target", "Performs a bitwise exclusive OR (XOR) operation between the Source and Target, storing the result in the Target."
   "MVN", "Source, Target", "Moves the bitwise NOT of the Source into the Target."


Number Theory Examples
-------------------------

.. note:: These are really more in line with discrete math topics, but I am structuring my prompts along the lines of ACM/IEEE curricula. I might move these to Discrete Math (and add math to them). These explanations provide a concise understanding of each concept's importance and how it works, allowing you to grasp their significance within Discrete Structures/Number Theory.

These explanations highlight the importance of each example within systems programming, showcasing their relevance in various optimization techniques, algorithm design, and efficient computation.

Prime Number Checking
^^^^^^^^^^^^^^^^^^^^^^^

Checking if a number is prime is crucial in cryptography, number theory, and algorithms. The function checks if a number `n` is divisible by any integer from 2 to the square root of `n`.

Prime number checking is important in systems programming for tasks such as generating cryptographic keys and optimizing algorithms.

.. code-block:: go

   func isPrime(n int) bool {
       if n <= 1 {
           return false
       }
       for i := 2; i*i <= n; i++ {
           if n%i == 0 {
               return false
           }
       }
       return true
   }

Greatest Common Divisor - GCD
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The GCD is used in various mathematical calculations, including simplifying fractions, finding modular inverses, and solving linear Diophantine equations. The function uses the Euclidean algorithm to iteratively find the GCD of two numbers `a` and `b`.

GCD calculations are useful in systems programming for tasks like optimizing memory allocation and implementing efficient algorithms.

.. code-block:: go

   func gcd(a, b int) int {
       for b != 0 {
           a, b = b, a%b
       }
       return a
   }


Least Common Multiple
^^^^^^^^^^^^^^^^^^^^^^^^

Lowest Common Multiple (LCM): The LCM is important in problems involving fractions, least common denominators, and scheduling. The function calculates the LCM of two numbers `a` and `b` by dividing their product by their GCD.

LCM calculations are relevant in systems programming for tasks such as scheduling processes and handling periodic tasks.

.. code-block:: go

   func lcm(a, b int) int {
       return a / gcd(a, b) * b
   }

Sieve of Eratosthenes (Simple)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sieve of Eratosthenes: Finding prime numbers is fundamental in number theory and cryptography. The function uses the Sieve of Eratosthenes algorithm to generate all prime numbers up to a given limit `n`.

The Sieve of Eratosthenes is valuable in systems programming for tasks like finding prime numbers efficiently and optimizing algorithms.

.. code-block:: go

   func sieveOfEratosthenes(n int) []int {
       primes := make([]bool, n+1)
       for i := 2; i <= n; i++ {
           primes[i] = true
       }
       p := 2
       for p*p <= n {
           if primes[p] {
               for i := p * p; i <= n; i += p {
                   primes[i] = false
               }
           }
           p++
       }

       var primeNumbers []int
       for i := 2; i <= n; i++ {
           if primes[i] {
               primeNumbers = append(primeNumbers, i)
           }
       }
       return primeNumbers
   }

Fibonacci sequence
^^^^^^^^^^^^^^^^^^^^^

Fibonacci Sequence: The Fibonacci sequence has applications in algorithms, mathematics, and nature. The function generates the Fibonacci sequence up to the `n`-th term.

The Fibonacci sequence has applications in systems programming for tasks such as optimizing algorithmic complexity and generating efficient code.

.. code-block:: go

   func fibonacci(n int) []int {
       fibSequence := make([]int, n+1)
       fibSequence[0], fibSequence[1] = 0, 1
       for i := 2; i <= n; i++ {
           fibSequence[i] = fibSequence[i-1] + fibSequence[i-2]
       }
       return fibSequence
   }


Checking if a number is a Fibonacci number
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Checking if a Number is Fibonacci: Identifying whether a number is part of the Fibonacci sequence is important in number theory and optimization problems. The function checks if a given number `n` is a Fibonacci number by verifying if either `5n^2 + 4` or `5n^2 - 4` is a perfect square.

Identifying Fibonacci numbers can be important in systems programming for optimizing algorithms and implementing efficient data structures.

.. code-block:: go

   func isFibonacci(n int) bool {
       x := 5*n*n + 4
       y := 5*n*n - 4
       return isPerfectSquare(x) || isPerfectSquare(y)
   }

   // Helper function to check if a number is a perfect square
   func isPerfectSquare(n int) bool {
       x := int(math.Sqrt(float64(n)))
       return x*x == n
   }

Factorial
^^^^^^^^^^^^

Factorial: The factorial is crucial in combinatorics, probability theory, and mathematical analysis. The function calculates the factorial of a non-negative integer `n` using an iterative approach.

Factorial calculations are relevant in systems programming for tasks like optimizing combinatorial algorithms and handling large-scale computations.

.. code-block:: go

   func factorial(n int) int {
       result := 1
       for i := 2; i <= n; i++ {
           result *= i
       }
       return result
   }

Permutations
^^^^^^^^^^^^^^^

Permutations (nPr): Permutations are essential in combinatorics and probability theory when the order of elements matters. The function calculates the number of permutations of `r` elements taken from a set of `n` elements using the factorial function.

Permutations are significant in systems programming for tasks such as generating test cases and optimizing algorithms that involve ordering or arrangement of elements.

.. note:: This shows the number of permutations but not the actual permutations. That comes later!

.. code-block:: go

   func permutations(n, r int) int {
       return factorial(n) / factorial(n-r)
   }


Combinations
^^^^^^^^^^^^^^^^

Combinations (nCr): Combinations are used when selecting a subset from a larger set without considering the order. The function calculates the number of combinations of `r` elements taken from a set of `n` elements using the factorial function.

Combinations are important in systems programming for tasks such as optimizing resource allocation and implementing efficient data structures.

.. code-block:: go

   func combinations(n, r int) int {
       return factorial(n) / (factorial(r) * factorial(n-r))
   }

Powerset
^^^^^^^^^^

Power Set: The power set is crucial in set theory, combinatorics, and algorithm design. The function generates all possible subsets of a given set using bitwise manipulation.

Power set generation is relevant in systems programming for tasks such as optimizing algorithms that involve exploring all possible subsets of a set.

.. code-block:: go

   func powerSet(set []int) [][]int {
       powerSetSize := int(math.Pow(2, float64(len(set))))
       var result [][]int
       for i := 0; i < powerSetSize; i++ {
           var subset []int
           for j := 0; j < len(set); j++ {
               if (i & (1 << uint(j))) > 0 {
                   subset = append(subset, set[j])
               }
           }
           result = append(result, subset)
       }
       return result
   }


Sum of an Arithmetic Series
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sum of an Arithmetic Series: The sum of an arithmetic series is used in mathematics, finance, and algorithm analysis. The function calculates the sum of an arithmetic series with `n` terms, initial term `a1`, and common difference `d`.

Calculating the sum of an arithmetic series is useful in systems programming for tasks such as optimizing loop iterations and memory management.

.. code-block:: go

   func sumArithmeticSeries(n, a1, d int) int {
       return n/2 * (2*a1 + (n-1)*d)
   }


Sum of a Geometric Series
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sum of a Geometric Series: Geometric series are used in various mathematical and financial calculations. The function calculates the sum of a geometric series with `n` terms, initial term `a1`, and common ratio `r`.

Geometric series calculations are important in systems programming for tasks such as optimizing algorithms that involve exponential growth or decay.

.. code-block:: go

   func sumGeometricSeries(n, a1, r int) int {
       if r == 1 {
           return n * a1
       }
       return a1 * (1 - int(math.Pow(float64(r), float64(n)))) / (1 - r)
   }

Cartesian Product of two sets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Cartesian Product: The Cartesian product is crucial in set theory, combinatorics, and database queries. The function calculates the Cartesian product of two sets by pairing each element of the first set with each element of the second set.

The Cartesian product is valuable in systems programming for tasks such as optimizing database queries and handling multi-dimensional data structures.

.. code-block:: go

   func cartesianProduct(setA, setB []int) [][2]int {
       var result [][2]int
       for _, a := range setA {
           for _, b := range setB {
               result = append(result, [2]int{a, b})
           }
       }
       return result
   }

Modulo operation (a mod b)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Modulo Operation: The modulo operation is widely used in computer science, number theory, and cryptography. The function calculates the remainder of the division of `a` by `b` using the modulo operator.

The modulo operation is significant in systems programming for tasks such as optimizing hashing functions and handling cyclic or periodic operations.

.. note:: This is showing how to compute modulo without the mod operator itself.
.. code-block:: go

   func mod(a, b int) int {
       return a - (a/b) * b
   }

Fast Exponentiation (a^n mod m)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Fast Exponentiation: Fast exponentiation is important for efficient computation of large powers in cryptography. The function calculates `a` raised to the power of `n` modulo `m` using the fast exponentiation algorithm.

Fast exponentiation is relevant in systems programming for tasks such as optimizing cryptographic algorithms and implementing efficient modular arithmetic operations.

.. code-block:: go

   func fastExponentiation(a, n, m int) int {
       res := 1
       a = a % m
       for n > 0 {
           if n%2 == 1 {
               res = (res * a) % m
           }
           n = n >> 1
           a = (a * a) % m
       }
       return res
   }

Data Representation
----------------------

These examples illustrate how different programming languages can represent and display data in various numeric formats, such as decimal, hexadecimal, octal, and binary, allowing you to observe the data representation in action.

.. note:: The intent here is to show what everyone should be learning (at a minimum!).

C Language
^^^^^^^^^^^

This C program demonstrates the data representation of an integer (`int`). It prints the decimal, hexadecimal, octal, and binary representations of the number 42.  Python

.. code-block:: c

   #include <stdio.h>
   
   int main() {
       int num = 42;
       printf("Decimal: %d\n", num);
       printf("Hexadecimal: 0x%x\n", num);
       printf("Octal: %o\n", num);
       printf("Binary: ");
       for (int i = sizeof(num) * 8 - 1; i >= 0; i--) {
           printf("%d", (num >> i) & 1);
       }
       printf("\n");
       return 0;
   }


Python
^^^^^^^^^

This Python program demonstrates the data representation of an integer. It prints the decimal, hexadecimal, octal, and binary representations of the number 42.

.. code-block:: python


   num = 42
   print(f"Decimal: {num}")
   print(f"Hexadecimal: 0x{num:x}")
   print(f"Octal: 0o{num:o}")
   print(f"Binary: {bin(num)[2:]}")
   

Java
^^^^^^^

This Java program demonstrates the data representation of an integer. It prints the decimal, hexadecimal, octal, and binary representations of the number 42.

.. code-block:: java

   public class DataRepresentation {
       public static void main(String[] args) {
           int num = 42;
           System.out.println("Decimal: " + num);
           System.out.println("Hexadecimal: 0x" + Integer.toHexString(num));
           System.out.println("Octal: 0" + Integer.toOctalString(num));
           System.out.println("Binary: " + Integer.toBinaryString(num));
       }
   }


Horner's Rule / Express an Integer in Any Base
-------------------------------------------------

Polynomial Evaluation
^^^^^^^^^^^^^^^^^^^^^^

Horner's Rule, also known as Horner's method or Horner's scheme, is a technique used to efficiently evaluate polynomials. It allows you to compute the value of a polynomial at a given point by factoring out common factors and reducing the number of multiplications.

The general form of a polynomial is :math:`P(x) = a_n x^n + a_{n-1} x^{n-1} + \ldots + a_1 x + a_0`.

where :math:`P(x)` is the polynomial, :math:`x` is the input value, and :math:`a_0`, :math:`a_1`, ..., :math:`a_n` are the coefficients of the polynomial.

Horner's Rule enables us to rewrite the polynomial as a nested form :math:`P(x) = ((\ldots((a_n x + a_{n-1}) x + a_{n-2}) x + \ldots) x + a_0`

This form allows for efficient evaluation by reducing the number of multiplications required. By repeatedly multiplying the result by x and adding the next coefficient, we can evaluate the polynomial with fewer multiplications compared to the traditional approach.

Converting a 32-bit Integer to its Digits in C
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To convert a 32-bit integer to its digits one at a time in C, you can use the following approach:

.. code-block:: c

    #include <stdio.h>

    void printDigits(int num) {
        if (num < 0) {
            num = -num; // Convert negative number to positive
            putchar('-');
        }

        if (num == 0) {
            putchar('0');
            return;
        }

        char digits[10];
        int count = 0;

        while (num > 0) {
            digits[count++] = num % 10 + '0';
            num /= 10;
        }

        for (int i = count - 1; i >= 0; --i) {
            putchar(digits[i]);
        }
    }

    int main() {
        int num = 1234567890;
        printDigits(num);
        return 0;
    }

In this code, the ``printDigits`` function takes an integer ``num`` as input and converts it to its digits one at a time. It handles negative numbers by converting them to positive and printing a minus sign (-) before the digits.

The function uses a character array ``digits`` to store the individual digits as characters. It iteratively extracts the least significant digit by taking the remainder of the number divided by 10 and converts it to the corresponding character by adding '0'. The number is then divided by 10 to remove the least significant digit. This process continues until the number becomes zero.

Finally, the function prints the digits in reverse order (from most significant to least significant) by iterating over the ``digits`` array in reverse.

In the ``main`` function, an example integer ``num`` is provided, and ``printDigits`` is called to convert and print its digits.

Executing this program will output: ``1234567890``, which are the individual digits of the number 1234567890 printed one at a time.



Converting a 32-bit Integer to its Digits in Go
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. note:: Here is another version, in Go, where we write each digit (one at a time) to a string builder (strings.Builder).  C operates at a really low-level and does not provide a standard string buffer (yet). 

.. code-block:: go

   package main
   
   import (
   	"fmt"
   	"strconv"
   	"strings"
   )
   
   func intToString(num int) *strings.Builder {
   	var sb strings.Builder
   
   	isNegative := false
   	if num < 0 {
   		isNegative = true
   		num = -num // Convert negative number to positive
   	}
   
   	if num == 0 {
   		sb.WriteRune('0')
   		return &sb
   	}
   
   	var digits []rune
   	for num > 0 {
   		digit := num % 10
   		digits = append(digits, '0'+rune(digit))
   		num /= 10
   	}
   
   	if isNegative {
   		sb.WriteRune('-')
   	}
   
   	for i := len(digits) - 1; i >= 0; i-- {
   		sb.WriteRune(digits[i])
   	}
   
   	return &sb
   }
   
   func main() {
   	num := 1234567890
   	strBuffer := intToString(num)
   	result := strBuffer.String()
   	fmt.Println(result)
   }
   

.. note:: In Go, a rune is a built-in type that represents a Unicode code point. It is synonymous with an integer value and is used to represent individual characters. Rune literals are expressed using single quotes, such as 'A' or '你', and they can represent characters from various scripts, including ASCII characters and characters from other languages. Runes are commonly used when dealing with Unicode strings and text processing in Go. They provide a way to work with individual characters, iterate over strings, perform character-based operations, and handle multi-byte encoded characters in a consistent and efficient manner. The rune type is an essential component in Go's robust support for Unicode and internationalization.

In this code, the ``intToString`` function takes an integer ``num`` as input and returns a pointer to a ``strings.Builder`` that contains the string representation of the integer.

Inside the function, a ``strings.Builder`` named ``sb`` is created to collect the characters. The function handles negative numbers by setting a flag and converting the number to positive. It handles the special case of ``num`` being zero by directly writing '0' to the string buffer.

The function iteratively extracts the least significant digit by taking the remainder of the number divided by 10 and appends it as a character to a slice of runes named ``digits``. The number is then divided by 10 to remove the least significant digit. This process continues until the number becomes zero.

Afterward, if the number was negative, a negative sign ('-') is written to the string buffer.

Finally, the function iterates over the ``digits`` slice in reverse order and writes each rune to the string buffer. The function returns a pointer to the string buffer.

In the ``main`` function, an example integer ``num`` is provided, and the ``intToString`` function is called to convert it to a string representation using the string buffer. The resulting string is printed using ``fmt.Println``.

Executing this Go program will output: ``1234567890``, which is the string representation of the number ``1234567890`` obtained by converting its digits using the string buffer.

Simplify using Recursion
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: go

   package main
   
   import (
   	"fmt"
   	"strings"
   )
   
   func intToString(num int) *strings.Builder {
   	var sb strings.Builder
   
   	if num < 0 {
   		sb.WriteRune('-')
   		num = -num
   	}
   
   	intToStringRecursive(num, &sb)
   
   	return &sb
   }
   
   func intToStringRecursive(num int, sb *strings.Builder) {
   	if num == 0 {
   		return
   	}
   
   	intToStringRecursive(num/10, sb)
   	sb.WriteRune('0' + rune(num%10))
   }
   
   func main() {
   	num := 1234567890
   	strBuffer := intToString(num)
   	result := strBuffer.String()
   	fmt.Println(result)
   }
   


In this recursive version, the intToString function now calls a recursive helper function named ``intToStringRecursive``. The ``intToStringRecursive`` function takes the integer num and a pointer to the string buffer sb.

Inside the ``intToStringRecursive`` function, the base case is when ``num`` becomes zero. In that case, the function simply returns.

For the recursive case, the function divides num by 10 and recursively calls ``intToStringRecursive`` with the quotient to process the remaining digits. After the recursive call, the remainder of num modulo 10 is added as a rune to the string buffer using sb.WriteRune.

In the ``intToString`` function, if the input num is negative, a negative sign ('-') is added to the string buffer before calling ``intToStringRecursive``.

The main function remains the same, where an example integer ``num`` is provided, and the ``intToString`` function is called to convert it to a string representation using the string buffer. The resulting string is printed using ``fmt.Println``.

Executing this Go program will output: 1234567890, which is the string representation of the number 1234567890 obtained by converting its digits using the recursive approach with a string buffer.
