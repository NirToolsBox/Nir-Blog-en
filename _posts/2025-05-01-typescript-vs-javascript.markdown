---
layout: post
title: "Comparison between TypeScript and JavaScript"
date: 2025-05-01
category: Development
excerpt: "Discover the key differences between TypeScript and JavaScript."
---

# Introduction

JavaScript and TypeScript are two widely used languages in web development. JavaScript is the base language, while TypeScript is an extension of JavaScript that adds additional features. In this article, we will explore the important differences between these two languages in a simple and clear manner.

<br>

## What is JavaScript?

JavaScript is a programming language primarily used to make web pages interactive. It allows you to add dynamic features to websites, such as animations, interactive forms, and much more. JavaScript is executed directly in the browser, making it very fast and efficient for web applications.

<br>

## What is TypeScript?

TypeScript is a superset of JavaScript developed by Microsoft. It adds static types to JavaScript, which means you can define types for your variables, functions, and objects. This allows errors to be detected before the code is even executed, making development safer and more reliable.

<br>

# Key Differences between TypeScript and JavaScript
<br>

## 1. Static Typing vs Dynamic Typing

* **JavaScript**: Uses dynamic typing. This means you don't need to define the type of a variable in advance. The type is determined during code execution.

```javascript
let message = "Hello, World!";
message = 42; // This is possible in JavaScript

// Another example
let user = "John";
user = { name: "John", age: 30 }; // No error in JavaScript
console.log(user.name); // "John"
```

* **TypeScript**: Uses static typing. You must define the type of a variable when declaring it. This allows type errors to be detected before execution.

```typescript
let message: string = "Hello, World!";
message = 42; // Error: Type 'number' is not assignable to type 'string'

// Another example
let user: string = "John";
user = { name: "John", age: 30 }; // Error: Type '{ name: string; age: number; }' is not assignable to type 'string'
```
<br>

## 2. Error Detection

* **JavaScript**: Errors are often detected at runtime, which can make debugging more difficult.

```javascript
// JavaScript example - Error detected only at runtime
function calculateArea(width, height) {
  return width * heigth; // Typo "heigth" instead of "height"
}

console.log(calculateArea(5, 10)); // Generates an error at runtime: "heigth is not defined"
```

* **TypeScript**: Errors can be detected at compile time, thanks to static typing. This allows errors to be fixed before the application is even launched.

```typescript
// TypeScript example - Error detected at compile time
function calculateArea(width: number, height: number): number {
  return width * heigth; // Compilation error: "Cannot find name 'heigth'"
}

console.log(calculateArea(5, 10));
```
<br>

## 3. Object-Oriented

* **JavaScript**: Although JavaScript supports object-oriented programming, it doesn't have native classes and inheritance (before ES6). You can use constructor functions and prototypes to create objects.

```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log("Hello, " + this.name);
};

let person = new Person("Alice");
person.greet(); // Displays "Hello, Alice"

// Example of inheritance in JavaScript
function Employee(name, position) {
  Person.call(this, name);
  this.position = position;
}

Employee.prototype = Object.create(Person.prototype);
Employee.prototype.constructor = Employee;

Employee.prototype.introduce = function() {
  console.log(`My name is ${this.name} and I am a ${this.position}`);
};

let employee = new Employee("Bob", "developer");
employee.greet(); // "Hello, Bob"
employee.introduce(); // "My name is Bob and I am a developer"
```

* **TypeScript**: TypeScript fully supports classes and inheritance, making object-oriented programming more intuitive and cleaner.

```typescript
class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.log("Hello, " + this.name);
  }
}

let person = new Person("Alice");
person.greet(); // Displays "Hello, Alice"

// Example of inheritance in TypeScript
class Employee extends Person {
  position: string;

  constructor(name: string, position: string) {
    super(name);
    this.position = position;
  }

  introduce() {
    console.log(`My name is ${this.name} and I am a ${this.position}`);
  }
}

let employee = new Employee("Bob", "developer");
employee.greet(); // "Hello, Bob"
employee.introduce(); // "My name is Bob and I am a developer"
```
<br>

## 4. Interfaces

* **JavaScript**: JavaScript doesn't have the concept of interfaces. You can use objects to define structures, but it's not as strict as interfaces.

```javascript
// JavaScript - Using objects as structures
function greet(person) {
  console.log("Hello, " + person.name);
}

let person = { name: "Alice", age: 30 };
greet(person); // Displays "Hello, Alice"

// But nothing prevents passing an incompatible object
greet({ firstName: "Bob" }); // Displays "Hello, undefined" - No error detected
```

* **TypeScript**: TypeScript allows you to define interfaces, enabling you to create contracts for your objects. This makes the code more predictable and easier to understand.

```typescript
interface Person {
  name: string;
  age: number;
}

function greet(person: Person) {
  console.log("Hello, " + person.name);
}

let person: Person = { name: "Alice", age: 30 };
greet(person); // Displays "Hello, Alice"

// Compilation error - Missing 'name' property
greet({ firstName: "Bob" }); // Error: Argument of type '{ firstName: string; }' is not assignable to parameter of type 'Person'.
```
<br>

## 5. Modules

* **JavaScript**: JavaScript supports modules (from ES6), but their usage can be a bit complex.

```javascript
// person.js
export function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log("Hello, " + this.name);
};

// main.js
import { Person } from './person.js';

let person = new Person("Alice");
person.greet(); // Displays "Hello, Alice"
```

* **TypeScript**: TypeScript natively supports modules, making code organization easier and cleaner.

```typescript
// person.ts
export class Person {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.log("Hello, " + this.name);
  }
}

// main.ts
import { Person } from './person';

let person = new Person("Alice");
person.greet(); // Displays "Hello, Alice"
```

<br>

# Conclusion

TypeScript and JavaScript are both powerful languages for web development. JavaScript is more flexible and quicker to learn, while TypeScript offers additional features that make development safer and more reliable. If you're working on a complex project or in a team, TypeScript can be an excellent choice thanks to its static types and advanced features.

If you're a JavaScript developer, consider exploring TypeScript for your next projects. You might be surprised by the productivity gains and code quality you'll achieve.