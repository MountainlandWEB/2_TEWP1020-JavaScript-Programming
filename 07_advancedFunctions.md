
# 07: Advanced Functions (Iterators, Closures), Error Handling and Debugging

#### [Table of Contents](#table-of-contents)

  - [1. Advanced Functions (common)](#1-advanced-functions-common)
    - [Iterators](#iterators)
      - [In-class Exercise #1](#in-class-exercise-1)
    - [Closures](#closures)
      - [In-class Exercise #2](#in-class-exercise-2)
    - [Higher-order Functions](#higher-order-functions)
      - [In-class Exercise #3](#in-class-exercise-3)
  - [2. Error Handling Best Practices](#2-error-handling-best-practices)
    - [Use try-catch Blocks](#use-try-catch-blocks)
      - [In-class Exercise #4](#in-class-exercise-4)
    - [Throwing Custom Errors](#throwing-custom-errors)
      - [In-class Exercise #5](#in-class-exercise-5)
    - [Error Propagation](#error-propagation)
      - [In-class Exercise #6](#in-class-exercise-6)
  - [3. Debugging Techniques](#3-debugging-techniques)
    - [Console Logging](#console-logging)
      - [In-class Exercise #7](#in-class-exercise-7)
    - [Debugger Statement](#debugger-statement)
      - [In-class Exercise #8](#in-class-exercise-8)
    - [Browser DevTools and Node.js Debugger](#browser-devtools-and-nodejs-debugger)
      - [In-class Exercise #9](#in-class-exercise-9)

## 1. Advanced Functions (common)

<details open>
<summary>Parable of Advanced Functions</summary>

> To understand the concept of advanced functions, let's consider a simple parable about a coach and their team of players. 
>
> ![alt text](https://pikwizard.com/pw/medium/195f8abf1c07f0d9e6ff5a83910cb891.jpg)
> 
> The coach represents a **higher-order function**, capable of strategizing and assigning roles to players (inner functions). 
> 
> These players have access to the coach's playbook and training, akin to the tools and knowledge passed down by the coach (**closures**), enabling them to execute their roles effectively on the field. 
> 
> As the players work together under the guidance of the coach, they move dynamically across the field, passing, dribbling, and shooting (**iterating**), 
> 
> refining their techniques and tactics with each play. Ultimately, through teamwork and coordination, the coach, players, and their collaborative efforts exemplify the principles of iterators, closures, and higher-order functions in action on the sports field.

</details>

### Iterators

<details open>
<summary>How can you iterate over elements in JavaScript?</summary>

> Iterating over elements in JavaScript can be achieved using iterators. An iterator is an object that provides a way to access elements sequentially.

> ```javascript
> // Example of iterating over elements using array iterator
> const numbers = [1, 2, 3, 4, 5];
> const iterator = numbers[Symbol.iterator]();
>
> let result = iterator.next();
> while (!result.done) {
>   console.log(result.value);
>   result = iterator.next();
> }
> ```

</details>

#### In-class Exercise #1

<details open>
<summary>Exercise: iterators</summary>

> Practice Exercise: Write a JavaScript function called `printArray` that takes an array as input and logs each element of the array to the console using iteration.
>```javascript
>// Exercise: iterator
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ``` javascript
> function printArray(arr) {
>   for (let i = 0; i < arr.length; i++) {
>     console.log(arr[i]);
>   }
> } 
>
> // Test the function
> const numbers = [1, 2, 3, 4, 5];
> printArray(numbers);
>

</details>

### Closures


<details open>
<summary>How do closures work in JavaScript?</summary>

> Closures in JavaScript allow inner functions to access variables from their outer scope, even after the outer function has finished executing. This is because the inner function maintains a reference to its lexical environment.
>
> ```javascript
> // Example of closure in JavaScript
> function outer() {
>   const message = 'Hello';
>
>   function inner() {
>     console.log(message);
>   }
>
>   return inner;
> }
>
> const innerFunction = outer();
> innerFunction(); // Output: Hello
> ```
>
>### Example 1: Counter Function
>
> Closures can be used to create private variables. In the following example, the `counter` function returns another function that, when called, increments and returns the count.
>
> ```javascript
> function counter() {
>   let count = 0;
>   return function () {
>     return ++count;
>   };
> }
>
> const increment = counter();
> console.log(increment()); // Output: 1
> console.log(increment()); // Output: 2
> ```
>
>### Example 2: Memoization
>
> Closures are often used in memoization, a technique to cache expensive function calls. In the example below, the `memoizedAdd` function memoizes the result of adding two numbers, returning the cached result if the same inputs are provided again.
>
> ```javascript
> function memoizedAdd() {
>   const cache = {};
>   return function (a, b) {
>     const key = a + '-' + b;
>     if (key in cache) {
>       console.log('Fetching from cache');
>       return cache[key];
>     } else {
>       console.log('Calculating result');
>       const result = a + b;
>       cache[key] = result;
>       return result;
>     }
>   };
> }
>
> const add = memoizedAdd();
> console.log(add(2, 3)); // Output: Calculating result, 5
> console.log(add(2, 3)); // Output: Fetching from cache, 5
> ```
>
>### Example 3: Event Handlers
>
> Closures can capture variables in event handler functions, preserving their values even after the outer function has finished executing. In the example below, each button click logs its corresponding index, thanks to the closure capturing the `i` variable.
>
> ```javascript
> function createButtons() {
>   for (let i = 0; i < 5; i++) {
>     const button = document.createElement('button');
>     button.innerText = 'Button ' + i;
>     button.addEventListener('click', function () {
>       console.log('Button ' + i + ' clicked');
>     });
>     document.body.appendChild(button);
>   }
> }
>
> createButtons();
> ```

</details>



#### In-class Exercise #2

<details open>
<summary>Exercise - Closures</summary>

> **Exercise: Understanding Closures**
>
> Explore the concept of closures through progressively challenging coding examples.
>
> 1. **Basic Closure:**
>
> Define an outer function named `outerFunction` that declares a variable `outerVar`. Within `outerFunction`, define an inner function named `innerFunction` that logs the value of `outerVar` to the console. Finally, return the `innerFunction`.
>
>
> 2. **Closure with Arguments:**
>
> Create a function named `createCounter` that takes a parameter `initialValue`. Inside `createCounter`, define a variable `counter` initialized to `initialValue`. Return an inner function named `increment` that increments `counter` by 1 and logs its value to the console.
>
>
> 3. **Closure with Private Variables:**
>
> Implement a function called `createPerson` that takes two parameters `name` and `age`. Inside `createPerson`, declare two private variables `personName` and `personAge` initialized to the values of `name` and `age`, respectively. Define an inner object named `person` with two methods: `getDetails`, which returns a string containing the person's name and age, and `celebrateBirthday`, which increments the person's age by 1. Return the `person` object.
>
>
> <details>
> <summary>Answers</summary>
>
> 1. **Basic Closure:**
>
> ```javascript
> function outerFunction() {
>   let outerVar = "I am from outer function";
>
>   function innerFunction() {
>     console.log(outerVar);
>   }
>
>   return innerFunction;
> }
>
> let closureFunction = outerFunction();
> closureFunction(); // Output: "I am from outer function"
> ```
>
> 2. **Closure with Arguments:**
>
> ```javascript
> function createCounter(initialValue) {
>   let counter = initialValue;
>
>   function increment() {
>     counter++;
>     console.log(counter);
>   }
>
>   return increment;
> }
>
> let counter1 = createCounter(0);
> counter1(); // Output: 1
> counter1(); // Output: 2
> ```
>
> 3. **Closure with Private Variables:**
>
> ```javascript
> function createPerson(name, age) {
>   let personName = name;
>   let personAge = age;
>
>   let person = {
>     getDetails: function () {
>       return `Name: ${personName}, Age: ${personAge}`;
>     },
>     celebrateBirthday: function () {
>       personAge++;
>       console.log(
>         `Happy birthday, ${personName}! You are now ${personAge} years old.`
>       );
>     },
>   };
>
>   return person;
> }
>
> let person1 = createPerson("Alice", 30);
> console.log(person1.getDetails()); // Output: "Name: Alice, Age: 30"
> person1.celebrateBirthday(); // Output: "Happy birthday, Alice! You are now 31 years old."
> ```
>
> </details>
</details>

### Higher-order Functions


<details open>
<summary>What are higher-order functions and how can you use them?</summary>

> Higher-order functions are functions that can take other functions as arguments or return functions as results. They enable powerful functional programming techniques such as mapping, filtering, and reducing.

> ```javascript
> // Example of higher-order function in JavaScript
> function multiplier(factor) {
>   return function (x) {
>     return x * factor;
>   };
> }
>
> const double = multiplier(2);
> console.log(double(5)); // Output: 10
> ```

</details>

#### In-class Exercise #3

<details open>
<summary>Exercise: higher-order functions</summary>

> Practice Exercise: Write a higher-order function called `transformArray` that takes an array and a transformation function as input, and applies the transformation function to each element of the array.
>```javascript
>// Exercise: higher-order functions
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function transformArray(arr, transformFunc) {
>   const transformedArray = [];
>   for (let i = 0; i < arr.length; i++) {
>     transformedArray.push(transformFunc(arr[i]));
>   }
>   return transformedArray;
> } 
>
> // Test the function
> const numbers = [1, 2, 3, 4, 5];
> const double = num => num * 2;
> const doubledNumbers = transformArray(numbers, double);
> console.log(doubledNumbers);
> ```

</details>

---




## 2. Error Handling Best Practices

> In this section, we'll explore best practices for error handling in JavaScript.

### Use try-catch Blocks

<details open>
<summary>What are try-catch blocks and how do they work?</summary>

> Try-catch blocks are a JavaScript construct used for handling exceptions. The code inside the try block is executed, and if an error occurs, it's caught by the catch block. This allows for graceful error handling and prevents the program from crashing.

> ```javascript
> try {
>   // Code that might throw an error
>   throw new Error('Oops! Something went wrong.');
> } catch (error) {
>   // Handle the error
>   console.error('Error:', error.message);
> }
> ```

</details>

<details open>
<summary>The Parable of Try-Catch Blocks</summary>

> Imagine you're a skilled juggler performing in front of a large audience. You're juggling balls, plates, and even fiery torches with great finesse. Each throw and catch is meticulously planned, but sometimes, despite your best efforts, an unexpected mishap occurs. Maybe a ball slips from your grasp or a plate shatters mid-air.
>
>
>![alt text](https://media.istockphoto.com/id/831679804/photo/woman-juggler.jpg?b=1&s=612x612&w=0&k=20&c=GWGJ9by0ajBTTqZZuk5sGWt73j0t_SwC9QWYY4MyqY4=)
>
> This is where try-catch blocks come into play. Think of the try block as your performance routine – you execute your juggling act with confidence, knowing that you've practiced and prepared well. 
> 
> However, the catch block serves as your safety net. If any of your juggling props go awry and an error (or mishap) occurs, the catch block is there to gracefully handle the situation.
>
> Just like a skilled performer who seamlessly adjusts to unexpected events during a show, try-catch blocks allow your JavaScript code to gracefully handle errors, preventing your program from crashing and providing a smoother experience for users.

</details>

#### In-class Exercise #4

<details open>
<summary>Exercise: try-catch blocks</summary>

> Practice Exercise: Write a JavaScript function called `divide` that takes two numbers as input and returns the result of dividing the first number by the second number. Handle the case where the second number is zero by throwing a custom error.

>```javascript
>// Exercise: try-catch blocks
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function divide(a, b) {
>   try {
>     if (b === 0) {
>       throw new Error('Division by zero is not allowed.');
>     }
>     return a / b;
>   } catch (error) {
>     console.error('Error:', error.message);
>   }
> }
>
> console.log(divide(10, 0)); // Output: Error: Division by zero is not allowed.
> ```

</details>

### Throwing Custom Errors

<details open>
<summary>What are custom errors and when should you throw them?</summary>

> Custom errors, also known as user-defined errors, are instances of the `Error` class that you create yourself. You should throw custom errors when you encounter specific conditions in your code that warrant special handling.

> ```javascript
> // Example of throwing a custom error
> function validateNumber(num) {
>   if (typeof num !== 'number') {
>     throw new Error('Invalid number format.');
>   }
> }
>
> try {
>   validateNumber('abc');
> } catch (error) {
>   console.error('Error:', error.message);
> }
> ```

</details>

#### In-class Exercise #5

<details open>
<summary>Exercise: throwing custom errors</summary>

> Practice Exercise: Write a JavaScript function called `validateEmail` that takes an email address as input and throws a custom error if the email address is not in a valid format.

>```javascript
>// Exercise: throwing custom errors
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function validateEmail(email) {
>   const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
>   if (!emailRegex.test(email)) {
>     throw new Error('Invalid email address.');
>   }
> }
>
> try {
>   validateEmail('invalid-email');
> } catch (error) {
>   console.error('Error:', error.message);
> }
> ```

</details>

### Error Propagation

<details open>
<summary>What is error propagation and why is it important?</summary>

> Error propagation is the process of passing errors up the call stack to higher-level functions or components for handling. It's important because it allows errors to be handled at appropriate levels of abstraction, improving code maintainability and readability.

> ```javascript
> // Example of error propagation
> function fetchData() {
>   try {
>     // Fetch data from API
>   } catch (error) {
>     throw new Error('Failed to fetch data.');
>   }
> }
>
> function processData() {
>   try {
>     fetchData();
>   } catch (error) {
>     console.error('Error:', error.message);
>   }
> }
>
> processData();
> ```

</details>

<details open>
<summary>The Parable of Error Propagation</summary>

> Picture yourself as the captain of a soccer team leading your players through a crucial match. Each player has a specific position and role on the field, contributing to the team's overall performance. As the captain, you're responsible for guiding your team to victory.
>
> Error propagation in programming is akin to leading your soccer team during a match. If one of your players makes a mistake or encounters an obstacle during the game, it's essential for them to communicate that error to you, the captain. This allows you to provide feedback, adjust strategies, and keep the team focused on winning.
>
> ![alt text](https://images.pexels.com/photos/10719279/pexels-photo-10719279.jpeg?auto=compress&cs=tinysrgb&h=627&fit=crop&w=1200)
>
> Just as effective communication between players and the captain is crucial for success on the soccer field, error propagation in programming ensures that errors are communicated up the hierarchy to be addressed by coaches or team leaders. This approach fosters teamwork, maintains momentum, and ultimately leads to better performance.

</details>



#### In-class Exercise #6

<details open>
<summary>Exercise: error propagation</summary>

> Practice Exercise: Write a JavaScript function called `readFile` that simulates reading a file from disk. If the file cannot be read, throw an error. Write another function called `processFile` that calls `readFile` and handles any errors that occur.

>```javascript
>// Exercise: error propagation
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function readFile(filename) {
>   if (filename !== 'example.txt') {
>     throw new Error('File not found.');
>   }
>   // Simulate reading file
>   console.log('Reading file:', filename);
> }
>
> function processFile(filename) {
>   try {
>     readFile(filename);
>   } catch (error) {
>     console.error('Error:', error.message);
>   }
> }
>
> processFile('example.txt'); // Output: Reading file: example.txt
> processFile('invalid.txt'); // Output: Error: File not found.
> ```

</details>


---



## 3. Debugging Techniques

> In this section, we'll explore various debugging techniques in JavaScript.

### Console Logging

<details open>
<summary>What is console logging and how can it help with debugging?</summary>

> Console logging is a technique used to output information to the console during program execution. It can help with debugging by allowing developers to inspect variable values, track the flow of execution, and identify potential errors or unexpected behavior.
>
> ```javascript
> // Example of console logging
> const name = 'John';
> console.log('Hello,', name);
> ```

</details>

#### In-class Exercise #7

<details open>
<summary>Exercise: console logging</summary>

> Practice Exercise: Write a JavaScript function called `calculateArea` that calculates the area of a rectangle given its length and width. Use console logging to output the intermediate steps and the final result.
>
>```javascript
>// Exercise: console logging
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function calculateArea(length, width) {
>   console.log('Calculating area...');
>   console.log('Length:', length);
>   console.log('Width:', width);
>   const area = length * width;
>   console.log('Area:', area);
>   return area;
> }
>
> console.log(calculateArea(5, 3)); // Output: 15
> ```

</details>

### Debugger Statement

<details open>
<summary>What is the debugger statement and how does it work?</summary>

> The debugger statement is a JavaScript keyword used to pause code execution and launch the browser's built-in debugger. It allows developers to step through code, inspect variables, and diagnose issues in real-time.
>
> ```javascript
> // Example of using the debugger statement
> function processInput(input) {
>   debugger;
>   // Code logic here
> }
>
> processInput('test');
> ```

</details>

#### In-class Exercise #8

<details open>
<summary>Exercise: debugger statement</summary>
>
> Practice Exercise: Write a JavaScript function called `findLargestNumber` that takes an array of numbers as input and returns the largest number in the array. Use the debugger statement to debug the function and identify any issues.

>```javascript
>// Exercise: debugger statement
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> function findLargestNumber(numbers) {
>   let largest = numbers[0];
>   debugger;
>   for (let i = 1; i < numbers.length; i++) {
>     if (numbers[i] > largest) {
>       largest = numbers[i];
>     }
>   }
>   return largest;
> }
>
> const numbers = [10, 5, 20, 8, 15];
> console.log(findLargestNumber(numbers)); // Output: 20
> ```

</details>

### Browser DevTools and Node.js Debugger

<details open>
<summary>How can browser DevTools and Node.js debugger aid in debugging?</summary>

> Browser DevTools and the Node.js debugger are powerful tools that provide developers with advanced debugging capabilities. 
> 
> They offer features such as breakpoints, watch expressions, call stacks, and performance profiling, allowing developers to debug code efficiently and effectively.
>
> ```javascript
> // Example of using breakpoints in Chrome DevTools
> function processInput(input) {
>   debugger;
>   // Code logic here
> }
>
> processInput('test');
> ```

</details>

#### In-class Exercise #9

<details open>
<summary>Exercise: browser DevTools and Node.js debugger</summary>

> Practice Exercise: Set up a breakpoint in a JavaScript file using browser DevTools or the Node.js debugger. 
> 
> Step through the code execution and observe how breakpoints can help identify and resolve issues.
>
>```javascript
>// Exercise: browser DevTools and Node.js debugger
>
>```
>
> <details>
> <summary>Answers</summary>
>
> ```javascript
> // Open your browser's DevTools and navigate to the Sources tab
> // Find the JavaScript file you want to debug and set a breakpoint on the desired line
> // Refresh the page or trigger the code execution to reach the breakpoint
> // Use the debugger controls (step into, step over, step out) to navigate through the code
> // Inspect variable values and the call stack to diagnose issues
>
> // Example using Chrome DevTools
> function processInput(input) {
>   debugger;
>   // Code logic here
> }
>
> processInput('test');
> ```

</details>

