# Introduction to JavaScript Programming
+ Values
  + ``` 42, 3.14, "Hello Friend", true, false, null, undefined, [1,2,3] {name: "kylie"}```
+ Operations
  + string involved in a plus sign that is called concentation, overloaded ... ``` "Jason" + "Snow"
   binary operators + / -
  + unary means 1 - single operand,
  + boolean can only be false or true,
  + double equals operator or loose equality operator - ``` 3.0 == 3``` single = for assignment; double equal ==== is used
  + less than or greater than equal to
  + logical operators - true || false, put two together it will be OR operator  ``` || && ``` 
+ Types
  + typeof 42          >> number
  + typeof "Kyle"      >> string
  + typeof true        >> boolean
  + typeof undefined   >> undefined
  + typeof { age: 39 } >> object
  + typeof null        >> object !?!?
  + typeof [1,2,3]     >> object 
+ Variables
  + ```var name = "Jason Snow"; var age; age = 39; var friends = ["Brandon", "Marc"], console.log(friends.length);console.log(friends[]);
  + ``` 
+ Expressions vs. Statements
+ If & Else
+ Loops
+ Functions

# Types and Coercion
+ Primitive Types
+ NaN
+ new
+ Coercion
+ Booleans
+ Equality

# Scope
+ Scope
+ Undefined vs. Undeclared
+ Function Expressions
+ IIFEs
+ Block Scoping with let
+ Closure

# this & Prototype
+ this
+ Prototype
+ class




# Week 1: Foundations of JavaScript
## Day 1: Chapter 1 – What Is JavaScript?
### Topics:
+ The purpose and history of JavaScript.
+ JavaScript's evolution (ES versions, modern features).
+ What makes JavaScript unique:
  + Dynamic typing
  + Single-threaded, event-driven nature
  + Prototype-based inheritance

Activities:
* Discussion: Where is JavaScript used today? (Browsers, servers, IoT, etc.)

Demo: Running JavaScript in the browser (console and script tags).
* Group brainstorm: Compare JavaScript with other programming languages students may know.

Homework:
* Write a short reflection: Why is JavaScript so widely used?
* Optional: Watch a video on the history of JavaScript (e.g., from ES5 to ES6+).

## Day 2: Chapter 2 – Surveying JS (Part 1: Syntax and Basics)
### Topics:
+ Variables: var, let, const (scoping differences).
+ Primitive data types: string, number, boolean, null, undefined, symbol.
+ Operators: Arithmetic, comparison, logical.
+ Control flow: if/else, switch, for, while.

Activities:
* Hands-on: Write a program that takes user input (via prompt) and processes it.
* Debugging challenge: Fix broken code examples with syntax errors.

Homework:
* Practice problems with variables and loops (e.g., create a multiplication table).
* Read Chapter 2 sections on data types and control flow.

## Day 3: Chapter 2 – Surveying JS (Part 2: Functions and Objects)
Topics:
+  Functions:
+  Function declarations vs. expressions.
+  Arrow functions and this.

Objects:
+  Object literals and properties.
+  Arrays and basic array methods.

Activities:
* Write a function to compute the factorial of a number.
* Create a simple object (e.g., car) and add, update, and delete properties.
* Debugging exercise: Identify issues with functions and objects.

Homework:
* Write a function that processes an array of numbers (e.g., find the max/min).
* Read Chapter 2 sections on functions and objects.

# Day 4: Chapter 3 – Digging to the Roots of JS (Part 1: Type Coercion and Truthiness)
Topics:
Type coercion:
Implicit vs. explicit conversion.
== vs. ===.
Truthy and falsy values.
Activities:
Hands-on: Write a function that evaluates truthy/falsy behavior in different scenarios.
Group challenge: Predict the output of coercion-based examples.
Homework:
Write a program that validates user input (e.g., check if it's truthy or falsy).
Read Chapter 3 sections on type coercion.
Day 5: Chapter 3 – Digging to the Roots of JS (Part 2: Closures and Prototypes)
Topics:
Closures:
How functions “remember” their scope.
Prototypes and inheritance.
Prototype chains.
Object.create() and __proto__.
Activities:
Hands-on: Write a closure-based function (e.g., counter function).
Debugging exercise: Fix incorrect usage of prototypes.
Homework:
Explore closures by creating a function that generates customizable greetings.
Review Chapter 3.
Week 2: Advanced Concepts and Big Picture

Day 6: Chapter 4 – The Bigger Picture (Part 1: JS Engines and Call Stack)
Topics:
How JavaScript runs:
JS engines (e.g., V8, SpiderMonkey).
Parsing, compiling, and interpreting code.
Call stack and execution context.
Activities:
Visualize the call stack with code examples (e.g., nested function calls).
Hands-on: Trace the flow of execution in provided examples.
Homework:
Write a reflection: Why is understanding the call stack important?
Read Chapter 4 sections on JS engines.
Day 7: Chapter 4 – The Bigger Picture (Part 2: Event Loop and Async Basics)
Topics:
Event loop and concurrency model:
setTimeout and setInterval.
Tasks and microtasks.
Basics of asynchronous programming:
Promises and async/await.
Activities:
Hands-on: Write code using setTimeout to simulate a delay.
Debugging challenge: Fix async code with incorrect promise chaining.
Homework:
Rewrite a callback-based function using Promises or async/await.
Day 8: Advanced Practice and Review
Topics:
Review Chapters 1–4: Key concepts and how they connect.
Real-world applications of JavaScript concepts:
Modules and reusability.
Event handling in browsers.
Activities:
Hands-on: Refactor previous homework using modules.
Group quiz: Review key concepts (closures, prototypes, event loop).
Homework:
Start the mini-project: Build a small app (e.g., a to-do list).
Day 9: Mini-Project Development
Topics:
Bringing it all together: Create a project using concepts from Chapters 1–4.
Example project: To-Do App with DOM manipulation and event handling.
Activities:
Hands-on: Write code for the app in small steps.
Peer review: Students share and discuss their implementations.
Homework:
Finalize the project for presentation.
Day 10: Final Assessment and Wrap-Up
Topics:
Assessment of understanding:
Short coding quiz.
Debugging exercise.
Presentation of projects.
Activities:
Students present their projects and share learnings.
Instructor feedback on strengths and areas for improvement.
Wrap-Up:
Discussion: Next steps in learning JavaScript.
Share resources for further study (e.g., MDN, advanced JS books).
Key Features of This Plan
Daily Homework: Reinforces concepts covered in class.
Hands-On Focus: Every session includes coding exercises.
Mini-Project: Provides a practical application of skills.
Flexibility: You can expand or condense topics based on the pace of the group.
