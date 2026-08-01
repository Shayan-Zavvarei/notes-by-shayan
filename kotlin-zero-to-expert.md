# Kotlin: Zero to Expert

*A complete, self-study path from your first `println` to production Kotlin — backend, Android, and multiplatform.*

## Who this booklet is for

You need no prior Kotlin. If you have written *any* code before — even a little Python, JavaScript, or Java — you have enough to start at Chapter 1. If you already know Java, you will move faster and find dedicated **☕ Coming from Java** notes throughout.

The goal is not just to make you *productive* in Kotlin, but to make you *understand* it: not only how to write `?.`, but what `?.` compiles to; not only how to launch a coroutine, but why a suspending function is a state machine. That "under the hood" understanding is what separates an advanced user from an expert, and it is woven into every chapter.

## How each chapter is structured

Every chapter follows the same rhythm, so you always know where you are:

- **Learning objectives** up front — what you'll be able to do by the end.
- For each new idea: **the problem it solves** → **a mental model** → **the syntax, explained line by line** → **a worked example with its output** → callouts for internals, traps, and idioms.
- **Interleaved micro-exercises** — small challenges *inside* the text. Try them before reading on.
- A **Summary**, a **Self-check quiz**, graduated **Exercises**, and a **Chapter Project**.
- A **Glossary** of new terms and a **What's next** pointer.

**Read actively.** Type the examples out. Predict outputs before you check them. Open the collapsible solutions only after you have attempted the exercise yourself — the struggle is where the learning happens.

## The callout legend

Throughout the booklet you'll see these labelled notes:

| Callout | Meaning |
|---------|---------|
| ⚙️ **Under the hood** | What the feature compiles to / how it behaves at runtime (the expert layer). |
| ⚠️ **Gotcha** | A common mistake or surprising behaviour to watch for. |
| ☕ **Coming from Java** | How this differs from Java, for readers with a Java background. |
| 💡 **Idiom** | The idiomatic, "Kotlin-native" way to do something. |
| 📝 **Exercise** | A challenge to attempt before moving on. |
| 🛠️ **Chapter Project** | The cumulative end-of-chapter project (see below). |

## The running project: a Task Manager

Rather than a scatter of unrelated snippets, most chapters grow **one application**: a small **Task Manager**. It starts in Chapter 1 as a few `println`s, becomes real data and functions, gains a proper domain model with classes, learns to run work asynchronously, then grows a REST API, a database, an Android UI, tests, and finally a shared multiplatform core.

Each **🛠️ Chapter Project** tells you whether it *advances the running Task Manager* or is a *standalone mini-project* (used only where a chapter's topic doesn't fit the app, like Java interop). A project never needs a concept from a later chapter — so you can always complete it with what you've learned so far. The fully assembled final version lives in **Appendix D**.

## Learning roadmap

The 36 chapters form five parts. You can read straight through, or use this as a map. Parts 1–4 take you from zero to a genuinely advanced, ship-capable developer; **Part 5 is where advanced becomes expert.**

**Part 1 — Fundamentals (Ch. 1–7).** The core language: values, types, control flow, functions, collections, and null safety.
*After this part you can write correct, null-safe Kotlin programs and command-line logic.*

**Part 2 — Object-Oriented Kotlin (Ch. 8–12).** Classes, inheritance and interfaces, sealed/enum/object, extensions, and generics.
*After this part you can design clean, reusable, type-safe domain models.*

**Part 3 — Functional & Concurrent Kotlin (Ch. 13–17).** Delegated properties, scope functions, coroutines and Flow, exception handling, and DSLs.
*After this part you can write asynchronous, expressive, idiomatic Kotlin.*

**Part 4 — Kotlin in the Real World (Ch. 18–25).** Java interop, Gradle, Ktor backends, databases, Android, best practices, testing, and advanced/next-step topics.
*After this part you can ship real backend, Android, and multiplatform applications.*

**Part 5 — Mastery (Ch. 26–36).** The expert layer: Flow in depth, advanced concurrency, operator conventions, reflection, metaprogramming (KSP & compiler plugins), serialization internals, performance & memory, architecture & dependency injection, Kotlin Multiplatform in depth, designing public libraries, and advanced testing.
*After this part you can design frameworks, optimise hot paths, architect large systems, and reason about Kotlin the way its own library authors do.*

> **Version baseline (July 2026).** Language and build examples target **Kotlin 2.4.0** and the K2 compiler. The production chapters use Ktor 3.x and current stable releases named in their setup sections. Experimental or preview APIs are labelled at the point of use; unlabelled language features are stable in Kotlin 2.4. Dependency versions are examples, not timeless constants: before starting a new project, check the official compatibility tables and update patch versions together.

## Table of Contents

**Part 1 — Fundamentals**

- [Chapter 1 — Getting Started](#chapter-1--getting-started)
- [Chapter 2 — Variables & Data Types](#chapter-2--variables--data-types)
- [Chapter 3 — Operators & Expressions](#chapter-3--operators--expressions)
- [Chapter 4 — Control Flow](#chapter-4--control-flow)
- [Chapter 5 — Functions](#chapter-5--functions)
- [Chapter 6 — Collections](#chapter-6--collections)
- [Chapter 7 — Null Safety](#chapter-7--null-safety)

**Part 2 — Object-Oriented Kotlin**

- [Chapter 8 — Classes & Objects](#chapter-8--classes--objects)
- [Chapter 9 — Inheritance & Interfaces](#chapter-9--inheritance--interfaces)
- [Chapter 10 — Advanced Object-Oriented Features](#chapter-10--advanced-object-oriented-features)
- [Chapter 11 — Extension Functions & Properties](#chapter-11--extension-functions--properties)
- [Chapter 12 — Generics](#chapter-12--generics)

**Part 3 — Functional & Concurrent Kotlin**

- [Chapter 13 — Delegated Properties](#chapter-13--delegated-properties)
- [Chapter 14 — Scope Functions](#chapter-14--scope-functions)
- [Chapter 15 — Coroutines & Flow](#chapter-15--coroutines--flow)
- [Chapter 16 — Exception Handling](#chapter-16--exception-handling)
- [Chapter 17 — Type-Safe Builders & DSLs](#chapter-17--type-safe-builders--dsls)

**Part 4 — Kotlin in the Real World**

- [Chapter 18 — Kotlin ↔ Java Interoperability](#chapter-18--kotlin--java-interoperability)
- [Chapter 19 — Gradle with Kotlin DSL](#chapter-19--gradle-with-kotlin-dsl)
- [Chapter 20 — Ktor for Backend Development](#chapter-20--ktor-for-backend-development)
- [Chapter 21 — Database Access](#chapter-21--database-access)
- [Chapter 22 — Android Development with Kotlin](#chapter-22--android-development-with-kotlin)
- [Chapter 23 — Best Practices & Idioms](#chapter-23--best-practices--idioms)
- [Chapter 24 — Testing in Kotlin](#chapter-24--testing-in-kotlin)
- [Chapter 25 — Advanced Topics & Next Steps](#chapter-25--advanced-topics--next-steps)

**Part 5 — Mastery**

- [Chapter 26 — Flow in Depth](#chapter-26--flow-in-depth)
- [Chapter 27 — Advanced Coroutines & Concurrency](#chapter-27--advanced-coroutines--concurrency)
- [Chapter 28 — Operator Overloading & Conventions](#chapter-28--operator-overloading--conventions)
- [Chapter 29 — Reflection & Annotations](#chapter-29--reflection--annotations)
- [Chapter 30 — Metaprogramming: KSP & Compiler Plugins](#chapter-30--metaprogramming-ksp--compiler-plugins)
- [Chapter 31 — Serialization in Depth](#chapter-31--serialization-in-depth)
- [Chapter 32 — Performance & Memory](#chapter-32--performance--memory)
- [Chapter 33 — Architecture & Dependency Injection](#chapter-33--architecture--dependency-injection)
- [Chapter 34 — Kotlin Multiplatform in Depth](#chapter-34--kotlin-multiplatform-in-depth)
- [Chapter 35 — Designing Libraries & Public APIs](#chapter-35--designing-libraries--public-apis)
- [Chapter 36 — Advanced Testing](#chapter-36--advanced-testing)

**Appendices**

- [Appendix A — Cheat Sheet](#appendix-a--cheat-sheet)
- [Appendix B — Glossary](#appendix-b--glossary)
- [Appendix C — Further Resources](#appendix-c--further-resources)
- [Appendix D — The Task Manager, Assembled](#appendix-d--the-task-manager-assembled)


---

## Chapter 1 — Getting Started

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** none — start here.

**Learning objectives** — after this chapter you will be able to:

- Say what Kotlin is, where it runs, and why it exists.
- Set up a working Kotlin environment (or write your first program with *zero* install).
- Create and run a Kotlin program, and explain what "run" actually does.
- Read the anatomy of `fun main()` and print output with `println`.
- Organize source files with packages and imports.

**In this chapter**

- [1.1 What is Kotlin, and why?](#11-what-is-kotlin-and-why)
- [1.2 Setting up (or skipping setup)](#12-setting-up-or-skipping-setup)
- [1.3 Your first program](#13-your-first-program)
- [1.4 What "running" actually does](#14-what-running-actually-does)
- [1.5 `println`, `print`, and the console](#15-println-print-and-the-console)
- [1.6 Files, packages, and imports](#16-files-packages-and-imports)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-task-manager-v0) · Glossary · What's next

---

### 1.1 What is Kotlin, and why?

**Kotlin** is a modern, statically-typed programming language created by **JetBrains** (the company behind IntelliJ IDEA) and first released in 2016. In 2019 Google made it the **preferred language for Android** development. Today it is used for Android apps, server-side backends, desktop tools, and even code that compiles to JavaScript or native binaries.

Two words in that description carry a lot of weight:

- **Statically-typed** means every value has a type the compiler knows *before* the program runs. If you try to subtract text from a number or call a string-only operation on an integer, the compiler stops you at build time instead of letting the program crash later. Types are a safety net. (String concatenation with `+` is deliberately supported, so `"tasks: " + 3` is valid.)
- **Modern** means Kotlin learned from decades of pain in older languages. It is concise (little boilerplate), safe (null safety, immutability by default), and pragmatic (it runs on the same platform as Java and works seamlessly with the enormous Java ecosystem).

The single most important fact about Kotlin's origins: it runs primarily on the **Java Virtual Machine (JVM)** — the same runtime as Java. This is why Kotlin could arrive with a mature ecosystem on day one: every Java library ever written is available to you. You get a nicer language *and* keep the tools.

> ☕ **Coming from Java** — Think of Kotlin as "Java with twenty years of hindsight." Your Java knowledge transfers almost entirely; you'll mostly be *un*learning boilerplate. The two languages compile to the same bytecode and can call each other freely (Chapter 18 is devoted to this).

### 1.2 Setting up (or skipping setup)

You have two paths. Pick based on how much you want to install today.

**Path A — Zero install (fastest start).** Open the **Kotlin Playground** in your browser at `play.kotlinlang.org`. You can type and run Kotlin immediately, with nothing to install. This is perfect for the early chapters — every non-project example here runs there.

**Path B — A real development environment (recommended once you're serious).** Install an IDE that understands Kotlin deeply:

- **IntelliJ IDEA Community Edition** (free) for general/backend Kotlin.
- **Android Studio** (free) if you're targeting Android.

Both bundle everything you need — including a **JDK** (Java Development Kit), the toolchain that actually compiles and runs JVM code. To create a project in IntelliJ IDEA:

1. **New Project**.
2. Choose **Kotlin**, and **JVM** as the platform.
3. Pick **Gradle** with the **Kotlin DSL** as the build system (we cover Gradle properly in Chapter 19).
4. Name it and click **Create**.

> ⚠️ **Gotcha** — Running Kotlin on your own machine requires a **JDK** to be present. The IDEs install one for you, which is why Path B "just works." If you ever try to compile from the command line and get "command not found" or "no JDK," an absent or unconfigured JDK is almost always the cause.

### 1.3 Your first program

Create a file named `Main.kt` (Kotlin source files end in `.kt`). Put exactly this in it:

```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```

Run it, and the console prints:

```text
Hello, Kotlin!
```

That is a complete, valid Kotlin program. Let's read it token by token, because every part will recur thousands of times:

- **`fun`** — the keyword that begins a *function*, a named block of code you can run. (Functions get a full chapter of their own, Chapter 5.)
- **`main`** — the function's name. `main` is special: it is an **entry point**, a function the launcher can call to start your program. A small application normally has one, but a project may contain several `main` functions; an IDE run configuration or Gradle's `mainClass` chooses which one to launch.
- **`()`** — the parameter list. Here it's empty: `main` takes no inputs.
- **`{ … }`** — the function *body*: the code that runs when the function is called.
- **`println("Hello, Kotlin!")`** — a call to the built-in `println` function, asking it to print the text `"Hello, Kotlin!"`. Text wrapped in double quotes is a **string** (Chapter 2).

There is also a variant that receives command-line arguments, which you'll see in some projects:

```kotlin
fun main(args: Array<String>) {
    println("You passed ${args.size} arguments")
}
```

`args` is an array of the strings typed after the program name on the command line. You rarely need it early on, so the no-argument `fun main()` is the norm.

> ☕ **Coming from Java** — In Java the entry point is `public static void main(String[] args)` *inside a class*. Kotlin needs none of that ceremony: no `public`, no `static`, no `void`, and no enclosing class. A bare top-level `fun main()` is enough. That compactness is a theme, not a one-off.

### 1.4 What "running" actually does

When you click Run, three things happen in sequence:

1. The Kotlin **compiler** reads your `.kt` source and translates it into **JVM bytecode** — compact instructions stored in `.class` files. This step is where type errors are caught.
2. The **JVM** loads those `.class` files.
3. The JVM finds your `main` and executes it.

So "running" is really *compile, then execute*. The important payoff: many mistakes (a typo in a name, a type mismatch) are caught in step 1, before your program ever runs, rather than surprising a user later.

> ⚙️ **Under the hood** — The JVM has no concept of a "top-level function" — everything on the JVM lives inside a class. So when the compiler sees your top-level `fun main()` in `Main.kt`, it *generates* a class to hold it, named after the file with `Kt` appended: `MainKt`, with a static `main` method. Your "class-free" program is class-free only in the source; the compiler quietly builds the class the JVM requires. (We'll use this fact in Chapter 18 when calling Kotlin from Java.)

### 1.5 `println`, `print`, and the console

`println` prints its argument **followed by a newline**, so each call starts a fresh line. Its sibling `print` does the same but **without** the trailing newline:

```kotlin
fun main() {
    print("Hello, ")
    print("world")
    println("!")      // ends this line
    println("next line")
}
```

Output:

```text
Hello, world!
next line
```

Notice how the two `print` calls and the first `println` all landed on one line, because only `println` added a line break. This is your primary tool for seeing what a program is doing, and you'll lean on it constantly while learning.

> 📝 **Micro-exercise** — Without running it, predict the exact output:
> ```kotlin
> fun main() {
>     println("A")
>     print("B")
>     print("C")
>     println("D")
> }
> ```
> <details><summary>Show answer</summary>
>
> ```text
> A
> BCD
> ```
> `println("A")` prints `A` and a newline. `print("B")` and `print("C")` add `B` then `C` with no breaks. `println("D")` adds `D` and ends the line. So line one is `A`, line two is `BCD`.
> </details>

### 1.6 Files, packages, and imports

Real programs do not stay in one `Main.kt`. A **package** gives declarations a stable, globally unique name and an **import** lets another file use that declaration without spelling its full name.

```kotlin
// src/main/kotlin/com/example/tasks/model/Task.kt
package com.example.tasks.model

data class Task(val title: String)
```

```kotlin
// src/main/kotlin/com/example/tasks/app/Main.kt
package com.example.tasks.app

import com.example.tasks.model.Task

fun main() {
    println(Task("Learn packages"))
}
```

The fully qualified name is `com.example.tasks.model.Task`. Package names conventionally use a reversed domain and lowercase segments. Kotlin does not require the directory to match the package, but matching them makes navigation and build configuration predictable.

Imports can name more than classes:

```kotlin
import com.example.tasks.model.Task
import com.example.tasks.format.summary       // top-level function
import com.example.tasks.Priority.HIGH         // enum entry
import java.time.LocalDate as JavaDate          // resolve a name collision
```

Kotlin automatically imports common packages such as `kotlin.*`, `kotlin.collections.*`, and—on the JVM—`java.lang.*`. An explicit import is therefore unnecessary for `String`, `List`, or `println`.

> 💡 **Idiom** — Prefer explicit imports in production code. A star import such as `import com.example.tasks.*` is legal, but it hides where names came from and makes collisions easier during large refactors. IDEs can manage imports automatically.

> ⚙️ **Under the hood** — A package is a naming boundary, not an object and not necessarily a folder. Top-level declarations compile into generated file classes on the JVM, while their package becomes part of their bytecode name. This is why moving a public declaration to another package is an API-breaking change.

> 📝 **Micro-exercise** — Two libraries both declare `Clock`. Import one normally and alias the other to `TestClock`.
>
> <details><summary>Show answer</summary>
>
> ```kotlin
> import com.example.time.Clock
> import com.example.testing.Clock as TestClock
> ```
> </details>

---

### Summary

- **Kotlin** is a modern, statically-typed language from JetBrains that runs mainly on the **JVM**, giving it Java's entire ecosystem while fixing much of Java's verbosity. It's Google's preferred language for Android.
- **Statically typed** = types are checked at compile time, catching a class of bugs before the program runs.
- You can start with **zero install** in the Kotlin Playground, or use **IntelliJ IDEA / Android Studio** (which bundle a **JDK**) for real projects.
- The entry point is a top-level **`fun main()`** — no class, no `static`, no boilerplate.
- "Running" means **compile to JVM bytecode, then execute**. The compiler generates a class (`MainKt`) to hold your top-level `main`, because the JVM requires everything to live in a class.
- **`println`** prints with a trailing newline; **`print`** prints without one.
- A source file may declare a **package**; **imports** make declarations from other packages available, and `as` aliases resolve name collisions.

### Self-check quiz

1. Why can Kotlin use Java libraries?
   <details><summary>Answer</summary>Because Kotlin compiles to the same JVM bytecode Java does and runs on the same JVM, so Java libraries are directly available.</details>
2. What does "statically typed" buy you?
   <details><summary>Answer</summary>The compiler knows every value's type before the program runs and rejects type-mismatched code at build time, catching many bugs early.</details>
3. What is special about the `main` function?
   <details><summary>Answer</summary>It is a valid program entry point. A project may contain several; the launcher or Gradle configuration chooses the one to run.</details>
4. Your top-level `fun main()` has no class. What does the compiler do about the JVM's requirement that code live in a class?
   <details><summary>Answer</summary>It generates a class named after the file with `Kt` appended (e.g. `MainKt`) containing a static `main` method.</details>

### Exercises

**Exercise 1.1 — Personal intro (guided).** Write a program that prints your name, your age, and your city, each on its own line.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    println("Name: Alice")
    println("Age: 25")
    println("City: Berlin")
}
```

**Why this works:** three separate `println` calls each print their text and then a newline, so the three facts land on three lines. (In Chapter 2 you'll store these as variables instead of hard-coding them.)

</details>

**Exercise 1.2 — One line, two ways.** Produce the single output line `Kotlin is fun!` using **at least two** `print`/`println` calls (not one big string).

<details><summary>Show solution</summary>

```kotlin
fun main() {
    print("Kotlin ")
    print("is ")
    println("fun!")
}
```

**Why this works:** `print` writes without a newline, so the fragments stay on one line; the final `println` adds `fun!` and ends the line. Because only the last call breaks the line, all the pieces appear together as `Kotlin is fun!`.

</details>

### Chapter project: Task Manager v0

> 🛠️ **Chapter Project** — This is the very first version of the **running Task Manager** we grow across the book. **Builds on:** Chapter 1 only. It's deliberately tiny — the point is to run *something* end to end.

**Goal.** Print a welcome banner and a short, hard-coded task list.

**Requirements.**
1. Print a banner line (e.g. `=== My Task Manager ===`).
2. Print two or three tasks, one per line.
3. Print a closing line (e.g. `You have 3 tasks.`).

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun main() {
    println("=== My Task Manager ===")
    println("1. Write the first chapter")
    println("2. Review it with a friend")
    println("3. Take a break")
    println("You have 3 tasks.")
}
```

Output:

```text
=== My Task Manager ===
1. Write the first chapter
2. Review it with a friend
3. Take a break
You have 3 tasks.
```

**Commentary.** Everything here is hard-coded — the task text, the numbers, even the count `3`. That's fine for v0; the *whole rest of the book* is about removing that hard-coding. In Chapter 2 the count becomes a computed value from variables; in Chapter 6 the tasks become a real list you can add to; in Chapter 8 each task becomes a proper object. Watch this program grow.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Kotlin** | A modern, statically-typed JVM language by JetBrains; Google's preferred Android language. |
| **JVM (Java Virtual Machine)** | The runtime that executes JVM bytecode; Kotlin's primary target. |
| **Statically typed** | Types are known and checked at compile time, before the program runs. |
| **Compiler** | The tool that translates source code into bytecode, catching type errors. |
| **Bytecode** | The compact JVM instructions in `.class` files that the JVM executes. |
| **JDK (Java Development Kit)** | The toolchain (compiler + runtime + libraries) needed to build and run JVM code. |
| **Entry point** | The function the runtime calls to start a program — Kotlin's top-level `main`. |
| **`println` / `print`** | Console output, with / without a trailing newline. |
| **Package / import** | A namespace for declarations / a directive that brings a declaration into a file by its short name. |
| **Fully qualified name** | A declaration's complete package plus name, such as `com.example.tasks.model.Task`. |

### What's next

You can run a program and print output — now let's give it something to work with. **[Ch.2 — Variables & Data Types](#chapter-2--variables--data-types)** introduces `val`/`var`, Kotlin's basic types, and string templates, and turns Task Manager v0's hard-coded numbers into real, computed values.

[↑ back to top](#chapter-1--getting-started)


---

## Chapter 2 — Variables & Data Types

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.1 — Getting Started](#chapter-1--getting-started)

**Learning objectives** — after this chapter you will be able to:

- Choose between `val` and `var`, and explain what each really guarantees.
- Use Kotlin's basic types and their literals confidently.
- Convert between numeric types, and explain why Kotlin refuses to do it for you.
- Build strings with templates, and use multiline strings cleanly.
- Explain Kotlin's root and bottom types, and choose between generic and primitive arrays.
- Use unsigned integers only when their domain semantics justify them.
- Avoid the classic beginner traps: integer division, silent overflow, and "immutable that isn't."

**In this chapter**

- [2.1 `val` and `var`: naming values](#21-val-and-var-naming-values)
- [2.2 Type inference](#22-type-inference)
- [2.3 The basic types](#23-the-basic-types)
- [2.4 Number literals](#24-number-literals)
- [2.5 Type conversions](#25-type-conversions)
- [2.6 Strings, templates, and multiline text](#26-strings-templates-and-multiline-text)
- [2.7 `Any`, `Unit`, and `Nothing`](#27-any-unit-and-nothing)
- [2.8 Arrays and primitive arrays](#28-arrays-and-primitive-arrays)
- [2.9 Unsigned integers](#29-unsigned-integers)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-modelling-a-task) · Glossary · What's next

---

### 2.1 `val` and `var`: naming values

A program needs to give names to values so it can refer to them. Kotlin has two keywords for this, and choosing between them is a small decision you'll make hundreds of times a day.

- **`val`** declares a **read-only** name: once assigned, it can never be reassigned. (Think "value" or "final.")
- **`var`** declares a **reassignable** name: you can point it at a new value later. (Think "variable.")

```kotlin
val name = "Alice"   // read-only
var age = 25         // reassignable
age = 26             // ✅ fine — var can be reassigned
// name = "Bob"      // ❌ compile error: Val cannot be reassigned
```

Read that error as the compiler protecting you: you *said* `name` was a fixed value, so it holds you to it.

> 💡 **Idiom** — **Prefer `val` by default; reach for `var` only when you truly need to reassign.** Read-only names are easier to reason about (their value can't change out from under you) and prevent a whole category of bugs. In good Kotlin, `val` vastly outnumbers `var`.

> ⚠️ **Gotcha** — `val` freezes the *name*, not the *object it points to*. If a `val` holds a mutable object, the object's contents can still change:
> ```kotlin
> val list = mutableListOf(1, 2, 3)
> list.add(4)          // ✅ allowed — we're mutating the list, not reassigning `list`
> println(list)        // → [1, 2, 3, 4]
> // list = mutableListOf(9)  // ❌ this would be reassignment — not allowed
> ```
> `val` means "this name will always point to *this* object." Whether that object is itself changeable is a separate question (Chapter 6).

> ☕ **Coming from Java** — `val` is like Java's `final`. The difference is cultural: in Kotlin `val` is the *default* you should reach for, whereas Java code often makes everything mutable. Kotlin nudges you toward immutability.

### 2.2 Type inference

You may have noticed we never wrote the *type* of `name` or `age`. We could:

```kotlin
val name: String = "Alice"
var age: Int = 25
```

The part after the colon is the **type annotation**. But Kotlin has **type inference**: the compiler looks at the value on the right and figures the type out for you. Since `"Alice"` is obviously a `String` and `25` is obviously an `Int`, the annotations are redundant, and idiomatic Kotlin omits them:

```kotlin
val name = "Alice"   // inferred as String
var age = 25         // inferred as Int
```

Inference is *not* dynamic typing — the type is still fixed and checked at compile time; you just didn't have to spell it out. You'll add explicit annotations when they aid clarity, when there's no initializer, or when you want a *different* type than the default (e.g. a `Long` instead of an `Int`).

### 2.3 The basic types

Kotlin's built-in types cover numbers, truth values, characters, and text.

**Integers** (whole numbers), in increasing size:

```kotlin
val b: Byte = 127                       // 8-bit,  -128 … 127
val s: Short = 32_000                   // 16-bit
val i: Int = 2_000_000_000             // 32-bit — the default for whole numbers
val l: Long = 9_000_000_000L           // 64-bit — note the L suffix
```

**Floating-point** (fractional numbers):

```kotlin
val pi: Double = 3.14159265358979       // 64-bit — the default for decimals
val g: Float = 9.81f                    // 32-bit — note the f suffix
```

**Boolean**, **Char**, and **String**:

```kotlin
val isReady: Boolean = true             // true or false
val grade: Char = 'A'                   // a single character, in SINGLE quotes
val greeting: String = "Hello"          // text, in DOUBLE quotes
```

When you write `25`, its inferred type is `Int`; when you write `3.14`, it's `Double`. Those two are the everyday defaults; you opt into the others deliberately.

> ⚠️ **Gotcha** — `Char` and `String` are different types with different quotes. `'A'` is a single `Char`. `"A"` is a `String` that happens to be one character long. Mixing the quotes is a common first-week mistake: `'Hello'` is an error (single quotes hold exactly one character).

> ⚙️ **Under the hood** — Kotlin's docs say it "has no primitive types" — everything looks like an object (`Int` has methods, e.g. `25.toLong()`). But at runtime the compiler is smart: a plain non-null `Int` compiles to a JVM **primitive `int`** (fast, no memory overhead), not a boxed object. The object-like surface is a compile-time convenience. The exception is when an `Int` must hold `null` (`Int?`) — then it *must* become a boxed `java.lang.Integer`. We unpack that fully in [Ch.7 — Null Safety](#chapter-7--null-safety).

### 2.4 Number literals

Kotlin lets you write numbers readably:

```kotlin
val million = 1_000_000        // underscores are ignored — just for grouping
val hex = 0xFF                 // hexadecimal → 255
val binary = 0b0000_1010       // binary → 10
val long = 100L                // Long (the L suffix)
val float = 2.5f               // Float (the f suffix)
val scientific = 1.5e3         // 1.5 × 10³ = 1500.0 (a Double)
```

The underscores are purely cosmetic — the compiler ignores them — but `1_000_000` is far easier to read than `1000000`.

### 2.5 Type conversions

Here Kotlin makes a choice that surprises newcomers: it **never** converts number types automatically. Even going from a smaller type to a bigger one — which is always safe — must be explicit.

```kotlin
val i: Int = 42
val l: Long = i        // ❌ compile error: type mismatch (Int is not a Long)
val l2: Long = i.toLong()   // ✅ explicit conversion
```

Every numeric type provides `toByte()`, `toShort()`, `toInt()`, `toLong()`, `toFloat()`, `toDouble()`, and `toString()`:

```kotlin
val i = 42
println(i.toLong())     // → 42
println(i.toDouble())   // → 42.0
println(i.toString())   // → "42"

val d = 3.99
println(d.toInt())      // → 3  (truncates toward zero — it does NOT round)
```

> ☕ **Coming from Java** — Java silently *widens* `int` to `long` and even `int` to `double`. Kotlin removed this implicit conversion on purpose, because it hides subtle bugs (an accidental `int`/`long` mix, precision loss). You trade a little typing for the compiler forcing you to *mean* every conversion.

> ⚠️ **Gotcha — integer division.** When both operands are integers, `/` does **integer division** and throws away the remainder:
> ```kotlin
> println(7 / 2)        // → 3   (not 3.5!)
> println(7 % 2)        // → 1   (the remainder, via the % operator)
> println(7.0 / 2)      // → 3.5 (at least one operand is a Double → real division)
> ```
> If you want a fractional result, make at least one side a floating-point number: `7.0 / 2` or `7 / 2.0`.

> ⚠️ **Gotcha — silent overflow.** Integer types wrap around at their limits without any error:
> ```kotlin
> val max = 2_147_483_647       // Int.MAX_VALUE
> println(max + 1)              // → -2147483648  (wraps to Int.MIN_VALUE!)
> ```
> If a value can exceed ~2.1 billion, use `Long`.

### 2.6 Strings, templates, and multiline text

You'll build strings out of other values constantly. The clumsy way is concatenation with `+`; the Kotlin way is a **string template**, where `$` splices a value directly into the string:

```kotlin
val name = "Alice"
val age = 25

println("My name is $name and I am $age years old")
// → My name is Alice and I am 25 years old
```

A bare `$name` inserts a simple variable. For anything more than a name — an expression, a property, a method call — wrap it in `${ … }`:

```kotlin
println("Next year I will be ${age + 1}")   // → Next year I will be 26
println("My name has ${name.length} letters")  // → My name has 5 letters
```

For text that spans several lines, use a **raw string** in triple quotes. It keeps newlines literally and needs no escaping, and `.trimIndent()` removes the leading indentation you added for readability:

```kotlin
val report = """
    Task Report
    ===========
    Name: $name
    Status: active
""".trimIndent()

println(report)
```

Output:

```text
Task Report
===========
Name: Alice
Status: active
```

> ⚙️ **Under the hood** — A string template isn't magic string-insertion at runtime; the compiler rewrites `"Hi $name"` into efficient concatenation (conceptually `StringBuilder().append("Hi ").append(name).toString()`). So templates are just nicer syntax over the same work you'd do by hand — with no performance penalty.

> 💡 **Idiom** — Prefer templates (`"Total: $count"`) over `+` concatenation (`"Total: " + count`). They read better and are less error-prone (no forgotten spaces, no accidental type surprises).

### 2.7 `Any`, `Unit`, and `Nothing`

Three types explain the edges of Kotlin's type system:

- **`Any`** is the root of every non-null Kotlin type. It exposes `equals`, `hashCode`, and `toString`.
- **`Unit`** is the meaningful "no result" value. A function that only performs an effect returns the single value `Unit`; the annotation is normally omitted.
- **`Nothing`** has no values. A function returning `Nothing` never completes normally—it throws or loops forever. Because no `Nothing` value can exist, `Nothing` is a subtype of every type.

```kotlin
fun log(message: String): Unit {
    println(message)
}

fun fail(message: String): Nothing = throw IllegalStateException(message)

fun titleOrFail(title: String?): String = title ?: fail("missing title")
```

The Elvis expression type-checks because the left branch produces `String` and the right branch never produces a competing value. `return`, `throw`, and `continue` fit naturally inside expressions for the same reason.

> ⚠️ **Gotcha** — `Any` excludes `null`; `Any?` includes every Kotlin value including `null`. `Nothing?` has exactly one possible value: `null`.

### 2.8 Arrays and primitive arrays

An `Array<T>` has fixed size and mutable elements. Use lists for most application data; use arrays at platform boundaries, for indexed mutable buffers, or after measurement shows they matter.

```kotlin
val names: Array<String> = arrayOf("Ada", "Linus")
names[1] = "Grace"
println(names.contentToString())          // [Ada, Grace]

val squares = Array(5) { index -> index * index }
println(squares.contentToString())        // [0, 1, 4, 9, 16]
```

Primitive-specialized arrays avoid boxing on the JVM:

```kotlin
val ids: IntArray = intArrayOf(10, 20, 30)
val bytes: ByteArray = "OK".encodeToByteArray()
val flags: BooleanArray = BooleanArray(1_000)
```

`Array<Int>` and `IntArray` are different, unrelated types. Convert deliberately with `toIntArray()` or `toTypedArray()`.

> ⚠️ **Gotcha — equality and printing.** Arrays inherit reference equality. Use `contentEquals`, `contentDeepEquals`, `contentToString`, and `contentHashCode` for their elements. `arrayOf(1) == arrayOf(1)` is `false` because they are different array objects.

### 2.9 Unsigned integers

`UByte`, `UShort`, `UInt`, and `ULong` represent non-negative bit patterns. Their literals use `u`/`uL`:

```kotlin
val permissions: UInt = 0b1010u
val maxPacketSize: UShort = 65_535u
val mask = permissions and 0b0010u
```

They are useful for binary formats, cryptography, protocol fields, and native APIs whose domain is genuinely unsigned. They are usually the wrong model for ordinary quantities: subtracting two counts can still underflow and wrap, and many Java/database APIs expect signed numbers.

> 💡 **Idiom** — "Cannot be negative" is not by itself a reason to use `UInt`. For a task count, use `Int` plus validation (`require(count >= 0)`). Choose unsigned types when interoperability or bit-level semantics require their exact range and operations.

---

### Summary

- **`val`** is a read-only name; **`var`** is reassignable. Prefer `val`. `val` freezes the *name*, not the object it points to.
- **Type inference** lets you omit type annotations when the value makes the type obvious — but the type is still static and checked.
- The everyday types: **`Int`** (whole numbers) and **`Double`** (decimals) are the defaults; **`Long`**/`Float`/`Byte`/`Short` are opt-in; plus **`Boolean`**, **`Char`** (single quotes), and **`String`** (double quotes).
- Literals can use `_` for grouping, `0x`/`0b` prefixes, and `L`/`f` suffixes.
- Kotlin **never converts numbers implicitly** — call `.toLong()`, `.toDouble()`, etc. Beware **integer division** (`7/2 == 3`) and **silent overflow** (use `Long` for big values).
- **String templates** (`$x`, `${expr}`) and **triple-quoted** multiline strings (`""" … """.trimIndent()`) are the idiomatic way to build text.
- **`Any`** is the non-null root type, **`Unit`** is the single no-result value, and **`Nothing`** marks code that cannot return.
- Arrays are fixed-size mutable buffers; primitive arrays such as **`IntArray`** avoid boxing. Unsigned types are specialized tools for unsigned protocols and bit patterns.

### Self-check quiz

1. What exactly does `val` prevent, and what does it *not* prevent?
   <details><summary>Answer</summary>It prevents reassigning the name to a different object. It does not prevent mutating the object the name points to (e.g. adding to a `MutableList` held by a `val`).</details>
2. What is `9 / 4` and why? What about `9.0 / 4`?
   <details><summary>Answer</summary>`9 / 4` is `2` — integer division discards the remainder because both operands are `Int`. `9.0 / 4` is `2.25` because one operand is a `Double`, giving real division.</details>
3. Why won't `val x: Long = someInt` compile, and how do you fix it?
   <details><summary>Answer</summary>Kotlin has no implicit numeric widening; `Int` and `Long` are distinct types. Fix: `val x: Long = someInt.toLong()`.</details>
4. When do you need `${ … }` instead of just `$x` in a template?
   <details><summary>Answer</summary>Whenever you interpolate more than a plain variable — any expression, property access, or function call, e.g. `${age + 1}` or `${name.length}`.</details>

### Exercises

**Exercise 2.1 — Rectangle (guided).** Store a rectangle's `length` and `width`, compute its area and perimeter, and print all four using string templates.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val length = 10.0
    val width = 5.0
    val area = length * width
    val perimeter = 2 * (length + width)

    println("Dimensions: $length x $width")
    println("Area: $area")
    println("Perimeter: $perimeter")
}
```

Output:

```text
Dimensions: 10.0 x 5.0
Area: 50.0
Perimeter: 30.0
```

**Why this works:** using `Double` literals (`10.0`, `5.0`) makes all the arithmetic floating-point, so there's no integer-division surprise. `area` and `perimeter` are computed once into `val`s and then spliced into the output with templates.

</details>

**Exercise 2.2 — Convert and truncate.** Given `val price = 19.99`, print the whole-dollar amount (the part before the decimal) as an `Int`. Then explain, in a comment, why the result isn't rounded.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val price = 19.99
    val dollars = price.toInt()   // truncates toward zero — does NOT round
    println("Whole dollars: $dollars")   // → Whole dollars: 19
}
```

**Why this works:** `toInt()` on a `Double` drops the fractional part entirely (it truncates, not rounds), so `19.99` becomes `19`, not `20`. If you actually wanted rounding you'd use `price.roundToInt()` (from `kotlin.math`).

</details>

### Chapter project: modelling a task

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–2. We replace v0's hard-coded numbers with real values and computed output. (No functions, collections, or `if` yet — those come in Ch.4–6.)

**Goal.** Represent a single task and a small progress summary using variables, arithmetic, and templates.

**Requirements.**
1. Store a task's `id`, `title`, and `isDone` in appropriately-typed `val`s/`var`s.
2. Store `totalTasks` and `completedTasks` counts.
3. Compute a whole-number completion **percentage**.
4. Print a formatted summary using string templates (and one multiline block).

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun main() {
    // A single task, modelled as loose variables (Ch.8 will make this a real type)
    val id = 1
    val title = "Write chapter 2"
    var isDone = false
    isDone = true          // we just finished it — var lets us update the flag

    // Progress counts
    val totalTasks = 3
    val completedTasks = 2

    // Whole-number percentage. Note: multiply BEFORE dividing so integer
    // division doesn't crush the result to 0.
    val percentComplete = completedTasks * 100 / totalTasks

    val summary = """
        === My Task Manager ===
        Task #$id: $title (done: $isDone)
        Progress: $completedTasks of $totalTasks tasks
        Completion: $percentComplete%
    """.trimIndent()

    println(summary)
}
```

Output:

```text
=== My Task Manager ===
Task #1: Write chapter 2 (done: true)
Progress: 2 of 3 tasks
Completion: 66%
```

**Commentary.**
- `id`, `title` are `val` (they don't change); `isDone` is `var` because a task's done-state genuinely changes over time — a textbook case for `var`.
- `completedTasks * 100 / totalTasks` deliberately multiplies first: `2 * 100 / 3 = 200 / 3 = 66` (integer division truncates the `.66…`). If you wrote `completedTasks / totalTasks * 100` you'd get `0 * 100 = 0` — a classic bug. Ordering matters.
- The three loose variables (`id`, `title`, `isDone`) describing *one* thing are a smell we'll cure in Chapter 8 with a `data class Task`. For now, variables + templates are all we have — and they're enough.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`val`** | A read-only name; cannot be reassigned. |
| **`var`** | A reassignable name. |
| **Type inference** | The compiler deducing a value's type so you can omit the annotation. |
| **Type annotation** | Explicitly stating a type after `:` (e.g. `val x: Long`). |
| **`Int` / `Long`** | 32-bit / 64-bit whole-number types. |
| **`Double` / `Float`** | 64-bit / 32-bit fractional types. |
| **`Char` / `String`** | A single character (single quotes) / text (double quotes). |
| **Integer division** | `/` between integers, discarding the remainder. |
| **Overflow** | Wrapping around when a value exceeds a type's range. |
| **String template** | Splicing values into a string with `$x` / `${expr}`. |
| **Raw string** | A triple-quoted string that preserves newlines and needs no escaping. |

### What's next

You can name and compute values — but real programs make *decisions* and *repeat* work. **[Ch.3 — Operators & Expressions](#chapter-3--operators--expressions)** sharpens how those values combine (including the crucial difference between `==` and `===`), and **[Ch.4 — Control Flow](#chapter-4--control-flow)** adds `if`, `when`, and loops so the Task Manager can react and iterate.

[↑ back to top](#chapter-2--variables--data-types)


---

## Chapter 3 — Operators & Expressions

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.2 — Variables & Data Types](#chapter-2--variables--data-types)

**Learning objectives** — after this chapter you will be able to:

- Combine values with arithmetic, comparison, and logical operators.
- Explain the single most important operator difference for Java refugees: `==` vs `===`.
- Predict short-circuit evaluation and the value of pre- vs post-increment.
- Understand that Kotlin operators are really *function calls in disguise*.

**In this chapter**

- [3.1 Expressions vs statements](#31-expressions-vs-statements)
- [3.2 Arithmetic operators](#32-arithmetic-operators)
- [3.3 Comparison and equality: `==` vs `===`](#33-comparison-and-equality--vs)
- [3.4 Logical operators and short-circuiting](#34-logical-operators-and-short-circuiting)
- [3.5 Increment and decrement](#35-increment-and-decrement)
- [3.6 Operators are functions](#36-operators-are-functions)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-task-manager-statistics) · Glossary · What's next

---

### 3.1 Expressions vs statements

An **expression** is a piece of code that produces a *value*: `2 + 3` produces `5`; `age > 18` produces `true`. A **statement** performs an action but doesn't itself yield a usable value.

This distinction matters more in Kotlin than in many languages, because Kotlin makes an unusually large number of things into *expressions*. As you'll see next chapter, even `if` and `when` produce values in Kotlin. For now, the takeaway is simple: operators build expressions, and expressions can be stored in `val`s, passed around, and combined.

### 3.2 Arithmetic operators

The five arithmetic operators work as you'd expect, with the integer-division caveat from Chapter 2:

```kotlin
val a = 10
val b = 3

println(a + b)   // → 13   addition
println(a - b)   // → 7    subtraction
println(a * b)   // → 30   multiplication
println(a / b)   // → 3    division (integer: remainder discarded)
println(a % b)   // → 1    remainder (modulo)
```

The `%` operator (remainder) is quietly one of the most useful: `n % 2 == 0` tests evenness, `n % 10` extracts a last digit, and index wraparound (`(i + 1) % size`) rides on it.

> ⚠️ **Gotcha** — Floating-point arithmetic is *inexact*, because numbers like `0.1` can't be represented perfectly in binary:
> ```kotlin
> println(0.1 + 0.2)          // → 0.30000000000000004  (!)
> println(0.1 + 0.2 == 0.3)   // → false
> ```
> Never compare `Double`/`Float` values with `==` for equality. Compare within a small tolerance instead (e.g. `kotlin.math.abs(x - y) < 1e-9`), or use `BigDecimal` for money.

### 3.3 Comparison and equality: `==` vs `===`

Comparison operators produce a `Boolean`:

```kotlin
val x = 5
val y = 10

println(x < y)    // → true
println(x > y)    // → false
println(x <= y)   // → true
println(x >= y)   // → false
println(x == y)   // → false   equal?
println(x != y)   // → true    not equal?
```

Now the crucial part. Kotlin has **two** kinds of "equal":

- **`==` — structural equality.** "Do these two things have the same *content*?" This is what you want almost always.
- **`===` — referential equality.** "Are these two references the *same object* in memory?"

```kotlin
val a = "Kotlin"
val b = buildString { append("Kot"); append("lin") }  // a different String object, same text

println(a == b)    // → true   same content
println(a === b)   // → false  different objects in memory
```

> ☕ **Coming from Java** — This is the number-one trap for Java developers, and it's *reversed* from Java. In Java, `==` on objects means "same reference" and you must call `.equals()` for content. In Kotlin, **`==` means content** (it calls `equals()` for you) and **`===` means reference**. The Java habit of reaching for `==` to compare strings — a classic Java bug — is actually *correct* in Kotlin. Retrain your fingers accordingly.

> ⚙️ **Under the hood** — `a == b` compiles to a null-safe `equals` call: `a?.equals(b) ?: (b === null)`. So `==` handles nulls for you (two nulls are equal; a null and a non-null are not) and delegates content comparison to the type's `equals()`. For `data class`es, that `equals()` is generated for you (Chapter 8).

### 3.4 Logical operators and short-circuiting

Three operators combine `Boolean` values:

```kotlin
val sunny = true
val warm = false

println(sunny && warm)   // → false   AND: both must be true
println(sunny || warm)   // → true    OR:  at least one true
println(!sunny)          // → false   NOT: negation
```

`&&` and `||` are **short-circuiting**: they evaluate the right side only if they must.

- `a && b`: if `a` is `false`, the result is already `false`, so `b` is never evaluated.
- `a || b`: if `a` is `true`, the result is already `true`, so `b` is never evaluated.

This is not just an optimization — it's a tool. It lets you guard an operation with a cheap check first:

```kotlin
val name: String? = null
// Because the left side is false, `name.length` is never touched → no crash:
if (name != null && name.length > 3) {
    println("Long name")
}
```

You relied on exactly this in Chapter 7's smart casts: the `name != null &&` on the left makes the right side safe.

> ⚠️ **Gotcha** — There are also non-short-circuiting bitwise-style boolean operators `and`/`or` (as infix functions) that *always* evaluate both sides. You rarely want them for control flow. Stick with `&&` and `||` unless you specifically need both sides evaluated for their side effects.

### 3.5 Increment and decrement

`++` adds one; `--` subtracts one. Their *position* changes what the surrounding expression sees:

```kotlin
var count = 5
count++          // count is now 6
count--          // count is now 5
++count          // count is now 6
```

When used inside a larger expression, **post**-increment (`count++`) yields the value *before* incrementing, while **pre**-increment (`++count`) yields the value *after*:

```kotlin
var n = 5
println(n++)     // → 5   (prints old value, THEN n becomes 6)
println(n)       // → 6

var m = 5
println(++m)     // → 6   (m becomes 6 first, THEN prints)
```

> 💡 **Idiom** — When you're just bumping a counter on its own line, `count++` and `++count` are identical, so pick either. Only worry about the distinction when the increment is *embedded* in a bigger expression — and even then, prefer to split it out for readability. Clever `a[i++] = b[++j]` lines are how bugs hide.

### 3.6 Operators are functions

Here is the idea that unlocks how Kotlin really works: **every operator is shorthand for a function call.** When you write `a + b`, the compiler translates it into `a.plus(b)`. The `+` symbol is sugar over a method named `plus`.

```kotlin
val sum = 2 + 3          // is exactly: 2.plus(3)
val text = "Ho" + "!"    // is exactly: "Ho".plus("!")
```

This is why `+` works on `Int`, `Double`, `String`, and more: each of those types *defines* a `plus` function. And it's why **you** can make `+` (or `[]`, or `in`, or `==`) work on your *own* types — by defining the corresponding function. That power is called **operator overloading**, and it has a full treatment in [Ch.28 — Operator Overloading & Conventions](#chapter-28--operator-overloading--conventions). For now, just carry the mental model: operators are named functions wearing symbols.

| You write | Compiler calls |
|-----------|----------------|
| `a + b` | `a.plus(b)` |
| `a - b` | `a.minus(b)` |
| `a * b` | `a.times(b)` |
| `a / b` | `a.div(b)` |
| `a % b` | `a.rem(b)` |
| `a == b` | `a?.equals(b) ?: (b === null)` |
| `a in c` | `c.contains(a)` |
| `a[i]` | `a.get(i)` |

> ⚙️ **Under the hood** — Because operators map to *named* functions resolved at compile time, there's no runtime "operator dispatch" machinery — `2 + 3` compiles to the same efficient integer-add bytecode you'd get in Java. The function-call view is a compile-time model; the generated code is as fast as it gets.

---

### Summary

- An **expression** produces a value; Kotlin makes unusually many things expressions.
- Arithmetic: `+ - * / %`. Remember integer division and inexact floating-point (never `==` on `Double`).
- **`==` is structural** (content, via `equals`) and **`===` is referential** (same object). For Java developers this is *reversed* from Java — `==` on strings is correct here.
- `&&` and `||` **short-circuit**; use that to guard expensive or unsafe right-hand sides.
- `++`/`--`: post- yields the old value, pre- yields the new; identical when standalone.
- Every operator is a **function call** in disguise (`a + b` → `a.plus(b)`), which is why operators work across types and can be defined for your own.

### Self-check quiz

1. What does `7 % 3` evaluate to, and name one common use of `%`.
   <details><summary>Answer</summary>`1` (the remainder). Common uses: evenness test (`n % 2 == 0`), extracting a digit, or wrapping an index (`(i+1) % size`).</details>
2. In Kotlin, how do you check whether two strings have the same text? What does `===` check instead?
   <details><summary>Answer</summary>Use `==` (structural equality — it calls `equals`). `===` checks referential equality: whether both refer to the exact same object in memory.</details>
3. Why doesn't `name.length` crash in `if (name != null && name.length > 3)` when `name` is null?
   <details><summary>Answer</summary>`&&` short-circuits: `name != null` is `false`, so the right side (`name.length > 3`) is never evaluated.</details>
4. What do `println(n++)` then `println(n)` print if `n` starts at 0?
   <details><summary>Answer</summary>`0` then `1`. Post-increment yields the old value (0) before bumping `n` to 1.</details>

### Exercises

**Exercise 3.1 — Calculator (guided).** Given two `Double`s, print their sum, difference, product, and quotient using templates.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val a = 20.0
    val b = 4.0
    println("Sum: ${a + b}")           // → Sum: 24.0
    println("Difference: ${a - b}")    // → Difference: 16.0
    println("Product: ${a * b}")       // → Product: 80.0
    println("Quotient: ${a / b}")      // → Quotient: 5.0
}
```

**Why this works:** using `Double` operands makes `/` real division, so `20.0 / 4.0` is `5.0`, not a truncated integer. Each result is computed inline inside a `${ }` template.

</details>

**Exercise 3.2 — Even or odd, safely.** Write an expression that is `true` when an `Int` `n` is even. Then predict `println(4 % 2 == 0)` and `println(7 % 2 == 0)`.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val n = 4
    val isEven = n % 2 == 0
    println(isEven)              // → true
    println(4 % 2 == 0)         // → true
    println(7 % 2 == 0)         // → false
}
```

**Why this works:** an even number leaves remainder `0` when divided by 2. Note precedence: `%` binds tighter than `==`, so `n % 2 == 0` means `(n % 2) == 0` — exactly what we want.

</details>

**Exercise 3.3 — Reference vs content.** Predict the two outputs, then explain them.
```kotlin
val x = listOf(1, 2, 3)
val y = listOf(1, 2, 3)
println(x == y)
println(x === y)
```

<details><summary>Show solution</summary>

```text
true
false
```

**Why:** `x` and `y` are two *separate* list objects that happen to hold the same elements. `==` compares content (element by element) → `true`. `===` compares identity (same object?) → `false`, because they're distinct objects.

</details>

### Chapter project: Task Manager statistics

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–3. We add computed *statistics* using the operators. (Still no functions/collections/`if` — those arrive in Ch.4–6.)

**Goal.** From a few count variables, compute and print progress statistics — including a comparison result.

**Requirements.**
1. Track `total`, `completed` counts (and derive `remaining`).
2. Compute a whole-number `percentDone`.
3. Compute a `Boolean` "are we more than halfway done?".
4. Print a summary using templates.

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun main() {
    val total = 8
    val completed = 5
    val remaining = total - completed

    // Multiply before dividing so integer division keeps precision (Ch.2 gotcha)
    val percentDone = completed * 100 / total

    // A Boolean expression built from a comparison
    val pastHalfway = completed > total / 2

    println("=== Task Manager — Stats ===")
    println("Total: $total, Done: $completed, Remaining: $remaining")
    println("Progress: $percentDone%")
    println("Past halfway: $pastHalfway")
}
```

Output:

```text
=== Task Manager — Stats ===
Total: 8, Done: 5, Remaining: 3
Progress: 62%
Past halfway: true
```

**Commentary.**
- `completed * 100 / total` = `500 / 8` = `62` (integer division truncates `62.5`). Ordering matters, as in Chapter 2.
- `pastHalfway` is a plain `Boolean` value produced by the comparison `completed > total / 2` (that's `5 > 4` → `true`). Note `total / 2` is `4` by integer division — good enough for a "past halfway" heuristic, though for odd totals you'd think about the rounding.
- Everything here is still loose variables and arithmetic. In Chapter 4 we'll *branch* on these Booleans (`if`/`when`), and in Chapter 6 we'll compute stats over a real list of tasks instead of hand-maintained counters.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Expression** | Code that produces a value. |
| **Statement** | Code that performs an action without yielding a usable value. |
| **`%` (remainder)** | The modulo operator; the leftover after integer division. |
| **Structural equality (`==`)** | Same content; calls `equals()`. |
| **Referential equality (`===`)** | Same object in memory. |
| **Short-circuiting** | `&&`/`||` skipping the right side when the result is already determined. |
| **Pre/post increment** | `++x` yields the new value; `x++` yields the old value. |
| **Operator overloading** | Defining an operator (via its function, e.g. `plus`) for your own type. |

### What's next

You can build and compare values — now let's make the program *decide* and *repeat*. **[Ch.4 — Control Flow](#chapter-4--control-flow)** introduces `if` and `when` as expressions, plus `for`/`while` loops, so the Task Manager can react to those Booleans and iterate over work.

[↑ back to top](#chapter-3--operators--expressions)


---

## Chapter 4 — Control Flow

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Operators & Expressions](#chapter-3--operators--expressions)

**Learning objectives** — after this chapter you will be able to:

- Use `if` and `when` as **expressions** that return values, not just branches.
- Write `when` in all its forms: value matching, boolean conditions, ranges, and type checks.
- Iterate with `for`, ranges, `while`, and `do-while`, and control loops with `break`/`continue`.
- Avoid the classic range and exhaustiveness traps.

**In this chapter**

- [4.1 `if` as an expression](#41-if-as-an-expression)
- [4.2 The `when` expression](#42-the-when-expression)
- [4.3 `for` loops and ranges](#43-for-loops-and-ranges)
- [4.4 `while` and `do-while`](#44-while-and-do-while)
- [4.5 `break`, `continue`, labels, and `repeat`](#45-break-continue-labels-and-repeat)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-task-review-loop) · Glossary · What's next

---

### 4.1 `if` as an expression

You already know `if` as a way to run code conditionally. In Kotlin, `if` does something extra: it **returns a value**, so you can assign its result directly.

```kotlin
val a = 7
val b = 12

// if used as an expression — the whole thing evaluates to a or b
val max = if (a > b) a else b
println(max)   // → 12
```

When the branches need multiple lines, use blocks — the **last expression in each block is its value**:

```kotlin
val score = 82
val grade = if (score >= 90) {
    "A"
} else if (score >= 80) {
    "B"
} else {
    "C"
}
println(grade)   // → B
```

> ☕ **Coming from Java** — Java has a separate ternary operator (`a > b ? a : b`) *and* an `if` statement. Kotlin doesn't need a ternary: `if` *is* the expression, so `if (a > b) a else b` replaces `a > b ? a : b`. One construct, two jobs.

> ⚠️ **Gotcha** — When you use `if` as an *expression* (assigning its result), the `else` branch is **mandatory** — otherwise, what would the value be when the condition is false? As a plain statement (no value used), `else` is optional.

### 4.2 The `when` expression

`when` is Kotlin's supercharged replacement for the `switch` statement — and, like `if`, it's an expression. It comes in several forms.

**Value matching** (compare a subject against branches):

```kotlin
val day = 3
val name = when (day) {
    1 -> "Monday"
    2 -> "Tuesday"
    3 -> "Wednesday"
    4, 5 -> "Thursday or Friday"   // multiple values in one branch
    else -> "Weekend"
}
println(name)   // → Wednesday
```

`when` branches can test far more than equality — ranges with `in`, and types with `is`:

```kotlin
val x: Any = 42
val description = when (x) {
    0 -> "zero"
    in 1..9 -> "small number"          // range check
    in 10..99 -> "medium number"
    is String -> "a string of length ${x.length}"   // type check + smart cast
    else -> "something else"
}
println(description)   // → medium number
```

**Subject-less form** (each branch is a boolean condition — a clean replacement for long `if/else if` chains):

```kotlin
val temp = 5
val advice = when {
    temp < 0 -> "Freezing"
    temp < 10 -> "Cold"
    temp < 25 -> "Mild"
    else -> "Warm"
}
println(advice)   // → Cold
```

> ⚠️ **Gotcha — exhaustiveness.** When `when` is used as an *expression*, it must be exhaustive — every possible input must be covered, usually via `else`. Over an `enum` or `sealed` type (Chapter 10), the compiler can verify you've covered every case *without* an `else`, and will error if you miss one — a fantastic safety feature. Over open types like `Int` or `String`, you always need `else`.

> ⚙️ **Under the hood** — A `when` over an `enum` or over integer/`Int` constants can compile to a JVM `tableswitch`/`lookupswitch` — a constant-time jump table — rather than a chain of comparisons. So a large `when` on an enum isn't just readable; it's fast. Unlike Java's `switch`, `when` branches never "fall through," so there's no `break` boilerplate and no accidental fall-through bugs.

### 4.3 `for` loops and ranges

Kotlin's `for` loop iterates over anything that provides elements — most commonly a **range**. The `..` operator builds an inclusive range:

```kotlin
for (i in 1..5) {
    print("$i ")         // → 1 2 3 4 5
}
```

Ranges have modifiers for stepping, counting down, and exclusive ends:

```kotlin
for (i in 0..10 step 2) print("$i ")   // → 0 2 4 6 8 10
println()
for (i in 5 downTo 1) print("$i ")     // → 5 4 3 2 1
println()
for (i in 0 until 5) print("$i ")      // → 0 1 2 3 4   (until excludes the end)
```

You can iterate over collections directly, and get the index too with `withIndex()`:

```kotlin
val fruits = arrayOf("Apple", "Banana", "Cherry")

for (fruit in fruits) {
    println(fruit)
}

for ((index, fruit) in fruits.withIndex()) {
    println("$index: $fruit")   // → 0: Apple, then 1: Banana, then 2: Cherry
}
```

That `(index, fruit)` is a **destructuring declaration** — unpacking a pair of values into two names at once (more in Chapter 8).

> ⚠️ **Gotcha — range direction and off-by-one.** `1..5` includes `5`; `1 until 5` stops at `4`. And a range only counts *upward*: `for (i in 5..1)` runs **zero** times (it's an empty range), which surprises people. To count down you must use `downTo`: `for (i in 5 downTo 1)`.

> ⚙️ **Under the hood** — Writing `for (i in 1..100)` looks like it allocates an `IntRange` object and iterates it. But the compiler recognizes the pattern and **optimizes it into a plain counted loop** — the same `int i = 1; i <= 100; i++` bytecode you'd write in Java, with *no* object allocation. You get range readability at primitive-loop speed. (Store the range in a variable first, though, and that optimization can't apply.)

### 4.4 `while` and `do-while`

When you don't know the iteration count up front, use `while` (test *before* each pass) or `do-while` (test *after*, so the body always runs at least once):

```kotlin
var count = 0
while (count < 3) {
    println("count = $count")
    count++
}

var n = 0
do {
    println("n = $n")
    n++
} while (n < 3)
```

Use `do-while` when the body must run once regardless — a menu that shows at least once, an input prompt that asks at least once.

### 4.5 `break`, `continue`, labels, and `repeat`

Inside loops, `break` exits the loop entirely and `continue` skips to the next iteration:

```kotlin
for (i in 1..10) {
    if (i == 5) break           // stop the whole loop at 5
    if (i % 2 == 0) continue    // skip even numbers
    print("$i ")                 // → 1 3
}
```

For **nested** loops, a plain `break` only exits the innermost loop. A **label** lets you break out of an outer loop:

```kotlin
outer@ for (row in 1..3) {
    for (col in 1..3) {
        if (row + col == 4) break@outer   // jumps out of BOTH loops
        println("($row, $col)")
    }
}
// prints (1, 1), (1, 2)  then breaks out entirely at (1,3) where 1+3==4
```

Finally, when you simply want to do something *N* times, `repeat(n)` is cleaner than a manual counter (`it` is the current index, 0-based):

```kotlin
repeat(3) {
    println("Hello #$it")   // → Hello #0, Hello #1, Hello #2
}
```

> 💡 **Idiom** — Reach for `repeat(n) { … }` instead of `for (i in 0 until n) { … }` when you don't actually need the index for anything but counting. It states the intent — "do this n times" — more directly.

---

### Summary

- **`if` is an expression**: `val max = if (a > b) a else b`. As an expression it requires `else`; the last line of a block is its value.
- **`when`** replaces `switch` and is also an expression. Forms: value matching (with `,` for multiple, `in` for ranges, `is` for types) and the subject-less boolean form. It must be **exhaustive** as an expression; over `enum`/`sealed` the compiler checks coverage for you. No fall-through.
- **`for`** iterates ranges (`..`, `until`, `downTo`, `step`), arrays/collections, and `withIndex()`. Ranges only count upward — use `downTo` to descend. The compiler optimizes literal-range `for` loops into allocation-free counted loops.
- **`while`** tests before, **`do-while`** tests after (runs at least once).
- **`break`/`continue`** control loops; **labels** (`outer@` … `break@outer`) reach outer loops; **`repeat(n)`** does something n times.

### Self-check quiz

1. Rewrite `val s = if (n > 0) "pos" else "non-pos"` using nothing but this line — why is the `else` required here?
   <details><summary>Answer</summary>It's already correct. `else` is required because `if` is used as an *expression* (its value assigned to `s`), so every path must produce a value.</details>
2. How many times does `for (i in 5..1)` run, and how do you actually count down from 5 to 1?
   <details><summary>Answer</summary>Zero times — `5..1` is an empty upward range. Count down with `for (i in 5 downTo 1)`.</details>
3. When can a `when` expression omit `else` and still compile?
   <details><summary>Answer</summary>When its subject is an `enum` or `sealed` type and every case is covered — the compiler can verify exhaustiveness.</details>
4. What's the difference between `while` and `do-while`?
   <details><summary>Answer</summary>`while` checks the condition before the body (may run zero times); `do-while` checks after, so the body always runs at least once.</details>

### Exercises

**Exercise 4.1 — FizzBuzz (guided).** Print 1 to 100, but print "Fizz" for multiples of 3, "Buzz" for multiples of 5, and "FizzBuzz" for multiples of both.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    for (i in 1..100) {
        val line = when {
            i % 15 == 0 -> "FizzBuzz"
            i % 3 == 0 -> "Fizz"
            i % 5 == 0 -> "Buzz"
            else -> "$i"
        }
        println(line)
    }
}
```

**Why this works:** the subject-less `when` reads top to bottom and takes the *first* matching branch, so the combined case (`% 15`) must come first — otherwise `% 3` would grab multiples of 15 before it. A number divisible by both 3 and 5 is divisible by 15, which is why that single check suffices.

</details>

**Exercise 4.2 — Sum of evens.** Using a `for` loop, compute the sum of all even numbers from 1 to 20.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    var sum = 0
    for (i in 2..20 step 2) {
        sum += i
    }
    println(sum)   // → 110
}
```

**Why this works:** starting at 2 with `step 2` visits exactly the even numbers (2, 4, …, 20), so no `if` is needed. `sum += i` accumulates into a `var`. (2+4+…+20 = 110.)

</details>

**Exercise 4.3 — Countdown with a message.** Use a `while` loop to count down from 5 to 1, printing each number, then print "Liftoff!".

<details><summary>Show solution</summary>

```kotlin
fun main() {
    var n = 5
    while (n >= 1) {
        println(n)
        n--
    }
    println("Liftoff!")
}
```

**Why this works:** the loop runs while `n >= 1`, printing then decrementing, so it prints 5, 4, 3, 2, 1 and stops when `n` reaches 0. The final `println` runs after the loop. (You could also write the loop as `for (n in 5 downTo 1)`.)

</details>

### Chapter project: a task review loop

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–4. We loop over tasks and classify each with `when`. (We still lack real per-task data — that needs collections, Ch.6 — so here we *derive* a status from a rule, just to exercise control flow.)

**Goal.** Loop over a set of task numbers, assign each a status with `when`, tally the completed ones, and print a summary.

**Requirements.**
1. Loop `for` over task numbers `1..total`.
2. Use `when` to give each task a status string.
3. Keep a running `completed` count with `var` and `if`.
4. After the loop, print a percentage using arithmetic + templates.

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun main() {
    val total = 6
    var completed = 0

    println("=== Task Manager — Daily Review ===")
    for (taskNumber in 1..total) {
        // Placeholder rule (real per-task data arrives in Ch.6):
        val status = when {
            taskNumber % 6 == 0 -> "done + urgent"
            taskNumber % 2 == 0 -> "done"
            taskNumber % 3 == 0 -> "urgent"
            else -> "todo"
        }
        if (status.startsWith("done")) {
            completed++
        }
        println("Task #$taskNumber: $status")
    }

    val percent = completed * 100 / total
    println("Completed $completed of $total ($percent%)")
}
```

Output:

```text
=== Task Manager — Daily Review ===
Task #1: todo
Task #2: done
Task #3: urgent
Task #4: done
Task #5: todo
Task #6: done + urgent
Completed 3 of 6 (50%)
```

**Commentary.**
- The subject-less `when` classifies each task; the `% 6` branch comes first because it's the most specific (a task divisible by 6 is divisible by both 2 and 3).
- `completed` is a `var` mutated across iterations — a legitimate use of mutability for accumulation. `status.startsWith("done")` catches both `"done"` and `"done + urgent"`.
- `completed * 100 / total` = `300 / 6` = `50`.
- The "rule" is obviously artificial — we have no genuine per-task state yet. Chapter 6 replaces it with a real list of tasks you can add to and query; Chapter 8 turns each task into a proper object. The *control-flow shape* here (loop + `when` + tally) stays; only the data source improves.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`if` expression** | `if` used to produce a value (`else` required). |
| **`when`** | Kotlin's `switch` replacement; also an expression; no fall-through. |
| **Exhaustiveness** | A `when` expression covering every possible input (via `else`, or all `enum`/`sealed` cases). |
| **Range** | A sequence of values from `..`, `until`, `downTo`, optionally with `step`. |
| **`withIndex()`** | Iterates giving both index and element. |
| **`while` / `do-while`** | Loop testing before / after the body. |
| **`break` / `continue`** | Exit a loop / skip to its next iteration. |
| **Label** | `name@` marker letting `break`/`continue` target an outer loop. |
| **`repeat(n)`** | Runs a block n times, with index `it`. |

### What's next

Your programs can now decide and iterate. But we keep repeating logic inline — it's time to *name and reuse* it. **[Ch.5 — Functions](#chapter-5--functions)** introduces functions, default and named arguments, lambdas, and higher-order functions, letting the Task Manager's operations become reusable building blocks.

[↑ back to top](#chapter-4--control-flow)


---

## Chapter 5 — Functions

> **Level:** Beginner → Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.4 — Control Flow](#chapter-4--control-flow)

**Learning objectives** — after this chapter you will be able to:

- Declare functions with parameters, return types, and single-expression bodies.
- Use default and named arguments to replace piles of overloads.
- Pass behaviour around as lambdas, and write higher-order functions.
- Recognise `infix` and `tailrec`, and know what they buy you.

**In this chapter**

- [5.1 Declaring functions](#51-declaring-functions)
- [5.2 Single-expression functions](#52-single-expression-functions)
- [5.3 Default and named arguments](#53-default-and-named-arguments)
- [5.4 `vararg` and the spread operator](#54-vararg-and-the-spread-operator)
- [5.5 Lambdas and function types](#55-lambdas-and-function-types)
- [5.6 Higher-order functions](#56-higher-order-functions)
- [5.7 Local, `infix`, and `tailrec` functions](#57-local-infix-and-tailrec-functions)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-functions-for-the-task-manager) · Glossary · What's next

---

### 5.1 Declaring functions

A **function** packages a piece of behaviour under a name so you can run it repeatedly without repeating yourself. You've been calling `println` and writing `main` — now you'll write your own.

```kotlin
fun greet(name: String) {
    println("Hello, $name!")
}

fun add(a: Int, b: Int): Int {
    return a + b
}
```

Anatomy: `fun` starts the declaration; `add` is the name; `(a: Int, b: Int)` is the **parameter list** (each parameter is `name: Type`); `: Int` after the parentheses is the **return type**; and `return` hands a value back.

If a function returns nothing meaningful (like `greet`, which just prints), its return type is `Unit` — Kotlin's equivalent of `void`. You can write it or leave it off; these are identical:

```kotlin
fun printSum(a: Int, b: Int): Unit {   // explicit Unit
    println(a + b)
}

fun printSum2(a: Int, b: Int) {        // Unit inferred — the idiomatic form
    println(a + b)
}
```

> ☕ **Coming from Java** — A parameter's type comes *after* its name (`a: Int`, not `int a`), and the return type comes *after* the parameter list. `Unit` is like `void`, but — unlike `void` — it's a real type with a single value, which lets functions be used more flexibly (it matters for generics and lambdas later).

### 5.2 Single-expression functions

When a function's body is just "return this one expression," the braces-and-`return` ceremony is noise. Kotlin lets you use `=` instead:

```kotlin
fun multiply(a: Int, b: Int): Int = a * b

// The return type can usually be inferred, so you can drop it:
fun square(n: Int) = n * n
```

Read `fun multiply(a: Int, b: Int) = a * b` as "multiply *is* `a * b`." This **single-expression** form is extremely common in idiomatic Kotlin — you'll see it everywhere for small, focused functions.

> 💡 **Idiom** — Prefer the single-expression form for one-liners, but **keep an explicit return type on public functions** even when it could be inferred. It documents the API and stops an accidental body change from silently altering the return type.

### 5.3 Default and named arguments

A parameter can declare a **default value**, used when the caller omits it:

```kotlin
fun greet(name: String, greeting: String = "Hello") {
    println("$greeting, $name!")
}

greet("Alice")          // → Hello, Alice!   (greeting defaulted)
greet("Bob", "Hi")      // → Hi, Bob!
```

And you can pass arguments **by name**, in any order — which makes call sites self-documenting and lets you skip over defaulted parameters:

```kotlin
fun createUser(name: String, age: Int = 0, city: String = "Unknown") {
    println("$name, $age, $city")
}

createUser("Alice", city = "Berlin")   // → Alice, 0, Berlin   (age defaulted, city named)
createUser(name = "Bob", age = 30)     // → Bob, 30, Unknown
```

> ☕ **Coming from Java** — This one feature erases two entire Java patterns. The **telescoping overloads** (`createUser(name)`, `createUser(name, age)`, `createUser(name, age, city)` — three methods) collapse into *one* function with defaults. And many **builder classes** become unnecessary, because named arguments already give you readable, order-free construction.

> ⚠️ **Gotcha** — Positional arguments must come *before* named ones in a call. `createUser(age = 30, "Bob")` is an error; write `createUser(name = "Bob", age = 30)` (or put the positional first: `createUser("Bob", age = 30)`).

> ⚙️ **Under the hood** — Default arguments aren't copied into every call site. The compiler generates one extra synthetic method (a `…$default` method) that takes an integer **bitmask** marking which arguments the caller supplied; omitted ones get filled with their defaults inside that method. That's why default args are essentially free and why calling such a function *from Java* needs the `@JvmOverloads` annotation (Chapter 18) to see the convenient overloads.

### 5.4 `vararg` and the spread operator

A `vararg` parameter accepts *any number* of arguments, which arrive inside the function as an array:

```kotlin
fun sumAll(vararg numbers: Int): Int {
    return numbers.sum()   // numbers is an IntArray here
}

println(sumAll(1, 2, 3))          // → 6
println(sumAll(1, 2, 3, 4, 5))    // → 15
println(sumAll())                  // → 0
```

If you already have an array and want to pass its elements as the varargs, use the **spread operator** `*`:

```kotlin
val existing = intArrayOf(1, 2, 3)
println(sumAll(*existing, 4, 5))   // → 15   (spreads the array, then adds 4 and 5)
```

### 5.5 Lambdas and function types

Here's the leap that makes Kotlin feel modern: **functions are values.** You can store a function in a variable, pass it to another function, and return it — just like an `Int` or a `String`.

A function *value* is written as a **lambda**: code in braces, with parameters before an arrow `->`:

```kotlin
val square: (Int) -> Int = { x -> x * x }
println(square(5))   // → 25
```

The type `(Int) -> Int` reads "a function taking an `Int` and returning an `Int`." When a lambda has exactly **one** parameter, you can skip naming it and use the implicit `it`:

```kotlin
val double: (Int) -> Int = { it * 2 }
println(double(4))   // → 8

val shout: (String) -> String = { it.uppercase() + "!" }
println(shout("hi"))  // → HI!
```

A lambda's **last expression is its return value** — no `return` keyword inside:

```kotlin
val describe: (Int) -> String = { n ->
    val parity = if (n % 2 == 0) "even" else "odd"
    "$n is $parity"       // this line is the lambda's result
}
println(describe(7))   // → 7 is odd
```

### 5.6 Higher-order functions

A **higher-order function** is one that takes a function as a parameter (or returns one). This is how you write logic with a *hole* in it that the caller fills:

```kotlin
fun operate(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}

println(operate(5, 3, { x, y -> x + y }))   // → 8
println(operate(5, 3, { x, y -> x * y }))   // → 15
```

There's a syntax rule that makes this beautiful: if a lambda is the **last** argument, it can move *outside* the parentheses. And if it's the *only* argument, the parentheses vanish entirely. This is the **trailing-lambda** convention, and it's why so much Kotlin code reads like it has custom keywords:

```kotlin
println(operate(5, 3) { x, y -> x + y })   // same call, trailing-lambda style
```

You already saw this shape in `repeat(3) { … }` (Chapter 4) — `repeat` is just a higher-order function whose second argument is a lambda.

> ⚙️ **Under the hood** — On the JVM, a lambda becomes an object implementing a function interface (`Function2<Int, Int, Int>` for a two-arg lambda). Modern Kotlin uses the JVM's `invokedynamic` mechanism to create these lazily, keeping class counts and startup cost low. When a higher-order function is marked `inline` (Chapter 25), the compiler goes further and *pastes the lambda's body directly into the call site* — no object at all. That's why Kotlin's functional style has essentially no overhead where it counts.

> ⚠️ **Gotcha** — A bare `return` inside a lambda doesn't always mean "return from this lambda." In lambdas passed to `inline` functions (like `forEach`), a `return` returns from the *enclosing* function (a "non-local return"). To return just from the lambda, use a **labeled return**: `return@forEach`. We revisit this with `inline` in Chapter 25; for now, prefer letting the last expression be the result.

### 5.7 Local, `infix`, and `tailrec` functions

**Local functions** are functions declared *inside* other functions — handy for a helper used only in one place, and they can see the enclosing function's variables:

```kotlin
fun printGrades(scores: List<Int>) {
    fun label(score: Int) = if (score >= 60) "pass" else "fail"   // local helper
    for (s in scores) println("$s → ${label(s)}")
}
```

**`infix` functions** can be called without the dot and parentheses, reading like an operator. A function qualifies if it's a member or extension with exactly one parameter, marked `infix`:

```kotlin
infix fun Int.repeatedTimes(action: String) {
    repeat(this) { println(action) }
}

3 repeatedTimes "hi"   // reads like a sentence; prints hi three times
```

You've been using built-in infix functions already: `1 to "one"` (builds a `Pair`), `0 until 10`, `5 downTo 1`, and `10 step 2` are all infix functions, not special syntax.

**`tailrec` functions** let you write a recursive function that the compiler rewrites into a loop — so it can't blow the stack:

```kotlin
tailrec fun factorial(n: Int, acc: Long = 1): Long =
    if (n <= 1) acc else factorial(n - 1, acc * n)

println(factorial(5))    // → 120
```

For `tailrec` to apply, the recursive call must be the *very last* thing the function does (a "tail call"), as it is here.

> ⚙️ **Under the hood** — Normal recursion adds a stack frame per call, so a deep recursion throws `StackOverflowError`. `tailrec` transforms `factorial(n-1, acc*n)` into a plain loop that updates `n` and `acc` in place — constant stack, no overflow, loop speed. If you mark a function `tailrec` but its recursive call *isn't* in tail position, the compiler warns you rather than silently producing slow code.

---

### Summary

- A **function** is named, reusable behaviour: `fun name(params): ReturnType { … }`. `Unit` is the "returns nothing" type (like `void`).
- **Single-expression** functions use `=`: `fun square(n: Int) = n * n`.
- **Default arguments** and **named arguments** replace Java's telescoping overloads and many builders; positional args must precede named ones.
- **`vararg`** accepts any number of arguments (as an array); **`*`** spreads an existing array into a vararg.
- Functions are **values**: write them as **lambdas** (`{ x -> … }`, or `{ it … }` for one param; last expression is the result).
- **Higher-order functions** take/return functions; the **trailing-lambda** rule lets the last lambda sit outside the parentheses.
- **Local** functions are nested helpers; **`infix`** functions read like operators; **`tailrec`** turns tail recursion into a safe loop.

### Self-check quiz

1. What's the single-expression form of `fun cube(n: Int): Int { return n * n * n }`?
   <details><summary>Answer</summary>`fun cube(n: Int): Int = n * n * n` (and the `: Int` may be dropped, though keeping it on public functions is preferred).</details>
2. How do default + named arguments replace telescoping overloads?
   <details><summary>Answer</summary>One function with defaults covers all the "some args omitted" cases; named arguments let callers supply just the ones they want, in any order — no separate overloaded methods needed.</details>
3. In `list.forEach { println(it) }`, what is `it`?
   <details><summary>Answer</summary>The implicit name for the lambda's single parameter — here, the current element being iterated.</details>
4. Why can `tailrec` prevent a `StackOverflowError`?
   <details><summary>Answer</summary>Because the compiler rewrites the tail-recursive call into a loop that reuses one stack frame, instead of adding a new frame per recursion.</details>

### Exercises

**Exercise 5.1 — Temperature converter (guided).** Write single-expression functions to convert Celsius↔Fahrenheit, plus a `printTemperature(temp, unit)` with a default unit of `"C"`.

<details><summary>Show solution</summary>

```kotlin
fun celsiusToFahrenheit(c: Double): Double = c * 9 / 5 + 32
fun fahrenheitToCelsius(f: Double): Double = (f - 32) * 5 / 9

fun printTemperature(temp: Double, unit: String = "C") {
    when (unit.uppercase()) {
        "C" -> println("$temp°C = ${celsiusToFahrenheit(temp)}°F")
        "F" -> println("$temp°F = ${fahrenheitToCelsius(temp)}°C")
        else -> println("Unknown unit: $unit")
    }
}

fun main() {
    printTemperature(100.0)          // → 100.0°C = 212.0°F
    printTemperature(32.0, "F")      // → 32.0°F = 0.0°C
}
```

**Why this works:** the conversions are pure one-liners, ideal for the single-expression form. Note `c * 9 / 5` uses `Double` `c`, so it's real division (no integer-division trap). `printTemperature` defaults `unit` to `"C"`, so the common call needs only the number.

</details>

**Exercise 5.2 — Apply an operation twice.** Write `applyTwice(x, f)` that applies a function `f: (Int) -> Int` to `x` two times. Test it with a "+3" lambda.

<details><summary>Show solution</summary>

```kotlin
fun applyTwice(x: Int, f: (Int) -> Int): Int = f(f(x))

fun main() {
    println(applyTwice(10) { it + 3 })   // → 16
}
```

**Why this works:** `applyTwice` is higher-order — it takes a function and calls it on its own result: `f(f(10))`. With `{ it + 3 }`, that's `(10 + 3) + 3 = 16`. The trailing-lambda syntax lets the lambda sit outside the parentheses.

</details>

**Exercise 5.3 — Variadic max.** Write `maxOfAll(vararg n: Int): Int` that returns the largest of any number of ints (assume at least one). 

<details><summary>Show solution</summary>

```kotlin
fun maxOfAll(vararg n: Int): Int {
    var largest = n[0]
    for (value in n) {
        if (value > largest) largest = value
    }
    return largest
}

fun main() {
    println(maxOfAll(3, 9, 2, 7))   // → 9
    println(maxOfAll(42))           // → 42
}
```

**Why this works:** `vararg` gives `n` as an `IntArray`. We seed `largest` with the first element, then scan for anything bigger. (The standard library actually has `n.max()`, but writing the loop shows what `vararg` gives you.)

</details>

### Chapter project: functions for the Task Manager

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–5. We turn Chapter 4's inline review loop into reusable functions — including a higher-order one. (Real task *data* still waits for collections in Ch.6.)

**Goal.** Decompose the review logic into named functions with a default argument and a higher-order summary.

**Requirements.**
1. `completionPercent(done, total)` — a single-expression function.
2. `statusFor(taskNumber)` — returns a status string via `when`.
3. `review(total, header)` — loops, prints each task, returns the completed count; `header` has a default.
4. `summarize(done, total, format)` — higher-order: builds the summary using a caller-supplied formatter.

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun completionPercent(done: Int, total: Int): Int = done * 100 / total

fun statusFor(taskNumber: Int): String = when {
    taskNumber % 6 == 0 -> "done + urgent"
    taskNumber % 2 == 0 -> "done"
    taskNumber % 3 == 0 -> "urgent"
    else -> "todo"
}

fun review(total: Int, header: String = "Daily Review"): Int {
    var completed = 0
    println("=== Task Manager — $header ===")
    for (n in 1..total) {
        val status = statusFor(n)
        if (status.startsWith("done")) completed++
        println("Task #$n: $status")
    }
    return completed
}

fun summarize(done: Int, total: Int, format: (Int, Int) -> String): String =
    format(done, total)

fun main() {
    val total = 6
    val done = review(total)   // header defaults to "Daily Review"

    val summary = summarize(done, total) { d, t ->
        "Progress: ${completionPercent(d, t)}% ($d/$t)"
    }
    println(summary)
}
```

Output:

```text
=== Task Manager — Daily Review ===
Task #1: todo
Task #2: done
Task #3: urgent
Task #4: done
Task #5: todo
Task #6: done + urgent
Progress: 50% (3/6)
```

**Commentary.**
- The Chapter 4 blob is now four focused, testable functions. `completionPercent` and `statusFor` are single-expression; `review` uses a **default argument** (`header`) so the common call stays short.
- `summarize` is **higher-order**: it doesn't know *how* to format — the caller passes that in as a lambda. Swap the lambda and you get a different report with no change to `summarize`. That flexibility is the whole point of first-class functions.
- We still fabricate task status from a rule. In Chapter 6 these functions will operate over a *real* `List` of tasks; the function *shapes* stay, and their bodies get real data.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Function** | Named, reusable behaviour with parameters and a return type. |
| **`Unit`** | The "no meaningful return value" type (like `void`). |
| **Single-expression function** | A function whose body is one expression after `=`. |
| **Default argument** | A parameter value used when the caller omits it. |
| **Named argument** | Passing an argument by parameter name, in any order. |
| **`vararg`** | A parameter accepting any number of arguments (as an array). |
| **Spread (`*`)** | Expands an array into vararg arguments. |
| **Lambda** | A function value: `{ params -> body }` (or `{ it }` for one param). |
| **Higher-order function** | A function that takes or returns a function. |
| **Trailing lambda** | The convention of moving a last-argument lambda outside the parentheses. |
| **`infix`** | A one-parameter function callable without dot/parentheses. |
| **`tailrec`** | A modifier turning tail recursion into a loop. |

### What's next

Functions give the Task Manager reusable operations — but it still can't hold a real, growing list of tasks. **[Ch.6 — Collections](#chapter-6--collections)** introduces lists, sets, and maps, plus the powerful functional operators (`filter`, `map`, `groupBy`, …) that turn those lambdas from Chapter 5 into data-processing pipelines.

[↑ back to top](#chapter-5--functions)


---

## Chapter 6 — Collections

> **Level:** Beginner → Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions)

**Learning objectives** — after this chapter you will be able to:

- Choose between `List`, `Set`, and `Map`, and between read-only and mutable versions.
- Transform data with the functional operators (`filter`, `map`, `groupBy`, `reduce`, …).
- Explain why "read-only" is not the same as "immutable."
- Know when to switch a pipeline to a lazy `Sequence` — and why it matters.

**In this chapter**

- [6.1 Read-only vs mutable](#61-read-only-vs-mutable)
- [6.2 Lists](#62-lists)
- [6.3 Sets](#63-sets)
- [6.4 Maps](#64-maps)
- [6.5 Functional operations](#65-functional-operations)
- [6.6 Sequences: lazy pipelines](#66-sequences-lazy-pipelines)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-real-task-list) · Glossary · What's next

---

### 6.1 Read-only vs mutable

A **collection** holds many values in one object. Kotlin's collections come in two families, and understanding the split is the key to the whole chapter:

- **Read-only** interfaces: `List`, `Set`, `Map`. They expose *reading* operations (size, get, iterate) but no way to add or remove.
- **Mutable** interfaces: `MutableList`, `MutableSet`, `MutableMap`. They add the *writing* operations (`add`, `remove`, `put`, …).

You pick the family through the construction function: `listOf(...)` gives you a read-only `List`; `mutableListOf(...)` gives you a `MutableList`.

```kotlin
val readOnly = listOf(1, 2, 3)          // List<Int> — no add/remove
val mutable = mutableListOf(1, 2, 3)     // MutableList<Int> — can grow/shrink
mutable.add(4)                           // ✅
// readOnly.add(4)                        // ❌ no such method on List
```

> 💡 **Idiom** — **Default to read-only.** Return `List` from functions, accept `List` as parameters, and only reach for `MutableList` when you genuinely need to modify in place. Read-only collections are safer to share (a caller can't mutate your data behind your back) and communicate intent.

> ⚠️ **Gotcha — read-only ≠ immutable.** `List` means *you* have a read-only *view*. It does **not** guarantee the underlying data can never change. If some other reference holds the same collection as a `MutableList`, it can still mutate it, and your read-only view will see the change:
> ```kotlin
> val mutable = mutableListOf(1, 2, 3)
> val view: List<Int> = mutable      // a read-only view of the SAME list
> mutable.add(4)
> println(view)                       // → [1, 2, 3, 4]  — the view changed!
> ```
> Read-only restricts *what you can do through this reference*, not *what can ever happen to the data*. For guaranteed-unchanging data, don't hand out a mutable reference in the first place.

### 6.2 Lists

A **list** is an ordered collection allowing duplicates, indexed from 0:

```kotlin
val fruits = listOf("Apple", "Banana", "Cherry")
println(fruits[0])              // → Apple
println(fruits.size)            // → 3
println("Banana" in fruits)     // → true   (the `in` operator → contains)
println(fruits.first())         // → Apple
println(fruits.last())          // → Cherry
```

Mutable lists add in-place editing:

```kotlin
val numbers = mutableListOf(1, 2, 3)
numbers.add(4)          // [1, 2, 3, 4]
numbers.remove(2)       // removes the VALUE 2 → [1, 3, 4]
numbers[0] = 10         // index assignment → [10, 3, 4]
println(numbers)        // → [10, 3, 4]
```

> ⚠️ **Gotcha** — `numbers.remove(2)` removes the *element equal to* `2`, not the element at index 2. To remove by position, use `removeAt(2)`. For an `Int` list this is a classic confusion — read `remove` as "remove this value."

### 6.3 Sets

A **set** is an unordered collection of *unique* values — duplicates are silently dropped:

```kotlin
val unique = setOf(1, 2, 3, 2, 1)
println(unique)              // → [1, 2, 3]   (duplicates collapsed)
println(2 in unique)        // → true

val colors = mutableSetOf("Red", "Green")
colors.add("Blue")
colors.add("Red")           // already present — no effect
println(colors)             // → [Red, Green, Blue]
```

Sets shine for membership tests and de-duplication. Checking `x in someSet` is fast (roughly constant time), whereas `x in someList` scans the whole list.

### 6.4 Maps

A **map** associates **keys** with **values** — a lookup table:

```kotlin
val ages = mapOf("Alice" to 30, "Bob" to 25)
println(ages["Alice"])      // → 30
println(ages["Carol"])      // → null   (missing key → null, not a crash)
println(ages.keys)          // → [Alice, Bob]
println(ages.values)        // → [30, 25]

val scores = mutableMapOf("Math" to 90)
scores["Science"] = 95      // add/update via index assignment
scores["Math"] = 92         // overwrites
println(scores)             // → {Math=92, Science=95}
```

The `to` in `"Alice" to 30` is the infix function from Chapter 5 that builds a `Pair`. And notice `ages["Carol"]` returns `null` — map lookup is nullable by design, which is exactly the safety you studied in Chapter 7.

### 6.5 Functional operations

This is where collections become powerful. Kotlin's standard library gives every collection a rich set of operators that take the **lambdas** from Chapter 5 and build data pipelines. Here's the essential toolkit, over `val numbers = (1..10).toList()`:

```kotlin
val numbers = (1..10).toList()

// filter — keep elements matching a predicate
println(numbers.filter { it % 2 == 0 })     // → [2, 4, 6, 8, 10]

// map — transform each element
println(numbers.map { it * it })            // → [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

// reduce / fold — collapse to a single value
println(numbers.reduce { acc, n -> acc + n })     // → 55
println(numbers.fold(100) { acc, n -> acc + n })  // → 155  (starts from 100)

// find — first match (or null)
println(numbers.find { it > 7 })            // → 8

// any / all / none — boolean questions
println(numbers.any { it > 5 })             // → true
println(numbers.all { it > 0 })             // → true
println(numbers.none { it < 0 })            // → true

// take / drop — slice off the front
println(numbers.take(3))                    // → [1, 2, 3]
println(numbers.drop(8))                    // → [9, 10]

// sumOf / count / maxByOrNull — aggregates
println(numbers.sumOf { it })               // → 55
println(numbers.count { it % 2 == 0 })      // → 5
println(numbers.maxByOrNull { it })         // → 10

// groupBy — partition into a Map by a key function
println(numbers.groupBy { if (it % 2 == 0) "even" else "odd" })
// → {odd=[1, 3, 5, 7, 9], even=[2, 4, 6, 8, 10]}
```

These compose: chain them to express a transformation as a readable pipeline.

```kotlin
val result = numbers
    .filter { it % 2 == 0 }   // [2, 4, 6, 8, 10]
    .map { it * 10 }          // [20, 40, 60, 80, 100]
    .take(3)                  // [20, 40, 60]
println(result)               // → [20, 40, 60]
```

> ⚠️ **Gotcha** — `reduce` throws on an **empty** collection (there's no first element to start from), whereas `fold` takes an explicit initial value and handles empty gracefully. Prefer `fold` when the collection might be empty.

> ☕ **Coming from Java** — These read like Java Streams (`stream().filter().map()`), but with a crucial difference: on a plain Kotlin collection, `filter`/`map` are **eager** — each one runs immediately and returns a new list. Java's `Stream` is lazy. Kotlin's lazy equivalent is the `Sequence`, next.

> ⚙️ **Under the hood** — Because they're eager, `numbers.filter { … }.map { … }` allocates an **intermediate list after `filter`**, then another after `map`. On small collections that's irrelevant. On large ones (or long chains) it's wasted allocation and garbage — which is the problem `Sequence` solves.

### 6.6 Sequences: lazy pipelines

A **`Sequence`** runs the same operators **lazily**: instead of materializing a new list at each step, it pulls *one element* all the way through the pipeline, then the next. Nothing runs until a **terminal** operation (like `toList()` or `first()`) asks for results.

```kotlin
val result = (1..1_000_000).asSequence()
    .filter { it % 2 == 0 }
    .map { it * 2 }
    .take(5)
    .toList()
println(result)   // → [4, 8, 12, 16, 20]
```

Read what *doesn't* happen here: without `asSequence()`, `.filter` on a million numbers would build a 500,000-element list, then `.map` would build another, and only then `.take(5)` would slice off five — a huge amount of work for five results. As a `Sequence`, elements flow one at a time and `take(5)` stops the whole pipeline after the fifth result. The other 999,990 numbers are never processed.

> 💡 **Idiom** — Use a **`Sequence`** when you have a *large* collection **and** a *multi-step* pipeline (and especially when a `take`/`first` can short-circuit it). For small collections or single operations, plain eager operators are simpler and often faster (a Sequence has small per-element overhead). Rule of thumb: reach for `asSequence()` when the data is big or the chain is long — otherwise don't bother.

---

### Summary

- Collections come **read-only** (`List`/`Set`/`Map`, from `listOf`/`setOf`/`mapOf`) and **mutable** (`MutableList`/…, from `mutableListOf`/…). Prefer read-only.
- **Read-only ≠ immutable**: a read-only reference just can't mutate; another mutable reference to the same data still can.
- **`List`** ordered + duplicates + indexed; **`Set`** unique + fast membership; **`Map`** key→value with nullable lookup.
- The **functional operators** (`filter`, `map`, `reduce`/`fold`, `find`, `any`/`all`/`none`, `take`/`drop`, `groupBy`, `sumOf`, `count`, `maxByOrNull`) build readable pipelines from lambdas. `reduce` throws on empty — use `fold`.
- These operators are **eager** (each allocates a new list). A **`Sequence`** (`asSequence()`) makes them **lazy** — one element flows through the whole chain, and terminal ops like `take` can short-circuit. Use it for big data / long chains.

### Self-check quiz

1. What does "read-only ≠ immutable" mean in practice?
   <details><summary>Answer</summary>A read-only reference (`List`) can't be used to modify the data, but if another reference to the *same* collection is a `MutableList`, that reference can still change it — and the read-only view will see the change.</details>
2. Why does `map[missingKey]` return `null` instead of throwing?
   <details><summary>Answer</summary>Map lookup is nullable by design (`V?`), so the type system forces you to handle "key not present" — a null — rather than crash.</details>
3. When should you convert a chain to a `Sequence`?
   <details><summary>Answer</summary>When the collection is large and the pipeline has multiple steps (especially with a `take`/`first` that can short-circuit), to avoid allocating an intermediate list at each step.</details>
4. Why prefer `fold` over `reduce` for a possibly-empty list?
   <details><summary>Answer</summary>`reduce` throws on an empty collection (no initial element); `fold` supplies an explicit initial value and handles empty safely.</details>

### Exercises

**Exercise 6.1 — Student grades (guided).** Given a `Map<String, Int>` of names to grades, compute the average, the highest and lowest scorers, and the list of students who passed (grade ≥ 60).

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val grades = mapOf(
        "Alice" to 85, "Bob" to 72, "Charlie" to 58, "Diana" to 94, "Eve" to 67
    )

    val average = grades.values.average()
    val highest = grades.maxByOrNull { it.value }
    val lowest = grades.minByOrNull { it.value }
    val passed = grades.filter { it.value >= 60 }.keys

    println("Average: $average")                       // → Average: 75.2
    println("Highest: ${highest?.key} (${highest?.value})")  // → Highest: Diana (94)
    println("Lowest: ${lowest?.key} (${lowest?.value})")     // → Lowest: Charlie (58)
    println("Passed: $passed")                          // → Passed: [Alice, Bob, Diana, Eve]
}
```

**Why this works:** `grades.values` is the collection of scores, so `.average()` gives `(85+72+58+94+67)/5 = 75.2`. `maxByOrNull`/`minByOrNull` return the whole `Map.Entry` with the largest/smallest `value` (nullable, since the map could be empty). `filter` keeps entries whose value ≥ 60, and `.keys` extracts just the names.

</details>

**Exercise 6.2 — Word frequencies.** Given a sentence, count how many times each word appears (case-insensitive), returning a `Map<String, Int>`.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val sentence = "the cat sat on the mat the cat"
    val counts = sentence
        .split(" ")
        .groupingBy { it }
        .eachCount()
    println(counts)   // → {the=3, cat=2, sat=1, on=1, mat=1}
}
```

**Why this works:** `split(" ")` turns the sentence into a list of words. `groupingBy { it }.eachCount()` is a specialized, efficient idiom that groups by the word and counts each group in a single pass — cleaner than `groupBy { it }.mapValues { it.value.size }`. (All words here are already lowercase; for real input you'd `.lowercase()` first.)

</details>

**Exercise 6.3 — Lazy first matches.** From `1..1_000_000`, get the first 4 numbers that are divisible by 7 *and* whose square is greater than 1000 — efficiently.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val result = (1..1_000_000).asSequence()
        .filter { it % 7 == 0 }
        .filter { it * it > 1000 }
        .take(4)
        .toList()
    println(result)   // → [35, 42, 49, 56]
}
```

**Why this works:** as a `Sequence`, the pipeline stops as soon as `take(4)` has four results — it never scans the full million. The first multiples of 7 are 7, 14, 21, 28, 35, … ; the square->1000 filter needs the value above ~31.6, so 7/14/21/28 are dropped and 35, 42, 49, 56 are the first four survivors.

</details>

### Chapter project: a real task list

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — a big step. **Builds on:** Ch.1–6. At last we store *real* tasks in a collection and query them, instead of faking status from a rule.

**Goal.** Keep tasks in a `MutableList`, track completed ones in a `Set`, and produce reports with the functional operators — including a lazy version.

**Requirements.**
1. Store task titles in a `MutableList<String>`; track completed titles in a `MutableSet<String>`.
2. List **pending** tasks (not in the completed set) and count completed ones.
3. Group tasks by their first word.
4. Produce an uppercase display list, and a lazy "first few long tasks" list.

<details><summary>Show reference solution + commentary</summary>

```kotlin
fun main() {
    val tasks = mutableListOf("Write report", "Buy milk", "Call Sam", "Book flight")
    val done = mutableSetOf("Buy milk")

    // The manager evolves:
    tasks.add("Water plants")
    done.add("Call Sam")

    val pending = tasks.filter { it !in done }
    val completedCount = tasks.count { it in done }
    val byFirstWord = tasks.groupBy { it.substringBefore(" ") }
    val shouting = tasks.map { it.uppercase() }

    val firstLongTasks = tasks.asSequence()
        .filter { it.length > 8 }
        .map { it.uppercase() }
        .take(3)
        .toList()

    println("All tasks (${tasks.size}): $tasks")
    println("Pending (${pending.size}): $pending")
    println("Completed: $completedCount")
    println("Grouped by first word: $byFirstWord")
    println("Shouting: $shouting")
    println("First long tasks: $firstLongTasks")
}
```

Output:

```text
All tasks (5): [Write report, Buy milk, Call Sam, Book flight, Water plants]
Pending (3): [Write report, Book flight, Water plants]
Completed: 2
Grouped by first word: {Write=[Write report], Buy=[Buy milk], Call=[Call Sam], Book=[Book flight], Water=[Water plants]}
Shouting: [WRITE REPORT, BUY MILK, CALL SAM, BOOK FLIGHT, WATER PLANTS]
First long tasks: [WRITE REPORT, BOOK FLIGHT, WATER PLANTS]
```

**Commentary.**
- Tasks now live in real collections. `pending` uses `filter { it !in done }` — the `Set` gives fast membership tests. `completedCount` counts via the same set.
- `groupBy { it.substringBefore(" ") }` buckets tasks by their first word into a `Map`; `map { it.uppercase() }` transforms every title.
- The `asSequence()` version demonstrates laziness — with `take(3)`, only enough tasks are processed to find three long ones. Here the list is tiny so it doesn't matter, but the *pattern* is exactly what you'd use on 100,000 tasks.
- **The lingering smell:** a task is still just a `String`, and "done-ness" lives in a *separate* `Set`, so the two can drift out of sync. There's no place to hang a due date, a priority, or an id. Chapter 8 fixes this properly by making each task a real object — a `data class Task` — and the collection a `List<Task>`.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Collection** | An object holding many values (`List`/`Set`/`Map`). |
| **Read-only vs mutable** | Interfaces that expose reading only vs reading + writing. |
| **`List`** | Ordered collection allowing duplicates, indexed from 0. |
| **`Set`** | Unordered collection of unique values; fast membership. |
| **`Map`** | Key→value associations; lookup returns a nullable value. |
| **`filter` / `map`** | Keep matching elements / transform each element. |
| **`reduce` / `fold`** | Collapse a collection to one value (fold takes an initial value). |
| **`groupBy`** | Partition elements into a `Map` by a key function. |
| **Eager** | Operators that compute immediately, allocating a new list per step. |
| **`Sequence`** | A lazy pipeline; elements flow one at a time; terminal ops can short-circuit. |

### What's next

That's Part 1 complete — you can write correct, null-safe Kotlin that computes, decides, iterates, and processes collections. **Part 2 begins with [Ch.8 — Classes & Objects](#chapter-8--classes--objects)**, where the Task Manager's loose `String`s and parallel `Set` finally become a proper `data class Task`, and you learn to design your own types. (Chapter 7 — Null Safety — sits between them, and you've already piloted it.)

[↑ back to top](#chapter-6--collections)


---

## Chapter 7 — Null Safety

> **Level:** Beginner → Intermediate &nbsp;·&nbsp; **Under-the-hood boxes:** Advanced
>
> **Prerequisites:** [Ch.2 — Variables & Data Types](#chapter-2--variables--data-types), [Ch.5 — Functions](#chapter-5--functions), [Ch.6 — Collections](#chapter-6--collections)
>

**Learning objectives** — after this chapter you will be able to:

- Explain *why* a language would build null-tracking into its type system, and what class of bugs it removes.
- Read and write the difference between a nullable type (`String?`) and a non-nullable type (`String`).
- Reach for the right tool for each situation: smart casts, `?.`, `?:`, `as?`, `!!`, `?.let`.
- Handle collections that contain nulls, and tell `List<String?>` apart from `List<String>?`.
- Use `lateinit` and `by lazy` correctly, and know which one fits which problem.
- Work safely across the Java boundary, where Kotlin's guarantees temporarily switch off (*platform types*).
- Understand what null safety actually compiles to on the JVM — boxing, null-check branches, and runtime assertions.

**In this chapter**

- [7.1 The problem: the billion-dollar mistake](#71-the-problem-the-billion-dollar-mistake)
- [7.2 Nullable vs non-nullable types](#72-nullable-vs-non-nullable-types)
- [7.3 The compiler forces you to handle null](#73-the-compiler-forces-you-to-handle-null)
- [7.4 Smart casts: proving non-null with a check](#74-smart-casts-proving-non-null-with-a-check)
- [7.5 The safe-call operator `?.`](#75-the-safe-call-operator)
- [7.6 The Elvis operator `?:`](#76-the-elvis-operator)
- [7.7 The not-null assertion `!!`](#77-the-not-null-assertion)
- [7.8 Safe casts with `as?`](#78-safe-casts-with-as)
- [7.9 Nullable collections and stdlib helpers](#79-nullable-collections-and-stdlib-helpers)
- [7.10 `lateinit` and `by lazy`](#710-lateinit-and-by-lazy)
- [7.11 Crossing the Java boundary: platform types](#711-crossing-the-java-boundary-platform-types)
- [7.12 Nullability and generics](#712-nullability-and-generics)
- [7.13 Under the hood: how null safety works on the JVM](#713-under-the-hood-how-null-safety-works-on-the-jvm)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-null-safe-task-manager) · Glossary · What's next

---

### 7.1 The problem: the billion-dollar mistake

Almost every non-trivial program has to represent the idea of *"there is no value here."* A user hasn't entered their middle name. A database lookup found no matching row. A cache is empty. Somehow the language needs a way to say *"nothing."*

For decades the universal answer was **`null`** — a special reference that points at nothing. It is cheap, it is simple, and it is a trap. The moment you try to *use* a `null` as if it were a real object — call a method on it, read a property from it — the program blows up with a **`NullPointerException`** (NPE). In Java, that crash can happen almost anywhere, because *any* reference can secretly be `null` and the type system says nothing about it.

The man who introduced null references, Tony Hoare, later called it his **"billion-dollar mistake"** — a single design decision that has caused countless crashes, security holes, and wasted debugging hours across the whole industry.

Here is the Java version of the trap:

```java
// Java
String name = findUser(42);   // might return null — the type doesn't warn you
int len = name.length();      // 💥 NullPointerException at runtime if it was null
```

Nothing in `String name` tells you whether `name` can be null. The compiler is happy. You find out it was null only when a real user hits that code path in production.

**Kotlin's core idea:** move this information *into the type system*. A type either promises it can never be null, or it openly admits it might be — and the compiler will not let you ignore the difference. NPEs stop being a runtime surprise and become a compile-time conversation.

> ⚙️ **Under the hood** — This is not achieved by wrapping values in some `Option` box at runtime (the way some languages do). A Kotlin `String` and a Kotlin `String?` are *the same* `java.lang.String` on the JVM. The nullability lives almost entirely in the **compiler** and in metadata, so you get the safety with essentially zero runtime cost. We unpack exactly how in [§7.13](#713-under-the-hood-how-null-safety-works-on-the-jvm).

---

### 7.2 Nullable vs non-nullable types

In Kotlin, every type comes in two flavours:

- **Non-nullable** — the default. `String` means *"a string, guaranteed to be a real string, never null."*
- **Nullable** — written with a trailing `?`. `String?` means *"either a string, or `null`."*

```kotlin
val name: String = "Alice"   // non-nullable: this can never hold null
// name = null               // ❌ compile error: Null can not be a value of a non-null type String

var nickname: String? = "Ali" // nullable: null is a legal value here
nickname = null               // ✅ perfectly fine
```

Think of the `?` as the value's honesty badge. A `String` has *promised* it is never null, so the compiler lets you use it freely. A `String?` has *admitted* it might be null, so the compiler makes you deal with that possibility before you can treat it like a real string.

**The mental model:** `String?` is a slightly *bigger* type than `String`. It contains everything a `String` can be, **plus** the extra value `null`. So a `String` fits into a `String?` (every non-null string is also a "maybe-string"), but a `String?` does **not** fit into a `String` (because it might be the one value — `null` — that a `String` is not allowed to be).

```kotlin
val sure: String = "hello"
val maybe: String? = sure      // ✅ widening: String → String?  is always safe
// val back: String = maybe    // ❌ narrowing: String? → String  needs you to handle null first
```

> ☕ **Coming from Java** — In Java, `String` and a "nullable String" are the same type; the nullability is at best documented with a `@Nullable` annotation that the compiler does not enforce. In Kotlin they are genuinely *different types* with different rules. `String` in Kotlin is closer to a Java `String` that you have personally verified is never null everywhere it is used.

> ⚠️ **Gotcha** — `?` is part of the *type*, not the variable name. `val name: String? = null` declares a nullable String. Writing the `?` in other positions (like `String ?`) is just whitespace and still means the same type, but keep it attached to the type for readability. Also note `String?` and `String` are different types even though they print the same way in error messages if you read too fast.

> ⚙️ **Under the hood** — For reference types like `String`, both `String` and `String?` compile to the exact same JVM type. But for the primitive-backed types this matters a lot: a non-null `Int` compiles to a JVM primitive `int`, while an `Int?` must be able to hold `null`, so it compiles to a **boxed** `java.lang.Integer`. That has a real performance and memory cost — see [§7.13](#713-under-the-hood-how-null-safety-works-on-the-jvm).

---

### 7.3 The compiler forces you to handle null

Once a value is nullable, Kotlin will not let you use it as if it were definitely there:

```kotlin
val nickname: String? = "Ali"
val length = nickname.length   // ❌ compile error:
                               //    Only safe (?.) or non-null asserted (!!.) calls are allowed
                               //    on a nullable receiver of type String?
```

This error message is the whole chapter in one sentence. The compiler is telling you: *"This might be null. Choose how you want to handle that — safely, or by asserting."* The rest of this chapter is the menu of ways to answer that question. Here is the menu at a glance, before we study each in depth:

| Tool | Reads as | Use when |
|------|----------|----------|
| `if (x != null) …` | "if it's there, …" (smart cast) | you want a plain block guarded by a check |
| `x?.foo()` | "call foo if x isn't null, else null" | you want to chain calls and let null flow through |
| `x ?: default` | "x, or else default" | you have a sensible fallback value |
| `x ?: return` / `?: throw` | "x, or else bail out" | absence means you should stop here |
| `x as? Type` | "cast if it really is Type, else null" | the cast might legitimately fail |
| `x!!` | "trust me, it's not null" | you can *prove* it's non-null but the compiler can't |
| `x?.let { … }` | "run this block only if x isn't null" | you want a scope where x is non-null |

---

### 7.4 Smart casts: proving non-null with a check

The most natural way to handle a nullable value is to *check* it. Once you have checked `x != null` inside an `if`, Kotlin is smart enough to know that, inside that branch, `x` cannot be null — so it lets you use it as a non-nullable value. This is called a **smart cast**.

```kotlin
fun printLength(text: String?) {
    if (text != null) {
        // Inside here, the compiler has "smart cast" text from String? to String
        println("Length is ${text.length}")   // no ?. needed
    } else {
        println("No text provided")
    }
}
```

Smart casts also flow through early returns and `&&`/`||`, because the compiler tracks what must be true to reach each point:

```kotlin
fun greet(name: String?) {
    if (name == null) return            // after this line, name is known non-null
    println("Hello, ${name.uppercase()}")  // smart cast: name is String here
}

fun isLongName(name: String?): Boolean {
    // If the left side is false, the right side never runs, so name is non-null there:
    return name != null && name.length > 10
}
```

#### When smart casts stop working

A smart cast is only sound if the compiler can *guarantee* the value won't change between the check and the use. When it can't guarantee that, the smart cast is refused. The classic cases:

```kotlin
var name: String? = "Alice"
val printIt = {
    // ❌ Smart cast to 'String' is impossible, because 'name' is a local variable
    //    that is captured by a changing closure
    if (name != null) println(name.length)
}
```

Because `name` is a mutable `var` captured by a lambda, another call could reassign it to `null` between the check and the `.length`. The compiler cannot prove safety, so it refuses.

> ⚠️ **Gotcha** — The single most common real-world smart-cast failure is a **mutable property** (you'll meet properties in [Ch.8](#chapter-8--classes--objects)). A `var` property could, in principle, be changed by another thread right after your null check, so Kotlin never smart-casts a mutable property. The standard fix is to copy it into a local `val` first:
>
> ```kotlin
> // Won't compile if `config.token` is a `var` property:
> //   if (config.token != null) use(config.token)   // ❌
> val token = config.token          // snapshot into an immutable local
> if (token != null) use(token)     // ✅ local val smart-casts fine
> ```
>
> A `val` with a **custom getter** also can't be smart-cast, because each access might return a different value.

> ⚙️ **Under the hood** — A smart cast is *purely a compile-time convenience*. It generates the ordinary `if (x != null)` bytecode you would have written by hand; there is no runtime cast object and no wrapper. The compiler is just tracking, statement by statement, the narrowest type it can prove for each variable — a process called *control-flow analysis*. The modern **K2 compiler** (Kotlin 2.0+) does this tracking more thoroughly than the old one, so some checks that used to be refused now succeed.

---

### 7.5 The safe-call operator `?.`

Checking with `if` is fine, but it gets verbose when you just want to *reach through* a possibly-null value. The **safe-call operator `?.`** does the null check for you:

```kotlin
val nickname: String? = "Ali"
val length: Int? = nickname?.length
```

Read `nickname?.length` as: *"if `nickname` is not null, give me `nickname.length`; otherwise, the whole expression is `null`."* Note the result type: because the call can produce `null`, `length` is an `Int?`, not an `Int`.

```kotlin
val a: String? = "Kotlin"
val b: String? = null

println(a?.length)   // → 6
println(b?.length)   // → null   (the call is skipped, result is null)
```

#### Chaining safe calls

The real power shows up when you walk a chain of nullable steps. If *any* link is null, the whole chain short-circuits to `null` instead of crashing:

```kotlin
// Each step might be absent. The chain yields the country, or null if any step is missing.
val country: String? = user?.address?.city?.country
```

Without `?.`, that single line would be a nested pyramid of `if (user != null) { if (user.address != null) { … } }`.

#### `?.let { … }` — a scope where the value is non-null

Pairing `?.` with the `let` scope function (covered in depth in [Ch.14](#chapter-14--scope-functions)) gives you a block that runs **only** when the value is present, with the value available as `it`:

```kotlin
val email: String? = readEmail()

email?.let {
    // This block runs only if email != null. Inside, `it` is a non-null String.
    println("Sending welcome mail to ${it.trim().lowercase()}")
}
```

> 💡 **Idiom** — `value?.let { … }` is the idiomatic Kotlin replacement for `if (value != null) { … }` when you want a small scoped block and you don't need an `else`. Prefer it over the not-null assertion `!!` (next-but-one section).

> ⚙️ **Under the hood** — `a?.b` compiles to roughly `if (a != null) a.b else null`. It is exactly the hand-written null check, generated for you. There is no magic and no runtime helper object — which is why safe calls are effectively free.

---

### 7.6 The Elvis operator `?:`

Very often "the value might be null" really means "…and if it is, use this default instead." That is the job of the **Elvis operator `?:`** (named because `?:` sideways looks like Elvis Presley's hair and eyes).

```kotlin
val nickname: String? = null
val display: String = nickname ?: "Anonymous"
println(display)   // → Anonymous
```

Read `a ?: b` as: *"a, but if a is null, then b."* The beauty is the result type: since the fallback `b` is a non-null `String`, the whole expression is a non-null `String`. Elvis is how you *turn a nullable into a non-nullable* by supplying a default.

It pairs perfectly with `?.`:

```kotlin
val name: String? = null
val length: Int = name?.length ?: 0   // "length of name, or 0 if name is null"
println(length)   // → 0
```

#### Elvis for early exit: `?: return` and `?: throw`

Because the right-hand side of `?:` is just an expression, and in Kotlin `return` and `throw` are expressions too, you can use Elvis to *bail out* when a value is missing. This is one of the most useful patterns in the whole language:

```kotlin
fun sendReceipt(order: Order?) {
    val realOrder = order ?: return           // if order is null, stop here
    // from here down, realOrder is a non-null Order
    println("Emailing receipt for order ${realOrder.id}")
}

fun requireName(name: String?): String {
    return name ?: throw IllegalArgumentException("name is required")
}
```

> 💡 **Idiom** — `val x = maybe ?: return` (or `?: throw …`) at the top of a function is the idiomatic "guard clause." It handles the null case once, up front, and leaves the rest of the function working with a clean non-nullable value. This reads far better than nesting the whole function body inside an `if`.

> ⚠️ **Gotcha** — Watch the precedence when mixing Elvis with other operators. `a ?: b + c` parses as `a ?: (b + c)`, and `a + b ?: c` parses as `(a + b) ?: c`. When in doubt, add parentheses — they cost nothing and remove the guesswork.

---

### 7.7 The not-null assertion `!!`

Sometimes *you* know a value is not null even though the compiler can't prove it. The **not-null assertion operator `!!`** lets you override the compiler: `x!!` evaluates to `x` as a non-null value — but if `x` turns out to be null at runtime, it throws a `NullPointerException` on the spot.

```kotlin
val name: String? = "Alice"
val length: Int = name!!.length   // "I promise this isn't null" → 5
```

In effect, `!!` converts a compile-time guarantee you don't have into a runtime crash you accept responsibility for.

> ⚠️ **Gotcha** — `!!` is a code smell in the vast majority of cases. Every `!!` is a little landmine: it says "I've decided this can't be null," and the day that assumption is wrong, you get exactly the `NullPointerException` that this whole chapter exists to prevent. Reach for `?.`, `?:`, `?.let`, or a smart-casting `if` first. Legitimate uses of `!!` are rare — for example, right after you've *just* put a value into a map and you know the very next `get` will find it.

> ⚙️ **Under the hood** — `x!!` compiles to a call into the Kotlin runtime that checks for null and throws if needed — conceptually `x ?: throw NullPointerException(...)`. On modern Kotlin the thrown exception is a `NullPointerException` whose message points at the expression that failed, which is why you'll sometimes see messages that name the exact property or call. The important part: the crash happens **at the `!!`**, not later — so at least it fails fast, at the place you made the promise.

> 📝 **Micro-exercise** — Rewrite `val len = user!!.name!!.length` so that a missing `user` or a missing `name` yields `0` instead of throwing.
>
> <details><summary>Show solution</summary>
>
> ```kotlin
> val len = user?.name?.length ?: 0
> ```
>
> Each `?.` short-circuits to `null` if its receiver is null, and the trailing `?: 0` supplies the default. No exception is ever thrown, and `len` is a clean non-null `Int`. This is almost always what you actually wanted when you were tempted to write `!!`.
>
> </details>

---

### 7.8 Safe casts with `as?`

A normal cast with `as` throws a `ClassCastException` if the object isn't of the expected type:

```kotlin
val obj: Any = "hello"
val n = obj as Int   // 💥 ClassCastException at runtime: String cannot be cast to Int
```

The **safe cast operator `as?`** instead returns `null` when the cast doesn't apply, turning a potential crash into a nullable you can handle:

```kotlin
val obj: Any = "hello"

val asString: String? = obj as? String   // → "hello"  (cast succeeds)
val asInt: Int? = obj as? Int             // → null      (cast fails, no crash)
```

This composes naturally with Elvis to give a typed default:

```kotlin
fun describe(value: Any): String {
    val text = value as? String ?: "not a string"
    return "Text: $text"
}

println(describe("hi"))   // → Text: hi
println(describe(42))     // → Text: not a string
```

> ⚙️ **Under the hood** — `x as? Type` compiles to the JVM `instanceof` check plus a cast: *"if x is a Type, cast it; otherwise produce null."* It is the safe, branch-y version of the raw `checkcast` bytecode that `as` emits.

---

### 7.9 Nullable collections and stdlib helpers

There are **two different things** the `?` can attach to when a collection is involved, and mixing them up is a classic beginner bug:

```kotlin
val a: List<String?>   // a non-null list, whose ELEMENTS may each be null
val b: List<String>?   // a nullable list (maybe null), whose elements are all non-null
val c: List<String?>?  // a nullable list whose elements may each be null
```

Read the `?` from the inside out: `List<String?>` — the `?` hugs `String`, so it's the *elements* that are nullable. `List<String>?` — the `?` is outside the `List<…>`, so it's the *whole list* that might be null.

#### Getting values out is nullable by design

Map lookups and "safe" accessors return nullable on purpose, which is the standard library nudging you toward null safety:

```kotlin
val ages = mapOf("Alice" to 30, "Bob" to 25)

val a: Int? = ages["Alice"]     // → 30
val c: Int? = ages["Carol"]     // → null   (missing key → null, not a crash)

val list = listOf(10, 20, 30)
val first: Int? = list.firstOrNull()   // → 10
val tenth: Int? = list.getOrNull(9)    // → null   (out of range → null, not an exception)
```

> ⚠️ **Gotcha** — `map[key]` returns a nullable `V?`. So `ages["Alice"] + 1` does **not** compile — you must handle the null first: `(ages["Alice"] ?: 0) + 1`. Prefer the `…OrNull` accessors (`firstOrNull`, `getOrNull`, `singleOrNull`) over the throwing ones (`first`, `get`, `single`) whenever "not found" is a normal, expected outcome rather than a bug.

#### Helpers built for nullables

The standard library has a whole family of functions designed to make nullable-handling terse and safe:

```kotlin
// Drop nulls from a collection of nullable elements:
val withNulls: List<String?> = listOf("a", null, "b", null, "c")
val clean: List<String> = withNulls.filterNotNull()
println(clean)   // → [a, b, c]   (note the result type is List<String>, no more ?)

// Transform AND drop nulls in one pass:
val inputs = listOf("1", "two", "3", "four")
val numbers: List<Int> = inputs.mapNotNull { it.toIntOrNull() }
println(numbers)   // → [1, 3]

// Convenience checks and conversions on a nullable string:
val s: String? = null
println(s.isNullOrEmpty())   // → true   (callable even though s is null!)
println(s.isNullOrBlank())   // → true
println(s.orEmpty())         // → ""     (null becomes empty string)
```

Notice `s.isNullOrEmpty()` is called directly on a `String?` *without* a `?.` — these are **extension functions declared on the nullable type itself** (you'll build your own in [Ch.11](#chapter-11--extension-functions--properties)), so they can safely inspect the null case internally.

---

### 7.10 `lateinit` and `by lazy`

Sometimes a value is genuinely non-null in spirit, but you can't provide it at construction time — think of a dependency injected later, or an expensive object you only want to build on demand. Declaring it `String?` and then peppering the code with `?.` and `!!` would be dishonest: the value is *conceptually* always there once set-up finishes. Kotlin gives you two cleaner tools.

#### `lateinit` — "I'll set this before I use it"

`lateinit var` lets you declare a **non-nullable** `var` without an initial value, promising the compiler you'll assign it before anyone reads it:

```kotlin
lateinit var database: Database   // non-null type, but no value yet

fun setUp() {
    database = connectToDatabase()  // assigned here
}

fun query() {
    database.runQuery()             // used as a plain non-null Database — no ?. or !!
}
```

If you read a `lateinit` property before it has been assigned, you get an `UninitializedPropertyAccessException` — a clear, specific error, not a vague NPE. You can check whether it's been set with the `.isInitialized` reference:

```kotlin
fun queryIfReady() {
    if (::database.isInitialized) {   // note the :: reference to the property
        database.runQuery()
    }
}
```

`lateinit` has firm restrictions, and knowing them prevents confusing errors:

- Only for `var`, never `val`.
- Only for **non-null reference types** — *not* primitives like `Int`, `Double`, `Boolean` (they can't represent "unset").
- The property must have no custom getter/setter.
- `.isInitialized` is only accessible via a property reference from inside the declaring scope.

#### `by lazy` — "compute this the first time it's asked for"

`by lazy { … }` is for a **`val`** that should be computed *once*, lazily, on first access, then cached (property delegation is covered fully in [Ch.13](#chapter-13--delegated-properties)):

```kotlin
val config: Config by lazy {
    println("Loading config...")   // runs at most once, on first access
    loadConfigFromDisk()
}

fun useIt() {
    println(config.timeout)  // first access here: prints "Loading config..." then the value
    println(config.timeout)  // second access: cached, no reload
}
```

> 💡 **Idiom** — Choosing between them: use **`by lazy`** when the value is computed *by you*, exactly once, and never changes (a `val`). Use **`lateinit`** when the value is *handed to you later* from outside (a `var` set by a framework, test harness, or DI container). If the type is a primitive and you need "not set yet," neither applies — use a nullable (`Int?`) with `?:`.

> ⚠️ **Gotcha** — `lateinit` silences the compiler, not reality. If a code path reads the property before `setUp()` runs, you'll get `UninitializedPropertyAccessException` at runtime. `lateinit` trades "nullable everywhere" for "one clear crash if I break my own promise" — use it only when you can keep that promise.

---

### 7.11 Crossing the Java boundary: platform types

Kotlin's null guarantees are airtight *within Kotlin*. But the moment you call **Java** code, the compiler faces a problem: Java types don't carry Kotlin's non-null/nullable distinction. A Java method returning `String` might return `null` or might not — Java simply doesn't say.

Rather than force you to treat *every* Java value as nullable (which would drown you in `?.`), Kotlin introduces a pragmatic compromise: the **platform type**, written `String!` in error messages and IDE hints (you never type the `!` yourself).

```kotlin
// Suppose Java has:  public String getName() { ... }   // could be null, doesn't say

val name = javaObject.name    // type is String!  — a "platform type"

val len1 = name.length        // allowed: Kotlin trusts you (may NPE at runtime if null)
val len2 = name?.length ?: 0  // also allowed: you chose to treat it as nullable — safe
```

A platform type is Kotlin saying: *"I don't know if this is null. I'll let you decide how careful to be — but if you treat it as non-null and it turns out to be null, that's on you (runtime NPE)."* It's a deliberate hole in the safety net, sized exactly to fit Java interop.

#### Making the boundary safer

You have two good options at the boundary:

1. **Declare the type explicitly** as you receive the value, which forces the compiler to check right there:

   ```kotlin
   val safe: String? = javaObject.name   // you chose nullable: fully safe from here on
   // val strict: String = javaObject.name // you chose non-null: compiler inserts a null check;
   //                                       // throws immediately at this line if it was null
   ```

2. **Annotate the Java side.** If the Java code uses nullability annotations (`@Nullable` / `@NotNull`, e.g. from JetBrains, JSpecify, or Android's `androidx.annotation`), Kotlin *reads* them and treats the value as a proper `String?` or `String` — no platform type, full safety.

   ```java
   // Java, annotated:
   public @Nullable String getMiddleName() { ... }   // Kotlin sees this as String?
   public @NotNull  String getId()         { ... }   // Kotlin sees this as String
   ```

> 💡 **Idiom** — When consuming an un-annotated Java API, pin the nullability the instant the value crosses into Kotlin by writing an explicit `String?` (or `String`) type on the variable. One decision at the boundary beats scattered `!!`s everywhere downstream.

> ⚙️ **Under the hood** — Platform types are the compiler *relaxing* its checks, not adding any runtime behaviour. If you assign a platform value into an explicitly non-null Kotlin type, the compiler inserts an *intrinsic null check* (`Intrinsics.checkNotNullExpressionValue`) at that assignment, so a smuggled-in null fails fast right there instead of corrupting data three functions later.

---

### 7.12 Nullability and generics

Generics (the full story is [Ch.12](#chapter-12--generics)) interact with nullability in a way that trips people up, so it's worth a focused look.

A bare type parameter `T` is implicitly **nullable-capable**: unless you constrain it, `T` could be substituted with a nullable type like `String?`. That means a value of type `T` might already be nullable, and `T?` means "T, or additionally null."

```kotlin
fun <T> firstOrNull(items: List<T>): T? =
    if (items.isEmpty()) null else items[0]
```

To *require* that `T` itself is non-null, add `Any` as an upper bound:

```kotlin
fun <T : Any> firstOrThrow(items: List<T>): T =
    if (items.isEmpty()) throw NoSuchElementException() else items[0]
// Here T can only be a non-null type, so the return T is genuinely non-null.
```

#### Definitely non-null types: `T & Any`

Kotlin 1.7 added a way to say "the non-null version of whatever `T` is" — the **definitely non-null type** `T & Any`. It's mainly useful when you take a `T?` and want to return a guaranteed-non-null result:

```kotlin
fun <T> orDefault(value: T?, default: T & Any): T & Any =
    value ?: default
```

Read `T & Any` as *"T, intersected with the always-non-null type Any"* — i.e. T with its null possibility stripped away. You'll mostly *encounter* this in library signatures rather than write it yourself, but recognising it removes a moment of confusion later.

---

### 7.13 Under the hood: how null safety works on the JVM

This is the section that turns "I can use `?.`" into "I understand what `?.` *is*." Everything above is powered by three simple mechanisms.

**1. Nullability is compiler metadata, not a runtime wrapper.**
A `String` and a `String?` are the *same* `java.lang.String` at runtime. Kotlin records the nullability in the `@Metadata` attached to compiled classes (and, for public API, via annotations on parameters/returns). Your safety comes from the compiler refusing bad code — not from any per-value overhead. This is why null safety is "free" for reference types.

**2. For primitives, nullability forces boxing.**
This one has a real cost. A non-null `Int` is a JVM `int` (a raw 32-bit value on the stack). But `null` is not a legal `int`, so an `Int?` must be represented as a **boxed** `java.lang.Integer` object on the heap:

```kotlin
val a: Int = 5     // JVM: primitive int, no allocation
val b: Int? = 5    // JVM: java.lang.Integer.valueOf(5) — a heap object
```

In a hot loop, a million `Int?` values means a million boxed objects and extra garbage collection. This is why performance-sensitive Kotlin avoids nullable primitives where it can.

**3. The operators compile to plain null checks and assertions.**

| You write | Compiler emits (conceptually) |
|-----------|-------------------------------|
| `a?.b` | `if (a != null) a.b else null` |
| `a ?: b` | `if (a != null) a else b` |
| `a!!` | `a ?: throw NullPointerException(...)` (fails at this spot) |
| `a as? T` | `if (a is T) a else null` |
| assigning a platform value to a non-null type | inserts `Intrinsics.checkNotNull…` — fail-fast |

> ⚙️ **Under the hood** — Put together, the philosophy is: **push the check as early as possible, and make it cheap.** The compiler proves what it can at compile time (smart casts, non-null types), inserts a tiny fail-fast check exactly where an unproven value enters (`!!`, platform boundaries), and pays a heap cost only where it truly must (boxed nullable primitives). Null safety in Kotlin is less a runtime feature than a compile-time discipline with a few well-placed runtime guards.

---

### Summary

- Kotlin encodes "can this be null?" **in the type**: `String` never null, `String?` maybe null. This turns most NPEs from runtime surprises into compile-time errors.
- You cannot use a nullable value directly; you must choose a handling tool: a **smart-casting `if`**, safe call **`?.`**, Elvis **`?:`**, safe cast **`as?`**, scoped **`?.let`**, or the last-resort assertion **`!!`**.
- **`?:`** is how you convert nullable → non-null by supplying a default; **`?: return`/`?: throw`** make clean guard clauses.
- Prefer `?.`, `?:`, and `?.let` over **`!!`**. Every `!!` is a potential NPE you signed off on.
- Distinguish `List<String?>` (nullable *elements*) from `List<String>?` (nullable *list*). Prefer `…OrNull` accessors; clean nullables with `filterNotNull` / `mapNotNull`.
- Use **`lateinit var`** for non-null values supplied later from outside, and **`by lazy`** for a `val` computed once on first use. Neither works for nullable primitives.
- Across the **Java boundary**, values become **platform types** (`String!`) where safety is relaxed; pin them to an explicit `String?`/`String` immediately, or rely on Java `@Nullable`/`@NotNull` annotations.
- Under the hood: nullability is mostly compiler metadata (free for references), forces **boxing** for nullable primitives, and the operators compile to ordinary null-check branches and fail-fast assertions.

### Self-check quiz

Try to answer before expanding.

1. What is the difference between `List<Int?>` and `List<Int>?`?
   <details><summary>Answer</summary>`List<Int?>` is a non-null list whose elements may each be null. `List<Int>?` is a list variable that itself may be null, but whose elements (if the list exists) are all non-null.</details>

2. Why does `map[key]` return a nullable type?
   <details><summary>Answer</summary>Because the key might be absent. Returning `V?` (with `null` for "not found") lets the type system force you to handle the missing-key case, instead of throwing.</details>

3. Given `val x: String? = null`, what does `x?.length ?: -1` evaluate to, and what is its type?
   <details><summary>Answer</summary>`-1`, of type `Int`. The `?.` yields `null` because `x` is null, then Elvis substitutes `-1`; since the fallback is a non-null `Int`, the whole expression is a non-null `Int`.</details>

4. You have a `var` **property** `token: String?`. Why won't `if (token != null) use(token)` smart-cast, and how do you fix it?
   <details><summary>Answer</summary>A mutable property could be changed (e.g. by another thread) between the check and the use, so Kotlin refuses the smart cast. Fix: snapshot into a local `val` first — `val t = token; if (t != null) use(t)`.</details>

5. When would you legitimately prefer `lateinit` over a nullable `var`?
   <details><summary>Answer</summary>When the value is conceptually always present once initialization finishes, is a non-null reference type, and is supplied from outside after construction (e.g. by a framework or DI). It lets you use the value as plain non-null instead of littering `?.`/`!!` everywhere, and gives a clear `UninitializedPropertyAccessException` if you break the promise.</details>

### Exercises

Work them in order; each builds a little on the last. Try before opening the solution.

**Exercise 7.1 — Safe parsing (guided).** Write `fun parsePositive(input: String?): Int?` that returns the number if `input` is a valid integer greater than zero, and `null` otherwise. Use safe calls and `toIntOrNull()`; do not use `try`/`catch` or `!!`.

<details><summary>Show solution</summary>

```kotlin
fun parsePositive(input: String?): Int? {
    val n = input?.trim()?.toIntOrNull() ?: return null
    return if (n > 0) n else null
}

fun main() {
    println(parsePositive("  42 "))  // → 42
    println(parsePositive("-3"))     // → null
    println(parsePositive("abc"))    // → null
    println(parsePositive(null))     // → null
}
```

**Why this works:** `input?.trim()?.toIntOrNull()` short-circuits to `null` if `input` is null *or* if it isn't a valid integer — no exception is ever thrown. The `?: return null` is a guard clause that also **smart-casts** `n` to a non-null `Int` for the rest of the function, so `n > 0` compiles cleanly. Returning `null` for non-positive keeps the whole function honest about "no valid value."

</details>

**Exercise 7.2 — Clean and summarise.** Given `val raw: List<String?> = listOf("5", null, "12", "oops", "7")`, produce the **sum** of all entries that are valid integers (here: 5 + 12 + 7 = 24), in a single expression chain.

<details><summary>Show solution</summary>

```kotlin
val raw: List<String?> = listOf("5", null, "12", "oops", "7")

val total: Int = raw.mapNotNull { it?.toIntOrNull() }.sum()
println(total)   // → 24
```

**Why this works:** `mapNotNull` runs the lambda on each element and keeps only the non-null results. Inside, `it` is a `String?`, so `it?.toIntOrNull()` handles both the null element (`null`) and the non-numeric `"oops"` (also `null`); both are dropped. What survives is a `List<Int>`, so `.sum()` returns a plain non-null `Int`. One pass, fully null-safe.

</details>

**Exercise 7.3 — Challenge: safest lookup.** You are given `val phoneBook: Map<String, String> = mapOf("alice" to "555-1234")`. Write `fun callInfo(name: String?): String` that returns `"Calling <name> at <number>"` when the (case-insensitive) name is found, and a helpful message otherwise — for a null name, `"No name given"`; for an unknown name, `"<name> is not in the phone book"`. Use no `!!` anywhere.

<details><summary>Show solution</summary>

```kotlin
val phoneBook: Map<String, String> = mapOf("alice" to "555-1234")

fun callInfo(name: String?): String {
    val key = name?.trim()?.lowercase() ?: return "No name given"
    val number = phoneBook[key] ?: return "$name is not in the phone book"
    return "Calling $name at $number"
}

fun main() {
    println(callInfo("  Alice "))  // → Calling   Alice  at 555-1234
    println(callInfo("bob"))       // → bob is not in the phone book
    println(callInfo(null))        // → No name given
}
```

**Why this works:** Two guard clauses handle the two "absent" cases up front. `name?.trim()?.lowercase() ?: return …` deals with a null name *and* normalises the key in one line (and smart-casts nothing is needed afterward because `key` is already non-null). `phoneBook[key] ?: return …` handles the missing-key case using the nullable that map lookup hands us. By the last line, both `name`-derived data and `number` are known-present, so the happy path reads cleanly with zero `!!`.

</details>

### Chapter project: a null-safe Task Manager

> 🛠️ **Chapter Project** — This is the first installment of the **running Task Manager** we grow throughout the book. **Builds on:** Ch.1–6 (basics, control flow, functions, collections) and this chapter (null safety). **Uses no classes yet** — you meet those in Ch.8, and we'll refactor `Task` into a proper type then. For now a task is just data in maps.

**Goal.** Build a tiny in-memory task manager whose public functions *never* throw a `NullPointerException`, no matter what the caller passes — including `null` and garbage input.

**Model.** Represent tasks with two collections keyed by an integer id:

- `titles: MutableMap<Int, String>` — id → task title
- `done: MutableSet<Int>` — the ids that are completed

**Requirements.**

1. `addTask(id: Int, title: String)` — store the title.
2. `parseId(input: String?): Int?` — safely turn possibly-null, possibly-garbage user input into an id, or `null`.
3. `titleOf(id: Int): String?` — the title for an id, or `null` if there's no such task.
4. `describe(input: String?): String` — take *raw user input*, and return either `"#<id>: <title> [done|todo]"` or a helpful message for missing/invalid input. No `!!` anywhere.
5. `complete(input: String?): Boolean` — mark a task done from raw input; return whether it actually marked something.

<details><summary>Show reference solution + commentary</summary>

```kotlin
val titles: MutableMap<Int, String> = mutableMapOf()
val done: MutableSet<Int> = mutableSetOf()

fun addTask(id: Int, title: String) {
    titles[id] = title
}

fun parseId(input: String?): Int? =
    input?.trim()?.toIntOrNull()

fun titleOf(id: Int): String? =
    titles[id]                     // Map.get returns String? — nullability handed to us

fun describe(input: String?): String {
    val id = parseId(input) ?: return "Please enter a valid task number."
    val title = titleOf(id) ?: return "No task #$id exists."
    val status = if (id in done) "done" else "todo"
    return "#$id: $title [$status]"
}

fun complete(input: String?): Boolean {
    val id = parseId(input) ?: return false
    if (titleOf(id) == null) return false   // don't complete a task that doesn't exist
    return done.add(id)                     // Set.add returns false if it was already there
}

fun main() {
    addTask(1, "Write the pilot chapter")
    addTask(2, "Review with Shayan")

    println(describe("1"))        // → #1: Write the pilot chapter [todo]
    println(complete(" 1 "))      // → true
    println(describe("1"))        // → #1: Write the pilot chapter [done]
    println(complete("1"))        // → false   (already done)
    println(describe("99"))       // → No task #99 exists.
    println(describe("abc"))      // → Please enter a valid task number.
    println(describe(null))       // → Please enter a valid task number.
}
```

**Commentary.**

- **Every entry point that can fail begins with a guard clause.** `parseId(input) ?: return …` collapses "null input," "blank input," and "non-numeric input" into a single, honest early exit — and smart-casts `id` to a non-null `Int` for the rest of the function.
- **We never fight the standard library's nullability; we use it.** `titles[id]` *returns* `String?`, and `titleOf` simply passes that truth along. Callers then handle it with `?:`.
- **No `!!` appears anywhere.** Each place the compiler warned "this might be null," we answered with a default, an early return, or an explicit check — which is exactly the discipline this chapter teaches.
- **`done.add(id)` returning `Boolean` gives `complete` its answer for free** — `Set.add` reports whether the element was newly added, so "was it already done?" needs no extra lookup.

**Forward look (Ch.8+):** those two parallel collections and the string-typed status are a smell we'll fix once we have classes. A `data class Task(val id: Int, val title: String, val done: Boolean)` will replace the maps, `equals`/`copy` will come for free, and the null-safety habits you built here will carry straight over.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **NullPointerException (NPE)** | Runtime error from using a null reference as if it held a value. |
| **Nullable type** (`T?`) | A type whose values may be `null`. |
| **Non-nullable type** (`T`) | A type guaranteed never to be `null`; the Kotlin default. |
| **Smart cast** | Compiler automatically narrowing a nullable to non-null inside a scope where a check proves it can't be null. |
| **Safe call** (`?.`) | Call/access that yields `null` instead of executing when the receiver is null. |
| **Elvis operator** (`?:`) | Supplies a fallback value when the left side is null. |
| **Not-null assertion** (`!!`) | Overrides the compiler; throws NPE at runtime if the value is null. |
| **Safe cast** (`as?`) | Cast that yields `null` instead of throwing when the type doesn't match. |
| **`lateinit`** | A non-null `var` you promise to assign before first use. |
| **`by lazy`** | A `val` computed once on first access, then cached. |
| **Platform type** (`T!`) | A type from Java whose nullability is unknown; safety checks are relaxed. |
| **Definitely non-null type** (`T & Any`) | The non-null form of a generic type parameter `T`. |
| **Boxing** | Representing a primitive (e.g. `int`) as a heap object (e.g. `Integer`); required for nullable primitives. |

### What's next

You can now model "maybe absent" honestly and handle it without crashes — a habit that pays off in every chapter after this. Next, **[Ch.8 — Classes and Objects](#chapter-8--classes--objects)** gives tasks a real type, and you'll see null safety combine with constructors, properties, and data classes. The `?.`, `?:`, and guard-clause reflexes you built here don't change — they just get more to work with.

[↑ back to top](#chapter-7--null-safety)


---

## Chapter 8 — Classes & Objects

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.6 — Collections](#chapter-6--collections), [Ch.7 — Null Safety](#chapter-7--null-safety)

**Learning objectives** — after this chapter you will be able to:

- Define classes with primary constructors, `init` blocks, and secondary constructors.
- Write properties with custom getters/setters and understand the backing `field`.
- Use `data class` for models and know exactly what it generates for you.
- Control visibility, and validate construction with `require`/`check`.

**In this chapter**

- [8.1 Why classes?](#81-why-classes)
- [8.2 The primary constructor](#82-the-primary-constructor)
- [8.3 `init` blocks and initialization order](#83-init-blocks-and-initialization-order)
- [8.4 Secondary constructors](#84-secondary-constructors)
- [8.5 Properties: getters, setters, and `field`](#85-properties-getters-setters-and-field)
- [8.6 Visibility modifiers](#86-visibility-modifiers)
- [8.7 Data classes](#87-data-classes)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-the-task-manager-grows-a-domain) · Glossary · What's next

---

### 8.1 Why classes?

By the end of Chapter 6 the Task Manager had a real problem: a task was a bare `String` title, its done-state lived in a *separate* `Set`, and there was nowhere to put an id, a due date, or a priority. Three facts about one thing, scattered across three places, free to drift apart.

A **class** solves this. It's a blueprint that bundles **data** (properties) and **behaviour** (functions, here called *methods*) into a single named type. An **object** is a concrete instance made from that blueprint.

```kotlin
class Person {
    var name: String = ""
    var age: Int = 0

    fun introduce() {
        println("I'm $name, and I'm $age years old")
    }
}

fun main() {
    val alice = Person()      // create an instance — note: no `new` keyword
    alice.name = "Alice"
    alice.age = 30
    alice.introduce()         // → I'm Alice, and I'm 30 years old
}
```

> ☕ **Coming from Java** — You create an instance by calling the class like a function: `Person()`, **not** `new Person()`. Kotlin has no `new` keyword. Otherwise the mental model — data + methods bundled into a type — is the same OOP you already know.

### 8.2 The primary constructor

Setting each property after construction (as above) is clumsy and leaves the object briefly half-built. The **primary constructor** lets you require the data up front, right in the class header:

```kotlin
class Person(val name: String, var age: Int) {
    fun introduce() {
        println("I'm $name, and I'm $age years old")
    }
}

fun main() {
    val alice = Person("Alice", 30)   // name and age supplied at construction
    alice.introduce()
    alice.age = 31                    // age is `var`, so it can change
    // alice.name = "Bob"             // ❌ name is `val` — read-only
}
```

That header `(val name: String, var age: Int)` does a remarkable amount in one line: it declares two constructor parameters **and** turns them into properties of the class. `val` makes a read-only property; `var` a mutable one. If you write a parameter with *neither* `val` nor `var`, it's just a constructor argument — usable during initialization but *not* kept as a property.

```kotlin
class Circle(radius: Double) {          // `radius` has no val/var — it's constructor-only
    val area = 3.14159 * radius * radius  // used here, but `radius` isn't stored
}
```

### 8.3 `init` blocks and initialization order

The primary constructor has no body of its own. When you need to run setup logic — validation, logging, derived state — you put it in an **`init` block**:

```kotlin
class Person(val name: String, var age: Int) {
    init {
        require(age >= 0) { "Age cannot be negative, was $age" }
        println("Created person: $name")
    }
}
```

`require(condition) { message }` throws an `IllegalArgumentException` with your message if the condition is false — the idiomatic way to reject bad constructor arguments (more in Chapter 16).

Initialization runs **top to bottom** in declaration order: property initializers and `init` blocks execute in the order they appear. This matters when one depends on another:

```kotlin
class Demo {
    val a = "A".also { println("init a") }
    init { println("init block 1") }
    val b = "B".also { println("init b") }
    init { println("init block 2") }
}
// Creating Demo() prints, in order:
// init a
// init block 1
// init b
// init block 2
```

### 8.4 Secondary constructors

When you need an *alternative* way to construct an object, add a **secondary constructor** with the `constructor` keyword. It must delegate to the primary one via `this(...)`:

```kotlin
class Person(val name: String, var age: Int) {
    var email: String = ""

    // An alternative constructor that also sets email
    constructor(name: String, age: Int, email: String) : this(name, age) {
        this.email = email
    }
}

val bob = Person("Bob", 25, "bob@example.com")
```

> 💡 **Idiom** — In Kotlin you need secondary constructors far less often than in Java, because **default arguments** (Chapter 5) usually replace them. Instead of two constructors, one with an extra parameter, write one primary constructor with a default: `class Person(val name: String, var age: Int, var email: String = "")`. Reach for a secondary constructor only when the alternative genuinely needs *different logic*, not just different arguments.

### 8.5 Properties: getters, setters, and `field`

A **property** looks like a field but is really a getter (and, for `var`, a setter) in disguise. You can supply *custom* accessors. A **computed property** has a custom getter and stores nothing:

```kotlin
class Rectangle(val width: Int, val height: Int) {
    val area: Int
        get() = width * height   // recomputed on every access; no stored value
}

val r = Rectangle(3, 4)
println(r.area)   // → 12
```

A custom setter can validate or transform on assignment. Inside an accessor, the special identifier **`field`** refers to the property's **backing field** — the actual storage — letting you intercept reads and writes without infinite recursion:

```kotlin
class User {
    var name: String = ""
        set(value) {
            field = value.trim()   // store the trimmed value; `field` is the storage
        }
}

val u = User()
u.name = "   Alice   "
println("[${u.name}]")   // → [Alice]
```

> ⚙️ **Under the hood** — Every property is compiled to a private backing field plus a `getX()`/`setX()` method pair (that's how Java sees them, Chapter 18). A **computed** property like `area` has **no backing field at all** — the compiler omits it because the getter never touches `field`; the value is calculated fresh each call. Referring to `field` is the signal that says "I want real storage here."

> ⚠️ **Gotcha** — Never write `name = value` inside `name`'s own setter (or `return name` inside its getter). That calls the setter/getter again — infinite recursion → `StackOverflowError`. Use `field` to touch the storage directly.

### 8.6 Visibility modifiers

Kotlin has four visibility levels for classes, functions, and properties:

- **`public`** (the default): visible everywhere.
- **`private`**: visible only inside the declaring class (or file, for top-level declarations).
- **`protected`**: like `private`, but also visible to subclasses (Chapter 9).
- **`internal`**: visible everywhere in the same **module** (a set of files compiled together).

```kotlin
class BankAccount(private var balance: Double) {
    fun deposit(amount: Double) {
        require(amount > 0) { "Deposit must be positive" }
        balance += amount             // accessible: same class
    }
    fun balance(): Double = balance   // controlled read access
}

val acc = BankAccount(100.0)
acc.deposit(50.0)
// acc.balance = 0.0     // ❌ balance is private — can't be tampered with from outside
println(acc.balance())   // → 150.0
```

> 💡 **Idiom** — Make mutable state `private` and expose it through controlled methods or read-only properties. This is **encapsulation**: the object guards its own invariants (here, that a balance is only changed through valid operations), so no outside code can put it into an illegal state.

### 8.7 Data classes

A huge share of the classes you write exist just to *hold data* — a task, a user, a coordinate. For these, Kotlin offers the **`data class`**, which auto-generates the tedious members you'd otherwise write by hand:

```kotlin
data class User(val name: String, val age: Int, val email: String)

fun main() {
    val u1 = User("Alice", 25, "alice@example.com")
    val u2 = User("Alice", 25, "alice@example.com")

    println(u1)              // → User(name=Alice, age=25, email=alice@example.com)   [toString]
    println(u1 == u2)        // → true    [structural equals — same content]
    println(u1.hashCode() == u2.hashCode())  // → true

    val u3 = u1.copy(age = 26)   // copy with one field changed
    println(u3)                   // → User(name=Alice, age=26, email=alice@example.com)

    val (name, age, email) = u1   // destructuring, via generated componentN()
    println("$name is $age")      // → Alice is 25
}
```

From `data class User(...)` the compiler generates:

- **`equals()`** / **`hashCode()`** — structural, based on the primary-constructor properties. This is why `u1 == u2` is `true` and why data classes work correctly as `Set` elements and `Map` keys.
- **`toString()`** — the readable `User(name=Alice, …)` form.
- **`copy(...)`** — make a modified duplicate, changing only the fields you name. Essential for working with immutable data.
- **`component1()`, `component2()`, …** — enabling destructuring `val (a, b) = user`.

> ☕ **Coming from Java** — A `data class` is close to a Java **`record`**, but it also gives you `copy()` (records don't) and works seamlessly with Kotlin's immutability idioms. In pre-record Java, replicating one data class meant dozens of lines of `equals`/`hashCode`/`toString`/getters — all of which the compiler now writes and keeps in sync for you.

> ⚠️ **Gotcha — only the primary constructor counts.** The generated `equals`/`hashCode`/`toString`/`copy` use *only* the properties declared **in the primary constructor**. A property declared in the class *body* is ignored by all of them:
> ```kotlin
> data class Item(val id: Int) {
>     var note: String = ""   // NOT part of equals/hashCode/toString/copy
> }
> val x = Item(1).apply { note = "hello" }
> val y = Item(1).apply { note = "world" }
> println(x == y)   // → true  (notes differ, but only `id` is compared!)
> ```
> Put every property that defines the object's identity in the primary constructor.

> ⚠️ **Gotcha — `copy` is shallow, and mutable data is dangerous.** `copy()` copies references, not deep structures — a copied list is the *same* list object. And a `data class` with `var` properties (or holding mutable collections) can change its own `hashCode` after being placed in a `Set`/`Map` key, corrupting the collection. **Prefer `val` properties and immutable data** in data classes; model change with `copy()`, not mutation.

---

### Summary

- A **class** bundles data (properties) and behaviour (methods); an **object** is an instance, created with `ClassName(...)` — no `new`.
- The **primary constructor** `(val x: T, var y: U)` declares parameters *and* properties in the header; a bare parameter (no `val`/`var`) is constructor-only.
- **`init` blocks** run setup in declaration order (interleaved with property initializers); `require`/`check` validate.
- **Secondary constructors** delegate with `: this(...)`, but **default arguments** usually replace them.
- **Properties** compile to getter/setter pairs; custom accessors use **`field`** for the backing storage; a **computed property** has no backing field. Never assign the property inside its own accessor.
- **Visibility**: `public` (default), `private`, `protected`, `internal` (module). Encapsulate mutable state as `private`.
- A **`data class`** generates `equals`/`hashCode`/`toString`/`copy`/`componentN` from its **primary-constructor** properties. Prefer `val`/immutable data; use `copy()` to model change.

### Self-check quiz

1. What's the difference between `class C(val x: Int)`, `class C(var x: Int)`, and `class C(x: Int)`?
   <details><summary>Answer</summary>`val x` = a read-only property; `var x` = a mutable property; bare `x` = a constructor parameter only (usable during init, not stored as a property).</details>
2. Why does a computed property (custom getter, no `field`) have no backing field?
   <details><summary>Answer</summary>Because its value is calculated on each access from other data; there's nothing to store, so the compiler omits the field. Touching `field` is what forces a backing field to exist.</details>
3. A `data class` has a `var` property declared in its body. Is it used in `equals()`?
   <details><summary>Answer</summary>No. Only properties in the *primary constructor* are used by the generated `equals`/`hashCode`/`toString`/`copy`.</details>
4. Why prefer `val` properties in a `data class`?
   <details><summary>Answer</summary>Immutability keeps `hashCode` stable (safe as `Set`/`Map` keys), avoids shared-mutation bugs, and fits Kotlin's `copy()`-to-change idiom. Mutable data classes can corrupt hash-based collections.</details>

### Exercises

**Exercise 8.1 — Bank account (guided).** Model a `BankAccount` with a private balance, `deposit`, a `withdraw` that refuses overdrafts, and an info method. Validate inputs.

<details><summary>Show solution</summary>

```kotlin
class BankAccount(val owner: String, private var balance: Double = 0.0) {
    fun deposit(amount: Double) {
        require(amount > 0) { "Deposit must be positive" }
        balance += amount
    }

    fun withdraw(amount: Double): Boolean {
        if (amount <= 0 || amount > balance) return false
        balance -= amount
        return true
    }

    fun info() = "Account($owner): balance = $balance"
}

fun main() {
    val acc = BankAccount("Alice")
    acc.deposit(1000.0)
    println(acc.withdraw(300.0))   // → true
    println(acc.withdraw(800.0))   // → false  (only 700 left)
    println(acc.info())            // → Account(Alice): balance = 700.0
}
```

**Why this works:** `balance` is `private`, so it can only change via `deposit`/`withdraw`, which enforce the rules (positive deposits, no overdraft) — encapsulation in action. `withdraw` returns a `Boolean` so the caller learns whether it succeeded.

</details>

**Exercise 8.2 — Immutable update.** Given `data class Point(val x: Int, val y: Int)`, write a function `movedRight(p: Point, dx: Int): Point` that returns a new point shifted right, without mutating `p`.

<details><summary>Show solution</summary>

```kotlin
data class Point(val x: Int, val y: Int)

fun movedRight(p: Point, dx: Int): Point = p.copy(x = p.x + dx)

fun main() {
    val a = Point(1, 1)
    val b = movedRight(a, 5)
    println(a)   // → Point(x=1, y=1)   (unchanged)
    println(b)   // → Point(x=6, y=1)
}
```

**Why this works:** `copy(x = p.x + dx)` produces a brand-new `Point` with `x` changed and `y` carried over, leaving the original `a` untouched — the immutable-update pattern you'll use constantly (especially in Android state, Chapter 22).

</details>

### Chapter project: the Task Manager grows a domain

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — the biggest refactor yet. **Builds on:** Ch.1–8. We finally give a task a real *type* and wrap all operations in a `TaskManager` class.

**Goal.** Replace Chapter 6's `List<String>` + `Set` with a `data class Task` and a `TaskManager` that owns a `List<Task>`, using immutable updates.

**Requirements.**
1. `data class Task(id, title, done = false)`.
2. `TaskManager` with a *private* task list and an auto-incrementing id.
3. `add(title)`, `toggle(id)` (via `copy`), `find(id): Task?` (null-safe), `pending()`, and a read-only `all()`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
data class Task(val id: Int, val title: String, val done: Boolean = false)

class TaskManager {
    private val tasks = mutableListOf<Task>()
    private var nextId = 1

    fun add(title: String): Task {
        val task = Task(nextId++, title)
        tasks.add(task)
        return task
    }

    fun toggle(id: Int): Boolean {
        val index = tasks.indexOfFirst { it.id == id }
        if (index == -1) return false
        val current = tasks[index]
        tasks[index] = current.copy(done = !current.done)   // immutable update
        return true
    }

    fun find(id: Int): Task? = tasks.firstOrNull { it.id == id }

    fun pending(): List<Task> = tasks.filter { !it.done }

    fun all(): List<Task> = tasks.toList()   // read-only snapshot — callers can't mutate ours
}

fun main() {
    val manager = TaskManager()
    manager.add("Write chapter 8")
    manager.add("Review chapter 7")
    val third = manager.add("Water plants")

    manager.toggle(third.id)

    println("All tasks:")
    manager.all().forEach {
        val mark = if (it.done) "x" else " "
        println("  #${it.id} [$mark] ${it.title}")
    }
    println("Pending: ${manager.pending().map { it.title }}")
    println("Task 99: ${manager.find(99)?.title ?: "not found"}")
}
```

Output:

```text
All tasks:
  #1 [ ] Write chapter 8
  #2 [ ] Review chapter 7
  #3 [x] Water plants
Pending: [Write chapter 8, Review chapter 7]
Task 99: not found
```

**Commentary.**
- A `Task` is now one cohesive value — id, title, and done-state travel together and can never drift apart. `data class` gives it `equals`/`toString`/`copy` for free.
- `TaskManager` **encapsulates** the list (`private`), so the only way to change tasks is through its methods. `all()` returns a `toList()` *snapshot*, so a caller can't reach in and mutate the internal list (the read-only ≠ immutable lesson from Chapter 6).
- `toggle` models change the immutable way: it doesn't mutate a `Task`; it `copy()`es one with `done` flipped and swaps it into the list.
- `find` returns `Task?`, and `main` handles the miss with `?: "not found"` — the null-safety habits from Chapter 7, now on real objects.
- **What's still missing:** all tasks are the *same kind* of thing. What if some tasks behave differently — a recurring task, a task with a deadline? And what if we want to swap the in-memory storage for a database later without rewriting `TaskManager`? Those need **inheritance and interfaces** — Chapter 9.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Class / object** | A blueprint of data + behaviour / a concrete instance of it. |
| **Primary constructor** | Parameters (and, with `val`/`var`, properties) declared in the class header. |
| **`init` block** | Setup code run during construction, in declaration order. |
| **Secondary constructor** | An alternative constructor delegating via `: this(...)`. |
| **Property** | A field-like member compiled to getter/(setter); may be computed. |
| **Backing field (`field`)** | The actual storage behind a property, accessed inside accessors. |
| **Visibility** | `public`/`private`/`protected`/`internal` access control. |
| **Encapsulation** | Hiding mutable state and exposing controlled operations. |
| **`data class`** | A class with auto-generated `equals`/`hashCode`/`toString`/`copy`/`componentN`. |
| **`copy()`** | Generated function producing a modified duplicate of a data object. |
| **Destructuring** | Unpacking an object into multiple names via `componentN()`. |

### What's next

Tasks are real objects now, but they're all identical in kind, and `TaskManager` is welded to an in-memory list. **[Ch.9 — Inheritance & Interfaces](#chapter-9--inheritance--interfaces)** lets you define families of related types and program to *abstractions* — so the Task Manager can gain a `Repository` interface it doesn't have to care about the implementation of.

[↑ back to top](#chapter-8--classes--objects)


---

## Chapter 9 — Inheritance & Interfaces

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Classes & Objects](#chapter-8--classes--objects)

**Learning objectives** — after this chapter you will be able to:

- Create class hierarchies with `open`, `override`, and `abstract`.
- Define and implement interfaces, including default methods and properties.
- Resolve conflicts when implementing multiple interfaces.
- Program to abstractions (interfaces) rather than concrete classes.
- Replace forwarding boilerplate with interface delegation and model single-method contracts with `fun interface`.

**In this chapter**

- [9.1 Inheritance and `open`](#91-inheritance-and-open)
- [9.2 Abstract classes](#92-abstract-classes)
- [9.3 Interfaces](#93-interfaces)
- [9.4 Multiple interfaces and `super` resolution](#94-multiple-interfaces-and-super-resolution)
- [9.5 Polymorphism: programming to abstractions](#95-polymorphism-programming-to-abstractions)
- [9.6 Interface delegation with `by`](#96-interface-delegation-with-by)
- [9.7 Functional interfaces and SAM conversion](#97-functional-interfaces-and-sam-conversion)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-repository-abstraction) · Glossary · What's next

---

### 9.1 Inheritance and `open`

**Inheritance** lets one class build on another, reusing and specializing its behaviour. The general class is the **superclass** (or *base*); the specialized one is the **subclass** (or *derived*).

In Kotlin every class implicitly inherits from a root type called **`Any`** (the equivalent of Java's `Object`), which is where `equals`, `hashCode`, and `toString` come from. But there's a twist that surprises Java developers: **Kotlin classes are `final` by default** — you cannot inherit from a class unless it explicitly opts in with the **`open`** keyword. The same goes for methods and properties you want to override.

```kotlin
open class Animal(val name: String) {   // `open` → this class CAN be subclassed
    open fun makeSound() {              // `open` → this method CAN be overridden
        println("$name makes some sound")
    }
}

class Dog(name: String) : Animal(name) {   // `: Animal(name)` calls the super constructor
    override fun makeSound() {              // `override` is REQUIRED
        println("$name says Woof!")
    }
}

class Cat(name: String) : Animal(name) {
    override fun makeSound() {
        println("$name says Meow!")
    }
}

fun main() {
    val animals = listOf(Dog("Buddy"), Cat("Whiskers"))
    animals.forEach { it.makeSound() }
    // → Buddy says Woof!
    // → Whiskers says Meow!
}
```

Note three things: the subclass calls the superclass constructor in its header (`: Animal(name)`); overriding a method **requires** the `override` keyword (it's not optional as in Java); and you can only override members that are `open`.

> ☕ **Coming from Java** — This is reversed from Java, where classes are open by default and you write `final` to lock them. Kotlin flips the default to **closed**, so you must *deliberately* design for inheritance.

> ⚙️ **Under the hood — why final by default?** Open classes invite the *fragile base class problem*: a subclass can override a method the base class calls internally, and a later change to the base class silently breaks subclasses. By making classes `final` unless marked `open`, Kotlin forces you to *design and document* extension points on purpose. It also lets the compiler/JIT devirtualize `final` method calls for speed. "Design for inheritance or prohibit it" — baked into the language.

> ⚠️ **Gotcha — don't call `open` members from a constructor.** If a base-class `init`/constructor calls an `open` method, and a subclass overrides it, the override runs *before the subclass's own properties are initialized* — so it sees `null`/zero values. Avoid calling overridable members during construction.

### 9.2 Abstract classes

Sometimes a base class represents a concept too general to instantiate — a "Shape" with no specific area formula. An **`abstract`** class can declare members with *no implementation*, which subclasses must provide. Abstract members are `open` automatically.

```kotlin
import kotlin.math.PI

abstract class Shape {
    abstract val name: String          // no value — subclasses must supply it
    abstract fun area(): Double        // no body — subclasses must implement it

    fun describe() {                   // a concrete method, shared by all shapes
        println("$name has area ${area()}")
    }
}

class Circle(val radius: Double) : Shape() {
    override val name = "Circle"
    override fun area() = PI * radius * radius
}

class Rectangle(val width: Double, val height: Double) : Shape() {
    override val name = "Rectangle"
    override fun area() = width * height
}

fun main() {
    Circle(2.0).describe()        // → Circle has area 12.566370614359172
    Rectangle(3.0, 4.0).describe() // → Rectangle has area 12.0
}
```

An abstract class mixes the *abstract* (must be implemented) with the *concrete* (shared code like `describe()`). You can't write `Shape()` directly — only its concrete subclasses.

> 💡 **Idiom** — Note `PI` comes from `kotlin.math` (`import kotlin.math.PI`), not Java's `Math.PI`. Kotlin's `kotlin.math` package is the idiomatic home for math constants and functions (`sqrt`, `abs`, `pow`, …) and works across all platforms, not just the JVM.

### 9.3 Interfaces

An **interface** describes a *capability* — a set of methods (and properties) a type promises to provide — without dictating how. Unlike a class, a type can implement *many* interfaces. Interfaces can declare abstract members **and** provide default implementations.

```kotlin
interface Drivable {
    val maxSpeed: Int              // abstract property (no backing field allowed here)
    fun drive()                   // abstract method
    fun stop() {                  // default method — implementers inherit this unless they override
        println("Coming to a stop")
    }
}

class Car(override val maxSpeed: Int) : Drivable {
    override fun drive() {
        println("Car cruising at $maxSpeed km/h")
    }
    // stop() not overridden — uses the default
}

fun main() {
    val car = Car(200)
    car.drive()   // → Car cruising at 200 km/h
    car.stop()    // → Coming to a stop   (the default)
}
```

> ⚠️ **Gotcha — interface properties have no backing field.** An interface can *declare* a property (`val maxSpeed: Int`) but cannot *store* one — there's no `field`. Implementers provide the actual storage (here, `Car`'s primary-constructor `override val maxSpeed`). An interface property can have a custom getter, but never a backing field.

> ⚙️ **Under the hood** — On the JVM, an interface's **default methods** compile to real JVM default methods (or, for older targets, a hidden `DefaultImpls` class holding the bodies). Either way, implementers that don't override them inherit the default at no cost. This is how interfaces can carry behaviour, not just signatures.

**Interface vs abstract class — which?** Use an **interface** for a capability many unrelated types can have (`Drivable`, `Comparable`, `Serializable`); a type can implement several. Use an **abstract class** when subclasses share state (stored properties) or a common partial implementation and form one *kind* of thing. A class can implement many interfaces but extend only one class.

### 9.4 Multiple interfaces and `super` resolution

A class can implement several interfaces at once:

```kotlin
interface Flyable { fun move() = println("Flying") }
interface Swimmable { fun move() = println("Swimming") }

class Duck : Flyable, Swimmable {
    // Both interfaces provide a default `move()` → the compiler forces you to resolve the clash
    override fun move() {
        super<Flyable>.move()   // call Flyable's version explicitly
        super<Swimmable>.move() // call Swimmable's version explicitly
        println("A duck does both")
    }
}

fun main() {
    Duck().move()
    // → Flying
    // → Swimming
    // → A duck does both
}
```

When two interfaces supply a default method with the same signature, the class **must** override it, and can reach each parent's version with `super<InterfaceName>.method()`. This makes the "diamond" ambiguity explicit and safe rather than silently picking one.

### 9.5 Polymorphism: programming to abstractions

The real payoff of all this is **polymorphism**: code written against a base type or interface works with *any* implementation, present or future.

```kotlin
// This function knows only "Shape" — it works for circles, rectangles, and shapes not yet written
fun totalArea(shapes: List<Shape>): Double = shapes.sumOf { it.area() }

fun main() {
    val shapes = listOf(Circle(1.0), Rectangle(2.0, 3.0), Circle(2.0))
    println(totalArea(shapes))   // → 3.141592653589793 + 6.0 + 12.566370614359172 = 21.70796...
}
```

`totalArea` never mentions `Circle` or `Rectangle`. It depends on the *abstraction* `Shape`, so it automatically supports every shape — the definition of extensible design.

> 💡 **Idiom** — "**Program to an interface, not an implementation.**" Accept and return the most abstract type that does the job (`List` not `ArrayList`; `Shape` not `Circle`; a `Repository` interface not a concrete database class). Your code then depends on *what* a thing can do, not *how* it does it — which is exactly what this chapter's project exploits.

### 9.6 Interface delegation with `by`

Composition is often safer than inheritance: wrap an implementation, forward most operations, and override only the behavior you own. Kotlin generates the forwarding methods with `by`:

```kotlin
interface TaskStore {
    fun add(title: String)
    fun all(): List<String>
}

class LoggingTaskStore(
    private val delegate: TaskStore,
    private val log: (String) -> Unit
) : TaskStore by delegate {
    override fun add(title: String) {
        log("adding: $title")
        delegate.add(title)
    }
}
```

`LoggingTaskStore` still satisfies `TaskStore`. The compiler forwards `all()` to `delegate`; the explicit `add` overrides the generated forwarding method. This is the **decorator pattern** without a page of boilerplate.

> ⚠️ **Gotcha** — Calls made *inside the delegate* stay on the delegate. Delegation is forwarding, not a virtual self-rebinding mechanism. If `delegate.add()` internally calls its own `all()`, it does not jump to an override in the wrapper.

### 9.7 Functional interfaces and SAM conversion

A **functional interface** has one abstract method and represents a named behavior contract:

```kotlin
fun interface TaskValidator {
    fun validate(title: String): String?

    fun isValid(title: String): Boolean = validate(title) == null
}

val nonBlank = TaskValidator { title ->
    if (title.isBlank()) "title must not be blank" else null
}
```

The lambda becomes an implementation through **SAM conversion** (Single Abstract Method). Kotlin also converts lambdas to compatible Java SAM interfaces such as `Runnable`.

Choose deliberately:

- Use a function type such as `(String) -> String?` for a local, structural callback.
- Use `typealias Validator = (String) -> String?` only to give that same function type a readable alias; it does not create a new type.
- Use `fun interface` when the contract deserves a distinct type, default methods, documentation, Java-friendly API, or future non-abstract members.

> ⚙️ **Under the hood** — On the JVM, non-capturing SAM lambdas can be created through `invokedynamic` and reused. A capturing lambda must retain its captured values. Treat allocation claims as implementation details and measure hot paths rather than guessing.

---

### Summary

- Kotlin classes and members are **`final` by default**; opt into inheritance with **`open`**, and override with the mandatory **`override`** keyword. Every class inherits from **`Any`**.
- **`abstract`** classes declare members with no implementation (subclasses must provide them) while also sharing concrete code; they can't be instantiated.
- **Interfaces** describe capabilities; a type can implement many. They allow abstract members and **default methods**, but interface properties have **no backing field**.
- Clashing interface defaults must be resolved by overriding and calling **`super<Interface>.method()`**.
- **Polymorphism** lets code written against a base type/interface work with any implementation — program to abstractions for extensible design.
- **Interface delegation** (`: Interface by delegate`) generates forwarding methods and makes decorators cheap; a **`fun interface`** gives a single-method behavior a real named type and supports SAM conversion.

### Self-check quiz

1. Why won't `class Dog : Animal()` compile if `Animal` is a plain `class`?
   <details><summary>Answer</summary>Kotlin classes are `final` by default. `Animal` must be declared `open` (or `abstract`) to be subclassed.</details>
2. When do you *have* to override a method that has a default implementation?
   <details><summary>Answer</summary>When you implement two interfaces that both provide a default with the same signature — the ambiguity forces you to override and pick via `super<Interface>.method()`.</details>
3. Can an interface store a property value in a backing field? 
   <details><summary>Answer</summary>No. Interfaces have no backing fields; they can declare properties (optionally with a custom getter), but the implementing type provides the storage.</details>
4. Interface or abstract class for "anything that can be compared"?
   <details><summary>Answer</summary>An interface — it's a capability many unrelated types can have, and types can implement several interfaces (this is exactly what the standard `Comparable` is).</details>

### Exercises

**Exercise 9.1 — Employees (guided).** Model an `abstract` `Employee` with `name`, `baseSalary`, and an abstract `calculateSalary()`. Add a `Manager` (bonus per team member) and a `Developer` (bonus per language). Give managers a `Manageable` interface capability.

<details><summary>Show solution</summary>

```kotlin
interface Manageable {
    fun manageTeam()
}

abstract class Employee(val name: String, val baseSalary: Double) {
    abstract fun calculateSalary(): Double
    fun describe() = println("$name earns ${calculateSalary()}")
}

class Manager(name: String, base: Double, val teamSize: Int)
    : Employee(name, base), Manageable {
    override fun calculateSalary() = baseSalary + teamSize * 500
    override fun manageTeam() = println("$name manages $teamSize people")
}

class Developer(name: String, base: Double, val languages: Int) : Employee(name, base) {
    override fun calculateSalary() = baseSalary + languages * 1000
}

fun main() {
    val m = Manager("Alice", 50_000.0, 5)
    val d = Developer("Bob", 60_000.0, 3)
    m.describe()      // → Alice earns 52500.0
    m.manageTeam()    // → Alice manages 5 people
    d.describe()      // → Bob earns 63000.0
}
```

**Why this works:** `Employee` shares the concrete `describe()` while leaving `calculateSalary()` abstract, so each role computes pay differently (50000 + 5×500 = 52500; 60000 + 3×1000 = 63000). `Manager` *also* implements the `Manageable` interface — a capability a `Developer` doesn't have — showing how a class extends one class but can add interface capabilities on top.

</details>

**Exercise 9.2 — Payable total.** Using the classes above, write `payrollTotal(staff: List<Employee>): Double` that sums everyone's calculated salary.

<details><summary>Show solution</summary>

```kotlin
fun payrollTotal(staff: List<Employee>): Double = staff.sumOf { it.calculateSalary() }

fun main() {
    val staff = listOf(
        Manager("Alice", 50_000.0, 5),
        Developer("Bob", 60_000.0, 3)
    )
    println(payrollTotal(staff))   // → 115500.0
}
```

**Why this works:** `payrollTotal` depends only on the `Employee` abstraction and calls the polymorphic `calculateSalary()`, so it correctly totals a mixed list (52500 + 63000 = 115500) and would handle any future `Employee` subtype with no changes.

</details>

### Chapter project: a Repository abstraction

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–9. We introduce a `TaskRepository` *interface* and make `TaskManager` depend on it — not on a concrete list. This is the seam that later lets us swap in a database (Chapter 21) without touching `TaskManager`.

**Goal.** Extract storage behind an interface, implement it in memory, and rewire `TaskManager` to depend on the abstraction.

**Requirements.**
1. A `TaskRepository` interface (`add`, `all`, `findById`, `replace`).
2. An `InMemoryTaskRepository` implementing it.
3. `TaskManager` takes a `TaskRepository` in its constructor and uses only its interface.

<details><summary>Show reference solution + commentary</summary>

```kotlin
data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {
    fun add(task: Task)
    fun all(): List<Task>
    fun findById(id: Int): Task?
    fun replace(task: Task)
}

class InMemoryTaskRepository : TaskRepository {
    private val tasks = mutableListOf<Task>()

    override fun add(task: Task) { tasks.add(task) }
    override fun all(): List<Task> = tasks.toList()
    override fun findById(id: Int): Task? = tasks.firstOrNull { it.id == id }
    override fun replace(task: Task) {
        val index = tasks.indexOfFirst { it.id == task.id }
        if (index != -1) tasks[index] = task
    }
}

class TaskManager(private val repo: TaskRepository) {   // depends on the ABSTRACTION
    private var nextId = 1

    fun add(title: String): Task {
        val task = Task(nextId++, title)
        repo.add(task)
        return task
    }

    fun toggle(id: Int): Boolean {
        val task = repo.findById(id) ?: return false
        repo.replace(task.copy(done = !task.done))
        return true
    }

    fun pending(): List<Task> = repo.all().filter { !it.done }
    fun all(): List<Task> = repo.all()
}

fun main() {
    val manager = TaskManager(InMemoryTaskRepository())   // inject the implementation
    manager.add("Design the interface")
    val impl = manager.add("Implement it")
    manager.toggle(impl.id)

    manager.all().forEach {
        println("#${it.id} [${if (it.done) "x" else " "}] ${it.title}")
    }
    println("Pending: ${manager.pending().map { it.title }}")
}
```

Output:

```text
#1 [ ] Design the interface
#2 [x] Implement it
Pending: [Design the interface]
```

**Commentary.**
- `TaskManager` no longer owns a list — it holds a `TaskRepository`. It calls `add`/`findById`/`replace` without knowing (or caring) whether they're backed by a list, a file, or a database. That's **dependency inversion**: high-level policy (`TaskManager`) depends on an abstraction, not a detail.
- We **inject** the concrete `InMemoryTaskRepository` at the call site (`TaskManager(InMemoryTaskRepository())`). In Chapter 21 we'll write an `ExposedTaskRepository` backed by a real database and pass *that* in instead — `TaskManager`'s code won't change at all. In Chapter 33 we'll formalize this wiring with a DI framework.
- The null-safe `findById(id) ?: return false` and immutable `copy` carry straight over from Chapters 7 and 8.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Inheritance** | A subclass building on a superclass. |
| **`Any`** | The root of all Kotlin classes (like Java's `Object`). |
| **`open`** | Marks a class/member as inheritable/overridable (closed by default). |
| **`override`** | Mandatory keyword when redefining an inherited member. |
| **`abstract`** | A member with no implementation (or a class with such members); can't be instantiated. |
| **Interface** | A capability contract; a type may implement many; allows default methods. |
| **Default method** | An interface method with a body, inherited unless overridden. |
| **`super<T>.m()`** | Calls a specific parent's implementation to resolve a clash. |
| **Polymorphism** | Code against a base type/interface working with any implementation. |
| **Dependency inversion** | Depending on abstractions (interfaces), not concrete implementations. |

### What's next

You can build type families and program to interfaces. **[Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features)** adds the specialized class kinds that make Kotlin modelling so expressive: `sealed` hierarchies with exhaustive `when`, `enum`s, singleton `object`s, `companion object`s, and allocation-free `value` classes.

[↑ back to top](#chapter-9--inheritance--interfaces)


---

## Chapter 10 — Advanced Object-Oriented Features

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Classes & Objects](#chapter-8--classes--objects), [Ch.9 — Inheritance & Interfaces](#chapter-9--inheritance--interfaces)

**Learning objectives** — after this chapter you will be able to:

- Model closed hierarchies with `sealed` types and get exhaustive `when` for free.
- Use `enum` classes with properties and methods.
- Create singletons with `object`, and class-level members with `companion object`.
- Distinguish nested from `inner` classes, and use allocation-free `value` classes.

**In this chapter**

- [10.1 Sealed classes and interfaces](#101-sealed-classes-and-interfaces)
- [10.2 Enum classes](#102-enum-classes)
- [10.3 Object declarations (singletons)](#103-object-declarations-singletons)
- [10.4 Companion objects](#104-companion-objects)
- [10.5 Nested and inner classes](#105-nested-and-inner-classes)
- [10.6 Value classes](#106-value-classes)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-priorities-and-typed-results) · Glossary · What's next

---

### 10.1 Sealed classes and interfaces

A `sealed` type defines a **closed set of subtypes** — the compiler knows *every* possible case because all subclasses must live in the same module (and, conventionally, the same file). This is the perfect tool for modelling "a value that is one of a few known shapes": a result that is a success *or* an error, a UI state that is loading *or* loaded *or* failed.

```kotlin
sealed class Result {
    data class Success(val data: String) : Result()
    data class Error(val message: String) : Result()
    object Loading : Result()
}

fun handle(result: Result): String = when (result) {
    is Result.Success -> "Data: ${result.data}"   // smart-cast to Success here
    is Result.Error -> "Failed: ${result.message}"
    Result.Loading -> "Loading..."
    // NO `else` needed — the compiler knows these are ALL the cases
}
```

The magic is that **`when` over a sealed type is checked for exhaustiveness**. Because the compiler knows the complete list of subtypes, it verifies you've handled every one — and *no `else` is needed*. Better still, the day you add a `Result.Timeout` subtype, every `when` that isn't exhaustive becomes a **compile error**, pointing you at exactly the code that must handle the new case. That's a refactoring superpower.

A **`sealed interface`** works the same way and is often preferable, since a type can implement multiple interfaces:

```kotlin
sealed interface Payment {
    data class Card(val number: String) : Payment
    data class Cash(val amount: Double) : Payment
    object Free : Payment
}
```

> 💡 **Idiom** — Reach for `sealed` whenever you'd otherwise use an `enum` but each case needs to carry *different data*. An `enum` case is a single constant; a `sealed` subtype can be a `data class` with its own fields. "Enum for constants, sealed for variants."

> ⚠️ **Gotcha** — All direct subtypes of a sealed type must be declared in the same **module** (and, up to Kotlin's package rules, the same package). You can't have outside code sneak in a new subtype — which is precisely the guarantee that makes exhaustiveness safe.

### 10.2 Enum classes

An **`enum`** defines a fixed set of named constant instances:

```kotlin
enum class Direction { NORTH, SOUTH, EAST, WEST }

val d = Direction.NORTH
println(d)              // → NORTH
println(d.name)         // → NORTH   (the constant's name as a String)
println(d.ordinal)      // → 0       (its position, 0-based)
```

Enums can carry data (via a constructor) and define methods:

```kotlin
enum class Priority(val weight: Int) {
    LOW(1),
    MEDIUM(2),
    HIGH(3);                       // note the semicolon before members

    fun isUrgent(): Boolean = this == HIGH
}

fun main() {
    println(Priority.HIGH.weight)     // → 3
    println(Priority.HIGH.isUrgent()) // → true

    // Iterate every constant (entries is the modern replacement for values())
    for (p in Priority.entries) {
        println("${p.name}: ${p.weight}")
    }

    println(Priority.valueOf("LOW"))  // → LOW   (parse from a String)
}
```

> ⚙️ **Under the hood** — An `enum class` compiles to a `final` class extending `java.lang.Enum`, with each constant a `static final` singleton instance created once at class load. `entries`/`values()` return those instances; `valueOf` looks one up by name. Because each constant is a genuine singleton, comparing enums with `==` is both correct and reference-fast.

> 💡 **Idiom** — Prefer **`Priority.entries`** over the older `Priority.values()`. `values()` allocates a fresh array on every call; `entries` (Kotlin 1.9+) returns a cached, read-only list.

### 10.3 Object declarations (singletons)

Sometimes you want *exactly one* instance of something — a configuration holder, a registry, a stateless service. The **`object` declaration** creates a **singleton**: a class and its single instance in one stroke.

```kotlin
object AppConfig {
    const val VERSION = "2.0"
    var debugMode = false

    fun describe() = "App v$VERSION (debug=$debugMode)"
}

fun main() {
    AppConfig.debugMode = true
    println(AppConfig.describe())   // → App v2.0 (debug=true)
}
```

There's no constructor and no `AppConfig()` — you refer to it by name, and everyone shares the same instance.

> ⚙️ **Under the hood** — An `object` compiles to a class with a `private` constructor and a `public static final INSTANCE` field, initialized once, lazily and thread-safely, when the class is first loaded. This is the classic singleton pattern — correctly implemented — that Java developers used to hand-write (and often got subtly wrong).

> ⚠️ **Gotcha** — An `object` with mutable state (like `var debugMode`) is *global mutable state*. It's shared everywhere and lives for the whole program, which makes code harder to test and reason about (and unsafe under concurrency unless synchronized). Use `object` freely for stateless helpers and constants; be cautious about putting *mutable* state in one.

### 10.4 Companion objects

Kotlin has no `static` members. Instead, to attach functions and properties to a **class itself** (not its instances) — factory methods, constants, counters — you use a **`companion object`**:

```kotlin
class User private constructor(val name: String) {
    companion object {
        const val MAX_NAME_LENGTH = 50

        fun create(name: String): User {
            require(name.length <= MAX_NAME_LENGTH) { "Name too long" }
            return User(name.trim())
        }
    }
}

fun main() {
    val user = User.create("  Alice  ")   // called on the class, like a static method
    println(user.name)                     // → Alice
    println(User.MAX_NAME_LENGTH)          // → 50
}
```

Making the constructor `private` and exposing a companion `create` function is the idiomatic **factory pattern**: callers can't use `User(...)` directly, so you control exactly how instances come into being (here, trimming the name and enforcing a length).

> ⚙️ **Under the hood** — A `companion object` compiles to a nested class named `Companion` plus a static field holding its single instance; `User.create(...)` is really `User.Companion.create(...)`. Members aren't truly JVM-static unless you annotate them `@JvmStatic` (which matters when calling from Java — Chapter 18).

### 10.5 Nested and inner classes

A class declared inside another is **nested** by default and does **not** have access to the outer instance — it's just namespaced:

```kotlin
class Outer {
    private val secret = "hidden"

    class Nested {
        fun show() = "I'm nested (I can't see `secret`)"
    }

    inner class Inner {
        fun show() = "I'm inner, and I can see: $secret"
    }
}

fun main() {
    println(Outer.Nested().show())     // → I'm nested (I can't see `secret`)
    println(Outer().Inner().show())    // → I'm inner, and I can see: hidden
}
```

Add the **`inner`** keyword and the nested class gains a reference to the outer instance, so it can use the outer class's members. Note the construction difference: `Outer.Nested()` needs no outer instance; `Outer().Inner()` does.

> ☕ **Coming from Java** — This is exactly reversed from Java. In Java a nested class is "inner" (holds an outer reference) by default, and you write `static` to make it a plain nested class. Kotlin's default is the plain, non-`static` equivalent, and you *opt in* to `inner`. The Kotlin default avoids the accidental memory leaks Java's inner classes are famous for (an inner instance silently pins its outer instance in memory).

### 10.6 Value classes

Occasionally you want a type that wraps a single value for **type safety** — a `UserId` that is "really" an `Int`, but shouldn't be mixed up with a `TaskId` or a raw number — *without* paying for an extra object allocation. That's a **value class** (`@JvmInline value class`):

```kotlin
@JvmInline
value class UserId(val value: Int)

@JvmInline
value class Email(val raw: String) {
    init { require("@" in raw) { "Invalid email" } }
    fun domain(): String = raw.substringAfter("@")
}

fun sendTo(id: UserId, email: Email) { /* ... */ }

fun main() {
    val id = UserId(42)
    val email = Email("alice@example.com")
    println(email.domain())    // → example.com
    // sendTo(email, id)        // ❌ won't compile — arguments can't be swapped by accident
}
```

`UserId` and `Email` are distinct types the compiler enforces — you can't pass an `Int` where a `UserId` is expected — yet at runtime they mostly vanish.

> ⚙️ **Under the hood** — A `value class` is **inlined**: at runtime, a `UserId` is represented directly as its underlying `Int`, with *no wrapper object allocated*. You get a new *compile-time* type for safety and *zero runtime cost*. The catch: in a few situations the value must be **boxed** (wrapped after all) — when it's used as a nullable (`UserId?`), stored in a generic collection (`List<UserId>`), or treated as a supertype. In the common, direct case, though, it's free.

---

### Summary

- **`sealed`** classes/interfaces define a closed set of subtypes, giving **exhaustive `when`** with no `else` — and a compile error when you add a case and forget to handle it. Use `sealed` for variants that carry different data; `enum` for plain constants.
- **`enum`** classes are fixed sets of named constants that can carry data and methods; prefer **`entries`** over `values()`.
- **`object`** declarations create thread-safe **singletons**; beware mutable global state.
- **`companion object`** replaces `static`, hosting factory functions and constants on the class itself.
- Nested classes are **plain by default**; add **`inner`** to access the outer instance (reversed from Java).
- **`value class`** (`@JvmInline`) gives a distinct type wrapping one value with no allocation (except when boxed as nullable/generic/supertype).

### Self-check quiz

1. What does a `when` over a `sealed` type give you that a `when` over `Int` doesn't?
   <details><summary>Answer</summary>Compiler-checked exhaustiveness with no `else`: it knows all subtypes, verifies you covered each, and turns an unhandled new subtype into a compile error.</details>
2. When would you choose `sealed` over `enum`?
   <details><summary>Answer</summary>When each case needs to carry different data — a sealed subtype can be a `data class` with its own fields, whereas an enum case is a single constant.</details>
3. What's the difference between an `object` and a `companion object`?
   <details><summary>Answer</summary>An `object` is a standalone singleton. A `companion object` is a singleton attached to a class, providing that class's "static-like" members (factories, constants).</details>
4. Why can a `value class` be free at runtime, and when is it not?
   <details><summary>Answer</summary>It's inlined to its underlying value with no wrapper object. It gets boxed (allocated) when used as a nullable, in a generic/collection, or as a supertype.</details>

### Exercises

**Exercise 10.1 — Traffic light (guided).** Model a traffic light with a `sealed` type where each state knows its duration and the next state.

<details><summary>Show solution</summary>

```kotlin
sealed class TrafficLight {
    abstract val duration: Int
    abstract fun next(): TrafficLight

    object Red : TrafficLight() {
        override val duration = 30
        override fun next() = Green
    }
    object Green : TrafficLight() {
        override val duration = 25
        override fun next() = Yellow
    }
    object Yellow : TrafficLight() {
        override val duration = 3
        override fun next() = Red
    }
}

fun main() {
    var light: TrafficLight = TrafficLight.Red
    repeat(4) {
        val label = when (light) {           // exhaustive — no else
            TrafficLight.Red -> "RED"
            TrafficLight.Green -> "GREEN"
            TrafficLight.Yellow -> "YELLOW"
        }
        println("$label for ${light.duration}s")
        light = light.next()
    }
}
```

Output:
```text
RED for 30s
GREEN for 25s
YELLOW for 3s
RED for 30s
```

**Why this works:** each state is an `object` (there's only ever one Red), and the `sealed` parent makes the `when` exhaustive. `next()` encodes the state machine's transitions right on the states themselves.

</details>

**Exercise 10.2 — Enum with behaviour.** Make a `Coin` enum (`PENNY`, `NICKEL`, `DIME`, `QUARTER`) that stores its value in cents, then sum a handful of coins.

<details><summary>Show solution</summary>

```kotlin
enum class Coin(val cents: Int) {
    PENNY(1), NICKEL(5), DIME(10), QUARTER(25)
}

fun main() {
    val pocket = listOf(Coin.QUARTER, Coin.DIME, Coin.PENNY, Coin.QUARTER)
    val total = pocket.sumOf { it.cents }
    println("Total: $total cents")   // → Total: 61 cents
}
```

**Why this works:** each constant carries its `cents` via the enum constructor, so `sumOf { it.cents }` totals them (25+10+1+25 = 61). Enums with data replace piles of `when`-on-a-string lookups.

</details>

### Chapter project: priorities and typed results

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–10. We add a `Priority` **enum** to tasks, return a **`sealed`** result from `toggle` (instead of a bare `Boolean`), and generate ids from an **`object`**.

**Goal.** Enrich the domain with an enum priority and a typed operation result.

**Requirements.**
1. A `Priority` enum (`LOW`/`MEDIUM`/`HIGH`) with a label and an `isUrgent` flag.
2. `Task` gains a `priority`.
3. `toggle` returns a `sealed` `ToggleResult` (`Toggled(task)` or `NotFound`).
4. An `object IdGenerator` supplies ids; `urgentPending()` filters urgent, undone tasks.

<details><summary>Show reference solution + commentary</summary>

```kotlin
enum class Priority(val label: String) {
    LOW("low"), MEDIUM("medium"), HIGH("high");
    val isUrgent: Boolean get() = this == HIGH
}

data class Task(
    val id: Int,
    val title: String,
    val priority: Priority = Priority.MEDIUM,
    val done: Boolean = false
)

sealed interface ToggleResult {
    data class Toggled(val task: Task) : ToggleResult
    object NotFound : ToggleResult
}

object IdGenerator {
    private var current = 0
    fun next(): Int = ++current
}

class TaskManager {
    private val tasks = mutableListOf<Task>()

    fun add(title: String, priority: Priority = Priority.MEDIUM): Task {
        val task = Task(IdGenerator.next(), title, priority)
        tasks.add(task)
        return task
    }

    fun toggle(id: Int): ToggleResult {
        val index = tasks.indexOfFirst { it.id == id }
        if (index == -1) return ToggleResult.NotFound
        val updated = tasks[index].copy(done = !tasks[index].done)
        tasks[index] = updated
        return ToggleResult.Toggled(updated)
    }

    fun urgentPending(): List<Task> = tasks.filter { !it.done && it.priority.isUrgent }
    fun all(): List<Task> = tasks.toList()
}

fun describe(result: ToggleResult): String = when (result) {   // exhaustive
    is ToggleResult.Toggled -> "Toggled '${result.task.title}' → done=${result.task.done}"
    ToggleResult.NotFound -> "No such task"
}

fun main() {
    val manager = TaskManager()
    manager.add("Write chapter 10", Priority.HIGH)
    val coffee = manager.add("Buy coffee", Priority.LOW)

    println(describe(manager.toggle(coffee.id)))
    println(describe(manager.toggle(999)))

    manager.all().forEach {
        println("#${it.id} [${if (it.done) "x" else " "}] ${it.title} (${it.priority.label})")
    }
    println("Urgent pending: ${manager.urgentPending().map { it.title }}")
}
```

Output:

```text
Toggled 'Buy coffee' → done=true
No such task
#1 [ ] Write chapter 10 (high)
#2 [x] Buy coffee (low)
Urgent pending: [Write chapter 10]
```

**Commentary.**
- `Priority` is an **enum with data and a computed property** — every task now carries a real priority instead of a magic string.
- `toggle` returns a **sealed** `ToggleResult` rather than a `Boolean`. The caller's `when` in `describe` is **exhaustive** — if we later add a `ToggleResult.Locked` case, the compiler will flag `describe` until we handle it. That's far safer than a bare `true`/`false` that can't distinguish "not found" from "failed."
- `IdGenerator` is an **`object` singleton** — a small, deliberate use of shared state for id issuing. (In a bigger app we'd inject it to keep tests isolated, which Chapter 33 addresses.)
- The `when` in `describe` handling the sealed result is the same exhaustiveness win we'll rely on heavily for UI state in Chapter 22.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`sealed` type** | A closed hierarchy whose subtypes are all known to the compiler; enables exhaustive `when`. |
| **`enum` class** | A fixed set of named constant instances, optionally with data/methods. |
| **`entries`** | The cached, read-only list of an enum's constants (prefer over `values()`). |
| **`object` declaration** | A singleton class-and-instance in one. |
| **`companion object`** | A singleton attached to a class for its "static-like" members. |
| **Factory pattern** | A `companion` function that constructs instances (often with a `private` constructor). |
| **Nested class** | A class inside another, without access to the outer instance. |
| **`inner` class** | A nested class holding a reference to the outer instance. |
| **`value class`** | `@JvmInline` type wrapping one value with no runtime allocation (except when boxed). |

### What's next

You now have Kotlin's full modelling toolkit. **[Ch.11 — Extension Functions & Properties](#chapter-11--extension-functions--properties)** shows how to add behaviour to types you don't own — including the standard library and your own `Task` — keeping call sites clean and expressive.

[↑ back to top](#chapter-10--advanced-object-oriented-features)


---

## Chapter 11 — Extension Functions & Properties

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Classes & Objects](#chapter-8--classes--objects), [Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features)

**Learning objectives** — after this chapter you will be able to:

- Add functions and properties to types you don't own — including the standard library.
- Write extensions on nullable receivers.
- Explain why extensions are resolved *statically*, and the surprises that causes.
- Keep call sites clean by turning helpers into extensions.

**In this chapter**

- [11.1 Extension functions](#111-extension-functions)
- [11.2 Extension properties](#112-extension-properties)
- [11.3 Nullable receivers](#113-nullable-receivers)
- [11.4 How extensions really work (static resolution)](#114-how-extensions-really-work-static-resolution)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-domain-vocabulary) · Glossary · What's next

---

### 11.1 Extension functions

An **extension function** lets you add a new function to an existing type — *without* editing that type's source or subclassing it. You write the type name before the function name (the **receiver type**), and inside the body `this` refers to the instance you were called on.

```kotlin
fun String.isPalindrome(): Boolean {
    val clean = this.lowercase().filter { it.isLetterOrDigit() }
    return clean == clean.reversed()
}

fun main() {
    println("Racecar".isPalindrome())   // → true
    println("hello".isPalindrome())     // → false
}
```

`String.isPalindrome()` reads as though `isPalindrome` were a built-in method on `String` — but you added it, and you could do the same for `Int`, `List`, or any type at all, including ones from libraries you can't modify:

```kotlin
fun Int.isEven(): Boolean = this % 2 == 0

fun List<Int>.secondLargest(): Int? {
    val sorted = this.distinct().sortedDescending()
    return if (sorted.size >= 2) sorted[1] else null
}

fun main() {
    println(4.isEven())                       // → true
    println(listOf(5, 2, 8, 8, 1).secondLargest())   // → 5
}
```

> ☕ **Coming from Java** — Extensions are Java's static utility methods (`StringUtils.isPalindrome(s)`) turned inside out. Instead of `StringUtils.isPalindrome(s)`, you write `s.isPalindrome()` — the readable, discoverable, dot-completion form — but under the hood it's still just a static method (see §11.4). No more `Utils` grab-bags.

> 💡 **Idiom** — Extensions are the idiomatic way to add focused, reusable helpers. They keep your own classes small (only *core* behaviour lives inside the class) while giving call sites a fluent, method-style vocabulary. Kotlin's own standard library is built this way — `filter`, `map`, `first` on collections are all extension functions.

### 11.2 Extension properties

You can add **properties** too. Since an extension can't store data in the object (there's nowhere to add a field), an extension property must be **computed** — it needs a custom getter and no backing field:

```kotlin
val String.lastChar: Char
    get() = this[this.length - 1]

val List<Int>.sumOfSquares: Int
    get() = this.sumOf { it * it }

fun main() {
    println("Kotlin".lastChar)             // → n
    println(listOf(1, 2, 3, 4).sumOfSquares)   // → 30
}
```

Here's the correctly-escaped word-count property (a raw string `"""\s+"""` for the whitespace regex — a plain `"\s+"` would be an illegal escape):

```kotlin
val String.wordCount: Int
    get() = this.trim().split("""\s+""".toRegex()).size

fun main() {
    println("the quick   brown  fox".wordCount)   // → 4
}
```

> ⚠️ **Gotcha** — An extension property **cannot** have an initializer or a backing field: `val String.foo: Int = 0` is an error. It must compute its value in a getter every time. If you find yourself wanting to *store* per-instance data on a type you don't own, an extension property is the wrong tool.

### 11.3 Nullable receivers

An extension's receiver type can be **nullable**, which lets the extension handle the null case *itself* — so callers don't even need a `?.`:

```kotlin
fun String?.orPlaceholder(): String = this ?: "(none)"

fun main() {
    val a: String? = "hi"
    val b: String? = null
    println(a.orPlaceholder())   // → hi
    println(b.orPlaceholder())   // → (none)   — no NPE, called directly on null
}
```

This is exactly how the standard library's `isNullOrEmpty()` and `isNullOrBlank()` (Chapter 7) work: they're declared on `CharSequence?`, so they can inspect `this == null` safely from inside.

### 11.4 How extensions really work (static resolution)

Now the crucial mental correction. Despite the fluent `receiver.method()` syntax, an extension does **not** actually become a member of the class, and it is **not** dispatched polymorphically. Instead:

> ⚙️ **Under the hood** — The compiler translates an extension into a plain **static function** whose first (hidden) parameter is the receiver. `"Racecar".isPalindrome()` compiles to something like `StringExtKt.isPalindrome("Racecar")`. Because it's a static call resolved by the **declared (compile-time) type** of the receiver — not the runtime type — extensions are *statically dispatched*.

That static dispatch has a visible, sometimes-surprising consequence:

```kotlin
open class Shape
class Rectangle : Shape()

fun Shape.describe() = "a shape"
fun Rectangle.describe() = "a rectangle"

fun printDescription(shape: Shape) {
    println(shape.describe())   // resolved by the DECLARED type: Shape
}

fun main() {
    printDescription(Rectangle())   // → a shape   (NOT "a rectangle"!)
}
```

Even though we passed a `Rectangle`, `printDescription` sees its parameter as declared type `Shape`, so `Shape.describe()` is chosen — at compile time. This is the opposite of how *member* functions behave (those are virtual — the runtime type wins). Keep the rule in mind: **member functions dispatch on runtime type; extensions dispatch on declared type.**

A second consequence:

> ⚠️ **Gotcha — a member always beats an extension.** If a class has a member function and you define an extension with the same name and signature, calls resolve to the **member** — your extension is silently shadowed. Extensions add to types that *lack* a capability; they can't override one a class already has.

---

### Summary

- **Extension functions** add methods to existing types without modifying or subclassing them: `fun String.foo()`, with `this` as the receiver. They give library and your own types a fluent vocabulary.
- **Extension properties** must be computed (custom getter, no backing field, no initializer).
- Receivers can be **nullable** (`fun String?.foo()`), letting the extension handle null internally.
- Extensions compile to **static functions** taking the receiver as a hidden first argument, so they are **resolved by the declared type**, not the runtime type (unlike virtual member functions).
- A **member function always shadows** a same-signature extension.

### Self-check quiz

1. Why must an extension property be computed (no backing field)?
   <details><summary>Answer</summary>An extension can't add storage to a type it doesn't own — there's no place for a field — so the value must be produced by a getter each time.</details>
2. `printDescription(Rectangle())` prints "a shape", not "a rectangle." Why?
   <details><summary>Answer</summary>Extensions are statically dispatched by the *declared* type. Inside `printDescription`, the parameter's declared type is `Shape`, so `Shape.describe()` is chosen at compile time regardless of the runtime `Rectangle`.</details>
3. If a class has a member `fun size()` and you write an extension `fun C.size()`, which runs?
   <details><summary>Answer</summary>The member. Members always win over same-signature extensions; the extension is shadowed.</details>
4. How can `"x".isNullOrEmpty()` be called when the value might be null?
   <details><summary>Answer</summary>It's an extension on a *nullable* receiver (`CharSequence?`), so it can check `this == null` internally — no `?.` needed at the call site.</details>

### Exercises

**Exercise 11.1 — String utilities (guided).** Add extensions to `String`: `countVowels()`, `removeDigits()`, and `titleCase()` (capitalize each word). Add an extension property `wordCount`.

<details><summary>Show solution</summary>

```kotlin
fun String.countVowels(): Int = this.lowercase().count { it in "aeiou" }

fun String.removeDigits(): String = this.filter { !it.isDigit() }

fun String.titleCase(): String =
    this.split(" ").joinToString(" ") { word ->
        word.replaceFirstChar { it.uppercase() }
    }

val String.wordCount: Int
    get() = this.trim().split("""\s+""".toRegex()).size

fun main() {
    val text = "hello world 123"
    println(text.countVowels())   // → 3
    println(text.removeDigits())  // → hello world 
    println(text.titleCase())     // → Hello World 123
    println(text.wordCount)       // → 3
}
```

**Why this works:** each helper is a focused extension on `String`. `countVowels` counts characters in the vowel set; `removeDigits` filters out digits; `titleCase` splits on spaces and capitalizes each word's first char; `wordCount` splits on the (correctly-escaped) whitespace regex. Note `removeDigits` leaves the trailing space where "123" was.

</details>

**Exercise 11.2 — Collection extension.** Add `List<Int>.average2()` returning the mean as a `Double`, or `0.0` for an empty list — without using the built-in `average()`.

<details><summary>Show solution</summary>

```kotlin
fun List<Int>.average2(): Double =
    if (this.isEmpty()) 0.0 else this.sum().toDouble() / this.size

fun main() {
    println(listOf(2, 4, 6).average2())   // → 4.0
    println(emptyList<Int>().average2())  // → 0.0
}
```

**Why this works:** the extension guards the empty case (avoiding division by zero), then divides the sum — converted to `Double` so it's real division — by the size. `this` is the list it was called on.

</details>

### Chapter project: a domain vocabulary

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–11. We give `Task` and `List<Task>` a fluent extension vocabulary, keeping the core types tiny while making call sites read naturally.

**Goal.** Add domain extensions: a task summary, pending filter, completion-rate property, and a null-safe title parser.

**Requirements.**
1. `Task.summary(): String` — a one-line display.
2. `List<Task>.pending(): List<Task>`.
3. `val List<Task>.completionRate: Double` — percent done.
4. `String?.toTaskTitleOrNull(): String?` — trims and rejects blank input.

<details><summary>Show reference solution + commentary</summary>

```kotlin
data class Task(val id: Int, val title: String, val done: Boolean = false)

fun Task.summary(): String = "#$id ${if (done) "✓" else "○"} $title"

fun List<Task>.pending(): List<Task> = this.filter { !it.done }

val List<Task>.completionRate: Double
    get() = if (this.isEmpty()) 0.0 else this.count { it.done } * 100.0 / this.size

fun String?.toTaskTitleOrNull(): String? {
    val trimmed = this?.trim()
    return if (trimmed.isNullOrEmpty()) null else trimmed
}

fun main() {
    val tasks = listOf(
        Task(1, "Write extensions chapter", done = true),
        Task(2, "Review it"),
        Task(3, "Ship it")
    )

    tasks.forEach { println(it.summary()) }
    println("Pending: ${tasks.pending().map { it.title }}")
    println("Completion: ${tasks.completionRate}%")

    val raw: String? = "   "
    println("Parsed title: ${raw.toTaskTitleOrNull() ?: "invalid"}")
}
```

Output:

```text
#1 ✓ Write extensions chapter
#2 ○ Review it
#3 ○ Ship it
Pending: [Review it, Ship it]
Completion: 33.333333333333336%
Parsed title: invalid
```

**Commentary.**
- `Task` stays a plain `data class` — no display logic bloating it. Presentation lives in `summary()`, an extension, which the UI layer (Chapter 22) can reuse or replace.
- `List<Task>.pending()` and the `completionRate` property read like the collection *natively* understands tasks — that fluency is the point. `completionRate` is computed (no storage), exactly as extension properties must be.
- `String?.toTaskTitleOrNull()` is a **nullable-receiver** extension: it swallows `null` and blank input and returns a clean `String?`, so callers handle "no valid title" with a simple `?:` — the Chapter 7 discipline, packaged as vocabulary.
- Because extensions are statically resolved (§11.4), these are perfectly predictable — no surprise dispatch — which is why they're safe to sprinkle liberally across a codebase.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Extension function** | A function added to a type from outside, with the type as its receiver. |
| **Receiver** | The instance an extension is called on; `this` inside the body. |
| **Extension property** | A computed property added to a type (no backing field/initializer). |
| **Nullable receiver** | An extension declared on `T?`, able to handle `null` internally. |
| **Static resolution** | Extensions dispatched by the receiver's *declared* type at compile time. |
| **Shadowing** | A member function taking precedence over a same-signature extension. |

### What's next

Your types now have expressive vocabularies. **[Ch.12 — Generics](#chapter-12--generics)** makes them *reusable across types*: you'll write a single `Repository<T>` that works for tasks, users, or anything else, and learn variance (`in`/`out`), `reified`, and why the JVM "erases" generic types.

[↑ back to top](#chapter-11--extension-functions--properties)


---

## Chapter 12 — Generics

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Inheritance & Interfaces](#chapter-9--inheritance--interfaces), [Ch.11 — Extensions](#chapter-11--extension-functions--properties)

**Learning objectives** — after this chapter you will be able to:

- Write generic functions and classes that work across many types.
- Constrain type parameters with upper bounds.
- Use variance (`out`/`in`) to make generic types substitutable safely.
- Recover runtime type info with `reified`, and explain why erasure makes it necessary.
- Use star projections and use-site projections without falling back to unsafe casts.

**In this chapter**

- [12.1 Why generics?](#121-why-generics)
- [12.2 Generic functions and classes](#122-generic-functions-and-classes)
- [12.3 Type constraints (upper bounds)](#123-type-constraints-upper-bounds)
- [12.4 Variance: `out` and `in`](#124-variance-out-and-in)
- [12.5 Type erasure and `reified`](#125-type-erasure-and-reified)
- [12.6 Star projections and use-site variance](#126-star-projections-and-use-site-variance)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-generic-repository) · Glossary · What's next

---

### 12.1 Why generics?

In Chapter 9 we wrote a `TaskRepository` for storing tasks. But an app also stores users, orders, sessions… Do we write a `UserRepository`, an `OrderRepository`, each an identical copy with a different element type? That's duplication begging to be removed.

**Generics** let you write code parameterized *by type*: a single `Repository<T>` that works for `Task`, `User`, or anything, with the compiler still enforcing full type safety. You've already been using generics — `List<String>`, `Map<String, Int>`, `Box`-like types — the `<...>` is the type parameter. Now you'll write your own.

### 12.2 Generic functions and classes

A **generic function** declares a type parameter (conventionally `T`) in angle brackets *before* the function name, then uses it like a real type:

```kotlin
fun <T> firstOrNull(list: List<T>): T? =
    if (list.isEmpty()) null else list[0]

fun main() {
    println(firstOrNull(listOf(1, 2, 3)))       // → 1     (T = Int)
    println(firstOrNull(listOf<String>()))      // → null  (T = String)
}
```

The caller doesn't specify `T` — the compiler **infers** it from the argument. A **generic class** parameterizes its whole definition:

```kotlin
class Box<T>(private val content: T) {
    fun get(): T = content
    fun <R> map(transform: (T) -> R): Box<R> = Box(transform(content))
}

fun main() {
    val intBox = Box(42)
    val strBox = intBox.map { "Value is $it" }   // Box<Int> → Box<String>
    println(strBox.get())   // → Value is 42
}
```

`Box<T>` holds a `T`; its `map` even introduces a *second* type parameter `R` for the transformed result. This is exactly how `List<T>.map` works.

### 12.3 Type constraints (upper bounds)

A bare `T` could be *any* type, so you can only do to it what *every* type supports. To call type-specific methods, add an **upper bound** — a supertype `T` must extend:

```kotlin
// T must be Comparable, so we can use < and >
fun <T : Comparable<T>> maxOf(a: T, b: T): T = if (a > b) a else b

fun main() {
    println(maxOf(3, 7))               // → 7
    println(maxOf("apple", "banana"))  // → banana   (String is Comparable)
}
```

Without `: Comparable<T>`, the `a > b` wouldn't compile — a random `T` has no ordering. For **multiple** bounds, use a `where` clause:

```kotlin
fun <T> firstUpper(items: List<T>): T?
        where T : CharSequence, T : Comparable<T> =
    items.filter { it.isNotEmpty() && it[0].isUpperCase() }.minOrNull()
```

### 12.4 Variance: `out` and `in`

Here's a puzzle. A `List<String>` is clearly *also usable as* a `List<Any>` (every string is an Any, and you only read from it). But is a `MutableList<String>` usable as a `MutableList<Any>`? **No** — because then you could `add(42)` to it, corrupting a list that's supposed to hold strings. **Variance** is how Kotlin encodes which direction of substitution is safe.

**Covariance — `out`.** Mark a type parameter `out` when the type only ever **produces** (returns) `T`, never consumes it. Then `Producer<String>` *is a* `Producer<Any>`:

```kotlin
class Producer<out T>(private val value: T) {
    fun produce(): T = value       // T only comes OUT
}

fun main() {
    val strProducer: Producer<String> = Producer("hello")
    val anyProducer: Producer<Any> = strProducer   // ✅ safe: covariance (out)
    println(anyProducer.produce())
}
```

**Contravariance — `in`.** Mark a type parameter `in` when the type only ever **consumes** (accepts) `T`, never returns it. Then `Consumer<Any>` *is a* `Consumer<String>`:

```kotlin
class Consumer<in T> {
    fun consume(item: T) { println("Consuming $item") }   // T only goes IN
}

fun main() {
    val anyConsumer: Consumer<Any> = Consumer()
    val strConsumer: Consumer<String> = anyConsumer   // ✅ safe: contravariance (in)
    strConsumer.consume("Kotlin")
}
```

The memory aid is **"PECS": Producer-Extends (`out`), Consumer-Super (`in`)** — a producer of `T` can be treated as a producer of any supertype; a consumer of `T` can be treated as a consumer of any subtype. This is why the standard library's `List` is `List<out E>` (read-only, produces) but `MutableList` is invariant (both produces and consumes).

> ☕ **Coming from Java** — `out T` is Java's `? extends T` and `in T` is `? super T`. The difference is *where* you declare it. Java uses **use-site** variance (wildcards on every usage — `List<? extends Number>`), which is verbose and repeated everywhere. Kotlin lets you declare variance **once, at the class definition** (declaration-site), so users of `Producer<out T>` never write a wildcard. (Kotlin supports use-site variance too, e.g. `Array<out Any>`, when a type is naturally invariant.)

### 12.5 Type erasure and `reified`

On the JVM, generic type arguments **do not exist at runtime** — they are *erased*. A `List<String>` and a `List<Int>` are both just `List` once compiled; the `<String>`/`<Int>` is a compile-time-only annotation the compiler uses to check your code, then throws away.

This has real consequences:

```kotlin
fun <T> printTypeCheck(value: Any) {
    // if (value is T) { }   // ❌ COMPILE ERROR: cannot check for erased type T
}

val list: List<Any> = listOf("a", "b")
// list is List<String>       // ❌ can't check the element type — it's erased
println(list is List<*>)      // ✅ can only check "is it some List?" → true
```

To *recover* the type at runtime, Kotlin offers **`reified`** type parameters — but they work only in **`inline`** functions (Chapter 25). Because an inline function's body is copied directly into each call site, the concrete type is known *there*, so the compiler can substitute it and let you write `is T` or `T::class`:

```kotlin
inline fun <reified T> Any.isInstanceOf(): Boolean = this is T   // works because reified

fun main() {
    println("hi".isInstanceOf<String>())   // → true
    println(42.isInstanceOf<String>())     // → false
}
```

> ⚙️ **Under the hood** — Erasure is inherited from the JVM (Java erases generics too, for backward compatibility). `reified` is Kotlin's escape hatch: `inline` means "paste this function's body at the call site," and at that site the actual type argument is a literal, so `is T` compiles to a concrete `instanceof` check. This is why `reified` *requires* `inline`, and why it has **no Java equivalent** — Java must pass an explicit `Class<T>` token instead.

> ⚠️ **Gotcha** — Because of erasure you can't, in ordinary code, do `T()` (construct a `T`), make an `Array<T>` directly, or check `x is T`. Work around it with a factory lambda (`create: () -> T`), `reified`, or by passing a `KClass<T>`.

### 12.6 Star projections and use-site variance

Sometimes you know a value is a `Box` or `List` but intentionally do not know its element type. Use a **star projection**, not `Any`:

```kotlin
fun describe(values: List<*>) {
    val first: Any? = values.firstOrNull() // safe to read as Any?
    println("size=${values.size}, first=$first")
    // values.add("x")                     // impossible: element type is unknown
}
```

`List<*>` means "a list of some specific but unknown type." `List<Any?>` means "a list whose declared element type is `Any?`." Those are not interchangeable. For an invariant `MutableList<*>`, reads are safe as `Any?`, but writes other than `null` cannot be proven safe.

Use-site projections constrain one particular use of an invariant generic:

```kotlin
fun copyNumbers(from: Array<out Number>, to: Array<in Number>) {
    for (index in from.indices) to[index] = from[index]
}
```

`from` is projected as a producer, so you cannot write to it; `to` is projected as a consumer, so reading gives only `Any?`. This is Kotlin's local equivalent of Java wildcards.

> 💡 **Idiom** — Avoid unchecked casts such as `value as List<String>`. Validate elements (`all { it is String }`), transform with `filterIsInstance<String>()`, or preserve the type parameter through your API. `@Suppress("UNCHECKED_CAST")` belongs only at a small, audited boundary whose invariant you can explain.

---

### Summary

- **Generics** parameterize code by type: one `Box<T>`/`Repository<T>` serves all element types with full type safety; the compiler usually **infers** the type argument.
- **Upper bounds** (`<T : Comparable<T>>`, or multiple via `where`) let you call a supertype's members on `T`.
- **Variance** controls safe substitution: **`out`** (covariant, T only produced — like read-only `List`), **`in`** (contravariant, T only consumed). Mnemonic: **PECS**. Kotlin declares variance at the **class** (declaration-site), unlike Java's per-use wildcards.
- Generic types are **erased** at runtime, so you can't do `is T`, `T()`, or `Array<T>` normally. **`reified`** (only in **`inline`** functions) restores the type at the call site, enabling `is T`/`T::class`.
- **`List<*>`** preserves an unknown element type safely; **use-site projections** (`out`/`in`) restrict an invariant type to producing or consuming at a particular call boundary.

### Self-check quiz

1. Why does `maxOf` need the bound `<T : Comparable<T>>`?
   <details><summary>Answer</summary>To use `>`/`<` on `T`, the type must be orderable. The bound restricts `T` to `Comparable` types, so the comparison compiles.</details>
2. Why is `List<out E>` covariant but `MutableList<E>` invariant?
   <details><summary>Answer</summary>`List` only *produces* elements (read-only), so covariance (`out`) is safe. `MutableList` also *consumes* (via `add`), so treating a `MutableList<String>` as `MutableList<Any>` would let you add non-strings — unsafe — hence invariant.</details>
3. Why can't you write `if (x is T)` in a normal generic function?
   <details><summary>Answer</summary>Type arguments are erased at runtime, so `T` doesn't exist to check against. You need a `reified` T in an `inline` function.</details>
4. What's the "PECS" mnemonic?
   <details><summary>Answer</summary>Producer-Extends, Consumer-Super: a type that produces `T` uses `out` (Java `? extends`); one that consumes `T` uses `in` (Java `? super`).</details>

### Exercises

**Exercise 12.1 — Generic stack (guided).** Implement a generic `Stack<T>` with `push`, `pop` (returns `T?`), `peek`, and `isEmpty`.

<details><summary>Show solution</summary>

```kotlin
class Stack<T> {
    private val items = mutableListOf<T>()

    fun push(item: T) { items.add(item) }
    fun pop(): T? = if (items.isEmpty()) null else items.removeAt(items.size - 1)
    fun peek(): T? = items.lastOrNull()
    fun isEmpty(): Boolean = items.isEmpty()
    override fun toString(): String = items.toString()
}

fun main() {
    val s = Stack<Int>()
    s.push(1); s.push(2); s.push(3)
    println(s)          // → [1, 2, 3]
    println(s.pop())    // → 3
    println(s.peek())   // → 2

    val words = Stack<String>()
    words.push("a"); words.push("b")
    println(words)      // → [a, b]
}
```

**Why this works:** the type parameter `T` makes one class serve `Int`, `String`, or any type, with the compiler enforcing that a `Stack<Int>` only holds ints. `pop` returns `T?` so the empty case is a null, not a crash — the Chapter 7 habit applied to a generic.

</details>

**Exercise 12.2 — Reified filter.** Write `inline fun <reified T> List<*>.onlyInstances(): List<T>` returning only the elements that are of type `T`.

<details><summary>Show solution</summary>

```kotlin
inline fun <reified T> List<*>.onlyInstances(): List<T> {
    val result = mutableListOf<T>()
    for (item in this) {
        if (item is T) result.add(item)   // `is T` works because T is reified
    }
    return result
}

fun main() {
    val mixed: List<Any> = listOf(1, "two", 3, "four", 5)
    println(mixed.onlyInstances<String>())   // → [two, four]
    println(mixed.onlyInstances<Int>())      // → [1, 3, 5]
}
```

**Why this works:** marking `T` as `reified` (in an `inline` function) lets the runtime check `item is T`. Without `reified`, erasure would make that check impossible. (The standard library's `filterIsInstance<T>()` is implemented the same way.)

</details>

### Chapter project: a generic Repository

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–12. We generalize Chapter 9's `TaskRepository` into a reusable `Repository<T>` — one storage abstraction for tasks *and* any future entity.

**Goal.** Turn the task-specific repository into a generic one, constrained to identifiable items.

**Requirements.**
1. An `Identifiable` interface exposing `val id: Int`.
2. A generic `InMemoryRepository<T : Identifiable>` with `add`, `findById`, `replace`, `all`.
3. `Task` implements `Identifiable`; show the repo working with `Task`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
interface Identifiable {
    val id: Int
}

data class Task(
    override val id: Int,
    val title: String,
    val done: Boolean = false
) : Identifiable

class InMemoryRepository<T : Identifiable> {
    private val items = mutableListOf<T>()

    fun add(item: T) { items.add(item) }
    fun findById(id: Int): T? = items.firstOrNull { it.id == id }
    fun replace(item: T) {
        val index = items.indexOfFirst { it.id == item.id }
        if (index != -1) items[index] = item
    }
    fun all(): List<T> = items.toList()
}

fun main() {
    val repo = InMemoryRepository<Task>()
    repo.add(Task(1, "Learn generics"))
    repo.add(Task(2, "Use them", done = true))

    println(repo.findById(1)?.title)                       // → Learn generics
    println("Done: ${repo.all().filter { it.done }.map { it.title }}")  // → Done: [Use them]

    // The SAME repository class would work for any Identifiable — e.g. a User:
    // val users = InMemoryRepository<User>()
}
```

Output:

```text
Learn generics
Done: [Use them]
```

**Commentary.**
- One `InMemoryRepository<T>` replaces a family of near-identical repositories. The bound `T : Identifiable` guarantees every stored item has an `id`, so `findById`/`replace` can rely on it — a bound earning its keep.
- `Task` implements `Identifiable` by `override val id`, satisfying the constraint. A `User` (or any future entity) can join simply by implementing `Identifiable`, reusing all the storage logic.
- This is the shape most real apps use. In Chapter 21 the *implementation* behind this interface becomes a database; in Chapter 33 we'll wire the generic repository through dependency injection. The generic abstraction is what keeps all of that swappable.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Generic** | Code parameterized by a type (`<T>`). |
| **Type parameter / argument** | The placeholder `T` / the concrete type supplied for it. |
| **Upper bound** | A constraint `T : Super` restricting what `T` can be (multiple via `where`). |
| **Variance** | Rules for substituting `Generic<Sub>` where `Generic<Super>` is expected. |
| **Covariance (`out`)** | `T` only produced; `G<Sub>` is a `G<Super>`. |
| **Contravariance (`in`)** | `T` only consumed; `G<Super>` is a `G<Sub>`. |
| **PECS** | Producer-Extends (`out`), Consumer-Super (`in`). |
| **Type erasure** | Generic type arguments removed at runtime on the JVM. |
| **`reified`** | An `inline` type parameter available at runtime (enables `is T`, `T::class`). |

### What's next

That completes **Part 2 — Object-Oriented Kotlin**: you can design types, hierarchies, extensions, and generic abstractions. **Part 3 opens with [Ch.13 — Delegated Properties](#chapter-13--delegated-properties)**, where `by lazy`, observable properties, and custom delegates let you factor out *how a property works* — the first of Kotlin's more functional, compositional tools.

[↑ back to top](#chapter-12--generics)


---

## Chapter 13 — Delegated Properties

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Classes & Objects](#chapter-8--classes--objects), [Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features)

**Learning objectives** — after this chapter you will be able to:

- Delegate a property's get/set logic to a reusable object with `by`.
- Use the standard delegates: `lazy`, `observable`, `vetoable`, and `by map`.
- Write your own property delegate.
- Choose `lazy` correctly (and know when it's the *wrong* tool).

**In this chapter**

- [13.1 The idea: delegating a property](#131-the-idea-delegating-a-property)
- [13.2 `lazy`](#132-lazy)
- [13.3 `observable` and `vetoable`](#133-observable-and-vetoable)
- [13.4 Storing properties in a map](#134-storing-properties-in-a-map)
- [13.5 Writing a custom delegate](#135-writing-a-custom-delegate)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-lazy-setup-and-change-logging) · Glossary · What's next

---

### 13.1 The idea: delegating a property

You've written properties with custom getters and setters (Chapter 8). But some get/set *patterns* recur everywhere: "compute this once, lazily"; "log every change"; "reject invalid values." Copying that logic into every property's accessor is duplication.

**Delegated properties** factor the *how* of a property into a separate, reusable object. Instead of writing the accessor yourself, you say `by <delegate>`, and the delegate handles the reads and writes:

```kotlin
class Example {
    val data: String by lazy { computeExpensiveValue() }   // `lazy` is the delegate
}
```

The `by` keyword means "route this property's get (and set) through the object on the right." Kotlin ships several ready-made delegates and lets you write your own.

### 13.2 `lazy`

`by lazy { … }` computes a `val` **once, on first access**, then caches and returns that same value forever after. Perfect for expensive setup you might not even need:

```kotlin
class ReportGenerator {
    val header: String by lazy {
        println("(computing header once)")
        "=== Report ==="
    }
}

fun main() {
    val gen = ReportGenerator()
    println("created")           // header not computed yet
    println(gen.header)          // → (computing header once)  then  === Report ===
    println(gen.header)          // → === Report ===   (cached; no recompute)
}
```

By default `lazy` is **thread-safe** — if two threads race to first-access it, only one computation runs. You can relax that when you know only one thread is involved:

```kotlin
val value: Int by lazy(LazyThreadSafetyMode.NONE) { expensiveCompute() }
```

- `SYNCHRONIZED` (default): thread-safe, uses a lock.
- `PUBLICATION`: multiple threads may compute, but the first result wins.
- `NONE`: no synchronization — fastest, but only safe for single-threaded access.

> ⚙️ **Under the hood** — `val header by lazy { … }` makes the compiler create a hidden field, `header$delegate`, holding a `Lazy<String>` object. Reading `header` becomes `header$delegate.value`, which computes-and-caches on the first call. So the "laziness" is just a small wrapper object the compiler wires in for you.

> ⚠️ **Gotcha** — `lazy` caches **once**. It is the right tool for a value that's expensive but **never changes**. It is the *wrong* tool for a value *derived from mutable state* (like "the current sorted view of a changing list") — it would compute once and then serve a **stale** result forever. For derived-from-mutable data, use a normal computed property (`get() = …`), which recomputes each access.

### 13.3 `observable` and `vetoable`

From `kotlin.properties.Delegates`, two delegates react to changes of a `var`.

**`observable`** runs a callback **after** each assignment — ideal for logging or triggering updates:

```kotlin
import kotlin.properties.Delegates

class Settings {
    var theme: String by Delegates.observable("light") { property, old, new ->
        println("${property.name} changed: $old -> $new")
    }
}

fun main() {
    val s = Settings()
    s.theme = "dark"    // → theme changed: light -> dark
    s.theme = "system"  // → theme changed: dark -> system
}
```

**`vetoable`** runs a callback **before** each assignment and can **reject** it by returning `false`:

```kotlin
import kotlin.properties.Delegates

class Account {
    var balance: Int by Delegates.vetoable(0) { _, _, new ->
        new >= 0   // only accept non-negative balances
    }
}

fun main() {
    val a = Account()
    a.balance = 100
    println(a.balance)   // → 100
    a.balance = -50      // rejected — the callback returned false
    println(a.balance)   // → 100   (unchanged)
}
```

### 13.4 Storing properties in a map

A property can delegate to a **`Map`**, reading its value by the property's name as key. Handy for dynamic data (parsed JSON, config):

```kotlin
class Config(private val map: Map<String, Any?>) {
    val host: String by map
    val port: Int by map
}

fun main() {
    val config = Config(mapOf("host" to "localhost", "port" to 8080))
    println("${config.host}:${config.port}")   // → localhost:8080
}
```

Each property reads `map["host"]`, `map["port"]`, etc. (For a `MutableMap`, `var` properties can write back into it.)

### 13.5 Writing a custom delegate

Any object can be a property delegate if it provides the right **operator functions**: `getValue` (for `val`/`var`) and, for a `var`, `setValue`. Their signatures receive the owning object (`thisRef`) and a `KProperty` describing the property:

```kotlin
import kotlin.reflect.KProperty

class Trimmed {
    private var value: String = ""

    operator fun getValue(thisRef: Any?, property: KProperty<*>): String = value

    operator fun setValue(thisRef: Any?, property: KProperty<*>, newValue: String) {
        value = newValue.trim()   // always store the trimmed form
    }
}

class Form {
    var username: String by Trimmed()
}

fun main() {
    val form = Form()
    form.username = "   alice   "
    println("[${form.username}]")   // → [alice]
}
```

> ⚙️ **Under the hood** — When you write `var username by Trimmed()`, the compiler rewrites `form.username = x` into `delegate.setValue(form, ::username, x)` and reads into `delegate.getValue(...)`. The `operator` keyword on `getValue`/`setValue` is what lets the compiler recognize a valid delegate. That's the entire mechanism — a convention, not magic.

> ⚠️ **Gotcha — two different `by`s.** Don't confuse *property* delegation (`val x by lazy`) with *class/interface* delegation (`class Wrapper(list: List<T>) : List<T> by list`, Chapter 9's cousin). Both use `by`, but one delegates a single property's accessors, the other delegates a whole interface's methods to another object. Same keyword, different features.

> ☕ **Coming from Java** — Property delegates replace a grab-bag of Java boilerplate: hand-written double-checked-locking lazy holders (`lazy`), `PropertyChangeListener`/`PropertyChangeSupport` (`observable`), and manual validation setters (`vetoable`) — each now a one-liner.

---

### Summary

- **`by`** delegates a property's get/set to a reusable object, factoring out recurring accessor patterns.
- **`lazy`** computes a `val` once on first access and caches it (thread-safe by default; `NONE`/`PUBLICATION` relax that). Use it only for values that *don't change* — never for data derived from mutable state.
- **`observable`** runs a callback *after* each change; **`vetoable`** runs one *before* and can reject the change.
- **`by map`** reads a property's value from a map keyed by its name.
- A **custom delegate** is any object with `operator fun getValue` (and `setValue` for `var`); the compiler rewrites property access into calls on it.

### Self-check quiz

1. When is `lazy` the *wrong* choice?
   <details><summary>Answer</summary>When the value derives from mutable state and must stay current — `lazy` caches once and would serve a stale value. Use a computed `get()` property instead.</details>
2. What's the difference between `observable` and `vetoable`?
   <details><summary>Answer</summary>`observable` fires *after* the assignment (for reacting/logging); `vetoable` fires *before* and can reject the new value by returning `false`.</details>
3. What two operator functions can a custom delegate provide, and when is each needed?
   <details><summary>Answer</summary>`getValue` (needed for `val` and `var`) and `setValue` (needed for `var`). Both are marked `operator`.</details>
4. `class A : List<T> by b` and `val x by lazy {}` — same feature?
   <details><summary>Answer</summary>No. The first is interface/class delegation (delegating all `List` methods to `b`); the second is property delegation. They share the `by` keyword but are different mechanisms.</details>

### Exercises

**Exercise 13.1 — Length-validated field (guided).** Write a custom delegate that only accepts strings of at least a minimum length, ignoring shorter assignments. Use it for a `password` (min 8).

<details><summary>Show solution</summary>

```kotlin
import kotlin.reflect.KProperty

class MinLength(private val min: Int) {
    private var value: String = ""
    operator fun getValue(thisRef: Any?, property: KProperty<*>): String = value
    operator fun setValue(thisRef: Any?, property: KProperty<*>, newValue: String) {
        if (newValue.length >= min) {
            value = newValue
        } else {
            println("${property.name}: rejected (need >= $min chars)")
        }
    }
}

class Account {
    var password: String by MinLength(8)
}

fun main() {
    val acc = Account()
    acc.password = "short"          // → password: rejected (need >= 8 chars)
    acc.password = "longenough123"  // accepted
    println(acc.password)           // → longenough123
}
```

**Why this works:** the delegate centralizes the length rule in `setValue`. Any property declared `by MinLength(n)` inherits the validation — no repeated `if` in every setter. `property.name` gives a helpful message.

</details>

**Exercise 13.2 — Lazy expensive value.** Give a class a `by lazy` property that prints a "computing" message, and show it's computed only once across two accesses.

<details><summary>Show solution</summary>

```kotlin
class Cache {
    val pi: Double by lazy {
        println("computing pi...")
        3.14159
    }
}

fun main() {
    val c = Cache()
    println("start")
    println(c.pi)   // → computing pi...  then  3.14159
    println(c.pi)   // → 3.14159  (no recompute)
}
```

**Why this works:** `lazy` defers the block until the first `c.pi`, prints once, caches the result, and returns the cached value on the second access — hence a single "computing pi..." line.

</details>

### Chapter project: lazy setup and change logging

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–13. We add a `by lazy` one-time banner and an `observable` audit log of the last action.

**Goal.** Use the right delegate for each job: `lazy` for a compute-once banner, `observable` to log every state change.

**Requirements.**
1. A `banner: String by lazy { … }` built only on first use.
2. A `lastAction: String by Delegates.observable(...)` that logs each change.
3. `add`/`complete` update `lastAction`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlin.properties.Delegates

data class Task(val id: Int, val title: String, val done: Boolean = false)

class TaskManager {
    private val tasks = mutableListOf<Task>()

    // Compute-once: exactly what lazy is for.
    val banner: String by lazy {
        println("(building banner once...)")
        "=== Task Manager v1.0 ==="
    }

    // React-after-change: audit logging.
    var lastAction: String by Delegates.observable("none") { property, old, new ->
        println("[log] ${property.name}: '$old' -> '$new'")
    }

    fun add(title: String) {
        val task = Task(tasks.size + 1, title)
        tasks.add(task)
        lastAction = "added: $title"
    }

    fun complete(id: Int) {
        val index = tasks.indexOfFirst { it.id == id }
        if (index != -1) {
            tasks[index] = tasks[index].copy(done = true)
            lastAction = "completed #$id"
        }
    }

    fun all(): List<Task> = tasks.toList()
}

fun main() {
    val manager = TaskManager()
    manager.add("Write chapter 13")
    manager.add("Review it")
    manager.complete(1)

    println(manager.banner)   // built here, on first access
    println(manager.banner)   // cached — no rebuild

    manager.all().forEach { println("#${it.id} [${if (it.done) "x" else " "}] ${it.title}") }
}
```

Output:

```text
[log] lastAction: 'none' -> 'added: Write chapter 13'
[log] lastAction: 'added: Write chapter 13' -> 'added: Review it'
[log] lastAction: 'added: Review it' -> 'completed #1'
(building banner once...)
=== Task Manager v1.0 ===
=== Task Manager v1.0 ===
#1 [x] Write chapter 13
#2 [ ] Review it
```

**Commentary.**
- `banner` is `by lazy` because it's built once and never changes — note "(building banner once...)" prints a single time even across two accesses.
- `lastAction` is `observable` because we want to *react* to each change (here, log it). The three `[log]` lines appear as the actions happen, *before* the banner — because the additions/completion run first in `main`.
- **Why not `by lazy` for a sorted view?** A cached sorted list would go stale as tasks change (the gotcha in §13.2). If we needed "tasks sorted by title," it would be a plain computed `get()` property, recomputed each call. Picking the right tool per property is the lesson.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Delegated property** | A property whose get/set is handled by a separate delegate object via `by`. |
| **`by`** | Keyword routing a property's accessors to a delegate. |
| **`lazy`** | Delegate computing a `val` once on first access, then caching. |
| **`LazyThreadSafetyMode`** | `SYNCHRONIZED`/`PUBLICATION`/`NONE` — how `lazy` handles concurrent first access. |
| **`observable`** | Delegate firing a callback after each assignment. |
| **`vetoable`** | Delegate firing a callback before each assignment, able to reject it. |
| **`getValue`/`setValue`** | The `operator` functions a custom delegate provides. |
| **`KProperty`** | Reflection object describing the delegated property (e.g. its `name`). |

### What's next

Delegates let you reuse *how a property works*. **[Ch.14 — Scope Functions](#chapter-14--scope-functions)** brings a related idea to expressions: `let`, `run`, `with`, `apply`, and `also` create small scopes around an object, cleaning up configuration, transformation, and null-handling code.

[↑ back to top](#chapter-13--delegated-properties)


---

## Chapter 14 — Scope Functions

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.7 — Null Safety](#chapter-7--null-safety)

**Learning objectives** — after this chapter you will be able to:

- Use `let`, `run`, `with`, `apply`, and `also` for their intended jobs.
- Choose the right one using two simple questions.
- Combine scope functions with `?.` for clean null-handling.
- Avoid the "let-elvis" trap and scope-function overuse.

**In this chapter**

- [14.1 What scope functions are](#141-what-scope-functions-are)
- [14.2 The five functions](#142-the-five-functions)
- [14.3 Choosing the right one](#143-choosing-the-right-one)
- [14.4 `takeIf` and `takeUnless`](#144-takeif-and-takeunless)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-configuring-and-reporting) · Glossary · What's next

---

### 14.1 What scope functions are

Kotlin's five **scope functions** — `let`, `run`, `with`, `apply`, `also` — all do the same basic thing: they run a block of code **in the context of an object**, giving you a temporary scope where that object is easily accessible. They don't add new capabilities; they make common patterns (configure this, transform that, do something only if non-null) shorter and clearer.

They differ on exactly **two questions**:

1. **How is the object referred to inside the block** — as `this` (the receiver), or as `it` (an argument)?
2. **What does the whole call return** — the *result of the block*, or the *object itself*?

Master those two axes and all five fall into place.

### 14.2 The five functions

**`let`** — object as `it`, returns the **block result**. Its signature classic: transform a value, and (with `?.`) run only when non-null.

```kotlin
val name: String? = "Alice"
val length: Int = name?.let {
    println("Processing $it")
    it.length            // block result → returned
} ?: 0
println(length)          // → 5
```

**`run`** — object as `this`, returns the **block result**. Like `let` but you access members directly (no `it.`):

```kotlin
val message = "Hello".run {
    "$this has ${length} characters"   // `this`/`length` refer to the string
}
println(message)   // → Hello has 5 characters
```

**`with`** — same as `run` (object as `this`, returns block result) but called as `with(obj) { … }` rather than `obj.run { … }`. Use it to group several calls on an object:

```kotlin
val sb = StringBuilder()
val text = with(sb) {
    append("a")
    append("b")
    append("c")
    toString()          // block result
}
println(text)   // → abc
```

**`apply`** — object as `this`, returns the **object itself**. The configuration workhorse: set a bunch of properties and get the object back.

```kotlin
data class Person(var name: String = "", var age: Int = 0)

val person = Person().apply {
    name = "Alice"      // `this` is the Person
    age = 30
}
println(person)   // → Person(name=Alice, age=30)
```

**`also`** — object as `it`, returns the **object itself**. For side effects (logging, validation) that shouldn't interrupt a chain:

```kotlin
val numbers = mutableListOf(1, 2, 3)
    .also { println("Created: $it") }   // side effect
    .also { it.add(4) }                 // still returns the list
println(numbers)   // → [1, 2, 3, 4]
```

> ⚙️ **Under the hood** — All five are tiny `inline` functions, so using them adds **zero** runtime overhead (no extra objects, no call cost — the lambda body is pasted in). Their entire definitions are one-liners; for example:
> ```kotlin
> inline fun <T> T.apply(block: T.() -> Unit): T { block(); return this }
> inline fun <T> T.also(block: (T) -> Unit): T { block(this); return this }
> inline fun <T, R> T.let(block: (T) -> R): R = block(this)
> ```
> `apply`/`also` end in `return this` (→ the object); `let`/`run`/`with` return the block's value. That single line *is* the whole difference.

### 14.3 Choosing the right one

Here's the decision table — the whole chapter in one grid:

| Function | Object is | Returns | Typical use |
|----------|-----------|---------|-------------|
| `let`    | `it`      | block result | transform a value; run on non-null via `?.let` |
| `run`    | `this`    | block result | compute a result using the object's members |
| `with`   | `this`    | block result | call several members; not called on a nullable |
| `apply`  | `this`    | the object   | **configure** an object, then return it |
| `also`   | `it`      | the object   | **side effects** (log/validate) within a chain |

> 💡 **Idiom** — Quick heuristics: **`apply`** to configure (`Foo().apply { … }`), **`also`** for a peek/log in a chain, **`let`** for `x?.let { … }` null handling and transforms, **`run`**/**`with`** when you want a computed *result* from an object's members. If you're unsure, you can express most things with a plain variable — reach for a scope function only when it genuinely reads better.

> ⚠️ **Gotcha — the "let-elvis" trap.** `value?.let { … } ?: default` runs `default` if the **`let` block returns null**, even when `value` was *not* null:
> ```kotlin
> val name: String? = "Bob"
> val result = name?.let { null } ?: "fallback"   // block returns null...
> println(result)   // → fallback   (even though name was "Bob"!)
> ```
> The `?:` reacts to the *block's* result, not to `value`. If you only want the fallback when `value` is null, don't put logic that can itself return null inside the `let` before the `?:`.

> ⚠️ **Gotcha — overuse.** Nesting scope functions (`x.apply { y.also { z.let { … } } }`) with mixed `this`/`it` quickly becomes unreadable. Scope functions are seasoning, not the meal. If a block gets long or deeply nested, a named local variable and plain statements are clearer.

### 14.4 `takeIf` and `takeUnless`

Two close cousins return the object *only if* a condition holds, else `null` — great for turning a predicate into a nullable you can chain with `?:` or `?.let`:

```kotlin
val input = "hello@example.com"

val validEmail = input.takeIf { "@" in it }     // input if it contains @, else null
println(validEmail ?: "invalid")                 // → hello@example.com

val nonBlank = "   ".takeUnless { it.isBlank() } // null, because it IS blank
println(nonBlank ?: "(was blank)")               // → (was blank)
```

`takeIf { cond }` keeps the value when `cond` is true; `takeUnless { cond }` keeps it when `cond` is false.

---

### Summary

- Scope functions run a block **in the context of an object**, differing on two axes: object as **`this`** vs **`it`**, and returning the **block result** vs **the object**.
- **`let`** (`it`, result) — transform / `?.let` null handling. **`run`**/**`with`** (`this`, result) — compute from members. **`apply`** (`this`, object) — configure. **`also`** (`it`, object) — side effects in a chain.
- All five are **`inline`** — zero overhead. The `return this` vs "return block result" is the only real difference.
- **`takeIf`/`takeUnless`** yield the object or `null` based on a predicate.
- Beware the **let-elvis trap** (`?:` reacts to the block's null, not the receiver's) and **overuse** (nested mixed `this`/`it` hurts readability).

### Self-check quiz

1. Which scope functions return the *object*, and which return the *block result*?
   <details><summary>Answer</summary>`apply` and `also` return the object; `let`, `run`, and `with` return the block's result.</details>
2. Which use `this` and which use `it`?
   <details><summary>Answer</summary>`run`, `with`, `apply` use `this`; `let` and `also` use `it`.</details>
3. Which scope function best fits "create an object and set several properties"?
   <details><summary>Answer</summary>`apply` — it exposes the object as `this` for configuration and returns the object.</details>
4. Why can `name?.let { compute(it) } ?: default` run `default` even when `name` isn't null?
   <details><summary>Answer</summary>Because `?:` checks the *result of the `let` block*. If `compute(it)` returns null, the fallback runs regardless of `name` being non-null (the let-elvis trap).</details>

### Exercises

**Exercise 14.1 — Configure with `apply` (guided).** Build a `StringBuilder`-based greeting using `apply`, then return the string.

<details><summary>Show solution</summary>

```kotlin
fun greeting(name: String): String =
    StringBuilder().apply {
        append("Hello, ")
        append(name)
        append("!")
    }.toString()

fun main() {
    println(greeting("Alice"))   // → Hello, Alice!
}
```

**Why this works:** `apply` exposes the `StringBuilder` as `this`, so `append(...)` calls target it directly, and `apply` returns the builder — on which we call `toString()`. No temporary variable needed.

</details>

**Exercise 14.2 — Null handling with `let`.** Given a nullable `String?`, print its length in uppercase-count form only if present; otherwise print "absent".

<details><summary>Show solution</summary>

```kotlin
fun report(text: String?) {
    text?.let {
        println("'$it' has ${it.length} chars")
    } ?: println("absent")
}

fun main() {
    report("Kotlin")   // → 'Kotlin' has 6 chars
    report(null)       // → absent
}
```

**Why this works:** `?.let` runs the block only when `text` is non-null (as `it`). When `text` is null, `?.let` yields null and the `?:` runs the "absent" branch. (Here the `let` block returns `Unit` from `println`, which is non-null, so there's no let-elvis surprise.)

</details>

### Chapter project: configuring and reporting

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–14. We clean up construction with `apply`, add a logging peek with `also`, and build a text report.

**Goal.** Use `apply` to set up a manager, `also` to log, and a string builder to render a report. (The report uses `"=".repeat(30)` — the correct way to repeat a character; there is no `"=" * 30` operator in Kotlin.)

**Requirements.**
1. Create and seed a `TaskManager` with `apply`, logging via `also`.
2. A `buildReport(manager)` producing a formatted, bordered report.

<details><summary>Show reference solution + commentary</summary>

```kotlin
data class Task(val id: Int, val title: String, val done: Boolean = false)

class TaskManager {
    val tasks = mutableListOf<Task>()
}

fun buildReport(manager: TaskManager): String = buildString {
    val border = "=".repeat(30)       // NOT "=" * 30 — Kotlin strings have no * operator
    appendLine(border)
    appendLine("TASK REPORT")
    appendLine(border)
    manager.tasks.forEachIndexed { index, task ->
        val mark = if (task.done) "x" else " "
        appendLine("${index + 1}. [$mark] ${task.title}")
    }
    appendLine(border)
    append("Total: ${manager.tasks.size}")
}

fun main() {
    val manager = TaskManager().apply {
        tasks.add(Task(1, "Learn scope functions", done = true))
        tasks.add(Task(2, "Refactor with apply"))
    }.also {
        println("Manager ready with ${it.tasks.size} tasks")
    }

    println(buildReport(manager))
}
```

Output:

```text
Manager ready with 2 tasks
==============================
TASK REPORT
==============================
1. [x] Learn scope functions
2. [ ] Refactor with apply
==============================
Total: 2
```

**Commentary.**
- `TaskManager().apply { … }` configures the new manager (seeding tasks) and returns it; `.also { … }` then logs *without* breaking the chain — the manager still flows into `manager`. This is the canonical `apply`-then-`also` combo.
- `buildReport` uses `buildString { … }`, which gives a `StringBuilder` as `this` (a *lambda with receiver* — the subject of Chapter 17). Inside, `"=".repeat(30)` builds the border; the earlier version of this guide wrote `"=" * 30`, which does **not** compile — Kotlin's `String` has no `times` operator. Always use `repeat`.
- Notice how little glue code there is: no temporary variables, no manual `StringBuilder` juggling. That readability is exactly what scope functions and builders buy you.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Scope function** | `let`/`run`/`with`/`apply`/`also` — run a block in an object's context. |
| **Receiver (`this`)** | The object exposed as `this` (in `run`/`with`/`apply`). |
| **`it`** | The object exposed as an argument (in `let`/`also`). |
| **`apply`** | Configure an object; returns the object. |
| **`also`** | Side effect on an object; returns the object. |
| **`let`** | Transform / null-handle; returns block result. |
| **`run` / `with`** | Compute from an object's members; return block result. |
| **`takeIf` / `takeUnless`** | Return the object or `null` based on a predicate. |
| **let-elvis trap** | `?.let{}?:x` running `x` when the block (not the receiver) is null. |

### What's next

You can shape and configure objects fluently. Now for the big one: **[Ch.15 — Coroutines & Flow](#chapter-15--coroutines--flow)** brings asynchronous programming — running many tasks concurrently without blocking threads — and introduces `Flow` for streams of values. It's the feature that powers modern Kotlin backends and Android apps.

[↑ back to top](#chapter-14--scope-functions)


---

## Chapter 15 — Coroutines & Flow

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.7 — Null Safety](#chapter-7--null-safety), [Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features)

**Learning objectives** — after this chapter you will be able to:

- Explain the difference between *blocking* and *suspending*, and why it matters.
- Write `suspend` functions and run them with `launch`, `async`/`await`, and `runBlocking`.
- Structure concurrent work safely with `coroutineScope` and dispatchers.
- Cancel coroutines cooperatively and handle exceptions correctly.
- Model streams of values with `Flow`, and shared state with `StateFlow`.

> This chapter covers coroutines end-to-end and *introduces* `Flow`/`StateFlow`. Two Part-5 chapters go deeper: **[Ch.26 — Flow in Depth](#chapter-26--flow-in-depth)** (operators, hot/cold, backpressure) and **[Ch.27 — Advanced Coroutines & Concurrency](#chapter-27--advanced-coroutines--concurrency)** (shared state, `Mutex`, actors, custom contexts).

**In this chapter**

- [15.1 The problem: blocking vs suspending](#151-the-problem-blocking-vs-suspending)
- [15.2 Setup and your first coroutine](#152-setup-and-your-first-coroutine)
- [15.3 `suspend` functions](#153-suspend-functions)
- [15.4 Concurrency with `async`/`await`](#154-concurrency-with-asyncawait)
- [15.5 Structured concurrency and scopes](#155-structured-concurrency-and-scopes)
- [15.6 Dispatchers and `withContext`](#156-dispatchers-and-withcontext)
- [15.7 Cancellation](#157-cancellation)
- [15.8 Exception handling](#158-exception-handling)
- [15.9 `Flow`: streams of values](#159-flow-streams-of-values)
- [15.10 `StateFlow`: observable state](#1510-stateflow-observable-state)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-async-persistence-and-live-state) · Glossary · What's next

---

### 15.1 The problem: blocking vs suspending

Programs constantly wait — for a network response, a database query, a file read. The naive approach **blocks** a thread: the thread sits idle, doing nothing, until the wait ends. Threads are expensive (each costs ~1 MB of memory and OS scheduling), so blocking thousands of them to wait doesn't scale. A server that blocks one thread per request falls over under load.

Coroutines offer a better model: **suspending**. A `suspend`ing function can *pause* at a waiting point and **free its thread** to do other work, then *resume* later — possibly on a different thread — when the wait is over. No thread sits idle. You can run hundreds of thousands of coroutines on a handful of threads.

The mental picture: blocking is standing in line holding a phone booth you're not using; suspending is stepping aside so others can use the booth, and coming back when your call connects. Same waiting, vastly better resource use.

> ☕ **Coming from Java** — Coroutines are Kotlin's answer to `Thread`, `ExecutorService`, `CompletableFuture`, and reactive libraries like RxJava — but they read like ordinary sequential code. There's no callback pyramid and no `.thenCompose(...)` chains; you write `val x = fetch()` and the *suspension* happens invisibly. The key new guarantee, **structured concurrency**, has no direct Java equivalent (§15.5).

### 15.2 Setup and your first coroutine

Add the coroutines library to `build.gradle.kts` (Chapter 19 covers Gradle):

```kotlin
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.11.0")
}
```

The simplest program: `runBlocking` bridges the normal blocking world into the coroutine world, and `launch` starts a coroutine that runs concurrently.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {         // this block is a coroutine scope
    launch {                        // start a new coroutine, running concurrently
        delay(1000L)                // suspend for 1s (does NOT block the thread)
        println("World!")
    }
    println("Hello,")               // runs immediately, while launch is delayed
}
```

Output:

```text
Hello,
World!
```

`println("Hello,")` runs first; `launch`'s coroutine suspends at `delay` (releasing the thread), and after one second prints "World!". Crucially, `delay` **suspends** — unlike `Thread.sleep`, it doesn't block the underlying thread.

> ⚠️ **Gotcha** — `runBlocking` really does *block* its calling thread until everything inside finishes — it's the one deliberate bridge from blocking code (like `main` or a test) into coroutines. Use it at the *edges* of your program, never deep inside coroutine code (blocking a coroutine's thread defeats the purpose).

### 15.3 `suspend` functions

A function that can suspend is marked **`suspend`**. It can call other suspend functions (like `delay`), and can only be called from a coroutine or another suspend function.

```kotlin
import kotlinx.coroutines.*

suspend fun fetchUser(): String {
    delay(1000L)          // simulate a network call
    return "User data"
}

fun main() = runBlocking {
    println("Fetching...")
    val data = fetchUser()   // looks sequential; suspends here without blocking
    println(data)
}
```

The beauty is that `val data = fetchUser()` *reads* like ordinary blocking code, but under the hood the thread is freed during the wait.

> ⚙️ **Under the hood — the state machine.** How can a function "pause and resume"? The compiler transforms every `suspend` function into a **state machine**. It adds a hidden parameter — a `Continuation` (a callback capturing "what to do next") — and splits the function body at each suspension point into numbered states. When the function suspends, it saves its state and *returns*; when the awaited work completes, the `Continuation` is invoked to resume at the next state. So a coroutine that's "waiting" is not a parked thread — it's a small heap object holding a state number and local variables. That's why suspension is cheap and why you can have a million coroutines but only a few threads.

### 15.4 Concurrency with `async`/`await`

`launch` starts a coroutine that returns no result (fire-and-forget). When you need a *result*, use **`async`**, which returns a `Deferred<T>` — a promise of a future value you retrieve with **`await()`**.

The payoff is **concurrency**. Run independent work at the same time instead of one-after-another:

```kotlin
import kotlinx.coroutines.*

suspend fun fetchUser(): String { delay(1000L); return "User" }
suspend fun fetchPosts(): String { delay(1000L); return "Posts" }

fun main() = runBlocking {
    val time = System.currentTimeMillis()

    val user = async { fetchUser() }    // starts immediately
    val posts = async { fetchPosts() }  // starts immediately, alongside the first

    println("${user.await()} + ${posts.await()}")   // wait for both
    println("Took ~${System.currentTimeMillis() - time}ms")   // ~1000ms, NOT 2000ms
}
```

Both fetches run concurrently, so the total is about **1 second**, not two. Had we written `val user = fetchUser(); val posts = fetchPosts()` (plain sequential calls), it would take two seconds.

> ⚠️ **Gotcha** — An exception inside an `async` block is thrown when you call `await()`, not when it happens. If you `async { }` and never `await()`, an exception can be silently lost. Always `await` your `Deferred`s (structured concurrency, next, largely handles this for you).

### 15.5 Structured concurrency and scopes

Every coroutine runs within a **`CoroutineScope`**, and this gives Kotlin its signature safety feature: **structured concurrency**. The rule is simple and powerful: *a scope does not complete until all coroutines launched inside it complete.* Children can't outlive their parent; if the parent is cancelled, all children are cancelled; if a child fails, the parent knows.

The `coroutineScope { }` builder creates such a scope inside a suspend function:

```kotlin
import kotlinx.coroutines.*

suspend fun fetchProfile(): String = coroutineScope {   // scope: waits for all children
    val name = async { delay(500); "Alice" }
    val bio = async { delay(500); "Kotlin dev" }
    "${name.await()} — ${bio.await()}"                    // both done before we return
}

fun main() = runBlocking {
    println(fetchProfile())   // → Alice — Kotlin dev  (after ~500ms)
}
```

`fetchProfile` cannot return until both `async` children finish — the scope guarantees it. This prevents leaked coroutines (work that keeps running after the function that started it returned) — a whole category of bugs that plague callback- and future-based code.

> ⚠️ **Gotcha — avoid `GlobalScope`.** `GlobalScope.launch { }` starts a coroutine tied to the *whole application lifetime*, outside any structure. It's a classic leak: no parent cancels it, no scope waits for it. Prefer `coroutineScope`, or a scope tied to a lifecycle (like Android's `viewModelScope`, Chapter 22). Treat `GlobalScope` as a code smell.

### 15.6 Dispatchers and `withContext`

A **dispatcher** decides *which thread(s)* a coroutine runs on. The built-ins:

- **`Dispatchers.Default`** — a shared pool sized to the CPU cores, for CPU-intensive work (parsing, sorting).
- **`Dispatchers.IO`** — a larger pool for *blocking* I/O (file, network, JDBC).
- **`Dispatchers.Main`** — the UI thread (Android/desktop); touch UI only here.
- **`Dispatchers.Unconfined`** — starts in the caller's thread; rarely what you want.

Use **`withContext(dispatcher) { }`** to run a block on a specific dispatcher and get its result back — the standard way to move blocking work off your main thread:

```kotlin
import kotlinx.coroutines.*

suspend fun readConfig(): String = withContext(Dispatchers.IO) {
    // A blocking file read is OK here — it's on the IO pool, not the main thread
    delay(200)               // (stand-in for real blocking I/O)
    "config contents"
}
```

> 💡 **Idiom** — Wrap unavoidable *blocking* calls (a legacy JDBC driver, `File.readText()`) in `withContext(Dispatchers.IO) { … }`. This keeps the blocking confined to the IO pool and leaves your `Default`/`Main` threads free. A well-behaved `suspend` function never blocks the thread it's called on.

### 15.7 Cancellation

Coroutines are **cancellable**, but cancellation is **cooperative**: a coroutine only stops at a suspension point or when it checks for cancellation. Library suspend functions (`delay`, most I/O) check automatically; long CPU loops must check themselves.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        var i = 0
        while (isActive) {          // cooperate: stop when cancelled
            println("working ${i++}")
            delay(100)
        }
    }
    delay(350)
    println("cancelling")
    job.cancelAndJoin()             // cancel, then wait for it to finish
    println("done")
}
```

Check cancellation with `isActive` (a Boolean), or call `ensureActive()`/`yield()` (which throw `CancellationException` if cancelled). A cancelled coroutine's `delay`/suspend calls throw `CancellationException` to unwind cleanly.

> ⚠️ **Gotcha — never swallow `CancellationException`.** Cancellation *works by throwing* `CancellationException` at suspension points. If you catch it in a broad `catch (e: Exception)` and don't rethrow, you break cancellation — the coroutine keeps running when it should stop.
> ```kotlin
> try {
>     doWork()
> } catch (e: CancellationException) {
>     throw e                  // ALWAYS rethrow cancellation
> } catch (e: Exception) {
>     handle(e)                // handle real errors only
> }
> ```
> Run mandatory cleanup in a `finally` block; if the cleanup itself must suspend, wrap it in `withContext(NonCancellable) { … }`.

### 15.8 Exception handling

In a `coroutineScope`, if one child fails, the exception propagates: the scope cancels its other children and rethrows. Often that's what you want ("if any part fails, fail the whole operation"). When you instead want failures **isolated** — one child failing shouldn't cancel its siblings — use **`supervisorScope`**:

```kotlin
import kotlinx.coroutines.*

suspend fun loadDashboard() = supervisorScope {
    val a = async { delay(100); "widget A" }
    val b = async<String> { throw RuntimeException("B failed") }

    println(a.await())                     // → widget A  (survives B's failure)
    val bResult = try { b.await() } catch (e: Exception) { "B unavailable" }
    println(bResult)                       // → B unavailable
}
```

For fire-and-forget `launch` coroutines whose exceptions would otherwise crash the scope, a `CoroutineExceptionHandler` in the context acts as a last-resort handler. But for most `async` code, a plain `try`/`catch` around `await()` (as above) is the clearest tool.

### 15.9 `Flow`: streams of values

A `suspend` function returns *one* value. A **`Flow<T>`** represents an asynchronous **stream** of values over time — think "a suspendable sequence." You build one with the `flow { }` builder and `emit`:

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun countdown(): Flow<Int> = flow {
    for (i in 3 downTo 1) {
        delay(300)
        emit(i)          // push a value into the stream
    }
    emit(0)
}

fun main() = runBlocking {
    countdown()
        .map { it * 10 }              // transform each value
        .filter { it > 0 }           // keep some
        .collect { println(it) }      // terminal: consume the stream
}
```

Output:

```text
30
20
10
```

A Flow is **cold**: nothing runs until a terminal operator like `collect` subscribes, and it runs *again* for each collector. The intermediate operators (`map`, `filter`, `transform`, …) are lazy, just like `Sequence` (Chapter 6) — but suspendable, so each step can `delay`, call the network, etc.

> ⚙️ **Under the hood** — A `Flow` is essentially *a suspend lambda that emits values to a collector*. `collect { }` provides the collector; the `flow { }` block runs and calls it for each `emit`. Operators like `map` wrap the upstream flow in a new one. Because it's all suspend functions, a Flow naturally handles **backpressure**: a slow collector simply suspends the producer at `emit` until it's ready. (Operators, hot flows, buffering, and `flowOn` get the deep treatment in [Ch.26](#chapter-26--flow-in-depth).)

### 15.10 `StateFlow`: observable state

A **`StateFlow<T>`** is a special *hot* flow that always holds a **current value** and emits updates to collectors — perfect for representing state that a UI (or anything) observes. You expose a read-only `StateFlow` and keep a private `MutableStateFlow` to update it:

```kotlin
import kotlinx.coroutines.flow.*

class Counter {
    private val _count = MutableStateFlow(0)          // mutable, private
    val count: StateFlow<Int> = _count.asStateFlow()  // read-only, public

    fun increment() { _count.value++ }                 // update the state
}
```

Anyone can read `counter.count.value` for the current value, or `collect` it to react to every change. This is the backbone of modern Android UI (Chapter 22): the ViewModel holds a `StateFlow` of UI state, and the screen re-renders whenever it changes.

> 💡 **Idiom** — The **`_state` / `state`** pair (private `MutableStateFlow` + public `StateFlow`) is the standard pattern: only the owner mutates state, everyone else observes. It's the reactive cousin of the encapsulation you did with `private var` in Chapter 8.

---

### Summary

- **Suspending** frees the thread during waits, so a few threads run huge numbers of coroutines — unlike **blocking**, which wastes a thread per wait.
- Mark pausable functions **`suspend`**; run them with **`launch`** (no result), **`async`/`await`** (result, concurrent), and bridge from blocking code with **`runBlocking`** (edges only).
- **Structured concurrency** (`coroutineScope`) ensures children complete before the scope does, and cancel/fail together — no leaks. Avoid **`GlobalScope`**.
- **Dispatchers** pick threads (`Default` CPU, `IO` blocking, `Main` UI); move blocking work with **`withContext(Dispatchers.IO)`**.
- **Cancellation is cooperative** (check `isActive`/`ensureActive`); **never swallow `CancellationException`** — rethrow it.
- Use **`coroutineScope`** to fail-together, **`supervisorScope`** to isolate child failures.
- **`Flow<T>`** is a cold, suspendable stream (`flow{}`/`emit`, operators, `collect`); **`StateFlow<T>`** is hot observable state (private `MutableStateFlow` + public `StateFlow`).
- **Under the hood**, `suspend` compiles to a **state machine** with a `Continuation`, which is why suspension is cheap.

### Self-check quiz

1. Why does suspending scale better than blocking?
   <details><summary>Answer</summary>A suspended coroutine releases its thread during the wait, so a few threads can serve many coroutines. Blocking pins a whole thread (expensive) per wait.</details>
2. What does `async`/`await` give you that sequential suspend calls don't?
   <details><summary>Answer</summary>Concurrency: `async` starts work immediately and runs multiple operations at once; `await()` collects results. Two 1s fetches finish in ~1s, not 2s.</details>
3. What guarantee does structured concurrency (`coroutineScope`) provide?
   <details><summary>Answer</summary>The scope won't complete until all coroutines launched in it complete; cancelling the scope cancels children, and a child failure propagates — no leaked/orphaned coroutines.</details>
4. Why must you rethrow `CancellationException`?
   <details><summary>Answer</summary>Cancellation is implemented by throwing it at suspension points; swallowing it in a broad `catch` breaks cancellation, letting the coroutine keep running.</details>
5. What makes a `Flow` "cold," and how does `StateFlow` differ?
   <details><summary>Answer</summary>A cold `Flow` runs only when collected, and re-runs per collector. `StateFlow` is hot: it always holds a current value and shares emissions with all collectors.</details>

### Exercises

**Exercise 15.1 — Concurrent fetch (guided).** Fetch three "sources" (each a 500ms `delay`) concurrently and combine their results; confirm it takes ~500ms, not 1500ms.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*

suspend fun fetch(name: String): String { delay(500); return "data-$name" }

fun main() = runBlocking {
    val t = System.currentTimeMillis()
    val results = coroutineScope {
        val a = async { fetch("A") }
        val b = async { fetch("B") }
        val c = async { fetch("C") }
        listOf(a.await(), b.await(), c.await())
    }
    println(results)                                   // → [data-A, data-B, data-C]
    println("~${(System.currentTimeMillis() - t) / 100 * 100}ms")   // ≈ 500ms
}
```

**Why this works:** the three `async`s start immediately and run concurrently inside the `coroutineScope`, so the total wait is roughly the *longest* single fetch (~500ms), not the sum. `coroutineScope` ensures all three finish before `results` is built.

</details>

**Exercise 15.2 — Cooperative cancellation.** Launch a coroutine that counts up every 200ms; cancel it after ~700ms and confirm it stops.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        var n = 0
        while (isActive) {
            println("tick $n")
            n++
            delay(200)
        }
    }
    delay(700)
    job.cancelAndJoin()
    println("stopped")
}
```

**Why this works:** the loop checks `isActive` and `delay` is a cancellable suspension point, so `cancelAndJoin()` stops the coroutine cleanly. It prints roughly `tick 0..3` then `stopped` (exact count depends on timing).

</details>

### Chapter project: async persistence and live state

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–15. We give the manager a `StateFlow` of tasks, off-thread `save()`, and a **concurrent** `loadAll()` that fetches two sources at once.

**Goal.** Make the Task Manager reactive and asynchronous: observable state, non-blocking persistence, and concurrent loading.

**Requirements.**
1. Expose `tasks: StateFlow<List<Task>>` (private `MutableStateFlow`).
2. `add(title)` updates the state immutably.
3. `save()` runs on `Dispatchers.IO`.
4. `loadAll()` fetches two sources **concurrently** with `async` inside a `coroutineScope`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

data class Task(val id: Int, val title: String, val done: Boolean = false)

class TaskManager {
    private val _tasks = MutableStateFlow<List<Task>>(emptyList())
    val tasks: StateFlow<List<Task>> = _tasks.asStateFlow()

    fun add(title: String) {
        val id = (_tasks.value.maxOfOrNull { it.id } ?: 0) + 1
        _tasks.value = _tasks.value + Task(id, title)   // immutable update
    }

    suspend fun save(): Unit = withContext(Dispatchers.IO) {
        delay(200)   // stand-in for a blocking disk/DB write, off the main thread
    }

    suspend fun loadAll(): List<Task> = coroutineScope {
        val local = async { fetchFrom("local", 300) }
        val remote = async { fetchFrom("remote", 300) }
        local.await() + remote.await()                   // both fetched concurrently
    }

    private suspend fun fetchFrom(source: String, ms: Long): List<Task> {
        delay(ms)
        return listOf(Task(0, "from $source"))
    }
}

fun main() = runBlocking {
    val manager = TaskManager()

    manager.add("Write chapter 15")
    manager.add("Review it")
    println("After add: ${manager.tasks.value.map { it.title }}")

    manager.save()
    println("Saved to disk (off the main thread)")

    val loaded = manager.loadAll()
    println("Loaded ${loaded.size} tasks: ${loaded.map { it.title }}")
}
```

Output:

```text
After add: [Write chapter 15, Review it]
Saved to disk (off the main thread)
Loaded 2 tasks: [from local, from remote]
```

**Commentary.**
- `tasks` is a `StateFlow` — the reactive successor to Chapter 8's plain list. `main` reads `tasks.value`, but a UI (Chapter 22) would `collect` it and re-render on every change. The private-`_tasks` / public-`tasks` pair keeps mutation encapsulated.
- `add` updates state with `_tasks.value + Task(...)` — a *new* list each time (immutable update), which is exactly what `StateFlow` and Compose expect.
- `save()` uses `withContext(Dispatchers.IO)` so the (simulated) blocking write never stalls the caller's thread.
- `loadAll()` runs the two `fetchFrom` calls **concurrently** via `async`. Each takes 300ms, but because they overlap, the whole load is ~300ms, not 600ms. The `coroutineScope` guarantees both finish (or the whole load fails) before returning — structured concurrency in action.
- In [Ch.20](#chapter-20--ktor-for-backend-development) this same manager gets a Ktor REST API, in [Ch.21](#chapter-21--database-access) `save`/`loadAll` hit a real database, and in [Ch.27](#chapter-27--advanced-coroutines--concurrency) we make it thread-safe under concurrent access.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Blocking** | Occupying a thread while waiting (expensive; doesn't scale). |
| **Suspending** | Pausing at a wait and freeing the thread; resuming later. |
| **`suspend`** | Marks a function that can pause/resume. |
| **`launch`** | Starts a coroutine with no result. |
| **`async` / `await`** | Starts a coroutine returning a `Deferred<T>` / retrieves its result. |
| **`runBlocking`** | Bridges blocking code into coroutines (use at edges). |
| **Structured concurrency** | Children complete within their scope; cancel/fail together. |
| **`coroutineScope` / `supervisorScope`** | Fail-together scope / failure-isolating scope. |
| **Dispatcher** | Chooses the thread(s): `Default` (CPU), `IO` (blocking), `Main` (UI). |
| **`withContext`** | Runs a block on a given dispatcher, returning its result. |
| **Cancellation** | Cooperative stopping via `isActive`/`CancellationException`. |
| **`Flow<T>`** | A cold, suspendable stream of values. |
| **`StateFlow<T>`** | A hot flow holding a current value; observable state. |
| **Continuation** | The compiler-generated callback capturing "what to do next" (the state machine). |

### What's next

You can run concurrent, cancellable, streaming code. But real programs also *fail* — networks drop, files vanish. **[Ch.16 — Exception Handling](#chapter-16--exception-handling)** covers `try`/`catch` as an expression, custom exceptions, `Result`/`runCatching`, and `use` for resources — including how error handling interacts with the coroutines you just learned.

[↑ back to top](#chapter-15--coroutines--flow)


---

## Chapter 16 — Exception Handling

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.7 — Null Safety](#chapter-7--null-safety)

**Learning objectives** — after this chapter you will be able to:

- Handle errors with `try`/`catch`/`finally`, and use `try` as an expression.
- Throw and define exceptions, and validate with `require`/`check`/`error`.
- Model failure *as a value* with `Result`/`runCatching`.
- Manage resources safely with `use`.

**In this chapter**

- [16.1 `try`, `catch`, `finally`](#161-try-catch-finally)
- [16.2 `try` as an expression](#162-try-as-an-expression)
- [16.3 Throwing and custom exceptions](#163-throwing-and-custom-exceptions)
- [16.4 `require`, `check`, `error`](#164-require-check-error)
- [16.5 No checked exceptions](#165-no-checked-exceptions)
- [16.6 `Result` and `runCatching`](#166-result-and-runcatching)
- [16.7 Resources with `use`](#167-resources-with-use)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-failure-as-a-value) · Glossary · What's next

---

### 16.1 `try`, `catch`, `finally`

An **exception** is Kotlin's way of signalling that something went wrong — a division by zero, a malformed number, a missing file. If nothing handles it, it propagates up and crashes the program. You handle it with `try`/`catch`, and use `finally` for cleanup that must run whether or not an error occurred:

```kotlin
fun main() {
    try {
        val result = 10 / 0            // throws ArithmeticException
        println(result)                 // never reached
    } catch (e: ArithmeticException) {
        println("Cannot divide by zero")
    } finally {
        println("This always runs")
    }
}
```

Output:

```text
Cannot divide by zero
This always runs
```

The `catch` block runs only if a matching exception is thrown; `finally` runs no matter what — success, caught exception, or even an uncaught one on its way out.

### 16.2 `try` as an expression

Like `if` and `when`, **`try` is an expression** in Kotlin — it returns a value (the last expression of whichever block completed). This makes "parse, or use a default" concise:

```kotlin
val number: Int = try {
    "123".toInt()
} catch (e: NumberFormatException) {
    0
}
println(number)   // → 123

val bad: Int = try { "abc".toInt() } catch (e: NumberFormatException) { -1 }
println(bad)      // → -1
```

You can catch several exception types with multiple `catch` blocks, checked top to bottom:

```kotlin
fun process(input: String) {
    try {
        val n = input.toInt()
        println(100 / n)
    } catch (e: NumberFormatException) {
        println("Not a number")
    } catch (e: ArithmeticException) {
        println("Division by zero")
    } catch (e: Exception) {          // catch-all, must be LAST
        println("Other error: ${e.message}")
    }
}
```

Order matters: put specific exceptions first and broad ones last, since the first matching `catch` wins.

### 16.3 Throwing and custom exceptions

You raise an exception with **`throw`**, and — because `throw` is also an expression — you can use it on the right of `?:` (as you did in Chapter 7):

```kotlin
fun requirePositive(n: Int): Int {
    if (n <= 0) throw IllegalArgumentException("must be positive, was $n")
    return n
}

val value = mapOf("a" to 1)["b"] ?: throw NoSuchElementException("key missing")
```

Define your own exception types by extending `Exception` (or a more specific subclass) — useful for domain-specific errors your callers can catch precisely:

```kotlin
class InsufficientFundsException(val shortfall: Double)
    : Exception("Short by $shortfall")

fun withdraw(balance: Double, amount: Double): Double {
    if (amount > balance) throw InsufficientFundsException(amount - balance)
    return balance - amount
}
```

### 16.4 `require`, `check`, `error`

For the common cases — validating arguments and state — the standard library gives you concise helpers that throw the *right* exception with a message:

- **`require(condition) { message }`** — throws `IllegalArgumentException` if false. For validating **arguments**.
- **`check(condition) { message }`** — throws `IllegalStateException` if false. For validating **state**.
- **`error(message)`** — always throws `IllegalStateException`. For "this should never happen" branches.

```kotlin
fun setAge(age: Int) {
    require(age in 0..150) { "Age out of range: $age" }   // bad argument
    println("Age set to $age")
}

fun main() {
    setAge(30)                 // → Age set to 30
    try { setAge(200) }
    catch (e: IllegalArgumentException) { println("Rejected: ${e.message}") }
    // → Rejected: Age out of range: 200
}
```

> 💡 **Idiom** — Prefer `require`/`check` over hand-written `if (…) throw …`. They express intent (argument vs state precondition), throw the conventional exception type, and their message lambda is only evaluated on failure (so it's cheap on the happy path).

### 16.5 No checked exceptions

A defining difference from Java: **Kotlin has no checked exceptions.** No function is forced to declare `throws`, and no caller is forced to catch. Every exception is effectively "unchecked."

```kotlin
// No `throws IOException` anywhere — Kotlin doesn't have them
fun readData(): String {
    // may throw an IOException at runtime; the compiler doesn't force handling
    return "data"
}
```

> ☕ **Coming from Java** — Java's checked exceptions force `try`/`catch` or `throws` on the call chain, which famously leads to boilerplate and `catch (IOException e) { /* ignored */ }` anti-patterns. Kotlin dropped them: you catch what you *choose* to handle. The trade-off is discipline — the compiler won't remind you an operation can fail, so you must know your APIs.

> ⚙️ **Under the hood** — At the bytecode level, Java's "checked" is only a compiler rule, not a JVM one, so Kotlin simply doesn't enforce it. When you *do* need a Kotlin function to advertise a checked exception to **Java** callers (e.g., so Java's `try`-with-resources or `throws` works), annotate it with **`@Throws(IOException::class)`** (Chapter 18).

### 16.6 `Result` and `runCatching`

Sometimes you don't want to `throw` at all — you want failure to be an ordinary **value** you can pass around, transform, and handle later. Kotlin's **`Result<T>`** type and **`runCatching { }`** builder do exactly that: `runCatching` runs a block and captures either its result *or* the exception it threw, without propagating it.

```kotlin
fun parse(input: String): Result<Int> = runCatching { input.toInt() }

fun main() {
    val good = parse("42")     // Result.success(42)
    val bad = parse("oops")    // Result.failure(NumberFormatException)

    println(good.getOrDefault(-1))   // → 42
    println(bad.getOrDefault(-1))    // → -1

    // Transform and react without ever catching manually:
    parse("100")
        .map { it * 2 }              // success(200); no-op on failure
        .onSuccess { println("Got $it") }   // → Got 200
        .onFailure { println("Failed: ${it.message}") }
}
```

`Result` has a rich API: `getOrNull()`, `getOrDefault(x)`, `getOrElse { }`, `map { }`, `mapCatching { }`, `fold(onSuccess, onFailure)`, `onSuccess { }`, `onFailure { }`. It turns error handling into a composable pipeline.

> ⚠️ **Gotcha — don't over-catch, especially in coroutines.** `runCatching` (and a broad `catch (e: Throwable)`) also captures `CancellationException`, which — as you saw in Chapter 15 — must propagate for coroutine cancellation to work. Inside coroutines, either avoid `runCatching` around cancellable calls or rethrow cancellation explicitly. Also avoid using exceptions for *ordinary control flow* (they're comparatively slow and obscure intent) — a nullable or a `Result` is usually clearer.

### 16.7 Resources with `use`

Anything that must be *closed* — a file, a socket, a database connection (all implement `Closeable`/`AutoCloseable`) — should be closed even if an error occurs. The **`use`** function does this for you: it runs your block and guarantees `close()` afterward, success or failure.

```kotlin
import java.io.StringReader

fun main() {
    val text = StringReader("hello\nworld").buffered().use { reader ->
        reader.readText()      // reader is auto-closed when this block ends
    }
    println(text)              // → hello\nworld (two lines)
}
```

Whatever happens inside the block, `use` closes the resource — no leaked file handles, no forgotten `close()`.

> ☕ **Coming from Java** — `use { }` is Kotlin's **try-with-resources**. Instead of `try (Reader r = …) { … }`, you write `reader.use { … }`. It's an ordinary inline function, not special syntax, so it works with any `Closeable`.

---

### Summary

- **`try`/`catch`/`finally`** handles exceptions; `finally` always runs. **`try` is an expression** returning a value.
- Use **multiple `catch`** blocks specific-to-general (first match wins). **`throw`** is an expression (usable with `?:`). Define domain errors by extending `Exception`.
- **`require`** (bad argument → `IllegalArgumentException`), **`check`** (bad state → `IllegalStateException`), and **`error`** (always throws) are the idiomatic validators.
- Kotlin has **no checked exceptions** — you catch what you choose; use **`@Throws`** for Java interop.
- **`Result`/`runCatching`** model failure as a value you can `map`/`fold`/`getOrElse` — a composable alternative to `try`/`catch`. Beware capturing `CancellationException` in coroutines.
- **`use`** guarantees a `Closeable` is closed (Kotlin's try-with-resources).

### Self-check quiz

1. When does a `finally` block run?
   <details><summary>Answer</summary>Always — after the `try` completes normally, after a caught exception is handled, and even while an uncaught exception is propagating out.</details>
2. What's the difference between `require` and `check`?
   <details><summary>Answer</summary>`require` validates *arguments* and throws `IllegalArgumentException`; `check` validates *state* and throws `IllegalStateException`.</details>
3. How does `Result`/`runCatching` differ from `try`/`catch`?
   <details><summary>Answer</summary>It turns success/failure into a value (`Result<T>`) you can pass around and transform with `map`/`fold`/`getOrElse`, instead of controlling flow with `catch`.</details>
4. Why is `runCatching` risky inside a coroutine?
   <details><summary>Answer</summary>It captures *all* throwables including `CancellationException`, which must propagate for cancellation to work — swallowing it breaks coroutine cancellation.</details>

### Exercises

**Exercise 16.1 — Safe parse (guided).** Write `readNumberSafely(input, default)` that parses an int, rejects negatives via `require`, and returns `default` on any failure.

<details><summary>Show solution</summary>

```kotlin
fun readNumberSafely(input: String, default: Int = 0): Int {
    return try {
        val n = input.trim().toInt()
        require(n >= 0) { "must be non-negative" }
        n
    } catch (e: NumberFormatException) {
        println("bad format → $default")
        default
    } catch (e: IllegalArgumentException) {
        println("${e.message} → $default")
        default
    }
}

fun main() {
    println(readNumberSafely("42"))     // → 42
    println(readNumberSafely("abc"))    // → bad format → 0  then  0
    println(readNumberSafely("-5"))     // → must be non-negative → 0  then  0
    println(readNumberSafely("  9 "))   // → 9
}
```

**Why this works:** `try` is used as an expression returning the number or the default. `toInt()` throwing `NumberFormatException` and `require` throwing `IllegalArgumentException` are caught by separate blocks with tailored messages. `trim()` tolerates surrounding spaces.

</details>

**Exercise 16.2 — Result pipeline.** Using `runCatching`, write a function that parses a string to an int and returns its square, or `-1` on any failure — without a `try`/`catch`.

<details><summary>Show solution</summary>

```kotlin
fun parseSquare(input: String): Int =
    runCatching { input.toInt() }
        .map { it * it }
        .getOrElse { -1 }

fun main() {
    println(parseSquare("6"))     // → 36
    println(parseSquare("x"))     // → -1
}
```

**Why this works:** `runCatching` captures the parse outcome as a `Result`; `map` squares a success (and does nothing to a failure); `getOrElse` supplies `-1` if the `Result` is a failure. No manual `catch` anywhere — failure flows through as data.

</details>

### Chapter project: failure as a value

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–16. We validate input with `require` and expose a `Result`-returning API so callers handle failure without `try`/`catch`.

**Goal.** Make `add` reject blank titles, and offer a `tryAdd` that returns a `Result<Task>`.

**Requirements.**
1. `add(title)` validates with `require` (throws on blank).
2. `tryAdd(title): Result<Task>` wraps `add` in `runCatching`.
3. `main` handles both success and failure through the `Result` API — no `try`/`catch`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
data class Task(val id: Int, val title: String)

class TaskManager {
    private val tasks = mutableListOf<Task>()

    fun add(title: String): Task {
        require(title.isNotBlank()) { "Title must not be blank" }
        val task = Task(tasks.size + 1, title)
        tasks.add(task)
        return task
    }

    fun tryAdd(title: String): Result<Task> = runCatching { add(title) }

    fun all(): List<Task> = tasks.toList()
}

fun main() {
    val manager = TaskManager()

    val ok = manager.tryAdd("Write chapter 16")
    val bad = manager.tryAdd("   ")

    println(ok.map { it.title }.getOrElse { "error: ${it.message}" })   // → Write chapter 16
    println(bad.map { it.title }.getOrElse { "error: ${it.message}" })  // → error: Title must not be blank

    bad.onFailure { println("Rejected: ${it.message}") }                 // → Rejected: Title must not be blank

    println("Tasks: ${manager.all().map { it.title }}")                  // → Tasks: [Write chapter 16]
}
```

Output:

```text
Write chapter 16
error: Title must not be blank
Rejected: Title must not be blank
Tasks: [Write chapter 16]
```

**Commentary.**
- `add` uses `require` to enforce a precondition: a blank title is an *argument* error, so `IllegalArgumentException` is exactly right, and the lambda message is only built on failure.
- `tryAdd` converts that throwing API into a **value-returning** one with `runCatching`. Callers who prefer exceptions use `add`; callers who prefer values use `tryAdd` and pipe the `Result` through `map`/`getOrElse`/`onFailure` — no `try`/`catch` in sight.
- Only the valid task ends up in the list; the blank one failed *before* being added. This is the robust-persistence groundwork for [Ch.20](#chapter-20--ktor-for-backend-development)/[Ch.21](#chapter-21--database-access), where `tryAdd`-style results map cleanly onto HTTP status codes and database transactions.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Exception** | A signal that something went wrong, propagating until caught. |
| **`try`/`catch`/`finally`** | Handle exceptions; `finally` always runs; `try` is an expression. |
| **`throw`** | Raise an exception (also an expression). |
| **Custom exception** | A user-defined type extending `Exception`. |
| **`require` / `check` / `error`** | Validate arguments / state / "impossible" branches. |
| **Checked exception** | A compiler-enforced `throws` (Java only; Kotlin has none). |
| **`@Throws`** | Advertises an exception to Java callers. |
| **`Result<T>`** | A value holding either a success or a failure. |
| **`runCatching`** | Runs a block, capturing success/exception into a `Result`. |
| **`use`** | Runs a block and guarantees a `Closeable` is closed. |

### What's next

You can handle failure robustly. **[Ch.17 — Type-Safe Builders & DSLs](#chapter-17--type-safe-builders--dsls)** closes Part 3 with one of Kotlin's most distinctive features: *lambdas with receiver*, which let you build fluent, type-safe mini-languages — the machinery behind Gradle scripts, Ktor routing, and Jetpack Compose.

[↑ back to top](#chapter-16--exception-handling)


---

## Chapter 17 — Type-Safe Builders & DSLs

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.14 — Scope Functions](#chapter-14--scope-functions)

**Learning objectives** — after this chapter you will be able to:

- Understand *lambdas with receiver* — the feature behind Kotlin DSLs.
- Build a small, type-safe domain-specific language.
- Use `@DslMarker` to keep nested DSL scopes unambiguous.
- Recognise the DSLs you already use (Gradle, Ktor, Compose) for what they are.

**In this chapter**

- [17.1 Lambdas with receiver](#171-lambdas-with-receiver)
- [17.2 Building a DSL](#172-building-a-dsl)
- [17.3 `@DslMarker`: taming nested scopes](#173-dslmarker-taming-nested-scopes)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-task-seeding-dsl) · Glossary · What's next

---

### 17.1 Lambdas with receiver

You've met two lambda shapes: `(T) -> R` (a parameter you call as `block(x)`) and, in scope functions, something subtly different. `apply` let you write `person.apply { name = "A" }` and access `name` *directly*, as if you were inside the `Person`. That's a **lambda with receiver** — a function type written **`T.() -> R`**, where inside the lambda `this` is a `T`.

Compare the two:

```kotlin
val regular: (StringBuilder) -> Unit = { sb -> sb.append("hi") }   // sb is a parameter
val withReceiver: StringBuilder.() -> Unit = { append("hi") }      // `this` is the StringBuilder
```

In `withReceiver`, `append` resolves against the implicit receiver `this: StringBuilder`. You call such a lambda *on* a receiver:

```kotlin
fun buildText(block: StringBuilder.() -> Unit): String {
    val sb = StringBuilder()
    sb.block()          // invoke the lambda with sb as `this`
    return sb.toString()
}

fun main() {
    val text = buildText {
        append("Hello")     // `this` is the StringBuilder
        append(", ")
        append("DSL!")
    }
    println(text)   // → Hello, DSL!
}
```

This one feature — letting a lambda run *as if inside* a receiver object — is the entire foundation of Kotlin DSLs. (It's also how the standard `buildString`, `apply`, `run`, and `with` work.)

> ⚙️ **Under the hood** — A receiver lambda `T.() -> R` compiles to the *same* thing as an extension function: a function whose first, hidden argument is the receiver. `sb.block()` passes `sb` as that hidden receiver, so inside the lambda every unqualified call is dispatched on it. No new runtime machinery — it's the extension-function trick from Chapter 11 applied to lambdas.

### 17.2 Building a DSL

A **DSL** (domain-specific language) is an API designed to read like a little language for one domain — HTML, build configs, UI layouts. Receiver lambdas let you nest builder scopes so the code *looks* like structured data. Here's a compact HTML builder:

```kotlin
class Tag(val name: String) {
    private val children = mutableListOf<Tag>()
    var text: String = ""

    fun tag(name: String, init: Tag.() -> Unit) {
        children.add(Tag(name).apply(init))   // create child, configure it, keep it
    }

    override fun toString(): String {
        val inner = if (children.isEmpty()) text else children.joinToString("")
        return "<$name>$inner</$name>"
    }
}

fun html(init: Tag.() -> Unit): Tag = Tag("html").apply(init)

fun main() {
    val page = html {
        tag("body") {
            tag("h1") { text = "Welcome" }
            tag("p") { text = "Built with a DSL" }
        }
    }
    println(page)
}
```

Output:

```text
<html><body><h1>Welcome</h1><p>Built with a DSL</p></body></html>
```

Read the `html { … }` block: it *looks* like HTML structure, but it's fully type-safe Kotlin — the compiler checks every `tag` call, and you get autocompletion inside each scope. Each `tag(name) { … }` takes a receiver lambda, creates a child `Tag`, configures it with `apply(init)`, and nests it. The nesting of receiver lambdas *is* the nesting of the markup.

> ☕ **Coming from Java** — This replaces the classic **builder pattern** (`new HtmlBuilder().body().h1("Welcome").end()...`) with something far cleaner and impossible to misuse (you can't put an `<h1>` outside a `<body>` if the types don't allow it). Java has no equivalent to receiver lambdas, which is why Java builders are so much more verbose.

### 17.3 `@DslMarker`: taming nested scopes

There's a subtle hazard in nested DSLs. Inside the innermost `tag("h1") { … }`, *two* receivers are in scope: the `h1` tag and the enclosing `body` tag. So you could accidentally call the *outer* `tag(...)` from the inner block, producing confusing structure — the compiler wouldn't stop you.

**`@DslMarker`** fixes this. You define a marker annotation, apply it to your DSL classes, and Kotlin then forbids calling a method on an *outer* implicit receiver from an inner scope — you'd have to qualify it explicitly (`this@html.tag(...)`). This makes nested DSLs safe and unambiguous:

```kotlin
@DslMarker
annotation class HtmlDsl

@HtmlDsl
class Tag(val name: String) {
    // ... same as before ...
    fun tag(name: String, init: Tag.() -> Unit) { /* ... */ }
}
```

With `@HtmlDsl` applied, an inner `tag { … }` can only see its *own* receiver's members — accidental cross-scope calls become compile errors.

> 💡 **Idiom** — Always add a `@DslMarker` annotation to a multi-level DSL. It's a small amount of boilerplate that turns a whole class of subtle scoping bugs into compile errors. Kotlin's own DSLs (Ktor routing, Gradle) all use marker annotations.

> ⚠️ **Gotcha** — DSLs are powerful and *easy to overuse*. A DSL earns its complexity only when it's used a lot and genuinely reads better than plain function calls. A one-off configuration is usually clearer as named arguments or an `apply` block. Reach for a full DSL for real "languages" (routing tables, UI trees, build scripts), not for every builder.

---

### Summary

- A **lambda with receiver** (`T.() -> R`) runs with an implicit `this: T`, so its body reads as if written *inside* the receiver — the foundation of every Kotlin DSL. Under the hood it's the extension-function mechanism.
- **DSLs** nest receiver-lambda builder scopes so code reads like structured data (HTML, config, UI) while staying fully type-safe.
- **`@DslMarker`** prevents accidental calls to an *outer* receiver from an inner scope, making nested DSLs unambiguous.
- Use DSLs where they genuinely pay off (repeated, structural APIs); don't over-engineer simple configuration.

### Self-check quiz

1. What's the difference between `(T) -> R` and `T.() -> R`?
   <details><summary>Answer</summary>In `(T) -> R` the object is a parameter you name; in `T.() -> R` (a lambda with receiver) the object is the implicit `this`, so its members are accessible unqualified.</details>
2. What makes a Kotlin DSL "type-safe"?
   <details><summary>Answer</summary>It's ordinary Kotlin — the compiler checks every call, and the receiver types constrain what's valid in each scope, with full autocompletion. Invalid structure is a compile error.</details>
3. What problem does `@DslMarker` solve?
   <details><summary>Answer</summary>In nested DSLs multiple receivers are in scope; `@DslMarker` forbids implicitly calling an outer receiver's members from an inner scope, preventing accidental cross-scope calls.</details>
4. Which everyday Kotlin tools are built as DSLs?
   <details><summary>Answer</summary>Gradle Kotlin DSL build scripts, Ktor's `routing { }`, Jetpack Compose's `@Composable` layouts, and `buildString`/`kotlinx.html`.</details>

### Exercises

**Exercise 17.1 — Config DSL (guided).** Build a `server { host = ...; port = ... }` DSL that returns a configured object.

<details><summary>Show solution</summary>

```kotlin
class ServerConfig {
    var host: String = "localhost"
    var port: Int = 8080
    override fun toString() = "Server($host:$port)"
}

fun server(init: ServerConfig.() -> Unit): ServerConfig = ServerConfig().apply(init)

fun main() {
    val config = server {
        host = "example.com"
        port = 443
    }
    println(config)   // → Server(example.com:443)
}
```

**Why this works:** `server` takes a `ServerConfig.() -> Unit` receiver lambda and runs it via `apply`, so inside the block `host` and `port` refer to the new `ServerConfig`'s properties. `apply` returns the configured object.

</details>

**Exercise 17.2 — Menu DSL.** Build a `menu { item("A"); item("B") }` DSL that collects items into a `List<String>`.

<details><summary>Show solution</summary>

```kotlin
class MenuBuilder {
    private val items = mutableListOf<String>()
    fun item(name: String) { items.add(name) }
    fun build(): List<String> = items.toList()
}

fun menu(init: MenuBuilder.() -> Unit): List<String> =
    MenuBuilder().apply(init).build()

fun main() {
    val m = menu {
        item("Home")
        item("About")
        item("Contact")
    }
    println(m)   // → [Home, About, Contact]
}
```

**Why this works:** each `item(...)` call (dispatched on the `MenuBuilder` receiver) appends to the internal list; `menu` runs the block via `apply` and returns the built list. The block reads like a declarative menu.

</details>

### Chapter project: a task-seeding DSL

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–17. We add a small, `@DslMarker`-protected DSL for declaring an initial set of tasks — handy for seeding tests and demos.

**Goal.** Write a `tasks { task("...") { priority = HIGH } }` DSL that builds a `List<Task>`.

**Requirements.**
1. A `Priority` enum and a `Task` with a priority.
2. `@DslMarker`-annotated builder classes.
3. A `tasks { }` entry function; each `task(title) { }` can set a priority (default MEDIUM).

<details><summary>Show reference solution + commentary</summary>

```kotlin
enum class Priority { LOW, MEDIUM, HIGH }

data class Task(val id: Int, val title: String, val priority: Priority = Priority.MEDIUM)

@DslMarker
annotation class TaskDsl

@TaskDsl
class TaskBuilder(var title: String) {
    var priority: Priority = Priority.MEDIUM
}

@TaskDsl
class TaskListBuilder {
    private val built = mutableListOf<Task>()
    private var nextId = 1

    fun task(title: String, init: TaskBuilder.() -> Unit = {}) {
        val b = TaskBuilder(title).apply(init)
        built.add(Task(nextId++, b.title, b.priority))
    }

    fun build(): List<Task> = built.toList()
}

fun tasks(init: TaskListBuilder.() -> Unit): List<Task> =
    TaskListBuilder().apply(init).build()

fun main() {
    val seeded = tasks {
        task("Write the DSL chapter") { priority = Priority.HIGH }
        task("Buy coffee")                         // default priority
        task("Review PR") { priority = Priority.LOW }
    }
    seeded.forEach { println("#${it.id} ${it.title} [${it.priority}]") }
}
```

Output:

```text
#1 Write the DSL chapter [HIGH]
#2 Buy coffee [MEDIUM]
#3 Review PR [LOW]
```

**Commentary.**
- `tasks { … }` reads like a declarative task list, but it's type-safe Kotlin: `task(...)` is checked, `priority` autocompletes to the `Priority` enum, and misuse is a compile error.
- `task(title, init = {})` gives the inner configuration lambda a **default** (an empty block), so `task("Buy coffee")` with no braces works and takes the default `MEDIUM` priority — Chapter 5's default arguments meeting Chapter 17's receiver lambdas.
- `@TaskDsl` (via `@DslMarker`) prevents an inner `task { … }` block from accidentally calling the outer builder's `task(...)` — the nested-scope safety net.
- This DSL is a *seeding* convenience layered on top of the domain; it doesn't replace `TaskManager`. That's the right scope for a DSL — a focused, readable surface for one job.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Lambda with receiver** | A function type `T.() -> R` whose body has `this: T` implicitly. |
| **Receiver** | The implicit `this` object inside a receiver lambda. |
| **DSL** | A domain-specific mini-language built from nested builder scopes. |
| **Type-safe builder** | A DSL where the compiler checks structure and offers completion. |
| **`@DslMarker`** | An annotation restricting implicit access to outer receivers in nested DSLs. |

### What's next

That completes **Part 3 — Functional & Concurrent Kotlin**. You can compose properties, expressions, async streams, robust error handling, and expressive DSLs. **Part 4 turns to the real world, starting with [Ch.18 — Kotlin ↔ Java Interoperability](#chapter-18--kotlin--java-interoperability)** — how Kotlin and Java call each other seamlessly, so you can use the entire JVM ecosystem.

[↑ back to top](#chapter-17--type-safe-builders--dsls)


---

## Chapter 18 — Kotlin ↔ Java Interoperability

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.7 — Null Safety](#chapter-7--null-safety), [Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features)

**Learning objectives** — after this chapter you will be able to:

- Call Java code (libraries, collections, functional interfaces) from Kotlin.
- Handle Java's unknown nullability (platform types) safely.
- Make your Kotlin code pleasant to call from Java with the `@Jvm*` annotations.
- Bridge exceptions and static members across the two languages.

**In this chapter**

- [18.1 Calling Java from Kotlin](#181-calling-java-from-kotlin)
- [18.2 Platform types revisited](#182-platform-types-revisited)
- [18.3 Calling Kotlin from Java](#183-calling-kotlin-from-java)
- [18.4 The `@Jvm*` annotations](#184-the-jvm-annotations)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-wrapping-a-java-library) · Glossary · What's next

---

### 18.1 Calling Java from Kotlin

Kotlin's headline promise is **100% interoperability with Java**: any Java class, method, or library is usable from Kotlin with no wrappers. This is why Kotlin arrived with a mature ecosystem — the entire JVM world was instantly available.

You've been using Java from Kotlin already without noticing — `String`, `Math`, and the collection types are Java classes:

```kotlin
import java.util.ArrayList
import java.time.LocalDate

fun main() {
    val list = ArrayList<String>()   // java.util.ArrayList
    list.add("Kotlin")
    list.add("Java")

    val today = LocalDate.now()      // java.time.LocalDate
    println(today.plusDays(7))

    println(Math.sqrt(16.0))         // java.lang.Math static method → 4.0
}
```

Java **getters/setters** are exposed as Kotlin properties: a Java `getName()`/`setName()` pair can be used as `obj.name`. And Java **functional interfaces** (a single abstract method — `Runnable`, `Comparator`, listeners) accept a Kotlin lambda directly, thanks to **SAM conversion**:

```kotlin
val runnable = Runnable { println("Running!") }   // lambda → Runnable
val comparator = Comparator<String> { a, b -> a.length - b.length }
```

### 18.2 Platform types revisited

The one friction point is **nullability**. Java doesn't encode null in its types, so when a Java method returns `String`, Kotlin can't know whether it might be null. As you saw in [Ch.7](#chapter-7--null-safety), Kotlin represents such values as **platform types** (shown as `String!`), where it relaxes null checks and trusts you.

```kotlin
// Suppose a Java method:  public String getName()   (might return null)
val name = javaObject.name        // type is String! (platform type)

val len1 = name.length            // allowed — but NPE at runtime if it was null
val len2 = name?.length ?: 0      // you chose to treat it as nullable — safe
```

The two defenses (recap from Chapter 7): **pin the type explicitly** at the boundary (`val name: String? = javaObject.name`), or rely on **Java nullability annotations** (`@Nullable`/`@NotNull`) if the Java code has them — Kotlin reads them and drops the platform type.

> ⚠️ **Gotcha** — The most common interop bug is a platform-type NPE: you treated a Java value as non-null, and one day it was null. When consuming an un-annotated Java API, decide the nullability *at the boundary* with an explicit `String?`/`String`, rather than letting platform types propagate deep into your Kotlin code.

### 18.3 Calling Kotlin from Java

The reverse direction — Java calling Kotlin — mostly "just works," because Kotlin compiles to ordinary JVM bytecode. A Kotlin class is a normal class to Java; a Kotlin property becomes `getX()`/`setX()` methods. But a few Kotlin features have no Java equivalent, and knowing how they *appear* to Java matters when you write Kotlin that Java will consume.

**Top-level functions** don't belong to any class in Kotlin, but the JVM requires a class — so the compiler puts them in a synthetic class named after the file. `greet()` in `Utils.kt` becomes a static method on `UtilsKt`:

```kotlin
// File: Utils.kt
package com.example

fun greet(name: String) = println("Hello, $name")
```

```java
// From Java:
com.example.UtilsKt.greet("Alice");   // note the "Kt" suffix
```

> ⚙️ **Under the hood** — This `…Kt` class is the same mechanism as `MainKt` from Chapter 1: top-level declarations need a home class, so the compiler generates one named `<FileName>Kt`. You can rename it for Java callers with `@file:JvmName("Utils")` at the top of the file, so Java writes `Utils.greet(...)`.

### 18.4 The `@Jvm*` annotations

Several Kotlin features compile to bytecode that's awkward to call from Java. A family of annotations makes them Java-friendly:

**`@JvmStatic`** — makes a `companion object` / `object` member a true static method, so Java calls it as `MyClass.foo()` instead of `MyClass.Companion.foo()`:

```kotlin
class MathUtils {
    companion object {
        @JvmStatic
        fun square(n: Int) = n * n
    }
}
// Java: MathUtils.square(5);   (without @JvmStatic: MathUtils.Companion.square(5))
```

**`@JvmField`** — exposes a property as a plain public field (no getter/setter), useful for constants and interop:

```kotlin
class Config {
    companion object {
        @JvmField val MAX_RETRIES = 3   // Java: Config.MAX_RETRIES
    }
}
```

**`@JvmOverloads`** — generates the telescoping overloads for a function with default arguments, so Java (which has no default args) can call it with fewer arguments:

```kotlin
@JvmOverloads
fun connect(host: String, port: Int = 8080, timeout: Int = 30) { /* ... */ }
// Java gets: connect(host), connect(host, port), connect(host, port, timeout)
```

**`@JvmName`** — renames the generated method/class (to avoid clashes or improve the Java-facing name). **`@Throws`** — declares a checked exception so Java's `throws`/try-with-resources see it (Kotlin has no checked exceptions, Chapter 16):

```kotlin
@Throws(java.io.IOException::class)
fun readFile(path: String): String { /* ... */ return "" }
// Java can now write: try { readFile(p); } catch (IOException e) { ... }
```

> ⚙️ **Under the hood** — `@JvmOverloads` literally generates extra methods in the bytecode (one per omittable parameter), each forwarding to the full version with the defaults filled in. Without it, Java sees only the single all-parameters method — because Kotlin's default-argument mechanism (the `$default` method + bitmask from Chapter 5) isn't something Java's call syntax can use.

> ⚠️ **Gotcha** — A `suspend` function (Chapter 15) is *not* directly callable from plain Java — it compiles to a method with a hidden `Continuation` parameter. To expose async Kotlin to Java, provide a non-suspend wrapper (e.g., returning a `CompletableFuture` via `future { }` from the coroutines-jdk8 integration).

---

### Summary

- Kotlin has **full Java interop**: use any Java class/library directly; Java getters/setters appear as Kotlin properties; Java functional interfaces accept lambdas (**SAM conversion**).
- Java values of unknown nullability become **platform types** (`String!`); pin them to `String?`/`String` at the boundary, or rely on Java `@Nullable`/`@NotNull`.
- Java calls Kotlin normally; **top-level functions** live in a synthetic `<File>Kt` class (rename with `@file:JvmName`).
- The **`@Jvm*` annotations** make Kotlin Java-friendly: **`@JvmStatic`** (real statics), **`@JvmField`** (plain fields), **`@JvmOverloads`** (default-arg overloads), **`@JvmName`** (renaming), **`@Throws`** (checked exceptions for Java).
- `suspend` functions aren't directly callable from Java — wrap them.

### Self-check quiz

1. Why does Kotlin use platform types for Java return values?
   <details><summary>Answer</summary>Java types don't encode nullability, so Kotlin can't tell if a returned `String` might be null. A platform type relaxes checks and lets you decide how to treat it — at the cost of a possible runtime NPE if you assume wrong.</details>
2. How does Java call a Kotlin top-level function `foo()` in `Helpers.kt`?
   <details><summary>Answer</summary>As a static method on the generated class: `HelpersKt.foo()` (or `Helpers.foo()` if you used `@file:JvmName("Helpers")`).</details>
3. What does `@JvmOverloads` do, and why is it needed?
   <details><summary>Answer</summary>It generates telescoping overloads for a function with default arguments, because Java has no default-argument syntax and would otherwise only see the all-parameters version.</details>
4. Can plain Java call a Kotlin `suspend` function directly?
   <details><summary>Answer</summary>No — it compiles with a hidden `Continuation` parameter. Expose a non-suspend wrapper (e.g., returning a `CompletableFuture`) for Java callers.</details>

### Exercises

**Exercise 18.1 — Use a Java API (guided).** Using `java.time`, compute how many days until a given date and whether that date is a weekend.

<details><summary>Show solution</summary>

```kotlin
import java.time.LocalDate
import java.time.temporal.ChronoUnit

fun main() {
    val today = LocalDate.of(2026, 7, 12)
    val deadline = LocalDate.of(2026, 7, 20)

    val daysLeft = ChronoUnit.DAYS.between(today, deadline)
    val isWeekend = today.dayOfWeek.value >= 6   // 6 = Saturday, 7 = Sunday

    println("Days left: $daysLeft")     // → Days left: 8
    println("Today is weekend: $isWeekend")   // → Today is weekend: true
}
```

**Why this works:** `LocalDate`, `ChronoUnit`, and `DayOfWeek` are all Java classes used directly from Kotlin. `ChronoUnit.DAYS.between` counts days; `dayOfWeek.value` is 1 (Mon) … 7 (Sun), so `>= 6` detects a weekend. (2026-07-12 is a Sunday.)

</details>

**Exercise 18.2 — SAM conversion.** Sort a list of strings by length using a Java `Comparator` created from a Kotlin lambda.

<details><summary>Show solution</summary>

```kotlin
fun main() {
    val words = mutableListOf("banana", "kiwi", "apple", "fig")
    words.sortWith(Comparator { a, b -> a.length - b.length })
    println(words)   // → [fig, kiwi, apple, banana]
}
```

**Why this works:** `Comparator` is a Java functional interface; SAM conversion lets a Kotlin lambda `{ a, b -> … }` become one. `sortWith` (from the standard library) sorts in place by that comparator. (Idiomatic Kotlin would prefer `words.sortBy { it.length }`, but this shows the Java-interop path.) Result ordering: fig(3), kiwi(4), apple(5), banana(6).

</details>

### Chapter project: wrapping a Java library

> 🛠️ **Chapter Project** — **Standalone mini-project** (does *not* extend the Task Manager). **Builds on:** Ch.1–18 (especially Ch.11 extensions). Java interop doesn't fit the Task Manager naturally, so here we build a small, self-contained wrapper instead.

**Goal.** Give Java's `java.time.LocalDate` a friendlier Kotlin API via extension functions.

**Requirements.**
1. `LocalDate.addDays(n)` / `addWeeks(n)`.
2. `LocalDate.isWeekend()`.
3. `LocalDate.daysUntil(other)`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import java.time.LocalDate
import java.time.temporal.ChronoUnit

fun LocalDate.addDays(days: Long): LocalDate = this.plusDays(days)
fun LocalDate.addWeeks(weeks: Long): LocalDate = this.plusWeeks(weeks)
fun LocalDate.isWeekend(): Boolean = this.dayOfWeek.value >= 6
fun LocalDate.daysUntil(other: LocalDate): Long = ChronoUnit.DAYS.between(this, other)

fun main() {
    val start = LocalDate.of(2026, 7, 12)   // a Sunday

    println(start.addDays(5))            // → 2026-07-17
    println(start.addWeeks(2))           // → 2026-07-26
    println(start.isWeekend())            // → true
    println(start.daysUntil(LocalDate.of(2026, 7, 20)))   // → 8
}
```

Output:

```text
2026-07-17
2026-07-26
true
8
```

**Commentary.**
- We can't (and shouldn't) modify Java's `LocalDate`, but **extension functions** (Chapter 11) let us *add* a nicer vocabulary from the outside. `start.addDays(5)` reads better than `start.plusDays(5)` only if your domain prefers that wording — the real value is showing that Kotlin can put an idiomatic Kotlin surface on *any* Java type.
- Everything delegates to the underlying Java methods (`plusDays`, `dayOfWeek`, `ChronoUnit.DAYS.between`) — no reimplementation, full interop.
- This is exactly how many Kotlin libraries are built: thin, pleasant extension layers over battle-tested Java libraries. It's a standalone utility because date math isn't part of the Task Manager's domain — the right call per the hybrid-project rule.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Interoperability** | Kotlin and Java calling each other with no wrappers. |
| **SAM conversion** | Turning a lambda into a Java single-abstract-method interface instance. |
| **Platform type** (`T!`) | A Java value of unknown nullability; checks relaxed. |
| **`<File>Kt` class** | The synthetic class holding a file's top-level declarations. |
| **`@JvmStatic`** | Exposes a companion/object member as a true static method. |
| **`@JvmField`** | Exposes a property as a plain public field. |
| **`@JvmOverloads`** | Generates overloads for default-argument functions (for Java). |
| **`@JvmName`** | Renames a generated method/class. |
| **`@Throws`** | Declares a checked exception for Java callers. |

### What's next

You can bridge to the whole JVM ecosystem. But to *build* and manage real projects — pulling in dependencies like coroutines and Ktor — you need a build tool. **[Ch.19 — Gradle with Kotlin DSL](#chapter-19--gradle-with-kotlin-dsl)** shows how to configure projects, declare dependencies, and structure multi-module builds.

[↑ back to top](#chapter-18--kotlin--java-interoperability)


---

## Chapter 19 — Gradle with Kotlin DSL

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.1 — Getting Started](#chapter-1--getting-started), [Ch.17 — DSLs](#chapter-17--type-safe-builders--dsls)

**Learning objectives** — after this chapter you will be able to:

- Read and write a `build.gradle.kts` build script.
- Declare dependencies and understand `implementation` vs `api` vs `testImplementation`.
- Configure the JVM toolchain and the `application` plugin.
- Structure a multi-module project and use a version catalog.
- Make builds reproducible with the wrapper, verification, locking, toolchains, and CI-friendly tasks.
- Move shared build logic into convention plugins and keep configuration-cache compatibility.

**In this chapter**

- [19.1 What Gradle does](#191-what-gradle-does)
- [19.2 Anatomy of a build script](#192-anatomy-of-a-build-script)
- [19.3 Dependency configurations](#193-dependency-configurations)
- [19.4 Multi-module projects](#194-multi-module-projects)
- [19.5 Version catalogs and custom tasks](#195-version-catalogs-and-custom-tasks)
- [19.6 The wrapper and reproducible dependencies](#196-the-wrapper-and-reproducible-dependencies)
- [19.7 Convention plugins and lazy tasks](#197-convention-plugins-and-lazy-tasks)
- [19.8 The build as a quality gate](#198-the-build-as-a-quality-gate)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-build-for-the-task-manager) · Glossary · What's next

---

### 19.1 What Gradle does

Once a project needs external libraries (coroutines, Ktor, a JSON parser) or produces a runnable artifact, you need a **build tool** to fetch dependencies, compile, test, and package. For Kotlin, that tool is almost always **Gradle**.

Gradle build scripts can be written in Groovy (`build.gradle`) or — the modern, recommended choice — in **Kotlin** (`build.gradle.kts`), using the **Kotlin DSL**. The beauty of the Kotlin DSL is that a build script is *itself Kotlin code*: you get type checking, autocompletion, and everything you learned in Chapter 17, because the build file is a big type-safe DSL (`plugins { }`, `dependencies { }`, … are all receiver-lambda blocks).

> ⚙️ **Under the hood** — Gradle runs in two phases. In the **configuration** phase it executes your `build.gradle.kts` top to bottom to build a model of tasks and their dependencies. In the **execution** phase it runs the tasks you asked for (and their prerequisites), in order. So code at the top level of the script runs at *configuration* time; code inside a task's `doLast { }` runs at *execution* time — a distinction that explains many "why did this run?" surprises.

### 19.2 Anatomy of a build script

Here's a complete `build.gradle.kts` for a runnable Kotlin JVM application, annotated:

```kotlin
plugins {
    kotlin("jvm") version "2.4.0"       // the Kotlin JVM plugin
    application                          // adds `run` and packaging tasks
}

group = "com.example"
version = "1.0.0"

repositories {
    mavenCentral()                       // where to download dependencies from
}

dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.11.0")
    testImplementation(kotlin("test"))   // test-only dependency
}

kotlin {
    jvmToolchain(17)                      // compile/run against JDK 17
}

application {
    mainClass.set("com.example.MainKt")   // entry point (note the Kt suffix, Ch.18)
}

tasks.test {
    useJUnitPlatform()                    // run Jupiter tests on the JUnit Platform
}
```

Every block is a DSL scope: `plugins { }` chooses plugins (each plugin adds tasks and conventions), `repositories { }` says where to fetch from, `dependencies { }` lists libraries, and `kotlin { }`/`application { }` configure those plugins. With this file, `./gradlew run` builds and runs the app, and `./gradlew test` runs the tests.

> ⚠️ **Gotcha** — For modern JUnit Jupiter, call `useJUnitPlatform()` in `tasks.test { }`, or Jupiter tests may not be discovered. This is a common cause of "my tests don't execute" (Chapter 24).

### 19.3 Dependency configurations

*How* you declare a dependency controls who can see it:

- **`implementation`** — the dependency is used *inside* your module but **not** exposed to modules that depend on you. This is the default you should reach for.
- **`api`** — the dependency is part of your module's *public* API (it appears in your public signatures), so dependents also see it. Use sparingly.
- **`testImplementation`** — available only when compiling/running tests, not in production code.
- **`compileOnly`** / **`runtimeOnly`** — needed only at compile time / only at runtime.

```kotlin
dependencies {
    api("com.example:core-model:1.0")            // leaks to consumers (part of your API)
    implementation("com.squareup.okhttp3:okhttp:5.4.0")  // internal detail
    testImplementation("io.mockk:mockk:1.14.11")  // tests only
}
```

> 💡 **Idiom** — Prefer **`implementation`** over `api`. Using `api` everywhere leaks your internal dependencies to everyone who depends on you, creating a tangled graph where upgrading one library forces rebuilds across the whole project. Reach for `api` only when a type from that dependency genuinely appears in *your* public API.

### 19.4 Multi-module projects

As a project grows, you split it into **modules** — separately-compiled units with their own build files. Modules improve build speed (only changed modules recompile) and enforce boundaries (a `:core` module can't accidentally depend on `:ui`).

The **`settings.gradle.kts`** file declares the modules:

```kotlin
// settings.gradle.kts
rootProject.name = "task-manager"
include("core", "app")
```

Each module has its own `build.gradle.kts`, and one module can depend on another with `project(":name")`:

```kotlin
// app/build.gradle.kts
plugins {
    kotlin("jvm")
    application
}

dependencies {
    implementation(project(":core"))    // depend on the core module
}
```

The root `build.gradle.kts` can hold shared configuration (often via a `plugins { … apply false }` block that versions plugins without applying them everywhere).

### 19.5 Version catalogs and custom tasks

Hard-coding version strings across many modules invites drift. A **version catalog** (`gradle/libs.versions.toml`) centralizes them:

```toml
# gradle/libs.versions.toml
[versions]
coroutines = "1.11.0"

[libraries]
coroutines-core = { module = "org.jetbrains.kotlinx:kotlinx-coroutines-core", version.ref = "coroutines" }
```

Then any module references them type-safely:

```kotlin
dependencies {
    implementation(libs.coroutines.core)   // resolved from the catalog
}
```

You can also register your own **tasks**:

```kotlin
tasks.register("hello") {
    doLast {                               // runs at execution time
        println("Hello from a custom task")
    }
}
```

Run it with `./gradlew hello`.

> ☕ **Coming from Java** — Compared to Maven's XML (`pom.xml`), the Kotlin DSL is code: type-safe, IDE-completable, and programmable (loops, conditionals, functions). Compared to Groovy Gradle, the Kotlin DSL catches typos at edit time instead of at build time. It's a strict upgrade in tooling support.

### 19.6 The wrapper and reproducible dependencies

Commit the **Gradle Wrapper** (`gradlew`, `gradlew.bat`, and `gradle/wrapper/*`). It pins the Gradle distribution so developers and CI run the same build tool:

```bash
./gradlew --version
./gradlew clean check
```

Do not require a globally installed Gradle. Upgrade the wrapper deliberately and review its generated URL and checksum. Pin a JVM toolchain as shown earlier; the wrapper pins Gradle, while the toolchain pins the compiler/runtime used by tasks.

Dynamic dependency versions (`1.+`, `latest.release`) make yesterday's commit produce a different graph today. Prefer exact versions through the catalog, then enable locking for applications:

```kotlin
// build.gradle.kts
dependencyLocking {
    lockAllConfigurations()
}
```

Generate and commit lock state with:

```bash
./gradlew dependencies --write-locks
```

For stronger supply-chain protection, Gradle dependency verification records checksums/signatures in `gradle/verification-metadata.xml`. Update that file only while intentionally changing dependencies, and review the diff as carefully as source code.

> ⚠️ **Gotcha** — A version catalog centralizes requested versions; it does not by itself freeze the complete transitive graph. Locking and verification solve different problems: reproducibility and artifact integrity.

### 19.7 Convention plugins and lazy tasks

Copying the same `plugins`, compiler options, and test setup into every module creates configuration drift. Put shared rules in a **convention plugin**, commonly in an included `build-logic` build:

```text
build-logic/
├── settings.gradle.kts
└── src/main/kotlin/taskmanager.kotlin-library.gradle.kts
```

```kotlin
// taskmanager.kotlin-library.gradle.kts (precompiled script plugin)
plugins {
    kotlin("jvm")
}

kotlin { jvmToolchain(21) }

tasks.withType<Test>().configureEach {
    useJUnitPlatform()
}
```

A module then declares intent instead of repeating mechanics:

```kotlin
plugins { id("taskmanager.kotlin-library") }
```

Use Gradle's lazy APIs. `tasks.register` creates a task only if needed; `tasks.named` configures an existing task without eagerly realizing the whole graph. Model inputs and outputs so Gradle can skip unchanged work:

```kotlin
abstract class GenerateBuildInfo : DefaultTask() {
    @get:Input abstract val versionText: Property<String>
    @get:OutputFile abstract val outputFile: RegularFileProperty

    @TaskAction fun generate() {
        outputFile.get().asFile.writeText("version=${versionText.get()}\n")
    }
}

tasks.register<GenerateBuildInfo>("generateBuildInfo") {
    versionText.set(project.version.toString())
    outputFile.set(layout.buildDirectory.file("generated/build-info.txt"))
}
```

> ⚠️ **Gotcha — configuration cache.** A task action should not reach back into `Project`, capture script objects, read arbitrary environment variables, or perform network calls. Declare values as `Property` inputs during configuration. Test with `./gradlew check --configuration-cache`; fixing reported problems makes large builds dramatically faster.

### 19.8 The build as a quality gate

A production build should have one local/CI entry point that compiles, tests, and verifies style and static analysis:

```bash
./gradlew check
```

Wire tools into `check` rather than inventing undocumented CI-only commands. Typical gates include:

- compiler warnings promoted selectively (`allWarningsAsErrors`) after the baseline is clean;
- formatting (ktlint) and static analysis (Detekt);
- unit and integration test suites separated by task when their cost differs;
- API/binary compatibility validation for published libraries (Chapter 35);
- coverage reports used as diagnostic information, not a target to game.

CI should start from a clean checkout, use the wrapper, cache Gradle's user home by lockfile keys, and publish test reports even on failure. A green build must mean the same thing locally and remotely.

> 💡 **Idiom** — Keep build scripts declarative. A build is executable code, but unbounded I/O and clever control flow make it nondeterministic and difficult to cache. Prefer plugins, typed properties, providers, and explicit task dependencies.

---

### Summary

- **Gradle** builds Kotlin projects; the **Kotlin DSL** (`build.gradle.kts`) is a type-safe DSL — your build script is real Kotlin code.
- A build script has `plugins { }`, `repositories { }`, `dependencies { }`, and plugin-config blocks (`kotlin { jvmToolchain(...) }`, `application { mainClass.set(...) }`); enable JUnit Jupiter with `useJUnitPlatform()`.
- Dependency scope matters: **`implementation`** (internal, preferred), **`api`** (exposed to consumers), **`testImplementation`** (tests only).
- **Multi-module** projects declare modules in `settings.gradle.kts` and depend via `project(":name")` — faster builds, enforced boundaries.
- **Version catalogs** (`libs.versions.toml`) centralize versions; you can register **custom tasks**.
- Gradle runs in a **configuration** phase (build the task model) then an **execution** phase (run tasks).
- The **wrapper**, toolchains, exact versions, dependency locking, and verification make builds reproducible. **Convention plugins** centralize policy; lazy, input/output-aware tasks unlock incremental builds and the configuration cache.

### Self-check quiz

1. Why prefer `implementation` over `api` for most dependencies?
   <details><summary>Answer</summary>`implementation` keeps the dependency internal, so it doesn't leak to modules that depend on yours — smaller compile classpaths, fewer forced rebuilds. Use `api` only when the dependency's types are part of your public API.</details>
2. What happens if you forget `useJUnitPlatform()`?
   <details><summary>Answer</summary>JUnit Jupiter tests may not be discovered/run — the test task can report success while executing nothing.</details>
3. How does one module depend on another?
   <details><summary>Answer</summary>Declare both in `settings.gradle.kts` via `include(...)`, then in the consumer's `build.gradle.kts` add `implementation(project(":other"))`.</details>
4. What's the difference between Gradle's configuration and execution phases?
   <details><summary>Answer</summary>Configuration runs the build script to build the task graph; execution runs the requested tasks (and their dependencies). Top-level script code runs at configuration time; `doLast { }` runs at execution time.</details>

### Exercises

**Exercise 19.1 — Add a dependency (guided).** Write the `dependencies { }` block to add Ktor server core (`io.ktor:ktor-server-core:3.5.0`) as a normal dependency and `kotlin("test")` for tests.

<details><summary>Show solution</summary>

```kotlin
dependencies {
    implementation("io.ktor:ktor-server-core:3.5.0")
    testImplementation(kotlin("test"))
}
```

**Why this works:** `implementation` adds Ktor for production code without exposing it to consumers; `testImplementation(kotlin("test"))` pulls in the Kotlin test library only for the test compilation/runtime. (`kotlin("test")` is a helper for the version-matched Kotlin test artifact.)

</details>

**Exercise 19.2 — A greeting task.** Register a Gradle task named `greet` that prints a message when run.

<details><summary>Show solution</summary>

```kotlin
tasks.register("greet") {
    doLast {
        println("Hello, Gradle!")
    }
}
```

**Why this works:** `tasks.register` defines a new task; the work goes in `doLast { }` so it runs during the *execution* phase (when you invoke `./gradlew greet`), not while the script is being configured.

</details>

### Chapter project: a build for the Task Manager

> 🛠️ **Chapter Project** — Advances the running **Task Manager** (build setup). **Builds on:** Ch.1–19. We give the Task Manager a proper multi-module Gradle build: a `:core` module for the domain and an `:app` module for the entry point.

**Goal.** Write the Gradle files that turn the Task Manager into a real, buildable, multi-module project.

**Requirements.**
1. `settings.gradle.kts` including `core` and `app`.
2. `:core` with coroutines; `:app` depending on `:core`, with the `application` plugin.
3. JVM toolchain 17 and JUnit Platform/Jupiter for tests.

<details><summary>Show reference solution + commentary</summary>

```kotlin
// settings.gradle.kts
rootProject.name = "task-manager"
include("core", "app")
```

```kotlin
// core/build.gradle.kts
plugins {
    kotlin("jvm") version "2.4.0"
}

repositories { mavenCentral() }

dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.11.0")
    testImplementation(kotlin("test"))
}

kotlin { jvmToolchain(17) }

tasks.test { useJUnitPlatform() }
```

```kotlin
// app/build.gradle.kts
plugins {
    kotlin("jvm") version "2.4.0"
    application
}

repositories { mavenCentral() }

dependencies {
    implementation(project(":core"))     // the app uses the domain from :core
}

kotlin { jvmToolchain(17) }

application {
    mainClass.set("com.example.app.MainKt")
}
```

Resulting layout:

```text
task-manager/
├── gradlew / gradlew.bat              ← generated Gradle Wrapper launchers
├── gradle/wrapper/                    ← generated wrapper properties + JAR
├── settings.gradle.kts
├── core/
│   ├── build.gradle.kts
│   └── src/main/kotlin/com/example/core/   (Task, TaskManager, Repository...)
└── app/
    ├── build.gradle.kts
    └── src/main/kotlin/com/example/app/     (Main.kt)
```

**Commentary.**
- The **`:core`** module holds the domain we've been building — `Task`, `TaskManager`, the `Repository` interface (Chapters 8–12). It depends on coroutines (Chapter 15) but knows nothing about the UI or entry point. This isolation is what lets us later reuse `:core` from a backend (Chapter 20), an Android app (Chapter 22), or shared multiplatform code (Chapter 34).
- The **`:app`** module is a thin entry point that `implementation(project(":core"))` pulls the domain from, and the `application` plugin makes runnable (`./gradlew :app:run`).
- `jvmToolchain(17)` pins the JDK so every developer and CI machine compiles identically, regardless of what JDK they have installed. `useJUnitPlatform()` readies the `:core` tests for Chapter 24.
- This module split is the physical backbone of the clean architecture we formalize in [Ch.33](#chapter-33--architecture--dependency-injection).

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Gradle** | The build tool that compiles, tests, and packages Kotlin projects. |
| **Kotlin DSL (`build.gradle.kts`)** | Gradle build scripts written in Kotlin — a type-safe DSL. |
| **Plugin** | A unit adding tasks/conventions (`kotlin("jvm")`, `application`). |
| **`implementation` / `api`** | Internal dependency / dependency exposed to consumers. |
| **`testImplementation`** | Dependency available only to tests. |
| **`jvmToolchain`** | Pins the JDK version for compilation/run. |
| **Module** | A separately-compiled sub-project (declared in `settings.gradle.kts`). |
| **Version catalog** | `libs.versions.toml` — centralized dependency versions. |
| **Configuration / execution phase** | Building the task model / running tasks. |
| **Gradle Wrapper** | Committed launcher/configuration that pins the Gradle distribution. |
| **Dependency locking / verification** | Freezing the resolved graph / checking artifact integrity. |
| **Convention plugin** | Reusable build policy shared by modules. |
| **Configuration cache** | Reuses Gradle's configured task graph when declared inputs are compatible. |

### What's next

With a real build in place, you can pull in frameworks and ship applications. **[Ch.20 — Ktor for Backend Development](#chapter-20--ktor-for-backend-development)** uses the coroutines you learned to build a REST API — and gives the Task Manager an HTTP interface.

[↑ back to top](#chapter-19--gradle-with-kotlin-dsl)


---

## Chapter 20 — Ktor for Backend Development

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.15 — Coroutines](#chapter-15--coroutines--flow), [Ch.19 — Gradle](#chapter-19--gradle-with-kotlin-dsl)

**Learning objectives** — after this chapter you will be able to:

- Stand up an HTTP server with Ktor.
- Define routes for GET/POST/PUT/DELETE with path and query parameters.
- Send and receive JSON with `kotlinx.serialization`.
- Return proper HTTP status codes.
- Design DTO/domain boundaries, validate requests, centralize failures, authenticate callers, and expose operational health.

**In this chapter**

- [20.1 What Ktor is](#201-what-ktor-is)
- [20.2 A minimal server](#202-a-minimal-server)
- [20.3 JSON with content negotiation](#203-json-with-content-negotiation)
- [20.4 Parameters and status codes](#204-parameters-and-status-codes)
- [20.5 DTOs, validation, and stable errors](#205-dtos-validation-and-stable-errors)
- [20.6 StatusPages and authentication](#206-statuspages-and-authentication)
- [20.7 Configuration, observability, and shutdown](#207-configuration-observability-and-shutdown)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-rest-api-for-the-task-manager) · Glossary · What's next

---

### 20.1 What Ktor is

**Ktor** is a lightweight, Kotlin-native framework for building asynchronous servers (and clients), made by JetBrains. Its defining trait: it's built **on coroutines** from the ground up. Every request handler is a `suspend` block, so you can call suspending functions (database queries, other services) directly, and the server handles thousands of concurrent requests on a small thread pool without blocking — exactly the scaling win from Chapter 15.

Ktor is configured in code (no annotations-and-XML magic), and its routing is a **DSL** (Chapter 17) — `routing { get("/") { … } }` is nested receiver lambdas.

Dependencies (`build.gradle.kts`):

```kotlin
plugins {
    kotlin("jvm") version "2.4.0"
    kotlin("plugin.serialization") version "2.4.0"   // for @Serializable
}
dependencies {
    implementation("io.ktor:ktor-server-core:3.5.0")
    implementation("io.ktor:ktor-server-netty:3.5.0")
    implementation("io.ktor:ktor-server-content-negotiation:3.5.0")
    implementation("io.ktor:ktor-serialization-kotlinx-json:3.5.0")
    implementation("io.ktor:ktor-server-status-pages:3.5.0")
    implementation("io.ktor:ktor-server-auth-jwt:3.5.0")
    implementation("io.ktor:ktor-server-call-logging:3.5.0")
}
```

> ☕ **Coming from Java** — Ktor is the coroutine-first alternative to Spring Boot. Where Spring leans on annotations, reflection, and a large runtime, Ktor is explicit, code-configured, and minimal — you assemble exactly the features you install. For Kotlin-first teams it's lighter and more transparent; Spring remains popular where its vast ecosystem is needed.

### 20.2 A minimal server

`embeddedServer` starts an HTTP server on an engine (Netty here); `routing { }` maps paths to handlers:

```kotlin
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.application.*
import io.ktor.server.response.*
import io.ktor.server.routing.*

fun main() {
    embeddedServer(Netty, port = 8080) {
        routing {
            get("/") {
                call.respondText("Hello, Ktor!")
            }
            get("/health") {
                call.respondText("OK")
            }
        }
    }.start(wait = true)   // block the main thread, keeping the server alive
}
```

Run it, and `GET http://localhost:8080/` returns `Hello, Ktor!`. Inside each handler, `call` represents the request/response exchange: `call.respondText(...)` writes the body.

> ⚙️ **Under the hood** — Each route handler runs as a coroutine on Ktor's dispatcher. Because handlers are `suspend`, a handler that awaits a database call *suspends* rather than blocking its thread, freeing that thread to serve other requests. This is why a Ktor server handles high concurrency on few threads — coroutines (Chapter 15) applied to HTTP.

### 20.3 JSON with content negotiation

Real APIs speak JSON. Ktor's **ContentNegotiation** plugin plus **`kotlinx.serialization`** handle converting Kotlin objects to/from JSON automatically. Mark your data classes `@Serializable`, install the plugin, and `call.respond(obj)` / `call.receive<T>()` do the rest:

```kotlin
import io.ktor.serialization.kotlinx.json.*
import io.ktor.server.application.*
import io.ktor.server.plugins.contentnegotiation.*
import io.ktor.server.response.*
import io.ktor.server.routing.*
import kotlinx.serialization.Serializable

@Serializable
data class Task(val id: Int, val title: String, val done: Boolean = false)

fun Application.module() {
    install(ContentNegotiation) { json() }   // enable JSON

    routing {
        get("/tasks") {
            call.respond(listOf(Task(1, "Learn Ktor")))   // serialized to JSON automatically
        }
    }
}
```

A `GET /tasks` now returns `[{"id":1,"title":"Learn Ktor","done":false}]`.

> ⚠️ **Gotcha** — Forgetting `install(ContentNegotiation) { json() }` is the classic Ktor mistake: `call.respond(someObject)` then fails at runtime because Ktor doesn't know how to turn the object into a response. Install content negotiation once in your `module()`.

### 20.4 Parameters and status codes

Path parameters (`{id}`) come from `call.parameters`; the request body via `call.receive<T>()`. And a REST API must return correct **status codes** — 201 for created, 404 for not found, etc. — via `call.respond(HttpStatusCode.X, body)`:

```kotlin
get("/tasks/{id}") {
    val id = call.parameters["id"]?.toIntOrNull()
    val task = id?.let { findTask(it) }
    if (task != null) {
        call.respond(task)                                   // 200 OK + JSON
    } else {
        call.respond(HttpStatusCode.NotFound, "No such task") // 404
    }
}

post("/tasks") {
    val incoming = call.receive<Task>()                       // parse JSON body
    val created = save(incoming)
    call.respond(HttpStatusCode.Created, created)             // 201 Created
}
```

Note the null-safety chain: `call.parameters["id"]` is a `String?`, `?.toIntOrNull()` handles a non-numeric id, and `?.let { findTask(it) }` looks it up — all the Chapter 7 habits, now guarding an HTTP boundary.

> ⚠️ **Gotcha** — Don't do *blocking* work in a handler (a blocking JDBC call, `Thread.sleep`, heavy CPU) directly — it ties up a Ktor thread. Wrap blocking calls in `withContext(Dispatchers.IO)` (Chapter 15). And always set explicit status codes; silently returning 200 for a failed operation misleads clients.

### 20.5 DTOs, validation, and stable errors

Do not deserialize clients directly into your domain/entity type. A request DTO contains only fields the caller may choose; the server owns ids, audit timestamps, and authorization decisions:

```kotlin
@Serializable
data class CreateTaskRequest(val title: String, val priority: String = "NORMAL")

@Serializable
data class TaskResponse(val id: Long, val title: String, val priority: String)

@Serializable
data class ApiError(
    val code: String,
    val message: String,
    val fieldErrors: Map<String, String> = emptyMap(),
    val requestId: String? = null,
)
```

Parse transport syntax first, then validate domain meaning:

```kotlin
fun CreateTaskRequest.toCommand(): Result<CreateTask> = runCatching {
    val clean = title.trim()
    require(clean.length in 1..200) { "title must contain 1..200 characters" }
    val parsedPriority = Priority.entries.find { it.name == priority.uppercase() }
        ?: throw IllegalArgumentException("unknown priority")
    CreateTask(clean, parsedPriority)
}
```

Return a stable machine-readable `code`; clients should not parse human prose. Treat malformed JSON, invalid fields, missing resources, conflicts, authentication failures, and unexpected server failures as different categories.

> ⚠️ **Gotcha — mass assignment.** Accepting `Task(id, ownerId, isAdmin, ...)` from JSON and saving it wholesale lets a client set server-owned fields. Explicit request DTOs are a security boundary, not cosmetic duplication.

For list endpoints, bound work and make ordering deterministic:

```kotlin
val limit = call.request.queryParameters["limit"]?.toIntOrNull()?.coerceIn(1, 100) ?: 20
val after = call.request.queryParameters["after"]?.toLongOrNull()
call.respond(service.list(afterId = after, limit = limit))
```

Cursor pagination usually scales more predictably than large offsets, provided the cursor column and tie-breaker form a stable indexed order.

### 20.6 StatusPages and authentication

Centralize exception-to-HTTP mapping with `StatusPages`; route bodies then express the happy path rather than repeating `try/catch`:

```kotlin
install(StatusPages) {
    exception<ContentTransformationException> { call, _ ->
        call.respond(HttpStatusCode.BadRequest, ApiError("INVALID_JSON", "Malformed JSON body"))
    }
    exception<ValidationException> { call, cause ->
        call.respond(HttpStatusCode.UnprocessableEntity, ApiError("VALIDATION", cause.message ?: "Invalid input"))
    }
    exception<Throwable> { call, cause ->
        environment.log.error("Unhandled request failure", cause) // full details stay server-side
        call.respond(HttpStatusCode.InternalServerError, ApiError("INTERNAL", "Unexpected server error"))
    }
}
```

Never return stack traces, SQL messages, secrets, or internal class names to clients. Log the exception with a request/correlation id and return a controlled envelope.

Authentication establishes **who** the caller is; authorization decides **what that identity may do**. For bearer/JWT authentication:

```kotlin
install(Authentication) {
    jwt("auth-jwt") {
        realm = "task-manager"
        verifier(jwtVerifierFromTrustedConfiguration())
        validate { credential ->
            credential.payload.subject?.let(::UserPrincipal)
        }
        challenge { _, _ ->
            call.respond(HttpStatusCode.Unauthorized, ApiError("UNAUTHENTICATED", "Valid token required"))
        }
    }
}

routing {
    authenticate("auth-jwt") {
        delete("/tasks/{id}") {
            val user = call.principal<UserPrincipal>()!!
            service.deleteOwnedTask(user.id, call.requireTaskId())
            call.respond(HttpStatusCode.NoContent)
        }
    }
}
```

The verifier must check signature, issuer, audience, expiry, and allowed algorithms. Authorization belongs in a use case/policy, not merely in whether a route is nested under `authenticate`.

### 20.7 Configuration, observability, and shutdown

Configuration differs by environment; source code should not. Read ports, database URLs, and issuer/audience settings from Ktor configuration or environment-backed providers. Inject a typed configuration object and fail at startup if a required value is absent. Never commit production secrets.

Operational endpoints have distinct meanings:

- **liveness**: the process/event loop is alive; failure should trigger restart;
- **readiness**: the instance can serve traffic (database/migrations ready); failure should remove it from load balancing;
- **metrics**: request rate, latency, status distribution, pool saturation, and domain signals;
- **structured logs/traces**: request id, route, status, duration, and trace context—without credentials or sensitive payloads.

Install call logging with an explicit filter and MDC fields, put a reverse proxy in front for TLS when appropriate, and configure forwarded headers only for trusted proxies. Apply request/body limits, timeouts, and rate limits according to the threat model.

Graceful shutdown stops accepting new requests, allows in-flight work a bounded time to finish, closes database pools and clients, and then exits. Test the shutdown path; cleanup code that only runs in production is otherwise where leaks hide.

> 💡 **Production boundary rule** — Every external input is untrusted and bounded; every external call has a timeout; every failure has a stable public representation and a detailed private record; every resource has an owner that closes it.

---

### Summary

- **Ktor** is a coroutine-native, code-configured server framework; every handler is a `suspend` block, so it scales on few threads.
- `embeddedServer(Netty, port) { routing { … } }.start(wait = true)` starts a server; `call.respondText/respond` writes responses.
- Install **`ContentNegotiation { json() }`** and mark data classes **`@Serializable`** to send/receive JSON automatically (`call.respond`, `call.receive<T>()`).
- Read path params from **`call.parameters`**; return correct **`HttpStatusCode`** values (201/404/…).
- Don't block handlers (use `withContext(Dispatchers.IO)`); always install content negotiation.
- Separate request/response DTOs from domain objects, bound pagination, centralize error mapping with **StatusPages**, authenticate and authorize independently, and expose liveness/readiness plus structured telemetry.

### Self-check quiz

1. Why can Ktor handle high concurrency on few threads?
   <details><summary>Answer</summary>Handlers are `suspend` coroutines; awaiting I/O suspends the coroutine and frees its thread to serve other requests, rather than blocking one thread per request.</details>
2. What two things must you do to return a Kotlin object as JSON?
   <details><summary>Answer</summary>Mark the class `@Serializable` and `install(ContentNegotiation) { json() }`. Then `call.respond(obj)` serializes it.</details>
3. How do you read a path parameter `{id}` and a JSON body?
   <details><summary>Answer</summary>`call.parameters["id"]` (a `String?`) for the path; `call.receive<Task>()` for the JSON body.</details>
4. Why avoid blocking calls inside a handler?
   <details><summary>Answer</summary>They occupy a Ktor thread, undermining the coroutine scaling model. Wrap blocking work in `withContext(Dispatchers.IO)`.</details>

### Exercises

**Exercise 20.1 — Echo endpoint (guided).** Add a `GET /greet/{name}` route that responds `Hello, <name>!`, defaulting to `stranger` if the name is blank/missing.

<details><summary>Show solution</summary>

```kotlin
get("/greet/{name}") {
    val name = call.parameters["name"]?.takeIf { it.isNotBlank() } ?: "stranger"
    call.respondText("Hello, $name!")
}
```

**Why this works:** `call.parameters["name"]` is nullable; `?.takeIf { it.isNotBlank() }` yields null for a blank value, and `?: "stranger"` supplies the default. `GET /greet/Alice` → `Hello, Alice!`.

</details>

**Exercise 20.2 — Query parameter.** Add `GET /square?n=5` that returns the square of `n`, or a 400 for a missing/invalid `n`.

<details><summary>Show solution</summary>

```kotlin
get("/square") {
    val n = call.request.queryParameters["n"]?.toIntOrNull()
    if (n == null) {
        call.respond(HttpStatusCode.BadRequest, "Provide a numeric 'n'")
    } else {
        call.respondText("${n * n}")
    }
}
```

**Why this works:** query parameters live in `call.request.queryParameters`. `?.toIntOrNull()` yields null for a missing or non-numeric value, which we answer with a 400; otherwise we return the square. `GET /square?n=5` → `25`.

</details>

### Chapter project: a REST API for the Task Manager

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — a major step. **Builds on:** Ch.1–20. We expose the task domain over HTTP with full CRUD, JSON, and correct status codes.

**Goal.** Build a REST API: list, get, create, update, and delete tasks.

**Requirements.**
1. `@Serializable Task`; JSON content negotiation.
2. `GET /tasks`, `GET /tasks/{id}`, `POST /tasks`, `PUT /tasks/{id}`, `DELETE /tasks/{id}`.
3. Correct status codes (200/201/204/404).

<details><summary>Show reference solution + commentary</summary>

```kotlin
import io.ktor.http.*
import io.ktor.serialization.kotlinx.json.*
import io.ktor.server.application.*
import io.ktor.server.engine.*
import io.ktor.server.netty.*
import io.ktor.server.plugins.contentnegotiation.*
import io.ktor.server.request.*
import io.ktor.server.response.*
import io.ktor.server.routing.*
import kotlinx.serialization.Serializable

@Serializable
data class Task(val id: Int, val title: String, val done: Boolean = false)

fun main() {
    val tasks = mutableListOf(Task(1, "Learn Ktor"))
    var nextId = 2

    embeddedServer(Netty, port = 8080) {
        install(ContentNegotiation) { json() }

        routing {
            get("/tasks") {
                call.respond(tasks)                                  // 200 + JSON array
            }

            get("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                val task = tasks.find { it.id == id }
                if (task != null) call.respond(task)
                else call.respond(HttpStatusCode.NotFound, "Task not found")
            }

            post("/tasks") {
                val created = call.receive<Task>().copy(id = nextId++)
                tasks.add(created)
                call.respond(HttpStatusCode.Created, created)        // 201
            }

            put("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                val index = tasks.indexOfFirst { it.id == id }
                if (index == -1) {
                    call.respond(HttpStatusCode.NotFound); return@put
                }
                val updated = call.receive<Task>().copy(id = id!!)
                tasks[index] = updated
                call.respond(updated)                                 // 200
            }

            delete("/tasks/{id}") {
                val id = call.parameters["id"]?.toIntOrNull()
                if (tasks.removeIf { it.id == id }) call.respond(HttpStatusCode.NoContent)  // 204
                else call.respond(HttpStatusCode.NotFound)
            }
        }
    }.start(wait = true)
}
```

Sample interaction (via `curl`):

```text
$ curl localhost:8080/tasks
[{"id":1,"title":"Learn Ktor","done":false}]

$ curl -X POST localhost:8080/tasks -H "Content-Type: application/json" -d '{"id":0,"title":"Ship API"}'
{"id":2,"title":"Ship API","done":false}       (HTTP 201)

$ curl localhost:8080/tasks/99
Task not found                                   (HTTP 404)

$ curl -X DELETE localhost:8080/tasks/1
                                                 (HTTP 204, empty body)
```

**Commentary.**
- The domain from Chapters 8–12 is now reachable over HTTP. Each route is a `suspend` handler; `call.respond(tasks)` serializes via `kotlinx.serialization` (Chapter 31 goes deep on it).
- **Status codes carry meaning:** 201 for a created resource, 204 for a successful delete with no body, 404 for a missing id. This is what makes it a *REST* API rather than "JSON over one endpoint."
- Every id is parsed with `?.toIntOrNull()` — a malformed `/tasks/abc` yields `null`, handled as not-found, never a crash. The `?: return@put` guard is the Chapter 7 early-return applied to a route.
- Here tasks live in a `mutableListOf` for clarity. In [Ch.21](#chapter-21--database-access) we swap that for a real database behind the `Repository` interface (Chapter 9) — the routes won't change, because they depend on the abstraction, not the storage.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Ktor** | A coroutine-native Kotlin server/client framework. |
| **`embeddedServer`** | Starts an HTTP server on an engine (e.g. Netty). |
| **`routing { }`** | The DSL mapping paths/methods to handlers. |
| **`call`** | The request/response context inside a handler. |
| **ContentNegotiation** | The plugin converting objects to/from JSON (etc.). |
| **`@Serializable`** | Marks a class for `kotlinx.serialization`. |
| **`call.respond` / `call.receive`** | Send a response / parse the request body. |
| **`HttpStatusCode`** | HTTP status codes (200/201/204/404/…). |
| **DTO** | A transport-specific request/response shape separated from the domain model. |
| **StatusPages** | Ktor plugin mapping failures to controlled HTTP responses. |
| **Authentication / authorization** | Establishing identity / deciding permitted actions. |
| **Liveness / readiness** | Process-alive signal / ability-to-serve-traffic signal. |

### What's next

Your API stores tasks in memory — restart the server and they're gone. **[Ch.21 — Database Access](#chapter-21--database-access)** adds real persistence with Exposed (and a look at Room for Android), backing the `Repository` interface with a database so the same API survives restarts.

[↑ back to top](#chapter-20--ktor-for-backend-development)


---

## Chapter 21 — Database Access

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Interfaces](#chapter-9--inheritance--interfaces), [Ch.15 — Coroutines](#chapter-15--coroutines--flow), [Ch.20 — Ktor](#chapter-20--ktor-for-backend-development)

**Learning objectives** — after this chapter you will be able to:

- Define tables and run queries with the Exposed SQL library.
- Use transactions correctly.
- Recognise the Room persistence library for Android.
- Back a `Repository` interface with a real database.
- Evolve schemas safely, design indexes/relations, and choose transaction boundaries under concurrency.

**In this chapter**

- [21.1 Exposed: typed SQL for the JVM](#211-exposed-typed-sql-for-the-jvm)
- [21.2 Transactions and CRUD](#212-transactions-and-crud)
- [21.3 Room (Android)](#213-room-android)
- [21.4 Migrations: schema history is source code](#214-migrations-schema-history-is-source-code)
- [21.5 Relations, indexes, pools, and query plans](#215-relations-indexes-pools-and-query-plans)
- [21.6 Transaction boundaries and concurrency](#216-transaction-boundaries-and-concurrency)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-database-backed-repository) · Glossary · What's next

---

### 21.1 Exposed: typed SQL for the JVM

**Exposed** is JetBrains' lightweight SQL library for Kotlin. Its DSL flavour lets you write queries in Kotlin — `Tasks.selectAll().where { Tasks.done eq true }` — with the compiler checking column names and types, instead of untyped SQL strings. Under the surface it's just JDBC, so it works with any SQL database; we'll use **H2** (an in-memory database) for runnable examples.

Dependencies:

```kotlin
dependencies {
    implementation("org.jetbrains.exposed:exposed-core:1.3.1")
    implementation("org.jetbrains.exposed:exposed-jdbc:1.3.1")
    implementation("com.h2database:h2:2.4.240")
}
```

You describe a table as a Kotlin `object` extending `Table`, declaring each column as a typed property:

```kotlin
import org.jetbrains.exposed.v1.core.*

object Tasks : Table("tasks") {
    val id = integer("id").autoIncrement()
    val title = varchar("title", length = 255)
    val done = bool("done").default(false)
    override val primaryKey = PrimaryKey(id)
}
```

Each column property (`Tasks.id`, `Tasks.title`) is a typed handle you use to build queries — that's where the type safety comes from.

> ⚙️ **Under the hood** — Exposed's DSL is built on **operator and infix functions** (Chapters 3, 11): `Tasks.done eq true` is an `infix` call producing a query-condition object, and `and`/`or` combine them. The whole thing is a type-safe builder (Chapter 17) that assembles a SQL string plus bound parameters — so you get SQL's power with Kotlin's checking, and protection from SQL injection (values are always parameters, never concatenated).

### 21.2 Transactions and CRUD

Every database operation in Exposed runs inside a **`transaction { }`** block, which opens a connection, commits on success, and rolls back on an exception. Here's full CRUD against H2, runnable as-is:

```kotlin
import org.jetbrains.exposed.v1.core.*
import org.jetbrains.exposed.v1.jdbc.*
import org.jetbrains.exposed.v1.jdbc.transactions.transaction

object Tasks : Table("tasks") {
    val id = integer("id").autoIncrement()
    val title = varchar("title", 255)
    val done = bool("done").default(false)
    override val primaryKey = PrimaryKey(id)
}

fun main() {
    Database.connect("jdbc:h2:mem:test;DB_CLOSE_DELAY=-1", driver = "org.h2.Driver")

    transaction {
        SchemaUtils.create(Tasks)                          // CREATE TABLE

        // CREATE
        Tasks.insert { it[title] = "Learn Exposed" }
        Tasks.insert { it[title] = "Persist tasks"; it[done] = true }

        // READ
        println("All tasks:")
        Tasks.selectAll().forEach {
            println("  #${it[Tasks.id]} ${it[Tasks.title]} (done=${it[Tasks.done]})")
        }

        // UPDATE
        Tasks.update({ Tasks.id eq 1 }) { it[done] = true }

        // filtered READ (current API: selectAll().where { })
        val doneCount = Tasks.selectAll().where { Tasks.done eq true }.count()
        println("Done count: $doneCount")

        // DELETE
        Tasks.deleteWhere { Tasks.id eq 2 }
        println("Remaining: ${Tasks.selectAll().count()}")
    }
}
```

Output:

```text
All tasks:
  #1 Learn Exposed (done=false)
  #2 Persist tasks (done=true)
Done count: 2
Remaining: 1
```

Reading rows gives you `ResultRow`s, from which you extract typed values with `row[Tasks.title]`. Inserts and updates use the same column handles: `it[title] = "…"`.

> ⚠️ **Gotcha — the deprecated `select { }`.** Older Exposed used `Tasks.select { Tasks.done eq true }`. Current versions replace it with **`Tasks.selectAll().where { … }`** — the older form is deprecated. (Earlier editions of this very guide used `select { }`; if you see it, modernize to `selectAll().where { }`.)

> ⚠️ **Gotcha — don't touch results outside the transaction.** A `ResultRow` (and any lazy relation) is only valid *inside* its `transaction { }`. Returning a raw `ResultRow` and reading it later — after the connection closed — fails. Map rows to your own domain objects (`Task`) *inside* the transaction, and return those. Also beware **N+1 queries**: fetching a list then querying once *per row* in a loop; batch instead.

### 21.3 Room (Android)

On Android, the standard persistence library is **Room**, an abstraction over SQLite. It's annotation-driven and integrates with coroutines (DAO methods can be `suspend`). The three pieces:

```kotlin
import androidx.room.*

@Entity(tableName = "tasks")
data class TaskEntity(
    @PrimaryKey(autoGenerate = true) val id: Int = 0,
    val title: String,
    val done: Boolean = false
)

@Dao
interface TaskDao {
    @Query("SELECT * FROM tasks")
    suspend fun getAll(): List<TaskEntity>

    @Insert
    suspend fun insert(task: TaskEntity)

    @Update
    suspend fun update(task: TaskEntity)

    @Delete
    suspend fun delete(task: TaskEntity)
}

@Database(entities = [TaskEntity::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun taskDao(): TaskDao
}
```

An `@Entity` maps to a table, a `@Dao` interface declares queries (Room generates the implementation via KSP — Chapter 30), and the `@Database` ties them together. The `suspend` DAO methods run off the main thread automatically, fitting the coroutine model from Chapter 15.

> ☕ **Coming from Java** — Exposed and Room are Kotlin's take on persistence, contrasted with raw **JDBC** (verbose, stringly-typed) and **JPA/Hibernate** (powerful but heavy, reflection-driven). Exposed's DSL is code-first and type-checked; Room generates code at compile time (no runtime reflection), which is fast and catches query errors early.

### 21.4 Migrations: schema history is source code

`SchemaUtils.create` is convenient for a tutorial or disposable test database. It is not a production migration strategy. Once users have data, schema changes must be ordered, reviewable, repeatable, and applied exactly once.

A SQL migration tool such as Flyway stores numbered scripts:

```text
src/main/resources/db/migration/
├── V001__create_tasks.sql
├── V002__add_task_priority.sql
└── V003__index_pending_tasks.sql
```

```sql
-- V001__create_tasks.sql
CREATE TABLE tasks (
    id BIGINT GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    done BOOLEAN NOT NULL DEFAULT FALSE,
    version BIGINT NOT NULL DEFAULT 0
);
```

Migration scripts already applied to a shared environment are **immutable**: create a new migration to correct them. CI should start an empty real database, apply every migration, run integration tests, and optionally test upgrading from a representative older snapshot.

For zero/low-downtime changes, use **expand and contract**:

1. Add a nullable/defaulted new column or table that old code tolerates.
2. Deploy code that writes both shapes and backfill existing rows in bounded batches.
3. Switch reads to the new shape and verify.
4. In a later deployment, remove the old column/constraint.

> ⚠️ **Gotcha** — Renaming or making a large column `NOT NULL` can lock/rewrite a table. A syntactically valid migration is not automatically operationally safe. Inspect the database-specific plan, duration, lock level, rollback strategy, and backup/restore path.

Exposed's migration modules can generate/inspect schema differences, but generated SQL still requires review. A library cannot know your rollout constraints or data-backfill semantics.

### 21.5 Relations, indexes, pools, and query plans

Model relationships with foreign keys and explicit delete behavior:

```kotlin
object Projects : Table("projects") {
    val id = long("id").autoIncrement()
    val name = varchar("name", 120)
    override val primaryKey = PrimaryKey(id)
}

object Tasks : Table("tasks") {
    val id = long("id").autoIncrement()
    val projectId = long("project_id").references(Projects.id, onDelete = ReferenceOption.CASCADE)
    val title = varchar("title", 200)
    val done = bool("done").default(false)
    val createdAt = long("created_at_epoch_ms")
    init {
        index(false, projectId, done, createdAt)
    }
    override val primaryKey = PrimaryKey(id)
}
```

An index accelerates a **particular access pattern** and costs storage plus write work. Put equality-filter columns first, then ordering/range columns, and verify using `EXPLAIN (ANALYZE, BUFFERS)` on production-like data. Do not add an index for every field.

Avoid N+1 by joining or loading related rows in one bounded query:

```kotlin
val rows = (Tasks innerJoin Projects)
    .select(Tasks.id, Tasks.title, Projects.name)
    .where { Tasks.done eq false }
    .orderBy(Tasks.createdAt to SortOrder.DESC)
    .limit(100)
```

Production JDBC uses a bounded **connection pool** such as HikariCP. Set the pool based on database capacity, number of application instances, and measured query latency—not on request count. Always configure connection/statement timeouts and observe pool wait time. A pool that is too large merely moves overload into the database.

### 21.6 Transaction boundaries and concurrency

A transaction protects a business invariant, not merely one repository method. "Create task and increment project count" must succeed or fail as one unit; two independent repository transactions can leave half a change committed.

Keep transactions short: do not make HTTP calls, wait for user input, or perform slow unrelated computation while holding a database connection/locks. For blocking JDBC in a coroutine server, isolate it on `Dispatchers.IO` or a dedicated bounded dispatcher. Exposed 1.x also offers JDBC `suspendTransaction`; it does not make the JDBC driver non-blocking. Use Exposed R2DBC with a reactive driver when end-to-end non-blocking database I/O is a requirement.

Concurrent updates need an explicit strategy. **Optimistic locking** is appropriate when conflicts are rare:

```sql
UPDATE tasks
SET title = ?, version = version + 1
WHERE id = ? AND version = ?;
```

If the affected-row count is zero, another transaction changed the row; return a conflict or retry the complete operation from fresh state. Use `SELECT ... FOR UPDATE`/pessimistic locking only when contention and invariant requirements justify the reduced concurrency, and always acquire locks in a consistent order to reduce deadlocks.

Isolation levels trade anomalies for concurrency. Know whether an operation tolerates non-repeatable reads, phantoms, or write skew; choose database constraints as the final authority. A unique constraint is stronger than "check then insert" in application code because concurrent requests cannot race around it.

> 💡 **Idiom — transactional outbox.** A database commit and message-broker publish cannot be made atomic by hope. Write the domain change and an outbox row in one database transaction; a separate idempotent publisher sends and marks outbox records. Consumers should also be idempotent because delivery is commonly at least once.

---

### Summary

- **Exposed** provides type-safe SQL for the JVM: describe tables as `object : Table()`, and query with a DSL (`insert`, `selectAll().where { }`, `update`, `deleteWhere`) checked by the compiler.
- Every operation runs in a **`transaction { }`** (commit on success, rollback on error). Map `ResultRow`s to domain objects **inside** the transaction; don't use them after it closes; avoid **N+1** queries.
- The modern filter API is **`selectAll().where { }`** (the old `select { }` is deprecated).
- **Room** is Android's persistence library: `@Entity`, `@Dao` (with `suspend` queries), `@Database`; it generates code at compile time.
- Both are Kotlin-idiomatic alternatives to JDBC/JPA.
- Production schemas evolve through reviewed **migrations**; indexes follow measured query patterns; pools are bounded; business invariants define transaction boundaries; constraints and explicit locking strategies handle concurrency.

### Self-check quiz

1. Why must database work run inside `transaction { }`?
   <details><summary>Answer</summary>It manages the connection and atomicity: committing on success and rolling back if an exception is thrown, so partial changes don't persist.</details>
2. What's the modern replacement for the deprecated `Table.select { }`?
   <details><summary>Answer</summary>`Table.selectAll().where { … }`.</details>
3. Why shouldn't you return a raw `ResultRow` from a transaction?
   <details><summary>Answer</summary>It's only valid inside the transaction (the connection is open); reading it afterward fails. Map rows to domain objects inside the transaction and return those.</details>
4. How does Room fit the coroutine model?
   <details><summary>Answer</summary>DAO methods can be `suspend`, so queries run off the main thread and integrate with structured concurrency (Chapter 15).</details>

### Exercises

**Exercise 21.1 — Categories table (guided).** Define an Exposed `Categories` table (`id`, `name`) and insert two rows, then print them.

<details><summary>Show solution</summary>

```kotlin
import org.jetbrains.exposed.v1.core.*
import org.jetbrains.exposed.v1.jdbc.*
import org.jetbrains.exposed.v1.jdbc.transactions.transaction

object Categories : Table("categories") {
    val id = integer("id").autoIncrement()
    val name = varchar("name", 100)
    override val primaryKey = PrimaryKey(id)
}

fun main() {
    Database.connect("jdbc:h2:mem:test;DB_CLOSE_DELAY=-1", driver = "org.h2.Driver")
    transaction {
        SchemaUtils.create(Categories)
        Categories.insert { it[name] = "Work" }
        Categories.insert { it[name] = "Home" }
        Categories.selectAll().forEach { println("#${it[Categories.id]} ${it[Categories.name]}") }
    }
}
```

Output:
```text
#1 Work
#2 Home
```

**Why this works:** the table `object` declares typed columns; `insert { it[name] = … }` uses the column handle; `selectAll()` reads all rows; `row[Categories.name]` extracts the typed value. Everything runs in one `transaction`.

</details>

**Exercise 21.2 — Count with a filter.** Given the `Tasks` table from §21.2, write the query that counts undone tasks.

<details><summary>Show solution</summary>

```kotlin
val pendingCount = Tasks.selectAll().where { Tasks.done eq false }.count()
```

**Why this works:** `selectAll().where { Tasks.done eq false }` builds a filtered query (the `eq` infix produces the condition), and `count()` returns how many rows match — the current, non-deprecated API.

</details>

### Chapter project: a database-backed repository

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — a major step. **Builds on:** Ch.1–21. We implement the `TaskRepository` interface (Chapter 9) with Exposed, so persistence becomes real — and nothing above the interface changes.

**Goal.** Provide an `ExposedTaskRepository` that satisfies the same interface the in-memory one did.

**Requirements.**
1. A `Tasks` table.
2. `ExposedTaskRepository : TaskRepository` mapping rows ↔ `Task`, all inside transactions.
3. Demonstrate add/find/all through the interface.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import org.jetbrains.exposed.v1.core.*
import org.jetbrains.exposed.v1.jdbc.*
import org.jetbrains.exposed.v1.jdbc.transactions.transaction

data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {
    fun add(title: String): Task
    fun findById(id: Int): Task?
    fun all(): List<Task>
    fun setDone(id: Int, done: Boolean)
}

object Tasks : Table("tasks") {
    val id = integer("id").autoIncrement()
    val title = varchar("title", 255)
    val done = bool("done").default(false)
    override val primaryKey = PrimaryKey(id)
}

class ExposedTaskRepository : TaskRepository {
    // Map a row to the domain object — INSIDE a transaction
    private fun ResultRow.toTask() = Task(this[Tasks.id], this[Tasks.title], this[Tasks.done])

    override fun add(title: String): Task = transaction {
        val newId = Tasks.insert { it[Tasks.title] = title } get Tasks.id
        Task(newId, title, false)
    }

    override fun findById(id: Int): Task? = transaction {
        Tasks.selectAll().where { Tasks.id eq id }.singleOrNull()?.toTask()
    }

    override fun all(): List<Task> = transaction {
        Tasks.selectAll().map { it.toTask() }
    }

    override fun setDone(id: Int, done: Boolean) {
        transaction { Tasks.update({ Tasks.id eq id }) { it[Tasks.done] = done } }
    }
}

fun main() {
    Database.connect("jdbc:h2:mem:test;DB_CLOSE_DELAY=-1", driver = "org.h2.Driver")
    transaction { SchemaUtils.create(Tasks) }

    val repo: TaskRepository = ExposedTaskRepository()   // depend on the interface
    val first = repo.add("Persist with Exposed")
    repo.add("Survive a restart")
    repo.setDone(first.id, true)

    println("All tasks:")
    repo.all().forEach { println("  #${it.id} [${if (it.done) "x" else " "}] ${it.title}") }
    println("Find #1: ${repo.findById(1)}")
}
```

Output:

```text
All tasks:
  #1 [x] Persist with Exposed
  #2 [ ] Survive a restart
Find #1: Task(id=1, title=Persist with Exposed, done=true)
```

**Commentary.**
- `ExposedTaskRepository` implements the **exact same `TaskRepository` interface** from Chapter 9. Because `TaskManager` (and the Ktor routes from Chapter 20) depend on the *interface*, swapping the in-memory repo for this database-backed one requires **no changes** above the interface — the payoff of dependency inversion, finally cashed in.
- `ResultRow.toTask()` maps rows to domain objects **inside** each transaction (heeding the §21.2 gotcha), so no `ResultRow` ever escapes. Each method wraps its work in `transaction { }`.
- `insert { … } get Tasks.id` returns the auto-generated id — the standard Exposed idiom for "insert and get the new key."
- This is the shape of a real persistence layer. In [Ch.33](#chapter-33--architecture--dependency-injection) we'll inject `ExposedTaskRepository` (vs the in-memory one for tests) through a DI framework, and in [Ch.36](#chapter-36--advanced-testing) test it against a real database with Testcontainers.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Exposed** | JetBrains' type-safe SQL library for the JVM. |
| **`Table` object** | A Kotlin `object` describing a database table and its columns. |
| **`transaction { }`** | A block that commits on success / rolls back on error. |
| **`ResultRow`** | A returned row; valid only inside its transaction. |
| **`selectAll().where { }`** | The current filtered-query API (old `select { }` is deprecated). |
| **N+1 queries** | The anti-pattern of one query per row in a loop. |
| **Room** | Android's annotation-driven persistence library over SQLite. |
| **`@Entity` / `@Dao` / `@Database`** | Room's table / query-interface / database pieces. |
| **Migration** | An ordered, immutable database schema/data change. |
| **Index / query plan** | Auxiliary lookup structure / database strategy for executing a query. |
| **Connection pool** | A bounded set of reusable database connections. |
| **Optimistic locking** | Detecting concurrent modification with a version predicate. |

### What's next

Your data now survives restarts. **[Ch.22 — Android Development with Kotlin](#chapter-22--android-development-with-kotlin)** brings the Task Manager to a mobile screen with `ViewModel`, `StateFlow`, and Jetpack Compose — reusing the very same `:core` domain and repository you've built.

[↑ back to top](#chapter-21--database-access)


---

## Chapter 22 — Android Development with Kotlin

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Classes](#chapter-8--classes--objects), [Ch.15 — Coroutines](#chapter-15--coroutines--flow)

**Learning objectives** — after this chapter you will be able to:

- Explain the modern Android architecture: `ViewModel` + `StateFlow` + Compose.
- Model UI as immutable state with unidirectional data flow.
- Write a basic Jetpack Compose screen that observes state.
- Reuse a shared domain/`:core` module in an Android app.
- Collect state lifecycle-safely, hoist UI state, model one-off effects, and design an offline-capable data flow.

> Android is a huge topic; this chapter teaches the *Kotlin* patterns that define modern Android (they also apply to Compose Multiplatform desktop/web). The code is illustrative — it runs in an Android project, not a plain `main`.

**In this chapter**

- [22.1 The modern Android architecture](#221-the-modern-android-architecture)
- [22.2 ViewModel and StateFlow](#222-viewmodel-and-stateflow)
- [22.3 Jetpack Compose](#223-jetpack-compose)
- [22.4 Lifecycle-aware collection and state hoisting](#224-lifecycle-aware-collection-and-state-hoisting)
- [22.5 Effects, navigation, and offline-first data](#225-effects-navigation-and-offline-first-data)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-the-task-manager-on-screen) · Glossary · What's next

---

### 22.1 The modern Android architecture

Modern Android apps are built around a few Kotlin-friendly ideas you already know:

- A **`ViewModel`** holds screen state and survives configuration changes (like rotation). It's where your UI logic and coroutines live.
- The UI is described as **immutable state** — a single `data class` (Chapter 8) representing everything the screen shows — held in a **`StateFlow`** (Chapter 15).
- Data flows in **one direction** (*unidirectional data flow*, UDF): the ViewModel exposes state *down* to the UI; the UI sends events *up* to the ViewModel, which updates the state, which re-renders the UI. No two-way tangles.
- The UI itself is built with **Jetpack Compose**, a declarative toolkit where you describe *what* the screen looks like for a given state, and Compose figures out the updates.

This is the same shape as the Ktor backend and the `StateFlow` Task Manager from Chapter 15 — reactive state observed by a consumer. Android just makes the consumer a screen.

### 22.2 ViewModel and StateFlow

A `ViewModel` exposes a read-only `StateFlow` of an immutable UI-state object and updates it in response to events. Coroutines launched in **`viewModelScope`** are automatically cancelled when the ViewModel is destroyed — structured concurrency (Chapter 15) tied to the screen's lifecycle.

```kotlin
import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import kotlinx.coroutines.flow.*
import kotlinx.coroutines.launch

data class Task(val id: Int, val title: String, val done: Boolean = false)

// One immutable object describing the whole screen:
data class TaskUiState(
    val tasks: List<Task> = emptyList(),
    val isLoading: Boolean = false
)

class TaskViewModel(private val repo: TaskRepository) : ViewModel() {
    private val _uiState = MutableStateFlow(TaskUiState())
    val uiState: StateFlow<TaskUiState> = _uiState.asStateFlow()

    fun load() {
        viewModelScope.launch {                         // cancelled automatically with the screen
            _uiState.update { it.copy(isLoading = true) }
            val tasks = repo.all()                       // suspend call to the domain
            _uiState.update { it.copy(tasks = tasks, isLoading = false) }
        }
    }

    fun toggle(id: Int) {
        _uiState.update { state ->
            state.copy(tasks = state.tasks.map {
                if (it.id == id) it.copy(done = !it.done) else it   // immutable update
            })
        }
    }
}
```

Every state change makes a **new** `TaskUiState` via `copy` — the state is never mutated in place. `_uiState.update { … }` atomically applies the change.

> ⚠️ **Gotcha — never mutate state in place.** `StateFlow` (and Compose) detect a change by *comparing* the new value to the old. If you mutate the existing list/object, the reference is unchanged, so no update is emitted and the UI won't refresh. Always produce a *new* object with `copy` and new collections (`+`, `map`, …). This is exactly why Chapter 8 pushed immutable `data class`es.

> ⚠️ **Gotcha** — Launch coroutines in **`viewModelScope`**, not `GlobalScope`. `viewModelScope` cancels its coroutines when the ViewModel is cleared, preventing work (and leaks) that outlive the screen.

### 22.3 Jetpack Compose

**Jetpack Compose** is a declarative UI toolkit: you write `@Composable` functions that describe the UI for the *current* state, and Compose re-invokes them (*recomposition*) when the state they read changes. On Android, `collectAsStateWithLifecycle()` bridges a `StateFlow` into Compose and stops collection while the UI is not active.

```kotlin
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp
import androidx.lifecycle.compose.collectAsStateWithLifecycle

@Composable
fun TaskScreen(viewModel: TaskViewModel) {
    val state by viewModel.uiState.collectAsStateWithLifecycle()

    Column(modifier = Modifier.padding(16.dp)) {
        Text("Tasks (${state.tasks.size})", style = MaterialTheme.typography.headlineSmall)

        if (state.isLoading) {
            CircularProgressIndicator()
        }

        state.tasks.forEach { task ->
            Row {
                Checkbox(
                    checked = task.done,
                    onCheckedChange = { viewModel.toggle(task.id) }   // event flows UP
                )
                Text(task.title)
            }
        }

        Button(onClick = { viewModel.load() }) {
            Text("Refresh")
        }
    }
}
```

Trace the unidirectional flow: `TaskScreen` *reads* `state` (down) and renders it; tapping a checkbox calls `viewModel.toggle(id)` (an event, up); the ViewModel updates `_uiState`; lifecycle-aware collection sees the new state and Compose *recomposes* only the parts that changed. You never manually "update the checkbox" — you change the state, and the UI follows.

> ⚙️ **Under the hood** — Compose tracks which `@Composable`s read which state via a snapshot system. When a `State` (including one produced by lifecycle-aware collection) changes, Compose schedules **recomposition** of composables that read it. It may skip unaffected work; it does not promise a simplistic "one changed widget only" execution model. Composables must therefore be side-effect free and safe to run again.

> ☕ **Coming from Java / old Android** — This replaces XML layouts, `findViewById`, manual view updates, and `AsyncTask`/callbacks. Instead of imperatively poking widgets ("set this text, hide that spinner"), you declare the UI as a function of state and let Compose reconcile it — far less error-prone.

### 22.4 Lifecycle-aware collection and state hoisting

Add `androidx.lifecycle:lifecycle-runtime-compose` and use `collectAsStateWithLifecycle()` in Android UI. Plain `collectAsState()` remains useful in platform-agnostic Compose code, but an Android screen should not keep expensive upstream flows active while stopped.

Separate the route that obtains a ViewModel from a stateless, previewable screen:

```kotlin
sealed interface TaskAction {
    data class TitleChanged(val value: String) : TaskAction
    data class Toggled(val id: Long) : TaskAction
    data object Submitted : TaskAction
    data object Retried : TaskAction
}

@Composable
fun TaskRoute(viewModel: TaskViewModel) {
    val state by viewModel.uiState.collectAsStateWithLifecycle()
    TaskScreen(state = state, onAction = viewModel::onAction)
}

@Composable
fun TaskScreen(state: TaskUiState, onAction: (TaskAction) -> Unit) {
    // pure rendering: easy to preview and screenshot-test
}
```

This is **state hoisting**: the reusable composable receives state plus events and owns no business state. Keep ephemeral widget state locally only when no other component needs it (`rememberSaveable` for restorable UI state). Keys in `LazyColumn` preserve item identity:

```kotlin
LazyColumn {
    items(state.tasks, key = TaskItem::id) { task ->
        TaskRow(task, onToggle = { onAction(TaskAction.Toggled(task.id)) })
    }
}
```

> ⚠️ **Gotcha — unstable work during recomposition.** A composable may run many times. Do not start network calls, mutate repositories, or create expensive objects directly in its body. Events call the ViewModel; Compose effects (`LaunchedEffect`, `DisposableEffect`) are for UI-lifecycle synchronization and must use correct stable keys.

### 22.5 Effects, navigation, and offline-first data

Durable screen facts belong in `uiState`: a validation message that must survive rotation is state. One-time commands such as "navigate after save" or "show this snackbar once" are **effects**. Model them separately and ensure their delivery semantics are intentional:

```kotlin
import kotlinx.coroutines.channels.Channel
import kotlinx.coroutines.flow.receiveAsFlow

sealed interface TaskEffect {
    data class ShowSnackbar(val message: String) : TaskEffect
    data class OpenDetails(val id: Long) : TaskEffect
}

private val _effects = Channel<TaskEffect>(capacity = Channel.BUFFERED)
val effects = _effects.receiveAsFlow()
```

Collect effects in `LaunchedEffect` and call UI-owned navigators/snackbar hosts. Do not put `NavController`, `Context`, or composables in the ViewModel. For events that must not be lost while the UI is absent, model an acknowledged state/process instead of assuming a channel is durable.

For an offline-first screen, the database is the observable source of truth:

```text
Compose ← StateFlow ← ViewModel ← observeTasks() ← Room
                                      ↑
                         sync writes remote results
                                      ↑
                                  Ktor client
```

Writes update local state transactionally and enqueue sync work. A background worker retries with exponential backoff under network/battery constraints. Server ids, local pending state, conflict policy, and idempotency keys are domain decisions—not details to hide in a generic repository.

Test at layers: use-case/ViewModel tests with `runTest`, Compose semantics tests for behavior/accessibility, Room migration tests, and a small number of device end-to-end journeys. Check content descriptions, touch targets, font scaling, screen readers, dark theme, and process recreation before calling a screen shippable.

---

### Summary

- Modern Android = **`ViewModel`** (holds state + coroutines, survives rotation) + **`StateFlow`** (immutable UI-state) + **Compose** (declarative UI), with **unidirectional data flow**: state down, events up.
- UI state is one **immutable `data class`**, updated only via **`copy`** and `_uiState.update { }` — never mutated in place, or `StateFlow`/Compose won't detect the change.
- Launch coroutines in **`viewModelScope`** so they're cancelled with the screen.
- A **`@Composable`** describes the UI for the current state; **`collectAsStateWithLifecycle()`** is the recommended Android bridge from `Flow`; a stateless screen receives state/actions while a route owns the ViewModel.
- Effects, navigation, persistence/sync, accessibility, and process restoration need explicit designs; an offline-first app commonly observes Room as its source of truth.
- The same reactive-state pattern spans backend and Android; the shared domain/`:core` module is reused as-is.

### Self-check quiz

1. Why must UI state be updated with `copy` rather than mutated in place?
   <details><summary>Answer</summary>`StateFlow`/Compose detect change by comparing references/values. Mutating in place leaves the reference unchanged, so no update is emitted and the UI won't refresh. A new object (via `copy`) signals a real change.</details>
2. What does `viewModelScope` give you?
   <details><summary>Answer</summary>A coroutine scope tied to the ViewModel's lifecycle — its coroutines are cancelled when the ViewModel is cleared, preventing leaks and work outliving the screen.</details>
3. What is unidirectional data flow?
   <details><summary>Answer</summary>State flows down (ViewModel → UI) and events flow up (UI → ViewModel); the ViewModel updates state, which re-renders the UI. No two-way binding.</details>
4. How does a Compose screen react to `StateFlow` changes?
   <details><summary>Answer</summary>`collectAsStateWithLifecycle()` turns the flow into Compose `State` while the lifecycle is active; when it changes, Compose recomposes readers and stops unnecessary collection while the screen is inactive.</details>

### Exercises

**Exercise 22.1 — Counter ViewModel (guided).** Write a `CounterViewModel` exposing a `StateFlow<Int>` with `increment`/`decrement`/`reset`.

<details><summary>Show solution</summary>

```kotlin
import androidx.lifecycle.ViewModel
import kotlinx.coroutines.flow.*

class CounterViewModel : ViewModel() {
    private val _count = MutableStateFlow(0)
    val count: StateFlow<Int> = _count.asStateFlow()

    fun increment() { _count.update { it + 1 } }
    fun decrement() { _count.update { it - 1 } }
    fun reset() { _count.value = 0 }
}
```

**Why this works:** the private `MutableStateFlow` holds the count; the public `StateFlow` is read-only for the UI. `update { }` applies each change atomically, and a Compose screen collecting `count` re-renders on every change — the `_state`/`state` encapsulation pattern from Chapter 15.

</details>

**Exercise 22.2 — Immutable list update.** Given `data class UiState(val items: List<String>)` in a `MutableStateFlow`, write an `addItem(s)` that appends without mutating the old state.

<details><summary>Show solution</summary>

```kotlin
fun addItem(state: MutableStateFlow<UiState>, s: String) {
    state.update { it.copy(items = it.items + s) }
}
```

**Why this works:** `it.items + s` creates a *new* list, and `copy` a *new* `UiState`, so the reference changes and observers are notified. Mutating `it.items` in place would go undetected.

</details>

### Chapter project: the Task Manager on screen

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–22 (especially the `:core` domain and Ch.15 flows). We put a Compose UI on the domain via a `TaskViewModel`.

**Goal.** A `TaskViewModel` exposing `StateFlow<TaskUiState>` over the repository, and a `TaskScreen` that lists tasks, toggles them, and adds new ones.

**Requirements.**
1. `TaskUiState` (tasks + loading + input text).
2. `TaskViewModel` with `load`, `toggle`, `updateInput`, `add`.
3. A `TaskScreen` observing the state.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp
import androidx.lifecycle.compose.collectAsStateWithLifecycle
import kotlinx.coroutines.flow.*
import kotlinx.coroutines.launch

data class Task(val id: Int, val title: String, val done: Boolean = false)

data class TaskUiState(
    val tasks: List<Task> = emptyList(),
    val input: String = "",
    val isLoading: Boolean = false
)

class TaskViewModel(private val repo: TaskRepository) : ViewModel() {
    private val _uiState = MutableStateFlow(TaskUiState())
    val uiState: StateFlow<TaskUiState> = _uiState.asStateFlow()

    fun load() = viewModelScope.launch {
        _uiState.update { it.copy(isLoading = true) }
        val tasks = repo.all()
        _uiState.update { it.copy(tasks = tasks, isLoading = false) }
    }

    fun updateInput(text: String) = _uiState.update { it.copy(input = text) }

    fun add() {
        val title = _uiState.value.input.trim()
        if (title.isEmpty()) return
        viewModelScope.launch {
            repo.add(title)
            _uiState.update { it.copy(input = "", tasks = repo.all()) }
        }
    }

    fun toggle(id: Int) = _uiState.update { state ->
        state.copy(tasks = state.tasks.map {
            if (it.id == id) it.copy(done = !it.done) else it
        })
    }
}

@Composable
fun TaskScreen(viewModel: TaskViewModel) {
    val state by viewModel.uiState.collectAsStateWithLifecycle()

    Column(modifier = Modifier.padding(16.dp)) {
        Text("My Tasks (${state.tasks.size})", style = MaterialTheme.typography.headlineSmall)

        Row {
            TextField(value = state.input, onValueChange = viewModel::updateInput)
            Button(onClick = viewModel::add) { Text("Add") }
        }

        if (state.isLoading) CircularProgressIndicator()

        state.tasks.forEach { task ->
            Row {
                Checkbox(checked = task.done, onCheckedChange = { viewModel.toggle(task.id) })
                Text(task.title)
            }
        }
    }
}
```

**Commentary.**
- `TaskViewModel` reuses the **same `TaskRepository`** from Chapters 9/21 — the in-memory one for a demo, the Exposed one for production, injected in (Chapter 33). The UI knows nothing about storage.
- `TaskUiState` bundles *everything the screen needs* — tasks, the text-field input, a loading flag — into one immutable object. Every handler produces a new state via `copy`; nothing is mutated in place.
- `viewModel::updateInput` and `viewModel::add` are **function references** (Chapter 5) wired straight to Compose callbacks — event flowing up. `collectAsStateWithLifecycle()` brings state down while the screen is active. That loop *is* unidirectional data flow.
- The domain we started building in Chapter 1 is now reachable from a CLI (Ch.4), a REST API (Ch.20), and a mobile screen (here) — all sharing one `:core`. In [Ch.34](#chapter-34--kotlin-multiplatform-in-depth) that core becomes truly multiplatform (Android + iOS).

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`ViewModel`** | Holds screen state and logic; survives configuration changes. |
| **UI state** | An immutable `data class` describing everything the screen shows. |
| **Unidirectional data flow (UDF)** | State flows down; events flow up. |
| **`viewModelScope`** | A coroutine scope cancelled when the ViewModel clears. |
| **Jetpack Compose** | Kotlin's declarative UI toolkit. |
| **`@Composable`** | A function describing UI for the current state. |
| **Recomposition** | Compose re-running composables whose state changed. |
| **`collectAsStateWithLifecycle()`** | Android's lifecycle-aware bridge from a `Flow` into Compose `State`. |
| **State hoisting** | Moving state ownership upward so a composable receives state and events. |
| **Effect** | A one-off UI command kept separate from durable screen state. |
| **Offline-first** | Architecture that observes local durable data and synchronizes remotely. |

### What's next

You can ship the Task Manager as a backend and an app. **[Ch.23 — Best Practices & Idioms](#chapter-23--best-practices--idioms)** steps back to consolidate the habits of good Kotlin — immutability, expression bodies, `when`, `Sequence`, avoiding `!!` — and applies them in a guided refactor.

[↑ back to top](#chapter-22--android-development-with-kotlin)


---

## Chapter 23 — Best Practices & Idioms

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** all of Parts 1–3

**Learning objectives** — after this chapter you will be able to:

- Apply the core idioms that make Kotlin concise and safe.
- Recognise anti-patterns (needless mutability, `!!`, over-engineering).
- Refactor naive, Java-flavoured Kotlin into idiomatic Kotlin.

**In this chapter**

- [23.1 Prefer immutability](#231-prefer-immutability)
- [23.2 Expressions over statements](#232-expressions-over-statements)
- [23.3 Null safety without `!!`](#233-null-safety-without)
- [23.4 Small, focused, functional](#234-small-focused-functional)
- [23.5 API design and formatting](#235-api-design-and-formatting)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-an-idiomatic-refactor) · Glossary · What's next

---

### 23.1 Prefer immutability

The single highest-leverage habit: **default to `val` and read-only data**.

```kotlin
val name = "Alice"                      // val over var
val tasks = listOf(task1, task2)        // read-only collection over mutable
data class User(val id: Int, val name: String)   // immutable data class
```

Reach for `var`/`MutableList`/mutable state only when you genuinely need change, and prefer modelling change with `copy` (Chapter 8) over in-place mutation.

> ⚙️ **Under the hood — why it matters.** Immutable data is inherently **thread-safe**: if nothing can change it, no two coroutines/threads can corrupt it, and you need no locks (Chapter 27). It also makes equality and hashing stable (safe `Set`/`Map` keys, Chapter 8) and makes `StateFlow`/Compose change-detection work (Chapter 22). Immutability isn't a stylistic preference — it removes whole categories of bugs.

### 23.2 Expressions over statements

Kotlin makes `if`, `when`, and `try` **expressions** (Chapters 4, 16). Use them to compute values directly, and prefer **single-expression** function bodies (Chapter 5):

```kotlin
// Idiomatic:
fun grade(score: Int) = when {
    score >= 90 -> "A"
    score >= 80 -> "B"
    else -> "C"
}

fun isEven(n: Int) = n % 2 == 0

val label = if (task.done) "done" else "pending"
```

Prefer a `when` over a long `if/else if` chain — it's flatter and, over `enum`/`sealed`, exhaustively checked (Chapter 10). Use **named arguments** at call sites where the meaning isn't obvious (Chapter 5):

```kotlin
createUser(name = "Alice", age = 25, active = true)   // self-documenting
```

### 23.3 Null safety without `!!`

Use the null-safety toolkit (Chapter 7) and treat `!!` as a red flag:

```kotlin
// Avoid:
val len = name!!.length

// Prefer:
val len = name?.length ?: 0
val user = repo.find(id) ?: return   // guard clause
account.token?.let { authenticate(it) }
```

Handle nullability **at the boundary** (parse input, cross the Java line) and keep the interior of your code non-null. Every `!!` is a promise the compiler can't verify — and a future NPE waiting for the day your promise is wrong.

### 23.4 Small, focused, functional

- Write **small functions** that do one thing; extract helpers (local functions, extensions).
- Use the **collection operators** (`filter`/`map`/`groupBy`, Chapter 6) instead of manual loops with mutable accumulators.
- Add **extension functions** (Chapter 11) for utilities rather than `Util` classes.
- Use a **`Sequence`** for large, multi-step pipelines (Chapter 6) — but *not* for small collections, where eager operators are simpler and often faster.

```kotlin
// Loop-and-accumulate (Java style):
val result = mutableListOf<String>()
for (t in tasks) if (!t.done) result.add(t.title.uppercase())

// Idiomatic Kotlin:
val result = tasks.filter { !it.done }.map { it.title.uppercase() }
```

> ⚠️ **Gotcha — don't over-apply idioms.** Idioms are tools, not obligations. Nesting scope functions with mixed `this`/`it` (Chapter 14), wrapping tiny collections in `asSequence()`, or building elaborate generics/DSLs for a one-off need all *reduce* clarity. The goal is readable code; if an "idiomatic" version is harder to follow than a plain loop, use the plain loop.

### 23.5 API design and formatting

When you design types and functions others (or future-you) will use:

- **Expose the most abstract type that works** (`List` not `ArrayList`, an interface not a concrete class — Chapter 9).
- **Make nullability meaningful**: return `T?` when "absent" is normal; return a **`sealed` result** (Chapter 10) or `Result` (Chapter 16) when there are several distinct outcomes — richer than a bare `Boolean`.
- **Keep mutable state private** and expose read-only views (Chapter 8) — the `_state`/`state` pattern (Chapter 15).
- **Format consistently.** Adopt the official Kotlin style and enforce it automatically with **ktlint** or **detekt** (linters that catch style issues and some bugs) in your build. Consistent formatting removes an entire class of review noise. (Public library APIs get deeper treatment in [Ch.35](#chapter-35--designing-libraries--public-apis).)

---

### Summary

- **Prefer immutability** (`val`, read-only collections, immutable data classes, `copy` over mutation) — it's thread-safe, hash-stable, and reactive-friendly.
- Use **expressions** (`if`/`when`/`try`) and **single-expression** functions; `when` over `if/else if` chains; **named arguments** for clarity.
- Handle null with **`?.`/`?:`/`?.let`/guard clauses**; treat **`!!` as a red flag**; deal with nullability at boundaries.
- Write **small, focused** functions; use **collection operators** and **extensions**; reach for **`Sequence`** only for big, multi-step pipelines.
- Design APIs around **abstractions**, meaningful nullability/sealed results, and **private mutable state**; enforce style with **ktlint/detekt**.
- Idioms serve readability — **don't over-apply** them.

### Self-check quiz

1. Give two concrete benefits of preferring immutability.
   <details><summary>Answer</summary>Any two of: thread-safety (no locks needed), stable `hashCode`/`equals` (safe as collection keys), reliable change-detection for `StateFlow`/Compose, and easier reasoning (values can't change unexpectedly).</details>
2. When should you *not* use a `Sequence`?
   <details><summary>Answer</summary>For small collections or single operations — the per-element overhead makes eager operators simpler and often faster. Use `Sequence` for large, multi-step (short-circuitable) pipelines.</details>
3. Why prefer a `sealed` result or `Result` over a `Boolean` return?
   <details><summary>Answer</summary>A `Boolean` can't distinguish *which* outcome occurred (e.g. "not found" vs "invalid"); a sealed/`Result` type carries the specific case and any data, and enables exhaustive handling.</details>
4. What's wrong with sprinkling `!!` to satisfy the compiler?
   <details><summary>Answer</summary>Each `!!` is an unverifiable non-null promise that becomes an NPE when wrong — reintroducing exactly the crashes null safety exists to prevent.</details>

### Exercises

**Exercise 23.1 — De-Java-ify (guided).** Rewrite this Java-flavoured Kotlin idiomatically:
```kotlin
fun titlesOfDone(tasks: List<Task>): List<String> {
    var result = ArrayList<String>()
    for (i in 0 until tasks.size) {
        if (tasks.get(i).done == true) {
            result.add(tasks.get(i).title)
        }
    }
    return result
}
```

<details><summary>Show solution</summary>

```kotlin
fun titlesOfDone(tasks: List<Task>): List<String> =
    tasks.filter { it.done }.map { it.title }
```

**Why this works:** the manual index loop, mutable accumulator, `.get(i)`, and `== true` are all Java habits. Idiomatic Kotlin expresses "keep done tasks, take their titles" as `filter { it.done }.map { it.title }` — a single expression, no mutation, no indices, and `it.done` (a `Boolean`) needs no `== true`.

</details>

**Exercise 23.2 — Kill the `!!`.** Rewrite `val name = user!!.profile!!.displayName!!` to yield `"Unknown"` if any link is null.

<details><summary>Show solution</summary>

```kotlin
val name = user?.profile?.displayName ?: "Unknown"
```

**Why this works:** the safe-call chain short-circuits to null if any link is absent, and Elvis supplies the default — no exception, no `!!`, and a clean non-null `String`.

</details>

### Chapter project: an idiomatic refactor

> 🛠️ **Chapter Project** — Advances the running **Task Manager** (refactor pass). **Builds on:** Ch.1–23. We take a deliberately naive version and refactor it into idiomatic Kotlin.

**Goal.** Transform a Java-flavoured `TaskManager` into clean, idiomatic Kotlin, fixing each anti-pattern.

<details><summary>Show before/after + commentary</summary>

**Before** (works, but full of anti-patterns):

```kotlin
class TaskManager {
    var tasks = ArrayList<Task>()                 // public mutable, concrete type

    fun addTask(t: Task) {
        tasks.add(t)
    }

    fun getDoneTasks(): ArrayList<Task> {         // concrete return type
        var result = ArrayList<Task>()
        for (i in 0 until tasks.size) {           // index loop + mutable accumulator
            if (tasks.get(i).done == true) {      // .get + == true
                result.add(tasks.get(i))
            }
        }
        return result
    }

    fun findTask(id: Int): Task {                 // non-null return...
        for (t in tasks) {
            if (t.id == id) return t
        }
        return null!!                             // ...forced with a crash-on-miss !!
    }
}
```

**After** (idiomatic):

```kotlin
class TaskManager {
    private val tasks = mutableListOf<Task>()     // private, read-only reference, factory fn

    fun add(task: Task) { tasks.add(task) }

    fun doneTasks(): List<Task> =                 // abstract return type, single expression
        tasks.filter { it.done }                   // operator instead of loop

    fun find(id: Int): Task? =                     // honest nullable return
        tasks.firstOrNull { it.id == id }          // no !!, no crash on miss

    fun all(): List<Task> = tasks.toList()         // read-only snapshot
}
```

**Commentary — what changed and why:**
- `var tasks = ArrayList<Task>()` → `private val tasks = mutableListOf<Task>()`: the state is now **encapsulated** (private, Chapter 8), the *reference* is `val`, and we use the factory function and abstract type rather than `ArrayList` directly.
- `getDoneTasks()` returning `ArrayList` with an index loop → `doneTasks(): List<Task> = tasks.filter { it.done }`: **abstract return type**, **single expression**, **collection operator** instead of a manual loop + mutable accumulator. And `it.done` needs no `== true`.
- `findTask(): Task` with `return null!!` → `find(): Task?` with `firstOrNull`: the function is now **honest about absence** (`Task?`), and the `!!` (a guaranteed crash on a miss) is gone. Callers handle the null with `?:` — the Chapter 7 discipline.
- `all()` returns a `toList()` **snapshot**, so callers can't mutate our internal list (Chapter 6's read-only ≠ immutable).

Same behaviour, a fraction of the code, and every anti-pattern removed. This is the difference between *writing Java in Kotlin* and *writing Kotlin*.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Idiom** | A conventional, readable Kotlin way of doing something. |
| **Immutability** | Preferring `val`/read-only/`copy` over mutable state. |
| **Expression body** | A single-expression function via `=`. |
| **Guard clause** | An early `?: return`/`?: throw` handling a bad case up front. |
| **ktlint / detekt** | Linters enforcing style / catching issues in the build. |
| **Over-engineering** | Applying idioms/abstractions beyond what the problem needs. |

### What's next

Idiomatic code deserves a safety net. **[Ch.24 — Testing in Kotlin](#chapter-24--testing-in-kotlin)** covers JUnit Platform/Jupiter, MockK, and coroutine testing, and builds a real test suite for the Task Manager — proving the refactors above didn't change behaviour.

[↑ back to top](#chapter-23--best-practices--idioms)


---

## Chapter 24 — Testing in Kotlin

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Interfaces](#chapter-9--inheritance--interfaces), [Ch.15 — Coroutines](#chapter-15--coroutines--flow), [Ch.19 — Gradle](#chapter-19--gradle-with-kotlin-dsl)

**Learning objectives** — after this chapter you will be able to:

- Write unit tests with JUnit Jupiter and Kotlin's assertions.
- Test for exceptions and use readable test names.
- Isolate code under test with MockK.
- Test `suspend` functions with `runTest`.

**In this chapter**

- [24.1 Setup and your first test](#241-setup-and-your-first-test)
- [24.2 Assertions and exceptions](#242-assertions-and-exceptions)
- [24.3 Mocking with MockK](#243-mocking-with-mockk)
- [24.4 Testing coroutines](#244-testing-coroutines)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-testing-the-task-manager)· Glossary · What's next

---

### 24.1 Setup and your first test

Tests prove your code does what you claim — and, crucially, keep proving it as you change things. The current JVM stack is the **JUnit Platform** with the **Jupiter** engine plus Kotlin's **`kotlin.test`** assertions. JUnit 6 keeps the Jupiter API/package names; Kotlin's adapter is still named `kotlin-test-junit5` for compatibility.

```kotlin
dependencies {
    testImplementation(kotlin("test-junit5"))
    testImplementation("org.junit.jupiter:junit-jupiter:6.0.1")
}
tasks.test { useJUnitPlatform() }
```

A test is a function annotated **`@Test`**. Kotlin lets you use **backtick names** with spaces, so tests read as sentences:

```kotlin
import kotlin.test.Test
import kotlin.test.assertEquals

class Calculator {
    fun add(a: Int, b: Int) = a + b
}

class CalculatorTest {
    @Test
    fun `add returns the sum of its arguments`() {
        val calc = Calculator()
        val result = calc.add(2, 3)     // Act
        assertEquals(5, result)          // Assert
    }
}
```

The structure is **Arrange–Act–Assert**: set up inputs, perform the action, assert the outcome. `assertEquals(expected, actual)` fails the test if they differ.

> 💡 **Idiom** — Name tests for the *behaviour* they verify (`` `withdraw fails when balance is insufficient` ``), not the method (`testWithdraw`). A failing test's name should tell you what broke without reading the body.

### 24.2 Assertions and exceptions

`kotlin.test` provides `assertEquals`, `assertTrue`/`assertFalse`, `assertNull`/`assertNotNull`, and more. To assert that code **throws**, use `assertFailsWith`:

```kotlin
import kotlin.test.*

class Account(private var balance: Int) {
    fun withdraw(amount: Int) {
        require(amount <= balance) { "insufficient funds" }
        balance -= amount
    }
    fun balance() = balance
}

class AccountTest {
    @Test
    fun `withdraw reduces balance`() {
        val account = Account(100)
        account.withdraw(30)
        assertEquals(70, account.balance())
    }

    @Test
    fun `withdraw beyond balance throws`() {
        val account = Account(100)
        val ex = assertFailsWith<IllegalArgumentException> {
            account.withdraw(200)
        }
        assertEquals("insufficient funds", ex.message)
    }
}
```

`assertFailsWith<T> { … }` passes only if the block throws a `T` (and returns it, so you can assert on its message). For richer assertions (fluent matchers, `assertThat(x).isEqualTo(...)`) many teams add **AssertJ** or **Kotest** (Chapter 36).

### 24.3 Mocking with MockK

To test a class in **isolation**, you replace its dependencies with **test doubles**. **MockK** is Kotlin's mocking library — it handles Kotlin's `final`-by-default classes and `suspend` functions natively (Mockito can't, easily).

Create a mock with `mockk<T>()`, stub behaviour with `every { … } returns …`, and confirm interactions with `verify { … }`:

```kotlin
import io.mockk.*
import kotlin.test.*

interface UserRepository { fun findName(id: Int): String? }

class Greeter(private val repo: UserRepository) {
    fun greet(id: Int) = "Hello, ${repo.findName(id) ?: "stranger"}"
}

class GreeterTest {
    @Test
    fun `greets a known user by name`() {
        val repo = mockk<UserRepository>()
        every { repo.findName(1) } returns "Alice"     // stub

        val result = Greeter(repo).greet(1)

        assertEquals("Hello, Alice", result)
        verify { repo.findName(1) }                     // confirm it was called
    }

    @Test
    fun `greets stranger when name is missing`() {
        val repo = mockk<UserRepository>()
        every { repo.findName(any()) } returns null     // any() matches any argument

        assertEquals("Hello, stranger", Greeter(repo).greet(99))
    }
}
```

The mock lets you test `Greeter`'s logic without a real repository/database — fast, deterministic, and focused on *one* unit.

> ⚙️ **Under the hood** — MockK generates a subclass/proxy of the mocked type at runtime (via bytecode manipulation), intercepting calls to return your stubbed values and record invocations. Because it operates at the bytecode level, it can mock `final` classes and `suspend` functions — a common pain point with Java's Mockito.

> ⚠️ **Gotcha — test behaviour, not implementation.** Over-mocking and asserting on *every* internal call (`verify` on private helpers) makes tests brittle: they break on harmless refactors. Prefer asserting on observable *outcomes* (return values, state), and reserve `verify` for genuinely important interactions (e.g. "the payment was actually charged").

### 24.4 Testing coroutines

Testing `suspend` code with real `delay`s would be slow. The **`runTest`** builder (from `kotlinx-coroutines-test`) runs coroutines on a **virtual-time** scheduler that *skips* delays instantly while preserving ordering:

```kotlin
dependencies {
    testImplementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.11.0")
}
```

```kotlin
import kotlinx.coroutines.delay
import kotlinx.coroutines.test.runTest
import kotlin.test.*

class DataFetcher {
    suspend fun fetch(): String {
        delay(1000)           // in a real test this is skipped instantly
        return "data"
    }
}

class DataFetcherTest {
    @Test
    fun `fetch returns data`() = runTest {
        val result = DataFetcher().fetch()
        assertEquals("data", result)
    }
}
```

The test finishes in milliseconds, not a second, because `runTest` fast-forwards virtual time through the `delay`. For mocking `suspend` functions, MockK provides **`coEvery`**/**`coVerify`** (the coroutine-aware versions of `every`/`verify`).

> ⚙️ **Under the hood** — `runTest` installs a `TestDispatcher` whose clock is virtual. `delay(1000)` doesn't wait a real second; it *advances the virtual clock* by 1000ms, so all the timing logic runs but the wall-clock test is instant. You can also `advanceTimeBy(...)` manually to test time-dependent behaviour deterministically. (Deeper flow/coroutine testing — Turbine, `TestScope` — is in [Ch.36](#chapter-36--advanced-testing).)

---

### Summary

- Tests use **JUnit Platform/Jupiter** + **`kotlin.test`**; a **`@Test`** function follows **Arrange–Act–Assert**, and **backtick names** describe behaviour.
- Assert with `assertEquals`/`assertTrue`/`assertNull`/…; assert throwing with **`assertFailsWith<T> { }`** (which returns the exception).
- **MockK** replaces dependencies with test doubles: `mockk`, `every { } returns`, `verify { }` (and `coEvery`/`coVerify` for `suspend`). It handles `final` classes and coroutines natively.
- Test `suspend` code with **`runTest`**, which uses **virtual time** to skip delays instantly.
- **Test behaviour, not implementation** — assert outcomes, don't over-`verify` internals.

### Self-check quiz

1. Why name tests after behaviour rather than the method?
   <details><summary>Answer</summary>A behaviour name (`` `withdraw fails when insufficient` ``) tells you what broke from the failure report alone, and stays valid across refactors of the method's internals.</details>
2. How do you assert that a call throws a specific exception?
   <details><summary>Answer</summary>`assertFailsWith<TheException> { code() }` — it passes only if that exception type is thrown, and returns it so you can assert on its message.</details>
3. Why use MockK over Mockito in Kotlin?
   <details><summary>Answer</summary>MockK natively handles Kotlin's `final`-by-default classes and `suspend` functions (`coEvery`/`coVerify`), which Mockito struggles with.</details>
4. What does `runTest` do with `delay`?
   <details><summary>Answer</summary>It runs on a virtual-time scheduler that fast-forwards through delays instantly, so timing logic executes but the test doesn't actually wait.</details>

### Exercises

**Exercise 24.1 — Test a pure function (guided).** Write tests for `fun isPalindrome(s: String): Boolean` covering a palindrome, a non-palindrome, and the empty string.

<details><summary>Show solution</summary>

```kotlin
import kotlin.test.*

fun isPalindrome(s: String): Boolean {
    val clean = s.lowercase().filter { it.isLetterOrDigit() }
    return clean == clean.reversed()
}

class PalindromeTest {
    @Test fun `detects a palindrome`() = assertTrue(isPalindrome("Racecar"))
    @Test fun `rejects a non-palindrome`() = assertFalse(isPalindrome("hello"))
    @Test fun `treats empty as palindrome`() = assertTrue(isPalindrome(""))
}
```

**Why this works:** three focused tests cover the meaningful cases. Using `assertTrue`/`assertFalse` reads naturally, and single-expression test bodies keep them compact. (An empty string equals its own reverse, so it's trivially a palindrome.)

</details>

**Exercise 24.2 — Mock a dependency.** A `PriceService(private val rates: RateProvider)` computes `priceInUsd(eur)` as `eur * rates.usdPerEur()`. Test it with a mocked `RateProvider` returning `1.1`.

<details><summary>Show solution</summary>

```kotlin
import io.mockk.*
import kotlin.test.*

interface RateProvider { fun usdPerEur(): Double }

class PriceService(private val rates: RateProvider) {
    fun priceInUsd(eur: Double) = eur * rates.usdPerEur()
}

class PriceServiceTest {
    @Test
    fun `converts eur to usd using the rate`() {
        val rates = mockk<RateProvider>()
        every { rates.usdPerEur() } returns 1.1

        val result = PriceService(rates).priceInUsd(100.0)

        assertEquals(110.0, result, 0.0001)   // tolerance for Double comparison
    }
}
```

**Why this works:** the mocked `RateProvider` gives a fixed, deterministic rate, so the test isolates `PriceService`'s arithmetic (`100.0 * 1.1 = 110.0`). Note the third `assertEquals` argument — a tolerance — because comparing `Double`s exactly is unsafe (Chapter 3).

</details>

### Chapter project: testing the Task Manager

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–24. We write a real test suite: pure-logic unit tests, a MockK-mocked repository, and a `runTest` for a suspend function.

**Goal.** Test a `TaskService` in isolation from its repository, covering validation, delegation, and a suspend sync.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import io.mockk.*
import kotlinx.coroutines.test.runTest
import kotlin.test.*

data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {
    fun add(title: String): Task
    suspend fun sync(): Int
}

class TaskService(private val repo: TaskRepository) {
    fun addIfValid(title: String): Task? =
        if (title.isBlank()) null else repo.add(title.trim())

    suspend fun syncAndCount(): Int = repo.sync()
}

class TaskServiceTest {

    @Test
    fun `addIfValid rejects a blank title and never touches the repo`() {
        val repo = mockk<TaskRepository>()
        val service = TaskService(repo)

        assertNull(service.addIfValid("   "))
        verify(exactly = 0) { repo.add(any()) }   // important interaction: repo NOT called
    }

    @Test
    fun `addIfValid trims and delegates a valid title`() {
        val repo = mockk<TaskRepository>()
        every { repo.add("Write tests") } returns Task(1, "Write tests")
        val service = TaskService(repo)

        val result = service.addIfValid("  Write tests  ")

        assertEquals("Write tests", result?.title)
        verify { repo.add("Write tests") }         // trimmed value was passed through
    }

    @Test
    fun `syncAndCount returns the repository count`() = runTest {
        val repo = mockk<TaskRepository>()
        coEvery { repo.sync() } returns 42          // coEvery for a suspend fun
        val service = TaskService(repo)

        assertEquals(42, service.syncAndCount())
        coVerify { repo.sync() }
    }
}
```

**Commentary.**
- Each test isolates `TaskService` from any real storage with a **MockK** double, so they're fast and deterministic — no database, no I/O.
- The first test asserts an *interaction that should NOT happen* (`verify(exactly = 0)`): a blank title must be rejected *before* the repo is touched. That's a meaningful behaviour, worth verifying.
- The second checks both the outcome (`result?.title`) *and* that the **trimmed** value reached the repo (`verify { repo.add("Write tests") }`) — catching a subtle bug where trimming might be skipped.
- The third uses **`runTest`** and **`coEvery`/`coVerify`** to test the `suspend` path. No real delay, no real network — the suspend function is fully under test.
- Notice these tests would have caught any behaviour change in the Chapter 23 refactor — which is exactly why you write them.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **JUnit Platform / Jupiter** | The JVM test launcher/engine (`@Test`, `useJUnitPlatform()`); current major is JUnit 6. |
| **`kotlin.test`** | Kotlin's assertion library (`assertEquals`, `assertFailsWith`, …). |
| **Arrange–Act–Assert** | The three-part structure of a good test. |
| **`assertFailsWith<T>`** | Asserts a block throws `T` (returns the exception). |
| **Test double / mock** | A stand-in for a real dependency. |
| **MockK** | Kotlin's mocking library; handles `final`/`suspend`. |
| **`every` / `verify`** | Stub behaviour / confirm an interaction (`coEvery`/`coVerify` for suspend). |
| **`runTest`** | Runs coroutine tests on virtual time (skips delays). |

### What's next

Your code is idiomatic and tested. **[Ch.25 — Advanced Topics & Next Steps](#chapter-25--advanced-topics--next-steps)** closes Part 4 with `inline` functions, contracts, a reflection primer, and a first look at Kotlin Multiplatform — extracting the Task Manager's core to share across platforms, setting up the deep dives in Part 5.

[↑ back to top](#chapter-24--testing-in-kotlin)


---

## Chapter 25 — Advanced Topics & Next Steps

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Functions](#chapter-5--functions), [Ch.12 — Generics](#chapter-12--generics), [Ch.15 — Coroutines](#chapter-15--coroutines--flow)

**Learning objectives** — after this chapter you will be able to:

- Explain what `inline` functions do and when to use them.
- Understand contracts and how they help the compiler.
- Use reflection basics (`::class`, member references).
- Grasp Kotlin Multiplatform's `expect`/`actual` and share a core module.
- Apply Kotlin 2.4 language features—context parameters, guards, explicit backing fields, and multi-dollar interpolation—where they improve design.

> This chapter *introduces* topics that Part 5 explores in depth: `inline` (here) → performance ([Ch.32](#chapter-32--performance--memory)); reflection (here) → [Ch.29](#chapter-29--reflection--annotations); KSP (mentioned) → [Ch.30](#chapter-30--metaprogramming-ksp--compiler-plugins); Kotlin Multiplatform (here) → [Ch.34](#chapter-34--kotlin-multiplatform-in-depth).

**In this chapter**

- [25.1 Inline functions](#251-inline-functions)
- [25.2 Contracts](#252-contracts)
- [25.3 Reflection basics](#253-reflection-basics)
- [25.4 Kotlin Multiplatform](#254-kotlin-multiplatform)
- [25.5 Kotlin 2.4 language evolution](#255-kotlin-24-language-evolution)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-shareable-core)· Glossary · What's next

---

### 25.1 Inline functions

You've used many higher-order functions (`filter`, `let`, `apply`). Each lambda is normally a small heap object. For functions called in hot loops, that allocation adds up. Marking a function **`inline`** tells the compiler to **copy the function's body — and its lambda's body — directly into the call site**, eliminating the lambda object and the call entirely.

```kotlin
inline fun <T> measured(label: String, block: () -> T): T {
    val start = System.nanoTime()
    val result = block()                       // block is inlined — no lambda object
    println("$label took ${(System.nanoTime() - start) / 1_000_000}ms")
    return result
}

fun main() {
    val sum = measured("sum") {
        (1..1_000_000).sum()
    }
    println(sum)
}
```

At compile time, the `measured(...) { … }` call is replaced by the timing code with the lambda body pasted in — as if you'd written it by hand. This is exactly the mechanism behind the scope functions (Chapter 14) and `reified` generics (Chapter 12): both *require* inlining.

Two modifiers refine it: **`noinline`** (on a specific lambda parameter) opts one lambda *out* of inlining (e.g. to store it in a variable); **`crossinline`** forbids a lambda from doing a non-local `return` (needed when the lambda is called from another execution context).

> ⚙️ **Under the hood** — Inlining trades code size for speed: the body is duplicated at every call site, so a *large* inline function called in many places bloats the bytecode. Reserve `inline` for **small** higher-order functions where removing lambda allocation matters (utilities, hot paths), or where you need `reified`/non-local returns. The standard library's `inline` functions are all tiny for this reason. (Measuring, not guessing, is the theme of [Ch.32](#chapter-32--performance--memory).)

### 25.2 Contracts

Sometimes *you* know something about a function's behaviour that the compiler can't infer — for instance, that "if this returns `false`, the argument was non-null." A **contract** communicates such a fact to the compiler, improving smart-casting across the function boundary.

This is how the standard library's own `isNullOrEmpty()` lets a smart cast survive the call. Here's an illustrative reimplementation (renamed so it doesn't shadow the real one):

```kotlin
import kotlin.contracts.*

@OptIn(ExperimentalContracts::class)
fun CharSequence?.isNullOrEmptyDemo(): Boolean {
    contract {
        returns(false) implies (this@isNullOrEmptyDemo != null)
    }
    return this == null || this.length == 0
}

fun demo(text: String?) {
    if (!text.isNullOrEmptyDemo()) {
        println(text.length)   // smart-cast to non-null — thanks to the contract
    }
}
```

The `contract { returns(false) implies (… != null) }` tells the compiler: "when this returns `false`, the receiver is not null." So inside the `if (!…)` branch, `text` is smart-cast to a non-null `String`.

> ⚠️ **Gotcha** — The contracts DSL is still an **experimental/opt-in** API (`@OptIn(ExperimentalContracts::class)`) and has strict rules (the `contract { }` call must be the first statement). You'll *rely on* contracts constantly (every `require`, `isNullOrEmpty`, `check` has one) but rarely need to *write* your own. Know they exist so the smart-casts they enable don't seem like magic.

### 25.3 Reflection basics

**Reflection** lets a program inspect its own types at runtime. The entry point is the **`::class`** literal, which gives a `KClass`:

```kotlin
data class Task(val id: Int, val title: String)

fun main() {
    val kClass = Task::class
    println(kClass.simpleName)                       // → Task
    println(kClass.members.map { it.name })          // property/function names

    // Member references (Chapter 5's `::`):
    val titleRef = Task::title                        // a property reference
    val task = Task(1, "Learn reflection")
    println(titleRef.get(task))                       // → Learn reflection
}
```

Reflection powers serialization fallbacks, dependency injection, and test frameworks. Full reflection (`kotlin-reflect`) is a separate dependency and comparatively slow, so it's used judiciously — [Ch.29](#chapter-29--reflection--annotations) covers it (and annotations) in depth.

### 25.4 Kotlin Multiplatform

Kotlin runs not only on the JVM but also compiles to **native** (iOS, desktop), **JavaScript**, and **WebAssembly**. **Kotlin Multiplatform (KMP)** lets you write shared logic *once* in a `commonMain` source set and reuse it across all targets, dropping to platform-specific code only where necessary.

The bridge is **`expect`/`actual`**: `commonMain` *declares* what it needs with `expect`; each platform *provides* it with `actual`.

```kotlin
// commonMain — shared code, no platform APIs
expect fun platformName(): String

fun greeting(): String = "Hello from ${platformName()}"
```

```kotlin
// jvmMain
actual fun platformName(): String = "JVM"
```

```kotlin
// iosMain / nativeMain
actual fun platformName(): String = "iOS"
```

Shared `commonMain` code can use the multiplatform `kotlinx` libraries (coroutines, serialization, datetime), so a whole domain layer — models, business logic, networking — can be written once and consumed by an Android app, an iOS app, and a backend.

> ⚙️ **Under the hood** — There's no runtime bridge or shared VM. Each target *compiles* `commonMain` + its own `actual`s to that platform's native format: JVM bytecode for Android/backend, a native binary (via LLVM) for iOS, JavaScript for the web. The sharing happens at the *source* level, resolved at compile time — which is why KMP has no per-call overhead. ([Ch.34](#chapter-34--kotlin-multiplatform-in-depth) goes deep, including Compose Multiplatform.)

### 25.5 Kotlin 2.4 language evolution

Kotlin 2.4 stabilizes several features that older guides either omit or label experimental.

**Context parameters** make a required ambient capability part of a signature without threading it through every call:

```kotlin
interface AuditLog { fun record(message: String) }

context(log: AuditLog)
fun Task.complete(): Task {
    log.record("completed task $id")
    return copy(done = true)
}

fun demo(task: Task, audit: AuditLog) {
    context(audit) {
        task.complete()
    }
}
```

The dependency is still statically required and visible in the declaration. Use context parameters for truly scoped capabilities (transactions, tracing, DSL contexts), not to hide an application's entire dependency graph. Prefer ordinary constructor/function parameters when ownership and data flow should be explicit. Older **context receiver** syntax is superseded by named context parameters.

**Guard conditions** flatten conditional branches in `when`:

```kotlin
fun nextAction(task: Task) = when (task) {
    is TimedTask if task.isOverdue -> "escalate"
    is TimedTask -> "wait"
    is ChecklistTask if task.items.all { it.done } -> "complete"
    else -> "review"
}
```

**Explicit backing fields** make a property's storage contract visible when its public and stored types differ:

```kotlin
class TaskBasket {
    val tasks: List<Task>
        field: MutableList<Task> = mutableListOf()

    fun add(task: Task) {
        tasks.add(task) // smart-cast to the private backing-field type in this class
    }
}
```

Outside `TaskBasket`, callers see only `List<Task>`; inside its private scope, the compiler knows the backing field is `MutableList<Task>`. The property must be a non-open `val` without a custom getter or delegation, and the backing-field type must be a private subtype of the public property type.

**Multi-dollar interpolation** makes templates containing literal dollar signs readable. The number of leading dollars sets how many start interpolation:

```kotlin
val name = "task"
val jsonTemplate = $$"""
    { "shell": "$HOME", "kotlin": "$$name" }
""".trimIndent()
```

With `$$`, a single `$` is literal and `$$name` interpolates. This is especially useful for JSON schemas, shell snippets, and templating languages.

Kotlin 2.4 also includes stable/common UUID APIs (except generation variants that remain opt-in), better annotation use-site defaults, and newer collection helpers. Read release notes during upgrades: language compatibility, compiler, Gradle, Native/Swift export, and stdlib evolve independently.

---

### Summary

- **`inline`** copies a function's (and its lambdas') bodies into the call site, removing lambda allocation and call overhead — great for small hot-path utilities, and *required* for `reified` and non-local returns. `noinline`/`crossinline` refine which lambdas inline. It trades code size for speed.
- **Contracts** tell the compiler facts it can't infer (e.g. "returns false ⇒ non-null"), enabling smart-casts across function calls; you mostly *use* them (via `require`/`isNullOrEmpty`) rather than write them (they're experimental).
- **Reflection** (`::class` → `KClass`, member references) inspects types at runtime; powerful but comparatively costly.
- **Kotlin Multiplatform** shares a `commonMain` core across JVM/native/JS/Wasm via **`expect`/`actual`**; each target compiles the common code plus its actuals natively — no runtime bridge.
- Kotlin 2.4 stabilizes **context parameters**, guard conditions, explicit backing fields, and multi-dollar interpolation; use them to clarify contracts, not merely because they are new.

### Self-check quiz

1. What does `inline` eliminate, and what's the cost?
   <details><summary>Answer</summary>It eliminates the lambda object and the call by copying bodies into the call site; the cost is larger bytecode (the body is duplicated per call site), so it suits small functions.</details>
2. Which earlier features *require* inlining?
   <details><summary>Answer</summary>`reified` type parameters (Chapter 12) and non-local returns from lambdas; the scope functions (Chapter 14) are also inline for zero overhead.</details>
3. What do contracts enable, and do you usually write them?
   <details><summary>Answer</summary>They let the compiler smart-cast across a function boundary based on the function's outcome (e.g. `require`/`isNullOrEmpty`). You mostly rely on existing ones rather than writing your own.</details>
4. How does KMP share code without a runtime bridge?
   <details><summary>Answer</summary>Each target compiles the shared `commonMain` plus its platform `actual`s to that platform's native format (bytecode/native/JS) — sharing is resolved at compile time, so there's no runtime cost.</details>

### Exercises

**Exercise 25.1 — An inline timer (guided).** Write an `inline` function `time(block)` that returns the block's result and prints how long it took.

<details><summary>Show solution</summary>

```kotlin
inline fun <T> time(block: () -> T): T {
    val start = System.nanoTime()
    val result = block()
    println("Elapsed: ${(System.nanoTime() - start) / 1_000_000}ms")
    return result
}

fun main() {
    val total = time { (1..1_000_000).sum() }
    println(total)   // → 500000500000
}
```

**Why this works:** because `time` is `inline`, the `{ (1..1_000_000).sum() }` lambda is pasted directly into `time`'s body at compile time — no lambda object is allocated, so the timing wrapper is essentially free. The block returns the sum, which `time` returns unchanged.

</details>

**Exercise 25.2 — `expect`/`actual`.** Sketch a multiplatform `expect fun randomId(): String` with a JVM `actual` using `java.util.UUID`.

<details><summary>Show solution</summary>

```kotlin
// commonMain
expect fun randomId(): String

// jvmMain
actual fun randomId(): String = java.util.UUID.randomUUID().toString()
```

**Why this works:** `commonMain` declares the *capability* (`expect`) without knowing how any platform provides it; the JVM source set supplies the *implementation* (`actual`) using a JVM-only API (`UUID`). Other targets (iOS, JS) would provide their own `actual` using their platform's random/UUID facility.

</details>

### Chapter project: a shareable core

> 🛠️ **Chapter Project** — Advances the running **Task Manager** (a capstone step toward Part 5). **Builds on:** Ch.1–25. We extract the domain into a multiplatform-ready `commonMain` core with an `expect` storage seam and an `inline` timing helper.

**Goal.** Structure the Task Manager domain so it can be shared across platforms, with platform storage abstracted via `expect`/`actual`.

<details><summary>Show reference solution + commentary</summary>

```kotlin
// ---------- commonMain ----------  (shared, no platform APIs)
data class Task(val id: Int, val title: String, val done: Boolean = false)

// The core depends on an abstraction it doesn't implement here:
expect object TaskStorage {
    fun saveAll(tasks: List<Task>)
    fun loadAll(): List<Task>
}

class TaskManager {
    private val tasks = mutableListOf<Task>()
    private var nextId = 1

    fun add(title: String): Task =
        Task(nextId++, title).also { tasks.add(it) }

    fun toggle(id: Int) {
        val i = tasks.indexOfFirst { it.id == id }
        if (i != -1) tasks[i] = tasks[i].copy(done = !tasks[i].done)
    }

    fun persist() = TaskStorage.saveAll(tasks)      // uses the platform's storage
    fun all(): List<Task> = tasks.toList()
}

// A shared inline utility, available on every platform:
inline fun <T> timed(label: String, block: () -> T): T {
    val mark = kotlin.time.TimeSource.Monotonic.markNow()
    return block().also { println("$label: ${mark.elapsedNow()}") }
}

// ---------- jvmMain ----------  (JVM-specific storage)
actual object TaskStorage {
    private val file = java.io.File("tasks.txt")
    actual fun saveAll(tasks: List<Task>) {
        file.writeText(tasks.joinToString("\n") { "${it.id}|${it.title}|${it.done}" })
    }
    actual fun loadAll(): List<Task> =
        if (!file.exists()) emptyList()
        else file.readLines().map {
            val (id, title, done) = it.split("|")
            Task(id.toInt(), title, done.toBoolean())
        }
}
```

**Commentary.**
- The **`commonMain`** `TaskManager` and `Task` are pure Kotlin — no JVM, no Android, no iOS APIs — so they compile to *every* target. This is the domain we've grown since Chapter 1, now platform-neutral.
- **`expect object TaskStorage`** declares the storage *capability* the core needs; **`jvmMain`** provides the JVM `actual` using `java.io.File`. An iOS target would supply its own `actual` (using `NSUserDefaults` or a file), and none of the shared code changes — the same dependency-inversion idea from Chapter 9, now spanning *platforms*.
- The `inline fun timed` uses the common `kotlin.time` monotonic clock, so the shown code really belongs in `commonMain`; no JVM-only `System.nanoTime()` leaks into the shared source set.
- This is the seed of the full KMP treatment in [Ch.34](#chapter-34--kotlin-multiplatform-in-depth), where we add an iOS `actual`, a Compose Multiplatform UI, and shared serialization/networking.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`inline`** | Copies a function's/lambdas' bodies into the call site (removes allocation/call). |
| **`noinline` / `crossinline`** | Opt a lambda out of inlining / forbid non-local return. |
| **Contract** | A compiler hint about a function's behaviour, improving smart-casts. |
| **Reflection** | Inspecting types at runtime (`::class` → `KClass`, member references). |
| **Kotlin Multiplatform (KMP)** | Sharing a `commonMain` core across JVM/native/JS/Wasm. |
| **`expect` / `actual`** | Common declaration / per-platform implementation. |
| **Context parameter** | A statically required capability supplied by the surrounding context. |
| **Explicit backing field** | A property's private storage with a more specific subtype than its public type. |
| **Multi-dollar interpolation** | Raw-string syntax choosing how many `$` characters trigger interpolation. |

### What's next

That completes **Part 4** — you can build, test, and ship real Kotlin, and you've seen the frontier of `inline`, contracts, reflection, and multiplatform. **Part 5 — Mastery** now takes each of these to expert depth, beginning with **[Ch.26 — Flow in Depth](#chapter-26--flow-in-depth)**: operators, hot vs cold streams, backpressure, and testing reactive pipelines.

[↑ back to top](#chapter-25--advanced-topics--next-steps)


---

## Chapter 26 — Flow in Depth

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.15 — Coroutines & Flow](#chapter-15--coroutines--flow)

**Learning objectives** — after this chapter you will be able to:

- Build flows with every builder, and transform them with the full operator set.
- Control context and buffering (`flowOn`, `buffer`, `conflate`, `collectLatest`).
- Handle errors and completion transparently (`catch`, `onCompletion`).
- Master hot flows (`StateFlow`, `SharedFlow`, `shareIn`/`stateIn`) and know when to use `Channel`.

**In this chapter**

- [26.1 Cold flows and builders](#261-cold-flows-and-builders)
- [26.2 Intermediate operators](#262-intermediate-operators)
- [26.3 Context and buffering](#263-context-and-buffering)
- [26.4 Exception transparency](#264-exception-transparency)
- [26.5 Hot flows: StateFlow and SharedFlow](#265-hot-flows-stateflow-and-sharedflow)
- [26.6 Channels](#266-channels)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-reactive-search)· Glossary · What's next

---

### 26.1 Cold flows and builders

Recall from Chapter 15: a `Flow<T>` is a **cold**, asynchronous stream — nothing runs until a terminal operator collects it, and it re-runs for *each* collector. The builders:

```kotlin
import kotlinx.coroutines.flow.*

val a = flowOf(1, 2, 3)                       // from fixed values
val b = listOf(1, 2, 3).asFlow()              // from a collection
val c = flow {                                 // the general builder — can suspend
    for (i in 1..3) { emit(i) }
}
```

The `flow { }` builder is the general one: inside it you `emit` values, and you may call suspend functions (`delay`, network calls) between emissions. "Cold" means each collector triggers a fresh run of that block.

> ⚠️ **Gotcha — emission must stay in the flow's coroutine.** You cannot `emit` from a *different* coroutine launched inside `flow { }` (it violates "flow context preservation" and throws). If you need to produce values from callbacks or multiple coroutines, use the **`channelFlow { }`** builder, which allows concurrent `send` from multiple coroutines.

### 26.2 Intermediate operators

Operators transform a flow lazily, returning a new flow; they run only when collected. Beyond `map`/`filter` (Chapter 15):

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun main() = runBlocking {
    // transform: emit any number of values per input
    flowOf(1, 2).transform { emit(it); emit(it * 100) }
        .collect { print("$it ") }             // → 1 100 2 200
    println()

    // zip: pair values position-by-position
    flowOf(1, 2, 3).zip(flowOf("a", "b", "c")) { n, s -> "$n$s" }
        .collect { print("$it ") }             // → 1a 2b 3c
    println()

    // onEach + take
    flowOf(1, 2, 3, 4, 5).onEach { }.take(3)
        .collect { print("$it ") }             // → 1 2 3
    println()
}
```

Other essentials:

- **`combine(f1, f2) { … }`** — re-emits whenever *any* source emits, using each source's latest value (great for merging independent state streams — used in this chapter's project).
- **`distinctUntilChanged()`** — drops consecutive duplicates.
- **`debounce(ms)`** — emits only after a quiet period (perfect for search-as-you-type: wait until the user stops typing).
- **`flatMapConcat` / `flatMapMerge` / `flatMapLatest`** — for each value, start a *new* flow and flatten: `Concat` runs them sequentially, `Merge` concurrently, `Latest` cancels the previous when a new value arrives (ideal for "cancel the old search when a new query comes in").

Terminal operators end the chain: `collect`, `toList`, `first`, `single`, `reduce`, `fold`, `count`.

### 26.3 Context and buffering

By default a flow runs *entirely in the collector's coroutine* — including the `flow { }` block. To run the **upstream** (the producer) on a different dispatcher, use **`flowOn`**:

```kotlin
flow {
    // heavy CPU or blocking work
    emit(expensiveComputation())
}
.flowOn(Dispatchers.Default)   // upstream runs on Default...
.collect { render(it) }         // ...collector stays where it was (e.g. Main)
```

`flowOn` affects everything *above* it, not below — so you keep collection on the UI thread while producing off it.

By default, producer and collector run in lockstep: the producer suspends at `emit` until the collector finishes the previous value (natural **backpressure**). To decouple them, add buffering:

- **`buffer(n)`** — the producer runs ahead, queueing up to `n` values while the collector works.
- **`conflate()`** — keep only the *latest* value if the collector is slow (drop intermediates).
- **`collectLatest { }`** — cancel the current collector block when a new value arrives.

> ⚙️ **Under the hood** — A `Flow` is essentially *a suspend function that emits to a collector*: `collect { }` supplies the collector, and each operator wraps the upstream flow in a new flow. `flowOn` works by inserting an internal **channel** at that point: the upstream runs on its dispatcher and *sends* values through the channel; the downstream *receives* them on the collector's dispatcher. That channel is also why `buffer` exists — it's the same handoff mechanism, exposed for you to size.

### 26.4 Exception transparency

Flows enforce **exception transparency**: a flow must not swallow exceptions from *downstream* (the collector). So you can't wrap `emit` in a `try`/`catch` to handle collector errors. Instead, handle *upstream* failures with the **`catch`** operator, which only sees exceptions from above it:

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun main() = runBlocking {
    flow {
        emit(1)
        throw RuntimeException("boom")   // upstream failure
    }
    .catch { e -> emit(-1) }              // catches ONLY upstream; can emit a fallback
    .collect { println(it) }              // → 1  then  -1
}
```

Pair it with **`onCompletion { }`**, which runs when the flow finishes — normally *or* exceptionally (its parameter is the exception or null), ideal for cleanup:

```kotlin
flowOf(1, 2)
    .onCompletion { cause -> println(if (cause == null) "done" else "failed: $cause") }
    .collect { println(it) }             // → 1, 2, done
```

> ⚠️ **Gotcha** — `catch` handles upstream only *by design*. If your collector (`collect { }`) itself throws, `catch` won't see it — wrap the collector body in its own `try`/`catch`, or move that logic into an `onEach` above the `catch`. And in coroutines, remember (Chapter 15) that `CancellationException` must propagate — don't catch it here.

### 26.5 Hot flows: StateFlow and SharedFlow

Cold flows produce per-collector. **Hot** flows exist independently of collectors and *share* emissions among all of them.

**`StateFlow`** (Chapter 15 recap): always holds exactly one current value, conflated, with `replay = 1` (new collectors immediately get the current value). It's for *state*.

**`SharedFlow`** is the general hot flow: configurable `replay` (how many past values new collectors receive) and buffering, no required initial value. It's for *events* (a stream of one-off occurrences — navigation, toasts) where "current value" doesn't make sense.

```kotlin
import kotlinx.coroutines.flow.*

class Events {
    private val _events = MutableSharedFlow<String>()      // replay = 0 by default
    val events: SharedFlow<String> = _events.asSharedFlow()

    suspend fun emit(e: String) = _events.emit(e)
}
```

You can turn a **cold flow hot** with **`shareIn`** / **`stateIn`**, sharing one upstream run among many collectors (instead of re-running per collector):

```kotlin
val livePrices: StateFlow<Price> = priceFlow()
    .stateIn(scope, SharingStarted.WhileSubscribed(5000), initialPrice)
```

**`SharingStarted.WhileSubscribed(5000)`** is the idiomatic policy: keep the upstream active while there are collectors, and stop it 5 seconds after the last one leaves (surviving brief gaps like a screen rotation) — a crucial efficiency knob on Android.

> ⚠️ **Gotcha** — `MutableSharedFlow`'s default `replay` is 0 and it *suspends* the emitter if the buffer fills and collectors are slow. For fire-and-forget events, configure `extraBufferCapacity` and an `onBufferOverflow` strategy (e.g. `DROP_OLDEST`), or you can deadlock a producer waiting on a stuck collector.

### 26.6 Channels

A **`Channel`** is a coroutine primitive: a hot, *point-to-point* pipe where senders `send` and receivers `receive`, and each value goes to *exactly one* receiver (unlike a `SharedFlow`, which broadcasts). Channels are lower-level; you rarely expose them directly, but they underpin `flowOn`, `buffer`, and `channelFlow`.

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.channels.*

fun main() = runBlocking {
    val channel = Channel<Int>()
    launch { for (x in 1..3) channel.send(x); channel.close() }
    for (y in channel) println(y)   // → 1, 2, 3
}
```

> 💡 **Idiom** — Prefer **`Flow`** for streams you expose in an API (declarative, cold or shared, rich operators). Reach for a **`Channel`** for coroutine-to-coroutine hand-off where each item has a single consumer (a work queue, the actor pattern in Chapter 27). Rule of thumb: *Flow for broadcasting values, Channel for distributing work.*

---

### Summary

- A **cold `Flow`** runs per collector; builders: `flowOf`, `asFlow`, `flow { }`, and **`channelFlow { }`** (for concurrent emission).
- Rich **operators**: `transform`, `zip`, `combine`, `debounce`, `distinctUntilChanged`, `flatMap{Concat,Merge,Latest}`, plus terminals (`collect`, `toList`, `first`, `reduce`).
- **`flowOn`** runs upstream on another dispatcher (via an internal channel); **`buffer`/`conflate`/`collectLatest`** decouple producer and collector.
- **Exception transparency**: handle upstream failures with **`catch`** (never wrap `emit`), and finalize with **`onCompletion`**.
- **Hot flows**: **`StateFlow`** for state (current value, replay 1), **`SharedFlow`** for events (configurable replay/buffer). Convert cold→hot with **`stateIn`/`shareIn`** + `SharingStarted.WhileSubscribed`.
- **`Channel`** is point-to-point (one receiver per value); use `Flow` to broadcast, `Channel` to distribute work.

### Self-check quiz

1. Why can't you `emit` from a separate coroutine inside `flow { }`, and what's the fix?
   <details><summary>Answer</summary>Flow context preservation requires emission from the flow's own coroutine; emitting elsewhere throws. Use `channelFlow { }`, which permits concurrent `send`.</details>
2. What does `flowOn(Dispatchers.Default)` affect — upstream or downstream?
   <details><summary>Answer</summary>Only the *upstream* (operators/producer above it). The collector stays on its own dispatcher. It's implemented with an internal channel handoff.</details>
3. `StateFlow` vs `SharedFlow` — when each?
   <details><summary>Answer</summary>`StateFlow` for *state* (always one current value, replay 1). `SharedFlow` for *events* (no current value; configurable replay/buffer).</details>
4. Why does the `catch` operator only see upstream exceptions?
   <details><summary>Answer</summary>Exception transparency: a flow must not swallow downstream (collector) exceptions. `catch` handles failures from operators/producer above it; collector errors are handled separately.</details>

### Exercises

**Exercise 26.1 — Combine two streams (guided).** Combine a `name` flow and an `age` flow into a greeting flow that re-emits when either changes.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun main() = runBlocking {
    val name = MutableStateFlow("Alice")
    val age = MutableStateFlow(30)

    val greeting = combine(name, age) { n, a -> "$n is $a" }

    val job = launch { greeting.collect { println(it) } }
    delay(50); age.value = 31
    delay(50); name.value = "Bob"
    delay(50); job.cancel()
}
```

Output (timing-dependent but stable with the delays):
```text
Alice is 30
Alice is 31
Bob is 31
```

**Why this works:** `combine` emits whenever *either* source changes, using both latest values. The initial emission uses the starting values; each `.value` change (spaced by `delay`) triggers a fresh combined emission.

</details>

**Exercise 26.2 — Catch upstream.** Write a flow that emits `1`, then throws, and use `catch` to emit `-1` instead of crashing.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

fun main() = runBlocking {
    flow {
        emit(1)
        error("boom")
    }
    .catch { emit(-1) }
    .collect { println(it) }   // → 1  then  -1
}
```

**Why this works:** the exception thrown after emitting `1` is an *upstream* failure, so `catch` intercepts it and emits a fallback `-1`; the collector never sees the exception.

</details>

### Chapter project: a reactive search

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–26. We build a reactive search that combines the task list, a query, and a filter into a live results flow.

**Goal.** A `combine`-based results flow that reacts to changes in the tasks, the search query, and a "done only" toggle.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.flow.*

data class Task(val id: Int, val title: String, val done: Boolean = false)

fun main() = runBlocking {
    val tasks = MutableStateFlow(
        listOf(
            Task(1, "Write Flow chapter", done = true),
            Task(2, "Review Flow chapter"),
            Task(3, "Buy coffee")
        )
    )
    val query = MutableStateFlow("")
    val doneOnly = MutableStateFlow(false)

    // Live results = latest tasks × latest query × latest filter
    val results: Flow<List<Task>> = combine(tasks, query, doneOnly) { list, q, onlyDone ->
        list.filter { it.title.contains(q, ignoreCase = true) && (!onlyDone || it.done) }
    }

    val job = launch {
        results.collect { println("Results: ${it.map { t -> t.title }}") }
    }

    delay(50); query.value = "flow"      // user types
    delay(50); doneOnly.value = true     // user flips the filter
    delay(50); job.cancel()
}
```

Output:

```text
Results: [Write Flow chapter, Review Flow chapter, Buy coffee]
Results: [Write Flow chapter, Review Flow chapter]
Results: [Write Flow chapter]
```

**Commentary.**
- `combine(tasks, query, doneOnly)` fuses three independent `StateFlow`s: whenever *any* changes, results recompute from all three latest values. The initial emission shows all tasks; typing `"flow"` narrows to the two matching titles; flipping "done only" leaves just the completed one.
- In a real UI you'd insert **`query.debounce(300)`** into the combine so results don't recompute on every keystroke — only after the user pauses. (We omit it here so the console output is deterministic; with `debounce` you'd verify it in a `runTest` with virtual time, Chapter 36.)
- For a search that fires a network call per query, you'd use **`flatMapLatest`** so a new query *cancels* the in-flight request for the old one — the canonical "cancel stale work" pattern.
- Exposed from a ViewModel (Chapter 22), `results` would be `stateIn(viewModelScope, WhileSubscribed(5000), emptyList())` so the screen collects shared, lifecycle-aware state.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Cold flow** | Runs per collector; nothing happens until collected. |
| **`channelFlow`** | Builder allowing concurrent emission from multiple coroutines. |
| **`combine` / `zip`** | Merge latest values of streams / pair them position-by-position. |
| **`debounce` / `distinctUntilChanged`** | Emit after a quiet period / drop consecutive duplicates. |
| **`flatMapLatest`** | Switch to a new inner flow per value, cancelling the previous. |
| **`flowOn`** | Run upstream on a different dispatcher. |
| **`buffer` / `conflate` / `collectLatest`** | Decouple producer/collector; keep latest; cancel-and-restart. |
| **`catch` / `onCompletion`** | Handle upstream errors / run on completion. |
| **`StateFlow` / `SharedFlow`** | Hot flow for state / for events. |
| **`stateIn` / `shareIn`** | Convert a cold flow to a shared hot flow. |
| **`Channel`** | Point-to-point hot pipe; one receiver per value. |

### What's next

You've mastered reactive streams. **[Ch.27 — Advanced Coroutines & Concurrency](#chapter-27--advanced-coroutines--concurrency)** tackles the hard part of concurrency: safely sharing mutable state with `Mutex` and actors, composing `CoroutineContext`, and using `select` and timeouts.

[↑ back to top](#chapter-26--flow-in-depth)


---

## Chapter 27 — Advanced Coroutines & Concurrency

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.15 — Coroutines](#chapter-15--coroutines--flow), [Ch.26 — Flow in Depth](#chapter-26--flow-in-depth)

**Learning objectives** — after this chapter you will be able to:

- Protect shared mutable state with `Mutex` and thread confinement.
- Compose a `CoroutineContext` and manage custom scopes.
- Use timeouts, `select`, and the actor pattern.
- Handle cancellation edge cases (cleanup, `NonCancellable`).

**In this chapter**

- [27.1 The shared-state problem](#271-the-shared-state-problem)
- [27.2 `Mutex` and thread confinement](#272-mutex-and-thread-confinement)
- [27.3 CoroutineContext and scopes](#273-coroutinecontext-and-scopes)
- [27.4 Timeouts and `select`](#274-timeouts-and-select)
- [27.5 Cancellation edge cases](#275-cancellation-edge-cases)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-thread-safe-repository)· Glossary · What's next

---

### 27.1 The shared-state problem

Structured concurrency (Chapter 15) organizes *when* coroutines run. But when multiple coroutines touch the *same mutable data*, you get a **race condition**: their read-modify-write steps interleave and updates are lost.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    var counter = 0
    coroutineScope {
        repeat(1000) {
            launch(Dispatchers.Default) {
                counter++          // NOT atomic: read, add, write — steps can interleave
            }
        }
    }
    println(counter)   // often LESS than 1000 — updates were lost to races
}
```

`counter++` looks atomic but is three operations (read, increment, write). Two coroutines can both read the same value, both increment, and both write — losing one increment. On multiple threads (`Dispatchers.Default`), this happens constantly, and the result is unpredictable.

### 27.2 `Mutex` and thread confinement

The coroutine-friendly fix is a **`Mutex`** (mutual exclusion lock): only one coroutine holds it at a time, so the protected section runs without interleaving. Use **`withLock { }`** — the suspend equivalent of a `synchronized` block, but it *suspends* rather than *blocks* while waiting:

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.sync.*

fun main() = runBlocking {
    val mutex = Mutex()
    var counter = 0
    coroutineScope {
        repeat(1000) {
            launch(Dispatchers.Default) {
                mutex.withLock { counter++ }   // only one coroutine in here at a time
            }
        }
    }
    println(counter)   // → 1000, reliably
}
```

Two other approaches:

- **Thread confinement** — run all mutations on a *single-threaded* dispatcher (`newSingleThreadContext` or `Dispatchers.Default.limitedParallelism(1)`), so there's no concurrency to race in the first place.
- **Immutability** — if the shared data never changes (Chapter 23), there's nothing to protect. Prefer this when you can; it needs no locks at all.

> 💡 **Idiom** — Ranked preference for shared state: **(1) don't share mutable state** (use immutable data / message passing); **(2) confine** mutations to one coroutine/thread; **(3) `Mutex`** for the rest. Reach for a lock last, not first — it's the most error-prone (deadlocks, contention). Note: don't use plain `synchronized`/`ReentrantLock` around suspending code — they *block* the thread, defeating coroutines; use `Mutex`.

### 27.3 CoroutineContext and scopes

A coroutine runs with a **`CoroutineContext`** — a set of elements combined with `+`: a `Job` (its lifecycle), a `CoroutineDispatcher` (its thread), a `CoroutineName` (for debugging), and optionally a `CoroutineExceptionHandler`:

```kotlin
import kotlinx.coroutines.*

val scope = CoroutineScope(
    SupervisorJob() + Dispatchers.Default + CoroutineName("worker")
)

fun main() = runBlocking {
    scope.launch(CoroutineName("child")) {
        println("Running as ${coroutineContext[CoroutineName]}")   // child overrides worker
    }.join()
}
```

Context elements are inherited by children and overridable per launch. A **`SupervisorJob`** in a scope means a child's failure doesn't cancel its siblings (the scope-level version of `supervisorScope`, Chapter 15) — useful for a long-lived scope managing independent tasks.

> ⚙️ **Under the hood** — The dispatcher decides *where a continuation resumes* (Chapter 15's state machine): when a coroutine suspends and later resumes, the dispatcher schedules that resumption onto its thread pool. Structured concurrency is enforced by the `Job` hierarchy: each coroutine's `Job` is a child of its scope's `Job`, so cancelling a parent cancels all descendants, and a scope's `Job` won't complete until its children's do. Context is just an immutable map of these elements, merged with `+`.

### 27.4 Timeouts and `select`

**`withTimeout(ms)`** cancels a block (throwing `TimeoutCancellationException`) if it runs too long; **`withTimeoutOrNull`** returns `null` instead of throwing:

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val fast = withTimeoutOrNull(1000) { delay(300); "done" }
    val slow = withTimeoutOrNull(200) { delay(500); "done" }
    println(fast)   // → done
    println(slow)   // → null   (took too long)
}
```

The **`select { }`** expression waits on *multiple* suspending sources and proceeds with whichever is ready first — e.g. "take the first of two servers to respond, or a timeout." It's the coroutine equivalent of a multiplexed wait.

### 27.5 Cancellation edge cases

Cancellation (Chapter 15) throws `CancellationException` at suspension points. Two subtleties matter for correctness:

**Cleanup must survive cancellation.** Put cleanup in `finally` — but if the cleanup itself needs to *suspend* (close a connection, flush), a cancelled coroutine can't suspend normally. Wrap suspending cleanup in **`withContext(NonCancellable)`**:

```kotlin
import kotlinx.coroutines.*

suspend fun withResource() {
    try {
        delay(1000)             // may be cancelled here
    } finally {
        withContext(NonCancellable) {
            delay(50)           // suspending cleanup that must complete even when cancelled
            println("cleaned up")
        }
    }
}
```

**CPU loops must cooperate.** A tight computational loop never hits a suspension point, so it ignores cancellation. Insert `ensureActive()` or `yield()` periodically (Chapter 15) so it can be cancelled.

> ⚠️ **Gotcha — the actor pattern for shared state.** A clean alternative to locks is the **actor**: a single coroutine owning some state, receiving mutation *messages* through a `Channel` (Chapter 26). Because only that one coroutine touches the state, there are no races — no lock needed. It trades a lock for message passing, which is often easier to reason about for complex state. (This is how many robust concurrent systems are built.)

---

### Summary

- **Races** occur when coroutines mutate shared state concurrently (`counter++` isn't atomic); results become unpredictable.
- Fix with a **`Mutex` + `withLock`** (suspending, not blocking), **thread confinement** (single-threaded dispatcher), or — best — **immutability / message passing**. Never use blocking `synchronized`/locks around suspend code.
- A **`CoroutineContext`** combines `Job` + `Dispatcher` + `CoroutineName` (+ handler) with `+`; children inherit and can override it. **`SupervisorJob`** isolates child failures.
- **`withTimeout`/`withTimeoutOrNull`** bound how long work may run; **`select`** waits on the first of several sources.
- Cancellation: run cleanup in `finally`, wrapping *suspending* cleanup in **`withContext(NonCancellable)`**; make CPU loops cooperate with `ensureActive`/`yield`.
- The **actor pattern** (one coroutine owning state, fed by a `Channel`) avoids locks entirely.

### Self-check quiz

1. Why is `counter++` unsafe across coroutines on `Dispatchers.Default`?
   <details><summary>Answer</summary>It's three operations (read, increment, write) that can interleave across threads, so two coroutines can read the same value and one increment is lost — a race condition.</details>
2. Why use `Mutex.withLock` instead of `synchronized` in coroutine code?
   <details><summary>Answer</summary>`synchronized` *blocks* the thread while waiting, wasting it and risking deadlocks with coroutines; `Mutex.withLock` *suspends*, keeping the thread free — the coroutine-native lock.</details>
3. What does `withContext(NonCancellable)` protect?
   <details><summary>Answer</summary>Suspending cleanup in a `finally` block: a cancelled coroutine can't normally suspend, so `NonCancellable` lets the cleanup's suspend calls complete.</details>
4. What is the actor pattern and why does it avoid locks?
   <details><summary>Answer</summary>A single coroutine owns the state and receives mutation messages via a `Channel`; since only that one coroutine touches the state, there's no concurrent access to race — no lock needed.</details>

### Exercises

**Exercise 27.1 — Safe counter (guided).** Increment a shared counter from 500 coroutines safely, and confirm the total is exactly 500.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.sync.*

fun main() = runBlocking {
    val mutex = Mutex()
    var count = 0
    coroutineScope {
        repeat(500) {
            launch(Dispatchers.Default) { mutex.withLock { count++ } }
        }
    }
    println(count)   // → 500
}
```

**Why this works:** `mutex.withLock { count++ }` guarantees only one coroutine executes the increment at a time, so no updates are lost. `coroutineScope` waits for all 500 before printing, yielding exactly 500.

</details>

**Exercise 27.2 — Timeout.** Run a task that takes 400ms with a 1000ms timeout, then the same with a 200ms timeout; print the two outcomes.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val ok = withTimeoutOrNull(1000) { delay(400); "completed" }
    val timedOut = withTimeoutOrNull(200) { delay(400); "completed" }
    println(ok)        // → completed
    println(timedOut)  // → null
}
```

**Why this works:** the first block finishes (400ms) within its 1000ms budget, so it returns `"completed"`. The second exceeds its 200ms budget, so `withTimeoutOrNull` cancels it and returns `null`.

</details>

### Chapter project: a thread-safe repository

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–27. We make the repository safe under concurrent access with a `Mutex`, and add a cancellable, time-bounded sync.

**Goal.** A `SafeTaskRepository` whose mutations are race-free, plus a `sync` that gives up after a timeout.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlinx.coroutines.*
import kotlinx.coroutines.sync.*

data class Task(val id: Int, val title: String, val done: Boolean = false)

class SafeTaskRepository {
    private val mutex = Mutex()
    private val tasks = mutableListOf<Task>()
    private var nextId = 1

    suspend fun add(title: String): Task = mutex.withLock {
        Task(nextId++, title).also { tasks.add(it) }
    }

    suspend fun all(): List<Task> = mutex.withLock { tasks.toList() }
}

suspend fun sync(repo: SafeTaskRepository): String =
    withTimeoutOrNull(1000) {
        delay(300)                       // simulate a remote round-trip
        "synced ${repo.all().size} tasks"
    } ?: "sync timed out"

fun main() = runBlocking {
    val repo = SafeTaskRepository()

    // 100 concurrent adds on a multi-threaded dispatcher — safe thanks to the Mutex
    coroutineScope {
        repeat(100) { i ->
            launch(Dispatchers.Default) { repo.add("Task $i") }
        }
    }

    println("Total: ${repo.all().size}")   // → 100  (no lost updates)
    println(sync(repo))                      // → synced 100 tasks
}
```

Output:

```text
Total: 100
synced 100 tasks
```

**Commentary.**
- Every mutation and read goes through `mutex.withLock`, so the 100 concurrent `add`s on `Dispatchers.Default` never race — the count is **exactly 100**. Without the `Mutex`, `nextId++` and `tasks.add` would interleave and you'd lose tasks (and possibly corrupt the list).
- `add` returns inside the lock via `Task(...).also { tasks.add(it) }` — the whole read-modify-write is atomic with respect to other coroutines.
- `sync` is bounded by `withTimeoutOrNull(1000)`: the 300ms simulated round-trip completes comfortably, returning the count; a slow network would trip the timeout and yield `"sync timed out"` instead of hanging forever.
- In [Ch.33](#chapter-33--architecture--dependency-injection) this repository is injected via DI, and in [Ch.36](#chapter-36--advanced-testing) we test its concurrency guarantees. For *very* high contention you'd switch to the actor pattern (§27.5) — one coroutine owning the list — but a `Mutex` is the right, simple choice here.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Race condition** | Interleaved concurrent access corrupting shared state. |
| **`Mutex` / `withLock`** | A suspending mutual-exclusion lock / its scoped use. |
| **Thread confinement** | Restricting mutations to a single thread/coroutine. |
| **`CoroutineContext`** | The set of elements (Job/Dispatcher/Name/…) a coroutine runs with. |
| **`SupervisorJob`** | A Job where a child's failure doesn't cancel siblings. |
| **`withTimeout(OrNull)`** | Bound a block's running time (throw / return null). |
| **`select`** | Await the first ready of several suspending sources. |
| **`NonCancellable`** | A context letting suspending cleanup run during cancellation. |
| **Actor** | A coroutine owning state, mutated only via channel messages. |

### What's next

You can run concurrent code safely. **[Ch.28 — Operator Overloading & Conventions](#chapter-28--operator-overloading--conventions)** shifts to expressiveness: defining `+`, `[]`, `in`, `()`, comparison, and destructuring for your own types, so they read as naturally as built-ins.

[↑ back to top](#chapter-27--advanced-coroutines--concurrency)


---

## Chapter 28 — Operator Overloading & Conventions

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Operators](#chapter-3--operators--expressions), [Ch.11 — Extensions](#chapter-11--extension-functions--properties)

**Learning objectives** — after this chapter you will be able to:

- Define arithmetic, comparison, and equality operators for your own types.
- Implement indexing (`[]`), `invoke` (`()`), `in` (`contains`), and iteration.
- Enable destructuring with `componentN`.
- Know when operator overloading helps — and when it hurts.

**In this chapter**

- [28.1 Operators are conventions](#281-operators-are-conventions)
- [28.2 Arithmetic and comparison](#282-arithmetic-and-comparison)
- [28.3 Indexing, invoke, and `in`](#283-indexing-invoke-and-in)
- [28.4 Iteration and destructuring](#284-iteration-and-destructuring)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-money-type)· Glossary · What's next

---

### 28.1 Operators are conventions

Chapter 3 revealed that `a + b` compiles to `a.plus(b)` — operators are just calls to specially-named functions. Kotlin extends this to *your* types: define a function with the **`operator`** keyword and the conventional name, and the corresponding symbol works on your type. This is **operator overloading**, and it's governed by a fixed set of name conventions.

```kotlin
data class Vec(val x: Int, val y: Int) {
    operator fun plus(other: Vec) = Vec(x + other.x, y + other.y)
}

fun main() {
    println(Vec(1, 2) + Vec(3, 4))   // → Vec(x=4, y=6)   (calls plus)
}
```

The `operator` keyword is required — it signals "this function backs an operator" and lets the compiler map `+` to it.

### 28.2 Arithmetic and comparison

The arithmetic conventions map symbols to function names:

| Symbol | Function | | Symbol | Function |
|--------|----------|-|--------|----------|
| `a + b` | `plus` | | `a % b` | `rem` |
| `a - b` | `minus` | | `-a` | `unaryMinus` |
| `a * b` | `times` | | `+a` | `unaryPlus` |
| `a / b` | `div` | | `a++` | `inc` |

```kotlin
data class Vec(val x: Int, val y: Int) {
    operator fun plus(o: Vec) = Vec(x + o.x, y + o.y)
    operator fun times(scalar: Int) = Vec(x * scalar, y * scalar)
    operator fun unaryMinus() = Vec(-x, -y)
}

fun main() {
    val v = Vec(2, 3)
    println(v * 2)    // → Vec(x=4, y=6)
    println(-v)       // → Vec(x=-2, y=-3)
}
```

**Comparison** flows from one function. Implement **`Comparable`** with `compareTo`, and Kotlin derives `<`, `>`, `<=`, `>=` for free:

```kotlin
data class Version(val major: Int, val minor: Int) : Comparable<Version> {
    override fun compareTo(other: Version): Int =
        compareValuesBy(this, other, { it.major }, { it.minor })
}

fun main() {
    println(Version(1, 2) < Version(1, 5))   // → true
    println(Version(2, 0) > Version(1, 9))   // → true
}
```

`compareValuesBy` compares by each selector in turn — a clean way to implement multi-field ordering. **Equality** (`==`) comes from `equals` (auto-generated for `data class`es, Chapter 8).

**Augmented assignment** (`+=`, `-=`) uses `plusAssign`/`minusAssign` for in-place mutation, or falls back to `plus` + reassignment for immutable types:

```kotlin
val list = mutableListOf(1, 2)
list += 3            // MutableList defines plusAssign → mutates in place → [1, 2, 3]

var v = Vec(1, 1)
v += Vec(1, 1)       // no plusAssign → uses plus, then reassigns v → Vec(2, 2)
```

### 28.3 Indexing, invoke, and `in`

**Indexing** — `a[i]` maps to `get`, and `a[i] = v` to `set`:

```kotlin
class Grid(val width: Int) {
    private val cells = IntArray(width * width)
    operator fun get(x: Int, y: Int): Int = cells[y * width + x]
    operator fun set(x: Int, y: Int, value: Int) { cells[y * width + x] = value }
}

fun main() {
    val grid = Grid(3)
    grid[1, 2] = 7            // calls set(1, 2, 7)
    println(grid[1, 2])       // calls get(1, 2) → 7
}
```

**`invoke`** — makes an *instance* callable like a function, `obj()`:

```kotlin
class Multiplier(val factor: Int) {
    operator fun invoke(x: Int) = x * factor
}

fun main() {
    val triple = Multiplier(3)
    println(triple(5))        // calls invoke(5) → 15
}
```

**`in`** — `x in c` maps to `c.contains(x)`:

```kotlin
class DayRange(val start: Int, val end: Int) {
    operator fun contains(day: Int) = day in start..end
}

fun main() {
    println(5 in DayRange(1, 10))    // → true
    println(15 in DayRange(1, 10))   // → false
}
```

### 28.4 Iteration and destructuring

Give a type an **`iterator`** operator and it works in a `for` loop:

```kotlin
class Countdown(val from: Int) {
    operator fun iterator() = (from downTo 1).iterator()
}

fun main() {
    for (n in Countdown(3)) print("$n ")   // → 3 2 1
}
```

**Destructuring** (Chapter 8) works for any type providing `component1`, `component2`, … operators. `data class`es generate them; you can add them manually:

```kotlin
class Pair2(val first: String, val second: Int) {
    operator fun component1() = first
    operator fun component2() = second
}

fun main() {
    val (name, age) = Pair2("Alice", 30)     // uses component1/component2
    println("$name is $age")                  // → Alice is 30
}
```

> ⚙️ **Under the hood** — All of these are resolved *by convention name and signature at compile time* (like extensions, Chapter 11) — `a[i]` looks for an `operator fun get`, `for (x in c)` looks for `operator fun iterator`, `val (a, b) = p` looks for `component1`/`component2`. There's no runtime "operator dispatch"; the compiler rewrites the symbol into the named call. Missing or wrong-signature functions are a compile error, not a runtime surprise.

> ⚠️ **Gotcha — overload only when it reads naturally.** `+` on vectors, money, or matrices is intuitive. `+` that means "register a listener" or `*` that means "repeat" is a puzzle for readers. The test: would someone unfamiliar with your code *guess correctly* what the operator does? If not, use a named method. Cleverness that obscures intent is a net loss.

---

### Summary

- **Operator overloading**: define an `operator fun` with the conventional name and the symbol works on your type (`plus`→`+`, `times`→`*`, `unaryMinus`→`-a`, …).
- **Comparison** comes from implementing **`Comparable.compareTo`** (use `compareValuesBy` for multi-field); **equality** from `equals` (generated by `data class`).
- **`+=`** uses `plusAssign` (in-place) or falls back to `plus` + reassignment.
- **`get`/`set`** back indexing `a[i]`; **`invoke`** makes instances callable `obj()`; **`contains`** backs `in`; **`iterator`** enables `for`; **`componentN`** enables destructuring.
- All resolve by name/signature at compile time. **Overload only when the operator reads naturally** — otherwise prefer a named method.

### Self-check quiz

1. What function backs `a * b`, and what keyword must it have?
   <details><summary>Answer</summary>`times`, marked with the `operator` keyword: `operator fun times(...)`.</details>
2. How do you get all four comparison operators (`< > <= >=`) for a type?
   <details><summary>Answer</summary>Implement `Comparable<T>` with a single `compareTo` returning negative/zero/positive; Kotlin derives all four from it.</details>
3. What does `operator fun invoke` enable?
   <details><summary>Answer</summary>Calling an instance like a function: `obj(args)` maps to `obj.invoke(args)`.</details>
4. When should you *not* overload an operator?
   <details><summary>Answer</summary>When its meaning isn't obvious for your type — if a reader can't guess what `+`/`*` does, use a named method instead.</details>

### Exercises

**Exercise 28.1 — Comparable temperature (guided).** Make a `Temperature(celsius)` type comparable, so you can sort and compare readings.

<details><summary>Show solution</summary>

```kotlin
data class Temperature(val celsius: Double) : Comparable<Temperature> {
    override fun compareTo(other: Temperature) = celsius.compareTo(other.celsius)
}

fun main() {
    val readings = listOf(Temperature(20.0), Temperature(-5.0), Temperature(37.0))
    println(readings.sorted())        // → [Temperature(-5.0), Temperature(20.0), Temperature(37.0)]
    println(Temperature(20.0) < Temperature(37.0))   // → true
}
```

**Why this works:** `compareTo` delegates to `Double.compareTo`, giving a total order; `Comparable` then powers `sorted()`, `<`, `min`/`max`, etc. — all from one function.

</details>

**Exercise 28.2 — Indexed matrix.** Give a `Matrix(rows, cols)` `get`/`set` operators so `m[r, c]` works.

<details><summary>Show solution</summary>

```kotlin
class Matrix(val rows: Int, val cols: Int) {
    private val data = DoubleArray(rows * cols)
    operator fun get(r: Int, c: Int): Double = data[r * cols + c]
    operator fun set(r: Int, c: Int, value: Double) { data[r * cols + c] = value }
}

fun main() {
    val m = Matrix(2, 2)
    m[0, 1] = 3.5
    println(m[0, 1])   // → 3.5
}
```

**Why this works:** `operator fun get`/`set` translate `m[0, 1]` and `m[0, 1] = 3.5` into `get(0, 1)` / `set(0, 1, 3.5)`, indexing into the flat backing array by `r * cols + c`.

</details>

### Chapter project: a Money type

> 🛠️ **Chapter Project** — **Standalone mini-project** (operator conventions don't fit the Task Manager domain). **Builds on:** Ch.1–28 (especially Ch.10 value classes). We build a robust `Money` type with full, well-behaved operators.

**Goal.** A `Money` value type supporting `+`, `-`, `*`, comparison, and clean formatting — the kind of type that prevents money bugs.

<details><summary>Show reference solution + commentary</summary>

```kotlin
@JvmInline
value class Money(val cents: Long) : Comparable<Money> {
    operator fun plus(other: Money) = Money(cents + other.cents)
    operator fun minus(other: Money) = Money(cents - other.cents)
    operator fun times(quantity: Int) = Money(cents * quantity)
    override fun compareTo(other: Money) = cents.compareTo(other.cents)
    override fun toString() = "$" + "%.2f".format(cents / 100.0)

    companion object {
        // Round, don't truncate: 19.99 * 100 is 1998.999… in Double, so toLong() would give 1998.
        fun dollars(amount: Double) = Money(Math.round(amount * 100))
    }
}

fun main() {
    val price = Money.dollars(19.99)
    val tax = Money.dollars(1.60)

    val total = price + tax                 // plus
    val threeItems = price * 3              // times
    val change = Money.dollars(100.0) - total   // minus

    println("Total: $total")                // → Total: $21.59
    println("Three items: $threeItems")     // → Three items: $59.97
    println("Change from \$100: $change")   // → Change from $100: $78.41
    println("Expensive? ${price > Money.dollars(10.0)}")   // → Expensive? true
}
```

Output:

```text
Total: $21.59
Three items: $59.97
Change from $100: $78.41
Expensive? true
```

**Commentary.**
- Money is stored as an integer number of **cents** (a `Long`), never a `Double` — avoiding the floating-point rounding that plagues naive money code (Chapter 3's `0.1 + 0.2` gotcha). All arithmetic stays in exact integer cents.
- It's a **`value class`** (Chapter 10), so at runtime it's just a `Long` — full type safety (you can't accidentally add a `Money` to a raw number) at **zero allocation cost**.
- `plus`/`minus`/`times` are natural, unambiguous operators — adding money and multiplying by a quantity is exactly what a reader expects, so overloading *helps* here (unlike the gotcha's warning about surprising operators).
- `Comparable` gives `<`/`>`/sorting for free; `toString` formats as currency. `Money.dollars(...)` is a `companion` factory (Chapter 10) for readable construction. This is a small, production-quality value type — the kind of expressive, safe abstraction operator conventions are *for*.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Operator overloading** | Defining an operator for a type via a conventionally-named `operator fun`. |
| **`operator` keyword** | Marks a function as backing an operator/convention. |
| **`plus`/`times`/`unaryMinus`/…** | Arithmetic operator functions. |
| **`Comparable`/`compareTo`** | Provides `<`/`>`/`<=`/`>=` and sorting. |
| **`get`/`set`** | Back indexing `a[i]` / `a[i] = v`. |
| **`invoke`** | Makes an instance callable: `obj()`. |
| **`contains`** | Backs the `in` operator. |
| **`iterator`** | Enables `for (x in obj)`. |
| **`componentN`** | Enables destructuring `val (a, b) = obj`. |

### What's next

Your types can read like built-ins. **[Ch.29 — Reflection & Annotations](#chapter-29--reflection--annotations)** goes the other way — inspecting types *at runtime* — to build annotation-driven tools like mappers and validators.

[↑ back to top](#chapter-28--operator-overloading--conventions)


---

## Chapter 29 — Reflection & Annotations

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.10 — Advanced OOP](#chapter-10--advanced-object-oriented-features), [Ch.12 — Generics](#chapter-12--generics), [Ch.25 — Reflection basics](#chapter-25--advanced-topics--next-steps)

**Learning objectives** — after this chapter you will be able to:

- Inspect classes, properties, and functions at runtime with `KClass` and references.
- Declare annotations with targets, retention, and parameters.
- Read annotations reflectively to drive behaviour.
- Understand reflection's costs and use-site targets.

**In this chapter**

- [29.1 KClass and member references](#291-kclass-and-member-references)
- [29.2 Declaring annotations](#292-declaring-annotations)
- [29.3 Reading annotations at runtime](#293-reading-annotations-at-runtime)
- [29.4 Use-site targets and costs](#294-use-site-targets-and-costs)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-an-annotation-driven-mapper)· Glossary · What's next

---

### 29.1 KClass and member references

**Reflection** is a program inspecting and manipulating its own structure at runtime. The entry point is the **`::class`** literal, yielding a **`KClass`**:

```kotlin
data class Task(val id: Int, val title: String, val done: Boolean = false)

fun main() {
    val kClass = Task::class
    println(kClass.simpleName)                          // → Task
    println(kClass.qualifiedName)                       // → (package).Task
    println(kClass.isData)                              // → true
    println(Task(1, "x")::class.simpleName)             // → Task  (from an instance)
}
```

Full reflection (accessing members, calling constructors) needs the **`kotlin-reflect`** library:

```kotlin
dependencies { implementation(kotlin("reflect")) }
```

**References** (Chapter 5's `::`) turn declarations into callable objects:

```kotlin
val lengthOf: (String) -> Int = String::length     // function/property reference
println(lengthOf("hello"))                          // → 5

val bound = "hello"::length                          // bound reference (to a specific value)
println(bound())                                     // → 5

val ctor = ::Task                                    // constructor reference
println(ctor(1, "made via reference", false))        // → Task(id=1, title=made via reference, done=false)
```

### 29.2 Declaring annotations

An **annotation** is metadata you attach to code, later read by tools, frameworks, or reflection. You've used many (`@Serializable`, `@Test`, `@JvmStatic`); now you'll define them. An annotation is a class declared with the `annotation` keyword, configured with meta-annotations:

```kotlin
@Target(AnnotationTarget.PROPERTY, AnnotationTarget.VALUE_PARAMETER)   // where it can go
@Retention(AnnotationRetention.RUNTIME)                                 // keep it at runtime
annotation class Column(val name: String)                              // a parameter
```

- **`@Target`** restricts where the annotation may appear (class, function, property, parameter, …).
- **`@Retention`** controls how long it survives: `SOURCE` (compiler only), `BINARY` (in the class file, the **default**), or `RUNTIME` (readable by reflection).
- Parameters (like `val name: String`) must be compile-time constants, and are supplied at the use site: `@Column("full_name")`.

> ⚠️ **Gotcha** — To read an annotation via reflection, it **must** have `@Retention(AnnotationRetention.RUNTIME)`. The default is `BINARY`, which is present in the class file but *not* exposed to reflection — so a RUNTIME-less annotation will silently be invisible to your `kClass.annotations` lookup. This trips up nearly everyone the first time.

### 29.3 Reading annotations at runtime

With `RUNTIME` retention, reflection can read your annotations and act on them:

```kotlin
import kotlin.reflect.full.findAnnotation

@Retention(AnnotationRetention.RUNTIME)
annotation class Label(val text: String)

@Label("An important task")
class ImportantTask

fun main() {
    val label = ImportantTask::class.findAnnotation<Label>()
    println(label?.text)   // → An important task
}
```

This is how frameworks work: JUnit finds `@Test` methods, a DI container finds `@Inject` constructors, a serializer finds `@SerialName`. Your code declares intent with annotations; a tool reads them and does the work.

### 29.4 Use-site targets and costs

A Kotlin property compiles to several JVM elements — a field, a getter, maybe a constructor parameter. When you annotate a property, **use-site targets** say *which* element gets the annotation:

```kotlin
class User(
    @get:JvmName("fetchName") val name: String,   // annotate the GETTER
    @field:Volatile var counter: Int              // annotate the FIELD
)
```

Targets include `@get:`, `@set:`, `@field:`, `@param:`, `@property:`. Without one, Kotlin applies a default (usually the property/field), which is sometimes not what a Java framework expects — so many interop annotations need an explicit target.

> ⚙️ **Under the hood** — Reflection reads Kotlin-specific structure from the **`@Metadata`** annotation the compiler attaches to every class (that's how `kotlin-reflect` knows about properties, nullability, and default values that plain Java reflection can't see). It's powerful but **not free**: reflective lookups are far slower than direct calls, and they defeat some compiler optimizations. Cache reflective results (resolve a `KClass`'s members once, reuse them), and prefer **compile-time** codegen (KSP, Chapter 30) when you can — it has the same expressiveness with none of the runtime cost.

> ⚠️ **Gotcha** — Reflection also bypasses erasure's *guarantees* but not its *limits*: `kClass.typeParameters` exist, but a specific `List<String>`'s element type is still erased at runtime. And reflection can break encapsulation (accessing `private` members), which is powerful but should be used sparingly and deliberately.

---

### Summary

- **Reflection** inspects code at runtime: **`::class`** → **`KClass`** (needs **`kotlin-reflect`** for members/constructors); **references** (`String::length`, `::Task`, bound `x::length`) make declarations callable.
- **Annotations** are metadata classes (`annotation class`) configured with **`@Target`** (where) and **`@Retention`** (how long) and typed parameters.
- To read an annotation reflectively it **must** be **`@Retention(RUNTIME)`** (default is `BINARY`, invisible to reflection).
- **Use-site targets** (`@get:`, `@field:`, `@param:`, …) choose which JVM element an annotation lands on — often needed for Java-framework interop.
- Reflection reads Kotlin structure from **`@Metadata`**; it's powerful but **slow** — cache results, and prefer compile-time codegen (KSP) where possible.

### Self-check quiz

1. What retention must an annotation have to be read by reflection, and what's the default?
   <details><summary>Answer</summary>`AnnotationRetention.RUNTIME`. The default is `BINARY`, which is in the class file but not exposed to reflection.</details>
2. What does `kotlin-reflect` add over `::class` alone?
   <details><summary>Answer</summary>Access to members, constructors, parameters, and Kotlin-specific metadata (nullability, defaults). Bare `::class` gives a limited `KClass` without full reflection.</details>
3. Why do interop annotations often need a use-site target like `@get:`?
   <details><summary>Answer</summary>A property compiles to multiple JVM elements (field, getter, param); the target specifies which one gets the annotation, since a Java framework may expect it on, say, the getter.</details>
4. Why prefer KSP codegen over reflection when possible?
   <details><summary>Answer</summary>Reflection is comparatively slow and runs at runtime; KSP generates code at compile time, giving the same power with no runtime cost and earlier error detection.</details>

### Exercises

**Exercise 29.1 — Inspect a class (guided).** Print a data class's name, whether it's a data class, and its property names.

<details><summary>Show solution</summary>

```kotlin
import kotlin.reflect.full.memberProperties

data class Product(val id: Int, val name: String, val price: Double)

fun main() {
    val k = Product::class
    println(k.simpleName)                              // → Product
    println(k.isData)                                  // → true
    println(k.memberProperties.map { it.name })        // → [id, name, price]
}
```

**Why this works:** `Product::class` gives a `KClass`; `simpleName`/`isData` are basic metadata, and `memberProperties` (from `kotlin-reflect`) lists the properties, whose `.name` we map. The order matches declaration order.

</details>

**Exercise 29.2 — A runtime-readable annotation.** Declare a `@Doc(text)` annotation readable at runtime, apply it to a class, and print its text.

<details><summary>Show solution</summary>

```kotlin
import kotlin.reflect.full.findAnnotation

@Retention(AnnotationRetention.RUNTIME)
annotation class Doc(val text: String)

@Doc("A sample service")
class Service

fun main() {
    println(Service::class.findAnnotation<Doc>()?.text)   // → A sample service
}
```

**Why this works:** `@Retention(RUNTIME)` makes the annotation visible to reflection; `findAnnotation<Doc>()` retrieves it (or null), and `?.text` reads its parameter. Drop the `@Retention` and it would print `null`.

</details>

### Chapter project: an annotation-driven mapper

> 🛠️ **Chapter Project** — **Standalone mini-project** (reflection tooling, not the Task Manager domain). **Builds on:** Ch.1–29. We build a tiny mapper that constructs a data class from a `Map` using `@Column` annotations — a miniature of how ORMs and CSV libraries work.

**Goal.** Map a `Map<String, String>` (a "row") onto any data class, honouring `@Column` name overrides, via reflection.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlin.reflect.full.findAnnotation
import kotlin.reflect.full.primaryConstructor

@Target(AnnotationTarget.VALUE_PARAMETER)
@Retention(AnnotationRetention.RUNTIME)
annotation class Column(val name: String)

data class Person(
    @Column("full_name") val name: String,
    @Column("years") val age: Int
)

inline fun <reified T : Any> fromRow(row: Map<String, String>): T {
    val ctor = T::class.primaryConstructor
        ?: error("${T::class.simpleName} has no primary constructor")

    val args = ctor.parameters.associateWith { param ->
        val columnName = param.findAnnotation<Column>()?.name ?: param.name!!
        val raw = row[columnName] ?: error("Missing column: $columnName")
        when (param.type.classifier) {          // convert by the parameter's type
            Int::class -> raw.toInt()
            Boolean::class -> raw.toBoolean()
            else -> raw
        }
    }
    return ctor.callBy(args)
}

fun main() {
    val row = mapOf("full_name" to "Alice", "years" to "30")
    val person = fromRow<Person>(row)
    println(person)   // → Person(name=Alice, age=30)
}
```

Output:

```text
Person(name=Alice, age=30)
```

**Commentary.**
- `fromRow` is `reified` (Chapter 12) so `T::class` works. `primaryConstructor` (from `kotlin-reflect`) gives the constructor; `parameters` lists its params.
- For each parameter, `findAnnotation<Column>()?.name ?: param.name!!` picks the **column name** — the `@Column` override if present, else the parameter's own name. Because `@Column` has `RUNTIME` retention (§29.2's gotcha), reflection can read it.
- `param.type.classifier` drives a tiny type conversion (`"30"` → `30`), and `ctor.callBy(args)` constructs the instance from a map of parameter → value (which also respects default arguments).
- This is exactly how real mapping libraries operate — but note the cost: reflection here runs per call. A production library would either **cache** the resolved constructor/annotations per class, or generate the mapper at compile time with **KSP** — which is precisely [Ch.30](#chapter-30--metaprogramming-ksp--compiler-plugins).

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Reflection** | Inspecting/manipulating code structure at runtime. |
| **`KClass`** | The reflective handle for a class (`::class`). |
| **`kotlin-reflect`** | The library enabling full member/constructor reflection. |
| **Reference (`::`)** | A callable object for a function/property/constructor. |
| **Annotation** | Metadata attached to code (`annotation class`). |
| **`@Target` / `@Retention`** | Where an annotation may go / how long it survives. |
| **Use-site target** | `@get:`/`@field:`/… choosing which JVM element is annotated. |
| **`@Metadata`** | Compiler-attached data that `kotlin-reflect` reads. |

### What's next

Reflection reads types at runtime — powerful but costly. **[Ch.30 — Metaprogramming: KSP & Compiler Plugins](#chapter-30--metaprogramming-ksp--compiler-plugins)** does similar work at *compile time*, generating code (no runtime cost) — the modern replacement for reflection-heavy and annotation-processing tools.

[↑ back to top](#chapter-29--reflection--annotations)


---

## Chapter 30 — Metaprogramming: KSP & Compiler Plugins

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.17 — DSLs](#chapter-17--type-safe-builders--dsls), [Ch.29 — Reflection & Annotations](#chapter-29--reflection--annotations)

**Learning objectives** — after this chapter you will be able to:

- Explain KSP and how it differs from kapt.
- Understand the shape of a symbol processor that generates code.
- Recognise what the major compiler plugins do.
- Choose between codegen and reflection.
- Build, validate, test, and incrementally generate source with a real KSP2 processor module.

> KSP processors run inside the build, not in a `main`. Sections 30.1–30.4 build the mental model; §30.5 supplies the module setup, validation, incremental metadata, and testing requirements needed to turn the example into a real processor.

**In this chapter**

- [30.1 Why generate code?](#301-why-generate-code)
- [30.2 KSP vs kapt](#302-ksp-vs-kapt)
- [30.3 A minimal symbol processor](#303-a-minimal-symbol-processor)
- [30.4 Compiler plugins](#304-compiler-plugins)
- [30.5 Production KSP: correctness, incrementality, and tests](#305-production-ksp-correctness-incrementality-and-tests)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-an-automap-processor)· Glossary · What's next

---

### 30.1 Why generate code?

Chapter 29 built a reflection-based mapper — flexible, but it pays a runtime cost on every call. **Metaprogramming** offers the alternative: generate the boilerplate *at compile time*, so the running program executes plain, fast, hand-written-looking code with no reflection at all.

This is how much of the Kotlin ecosystem works under the hood: Room generates DAO implementations, Dagger/Hilt generate dependency wiring, Moshi/kotlinx.serialization generate serializers, Compose transforms your `@Composable`s. You annotate; a compile-time tool reads the annotations and *writes code* into your build.

### 30.2 KSP vs kapt

There are two annotation-processing routes on Kotlin:

- **kapt** (Kotlin Annotation Processing Tool) runs *Java* annotation processors by generating Java stubs of your Kotlin code first. It works, but it's slow (the stub-generation step) and sees your code through a Java-shaped lens.
- **KSP** (Kotlin Symbol Processing) is the modern, Kotlin-native replacement. It gives processors a **resolved, Kotlin-aware model** of your code (classes, functions, properties, nullability, generics) without generating Java stubs — so it's much faster and understands Kotlin properly.

The rule today: **prefer KSP.** New libraries target it, and existing ones (Room, Moshi) have migrated.

> ⚙️ **Under the hood** — KSP runs as a compiler plugin during compilation. It's given a `Resolver` — a queryable model of all the symbols in the current compilation — and a `CodeGenerator` to emit new `.kt` files, which are then compiled *in the same build*. Crucially, KSP can **generate** new code but cannot **modify** existing code (that's the domain of full compiler plugins, §30.4). Processing can run in multiple **rounds** (generated code can itself be annotated and processed) and supports incremental builds.

### 30.3 A minimal symbol processor

A KSP processor implements `SymbolProcessor`; a `SymbolProcessorProvider` wires it in. Here's the shape of one that finds classes annotated `@AutoMap` and generates a `toMap()` extension for each:

```kotlin
// The annotation (in your main module):
annotation class AutoMap

// The processor (in a separate KSP-processor module):
class AutoMapProcessor(
    private val codeGenerator: CodeGenerator,
    private val logger: KSPLogger
) : SymbolProcessor {

    override fun process(resolver: Resolver): List<KSAnnotated> {
        // 1. Find every class annotated @AutoMap
        val symbols = resolver.getSymbolsWithAnnotation("com.example.AutoMap")
            .filterIsInstance<KSClassDeclaration>()

        // 2. Generate a toMap() extension for each
        symbols.forEach { cls ->
            val packageName = cls.packageName.asString()
            val className = cls.simpleName.asString()
            val props = cls.getAllProperties().map { it.simpleName.asString() }

            val code = buildString {
                appendLine("package $packageName")
                appendLine()
                appendLine("fun $className.toMap(): Map<String, Any?> = mapOf(")
                props.forEach { appendLine("    \"$it\" to $it,") }
                appendLine(")")
            }

            // 3. Write it into the build
            val source = requireNotNull(cls.containingFile)
            codeGenerator.createNewFile(Dependencies(false, source), packageName, "${className}Map")
                .bufferedWriter()
                .use { writer -> writer.write(code) }
        }
        return emptyList()   // no symbols deferred to a later round
    }
}

class AutoMapProcessorProvider : SymbolProcessorProvider {
    override fun create(env: SymbolProcessorEnvironment): SymbolProcessor =
        AutoMapProcessor(env.codeGenerator, env.logger)
}
```

Given this input in your app:

```kotlin
@AutoMap
data class Person(val name: String, val age: Int)
```

KSP generates (into your build output) `PersonMap.kt`:

```kotlin
package com.example

fun Person.toMap(): Map<String, Any?> = mapOf(
    "name" to name,
    "age" to age,
)
```

…which you can then call as `person.toMap()` — a normal, fast function, no reflection. The provider is registered via a resource file (`META-INF/services/...SymbolProcessorProvider`), and you enable KSP in Gradle with `ksp(project(":processor"))`.

> ☕ **Coming from Java** — This replaces Java's `javax.annotation.processing` API (which kapt bridges to). KSP's model is Kotlin-shaped — it understands `data class`, nullability, and default arguments directly, whereas Java processors see a lossy Java projection of your Kotlin.

### 30.4 Compiler plugins

KSP only *generates* code. A full **compiler plugin** can *transform* existing code during compilation — a deeper, more powerful (and more complex) hook. You already depend on several without knowing:

- **`kotlin("plugin.serialization")`** generates a `KSerializer` for each `@Serializable` class (Chapter 31).
- **Compose** (`kotlin("plugin.compose")`) rewrites `@Composable` functions to add the recomposition machinery (Chapter 22).
- **all-open / no-arg** make classes `open` / add no-arg constructors for frameworks like Spring/JPA that require them.
- **Parcelize** (Android) generates `Parcelable` implementations from `@Parcelize`.

You'll rarely *write* a compiler plugin (the API is low-level and less stable), but knowing that these features are *plugins rewriting your code* demystifies a lot of "how does that annotation do so much?" magic.

> 💡 **Idiom** — Decision order for adding cross-cutting behaviour: **(1)** plain functions/extensions if it's simple; **(2)** a **KSP** processor if you need to generate boilerplate from annotations (fast, safe, Kotlin-aware); **(3)** **reflection** (Chapter 29) if the shape isn't known until runtime; **(4)** a compiler plugin only for deep transformations no other tool can do. Most needs stop at (1) or (2).

### 30.5 Production KSP: correctness, incrementality, and tests

Use KSP2 (the default in current KSP) and keep three concerns separate:

```text
:annotations   tiny runtime/API module containing @AutoMap
:processor     depends on symbol-processing-api; generates source
:app           depends on :annotations; applies KSP and ksp(project(":processor"))
```

```kotlin
// root build.gradle.kts
plugins {
    kotlin("jvm") version "2.4.0" apply false
    id("com.google.devtools.ksp") version "2.3.9" apply false
}

// processor/build.gradle.kts
plugins { kotlin("jvm") }
dependencies {
    implementation(project(":annotations"))
    implementation("com.google.devtools.ksp:symbol-processing-api:2.3.9")
    testImplementation(kotlin("test"))
}

// app/build.gradle.kts
plugins {
    kotlin("jvm")
    id("com.google.devtools.ksp")
}
dependencies {
    implementation(project(":annotations"))
    ksp(project(":processor"))
}
```

A real processor validates symbols and defers unresolved ones to a later round:

```kotlin
override fun process(resolver: Resolver): List<KSAnnotated> {
    val (valid, deferred) = resolver
        .getSymbolsWithAnnotation(AUTO_MAP_FQ_NAME)
        .partition { it.validate() }

    valid.filterIsInstance<KSClassDeclaration>().forEach(::generateMapper)
    return deferred
}

private fun generateMapper(type: KSClassDeclaration) {
    val source = requireNotNull(type.containingFile)
    val packageName = type.packageName.asString()
    val className = type.simpleName.asString()

    codeGenerator.createNewFile(
        dependencies = Dependencies(false, source),
        packageName = packageName,
        fileName = "${className}AutoMap",
    ).bufferedWriter().use { writer ->
        writer.appendLine("package $packageName")
        writer.appendLine("fun $className.toMap(): Map<String, Any?> = mapOf(")
        type.getAllProperties().forEach { property ->
            val name = property.simpleName.asString()
            writer.appendLine("    \"${name.asKotlinStringLiteral()}\" to this.`$name`,")
        }
        writer.appendLine(")")
    }
}

private fun String.asKotlinStringLiteral(): String =
    replace("\\", "\\\\").replace("\"", "\\\"")
```

`Dependencies(false, source)` declares an **isolating** output: this generated file depends on one source. An aggregating processor (for example, one registry containing every annotated type) declares `aggregating = true` and all relevant source files. Incorrect dependency metadata produces stale generated code or needless full rebuilds.

Production generators also must:

- reject unsupported declarations with `logger.error(message, symbol)` so the IDE points at the source;
- handle keywords, escaped identifiers, nested/generic types, visibility, inheritance, duplicate simple names, and empty/default packages;
- avoid generating the same file twice across rounds;
- close output streams, use deterministic ordering, and never embed absolute paths/timestamps;
- use KotlinPoet or an equivalent structured writer when types/imports become nontrivial;
- keep runtime annotations separate so consumers do not depend on KSP APIs.

Test by compiling source snippets and asserting both diagnostics and generated behavior. Cover one happy case plus invalid targets, keywords, nested classes, incremental changes, and two classes with the same simple name in different packages. A text snapshot catches accidental output changes; executing the compiled generated function proves it is valid Kotlin.

> ⚠️ **Gotcha** — `getAllProperties()` may include inherited properties and its order should not be treated as a serialization contract. Define whether inherited/private/computed properties participate, sort deterministically if order matters, and document schema compatibility.

---

### Summary

- **Metaprogramming** generates boilerplate at **compile time**, avoiding reflection's runtime cost — the basis of Room, Dagger, Moshi, serialization, Compose.
- **KSP** (prefer it) gives processors a **Kotlin-aware, resolved symbol model** and is much faster than **kapt** (which generates Java stubs). KSP can **generate** code, not modify it.
- A **`SymbolProcessor`** queries a `Resolver` for annotated symbols and emits `.kt` files via a `CodeGenerator`; a `SymbolProcessorProvider` registers it.
- **Compiler plugins** *transform* existing code (serialization, Compose, all-open, Parcelize) — more powerful, rarely hand-written.
- Choose: plain code → **KSP** → reflection → compiler plugin, in that order of preference.
- A production KSP processor validates/defer symbols, declares isolating or aggregating dependencies accurately, emits deterministic escaped source, reports source-attached errors, and is tested by compiling representative snippets.

### Self-check quiz

1. What's the key advantage of KSP over kapt?
   <details><summary>Answer</summary>KSP gives a Kotlin-aware, resolved symbol model without generating Java stubs, so it's faster and understands Kotlin constructs (data classes, nullability, generics) directly.</details>
2. What can KSP do, and what can it *not* do?
   <details><summary>Answer</summary>It can generate new code (new `.kt` files); it cannot modify existing code — that requires a full compiler plugin.</details>
3. Name two features that are actually compiler plugins.
   <details><summary>Answer</summary>Any two of: kotlinx.serialization, Jetpack Compose, all-open, no-arg, Parcelize.</details>
4. When would you use reflection instead of KSP?
   <details><summary>Answer</summary>When the type/shape isn't known until runtime (fully dynamic), so there's nothing to generate at compile time.</details>

### Exercises

**Exercise 30.1 — Predict the generated code (guided).** Given the `@AutoMap` processor from §30.3, what does it generate for `@AutoMap data class Point(val x: Int, val y: Int)`?

<details><summary>Show answer</summary>

```kotlin
package com.example   // (its actual package)

fun Point.toMap(): Map<String, Any?> = mapOf(
    "x" to x,
    "y" to y,
)
```

**Why:** the processor reads `Point`'s properties (`x`, `y`) and emits a `toMap()` extension mapping each property name to its value — a normal function with no reflection, compiled alongside your code.

</details>

**Exercise 30.2 — Codegen or reflection?** For each, pick codegen (KSP) or reflection: (a) a JSON serializer for known `@Serializable` classes; (b) a debugger that inspects arbitrary objects at runtime; (c) generating DB DAOs from `@Dao` interfaces.

<details><summary>Show answer</summary>

- (a) **Codegen** — the classes are known at compile time (this is what kotlinx.serialization does).
- (b) **Reflection** — the objects/types are arbitrary and only known at runtime.
- (c) **Codegen** — the interfaces are known at compile time (this is what Room does via KSP).

**Why:** codegen fits when the shape is known at compile time (fast, no runtime cost); reflection fits when it's only known at runtime.

</details>

### Chapter project: an AutoMap processor

> 🛠️ **Chapter Project** — **Standalone mini-project** (build tooling). **Builds on:** Ch.1–30. We specify (and hand-trace) a KSP processor that replaces Chapter 29's *reflective* mapper with *generated* code.

**Goal.** Design the `@AutoMap` → `toMap()` generator and compare it to the reflection version.

<details><summary>Show design + commentary</summary>

**Modules** (KSP requires the processor in a separate module):

```text
project/
├── app/                     ← uses @AutoMap; depends on :processor via ksp(...)
│   └── build.gradle.kts:  plugins { id("com.google.devtools.ksp") }
│                          dependencies { ksp(project(":processor")) }
└── processor/              ← the SymbolProcessor + provider (from §30.3)
```

**Input** (in `app`):

```kotlin
@AutoMap
data class Task(val id: Int, val title: String, val done: Boolean)
```

**Generated** (by KSP, into `app`'s build output — you never write this):

```kotlin
package com.example.app

fun Task.toMap(): Map<String, Any?> = mapOf(
    "id" to id,
    "title" to title,
    "done" to done,
)
```

**Use** (in `app`):

```kotlin
val map = Task(1, "Learn KSP", false).toMap()
// → {id=1, title=Learn KSP, done=false}
```

**Commentary.**
- Compare to Chapter 29's `fromRow`/reflective mapper: that resolved constructors and read annotations **at runtime, on every call**. This generates a `toMap()` **once, at compile time** — the running app calls a plain `mapOf(...)`, as fast as if you'd typed it, with no `kotlin-reflect` dependency.
- The processor "sees" `Task` through KSP's resolved model (`KSClassDeclaration`, `getAllProperties()`), so it correctly handles the `data class`'s properties — something kapt would see through a lossy Java projection.
- The trade-off: codegen needs the type known at compile time and a bit of build setup (a processor module, the KSP Gradle plugin). For fixed, annotation-driven boilerplate, that's a great deal — which is why Room, Moshi, and Dagger all work this way.
- This is the endpoint of the reflection→codegen progression: reflection (Ch.29) for the dynamic case, KSP here for the compile-time-known case.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Metaprogramming** | Generating/transforming code, typically at compile time. |
| **KSP** | Kotlin Symbol Processing — Kotlin-native code generation from annotations. |
| **kapt** | The older Java-stub-based annotation processing (slower). |
| **`SymbolProcessor`** | The KSP interface that reads symbols and generates code. |
| **`Resolver` / `CodeGenerator`** | KSP's model of the code / its file emitter. |
| **Compiler plugin** | A deeper hook that transforms existing code during compilation. |
| **all-open / no-arg / Parcelize** | Common compiler plugins. |
| **KSP2** | The current KSP implementation and default processing engine. |
| **Isolating / aggregating output** | Generated code depending on one source / a collection of sources. |
| **Incremental processing** | Regenerating only outputs affected by changed source dependencies. |

### What's next

You've seen how serializers are *generated*. **[Ch.31 — Serialization in Depth](#chapter-31--serialization-in-depth)** uses `kotlinx.serialization` (itself a compiler plugin) to its full extent — polymorphism, custom serializers, and formats — to give the Task Manager robust JSON persistence.

[↑ back to top](#chapter-30--metaprogramming-ksp--compiler-plugins)


---

## Chapter 31 — Serialization in Depth

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.10 — Sealed classes](#chapter-10--advanced-object-oriented-features), [Ch.20 — Ktor](#chapter-20--ktor-for-backend-development), [Ch.30 — Compiler plugins](#chapter-30--metaprogramming-ksp--compiler-plugins)

**Learning objectives** — after this chapter you will be able to:

- Serialize and deserialize objects with `kotlinx.serialization`.
- Configure JSON output and control field naming/inclusion.
- Serialize polymorphic (sealed) hierarchies.
- Write a custom serializer when needed.

**In this chapter**

- [31.1 The basics](#311-the-basics)
- [31.2 Configuring JSON](#312-configuring-json)
- [31.3 Field control](#313-field-control)
- [31.4 Polymorphic serialization](#314-polymorphic-serialization)
- [31.5 Custom serializers](#315-custom-serializers)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-persisting-tasks-as-json)· Glossary · What's next

---

### 31.1 The basics

**`kotlinx.serialization`** is Kotlin's multiplatform serialization library. It's driven by a **compiler plugin** (Chapter 30) that *generates* a serializer for each `@Serializable` class at compile time — so there's **no reflection**, it's fast, and it works on every platform.

Setup:

```kotlin
plugins {
    kotlin("plugin.serialization") version "2.4.0"
}
dependencies {
    implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.11.0")
}
```

Mark a class `@Serializable` and use `Json.encodeToString` / `decodeFromString`:

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
data class Task(val id: Int, val title: String, val done: Boolean = false)

fun main() {
    val task = Task(1, "Learn serialization")
    val text = Json.encodeToString(task)
    println(text)                                   // → {"id":1,"title":"Learn serialization"}

    val back = Json.decodeFromString<Task>(text)
    println(back)                                    // → Task(id=1, title=Learn serialization, done=false)
}
```

Notice `done` is **absent** from the output: by default, properties equal to their default value are omitted (`encodeDefaults = false`). On the way back, the missing `done` falls back to its default `false`.

> ⚙️ **Under the hood** — For each `@Serializable` type, the compiler plugin generates a `KSerializer` implementation describing the type's fields and how to read/write them. `Json.encodeToString(task)` finds that generated serializer (via a `reified` type parameter) and drives it — no runtime type inspection. This compile-time generation is why the same code serializes on JVM, JS, and Native identically, and why it's much faster than reflection-based libraries.

### 31.2 Configuring JSON

The `Json { }` builder configures behaviour; create a configured instance and reuse it:

```kotlin
val json = Json {
    prettyPrint = true          // human-readable, indented output
    ignoreUnknownKeys = true    // don't fail on JSON fields not in the class (API evolution)
    encodeDefaults = true       // include properties even when equal to their default
}
```

- **`ignoreUnknownKeys`** is essential for robustness: when a server adds a field your class doesn't have, decoding won't crash.
- **`prettyPrint`** indents (4 spaces) for readability/logging.
- **`encodeDefaults`** forces default-valued properties into the output.

### 31.3 Field control

Annotations fine-tune the mapping between properties and JSON keys:

```kotlin
import kotlinx.serialization.*

@Serializable
data class User(
    @SerialName("user_name") val name: String,     // JSON key differs from property name
    val email: String,
    @Transient val sessionToken: String = "",        // excluded from (de)serialization; needs a default
)
```

- **`@SerialName("...")`** maps a property to a different JSON key (e.g. snake_case APIs).
- **`@Transient`** excludes a property entirely (it must have a default, since it won't be read from JSON).
- A property is **optional** if it has a default value; without one, it's **required** and missing JSON fails decoding (`@Required` can force a defaulted property to be mandatory).

### 31.4 Polymorphic serialization

The real power: serializing a **`sealed`** hierarchy (Chapter 10), where the JSON must record *which* subtype each value is. Mark the sealed base and each subtype `@Serializable`, and kotlinx.serialization adds a **type discriminator** automatically:

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
sealed class Shape {
    @Serializable @SerialName("circle")
    data class Circle(val radius: Double) : Shape()

    @Serializable @SerialName("rectangle")
    data class Rectangle(val width: Double, val height: Double) : Shape()
}

fun main() {
    val shapes: List<Shape> = listOf(Shape.Circle(2.0), Shape.Rectangle(3.0, 4.0))
    val text = Json.encodeToString(shapes)
    println(text)
    // → [{"type":"circle","radius":2.0},{"type":"rectangle","width":3.0,"height":4.0}]

    val back: List<Shape> = Json.decodeFromString(text)
    println(back)   // → [Circle(radius=2.0), Rectangle(width=3.0, height=4.0)]
}
```

The `"type"` field (the **discriminator**) records the subtype via each `@SerialName`, so decoding reconstructs the *correct* subtype. Sealed classes get this automatically (their subtypes are known); for open hierarchies you'd register subtypes in a `SerializersModule`. Change the discriminator key with `@JsonClassDiscriminator("kind")` on the base class.

> ⚠️ **Gotcha** — Polymorphic decoding needs every subtype to be *registered*. For `sealed` classes this is automatic (the compiler knows them all). For **non-sealed** polymorphism you must build a `SerializersModule` listing the subtypes, or decoding an unregistered type throws. Prefer `sealed` when you can — it's simpler and safer.

### 31.5 Custom serializers

When a type isn't `@Serializable` (a third-party class) or needs a non-default representation (a date as an ISO string, a `Color` as a hex string), write a **`KSerializer`**:

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.descriptors.*
import kotlinx.serialization.encoding.*
import java.time.LocalDate

object LocalDateSerializer : KSerializer<LocalDate> {
    override val descriptor = PrimitiveSerialDescriptor("LocalDate", PrimitiveKind.STRING)
    override fun serialize(encoder: Encoder, value: LocalDate) =
        encoder.encodeString(value.toString())               // e.g. "2026-07-12"
    override fun deserialize(decoder: Decoder): LocalDate =
        LocalDate.parse(decoder.decodeString())
}

@Serializable
data class Event(
    val name: String,
    @Serializable(with = LocalDateSerializer::class) val date: LocalDate
)
```

The serializer defines a `descriptor` (the shape — here a string) plus `serialize`/`deserialize`. Attach it with `@Serializable(with = …)` on a property, or `@file:UseSerializers` for a whole file, or contextually via a `SerializersModule`.

---

### Summary

- **`kotlinx.serialization`** is a compiler-plugin-driven, reflection-free, multiplatform library. Mark classes **`@Serializable`**; use **`Json.encodeToString`/`decodeFromString`**.
- Default-valued properties are omitted unless **`encodeDefaults = true`**; configure via **`Json { }`** (`prettyPrint`, **`ignoreUnknownKeys`** for robustness).
- **`@SerialName`** renames a JSON key; **`@Transient`** excludes a property (needs a default); defaulted properties are optional.
- **`sealed`** hierarchies serialize polymorphically with an automatic **`"type"` discriminator** (each subtype's `@SerialName`); non-sealed polymorphism needs a `SerializersModule`.
- Write a **`KSerializer`** (descriptor + `serialize`/`deserialize`) for non-`@Serializable` or custom-format types.

### Self-check quiz

1. Why is kotlinx.serialization fast and multiplatform?
   <details><summary>Answer</summary>A compiler plugin generates a `KSerializer` per class at compile time — no runtime reflection — so it runs the same on JVM/JS/Native and avoids reflection's cost.</details>
2. Why is `ignoreUnknownKeys = true` important?
   <details><summary>Answer</summary>It lets decoding tolerate JSON fields the class doesn't have (e.g. when a server adds fields), instead of throwing — crucial for API evolution.</details>
3. How does a `sealed` hierarchy serialize which subtype a value is?
   <details><summary>Answer</summary>Via a type discriminator (default key `"type"`) set to each subtype's `@SerialName`; the compiler knows all sealed subtypes, so decoding reconstructs the right one automatically.</details>
4. When do you need a custom `KSerializer`?
   <details><summary>Answer</summary>For types you can't annotate `@Serializable` (third-party) or that need a non-default representation (e.g. a date as an ISO string).</details>

### Exercises

**Exercise 31.1 — Round-trip (guided).** Serialize a `Config(host, port, debug=false)` with `encodeDefaults=true` and pretty printing, then decode it back.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
data class Config(val host: String, val port: Int, val debug: Boolean = false)

fun main() {
    val json = Json { prettyPrint = true; encodeDefaults = true }
    val text = json.encodeToString(Config("localhost", 8080))
    println(text)
    val back = json.decodeFromString<Config>(text)
    println(back)   // → Config(host=localhost, port=8080, debug=false)
}
```

Output:
```text
{
    "host": "localhost",
    "port": 8080,
    "debug": false
}
Config(host=localhost, port=8080, debug=false)
```

**Why this works:** `encodeDefaults = true` forces `debug` (equal to its default) into the JSON; `prettyPrint` indents it. Decoding reconstructs the `Config` exactly.

</details>

**Exercise 31.2 — Rename a key.** Serialize `data class Person(val fullName: String)` so the JSON key is `full_name`.

<details><summary>Show solution</summary>

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
data class Person(@SerialName("full_name") val fullName: String)

fun main() {
    println(Json.encodeToString(Person("Alice")))   // → {"full_name":"Alice"}
}
```

**Why this works:** `@SerialName("full_name")` overrides the JSON key for that property while the Kotlin name stays `fullName` — the standard way to bridge Kotlin's camelCase to a snake_case API.

</details>

### Chapter project: persisting tasks as JSON

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–31. We give tasks a `sealed` type hierarchy and serialize a list of them polymorphically — robust, human-readable persistence.

**Goal.** Model simple and deadline tasks as a sealed hierarchy, then serialize/deserialize a mixed list with the correct subtypes preserved.

<details><summary>Show reference solution + commentary</summary>

```kotlin
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
sealed class Task {
    abstract val id: Int
    abstract val title: String

    @Serializable
    @SerialName("simple")
    data class Simple(override val id: Int, override val title: String) : Task()

    @Serializable
    @SerialName("deadline")
    data class Deadline(
        override val id: Int,
        override val title: String,
        val dueDay: Int
    ) : Task()
}

fun main() {
    val tasks: List<Task> = listOf(
        Task.Simple(1, "Buy milk"),
        Task.Deadline(2, "File taxes", dueDay = 105)
    )

    val json = Json { prettyPrint = true }
    val text = json.encodeToString(tasks)
    println(text)

    val restored: List<Task> = json.decodeFromString(text)
    println("Restored ${restored.size}: ${restored.map { it.title }}")
    println("Second is a Deadline: ${restored[1] is Task.Deadline}")
}
```

Output:

```text
[
    {
        "type": "simple",
        "id": 1,
        "title": "Buy milk"
    },
    {
        "type": "deadline",
        "id": 2,
        "title": "File taxes",
        "dueDay": 105
    }
]
Restored 2: [Buy milk, File taxes]
Second is a Deadline: true
```

**Commentary.**
- `Task` is now a **sealed hierarchy** (Chapter 10): a `Simple` task and a `Deadline` task carry different data. Serialization records *which* via the `"type"` discriminator (`"simple"`/`"deadline"` from `@SerialName`), so `decodeFromString` reconstructs the **exact subtypes** — `restored[1] is Task.Deadline` is `true`.
- Because `Task` is `sealed`, the subtypes are registered automatically — no `SerializersModule` boilerplate.
- This is the real persistence format that would sit behind the Chapter 21 database (as a JSON column) or the Chapter 20 API (as the response body) — one serialization scheme, reused everywhere, generated at compile time.
- For a real due-date you'd store a `LocalDate` with the custom `KSerializer` from §31.5; we used `dueDay: Int` here so the example is self-contained. The exhaustive `when` (Chapter 10) over `Task` pairs perfectly with this — add a `Recurring` subtype and the compiler flags every handler to update.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`kotlinx.serialization`** | Kotlin's compiler-plugin-driven, multiplatform serialization library. |
| **`@Serializable`** | Marks a type for serialization (generates a `KSerializer`). |
| **`Json { }`** | Configures JSON behaviour (`prettyPrint`, `ignoreUnknownKeys`, `encodeDefaults`). |
| **`@SerialName`** | Overrides a JSON key (or a subtype's discriminator value). |
| **`@Transient`** | Excludes a property from serialization (needs a default). |
| **Discriminator** | The `"type"` field recording a polymorphic subtype. |
| **`SerializersModule`** | Registers subtypes for non-sealed polymorphism. |
| **`KSerializer`** | A custom serializer (`descriptor` + `serialize`/`deserialize`). |

### What's next

Your data serializes efficiently. **[Ch.32 — Performance & Memory](#chapter-32--performance--memory)** turns to speed: allocation and boxing, primitive arrays, when `Sequence`/`inline` help, and how to *measure* performance properly with JMH instead of guessing.

[↑ back to top](#chapter-31--serialization-in-depth)


---

## Chapter 32 — Performance & Memory

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.6 — Collections](#chapter-6--collections), [Ch.7 — Null Safety](#chapter-7--null-safety), [Ch.10 — value classes](#chapter-10--advanced-object-oriented-features), [Ch.25 — inline](#chapter-25--advanced-topics--next-steps)

**Learning objectives** — after this chapter you will be able to:

- Reason about allocation and boxing costs.
- Choose primitive arrays and value classes to avoid overhead.
- Know when `Sequence`/`inline` help and when they don't.
- Measure performance properly with JMH instead of guessing.
- Profile whole applications, reason about coroutine/service latency, and distinguish JVM from Native memory behavior.

**In this chapter**

- [32.1 Allocation and boxing](#321-allocation-and-boxing)
- [32.2 Primitive arrays and value classes](#322-primitive-arrays-and-value-classes)
- [32.3 Sequences, inline, and strings](#323-sequences-inline-and-strings)
- [32.4 Measuring with JMH](#324-measuring-with-jmh)
- [32.5 Profiling applications and reading allocation evidence](#325-profiling-applications-and-reading-allocation-evidence)
- [32.6 Coroutines, latency, and Kotlin/Native memory](#326-coroutines-latency-and-kotlinnative-memory)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-optimising-a-hot-path)· Glossary · What's next

---

### 32.1 Allocation and boxing

Most Kotlin is fast enough without thought. But in **hot paths** — code run millions of times, tight loops, high-throughput services — a few patterns dominate cost, and the biggest is **allocation**: every object you create is memory the garbage collector must later reclaim. Fewer allocations means less GC pressure and better throughput.

The subtlest allocator is **boxing** (Chapter 7). A non-null `Int` is a JVM primitive `int` — no allocation. But the moment an `Int` must become an object — as a nullable (`Int?`), inside a generic (`List<Int>`), or as `Any` — it's **boxed** into a heap `java.lang.Integer`:

```kotlin
val a: Int = 5              // primitive int — free
val b: Int? = 5            // boxed Integer — a heap object
val list: List<Int> = listOf(1, 2, 3)   // THREE boxed Integers (generics erase to Object)
```

A `List<Int>` of a million elements is a million boxed `Integer` objects — plus the list's internal `Object[]`. In a hot path that's enormous, avoidable overhead.

> ⚙️ **Under the hood** — Generics are erased to `Object` (Chapter 12), and `Object` can't hold a primitive, so `List<Int>` *must* box. This is a JVM limitation Kotlin inherits from Java. The JIT's **escape analysis** can sometimes eliminate a short-lived boxing that never leaves a method, but you can't rely on it — for guaranteed no-boxing, use a primitive-specialized structure.

### 32.2 Primitive arrays and value classes

For collections of primitives, Kotlin provides **primitive arrays** — `IntArray`, `LongArray`, `DoubleArray`, `BooleanArray` — which map to JVM `int[]`, `long[]`, etc., with **no boxing**:

```kotlin
val boxed: Array<Int> = arrayOf(1, 2, 3)       // Integer[] — 3 boxed objects
val unboxed: IntArray = intArrayOf(1, 2, 3)    // int[] — raw primitives, zero boxing

fun sum(xs: IntArray): Int {                    // iterates raw ints
    var total = 0
    for (x in xs) total += x
    return total
}
```

For a large numeric dataset, an `IntArray` uses a fraction of the memory of a `List<Int>` (no per-element object header) and iterates faster. **`value` classes** (Chapter 10) similarly give type-safety with no allocation — a `Money(cents: Long)` is just a `Long` at runtime.

> 💡 **Idiom** — Use `List<Int>` for clarity in ordinary code; switch to **`IntArray`** only in measured hot paths over large numeric data. The `List` API is friendlier; the array is faster and leaner. Don't reach for `IntArray` prematurely — most code never needs it.

### 32.3 Sequences, inline, and strings

**`Sequence` (Chapter 6)** avoids intermediate-list allocations in multi-step pipelines over *large* data — but has per-element overhead that makes it *slower* on small collections. Use it when data is big and the chain is long/short-circuiting; otherwise eager operators win.

**`inline` (Chapter 25)** removes lambda allocation for higher-order functions in hot loops — but bloats bytecode if the function is large. Reserve it for small, hot utilities.

**String building**: concatenating in a loop with `+` allocates a new `String` each iteration (O(n²)). Use `buildString`/`StringBuilder`:

```kotlin
// Slow: a new String per iteration
var s = ""
for (i in 1..1000) s += i          // ~1000 intermediate strings

// Fast: one growing buffer
val fast = buildString { for (i in 1..1000) append(i) }
```

Also avoid **needless captures**: a lambda that captures a mutable variable can force allocation; a lambda capturing nothing may be reused. And prefer **`ArrayDeque`** over `LinkedList` for stack/queue workloads (better cache locality).

> ⚠️ **Gotcha — premature optimization.** These techniques matter in *measured* hot paths. Applying them everywhere makes code harder to read for no benefit — and can even *hurt* (a `Sequence` on a 3-element list is slower). The order is: **write clear code first, profile, then optimize the proven hot spots.** Guessing at performance is almost always wrong.

### 32.4 Measuring with JMH

You cannot optimize what you don't measure — and naive timing (`System.nanoTime()` around a loop) is *misleading* on the JVM, because the JIT compiler warms up, optimizes, and can even eliminate code whose result you ignore. The right tool is **JMH** (Java Microbenchmark Harness), via the `kotlinx-benchmark` plugin, which handles warmup, multiple iterations, and dead-code elimination correctly.

```kotlin
import org.openjdk.jmh.annotations.*

@State(Scope.Benchmark)
open class SumBenchmark {
    private val list = List(1_000_000) { it }
    private val array = IntArray(1_000_000) { it }

    @Benchmark fun sumList(): Int = list.sum()      // boxed
    @Benchmark fun sumArray(): Int = array.sum()    // unboxed
}
```

Run it, and JMH reports throughput (ops/sec) for each with statistical rigor. Typically `sumArray` is *several times* faster and allocates nothing, while `sumList` churns through boxed `Integer`s — but the point is you'd **see the actual numbers**, on your hardware, rather than assume.

> ⚙️ **Under the hood** — The JVM runs bytecode interpreted at first, then the **JIT** compiles hot methods to optimized native code (with inlining, escape analysis, loop optimizations). This means the first runs are slow and unrepresentative — hence JMH's **warmup** phase. It also inserts "blackholes" so the JIT can't delete a benchmark whose result you don't use. Measuring without these safeguards produces numbers that are often *wrong by an order of magnitude*.

### 32.5 Profiling applications and reading allocation evidence

A microbenchmark answers "which implementation is faster under this synthetic workload?" It does not tell you which code matters in the application. Start with production-like **profiling**:

1. Define a user-visible objective (p95/p99 latency, startup time, throughput, memory ceiling).
2. Reproduce with representative data, concurrency, JVM flags, and warmup.
3. Record CPU samples, allocation samples, GC pauses, locks, thread states, and I/O waits.
4. Optimize the dominant contributor, verify behavior, then repeat the same measurement.

On the JVM, Java Flight Recorder/JDK Mission Control provide low-overhead recordings; async-profiler produces CPU, wall-clock, allocation, and lock flame graphs. Heap histograms show which classes occupy memory; a heap dump plus dominator tree shows **why objects remain reachable**. A high allocation rate is not itself a leak—a leak is retained, unwanted reachability over time.

Interpret flame graphs carefully: width is sampled cost, not call count; an off-CPU/wall profile reveals blocking that a CPU profile cannot. Compare before/after distributions and confidence intervals, not one best run. Watch for coordinated omission in load generators and always report percentiles, not only averages.

> ⚠️ **Gotcha — benchmark environment.** Debug builds, profilers with heavy instrumentation, laptop power saving, thermal throttling, noisy neighbors, tiny datasets, and an un-warmed JIT can dominate the code being measured. Record the environment and keep benchmark inputs/results versioned.

### 32.6 Coroutines, latency, and Kotlin/Native memory

Coroutines are lightweight, not free. A suspended coroutine retains a continuation and whatever locals remain live across suspension. Millions of queued coroutines, unbounded channels, or `shareIn` scopes that never end can retain substantial graphs.

Performance rules for concurrent services:

- bound queues and concurrency (`Semaphore`, fixed worker count, connection pool);
- avoid `async` when work is sequential or immediately awaited;
- never use `Dispatchers.IO` to hide unbounded blocking—the dispatcher can expand, while downstream capacity remains finite;
- use timeouts at external boundaries and propagate cancellation;
- inspect coroutine dumps/debug probes during stalls, but do not ship expensive debug instrumentation blindly;
- measure end-to-end latency; reducing a 50 ns lambda allocation cannot fix a 50 ms database query.

Kotlin/Native has a shared heap and tracing garbage collector integrated with platform interop; it is not the old "freeze every shared object" model. Its collector/allocator and Swift/Objective-C ARC interaction differ from the JVM. Retain cycles that cross Kotlin and Swift ownership, stable references, pinned objects, and large global graphs deserve specific testing with Xcode Instruments and Native GC metrics. Kotlin 2.4 enables concurrent marking by default, improving pause behavior but not removing the need to measure allocation and retention.

For JS/Wasm, browser performance tools, bundle analysis, source maps, and DOM/layout costs matter more than JVM boxing. Performance advice is target-specific; keep shared algorithms clear, then profile the binary that users actually run.

---

### Summary

- **Allocation** drives GC pressure; the sneakiest source is **boxing** — an `Int` becomes a heap `Integer` as a nullable (`Int?`), in a generic (`List<Int>`), or as `Any`.
- Use **primitive arrays** (`IntArray`, …) for large numeric data (no boxing, less memory, faster) and **`value` classes** for zero-cost type safety.
- **`Sequence`** helps big multi-step pipelines but hurts small ones; **`inline`** removes lambda cost for small hot functions but bloats large ones; build strings with **`buildString`/`StringBuilder`**, not `+` in loops.
- **Don't optimize prematurely** — write clear code, profile, then fix proven hot spots.
- **Measure with JMH** (not naive timing): the JIT's warmup and dead-code elimination make hand-rolled microbenchmarks misleading.
- Use application profilers before microbenchmarks, distinguish allocation rate from retained leaks, bound coroutine concurrency/queues, and profile JVM, Native, JS, and Wasm with target-appropriate tools.

### Self-check quiz

1. Name three situations where an `Int` gets boxed.
   <details><summary>Answer</summary>As a nullable (`Int?`), inside a generic type (`List<Int>`), or when used as a supertype like `Any`.</details>
2. When should you use `IntArray` instead of `List<Int>`?
   <details><summary>Answer</summary>In measured hot paths over large numeric data, where avoiding per-element boxing and object headers matters. For ordinary code, `List<Int>` is clearer.</details>
3. Why is a `Sequence` sometimes slower than eager operators?
   <details><summary>Answer</summary>It has per-element overhead; on small collections that outweighs the saved intermediate-list allocations. It pays off only on large, multi-step (short-circuitable) pipelines.</details>
4. Why is naive `nanoTime`-around-a-loop benchmarking unreliable?
   <details><summary>Answer</summary>The JIT warms up and optimizes over time (early runs unrepresentative) and can eliminate code whose result is unused. JMH handles warmup and prevents dead-code elimination.</details>

### Exercises

**Exercise 32.1 — Spot the boxing (guided).** Which of these allocate boxed integers, and which don't?
```kotlin
val a = intArrayOf(1, 2, 3)
val b = listOf(1, 2, 3)
val c: Int? = 5
val d = 5 + 3
```

<details><summary>Show answer</summary>

- `a` (`IntArray`) — **no boxing** (raw `int[]`).
- `b` (`List<Int>`) — **boxes** each element (generics erase to `Object`).
- `c` (`Int?`) — **boxes** (nullable can't be a primitive).
- `d` (`Int`) — **no boxing** (a plain primitive `int`).

**Why:** boxing happens when an `Int` must be an object — nullable or inside a generic. `IntArray` and plain `Int` arithmetic stay primitive.

</details>

**Exercise 32.2 — Fix the string builder.** Rewrite this O(n²) concatenation efficiently:
```kotlin
fun joinNumbers(n: Int): String {
    var result = ""
    for (i in 1..n) result += "$i,"
    return result
}
```

<details><summary>Show solution</summary>

```kotlin
fun joinNumbers(n: Int): String = buildString {
    for (i in 1..n) append("$i,")
}
// Or, idiomatically: (1..n).joinToString(",") + ","
```

**Why this works:** `+=` on a `String` creates a new string each iteration (copying all prior characters — O(n²) total). `buildString`/`StringBuilder` appends into one growing buffer — O(n). For a simple join, `joinToString` is the clearest option of all.

</details>

### Chapter project: optimising a hot path

> 🛠️ **Chapter Project** — Advances the running **Task Manager**. **Builds on:** Ch.1–32. We optimise a bulk-import hot path — computing statistics over a *million* task ids — and benchmark the improvement.

**Goal.** Replace a boxed `List<Int>` hot path with an `IntArray`, and measure the difference with JMH.

<details><summary>Show solution + commentary</summary>

**Before** (idiomatic, but boxes a million integers on a hot path):

```kotlin
fun totalPriorityBoxed(priorities: List<Int>): Long {
    var sum = 0L
    for (p in priorities) sum += p   // each p is a boxed Integer, unboxed per iteration
    return sum
}
```

**After** (unboxed, for the measured hot path):

```kotlin
fun totalPriorityFast(priorities: IntArray): Long {
    var sum = 0L
    for (p in priorities) sum += p   // raw ints — no boxing, better cache locality
    return sum
}
```

**Benchmark:**

```kotlin
import org.openjdk.jmh.annotations.*

@State(Scope.Benchmark)
open class PriorityBenchmark {
    private val boxed = List(1_000_000) { it % 5 }
    private val unboxed = IntArray(1_000_000) { it % 5 }

    @Benchmark fun boxed(): Long = totalPriorityBoxed(boxed)
    @Benchmark fun unboxed(): Long = totalPriorityFast(unboxed)
}
```

**Representative result** (JMH, throughput — actual numbers vary by hardware):

```text
Benchmark                    Mode   Cnt   Score    Units
PriorityBenchmark.boxed     thrpt   ...   ~400    ops/s
PriorityBenchmark.unboxed   thrpt   ...  ~1600    ops/s   (several× faster)
```

**Commentary.**
- The `List<Int>` version stores a million boxed `Integer` objects; each iteration *unboxes* one, chasing a pointer to the heap. The `IntArray` version walks a contiguous `int[]` — no boxing, cache-friendly — and runs several times faster with **zero allocation** on the hot path.
- **Crucially, we measured.** The `IntArray` win is real *here* because the array is large and the loop is hot. On a 10-element list it would be irrelevant (and the `List` API is nicer) — which is exactly why the rule is *profile first*. We didn't guess; JMH showed the numbers.
- The rest of the Task Manager keeps using `List<Task>` for clarity — we optimized **only** the one proven bottleneck. That surgical approach — idiomatic everywhere, optimized where measured — is how experts balance readability and speed.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Allocation** | Creating a heap object (costs memory + eventual GC). |
| **Boxing** | Wrapping a primitive (`int`) in an object (`Integer`); needed for nullable/generic. |
| **Primitive array** | `IntArray`/`LongArray`/… mapping to `int[]` etc. — no boxing. |
| **Escape analysis** | A JIT optimization that can elide short-lived allocations. |
| **JIT** | Just-In-Time compiler turning hot bytecode into optimized native code. |
| **JMH** | Java Microbenchmark Harness — rigorous benchmarking (warmup, blackholes). |
| **Premature optimization** | Optimizing before profiling proves it's needed. |
| **Profiler / flame graph** | Runtime sampler / visualization of sampled call-stack cost. |
| **Allocation rate / retention** | How quickly objects are created / which objects remain reachable. |
| **Tail latency** | Slow-end request latency, commonly reported as p95/p99. |

### What's next

You can make hot code fast. **[Ch.33 — Architecture & Dependency Injection](#chapter-33--architecture--dependency-injection)** zooms out to the *structure* of large systems: clean layering, unidirectional dependencies, and wiring the Task Manager together with a DI framework.

[↑ back to top](#chapter-32--performance--memory)


---

## Chapter 33 — Architecture & Dependency Injection

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Interfaces](#chapter-9--inheritance--interfaces), [Ch.19 — Gradle modules](#chapter-19--gradle-with-kotlin-dsl), [Ch.21 — Repository](#chapter-21--database-access)

**Learning objectives** — after this chapter you will be able to:

- Structure an app in clean, unidirectional layers.
- Apply the dependency rule and program to abstractions.
- Wire dependencies manually and with a DI framework (Koin).
- Split a project into modules with clear boundaries.

**In this chapter**

- [33.1 Layered architecture](#331-layered-architecture)
- [33.2 The dependency rule and DI](#332-the-dependency-rule-and-di)
- [33.3 Manual DI](#333-manual-di)
- [33.4 DI frameworks: Koin and Hilt](#334-di-frameworks-koin-and-hilt)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-layered-task-manager)· Glossary · What's next

---

### 33.1 Layered architecture

As an app grows, *how you organize it* matters as much as the code. The dominant pattern is **layered (clean) architecture**, which separates concerns into rings:

- **Domain** — the core: entities (`Task`), business rules, and *use cases* (application logic). Pure Kotlin, no frameworks, no I/O. This is the part you've been growing since Chapter 1.
- **Data** — implementations of the domain's abstractions: repositories backed by a database (Chapter 21) or network (Chapter 20).
- **Presentation** — the UI: ViewModels/Compose (Chapter 22) or HTTP routes (Chapter 20).

The two common presentation styles: **MVVM** (Model–View–ViewModel; the ViewModel exposes state, Chapter 22) and **MVI** (Model–View–Intent; a stricter single-state, event-driven variant). Both use the unidirectional data flow you've already met.

### 33.2 The dependency rule and DI

The one rule that makes layering work: **dependencies point inward.** The domain depends on *nothing*; data and presentation depend on the domain (via its interfaces), never the reverse. The domain defines a `TaskRepository` *interface* (a "port"); the data layer provides an *implementation* (an "adapter"). This is **dependency inversion** — the exact seam you built in Chapter 9 and cashed in with Exposed in Chapter 21.

But *who creates* the implementations and hands them to the classes that need them? That's **dependency injection (DI)**: instead of a class constructing its own dependencies (hard-coding `InMemoryTaskRepository()` inside `TaskManager`), it *receives* them — usually through its constructor. The dependencies are wired together at one place, the **composition root**.

> 💡 **Idiom** — **Constructor injection is the default.** A class declares what it needs as constructor parameters (`class Service(private val repo: Repository)`) and never news up its own collaborators. This makes dependencies explicit, swappable (a real repo in production, a mock in tests — Chapter 24), and impossible to forget. Field injection and service locators are inferior fallbacks.

### 33.3 Manual DI

You don't need a framework to do DI — for many apps, wiring the graph by hand at the composition root is the simplest, clearest option:

```kotlin
// ---- Domain (pure) ----
data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {                     // port
    fun add(title: String): Task
    fun all(): List<Task>
}

class AddTaskUseCase(private val repo: TaskRepository) {   // application logic
    operator fun invoke(title: String): Task {
        require(title.isNotBlank()) { "Title must not be blank" }
        return repo.add(title.trim())
    }
}

// ---- Data (adapter) ----
class InMemoryTaskRepository : TaskRepository {
    private val tasks = mutableListOf<Task>()
    private var nextId = 1
    override fun add(title: String) = Task(nextId++, title).also { tasks.add(it) }
    override fun all() = tasks.toList()
}

// ---- Presentation ----
class TaskPresenter(
    private val addTask: AddTaskUseCase,
    private val repo: TaskRepository
) {
    fun onAdd(title: String) { addTask(title) }
    fun render(): String = repo.all().joinToString("\n") { "- ${it.title}" }
}

fun main() {
    // Composition root: build the graph once, here
    val repo: TaskRepository = InMemoryTaskRepository()
    val addTask = AddTaskUseCase(repo)
    val presenter = TaskPresenter(addTask, repo)

    presenter.onAdd("Design the architecture")
    presenter.onAdd("Wire the dependencies")
    println(presenter.render())
}
```

Output:

```text
- Design the architecture
- Wire the dependencies
```

Every class receives its dependencies; nothing constructs its own. To test `AddTaskUseCase`, pass a mock `TaskRepository` (Chapter 24). To switch to the Exposed repository (Chapter 21), change *one line* at the composition root. That flexibility is the whole point.

### 33.4 DI frameworks: Koin and Hilt

As the graph grows to dozens of classes, wiring by hand becomes tedious. **DI frameworks** automate it. Two dominate Kotlin:

**Koin** is a lightweight, pure-Kotlin DI framework using a DSL (Chapter 17). You declare *how* to build each type in a `module`, and Koin resolves the graph at runtime:

```kotlin
import org.koin.dsl.module

val appModule = module {
    single<TaskRepository> { InMemoryTaskRepository() }   // one shared instance
    factory { AddTaskUseCase(get()) }                     // new each time; get() resolves deps
    factory { TaskPresenter(get(), get()) }
}
```

`single` = one shared instance; `factory` = a fresh one per request; `get()` resolves a dependency from the graph. You start Koin with `startKoin { modules(appModule) }` and retrieve wired objects.

**Hilt/Dagger** take a different approach: **compile-time** DI via annotation processing (Chapter 30). You annotate (`@Inject`, `@Module`), and the compiler *generates* the wiring code — so errors surface at build time and there's no runtime resolution cost. Hilt is the Android standard.

> ⚙️ **Under the hood** — **Koin** is essentially a *runtime registry*: a map from types to factory lambdas, resolved when you ask (`get()`). Simple and flexible, but a missing binding fails at *runtime*. **Dagger/Hilt** generate the wiring at *compile time* (Chapter 30's codegen), so a missing/circular dependency is a *compile error* and there's zero runtime overhead — at the cost of build complexity. The trade-off: Koin's simplicity vs Dagger's compile-time safety.

> ⚠️ **Gotcha — don't over-engineer, and keep frameworks out of the domain.** Small apps often need no DI framework — manual wiring is fine. When you do use one, keep its annotations/types in the *outer* layers; the **domain must stay pure** (no `@Inject`, no framework imports), or you've coupled your core business logic to a tool. Also avoid the **service-locator** anti-pattern (classes reaching into a global container to *pull* dependencies) — it hides dependencies and hurts testability; prefer *pushing* them via constructors.

---

### Summary

- **Layered/clean architecture** separates **domain** (pure core + use cases), **data** (repository implementations), and **presentation** (UI/routes).
- The **dependency rule**: dependencies point *inward*; the domain defines interfaces (ports), outer layers implement them (adapters) — **dependency inversion**.
- **Dependency injection** hands a class its collaborators instead of it constructing them; **constructor injection** is the default, wired at a **composition root**.
- **Manual DI** (wiring by hand) suits many apps; **Koin** (runtime registry, DSL) and **Hilt/Dagger** (compile-time codegen, safer, heavier) automate larger graphs.
- Keep the **domain framework-free**; avoid **over-engineering** and the **service-locator** anti-pattern.

### Self-check quiz

1. Which way do dependencies point in clean architecture, and what does the domain depend on?
   <details><summary>Answer</summary>Inward. The domain depends on nothing (pure); data and presentation depend on the domain's interfaces — never the reverse.</details>
2. What is constructor injection and why prefer it?
   <details><summary>Answer</summary>A class receives its dependencies as constructor parameters rather than constructing them. It makes dependencies explicit, swappable (real vs mock), and impossible to forget.</details>
3. How do Koin and Hilt differ fundamentally?
   <details><summary>Answer</summary>Koin resolves the graph at runtime (a registry; missing binding fails at runtime). Hilt/Dagger generate wiring at compile time (missing/circular deps are compile errors, no runtime cost).</details>
4. Why keep DI annotations out of the domain layer?
   <details><summary>Answer</summary>To keep the core business logic pure and framework-independent; coupling the domain to a DI tool undermines its reusability and testability.</details>

### Exercises

**Exercise 33.1 — Inject a dependency (guided).** Given `interface Clock { fun now(): Long }`, write a `Greeter(clock)` that uses it, and wire a real and a fake clock.

<details><summary>Show solution</summary>

```kotlin
interface Clock { fun now(): Long }

class Greeter(private val clock: Clock) {
    fun greet() = "Hello at ${clock.now()}"
}

fun main() {
    val fake = object : Clock { override fun now() = 42L }   // injected fake
    println(Greeter(fake).greet())   // → Hello at 42

    // In production you'd inject a real clock:
    // val real = object : Clock { override fun now() = System.currentTimeMillis() }
}
```

**Why this works:** `Greeter` depends on the `Clock` *abstraction* and receives it via its constructor. A test injects a deterministic fake (always `42`); production injects a real clock — the same class, different wiring. That's dependency injection in miniature.

</details>

**Exercise 33.2 — Koin module.** Write a Koin `module` providing a `single` `Logger` and a `factory` `Service(logger)`.

<details><summary>Show solution</summary>

```kotlin
import org.koin.dsl.module

interface Logger { fun log(msg: String) }
class ConsoleLogger : Logger { override fun log(msg: String) = println(msg) }
class Service(private val logger: Logger) { fun run() = logger.log("running") }

val appModule = module {
    single<Logger> { ConsoleLogger() }   // one shared logger
    factory { Service(get()) }           // new Service each time; get() injects the Logger
}
```

**Why this works:** `single<Logger> { ConsoleLogger() }` registers one shared `Logger`; `factory { Service(get()) }` builds a `Service`, with `get()` resolving the `Logger` from the graph. Koin wires the constructor injection for you.

</details>

### Chapter project: a layered Task Manager

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — a major restructure. **Builds on:** Ch.1–33. We reorganize everything we've built into clean domain/data/presentation layers, wired by DI.

**Goal.** Structure the Task Manager into layers with a use case, a repository port + adapter, and a presenter — all constructor-injected — and show swapping the adapter.

<details><summary>Show solution + commentary</summary>

```kotlin
// ================= DOMAIN (pure — no frameworks, no I/O) =================
data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {                        // port
    fun add(title: String): Task
    fun toggle(id: Int): Boolean
    fun all(): List<Task>
}

class AddTaskUseCase(private val repo: TaskRepository) {
    operator fun invoke(title: String): Result<Task> = runCatching {
        require(title.isNotBlank()) { "Title must not be blank" }
        repo.add(title.trim())
    }
}

class ToggleTaskUseCase(private val repo: TaskRepository) {
    operator fun invoke(id: Int): Boolean = repo.toggle(id)
}

// ================= DATA (adapter — swappable) =================
class InMemoryTaskRepository : TaskRepository {
    private val tasks = mutableListOf<Task>()
    private var nextId = 1
    override fun add(title: String) = Task(nextId++, title).also { tasks.add(it) }
    override fun toggle(id: Int): Boolean {
        val i = tasks.indexOfFirst { it.id == id }
        if (i == -1) return false
        tasks[i] = tasks[i].copy(done = !tasks[i].done)
        return true
    }
    override fun all() = tasks.toList()
}

// ================= PRESENTATION =================
class TaskPresenter(
    private val addTask: AddTaskUseCase,
    private val toggleTask: ToggleTaskUseCase,
    private val repo: TaskRepository
) {
    fun add(title: String): String =
        addTask(title).fold(
            onSuccess = { "Added: ${it.title}" },
            onFailure = { "Rejected: ${it.message}" }
        )
    fun toggle(id: Int) { toggleTask(id) }
    fun render(): String =
        repo.all().joinToString("\n") { "#${it.id} [${if (it.done) "x" else " "}] ${it.title}" }
}

// ================= COMPOSITION ROOT =================
fun main() {
    val repo: TaskRepository = InMemoryTaskRepository()   // swap for ExposedTaskRepository (Ch.21)
    val presenter = TaskPresenter(
        addTask = AddTaskUseCase(repo),
        toggleTask = ToggleTaskUseCase(repo),
        repo = repo
    )

    println(presenter.add("Design the layers"))    // → Added: Design the layers
    println(presenter.add("   "))                  // → Rejected: Title must not be blank
    presenter.toggle(1)
    println(presenter.render())
}
```

Output:

```text
Added: Design the layers
Rejected: Title must not be blank
#1 [x] Design the layers
```

**Commentary.**
- The **domain** (`Task`, `TaskRepository`, the use cases) is completely framework-free — it could compile in a KMP `commonMain` (Chapter 34) unchanged. The use cases combine `require` (Chapter 16) and `Result` (Chapter 16) to express "add if valid" cleanly.
- The **data** layer's `InMemoryTaskRepository` is an *adapter* behind the port. Swapping to the Chapter 21 `ExposedTaskRepository` changes exactly **one line** at the composition root — the payoff of the dependency rule, at application scale.
- The **presentation** `TaskPresenter` depends only on use cases and the repository interface, all **constructor-injected**. It never news up a collaborator, so every piece is independently testable (Chapter 24) with mocks.
- The **composition root** (`main`, or in a real app a Koin module / Hilt component) is the *one* place that knows the concrete wiring. Everything else depends on abstractions. This structure — pure domain, swappable data, injected everything — is what lets the Task Manager span CLI, backend, and Android from one core.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Clean/layered architecture** | Separating domain, data, and presentation concerns. |
| **Domain layer** | The pure core: entities, business rules, use cases. |
| **Use case** | A single unit of application logic. |
| **Dependency rule** | Dependencies point inward; the domain depends on nothing. |
| **Port / adapter** | A domain interface / its outer-layer implementation. |
| **Dependency injection** | Supplying a class's collaborators rather than it creating them. |
| **Constructor injection** | Receiving dependencies as constructor parameters. |
| **Composition root** | The single place the object graph is wired. |
| **Koin / Hilt** | Runtime-registry DI / compile-time codegen DI. |

### What's next

Your architecture is clean and its core is pure. **[Ch.34 — Kotlin Multiplatform in Depth](#chapter-34--kotlin-multiplatform-in-depth)** takes that pure core and *shares it* across JVM, Android, and iOS with `expect`/`actual`, source sets, and Compose Multiplatform.

[↑ back to top](#chapter-33--architecture--dependency-injection)


---

## Chapter 34 — Kotlin Multiplatform in Depth

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.25 — KMP basics](#chapter-25--advanced-topics--next-steps), [Ch.33 — Architecture](#chapter-33--architecture--dependency-injection)

**Learning objectives** — after this chapter you will be able to:

- Structure a KMP project's source sets and targets.
- Use `expect`/`actual` for functions, classes, and type aliases.
- Share domain, coroutines, and serialization across platforms.
- Understand iOS interop and Compose Multiplatform.
- Design exported APIs for Swift/Objective-C and JavaScript, test every target, and publish compatible variants.

> KMP is inherently multi-file/multi-module; this chapter is largely structural. The code shows source-set layout and `expect`/`actual`, not a single runnable `main`.

**In this chapter**

- [34.1 Targets and source sets](#341-targets-and-source-sets)
- [34.2 `expect`/`actual` in depth](#342-expectactual-in-depth)
- [34.3 Sharing real code](#343-sharing-real-code)
- [34.4 iOS interop and Compose Multiplatform](#344-ios-interop-and-compose-multiplatform)
- [34.5 Swift, Objective-C, C, and JavaScript boundaries](#345-swift-objective-c-c-and-javascript-boundaries)
- [34.6 Multiplatform testing, publication, and CI](#346-multiplatform-testing-publication-and-ci)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-multiplatform-core)· Glossary · What's next

---

### 34.1 Targets and source sets

**Kotlin Multiplatform (KMP)** lets you write logic once and compile it to multiple **targets**: the JVM (Android, backend), native binaries (iOS, macOS, Linux, Windows), JavaScript, and WebAssembly. You share as much as makes sense and drop to platform-specific code only where you must.

The structure is a set of **source sets**:

```text
src/
├── commonMain/      ← shared code, compiled to EVERY target (no platform APIs)
├── jvmMain/         ← JVM-only code (can use java.*)
├── androidMain/     ← Android-only (can use android.*)
├── iosMain/         ← iOS-only (can use platform.* / Foundation)
└── jsMain/          ← JS-only
```

`commonMain` holds the shared truth; each platform source set adds what only that platform can provide, and gets to use that platform's full API. Kotlin also supports **intermediate** source sets (e.g. an `appleMain` shared by `iosMain` + `macosMain`) — the *hierarchical source-set model*.

The Gradle setup declares the targets:

```kotlin
kotlin {
    jvm()
    androidTarget()
    iosArm64(); iosSimulatorArm64()
    js(IR) { browser() }

    sourceSets {
        commonMain.dependencies {
            implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.11.0")
            implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.11.0")
        }
    }
}
```

### 34.2 `expect`/`actual` in depth

When shared code needs something a platform must provide, `commonMain` declares an **`expect`** and each target supplies an **`actual`** (Chapter 25). It works for functions, and also for **classes**, **objects**, **properties**, and — powerfully — **type aliases**:

```kotlin
// commonMain
expect class Uuid() {
    fun asString(): String
}

// jvmMain — actual as a real class
actual class Uuid actual constructor() {
    private val value = java.util.UUID.randomUUID()
    actual fun asString(): String = value.toString()
}
```

The **`actual typealias`** trick lets a platform satisfy an `expect class` by pointing at an *existing* platform type — no wrapper needed:

```kotlin
// commonMain
expect class StringBuilderCompat()

// jvmMain — just alias the JVM's StringBuilder
actual typealias StringBuilderCompat = java.lang.StringBuilder
```

> ⚠️ **Gotcha** — An `actual` must match its `expect` *exactly* (same signatures, same defaults). A mismatch is a compile error per target. Keep `expect` declarations minimal — every one multiplies the work across all targets — and push as much logic as possible into shared `commonMain` code that uses the small `expect` surface.

### 34.3 Sharing real code

The big win is sharing whole *layers*. Because the multiplatform `kotlinx` libraries (coroutines, serialization, `kotlinx-datetime`, Ktor client) run on every target, you can write a complete domain, networking, and persistence layer **once** in `commonMain`:

```kotlin
// commonMain — shared across Android, iOS, backend, web
@Serializable
data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {           // the same port from Chapter 9, now multiplatform
    suspend fun all(): List<Task>
    suspend fun add(title: String): Task
}

class TaskService(private val repo: TaskRepository) {
    suspend fun addValidated(title: String): Task {
        require(title.isNotBlank())
        return repo.add(title.trim())
    }
}
```

That `TaskService`, `Task`, coroutine logic, and JSON serialization compile identically for an Android app, an iOS app, and a Ktor backend — the same tested code, no duplication. Only the *outermost* bits (platform storage, UI) differ.

### 34.4 iOS interop and Compose Multiplatform

For **iOS**, Kotlin/Native compiles `commonMain` + `iosMain` into a framework that Swift/Objective-C consume like any native library — so a SwiftUI app calls your shared `TaskService` directly. Kotlin/Native interoperates with C and Objective-C APIs (via `platform.*` packages); the modern memory model unifies concurrency across platforms (older Kotlin/Native had stricter rules, now relaxed).

**Compose Multiplatform** extends Jetpack Compose (Chapter 22) beyond Android to **iOS, desktop, and web** — so you can share not just logic but the *UI* itself:

```kotlin
// commonMain — one @Composable for Android, iOS, and desktop
@Composable
fun TaskList(tasks: List<Task>) {
    Column {
        tasks.forEach { Text(it.title) }
    }
}
```

> ⚙️ **Under the hood** — There is no shared runtime. Each target *compiles* `commonMain` + its `actual`s to that platform's native artifact: JVM bytecode (Android/backend), a native binary via LLVM (iOS/desktop), or JavaScript/Wasm (web). Sharing is resolved entirely at **compile time**, so shared code runs at full native speed on each platform with no bridge or interpreter — the opposite of "write once, run slow everywhere."

### 34.5 Swift, Objective-C, C, and JavaScript boundaries

An API that is elegant in Kotlin may be awkward or impossible to export. Design the public boundary for its consumer language:

- avoid exposing deeply generic, inline/reified, or Kotlin-specific implementation types;
- prefer stable DTOs, simple sealed outcomes, explicit names, and small facades;
- translate exceptions to documented error/result behavior;
- keep coroutine scopes owned and cancellable rather than exporting fire-and-forget work;
- map nullability intentionally and test generated Swift/Objective-C/TypeScript signatures.

Kotlin 2.4's **Swift export** is Alpha and can map `suspend` to Swift `async` and Flow to `AsyncSequence`, which improves ergonomics but still requires version/feature-status review. Treat Alpha export configuration as an integration surface protected by Swift-side compile tests.

For C libraries, `cinterop` consumes headers/`.def` configuration and produces Kotlin bindings. Native pointers, pinning, allocation ownership, callbacks, and thread rules remain the underlying C contract; Kotlin syntax does not make unsafe ownership safe. Wrap raw bindings in a narrow `nativeMain` adapter and expose domain types to `commonMain`.

For JS/TypeScript, `@JsExport` exposes supported declarations and generated `.d.ts` files become part of your API. Use `external` declarations to model JavaScript libraries, prefer npm/typed wrappers over scattered `js()` strings, and test both module system and browser/Node runtime you publish for. Wasm and JS are distinct targets with different interoperability and deployment trade-offs.

> ⚠️ **Gotcha — ABI is per target.** A harmless-looking Kotlin change can alter a JVM signature, Objective-C header, Swift export, TypeScript declaration, Native symbol, or serialized schema differently. Compatibility checks must inspect every artifact consumers compile/link against.

### 34.6 Multiplatform testing, publication, and CI

Put pure domain tests in `commonTest`; they compile and execute on each configured target, catching target-specific runtime differences. Put platform integration tests in `jvmTest`, `androidInstrumentedTest`, `iosSimulatorArm64Test`, `jsTest`, and so on. A test merely compiling for a target is not the same as running there.

CI should:

1. run common/JVM/JS/Wasm tests on ordinary workers;
2. run Apple compilation, simulator tests, framework/Swift-consumer tests on macOS;
3. build Android variants and instrumentation/device tests where needed;
4. verify generated metadata, source artifacts, POMs, signatures, and API dumps;
5. publish only from an immutable tag after all target jobs succeed.

A multiplatform library publishes a root metadata artifact plus target variants. Consumers select the appropriate variant through Gradle metadata. Configure group, artifact, version, licenses, sources, documentation, repository credentials, and signing once; never place credentials in the build script. Test publication first against `mavenLocal()` or a temporary repository with a separate consumer project.

Choose the minimum supported versions—Kotlin, Gradle, Android API, iOS/macOS, JavaScript environment—as an explicit product contract. Adding a target increases build time, CI infrastructure, compatibility surface, and support burden; add one because a real consumer needs it, not to fill a target checklist.

---

### Summary

- **KMP** compiles shared code to JVM, native (iOS/desktop), JS, and Wasm **targets**, organized in **source sets** (`commonMain` + per-platform), with intermediate sets forming a **hierarchy**.
- **`expect`/`actual`** bridges to platform specifics — for functions, classes, objects, properties, and **`actual typealias`** (aliasing an existing platform type). Keep the `expect` surface small.
- The multiplatform **`kotlinx`** libraries let you share whole layers — domain, coroutines, serialization, networking — writing them once in `commonMain`.
- **iOS** consumes a Kotlin/Native framework from Swift; **Compose Multiplatform** shares UI across Android/iOS/desktop/web.
- Sharing is **compile-time** — each target compiles to its native format, so shared code runs at full speed with no runtime bridge.
- Exported Swift/C/JS APIs are separate compatibility surfaces. Run common and platform integration tests on real target environments and verify every published variant before release.

### Self-check quiz

1. What goes in `commonMain` vs a platform source set?
   <details><summary>Answer</summary>`commonMain` holds shared code that compiles to every target and uses no platform-specific APIs; platform source sets (`jvmMain`, `iosMain`, …) hold code using that platform's APIs, including `actual` implementations.</details>
2. What can `expect`/`actual` apply to besides functions?
   <details><summary>Answer</summary>Classes, objects, properties, and constructors — plus `actual typealias`, which satisfies an `expect class` by aliasing an existing platform type.</details>
3. Why can you share coroutines and serialization code across platforms?
   <details><summary>Answer</summary>The `kotlinx` libraries (coroutines, serialization, datetime) are themselves multiplatform, so code using them compiles for every target.</details>
4. How does KMP avoid a runtime performance cost?
   <details><summary>Answer</summary>Sharing is resolved at compile time — each target compiles the common code plus its actuals to that platform's native format (bytecode/native/JS), so there's no runtime bridge or interpreter.</details>

### Exercises

**Exercise 34.1 — `expect`/`actual` platform tag (guided).** Declare an `expect fun platform(): String` and give it a JVM `actual` and an (illustrative) iOS `actual`.

<details><summary>Show solution</summary>

```kotlin
// commonMain
expect fun platform(): String
fun describe() = "Running on ${platform()}"

// jvmMain
actual fun platform(): String = "JVM ${System.getProperty("java.version")}"

// iosMain
actual fun platform(): String = "iOS"
```

**Why this works:** `commonMain` declares the capability and builds shared logic (`describe`) on top of it; each target provides its own `actual`. The shared `describe()` compiles everywhere, calling whichever `platform()` the target supplies.

</details>

**Exercise 34.2 — Where does it go?** For each, name the source set: (a) `data class Task` with `@Serializable`; (b) reading an iOS `NSUserDefaults`; (c) a `TaskRepository` interface; (d) a JDBC-based repository.

<details><summary>Show answer</summary>

- (a) `commonMain` — pure data, multiplatform serialization.
- (b) `iosMain` — iOS-only API.
- (c) `commonMain` — a pure interface.
- (d) `jvmMain` (or `androidMain`) — JDBC is JVM-only.

**Why:** pure logic and interfaces go in `commonMain`; anything touching a platform's APIs goes in that platform's source set.

</details>

### Chapter project: a multiplatform core

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — the multiplatform capstone. **Builds on:** Ch.1–34 (especially Ch.25's KMP seed and Ch.33's clean layers). We share the whole domain across JVM and iOS, with platform storage via `expect`/`actual`.

**Goal.** Put the domain, use cases, and serialization in `commonMain`; provide platform-specific storage.

<details><summary>Show structure + commentary</summary>

```kotlin
// ================= commonMain (shared everywhere) =================
import kotlinx.serialization.*
import kotlinx.serialization.json.*

@Serializable
data class Task(val id: Int, val title: String, val done: Boolean = false)

interface TaskRepository {
    suspend fun all(): List<Task>
    suspend fun add(title: String): Task
}

class TaskService(private val repo: TaskRepository) {   // pure use-case logic
    suspend fun addValidated(title: String): Task {
        require(title.isNotBlank()) { "Title must not be blank" }
        return repo.add(title.trim())
    }
}

// Shared JSON persistence helpers — same on every platform
fun encodeTasks(tasks: List<Task>): String = Json.encodeToString(tasks)
fun decodeTasks(text: String): List<Task> = Json.decodeFromString(text)

// The one platform seam: where do we read/write the JSON string?
expect object TaskStore {
    fun save(json: String)
    fun load(): String
}

// ================= jvmMain =================
actual object TaskStore {
    private val file = java.io.File("tasks.json")
    actual fun save(json: String) = file.writeText(json)
    actual fun load(): String = if (file.exists()) file.readText() else "[]"
}

// ================= iosMain (illustrative) =================
// actual object TaskStore {
//     actual fun save(json: String) =
//         NSUserDefaults.standardUserDefaults.setObject(json, "tasks")
//     actual fun load(): String =
//         NSUserDefaults.standardUserDefaults.stringForKey("tasks") ?: "[]"
// }
```

**Commentary.**
- **Everything meaningful is shared.** `Task`, `TaskRepository`, `TaskService`, and the JSON encode/decode helpers live in `commonMain`; the same source and business semantics compile into target-specific binaries for Android, iOS, and a backend.
- The **only** platform seam is `expect object TaskStore` — "give me somewhere to persist a JSON string." The JVM `actual` uses a `File`; the iOS `actual` (sketched) uses `NSUserDefaults`. The shared code doesn't care which — the Chapter 33 dependency rule, now spanning *operating systems*.
- `@Serializable` works across targets because kotlinx.serialization is multiplatform and compile-time (Chapters 30–31) — no per-platform serializer code.
- With **Compose Multiplatform** you'd add a shared `@Composable TaskScreen` (Chapter 22's UI, now cross-platform), leaving only tiny platform entry points. The Task Manager — one core, many faces — is complete: CLI, backend, Android, iOS, from a single shared heart.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **KMP** | Kotlin Multiplatform — sharing code across JVM/native/JS/Wasm. |
| **Target** | A platform KMP compiles to (`jvm()`, `iosArm64()`, `js()`, …). |
| **Source set** | A code folder for a scope (`commonMain`, `jvmMain`, `iosMain`). |
| **Hierarchical source sets** | Intermediate shared sets (e.g. `appleMain`). |
| **`expect` / `actual`** | Common declaration / per-platform implementation. |
| **`actual typealias`** | Satisfying an `expect class` by aliasing a platform type. |
| **Compose Multiplatform** | Compose UI shared across Android/iOS/desktop/web. |
| **Swift export / `@JsExport`** | Exporting Kotlin APIs to Swift / JavaScript-TypeScript consumers. |
| **Publication variant** | The target-specific artifact selected from a multiplatform publication. |

### What's next

You can share a core across every platform. **[Ch.35 — Designing Libraries & Public APIs](#chapter-35--designing-libraries--public-apis)** teaches how to package such a core *as a library* others depend on — explicit API mode, binary compatibility, deprecation, and documentation.

[↑ back to top](#chapter-34--kotlin-multiplatform-in-depth)


---

## Chapter 35 — Designing Libraries & Public APIs

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — Extensions](#chapter-11--extension-functions--properties), [Ch.18 — Java interop](#chapter-18--kotlin--java-interoperability), [Ch.23 — Best Practices](#chapter-23--best-practices--idioms)

**Learning objectives** — after this chapter you will be able to:

- Apply API design principles for libraries others depend on.
- Control your public surface with visibility and explicit API mode.
- Preserve binary compatibility and deprecate gracefully.
- Document with KDoc and mark experimental APIs.
- Generate documentation, validate API/ABI, sign artifacts, and test a release as a real consumer.

**In this chapter**

- [35.1 API design principles](#351-api-design-principles)
- [35.2 Controlling the public surface](#352-controlling-the-public-surface)
- [35.3 Binary compatibility](#353-binary-compatibility)
- [35.4 Deprecation, opt-in, and KDoc](#354-deprecation-opt-in-and-kdoc)
- [35.5 Documentation, publication, and artifact integrity](#355-documentation-publication-and-artifact-integrity)
- [35.6 Compatibility is more than a method signature](#356-compatibility-is-more-than-a-method-signature)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-clean-public-api)· Glossary · What's next

---

### 35.1 API design principles

Writing a *library* — code others depend on — raises the stakes. Your users can't easily change your code, and every public element is a promise you must keep. Good API design follows a few principles:

- **Least surprise** — behave the way a reasonable user expects; follow Kotlin conventions (Chapter 23).
- **Small surface** — expose the minimum; every public class/function is something you must maintain and can't remove without breaking users. Hide implementation details.
- **Immutability** — prefer immutable types and read-only returns (Chapter 8); they're safer to hand out.
- **Meaningful types** — use nullable, sealed results, and value classes to make illegal states unrepresentable, so misuse is a *compile* error.
- **Discoverability** — organize for autocompletion; extension functions (Chapter 11) and DSLs (Chapter 17) create fluent, explorable APIs.

### 35.2 Controlling the public surface

By default, everything is `public`. For a library, be deliberate. Use **`internal`** to make declarations visible within your module but invisible to consumers — the workhorse for hiding implementation:

```kotlin
class TaskParser {
    fun parse(text: String): List<Task> = internalParse(text)   // public API

    internal fun internalParse(text: String): List<Task> =
        text.lineSequence()
            .filter { it.isNotBlank() }
            .mapIndexed { index, title -> Task(index + 1, title.trim(), done = false) }
            .toList()
}
```

**Explicit API mode** enforces discipline: enable it and the compiler *requires* explicit visibility modifiers and explicit return types on every public declaration, so nothing leaks into your API by accident:

```kotlin
// build.gradle.kts
kotlin {
    explicitApi()   // now public declarations MUST state visibility + return type
}
```

For members that must be `internal` but are used from **`inline`** functions (which are compiled into the *caller's* code, Chapter 25), use **`@PublishedApi internal`** — it stays out of the documented API but is technically accessible where inlining requires it.

> 💡 **Idiom** — Turn on `explicitApi()` for any library. It costs a little verbosity but prevents the single most common API mistake: a helper you meant to keep private silently becoming part of your public contract (which you then can't remove without breaking users).

### 35.3 Binary compatibility

There are two kinds of compatibility, and libraries must respect both:

- **Source compatibility** — existing *source* code still compiles against the new version.
- **Binary compatibility** — existing *compiled* code (a `.jar` built against the old version) still links against the new version *without recompiling*.

Binary compatibility is stricter and easy to break unknowingly. Adding a parameter (even with a default), changing a return type, or renaming a method all break it. **Semantic versioning** communicates this: breaking changes bump the *major* version; compatible additions bump *minor*; fixes bump *patch*.

> ⚠️ **Gotcha — default arguments and binary compatibility.** Adding a parameter *with a default* is *source*-compatible (old call sites still compile) but **not** *binary*-compatible: the method signature in the bytecode changed, so pre-compiled callers fail to link. Libraries use tools like **binary-compatibility-validator** to catch such breaks. Also recall (Chapter 18) that default args need `@JvmOverloads` for Java callers to see the convenient overloads.

> ⚙️ **Under the hood** — Binary compatibility is about **bytecode signatures**: a call site compiles to a reference to a specific method descriptor (name + parameter types + return type). Change any of those and the old reference no longer resolves at link time — an `NoSuchMethodError` at runtime for a consumer who didn't recompile. This is why "just add an optional parameter" is a bigger deal for a *published library* than for app code you compile all at once.

### 35.4 Deprecation, opt-in, and KDoc

When you must evolve an API, **deprecate** rather than delete — give users a migration path. `@Deprecated` warns (or errors), and `ReplaceWith` lets IDEs auto-migrate:

```kotlin
class TaskBook {
    private val tasks = mutableListOf<String>()

    @Deprecated(
        message = "Renamed for clarity",
        replaceWith = ReplaceWith("addTask(title)"),
        level = DeprecationLevel.WARNING     // WARNING → ERROR → HIDDEN over releases
    )
    fun add(title: String) = addTask(title)

    fun addTask(title: String) { tasks.add(title) }
}
```

Escalate `DeprecationLevel` across releases (`WARNING` → `ERROR` → `HIDDEN`) so users have time to migrate before removal.

For APIs that aren't stable yet, mark them **experimental** with `@RequiresOptIn`, forcing users to *acknowledge* the risk with `@OptIn`:

```kotlin
@RequiresOptIn(message = "This API is experimental and may change.")
annotation class ExperimentalTaskApi

@ExperimentalTaskApi
fun batchImport(data: String) { /* ... */ }

// A consumer must opt in explicitly:
@OptIn(ExperimentalTaskApi::class)
fun useIt() = batchImport("...")
```

Finally, **document with KDoc** (Kotlin's `/** */` doc comments, rendered by Dokka):

```kotlin
class TaskBook {
    private var nextId = 1

    /**
     * Adds a task to the book.
     *
     * @param title the task's title; must not be blank.
     * @return the created [Task].
     * @throws IllegalArgumentException if [title] is blank.
     */
    fun addTask(title: String): Task {
        require(title.isNotBlank()) { "title must not be blank" }
        return Task(nextId++, title.trim(), done = false)
    }
}
```

> 💡 **Idiom** — Document the *contract*, not the obvious. `@param`, `@return`, `@throws`, and links (`[Task]`) tell users what they can rely on and what can go wrong — the things they *can't* infer from the signature. Skip comments that just restate the code.

### 35.5 Documentation, publication, and artifact integrity

Use **Dokka** to generate HTML/Javadoc-style API documentation from KDoc, and publish source/documentation artifacts beside binaries. A useful library release also contains:

- coordinates (`group:artifact:version`) that remain stable;
- module metadata/POM with accurate dependencies and licenses;
- signed artifacts and checksums where the repository requires them;
- release notes and a migration guide for behavioral changes;
- an API dump reviewed in pull requests;
- reproducible CI that publishes only immutable tags.

Representative Gradle shape:

```kotlin
plugins {
    `maven-publish`
    signing
    id("org.jetbrains.dokka")
}

publishing {
    publications.withType<MavenPublication>().configureEach {
        pom {
            name.set("Task Format")
            description.set("Stable task interchange types and codecs")
            licenses { license { name.set("Apache-2.0") } }
            scm { url.set("https://example.com/task-format") }
        }
    }
}

signing { sign(publishing.publications) }
```

Credentials and private signing material come from environment variables/Gradle credentials providers and CI secrets, never version control. Test publication into a temporary repository, then compile/run a **separate consumer fixture** against the produced artifact. That catches missing runtime dependencies, bad metadata, wrong visibility, absent service files, and code that worked only because the library's own build leaked a dependency.

> ⚠️ **Gotcha** — `mavenLocal()` is stateful and can hide publication mistakes through stale artifacts. Use a unique version, clear evidence of which repository resolved it, and prefer an isolated temporary Maven directory in automated tests.

### 35.6 Compatibility is more than a method signature

Track several contracts independently:

- **source compatibility**: old source still compiles;
- **binary/ABI compatibility**: old binaries still link;
- **behavioral compatibility**: semantics, ordering, exceptions, performance bounds, and thread safety remain within contract;
- **serialization/wire compatibility**: old persisted/network data still decodes and mixed versions interoperate;
- **platform compatibility**: supported Java/Android/iOS/JS/Kotlin/Gradle ranges remain true.

Automate what tools can prove: public API dumps, JVM binary validation, generated Swift/TypeScript surface snapshots, serialized golden files, cross-version tests, and dependency convergence. Human review still decides semantic changes.

Kotlin-specific hazards include public `inline` functions embedding implementation into consumer binaries, `const val` values copied at compile time, default-argument synthetic methods, sealed hierarchy exhaustiveness, data-class generated members, changed variance/nullability, and compiler/plugin metadata requirements. A type being `public` accidentally can be more expensive than its implementation.

Use semantic versioning as communication, not permission to break carelessly. A major release still needs deprecation runway where possible, a precise migration guide, coexistence strategy for multi-module ecosystems, and tested downgrade/rollback implications.

---

### Summary

- Library API design: **least surprise**, a **small surface**, **immutability**, **meaningful types** (make illegal states unrepresentable), and **discoverability**.
- Control the surface with **`internal`** (module-only) and **`explicitApi()`** (require explicit visibility + return types); use **`@PublishedApi internal`** for `inline`-accessible internals.
- Respect **source** *and* **binary** compatibility; adding even a defaulted parameter breaks binary compat. Communicate with **semantic versioning**; validate with tooling.
- Evolve with **`@Deprecated`** (+ `ReplaceWith`, escalating `DeprecationLevel`); gate unstable APIs with **`@RequiresOptIn`**/`@OptIn`; document contracts with **KDoc**.
- Generate docs with **Dokka**, verify API/ABI and wire formats, sign/publish from CI, and test the exact artifact in a clean consumer. Compatibility includes behavior, data, tooling, and every target—not just source signatures.

### Self-check quiz

1. What does `explicitApi()` enforce, and why enable it for a library?
   <details><summary>Answer</summary>It requires explicit visibility modifiers and return types on all public declarations, preventing helpers from accidentally becoming part of the public API (which you then can't remove without breaking users).</details>
2. Why is adding a parameter *with a default* not binary-compatible?
   <details><summary>Answer</summary>It changes the method's bytecode signature, so pre-compiled callers referencing the old signature fail to link — even though new source still compiles.</details>
3. How should you remove an API without breaking users abruptly?
   <details><summary>Answer</summary>Deprecate it with `@Deprecated` (+ `ReplaceWith` for auto-migration), escalating `DeprecationLevel` (`WARNING` → `ERROR` → `HIDDEN`) across releases before finally removing it.</details>
4. What does `@RequiresOptIn` accomplish?
   <details><summary>Answer</summary>It marks an API as experimental/unstable, forcing consumers to explicitly `@OptIn` — acknowledging it may change — before using it.</details>

### Exercises

**Exercise 35.1 — Deprecate gracefully (guided).** Rename `size()` to `count()` on a class while keeping `size()` working with a deprecation and auto-migration hint.

<details><summary>Show solution</summary>

```kotlin
class Bag {
    private val items = mutableListOf<String>()
    fun add(item: String) { items.add(item) }

    @Deprecated("Renamed to count()", ReplaceWith("count()"))
    fun size(): Int = count()

    fun count(): Int = items.size
}

fun main() {
    val bag = Bag().apply { add("a"); add("b") }
    @Suppress("DEPRECATION")
    println(bag.size())    // → 2  (works, but warns)
    println(bag.count())   // → 2
}
```

**Why this works:** `size()` still functions (delegating to `count()`), so existing code keeps running, but the `@Deprecated` warns users and `ReplaceWith("count()")` lets the IDE auto-migrate call sites. Later you'd raise the level to `ERROR`, then remove it.

</details>

**Exercise 35.2 — Gate an experimental API.** Mark a `fun betaFeature()` as experimental so callers must opt in.

<details><summary>Show solution</summary>

```kotlin
@RequiresOptIn(message = "Beta: may change without notice.")
annotation class Beta

@Beta
fun betaFeature() = "beta result"

@OptIn(Beta::class)
fun main() {
    println(betaFeature())   // → beta result  (compiles only because of @OptIn)
}
```

**Why this works:** `@RequiresOptIn` on the `Beta` annotation means any use of `@Beta`-marked code is a compile error *unless* the caller acknowledges it with `@OptIn(Beta::class)` — a deliberate, visible opt-in to instability.

</details>

### Chapter project: a clean public API

> 🛠️ **Chapter Project** — **Standalone mini-project** (library design, not the Task Manager app). **Builds on:** Ch.1–35. We design the public API of a small "task-format" library — the surface others would depend on.

**Goal.** A well-designed public API: a small surface, hidden internals, KDoc, a deprecation, and an experimental function.

<details><summary>Show solution + commentary</summary>

```kotlin
// Enable in build.gradle.kts:  kotlin { explicitApi() }

/**
 * Parses and formats tasks in the compact "task-format" (`id|title|done`).
 *
 * Example:
 * ```
 * val tasks = TaskFormat.parse("1|Buy milk|false")
 * ```
 */
public object TaskFormat {

    /**
     * Parses [text] (one task per line, `id|title|done`) into [Task]s.
     *
     * @param text the encoded tasks, newline-separated.
     * @return the parsed tasks; empty if [text] is blank.
     * @throws IllegalArgumentException if a line is malformed.
     */
    public fun parse(text: String): List<Task> =
        text.lineSequence().filter { it.isNotBlank() }.map { parseLine(it) }.toList()

    /** Formats [tasks] back into the compact format. */
    public fun format(tasks: List<Task>): String =
        tasks.joinToString("\n") { "${it.id}|${it.title}|${it.done}" }

    @Deprecated("Use parse() instead", ReplaceWith("parse(text)"))
    public fun read(text: String): List<Task> = parse(text)

    @ExperimentalTaskFormat
    public fun parseLenient(text: String): List<Task> =
        text.lineSequence().mapNotNull { runCatching { parseLine(it) }.getOrNull() }.toList()

    // Hidden implementation detail — not part of the public API:
    private fun parseLine(line: String): Task {
        val parts = line.split("|")
        require(parts.size == 3) { "Malformed line: $line" }
        return Task(parts[0].toInt(), parts[1], parts[2].toBoolean())
    }
}

/** Marks unstable [TaskFormat] APIs that may change. */
@RequiresOptIn(message = "Lenient parsing is experimental.")
public annotation class ExperimentalTaskFormat

public data class Task(val id: Int, val title: String, val done: Boolean)

fun main() {
    val tasks = TaskFormat.parse("1|Buy milk|false\n2|Write docs|true")
    println(tasks)                        // → [Task(id=1, ...), Task(id=2, ...)]
    println(TaskFormat.format(tasks))     // → 1|Buy milk|false\n2|Write docs|true
}
```

Output:

```text
[Task(id=1, title=Buy milk, done=false), Task(id=2, title=Write docs, done=true)]
1|Buy milk|false
2|Write docs|true
```

**Commentary.**
- The **public surface is tiny and intentional**: `TaskFormat.parse`/`format`, the `Task` type, and one opt-in experimental function. `parseLine` is `private` — an implementation detail users can't depend on, so we're free to change it. With `explicitApi()` on, the compiler would *force* every public member to declare `public` and its return type, catching accidental leaks.
- **KDoc documents the contract** — what `parse` does, its parameter, return, and the `@throws` it can raise, with a `[Task]` link and a usage example. That's what users can't infer from signatures alone.
- `read()` is **deprecated** with a `ReplaceWith` so existing users get a warning and an auto-fix, not a broken build.
- `parseLenient` is gated behind **`@RequiresOptIn`** — it's experimental, so callers must `@OptIn(ExperimentalTaskFormat::class)` to use it, acknowledging it may change. This lets you ship and iterate on new APIs without committing to their stability.
- This is how a real, well-behaved Kotlin library presents itself: minimal, documented, evolvable, and honest about what's stable.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Public API** | The surface consumers depend on (everything not hidden). |
| **`internal`** | Visible within the module, hidden from consumers. |
| **`explicitApi()`** | Compiler mode requiring explicit visibility + return types. |
| **`@PublishedApi internal`** | An internal member accessible from `inline` functions. |
| **Source / binary compatibility** | Old source still compiles / old compiled code still links. |
| **Semantic versioning** | major.minor.patch signalling breaking/additive/fix changes. |
| **`@Deprecated` / `ReplaceWith`** | Marks an API obsolete / provides auto-migration. |
| **`@RequiresOptIn` / `@OptIn`** | Marks/acknowledges an unstable experimental API. |
| **KDoc** | Kotlin's documentation comments (`/** */`, rendered by Dokka). |
| **Dokka** | Documentation generator for Kotlin source and multiplatform APIs. |
| **ABI** | The binary-level surface against which compiled consumers link. |
| **Consumer fixture** | A separate project that verifies the published artifact as users receive it. |

### What's next

Your library is well-designed — now prove it works. **[Ch.36 — Advanced Testing](#chapter-36--advanced-testing)**, the final chapter, covers property-based testing, flow testing with Turbine, and integration tests with Testcontainers, culminating in a full test suite for everything you've built.

[↑ back to top](#chapter-35--designing-libraries--public-apis)


---

## Chapter 36 — Advanced Testing

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.24 — Testing](#chapter-24--testing-in-kotlin), [Ch.26 — Flow](#chapter-26--flow-in-depth), [Ch.33 — Architecture](#chapter-33--architecture--dependency-injection)

**Learning objectives** — after this chapter you will be able to:

- Write property-based tests that explore the input space.
- Test flows deterministically with Turbine.
- Write integration tests for Ktor and databases.
- Judge test *value* and avoid flaky, low-value tests.
- Add contract, mutation, concurrency, migration, and release-artifact tests to a CI strategy.

**In this chapter**

- [36.1 Kotest and property-based testing](#361-kotest-and-property-based-testing)
- [36.2 Testing flows with Turbine](#362-testing-flows-with-turbine)
- [36.3 Integration testing](#363-integration-testing)
- [36.4 Test quality and trust](#364-test-quality-and-trust)
- [36.5 Contract, mutation, concurrency, and CI](#365-contract-mutation-concurrency-and-ci)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-full-test-suite)· Glossary · What's next

---

### 36.1 Kotest and property-based testing

Chapter 24 covered example-based tests: pick specific inputs, assert specific outputs. **Property-based testing** flips this — you assert a *property* that should hold for *all* inputs, and the framework generates hundreds of random cases (including nasty edge cases) to try to falsify it.

**Kotest** is a popular Kotlin test framework with expressive spec styles and matchers, and built-in property testing:

```kotlin
import io.kotest.core.spec.style.StringSpec
import io.kotest.matchers.shouldBe
import io.kotest.property.checkAll

class StringPropertiesTest : StringSpec({
    "reversing a string twice yields the original" {
        checkAll<String> { s ->
            s.reversed().reversed() shouldBe s     // must hold for ALL strings
        }
    }

    "encoding then decoding is identity" {
        checkAll<Int> { n ->
            n.toString().toInt() shouldBe n
        }
    }
})
```

`checkAll<String> { … }` runs the block on many generated strings — empty, unicode, huge — far more thoroughly than you'd write by hand. When it finds a failure, it **shrinks** it: it repeatedly simplifies the failing input to the *smallest* case that still fails (e.g. from a 200-char string to `"a"`), so you get a minimal reproduction instead of random noise.

> 💡 **Idiom** — Property tests shine for **invariants**: round-trips (encode/decode, serialize/deserialize), commutativity/associativity, "output is always sorted," "count never negative." Example tests still matter for specific known cases and regressions; use *both* — properties for general laws, examples for concrete scenarios.

### 36.2 Testing flows with Turbine

Testing a `Flow`/`StateFlow` (Chapter 26) by collecting into a list is awkward and racy. **Turbine** makes it clean: `flow.test { }` lets you `awaitItem()` one emission at a time, with clear assertions and timeouts.

```kotlin
import app.cash.turbine.test
import kotlinx.coroutines.test.runTest
import kotlin.test.*

class CounterViewModelTest {
    @Test
    fun `increment updates state`() = runTest {
        val vm = CounterViewModel()          // exposes count: StateFlow<Int>

        vm.count.test {
            assertEquals(0, awaitItem())     // initial value
            vm.increment()
            assertEquals(1, awaitItem())     // after increment
            cancelAndIgnoreRemainingEvents()
        }
    }
}
```

Combined with **`runTest`** (Chapter 24) and its virtual time, you can test time-based flow operators (`debounce`, delays) deterministically — advancing the virtual clock with `advanceTimeBy(...)` instead of really waiting.

### 36.3 Integration testing

Unit tests isolate a class; **integration tests** verify pieces work *together* — a real route, a real database.

**Ktor** provides `testApplication` (Chapter 20), which runs your server in-memory (no real network) with a preconfigured client:

```kotlin
import io.ktor.client.request.*
import io.ktor.client.statement.*
import io.ktor.http.*
import io.ktor.server.testing.*
import kotlin.test.*

class ApiTest {
    @Test
    fun `GET tasks returns 200`() = testApplication {
        application { module() }                  // your Ktor module
        val response = client.get("/tasks")
        assertEquals(HttpStatusCode.OK, response.status)
    }
}
```

For databases, **Testcontainers** spins up a *real* database in a Docker container for the test, so you test against actual PostgreSQL — not an in-memory substitute that behaves differently:

```kotlin
import org.testcontainers.containers.PostgreSQLContainer
import org.testcontainers.junit.jupiter.*
import org.jetbrains.exposed.v1.jdbc.Database
import org.jetbrains.exposed.v1.jdbc.*
import org.jetbrains.exposed.v1.jdbc.transactions.transaction
import kotlin.test.*

@Testcontainers
class RepositoryIntegrationTest {
    companion object {
        @Container
        val postgres = PostgreSQLContainer<Nothing>("postgres:16")
    }

    @Test
    fun `saves and loads a task`() {
        val db = Database.connect(
            url = postgres.jdbcUrl,
            driver = "org.postgresql.Driver",
            user = postgres.username,
            password = postgres.password,
        )

        transaction(db) {
            SchemaUtils.create(Tasks)
            Tasks.insert { it[title] = "real PostgreSQL" }
            val saved = Tasks.selectAll().single()
            assertEquals("real PostgreSQL", saved[Tasks.title])
            assertFalse(saved[Tasks.done])
        }
    }
}
```

> 💡 **Idiom — the testing pyramid.** Have *many* fast unit tests (Chapter 24), *fewer* integration tests, and *few* end-to-end tests. Unit tests catch most bugs cheaply; integration tests catch wiring/DB/serialization issues; E2E tests verify critical user journeys. Inverting the pyramid (mostly slow E2E tests) yields slow, flaky suites that no one trusts.

### 36.4 Test quality and trust

Tests are only worth having if you *trust* them. Two threats:

**Flakiness** — a test that passes and fails nondeterministically. Causes: real time/`delay` (use virtual time, `runTest`), test order dependence or shared mutable state (isolate state per test), real network/threads (mock or containerize), and reliance on `System.currentTimeMillis()`/randomness (inject a `Clock`/seed). A flaky test is worse than no test — it trains people to ignore red.

**Low value** — tests that execute code but prove little: asserting getters return what you set, over-`verify`ing internal calls, or testing the framework rather than your logic. A good test can *fail* for a real bug; if you can't imagine a bug it would catch, delete it.

> ⚠️ **Gotcha — test behaviour, not implementation (again).** The single biggest cause of brittle suites is coupling tests to *how* code works rather than *what* it does. Assert on observable outcomes (return values, emitted state, HTTP responses), inject dependencies so you control inputs, and reserve interaction checks for genuinely important effects. Tests coupled to internals break on every refactor — punishing exactly the cleanup you want to encourage.

### 36.5 Contract, mutation, concurrency, and CI

The pyramid is a cost model, not a law about shapes. Add tests at the cheapest boundary that can detect each real risk:

- **contract tests** run the same repository/API expectations against every implementation;
- **consumer-driven contracts** verify independently deployed clients/providers without requiring every service in one fragile environment;
- **migration tests** apply all migrations to an empty database and upgrade representative old snapshots;
- **mutation tests** deliberately change conditions/returns and report tests that still pass, exposing assertions that execute code without proving behavior;
- **concurrency tests** repeat schedules or use model-checking tools such as Lincheck for linearizable data structures;
- **release-fixture tests** consume the actual published JAR/KMP variants, not project classes from the same build.

A reusable repository contract prevents the in-memory fake from drifting away from PostgreSQL semantics:

```kotlin
abstract class TaskRepositoryContract {
    protected abstract fun repository(): TaskRepository
    protected abstract fun resetStorage()

    @BeforeEach fun reset() = resetStorage()

    @Test fun `new task is observable by id`() = runTest {
        val repo = repository()
        val created = repo.add("contract")
        assertEquals(created, repo.find(created.id))
    }

    @Test fun `duplicate idempotency key creates once`() = runTest {
        val repo = repository()
        val first = repo.add("once", idempotencyKey = "k-1")
        val second = repo.add("once", idempotencyKey = "k-1")
        assertEquals(first.id, second.id)
        assertEquals(1, repo.all().size)
    }
}

class InMemoryRepositoryContract : TaskRepositoryContract() { /* factory + reset */ }
class PostgresRepositoryContract : TaskRepositoryContract() { /* Testcontainer + migrations */ }
```

CI layers fast feedback without hiding failures:

1. formatting/static analysis and unit/property tests;
2. build plus integration/contract/migration tests with real dependencies;
3. platform/device and end-to-end smoke tests;
4. API/ABI, dependency, security, and publication-fixture checks;
5. publish reports, seeds, shrunk counterexamples, logs, and container diagnostics on failure.

Quarantine is a short, owned repair state—not a trash bin. Record flaky-test frequency, owner, issue, and deadline; fix or delete it. Retrying an entire suite until green converts nondeterminism into false confidence.

> 💡 **Idiom — deterministic randomness.** Property/stress tests should print the random seed and replay it on failure. Run a small stable budget on every commit and a larger varied budget nightly; retain any discovered counterexample as a focused regression test.

---

### Summary

- **Property-based testing** (Kotest's `checkAll`) asserts invariants over many generated inputs and **shrinks** failures to a minimal case — ideal for round-trips and laws. Use it alongside example tests.
- **Turbine** (`flow.test { awaitItem() }`) tests flows deterministically; with **`runTest`** virtual time, even `debounce`/delays are testable.
- **Integration tests** verify pieces together: **Ktor `testApplication`** for routes in-memory, **Testcontainers** for a real database.
- Follow the **testing pyramid**: many unit, fewer integration, few E2E.
- Guard **trust**: eliminate **flakiness** (virtual time, isolated state, injected clocks) and **low-value** tests; **test behaviour, not implementation**.
- Contract, migration, mutation, concurrency, and release-fixture tests cover risks ordinary unit tests cannot. CI should preserve seeds and diagnostics and treat quarantine as temporary repair work.

### Self-check quiz

1. What does property-based testing add over example-based testing?
   <details><summary>Answer</summary>It asserts a property over *many generated inputs* (including edge cases you'd miss) and shrinks any failure to a minimal reproducing case — far broader coverage than hand-picked examples.</details>
2. Why use Turbine instead of collecting a flow into a list in tests?
   <details><summary>Answer</summary>Turbine lets you await and assert emissions one at a time with timeouts, avoiding the raciness and boilerplate of manual collection — clear, deterministic flow tests.</details>
3. When would you use Testcontainers over an in-memory database?
   <details><summary>Answer</summary>When you need to test against the *real* database (e.g. PostgreSQL-specific behavior), since an in-memory substitute (like H2) can behave differently and hide bugs.</details>
4. Why is a flaky test worse than no test?
   <details><summary>Answer</summary>It fails nondeterministically, eroding trust in the suite and training the team to ignore failures — hiding real regressions among the noise.</details>

### Exercises

**Exercise 36.1 — A property (guided).** Write a Kotest property asserting that sorting a list is idempotent (sorting an already-sorted list changes nothing).

<details><summary>Show solution</summary>

```kotlin
import io.kotest.core.spec.style.StringSpec
import io.kotest.matchers.shouldBe
import io.kotest.property.checkAll

class SortPropertiesTest : StringSpec({
    "sorting is idempotent" {
        checkAll<List<Int>> { list ->
            val once = list.sorted()
            once.sorted() shouldBe once     // sorting again changes nothing
        }
    }
})
```

**Why this works:** `checkAll<List<Int>>` generates many random lists; for each, sorting once and then again must yield the same result. If some input broke the property, Kotest would shrink it to a minimal failing list. This one law covers infinitely many cases a few examples couldn't.

</details>

**Exercise 36.2 — Spot the flaky test.** Why might this test be flaky, and how would you fix it?
```kotlin
@Test fun `token expires`() {
    val token = Token(createdAt = System.currentTimeMillis())
    Thread.sleep(1000)
    assertTrue(token.isExpired(ttlMillis = 500))
}
```

<details><summary>Show answer</summary>

**Why flaky/bad:** it depends on real wall-clock time (`System.currentTimeMillis()` + `Thread.sleep`) — slow (1s per run), and vulnerable to timing/GC pauses. **Fix:** inject a clock so time is controllable:

```kotlin
class Token(private val createdAt: Long, private val clock: () -> Long) {
    fun isExpired(ttlMillis: Long) = clock() - createdAt >= ttlMillis
}

@Test fun `token expires after ttl`() {
    val token = Token(createdAt = 0, clock = { 600 })   // "now" = 600
    assertTrue(token.isExpired(ttlMillis = 500))         // 600 - 0 >= 500 → true
}
```

**Why the fix works:** injecting `clock` (dependency injection, Chapter 33) makes time deterministic and instant — no `sleep`, no real clock, no flakiness. The test controls exactly what "now" is.

</details>

### Chapter project: a full test suite

> 🛠️ **Chapter Project** — Advances the running **Task Manager** — the testing capstone. **Builds on:** Ch.1–36. We assemble a layered test suite for the architected Task Manager: property tests for domain logic, Turbine for state, and integration tests for the API and database.

**Goal.** Cover the Task Manager at every layer with the right kind of test.

<details><summary>Show suite outline + commentary</summary>

```kotlin
// ---- (1) UNIT: domain use case with a mocked repository (Chapter 24) ----
class AddTaskUseCaseTest {
    @Test
    fun `rejects a blank title`() {
        val repo = mockk<TaskRepository>()
        val addTask = AddTaskUseCase(repo)
        assertTrue(addTask("   ").isFailure)
        verify(exactly = 0) { repo.add(any()) }
    }
}

// ---- (2) PROPERTY: a domain invariant (Kotest) ----
class TaskFormatPropertiesTest : StringSpec({
    "encode then decode is identity" {
        checkAll<Int, String> { id, rawTitle ->
            val title = rawTitle.replace("|", "").ifBlank { "x" }   // keep it valid
            val task = Task(id, title, false)
            TaskFormat.parse(TaskFormat.format(listOf(task))) shouldBe listOf(task)
        }
    }
})

// ---- (3) FLOW: reactive state with Turbine (Chapter 26) ----
class TaskViewModelTest {
    @Test
    fun `adding a task updates the state`() = runTest {
        val vm = TaskViewModel(InMemoryTaskRepository())
        vm.uiState.test {
            assertEquals(0, awaitItem().tasks.size)   // initial
            vm.add("Write tests")
            assertEquals(1, awaitItem().tasks.size)   // after add
            cancelAndIgnoreRemainingEvents()
        }
    }
}

// ---- (4) INTEGRATION: the Ktor API in-memory (Chapter 20) ----
class TaskApiTest {
    @Test
    fun `POST then GET returns the created task`() = testApplication {
        application { module() }
        client.post("/tasks") {
            contentType(ContentType.Application.Json)
            setBody("""{"id":0,"title":"Ship it"}""")
        }
        val body = client.get("/tasks").bodyAsText()
        assertTrue("Ship it" in body)
    }
}

// ---- (5) INTEGRATION: the repository against a real DB (Testcontainers, Chapter 21) ----
@Testcontainers
class ExposedRepositoryTest {
    companion object {
        @Container val postgres = PostgreSQLContainer<Nothing>("postgres:16")
    }

    private fun connect(container: PostgreSQLContainer<Nothing>): Database = Database.connect(
        url = container.jdbcUrl,
        driver = "org.postgresql.Driver",
        user = container.username,
        password = container.password,
    )

    private fun migrate(db: Database) {
        transaction(db) { SchemaUtils.create(Tasks) } // use Flyway migrations in the assembled app
    }

    @Test
    fun `persists across a reconnect`() {
        val firstDb = connect(postgres)
        migrate(firstDb)
        val firstRepo = ExposedTaskRepository(firstDb)
        val created = firstRepo.add("Survive reconnect")

        val secondDb = connect(postgres) // a distinct Exposed/connection-pool boundary
        val secondRepo = ExposedTaskRepository(secondDb)
        assertEquals(created, secondRepo.findById(created.id))
    }
}
```

**Commentary — the pyramid in practice.**
- **(1) Unit** tests dominate: fast, mocked, one class at a time. `AddTaskUseCase` is tested with a MockK `TaskRepository` (Chapter 24), asserting the *behaviour* (blank → failure, repo untouched).
- **(2) Property** tests cover *laws*: `parse(format(x)) == x` for arbitrary tasks — a single test that would catch a whole class of encoding bugs, with automatic shrinking (note we sanitize inputs to stay within the format's contract).
- **(3) Flow** tests use **Turbine** + `runTest` to verify the `StateFlow` emits the right state after an event — deterministic, no real delays.
- **(4)/(5) Integration** tests are *fewer* but vital: `testApplication` proves the routes, serialization, and status codes actually work end-to-end in-memory; **Testcontainers** proves the Exposed repository works against a *real* PostgreSQL, catching SQL/dialect issues H2 would hide.
- Together these give **trust**: every layer of the Task Manager — the domain we started in Chapter 1, the architecture of Chapter 33, the persistence of Chapter 21, the API of Chapter 20 — is verified by the *right kind* of test. That trust is what lets you refactor fearlessly, which is where this whole journey has been heading.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Property-based testing** | Asserting invariants over many generated inputs. |
| **Kotest** | A Kotlin test framework with spec styles, matchers, and property testing. |
| **Shrinking** | Simplifying a failing input to a minimal reproduction. |
| **Turbine** | A library for testing flows emission-by-emission. |
| **Integration test** | Verifying components working together (routes, DB). |
| **`testApplication`** | Ktor's in-memory server test harness. |
| **Testcontainers** | Runs real services (e.g. PostgreSQL) in Docker for tests. |
| **Testing pyramid** | Many unit, fewer integration, few E2E tests. |
| **Flakiness** | Nondeterministic pass/fail; erodes trust. |
| **Contract test** | A shared behavior suite applied to every implementation of an abstraction. |
| **Mutation testing** | Deliberately changing production code to check whether tests detect it. |
| **Migration test** | Verifies clean install and upgrade paths for persisted schemas/data. |

### What's next

That's the final chapter. You've gone from `println("Hello, Kotlin!")` to designing frameworks, optimizing hot paths, architecting multiplatform systems, and testing them with rigor. The appendices that follow are your quick reference: a **cheat sheet**, a consolidated **glossary**, **further resources**, and the fully **assembled Task Manager** you built across all 36 chapters.

Keep building — the best way to cement mastery is to ship real projects. Welcome to expert Kotlin.

[↑ back to top](#chapter-36--advanced-testing)


---

## Appendix A — Cheat Sheet

A one-page quick reference. Chapter numbers point to the full treatment.

### Declarations

```kotlin
val x = 1                      // read-only (Ch.2)
var y = 2                      // reassignable
val z: Long = 3               // explicit type
fun f(a: Int, b: Int = 0) = a + b        // default arg, single-expression (Ch.5)
fun g(vararg xs: Int) = xs.sum()          // vararg
class C(val name: String, var age: Int)   // primary constructor (Ch.8)
data class P(val x: Int, val y: Int)      // equals/hashCode/toString/copy
```

### Control flow (all expressions) — Ch.4

```kotlin
val m = if (a > b) a else b
val s = when (x) { 0 -> "zero"; in 1..9 -> "small"; is String -> "str"; else -> "?" }
for (i in 1..10 step 2) { }
for (i in 10 downTo 1) { }
while (cond) { }
repeat(3) { println(it) }
```

### Null safety — Ch.7

```kotlin
val a: String? = maybe            // nullable
val len = a?.length ?: 0         // safe call + Elvis
val x = a ?: return              // guard clause
a?.let { use(it) }               // scoped non-null
val s = obj as? String           // safe cast
lateinit var later: Service       // deferred non-null
```

### Collections — Ch.6

```kotlin
listOf(1,2,3); mutableListOf(); setOf(); mapOf("a" to 1)
list.filter { }.map { }.groupBy { }.sumOf { }
list.firstOrNull { }; list.any { }; list.all { }
list.asSequence().filter { }.take(5).toList()   // lazy for large data
```

### Functions & lambdas — Ch.5

```kotlin
val f: (Int) -> Int = { it * 2 }
fun higher(op: (Int, Int) -> Int) = op(1, 2)
higher { a, b -> a + b }          // trailing lambda
```

### Scope functions — Ch.14

```kotlin
obj.apply { prop = 1 }            // configure → obj
obj.also { log(it) }             // side effect → obj
obj.let { transform(it) }        // transform → result
obj.run { compute() }            // result, this
with(obj) { }                     // result, this
```

### Coroutines — Ch.15

```kotlin
suspend fun f() { delay(100) }
runBlocking { }                   // bridge (edges only)
launch { }                        // fire-and-forget
val d = async { }; d.await()      // concurrent + result
coroutineScope { }                // structured
withContext(Dispatchers.IO) { }   // move blocking off-thread
flow { emit(1) }.collect { }      // stream
MutableStateFlow(0)               // observable state
```

### OOP — Ch.8–10

```kotlin
open class Base; class Sub : Base()          // open/override
abstract class A { abstract fun f() }
interface I { fun f(); fun g() = "default" }
sealed interface Result { data class Ok(val v: Int) : Result; object Err : Result }
enum class Color(val hex: Int) { RED(0xFF0000) }
object Singleton { }
companion object { fun create() = ... }
@JvmInline value class Id(val v: Int)
```

## Appendix B — Glossary

A consolidated glossary of key terms (see each chapter's own glossary for the full list).

| Term | Meaning |
|------|---------|
| **`val` / `var`** | Read-only / reassignable name. |
| **Type inference** | Compiler deducing a type so you can omit the annotation. |
| **Nullable type (`T?`)** | A type whose values may be `null`. |
| **Smart cast** | Compiler narrowing a type after a check. |
| **Safe call (`?.`) / Elvis (`?:`)** | Null-yielding call / fallback for null. |
| **`data class`** | Class with generated `equals`/`hashCode`/`toString`/`copy`. |
| **`sealed`** | A closed type hierarchy enabling exhaustive `when`. |
| **Extension function** | A function added to a type from outside. |
| **Generic / variance** | Type-parameterized code / `in`/`out` substitution rules. |
| **`reified`** | An inline type parameter available at runtime. |
| **Delegated property (`by`)** | A property whose accessors are handled by a delegate. |
| **Scope function** | `let`/`run`/`with`/`apply`/`also`. |
| **Coroutine / `suspend`** | Lightweight concurrency / a pausable function. |
| **Structured concurrency** | Children complete within their scope; cancel/fail together. |
| **Dispatcher** | Chooses which thread(s) a coroutine runs on. |
| **`Flow` / `StateFlow`** | Cold stream / hot observable state. |
| **`Result` / `runCatching`** | Failure modeled as a value. |
| **DSL / lambda with receiver** | A type-safe mini-language / `T.() -> R`. |
| **Platform type (`T!`)** | A Java value of unknown nullability. |
| **`inline`** | Copies a function/lambda body into the call site. |
| **Reflection** | Inspecting types at runtime. |
| **KSP** | Compile-time code generation from annotations. |
| **`expect` / `actual`** | Common declaration / per-platform implementation (KMP). |
| **Boxing** | Wrapping a primitive in an object (for nullable/generic). |
| **Dependency injection** | Supplying a class's collaborators rather than it creating them. |

## Appendix C — Further Resources

- **Official documentation** — `kotlinlang.org` — the authoritative language reference and guides.
- **Kotlin Koans** — `play.kotlinlang.org/koans` — interactive exercises to practice language features.
- **Coroutines guide** — the official `kotlinx.coroutines` docs for deep async patterns.
- **Ktor / Exposed / Compose Multiplatform** — each has thorough official documentation and samples.
- **Kotlin standard library reference** — browsable API docs for every stdlib function.
- **Community** — the Kotlin Slack (`kotlinlang.slack.com`), r/Kotlin, and Stack Overflow's `kotlin` tag.
- **Keep building** — the fastest path to mastery is shipping real projects. Take the Task Manager further: add authentication, deploy the backend, publish the library, ship the app.

## Appendix D — The Task Manager, Assembled

Across 36 chapters, one application — a **Task Manager** — grew from three `println`s into a clean-architecture, multiplatform, tested system. This appendix maps *which chapter added which piece*, so you can see the whole arc.

### The evolution

| Chapter | What the Task Manager gained |
|---------|------------------------------|
| **1** | A hard-coded banner and task list (`println`). |
| **2** | Tasks modelled as variables; computed progress via string templates. |
| **3** | Progress *statistics* using operators. |
| **4** | A review loop with `when`-based status. |
| **5** | Operations extracted into functions (incl. a higher-order summary). |
| **6** | Real tasks in a `MutableList`/`Set`; functional queries. |
| **7** | Null-safe input parsing and lookups. |
| **8** | A proper `data class Task` and a `TaskManager` class. |
| **9** | A `TaskRepository` *interface* (dependency inversion). |
| **10** | A `Priority` enum and a `sealed` operation result. |
| **11** | A fluent extension vocabulary (`summary()`, `pending()`, …). |
| **12** | A generic `Repository<T>`. |
| **13** | `by lazy` setup and `observable` change logging. |
| **14** | Cleaner construction/reporting via scope functions. |
| **15** | Async persistence and a live `StateFlow` of tasks. |
| **16** | Robust validation and `Result`-returning APIs. |
| **17** | A `@DslMarker` task-seeding DSL. |
| **19** | A multi-module Gradle build (`:core` + `:app`). |
| **20** | A Ktor REST API (full CRUD). |
| **21** | A database-backed `ExposedTaskRepository`. |
| **22** | A Jetpack Compose UI via a `TaskViewModel`. |
| **23** | An idiomatic refactor pass. |
| **24** | A unit test suite (JUnit + MockK). |
| **25** | A shareable `commonMain` core (`expect`/`actual` storage). |
| **26** | A reactive search (`combine`/`debounce`). |
| **27** | Thread-safe storage (`Mutex`) + bounded sync. |
| **31** | Polymorphic JSON persistence (sealed task types). |
| **32** | An optimised bulk-import hot path (`IntArray` + JMH). |
| **33** | Clean domain/data/presentation layers wired by DI. |
| **34** | A truly multiplatform core (JVM + iOS). |
| **36** | A full layered test suite (unit → property → flow → integration). |

### The shape of the final system

By the end, the Task Manager is:

- a **pure domain** (`Task`, `TaskRepository`, use cases) in `commonMain`, framework-free and shared across platforms;
- a **swappable data layer** (`InMemoryTaskRepository` for tests/demos, `ExposedTaskRepository` for production) behind the repository port;
- multiple **presentation layers** — a Ktor REST API, a Compose UI — all depending only on the domain;
- **reactive state** via `StateFlow`, **safe concurrency** via `Mutex`, **robust serialization** via `kotlinx.serialization`;
- wired together by **dependency injection** at a composition root;
- and verified by a **layered test suite** that makes fearless refactoring possible.

That progression — from a beginner's first `println` to an expert's architected, tested, multiplatform system, built one concept at a time — *is* the journey from zero to expert. The language features were never the point; building real, well-structured software with them was. You now have both.

### Buildable reference implementation

The earlier chapter projects intentionally isolate one idea at a time. This section assembles their stable core into a small repository that actually compiles, runs, and tests. The default profile is self-contained and uses an in-memory adapter; replace only the composition-root binding with the Chapter 21 PostgreSQL adapter in production.

#### Repository layout

```text
task-manager/
├── settings.gradle.kts
├── build.gradle.kts
├── shared/
│   ├── build.gradle.kts
│   └── src/
│       ├── commonMain/kotlin/tasks/Domain.kt
│       └── commonTest/kotlin/tasks/TaskServiceTest.kt
└── server/
    ├── build.gradle.kts
    ├── src/main/kotlin/tasks/server/Application.kt
    └── src/test/kotlin/tasks/server/TaskApiTest.kt
```

#### Root build

```kotlin
// settings.gradle.kts
pluginManagement { repositories { gradlePluginPortal(); mavenCentral() } }
dependencyResolutionManagement { repositories { mavenCentral() } }
rootProject.name = "task-manager"
include("shared", "server")
```

```kotlin
// build.gradle.kts
plugins {
    kotlin("multiplatform") version "2.4.0" apply false
    kotlin("jvm") version "2.4.0" apply false
    kotlin("plugin.serialization") version "2.4.0" apply false
}

allprojects {
    group = "com.example.tasks"
    version = "1.0.0"
}
```

```kotlin
// shared/build.gradle.kts
plugins {
    kotlin("multiplatform")
    kotlin("plugin.serialization")
}

kotlin {
    jvm()
    explicitApi()

    sourceSets {
        commonMain.dependencies {
            implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.11.0")
            implementation("org.jetbrains.kotlinx:kotlinx-serialization-json:1.11.0")
        }
        commonTest.dependencies {
            implementation(kotlin("test"))
            implementation("org.jetbrains.kotlinx:kotlinx-coroutines-test:1.11.0")
        }
    }
}
```

#### Shared domain and concurrency-safe adapter

```kotlin
// shared/src/commonMain/kotlin/tasks/Domain.kt
package tasks

import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow
import kotlinx.coroutines.flow.asStateFlow
import kotlinx.coroutines.sync.Mutex
import kotlinx.coroutines.sync.withLock
import kotlinx.serialization.Serializable

@Serializable
public data class Task(
    public val id: Long,
    public val title: String,
    public val done: Boolean = false,
)

public sealed interface TaskError {
    public data object BlankTitle : TaskError
    public data class TitleTooLong(public val maximum: Int) : TaskError
    public data class NotFound(public val id: Long) : TaskError
}

public sealed interface TaskResult<out T> {
    public data class Ok<T>(public val value: T) : TaskResult<T>
    public data class Err(public val error: TaskError) : TaskResult<Nothing>
}

public interface TaskRepository {
    public val tasks: StateFlow<List<Task>>
    public suspend fun create(title: String): Task
    public suspend fun find(id: Long): Task?
    public suspend fun setDone(id: Long, done: Boolean): Task?
    public suspend fun delete(id: Long): Boolean
}

public class InMemoryTaskRepository : TaskRepository {
    private val mutex: Mutex = Mutex()
    private val state: MutableStateFlow<List<Task>> = MutableStateFlow(emptyList())
    private var nextId: Long = 1

    override val tasks: StateFlow<List<Task>> = state.asStateFlow()

    override suspend fun create(title: String): Task = mutex.withLock {
        Task(nextId++, title).also { created -> state.value = state.value + created }
    }

    override suspend fun find(id: Long): Task? = mutex.withLock {
        state.value.firstOrNull { it.id == id }
    }

    override suspend fun setDone(id: Long, done: Boolean): Task? = mutex.withLock {
        var updated: Task? = null
        state.value = state.value.map { task ->
            if (task.id == id) task.copy(done = done).also { updated = it } else task
        }
        updated
    }

    override suspend fun delete(id: Long): Boolean = mutex.withLock {
        val before = state.value
        state.value = before.filterNot { it.id == id }
        state.value.size != before.size
    }
}

public class TaskService(private val repository: TaskRepository) {
    public val tasks: StateFlow<List<Task>> = repository.tasks

    public suspend fun create(rawTitle: String): TaskResult<Task> {
        val title = rawTitle.trim()
        if (title.isEmpty()) return TaskResult.Err(TaskError.BlankTitle)
        if (title.length > MAX_TITLE_LENGTH) {
            return TaskResult.Err(TaskError.TitleTooLong(MAX_TITLE_LENGTH))
        }
        return TaskResult.Ok(repository.create(title))
    }

    public suspend fun complete(id: Long): TaskResult<Task> =
        repository.setDone(id, true)?.let { TaskResult.Ok(it) }
            ?: TaskResult.Err(TaskError.NotFound(id))

    public suspend fun delete(id: Long): TaskResult<Unit> =
        if (repository.delete(id)) TaskResult.Ok(Unit)
        else TaskResult.Err(TaskError.NotFound(id))

    public companion object {
        public const val MAX_TITLE_LENGTH: Int = 200
    }
}
```

The mutex protects `nextId` and each read-modify-write as one critical section. The public stream exposes immutable list snapshots, so callers cannot mutate repository state behind its back.

#### Ktor server

```kotlin
// server/build.gradle.kts
plugins {
    kotlin("jvm")
    kotlin("plugin.serialization")
    application
}

dependencies {
    implementation(project(":shared"))
    implementation("io.ktor:ktor-server-core:3.5.0")
    implementation("io.ktor:ktor-server-netty:3.5.0")
    implementation("io.ktor:ktor-server-content-negotiation:3.5.0")
    implementation("io.ktor:ktor-server-status-pages:3.5.0")
    implementation("io.ktor:ktor-serialization-kotlinx-json:3.5.0")
    implementation("ch.qos.logback:logback-classic:1.5.20")

    testImplementation(kotlin("test"))
    testImplementation("io.ktor:ktor-server-test-host:3.5.0")
    testImplementation("io.ktor:ktor-client-content-negotiation:3.5.0")
}

kotlin { jvmToolchain(21) }
application { mainClass.set("tasks.server.ApplicationKt") }
tasks.test { useJUnitPlatform() }
```

```kotlin
// server/src/main/kotlin/tasks/server/Application.kt
package tasks.server

import io.ktor.http.HttpStatusCode
import io.ktor.serialization.kotlinx.json.json
import io.ktor.server.application.*
import io.ktor.server.engine.embeddedServer
import io.ktor.server.netty.Netty
import io.ktor.server.plugins.BadRequestException
import io.ktor.server.plugins.ContentTransformationException
import io.ktor.server.plugins.contentnegotiation.ContentNegotiation
import io.ktor.server.plugins.statuspages.StatusPages
import io.ktor.server.request.receive
import io.ktor.server.response.respond
import io.ktor.server.routing.*
import kotlinx.serialization.Serializable
import tasks.*

@Serializable
data class CreateTaskRequest(val title: String)

@Serializable
data class ApiError(val code: String, val message: String)

fun main() {
    val repository = InMemoryTaskRepository()
    embeddedServer(Netty, port = 8080) { taskModule(TaskService(repository)) }
        .start(wait = true)
}

fun Application.taskModule(service: TaskService) {
    install(ContentNegotiation) { json() }
    install(StatusPages) {
        exception<ContentTransformationException> { call, _ ->
            call.respond(HttpStatusCode.BadRequest, ApiError("INVALID_JSON", "Malformed JSON body"))
        }
        exception<BadRequestException> { call, _ ->
            call.respond(HttpStatusCode.BadRequest, ApiError("BAD_REQUEST", "Malformed request"))
        }
        exception<Throwable> { call, cause ->
            environment.log.error("Unhandled request", cause)
            call.respond(HttpStatusCode.InternalServerError, ApiError("INTERNAL", "Unexpected failure"))
        }
    }

    routing {
        get("/health/live") { call.respond(mapOf("status" to "up")) }
        get("/tasks") { call.respond(service.tasks.value) }

        post("/tasks") {
            when (val result = service.create(call.receive<CreateTaskRequest>().title)) {
                is TaskResult.Ok -> call.respond(HttpStatusCode.Created, result.value)
                is TaskResult.Err -> call.respondTaskError(result.error)
            }
        }

        put("/tasks/{id}/complete") {
            val id = call.parameters["id"]?.toLongOrNull()
                ?: return@put call.respond(HttpStatusCode.BadRequest, ApiError("INVALID_ID", "Numeric id required"))
            when (val result = service.complete(id)) {
                is TaskResult.Ok -> call.respond(result.value)
                is TaskResult.Err -> call.respondTaskError(result.error)
            }
        }

        delete("/tasks/{id}") {
            val id = call.parameters["id"]?.toLongOrNull()
                ?: return@delete call.respond(HttpStatusCode.BadRequest, ApiError("INVALID_ID", "Numeric id required"))
            when (val result = service.delete(id)) {
                is TaskResult.Ok -> call.respond(HttpStatusCode.NoContent)
                is TaskResult.Err -> call.respondTaskError(result.error)
            }
        }
    }
}

private suspend fun ApplicationCall.respondTaskError(error: TaskError) {
    when (error) {
        TaskError.BlankTitle -> respond(
            HttpStatusCode.UnprocessableEntity,
            ApiError("BLANK_TITLE", "Title must not be blank"),
        )
        is TaskError.TitleTooLong -> respond(
            HttpStatusCode.UnprocessableEntity,
            ApiError("TITLE_TOO_LONG", "Maximum is ${error.maximum} characters"),
        )
        is TaskError.NotFound -> respond(
            HttpStatusCode.NotFound,
            ApiError("TASK_NOT_FOUND", "Task ${error.id} does not exist"),
        )
    }
}
```

#### Tests that exercise behavior through real boundaries

```kotlin
// shared/src/commonTest/kotlin/tasks/TaskServiceTest.kt
package tasks

import kotlinx.coroutines.test.runTest
import kotlin.test.*

class TaskServiceTest {
    @Test
    fun blankTitleIsRejectedWithoutMutation() = runTest {
        val service = TaskService(InMemoryTaskRepository())
        assertEquals(TaskResult.Err(TaskError.BlankTitle), service.create("   "))
        assertTrue(service.tasks.value.isEmpty())
    }

    @Test
    fun createThenCompletePublishesANewSnapshot() = runTest {
        val service = TaskService(InMemoryTaskRepository())
        val created = (service.create("  Ship it  ") as TaskResult.Ok<Task>).value
        val completed = (service.complete(created.id) as TaskResult.Ok<Task>).value
        assertEquals("Ship it", completed.title)
        assertTrue(completed.done)
        assertEquals(listOf(completed), service.tasks.value)
    }
}
```

```kotlin
// server/src/test/kotlin/tasks/server/TaskApiTest.kt
package tasks.server

import io.ktor.client.call.body
import io.ktor.client.plugins.contentnegotiation.ContentNegotiation
import io.ktor.client.request.*
import io.ktor.http.*
import io.ktor.serialization.kotlinx.json.json
import io.ktor.server.testing.testApplication
import kotlin.test.*
import tasks.*

class TaskApiTest {
    @Test
    fun createCompleteListDeleteJourney() = testApplication {
        application { taskModule(TaskService(InMemoryTaskRepository())) }
        val apiClient = createClient { install(ContentNegotiation) { json() } }

        val createdResponse = apiClient.post("/tasks") {
            contentType(ContentType.Application.Json)
            setBody("""{"title":"Integration test"}""")
        }
        assertEquals(HttpStatusCode.Created, createdResponse.status)
        val created = createdResponse.body<Task>()

        assertEquals(HttpStatusCode.OK, apiClient.put("/tasks/${created.id}/complete").status)
        val listed = apiClient.get("/tasks").body<List<Task>>()
        assertEquals(listOf(created.copy(done = true)), listed)

        assertEquals(HttpStatusCode.NoContent, apiClient.delete("/tasks/${created.id}").status)
        assertTrue(apiClient.get("/tasks").body<List<Task>>().isEmpty())
    }
}
```

#### Build, test, and run

After copying the files into a new directory, generate the wrapper once with a trusted local Gradle installation (or the IDE's Gradle action), then commit every generated wrapper file:

```bash
gradle wrapper --gradle-version 9.5
./gradlew clean check
./gradlew :server:run

curl -i -X POST http://localhost:8080/tasks \
  -H 'Content-Type: application/json' \
  -d '{"title":"Read the assembled appendix"}'
curl -s http://localhost:8080/tasks
```

Before calling this production-ready, apply the production sections of Chapters 19–22: commit the wrapper and lock/verify dependencies; replace the in-memory binding with a pooled PostgreSQL repository plus Flyway migrations; add authentication/authorization, request ids, metrics, readiness, bounded timeouts, secrets management, and graceful shutdown; then run the Chapter 36 contract, migration, container, and load tests. The architecture deliberately makes those adapters replaceable without changing the shared domain or route behavior.
