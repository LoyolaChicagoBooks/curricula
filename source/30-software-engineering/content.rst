Software Engineering (LUC COMP 330)
====================================

.. note:: GPT-4 + Insights

Design by Contract (DBC)
------------------------

.. note:: An important idea introduced by Eiffel (Bertrand Meyer).

What language was the first to support DBC?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The first programming language to support Design by Contract (DbC) natively was Eiffel. Eiffel was created by Bertrand Meyer in the mid-1980s and was designed from the ground up to support DbC as a fundamental part of the language.

The DbC concept introduced by Meyer in Eiffel is based on the idea that software components should be designed with clear and unambiguous contracts that define their behavior and requirements. DbC provides a way to specify these contracts directly in the code, making it easier to verify that a component satisfies its requirements and behaves correctly.

Eiffel's support for DbC includes built-in language constructs for specifying preconditions, postconditions, and invariants, as well as tools for automatically generating test cases and verifying that the contracts are satisfied.

Since Eiffel's introduction of DbC, many other programming languages have borrowed the concept and implemented similar features. However, Eiffel remains one of the most well-known languages with built-in support for DbC.


Eiffel Language
^^^^^^^^^^^^^^^^

Eiffel is an object-oriented programming language named after Gustave Eiffel, the designer of the Eiffel Tower.

The Eiffel programming language was developed in the 1980s by Bertrand Meyer, a computer scientist and software engineer from Switzerland. It was designed to be a high-level, efficient, and reliable language that emphasizes the principles of software engineering, such as modularity, extensibility, and reusability.

One of the key features of Eiffel is Design by Contract, a technique for ensuring that software components interact correctly by defining preconditions, postconditions, and invariants for each component. Eiffel also includes features such as multiple inheritance, garbage collection, and automatic memory management.

Eiffel has been used in a variety of applications, including finance, telecommunications, aerospace, and education. It remains a popular choice for developers who value its strong typing and its ability to produce efficient and reliable code.

Rational Numbers - Eiffel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: eiffel

   class RATIONAL
   
   feature
   
       numerator, denominator: INTEGER
       
       make (a_numerator, a_denominator: INTEGER)
           -- Initialize a new rational number with numerator `a_numerator` and denominator `a_denominator`.
           require
               a_denominator /= 0
           do
               numerator := a_numerator
               denominator := a_denominator
           end
       
       add (other: RATIONAL): RATIONAL
           -- Add this rational number to `other` and return the result.
           local
               common_denominator: INTEGER
               result: RATIONAL
           do
               common_denominator := denominator.lcm (other.denominator)
               create result.make (numerator * (common_denominator // denominator) + other.numerator * (common_denominator // other.denominator), common_denominator)
               Result := result
           end
       
       subtract (other: RATIONAL): RATIONAL
           -- Subtract `other` from this rational number and return the result.
           local
               common_denominator: INTEGER
               result: RATIONAL
           do
               common_denominator := denominator.lcm (other.denominator)
               create result.make (numerator * (common_denominator // denominator) - other.numerator * (common_denominator // other.denominator), common_denominator)
               Result := result
           end
       
       multiply (other: RATIONAL): RATIONAL
           -- Multiply this rational number by `other` and return the result.
           local
               result: RATIONAL
           do
               create result.make (numerator * other.numerator, denominator * other.denominator)
               Result := result
           end
       
       divide (other: RATIONAL): RATIONAL
           -- Divide this rational number by `other` and return the result.
           require
               other.numerator /= 0
           local
               result: RATIONAL
           do
               create result.make (numerator * other.denominator, denominator * other.numerator)
               Result := result
           end
       
       is_equal (other: RATIONAL): BOOLEAN
           -- Check if this rational number is equal to `other`.
           do
               Result := numerator * other.denominator = other.numerator * denominator
           end
       
   end


Eiffel Implementations
^^^^^^^^^^^^^^^^^^^^^^^^

Are there any open source Eiffel implementations?

There are open source Eiffel implementations available. Here are a few examples:

EiffelStudio: This is the most widely used Eiffel implementation and is available under the GPL license. EiffelStudio is a comprehensive development environment that includes an IDE, a compiler, and a number of libraries and tools.

SmartEiffel: This is another open source Eiffel implementation that is available under the GPL license. SmartEiffel is designed to be highly portable and can run on a variety of platforms, including Unix, Linux, and Windows.

ISE Eiffel: This is a commercial Eiffel implementation that is available under a proprietary license. However, ISE Eiffel also offers a free version called EiffelStudio Community Edition, which includes many of the same features as the commercial version.

Liberty Eiffel: This is an open source Eiffel implementation that is available under the LGPL license. Liberty Eiffel is designed to be highly portable and can run on a variety of platforms, including Unix, Linux, and Windows.

These implementations offer a variety of features and tools for developing Eiffel applications, and you can choose the one that best suits your needs.

What modern languages [besides Eiffel] support DBC?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Do any modern programming languages support Eiffel's DBC?

While Eiffel remains one of the most well-known languages with built-in support for Design by Contract (DbC), there are several modern programming languages that have borrowed the idea and implemented similar features.

Here are a few examples of modern programming languages that support DbC:

Rust: Rust is a systems programming language that emphasizes safety, concurrency, and performance. Rust includes a built-in macro system that allows developers to define custom preconditions, postconditions, and invariants.

TypeScript: TypeScript is a superset of JavaScript that adds static typing and other features to the language. TypeScript includes support for interface contracts, which allow developers to define preconditions and postconditions for functions and methods.

Kotlin: Kotlin is a modern programming language that is fully interoperable with Java. Kotlin includes support for annotations that can be used to define contracts for functions and methods.

Python: Python is a high-level, dynamically typed programming language. Python includes support for decorators that can be used to define contracts for functions and methods.

Ada: Ada is a high-level programming language that was developed for use in safety-critical systems such as aviation, defense, and healthcare. Ada also supports DbC natively, with built-in support for preconditions, postconditions, and invariants.

These languages offer varying levels of support for DbC and may implement the concept in slightly different ways. However, they all share the goal of improving the reliability and correctness of software through the use of contracts.

Python - DBC
^^^^^^^^^^^^^

Here is an example of how Python supports DBC? It must have at least one postcondition, precondition, and invariant.

.. code-block:: python

   import icontract
   
   @icontract.require(lambda x: x > 0)
   @icontract.ensure(lambda result: result > 0)
   def square(x):
       """Returns the square of a positive number"""
       return x ** 2
   
   @icontract.invariant(lambda self: self.balance >= 0)
   class BankAccount:
   
       def __init__(self, balance):
           self.balance = balance
   
       @icontract.require(lambda amount: amount > 0)
       def deposit(self, amount):
           self.balance += amount
   
       @icontract.require(lambda amount: amount > 0)
       def withdraw(self, amount):
           self.balance -= amount
   
Rust - DBC
^^^^^^^^^^^

.. code-block:: rust

   #![feature(proc_macro_hygiene)]
   
   use contract::contract_trait;
   
   #[contract_trait]
   pub trait Square {
       #[requires(x > 0)]
       #[ensures(result > 0)]
       fn square(x: i32) -> i32;
   }
   
   pub struct BankAccount {
       balance: f64,
   }
   
   impl BankAccount {
       pub fn new(balance: f64) -> Self {
           assert!(balance >= 0.0, "Negative balance");
           Self { balance }
       }
   
       #[invariant(self.balance >= 0.0)]
       #[requires(amount > 0.0)]
       pub fn deposit(&mut self, amount: f64) {
           self.balance += amount;
       }
   
       #[invariant(self.balance >= 0.0)]
       #[requires(amount > 0.0)]
       pub fn withdraw(&mut self, amount: f64) {
           self.balance -= amount;
       }
   }

In this example, we're using the contract crate to define preconditions, postconditions, and invariants for a trait and a struct.

The Square trait has a precondition that specifies that the input x must be greater than zero and a postcondition that specifies that the return value must also be greater than zero.

The BankAccount struct has an invariant that specifies that the balance property must be non-negative. The deposit and withdraw methods have preconditions that specify that the amount argument must be greater than zero.

If any of these contracts are violated at runtime, the contract crate will panic with a message indicating which contract was violated and where.

Note that the contract crate requires the use of the nightly version of Rust and the #![feature(proc_macro_hygiene)] feature flag. Also, note that the contract crate is not part of the Rust standard library and needs to be installed separately using a package manager like Cargo.

Scala's DBC
^^^^^^^^^^^^

Scala has support for Design by Contract (DbC) through the use of annotations and the Scala Compiler Plugin for Contracts.

The Scala Compiler Plugin for Contracts is a third-party library that extends the Scala compiler to include support for DbC. The plugin allows developers to use annotations to define preconditions, postconditions, and invariants for functions and methods, and provides compile-time checking to verify that these contracts are satisfied.

Here's an example of how you can use the Scala Compiler Plugin for Contracts to define preconditions, postconditions, and invariants:

.. code-block:: scala

   import org.scalacontracts._
   import org.scalacontracts.Contract._
   
   class BankAccount(var balance: Double) {
   
     @Invariant
     def checkBalance(): Unit = {
       require(balance >= 0.0)
     }
   
     @Requires("amount > 0.0")
     def deposit(amount: Double): Unit = {
       balance += amount
     }
   
     @Requires("amount > 0.0")
     def withdraw(amount: Double): Unit = {
       balance -= amount
     }
   }

