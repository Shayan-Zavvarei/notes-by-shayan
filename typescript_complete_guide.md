# TypeScript: From Beginner to Professional

A rigorous guide to TypeScript's type system, JavaScript runtime semantics, library and application architecture, tooling, testing, and production boundaries. The professional chapters target the TypeScript 7 generation while calling out compatibility-sensitive features.

## Table of Contents

1. Introduction to TypeScript
2. Development Environment Setup
3. Core Type System
4. Functions and Type Signatures
5. Object-Oriented Programming in TypeScript
6. Advanced Type Features
7. Generics
8. Utility Types
9. Modules and Namespaces
10. Working with Third-Party Libraries
11. TypeScript with Node.js and Express
12. TypeScript with React
13. Testing with Jest
14. Migrating from JavaScript to TypeScript
15. Best Practices and Configuration
16. Capstone Project
17. TypeScript's Soundness Boundaries and Structural Typing
18. Control-Flow Analysis and Exhaustive Domain Models
19. Professional Type-Level Programming
20. ESM, Module Resolution, and Package Boundaries
21. tsconfig Architecture, Project References, and Monorepos
22. Runtime Validation, Serialization, and API Contracts
23. Async Systems, Cancellation, Streams, and Errors
24. Application Architecture and Domain Modeling
25. Testing Runtime Behavior and Types
26. Authoring and Publishing TypeScript Libraries
27. Performance, Security, and Production Operations
28. Professional Capstone: A Validated Task Platform

---

## 1. Introduction to TypeScript

### What is TypeScript?

TypeScript is a statically typed superset of JavaScript that compiles to plain JavaScript. It adds optional type annotations and compile-time type checking to JavaScript, enabling developers to catch errors early and build more maintainable codebases.

### Why Use TypeScript?

- Early error detection during development
- Enhanced IDE support with autocomplete and intelligent refactoring
- Self-documenting code through type annotations
- Improved maintainability in large codebases
- Seamless JavaScript interoperability

### JavaScript vs TypeScript

JavaScript uses dynamic typing where types are checked at runtime. TypeScript introduces static typing where types are checked at compile time, preventing many runtime errors before code execution.

---

## 2. Development Environment Setup

### Installing Node.js and npm

Download and install Node.js from nodejs.org. This includes npm (Node Package Manager).

Verify installation:

```bash
node --version
npm --version
```

### Installing TypeScript

Prefer a project-local compiler so every contributor and CI job uses the version recorded by the lockfile:

```bash
npm install --save-dev typescript
```

Verify installation:

```bash
tsc --version
```

### Setting Up a TypeScript Project

Create a new project directory:

```bash
mkdir typescript-learning
cd typescript-learning
npm init -y
```

Install TypeScript locally (recommended for projects):

```bash
npm install --save-dev typescript
```

Initialize TypeScript configuration:

```bash
npx tsc --init
```

This creates a `tsconfig.json` file with default compiler options.

### Project Structure

```
typescript-learning/
├── src/
│   └── index.ts
├── dist/
├── node_modules/
├── package.json
└── tsconfig.json
```

### Basic tsconfig.json Configuration

```json
{
  "compilerOptions": {
    "target": "ES2023",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "verbatimModuleSyntax": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "useUnknownInCatchVariables": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

### Compiling TypeScript

Compile a single file:

```bash
npx tsc src/index.ts
```

Compile entire project:

```bash
npx tsc
```

Watch mode for automatic recompilation:

```bash
npx tsc --watch
```

### Exercise: Hello TypeScript

Create `src/hello.ts`:

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

const message: string = greet("TypeScript");
console.log(message);
```

Compile and run:

```bash
npx tsc
node dist/hello.js
```

---

## 3. Core Type System

### Primitive Types

TypeScript supports all JavaScript primitive types with type annotations.

#### String

```typescript
let username: string = "Alice";
let greeting: string = `Welcome, ${username}`;
```

#### Number

```typescript
let age: number = 30;
let price: number = 19.99;
let hex: number = 0xf00d;
let binary: number = 0b1010;
```

#### Boolean

```typescript
let isActive: boolean = true;
let hasPermission: boolean = false;
```

#### Null and Undefined

```typescript
let empty: null = null;
let notDefined: undefined = undefined;
```

#### Symbol

```typescript
let sym1: symbol = Symbol("key");
let sym2: symbol = Symbol("key");
console.log(sym1 === sym2); // false
```

#### BigInt

```typescript
let big: bigint = 100n;
let alsoHuge: bigint = BigInt(9007199254740991);
```

### Type Inference

TypeScript can automatically infer types when not explicitly declared:

```typescript
let inferredString = "Hello"; // Type: string
let inferredNumber = 42; // Type: number
let inferredBoolean = true; // Type: boolean
```

### Arrays

```typescript
let numbers: number[] = [1, 2, 3, 4, 5];
let names: Array<string> = ["Alice", "Bob", "Charlie"];
```

### Tuples

Tuples allow you to express arrays with fixed types and lengths:

```typescript
let person: [string, number] = ["Alice", 30];
let rgb: [number, number, number] = [255, 0, 128];

// Accessing elements
console.log(person[0]); // "Alice"
console.log(person[1]); // 30
```

### Enums

Enums define a set of named constants:

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let move: Direction = Direction.Up;

enum Status {
  Success = 200,
  NotFound = 404,
  ServerError = 500
}

let response: Status = Status.Success;
```

String enums:

```typescript
enum Color {
  Red = "RED",
  Green = "GREEN",
  Blue = "BLUE"
}

let favoriteColor: Color = Color.Blue;
```

### Any Type

The `any` type disables type checking:

```typescript
let anything: any = "Hello";
anything = 42;
anything = true; // No error
```

Use sparingly as it defeats the purpose of TypeScript.

### Unknown Type

`unknown` is a type-safe alternative to `any`:

```typescript
let value: unknown = "Hello";

// Must narrow the type before use
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

### Never Type

The `never` type represents values that never occur:

```typescript
function throwError(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {}
}
```

### Void Type

Used for functions that do not return a value:

```typescript
function logMessage(message: string): void {
  console.log(message);
}
```

### Literal Types

Literal types allow you to specify exact values:

```typescript
let direction: "north" | "south" | "east" | "west";
direction = "north"; // OK
// direction = "up"; // Error

let dice: 1 | 2 | 3 | 4 | 5 | 6;
dice = 3; // OK
```

### Type Aliases

Create custom type names:

```typescript
type ID = string | number;
type Point = { x: number; y: number };

let userId: ID = "abc123";
let coordinate: Point = { x: 10, y: 20 };
```

### Union Types

A value can be one of several types:

```typescript
function printId(id: string | number): void {
  console.log(`ID: ${id}`);
}

printId(101);
printId("abc123");
```

### Intersection Types

Combine multiple types:

```typescript
type Person = { name: string };
type Employee = { employeeId: number };

type Staff = Person & Employee;

let staff: Staff = {
  name: "Alice",
  employeeId: 12345
};
```

### Type Assertions

Tell the compiler you know the type better:

```typescript
let someValue: unknown = "This is a string";
let strLength: number = (someValue as string).length;

// Alternative syntax
let strLength2: number = (<string>someValue).length;
```

### Exercise: Type System Basics

Create `src/types-exercise.ts`:

```typescript
// Define types for a product catalog
type ProductId = string | number;

enum Category {
  Electronics = "ELECTRONICS",
  Clothing = "CLOTHING",
  Books = "BOOKS"
}

type Product = {
  id: ProductId;
  name: string;
  price: number;
  category: Category;
  inStock: boolean;
};

function displayProduct(product: Product): void {
  console.log(`${product.name} - $${product.price}`);
  console.log(`Category: ${product.category}`);
  console.log(`In Stock: ${product.inStock ? "Yes" : "No"}`);
}

const laptop: Product = {
  id: "LAP001",
  name: "Dell XPS 13",
  price: 1299.99,
  category: Category.Electronics,
  inStock: true
};

displayProduct(laptop);
```

---

## 4. Functions and Type Signatures

### Function Type Annotations

```typescript
function add(a: number, b: number): number {
  return a + b;
}

const subtract = (a: number, b: number): number => {
  return a - b;
};
```

### Optional Parameters

```typescript
function buildName(firstName: string, lastName?: string): string {
  if (lastName) {
    return `${firstName} ${lastName}`;
  }
  return firstName;
}

console.log(buildName("Alice")); // "Alice"
console.log(buildName("Alice", "Smith")); // "Alice Smith"
```

### Default Parameters

```typescript
function greet(name: string, greeting: string = "Hello"): string {
  return `${greeting}, ${name}!`;
}

console.log(greet("Alice")); // "Hello, Alice!"
console.log(greet("Bob", "Hi")); // "Hi, Bob!"
```

### Rest Parameters

```typescript
function sum(...numbers: number[]): number {
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // 15
```

### Function Overloading

Define multiple function signatures:

```typescript
function process(value: string): string;
function process(value: number): number;
function process(value: string | number): string | number {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value * 2;
}

console.log(process("hello")); // "HELLO"
console.log(process(5)); // 10
```

### Function Types

```typescript
type MathOperation = (a: number, b: number) => number;

const multiply: MathOperation = (a, b) => a * b;
const divide: MathOperation = (a, b) => a / b;
```

### Higher-Order Functions

Functions that accept or return functions:

```typescript
function createMultiplier(factor: number): (value: number) => number {
  return (value: number) => value * factor;
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

### Callback Functions

```typescript
function fetchData(callback: (data: string) => void): void {
  setTimeout(() => {
    callback("Data loaded");
  }, 1000);
}

fetchData((data) => {
  console.log(data);
});
```

### Exercise: Function Practice

Create `src/functions-exercise.ts`:

```typescript
// Calculator with function overloading
function calculate(operation: "add", a: number, b: number): number;
function calculate(operation: "multiply", a: number, b: number): number;
function calculate(operation: "concat", a: string, b: string): string;
function calculate(
  operation: "add" | "multiply" | "concat",
  a: any,
  b: any
): any {
  switch (operation) {
    case "add":
      return a + b;
    case "multiply":
      return a * b;
    case "concat":
      return a + b;
  }
}

console.log(calculate("add", 5, 3)); // 8
console.log(calculate("multiply", 5, 3)); // 15
console.log(calculate("concat", "Hello, ", "World!")); // "Hello, World!"

// Higher-order function for filtering
type Predicate<T> = (item: T) => boolean;

function filter<T>(array: T[], predicate: Predicate<T>): T[] {
  const result: T[] = [];
  for (const item of array) {
    if (predicate(item)) {
      result.push(item);
    }
  }
  return result;
}

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evenNumbers = filter(numbers, (n) => n % 2 === 0);
console.log(evenNumbers); // [2, 4, 6, 8, 10]
```

---

## 5. Object-Oriented Programming in TypeScript

### Classes

```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  introduce(): void {
    console.log(`Hi, I'm ${this.name} and I'm ${this.age} years old.`);
  }
}

const person = new Person("Alice", 30);
person.introduce();
```

### Access Modifiers

```typescript
class BankAccount {
  public accountNumber: string;
  private balance: number;
  protected owner: string;

  constructor(accountNumber: string, owner: string, initialBalance: number) {
    this.accountNumber = accountNumber;
    this.owner = owner;
    this.balance = initialBalance;
  }

  public deposit(amount: number): void {
    this.balance += amount;
  }

  public getBalance(): number {
    return this.balance;
  }
}

const account = new BankAccount("123456", "Alice", 1000);
account.deposit(500);
console.log(account.getBalance()); // 1500
// console.log(account.balance); // Error: private
```

### Readonly Properties

```typescript
class Point {
  readonly x: number;
  readonly y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

const point = new Point(10, 20);
// point.x = 15; // Error: readonly
```

### Getters and Setters

```typescript
class Temperature {
  private _celsius: number = 0;

  get celsius(): number {
    return this._celsius;
  }

  set celsius(value: number) {
    if (value < -273.15) {
      throw new Error("Temperature below absolute zero!");
    }
    this._celsius = value;
  }

  get fahrenheit(): number {
    return (this._celsius * 9) / 5 + 32;
  }

  set fahrenheit(value: number) {
    this.celsius = ((value - 32) * 5) / 9;
  }
}

const temp = new Temperature();
temp.celsius = 25;
console.log(temp.fahrenheit); // 77
```

### Static Members

```typescript
class MathUtils {
  static PI: number = 3.14159;

  static circleArea(radius: number): number {
    return this.PI * radius * radius;
  }
}

console.log(MathUtils.PI);
console.log(MathUtils.circleArea(5));
```

### Inheritance

```typescript
class Animal {
  constructor(public name: string) {}

  move(distance: number): void {
    console.log(`${this.name} moved ${distance} meters.`);
  }
}

class Dog extends Animal {
  bark(): void {
    console.log("Woof! Woof!");
  }
}

const dog = new Dog("Buddy");
dog.bark();
dog.move(10);
```

### Abstract Classes

```typescript
abstract class Shape {
  abstract area(): number;
  abstract perimeter(): number;

  describe(): void {
    console.log(`Area: ${this.area()}, Perimeter: ${this.perimeter()}`);
  }
}

class Rectangle extends Shape {
  constructor(private width: number, private height: number) {
    super();
  }

  area(): number {
    return this.width * this.height;
  }

  perimeter(): number {
    return 2 * (this.width + this.height);
  }
}

const rect = new Rectangle(10, 5);
rect.describe(); // Area: 50, Perimeter: 30
```

### Interfaces

Interfaces define contracts for objects:

```typescript
interface Vehicle {
  brand: string;
  model: string;
  year: number;
  start(): void;
}

class Car implements Vehicle {
  constructor(
    public brand: string,
    public model: string,
    public year: number
  ) {}

  start(): void {
    console.log(`${this.brand} ${this.model} is starting...`);
  }
}

const car = new Car("Toyota", "Camry", 2023);
car.start();
```

### Interface Extension

```typescript
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  employeeId: number;
  department: string;
}

const employee: Employee = {
  name: "Alice",
  age: 30,
  employeeId: 12345,
  department: "Engineering"
};
```

### Interface vs Type Alias

Interfaces can be extended and merged, type aliases cannot:

```typescript
interface User {
  name: string;
}

interface User {
  age: number;
}

// Merged into one interface
const user: User = { name: "Alice", age: 30 };
```

### Exercise: OOP Practice

Create `src/oop-exercise.ts`:

```typescript
// Library management system
interface LibraryItem {
  id: string;
  title: string;
  available: boolean;
  checkout(): void;
  return(): void;
}

abstract class BaseItem implements LibraryItem {
  constructor(
    public id: string,
    public title: string,
    public available: boolean = true
  ) {}

  checkout(): void {
    if (!this.available) {
      throw new Error(`${this.title} is not available`);
    }
    this.available = false;
    console.log(`Checked out: ${this.title}`);
  }

  return(): void {
    this.available = true;
    console.log(`Returned: ${this.title}`);
  }

  abstract getInfo(): string;
}

class Book extends BaseItem {
  constructor(id: string, title: string, private author: string, private pages: number) {
    super(id, title);
  }

  getInfo(): string {
    return `Book: ${this.title} by ${this.author} (${this.pages} pages)`;
  }
}

class DVD extends BaseItem {
  constructor(id: string, title: string, private director: string, private duration: number) {
    super(id, title);
  }

  getInfo(): string {
    return `DVD: ${this.title} directed by ${this.director} (${this.duration} min)`;
  }
}

class Library {
  private items: LibraryItem[] = [];

  addItem(item: LibraryItem): void {
    this.items.push(item);
  }

  findById(id: string): LibraryItem | undefined {
    return this.items.find(item => item.id === id);
  }

  listAvailable(): LibraryItem[] {
    return this.items.filter(item => item.available);
  }
}

const library = new Library();
library.addItem(new Book("B001", "1984", "George Orwell", 328));
library.addItem(new DVD("D001", "Inception", "Christopher Nolan", 148));

const book = library.findById("B001");
if (book) {
  book.checkout();
  book.return();
}
```

---

## 6. Advanced Type Features

### Type Guards

Type guards narrow down types within conditional blocks:

```typescript
function isString(value: unknown): value is string {
  return typeof value === "string";
}

function process(value: string | number): void {
  if (isString(value)) {
    console.log(value.toUpperCase());
  } else {
    console.log(value.toFixed(2));
  }
}
```

### Discriminated Unions

Use a common property to discriminate between types:

```typescript
interface Circle {
  kind: "circle";
  radius: number;
}

interface Square {
  kind: "square";
  sideLength: number;
}

interface Triangle {
  kind: "triangle";
  base: number;
  height: number;
}

type Shape = Circle | Square | Triangle;

function getArea(shape: Shape): number {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.sideLength ** 2;
    case "triangle":
      return (shape.base * shape.height) / 2;
  }
}
```

### Index Signatures

```typescript
interface StringMap {
  [key: string]: string;
}

const config: StringMap = {
  apiUrl: "https://api.example.com",
  apiKey: "abc123"
};
```

### Mapped Types

Transform properties of existing types:

```typescript
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};

type Optional<T> = {
  [P in keyof T]?: T[P];
};

interface User {
  id: number;
  name: string;
  email: string;
}

type ReadonlyUser = Readonly<User>;
type PartialUser = Optional<User>;
```

### Conditional Types

Types that depend on conditions:

```typescript
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false

type NonNullable<T> = T extends null | undefined ? never : T;

type C = NonNullable<string | null>; // string
```

### Keyof Operator

Extract keys from a type:

```typescript
interface Person {
  name: string;
  age: number;
  email: string;
}

type PersonKeys = keyof Person; // "name" | "age" | "email"

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person: Person = { name: "Alice", age: 30, email: "alice@example.com" };
const name = getProperty(person, "name"); // Type: string
```

### Indexed Access Types

```typescript
interface Car {
  make: string;
  model: string;
  year: number;
}

type Make = Car["make"]; // string
type ModelYear = Car["model" | "year"]; // string | number
```

### Template Literal Types

```typescript
type Direction = "left" | "right" | "up" | "down";
type Move = `move-${Direction}`; // "move-left" | "move-right" | "move-up" | "move-down"

type EventName<T extends string> = `on${Capitalize<T>}`;
type ClickEvent = EventName<"click">; // "onClick"
```

### Exercise: Advanced Types

Create `src/advanced-types-exercise.ts`:

```typescript
// Create a type-safe event emitter
type EventMap = {
  click: { x: number; y: number };
  keypress: { key: string };
  submit: { data: string };
};

class TypedEventEmitter<T extends object> {
  private listeners: {
    [K in keyof T]?: Array<(payload: T[K]) => void>;
  } = {};

  on<K extends keyof T>(event: K, listener: (payload: T[K]) => void): void {
    if (!this.listeners[event]) {
      this.listeners[event] = [];
    }
    this.listeners[event]!.push(listener);
  }

  emit<K extends keyof T>(event: K, payload: T[K]): void {
    const eventListeners = this.listeners[event];
    if (eventListeners) {
      eventListeners.forEach(listener => listener(payload));
    }
  }
}

const emitter = new TypedEventEmitter<EventMap>();

emitter.on("click", ({ x, y }) => {
  console.log(`Clicked at (${x}, ${y})`);
});

emitter.on("keypress", ({ key }) => {
  console.log(`Key pressed: ${key}`);
});

emitter.emit("click", { x: 100, y: 200 });
emitter.emit("keypress", { key: "Enter" });

// Deep readonly type
type DeepReadonly<T> = {
  readonly [P in keyof T]: T[P] extends object ? DeepReadonly<T[P]> : T[P];
};

interface Config {
  database: {
    host: string;
    port: number;
  };
  api: {
    key: string;
  };
}

type ReadonlyConfig = DeepReadonly<Config>;
```

---

## 7. Generics

### Generic Functions

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output1 = identity<string>("hello");
let output2 = identity<number>(42);
let output3 = identity("world"); // Type inferred
```

### Generic Interfaces

```typescript
interface Box<T> {
  value: T;
}

let stringBox: Box<string> = { value: "hello" };
let numberBox: Box<number> = { value: 42 };
```

### Generic Classes

```typescript
class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }

  isEmpty(): boolean {
    return this.items.length === 0;
  }
}

const numberStack = new Stack<number>();
numberStack.push(1);
numberStack.push(2);
console.log(numberStack.pop()); // 2

const stringStack = new Stack<string>();
stringStack.push("hello");
stringStack.push("world");
```

### Generic Constraints

```typescript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): void {
  console.log(arg.length);
}

logLength("hello"); // OK
logLength([1, 2, 3]); // OK
logLength({ length: 10, value: 3 }); // OK
// logLength(123); // Error: number doesn't have length
```

### Multiple Type Parameters

```typescript
function pair<K, V>(key: K, value: V): [K, V] {
  return [key, value];
}

const stringNumberPair = pair("age", 30);
const booleanArrayPair = pair(true, [1, 2, 3]);
```

### Generic Utility Functions

```typescript
function map<T, U>(array: T[], fn: (item: T) => U): U[] {
  return array.map(fn);
}

const numbers = [1, 2, 3, 4, 5];
const doubled = map(numbers, n => n * 2);
const strings = map(numbers, n => n.toString());
```

### Exercise: Generics Practice

Create `src/generics-exercise.ts`:

```typescript
// Generic queue data structure
class Queue<T> {
  private items: T[] = [];

  enqueue(item: T): void {
    this.items.push(item);
  }

  // For production queues use a head index or deque; Array.shift() is O(n).
  dequeue(): T | undefined { return this.items.shift(); }

  peek(): T | undefined {
    return this.items[0];
  }

  size(): number {
    return this.items.length;
  }

  isEmpty(): boolean {
    return this.items.length === 0;
  }
}

const numberQueue = new Queue<number>();
numberQueue.enqueue(1);
numberQueue.enqueue(2);
numberQueue.enqueue(3);
console.log(numberQueue.dequeue()); // 1
console.log(numberQueue.peek()); // 2

// Generic result type for error handling
type Result<T, E = Error> =
  | { success: true; value: T }
  | { success: false; error: E };

function divide(a: number, b: number): Result<number, string> {
  if (b === 0) {
    return { success: false, error: "Division by zero" };
  }
  return { success: true, value: a / b };
}

const result1 = divide(10, 2);
if (result1.success) {
  console.log(`Result: ${result1.value}`);
} else {
  console.log(`Error: ${result1.error}`);
}

// Generic cache with constraints
interface Cacheable {
  id: string | number;
}

class Cache<T extends Cacheable> {
  private store = new Map<string | number, T>();

  set(item: T): void {
    this.store.set(item.id, item);
  }

  get(id: string | number): T | undefined {
    return this.store.get(id);
  }

  has(id: string | number): boolean {
    return this.store.has(id);
  }

  clear(): void {
    this.store.clear();
  }
}

interface User extends Cacheable {
  id: number;
  name: string;
}

const userCache = new Cache<User>();
userCache.set({ id: 1, name: "Alice" });
console.log(userCache.get(1)); // { id: 1, name: "Alice" }
```

---

## 8. Utility Types

TypeScript provides several built-in utility types for common type transformations.

### Partial

Make all properties optional:

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

function updateTodo(todo: Todo, fieldsToUpdate: Partial<Todo>): Todo {
  return { ...todo, ...fieldsToUpdate };
}

const todo: Todo = {
  title: "Learn TypeScript",
  description: "Study utility types",
  completed: false
};

const updatedTodo = updateTodo(todo, { completed: true });
```

### Required

Make all properties required:

```typescript
interface Props {
  a?: number;
  b?: string;
}

const obj1: Props = { a: 5 };
const obj2: Required<Props> = { a: 5, b: "hello" };
```

### Readonly

Make all properties readonly:

```typescript
interface Config {
  endpoint: string;
  apiKey: string;
}

const config: Readonly<Config> = {
  endpoint: "https://api.example.com",
  apiKey: "abc123"
};

// config.apiKey = "new-key"; // Error: readonly
```

### Record

Construct an object type with keys of type K and values of type T:

```typescript
type Role = "admin" | "user" | "guest";

const permissions: Record<Role, string[]> = {
  admin: ["read", "write", "delete"],
  user: ["read", "write"],
  guest: ["read"]
};
```

### Pick

Create a type by picking specific properties:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  password: string;
}

type UserPreview = Pick<User, "id" | "name" | "email">;

const preview: UserPreview = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};
```

### Omit

Create a type by omitting specific properties:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  password: string;
}

type UserWithoutPassword = Omit<User, "password">;

const user: UserWithoutPassword = {
  id: 1,
  name: "Alice",
  email: "alice@example.com"
};
```

### Exclude

Exclude types from a union:

```typescript
type T = Exclude<"a" | "b" | "c", "a">; // "b" | "c"
type U = Exclude<string | number | boolean, string>; // number | boolean
```

### Extract

Extract types from a union:

```typescript
type T = Extract<"a" | "b" | "c", "a" | "f">; // "a"
type U = Extract<string | number | boolean, string | boolean>; // string | boolean
```

### NonNullable

Remove null and undefined from a type:

```typescript
type T = NonNullable<string | number | undefined | null>; // string | number
```

### ReturnType

Extract the return type of a function:

```typescript
function getUser() {
  return { id: 1, name: "Alice" };
}

type User = ReturnType<typeof getUser>; // { id: number; name: string; }
```

### Parameters

Extract parameter types of a function:

```typescript
function createUser(name: string, age: number) {
  return { name, age };
}

type CreateUserParams = Parameters<typeof createUser>; // [string, number]
```

### Exercise: Utility Types

Create `src/utility-types-exercise.ts`:

```typescript
// API response handler with utility types
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

interface User {
  id: number;
  username: string;
  email: string;
  password: string;
  createdAt: Date;
  updatedAt: Date;
}

type UserResponse = Omit<User, "password">;

type CreateUserInput = Pick<User, "username" | "email" | "password">;

type UpdateUserInput = Partial<CreateUserInput>;

function fetchUser(id: number): ApiResponse<UserResponse> {
  return {
    data: {
      id,
      username: "alice",
      email: "alice@example.com",
      createdAt: new Date(),
      updatedAt: new Date()
    },
    status: 200,
    message: "Success"
  };
}

function createUser(input: CreateUserInput): ApiResponse<UserResponse> {
  return {
    data: {
      id: 1,
      username: input.username,
      email: input.email,
      createdAt: new Date(),
      updatedAt: new Date()
    },
    status: 201,
    message: "User created"
  };
}

function updateUser(id: number, input: UpdateUserInput): ApiResponse<UserResponse> {
  return {
    data: {
      id,
      username: "alice",
      email: input.email || "alice@example.com",
      createdAt: new Date(),
      updatedAt: new Date()
    },
    status: 200,
    message: "User updated"
  };
}

// State management with readonly
type AppState = Readonly<{
  users: ReadonlyArray<Readonly<UserResponse>>;
  loading: boolean;
  error: string | null;
}>;

const initialState: AppState = {
  users: [],
  loading: false,
  error: null
};
```

---

## 9. Modules and Namespaces

### ES6 Modules

Export and import functionality between files.

`math.ts`:

```typescript
export function add(a: number, b: number): number {
  return a + b;
}

export function subtract(a: number, b: number): number {
  return a - b;
}

export const PI = 3.14159;
```

`app.ts`:

```typescript
import { add, subtract, PI } from "./math";

console.log(add(5, 3));
console.log(PI);
```

### Default Exports

`logger.ts`:

```typescript
export default class Logger {
  log(message: string): void {
    console.log(`[LOG]: ${message}`);
  }
}
```

`app.ts`:

```typescript
import Logger from "./logger";

const logger = new Logger();
logger.log("Application started");
```

### Re-exporting

`index.ts`:

```typescript
export { add, subtract } from "./math";
export { default as Logger } from "./logger";
export * from "./utils";
```

### Namespaces

Organize code into logical groups (less common in modern TypeScript):

```typescript
namespace Geometry {
  export interface Point {
    x: number;
    y: number;
  }

  export function distance(p1: Point, p2: Point): number {
    const dx = p2.x - p1.x;
    const dy = p2.y - p1.y;
    return Math.sqrt(dx * dx + dy * dy);
  }
}

const p1: Geometry.Point = { x: 0, y: 0 };
const p2: Geometry.Point = { x: 3, y: 4 };
console.log(Geometry.distance(p1, p2)); // 5
```

### Exercise: Module Organization

Create a modular calculator:

`src/calculator/operations.ts`:

```typescript
export function add(a: number, b: number): number {
  return a + b;
}

export function subtract(a: number, b: number): number {
  return a - b;
}

export function multiply(a: number, b: number): number {
  return a * b;
}

export function divide(a: number, b: number): number {
  if (b === 0) throw new Error("Division by zero");
  return a / b;
}
```

`src/calculator/advanced.ts`:

```typescript
export function power(base: number, exponent: number): number {
  return Math.pow(base, exponent);
}

export function sqrt(value: number): number {
  if (value < 0) throw new Error("Cannot calculate square root of negative number");
  return Math.sqrt(value);
}
```

`src/calculator/index.ts`:

```typescript
export * from "./operations";
export * from "./advanced";

export class Calculator {
  private history: string[] = [];

  calculate(left: number, operation: "+" | "-" | "*" | "/", right: number): number {
    const expression = `${left} ${operation} ${right}`;
    this.history.push(expression);
    switch (operation) {
      case "+": return left + right;
      case "-": return left - right;
      case "*": return left * right;
      case "/": if (right === 0) throw new Error("Division by zero"); return left / right;
    }
  }

  getHistory(): string[] {
    return [...this.history];
  }
}
```

`src/app.ts`:

```typescript
import { add, multiply, power, Calculator } from "./calculator";

console.log(add(5, 3));
console.log(multiply(4, 7));
console.log(power(2, 8));

const calc = new Calculator();
console.log(calc.calculate("10 + 5 * 2"));
```

---

## 10. Working with Third-Party Libraries

### Installing Type Definitions

Many JavaScript libraries have TypeScript type definitions available via DefinitelyTyped.

```bash
npm install axios
npm install --save-dev @types/node
```

### Using Axios with TypeScript

```typescript
import axios, { AxiosResponse } from "axios";

interface User {
  id: number;
  name: string;
  email: string;
}

async function fetchUser(id: number): Promise<User> {
  const response: AxiosResponse<User> = await axios.get(
    `https://api.example.com/users/${id}`
  );
  return response.data;
}

async function main() {
  try {
    const user = await fetchUser(1);
    console.log(user.name);
  } catch (error) {
    console.error("Error fetching user:", error);
  }
}
```

### Using Lodash with TypeScript

```bash
npm install lodash
npm install --save-dev @types/lodash
```

```typescript
import _ from "lodash";

const numbers = [1, 2, 3, 4, 5];
const doubled = _.map(numbers, n => n * 2);
const sum = _.sum(numbers);

console.log(doubled);
console.log(sum);
```

### ts-node for Running TypeScript Directly

```bash
npm install --save-dev ts-node
```

Add to `package.json`:

```json
{
  "scripts": {
    "dev": "ts-node src/index.ts"
  }
}
```

### Creating Declaration Files

For libraries without type definitions, create a `.d.ts` file:

`src/types/my-library.d.ts`:

```typescript
declare module "my-library" {
  export function doSomething(value: string): number;

  export interface Config {
    apiKey: string;
    timeout: number;
  }

  export class Client {
    constructor(config: Config);
    request(url: string): Promise<unknown>;
  }
}
```

### Exercise: Third-Party Integration

Create `src/third-party-exercise.ts`:

```bash
npm install axios date-fns
npm install --save-dev @types/node
```

```typescript
import axios from "axios";
import { format, addDays } from "date-fns";

interface Post {
  userId: number;
  id: number;
  title: string;
  body: string;
}

class BlogService {
  private baseUrl = "https://jsonplaceholder.typicode.com";

  async getPosts(): Promise<Post[]> {
    const response = await axios.get<Post[]>(`${this.baseUrl}/posts`);
    return response.data;
  }

  async getPost(id: number): Promise<Post> {
    const response = await axios.get<Post>(`${this.baseUrl}/posts/${id}`);
    return response.data;
  }

  async createPost(post: Omit<Post, "id">): Promise<Post> {
    const response = await axios.post<Post>(`${this.baseUrl}/posts`, post);
    return response.data;
  }
}

async function main() {
  const service = new BlogService();

  const posts = await service.getPosts();
  console.log(`Fetched ${posts.length} posts`);

  const firstPost = await service.getPost(1);
  console.log(`Post title: ${firstPost.title}`);

  const today = new Date();
  const nextWeek = addDays(today, 7);
  console.log(`Today: ${format(today, "yyyy-MM-dd")}`);
  console.log(`Next week: ${format(nextWeek, "yyyy-MM-dd")}`);
}

main().catch(console.error);
```

---

## 11. TypeScript with Node.js and Express

### Setting Up Express with TypeScript

```bash
npm init -y
npm install express
npm install --save-dev typescript @types/node @types/express ts-node nodemon
```

Initialize TypeScript:

```bash
npx tsc --init
```

Update `tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "ES2023",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "verbatimModuleSyntax": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true
  }
}
```

Add scripts to `package.json`:

```json
{
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js",
    "dev": "nodemon --exec ts-node src/index.ts"
  }
}
```

### Basic Express Server

`src/index.ts`:

```typescript
import express, { Request, Response, NextFunction } from "express";

const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

app.get("/", (req: Request, res: Response) => {
  res.json({ message: "Hello, TypeScript with Express!" });
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### Typed Request and Response

```typescript
import { Request, Response } from "express";

interface User {
  id: number;
  name: string;
  email: string;
}

const users: User[] = [
  { id: 1, name: "Alice", email: "alice@example.com" },
  { id: 2, name: "Bob", email: "bob@example.com" }
];

app.get("/users", (req: Request, res: Response) => {
  res.json(users);
});

app.get("/users/:id", (req: Request, res: Response) => {
  const id = parseInt(req.params.id);
  const user = users.find(u => u.id === id);

  if (!user) {
    return res.status(404).json({ error: "User not found" });
  }

  res.json(user);
});
```

### Request Body Typing

```typescript
interface CreateUserDto {
  name: string;
  email: string;
}

app.post("/users", (req: Request<{}, {}, CreateUserDto>, res: Response) => {
  const { name, email } = req.body;

  const newUser: User = {
    id: users.length + 1,
    name,
    email
  };

  users.push(newUser);
  res.status(201).json(newUser);
});
```

### Middleware with TypeScript

```typescript
import { Request, Response, NextFunction } from "express";

function logger(req: Request, res: Response, next: NextFunction): void {
  console.log(`${req.method} ${req.path}`);
  next();
}

function errorHandler(
  err: Error,
  req: Request,
  res: Response,
  next: NextFunction
): void {
  console.error(err.stack);
  res.status(500).json({ error: "Internal server error" });
}

app.use(logger);
app.use(errorHandler);
```

### Express Router with TypeScript

`src/routes/users.ts`:

```typescript
import { Router, Request, Response } from "express";

const router = Router();

interface User {
  id: number;
  name: string;
  email: string;
}

let users: User[] = [];

router.get("/", (req: Request, res: Response) => {
  res.json(users);
});

router.post("/", (req: Request, res: Response) => {
  const user: User = {
    id: users.length + 1,
    ...req.body
  };
  users.push(user);
  res.status(201).json(user);
});

router.put("/:id", (req: Request, res: Response) => {
  const id = parseInt(req.params.id);
  const index = users.findIndex(u => u.id === id);

  if (index === -1) {
    return res.status(404).json({ error: "User not found" });
  }

  users[index] = { ...users[index], ...req.body };
  res.json(users[index]);
});

router.delete("/:id", (req: Request, res: Response) => {
  const id = parseInt(req.params.id);
  users = users.filter(u => u.id !== id);
  res.status(204).send();
});

export default router;
```

`src/index.ts`:

```typescript
import express from "express";
import userRoutes from "./routes/users";

const app = express();
app.use(express.json());
app.use("/api/users", userRoutes);

app.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

### Exercise: REST API with Express

Create a complete REST API for a task management system in `src/task-api/`:

`src/task-api/types.ts`:

```typescript
export interface Task {
  id: number;
  title: string;
  description: string;
  completed: boolean;
  createdAt: Date;
  updatedAt: Date;
}

export type CreateTaskDto = Omit<Task, "id" | "createdAt" | "updatedAt" | "completed">;
export type UpdateTaskDto = Partial<CreateTaskDto & { completed: boolean }>;
```

`src/task-api/tasks.ts`:

```typescript
import { Router, Request, Response } from "express";
import { Task, CreateTaskDto, UpdateTaskDto } from "./types";

const router = Router();
let tasks: Task[] = [];
let nextId = 1;

router.get("/", (req: Request, res: Response) => {
  res.json(tasks);
});

router.get("/:id", (req: Request, res: Response) => {
  const task = tasks.find(t => t.id === parseInt(req.params.id));
  if (!task) {
    return res.status(404).json({ error: "Task not found" });
  }
  res.json(task);
});

router.post("/", (req: Request<{}, {}, CreateTaskDto>, res: Response) => {
  const newTask: Task = {
    id: nextId++,
    ...req.body,
    completed: false,
    createdAt: new Date(),
    updatedAt: new Date()
  };
  tasks.push(newTask);
  res.status(201).json(newTask);
});

router.put("/:id", (req: Request<{ id: string }, {}, UpdateTaskDto>, res: Response) => {
  const id = parseInt(req.params.id);
  const index = tasks.findIndex(t => t.id === id);

  if (index === -1) {
    return res.status(404).json({ error: "Task not found" });
  }

  tasks[index] = {
    ...tasks[index],
    ...req.body,
    updatedAt: new Date()
  };

  res.json(tasks[index]);
});

router.delete("/:id", (req: Request, res: Response) => {
  const id = parseInt(req.params.id);
  tasks = tasks.filter(t => t.id !== id);
  res.status(204).send();
});

export default router;
```

---

## 12. TypeScript with React

### Setting Up React with TypeScript

Create a new React app with TypeScript:

```bash
npx create-react-app my-app --template typescript
```

Or add TypeScript to existing React app:

```bash
npm install --save typescript @types/react @types/react-dom
```

### Function Components with TypeScript

```typescript
import React from "react";

interface GreetingProps {
  name: string;
  age?: number;
}

const Greeting: React.FC<GreetingProps> = ({ name, age }) => {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      {age && <p>You are {age} years old.</p>}
    </div>
  );
};

export default Greeting;
```

### useState Hook with TypeScript

```typescript
import React, { useState } from "react";

interface User {
  name: string;
  email: string;
}

const UserForm: React.FC = () => {
  const [user, setUser] = useState<User>({ name: "", email: "" });
  const [count, setCount] = useState<number>(0);

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    console.log(user);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={user.name}
        onChange={(e: React.ChangeEvent<HTMLInputElement>) =>
          setUser({ ...user, name: e.target.value })
        }
      />
      <input
        type="email"
        value={user.email}
        onChange={(e: React.ChangeEvent<HTMLInputElement>) =>
          setUser({ ...user, email: e.target.value })
        }
      />
      <button type="submit">Submit</button>
    </form>
  );
};
```

### useEffect Hook with TypeScript

```typescript
import React, { useState, useEffect } from "react";

interface Post {
  id: number;
  title: string;
  body: string;
}

const PostList: React.FC = () => {
  const [posts, setPosts] = useState<Post[]>([]);
  const [loading, setLoading] = useState<boolean>(true);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then(res => res.json())
      .then((data: Post[]) => {
        setPosts(data);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <ul>
      {posts.map(post => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  );
};
```

### useRef Hook with TypeScript

```typescript
import React, { useRef, useEffect } from "react";

const FocusInput: React.FC = () => {
  const inputRef = useRef<HTMLInputElement>(null);

  useEffect(() => {
    inputRef.current?.focus();
  }, []);

  return <input ref={inputRef} type="text" />;
};
```

### Custom Hooks with TypeScript

```typescript
import { useState, useEffect } from "react";

function useFetch<T>(url: string): {
  data: T | null;
  loading: boolean;
  error: Error | null;
} {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<Error | null>(null);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then((data: T) => {
        setData(data);
        setLoading(false);
      })
      .catch((err: Error) => {
        setError(err);
        setLoading(false);
      });
  }, [url]);

  return { data, loading, error };
}

// Usage
interface User {
  id: number;
  name: string;
}

const UserComponent: React.FC = () => {
  const { data, loading, error } = useFetch<User[]>(
    "https://api.example.com/users"
  );

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return (
    <ul>
      {data?.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
};
```

### Event Handlers with TypeScript

```typescript
import React from "react";

const EventExample: React.FC = () => {
  const handleClick = (e: React.MouseEvent<HTMLButtonElement>) => {
    console.log("Button clicked", e.currentTarget);
  };

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    console.log("Input changed", e.target.value);
  };

  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    console.log("Form submitted");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input onChange={handleChange} />
      <button onClick={handleClick}>Submit</button>
    </form>
  );
};
```

### Exercise: Todo App with React and TypeScript

Create a complete todo application:

`src/types/todo.ts`:

```typescript
export interface Todo {
  id: number;
  text: string;
  completed: boolean;
}

export type FilterType = "all" | "active" | "completed";
```

`src/components/TodoItem.tsx`:

```typescript
import React from "react";
import { Todo } from "../types/todo";

interface TodoItemProps {
  todo: Todo;
  onToggle: (id: number) => void;
  onDelete: (id: number) => void;
}

const TodoItem: React.FC<TodoItemProps> = ({ todo, onToggle, onDelete }) => {
  return (
    <li style={{ textDecoration: todo.completed ? "line-through" : "none" }}>
      <input
        type="checkbox"
        checked={todo.completed}
        onChange={() => onToggle(todo.id)}
      />
      <span>{todo.text}</span>
      <button onClick={() => onDelete(todo.id)}>Delete</button>
    </li>
  );
};

export default TodoItem;
```

`src/components/TodoList.tsx`:

```typescript
import React, { useState } from "react";
import { Todo, FilterType } from "../types/todo";
import TodoItem from "./TodoItem";

const TodoList: React.FC = () => {
  const [todos, setTodos] = useState<Todo[]>([]);
  const [input, setInput] = useState<string>("");
  const [filter, setFilter] = useState<FilterType>("all");

  const addTodo = () => {
    if (input.trim()) {
      const newTodo: Todo = {
        id: Date.now(),
        text: input,
        completed: false
      };
      setTodos([...todos, newTodo]);
      setInput("");
    }
  };

  const toggleTodo = (id: number) => {
    setTodos(
      todos.map(todo =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
      )
    );
  };

  const deleteTodo = (id: number) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };

  const filteredTodos = todos.filter(todo => {
    if (filter === "active") return !todo.completed;
    if (filter === "completed") return todo.completed;
    return true;
  });

  return (
    <div>
      <h1>Todo List</h1>
      <input
        value={input}
        onChange={(e: React.ChangeEvent<HTMLInputElement>) =>
          setInput(e.target.value)
        }
        onKeyPress={(e: React.KeyboardEvent) =>
          e.key === "Enter" && addTodo()
        }
      />
      <button onClick={addTodo}>Add</button>

      <div>
        <button onClick={() => setFilter("all")}>All</button>
        <button onClick={() => setFilter("active")}>Active</button>
        <button onClick={() => setFilter("completed")}>Completed</button>
      </div>

      <ul>
        {filteredTodos.map(todo => (
          <TodoItem
            key={todo.id}
            todo={todo}
            onToggle={toggleTodo}
            onDelete={deleteTodo}
          />
        ))}
      </ul>
    </div>
  );
};

export default TodoList;
```

---

## 13. Testing with Jest

### Setting Up Jest with TypeScript

```bash
npm install --save-dev jest @types/jest ts-jest
```

Generate Jest configuration:

```bash
npx ts-jest config:init
```

This creates `jest.config.js`:

```javascript
module.exports = {
  preset: "ts-jest",
  testEnvironment: "node"
};
```

Add test script to `package.json`:

```json
{
  "scripts": {
    "test": "jest",
    "test:watch": "jest --watch"
  }
}
```

### Writing Basic Tests

`src/math.ts`:

```typescript
export function add(a: number, b: number): number {
  return a + b;
}

export function subtract(a: number, b: number): number {
  return a - b;
}

export function multiply(a: number, b: number): number {
  return a * b;
}

export function divide(a: number, b: number): number {
  if (b === 0) {
    throw new Error("Division by zero");
  }
  return a / b;
}
```

`src/math.test.ts`:

```typescript
import { add, subtract, multiply, divide } from "./math";

describe("Math operations", () => {
  test("adds two numbers", () => {
    expect(add(2, 3)).toBe(5);
    expect(add(-1, 1)).toBe(0);
  });

  test("subtracts two numbers", () => {
    expect(subtract(5, 3)).toBe(2);
    expect(subtract(0, 5)).toBe(-5);
  });

  test("multiplies two numbers", () => {
    expect(multiply(3, 4)).toBe(12);
    expect(multiply(-2, 3)).toBe(-6);
  });

  test("divides two numbers", () => {
    expect(divide(10, 2)).toBe(5);
    expect(divide(7, 2)).toBe(3.5);
  });

  test("throws error on division by zero", () => {
    expect(() => divide(10, 0)).toThrow("Division by zero");
  });
});
```

### Testing Async Functions

`src/api.ts`:

```typescript
export async function fetchUser(id: number): Promise<{ id: number; name: string }> {
  const response = await fetch(`https://api.example.com/users/${id}`);
  if (!response.ok) throw new Error(`HTTP ${response.status}`);
  const body: unknown = await response.json();
  if (typeof body !== "object" || body === null) throw new Error("Invalid user response");
  const candidate = body as { id?: unknown; name?: unknown };
  if (typeof candidate.id !== "number" || typeof candidate.name !== "string")
    throw new Error("Invalid user response");
  return { id: candidate.id, name: candidate.name };
}
```

`src/api.test.ts`:

```typescript
import { fetchUser } from "./api";

global.fetch = jest.fn();

describe("API functions", () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  test("fetches user data", async () => {
    const mockUser = { id: 1, name: "Alice" };
    (fetch as jest.Mock).mockResolvedValue({
      json: async () => mockUser
    });

    const user = await fetchUser(1);
    expect(user).toEqual(mockUser);
    expect(fetch).toHaveBeenCalledWith("https://api.example.com/users/1");
  });
});
```

### Testing Classes

`src/user-service.ts`:

```typescript
interface User {
  id: number;
  name: string;
  email: string;
}

export class UserService {
  private users: User[] = [];

  addUser(user: User): void {
    this.users.push(user);
  }

  getUser(id: number): User | undefined {
    return this.users.find(u => u.id === id);
  }

  getAllUsers(): User[] {
    return [...this.users];
  }

  deleteUser(id: number): boolean {
    const index = this.users.findIndex(u => u.id === id);
    if (index === -1) return false;
    this.users.splice(index, 1);
    return true;
  }
}
```

`src/user-service.test.ts`:

```typescript
import { UserService } from "./user-service";

describe("UserService", () => {
  let service: UserService;

  beforeEach(() => {
    service = new UserService();
  });

  test("adds a user", () => {
    const user = { id: 1, name: "Alice", email: "alice@example.com" };
    service.addUser(user);
    expect(service.getUser(1)).toEqual(user);
  });

  test("gets all users", () => {
    const user1 = { id: 1, name: "Alice", email: "alice@example.com" };
    const user2 = { id: 2, name: "Bob", email: "bob@example.com" };
    service.addUser(user1);
    service.addUser(user2);
    expect(service.getAllUsers()).toEqual([user1, user2]);
  });

  test("deletes a user", () => {
    const user = { id: 1, name: "Alice", email: "alice@example.com" };
    service.addUser(user);
    expect(service.deleteUser(1)).toBe(true);
    expect(service.getUser(1)).toBeUndefined();
  });

  test("returns false when deleting non-existent user", () => {
    expect(service.deleteUser(999)).toBe(false);
  });
});
```

### Mocking Modules

`src/logger.ts`:

```typescript
export class Logger {
  log(message: string): void {
    console.log(`[LOG]: ${message}`);
  }

  error(message: string): void {
    console.error(`[ERROR]: ${message}`);
  }
}
```

`src/service.ts`:

```typescript
import { Logger } from "./logger";

export class Service {
  constructor(private logger: Logger) {}

  performAction(): void {
    this.logger.log("Action performed");
  }
}
```

`src/service.test.ts`:

```typescript
import { Service } from "./service";
import { Logger } from "./logger";

jest.mock("./logger");

describe("Service", () => {
  test("logs action", () => {
    const mockLogger = new Logger() as jest.Mocked<Logger>;
    mockLogger.log = jest.fn();

    const service = new Service(mockLogger);
    service.performAction();

    expect(mockLogger.log).toHaveBeenCalledWith("Action performed");
  });
});
```

### Exercise: Testing Practice

Create comprehensive tests for a shopping cart:

`src/shopping-cart.ts`:

```typescript
interface Product {
  id: number;
  name: string;
  price: number;
}

interface CartItem extends Product {
  quantity: number;
}

export class ShoppingCart {
  private items: CartItem[] = [];

  addItem(product: Product, quantity: number = 1): void {
    const existingItem = this.items.find(item => item.id === product.id);
    if (existingItem) {
      existingItem.quantity += quantity;
    } else {
      this.items.push({ ...product, quantity });
    }
  }

  removeItem(productId: number): void {
    this.items = this.items.filter(item => item.id !== productId);
  }

  updateQuantity(productId: number, quantity: number): void {
    const item = this.items.find(item => item.id === productId);
    if (item) {
      if (quantity <= 0) {
        this.removeItem(productId);
      } else {
        item.quantity = quantity;
      }
    }
  }

  getTotal(): number {
    return this.items.reduce((sum, item) => sum + item.price * item.quantity, 0);
  }

  getItemCount(): number {
    return this.items.reduce((sum, item) => sum + item.quantity, 0);
  }

  clear(): void {
    this.items = [];
  }

  getItems(): CartItem[] {
    return [...this.items];
  }
}
```

`src/shopping-cart.test.ts`:

```typescript
import { ShoppingCart } from "./shopping-cart";

describe("ShoppingCart", () => {
  let cart: ShoppingCart;
  const product1 = { id: 1, name: "Product 1", price: 10 };
  const product2 = { id: 2, name: "Product 2", price: 20 };

  beforeEach(() => {
    cart = new ShoppingCart();
  });

  test("adds items to cart", () => {
    cart.addItem(product1);
    expect(cart.getItemCount()).toBe(1);
    expect(cart.getTotal()).toBe(10);
  });

  test("increases quantity when adding same item", () => {
    cart.addItem(product1, 2);
    cart.addItem(product1, 1);
    expect(cart.getItemCount()).toBe(3);
    expect(cart.getTotal()).toBe(30);
  });

  test("removes items from cart", () => {
    cart.addItem(product1);
    cart.addItem(product2);
    cart.removeItem(1);
    expect(cart.getItemCount()).toBe(1);
    expect(cart.getTotal()).toBe(20);
  });

  test("updates item quantity", () => {
    cart.addItem(product1, 2);
    cart.updateQuantity(1, 5);
    expect(cart.getItemCount()).toBe(5);
    expect(cart.getTotal()).toBe(50);
  });

  test("removes item when quantity updated to zero", () => {
    cart.addItem(product1);
    cart.updateQuantity(1, 0);
    expect(cart.getItemCount()).toBe(0);
  });

  test("calculates correct total with multiple items", () => {
    cart.addItem(product1, 2);
    cart.addItem(product2, 3);
    expect(cart.getTotal()).toBe(80);
  });

  test("clears cart", () => {
    cart.addItem(product1);
    cart.addItem(product2);
    cart.clear();
    expect(cart.getItemCount()).toBe(0);
    expect(cart.getTotal()).toBe(0);
  });
});
```

---

## 14. Migrating from JavaScript to TypeScript

### Step-by-Step Migration Process

#### Step 1: Add TypeScript to Project

```bash
npm install --save-dev typescript @types/node
npx tsc --init
```

#### Step 2: Configure tsconfig.json for Migration

```json
{
  "compilerOptions": {
    "target": "ES2023",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "lib": ["ES2023"],
    "allowJs": true,
    "checkJs": false,
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": false,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "resolveJsonModule": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

#### Step 3: Rename Files Incrementally

Start with `.js` to `.ts` and `.jsx` to `.tsx` for files with the least dependencies.

#### Step 4: Add Type Annotations Gradually

Before:

```javascript
function greet(name) {
  return `Hello, ${name}!`;
}

const user = {
  id: 1,
  name: "Alice"
};
```

After:

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

interface User {
  id: number;
  name: string;
}

const user: User = {
  id: 1,
  name: "Alice"
};
```

#### Step 5: Enable Strict Mode Gradually

Once most files are converted, enable strict checks:

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictPropertyInitialization": true
  }
}
```

### Common Migration Patterns

#### Handling any Types

```typescript
// Temporary during migration
function processData(data: any) {
  return data;
}

// Better approach
function processData(data: unknown) {
  if (typeof data === "string") {
    return data.toUpperCase();
  }
  return data;
}
```

#### Converting Classes

Before:

```javascript
class Calculator {
  constructor() {
    this.result = 0;
  }

  add(value) {
    this.result += value;
    return this;
  }

  getResult() {
    return this.result;
  }
}
```

After:

```typescript
class Calculator {
  private result: number = 0;

  add(value: number): this {
    this.result += value;
    return this;
  }

  getResult(): number {
    return this.result;
  }
}
```

#### Handling External Libraries

Install type definitions:

```bash
npm install --save-dev @types/express @types/lodash
```

For libraries without types, create declaration files:

`src/types/my-library.d.ts`:

```typescript
declare module "my-library" {
  export function doSomething(value: string): void;
}
```

### Exercise: Migration Practice

Convert this JavaScript module to TypeScript:

Before (`config.js`):

```javascript
const defaultConfig = {
  port: 3000,
  host: "localhost",
  database: {
    url: "mongodb://localhost:27017",
    name: "myapp"
  }
};

function createConfig(overrides) {
  return {
    ...defaultConfig,
    ...overrides,
    database: {
      ...defaultConfig.database,
      ...(overrides.database || {})
    }
  };
}

module.exports = { createConfig, defaultConfig };
```

After (`config.ts`):

```typescript
interface DatabaseConfig {
  url: string;
  name: string;
}

interface Config {
  port: number;
  host: string;
  database: DatabaseConfig;
}

const defaultConfig: Config = {
  port: 3000,
  host: "localhost",
  database: {
    url: "mongodb://localhost:27017",
    name: "myapp"
  }
};

function createConfig(overrides: Partial<Config> = {}): Config {
  return {
    ...defaultConfig,
    ...overrides,
    database: {
      ...defaultConfig.database,
      ...(overrides.database || {})
    }
  };
}

export { createConfig, defaultConfig };
```

---

## 15. Best Practices and Configuration

### Strict Mode Configuration

Enable strict mode for maximum type safety:

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictBindCallApply": true,
    "strictPropertyInitialization": true,
    "noImplicitThis": true,
    "alwaysStrict": true
  }
}
```

### Additional Compiler Options

```json
{
  "compilerOptions": {
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true
  }
}
```

### Type Safety Best Practices

#### Avoid any

```typescript
// Bad
function process(data: any) {
  return data.value;
}

// Good
function process(data: unknown) {
  if (typeof data === "object" && data !== null && "value" in data) {
    return (data as { value: unknown }).value;
  }
  throw new Error("Invalid data");
}

// Better
interface DataWithValue {
  value: string;
}

function process(data: DataWithValue) {
  return data.value;
}
```

#### Use Const Assertions

```typescript
const colors = ["red", "green", "blue"] as const;
type Color = typeof colors[number]; // "red" | "green" | "blue"

const config = {
  apiUrl: "https://api.example.com",
  timeout: 5000
} as const;
```

#### Choose Interfaces and Type Aliases Deliberately

```typescript
// Interfaces support declaration merging and are convenient for extendable object contracts.
interface User {
  id: number;
  name: string;
}

// Type aliases express unions, tuples, primitives, mapped/conditional types, and closed models.
type ID = string | number;
type EntityWithId = { id: ID } & { createdAt: Date };
```

#### Use Discriminated Unions for States

```typescript
type LoadingState = { status: "loading" };
type SuccessState<T> = { status: "success"; data: T };
type ErrorState = { status: "error"; error: Error };

type AsyncState<T> = LoadingState | SuccessState<T> | ErrorState;

function handleState<T>(state: AsyncState<T>) {
  switch (state.status) {
    case "loading":
      console.log("Loading...");
      break;
    case "success":
      console.log("Data:", state.data);
      break;
    case "error":
      console.log("Error:", state.error.message);
      break;
  }
}
```

#### Leverage Type Guards

```typescript
function isString(value: unknown): value is string {
  return typeof value === "string";
}

function isNumber(value: unknown): value is number {
  return typeof value === "number";
}

function process(value: unknown) {
  if (isString(value)) {
    console.log(value.toUpperCase());
  } else if (isNumber(value)) {
    console.log(value.toFixed(2));
  }
}
```

### Project Structure Best Practices

```
src/
├── types/
│   ├── index.ts
│   ├── user.ts
│   └── product.ts
├── services/
│   ├── userService.ts
│   └── productService.ts
├── utils/
│   ├── validation.ts
│   └── formatting.ts
├── controllers/
│   ├── userController.ts
│   └── productController.ts
├── routes/
│   ├── index.ts
│   ├── userRoutes.ts
│   └── productRoutes.ts
└── index.ts
```

### Code Organization

Use barrel exports in `index.ts` files:

```typescript
// types/index.ts
export * from "./user";
export * from "./product";

// Usage elsewhere
import { User, Product } from "./types";
```

### Error Handling

```typescript
class AppError extends Error {
  constructor(
    public message: string,
    public statusCode: number,
    public isOperational: boolean = true
  ) {
    super(message);
    Object.setPrototypeOf(this, AppError.prototype);
  }
}

class ValidationError extends AppError {
  constructor(message: string) {
    super(message, 400);
  }
}

class NotFoundError extends AppError {
  constructor(message: string) {
    super(message, 404);
  }
}

function handleError(error: Error): void {
  if (error instanceof AppError) {
    console.log(`[${error.statusCode}] ${error.message}`);
  } else {
    console.log("Unexpected error:", error);
  }
}
```

### Exercise: Best Practices Implementation

Create a type-safe API client:

```typescript
// types.ts
export interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

export interface User {
  id: number;
  username: string;
  email: string;
}

export interface CreateUserDto {
  username: string;
  email: string;
  password: string;
}

// api-client.ts
type Decoder<T> = (input: unknown) => T;

function decodeUser(input: unknown): User {
  if (typeof input !== "object" || input === null) throw new Error("Invalid user");
  const value = input as Record<string, unknown>;
  if (typeof value.id !== "number" || typeof value.username !== "string" ||
      typeof value.email !== "string") throw new Error("Invalid user");
  return { id: value.id, username: value.username, email: value.email };
}

function decodeResponse<T>(decodeData: Decoder<T>): Decoder<ApiResponse<T>> {
  return input => {
    if (typeof input !== "object" || input === null) throw new Error("Invalid response");
    const value = input as Record<string, unknown>;
    if (typeof value.status !== "number" || typeof value.message !== "string")
      throw new Error("Invalid response envelope");
    return { data: decodeData(value.data), status: value.status, message: value.message };
  };
}

class ApiClient {
  constructor(private baseUrl: string) {}

  private async request<T>(
    endpoint: string,
    decode: Decoder<T>,
    options?: RequestInit
  ): Promise<T> {
    const url = `${this.baseUrl}${endpoint}`;
    const response = await fetch(url, options);

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}: ${response.statusText}`);
    }

    const body: unknown = await response.json();
    return decode(body);
  }

  async get<T>(endpoint: string, decode: Decoder<T>): Promise<T> {
    return this.request(endpoint, decode);
  }

  async post<T, U>(endpoint: string, body: U, decode: Decoder<T>): Promise<T> {
    return this.request(endpoint, decode, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(body)
    });
  }

  async put<T, U>(endpoint: string, body: U, decode: Decoder<T>): Promise<T> {
    return this.request(endpoint, decode, {
      method: "PUT",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(body)
    });
  }

  async delete(endpoint: string): Promise<void> {
    const response = await fetch(`${this.baseUrl}${endpoint}`, { method: "DELETE" });
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
  }
}

// user-service.ts
class UserService {
  constructor(private client: ApiClient) {}

  async getUsers(): Promise<User[]> {
    const response = await this.client.get(
      "/users",
      decodeResponse(input => {
        if (!Array.isArray(input)) throw new Error("Invalid users");
        return input.map(decodeUser);
      })
    );
    return response.data;
  }

  async getUser(id: number): Promise<User> {
    const response = await this.client.get(`/users/${id}`, decodeResponse(decodeUser));
    return response.data;
  }

  async createUser(dto: CreateUserDto): Promise<User> {
    const response = await this.client.post("/users", dto, decodeResponse(decodeUser));
    return response.data;
  }

  async deleteUser(id: number): Promise<void> {
    await this.client.delete(`/users/${id}`);
  }
}

// Usage
const client = new ApiClient("https://api.example.com");
const userService = new UserService(client);

async function main() {
  const users = await userService.getUsers();
  console.log(users);

  const newUser = await userService.createUser({
    username: "alice",
    email: "alice@example.com",
    password: "secret123"
  });
  console.log(newUser);
}
```

---

## 16. Capstone Project

Build a learning-scale Task Management API with authentication, an in-memory repository, and integration tests. Chapter 28 evolves it into a production architecture with validated contracts and persistent adapters.

### Project Setup

```bash
mkdir task-manager-api
cd task-manager-api
npm init -y
npm install express bcrypt jsonwebtoken dotenv zod
npm install --save-dev typescript @types/express @types/node @types/bcrypt @types/jsonwebtoken ts-node nodemon jest @types/jest ts-jest supertest @types/supertest
npx tsc --init
```

### Project Structure

```
task-manager-api/
├── src/
│   ├── types/
│   │   └── index.ts
│   ├── models/
│   │   ├── User.ts
│   │   └── Task.ts
│   ├── services/
│   │   ├── AuthService.ts
│   │   └── TaskService.ts
│   ├── middleware/
│   │   ├── auth.ts
│   │   └── errorHandler.ts
│   ├── routes/
│   │   ├── auth.ts
│   │   └── tasks.ts
│   ├── utils/
│   │   └── validation.ts
│   ├── app.ts
│   └── server.ts
├── tests/
│   ├── auth.test.ts
│   └── tasks.test.ts
├── .env
├── tsconfig.json
├── jest.config.js
└── package.json
```

### Implementation

`src/types/index.ts` (the schemas validate untrusted runtime input; the inferred types prevent drift):

```typescript
import { z } from "zod";

export interface User {
  id: number;
  username: string;
  email: string;
  password: string;
  createdAt: Date;
}

export interface Task {
  id: number;
  userId: number;
  title: string;
  description: string;
  status: TaskStatus;
  priority: TaskPriority;
  dueDate?: Date;
  createdAt: Date;
  updatedAt: Date;
}

export enum TaskStatus {
  TODO = "TODO",
  IN_PROGRESS = "IN_PROGRESS",
  DONE = "DONE"
}

export enum TaskPriority {
  LOW = "LOW",
  MEDIUM = "MEDIUM",
  HIGH = "HIGH"
}

export const CreateUserSchema = z.object({
  username: z.string().trim().min(3).max(50),
  email: z.string().email(),
  password: z.string().min(12).max(200)
}).strict();
export type CreateUserDto = z.infer<typeof CreateUserSchema>;

export const LoginSchema = z.object({
  email: z.string().email(),
  password: z.string().min(1).max(200)
}).strict();
export type LoginDto = z.infer<typeof LoginSchema>;

export const CreateTaskSchema = z.object({
  title: z.string().trim().min(1).max(200),
  description: z.string().max(10_000),
  status: z.nativeEnum(TaskStatus).optional(),
  priority: z.nativeEnum(TaskPriority).optional(),
  dueDate: z.coerce.date().optional()
}).strict();
export type CreateTaskDto = z.infer<typeof CreateTaskSchema>;

export const UpdateTaskSchema = CreateTaskSchema.partial();
export type UpdateTaskDto = z.infer<typeof UpdateTaskSchema>;

export interface AuthRequest extends Express.Request {
  user?: { id: number; email: string };
}
```

`src/models/User.ts`:

```typescript
import { User, CreateUserDto } from "../types";

export class UserModel {
  private users: User[] = [];
  private nextId = 1;

  create(dto: CreateUserDto): User {
    const user: User = {
      id: this.nextId++,
      ...dto,
      createdAt: new Date()
    };
    this.users.push(user);
    return user;
  }

  findByEmail(email: string): User | undefined {
    return this.users.find(u => u.email === email);
  }

  findById(id: number): User | undefined {
    return this.users.find(u => u.id === id);
  }
}
```

`src/models/Task.ts`:

```typescript
import { Task, CreateTaskDto, UpdateTaskDto, TaskStatus, TaskPriority } from "../types";

export class TaskModel {
  private tasks: Task[] = [];
  private nextId = 1;

  create(userId: number, dto: CreateTaskDto): Task {
    const task: Task = {
      id: this.nextId++,
      userId,
      title: dto.title,
      description: dto.description,
      status: dto.status || TaskStatus.TODO,
      priority: dto.priority || TaskPriority.MEDIUM,
      dueDate: dto.dueDate,
      createdAt: new Date(),
      updatedAt: new Date()
    };
    this.tasks.push(task);
    return task;
  }

  findByUserId(userId: number): Task[] {
    return this.tasks.filter(t => t.userId === userId);
  }

  findById(id: number): Task | undefined {
    return this.tasks.find(t => t.id === id);
  }

  update(id: number, dto: UpdateTaskDto): Task | undefined {
    const task = this.findById(id);
    if (!task) return undefined;

    Object.assign(task, dto, { updatedAt: new Date() });
    return task;
  }

  delete(id: number): boolean {
    const index = this.tasks.findIndex(t => t.id === id);
    if (index === -1) return false;
    this.tasks.splice(index, 1);
    return true;
  }
}
```

`src/services/AuthService.ts`:

```typescript
import bcrypt from "bcrypt";
import jwt from "jsonwebtoken";
import { UserModel } from "../models/User";
import { CreateUserDto, LoginDto } from "../types";

export class AuthService {
  private readonly jwtSecret: string;

  constructor(private userModel: UserModel) {
    const secret = process.env.JWT_SECRET;
    if (!secret || secret.length < 32) {
      throw new Error("JWT_SECRET must be configured with at least 32 characters");
    }
    this.jwtSecret = secret;
  }

  async register(dto: CreateUserDto): Promise<{ token: string }> {
    const existingUser = this.userModel.findByEmail(dto.email);
    if (existingUser) {
      throw new Error("User already exists");
    }

    const hashedPassword = await bcrypt.hash(dto.password, 10);
    const user = this.userModel.create({
      ...dto,
      password: hashedPassword
    });

    const token = jwt.sign({ id: user.id, email: user.email }, this.jwtSecret, {
      expiresIn: "7d"
    });

    return { token };
  }

  async login(dto: LoginDto): Promise<{ token: string }> {
    const user = this.userModel.findByEmail(dto.email);
    if (!user) {
      throw new Error("Invalid credentials");
    }

    const isValidPassword = await bcrypt.compare(dto.password, user.password);
    if (!isValidPassword) {
      throw new Error("Invalid credentials");
    }

    const token = jwt.sign({ id: user.id, email: user.email }, this.jwtSecret, {
      expiresIn: "7d"
    });

    return { token };
  }

  verifyToken(token: string): { id: number; email: string } {
    try {
      return jwt.verify(token, this.jwtSecret) as { id: number; email: string };
    } catch {
      throw new Error("Invalid token");
    }
  }
}
```

`src/services/TaskService.ts`:

```typescript
import { TaskModel } from "../models/Task";
import { CreateTaskDto, UpdateTaskDto, Task } from "../types";

export class TaskService {
  constructor(private taskModel: TaskModel) {}

  createTask(userId: number, dto: CreateTaskDto): Task {
    return this.taskModel.create(userId, dto);
  }

  getUserTasks(userId: number): Task[] {
    return this.taskModel.findByUserId(userId);
  }

  getTask(id: number, userId: number): Task {
    const task = this.taskModel.findById(id);
    if (!task) {
      throw new Error("Task not found");
    }
    if (task.userId !== userId) {
      throw new Error("Unauthorized");
    }
    return task;
  }

  updateTask(id: number, userId: number, dto: UpdateTaskDto): Task {
    const task = this.getTask(id, userId);
    const updated = this.taskModel.update(id, dto);
    if (!updated) {
      throw new Error("Failed to update task");
    }
    return updated;
  }

  deleteTask(id: number, userId: number): void {
    this.getTask(id, userId);
    const deleted = this.taskModel.delete(id);
    if (!deleted) {
      throw new Error("Failed to delete task");
    }
  }
}
```

`src/middleware/auth.ts`:

```typescript
import { Response, NextFunction } from "express";
import { AuthRequest } from "../types";
import { AuthService } from "../services/AuthService";

export function authMiddleware(authService: AuthService) {
  return (req: AuthRequest, res: Response, next: NextFunction): void => {
    const authHeader = req.headers.authorization;
    if (!authHeader || !authHeader.startsWith("Bearer ")) {
      res.status(401).json({ error: "No token provided" });
      return;
    }

    const token = authHeader.substring(7);
    try {
      const decoded = authService.verifyToken(token);
      req.user = decoded;
      next();
    } catch {
      res.status(401).json({ error: "Invalid token" });
    }
  };
}
```

`src/middleware/errorHandler.ts`:

```typescript
import { Request, Response, NextFunction } from "express";

export function errorHandler(
  err: Error,
  req: Request,
  res: Response,
  next: NextFunction
): void {
  console.error(err.stack);
  res.status(500).json({ error: "Internal server error" });
}
```

`src/routes/auth.ts`:

```typescript
import { Router, Request, Response } from "express";
import { AuthService } from "../services/AuthService";
import { CreateUserSchema, LoginSchema } from "../types";

export function createAuthRouter(authService: AuthService): Router {
  const router = Router();

  router.post("/register", async (req: Request, res: Response) => {
    try {
      const dto = CreateUserSchema.parse(req.body);
      const result = await authService.register(dto);
      res.status(201).json(result);
    } catch (error) {
      res.status(400).json({ error: error instanceof Error ? error.message : "Invalid request" });
    }
  });

  router.post("/login", async (req: Request, res: Response) => {
    try {
      const dto = LoginSchema.parse(req.body);
      const result = await authService.login(dto);
      res.json(result);
    } catch (error) {
      res.status(401).json({ error: error instanceof Error ? error.message : "Authentication failed" });
    }
  });

  return router;
}
```

`src/routes/tasks.ts`:

```typescript
import { Router, Response } from "express";
import { TaskService } from "../services/TaskService";
import { AuthRequest, CreateTaskSchema, UpdateTaskSchema } from "../types";

export function createTaskRouter(taskService: TaskService): Router {
  const router = Router();

  router.get("/", (req: AuthRequest, res: Response) => {
    try {
      const tasks = taskService.getUserTasks(req.user!.id);
      res.json(tasks);
    } catch (error) {
      res.status(500).json({ error: error instanceof Error ? error.message : "Internal error" });
    }
  });

  router.get("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      const task = taskService.getTask(id, req.user!.id);
      res.json(task);
    } catch (error) {
      res.status(404).json({ error: error instanceof Error ? error.message : "Task not found" });
    }
  });

  router.post("/", (req: AuthRequest, res: Response) => {
    try {
      const dto = CreateTaskSchema.parse(req.body);
      const task = taskService.createTask(req.user!.id, dto);
      res.status(201).json(task);
    } catch (error) {
      res.status(400).json({ error: error instanceof Error ? error.message : "Invalid task" });
    }
  });

  router.put("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      const dto = UpdateTaskSchema.parse(req.body);
      const task = taskService.updateTask(id, req.user!.id, dto);
      res.json(task);
    } catch (error) {
      res.status(400).json({ error: error instanceof Error ? error.message : "Invalid update" });
    }
  });

  router.delete("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      taskService.deleteTask(id, req.user!.id);
      res.status(204).send();
    } catch (error) {
      res.status(400).json({ error: error instanceof Error ? error.message : "Delete failed" });
    }
  });

  return router;
}
```

`src/app.ts`:

```typescript
import express from "express";
import { UserModel } from "./models/User";
import { TaskModel } from "./models/Task";
import { AuthService } from "./services/AuthService";
import { TaskService } from "./services/TaskService";
import { authMiddleware } from "./middleware/auth";
import { errorHandler } from "./middleware/errorHandler";
import { createAuthRouter } from "./routes/auth";
import { createTaskRouter } from "./routes/tasks";

export function createApp() {
  const app = express();

  const userModel = new UserModel();
  const taskModel = new TaskModel();
  const authService = new AuthService(userModel);
  const taskService = new TaskService(taskModel);

  app.use(express.json());

  app.use("/api/auth", createAuthRouter(authService));
  app.use("/api/tasks", authMiddleware(authService), createTaskRouter(taskService));

  app.use(errorHandler);

  return app;
}
```

`src/server.ts`:

```typescript
import dotenv from "dotenv";
import { createApp } from "./app";

dotenv.config();

const app = createApp();
const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

`tests/auth.test.ts`:

```typescript
import request from "supertest";
import { createApp } from "../src/app";

const app = createApp();

describe("Authentication", () => {
  test("registers a new user", async () => {
    const response = await request(app)
      .post("/api/auth/register")
      .send({
        username: "testuser",
        email: "test@example.com",
        password: "password123"
      });

    expect(response.status).toBe(201);
    expect(response.body).toHaveProperty("token");
  });

  test("logs in existing user", async () => {
    await request(app)
      .post("/api/auth/register")
      .send({
        username: "testuser2",
        email: "test2@example.com",
        password: "password123"
      });

    const response = await request(app)
      .post("/api/auth/login")
      .send({
        email: "test2@example.com",
        password: "password123"
      });

    expect(response.status).toBe(200);
    expect(response.body).toHaveProperty("token");
  });

  test("rejects invalid credentials", async () => {
    const response = await request(app)
      .post("/api/auth/login")
      .send({
        email: "nonexistent@example.com",
        password: "wrongpassword"
      });

    expect(response.status).toBe(401);
  });
});
```

`tests/tasks.test.ts`:

```typescript
import request from "supertest";
import { createApp } from "../src/app";

const app = createApp();

describe("Tasks", () => {
  let token: string;

  beforeAll(async () => {
    const response = await request(app)
      .post("/api/auth/register")
      .send({
        username: "taskuser",
        email: "tasks@example.com",
        password: "password123"
      });
    token = response.body.token;
  });

  test("creates a new task", async () => {
    const response = await request(app)
      .post("/api/tasks")
      .set("Authorization", `Bearer ${token}`)
      .send({
        title: "Test Task",
        description: "This is a test task"
      });

    expect(response.status).toBe(201);
    expect(response.body).toHaveProperty("id");
    expect(response.body.title).toBe("Test Task");
  });

  test("gets all user tasks", async () => {
    const response = await request(app)
      .get("/api/tasks")
      .set("Authorization", `Bearer ${token}`);

    expect(response.status).toBe(200);
    expect(Array.isArray(response.body)).toBe(true);
  });

  test("updates a task", async () => {
    const createResponse = await request(app)
      .post("/api/tasks")
      .set("Authorization", `Bearer ${token}`)
      .send({
        title: "Original Title",
        description: "Original description"
      });

    const taskId = createResponse.body.id;

    const updateResponse = await request(app)
      .put(`/api/tasks/${taskId}`)
      .set("Authorization", `Bearer ${token}`)
      .send({
        title: "Updated Title"
      });

    expect(updateResponse.status).toBe(200);
    expect(updateResponse.body.title).toBe("Updated Title");
  });

  test("deletes a task", async () => {
    const createResponse = await request(app)
      .post("/api/tasks")
      .set("Authorization", `Bearer ${token}`)
      .send({
        title: "To Delete",
        description: "This will be deleted"
      });

    const taskId = createResponse.body.id;

    const deleteResponse = await request(app)
      .delete(`/api/tasks/${taskId}`)
      .set("Authorization", `Bearer ${token}`);

    expect(deleteResponse.status).toBe(204);
  });

  test("rejects unauthenticated requests", async () => {
    const response = await request(app).get("/api/tasks");

    expect(response.status).toBe(401);
  });
});
```

`package.json` scripts:

```json
{
  "scripts": {
    "build": "tsc",
    "start": "node dist/server.js",
    "dev": "nodemon --exec ts-node src/server.ts",
    "test": "jest"
  }
}
```

### Running the Project

```bash
npm run dev
npm test
npm run build
npm start
```

### API Testing with curl

```bash
# Register
curl -X POST http://localhost:3000/api/auth/register   -H "Content-Type: application/json"   -d '{"username":"alice","email":"alice@example.com","password":"secret123"}'

# Login
curl -X POST http://localhost:3000/api/auth/login   -H "Content-Type: application/json"   -d '{"email":"alice@example.com","password":"secret123"}'

# Create task
curl -X POST http://localhost:3000/api/tasks   -H "Content-Type: application/json"   -H "Authorization: Bearer YOUR_TOKEN"   -d '{"title":"Learn TypeScript","description":"Complete the guide"}'

# Get all tasks
curl http://localhost:3000/api/tasks   -H "Authorization: Bearer YOUR_TOKEN"
```

---

## 17. TypeScript's Soundness Boundaries and Structural Typing

TypeScript 7 is the current-generation compiler baseline for this section. TypeScript remains a static analyzer for JavaScript: types are erased, JavaScript values keep their runtime semantics, and the compiler intentionally permits several unsound operations for ecosystem usability. Follow the [official TypeScript announcements](https://devblogs.microsoft.com/typescript/) and migration guidance when pinning a concrete version.

### Types Are Erased

An annotation neither converts nor validates a value:

```typescript
type User = { id: string; name: string };

const value: unknown = JSON.parse(input);
// const user = value as User; // assertion: no runtime check
const user = parseUser(value); // validation creates evidence
```

Treat file contents, environment variables, database rows, message queues, `fetch().json()`, and request bodies as `unknown` until validated.

### Structural Compatibility

Types are compatible by shape, not declaration name:

```typescript
type UserId = string;
type OrderId = string;
declare const orderId: OrderId;
const userId: UserId = orderId; // allowed: both are string
```

Use a brand when mixing structurally identical identifiers is dangerous:

```typescript
declare const userIdBrand: unique symbol;
type UserId = string & { readonly [userIdBrand]: true };

function userId(raw: string): UserId {
  if (!/^usr_[a-z0-9]+$/.test(raw)) throw new Error("invalid user id");
  return raw as UserId; // assertion is localized behind validation
}
```

Brands are compile-time distinctions, not runtime wrappers. Serialize them as their underlying value and validate again when reading.

### Freshness and Excess Properties

Fresh object literals receive excess-property checks, while assigned variables use ordinary structural compatibility:

```typescript
type Point = { x: number; y: number };
// const p: Point = { x: 1, y: 2, colour: "red" }; // excess property
const candidate = { x: 1, y: 2, colour: "red" };
const p: Point = candidate; // compatible; extra fields exist at runtime
```

Do not interpret a type as an exact object schema. Use runtime `.strict()` validation where unknown keys must be rejected.

### Variance and Mutable Arrays

Function-parameter checking, callbacks, methods, and mutable containers have subtle variance rules. Prefer `readonly T[]` for inputs that are not modified:

```typescript
class Animal { kind = "animal"; }
class Dog extends Animal { bark() {} }

function countAnimals(values: readonly Animal[]): number {
  return values.length;
}
```

`readonly` prevents mutation through this reference; it does not deep-freeze the runtime array.

### Professional Checklist

- Keep `any` at audited interoperability shims; use `unknown` at boundaries.
- Minimize non-null assertions and `as`; document the proof behind each.
- Distinguish compile-time immutability from runtime freezing.
- Turn on `noUncheckedIndexedAccess` and `exactOptionalPropertyTypes` deliberately.

### Exercise: Boundary Audit

Search a project for `as`, `any`, `!`, `JSON.parse`, `response.json()`, and `process.env`. Classify each occurrence as trusted internal construction or an unvalidated boundary, then replace one unsafe assertion with validation.

---

## 18. Control-Flow Analysis and Exhaustive Domain Models

### Narrowing Tools

TypeScript narrows through `typeof`, `instanceof`, equality, property checks, discriminants, truthiness, predicates, and assertion functions. Narrow the smallest value possible and avoid mutating discriminants after narrowing.

```typescript
function normalize(value: string | string[] | null): string[] {
  if (value === null) return [];
  return typeof value === "string" ? [value] : value;
}
```

Truthiness is not always validity: `if (value)` drops `0`, `""`, and `false`. Test `value !== undefined` when absence—not falsiness—is the concern.

### Predicates and Assertion Functions

```typescript
function isError(value: unknown): value is Error {
  return value instanceof Error;
}

function assertDefined<T>(value: T, message = "missing value"):
  asserts value is NonNullable<T> {
  if (value === null || value === undefined) throw new Error(message);
}
```

A predicate is a promise made by its implementation. Test it like a parser; a lying predicate creates unsoundness everywhere it is used.

### Exhaustiveness with `never`

```typescript
type Command =
  | { kind: "create"; title: string }
  | { kind: "complete"; id: string }
  | { kind: "delete"; id: string };

function assertNever(value: never): never {
  throw new Error(`Unhandled command: ${JSON.stringify(value)}`);
}

function handle(command: Command): void {
  switch (command.kind) {
    case "create": return create(command.title);
    case "complete": return complete(command.id);
    case "delete": return remove(command.id);
    default: return assertNever(command);
  }
}
```

This turns addition of a union member into compile errors at every exhaustive consumer.

### Model States, Not Flags

```typescript
type RequestState<T> =
  | { status: "idle" }
  | { status: "loading"; startedAt: number }
  | { status: "success"; data: T; receivedAt: number }
  | { status: "failure"; error: AppError; retryable: boolean };
```

This prevents impossible combinations such as `loading: true` with both `data` and `error` populated.

### Exercise: Workflow State Machine

Model a payment as `draft → authorized → captured` with explicit failed/cancelled states. Write exhaustive transition and rendering functions. Add a `refunded` state and confirm every required consumer fails to compile until updated.

---

## 19. Professional Type-Level Programming

Advanced types should reduce invalid runtime states and duplication—not become a second programming language for its own sake.

### `satisfies` and Literal Preservation

```typescript
type RouteName = "home" | "tasks";
type Route = { path: `/${string}`; auth: boolean };

const routes = {
  home: { path: "/", auth: false },
  tasks: { path: "/tasks", auth: true }
} satisfies Record<RouteName, Route>;

type TaskPath = typeof routes.tasks.path; // "/tasks", not string
```

An annotation changes the variable's apparent type; `satisfies` checks compatibility while preserving useful inference.

### Const Type Parameters

```typescript
function tuple<const T extends readonly unknown[]>(...values: T): T {
  return values;
}
const columns = tuple("id", "title", "status");
// readonly ["id", "title", "status"]
```

### Conditional Types, Distribution, and `infer`

```typescript
type AwaitedValue<T> = T extends PromiseLike<infer U> ? AwaitedValue<U> : T;
type ElementOf<T> = T extends readonly (infer U)[] ? U : never;

type Distributed<T> = T extends unknown ? { value: T } : never;
type NotDistributed<T> = [T] extends [unknown] ? { value: T } : never;
```

A conditional type distributes over a naked union type parameter. Bracketing both sides suppresses distribution.

### Mapped Types and Key Remapping

```typescript
type Getters<T> = {
  [K in keyof T as `get${Capitalize<string & K>}`]: () => T[K]
};

type MutableRequired<T> = {
  -readonly [K in keyof T]-?: T[K]
};
```

### Controlling Inference

Use `NoInfer<T>` when one parameter must be checked against a type inferred elsewhere:

```typescript
function choose<C extends string>(choices: readonly C[], defaultValue: NoInfer<C>): C {
  return choices.includes(defaultValue) ? defaultValue : choices[0]!;
}
choose(["red", "blue"] as const, "red");
// choose(["red", "blue"] as const, "green"); // error
```

### Type Complexity Budget

Deep recursive/distributive types can slow the compiler and produce unusable diagnostics. Name intermediate types, constrain unions, avoid computing types already expressible by code generation, and measure with `tsc --extendedDiagnostics` and a compiler trace when builds regress.

### Modern Decorators

Decorators are runtime functions with compile-time typing. Do not confuse the modern ECMAScript decorator model with the older `experimentalDecorators`/metadata ecosystem; frameworks may require one specific mode.

```typescript
function logged<This, Args extends unknown[], Return>(
  original: (this: This, ...args: Args) => Return,
  context: ClassMethodDecoratorContext<This, (this: This, ...args: Args) => Return>
) {
  return function (this: This, ...args: Args): Return {
    console.debug({ method: String(context.name) }, "called");
    return original.call(this, ...args);
  };
}

class Worker {
  @logged
  run(jobId: string): number { return jobId.length; }
}
```

Decorators can affect initialization order, identity, metadata, tree-shaking, and testing. Keep domain rules in ordinary code; use decorators for narrow cross-cutting integration when the runtime contract is understood.

### Explicit Resource Management

Objects implementing `Symbol.dispose` or `Symbol.asyncDispose` can be bound with `using`/`await using`, providing deterministic cleanup when the configured runtime supports the emitted protocol:

```typescript
await using transaction = await database.beginTransaction();
await transaction.execute(command);
await transaction.commit();
// async disposal runs on success, failure, or early return
```

Disposal does not automatically mean rollback after commit; define idempotent lifecycle semantics and test suppressed/combined failures. Confirm runtime and downlevel-helper compatibility before publishing a library that exposes this syntax.

### Exercise: Typed Event Protocol

Create an event map whose keys become `onX` subscription methods through key remapping. Add compile-time tests for correct payloads and ensure unknown event names fail.

---

## 20. ESM, Module Resolution, and Package Boundaries

TypeScript does not decide how a runtime loads modules; it must model Node.js, a bundler, or another host. The [official module reference](https://www.typescriptlang.org/docs/handbook/modules/reference) is the authority for compatibility-sensitive details.

### Node Applications

```json
// package.json
{ "type": "module" }
```

```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2023",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "verbatimModuleSyntax": true,
    "strict": true
  }
}
```

Under Node ESM, relative imports use the runtime extension:

```typescript
import type { Task } from "./task.js";
import { createTask } from "./service.js";
```

Use `.mts`/`.cts` only when a file must force ESM/CJS independently of the package default. Do not choose `module: esnext` for a Node application merely because output looks like ESM; `NodeNext` also models Node resolution and package conditions.

### Bundled Applications

For Vite/esbuild/Rollup/Webpack-style builds, `moduleResolution: "Bundler"`, `module: "ESNext"`, and `noEmit: true` commonly model the bundler while another tool emits JavaScript. Test that the bundler and TypeScript resolve identical files and aliases.

### Type-Only Imports

`import type` documents erasure and prevents an accidental runtime edge. With `verbatimModuleSyntax`, what you write has predictable emit behavior.

### Package Exports

```json
{
  "name": "@acme/tasks",
  "type": "module",
  "exports": {
    ".": { "types": "./dist/index.d.ts", "import": "./dist/index.js" },
    "./testing": { "types": "./dist/testing.d.ts", "import": "./dist/testing.js" }
  },
  "types": "./dist/index.d.ts"
}
```

`exports` is an encapsulation boundary. Test a packed tarball from an external consumer rather than importing internal `src/` paths in a monorepo.

### Exercise: ESM Diagnosis

Create a Node ESM package, deliberately omit `.js` from a relative import, then use `tsc --traceResolution` to explain the failure. Add an exported subpath and verify it from a separate consumer.

---

## 21. tsconfig Architecture, Project References, and Monorepos

### Strict Application Baseline

```json
{
  "compilerOptions": {
    "target": "ES2023",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    "useUnknownInCatchVariables": true,
    "noImplicitOverride": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "verbatimModuleSyntax": true,
    "isolatedModules": true,
    "sourceMap": true,
    "declaration": true
  }
}
```

`skipLibCheck` can reduce time and tolerate duplicate ecosystem declarations, but it also suppresses errors inside `.d.ts` files. It does not make application code safer; document why it is enabled.

### Project References

Large repositories should encode build boundaries:

```json
// tsconfig.json
{
  "files": [],
  "references": [
    { "path": "./packages/domain" },
    { "path": "./packages/api" },
    { "path": "./apps/web" }
  ]
}
```

Referenced packages enable `composite`, declarations, incremental metadata, and `tsc -b`. References are not a substitute for package exports; keep source and distribution boundaries aligned.

### Separate Type-Check and Emit

Many frontend systems use `tsc --noEmit` for analysis and a bundler for output. Libraries need declaration emit and should test emitted `.d.ts`. Node applications may emit with `tsc`, swc, esbuild, or a runtime loader—but only one tool should own each transformation responsibility.

### Performance Diagnostics

Use:

```bash
npx tsc -b --verbose
npx tsc --extendedDiagnostics
npx tsc --generateTrace .trace
```

Common problems include enormous unions, distributive recursive conditionals, duplicated library versions, one giant project, and including generated/test data unintentionally.

### Exercise: Three-Package Workspace

Build `domain → api → web` with project references. Prove that the domain cannot import infrastructure, and compare clean versus incremental build time.

---

## 22. Runtime Validation, Serialization, and API Contracts

### Parse, Don't Cast

```typescript
import { z } from "zod";

const TaskSchema = z.object({
  id: z.string().uuid(),
  title: z.string().trim().min(1).max(200),
  status: z.enum(["todo", "doing", "done"]),
  dueAt: z.string().datetime().transform(value => new Date(value))
}).strict();

type Task = z.infer<typeof TaskSchema>;

function parseTask(input: unknown): Task {
  return TaskSchema.parse(input);
}
```

Validation libraries differ in bundle size, inference, coercion, error format, JSON Schema support, and performance. The architectural rule is independent of library: one executable schema owns the runtime boundary and the static type is derived or checked against it.

### Typed `fetch` Is Not Validated `fetch`

```typescript
async function getTask(id: string, signal?: AbortSignal): Promise<Task> {
  const response = await fetch(`/api/tasks/${encodeURIComponent(id)}`, { signal });
  if (!response.ok) throw new HttpError(response.status, await response.text());
  const body: unknown = await response.json();
  return TaskSchema.parse(body);
}
```

`fetch<Task>()`, `response.json() as Task`, and Axios generics only describe an expectation. They do not prove the server obeyed it.

### Serialization Is a Contract

JSON loses `Date`, `Map`, `Set`, `bigint`, `undefined`, prototypes, and object identity. Define wire types separately from domain types and perform explicit conversion.

```typescript
type TaskWire = { id: string; dueAt: string | null };
type TaskDomain = { id: TaskId; dueAt: Date | null };
```

Version durable events and stored records. Prefer additive evolution, reject unknown incompatible versions, and test old fixtures against new readers.

### Environment Validation

```typescript
const EnvSchema = z.object({
  NODE_ENV: z.enum(["development", "test", "production"]),
  DATABASE_URL: z.string().url(),
  JWT_SECRET: z.string().min(32)
});
export const env = EnvSchema.parse(process.env);
```

Validate once at startup; do not scatter `process.env.X!` across the codebase.

### Exercise: Contract Failure Matrix

Test missing fields, unknown fields, wrong primitives, invalid dates, oversized text, malformed JSON, non-2xx responses, timeouts, and client cancellation. Confirm every failure becomes a stable application error rather than an unchecked cast.

---

## 23. Async Systems, Cancellation, Streams, and Errors

### Promise Semantics

An `async` function always returns a promise. `await` pauses that async continuation, not the JavaScript thread. Independent work should be started together; sequential `await` accidentally serializes it.

```typescript
const [user, tasks] = await Promise.all([
  getUser(userId, signal),
  getTasks(userId, signal)
]);
```

`Promise.all` fails fast but does not cancel other operations. Use a shared `AbortSignal` and make every participating operation honor it.

### Structured Cancellation and Deadlines

```typescript
async function withTimeout<T>(
  milliseconds: number,
  operation: (signal: AbortSignal) => Promise<T>
): Promise<T> {
  const controller = new AbortController();
  const timer = setTimeout(() => controller.abort(new Error("deadline exceeded")), milliseconds);
  try {
    return await operation(controller.signal);
  } finally {
    clearTimeout(timer);
  }
}
```

Propagate a caller's signal as well as internal deadlines in production. Clean up listeners and timers in `finally` blocks.

### Concurrency Limits and Backpressure

Starting a promise for every item can exhaust sockets or memory. Process bounded batches or use a concurrency limiter. Streams communicate backpressure so producers do not outrun consumers.

```typescript
import { pipeline } from "node:stream/promises";
import { createReadStream, createWriteStream } from "node:fs";
import { createGzip } from "node:zlib";

await pipeline(
  createReadStream("events.ndjson"),
  createGzip(),
  createWriteStream("events.ndjson.gz"),
  { signal }
);
```

### Error Taxonomy

```typescript
type AppError =
  | { kind: "validation"; issues: readonly string[] }
  | { kind: "not-found"; resource: string; id: string }
  | { kind: "conflict"; code: string }
  | { kind: "dependency"; service: string; retryable: boolean; cause: unknown };
```

Throwing is convenient within imperative layers; explicit `Result<T,E>` is useful when failure is an expected branch callers must handle. Preserve `cause`, never assume a caught value is `Error`, and translate internal failures at process/API boundaries without leaking secrets.

### Retries and Idempotency

Retry only transient failures, with capped exponential backoff and jitter. A timeout does not prove the server did nothing; unsafe retries can duplicate writes. Use idempotency keys or naturally idempotent operations and set a total deadline.

### Exercise: Resilient Batch Client

Implement a client with a concurrency limit, deadline, caller cancellation, retry classification, jitter, and an idempotency key. Test it with fake timers and a deterministic failing transport.

---

## 24. Application Architecture and Domain Modeling

### Keep Dependencies Pointing Inward

```text
HTTP/CLI/worker → application use cases → domain
database/message broker ────────────────┘ (through ports)
```

The domain should not import Express, an ORM, React, or environment variables. Framework adapters validate external data and translate it into domain commands.

### Domain Values and Invariants

```typescript
declare const taskIdSymbol: unique symbol;
type TaskId = string & { readonly [taskIdSymbol]: true };

class Task {
  private constructor(
    readonly id: TaskId,
    private title: string,
    private status: "todo" | "done"
  ) {}

  static create(id: TaskId, title: string): Task {
    const normalized = title.trim();
    if (!normalized) throw new DomainError("task.title.empty");
    return new Task(id, normalized, "todo");
  }

  complete(): void {
    if (this.status === "done") return; // idempotent transition
    this.status = "done";
  }
}
```

Do not create setters for invariants. Expose operations named in the domain and make invalid transitions impossible or explicit failures.

### Ports and Adapters

```typescript
interface TaskRepository {
  findById(id: TaskId): Promise<Task | null>;
  save(task: Task): Promise<void>;
}

class CompleteTask {
  constructor(private readonly tasks: TaskRepository) {}
  async execute(id: TaskId): Promise<void> {
    const task = await this.tasks.findById(id);
    if (!task) throw new NotFoundError("task", id);
    task.complete();
    await this.tasks.save(task);
  }
}
```

Dependency injection can be plain constructor injection. A container is optional; hidden service locators and global singletons make tests and lifetimes harder.

### Transactions and Concurrency

Static types cannot prevent lost updates. Use database constraints, transactions, optimistic versions, idempotency, and outbox/inbox patterns where consistency crosses process boundaries. Model these failures in application contracts.

### Frontend Boundaries

Keep server wire schemas separate from UI state. Model remote state with discriminated unions, isolate query/cache libraries behind hooks, and never share secret-bearing server modules with browser bundles merely because TypeScript allows the import.

### Exercise: Replace the In-Memory Model

Define repository ports for the original capstone and implement both in-memory and SQL adapters. Run the same contract test suite against each. Add an optimistic version and test conflicting updates.

---

## 25. Testing Runtime Behavior and Types

### A Testing Portfolio

- Unit tests exercise pure domain behavior.
- Contract tests verify every adapter implements a port consistently.
- Integration tests cover databases, HTTP serialization, and migrations.
- End-to-end tests cover a few critical user journeys.
- Property-based tests explore invariants over generated inputs.
- Type tests lock public inference and rejected usages.

Test behavior, not private implementation calls. Excessive mocking produces tests that agree with mocks rather than production.

### Property-Based Testing

```typescript
import fc from "fast-check";

test("decode(encode(x)) preserves values", () => {
  fc.assert(fc.property(taskArbitrary, task => {
    expect(decodeTask(encodeTask(task))).toEqual(task);
  }));
});
```

Properties are powerful for parsers, serializers, state machines, sort/order logic, and algebraic utilities. Shrinking turns a large failure into a small counterexample.

### Type-Level Tests

Use `tsd`, `expect-type`, or checked fixture projects. For local negative tests, `@ts-expect-error` must include a reason and should fail when the expected error disappears.

```typescript
import { expectTypeOf } from "expect-type";

expectTypeOf(routes.tasks.path).toEqualTypeOf<"/tasks">();
// @ts-expect-error -- user ids cannot be passed where task ids are required
completeTask(userId);
```

Avoid `@ts-ignore`: it remains silent when the underlying issue is fixed.

### Testing Time and Concurrency

Inject clocks and ID generators. Use fake timers for scheduling logic, but keep integration coverage with real timers and abort signals. Assert that cancellation releases resources and that rejected promises are observed.

### Coverage and Mutation

Line coverage does not prove useful assertions. Track branch coverage for state machines and validation failures; mutation testing can reveal tests that execute code without detecting incorrect behavior.

### Exercise: Testing Pyramid

Add unit, property, repository-contract, HTTP integration, and type tests for one task workflow. Deliberately break validation, persistence, and inference to confirm each layer detects the appropriate regression.

---

## 26. Authoring and Publishing TypeScript Libraries

### Design the Public Surface First

Export the smallest stable API. Do not expose internal conditional types, dependency-specific classes, or source paths accidentally. Use an explicit `index.ts` and package `exports`; avoid a barrel that causes cycles or makes every internal module public.

### Declaration Emit

```json
{
  "compilerOptions": {
    "declaration": true,
    "declarationMap": true,
    "emitDeclarationOnly": true,
    "stripInternal": true,
    "composite": true
  }
}
```

Inspect generated `.d.ts` files as deliverables. A library can run correctly while emitting unusable or non-portable declarations.

### Declaration Authoring Patterns

Understand global, UMD, CommonJS, ESM, module augmentation, callable objects, and generic classes before hand-writing `.d.ts`. Never declare a dependency more precisely than its runtime behavior. Use `unknown` when the contract is unknown.

```typescript
declare module "legacy-parser" {
  export interface Options { strict?: boolean }
  export function parse(input: string, options?: Options): unknown;
}
```

Module augmentation adds declarations but cannot create runtime members. Pair augmentation with the code that actually installs the behavior.

### Compatibility and SemVer

Type changes can be breaking even without JavaScript changes: narrowing accepted input, widening output, changing generic defaults, modifying overload order, or altering inference may break consumers. Test against supported TypeScript versions and representative consumer fixtures.

### Dual-Package Hazards

Publishing both CJS and ESM can create two copies of stateful modules and complex declaration routing. Prefer one format when possible. If dual publishing is required, test `import` and `require` consumers, conditional exports, singleton behavior, and Node/bundler resolution separately.

### Release Verification

```bash
npm pack --dry-run
npm pack
# install the tarball into clean ESM and bundler fixtures
```

Check files, source maps, license, exports, types, side-effects metadata, provenance, and minimum runtime before publishing.

### Exercise: Publishable Validation Package

Extract task schemas and domain IDs into a small ESM package. Generate declarations, expose one testing subpath, pack it, and compile clean external consumers without workspace path aliases.

---

## 27. Performance, Security, and Production Operations

### Compiler Performance

Prefer named types and simple public signatures over enormous inferred declarations. Split project references by stable ownership, deduplicate dependencies, avoid unconstrained distributive conditionals, and establish a type-check time budget in CI. TypeScript 7's native compiler improves throughput, but pathological type design still affects diagnostics and editor usability.

### Runtime Performance

Types disappear, so optimize JavaScript behavior: algorithmic complexity, allocation, object shapes, serialization, I/O, database queries, and event-loop blocking. Benchmark production builds with representative data. Do not rewrite readable code based on assumptions about erased types.

### Security Boundaries

- Validate and size-limit all external input.
- Use parameterized queries and database constraints.
- Never use `eval` for calculators, templates, or configuration.
- Fail startup when secrets are missing; do not ship fallback secrets.
- Hash passwords with a current password-hashing algorithm and an explicit cost policy.
- Verify JWT algorithm, issuer, audience, expiry, rotation, and revocation requirements.
- Apply authorization to the resource, not merely authentication to the route.
- Prevent prototype-pollution paths when merging untrusted objects.
- Pin/lock dependencies, audit releases, and minimize install scripts.

### Observability

Use structured logs with request/job correlation IDs and redaction. Emit metrics for latency, throughput, error classes, saturation, queue depth, and dependency health. Trace work across service boundaries. Keep PII and credentials out of logs and error responses.

```typescript
type LogContext = {
  requestId: string;
  userId?: string;
  operation: string;
};
logger.info({ ...context, durationMs }, "task completed");
```

### Graceful Shutdown

Stop accepting work, signal cancellation, drain with a deadline, close servers/queues/pools, flush telemetry, and exit non-zero when shutdown fails. Test SIGTERM behavior; container orchestration assumes it works.

### Migrations and Deployment

Use backward-compatible expand/migrate/contract database and event-schema changes. A rolling deployment runs old and new versions simultaneously. Type checking one revision cannot prove cross-version compatibility.

### Exercise: Production Readiness Review

Threat-model the task API. Add environment validation, body limits, authorization tests, structured redacted logs, health/readiness endpoints, graceful shutdown, and a dependency/database failure drill.

---

## 28. Professional Capstone: A Validated Task Platform

The original capstone demonstrates routing, services, authentication, and tests. This professional version removes its production gaps: unvalidated bodies, fallback secrets, in-memory-only persistence, domain/framework coupling, unchecked token assertions, and missing package/build boundaries.

### Repository Shape

```text
task-platform/
├── package.json
├── tsconfig.json
├── packages/
│   ├── contracts/       # executable wire schemas, no server secrets
│   ├── domain/          # Task aggregate and repository ports
│   ├── application/     # use cases, errors, clock/id ports
│   ├── persistence/     # SQL repository, migrations, transaction adapter
│   └── observability/   # logging/tracing interfaces
├── apps/
│   ├── api/             # HTTP adapter and composition root
│   ├── worker/          # outbox consumer and retries
│   └── web/             # React client consuming contracts
├── tests/
│   ├── contracts/
│   ├── integration/
│   └── e2e/
└── tooling/             # shared tsconfig, lint, CI scripts
```

### Contract Package

```typescript
import { z } from "zod";

export const TaskIdSchema = z.string().uuid().brand<"TaskId">();
export const CreateTaskSchema = z.object({
  title: z.string().trim().min(1).max(200),
  description: z.string().max(10_000).default("")
}).strict();

export const TaskResponseSchema = z.object({
  id: TaskIdSchema,
  title: z.string(),
  status: z.enum(["todo", "done"]),
  version: z.number().int().nonnegative(),
  createdAt: z.string().datetime()
});

export type CreateTaskInput = z.infer<typeof CreateTaskSchema>;
export type TaskResponse = z.infer<typeof TaskResponseSchema>;
```

### HTTP Adapter

```typescript
app.post("/tasks", authenticate, async (req, res, next) => {
  try {
    const input = CreateTaskSchema.parse(req.body);
    const output = await createTask.execute({
      actorId: req.auth.userId,
      input,
      idempotencyKey: req.get("Idempotency-Key") ?? undefined
    });
    res.status(201).json(TaskResponseSchema.parse(output));
  } catch (error: unknown) {
    next(error);
  }
});
```

The route validates input and output. The use case owns authorization and idempotency policy. The error middleware maps a closed application-error union to stable public responses and logs the original cause privately.

### Persistence Contract

```typescript
interface UnitOfWork {
  tasks: TaskRepository;
  outbox: Outbox;
  commit(): Promise<void>;
  rollback(): Promise<void>;
}

interface TaskRepository {
  get(id: TaskId): Promise<Task | null>;
  insert(task: Task): Promise<void>;
  save(task: Task, expectedVersion: number): Promise<"saved" | "conflict">;
}
```

Creating a task and writing its integration event occur in one transaction. A worker later publishes the outbox record with retries and deduplication.

### Required Test Matrix

- Domain unit and state-machine property tests.
- Schema fixtures for valid, invalid, oversized, and backward-compatible payloads.
- Repository contract tests against memory and real database adapters.
- HTTP integration tests for validation, authn, authz, idempotency, conflict, and redaction.
- Type tests for branded IDs and public package inference.
- Worker tests for retry, poison messages, cancellation, and duplicate delivery.
- Packed-package consumer builds under supported TypeScript versions.
- Load test with p95/p99 latency, event-loop delay, database saturation, and error budget.

### CI and Definition of Done

```text
install --frozen lockfile
→ format/lint
→ tsc -b
→ type tests
→ unit/property tests
→ integration tests with ephemeral database
→ build + npm pack + consumer fixtures
→ dependency/security scan
→ container smoke test + graceful-shutdown test
```

The capstone is complete when a clean checkout can build, test, package, migrate, start, serve a documented workflow, shut down safely, and reproduce the results using committed commands. “It type-checks” is only one gate.

### Final Challenges

1. Add cursor pagination whose opaque cursor is runtime validated and versioned.
2. Add optimistic concurrency with `If-Match` and prove conflicts do not lose updates.
3. Generate OpenAPI from the executable schemas and contract-test a client.
4. Add an outbox worker with bounded concurrency, cancellation, retries, and metrics.
5. Publish the contracts package and consume its packed tarball from both Node ESM and Vite.
6. Migrate one package to TypeScript 7, recording compiler-time and compatibility differences.

---

## Conclusion

You have now completed a comprehensive journey through TypeScript, from basic types to advanced patterns and real-world application development. This guide covered:

- Core type system and annotations
- Functions, classes, and interfaces
- Advanced type features including generics, mapped types, and conditional types
- Integration with popular frameworks and libraries
- Testing strategies with Jest
- Migration patterns from JavaScript
- Best practices and strict configuration
- Structural typing, soundness boundaries, narrowing, and exhaustive models
- ESM/NodeNext resolution, package exports, declarations, and monorepo builds
- Runtime schemas, async cancellation, architecture, and error contracts
- Runtime, integration, property-based, and type-level testing
- Library publishing, performance diagnostics, security, and operations
- A professional capstone with persistence ports, outbox processing, CI, and release criteria

Continue practicing by building more projects, exploring TypeScript documentation, and contributing to open-source TypeScript projects. TypeScript is continuously evolving, so stay updated with new features and community best practices.
