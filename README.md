# Turicum Programming Language Reference

[`GITHUB REPO`](https://github.com/verhas/turicum)
[ARTICLES](blog)


Turicum is a modern programming language designed for expressiveness, safety, and concurrency.
It combines functional and object-oriented paradigms with a clean and coherent syntax.
Its preprocessing capabilities and dynamic nature make it a uniquely powerful tool for  programming.

* **Functional**
+
Functions, closures, and macros are first-class citizens in Turicum.
Any of these can be used as values.
Every command evaluates to a value, so any command can appear within an expression, and every expression is also a command.

* **Object-Oriented**
+
Programs can define classes, methods, and multiple inheritance,
and objects that inherit properties from their class.

* **Dynamic**
+
All definitions are created at runtime and can be modified at runtime.
For example, a class or function is created when its definition is executed, and it exists within the defining context.
Methods are just fields containing closures or function values, and they can be added to any class or object—even after creation.

* **Flexible**
+
The interpreter can evaluate loaded code at any time, passing the remaining lexical tokens to a preprocessor.
This preprocessor—written in Turicum as a function or closure—can transform the token stream, enabling arbitrary syntactic extensions to the language.

* **Multithreaded**
+
The interpreter is built on Java 21 and supports for Virtual Threads, using native language constructs.

* **Typed and Scoped**
+
Variables can be optionally typed, and assignments are dynamically type-checked at runtime.

Turicum functions both as a scripting language and as an embeddable engine.
It can run as a standalone command-line tool or be integrated into Java or Kotlin applications as a library.

Turicum is implemented in Java and is designed to be approachable for JVM developers while introducing powerful new abstractions.

The name “Turicum” is the ancient Roman name for the city of Zürich, Switzerland, where the language is being developed.

## Design Goals and Philosophy

Turicum was designed with the following principles:

* A **concise syntax** that remains readable and expressive.
* A **functional-first** execution model with support for **side effects** when necessary.
* **Multithreading and pipeline constructs** built directly into the language.
* **Safe scoping and closures**, including *reclosable* closures, which can adapt to new context bindings.
Closure reclosing is a unique feature of the language.
* **Macro-based metaprogramming**, allowing deferred and explicit evaluation of arguments.
* A flexible function/method call **parameter system**

The language is intended for **experienced developers**, especially those working with the JVM, who require a powerful scripting or DSL tool that feels natural but scales to complex architectural needs.