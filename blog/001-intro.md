# Introduction to Turicum



## Why I Created Turicum

I created Turicum because I needed a language that balances expressive power, runtime flexibility, and concurrency—while staying familiar to experienced developers, especially those working in the Java ecosystem.
Existing JVM languages each address parts of this puzzle, but none offered the particular combination of features I was looking for: a language that is both functional and object-oriented, dynamic yet safe, embeddable yet powerful enough to serve as a standalone DSL or scripting engine.

Turicum emerged from this gap.
I wanted a language that:

* Treats functions, closures, and macros as first-class citizens.
* Allows all definitions—classes, functions, variables—to exist and evolve at runtime.
* Supports preprocessing and metaprogramming as intrinsic parts of the language, not bolted-on extras.
* Handles concurrency with native constructs built atop Java 21's virtual threads.
* Offers flexible scoping, including reclosable closures and intuitive context wrapping.
* Feels approachable to JVM developers but offers new abstractions that simplify complex reactive or asynchronous architectures.

Turicum isn't a reinvention of syntax for its own sake.
Its goal is to empower developers with high-level constructs while preserving clarity, conciseness, and runtime adaptability.
It is both a personal tool and a professional instrument—crafted out of necessity, shaped by real-world needs, and continually evolving through practical use.

## What Is Turicum?

Turicum is a modern programming language designed to blend expressiveness, flexibility, and concurrency into a coherent and practical whole.
It draws inspiration from both functional and object-oriented paradigms while introducing novel features to meet the demands of dynamic applications and developer productivity.

At its core, Turicum is:

* *Functional* – Functions, closures, and macros are first-class citizens.
Every command yields a value, and every expression can be used as a command.
This makes functional composition and expression-oriented design feel natural and powerful.

* *Object-Oriented* – Classes, methods, and multiple inheritance are supported.
Objects can inherit behavior from classes, and both can be modified dynamically.

* *Dynamic* – Definitions (functions, classes, variables) are evaluated at runtime and exist within their defining context.
This dynamic behavior enables runtime code generation, interactive experimentation, and late binding of functionality.

* *Extensible* – The syntax itself can be extended at runtime via macros and user-defined preprocessors.
Code can transform code, making domain-specific languages and custom syntactic constructs first-class capabilities.

* *Concurrent* – Built on Java 21's virtual threads, Turicum supports lightweight, scalable concurrency with built-in `async`, `await`, `yield`, and `flow` constructs.
Reactive, parallel, and streaming computations are native features of the language.

* *Embeddable* – Turicum can run as a command-line tool or be embedded into JVM-based applications.
This makes it ideal as a general-purpose scripting language or a tightly integrated DSL within Java or Kotlin projects.
The JAR size for the version 1.0.0 is less than half MB.

* *Approachable for JVM Developers* – While introducing powerful new abstractions, Turicum avoids alien syntax.
Its design will feel familiar to those who know Java, Python, or JavaScript, while remaining lean and free of superfluous boilerplate.

The name _Turicum_ comes from the ancient Roman name for Zürich, Switzerland—where the language is being developed.


## Who Is Turicum For?

Turicum is designed for experienced developers who want more control, flexibility, and conciseness in their tools—without giving up safety or integration with established ecosystems.
Its ideal users include:

* *JVM Developers* who want a powerful embedded scripting language or DSL that integrates tightly with Java and Kotlin.

* *Tooling and DSL Authors* who need dynamic syntax, macros, and context-aware evaluation to implement rich, language-like interfaces without building a compiler from scratch.

* *Architects and Library Designers* who are creating complex systems where declarative configuration, reactive behavior, or staged computation models are needed—and where traditional languages become verbose or rigid.

* *Power Users and Explorers* who enjoy languages that expose their internals, allow runtime reflection and transformation, and encourage deep customization.

* *Concurrency-Focused Engineers* who are building systems that require safe, high-level coordination of tasks, dataflow, and reactivity.
Turicum's `flow` blocks and native use of virtual threads remove much of the boilerplate and complexity typically associated with concurrent computation.

Turicum is *not* aimed at beginners or casual scripting.
It makes deliberate trade-offs to support power and flexibility, and while its syntax is compact and learnable, its concepts—like reclosable closures, macro-based metaprogramming, and dynamic scope wrapping—require a solid grounding in programming fundamentals.

In short, Turicum is for developers who want their language to feel like a precision tool: minimal where it can be, expressive where it matters, and extensible where nothing else will do.

## What Makes Turicum Different?

Turicum doesn’t aim to reinvent programming.
Instead, it builds on what works—while introducing unique, deeply integrated features that set it apart from other languages in the JVM ecosystem and beyond.

Here’s what makes Turicum stand out:

### 🧠 *Everything Is a Value, Even Commands*

In Turicum, every command returns a value, and every expression can act as a command.
This uniform model allows natural composition and avoids the sharp edges between "statements" and "expressions" that plague many languages.

### 🌀 *Closures That Can Be Reclosed*

Closures in Turicum carry their defining context—but uniquely, they can be _reclosed_, meaning rebound to the current context using `reclose()`.
This enables safe and explicit context switching for deferred computation or stateful logic reuse, a capability rare in most languages.

### 🧱 *Macros With Explicit Evaluation*

Turicum macros receive their arguments unevaluated.
This means they can choose _when_ and _if_ to evaluate each argument using the `evaluate()` function.
This allows safe, controlled metaprogramming and avoids the pitfalls of implicit expansion or over-evaluation common in Lisp-style macros.

### 🔄 *Context-Wrapped Blocks and Scoped Execution*

Block execution happens in isolated runtime scopes that wrap their surrounding context.
You can control scope visibility and variable lifetimes with precision.
Combined with `with` blocks, this allows expressive resource handling and declarative configuration patterns—without needing complex object graphs.

### ⚙️ *Flexible and Typed Parameters*

Turicum supports positional-only, named-only, rest (`[x]`), meta (`{x}`), and trailing closure (`^x`) parameters—all within the same function signature.
This enables highly readable and flexible APIs, especially for DSLs and configuration-heavy code.

### ⚡ *Concurrency With Built-In Reactive Flow*

Turicum's `flow` command defines reactive, data-driven computations where dependent cells update automatically and concurrently.
Built atop Java virtual threads, `flow` offers high-level concurrent reactivity without frameworks or annotations.
It’s like Excel formulas for code—but safe, deterministic, and fully programmable.

### 🧬 *Runtime Mutability and Preprocessing*

Classes, functions, and even syntax can be defined and transformed at runtime.
Built-in preprocessing, scoped macro expansion, and runtime imports mean you can evolve a running program’s behavior—safely and explicitly—without magic or hidden globals.


### ⚖️ *Balance of Familiar and Inventive*

Turicum is deliberately designed so that experienced developers can read most code without ever having studied the language.
Its syntax draws from familiar conventions—like curly braces for blocks, `if` and `for` constructs, and standard operator precedence—so it feels natural on first contact.
At the same time, it introduces deeper innovations—such as reclosable closures, macros with explicit evaluation, and reactive `flow` constructs—only where they provide clear, expressive power.
The result is a language that's immediately approachable yet uniquely capable.

In sum, Turicum is not a toy language or a syntax experiment.
It is a precision tool for people who need runtime flexibility, high-level concurrency, and expressive metaprogramming—all while remaining grounded in a clear, readable, and deterministic core.

## How Turicum Works _(show example code and behavior)_

## How Turicum Works

Turicum programs are built from commands, and *every command is also a value*.
This foundational principle shapes the entire language: assignments, loops, conditionals, blocks, even `if` and `for` constructs—all produce values that can be used directly in expressions.
The language is both imperative and expression-oriented, enabling concise yet powerful constructs.

Here’s a quick look at how Turicum code feels and behaves:

### ✨ Everything Returns a Value


```turi
mut result = {
  mut x = 3;
  mut y = x * 2;
  y + 1
}
println(result)  // prints 7
```

The block returns the result of the last command—in this case, `y + 1`.

🧪 If Commands Return Values

```turi
mut status = if a > 0: "positive" else: "non-positive";
```

There is no ternary operator—just plain, readable if expressions that act as values.

🔁 Loops Are Expressions Too


```turi
mut l = {
  mut i = 0;
  for ; i < 5 ; i = i + 1 list { i * i }
}
println(l)  // [0, 1, 4, 9, 16]

```

Adding `list`: before the loop body collects the results of each iteration.

🔄 Dynamic Objects

Objects are dictionary-like and can be constructed inline:


```turi
mut person = {
  name: "Alice",
  age: 30
}
println(person.name)  // Alice

```

Fields can be added or modified dynamically unless the object is explicitly pinned.

🧵 Native Concurrency With async and yield


```turi
mut task = async {
  for i = 1 ; i <= 3 ; i = i + 1 : yield i;
  "done"
}

while task.has_next(): println(task.next());
println(await task);  // done

```

Turicum uses Java 21 virtual threads to support lightweight asynchronous tasks without a complex boilerplate.

⚡ Reactive Computation With flow


```turi
mut root = (flow until abs(a * a - 13) < 0.0001 {
  a <- 13
  a <- (a + 13 / a) / 2
  yield a
})
println(root)  // ≈ 3.605...
```

This defines a reactive computation where `a` updates until a stable approximation of √13 is reached.

🧰 First-Class Macros

Turicum macros receive unevaluated arguments and control when and how to evaluate them:


```turi
mut my_if = macro(
  {|cond, then, `else`|
    if evaluate(cond): evaluate(then) else: evaluate(`else`)
  }
)
my_if(true, (println "yes"), (println "no"))  // prints: yes

```

This makes advanced metaprogramming safe and readable—no compiler plugins or templating needed.

🔍 Preprocessing Is Built In

You can define compile-time transformations using ordinary Turicum code.
This enables DSL extensions, custom directives, and context-aware token manipulation—all with zero external tooling.

## Using Turicum as a Maven Extension

One of the practical and immediate uses of Turicum is as a drop-in replacement syntax for Maven project definitions.
Turicum 1.0.0 includes an officially supported *Maven extension* that reads `pom.turi` files written in Turicum and transparently converts them into standard `pom.xml` files.

When configured via `extensions.xml` in the `.mvn` directory of your project, the Turicum Maven extension automatically:

* Locates `pom.turi` files in the root and in each module directory.
* Executes them using the Turicum interpreter.
* Generates standard-compliant `pom.xml` files from the results.
* Redirects Maven to load and process those `pom.xml` files as if they were present all along.

### 🧩 Why This Approach Is Better Than Polyglot Maven

Unlike older approaches such as https://github.com/takari/polyglot-maven[Polyglot Maven], which bypass the XML serialization and load internal Maven model objects directly from alternate formats (like Groovy or YAML), Turicum's approach *preserves compatibility* with the entire Maven ecosystem:

* The resulting `pom.xml` files are real XML files on disk.
* Tools that don't understand Maven extensions—like IDEs, CI/CD scanners, or Maven wrappers—can still function normally after a `mvn verify` or similar command.
* You can inspect or edit the generated `pom.xml` at any time.

In essence, you're using Turicum to author Maven projects in a cleaner, programmable, yet fully transparent way—with no lock-in.

### 🚪 No Vendor Lock-In

Turicum leaves no hidden state.
If at any time you want to switch back to plain XML, simply:

* Run `mvn verify` (or any Maven lifecycle goal).
* Delete the `.mvn` directory (containing `extensions.xml`).
* Keep the generated `pom.xml` files.

Your project continues to build exactly as before.
You can even commit only the `pom.xml` files and exclude `pom.turi` from source control if desired.

### ✨ Why Use Turicum for Maven POMs?

Turicum offers major advantages when used as a syntax for describing Maven projects:

* *Clarity and structure*: The syntax is concise, expressive, and free from XML boilerplate.
* *Powerful templating*: Common structures can be shared, parameterized, and reused—without relying on Maven's limited inheritance and parent POM mechanisms.
* *Programmability*: You can compute dependency lists, plugin versions, or module structures at runtime based on external metadata or conventions.

However, *this programmability must be used with discipline*.

____
❗ Turicum should never be used to defeat the declarative nature of Maven.
Its programmability is intended solely to _compute_ the inputs of the build—such as artifact coordinates, plugin declarations, or module lists—not to _redefine_ Maven behavior or replace plugins.
____

Treat Turicum as a better authoring tool for declarative builds—not a mechanism to embed logic where it doesn't belong.

### 🧪 Real Example: Convention Over Repetition

The Turicum compiler itself is built using this Maven extension.
As they say, the cook eats their own food.

In the `pom.turi` of the root project, module definitions are centralized with a simple declaration:

```
let modules = [ "core", "maven", "cli" ];
```

Later, these same module names are reused to generate the `dependencyManagement` section:

```
    dependencyManagement : {
        dependencies : [
          ..{
              for each m in modules list{
                  {
                      groupId : "ch.turic",
                      artifactId : m,
                      version : VERSION
                  }
              }
            },
```

The `for each` loop dynamically constructs a list of dependency objects—one for each module.
Since `for each` returns a list, and the outer code uses `..` to flatten the result, the final structure is exactly what Maven expects: a flat list of `<dependency>` entries in the generated `pom.xml`.
The full code is available in the GitHub [Turicum](https://github.com/verhas/turicum) repo.

This eliminates the need to copy, paste, and manually modify repeated declarations.
It captures a convention once, in one place, and reuses it throughout the build.
And because the final `pom.xml` is fully materialized, the output remains 100% compatible with any Maven tool.

This kind of structure is where Turicum shines: *programming the shape of the build configuration*, not the behavior of the build itself.

## Design Philosophy

Turicum is not an academic experiment or a feature checklist—it is a tool shaped by experience.
Its design grows out of real-world software development, especially on the JVM, where power and clarity must coexist, and where developers need flexibility without losing control.

At the core of Turicum’s philosophy are a few consistent values:

### ✅ *Everything Is Executable, But Nothing Is Magical*

Turicum treats most language constructs as expressions with values.
A `class`, a `fn`, an `if`, even a block or a `for` loop—each evaluates to something and can be nested, assigned, or passed around.
Some syntactic forms, like `if` or `while`, are built-in commands.
Others, like `import`, are just functions—yet they’re still expressions, and therefore usable as commands.

This uniform model allows rich composition and evaluation, but nothing happens behind your back.
There's no compiler magic, no hidden rewrites—just transparent, inspectable behavior.

### 🔍 *Explicit Is Better Than Implicit*

Turicum’s macro system, for example, requires explicit evaluation of arguments using `evaluate(x)`.
This avoids the unpredictable behavior of macros that guess what should be expanded when.
Similarly, closures capture their environment only once—unless you _reclose_ them explicitly.
Clarity always wins over cleverness.

### 🧱 *Composability Over Complexity*

Turicum avoids special-purpose features when general-purpose constructs suffice.
There is no ternary operator, because `if` is already an expression.
There are no decorators as a separate concept, because ordinary functions with closures do the job.
Instead of introducing keywords, Turicum encourages building higher-level behaviors through composition.

### 🔒 *Safe by Default, Flexible by Choice*

Mutable state is allowed, but only when explicitly declared with `mut`.
Parameters are pinned by default.
Contexts are isolated unless you intentionally wrap them.
This balance makes it possible to write robust code without sacrificing expressiveness.
Concurrency, for instance, uses Java virtual threads but protects shared state with clear context boundaries and update rules.

### 🔁 *Dynamic Without Becoming Unpredictable*

Turicum embraces runtime definition of functions, classes, and macros.
It supports reflection and even preprocessing.
But it keeps the model deterministic: every block, closure, and macro operates in a well-defined scope with known inputs.
You can generate behavior dynamically, but that behavior remains testable, debuggable, and traceable.

### 📦 *Integrated, Not Fragmented*

Where other languages bolt on features like reactive streams, macros, or preprocessors, Turicum integrates them as first-class capabilities.
You don’t need plugins, frameworks, or DSLs to extend syntax, build asynchronous pipelines, or manipulate code at runtime.
The language itself is the framework.

### 💡 *Use Power Responsibly*

Perhaps most importantly, Turicum trusts you to use its power with discipline.
It gives you runtime metaprogramming, lexical token manipulation, and context-aware evaluation—but it also expects you not to misuse them.

Turicum's design gives you sharp tools.
It also gives you clean defaults, clear semantics, and just enough structure to avoid chaos.



## Getting Started

Turicum is easy to adopt, whether you want to try it interactively, use it to author Maven projects, or embed it as a scripting engine in your JVM applications.

### 🖥️ Install the CLI Tool

Prebuilt binaries are available for:

* *Windows*
* *Linux*
* *macOS*

Download the appropriate installation kit from the [official release page](https://github.com/turicum-pl/turicum-pl.github.io/tree/main/download) and place the executable on your `PATH`.
Once installed, you can run Turicum scripts from the command line:

```sh
turi hello.turi
```

The CLI is lightweight, fast, and self-contained.
No JVM setup is required.

### 🛠️ Use Turicum as a Maven Extension

To use Turicum for writing your `pom.turi` files, all you need is a single configuration file in your project.
Create a `.mvn/extensions.xml` file with the following content:

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<extensions>
    <extension>
        <groupId>ch.turic</groupId>
        <artifactId>turicum-maven-extension</artifactId>
        <version>1.0.0</version>
    </extension>
</extensions>
```

Then write your build descriptor in Turicum syntax as `pom.turi`.
The extension will automatically generate `pom.xml` files and redirect Maven to them.
This works seamlessly with standard Maven workflows and also enables tool compatibility (e.g., IDE import) since the XML is materialized.

You can always revert to plain XML by running `mvn verify` and removing the `.mvn` directory—*no lock-in*.

### ⚙️ Embed Turicum in Your Java or Kotlin Application

Turicum can also be embedded as a scripting engine or DSL interpreter.
Just add the core runtime as a single Maven dependency:

```
<dependency>
  <groupId>ch.turic</groupId>
  <artifactId>turicum-core</artifactId>
  <version>1.0.0</version>
</dependency>
```

This dependency brings in *no transitive dependencies* and runs on any Java 21+ JVM.
It is ideal for applications needing lightweight scripting, dynamic configuration, or macro-based extensibility.

## 📚 Documentation

Turicum comes with thorough and precise documentation, including:

* A complete *reference manual* that describes the language in detail.
* A formal *annotated EBNF grammar* defining the full syntax of the language.
* Explanations of all core features—functions, objects, macros, concurrency, and more.
* Dozens of code examples with exact output for every major feature.

A distinctive goal of the documentation is *LLM-readability*.
The language reference was deliberately structured so that it could be embedded into the prompt of large language models (LLMs).
This allows AI tools to understand and generate Turicum code with remarkable accuracy—even without prior fine-tuning on the language.

In fact, much of the code in this article was written using exactly that approach: the reference grammar and a few style hints were enough for the AI to produce runnable, idiomatic Turicum code that needed only minor edits.

If you want to teach an AI to write your DSL or tooling, or just want precise, unambiguous documentation for your team, Turicum’s reference model is designed to serve both purposes equally well.


## 📜 Open and Permissive Licensing

Turicum is released under the *Apache 2.0 License*—permissive, business-friendly, and free of usage restrictions.
You can use it in commercial, open-source, educational, or experimental projects without worry.


## Takeaway

Turicum is a language designed for developers who value clarity, control, and composability.
It solves real problems with practical tools—clean syntax, dynamic evaluation, macro-based extensibility, and lightweight concurrency.
It integrates into your workflow without locking you in, whether you're scripting logic, describing builds, or embedding dynamic behavior in your own applications.

If you take away only one thing from this article, let it be this:

____
*Turicum gives you the power to automate structure, not blur it—to write expressive, correct programs and configurations that stay readable, maintainable, and testable.*
____

It's not a toy language or a flashy syntax demo.
It’s a precision tool—one you can put to work immediately, from scripting to Maven project definitions to embedded execution.

*Don’t do yourself a disservice by ignoring what’s possible.* If you’ve ever felt your current tools make you repeat yourself, fight the language, or compromise clarity for power, then Turicum is worth your attention.

You can start small.
Write a `+pom.turi+`.
Embed a script.
Run it from the command line.
The power is there when you need it—and the simplicity when you don’t.