# Python: Zero to Expert
## A Modern, Project-Driven Guide to Python 3.14, Data, Web, APIs, and Production Engineering

---

## Who This Handbook Is For

This handbook starts with no programming assumptions and ends with professional Python: typed packages, tested data pipelines, asynchronous services, secure APIs, observability, and reproducible delivery. The original thirty-day sequence is preserved, but “day” means a learning unit—not a promise that mastery takes one day.

**Baseline:** CPython 3.14. Examples that require third-party packages state the dependency. Python 3.12/3.13 users can follow most chapters; check version notes before using newer syntax or library behavior.

## How to Use It

For each chapter: read the model, type examples yourself, predict output, run tests, complete exercises, and extend the running project. Do not merely copy code. When an example touches networks, websites, credentials, or databases, use systems you own or are authorized to access.

### What “complete” means in this handbook

This is a self-study book, but no book can guarantee expertise. Here, completing a
topic means that you can do all of the following without copying the chapter:

1. explain the mental model in plain language;
2. predict the output and failure mode of a small program;
3. write a working solution from a blank file;
4. test normal, boundary, and invalid inputs;
5. choose the feature deliberately and name a reasonable alternative;
6. diagnose a broken version from its traceback or observable behavior.

Treat short syntax and prediction exercises as **Foundation**, Atlas extensions as
**Application**, and performance/security/production investigations as
**Challenge**. Foundation work should be completed before continuing; challenges
may require consulting documentation. Selected solutions and explicit passing
criteria are in Appendix G. Compare only after attempting the problem: a solution
is a discussion aid, not the only valid implementation.

### Setup from an empty computer

Install a supported CPython from [python.org](https://www.python.org/downloads/) or
your operating system's trusted package source. During the first pass, use Python
3.12 or newer; examples whose behavior is 3.14-specific are labeled. On Windows,
select “Add python.exe to PATH” or use the `py` launcher. On macOS/Linux, do not
replace the Python used internally by the operating system.

Open a terminal and verify the interpreter:

```console
$ python --version
Python 3.14.0
$ python -c "import sys; print(sys.executable)"
/path/to/python
```

If `python` is unavailable on macOS/Linux, try `python3` consistently. Create a
workspace and virtual environment:

```bash
mkdir atlas-learning
cd atlas-learning
python -m venv .venv
```

Activate it with `. .venv/bin/activate` on POSIX shells or
`.venv\Scripts\Activate.ps1` in PowerShell. Your prompt usually gains `(.venv)`.
Create `hello.py` in an editor, save `print("Atlas is ready")`, and run:

```console
$ python hello.py
Atlas is ready
```

The terminal's current directory controls how relative paths are resolved. Use
`pwd` on POSIX or `Get-Location` in PowerShell to see it; use `cd` to change it.
An editor runs the same interpreter only when its selected interpreter points at
this `.venv`.

### A test habit from day one

Chapters ask for tests before the full testing chapter because tiny executable
checks are part of learning. At first, use `assert`:

```python
def double(value: int) -> int:
    return value * 2


assert double(0) == 0
assert double(3) == 6
assert double(-2) == -4
print("checks passed")
```

Run the file normally. Do not use `assert` for validating hostile production input,
because optimized Python can remove assertions. In Chapter 34 these checks become
pytest tests with fixtures, parametrization, and failure reporting.

### How to read code blocks

- A `python` block with all names defined is directly runnable. Short blocks that
  refer to surrounding domain names (`records`, `Event`, `logger`, and similar) are
  excerpts; reproduce the missing fixture explicitly before experimenting.
- `console` blocks include command output; do not type the leading `$`.
- `...` means intentionally omitted code only when the text says so.
- Third-party examples name their dependency and should be tested in a disposable
  environment or against local fixtures rather than the public network.

### Callouts

- **WHY** — the problem a feature solves.
- **MODEL** — how to reason about behavior.
- **TRAP** — a frequent bug or misleading shortcut.
- **SECURITY** — a trust-boundary concern.
- **PERFORMANCE** — measure before optimizing.
- **VERSION** — behavior tied to a Python/library release.

## The Running Project: Atlas Data Platform

Atlas begins as a command-line record tracker. It grows into a package that imports files, validates records, scrapes authorized sources, analyzes data with NumPy/Pandas, stores documents in MongoDB, exposes a FastAPI service, runs background ingestion, and ships with typing, tests, logging, security controls, CI, and a reproducible release.

## Learning Roadmap

1. **Foundations (1–10):** objects, collections, decisions, iteration.
2. **Pythonic Core (11–21):** functions, modules, errors, files, packages, objects.
3. **Data and Web (22–30):** scraping, statistics, Pandas, HTTP, MongoDB, APIs.
4. **Professional Python (31–42):** typing, protocols, tests, concurrency, async, security, performance, packaging, deployment.
5. **Capstone and Reference:** assembled architecture, checklists, cheat sheets.

## Table of Contents

### Part I — The Original 30-Day Path

1. Introduction
2. Variables and Built-in Functions
3. Operators
4. Strings
5. Lists
6. Tuples
7. Sets
8. Dictionaries
9. Conditionals
10. Loops
11. Functions
12. Modules
13. Comprehensions
14. Higher-Order Functions
15. Python Error Types and Tracebacks
16. Date and Time
17. Exception Handling
18. Regular Expressions
19. File Handling
20. Package Management
21. Classes and Objects
22. Web Scraping
23. Virtual Environments
24. Statistics and NumPy
25. Pandas
26. Python for the Web
27. Python with MongoDB
28. Consuming APIs
29. Building APIs
30. Conclusion and Integration

### Part II — Professional Python

31. Iterators, Generators, and Lazy Pipelines
32. Decorators, Closures, Context Managers, and Descriptors
33. Type Hints, Generics, and Protocols
34. Testing, Property Testing, and Fuzzing
35. Debugging, Logging, and Observability
36. Concurrency, Multiprocessing, and the GIL
37. Async Python and Structured Cancellation
38. Security and Hostile Input
39. Performance, Memory, and Profiling
40. Production Project Architecture and CLI Design
41. Packaging, CI, and Reproducible Delivery
42. Deployment and Operations

### Part III — Deep Reference and Production Mastery

43. The Python Object Model and Memory
44. Built-in Types and Standard Library Mastery
45. Iterator, Generator, and Coroutine Protocols
46. Attribute Access, Descriptors, and Metaclasses
47. Advanced Static Typing
48. Testing Architecture and Quality Engineering
49. Threads, Processes, IPC, and Synchronization
50. Asyncio Internals and Reliable Async Systems
51. Numerical Python and Statistical Engineering
52. Production Pandas and Data Pipelines
53. Production MongoDB
54. Production FastAPI
55. Configuration, Migrations, Observability, and Operations
56. Secure Python Engineering
57. Atlas: Buildable Multi-file Capstone

### Part IV — Integrated Learning Projects

58. Project 1: Personal Expense CLI
59. Project 2: File ETL and Data-Quality Report
60. Project 3: Resilient API Client and Authorized Scraper
61. Project 4: Database-Backed FastAPI Service
62. Project 5: Production Release and Failure Drill

### Appendices

- A. Atlas Capstone Blueprint
- B. Python Cheat Sheet
- C. Complexity and Selection Guide
- D. Readiness Matrix and Resources
- E. Thirty-Chapter Practice Matrix
- F. Professional Capstone Labs
- G. Hints, Selected Solutions, and Mastery Checks

---

# Part I — The Original 30-Day Path

## Chapter 1 — Introduction

> **Level:** Beginner · **Prerequisites:** none

### Learning objectives

Install/select Python, distinguish the REPL from scripts, understand indentation and execution, inspect values and errors, and run the first Atlas command.

By the end you should also be able to explain source code, interpreter,
implementation, expression, statement, module, standard library and third-party
package; find the current directory and selected executable; predict the order of
top-level execution; read a basic traceback; and create an import-safe program from
a blank directory.

### 1.0 What programming is

A program is a precise sequence of instructions and definitions represented as
text. Python source code is written in `.py` files. The Python runtime parses that
text, rejects invalid grammar, and executes valid statements. Programming is not
mainly memorizing syntax: it is translating requirements into states,
transformations, decisions and observable results.

Consider a requirement: “Show how many records were accepted.” Before code, identify:

- input: records and their validity;
- rule: count only accepted records;
- output: a human-readable message;
- invalid states: malformed records or unavailable input;
- evidence: examples and tests proving the count.

The eventual Python may be short, but the reasoning is the real work.

### 1.0.1 Python language, implementation, and ecosystem

“Python” can refer to several related things:

- the language specification: syntax and required behavior;
- an implementation such as CPython or PyPy;
- the executable selected by a command such as `python`;
- the standard library distributed with that implementation;
- third-party packages installed separately;
- your own modules and packages.

CPython is the reference and most widely used implementation. Code should not rely
on CPython-only details such as exact reference-count timing unless the application
explicitly targets CPython and documents that dependency.

### 1.0.2 Checking the installation

Commands shown with `$` are terminal sessions; do not type the `$` prompt.

```console
$ python --version
Python 3.14.0
$ python -c "import sys; print(sys.executable)"
/path/to/python
$ python -c "import platform; print(platform.python_implementation())"
CPython
```

On systems where `python` is not configured, use `python3`. On Windows the `py`
launcher can select a version explicitly: `py -3.14`. Be consistent inside one
project. `sys.executable` is stronger evidence than the shell prompt because it
shows the actual executable running the code.

The current working directory affects relative file paths and import discovery:

```python
from pathlib import Path

print(Path.cwd())
print(Path(__file__).resolve())           # available in a script, not normal REPL
```

`Path.cwd()` answers “where was the process started?” while `__file__` answers
“where is this source file?” They need not be the same directory.

### 1.1 What Python executes

Python source is parsed, compiled to bytecode, and executed by an implementation such as CPython. “Interpreted” does not mean “never compiled”; it means users normally run source through an interpreter/runtime rather than shipping one fixed native executable. CPython, PyPy, and other implementations may differ in performance and implementation details while following the language specification.

```bash
python3 --version
python3                    # interactive REPL
python3 app.py             # execute a script
python3 -m module_name     # execute a module through import machinery
python3 -m pip --version   # run pip belonging to this interpreter
```

Use `python -m ...` when interpreter identity matters; a bare `pip` may belong to another installation.

### 1.1.1 Parse, compile, execute

For ordinary CPython execution:

1. source text is decoded;
2. the parser builds an internal syntax representation;
3. valid code is compiled to Python bytecode;
4. the virtual machine executes instructions;
5. imported bytecode may be cached under `__pycache__` as an optimization.

The cache is disposable and is not your source of truth. Bytecode compatibility may
change between Python versions. Use `dis` for learning, not for designing business
logic around implementation details:

```python
import dis

def add(left: int, right: int) -> int:
    return left + right

dis.dis(add)
```

### 1.1.2 REPL, script, module, and notebook

The REPL reads one input, evaluates it, prints a representation, and loops. It is
excellent for experiments:

```console
$ python
>>> 2 + 3
5
>>> name = "Atlas"
>>> name.upper()
'ATLAS'
>>> exit()
```

Do not copy `>>>` or `...` prompts into a `.py` file. A script is saved source that
can be reviewed, rerun and tested. `python path/to/app.py` executes a file as the
top-level program. `python -m atlas` asks the import system to locate the `atlas`
module/package and execute it, which is preferable for package entry points.

Notebooks store code in separately executable cells. They are useful for exploration
and visualization, but cell execution order can hide state. Restart and run all
cells before trusting a result; move reusable logic into normal modules and tests.

### 1.1.3 Top-level execution order

Python normally executes top-level statements from top to bottom. A function body
is defined now and executed later when called.

```python
print("A")

def announce() -> None:
    print("C")

print("B")
announce()
```

```console
A
B
C
```

Imports also execute a module's top-level code on first import in an interpreter.
This is why modules should avoid surprising file writes, network calls and server
startup during import.

### 1.2 Syntax, blocks, and the first program

Indentation defines suites. Four spaces are conventional; mixing tabs and spaces is a bug source.

```python
def greet(name: str) -> str:
    """Return a greeting; this docstring documents the function."""
    if not name.strip():
        raise ValueError("name cannot be blank")
    return f"Hello, {name.strip()}!"


if __name__ == "__main__":
    print(greet("Atlas"))
```

The guard prevents command-line behavior from running when another module imports the file. Python executes top-level statements in order. Names are case-sensitive.

### 1.2.1 Tokens, literals, expressions, and statements

Source is composed of tokens such as names, keywords, literals, operators and
delimiters. Keywords (`if`, `def`, `return`, `class`, and others) have grammatical
meaning and cannot be ordinary variable names.

```python
message = "Atlas"                        # assignment statement
count = 2 + 3                            # 2 + 3 is an expression
print(message, count)                    # expression statement: a function call
```

An expression produces a value. A statement performs a language action such as
assignment, import, definition or control flow. Literals write values directly:

```python
42                 # integer literal
3.5                # floating-point literal
"hello"            # string literal
True               # Boolean literal/keyword
None               # absence sentinel
[1, 2]             # list display
{"id": 7}          # dictionary display
```

Later chapters explain these types. For now, notice that names are case-sensitive:
`count`, `Count`, and `COUNT` are three different names.

### 1.2.2 Physical lines, continuation, and comments

One simple statement usually occupies one line. Prefer implicit continuation inside
parentheses, brackets or braces for long expressions:

```python
total = (
    10
    + 20
    + 30
)

settings = {
    "host": "127.0.0.1",
    "port": 8000,
}
```

Avoid backslash continuation when brackets can express the structure. `#` begins a
comment outside a string. Comments should explain reasoning, constraints or a
surprising choice—not narrate obvious syntax.

```python
timeout_seconds = 5  # API contract; keep below proxy timeout
```

A string placed first in a module, function or class is a docstring accessible to
documentation tools. It is not the same mechanism as a comment.

### 1.2.3 Indentation and suites

A colon introduces an indented suite after constructs such as `if`, `for`, `while`,
`def`, `class`, `try`, `with` and `match`. Four spaces are the standard indentation
level.

```python
temperature = 22

if temperature > 20:
    label = "warm"
    print(label)

print("finished")                         # outside the if suite
```

Indentation changes meaning. Tabs that visually resemble spaces may cause
`TabError` or subtle editor confusion. Configure the editor to insert spaces and
show invisible whitespace. Empty suites require `pass` as a temporary placeholder:

```python
def implement_later() -> None:
    pass
```

Do not leave unexplained `pass` in finished behavior.

### 1.2.4 Basic output and input

`print` converts objects to text, separates arguments with a space, and ends with a
newline by default:

```python
print("accepted", 3)                     # accepted 3
print("a", "b", sep="|")                # a|b
print("loading", end="...")
print("done")                            # loading...done
```

`input` displays a prompt and always returns a string. Conversion may fail and must
be handled deliberately:

```python
raw = input("Record count: ")
try:
    count = int(raw)
except ValueError:
    print("Count must be an integer")
else:
    print(f"Accepted count: {count}")
```

Interactive input is unsuitable for unattended automation unless explicitly
enabled. Command-line arguments and configuration are covered later.

### 1.2.5 The main guard explained

Every module receives a `__name__`. For the top-level module it is `"__main__"`;
when imported, it is normally the import name. Keep orchestration in `main` and
return an integer exit status:

```python
def main() -> int:
    print("Atlas is ready")
    return 0


if __name__ == "__main__":
    raise SystemExit(main())
```

`SystemExit(0)` means success to the operating system; nonzero values indicate
documented failure classes. The guard prevents the call to `main`, but all other
top-level statements still run during import.

### 1.3 Help and inspection

```python
help(str.split)
type(42)
isinstance(42, int)
dir(str)
```

`type` reports the concrete class; `isinstance` respects inheritance and is usually better for behavioral checks. `dir` is discovery, not a stable public API list.

### 1.3.1 Getting documentation without guessing

Use `help(object)` in the REPL, `python -m pydoc module`, an IDE's signature view,
and the official Python documentation. Inspect a callable's docstring/signature:

```python
import inspect

print(str.split.__doc__)
print(inspect.signature(str.split))
```

Names beginning with `_` are generally non-public implementation details. `dir`
includes such names and dynamically discovered attributes; it is a discovery tool,
not a compatibility guarantee.

### 1.4 Reading errors and tracebacks

A `SyntaxError` means parsing failed and execution did not start. Runtime exceptions
occur after valid code begins executing. Read a traceback from its final line, then
move upward to the first relevant frame in your code.

```python
def divide(total: int, count: int) -> float:
    return total / count


divide(10, 0)
```

The final line is `ZeroDivisionError: division by zero`. The preceding frame points
to `return total / count`; its caller shows how invalid state reached that line.
Do not fix an error by broadly catching and ignoring it. Identify the violated rule,
choose where validation/recovery belongs, and add a test.

Useful first diagnostic facts:

```python
import platform
import sys

print(sys.version)
print(sys.executable)
print(platform.platform())
```

### 1.5 Building the first Atlas program

Create this structure:

```text
atlas-learning/
├── atlas.py
└── test_atlas.py
```

`atlas.py`:

```python
def status_message(name: str) -> str:
    cleaned = name.strip()
    if not cleaned:
        raise ValueError("name cannot be blank")
    return f"{cleaned} is ready"


def main() -> int:
    print(status_message("Atlas"))
    return 0


if __name__ == "__main__":
    raise SystemExit(main())
```

`test_atlas.py` initially uses plain assertions:

```python
from atlas import status_message

assert status_message("Atlas") == "Atlas is ready"
assert status_message("  Atlas  ") == "Atlas is ready"

try:
    status_message("   ")
except ValueError as exc:
    assert "blank" in str(exc)
else:
    raise AssertionError("blank name was accepted")
```

Verify three different contracts:

```console
$ python atlas.py
Atlas is ready
$ python test_atlas.py
$ python -c "import atlas"
```

The test command and import command should print nothing and exit successfully.

### 1.6 A repeatable debugging loop

1. Preserve the exact failing input and error.
2. Reproduce it with the smallest deterministic program.
3. State expected and actual behavior.
4. Read the final exception and relevant frames.
5. Inspect values immediately before the violation.
6. Fix the cause, not merely the symptom.
7. Add a regression test that failed before the fix.
8. Run related tests and the original scenario.

Temporary `print` calls are useful, but learn `breakpoint()` and a debugger later.
Remove accidental diagnostic output from library code.

### Common mistakes

- Naming a file `json.py`, `typing.py`, or `pandas.py`, shadowing the real module.
- Copying `>>>` REPL prompts into a script.
- Installing packages globally as root.
- Treating a traceback as noise instead of reading its final exception and frames.
- Running a file from a different current directory and assuming relative paths are
  relative to the source file.
- Believing installation succeeded without checking `sys.executable` and the pip
  associated with it.
- Putting network/database/file mutations at module top level.
- Confusing notebook output state with reproducible top-to-bottom execution.
- Naming a variable with a keyword or relying on different capitalization.

### Exercises and project

1. **Foundation:** print Python version, implementation, executable, current working
   directory and source-file directory. Explain each value.
2. **Foundation:** predict and verify the output order of a file containing three
   top-level prints and two function calls.
3. **Foundation:** intentionally produce `SyntaxError`, `NameError`, `TypeError`,
   `ValueError` and `ZeroDivisionError`; identify the final exception and relevant frame.
4. **Foundation:** use `help`, `dir`, `type`, `isinstance` and
   `inspect.signature` on three built-ins; explain what each tool does *not* prove.
5. **Application:** implement the Atlas program and tests above from a blank
   directory without copying. Add a `--version` behavior after Chapter 40.
6. **Challenge:** run the same module as a file and with `-m`; record `__name__`,
   `__package__`, current directory and import behavior, then explain differences.

### Completion criteria

You can create and activate a clean environment, prove which executable runs, use
REPL/script/module modes deliberately, explain top-level execution and indentation,
write an import-safe `main`, inspect documentation, and diagnose five basic errors.
Your first Atlas script, test file and import check all pass from a blank workspace.

### Summary

Python runs modules in order, indentation is syntax, the REPL is for exploration, scripts are reproducible artifacts, and interpreter identity controls packages.
Source is parsed before execution, function bodies run only when called, imports can
execute top-level code, `input` returns text, `print` is a side effect, and tracebacks
are structured diagnostic evidence. Reproducibility begins by knowing the exact
interpreter, directory, input and command.

---

## Chapter 2 — Variables and Built-in Functions

> **Level:** Beginner · **Prerequisites:** Chapter 1

### Learning objectives

Explain names, objects, identity, type, value, mutability and lifetime; create and
rebind names; recognize core scalar types; convert external text safely; use
essential built-ins; unpack values; and diagnose aliasing, shadowing and conversion
errors.

### 2.0 The object model

Python evaluates the right side of an assignment to obtain an object, then binds
the left-side name to it. A name is not a typed storage box.

```text
name ───────► object
other_name ─┘
```

Every object has identity, type and value. Identity distinguishes it during its
lifetime; type determines supported operations; value is the represented data.

```python
value = 42
print(type(value))            # <class 'int'>
print(value)                  # 42
print(id(value))              # runtime-specific; never persist or compare this
```

### 2.0.1 Core scalar values

```python
nothing = None
enabled = True
count = 1_000
ratio = 3.5
impedance = 2 + 3j
label = "sensor-a"
payload = b"ABC"
```

`None` means absence—not zero or empty text. `bool` subclasses `int`, so
`True == 1`; reject booleans explicitly when a count must be an integer but not a
truth value. Python integers grow as needed; floats are finite-precision binary
approximations. Strings contain Unicode text; bytes contain octets.

### 2.1 Names point to objects

Assignment binds a name to an object; it does not copy an object or declare a fixed storage box.

```python
records = [{"id": 1}]
alias = records
alias.append({"id": 2})
assert records is alias and len(records) == 2

copy = records.copy()          # shallow outer copy
assert copy == records and copy is not records
```

`==` asks whether values are equal; `is` asks whether two references identify the same object. Use `is None`, not `== None`. Mutable objects (lists, dicts, sets) can change in place; immutable objects (integers, strings, tuples of immutable values) cannot.

### 2.2 Naming, unpacking, and constants

### 2.1.1 Binding, rebinding, mutation, and aliasing

Rebinding changes which object a name points to; mutation changes an existing
object while preserving its identity.

```python
count = 10
count = count + 1                         # new int, then rebinding

items = [1, 2]
alias = items
before = id(items)
items.append(3)                           # mutation
assert id(items) == before
assert alias == [1, 2, 3]
```

Shared objects are useful, but ownership must be explicit. Ask who may mutate the
object and whether a function promises a snapshot or a live shared value.

### 2.1.2 Identity and equality

```python
left = [1, 2]
right = [1, 2]
alias = left
assert left == right
assert left is not right
assert alias is left
```

Interpreter caching can make some integers or strings incidentally identical. Never
use `is` for ordinary value equality; use it for sentinels such as `None`.

### 2.1.3 Mutability is sometimes shallow

Common immutable types include `NoneType`, `bool`, `int`, `float`, `complex`, `str`,
`bytes`, `tuple`, `frozenset` and `range`. Lists, dictionaries, sets, bytearrays and
most user objects are mutable. A tuple prevents replacing slots but does not freeze
objects stored inside:

```python
configuration = ("production", ["api"])
configuration[1].append("worker")
assert configuration == ("production", ["api", "worker"])
```

### 2.1.4 Lifetime and deletion

`del` removes a binding or container entry; it is not a command to destroy an
object. Other references may keep it alive. Files and locks require explicit context
management rather than reliance on garbage collection.

```python
data = [1, 2]
alias = data
del data
assert alias == [1, 2]
```

### 2.1.5 Dynamic typing and annotations

A name can legally be rebound to another type. Keep one logical role consistent and
use annotations so static tools can detect mistakes:

```python
event_count: int = 12
# event_count = "twelve"  # runtime permits rebinding; checker reports mismatch
```

Annotations do not validate hostile input. Runtime conversion and validation remain
necessary at the boundary.

```python
source_name = "sensor-a"
count, unit = 12, "events"
first, *middle, last = [1, 2, 3, 4]
MAX_BATCH_SIZE = 10_000        # convention, not enforced immutability
```

Use descriptive `snake_case`, `UPPER_CASE` for constants, and avoid shadowing built-ins (`list`, `id`, `str`). Deleting a name with `del` removes a binding; object lifetime depends on remaining references and implementation/runtime behavior.

### 2.2.1 Naming rules and conventions

Identifiers contain letters, digits after the first character, and underscores.
Keywords cannot be names. Public code usually chooses portable descriptive ASCII
names even though Unicode identifiers are supported.

```python
import keyword
assert keyword.iskeyword("class")
assert not keyword.iskeyword("event_count")
```

Use nouns for values, verbs for functions, and positive Boolean questions such as
`is_valid`. A leading underscore means non-public by convention. Do not invent
double-leading-and-trailing names reserved for Python protocols.

### 2.2.2 Assignment and unpacking

```python
x = y = 0
width, height = 640, 480
left, right = right, left
first, *middle, last = [1, 2, 3, 4]
assert middle == [2, 3]
```

The entire right side is evaluated before targets are rebound. Starred unpacking
creates a list and verifies shape. Augmented assignment depends on type:

```python
numbers = [1]
alias = numbers
numbers += [2]                            # list mutation
assert alias == [1, 2]

text = "a"
old_text = text
text += "b"                              # new string and rebinding
assert old_text == "a" and text == "ab"
```

### 2.2.3 Constants, sentinels, and copying

Uppercase constants are conventions, not enforced immutability. When `None` is a
valid value, a unique sentinel distinguishes it from “not supplied”:

```python
_MISSING = object()

def describe(value: object = _MISSING) -> str:
    if value is _MISSING:
        return "not supplied"
    if value is None:
        return "explicitly empty"
    return str(value)
```

Assignment never copies. `.copy()`, constructors and slices are usually shallow:

```python
original = [{"tags": ["new"]}]
outer_copy = original.copy()
outer_copy[0]["tags"].append("reviewed")
assert original[0]["tags"] == ["new", "reviewed"]
```

Deep copy is not automatically correct for files, locks, sockets, caches or shared
domain identities. Prefer explicit ownership and immutable domain values.

### 2.3 Essential built-ins

| Built-in | Purpose |
|---|---|
| `print`, `input` | Text output/input; validate all input strings. |
| `len`, `min`, `max`, `sum` | Aggregate sized/iterable values. |
| `type`, `isinstance` | Runtime type inspection. |
| `int`, `float`, `str`, `bool` | Explicit conversion/construction. |
| `enumerate`, `zip` | Add indices; iterate corresponding streams. |
| `sorted`, `reversed` | Produce ordered/reversed iteration. |
| `any`, `all` | Boolean reduction with short-circuiting. |
| `range` | Lazy arithmetic sequence for iteration. |

```python
raw = " 42 "
try:
    event_count = int(raw)
except ValueError:
    event_count = 0

names = ["alpha", "beta"]
for position, name in enumerate(names, start=1):
    print(position, name)
```

**TRAP:** `bool("False")` is `True` because any nonempty string is truthy. Parse textual booleans explicitly.

### Scope preview

### 2.3.1 Conversion is validation work

```python
assert int("42") == 42
assert int("101", 2) == 5
assert float("3.5") == 3.5
assert str(42) == "42"
assert list("abc") == ["a", "b", "c"]
```

`int(3.9)` truncates toward zero; it does not round. Conversion can fail or lose
information, so never replace malformed business input with zero without an
explicit requirement.

```python
def parse_boolean(raw: str) -> bool:
    normalized = raw.strip().casefold()
    if normalized in {"true", "yes", "1"}:
        return True
    if normalized in {"false", "no", "0"}:
        return False
    raise ValueError(f"invalid boolean: {raw!r}")
```

### 2.3.2 Aggregation built-ins

```python
values = [3, 1, 4]
assert len(values) == 3
assert min(values) == 1
assert max(values) == 4
assert sum(values, start=10) == 18
assert any(value > 3 for value in values)
assert all(value > 0 for value in values)
assert sorted(values) == [1, 3, 4]
assert list(reversed(values)) == [4, 1, 3]
```

`min`/`max` reject empty iterables unless given `default`. For empty input, `any`
is false and `all` is true. `sorted` returns a list; `reversed` is lazy.

```python
names = ["Zahra", "ali", "Reza"]
assert sorted(names, key=str.casefold) == ["ali", "Reza", "Zahra"]
```

### 2.3.3 Iteration helpers

```python
names = ["alpha", "beta"]
assert list(enumerate(names, 1)) == [(1, "alpha"), (2, "beta")]
assert list(zip([1, 2], names, strict=True)) == [(1, "alpha"), (2, "beta")]
assert list(range(2, 8, 2)) == [2, 4, 6]
```

Ordinary `zip` truncates to the shorter input; strict zip detects mismatched data.
`range` represents arithmetic boundaries lazily and excludes its stop.

### 2.3.4 `str`, `repr`, `callable`, and introspection

`str` targets readable display; `repr` targets an unambiguous developer view.

```python
value = "line\nnext"
assert repr(value) == "'line\\nnext'"
assert callable(len)
```

Use dynamic `getattr` only when attribute names truly come from metadata; ordinary
dot access is clearer and safer for a known interface.

Name lookup follows Local → Enclosing → Global → Builtins (LEGB). Assignment in a function creates a local name unless `global`/`nonlocal` is declared; prefer returning values over mutating globals.

```python
list = [1, 2]                             # shadows built-in: avoid
del list
assert list("abc") == ["a", "b", "c"]
```

### Worked example — validated record

```python
def build_record(source_raw: str, count_raw: str) -> dict[str, object]:
    source = source_raw.strip().casefold()
    if not source:
        raise ValueError("source cannot be blank")
    try:
        count = int(count_raw)
    except ValueError as exc:
        raise ValueError(f"count must be an integer: {count_raw!r}") from exc
    if count < 0:
        raise ValueError("count cannot be negative")
    return {"source": source, "count": count}


assert build_record(" Alpha ", " 12 ") == {"source": "alpha", "count": 12}
```

### Common mistakes

- Thinking assignment copies or permanently fixes a name's type.
- Comparing ordinary values with `is`.
- Treating `None`, zero, false and empty text as interchangeable.
- Assuming tuple immutability recursively freezes values.
- Calling `bool` to parse text.
- Shadowing a built-in or hiding a conversion failure with a false default.
- Forgetting ordinary `zip` truncates.

### Exercises and project

Read a source name and count, normalize whitespace, convert the count, reject negatives, and print a record. Explain every name/object relationship after a shallow copy.

1. Draw reference graphs for two aliases before/after mutation and rebinding.
2. Predict equality and identity for equal lists, aliases and `None`.
3. Demonstrate shallow-copy sharing with three nested levels, then redesign ownership.
4. Write strict integer and Boolean parsers with contextual errors.
5. Test every built-in above on empty and boundary inputs.
6. Extend `build_record` while proving raw arguments remain unchanged.

### Completion criteria

Predict bindings and visible mutations from a reference graph; distinguish
identity/type/value; classify common mutability; convert text safely; choose
essential built-ins; avoid shadowing; and implement/test the record builder.

---

## Chapter 3 — Operators

> **Level:** Beginner · **Prerequisites:** Chapters 1–2

### Learning objectives

Evaluate arithmetic, comparison, Boolean, membership, identity, bitwise and
assignment operators; predict precedence and short-circuiting; distinguish floor
division from truncation; choose numeric representations; and avoid truthiness,
chained-comparison and floating-point traps.

### 3.0 Operators, operands, and expressions

An operator combines or transforms operands to produce a value. Operators dispatch
behavior based on operand types: `+` adds numbers, concatenates compatible sequences,
and may call a user-defined protocol later.

```python
assert 2 + 3 == 5
assert "py" + "thon" == "python"
assert [1] + [2] == [1, 2]
```

Similar spelling does not imply interchangeable meaning. Multiplying a sequence
repeats references and may create aliasing in nested mutable structures.

### 3.1 Families and precedence

### 3.1.1 Arithmetic operators

| Operator | Meaning | Example result |
|---|---|---|
| `+`, `-` | addition/subtraction | `7 - 3 == 4` |
| `*` | multiplication/repetition | `3 * 4 == 12` |
| `/` | true division | `7 / 2 == 3.5` |
| `//` | floor division | `7 // 2 == 3` |
| `%` | modulo | `7 % 2 == 1` |
| `**` | exponentiation | `2 ** 3 == 8` |
| unary `+`, `-` | numeric sign | `-(-2) == 2` |

Division by numeric zero raises `ZeroDivisionError`. For integers `a ==
(a // b) * b + (a % b)` when `b != 0`.

```python
for a, b in [(7, 3), (-7, 3), (7, -3)]:
    assert a == (a // b) * b + (a % b)
```

`//` floors toward negative infinity, so `-7 // 3 == -3`. `int(-7 / 3)` truncates
toward zero and is `-2`; they solve different requirements.

Exponentiation binds more tightly than unary minus: `-2 ** 2` is `-(2 ** 2)` and
equals `-4`; write `(-2) ** 2` for `4`.

### 3.1.2 Precedence and associativity

From tighter to looser in common beginner expressions: parentheses/calls/indexing,
`**`, unary signs/`~`, `* / // %`, `+ -`, shifts, `&`, `^`, `|`, comparisons,
`not`, `and`, `or`, conditional expression, assignment expression.

```python
assert 2 + 3 * 4 == 14
assert (2 + 3) * 4 == 20
assert 2 ** 3 ** 2 == 2 ** (3 ** 2)       # exponentiation is right-associative
```

Do not make readers memorize an opaque expression. Parenthesize mixed families when
it clarifies domain intent, even if precedence already gives the desired result.

### 3.1.3 Comparison operators

`< <= > >= == !=` produce Boolean results according to type semantics. Ordering
mixed unrelated types usually raises `TypeError`; normalize data first.

```python
age = 20
assert 18 <= age < 65                     # equivalent logical chain
assert "a" < "b"                         # Unicode code-point lexicographic order
```

Chained comparisons evaluate the middle operand once and behave like conjunctions,
but they are not a general replacement for `and`.

```python
def next_value() -> int:
    print("called")
    return 5

assert 0 < next_value() < 10              # prints called once
```

`float("nan")` is unequal to itself and unordered. Use `math.isnan` and define a
missing/nonfinite policy instead of ordinary equality.

### 3.1.4 Boolean operators and truthiness

Falsy built-ins include `None`, `False`, numeric zero, and empty strings/containers.
Other ordinary objects are truthy unless their class defines otherwise.

```python
assert not None
assert not 0
assert not ""
assert bool("False")                      # nonempty text is truthy
```

`not` always returns `bool`. `and` and `or` short-circuit and return an operand:

```python
assert ("" or "fallback") == "fallback"
assert ("value" and 42) == 42

def fail() -> None:
    raise AssertionError("must not run")

assert False and fail() is False
assert True or fail() is True
```

Short-circuiting safely guards dependent work:

```python
if record is not None and record.is_valid():
    process(record)
```

Defaulting with `value or default` wrongly replaces legitimate `0`, `False`, or
empty text. Test `is None` when only absence should trigger the default.

### 3.1.5 Conditional expressions

```python
status = "adult" if age >= 18 else "minor"
```

Both branches are expressions but only the selected branch evaluates. Use this for
small value choices; use `if` statements for multi-step behavior or side effects.

```python
total = 7 + 3
ratio = 7 / 3       # true division: float
whole = 7 // 3      # floor division: 2
remainder = 7 % 3
power = 2 ** 10
```

`//` floors toward negative infinity (`-7 // 3 == -3`), not toward zero. Use parentheses when intent is not immediately obvious. Arithmetic may dispatch special methods on user types.

Comparisons chain: `0 <= x < 100` evaluates `x` once. Boolean `and`/`or` short-circuit and return an operand, not necessarily `bool`:

```python
label = user_label or "unknown"
if record is not None and record.valid:
    process(record)
```

This defaulting pattern treats every falsy value—including `0` and `""`—as absent. Use `if value is None` when zero/empty is valid.

### 3.2 Membership, identity, bitwise, and assignment expressions

### 3.2.1 Membership

`in` and `not in` ask a container/iterable protocol. Dictionary membership checks
keys, not values.

```python
record = {"id": 7, "status": "ok"}
assert "id" in record
assert 7 not in record
assert 7 in record.values()
assert "yth" in "python"
```

Repeated membership in a list is linear; a set/dictionary offers average constant
lookup when elements are hashable. Choose based on required ordering, duplicates and
workload rather than converting blindly.

### 3.2.2 Identity

Use `is`/`is not` for `None`, unique sentinels, or deliberate object identity. Value
equality can execute custom code; identity cannot be overloaded.

### 3.2.3 Bitwise operators

`& | ^ ~ << >>` operate on integer bit patterns; `& | - ^` also express set algebra.

```python
READ = 0b001
WRITE = 0b010
DELETE = 0b100
permissions = READ | WRITE
assert permissions & WRITE
permissions &= ~WRITE
assert not permissions & WRITE
```

For ordinary permission domains, an enum or set of explicit names is often clearer.
Never confuse Boolean `and` with bitwise `&`: they have different return values,
precedence and short-circuit behavior.

### 3.2.4 Assignment and walrus

`=`, augmented assignments and `:=` bind names. Assignment is a statement; the
walrus binds within a larger expression and should eliminate meaningful duplication:

```python
while (line := stream.readline()) != "":
    consume(line)
```

Do not use `:=` merely to compress control flow. Parentheses are often required by
grammar and help reveal the binding scope.

```python
"id" in record            # mapping membership checks keys
a is b                    # identity, not equality
flags = 0b0010 | 0b1000
enabled = bool(flags & 0b1000)

if (line := stream.readline()) != "":
    consume(line)
```

Bitwise operators act on integer bits (and sets define meaningful `|`, `&`, `-`, `^`). The walrus operator binds within an expression; use it only when it removes duplication without hiding control flow.

### 3.3 Numeric precision

Binary floats cannot exactly represent many decimal fractions. Use `math.isclose` with domain tolerances for approximate results; use `decimal.Decimal` constructed from strings for exact decimal rules such as money; use `fractions.Fraction` for rational arithmetic.

```python
import math
assert math.isclose(0.1 + 0.2, 0.3, rel_tol=1e-12)
```

### 3.3.1 Integers, floats, Decimal, and Fraction

```python
from decimal import Decimal, ROUND_HALF_EVEN
from fractions import Fraction

price = Decimal("19.95")
total = (price * 3).quantize(Decimal("0.01"), rounding=ROUND_HALF_EVEN)
assert total == Decimal("59.85")
assert Fraction(1, 3) + Fraction(1, 6) == Fraction(1, 2)
```

Construct `Decimal` from text, not an already inexact float. Decimal does not
automatically define correct financial policy: currency scale, rounding moment and
rounding mode remain requirements. Fractions are exact rationals but numerator and
denominator can grow.

`math.isclose` needs domain-chosen relative and absolute tolerances. Near zero, an
absolute tolerance is often necessary:

```python
assert math.isclose(1e-13, 0.0, abs_tol=1e-12)
```

### Worked example — safe percentage

```python
def acceptance_percentage(accepted: int, rejected: int) -> float | None:
    if isinstance(accepted, bool) or isinstance(rejected, bool):
        raise TypeError("counts cannot be booleans")
    if accepted < 0 or rejected < 0:
        raise ValueError("counts cannot be negative")
    total = accepted + rejected
    return None if total == 0 else accepted / total * 100


assert acceptance_percentage(3, 1) == 75.0
assert acceptance_percentage(0, 0) is None
```

### Common mistakes

- Assuming floor division truncates toward zero.
- Comparing measured floats with exact `==` without a tolerance policy.
- Constructing `Decimal` from a float or omitting rounding rules.
- Treating `and`/`or` as Boolean-only operators.
- Using `or` defaults when zero/empty is valid.
- Confusing membership, identity and equality.
- Mixing bitwise and Boolean operators without parentheses.
- Writing clever walrus expressions that hide state changes.

### Exercises and project

Compute accepted/rejected counts and percentage without division by zero. Represent record-status flags and explain why `and` is not the same as `&`.

1. Build a table predicting `/`, `//` and `%` for positive/negative operands.
2. Parenthesize ten mixed expressions, predict results, then verify.
3. Prove short-circuit behavior with functions that record calls.
4. Implement None-aware defaults that preserve `0`, `False` and `""`.
5. Compare float, Decimal and Fraction for three domain scenarios.
6. Extend the percentage function with tests for booleans, negatives and huge ints.

### Completion criteria

Predict precedence and evaluation order; explain operand-returning Boolean logic;
distinguish equality/identity/membership; apply bit flags deliberately; select a
numeric representation with explicit precision policy; and test all percentage
boundaries.

---

## Chapter 4 — Strings

> **Level:** Beginner · **Prerequisites:** Chapters 1–3

### Learning objectives

Explain Unicode text versus encoded bytes; construct and escape strings; index and
slice safely; search, split, join, normalize, compare and format text; parse bounded
records; and choose explicit encoding/error/security policies.

### 4.0 Mental model: text is not bytes

Human text consists of Unicode code points. Files, networks and devices carry bytes.
An encoding such as UTF-8 maps between those domains. `len(str)` counts code points,
not displayed glyphs or encoded bytes.

```python
composed = "é"
decomposed = "e\u0301"
assert composed != decomposed
assert len(composed) == 1 and len(decomposed) == 2

import unicodedata
assert unicodedata.normalize("NFC", composed) == unicodedata.normalize("NFC", decomposed)
```

Preserve display text and derive a separate normalized search key when presentation
matters. Normalization is not automatically correct for passwords or opaque tokens.

```python
word = "سلام"
encoded = word.encode("utf-8")
assert isinstance(encoded, bytes)
assert encoded.decode("utf-8") == word
```

Wrong decoding may fail or corrupt text. Prefer strict errors for identifiers/data;
lossy replacement is acceptable only under an explicit display policy.

```python
try:
    b"valid\xfftext".decode("utf-8")
except UnicodeDecodeError:
    pass
else:
    raise AssertionError("invalid UTF-8 accepted")
```

Byte indexing yields an integer octet; string indexing yields a one-character str.
Text and bytes cannot be concatenated without an explicit encode/decode boundary.

### 4.0.1 Construction and escaping

```python
single = 'He said "hello"'
double = "It's ready"
multiline = """first
second"""
raw_pattern = r"\d+\.\d+"
assert "\n" in multiline
```

Escapes include `\n`, `\t`, `\\`, quotes and Unicode forms. Raw strings reduce
escape processing but cannot end with one unmatched backslash. Use `pathlib` for
paths rather than relying on clever string escaping.

### 4.0.2 Indexing and slicing

```python
word = "python"
assert word[0] == "p" and word[-1] == "n"
assert word[1:4] == "yth"
assert word[:3] == "pyt" and word[3:] == "hon"
assert word[::2] == "pto"
assert word[::-1] == "nohtyp"
```

Indexing outside bounds raises `IndexError`; slicing clamps safely and excludes the
stop. A zero step raises `ValueError`. Strings are immutable, so slicing/methods
produce new strings and item assignment is forbidden.

### 4.0.3 Searching and classification

```python
text = "atlas-event-42"
assert text.startswith("atlas") and text.endswith("42")
assert "event" in text
assert text.find("event") == 6
assert text.count("-") == 2
```

`find` returns `-1` when absent; `index` raises. Classification methods such as
`isdecimal`, `isdigit`, `isalpha`, `isalnum` and `isspace` follow Unicode rules and
may accept more than ASCII. Validate the exact domain required.

### 4.0.4 Trimming, splitting, and joining

`strip(chars)` removes any listed characters repeatedly from the ends; it does not
remove an exact substring.

```python
assert "  name  ".strip() == "name"
assert "xynameyx".strip("xy") == "name"
assert "sensor-alpha".removeprefix("sensor-") == "alpha"
assert "report.csv".removesuffix(".csv") == "report"

assert " a  b \n c ".split() == ["a", "b", "c"]
assert "a,,b".split(",") == ["a", "", "b"]
assert "key:value:extra".split(":", 1) == ["key", "value:extra"]

key, separator, value = "status:ok".partition(":")
assert (key, separator, value) == ("status", ":", "ok")
assert ",".join(["a", "b", "c"]) == "a,b,c"
```

For large construction collect pieces and join once. Use CSV/JSON parsers for
structured formats rather than manual splitting.

### 4.0.5 Replacement, case, and line handling

```python
assert "one one".replace("one", "1", 1) == "1 one"
assert "a\r\nb\nc".splitlines() == ["a", "b", "c"]
table = str.maketrans({"-": "_", "/": "_"})
assert "a-b/c".translate(table) == "a_b_c"
assert "Straße".casefold() == "STRASSE".casefold()
```

`casefold` supports caseless matching better than `lower`, but it is not a complete
locale collation or confusable-character security policy.

### 4.0.6 Formatting values

```python
name = "Atlas"
value = 12345.678
assert f"{name:>10}" == "     Atlas"
assert f"{value:,.2f}" == "12,345.68"
assert f"{42:08d}" == "00000042"
assert f"{0.875:.1%}" == "87.5%"
assert f"{255:#x}" == "0xff"
```

Formatting changes presentation, not data. F-strings do not escape SQL, shell,
HTML or URLs; use parameters, argument arrays, template autoescaping and URL tools.

### 4.0.7 Complete bounded parser

```python
from dataclasses import dataclass

@dataclass(frozen=True)
class ParsedRecord:
    display_source: str
    search_source: str
    count: int

def parse_record(line: str, *, max_length: int = 100) -> ParsedRecord:
    if len(line) > max_length:
        raise ValueError("record is too long")
    raw_source, separator, raw_count = line.partition(":")
    if not separator:
        raise ValueError("missing ':' separator")
    display = raw_source.strip()
    if not display:
        raise ValueError("source cannot be blank")
    search = unicodedata.normalize("NFC", display).casefold()
    try:
        count = int(raw_count.strip())
    except ValueError as exc:
        raise ValueError(f"invalid count: {raw_count!r}") from exc
    if count < 0:
        raise ValueError("count cannot be negative")
    return ParsedRecord(display, search, count)


assert parse_record(" Café : 2 ").search_source == "café"
```

### 4.0.8 Worked case study — multilingual identifiers

Suppose Atlas receives user-visible source names but also needs deterministic lookup.
One string cannot safely serve both roles. Keep the original display value, derive a
documented canonical key, and reject input outside resource limits.

```python
import re

CONTROL_CHARACTER = re.compile(r"[\x00-\x1f\x7f]")

def canonical_source(raw: str, *, maximum: int = 64) -> tuple[str, str]:
    display = raw.strip()
    if not display:
        raise ValueError("source cannot be blank")
    if len(display) > maximum:
        raise ValueError("source is too long")
    if CONTROL_CHARACTER.search(display):
        raise ValueError("source contains a control character")
    key = unicodedata.normalize("NFC", display).casefold()
    return display, key


assert canonical_source("  Café  ") == ("Café", "café")
```

This policy intentionally does not remove punctuation, transliterate scripts or
collapse internal whitespace. Adding those transformations can merge distinct
names. If uniqueness has legal/security consequences, specify allowed scripts,
confusable handling and migration rules with domain experts.

### 4.0.9 Parsing versus validation versus escaping

These are different operations:

- parsing turns representation into structure (`"42"` → integer 42);
- validation checks whether structure obeys domain constraints;
- normalization chooses a canonical representation;
- escaping/encoding prepares a value for one output context.

An HTML-escaped value is not safe SQL, a shell-quoted value is not a filesystem
authorization check, and URL encoding is not validation. Keep raw input, validated
domain data and output representations conceptually separate.

```python
from urllib.parse import urlencode

query = urlencode({"source": "café & tea", "limit": 10})
assert query == "source=caf%C3%A9+%26+tea&limit=10"
```

### 4.0.10 Testing string boundaries

Good string tests include empty and whitespace-only values, minimum/maximum length,
one beyond the maximum, combining marks, right-to-left text, emoji, embedded NUL,
newlines, invalid encoded bytes, and delimiter characters. Assert invariant results,
not a single platform's font rendering.

```python
for raw in ["", "   ", "\x00name", "x" * 65]:
    try:
        canonical_source(raw)
    except ValueError:
        pass
    else:
        raise AssertionError(f"invalid source accepted: {raw!r}")
```

### 4.1 Unicode text versus bytes

`str` stores Unicode text; `bytes` stores octets. Encoding converts text to bytes; decoding converts bytes to text.

```python
text = "café ☕"
payload = text.encode("utf-8")
assert payload.decode("utf-8") == text
```

Never decode arbitrary bytes without knowing the encoding/error policy. Unicode normalization matters for comparison/security:

```python
import unicodedata
normalized = unicodedata.normalize("NFC", text).casefold()
```

### 4.2 Slicing and methods

Strings are immutable sequences.

```python
name = "  Sensor-A  "
clean = name.strip().casefold()
prefix = clean[:6]
parts = "a,b,c".split(",")
joined = " | ".join(parts)
replaced = clean.removeprefix("sensor-")
```

`split()` without an argument collapses runs of whitespace; `split(" ")` preserves empty fields between literal spaces. Prefer `partition` when exactly one separator has semantic roles.

### 4.3 Formatting

```python
source = "alpha"
count = 1234
print(f"{source=}, {count:,}, mean={12.34567:.2f}")
```

F-strings evaluate expressions. Do not build SQL/shell commands with interpolation; use driver parameters/argument arrays. For logs, prefer deferred parameterized logging (`logger.info("count=%d", count)`).

### Exercises and project

### Common mistakes

- Confusing code points, graphemes and encoded bytes.
- Decoding without an encoding/error policy.
- Treating normalization/casefolding as universal security policy.
- Assuming `strip(".csv")` removes the suffix `.csv`.
- Repeatedly concatenating large text or manually parsing CSV/JSON.
- Building SQL, shell commands or HTML with f-strings.
- Forgetting that string methods return new values.

Normalize labels, validate a `SOURCE:COUNT` line, preserve Unicode display name and store a casefolded search key. Demonstrate why bytes and text cannot be concatenated directly.

1. Compare code-point length and UTF-8 byte length for Persian, emoji and ASCII.
2. Test NFC/NFD normalization while preserving display text.
3. Predict fifteen slices including negative steps and out-of-range bounds.
4. Contrast `split`, `partition`, `find`, `index`, `strip` and `removeprefix`.
5. Format counts, percentages, decimal values and developer representations.
6. Test the parser for empty, oversized, missing separator, invalid/negative count
   and canonically equivalent Unicode sources.

### Completion criteria

Explain text/bytes boundaries; select encoding/normalization policies; predict
slices; use search/split/join/format correctly; identify unsafe interpolation; and
implement/test the bounded parser.

---

## Chapter 5 — Lists

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 1–4

### Learning objectives

Create, inspect, update and traverse lists; predict indexing/slicing and mutation;
choose list versus tuple/deque/set/dict; reason about aliasing and copies; sort by
single/multiple keys; avoid mutation-during-iteration; use stacks safely; state
operation complexity; and design a tested batch transformation.

### 5.0 Mental model and construction

A list is an ordered, mutable sequence of object references. It permits duplicates,
supports integer positions, and grows dynamically. It need not contain one type,
but homogeneous domain lists are usually easier to validate and process.

```python
empty = []
also_empty = list()
numbers = [10, 20, 30]
characters = list("abc")
generated = list(range(3))
assert characters == ["a", "b", "c"]
assert generated == [0, 1, 2]
```

The list stores references, not embedded copies:

```text
items ──► [ slot 0 | slot 1 ]
             │        │
             ▼        ▼
           object   object
```

### 5.0.1 Indexing and slicing

```python
values = [10, 20, 30, 40, 50]
assert values[0] == 10 and values[-1] == 50
assert values[1:4] == [20, 30, 40]
assert values[:3] == [10, 20, 30]
assert values[::2] == [10, 30, 50]
assert values[::-1] == [50, 40, 30, 20, 10]
```

Indexing outside bounds raises `IndexError`; slices clamp and create a new outer
list containing the same referenced elements. Slice assignment can replace a range
with a differently sized iterable:

```python
values[1:3] = [21, 31, 41]
assert values == [10, 21, 31, 41, 40, 50]
```

### 5.0.2 Adding, replacing, and removing

```python
items = ["a", "b"]
items.append("c")                         # one object
items.extend(["d", "e"])                # each iterable element
items.insert(1, "new")
assert items == ["a", "new", "b", "c", "d", "e"]

items[0] = "A"
removed_last = items.pop()
removed_at_one = items.pop(1)
items.remove("c")                         # first equal value
assert removed_last == "e" and removed_at_one == "new"
```

`remove` raises `ValueError` if absent; `pop` raises `IndexError` for an invalid
position. `clear` removes all slots. `del` can delete an item/slice or a name.

`append([3, 4])` adds one nested list; `extend([3, 4])` adds two integers. This
distinction is a frequent source of wrong shapes.

### 5.0.3 Membership, location, and counting

```python
items = ["a", "b", "a"]
assert "b" in items
assert items.index("a") == 0
assert items.count("a") == 2
```

Membership, `index`, `count` and `remove` scan and use equality. Repeated lookup in
large data may warrant a set/dictionary index, provided ordering/duplicates are
handled separately.

### 5.0.4 Iterating without accidental mutation

```python
values = [1, 2, 3]
for position, value in enumerate(values):
    print(position, value)
```

Changing an existing slot during iteration can be intentional; changing length can
skip or repeat elements. Filter into a new list:

```python
values = [1, -1, 2, -2]
nonnegative = [value for value in values if value >= 0]
assert nonnegative == [1, 2]
```

If aliases must observe the update, replace the full slice:

```python
alias = values
values[:] = [value for value in values if value >= 0]
assert alias is values and alias == [1, 2]
```

### 5.0.5 Lists as stacks, not front queues

```python
stack: list[str] = []
stack.append("first")
stack.append("second")
assert stack.pop() == "second"            # LIFO
```

End append/pop are amortized O(1). Front insertion/pop shifts remaining references
and is O(n). Use `collections.deque` for FIFO or frequent operations at both ends.

### 5.0.6 Copy, alias, and nested structure

```python
original = [[1], [2]]
shallow = original.copy()
assert shallow is not original
assert shallow[0] is original[0]
shallow[0].append(99)
assert original == [[1, 99], [2]]
```

The classic repeated-row bug creates aliases:

```python
bad = [[0] * 3] * 3
bad[0][0] = 1
assert bad == [[1, 0, 0], [1, 0, 0], [1, 0, 0]]

good = [[0] * 3 for _ in range(3)]
good[0][0] = 1
assert good == [[1, 0, 0], [0, 0, 0], [0, 0, 0]]
```

Use `copy.deepcopy` only after deciding recursive duplication matches ownership.

### 5.0.7 Sorting correctly

`sorted(iterable)` creates a new list. `list.sort()` mutates and returns `None` so
accidental assignment is visible.

```python
values = [3, 1, 2]
ordered = sorted(values)
assert ordered == [1, 2, 3] and values == [3, 1, 2]

result = values.sort()
assert result is None and values == [1, 2, 3]
```

Keys are calculated once per element. Normalize incomparable data before sorting.

```python
records = [
    {"id": "b", "priority": 2},
    {"id": "a", "priority": 2},
    {"id": "c", "priority": 3},
]
records.sort(key=lambda record: (-record["priority"], record["id"]))
assert [record["id"] for record in records] == ["c", "a", "b"]
```

Python sorting is stable: equal keys retain input order. For mixed ascending and
descending fields, use a carefully justified tuple key or multiple stable sorts.

### 5.0.8 Complexity table

| Operation | Typical cost | Note |
|---|---:|---|
| `items[i]`, assignment | O(1) | integer position |
| `append`, end `pop` | amortized O(1) | occasional resize |
| front/middle insert/delete | O(n) | shifts references |
| membership/index/remove | O(n) | equality scan |
| slice of k elements | O(k) | new outer list |
| copy | O(n) | shallow references |
| sort | O(n log n) | stable; key once/item |
| reverse | O(n) | in place |

Big-O describes growth, not exact time. Equality cost, key work, cache behavior and
memory pressure still matter.

### 5.0.9 Choosing a collection

- list: ordered mutable sequence, duplicates and position matter;
- tuple: fixed positional shape or immutable sequence interface;
- deque: efficient operations at both ends;
- set: unique membership/algebra, no meaningful positional indexing;
- dict: lookup/update by key;
- array/NumPy: homogeneous numeric storage and vectorized computation.

### 5.0.10 Complete batch example

```python
from collections.abc import Iterable
from dataclasses import dataclass

@dataclass(frozen=True)
class Batch:
    accepted: tuple[dict[str, object], ...]
    rejected_positions: tuple[int, ...]

def prepare_records(records: Iterable[dict[str, object]]) -> Batch:
    accepted: list[dict[str, object]] = []
    rejected: list[int] = []
    seen_ids: set[str] = set()
    for position, source in enumerate(records, start=1):
        record = source.copy()
        event_id = str(record.get("id", "")).strip()
        if not event_id or event_id in seen_ids:
            rejected.append(position)
            continue
        seen_ids.add(event_id)
        record["id"] = event_id
        record["input_position"] = position
        accepted.append(record)
    accepted.sort(key=lambda item: str(item["id"]))
    return Batch(tuple(accepted), tuple(rejected))
```

The input dictionaries are not mutated; duplicate detection is indexed; rejected
positions preserve context; immutable outer results prevent accidental reshaping.

Lists are mutable, ordered arrays of references with amortized O(1) append and O(n) insertion/removal near the front.

Use a list when order, duplicates, positional access, and mutation are meaningful. A list stores references, not copies of objects; replacing a slot and mutating the referenced object are different operations.

```python
events: list[dict[str, object]] = []
events.append({"id": 1, "value": 3.5})
events.extend([{"id": 2, "value": 4.2}])
first = events[0]
tail_copy = events[1:]
```

### Core operations and costs

```python
queue = ["a", "b", "c"]
last = queue.pop()          # O(1) from end
first = queue.pop(0)       # O(n): remaining references shift
queue.insert(0, "new")    # O(n)
queue.remove("b")         # finds first equal value, then shifts
```

Indexing is O(1); membership and `index` are O(n); slicing copies selected references. Use `deque` for a queue with frequent work at both ends and a set/dictionary for repeated membership/lookup. Big-O is a growth model, not a timing promise—element equality and memory behavior still matter.

`append(x)` adds one object; `extend(iterable)` adds its elements. `list.sort()` mutates and returns `None`; `sorted(iterable)` returns a new list. Sorting is stable:

```python
events.sort(key=lambda e: (e["value"], e["id"]))
```

Because sorting is stable, multi-stage sorting is possible, though one tuple key is often clearer. Key functions run once per item. Sorting incomparable mixed types fails; normalize data before ordering. `reverse=True` reverses the entire ordering, so mixed ascending/descending fields may require a carefully designed key or multiple stable sorts.

### Copying and alias traps

```python
matrix_bad = [[0] * 3] * 3       # three references to one inner list
matrix = [[0] * 3 for _ in range(3)]

import copy
deep = copy.deepcopy(events)      # use deliberately; can be expensive/surprising
```

`copy()` and `[:]` duplicate the outer list only. Nested objects remain shared. `deepcopy` recursively attempts copying but may be inappropriate for files, sockets, locks, shared caches, or objects whose identity is meaningful. Often the best design is immutable domain values rather than indiscriminate deep copying.

Iteration while structurally mutating a list can skip items. Filter into a new list or iterate over a copy. Use `collections.deque` for efficient appends/pops at both ends.

```python
valid_events = [event for event in events if is_valid(event)]
events[:] = valid_events       # preserve list identity for existing aliases
```

### Worked example — stable priority batch

```python
def prepare_batch(records: list[dict[str, object]]) -> list[dict[str, object]]:
    copied = [record.copy() for record in records]
    for position, record in enumerate(copied):
        record["input_position"] = position
    copied.sort(key=lambda r: (-int(r["priority"]), int(r["input_position"])))
    return copied
```

The input is not mutated, nested ownership remains an explicit concern, and equal priorities retain input order.

### Common mistakes

- Assuming slicing or `.copy()` recursively duplicates nested objects.
- Building nested rows with `[[value] * width] * height`.
- Assigning the result of `.sort()`, `.append()`, `.extend()` or `.reverse()`.
- Removing elements while iterating over the same list.
- Using a list for repeated membership or front-queue operations.
- Confusing `append` with `extend` and creating the wrong nesting.
- Depending on mixed-type ordering or mutating sort keys during sorting.
- Returning a mutable internal list that callers can corrupt.

### Exercises and project

Build a batch, remove invalid events without mutating during iteration, sort by timestamp then ID, and compare shallow/deep copies.

1. Predict twenty indexing/slicing/slice-assignment cases before running them.
2. Implement append, insert, replace and removal tasks with explicit failure behavior.
3. Draw reference graphs for alias, shallow copy, nested repetition and explicit rows.
4. Compare list front-pop with deque popleft using a reproducible benchmark.
5. Sort records by descending priority then ascending timestamp/ID; prove stability.
6. Test `prepare_records` with empty input, a generator, missing/duplicate IDs and
   source dictionaries containing nested values.
7. Extend the batch with an explicit nested-copy ownership policy and document it.

### Completion criteria

Predict every indexing/mutation result; select the appropriate collection; explain
all operation costs; diagnose aliasing from a reference diagram; filter safely;
design stable sort keys; and implement/test the batch without mutating caller input.

---

## Chapter 6 — Tuples

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 2–5

### Learning objectives

Create and recognize tuples; distinguish grouping parentheses from tuple commas;
index, slice, compare and unpack fixed shapes; explain shallow immutability and
hashability; use tuples as composite keys; choose among tuple, `NamedTuple` and
dataclass; and design return values that remain readable as APIs evolve.

### 6.0 Why tuples exist

A tuple is an ordered, immutable sequence of references. Lists usually model a
variable-length collection of similar items; tuples often model a fixed number of
positions with distinct meanings, such as `(x, y)` or `(host, port)`.

```python
point = (3.0, 4.0)
server = ("localhost", 8000)
colors = tuple(["red", "green", "blue"])
assert len(point) == 2
```

The comma creates a tuple; parentheses group expressions and improve readability:

```python
not_a_tuple = (42)
one_item = (42,)
also_tuple = 1, 2, 3
assert isinstance(not_a_tuple, int)
assert isinstance(one_item, tuple)
```

### 6.0.1 Construction and conversion

```python
empty = ()
from_range = tuple(range(3))
from_text = tuple("abc")
assert from_range == (0, 1, 2)
assert from_text == ("a", "b", "c")
```

Converting a generator consumes it. Repeated tuple concatenation creates a new tuple
each time and can become quadratic; build a list and convert once.

### 6.0.2 Indexing, slicing, and iteration

```python
values = (10, 20, 30, 40)
assert values[0] == 10 and values[-1] == 40
assert values[1:3] == (20, 30)
assert values[::-1] == (40, 30, 20, 10)
assert 30 in values
```

Indexing outside bounds raises `IndexError`; slicing returns a tuple. You cannot
replace, append or remove a slot. `sorted(tuple_value)` deliberately returns a list;
wrap with `tuple(...)` only when the result contract requires immutability.

### 6.0.3 Comparison and ordering

Tuple equality compares length and corresponding values. Ordering is lexicographic:
compare the first unequal position. Elements encountered during ordering must be
comparable.

```python
assert (1, "a") < (1, "b")
assert (1, 2) < (1, 2, 0)

records = [(2, "b"), (1, "z"), (1, "a")]
assert sorted(records) == [(1, "a"), (1, "z"), (2, "b")]
```

This makes tuple sort keys useful, but relying on mysterious position meanings
damages readability.

### 6.0.4 Packing, unpacking, and shape validation

Packing collects comma-separated values; unpacking assigns positions to targets.

```python
record = "alpha", 42, True
source, count, valid = record
assert source == "alpha" and count == 42 and valid

head, *body, tail = (1, 2, 3, 4)
assert head == 1 and body == [2, 3] and tail == 4
```

Unpacking too few/many values raises `ValueError`. That early shape failure is useful
for internal fixed contracts, but external data needs contextual validation rather
than an unexplained unpacking traceback.

Nested unpacking mirrors shape:

```python
name, (x, y) = ("target", (10, 20))
assert (name, x, y) == ("target", 10, 20)
```

Use `_` for an intentionally ignored value only by convention; it still receives a
binding. Extended unpacking always puts the starred remainder in a list.

### 6.0.5 Multiple return values

Functions return one object. Comma-separated values create one tuple:

```python
def quotient_remainder(total: int, divisor: int) -> tuple[int, int]:
    if divisor == 0:
        raise ValueError("divisor cannot be zero")
    return divmod(total, divisor)


quotient, remainder = quotient_remainder(17, 5)
assert (quotient, remainder) == (3, 2)
```

Two or three obvious local results are readable. A public API returning many fields
should use named fields so adding/reordering values does not silently confuse users.

### 6.0.6 Shallow immutability and ownership

Tuple immutability prevents slot replacement, not mutation of referenced objects:

```python
snapshot = ("batch-1", ["new"])
snapshot[1].append("ready")
assert snapshot == ("batch-1", ["new", "ready"])
```

Therefore “tuple” does not automatically mean thread-safe, hashable, recursively
immutable, or a reliable snapshot. Build nested immutable values when those
properties are required.

### 6.0.7 Tuple keys and hash contracts

A tuple is hashable only when every element is hashable. Good composite keys use
stable immutable domain values:

```python
by_event: dict[tuple[str, str], float] = {
    ("alpha", "e1"): 12.5,
    ("alpha", "e2"): 15.0,
}
assert by_event[("alpha", "e1")] == 12.5
```

Do not include mutable state or values whose equality meaning can change while the
key is stored. Tuple keys are excellent for multi-dimensional coordinates and
compound indexes, but a dedicated frozen dataclass may communicate the domain better.

### 6.0.8 Performance and selection

Tuple indexing is O(1); slicing/copy-conversion is O(k); membership is O(n). Tuples
are often slightly smaller than equivalent lists, but choose them for semantics, not
micro-optimization. Immutability makes structural intent explicit and permits
hashing when all elements qualify.

Tuples are immutable sequences. Use them when the *number and meaning of positions are fixed*, when unpacking makes an interface clearer, or when a composite value must be hashable. Immutability prevents replacing tuple slots; it does not freeze mutable objects stored inside them.

```python
point = (3.0, 4.0)
x, y = point
single = (42,)                 # comma creates the tuple
also_a_tuple = 1, 2, 3         # parentheses are often optional
empty = ()
key = ("sensor-a", 2026)
```

### Sequence operations and immutability

Tuples support indexing, slicing, iteration, membership, `len`, `count`, and `index`, just like other sequences. They do not support item assignment, append, or removal.

```python
rgb = (120, 80, 200)
assert rgb[0] == 120
assert rgb[-1] == 200
assert rgb[1:] == (80, 200)
assert 80 in rgb

# rgb[0] = 0        # TypeError: tuple does not support item assignment
```

Concatenation creates a new tuple rather than changing the original. Repeated concatenation in a loop is therefore inefficient; build a list and convert once.

```python
parts = ["year", "month", "day"]
path_key = tuple(parts)
```

Immutability is shallow:

```python
configuration = ("production", ["api", "worker"])
configuration[1].append("scheduler")     # the referenced list is mutable
# configuration[1] = []                  # replacing the slot is forbidden
```

### Unpacking as an interface

Unpacking checks the shape and assigns meaningful local names. Starred unpacking captures the remaining values in a new list.

```python
host, port = ("localhost", 8000)
first, *middle, last = [10, 20, 30, 40]
assert middle == [20, 30]

left, right = right, left       # RHS tuple is evaluated before assignment

for event_id, status in [(1, "ok"), (2, "failed")]:
    print(event_id, status)
```

The number of targets must match unless one target is starred. An unpacking `ValueError` often reveals malformed external data early.

Functions return one object; comma-separated return values create a tuple:

```python
def divmod_checked(total: int, size: int) -> tuple[int, int]:
    if size == 0:
        raise ValueError("size must be non-zero")
    quotient, remainder = divmod(total, size)
    return quotient, remainder

pages, leftover = divmod_checked(103, 20)
```

### Hashability and composite keys

A tuple is hashable only if every element is hashable. This makes tuples useful for coordinates, cache keys, and multi-column dictionary indexes.

```python
temperatures: dict[tuple[str, str], float] = {}
temperatures[("Tehran", "2026-07-14")] = 38.5

visited_cells: set[tuple[int, int]] = {(0, 0), (0, 1)}

# hash(("region", []))  # TypeError: the nested list is unhashable
```

### Tuple, `NamedTuple`, or dataclass?

Use a plain tuple for a small local structure whose positions are obvious. Prefer a named model when values cross module boundaries or acquire domain rules.

```python
from typing import NamedTuple

class Coordinate(NamedTuple):
    latitude: float
    longitude: float

tehran = Coordinate(35.6892, 51.3890)
assert tehran.latitude == tehran[0]       # named and positional access
```

`NamedTuple` stays immutable and tuple-compatible. A frozen dataclass provides named fields and immutability but does not pretend to be a sequence. A normal dataclass is appropriate when controlled mutation is part of the model.

### Common mistakes

- Forgetting the comma in a one-item tuple: `(42)` is an `int`, `(42,)` is a tuple.
- Using a long tuple as a public record so callers must remember what index 6 means.
- Believing a tuple recursively freezes nested values.
- Returning many unrelated values instead of a result object.
- Using tuple concatenation as a growable buffer.

### Worked example — Grid route analyzer

```python
Point = tuple[int, int]

def analyze_route(route: list[Point]) -> dict[str, object]:
    if not route:
        raise ValueError("route cannot be empty")

    visited: set[Point] = set()
    repeated: set[Point] = set()
    distance = 0
    previous = route[0]

    for point in route:
        if point in visited:
            repeated.add(point)
        visited.add(point)
        distance += abs(point[0] - previous[0]) + abs(point[1] - previous[1])
        previous = point

    start, *_, end = route
    return {"start": start, "end": end, "distance": distance,
            "unique_cells": len(visited), "repeated": sorted(repeated)}
```

This example combines tuple records and unpacking with lists, sets, dictionaries, loops, validation, and sorting.

### Exercises

1. Use `(source, external_id)` as a deduplication key and reject duplicate events.
2. Replace an unclear five-tuple API with `NamedTuple`; explain the compatibility and readability trade-off.
3. Implement `bounding_box(points)` returning two coordinate tuples.
4. Demonstrate shallow tuple immutability with a nested dictionary, then redesign the value to be deeply immutable.
5. Extend the route analyzer to reject non-adjacent moves and report the first invalid pair.

6. Predict lexicographic ordering for ten tuple pairs and identify incomparable cases.
7. Compare a tuple key with a frozen dataclass key for validation and readability.
8. Write tests for empty, one-point, repeated, closed-loop and invalid routes.

### Chapter completion criteria

From a blank file, construct/unpack fixed shapes, explain comma syntax and shallow
immutability, determine hashability recursively, use compound keys, choose tuple
versus named record, and implement/test route analysis without ambiguous positions.

---

## Chapter 7 — Sets

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 2–6

### Learning objectives

After this chapter you can explain the set data model, select a set instead of a list/dictionary, use every major set operation and mutation method, preserve order when deduplicating, design hashable values, use `frozenset`, reason about complexity, and apply sets to permissions, validation, graph search, data reconciliation, and testing.

### 7.1 What problem does a set solve?

A set represents a collection in which **membership and uniqueness** matter but position and duplicate count do not. A list answers “what is the first value?” and preserves repeated observations. A set answers “have we seen this value?” and “how do these two groups overlap?”

```python
observed_ids = ["a", "b", "a", "c"]
unique_ids = {"a", "b", "c"}

assert observed_ids.count("a") == 2
assert "a" in unique_ids
```

Converting the list to a set discards two facts: original ordering and how many times each value appeared. If either matters, keep the list or use `Counter` alongside a set.

**MODEL:** CPython implements sets using a hash table. It computes an element's hash to locate a candidate slot and then uses equality to confirm the match. This provides average O(1) membership/add/remove, but worst-case behavior and exact layout/order are not contractual.

### 7.2 Creating sets correctly

```python
empty: set[str] = set()             # {} is an empty dictionary, not a set
numbers = {1, 2, 3}
letters = set("banana")             # {'b', 'a', 'n'} in unspecified display order
from_list = set([3, 1, 3, 2])
normalized = {name.strip().casefold() for name in [" Alice ", "ALICE", "Bob"]}
```

Set displays may look stable during one run, but order can vary with hashes, process randomization, versions, and mutations. Never use set iteration when an API/report requires stable order. Sort explicitly:

```python
for source in sorted(normalized):
    print(source)
```

### 7.3 Adding, removing, and updating

```python
tags = {"new", "verified"}
tags.add("important")                    # add one hashable element
tags.update(["archived", "verified"])   # add every element from an iterable

tags.remove("new")                       # KeyError if absent
tags.discard("missing")                  # no error if absent
item = tags.pop()                         # removes an arbitrary element
tags.clear()                              # remove every element
```

Choose `remove` when absence violates an invariant and should fail loudly. Choose `discard` for idempotent cleanup. `pop` does **not** mean “last item”; sets have no stack order.

`update`, `intersection_update`, `difference_update`, and `symmetric_difference_update` mutate the receiver. Operator expressions return new sets. The distinction matters when aliases exist:

```python
active = {"read", "write"}
alias = active
active &= {"read"}             # mutates active; alias now sees {'read'}

active = {"read", "write"}
alias = active
active = active & {"read"}     # rebinds active; alias retains original set
```

### 7.4 Set algebra as domain logic

```python
requested = {"read", "write", "delete"}
granted = {"read", "write", "audit"}

allowed = requested & granted              # intersection
denied = requested - granted               # difference
all_capabilities = requested | granted     # union
one_side_only = requested ^ granted        # symmetric difference

assert allowed == requested.intersection(granted)
assert denied == requested.difference(granted)
```

Operators generally require set-like operands; named methods accept any iterable in many implementations/usages:

```python
allowed = requested.intersection(["read", "audit"])
```

Use algebra to make intent visible. A manual nested loop for overlap is slower and obscures the domain relationship.

### 7.5 Subsets, supersets, and disjointness

```python
required = {"source", "external_id", "value"}
provided = {"source", "external_id", "value", "tags"}

assert required <= provided            # subset (allows equality)
assert required < provided             # proper subset
assert provided >= required            # superset
assert not required.isdisjoint(provided)

missing = required - provided
if missing:
    raise ValueError(f"missing fields: {sorted(missing)}")
```

`isdisjoint` can stop as soon as it finds an overlap and is clearer than building an intersection merely to convert it to `bool`.

### 7.6 Hashability and equality

Set elements must be hashable. Typical immutable scalar values, tuples of hashable elements, frozen dataclasses, and frozensets qualify. Lists, dictionaries, and mutable sets do not.

```python
hash("alpha")
hash(("alpha", 42))

# TypeError: unhashable type: 'list'
# {["alpha", 42]}
```

Why? If an element changed after insertion, its new hash might point to a different slot while the object remained stored in the old slot, corrupting membership semantics.

Custom equality and hashing must agree:

```python
from dataclasses import dataclass

@dataclass(frozen=True, slots=True)
class EventKey:
    source: str
    external_id: str

keys = {EventKey("alpha", "7"), EventKey("alpha", "7")}
assert len(keys) == 1
```

### 7.7 `frozenset`: an immutable set value

`frozenset` supports non-mutating set operations and is itself hashable when its elements are hashable. Use it as a dictionary key, set element, immutable configuration value, or cache key.

```python
role_permissions = {
    frozenset({"read"}): "reader",
    frozenset({"read", "write"}): "editor",
}

permission_set = frozenset({"write", "read"})
assert role_permissions[permission_set] == "editor"
```

Because equality ignores order, the two construction orders represent the same key.

### 7.8 Preserving order while deduplicating

For hashable values, dictionaries preserve first-seen order:

```python
items = ["b", "a", "b", "c", "a"]
stable_unique = list(dict.fromkeys(items))
assert stable_unique == ["b", "a", "c"]
```

For normalization or unhashable objects, track a hashable key explicitly:

```python
def unique_by(records, key):
    seen = set()
    for record in records:
        marker = key(record)
        if marker in seen:
            continue
        seen.add(marker)
        yield record

records = [
    {"source": "Alpha", "id": "1"},
    {"source": "alpha", "id": "1"},
    {"source": "beta", "id": "2"},
]
unique = list(unique_by(records, lambda r: (r["source"].casefold(), r["id"])))
```

This keeps the first record for each normalized key without trying to hash dictionaries.

### 7.9 Real-world patterns

#### Validation

```python
required = {"source", "external_id", "value"}
allowed = required | {"observed_at", "tags"}
received = set(payload)

if missing := required - received:
    raise ValueError(f"missing: {sorted(missing)}")
if unknown := received - allowed:
    raise ValueError(f"unknown: {sorted(unknown)}")
```

#### Reconciliation

```python
database_ids = {"1", "2", "3"}
remote_ids = {"2", "3", "4"}

to_create = remote_ids - database_ids
to_delete = database_ids - remote_ids
unchanged = remote_ids & database_ids
```

#### Graph traversal and cycle prevention

```python
def reachable(graph: dict[str, set[str]], start: str) -> set[str]:
    visited: set[str] = set()
    pending = [start]
    while pending:
        node = pending.pop()
        if node in visited:
            continue
        visited.add(node)
        pending.extend(graph.get(node, set()) - visited)
    return visited
```

#### Test assertions

```python
assert set(actual_ids) == {"1", "2"}  # only when order/count are irrelevant
```

Be careful: converting both sides to sets can hide duplicate bugs. If duplicates are forbidden, also assert lengths or use `Counter`.

### 7.10 Complexity and performance reasoning

| Operation | Average complexity | Notes |
|---|---:|---|
| `x in s` | O(1) | Hash and equality cost still matter. |
| `add`, `discard` | O(1) | Resizing occasionally costs O(n). |
| union/intersection/difference | proportional to involved set sizes | Implementation can choose the smaller operand for some operations. |
| iteration/copy | O(n) | Order is not a semantic contract. |

Sets use more memory than compact lists because hash tables keep spare capacity. For a tiny collection scanned once, a list may be simpler/faster. For repeated membership over many values, a set usually wins. Measure with realistic element hash/equality costs.

### 7.11 Common mistakes

- Writing `{}` for an empty set.
- Expecting stable ordering or using `pop` as “last”.
- Using `remove` when absence is normal.
- Losing duplicate counts by converting too early.
- Placing mutable/unhashable objects in a set.
- Mutating a field used in a custom object's hash/equality.
- Comparing lists through sets when multiplicity matters.
- Building a set merely to perform one tiny scan.

### Worked project — Permission and Data-Reconciliation Engine

Combine strings, lists, tuples, sets, dictionaries, conditionals, and loops from Chapters 2–10:

```python
from dataclasses import dataclass

@dataclass(frozen=True, slots=True)
class UserAccess:
    username: str
    roles: frozenset[str]

ROLE_PERMISSIONS: dict[str, frozenset[str]] = {
    "reader": frozenset({"events:read"}),
    "editor": frozenset({"events:read", "events:write"}),
    "admin": frozenset({"events:read", "events:write", "events:delete"}),
}

def effective_permissions(user: UserAccess) -> frozenset[str]:
    unknown = user.roles - ROLE_PERMISSIONS.keys()
    if unknown:
        raise ValueError(f"unknown roles: {sorted(unknown)}")
    permissions: set[str] = set()
    for role in user.roles:
        permissions.update(ROLE_PERMISSIONS[role])
    return frozenset(permissions)

def authorize(user: UserAccess, required: set[str]) -> tuple[bool, set[str]]:
    effective = effective_permissions(user)
    missing = required - effective
    return not missing, missing

alice = UserAccess("alice", frozenset({"reader", "editor"}))
allowed, missing = authorize(alice, {"events:read", "events:write"})
assert allowed and not missing
```

**Extension 1:** normalize role names without silently accepting blank values.
**Extension 2:** reconcile desired versus current users with create/delete/unchanged sets.
**Extension 3:** preserve input order in an audit report while deduplicating.
**Extension 4:** add tests proving duplicate permissions do not matter but duplicate input records are detected.
**Extension 5:** benchmark repeated list membership against precomputed-set membership.

### Self-check quiz

1. What does `{}` create? An empty dictionary; use `set()`.
2. `remove` versus `discard`? Both remove; only `remove` raises on absence.
3. Why can a tuple be unhashable? It may contain an unhashable element.
4. Which operation finds values in exactly one operand? Symmetric difference (`^`).
5. Why is set order unsuitable for an API? It is not the set abstraction's semantic contract.
6. When is `frozenset` required? When set semantics must be hashable/immutable, such as a mapping key.
7. Does set equality check insertion order? No; it checks members.

### Exercises

1. Write `stable_unique(iterable, key)` supporting unhashable records.
2. Validate required and allowed configuration keys and produce sorted error messages.
3. Implement a plagiarism-like Jaccard similarity: `len(a & b) / len(a | b)`, defining empty behavior.
4. Find users who have every required permission, no forbidden permission, and at least one audit permission.
5. Traverse a dependency graph and report reachable nodes plus detected cycles.
6. Use `Counter` to prove whether two lists have the same multiplicities; contrast with set equality.

### Chapter completion criteria

You can explain hash/equality invariants, choose list/set/Counter/frozenset, predict mutation/alias effects, use algebra for domain logic, preserve order when required, and complete the permission/reconciliation project with tests.

---

## Chapter 8 — Dictionaries

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 2–7

### Learning objectives

Model key-to-value relationships; create, inspect, update and delete entries; choose
strict lookup versus defaults; use views and ordering correctly; group/count/index
records; merge configurations with explicit precedence; understand hash/equality,
copying and complexity; and validate external mappings before using them as records.

### 8.0 Mental model: lookup by key

A dictionary maps each unique hashable key to one value. Use it when retrieving by
identity/name matters more than numeric position.

```python
capitals = {"Iran": "Tehran", "Japan": "Tokyo"}
assert capitals["Iran"] == "Tehran"
```

Keys are unique: assigning an equal key replaces its value without creating another
entry. Values may repeat and need not be hashable.

```python
settings = {"timeout": 5}
settings["timeout"] = 10
assert settings == {"timeout": 10}
```

Dictionaries preserve insertion order, but equality compares key/value content, not
order. Do not use dict order as sorted order unless you explicitly sort.

### 8.0.1 Construction forms

```python
empty = {}
also_empty = dict()
from_pairs = dict([("a", 1), ("b", 2)])
from_keywords = dict(timeout=5, retries=2)
from_keys = dict.fromkeys(["read", "write"], False)
assert from_pairs == {"a": 1, "b": 2}
```

Avoid a mutable shared `fromkeys` default:

```python
bad = dict.fromkeys(["a", "b"], [])
bad["a"].append(1)
assert bad["b"] == [1]

good = {key: [] for key in ["a", "b"]}
good["a"].append(1)
assert good["b"] == []
```

Dictionary comprehensions transform/filter pairs:

```python
squares = {number: number * number for number in range(4)}
assert squares == {0: 0, 1: 1, 2: 4, 3: 9}
```

### 8.0.2 Strict lookup, expected absence, and insertion

Use `mapping[key]` when absence violates a requirement; it raises `KeyError` with the
missing key. Use `get` when absence is expected and a non-inserting default is clear.

```python
record = {"id": "e1", "count": 0}
assert record["id"] == "e1"
assert record.get("count") == 0
assert record.get("status", "unknown") == "unknown"
assert "status" not in record             # get did not insert
```

Never use `if mapping.get(key)` to test presence when falsy values are valid. Use
`key in mapping`.

`setdefault` returns an existing value or inserts the supplied default. Its default
expression is evaluated before the call; use `defaultdict` for systematic grouping.

```python
groups: dict[str, list[int]] = {}
groups.setdefault("alpha", []).append(1)
assert groups == {"alpha": [1]}
```

### 8.0.3 Updating and deleting

```python
record["status"] = "new"
record.update({"status": "ready", "priority": 2})
removed = record.pop("priority")
missing = record.pop("missing", None)
last_key, last_value = record.popitem()
record.clear()
```

`popitem` removes the most recently inserted entry. `del mapping[key]` is strict;
`pop(key, default)` supports expected absence. Do not catch a broad exception to hide
unexpected missing keys.

### 8.0.4 Views and iteration

`keys`, `values` and `items` return dynamic views backed by the dictionary.

```python
scores = {"Ada": 98, "Linus": 91}
names = scores.keys()
scores["Grace"] = 99
assert "Grace" in names

for name, score in scores.items():
    print(name, score)
```

Changing dictionary size during iteration raises or behaves incorrectly. Iterate a
snapshot when deletion is intentional, or build a new dictionary:

```python
passing = {name: score for name, score in scores.items() if score >= 95}
```

### 8.0.5 Hashability and key design

Keys obey the set hash/equality contract. Typical keys are strings, integers, enums,
immutable tuples and frozen domain values. Equal numeric keys collide:

```python
collision = {1: "integer", True: "boolean"}
assert len(collision) == 1
assert collision[1] == "boolean"
```

Normalize external identifiers once before using them as keys. Never mutate data
that participates in a custom key's hash/equality.

### 8.0.6 Grouping, counting, and indexing

```python
from collections import Counter, defaultdict

events = [
    {"id": "e1", "source": "a", "status": "ok"},
    {"id": "e2", "source": "a", "status": "bad"},
    {"id": "e3", "source": "b", "status": "ok"},
]

by_id = {event["id"]: event for event in events}
by_source: defaultdict[str, list[str]] = defaultdict(list)
for event in events:
    by_source[event["source"]].append(event["id"])
statuses = Counter(event["status"] for event in events)
assert statuses == {"ok": 2, "bad": 1}
```

A comprehension silently overwrites duplicate IDs. Production indexing must detect
duplicates before assignment when uniqueness is required.

### 8.0.7 Merge, copy, and ownership

`left | right` creates a shallow merged dict with right-hand precedence; `update`
mutates. Nested mappings are replaced, not recursively merged.

```python
defaults = {"port": 8000, "features": {"audit": False}}
override = {"port": 9000, "features": {"metrics": True}}
effective = defaults | override
assert effective["features"] == {"metrics": True}
```

A recursive merge needs explicit rules for conflicting types, lists and deletion.
`.copy()` is shallow; nested values remain shared just like lists.

### 8.0.8 Complexity and choosing a representation

Lookup, insertion and deletion are average O(1); iteration/copy are O(n). Worst-case
hash behavior and expensive equality still matter. A dict is suitable for dynamic
JSON-like data and indexes. Prefer dataclass/TypedDict/validation models for stable
internal schemas; annotations alone do not validate runtime input.

### 8.0.9 Boundary validation example

```python
def parse_event(payload: dict[str, object]) -> dict[str, object]:
    required = {"id", "source", "value"}
    allowed = required | {"tags"}
    missing = required - payload.keys()
    extra = payload.keys() - allowed
    if missing:
        raise ValueError(f"missing keys: {sorted(missing)}")
    if extra:
        raise ValueError(f"unknown keys: {sorted(extra)}")
    event_id = str(payload["id"]).strip()
    source = str(payload["source"]).strip().casefold()
    if not event_id or not source:
        raise ValueError("id/source cannot be blank")
    if isinstance(payload["value"], bool) or not isinstance(payload["value"], (int, float)):
        raise TypeError("value must be numeric")
    return {**payload, "id": event_id, "source": source}
```

Dictionaries map unique, hashable keys to values. They are the right tool when a program retrieves or updates a value by identity or name rather than numeric position. Dictionaries preserve insertion order, but equality compares key/value content, not order.

### Creating, reading, and updating

```python
record = {"id": 7, "source": "alpha", "tags": ["new"]}
record["value"] = 3.14
source = record.get("source", "unknown")

empty: dict[str, int] = {}
from_pairs = dict([("accepted", 4), ("rejected", 1)])
defaults = dict(timeout=5, retries=2)

for key, value in record.items():
    print(key, value)
```

Indexing a missing key raises `KeyError`; use it when absence means broken data. `get` returns a default and suits expected absence. Do not use `if mapping.get(key)` to test presence because valid values may be `0`, `False`, `None`, or empty.

```python
settings = {"retries": 0}
assert "retries" in settings
assert settings.get("retries") == 0
assert settings.get("timeout", 30) == 30  # does not insert timeout

removed = settings.pop("retries")
missing = settings.pop("missing", None)
```

`setdefault` inserts only when absent, but its default expression is evaluated eagerly. `defaultdict` is clearer for systematic grouping; `Counter` expresses frequency counting directly.

```python
from collections import Counter, defaultdict

groups: defaultdict[str, list[int]] = defaultdict(list)
groups["alpha"].append(7)
counts = Counter(["ok", "ok", "bad"])
```

### Merge precedence and shallow behavior

`a | b` creates a new dictionary with right-hand values winning; `a.update(b)` mutates `a`. Configuration layers must document precedence.

```python
defaults = {"host": "127.0.0.1", "port": 8000, "debug": False}
file_config = {"port": 9000}
cli_config = {"debug": True}
effective = defaults | file_config | cli_config
```

This merge is shallow: a nested mapping is replaced, not recursively merged. “Deep merge” needs an explicit policy for lists, deletion, and conflicting types.

### Views, iteration, and keys

`keys()`, `values()`, and `items()` are live views backed by the dictionary. They reflect later changes. Never change dictionary size during iteration; build a filtered dictionary or iterate over `list(mapping)` when deletion is intentional.

```python
scores = {"Ada": 98, "Linus": 91}
names = scores.keys()
scores["Grace"] = 99
assert "Grace" in names

excellent = {name: score for name, score in scores.items() if score >= 95}
```

Keys use the same hash/equality contract as set elements. Strings, numbers, immutable tuples, enums, and frozen domain objects are typical keys. Equal numeric values collide: `{1: "int", True: "bool"}` has one entry because `1 == True` and their hashes agree.

### Record, index, or typed model?

A dictionary works well for dynamic JSON-like data and lookup indexes. For a stable internal schema, use a dataclass, `TypedDict`, or validation model. `TypedDict` helps static tools but performs no runtime validation.

```python
from typing import TypedDict

class EventPayload(TypedDict):
    id: str
    source: str
    value: float

event: EventPayload = {"id": "e-1", "source": "sensor", "value": 2.5}
by_id: dict[str, EventPayload] = {event["id"]: event}
```

### Common mistakes

- Confusing a missing key with a present falsy value.
- Using `get` where malformed input should fail loudly.
- Sharing nested mutable values after a shallow copy or merge.
- Silently overwriting duplicate keys while building an index.
- Mutating dictionary size during iteration.
- Treating `TypedDict` annotations as runtime checks.

### Worked project — Validation and aggregation engine

```python
from collections import Counter, defaultdict
from collections.abc import Iterable

def summarize_events(events: Iterable[dict[str, object]]) -> dict[str, object]:
    required = {"id", "source", "status"}
    by_id: dict[str, dict[str, object]] = {}
    by_source: defaultdict[str, list[str]] = defaultdict(list)
    statuses: Counter[str] = Counter()

    for position, event in enumerate(events, start=1):
        if missing := required - event.keys():
            raise ValueError(f"event {position}: missing {sorted(missing)}")
        event_id = str(event["id"])
        if event_id in by_id:
            raise ValueError(f"duplicate id: {event_id}")
        source, status = str(event["source"]), str(event["status"])
        by_id[event_id] = event.copy()
        by_source[source].append(event_id)
        statuses[status] += 1

    return {"by_id": by_id, "by_source": dict(by_source),
            "statuses": dict(statuses)}
```

This uses a keys view for validation, a dictionary for uniqueness, `defaultdict` for grouping, and `Counter` for frequency. Duplicate IDs fail instead of being silently overwritten.

### Exercises

1. Add allowed-key validation with event/line context.
2. Invert a mapping with non-unique values into `value -> list[key]`.
3. Write and test an explicit recursive-merge policy.
4. Extend the project with per-source status counts and stable sorting.
5. Compare a dictionary index with repeated list scans on realistic data.

---

## Chapter 9 — Conditionals

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 2–8

### Learning objectives

Use `if`/`elif`/`else`, truthiness, comparison chains, membership and guard clauses;
distinguish missing from falsy values; structure mutually exclusive rules; apply
conditional expressions and structural pattern matching; reason about reachability;
and test every decision boundary.

### 9.0 Decisions and predicates

A conditional selects a suite based on the truth value of an expression. A predicate
is an expression/function used as a yes/no question.

```python
temperature = 28

if temperature > 25:
    print("warm")
```

The condition is evaluated once. If truthy, its indented suite executes. Execution
then continues after the entire conditional.

### 9.0.1 `if`, `elif`, and `else`

```python
score = 82

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "D"

assert grade == "B"
```

Branches are checked top to bottom and only the first truthy branch executes. Order
from most specific/restrictive to broader rules when ranges overlap. Here, checking
`score >= 70` first would make higher branches unreachable.

Separate `if` statements are not mutually exclusive:

```python
flags: list[str] = []
value = 12
if value > 0:
    flags.append("positive")
if value % 2 == 0:
    flags.append("even")
assert flags == ["positive", "even"]
```

Use independent `if`s when several facts can simultaneously hold; use an
`if`/`elif` chain for one classification.

### 9.0.2 Truthiness and explicit domain questions

Falsy built-ins include `None`, `False`, numeric zero, and empty strings/collections.

```python
for value in [None, False, 0, 0.0, "", [], {}, set()]:
    assert not value
```

Truthiness is convenient for “nonempty” but dangerous when states differ:

```python
def classify(value: object) -> str:
    if value is None:
        return "missing"
    if value == "":
        return "empty text"
    if value is False:
        return "explicit false"
    if value == 0:
        return "zero"
    return "other"
```

Note `False == 0`; identity checks before equality preserve the intended distinction.
Prefer the exact domain predicate over a vague truthiness shortcut.

### 9.0.3 Combining conditions

Use `and`, `or`, `not`, chained comparisons and membership. Parenthesize mixed logic
to communicate intent.

```python
age = 25
country = "IR"
has_ticket = True

eligible = 18 <= age < 65 and country in {"IR", "TR"} and has_ticket
assert eligible
```

Short-circuiting prevents dependent operations:

```python
name: str | None = None
if name is not None and name.strip():
    normalized = name.strip().casefold()
```

Avoid double negatives and long Boolean expressions. Extract named predicates:

```python
is_working_age = 18 <= age < 65
is_supported_country = country in {"IR", "TR"}
eligible = is_working_age and is_supported_country and has_ticket
```

### 9.0.4 Guard clauses

Guard clauses reject invalid/special cases early and leave the successful path flat.

```python
def shipping_cost(weight: float, *, premium: bool) -> float:
    if isinstance(weight, bool) or not isinstance(weight, (int, float)):
        raise TypeError("weight must be numeric")
    if weight <= 0:
        raise ValueError("weight must be positive")
    if premium:
        return 0.0
    if weight <= 1:
        return 5.0
    return 5.0 + (weight - 1) * 2.0
```

This structure makes validation, premium behavior and normal pricing individually
testable. Do not turn every line into a guard; group coherent rules.

### 9.0.5 Nested conditionals and decision tables

Deep nesting multiplies mental state. Flatten with guards, extracted predicates or a
decision table. For closed exact combinations, a mapping can be clearer:

```python
transition = {
    ("pending", "approve"): "approved",
    ("pending", "reject"): "rejected",
    ("approved", "archive"): "archived",
}

def next_status(current: str, action: str) -> str:
    try:
        return transition[current, action]
    except KeyError as exc:
        raise ValueError(f"invalid transition: {current} + {action}") from exc
```

Mappings suit exact lookup; conditionals suit ranges and predicates. Make invalid
combinations explicit rather than silently preserving state.

### 9.0.6 Conditional expressions

```python
label = "empty" if count == 0 else "available"
```

Use for one small value choice. Nested conditional expressions are hard to read and
should become statements or a function.

### 9.0.7 Structural pattern matching

`match` compares a subject against patterns top to bottom. Patterns can check literal
values and structure while binding parts.

```python
def handle(message: object) -> str:
    match message:
        case {"type": "ping"}:
            return "pong"
        case {"type": "event", "payload": {"id": str(event_id)}} if event_id:
            return f"event:{event_id}"
        case {"type": unknown}:
            raise ValueError(f"unsupported message type: {unknown!r}")
        case _:
            raise ValueError("malformed message")
```

Mapping patterns ignore extra keys unless explicitly constrained elsewhere. Pattern
matching is not full schema validation: check lengths, ranges, allowed keys and
cross-field rules. Bare names capture rather than compare; use literals, qualified
constants or guards deliberately.

### 9.0.8 Reachability and completeness

An earlier broad condition can make later code unreachable. For finite states, aim
for exhaustive handling and fail loudly on unexpected states.

```python
def status_color(status: str) -> str:
    match status:
        case "ok":
            return "green"
        case "warning":
            return "yellow"
        case "error":
            return "red"
        case _:
            raise ValueError(f"unknown status: {status!r}")
```

### 9.0.9 Boundary testing

For every inequality, test immediately below, at, and above its boundary. For every
branch, provide at least one test. Also test wrong type, missing, empty and unexpected
state when accepted inputs cross a runtime boundary.

```python
assert shipping_cost(1, premium=False) == 5.0
assert shipping_cost(1.5, premium=False) == 6.0
assert shipping_cost(10, premium=True) == 0.0
```

### Common mistakes

- Ordering broad `elif` conditions before specific ones.
- Using independent `if`s when exactly one branch must run, or vice versa.
- Collapsing `None`, zero, false and empty values through truthiness.
- Writing long double-negative Boolean expressions.
- Nesting deeply instead of using guards/named predicates.
- Believing `match` automatically validates types and extra keys.
- Forgetting a bare pattern name captures.
- Testing only the middle of ranges instead of boundaries.

Conditionals choose a path based on truth value. Falsy values include `False`, `None`, numeric zero, and empty containers/strings.

```python
if value is None:
    state = "missing"
elif value < 0:
    state = "invalid"
else:
    state = "accepted"
```

Guard clauses keep the successful path flat:

```python
def normalize_count(value: object) -> int:
    if isinstance(value, bool):
        raise TypeError("boolean is not a count")
    if not isinstance(value, int):
        raise TypeError("count must be int")
    if value < 0:
        raise ValueError("count cannot be negative")
    return value
```

`bool` subclasses `int`, hence the explicit rejection. Structural pattern matching checks shapes and may bind names:

```python
match message:
    case {"type": "event", "payload": payload}:
        process(payload)
    case {"type": unknown}:
        raise ValueError(f"unsupported type: {unknown}")
    case _:
        raise ValueError("malformed message")
```

Matching is not automatic validation; verify bound value types/constraints.

### Exercises and project

Classify records with guard clauses and match three message shapes. Write tests for missing, empty, zero, false, negative, and valid values.

1. Rewrite a deeply nested eligibility function using guard clauses and named predicates.
2. Build a truth table for three Boolean conditions and identify redundant branches.
3. Test grade classification immediately below/at/above every threshold.
4. Implement a finite workflow with a transition mapping and explicit invalid transitions.
5. Match ping/event/error message shapes; reject wrong field types and unknown keys.
6. Extend Atlas validation so missing, blank, false, zero and negative values receive
   distinct documented outcomes rather than one generic falsy branch.

### Worked project — record decision engine

```python
def decide_record(record: dict[str, object]) -> str:
    if "id" not in record:
        return "reject:missing-id"
    event_id = record["id"]
    if not isinstance(event_id, str):
        return "reject:id-type"
    if not event_id.strip():
        return "reject:blank-id"
    if "value" not in record:
        return "reject:missing-value"
    value = record["value"]
    if isinstance(value, bool) or not isinstance(value, (int, float)):
        return "reject:value-type"
    if value < 0:
        return "reject:negative-value"
    return "accept"
```

### Chapter completion criteria

Explain truthiness without losing domain states; select independent versus exclusive
branches; flatten nested validation; order overlapping ranges; use match with guards
and explicit fallbacks; and prove every decision boundary with tests.

---

## Chapter 10 — Loops

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 2–9

### Learning objectives

Explain iterable/iterator traversal; choose `for` versus `while`; use `break`,
`continue` and loop `else`; traverse mappings and nested data; prove termination;
avoid mutation and exhausted-iterator bugs; implement bounded search, pagination,
retry, batching and graph traversal; and state time/space complexity.

### 10.0 Repetition as state change

A loop repeatedly executes a suite. Every useful loop needs a changing state or a
finite iterable, a termination argument, and observable work. Ask what changes each
iteration and why the loop must eventually stop.

```python
total = 0
for value in [10, 20, 30]:
    total += value
assert total == 60
```

### 10.0.1 Iterable versus iterator

An iterable can produce an iterator. An iterator yields values one at a time and
remembers its position until it raises `StopIteration`.

```python
values = [10, 20]
iterator = iter(values)
assert next(iterator) == 10
assert next(iterator) == 20
try:
    next(iterator)
except StopIteration:
    pass
```

A `for` loop obtains an iterator and repeatedly calls its protocol automatically.
Containers usually produce fresh iterators; a generator is commonly its own
one-pass iterator.

### 10.0.2 Choosing `for` or `while`

Use `for` when consuming an iterable. Use `while` when repetition depends on evolving
state such as attempts, queues, sentinels or deadlines.

```python
attempt = 0
maximum_attempts = 3
while attempt < maximum_attempts:
    attempt += 1
    print(f"attempt {attempt}")
```

Do not translate every `for` into manual indexing. Direct iteration is clearer and
works with generators and non-sequence iterables.

### 10.0.3 `break`, `continue`, and `else`

`continue` skips to the next iteration; `break` exits the nearest loop. Loop `else`
runs only when iteration ends without `break`.

```python
def find_even(values: list[int]) -> int | None:
    for value in values:
        if value % 2 != 0:
            continue
        return value
    return None
```

Return is often clearer than loop `else` inside a function. Loop `else` is valuable
when “searched completely without finding” is the intended meaning.

### 10.0.4 Iterating dictionaries and multiple streams

```python
scores = {"Ada": 98, "Grace": 99}
for name, score in scores.items():
    print(name, score)

names = ["a", "b"]
values = [1, 2]
for position, (name, value) in enumerate(zip(names, values, strict=True), 1):
    assert position >= 1
```

Dictionary iteration yields keys. Use `.items()` for key/value pairs. Strict zip
detects length mismatch instead of silently truncating.

### 10.0.5 Nested loops and complexity

```python
pairs = []
for left in [1, 2]:
    for right in ["a", "b"]:
        pairs.append((left, right))
assert pairs == [(1, "a"), (1, "b"), (2, "a"), (2, "b")]
```

Nested loops are not automatically wrong, but a full n-by-m scan is O(nm). Repeated
lookup joins should often build a dictionary/set index first:

```python
users = [{"id": "u1", "name": "Ada"}, {"id": "u2", "name": "Grace"}]
orders = [{"user_id": "u2", "amount": 10}]
user_by_id = {user["id"]: user for user in users}
for order in orders:
    order["user_name"] = user_by_id[order["user_id"]]["name"]
```

### 10.0.6 Safe mutation

Changing collection size during iteration can skip values or raise. Build a result,
iterate a snapshot, or drain a data structure with a documented pattern.

```python
numbers = [1, -1, 2, -2]
numbers[:] = [number for number in numbers if number >= 0]
assert numbers == [1, 2]
```

For a queue, `while queue:` plus `popleft()` is intentional state-controlled
mutation; use deque for efficient front removal.

### 10.0.7 Sentinel loops and input streams

```python
from collections.abc import Iterable

def lines_until_stop(lines: Iterable[str]) -> list[str]:
    result: list[str] = []
    for line in lines:
        cleaned = line.rstrip("\n")
        if cleaned == "STOP":
            break
        result.append(cleaned)
    return result
```

Distinguish an empty valid value from the end-of-stream sentinel. File `readline`
returns `""` at EOF; a blank line is `"\n"`.

### 10.0.8 Termination proofs and limits

For each state-driven loop identify a variant moving toward termination: attempts
increase to a fixed bound, a queue shrinks, a cursor becomes absent, or a monotonic
deadline expires. External systems can repeat/cycle, so combine semantic completion
with hard resource limits.

### 10.0.9 Bounded retry sketch

```python
from collections.abc import Callable

def retry(
    operation: Callable[[], str],
    *,
    attempts: int = 3,
    retryable: tuple[type[Exception], ...] = (TimeoutError,),
) -> str:
    if attempts < 1:
        raise ValueError("attempts must be positive")
    for attempt in range(1, attempts + 1):
        try:
            return operation()
        except retryable:
            if attempt == attempts:
                raise
    raise AssertionError("unreachable")
```

Production retries additionally need an end-to-end monotonic deadline, backoff with
jitter, idempotency analysis, cancellation and metrics. Never retry every exception.

### 10.0.10 Iterative graph traversal

```python
def reachable(graph: dict[str, list[str]], start: str) -> set[str]:
    seen: set[str] = set()
    stack = [start]
    while stack:
        node = stack.pop()
        if node in seen:
            continue
        seen.add(node)
        stack.extend(reversed(graph.get(node, [])))
    return seen


graph = {"a": ["b", "c"], "b": ["c"], "c": ["a"]}
assert reachable(graph, "a") == {"a", "b", "c"}
```

The visited set both prevents infinite cycles and avoids repeated work.

`for` consumes values from an iterable until exhaustion. `while` repeats while a condition stays truthy. Choose `for` for traversal and `while` for state-controlled repetition such as queues or bounded polling.

### Direct iteration and control flow

Iterate over values instead of indexes unless position is meaningful. `continue` skips the current item; `break` exits the nearest loop.

```python
for index, record in enumerate(records, start=1):
    if not record.get("valid"):
        continue
    process(record)
else:
    print("completed without break")
```

Loop `else` runs only when no `break` occurred, making search failure explicit:

```python
for event in events:
    if event["id"] == target_id:
        found = event
        break
else:
    raise LookupError(f"event not found: {target_id}")
```

### `range`, `enumerate`, and `zip`

`range` produces integers lazily and excludes its stop. `enumerate` adds a counter while preserving direct iteration. `zip` combines positions; ordinary `zip` silently stops at the shortest input, while `strict=True` detects unequal lengths.

```python
for name, value in zip(names, values, strict=True):
    print(name, value)
```

Nested scans can cost O(n×m). For repeated membership or joins, first build a set/dictionary index:

```python
known_ids = {record["id"] for record in database_records}
new_records = [record for record in incoming if record["id"] not in known_ids]
```

### Termination and safe pagination

Every state-driven loop needs a termination argument: a counter reaches a bound, a queue shrinks, a deadline expires, or a next-page token disappears. External progress requires safety limits.

```python
from collections.abc import Callable
from typing import Any

Page = tuple[list[dict[str, Any]], str | None]

def fetch_all(
    fetch_page: Callable[[str | None], Page], *, max_pages: int = 100
) -> list[dict[str, Any]]:
    results: list[dict[str, Any]] = []
    cursor: str | None = None
    seen: set[str] = set()

    for page_number in range(1, max_pages + 1):
        items, next_cursor = fetch_page(cursor)
        results.extend(items)
        if next_cursor is None:
            return results
        if next_cursor in seen:
            raise RuntimeError(f"pagination cycle at page {page_number}")
        seen.add(next_cursor)
        cursor = next_cursor
    raise RuntimeError(f"pagination exceeded {max_pages} pages")
```

This design proves a hard upper bound and detects a server that repeats tokens. Retry loops should similarly combine attempt limits, monotonic deadlines, backoff, and testable injected sleeping.

### One-pass iterators

Iterators remember their position and cannot normally rewind. Containers can create fresh iterators; a generator is itself one-pass.

```python
numbers = iter([1, 2, 3])
assert sum(numbers) == 6
assert sum(numbers) == 0
```

Materializing with `list` enables replay but may be unsafe for huge or infinite streams. Decide who owns buffering and whether replay is a requirement.

### Common mistakes

- Structurally mutating a collection while iterating over it.
- Using `range(len(items))` when only values are needed.
- Writing unbounded retry/pagination loops or busy polling.
- Forgetting `break` exits only the innermost loop.
- Silently truncating paired inputs with ordinary `zip`.
- Reusing an exhausted iterator.

### Worked project — Bounded batch processor

```python
from collections.abc import Callable, Iterable
from dataclasses import dataclass

@dataclass(frozen=True)
class BatchResult:
    accepted: tuple[str, ...]
    rejected: tuple[tuple[int, str], ...]
    stopped_early: bool

def process_batch(
    records: Iterable[dict[str, object]],
    validate: Callable[[dict[str, object]], str],
    *, error_budget: int = 3,
) -> BatchResult:
    if error_budget < 0:
        raise ValueError("error_budget must be non-negative")
    accepted: list[str] = []
    rejected: list[tuple[int, str]] = []

    for line, record in enumerate(records, start=1):
        try:
            accepted.append(validate(record))
        except ValueError as exc:
            rejected.append((line, str(exc)))
            if len(rejected) > error_budget:
                break
    else:
        return BatchResult(tuple(accepted), tuple(rejected), False)
    return BatchResult(tuple(accepted), tuple(rejected), True)
```

The exception boundary is narrow, line context survives, output is immutable, and early stopping is testable.

### Exercises

1. Test empty, exactly-at-budget, over-budget, and generator inputs.
2. Add duplicate-ID detection without changing accepted order.
3. Traverse a graph iteratively using a stack and visited set.
4. Implement bounded exponential retry with an injected sleeper.
5. Compare a nested-loop join with a dictionary-indexed join.

---
## Chapter 11 — Functions

Functions package a contract: accepted inputs, returned value, side effects, errors, and performance. Keep domain logic pure where practical and isolate I/O at boundaries.

### Learning objectives

After this chapter you should be able to define and call a function, distinguish a
parameter from an argument, predict `return` and `None`, use every parameter kind,
explain argument mutation, write a useful docstring and annotation, pass functions
as values, and test a function at its boundaries.

### 11.1 Defining, calling, and returning

`def` executes a function definition and binds its name to a function object. The
body does not run until a call expression uses parentheses.

```python
def greet(name):                         # name is a parameter
    message = f"Hello, {name}!"
    return message


result = greet("Ada")                    # "Ada" is an argument
print(result)
```

```console
Hello, Ada!
```

Execution enters with a new local scope. `return expression` immediately ends the
call and gives one object to the caller. Falling off the end, using bare `return`,
or writing `return None` all return the singleton `None`.

```python
def show_total(a: int, b: int) -> None:
    print(a + b)


returned = show_total(2, 3)              # prints 5
assert returned is None
```

Printing and returning are different. Printing is an output side effect; a return
value can be stored, tested, transformed, or ignored. Prefer computation that
returns data and let an outer CLI/UI layer print it.

Python returns exactly one object. Commas construct a tuple, which callers may
unpack:

```python
def minimum_maximum(values: list[int]) -> tuple[int, int]:
    if not values:
        raise ValueError("values cannot be empty")
    return min(values), max(values)


low, high = minimum_maximum([8, 2, 5])
assert (low, high) == (2, 8)
```

Code after an unconditional `return` is unreachable. A function may have several
guard-clause returns, but every path should have an intentional result type.

### 11.2 Arguments and all parameter kinds

Ordinary parameters accept positional or keyword arguments. Keywords improve
readability and are independent of call-site order:

```python
def rectangle_area(width: float, height: float = 1.0) -> float:
    if width < 0 or height < 0:
        raise ValueError("dimensions cannot be negative")
    return width * height


assert rectangle_area(4, 3) == 12
assert rectangle_area(width=4, height=3) == 12
assert rectangle_area(4) == 4
```

Required parameters must precede defaulted parameters within the same parameter
group. Defaults are evaluated once, when the `def` statement runs—not for every
call. This is why a mutable default accidentally shares state:

```python
def broken_append(value, bucket=[]):     # do not copy this API
    bucket.append(value)
    return bucket


assert broken_append(1) == [1]
assert broken_append(2) == [1, 2]        # same list survived
```

Use a sentinel such as `None` and create the value inside:

```python
def append_value(value: int, bucket: list[int] | None = None) -> list[int]:
    result = [] if bucket is None else bucket.copy()
    result.append(value)
    return result
```

The complete parameter order is positional-only, positional-or-keyword, variadic
positional, keyword-only, and variadic keyword:

```python
def request(
    method: str,                         # positional-only
    /,
    url: str,                            # positional or keyword
    *segments: str,                      # extra positional arguments -> tuple
    timeout: float = 5.0,                # keyword-only
    **headers: str,                      # extra keywords -> dict
) -> tuple[str, str, tuple[str, ...], float, dict[str, str]]:
    return method, url, segments, timeout, headers


parts = request(
    "GET", "/events", "today", timeout=2.0, Accept="application/json"
)
assert parts[2] == ("today",)
assert parts[4] == {"Accept": "application/json"}
```

Use `/` when a parameter name is an implementation detail. Use `*` to force
important options to be named. Use `*args`/`**kwargs` only for genuinely variadic or
forwarding APIs; they otherwise hide spelling errors and weaken documentation.

Sequences and mappings can be unpacked into a call:

```python
dimensions = (4.0, 3.0)
assert rectangle_area(*dimensions) == 12.0

options = {"width": 4.0, "height": 3.0}
assert rectangle_area(**options) == 12.0
```

Duplicate values, missing required arguments, unexpected keywords, and too many
positional arguments raise `TypeError` before the body runs.

### 11.3 What is passed to a function?

Python binds local parameter names to the same argument objects supplied by the
caller. It is neither pass-by-copy nor C-style pass-by-reference. Rebinding the
local name is invisible; mutating a shared mutable object is visible.

```python
def update(values: list[int]) -> None:
    values.append(3)                     # mutation is visible
    values = [99]                        # local rebinding is not


numbers = [1, 2]
update(numbers)
assert numbers == [1, 2, 3]
```

Document whether a function mutates an argument. For public APIs, returning a new
value is often easier to reason about; in-place mutation may be appropriate for
large buffers or explicitly stateful objects.

### 11.4 Annotations and docstrings

Annotations describe intended types to readers and static checkers; Python does not
normally enforce them at runtime.

```python
def fahrenheit(celsius: float) -> float:
    """Convert a Celsius temperature to Fahrenheit.

    The input and result are ordinary finite temperature measurements. This
    function performs no I/O and does not mutate caller-owned state.
    """
    return celsius * 9 / 5 + 32
```

`fahrenheit("hot")` is still attempted at runtime and fails only when its operations
reject the string. Validate external data at boundaries; use annotations to keep the
validated interior coherent. A useful docstring adds units, mutation, ordering,
errors, or complexity rather than repeating the function name.

### Signature design and contracts

A strong function has one coherent responsibility, names domain concepts, validates at the appropriate boundary, and makes optional behavior explicit. Type hints describe intended static types; docstrings should add semantics not expressible in annotations: units, mutation, errors, ordering, and complexity.

```python
def summarize(
    values: list[float],
    /,
    *,
    ignore_nonfinite: bool = True,
) -> tuple[int, float]:
    """Return accepted count and arithmetic mean."""
    import math
    selected = [x for x in values if math.isfinite(x) or not ignore_nonfinite]
    if not selected:
        raise ValueError("no usable values")
    return len(selected), sum(selected) / len(selected)
```

`/` marks positional-only parameters; `*` marks following parameters keyword-only. Defaults are evaluated once when `def` executes, so never use a mutable default:

```python
def add_tag(tag: str, tags: list[str] | None = None) -> list[str]:
    result = [] if tags is None else tags.copy()
    result.append(tag)
    return result
```

`*args` collects positional arguments; `**kwargs` collects keyword arguments. Use them when forwarding or representing a genuinely open interface, not to hide an unclear API. Python passes object references by assignment: mutating an argument's object is visible; rebinding the local parameter is not.

```python
def mutate(values: list[int]) -> None:
    values.append(3)       # caller observes mutation

def rebind(values: list[int]) -> None:
    values = [3]           # caller's reference is unchanged
```

Return a value rather than mixing computation and printing. A pure function with the same output for the same input is easier to test, cache, parallelize, and reason about. I/O functions remain necessary; keep the boundary visible.

### Scope, closures, and callable values

Name lookup follows local, enclosing, global, then built-in scopes. Assignment makes a name local unless declared `nonlocal` or `global`; this explains many `UnboundLocalError` cases.

Closures retain referenced enclosing state. `nonlocal` rebinds an enclosing name; prefer an explicit object when state grows complex. Functions are objects and can be stored, passed, decorated, and returned.

```python
from collections.abc import Callable

def make_threshold(minimum: float) -> Callable[[float], bool]:
    def accepts(value: float) -> bool:
        return value >= minimum
    return accepts

accept_production = make_threshold(0.95)
```

Functions are ordinary objects:

```python
def double(value: int) -> int:
    return value * 2


operation = double
assert operation(4) == 8

operations = [str.strip, str.casefold]
text = "  Atlas  "
for operation in operations:
    text = operation(text)
assert text == "atlas"
```

A lambda is a small anonymous expression function. It cannot contain statements and
should stay short; give nontrivial behavior a descriptive `def` name.

```python
records = [{"id": "b", "score": 2}, {"id": "a", "score": 2}]
records.sort(key=lambda record: (record["score"], record["id"]))
```

Closures capture names, not frozen snapshots. When creating callbacks in a loop, bind the current value with a default or helper:

```python
callbacks = [lambda value=i: value for i in range(3)]
assert [callback() for callback in callbacks] == [0, 1, 2]
```

### Recursion and API evolution

Recursion suits recursively structured data, but Python has a recursion limit and no tail-call optimization. Prefer iteration for deep/untrusted structures. Keyword-only parameters make call sites clear and allow safer API evolution; positional-only parameters can hide irrelevant parameter names in low-level APIs.

### Worked example — dependency injection without a framework

```python
from collections.abc import Callable
from datetime import datetime

def create_record(source: str, *, now: Callable[[], datetime],
                  save: Callable[[dict[str, object]], None]) -> dict[str, object]:
    normalized = source.strip().casefold()
    if not normalized:
        raise ValueError("source cannot be blank")
    record = {"source": normalized, "created_at": now()}
    save(record)
    return record
```

Injecting clock and persistence keeps tests deterministic and makes side effects explicit.

### 11.5 Testing a function as a contract

Test normal, boundary, and invalid inputs and verify side effects explicitly:

```python
def test_rectangle_area() -> None:
    assert rectangle_area(4, 3) == 12
    assert rectangle_area(0, 3) == 0      # boundary
    try:
        rectangle_area(-1, 3)
    except ValueError as exc:
        assert "negative" in str(exc)
    else:
        raise AssertionError("negative width was accepted")
```

Tests should not inspect local variables. They should observe return values, expected
exceptions, and documented mutations/I/O. Later pytest chapters express the same
contract more concisely.

### Exercises and project

1. **Foundation:** write `is_even`, `absolute`, and `clamp` functions; test zero,
   negative values, and both clamp boundaries.
2. **Foundation:** predict the result of calls mixing positional/default/keyword
   arguments, then run them; include three calls that intentionally raise TypeError.
3. **Foundation:** demonstrate print versus return and mutation versus rebinding in
   four minimal functions.
4. **Application:** extract Atlas validation, normalization, summarization, and
   formatting into typed functions. Document units, errors, mutation, and ordering.
5. **Application:** accept an injected clock and saver; test with a fixed clock and a
   list's `append` method without touching disk or wall-clock time.
6. **Challenge:** design a backward-compatible signature change using a new
   keyword-only option. Explain why changing an existing positional parameter would
   be risky.

Completion criterion: from a blank file, implement and test a function using every
parameter kind, explain every binding created during one call, and diagnose a
mutable-default failure without consulting this chapter.

---

## Chapter 12 — Modules

A module is normally one `.py` file loaded once per interpreter and cached in `sys.modules`. A package groups modules under an import namespace. Imports execute top-level module code, so keep it fast and free of surprising network/file mutations.

### What import actually does

On first import, Python finds a module through import finders and `sys.path`, creates a module object, registers it in `sys.modules`, and executes top-level statements. Later imports usually reuse that object. “Imported once” is per interpreter/module name, and partially initialized entries are why circular imports produce confusing missing attributes.

The current working directory and installation layout affect discovery. Install the project (editable during development) instead of modifying `sys.path`. A `src/` layout helps tests prove they use the installed package rather than accidentally importing the repository directory.

```text
atlas/
├── pyproject.toml
├── src/atlas/__init__.py
├── src/atlas/__main__.py
├── src/atlas/models.py
└── src/atlas/validation.py
```

```python
# src/atlas/__main__.py
from .cli import main

if __name__ == "__main__":
    raise SystemExit(main())
```

Prefer absolute imports for clarity; relative imports are useful inside a package. `from module import *` obscures origins and public API. `__all__` documents wildcard export, not access control. Import cycles indicate tangled responsibilities: move shared contracts to a lower-level module or inject dependencies.

Run package code with `python -m atlas`, ensuring the package import model matches production. Do not modify `sys.path` in application code to compensate for a broken layout.

### Public API and dependency direction

Keep `__init__.py` small and intentional. Re-export only stable public names; importing every submodule increases startup time and cycle risk. Code should depend inward: CLI/web/database adapters import domain/application code, while the domain does not import frameworks.

```python
# src/atlas/__init__.py
from .models import Event
from .service import EventService

__all__ = ["Event", "EventService"]
```

`if __name__ == "__main__"` prevents entry-point behavior during import. It does not make arbitrary top-level code safe: declarations, constants, and cheap deterministic setup belong at module scope; network calls, file writes, and process startup do not.

### Circular-import repair

If `models` imports `service` while `service` imports `models`, identify the shared abstraction and move it to a lower-level module, or pass behavior in through a protocol/callback. A local import can sometimes defer a cycle but often hides a design problem. Type-only imports can use `TYPE_CHECKING` and forward annotations without changing runtime dependency direction.

```python
from typing import TYPE_CHECKING
if TYPE_CHECKING:
    from .repository import EventRepository
```

### Worked package milestone

Add console entry points in `pyproject.toml`, run `python -m atlas`, and import `atlas` in a subprocess. Assert that import writes nothing, starts no threads, opens no database, and performs no network request. Then build/install the wheel in a clean environment to catch packaging omissions.

### Exercises and project

Convert Atlas into `src/atlas`, expose a small public API from `__init__.py`, add `__main__.py`, and draw the dependency direction. Prove imports have no output/side effects.

---

## Chapter 13 — Comprehensions

Comprehensions are compact collection-building expressions. Use them for a clear transformation/filter, not to compress a whole workflow into one line. List, set, and dictionary comprehensions are eager; generator expressions are lazy.

### Reading the syntax

```python
squares = [x * x for x in range(10) if x % 2 == 0]
by_id = {r["id"]: r for r in records}
tags = {tag.casefold() for r in records for tag in r.get("tags", [])}
total = sum(r["value"] for r in records)  # generator expression: no list needed
```

Read `expression for item in iterable if condition` as: iterate, optionally select, then produce. A filtering `if` omits items; a conditional expression transforms every item.

```python
labels = ["positive" if x > 0 else "non-positive" for x in values]
positives = [x for x in values if x > 0]
```

### Choose output semantics deliberately

```python
ordered_names = [user.name for user in users]  # order and duplicates remain
unique_roles = {role for user in users for role in user.roles}
user_by_id = {user.id: user for user in users} # later duplicate ID wins
lazy_sizes = (path.stat().st_size for path in paths)
```

Dictionary comprehensions overwrite duplicate keys. If duplicates violate an invariant, use a loop and raise instead. A set comprehension loses order and duplicate count by design.

### Nested clauses and readability

Clauses follow the same order as equivalent nested loops:

```python
matrix = [[1, 2], [3, 4], [5, 6]]
flat = [value for row in matrix for value in row]

flat_explicit = []
for row in matrix:
    for value in row:
        flat_explicit.append(value)
```

One simple flattening is readable. Multiple filters, exception handling, logging, mutation, or three levels of nesting deserve named helpers and loops. For Cartesian products, `itertools.product` often states intent better.

The assignment expression can compute once, but use it sparingly:

```python
import re
pattern = re.compile(r"^[a-z][a-z0-9_-]{2,31}$")
valid_names = [m.group(0) for name in names if (m := pattern.fullmatch(name))]
```

### Eager versus lazy behavior

Generator expressions are lazy and one-pass. List comprehensions eagerly allocate. Choose based on required ownership/reuse and downstream API—not style alone.

```python
eager = [expensive(x) for x in source]  # all work now; result reusable
lazy = (expensive(x) for x in source)   # work occurs during consumption
first = next(lazy)
```

Laziness can reduce peak memory and stop early with `any`, `all`, `next`, `min`, or `max`; it also delays exceptions until consumption. Comprehension variables have local scope in Python 3. Avoid side effects inside comprehensions because loops make sequencing and partial failure clearer.

### Common mistakes

- Losing order/count by choosing a set merely for brevity.
- Overwriting duplicate dictionary keys without noticing.
- Allocating `[... ]` only to pass it once to `sum`, `any`, or `all`.
- Reusing a consumed generator.
- Repeating an expensive expression in both filter and result.
- Hiding complex business logic or side effects in nested syntax.

### Worked project — Event transformation report

```python
def build_report(records: list[dict[str, object]]) -> dict[str, object]:
    normalized = [str(r["source"]).strip().casefold() for r in records]
    sources = sorted(set(normalized))
    accepted_values = (
        float(r["value"])
        for r in records
        if r.get("status") == "accepted"
    )

    by_id: dict[str, dict[str, object]] = {}
    for record in records:  # explicit loop protects uniqueness
        event_id = str(record["id"])
        if event_id in by_id:
            raise ValueError(f"duplicate id: {event_id}")
        by_id[event_id] = record.copy()

    return {"sources": sources, "accepted_total": sum(accepted_values),
            "by_id": by_id}
```

Professional code mixes comprehensions and loops based on error and data semantics; shortest is not automatically clearest.

### Exercises

1. Convert three simple loops to list/set/dict comprehensions and justify the output type.
2. Rewrite an unreadable three-level comprehension as named loops.
3. Implement `first_valid(records)` with `next` and a generator, including absence.
4. Build an ID index that detects duplicates instead of overwriting them.
5. Measure peak memory for eager and lazy processing of one million integers.

---

## Chapter 14 — Higher-Order Functions

A higher-order function accepts or returns callables. Built-ins such as `sorted`, `min`, and `max` accept `key` functions; this is often clearer than `map`/`filter` chains.

```python
from collections.abc import Callable, Iterable

def select(
    records: Iterable[dict[str, object]],
    predicate: Callable[[dict[str, object]], bool],
) -> list[dict[str, object]]:
    return [r for r in records if predicate(r)]

highest = max(records, key=lambda r: r["value"], default=None)
```

`map` lazily transforms, `filter` lazily selects, and `functools.reduce` combines. Prefer `sum`, `any`, `all`, `min`, `max`, `itertools`, or a loop when they name intent better.

Decorators wrap callables while preserving metadata:

```python
from functools import wraps
from time import perf_counter

def timed(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = perf_counter()
        try:
            return func(*args, **kwargs)
        finally:
            print(f"{func.__name__}: {perf_counter() - start:.6f}s")
    return wrapper
```

Production timing should use logging/metrics and preserve sync/async semantics. Decorator order is bottom-up at definition time.

### Exercises and project

Implement configurable predicates and sort keys. Add a metadata-preserving timing decorator; test return values and exceptions.

---

## Chapter 15 — Python Error Types and Tracebacks

Errors are evidence. Read the final exception type/message first, then frames from your code outward. A traceback shows the active call chain, not necessarily the moment the bad state originated.

| Error | Meaning and usual diagnosis |
|---|---|
| `SyntaxError`, `IndentationError` | Parser cannot form the program; inspect marked token and preceding delimiters. |
| `NameError`, `UnboundLocalError` | Name missing or made local by assignment before read. |
| `TypeError` | Operation/call incompatible with object types/signature. |
| `ValueError` | Type accepted but value violates the operation's domain. |
| `AttributeError` | Object lacks an attribute; inspect actual type and spelling. |
| `KeyError`, `IndexError` | Mapping key or sequence index absent. |
| `ModuleNotFoundError`, `ImportError` | Environment/path/module exists incorrectly or import symbol fails. |
| `OSError` family | Filesystem/network/process OS failure; inspect `errno`, filename, cause. |

```python
def parse_count(text: str) -> int:
    value = int(text)            # may raise ValueError
    if value < 0:
        raise ValueError("count must be non-negative")
    return value
```

Use `python -m pdb app.py` or `breakpoint()` to stop and inspect. Reduce the input, reproduce deterministically, identify the violated invariant, fix the cause, then add a regression test. Do not catch `Exception` merely to print and continue with invalid state.

### Worked diagnosis — read from the bottom upward

```python
def mean_text(values: list[str]) -> float:
    numbers = [int(value) for value in values]
    return sum(numbers) / len(numbers)


print(mean_text(["10", "twenty", "30"]))
```

The final line of the traceback is similar to
`ValueError: invalid literal for int() with base 10: 'twenty'`. The frame immediately
above it points to the conversion in the comprehension; callers above that explain
how execution arrived there. Replacing the conversion with a broad `except` would
hide which record was invalid. Add context and preserve the cause instead:

```python
def parse_integer(text: str, *, position: int) -> int:
    try:
        return int(text)
    except ValueError as exc:
        raise ValueError(f"item {position} is not an integer: {text!r}") from exc
```

Syntax errors differ: the program did not begin running. Runtime exceptions mean a
validly parsed path failed. Logical errors may raise nothing, so tests and debugging
must compare actual behavior with the requirement.

### Exercises and project

Create one example for each error family, interpret its traceback, and fix it. Add error context to Atlas without losing the original exception chain.

---

## Chapter 16 — Date and Time

Time has an instant, timezone, calendar representation, precision, and clock source. Use aware UTC datetimes for instants; convert for display at boundaries.

```python
from datetime import UTC, datetime, timedelta
from zoneinfo import ZoneInfo

now = datetime.now(UTC)
expires = now + timedelta(minutes=15)
tehran = now.astimezone(ZoneInfo("Asia/Tehran"))
encoded = now.isoformat()
decoded = datetime.fromisoformat(encoded)
```

Naive datetimes have no timezone interpretation and are unsafe for global instants. Timezone offsets change historically and through daylight-saving rules; use IANA zones through `zoneinfo`, not a fixed offset when civil-time rules matter.

Use `time.monotonic()`/`perf_counter()` for durations and deadlines because wall clock can jump. Unix timestamps represent seconds from an epoch but do not carry timezone/display format. `strptime` parses according to a format; validate ambiguous user dates.

```python
from time import monotonic
deadline = monotonic() + 2.0
while monotonic() < deadline:
    if ready():
        break
```

### Exercises and project

Store `observed_at` in UTC, display it in two zones, reject naive inputs, and implement a monotonic retry deadline. Test a DST transition.

---

## Chapter 17 — Exception Handling

Catch exceptions only where you can add context, recover, translate across a boundary, or clean up. Catch the narrowest expected type.

```python
class AtlasError(Exception):
    """Base exception for public Atlas failures."""

class InvalidRecordError(AtlasError):
    pass

def load_count(text: str) -> int:
    try:
        value = int(text)
    except ValueError as exc:
        raise InvalidRecordError(f"invalid count {text!r}") from exc
    else:
        if value < 0:
            raise InvalidRecordError("count cannot be negative")
        return value
```

`else` runs only when the `try` block succeeds; `finally` always runs and is for cleanup, but context managers are usually clearer. Exception chaining (`raise ... from exc`) preserves causality. Bare `except:` also catches cancellation/system-exit signals; almost never use it.

Exception groups and `except*` handle multiple independent failures from concurrent work. Design public exception hierarchies sparingly. Do not use exceptions for ordinary high-volume branching when a normal result type is clearer.

### Exercises and project

Translate CSV parsing errors into `InvalidRecordError` with line context. Ensure file cleanup through `with`; test success, expected failure, and unexpected failure propagation.

---

## Chapter 18 — Regular Expressions

Regex matches text patterns; it is not a parser for arbitrary nested languages. Use raw strings so Python escaping does not compete with regex escaping.

```python
import re

LINE_RE = re.compile(
    r"^(?P<source>[A-Za-z][\w-]{0,31}):(?P<count>0|[1-9]\d*)$"
)

match = LINE_RE.fullmatch("sensor-a:42")
if match:
    source = match["source"]
    count = int(match["count"])
```

`search` finds anywhere, `match` begins at the start, `fullmatch` requires the whole string, `finditer` yields match objects, and `sub` replaces. Groups capture; `(?:...)` groups without capture; `(?P<name>...)` names a group. Flags control case, multiline anchors, dot behavior, and verbosity.

**SECURITY:** ambiguous nested quantifiers can cause catastrophic backtracking and denial of service. Bound input length, simplify patterns, use timeouts through suitable engines/process isolation where needed, and prefer explicit parsing for structured formats.

### Worked comparison — regex or ordinary string operations?

For exactly one literal separator, `partition` produces clearer error handling:

```python
def parse_record(line: str) -> tuple[str, int]:
    source, separator, raw_count = line.partition(":")
    if not separator or not source or not raw_count.isdecimal():
        raise ValueError(f"invalid record: {line!r}")
    return source, int(raw_count)


assert parse_record("sensor-a:42") == ("sensor-a", 42)
```

Choose regex when the grammar has alternatives, repetition, or named fields that
would otherwise require error-prone manual scanning. Test empty input, a near match,
Unicode policy, maximum length, and trailing junk. `[A-Z]` and `\w` do not express
the same Unicode policy; document which identifiers the application accepts.

### Exercises and project

Parse Atlas text records with named groups, reject trailing junk, extract URLs from controlled text, and benchmark a malicious near-match against a rewritten safe pattern.

---

## Chapter 19 — File Handling

Files are resources and byte streams. `open` returns a context manager; specify text encoding explicitly.

```python
from pathlib import Path

path = Path("data/events.jsonl")
with path.open("r", encoding="utf-8", newline="") as stream:
    for line_number, line in enumerate(stream, 1):
        process(line_number, line)
```

Modes: `r` read, `w` truncate/create, `a` append, `x` exclusive create, `b` binary, `+` update. Text I/O encodes/decodes and translates newlines; binary I/O returns bytes. Streaming avoids loading unbounded files.

### Structured formats and atomic replacement

```python
import json
import os
import tempfile

def atomic_json(path: Path, value: object) -> None:
    path.parent.mkdir(parents=True, exist_ok=True)
    with tempfile.NamedTemporaryFile(
        "w", encoding="utf-8", dir=path.parent, delete=False
    ) as tmp:
        json.dump(value, tmp, ensure_ascii=False)
        tmp.flush()
        os.fsync(tmp.fileno())
        temp_name = tmp.name
    os.replace(temp_name, path)
```

JSON supports only a limited data model; validate schema/types after decoding. CSV must use the `csv` module with correct newline handling, not `split(',')`. Pickle can execute code while loading—never unpickle untrusted input.

`pathlib` composes paths without unsafe string separators. Resolve/canonicalize carefully: path traversal protection also needs trusted roots, race-resistant operations, and permission boundaries.

### Exercises and project

Read/write JSON Lines and CSV, stream a large file, quarantine malformed rows, and implement atomic state saving with recovery tests.

---

## Chapter 20 — Python Package Management

Packages are supply-chain inputs. Install into an isolated environment, declare dependencies in `pyproject.toml`, distinguish direct from transitive dependencies, and review updates.

```bash
python3.14 -m venv .venv
. .venv/bin/activate                 # Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install requests
python -m pip list
python -m pip check
python -m pip uninstall requests
```

Modern project metadata:

```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "atlas-data-platform"
version = "0.1.0"
requires-python = ">=3.12"
dependencies = ["httpx>=0.27,<1", "pydantic>=2,<3"]

[project.optional-dependencies]
dev = ["pytest", "ruff", "mypy"]
```

Version ranges are policy. Applications often lock a fully resolved environment; libraries usually declare compatible ranges. Hashes, internal mirrors, vulnerability scanning, licenses, provenance, and reproducible builds matter. Never trust a package merely because its name resembles a popular one.

### Exercises and project

Create Atlas metadata, install it editable (`python -m pip install -e '.[dev]'`), inspect dependency metadata, build a wheel, and install the wheel into a clean venv.

---

## Chapter 21 — Classes and Objects

Use classes when data and invariants have behavior/lifecycle; use functions and plain mappings when they are clearer. Prefer composition over inheritance unless there is a genuine substitutable “is-a” relationship.

```python
from dataclasses import dataclass, field
from datetime import UTC, datetime

@dataclass(frozen=True, slots=True)
class Event:
    source: str
    value: float
    observed_at: datetime = field(default_factory=lambda: datetime.now(UTC))

    def __post_init__(self) -> None:
        if not self.source.strip():
            raise ValueError("source cannot be blank")
        if self.observed_at.tzinfo is None:
            raise ValueError("observed_at must be timezone-aware")
```

`default_factory` avoids shared mutable/default-time bugs. `frozen` discourages mutation but is not a security boundary; `slots` can reduce per-instance memory and prevents arbitrary new attributes, with inheritance/tooling tradeoffs.

Instance methods receive `self`; class methods receive `cls` and suit alternate constructors; static methods are namespaced functions and often belong at module level. Properties preserve attribute syntax while controlling calculation/validation, but surprising I/O or expensive work in a property is poor design.

Special methods implement protocols: `__repr__`, `__eq__`, `__hash__`, iteration, context management, arithmetic. Equality/hash must agree and mutable value objects should not be hash keys. ABCs express nominal interfaces; `Protocol` later provides structural typing.

### Construction, instance state, inheritance, and composition

`__new__` creates an instance and `__init__` initializes an already-created one.
Ordinary application classes almost always customize only `__init__`. Attributes on
an instance normally live separately from class attributes:

```python
class Counter:
    category = "events"                 # shared class attribute

    def __init__(self, start: int = 0) -> None:
        self.value = start               # per-instance attribute

    def increment(self) -> int:
        self.value += 1
        return self.value


left = Counter()
right = Counter(10)
assert left.increment() == 1
assert right.value == 10
```

Inheritance is appropriate only when every subclass can honor the base contract.
Use `super()` so cooperative method resolution can work; do not call a particular
parent by name unless deliberately bypassing that protocol.

```python
class Formatter:
    def format(self, value: object) -> str:
        return str(value)


class PrefixFormatter(Formatter):
    def __init__(self, prefix: str) -> None:
        self.prefix = prefix

    def format(self, value: object) -> str:
        return self.prefix + super().format(value)


assert PrefixFormatter("event=").format(7) == "event=7"
```

Most domain services need composition instead: an `EventService` *has a*
repository, rather than *is a* repository. Composition keeps policies replaceable
without inheriting implementation details. A single leading underscore marks a
non-public attribute by convention; double-leading underscores trigger name
mangling, not security. Python does not enforce private access boundaries.

### Choosing the simplest representation

Use a plain value for one value, a tuple for a short local positional shape, a
dictionary for dynamic external fields, a dataclass for a stable data model, and a
handwritten class when construction/lifecycle/behavior needs more control. Do not
create getters and setters mechanically; use direct attributes until an invariant
requires a property or method.

### Exercises and project

Model Event, Batch, and SourceConfig with invariants and value semantics. Add an alternate constructor from a mapping, test equality/repr, and explain composition versus a proposed inheritance tree.

---

## Chapter 22 — Web Scraping

Scraping is an HTTP client plus an HTML parser plus an ethical/operational policy. Confirm permission, Terms of Service, robots guidance, copyright/privacy, and rate limits. Prefer an official API when available.

```python
import httpx
from bs4 import BeautifulSoup

with httpx.Client(
    timeout=httpx.Timeout(10.0),
    follow_redirects=True,
    headers={"User-Agent": "AtlasResearchBot/1.0 contact@example.com"},
) as client:
    response = client.get("https://example.com/data")
    response.raise_for_status()
    if "text/html" not in response.headers.get("content-type", ""):
        raise ValueError("expected HTML")
    soup = BeautifulSoup(response.text, "html.parser")
    rows = [node.get_text(" ", strip=True) for node in soup.select("table.data tr")]
```

Set connect/read/write/pool timeouts, bound response size, retry only safe/idempotent requests with backoff+jitter, cache responsibly, and stop on repeated errors. CSS/XPath selectors break as sites change; validate extracted fields and retain a fixture for tests. JavaScript-rendered pages may require browser automation, but that adds cost and attack surface. Never bypass access controls or CAPTCHA.

### Project

Build an authorized scraper adapter with rate limiting, conditional requests (`ETag`/`Last-Modified`), pagination bounds, fixture-based parser tests, and provenance (URL/time/hash).

---

## Chapter 23 — Virtual Environments

A venv isolates interpreter-level package installation, not the OS, network, filesystem, or secrets.

### Why environments exist

Two projects may require incompatible versions of the same library. Installing both into a global interpreter makes resolution depend on whichever command ran last. A virtual environment gives one project its own interpreter entry points and `site-packages` directory while reusing the base interpreter's standard library/runtime.

```bash
python3.14 -m venv .venv
. .venv/bin/activate
python -c "import sys; print(sys.executable); print(sys.prefix)"
python -m pip install -e '.[dev]'
deactivate
```

Activation primarily adjusts `PATH` and environment metadata; it does not “turn Python into” a different language runtime. CI and scripts can invoke `.venv/bin/python` directly. Prefer `python -m pip` so the installer unquestionably belongs to the selected interpreter.

```bash
python -c "import sys; print(sys.executable)"
python -m pip --version
python -m pip check
```

If `pip` and `python` report different environment paths, stop and fix interpreter selection. Deleting a venv should be safe because dependencies and project metadata—not the directory—are the source of truth.

### Reproducibility and limits

Do not commit `.venv`; recreate it from `pyproject.toml` and the project's chosen lock/constraints mechanism. A venv does not pin Python itself, system libraries, CPU architecture, locale, timezone database, external services, or OS tools. Record those separately where results depend on them.

Containers isolate filesystem/process/network layers differently and often contain a venv or an installed wheel. Neither is a security sandbox by itself. Secrets remain accessible to code running inside the environment.

### Troubleshooting

- `ModuleNotFoundError` often means the package was installed into another interpreter.
- A stale venv may contain absolute paths to a moved/deleted interpreter; recreate it.
- IDE, shell, test runner, and notebook kernel must all select the same environment.
- Editable installs expose source changes immediately; test the built wheel separately before release.

### Project and verification

Document clean setup on Linux/macOS/Windows. Build a wheel, create a second empty environment, install only that wheel plus declared runtime dependencies, run a smoke test from outside the repository, then delete and recreate both environments. Record Python version and dependency inventory.

---

## Chapter 24 — Statistics and NumPy

Descriptive statistics summarize a sample; inference makes assumptions about a population/process. Always define missingness, units, sampling mechanism, outliers, and uncertainty before computing.

```python
from statistics import mean, median, stdev

values = [1.0, 2.0, 100.0]
summary = {"n": len(values), "mean": mean(values), "median": median(values),
           "sample_sd": stdev(values)}
```

Variance/stdev distinguish sample versus population formulas. Correlation is not causation; a p-value is not effect size or probability the hypothesis is true. Report confidence intervals and practical significance.

NumPy stores homogeneous n-dimensional arrays and vectorizes operations:

```python
import numpy as np

x = np.asarray(values, dtype=np.float64)
finite = x[np.isfinite(x)]
z = (finite - finite.mean()) / finite.std(ddof=1)
```

Views can share memory; advanced/boolean indexing commonly copies. Broadcasting aligns trailing dimensions and can accidentally create huge intermediates. Integer dtypes can overflow; floating reductions have order/precision effects. Fix and record RNG generators (`np.random.default_rng(seed)`) for reproducible experiments.

### Project

Compute robust summaries, quantiles, confidence intervals through bootstrap, and document assumptions. Compare vectorized and Python-loop results for correctness before timing.

---

## Chapter 25 — Pandas

> **Level:** Beginner → Intermediate · **Prerequisites:** Chapters 4–13 and 24  
> **Dependency:** `python -m pip install "pandas>=3,<4"`  
> **Reference baseline:** Pandas 3.0; pin the version used by a real project.

Pandas is a library for manipulating *labeled tabular data*. Use it to load CSV,
Excel, Parquet, SQL results and similar tables; clean inconsistent values; join
tables; calculate grouped statistics; reshape wide/long layouts; analyze time
series; and prepare reports or model inputs. It is not a database, spreadsheet UI,
distributed engine, or replacement for understanding the data's meaning.

### Learning objectives

After this chapter you should be able to create and inspect `Series`/`DataFrame`
objects; reason about index alignment and dtypes; select and update safely; handle
missing/duplicate data; transform strings, numbers and dates; aggregate, join and
reshape tables; read/write common formats; avoid common performance/correctness
traps; and build a tested cleaning pipeline.

### 25.1 Mental model: values plus labels

A `Series` is a one-dimensional array with an `Index`. A `DataFrame` is a
two-dimensional table whose columns may have different dtypes and whose rows and
columns both have labels.

```python
import pandas as pd

temperatures = pd.Series(
    [21.5, 19.0, 24.5], index=["Tehran", "Tabriz", "Shiraz"], name="celsius"
)
assert temperatures.loc["Tabriz"] == 19.0

events = pd.DataFrame(
    {
        "event_id": ["e1", "e2", "e3"],
        "source": ["alpha", "beta", "alpha"],
        "value": [10.0, 20.5, 12.0],
        "valid": [True, False, True],
    }
)
assert events.shape == (3, 4)
```

The index is not merely row decoration: Pandas aligns labeled objects during
arithmetic and assignment.

```python
left = pd.Series([10, 20], index=["a", "b"])
right = pd.Series([1, 2], index=["b", "c"])
result = left + right
assert pd.isna(result["a"]) and result["b"] == 21 and pd.isna(result["c"])
```

Only label `b` existed on both sides. Use `left.add(right, fill_value=0)` only when
treating absence as zero is correct for the domain. Use `reset_index(drop=True)` or
explicit NumPy arrays only when positional semantics are truly intended.

### 25.2 Creating and inspecting a DataFrame

Construct from dictionaries, records, arrays, or readers such as `read_csv`.

```python
records = [
    {"id": 1, "city": "Tehran", "score": 18.5},
    {"id": 2, "city": "Tabriz", "score": 17.0},
]
df = pd.DataFrame.from_records(records)

print(df.head())           # first rows
print(df.tail())           # last rows
print(df.shape)            # (rows, columns)
print(df.columns.tolist())
print(df.dtypes)
df.info(memory_usage="deep")
print(df.describe(include="all"))
```

Before transforming unfamiliar data, inspect shape, column names, dtypes, sample
rows, missing counts, uniqueness and plausible ranges. `head()` alone cannot reveal
rare invalid values.

```python
profile = pd.DataFrame({
    "dtype": df.dtypes.astype(str),
    "missing": df.isna().sum(),
    "unique": df.nunique(dropna=False),
})
```

### 25.3 Selecting rows and columns

Use brackets for columns, `.loc` for labels/boolean masks, and `.iloc` for integer
positions. A single column is a Series; a list of columns produces a DataFrame.

```python
scores = df["score"]                       # Series
small_table = df[["id", "score"]]         # DataFrame
first_row = df.iloc[0]
first_two = df.iloc[:2, :2]
tehran = df.loc[df["city"].eq("Tehran"), ["id", "score"]]
high = df.loc[df["score"].between(18, 20)]
selected = df.loc[df["city"].isin(["Tehran", "Shiraz"])]
```

Combine masks with `&`, `|`, and `~`; parenthesize every comparison because Python's
`and`/`or` do not perform elementwise Series logic.

```python
mask = (df["score"] >= 17) & (df["city"] != "Tabriz")
result = df.loc[mask]
```

Prefer explicit `.loc` assignment. Chained assignment is ambiguous and is rejected
under modern Copy-on-Write behavior.

```python
df.loc[df["score"] < 18, "needs_review"] = True
# Avoid: df[df["score"] < 18]["needs_review"] = True
```

### 25.4 Dtypes and conversion

Dtype determines valid values, missing representation, memory and available
operations. Common dtypes include integer, floating, boolean, datetime, timedelta,
string and category. Prefer nullable extension dtypes when missing values are valid:

```python
typed = pd.DataFrame(
    {
        "count": pd.Series([1, None, 3], dtype="Int64"),
        "active": pd.Series([True, None, False], dtype="boolean"),
        "name": pd.Series(["a", None, "c"], dtype="string"),
    }
)
```

Convert deliberately. `errors="coerce"` replaces invalid parsing with missing data;
never use it without counting/reporting what was lost.

```python
raw = pd.Series(["10", "bad", "12"], dtype="string")
numbers = pd.to_numeric(raw, errors="coerce")
invalid = raw[numbers.isna() & raw.notna()]
assert invalid.tolist() == ["bad"]
```

`astype` converts an already compatible representation; `to_numeric` and
`to_datetime` are parsers. Categories suit a bounded repeated vocabulary, save
memory, and can define an order—but new values must first be added to the category.

### 25.5 Missing values and duplicates

Depending on dtype, missingness may appear as `pd.NA`, `NaN`, `NaT`, or `None`. Test
with `isna`/`notna`, never `value == pd.NA`.

```python
missing_per_column = typed.isna().sum()
complete = typed.dropna(subset=["name"])
filled = typed.assign(count=typed["count"].fillna(0))
```

Dropping, filling, interpolating, or retaining missing data is a domain decision.
Filling unknown revenue with zero changes meaning; forward-filling a sensor value
assumes it remains valid until the next observation. Record the policy.

```python
duplicate_mask = events.duplicated(subset=["source", "event_id"], keep=False)
duplicates = events.loc[duplicate_mask]
events_unique = events.drop_duplicates(
    subset=["source", "event_id"], keep="last"
)
```

Choose `keep="last"` only when ordering has a documented meaning. Duplicate index
labels can make selection surprising; a stable unique key is usually safer.

### 25.6 Cleaning and transforming columns

String methods under `.str` operate elementwise and normally preserve missingness.
Datetime components use `.dt`.

```python
dirty = pd.DataFrame({
    "source": [" Alpha ", "BETA", None],
    "value": ["10.5", "bad", "12"],
    "observed_at": ["2026-01-01T10:00:00Z", "invalid", None],
})

clean = dirty.assign(
    source=lambda x: x["source"].astype("string").str.strip().str.casefold(),
    value=lambda x: pd.to_numeric(x["value"], errors="coerce"),
    observed_at=lambda x: pd.to_datetime(x["observed_at"], errors="coerce", utc=True),
)
clean["day"] = clean["observed_at"].dt.floor("D")
```

`assign` supports readable transformation pipelines. `rename`, `replace`, `map`,
`where`, `mask`, `clip`, `sort_values`, and `sort_index` cover common cleanup:

```python
normalized = (
    clean.rename(columns={"value": "reading"})
         .loc[lambda x: x["source"].notna()]
         .assign(reading=lambda x: x["reading"].clip(lower=0, upper=100))
         .sort_values(["source", "observed_at"], na_position="last")
         .reset_index(drop=True)
)
```

Prefer vectorized column operations over `iterrows`. Use `map` for elementwise
mapping, `agg` for reductions, and `transform` when output must align with input.
Use row-wise `apply(axis=1)` only when no clear vectorized formulation exists and
measurement shows its cost is acceptable.

### 25.7 Summaries, GroupBy, windows, and ranking

`groupby` implements split → apply → combine. Aggregation returns one or more
summary rows per group; transformation returns one aligned value per original row;
filtering retains or removes whole groups.

```python
events = pd.DataFrame({
    "source": ["a", "a", "b", "b"],
    "value": [10.0, 14.0, 8.0, 12.0],
})

report = events.groupby("source", as_index=False).agg(
    count=("value", "size"),
    mean=("value", "mean"),
    minimum=("value", "min"),
    maximum=("value", "max"),
)
events["source_mean"] = events.groupby("source")["value"].transform("mean")
events["difference"] = events["value"] - events["source_mean"]
```

Know whether to use `size` (rows, including missing values) or `count` (non-missing
values). Useful analytical operations include `value_counts`, `rank`, `cumsum`,
`diff`, `shift`, `pct_change`, `rolling`, `expanding`, and exponentially weighted
windows.

```python
events["rolling_mean"] = events.groupby("source")["value"].transform(
    lambda values: values.rolling(2, min_periods=1).mean()
)
```

Sort within each group before order-dependent operations.

### 25.8 Combining tables

`concat` stacks compatible objects by rows or columns. `merge` performs database-like
joins on keys. Always state the expected cardinality.

```python
users = pd.DataFrame({"user_id": [1, 2], "name": ["Ada", "Grace"]})
orders = pd.DataFrame({"order_id": [10, 11, 12], "user_id": [1, 1, 2]})

enriched = orders.merge(
    users,
    on="user_id",
    how="left",
    validate="many_to_one",
    indicator=True,
)
assert enriched["_merge"].eq("both").all()
```

`validate` detects accidental many-to-many multiplication. Audit unmatched keys.
Use `one_to_one`, `one_to_many`, `many_to_one`, or `many_to_many` intentionally.

```python
combined = pd.concat([events.iloc[:2], events.iloc[2:]], ignore_index=True)
assert len(combined) == len(events)
```

### 25.9 Reshaping: wide and long

Long/tidy data commonly stores one observation per row. `melt` converts wide to
long; `pivot` requires unique row/column pairs; `pivot_table` aggregates duplicates.

```python
wide = pd.DataFrame({"city": ["Tehran", "Tabriz"], "2025": [20, 18], "2026": [21, 19]})
long = wide.melt(id_vars="city", var_name="year", value_name="temperature")
round_trip = long.pivot(index="city", columns="year", values="temperature")
```

Also learn `stack`/`unstack`, `explode` for list-like cells, `crosstab` for frequency
tables, and `get_dummies` for indicator columns. Avoid MultiIndex unless hierarchical
labels materially simplify the task; reset it before APIs that expect ordinary
columns.

### 25.10 Time series

Parse instants with an explicit timezone policy, sort before time operations, and
distinguish calendar periods from elapsed durations.

```python
readings = pd.DataFrame({
    "observed_at": pd.to_datetime(
        ["2026-01-01T00:10:00Z", "2026-01-01T01:20:00Z"], utc=True
    ),
    "value": [10.0, 14.0],
}).set_index("observed_at").sort_index()

hourly = readings.resample("1h").agg(mean=("value", "mean"), count=("value", "size"))
```

`resample` groups by time bins; `rolling` uses moving windows. Learn bin boundary,
label, timezone and daylight-saving behavior before analyzing civil time.

### 25.11 Reading and writing data

CSV has no embedded schema, so declare what you know and validate afterward.

```python
df = pd.read_csv(
    "events.csv",
    usecols=["event_id", "source", "value", "observed_at"],
    dtype={"event_id": "string", "source": "string"},
    na_values=["", "NA", "null"],
)
df["value"] = pd.to_numeric(df["value"], errors="raise")
df["observed_at"] = pd.to_datetime(df["observed_at"], utc=True, errors="raise")
```

Use `read_excel` for spreadsheets, `read_json` for suitable JSON shapes,
`read_sql_query` with parameterized SQL, and `read_parquet` for typed columnar data.
Write with `to_csv(index=False)` or `to_parquet(index=False)`. Parquet preserves
dtypes better and supports column projection, but compatibility still requires a
declared schema and tested engine.

For large inputs, read only needed columns/rows, filter at the database, or process
CSV in `chunksize` batches when the calculation can be combined incrementally.

### 25.12 Visualization and reporting

`df.plot(...)` offers quick plotting through a configured backend, commonly
Matplotlib. Plot distributions, missingness, trends and group comparisons during
exploration; label axes/units and do not treat a chart as proof of causality.

```python
axis = events.plot(kind="bar", x="source", y="value", legend=False)
axis.set_ylabel("reading (unit)")
```

Use `Styler` for display formatting, not for changing underlying numeric values.

### 25.13 Performance and correctness

- Prefer vectorized operations and built-in groupby/merge/window methods.
- Choose dtypes deliberately; inspect with `info(memory_usage="deep")`.
- Filter columns and rows early, but preserve correctness/audit columns.
- Avoid repeated `concat` in a loop; collect frames and concatenate once.
- Avoid `iterrows` for transformation; it is slow and may coerce row dtypes.
- Do not assume `inplace=True` is faster or safer.
- Treat intermediate DataFrames as values; assign the returned result.
- Profile realistic data before switching tools.

Pandas is an in-memory single-machine tool. If data does not fit, first improve
dtypes/projection, aggregate in SQL, stream an associative calculation, or use a
columnar format. Move to Polars/Dask/Spark only after workload and operational needs
justify another execution model.

### 25.14 A complete validation pipeline

```python
def clean_events(raw: pd.DataFrame) -> tuple[pd.DataFrame, pd.DataFrame]:
    required = {"event_id", "source", "value", "observed_at"}
    missing_columns = required - set(raw.columns)
    if missing_columns:
        raise ValueError(f"missing columns: {sorted(missing_columns)}")

    work = raw.loc[:, sorted(required)].copy()
    work["event_id"] = work["event_id"].astype("string").str.strip()
    work["source"] = work["source"].astype("string").str.strip().str.casefold()
    work["value"] = pd.to_numeric(work["value"], errors="coerce")
    work["observed_at"] = pd.to_datetime(work["observed_at"], errors="coerce", utc=True)

    invalid = (
        work["event_id"].isna() | work["event_id"].eq("") |
        work["source"].isna() | work["source"].eq("") |
        work["value"].isna() | work["observed_at"].isna() |
        work.duplicated(["source", "event_id"], keep=False)
    )
    rejected = work.loc[invalid].copy()
    accepted = work.loc[~invalid].sort_values(
        ["observed_at", "source", "event_id"]
    ).reset_index(drop=True)
    return accepted, rejected
```

This function preserves rejected records instead of silently dropping them. A real
pipeline should attach reason codes and original row numbers, validate numeric
ranges/units, and publish outputs atomically.

### Common mistakes

- Assuming the index is row position or forgetting automatic alignment.
- Using `and`/`or` instead of `&`/`|` for masks.
- Chained assignment instead of one `.loc` operation.
- Silently coercing invalid input and then dropping the resulting missing values.
- Confusing `size` with `count` or aggregation with transformation.
- Performing a many-to-many merge unintentionally.
- Parsing dates without timezone/format/error policy.
- Looping row by row for a vectorizable calculation.
- Treating inferred CSV dtypes or notebook display as a data contract.
- Mutating a shared DataFrame across pipeline stages.

### Exercises and project

1. Build Series with mismatched indexes; predict and test arithmetic alignment.
2. Select rows using three combined conditions with `.loc` and explain parentheses.
3. Parse nullable integers, booleans, strings and UTC datetimes; report failures.
4. Compare `agg`, `transform` and `filter` on the same grouped dataset.
5. Demonstrate one-to-one, many-to-one and accidental many-to-many merges.
6. Convert a wide monthly table to long form and back; explain duplicate handling.
7. Compute daily resampling and a seven-observation rolling mean without mixing them.
8. Measure vectorized arithmetic against `iterrows` on realistic data and verify equal output.

**Capstone:** build raw → validated → curated → report stages. Require schema checks,
row/reason quarantine, duplicate policy, merge-cardinality validation, UTC time
windows, grouped/windowed reports, Parquet output, input/output hashes and tests for
empty data, missing columns, malformed values, duplicate keys, unmatched joins and
timezone boundaries. The project passes only when rerunning the same input produces
the same ordered data and quality report.

### Completion criteria

Without copying examples, explain Series/DataFrame/Index/dtype; implement selection,
cleaning, grouping, joining, reshaping and time analysis; predict alignment and
missing-value behavior; diagnose a chained assignment or merge explosion; and test
a complete pipeline. Continue with Chapter 52 for schema evolution, partitioning,
incremental rebuilds and production operations.

---

## Chapter 26 — Python for the Web

HTTP requests contain method, target, headers and optional body; responses contain status, headers and body. GET should be safe/idempotent; POST creates/processes; PUT replaces idempotently; PATCH partially updates; DELETE intends removal. Caches, proxies, cookies, TLS, same-origin/CORS and authentication affect behavior.

### Request lifecycle and boundaries

The server accepts a connection, a reverse proxy may terminate TLS, middleware applies cross-cutting policy, routing chooses a handler, validation converts external bytes into typed data, application logic runs, and serialization creates the response. Keep transport-specific objects at the edge so the domain can be tested without a web server.

Status codes are part of the contract: 2xx is success, 3xx redirects, 4xx means the request/authorization cannot be fulfilled as sent, and 5xx means the server failed. A JSON body saying `{"success": false}` with status 200 breaks caches, monitoring, and clients.

Web applications separate transport, validation, domain logic, persistence, and templates/serialization. WSGI serves synchronous Python applications; ASGI supports async connections and modern protocols. Never use a framework's development server as the production plan.

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/health")
def health() -> dict[str, str]:
    return {"status": "ok"}
```

WSGI defines a synchronous request/response interface. ASGI also represents asynchronous connections, lifespan, streaming, and WebSockets. `async def` helps only when called libraries perform non-blocking I/O; CPU-heavy or blocking code still blocks the event loop and must be moved or redesigned.

### State and security

HTTP is stateless, so identity/state arrives through cookies, authorization headers, or explicit tokens. Cookies carrying sessions should normally be `Secure`, `HttpOnly`, and use an appropriate `SameSite` policy. Browser forms using cookie authentication need CSRF protection. HTML needs context-aware escaping; SQL/commands require parameterized APIs, not string interpolation.

Do not trust arbitrary proxy-forwarded headers unless the connection comes through configured proxies. Configuration and secrets come from runtime configuration/secret systems, not source control. Distinguish liveness (“process can run”) from readiness (“can safely receive traffic”).

### Worked example — thin transport

```python
from fastapi import Depends, FastAPI, HTTPException

app = FastAPI()

@app.get("/events/{event_id}")
def get_event(event_id: str, service=Depends(get_service)):
    event = service.find(event_id)
    if event is None:
        raise HTTPException(status_code=404, detail={"code": "event_not_found"})
    return EventResponse.from_domain(event)
```

The handler translates HTTP input/output and expected errors; it does not contain database queries or domain rules.

### Project

Serve Atlas health and an HTML summary through a thin transport layer calling existing domain services.

---

## Chapter 27 — Python with MongoDB

MongoDB stores BSON documents in collections. Model access patterns first: embedding makes one-document reads/atomic updates easy; references reduce duplication but require joins/application coordination. Enforce validation and indexes.

```python
from datetime import UTC, datetime
from pymongo import ASCENDING, MongoClient

client = MongoClient("mongodb://localhost:27017", serverSelectionTimeoutMS=3000)
db = client.atlas
events = db.events
events.create_index([("source", ASCENDING), ("external_id", ASCENDING)], unique=True)
events.insert_one({"source": "alpha", "external_id": "42",
                   "value": 3.5, "observed_at": datetime.now(UTC)})
doc = events.find_one({"source": "alpha", "external_id": "42"}, {"_id": 0})
```

Use operators (`$set`, `$inc`, `$in`) rather than constructing untrusted query documents. Projection limits returned fields; `explain` and indexes diagnose performance. Unique indexes enforce concurrency-safe uniqueness better than check-then-insert. Multi-document transactions cost coordination and require supported deployments; design for single-document atomicity when possible. Manage client lifecycle once per process and configure timeouts/write concern/read concern deliberately.

### Data modeling and update semantics

Embed data read and updated with its parent when size remains bounded. Reference independently growing/shared entities. MongoDB guarantees atomicity for a single-document write; conditional updates can implement compare-and-set without a transaction.

```python
result = events.update_one(
    {"_id": event_id, "version": expected_version},
    {"$set": {"status": "processed"}, "$inc": {"version": 1}},
)
if result.matched_count == 0:
    raise RuntimeError("event missing or concurrently modified")
```

An index accelerates matching/sorting at the cost of storage and write work. Index prefix/order must reflect actual filters and sorts. Examine execution statistics rather than assuming an index is used. Avoid unbounded arrays/documents and unbounded result cursors.

### Boundary conversion and errors

BSON differs from JSON: it has `ObjectId`, datetime, binary, decimal and other types. Convert database documents explicitly into domain models and API responses. Translate duplicate-key and timeout errors at the adapter boundary while preserving causal chains. Never expose internal IDs or raw driver errors accidentally.

### Project

Implement a repository interface with upsert, pagination using a stable indexed cursor, aggregation by source, schema validation, duplicate handling, and integration tests against an isolated database.

---

## Chapter 28 — Consuming APIs

Treat every remote response as untrusted and every network call as fallible.

```python
from pydantic import BaseModel, ValidationError
import httpx

class RemoteEvent(BaseModel):
    id: str
    value: float

def fetch_event(client: httpx.Client, base_url: str, event_id: str) -> RemoteEvent:
    response = client.get(f"{base_url}/events/{event_id}", timeout=5.0)
    response.raise_for_status()
    try:
        return RemoteEvent.model_validate(response.json())
    except (ValueError, ValidationError) as exc:
        raise RuntimeError("remote API returned an invalid event") from exc
```

URL-encode through client parameters, verify TLS, never log tokens, bound body sizes, and distinguish transport errors, HTTP errors, decoding errors and schema errors. Retry idempotent operations on selected transient failures, respect `Retry-After`, add jitter, and use idempotency keys where the server supports safe POST retries. Pagination must have stop conditions and deduplication.

### Client ownership and error taxonomy

Reuse a configured client so connections are pooled; close it with a context manager or application lifespan. Separate errors into transport (DNS/connect/TLS/timeout), HTTP status, content decoding, and schema/domain validation because callers may recover differently.

```python
timeout = httpx.Timeout(connect=2.0, read=5.0, write=5.0, pool=1.0)
with httpx.Client(timeout=timeout, base_url=base_url,
                  headers={"Authorization": f"Bearer {token}"}) as client:
    event = fetch_event(client, "", "e-1")
```

A timeout on each attempt is not a total deadline: five retries can multiply user-visible latency. Combine per-operation timeout, maximum attempts, and a monotonic overall deadline. Retry only status codes and exceptions defined by policy; 400/401/403 usually require caller action, not repetition.

Validate content type and optionally size before parsing. Treat even a 2xx response as invalid until its schema is checked. Store only redacted diagnostic context—URLs may contain secrets in query parameters.

### Test without the network

Use an injected client/transport and deterministic clock/sleeper. Tests should cover valid data, every error layer, 429 `Retry-After`, a 5xx-then-success sequence, invalid JSON, schema drift, pagination cycles, and token redaction.

### Project

Write a typed API adapter with injected client, auth header, timeouts, bounded retries, cursor pagination, metrics, and mocked transport tests.

---

## Chapter 29 — Building APIs

FastAPI uses type annotations/Pydantic for validation and OpenAPI. Keep handlers thin; domain and repository code must be testable without HTTP.

```python
from typing import Annotated
from fastapi import Depends, FastAPI, HTTPException, Query, status
from pydantic import BaseModel, Field

app = FastAPI(title="Atlas API", version="1.0.0")

class EventCreate(BaseModel):
    source: str = Field(min_length=1, max_length=64)
    external_id: str = Field(min_length=1, max_length=128)
    value: float

@app.post("/events", status_code=status.HTTP_201_CREATED)
def create_event(payload: EventCreate, service=Depends(get_service)):
    try:
        return service.create(payload)
    except DuplicateEvent as exc:
        raise HTTPException(409, "event already exists") from exc

@app.get("/events")
def list_events(limit: Annotated[int, Query(ge=1, le=100)] = 50,
                cursor: str | None = None, service=Depends(get_service)):
    return service.list(limit=limit, cursor=cursor)
```

Use correct status codes, stable error shapes, response models, cursor pagination, authorization per resource, rate/body limits, and database uniqueness. Passwords require a modern password hasher; tokens require signature/issuer/audience/expiry validation and rotation. CORS is browser policy, not authentication. Sync database drivers belong in sync handlers/thread pools; async handlers must not block the event loop. Test OpenAPI contract, validation, authentication, conflicts, not-found, pagination, and failure mapping.

### Input and output are different models

Creation input omits server-owned fields; update input distinguishes “missing” from explicit `null`; response models prevent accidental leakage. Domain models protect business invariants; Pydantic models protect transport shape. Do not pass raw request dictionaries directly into database updates.

### Stable error mapping

```python
from fastapi import Request
from fastapi.responses import JSONResponse

@app.exception_handler(DuplicateEvent)
async def duplicate_handler(request: Request, exc: DuplicateEvent):
    return JSONResponse(
        status_code=409,
        content={"error": {"code": "event_exists", "message": "event already exists",
                           "request_id": request.state.request_id}},
    )
```

Expected failures become stable public codes. Unexpected failures are logged with internal context and return a generic 500 response. Never expose stack traces or database messages to clients.

### Lifespan, dependencies, and testing

Create shared clients/pools during application lifespan and close them on shutdown. Dependency injection makes authorization and repositories replaceable in tests. Test through the ASGI application for serialization/middleware behavior, and separately test services without HTTP. An API is not complete until its OpenAPI output, compatibility policy, authentication failures, tenant isolation, concurrency conflicts, and operational endpoints are verified.

### Project

Build Atlas CRUD/search/statistics endpoints, API-key or OAuth2 authentication, request IDs, structured logs, health/readiness, metrics, and pytest integration tests.

---

## Chapter 30 — Conclusion and Integration

The first thirty chapters form a complete application path: language → validated domain model → durable files/package → data acquisition/analysis → database → API. Integration is where hidden contracts appear.

### Integration checklist

- One canonical Event model and explicit conversions at boundaries.
- UTC-aware time, Unicode/encoding policy, stable IDs and duplicate policy.
- Dependency direction: HTTP/CLI/database adapters depend on domain services.
- Bounded network/file/database operations and contextual errors.
- Tests from unit through installed-package/API/database integration.
- Configuration separated from secrets; logs contain no credentials/private payloads.
- Schema/API/package versions and migrations documented.

### Milestone

Run authorized scraping/import, validate and deduplicate records, persist them, produce a Pandas report, expose results through FastAPI, and reconstruct the environment from `pyproject.toml` plus deployment configuration.

---

# Part II — Professional Python

## Chapter 31 — Iterators, Generators, and Lazy Pipelines

An iterable can produce an iterator; an iterator maintains traversal state and returns values from `__next__` until `StopIteration`. Generators implement this protocol with suspended frames.

```python
from collections.abc import Iterable, Iterator

def batched(items: Iterable[object], size: int) -> Iterator[list[object]]:
    if size < 1:
        raise ValueError("size must be positive")
    batch = []
    for item in items:
        batch.append(item)
        if len(batch) == size:
            yield batch
            batch = []
    if batch:
        yield batch
```

Lazy pipelines bound memory and support infinite streams, but are one-pass and retain resources/state until exhausted or closed. `yield from` delegates; `itertools` provides efficient composition. Do not return a generator tied to a file already closed by its context manager. Add cancellation/cleanup with `try/finally` where generator lifetime owns resources.

**Project:** stream multi-gigabyte JSONL in validated batches without loading the whole file.

---

## Chapter 32 — Decorators, Closures, Context Managers, and Descriptors

Closures capture lexical names; decorators transform definitions; context managers delimit acquire/use/release; descriptors control attribute access.

```python
from contextlib import contextmanager

@contextmanager
def transaction(repository):
    tx = repository.begin()
    try:
        yield tx
    except BaseException:
        tx.rollback()
        raise
    else:
        tx.commit()
```

Class context managers implement `__enter__`/`__exit__`; async versions implement `__aenter__`/`__aexit__`. `property`, functions/method binding, `classmethod`, and many ORM fields use the descriptor protocol (`__get__`, `__set__`, `__set_name__`). Descriptors belong on the class; data descriptors outrank instance dictionaries. Use these mechanisms to enforce clear lifecycle/API behavior, not metaprogramming spectacle.

**Project:** add transaction, timing, retry, and authorization boundaries with preserved metadata and tests proving cleanup.

---

## Chapter 33 — Type Hints, Generics, and Protocols

Annotations aid static tools/documentation and normally do not enforce runtime values. Run a type checker in CI.

```python
from collections.abc import Iterable
from typing import Protocol, TypeVar

T = TypeVar("T")

class Repository(Protocol[T]):
    def add(self, item: T) -> T: ...
    def get(self, item_id: str) -> T | None: ...

def first(items: Iterable[T]) -> T | None:
    return next(iter(items), None)
```

Use `TypedDict` for typed mapping shapes, dataclass/Pydantic for runtime objects, `Literal` for closed literal choices, `NewType`/small classes for distinct IDs, `Self` for fluent returns, overloads only when return type truly depends on call shape. Protocols express structural behavior and reduce inheritance coupling. Avoid `Any`; it turns checking off. Narrow unions through `isinstance`, `is None`, matches, or type guards.

**Project:** type the public Atlas API under strict mypy/Pyright, with repository/service protocols and no unjustified `Any`.

---

## Chapter 34 — Testing, Property Testing, and Fuzzing

Test observable contracts, not implementation trivia. Arrange → act → assert; keep tests deterministic and independent.

```python
import pytest

@pytest.mark.parametrize(("raw", "expected"), [("0", 0), ("42", 42)])
def test_parse_count(raw, expected):
    assert parse_count(raw) == expected

def test_negative_rejected():
    with pytest.raises(InvalidRecordError, match="negative"):
        parse_count("-1")
```

Fixtures manage resources; monkeypatch/mock external boundaries, not your own domain logic. Hypothesis generates/shrinks cases and checks invariants such as encode/decode round trips. Coverage identifies unexecuted code, not assertion quality. Fuzz parsers with bounded inputs and retain every failure as a regression. Integration tests cover real serialization/database/HTTP contracts; contract tests cover external consumers.

**Project:** unit, property, integration and API suites; test timeouts, malformed Unicode, duplicate races, migrations, and installed package.

---

## Chapter 35 — Debugging, Logging, and Observability

Reproduce and preserve input/version/config before editing. Use `breakpoint()`, `python -m pdb`, post-mortem debugging, minimal cases, and regression tests. Profile rather than guessing.

```python
import logging

logger = logging.getLogger(__name__)
logger.info("event accepted", extra={"event_id": event.id, "source": event.source})
```

Configure logging once at the application boundary. Use levels consistently, parameterized messages, structured fields, request/correlation IDs, and redaction. Logs explain discrete events; metrics aggregate rates/latency/errors/saturation; traces connect distributed work. Health says the process lives, readiness says it can serve, and neither replaces functional monitoring. Never log secrets, authorization headers, passwords, or uncontrolled full payloads.

**Project:** JSON logs, request IDs, RED metrics, startup/version metadata, error-chain reporting, and an incident runbook.

---

## Chapter 36 — Concurrency, Multiprocessing, and the GIL

Threads share memory and suit blocking I/O; processes isolate memory and enable CPU parallelism with serialization/IPC cost. The GIL behavior depends on CPython build/version and does not make compound operations or external state race-free. Write synchronization-correct code rather than relying on incidental atomicity.

```python
from concurrent.futures import ThreadPoolExecutor, as_completed

with ThreadPoolExecutor(max_workers=8) as pool:
    futures = [pool.submit(fetch, url) for url in urls]
    for future in as_completed(futures):
        consume(future.result())
```

Bound queues/workers, time out blocking operations, propagate exceptions, make cancellation cooperative, and define shutdown. Use locks for shared invariants, queues for ownership transfer, and process pools for sufficiently large picklable CPU tasks. Protect multiprocessing entry with `if __name__ == "__main__"` for spawn platforms.

**Project:** bounded concurrent fetch with per-host limits and a process-pool analysis stage; compare throughput and failure semantics.

---

## Chapter 37 — Async Python and Structured Cancellation

`asyncio` runs cooperative tasks on an event loop. `await` yields only at await points; blocking CPU/synchronous I/O freezes all tasks.

```python
import asyncio
import httpx

async def fetch_all(urls: list[str]) -> list[str]:
    limits = asyncio.Semaphore(10)
    async with httpx.AsyncClient(timeout=5.0) as client:
        async def one(url: str) -> str:
            async with limits:
                response = await client.get(url)
                response.raise_for_status()
                return response.text
        async with asyncio.TaskGroup() as group:
            tasks = [group.create_task(one(url)) for url in urls]
        return [task.result() for task in tasks]
```

Task groups provide scoped lifetime and aggregate failures. Cancellation is normal control flow: clean up in `finally`, do not swallow `CancelledError`, and place deadlines with `asyncio.timeout`. Use `to_thread` for limited blocking calls and processes for CPU work. Apply backpressure through bounded queues/semaphores.

**Project:** async ingestion with graceful shutdown, deadlines, bounded concurrency and failure/cancellation tests.

---

## Chapter 38 — Security and Hostile Input

Threat-model assets, trust boundaries, attackers, entry points and abuse cases. Validate type, length, range, count, nesting, encoding and total resource budgets before expensive work.

- Never use `eval`/`exec`, unsafe pickle/YAML loaders, or shell interpolation on untrusted data.
- Use `subprocess.run([program, arg], shell=False, check=True, timeout=...)`.
- Parameterize SQL/NoSQL queries and allowlist selectable field/operator names.
- Prevent path traversal with trusted-directory operations and authorization—not string prefix alone.
- Hash passwords with Argon2id/bcrypt/scrypt through maintained libraries; never encrypt/store plaintext passwords.
- Store secrets in a secret system/environment with rotation and least privilege.
- Validate token signature, algorithm, issuer, audience, expiry and authorization.
- Bound uploads, decompression, regex, pagination, concurrency, retries and logs.
- Pin/review dependencies, scan vulnerabilities, produce an SBOM, and plan incident response.

**Project:** write Atlas's threat model and abuse tests; add resource limits, authorization, secure headers, secret redaction and dependency policy.

---

## Chapter 39 — Performance, Memory, and Profiling

Choose the right algorithm/data structure, then measure end to end. Use `timeit` for controlled microbenchmarks, `cProfile`/`pstats` for call cost, sampling profilers for realistic workloads, `tracemalloc` for Python allocations, and database/HTTP telemetry for external bottlenecks.

```python
import tracemalloc
tracemalloc.start()
before = tracemalloc.take_snapshot()
run_workload()
after = tracemalloc.take_snapshot()
for stat in after.compare_to(before, "lineno")[:10]:
    print(stat)
```

Generators reduce peak memory; vectorization moves loops to optimized native kernels; batching amortizes I/O; caching trades memory/staleness/complexity for repeated work. `__slots__` helps many small objects only after measurement. Benchmark correctness, warm-up, realistic data, variance, environment and complexity cost. A faster wrong answer is not an optimization.

**Project:** performance dossier with baseline, profile, hypothesis, change, correctness tests, raw results, memory/latency percentiles and rollback.

---

## Chapter 40 — Production Project Architecture and CLI Design

```text
atlas/
├── pyproject.toml
├── src/atlas/{domain,services,ports,adapters,api,cli}.py
├── tests/{unit,integration,contract}/
├── migrations/
└── docs/
```

Domain policy owns interfaces; adapters implement database/HTTP/filesystem details. Inject clock, repository and client dependencies. Configuration is validated once at startup. CLI commands use `argparse` (or a chosen framework), return documented exit codes, write data to stdout and diagnostics to stderr, support `--help`/`--version`, and do not prompt in automation unless requested.

```python
def main(argv: list[str] | None = None) -> int:
    args = build_parser().parse_args(argv)
    try:
        return dispatch(args)
    except AtlasError as exc:
        logger.error("%s", exc)
        return 2
```

**Project:** refactor Atlas to inward dependencies and test CLI behavior without subprocess where possible, plus end-to-end installed executable tests.

---

## Chapter 41 — Packaging, CI, and Reproducible Delivery

Build source distributions/wheels from declared metadata; test the wheel, not only the checkout.

```bash
python -m build
python -m twine check dist/*
python -m venv /tmp/atlas-check
/tmp/atlas-check/bin/python -m pip install dist/*.whl
/tmp/atlas-check/bin/atlas --version
```

CI matrix: supported Python/OS, Ruff format/lint, strict types, unit/integration tests, coverage threshold as signal, security/dependency checks, package build, install-consumer smoke, and artifact provenance. Pin CI actions/images, minimize token permissions, keep publishing behind protected trusted events and use trusted publishing rather than long-lived repository tokens. Semantic versioning must consider API, behavior, CLI, schema and data migrations.

**Project:** release a signed/versioned wheel and source archive with changelog, licenses, SBOM, hashes, migration notes and reproducible clean-environment verification.

---

## Chapter 42 — Deployment and Operations

Run ASGI behind a production process/server and trusted reverse proxy/load balancer as appropriate. Containers package userspace but do not replace application security.

- Run as non-root with a read-only filesystem where possible.
- Separate config/secrets; validate on startup and fail fast.
- Set request/body/timeouts, worker/concurrency/memory limits and graceful shutdown.
- Use readiness/liveness/startup probes correctly.
- Apply database migrations as a controlled compatible rollout.
- Back up and restore-test MongoDB/data; define RPO/RTO.
- Use rolling/canary release, observability, alerting and rollback.
- Scale only after finding bottlenecks; workers multiply connections/memory.

**Project:** deploy Atlas locally in containers with a pinned image, non-root user, health/readiness, persistent database, migration job, graceful SIGTERM, metrics and a tested rollback/restore runbook.

---

# Part III — Deep Reference and Production Mastery

## Chapter 43 — The Python Object Model and Memory

> **Level:** Advanced → Expert · **Prerequisites:** Chapters 2, 11, 21, 39

### Names, identity, type, and value

Every Python object has an identity, a type, and a value. A variable is a name bound in a namespace; assignment changes bindings. Function calls create frames containing local namespaces and references to arguments.

```python
def mutate_and_rebind(items: list[int]) -> None:
    items.append(3)          # mutates caller-visible object
    items = [99]             # rebinds only this local name

original = [1, 2]
mutate_and_rebind(original)
assert original == [1, 2, 3]
```

CPython primarily reclaims objects through reference counting and uses a cyclic garbage collector for certain reference cycles. This is an implementation fact, not a language promise that cleanup always occurs at the last reference. Resource lifetime must be explicit through context managers.

```python
import sys
obj = []
baseline = sys.getrefcount(obj)  # includes temporary reference used by the call
```

Do not build correctness around exact reference counts. `weakref` observes an object without keeping it alive and supports caches/callbacks, but many built-in objects are not weak-referenceable.

### Mutability and hashing

Hashable objects need a hash stable while stored and equality compatible with hashing: if `a == b`, then `hash(a) == hash(b)`. Immutable does not automatically mean hashable (`tuple` containing a list is not), and user classes are hashable by identity unless equality changes the default contract.

```python
from dataclasses import dataclass

@dataclass(frozen=True)
class EventKey:
    source: str
    external_id: str
```

### Scope, frames, and closures

LEGB lookup is lexical. Assignment makes a name local at compile time unless declared `nonlocal`/`global`; this explains `UnboundLocalError`.

```python
def counters():
    accepted = 0
    def accept() -> int:
        nonlocal accepted
        accepted += 1
        return accepted
    return accept
```

Closures capture variables, not frozen values. Lambdas created in a loop therefore see the final loop variable unless bound through a default or helper.

```python
funcs = [lambda i=i: i for i in range(3)]
assert [f() for f in funcs] == [0, 1, 2]
```

### Copying, serialization, and object lifetime

Shallow copy duplicates one container but shares nested objects. Deep copy recursively follows its protocol and can be expensive, duplicate unwanted state, or fail on external resources. Prefer domain-specific copying/construction. Serialization creates a representation, not a universal clone.

### Memory diagnosis

Use `sys.getsizeof` only for an object's direct footprint, `tracemalloc` for Python allocation traces, process RSS for total resident memory, and domain metrics for cache/batch sizes. Native extensions may allocate outside tracemalloc. Memory “leaks” may be live caches, reference cycles, allocator arenas, native allocations, or fragmentation.

### Self-check

1. Why can `del name` leave the object alive? Other references still exist.
2. Why is `is` unreliable for integers/strings? Interning is an implementation optimization; identity is not value semantics.
3. Why does context management matter under reference counting? Deterministic language-level cleanup must not depend on implementation/finalizer timing.

### Project

Draw Atlas's reference graph for one ingestion batch, audit every mutable default/cache/view, measure allocations with tracemalloc, and replace one accidental shared structure with an explicit immutable value.

---

## Chapter 44 — Built-in Types and Standard Library Mastery

### Numbers

`int` has arbitrary precision but operations grow with digit count. `float` is usually IEEE-754 binary64. `Decimal` supports decimal contexts/traps/rounding; construct from strings. `Fraction` preserves rational values but numerator/denominator can grow.

```python
from decimal import Decimal, localcontext, ROUND_HALF_EVEN

with localcontext() as ctx:
    ctx.prec = 28
    total = (Decimal("19.95") * 3).quantize(Decimal("0.01"), rounding=ROUND_HALF_EVEN)
```

Booleans subclass integers, so validate them separately where `1` and `True` have different meanings.

### String and bytes toolbox

Know `strip`, `split`, `rsplit`, `splitlines`, `partition`, `join`, `replace`, prefix/suffix operations, classification, search/index, alignment, formatting, encode/decode. `str.find` returns `-1`; `str.index` raises. `bytes` methods often mirror text but operate on integer octets. Use `bytearray` for mutable byte buffers and `memoryview` for zero-copy views with strict owner lifetime.

### Collection selection

| Operation | `list` | `deque` | `set`/`dict` |
|---|---:|---:|---:|
| append right | amortized O(1) | O(1) | average O(1) insert |
| pop right | O(1) | O(1) | — |
| insert/pop left | O(n) | O(1) | — |
| membership | O(n) | O(n) | average O(1) |
| index | O(1) | O(n) middle | key lookup average O(1) |

`heapq` implements a min-heap for priority queues/top-k; `bisect` searches/inserts sorted lists (insertion remains O(n)); `Counter` counts; `defaultdict` constructs missing buckets; `ChainMap` provides layered lookup without merging; `OrderedDict` retains specialized reordering/equality behavior beyond normal ordered dicts.

```python
from collections import deque
from heapq import heappush, heappop

queue = deque(maxlen=1000)
heap: list[tuple[float, str]] = []
heappush(heap, (3.5, "event-7"))
priority, event_id = heappop(heap)
```

### Essential standard-library map

- `pathlib`, `shutil`, `tempfile`: paths, copies/trees, safe temporary resources.
- `json`, `csv`, `tomllib`, `sqlite3`: structured data/config/local relational storage.
- `collections`, `itertools`, `functools`, `operator`: data-flow building blocks.
- `datetime`, `zoneinfo`, `time`: civil time, zones, monotonic clocks.
- `subprocess`, `signal`, `os`, `sys`: process/system boundaries.
- `logging`, `argparse`, `configparser`: applications and operations.
- `hashlib`, `hmac`, `secrets`: hashes/MACs/secure random tokens—not password hashing.
- `concurrent.futures`, `threading`, `multiprocessing`, `asyncio`: concurrency models.
- `unittest.mock`, `doctest`, `pdb`, `profile`: verification/diagnosis.

### Project

Implement a bounded queue, priority retry schedule, layered configuration, safe temp output and cryptographically random request ID using the appropriate standard types. Justify each selection and complexity.

---

## Chapter 45 — Iterator, Generator, and Coroutine Protocols

### Protocol mechanics

`iter(obj)` calls `obj.__iter__()` or sequence fallback. `next(iterator)` calls `__next__`; exhaustion raises `StopIteration`. An iterator returns itself from `__iter__`; an iterable may create fresh iterators.

```python
class Countdown:
    def __init__(self, start: int):
        self.current = start
    def __iter__(self):
        return self
    def __next__(self) -> int:
        if self.current <= 0:
            raise StopIteration
        value = self.current
        self.current -= 1
        return value
```

Generators package that state automatically. `yield from subiterator` delegates values plus `send`, `throw`, `close`, and return-value propagation. Sending a non-`None` value into a just-started generator is invalid.

```python
def running_average():
    total = 0.0
    count = 0
    value = yield None
    while True:
        total += value
        count += 1
        value = yield total / count
```

`close()` injects `GeneratorExit`; cleanup belongs in `finally`. Do not yield while handling `GeneratorExit`. Generator expressions evaluate the outer iterable immediately but consume lazily.

### Async protocols

`async def` returns a coroutine object; it runs when awaited/scheduled. `async for` uses `__aiter__`/`__anext__` and stops on `StopAsyncIteration`. Async generators support `aclose`. Async context managers delimit asynchronous acquisition/cleanup.

```python
async def stream_pages(client, url):
    while url is not None:
        response = await client.get(url)
        response.raise_for_status()
        data = response.json()
        yield data["items"]
        url = data.get("next")
```

### Pipeline design

Define ownership: who closes file/client/generator, whether items can be replayed, how exceptions/cancellation propagate, and where buffering/backpressure occurs. Laziness moves failures from construction to consumption; document that timing.

### Project

Build sync and async Atlas page streams with deduplication, max-page/max-item limits, cancellation cleanup, test doubles, and explicit replay semantics.

---

## Chapter 46 — Attribute Access, Descriptors, and Metaclasses

Attribute lookup roughly considers data descriptors on the class/MRO, instance dictionary, non-data descriptors/class attributes, then `__getattr__`. `__getattribute__` intercepts every lookup and must delegate carefully to avoid recursion.

```python
class Positive:
    def __set_name__(self, owner, name):
        self.storage_name = f"_{name}"
    def __get__(self, instance, owner=None):
        if instance is None:
            return self
        return getattr(instance, self.storage_name)
    def __set__(self, instance, value):
        if value <= 0:
            raise ValueError("must be positive")
        setattr(instance, self.storage_name, value)

class Batch:
    size = Positive()
    def __init__(self, size):
        self.size = size
```

A descriptor defining `__set__`/`__delete__` is a data descriptor and outranks instance attributes. Functions are non-data descriptors that bind methods. `property`, ORM columns and validators build on this protocol.

### Class creation and metaclasses

Calling a class invokes its metaclass (`type` normally): `__call__` coordinates `__new__` and `__init__`. `__init_subclass__` and class decorators solve many registration/validation needs more simply than custom metaclasses.

```python
class Adapter:
    registry: dict[str, type["Adapter"]] = {}
    def __init_subclass__(cls, *, kind: str, **kwargs):
        super().__init_subclass__(**kwargs)
        if kind in cls.registry:
            raise TypeError(f"duplicate adapter kind {kind}")
        cls.registry[kind] = cls
```

Metaclasses can enforce/transform class creation but interact through the most-derived common metaclass and create conflict/comprehension costs. Use only when the behavior truly concerns classes as objects and simpler protocols cannot express it.

### Project

Implement a descriptor-backed configuration model and adapter registry, then compare it with dataclasses/Pydantic and document when framework machinery is preferable.

---

## Chapter 47 — Advanced Static Typing

### Type parameters and variance

Mutable containers are normally invariant: accepting `list[Dog]` as `list[Animal]` would allow inserting a Cat. Read-only producer protocols can be covariant; consumers can be contravariant. Prefer abstract `Sequence[T]`/`Iterable[T]` for read-only inputs and concrete mutable types only when mutation is required.

```python
from collections.abc import Sequence
from typing import TypeGuard

def all_strings(values: list[object]) -> TypeGuard[list[str]]:
    return all(isinstance(v, str) for v in values)

def join_names(names: Sequence[str]) -> str:
    return ", ".join(names)
```

### Typed structures and callable APIs

Use `TypedDict` for dictionaries with known keys, `Protocol` for structural behavior, `ParamSpec` for decorators preserving callable parameters, `TypeVar` for relationships, and overloads for call-dependent return types.

```python
from collections.abc import Callable
from typing import ParamSpec, TypeVar

P = ParamSpec("P")
R = TypeVar("R")

def traced(func: Callable[P, R]) -> Callable[P, R]:
    def wrapper(*args: P.args, **kwargs: P.kwargs) -> R:
        logger.debug("calling %s", func.__qualname__)
        return func(*args, **kwargs)
    return wrapper
```

Use `cast` only to communicate a fact the checker cannot prove—it performs no runtime conversion. `assert_never` checks exhaustive unions/matches. Stubs (`.pyi`) describe untyped/runtime-generated APIs. Type-checking configuration, checker/version, plugins and ignored errors are part of the build contract.

### Runtime boundaries

Annotations do not validate JSON. Parse external data with explicit runtime models, then pass typed domain values inward. Keep ORM/API models from becoming the universal domain object. A strict internal core plus validated adapters produces more value than annotating every dynamic integration with `Any`.

### Project

Achieve strict checking for Atlas core, write generic repository/service protocols, preserve decorator signatures, exhaustively handle result variants, and publish a `py.typed` marker for consumers.

---

## Chapter 48 — Testing Architecture and Quality Engineering

### Test portfolio

Unit tests isolate pure policy; component tests exercise a real adapter with controlled dependencies; integration tests verify database/network/filesystem contracts; contract tests protect provider/consumer schemas; end-to-end tests verify a few critical user journeys. The testing pyramid is a cost/feedback model, not a mandated shape.

Fixtures should have narrow scope and explicit cleanup. Factories/builders reduce irrelevant setup. Patch where a name is looked up, not where originally defined. Prefer dependency injection/fake ports over deep mock chains.

```python
@pytest.fixture
def event_factory():
    def build(**changes):
        values = {"source": "alpha", "external_id": "1", "value": 3.5}
        values.update(changes)
        return Event(**values)
    return build

def test_service_rejects_duplicate(event_factory):
    repo = InMemoryRepository([event_factory()])
    service = EventService(repo=repo, clock=FixedClock())
    with pytest.raises(DuplicateEvent):
        service.create(event_factory())
```

### Property and stateful testing

Good properties include round-trip, idempotence, invariants, monotonicity, permutation independence and equivalence to a simple oracle. Constrain generators to both valid and deliberately invalid domain regions. Stateful testing models sequences such as create/update/delete and checks a reference model.

### Time, randomness, concurrency, and external systems

Inject clocks/RNGs; do not sleep in tests. Coordinate threads/tasks with events/barriers and bounded deadlines. Use temporary directories and isolated databases. Record/replay HTTP fixtures carefully—sanitize secrets and avoid petrifying accidental behavior. Test migrations forward and, where promised, rollback/compatibility.

### Mutation, coverage, and CI

Branch coverage and mutation testing reveal gaps but are metrics, not goals. Flaky tests are defects: quarantine only with owner/deadline, preserve evidence, repair nondeterminism. Parallel tests must not share ports, files, users or database names. Separate quick per-change suite from scheduled expensive/fuzz/load suites.

### Project

Create Atlas's test matrix mapping every public contract and threat to unit/property/integration/contract/E2E coverage. Add factories, fake clock/repository, Mongo/FastAPI integration, Hypothesis round trips, mutation review and a no-flake policy.

---

## Chapter 49 — Threads, Processes, IPC, and Synchronization

### Threads and shared-state invariants

Locks protect invariants, not lines. A condition variable waits for a predicate while releasing/reacquiring its lock; always loop because wakeups/state changes race.

```python
from collections import deque
from threading import Condition

class BoundedQueue:
    def __init__(self, capacity: int):
        self._capacity = capacity
        self._items = deque()
        self._closed = False
        self._changed = Condition()
    def put(self, item):
        with self._changed:
            self._changed.wait_for(lambda: len(self._items) < self._capacity or self._closed)
            if self._closed:
                raise RuntimeError("queue closed")
            self._items.append(item)
            self._changed.notify_all()
```

Production code must add timeout/cancellation and `get`/`close` semantics. `Lock` is non-reentrant; `RLock` can mask tangled ownership. Semaphores bound permits; barriers coordinate phases; thread-local/context variables scope state but can hide dependencies.

### Processes and IPC

Process pools serialize arguments/results. Large objects pay copying/pickling cost; globals initialized before fork behave differently from spawn and may hold unsafe inherited locks/connections. Create database/network clients inside the child lifecycle. Use queues/pipes/shared memory deliberately; define message schema, ownership, shutdown and child-crash detection.

`multiprocessing.shared_memory` avoids copies but requires explicit shape/dtype synchronization and unlink cleanup. Managers are convenient proxies with significant IPC overhead. Never unpickle messages from untrusted peers.

### GIL and free-threading awareness

Traditional CPython builds allow one thread at a time to execute Python bytecode while many extensions release the GIL. Newer CPython supports evolving free-threaded configurations, but libraries and synchronization semantics must be verified for that build. Data races, lost updates and external-resource races exist regardless. Do not rely on “looks atomic” bytecode operations as API guarantees.

### Project

Build bounded thread ingestion and process-based CPU analysis. Test overload, worker exception, parent cancellation, child crash, SIGTERM, queue closure and exact-once/at-least-once semantics. Benchmark serialization versus compute.

---

## Chapter 50 — Asyncio Internals and Reliable Async Systems

### Event-loop model

The loop polls I/O/timers and runs ready callbacks/tasks until their next suspension. A coroutine object is inert until awaited/scheduled. A Task drives a coroutine and stores result/exception. Creating an orphan task loses lifetime/error ownership.

```python
async def worker(queue: asyncio.Queue[Event]) -> None:
    while True:
        event = await queue.get()
        try:
            await persist(event)
        finally:
            queue.task_done()
```

Sentinels, cancellation, or queue shutdown policy must terminate workers; the infinite sketch alone is incomplete. Queue `maxsize` provides backpressure. `TaskGroup` owns children and cancels siblings on failure, producing exception groups.

### Deadlines, cancellation, and cleanup

Timeout every remote phase and propagate one end-to-end deadline rather than multiplying independent full timeouts. Cancellation arrives at await points. Catch only to clean up and re-raise. Shielding prevents caller cancellation from reaching work and should be narrow (for a must-finish commit/cleanup) with its own deadline.

### Async synchronization and context

Async locks protect task-level invariants but do not make blocking/thread access safe. Events signal state; Conditions combine predicate+lock; Semaphores bound concurrency. `contextvars` propagates request context across tasks better than thread-local state, but explicitly passing dependencies remains clearest.

### Streams and graceful service lifecycle

TCP is a byte stream: frame messages, handle partial operations, set maximum frame/body sizes, drain bounded writes, and authenticate/encrypt. On shutdown: stop accepting, signal producers, drain or persist queue per policy, cancel bounded leftovers, close clients/pools, flush observability, exit before orchestrator kill deadline.

### Project

Implement Atlas async supervisor using TaskGroup, bounded queues, per-host semaphores, propagated deadlines, retry budget, graceful SIGTERM, context request IDs and tests proving no leaked tasks.

---

## Chapter 51 — Numerical Python and Statistical Engineering

### Array semantics

An ndarray has data buffer, dtype, shape, strides and flags. Reshape/transposes/slices can be views; advanced indexing usually copies. `np.shares_memory` helps diagnose aliasing. Contiguous memory/layout affects native-kernel performance.

```python
x = np.arange(12, dtype=np.float64).reshape(3, 4)
column = x[:, 1]              # strided view
selected = x[x > 5]           # copy
```

Broadcasting compares trailing dimensions: equal or one expands conceptually. Use `einsum`, matrix multiplication and ufunc `out=` only after checking shapes and memory cost. Never use `np.vectorize` expecting native vectorization—it is convenience looping.

### Numerical reliability

Check dtype before arithmetic; integer overflow wraps according to dtype, while Python ints grow. Avoid subtractive cancellation and naive sums for ill-conditioned data; use stable algorithms/libraries. `allclose` needs domain tolerances and handles NaNs only by explicit policy. Linear algebra should solve systems/decompose rather than explicitly invert; inspect residual and condition number.

### Statistical workflow

Define estimand and sampling design; separate exploratory from confirmatory analysis; visualize distributions/missingness; report effect size and uncertainty; account for multiple comparisons; validate model assumptions; avoid leakage between train/test/time. Seeds enable replay but do not repair biased sampling.

### Reproducible randomness

Use `Generator`, derive independent streams through `SeedSequence`, record seed/algorithm/version, and do not share a mutable generator unsafely across workers. Distributed simulations need stable stream identities independent of scheduling.

### Project

Build a statistically documented Atlas anomaly report with missing/outlier policy, robust summaries, bootstrap intervals, stable RNG streams, numerical tests against an oracle, and provenance manifest.

---

## Chapter 52 — Production Pandas and Data Pipelines

### Schema-first ingestion

Specify column names, dtypes, dates, categorical domains, nullability, units and uniqueness at the boundary. CSV inference is convenient exploration, not a durable contract. Validate after reading and before transformations.

```python
def validate_events(df: pd.DataFrame) -> pd.DataFrame:
    required = {"source", "external_id", "value", "observed_at"}
    missing = required - set(df.columns)
    if missing:
        raise ValueError(f"missing columns: {sorted(missing)}")
    if df[["source", "external_id"]].duplicated().any():
        raise ValueError("duplicate event key")
    if df["value"].isna().any():
        raise ValueError("value cannot be null")
    return df
```

### Index, alignment, and mutation

Arithmetic aligns labels. Reset/align deliberately before positional comparison. `.loc[row, column]` performs explicit assignment; chained selection may operate on a copy/view under evolving copy-on-write behavior. Treat intermediate DataFrames as values and keep transformation functions side-effect-free.

### Joins and grouping

State expected key cardinality and enforce with `validate`. Inspect unmatched keys using merge indicators. Avoid accidental many-to-many explosion. `groupby` splits/applies/combines; named aggregation makes outputs stable. Window/resample operations require sorted, timezone-aware time and boundary/closed-label policy.

### Scale and pipeline design

Use appropriate dtypes, project/filter early, Parquet/Arrow for typed columnar data, categorical encoding for repeated labels, database query pushdown, chunks for associative streaming calculations, and Dask/Polars/Spark only when workload/operations justify them. Pandas object dtype often hides Python objects and memory cost.

### Project

Create a typed raw→validated→curated→report pipeline with immutable inputs, quality metrics, join audits, timezone policy, partitioned Parquet, incremental/idempotent rebuild and golden/property tests.

---

## Chapter 53 — Production MongoDB

### Modeling and indexes

Start from bounded documents and query/update patterns. Embed values read/updated atomically with parent; reference independently growing/shared entities. Avoid unbounded arrays/documents and polymorphic chaos without discriminators/versioning.

Indexes accelerate selected reads/sorts and uniqueness but cost memory/write amplification. Compound index prefix/order matters; equality fields commonly precede sort/range according to actual plan. Partial, sparse, TTL, text and wildcard indexes solve specific problems. Inspect `explain("executionStats")`, returned/examined counts, sort stages and index size.

### Writes and concurrency

Use atomic update operators and conditional filters for optimistic concurrency:

```python
result = events.update_one(
    {"_id": event_id, "version": expected_version},
    {"$set": changes, "$inc": {"version": 1}},
)
if result.matched_count == 0:
    raise ConcurrentModification(event_id)
```

Choose write concern, read concern and read preference based on durability/consistency. Retrying writes can be supported by driver/server semantics, but application operations still need idempotency. Transactions require sessions, short duration and error/retry handling; they do not make poor schemas cheap.

### Aggregation, pagination, and operations

Filter/project early, bound pipelines, understand `$lookup`/unwind cardinality, permit disk use deliberately, and index match/sort. Prefer range/cursor pagination on a unique stable ordering key over large `skip`. Monitor pool, operation latency, replication lag, storage/index growth and slow queries. Backups are complete only after restore testing and documented point-in-time objectives.

### Project

Create Atlas schema versions/migrations, indexes with measured plans, optimistic update, idempotent upsert, cursor pagination, aggregation, transaction only where justified, timeout/pool settings and replica-set backup/restore test.

---

## Chapter 54 — Production FastAPI

### Layered application and lifespan

Create shared clients/pools during application lifespan and close them once. Dependency functions provide request-scoped auth/session/services; they should not hide arbitrary global state. Route models are transport contracts; map them to domain commands/results.

```python
from contextlib import asynccontextmanager
from fastapi import FastAPI

@asynccontextmanager
async def lifespan(app: FastAPI):
    app.state.container = await build_container()
    try:
        yield
    finally:
        await app.state.container.close()

app = FastAPI(lifespan=lifespan)
```

### Validation, errors, and versioning

Constrain fields/body size and reject nonfinite numbers if domain forbids them. Response models prevent accidental field leaks. Publish a stable machine-readable error envelope with code/message/request ID/details policy. Separate 400 syntax/domain errors, 401 authentication, 403 authorization, 404 hidden/missing, 409 conflicts, 422 validation, 429 limits and 5xx failures. Version APIs only with a migration/deprecation policy.

### Authentication and authorization

OAuth2/JWT examples are not complete security. Validate cryptography/claims/key rotation and enforce resource/action authorization after authentication. API keys need hashing/storage/rotation/scopes. Cookies need Secure/HttpOnly/SameSite and CSRF defense. Apply tenant filters at repository boundaries and test cross-tenant access.

### Middleware, performance, and testing

Middleware order affects exception, CORS, tracing and timing. Trust proxy headers only from known proxies. Sync blocking work belongs in sync endpoints/thread pool; async drivers in async endpoints. Bound threads/connections/tasks. Test with dependency overrides and lifespan-aware clients; include OpenAPI snapshot/contract, auth, validation, concurrency, disconnect/cancellation, database failure and information leakage.

### Project

Deliver Atlas v1 with lifespan container, domain mapping, auth/scopes, cursor pagination, idempotency key, ETag/conditional update, request limits, consistent errors, OpenTelemetry/metrics and load/failure tests.

---

## Chapter 55 — Configuration, Migrations, Observability, and Operations

Configuration has schema, source precedence, type validation, secret sensitivity and reload policy. A typical precedence is defaults < config file < environment < CLI; document it. Fail startup on invalid required config and log safe effective metadata—not secrets.

Migrations are versioned programs. Use expand/migrate/contract for zero-downtime compatibility: add tolerant fields/indexes, deploy dual-compatible code, backfill idempotently with checkpoints/metrics, then remove old shape later. Back up and rehearse rollback/forward-fix.

Observability connects logs, metrics and traces through correlation IDs. Define service-level indicators/objectives and alert on user-impacting symptoms, not every internal fluctuation. RED (rate/errors/duration) and USE (utilization/saturation/errors) guide instrumentation. Control metric-label cardinality.

Operations require runbooks for dependency outage, latency, queue saturation, bad deploy, migration failure, credential rotation, data corruption and restore. Record owner, diagnosis queries, safe mitigations, escalation and verification. Practice game days.

### Project

Implement typed settings, secret redaction, schema migration with resumable backfill, logs/metrics/traces, dashboards/alerts, SLO and incident/restore/rollback runbooks.

---

## Chapter 56 — Secure Python Engineering

### Boundary checklist

For each input identify origin/trust, parser, canonical representation, validation, authorization, resource budget, storage/log policy and output encoding. Validation without authorization is insufficient; authentication without resource-level checks is insufficient.

### Injection and unsafe features

Use argument arrays for subprocess, query parameters for databases, template autoescaping for HTML, safe structured loaders, and allowlists for dynamic identifiers/operators. Avoid `eval`, `exec`, pickle from untrusted sources, unsafe YAML, dynamic imports from user names, and archive extraction without path/link/size checks.

```python
import subprocess

completed = subprocess.run(
    ["convert-tool", "--input", user_path],
    shell=False,
    check=True,
    timeout=10,
    capture_output=True,
    text=True,
    env={"PATH": "/usr/bin:/bin"},
)
```

This still needs executable trust, path/file authorization, output limits and sandboxing for hostile parsers.

### Cryptography and secrets

Use `secrets` for tokens, constant-time `hmac.compare_digest` for secret comparison, TLS verification, and maintained high-level AEAD/password-hashing libraries. Encryption needs key generation/storage/rotation/nonce policy and authenticity. Minimize secret lifetime/copies and exclude secrets from errors, logs, traces, cores and test fixtures.

### Supply chain and runtime hardening

Pin/lock reviewed direct/transitive dependencies, monitor advisories, verify provenance/hashes, minimize packages, produce SBOM/license inventory and separate build/publish permissions. Run non-root with least filesystem/network/database privileges, read-only root where possible, limits, sandbox/container policies and patched runtime. Security scanning complements threat modeling/review/fuzzing.

### Project

Perform STRIDE-style Atlas threat review, fix top risks, add malicious-input/authz/dependency tests, rotate keys without downtime, generate SBOM, and conduct an incident tabletop with evidence-preserving response.

---

## Chapter 57 — Atlas: Buildable Multi-file Capstone

> **Goal:** assemble the handbook into a small installable core/API whose domain tests run without MongoDB. Production adapters remain replaceable behind protocols.

### Repository

```text
atlas-data-platform/
├── pyproject.toml
├── src/atlas/
│   ├── __init__.py
│   ├── __main__.py
│   ├── domain.py
│   ├── ports.py
│   ├── service.py
│   ├── memory.py
│   ├── api.py
│   └── cli.py
└── tests/
    ├── test_service.py
    └── test_api.py
```

### Project metadata

```toml
[build-system]
requires = ["hatchling>=1.27"]
build-backend = "hatchling.build"

[project]
name = "atlas-data-platform"
version = "1.0.0"
requires-python = ">=3.12"
dependencies = [
  "fastapi>=0.115,<1",
  "pydantic>=2.10,<3",
  "uvicorn>=0.34,<1",
]

[project.optional-dependencies]
dev = [
  "build>=1.2,<2",
  "httpx>=0.27,<1",
  "pytest>=8,<9",
  "ruff>=0.9",
  "mypy>=1.14",
]
mongo = ["pymongo>=4.10,<5"]

[project.scripts]
atlas = "atlas.cli:main"

[tool.hatch.build.targets.wheel]
packages = ["src/atlas"]

[tool.pytest.ini_options]
testpaths = ["tests"]
addopts = "-q --strict-markers"

[tool.ruff]
line-length = 100
target-version = "py312"

[tool.mypy]
python_version = "3.12"
strict = true
packages = ["atlas"]
```

Version bounds are illustrative and must be refreshed/tested before release.

### Domain model — `domain.py`

```python
from dataclasses import dataclass
from datetime import UTC, datetime
import math


class AtlasError(Exception):
    pass


class InvalidEvent(AtlasError):
    pass


class DuplicateEvent(AtlasError):
    pass


@dataclass(frozen=True, slots=True)
class Event:
    source: str
    external_id: str
    value: float
    observed_at: datetime

    def __post_init__(self) -> None:
        source = self.source.strip().casefold()
        external_id = self.external_id.strip()
        if not source or len(source) > 64:
            raise InvalidEvent("source must contain 1..64 characters")
        if not external_id or len(external_id) > 128:
            raise InvalidEvent("external_id must contain 1..128 characters")
        if not math.isfinite(self.value):
            raise InvalidEvent("value must be finite")
        if self.observed_at.tzinfo is None:
            raise InvalidEvent("observed_at must be timezone-aware")
        object.__setattr__(self, "source", source)
        object.__setattr__(self, "external_id", external_id)
        object.__setattr__(self, "observed_at", self.observed_at.astimezone(UTC))

    @property
    def key(self) -> tuple[str, str]:
        return self.source, self.external_id
```

The frozen model normalizes once and rejects non-finite JSON-hostile floats. `object.__setattr__` is deliberately confined to post-initialization normalization.

### Port — `ports.py`

```python
from datetime import datetime
from typing import Protocol
from .domain import Event


class EventRepository(Protocol):
    def add(self, event: Event) -> Event: ...
    def get(self, source: str, external_id: str) -> Event | None: ...
    def list(self, *, limit: int, after: tuple[str, str] | None) -> list[Event]: ...


class Clock(Protocol):
    def now(self) -> datetime: ...
```

Static typing cannot express timezone awareness by itself; every concrete clock and domain boundary must enforce that runtime invariant.

### In-memory adapter — `memory.py`

```python
from threading import RLock
from .domain import DuplicateEvent, Event


class InMemoryEventRepository:
    def __init__(self) -> None:
        self._events: dict[tuple[str, str], Event] = {}
        self._lock = RLock()

    def add(self, event: Event) -> Event:
        with self._lock:
            if event.key in self._events:
                raise DuplicateEvent(f"duplicate event {event.key!r}")
            self._events[event.key] = event
            return event

    def get(self, source: str, external_id: str) -> Event | None:
        with self._lock:
            return self._events.get((source.strip().casefold(), external_id.strip()))

    def list(self, *, limit: int, after: tuple[str, str] | None) -> list[Event]:
        if not 1 <= limit <= 100:
            raise ValueError("limit must be in 1..100")
        normalized_after = None if after is None else (
            after[0].strip().casefold(), after[1].strip()
        )
        with self._lock:
            keys = sorted(self._events)
            selected = (key for key in keys if normalized_after is None or key > normalized_after)
            return [self._events[key] for key in list(selected)[:limit]]
```

The lock makes check+insert atomic inside one process. MongoDB production uniqueness must be enforced by a unique index because multiple processes exist.

### Application service — `service.py`

```python
from datetime import datetime
from .domain import Event
from .ports import EventRepository


class EventService:
    def __init__(self, repository: EventRepository) -> None:
        self._repository = repository

    def create(
        self, *, source: str, external_id: str, value: float, observed_at: datetime
    ) -> Event:
        event = Event(source, external_id, value, observed_at)
        return self._repository.add(event)

    def get(self, source: str, external_id: str) -> Event | None:
        return self._repository.get(source, external_id)

    def list(self, *, limit: int, after: tuple[str, str] | None) -> list[Event]:
        return self._repository.list(limit=limit, after=after)
```

### API adapter — `api.py`

```python
from collections.abc import AsyncIterator
from contextlib import asynccontextmanager
from datetime import datetime
from typing import cast
from fastapi import Depends, FastAPI, HTTPException, Query, Request, status
from pydantic import BaseModel, ConfigDict, Field
from .domain import DuplicateEvent, Event, InvalidEvent
from .memory import InMemoryEventRepository
from .service import EventService


class EventCreate(BaseModel):
    source: str = Field(min_length=1, max_length=64)
    external_id: str = Field(min_length=1, max_length=128)
    value: float
    observed_at: datetime


class EventView(BaseModel):
    model_config = ConfigDict(from_attributes=True)
    source: str
    external_id: str
    value: float
    observed_at: datetime


@asynccontextmanager
async def lifespan(app: FastAPI) -> AsyncIterator[None]:
    app.state.service = EventService(InMemoryEventRepository())
    try:
        yield
    finally:
        del app.state.service


app = FastAPI(title="Atlas", version="1.0.0", lifespan=lifespan)


def get_service(request: Request) -> EventService:
    return cast(EventService, request.app.state.service)


@app.post("/events", response_model=EventView, status_code=status.HTTP_201_CREATED)
def create_event(payload: EventCreate, service: EventService = Depends(get_service)) -> Event:
    try:
        return service.create(**payload.model_dump())
    except InvalidEvent as exc:
        raise HTTPException(status_code=422, detail=str(exc)) from exc
    except DuplicateEvent as exc:
        raise HTTPException(status_code=409, detail="event already exists") from exc


@app.get("/events/{source}/{external_id}", response_model=EventView)
def get_event(source: str, external_id: str,
              service: EventService = Depends(get_service)) -> Event:
    event = service.get(source, external_id)
    if event is None:
        raise HTTPException(status_code=404, detail="event not found")
    return event


@app.get("/events", response_model=list[EventView])
def list_events(limit: int = Query(50, ge=1, le=100),
                service: EventService = Depends(get_service)) -> list[Event]:
    return service.list(limit=limit, after=None)
```

Production must add authenticated cursor encoding, Mongo adapter, stable error envelope, request/body/rate limits, observability and shutdown. The minimal slice intentionally keeps those extension seams visible.

### CLI — `cli.py`, `__main__.py`

```python
# cli.py
import argparse
from .api import app


def build_parser() -> argparse.ArgumentParser:
    parser = argparse.ArgumentParser(prog="atlas")
    parser.add_argument("--version", action="version", version="%(prog)s 1.0.0")
    sub = parser.add_subparsers(dest="command", required=True)
    sub.add_parser("serve", help="serve the ASGI application")
    return parser


def main(argv: list[str] | None = None) -> int:
    args = build_parser().parse_args(argv)
    if args.command == "serve":
        import uvicorn
        uvicorn.run(app, host="127.0.0.1", port=8000)
        return 0
    return 2
```

```python
# __main__.py
from .cli import main

if __name__ == "__main__":
    raise SystemExit(main())
```

Importing Uvicorn inside the branch keeps ordinary library imports free of server startup side effects. A larger library may move it to a `server` extra; this compact application declares it directly so the installed CLI is runnable.

### Tests — `tests/test_service.py`

```python
from datetime import UTC, datetime
import pytest
from atlas.domain import DuplicateEvent
from atlas.memory import InMemoryEventRepository
from atlas.service import EventService


def test_create_normalizes_and_rejects_duplicate() -> None:
    service = EventService(InMemoryEventRepository())
    created = service.create(
        source=" Alpha ", external_id=" 7 ", value=3.5,
        observed_at=datetime(2026, 1, 1, tzinfo=UTC),
    )
    assert created.source == "alpha"
    assert created.external_id == "7"
    with pytest.raises(DuplicateEvent):
        service.create(source="ALPHA", external_id="7", value=4.0,
                       observed_at=datetime(2026, 1, 1, tzinfo=UTC))
```

### API tests — `tests/test_api.py`

These tests enter the FastAPI lifespan, so application state is initialized exactly
as it is by a real ASGI server.

```python
from fastapi.testclient import TestClient
from atlas.api import app


def test_create_get_and_duplicate() -> None:
    payload = {
        "source": " Alpha ",
        "external_id": " 7 ",
        "value": 3.5,
        "observed_at": "2026-01-01T00:00:00Z",
    }
    with TestClient(app) as client:
        created = client.post("/events", json=payload)
        assert created.status_code == 201
        assert created.json()["source"] == "alpha"

        fetched = client.get("/events/ALPHA/7")
        assert fetched.status_code == 200
        assert fetched.json()["external_id"] == "7"

        duplicate = client.post("/events", json=payload)
        assert duplicate.status_code == 409


def test_domain_validation_becomes_client_error() -> None:
    payload = {
        "source": "   ",
        "external_id": "7",
        "value": 3.5,
        "observed_at": "2026-01-01T00:00:00Z",
    }
    with TestClient(app) as client:
        response = client.post("/events", json=payload)
    assert response.status_code == 422
```

### Build and verification ladder

```bash
python -m venv .venv
. .venv/bin/activate
python -m pip install -e '.[dev]'
python -m ruff format --check .
python -m ruff check .
python -m mypy src
python -m pytest
python -m build
python -m pip install --force-reinstall dist/*.whl
atlas --version
```

Expected production refinement tasks: add property tests, Mongo adapter/index migration,
authentication and authorization, opaque cursor tokens, a stable structured error
envelope, request limits, logs/metrics/traces, async ingestion, container/CI, SBOM,
and restore/rollback evidence. Pin the checker versions used by CI and treat any new
warning as a build failure or a documented, narrowly scoped exception.

### Final defense

Explain every boundary, mutation, exception, data constraint, timeout, concurrency guarantee, index, authorization decision, metric and migration. Demonstrate a failure and recovery. That evidence—not chapter completion—is the expert outcome.

---

# Part IV — Integrated Learning Projects

These projects are not isolated syntax exercises. Each one combines earlier chapters, has staged milestones, requires tests, and leaves design decisions for the learner. Build them in order: every project adds a new boundary while retaining the engineering discipline of the previous one.

## Chapter 58 — Project 1: Personal Expense CLI

**Combines:** variables, strings, numeric policy, lists, tuples, sets, dictionaries, conditions, loops, functions, modules, comprehensions, exceptions, dates, files, and virtual environments.

### Product requirements

Build a command-line application that can add, list, filter, summarize, and delete expenses. An expense has an immutable ID, UTC creation time, date paid, normalized category, decimal amount, currency, description, and unique tags. Store data in JSON Lines so one bad line can be reported precisely.

Do not use binary floating point for money. Define whether amounts may be negative, whether categories are case-sensitive, and whether deleting an absent ID is an error or an idempotent success.

```text
expense_tracker/
├── pyproject.toml
├── src/expense_tracker/
│   ├── __init__.py
│   ├── __main__.py
│   ├── cli.py
│   ├── model.py
│   ├── service.py
│   └── storage.py
└── tests/
    ├── test_model.py
    ├── test_service.py
    └── test_storage.py
```

### Domain model and validation

```python
from dataclasses import dataclass
from datetime import UTC, date, datetime
from decimal import Decimal, InvalidOperation
from uuid import uuid4

@dataclass(frozen=True, slots=True)
class Expense:
    id: str
    paid_on: date
    amount: Decimal
    currency: str
    category: str
    description: str
    tags: frozenset[str]
    created_at: datetime

def normalize_token(value: str, *, field: str) -> str:
    normalized = value.strip().casefold()
    if not normalized:
        raise ValueError(f"{field} cannot be blank")
    return normalized

def new_expense(*, paid_on: str, amount: str, currency: str,
                category: str, description: str = "",
                tags: list[str] | None = None) -> Expense:
    try:
        parsed_amount = Decimal(amount)
    except InvalidOperation as exc:
        raise ValueError("amount must be decimal") from exc
    if not parsed_amount.is_finite() or parsed_amount <= 0:
        raise ValueError("amount must be finite and positive")
    return Expense(
        id=str(uuid4()), paid_on=date.fromisoformat(paid_on),
        amount=parsed_amount, currency=normalize_token(currency, field="currency").upper(),
        category=normalize_token(category, field="category"),
        description=description.strip(),
        tags=frozenset(normalize_token(t, field="tag") for t in tags or []),
        created_at=datetime.now(UTC),
    )
```

Notice what is combined: a list arrives at the boundary, a `frozenset` expresses unique immutable tags, strings are normalized, `Decimal` protects money semantics, a dataclass names the record, and exceptions reject invalid state.

### Atomic JSONL persistence

Serialize `Decimal`, dates, and datetimes explicitly; JSON does not understand them automatically. Write a complete temporary file, flush it, then replace the destination so interruption does not publish half a database.

```python
import json
import os
from pathlib import Path

def encode(expense: Expense) -> dict[str, object]:
    return {
        "id": expense.id, "paid_on": expense.paid_on.isoformat(),
        "amount": str(expense.amount), "currency": expense.currency,
        "category": expense.category, "description": expense.description,
        "tags": sorted(expense.tags), "created_at": expense.created_at.isoformat(),
    }

def save_all(path: Path, expenses: list[Expense]) -> None:
    temporary = path.with_suffix(path.suffix + ".tmp")
    with temporary.open("w", encoding="utf-8", newline="\n") as stream:
        for expense in expenses:
            stream.write(json.dumps(encode(expense), ensure_ascii=False) + "\n")
        stream.flush()
        os.fsync(stream.fileno())
    temporary.replace(path)
```

For production-grade durability, discuss directory `fsync`, concurrent writers, file permissions, backups, and locking. Atomic replacement prevents partial publication but does not solve every durability or concurrency problem.

### Milestones

1. Implement model validation with table-driven tests.
2. Add `add` and `list`; keep CLI parsing separate from services.
3. Add date/category/tag filters and totals by category/currency.
4. Add malformed-line errors containing path and line number.
5. Add atomic delete, stable sorting, and an export command.
6. Package it and prove installation in a clean virtual environment.

### Required tests and review questions

- Test blank Unicode input, invalid ISO dates, NaN/infinity, duplicates tags, empty files, corrupt JSON, duplicate IDs, and interrupted replacement.
- Why is `float` unsuitable? Why is a set unsuitable for preserving displayed tag order? Where does mutation occur? Can two processes lose updates? What is the complexity of finding an ID?
- Extension: introduce a repository interface and SQLite adapter without changing domain tests.

## Chapter 59 — Project 2: File ETL and Data-Quality Report

**Combines:** iterators, generators, context managers, regex, CSV/JSONL, exception design, typing, testing, statistics, NumPy, Pandas, logging, and profiling.

### Scenario and pipeline

An organization receives files from multiple sensors. Each row contains `source`, `external_id`, `observed_at`, `value`, and optional tags. Build a streaming pipeline that validates records, quarantines failures, detects duplicates, and publishes reproducible summary files.

```text
bytes → decoded rows → syntactic parse → normalized domain record
      → uniqueness checks → accepted stream → aggregates/report
                       ↘ rejected rows with reason and line context
```

Keep parsing, validation, and reporting separate. A parser answers “can these bytes become fields?” Domain validation answers “is this event allowed?” Reporting must receive only validated data.

```python
from collections.abc import Iterable, Iterator
from dataclasses import dataclass
from datetime import datetime
from decimal import Decimal

@dataclass(frozen=True, slots=True)
class RowError:
    line: int
    code: str
    message: str
    raw: dict[str, str]

def transform(rows: Iterable[dict[str, str]]) -> Iterator[tuple[Event | None, RowError | None]]:
    seen: set[tuple[str, str]] = set()
    for line, row in enumerate(rows, start=2):
        try:
            event = parse_event(row)
            key = (event.source, event.external_id)
            if key in seen:
                raise ValueError(f"duplicate key: {key}")
            seen.add(key)
        except (KeyError, ValueError, TypeError) as exc:
            yield None, RowError(line, "invalid_row", str(exc), row.copy())
        else:
            yield event, None
```

Do not catch `Exception`: programming defects should fail the run rather than be mislabeled as bad customer data. For huge files, an in-memory `seen` set may be too large; use sorted external processing, SQLite, or a database unique constraint.

### Reproducible reporting

Produce accepted/rejected counts, rejection reasons, per-source distributions, missingness, quantiles, outliers under a documented rule, input SHA-256, schema version, code version, timezone policy, and run timestamp. Separate observations by unit/currency rather than adding incompatible values.

```python
import pandas as pd

def source_report(frame: pd.DataFrame) -> pd.DataFrame:
    required = {"source", "value", "observed_at"}
    if missing := required - set(frame.columns):
        raise ValueError(f"missing columns: {sorted(missing)}")
    data = frame.assign(
        observed_at=pd.to_datetime(frame["observed_at"], utc=True, errors="raise"),
        value=pd.to_numeric(frame["value"], errors="raise"),
    )
    return (
        data.groupby("source", dropna=False)["value"]
        .agg(count="size", mean="mean", median="median", minimum="min", maximum="max")
        .reset_index()
        .sort_values("source", kind="stable")
    )
```

### Milestones and failure drills

1. Stream valid CSV and JSONL fixtures without loading them entirely.
2. Quarantine invalid encoding, missing fields, overflow, invalid times, and duplicates.
3. Atomically publish report and metadata only after success.
4. Add Pandas reports and compare results with a pure-Python reference on small fixtures.
5. Property-test normalization and invariants; fuzz parsers with bounded input.
6. Profile CPU and peak memory on a generated million-row file; optimize only measured bottlenecks.

Kill the process during parsing and publication. Confirm the previous report remains intact and temporary files are detectable/cleanable. Re-run identical input and explain which metadata should remain identical and which may change.

## Chapter 60 — Project 3: Resilient API Client and Authorized Scraper

**Combines:** HTTP, APIs, scraping policy, regular expressions/selectors, retries, pagination, async, typed boundaries, caching, testing, security, and observability.

### Rules before code

Use only sources you are authorized to access. Respect terms, robots guidance where applicable, rate limits, copyright/privacy constraints, and server capacity. Identify the client appropriately. A scraper being technically possible does not imply permission.

All remote input is untrusted. Set connect/read/write/pool timeouts, cap response size and pages, validate content type/schema, constrain redirects, and never log credentials. Retry transient failures only when the method is safe or the operation has an idempotency key.

### Injected transport and bounded pagination

```python
from dataclasses import dataclass
from typing import Any, Protocol
import httpx

class Transport(Protocol):
    def get(self, url: str, *, params: dict[str, str]) -> httpx.Response: ...

@dataclass(frozen=True)
class Item:
    id: str
    title: str

class CatalogClient:
    def __init__(self, transport: Transport, base_url: str, *, max_pages: int = 50):
        self.transport, self.base_url, self.max_pages = transport, base_url.rstrip("/"), max_pages

    def iter_items(self):
        cursor: str | None = None
        seen: set[str] = set()
        for _ in range(self.max_pages):
            response = self.transport.get(
                f"{self.base_url}/items", params={} if cursor is None else {"cursor": cursor}
            )
            response.raise_for_status()
            payload: Any = response.json()
            items, cursor = validate_page(payload)
            yield from items
            if cursor is None:
                return
            if cursor in seen:
                raise RuntimeError("pagination cursor cycle")
            seen.add(cursor)
        raise RuntimeError("page limit exceeded")
```

The real `httpx.Client` should be configured once and closed via a context manager. Tests inject `httpx.MockTransport` or a fake protocol implementation; they should never require the public internet.

### Retry policy

Retry connection failures, selected 5xx responses, and 429 according to a bounded policy. Honor a valid `Retry-After`, otherwise use exponential backoff with jitter. Use a monotonic deadline so individual retries cannot exceed the total budget. Do not retry authentication/validation errors. Emit attempt count and outcome metrics without secrets or full personal data.

### Scraper adapter

Treat HTML parsing as an adapter behind the same domain interface. Store small authorized fixtures for tests. Test missing elements, changed class names, duplicate IDs, relative URLs, unexpected encodings, oversized pages, and malicious links. Prefer semantic attributes over brittle absolute selectors.

### Milestones

1. Implement a schema-validating API client with fixture-based tests.
2. Add bounded cursor pagination and cycle detection.
3. Add retry/deadline logic with injected clock/sleeper and deterministic jitter.
4. Add conditional caching with ETag/Last-Modified where supported.
5. Implement the authorized HTML adapter and contract tests shared with the API adapter.
6. Add an async version with a semaphore, cancellation-safe cleanup, and the same limits.

Failure tests must cover DNS/connect/read timeout, TLS/redirect failures, 401/403, 404, 429, retryable/non-retryable 5xx, invalid JSON, wrong schema, page cycles, cancellation, and secret redaction.

## Chapter 61 — Project 4: Database-Backed FastAPI Service

**Combines:** classes, protocols, MongoDB, API design, Pydantic, FastAPI, authentication/authorization, indexes, concurrency, migrations, integration testing, and OpenAPI.

### Architecture and invariants

Expose the validated events from Project 2 through an authenticated service. Keep HTTP models separate from domain models and database documents. Application services depend on a repository protocol; adapters depend inward on that contract.

```text
HTTP/Pydantic → application service → domain model
                       ↓ protocol
                 Mongo repository → database
```

Required invariants include unique `(source, external_id)`, UTC instants, finite bounded values, immutable creation metadata, authorized tenant ownership, stable error codes, and bounded cursor pagination. Enforce invariants at more than one layer when races are possible; a database unique index is the final atomic guard.

```python
from typing import Protocol

class EventRepository(Protocol):
    async def add(self, event: Event) -> None: ...
    async def get(self, event_id: str, *, tenant_id: str) -> Event | None: ...
    async def list_page(self, *, tenant_id: str, after: str | None,
                        limit: int) -> tuple[list[Event], str | None]: ...

class EventService:
    def __init__(self, repository: EventRepository) -> None:
        self.repository = repository

    async def create(self, command: CreateEvent, actor: Actor) -> Event:
        actor.require("events:create")
        event = Event.from_command(command, tenant_id=actor.tenant_id)
        await self.repository.add(event)
        return event
```

### HTTP contract

Use correct status codes: 201 with `Location` for creation, 404 without leaking cross-tenant existence, 409 for unique conflicts, 422 for structured input validation, and stable problem details for expected errors. Do not expose stack traces. Apply request-size limits and safe CORS configuration at the deployment boundary.

Cursor tokens should be opaque, signed or integrity-protected when clients must not modify them, and based on a stable unique sort such as `(created_at, id)`. Offset pagination becomes slow and unstable as data changes.

### Database and migration work

- Derive compound indexes from real query filters and sort order; verify with `explain`.
- Translate duplicate-key errors to the domain conflict without a prior check-then-insert race.
- Version documents and write idempotent, resumable migrations with counters and checkpoints.
- Bound server selection and operation timeouts; do not retry arbitrary writes blindly.
- Test against a real disposable MongoDB for adapter behavior; mocks cannot validate indexes or wire semantics.

### Test pyramid and milestones

1. Domain tests: normalization, invariants, equality, authorization.
2. Service tests: fake repository, duplicate translation, tenant isolation.
3. HTTP tests: dependency override, auth, validation, errors, OpenAPI, pagination.
4. Mongo integration: unique/index behavior, ordering, migration, transient failures.
5. Race test: concurrent creation of the same key results in one success and conflicts.
6. Security test: horizontal/vertical privilege escalation, oversized input, injection-like values, and token/log leakage.

Definition of done includes a clean database bootstrap, readiness/liveness distinction, graceful shutdown, request IDs, latency/error metrics, structured redacted logs, and documented compatibility/versioning policy.

## Chapter 62 — Project 5: Production Release and Failure Drill

**Combines:** packaging, typing, testing, CI, containers, configuration, secrets, observability, performance, deployment, backup/restore, security, and incident response.

The last project is evidence that the earlier service can be operated, not merely started on a laptop.

### Reproducible release pipeline

```text
format/lint → type-check → unit/property tests → integration tests
→ build wheel/container → dependency and image scan → SBOM
→ sign/attest artifact → deploy staging → migration → smoke test
→ progressive production rollout → observe → promote or rollback
```

Pin the build environment, retain dependency hashes/lock data appropriate to the chosen workflow, build once, and promote the same artifact. Run as a non-root user with a read-only filesystem where possible. Supply secrets at runtime rather than baking them into images or repositories.

### Operational objectives

Define service-level indicators before dashboards: request success rate, latency distribution, ingestion freshness, queue depth, database saturation, and rejected-event rate. Choose objectives and alerts tied to user impact. Logs answer individual-event questions; metrics show trends; traces connect distributed latency.

### Mandatory failure drills

| Failure | Expected evidence |
|---|---|
| Invalid configuration | Process refuses startup with a redacted actionable error. |
| Database unavailable | Readiness fails, liveness remains meaningful, requests time out within budget. |
| Slow downstream | Deadlines and bounded concurrency prevent resource exhaustion. |
| Duplicate race | Database invariant holds; API returns one success and deterministic conflicts. |
| Broken migration | Checkpoint permits safe resume or rollback; old version compatibility is known. |
| Process termination | Graceful window drains/cancels work without accepting new traffic indefinitely. |
| Corrupt primary data | Restore into isolation is verified before promotion. |
| Vulnerable dependency | Ownership, patch decision, rebuild, redeploy, and evidence are recorded. |

### Performance experiment

Write a workload model with realistic payloads and concurrency. Measure p50/p95/p99 latency, throughput, error rate, CPU, memory, event-loop lag, connection-pool wait, and database query plans. Warm up, repeat, preserve raw results, and change one variable at a time. A benchmark without environment and workload description is not reproducible evidence.

### Final portfolio deliverables

- Architecture decision records and threat model.
- Versioned API/schema and migration compatibility matrix.
- Automated CI evidence and reproducible artifacts with SBOM.
- Load-test method/results and one profile-guided improvement.
- Dashboards, alerts, runbooks, ownership, rollback, and verified restore record.
- Post-incident report from one injected failure: timeline, impact, detection, contributing factors, corrective actions, and owners.

The project is complete when another engineer can clone it, verify it, deploy it without hidden knowledge, observe normal behavior, trigger a documented failure, and recover using the runbook.

---

# Appendices

## Appendix A — Atlas Capstone Blueprint

Final request flow:

```text
CLI / Scraper / API client
          ↓ validated boundary models
Application services → domain Event/Batch policies
          ↓ repository and clock/client protocols
MongoDB / files / remote HTTP adapters
          ↓
Pandas/NumPy report pipeline → API/CLI outputs
```

Definition of done: clean install; typed public API; tests and analyzers pass; authorized bounded ingestion; UTC/Unicode/schema policy; unique indexed persistence; authenticated/paginated API; structured logs/metrics; threat model; benchmark evidence; backup restore; reproducible release and external consumer.

## Appendix B — Python Cheat Sheet

```python
# collections and iteration
[f(x) for x in xs if ok(x)]
{x.key: x for x in xs}
{x.tag for x in xs}
(f(x) for x in xs)
for i, x in enumerate(xs, 1): ...
for a, b in zip(left, right, strict=True): ...

# boundaries
with path.open(encoding="utf-8") as f: ...
try: ...
except ExpectedError as exc: ...
else: ...
finally: ...

# typing
def find(items: Iterable[T], pred: Callable[[T], bool]) -> T | None: ...
```

```bash
# commands
python -m venv .venv
python -m pip install -e '.[dev]'
python -m pytest
python -m mypy src
python -m ruff check .
python -m build
```

## Appendix C — Complexity and Selection Guide

| Need | Prefer | Typical property |
|---|---|---|
| Ordered mutable sequence | `list` | index O(1), append amortized O(1) |
| Queue/deque | `collections.deque` | ends O(1) |
| Unique membership | `set` | average lookup O(1) |
| Key lookup | `dict` | average lookup O(1), insertion order |
| Fixed record | dataclass/NamedTuple | named schema |
| Lazy stream | generator/iterator | bounded memory, one pass |
| Homogeneous numeric array | NumPy | vectorized n-D storage |
| Labeled table | Pandas | alignment/group/merge |
| Validation boundary | Pydantic | runtime parse/error model |
| Closed async lifetime | `TaskGroup` | scoped tasks/failure aggregation |

## Appendix D — Readiness Matrix and Resources

You are professionally ready when you can explain and demonstrate: object identity/mutability; collection complexity; Unicode/bytes/timezones; function/import/error contracts; iterators/context managers/object protocols; strict typing; property/integration tests; safe files/network/database/API boundaries; concurrency/async cancellation; profiling; threat modelling; packaging; deployment; observability and rollback.

Primary references:

- [Python 3 documentation](https://docs.python.org/3/)
- [Python Packaging User Guide](https://packaging.python.org/)
- [NumPy documentation](https://numpy.org/doc/)
- [Pandas documentation](https://pandas.pydata.org/docs/)
- [FastAPI documentation](https://fastapi.tiangolo.com/)
- [PyMongo documentation](https://www.mongodb.com/docs/languages/python/pymongo-driver/current/)
- [pytest documentation](https://docs.pytest.org/)
- [mypy documentation](https://mypy.readthedocs.io/)
- [OWASP](https://owasp.org/) for web threat classes and verification guidance

No finite handbook replaces the language reference, library documentation, measured production behavior, or building real systems. Mastery means you can predict, test, diagnose, secure, and explain—not merely recognize syntax.

## Appendix E — Thirty-Chapter Practice Matrix

Use these as closed-book assessments. A solution is complete only with tests, invalid-input behavior, type/ownership explanation, and complexity or operational notes where relevant.

| Chapter | Required challenge |
|---|---|
| 1 | Build an import-safe CLI module; explain script, module, package, REPL and interpreter selection. |
| 2 | Draw the reference graph for nested shallow/deep copies and predict every mutation. |
| 3 | Implement decimal-safe invoice totals and justify equality/tolerance choices. |
| 4 | Normalize multilingual identifiers while retaining display text; test bytes/encoding failures. |
| 5 | Build batch editing without aliasing or mutation-during-iteration bugs; state operation costs. |
| 6 | Replace ambiguous tuple APIs with named records while preserving unpacking where useful. |
| 7 | Implement permission/tag difference, intersection and subset checks without losing required order. |
| 8 | Aggregate/group records, merge configuration with explicit precedence, and reject missing keys. |
| 9 | Validate message shapes with guards/match and distinguish missing, empty, false and zero. |
| 10 | Implement bounded pagination/retry and prove termination under repeated/empty pages. |
| 11 | Design a clean typed function API with positional/keyword rules and no mutable defaults. |
| 12 | Package modules with acyclic inward dependencies and no import-time I/O. |
| 13 | Compare eager/lazy transformations for readability, reuse, peak memory and error handling. |
| 14 | Implement predicates, callbacks and decorators while preserving metadata/exceptions. |
| 15 | Diagnose a supplied traceback, minimize the reproducer, identify root cause, add regression. |
| 16 | Schedule/display across DST boundaries using UTC instants and monotonic deadlines. |
| 17 | Design a public exception hierarchy with chaining, cleanup and narrow recovery. |
| 18 | Validate a bounded record grammar; demonstrate and repair a backtracking-prone regex. |
| 19 | Stream CSV/JSONL, quarantine bad records, atomically replace output, recover interruption. |
| 20 | Build/install a wheel in a clean venv and explain ranges, locks and supply-chain controls. |
| 21 | Model immutable domain values and composed services; verify equality/hash/invariants. |
| 22 | Scrape an authorized fixture/site with policy, rate, cache, timeout and parser-change tests. |
| 23 | Reproduce the project in two clean environments without committing environment contents. |
| 24 | Report statistical assumptions, robust summaries, uncertainty and reproducible NumPy results. |
| 25 | Validate schema/missingness/merge cardinality and optimize a measured Pandas bottleneck. |
| 26 | Explain HTTP/ASGI request flow and implement safe config, templates/cookies and health. |
| 27 | Design MongoDB documents/indexes from queries; prove duplicate safety and inspect a plan. |
| 28 | Build a typed client with TLS, auth, deadline, retry, pagination and malformed-response tests. |
| 29 | Build authenticated CRUD with stable errors, cursor pagination, OpenAPI and integration tests. |
| 30 | Run the complete Atlas flow from authorized source to report/database/API and clean rebuild. |

### Review questions

1. Why can a tuple be immutable yet contain changing state? Because immutability prevents rebinding tuple slots, not mutation of referenced objects.
2. Why is `is` correct for `None` but wrong for ordinary string/number equality? Identity asks object sameness; value equality is the domain requirement.
3. Why is an async endpoint sometimes slower than sync? Blocking calls freeze the loop, task overhead exists, and async primarily improves concurrent waiting—not CPU work.
4. Why does a unique database index beat “check then insert”? It makes the invariant atomic under concurrent writers.
5. Why is 100% coverage insufficient? Executing lines does not prove assertions, input space, concurrency, failure semantics, or requirements are correct.

## Appendix F — Professional Capstone Labs

### Lab 1 — Hostile file ingestion

Generate valid, truncated, oversized, invalid-UTF-8, duplicate and deeply nested inputs. Enforce byte/record/time limits; preserve line context; atomically publish only a fully validated result; fuzz the decoder and retain minimized regressions.

### Lab 2 — Data quality and reproducibility

Create a versioned schema and data dictionary with units, missingness and duplicate policy. Produce NumPy/Pandas reports with input hashes, code/dependency version, UTC execution time, random seed and statistical assumptions. Re-run from a clean environment.

### Lab 3 — Resilient external API adapter

Use an injected `httpx` transport. Test DNS/connect/read timeout, TLS/HTTP errors, 429 with `Retry-After`, 5xx retry with jitter, invalid JSON/schema, pagination cycle, cancellation and token redaction. Prove the retry policy cannot duplicate unsafe work.

### Lab 4 — MongoDB integrity and performance

Create schema validation and unique/compound indexes. Race duplicate writers, inspect `explain`, test cursor stability during inserts, handle transient errors, and demonstrate backup plus restore into an isolated database.

### Lab 5 — Secure production API

Test authentication and per-object authorization separately; validate token claims; bound bodies/pages/concurrency; add rate limits, secure headers and CORS policy; remove secrets/PII from logs; test mass assignment, injection and error information leakage.

### Lab 6 — Async lifecycle

Run bounded producers/consumers under normal completion, one-task failure, timeout, SIGTERM and cancellation. Prove all tasks/resources close and no record is silently lost. Record queue depth, throughput, failure and shutdown latency.

### Lab 7 — Performance dossier

Select a production-like workload, establish a correctness oracle, collect CPU/allocation/I/O/database profiles, form a hypothesis, change one thing, repeat statistically, and document rejected ideas plus complexity cost.

### Lab 8 — Release defense

From a clean checkout: build and install artifacts, run lint/types/tests/security checks, start dependencies, migrate data, ingest/report/serve, test readiness/shutdown/rollback, restore backup, verify SBOM/provenance and compile a separate consumer against the public API.

### Final scoring rubric

| Dimension | Weight | Mandatory evidence |
|---|---:|---|
| Correctness/domain model | 25% | invariants, error semantics, regression/property tests |
| Python/API design | 15% | clear ownership, types, protocols, inward dependencies |
| Data/database | 15% | schema, indexes, migrations, reproducibility, restore |
| Reliability/async | 15% | bounds, deadlines, cancellation, graceful shutdown |
| Security | 15% | threat model, authorization, validation, secret policy |
| Operations/performance | 15% | logs/metrics, profiling evidence, release/rollback |

Any remote-code execution, credential leak, unauthorized data access, silent corruption, unbounded hostile allocation, or unrecoverable migration is a mandatory failure regardless of total score.

## Appendix G — Hints, Selected Solutions, and Mastery Checks

Use this appendix only after writing and testing your own attempt. The short answers
cover foundation skills and establish the expected level of evidence; application
and challenge projects deliberately permit multiple architectures.

### Chapters 1–4 — execution, values, operators, and text

**Import-safe command (Chapter 1):**

```python
def main() -> int:
    print("Atlas is ready")
    return 0


if __name__ == "__main__":
    raise SystemExit(main())
```

Running the file prints once. `python -c "import atlas"` prints nothing because an
import sets `__name__` to the module name, not `"__main__"`.

**Validated count (Chapters 2–3):**

```python
def parse_count(raw: str) -> int:
    try:
        count = int(raw.strip())
    except ValueError as exc:
        raise ValueError(f"not an integer: {raw!r}") from exc
    if count < 0:
        raise ValueError("count cannot be negative")
    return count


assert parse_count(" 12 ") == 12
for invalid in ("", "1.5", "-1"):
    try:
        parse_count(invalid)
    except ValueError:
        pass
    else:
        raise AssertionError(f"accepted {invalid!r}")
```

**Unicode record (Chapter 4):** retain the user's display form and derive a search
key separately. Normalizing the stored display value would lose presentation data.

```python
import unicodedata

display = "  CAFÉ  ".strip()
search_key = unicodedata.normalize("NFC", display).casefold()
assert search_key == "café"
assert search_key.encode("utf-8").decode("utf-8") == search_key
```

### Chapters 5–10 — collections and control flow

**No aliasing and no mutation during iteration:**

```python
source = [{"id": "a", "valid": True}, {"id": "b", "valid": False}]
accepted = [record.copy() for record in source if record["valid"]]
accepted[0]["reviewed"] = True
assert "reviewed" not in source[0]
```

A shallow dictionary copy is sufficient here because every nested value is
immutable. If records contained nested lists, state an ownership policy rather than
blindly applying `deepcopy`.

**Order-preserving deduplication:**

```python
def unique_in_order(values: list[str]) -> list[str]:
    return list(dict.fromkeys(values))


assert unique_in_order(["b", "a", "b"]) == ["b", "a"]
```

**Bounded pagination:** a correct answer must stop on `None`, reject a repeated
cursor, and fail after a maximum page count. Tests need empty first page, normal
two-page flow, cursor cycle, and a server that never terminates. Chapter 10's
`fetch_all` is the reference implementation.

### Chapters 11–21 — functions, packages, errors, files, and objects

For every public function, write a five-part contract: accepted inputs, returned
value, side effects, expected exceptions, and complexity/limits. This is an example:

```python
from collections.abc import Iterable

def mean(values: Iterable[float]) -> float:
    """Return the arithmetic mean after one pass.

    Consumes ``values``; raises ValueError when empty; O(n) time and O(1) extra
    space. The caller owns any policy for NaN and infinity.
    """
    total = 0.0
    count = 0
    for value in values:
        total += value
        count += 1
    if count == 0:
        raise ValueError("mean requires at least one value")
    return total / count
```

**Atomic-file review:** the Chapter 19 implementation prevents readers from seeing
a partially written new JSON document on the same filesystem. A production answer
must additionally clean a temporary file after serialization/write failure and
decide whether directory metadata must be synced for the durability requirement.

**Composition answer:** `EventService(repository)` is preferable to
`EventService(InMemoryRepository)` inheritance because a service is not a
substitutable repository. It collaborates with one through a small contract.

### Chapters 22–30 — data and HTTP boundaries

A passing scraper/API-client solution has no live-network unit tests. Inject a
transport and test a fixture for success, malformed content, oversized content,
timeouts, non-retryable 4xx, bounded retryable 5xx, and pagination cycles. A passing
Pandas solution declares columns and duplicate/null policy before aggregation and
uses `merge(validate=...)` when cardinality is known.

Do not claim a statistical conclusion from code alone. State population, sample,
estimand, missingness mechanism, uncertainty method, assumptions, and practical
effect. A reproducible result records input hash, code/dependency versions, timezone,
and RNG seed where randomness exists.

### Chapters 31–42 — professional Python evidence

The minimum evidence portfolio is:

1. a typed package that installs from its wheel in a clean environment;
2. unit tests for domain policy and integration tests for real adapters;
3. one property test and one retained fuzz regression;
4. a bounded thread/process or async pipeline with failure and shutdown tests;
5. a threat model tied to concrete abuse tests;
6. a profile containing baseline, hypothesis, change, correctness check, and result;
7. CI that builds once and tests the produced artifact;
8. a deployment drill demonstrating readiness, rollback, and restored backup.

Reading the chapters without producing this evidence is familiarity, not mastery.

### Debugging rubric for any exercise

When a solution fails, record:

- the smallest input that reproduces it;
- exact Python/dependency versions;
- expected versus actual behavior;
- the final exception and first relevant application frame;
- the violated invariant, not merely the failing line;
- a regression test that fails before the fix and passes after it.

### Final self-assessment

Score each row from 0 to 3: **0** cannot explain; **1** recognizes; **2** implements
with documentation; **3** predicts failures, tests boundaries, and justifies tradeoffs.

| Area | Required demonstration |
|---|---|
| Language model | identity, mutability, scope, protocols, exceptions |
| Data structures | selection, complexity, aliasing, ordering, hashing |
| Boundaries | Unicode, time, files, JSON/CSV, HTTP, database validation |
| Design | small contracts, composition, dependency direction, public API |
| Quality | types, unit/property/integration tests, deterministic debugging |
| Reliability | bounds, deadlines, retries, cancellation, graceful shutdown |
| Security | threat model, authn/authz, injection defense, secret handling |
| Delivery | wheel, CI, migration, telemetry, rollback, restore |

A total below 16 means revisit foundations; 16–20 indicates productive junior-level
evidence; 21–23 indicates strong independent engineering; 24 requires defensible
evidence in every row. The score is diagnostic, not a job title or guarantee.
