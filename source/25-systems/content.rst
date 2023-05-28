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
------------

Truth tables show the outcome of all possible inputs of a logic gate. While ARM assembly does not directly support the creation of truth tables, the results of logic gates can be computed and stored in registers.

Logical Equivalence
-------------------

ARM assembly can compare two values and set the condition codes based on the result, which can be used to test logical equivalence. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    MOV R1, #1      ; Load 1 into R1
    CMP R0, R1      ; Compare R0 with R1
    BEQ equivalent  ; If R0 equals R1, branch to 'equivalent'

De Morgan's Laws
----------------

De Morgan's laws state that the negation of a conjunction is the disjunction of the negations, and the negation of a disjunction is the conjunction of the negations. This can be demonstrated using bitwise operations in ARM assembly, but the implementation is nontrivial.

Conditional Statements
----------------------

Conditional execution in ARM assembly is handled by condition codes. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    CMP R0, #1      ; Compare R0 with 1
    BEQ true_branch ; If R0 equals 1, branch to 'true_branch'
    B false_branch  ; Otherwise, branch to 'false_branch'

Biconditional Statements
------------------------

A biconditional statement in ARM assembly can be represented as two conditional branches. For example:

.. code-block:: asm

    MOV R0, #1      ; Load 1 into R0
    MOV R1, #1      ; Load 1 into R1
    CMP R0, R1      ; Compare R0 with R1
    BEQ true_branch ; If R0 equals R1, branch to 'true_branch'
    B false_branch  ; Otherwise, branch to 'false_branch'


Alright, here are the remaining 10 logic concepts, along with brief explanations of how they might be implemented in ARM Assembly. 

Logical Implication
-------------------

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
------------------

The XOR operation can be performed using the EOR instruction.

.. code-block:: asm

    MOV R0, #1
    MOV R1, #0
    EOR R2, R0, R1  ; R2 = R0 XOR R1

NAND and NOR Operations
-----------------------

NAND and NOR are not directly supported, but can be implemented using AND/OR and NOT.

.. code-block:: asm

    AND R2, R0, R1  ; R2 = R0 AND R1
    MVN R2, R2      ; R2 = NOT R2 (NAND)

    ORR R2, R0, R1  ; R2 = R0 OR R1
    MVN R2, R2      ; R2 = NOT R2 (NOR)

Logical Operators with Non-Boolean Values
-----------------------------------------

In assembly, non-zero values are often treated as true and zero as false. So, you might see code that uses non-boolean values with logical operators.

.. code-block:: asm

    CMP R0, #0   ; Compare R0 with 0
    BNE true_branch ; If R0 is not zero, branch to 'true_branch'

Short-Circuit Evaluation
------------------------

There's no direct equivalent of short-circuit evaluation in assembly. However, the behavior can be emulated through the use of conditional branching.

.. code-block:: asm

    CMP R0, #1   ; Compare R0 with 1
    BEQ end      ; If R0 is 1, branch to 'end' (skip the next instruction)
    CMP R1, #1   ; Compare R1 with 1 (only executed if R0 is not 1)
    end:

Truth Tables
------------

As an assembly language, ARM does not directly support data structures like tables. However, you could use an array of values to represent a truth table, and then loop through the array to perform operations.

Logical Equivalence
-------------------

Logical equivalence can be demonstrated by comparing two values.

.. code-block:: asm

    CMP R0, R1  ; Compare R0 and R1
    BEQ equivalent ; If they are equal, branch to 'equivalent'

De Morgan's Laws
----------------

De Morgan's laws are not directly supported in assembly. However, they could be implemented using a combination of AND, OR, and NOT operations, along with appropriate branching.

Conditional Statements
----------------------

Conditional statements can be represented with conditional branches in assembly.

.. code-block:: asm

    CMP R0, #1   ; Compare R0 with 1
    BEQ true_branch ; If R0 is 1, branch to 'true_branch'

Biconditional Statements
------------------------

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


