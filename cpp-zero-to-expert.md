# C++: Zero to Expert — for Scientific & High-Performance Computing

*A complete, self-study path from your first `std::cout` to expert-level modern C++ for numerical and high-performance computing — every runnable example compiled, run, and shown with its real output.*

## Who this booklet is for

You need no prior C++. If you have written *any* code before — even a little Python, or some C, or Fortran from a numerics course — you have enough to start at Chapter 1. The orientation is **scientific and high-performance computing**: the examples are drawn from computational physics (energies, momenta, Monte Carlo, histograms, linear algebra), and the emphasis throughout is on *correctness of numbers* and *speed on real hardware* — the two things that matter when your code produces a result someone will publish.

The goal is not just to make you *productive* in C++, but to make you *understand* it: not only how to write a `unique_ptr`, but what it compiles to and why it costs nothing; not only how to sum a vector, but why the *order* of the sum changes the answer; not only how to launch a thread, but what a data race actually is. That "under the hood" understanding is what separates an advanced user from an expert, and it is woven into every chapter.

## Modern C++, verified

This booklet targets **modern C++ (C++23)** and teaches the modern idioms *first* — RAII, smart pointers, `std::vector`, ranges, concepts, `std::format`, `std::expected` — not the legacy C-with-classes style. Raw pointers, `new`/`delete`, and manual memory management are taught so you *understand* them (and can read older code), but always in service of the safe, modern way.

The foundational runnable examples were compiled and executed with `g++ -std=c++23 -Wall -Wextra` (GCC 13.3), and their output blocks record observed output. Timing and random output are labelled representative where machines or runs can differ. Later expert chapters also contain **interface sketches** for facilities whose build commands depend on an external implementation (MPI, OpenMP, CUDA/SYCL, Google Benchmark, and modules); these are explicitly described as such and must be validated against your selected toolchain. Treat compiler diagnostics, tests, and reproducible scripts—not a printed output block—as the final authority.

## How each chapter is structured

Every chapter follows the same rhythm, so you always know where you are:

- **Learning objectives** up front — what you'll be able to do by the end.
- A short **in-this-chapter** table of contents.
- For each new idea: **the problem it solves** → **a mental model** → **the syntax, explained** → **a worked example with its verified output** → callouts for internals, traps, and idioms.
- A **Summary**, a **Self-check quiz** (with collapsible answers), graduated **Exercises** (with collapsible solutions and their real output), and a **Chapter Project**.
- A **Glossary** of new terms and a **What's next** pointer.

**Read actively.** Type the examples out and compile them. Predict outputs before you check them. Open the collapsible solutions only after you have attempted the exercise yourself — the struggle is where the learning happens.

## The callout legend

Throughout the booklet you'll see these labelled notes:

| Callout | Meaning |
|---------|---------|
| ⚙️ **Under the hood** | What the feature compiles to / how it behaves at runtime and in memory (the expert layer). |
| ⚠️ **Gotcha** | A common mistake, surprising behaviour, or source of undefined behavior to watch for. |
| 💡 **Idiom** | The idiomatic, modern-C++ way to do something. |
| 🛠️ **Chapter Project** | The cumulative end-of-chapter project (see below). |

## The running project: a Monte Carlo Analysis Toolkit

Rather than a scatter of unrelated snippets, most chapters grow **one application**: a small, particle-physics-flavoured **Monte Carlo Analysis Toolkit**. It starts in Chapter 1 as a `main()` printing a particle's energy, becomes floating-point-correct statistics, gains a `Histogram` class with RAII-owned storage, learns to own data buffers (rule of five, move semantics) and manage them with smart pointers, grows a generic `Matrix` and operator-overloaded physics vectors (reconstructing the Z boson at 91.3 GeV), then a full **Monte Carlo event generator**, numerical integrators, `constexpr` physics constants, binary data I/O, a CMake build, a parallel π-integrator, and finally a sanitized, reproducible **test suite**.

Each **🛠️ Chapter Project** builds only on concepts already introduced — so you can always complete it with what you've learned so far. The fully assembled arc lives in **Appendix D**.

## Learning roadmap

The 58 chapters form seven parts. You can read straight through, or use this as a map. Parts 1–4 build a strong modern-C++ and scientific-computing foundation, Part 5 develops language and performance expertise, Part 6 connects that expertise to production HPC systems, and **Part 7 hardens it through systems work, adversarial verification, and deep specialization.**

**Part 1 — Foundations (Ch. 1–8).** The core language: the toolchain, types and initialization, floating-point (in depth — it's where scientific bugs live), operators, control flow, functions (parameters/performance *and* lambdas), and the build model.
*After this part you can write correct, numerically careful C++ programs and command-line logic, and build them.*

**Part 2 — Memory & Objects (Ch. 9–15).** The heart of C++: classes, pointers and references, dynamic memory and **RAII**, the rule of five, move semantics, smart pointers, and inheritance/polymorphism.
*After this part you can manage resources safely and design clean object models with precise control over memory.*

**Part 3 — Generic Programming & the STL (Ch. 16–21).** Templates, operator overloading, the STL containers, iterators/algorithms/`<numeric>`, concepts, and error handling.
*After this part you can write generic, constrained, robust code over the standard library.*

**Part 4 — Scientific Computing Core (Ch. 22–28).** The science: random numbers and Monte Carlo, numerical algorithms (integration, root-finding, ODEs), linear algebra and matrices, multidimensional data layout, compile-time computation, scientific I/O, and CMake with numerical libraries.
*After this part you can build real numerical software — simulate, integrate, solve, store, and build it.*

**Part 5 — Performance & Mastery (Ch. 29–33).** The expert layer: the abstract machine and undefined behavior, template metaprogramming, performance and optimization for HPC (cache, SIMD, benchmarking), concurrency and parallelism, and testing/reproducibility/safety.
*After this part you can reason about C++ down to the abstract machine, optimise hot paths to the hardware, parallelise correctly, and produce numerical software you can trust and reproduce.*

**Part 6 — Expert C++ & Production HPC (Ch. 34–45).** Object lifetime and ABI, advanced generic programming, vocabulary types and ranges, coroutines and modules, the formal memory model, production CMake and tooling, performance modelling, OpenMP, MPI, GPU portability, robust numerical software, and a fully integrated capstone.
*After this part you can design stable libraries, diagnose lifetime and concurrency failures, build and package portable projects, and scale a measured scientific kernel from one core to a node, a cluster, and an accelerator.*

**Part 7 — Production Systems, Verification & Deep Specialization (Ch. 46–58).** Allocator engineering, exception guarantees, debugger-led diagnosis, fuzz/property testing, hardware-counter profiling, advanced synchronization and reclamation, asynchronous networking, durable serialization, library architecture, language-lawyer object rules, cross-platform security, modules/package delivery, accelerator optimization, and a final competency audit.
*After this part you can investigate failures from evidence, design hostile-input and compatibility boundaries, justify low-level optimizations, and demonstrate expert competence through reproducible builds and adversarial tests.*

> **Note on the toolchain.** The language baseline is **C++23**. Foundational examples were validated with GCC 13.3; newer standard-library facilities and external HPC examples require a toolchain that actually implements them. Record the compiler, standard library, dependency versions, and flags used for each experiment. Portable alternatives are shown where support is uneven, and CI—not the standard-mode flag alone—defines the supported matrix.

## Table of Contents

**Part 1 — Foundations**

- [Chapter 1 — Getting Started & the C++ Toolchain](#chapter-1--getting-started--the-c-toolchain)
- [Chapter 2 — Types, Initialization & `const`](#chapter-2--types-initialization--const)
- [Chapter 3 — Floating-Point & Numeric Types](#chapter-3--floating-point--numeric-types)
- [Chapter 4 — Operators & Expressions](#chapter-4--operators--expressions)
- [Chapter 5 — Control Flow](#chapter-5--control-flow)
- [Chapter 6 — Functions I: Parameters, Overloading & Performance](#chapter-6--functions-i-parameters-overloading--performance)
- [Chapter 7 — Functions II: Lambdas & Function Objects](#chapter-7--functions-ii-lambdas--function-objects)
- [Chapter 8 — Headers, Translation Units & the Build Model](#chapter-8--headers-translation-units--the-build-model)

**Part 2 — Memory & Objects**

- [Chapter 9 — Classes & Objects](#chapter-9--classes--objects)
- [Chapter 10 — Pointers, References & const-correctness](#chapter-10--pointers-references--const-correctness)
- [Chapter 11 — Dynamic Memory & RAII](#chapter-11--dynamic-memory--raii)
- [Chapter 12 — The Rule of Three / Five / Zero](#chapter-12--the-rule-of-three--five--zero)
- [Chapter 13 — Move Semantics](#chapter-13--move-semantics)
- [Chapter 14 — Smart Pointers](#chapter-14--smart-pointers)
- [Chapter 15 — Inheritance & Polymorphism](#chapter-15--inheritance--polymorphism)

**Part 3 — Generic Programming & the STL**

- [Chapter 16 — Templates](#chapter-16--templates)
- [Chapter 17 — Operator Overloading](#chapter-17--operator-overloading)
- [Chapter 18 — STL Containers](#chapter-18--stl-containers)
- [Chapter 19 — Iterators, Algorithms & `<numeric>`](#chapter-19--iterators-algorithms--numeric)
- [Chapter 20 — Concepts & Constraints](#chapter-20--concepts--constraints)
- [Chapter 21 — Error Handling](#chapter-21--error-handling)

**Part 4 — Scientific Computing Core**

- [Chapter 22 — Random Numbers & Monte Carlo](#chapter-22--random-numbers--monte-carlo)
- [Chapter 23 — Numerical Algorithms](#chapter-23--numerical-algorithms)
- [Chapter 24 — Linear Algebra & Matrices](#chapter-24--linear-algebra--matrices)
- [Chapter 25 — Multidimensional Data & Layout](#chapter-25--multidimensional-data--layout)
- [Chapter 26 — `constexpr` & Compile-Time Computation](#chapter-26--constexpr--compile-time-computation)
- [Chapter 27 — I/O, `std::format` & Scientific Data](#chapter-27--io-stdformat--scientific-data)
- [Chapter 28 — Build Systems, CMake & Linking Numerical Libraries](#chapter-28--build-systems-cmake--linking-numerical-libraries)

**Part 5 — Performance & Mastery**

- [Chapter 29 — The Abstract Machine & Undefined Behavior](#chapter-29--the-abstract-machine--undefined-behavior)
- [Chapter 30 — Template Metaprogramming](#chapter-30--template-metaprogramming)
- [Chapter 31 — Performance & Optimization for HPC](#chapter-31--performance--optimization-for-hpc)
- [Chapter 32 — Concurrency & Parallelism](#chapter-32--concurrency--parallelism)
- [Chapter 33 — Testing, Reproducibility & Safety](#chapter-33--testing-reproducibility--safety)

**Part 6 — Expert C++ & Production HPC**

- [Chapter 34 — Object Lifetime, Layout, Casts & ABI](#chapter-34--object-lifetime-layout-casts--abi)
- [Chapter 35 — Advanced Templates, Deduction & Perfect Forwarding](#chapter-35--advanced-templates-deduction--perfect-forwarding)
- [Chapter 36 — Vocabulary Types, Advanced Ranges & Library Design](#chapter-36--vocabulary-types-advanced-ranges--library-design)
- [Chapter 37 — Coroutines, Modules & Modern Program Structure](#chapter-37--coroutines-modules--modern-program-structure)
- [Chapter 38 — The C++ Memory Model & Advanced Concurrency](#chapter-38--the-c-memory-model--advanced-concurrency)
- [Chapter 39 — Production CMake, Dependencies, Packaging & CI](#chapter-39--production-cmake-dependencies-packaging--ci)
- [Chapter 40 — Performance Engineering: Benchmarking, SIMD & NUMA](#chapter-40--performance-engineering-benchmarking-simd--numa)
- [Chapter 41 — Shared-Memory HPC with OpenMP](#chapter-41--shared-memory-hpc-with-openmp)
- [Chapter 42 — Distributed HPC with MPI](#chapter-42--distributed-hpc-with-mpi)
- [Chapter 43 — GPU & Accelerator Programming](#chapter-43--gpu--accelerator-programming)
- [Chapter 44 — Robust Numerical Software](#chapter-44--robust-numerical-software)
- [Chapter 45 — Capstone: A Production Monte Carlo Toolkit](#chapter-45--capstone-a-production-monte-carlo-toolkit)

**Part 7 — Production Systems, Verification & Deep Specialization**

- [Chapter 46 — Allocator Engineering & Transactional Error Safety](#chapter-46--allocator-engineering--transactional-error-safety)
- [Chapter 47 — Debugging, Core Dumps & Program Analysis](#chapter-47--debugging-core-dumps--program-analysis)
- [Chapter 48 — Property Testing, Fuzzing & Verification Strategy](#chapter-48--property-testing-fuzzing--verification-strategy)
- [Chapter 49 — Evidence-Driven Profiling, PGO & LTO](#chapter-49--evidence-driven-profiling-pgo--lto)
- [Chapter 50 — Advanced Concurrency, Lock-Free Memory & Executors](#chapter-50--advanced-concurrency-lock-free-memory--executors)
- [Chapter 51 — Coroutines, Event Loops & Network Programming](#chapter-51--coroutines-event-loops--network-programming)
- [Chapter 52 — Serialization, Schemas & Scientific Data Systems](#chapter-52--serialization-schemas--scientific-data-systems)
- [Chapter 53 — API Design, Architecture, Patterns & Plugins](#chapter-53--api-design-architecture-patterns--plugins)
- [Chapter 54 — Deep Templates, Object Representation & Type Erasure](#chapter-54--deep-templates-object-representation--type-erasure)
- [Chapter 55 — Cross-Platform Systems & Secure C++](#chapter-55--cross-platform-systems--secure-c)
- [Chapter 56 — Modules, Package Managers & Reproducible Delivery](#chapter-56--modules-package-managers--reproducible-delivery)
- [Chapter 57 — Accelerator Optimization & Multi-GPU Design](#chapter-57--accelerator-optimization--multi-gpu-design)
- [Chapter 58 — Expert Assessment & Validation Matrix](#chapter-58--expert-assessment--validation-matrix)

**Appendices**

- [Appendix A — Cheat Sheet](#appendix-a--cheat-sheet)
- [Appendix B — Glossary](#appendix-b--glossary)
- [Appendix C — Further Resources](#appendix-c--further-resources)
- [Appendix D — The Monte Carlo Analysis Toolkit, Assembled](#appendix-d--the-monte-carlo-analysis-toolkit-assembled)


---

## Chapter 1 — Getting Started & the C++ Toolchain

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** none — start here.

**Learning objectives** — after this chapter you will be able to:

- Say why C++ dominates scientific and high-performance computing.
- Build a program from the command line and read the compiler's flags.
- Explain what *compiling* and *linking* actually do, and tell their errors apart.
- Print results, and format numbers precisely with `std::format` — the core skill of scientific reporting.

**In this chapter**

- [1.1 Why C++ for science?](#11-why-c-for-science)
- [1.2 The toolchain and build flags](#12-the-toolchain-and-build-flags)
- [1.3 Your first program](#13-your-first-program)
- [1.4 The compile-link pipeline](#14-the-compile-link-pipeline)
- [1.5 Printing with `std::cout`](#15-printing-with-stdcout)
- [1.6 Formatted output with `std::format`](#16-formatted-output-with-stdformat)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-toolkit-v0) · Glossary · What's next

---

### 1.1 Why C++ for science?

If you do computational science — simulating particle collisions, fitting models to detector data, running Monte Carlo integrations, solving PDEs — you will meet C++. It is the language of **CERN's ROOT** analysis framework and **Geant4** detector simulation, of numerical libraries like **Eigen** and **BLAS/LAPACK**, and the host language under **CUDA** GPU kernels. The field keeps choosing it for concrete reasons:

- **Performance.** C++ compiles to native machine code — no interpreter, no mandatory garbage collector. You get control over memory layout, cache behaviour, and vectorization, which is decisive when a job runs for days on thousands of cores.
- **Zero-overhead abstraction.** Its guiding principle: *you don't pay for what you don't use, and what you do use is as efficient as hand-written code.* You write expressive high-level code (templates, ranges) that compiles down to tight loops.
- **Control.** *You* decide when memory is allocated and freed and how data is laid out — essential when an inner loop runs 10¹² times.
- **Ecosystem.** Decades of battle-tested scientific libraries, plus interoperability with C, Fortran (LAPACK), Python (pybind11), and GPUs.

The trade-off is responsibility: C++ trusts you. It will let you read freed memory, overflow an integer, or trigger *undefined behaviour* — and won't always warn you. This booklet's job is to make you a C++ programmer who wields that power safely, writing code that is both fast *and* correct.

> ⚙️ **Under the hood** — "Zero-overhead" is not marketing. A `std::vector<double>` compiles to essentially the same code as a hand-managed `double*` array; a range pipeline can compile to the same loop you'd write by hand. The optimizer, guided by the *as-if rule* (Chapter 30), may transform your code however it likes as long as the observable behaviour is unchanged — so high-level and low-level C++ often produce *identical* assembly.

> ☕ **Coming from Python** — Many scientists use Python for exploration and C++ for the heavy lifting (the "two-language problem"). A common pattern at labs like CERN: performance-critical cores in C++, driven from Python notebooks (via pybind11). The C++ you learn here is exactly what sits under that fast layer.

### 1.2 The toolchain and build flags

To turn C++ source into a running program you need a **compiler**. The three major ones are **GCC** (`g++`), **Clang** (`clang++`), and **MSVC** (Windows). This booklet uses **`g++`** and targets **C++23**, the current standard. Check it:

```text
$ g++ --version
g++ (Ubuntu 13.3.0) 13.3.0
```

Compile a file to an executable and run it:

```text
$ g++ -std=c++23 -Wall -Wextra main.cpp -o prog
$ ./prog
```

The flags you'll use constantly, and what each does:

| Flag | Meaning |
|------|---------|
| `-std=c++23` | Use the C++23 standard (older toolchains: `-std=c++20`). |
| `-Wall -Wextra` | Enable warnings — your first line of defence against silent bugs. |
| `-O2` | Optimize for speed (use for production/benchmark builds). |
| `-g` | Include debug symbols (for `gdb` / sanitizers). |
| `-c` | Compile *only* to an object file (`.o`), don't link (Chapter 8). |
| `-o name` | Name the output file. |
| `-fsanitize=address,undefined` | Turn on runtime bug detectors (Chapter 33) — invaluable for scientific code. |

A typical development build is `g++ -std=c++23 -Wall -Wextra -g -fsanitize=address,undefined`; a production build is `g++ -std=c++23 -O2 -DNDEBUG`.

> 💡 **Idiom** — Always compile with **`-Wall -Wextra`** (many projects add `-Wpedantic`, and `-Werror` to make warnings fatal). C++ won't stop you doing something dangerous unless you ask it to be strict, so a clean, warning-free build is the *baseline* for correct scientific code — treat every warning as a bug to fix.

### 1.3 Your first program

Create `main.cpp`:

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, scientific C++!\n";
    return 0;
}
```

Compiled and run, it prints:

```text
Hello, scientific C++!
```

Read it token by token — every part recurs thousands of times:

- **`#include <iostream>`** — a *preprocessor directive* (Chapter 8) that pulls in the input/output library, giving `std::cout`. C++ has no built-in `print`; you include what you need.
- **`int main()`** — the **entry point**. Every program has exactly one `main`; the OS calls it to start. Its `int` return is an *exit code* (0 = success).
- **`{ … }`** — the function body.
- **`std::cout << "..."`** — sends text to *standard output*. `std::cout` is the output stream; `<<` is the "stream insertion" operator (the same `<<` as bit-shift, overloaded — Chapter 15). `std::` is the *standard-library namespace*.
- **`\n`** — a newline. **`return 0;`** — the exit code (for `main`, you may omit it; C++ returns 0 implicitly).

> ☕ **Coming from Python/other languages** — There is no "just run the file." C++ is compiled *ahead of time*: you translate the whole program to a native executable first, then run it. This is why type errors are caught before the program starts — and why C++ programs launch instantly and run fast, with no interpreter.

### 1.4 The compile-link pipeline

"Compiling" is really several stages, and knowing them explains most build errors:

```text
main.cpp ──preprocess──▶ (expanded source) ──compile──▶ main.o ──link──▶ prog
```

1. **Preprocessing** — handles `#include`, `#define`, etc., producing one expanded *translation unit* (Chapter 8).
2. **Compilation** — translates that into **object code** (machine instructions) in a `.o` file. *Type errors are caught here.*
3. **Linking** — the **linker** combines your object files (and libraries) into one executable, connecting references (e.g., your call to `std::cout` to its implementation).

> ⚙️ **Under the hood** — This split is why C++ has two error classes. A **compile error** (unknown type, syntax slip) comes from stage 2 and names a file/line. A **linker error** ("undefined reference to …") comes from stage 3 — the code compiled, but the linker couldn't find a definition (a missing library, or a declared-but-undefined function). When you later link a numerical library like BLAS (`-lblas`), you feed the *linker* extra object code. Knowing which stage failed tells you where to look — a distinction we'll use in Chapter 8.

### 1.5 Printing with `std::cout`

`std::cout << x` streams a value to the console; chain `<<` to print several things:

```cpp
#include <iostream>
int main() {
    std::cout << "A";
    std::cout << "B" << "C";
    std::cout << "\n";
    std::cout << "next line\n";
}
```

Output:

```text
ABC
next line
```

Nothing prints a newline unless you include `\n` — the pieces `A`, `B`, `C` land on one line. `std::cout` can print numbers too (`std::cout << 42 << " " << 3.14`), but controlling *how* numbers look — decimal places, alignment — through `std::cout` alone is clumsy (it needs `<iomanip>` manipulators). For scientific output, `std::format` is far better.

### 1.6 Formatted output with `std::format`

Scientific reporting lives on *precise* number formatting — a table of results to 4 decimals, a value in scientific notation, aligned columns. C++20's **`std::format`** builds a string from a template with `{}` placeholders and a mini-language after `:` inside each brace. This section is worth mastering; you'll use it in every chapter.

```cpp
#include <iostream>
#include <format>
#include <numbers>            // std::numbers::pi (C++20)
int main() {
    double pi = std::numbers::pi;

    std::cout << std::format("pi = {:.5f}\n", pi);          // fixed, 5 decimals
    std::cout << std::format("[{:8.2f}]\n", pi);            // width 8, right-aligned
    std::cout << std::format("[{:<8.2f}]\n", pi);           // left-aligned
    std::cout << std::format("Avogadro = {:.3e}\n", 6.02214076e23);   // scientific
    std::cout << std::format("hex={:#x} bin={:#b} padded={:05d}\n", 255, 5, 42);
    std::cout << std::format("{0} squared is {1}\n", 7, 7*7);         // positional
    std::cout << std::format("{:+.1f} {:+.1f}\n", 3.0, -3.0);        // explicit sign
}
```

Output:

```text
pi = 3.14159
[    3.14]
[3.14    ]
Avogadro = 6.022e+23
hex=0xff bin=0b101 padded=00042
7 squared is 49
+3.0 -3.0
```

The format mini-language, in the pieces you'll reach for:

| Spec | Effect | Example → output |
|------|--------|------------------|
| `{:.Nf}` | Fixed-point, N decimals | `{:.3f}` of π → `3.142` |
| `{:.Ne}` | Scientific, N decimals | `{:.2e}` of 6.022e23 → `6.02e+23` |
| `{:W.Pf}` | Width W, precision P | `{:8.2f}` → `␣␣␣␣3.14` |
| `{:<}` `{:>}` `{:^}` | Left / right / centre align | `{:<8}` → left in 8 cols |
| `{:05d}` | Zero-pad an integer to width 5 | `42` → `00042` |
| `{:#x}` `{:#b}` | Hex / binary with prefix | `255` → `0xff` |
| `{:+}` | Always show sign | `3.0` → `+3.0` |
| `{0}` `{1}` | Positional arguments | reorder/repeat args |

> 💡 **Idiom** — Reach for `std::format` (via `std::cout << std::format(...)`) rather than `std::cout` manipulators (`std::setprecision`, `std::setw` from `<iomanip>`), which are stateful and clumsy. `std::format` is stateless, type-safe (a wrong type is a *compile* error), and reads like the result. For a results table, `{:>10.4f}` per column gives clean alignment.

> ⚠️ **Gotcha** — C++23 also specifies `std::print("...")` (like Python's `print`), but not every compiler ships it yet (GCC 13 does not). Throughout this booklet we use the universally-available **`std::cout << std::format(...)`**. If your compiler has `<print>`, `std::print("x = {}\n", x)` is the tidier equivalent — otherwise the pattern here works everywhere.

---

### Summary

- C++ powers scientific/HPC computing (**ROOT**, **Geant4**, **Eigen**, CUDA) for **native performance**, **zero-overhead abstraction**, and **control** — at the cost of responsibility (avoiding undefined behaviour).
- Build with **`g++ -std=c++23 -Wall -Wextra main.cpp -o prog`**; key flags: `-O2` (speed), `-g` (debug), `-c` (compile-only), `-fsanitize=...` (bug detectors). Always enable warnings.
- **`int main()`** is the entry point; **`#include`** pulls in libraries; **`std::cout << … << "\n"`** prints.
- Building runs **preprocess → compile → link**; *compile* errors and *linker* errors ("undefined reference") come from different stages.
- **`std::format`** is the scientific-output workhorse: `{:.Nf}` (decimals), `{:.Ne}` (scientific), width/alignment (`{:8.2f}`, `{:<}`), `{:05d}`, `{:#x}`, `{:+}`, positional `{0}`.

### Self-check quiz

1. Name two reasons C++ is favoured for scientific computing.
   <details><summary>Answer</summary>Any two of: native performance (no interpreter/GC), zero-overhead abstractions, fine control over memory/layout, a mature scientific ecosystem (ROOT, Eigen, BLAS/LAPACK, CUDA).</details>
2. What do `-Wall -Wextra` do, and why always use them?
   <details><summary>Answer</summary>Enable compiler warnings. C++ accepts many mistakes silently; warnings surface them early — essential since the compiler won't otherwise stop dangerous-but-legal code.</details>
3. What's the difference between a compile error and a linker error?
   <details><summary>Answer</summary>A compile error is a problem translating one translation unit (syntax/type), with a file/line. A linker error ("undefined reference") means compilation succeeded but the linker couldn't find a definition (missing library/source).</details>
4. How do you print π to exactly 4 decimal places?
   <details><summary>Answer</summary>`std::cout << std::format("{:.4f}\n", pi);` — `{:.4f}` is fixed-point with 4 digits after the decimal.</details>
5. What does `-c` do?
   <details><summary>Answer</summary>Compiles a source file only to an object file (`.o`) without linking — used to build each translation unit separately before a final link step (Chapter 8).</details>

### Exercises

**Exercise 1.1 — Personal intro (guided).** Print your name and a physical constant on separate lines.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    std::cout << "Name: Alice\n";
    std::cout << std::format("Speed of light: {} m/s\n", 299792458);
}
```

Output:
```text
Name: Alice
Speed of light: 299792458 m/s
```

**Why this works:** two `std::cout` statements each end in `\n`, giving two lines. `std::format` with `{}` inserts the integer without a decimal point.

</details>

**Exercise 1.2 — A results table.** Print three energies aligned to 2 decimals in a width-8 column, one per line.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    double es[] = {91.1876, 125.0, 4.18};
    for (double e : es)
        std::cout << std::format("{:>8.2f} GeV\n", e);
}
```

Output:
```text
   91.19 GeV
  125.00 GeV
    4.18 GeV
```

**Why this works:** `{:>8.2f}` right-aligns (`>`) each value in an 8-character field with 2 decimals, so the decimal points line up — exactly how you present a results table. (`91.1876` rounds to `91.19`.)

</details>

**Exercise 1.3 — Scientific notation.** Print Avogadro's number and the electron charge (1.602176634e-19) in scientific notation to 4 significant decimals.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    std::cout << std::format("N_A = {:.4e} /mol\n", 6.02214076e23);
    std::cout << std::format("e   = {:.4e} C\n", 1.602176634e-19);
}
```

Output:
```text
N_A = 6.0221e+23 /mol
e   = 1.6022e-19 C
```

**Why this works:** `{:.4e}` uses scientific (exponential) notation with 4 digits after the decimal — the natural format for the very large and very small numbers of physics.

</details>

**Exercise 1.4 — Hex and binary.** Print the number 200 in decimal, hexadecimal (with prefix), and binary (with prefix).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    int n = 200;
    std::cout << std::format("dec={} hex={:#x} bin={:#b}\n", n, n, n);
}
```

Output:
```text
dec=200 hex=0xc8 bin=0b11001000
```

**Why this works:** `{:#x}` and `{:#b}` format an integer as hex/binary with the `0x`/`0b` prefix (the `#` adds the prefix) — useful for detector trigger words and bit masks (Chapter 4).

</details>

### Chapter project: Toolkit v0

> 🛠️ **Chapter Project** — The first version of the **running Monte Carlo Analysis Toolkit** we grow across the book — a particle-physics-flavoured tool for simulating and analysing "events." **Builds on:** Chapter 1 only. It's deliberately tiny: the goal is to build and run *something*, formatted like a real report.

**Goal.** Print a banner and a few hard-coded "analysis results," neatly formatted.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v0 ===\n";
    std::cout << std::format("{:<16}: {}\n",     "Events analyzed", 3);
    std::cout << std::format("{:<16}: {:.2f} GeV\n", "Mean energy",  91.19);
    std::cout << std::format("{:<16}: {:.3e}\n",  "Luminosity",     1.4e34);
    std::cout << "Status: ready\n";
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v0 ===
Events analyzed : 3
Mean energy     : 91.19 GeV
Luminosity      : 1.400e+34
Status: ready
```

**Commentary.**
- Everything is hard-coded — the event count, the mean, the luminosity. That's fine for v0; the entire book is about *replacing* those constants with real computation. In Chapter 3 the mean becomes a floating-point-correct calculation; in Chapter 9 an "event" becomes a real `Particle` type; in Chapter 18 events live in a `std::vector`; in Chapter 22 we *simulate* them with Monte Carlo.
- The `{:<16}` left-aligns each label in a 16-character field so the colons line up — a report, not a debug dump. `{:.3e}` puts the luminosity (a huge number) in scientific notation. Presentation is part of doing science: results people can *read* are results people trust.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Compiler** | Translates C++ source into native machine code (`g++`). |
| **`main`** | The program's entry point; returns an `int` exit code. |
| **`#include`** | Preprocessor directive pulling in a header/library. |
| **`std::cout` / `<<`** | The standard output stream / the insertion operator. |
| **`std::format`** | Builds a formatted string from `{}` placeholders (C++20). |
| **Format spec** | The mini-language after `:` (`{:.4f}`, `{:>8}`, `{:#x}`, …). |
| **Namespace (`std`)** | The standard library's naming scope. |
| **Translation unit** | One source file after preprocessing. |
| **Object code / linking** | Compiled `.o` output / combining objects into an executable. |
| **Undefined behaviour (UB)** | Code whose behaviour the standard doesn't define (Chapter 30). |
| **Zero-overhead abstraction** | High-level code costing no more than hand-written low-level code. |

### What's next

You can build, run, and format output like a scientist. Now for real data. **[Ch.2 — Types, Initialization & `const`](#chapter-2--types-initialization--const)** introduces C++'s value types and the (many) ways to initialize them, and **[Ch.3 — Floating-Point & Numeric Types](#chapter-3--floating-point--numeric-types)** tackles the number representation every computational scientist must understand deeply.

[↑ back to top](#chapter-1--getting-started--the-c-toolchain)


---

## Chapter 2 — Types, Initialization & `const`

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.1 — Getting Started](#chapter-1--getting-started--the-c-toolchain)

**Learning objectives** — after this chapter you will be able to:

- Use C++'s fundamental types, including the integer family and fixed-width types.
- Reason about signed vs unsigned, type sizes, and numeric limits.
- Choose the right initialization form and avoid narrowing.
- Distinguish `const`, `constexpr`, and `auto`, and use them idiomatically.

**In this chapter**

- [2.1 Fundamental types and the integer family](#21-fundamental-types-and-the-integer-family)
- [2.2 Signed, unsigned, and numeric limits](#22-signed-unsigned-and-numeric-limits)
- [2.3 Fixed-width integers](#23-fixed-width-integers)
- [2.4 Characters and strings](#24-characters-and-strings)
- [2.5 Initialization and narrowing](#25-initialization-and-narrowing)
- [2.6 `auto` type deduction](#26-auto-type-deduction)
- [2.7 `const` and `constexpr`](#27-const-and-constexpr)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-typed-event) · Glossary · What's next

---

### 2.1 Fundamental types and the integer family

C++ is **statically typed**: every value has a type fixed at compile time. The fundamental types you'll use most:

```cpp
int    i = 42;       // integer (typically 32-bit)
double d = 3.14;     // 64-bit floating-point — the scientific default
bool   b = true;     // true / false
char   c = 'A';      // a single byte
```

Integers come in a *family* of sizes. Their exact widths aren't fixed by the standard (only minimums), so query them with `sizeof` (in bytes):

```cpp
// sizeof: char=1 short=2 int=4 long=8 longlong=8   (typical 64-bit Linux)
```

| Type | Typical size | Typical range (signed) |
|------|-------------|------------------------|
| `char` | 1 byte | −128 … 127 |
| `short` | 2 bytes | ±32 767 |
| `int` | 4 bytes | ±2.1 × 10⁹ |
| `long` | 8 bytes | ±9.2 × 10¹⁸ |
| `long long` | 8 bytes | ±9.2 × 10¹⁸ |

Floating-point: **`double`** (64-bit, ~15–16 digits — the numerical default), **`float`** (32-bit, ~7 digits — half the memory, used on huge datasets/GPUs), and `long double` (extended precision). When you write `42` its type is `int`; `3.14` is `double`. Those are the everyday defaults; the others you opt into deliberately.

> ⚠️ **Gotcha** — `int` is typically 32-bit, so its maximum is about **2.1 billion**. In scientific code that counts events, samples, or array indices this overflows easily (a detector records billions of hits). When a count might exceed ~2×10⁹, use a 64-bit type (`long`, `std::int64_t`, or `std::size_t` for sizes). Signed overflow is **undefined behaviour** (Chapter 3) — a silent, dangerous bug.

### 2.2 Signed, unsigned, and numeric limits

Every integer type has a **signed** (default) and **unsigned** variant. Unsigned types can't hold negatives but double the positive range:

```cpp
int      s;   // signed:   about [-2.1e9, 2.1e9]
unsigned u;   // unsigned: [0, 4.29e9]
```

Query exact ranges (and much more) with **`std::numeric_limits<T>`** from `<limits>`:

```cpp
#include <limits>
// int:  [-2147483648, 2147483647]
// uint: [0, 4294967295]
// double: max=1.798e+308  eps=2.220e-16  inf=inf
```

`numeric_limits` gives `min()`, `max()`, `epsilon()` (machine epsilon, Chapter 3), `infinity()`, and more — indispensable when you need to know whether a value fits, or how much precision a type has.

> ⚠️ **Gotcha — signed/unsigned mixing.** Comparing or arithmetic between signed and unsigned converts the *signed* value to unsigned, which flips negatives into huge positives. `-1 < 1u` is **false**! This causes subtle bugs, especially in loop conditions (`for (int i = 0; i < v.size(); ++i)` mixes `int` and `size_t`). Prefer signed integers for arithmetic (to get sane behaviour and let sanitizers catch overflow), and match `std::size_t` for sizes/indices. Compile with `-Wall` to catch `-Wsign-compare` warnings.

### 2.3 Fixed-width integers

Because `int`/`long` sizes vary across platforms, portable and *reproducible* scientific code uses the **fixed-width integer types** from `<cstdint>`, which guarantee an exact bit width:

```cpp
#include <cstdint>
std::int32_t  a   = 100;              // exactly 32-bit signed
std::int64_t  big = 9'000'000'000;    // exactly 64-bit signed
std::uint32_t u   = 4'000'000'000u;   // exactly 32-bit unsigned
std::size_t   n   = 1000;             // unsigned; the type of sizes/indices
```

The `'` digit separators (`9'000'000'000`) are cosmetic — the compiler ignores them — but make large numbers readable.

> 💡 **Idiom** — For data that crosses machines or files (event counts, serialized records, reproducible simulations), prefer fixed-width types (`std::int64_t`, `std::uint32_t`). Use plain `int` for small local loop counters, and **`std::size_t`** for sizes and container indices (it's what `.size()` returns). This discipline matters when a result must be bit-for-bit reproducible across a compute grid.

### 2.4 Characters and strings

A **`char`** is a single byte — and *is an integer* (its numeric value is the character code):

```cpp
char c = 'A';
// static_cast<int>(c) is 65   ('A' has code 65)
```

For text, use **`std::string`** (from `<string>`), a growable, owning sequence of characters:

```cpp
#include <string>
std::string name = "muon";
// name.size() is 4, name[0] is 'm'
```

`std::string` manages its own memory (Chapter 11's RAII in action), grows as needed, and provides `.size()`, indexing `name[i]`, concatenation with `+`, and much more. Prefer it over C-style `char*` strings, which are error-prone. (`std::string_view`, a cheap non-owning view, comes in Chapter 22.)

### 2.5 Initialization and narrowing

C++ has, notoriously, several ways to initialize a variable:

```cpp
int a = 42;      // copy initialization  (=)
int b(42);       // direct initialization (parentheses)
int c{42};       // brace initialization  {} — "uniform initialization"
```

They usually mean the same thing, but **brace initialization `{}` has one crucial safety advantage: it forbids narrowing conversions** — silent, lossy conversions like `double`→`int`:

```cpp
double d = 3.9;
int a(d);        // OK: silently truncates to 3  (dangerous — no warning)
int b{d};        // narrowing → the compiler complains
```

Compiling `int b{d}` yields:

```text
warning: narrowing conversion of 'd' from 'double' to 'int' [-Wnarrowing]
```

The parenthesis/`=` forms silently drop the `.9`; the brace form catches it (a warning here, a hard error under `-Werror`). For scientific code, silently truncating a `double` to an `int` is exactly the bug that corrupts results.

> 💡 **Idiom** — **Prefer brace initialization `{}`** for its narrowing protection and uniformity (it works for scalars, arrays, and objects — Chapter 9). Use `=` for simple, obviously-safe scalar assignments where it reads more naturally. When you *mean* to truncate, say so explicitly with `static_cast<int>(d)` — never rely on silent conversion.

### 2.6 `auto` type deduction

When the type is obvious from the initializer, **`auto`** lets the compiler deduce it:

```cpp
auto energy = 125.0;   // deduced as double
auto count  = 3;       // deduced as int
auto name   = "muon";  // deduced as const char* (a C string, not std::string!)
```

`auto` is *not* dynamic typing — the type is still fixed and checked at compile time; you just didn't spell it out. It shines with verbose types (iterators, template results — Chapters 16, 19) where the full type is painful to write.

But `auto` **drops references and top-level `const` by default**, so it *copies*:

```cpp
std::string big = "some data";
auto        copy = big;      // COPIES the whole string
const auto& ref  = big;      // binds a reference — no copy
```

> ⚠️ **Gotcha** — `auto x = bigContainer;` silently **copies** an entire vector/string/large object — a common, invisible performance bug. To observe without copying, use **`const auto&`**; to modify in place, **`auto&`**. This value-vs-reference distinction (Chapter 6) is central to C++ performance, and `auto` hides it unless you add the `&`.

### 2.7 `const` and `constexpr`

Two keywords make values immutable, but at different times:

- **`const`** — "won't change after initialization." The value may be computed at *runtime*, but is then read-only.
- **`constexpr`** — "a *compile-time* constant." Stronger: computable during compilation, so usable where the language requires a constant (array sizes, template arguments).

```cpp
const double     proton_mass  = 0.938272;      // GeV; runtime const, read-only
constexpr double speed_of_light = 299792458.0; // compile-time constant
constexpr int    samples = 1000 * 1000;        // computed at compile time → 1000000
```

> 💡 **Idiom** — **Reach for `const` by default** — mark immutable everything that doesn't need to change. Const-correctness makes code easier to reason about, prevents accidental mutation, and enables optimizations. Use **`constexpr`** for true constants (physical constants, table sizes) so they cost nothing at runtime and can drive compile-time computation (Chapter 26). "`const` unless you need mutability" is a hallmark of good C++.

> ⚙️ **Under the hood** — A `constexpr` value is baked into the program at compile time — uses of it become literal constants in the machine code; it may not exist as a runtime variable at all. A `const` runtime value does occupy storage, but the compiler knows it never changes, so it can cache it in a register and skip re-reads. Both help the optimizer; `constexpr` additionally enables compile-time computation (Chapter 26) — which scientific code uses for lookup tables and derived constants.

---

### Summary

- Fundamental types: the **integer family** (`char`/`short`/`int`/`long`/`long long`) and floating-point (**`double`** the scientific default, `float`, `long double`); query sizes with `sizeof`, ranges with **`std::numeric_limits<T>`**.
- Integers are **signed** (default) or **unsigned**; beware **signed/unsigned mixing** (negatives become huge). Prefer signed arithmetic; `std::size_t` for sizes.
- Use **fixed-width integers** (`std::int64_t`, `std::uint32_t`) for portable, reproducible data; `int`'s ~2.1-billion limit overflows easily.
- A **`char`** is a 1-byte integer; use **`std::string`** for text (owning, growable).
- Prefer **brace initialization `{}`** — it forbids silent **narrowing**. Cast explicitly (`static_cast`) when you mean to convert.
- **`auto`** deduces the type but **copies** by default — use `const auto&`/`auto&` to avoid copies.
- **`const`** = immutable (runtime); **`constexpr`** = compile-time constant. Prefer `const` by default.

### Self-check quiz

1. Why prefer `std::int64_t` over `int` for an event counter?
   <details><summary>Answer</summary>`int` is typically 32-bit (max ~2.1 billion), which counts can exceed; `std::int64_t` guarantees 64 bits and portable, reproducible width across platforms.</details>
2. Why is `-1 < 1u` false?
   <details><summary>Answer</summary>Mixing signed and unsigned converts the signed `-1` to unsigned, wrapping it to a huge value (≈4.29e9), which is not less than `1`. Avoid signed/unsigned mixing.</details>
3. What does brace init `int b{d}` do that `int b(d)` doesn't?
   <details><summary>Answer</summary>It rejects narrowing conversions (e.g. `double`→`int`) with a warning/error, whereas `()`/`=` silently truncate.</details>
4. Why can `auto x = bigVector;` be a performance bug?
   <details><summary>Answer</summary>`auto` deduces the value type and copies the whole vector. Use `const auto&` to bind a reference and avoid the copy.</details>
5. What's the difference between `const` and `constexpr`?
   <details><summary>Answer</summary>`const` is read-only after initialization (value may be runtime-computed); `constexpr` is a compile-time constant, usable where the language needs one (array sizes, template args).</details>

### Exercises

**Exercise 2.1 — Type limits (guided).** Print the max of `int`, `long`, and `double` (the last in scientific notation).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <limits>
int main() {
    std::cout << std::format("int  max = {}\n", std::numeric_limits<int>::max());
    std::cout << std::format("long max = {}\n", std::numeric_limits<long>::max());
    std::cout << std::format("double max = {:.3e}\n", std::numeric_limits<double>::max());
}
```

Output:
```text
int  max = 2147483647
long max = 9223372036854775807
double max = 1.798e+308
```

**Why this works:** `std::numeric_limits<T>::max()` gives each type's largest value. The difference between `int`'s ~2.1 billion and `long`'s ~9.2 quintillion is exactly why type choice matters for large counts.

</details>

**Exercise 2.2 — Constants.** Compute the number of seconds in a year as a `constexpr`, and show integer vs floating division.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    constexpr long seconds_per_year = 365L * 24 * 60 * 60;
    std::cout << std::format("{}\n", seconds_per_year);   // 31536000
    std::cout << std::format("{} {}\n", 7/2, 7.0/2);       // 3 3.5
}
```

Output:
```text
31536000
3 3.5
```

**Why this works:** `365L * 24 * 60 * 60` is all constants, computed at compile time into a `constexpr long` (using `L` to keep it 64-bit safe). Note `7/2` is **integer division** = 3 (remainder discarded) while `7.0/2` = 3.5 — a distinction that causes real numerical bugs (Chapter 3).

</details>

**Exercise 2.3 — Safe conversion.** You have `double x = 2.7;` and want the truncated integer part *intentionally*, with no narrowing warning.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
int main() {
    double x = 2.7;
    int n = static_cast<int>(x);   // explicit, intentional truncation → 2
    std::cout << n << "\n";
}
```

**Why this works:** `static_cast<int>(x)` states "I deliberately convert `double` to `int`," so there's no narrowing warning and the intent is documented. Silent truncation via `int n = x;` would be a code smell.

</details>

**Exercise 2.4 — A char is a number.** Print the character `'Z'` and its numeric code, then the character three positions later in the alphabet.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    char z = 'Z';
    std::cout << std::format("'{}' = {}\n", z, static_cast<int>(z));   // 90
    char shifted = 'A' + 3;                                             // arithmetic on chars
    std::cout << std::format("'A'+3 = '{}'\n", shifted);               // 'D'
}
```

Output:
```text
'Z' = 90
'A'+3 = 'D'
```

**Why this works:** a `char` holds an integer code (`'Z'` is 90), so arithmetic works: `'A' + 3` is the code for `'D'`. This is why character ranges (`c >= 'a' && c <= 'z'`) and case conversions work with plain arithmetic.

</details>

### Chapter project: a typed event

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–2. We replace v0's hard-coded numbers with real, typed physics: a particle's energy and momentum, and its invariant mass. (No classes yet — Chapter 9 — so plain variables.)

**Goal.** From energy and momentum components, compute the momentum magnitude and invariant mass, formatted cleanly.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>

int main() {
    // One particle "event", modelled as typed variables (Ch.9 makes this a real type)
    const double energy = 91.2;                       // total energy, GeV
    const double px = 30.0, py = -40.0, pz = 50.0;    // momentum components, GeV/c

    const double p_mag    = std::sqrt(px*px + py*py + pz*pz);
    const double inv_mass = std::sqrt(energy*energy - p_mag*p_mag);  // E^2 = p^2 + m^2

    std::cout << "=== Monte Carlo Analysis Toolkit v1 ===\n";
    std::cout << std::format("{:<15}: {:.2f} GeV\n",     "Energy",         energy);
    std::cout << std::format("{:<15}: {:.4f} GeV/c\n",   "|momentum|",     p_mag);
    std::cout << std::format("{:<15}: {:.4f} GeV/c^2\n", "Invariant mass", inv_mass);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v1 ===
Energy         : 91.20 GeV
|momentum|     : 70.7107 GeV/c
Invariant mass : 57.5972 GeV/c^2
```

**Commentary.**
- Every quantity is a `const double` — immutable measured values, marked `const` by default (§2.7). They can't be accidentally overwritten mid-calculation.
- `p_mag = sqrt(30² + 40² + 50²) = sqrt(5000) ≈ 70.7107`; the invariant mass follows from `E² = p² + m²`, so `m = sqrt(E² − |p|²) ≈ 57.5972` GeV/c² — a real (simplified) particle-physics computation.
- `{:<15}` left-aligns the labels; the display precision (`{:.4f}`) is separate from the full `double` stored precision (Chapter 3 explains why that matters).
- These loose variables describing *one* particle are a smell we cure in Chapter 9 with a `Particle` type. For now, typed variables + `<cmath>` suffice.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`int` / `double`** | Integer / 64-bit floating-point (the scientific default). |
| **Integer family** | `char`/`short`/`int`/`long`/`long long`, increasing size. |
| **Signed / unsigned** | With / without negatives (unsigned doubles the positive range). |
| **`sizeof` / `std::numeric_limits`** | Type size in bytes / a type's range, epsilon, etc. |
| **Fixed-width integer** | `std::int32_t`/`int64_t`/… — exact, portable width. |
| **`std::size_t`** | Unsigned type for sizes and indices. |
| **`std::string`** | An owning, growable text type. |
| **Brace initialization `{}`** | Uniform init that forbids narrowing. |
| **`auto`** | Compile-time type deduction (copies unless `&`). |
| **`const` / `constexpr`** | Immutable (runtime) / compile-time constant. |

### What's next

You can declare typed values — but scientific computing lives and dies by *floating-point*. **[Ch.3 — Floating-Point & Numeric Types](#chapter-3--floating-point--numeric-types)** covers IEEE 754, precision and rounding, `NaN`/`inf`, catastrophic cancellation, and integer-overflow UB — the number knowledge every computational scientist needs before trusting a result.

[↑ back to top](#chapter-2--types-initialization--const)


---

## Chapter 3 — Floating-Point & Numeric Types

> **Level:** Beginner → Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.2 — Types & Initialization](#chapter-2--types-initialization--const)

**Learning objectives** — after this chapter you will be able to:

- Explain why floating-point is inexact, and why `double` beats `float` for accuracy.
- Compare floating-point values *correctly* (absolute and relative tolerance).
- Detect and handle `NaN` and infinity.
- Avoid catastrophic cancellation — and use compensated summation to fight it.
- Recognise integer-overflow undefined behaviour.

**In this chapter**

- [3.1 Why floating-point is inexact](#31-why-floating-point-is-inexact)
- [3.2 `float` vs `double`](#32-float-vs-double)
- [3.3 Comparing floating-point values](#33-comparing-floating-point-values)
- [3.4 NaN and infinity](#34-nan-and-infinity)
- [3.5 The `<cmath>` toolbox](#35-the-cmath-toolbox)
- [3.6 Catastrophic cancellation and compensated summation](#36-catastrophic-cancellation-and-compensated-summation)
- [3.7 Integer overflow: UB vs wraparound](#37-integer-overflow-ub-vs-wraparound)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-floating-point-correct-mean) · Glossary · What's next

---

### 3.1 Why floating-point is inexact

No topic matters more to a computational scientist. Your entire result rests on floating-point arithmetic, and if you don't understand its limits you *will* publish a wrong number someday.

A `double` follows **IEEE 754**: 64 bits split into a **sign** (1), an **exponent** (11), and a **mantissa** (52). It represents a number as roughly *sign × mantissa × 2^exponent* — a *binary* fraction. The catch: just as `1/3` has no exact *decimal* form (0.3333…), most *decimal* fractions have no exact *binary* one. `0.1` is one — a repeating binary fraction, stored as the nearest representable value, slightly off.

```cpp
#include <iostream>
#include <format>
int main() {
    double s = 0.1 + 0.2;
    std::cout << std::format("0.1 + 0.2 = {:.17f}\n", s);
    std::cout << std::format("(0.1+0.2 == 0.3) is {}\n", (s == 0.3));
}
```

Output:

```text
0.1 + 0.2 = 0.30000000000000004
(0.1+0.2 == 0.3) is false
```

`0.1 + 0.2` is **not** `0.3` — it's `0.30000000000000004`. Each of `0.1`, `0.2`, `0.3` is stored slightly wrong and the errors don't cancel. This is not a C++ or CPU bug; it's finite binary floating-point, identical in Python, Fortran, and every IEEE-754 language.

### 3.2 `float` vs `double`

A `double` holds ~**15–16** significant decimal digits; a `float` (32-bit) only ~**7**. That difference compounds catastrophically when you accumulate. Watch what happens adding `0.1` a million times in each:

```cpp
float  fsum = 0.0f;
double dsum = 0.0;
for (int i = 0; i < 1'000'000; ++i) { fsum += 0.1f; dsum += 0.1; }
// float sum  = 100958.3438  (should be 100000!)
// double sum = 100000.0000
```

The **`float` result is off by nearly 1000** — its 7 digits ran out and each addition compounded the error. The `double` stayed exact to display precision. This is why numerical code defaults to `double`.

> 💡 **Idiom** — Use **`double`** as your default for scientific computing — its ~16 digits absorb accumulated rounding far better than `float`'s ~7. Reach for `float` only to *halve memory/bandwidth* on huge datasets or GPUs where you've confirmed the reduced precision is acceptable (and even then, accumulate in `double`). The smallest gap between 1.0 and the next double — **machine epsilon** — is about `2.22e-16`; for `float` it's ~`1.2e-7`.

### 3.3 Comparing floating-point values

Since values are approximate, **never compare floating-point numbers with `==`**. Computations that *should* be equal can differ in the last bits. Test whether they're *close enough* — within a **tolerance**:

```cpp
double s = 0.1 + 0.2;
bool close = std::fabs(s - 0.3) < 1e-9;      // ABSOLUTE tolerance → true
```

`std::fabs` (from `<cmath>`) is floating-point absolute value. But an *absolute* tolerance fails for values of very different magnitudes (a tolerance of `1e-9` is meaningless when comparing numbers around `1e12`). Then use a **relative** tolerance:

```cpp
auto close = [](double a, double b, double rtol = 1e-9) {
    return std::fabs(a - b) <= rtol * std::max(std::fabs(a), std::fabs(b));
};
// close(1e9, 1e9 + 1.0) → true   (1 part in 1e9 is within rtol)
```

The relative test scales the tolerance to the magnitude of the values — the robust default for scientific comparisons.

> ⚠️ **Gotcha** — Sometimes `==` on floats *appears* to work (you'll see this in the chapter project: a computed mean compares equal to a literal). That's luck — both sides happened to round to the same bits. You **cannot rely on it**, as `0.1 + 0.2 == 0.3` proves. Always use a tolerance. And choose it thoughtfully: too tight and equal-in-theory values fail; too loose and you accept genuinely different ones.

### 3.4 NaN and infinity

IEEE 754 defines special values for exceptional results — and scientific code hits them constantly (a log of zero, a blown-up division, a failed fit):

- **Infinity** (`inf`, `-inf`) — from overflow or division by zero: `1.0 / 0.0`.
- **NaN** ("Not a Number") — from undefined operations: `0.0 / 0.0`, `sqrt(-1.0)`, `log(-1.0)`, `inf - inf`.

```cpp
double inf = 1.0 / 0.0;
double nan = 0.0 / 0.0;
// 1/0 = inf, isinf=true
// 0/0 = -nan, isnan=true
// nan == nan is false          <-- NaN is not even equal to itself
// sqrt(-1) isnan = true
```

Two critical facts:

- **`NaN` is not equal to anything, including itself** — `nan == nan` is **`false`**. That's actually the by-hand way to detect it (`x != x`), but the clear way is **`std::isnan(x)`** (and `std::isinf(x)`).
- NaN **propagates**: any arithmetic with a NaN yields NaN. One bad value silently poisons an entire calculation — a sum of a million energies becomes NaN if a single one is NaN.

> ⚠️ **Gotcha** — A single NaN in your dataset turns a mean, a fit result, or a histogram entry into NaN — often *without a crash*. Scientific pipelines must check for NaN/inf at boundaries (after reading data, after risky operations) with **`std::isfinite(x)`** (true only for normal, non-NaN, non-inf values). A silent NaN that reaches a plot is a classic way to waste a week.

### 3.5 The `<cmath>` toolbox

`<cmath>` provides the mathematical functions numerical code needs, all on (and returning) floating-point:

```cpp
std::sqrt(2.0);        // 1.4142135623730951
std::cbrt(27.0);       // 3.0   (cube root)
std::pow(2.0, 10.0);   // 1024.0
std::exp(1.0);         // e ≈ 2.71828
std::log(x); std::log10(x); std::log2(x);   // natural / base-10 / base-2
std::sin(x); std::cos(x); std::atan2(y, x); // trig (atan2 handles quadrants)
std::hypot(3.0, 4.0);  // 5.0   — sqrt(x^2+y^2) WITHOUT intermediate overflow
std::abs(-3.5);        // 3.5   (std::abs is overloaded for floats; std::fabs is the C name)
std::floor(x); std::ceil(x); std::round(x);  // rounding modes
```

Prefer these over hand-rolled equivalents: `std::hypot` avoids overflow in `x²+y²`, `std::atan2(y,x)` gets the angle's quadrant right, and library implementations are correctly rounded and often faster than naive code.

### 3.6 Catastrophic cancellation and compensated summation

The most insidious numerical error: **subtracting two nearly-equal numbers destroys precision**. The leading digits cancel, leaving only the (already-imprecise) trailing digits, magnified into garbage:

```cpp
double a = 1e16 + 1.0;
double b = 1e16;
// (a - b) = 0     — should be 1!
```

The answer should be `1`, but it's **`0`** — because `1e16 + 1` can't be represented (doubles near 10¹⁶ have gaps larger than 1), so the `+ 1` was lost *before* the subtraction. Related is **accumulation error**: summing many values, the running total grows large and small additions lose precision. **Kahan (compensated) summation** fixes this by tracking a running correction term:

```cpp
double sum = 0.0, c = 0.0;             // c accumulates the lost low-order bits
for (double x : data) {
    double y = x - c;
    double t = sum + y;
    c = (t - sum) - y;                 // recover what rounding dropped
    sum = t;
}
```

Summing `0.1` ten million times shows the payoff:

```text
exact = 1000000.0000000000
naive = 999999.9998389754  (err -1.61e-04)
kahan = 1000000.0000000000  (err  0.00e+00)
```

Naive summation **drifts by 1.6×10⁻⁴**; Kahan is *exact*. For a physics analysis summing millions of weights or energies, that error is the difference between a right and a wrong result.

> ⚙️ **Under the hood** — Floating-point numbers are *denser* near zero and *sparser* for large magnitudes (the gap between representable values grows with the exponent). Near 10¹⁶, consecutive doubles are ~2 apart, so `1e16 + 1` rounds back to `1e16`. Adding a small number to a huge one silently drops it — the reason order of operations matters in scientific sums (add small terms first, sort by magnitude, or use Kahan). The standard library's `std::reduce` (Chapter 18) and numerical libraries offer accurate summation so you rarely hand-write Kahan — but you must know *why* it exists.

### 3.7 Integer overflow: UB vs wraparound

Integers overflow too, and C++ treats signed and unsigned differently — a distinction with teeth:

- **Signed overflow is *undefined behaviour*** (Chapter 30). `int` at its max plus one is UB — the compiler may *assume it never happens* and optimize accordingly, producing bizarre results. Never rely on signed wraparound.
- **Unsigned overflow *wraps around*** (well-defined modular arithmetic):

```cpp
std::uint32_t u = 0;
u = u - 1;          // wraps to 4294967295  (2^32 - 1)
```

`0u - 1` wraps to `2³² − 1` — *defined*, but still a bug magnet: an unsigned loop counter decremented past zero becomes gigantic (the reverse-loop trap from Chapter 5).

> ⚠️ **Gotcha** — Because signed overflow is UB, **`-fsanitize=undefined`** (UBSan, Chapter 33) can *catch* it at runtime during testing — strongly recommended for scientific code, where an overflowing index or accumulator corrupts results silently. Prefer signed types for arithmetic (to get UBSan's help and avoid unsigned-wraparound surprises), reserving unsigned for genuine bit-manipulation and sizes.

---

### Summary

- Floating-point is **inexact**: `0.1 + 0.2 != 0.3`. **`double`** (~16 digits) hugely outperforms **`float`** (~7) when accumulating — default to `double`.
- **Never compare floats with `==`** — use an **absolute** (`|a-b| < tol`) or, for differing magnitudes, a **relative** tolerance.
- **`NaN`** (from `0/0`, `sqrt(-1)`) equals nothing (even itself) and **propagates**; **`inf`** from overflow/`x/0`. Test with **`std::isnan`/`isinf`/`isfinite`**; guard data boundaries.
- `<cmath>` gives correctly-rounded math (`sqrt`, `exp`, `log`, `hypot`, `atan2`, …) — prefer it to hand-rolled formulas.
- **Catastrophic cancellation** destroys precision (`(1e16+1)-1e16 == 0`); **Kahan summation** recovers accuracy when summing large datasets (naive drifts 1.6e-4 over 10⁷ adds; Kahan is exact).
- **Signed integer overflow is UB** (catchable with UBSan); **unsigned overflow wraps**.

### Self-check quiz

1. Why default to `double` over `float` in numerical code?
   <details><summary>Answer</summary>`double` has ~16 significant digits vs `float`'s ~7, so accumulated rounding error is far smaller — as the million-add example shows (`float` drifted by ~1000, `double` stayed exact).</details>
2. When is a *relative* tolerance better than an *absolute* one?
   <details><summary>Answer</summary>When comparing values of large or very different magnitudes: a fixed absolute tolerance (`1e-9`) is meaningless near `1e12`. A relative tolerance scales to the values' size.</details>
3. How do you detect a `NaN`, and why is `nan == nan` false?
   <details><summary>Answer</summary>Use `std::isnan(x)`. NaN compares unequal to everything including itself by IEEE 754, so `==` can't detect it (though `x != x` being true is a hand check).</details>
4. What does Kahan summation fix, and roughly how?
   <details><summary>Answer</summary>Loss of precision when accumulating many values into a growing sum. It tracks a compensation term capturing the low-order bits dropped by each rounding, adding them back — keeping the sum accurate.</details>
5. What's the difference between signed and unsigned integer overflow?
   <details><summary>Answer</summary>Signed overflow is undefined behaviour (compiler may assume it can't happen); unsigned overflow is defined and wraps modulo 2^N.</details>

### Exercises

**Exercise 3.1 — Tolerance comparison (guided).** Check whether `std::sqrt(2.0) * std::sqrt(2.0)` equals `2.0`, both with `==` and with a tolerance.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
int main() {
    double x = std::sqrt(2.0) * std::sqrt(2.0);
    std::cout << std::format("x = {:.17f}\n", x);
    std::cout << std::format("x == 2.0     : {}\n", (x == 2.0));
    std::cout << std::format("close to 2.0 : {}\n", std::fabs(x - 2.0) < 1e-12);
}
```

Output (representative):
```text
x = 2.00000000000000044
x == 2.0     : false
close to 2.0 : true
```

**Why this works:** `sqrt(2)` is irrational and rounded; squaring gives `2.0000…044`, so `==` is `false`. The tolerance test correctly reports agreement to within rounding.

</details>

**Exercise 3.2 — Guard against NaN.** Report whether `double x = std::log(-1.0);` is safe to use.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
int main() {
    double x = std::log(-1.0);          // undefined → NaN
    std::cout << std::format("x = {}, finite = {}\n", x, std::isfinite(x));
}
```

Output:
```text
x = -nan, finite = false
```

**Why this works:** `log` of a negative is NaN; `std::isfinite(x)` is `false` for NaN (and ±inf) — the right guard before trusting a computed value.

</details>

**Exercise 3.3 — Compensated sum.** Sum `0.1` a million times naively and with Kahan; print both and their error from the exact `100000.0`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    const int N = 1'000'000;
    double naive = 0.0;
    for (int i = 0; i < N; ++i) naive += 0.1;

    double sum = 0.0, c = 0.0;
    for (int i = 0; i < N; ++i) { double y = 0.1 - c; double t = sum + y; c = (t - sum) - y; sum = t; }

    std::cout << std::format("naive = {:.10f} (err {:.2e})\n", naive, naive - 100000.0);
    std::cout << std::format("kahan = {:.10f} (err {:.2e})\n", sum,   sum   - 100000.0);
}
```

Output (representative):
```text
naive = 100000.0000013329 (err 1.33e-06)
kahan = 100000.0000000000 (err 0.00e+00)
```

**Why this works:** naive summation accumulates rounding error (here ~1.3e-6, and it grows with the number of terms); Kahan's compensation term recaptures the dropped bits, giving the exact result. For large scientific sums this is the difference between accurate and drifting totals.

</details>

**Exercise 3.4 — Overflow-safe magnitude.** Compute the magnitude of a vector `(3e200, 4e200)` two ways — naive `sqrt(x²+y²)` and `std::hypot` — and see which overflows.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
int main() {
    double x = 3e200, y = 4e200;
    double naive = std::sqrt(x*x + y*y);   // x*x = 9e400 → overflows to inf!
    double safe  = std::hypot(x, y);       // 5e200, no overflow
    std::cout << std::format("naive = {}\n", naive);
    std::cout << std::format("hypot = {:.1e}\n", safe);
}
```

Output:
```text
naive = inf
hypot = 5.0e+200
```

**Why this works:** `x*x` = `9e400` exceeds `double`'s max (~1.8e308), overflowing to `inf` — so the naive formula gives `inf`. `std::hypot` computes the magnitude *without* squaring into the overflow range, giving the correct `5e200`. Always prefer `std::hypot` for 2-D magnitudes.

</details>

### Chapter project: a floating-point-correct mean

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–3. We compute the mean of measured energies and learn — with real output — why `==` can't be trusted. (No loops yet — Chapter 5 — so five values by hand.)

**Goal.** Compute the mean of five energies and compare it to an expected value naively and with a tolerance.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
int main() {
    // Five measured energies (GeV), summed by hand (loops arrive in Ch.5)
    const double e1 = 91.1, e2 = 91.3, e3 = 90.9, e4 = 91.2, e5 = 91.0;
    const double mean = (e1 + e2 + e3 + e4 + e5) / 5.0;

    const double expected = 91.1;
    const bool exact  = (mean == expected);
    const bool agrees = std::fabs(mean - expected) < 1e-9;

    std::cout << "=== Monte Carlo Analysis Toolkit v2 ===\n";
    std::cout << std::format("Mean energy      : {:.15f} GeV\n", mean);
    std::cout << std::format("mean == 91.1      : {}\n", exact);
    std::cout << std::format("agrees (tol 1e-9) : {}\n", agrees);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v2 ===
Mean energy      : 91.099999999999994 GeV
mean == 91.1      : true
agrees (tol 1e-9) : true
```

**Commentary.**
- The mean is stored as `91.099999999999994`, **not** exactly `91.1` (§3.1). Yet `mean == 91.1` prints **`true`** here — because the literal `91.1` rounds to the *same* nearest double as the computed mean. **This is luck.** Change the inputs and it can flip to `false` (as `0.1 + 0.2 == 0.3` does). The lesson: *never* depend on `==` for floats — the tolerance test (`agrees`) is the one you trust.
- In Chapter 5 this hand-written sum becomes a loop; in Chapter 18 it becomes `std::reduce`; in Chapter 22 the energies come from a *Monte Carlo simulation*. The floating-point discipline built here — tolerances, NaN guards, compensated sums — carries through all of it, because it's the foundation of trusting any numerical result.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **IEEE 754** | The standard for floating-point (sign/exponent/mantissa). |
| **`double` / `float`** | 64-bit (~16 digits) / 32-bit (~7 digits) floating-point. |
| **Machine epsilon** | Smallest gap between 1.0 and the next value (~2.2e-16 for double). |
| **Absolute / relative tolerance** | `|a-b| < tol` / scaled to magnitude. |
| **`NaN` / `inf`** | Not-a-Number / infinity; test with `isnan`/`isinf`/`isfinite`. |
| **Catastrophic cancellation** | Precision loss subtracting nearly-equal values. |
| **Kahan summation** | Compensated summation that recovers accumulation error. |
| **`std::hypot`** | Overflow-safe `sqrt(x²+y²)`. |
| **Signed overflow** | Undefined behaviour (unlike unsigned wraparound). |

### What's next

You understand the numbers. **[Ch.4 — Operators & Expressions](#chapter-4--operators--expressions)** covers how they combine — arithmetic, bitwise operations, and evaluation-order rules — before **[Ch.5 — Control Flow](#chapter-5--control-flow)** lets the toolkit loop over real datasets.

[↑ back to top](#chapter-3--floating-point--numeric-types)


---

## Chapter 4 — Operators & Expressions

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Floating-Point](#chapter-3--floating-point--numeric-types)

**Learning objectives** — after this chapter you will be able to:

- Use arithmetic, comparison, and logical operators, and short-circuiting.
- Manipulate bit flags — pack many yes/no signals into one integer (detector trigger words).
- Use compound assignment, increment, precedence, and the ternary operator.
- Recognise that evaluation-order surprises can cause undefined behaviour.

**In this chapter**

- [4.1 Arithmetic operators](#41-arithmetic-operators)
- [4.2 Comparison and logical operators](#42-comparison-and-logical-operators)
- [4.3 Bitwise operators and flags](#43-bitwise-operators-and-flags)
- [4.4 Compound assignment and increment](#44-compound-assignment-and-increment)
- [4.5 Precedence, ternary, and evaluation order](#45-precedence-ternary-and-evaluation-order)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-event-selection-logic) · Glossary · What's next

---

### 4.1 Arithmetic operators

The five arithmetic operators, with the integer-division rule from Chapter 3:

```cpp
int a = 17, b = 5;
// a+b=22  a-b=12  a*b=85  a/b=3  a%b=2
```

`a/b` is **integer division** (3, remainder discarded); `a%b` is the remainder (2). Make an operand floating-point for a real quotient: `17.0/5` is `3.4`. The `%` operator (modulo) works only on integers and is invaluable — `i % n` wraps an index into `[0, n)`, `k % 2 == 0` tests evenness, and it drives hashing and periodic boundary conditions in simulations.

```text
a+b=22 a-b=12 a*b=85 a/b=3 a%b=2
17.0/5 = 3.4
```

### 4.2 Comparison and logical operators

Comparisons (`<`, `>`, `<=`, `>=`, `==`, `!=`) produce a `bool`. Logical operators combine them: `&&` (and), `||` (or), `!` (not):

```cpp
int a = 17, b = 5;
// (a>b)=true  (a==b)=false  (a>b && b>0)=true  (a<b || b>0)=true
```

`&&` and `||` **short-circuit**: `a && b` skips `b` if `a` is `false`; `a || b` skips `b` if `a` is `true`. This is both an optimization and a *safety* tool — guard an expensive or unsafe check behind a cheap one:

```cpp
if (index < size && data[index] > threshold) { /* ... */ }
// If index >= size, data[index] is never evaluated → no out-of-bounds read.
```

> ⚠️ **Gotcha** — Remember from Chapter 3: never use `==` on floating-point values. `a == b` is fine for integers and booleans, but for `double`s use a tolerance (`std::fabs(a-b) < tol`). This is the single most common numerical bug for newcomers.

### 4.3 Bitwise operators and flags

Bitwise operators manipulate individual bits: **`&`** (AND), **`|`** (OR), **`^`** (XOR), **`~`** (NOT), and **`<<`** / **`>>`** (shift):

```cpp
// 5&3=1   5|3=7   5^3=6   ~5=-6   1<<4=16   20>>2=5
```

`1 << 4` is `16` (2⁴) — a fast exact power of two; `20 >> 2` is `5` (divide by 4). Their signature use in scientific code is **bit flags**: packing many yes/no signals into one integer — exactly how a **detector trigger word** records which subsystems fired:

```cpp
#include <cstdint>
constexpr std::uint32_t MUON     = 1u << 0;   // bit 0
constexpr std::uint32_t ELECTRON = 1u << 1;   // bit 1
constexpr std::uint32_t JET      = 1u << 2;   // bit 2

std::uint32_t trigger = 0;
trigger |= MUON;                    // SET the muon bit
trigger |= JET;                     // SET the jet bit
// trigger = 0b0101

bool has_muon = (trigger & MUON) != 0;      // TEST a bit  → true
bool has_e    = (trigger & ELECTRON) != 0;  // TEST        → false
trigger ^= MUON;                    // TOGGLE the muon bit off
trigger &= ~JET;                    // CLEAR the jet bit  → trigger = 0b0000
```

Verified:

```text
trigger = 0b0101
has muon?     true
has electron? false
after toggle, has muon? false
after clear jet, trigger = 0b0000
```

The four operations — **set** (`|= FLAG`), **test** (`& FLAG`), **toggle** (`^= FLAG`), **clear** (`&= ~FLAG`) — are the vocabulary of bit manipulation, used everywhere from trigger words to permission masks to compact boolean arrays.

> ⚠️ **Gotcha** — Don't confuse bitwise `&`/`|` with logical `&&`/`||`. `a & b` operates on bits and does *not* short-circuit; `a && b` is a boolean test that does. `if (x & y)` when you meant `if (x && y)` compiles but computes something different — a subtle, real bug.

### 4.4 Compound assignment and increment

Compound assignment combines an operation with assignment — for every arithmetic and bitwise operator:

```cpp
int count = 10;
count += 5;   // count = count + 5  → 15
count *= 2;   // → 30
// also: -=  /=  %=  &=  |=  ^=  <<=  >>=
```

The **increment/decrement** operators `++`/`--` add or subtract one, and their *position* matters in expressions:

```cpp
int y = 3;
int post = y++;   // post-increment: post gets the OLD value (3), then y becomes 4
int pre  = ++y;   // pre-increment:  y becomes 5 first, then pre gets 5
// x=30 y=5 post=3 pre=5
```

> 💡 **Idiom** — For loop counters and iterators, prefer **pre-increment `++it`** over post-increment `it++`. Post-increment must copy the old value to return it; for an `int` the optimizer erases the difference, but for a heavy iterator type (Chapter 19) the copy is real cost. `++it` never copies — the habit to build.

### 4.5 Precedence, ternary, and evaluation order

Operators have **precedence**: `*` and `/` bind tighter than `+` and `-`, so `2 + 3 * 4` is `14`, not `20`. When in doubt, parenthesize. The **ternary** operator `?:` is a compact `if/else` that produces a value, and it chains:

```cpp
int x = 2 + 3 * 4;                                   // 14
double v = 55.0;
const char* band = (v < 10) ? "low" : (v < 100) ? "mid" : "high";   // "mid"
```

> ⚠️ **Gotcha — evaluation order is often unspecified.** C++ does **not** guarantee left-to-right evaluation of a function's arguments or of the two sides of most binary operators. And modifying a variable *and* reading it in the same expression without a sequencing guarantee is **undefined behaviour**: `i = i++ + 1;` and `a[i] = i++;` are UB — the compiler may produce anything. (You saw this live in Chapter 7: calling a stateful function three times inside one `std::format` printed the results *right-to-left* under g++.) Never write expressions where a value is modified and used ambiguously; split them into separate statements.

> ⚙️ **Under the hood** — Leaving evaluation order unspecified lets the compiler reorder work for speed (register allocation, instruction scheduling) — part of C++'s zero-overhead bargain. The price: *you* must not write code whose result depends on an order the standard doesn't fix. The safe rule is one modification of a given object per full expression.

---

### Summary

- Arithmetic `+ - * / %`; `/` is integer division for integers (use a `double` operand for a real quotient); `%` (modulo) is integer-only and widely useful.
- Comparisons yield `bool`; **`&&`/`||` short-circuit** (guard unsafe checks with them). Never `==` on floats.
- **Bitwise** `& | ^ ~ << >>` manipulate bits; the **flag idiom** — set (`|=`), test (`&`), toggle (`^=`), clear (`&= ~`) — packs many booleans into one integer (trigger words, masks). Don't confuse with logical `&&`/`||`.
- **Compound assignment** (`+=`, `&=`, …) and **`++`/`--`** (pre returns new value, post the old; prefer `++it`).
- Mind **precedence** (parenthesize when unclear); the **ternary** `?:` is an expression. **Evaluation order is often unspecified** — modifying and reading a value in one expression is **UB**.

### Self-check quiz

1. What is `17 / 5` and `17 % 5`, and how do you get `3.4`?
   <details><summary>Answer</summary>`17/5` is `3` (integer division), `17%5` is `2`. For `3.4`, make an operand floating-point: `17.0/5`.</details>
2. Given a flags integer, how do you set, test, and clear a specific `FLAG` bit?
   <details><summary>Answer</summary>Set: `x |= FLAG;` Test: `(x & FLAG) != 0`. Clear: `x &= ~FLAG;` (Toggle: `x ^= FLAG;`.)</details>
3. Why does `if (i < n && a[i] > 0)` avoid an out-of-bounds read?
   <details><summary>Answer</summary>`&&` short-circuits: if `i < n` is false, `a[i]` is never evaluated.</details>
4. Why is `a[i] = i++;` dangerous?
   <details><summary>Answer</summary>It reads and modifies `i` in one expression without a sequencing guarantee — undefined behaviour. Split into separate statements.</details>

### Exercises

**Exercise 4.1 — Even/odd and powers (guided).** Print whether 42 is even, and compute 2⁸ two ways (`<<` and by multiplication).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    int n = 42;
    std::cout << std::format("{} is even: {}\n", n, (n % 2 == 0));
    std::cout << std::format("2^8 = {} (shift) = {} (mul)\n", 1 << 8, 256);
}
```

Output:
```text
42 is even: true
2^8 = 256 (shift) = 256 (mul)
```

**Why this works:** `n % 2 == 0` is the standard evenness test. `1 << 8` shifts the bit `1` left eight places, giving `2⁸ = 256` — an exact, fast power of two (valid only for powers of 2, and watch for overflow at large shifts).

</details>

**Exercise 4.2 — Trigger word (bit flags).** Build a trigger with the MUON (bit 0) and MISSING_ET (bit 3) bits set, then report whether it has a muon and whether it has an electron (bit 1).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cstdint>
int main() {
    constexpr std::uint32_t MUON = 1u << 0, ELECTRON = 1u << 1, MISSING_ET = 1u << 3;
    std::uint32_t trig = MUON | MISSING_ET;                 // set two bits at once
    std::cout << std::format("trigger = {:#06b}\n", trig);  // 0b1001
    std::cout << std::format("muon?     {}\n", (trig & MUON) != 0);
    std::cout << std::format("electron? {}\n", (trig & ELECTRON) != 0);
}
```

Output:
```text
trigger = 0b1001
muon?     true
electron? false
```

**Why this works:** `MUON | MISSING_ET` combines bits 0 and 3 into `0b1001`. Testing with `& MUON` finds the muon bit set (`true`); `& ELECTRON` finds bit 1 unset (`false`). This is exactly how a detector's readout encodes which subsystems fired.

</details>

**Exercise 4.3 — Classify with a ternary chain.** Map an energy to `"soft"`, `"medium"`, or `"hard"` (thresholds 10 and 100 GeV) using ternaries.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <string_view>
int main() {
    double e = 250.0;
    std::string_view band = (e < 10.0) ? "soft" : (e < 100.0) ? "medium" : "hard";
    std::cout << band << "\n";   // hard
}
```

**Why this works:** ternaries chain — the `false` branch of one is another ternary, giving a three-way classification as a single expression. (`std::string_view`, Chapter 22, is a cheap non-owning string reference.) For more branches, an `if`/`else if` chain (Chapter 5) is clearer.

</details>

**Exercise 4.4 — Compound assignment pipeline.** Start with `double e = 100.0` and apply, in order: ×1.05 (a 5% correction), −2.0 (a pedestal subtraction), ÷2 (two readouts). Print the result.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    double e = 100.0;
    e *= 1.05;   // 105
    e -= 2.0;    // 103
    e /= 2.0;    // 51.5
    std::cout << std::format("e = {}\n", e);   // 51.5
}
```

Output:
```text
e = 51.5
```

**Why this works:** each compound-assignment step transforms `e` in place — `e *= 1.05` is `e = e * 1.05`. Applying corrections as a sequence of `*=`/`-=`/`/=` is exactly how a calibration chain adjusts a raw detector reading. (Here the arithmetic happens to land on a clean `51.5`; recall from Chapter 3 that many decimals wouldn't.)

</details>

### Chapter project: event-selection logic

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–4. Real analyses *select* events by cuts and read trigger bits. We classify one event using comparisons, logic, and a bit test.

**Goal.** Given an event's energy, momentum magnitude, and trigger word, decide whether it passes a selection: energy above 50 GeV, momentum below 80 GeV/c, **and** the muon trigger bit set.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <cstdint>

int main() {
    const double energy = 91.2;                       // GeV
    const double px = 30.0, py = -40.0, pz = 50.0;    // GeV/c
    const double p_mag = std::sqrt(px*px + py*py + pz*pz);

    constexpr std::uint32_t MUON = 1u << 0;
    const std::uint32_t trigger = MUON | (1u << 2);   // muon + jet fired

    const bool kinematic = (energy > 50.0) && (p_mag < 80.0);
    const bool triggered = (trigger & MUON) != 0;
    const bool selected  = kinematic && triggered;

    std::cout << "=== Monte Carlo Analysis Toolkit — event selection ===\n";
    std::cout << std::format("energy = {:.1f} GeV, |p| = {:.2f} GeV/c\n", energy, p_mag);
    std::cout << std::format("kinematic cut : {}\n", kinematic);
    std::cout << std::format("muon trigger  : {}\n", triggered);
    std::cout << std::format("SELECTED      : {}\n", selected);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit — event selection ===
energy = 91.2 GeV, |p| = 70.71 GeV/c
kinematic cut : true
muon trigger  : true
SELECTED      : true
```

**Commentary.**
- The selection combines a **kinematic cut** (`energy > 50 && p_mag < 80`) with a **trigger requirement** (`trigger & MUON`) — precisely how a physics analysis selects events: kinematic thresholds *and* the right detector signals. Here energy 91.2 > 50, |p| 70.71 < 80, and the muon bit is set, so the event is **selected**.
- `(trigger & MUON) != 0` reads the muon bit out of the packed trigger word (§4.3) — one integer carrying many yes/no detector signals.
- In Chapter 5 we'll run this selection in a *loop* over many events and count how many pass — the first real "analysis." In Chapter 22 the events (and their triggers) will be generated by Monte Carlo.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`/` (integer division)** | Discards the remainder for integer operands. |
| **`%` (modulo)** | Integer remainder; wraps indices, tests parity. |
| **Short-circuit** | `&&`/`||` skipping the second operand when the result is known. |
| **Bitwise `& | ^ ~ << >>`** | Per-bit operations (flags, masks, shifts). |
| **Bit flag idiom** | set `|=`, test `&`, toggle `^=`, clear `&= ~`. |
| **Compound assignment** | `+=`, `&=`, … combine an op with assignment. |
| **Pre/post increment** | `++x` returns the new value; `x++` the old. |
| **Precedence** | The binding order of operators (`*` before `+`). |
| **Ternary `?:`** | A conditional expression producing a value. |
| **Evaluation order** | Often unspecified; modifying+reading a value in one expression is UB. |

### What's next

You can combine values into expressions. **[Ch.5 — Control Flow](#chapter-5--control-flow)** adds decisions and loops — including the range-based `for` — so the toolkit can iterate over a whole dataset of events.

[↑ back to top](#chapter-4--operators--expressions)


---

## Chapter 5 — Control Flow

> **Level:** Beginner &nbsp;·&nbsp; **Prerequisites:** [Ch.4 — Operators](#chapter-4--operators--expressions)

**Learning objectives** — after this chapter you will be able to:

- Branch with `if`/`else` (including the init-statement) and `switch`.
- Write every loop form: `for`, nested `for`, `while`, `do-while`, and range-based `for`.
- Iterate correctly with `std::size_t` indices, in reverse, and over 2-D grids.
- Use `break`/`continue`, convergence loops, and find-first patterns.

**In this chapter**

- [5.1 `if` and `else`](#51-if-and-else)
- [5.2 `switch`](#52-switch)
- [5.3 The `for` loop](#53-the-for-loop)
- [5.4 Nested loops and grids](#54-nested-loops-and-grids)
- [5.5 `while`, `do-while`, and convergence](#55-while-do-while-and-convergence)
- [5.6 The range-based `for`](#56-the-range-based-for)
- [5.7 `break`, `continue`, and reverse iteration](#57-break-continue-and-reverse-iteration)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-dataset-statistics) · Glossary · What's next

---

### 5.1 `if` and `else`

`if` runs a block when a condition is true; `else if` and `else` chain alternatives:

```cpp
int score = 82;
if (score >= 90)      std::cout << "A\n";
else if (score >= 80) std::cout << "B\n";   // ← this runs → "B"
else                  std::cout << "C\n";
```

The condition must be (convertible to) a `bool`. Any nonzero number is "true," which enables a common — and dangerous — shorthand: `if (n)` means `if (n != 0)`. Be explicit (`if (n != 0)`) in numerical code; it reads clearly and avoids the "did they mean `= `or `==`?" ambiguity.

C++17 added an **init-statement**: declare a variable scoped to the `if`, then test it. This keeps temporaries from leaking into the surrounding scope:

```cpp
double energies[] = {91.1, 91.3, 90.9};
if (double m = (energies[0] + energies[1] + energies[2]) / 3.0; m > 91.0) {
    std::cout << std::format("mean {:.2f} passes\n", m);   // m is visible only inside the if
}
```

> ⚠️ **Gotcha** — Always brace your blocks, even one-liners. The infamous bug: `if (x > 0)\n    a();\n    b();` — `b()` looks indented into the branch but runs *unconditionally* (only `a()` is guarded). Braces (`if (x > 0) { a(); b(); }`) make the block explicit and survive later edits. Some teams enforce this with a linter.

### 5.2 `switch`

`switch` branches on an *integral* (or enum, Chapter 9) value. Each `case` needs a **`break`**, or control "falls through" into the next case:

```cpp
int day = 3;
switch (day) {
    case 1: std::cout << "Mon\n"; break;
    case 3: std::cout << "Wed\n"; break;   // ← runs → "Wed"
    default: std::cout << "other\n"; break;
}
```

Deliberate fall-through (grouping cases) is fine, but mark it so the compiler and readers know it's intentional:

```cpp
switch (particle_charge) {
    case -1:
    case  1: std::cout << "charged\n"; break;   // -1 and +1 share this (natural grouping)
    case  0: std::cout << "neutral\n"; break;
    default: std::cout << "unknown\n"; break;
}
```

> ⚠️ **Gotcha** — Forgetting `break` is a classic bug — control falls through and runs the next case too. For *intentional* fall-through of a case *with code*, write **`[[fallthrough]];`** so the compiler doesn't warn. `switch` works only on integral/enum types — never `double` or `std::string` (use `if`/`else if` for those).

### 5.3 The `for` loop

The `for` loop bundles initialization, condition, and update. It's the workhorse of numerical code. Here are the forms you'll write constantly:

```cpp
// Count up
for (int i = 0; i < 5; ++i) std::cout << i << " ";        // 0 1 2 3 4

// Count down with a step
for (int i = 10; i > 0; i -= 2) std::cout << i << " ";    // 10 8 6 4 2
```

Output: `0 1 2 3 4 | 10 8 6 4 2`.

**Indexing an array** is the second essential form. Use **`std::size_t`** for the index — it's the unsigned type sizes come in, and matching it avoids signed/unsigned comparison warnings:

```cpp
double e[] = {91.1, 91.3, 90.9};
for (std::size_t i = 0; i < std::size(e); ++i)
    std::cout << std::format("e[{}]={} ", i, e[i]);       // e[0]=91.1 e[1]=91.3 e[2]=90.9
```

> ⚠️ **Gotcha** — Mixing signed and unsigned in the loop condition is a real trap: `for (int i = 0; i < v.size(); ++i)` compares a signed `int` with an unsigned `size_t`, which the compiler warns about (`-Wsign-compare`) and which misbehaves if `v.size()` exceeds `INT_MAX`. Match types: use `std::size_t i`, or better, the **range-based `for`** (§5.6) when you don't need the index.

### 5.4 Nested loops and grids

Loops nest — the inner loop runs fully for each pass of the outer. This is how you traverse **2-D data**: a matrix, an image, or a detector's grid of cells:

```cpp
int grid[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};
int total = 0;
for (int r = 0; r < 3; ++r)          // outer: rows
    for (int c = 0; c < 3; ++c)      // inner: columns
        total += grid[r][c];
// grid sum = 45
```

Nested loops are everywhere in scientific computing — summing a matrix, convolving an image, iterating pairs of particles. Just remember the cost multiplies: an *n×n* grid means *n²* iterations, so nested loops are where performance (Chapter 33) is won or lost.

> 💡 **Idiom** — For row-major 2-D arrays (C++'s layout), loop with the **row index outermost and column innermost** (as above). This walks memory *sequentially*, which is far friendlier to the CPU cache than the reverse order — a real speedup on large grids (Chapter 33 quantifies it). "Rows outer, columns inner" is a habit worth building for numerical loops.

### 5.5 `while`, `do-while`, and convergence

Use **`while`** when you loop *until a condition*, not a fixed count — the natural shape of iterative numerical methods. Here is Newton's method converging to √2:

```cpp
double x = 1.0;
int iters = 0;
while (std::abs(x*x - 2.0) > 1e-12) {   // loop until close enough
    x = 0.5 * (x + 2.0/x);              // Newton step
    ++iters;
}
// sqrt2 ~= 1.4142135624 in 5 iters
```

The loop runs until the estimate is within tolerance — exactly the "iterate to convergence" pattern behind root-finders, ODE solvers, and optimizers (Chapter 23). **`do-while`** is the same but tests *after* the body, so it always runs at least once — useful for "prompt, then validate" or a solver step you always want to take before checking:

```cpp
int n = 0;
while (n < 3) { std::cout << n << " "; ++n; }   // 0 1 2  (tests before)
```

> ⚠️ **Gotcha** — A convergence loop needs a *guaranteed exit*: a tolerance the method actually reaches, **and** a maximum-iteration cap as a safety net. A method that diverges (or a tolerance tighter than floating-point precision allows, Chapter 3) loops forever. Real numerical code writes `while (error > tol && iters < max_iters)` — never trust convergence blindly.

### 5.6 The range-based `for`

To visit every element of an array or container, the **range-based `for`** is cleaner and safer than an index loop — no bounds, no off-by-one:

```cpp
double energies[] = {91.1, 91.3, 90.9, 91.2, 91.0};
double sum = 0.0;
for (double e : energies) sum += e;                 // "for each e in energies"
// total = 455.5, n = 5   (std::size(energies) gives the length)
```

Choose the loop variable's form deliberately — this is a genuine performance decision:

```cpp
for (double e : data)            { /* a COPY of each element (fine for cheap doubles) */ }
for (const auto& e : data)       { /* const reference: no copy, read-only */ }
for (auto& e : data)             { e *= 2.0; /* mutable reference: modify in place */ }
```

> 💡 **Idiom** — Default to **`for (const auto& x : data)`**. For a container of `double`s the copy is trivial, but for elements like a `Particle` (Chapter 9), a `std::string`, or a big struct, copying each one is real, avoidable cost. Use `auto&` only when you intend to modify elements. Building the `const auto&` habit now pays off across every loop you'll write.

### 5.7 `break`, `continue`, and reverse iteration

**`break`** exits the loop entirely; **`continue`** skips to the next iteration:

```cpp
for (int i = 1; i <= 10; ++i) {
    if (i == 5) break;         // stop the whole loop at 5
    if (i % 2 == 0) continue;  // skip even numbers
    std::cout << i << " ";     // 1 3
}
```

`break` implements **find-first**: stop as soon as you have what you need — the fastest way to locate a matching event:

```cpp
double e[] = {91.1, 91.3, 90.9};
int first_big = -1;
for (std::size_t i = 0; i < std::size(e); ++i)
    if (e[i] > 91.2) { first_big = static_cast<int>(i); break; }
// first index with e>91.2: 1   (stops immediately at index 1)
```

**Reverse iteration** over an unsigned-indexed array needs care, because `std::size_t` can't go below 0 (it wraps, Chapter 3). The safe idiom uses `i-- > 0` in the condition:

```cpp
double e[] = {91.1, 91.3, 90.9};
for (std::size_t i = std::size(e); i-- > 0; )   // i is decremented in the test
    std::cout << e[i] << " ";                    // 90.9 91.3 91.1  (last to first)
```

> ⚠️ **Gotcha — the reverse-loop trap.** The naive reverse loop `for (std::size_t i = size - 1; i >= 0; --i)` is an **infinite loop**: `std::size_t` is unsigned, so `i >= 0` is *always true* — when `i` is 0 and decremented it wraps to a huge number, not −1. Use the `i-- > 0` idiom above, or reverse iterators (Chapter 19), or a signed index if the range is small. This bug is a rite of passage; now you know it.

---

### Summary

- **`if`/`else if`/`else`** branch on `bool`; always brace blocks; C++17's `if (init; cond)` scopes a variable to the branch.
- **`switch`** branches on integral/enum values; each `case` needs `break` (mark intentional fall-through with `[[fallthrough]]`).
- **`for`** counts up/down/by steps; index arrays with **`std::size_t`** (avoid signed/unsigned mixing).
- **Nested loops** traverse 2-D data (*n²* cost); loop **rows-outer, columns-inner** for cache-friendly access.
- **`while`** loops to a condition — the **convergence** pattern (with a tolerance *and* an iteration cap); **`do-while`** runs at least once.
- The **range-based `for`** (`for (const auto& x : data)`) is the clean default; choose copy / `const&` / `&` deliberately.
- **`break`** (find-first / early exit) and **`continue`** (skip); **reverse iteration** over unsigned indices needs the `i-- > 0` idiom.

### Self-check quiz

1. Why prefer `std::size_t` for an array index?
   <details><summary>Answer</summary>It's the unsigned type sizes come in; using it avoids signed/unsigned comparison warnings and misbehaviour when the size exceeds `INT_MAX`. Matching the index type to `.size()` is correct.</details>
2. Why is `for (std::size_t i = n-1; i >= 0; --i)` an infinite loop?
   <details><summary>Answer</summary>`std::size_t` is unsigned, so `i >= 0` is always true; when `i` is 0 and decremented, it wraps to a huge value instead of −1. Use the `i-- > 0` idiom.</details>
3. In a range-based `for`, when do you use `const auto&` vs `auto&` vs a value?
   <details><summary>Answer</summary>`const auto&` for read-only, no-copy (the default, essential for large elements); `auto&` to modify elements in place; a value (copy) only for small cheap types.</details>
4. What two conditions should a convergence `while` loop have?
   <details><summary>Answer</summary>A tolerance the method actually reaches, and a maximum-iteration cap as a safety net against divergence or a too-tight tolerance — e.g. `while (error > tol && iters < max_iters)`.</details>

### Exercises

**Exercise 5.1 — Count passing events (guided).** Count how many energies exceed 91.0 GeV with a range-based `for`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    double energies[] = {91.1, 91.3, 90.9, 91.2, 91.0};
    int passing = 0;
    for (double e : energies)
        if (e > 91.0) ++passing;
    std::cout << std::format("{} events above 91.0 GeV\n", passing);   // 3
}
```

Output:
```text
3 events above 91.0 GeV
```

**Why this works:** the range-based `for` visits each energy; the `if` applies the cut and `++passing` tallies. Three values (91.1, 91.3, 91.2) exceed 91.0 — a physics event count in miniature.

</details>

**Exercise 5.2 — Multiplication table (nested loops).** Print a 3×3 multiplication table using nested `for` loops.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    for (int r = 1; r <= 3; ++r) {
        for (int c = 1; c <= 3; ++c)
            std::cout << std::format("{:3}", r * c);   // width-3 columns
        std::cout << "\n";
    }
}
```

Output:
```text
  1  2  3
  2  4  6
  3  6  9
```

**Why this works:** the outer loop picks a row, the inner loop prints that row's products, then a newline ends the row. `{:3}` right-aligns each number in a 3-wide field for a tidy grid — the same nested pattern used to fill a matrix.

</details>

**Exercise 5.3 — Newton's method (convergence loop).** Use a `while` loop to compute √10 by Newton's method, printing the iteration count.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
int main() {
    double target = 10.0;
    double x = target;                 // initial guess
    int iters = 0;
    while (std::abs(x*x - target) > 1e-12 && iters < 100) {   // tolerance + safety cap
        x = 0.5 * (x + target/x);      // Newton step
        ++iters;
    }
    std::cout << std::format("sqrt({}) = {:.10f} in {} iters\n", target, x, iters);
}
```

Output (representative):
```text
sqrt(10) = 3.1622776602 in 6 iters
```

**Why this works:** each Newton step `x ← ½(x + target/x)` roughly doubles the correct digits, so the loop converges in a handful of iterations. The condition combines a tolerance (`> 1e-12`) with an iteration cap (`iters < 100`) — the safe convergence-loop pattern from §5.5.

</details>

### Chapter project: dataset statistics

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–5. We loop over a *dataset* of events and compute real summary statistics — mean, standard deviation, and range.

**Goal.** Over an array of measured energies, compute the mean, standard deviation, and min/max using loops.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>

int main() {
    double energies[] = {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4};
    const std::size_t n = std::size(energies);

    // Mean (pass 1)
    double sum = 0.0;
    for (double e : energies) sum += e;
    double mean = sum / n;

    // Standard deviation (pass 2 — uses the mean)
    double var = 0.0;
    for (double e : energies) var += (e - mean) * (e - mean);
    var /= n;
    double stddev = std::sqrt(var);

    // Min / max (pass 3)
    double emin = energies[0], emax = energies[0];
    for (double e : energies) {
        if (e < emin) emin = e;
        if (e > emax) emax = e;
    }

    std::cout << "=== Monte Carlo Analysis Toolkit v3 ===\n";
    std::cout << std::format("N events : {}\n", n);
    std::cout << std::format("Mean     : {:.4f} GeV\n", mean);
    std::cout << std::format("Std dev  : {:.4f} GeV\n", stddev);
    std::cout << std::format("Range    : [{:.1f}, {:.1f}] GeV\n", emin, emax);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v3 ===
N events : 7
Mean     : 91.1000 GeV
Std dev  : 0.2000 GeV
Range    : [90.8, 91.4] GeV
```

**Commentary.**
- Three range-based loops compute the three statistics: mean (91.1), spread (σ = 0.2), and range — exactly the summary a physicist reports.
- `std::size(energies)` gives the length safely (no hard-coded `7`), returning a `std::size_t` (Chapter 2). Adding an event needs no change to the loops.
- The variance uses **two passes** (mean first, then squared deviations) — numerically the safe choice. The tempting one-pass formula `Σx² − (Σx)²/n` suffers **catastrophic cancellation** (Chapter 3) when the mean is large — a real bug in naive statistics code.
- In Chapter 18 these hand loops become `std::accumulate`/`std::reduce`; in Chapter 22 the energies come from a Monte Carlo generator. But the analysis *shape* — loop, accumulate, summarize — stays.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`if (init; cond)`** | An `if` with a branch-scoped variable (C++17). |
| **`switch` / fall-through** | Multi-way branch on an integral; a `case` without `break` continues into the next. |
| **`for`** | Counted loop (init; condition; update). |
| **`std::size_t`** | Unsigned type for sizes/indices (correct loop index type). |
| **Nested loop** | A loop inside a loop; traverses 2-D data at *n²* cost. |
| **`while` / `do-while`** | Test-before / test-after loops (convergence pattern). |
| **Range-based `for`** | `for (const auto& x : data)` — iterate every element. |
| **`break` / `continue`** | Exit the loop / skip to its next iteration. |
| **Reverse-loop idiom** | `for (std::size_t i = n; i-- > 0; )` — safe unsigned reverse. |

### What's next

You can iterate over data in every way C++ offers. **[Ch.6 — Functions I](#chapter-6--functions-i-parameters-overloading--performance)** introduces functions to name and reuse this logic, with a deep look at parameter passing (value vs reference) and its decisive effect on performance.

[↑ back to top](#chapter-5--control-flow)


---

## Chapter 6 — Functions I: Parameters, Overloading & Performance

> **Level:** Beginner → Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.5 — Control Flow](#chapter-5--control-flow)

**Learning objectives** — after this chapter you will be able to:

- Declare functions (including trailing/deduced return types).
- Choose how parameters are passed — the decision that most affects performance.
- Return values (and multiple values) efficiently via RVO and structured bindings.
- Use overloading, default arguments, `constexpr`, `noexcept`, and `[[nodiscard]]`.

**In this chapter**

- [6.1 Declaring functions](#61-declaring-functions)
- [6.2 Passing parameters: value, reference, const reference](#62-passing-parameters-value-reference-const-reference)
- [6.3 Returning values, RVO, and multiple results](#63-returning-values-rvo-and-multiple-results)
- [6.4 Overloading and default arguments](#64-overloading-and-default-arguments)
- [6.5 `constexpr`, `noexcept`, `[[nodiscard]]`, `inline`](#65-constexpr-noexcept-nodiscard-inline)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-statistics-as-functions) · Glossary · What's next

---

### 6.1 Declaring functions

A **function** names a reusable computation, with a return type, name, parameter list, and body:

```cpp
double square(double x) { return x * x; }        // square(3.0) → 9
```

`void` means "returns nothing." Two modern spellings you'll meet: a **trailing return type** (`-> T` after the parameters) and a **deduced return** (`auto`, inferred from `return`):

```cpp
auto add(double a, double b) -> double { return a + b; }   // trailing return type
auto mul(double a, double b)           { return a * b; }   // deduced → double
```

Trailing return types matter when the return type *depends on the parameters* (common in templates, Chapter 16); `auto` return is handy for small functions but keep explicit types on public interfaces for clarity. Functions must be *declared before use* — the reason headers exist (Chapter 8).

### 6.2 Passing parameters: value, reference, const reference

This is the most consequential section in the chapter — how you pass a parameter decides whether your code *copies* data (slow) or *shares* it (fast). C++'s explicit control here is exactly why it's fast.

**Pass by value** — the function gets a *copy*:

```cpp
double square(double x) { return x * x; }        // x is a copy; fine — a double is 8 bytes
```

Copying a `double` is free. But copying a `std::vector<double>` of a million elements, or a large struct, means allocating and duplicating all of it — potentially your program's dominant cost.

**Pass by reference** (`&`) — operate on the *caller's* object; can modify it, no copy:

```cpp
void scale(double& x, double factor) { x *= factor; }
double e = 10.0; scale(e, 2.5);                  // e is now 25
```

**Pass by const reference** (`const&`) — share, no copy, *promise not to modify* — the workhorse for large read-only data:

```cpp
std::size_t length(const std::string& s) { return s.size(); }   // no copy of the string
```

Verified: `square(3)=9`, `scaled=25`, `len=4`.

> 💡 **Idiom — the parameter-passing rule of thumb.**
> - **Small, cheap-to-copy types** (`int`, `double`, a pointer, a small struct): **pass by value** — simple and often faster (no indirection).
> - **Large read-only types** (`std::string`, `std::vector`, big structs): **pass by `const&`** — no copy, read-only.
> - **Objects to modify** in place: **pass by `&`**.
>
> This choice is the difference between a loop that runs in seconds and one that runs in hours. When in doubt for a big type, `const&`.

> ⚙️ **Under the hood** — A reference is, at the machine level, essentially a pointer (an address) the compiler dereferences for you — with no null and no rebinding. So `const std::string&` passes a single 8-byte address, not the whole heap buffer. "Pass by value" for a big object invokes its *copy constructor* (Chapter 12), allocating and duplicating its contents. This is why parameter choice dominates performance.

### 6.3 Returning values, RVO, and multiple results

Returning a large object *looks* like it copies it out — but modern C++ elides that via **RVO** (Return Value Optimization / copy elision): the compiler constructs the result directly in the caller. So return big objects **by value** — it's clean *and* efficient:

```cpp
std::vector<double> make_energies(int n) {
    std::vector<double> v;
    for (int i = 0; i < n; ++i) v.push_back(90.0 + i * 0.1);
    return v;              // no copy — constructed directly in the caller
}
// make_energies(3) → {90, 90.1, 90.2}
```

To return **several values**, return a small struct — and unpack it at the call site with a **structured binding** (`auto [a, b] = ...`):

```cpp
struct Stats { double mean, stddev; };
Stats analyze(const std::vector<double>& v) {
    double s = 0; for (double x : v) s += x;
    double m = s / v.size();
    double var = 0; for (double x : v) var += (x-m)*(x-m);
    return {m, std::sqrt(var / v.size())};       // brace-construct the struct; returned by value (RVO)
}

auto [mean, sd] = analyze({91.0, 91.2, 90.8});   // unpack both results
// mean=91.0000 sd=0.1633
```

> 💡 **Idiom** — **Return by value** for computed results, even large ones — RVO (and move semantics, Chapter 13) make it cheap, and it's the clearest, safest style. To return multiple values, prefer a **named struct + structured binding** over out-parameters (pointers/references you write into): it's self-documenting and can't be misused. The old C habit of "pass an output buffer by pointer" is rarely needed in modern C++.

### 6.4 Overloading and default arguments

**Overloading** lets several functions share a name, distinguished by parameter types; the compiler picks the best match (*overload resolution*):

```cpp
int    absval(int x)    { return x < 0 ? -x : x; }
double absval(double x) { return std::fabs(x); }
// absval(-5) → 5 (int version), absval(-2.5) → 2.5 (double version)
```

**Default arguments** let callers omit trailing parameters:

```cpp
double kinetic_energy(double mass, double v, double c = 299792458.0) {
    double gamma = 1.0 / std::sqrt(1.0 - (v*v)/(c*c));
    return (gamma - 1.0) * mass * c * c;
}
kinetic_energy(1.0, 0.1 * 299792458.0);          // c defaulted → 4.5278e+14 J
```

> ⚠️ **Gotcha** — Default arguments belong in the *declaration* (usually the header), not repeated in the definition, and only *trailing* parameters can have them. Beware overloading + implicit conversions: `absval(2u)` (unsigned) may pick a surprising overload or be ambiguous. Keep overload sets small; for numeric code, a function *template* (Chapter 16) is often cleaner than many overloads.

### 6.5 `constexpr`, `noexcept`, `[[nodiscard]]`, `inline`

Four annotations you'll use constantly:

**`constexpr` functions** can run at *compile time* when given compile-time arguments — precompute constants, tables, derived values with zero runtime cost:

```cpp
constexpr long factorial(int n) { return n <= 1 ? 1 : n * factorial(n - 1); }
constexpr long f5 = factorial(5);   // computed during compilation → 120
```

**`noexcept`** promises no exceptions (enables optimizations, especially for move — Chapter 13). **`[[nodiscard]]`** makes the compiler *warn* if the caller ignores the result — perfect for validators and error codes:

```cpp
[[nodiscard]] bool is_valid(double energy) noexcept { return energy > 0.0 && energy < 1e6; }
is_valid(91.2);   // ⚠️ warning: ignoring return value declared [[nodiscard]]
```

**`inline`** today mainly *permits a function to be defined in a header* (Chapter 8's ODR); the optimizer decides actual inlining itself.

> 💡 **Idiom** — Mark **`constexpr`** any small function that *could* run at compile time; **`[[nodiscard]]`** functions whose result must not be dropped (validators, `empty()`, error status); **`noexcept`** functions you guarantee won't throw (move constructors, swap). These make scientific code faster and safer for almost no effort.

---

### Summary

- Functions have a return type, name, parameters, body; **trailing** (`-> T`) and **deduced** (`auto`) return types exist. Declare before use.
- **Parameter passing is the key performance decision**: **by value** (small cheap types), **by `const&`** (large read-only — no copy), **by `&`** (to modify).
- **Return by value** even for large objects (**RVO**); return **multiple values** via a struct + **structured binding**; avoid out-parameters.
- **Overloading** picks a function by argument types; **default arguments** (trailing, in the declaration) let callers omit parameters.
- **`constexpr`** (compile-time), **`noexcept`** (no throw), **`[[nodiscard]]`** (warn on ignored result), **`inline`** (header definitions).

### Self-check quiz

1. When pass by value, `const&`, and `&`?
   <details><summary>Answer</summary>By value for small cheap types; `const&` for large read-only (avoid copy); `&` to modify the caller's object.</details>
2. How do you return two values from a function idiomatically?
   <details><summary>Answer</summary>Return a small struct and unpack it with a structured binding: `auto [a, b] = f();`. RVO makes it cheap; it's clearer than out-parameters.</details>
3. Does `return bigVector;` copy the vector?
   <details><summary>Answer</summary>No — RVO/copy elision constructs it in the caller. Returning large objects by value is idiomatic and efficient.</details>
4. What does `[[nodiscard]]` do?
   <details><summary>Answer</summary>Warns if the caller ignores the return value — for results that must be checked (validators, error status).</details>

### Exercises

**Exercise 6.1 — Pass by const reference (guided).** Write `double sum(const std::vector<double>& v)` and a `[[nodiscard]] bool nonempty(const std::vector<double>& v)`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
double sum(const std::vector<double>& v) {
    double s = 0.0; for (double x : v) s += x; return s;
}
[[nodiscard]] bool nonempty(const std::vector<double>& v) noexcept { return !v.empty(); }
int main() {
    std::vector<double> data = {1.0, 2.0, 3.0};
    if (nonempty(data)) std::cout << std::format("sum = {}\n", sum(data));   // 6
}
```

Output:
```text
sum = 6
```

**Why this works:** `const std::vector<double>&` passes the vector *without copying* (Chapter 5's `const auto&` habit, now for parameters). `nonempty` is `[[nodiscard]]`, so ignoring its result warns. Both functions read but never modify the data.

</details>

**Exercise 6.2 — Return two results.** Write `min_max(const std::vector<double>&)` returning a struct with `min` and `max`, and unpack it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
struct MinMax { double min, max; };
MinMax min_max(const std::vector<double>& v) {
    double lo = v[0], hi = v[0];
    for (double x : v) { if (x < lo) lo = x; if (x > hi) hi = x; }
    return {lo, hi};
}
int main() {
    auto [lo, hi] = min_max({91.1, 90.8, 91.4, 91.0});
    std::cout << std::format("min={} max={}\n", lo, hi);   // min=90.8 max=91.4
}
```

Output:
```text
min=90.8 max=91.4
```

**Why this works:** returning a `MinMax` struct bundles both results; the structured binding `auto [lo, hi]` unpacks them at the call site — cleaner and safer than two out-parameters. RVO means the struct isn't actually copied out.

</details>

**Exercise 6.3 — `constexpr` power.** Write a `constexpr` `ipow(base, exp)` and use it as a compile-time constant.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
constexpr long ipow(long base, int exp) {
    long r = 1; for (int i = 0; i < exp; ++i) r *= base; return r;
}
int main() {
    constexpr long k = ipow(2, 10);   // computed at compile time → 1024
    std::cout << k << "\n";
}
```

Output:
```text
1024
```

**Why this works:** `ipow` is `constexpr` and `ipow(2, 10)` uses compile-time arguments, so `k` is computed *during compilation* — `1024` is baked into the executable with no runtime work. (C++14+ allows loops in `constexpr` functions.)

</details>

**Exercise 6.4 — Overload for units.** Overload `to_si(double, ...)` so `to_si(5.0, "GeV")` and `to_si(5.0, "MeV")` convert to joules. (Hint: one function with a `std::string_view` unit is cleaner than overloads — write that.)

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <string_view>
double to_joules(double value, std::string_view unit) {
    constexpr double eV = 1.602176634e-19;
    if (unit == "GeV") return value * 1e9  * eV;
    if (unit == "MeV") return value * 1e6  * eV;
    return value;   // assume already joules
}
int main() {
    std::cout << std::format("5 GeV = {:.3e} J\n", to_joules(5.0, "GeV"));
    std::cout << std::format("5 MeV = {:.3e} J\n", to_joules(5.0, "MeV"));
}
```

Output:
```text
5 GeV = 8.011e-10 J
5 MeV = 8.011e-13 J
```

**Why this works:** the hint's lesson — a single function parameterized by a `std::string_view` unit is clearer than an overload per unit. It compares the unit and applies the right factor. (For heavy use you'd use an `enum` (Chapter 9), not string comparison.)

</details>

### Chapter project: statistics as functions

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–6. We extract the statistics into reusable functions — passing data by `const&`, returning results by value.

**Goal.** Provide `mean`, `stddev`, and a combined `analyze` returning a struct, plus a `[[nodiscard]]` `passes_cut`.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <cmath>

struct Stats { double mean, stddev; };

Stats analyze(const std::vector<double>& data) {   // const& — no copy of the dataset
    double sum = 0.0;
    for (double x : data) sum += x;
    double m = sum / data.size();
    double var = 0.0;
    for (double x : data) var += (x - m) * (x - m);
    return {m, std::sqrt(var / data.size())};       // returned by value (RVO)
}

[[nodiscard]] bool passes_cut(double energy, double threshold = 91.0) noexcept {
    return energy > threshold;
}

int main() {
    std::vector<double> energies = {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4};

    auto [mean, stddev] = analyze(energies);        // structured binding

    int passing = 0;
    for (double e : energies) if (passes_cut(e)) ++passing;

    std::cout << "=== Monte Carlo Analysis Toolkit v4 ===\n";
    std::cout << std::format("Mean         : {:.4f} GeV\n", mean);
    std::cout << std::format("Std dev      : {:.4f} GeV\n", stddev);
    std::cout << std::format("Passing (>91): {} / {}\n", passing, energies.size());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v4 ===
Mean         : 91.1000 GeV
Std dev      : 0.2000 GeV
Passing (>91): 4 / 7
```

**Commentary.**
- The statistics are now **reusable functions**, the first step toward a real library. `analyze` takes the dataset as **`const std::vector<double>&`** (no copy) and returns a `Stats` struct **by value** (RVO), unpacked with a structured binding — modern, efficient, and clear.
- `passes_cut` has a **default threshold** and is **`[[nodiscard]]`**, so you can't call it and ignore whether the event passed; `noexcept` documents that a comparison never throws.
- We've switched the dataset from a raw C array to a **`std::vector<double>`** (Chapter 18 covers it fully) — which knows its own `.size()` and passes safely by reference, unlike a decayed array. Four energies exceed 91.0.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Pass by value / `&` / `const&`** | Copy / modify caller's object / share read-only. |
| **Trailing return type** | `-> T` after the parameter list. |
| **RVO / copy elision** | Returning an object by value without copying. |
| **Structured binding** | `auto [a, b] = f();` unpacking a struct/pair. |
| **Overloading** | Multiple functions, one name, distinguished by parameters. |
| **Default argument** | A preset value for a trailing parameter. |
| **`constexpr` function** | Can be evaluated at compile time. |
| **`noexcept`** | Promises a function won't throw. |
| **`[[nodiscard]]`** | Warns if the return value is ignored. |

### What's next

Functions can be *values* too. **[Ch.7 — Functions II: Lambdas & Function Objects](#chapter-7--functions-ii-lambdas--function-objects)** covers lambdas, captures, functors, and `std::function` — the tools that let you pass *behaviour* to the STL algorithms (Chapter 19) and write flexible numerical code.

[↑ back to top](#chapter-6--functions-i-parameters-overloading--performance)


---

## Chapter 7 — Functions II: Lambdas & Function Objects

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.6 — Functions I](#chapter-6--functions-i-parameters-overloading--performance)

**Learning objectives** — after this chapter you will be able to:

- Write lambdas and understand capture by value vs by reference.
- Use generic, mutable, and returned lambdas (closures).
- Write function objects (functors) and use `std::function`.
- Pass *behaviour* to functions — the foundation of the STL algorithms.

**In this chapter**

- [7.1 Lambdas](#71-lambdas)
- [7.2 Captures](#72-captures)
- [7.3 Generic, mutable, and returned lambdas](#73-generic-mutable-and-returned-lambdas)
- [7.4 Function objects (functors)](#74-function-objects-functors)
- [7.5 `std::function` and higher-order functions](#75-stdfunction-and-higher-order-functions)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-pluggable-selection-cuts) · Glossary · What's next

---

### 7.1 Lambdas

A **lambda** is an anonymous function you define right where you use it — and can store in a variable and pass to other functions. This makes *behaviour* a value, which is exactly what the STL algorithms (Chapter 19) and numerical routines need.

```cpp
auto square = [](double x) { return x * x; };
// square(4.0) → 16
```

The syntax is `[captures](parameters) { body }`. Store it in an `auto` variable (each lambda has a unique compiler-generated type) and call it like any function. The return type is deduced; add `-> Type` before the body to specify it.

### 7.2 Captures

The **capture list** `[...]` lets the lambda *remember* variables from the surrounding scope — **by value** (a copy, frozen at definition) or **by reference** (a live link):

```cpp
double factor = 3.0;
auto by_val = [factor](double x) { return x * factor; };   // copies factor = 3.0
auto by_ref = [&factor](double x) { return x * factor; };  // links to factor
factor = 10.0;
// by_val(2) → 6   (used the captured copy, still 3.0)
// by_ref(2) → 20  (used the live factor, now 10.0)
```

Shorthands: `[=]` captures everything used by value; `[&]` everything by reference; mix them (`[=, &accumulator]`). **Init-capture** creates a new variable: `[total = 0.0]`.

> ⚠️ **Gotcha — dangling reference captures.** Capturing by reference (`[&]`) is a footgun if the lambda **outlives** the variable it references — the reference dangles and using it is undefined behaviour (Chapter 30). This happens when a lambda is stored (in a `std::function`, returned from a function, or run later by another thread) and the captured local was destroyed. Rule: capture by reference only for lambdas used *immediately* (passed straight to an algorithm); capture by **value** for lambdas that are stored or outlive the scope.

### 7.3 Generic, mutable, and returned lambdas

A **generic lambda** uses `auto` parameters, so one lambda works for many types (a template under the hood, Chapter 16):

```cpp
auto add = [](auto a, auto b) { return a + b; };
// add(2, 3) → 5      (ints)
// add(1.5, 0.5) → 2   (doubles)
```

A lambda's `operator()` is `const` by default; add **`mutable`** to modify by-value captures (stateful callables):

```cpp
auto counter = [count = 0]() mutable { return ++count; };
int c1 = counter(); int c2 = counter(); int c3 = counter();
// counter: 1 2 3
```

A lambda can even **return another lambda** — a *closure factory*. The returned closure captures the outer parameter *by value* (so it stays valid after the factory returns):

```cpp
auto make_scaler = [](double k) { return [k](double x){ return k * x; }; };
auto triple = make_scaler(3.0);
// triple(4.0) → 12
```

> ⚠️ **Gotcha** — When calling a stateful lambda several times *inside one expression*, the order is unspecified (Chapter 4): `std::format("{} {} {}", counter(), counter(), counter())` may print `3 2 1` under g++. Sequence the calls into separate statements when order matters.

### 7.4 Function objects (functors)

Before lambdas, C++ used **function objects** (**functors**): a class defining `operator()`, so instances are callable and can carry configuration/state:

```cpp
struct AboveThreshold {
    double threshold;
    bool operator()(double x) const { return x > threshold; }
};
AboveThreshold cut{91.2};
// cut(91.3) → true
```

Lambdas *are* compiler-generated functors — a lambda with captures becomes a hidden struct whose members are the captures and whose `operator()` is the body. You still write explicit functors when the callable is reused widely, needs a name, or is part of a class's interface.

> ⚙️ **Under the hood** — `auto sq = [](double x){ return x*x; };` compiles to roughly `struct __L { double operator()(double x) const { return x*x; } }; __L sq;`. Captures become data members. Because the call operator is an ordinary (often `inline`) member function, the compiler can **inline** a lambda passed to an algorithm completely — which is why `std::sort(v, [](...){...})` is as fast as a hand-written loop, and faster than C's `qsort` (which calls through a function pointer it can't inline). Zero-overhead abstraction again.

### 7.5 `std::function` and higher-order functions

A **higher-order function** takes a callable as a parameter. Accept any lambda/functor with a template (Chapter 16), or — when you need a concrete stored type — with **`std::function`**, a type-erased wrapper for "any callable with this signature":

```cpp
#include <functional>
int count_if_energy(const std::vector<double>& data, const std::function<bool(double)>& pred) {
    int c = 0; for (double x : data) if (pred(x)) ++c; return c;
}
// count_if_energy(es, [](double x){ return x > 91.0; })  → 4
// count_if_energy(es, AboveThreshold{91.2})              → 2   (a functor works too)
```

`std::function` also lets you write a **recursive lambda** (a lambda that calls itself needs a named type to refer to):

```cpp
std::function<long(int)> fact = [&](int n){ return n <= 1 ? 1L : n * fact(n-1); };
// fact(5) → 120
```

And a lambda is what you pass to drive an **algorithm** (Chapter 19) — e.g., sort descending:

```cpp
std::vector<double> es = {91.3, 90.8, 91.1};
std::sort(es.begin(), es.end(), [](double a, double b){ return a > b; });
// es → 91.3 91.1 90.8
```

> 💡 **Idiom** — Prefer a **template parameter** (or C++20 `auto` parameter, Chapter 20) over `std::function` when you can, because `std::function` has runtime overhead (an indirection and possible heap allocation) and can't be inlined. Reach for `std::function` only when you *need* a single concrete type — storing heterogeneous callbacks, a recursive lambda, or a stable interface across a compiled boundary. In a hot numerical loop, pass the callable as a template to keep it inlinable.

---

### Summary

- A **lambda** `[captures](params){body}` is an anonymous, storable, passable function.
- **Captures** bring in surrounding variables **by value** (frozen) or **by reference** (`&`, live). Beware **dangling reference captures** in stored/outliving lambdas.
- **Generic lambdas** (`auto` params) work across types; **`mutable`** allows stateful captures; a lambda can **return a lambda** (a closure factory, capturing by value).
- **Functors** are classes with `operator()`; lambdas *are* compiler-generated functors, and both **inline** fully (zero overhead).
- **Higher-order functions** take callables — via a **template** (inlinable, preferred) or **`std::function`** (type-erased; needed for stored/recursive callables). Lambdas drive the STL algorithms.

### Self-check quiz

1. `[factor]` vs `[&factor]` — difference?
   <details><summary>Answer</summary>`[factor]` captures a frozen copy; `[&factor]` a live reference (sees later changes, but dangles if the lambda outlives the variable).</details>
2. Why does a closure factory (a lambda returning a lambda) capture by value?
   <details><summary>Answer</summary>So the returned closure stays valid after the factory returns; a reference capture of the factory's parameter/local would dangle.</details>
3. How does a lambda achieve zero overhead in an algorithm?
   <details><summary>Answer</summary>It compiles to a functor with an inlinable `operator()`, so the algorithm inlines the body entirely — faster than a function pointer, which can't be inlined.</details>
4. When use `std::function` vs a template parameter?
   <details><summary>Answer</summary>Prefer a template (inlinable, no overhead). Use `std::function` for a concrete stored type — heterogeneous callbacks, recursive lambdas, or a compiled interface.</details>

### Exercises

**Exercise 7.1 — A transforming lambda (guided).** Write a lambda converting GeV→MeV (×1000) and apply it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    auto to_MeV = [](double gev) { return gev * 1000.0; };
    std::cout << std::format("{} GeV = {} MeV\n", 0.511, to_MeV(0.511));
}
```

Output:
```text
0.511 GeV = 511 MeV
```

**Why this works:** the lambda captures nothing and transforms its argument. `to_MeV(0.511)` gives `511.0` (the electron mass in MeV) — the kind of conversion you'd apply across a dataset with an algorithm (Chapter 19).

</details>

**Exercise 7.2 — Accumulator with reference capture.** Sum an array into a local `total` via a `[&]` lambda used immediately.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    double xs[] = {1.5, 2.5, 3.0};
    double total = 0.0;
    auto add_to_total = [&total](double x) { total += x; };   // safe: used immediately
    for (double x : xs) add_to_total(x);
    std::cout << std::format("total = {}\n", total);   // 7
}
```

Output:
```text
total = 7
```

**Why this works:** `[&total]` captures by reference, so the lambda mutates the caller's variable — safe because it's used in the loop and never outlives `total`. (Stored later, the reference could dangle — §7.2.)

</details>

**Exercise 7.3 — Closure factory.** Write `make_threshold(double t)` returning a lambda that tests `x > t`, and use two different thresholds.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    auto make_threshold = [](double t) { return [t](double x){ return x > t; }; };
    auto above_91 = make_threshold(91.0);
    auto above_92 = make_threshold(92.0);
    std::cout << std::format("{} {}\n", above_91(91.5), above_92(91.5));   // true false
}
```

Output:
```text
true false
```

**Why this works:** `make_threshold` returns a closure capturing `t` **by value**, so each returned lambda carries its own threshold and stays valid after the factory returns. `above_91(91.5)` is `true`; `above_92(91.5)` is `false`.

</details>

**Exercise 7.4 — Sort with a lambda.** Sort a vector of energies in descending order using `std::sort` and a comparator lambda.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <algorithm>
int main() {
    std::vector<double> es = {91.3, 90.8, 91.1, 91.4, 90.9};
    std::sort(es.begin(), es.end(), [](double a, double b){ return a > b; });
    for (double e : es) std::cout << std::format("{} ", e);
    std::cout << "\n";
}
```

Output:
```text
91.4 91.3 91.1 90.9 90.8
```

**Why this works:** `std::sort` (Chapter 19) orders the range using the comparator lambda `a > b`, which requests *descending* order. The lambda is inlined into the sort, so this is as fast as a hand-written sort with the comparison baked in.

</details>

### Chapter project: pluggable selection cuts

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–7. Analyses swap *selection cuts* constantly. We make the cut a **lambda** passed to a generic counting function.

**Goal.** A `count_if` taking a cut as a callable, and two cuts as lambdas.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <functional>

int count_if(const std::vector<double>& data, const std::function<bool(double)>& cut) {
    int c = 0;
    for (double x : data) if (cut(x)) ++c;
    return c;
}

int main() {
    std::vector<double> energies = {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4};

    auto high_energy = [](double e) { return e > 91.1; };
    double lo = 90.95, hi = 91.25;
    auto in_window   = [=](double e) { return e >= lo && e <= hi; };   // capture bounds by value

    std::cout << "=== Monte Carlo Analysis Toolkit v5 ===\n";
    std::cout << std::format("E > 91.1 GeV       : {} / {}\n", count_if(energies, high_energy), energies.size());
    std::cout << std::format("E in [90.95,91.25] : {} / {}\n", count_if(energies, in_window),   energies.size());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v5 ===
E > 91.1 GeV       : 3 / 7
E in [90.95,91.25] : 3 / 7
```

**Commentary.**
- `count_if` doesn't know *what* the cut is — it just calls the predicate. Analysts express each cut as a **lambda**: `high_energy` captures nothing; `in_window` captures its window bounds **by value** (`[=]`), safely, since it's used immediately.
- This is higher-order programming: `count_if` is written once; the *behaviour* varies by the lambda. It's a hand-rolled preview of `std::count_if` (Chapter 19), which does exactly this over any container.
- We used `std::function` for a clean signature; in performance-critical code you'd template `count_if` on the predicate type so the lambda inlines. Three events exceed 91.1; three fall in the window.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Lambda** | An anonymous, storable function: `[captures](params){body}`. |
| **Capture** | Bringing surrounding variables into a lambda (value or `&`). |
| **Closure** | A lambda together with its captured state. |
| **Generic lambda** | A lambda with `auto` parameters. |
| **`mutable` lambda** | One allowed to modify its by-value captures. |
| **Functor** | A class with `operator()`, callable like a function. |
| **Higher-order function** | A function taking/returning a callable. |
| **`std::function`** | A type-erased wrapper for any callable of a signature. |

### What's next

You can package and pass behaviour. **[Ch.8 — Headers, Translation Units & the Build Model](#chapter-8--headers-translation-units--the-build-model)** closes Part 1: how multi-file programs split into headers and sources, the One-Definition Rule, and linkage — the knowledge to organize (and link) a real scientific codebase.

[↑ back to top](#chapter-7--functions-ii-lambdas--function-objects)


---

## Chapter 8 — Headers, Translation Units & the Build Model

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.1 — Toolchain](#chapter-1--getting-started--the-c-toolchain), [Ch.6 — Functions I](#chapter-6--functions-i-parameters-overloading--performance)

**Learning objectives** — after this chapter you will be able to:

- Split a program into headers and source files.
- Explain declaration vs definition, translation units, and the One-Definition Rule.
- Use include guards and namespaces, and know when `inline` is required.
- Diagnose linker errors ("undefined reference").

**In this chapter**

- [8.1 Declaration vs definition](#81-declaration-vs-definition)
- [8.2 Headers and source files](#82-headers-and-source-files)
- [8.3 The One-Definition Rule](#83-the-one-definition-rule)
- [8.4 Namespaces](#84-namespaces)
- [8.5 Linker errors](#85-linker-errors)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-multi-file-toolkit) · Glossary · What's next

---

### 8.1 Declaration vs definition

A real scientific codebase spans many files. To understand how they fit together, distinguish two things:

- A **declaration** introduces a name and its type/signature — enough for other code to *use* it: `double mean(const double data[], std::size_t n);` (note the semicolon, no body).
- A **definition** provides the actual implementation (the body): `double mean(...) { ... }`.

You can *declare* a function many times but must *define* it exactly once. Code that calls `mean` only needs its declaration to compile; the definition is connected later, by the linker.

### 8.2 Headers and source files

C++ organizes multi-file programs by convention:

- A **header** (`.hpp` or `.h`) holds *declarations* (the interface): function prototypes, class definitions, `constexpr`/`inline` functions, templates.
- A **source file** (`.cpp`) holds *definitions* (the implementation), and `#include`s the headers it needs.

`#include "stats.hpp"` literally pastes the header's text into the file (a *translation unit* = one `.cpp` after all its includes are expanded). Each `.cpp` is compiled independently into an object file; the linker joins them (Chapter 1's pipeline).

A header must not be pasted in twice within one translation unit (that would redefine things). The guard is **`#pragma once`** at the top (or the classic `#ifndef`/`#define`/`#endif` include guard):

```cpp
// stats.hpp
#pragma once
#include <cstddef>

namespace toolkit {
    double mean(const double data[], std::size_t n);          // declaration
    inline double to_MeV(double gev) { return gev * 1000.0; } // header-defined → must be inline
}
```

```cpp
// stats.cpp
#include "stats.hpp"
namespace toolkit {
    double mean(const double data[], std::size_t n) {         // definition
        double s = 0.0;
        for (std::size_t i = 0; i < n; ++i) s += data[i];
        return s / n;
    }
}
```

```cpp
// main.cpp
#include "stats.hpp"
#include <iostream>
#include <format>
int main() {
    double e[] = {91.1, 91.3, 90.9};
    std::cout << std::format("mean   = {:.4f} GeV\n", toolkit::mean(e, std::size(e)));
    std::cout << std::format("0.511 GeV = {} MeV\n", toolkit::to_MeV(0.511));
}
```

Build it by compiling each source to an object, then linking:

```text
$ g++ -std=c++23 -c stats.cpp -o stats.o
$ g++ -std=c++23 -c main.cpp  -o main.o
$ g++ stats.o main.o -o prog
$ ./prog
mean   = 91.1000 GeV
0.511 GeV = 511 MeV
```

`main.cpp` compiled knowing only `mean`'s *declaration* (from the header); the linker connected the call to the *definition* in `stats.o`.

### 8.3 The One-Definition Rule

The **One-Definition Rule (ODR)** is the law governing all this: every function or variable must have **exactly one definition** across the whole program. Break it and you get either a linker error (missing definition) or a nastier "multiple definition" error.

This creates a puzzle for functions you want to *define in a header* (small helpers, so they inline). If a header is `#include`d by five `.cpp` files, its definition appears five times — an ODR violation. The escape hatch is **`inline`**: an `inline` function (or variable) may be defined in every translation unit that includes it, and the linker merges the copies into one. That's the real modern meaning of `inline` (Chapter 6) — *"this definition may appear in multiple translation units."* This is why `to_MeV` above is `inline` but `mean` (defined once in `stats.cpp`) is not.

> ⚠️ **Gotcha** — Never define a *non-inline* function or a global variable *in a header*. If two `.cpp`s include it, you get a "multiple definition" linker error. Headers should contain declarations, plus `inline`/`constexpr`/`template` definitions (which are ODR-exempt). Regular function bodies belong in a `.cpp`.

> ⚙️ **Under the hood** — Templates (Chapter 16) live entirely in headers precisely because of the ODR/`inline` mechanism: a template isn't code until *instantiated* with concrete types, so its definition must be visible wherever it's used, and the compiler generates (and the linker de-duplicates) each instantiation. This is why STL containers and algorithms are header-only — and why heavy template use can slow compilation.

### 8.4 Namespaces

A **namespace** groups related names to avoid clashes — essential when combining libraries (imagine two libraries both defining `Vector`). You've used `std::` (the standard-library namespace) throughout. Define your own with `namespace name { ... }`:

```cpp
namespace toolkit {
    double mean(const double data[], std::size_t n);
}
// used as: toolkit::mean(...)
```

Access members with the scope operator `::` (`toolkit::mean`). Inside the namespace, names are unqualified.

> 💡 **Idiom** — Put your library's names in a namespace (`toolkit`, or nested like `cern::analysis`). And **avoid `using namespace std;` in headers** (and at file scope in large projects) — it dumps every `std` name into scope, inviting ambiguity and surprising overload resolution. Prefer explicit `std::` prefixes, or a narrow `using std::vector;` inside a function. In scientific code that links many libraries, disciplined namespaces prevent maddening clashes.

### 8.5 Linker errors

Understanding the model lets you read the errors. If you *declare* and *call* a function but never link its definition, compilation succeeds (the declaration was enough) but linking fails:

```text
$ g++ main.o -o prog          # forgot to include stats.o
main.cpp:(.text+0x5b): undefined reference to 'toolkit::mean(double const*, unsigned long)'
```

**"undefined reference"** is *the* signature of a linker error: the code compiled, but the linker couldn't find a definition — a forgotten source file, an unlinked library (e.g., you used a numerical library but didn't pass `-lname`), or a typo'd signature. This is a different failure from a *compile* error, and knowing which stage failed tells you where to look.

> 💡 **Idiom** — When you link an external numerical library (BLAS, GSL, ROOT — Chapter 28), you tell the *linker* where to find its compiled definitions with `-l` flags (e.g. `-lgsl -lgslcblas`). An "undefined reference to `gsl_...`" almost always means a missing or misordered `-l` flag — not a bug in your code. Reading the error as a *linker* problem points you straight at the build command.

---

### Summary

- A **declaration** (signature) lets code compile against a name; a **definition** (body) must appear **exactly once** (the **ODR**).
- **Headers** (`.hpp`) hold declarations (+ `inline`/`constexpr`/`template` definitions); **sources** (`.cpp`) hold definitions. `#include` pastes a header into a **translation unit**.
- Guard headers with **`#pragma once`**. A function defined in a header must be **`inline`** (definition may appear in many translation units); regular function bodies go in a `.cpp`.
- **Namespaces** group names to avoid clashes (`toolkit::mean`); avoid `using namespace std;` in headers.
- **"undefined reference"** is a **linker** error (missing definition / unlinked library) — distinct from a compile error, and often fixed by a `-l` flag.

### Self-check quiz

1. What's the difference between a declaration and a definition?
   <details><summary>Answer</summary>A declaration introduces a name and its signature (no body) so callers can compile; a definition provides the implementation. You may declare many times but must define exactly once (ODR).</details>
2. Why must a function *defined in a header* be `inline`?
   <details><summary>Answer</summary>Because the header may be included in many translation units, producing multiple definitions — an ODR violation. `inline` allows the definition in each TU and lets the linker merge them.</details>
3. What does an "undefined reference" error mean, and at which stage does it occur?
   <details><summary>Answer</summary>The linker couldn't find a definition for something declared and used — at the *link* stage (compilation succeeded). Causes: a missing source file or an unlinked library (`-l` flag).</details>
4. Why avoid `using namespace std;` in a header?
   <details><summary>Answer</summary>It injects all of `std` into every file that includes the header, causing name clashes and surprising overload resolution across the project.</details>

### Exercises

**Exercise 8.1 — Split a function (guided).** Given a header declaring `double variance(const double[], std::size_t, double mean);`, write the matching `.cpp` definition.

<details><summary>Show solution</summary>

```cpp
// stats.hpp
#pragma once
#include <cstddef>
namespace toolkit {
    double variance(const double data[], std::size_t n, double mean);
}
```
```cpp
// stats.cpp
#include "stats.hpp"
namespace toolkit {
    double variance(const double data[], std::size_t n, double mean) {
        double v = 0.0;
        for (std::size_t i = 0; i < n; ++i) v += (data[i] - mean) * (data[i] - mean);
        return v / n;
    }
}
```

**Why this works:** the header declares the interface (what callers need); the source defines the body exactly once. Compile with `g++ -c stats.cpp` and link the resulting `stats.o` with any code that includes `stats.hpp` and calls `toolkit::variance`.

</details>

**Exercise 8.2 — Header-only helper.** Add a small `inline` unit-conversion function to a header so it can be used from multiple `.cpp` files without a linker error.

<details><summary>Show solution</summary>

```cpp
// units.hpp
#pragma once
namespace toolkit {
    inline double GeV_to_MeV(double gev) { return gev * 1000.0; }   // inline → ODR-safe in a header
    inline constexpr double kSpeedOfLight = 299792458.0;            // inline variable (C++17)
}
```

**Why this works:** marking the function `inline` (and the constant `inline constexpr`) permits its definition to appear in every translation unit that includes `units.hpp`, with the linker merging them — the ODR-safe way to put a definition in a header. Without `inline`, including it in two `.cpp` files would be a "multiple definition" error.

</details>

### Chapter project: a multi-file toolkit

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–8. We reorganize the toolkit's statistics into a proper header + source, in a `toolkit` namespace — the structure every real C++ project uses.

**Goal.** A `stats.hpp` interface, a `stats.cpp` implementation, and a `main.cpp` that uses them, built by separate compilation.

<details><summary>Show reference solution + commentary</summary>

```cpp
// ---------- stats.hpp (interface) ----------
#pragma once
#include <cstddef>
namespace toolkit {
    double mean(const double data[], std::size_t n);
    inline double to_MeV(double gev) { return gev * 1000.0; }   // header-defined → inline
}
```

```cpp
// ---------- stats.cpp (implementation) ----------
#include "stats.hpp"
namespace toolkit {
    double mean(const double data[], std::size_t n) {
        double s = 0.0;
        for (std::size_t i = 0; i < n; ++i) s += data[i];
        return s / n;
    }
}
```

```cpp
// ---------- main.cpp (usage) ----------
#include "stats.hpp"
#include <iostream>
#include <format>
int main() {
    double e[] = {91.1, 91.3, 90.9};
    std::cout << std::format("mean   = {:.4f} GeV\n", toolkit::mean(e, std::size(e)));
    std::cout << std::format("0.511 GeV = {} MeV\n", toolkit::to_MeV(0.511));
}
```

Build & run:

```text
$ g++ -std=c++23 -c stats.cpp -o stats.o
$ g++ -std=c++23 -c main.cpp  -o main.o
$ g++ stats.o main.o -o prog
$ ./prog
mean   = 91.1000 GeV
0.511 GeV = 511 MeV
```

And forgetting to link `stats.o` shows the linker error we now understand:

```text
$ g++ main.o -o prog
undefined reference to 'toolkit::mean(double const*, unsigned long)'
```

**Commentary.**
- The toolkit now has a real **interface/implementation split**: `stats.hpp` is the contract, `stats.cpp` the code. Any part of the project (and, later, its tests) includes the header and links the object — the same structure used by ROOT, Eigen, and every serious codebase.
- Everything lives in the **`toolkit` namespace**, so these names won't clash with a library you link later.
- `to_MeV` is `inline` because it's *defined in the header*; `mean` is defined once in `stats.cpp`, so it isn't. That single distinction is the ODR in practice.
- This file layout is exactly what **CMake** (Chapter 28) will automate — you'll declare the sources and let the build system compile and link them, scaling from three files to hundreds.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Declaration / definition** | A name+signature / the actual implementation (define once). |
| **Header (`.hpp`)** | Holds declarations and inline/template definitions. |
| **Source (`.cpp`)** | Holds definitions; compiled to an object file. |
| **Translation unit** | One `.cpp` after all `#include`s are expanded. |
| **`#pragma once`** | Include guard preventing double-inclusion. |
| **One-Definition Rule (ODR)** | Exactly one definition per entity program-wide. |
| **`inline`** | Permits a definition in multiple translation units (header). |
| **Namespace** | A named scope grouping declarations (`toolkit::`). |
| **Undefined reference** | A linker error: a used definition wasn't found/linked. |

### What's next

That completes **Part 1 — Foundations**: you can write, structure, and build correct C++ programs, with special care for numerics. **Part 2 opens with [Ch.9 — Classes & Objects](#chapter-9--classes--objects)**, where a scattered "event" (energy, momentum in loose variables) finally becomes a real type — the gateway to C++'s defining strength: precise control over objects and their memory.

[↑ back to top](#chapter-8--headers-translation-units--the-build-model)


---

## Chapter 9 — Classes & Objects

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.6 — Functions I](#chapter-6--functions-i-parameters-overloading--performance), [Ch.8 — Headers](#chapter-8--headers-translation-units--the-build-model)

**Learning objectives** — after this chapter you will be able to:

- Define classes bundling data and behaviour.
- Write constructors, member initializer lists, and delegating constructors.
- Use `const` member functions, access control, and static members.
- Model scientific entities (a particle, a histogram) as proper types.

**In this chapter**

- [9.1 From loose variables to a type](#91-from-loose-variables-to-a-type)
- [9.2 Constructors and member initializer lists](#92-constructors-and-member-initializer-lists)
- [9.3 `const` member functions](#93-const-member-functions)
- [9.4 Access control and encapsulation](#94-access-control-and-encapsulation)
- [9.5 `struct` vs `class`, and default member initializers](#95-struct-vs-class-and-default-member-initializers)
- [9.6 Static members](#96-static-members)
- [9.7 A worked example: a histogram](#97-a-worked-example-a-histogram)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-histogram-for-the-toolkit) · Glossary · What's next

---

### 9.1 From loose variables to a type

Since Chapter 2 we've described a particle with four loose variables — `energy`, `px`, `py`, `pz` — scattered wherever needed. That's fragile: nothing keeps them together or enforces consistency. A **class** bundles **data** (member variables) and **behaviour** (member functions) into one type; an **object** is an instance.

```cpp
class Particle {
public:
    double energy() const { return energy_; }
    double momentum_magnitude() const { return std::sqrt(px_*px_ + py_*py_ + pz_*pz_); }
private:
    double energy_, px_, py_, pz_;   // the object's data
};
```

A `Particle` is now one cohesive thing: its numbers travel together, and its physics lives *with* the data. The trailing-underscore naming (`energy_`) is a common convention marking private members.

### 9.2 Constructors and member initializer lists

A **constructor** initializes an object at creation — same name as the class, no return type. The idiomatic way to set members is the **member initializer list** (after `:`), which constructs each member directly:

```cpp
class Particle {
public:
    Particle(double e, double px, double py, double pz)
        : energy_(e), px_(px), py_(py), pz_(pz) {}   // initializer list
private:
    double energy_, px_, py_, pz_;
};
Particle z{91.2, 30.0, -40.0, 50.0};
```

A class can have **several constructors** (overloaded by parameters), and one can **delegate** to another with `: ClassName(...)` — avoiding duplicated setup:

```cpp
class Histogram {
public:
    Histogram(double lo, double hi, int nbins) : lo_(lo), hi_(hi), counts_(nbins, 0) {}
    Histogram() : Histogram(0.0, 1.0, 10) {}          // delegating: reuse the 3-arg ctor
private:
    double lo_, hi_;
    std::vector<int> counts_;
};
```

> 💡 **Idiom** — **Use the member initializer list, not assignment in the body.** `Particle(...) { energy_ = e; }` *default-constructs* each member, then assigns — two steps. The initializer list constructs each with its final value in one step; it's *required* for `const`/reference members and far more efficient for expensive members (a `std::vector`, `std::string`). **Members initialize in declaration order** — list them in that order to avoid confusion. Use **delegating constructors** to funnel all setup through one "master" constructor.

> ⚠️ **Gotcha** — Mark single-argument constructors **`explicit`** unless you *want* implicit conversion. Without it, `Particle p = 91.2;` might silently construct a `Particle` from a bare `double` — rarely intended. `explicit` on single-arg constructors is a widely-followed rule.

### 9.3 `const` member functions

A member function marked **`const`** (after the parameter list) promises **not to modify the object** — central to correctness:

```cpp
double energy() const { return energy_; }          // const: read-only
void   boost_energy(double d) { energy_ += d; }    // non-const: modifies
```

`const` members can be called on `const` objects and `const&` parameters; non-`const` ones cannot. So passing a `const Particle&` (the efficient way, Chapter 6) lets you call only `const` members — the compiler enforces you don't mutate read-only data.

> 💡 **Idiom** — Mark **every non-modifying member function `const`** (accessors, computations, queries). This "const-correctness" lets objects pass as `const&` (no copies) and be used in `const` contexts. A class whose read-only methods aren't `const` can't be used efficiently — const-correctness is not optional in good C++.

> ⚙️ **Under the hood** — A member function is a free function with a hidden first parameter: **`this`**, a pointer to the object. `z.energy()` is essentially `energy(&z)`, and `energy_` means `this->energy_`. A `const` member gets `this` as a *pointer to const*, so the compiler simply won't let you write members — that's why `const` methods cost nothing; they're a compile-time promise.

### 9.4 Access control and encapsulation

**`public`** members are accessible anywhere; **`private`** only from within the class's own functions. Making data `private` and exposing controlled methods is **encapsulation** — the class guards its own invariants:

```cpp
class Particle {
public:
    Particle(double e, double px, double py, double pz) : energy_(e), px_(px), py_(py), pz_(pz) {}
    double energy() const { return energy_; }     // controlled read access
private:
    double energy_, px_, py_, pz_;                 // no outside code can corrupt these
};
```

For a physics type, a constructor might enforce `E² ≥ |p|²` (so the mass is real) or energy ≥ 0 — invariants only the class can protect.

### 9.5 `struct` vs `class`, and default member initializers

`struct` and `class` are almost identical — the *only* difference is default access: **`struct` is `public` by default, `class` is `private`**. Convention: `struct` for passive data bundles, `class` when you protect invariants.

```cpp
struct Config {                    // public by default — a plain bundle
    double low  = 0.0;             // default member initializers
    double high = 100.0;
    int    bins = 10;
    double bin_width() const { return (high - low) / bins; }
};
Config c;                          // uses defaults → bin_width() = 10
Config c2{0.0, 50.0, 25};          // aggregate initialization → bin_width() = 2
```

**Default member initializers** (`= 0.0`) give members starting values unless a constructor overrides them; an all-public `struct` with no constructor supports **aggregate initialization** with braces.

### 9.6 Static members

A **static** member belongs to the *class*, not to any object — one shared copy for all instances. Static data tracks class-wide state (a count, a shared table); a static member function accesses it without an object:

```cpp
class Particle {
public:
    Particle(double e, double px, double py, double pz) : energy_(e), px_(px), py_(py), pz_(pz) { ++count_; }
    static int count() { return count_; }          // static member function
private:
    double energy_, px_, py_, pz_;
    static inline int count_ = 0;                  // static data member (C++17 inline)
};
// Particle::count() returns how many Particles exist — called on the class, not an object
```

> 💡 **Idiom** — Use `static inline` data members (C++17) so you can *define and initialize them in the class body* (older C++ required a separate definition in a `.cpp`). Static members suit truly class-wide data — an instance counter, a shared lookup table, physical constants attached to a type. But beware: a *mutable* static is global shared state, with the concurrency and testing hazards that implies (Chapter 34).

### 9.7 A worked example: a histogram

Histograms are the workhorse of physics analysis (ROOT's `TH1` is one). Here's a minimal one that ties the chapter together — a constructor, `const` and non-`const` methods, encapsulated storage:

```cpp
#include <vector>
class Histogram {
public:
    Histogram(double lo, double hi, int nbins) : lo_(lo), hi_(hi), counts_(nbins, 0) {}
    Histogram() : Histogram(0.0, 1.0, 10) {}                 // delegating

    void fill(double x) {                                    // non-const: modifies
        if (x < lo_ || x >= hi_) { ++overflow_; return; }
        int b = static_cast<int>((x - lo_) / (hi_ - lo_) * counts_.size());
        ++counts_[b];
        ++total_;
    }
    int  bin(int i) const { return counts_[i]; }             // const accessors
    long total() const    { return total_; }
private:
    double lo_, hi_;
    std::vector<int> counts_;
    long total_ = 0, overflow_ = 0;
};

Histogram h(0.0, 10.0, 5);
for (double x : {1.0, 2.5, 2.6, 9.9, 11.0}) h.fill(x);
// bin0=1  bin1=2  total=4   (11.0 fell in overflow)
```

The `Histogram` owns a `std::vector<int>` of bin counts; `fill` routes a value into the right bin (or overflow); the counts are `private` so no code can corrupt them out of band. This is a real, if minimal, analysis tool.

---

### Summary

- A **class** bundles data (members) and behaviour (methods); an **object** is an instance.
- **Constructors** initialize objects; use the **member initializer list** (constructs members directly, required for `const`/reference members, init in declaration order). **Delegating constructors** (`: OtherCtor(...)`) reuse setup. Mark single-arg constructors **`explicit`**.
- **`const` member functions** promise not to modify the object (const-correctness → objects usable as `const&`); under the hood they get a `const this`.
- **`private`** data + **`public`** methods = **encapsulation**, protecting invariants.
- **`struct`** defaults to public (bundles), **`class`** to private; **default member initializers** and **aggregate init** simplify structs.
- **Static members** belong to the class (one shared copy); use `static inline` for in-class definition. Beware mutable static (global state).

### Self-check quiz

1. Why prefer a member initializer list over assignment in the body?
   <details><summary>Answer</summary>It constructs each member directly with its final value (one step) vs default-construct-then-assign (two). Required for `const`/reference members; far more efficient for expensive members.</details>
2. What does a delegating constructor do?
   <details><summary>Answer</summary>It calls another constructor of the same class (`: Class(args)`) to reuse its setup, avoiding duplicated initialization logic.</details>
3. What does marking a member function `const` guarantee, and how?
   <details><summary>Answer</summary>It won't modify the object; the compiler passes `this` as pointer-to-const, rejecting member writes. It also allows calls on `const` objects/`const&`.</details>
4. What's the difference between a static member and a normal member?
   <details><summary>Answer</summary>A static member belongs to the class (one shared copy for all objects), not to each instance; a static member function is called on the class without an object.</details>

### Exercises

**Exercise 9.1 — A Vector3 type (guided).** A class of 3 components with a `const magnitude()` and encapsulated data.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
class Vector3 {
public:
    Vector3(double x, double y, double z) : x_(x), y_(y), z_(z) {}
    double magnitude() const { return std::sqrt(x_*x_ + y_*y_ + z_*z_); }
private: double x_, y_, z_;
};
int main() { std::cout << std::format("{}\n", Vector3{3,4,12}.magnitude()); }   // 13
```

Output:
```text
13
```

**Why this works:** the components are `private`; `magnitude()` is `const` and computes `sqrt(3²+4²+12²)=13`. The initializer list sets all three directly. (Chapter 15 adds `operator+`.)

</details>

**Exercise 9.2 — Enforce an invariant.** A `Fraction(num, den)` whose constructor rejects a zero denominator; add a `value()`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <stdexcept>
class Fraction {
public:
    Fraction(int n, int d) : num_(n), den_(d) { if (d == 0) throw std::invalid_argument("den 0"); }
    double value() const { return static_cast<double>(num_) / den_; }
private: int num_, den_;
};
int main() { std::cout << std::format("{}\n", Fraction{3, 4}.value()); }   // 0.75
```

Output:
```text
0.75
```

**Why this works:** the constructor validates the invariant (denominator ≠ 0) — only possible because `den_` is `private`. `value()` is `const` and casts to `double` for real division.

</details>

**Exercise 9.3 — Delegating constructor.** Give a `Grid(rows, cols)` and a default `Grid()` that delegates to `Grid(3, 3)`; expose `cells()`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
class Grid {
public:
    Grid(int rows, int cols) : rows_(rows), cols_(cols) {}
    Grid() : Grid(3, 3) {}                        // delegate to the 2-arg ctor
    int cells() const { return rows_ * cols_; }
private: int rows_, cols_;
};
int main() {
    std::cout << std::format("{} {}\n", Grid{}.cells(), Grid{4, 5}.cells());   // 9 20
}
```

Output:
```text
9 20
```

**Why this works:** `Grid()` delegates to `Grid(3, 3)`, so the default grid is 3×3 = 9 cells without duplicating the initialization. `Grid{4,5}` gives 20. Delegation keeps one place responsible for setup.

</details>

**Exercise 9.4 — Instance counter.** Give a class a `static inline int count_` incremented in the constructor and a `static count()`; create three objects and print the count.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
class Event {
public:
    Event() { ++count_; }
    static int count() { return count_; }
private:
    static inline int count_ = 0;
};
int main() {
    Event a, b, c;
    std::cout << std::format("events created: {}\n", Event::count());   // 3
}
```

Output:
```text
events created: 3
```

**Why this works:** `count_` is a single `static` shared across all `Event`s; each constructor increments it. `Event::count()` (called on the *class*) reports the total — a common bookkeeping pattern. `static inline` lets it be defined right in the class body.

</details>

### Chapter project: a histogram for the toolkit

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit** — a major addition. **Builds on:** Ch.1–9. Every physics analysis histograms its data. We add a real `Histogram` class (like ROOT's `TH1`) and fill it with energies.

**Goal.** A `Histogram` class with `fill`, `const` accessors, mean, and a text display, filled with a dataset.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>

class Histogram {
public:
    Histogram(double lo, double hi, int nbins) : lo_(lo), hi_(hi), counts_(nbins, 0) {}

    void fill(double x) {
        if (x < lo_ || x >= hi_) { ++overflow_; return; }
        int b = static_cast<int>((x - lo_) / (hi_ - lo_) * counts_.size());
        ++counts_[b];
        ++total_;
        sum_ += x;
    }

    long   total() const { return total_; }
    double mean()  const { return total_ > 0 ? sum_ / total_ : 0.0; }

    void print() const {
        double width = (hi_ - lo_) / counts_.size();
        for (std::size_t i = 0; i < counts_.size(); ++i) {
            double edge = lo_ + i * width;
            std::cout << std::format("[{:5.1f},{:5.1f}) | ", edge, edge + width);
            for (int k = 0; k < counts_[i]; ++k) std::cout << '#';
            std::cout << ' ' << counts_[i] << '\n';
        }
    }
private:
    double lo_, hi_;
    std::vector<int> counts_;
    long   total_ = 0, overflow_ = 0;
    double sum_ = 0.0;
};

int main() {
    Histogram h(90.0, 92.0, 4);   // 4 bins of width 0.5 over [90, 92)
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4, 91.1, 90.6})
        h.fill(e);

    std::cout << "=== Monte Carlo Analysis Toolkit v6 — energy histogram ===\n";
    h.print();
    std::cout << std::format("entries={} mean={:.4f} GeV\n", h.total(), h.mean());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v6 — energy histogram ===
[ 90.0, 90.5) |  0
[ 90.5, 91.0) | ### 3
[ 91.0, 91.5) | ###### 6
[ 91.5, 92.0) |  0
entries=9 mean=91.0444 GeV
```

**Commentary.**
- The `Histogram` is a real analysis tool: a constructor sets the range and bin count, `fill` routes each value into its bin (tracking total, sum, and overflow), and `const` accessors (`total`, `mean`) and `print` report results without mutating anything.
- The storage (`counts_`, `sum_`) is **`private`** — encapsulated, so nothing corrupts the counts. `mean()` guards against division by zero (empty histogram) — an invariant the class protects.
- Of the nine values, three (`90.9`, `90.8`, `90.6`) land in `[90.5, 91.0)` and six (`91.1`, `91.3`, `91.2`, `91.0`, `91.4`, `91.1`) in `[91.0, 91.5)`; the ASCII bars show the distribution at a glance — exactly like a physicist's first look at data. The mean of all nine is `91.0444` GeV.
- In Chapter 18 the counts become easier to compute with algorithms; in Chapter 22 the fills come from a Monte Carlo generator. This `Histogram` is the toolkit's new analysis centrepiece.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Class / object** | A type bundling data + behaviour / an instance. |
| **Constructor** | Initializes an object at creation. |
| **Member initializer list** | `: a_(x), b_(y)` — constructs members directly. |
| **Delegating constructor** | A constructor calling another of the same class. |
| **`const` member function** | Promises not to modify the object. |
| **`explicit`** | Prevents implicit conversion via a single-arg constructor. |
| **`public` / `private`** | Accessible everywhere / only within the class. |
| **Encapsulation** | Hiding data behind methods to protect invariants. |
| **Static member** | Belongs to the class (one shared copy), not instances. |
| **`this`** | The hidden pointer to the object a member function acts on. |

### What's next

Objects holding only `double`s are simple. The moment an object owns a *resource* — heap memory, a file — everything changes. **[Ch.10 — Pointers, References & const-correctness](#chapter-10--pointers-references--const-correctness)** and then **[Ch.11 — Dynamic Memory & RAII](#chapter-11--dynamic-memory--raii)** tackle the defining challenge (and superpower) of C++: managing resources correctly.

[↑ back to top](#chapter-9--classes--objects)


---

## Chapter 10 — Pointers, References & const-correctness

> **Level:** Intermediate &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Classes](#chapter-9--classes--objects)

**Learning objectives** — after this chapter you will be able to:

- Use raw pointers (`*`, `&`, `nullptr`, `->`) and understand what they are.
- Distinguish pointers from references and choose between them.
- Apply const-correctness with pointers.
- Understand array decay and non-owning observation.

**In this chapter**

- [10.1 Pointers](#101-pointers)
- [10.2 References vs pointers](#102-references-vs-pointers)
- [10.3 Pointers to objects and member access](#103-pointers-to-objects-and-member-access)
- [10.4 Arrays, decay, and pointer arithmetic](#104-arrays-decay-and-pointer-arithmetic)
- [10.5 const-correctness with pointers](#105-const-correctness-with-pointers)
- [10.6 Non-owning observation](#106-non-owning-observation)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-find-the-peak) · Glossary · What's next

---

### 10.1 Pointers

A **pointer** holds the *memory address* of another object. Two operators drive them: **`&`** ("address-of") gets an object's address, **`*`** ("dereference") accesses the pointed-to object:

```cpp
int x = 42;
int* p = &x;          // p holds the address of x
// *p is 42
*p = 100;             // write through the pointer → x becomes 100
```

Verified: `x=42 *p=42`, then `x now = 100`. A pointer to nothing is **`nullptr`** — always use `nullptr` (not the old `NULL` or `0`). Dereferencing a null (or otherwise invalid) pointer is **undefined behaviour** — a common way C++ programs crash or corrupt data.

> ⚠️ **Gotcha** — Pointers are C++'s sharpest and most dangerous tool. A **dangling pointer** (to freed/expired memory), a **null dereference**, and **out-of-bounds** access are all undefined behaviour (Chapter 30) — silent corruption or crashes. Modern C++ *minimizes* raw pointers: prefer references, containers (Chapter 18), and smart pointers (Chapter 14). Raw pointers survive for one honest job: **non-owning observation** (§10.6).

### 10.2 References vs pointers

A **reference** (`&` in a declaration) is an *alias* — another name for an existing object:

```cpp
int x = 5;
int& r = x;      // r is an alias for x
r = 7;           // changes x → 7  (no dereference)
int* p = &x;
*p = 9;          // changes x → 9  (explicit dereference)
```

| | Reference | Pointer |
|---|-----------|---------|
| Can be null? | **No** | Yes (`nullptr`) |
| Can be reseated? | **No** — bound once | Yes |
| Syntax | Transparent (`r = 7`) | Explicit (`*p`, `&x`) |
| Use for | Aliasing, parameters | When it might be null or must reseat |

> 💡 **Idiom** — **Prefer references** when the thing always exists and never changes what it refers to — function parameters (`const T&`), return values, aliases. Use a **pointer** only when you need its extra abilities: it might be *null* (optional/absent), it needs *reseating*, or you're doing pointer arithmetic. "Reference by default, pointer when you need null or reseating."

### 10.3 Pointers to objects and member access

A pointer to a class object accesses its members with the **`->`** operator — shorthand for "dereference, then access":

```cpp
struct Particle { double energy; double mass() const { return energy * 0.5; } };
Particle p{91.2};
Particle* pp = &p;
pp->energy;    // 91.2   — same as (*pp).energy
pp->mass();    // 45.6   — call a member through the pointer
```

`pp->energy` is exactly `(*pp).energy` — the arrow is just the common case made readable. You'll use `->` constantly with smart pointers (Chapter 14) and linked structures.

An **array of pointers** is a classic non-owning collection — several observers pointing at objects owned elsewhere:

```cpp
Particle a{10}, b{20}, c{30};
Particle* list[] = {&a, &b, &c};        // pointers to existing particles
double sum = 0;
for (Particle* q : list) sum += q->energy;
// sum via pointers = 60
```

### 10.4 Arrays, decay, and pointer arithmetic

A C array's name **decays** to a pointer to its first element in most contexts — which is why passing an array to a function really passes a pointer (Chapter 6), and you must pass the length separately:

```cpp
double a[] = {10.0, 20.0, 30.0};
double* ap = a;          // decays: ap points to a[0]
// ap[0] is 10.0,  *(ap + 2) is 30.0   (pointer arithmetic: +2 moves two doubles forward)
```

Pointer arithmetic advances by *element size*: `ap + 2` is two `double`s (16 bytes) later; `ap[i]` is exactly `*(ap + i)`.

> ⚠️ **Gotcha** — Once an array decays to a pointer, `sizeof`/`std::size` no longer give the element count (they'd give the pointer size). This is why raw arrays are fragile and why `std::array`/`std::vector`/`std::span` (Chapter 18) — which *remember* their size — are strongly preferred. Reserve raw pointer arithmetic for low-level buffer code where you've measured it matters.

### 10.5 const-correctness with pointers

`const` and pointers combine two independent ways — *what* is const matters:

```cpp
const int c = 5;
const int* pc = &c;      // pointer to const: can't modify *pc (can repoint pc)
int y = 9;
int* const cp = &y;      // const pointer: can't repoint cp (can modify *cp)
*cp = 11;                // OK — the pointee isn't const
// *pc = ...             // ERROR — the pointee is const
```

Read right-to-left: `const int* pc` is "a pointer to a `const int`" (the *data* is read-only); `int* const cp` is "a `const` pointer to an `int`" (the *pointer* is fixed). `const int* const` locks both.

> 💡 **Idiom** — Use **pointer-to-const** (`const T*`) for a non-owning observer you won't modify — the pointer counterpart of `const T&`. It documents "I look but don't touch," lets `const` data be observed, and prevents accidental writes. This matters most at API boundaries (a function taking `const double*` promises not to alter your data).

### 10.6 Non-owning observation

With smart pointers (Chapter 14) and containers handling *ownership*, the legitimate modern use of a raw pointer is **non-owning observation**: "here is a thing I'm looking at, which might be absent (null)." A function that returns *which* element matched — or nothing — is the classic case:

```cpp
const double* max_energy(const double* data, std::size_t n) {
    if (n == 0) return nullptr;          // nothing to point at
    const double* best = &data[0];
    for (std::size_t i = 1; i < n; ++i)
        if (data[i] > *best) best = &data[i];
    return best;                         // a pointer INTO the caller's data (not owned)
}
```

The returned pointer *observes* an element the caller still owns; `nullptr` cleanly represents "empty range, no maximum." The caller checks for null before dereferencing.

> ⚠️ **Gotcha** — A non-owning pointer is valid only as long as what it points into stays alive. If `max_energy` returned a pointer into a *local* array (destroyed at return), the pointer would **dangle** — UB. Here it points into the *caller's* data, which outlives the call, so it's safe. Always ask: *does the pointed-to object outlive the pointer?* (C++20's `std::span`, Chapter 18, packages "non-owning view of a range" more safely.)

---

### Summary

- A **pointer** holds an address; **`&`** takes an address, **`*`** dereferences, **`->`** accesses a member through a pointer (`p->m` = `(*p).m`). **`nullptr`** points to nothing; dereferencing null/invalid pointers is **UB**.
- A **reference** is a non-null, non-reseatable alias. **Prefer references**; use pointers only for *null*, *reseating*, or arithmetic.
- Arrays **decay** to pointers (losing size) — prefer `std::array`/`std::vector`/`std::span`. An **array of pointers** is a non-owning collection.
- **const-correctness**: `const T*` (pointer to const — read-only data) vs `T* const` (const pointer — fixed target); read right-to-left.
- The modern role of raw pointers is **non-owning observation** (possibly-null); ensure the pointee outlives the pointer.

### Self-check quiz

1. What does `p->m` mean?
   <details><summary>Answer</summary>Dereference the pointer `p` and access member `m` — exactly `(*p).m`. Used to reach members of an object through a pointer.</details>
2. Give two things a pointer can do that a reference can't.
   <details><summary>Answer</summary>Be null (`nullptr`) and be reseated (repointed). References are non-null and bound once.</details>
3. What's the difference between `const int*` and `int* const`?
   <details><summary>Answer</summary>`const int*` is a pointer to const (can't modify the pointee, can repoint); `int* const` is a const pointer (can modify the pointee, can't repoint). Read right-to-left.</details>
4. Why is returning a pointer into a *local* array dangerous?
   <details><summary>Answer</summary>The local is destroyed at return, so the pointer dangles — dereferencing it is UB. The pointee must outlive the pointer.</details>

### Exercises

**Exercise 10.1 — Swap via pointers (guided).** Write `swap(double* a, double* b)`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
void swap(double* a, double* b) { double t = *a; *a = *b; *b = t; }
int main() {
    double x = 1.5, y = 9.5;
    swap(&x, &y);
    std::cout << std::format("x={} y={}\n", x, y);   // x=9.5 y=1.5
}
```

Output:
```text
x=9.5 y=1.5
```

**Why this works:** passing addresses (`&x`, `&y`) lets `swap` modify the caller's variables through the pointers. (A reference version — `swap(double&, double&)` — is cleaner and can't be null; `std::swap` is what you'd actually use.)

</details>

**Exercise 10.2 — Count via pointer-to-const.** Write `count_above(const double* data, std::size_t n, double thr)`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int count_above(const double* data, std::size_t n, double thr) {
    int c = 0;
    for (std::size_t i = 0; i < n; ++i) if (data[i] > thr) ++c;
    return c;
}
int main() {
    double e[] = {91.1, 91.3, 90.9, 91.2};
    std::cout << std::format("{}\n", count_above(e, std::size(e), 91.0));   // 3
}
```

Output:
```text
3
```

**Why this works:** `const double*` is a non-owning, read-only view — the pointer counterpart of `const double&`. Three values exceed 91.0.

</details>

**Exercise 10.3 — Access an object through a pointer.** Given `struct Vec { double x, y; double norm2() const { return x*x + y*y; } };`, make a pointer to one and call `norm2()` via `->`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
struct Vec { double x, y; double norm2() const { return x*x + y*y; } };
int main() {
    Vec v{3.0, 4.0};
    Vec* p = &v;
    std::cout << std::format("x={} norm2={}\n", p->x, p->norm2());   // x=3 norm2=25
}
```

Output:
```text
x=3 norm2=25
```

**Why this works:** `p->x` and `p->norm2()` reach the member and method through the pointer — shorthand for `(*p).x` and `(*p).norm2()`. `norm2()` is `3²+4²=25`.

</details>

**Exercise 10.4 — Sum through an array of pointers.** Make three `double`s, an array of pointers to them, and sum the pointed-to values.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
int main() {
    double a = 10.0, b = 20.0, c = 30.0;
    double* ptrs[] = {&a, &b, &c};
    double sum = 0.0;
    for (double* p : ptrs) sum += *p;
    std::cout << std::format("sum = {}\n", sum);   // 60
}
```

Output:
```text
sum = 60
```

**Why this works:** `ptrs` holds addresses of `a`, `b`, `c` (non-owning). The range-based loop dereferences each pointer (`*p`) to add the pointed-to value, giving `60`. This is a hand-built non-owning collection — the pattern smart pointers and containers formalize safely.

</details>

### Chapter project: find the peak

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–10. Finding *which* event has the maximum energy — returning a non-owning pointer (or null for an empty dataset) — is a textbook use of raw pointers.

**Goal.** A `max_energy` returning a non-owning pointer to the largest element, or `nullptr` if empty.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>

const double* max_energy(const double* data, std::size_t n) {
    if (n == 0) return nullptr;
    const double* best = &data[0];
    for (std::size_t i = 1; i < n; ++i)
        if (data[i] > *best) best = &data[i];
    return best;
}

int main() {
    double energies[] = {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4};
    const std::size_t n = std::size(energies);

    const double* hi = max_energy(energies, n);
    std::cout << "=== Monte Carlo Analysis Toolkit v7 ===\n";
    if (hi != nullptr)
        std::cout << std::format("Max energy = {:.1f} GeV (at index {})\n", *hi, hi - energies);

    const double* none = max_energy(energies, 0);
    std::cout << std::format("empty range returns nullptr: {}\n", (none == nullptr));
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v7 ===
Max energy = 91.4 GeV (at index 6)
empty range returns nullptr: true
```

**Commentary.**
- `max_energy` returns a **non-owning pointer** into the caller's array — it points at the winning element (91.4, index 6) without owning or copying anything. `nullptr` cleanly encodes "empty range, no maximum," which the caller checks before dereferencing.
- `hi - energies` is **pointer subtraction**: the distance (in elements) between two pointers into the same array gives the index.
- This is exactly what `std::max_element` (Chapter 19) does, returning an *iterator* (a generalized pointer). We're building iterator intuition by hand.
- Safe because the returned pointer points into `energies`, which outlives the call. Returning a pointer into a *local* array would dangle (§10.6) — the hazard the next chapters (RAII, smart pointers) systematically eliminate.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Pointer** | A variable holding another object's address. |
| **`&` / `*` / `->`** | Address-of / dereference / member-through-pointer. |
| **`nullptr`** | A pointer to nothing (type-safe null). |
| **Reference** | A non-null, non-reseatable alias. |
| **Array decay** | An array name converting to a pointer to its first element. |
| **Pointer arithmetic** | Advancing a pointer by element-sized steps. |
| **`const T*` / `T* const`** | Pointer to const data / const pointer. |
| **Non-owning observation** | Using a pointer to look at (not own) an object. |
| **Dangling pointer** | A pointer to freed/expired memory (UB to use). |

### What's next

Pointers can *address* memory — but who *allocates* and *frees* it? That question is the crux of C++. **[Ch.11 — Dynamic Memory & RAII](#chapter-11--dynamic-memory--raii)** introduces `new`/`delete`, the leaks and dangling they cause, and **RAII** — C++'s elegant, defining solution to resource management.

[↑ back to top](#chapter-10--pointers-references--const-correctness)


---

## Chapter 11 — Dynamic Memory & RAII

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Classes](#chapter-9--classes--objects), [Ch.10 — Pointers](#chapter-10--pointers-references--const-correctness)

**Learning objectives** — after this chapter you will be able to:

- Allocate and free heap memory with `new`/`delete`.
- Recognise the classic memory bugs: leaks, dangling pointers, double-free.
- Apply **RAII** — C++'s defining solution to resource management.
- Write a resource-owning class whose destructor cleans up automatically.

**In this chapter**

- [11.1 Stack vs heap; `new` and `delete`](#111-stack-vs-heap-new-and-delete)
- [11.2 The classic memory bugs](#112-the-classic-memory-bugs)
- [11.3 RAII: the core idea](#113-raii-the-core-idea)
- [11.4 A resource-owning class](#114-a-resource-owning-class)
- [11.5 Why manual `delete` is unsafe (exceptions)](#115-why-manual-delete-is-unsafe-exceptions)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-an-owning-energy-buffer) · Glossary · What's next

---

### 11.1 Stack vs heap; `new` and `delete`

Every object lives in one of two places:

- The **stack** — automatic storage. Local variables live here; they're created when declared and destroyed automatically at the end of their scope (`}`). Fast, but the size must be known and bounded.
- The **heap** — dynamic storage. You request memory *explicitly* at runtime, for data whose size or lifetime isn't known at compile time (a dataset read from a file, a buffer sized by user input).

You allocate on the heap with **`new`** and free with **`delete`** (or `new[]`/`delete[]` for arrays):

```cpp
double* p = new double(3.14);   // allocate one double on the heap
delete p;                        // free it

double* arr = new double[1000]; // allocate an array
delete[] arr;                    // free it (note the [] !)
```

`new` returns a *pointer* to the heap memory. That memory stays alive until *you* `delete` it — the heap does not clean up after itself. This manual control is powerful and, unmanaged, dangerous.

> ⚠️ **Gotcha** — Match `new` with `delete` and `new[]` with `delete[]` — mixing them (`delete` on a `new[]` array) is undefined behaviour. But the deeper lesson of this chapter is: **you should almost never write raw `new`/`delete` in modern C++.** RAII (§11.3) and smart pointers (Chapter 14) manage heap memory for you. We show `new`/`delete` so you understand what those tools automate — and can read older code.

### 11.2 The classic memory bugs

Manual `new`/`delete` invites three infamous bugs, each undefined behaviour or a silent resource drain:

```cpp
double* p = new double[100];
// ... use p ...
// (1) LEAK: forget to delete → the memory is never reclaimed
```

```cpp
double* p = new double(1.0);
delete p;
double x = *p;        // (2) DANGLING / use-after-free: p points to freed memory → UB
```

```cpp
double* p = new double(1.0);
delete p;
delete p;             // (3) DOUBLE-FREE: freeing twice → UB (often a crash)
```

- **Memory leak** — you never `delete`, so freed-but-unreclaimed memory accumulates. In a long-running simulation, leaks grow until the job is killed for exhausting RAM.
- **Dangling pointer / use-after-free** — you use memory after freeing it. The bytes may still look valid, so the bug is silent — until they're reused and your data is garbage.
- **Double-free** — freeing the same memory twice corrupts the allocator.

These are the bugs that make C++ notorious. The tools **`-fsanitize=address`** (AddressSanitizer) and **`-fsanitize=leak`** catch them at runtime during testing — indispensable for scientific code. But the real fix is a design that makes them *impossible*: RAII.

### 11.3 RAII: the core idea

**RAII** — *Resource Acquisition Is Initialization* — is C++'s defining idiom and arguably its greatest strength. The principle:

> **Tie a resource's lifetime to an object's lifetime.** Acquire the resource in a **constructor**; release it in the **destructor**. Because C++ guarantees the destructor runs *automatically* when the object leaves scope, the resource is *always* released — no leak, even if you forget, even if an exception is thrown.

A **destructor** is a special member function named `~ClassName()`, called automatically when an object is destroyed. This is the hook RAII hangs on: put cleanup there, and it happens deterministically, every time.

RAII isn't only for memory — it manages *any* resource: files (close on destruction), locks (unlock), GPU buffers, network connections, timers. "Acquire in constructor, release in destructor" is the pattern behind almost every well-designed C++ class.

### 11.4 A resource-owning class

Here's RAII made concrete: a `Buffer` that owns a heap array. Its constructor `new[]`s the memory; its destructor `delete[]`s it. Watch the destructor fire automatically at the end of the inner scope:

```cpp
#include <iostream>
#include <format>
class Buffer {
public:
    explicit Buffer(std::size_t n) : size_(n), data_(new double[n]{}) {   // ACQUIRE
        std::cout << std::format("Buffer: acquired {} doubles\n", n);
    }
    ~Buffer() {                                                           // RELEASE
        std::cout << std::format("Buffer: releasing {} doubles\n", size_);
        delete[] data_;
    }
    void   set(std::size_t i, double v) { data_[i] = v; }
    double sum() const { double s=0; for (std::size_t i=0;i<size_;++i) s+=data_[i]; return s; }
private:
    std::size_t size_;
    double* data_;
};

int main() {
    std::cout << "before scope\n";
    {
        Buffer b(3);
        b.set(0, 10.0); b.set(1, 20.0); b.set(2, 30.0);
        std::cout << std::format("sum = {}\n", b.sum());
    }   // <-- b leaves scope here; ~Buffer() runs AUTOMATICALLY
    std::cout << "after scope\n";
}
```

Output:

```text
before scope
Buffer: acquired 3 doubles
sum = 60
Buffer: releasing 3 doubles
after scope
```

Notice `Buffer: releasing` prints *between* "sum" and "after scope" — the destructor fired at the closing `}` of the inner block, with no `delete` written by the user. AddressSanitizer confirms **no leak**. That automatic, guaranteed cleanup is RAII.

> ⚙️ **Under the hood** — When a scope exits, the compiler inserts destructor calls for every automatic (stack) object in it, in *reverse* order of construction. This runs on *every* exit path — falling off the end, a `return`, or an exception unwinding the stack (§11.5). There's no garbage collector and no runtime cost beyond the destructor's own work; the cleanup is compiled in at each scope exit. This determinism — you know *exactly* when cleanup happens — is why C++ can manage files, locks, and GPU memory as reliably as heap memory.

> ⚠️ **Gotcha — the copy problem.** The `Buffer` above has a lurking bug: if you *copy* it (`Buffer b2 = b;`), the default copy duplicates the *pointer*, not the data — so two `Buffer`s own the same array, and both destructors `delete[]` it → **double-free**. A class that owns a resource must control copying. That's the **Rule of Three/Five** — Chapter 12, the very next chapter. (This chapter's project sidesteps it by *forbidding* copies with `= delete`.)

### 11.5 Why manual `delete` is unsafe (exceptions)

Even careful manual `delete` fails in the presence of **exceptions** (Chapter 21). Consider:

```cpp
void process() {
    double* p = new double[1000];
    risky_operation();        // if this THROWS, the next line never runs...
    delete[] p;               // ...so p LEAKS
}
```

If `risky_operation()` throws, control jumps out of `process` and `delete[] p` is skipped — a leak. You *could* wrap it in `try`/`catch`, but that's exactly the boilerplate RAII eliminates: a resource-owning object's destructor runs *during* exception unwinding, so it cleans up no matter how the scope is left.

> 💡 **Idiom** — **Never manage a raw resource by hand; wrap it in an RAII object.** The standard library already provides RAII wrappers for the common cases: **`std::vector`** and **`std::string`** own heap memory; **`std::unique_ptr`/`std::shared_ptr`** (Chapter 14) own single objects; **`std::fstream`** owns a file; **`std::lock_guard`** owns a lock. Reach for these instead of `new`/`delete`. You'll write a *custom* RAII class only when wrapping a resource the standard library doesn't cover (a C library handle, a GPU buffer) — and then this chapter's pattern is your template.

---

### Summary

- Objects live on the **stack** (automatic, freed at scope end) or the **heap** (via **`new`/`delete`**, `new[]`/`delete[]`, freed manually).
- Manual heap management invites **leaks** (never freed), **dangling/use-after-free** (used after freed), and **double-free** — all UB or resource drains. Catch them with **`-fsanitize=address,leak`**.
- **RAII** ties a resource's lifetime to an object's: **acquire in the constructor, release in the destructor** (`~Class()`), which runs *automatically* at scope exit — even on an exception.
- A resource-owning class's destructor makes cleanup guaranteed and leak-free; but such a class must control **copying** (the double-free trap → Rule of Five, Chapter 12).
- **Prefer standard RAII wrappers** (`std::vector`, `std::unique_ptr`, `std::fstream`, `std::lock_guard`) over raw `new`/`delete`.

### Self-check quiz

1. What are the three classic manual-memory bugs?
   <details><summary>Answer</summary>Memory leak (never `delete`d), dangling pointer / use-after-free (used after `delete`), and double-free (`delete`d twice). All are UB or resource drains.</details>
2. State the RAII principle.
   <details><summary>Answer</summary>Tie a resource's lifetime to an object's: acquire it in the constructor, release it in the destructor — which runs automatically at scope exit, so the resource is always released (even on exceptions).</details>
3. Why does RAII survive exceptions when manual `delete` doesn't?
   <details><summary>Answer</summary>When an exception unwinds the stack, destructors of local objects still run, so an RAII object frees its resource. A manual `delete` after the throwing call is skipped, leaking.</details>
4. Why can copying a naive resource-owning class cause a double-free?
   <details><summary>Answer</summary>The default copy duplicates the pointer, not the data, so two objects own the same memory; both destructors free it. The class must control copying (Rule of Five, Ch.12).</details>

### Exercises

**Exercise 11.1 — Watch the destructor (guided).** Write a `ScopedLog` whose constructor prints "enter" and destructor prints "exit"; create one in a nested scope and observe the order.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
class ScopedLog {
public:
    ScopedLog()  { std::cout << "enter\n"; }
    ~ScopedLog() { std::cout << "exit\n"; }
};
int main() {
    std::cout << "start\n";
    { ScopedLog log; std::cout << "working\n"; }   // exit prints here
    std::cout << "end\n";
}
```

Output:
```text
start
enter
working
exit
end
```

**Why this works:** the constructor runs at `ScopedLog log;`, the destructor at the closing `}` — automatically. "exit" prints between "working" and "end". This is the RAII hook: any cleanup in the destructor happens deterministically at scope exit. (Real uses: a scoped timer, a scoped lock.)

</details>

**Exercise 11.2 — Spot the leak.** This function leaks. Explain why, and fix it *without* adding `delete` (use a standard RAII type).

```cpp
void f() {
    int* data = new int[1000];
    // ... use data ...
    // (returns without delete)
}
```

<details><summary>Show solution</summary>

```cpp
#include <vector>
void f() {
    std::vector<int> data(1000);   // owns its memory; freed automatically
    // ... use data ...
}                                   // no leak — vector's destructor runs here
```

**Why this works:** the original leaks because `new int[1000]` is never `delete[]`d before the function returns. `std::vector<int>` is an RAII wrapper: it `new[]`s in its constructor and `delete[]`s in its destructor, so the memory is freed automatically at scope exit — no manual `delete`, no leak, and exception-safe for free. This is why you almost never write `new` in modern C++.

</details>

**Exercise 11.3 — Forbid copying.** Give a resource-owning class `Handle` a deleted copy constructor and copy assignment, and show that copying it is a compile error.

<details><summary>Show solution</summary>

```cpp
class Handle {
public:
    explicit Handle(int id) : id_(id) {}
    Handle(const Handle&) = delete;              // no copying
    Handle& operator=(const Handle&) = delete;
    int id() const { return id_; }
private:
    int id_;
};
int main() {
    Handle h(7);
    // Handle h2 = h;   // ❌ compile error: copy constructor is deleted
    return h.id() == 7 ? 0 : 1;
}
```

**Why this works:** `= delete` removes the copy operations, so any attempt to copy `Handle` fails at *compile time* — preventing the double-free trap for a type that owns a resource. (Chapter 12 shows how to *properly* support copying/moving instead of forbidding it.)

</details>

### Chapter project: an owning energy buffer

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–11. We give the toolkit an RAII class that *owns* a heap array of energies — freed automatically, no leaks.

**Goal.** An `EnergyBuffer` owning `new double[n]`, with `set`/`mean`, copying forbidden (for now), and guaranteed cleanup.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>

class EnergyBuffer {
public:
    explicit EnergyBuffer(std::size_t n) : n_(n), data_(new double[n]{}) {}
    ~EnergyBuffer() { delete[] data_; }                       // RAII release

    // Forbid copying for now — a shallow copy would double-free. Chapter 12 fixes this.
    EnergyBuffer(const EnergyBuffer&) = delete;
    EnergyBuffer& operator=(const EnergyBuffer&) = delete;

    void   set(std::size_t i, double v) { data_[i] = v; }
    double mean() const {
        double s = 0.0;
        for (std::size_t i = 0; i < n_; ++i) s += data_[i];
        return n_ ? s / n_ : 0.0;
    }
    std::size_t size() const { return n_; }
private:
    std::size_t n_;
    double* data_;
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v8 ===\n";
    EnergyBuffer buf(5);
    double es[] = {91.1, 91.3, 90.9, 91.2, 91.0};
    for (std::size_t i = 0; i < buf.size(); ++i) buf.set(i, es[i]);
    std::cout << std::format("buffer holds {} energies, mean = {:.4f} GeV\n",
                             buf.size(), buf.mean());
}   // buf's destructor frees the heap array here — no leak, no manual delete
```

Output:

```text
=== Monte Carlo Analysis Toolkit v8 ===
buffer holds 5 energies, mean = 91.1000 GeV
```

**Commentary.**
- `EnergyBuffer` **owns** a heap array: it `new[]`s in the constructor and `delete[]`s in the destructor. The array is freed automatically when `buf` leaves `main` — AddressSanitizer confirms **no leak**, and we never wrote `delete` at the call site.
- Copying is **forbidden** (`= delete`) because the default shallow copy would leave two buffers owning the same array — a double-free. This is the honest "not yet" answer; Chapter 12's Rule of Five shows how to *properly* copy and move an owning class.
- In practice you'd use **`std::vector<double>`** — which is exactly this RAII pattern, done right, including copy/move. We hand-wrote it here to *see* how ownership works, so that when you use `std::vector` (Chapter 18) you know what it's doing for you.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Stack / heap** | Automatic (scope-lifetime) storage / manual dynamic storage. |
| **`new` / `delete`** | Allocate / free one heap object (`new[]`/`delete[]` for arrays). |
| **Memory leak** | Heap memory never freed. |
| **Dangling pointer** | A pointer to freed memory (use-after-free is UB). |
| **Double-free** | Freeing the same memory twice (UB). |
| **RAII** | Resource Acquisition Is Initialization — resource lifetime tied to an object's. |
| **Destructor (`~Class`)** | Runs automatically at object destruction; releases the resource. |
| **AddressSanitizer** | `-fsanitize=address` runtime detector of memory bugs. |
| **`= delete`** | Removes a special member (e.g. forbids copying). |

### What's next

Your class owns a resource — but it can't yet be safely copied or moved. **[Ch.12 — The Rule of Three/Five/Zero](#chapter-12--the-rule-of-three--five--zero)** completes the story: how a resource-owning class properly copies, and how the **Rule of Zero** lets you avoid writing any of it by using standard RAII members.

[↑ back to top](#chapter-11--dynamic-memory--raii)


---

## Chapter 12 — The Rule of Three / Five / Zero

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — Dynamic Memory & RAII](#chapter-11--dynamic-memory--raii)

**Learning objectives** — after this chapter you will be able to:

- Explain deep vs shallow copy and why owning classes need special members.
- Apply the Rule of Three (copy) and know what the Rule of Five adds (move).
- Use `= default` and `= delete` to control special members.
- Prefer the **Rule of Zero** — the modern default that writes none of them.

**In this chapter**

- [12.1 The special member functions](#121-the-special-member-functions)
- [12.2 Shallow vs deep copy](#122-shallow-vs-deep-copy)
- [12.3 The Rule of Three](#123-the-rule-of-three)
- [12.4 The Rule of Five and `= default`/`= delete`](#124-the-rule-of-five-and--default-delete)
- [12.5 The Rule of Zero](#125-the-rule-of-zero)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-copyable-dataset-rule-of-zero) · Glossary · What's next

---

### 12.1 The special member functions

Every class has a set of **special member functions** the compiler will generate for you if you don't write them:

- **Destructor** — `~Class()`
- **Copy constructor** — `Class(const Class&)` (make a new object from an existing one)
- **Copy assignment** — `operator=(const Class&)` (overwrite one existing object with another)
- **Move constructor** — `Class(Class&&)` (Chapter 13)
- **Move assignment** — `operator=(Class&&)` (Chapter 13)

For a class holding only simple members (`double`, `int`, or other well-behaved types), the compiler-generated versions are correct — copying copies each member. The trouble begins when a class **owns a resource** (raw heap memory, a file handle), because the *default* copy does the wrong thing.

### 12.2 Shallow vs deep copy

The compiler's default copy is a **shallow copy** — it copies each member *value*, including a pointer. For a class owning heap memory, that copies the *pointer*, not the pointed-to data — so two objects end up sharing (and both trying to free) the same buffer:

```cpp
class Bad {
    double* data_;              // owns heap memory
public:
    explicit Bad(std::size_t n) : data_(new double[n]) {}
    ~Bad() { delete[] data_; }
    // default copy: copies data_ (the pointer!) → two Bads share one array
};
Bad a(10);
Bad b = a;        // shallow copy: b.data_ == a.data_
// ...both destructors run → delete[] the SAME array twice → DOUBLE-FREE (UB)
```

A **deep copy** instead allocates a *new* buffer and copies the contents, so each object owns its own independent memory. An owning class must provide a deep copy — that's the Rule of Three.

### 12.3 The Rule of Three

> **The Rule of Three:** if a class needs a custom **destructor**, it almost certainly also needs a custom **copy constructor** and **copy assignment** — because it owns a resource that requires deep copying and proper cleanup.

Here's an owning `Array` done correctly:

```cpp
class Array {
public:
    explicit Array(std::size_t n) : n_(n), data_(new double[n]{}) {}
    ~Array() { delete[] data_; }                                  // (1) destructor

    Array(const Array& o) : n_(o.n_), data_(new double[o.n_]) {   // (2) copy constructor — DEEP
        for (std::size_t i = 0; i < n_; ++i) data_[i] = o.data_[i];
    }
    Array& operator=(const Array& o) {                            // (3) copy assignment — DEEP
        if (this != &o) {                                         // guard against self-assignment
            delete[] data_;                                       // free the old buffer
            n_ = o.n_; data_ = new double[o.n_];
            for (std::size_t i = 0; i < n_; ++i) data_[i] = o.data_[i];
        }
        return *this;
    }
    void set(std::size_t i, double v) { data_[i] = v; }
    double get(std::size_t i) const { return data_[i]; }
private:
    std::size_t n_; double* data_;
};

Array a(3); a.set(0, 10.0);
Array b = a;        // deep copy
b.set(0, 99.0);     // modify the copy — a is untouched
// a[0]=10  b[0]=99  (independent)
```

Verified: `a[0]=10 b[0]=99`, AddressSanitizer reports **no leak** and no double-free. Two independent arrays.

> ⚠️ **Gotcha — the copy-assignment pitfalls.** Copy assignment has two classic traps: **self-assignment** (`a = a;` — without the `if (this != &o)` guard you'd `delete[]` your own data before copying it) and **exception safety** (if `new` throws after `delete[]`, you've destroyed the object). The robust idiom is **copy-and-swap**: make a copy, then swap it with `*this` — which handles both automatically. (Look it up when you write a real owning class; it's the gold standard.)

### 12.4 The Rule of Five and `= default`/`= delete`

C++11 added **move** operations (Chapter 13), which *steal* a resource from a temporary instead of deep-copying it — a big performance win. So the Rule of Three became the **Rule of Five**: an owning class should define (or default) all five — destructor, copy constructor, copy assignment, **move constructor**, **move assignment** — because declaring any one of them suppresses the compiler's automatic generation of the move operations.

You control the special members explicitly with **`= default`** (ask the compiler for the standard one) and **`= delete`** (forbid it):

```cpp
class Owner {
public:
    Owner(const Owner&) = delete;             // forbid copying
    Owner& operator=(const Owner&) = delete;
    Owner(Owner&&) = default;                  // allow (default) moving
    Owner& operator=(Owner&&) = default;
    ~Owner() = default;
};
```

This is exactly what `std::unique_ptr` does — move-only (Chapter 14). `= delete` (which you met in Chapter 11) prevents a special member entirely; `= default` restores the compiler's version even when you've written others.

> ⚙️ **Under the hood** — The rules for *which* special members the compiler auto-generates are famously subtle: declaring a destructor or copy operation *disables* the automatic move operations (so a Rule-of-Three class silently loses moves and falls back to slow copies). This trap is the whole reason the guidance escalated from "Three" to "Five": if you touch one, be explicit about all five. Which is also why the *real* modern advice is to touch *none* of them — the Rule of Zero.

### 12.5 The Rule of Zero

Here is the punchline, and the rule you should actually follow 95% of the time:

> **The Rule of Zero:** design classes so they need *none* of the five special functions. Store resources in members that already manage themselves — `std::vector`, `std::string`, `std::unique_ptr`, `std::shared_ptr` — and the compiler-generated destructor, copy, and move are all **automatically correct**, because each member cleans up, copies, and moves itself.

```cpp
#include <vector>
class Dataset {
    std::vector<double> data_;       // RAII member — manages its own memory
public:
    void add(double x) { data_.push_back(x); }
    std::size_t size() const { return data_.size(); }
    double sum() const { double s=0; for (double x : data_) s+=x; return s; }
};

Dataset d1; d1.add(1.0); d1.add(2.0);
Dataset d2 = d1;      // copy JUST WORKS — deep copy, no code written
d2.add(3.0);
// d1.size=2 d2.size=3 d2.sum=6   (independent, leak-free)
```

`Dataset` writes **zero** special members, yet copies correctly (deep), moves efficiently, and never leaks — because `std::vector` does all of that for its `data_`. Verified: `d1.size=2 d2.size=3 d2.sum=6`, no leaks.

> 💡 **Idiom** — **Follow the Rule of Zero by default.** Build classes from self-managing members (`std::vector`, `std::string`, smart pointers) and write no destructor, copy, or move at all — the compiler's generated versions are correct and optimal. Write the Rule of Five *only* when you're implementing a low-level resource wrapper the standard library doesn't provide (a C API handle, a GPU buffer). For everything else — which is almost everything — zero is the answer. This is the single most important class-design guideline in modern C++.

---

### Summary

- The **special member functions** (destructor, copy ctor/assignment, move ctor/assignment) are auto-generated; the defaults are wrong for a class that **owns a resource** (shallow copy → double-free).
- A **deep copy** allocates independent memory and copies contents.
- **Rule of Three**: a custom destructor implies you need a custom copy constructor *and* copy assignment (with self-assignment guard; prefer **copy-and-swap**).
- **Rule of Five**: add move constructor/assignment; use **`= default`**/**`= delete`** to control the set (declaring one suppresses the auto-generated moves).
- **Rule of Zero** (the real advice): build from self-managing members (`std::vector`, `std::unique_ptr`, …) so you write **none** of the five — copy/move/cleanup are automatically correct.

### Self-check quiz

1. Why does the default (shallow) copy of a pointer-owning class cause a double-free?
   <details><summary>Answer</summary>It copies the pointer, so two objects share one buffer; both destructors `delete[]` it — freeing the same memory twice (UB).</details>
2. State the Rule of Three.
   <details><summary>Answer</summary>If a class needs a custom destructor, it almost certainly also needs a custom copy constructor and copy assignment (to deep-copy the owned resource).</details>
3. What does `= default` vs `= delete` do?
   <details><summary>Answer</summary>`= default` asks the compiler for its standard version of a special member; `= delete` forbids it (e.g. a move-only or non-copyable type).</details>
4. What is the Rule of Zero, and why prefer it?
   <details><summary>Answer</summary>Design classes needing none of the five special functions by storing resources in self-managing members (`std::vector`, smart pointers); the generated copy/move/destructor are then automatically correct — less code, no bugs.</details>

### Exercises

**Exercise 12.1 — Deep copy (guided).** Write an owning `IntArray` (Rule of Three) and prove a copy is independent.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
class IntArray {
public:
    explicit IntArray(std::size_t n) : n_(n), data_(new int[n]{}) {}
    ~IntArray() { delete[] data_; }
    IntArray(const IntArray& o) : n_(o.n_), data_(new int[o.n_]) {
        for (std::size_t i = 0; i < n_; ++i) data_[i] = o.data_[i];
    }
    IntArray& operator=(const IntArray& o) {
        if (this != &o) { delete[] data_; n_ = o.n_; data_ = new int[o.n_];
            for (std::size_t i = 0; i < n_; ++i) data_[i] = o.data_[i]; }
        return *this;
    }
    void set(std::size_t i, int v) { data_[i] = v; }
    int  get(std::size_t i) const { return data_[i]; }
private:
    std::size_t n_; int* data_;
};
int main() {
    IntArray a(2); a.set(0, 5);
    IntArray b = a; b.set(0, 99);
    std::cout << std::format("a[0]={} b[0]={}\n", a.get(0), b.get(0));   // 5 99
}
```

Output:
```text
a[0]=5 b[0]=99
```

**Why this works:** the copy constructor allocates a *new* array and copies elements (deep copy), so `b` is independent — modifying `b[0]` leaves `a[0]` at 5. The destructor and copy assignment complete the Rule of Three. (In real code, use `std::vector<int>` and write none of this — §12.5.)

</details>

**Exercise 12.2 — Rule of Zero.** Rewrite `IntArray` using a standard container so you write no special members, and show copying works.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
class IntArray {
    std::vector<int> data_;
public:
    explicit IntArray(std::size_t n) : data_(n, 0) {}
    void set(std::size_t i, int v) { data_[i] = v; }
    int  get(std::size_t i) const { return data_[i]; }
};
int main() {
    IntArray a(2); a.set(0, 5);
    IntArray b = a; b.set(0, 99);              // copy just works
    std::cout << std::format("a[0]={} b[0]={}\n", a.get(0), b.get(0));   // 5 99
}
```

Output:
```text
a[0]=5 b[0]=99
```

**Why this works:** `std::vector<int>` manages its own memory, so the compiler-generated copy constructor deep-copies `data_` automatically — `b` is independent with *zero* special members written. Compare the code volume to Exercise 12.1: the Rule of Zero is dramatically less error-prone.

</details>

**Exercise 12.3 — Move-only type.** Make a `UniqueHandle` that can be moved but not copied (using `= default`/`= delete`).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
class UniqueHandle {
public:
    explicit UniqueHandle(int id) : id_(id) {}
    UniqueHandle(const UniqueHandle&) = delete;             // no copy
    UniqueHandle& operator=(const UniqueHandle&) = delete;
    UniqueHandle(UniqueHandle&&) = default;                  // yes move
    UniqueHandle& operator=(UniqueHandle&&) = default;
    int id() const { return id_; }
private:
    int id_;
};
int main() {
    UniqueHandle a(7);
    UniqueHandle b = std::move(a);       // move OK
    // UniqueHandle c = b;               // ❌ copy is deleted
    std::cout << "b.id = " << b.id() << "\n";   // 7
}
```

Output:
```text
b.id = 7
```

**Why this works:** deleting the copy operations and defaulting the move operations makes `UniqueHandle` *move-only* — it can be transferred (`std::move`) but not duplicated. This is exactly the design of `std::unique_ptr` (Chapter 14). `std::move` (Chapter 13) casts `a` to an rvalue so the move constructor is chosen.

</details>

### Chapter project: a copyable dataset (Rule of Zero)

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–12. We replace Chapter 11's hand-managed `EnergyBuffer` with a **Rule of Zero** `Dataset` — copyable, movable, leak-free, with *no* special members.

**Goal.** A `Dataset` holding energies in a `std::vector`, with `add`/`mean`, that copies correctly for free.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>

class Dataset {
    std::vector<double> energies_;      // RAII member → Rule of Zero
public:
    void add(double e) { energies_.push_back(e); }
    std::size_t size() const { return energies_.size(); }
    double mean() const {
        if (energies_.empty()) return 0.0;
        double s = 0.0;
        for (double e : energies_) s += e;
        return s / energies_.size();
    }
};

int main() {
    Dataset data;
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) data.add(e);

    Dataset backup = data;              // deep copy — for free (Rule of Zero)
    backup.add(200.0);                  // modify the copy only

    std::cout << "=== Monte Carlo Analysis Toolkit v9 ===\n";
    std::cout << std::format("data:   {} events, mean = {:.4f} GeV\n", data.size(), data.mean());
    std::cout << std::format("backup: {} events, mean = {:.4f} GeV\n", backup.size(), backup.mean());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v9 ===
data:   5 events, mean = 91.1000 GeV
backup: 6 events, mean = 109.2500 GeV
```

**Commentary.**
- `Dataset` writes **zero** special members, yet `Dataset backup = data;` makes an independent **deep copy** — because its `std::vector` member copies itself. Modifying `backup` (adding a 200 GeV outlier) leaves `data` untouched; `data` still means 91.1, `backup` now means 109.25.
- Compare to Chapter 11's `EnergyBuffer`, which had to *forbid* copying to avoid a double-free. By building on `std::vector` instead of raw `new[]`, we get correct copy, move, and cleanup with none of the Rule-of-Five machinery — and no leaks.
- This is the toolkit's dataset from here on: a Rule-of-Zero class over `std::vector`. Chapter 13 explains the *move* that makes returning and passing such datasets cheap; Chapter 18 explores `std::vector` fully.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Special member functions** | Destructor, copy/move constructor, copy/move assignment. |
| **Shallow / deep copy** | Copies the pointer (shares data) / copies the contents (independent). |
| **Rule of Three** | Custom destructor ⇒ also custom copy ctor + copy assignment. |
| **Rule of Five** | Rule of Three + move constructor + move assignment. |
| **`= default` / `= delete`** | Request the compiler's version / forbid a special member. |
| **Rule of Zero** | Design classes needing none of the five (use self-managing members). |
| **Copy-and-swap** | The robust copy-assignment idiom (exception- and self-assignment-safe). |

### What's next

The Rule of Five mentions *move* operations — the feature that makes returning big objects and passing datasets cheap. **[Ch.13 — Move Semantics](#chapter-13--move-semantics)** explains rvalue references, `std::move`, and why moving is so much faster than copying — essential for high-performance scientific code.

[↑ back to top](#chapter-12--the-rule-of-three--five--zero)


---

## Chapter 13 — Move Semantics

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.12 — Rule of Five](#chapter-12--the-rule-of-three--five--zero)

**Learning objectives** — after this chapter you will be able to:

- Distinguish lvalues from rvalues and use rvalue references (`T&&`).
- Write move constructors/assignment that *steal* a resource instead of copying.
- Use `std::move`, and know when moves happen automatically.
- Explain why moving is far cheaper than copying — key to fast scientific code.

**In this chapter**

- [13.1 The problem: copies are expensive](#131-the-problem-copies-are-expensive)
- [13.2 lvalues, rvalues, and `T&&`](#132-lvalues-rvalues-and-t)
- [13.3 Move constructors: stealing](#133-move-constructors-stealing)
- [13.4 `std::move` and when moves happen](#134-stdmove-and-when-moves-happen)
- [13.5 The moved-from state and `noexcept`](#135-the-moved-from-state-and-noexcept)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-cheap-dataset-transfer) · Glossary · What's next

---

### 13.1 The problem: copies are expensive

A `std::vector<double>` of a million elements is 8 MB of heap memory. *Copying* it means allocating another 8 MB and duplicating every element — expensive. Yet much of the time you don't *need* a copy: when you return a vector from a function, or pass a temporary, the source is about to be destroyed anyway. Copying it, only to throw the original away, is pure waste.

**Move semantics** (C++11) is the solution: instead of *copying* a resource, *transfer ownership* of it — steal the internal pointer from the soon-to-die source and leave the source empty. Moving a million-element vector is a handful of pointer assignments, regardless of size. This is one of the biggest reasons modern C++ is fast.

### 13.2 lvalues, rvalues, and `T&&`

To know *when* it's safe to steal, C++ classifies expressions:

- An **lvalue** has a name and a persistent location — `x`, `arr[i]`, a variable. It lives on; you must *not* steal from it.
- An **rvalue** is a temporary with no lasting identity — `Vec(1000)`, `a + b`, the result of a function returning by value. It's about to be destroyed; stealing from it is safe.

An **rvalue reference**, written **`T&&`**, binds *only* to rvalues — it's the language's way to say "this is a temporary I'm allowed to gut":

```cpp
Vec       a(1000);
Vec&      lref = a;          // lvalue reference — binds to the named a
Vec&&     rref = Vec(500);   // rvalue reference — binds to a temporary
// Vec&&  bad  = a;          // ❌ can't bind an rvalue reference to an lvalue
```

Overloading on `const T&` (copy) vs `T&&` (move) lets a function do different things for a persistent object vs a temporary — the mechanism behind move constructors.

### 13.3 Move constructors: stealing

A **move constructor** takes a `T&&` and *steals* the source's resource — copying the pointer (cheap) and nulling the source, rather than deep-copying the data. Compare copy and move on an owning `Vec`:

```cpp
class Vec {
public:
    explicit Vec(std::size_t n) : n_(n), data_(new double[n]{}) {}
    ~Vec() { delete[] data_; }

    Vec(const Vec& o) : n_(o.n_), data_(new double[o.n_]) {      // COPY: allocate + duplicate
        for (std::size_t i = 0; i < n_; ++i) data_[i] = o.data_[i];
        std::cout << std::format("copied {} doubles\n", n_);
    }
    Vec(Vec&& o) noexcept : n_(o.n_), data_(o.data_) {           // MOVE: steal the pointer
        o.n_ = 0; o.data_ = nullptr;                             // leave source empty (but valid)
        std::cout << std::format("moved {} doubles\n", n_);
    }
    std::size_t size() const { return n_; }
private:
    std::size_t n_; double* data_;
};
```

The move constructor does **no allocation and no element copying** — it takes `o`'s buffer pointer and sets `o.data_ = nullptr` so the dying source's destructor `delete[] nullptr`s (a safe no-op). Watch the difference:

```cpp
Vec a(1000);
Vec b = a;                 // a is an lvalue → COPY   → "copied 1000 doubles"
Vec c = std::move(a);      // std::move(a) is an rvalue → MOVE → "moved 1000 doubles"
// after: a.size() == 0    (a was gutted)
```

Verified:

```text
copied 1000 doubles
moved 1000 doubles
after move, a.size = 0 (moved-from)
```

Copying `b` allocated and duplicated 1000 doubles; moving `c` just swapped pointers. For an 8 MB vector, that's the difference between an 8 MB memcpy and three assignments.

### 13.4 `std::move` and when moves happen

**`std::move(x)`** does *not* move anything — it's just a **cast** that turns an lvalue into an rvalue reference, *telling the compiler "you may steal from `x`."* The actual moving is done by the move constructor/assignment that the cast selects.

Moves happen **automatically** for rvalues, and you request them explicitly with `std::move`:

```cpp
Vec make() { return Vec(1000); }     // return value is an rvalue → moved (or elided by RVO)
std::vector<Vec> v;
v.push_back(Vec(500));               // temporary Vec(500) is an rvalue → MOVED into the vector
v.push_back(std::move(existing));    // explicit: steal from a named lvalue you're done with
```

Verified: `v.push_back(Vec(500))` prints `moved 500 doubles` — the temporary was moved, not copied. This is why returning big objects by value (Chapter 6) and growing a `std::vector` are cheap: the elements move.

> ⚠️ **Gotcha** — Don't `std::move` a value you still need — after moving, its state is *unspecified* (for our `Vec`, empty). And **don't `std::move` a local you're returning**: `return std::move(local);` actually *disables* RVO (Chapter 6), making it slower, not faster. Just `return local;` — the compiler moves or elides automatically. Reserve explicit `std::move` for when you're genuinely done with a named object and want to transfer it (e.g., into a container).

### 13.5 The moved-from state and `noexcept`

After a move, the source is in a **valid but unspecified state** — you may safely destroy it or assign to it, but you shouldn't assume its value. For our `Vec`, moved-from means `size() == 0`. The standard library guarantees this for its types (a moved-from `std::vector` is empty).

Move operations should be marked **`noexcept`** — and this is not cosmetic. `std::vector`, when it grows and must relocate its elements to a bigger buffer, will only *move* them (instead of copying) if their move constructor is `noexcept`; otherwise it copies, to preserve its strong exception guarantee.

> 💡 **Idiom** — Always mark your move constructor and move assignment **`noexcept`**. It's usually true (stealing pointers can't throw), and it unlocks the fast path: `std::vector` and other containers will *move* your objects during reallocation only if the move is `noexcept`. A non-`noexcept` move silently degrades to copies inside containers — a subtle, real performance loss in scientific code that grows large vectors.

> ⚙️ **Under the hood** — Copy elision and RVO (Chapter 6) mean that in many cases *neither* a copy *nor* a move happens — the object is constructed directly in its destination. Move semantics is the fallback for when elision can't apply (e.g., moving into an existing container element, or a conditional return). The three-tier hierarchy — elide if possible, else move, else copy — is why modern C++ passes and returns large objects by value with a clear conscience. And crucially: a class following the **Rule of Zero** (Chapter 12) gets correct, `noexcept`, member-wise moves *for free* — you rarely write a move constructor yourself.

---

### Summary

- **Move semantics** transfers ownership of a resource instead of copying it — cheap (pointer swaps) regardless of size.
- **lvalues** (named, persistent) vs **rvalues** (temporaries, about to die); an **rvalue reference `T&&`** binds only to rvalues.
- A **move constructor** (`T(T&&)`) *steals* the source's resource and empties the source; no allocation, no element copy.
- **`std::move`** is a cast (lvalue→rvalue) that *permits* stealing; moves happen automatically for rvalues (temporaries, returns). Don't `std::move` a `return local;` (it disables RVO) or a value you still need.
- Moved-from objects are **valid but unspecified**; mark moves **`noexcept`** so containers use the fast move path. **Rule of Zero** classes get correct moves for free.

### Self-check quiz

1. What's the difference between an lvalue and an rvalue?
   <details><summary>Answer</summary>An lvalue has a name/persistent location (e.g. a variable); an rvalue is a temporary with no lasting identity (e.g. `Vec(500)`, a by-value return). Rvalues are safe to steal from.</details>
2. What does a move constructor do that a copy constructor doesn't?
   <details><summary>Answer</summary>It steals the source's resource (copies the pointer, empties the source) instead of allocating and deep-copying — cheap regardless of size.</details>
3. Does `std::move(x)` move `x`?
   <details><summary>Answer</summary>No — it's a cast that turns `x` into an rvalue, *allowing* a move. The move is done by the move constructor/assignment the cast selects.</details>
4. Why mark move operations `noexcept`?
   <details><summary>Answer</summary>So containers like `std::vector` use the fast *move* path (not copy) when reallocating; a non-`noexcept` move degrades to copies to preserve exception safety.</details>

### Exercises

**Exercise 13.1 — Observe copy vs move (guided).** Using a class that prints in its copy and move constructors, show that assigning a variable copies but assigning `std::move(var)` moves.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <utility>
struct Loud {
    Loud() = default;
    Loud(const Loud&) { std::cout << "copy\n"; }
    Loud(Loud&&) noexcept { std::cout << "move\n"; }
};
int main() {
    Loud a;
    Loud b = a;              // copy
    Loud c = std::move(a);   // move
}
```

Output:
```text
copy
move
```

**Why this works:** `Loud b = a;` binds the lvalue `a` to the copy constructor (`const Loud&`); `std::move(a)` casts to an rvalue, selecting the move constructor. The prints reveal which ran.

</details>

**Exercise 13.2 — Move into a vector.** Push a temporary and a `std::move`d local into a `std::vector<Loud>`; observe both are moves.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <utility>
#include <vector>
struct Loud {
    Loud() = default;
    Loud(const Loud&) { std::cout << "copy\n"; }
    Loud(Loud&&) noexcept { std::cout << "move\n"; }
};
int main() {
    std::vector<Loud> v;
    v.reserve(2);            // avoid reallocation noise
    v.push_back(Loud{});     // temporary → move
    Loud local;
    v.push_back(std::move(local));   // explicit move
}
```

Output:
```text
move
move
```

**Why this works:** the temporary `Loud{}` is an rvalue, so `push_back` moves it; `std::move(local)` casts the named `local` to an rvalue, moving it too. `reserve(2)` prevents a reallocation (which would otherwise move existing elements and add prints). Growing a `std::vector` of movable types is cheap.

</details>

**Exercise 13.3 — Don't move a return.** Explain why `return std::move(local);` is worse than `return local;`.

<details><summary>Show answer</summary>

`return local;` lets the compiler apply **RVO/NRVO** — constructing `local` directly in the caller's storage, so *no* copy *or* move happens at all. Writing `return std::move(local);` turns the return expression into an rvalue *reference*, which **disables** RVO; the compiler must then perform an actual move construction. So `std::move` on a return makes it *slower* (a move instead of nothing) and is a common anti-pattern. Rule: `return local;` — the compiler moves or elides automatically.

</details>

### Chapter project: cheap dataset transfer

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–13. We show that the toolkit's `Dataset` (Chapter 12, Rule of Zero) *moves* instead of copies when returned or transferred — cheap even for millions of events.

**Goal.** A function returning a large `Dataset` by value, and a transfer via `std::move`, confirming moves (not copies) via element-count arithmetic.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <utility>

class Dataset {
    std::vector<double> energies_;
public:
    void add(double e) { energies_.push_back(e); }
    std::size_t size() const { return energies_.size(); }
    double mean() const {
        if (energies_.empty()) return 0.0;
        double s = 0.0; for (double e : energies_) s += e; return s / energies_.size();
    }
};

Dataset generate(std::size_t n) {          // returns a big Dataset BY VALUE (moved/elided)
    Dataset d;
    for (std::size_t i = 0; i < n; ++i) d.add(91.0 + (i % 5) * 0.1);
    return d;                              // no copy — RVO or move
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v10 ===\n";
    Dataset data = generate(1'000'000);    // a million events — returned cheaply
    std::cout << std::format("generated {} events, mean = {:.4f} GeV\n", data.size(), data.mean());

    Dataset moved = std::move(data);       // transfer ownership — no 8 MB copy
    std::cout << std::format("after move: moved={} events, source={} events\n",
                             moved.size(), data.size());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v10 ===
generated 1000000 events, mean = 91.2000 GeV
after move: moved=1000000 events, source=0 events
```

**Commentary.**
- `generate` returns a **million-event `Dataset` by value** — but there's no million-element copy: RVO constructs it directly in `data`, or (if elision can't apply) it's *moved*. Returning big objects by value is idiomatic *because* of move semantics.
- `Dataset moved = std::move(data);` **transfers** the million events — the internal `std::vector` buffer is stolen, not duplicated. Afterward the source is empty (`0 events`) — the valid-but-unspecified moved-from state (§13.5).
- `Dataset` is a **Rule of Zero** class (Chapter 12), so its move constructor is compiler-generated, `noexcept`, and member-wise — it moves the `std::vector`, which itself moves in O(1). You wrote *no* move code, yet transferring a million events costs three pointer assignments.
- This is why the toolkit can pass datasets around freely: with Rule of Zero + move semantics, "by value" is cheap.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **lvalue / rvalue** | Named persistent object / temporary about to die. |
| **Rvalue reference (`T&&`)** | A reference binding only to rvalues (temporaries). |
| **Move constructor** | `T(T&&)` — steals the source's resource, empties it. |
| **`std::move`** | A cast (lvalue→rvalue) permitting a move; moves nothing itself. |
| **Moved-from state** | Valid but unspecified (often empty). |
| **`noexcept` move** | Promise enabling containers' fast move-on-reallocation path. |
| **Copy elision / RVO** | Constructing directly in the destination — no copy or move. |

### What's next

You can transfer resources cheaply. Now the tool that automates ownership entirely: **[Ch.14 — Smart Pointers](#chapter-14--smart-pointers)** — `unique_ptr` and `shared_ptr` give you heap objects with automatic, leak-free lifetime management and clear ownership, eliminating raw `new`/`delete` from your code for good.

[↑ back to top](#chapter-13--move-semantics)


---

## Chapter 14 — Smart Pointers

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — RAII](#chapter-11--dynamic-memory--raii), [Ch.13 — Move Semantics](#chapter-13--move-semantics)

**Learning objectives** — after this chapter you will be able to:

- Use `std::unique_ptr` for exclusive ownership of a heap object.
- Use `std::shared_ptr` for shared ownership, and `std::weak_ptr` to break cycles.
- Choose the right ownership model, and eliminate raw `new`/`delete`.

**In this chapter**

- [14.1 Why smart pointers](#141-why-smart-pointers)
- [14.2 `unique_ptr`: exclusive ownership](#142-unique_ptr-exclusive-ownership)
- [14.3 `shared_ptr`: shared ownership](#143-shared_ptr-shared-ownership)
- [14.4 `weak_ptr`: breaking cycles](#144-weak_ptr-breaking-cycles)
- [14.5 Choosing an ownership model](#145-choosing-an-ownership-model)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-detector-owning-sensors) · Glossary · What's next

---

### 14.1 Why smart pointers

Chapter 11 showed that raw `new`/`delete` invites leaks and dangling pointers, and RAII is the cure. **Smart pointers** are the standard library's RAII wrappers for *heap objects*: they own a `new`ed object and `delete` it automatically when they go out of scope. With them, you get heap allocation's flexibility (runtime-sized, polymorphic, long-lived objects) *without* manual memory management — and, crucially, they encode **ownership** in the type, so it's clear from a signature who is responsible for an object's lifetime.

There are two you'll use constantly — `std::unique_ptr` and `std::shared_ptr` (from `<memory>`) — plus `std::weak_ptr` for a special case.

### 14.2 `unique_ptr`: exclusive ownership

A **`std::unique_ptr<T>`** owns a heap object *exclusively* — there is exactly one owner, and when it's destroyed, the object is destroyed. It's **move-only** (you can transfer ownership but not copy it, Chapter 12's move-only design). Create one with **`std::make_unique`**:

```cpp
auto s = std::make_unique<Sensor>(1);   // heap Sensor, owned by s
s->read();                               // use it like a pointer (-> and *)
auto s2 = std::move(s);                  // TRANSFER ownership; s is now null
// s == nullptr is true
```

When `s2` leaves scope, the `Sensor` is destroyed automatically — no `delete`:

```text
Sensor 1 created
reading sensor 1
s is null: true
Sensor 1 destroyed
```

`unique_ptr` has **zero overhead** — it's the size of a raw pointer, and its operations compile to the same code you'd write by hand, but with guaranteed cleanup.

> 💡 **Idiom** — **Prefer `std::make_unique<T>(args)`** over `std::unique_ptr<T>(new T(args))`. It's exception-safe (no raw `new` that could leak if something else in the expression throws), shorter, and never mentions `new`. `unique_ptr` should be your **default** for a dynamically-allocated object — it's exclusive, zero-overhead, and expresses "one owner" clearly. Return it from factory functions to hand ownership to the caller.

### 14.3 `shared_ptr`: shared ownership

Sometimes an object genuinely has *several* owners, and should live until the *last* one is done. **`std::shared_ptr<T>`** provides this via **reference counting**: it keeps a count of how many `shared_ptr`s point at the object, and destroys it when the count hits zero. Copyable (each copy increments the count); create with **`std::make_shared`**:

```cpp
auto sh = std::make_shared<Sensor>(2);
// sh.use_count() == 1
{
    auto sh2 = sh;                    // shared: both own it
    // sh.use_count() == 2
}                                     // sh2 destroyed → count back to 1
// sh.use_count() == 1
// ...object destroyed when the last shared_ptr (sh) dies
```

Verified: the count goes `1 → 2 → 1`, and `Sensor 2` is destroyed only at the very end, when the final `shared_ptr` is gone.

> ⚠️ **Gotcha** — `shared_ptr` is **not free**: it carries a heap-allocated *control block* (the reference count), and count updates are *atomic* (thread-safe), which costs performance. Overusing `shared_ptr` — making everything shared "to be safe" — bloats memory and slows code, and obscures who really owns what. Use it only when ownership is *genuinely* shared. Also beware **reference cycles** (§14.4), which `shared_ptr` alone can't reclaim.

### 14.4 `weak_ptr`: breaking cycles

Reference counting has one blind spot: a **cycle**. If object A holds a `shared_ptr` to B and B holds one back to A, their counts never reach zero even when nothing else references them — a leak. A **`std::weak_ptr<T>`** is a *non-owning* observer of a `shared_ptr`'s object: it doesn't affect the count, and you must `lock()` it to get a usable `shared_ptr` (which is null if the object is already gone):

```cpp
std::shared_ptr<Node> a = std::make_shared<Node>();
std::weak_ptr<Node> observer = a;        // does NOT increase the count
if (auto p = observer.lock()) {          // try to get a shared_ptr
    // p is valid — use it
}                                         // (null if a was already destroyed)
```

Use `weak_ptr` for the "back-edge" of a relationship (a child pointing to its parent, a cache entry pointing to its owner) to break ownership cycles.

### 14.5 Choosing an ownership model

A simple decision hierarchy for a heap object:

1. **Do you need heap allocation at all?** Often not — a local or a `std::vector<T>` (which owns its elements) is better. Prefer values and containers.
2. **One owner?** → **`std::unique_ptr<T>`** (the default; zero overhead).
3. **Genuinely shared ownership** (several owners, lifetime = last one)? → **`std::shared_ptr<T>`**.
4. **Non-owning reference** to a shared object (avoid a cycle)? → **`std::weak_ptr<T>`**.
5. **Non-owning "just look at it"** where lifetime is guaranteed elsewhere? → a **raw pointer or reference** (Chapter 10).

> 💡 **Idiom** — This is the whole ownership story: `std::vector`/values for collections, **`unique_ptr` by default** for single heap objects, `shared_ptr` only for true sharing, `weak_ptr` to break cycles, raw pointer/reference for non-owning observation. Following it, **you should essentially never write `new` or `delete`** in application code again. Ownership becomes visible in your types — a function taking a `unique_ptr` by value clearly *takes* ownership; one taking a `const T&` clearly just *borrows*.

> ⚙️ **Under the hood** — `unique_ptr` is a zero-cost abstraction: one pointer, its destructor calls `delete`. `shared_ptr` is *two* pointers (to the object and to a control block holding the atomic reference count); `make_shared` allocates the object and control block together in one block (faster, better cache locality). The atomic count is why `shared_ptr` is thread-safe to copy but costs more than `unique_ptr` — the reason "unique by default" is also the performance-optimal default.

---

### Summary

- **Smart pointers** (`<memory>`) are RAII for heap objects — automatic `delete`, ownership encoded in the type — replacing raw `new`/`delete`.
- **`std::unique_ptr<T>`** — exclusive owner, move-only, zero overhead; create with **`make_unique`**; the **default** for single heap objects.
- **`std::shared_ptr<T>`** — shared ownership via atomic reference counting; create with **`make_shared`**; use only for *genuine* sharing (it has real overhead).
- **`std::weak_ptr<T>`** — non-owning observer; `lock()` to use; breaks **reference cycles**.
- Ownership hierarchy: values/containers → `unique_ptr` → `shared_ptr` → `weak_ptr` → raw pointer/reference (non-owning). With it, **stop writing `new`/`delete`**.

### Self-check quiz

1. What's the difference between `unique_ptr` and `shared_ptr`?
   <details><summary>Answer</summary>`unique_ptr` has exactly one owner (move-only, zero overhead); `shared_ptr` allows several owners via atomic reference counting (destroys the object when the last owner dies, at a runtime cost).</details>
2. Why prefer `make_unique`/`make_shared` over `unique_ptr<T>(new T)`?
   <details><summary>Answer</summary>They're exception-safe (no raw `new` to leak), shorter, and never mention `new`. `make_shared` also allocates object + control block together for efficiency.</details>
3. When do you need `weak_ptr`?
   <details><summary>Answer</summary>To observe a `shared_ptr`'s object without owning it — especially to break reference cycles (which reference counting can't reclaim), like a back-pointer to a parent.</details>
4. What's the default smart pointer, and why?
   <details><summary>Answer</summary>`unique_ptr` — it's exclusive, zero-overhead, and clearly expresses single ownership. Reach for `shared_ptr` only when ownership is genuinely shared.</details>

### Exercises

**Exercise 14.1 — Factory returning `unique_ptr` (guided).** Write `make_sensor(int)` returning `std::unique_ptr<Sensor>`, and use it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
struct Sensor {
    int id;
    explicit Sensor(int i) : id(i) {}
    void read() const { std::cout << std::format("sensor {}\n", id); }
};
std::unique_ptr<Sensor> make_sensor(int id) { return std::make_unique<Sensor>(id); }
int main() {
    auto s = make_sensor(42);   // caller receives ownership
    s->read();
}   // Sensor auto-deleted here
```

Output:
```text
sensor 42
```

**Why this works:** `make_sensor` returns a `unique_ptr` by value, *transferring* ownership to the caller (moved out, Chapter 13). The caller uses it with `->` and never deletes it — the `unique_ptr`'s destructor does that at scope exit. This is the idiomatic C++ factory.

</details>

**Exercise 14.2 — Shared ownership count.** Create a `shared_ptr`, make two more copies, and print the `use_count` at each step.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
int main() {
    auto p1 = std::make_shared<int>(99);
    std::cout << std::format("count = {}\n", p1.use_count());   // 1
    auto p2 = p1;
    auto p3 = p1;
    std::cout << std::format("count = {}\n", p1.use_count());   // 3
    p2.reset();                                                  // p2 releases
    std::cout << std::format("count = {}\n", p1.use_count());   // 2
}
```

Output:
```text
count = 1
count = 3
count = 2
```

**Why this works:** each copy of the `shared_ptr` increments the reference count (1 → 3); `p2.reset()` releases one owner (→ 2). The `int` is destroyed only when the count reaches 0 (when `p1` and `p3` die at scope end).

</details>

**Exercise 14.3 — No more `new`.** Rewrite this leaky code with a smart pointer.

```cpp
void f() {
    Sensor* s = new Sensor(1);
    s->read();
    // (no delete → leak)
}
```

<details><summary>Show solution</summary>

```cpp
#include <memory>
void f() {
    auto s = std::make_unique<Sensor>(1);   // owns the Sensor
    s->read();
}                                            // auto-deleted — no leak
```

**Why this works:** `std::make_unique<Sensor>(1)` heap-allocates the `Sensor` and hands it to a `unique_ptr` that deletes it at scope exit. The leak is gone, the code is shorter, and there's no `new`/`delete` — the modern default.

</details>

### Chapter project: a detector owning sensors

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–14. A detector owns many sensors, created at runtime. We manage them with `unique_ptr` in a `std::vector` — heap objects, automatic cleanup, zero manual memory management.

**Goal.** A `Detector` owning a `std::vector<std::unique_ptr<Sensor>>`, added at runtime, all auto-destroyed.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
#include <vector>

struct Sensor {
    int id;
    explicit Sensor(int i) : id(i) { std::cout << std::format("  Sensor {} online\n", i); }
    ~Sensor() { std::cout << std::format("  Sensor {} offline\n", id); }
    double read() const { return 90.0 + id * 0.5; }
};

class Detector {
    std::vector<std::unique_ptr<Sensor>> sensors_;   // owns its sensors
public:
    void add(int id) { sensors_.push_back(std::make_unique<Sensor>(id)); }
    double total_reading() const {
        double s = 0.0;
        for (const auto& sensor : sensors_) s += sensor->read();
        return s;
    }
    std::size_t count() const { return sensors_.size(); }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v11 — detector ===\n";
    Detector d;
    d.add(1); d.add(2); d.add(3);
    std::cout << std::format("{} sensors, total reading = {:.1f} GeV\n", d.count(), d.total_reading());
}   // Detector destroyed → its vector destroyed → every unique_ptr deletes its Sensor
```

Output:

```text
=== Monte Carlo Analysis Toolkit v11 — detector ===
  Sensor 1 online
  Sensor 2 online
  Sensor 3 online
3 sensors, total reading = 273.0 GeV
  Sensor 1 offline
  Sensor 2 offline
  Sensor 3 offline
```

**Commentary.**
- `Detector` owns a `std::vector<std::unique_ptr<Sensor>>` — the sensors are heap objects (created at runtime with `make_unique`), but the toolkit writes *no* `new`/`delete`. When the `Detector` dies, its vector dies, and each `unique_ptr` deletes its `Sensor` — note the "offline" messages fire automatically (the vector destroys its elements in order).
- `unique_ptr` here expresses that the `Detector` **exclusively owns** its sensors. The reading loop borrows each via `const auto&` (no ownership transfer, no copy). This is the standard pattern for a container of heap-allocated objects — which becomes powerful once the sensors have *different types* via inheritance (Chapter 15).
- Readings: `sensor->read()` gives `90+0.5·id`, so 90.5 + 91.0 + 91.5 = 273.0. Everything is leak-free (AddressSanitizer confirms) with zero memory-management code.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Smart pointer** | An RAII wrapper owning a heap object (`<memory>`). |
| **`unique_ptr`** | Exclusive owner; move-only; zero overhead. |
| **`make_unique` / `make_shared`** | Exception-safe smart-pointer factories. |
| **`shared_ptr`** | Shared owner via atomic reference counting. |
| **`use_count`** | The number of `shared_ptr`s owning an object. |
| **`weak_ptr`** | Non-owning observer of a `shared_ptr`; `lock()` to use. |
| **Reference cycle** | Mutual `shared_ptr`s that never reach count 0 (leak). |
| **Control block** | The heap block holding a `shared_ptr`'s reference count. |

### What's next

You can manage heap objects safely — and a `unique_ptr<Base>` can own an object of a *derived* type. **[Ch.15 — Inheritance & Polymorphism](#chapter-15--inheritance--polymorphism)** introduces base classes, virtual functions, and polymorphism, letting a detector hold sensors of many kinds behind one interface — the object-oriented backbone of frameworks like Geant4 and ROOT.

[↑ back to top](#chapter-14--smart-pointers)


---

## Chapter 15 — Inheritance & Polymorphism

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Classes](#chapter-9--classes--objects), [Ch.14 — Smart Pointers](#chapter-14--smart-pointers)

**Learning objectives** — after this chapter you will be able to:

- Derive classes and override virtual functions.
- Define abstract base classes (interfaces) and use runtime polymorphism.
- Understand virtual destructors, object slicing, and vtables.
- Judge when to use inheritance vs composition/templates in HPC.

**In this chapter**

- [15.1 Inheritance and virtual functions](#151-inheritance-and-virtual-functions)
- [15.2 Abstract base classes](#152-abstract-base-classes)
- [15.3 Polymorphism through base pointers](#153-polymorphism-through-base-pointers)
- [15.4 Virtual destructors and slicing](#154-virtual-destructors-and-slicing)
- [15.5 Inheritance vs composition and templates](#155-inheritance-vs-composition-and-templates)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-polymorphic-detector) · Glossary · What's next

---

### 15.1 Inheritance and virtual functions

**Inheritance** lets a **derived** class extend a **base** class, reusing and specializing it. A member function marked **`virtual`** can be *overridden* in a derived class, and — the key to polymorphism — the *derived* version runs even when called through a *base* pointer or reference:

```cpp
class Shape {
public:
    virtual double area() const { return 0.0; }   // virtual: overridable
};
class Circle : public Shape {                       // Circle IS-A Shape
public:
    explicit Circle(double r) : r_(r) {}
    double area() const override { return 3.14159 * r_ * r_; }   // override
private:
    double r_;
};
```

`class Circle : public Shape` means "Circle publicly inherits from Shape" — a Circle *is a* Shape and can be used wherever a Shape is expected. The **`override`** keyword is optional but you should always use it: it makes the compiler *check* that you're actually overriding a base virtual (catching typos and signature mismatches — a common, silent bug without it).

### 15.2 Abstract base classes

A **pure virtual** function (`= 0`) has no implementation and makes its class **abstract** — you can't instantiate it directly; it exists to define an *interface* that derived classes must implement:

```cpp
class Sensor {
public:
    virtual ~Sensor() = default;               // (see §15.4)
    virtual std::string name() const = 0;      // pure virtual → must be overridden
    virtual double read() const = 0;
};
```

`Sensor` is an **interface**: it declares *what* every sensor can do (`name`, `read`) without saying *how*. Concrete sensors implement it:

```cpp
class Calorimeter : public Sensor {
public:
    explicit Calorimeter(double e) : energy_(e) {}
    std::string name() const override { return "Calorimeter"; }
    double read() const override { return energy_; }
private:
    double energy_;
};
class Tracker : public Sensor {
public:
    explicit Tracker(int hits) : hits_(hits) {}
    std::string name() const override { return "Tracker"; }
    double read() const override { return hits_ * 1.5; }
private:
    int hits_;
};
```

This is exactly how frameworks like **Geant4** and **ROOT** are built: abstract base classes define interfaces (a detector component, a physics process), and concrete classes plug in.

### 15.3 Polymorphism through base pointers

**Runtime polymorphism** is the payoff: hold different derived objects behind *one* base interface (via a pointer or reference — typically a `unique_ptr<Base>` from Chapter 14), and the *right* override runs for each:

```cpp
std::vector<std::unique_ptr<Sensor>> sensors;
sensors.push_back(std::make_unique<Calorimeter>(125.0));
sensors.push_back(std::make_unique<Tracker>(40));

for (const auto& s : sensors)
    std::cout << std::format("{:12}: {:.1f}\n", s->name(), s->read());
```

Output:

```text
Calorimeter : 125.0
Tracker     : 60.0
```

`s->read()` calls `Calorimeter::read` for the first and `Tracker::read` for the second — chosen *at runtime* by the actual object type, though the loop only knows `Sensor`. One loop, heterogeneous behaviour: that's polymorphism. (Adding a new sensor type needs no change to this loop — the open/closed principle.)

> ⚙️ **Under the hood — the vtable.** Runtime polymorphism works via a **virtual table (vtable)**: each polymorphic class has a hidden table of pointers to its virtual functions, and each object carries a hidden pointer (the *vptr*) to its class's vtable. A call like `s->read()` looks up `read` in the object's vtable and jumps there — an *indirect* call decided at runtime. This costs a pointer indirection per virtual call (and blocks inlining), which is why virtual calls aren't free — a real consideration in hot loops (§15.5, Chapter 33). Non-virtual calls have no such cost.

### 15.4 Virtual destructors and slicing

Two hazards define correct polymorphic code.

**Virtual destructors.** If you `delete` a derived object *through a base pointer* and the base destructor is **not `virtual`**, only the base part is destroyed — the derived part leaks (and it's undefined behaviour). Rule: **a base class intended for polymorphic use must have a `virtual` destructor**:

```cpp
class Sensor {
public:
    virtual ~Sensor() = default;   // ← essential; without it, delete via Sensor* is UB
    // ...
};
```

`std::unique_ptr<Sensor>` deleting a `Calorimeter` works *only* because `~Sensor` is virtual — the destructor call is dispatched to `~Calorimeter`.

**Object slicing.** If you copy a derived object *into a base value* (not a pointer/reference), the derived part is "sliced off" — you get only the base:

```cpp
Calorimeter c(125.0);
Sensor s = c;        // ❌ (won't compile here since Sensor is abstract, but with a concrete base:)
// s would be sliced — only the Sensor part copied, polymorphism lost
```

> ⚠️ **Gotcha** — **Slicing** is why polymorphism *requires* pointers or references, never values. `std::vector<Sensor>` (by value) would slice every object to the base; `std::vector<std::unique_ptr<Sensor>>` (pointers) preserves the derived types. Always store and pass polymorphic objects by `unique_ptr<Base>`, `Base*`, or `Base&` — never by base value. And always give a polymorphic base a `virtual ~Base()`.

### 15.5 Inheritance vs composition and templates

Inheritance is powerful but often *overused*. In scientific/HPC code especially, weigh it against the alternatives:

- **Composition** ("has-a") — a class *contains* another as a member — is usually more flexible than inheritance ("is-a"). Prefer composition unless you genuinely need a shared interface with runtime substitutability.
- **Templates** (Chapter 16) give *compile-time* polymorphism with **zero runtime cost** (no vtable, fully inlinable) — ideal for hot numerical kernels where a virtual call per element would dominate. A `template<class T> void process(T& sensor)` picks the right `read()` at compile time.

> 💡 **Idiom** — Use **runtime polymorphism (virtual/inheritance)** when you need a *heterogeneous collection* behind one interface, chosen at runtime (a detector's mixed sensors, ROOT's object hierarchy, a plugin system) — the flexibility is worth the vtable indirection. Use **templates (compile-time polymorphism)** in *performance-critical* generic code where the type is known at compile time and the virtual-call overhead per element would matter (a numerical algorithm over a known scalar type). Geant4/ROOT lean on inheritance for their extensible frameworks; a tight simulation kernel leans on templates. Knowing which to reach for is a mark of an expert C++ scientist.

---

### Summary

- **Inheritance** (`class D : public B`) makes D an extended B; **`virtual`** functions are overridable, and the override runs even through a base pointer/reference — always mark overrides **`override`**.
- A **pure virtual** (`= 0`) makes a class **abstract** — an interface derived classes implement (the Geant4/ROOT pattern).
- **Runtime polymorphism**: hold derived objects behind a base pointer (`unique_ptr<Base>`), and the correct override runs per object — via a **vtable** (a per-call indirection).
- A polymorphic base **must have a `virtual` destructor** (else deleting through the base is UB); store polymorphic objects by pointer/reference to avoid **slicing**.
- Prefer **composition** over inheritance; use **templates** (compile-time polymorphism, zero overhead) for hot generic code, and **virtual/inheritance** for runtime-heterogeneous collections.

### Self-check quiz

1. Why always write `override`?
   <details><summary>Answer</summary>It makes the compiler verify you're actually overriding a base virtual; without it, a signature typo silently creates a *new* function instead of overriding — a common bug.</details>
2. What makes a class abstract, and what's it for?
   <details><summary>Answer</summary>A pure virtual function (`= 0`) makes the class abstract (non-instantiable); it defines an interface that derived classes must implement.</details>
3. Why must a polymorphic base class have a virtual destructor?
   <details><summary>Answer</summary>So that deleting a derived object through a base pointer dispatches to the derived destructor; without it, only the base part is destroyed (leak + UB).</details>
4. When choose templates over virtual inheritance?
   <details><summary>Answer</summary>In performance-critical generic code where the type is known at compile time — templates give zero-overhead compile-time polymorphism (no vtable, inlinable), avoiding the per-call virtual indirection.</details>

### Exercises

**Exercise 15.1 — Shape hierarchy (guided).** An abstract `Shape` with `virtual double area() const = 0`, and `Circle`/`Square`; compute total area polymorphically.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
#include <vector>
class Shape { public: virtual ~Shape() = default; virtual double area() const = 0; };
class Circle : public Shape { double r_; public: explicit Circle(double r):r_(r){}
    double area() const override { return 3.14159 * r_ * r_; } };
class Square : public Shape { double s_; public: explicit Square(double s):s_(s){}
    double area() const override { return s_ * s_; } };
int main() {
    std::vector<std::unique_ptr<Shape>> shapes;
    shapes.push_back(std::make_unique<Circle>(1.0));
    shapes.push_back(std::make_unique<Square>(2.0));
    double total = 0.0;
    for (const auto& s : shapes) total += s->area();
    std::cout << std::format("total area = {:.5f}\n", total);   // 3.14159 + 4 = 7.14159
}
```

Output:
```text
total area = 7.14159
```

**Why this works:** `Shape` is an abstract interface; `Circle`/`Square` override `area()`. The loop calls `s->area()` through `Shape*`, and each object's *own* `area()` runs (vtable dispatch) — so `total` is `π·1² + 2² ≈ 7.14159`. The virtual destructor makes deleting through `unique_ptr<Shape>` safe.

</details>

**Exercise 15.2 — Physics process interface.** Define an abstract `Process` with `virtual double cross_section(double E) const = 0`, and two processes; print each at E=100.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
#include <vector>
#include <cmath>
class Process { public: virtual ~Process() = default; virtual double cross_section(double E) const = 0;
    virtual const char* name() const = 0; };
class Ionization : public Process { public:
    double cross_section(double E) const override { return 10.0 / E; }
    const char* name() const override { return "Ionization"; } };
class Bremsstrahlung : public Process { public:
    double cross_section(double E) const override { return 0.01 * std::log(E); }
    const char* name() const override { return "Bremsstrahlung"; } };
int main() {
    std::vector<std::unique_ptr<Process>> procs;
    procs.push_back(std::make_unique<Ionization>());
    procs.push_back(std::make_unique<Bremsstrahlung>());
    for (const auto& p : procs)
        std::cout << std::format("{:15}: sigma(100) = {:.4f}\n", p->name(), p->cross_section(100.0));
}
```

Output:
```text
Ionization     : sigma(100) = 0.1000
Bremsstrahlung : sigma(100) = 0.0461
```

**Why this works:** `Process` is an interface (as in Geant4); each concrete process overrides `cross_section`. The loop treats them uniformly through `Process*`, and each computes its own physics — `10/100 = 0.1` and `0.01·ln(100) ≈ 0.0461`. Adding a new process needs no change to the loop.

</details>

**Exercise 15.3 — Spot the missing `virtual`.** This code leaks the derived part. What's wrong, and how do you fix it?

```cpp
class Base { public: ~Base() { /* ... */ } };
class Derived : public Base { std::vector<double> big_; public: Derived() : big_(1000) {} };
// std::unique_ptr<Base> p = std::make_unique<Derived>();  // deleting via Base* ...
```

<details><summary>Show answer</summary>

**Wrong:** `~Base()` is **not virtual**, so deleting a `Derived` through a `Base*`/`unique_ptr<Base>` calls only `~Base` — `Derived::big_` (its 1000-element vector) is never destroyed → leak + undefined behaviour. **Fix:** make the base destructor virtual:

```cpp
class Base { public: virtual ~Base() = default; };
```

Now deleting through `Base*` dispatches to `~Derived` first (which destroys `big_`), then `~Base`. **Rule:** any class used polymorphically (has virtual functions, or is deleted through a base pointer) must have a `virtual` destructor.

</details>

### Chapter project: a polymorphic detector

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit** — the OOP centrepiece. **Builds on:** Ch.1–15. A real detector has *different kinds* of sensors. We make `Sensor` an abstract interface and give the `Detector` a heterogeneous, polymorphic collection.

**Goal.** An abstract `Sensor` with `Calorimeter` and `Tracker` implementations, held polymorphically by a `Detector`.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <memory>
#include <vector>
#include <string>

class Sensor {
public:
    virtual ~Sensor() = default;                 // virtual dtor — essential
    virtual std::string name() const = 0;        // interface
    virtual double read() const = 0;
};

class Calorimeter : public Sensor {
    double energy_;
public:
    explicit Calorimeter(double e) : energy_(e) {}
    std::string name() const override { return "Calorimeter"; }
    double read() const override { return energy_; }
};

class Tracker : public Sensor {
    int hits_;
public:
    explicit Tracker(int hits) : hits_(hits) {}
    std::string name() const override { return "Tracker"; }
    double read() const override { return hits_ * 1.5; }   // 1.5 GeV per hit (toy model)
};

class Detector {
    std::vector<std::unique_ptr<Sensor>> sensors_;
public:
    void install(std::unique_ptr<Sensor> s) { sensors_.push_back(std::move(s)); }
    double total_energy() const {
        double e = 0.0;
        for (const auto& s : sensors_) e += s->read();
        return e;
    }
    void report() const {
        for (const auto& s : sensors_)
            std::cout << std::format("  {:12}: {:.1f} GeV\n", s->name(), s->read());
    }
};

int main() {
    Detector d;
    d.install(std::make_unique<Calorimeter>(125.0));
    d.install(std::make_unique<Tracker>(40));
    d.install(std::make_unique<Calorimeter>(30.5));

    std::cout << "=== Monte Carlo Analysis Toolkit v12 — polymorphic detector ===\n";
    d.report();
    std::cout << std::format("total energy deposited = {:.1f} GeV\n", d.total_energy());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v12 — polymorphic detector ===
  Calorimeter : 125.0 GeV
  Tracker     : 60.0 GeV
  Calorimeter : 30.5 GeV
total energy deposited = 215.5 GeV
```

**Commentary.**
- `Sensor` is an **abstract interface**; `Calorimeter` and `Tracker` are concrete implementations. The `Detector` holds them polymorphically as `unique_ptr<Sensor>` — a *heterogeneous* collection (two calorimeters and a tracker) behind one interface.
- `report()` and `total_energy()` iterate uniformly, and each `s->read()` dispatches (via the vtable) to the object's real type — `Calorimeter::read` returns the energy, `Tracker::read` returns `hits × 1.5`. Total: 125.0 + 60.0 + 30.5 = 215.5 GeV.
- The **`virtual` destructor** makes deleting through `unique_ptr<Sensor>` correct; storing by `unique_ptr` (not value) avoids **slicing**. Adding a new sensor type (a `MuonChamber`) requires *no* change to `Detector` — just a new class. This is precisely the extensible design pattern of Geant4 and ROOT.
- For a *performance-critical* per-event loop over millions of hits, you'd reconsider the virtual call per read (§15.5) — but for a detector's handful of subsystem types, runtime polymorphism is exactly right.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Inheritance** | A derived class extending a base (`class D : public B`). |
| **`virtual` / `override`** | Overridable function / explicit override marker. |
| **Pure virtual (`= 0`)** | An unimplemented function making a class abstract. |
| **Abstract class / interface** | A class with pure virtuals; can't be instantiated. |
| **Runtime polymorphism** | The right override running through a base pointer/reference. |
| **vtable / vptr** | Per-class table of virtual functions / per-object pointer to it. |
| **Virtual destructor** | Required for safe `delete` through a base pointer. |
| **Object slicing** | Losing the derived part when copying into a base value. |

### What's next

That completes **Part 2 — Memory & Objects**: you can manage resources with RAII, move them cheaply, own them with smart pointers, and build polymorphic hierarchies. **Part 3 opens with [Ch.16 — Templates](#chapter-16--templates)**, the other kind of polymorphism — *compile-time* generics — that powers the STL and lets you write one numerical routine that works for `float`, `double`, or any type, with zero overhead.

[↑ back to top](#chapter-15--inheritance--polymorphism)


---

## Chapter 16 — Templates

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Headers](#chapter-8--headers-translation-units--the-build-model), [Ch.15 — Inheritance](#chapter-15--inheritance--polymorphism)

**Learning objectives** — after this chapter you will be able to:

- Write function and class templates that work for any type.
- Understand template argument deduction and instantiation.
- Use variadic templates and fold expressions.
- Explain why templates give zero-overhead compile-time polymorphism.

**In this chapter**

- [16.1 Why templates](#161-why-templates)
- [16.2 Function templates](#162-function-templates)
- [16.3 Class templates](#163-class-templates)
- [16.4 Variadic templates and fold expressions](#164-variadic-templates-and-fold-expressions)
- [16.5 Specialization, and templates in headers](#165-specialization-and-templates-in-headers)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-generic-statistics-accumulator) · Glossary · What's next

---

### 16.1 Why templates

Chapter 15 gave *runtime* polymorphism (virtual functions, chosen at run time, with a vtable cost). **Templates** give the other kind: *compile-time* polymorphism — you write code parameterized by a **type**, and the compiler generates a specialized version for each type you use it with, with **zero runtime overhead**.

The motivation is duplication. A function to find the maximum of two values, or the mean of a dataset, shouldn't be rewritten for `int`, `float`, and `double`. A template writes it *once*, for all types at once — and the entire STL (Chapter 18) is built this way.

### 16.2 Function templates

A **function template** declares one or more type parameters with `template<typename T>`, then uses `T` as a type. The compiler *deduces* `T` from the arguments:

```cpp
template<typename T>
T maximum(T a, T b) { return (a > b) ? a : b; }

// maximum(3, 7)     → 7     (T = int, deduced)
// maximum(2.5, 1.5) → 2.5   (T = double, deduced)
```

You don't specify `T` — the compiler infers it. The template works for *any* type supporting the operations used inside (here, `>`). A generic numeric mean:

```cpp
template<typename T>
double mean(const std::vector<T>& v) {
    double s = 0.0;
    for (const T& x : v) s += x;
    return v.empty() ? 0.0 : s / v.size();
}
// mean(vector<double>{91.0,91.2,90.8}) → 91.0000
// mean(vector<int>{1,2,3,4})           → 2.5000
```

One `mean`, working for `double`, `int`, `float`, `long`… `typename` and `class` are interchangeable here (`template<class T>` means the same).

> ⚙️ **Under the hood — instantiation.** A template is not code until *used*. When you call `maximum(3, 7)`, the compiler **instantiates** a concrete `maximum<int>` by substituting `int` for `T` — generating actual machine code for that type. Call it with `double` and it generates a *separate* `maximum<double>`. So a template is a *code generator*; each distinct type argument produces its own compiled function, each as efficient as if hand-written for that type. This is the "zero overhead" of templates — and also why heavy template use lengthens compile times and can grow the binary (code bloat).

### 16.3 Class templates

A **class template** parameterizes a whole type — the mechanism behind `std::vector<T>`, `std::unique_ptr<T>`, etc.:

```cpp
template<typename T>
class Box {
    T value_;
public:
    explicit Box(T v) : value_(v) {}
    T get() const { return value_; }
};

Box<double> bd(3.14);   // Box holding a double
Box<int>    bi(42);     // Box holding an int
// bd.get() → 3.14,  bi.get() → 42
```

Unlike function templates, class templates historically needed the type in angle brackets (`Box<double>`), though C++17's **class template argument deduction (CTAD)** often lets you omit it (`Box b{3.14};` deduces `Box<double>`). A class template can have multiple parameters, including *non-type* parameters (like a size): `template<typename T, std::size_t N> class Array;` — how `std::array<double, 3>` fixes its size at compile time.

### 16.4 Variadic templates and fold expressions

A **variadic template** takes *any number* of arguments of *any types*, via a *parameter pack* (`typename... Args`). Combined with a C++17 **fold expression**, you can, for example, sum an arbitrary argument list:

```cpp
template<typename... Args>
auto sum(Args... args) { return (args + ...); }   // fold: args[0] + args[1] + ... + args[n]

// sum(1, 2, 3, 4, 5) → 15
// sum(1.5, 2.5)      → 4
```

`(args + ...)` is a *fold* — it expands the pack `args` joined by `+`. Variadic templates power `std::make_unique`, `std::format`, `std::tuple`, and any interface that takes a variable number of typed arguments. (You'll rarely *write* them, but understanding them demystifies the STL.)

### 16.5 Specialization, and templates in headers

Sometimes a generic template needs a *different* implementation for a specific type. **Specialization** provides it:

```cpp
template<typename T> const char* type_name()        { return "unknown"; }
template<>           const char* type_name<double>() { return "double"; }   // specialization
template<>           const char* type_name<int>()    { return "int"; }
// type_name<double>() → "double"
```

Because a template is instantiated wherever it's used, its **full definition must be visible at every call site** — so templates live in **headers** (`.hpp`), not split into a `.cpp` (Chapter 8's ODR/`inline` mechanism). This is why STL containers and algorithms are header-only.

> 💡 **Idiom** — Reach for a **template** when you want the *same logic* to work across types with **no runtime cost** — generic numerical routines, containers, algorithms. Prefer it over runtime polymorphism (Chapter 15) in hot code, and over copy-pasting overloads. But keep template code *readable*: constrain what types are allowed with **concepts** (Chapter 20) so errors are clear, and don't over-genericize a function only ever used with `double`. Templates are the engine of high-performance generic C++ — the STL, Eigen, and every serious numerical library are templates end to end.

---

### Summary

- **Templates** give **compile-time polymorphism**: write code parameterized by a **type**, and the compiler generates a specialized, **zero-overhead** version per type used.
- A **function template** (`template<typename T>`) deduces `T` from its arguments; works for any type supporting the operations used.
- A **class template** parameterizes a whole type (`Box<T>`, like `std::vector<T>`); C++17 **CTAD** often lets you omit the `<T>`. Non-type parameters fix compile-time values (sizes).
- **Variadic templates** (`typename... Args`) + **fold expressions** (`(args + ...)`) handle any number of typed arguments — the basis of `make_unique`, `format`, `tuple`.
- **Specialization** gives a type-specific implementation. Templates are **instantiated** per use, so they live in **headers**.

### Self-check quiz

1. What does "the compiler instantiates a template" mean?
   <details><summary>Answer</summary>When you use a template with a concrete type, the compiler substitutes that type and generates actual machine code for that instantiation — one per distinct type argument.</details>
2. Why do templates give zero runtime overhead?
   <details><summary>Answer</summary>Each instantiation is compiled specifically for its type (chosen at compile time, no vtable/indirection), so it's as efficient as hand-written code for that type.</details>
3. Why must template definitions live in headers?
   <details><summary>Answer</summary>A template is instantiated wherever it's used, so its full definition must be visible at every call site — it can't be hidden in a separate `.cpp`.</details>
4. What's a fold expression?
   <details><summary>Answer</summary>A C++17 way to expand a variadic parameter pack with an operator, e.g. `(args + ...)` sums all the arguments.</details>

### Exercises

**Exercise 16.1 — Generic clamp (guided).** Write a `clamp(value, lo, hi)` template returning `value` bounded to `[lo, hi]`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
template<typename T>
T clamp(T value, T lo, T hi) {
    if (value < lo) return lo;
    if (value > hi) return hi;
    return value;
}
int main() {
    std::cout << std::format("{} {} {}\n", clamp(5, 0, 10), clamp(-3, 0, 10), clamp(2.5, 0.0, 1.0));
}
```

Output:
```text
5 0 1
```

**Why this works:** `clamp` works for any comparable type (`int`, `double`, …), deduced from the arguments. `clamp(5,0,10)` stays 5; `clamp(-3,0,10)` clamps up to 0; `clamp(2.5,0.0,1.0)` clamps down to 1.0. (The standard `std::clamp` exists — this shows how it's built.)

</details>

**Exercise 16.2 — Generic pair container.** Write a `Pair<A, B>` class template holding two values of possibly different types, with `first()`/`second()`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <string>
template<typename A, typename B>
class Pair {
    A a_; B b_;
public:
    Pair(A a, B b) : a_(a), b_(b) {}
    A first() const { return a_; }
    B second() const { return b_; }
};
int main() {
    Pair<std::string, double> p{"energy", 91.2};
    std::cout << std::format("{} = {}\n", p.first(), p.second());
}
```

Output:
```text
energy = 91.2
```

**Why this works:** two type parameters let `Pair` hold a `std::string` and a `double` together. This is essentially `std::pair` — one of the most-used class templates. (C++17 CTAD would even allow `Pair p{"energy", 91.2};`.)

</details>

**Exercise 16.3 — Variadic average.** Write an `average(args...)` template returning the mean of any number of numeric arguments.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
template<typename... Args>
double average(Args... args) {
    return (args + ... + 0.0) / sizeof...(args);   // fold sum / count
}
int main() {
    std::cout << std::format("{:.4f}\n", average(91.0, 91.2, 90.8, 91.1));   // 91.025
}
```

Output:
```text
91.0250
```

**Why this works:** the fold `(args + ... + 0.0)` sums all arguments (the `+ 0.0` seeds it as `double` and handles the empty case); `sizeof...(args)` is the argument count. So `average(91.0,91.2,90.8,91.1)` is `364.1/4 = 91.025`. Variadic templates let one function take any arity.

</details>

### Chapter project: a generic statistics accumulator

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–16. We make the toolkit's statistics **generic** — one accumulator that works for `double`, `float`, or `int` data — with zero overhead per type.

**Goal.** A `Stats<T>` class template accumulating values and reporting count, mean, and min/max, used with two element types.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <limits>

template<typename T>
class Stats {
    long   n_   = 0;
    double sum_ = 0.0;
    T min_ =  std::numeric_limits<T>::max();
    T max_ =  std::numeric_limits<T>::lowest();
public:
    void add(T x) {
        ++n_; sum_ += x;
        if (x < min_) min_ = x;
        if (x > max_) max_ = x;
    }
    long   count() const { return n_; }
    double mean()  const { return n_ ? sum_ / n_ : 0.0; }
    T      min()   const { return min_; }
    T      max()   const { return max_; }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v13 — generic stats ===\n";

    Stats<double> energy;                       // works for double...
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) energy.add(e);
    std::cout << std::format("energy : n={} mean={:.4f} range=[{:.1f},{:.1f}] GeV\n",
                             energy.count(), energy.mean(), energy.min(), energy.max());

    Stats<int> hits;                            // ...and for int, same code
    for (int h : {12, 8, 15, 10, 9}) hits.add(h);
    std::cout << std::format("hits   : n={} mean={:.2f} range=[{},{}]\n",
                             hits.count(), hits.mean(), hits.min(), hits.max());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v13 — generic stats ===
energy : n=5 mean=91.1000 range=[90.9,91.3] GeV
hits   : n=5 mean=10.80 range=[8,15]
```

**Commentary.**
- `Stats<T>` is written **once** but instantiated for `double` (energies) and `int` (hit counts) — the compiler generates a specialized version of each, both as fast as hand-written code. One accumulator, many element types: that's compile-time genericity.
- The accumulator uses `std::numeric_limits<T>::max()`/`lowest()` (Chapter 2) to seed min/max correctly for *any* numeric `T` — so the template adapts its neutral elements to the type. `sum_` is kept in `double` for accuracy (Chapter 3), even when `T` is `int`.
- Energies: mean 91.1, range [90.9, 91.3]; hits: mean 10.8, range [8, 15]. Adding a `Stats<float>` for a GPU dataset would need *no* new code.
- The STL's containers and algorithms (Chapters 18–19) are exactly this idea at scale — which is where we go next.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Template** | Code parameterized by a type (compile-time generics). |
| **Function / class template** | A generic function / generic type. |
| **Type parameter** | The placeholder (`T`) a template is generic over. |
| **Instantiation** | Generating concrete code for a specific type argument. |
| **CTAD** | Class Template Argument Deduction (omit `<T>`, C++17). |
| **Variadic template** | Takes any number of typed arguments (a parameter pack). |
| **Fold expression** | Expands a pack with an operator (`(args + ...)`). |
| **Specialization** | A type-specific version of a template. |

### What's next

Templates let types be generic — and let *your* types integrate with the language's syntax. **[Ch.17 — Operator Overloading](#chapter-17--operator-overloading)** shows how to give your numeric types (vectors, matrices) natural `+`, `*`, `[]`, and `<<` operators, so scientific code reads like the mathematics it implements.

[↑ back to top](#chapter-16--templates)


---

## Chapter 17 — Operator Overloading

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.9 — Classes](#chapter-9--classes--objects), [Ch.16 — Templates](#chapter-16--templates)

**Learning objectives** — after this chapter you will be able to:

- Give your types natural arithmetic operators (`+`, `-`, `*`).
- Overload comparison (including the C++20 spaceship), indexing `[]`, and stream output `<<`.
- Choose member vs non-member operators.
- Write numeric types (vectors, 4-momenta) that read like mathematics.

**In this chapter**

- [17.1 Why overload operators](#171-why-overload-operators)
- [17.2 Arithmetic operators](#172-arithmetic-operators)
- [17.3 Member vs non-member](#173-member-vs-non-member)
- [17.4 Comparison and the spaceship operator](#174-comparison-and-the-spaceship-operator)
- [17.5 Indexing and stream output](#175-indexing-and-stream-output)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-relativistic-4-vector) · Glossary · What's next

---

### 17.1 Why overload operators

Scientific code manipulates mathematical objects — vectors, matrices, complex numbers, 4-momenta. Writing `add(scale(a, 2.0), b)` for `2*a + b` is a readability disaster. **Operator overloading** lets your types use the built-in operators (`+`, `*`, `==`, `[]`, `<<`), so code reads like the mathematics it implements. This is why `std::complex`, Eigen matrices, and physics 4-vectors feel natural.

An operator is just a function with a special name (`operator+`, `operator[]`, …). You define it, and the compiler translates `a + b` into `a.operator+(b)` (or `operator+(a, b)`).

### 17.2 Arithmetic operators

Define arithmetic operators as member functions taking the right-hand operand. For a 3-vector:

```cpp
struct Vec3 {
    double x, y, z;
    Vec3 operator+(const Vec3& o) const { return {x+o.x, y+o.y, z+o.z}; }
    Vec3 operator-(const Vec3& o) const { return {x-o.x, y-o.y, z-o.z}; }
    Vec3 operator*(double s)      const { return {x*s, y*s, z*s}; }        // vector * scalar
    double dot(const Vec3& o) const { return x*o.x + y*o.y + z*o.z; }
    double norm() const { return std::sqrt(dot(*this)); }
};

Vec3 p{3, 0, 4}, q{0, 0, 1};
// p + q → (3, 0, 5)
// p * 2 → (6, 0, 8)     but 2 * p needs a non-member (§17.3)
// p.norm() → 5,  p.dot(q) → 4
```

Each returns a *new* `Vec3` (by value — cheap, and RVO applies, Chapter 6). Note the operators are **`const`** (they don't modify the operands) — const-correctness (Chapter 9) applied to operators.

> 💡 **Idiom** — Overload an operator **only when its meaning is obvious**. `+` on vectors, `*` for scalar multiplication, `==` for equality — all read naturally. But don't overload `+` to mean "append to a log" or `*` to mean "repeat" — a reader must be able to *guess* what an operator does from the types. Surprising operators are worse than named functions. (Also: provide the *compound* forms — `+=`, `*=` — for efficiency and symmetry when the type is used heavily.)

### 17.3 Member vs non-member

`p * 2` works as a member (`p.operator*(2)`), but `2 * p` does **not** — the left operand is a `double`, which has no `operator*(Vec3)`. For symmetry, define a **non-member** operator (a free function) for the scalar-on-the-left case:

```cpp
Vec3 operator*(double s, const Vec3& v) { return v * s; }   // non-member: enables 2 * p
// 2.0 * p → (6, 0, 8)
```

The rule: an operator whose **left operand is not your type** (like `2 * p`, or `os << v` for streams) *must* be a non-member. Binary arithmetic operators are often best as non-members anyway (for symmetric conversions), but member functions are fine and common. `[]`, `()`, `=`, and `->` *must* be members.

### 17.4 Comparison and the spaceship operator

Before C++20, giving a type all six comparisons (`== != < <= > >=`) meant writing six operators. C++20's **three-way comparison operator `<=>`** (the "spaceship") generates them from one definition — and you can `= default` it to compare member-by-member:

```cpp
struct Vec3 {
    double x, y, z;
    bool operator==(const Vec3&) const = default;   // defaulted equality (member-wise)
};
// p == p → true,  p == q → false
```

`= default` on `operator==` compares all members; adding `auto operator<=>(const Vec3&) const = default;` would generate the ordering operators too (though ordering a 3-vector isn't physically meaningful — use `<=>` for types with a natural order, like a `Version` or a `Money`).

> ⚙️ **Under the hood** — Defaulted `operator==` and `operator<=>` generate member-wise comparisons the compiler writes for you — correct and efficient, and they stay in sync when you add a member. `<=>` returns a *category* (`std::strong_ordering`, etc.) that encodes `<`, `==`, `>` in one call; the compiler synthesizes the individual relational operators from it. This eliminated a whole class of boilerplate (and the bugs of hand-written, inconsistent comparisons).

### 17.5 Indexing and stream output

**Indexing `[]`** lets your type be subscripted like an array — natural for a vector or matrix:

```cpp
struct Vec3 {
    double x, y, z;
    double operator[](int i) const { return i==0 ? x : (i==1 ? y : z); }
};
// p[0] → 3   (element access by index)
```

(A real type would provide a non-`const` `operator[]` returning a reference, so `v[0] = 5` works.) **Stream output `<<`** makes your type printable with `std::cout`. It *must* be a non-member (its left operand is the stream), taking `std::ostream&` and returning it (to allow chaining):

```cpp
#include <ostream>
std::ostream& operator<<(std::ostream& os, const Vec3& v) {
    return os << std::format("({:.1f}, {:.1f}, {:.1f})", v.x, v.y, v.z);
}
// std::cout << p  prints  (3.0, 0.0, 4.0)
```

> 💡 **Idiom** — Provide an `operator<<` for any type you'll print or log — it makes debugging and reporting natural (`std::cout << particle`). Format inside it with `std::format` (Chapter 1). Returning the stream (`return os;`) enables chaining (`os << a << b`). This is the standard way to make a type "printable," and it's what lets your scientific objects appear cleanly in output.

---

### Summary

- **Operator overloading** gives your types built-in operators so code reads like mathematics — essential for vectors, matrices, 4-momenta.
- **Arithmetic** operators (`operator+`, `*`, …) are usually `const` members returning a new value; overload only when the meaning is **obvious**.
- An operator whose **left operand isn't your type** (`2 * v`, `os << v`) must be a **non-member**; `[]`, `()`, `=`, `->` must be **members**.
- C++20's **`<=>`** (spaceship) and defaulted **`operator==`** generate comparisons member-wise from one line.
- **`operator[]`** provides indexing; **`operator<<`** (non-member, `std::ostream&`) makes a type printable — provide it for anything you'll log.

### Self-check quiz

1. Why must `operator<<` for stream output be a non-member?
   <details><summary>Answer</summary>Its left operand is the `std::ostream`, not your type, so it can't be a member of your class. It's a free function taking `(std::ostream&, const T&)`.</details>
2. Why does `2 * v` need a non-member operator when `v * 2` works as a member?
   <details><summary>Answer</summary>`v * 2` is `v.operator*(2)`, but `2 * v` would need `double::operator*(Vec3)`, which doesn't exist. A non-member `operator*(double, Vec3)` handles scalar-on-the-left.</details>
3. What does `bool operator==(const T&) const = default;` do?
   <details><summary>Answer</summary>Generates a member-wise equality comparison automatically (C++20), comparing all members — correct and kept in sync as members change.</details>
4. When should you *not* overload an operator?
   <details><summary>Answer</summary>When its meaning isn't obvious for your type — a reader must be able to guess what `+`/`*` do. Surprising operators are worse than named functions.</details>

### Exercises

**Exercise 17.1 — Complex number (guided).** Write a `Complex` with `+`, `*`, and `operator<<`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <ostream>
struct Complex {
    double re, im;
    Complex operator+(const Complex& o) const { return {re+o.re, im+o.im}; }
    Complex operator*(const Complex& o) const {
        return {re*o.re - im*o.im, re*o.im + im*o.re};   // (a+bi)(c+di)
    }
};
std::ostream& operator<<(std::ostream& os, const Complex& c) {
    return os << std::format("{:.1f}{:+.1f}i", c.re, c.im);
}
int main() {
    Complex a{1, 2}, b{3, -1};
    std::cout << "a+b = " << (a + b) << "\n";   // 4.0+1.0i
    std::cout << "a*b = " << (a * b) << "\n";   // 5.0+5.0i
}
```

Output:
```text
a+b = 4.0+1.0i
a*b = 5.0+5.0i
```

**Why this works:** `+` adds components; `*` applies the complex-multiplication rule `(1+2i)(3−i) = 3−i+6i−2i² = 5+5i`. `operator<<` formats with an explicit sign (`{:+.1f}`) so the imaginary part reads correctly. (The standard `std::complex` exists — this shows the mechanism.)

</details>

**Exercise 17.2 — Money with `<=>`.** Give a `Money` (integer cents) the spaceship operator so it's fully comparable and sortable.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <compare>
struct Money {
    long cents;
    auto operator<=>(const Money&) const = default;   // all comparisons, from one line
    bool operator==(const Money&) const = default;
};
int main() {
    Money a{1050}, b{995};
    std::cout << std::format("a>b: {}, a==b: {}, a<b: {}\n", (a > b), (a == b), (a < b));
}
```

Output:
```text
a>b: true, a==b: false, a<b: false
```

**Why this works:** `= default` on `<=>` generates `<`, `>`, `<=`, `>=` (comparing `cents`), and defaulted `==` gives equality. `Money{1050}` (\$10.50) > `Money{995}` (\$9.95), so `a>b` is true and `a<b` is false. One line yields all comparisons — and makes `Money` sortable with `std::sort` (Chapter 19).

</details>

**Exercise 17.3 — Indexed 2-vector.** Give a `Vec2` a *mutable* `operator[]` (returning a reference) so `v[0] = 5` works.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
struct Vec2 {
    double data[2];
    double&       operator[](int i)       { return data[i]; }   // mutable
    const double& operator[](int i) const { return data[i]; }   // const
};
int main() {
    Vec2 v{{1.0, 2.0}};
    v[0] = 9.0;                       // uses the mutable overload
    std::cout << std::format("{} {}\n", v[0], v[1]);   // 9 2
}
```

Output:
```text
9 2
```

**Why this works:** the non-`const` `operator[]` returns a `double&` (a reference into the array), so `v[0] = 9.0` assigns through it. The `const` overload returns `const double&` for read-only access on `const` objects. Providing both is the standard indexing pattern (as `std::vector` does).

</details>

### Chapter project: a relativistic 4-vector

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–17. The 4-momentum (energy + 3-momentum) is *the* object of particle physics. We give it `+` (to combine particles) and an invariant `mass()`, so analysis code reads like the physics.

**Goal.** A `LorentzVector` with `operator+` and `mass()`, used to reconstruct the invariant mass of two muons.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <ostream>

struct LorentzVector {
    double E, px, py, pz;
    LorentzVector operator+(const LorentzVector& o) const {
        return {E+o.E, px+o.px, py+o.py, pz+o.pz};
    }
    double mass() const {
        double m2 = E*E - (px*px + py*py + pz*pz);   // E^2 = p^2 + m^2
        return m2 > 0 ? std::sqrt(m2) : 0.0;
    }
};
std::ostream& operator<<(std::ostream& os, const LorentzVector& v) {
    return os << std::format("(E={:.2f}, p=({:.0f},{:.0f},{:.0f}))", v.E, v.px, v.py, v.pz);
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v14 — 4-vectors ===\n";
    // Two (nearly massless) muons emitted back-to-back, as from a Z at rest
    double p = std::sqrt(30.0*30.0 + 20.0*20.0 + 28.0*28.0);   // |momentum| ~= energy
    LorentzVector mu1{p, 30.0, 20.0, 28.0};
    LorentzVector mu2{p, -30.0, -20.0, -28.0};
    LorentzVector Z = mu1 + mu2;                                // operator+ adds 4-momenta

    std::cout << "mu1 = " << mu1 << "\n";
    std::cout << "Z   = " << Z << "\n";
    std::cout << std::format("reconstructed invariant mass = {:.2f} GeV\n", Z.mass());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v14 — 4-vectors ===
mu1 = (E=45.65, p=(30,20,28))
Z   = (E=91.30, p=(0,0,0))
reconstructed invariant mass = 91.30 GeV
```

**Commentary.**
- `LorentzVector` overloads **`+`** to add 4-momenta component-wise, and provides the physically meaningful **`mass()`** (`√(E² − |p|²)`). Now `mu1 + mu2` reads exactly like the physics: summing two particles' 4-momenta.
- The two muons are emitted **back-to-back** (opposite 3-momenta), each with energy ≈ its momentum magnitude (nearly massless). Their sum has zero net momentum and energy 91.30 GeV, so its invariant mass is **91.30 GeV** — a reconstructed **Z boson**, the classic dimuon analysis at the LHC.
- **`operator<<`** makes a `LorentzVector` printable (`std::cout << Z`) — reporting and debugging read naturally. This is exactly how ROOT's `TLorentzVector` works, and why operator overloading is indispensable in physics code.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Operator overloading** | Defining built-in operators for your types. |
| **`operator+`, `operator*`** | Overloaded arithmetic (usually `const` members). |
| **Member vs non-member** | `[]`/`()`/`=`/`->` must be members; left-operand-not-yours must be non-member. |
| **`<=>` (spaceship)** | Three-way comparison generating all relational operators (C++20). |
| **Defaulted `operator==`** | Compiler-generated member-wise equality. |
| **`operator[]`** | Indexing; provide `const` and mutable overloads. |
| **`operator<<`** | Non-member stream output making a type printable. |

### What's next

Your types integrate with the language's syntax. Now the standard library's data structures: **[Ch.18 — STL Containers](#chapter-18--stl-containers)** covers `std::vector`, `std::array`, `std::span`, `std::map`, and `std::set` — the workhorses for holding and organizing scientific data, and the foundation for the algorithms in Chapter 19.

[↑ back to top](#chapter-17--operator-overloading)


---

## Chapter 18 — STL Containers

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.12 — Rule of Zero](#chapter-12--the-rule-of-three--five--zero), [Ch.16 — Templates](#chapter-16--templates)

**Learning objectives** — after this chapter you will be able to:

- Use `std::vector` — the default container — fluently.
- Choose between `vector`, `array`, `map`, `unordered_map`, and `set`.
- Use `std::span` for non-owning views and understand multidimensional data.

**In this chapter**

- [18.1 `std::vector`: the default container](#181-stdvector-the-default-container)
- [18.2 `std::array`: fixed size on the stack](#182-stdarray-fixed-size-on-the-stack)
- [18.3 `std::span`: non-owning views](#183-stdspan-non-owning-views)
- [18.4 Associative containers: `map` and `set`](#184-associative-containers-map-and-set)
- [18.5 Multidimensional data](#185-multidimensional-data)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-span-based-dataset) · Glossary · What's next

---

### 18.1 `std::vector`: the default container

**`std::vector<T>`** is a dynamic array — a contiguous, growable sequence — and your **default** container for a collection of values. It owns its memory (Rule of Zero, Chapter 12: copy/move/cleanup all correct), grows as you add elements, and stores them contiguously (cache-friendly, ideal for numerics):

```cpp
std::vector<double> v = {1.0, 2.0, 3.0};
v.push_back(4.0);                    // append (grows if needed)
// v.size() → 4,  v.back() → 4,  v[0] → 1.0
double s = 0; for (double x : v) s += x;   // sum → 10
```

Key operations: `push_back` (append), `size`, `[i]` (unchecked access) and `at(i)` (bounds-checked, throws), `front`/`back`, `clear`, `resize`, `begin`/`end` (for algorithms, Chapter 19). Reserve capacity up front with **`reserve(n)`** when you know the size — it avoids repeated reallocations as the vector grows.

> 💡 **Idiom** — **Default to `std::vector`.** For contiguous numerical data it's cache-optimal, works with every algorithm, and is Rule-of-Zero safe. When you know the final size, call **`reserve(n)`** before a loop of `push_back`s — otherwise the vector reallocates (and copies/moves everything) several times as it grows, which is wasted work in a hot data-loading loop. Use `[i]` in code you've verified is in-bounds, and `at(i)` where a bad index should throw rather than corrupt.

> ⚙️ **Under the hood** — A common `vector` implementation stores three pointer-like values: begin, logical end, and capacity end; the standard specifies behaviour, not that representation. When `push_back` exceeds capacity, it allocates a larger buffer, moves or copies the elements, and releases the old one. The growth factor is implementation-defined. This gives amortized O(1) append, but each reallocation is O(n) and invalidates pointers, references, and iterators. Contiguous storage makes `v.data()` suitable for C and BLAS/LAPACK APIs; unlike `&v[0]`, `data()` is also the correct expression when the vector is empty.

### 18.2 `std::array`: fixed size on the stack

**`std::array<T, N>`** is a fixed-size array whose size `N` is a compile-time constant. Its elements live *inside the array object*: a local array normally has automatic storage, a member lives inside its owner, and a dynamically allocated owner places it in dynamic storage. The container itself performs no allocation. Use it when the size is known and usually small:

```cpp
std::array<int, 3> a = {10, 20, 30};
// a[0] → 10,  a.size() → 3
```

It has the same interface as `vector` (`[]`, `size`, `begin`/`end`, range-based `for`) but can't grow. It's a safe, zero-overhead replacement for C arrays — it *knows its size* (no decay, Chapter 10) and copies properly.

> 💡 **Idiom** — Use **`std::array<T, N>`** for fixed-size value-semantic data (a 3-vector's components, a 4×4 matrix, a lookup table). Use **`std::vector`** when the size is dynamic or very large. A built-in array still appears at C interfaces and in low-level layout-sensitive code, but `std::array` is usually the safer application-level default because it retains its size and supports value semantics.

### 18.3 `std::span`: non-owning views

**`std::span<T>`** (C++20) is a *non-owning view* of a contiguous sequence — a pointer + length, with the safe container interface. It lets a function accept "any contiguous range of `T`" — a `vector`, an `array`, or a C array — *without copying and without templating*:

```cpp
double sum_span(std::span<const double> s) {   // accepts vector, array, C array...
    double t = 0; for (double x : s) t += x; return t;
}
std::vector<double> v = {1, 2, 3, 4};
sum_span(v);              // pass the vector → 10 (no copy)
```

`std::span<const double>` is the modern replacement for the old "`const double* data, std::size_t n`" pair (Chapter 6) — it carries the length safely, prevents decay bugs, and works with any contiguous container.

> 💡 **Idiom** — Take a **`std::span<const T>`** parameter for a function that *reads* a contiguous range but doesn't own it — it's the safe, non-owning, non-copying way to accept "a view of some data." Use `std::span<T>` (non-const) to modify in place. This replaces both raw pointer+length pairs *and* unnecessary `const std::vector<T>&` parameters (which force the caller to have a `vector`, not an `array`). A `span` is cheap (two words) and general.

### 18.4 Associative containers: `map` and `set`

For key-based lookup and uniqueness, the standard library offers:

- **`std::map<K, V>`** — an *ordered* key→value dictionary (keys sorted; O(log n) operations, tree-based).
- **`std::unordered_map<K, V>`** — a *hash* map (average O(1), unordered) — prefer it when you don't need ordering and want speed.
- **`std::set<T>`** — a sorted collection of *unique* values.

```cpp
std::map<std::string, int> counts;
counts["muon"] = 3; counts["electron"] = 5; counts["muon"]++;
// counts["muon"] → 4,  counts["electron"] → 5

std::set<int> s = {3, 1, 2, 1};    // duplicates dropped, sorted
// iterating s → 1 2 3
// s.contains(2) → true   (C++20)
```

`map`/`unordered_map` are perfect for histograms-by-category (counts per particle type), lookups by ID, and caches; `set` for tracking a unique collection (which detector channels fired).

> 💡 **Idiom** — Choose from measured requirements. `unordered_map` offers average O(1) lookup but pays for hashing, buckets, rehashing, and weak locality; `map` offers ordered iteration, stable iterators, range queries, and guaranteed O(log n). For small collections, a sorted `vector` can beat both. Select by ordering, invalidation rules, worst-case guarantees, memory budget, and benchmarks—not Big-O alone.

### 18.5 Multidimensional data

Scientific data is often multidimensional — a matrix, a 3-D field, a detector grid. The simplest representation is a **`std::vector` with manual indexing** (row-major): a 2-D `r×c` grid is a `vector<double>` of size `r*c`, indexed `data[row * c + col]`:

```cpp
std::size_t rows = 3, cols = 4;
std::vector<double> grid(rows * cols, 0.0);
grid[1 * cols + 2] = 5.0;          // element (row 1, col 2)
```

C++23 adds **`std::mdspan`** — a non-owning *multidimensional view* over such flat storage, so you write `grid(1, 2)` instead of manual index arithmetic. (Not all compilers ship it yet — GCC 13 doesn't — so flat `vector` + `row*cols+col` remains the portable idiom, and small libraries provide an `mdspan` wrapper.)

> 💡 **Idiom** — Store multidimensional numerical data as a **flat `std::vector` in row-major order** with `index = row*cols + col` (or the mdspan/library equivalent). This keeps the data **contiguous** — essential for cache performance (Chapter 33) and for passing to BLAS/LAPACK, which expect flat column- or row-major buffers. A `vector<vector<double>>` ("array of arrays") is *not* contiguous (each row is a separate heap allocation) and is markedly slower for numerics — avoid it for matrices.

---

### Summary

- **`std::vector<T>`** — the **default**: dynamic, contiguous, Rule-of-Zero-safe. `push_back`, `size`, `[i]`/`at(i)`; **`reserve(n)`** to avoid reallocations. Contiguous → cache-friendly and BLAS-compatible.
- **`std::array<T, N>`** — fixed compile-time size with inline element storage; usually the value-semantic replacement for a built-in array.
- **`std::span<const T>`** — a non-owning view (pointer+length) accepting any contiguous range; replaces raw pointer+length pairs.
- **`std::map`/`unordered_map`** (key→value, ordered/hashed) and **`std::set`** (unique, sorted) for keyed access; prefer **`unordered_map`** unless you need ordering.
- Store **multidimensional** data as a **flat contiguous `vector`** (`row*cols+col`), not a vector-of-vectors; C++23 `mdspan` gives a nicer view.

### Self-check quiz

1. Why is `std::vector` the default container for numerical data?
   <details><summary>Answer</summary>It's contiguous (cache-friendly, BLAS-compatible), dynamically sized, and Rule-of-Zero-safe (correct copy/move/cleanup). Its append is amortized O(1).</details>
2. When should you call `reserve`?
   <details><summary>Answer</summary>Before a loop of `push_back`s when you know (or can estimate) the final size — it pre-allocates so the vector doesn't reallocate and move elements repeatedly as it grows.</details>
3. What does `std::span` give you over `const std::vector<T>&`?
   <details><summary>Answer</summary>It's a non-owning view that accepts *any* contiguous range (vector, array, C array, sub-range), not just a `vector`, without copying or templating — a safer replacement for pointer+length pairs.</details>
4. Why store a matrix as a flat `vector`, not a vector-of-vectors?
   <details><summary>Answer</summary>A flat `vector` is contiguous (cache-friendly, passable to BLAS); a vector-of-vectors scatters rows across separate heap allocations, hurting performance.</details>

### Exercises

**Exercise 18.1 — Vector basics (guided).** Fill a `vector<double>` with the squares of 1..5 (using `reserve`), and print the size and sum.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
int main() {
    std::vector<double> squares;
    squares.reserve(5);                       // pre-allocate
    for (int i = 1; i <= 5; ++i) squares.push_back(i * i);
    double sum = 0; for (double x : squares) sum += x;
    std::cout << std::format("size={} sum={}\n", squares.size(), sum);   // size=5 sum=55
}
```

Output:
```text
size=5 sum=55
```

**Why this works:** `reserve(5)` pre-allocates capacity so the five `push_back`s don't reallocate. The squares 1+4+9+16+25 sum to 55. This is the standard "build a dataset" pattern.

</details>

**Exercise 18.2 — Count by category (map).** Given a list of particle-type strings, count occurrences of each with a `map`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <map>
#include <string>
#include <vector>
int main() {
    std::vector<std::string> events = {"muon","electron","muon","muon","electron","jet"};
    std::map<std::string,int> counts;
    for (const auto& e : events) counts[e]++;      // ++ on a missing key starts at 0
    for (const auto& [type, n] : counts)           // structured binding over map entries
        std::cout << std::format("{:10}: {}\n", type, n);
}
```

Output:
```text
electron  : 2
jet       : 1
muon      : 3
```

**Why this works:** `counts[e]++` inserts `e` with value 0 if absent, then increments — the idiomatic histogram-by-category. Iterating a `std::map` yields entries in *sorted key order* (electron, jet, muon), unpacked with a structured binding `[type, n]`.

</details>

**Exercise 18.3 — Generic sum via span.** Write `double total(std::span<const double>)` and call it with both a `vector` and a `std::array`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <array>
#include <span>
double total(std::span<const double> s) { double t = 0; for (double x : s) t += x; return t; }
int main() {
    std::vector<double> v = {1.0, 2.0, 3.0};
    std::array<double, 2> a = {10.0, 20.0};
    std::cout << std::format("v={} a={}\n", total(v), total(a));   // v=6 a=30
}
```

Output:
```text
v=6 a=30
```

**Why this works:** `total` takes a `std::span<const double>` — a non-owning view — so *both* a `vector` and an `array` convert to it implicitly, with no copy and no template. One function, any contiguous source: `1+2+3=6`, `10+20=30`.

</details>

### Chapter project: a span-based dataset

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–18. We back the toolkit's `Dataset` with a `std::vector` and expose its data as a `std::span` — so analysis functions read the data with zero copies and no ownership entanglement.

**Goal.** A `Dataset` storing energies in a `vector`, offering a `std::span<const double>` view, and a free `mean` over any span.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <span>

double mean(std::span<const double> s) {
    if (s.empty()) return 0.0;
    double t = 0; for (double x : s) t += x; return t / s.size();
}

class Dataset {
    std::vector<double> energies_;
public:
    void reserve(std::size_t n) { energies_.reserve(n); }
    void add(double e) { energies_.push_back(e); }
    std::span<const double> view() const { return energies_; }   // non-owning window
    std::size_t size() const { return energies_.size(); }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v15 — vector-backed dataset ===\n";
    Dataset d;
    d.reserve(5);
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) d.add(e);
    std::cout << std::format("n={} mean={:.4f} GeV (via span)\n", d.size(), mean(d.view()));
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v15 — vector-backed dataset ===
n=5 mean=91.1000 GeV (via span)
```

**Commentary.**
- `Dataset` now owns a `std::vector<double>` (Rule of Zero — copyable, movable, leak-free, Chapters 12–13) and pre-allocates with `reserve`. It's the real, safe replacement for Chapter 11's hand-managed `EnergyBuffer`.
- `view()` returns a **`std::span<const double>`** — a non-owning window into the data. The free `mean` takes a `span`, so it works on the dataset (or any contiguous range) **without copying** and without knowing about `Dataset`. Ownership stays with the `Dataset`; analysis code just *views*.
- This is the modern pattern: **`vector` owns, `span` views**. It cleanly separates data ownership from data processing — analysis functions accept `span`s, containers own `vector`s. Chapter 19's algorithms operate on exactly these ranges.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`std::vector<T>`** | The default dynamic, contiguous, owning array. |
| **`reserve`** | Pre-allocate capacity to avoid reallocations. |
| **`std::array<T, N>`** | Fixed compile-time-size array whose elements live inside the array object. |
| **`std::span<T>`** | A non-owning view (pointer+length) of a contiguous range. |
| **`std::map` / `unordered_map`** | Ordered / hashed key→value dictionary. |
| **`std::set`** | A sorted collection of unique values. |
| **Row-major flat storage** | A matrix as a contiguous `vector` (`row*cols+col`). |
| **`std::mdspan`** | A multidimensional view over flat storage (C++23). |

### What's next

You can store and view data. **[Ch.19 — Iterators, Algorithms & `<numeric>`](#chapter-19--iterators-algorithms--numeric)** brings the STL algorithms — `accumulate`, `reduce`, `transform`, `sort`, `find` — that process these containers concisely and efficiently, replacing hand-written loops with named, optimized operations.

[↑ back to top](#chapter-18--stl-containers)


---

## Chapter 19 — Iterators, Algorithms & `<numeric>`

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.7 — Lambdas](#chapter-7--functions-ii-lambdas--function-objects), [Ch.18 — Containers](#chapter-18--stl-containers)

**Learning objectives** — after this chapter you will be able to:

- Understand iterators as the glue between containers and algorithms.
- Use `<algorithm>` (`sort`, `find`, `count_if`, `transform`, `max_element`).
- Use `<numeric>` (`accumulate`, `reduce`, `transform_reduce`) for statistics.
- Compose data pipelines with C++20 ranges.

**In this chapter**

- [19.1 Iterators](#191-iterators)
- [19.2 `<numeric>`: accumulate, reduce, transform_reduce](#192-numeric-accumulate-reduce-transform_reduce)
- [19.3 `<algorithm>`: sort, find, count, transform](#193-algorithm-sort-find-count-transform)
- [19.4 Ranges: composable pipelines](#194-ranges-composable-pipelines)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-statistics-by-algorithm) · Glossary · What's next

---

### 19.1 Iterators

An **iterator** is a generalization of a pointer — an object that points at an element and can advance (`++`), dereference (`*`), and compare. Every container provides `begin()` (first element) and `end()` (*one past* the last), and the STL **algorithms** operate on this `[begin, end)` range. This is the STL's central design: containers and algorithms are decoupled, connected only by iterators, so *any* algorithm works with *any* container.

```cpp
std::vector<double> v = {91.1, 91.3, 90.9};
for (auto it = v.begin(); it != v.end(); ++it)   // manual iteration (range-based for hides this)
    std::cout << *it << " ";
```

You rarely write iterator loops by hand (the range-based `for` and algorithms do it for you), but understanding `begin()`/`end()` explains every algorithm's signature. Iterators come in *categories* (forward, bidirectional, random-access) describing what they support; a `vector`'s are random-access (fast `+n`), a `list`'s only bidirectional.

### 19.2 `<numeric>`: accumulate, reduce, transform_reduce

`<numeric>` provides the reductions at the heart of data analysis:

```cpp
#include <numeric>
std::vector<double> v = {91.1, 91.3, 90.9, 91.2, 91.0};

double sum  = std::accumulate(v.begin(), v.end(), 0.0);   // sequential sum → 455.5
double sum2 = std::reduce(v.begin(), v.end());            // C++17: may parallelize → 455.5

// transform_reduce: transform each element, then reduce — e.g. sum of squares
double sumsq = std::transform_reduce(v.begin(), v.end(), 0.0,
                                     std::plus{},                 // reduce with +
                                     [](double x){ return x*x; }); // transform: square
// sumsq → 41496.15
```

- **`accumulate(first, last, init)`** sums (or folds with a custom operation) *sequentially*, left to right. The `init` value sets the type — pass `0.0` (double), not `0` (int), or you'll get integer accumulation!
- **`reduce`** (C++17) is like `accumulate` but may run *out of order* or in *parallel* (Chapter 34) — so its operation must be associative; for plain `+` on doubles, results can differ in the last bits.
- **`transform_reduce`** fuses a per-element transform with a reduction — the one-pass idiom for sum-of-squares, dot products, weighted sums. **`inner_product`** is the classic dot product.

> ⚠️ **Gotcha — the `init` type.** `std::accumulate(v.begin(), v.end(), 0)` with an *integer* `0` accumulates in `int`, truncating a vector of doubles to integer arithmetic — a silent, catastrophic bug in numerical code. **Always pass a `0.0` (double) init** for floating-point data. (And for a very large or ill-conditioned sum, recall Chapter 3: naive summation drifts — use compensated summation or split the work.)

### 19.3 `<algorithm>`: sort, find, count, transform

`<algorithm>` provides dozens of operations that replace hand-written loops with named, tested, optimized calls:

```cpp
#include <algorithm>
std::vector<double> v = {91.1, 91.3, 90.9, 91.2, 91.0};

int above = std::count_if(v.begin(), v.end(), [](double x){ return x > 91.0; });   // → 3
auto mx   = std::max_element(v.begin(), v.end());   // iterator to the max → *mx = 91.3
std::sort(v.begin(), v.end());                       // in-place ascending → 90.9 91 91.1 91.2 91.3
// sorted: 90.9 91 91.1 91.2 91.3
```

The staples: **`sort`** (with an optional comparator lambda, Chapter 7), **`find`/`find_if`**, **`count`/`count_if`**, **`max_element`/`min_element`**, **`transform`** (map a function over a range), **`for_each`**, **`copy`**, **`all_of`/`any_of`/`none_of`**. Each takes a `[begin, end)` range and, often, a lambda — expressing intent (*"count the elements above threshold"*) far more clearly than a raw loop.

> 💡 **Idiom** — **Prefer a named algorithm over a hand-written loop.** `std::count_if(v, pred)` says *what* you're doing; a `for` loop with an `if` and a counter makes the reader reverse-engineer it. Named algorithms are also less bug-prone (no off-by-one), and some (`sort`, `reduce`) are highly optimized or parallelizable. "No raw loops" is a well-known guideline: reach for `<algorithm>`/`<numeric>` first, write a loop only when no algorithm fits.

### 19.4 Ranges: composable pipelines

C++20 **ranges** let you compose operations into a readable *pipeline* with the `|` operator, and act on whole containers (no `begin()`/`end()`). **Views** (`std::views::filter`, `transform`, `take`, …) are *lazy* — they don't compute until iterated, and don't allocate intermediates:

```cpp
#include <ranges>
std::vector<double> v = {90.9, 91.0, 91.1, 91.2, 91.3};   // (sorted)

auto high = v | std::views::filter([](double x){ return x > 91.0; })   // keep > 91
              | std::views::transform([](double x){ return x * 1000.0; }); // GeV → MeV

for (double x : high) std::cout << x << " ";   // 91100 91200 91300
```

The pipeline reads top-to-bottom as a data flow: *filter, then transform*. Because views are lazy, `high` computes each element on demand as you iterate — no temporary vector is built. This is the modern, expressive style for data transformations (analogous to Python generators or SQL).

> 💡 **Idiom** — Use **ranges/views** for readable, allocation-free data pipelines: `data | filter | transform | take`. They compose cleanly and are lazy, so chaining is cheap. For a one-off operation a single algorithm is fine; for a multi-step transformation of a dataset (select events, compute a quantity, take the first N), a ranges pipeline is clearest. (C++23 adds `ranges::to` to collect a view back into a container, and more views.)

---

### Summary

- **Iterators** (`begin()`/`end()`, the `[first, last)` range) decouple containers from algorithms — any algorithm works with any container.
- **`<numeric>`**: **`accumulate`** (sequential fold), **`reduce`** (possibly parallel/reordered), **`transform_reduce`** (fused map+reduce, e.g. sum of squares), `inner_product`. **Pass a `0.0` init** for doubles!
- **`<algorithm>`**: **`sort`**, `find`/`find_if`, `count`/`count_if`, `max_element`/`min_element`, `transform`, `for_each`, `all_of`/`any_of` — named, tested replacements for hand loops.
- **Ranges** (C++20) compose lazy **views** (`filter`, `transform`, `take`) into `|` pipelines over whole containers — readable and allocation-free.
- Guideline: **prefer named algorithms/ranges over raw loops**.

### Self-check quiz

1. What do `begin()` and `end()` represent, and why is `end()` "one past the last"?
   <details><summary>Answer</summary>`begin()` points at the first element, `end()` at one *past* the last, so `[begin, end)` is a half-open range — iteration stops when the iterator equals `end()`, and an empty range has `begin() == end()`.</details>
2. Why must you pass `0.0` (not `0`) to `accumulate` for a vector of doubles?
   <details><summary>Answer</summary>The init value's type sets the accumulation type; `0` (int) accumulates in integer arithmetic, truncating the doubles — a silent numerical bug. `0.0` accumulates in double.</details>
3. What does `transform_reduce` do that `accumulate` alone doesn't?
   <details><summary>Answer</summary>It applies a per-element transform (e.g. squaring) *and* a reduction in one pass — ideal for sums of squares, dot products, weighted sums.</details>
4. What makes ranges views efficient?
   <details><summary>Answer</summary>They're lazy — each element is computed on demand as you iterate, so a `filter | transform` pipeline builds no intermediate containers.</details>

### Exercises

**Exercise 19.1 — Sum of squares (guided).** Compute the sum of squares of a vector two ways: a raw loop and `transform_reduce`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <numeric>
int main() {
    std::vector<double> v = {1.0, 2.0, 3.0, 4.0};
    double loop = 0.0; for (double x : v) loop += x * x;
    double alg  = std::transform_reduce(v.begin(), v.end(), 0.0, std::plus{},
                                        [](double x){ return x*x; });
    std::cout << std::format("loop={} alg={}\n", loop, alg);   // both 30
}
```

Output:
```text
loop=30 alg=30
```

**Why this works:** both compute `1+4+9+16 = 30`. `transform_reduce` fuses the square (transform) and sum (reduce) into one expression — clearer and parallelizable — while the loop spells it out. The `0.0` init keeps it in `double`.

</details>

**Exercise 19.2 — Sort and find (algorithms).** Sort a vector descending, then find the first element below 91.0.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <algorithm>
int main() {
    std::vector<double> v = {91.1, 90.9, 91.3, 90.8, 91.0};
    std::sort(v.begin(), v.end(), [](double a, double b){ return a > b; });   // descending
    auto it = std::find_if(v.begin(), v.end(), [](double x){ return x < 91.0; });
    std::cout << std::format("first below 91.0: {} (index {})\n", *it, it - v.begin());
}
```

Output:
```text
first below 91.0: 90.9 (index 3)
```

**Why this works:** `sort` with a `a > b` comparator orders descending (91.3, 91.1, 91.0, 90.9, 90.8); `find_if` returns an iterator to the first element satisfying the predicate (`< 91.0` → 90.9 at index 3). `it - v.begin()` converts the iterator to an index (random-access iterators support subtraction).

</details>

**Exercise 19.3 — Ranges pipeline.** From a vector of energies, take those above 91.0, convert to MeV, and collect the count.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <ranges>
#include <algorithm>
int main() {
    std::vector<double> v = {91.1, 90.9, 91.3, 90.8, 91.0, 91.2};
    auto pipeline = v | std::views::filter([](double x){ return x > 91.0; })
                      | std::views::transform([](double x){ return x * 1000.0; });
    for (double x : pipeline) std::cout << std::format("{:.0f} ", x);
    std::cout << std::format("\ncount = {}\n", std::ranges::distance(pipeline));
}
```

Output:
```text
91100 91300 91200
count = 3
```

**Why this works:** the pipeline lazily keeps energies > 91.0 (91.1, 91.3, 91.2) and scales them to MeV. `std::ranges::distance` counts the elements the view yields (3). No intermediate vector is created — the view computes on demand.

</details>

### Chapter project: statistics by algorithm

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–19. We replace the toolkit's hand-written statistics loops (Chapters 5–6) with STL algorithms — concise, tested, and parallelizable.

**Goal.** Compute mean, standard deviation, and max of a dataset using `<numeric>`/`<algorithm>` instead of manual loops.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <numeric>
#include <algorithm>
#include <cmath>

int main() {
    std::vector<double> energies = {91.1, 91.3, 90.9, 91.2, 91.0, 90.8, 91.4};
    const std::size_t n = energies.size();

    // Mean via accumulate (0.0 init keeps it double!)
    const double mean = std::accumulate(energies.begin(), energies.end(), 0.0) / n;

    // Variance via transform_reduce: sum of (x - mean)^2, in one pass
    const double var = std::transform_reduce(
        energies.begin(), energies.end(), 0.0, std::plus{},
        [mean](double x){ return (x - mean) * (x - mean); }) / n;
    const double stddev = std::sqrt(var);

    // Max via max_element
    const double emax = *std::max_element(energies.begin(), energies.end());

    std::cout << "=== Monte Carlo Analysis Toolkit v16 — stats by algorithm ===\n";
    std::cout << std::format("N       : {}\n", n);
    std::cout << std::format("Mean    : {:.4f} GeV\n", mean);
    std::cout << std::format("Std dev : {:.4f} GeV\n", stddev);
    std::cout << std::format("Max     : {:.1f} GeV\n", emax);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v16 — stats by algorithm ===
N       : 7
Mean    : 91.1000 GeV
Std dev : 0.2000 GeV
Max     : 91.4 GeV
```

**Commentary.**
- The Chapter 5 statistics — three hand-written loops — become three algorithm calls: `accumulate` for the mean, `transform_reduce` for the variance (fusing "subtract mean, square, sum" into one pass), and `max_element` for the maximum. Each *names* its intent and is individually tested and optimizable.
- The `0.0` init on `accumulate` is essential — an integer `0` would truncate (§19.2). The variance lambda captures `mean` by value and computes squared deviations, reduced with `std::plus{}`.
- Same results as the hand-written version (mean 91.1, σ 0.2, max 91.4) — but shorter, clearer, and ready to parallelize (swap `reduce`/`transform_reduce` to `std::execution::par`, Chapter 34). This is idiomatic modern C++ data analysis: **express the computation, don't hand-code the loop**.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Iterator** | A pointer-like object over a range; `begin()`/`end()`. |
| **`accumulate` / `reduce`** | Sequential fold / possibly-parallel reduction. |
| **`transform_reduce`** | Fused per-element transform + reduction. |
| **`inner_product`** | Dot product of two ranges. |
| **`sort` / `find_if` / `count_if`** | Ordering / search / conditional count. |
| **`max_element`** | Iterator to the largest element. |
| **Ranges / views** | Lazy, composable pipelines (`filter`, `transform`, `|`). |
| **`std::ranges::distance`** | Counts the elements a range yields. |

### What's next

You can process data expressively. But a template accepts *any* type — even ones that don't make sense, giving cryptic errors. **[Ch.20 — Concepts & Constraints](#chapter-20--concepts--constraints)** shows how to constrain templates (e.g. "this works for any *numeric* type"), producing clear errors and self-documenting generic code.

[↑ back to top](#chapter-19--iterators-algorithms--numeric)


---

## Chapter 20 — Concepts & Constraints

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.16 — Templates](#chapter-16--templates)

**Learning objectives** — after this chapter you will be able to:

- Constrain template parameters with concepts.
- Use standard concepts (`std::integral`, `std::floating_point`).
- Define your own concepts and use `requires` clauses.
- Get clear errors and self-documenting generic code.

**In this chapter**

- [20.1 The unconstrained-template problem](#201-the-unconstrained-template-problem)
- [20.2 Constraining with concepts](#202-constraining-with-concepts)
- [20.3 Standard and custom concepts](#203-standard-and-custom-concepts)
- [20.4 `requires` clauses](#204-requires-clauses)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-constrained-numeric-accumulator) · Glossary · What's next

---

### 20.1 The unconstrained-template problem

A template (Chapter 16) accepts *any* type — including ones that don't make sense. Call a `mean` template on a `std::vector<std::string>` and you get a wall of cryptic errors from *deep inside* the template (about `operator+` on strings), pointing at the library, not your mistake. Pre-C++20 templates were "duck-typed": they compiled if the operations happened to work, and exploded confusingly if not.

**Concepts** (C++20) fix this: they let you state *requirements* on template parameters — "this works for any *floating-point* type" — so misuse is rejected *at the call site* with a clear message ("constraint not satisfied"), and the constraint *documents* what the template needs.

### 20.2 Constraining with concepts

The concise syntax replaces `typename T` with a *concept name* — the type must satisfy it:

```cpp
#include <concepts>
template<std::floating_point T>          // T must be a floating-point type
T mean(const std::vector<T>& v) {
    T s{}; for (const T& x : v) s += x;
    return v.empty() ? T{} : s / v.size();
}

mean(std::vector<double>{1.0, 2.0, 3.0});   // OK → 2
// mean(std::vector<int>{1, 2, 3});         // ERROR at the call: int isn't floating_point
```

`std::floating_point` is a standard concept (`float`, `double`, `long double`). If you call `mean` with a `vector<int>`, the compiler says *"the associated constraints are not satisfied"* — a clear, immediate error, not a deep template dump.

### 20.3 Standard and custom concepts

The `<concepts>` header (and `<ranges>`, `<iterator>`) provides many ready concepts: `std::integral`, `std::floating_point`, `std::signed_integral`, `std::same_as<U>`, `std::convertible_to<U>`, `std::equality_comparable`, `std::sortable`, and more. You combine them with `&&`/`||` to define your own:

```cpp
template<typename T>
concept Numeric = std::integral<T> || std::floating_point<T>;   // any number

template<Numeric T>
T square(T x) { return x * x; }
// square(5) → 25,  square(2.5) → 6.25,  square("x") → compile error
```

`Numeric` now means "an integral or floating-point type," and any template constrained by `Numeric` accepts exactly those. Concepts can also express *syntactic* requirements (that a type supports certain operations) with a `requires` expression — e.g., "has a `.size()` and is iterable."

### 20.4 `requires` clauses

The `requires` clause is the general form — attach it to a template to state an arbitrary compile-time condition:

```cpp
template<typename T>
requires std::floating_point<T>          // requires clause (equivalent to the concise form)
T reciprocal(T x) { return T{1} / x; }
// reciprocal(4.0) → 0.25
```

A `requires` clause can combine concepts and even inline `requires` *expressions* that check whether specific operations compile:

```cpp
template<typename T>
requires requires(T a, T b) { a + b; a * b; }   // T must support + and *
T combine(T a, T b) { return a + b * a; }
```

The doubled `requires requires` is a `requires` *clause* containing a `requires` *expression* (an unfortunate but real syntax). You'll mostly use named concepts; the raw form is for one-off syntactic checks.

> 💡 **Idiom** — **Constrain your public template parameters with concepts.** For numerical code, `template<std::floating_point T>` (or a custom `Numeric`) states intent, rejects nonsense at the call site with a readable error, and serves as documentation of what the template needs. It's the modern replacement for the old SFINAE tricks (Chapter 31) — vastly clearer. Even a simple constraint (`std::floating_point`, `std::integral`) turns a confusing 50-line template error into a one-line "constraint not satisfied," which pays for itself the first time a colleague misuses your function.

> ⚙️ **Under the hood** — Concepts are checked at *overload resolution* time: a constrained template is only a candidate if its constraints are satisfied, so the compiler can reject it early (before instantiating the body) and pick the *best* matching overload. This also enables **concept-based overloading** — two templates with different constraints (`std::integral` vs `std::floating_point`), the right one chosen by the argument type. It replaces the old, arcane SFINAE (`std::enable_if`) machinery with something readable and diagnosable.

---

### Summary

- Unconstrained templates accept *any* type, giving cryptic deep errors on misuse. **Concepts** (C++20) state requirements, rejecting misuse **at the call site** with clear messages and documenting the template.
- Constrain concisely: **`template<std::floating_point T>`** — `T` must satisfy the concept.
- Use **standard concepts** (`std::integral`, `std::floating_point`, `std::same_as`, …) and combine them (`&&`/`||`) into **custom concepts** (`concept Numeric = ...`).
- The **`requires` clause** is the general form; a `requires` *expression* checks that specific operations compile.
- Concepts replace old **SFINAE** and enable clean **concept-based overloading**; always constrain public template parameters.

### Self-check quiz

1. What problem do concepts solve?
   <details><summary>Answer</summary>Unconstrained templates give cryptic errors deep in the library on misuse. Concepts state requirements so misuse is rejected at the call site with a clear message, and document what the template needs.</details>
2. How do you constrain a template to floating-point types only?
   <details><summary>Answer</summary>`template<std::floating_point T>` (concise form) or `template<typename T> requires std::floating_point<T>`.</details>
3. How do you define a custom concept for "any number"?
   <details><summary>Answer</summary>`template<typename T> concept Numeric = std::integral<T> || std::floating_point<T>;`.</details>
4. What do concepts replace, and why are they better?
   <details><summary>Answer</summary>They replace SFINAE (`std::enable_if`) tricks — with readable syntax, clear error messages, and clean concept-based overloading.</details>

### Exercises

**Exercise 20.1 — Constrain a function (guided).** Write a `safe_divide(a, b)` constrained to `std::floating_point` (so integer division can't sneak in), returning `a/b`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <concepts>
template<std::floating_point T>
T safe_divide(T a, T b) { return a / b; }
int main() {
    std::cout << std::format("{}\n", safe_divide(7.0, 2.0));   // 3.5
    // safe_divide(7, 2);   // ERROR: int is not floating_point (prevents integer division bug)
}
```

Output:
```text
3.5
```

**Why this works:** constraining to `std::floating_point` means `safe_divide(7, 2)` (integers) is *rejected at compile time* with a clear "constraint not satisfied" — preventing the integer-division bug (Chapter 3) by making the type requirement explicit. `safe_divide(7.0, 2.0)` gives `3.5`.

</details>

**Exercise 20.2 — Custom concept.** Define a `concept Scalar` for integral or floating-point types, and a `norm2(x, y)` returning `x*x + y*y` constrained by it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <concepts>
template<typename T>
concept Scalar = std::integral<T> || std::floating_point<T>;
template<Scalar T>
T norm2(T x, T y) { return x*x + y*y; }
int main() {
    std::cout << std::format("{} {}\n", norm2(3, 4), norm2(3.0, 4.0));   // 25 25
}
```

Output:
```text
25 25
```

**Why this works:** `Scalar` accepts integral *and* floating-point types, so `norm2` works for both `int` (25) and `double` (25). A non-numeric type (`std::string`) would be rejected at the call with a clear constraint error, instead of a confusing failure inside `x*x`.

</details>

**Exercise 20.3 — `requires` expression.** Constrain a `first_element(c)` to types that have a `.front()` member.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
template<typename C>
requires requires(C c) { c.front(); }        // C must have .front()
auto first_element(const C& c) { return c.front(); }
int main() {
    std::vector<double> v = {91.1, 91.2};
    std::cout << std::format("{}\n", first_element(v));   // 91.1
}
```

Output:
```text
91.1
```

**Why this works:** the `requires requires(C c) { c.front(); }` clause checks that `C` supports `.front()`; a `std::vector` does, so `first_element(v)` returns `91.1`. A type without `.front()` (like a raw array) would fail the constraint at the call site — a clear error, not a deep template failure.

</details>

### Chapter project: a constrained numeric accumulator

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–20. We constrain Chapter 16's generic `Stats<T>` to numeric types, so misuse (a `Stats<std::string>`) is a clear compile error, not a cryptic one.

**Goal.** Add a `Numeric` concept and constrain the `Stats<T>` template with it.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <concepts>
#include <limits>

template<typename T>
concept Numeric = std::integral<T> || std::floating_point<T>;

template<Numeric T>                          // ← constrained: only numeric element types
class Stats {
    long   n_   = 0;
    double sum_ = 0.0;
    T min_ = std::numeric_limits<T>::max();
    T max_ = std::numeric_limits<T>::lowest();
public:
    void add(T x) { ++n_; sum_ += x; if (x < min_) min_ = x; if (x > max_) max_ = x; }
    long   count() const { return n_; }
    double mean()  const { return n_ ? sum_ / n_ : 0.0; }
    T      min()   const { return min_; }
    T      max()   const { return max_; }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v17 — constrained stats ===\n";
    Stats<double> energy;
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) energy.add(e);
    std::cout << std::format("energy: n={} mean={:.4f} range=[{:.1f},{:.1f}] GeV\n",
                             energy.count(), energy.mean(), energy.min(), energy.max());
    // Stats<std::string> bad;   // ← now a CLEAR error: string does not satisfy Numeric
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v17 — constrained stats ===
energy: n=5 mean=91.1000 range=[90.9,91.3] GeV
```

**Commentary.**
- `Stats<T>` is now constrained by **`Numeric`** — it accepts `double`, `int`, `float`, etc., but a `Stats<std::string>` is rejected *at the declaration* with a readable "constraint not satisfied," rather than a confusing error deep inside `sum_ += x`.
- The concept makes the template **self-documenting**: `template<Numeric T> class Stats` tells a reader exactly what `T` may be, no comment needed. This is the small, high-value discipline of modern generic C++ — constrain, and errors and intent both become clear.
- Same behaviour as Chapter 16 (mean 91.1, range [90.9, 91.3]), but now misuse-proof. Eigen, the ranges library, and every modern numerical template library constrain their parameters this way.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Concept** | A named set of requirements on a template parameter (C++20). |
| **Constrained template** | `template<Concept T>` — `T` must satisfy the concept. |
| **`std::floating_point` / `std::integral`** | Standard concepts for number types. |
| **`requires` clause** | Attaches a compile-time condition to a template. |
| **`requires` expression** | Checks that given operations compile. |
| **Concept-based overloading** | Choosing an overload by which constraints a type satisfies. |
| **SFINAE** | The old (pre-concepts) constraint mechanism (Chapter 31). |

### What's next

Constrained, generic code is robust — but real programs also *fail*: files missing, data malformed, computations diverging. **[Ch.21 — Error Handling](#chapter-21--error-handling)** covers exceptions (and their RAII partnership), `std::optional`, and C++23's `std::expected` — how to report and handle failure cleanly in scientific code.

[↑ back to top](#chapter-20--concepts--constraints)


---

## Chapter 21 — Error Handling

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — RAII](#chapter-11--dynamic-memory--raii), [Ch.16 — Templates](#chapter-16--templates)

**Learning objectives** — after this chapter you will be able to:

- Throw and catch exceptions, and understand their RAII partnership.
- Use `noexcept` correctly.
- Model absence with `std::optional` and errors-as-values with `std::expected`.
- Choose the right error-handling mechanism for scientific code.

**In this chapter**

- [21.1 Exceptions](#211-exceptions)
- [21.2 Exceptions and RAII](#212-exceptions-and-raii)
- [21.3 `std::optional`: maybe a value](#213-stdoptional-maybe-a-value)
- [21.4 `std::expected`: value or error](#214-stdexpected-value-or-error)
- [21.5 Choosing a mechanism](#215-choosing-a-mechanism)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-robust-input-validation) · Glossary · What's next

---

### 21.1 Exceptions

An **exception** signals that something went wrong, transferring control up the call stack to a handler. You **`throw`** an exception and **`catch`** it with `try`/`catch`:

```cpp
#include <stdexcept>
double reciprocal(double x) {
    if (x == 0.0) throw std::invalid_argument("division by zero");
    return 1.0 / x;
}

try {
    reciprocal(0.0);
} catch (const std::exception& ex) {          // catch by const reference to the base
    std::cout << "caught: " << ex.what() << "\n";   // caught: division by zero
}
```

The standard exception hierarchy (from `<stdexcept>`) roots at **`std::exception`** (with a `.what()` message), with subtypes like `std::runtime_error`, `std::logic_error`, `std::invalid_argument`, `std::out_of_range`, and `std::bad_alloc` (allocation failure). Always **catch by `const&`** to the base (`const std::exception&`) — it catches any standard exception and avoids slicing (Chapter 15).

### 21.2 Exceptions and RAII

Exceptions and RAII (Chapter 11) are partners. When an exception is thrown, the stack **unwinds**: every local object between the `throw` and the `catch` is destroyed, in reverse order — so RAII objects release their resources automatically. This is *why* RAII matters: it makes code **exception-safe** for free.

```cpp
void process() {
    std::vector<double> data(1000);   // RAII: owns memory
    risky_operation();                // if this throws...
    // ...data's destructor still runs during unwinding → no leak
}
```

Contrast Chapter 11's raw-`new` version, which leaked on exception. RAII members (`std::vector`, smart pointers) make cleanup automatic without local `try`/`catch`. That provides resource safety, but not automatically the **strong guarantee**: a multi-step operation can still leave logical state partially changed. Design updates as commit-or-rollback transactions (often build a temporary, then `swap`) when callers require all-or-nothing behaviour.

> ⚠️ **Gotcha — never let a destructor throw.** If a destructor throws *during* stack unwinding (while another exception is propagating), the program **terminates** (`std::terminate`). Destructors must not throw — mark them `noexcept` (they are by default) and handle any errors internally. Also: **don't use exceptions for normal control flow** — they're for *exceptional* conditions; throwing to signal "not found" in a hot loop is slow and obscures logic (use `optional`/`expected` instead, §21.3–21.5).

### 21.3 `std::optional`: maybe a value

Not every failure is exceptional. Often a function simply *might not have a result* — a lookup that finds nothing, a computation undefined for some inputs. **`std::optional<T>`** models "a `T`, or nothing," without exceptions:

```cpp
#include <optional>
std::optional<double> safe_sqrt(double x) {
    if (x < 0) return std::nullopt;    // no result
    return std::sqrt(x);               // a result
}

auto r = safe_sqrt(16.0);
r.has_value();        // true
r.value();            // 4.0   (throws if empty — check first, or...)
r.value_or(-1.0);     // 4.0   (default if empty)
// safe_sqrt(-4.0).has_value() → false
```

`std::optional` makes "absence" explicit in the *type* — a caller can't ignore it the way they might ignore a magic sentinel value (like returning `-1`). Access with `has_value()`/`value()`/`value_or(default)`, or the `*`/`->` operators (after checking).

### 21.4 `std::expected`: value or error

`optional` says *whether* something failed, but not *why*. C++23's **`std::expected<T, E>`** carries either a value (`T`) **or** an error (`E`) — the modern "errors as values" approach, without exceptions:

```cpp
#include <expected>
std::expected<double, std::string> parse_energy(double e) {
    if (e < 0)   return std::unexpected("negative energy");
    if (e > 1e6) return std::unexpected("energy out of range");
    return e;                          // success: the value
}

auto ok  = parse_energy(91.2);
auto bad = parse_energy(-5.0);
ok.value();      // 91.2         (has_value() is true)
bad.error();     // "negative energy"   (has_value() is false)
```

`std::expected` shines for *recoverable, expected* failures where the caller wants the reason: parsing, validation, I/O that may fail predictably. It's checkable (`has_value()`), gives the value (`.value()`) or error (`.error()`), and composes (`.and_then`, `.transform`, `.or_else`) into pipelines — without the cost and non-locality of exceptions.

> ⚙️ **Under the hood** — `std::optional<T>` and `std::expected<T, E>` store their value *in place* (a union, no heap allocation) plus a flag — so they're cheap. Returning them is as fast as returning a struct (RVO, Chapter 6). Unlike exceptions, they have **zero cost when there's no error** *and* zero cost on the error path (exceptions are cheap when not thrown but expensive when thrown, due to stack unwinding). This predictable cost is why `expected` is favoured in performance-sensitive and embedded code.

### 21.5 Choosing a mechanism

A practical decision guide for scientific code:

| Situation | Use |
|-----------|-----|
| Truly *exceptional*, rarely-hit errors (out of memory, corrupt state, programmer bugs) | **exception** (`throw`) |
| A value that may legitimately be *absent* (lookup miss, undefined result) | **`std::optional<T>`** |
| A *recoverable* failure where the caller needs the *reason* (parse/validation/IO error) | **`std::expected<T, E>`** |
| A precondition violation (bad argument, "can't happen") | **`throw` / assert** — fail loudly |
| A hot inner loop where the "failure" is common | **`optional`/`expected`** (never exceptions) |

> 💡 **Idiom** — Reserve **exceptions** for genuinely exceptional situations (they're expensive when thrown and non-local); use **`std::optional`** for "maybe absent" and **`std::expected`** for "value or a reason it failed." In numerical/HPC code especially, prefer `optional`/`expected` on any path that runs often — a per-event validation that threw would tank performance. And *always* lean on **RAII** so that whichever mechanism fires, resources are cleaned up automatically. Clear, cheap, local error handling is a mark of robust scientific software.

---

### Summary

- **Exceptions** (`throw`/`try`/`catch`) transfer control to a handler; catch by **`const std::exception&`**. The hierarchy roots at `std::exception` (`.what()`).
- Exceptions **partner with RAII**: stack unwinding destroys locals, so RAII objects free resources — making code exception-safe for free. **Never throw from a destructor.**
- **`std::optional<T>`** models "a value or nothing" (lookup misses, undefined results) — `has_value`/`value`/`value_or`.
- **`std::expected<T, E>`** (C++23) carries a value *or* an error — recoverable failures with a reason; cheap, checkable, composable.
- **Choose**: exceptions for truly exceptional cases, `optional` for absence, `expected` for recoverable errors — and never exceptions in hot loops. Always rely on RAII for cleanup.

### Self-check quiz

1. Why catch exceptions by `const std::exception&`?
   <details><summary>Answer</summary>It catches any standard exception (base class) and avoids object slicing that catching by value would cause; `.what()` gives the message.</details>
2. How do exceptions and RAII work together?
   <details><summary>Answer</summary>When an exception unwinds the stack, local objects' destructors run in reverse order, so RAII objects release their resources — making the code exception-safe without `try`/`catch`.</details>
3. When use `std::optional` vs `std::expected`?
   <details><summary>Answer</summary>`optional` when a value may simply be absent (no reason needed); `expected` when a failure is recoverable and the caller needs to know *why* (an error value).</details>
4. Why avoid exceptions in a hot loop?
   <details><summary>Answer</summary>Throwing is expensive (stack unwinding) and non-local; a common "failure" in a hot path should use `optional`/`expected`, which have predictable near-zero cost.</details>

### Exercises

**Exercise 21.1 — Optional lookup (guided).** Write `element_at(vec, i)` returning `std::optional<double>` — the element, or `nullopt` if out of range.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <optional>
#include <vector>
std::optional<double> element_at(const std::vector<double>& v, std::size_t i) {
    if (i >= v.size()) return std::nullopt;
    return v[i];
}
int main() {
    std::vector<double> v = {91.1, 91.2, 91.3};
    std::cout << std::format("[1]={} [9]={}\n", element_at(v, 1).value_or(-1.0),
                                                 element_at(v, 9).value_or(-1.0));
}
```

Output:
```text
[1]=91.2 [9]=-1
```

**Why this works:** `element_at` returns the value for a valid index and `std::nullopt` for out-of-range — absence encoded in the type. `value_or(-1.0)` supplies a default for the missing case, so `[9]` yields `-1`. No exception, no magic sentinel that could be mistaken for data.

</details>

**Exercise 21.2 — Expected validation.** Write `validate_probability(p)` returning `std::expected<double, std::string>` — the value if `0 ≤ p ≤ 1`, else an error message.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <expected>
#include <string>
std::expected<double, std::string> validate_probability(double p) {
    if (p < 0.0) return std::unexpected("probability < 0");
    if (p > 1.0) return std::unexpected("probability > 1");
    return p;
}
int main() {
    for (double p : {0.5, -0.1, 1.5}) {
        auto r = validate_probability(p);
        if (r) std::cout << std::format("ok: {}\n", r.value());
        else   std::cout << std::format("error: {}\n", r.error());
    }
}
```

Output:
```text
ok: 0.5
error: probability < 0
error: probability > 1
```

**Why this works:** `validate_probability` returns the value for a valid probability and a descriptive error otherwise. The caller checks `if (r)` (true when it holds a value) and reads `.value()` or `.error()` accordingly — recoverable failure with a reason, no exception.

</details>

**Exercise 21.3 — Exception safety with RAII.** Show that a `std::vector` is freed even when a function throws after allocating it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <vector>
#include <stdexcept>
void process() {
    std::vector<double> data(1000);      // RAII: owns 1000 doubles
    throw std::runtime_error("boom");    // throws — data's destructor still runs
}
int main() {
    try { process(); }
    catch (const std::exception& e) { std::cout << "caught: " << e.what() << "\n"; }
    std::cout << "no leak (vector freed during unwinding)\n";
}
```

Output:
```text
caught: boom
no leak (vector freed during unwinding)
```

**Why this works:** when `process` throws, the stack unwinds and `data`'s destructor runs — freeing its 1000 doubles — *before* control reaches the handler. So the exception causes no leak, with no `try`/`catch` inside `process`. (AddressSanitizer confirms no leak.) This is RAII's exception-safety guarantee.

</details>

### Chapter project: robust input validation

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–21. Real data has bad values. We make the toolkit's dataset loading **validate** each energy with `std::expected`, rejecting bad input with a reason — no crashes, no silent corruption.

**Goal.** A validating `add` returning `std::expected`, so loading reports which values were rejected and why.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <expected>
#include <string>
#include <cmath>

class Dataset {
    std::vector<double> energies_;
public:
    // Validate on the way in: return the accepted value, or an error reason.
    std::expected<double, std::string> add(double e) {
        if (std::isnan(e))  return std::unexpected("NaN energy");
        if (e < 0.0)        return std::unexpected("negative energy");
        if (e > 1e6)        return std::unexpected("energy out of range");
        energies_.push_back(e);
        return e;
    }
    double mean() const {
        if (energies_.empty()) return 0.0;
        double s = 0; for (double x : energies_) s += x; return s / energies_.size();
    }
    std::size_t size() const { return energies_.size(); }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v18 — validated loading ===\n";
    Dataset d;
    double raw[] = {91.1, -5.0, 91.3, std::nan(""), 91.2, 91.0};
    for (double e : raw) {
        auto r = d.add(e);
        if (!r) std::cout << std::format("  rejected {}: {}\n", e, r.error());
    }
    std::cout << std::format("accepted {} events, mean = {:.4f} GeV\n", d.size(), d.mean());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v18 — validated loading ===
  rejected -5: negative energy
  rejected nan: NaN energy
accepted 4 events, mean = 91.1500 GeV
```

**Commentary.**
- `add` returns **`std::expected<double, std::string>`** — it validates each energy (rejecting NaN, negatives, and out-of-range values, guarding against the NaN-propagation trap from Chapter 3) and reports *why* a value was rejected, without throwing. The loading loop checks `if (!r)` and logs rejections.
- Four of six values are accepted (91.1, 91.3, 91.2, 91.0); the negative and the NaN are rejected with clear reasons. The mean of the good data is 91.15 GeV — *uncorrupted* by the bad inputs, exactly the robustness scientific pipelines need.
- This is the idiomatic modern approach: **validate at the boundary, report errors as values**. It's cheaper and clearer than exceptions for the common case of "some input is bad," and it makes the toolkit trustworthy — no silent NaN reaching a histogram (Chapter 3's warning).

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Exception** | A thrown signal transferring control to a handler. |
| **`std::exception`** | Base of the standard exception hierarchy (`.what()`). |
| **Stack unwinding** | Destroying locals as an exception propagates (RAII cleanup). |
| **`noexcept`** | Promises a function won't throw (destructors are, by default). |
| **`std::optional<T>`** | A value or nothing (`has_value`/`value_or`). |
| **`std::expected<T, E>`** | A value or an error (C++23; `value`/`error`). |
| **`std::unexpected`** | Constructs the error case of an `expected`. |
| **Errors as values** | Returning failures (optional/expected) instead of throwing. |

### What's next

That completes **Part 3 — Generic Programming & the STL**. You can write generic, constrained, robust code over the standard containers and algorithms. **Part 4 turns to the science: [Ch.22 — Random Numbers & Monte Carlo](#chapter-22--random-numbers--monte-carlo)** — the `<random>` library and the simulation techniques at the heart of computational physics.

[↑ back to top](#chapter-21--error-handling)


---

## Chapter 22 — Random Numbers & Monte Carlo

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.18 — Containers](#chapter-18--stl-containers), [Ch.19 — Algorithms](#chapter-19--iterators-algorithms--numeric)

**Learning objectives** — after this chapter you will be able to:

- Generate random numbers correctly with `<random>` (engines + distributions).
- Ensure reproducibility by seeding.
- Perform Monte Carlo integration and simulation.
- Build a physics-style event generator.

**In this chapter**

- [22.1 Engines and distributions](#221-engines-and-distributions)
- [22.2 Reproducibility](#222-reproducibility)
- [22.3 Monte Carlo integration](#223-monte-carlo-integration)
- [22.4 Monte Carlo simulation](#224-monte-carlo-simulation)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-z-boson-event-generator) · Glossary · What's next

---

### 22.1 Engines and distributions

Monte Carlo methods — simulating physical processes with random sampling — are foundational to computational physics (particle transport in Geant4, integration in many dimensions, statistical inference). C++'s **`<random>`** library does this *right*, separating two concerns:

- An **engine** generates raw pseudo-random bits. **`std::mt19937`** (the Mersenne Twister) is the standard high-quality choice.
- A **distribution** shapes those bits into numbers with a desired probability law — uniform, Gaussian, Poisson, exponential, …

```cpp
#include <random>
std::mt19937 rng(42);                                  // engine, seeded with 42
std::uniform_real_distribution<double> uni(0.0, 1.0);  // uniform in [0, 1)
std::normal_distribution<double>       gauss(91.19, 2.5);  // mean 91.19, sigma 2.5
std::poisson_distribution<int>         pois(3.5);      // mean 3.5

double u = uni(rng);      // draw a uniform     → e.g. 0.1834
double g = gauss(rng);    // draw a Gaussian    → e.g. 92.37
int    k = pois(rng);     // draw a Poisson int → e.g. 2
```

You call `distribution(engine)` to draw a value. The available distributions cover the physicist's needs: `uniform_real`/`uniform_int`, `normal` (Gaussian), `poisson`, `exponential`, `gamma`, `binomial`, `chi_squared`, and more.

> ⚠️ **Gotcha — never use `rand()`.** C's `std::rand()` (and `rand() % n`) is *low quality* (poor statistical properties, correlations) and *biased* (`% n` skews the distribution). It has no place in scientific code. **Always use `<random>`** — a proper engine (`mt19937`) plus a distribution, which is unbiased and statistically sound. Using `rand()` for a Monte Carlo simulation can produce subtly wrong physics.

### 22.2 Reproducibility

Scientific results must be **reproducible**: the same seed must give the same sequence, so a run can be repeated and debugged. Seeding the engine with a fixed value guarantees this:

```cpp
std::mt19937 rng(42);     // fixed seed → identical sequence every run
```

For runs that should differ (production, independent samples), seed from a random source: `std::random_device rd; std::mt19937 rng(rd());`. But *record the seed you used* — reproducibility means being able to *re-run* an analysis exactly, which is impossible without the seed.

> 💡 **Idiom** — **Seed explicitly and log the seed.** Use a fixed seed (like `mt19937 rng(42)`) for tests and debugging so results are deterministic; for production, seed from `std::random_device` but *store* the seed in your output so any run can be reproduced. Never rely on an unseeded or time-seeded generator whose seed you can't recover — irreproducible Monte Carlo is a scientific liability. Also: create *one* engine and reuse it; constructing a fresh engine per draw is slow and can correlate.

### 22.3 Monte Carlo integration

Monte Carlo **integration** estimates integrals (especially high-dimensional ones where grid methods fail) by random sampling. The classic teaching example estimates π by throwing points into a unit square and counting those inside the quarter-circle:

```cpp
std::mt19937 rng(42);
std::uniform_real_distribution<double> uni(0.0, 1.0);
int inside = 0, N = 1'000'000;
for (int i = 0; i < N; ++i) {
    double x = uni(rng), y = uni(rng);
    if (x*x + y*y <= 1.0) ++inside;          // inside the quarter circle?
}
double pi = 4.0 * inside / N;                 // → 3.14099
```

The fraction inside approximates the area ratio (π/4), so `4 × fraction ≈ π`. More generally, ∫f over a region ≈ (volume) × (average of f at random points):

```cpp
double sum = 0.0;
for (int i = 0; i < N; ++i) { double x = uni(rng); sum += x * x; }
double integral = sum / N;                    // ∫₀¹ x² dx ≈ 0.33342  (exact 1/3)
```

MC integration's error shrinks as **1/√N** — *independent of dimension*, which is why it wins for high-dimensional integrals (phase-space integration in particle physics) where a grid would need impossibly many points.

> ⚙️ **Under the hood** — The 1/√N convergence is the central limit theorem: the estimate is an average of N random samples, whose standard error is σ/√N. To halve the error you need 4× the samples — MC is *slow to converge* but *dimension-independent*, the opposite trade-off from grid quadrature (fast in 1-D, hopeless in 10-D). *Variance reduction* techniques (importance sampling, stratification) improve the constant without changing the 1/√N law — a deep topic in computational physics.

### 22.4 Monte Carlo simulation

Beyond integration, Monte Carlo **simulates** stochastic processes — generating synthetic "events" from a physical distribution, exactly as a detector simulation or event generator does. Draw energies from a Gaussian to simulate a resonance peak:

```cpp
std::mt19937 rng(123);
std::normal_distribution<double> mass_peak(91.19, 2.5);   // Z boson: mean, width
std::vector<double> events;
events.reserve(10000);
for (int i = 0; i < 10000; ++i) events.push_back(mass_peak(rng));
// events now sample a Gaussian centred at 91.19 GeV — a simulated Z peak
```

These simulated events feed the rest of the toolkit — histograms (Chapter 9), statistics (Chapter 19), selection cuts — letting you test an analysis on data whose "truth" you know before running it on real data. This is precisely how experiments validate their pipelines.

---

### Summary

- **`<random>`** separates **engines** (`std::mt19937` — quality bits) from **distributions** (`uniform_real`, `normal`, `poisson`, …); call `dist(engine)` to draw. **Never use `rand()`** (low quality, biased).
- **Reproducibility**: seed the engine (fixed seed for tests; `random_device` for production, but *log the seed*). Reuse one engine.
- **Monte Carlo integration** estimates integrals by random sampling (∫f ≈ volume × average f); error ∝ **1/√N**, *dimension-independent* — wins for high-D integrals.
- **Monte Carlo simulation** generates synthetic events from a distribution (a Gaussian mass peak, a Poisson hit count) to test analyses — the event-generator pattern of particle physics.

### Self-check quiz

1. What are the two components of `<random>`, and why separate them?
   <details><summary>Answer</summary>An **engine** (generates raw random bits, e.g. `mt19937`) and a **distribution** (shapes them into a probability law). Separating lets any engine feed any distribution.</details>
2. Why must you seed the engine, and log the seed?
   <details><summary>Answer</summary>A fixed seed makes the sequence reproducible (essential for debugging and repeating a run). Logging the seed lets any production run be reproduced exactly.</details>
3. How does Monte Carlo integration error scale, and why does that favour high dimensions?
   <details><summary>Answer</summary>As 1/√N, *independent of dimension* — unlike grid methods that blow up with dimension. So MC wins for high-dimensional integrals.</details>
4. Why never use `std::rand()`?
   <details><summary>Answer</summary>It has poor statistical quality and `rand() % n` is biased — unsuitable for scientific Monte Carlo, which needs unbiased, high-quality randomness from `<random>`.</details>

### Exercises

**Exercise 22.1 — Estimate π (guided).** Estimate π by Monte Carlo with a fixed seed, over 1,000,000 samples.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <random>
int main() {
    std::mt19937 rng(42);
    std::uniform_real_distribution<double> uni(0.0, 1.0);
    int inside = 0, N = 1'000'000;
    for (int i = 0; i < N; ++i) {
        double x = uni(rng), y = uni(rng);
        if (x*x + y*y <= 1.0) ++inside;
    }
    std::cout << std::format("pi ~= {:.5f}\n", 4.0 * inside / N);   // 3.14099
}
```

Output:
```text
pi ~= 3.14099
```

**Why this works:** points uniform in the unit square fall inside the quarter-circle with probability π/4, so `4·(inside/N)` estimates π. With seed 42 and a million samples the estimate is 3.14099 — the same every run (reproducible). More samples → closer (error ∝ 1/√N).

</details>

**Exercise 22.2 — Sample a Gaussian.** Draw 5 energies from a Gaussian (mean 91.19, σ 2.5) with seed 7 and print them.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <random>
int main() {
    std::mt19937 rng(7);
    std::normal_distribution<double> gauss(91.19, 2.5);
    for (int i = 0; i < 5; ++i) std::cout << std::format("{:.2f} ", gauss(rng));
    std::cout << "\n";
}
```

Output (deterministic for seed 7):
```text
89.39 88.48 91.10 92.19 88.46
```

**Why this works:** `normal_distribution(91.19, 2.5)` draws values scattered around 91.19 with standard deviation 2.5 — a simulated resonance mass measurement. Seed 7 fixes the sequence, so these five values are the same every run.

</details>

**Exercise 22.3 — Monte Carlo integral.** Estimate ∫₀¹ e^x dx (exact = e − 1 ≈ 1.71828) by MC.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <random>
#include <cmath>
int main() {
    std::mt19937 rng(42);
    std::uniform_real_distribution<double> uni(0.0, 1.0);
    double sum = 0.0; int N = 1'000'000;
    for (int i = 0; i < N; ++i) sum += std::exp(uni(rng));
    std::cout << std::format("integral ~= {:.5f} (exact 1.71828)\n", sum / N);
}
```

Output:
```text
integral ~= 1.71835 (exact 1.71828)
```

**Why this works:** ∫₀¹ f(x) dx equals the average of f over uniformly-random x in [0,1]. Averaging `exp(x)` at a million random points gives ≈ 1.71835, close to the exact `e − 1 ≈ 1.71828` (within the 1/√N Monte Carlo error).

</details>

### Chapter project: a Z-boson event generator

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit** — the science comes alive. **Builds on:** Ch.1–22. We *generate* simulated events — dilepton masses scattered around the Z boson — and histogram them, reproducing the classic resonance peak.

**Goal.** Simulate 100,000 dimuon-mass events from a Gaussian Z peak, histogram them, and report the reconstructed mean.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <random>
#include <vector>
#include <cmath>

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v19 — Z-boson generator ===\n";

    std::mt19937 rng(2026);                                 // seeded → reproducible
    std::normal_distribution<double> Zmass(91.19, 2.5);     // Z mass 91.19 GeV, width 2.5

    // Histogram: 20 bins over [85, 97] GeV
    const int    nbins = 20;
    const double lo = 85.0, hi = 97.0;
    std::vector<int> hist(nbins, 0);

    const int N = 100'000;
    double sum = 0.0;
    for (int i = 0; i < N; ++i) {
        double m = Zmass(rng);                               // simulated invariant mass
        sum += m;
        if (m >= lo && m < hi) {
            int b = static_cast<int>((m - lo) / (hi - lo) * nbins);
            ++hist[b];
        }
    }

    // Print the histogram as a horizontal bar chart
    for (int b = 0; b < nbins; ++b) {
        double edge = lo + b * (hi - lo) / nbins;
        int bars = hist[b] / 400;                            // scale for display
        std::cout << std::format("{:5.1f} | ", edge);
        for (int k = 0; k < bars; ++k) std::cout << '#';
        std::cout << ' ' << hist[b] << '\n';
    }
    std::cout << std::format("generated {} events, mean mass = {:.3f} GeV\n", N, sum / N);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v19 — Z-boson generator ===
 85.0 | # 585
 85.6 | ## 1007
 86.2 | #### 1662
 86.8 | ###### 2526
 87.4 | ######### 3637
 88.0 | ########### 4749
 88.6 | ############### 6348
 89.2 | ################## 7536
 89.8 | ###################### 8889
 90.4 | ####################### 9468
 91.0 | ######################## 9685
 91.6 | ###################### 9011
 92.2 | #################### 8276
 92.8 | ################# 7191
 93.4 | ############## 5722
 94.0 | ########### 4438
 94.6 | ####### 3184
 95.2 | ##### 2167
 95.8 | ### 1420
 96.4 | ## 850
generated 100000 events, mean mass = 91.194 GeV
```

**Commentary.**
- We **simulated** 100,000 dimuon events by drawing invariant masses from a Gaussian centred at the Z mass (91.19 GeV) with the detector's resolution (σ = 2.5 GeV) — a Monte Carlo event generator in miniature.
- The histogram (Chapter 9's idea, here as a bar chart) shows the unmistakable **resonance peak** at ~91 GeV (the 91.0 bin holds 9685 events) — the shape every LHC dilepton analysis sees. The reconstructed mean, **91.194 GeV**, recovers the input 91.19, validating the pipeline.
- Everything is **reproducible** (seed 2026): re-running gives the identical peak. This is exactly how experiments generate "Monte Carlo truth" samples to test an analysis before touching real data.
- The pieces assembled here — `<random>` (this chapter), histogramming (Chapter 9), statistics (Chapter 19), `std::vector` (Chapter 18) — are the core of a real analysis toolkit. The next chapters add numerical methods, linear algebra, and performance to make it production-grade.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Engine** | A pseudo-random bit generator (`std::mt19937`). |
| **Distribution** | Shapes bits into a probability law (`normal`, `poisson`, …). |
| **Seed** | The value initializing an engine (fixed → reproducible). |
| **`std::random_device`** | A source of non-deterministic seeds. |
| **Monte Carlo integration** | Estimating integrals by random sampling (error ∝ 1/√N). |
| **Monte Carlo simulation** | Generating synthetic events from a distribution. |
| **Event generator** | Code producing simulated physics events. |

### What's next

You can generate and integrate with randomness. **[Ch.23 — Numerical Algorithms](#chapter-23--numerical-algorithms)** covers the deterministic numerical methods — root-finding, integration by quadrature, and ODE solvers — with a careful eye on stability and accuracy, the other half of computational physics.

[↑ back to top](#chapter-22--random-numbers--monte-carlo)


---

## Chapter 23 — Numerical Algorithms

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Floating-Point](#chapter-3--floating-point--numeric-types), [Ch.7 — Lambdas](#chapter-7--functions-ii-lambdas--function-objects)

**Learning objectives** — after this chapter you will be able to:

- Find roots with bisection and Newton–Raphson.
- Integrate functions numerically (trapezoidal, Simpson).
- Solve ODEs with Euler and Runge–Kutta (RK4).
- Reason about accuracy and stability.

**In this chapter**

- [23.1 Root-finding](#231-root-finding)
- [23.2 Numerical integration](#232-numerical-integration)
- [23.3 Solving ODEs](#233-solving-odes)
- [23.4 Accuracy and stability](#234-accuracy-and-stability)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-decay-simulation) · Glossary · What's next

---

### 23.1 Root-finding

Finding where *f(x) = 0* — a root — is a fundamental numerical task (equilibrium points, threshold energies, inverse functions). Two workhorses:

**Bisection** — robust and simple. If `f` changes sign over `[a, b]`, a root lies between; repeatedly halve the interval, keeping the half where the sign changes:

```cpp
double bisect(const std::function<double(double)>& f, double a, double b, double tol = 1e-10) {
    while (b - a > tol) {
        double m = 0.5 * (a + b);
        if (f(a) * f(m) <= 0) b = m; else a = m;   // keep the sign-changing half
    }
    return 0.5 * (a + b);
}
// bisect([](double x){ return x*x - 2; }, 0, 2) → 1.4142135624   (√2)
```

**Newton–Raphson** — fast (quadratic convergence) when you have the derivative: iterate `x ← x − f(x)/f′(x)`:

```cpp
double newton(auto f, auto df, double x, int iters = 50) {
    for (int i = 0; i < iters; ++i) x -= f(x) / df(x);
    return x;
}
// newton(x²−2, 2x, start=1) → 1.4142135624   (converges in ~5 steps)
```

Bisection *always* converges (given a sign change) but slowly (linear); Newton is fast but can diverge if the start is poor or `f′` vanishes. A robust solver often combines them.

> ⚠️ **Gotcha — the tolerance and floating-point.** A root-finder's stopping tolerance can't be tighter than floating-point precision allows (Chapter 3): asking for `tol = 1e-20` on a `double` loops forever, since `b - a` can't shrink below ~1e-16 relative. Use a sensible tolerance (`1e-10`) *and* an iteration cap. And `f(a) * f(m)` can **overflow** for large values — compare *signs* (`std::signbit`) instead of multiplying in production code.

### 23.2 Numerical integration

Numerical **quadrature** approximates ∫f by evaluating `f` at sample points. The **trapezoidal rule** connects samples with straight lines:

```cpp
double trapezoid(auto f, double a, double b, int n) {
    double h = (b - a) / n, s = 0.5 * (f(a) + f(b));
    for (int i = 1; i < n; ++i) s += f(a + i * h);
    return s * h;
}
// trapezoid(x², 0, 1, 1000) → 0.333333   (∫₀¹ x² = 1/3)
```

**Simpson's rule** fits parabolas through triples of points and is far more accurate for the same number of samples (error ∝ h⁴ vs the trapezoidal h²). For smooth functions, prefer Simpson or adaptive quadrature; for oscillatory or singular integrands, specialized methods (or the GSL library, Chapter 28) are needed.

> 💡 **Idiom** — For deterministic 1-D integrals of smooth functions, use **Simpson's rule** (or an adaptive quadrature) — its h⁴ error means far fewer function evaluations for a target accuracy than the trapezoidal rule. But recall Chapter 22: for *high-dimensional* integrals (phase space in particle physics), deterministic quadrature is hopeless (the grid grows exponentially) — **Monte Carlo** wins there. Match the method to the dimension: quadrature in 1–3 D, Monte Carlo above.

### 23.3 Solving ODEs

Ordinary differential equations *dy/dx = f(x, y)* describe dynamics — motion, decay, reaction rates. The simplest solver, **Euler's method**, steps `y ← y + h·f(x, y)` — but it's inaccurate (error ∝ h) and unstable. The standard workhorse is **fourth-order Runge–Kutta (RK4)**, which samples the slope four times per step:

```cpp
double rk4(auto f, double x, double y, double h) {
    double k1 = f(x, y);
    double k2 = f(x + h/2, y + h/2*k1);
    double k3 = f(x + h/2, y + h/2*k2);
    double k4 = f(x + h,   y + h*k3);
    return y + h/6 * (k1 + 2*k2 + 2*k3 + k4);
}

// solve dy/dx = y, y(0)=1 over [0,1]  → e
double y = 1.0, h = 0.01;
for (double x = 0; x < 1.0 - 1e-9; x += h) y = rk4([](double, double yy){ return yy; }, x, y, h);
// y(1) → 2.71828183   (exact e = 2.71828183)
```

RK4's error per step is ∝ h⁵ (global h⁴) — with h = 0.01 it recovers *e* to 8 digits. It's the default for non-stiff ODEs; stiff systems need implicit solvers (backward Euler, BDF).

### 23.4 Accuracy and stability

Two distinct concerns govern every numerical method:

- **Accuracy** — how close the result is to the true answer, set by the method's *order* (trapezoidal h², Simpson h⁴, RK4 h⁴) and the step size `h`. Smaller `h` → more accurate, but more work, and eventually *rounding* error (Chapter 3) dominates truncation error — there's an optimal `h`.
- **Stability** — whether errors *grow* as the computation proceeds. Euler's method can be *unstable* for some equations (errors blow up) even with small `h`; RK4 and implicit methods have larger stability regions. A stable-but-inaccurate result is useless; an accurate-but-unstable method diverges. Both matter.

> ⚙️ **Under the hood** — Every step of a numerical method incurs **truncation error** (from approximating the true operation) and **rounding error** (from floating-point, Chapter 3). Truncation shrinks as `h → 0` (∝ hᵖ for an order-p method); rounding *grows* as more steps accumulate. So error is a U-curve in `h`: too large and truncation dominates, too small and rounding (and cost) do. The sweet spot depends on the method's order and the machine precision — which is why you don't just make `h` tiny. This interplay is the core of numerical analysis, and why a physicist validates a solver against a known solution (as we do with *e*) before trusting it.

---

### Summary

- **Root-finding**: **bisection** (robust, linear, needs a sign change) and **Newton–Raphson** (fast/quadratic, needs the derivative, can diverge). Use sensible tolerances and iteration caps.
- **Integration**: **trapezoidal** (error ∝ h²) and **Simpson** (∝ h⁴, prefer it) for smooth 1-D integrals; **Monte Carlo** (Chapter 22) for high dimensions.
- **ODEs**: **Euler** (simple, inaccurate/unstable) vs **RK4** (order-4, the default) — RK4 recovers *e* to 8 digits solving `y′ = y`. Stiff systems need implicit solvers.
- **Accuracy** (method order + step `h`) and **stability** (do errors grow?) are distinct; total error is a U-curve in `h` (truncation vs rounding) — validate solvers against known solutions.

### Self-check quiz

1. Bisection vs Newton — trade-offs?
   <details><summary>Answer</summary>Bisection always converges given a sign change but slowly (linear), needing no derivative. Newton converges fast (quadratic) but needs `f′` and can diverge from a poor start.</details>
2. Why is Simpson's rule usually better than the trapezoidal rule?
   <details><summary>Answer</summary>Its error scales as h⁴ (vs h² for trapezoidal), so it achieves a target accuracy with far fewer function evaluations for smooth functions.</details>
3. Why prefer RK4 over Euler for ODEs?
   <details><summary>Answer</summary>RK4 is order-4 accurate (error ∝ h⁴) and far more stable; Euler is order-1 and can be unstable. RK4 recovers `e` to 8 digits where Euler would be crude.</details>
4. Why doesn't making the step `h` arbitrarily small always help?
   <details><summary>Answer</summary>Truncation error shrinks with `h`, but rounding error accumulates over more steps and cost rises — total error is a U-curve, so there's an optimal `h`.</details>

### Exercises

**Exercise 23.1 — Find a root (guided).** Use bisection to find the root of `cos(x) − x = 0` in `[0, 1]`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <functional>
double bisect(const std::function<double(double)>& f, double a, double b, double tol = 1e-10) {
    while (b - a > tol) { double m = 0.5*(a+b); if (f(a)*f(m) <= 0) b = m; else a = m; }
    return 0.5*(a+b);
}
int main() {
    double r = bisect([](double x){ return std::cos(x) - x; }, 0.0, 1.0);
    std::cout << std::format("root = {:.8f}\n", r);   // 0.73908513
}
```

Output:
```text
root = 0.73908513
```

**Why this works:** `cos(x) − x` is positive at 0 (cos 0 = 1 > 0) and negative at 1 (cos 1 ≈ 0.54 < 1), so a root lies in [0,1]. Bisection halves the interval until it's within tolerance, converging to the Dottie number `0.73908513` — the unique fixed point of cosine.

</details>

**Exercise 23.2 — Integrate numerically.** Compute ∫₀^π sin(x) dx (exact = 2) with the trapezoidal rule and 1000 intervals.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <numbers>
#include <functional>
double trapezoid(const std::function<double(double)>& f, double a, double b, int n) {
    double h = (b-a)/n, s = 0.5*(f(a)+f(b));
    for (int i = 1; i < n; ++i) s += f(a + i*h);
    return s*h;
}
int main() {
    double I = trapezoid([](double x){ return std::sin(x); }, 0.0, std::numbers::pi, 1000);
    std::cout << std::format("integral = {:.6f} (exact 2)\n", I);
}
```

Output:
```text
integral = 1.999998 (exact 2)
```

**Why this works:** ∫₀^π sin = [−cos]₀^π = 2. The trapezoidal rule with 1000 intervals over [0, π] gives 1.999998 — off by ~2×10⁻⁶, the h² truncation error at this resolution. Simpson's rule would nail it to machine precision with the same samples.

</details>

**Exercise 23.3 — Solve an ODE.** Solve radioactive decay `dN/dt = −λN`, N(0)=1000, λ=0.1, to t=10 with RK4 (exact = 1000·e⁻¹).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <functional>
double rk4(const std::function<double(double,double)>& f, double x, double y, double h) {
    double k1=f(x,y), k2=f(x+h/2,y+h/2*k1), k3=f(x+h/2,y+h/2*k2), k4=f(x+h,y+h*k3);
    return y + h/6*(k1+2*k2+2*k3+k4);
}
int main() {
    const double lambda = 0.1;
    double N = 1000.0, h = 0.01;
    for (double t = 0; t < 10.0 - 1e-9; t += h)
        N = rk4([lambda](double, double n){ return -lambda*n; }, t, N, h);
    std::cout << std::format("N(10) = {:.4f} (exact {:.4f})\n", N, 1000.0*std::exp(-1.0));
}
```

Output:
```text
N(10) = 367.8794 (exact 367.8794)
```

**Why this works:** exponential decay `N(t) = N₀ e^(−λt)`, so `N(10) = 1000·e^(−1) ≈ 367.88`. RK4 stepping with h = 0.01 recovers it to four digits — the standard way to simulate decay, reaction kinetics, or any first-order process.

</details>

### Chapter project: a decay simulation

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–23. We add a deterministic ODE solver to simulate particle decay over time, complementing the Monte Carlo generator (Chapter 22).

**Goal.** Simulate a two-species decay chain (A → B → stable) with RK4, printing the populations over time.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v20 — decay chain ===\n";
    // A --lambdaA--> B --lambdaB--> stable
    const double lA = 0.20, lB = 0.10;
    double A = 1000.0, B = 0.0;
    const double h = 0.01;

    std::cout << std::format("{:>5} {:>10} {:>10}\n", "t", "N_A", "N_B");
    for (double t = 0.0; t <= 10.0 + 1e-9; t += h) {
        if (std::fabs(t - std::round(t)) < 1e-9)          // print at integer times
            std::cout << std::format("{:5.0f} {:10.2f} {:10.2f}\n", t, A, B);
        // RK4 for the coupled system dA/dt=-lA*A, dB/dt=lA*A-lB*B
        double a1 = -lA*A,           b1 = lA*A - lB*B;
        double a2 = -lA*(A+h/2*a1),  b2 = lA*(A+h/2*a1) - lB*(B+h/2*b1);
        double a3 = -lA*(A+h/2*a2),  b3 = lA*(A+h/2*a2) - lB*(B+h/2*b2);
        double a4 = -lA*(A+h*a3),    b4 = lA*(A+h*a3)   - lB*(B+h*b3);
        A += h/6*(a1+2*a2+2*a3+a4);
        B += h/6*(b1+2*b2+2*b3+b4);
    }
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v20 — decay chain ===
    t        N_A        N_B
    0    1000.00       0.00
    1     818.73     172.21
    2     670.32     296.82
    3     548.81     384.01
    4     449.33     441.98
    5     367.88     477.30
    6     301.19     495.23
    7     246.60     499.98
    8     201.90     494.86
    9     165.30     482.54
   10     135.34     465.09
```

**Commentary.**
- This solves a **coupled ODE system** — a two-step decay chain A → B → stable — with RK4 applied to both species simultaneously (the `a`/`b` RK4 stages are computed together because dB/dt depends on A). This is exactly the Bateman-equation physics of radioactive decay chains and reaction networks.
- N_A decays exponentially (818.73, 670.32, … ≈ 1000·e^(−0.2t)); N_B *rises then falls* — it's fed by A's decay but drains via its own, peaking around t ≈ 7 (N_B ≈ 500) when production and decay balance. That characteristic "grow then decay" curve of a daughter isotope is captured precisely.
- Combined with Chapter 22's Monte Carlo generator, the toolkit now has *both* stochastic (event-by-event) and deterministic (population-level) simulation — the two complementary modes of computational physics.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Root-finding** | Solving f(x) = 0. |
| **Bisection** | Halving a sign-changing interval (robust, linear). |
| **Newton–Raphson** | `x ← x − f/f′` (fast, needs the derivative). |
| **Quadrature** | Numerical integration (trapezoidal, Simpson). |
| **RK4** | Fourth-order Runge–Kutta ODE solver. |
| **Truncation / rounding error** | From approximating the operation / floating-point. |
| **Order of accuracy** | How error scales with step size `h` (hᵖ). |
| **Stability** | Whether numerical errors grow over the computation. |

### What's next

You can solve equations numerically. Much of that computation is **linear algebra** — matrices and vectors. **[Ch.24 — Linear Algebra & Matrices](#chapter-24--linear-algebra--matrices)** builds a `Matrix` type and surveys the high-performance libraries (Eigen, BLAS/LAPACK) that power real scientific computing.

[↑ back to top](#chapter-23--numerical-algorithms)


---

## Chapter 24 — Linear Algebra & Matrices

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.17 — Operator Overloading](#chapter-17--operator-overloading), [Ch.18 — Containers](#chapter-18--stl-containers)

**Learning objectives** — after this chapter you will be able to:

- Build a matrix type over contiguous storage.
- Implement matrix operations (multiply, transpose) with natural operators.
- Understand solving linear systems.
- Know when to use Eigen / BLAS / LAPACK instead of rolling your own.

**In this chapter**

- [24.1 A matrix type](#241-a-matrix-type)
- [24.2 Matrix operations](#242-matrix-operations)
- [24.3 Solving linear systems](#243-solving-linear-systems)
- [24.4 Don't roll your own: Eigen, BLAS, LAPACK](#244-dont-roll-your-own-eigen-blas-lapack)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-rotation-matrix)· Glossary · What's next

---

### 24.1 A matrix type

Linear algebra — matrices and vectors — underlies most scientific computing: transformations, systems of equations, least-squares fits, covariance matrices, quantum states. A matrix should be stored as a **flat, contiguous `std::vector`** in row-major order (Chapter 18), *not* a vector-of-vectors (which scatters rows across the heap). We index it with `operator()(i, j)` (Chapter 17) — `[i][j]` can't take two indices cleanly, so `(i, j)` is the C++ convention:

```cpp
class Matrix {
    std::size_t rows_, cols_;
    std::vector<double> data_;                 // flat, contiguous
public:
    Matrix(std::size_t r, std::size_t c) : rows_(r), cols_(c), data_(r*c, 0.0) {}
    double&       operator()(std::size_t i, std::size_t j)       { return data_[i*cols_ + j]; }
    double        operator()(std::size_t i, std::size_t j) const { return data_[i*cols_ + j]; }
    std::size_t rows() const { return rows_; }
    std::size_t cols() const { return cols_; }
};
// m(i, j) accesses element (row i, col j)
```

The `i*cols_ + j` maps 2-D indices to the flat buffer. Row-major means a *row* is contiguous — so iterating along rows is cache-friendly (Chapter 33), and the data can be handed directly to BLAS.

### 24.2 Matrix operations

Overload operators (Chapter 17) so matrix code reads like the math. Multiplication is the classic triple loop:

```cpp
Matrix operator*(const Matrix& b) const {
    if (cols_ != b.rows_) throw std::invalid_argument("dimension mismatch");   // validate!
    Matrix r(rows_, b.cols_);
    for (std::size_t i = 0; i < rows_; ++i)
        for (std::size_t j = 0; j < b.cols_; ++j) {
            double s = 0.0;
            for (std::size_t k = 0; k < cols_; ++k) s += (*this)(i,k) * b(k,j);
            r(i,j) = s;
        }
    return r;
}
```

With `A` = [[1,2,3],[4,5,6]] (2×3) and `B` = [[7,8],[9,10],[11,12]] (3×2), `A * B` is:

```text
  58.0   64.0
 139.0  154.0
```

`transpose()` flips rows and columns similarly. Note the dimension **validation** (throwing on mismatch, Chapter 21) — a linear-algebra type must guard its invariants, since a dimension bug produces silent garbage.

> ⚠️ **Gotcha — the naive matrix multiply is slow.** That triple loop is O(n³) *and* cache-unfriendly for large matrices: the inner loop over `k` strides through `b` *column-wise* (jumping `cols_` elements each step), thrashing the cache. Real implementations use **loop reordering** (ikj order), **blocking/tiling**, and **SIMD** (Chapter 33) to get 10–100× speedups. For anything beyond small matrices, *don't* write your own multiply — call an optimized library (§24.4). This hand-rolled version is for understanding, not production.

### 24.3 Solving linear systems

Solving `Ax = b` (a system of linear equations) is ubiquitous — fitting, circuit analysis, PDE discretization. The standard method is **Gaussian elimination** (LU decomposition): reduce `A` to triangular form, then back-substitute. It's O(n³), and a careful implementation uses **pivoting** for numerical stability (swapping rows to avoid dividing by small numbers — catastrophic cancellation, Chapter 3).

Writing a correct, stable, fast solver is genuinely hard (pivoting, conditioning, special structure). For anything real, you use a library — which brings us to the key lesson of this chapter.

### 24.4 Don't roll your own: Eigen, BLAS, LAPACK

Numerical linear algebra is a *solved problem* — decades of expert effort live in libraries you should use:

- **BLAS** (Basic Linear Algebra Subprograms) — the low-level standard for vector/matrix operations (`dgemm` for matrix multiply). Highly optimized implementations (OpenBLAS, Intel MKL) approach hardware peak performance with SIMD, blocking, and multithreading.
- **LAPACK** — solvers built on BLAS: linear systems, eigenvalues, SVD, least squares.
- **Eigen** — a modern, header-only C++ template library with natural syntax (`C = A * B`), expression templates (Chapter 31) that fuse operations, and optional BLAS/LAPACK backends. The go-to for C++ linear algebra.

```cpp
// With Eigen (illustrative — not compiled here):
#include <Eigen/Dense>
Eigen::MatrixXd A(3,3), B(3,3);
Eigen::MatrixXd C = A * B;                    // optimized, fused, SIMD
Eigen::VectorXd x = A.colPivHouseholderQr().solve(b);   // stable linear solve
```

> 💡 **Idiom** — **For real linear algebra, use Eigen (or a BLAS/LAPACK wrapper) — never your own matrix multiply or solver.** A hand-rolled multiply is 10–100× slower than OpenBLAS's `dgemm`, and a hand-rolled solver risks instability without proper pivoting. Eigen gives you natural syntax *and* near-optimal performance (expression templates eliminate temporaries, SIMD vectorizes the kernels). Write your own `Matrix` only to *understand* the mechanics (as here) or for tiny fixed-size matrices where a library's generality is overkill. Knowing what to delegate is expert judgment — and in numerical linear algebra, you delegate to Eigen/BLAS.

---

### Summary

- Store a matrix as a **flat, contiguous `std::vector`** (row-major), indexed with **`operator()(i, j)`** (`i*cols + j`) — *not* a vector-of-vectors.
- Overload operators for natural syntax (`A * B`, `A.transpose()`); **validate dimensions** (throw on mismatch).
- Solving `Ax = b` uses **Gaussian elimination / LU** with **pivoting** for stability — genuinely hard to do well.
- **Don't roll your own** for real work: use **Eigen** (header-only, natural syntax, expression templates) or **BLAS/LAPACK** (peak performance). A hand multiply/solver is far slower and riskier. Write your own only to learn or for tiny fixed sizes.

### Self-check quiz

1. Why store a matrix as a flat `vector`, not a vector-of-vectors?
   <details><summary>Answer</summary>A flat vector is contiguous (cache-friendly, BLAS-compatible); a vector-of-vectors scatters rows across separate heap allocations, hurting performance.</details>
2. Why use `operator()(i, j)` for indexing instead of `[i][j]`?
   <details><summary>Answer</summary>`operator[]` takes a single index; `operator()` can take two (row, col), mapping to the flat buffer as `i*cols + j` — the C++ convention for 2-D access.</details>
3. Why is the naive triple-loop matrix multiply slow for large matrices?
   <details><summary>Answer</summary>It's O(n³) and cache-unfriendly (the inner loop strides column-wise through the second matrix). Optimized libraries use loop reordering, blocking, and SIMD for 10–100× speedups.</details>
4. Why use Eigen/BLAS instead of your own linear algebra?
   <details><summary>Answer</summary>They're vastly faster (optimized kernels, SIMD, blocking) and numerically robust (proper pivoting). A hand-rolled multiply/solver is slow and error-prone; delegate to the experts' libraries.</details>

### Exercises

**Exercise 24.1 — Matrix–vector product (guided).** Add a method multiplying a `Matrix` by a `std::vector<double>` (as a column vector).

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
class Matrix {
    std::size_t rows_, cols_;
    std::vector<double> data_;
public:
    Matrix(std::size_t r, std::size_t c) : rows_(r), cols_(c), data_(r*c, 0.0) {}
    double& operator()(std::size_t i, std::size_t j) { return data_[i*cols_+j]; }
    double  operator()(std::size_t i, std::size_t j) const { return data_[i*cols_+j]; }
    std::vector<double> operator*(const std::vector<double>& v) const {
        std::vector<double> r(rows_, 0.0);
        for (std::size_t i = 0; i < rows_; ++i)
            for (std::size_t j = 0; j < cols_; ++j) r[i] += (*this)(i,j) * v[j];
        return r;
    }
};
int main() {
    Matrix m(2, 2);
    m(0,0)=1; m(0,1)=2; m(1,0)=3; m(1,1)=4;
    auto r = m * std::vector<double>{5.0, 6.0};   // [1*5+2*6, 3*5+4*6]
    std::cout << std::format("{} {}\n", r[0], r[1]);   // 17 39
}
```

Output:
```text
17 39
```

**Why this works:** the matrix–vector product `r[i] = Σⱼ M(i,j)·v[j]` gives `[1·5+2·6, 3·5+4·6] = [17, 39]`. This is the core operation of applying a linear transformation (a rotation, a basis change) to a vector.

</details>

**Exercise 24.2 — Trace.** Add a `trace()` returning the sum of the diagonal of a square matrix.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
class Matrix {
    std::size_t n_;
    std::vector<double> data_;
public:
    explicit Matrix(std::size_t n) : n_(n), data_(n*n, 0.0) {}
    double& operator()(std::size_t i, std::size_t j) { return data_[i*n_+j]; }
    double  operator()(std::size_t i, std::size_t j) const { return data_[i*n_+j]; }
    double trace() const { double t=0; for (std::size_t i=0;i<n_;++i) t += (*this)(i,i); return t; }
};
int main() {
    Matrix m(3);
    m(0,0)=2; m(1,1)=5; m(2,2)=9;
    std::cout << std::format("trace = {}\n", m.trace());   // 16
}
```

Output:
```text
trace = 16
```

**Why this works:** the trace sums the diagonal elements `M(i,i)`: 2+5+9 = 16. The trace is invariant under basis change and equals the sum of eigenvalues — a fundamental quantity in physics (e.g. the trace of a density matrix is 1).

</details>

### Chapter project: a rotation matrix

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–24. Coordinate rotations are everywhere in physics (detector alignment, boosts, frame transforms). We build a 2-D rotation and apply it to a momentum vector.

**Goal.** A `Matrix` holding a 2-D rotation by angle θ, applied to a vector via matrix–vector multiply.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <cmath>
#include <numbers>

class Matrix {
    std::size_t rows_, cols_;
    std::vector<double> data_;
public:
    Matrix(std::size_t r, std::size_t c) : rows_(r), cols_(c), data_(r*c, 0.0) {}
    double& operator()(std::size_t i, std::size_t j) { return data_[i*cols_+j]; }
    double  operator()(std::size_t i, std::size_t j) const { return data_[i*cols_+j]; }
    std::vector<double> operator*(const std::vector<double>& v) const {
        std::vector<double> r(rows_, 0.0);
        for (std::size_t i = 0; i < rows_; ++i)
            for (std::size_t j = 0; j < cols_; ++j) r[i] += (*this)(i,j) * v[j];
        return r;
    }
};

Matrix rotation2d(double theta) {
    Matrix R(2, 2);
    R(0,0) = std::cos(theta);  R(0,1) = -std::sin(theta);
    R(1,0) = std::sin(theta);  R(1,1) =  std::cos(theta);
    return R;
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v21 — coordinate rotation ===\n";
    Matrix R = rotation2d(std::numbers::pi / 2);      // rotate 90 degrees
    std::vector<double> p = {1.0, 0.0};               // momentum along +x
    auto rotated = R * p;
    std::cout << std::format("p       = ({:.3f}, {:.3f})\n", p[0], p[1]);
    std::cout << std::format("R(90) p = ({:.3f}, {:.3f})\n", rotated[0], rotated[1]);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v21 — coordinate rotation ===
p       = (1.000, 0.000)
R(90) p = (0.000, 1.000)
```

**Commentary.**
- The 2-D rotation matrix `[[cos θ, −sin θ], [sin θ, cos θ]]` applied to `(1, 0)` at θ = 90° gives `(0, 1)` — the +x direction rotated to +y, exactly as expected. (The `0.000` is really ~6×10⁻¹⁷ — cos(π/2) isn't exactly 0 in floating point, Chapter 3 — but rounds to zero at this precision.)
- This uses the `Matrix` type (flat storage, `operator()`) and the matrix–vector product from Exercise 24.1 — reading like the physics: `R * p`.
- Coordinate transforms like this (and their 3-D and Lorentz-boost generalizations) are constant in physics analysis: aligning detector frames, boosting to a particle's rest frame, transforming momenta. For production you'd use Eigen's `Rotation2D`/`Matrix2d` (§24.4) — natural syntax *and* SIMD speed — but the mechanics are exactly what we built here.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Row-major flat storage** | A matrix as a contiguous `vector` (`i*cols+j`). |
| **`operator()(i, j)`** | The 2-D indexing convention for matrices. |
| **Matrix multiply** | O(n³) triple loop; slow naively, fast in BLAS. |
| **Gaussian elimination / LU** | Solving `Ax = b` (with pivoting for stability). |
| **BLAS / LAPACK** | Optimized low-level / higher-level linear algebra libraries. |
| **Eigen** | A modern header-only C++ linear-algebra library. |
| **Trace** | Sum of a square matrix's diagonal. |

### What's next

Matrices are 2-D data. **[Ch.25 — Multidimensional Data & Layout](#chapter-25--multidimensional-data--layout)** generalizes this: memory layouts (row- vs column-major, SoA vs AoS), the C++23 `mdspan` view, and how data layout drives performance in scientific code.

[↑ back to top](#chapter-24--linear-algebra--matrices)


---

## Chapter 25 — Multidimensional Data & Layout

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.18 — Containers](#chapter-18--stl-containers), [Ch.24 — Linear Algebra](#chapter-24--linear-algebra--matrices)

**Learning objectives** — after this chapter you will be able to:

- Choose a memory layout (row- vs column-major) and index it.
- Understand `mdspan`-style multidimensional views.
- Weigh AoS vs SoA layouts and their performance impact.

**In this chapter**

- [25.1 Row-major vs column-major](#251-row-major-vs-column-major)
- [25.2 Multidimensional views (`mdspan`)](#252-multidimensional-views-mdspan)
- [25.3 AoS vs SoA](#253-aos-vs-soa)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-2-d-field-view)· Glossary · What's next

---

### 25.1 Row-major vs column-major

Multidimensional data (matrices, images, fields, tensors) is stored in *linear* memory, so a **layout** maps N-D indices to a 1-D offset. The two conventions:

- **Row-major** (C, C++): a *row* is contiguous. Element `(i, j)` of an `r×c` array is at `i*cols + j`. Iterating a row walks memory sequentially.
- **Column-major** (Fortran, BLAS/LAPACK, MATLAB): a *column* is contiguous. Element `(i, j)` is at `j*rows + i`.

The choice matters for two reasons: **cache performance** (iterate along the contiguous dimension — Chapter 33) and **interop** (BLAS/LAPACK expect column-major, so C++ code passing to them either transposes or uses column-major storage). Pick a convention, document it, and iterate the contiguous dimension in the innermost loop.

> 💡 **Idiom** — Use **row-major** in C++ (it's the language's native array layout and what most C++ libraries expect) and always loop with the **last index innermost** (`for i: for j: a(i,j)`) so you stride contiguously. When calling **BLAS/LAPACK** (column-major), either store column-major, pass a "transpose" flag, or use a library (Eigen) that handles the convention. A layout mismatch silently transposes your data or tanks performance — know which convention every buffer uses.

### 25.2 Multidimensional views (`mdspan`)

Manually writing `data[i*cols + j]` everywhere is error-prone. C++23's **`std::mdspan`** is a *non-owning multidimensional view* over flat storage — you write `grid(i, j)` and it does the index math, with configurable layout and extents. (GCC 13 doesn't ship it yet, so here's a minimal stand-in showing the idea:)

```cpp
class MdView {                                   // a tiny 2D mdspan-like view
    double* data_; std::size_t rows_, cols_;
public:
    MdView(double* d, std::size_t r, std::size_t c) : data_(d), rows_(r), cols_(c) {}
    double& operator()(std::size_t i, std::size_t j) { return data_[i*cols_ + j]; }
};

std::vector<double> flat(6, 0.0);                // owns the memory
MdView grid(flat.data(), 2, 3);                  // views it as 2×3
grid(1, 2) = 42.0;                               // grid(1,2) → flat[1*3+2] = flat[5]
// flat[5] is now 42
```

`std::mdspan` (C++23) generalizes this to any rank, with `std::layout_right` (row-major), `std::layout_left` (column-major), and even strided/custom layouts — separating the *data* (a flat `vector`) from the *view* of its shape. It's the standard, zero-overhead way to treat flat memory as multidimensional.

> 💡 **Idiom** — Store multidimensional data as **one flat `std::vector` (owning)** and view it through an **`mdspan` (or wrapper)** for indexing. This keeps data contiguous (cache-friendly, BLAS-ready) while giving clean `a(i, j, k)` syntax — the best of both worlds. Never use `vector<vector<vector<double>>>` for a 3-D field: it's non-contiguous, cache-hostile, and slow. When GCC ships `<mdspan>`, use it; until then, a small wrapper (as above) does the job.

### 25.3 AoS vs SoA

How you group *records* also shapes performance. Consider a million particles, each with `px, py, pz, E`:

- **Array of Structs (AoS)** — `std::vector<Particle>` where `struct Particle { double px, py, pz, E; };`. Natural and object-oriented, but if you only need `E` for all particles, you load `px, py, pz` into cache too (wasted bandwidth) since each particle's fields are interleaved.
- **Struct of Arrays (SoA)** — `struct { vector<double> px, py, pz, E; };`. Each field is its own contiguous array. Iterating just `E` reads *only* `E` — perfect cache use and **SIMD**-friendly (the compiler can vectorize a loop over a contiguous `double` array).

```cpp
struct ParticleAoS  { double px, py, pz, E; };            // AoS: fields interleaved
struct ParticlesSoA { std::vector<double> px, py, pz, E; }; // SoA: fields separate

ParticlesSoA soa{{1,2}, {0,0}, {0,0}, {10.0, 20.0}};
double total = 0; for (double e : soa.E) total += e;      // reads only E → 30
```

> ⚙️ **Under the hood** — In a hot loop that touches *one* field of many records, **SoA** dramatically outperforms AoS: it reads only the needed data (no wasted cache lines) and lets the compiler **auto-vectorize** (SIMD, Chapter 33) — one instruction processing 4–8 doubles at once. AoS is more convenient and fine when you use *all* fields of each record together. High-performance physics codes (and GPU kernels) often use SoA for exactly this reason — it's a layout decision worth billions of cycles in a simulation. The trade-off is ergonomics: AoS reads more naturally (`p.E`), SoA needs parallel-array bookkeeping.

---

### Summary

- **Layout** maps N-D indices to linear memory: **row-major** (C++, `i*cols+j`, rows contiguous) vs **column-major** (Fortran/BLAS, columns contiguous). Iterate the **contiguous dimension innermost** for cache performance.
- **`std::mdspan`** (C++23) is a non-owning multidimensional view over flat storage (`grid(i, j)`); use a flat `vector` + a view, never nested vectors.
- **AoS** (`vector<Particle>`) is natural but wastes bandwidth when you touch one field; **SoA** (`struct { vector<double> px, ...; }`) reads only needed data and **auto-vectorizes** — much faster in field-at-a-time hot loops.

### Self-check quiz

1. What's the difference between row-major and column-major?
   <details><summary>Answer</summary>Row-major (C++) stores rows contiguously — `(i,j)` at `i*cols+j`; column-major (Fortran/BLAS) stores columns contiguously — `(i,j)` at `j*rows+i`. Iterate the contiguous dimension innermost.</details>
2. Why store multidimensional data as a flat vector + view, not nested vectors?
   <details><summary>Answer</summary>A flat vector is contiguous (cache-friendly, BLAS-compatible); nested vectors scatter data across separate heap allocations, ruining performance. A view (`mdspan`) gives clean indexing over the flat storage.</details>
3. When does SoA beat AoS?
   <details><summary>Answer</summary>In hot loops that touch one (or few) fields across many records: SoA reads only needed data (no wasted cache) and auto-vectorizes. AoS is fine when you use all fields of each record together.</details>

### Exercises

**Exercise 25.1 — 2D indexing (guided).** Store a 3×3 grid flat, set the diagonal to 1, and print it via a view.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
class View2D {
    double* d_; std::size_t n_;
public:
    View2D(double* d, std::size_t n) : d_(d), n_(n) {}
    double& operator()(std::size_t i, std::size_t j) { return d_[i*n_ + j]; }
};
int main() {
    std::vector<double> flat(9, 0.0);
    View2D g(flat.data(), 3);
    for (std::size_t i = 0; i < 3; ++i) g(i, i) = 1.0;   // identity diagonal
    for (std::size_t i = 0; i < 3; ++i) {
        for (std::size_t j = 0; j < 3; ++j) std::cout << std::format("{:.0f} ", g(i,j));
        std::cout << "\n";
    }
}
```

Output:
```text
1 0 0
0 1 0
0 0 1
```

**Why this works:** the flat `vector` owns 9 doubles; `View2D` maps `(i,j)` to `flat[i*3+j]`. Setting `g(i,i)=1` builds the identity matrix, stored contiguously. This is the flat-storage + view pattern `mdspan` formalizes.

</details>

**Exercise 25.2 — SoA sum.** Given a SoA of particle energies, sum them; note it reads only the `E` array.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
struct Particles { std::vector<double> px, py, pz, E; };
int main() {
    Particles p{{1,2,3}, {0,0,0}, {0,0,0}, {10.0, 20.0, 30.0}};
    double totalE = 0;
    for (double e : p.E) totalE += e;       // touches ONLY the contiguous E array
    std::cout << std::format("total E = {}\n", totalE);   // 60
}
```

Output:
```text
total E = 60
```

**Why this works:** with SoA, `p.E` is its own contiguous array, so summing it reads *only* energies (10+20+30=60) — no wasted loading of `px/py/pz`, and the loop auto-vectorizes. In AoS (`vector<Particle>`), the same sum would drag the other fields through cache.

</details>

### Chapter project: a 2-D field view

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–25. A detector often reads out a 2-D grid of cells (a calorimeter tower map). We store it flat and view it as 2-D, computing the total and the hottest cell.

**Goal.** A flat-stored 2-D calorimeter grid with an `mdspan`-style view, filled and summarized.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>

class Grid2D {
    std::vector<double> data_;
    std::size_t rows_, cols_;
public:
    Grid2D(std::size_t r, std::size_t c) : data_(r*c, 0.0), rows_(r), cols_(c) {}
    double& operator()(std::size_t i, std::size_t j) { return data_[i*cols_ + j]; }
    double  operator()(std::size_t i, std::size_t j) const { return data_[i*cols_ + j]; }
    std::size_t rows() const { return rows_; }
    std::size_t cols() const { return cols_; }
    double total() const { double s=0; for (double x : data_) s += x; return s; }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v22 — calorimeter grid ===\n";
    Grid2D calo(3, 4);                              // 3x4 tower map, flat storage
    calo(1, 2) = 85.0;                              // an energy deposit
    calo(1, 1) = 30.0;
    calo(2, 3) = 12.5;

    // find the hottest cell
    std::size_t hi_i = 0, hi_j = 0; double hi_e = calo(0,0);
    for (std::size_t i = 0; i < calo.rows(); ++i)
        for (std::size_t j = 0; j < calo.cols(); ++j)
            if (calo(i,j) > hi_e) { hi_e = calo(i,j); hi_i = i; hi_j = j; }

    for (std::size_t i = 0; i < calo.rows(); ++i) {
        for (std::size_t j = 0; j < calo.cols(); ++j) std::cout << std::format("{:6.1f}", calo(i,j));
        std::cout << "\n";
    }
    std::cout << std::format("total = {:.1f} GeV, hottest cell ({},{}) = {:.1f} GeV\n",
                             calo.total(), hi_i, hi_j, hi_e);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v22 — calorimeter grid ===
   0.0   0.0   0.0   0.0
   0.0  30.0  85.0   0.0
   0.0   0.0   0.0  12.5
total = 127.5 GeV, hottest cell (1,2) = 85.0 GeV
```

**Commentary.**
- The calorimeter is a `3×4` grid stored as **one flat `std::vector`** (contiguous — cache-friendly, BLAS-ready), viewed as 2-D through `operator()(i, j)`. This is exactly the `mdspan` pattern from §25.2, and how real detector readouts are laid out.
- `total()` sums the whole flat buffer in one contiguous pass; the nested loop finds the hottest cell — the "seed" of a calorimeter cluster in a real analysis. The deposits (85 + 30 + 12.5 = 127.5 GeV) and the hottest cell (1,2) are found by walking the grid.
- Storing flat + viewing 2-D (rather than `vector<vector<double>>`) keeps the data contiguous — essential when a real event has thousands of cells and the analysis runs millions of events. Layout *is* performance in scientific computing.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Row-major / column-major** | Rows / columns stored contiguously. |
| **`std::mdspan`** | A non-owning multidimensional view over flat storage (C++23). |
| **`layout_right` / `layout_left`** | Row-major / column-major mdspan layouts. |
| **AoS (Array of Structs)** | `vector<Record>` — fields interleaved. |
| **SoA (Struct of Arrays)** | Separate contiguous array per field. |
| **Auto-vectorization** | The compiler using SIMD on a contiguous loop. |

### What's next

Layout drives runtime performance; the next chapter moves work to *compile time*. **[Ch.26 — `constexpr` & Compile-Time Computation](#chapter-26--constexpr--compile-time-computation)** shows how to compute constants, tables, and even algorithms during compilation — zero runtime cost, with results baked into the binary.

[↑ back to top](#chapter-25--multidimensional-data--layout)


---

## Chapter 26 — `constexpr` & Compile-Time Computation

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.6 — Functions](#chapter-6--functions-i-parameters-overloading--performance), [Ch.16 — Templates](#chapter-16--templates)

**Learning objectives** — after this chapter you will be able to:

- Compute constants, tables, and algorithms at compile time.
- Distinguish `constexpr`, `consteval`, and `constinit`.
- Use `static_assert` for compile-time checks.

**In this chapter**

- [26.1 `constexpr` computation](#261-constexpr-computation)
- [26.2 Compile-time tables](#262-compile-time-tables)
- [26.3 `consteval` and `static_assert`](#263-consteval-and-static_assert)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-compile-time-physics-constants)· Glossary · What's next

---

### 26.1 `constexpr` computation

`constexpr` (Chapters 2, 6) means "computable at compile time." A `constexpr` function, called with compile-time arguments, runs *during compilation* — its result is baked into the binary as a literal, with **zero runtime cost**. Since C++14, `constexpr` functions can contain loops, branches, and local variables — nearly the full language:

```cpp
constexpr long factorial(int n) { return n <= 1 ? 1 : n * factorial(n - 1); }

constexpr long f5 = factorial(5);   // computed at COMPILE time → 120 baked into the binary
long runtime_n = 5;
long f = factorial(runtime_n);      // same function, called at RUNTIME (runtime arg)
```

The same `constexpr` function works in *both* contexts: compile-time when given constant arguments, runtime otherwise. This lets you write one implementation and get compile-time evaluation for free where inputs are known. Scientific uses: derived physical constants, unit conversions, precomputed coefficients.

### 26.2 Compile-time tables

The killer application: **precompute lookup tables at compile time**. A table of factorials, trig values, or physics coefficients can be built during compilation (using a `constexpr` function returning a `std::array`), so the running program just *reads* it — no startup computation, no runtime cost:

```cpp
constexpr std::array<long, 10> make_factorials() {
    std::array<long, 10> t{};
    for (int i = 0; i < 10; ++i) t[i] = factorial(i);   // loop in a constexpr function
    return t;
}

constexpr auto facs = make_factorials();   // the whole table built at COMPILE time
// facs[5] → 120,  facs[9] → 362880   (just array reads at runtime)
```

`std::array` (and, in C++20, even `std::vector` and many algorithms) can be used in `constexpr` context, so quite elaborate tables and precomputations move to compile time. The binary ships with the answers.

> 💡 **Idiom** — Move **fixed computations to compile time with `constexpr`** — physical constants derived from others, unit-conversion factors, lookup tables (Gaussian weights, spline coefficients, CORDIC tables). The result costs nothing at runtime (it's a literal or a static array), can't be miscomputed at startup, and documents that the value is fixed. If a quantity is known at compile time, *compute it at compile time*. This is a real speedup for programs that would otherwise build tables during initialization.

### 26.3 `consteval` and `static_assert`

Three related tools sharpen compile-time programming:

- **`consteval`** — an *immediate* function that **must** run at compile time (it's an error to call it with runtime arguments). Use it when compile-time evaluation is *required*, not just allowed:

```cpp
consteval int square(int x) { return x * x; }
constexpr int s = square(7);   // OK → 49 at compile time
// int r = square(runtime_x);  // ERROR: consteval needs a constant argument
```

- **`static_assert`** — a **compile-time assertion**: if the condition is false, compilation *fails* with your message. Perfect for validating `constexpr` results, type properties, and invariants that must hold at build time:

```cpp
static_assert(factorial(5) == 120);              // checked during compilation
static_assert(sizeof(double) == 8, "need 64-bit double");
```

- **`constinit`** — guarantees a variable is initialized at compile time (avoiding the "static initialization order fiasco"), while allowing later mutation (unlike `constexpr`, which is also `const`).

> ⚙️ **Under the hood** — When the compiler evaluates a `constexpr`/`consteval` call, it runs a full interpreter *at compile time* over your code — allocating (in C++20, even `constexpr` `new`/`delete` within an evaluation), looping, branching — then emits only the *result* into the binary. `static_assert` runs a condition through that same evaluator and halts the build on failure. This "compile-time computation" is Turing-complete and increasingly powerful each standard; it's how libraries validate types, generate tables, and catch errors *before the program ever runs* — the earliest, cheapest place to catch a bug.

---

### Summary

- **`constexpr`** functions run at **compile time** when given constant arguments (zero runtime cost), and at runtime otherwise — one implementation, both contexts. C++14+ allows loops/branches; C++20 allows `constexpr` containers/algorithms.
- **Compile-time tables**: a `constexpr` function returning a `std::array` builds lookup tables *during compilation*, so the program just reads them.
- **`consteval`** forces compile-time evaluation; **`static_assert`** fails the build on a false condition (validating results/types); **`constinit`** guarantees compile-time initialization.
- Move fixed computations (constants, conversions, tables) to compile time — free at runtime, and validated early.

### Self-check quiz

1. What's the difference between `constexpr` and `consteval`?
   <details><summary>Answer</summary>`constexpr` *can* run at compile time (and at runtime otherwise); `consteval` *must* run at compile time — calling it with a runtime argument is an error.</details>
2. How do you build a lookup table at compile time?
   <details><summary>Answer</summary>Write a `constexpr` function that fills and returns a `std::array`, and assign it to a `constexpr` variable — the whole table is computed during compilation.</details>
3. What does `static_assert` do?
   <details><summary>Answer</summary>Checks a condition at compile time; if false, compilation fails with your message — for validating constexpr results, type properties, and build-time invariants.</details>
4. Why move fixed computations to compile time?
   <details><summary>Answer</summary>Zero runtime cost (baked into the binary), no startup computation, and the value is validated/fixed at build time — errors caught before the program runs.</details>

### Exercises

**Exercise 26.1 — Compile-time power (guided).** Write a `constexpr` `ipow(base, exp)` and verify with `static_assert`.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
constexpr long ipow(long base, int exp) {
    long r = 1; for (int i = 0; i < exp; ++i) r *= base; return r;
}
int main() {
    static_assert(ipow(2, 10) == 1024);          // checked at compile time
    constexpr long k = ipow(3, 4);               // computed at compile time → 81
    std::cout << k << "\n";
}
```

Output:
```text
81
```

**Why this works:** `ipow` is `constexpr`, so `ipow(2,10)` and `ipow(3,4)` evaluate during compilation. `static_assert` verifies `2¹⁰ = 1024` at build time (a wrong value would fail compilation); `k` is the literal `81` baked into the binary.

</details>

**Exercise 26.2 — Compile-time table.** Build a compile-time table of the first 8 powers of 2 and read from it.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <array>
constexpr std::array<long, 8> powers_of_two() {
    std::array<long, 8> t{};
    long v = 1;
    for (int i = 0; i < 8; ++i) { t[i] = v; v *= 2; }
    return t;
}
int main() {
    constexpr auto p2 = powers_of_two();          // table built at compile time
    static_assert(p2[7] == 128);
    std::cout << std::format("2^3={} 2^7={}\n", p2[3], p2[7]);   // 8 128
}
```

Output:
```text
2^3=8 2^7=128
```

**Why this works:** `powers_of_two()` fills a `std::array` in a loop, all at compile time. `p2` is a `constexpr` array — the program reads `p2[3]=8`, `p2[7]=128` with no computation. `static_assert` confirms `2⁷=128` during the build.

</details>

### Chapter project: compile-time physics constants

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–26. Physics constants and derived quantities are fixed — so compute them at compile time. We build a `constexpr` constants module and a derived-quantity table.

**Goal.** `constexpr` physical constants and a compile-time table of relativistic γ-factors, validated with `static_assert`.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <array>

namespace constants {
    inline constexpr double c        = 299792458.0;        // m/s
    inline constexpr double electron_mass = 0.000510999;   // GeV
    inline constexpr double proton_mass   = 0.938272;      // GeV
    // derived at compile time:
    inline constexpr double c_squared = c * c;
}

// Lorentz gamma factor as a function of beta = v/c
constexpr double gamma_factor(double beta) {
    // constexpr sqrt via Newton's method (std::sqrt isn't constexpr before C++23/26)
    double x = 1.0 - beta * beta;
    double g = x;                                          // initial guess for sqrt(x)
    for (int i = 0; i < 30; ++i) g = 0.5 * (g + x / g);    // Newton for sqrt(x)
    return 1.0 / g;                                        // gamma = 1/sqrt(1-beta^2)
}

// A compile-time table of gamma for beta = 0.0, 0.1, ..., 0.9
constexpr std::array<double, 10> gamma_table() {
    std::array<double, 10> t{};
    for (int i = 0; i < 10; ++i) t[i] = gamma_factor(i * 0.1);
    return t;
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v23 — compile-time constants ===\n";
    constexpr auto gammas = gamma_table();                 // built at COMPILE time
    static_assert(constants::c > 0);                       // build-time sanity checks

    std::cout << std::format("proton mass = {} GeV\n", constants::proton_mass);
    std::cout << std::format("gamma(beta=0.0) = {:.4f}\n", gammas[0]);
    std::cout << std::format("gamma(beta=0.9) = {:.4f}\n", gammas[9]);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v23 — compile-time constants ===
proton mass = 0.938272 GeV
gamma(beta=0.0) = 1.0000
gamma(beta=0.9) = 2.2942
```

**Commentary.**
- The physical constants are **`inline constexpr`** in a namespace — header-safe (Chapter 8), zero-cost (baked in), and const-correct. Derived quantities like `c_squared` are computed at compile time from primitives.
- The **γ-factor table** is built *entirely during compilation* by `gamma_table()`, which even implements `sqrt` via Newton's method (Chapter 23) inside a `constexpr` function (since `std::sqrt` wasn't `constexpr` in older standards). At runtime the program just reads `gammas[i]` — no computation. γ(0)=1 (at rest), γ(0.9)=2.294 (relativistic) — the Lorentz factor every kinematics calculation needs.
- `static_assert` validates constants at build time. This is the idiomatic way to handle the many fixed numbers of physics: **compute once, at compile time, validated** — the toolkit ships with its constants precomputed and checked.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`constexpr`** | Computable at compile time (and runtime otherwise). |
| **`consteval`** | An immediate function that *must* run at compile time. |
| **`constinit`** | Guarantees compile-time initialization (mutable after). |
| **`static_assert`** | A compile-time assertion (fails the build if false). |
| **Compile-time table** | A `constexpr` array built during compilation. |
| **Immediate function** | Another name for `consteval`. |

### What's next

You can compute at compile time. Real programs also read and write *data*. **[Ch.27 — I/O, `std::format` & Scientific Data](#chapter-27--io-stdformat--scientific-data)** covers file streams, binary I/O for large datasets, the filesystem library, and the scientific data-format ecosystem (ROOT, HDF5).

[↑ back to top](#chapter-26--constexpr--compile-time-computation)


---

## Chapter 27 — I/O, `std::format` & Scientific Data

> **Level:** Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — RAII](#chapter-11--dynamic-memory--raii), [Ch.18 — Containers](#chapter-18--stl-containers)

**Learning objectives** — after this chapter you will be able to:

- Read and write text data files with streams.
- Parse structured lines with `stringstream`.
- Use binary I/O for large datasets.
- Know the scientific data-format ecosystem (ROOT, HDF5).

**In this chapter**

- [27.1 File streams](#271-file-streams)
- [27.2 Parsing with `stringstream`](#272-parsing-with-stringstream)
- [27.3 Binary I/O](#273-binary-io)
- [27.4 The filesystem and data formats](#274-the-filesystem-and-data-formats)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-save-and-load-a-dataset)· Glossary · What's next

---

### 27.1 File streams

Files are read and written with **streams** from `<fstream>`: **`std::ofstream`** (output) and **`std::ifstream`** (input). A stream is an **RAII** object (Chapter 11) — it opens the file in its constructor and *closes it in its destructor*, so you never forget to close it:

```cpp
#include <fstream>
{
    std::ofstream out("energies.txt");             // opens the file
    for (double e : {91.1, 91.3, 90.9, 91.2})
        out << std::format("{:.4f}\n", e);         // write formatted lines
}   // out's destructor closes the file (RAII)

std::vector<double> data;
{
    std::ifstream in("energies.txt");              // opens for reading
    double x;
    while (in >> x) data.push_back(x);             // read until end/failure
}
// read 4 values, first = 91.1
```

The `>>` extraction operator reads whitespace-separated values; `while (in >> x)` loops until the stream fails (end of file or a parse error), which is the idiomatic read loop. Use `std::format` (Chapter 1) for the *formatting* and the stream for the *destination*.

> ⚠️ **Gotcha — always check that the file opened.** `std::ifstream in("missing.txt");` doesn't throw if the file is absent — it silently sets a fail state, and reads yield nothing. **Check `if (!in) { /* handle error */ }`** (or `in.is_open()`) before reading, or return a `std::expected` (Chapter 21). A scientific pipeline that silently reads an empty dataset from a mistyped path produces empty results, not an error — a classic waste of a run.

### 27.2 Parsing with `stringstream`

To parse a *line* with mixed types (a name, then numbers), read it into a **`std::istringstream`** and extract fields with `>>` — the same interface as a file stream, but over a string:

```cpp
#include <sstream>
std::string line = "muon 91.19 42";
std::istringstream iss(line);
std::string name; double mass; int hits;
iss >> name >> mass >> hits;
// name = "muon", mass = 91.19, hits = 42
```

`stringstream` is the standard tool for parsing structured text (a CSV row, a config line, a data record) and for building strings piecewise. Combined with `std::getline(file, line)` to read line by line, it handles most scientific text formats.

### 27.3 Binary I/O

Text I/O is human-readable but *large and slow* — a `double` written as text takes ~20 bytes and needs parsing; in **binary** it's exactly 8 bytes, written and read directly. For big datasets (millions of events), binary is essential:

```cpp
// Write: element count, then the raw bytes of the vector
{
    std::ofstream bout("data.bin", std::ios::binary);
    std::size_t n = data.size();
    bout.write(reinterpret_cast<const char*>(&n), sizeof(n));
    bout.write(reinterpret_cast<const char*>(data.data()), n * sizeof(double));
}
// Read it back
std::vector<double> loaded;
{
    std::ifstream bin("data.bin", std::ios::binary);
    std::size_t n;
    bin.read(reinterpret_cast<char*>(&n), sizeof(n));
    loaded.resize(n);
    bin.read(reinterpret_cast<char*>(loaded.data()), n * sizeof(double));
}
// binary round-trip: 4 values, [2] = 90.9
```

`write`/`read` transfer raw bytes; `reinterpret_cast<char*>` views the data as bytes. Because a `std::vector<double>` is *contiguous* (Chapter 18), you can write the whole buffer in one call — fast.

> ⚠️ **Gotcha — binary portability.** Raw binary is *not portable* across machines with different **endianness** or type sizes — a file written on one architecture may read as garbage on another. For data that crosses machines, use a portable format (a defined byte order, or a library like HDF5/ROOT) rather than raw `write`. Also, raw binary of a struct with pointers or a `std::string` is meaningless (it writes the pointer, not the data). Raw binary is great for *contiguous POD arrays* on *one platform* (a fast local cache); for archival/shared data, use a real format.

### 27.4 The filesystem and data formats

**`<filesystem>`** (C++17) handles paths, directories, and file metadata portably:

```cpp
#include <filesystem>
namespace fs = std::filesystem;
fs::exists("data.bin");            // does it exist?
fs::file_size("data.bin");         // size in bytes
for (auto& entry : fs::directory_iterator("."))   // list a directory
    /* entry.path() */;
```

For *real* scientific data, the field uses specialized formats and libraries, not hand-rolled I/O:

- **ROOT** (CERN) — the standard for particle physics: self-describing `TTree`s of events, compression, schema evolution, and analysis tools.
- **HDF5** — a portable, hierarchical format for large numerical datasets (astronomy, climate, ML), with chunking and compression.
- **NetCDF**, **Parquet**, **npy** — domain- and language-specific formats.

> 💡 **Idiom** — For *scratch/cache* data on one machine, raw **binary I/O** of contiguous vectors is fast and simple. For *shared, archival, or cross-language* data, use a **real scientific format** (ROOT in HEP, HDF5 elsewhere) — they handle portability, compression, self-description, and schema evolution that raw binary can't. Hand-rolled text is fine for small config/results a human reads. Match the format to the audience: humans → text, one machine → binary, the world → HDF5/ROOT.

---

### Summary

- **`std::ofstream`/`std::ifstream`** (from `<fstream>`) write/read files; they're **RAII** (auto-close). Read with `while (in >> x)`; format with `std::format`. **Always check the file opened** (`if (!in)`).
- **`std::istringstream`** parses structured lines (`iss >> name >> mass >> hits`); pair with `std::getline` for line-by-line reading.
- **Binary I/O** (`write`/`read` with `reinterpret_cast<char*>`) is compact and fast for large contiguous data — but **not portable** across endianness/architectures.
- **`<filesystem>`** handles paths/directories portably. For real scientific data use **ROOT** (HEP) or **HDF5** (general), not hand-rolled I/O.

### Self-check quiz

1. Why don't you need to close a file stream manually?
   <details><summary>Answer</summary>Streams are RAII objects — their destructor closes the file automatically at scope exit, even on an exception.</details>
2. What's the idiomatic loop to read all values from a file?
   <details><summary>Answer</summary>`while (in >> x) { ... }` — it reads until the stream fails (end of file or parse error). And check `if (!in)` first to confirm the file opened.</details>
3. Why use binary I/O for large datasets, and what's its main pitfall?
   <details><summary>Answer</summary>Binary is compact (8 bytes/double vs ~20 as text) and fast (no parsing). Pitfall: it's not portable across endianness/type-size differences — use a real format for cross-machine data.</details>
4. When use ROOT/HDF5 instead of raw I/O?
   <details><summary>Answer</summary>For shared, archival, or cross-language data — they provide portability, compression, self-description, and schema evolution that raw binary lacks.</details>

### Exercises

**Exercise 27.1 — Write and read (guided).** Write three energies to a file and read them back into a vector.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <fstream>
#include <vector>
int main() {
    { std::ofstream out("e.txt"); for (double e : {91.1, 91.2, 91.3}) out << e << "\n"; }
    std::vector<double> v;
    { std::ifstream in("e.txt");
      if (!in) { std::cerr << "open failed\n"; return 1; }
      double x; while (in >> x) v.push_back(x); }
    std::cout << std::format("read {} values, sum={}\n", v.size(), v[0]+v[1]+v[2]);
}
```

Output:
```text
read 3 values, sum=273.6
```

**Why this works:** the `ofstream` writes each energy on a line (closing the file via RAII at the block's end); the `ifstream` reads them back with `while (in >> x)`, after checking the open succeeded. Three values summing to 273.6.

</details>

**Exercise 27.2 — Parse a record.** Parse the line `"event 42 91.19 GeV"` into an id, a mass, and a unit.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <sstream>
#include <string>
int main() {
    std::string line = "event 42 91.19 GeV";
    std::istringstream iss(line);
    std::string tag, unit; int id; double mass;
    iss >> tag >> id >> mass >> unit;
    std::cout << std::format("id={} mass={} {}\n", id, mass, unit);
}
```

Output:
```text
id=42 mass=91.19 GeV
```

**Why this works:** `istringstream` extracts fields by type in order — `tag` (string), `id` (int), `mass` (double), `unit` (string) — automatically skipping whitespace. This is the standard way to parse a structured data record or config line.

</details>

### Chapter project: save and load a dataset

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–27. Analyses persist results. We give the toolkit's `Dataset` binary save/load — fast, compact round-tripping of event data.

**Goal.** A `Dataset` that saves its energies to a binary file and loads them back, verifying the round-trip.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <fstream>
#include <vector>

class Dataset {
    std::vector<double> energies_;
public:
    void add(double e) { energies_.push_back(e); }
    std::size_t size() const { return energies_.size(); }
    double mean() const {
        if (energies_.empty()) return 0.0;
        double s = 0; for (double e : energies_) s += e; return s / energies_.size();
    }
    bool save(const std::string& path) const {
        std::ofstream out(path, std::ios::binary);
        if (!out) return false;
        std::size_t n = energies_.size();
        out.write(reinterpret_cast<const char*>(&n), sizeof(n));
        out.write(reinterpret_cast<const char*>(energies_.data()), n * sizeof(double));
        return static_cast<bool>(out);
    }
    bool load(const std::string& path) {
        std::ifstream in(path, std::ios::binary);
        if (!in) return false;
        std::size_t n;
        in.read(reinterpret_cast<char*>(&n), sizeof(n));
        energies_.resize(n);
        in.read(reinterpret_cast<char*>(energies_.data()), n * sizeof(double));
        return static_cast<bool>(in);
    }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v24 — persistence ===\n";
    Dataset d;
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) d.add(e);
    if (!d.save("events.bin")) { std::cerr << "save failed\n"; return 1; }

    Dataset reloaded;
    if (!reloaded.load("events.bin")) { std::cerr << "load failed\n"; return 1; }

    std::cout << std::format("saved {} events (mean {:.4f})\n", d.size(), d.mean());
    std::cout << std::format("reloaded {} events (mean {:.4f}) — {}\n",
                             reloaded.size(), reloaded.mean(),
                             (reloaded.size() == d.size()) ? "round-trip OK" : "MISMATCH");
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v24 — persistence ===
saved 5 events (mean 91.1000)
reloaded 5 events (mean 91.1000) — round-trip OK
```

**Commentary.**
- `save`/`load` write and read the energies as **binary** — the count, then the raw contiguous `double`s (Chapter 18) — fast and compact for large event samples. Both **check the file opened** (`if (!out)`/`if (!in)`) and return success/failure, so the caller handles errors (Chapter 21's discipline).
- The round-trip preserves the data exactly: 5 events, mean 91.1 before and after. The streams close via RAII (Chapter 11) — no manual cleanup.
- For a *local cache* of Monte Carlo events this raw binary is ideal. For data shared with collaborators or across machines, the toolkit would write **ROOT** or **HDF5** (§27.4) — but the persistence *interface* (`save`/`load` returning success) stays the same. This completes the toolkit's data lifecycle: generate (Ch.22), analyze (Ch.19), persist (here).

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`ofstream` / `ifstream`** | Output / input file streams (RAII, auto-close). |
| **`while (in >> x)`** | The idiomatic read-until-fail loop. |
| **`istringstream`** | Parses fields from a string by type. |
| **`std::getline`** | Reads a line into a string. |
| **Binary I/O** | `write`/`read` of raw bytes (compact, fast, non-portable). |
| **`<filesystem>`** | Portable paths, directories, metadata (C++17). |
| **ROOT / HDF5** | Scientific data formats (HEP / general). |

### What's next

You can persist data. Real projects also need to *build* — compile many files, link libraries, manage dependencies. **[Ch.28 — Build Systems, CMake & Linking Numerical Libraries](#chapter-28--build-systems-cmake--linking-numerical-libraries)** covers CMake, the de facto C++ build tool, and how to link Eigen, BLAS, ROOT, and friends.

[↑ back to top](#chapter-27--io-stdformat--scientific-data)


---

## Chapter 28 — Build Systems, CMake & Linking Numerical Libraries

> **Level:** Intermediate → Advanced &nbsp;·&nbsp; **Prerequisites:** [Ch.8 — Headers & Build](#chapter-8--headers-translation-units--the-build-model)

**Learning objectives** — after this chapter you will be able to:

- Explain why real projects use a build system.
- Write a `CMakeLists.txt` for an executable and a library.
- Link external numerical libraries (Eigen, BLAS, ROOT).
- Set build types and compiler flags portably.

**In this chapter**

- [28.1 Why a build system](#281-why-a-build-system)
- [28.2 A basic CMake project](#282-a-basic-cmake-project)
- [28.3 Libraries and linking dependencies](#283-libraries-and-linking-dependencies)
- [28.4 Build types, flags, and sanitizers](#284-build-types-flags-and-sanitizers)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-cmake-build-for-the-toolkit)· Glossary · What's next

---

### 28.1 Why a build system

Chapter 8 built a program by hand: `g++ -c` each source, then link. For three files that's fine; for a real project — dozens of sources, several libraries, multiple platforms, debug *and* optimized builds — hand-typing compile commands is unworkable. A **build system** automates it: it tracks which files changed (rebuilding only those), resolves dependencies, finds and links libraries, and generates the right commands for your platform and compiler.

**CMake** is the de facto standard for C++. It's a *meta*-build system: you describe your project in `CMakeLists.txt` (declaratively — targets and their dependencies), and CMake **generates** the actual build files (Makefiles, Ninja, Visual Studio projects) for your platform. Nearly every C++ library (Eigen, ROOT, Boost) ships CMake integration.

### 28.2 A basic CMake project

A minimal `CMakeLists.txt` for an executable:

```cmake
cmake_minimum_required(VERSION 3.20)
project(analysis LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)              # use C++23
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(analyze main.cpp stats.cpp)   # target: an executable from these sources
```

The workflow (out-of-source build — keep generated files out of your source tree):

```text
$ cmake -B build          # configure: generate build files into ./build
$ cmake --build build     # compile & link
$ ./build/analyze         # run
```

`add_executable(analyze main.cpp stats.cpp)` declares a **target** `analyze` built from those sources. CMake figures out the compile-and-link commands (equivalent to Chapter 8's manual `g++ -c` + link), tracks dependencies, and rebuilds only what changed.

### 28.3 Libraries and linking dependencies

Split reusable code into a **library target**, and link it into executables:

```cmake
add_library(toolkit stats.cpp histogram.cpp)     # a library from these sources
target_include_directories(toolkit PUBLIC include)  # where its headers live

add_executable(analyze main.cpp)
target_link_libraries(analyze PRIVATE toolkit)   # link the library into the executable
```

To use an **external** library, `find_package` locates it and you link its target — CMake handles the include paths and link flags:

```cmake
find_package(Eigen3 REQUIRED)                    # find Eigen (header-only linear algebra)
target_link_libraries(analyze PRIVATE Eigen3::Eigen)

find_package(ROOT REQUIRED COMPONENTS Core Hist)  # find CERN ROOT
target_link_libraries(analyze PRIVATE ROOT::Core ROOT::Hist)
```

This replaces the fragile manual `-I/path/to/eigen -lblas` flags (Chapter 8's linker story) with a portable, self-locating declaration. `find_package(Eigen3)` finds Eigen wherever it's installed and sets up everything; linking `Eigen3::Eigen` pulls in its include paths automatically.

> 💡 **Idiom** — Express dependencies as **targets** (`target_link_libraries(analyze PRIVATE toolkit Eigen3::Eigen)`), not raw flags. Modern "target-based" CMake propagates include paths, compile definitions, and link requirements automatically — link Eigen and you *get* its headers, no manual `-I`. `PRIVATE` means "only this target needs it"; `PUBLIC` means "and so do things that link me" (Chapter 8's `api` vs `implementation` idea). This is how you link BLAS/LAPACK, ROOT, HDF5, or Boost cleanly across machines — the build "just works" on a collaborator's system.

### 28.4 Build types, flags, and sanitizers

CMake's **build types** bundle appropriate compiler flags:

- **`Debug`** (`-g`, no optimization) — for debugging and sanitizers.
- **`Release`** (`-O2`/`-O3 -DNDEBUG`) — optimized production builds.
- **`RelWithDebInfo`** — optimized *with* debug symbols (for profiling).

```text
$ cmake -B build -DCMAKE_BUILD_TYPE=Release      # optimized build
$ cmake -B build-dbg -DCMAKE_BUILD_TYPE=Debug -DCMAKE_CXX_FLAGS="-fsanitize=address,undefined"
```

The second configures a debug build with **AddressSanitizer + UBSan** (Chapters 11, 33) — the setup you'd use to test scientific code for memory bugs and undefined behaviour before a production run.

> 💡 **Idiom** — Maintain (at least) two build configurations: a **`Debug`** build with **sanitizers** (`-fsanitize=address,undefined`) for development and testing — it catches the memory and UB bugs that silently corrupt numerical results — and a **`Release`** build (`-O2`/`-O3`) for the actual computation, where every optimization counts. Run your tests under the sanitized debug build; run the science under the optimized one. CMake makes maintaining both trivial (`-DCMAKE_BUILD_TYPE=...`).

---

### Summary

- A **build system** automates compiling many files, tracking changes, and linking libraries across platforms — essential beyond a few files.
- **CMake** describes the project declaratively in **`CMakeLists.txt`** (targets + dependencies) and generates the platform's build files. Workflow: `cmake -B build` then `cmake --build build`.
- **`add_executable`**/**`add_library`** declare targets; **`target_link_libraries`** links them; **`find_package`** locates external libraries (Eigen, ROOT) and you link their targets — no manual `-I`/`-l`.
- **Build types** (`Debug`/`Release`/`RelWithDebInfo`) set flags; maintain a **sanitized Debug** build for testing and an **optimized Release** for computation.

### Self-check quiz

1. What does CMake generate, and why is that useful?
   <details><summary>Answer</summary>It generates platform-specific build files (Makefiles, Ninja, IDE projects) from a declarative `CMakeLists.txt`, so one description builds portably across platforms and compilers.</details>
2. How do you link an external library like Eigen?
   <details><summary>Answer</summary>`find_package(Eigen3 REQUIRED)` locates it, then `target_link_libraries(mytarget PRIVATE Eigen3::Eigen)` — which pulls in its include paths and flags automatically.</details>
3. What's the difference between `PRIVATE` and `PUBLIC` in `target_link_libraries`?
   <details><summary>Answer</summary>`PRIVATE` — only this target needs the dependency; `PUBLIC` — this target and anything linking it need it (propagated), analogous to implementation vs api dependencies.</details>
4. Why keep a sanitized Debug build and an optimized Release build?
   <details><summary>Answer</summary>Debug + sanitizers catch memory/UB bugs that corrupt results (run tests here); Release (`-O2`/`-O3`) gives performance for the actual computation.</details>

### Exercises

**Exercise 28.1 — Executable CMakeLists (guided).** Write a `CMakeLists.txt` that builds an executable `sim` from `main.cpp` and `physics.cpp`, using C++23.

<details><summary>Show solution</summary>

```cmake
cmake_minimum_required(VERSION 3.20)
project(sim LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(sim main.cpp physics.cpp)
```

**Why this works:** `project` names the project and enables C++; setting the standard to 23 configures the compiler; `add_executable(sim ...)` declares the `sim` target from the two sources. Build with `cmake -B build && cmake --build build`, run `./build/sim`. This is the minimal complete CMake project.

</details>

**Exercise 28.2 — Library + link.** Write CMake that builds a `toolkit` *library* from `stats.cpp`, and an executable `analyze` (from `main.cpp`) that links it.

<details><summary>Show solution</summary>

```cmake
cmake_minimum_required(VERSION 3.20)
project(analysis LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 23)

add_library(toolkit stats.cpp)
target_include_directories(toolkit PUBLIC include)

add_executable(analyze main.cpp)
target_link_libraries(analyze PRIVATE toolkit)
```

**Why this works:** `add_library(toolkit stats.cpp)` builds a reusable library; `target_include_directories(... PUBLIC include)` makes its headers available to anything that links it; `target_link_libraries(analyze PRIVATE toolkit)` links the library into the executable. This is the standard structure for a project with reusable components — exactly what the toolkit needs as it grows.

</details>

### Chapter project: a CMake build for the toolkit

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit** (build setup). **Builds on:** Ch.1–28. We give the toolkit a real, multi-target CMake build: a `toolkit` library, an `analyze` executable, and Eigen linked for future linear algebra.

**Goal.** A `CMakeLists.txt` structuring the toolkit as a library + executable, with C++23, Eigen, and a sanitized-debug option.

<details><summary>Show reference solution + commentary</summary>

Project layout:

```text
mc-toolkit/
├── CMakeLists.txt
├── include/toolkit/    (headers: dataset.hpp, histogram.hpp, ...)
├── src/                (dataset.cpp, histogram.cpp, stats.cpp)
└── app/main.cpp        (the analysis program)
```

`CMakeLists.txt`:

```cmake
cmake_minimum_required(VERSION 3.20)
project(mc_toolkit VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)          # for IDE/tooling

# --- the toolkit library ---
add_library(toolkit
    src/dataset.cpp
    src/histogram.cpp
    src/stats.cpp
)
target_include_directories(toolkit PUBLIC include)
target_compile_options(toolkit PRIVATE -Wall -Wextra)

# --- external dependency: Eigen (for linear algebra, Ch.24) ---
find_package(Eigen3 3.4 QUIET)
if(Eigen3_FOUND)
    target_link_libraries(toolkit PUBLIC Eigen3::Eigen)
endif()

# --- the analysis executable ---
add_executable(analyze app/main.cpp)
target_link_libraries(analyze PRIVATE toolkit)
```

Build it, in Release and in sanitized Debug:

```text
# optimized production build
$ cmake -B build -DCMAKE_BUILD_TYPE=Release
$ cmake --build build
$ ./build/analyze

# sanitized debug build for testing (catches memory bugs & UB)
$ cmake -B build-asan -DCMAKE_BUILD_TYPE=Debug \
        -DCMAKE_CXX_FLAGS="-fsanitize=address,undefined -g"
$ cmake --build build-asan
$ ./build-asan/analyze
```

**Commentary.**
- The toolkit is now a proper **library target** (`toolkit`, built from the `.cpp` sources we've written across the book) with **public headers** (`include/`), and the analysis is a separate **executable** (`analyze`) that links it — the same interface/implementation split from Chapter 8, now automated and scalable.
- **Eigen** is linked via `find_package` (optional here with `QUIET`/`if`), ready for the linear algebra of Chapter 24 — and adding ROOT or HDF5 for real data (Chapter 27) is the same pattern. No manual `-I`/`-l` flags anywhere.
- The two build commands give the two configurations the idiom recommends: **Release** (optimized) for running the science, **Debug + sanitizers** for catching the memory and UB bugs that silently corrupt numerical results before they reach a paper.
- This is a production-grade project structure. Every serious C++ scientific project — Geant4, ROOT-based analyses, lattice QCD codes — is organized and built essentially this way.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Build system** | Automates compiling, dependency tracking, and linking. |
| **CMake** | The de facto C++ meta-build system (`CMakeLists.txt`). |
| **Target** | An executable or library CMake builds (`add_executable`/`add_library`). |
| **`target_link_libraries`** | Declares a target's link dependencies. |
| **`find_package`** | Locates an installed external library. |
| **`PRIVATE` / `PUBLIC`** | Dependency needed by this target only / and its consumers. |
| **Build type** | `Debug`/`Release`/`RelWithDebInfo` — flag bundles. |

### What's next

That completes **Part 4 — Scientific Computing Core**: you can generate, integrate, solve, store, and build. **Part 5 — Performance & Mastery** takes it to the expert level, opening with **[Ch.29 — The Abstract Machine & Undefined Behavior](#chapter-29--the-abstract-machine--undefined-behavior)** — the mental model of *what C++ code really means*, and the undefined behaviour that every expert must understand to write correct, fast code.

[↑ back to top](#chapter-28--build-systems-cmake--linking-numerical-libraries)


---

## Chapter 29 — The Abstract Machine & Undefined Behavior

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Floating Point](#chapter-3--floating-point--numeric-types), [Ch.11 — RAII](#chapter-11--dynamic-memory--raii)

**Learning objectives** — after this chapter you will be able to:

- Explain the C++ abstract machine and the "as-if" rule.
- Recognize the major categories of undefined behavior (UB).
- Understand why UB enables optimization — and how it bites.
- Detect UB with sanitizers.

**In this chapter**

- [29.1 The abstract machine and the as-if rule](#291-the-abstract-machine-and-the-as-if-rule)
- [29.2 Undefined behavior](#292-undefined-behavior)
- [29.3 Why UB exists: optimization](#293-why-ub-exists-optimization)
- [29.4 Detecting UB](#294-detecting-ub)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-ub-audit-of-the-toolkit)· Glossary · What's next

---

### 29.1 The abstract machine and the as-if rule

C++ is not defined in terms of your actual CPU. The standard defines an **abstract machine** — an idealized computer — and specifies your program's behaviour *on that machine*. The compiler may generate any real machine code it likes, **as long as the observable behaviour matches** what the abstract machine would produce. This is the **as-if rule**: the compiler can transform, reorder, and eliminate code freely, provided the *observable* effects (I/O, `volatile` accesses, program termination) are preserved.

```cpp
long s = 0;
for (int i = 1; i <= 100; ++i) s += i;     // you wrote a loop
// observable result: 5050
```

The compiler is free to replace that entire loop with the constant `5050` (the closed form `n(n+1)/2`) — the observable result is identical, so the as-if rule permits it. Optimization *is* the compiler exploiting this freedom: it does whatever is fastest, as long as you can't tell the difference through observable behaviour.

> ⚙️ **Under the hood** — This is why you can't reason about performance by counting the operations in your source. The source describes *what result* to produce on the abstract machine; the optimizer decides *how*. A hand-written loop may become a closed form, a SIMD burst, or nothing at all (if the result is unused — "dead code elimination"). Your source is a *specification of observable behaviour*, not a script of CPU instructions. Understanding this is the foundation of both optimization (Chapter 31) and undefined behaviour.

### 29.2 Undefined behavior

The abstract machine defines behaviour for *correct* programs. For certain erroneous operations, the standard imposes **no requirements at all** — this is **undefined behavior (UB)**. A program with UB has *no defined meaning*; the compiler may do anything — produce wrong results, crash, or (worst) appear to work until it doesn't. The major categories:

- **Signed integer overflow** — `INT_MAX + 1` is UB (unsigned overflow, by contrast, is *defined* to wrap modulo 2ⁿ).
- **Out-of-bounds access** — indexing past an array/vector (`v[v.size()]`).
- **Reading uninitialized memory** — using a variable before assigning it.
- **Dangling references/pointers** — using memory after it's freed or out of scope (Chapters 10–11).
- **Data races** — unsynchronized concurrent access to the same memory (Chapter 32).
- **Strict aliasing / invalid casts** — accessing an object through an incompatible type.
- **Null pointer dereference**, **division by zero**, **infinite loops with no side effects**.

```cpp
unsigned u = 0; u -= 1;    // DEFINED: wraps to UINT_MAX = 4294967295
int x = INT_MAX; int y = x + 1;   // UNDEFINED BEHAVIOR: signed overflow
```

> ⚠️ **Gotcha — signed overflow is UB, and it *silently miscompiles*.** Because the compiler is *allowed to assume signed overflow never happens*, it may optimize `if (x + 1 < x)` to `if (false)` — a check you wrote to detect overflow is deleted because "it can't happen." In scientific code, an index or counter that overflows doesn't wrap predictably; it enters the realm of nasal demons. Use unsigned types for defined wraparound, wider types (`long`/`int64_t`) to avoid overflow, and sanitizers to catch it.

### 29.3 Why UB exists: optimization

UB isn't an oversight — it's a deliberate *contract*. By declaring certain things undefined, the standard lets the compiler **assume they never happen**, and optimize on that assumption. If signed overflow were defined to wrap, the compiler couldn't simplify `2*x/2` to `x`, or promote a 32-bit loop counter to a 64-bit register, or assume `i < n` eventually holds. UB is the price of performance: the language trusts you to not do the undefined thing, and in return generates fast code.

The bargain is dangerous because UB is **not local**. A UB operation doesn't just produce a wrong value *there* — it poisons the compiler's reasoning about surrounding code, and the visible symptom can appear far from the cause (or vanish under `-O0` and reappear under `-O2`). This is why UB is the source of the most baffling C++ bugs.

> ⚙️ **Under the hood** — The optimizer works by *propagating assumptions*. When it sees `a[i]`, it may assume `i` is in bounds (else UB) and use that to eliminate a later bounds check. When it sees `*p`, it assumes `p` is non-null (else UB) and deletes your `if (p)` guard *below* the dereference — a real class of security bug. The compiler isn't being malicious; it's holding you to the contract. "It worked before" means "the UB happened to do what you wanted"; a new compiler, flag, or surrounding change can break it at any time. The only safe amount of UB is *zero*.

### 29.4 Detecting UB

You cannot rely on UB "looking wrong" — it often looks fine. The tools:

- **UndefinedBehaviorSanitizer (UBSan)** — `-fsanitize=undefined` instruments the program to *catch UB at runtime* (signed overflow, OOB, misaligned access, invalid casts) and report the exact location.
- **AddressSanitizer (ASan)** — `-fsanitize=address` catches memory UB: out-of-bounds, use-after-free, leaks (Chapter 11).
- **Compiler warnings** — `-Wall -Wextra` flag many likely-UB constructs at compile time.
- **Static analyzers** (`clang-tidy`, `cppcheck`) — find UB patterns without running.

```text
$ g++ -std=c++23 -fsanitize=undefined overflow.cpp && ./a.out
overflow.cpp:4:9: runtime error: signed integer overflow:
    2147483647 + 1 cannot be represented in type 'int'
```

UBSan pinpoints the overflow — the exact line and values — turning an invisible miscompilation into a clear runtime error.

> 💡 **Idiom** — **Run your test suite under sanitizers.** Build a `Debug` configuration (Chapter 28) with `-fsanitize=address,undefined` and run all tests through it. Sanitizers catch the memory and integer UB that silently corrupts numerical results — a use-after-free that reads stale energies, an index overflow that skips events, a misaligned SIMD load. For scientific code where a wrong number in a paper is the failure mode, this is not optional. Catch UB in testing, run the science with `-O2`. (Chapter 33 goes deeper on the testing discipline.)

---

### Summary

- C++ programs are defined on an **abstract machine**; the **as-if rule** lets the compiler generate any code with the same *observable* behaviour — so your source specifies *results*, not instructions.
- **Undefined behavior (UB)** — signed overflow, out-of-bounds, uninitialized reads, dangling pointers, data races, aliasing violations — has *no defined meaning*; the program may do anything.
- UB exists to enable **optimization**: the compiler assumes it never happens. This makes UB **non-local** — the symptom can appear far from the cause, or change with optimization level.
- **Detect UB with sanitizers** (`-fsanitize=undefined,address`), warnings, and static analysis. Run tests under sanitizers; the only safe amount of UB is zero.

### Self-check quiz

1. What is the "as-if" rule?
   <details><summary>Answer</summary>The compiler may generate any machine code it likes as long as the program's *observable behaviour* (I/O, volatile access, termination) matches what the abstract machine would produce.</details>
2. Is `unsigned` overflow undefined? Is `signed`?
   <details><summary>Answer</summary>Unsigned overflow is *defined* (wraps modulo 2ⁿ). Signed overflow is *undefined behavior*.</details>
3. Why is UB "non-local"?
   <details><summary>Answer</summary>The compiler optimizes assuming UB never happens, so a UB operation poisons reasoning about surrounding code — the visible symptom can appear far from the cause, or only under optimization.</details>
4. How do you catch UB that "looks like it works"?
   <details><summary>Answer</summary>Run under sanitizers (`-fsanitize=undefined,address`), enable `-Wall -Wextra`, and use static analyzers — UB often produces correct-looking output until it doesn't.</details>

### Exercises

**Exercise 29.1 — Defined vs undefined (guided).** Show that unsigned wraparound is defined and predictable.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <climits>
int main() {
    unsigned u = 0;
    u -= 1;                                  // defined: wraps to UINT_MAX
    std::cout << std::format("0u - 1 = {}\n", u);
    std::cout << std::format("UINT_MAX = {}\n", UINT_MAX);
}
```

Output:
```text
0u - 1 = 4294967295
UINT_MAX = 4294967295
```

**Why this works:** unsigned arithmetic is defined to wrap modulo 2³², so `0u - 1` is exactly `UINT_MAX = 4294967295` — reliable and portable. The *same* operation on a signed `int` would be undefined behavior. This is why counters and bit manipulation use unsigned types when wraparound is intended.

</details>

**Exercise 29.2 — Catch overflow with UBSan.** Compile a signed-overflow program with `-fsanitize=undefined` and observe the diagnostic.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <climits>
int main() {
    int x = INT_MAX;
    int y = x + 1;          // signed overflow — UB
    std::cout << y << "\n";
}
```

Compile and run with UBSan:
```text
$ g++ -std=c++23 -fsanitize=undefined ex29.cpp && ./a.out
ex29.cpp:5:15: runtime error: signed integer overflow:
    2147483647 + 1 cannot be represented in type 'int'
-2147483648
```

**Why this works:** UBSan instruments arithmetic and reports the exact overflow — line, values, and type — at runtime. Without it, the program might print `-2147483648` (as here) *or* be miscompiled entirely, with no warning. Sanitizers turn silent UB into a loud, locatable error.

</details>

### Chapter project: a UB audit of the toolkit

> 🛠️ **Chapter Project** — Hardens the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–29. Before trusting results in a paper, audit the toolkit for UB. We enumerate the risks and set up a sanitized build.

**Goal.** A checklist of UB risks in a scientific toolkit and a demonstration that a sanitized build catches a planted bug.

<details><summary>Show reference solution + commentary</summary>

The audit — where UB hides in numerical code:

| Risk | Where | Guard |
|------|-------|-------|
| **Signed overflow** | Event counters, index arithmetic on large samples | `int64_t`/`std::size_t`; UBSan |
| **Out-of-bounds** | Histogram binning, grid indexing (Ch.9, 25) | `.at()` in debug; ASan; bounds checks |
| **Uninitialized reads** | Accumulators, struct fields | `{}` initialization (Ch.2); `-Wall` |
| **Dangling references** | Returning refs to locals, `span` over freed data (Ch.10, 18) | RAII; ASan |
| **Data races** | Parallel histogram fills (Ch.32) | Atomics/locks; TSan |

A planted bug and its detection:

```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<double> energies{91.1, 91.3, 90.9};
    double sum = 0;
    for (std::size_t i = 0; i <= energies.size(); ++i)   // BUG: <= reads energies[3]
        sum += energies[i];
    std::cout << sum << "\n";
}
```

Under AddressSanitizer:
```text
$ g++ -std=c++23 -fsanitize=address audit.cpp && ./a.out
==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x...
    READ of size 8 at 0x... thread T0
    #0 ... in main audit.cpp:6
    0x... is located 0 bytes after 24-byte region
```

**Commentary.**
- The classic off-by-one (`<=` instead of `<`) reads one element past the vector — **undefined behavior**. Without a sanitizer it might read garbage and silently corrupt `sum`, producing a subtly wrong result that passes casual inspection. ASan reports it precisely: a heap-buffer-overflow read of 8 bytes, 0 bytes past the 24-byte (3-`double`) region, at line 6.
- This is the whole argument of the chapter in one example: the bug is invisible in the output (`sum` is just *wrong*, not obviously broken), but a sanitized build turns it into a locatable error. For the toolkit — whose output ends up in a physics result — running the test suite under `-fsanitize=address,undefined` is the difference between catching this in CI and publishing a wrong number.
- The fix is a one-character change (`<`), but the *discipline* is the point: sanitized builds (Chapter 28) + a habit of `{}` initialization + `.at()` in debug + `int64_t` for large counts. That discipline is what makes the toolkit's numbers trustworthy.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Abstract machine** | The idealized computer the C++ standard defines behaviour on. |
| **As-if rule** | Compiler may do anything preserving observable behaviour. |
| **Observable behaviour** | I/O, volatile accesses, termination — what must be preserved. |
| **Undefined behavior (UB)** | An operation with no defined meaning; anything may happen. |
| **Signed overflow** | UB (unlike unsigned, which wraps). |
| **UBSan / ASan** | Sanitizers that catch undefined / memory UB at runtime. |
| **Nasal demons** | Folklore term for "anything can happen" under UB. |

### What's next

You understand what code *means* and how it can go undefined. Next we turn the compiler's freedom into a tool: **[Ch.30 — Template Metaprogramming](#chapter-30--template-metaprogramming)** — computing with types, `if constexpr`, SFINAE, and CRTP to write generic, zero-overhead abstractions.

[↑ back to top](#chapter-29--the-abstract-machine--undefined-behavior)


---

## Chapter 30 — Template Metaprogramming

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.16 — Templates](#chapter-16--templates), [Ch.20 — Concepts](#chapter-20--concepts--constraints)

**Learning objectives** — after this chapter you will be able to:

- Branch on types at compile time with `if constexpr`.
- Query and constrain types with type traits.
- Understand SFINAE and how concepts supersede it.
- Use CRTP for zero-overhead static polymorphism.
- Handle variadic arguments with fold expressions.

**In this chapter**

- [30.1 `if constexpr` — compile-time branching](#301-if-constexpr--compile-time-branching)
- [30.2 Type traits](#302-type-traits)
- [30.3 SFINAE and concepts](#303-sfinae-and-concepts)
- [30.4 CRTP — static polymorphism](#304-crtp--static-polymorphism)
- [30.5 Variadic templates and fold expressions](#305-variadic-templates-and-fold-expressions)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-generic-accumulator)· Glossary · What's next

---

Template metaprogramming means **computing with types and values at compile time** — writing code that the compiler *runs during compilation* to generate the code that actually executes. Done well, it produces generic abstractions with **zero runtime overhead**: the genericity is resolved at build time, leaving optimal specialized code. This is how the STL, Eigen, and every high-performance C++ library achieve "fast *and* general."

### 30.1 `if constexpr` — compile-time branching

Ordinary `if` chooses a branch *at runtime*; **`if constexpr`** (C++17) chooses *at compile time*, and the *untaken branch is discarded* — it need not even compile for the current type. This lets one template behave differently per type:

```cpp
template<typename T>
std::string describe(T v) {
    if constexpr (std::is_integral_v<T>)
        return std::format("integer {}", v);
    else if constexpr (std::is_floating_point_v<T>)
        return std::format("real {:.2f}", v);
    else
        return "other";
}
// describe(42)    → "integer 42"
// describe(91.19) → "real 91.19"
```

Because the false branches are *discarded*, `describe(42)` never instantiates the floating-point `{:.2f}` formatting — no runtime check, no dead code. This replaces the old, painful SFINAE overloading (§30.3) for most "do X for this kind of type" needs.

### 30.2 Type traits

The **`<type_traits>`** header provides compile-time *queries* and *transformations* on types. Queries (ending in `_v`) yield a `bool`: `std::is_integral_v<T>`, `std::is_floating_point_v<T>`, `std::is_same_v<A, B>`, `std::is_pointer_v<T>`. Transformations (ending in `_t`) yield a type: `std::remove_const_t<T>`, `std::decay_t<T>`, `std::common_type_t<A, B>`:

```cpp
static_assert(std::is_floating_point_v<double>);       // true
static_assert(std::is_same_v<int, std::int32_t>);      // true (on this platform)
using U = std::remove_reference_t<int&>;               // U is int
```

Traits are the vocabulary of metaprogramming: you *ask* about a type (`is_floating_point_v`) and *react* (`if constexpr`, concepts) or *transform* it. Combined with `static_assert` (Chapter 26), they validate template arguments at compile time with clear errors.

> ⚙️ **Under the hood** — Type traits are themselves templates. `std::is_integral<T>` is a struct specialized so that `is_integral<int>` derives from `true_type` (which has `static constexpr bool value = true`) and the primary template from `false_type`. The `_v` suffix is just `is_integral<T>::value`. All of it evaluates during compilation to a `bool` literal — the trait "call" leaves *no code* in the binary. Metaprogramming is the compiler's type system doing computation for you, for free at runtime.

### 30.3 SFINAE and concepts

Before concepts (Chapter 20), constraining templates relied on **SFINAE** — *"Substitution Failure Is Not An Error."* When the compiler substitutes a type into a template and the substitution produces an *invalid type* (in the signature), that overload is silently *removed from consideration* rather than causing an error. Libraries exploited this (via `std::enable_if`) to enable/disable overloads by type properties — powerful, but notoriously cryptic:

```cpp
// Old SFINAE style (avoid in new code):
template<typename T, std::enable_if_t<std::is_floating_point_v<T>, int> = 0>
T normalize(T x) { return x / T{2}; }
```

**Concepts (C++20) replace this** with readable, direct constraints — the same intent, a fraction of the noise and vastly better error messages:

```cpp
template<std::floating_point T>       // a concept — reads like English
T normalize(T x) { return x / T{2}; }
```

> 💡 **Idiom** — In modern C++, **prefer `if constexpr` and concepts over SFINAE**. For "one function, type-dependent body," use `if constexpr` (§30.1). For "constrain what types are allowed," use **concepts** (Chapter 20). Reserve raw `enable_if`/SFINAE for maintaining old code or the rare corner concepts don't cover. You still need to *recognize* SFINAE (it pervades pre-C++20 libraries), but you should rarely *write* it. The result is generic code that reads almost like ordinary code.

### 30.4 CRTP — static polymorphism

The **Curiously Recurring Template Pattern** achieves polymorphism *without virtual functions* — and thus without their runtime cost (Chapter 15's vtable indirection). A base class is templated on the *derived* class and casts `this` to it, calling the derived method at compile time:

```cpp
template<typename Derived>
struct Detector {
    double calibrated(double raw) {
        return static_cast<Derived*>(this)->gain() * raw;   // resolved at COMPILE time
    }
};
struct Calo  : Detector<Calo>  { double gain() { return 2.0; } };
struct Track : Detector<Track> { double gain() { return 0.5; } };

// Calo{}.calibrated(10)  → 20   (gain 2.0)
// Track{}.calibrated(10) → 5    (gain 0.5)
```

`Detector<Calo>` and `Detector<Track>` are *distinct types*; the call to `gain()` is a direct, **inlinable** call — no vtable, no virtual dispatch. You get the *code reuse* of a base class and the *dispatch* of polymorphism, with zero runtime overhead. This is a staple of high-performance libraries (Eigen's expression templates use it heavily).

> ⚙️ **Under the hood** — Runtime polymorphism (Chapter 15) costs a vtable pointer per object and an indirect call that the compiler usually *can't inline* (it doesn't know the dynamic type). CRTP moves the choice to compile time: because `Detector<Calo>::calibrated` statically knows the derived type, `gain()` inlines to a direct multiply — the whole call can collapse to a single instruction. The trade-off: CRTP dispatches on the *static* type (no heterogeneous `vector<Base*>`), so use it when the type is known at compile time and speed matters; use virtuals when you need runtime dispatch over a mixed collection.

### 30.5 Variadic templates and fold expressions

**Variadic templates** accept any number of arguments of any types (`typename... Args`), and **fold expressions** (C++17) apply an operator across them concisely:

```cpp
template<typename... Args>
auto sum(Args... args) { return (args + ...); }    // fold: a0 + a1 + ... + aN

// sum(1, 2, 3, 4)  → 10
// sum(1.5, 2.5)    → 4.0
```

`(args + ...)` expands to `arg0 + arg1 + ... + argN` at compile time — no loop, no array, fully inlined. Fold expressions handle any binary operator (`+`, `*`, `&&`, `,`), making variadic code (previously requiring recursive template tricks) a one-liner. This is how `std::format`, `std::make_unique`, and `emplace_back` forward arbitrary arguments.

---

### Summary

- **`if constexpr`** branches at *compile time* and *discards* the untaken branch — one template, type-dependent bodies, zero runtime cost.
- **Type traits** (`<type_traits>`) query (`is_floating_point_v`, `is_same_v`) and transform (`remove_reference_t`, `decay_t`) types at compile time; they leave no code in the binary.
- **SFINAE** (`enable_if`) was the old way to constrain templates; **concepts** (Chapter 20) supersede it — prefer `if constexpr` + concepts, but recognize SFINAE in legacy code.
- **CRTP** gives **static polymorphism** (base templated on derived) — code reuse + dispatch with *no vtable*, fully inlinable; use it when the type is known at compile time.
- **Variadic templates + fold expressions** (`(args + ...)`) handle any number of arguments with no loop, fully inlined.

### Self-check quiz

1. How does `if constexpr` differ from ordinary `if`?
   <details><summary>Answer</summary>It's evaluated at compile time and the untaken branch is *discarded* (need not compile for the current type) — enabling type-dependent bodies with no runtime branch.</details>
2. What does `std::is_floating_point_v<T>` cost at runtime?
   <details><summary>Answer</summary>Nothing — it's a compile-time `bool` constant; the trait leaves no code in the binary.</details>
3. What replaced SFINAE in modern C++?
   <details><summary>Answer</summary>Concepts (C++20) for constraints, and `if constexpr` for type-dependent bodies — both far more readable with better error messages.</details>
4. Why is CRTP faster than virtual functions?
   <details><summary>Answer</summary>It resolves the derived call at compile time (no vtable, no indirect call), so the call inlines — whereas virtual dispatch is an indirect call the compiler usually can't inline.</details>

### Exercises

**Exercise 30.1 — Compile-time type dispatch (guided).** Write a `zero<T>()` that returns the right zero: `0` for integers, `0.0` for floats.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <type_traits>
template<typename T>
T zero() {
    if constexpr (std::is_integral_v<T>) return T{0};
    else return T{0.0};
}
int main() {
    std::cout << std::format("int zero: {}\n", zero<int>());
    std::cout << std::format("double zero: {:.1f}\n", zero<double>());
}
```

Output:
```text
int zero: 0
double zero: 0.0
```

**Why this works:** `if constexpr` picks the branch at compile time based on `T`. For `int` it returns `T{0}`; for `double`, `T{0.0}`. The untaken branch is discarded, so there's no runtime type check — the compiler generates a function that simply returns the constant.

</details>

**Exercise 30.2 — Fold-expression product.** Write a variadic `product(...)` that multiplies all its arguments.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
template<typename... Args>
auto product(Args... args) { return (args * ...); }
int main() {
    std::cout << std::format("product(2,3,4)={}\n", product(2, 3, 4));
    std::cout << std::format("product(1.5,2.0,3.0)={}\n", product(1.5, 2.0, 3.0));
}
```

Output:
```text
product(2,3,4)=24
product(1.5,2.0,3.0)=9
```

**Why this works:** `(args * ...)` is a fold expression expanding to `arg0 * arg1 * arg2` at compile time. It works for any number of arguments and any multipliable type — `2*3*4=24`, `1.5*2.0*3.0=9.0`. No loop, no container; the whole product inlines to a chain of multiplies.

</details>

**Exercise 30.3 — CRTP counter.** Use CRTP to give any class an auto-incrementing instance count without repeating the counter code.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
template<typename Derived>
struct Counted {
    static inline int count = 0;
    Counted() { ++count; }
};
struct Event    : Counted<Event>    {};
struct Particle : Counted<Particle> {};
int main() {
    Event e1, e2, e3;
    Particle p1, p2;
    std::cout << std::format("Events: {}  Particles: {}\n",
                             Counted<Event>::count, Counted<Particle>::count);
}
```

Output:
```text
Events: 3  Particles: 2
```

**Why this works:** each `Counted<Derived>` instantiation has its *own* `static count` (distinct types → distinct statics), so `Event` and `Particle` count independently — 3 events, 2 particles — from a single shared base. This is CRTP for *mixin* behaviour: inject a capability (counting, cloning, comparison) into many classes with zero duplication and no virtual overhead.

</details>

### Chapter project: a generic accumulator

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–30. The toolkit accumulates many quantities (energies, counts, momenta). We build one *generic, zero-overhead* accumulator that adapts to the value type at compile time.

**Goal.** A `constexpr`-friendly `Accumulator<T>` that works for integers and reals, reporting count, sum, and mean with type-appropriate behaviour.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <type_traits>

template<typename T>
class Accumulator {
    static_assert(std::is_arithmetic_v<T>, "Accumulator needs a numeric type");
    // integers accumulate into a wider type to resist overflow (Ch.29);
    // reals accumulate as double for precision (Ch.3)
    using Sum = std::conditional_t<std::is_integral_v<T>, long long, double>;
    Sum sum_ = 0;
    long n_ = 0;
public:
    void add(T x) { sum_ += x; ++n_; }
    long count() const { return n_; }
    Sum sum() const { return sum_; }
    double mean() const { return n_ ? static_cast<double>(sum_) / n_ : 0.0; }
};

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v25 — generic accumulator ===\n";

    Accumulator<double> energy;
    for (double e : {91.1, 91.3, 90.9, 91.2, 91.0}) energy.add(e);
    std::cout << std::format("energies: n={} sum={:.1f} mean={:.4f}\n",
                             energy.count(), energy.sum(), energy.mean());

    Accumulator<int> hits;
    for (int h : {12, 7, 23, 4, 19}) hits.add(h);
    std::cout << std::format("hits:     n={} sum={} mean={:.2f}\n",
                             hits.count(), hits.sum(), hits.mean());
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v25 — generic accumulator ===
energies: n=5 sum=455.5 mean=91.1000
hits:     n=5 sum=65 mean=13.00
```

**Commentary.**
- One `Accumulator<T>` template serves both `double` energies and `int` hit-counts. The metaprogramming does real work: **`std::conditional_t`** selects the *accumulation type* per `T` — `long long` for integers (wide, to resist the overflow UB of Chapter 29) and `double` for reals (precision, Chapter 3). This is a compile-time decision with zero runtime cost; each instantiation is optimal for its type.
- **`static_assert(std::is_arithmetic_v<T>)`** rejects non-numeric types at *compile time* with a clear message — `Accumulator<std::string>` fails to build, not at runtime. This is the metaprogramming safety net (Chapter 26).
- The result is a single, correct, zero-overhead abstraction that the whole toolkit can use for *any* numeric quantity — energies (mean 91.1), hit counts (mean 13.0), momenta, χ² values. This is the payoff of template metaprogramming: **write once, specialized-and-fast everywhere**, with correctness (right accumulation type, validated inputs) baked in at build time. It's exactly how production numerical libraries are built.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`if constexpr`** | Compile-time branch; untaken branch is discarded. |
| **Type trait** | Compile-time query/transform on a type (`<type_traits>`). |
| **SFINAE** | "Substitution failure is not an error" — old constraint mechanism. |
| **`enable_if`** | The SFINAE helper concepts replace. |
| **CRTP** | Base templated on derived → static polymorphism, no vtable. |
| **Variadic template** | Accepts any number of arguments (`typename... Args`). |
| **Fold expression** | Applies an operator across a parameter pack (`(args + ...)`). |
| **`std::conditional_t`** | Selects one of two types at compile time. |

### What's next

You can write generic, zero-overhead abstractions. Now we make code *fast* on real hardware: **[Ch.31 — Performance & Optimization for HPC](#chapter-31--performance--optimization-for-hpc)** — the memory hierarchy, cache-friendly data layout, inlining, SIMD, and how to *measure* before you optimize.

[↑ back to top](#chapter-30--template-metaprogramming)


---

## Chapter 31 — Performance & Optimization for HPC

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.13 — Move Semantics](#chapter-13--move-semantics), [Ch.25 — Memory Layout](#chapter-25--multidimensional-data--layout), [Ch.29 — Abstract Machine](#chapter-29--the-abstract-machine--undefined-behavior)

**Learning objectives** — after this chapter you will be able to:

- Reason about the memory hierarchy and cache.
- Write cache-friendly, vectorizable code.
- Understand inlining, allocation cost, and how the optimizer helps.
- *Measure* performance before optimizing.

**In this chapter**

- [31.1 Measure first](#311-measure-first)
- [31.2 The memory hierarchy and cache locality](#312-the-memory-hierarchy-and-cache-locality)
- [31.3 Allocation, inlining, and move](#313-allocation-inlining-and-move)
- [31.4 SIMD and auto-vectorization](#314-simd-and-auto-vectorization)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-optimizing-the-histogram-fill)· Glossary · What's next

---

### 31.1 Measure first

The cardinal rule of optimization: **measure, don't guess.** The compiler's as-if rule (Chapter 29) and modern CPUs make intuition unreliable — the "obvious" bottleneck is often already optimized away, and the real one is somewhere surprising. Profile to find where time actually goes, then optimize *that*, then measure again.

The simplest measurement is timing with **`<chrono>`**:

```cpp
#include <chrono>
using Clock = std::chrono::steady_clock;
auto t0 = Clock::now();
/* ... work ... */
auto t1 = Clock::now();
double ms = std::chrono::duration<double, std::milli>(t1 - t0).count();
```

Use `steady_clock` (monotonic — for measuring *durations*), not `system_clock` (wall time, can jump). For serious work, use a profiler (`perf`, `valgrind --tool=callgrind`, VTune) and a benchmarking library (Google Benchmark) that handles warm-up, repetition, and statistics.

> ⚠️ **Gotcha — the optimizer deletes unmeasured work.** If a benchmark computes a result nobody uses, the as-if rule lets the compiler *delete the whole computation* — you measure nothing (0 ms). Force the result to be "observed": accumulate into a `volatile`, print it, or use a benchmark library's `DoNotOptimize`. Also always benchmark with **optimization on** (`-O2`/`-O3`) — timing a `-O0` debug build measures code no one will ever run.

### 31.2 The memory hierarchy and cache locality

The single most important performance fact in HPC: **memory is a hierarchy, and the gap is enormous.** A modern CPU can do an arithmetic op in well under a nanosecond, but fetching data from main RAM takes ~100 ns — hundreds of wasted cycles. Between them sit **caches** (L1 ~1 ns, L2 ~4 ns, L3 ~15 ns). The CPU loads memory in **cache lines** (64 bytes) and prefetches sequential accesses. So the golden rule: **access memory contiguously** — touch data that's next to data you just touched.

The effect is dramatic. Summing a 4000×4000 matrix stored row-major, traversed two ways:

```cpp
// Row-major traversal — contiguous (cache-friendly)
for (int i = 0; i < N; ++i)
    for (int j = 0; j < N; ++j) s += m[i*N + j];   // m[i*N+j], m[i*N+j+1], ... adjacent

// Column-major traversal — strided (cache-hostile)
for (int j = 0; j < N; ++j)
    for (int i = 0; i < N; ++i) s += m[i*N + j];   // jumps N*8 bytes each step
```

Measured (`-O3`, representative — exact numbers vary by machine/run):

```text
row-major:    ~27 ms
column-major: ~282 ms
speedup:      ~10x
```

*Same computation, same data, same result* — a **~10× difference** purely from access pattern. The row-major loop walks memory sequentially (every cache line fully used, prefetcher engaged); the column-major loop jumps `N×8` bytes each step, touching one value per cache line and thrashing the cache. This is why data *layout* (Chapter 25 — SoA, contiguous grids) is a first-order performance concern, not a detail.

> ⚙️ **Under the hood** — On many current CPUs a cache line is 64 bytes, so a line can hold 8 `double`s. Contiguous access can use the whole line and help hardware prefetching; a large stride may use only one value per fetched line. Exact line size, cache behavior, and prefetching are architecture-specific, so confirm them with hardware documentation and counters. On memory-bound code, how data moves can matter more than arithmetic throughput.

### 31.3 Allocation, inlining, and move

**Heap allocation is expensive** (Chapter 11) — a `new`/`malloc` may take hundreds of nanoseconds and cause fragmentation. In hot loops, avoid repeated allocation:

```cpp
std::vector<int> v;
v.reserve(2'000'000);                 // one allocation up front
for (int i = 0; i < 2'000'000; ++i) v.push_back(i);
// vs. no reserve: ~20 reallocations as the vector grows → ~2-3x slower here
```

Reserving the final size once (~9 ms) beat letting the vector reallocate geometrically as it grows (~21 ms) — a **~2× win** from eliminating repeated allocation and copying. Similarly, **move semantics** (Chapter 13) avoids deep copies of large buffers, and **RVO** (Chapter 6) elides return copies entirely.

**Inlining** is the optimizer's most valuable transformation: replacing a function call with the function's body eliminates call overhead *and* — crucially — exposes the body to further optimization across the call boundary. Small functions in headers (and `constexpr`, templates, CRTP — Chapter 30) inline readily; this is why zero-overhead abstraction works.

> 💡 **Idiom** — In performance-critical code: **`reserve()` containers** to their final size; **pass large objects by `const&`** and **move** (not copy) them (Chapters 6, 13); **keep data contiguous** (`vector`/`array`, SoA); and let small functions **inline** (define them in headers, use templates/`constexpr`). None of these change *what* the code computes — they change how well it maps to the machine. Combined with a cache-friendly layout, they routinely yield order-of-magnitude speedups over naive code, with no algorithm change.

### 31.4 SIMD and auto-vectorization

Modern CPUs have **SIMD** units (Single Instruction, Multiple Data): one instruction operates on a *vector* of values at once — e.g. AVX processes 4 `double`s (256 bits) per instruction. The compiler **auto-vectorizes** suitable loops at `-O3`, turning scalar code into SIMD automatically:

```cpp
void axpy(double* y, const double* x, double a, std::size_t n) {
    for (std::size_t i = 0; i < n; ++i) y[i] += a * x[i];   // vectorizable
}
```

Compiled with `-O3 -march=native`, GCC reports:

```text
$ g++ -O3 -march=native -fopt-info-vec-optimized -c axpy.cpp
axpy.cpp:3: optimized: loop vectorized using 32 byte vectors
```

"32 byte vectors" = 4 `double`s per SIMD instruction — up to a **4× arithmetic throughput** win, for free, from a plain loop. To *enable* vectorization: keep loops simple (no early exits, no aliasing surprises), use contiguous data, and compile with `-O3 -march=native`. Check `-fopt-info-vec` to see what did and didn't vectorize.

> ⚙️ **Under the hood** — Auto-vectorization needs to prove the loop is safe to parallelize across lanes: no loop-carried dependency, no overlap between `x` and `y` (aliasing — Chapter 29), a trip count it can reason about. `-march=native` tells GCC which SIMD instructions your CPU supports (SSE/AVX/AVX-512). When auto-vectorization isn't enough, you can drop to `std::experimental::simd`, compiler intrinsics, or libraries (Eigen, xsimd) — but a clean, contiguous loop at `-O3` gets the compiler most of the way for free. This is why the *layout* and *simplicity* idioms above matter: they're what let the vectorizer fire.

---

### Summary

- **Measure first** with `<chrono>` (`steady_clock`) or a profiler; optimize the real bottleneck, always with `-O2`/`-O3`. Beware the optimizer deleting unobserved work.
- The **memory hierarchy** dominates HPC: RAM is ~100× slower than cache. **Access memory contiguously** — a cache-friendly access pattern gave a **~10× speedup** with identical computation.
- **Avoid repeated allocation** (`reserve`), prefer **move** over copy and **RVO**, and let small functions **inline** — routine order-of-magnitude wins with no algorithm change.
- **SIMD auto-vectorization** (`-O3 -march=native`) processes multiple values per instruction (~4 `double`s) for free — enabled by simple, contiguous, non-aliasing loops.

### Self-check quiz

1. Why "measure first"?
   <details><summary>Answer</summary>The compiler and CPU make intuition unreliable — the guessed bottleneck is often already optimized; profiling finds where time *actually* goes so you optimize the right thing.</details>
2. Why is contiguous memory access so much faster than strided?
   <details><summary>Answer</summary>Contiguous access makes effective use of fetched cache lines and often helps prefetching; a large stride wastes transferred bytes. The line size and measured ratio are machine-specific.</details>
3. What does `reserve()` save?
   <details><summary>Answer</summary>Repeated reallocation and copying as a vector grows — one allocation up front instead of ~log(n) reallocations, ~2× faster in the example.</details>
4. What enables auto-vectorization?
   <details><summary>Answer</summary>Simple loops (no early exit, no loop-carried dependency, no aliasing), contiguous data, and `-O3 -march=native` so the compiler knows the CPU's SIMD instructions.</details>

### Exercises

**Exercise 31.1 — Time it (guided).** Measure how long it takes to sum a million doubles, forcing the result to be observed.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <chrono>
int main() {
    std::vector<double> v(1'000'000, 1.5);
    auto t0 = std::chrono::steady_clock::now();
    volatile double s = 0;                       // volatile: prevent deletion
    double acc = 0; for (double x : v) acc += x; s = acc;
    auto t1 = std::chrono::steady_clock::now();
    double ms = std::chrono::duration<double, std::milli>(t1 - t0).count();
    std::cout << std::format("sum={} in {:.3f} ms\n", double(s), ms);
}
```

Output (representative):
```text
sum=1500000 in 1.7 ms
```

**Why this works:** `steady_clock` brackets the work; assigning to a `volatile` forces the compiler to actually compute the sum (the as-if rule would otherwise delete an unused result). The exact time varies by machine, but the *method* — bracket, observe, report — is the foundation of all benchmarking. (Compile with `-O2`.)

</details>

**Exercise 31.2 — Cache-friendly vs hostile.** Explain (and if you can, measure) why summing a matrix row-by-row is far faster than column-by-column when it's stored row-major.

<details><summary>Show solution</summary>

Row-major storage places `m[i][0], m[i][1], ...` contiguously in memory. Traversing **row-by-row** walks memory sequentially and usually uses fetched cache lines efficiently. Traversing **column-by-column** jumps `N*sizeof(double)` bytes between accesses, often wasting most of each line and frustrating prefetching. Exact effects depend on dimensions, caches, translation lookaside buffers, and architecture.

Measured on a 4000×4000 matrix (`-O3`):
```text
row-major:    ~27 ms
column-major: ~282 ms   (~10x slower)
```

**Why this works:** the computation and result are *identical* — only the memory access order differs. On memory-bound scientific code the access pattern, not the arithmetic, sets the speed. Store and traverse data so that your innermost loop walks memory contiguously (Chapter 25's layout advice).

</details>

### Chapter project: optimizing the histogram fill

> 🛠️ **Chapter Project** — Optimizes the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–31. Filling histograms with millions of events is a hot path. We measure a naive fill, then optimize it — *measuring* each step.

**Goal.** Benchmark filling a histogram with 10 million events, apply `reserve` + contiguous layout, and report the speedup — following "measure first."

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
#include <chrono>
#include <random>

using Clock = std::chrono::steady_clock;
double ms_since(Clock::time_point t) {
    return std::chrono::duration<double, std::milli>(Clock::now() - t).count();
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v26 — optimized fill ===\n";
    const int N = 10'000'000;
    const int bins = 100;
    const double lo = 80.0, hi = 100.0, w = (hi - lo) / bins;

    // Generate events once (contiguous vector)
    std::vector<double> events;
    events.reserve(N);                                   // reserve: one allocation
    std::mt19937 gen(42);
    std::normal_distribution<double> dist(91.2, 2.5);
    for (int i = 0; i < N; ++i) events.push_back(dist(gen));

    // Fill: a flat, contiguous histogram array, sequential pass over events
    auto t0 = Clock::now();
    std::vector<long> hist(bins, 0);                     // contiguous counters
    long in_range = 0;
    for (double e : events) {                            // sequential -> cache-friendly
        if (e >= lo && e < hi) { ++hist[static_cast<int>((e - lo) / w)]; ++in_range; }
    }
    double fill_ms = ms_since(t0);

    // Find the peak bin
    int peak = 0; for (int b = 1; b < bins; ++b) if (hist[b] > hist[peak]) peak = b;
    std::cout << std::format("filled {} events in {:.1f} ms ({:.0f} M events/s)\n",
                             N, fill_ms, N / fill_ms / 1000.0);
    std::cout << std::format("in range: {}, peak bin {} [{:.1f}-{:.1f}] with {} events\n",
                             in_range, peak, lo + peak*w, lo + (peak+1)*w, hist[peak]);
}
```

Output (representative — timing varies by machine):

```text
=== Monte Carlo Analysis Toolkit v26 — optimized fill ===
filled 10000000 events in 26.6 ms (376 M events/s)
in range: 9997722, peak bin 56 [91.2-91.4] with 319468 events
```

**Commentary.**
- Every optimization here is from this chapter, and each is *measured*: **`reserve(N)`** avoids ~24 reallocations while generating events; the histogram is a **flat contiguous `vector<long>`** (Chapter 25) so the fill loop's `++hist[bin]` hits cache well; the pass over `events` is **sequential** (cache-friendly, §31.2, and auto-vectorizable-friendly). At `-O2` this fills **10 million events in ~27 ms — ~370 million events/second** on one core.
- The result is also *correct* physics: 9,997,722 of 10M events land in [80,100], peaking in bin 56 = [91.2, 91.4] around the Z mass — the same distribution the toolkit generated back in Chapter 22, now processed at HPC speed.
- The discipline is the lesson: we didn't guess: we chose contiguous layout and `reserve` *because* §31.2–31.3 showed those are the wins, and we *measured* the throughput to confirm. For a real analysis over billions of events, this per-event cost is what determines whether a study takes minutes or days. Performance work is layout + allocation + measurement — not cleverness.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Cache** | Fast memory between CPU and RAM (L1/L2/L3). |
| **Cache line** | 64-byte block the CPU loads at once. |
| **Locality** | Accessing nearby memory / recently-used data (cache-friendly). |
| **`steady_clock`** | Monotonic clock for measuring durations. |
| **`reserve()`** | Pre-allocate a vector's capacity (avoid reallocation). |
| **Inlining** | Replacing a call with the function body (enables more optimization). |
| **SIMD** | One instruction on multiple values (AVX: 4 `double`s). |
| **Auto-vectorization** | Compiler turning a scalar loop into SIMD (`-O3`). |

### What's next

You can make single-threaded code fast. To use *all* the cores — essential for HPC — you need **[Ch.32 — Concurrency & Parallelism](#chapter-32--concurrency--parallelism)**: threads, the memory model, atomics, data races, and parallel algorithms.

[↑ back to top](#chapter-31--performance--optimization-for-hpc)


---

## Chapter 32 — Concurrency & Parallelism

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.11 — RAII](#chapter-11--dynamic-memory--raii), [Ch.29 — Undefined Behavior](#chapter-29--the-abstract-machine--undefined-behavior), [Ch.31 — Performance](#chapter-31--performance--optimization-for-hpc)

**Learning objectives** — after this chapter you will be able to:

- Launch and join threads with `std::jthread`.
- Recognize data races and prevent them with mutexes and atomics.
- Understand the memory model at a working level.
- Parallelize a computation with a thread-based reduction and `std::async`.

**In this chapter**

- [32.1 Threads](#321-threads)
- [32.2 Data races, mutexes, and atomics](#322-data-races-mutexes-and-atomics)
- [32.3 Parallel reduction](#323-parallel-reduction)
- [32.4 `std::async`, futures, and parallel algorithms](#324-stdasync-futures-and-parallel-algorithms)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-parallel-monte-carlo-integrator)· Glossary · What's next

---

Modern CPUs have many cores; a single-threaded program uses one. For HPC — where a computation may run for hours — **parallelism** across cores is essential. C++ gives you portable threads, synchronization, and a defined memory model. It also gives you the sharpest footgun in the language: the **data race**.

### 32.1 Threads

A **`std::thread`** runs a function on a new OS thread. Since C++20, prefer **`std::jthread`** ("joining thread") — it *automatically joins* in its destructor (RAII, Chapter 11), so you can't forget to join (a bug that terminates the program):

```cpp
#include <thread>
{
    std::vector<std::jthread> workers;
    for (int t = 0; t < 4; ++t)
        workers.emplace_back([t]{ /* work for thread t */ });
}   // each jthread's destructor joins — all work finished here
```

`std::thread::hardware_concurrency()` returns an implementation hint about useful concurrency and may return zero. It can reflect logical CPUs rather than physical cores and ignores affinity, quotas, NUMA, and competing jobs. Use a checked fallback, allow user configuration, and confirm the best worker count by measurement. Compile threaded code with **`-pthread`**.

> ⚙️ **Under the hood** — A thread is an OS-scheduled execution context with its own stack, sharing the process's heap and globals with other threads. Creating one costs microseconds (a system call, stack allocation), so for fine-grained work you *reuse* threads (a pool) rather than spawning per task. The `jthread` also supports cooperative cancellation via `std::stop_token` — a clean way to ask a long-running worker to stop. The shared address space is what makes threads fast to communicate *and* dangerous: two threads touching the same memory is the setup for a data race.

### 32.2 Data races, mutexes, and atomics

A **data race** — two threads accessing the same memory concurrently, at least one writing, with no synchronization — is **undefined behavior** (Chapter 29). Not "sometimes wrong": *undefined*. The classic example, an unsynchronized shared counter:

```cpp
long counter = 0;                          // shared, NOT synchronized
std::vector<std::jthread> ts;
for (int t = 0; t < 4; ++t)
    ts.emplace_back([&]{ for (int i = 0; i < 100000; ++i) ++counter; });   // DATA RACE
// expected 400000 — actual results across runs:
```

```text
racy counter (expected 400000): 147011
racy counter (expected 400000): 187631
racy counter (expected 400000): 204335
```

Observed runs often give different wrong answers, but undefined behavior may also appear correct or fail in unrelated ways. `++counter` is conceptually a read-modify-write; unsynchronized executions can lose updates. The fix is proper synchronization. Two tools:

- **`std::atomic<T>`** — operations on it are indivisible and participate in the memory model. A particular specialization may use lock-free machine instructions or an internal lock; query `is_lock_free()` when that property matters. For a simple counter, it is usually the right tool:

```cpp
std::atomic<long> counter{0};
// ... ++counter from 4 threads ...
// counter.load() == 400000   — always correct
```

- **`std::mutex`** — a lock that only one thread holds at a time; guard a critical section with **`std::lock_guard`** (RAII — unlocks on scope exit):

```cpp
std::mutex m;
{
    std::lock_guard lock(m);     // locks; unlocks at end of scope
    /* exclusive access to shared data */
}
```

> ⚠️ **Gotcha — a data race can *look* like it works.** The racy counter above *sometimes* prints 400000 (especially at `-O2`, or on a lightly loaded machine) — then fails in production under load, or on a different CPU, or after a compiler upgrade. Because it's UB, the compiler may even optimize assuming no race, producing code that can't be reasoned about. **Never** rely on "it printed the right number once." Any shared mutable data touched by multiple threads *must* be synchronized (atomic or mutex) — no exceptions. Detect races with **ThreadSanitizer** (`-fsanitize=thread`), which instruments memory accesses and reports the racing pair.

### 32.3 Parallel reduction

The workhorse pattern for scientific computing: split a big computation across threads, then combine the partial results — a **parallel reduction**. Give each thread its *own* accumulator (no sharing → no race), then sum the partials at the end:

```cpp
const int N = 8'000'000;
std::vector<double> data(N, 1.0);
unsigned nthreads = 4;
std::vector<double> partial(nthreads, 0.0);          // one slot per thread
{
    std::vector<std::jthread> ts;
    int chunk = N / nthreads;
    for (unsigned t = 0; t < nthreads; ++t)
        ts.emplace_back([&, t]{
            int b = t*chunk, e = (t == nthreads-1) ? N : b+chunk;
            double s = 0;
            for (int i = b; i < e; ++i) s += data[i];  // each thread: private sum
            partial[t] = s;                            // writes its OWN slot — no race
        });
}   // join
double total = std::accumulate(partial.begin(), partial.end(), 0.0);
// total == 8000000  (8e+06)
```

Each thread sums a disjoint chunk into a private variable and writes one distinct `partial[t]` — no shared mutable state during the hot loop, so no synchronization needed (the fast path). Only the final combine touches all partials, and that's after every thread has joined. This is the template for parallelizing sums, integrals, histograms, and χ² computations.

> 💡 **Idiom** — Parallelize by **partitioning, not sharing**: give each thread a disjoint slice and a *private* accumulator, then combine after joining. Synchronization (atomics/mutexes) is *expensive* (contention, cache-line bouncing) — the fast parallel code minimizes it by having threads touch independent memory. Share only at the boundaries. A parallel reduction with private partials scales nearly linearly with cores; one where every thread hammers a shared atomic often runs *slower* than single-threaded due to contention.

### 32.4 `std::async`, futures, and parallel algorithms

For fire-and-forget parallel tasks, **`std::async`** runs a function (possibly on another thread) and returns a **`std::future`** — a handle you later `.get()` to retrieve the result (blocking until ready):

```cpp
#include <future>
auto fut = std::async(std::launch::async, []{
    double s = 0; for (int i = 1; i <= 1000; ++i) s += i; return s;
});
double result = fut.get();      // waits for the task, returns 500500
```

The standard library also offers **parallel algorithms**: passing an *execution policy* (`std::execution::par`) to `std::for_each`, `std::reduce`, `std::transform_reduce`, etc. parallelizes them automatically:

```cpp
#include <execution>
double s = std::reduce(std::execution::par, data.begin(), data.end());  // parallel sum
```

This is the *highest-level* parallelism — you express *what* to compute and the library handles the threading. (It requires a parallel backend such as Intel TBB to actually use multiple threads; without one, `par` runs sequentially but the code is correct either way.)

> 💡 **Idiom** — Reach for parallelism at the *highest* level that fits: prefer a **parallel algorithm** (`std::reduce(std::execution::par, ...)`) if it expresses your computation — it's the least code and least error-prone. Drop to **`std::async`/futures** for a few coarse independent tasks. Hand-roll **`jthread` + partitioned reduction** (§32.3) when you need control over chunking, load balancing, or NUMA placement — the HPC case. And always: measure (Chapter 31) — parallelism has overhead, and a well-optimized single-threaded loop can beat a poorly-partitioned parallel one.

---

### Summary

- **`std::jthread`** runs work on another core and *auto-joins* (RAII); size pools with `hardware_concurrency()`; compile with `-pthread`.
- A **data race** (conflicting concurrent accesses without a happens-before relationship) is **undefined behavior**: it may appear correct, produce wrong values, or invalidate reasoning entirely. Prevent simple races with **`std::atomic`** and protect multi-object invariants with **`std::mutex`** + `lock_guard`. Atomics are not guaranteed to be lock-free. Detect races with ThreadSanitizer.
- **Parallel reduction** — partition the data, give each thread a *private* accumulator, combine after joining — is the scalable HPC pattern; it avoids synchronization on the hot path.
- **`std::async`/`future`** run coarse tasks; **parallel algorithms** (`std::execution::par`) parallelize STL algorithms declaratively. Choose the highest level that fits, and *measure*.

### Self-check quiz

1. Why prefer `std::jthread` over `std::thread`?
   <details><summary>Answer</summary>`jthread` auto-joins in its destructor (RAII), so you can't forget to join — a forgotten `join()` on a `std::thread` calls `std::terminate`.</details>
2. What exactly is a data race, and what is its consequence?
   <details><summary>Answer</summary>Two threads accessing the same memory concurrently with at least one writing and no synchronization — it's *undefined behavior* (different wrong results each run, and the compiler may miscompile).</details>
3. When use `atomic` vs `mutex`?
   <details><summary>Answer</summary>`atomic` for indivisible operations on a single value (counters, flags); `mutex` for guarding a multi-step invariant over complex shared state. An atomic specialization may or may not be lock-free.</details>
4. Why does a partitioned reduction scale better than a shared atomic accumulator?
   <details><summary>Answer</summary>Private per-thread accumulators avoid synchronization and cache-line contention on the hot loop; a shared atomic serializes every update and bounces the cache line between cores, often running slower than single-threaded.</details>

### Exercises

**Exercise 32.1 — Atomic vs racy (guided).** Show that an atomic counter gives the correct total from multiple threads.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <thread>
#include <atomic>
#include <vector>
int main() {
    std::atomic<long> counter{0};
    {
        std::vector<std::jthread> ts;
        for (int t = 0; t < 4; ++t)
            ts.emplace_back([&]{ for (int i = 0; i < 100000; ++i) ++counter; });
    }   // all jthreads join here
    std::cout << std::format("counter = {}\n", counter.load());
}
```

Output:
```text
counter = 400000
```

**Why this works:** `std::atomic<long>` makes `++counter` an indivisible read-modify-write with proper synchronization, so no updates are lost — 4 threads × 100000 = exactly 400000, *every* run. Replace `atomic<long>` with a plain `long` and the same program gives a different wrong number each run (a data race). Compile with `-pthread`.

</details>

**Exercise 32.2 — Async result.** Use `std::async` to compute a factorial on another thread and retrieve it via a future.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <future>
int main() {
    auto fut = std::async(std::launch::async, []{
        long f = 1; for (int i = 1; i <= 10; ++i) f *= i; return f;
    });
    std::cout << std::format("10! = {}\n", fut.get());
}
```

Output:
```text
10! = 3628800
```

**Why this works:** `std::async(std::launch::async, ...)` runs the lambda on another thread immediately; `fut.get()` blocks until it finishes and returns the result (10! = 3628800). This is the simplest way to run one coarse task in parallel and collect its result — no manual thread management or synchronization.

</details>

### Chapter project: a parallel Monte Carlo integrator

> 🛠️ **Chapter Project** — Advances the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–32. Monte Carlo integration is *embarrassingly parallel* — each sample is independent. We parallelize it with a partitioned reduction across cores.

**Goal.** Estimate π by Monte Carlo (fraction of random points inside the unit circle) using a multi-threaded partitioned reduction, with each thread using its *own* RNG (no shared state).

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <thread>
#include <vector>
#include <random>
#include <numeric>

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v27 — parallel integrator ===\n";
    const long total = 40'000'000;                 // samples
    const unsigned nthreads = 4;
    std::vector<long> hits(nthreads, 0);           // per-thread count (private slot)

    {
        std::vector<std::jthread> ts;
        long chunk = total / nthreads;
        for (unsigned t = 0; t < nthreads; ++t) {
            ts.emplace_back([&, t]{
                std::mt19937_64 gen(1234 + t);     // each thread: its OWN seeded RNG
                std::uniform_real_distribution<double> u(0.0, 1.0);
                long b = t*chunk, e = (t == nthreads-1) ? total : b+chunk;
                long count = 0;
                for (long i = b; i < e; ++i) {
                    double x = u(gen), y = u(gen);
                    if (x*x + y*y <= 1.0) ++count;  // inside quarter circle
                }
                hits[t] = count;                    // writes its OWN slot — no race
            });
        }
    }   // all threads join

    long inside = std::accumulate(hits.begin(), hits.end(), 0L);
    double pi = 4.0 * static_cast<double>(inside) / total;
    std::cout << std::format("samples: {}, inside: {}\n", total, inside);
    std::cout << std::format("pi estimate = {:.6f}  (true {:.6f}, error {:.2e})\n",
                             pi, 3.141592653589793, pi - 3.141592653589793);
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v27 — parallel integrator ===
samples: 40000000, inside: 31411372
pi estimate = 3.141137  (true 3.141593, error -4.55e-04)
```

**Commentary.**
- Monte Carlo integration is the toolkit's raison d'être, and it's **embarrassingly parallel** — every sample is independent. The partitioned-reduction pattern (§32.3) fits perfectly: each `jthread` runs a disjoint chunk with a **private counter** and, crucially, its **own RNG seeded differently** (`1234 + t`). Sharing one RNG across threads would be both a data race *and* statistically wrong (correlated streams). Private per-thread RNGs are the correct pattern for parallel Monte Carlo.
- No mutex, no atomic on the hot loop — each thread writes only its own `hits[t]`. The single `std::accumulate` combines partials after all threads join. This scales nearly linearly with cores (§32.3's idiom).
- The result: 40 million samples give π ≈ 3.1411, within ~4.5×10⁻⁴ of the true value (Monte Carlo error scales as 1/√N, Chapter 22 — so ~10⁻⁴ at this N is exactly the expected accuracy). On four cores this runs in a fraction of the single-threaded time — the whole point of parallelism for HPC. This is a genuine, correct, parallel scientific kernel: the same structure scales to computing cross-sections, phase-space integrals, or lattice sums on a cluster.
- ⚠️ Reproducibility note (Chapter 33): this result is deterministic *given the seeds and thread count* — but changing `nthreads` changes how samples map to RNG streams, so the estimate shifts slightly. Reproducible parallel Monte Carlo requires fixing both the seeds *and* the decomposition.

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **`std::jthread`** | A thread that auto-joins on destruction (RAII). |
| **Data race** | Concurrent unsynchronized access (≥1 write) — undefined behavior. |
| **`std::atomic`** | A type with indivisible, synchronized operations. |
| **`std::mutex` / `lock_guard`** | A lock guarding a critical section (RAII unlock). |
| **Parallel reduction** | Partition → private accumulators → combine after join. |
| **`std::async` / `future`** | Run a task; retrieve its result later via `.get()`. |
| **`std::execution::par`** | Execution policy parallelizing an STL algorithm. |
| **ThreadSanitizer** | Runtime detector of data races (`-fsanitize=thread`). |

### What's next

You can use all the cores — correctly. The final piece of expertise is *trusting* your results: **[Ch.33 — Testing, Reproducibility & Safety](#chapter-33--testing-reproducibility--safety)** — unit tests, sanitizers as a habit, floating-point determinism, and the discipline that makes scientific software correct and reproducible.

[↑ back to top](#chapter-32--concurrency--parallelism)


---

## Chapter 33 — Testing, Reproducibility & Safety

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** [Ch.3 — Floating Point](#chapter-3--floating-point--numeric-types), [Ch.29 — Undefined Behavior](#chapter-29--the-abstract-machine--undefined-behavior), [Ch.32 — Concurrency](#chapter-32--concurrency--parallelism)

**Learning objectives** — after this chapter you will be able to:

- Write unit tests (arrange–act–assert) and structure a test suite.
- Use sanitizers and static analysis as a routine safety net.
- Understand why floating-point results depend on evaluation order — and how to make computations reproducible.
- Apply the discipline that makes scientific software trustworthy.

**In this chapter**

- [33.1 Unit testing](#331-unit-testing)
- [33.2 Sanitizers and static analysis as habit](#332-sanitizers-and-static-analysis-as-habit)
- [33.3 Floating-point reproducibility](#333-floating-point-reproducibility)
- [33.4 The reproducibility discipline](#334-the-reproducibility-discipline)
- Summary · Self-check quiz · Exercises · [Chapter project](#chapter-project-a-test-suite-for-the-toolkit)· Glossary · What's next

---

A scientific program's failure mode is not a crash — it's a *wrong number in a paper*. Correctness you can't see is the hardest kind to ensure. This final chapter is about the discipline that makes numerical software trustworthy: testing it, hardening it against undefined behavior, and making its results *reproducible*.

### 33.1 Unit testing

A **unit test** runs a small piece of code with known inputs and checks the output against the expected result. The structure is **arrange–act–assert**: set up inputs, call the code, assert the result. A test suite is just a program that runs many such checks and reports pass/fail:

```cpp
int g_pass = 0, g_fail = 0;
void check(bool cond, const std::string& name) {
    if (cond) ++g_pass;
    else { ++g_fail; std::cout << std::format("  FAIL: {}\n", name); }
}
bool close(double a, double b, double tol = 1e-9) {           // FP comparison (Ch.3)!
    return std::fabs(a - b) <= tol * std::max(1.0, std::fabs(b));
}

// ... in main(), testing the toolkit's invariant-mass function:
check(close(inv_mass(5, 3, 0, 4), 0.0), "photon-like (E=|p|) is massless");
check(close(inv_mass(13, 3, 4, 0), std::sqrt(13.0*13 - 25)), "known massive case");
// tests: 3 passed, 0 failed
```

Two things make this a *scientific* test suite: results are compared with a **tolerance** (`close`, never `==` on floats — Chapter 3), and tests encode *physics invariants* (a photon-like four-vector is massless). In real projects use a framework — **Catch2**, **GoogleTest**, or **doctest** — which provides assertions, fixtures, test discovery, and reporting; but the essence is exactly the above.

> 💡 **Idiom** — **Test invariants and known cases, not just "some number."** For numerical code the best tests assert properties that *must* hold: a rotation preserves length, `inv_mass` is frame-independent, `integrate(f)` over a symmetric interval of an odd function is ~0, a probability distribution sums to 1, a matrix times its inverse is the identity. These catch bugs that a single hand-computed expected value would miss, and they document the math. Add a regression test whenever you fix a bug (the case that broke), so it never silently returns. Always compare floats with a tolerance.

### 33.2 Sanitizers and static analysis as habit

Testing checks *outputs*; sanitizers check *undefined behavior* the output might hide (Chapters 11, 29). Make them routine, not a last resort:

- **AddressSanitizer** (`-fsanitize=address`) — out-of-bounds, use-after-free, leaks.
- **UndefinedBehaviorSanitizer** (`-fsanitize=undefined`) — signed overflow, bad casts, misalignment.
- **ThreadSanitizer** (`-fsanitize=thread`) — data races (Chapter 32).
- **Static analysis** (`clang-tidy`, `cppcheck`) — bug patterns found *without running*.
- **Warnings** (`-Wall -Wextra -Wpedantic`, even `-Werror`) — the cheapest analysis, at compile time.

```text
# Run the whole test suite under sanitizers in CI:
$ g++ -std=c++23 -fsanitize=address,undefined -g tests.cpp -o tests && ./tests
```

The winning workflow: a **sanitized Debug build** (Chapter 28) that runs the test suite in CI on every change, plus an optimized Release build for production runs. A memory bug that corrupts one event in a million is invisible in the output but caught instantly by ASan — *if* you run the tests under it.

> ⚙️ **Under the hood** — Sanitizers instrument the program: ASan surrounds every allocation with poisoned "redzones" and maintains shadow memory recording which bytes are valid, trapping any bad access; UBSan inserts checks before risky operations; TSan tracks a "happens-before" graph of memory accesses to spot unsynchronized pairs. This costs ~2× runtime and memory — fine for testing, not for production. That split is the point: pay for safety while *developing and testing*, run the science at full speed. The bugs sanitizers catch (Chapter 29's UB) are exactly the ones that silently corrupt results, so this is where correctness is won.

### 33.3 Floating-point reproducibility

Here is a fact that surprises many scientists: **floating-point addition is not associative** (Chapter 3). `(a + b) + c` can differ from `a + (b + c)`, because each operation rounds. So the *order* in which you sum values changes the result:

```cpp
std::vector<double> v{1.0, 1e20, -1e20};    // same values, summed two ways
double fwd = 0; for (double x : v) fwd += x;                // front to back
double rev = 0; for (auto it = v.rbegin(); it != v.rend(); ++it) rev += *it;
```

```text
forward sum = 0
reverse sum = 1
equal? false
```

*Identical inputs, identical mathematics, different results* — 0 vs 1 — purely from summation order. In forward order the `1.0` is swallowed by `1e20` and never recovered; in reverse, `1e20` and `-1e20` cancel first, leaving the `1.0`. This is why parallel reductions (Chapter 32), which sum partial results in a nondeterministic order, can give run-to-run variation — and why **bitwise reproducibility** requires fixing the evaluation order.

> ⚠️ **Gotcha — `-ffast-math` breaks reproducibility (and standards).** The `-ffast-math` flag lets the compiler *reassociate* and *approximate* floating-point freely (treating it as if it were real arithmetic) — often a nice speedup, but it silently changes results, breaks `NaN`/`Inf` handling, and can make the same source give different answers at different optimization levels. For reproducible scientific code, **do not** use `-ffast-math` (or use it only on kernels you've validated). If you need a deterministic sum, fix the order (sequential accumulation, or a stable tree reduction) and consider **Kahan summation** (Chapter 3) to reduce the rounding error itself.

### 33.4 The reproducibility discipline

Reproducibility — same inputs producing the same outputs, by you and by others — is a scientific *obligation*, and in C++ it takes deliberate effort:

- **Fix random seeds** explicitly (Chapter 22); a Monte Carlo result is only reproducible if the seed *and* the RNG engine are pinned. In parallel, fix the seeds *and* the decomposition (Chapter 32).
- **Pin the evaluation order** for reductions where bitwise identity matters; document where you accept nondeterminism (e.g. parallel sums) and its magnitude.
- **Record the environment**: compiler and version, flags (especially `-O` level and math flags), library versions, hardware. The *same source* can give different results under a different compiler or `-march` (different SIMD, different FP contraction).
- **Control FP contraction**: fused multiply-add (`a*b+c` in one rounding) changes low bits; `-ffp-contract=off` disables it for cross-platform bit-identity.
- **Version everything** and **test continuously**: pin dependencies, run the sanitized test suite in CI, add a regression test per bug.

> 💡 **Idiom** — Treat a scientific result as **reproducible-by-construction**: pin the seed, the compiler/flags, the library versions, and the parallel decomposition; compare floats with tolerances; and gate every change behind a sanitized test suite. When a collaborator (or you, in a year) reruns the analysis, they should get the same numbers — or an explicitly documented, bounded difference. This discipline is what separates code that *produced* a result from code that can *defend* it. It is the culmination of everything in this book: correct types (Ch.2–3), safe memory (Ch.11–14), sound abstractions (Ch.15–20), robust errors (Ch.21), fast kernels (Ch.31), correct parallelism (Ch.32) — all in service of a number you can trust and reproduce.

---

### Summary

- **Unit tests** (arrange–act–assert) check outputs against known results; for numerical code, **test invariants and known cases** and compare floats with a **tolerance**, never `==`. Use Catch2/GoogleTest/doctest in practice.
- Make **sanitizers** (address/undefined/thread) and **static analysis** *routine* — run the test suite under them in CI. They catch the UB (Chapter 29) that silently corrupts results.
- **Floating-point addition isn't associative** — summation *order* changes the result (0 vs 1 in the demo). Parallel reductions vary run-to-run; **`-ffast-math` breaks reproducibility**.
- **Reproducibility takes deliberate effort**: fix seeds and decomposition, pin evaluation order and FP contraction, record compiler/flags/versions, and gate changes behind a sanitized test suite.

### Self-check quiz

1. Why must numerical tests use a tolerance instead of `==`?
   <details><summary>Answer</summary>Floating-point results carry rounding error (Chapter 3), so mathematically-equal values rarely compare bit-equal; tests assert `|a-b| ≤ tolerance` instead.</details>
2. Why run the test suite under sanitizers?
   <details><summary>Answer</summary>Tests check outputs, but undefined behavior (out-of-bounds, use-after-free, races, overflow) can corrupt results invisibly; sanitizers catch that UB at runtime with precise diagnostics.</details>
3. Why can the *same* summation give different results?
   <details><summary>Answer</summary>Floating-point addition isn't associative — each operation rounds, so the order of additions changes the result; parallel/reordered sums therefore vary.</details>
4. Name three things you must pin for a reproducible Monte Carlo result.
   <details><summary>Answer</summary>The RNG seed and engine, the compiler and flags (optimization/math), and — in parallel — the thread decomposition (plus library versions and FP-contraction settings).</details>

### Exercises

**Exercise 33.1 — A tiny test suite (guided).** Write a `check` harness and test that a `normalize(v)` function (dividing a vector by its norm) produces a unit-length result.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <array>
int g_pass = 0, g_fail = 0;
void check(bool c, const std::string& n) {
    if (c) ++g_pass; else { ++g_fail; std::cout << std::format("  FAIL: {}\n", n); }
}
double norm(std::array<double,3> v) { return std::sqrt(v[0]*v[0]+v[1]*v[1]+v[2]*v[2]); }
std::array<double,3> normalize(std::array<double,3> v) {
    double n = norm(v); return {v[0]/n, v[1]/n, v[2]/n};
}
int main() {
    auto u = normalize({3.0, 0.0, 4.0});
    check(std::fabs(norm(u) - 1.0) < 1e-12, "normalized vector has unit length");
    check(std::fabs(u[0] - 0.6) < 1e-12, "x component is 3/5");
    std::cout << std::format("tests: {} passed, {} failed\n", g_pass, g_fail);
}
```

Output:
```text
tests: 2 passed, 0 failed
```

**Why this works:** the tests assert an *invariant* (`norm(normalize(v)) == 1`, the defining property) and a known value (3/5/0/4 triangle → x = 0.6), both with a tolerance — the correct way to test numerical code. A bug in `normalize` (e.g. forgetting to divide one component) would fail the unit-length check immediately.

</details>

**Exercise 33.2 — Order-dependent sum.** Demonstrate that summing the same values in two orders can give different results.

<details><summary>Show solution</summary>

```cpp
#include <iostream>
#include <format>
#include <vector>
int main() {
    std::vector<double> v{1.0, 1e20, -1e20};
    double fwd = 0; for (double x : v) fwd += x;
    double rev = 0; for (auto it = v.rbegin(); it != v.rend(); ++it) rev += *it;
    std::cout << std::format("forward = {}, reverse = {}, equal? {}\n",
                             fwd, rev, fwd == rev);
}
```

Output:
```text
forward = 0, reverse = 1, equal? false
```

**Why this works:** forward, `1.0 + 1e20` rounds to `1e20` (the 1 is below the precision of 1e20), then `- 1e20` gives 0. Reverse, `-1e20 + 1e20` cancels to 0 first, then `+ 1.0` gives 1. Same numbers, same math, different result — floating-point addition is not associative. This is why reproducible code must control summation order and why `-ffast-math` (which reorders freely) breaks determinism.

</details>

### Chapter project: a test suite for the toolkit

> 🛠️ **Chapter Project** — Completes the **Monte Carlo Analysis Toolkit**. **Builds on:** Ch.1–33 — the whole book. We give the toolkit a real test suite: physics-invariant tests, a regression test, and reproducibility checks — the final guarantee that its numbers can be trusted.

**Goal.** A self-contained test program that validates the toolkit's core computations against physics invariants and known values, reporting pass/fail — runnable under sanitizers in CI.

<details><summary>Show reference solution + commentary</summary>

```cpp
#include <iostream>
#include <format>
#include <cmath>
#include <vector>
#include <string>
#include <random>

// ---- functions under test (the toolkit's core, from earlier chapters) ----
double inv_mass(double E, double px, double py, double pz) {       // Ch.17
    double m2 = E*E - (px*px + py*py + pz*pz);
    return m2 > 0 ? std::sqrt(m2) : 0.0;
}
double mean(const std::vector<double>& v) {                        // Ch.9,19
    if (v.empty()) return 0.0;
    double s = 0; for (double x : v) s += x; return s / v.size();
}

// ---- test harness ----
int g_pass = 0, g_fail = 0;
void check(bool cond, const std::string& name) {
    if (cond) ++g_pass;
    else { ++g_fail; std::cout << std::format("  FAIL: {}\n", name); }
}
bool close(double a, double b, double tol = 1e-9) {
    return std::fabs(a - b) <= tol * std::max(1.0, std::fabs(b));
}

int main() {
    std::cout << "=== Monte Carlo Analysis Toolkit v28 — test suite ===\n";

    // 1. Physics invariants
    check(close(inv_mass(5, 3, 0, 4), 0.0), "massless: E=|p| gives m=0");
    check(close(inv_mass(91.1876, 0, 0, 0), 91.1876), "rest frame: m = E");
    // frame independence: boost a particle, mass is invariant
    double E = 100, pz = 60, m_rest = inv_mass(E, 0, 0, pz);
    double g = 1.2, bg = std::sqrt(g*g - 1);                        // a Lorentz boost
    double E2 = g*E + bg*pz, pz2 = bg*E + g*pz;
    check(close(inv_mass(E2, 0, 0, pz2), m_rest, 1e-9), "invariant mass is frame-independent");

    // 2. Statistics known cases
    check(close(mean({1, 2, 3, 4, 5}), 3.0), "mean of 1..5 is 3");
    check(mean({}) == 0.0, "mean of empty is 0 (guarded)");

    // 3. Reproducibility: same seed -> same Monte Carlo result
    auto run = [](unsigned seed) {
        std::mt19937 gen(seed);
        std::normal_distribution<double> d(91.2, 2.5);
        std::vector<double> s; for (int i = 0; i < 1000; ++i) s.push_back(d(gen));
        return mean(s);
    };
    check(run(42) == run(42), "same seed reproduces exactly");
    check(run(42) != run(43), "different seed differs");

    // 4. Regression test (a bug we once fixed: spacelike must guard to 0, not NaN)
    check(inv_mass(1, 2, 0, 0) == 0.0 && !std::isnan(inv_mass(1, 2, 0, 0)),
          "regression: spacelike four-vector guarded, not NaN");

    std::cout << std::format("\ntests: {} passed, {} failed\n", g_pass, g_fail);
    return g_fail == 0 ? 0 : 1;                    // non-zero exit fails CI
}
```

Output:

```text
=== Monte Carlo Analysis Toolkit v28 — test suite ===

tests: 8 passed, 0 failed
```

**Commentary.**
- The suite tests the toolkit the *right* way — by **physics invariants**, not magic numbers. The strongest test is **frame independence**: we compute a particle's mass, apply a real Lorentz boost, recompute, and assert the mass is unchanged (to 10⁻⁹). A bug in `inv_mass` that happened to give the right answer in the rest frame would fail this — invariant tests catch what point tests miss.
- It includes a **reproducibility check** (same seed → *identical* result, `==` is valid here because the computation is deterministic given the seed) and a **regression test** for a real bug from earlier chapters (the spacelike guard returning 0 instead of `NaN`). Every fixed bug should leave such a test behind.
- It returns a **non-zero exit code on failure**, so CI fails the build — and it's designed to run under **`-fsanitize=address,undefined`** (Chapter 28), so the same run that checks outputs also checks for the UB that could corrupt them.
- This is the capstone: the toolkit we built from a `main()` printing an energy (Chapter 1) is now a tested, reproducible, sanitized numerical library — generate (Ch.22), analyze (Ch.19), integrate (Ch.23), parallelize (Ch.32), persist (Ch.27), and *verify* (here). That full arc — from a first program to trustworthy scientific software — is exactly what "zero to expert" means. **You've arrived.**

</details>

### Glossary

| Term | Meaning |
|------|---------|
| **Unit test** | A check of code with known inputs vs expected output. |
| **Arrange–act–assert** | Set up, call, verify — the test structure. |
| **Tolerance** | Allowed difference when comparing floats (never `==`). |
| **Invariant test** | Asserts a property that must always hold (e.g. mass is frame-independent). |
| **Regression test** | A test for a specific fixed bug, so it can't return. |
| **Sanitizer** | Runtime UB/memory/race detector (address/undefined/thread). |
| **Non-associativity** | `(a+b)+c ≠ a+(b+c)` for floats — order matters. |
| **`-ffast-math`** | Flag that reorders/approximates FP — breaks reproducibility. |
| **Reproducibility** | Same inputs → same outputs (pinned seed/flags/order). |

### What's next

This closes Part 5, but not the journey. You now have the arc from a first `main()` to a tested, reproducible, parallel scientific toolkit and can reason down to the abstract machine. Parts 6 and 7 continue into production HPC, systems engineering, adversarial verification, and release discipline.

[↑ back to top](#chapter-33--testing-reproducibility--safety)


---

## Chapter 34 — Object Lifetime, Layout, Casts & ABI

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.10–15, Ch.29

**Learning objectives** — reason about object lifetime, detect dangling views, use casts deliberately, inspect layout, and design ABI-conscious library boundaries.

### 34.1 Lifetime is not storage

Storage is bytes; an object's **lifetime** is the interval in which those bytes contain a live object of a particular type. A pointer can still contain an address after the object's lifetime ends, but dereferencing it is invalid.

```cpp
#include <string_view>

std::string_view bad_label() {
    std::string s = "muon";
    return s;                 // view escapes; s dies on return
}
```

The same hazard affects `span`, iterators, lambda reference captures, and pointers into a `vector` invalidated by reallocation. An owning return value is safe:

```cpp
std::string label() { return "muon"; } // moved/elided efficiently
```

> 💡 **Idiom** — Every non-owning type needs a visible lifetime contract. Prefer a view as a short-lived parameter; be cautious storing it as a member or returning it.

### 34.2 Value categories and temporary lifetime

An lvalue identifies a persistent object; a prvalue computes a value; an xvalue identifies an object whose resources may be reused. A `const T&` can extend the lifetime of a directly bound temporary, but returning a reference to a local never does.

```cpp
const std::string& ok = std::string{"event-42"}; // lifetime extended to ok's scope

const std::string& broken() {
    std::string local = "gone";
    return local;                                // dangling reference
}
```

### 34.3 Alignment, padding, and representation

Compilers insert padding to meet alignment requirements. Never serialize a struct by dumping its raw bytes: padding may be indeterminate, endianness differs, and layout changes with compiler options.

```cpp
struct Sample { char valid; double energy; };
static_assert(alignof(Sample) >= alignof(double));
```

Use `sizeof`, `alignof`, and `offsetof` only where their rules apply. Use `std::bit_cast` for same-sized trivially copyable representations, and `std::memcpy`/explicit field encoding for portable binary data.

### 34.4 Casts and type punning

- `static_cast` performs checked-at-compile-time conversions and explicit numeric narrowing.
- `dynamic_cast` performs checked runtime casts in polymorphic hierarchies.
- `const_cast` changes cv-qualification; modifying an originally const object is UB.
- `reinterpret_cast` changes interpretation, not reality; it does not create an object or defeat aliasing rules.

```cpp
if (auto* cal = dynamic_cast<Calorimeter*>(sensor)) cal->calibrate();
auto bits = std::bit_cast<std::uint64_t>(energy); // inspect a double's representation
```

### 34.5 ABI and PImpl

An ABI covers name mangling, calling conventions, exception/runtime conventions, and object layout. Changing private data members can break clients of a binary library. PImpl moves representation behind a stable pointer:

```cpp
class Analyzer {
public:
    Analyzer();
    ~Analyzer();
    Analyzer(Analyzer&&) noexcept;
    Analyzer& operator=(Analyzer&&) noexcept;
    void run(std::span<const double>);
private:
    struct Impl;
    std::unique_ptr<Impl> impl_;
};
```

Define the destructor in the `.cpp` after `Impl` is complete. PImpl improves binary stability and build isolation, at the cost of an allocation and indirection.

### Summary

- Storage duration and object lifetime are different; views are safe only while their referent lives and remains valid.
- Layout contains implementation choices; serialize fields, not object bytes.
- Casts document distinct operations; `reinterpret_cast` is not a general conversion tool.
- ABI-stable libraries hide changeable representation and test compatibility explicitly.

### Self-check quiz

1. Why can a non-null `span` still be invalid? <details><summary>Answer</summary>Its owner may have died or reallocated; address and lifetime are separate facts.</details>
2. Does `reinterpret_cast<T*>` start a `T` lifetime? <details><summary>Answer</summary>No. It only converts a pointer value; lifetime and aliasing rules still apply.</details>

### Exercises

Audit every `span`, `string_view`, iterator, and reference member in the toolkit. For each, write down its owner and invalidation events. Then replace one unsafe returned view with an owning value and verify it under ASan.

### Chapter project: a stable analysis API

Split `Analyzer` into a public PImpl header and private implementation. Build a shared library, link a client, then add a private cache without changing the public class layout.

### Glossary

| Term | Meaning |
|---|---|
| Lifetime | Interval in which storage contains a live object. |
| Padding | Unnamed bytes inserted for alignment. |
| ABI | Binary contract between compiled components. |
| PImpl | Private implementation hidden behind an owning pointer. |

---

## Chapter 35 — Advanced Templates, Deduction & Perfect Forwarding

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.16, 20, 30, 34

**Learning objectives** — master deduction, forwarding references, specialization, dependent names, and readable generic interfaces.

### 35.1 Deduction transforms types

For a by-value parameter, top-level `const` and references are discarded. For `T&`, the argument must be an lvalue. For forwarding `T&&`, an lvalue argument deduces `T` as an lvalue reference and reference collapsing preserves it.

```cpp
template<class T> void by_value(T);
template<class T> void by_ref(T&);
template<class T> void forward_to_sink(T&& x) {
    sink(std::forward<T>(x));
}
```

`std::move(x)` always casts toward an rvalue; `std::forward<T>(x)` preserves how the caller supplied `x`. Forward only a forwarding reference, and normally forward it once.

### 35.2 Perfect construction

```cpp
template<class T, class... Args>
requires std::constructible_from<T, Args...>
std::unique_ptr<T> make_owned(Args&&... args) {
    return std::unique_ptr<T>(new T(std::forward<Args>(args)...));
}
```

This is educational; production code uses `std::make_unique`. The pattern explains `emplace`, factories, and wrappers that add logging without forcing copies.

### 35.3 Overload resolution, ADL, and customization

Unqualified calls also search namespaces associated with argument types (**ADL**). This enables generic `swap`:

```cpp
using std::swap;
swap(a, b); // finds a type-specific swap through ADL, otherwise std::swap
```

Customization-point objects used by ranges are more controlled than adding overloads to `std` (which is generally forbidden except documented specializations).

### 35.4 Specialization and dependent names

Class templates may be partially specialized; function templates may not. Prefer overloading or concepts for functions. In a template, a dependent qualified type needs `typename`, and a dependent member template may need the `template` disambiguator.

```cpp
template<class R>
using value_t = typename R::value_type;

template<class T> struct Storage<T*> { /* pointer policy */ }; // partial specialization
```

### 35.5 Compile-time cost and diagnostics

Templates trade runtime abstraction cost for compilation and binary work. Constrain public APIs, keep implementation helpers private, avoid accidental instantiation, inspect time traces, and use explicit instantiation when a closed set of heavy types dominates build time.

### Summary

- Forwarding references plus `std::forward` preserve the caller's value category.
- ADL supports generic customization but must be used deliberately.
- Partial specialization belongs to class/variable templates; concepts and overloads usually clarify functions.
- Zero runtime overhead does not mean zero compile-time or code-size cost.

### Self-check quiz

1. Why is a named `T&& x` expression an lvalue? <details><summary>Answer</summary>Every named variable is an lvalue expression, regardless of its declared reference type.</details>
2. Why not replace `forward<T>` with `move`? <details><summary>Answer</summary>`move` would steal from lvalue callers; `forward` preserves lvalue/rvalue intent.</details>

### Exercises

Write a logging factory that constructs a `Histogram` from lvalues and rvalues without extra copies. Instrument copy/move constructors and verify the call counts.

### Chapter project: a policy-based accumulator

Create `Accumulator<T, SummationPolicy>` with naive, pairwise, and compensated policies. Constrain policies with a concept requiring `add(T)` and `value()`; benchmark accuracy and speed.

### Glossary

| Term | Meaning |
|---|---|
| Forwarding reference | Deduced `T&&` that can bind lvalues and rvalues. |
| Reference collapsing | Rules reducing combinations such as `T& &&` to `T&`. |
| ADL | Lookup in namespaces associated with argument types. |
| Dependent name | Name whose meaning depends on a template parameter. |

---

## Chapter 36 — Vocabulary Types, Advanced Ranges & Library Design

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** Ch.18–21, 35

**Learning objectives** — model APIs with standard vocabulary types, compose lazy ranges safely, and choose ownership explicitly.

### 36.1 Types communicate states

Use `optional<T>` for absence, `expected<T,E>` for recoverable failure, `variant<A,B>` for a closed set of alternatives, and a polymorphic hierarchy for an open set. `any` erases type when the set is genuinely unknown, but loses compile-time exhaustiveness.

```cpp
using Measurement = std::variant<Energy, Momentum, Missing>;

double magnitude(const Measurement& m) {
    return std::visit([](const auto& x) -> double {
        using T = std::remove_cvref_t<decltype(x)>;
        if constexpr (std::same_as<T, Missing>) return 0.0;
        else return x.value;
    }, m);
}
```

Strong domain types prevent unit mistakes that aliases cannot:

```cpp
struct GeV { double value; };
struct Radians { double value; };
```

### 36.2 Tuples versus named records

`pair` and `tuple` are useful for generic plumbing and short local returns. If fields have domain meaning or persist across an API, prefer a named struct. `std::apply` invokes a callable with tuple elements; structured bindings unpack either form.

### 36.3 Lazy ranges and dangling

Views usually store iterators or references and compute on demand. They avoid allocation but inherit source lifetime.

```cpp
auto calibrated = events
    | std::views::filter([](const Event& e) { return e.valid; })
    | std::views::transform([](const Event& e) { return e.energy * 1.002; });
```

Do not return a view into a local container. Materialize at ownership boundaries with an explicit loop (or `ranges::to` when the implementation provides C++23 support).

### 36.4 Iterator invalidation and complexity contracts

Document whether an operation invalidates references and its complexity. `vector` reallocation invalidates all element handles; erase invalidates from the erased position onward. Node-based containers offer different stability but worse locality. Correct library design treats these as API contracts.

### 36.5 Polymorphic memory resources

`std::pmr` separates allocation strategy from container type. A monotonic resource is effective for phase-based work where all temporary allocations die together:

```cpp
std::array<std::byte, 64 * 1024> arena{};
std::pmr::monotonic_buffer_resource pool{arena.data(), arena.size()};
std::pmr::vector<Event> batch{&pool};
```

The vector must not outlive its resource. Measure before adopting custom allocation; it changes lifetime and thread-safety constraints.

### Summary

- Vocabulary types make invalid states harder to express.
- Views are lazy and usually non-owning; materialize at lifetime boundaries.
- Iterator invalidation and complexity are part of an API's correctness.
- `pmr` can reduce allocation overhead in phase-oriented workloads, with explicit resource lifetime.

### Self-check quiz

1. When is `variant` better than inheritance? <details><summary>Answer</summary>When alternatives form a closed set and exhaustive compile-time visitation is desirable.</details>
2. What does a range pipeline own? <details><summary>Answer</summary>It depends on the view; many own only adaptors and references/iterators into a source.</details>

### Exercises

Replace a stringly typed event status with `variant`. Add an alternative and observe how exhaustive visitation forces every consumer to handle it.

### Chapter project: zero-copy event queries

Expose events as `span<const Event>`, implement lazy filter/transform queries, and provide an explicit `collect()` boundary. Test that no view escapes its dataset.

### Glossary

| Term | Meaning |
|---|---|
| Vocabulary type | Widely understood type expressing an API state or ownership rule. |
| View | Usually lazy, non-owning range adaptor. |
| Invalidation | Event after which a handle may no longer be used. |
| Memory resource | Runtime allocation strategy used by `pmr` containers. |

---

## Chapter 37 — Coroutines, Modules & Modern Program Structure

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.8, 13, 35–36

**Learning objectives** — understand coroutine state machines, write a small generator, and apply modules without confusing them with packaging.

### 37.1 Coroutines are compiler-transformed functions

A function using `co_yield`, `co_await`, or `co_return` can suspend and resume. The compiler typically creates a heap- or caller-allocated **coroutine frame** holding parameters, locals, and resume state. The return type's `promise_type` controls lifecycle.

```cpp
Generator<Event> read_events(std::istream& in) {
    Event e;
    while (read_one(in, e)) co_yield e;
}

for (const Event& e : read_events(file)) analyze(e);
```

The interface is synchronous here: it lazily produces one event at a time without storing the full file. A complete `Generator<T>` must own/destroy its coroutine handle, define initial/final suspension, propagate exceptions, and specify whether yielded references remain valid.

> ⚠️ **Gotcha** — Coroutines do not inherently create threads, asynchronous I/O, or speed. They reorganize control flow. The awaiter and scheduler determine execution.

### 37.2 Cancellation and structured asynchronous work

Cancellation is cooperative. Pass `std::stop_token`, check at bounded intervals, and ensure cleanup is RAII-owned. Avoid detached tasks whose lifetime outlives captured references.

### 37.3 Modules

Modules replace repeated textual inclusion with compiled interfaces and make export boundaries explicit:

```cpp
// toolkit.ixx
export module toolkit;
import <span>;
export double mean(std::span<const double>);

// app.cpp
import toolkit;
```

Compiler and CMake module workflows continue to vary, so keep a tested minimum toolchain. Modules do not replace libraries, package managers, ABI design, or CMake targets; they change language-level dependency handling.

### 37.4 Migration strategy

Start with leaf libraries, eliminate macro-dependent public headers, keep generated build graphs authoritative, and measure clean/incremental builds. Header units can help but inherit macro complexity. Do not mix several experimental module workflows without CI coverage on every supported compiler.

### Summary

- Coroutines are resumable state machines governed by a promise/awaiter protocol.
- Suspension is not parallelism; scheduling and I/O remain separate concerns.
- Modules improve boundaries and build scalability but do not solve packaging or ABI.
- Adopt both features behind measured use cases and a pinned toolchain matrix.

### Self-check quiz

1. Where do locals live while a coroutine is suspended? <details><summary>Answer</summary>In its coroutine frame if they must survive suspension.</details>
2. Does `import` link a library? <details><summary>Answer</summary>No. Build-system targets and the linker still provide compiled definitions.</details>

### Exercises

Implement or use a small generator to stream integers from a large text file. Compare peak memory with reading the whole file into a vector.

### Chapter project: streaming event ingestion

Add a lazy event generator with parse errors represented by `expected`. Support cancellation and test early loop termination for correct frame/resource destruction.

### Glossary

| Term | Meaning |
|---|---|
| Coroutine frame | State retained across suspension. |
| Awaiter | Object defining ready/suspend/resume behavior. |
| Module interface | Compilation unit exporting module declarations. |
| Header unit | Imported form of a header, with compatibility constraints. |

---

## Chapter 38 — The C++ Memory Model & Advanced Concurrency

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.29, 32, 34

**Learning objectives** — reason with happens-before, select memory order, coordinate tasks, and recognize false sharing and lock-free hazards.

### 38.1 Happens-before, not wall-clock time

Two conflicting accesses form a data race unless ordered by **happens-before**. Sequenced-before orders operations within a thread; synchronization such as mutex unlock/lock or release/acquire connects threads. “Thread A probably ran first” proves nothing.

```cpp
std::string payload;
std::atomic<bool> ready{false};

// producer
payload = "complete";
ready.store(true, std::memory_order_release);

// consumer
if (ready.load(std::memory_order_acquire))
    std::cout << payload; // release/acquire publishes payload
```

`seq_cst` is the easiest default for independent atomic state. Weaken ordering only with a documented proof and a benchmark showing value.

### 38.2 Relaxed atomics

`memory_order_relaxed` guarantees atomicity and per-object modification order, not publication of other data. It suits statistics whose exact ordering is irrelevant:

```cpp
counter.fetch_add(1, std::memory_order_relaxed);
```

It does not make a multi-field invariant atomic.

### 38.3 Waiting and coordination

Use `condition_variable` with a predicate because waits can wake spuriously:

```cpp
std::unique_lock lock(mutex);
cv.wait(lock, [&] { return done || !queue.empty(); });
```

C++20 also provides `latch` (one-shot arrival), `barrier` (reusable phases), semaphores (permits), and atomic wait/notify. `jthread` plus `stop_token` supports cooperative cancellation.

### 38.4 False sharing

Independent counters on the same cache line can invalidate each other's caches. Give workers private accumulators, combine later, and when measurement confirms contention consider `alignas(std::hardware_destructive_interference_size)` with a portable fallback. Padding is a measured optimization, not a universal rule.

### 38.5 Lock-free is a specialist tool

Lock-free algorithms must handle lifetime reclamation, ABA, progress guarantees, and memory ordering. Prefer mutexes or established concurrent containers unless profiling identifies a bottleneck and the team can review the proof. “No mutex” is not synonymous with faster or safer.

### Summary

- Happens-before is the foundation of cross-thread visibility.
- Release/acquire publishes prior writes; relaxed atomics do not.
- Predicate-based waits and structured cancellation prevent common coordination bugs.
- False sharing and reclamation can dominate apparently elegant parallel code.

### Self-check quiz

1. Does atomicity of `ready` make `payload` safe automatically? <details><summary>Answer</summary>No; the release/acquire synchronization publishes payload.</details>
2. When is relaxed ordering appropriate? <details><summary>Answer</summary>When only atomicity/modification order of that object matters and no other data is published through it.</details>

### Exercises

Build the publication example, deliberately replace acquire/release with relaxed, and explain why a successful run is not a proof. Run race-focused tests under TSan.

### Chapter project: bounded analysis queue

Implement a bounded producer/consumer queue with mutex, two condition variables, close semantics, and stop-token cancellation. Test empty/full waits, shutdown, exceptions, and multiple producers.

### Glossary

| Term | Meaning |
|---|---|
| Happens-before | Ordering that makes writes visible and prevents a race. |
| Release/acquire | Synchronization pair publishing preceding operations. |
| Spurious wakeup | Wait returning without the desired condition becoming true. |
| False sharing | Cache contention between independent nearby objects. |

---

## Chapter 39 — Production CMake, Dependencies, Packaging & CI

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** Ch.8, 28, 33

**Learning objectives** — create target-based builds, tests, installable packages, reproducible presets, and a useful CI matrix.

### 39.1 Targets carry usage requirements

Avoid global include directories and flags. Give each target the requirements its consumers need:

```cmake
add_library(toolkit src/histogram.cpp src/analyzer.cpp)
add_library(MCToolkit::toolkit ALIAS toolkit)
target_compile_features(toolkit PUBLIC cxx_std_23)
target_include_directories(toolkit
  PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
         $<INSTALL_INTERFACE:include>)
target_compile_options(toolkit PRIVATE
  $<$<CXX_COMPILER_ID:GNU,Clang>:-Wall;-Wextra;-Wpedantic>)
```

### 39.2 Tests and sanitizers

```cmake
include(CTest)
if(BUILD_TESTING)
  add_executable(toolkit_tests tests/test_histogram.cpp)
  target_link_libraries(toolkit_tests PRIVATE MCToolkit::toolkit)
  add_test(NAME toolkit.unit COMMAND toolkit_tests)
endif()
```

Create sanitizer options as an opt-in interface target rather than writing `CMAKE_CXX_FLAGS`. Keep ASan/UBSan and TSan in separate jobs; combining them is commonly unsupported.

### 39.3 Presets and toolchains

`CMakePresets.json` records generators, cache variables, build/test presets, and CI-friendly names. A toolchain file selects compilers, sysroots, and cross-compilation rules before project configuration. Presets are workflow configuration; toolchains describe a platform.

### 39.4 Dependencies

Prefer installed package configs for system/HPC libraries. `FetchContent` is convenient for small source dependencies but can make offline and supply-chain behavior implicit. Conan and vcpkg can lock dependency graphs; record versions and hashes. Never silently download dependencies during a production cluster build.

### 39.5 Install and export

```cmake
install(TARGETS toolkit EXPORT MCToolkitTargets)
install(DIRECTORY include/ DESTINATION include)
install(EXPORT MCToolkitTargets NAMESPACE MCToolkit::
        DESTINATION lib/cmake/MCToolkit)
```

A complete package also generates version/config files and verifies itself from a separate consumer project. This catches accidental reliance on the source tree.

### 39.6 CI as a risk matrix

Test supported GCC/Clang versions, Debug + sanitizers, Release tests, formatting/static analysis, and at least one clean package-consumer build. Cache dependencies, not stale build directories. Store benchmark trends separately; noisy timing should not be a unit-test assertion.

### Summary

- Modern CMake is target-based and transitive.
- Presets make workflows repeatable; toolchains define platforms.
- Dependency locks and offline behavior are reproducibility requirements.
- Installation is incomplete until an external consumer can `find_package` the result.

### Self-check quiz

1. Why is `PUBLIC` different from `PRIVATE`? <details><summary>Answer</summary>PUBLIC requirements affect the target and its consumers; PRIVATE affects only the target.</details>
2. Why test the installed package externally? <details><summary>Answer</summary>It exposes missing exported usage requirements and source-tree assumptions.</details>

### Exercises

Add presets for debug-sanitized and release builds. Run configure, build, and CTest exclusively through preset names.

### Chapter project: distributable toolkit

Package the toolkit as `MCToolkit::toolkit`, add version/config files, install it to a temporary prefix, and build a five-line external consumer with `find_package(MCToolkit CONFIG REQUIRED)`.

### Glossary

| Term | Meaning |
|---|---|
| Usage requirement | Property propagated through target dependencies. |
| Preset | Named configure/build/test workflow. |
| Toolchain file | Early platform/compiler configuration. |
| Export | Metadata allowing installed targets to be imported. |

---

## Chapter 40 — Performance Engineering: Benchmarking, SIMD & NUMA

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.25, 29, 31, 38

**Learning objectives** — build trustworthy benchmarks, classify bottlenecks, guide vectorization, and reason about topology.

### 40.1 A benchmark is an experiment

Define the question, representative inputs, observable result, warm-up, repetitions, uncertainty, compiler/flags, CPU governor, affinity, and machine metadata. Use Google Benchmark or an equivalent harness for microbenchmarks; use end-to-end workloads for user-visible claims.

```cpp
static void BM_histogram(benchmark::State& state) {
    auto events = make_events(state.range(0));
    for (auto _ : state) {
        auto h = histogram(events);
        benchmark::DoNotOptimize(h);
    }
    state.SetItemsProcessed(state.iterations() * state.range(0));
}
BENCHMARK(BM_histogram)->Range(1 << 10, 1 << 24);
```

Report distributions or confidence intervals, not a single best run. A statistically significant regression may still be operationally irrelevant; define both thresholds.

### 40.2 Roofline reasoning

Arithmetic intensity is operations per byte transferred. A low-intensity kernel is bandwidth-bound; more FLOPs or wider SIMD will not help after memory bandwidth saturates. A compute-bound kernel benefits from vectorization and instruction throughput. Measure bytes, operations, cache misses, bandwidth, and vectorization reports before changing code.

### 40.3 Aliasing and SIMD

Keep hot loops simple, contiguous, and free of hidden dependencies. `std::span` expresses bounds but not non-aliasing. Compiler reports (`-fopt-info-vec`, Clang optimization remarks) explain missed vectorization. Validate numerical changes: reassociation and fused operations can change rounding.

```cpp
for (std::size_t i = 0; i < n; ++i)
    y[i] = a * x[i] + y[i];
```

Portable SIMD facilities and vendor intrinsics are escalation tools, not the first step. Keep a scalar reference implementation and test exceptional values, tails, and alignment.

### 40.4 NUMA and topology

On multi-socket systems, memory is faster for the socket that first touched its pages. Initialize data in parallel with the same placement used for computation, partition work by locality, avoid cross-socket sharing, and benchmark affinity policies. `hardware_concurrency()` cannot describe this topology.

### 40.5 Profile the entire stack

Sampling profilers find hot call paths; hardware counters reveal cycles, instructions, branches, cache misses, and bandwidth; allocation profilers expose churn. Optimize an algorithm before its instructions, and include I/O and synchronization in end-to-end profiles.

### Summary

- Trust benchmarks only when their experimental method is reproducible.
- Roofline analysis distinguishes bandwidth from compute limits.
- SIMD requires dependency/aliasing proofs and numerical validation.
- NUMA placement can dominate scaling beyond one socket.

### Self-check quiz

1. Why might 2× wider SIMD give no speedup? <details><summary>Answer</summary>The kernel may already be limited by memory bandwidth or another bottleneck.</details>
2. Why preserve a scalar implementation? <details><summary>Answer</summary>It is a readable correctness oracle for optimized paths and unusual inputs.</details>

### Exercises

Benchmark histogram throughput over logarithmic dataset sizes. Plot items/s and cache misses; identify where working-set transitions occur.

### Chapter project: performance dossier

Produce a reproducible report for event generation, parsing, histogramming, and reduction, including commands, hardware, compiler, raw results, flame graph, and one justified optimization.

### Glossary

| Term | Meaning |
|---|---|
| Arithmetic intensity | Operations performed per byte transferred. |
| Roofline | Bound combining peak compute and memory bandwidth. |
| NUMA | Memory whose access cost depends on processor location. |
| Affinity | Restriction of work to selected CPUs. |

---

## Chapter 41 — Shared-Memory HPC with OpenMP

> **Level:** Expert/HPC &nbsp;·&nbsp; **Prerequisites:** Ch.32, 38, 40

**Learning objectives** — parallelize loops and reductions, choose data-sharing clauses, schedule irregular work, and measure scaling.

### 41.1 Parallel loops

OpenMP adds structured parallelism through directives:

```cpp
double sum = 0.0;
#pragma omp parallel for reduction(+:sum) schedule(static)
for (std::int64_t i = 0; i < n; ++i)
    sum += f(i);
```

Compile with `-fopenmp`. `reduction` gives each worker private state and combines it safely. Floating-point order differs from serial execution, so compare with a justified tolerance and document reproducibility expectations.

### 41.2 Data environment

Be explicit with `default(none)` in important regions; classify variables as `shared`, `private`, `firstprivate`, or reductions. A shared loop index is a race; a private copy of a large table is a memory disaster. Scope is part of correctness.

```cpp
#pragma omp parallel for default(none) shared(events, partial)
for (std::size_t i = 0; i < events.size(); ++i) { /* ... */ }
```

### 41.3 Scheduling and tasks

`static` has low overhead and predictable placement for uniform work. `dynamic`/`guided` balance irregular iterations at additional scheduling cost. OpenMP tasks express recursive or graph-shaped work; use task groups/dependencies so lifetimes remain structured.

### 41.4 Scaling and affinity

Measure speedup, efficiency, and serial fraction. Strong scaling fixes problem size; weak scaling grows it with workers. Control binding and placement (`OMP_PROC_BIND`, `OMP_PLACES`) and initialize memory in parallel on NUMA nodes. More threads than cores rarely helps CPU-bound kernels.

### Summary

- Reductions express safe parallel accumulation.
- Explicit data-sharing clauses prevent subtle races and copies.
- Scheduling must match workload regularity.
- Scaling claims require thread placement and strong/weak-scaling context.

### Self-check quiz

1. Why can a correct OpenMP sum differ from serial? <details><summary>Answer</summary>Its reduction tree changes floating-point evaluation order.</details>
2. When prefer static scheduling? <details><summary>Answer</summary>For regular work where low overhead and locality matter.</details>

### Exercises

Parallelize Monte Carlo integration using per-thread RNG state. Verify no generator is shared, then plot speedup from one thread to the physical-core count.

### Chapter project: parallel histogram

Give each worker a private padded histogram, merge after the loop, and compare with an atomic-per-bin implementation across narrow and wide histograms.

### Glossary

| Term | Meaning |
|---|---|
| Reduction | Private accumulation followed by a defined combine. |
| Schedule | Policy assigning loop iterations to workers. |
| Strong scaling | Fixed problem size across more workers. |
| Weak scaling | Problem size grows with worker count. |

---

## Chapter 42 — Distributed HPC with MPI

> **Level:** Expert/HPC &nbsp;·&nbsp; **Prerequisites:** Ch.22, 32, 40–41

**Learning objectives** — use ranks, collectives, nonblocking communication, decomposition, and reproducible distributed execution.

### 42.1 Processes and ranks

MPI processes have separate address spaces. Initialize the runtime, obtain rank/size, and finalize through an RAII environment wrapper in real C++ code.

```cpp
MPI_Init(&argc, &argv);
int rank{}, size{};
MPI_Comm_rank(MPI_COMM_WORLD, &rank);
MPI_Comm_size(MPI_COMM_WORLD, &size);
// work
MPI_Finalize();
```

Build with the implementation wrapper (`mpicxx`) or an imported CMake target and launch with the site scheduler (`srun`, `mpirun`, or equivalent).

### 42.2 Collectives

Use `MPI_Bcast`, `Scatter[v]`, `Gather[v]`, and `Reduce/Allreduce` rather than recreating collective algorithms with point-to-point messages.

```cpp
double local = simulate(rank, samples_per_rank);
double global{};
MPI_Reduce(&local, &global, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
```

Collective calls must occur in compatible order on all participating ranks. Counts and datatypes must match actual buffers.

### 42.3 Decomposition and communication

Domain decomposition minimizes boundary data while balancing work. Latency dominates tiny messages; bandwidth dominates large ones. Aggregate communication and overlap useful work with `MPI_Isend`/`MPI_Irecv`, but do not reuse buffers until requests complete.

### 42.4 Failure, I/O, and reproducibility

Seed random streams from a global experiment seed plus a stable stream identifier, not merely current rank if results must survive repartitioning. Record rank count and reduction scheme. Use parallel HDF5/MPI-IO for large shared datasets; avoid thousands of ranks independently writing tiny files.

### Summary

- MPI scales by explicit communication between separate processes.
- Prefer collectives and minimize message count/volume.
- Nonblocking operations require buffer-lifetime discipline.
- Reproducibility must account for decomposition and reduction order.

### Self-check quiz

1. Why is shared-memory reasoning insufficient for MPI? <details><summary>Answer</summary>Ranks normally have distinct address spaces; data moves through communication.</details>
2. When may a nonblocking send buffer be modified? <details><summary>Answer</summary>Only after its request completes.</details>

### Exercises

Implement distributed π estimation with `MPI_Reduce`. Handle remainders so total samples remain exact for every rank count.

### Chapter project: hybrid node/cluster analysis

Use MPI across nodes and OpenMP within each rank. Compare one-rank-per-core and one-rank-per-NUMA-domain layouts, recording affinity and memory use.

### Glossary

| Term | Meaning |
|---|---|
| Rank | Process identifier within a communicator. |
| Collective | Coordinated communication over a communicator. |
| Domain decomposition | Partition of data/work among ranks. |
| Nonblocking operation | Communication represented by a request completed later. |

---

## Chapter 43 — GPU & Accelerator Programming

> **Level:** Expert/HPC &nbsp;·&nbsp; **Prerequisites:** Ch.25, 40–42

**Learning objectives** — map kernels to accelerator execution, manage transfers, avoid divergence, and preserve a portable reference path.

### 43.1 Execution and memory model

GPU programming launches many lightweight work-items grouped for execution. High throughput requires enough parallel work, coalesced memory access, and limited branch divergence. Device memory is distinct on many systems; transfers can dominate a short kernel.

```cpp
// CUDA-style kernel (toolchain-specific)
__global__ void axpy(double* y, const double* x, double a, std::size_t n) {
    auto i = blockIdx.x * blockDim.x + threadIdx.x;
    if (i < n) y[i] += a * x[i];
}
```

### 43.2 Portability choices

CUDA targets NVIDIA deeply; HIP targets AMD/NVIDIA-style ecosystems; SYCL, Kokkos, RAJA, and OpenMP target offload offer different portability/productivity tradeoffs. Choose based on deployed machines, required libraries, debugging maturity, and team expertise—not syntax alone.

### 43.3 Data movement and layout

Batch enough work to amortize launch/transfer cost. Keep data resident across multiple kernels, use SoA when neighboring work-items consume neighboring fields, and overlap transfers with computation only after establishing a correct synchronous baseline.

### 43.4 Numerical validation

Accelerators may use fused operations and different math-library approximations. Test invariants and error envelopes, not bitwise equality by default. Record architecture, driver/runtime, compiler options, and deterministic-mode choices.

### Summary

- Accelerator speed requires massive parallelism and efficient memory access.
- End-to-end speed includes transfers and launch overhead.
- Portability layers trade peak control for multi-backend maintainability.
- A scalar CPU oracle is essential for validation.

### Self-check quiz

1. Why can a fast kernel make an application slower? <details><summary>Answer</summary>Transfer, launch, synchronization, or underfilled-device overhead can exceed saved compute time.</details>
2. What is coalescing? <details><summary>Answer</summary>Neighboring work-items accessing neighboring addresses so transactions are efficient.</details>

### Exercises

Port vector transform and histogram stages to one available accelerator model. Measure transfer-only, kernel-only, and end-to-end time over increasing batch sizes.

### Chapter project: backend-selectable event transform

Define a backend-neutral interface with serial and accelerator implementations. Run the same correctness suite against both and emit a machine-readable benchmark comparison.

### Glossary

| Term | Meaning |
|---|---|
| Kernel | Function executed across accelerator work-items. |
| Divergence | Different control paths within a hardware execution group. |
| Coalescing | Combining neighboring device-memory accesses efficiently. |
| Offload | Moving work/data from host to an accelerator. |

---

## Chapter 44 — Robust Numerical Software

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.3, 21–25, 33, 40

**Learning objectives** — connect conditioning, stability, units, uncertainty, and solver diagnostics to software contracts.

### 44.1 Conditioning versus algorithmic stability

Conditioning describes sensitivity inherent in the mathematical problem; stability describes error introduced by the algorithm. A stable method cannot recover information a badly conditioned problem does not contain. Estimate condition numbers or sensitivity and report them with results.

### 44.2 Scale-aware stopping criteria

Absolute tolerances fail at large scale; relative tolerances fail near zero. Combine both:

```cpp
bool close(double a, double b, double abs_tol, double rel_tol) {
    return std::abs(a - b) <=
           std::max(abs_tol, rel_tol * std::max(std::abs(a), std::abs(b)));
}
```

Tolerances come from measurement uncertainty and model needs, not `epsilon` multiplied by an arbitrary constant. Iterative solvers should return convergence status, iteration count, residual, and reason for termination.

### 44.3 Linear algebra choices

Do not form an inverse to solve `Ax=b`; use a decomposition suited to matrix structure. Cholesky fits symmetric positive-definite systems, pivoted LU handles general dense systems, QR is safer for least squares, and iterative Krylov methods serve large sparse systems. Validate residuals and, where relevant, backward error.

### 44.4 Units and uncertainty

Strong quantity types prevent mixing GeV, MeV, seconds, and meters. Propagate uncertainty analytically when assumptions hold, or with resampling/Monte Carlo when nonlinear behavior matters. Preserve covariance when variables are correlated.

### 44.5 Data and solver provenance

Persist schema version, units, endian/encoding choices, algorithm version, tolerances, seeds, dependencies, and input hashes. Reject incompatible data explicitly. A result without provenance is not reproducible scientific output.

### Summary

- Conditioning belongs to the problem; stability belongs to the method.
- Convergence is a structured result, not just a number.
- Exploit matrix structure and validate residuals.
- Units, uncertainty, schema, and provenance are correctness concerns.

### Self-check quiz

1. Why is machine epsilon not a universal tolerance? <details><summary>Answer</summary>Acceptable error depends on scale, accumulated operations, input uncertainty, and domain requirements.</details>
2. Why avoid explicit matrix inversion for solves? <details><summary>Answer</summary>Factorization-based solves are usually faster and numerically more stable.</details>

### Exercises

Replace one solver's plain `double` return with `expected<Solution, SolverError>` containing residual and iteration metadata. Test non-convergence and non-finite inputs.

### Chapter project: validated fit pipeline

Fit a model with weighted least squares, report covariance and residual diagnostics, serialize provenance, and validate against synthetic data with known parameters.

### Glossary

| Term | Meaning |
|---|---|
| Conditioning | Sensitivity of a problem's answer to input perturbations. |
| Stability | Degree to which an algorithm controls introduced error. |
| Residual | Discrepancy obtained by substituting a computed solution. |
| Provenance | Recorded origin and processing history of a result. |

---

## Chapter 45 — Capstone: A Production Monte Carlo Toolkit

> **Level:** Expert capstone &nbsp;·&nbsp; **Prerequisites:** all previous chapters

**Learning objectives** — integrate architecture, correctness, packaging, performance, and multi-backend execution into one reviewable system.

### 45.1 Repository architecture

```text
monte-carlo-toolkit/
├── CMakeLists.txt
├── CMakePresets.json
├── cmake/MCToolkitConfig.cmake.in
├── include/mct/{event,histogram,analysis,backend}.hpp
├── src/{event_io,histogram,analysis}.cpp
├── apps/mct-analyze.cpp
├── tests/{unit,integration,reproducibility}/
├── benchmarks/
├── backends/{openmp,mpi,gpu}/
└── .github/workflows/ci.yml
```

The core library owns domain logic and exposes value/view types. Backends depend on the core, never the reverse. The command-line app performs configuration and I/O. Tests consume only public APIs where possible.

### 45.2 Explicit pipeline contracts

1. Parse configuration into validated strong types.
2. Select a deterministic RNG stream plan.
3. Ingest or generate bounded event batches.
4. Transform and reduce through a selected backend.
5. Merge using a documented numerical order.
6. Persist results with schema and provenance.

Every boundary states ownership, errors, cancellation, thread safety, numerical tolerance, and complexity. `expected` represents anticipated failures; exceptions represent failures a local operation cannot reasonably handle.

### 45.3 Verification ladder

- Unit tests: bins, parsers, strong units, boundary values.
- Property tests: conservation laws and histogram-count invariants.
- Differential tests: serial oracle versus OpenMP/MPI/GPU.
- Integration tests: installed package and command-line golden metadata.
- Dynamic analysis: ASan/UBSan, separate TSan, leak checks.
- Static analysis and warnings on every change.
- Benchmarks tracked as trends with environment metadata.

### 45.4 Definition of done

The capstone is complete only when a clean machine can configure from a preset, build, test, install, consume with `find_package`, run a documented dataset, and reproduce results within the declared contract. Performance claims include raw data and hardware context. Backend absence degrades cleanly rather than breaking the core build.

### 45.5 Final challenge

Run 10⁸ events using serial and at least one parallel backend. Produce:

- a correctness report comparing counts, moments, and error bounds;
- strong-scaling and throughput plots;
- profiler evidence for the dominant bottleneck;
- a provenance manifest with source revision, compiler, flags, dependencies, hardware, seed plan, and input hashes;
- an installed-package consumer demonstrating that the public API is sufficient.

### Summary

- Expert C++ is the ability to make ownership, lifetime, failure, numerical, and performance contracts explicit.
- HPC expertise connects algorithms to topology and validates scaling with evidence.
- Production quality requires packaging, external consumption, automated analysis, and reproducible outputs.
- The serial implementation remains the clarity and correctness oracle for optimized backends.

### Self-check quiz

1. Why must backends depend on the core rather than vice versa? <details><summary>Answer</summary>It keeps domain correctness portable and allows optional backends without contaminating the public model.</details>
2. What turns a fast demo into a defensible scientific tool? <details><summary>Answer</summary>Explicit contracts, verification across implementations, provenance, packaging, and reproducible performance evidence.</details>

### Exercises

Perform a release review: threat-model malformed input, audit every non-owning view, run all analyzers, build an external consumer, and reproduce one benchmark from only committed instructions.

### Chapter project: release 1.0

Tag a versioned release with changelog, generated package config, documentation, source archive hashes, sample dataset, reproducibility manifest, and a report of known numerical/performance limitations.

### Glossary

| Term | Meaning |
|---|---|
| Differential test | Same workload compared across independent implementations. |
| Backend | Replaceable execution implementation behind a common contract. |
| Provenance manifest | Machine-readable record needed to reproduce a result. |
| Definition of done | Verifiable completion conditions rather than an informal claim. |

---

## Chapter 46 — Allocator Engineering & Transactional Error Safety

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.11–14, 21, 34, 36

**Learning objectives** — distinguish allocation from object lifetime, select and instrument memory resources, state exception guarantees, and implement rollback-safe state changes.

### 46.1 Allocation is a policy, not ownership

An allocator obtains suitably aligned raw storage; construction starts object lifetime in that storage; destruction ends lifetime; deallocation returns storage. Containers own elements even when an external resource supplies their bytes. `std::allocator_traits<A>` is the standard adaptation layer used by allocator-aware containers; custom allocators must obey its propagation, equality, and rebind contracts.

Do not write an allocator merely to wrap `malloc`. First measure allocation count, size distribution, lifetime phases, fragmentation, locality, and contention. General-purpose allocators are difficult to beat for mixed workloads.

### 46.2 Polymorphic memory resources

`std::pmr` lets the same container type select allocation behavior at runtime:

```cpp
#include <array>
#include <cstddef>
#include <memory_resource>
#include <vector>

std::array<std::byte, 1 << 20> storage{};
std::pmr::monotonic_buffer_resource arena{storage.data(), storage.size()};
std::pmr::vector<double> samples{&arena};
samples.reserve(100'000);
```

A monotonic resource allocates cheaply and releases everything as a phase; individual deallocation is intentionally ineffective. `unsynchronized_pool_resource` reuses size-class blocks within one thread; `synchronized_pool_resource` adds synchronization. The resource must outlive every container using it. An upstream resource handles exhaustion; `null_memory_resource()` instead makes a fixed arena fail predictably with `std::bad_alloc`.

To measure rather than guess, derive a forwarding resource:

```cpp
class counting_resource final : public std::pmr::memory_resource {
    std::pmr::memory_resource* upstream_;
public:
    std::size_t bytes{};
    explicit counting_resource(std::pmr::memory_resource* u) : upstream_(u) {}
private:
    void* do_allocate(std::size_t n, std::size_t a) override {
        bytes += n; return upstream_->allocate(n, a);
    }
    void do_deallocate(void* p, std::size_t n, std::size_t a) override {
        upstream_->deallocate(p, n, a);
    }
    bool do_is_equal(const std::pmr::memory_resource& x) const noexcept override {
        return this == &x;
    }
};
```

Alignment is part of the allocation contract. Use aligned `operator new`, `alignas`, or resources; never “fix” alignment by rounding a pointer and then losing the original allocation address.

### 46.3 Exception guarantees

| Guarantee | Contract |
|---|---|
| No-throw | Operation cannot emit an exception; destructors and swaps should normally meet this. |
| Strong | Failure leaves observable state unchanged: commit or rollback. |
| Basic | Invariants hold and resources do not leak, but values may change. |
| None | Even invariants may be lost; avoid at public boundaries. |

Build a new state before committing it:

```cpp
void Dataset::replace(std::span<const double> input) {
    std::vector<double> candidate(input.begin(), input.end()); // may throw
    validate(candidate);                                      // may throw
    values_.swap(candidate);                                  // noexcept commit
}
```

This gives the strong guarantee because all failure-prone work precedes the no-throw commit. Copy-and-swap is a useful pattern, not a universal prescription: it may allocate unnecessarily and can discard storage capacity.

### 46.4 Rollback guards and error channels

RAII scope guards undo partially completed external changes unless committed. Use exceptions when a layer cannot complete its contract and callers may recover at a boundary; use `expected<T,E>` for anticipated local failures that callers inspect; use error codes when interoperability or allocation-free operation requires them. Never allow exceptions to escape a destructor during stack unwinding—terminate would result.

### Summary

- Allocation strategy, ownership, and object lifetime are separate contracts.
- `pmr` is valuable for measurable phase/locality problems, not as decoration.
- Strong exception safety performs fallible work before a no-throw commit.
- Rollback must cover files, locks, transactions, and remote effects—not only memory.

### Self-check quiz

1. Why can moving a `pmr::vector` between unequal resources allocate? <details><summary>Answer</summary>The destination may be required to own elements from its own resource; allocator propagation/equality controls whether storage can transfer.</details>
2. Does `noexcept` prevent throwing? <details><summary>Answer</summary>No. It promises that no exception escapes; violation calls `std::terminate`.</details>

### Exercises

Instrument the toolkit's parsing phase with `counting_resource`; compare default, monotonic, and pool resources using allocation count, peak bytes, wall time, and lifetime tests. Inject allocation failure and verify invariants.

### Chapter project: transactional event import

Import a versioned event file into a temporary arena, validate every record, then atomically replace the live dataset. Test malformed input, injected `bad_alloc`, duplicate IDs, cancellation, and cleanup.

### Glossary

| Term | Meaning |
|---|---|
| Arena | Region whose allocations share a bulk lifetime. |
| Upstream resource | Fallback resource used by another `memory_resource`. |
| Strong guarantee | Failure has no observable effect. |
| Commit point | Final no-fail transition that publishes prepared state. |

---

## Chapter 47 — Debugging, Core Dumps & Program Analysis

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** Ch.8, 21, 29, 32–34

**Learning objectives** — preserve evidence, debug live and crashed processes, diagnose optimized and concurrent programs, and combine debuggers with static/dynamic analysis.

### 47.1 Build debuggable evidence

Use `-g` (preferably `-Og` during investigation), keep the exact executable and separate debug symbols, record source revision and flags, and avoid rebuilding before opening a core. Optimized debugging is possible but variables may be folded, reordered, or absent.

```text
g++ -std=c++23 -Og -g3 -fno-omit-frame-pointer app.cpp -o app
ulimit -c unlimited
gdb ./app core
```

On systemd hosts, `coredumpctl list`, `coredumpctl info PID`, and `coredumpctl debug PID` locate captured crashes. A core may contain credentials and personal data; handle it as sensitive evidence.

### 47.2 GDB/LLDB investigation loop

| Intent | GDB | LLDB |
|---|---|---|
| Start/arguments | `run arg1` | `run -- arg1` |
| Break | `break file.cpp:42` | `breakpoint set -f file.cpp -l 42` |
| Conditional break | `break f if id==7` | `breakpoint set -n f -c 'id==7'` |
| Stack | `bt full`, `frame N` | `bt all`, `frame select N` |
| Data | `print x`, `x/16gx p` | `frame variable x`, `memory read p` |
| Watch change | `watch value` | `watchpoint set variable value` |
| Threads | `info threads`, `thread apply all bt` | `thread list`, `thread backtrace all` |

First reproduce, capture signal/exception, inspect every thread and frame, identify the first corrupted invariant, then work backward. The crash line is often the first detection point, not the original cause.

### 47.3 Memory, races, and deterministic replay

- ASan: out-of-bounds, use-after-free, many lifetime errors.
- UBSan: selected undefined operations.
- TSan: data races; run separately from ASan.
- MSan: uninitialized reads, requiring instrumented dependencies.
- Valgrind Memcheck: slower binary instrumentation useful when sanitizer rebuilds are unavailable.
- `rr record` / `rr replay`: deterministic record/replay on supported Linux targets; reverse-continue to the earlier mutation.

Sanitizers find different classes and do not prove correctness. Keep assertions and minimize a failing input. For deadlocks, collect all-thread stacks twice: threads blocked at the same lock graph are stronger evidence than a single snapshot.

### 47.4 Static analysis as a policy

Enable compiler warnings, then a focused `clang-tidy` profile. Treat diagnostics as reviewed evidence, not a blind rewrite. Use `compile_commands.json`, pin tool versions, suppress with a reason, and measure warning debt.

```cmake
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
target_compile_options(core PRIVATE -Wall -Wextra -Wpedantic -Wconversion)
```

```text
clang-tidy -p build src/event.cpp --checks='bugprone-*,performance-*,cppcoreguidelines-*'
cppcheck --project=build/compile_commands.json --enable=warning,performance,portability
include-what-you-use -p build src/event.cpp
```

### Summary

- Preserve the exact binary, symbols, core, input, environment, and timeline.
- Inspect state and invariants before changing code.
- Debuggers, sanitizers, replay, and static tools answer different questions.
- Optimized or concurrent failures need multiple independent observations.

### Self-check quiz

1. Why keep the original executable with a core? <details><summary>Answer</summary>Addresses, layout, and symbols must match the crashed process.</details>
2. Why can a hardware watchpoint be expensive or unavailable? <details><summary>Answer</summary>CPUs expose only a small number with size/alignment constraints; software watchpoints single-step.</details>

### Exercises

Plant an iterator invalidation, stack-use-after-return, integer overflow, and lock inversion. Diagnose each from evidence with the appropriate tool and write the root cause—not only the failing line.

### Chapter project: crash investigation dossier

Produce a reproducible report containing core backtrace, minimized input, sanitizer confirmation, failing invariant, patch, regression test, and proof that the fix does not merely hide the symptom.

### Glossary

| Term | Meaning |
|---|---|
| Core dump | Snapshot of process memory/register state after failure. |
| Watchpoint | Break when a memory location is accessed or changed. |
| Symbolization | Mapping machine addresses to source names/lines. |
| Record/replay | Capture execution so it can be replayed deterministically. |

---

## Chapter 48 — Property Testing, Fuzzing & Verification Strategy

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.21–23, 33, 44, 47

**Learning objectives** — design a layered test strategy, generate adversarial inputs, shrink failures, test numerical/concurrent code, and assess test-suite strength.

### 48.1 Examples, properties, and oracles

Example tests protect known cases. Property tests generate many cases and assert invariants: sorting is ordered and permutation-preserving; encode/decode round-trips; histogram total weight is conserved. A property still needs domain-valid generators and meaningful bounds.

```cpp
RC_GTEST_PROP(Histogram, ConservesFiniteWeight,
              (const std::vector<double>& xs)) {
    auto h = make_test_histogram();
    for (double x : xs) if (std::isfinite(x)) h.fill(mct::GeV{x});
    RC_ASSERT(h.total_weight() == static_cast<double>(
        std::count_if(xs.begin(), xs.end(), [](double x){ return std::isfinite(x); })));
}
```

RapidCheck is illustrative; Catch2 generators, Hypothesis for cross-language or custom generators can serve the same idea. Shrinking reduces a failing case to a small counterexample.

### 48.2 Coverage-guided fuzzing

Fuzz parsers at a byte boundary and keep the harness deterministic, fast, and side-effect-free:

```cpp
extern "C" int LLVMFuzzerTestOneInput(const std::uint8_t* data, std::size_t size) {
    auto result = parse_event(std::span{data, size});
    if (result) validate(*result);
    return 0;
}
```

```text
clang++ -std=c++23 -g -O1 -fsanitize=fuzzer,address,undefined \
  fuzz_event.cpp parser.cpp -o fuzz_event
./fuzz_event corpus/ -max_total_time=300
```

Seed the corpus with valid and boundary inputs; add dictionaries for structured tokens; persist minimized regressions. AFL++ supports fork-based instrumentation and external targets. Fuzzing proves only explored behavior, not absence of bugs.

### 48.3 Differential, metamorphic, and mutation testing

Compare an optimized backend against a simple independent oracle. When exact output is unknown, use metamorphic relations: scaling all weights scales totals; permuting independent events preserves aggregate results. Mutation testing deliberately alters operators/branches and checks whether tests fail; surviving mutants expose weak assertions or unreachable code.

Golden files are appropriate for stable, reviewed interfaces, but normalize timestamps/order and require intentional review of updates. Do not approve a giant snapshot because “the diff looks noisy.”

### 48.4 Concurrency and numerical testing

Repeat under varied scheduling, worker counts, tiny queue capacities, cancellation points, and TSan. Avoid sleep-based tests; coordinate with barriers/latches and bounded deadlines. Numerical tests distinguish exact identities, error envelopes, statistical goodness-of-fit, and reproducibility contracts. A p-value is not a universal pass/fail oracle; fix significance and multiple-testing policy in advance.

### Summary

- Unit examples, properties, fuzzing, differential tests, and static analysis overlap but do not replace one another.
- Fuzz harnesses need sanitizers, deterministic behavior, corpora, and regression retention.
- Mutation score measures whether tests detect plausible faults, not product quality by itself.
- Numerical and concurrent tests require explicit nondeterminism contracts.

### Self-check quiz

1. Why should a fuzzer harness avoid logging every input? <details><summary>Answer</summary>I/O destroys execution rate and can introduce nondeterministic side effects; report only actionable failures.</details>
2. What does a surviving mutant suggest? <details><summary>Answer</summary>The changed behavior was unobserved, equivalent, or unreachable; investigate rather than chasing the score blindly.</details>

### Exercises

Add round-trip properties and a libFuzzer target for the event format. Seed ten structural cases, run with ASan/UBSan, minimize one synthetic failure, and turn it into a named regression.

### Chapter project: verification matrix

Map each public contract to examples, properties, fuzz targets, static checks, dynamic analysis and production observability. Identify untestable designs and refactor one boundary to expose a deterministic seam.

### Glossary

| Term | Meaning |
|---|---|
| Property test | Generated cases checked against a general invariant. |
| Shrinking | Reducing a generated failure to a minimal counterexample. |
| Fuzz corpus | Retained inputs guiding future exploration. |
| Mutation test | Deliberate code change used to assess test sensitivity. |

---

## Chapter 49 — Evidence-Driven Profiling, PGO & LTO

> **Level:** Expert/HPC &nbsp;·&nbsp; **Prerequisites:** Ch.31, 40, 47

**Learning objectives** — design defensible benchmarks, interpret sampling and hardware counters, use profile-guided/link-time optimization, and reject misleading speedups.

### 49.1 Benchmark method before numbers

Define workload, correctness oracle, build, input, machine state, repetitions and statistic. Separate latency from throughput; include warm-up where caches/JIT-like runtime initialization matter; consume results so the compiler cannot remove work. Report distributions and confidence, not a single best run.

Google Benchmark's `DoNotOptimize` and `ClobberMemory` create compiler barriers, not magical realism. Inspect generated assembly and benchmark the end-to-end path as well as isolated kernels.

### 49.2 Linux profiling workflow

```text
perf stat -r 10 -e cycles,instructions,branches,branch-misses,cache-misses ./mct
perf record -g --call-graph dwarf ./mct
perf report
valgrind --tool=cachegrind ./mct
valgrind --tool=callgrind ./mct
```

`perf stat` counts events; `perf record` samples where time occurs; flame graphs aggregate stacks; Cachegrind models caches and is not the physical CPU. Normalize counters per operation. IPC, miss rate, and branch rate need workload and architecture context.

### 49.3 PGO and LTO

```text
# GCC example
g++ -O3 -fprofile-generate ... -o app
./app representative-workload
g++ -O3 -fprofile-use -fprofile-correction ... -o app
```

PGO uses representative execution to guide layout, inlining and branch decisions; biased training can harm production. LTO optimizes across translation units and may increase link memory/time or expose ODR violations. Benchmark PGO, LTO, and PGO+LTO separately; preserve reproducible profiles or regenerate them in a controlled pipeline.

### 49.4 Optimization decision record

For every accepted optimization record baseline, hypothesis, profiler evidence, code change, correctness comparison, confidence interval, affected hardware, binary-size/build-time cost, and rollback. A 5% microbenchmark gain that adds 20% end-to-end complexity is often a loss.

### Summary

- Profiling locates cost; counters and models explain it; benchmarks validate change.
- Optimizer barriers, warm-up and statistical reporting prevent common illusions.
- PGO is only as representative as its training workload.
- Performance changes require correctness and maintainability evidence.

### Self-check quiz

1. Can high cache-miss count alone prove a cache bottleneck? <details><summary>Answer</summary>No; normalize it, inspect stalled cycles/bandwidth and establish whether misses lie on the critical path.</details>
2. Why can PGO regress a rare path? <details><summary>Answer</summary>The optimizer spends layout/inlining budget according to the observed training distribution.</details>

### Exercises

Profile parsing and histogramming separately and end to end. Produce a flame graph, counter table, one rejected hypothesis, and one optimization with an independently repeated result.

### Chapter project: reproducible performance laboratory

Add pinned Release/PGO/LTO presets, Google Benchmark targets, raw JSON output, hardware metadata, regression thresholds with noise allowance, and a report generator.

### Glossary

| Term | Meaning |
|---|---|
| IPC | Retired instructions per CPU cycle. |
| Sampling profiler | Periodically records execution state to estimate hot paths. |
| PGO | Optimization guided by profiles from representative runs. |
| LTO | Optimization across translation-unit boundaries during linking. |

---

## Chapter 50 — Advanced Concurrency, Lock-Free Memory & Executors

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.32, 38, 46–49

**Learning objectives** — choose synchronization primitives, design bounded work execution, reason about lock-free progress and safe reclamation, and validate shutdown/cancellation.

### 50.1 Prefer structured synchronization

Use the highest-level primitive that expresses the protocol. `latch` is a one-shot countdown; `barrier` is reusable and may run a phase-completion function; `counting_semaphore` represents permits. `atomic::wait/notify` blocks until an atomic changes without a separate condition variable.

```cpp
std::atomic<bool> ready{false};
// consumer
ready.wait(false);
consume();                         // acquire is supplied by the chosen load/RMW protocol
// producer
produce();
ready.store(true, std::memory_order_release);
ready.notify_all();
```

Use an acquire load or acquire-capable wait loop before consuming published data. Spurious wakeups and value changes require a predicate loop. `atomic_ref<T>` applies atomic operations to an existing suitably aligned object, but every concurrent access to that object must follow a compatible atomic protocol.

### 50.2 A bounded thread-pool contract

A production pool defines queue capacity/backpressure, task ownership, exception capture, cancellation, shutdown, worker reentrancy, fairness and observability. An unbounded queue converts overload into memory exhaustion. `std::jthread` and `stop_token` support cooperative cancellation; blocking operations must participate or have a bounded timeout.

```cpp
class executor {
public:
    explicit executor(std::size_t workers, std::size_t capacity);
    std::future<void> submit(std::move_only_function<void(std::stop_token)> task);
    void request_stop() noexcept;
    ~executor();                   // request stop, wake waiters, join
};
```

The interface is a contract sketch: submission must specify whether a full queue blocks, fails, or runs inline. Do not hold the queue mutex while executing user code.

### 50.3 Lock-free is a progress property

Wait-free means every operation finishes in bounded own steps; lock-free means system-wide progress; obstruction-free means progress in isolation. Lock-free is not automatically faster, fairer, or simpler. Compare against a mutex under realistic contention.

The ABA problem occurs when a location changes A→B→A and a compare-exchange mistakes it for unchanged. Tagged pointers/counters can detect some ABA, but safe memory reclamation remains necessary: another thread may still hold the removed node.

### 50.4 Reclamation: the hard part

- Hazard pointers publish which nodes threads may dereference; retired nodes are freed only when unhazarded.
- Epoch-based reclamation frees nodes after all participating threads pass a quiescent epoch.
- Reference counting is simpler for some graphs but has atomic and cycle costs.

Never present a toy Treiber stack that immediately `delete`s a popped node as production lock-free code. Test weak-memory behavior across architectures, run TSan where applicable, and use established libraries when possible.

### 50.5 Work stealing and executors

Work stealing gives workers local deques and lets idle workers steal, improving irregular parallelism. It complicates ordering, affinity, cancellation and deterministic testing. C++ standard execution facilities continue evolving; isolate executor/scheduler dependencies behind your own narrow application contract rather than binding domain code to one experimental API.

### Summary

- Bound queues and make overload behavior explicit.
- Cooperative cancellation requires every blocking boundary to participate.
- Lock-free algorithms need a progress proof and a reclamation scheme.
- Measure synchronization designs under the intended topology and workload.

### Self-check quiz

1. Why does successful compare-exchange not make node deletion safe? <details><summary>Answer</summary>Another thread may already hold a pointer to the removed node; reclamation requires proving no reader can dereference it.</details>
2. What is backpressure? <details><summary>Answer</summary>A bounded mechanism that slows or rejects producers when consumers cannot keep up.</details>

### Exercises

Implement a bounded mutex/condition-variable queue with close, timeout, stop-token cancellation and exception-safe move operations. Prove no lost wakeup with predicate reasoning and stress it under TSan.

### Chapter project: measured executor

Build a fixed pool with bounded submission, futures, cooperative stop, per-worker metrics and deterministic tests. Compare centralized and work-stealing queues for uniform and skewed tasks.

### Glossary

| Term | Meaning |
|---|---|
| Progress guarantee | Formal statement about which operations must eventually finish. |
| ABA | Value returns to an old representation while its history changed. |
| Hazard pointer | Published reference preventing reclamation of a retired node. |
| Backpressure | Flow control when downstream capacity is exhausted. |

---

## Chapter 51 — Coroutines, Event Loops & Network Programming

> **Level:** Expert/Systems &nbsp;·&nbsp; **Prerequisites:** Ch.7, 21, 32, 37–38, 50

**Learning objectives** — understand coroutine lowering and lifetime, implement framed TCP safely, integrate nonblocking I/O, TLS, timeouts, cancellation and backpressure.

### 51.1 Coroutine mechanics beyond syntax

A coroutine call allocates or embeds a frame containing parameters, locals, promise and suspension state. The return type's `promise_type` controls construction, initial/final suspension, yielded/returned values and unhandled exceptions. An awaiter supplies `await_ready`, `await_suspend`, and `await_resume`.

```cpp
struct suspend_once {
    bool await_ready() const noexcept { return false; }
    void await_suspend(std::coroutine_handle<> h) const noexcept { schedule(h); }
    void await_resume() const noexcept {}
};
```

`await_suspend` transfers continuation responsibility to a scheduler. Destroying a live frame too early dangles state; never resume a completed/destroyed coroutine. Symmetric transfer can return another handle from `await_suspend` to avoid recursive resume chains. Cancellation is a protocol, not automatic destruction.

### 51.2 TCP is a byte stream

One `send` is not one `recv`; both may transfer fewer bytes. Define framing such as fixed header + length-prefixed payload, cap lengths before allocation, and loop on partial I/O. Handle zero-byte read as orderly peer close.

```cpp
std::expected<Message, NetError> read_frame(Socket& s) {
    std::array<std::byte, 4> header{};
    TRY(read_exact(s, header));
    const auto n = decode_u32_be(header);
    if (n > max_frame_size) return std::unexpected(NetError::oversized);
    std::vector<std::byte> body(n);
    TRY(read_exact(s, body));
    return decode_message(body);
}
```

`TRY` is pseudocode for local expected-propagation; define it or spell the checks in buildable code. Network byte order is big-endian. UDP preserves datagrams but may drop, duplicate or reorder them and has practical size limits.

### 51.3 Nonblocking readiness

`select` is portable but limited; `poll` scales linearly; Linux `epoll` and BSD/macOS `kqueue` provide scalable readiness. Readiness means an operation may make progress—not that a whole message is ready. Edge-triggered loops drain until `EAGAIN`; level-triggered APIs keep reporting while work remains.

Boost.Asio supplies portable asynchronous operations, timers and executors. Keep an operation's buffers and owning session alive through completion. Serialize per-connection mutation using a strand or explicit protocol.

### 51.4 Timeouts, retries, TLS, and overload

Apply deadlines to connect, handshake, read, write and idle phases; cancel the losing operation in a timeout race. Retry only idempotent/replay-safe work, use exponential backoff with jitter, and cap attempts. A reconnect loop without backpressure creates a retry storm.

TLS authenticates peers and protects transport when certificate/hostname verification is enabled. Configure trust roots, protocol minimums and server identity; never “fix” a certificate error by disabling verification. OpenSSL is stateful and often reports WANT_READ/WANT_WRITE during nonblocking handshakes.

### Summary

- Coroutine frames and continuations have explicit ownership and cancellation rules.
- TCP requires framing, bounded lengths and partial-I/O loops.
- Readiness and asynchronous completion are different models.
- Deadlines, TLS verification, backpressure and retry safety are part of protocol correctness.

### Self-check quiz

1. Why may a writable socket still not accept a full frame? <details><summary>Answer</summary>Readiness promises some progress; kernel buffer capacity can be smaller than the pending data.</details>
2. Who owns a suspended coroutine? <details><summary>Answer</summary>The design must say: return object, scheduler, or another structured owner; otherwise leaks/double-destruction are likely.</details>

### Exercises

Implement a blocking length-prefixed echo protocol first, including fragmented reads and oversized rejection. Then port it to Asio with per-operation deadlines and a bounded outgoing queue.

### Chapter project: secure event ingestion service

Build a TLS server that accepts versioned event batches, validates frames, enforces size/rate limits, supports graceful stop, exposes queue/latency metrics, and fuzzes its decoder independently of the network.

### Glossary

| Term | Meaning |
|---|---|
| Coroutine frame | Stored state of a suspended coroutine. |
| Framing | Protocol that separates messages on a byte stream. |
| Readiness | Notification that an I/O operation can probably progress. |
| Strand | Serialized execution context for handlers. |

---

## Chapter 52 — Serialization, Schemas & Scientific Data Systems

> **Level:** Advanced → Expert &nbsp;·&nbsp; **Prerequisites:** Ch.27, 34, 44, 48, 51

**Learning objectives** — design portable formats, evolve schemas, validate hostile data, choose serialization/storage systems, and use memory mapping safely.

### 52.1 A file format is a long-lived protocol

Never dump a C++ object representation: it contains padding, implementation-defined layout and host endianness, and may hold pointers. Encode fields explicitly with magic, format version, lengths, units and integrity metadata.

```text
magic[4] = "MCT1"
u16 format_version (big-endian)
u16 flags
u64 record_count
u32 header_crc
records: [u32 length][u16 type][payload][u32 crc]
```

Check arithmetic before allocating: validate `count <= max`, `length <= remaining`, and multiplication without overflow. Put global and per-record limits in the contract.

### 52.2 Text and binary choices

JSON is inspectable and ecosystem-rich but ambiguous without a schema and weak for large arrays. Protocol Buffers support tagged fields and forward/backward evolution; FlatBuffers/Cap'n Proto favor direct access with different validation/lifetime tradeoffs; MessagePack/CBOR are compact generic trees. HDF5 provides typed multidimensional datasets, metadata, chunking, compression and parallel variants. ROOT integrates columnar scientific data and analysis workflows.

Choose based on interoperability, evolution, random access, streaming, compression, tooling and corruption model—not smallest demo.

### 52.3 Schema evolution

Add fields with defaults, retain stable field IDs, ignore unknown optional fields, and never silently reinterpret an old field. Removing/reusing an ID is usually breaking. Separate format version from application release. Migrations must be testable from every supported version and preserve units/provenance.

Checksums detect accidental corruption, not malicious tampering; use an authenticated MAC/signature when an adversary matters. Compression must enforce decompressed-size and nesting limits to resist bombs.

### 52.4 Memory mapping and zero-copy

`mmap` maps file pages into an address range, but mapped bytes are not automatically live C++ objects. Parse bounds and alignment; use byte views and explicit decoding. Mapping lifetime must exceed every view, file truncation can fault access, and random scans can cause page-fault storms. Zero-copy often shifts ownership and validation cost rather than eliminating it.

### Summary

- Serialize logical fields, not compiler object bytes.
- Versioning, limits, units and provenance belong in the format from day one.
- Library choice is an operational/ecosystem decision as well as a speed decision.
- Mapping and zero-copy demand strict lifetime and bounds contracts.

### Self-check quiz

1. Why is CRC insufficient against an attacker? <details><summary>Answer</summary>An attacker can alter data and recompute a non-keyed checksum; authenticity needs a MAC or signature.</details>
2. Is a mapped `byte*` safely castable to an arbitrary record struct? <details><summary>Answer</summary>Generally no: lifetime, alignment, layout, aliasing and endian requirements may all fail.</details>

### Exercises

Specify a two-version event schema. Write v1/v2 readers, a v1→v2 migration, corruption/overflow tests, unknown-field tests and a fuzz harness.

### Chapter project: durable event store

Implement streaming write, atomic temp-file replacement, checksums, schema metadata, chunked reads, HDF5 or Protobuf interoperability, and recovery behavior for a truncated final record.

### Glossary

| Term | Meaning |
|---|---|
| Schema evolution | Compatible change of persisted/message structure. |
| Endianness | Byte order used to encode multi-byte values. |
| Memory mapping | Mapping file-backed pages into virtual memory. |
| Compression bomb | Small input that expands beyond safe resource limits. |

---

## Chapter 53 — API Design, Architecture, Patterns & Plugins

> **Level:** Expert &nbsp;·&nbsp; **Prerequisites:** Ch.15–21, 34–39, 45

**Learning objectives** — design explicit contracts, choose runtime/compile-time variation, apply patterns by pressure, build stable plugin boundaries, and evolve libraries compatibly.

### 53.1 Start with contract and dependency direction

For each API state ownership, nullability, lifetime, mutation, thread safety, errors, complexity, invalidation, units and version stability. Prefer value semantics and narrow interfaces. Domain code should depend on abstractions it owns; filesystem, MPI, GPU and database adapters depend inward.

Use semantic versioning as communication, not proof: source, binary, behavioral and data compatibility are distinct. Test installed-package consumers and ABI reports.

### 53.2 Choosing a variation mechanism

| Need | Mechanism |
|---|---|
| Closed alternatives | `variant` + visitor |
| Open runtime implementations | virtual interface/type erasure |
| Compile-time zero-overhead policy | concepts/templates |
| Construction hidden behind stable intent | factory |
| Replaceable algorithm | strategy |
| Adapt foreign interface | adapter |
| Notify many observers | observer with explicit lifetime/unsubscribe |
| Reversible request/log | command |

Patterns name recurring pressures; adding a class named `FactoryManager` does not create architecture. Prefer the simplest mechanism that meets extension, test and performance needs.

### 53.3 Type erasure

Type erasure stores different concrete types behind one value-like interface without requiring inheritance in those types. `std::function` is an example. A custom erased backend needs ownership, copy/move, small-buffer, exception and ABI decisions.

```cpp
class Backend {
public:
    template<class T> requires EventBackend<T>
    Backend(T value);                       // stores model<T>
    Result run(std::span<const Event>);
private:
    struct concept_t;
    template<class T> struct model;
    std::unique_ptr<concept_t> self_;
};
```

### 53.4 Plugin boundaries

C++ ABI varies across compiler/runtime/build flags. A robust dynamic plugin boundary often exposes a versioned C ABI with opaque handles and function tables; memory is freed by the module that allocated it; exceptions and STL types do not cross.

```c
typedef struct mct_host_v1 mct_host_v1;
typedef struct mct_plugin_v1 {
    unsigned abi_version;
    void* (*create)(const mct_host_v1*);
    int (*run)(void*, const void*, size_t);
    void (*destroy)(void*);
} mct_plugin_v1;
```

Validate version/capabilities before calling, keep the library loaded while objects exist, sandbox untrusted plugins out of process, and define thread/unload behavior.

### 53.5 Data-oriented and dependency-injected design

Data-oriented design arranges data and transformations around access patterns; it complements, not opposes, object design. Dependency injection means supplying collaborators explicitly through constructors/functions; a global service locator hides dependencies and complicates tests. An ECS can suit large homogeneous entity sets but is not a universal pattern.

### Summary

- API contracts include lifetime, failure, invalidation, threading and compatibility.
- Choose pattern/dispatch based on extension shape and operational constraints.
- Plugins need a deliberately stable boundary and allocator/exception ownership rules.
- Dependency direction keeps domain policy independent of infrastructure.

### Self-check quiz

1. Why avoid `std::string` across an unknown plugin ABI? <details><summary>Answer</summary>Layout, allocator and runtime ownership can differ; a versioned C byte-buffer contract is safer.</details>
2. When is `variant` better than virtual dispatch? <details><summary>Answer</summary>When alternatives are closed and exhaustive handling is valuable.</details>

### Exercises

Write contracts for the toolkit's Dataset, Backend and Serializer APIs. Mark ownership, invalidation, exceptions, thread safety, complexity and compatibility; redesign one ambiguous call.

### Chapter project: versioned backend plugin SDK

Create host and two plugins with a C ABI, capability negotiation, error buffer, no cross-module allocation, loader tests, incompatible-version tests and optional out-of-process isolation.

### Glossary

| Term | Meaning |
|---|---|
| Type erasure | Runtime polymorphism hiding concrete type behind a value interface. |
| Opaque handle | Incomplete token whose representation stays inside its module. |
| Dependency inversion | High-level policy owns abstractions implemented by lower-level code. |
| Behavioral compatibility | New version preserves externally observable contracts. |

---

## Chapter 54 — Deep Templates, Object Representation & Type Erasure

> **Level:** Expert/Language &nbsp;·&nbsp; **Prerequisites:** Ch.29–30, 34–36, 46, 53

**Learning objectives** — diagnose two-phase lookup and overload ordering, build detection/expression templates, reason about implicit lifetime and provenance, and implement constrained erased storage.

### 54.1 Two-phase lookup and ordering

Non-dependent names are looked up when a template is defined; dependent names wait until instantiation. This explains why missing `this->`, `typename`, or `template` causes surprising errors. Function-template partial specialization does not exist—use overloads with concepts. Partial ordering chooses the more specialized viable template; constraints also participate.

```cpp
template<class T>
concept HasEnergy = requires(const T& x) {
    { x.energy() } -> std::convertible_to<double>;
};

template<HasEnergy T> double read_energy(const T& x) { return x.energy(); }
template<class T> double read_energy(const T&) = delete; // focused diagnostic
```

The classic detection idiom uses `void_t`; concepts now express most public detection more clearly. Tag dispatch remains useful when choosing implementations from iterator/category tags.

### 54.2 Expression templates and compile-time cost

Expression templates retain an operation tree such as `a + b * c` and evaluate later, avoiding temporaries/fusing loops. They also risk dangling references, code bloat, long diagnostics and repeated evaluation. Store lvalues by reference and rvalues by value (or use a proven library); constrain dimensions and aliasing; compare against compiler-optimized simple loops.

### 54.3 Lifetime, storage, and representation

Storage duration (automatic/static/thread/dynamic) does not identify object lifetime. C++ permits implicit lifetime start for certain implicit-lifetime types in suitable allocated byte storage, but non-trivial objects require construction such as `std::construct_at`; end them with `std::destroy_at`.

```cpp
alignas(T) std::byte storage[sizeof(T)];
T* p = std::construct_at(reinterpret_cast<T*>(storage), args...);
use(*p);
std::destroy_at(p);
```

`std::launder` is narrowly relevant when a new object occupies storage and an old pointer cannot transparently refer to it; it is not an aliasing escape hatch. Strict aliasing permits access through the dynamic type, corresponding signed/unsigned/character-byte cases and documented exceptions. Use `memcpy`/`bit_cast` for representations.

Union active-member rules matter: reading an inactive member is generally invalid outside narrow language allowances. Trivially copyable and standard-layout are distinct properties; padding bytes may remain indeterminate.

### 54.4 Small-buffer type erasure

An erased container needs a function table for destroy/move/copy/invoke, aligned inline storage, heap fallback, and a valid empty state. Correctness depends on exception-safe construction and selecting an inline candidate by size, alignment and nothrow-move—not size alone. Prefer `std::function`, `std::move_only_function`, `any`, `variant`, or a mature library unless custom semantics are essential.

### Summary

- Lookup timing and constraint ordering explain advanced template diagnostics.
- Expression templates trade temporary elimination for lifetime/compile complexity.
- Raw storage does not automatically contain every type of object.
- Type erasure is a resource/lifetime design, not merely a virtual-call trick.

### Self-check quiz

1. Why is `reinterpret_cast<T*>(bytes)` insufficient for a non-trivial `T`? <details><summary>Answer</summary>It changes a pointer representation but does not construct/start the required object lifetime.</details>
2. Why can an expression object dangle? <details><summary>Answer</summary>It may retain references to temporary operands that died before delayed evaluation.</details>

### Exercises

Implement a constrained vector-expression prototype and test lvalue/rvalue lifetime under ASan. Then replace it with a plain fused loop and compare diagnostics, compile time and runtime.

### Chapter project: move-only erased kernel

Build a minimal `Kernel` similar to `move_only_function`: inline small nothrow-movable callables, heap-store others, support empty/move/invoke, and test alignment, exceptions and destruction counts.

### Glossary

| Term | Meaning |
|---|---|
| Two-phase lookup | Template lookup split between definition and instantiation. |
| Implicit-lifetime type | Type whose lifetime may begin implicitly in qualifying storage operations. |
| Expression template | Object representing a delayed expression tree. |
| Small-buffer optimization | Store small objects inline to avoid allocation. |

---

## Chapter 55 — Cross-Platform Systems & Secure C++

> **Level:** Expert/Production &nbsp;·&nbsp; **Prerequisites:** Ch.21, 27, 29, 34, 47–48, 51–52

**Learning objectives** — isolate platform differences, handle text/process/filesystem APIs safely, threat-model native code, and harden hostile-input boundaries.

### 55.1 Portability is a tested contract

Define supported OS, architecture, compiler, standard library and dependency versions. Keep platform code in small adapters selected by the build, not scattered preprocessor branches. CI must compile and test the matrix; `#ifdef _WIN32` alone is not portability.

Dynamic libraries differ: ELF uses visibility and SONAME conventions; Windows DLLs use import/export attributes and different lookup/path rules; macOS uses Mach-O install names. Default to hidden symbols and export only the public ABI.

```cmake
set(CMAKE_CXX_VISIBILITY_PRESET hidden)
set(CMAKE_VISIBILITY_INLINES_HIDDEN YES)
generate_export_header(mctoolkit)
```

### 55.2 Files, paths, text, processes, and signals

`std::filesystem::path` represents native path syntax, not a security boundary. Windows path/Unicode behavior and POSIX byte-oriented filenames differ. Define internal text encoding (normally UTF-8), validate conversions at boundaries, and do not assume one byte equals one character or display column.

Avoid shell construction from untrusted strings. Prefer APIs that pass an executable and argument vector directly (`execve`-style or a process library). If a shell is required, treat its entire language as an injection surface. Temporary files need exclusive creation and restrictive permissions.

POSIX signals allow only async-signal-safe operations in handlers; set an atomic flag or write to a self-pipe, then handle work normally. Windows process/control events require a different adapter. Never log with iostreams or allocate in a POSIX signal handler.

### 55.3 Threat modelling and secure parsing

Identify assets, trust boundaries, attackers, entry points and abuse cases. For every length/count/index perform checked arithmetic before allocation/access. Bound recursion, decompression, CPU work, open files, threads, queues and log volume. Reject malformed data early and consistently.

Common native failure classes:

- signed overflow, narrowing and signed/unsigned confusion;
- out-of-bounds, use-after-free, double free and dangling views;
- format-string misuse (`printf(untrusted)`), command/path injection;
- TOCTOU filesystem races and unsafe symlink following;
- insecure deserialization and algorithmic-complexity attacks;
- secret leakage through logs, cores, swap, exceptions and copies.

Use prepared paths/handles and operate relative to trusted directory descriptors where available. Canonicalization alone does not defeat races. Cryptography must use a reviewed library and high-level authenticated-encryption/password-hashing APIs; do not design primitives.

### 55.4 Hardening and supply chain

Enable warnings, sanitizers in tests, stack protections/fortification/PIE/RELRO where toolchains support them, dependency pinning, SBOM/provenance, signed releases and vulnerability response. Hardening mitigates classes of exploitation; it does not repair incorrect bounds or ownership.

CERT C++ and the C++ Core Guidelines are review inputs, not substitutes for a project-specific threat model. Fuzz external parsers continuously and keep resource limits in integration tests.

### Summary

- Portability is an explicit CI-tested matrix with isolated adapters.
- Unicode, path, process and signal behavior differs materially by OS.
- Hostile-input safety requires checked arithmetic and resource budgets.
- Toolchain hardening and supply-chain controls complement secure design.

### Self-check quiz

1. Why is `canonical(path).starts_with(root)` not a complete sandbox? <details><summary>Answer</summary>The filesystem can change between check and use, links/mounts complicate identity, and string-prefix boundaries can be wrong.</details>
2. Why avoid wiping a secret with ordinary `memset`? <details><summary>Answer</summary>The optimizer may remove a write whose result is unobservable; use a documented secure-zero facility and minimize secret lifetime/copies.</details>

### Exercises

Threat-model the event ingestion pipeline. Add checked size arithmetic, total allocation/CPU limits, log redaction, temp-file safety and fuzz regressions. Run on Linux and one other supported OS.

### Chapter project: hardened portable CLI

Build a UTF-8-aware CLI with direct process spawning, atomic output replacement, cancellation, restrictive temporary files, structured errors and Linux/Windows/macOS CI.

### Glossary

| Term | Meaning |
|---|---|
| Trust boundary | Point where data/control crosses between different trust levels. |
| TOCTOU | Race between checking a resource and using it. |
| Attack surface | Reachable operations an attacker can influence. |
| SBOM | Inventory of software components in an artifact. |

---

## Chapter 56 — Modules, Package Managers & Reproducible Delivery

> **Level:** Expert/Build &nbsp;·&nbsp; **Prerequisites:** Ch.8, 28, 37, 39, 53, 55

**Learning objectives** — structure modules, understand dependency scanning/toolchain limits, integrate Conan/vcpkg responsibly, cross-compile, and produce reproducible consumable artifacts.

### 56.1 Module structure and reality

A named module can contain a primary interface, implementation units and partitions:

```cpp
// mct.core.cppm
export module mct.core;
export struct Event { double energy; };

// mct.core-detail.cppm
module mct.core:detail;
double calibrate(double);

// mct.core.cpp
module mct.core;
```

`export import` re-exports a dependency; ordinary `import` does not. Header units import legacy headers as compiler-managed units and have macro caveats. A module protects names from textual inclusion but does not automatically provide ABI stability, smaller binaries or faster clean builds.

Compiler-specific BMI/PCM artifacts are build outputs, not portable distribution files. Build tools must scan imports and establish compilation order. Pin CMake/compiler versions and keep a supported header interface while module ecosystems remain uneven where your users require it.

### 56.2 Dependency policy

Conan recipes/profiles model settings, options and packages; vcpkg manifests/baselines model dependency versions and triplets. Lock/baseline versions, verify sources, isolate caches, and decide whether CI may access networks. `FetchContent` is convenient but makes configure time a supply-chain/network event unless sources are pinned and mirrored.

Public dependencies appear in installed usage requirements; private implementation dependencies must not leak. Test the installed package with a separate consumer, not only build-tree aliases.

### 56.3 Cross-compilation

A CMake toolchain file states target system, compiler/sysroot and search modes. During cross-compilation, target executables cannot normally run on the build host; feature checks need compile-only alternatives, emulators or preset cache facts. Distinguish build, host and target machines.

```cmake
set(CMAKE_SYSTEM_NAME Linux)
set(CMAKE_SYSTEM_PROCESSOR aarch64)
set(CMAKE_C_COMPILER aarch64-linux-gnu-gcc)
set(CMAKE_CXX_COMPILER aarch64-linux-gnu-g++)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)
```

### 56.4 Reproducible release pipeline

Pin compiler/dependencies/container image, normalize timestamps/path embedding, sort archives, set a source-date epoch where supported, and compare artifacts or explain nondeterministic sections. Produce source archive, checksums/signature, SBOM, provenance, licenses, ABI report and changelog. Rebuild verification is stronger than merely signing one opaque binary.

### Summary

- Modules require dependency-aware builds and compiler-specific artifacts.
- Package managers need pinned manifests, profiles and supply-chain policy.
- Cross builds cannot assume target programs run during configuration.
- A release is consumable only after install-tree and clean-consumer tests.

### Self-check quiz

1. Should a library ship its compiler BMI as the universal module interface? <details><summary>Answer</summary>No; BMIs are generally tied to compiler/version/options and are rebuilt as part of the consumer-compatible build.</details>
2. Why test an installed consumer? <details><summary>Answer</summary>Build-tree aliases can hide missing headers, exports, transitive requirements and broken package configuration.</details>

### Exercises

Add Conan or vcpkg manifest mode with a pinned baseline. Build offline from a prepared cache, install the toolkit, and compile a separate consumer for native and one cross target.

### Chapter project: reproducible SDK release

Ship headers plus optional module interface, CMake package config, package-manager recipe, toolchain presets, SBOM/provenance, ABI compatibility check and two-clean-build artifact comparison.

### Glossary

| Term | Meaning |
|---|---|
| BMI | Compiler-generated binary representation of a module interface. |
| Toolchain file | CMake description of compilers and target platform. |
| Baseline/lockfile | Recorded dependency resolution for repeatable builds. |
| Reproducible build | Same declared inputs produce equivalent artifacts. |

---

## Chapter 57 — Accelerator Optimization & Multi-GPU Design

> **Level:** Expert/HPC &nbsp;·&nbsp; **Prerequisites:** Ch.25, 40–45, 49–50

**Learning objectives** — reason about CUDA/HIP/SYCL memory and execution, overlap safely, profile kernels, tune occupancy, and scale across accelerators while retaining a correctness oracle.

### 57.1 Memory hierarchy and execution

Global device memory is high-latency/high-bandwidth; registers are per-thread; shared/local memory is per-block/work-group and requires coordinated access; constant/read-only caches suit particular patterns. Coalesced accesses and shared-memory tiling can reduce transactions, but bank conflicts and synchronization can erase gains.

Occupancy is active warps/wavefronts relative to hardware capacity. More occupancy can hide latency, but maximizing it may reduce useful registers or increase spills. Measure achieved occupancy, memory throughput, instruction mix and stall reasons with Nsight Compute/Systems, rocprof/rocgdb, or SYCL vendor tools.

### 57.2 Transfers, streams, and lifetime

Pinned host memory enables efficient asynchronous DMA but is scarce and costly to allocate. Streams/queues order operations locally; independent streams may overlap only when dependencies, hardware engines and pinned/resident buffers permit. Events express dependencies and timings.

Unified/managed memory simplifies addressing but page migration can be unpredictable; prefetch/advice may help. A kernel launch is asynchronous relative to the host: do not free/reuse buffers until the relevant stream/event completes. Check both immediate launch errors and deferred execution errors.

### 57.3 Divergence, atomics, and reductions

Branches within a warp/wavefront may serialize paths. Reorganize data/work only when profiling shows divergence cost. Atomics can be effective at low contention; privatized block histograms followed by reduction often scale better. Floating reductions change order, so publish accuracy/reproducibility policy and compare to a high-quality CPU oracle.

### 57.4 Multi-GPU and portability

Partition by data and minimize exchange. Peer-to-peer links, topology, NUMA placement and MPI GPU-awareness determine transfer paths. Use one controlling CPU thread/process per device when it simplifies ownership; overlap halo/partition transfers with independent computation. Handle heterogeneous device capacity and one-device failure explicitly.

CUDA offers deepest NVIDIA control, HIP targets AMD-style ecosystems, SYCL expresses standard C++ single-source queues, and Kokkos/RAJA/OpenMP offload provide higher-level portability. Keep backend contracts and validation shared while allowing backend-specific tuning.

### Summary

- Memory traffic, occupancy, divergence and synchronization interact; profile them together.
- Asynchrony creates buffer-lifetime and deferred-error obligations.
- Multi-GPU scaling is a topology and communication problem.
- Portable architecture retains backend-specific optimization behind tested contracts.

### Self-check quiz

1. Why can reducing register use hurt performance despite higher occupancy? <details><summary>Answer</summary>Spills add memory traffic and lower per-thread efficiency; occupancy is a means, not the goal.</details>
2. When is an asynchronous copy actually asynchronous? <details><summary>Answer</summary>When memory type, stream/dependencies and hardware permit overlap; API naming alone is insufficient.</details>

### Exercises

Profile a tiled transform/histogram. Vary block size, register pressure and data layout; record transfers, kernel time, occupancy, stalls, correctness error and energy if available.

### Chapter project: multi-device event backend

Implement serial, one-GPU and multi-GPU backends with persistent buffers, streams/events, topology-aware partitioning, deterministic validation and end-to-end scaling reports including transfers.

### Glossary

| Term | Meaning |
|---|---|
| Occupancy | Fraction of hardware-resident execution capacity in use. |
| Pinned memory | Host memory fixed for direct asynchronous device transfer. |
| Bank conflict | Serialized accesses to conflicting shared-memory banks. |
| Peer-to-peer | Direct transfer/access between accelerators when supported. |

---

## Chapter 58 — Expert Assessment & Validation Matrix

> **Level:** Final audit &nbsp;·&nbsp; **Prerequisites:** all chapters

**Learning objectives** — replace “I read it” with evidence of competence, validate the handbook's code by category, and plan progressively harder capstones.

### 58.1 Four competency gates

| Level | You can demonstrate—not merely describe |
|---|---|
| Foundation | Build multi-file code; use types/RAII/STL; explain ownership; write tests; diagnose compiler/linker errors. |
| Intermediate | Design APIs; use templates/ranges/errors; package with CMake; debug sanitizer failures; implement numerical contracts. |
| Advanced | Reason about lifetime/UB/memory model; profile before optimizing; build robust concurrent and serialized systems. |
| Expert | Maintain ABI/schema/security contracts; investigate production evidence; scale across node/cluster/accelerator; release reproducibly. |

### 58.2 Code-validation classes

Not every fenced fragment is a standalone program. Classify it before testing:

1. **Standalone:** compile and run with GCC and Clang in its stated standard mode.
2. **Translation-unit fragment:** compile inside a minimal declared harness.
3. **Pseudocode/interface sketch:** clearly labelled and reviewed for contract, not compiled as-is.
4. **External stack:** build in a pinned environment with the named CMake target/toolchain (MPI, CUDA, SYCL, HDF5, etc.).
5. **Command/configuration:** syntax-check and execute in a disposable CI/lab environment.

For code, run Debug warnings, Release, ASan+UBSan, separate TSan where meaningful, tests and install-consumer checks. Record compiler/library versions because C++23 support differs.

### 58.3 Practical examinations

**Foundation exam:** repair ten compile/runtime defects, implement a value-semantic histogram, parse input safely, and explain every copy/move/lifetime.

**Intermediate exam:** publish a tested CMake library with `expected` errors, ranges, property tests, sanitizer CI and an external consumer.

**Advanced exam:** diagnose a supplied core/race, fuzz a versioned parser, implement bounded cancellation-aware concurrency, and justify a profiler-backed optimization.

**Expert exam:** threat-model and release the distributed toolkit with plugin/schema compatibility, OpenMP/MPI/accelerator differential validation, reproducible artifacts and an incident rollback plan.

Score each on correctness (35%), lifetime/resource safety (15%), tests/evidence (15%), API/maintainability (15%), performance method (10%), security/portability (10%). Any UB, data corruption, unbounded hostile allocation, or unverifiable result is a mandatory remediation regardless of total.

### 58.4 Final coverage checklist

- Language: expressions, initialization, overloads, classes, lifetime, exceptions, templates, concepts, modules, coroutines and object model.
- Library: containers, algorithms, ranges, vocabulary/view types, filesystem, chrono, random, atomics, synchronization and `pmr`.
- Engineering: CMake, dependencies, packaging, ABI, CI, debugging, static/dynamic analysis, tests, fuzzing and profiling.
- Systems: processes/signals, networking/TLS, serialization/schema, concurrency, platform/Unicode and security.
- Scientific/HPC: floating point, numerics, linear algebra, data layout, reproducibility, SIMD/NUMA, OpenMP, MPI and accelerators.
- Delivery: documentation, consumers, versioning, SBOM/provenance, reproducible artifacts, migration and operational observability.

### 58.5 Honest definition of “complete”

No finite C++ handbook contains every standard rule, platform API, library ecosystem and hardware technique. This guide is complete as a **zero-to-expert curriculum for modern scientific/production C++** when every checklist domain has explanation, practice and a project path. The published C++ standard, implementation documentation and measured target behavior remain authoritative for edge cases.

### Summary

- Competence is demonstrated through artifacts, diagnosis and explanation.
- Snippets need explicit validation categories and toolchain records.
- Security/correctness failures cannot be averaged away by a high score.
- Expert learning continues through standards, implementation evidence and real systems.

### Self-check quiz

1. Why should pseudocode be labelled? <details><summary>Answer</summary>Readers otherwise assume it compiles and may copy undefined helpers or incomplete lifetime/error behavior.</details>
2. What is the strongest evidence of a performance claim? <details><summary>Answer</summary>Reproducible raw measurements with correctness validation, environment metadata, profiler evidence and an independently repeatable baseline.</details>

### Exercises

Choose one competency gate and perform it under a time limit without consulting chapter solutions. Record unknowns, then turn every failure into a regression test or study task.

### Chapter project: release and defense

Produce toolkit 2.0, then defend it in a review: build from clean source, run analyzers/tests/fuzz smoke, consume the installed package, migrate old data, demonstrate cancellation/failure, reproduce a benchmark, and explain every remaining limitation.

### Glossary

| Term | Meaning |
|---|---|
| Competency gate | Observable work required before claiming a skill level. |
| Validation matrix | Mapping from artifact class to required verification. |
| Mandatory remediation | Defect that must be fixed regardless of aggregate score. |
| Curriculum-complete | Covers defined outcomes without claiming all possible domain knowledge. |

---

## Appendix A — Cheat Sheet

A quick reference to modern C++ (C++23). Chapter numbers point to the full treatment. Compile with `g++ -std=c++23 -Wall -Wextra`.

### Declarations & types — Ch.2–3

```cpp
int x = 42;                       // fundamental type
auto y = 3.14;                    // deduced type (double)
const double c = 299792458.0;     // immutable
constexpr int N = 1000;           // compile-time constant (Ch.26)
std::int64_t big = 1'000'000;     // fixed-width, digit separators (<cstdint>)
double e{91.19};                  // brace init — no narrowing
std::vector<double> v{1, 2, 3};   // list init
auto [a, b] = std::pair{1, 2};    // structured bindings (Ch.6)
// Floating point (Ch.3): use == for exact identities; use a scale-aware tolerance for approximations
```

### Control flow — Ch.5

```cpp
if (x > 0) { } else if (x < 0) { } else { }
if (auto p = find(); p) use(p);          // init-statement
switch (n) { case 1: ...; break; default: ...; }
for (int i = 0; i < n; ++i) { }
for (double e : energies) { }             // range-based
while (in >> x) { }                        // read loop (Ch.27)
for (int i = n; i-- > 0; ) { }             // reverse
```

### Functions & lambdas — Ch.6–7

```cpp
double mean(const std::vector<double>& v);   // pass big objects by const&
constexpr double sq(double x) { return x*x; } // usable at compile time
[[nodiscard]] int compute() noexcept;         // don't-ignore, won't-throw
auto f = [](int x) { return x * 2; };          // lambda
auto g = [scale](double x) { return scale*x; };// capture by value
auto h = [&acc](double x) { acc += x; };       // capture by reference
std::function<double(double)> fn = f;          // type-erased callable
```

### Classes & RAII — Ch.9, 11

```cpp
class Histogram {
    std::vector<long> bins_;                  // members with trailing _
public:
    explicit Histogram(int n) : bins_(n, 0) {} // member-init list
    void fill(double x);                        // mutating
    double mean() const;                        // const method
    ~Histogram() = default;                     // destructor (RAII)
};
```

### Rule of Five / move — Ch.12–13

```cpp
struct Buffer {
    Buffer(const Buffer&);                 // copy ctor
    Buffer& operator=(const Buffer&);      // copy assign
    Buffer(Buffer&&) noexcept;             // move ctor
    Buffer& operator=(Buffer&&) noexcept;  // move assign
    ~Buffer();                             // destructor
};
struct Zero { std::vector<double> data; }; // Rule of Zero — prefer this!
auto y = std::move(x);                      // cast to rvalue → move
```

### Smart pointers — Ch.14

```cpp
auto p = std::make_unique<T>(args);   // unique ownership (Ch.14)
auto s = std::make_shared<T>(args);   // shared ownership (ref-counted)
std::weak_ptr<T> w = s;               // non-owning observer
// Never `new`/`delete` in modern code — let smart pointers own.
```

### Templates & concepts — Ch.16, 20, 30

```cpp
template<typename T> T add(T a, T b) { return a + b; }
template<std::floating_point T> T norm(T x);      // concept-constrained (Ch.20)
if constexpr (std::is_integral_v<T>) { } else { } // compile-time branch (Ch.30)
template<typename... A> auto sum(A... a) { return (a + ...); } // fold
static_assert(sizeof(double) == 8);                // compile-time check
```

### STL & algorithms — Ch.18–19

```cpp
std::vector<T> v; v.reserve(n); v.push_back(x);   // dynamic array
std::array<T, N> a;                                // fixed size
std::span<T> s{v};                                 // non-owning view (Ch.18)
std::map<K,V> m; std::unordered_map<K,V> um;       // ordered / hashed
#include <numeric>
double s = std::accumulate(v.begin(), v.end(), 0.0);
double s2 = std::transform_reduce(v.begin(), v.end(), 0.0, std::plus{},
                                  [](double x){ return x*x; });
std::sort(v.begin(), v.end());
auto evens = v | std::views::filter([](int x){ return x%2==0; }); // ranges (Ch.19)
```

### Error handling — Ch.21

```cpp
std::optional<double> parse(std::string_view);     // maybe a value
std::expected<double, std::string> read();          // value or error (C++23)
if (auto r = read(); r) use(*r); else log(r.error());
try { risky(); } catch (const std::exception& e) { /* e.what() */ }
```

### Numerics, random & time — Ch.3, 22, 31

```cpp
#include <cmath>     // std::sqrt, std::sin, std::hypot, std::isnan
#include <numbers>   // std::numbers::pi
#include <random>
std::mt19937_64 gen(seed);                          // seed → reproducible (Ch.22)
std::normal_distribution<double> d(mean, sigma);
double x = d(gen);
#include <chrono>     // steady_clock for timing (Ch.31)
auto t0 = std::chrono::steady_clock::now();
```

### Concurrency — Ch.32

```cpp
#include <thread>
std::jthread t([]{ work(); });          // auto-joins (RAII)
std::atomic<long> counter{0}; ++counter; // atomic; lock-freedom is implementation-dependent
std::mutex m; { std::lock_guard lk(m); } // critical section
auto fut = std::async(std::launch::async, task); fut.get();
```

### Expert lifetime, generic code & memory model — Ch.34–38

```cpp
std::string_view view = owner;                  // owner must outlive every use
auto bits = std::bit_cast<std::uint64_t>(value);// representation-safe bit copy
template<class T> void relay(T&& x) {
    sink(std::forward<T>(x));                   // preserve caller value category
}
using Result = std::variant<Energy, Momentum, Missing>;
std::pmr::monotonic_buffer_resource phase_pool;
ready.store(true, std::memory_order_release);   // publish preceding writes
if (ready.load(std::memory_order_acquire)) use(payload);
```

### HPC execution — Ch.40–43

```cpp
#pragma omp parallel for reduction(+:sum) schedule(static)
for (std::int64_t i = 0; i < n; ++i) sum += f(i);

// MPI: local values become one global result on rank 0
MPI_Reduce(&local, &global, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);

// Always compare optimized/OpenMP/MPI/GPU backends with a scalar oracle.
```

### Allocation and transactional state — Ch.46

```cpp
std::pmr::monotonic_buffer_resource arena;
std::pmr::vector<Event> phase_data{&arena};
auto candidate = current;          // perform fallible work on candidate
validate(candidate);
swap(current, candidate);          // noexcept commit → strong guarantee
```

### Advanced synchronization — Ch.50

```cpp
std::latch started{workers};
std::counting_semaphore<> slots{capacity};
flag.wait(false);                  // always pair with a complete atomic protocol
flag.store(true, std::memory_order_release);
flag.notify_all();
// Lock-free removal also needs safe reclamation (hazard pointer/epoch/etc.).
```

### Durable/network boundaries — Ch.51–52, 55

```text
TCP: loop for partial read/write; frame messages; cap length before allocation
TLS: verify certificate chain and hostname; apply handshake/read/write deadlines
Files: magic + version + explicit endian fields + lengths + integrity metadata
Hostile input: checked arithmetic + recursion/CPU/memory/file/thread budgets
```

### Build, debugging, testing and profiling — Ch.28–29, 33, 47–49, 56

```text
g++ -std=c++23 -Wall -Wextra                  # baseline
g++ -std=c++23 -O2                            # optimized (production)
g++ -std=c++23 -O3 -march=native              # + SIMD for this CPU (Ch.31)
g++ -std=c++23 -g -fsanitize=address,undefined# catch memory/UB bugs (Ch.29,33)
g++ -std=c++23 -fsanitize=thread              # catch data races (Ch.32)
cmake -B build -DCMAKE_BUILD_TYPE=Release     # CMake build (Ch.28)
gdb ./app core                                # matching executable + core (Ch.47)
clang++ -fsanitize=fuzzer,address,undefined   # parser fuzz target (Ch.48)
perf stat -r 10 ./app                         # repeated hardware counters (Ch.49)
perf record -g ./app && perf report           # sampled call paths (Ch.49)
```

## Appendix B — Glossary

A consolidated glossary of key terms (each chapter also has its own).

| Term | Meaning |
|------|---------|
| **`auto` / type deduction** | Compiler deducing a variable's type from its initializer. |
| **`const` / `constexpr`** | Immutable value / value computable at compile time. |
| **Fixed-width type** | `std::int32_t`, `std::int64_t`, … — exact-size integers (`<cstdint>`). |
| **IEEE 754** | The floating-point standard; explains rounding, `NaN`, `inf`. |
| **Non-associativity** | `(a+b)+c ≠ a+(b+c)` for floats — summation order matters. |
| **Undefined behavior (UB)** | An operation with no defined meaning (overflow, OOB, races). |
| **RVO / NRVO** | Return-value optimization — eliding a return copy. |
| **Lambda / closure** | An inline callable / a lambda capturing variables. |
| **`std::function`** | A type-erased wrapper for any callable. |
| **RAII** | Resource Acquisition Is Initialization — a destructor releases resources. |
| **Rule of Five / Zero** | Define all five special members, or (better) none. |
| **lvalue / rvalue** | A named object / a temporary; `std::move` casts to rvalue. |
| **Move semantics** | Transferring resources instead of copying them. |
| **`unique_ptr` / `shared_ptr`** | Sole / reference-counted owning smart pointer. |
| **Virtual function / vtable** | Runtime-dispatched method / its dispatch table. |
| **Object slicing** | Copying a derived object into a base — losing the derived part. |
| **Template / instantiation** | Generic code / a concrete version generated for a type. |
| **Concept** | A named compile-time constraint on a template parameter. |
| **SFINAE / CRTP** | Old constraint mechanism / base-templated-on-derived static polymorphism. |
| **`if constexpr`** | A compile-time branch; the untaken branch is discarded. |
| **Fold expression** | Applies an operator across a parameter pack (`(args + ...)`). |
| **Iterator / range** | A generalized pointer into a container / a view pipeline (`\|`). |
| **`std::span` / `std::string_view`** | Non-owning views over contiguous data / characters. |
| **`optional` / `expected`** | A maybe-value / a value-or-error return type. |
| **Exception / `noexcept`** | A thrown error object / a promise not to throw. |
| **PRNG / engine / distribution** | Pseudo-random generator / its algorithm / a shaping of its output. |
| **Monte Carlo** | Estimating quantities by random sampling. |
| **Cache line / locality** | Architecture-sized block transferred through caches (commonly 64 bytes on current CPUs) / reuse of nearby data. |
| **SoA / AoS** | Struct-of-Arrays / Array-of-Structs data layout. |
| **SIMD / vectorization** | One instruction on multiple values / the compiler using it. |
| **Data race** | Concurrent unsynchronized access (≥1 write) — undefined behavior. |
| **`atomic` / `mutex`** | Indivisible operations / a lock guarding a critical section. |
| **Sanitizer (ASan/UBSan/TSan)** | Runtime detector of memory / UB / race bugs. |
| **Tolerance** | Domain-justified absolute/relative/ULP bound for approximate floating-point comparisons; exact comparisons still have valid uses. |
| **Reproducibility** | Same inputs → same outputs (pinned seed, flags, order). |
| **Lifetime / dangling** | Validity interval of an object / a handle referring outside that interval. |
| **ABI / PImpl** | Binary compatibility contract / representation-hiding library technique. |
| **Forwarding reference** | Deduced `T&&` parameter preserving lvalue/rvalue intent with `forward`. |
| **Coroutine frame** | State retained while a coroutine is suspended. |
| **Happens-before** | Cross-thread ordering required for defined visibility of conflicting accesses. |
| **False sharing** | Cache-line contention between logically independent worker data. |
| **NUMA** | Hardware where memory access cost depends on processor location. |
| **OpenMP / MPI** | Shared-memory directive model / distributed-memory message-passing interface. |
| **Arithmetic intensity** | Work performed per byte transferred, used in roofline analysis. |
| **Conditioning / stability** | Problem sensitivity / algorithm's control of introduced error. |

## Appendix C — Further Resources

- **cppreference.com** — a comprehensive, community-maintained language and library reference. Use the published standard and WG21 papers when exact normative wording matters.
- **The C++ standard & proposals** — `isocpp.org` and the `wg21` papers, for the definitive rules and the rationale behind new features.
- **Compiler Explorer (godbolt.org)** — see exactly what assembly your code compiles to across compilers and flags; indispensable for the "under the hood" and performance chapters.
- **ROOT (root.cern)** — CERN's C++ data-analysis framework: `TTree` storage, histograms, fitting, plotting — the standard toolkit in experimental particle physics.
- **Eigen (eigen.tuxfamily.org)** — the header-only linear-algebra library (Chapter 24): dense/sparse matrices, decompositions, expression templates. Pair with **BLAS/LAPACK** for large dense problems.
- **Guidelines & style** — the *C++ Core Guidelines* (Stroustrup & Sutter) for modern best practices; *Effective Modern C++* (Meyers) for the reasoning behind the idioms.
- **HPC & parallelism** — **OpenMP** (shared-memory `#pragma` parallelism), **MPI** (distributed clusters), and **CUDA/SYCL** (GPUs) are the next steps beyond `std::thread` for large-scale scientific computing.
- **Tools** — `cmake` (Chapter 28), `perf`/`valgrind`/VTune (profiling), `clang-tidy`/`cppcheck` (static analysis), Catch2/GoogleTest (testing), Google Benchmark (micro-benchmarks).
- **Keep building** — the fastest path to mastery is shipping real code. Take the Monte Carlo Analysis Toolkit further: write it to ROOT/HDF5, parallelise it with OpenMP or a GPU, wrap it in a CMake package, and validate it against a known physics result.

## Appendix D — The Monte Carlo Analysis Toolkit, Assembled

Across 58 chapters, one application — a **Monte Carlo Analysis Toolkit** — grows from a single `std::cout` into a tested, installable, reproducible, multi-backend numerical library and then into a hardened networked SDK. This appendix gives a **buildable reference slice** rather than only a narrative map. It intentionally keeps the physics model small; the engineering boundaries are the important part.

### Minimal repository

```text
mctoolkit/
├── CMakeLists.txt
├── cmake/MCToolkitConfig.cmake.in
├── include/mct/event.hpp
├── include/mct/histogram.hpp
├── src/histogram.cpp
├── apps/analyze.cpp
└── tests/histogram_test.cpp
```

`include/mct/event.hpp` owns domain values and validates construction:

```cpp
#pragma once
#include <cmath>
#include <expected>
#include <string>

namespace mct {
struct GeV { double value; };

struct Event {
    GeV energy;
    double weight{1.0};
};

inline std::expected<Event, std::string> make_event(double energy, double weight = 1.0) {
    if (!std::isfinite(energy) || energy < 0.0)
        return std::unexpected("energy must be finite and non-negative");
    if (!std::isfinite(weight))
        return std::unexpected("weight must be finite");
    return Event{GeV{energy}, weight};
}
} // namespace mct
```

`include/mct/histogram.hpp` exposes value semantics and a narrow interface:

```cpp
#pragma once
#include <cstddef>
#include <expected>
#include <span>
#include <string>
#include <vector>
#include "mct/event.hpp"

namespace mct {
class Histogram {
public:
    static std::expected<Histogram, std::string>
    create(std::size_t bins, GeV low, GeV high);

    void fill(GeV value, double weight = 1.0) noexcept;
    void fill(std::span<const Event> events) noexcept;
    [[nodiscard]] std::span<const double> counts() const noexcept { return counts_; }
    [[nodiscard]] double underflow() const noexcept { return underflow_; }
    [[nodiscard]] double overflow() const noexcept { return overflow_; }
    [[nodiscard]] double total_weight() const noexcept;

private:
    Histogram(std::size_t bins, double low, double high);
    double low_{};
    double high_{};
    double inverse_width_{};
    std::vector<double> counts_;
    double underflow_{};
    double overflow_{};
};
} // namespace mct
```

`src/histogram.cpp` contains the checked factory and hot path:

```cpp
#include "mct/histogram.hpp"
#include <algorithm>
#include <numeric>

namespace mct {
Histogram::Histogram(std::size_t bins, double low, double high)
    : low_(low), high_(high), inverse_width_(bins / (high - low)), counts_(bins) {}

std::expected<Histogram, std::string>
Histogram::create(std::size_t bins, GeV low, GeV high) {
    if (bins == 0) return std::unexpected("histogram needs at least one bin");
    if (!std::isfinite(low.value) || !std::isfinite(high.value) || low.value >= high.value)
        return std::unexpected("histogram range must be finite and increasing");
    return Histogram{bins, low.value, high.value};
}

void Histogram::fill(GeV x, double weight) noexcept {
    if (!std::isfinite(x.value) || !std::isfinite(weight)) return;
    if (x.value < low_) { underflow_ += weight; return; }
    if (x.value >= high_) { overflow_ += weight; return; }
    auto index = static_cast<std::size_t>((x.value - low_) * inverse_width_);
    index = std::min(index, counts_.size() - 1);
    counts_[index] += weight;
}

void Histogram::fill(std::span<const Event> events) noexcept {
    for (const Event& event : events) fill(event.energy, event.weight);
}

double Histogram::total_weight() const noexcept {
    return underflow_ + overflow_ + std::accumulate(counts_.begin(), counts_.end(), 0.0);
}
} // namespace mct
```

`apps/analyze.cpp` is composition, not domain logic:

```cpp
#include "mct/histogram.hpp"
#include <iostream>
#include <random>
#include <vector>

int main() {
    auto histogram = mct::Histogram::create(100, mct::GeV{80.0}, mct::GeV{100.0});
    if (!histogram) { std::cerr << histogram.error() << '\n'; return 2; }

    std::mt19937_64 rng{42};
    std::normal_distribution<double> z_mass{91.19, 2.5};
    std::vector<mct::Event> events;
    events.reserve(1'000'000);
    for (int i = 0; i < 1'000'000; ++i)
        events.push_back({mct::GeV{z_mass(rng)}, 1.0});

    histogram->fill(events);
    std::cout << "accepted weight: "
              << histogram->total_weight() - histogram->underflow() - histogram->overflow()
              << '\n';
}
```

`tests/histogram_test.cpp` checks invariants and boundaries:

```cpp
#include "mct/histogram.hpp"
#include <cassert>
#include <cmath>

int main() {
    auto h = mct::Histogram::create(2, mct::GeV{0.0}, mct::GeV{2.0});
    assert(h);
    h->fill(mct::GeV{-1.0}, 2.0);
    h->fill(mct::GeV{0.0}, 3.0);
    h->fill(mct::GeV{1.999}, 5.0);
    h->fill(mct::GeV{2.0}, 7.0);
    assert(h->counts()[0] == 3.0);
    assert(h->counts()[1] == 5.0);
    assert(h->underflow() == 2.0);
    assert(h->overflow() == 7.0);
    assert(std::abs(h->total_weight() - 17.0) < 1e-12);
}
```

The root `CMakeLists.txt` builds, tests, and installs the library:

```cmake
cmake_minimum_required(VERSION 3.25)
project(MCToolkit VERSION 1.0.0 LANGUAGES CXX)
include(CTest)
include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

add_library(mctoolkit src/histogram.cpp)
add_library(MCToolkit::mctoolkit ALIAS mctoolkit)
target_compile_features(mctoolkit PUBLIC cxx_std_23)
target_include_directories(mctoolkit
  PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
         $<INSTALL_INTERFACE:include>)

add_executable(mct-analyze apps/analyze.cpp)
target_link_libraries(mct-analyze PRIVATE MCToolkit::mctoolkit)

if(BUILD_TESTING)
  add_executable(histogram-test tests/histogram_test.cpp)
  target_link_libraries(histogram-test PRIVATE MCToolkit::mctoolkit)
  add_test(NAME histogram.boundaries COMMAND histogram-test)
endif()

install(TARGETS mctoolkit EXPORT MCToolkitTargets
        INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(EXPORT MCToolkitTargets NAMESPACE MCToolkit::
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/MCToolkit)
configure_package_config_file(cmake/MCToolkitConfig.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/MCToolkitConfig.cmake
  INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/MCToolkit)
write_basic_package_version_file(
  ${CMAKE_CURRENT_BINARY_DIR}/MCToolkitConfigVersion.cmake
  COMPATIBILITY SameMajorVersion)
install(FILES
  ${CMAKE_CURRENT_BINARY_DIR}/MCToolkitConfig.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/MCToolkitConfigVersion.cmake
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/MCToolkit)
```

`cmake/MCToolkitConfig.cmake.in` loads the exported targets for consumers:

```cmake
@PACKAGE_INIT@
include("${CMAKE_CURRENT_LIST_DIR}/MCToolkitTargets.cmake")
check_required_components(MCToolkit)
```

Build and validate from a clean directory:

```text
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=ON
cmake --build build --parallel
ctest --test-dir build --output-on-failure
./build/mct-analyze
```

This reference slice deliberately leaves OpenMP/MPI/GPU backends optional. Add each as a separate target implementing the Chapter 45 backend contract, and run the same invariant suite against every enabled implementation.

### The evolution

| Chapter | What the toolkit gained |
|---------|-------------------------|
| **1** | A `main()` printing a particle's energy — the first program. |
| **2** | An "event" modelled with typed, `const`-correct variables. |
| **3** | Floating-point-correct statistics (mean; Kahan summation). |
| **4** | Detector-status bit flags and derived quantities via operators. |
| **5** | A scan/convergence loop over measurements. |
| **6** | Analysis extracted into functions (pass-by-`const&`, RVO). |
| **7** | Higher-order analysis via lambdas, functors, and `std::function`. |
| **8** | The toolkit split across headers and translation units. |
| **9** | A real `Histogram` class (encapsulated bins, `const` methods). |
| **10** | `const`-correct pointer/reference interfaces over events. |
| **11** | An RAII-owning data `Buffer` (leak-free, ASan-verified). |
| **12** | A deep-copyable dataset (Rule of Three/Five). |
| **13** | A cheaply movable dataset (move semantics; 1M events). |
| **14** | Smart-pointer-owned detectors and datasets. |
| **15** | A polymorphic `Sensor` hierarchy (Calorimeter/Tracker). |
| **16** | A generic `Stats<T>` over any numeric type (templates). |
| **17** | An operator-overloaded `LorentzVector` → the Z boson at 91.30 GeV. |
| **18** | STL-container-backed datasets with `span` views. |
| **19** | Statistics via `<numeric>` and ranges pipelines. |
| **20** | Numeric routines constrained by concepts. |
| **21** | `optional`/`expected`-based robust data parsing. |
| **22** | A **Monte Carlo event generator** (Z-mass peak, mean 91.19). |
| **23** | Numerical integrators & solvers (bisection, Newton, RK4 decay chain). |
| **24** | A `Matrix` class and the Eigen/BLAS ecosystem. |
| **25** | A calorimeter grid with SoA/AoS layout. |
| **26** | Compile-time physical constants and a γ-factor table (`constexpr`). |
| **27** | Binary save/load persistence for datasets. |
| **28** | A multi-target CMake build (library + app + Eigen). |
| **29** | A UB audit and a sanitized build catching a planted bug. |
| **30** | A generic, zero-overhead `Accumulator<T>` (metaprogramming). |
| **31** | An optimized histogram fill — 10M events at ~370 M events/s. |
| **32** | A **parallel Monte Carlo integrator** (π via partitioned reduction). |
| **33** | A sanitized, reproducible **test suite** (physics-invariant tests). |
| **34** | Audited lifetimes, stable ABI boundaries, and PImpl where justified. |
| **35** | Policy-based, constrained generic kernels with correct forwarding. |
| **36** | Strong domain/vocabulary types, lazy queries, and phase allocators. |
| **37** | Streaming coroutine ingestion and an optional module interface. |
| **38** | A bounded queue with explicit memory-model reasoning and cancellation. |
| **39** | Presets, CTest, installation, dependency policy, and CI. |
| **40** | A reproducible performance dossier including SIMD and NUMA evidence. |
| **41** | An OpenMP private-histogram backend. |
| **42** | MPI distribution and a hybrid MPI+OpenMP configuration. |
| **43** | An optional accelerator backend validated against the serial oracle. |
| **44** | Solver diagnostics, units, uncertainty, schema, and provenance. |
| **45** | A packaged, externally consumable 1.0 capstone release. |
| **46** | Phase allocators, allocation instrumentation, and transactional import. |
| **47** | A crash-analysis workflow with cores, debuggers, replay, and static analysis. |
| **48** | Property, fuzz, differential, mutation, and adversarial verification. |
| **49** | Hardware-counter evidence, PGO/LTO presets, and performance decision records. |
| **50** | Bounded execution, cancellation, progress guarantees, and reclamation reasoning. |
| **51** | A framed TLS event-ingestion service with deadlines and backpressure. |
| **52** | A versioned, checksummed, migratable scientific event format. |
| **53** | Stable APIs, plugin SDK, explicit dependency direction, and compatibility tests. |
| **54** | Deep template diagnostics, object-lifetime storage, and move-only type erasure. |
| **55** | Cross-platform adapters, threat model, resource limits, and hardening. |
| **56** | Modules, pinned packages, cross-compilation, SBOM, and reproducible releases. |
| **57** | Profiled single/multi-GPU backends with transfer and topology evidence. |
| **58** | A competency and validation matrix for defending toolkit 2.0. |

### The shape of the final system

By the end, the Monte Carlo Analysis Toolkit is:

- a set of **RAII-owning, value-semantic types** (`Histogram`, `Dataset`, `LorentzVector`, `Matrix`) — no manual memory management, no leaks, cheap to move;
- built on **generic, zero-overhead abstractions** (`Stats<T>`, `Accumulator<T>`) constrained by concepts and validated at compile time;
- a **complete numerical pipeline** — generate events by Monte Carlo, analyze them with `<numeric>` and ranges, integrate and solve, and persist results to disk;
- **fast on real hardware** — cache-friendly layout, `reserve`d buffers, auto-vectorized loops, and a **parallel reduction** across cores;
- **built with CMake**, linking numerical libraries the modern way;
- and **verified** by a sanitized, reproducible test suite that asserts *physics invariants* (a mass is frame-independent) and fails CI on any regression.

That progression — from a beginner's first `std::cout` to an expert's tested, optimized, parallel, reproducible scientific library, built one concept at a time — *is* the journey from zero to expert. The language features were never the point; producing numbers you can *trust, reproduce, and defend* was. You now have both the C++ and the discipline. Go build something worth reproducing.
