# TypeScript: From Beginner to Advanced

A comprehensive guide to mastering TypeScript from foundational concepts to advanced patterns and real-world application development.

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

Install TypeScript globally:

```bash
npm install -g typescript
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
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
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

class TypedEventEmitter<T extends Record<string, any>> {
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

  dequeue(): T | undefined {
    return this.items.shift();
  }

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

  calculate(expression: string): number {
    this.history.push(expression);
    return eval(expression);
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
    request(url: string): Promise<any>;
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
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
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
  return response.json();
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
    "target": "ES2020",
    "module": "commonjs",
    "lib": ["ES2020"],
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

#### Prefer Interfaces for Object Types

```typescript
// Good
interface User {
  id: number;
  name: string;
}

// Use type for unions and intersections
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
class ApiClient {
  constructor(private baseUrl: string) {}

  private async request<T>(
    endpoint: string,
    options?: RequestInit
  ): Promise<ApiResponse<T>> {
    const url = `${this.baseUrl}${endpoint}`;
    const response = await fetch(url, options);

    if (!response.ok) {
      throw new Error(`HTTP ${response.status}: ${response.statusText}`);
    }

    return response.json();
  }

  async get<T>(endpoint: string): Promise<ApiResponse<T>> {
    return this.request<T>(endpoint);
  }

  async post<T, U>(endpoint: string, body: U): Promise<ApiResponse<T>> {
    return this.request<T>(endpoint, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(body)
    });
  }

  async put<T, U>(endpoint: string, body: U): Promise<ApiResponse<T>> {
    return this.request<T>(endpoint, {
      method: "PUT",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(body)
    });
  }

  async delete<T>(endpoint: string): Promise<ApiResponse<T>> {
    return this.request<T>(endpoint, { method: "DELETE" });
  }
}

// user-service.ts
class UserService {
  constructor(private client: ApiClient) {}

  async getUsers(): Promise<User[]> {
    const response = await this.client.get<User[]>("/users");
    return response.data;
  }

  async getUser(id: number): Promise<User> {
    const response = await this.client.get<User>(`/users/${id}`);
    return response.data;
  }

  async createUser(dto: CreateUserDto): Promise<User> {
    const response = await this.client.post<User, CreateUserDto>("/users", dto);
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

Build a complete Task Management API with authentication, database integration, and comprehensive testing.

### Project Setup

```bash
mkdir task-manager-api
cd task-manager-api
npm init -y
npm install express bcrypt jsonwebtoken dotenv
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

`src/types/index.ts`:

```typescript
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

export interface CreateUserDto {
  username: string;
  email: string;
  password: string;
}

export interface LoginDto {
  email: string;
  password: string;
}

export interface CreateTaskDto {
  title: string;
  description: string;
  status?: TaskStatus;
  priority?: TaskPriority;
  dueDate?: Date;
}

export interface UpdateTaskDto {
  title?: string;
  description?: string;
  status?: TaskStatus;
  priority?: TaskPriority;
  dueDate?: Date;
}

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
  private jwtSecret = process.env.JWT_SECRET || "secret";

  constructor(private userModel: UserModel) {}

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
  res.status(500).json({ error: err.message || "Internal server error" });
}
```

`src/routes/auth.ts`:

```typescript
import { Router, Request, Response } from "express";
import { AuthService } from "../services/AuthService";
import { CreateUserDto, LoginDto } from "../types";

export function createAuthRouter(authService: AuthService): Router {
  const router = Router();

  router.post("/register", async (req: Request, res: Response) => {
    try {
      const dto: CreateUserDto = req.body;
      const result = await authService.register(dto);
      res.status(201).json(result);
    } catch (error) {
      res.status(400).json({ error: (error as Error).message });
    }
  });

  router.post("/login", async (req: Request, res: Response) => {
    try {
      const dto: LoginDto = req.body;
      const result = await authService.login(dto);
      res.json(result);
    } catch (error) {
      res.status(401).json({ error: (error as Error).message });
    }
  });

  return router;
}
```

`src/routes/tasks.ts`:

```typescript
import { Router, Response } from "express";
import { TaskService } from "../services/TaskService";
import { AuthRequest, CreateTaskDto, UpdateTaskDto } from "../types";

export function createTaskRouter(taskService: TaskService): Router {
  const router = Router();

  router.get("/", (req: AuthRequest, res: Response) => {
    try {
      const tasks = taskService.getUserTasks(req.user!.id);
      res.json(tasks);
    } catch (error) {
      res.status(500).json({ error: (error as Error).message });
    }
  });

  router.get("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      const task = taskService.getTask(id, req.user!.id);
      res.json(task);
    } catch (error) {
      res.status(404).json({ error: (error as Error).message });
    }
  });

  router.post("/", (req: AuthRequest, res: Response) => {
    try {
      const dto: CreateTaskDto = req.body;
      const task = taskService.createTask(req.user!.id, dto);
      res.status(201).json(task);
    } catch (error) {
      res.status(400).json({ error: (error as Error).message });
    }
  });

  router.put("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      const dto: UpdateTaskDto = req.body;
      const task = taskService.updateTask(id, req.user!.id, dto);
      res.json(task);
    } catch (error) {
      res.status(400).json({ error: (error as Error).message });
    }
  });

  router.delete("/:id", (req: AuthRequest, res: Response) => {
    try {
      const id = parseInt(req.params.id);
      taskService.deleteTask(id, req.user!.id);
      res.status(204).send();
    } catch (error) {
      res.status(400).json({ error: (error as Error).message });
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

## Conclusion

You have now completed a comprehensive journey through TypeScript, from basic types to advanced patterns and real-world application development. This guide covered:

- Core type system and annotations
- Functions, classes, and interfaces
- Advanced type features including generics, mapped types, and conditional types
- Integration with popular frameworks and libraries
- Testing strategies with Jest
- Migration patterns from JavaScript
- Best practices and strict configuration
- A complete capstone project demonstrating production-ready patterns

Continue practicing by building more projects, exploring TypeScript documentation, and contributing to open-source TypeScript projects. TypeScript is continuously evolving, so stay updated with new features and community best practices.
