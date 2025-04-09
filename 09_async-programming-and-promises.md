# 09: Asynchronous with Promises

### [Table of Contents](#-table-of-contents)

  - [📰 Review](#-review)
    - [🗓️ Events, Callbacks](#️-events-callbacks)
    - [In-class Exercise #1](#in-class-exercise-1)
    - [In-class Exercise #2](#in-class-exercise-2)
  - [📰 Intro](#-intro)
    - [In-class Exercise #3](#in-class-exercise-3)
  - [⏳ Async vs Synchronous](#-async-vs-synchronous)
    - [In-class Exercise #4](#in-class-exercise-4)
    - [In-class Exercise #5](#in-class-exercise-5)
    - [In-class Exercise #6](#in-class-exercise-6)
  - [🌀 Promises](#-promises)
    - [In-class Exercise #7](#in-class-exercise-7)
    - [In-class Exercise #8](#in-class-exercise-8)
    - [In-class Exercise #9](#in-class-exercise-9)

---

## 📰 Review

### 🗓️ Events, Callbacks

<details open>
<summary>Events</summary>

>Events are actions or occurrences that happen in the system you are programming, which the system tells you about so your code can respond to them. Examples include user actions like clicks, key presses, and mouse movements.
>
>```javascript
>// Example of handling a click event in JavaScript
>document.getElementById("myButton").addEventListener("click", function() {
>    alert("Button was clicked!");
>});
>```
>
>
>
</details>

<details open>
<summary>Callbacks</summary>

>Callbacks are functions that are passed as arguments to other functions, which can be invoked within the outer function to complete some kind of action or routine. Callbacks ensure that a function is not going to run before a task is completed, but will run right after the task is completed.
>
>```javascript
>// Example of a simple callback function in JavaScript
>function greet(name, callback) {
>    console.log("Hello " + name);
>    callback();
>}
>
>function sayGoodbye() {
>    console.log("Goodbye!");
>}
>
>greet("Alice", sayGoodbye); 
>// Output:
>// Hello Alice
>// Goodbye!
>```
>
>
>
</details>

### In-class Exercise #1

<details open>
<summary>Exercise: events</summary>

>Create a webpage with a button that changes its text when clicked.
>
>```html
><!DOCTYPE html>
><html>
><head>
>    <title>Event Exercise</title>
></head>
><body>
>    <button id="myButton">Click me!</button>
>    <script>
>        document.getElementById("myButton").addEventListener("click", function() {
>            this.textContent = "Clicked!";
>        });
>    </script>
></body>
></html>
>```
>
>
>
</details>

### In-class Exercise #2

<details open>
<summary>Exercise: callbacks</summary>

>Create a function that takes a number and a callback, and then calls the callback with the number squared.
>
>```javascript
>function processNumber(num, callback) {
>    const result = num * num;
>    callback(result);
>}
>
>function displayResult(result) {
>    console.log("The result is: " + result);
>}
>
>processNumber(5, displayResult);  
>// Output: The result is: 25
>```
>
>
>
</details>


---
## 📰 Intro

<details open>
<summary>Can we have our code multitask?</summary>

>Yes, we can have our code multitask through asynchronous programming techniques. In JavaScript, this is commonly achieved using callbacks, promises, and async/await. These techniques allow the program to handle multiple operations simultaneously without blocking the main execution thread.
>
>```javascript
>// Example using setTimeout to simulate multitasking
>console.log("Start");
>
>setTimeout(() => {
>    console.log("This runs after 2 seconds");
>}, 2000);
>
>console.log("End");
>// Output:
>// Start
>// End
>// This runs after 2 seconds
>```
>
>
>
</details>

<details open>
<summary>What are the risks of multitasking</summary>

>Multitasking in code can introduce several risks, such as:
>
> 1. **Race Conditions**: Occur when two or more operations must be done in the correct order but the code doesn't ensure that order.
>
>    ```javascript
>    let counter = 0;
>    function increment() {
>        counter++;
>    }
>
>    function printCounter() {
>        console.log(counter);
>    }
>
>    increment();
>    printCounter();
>    // If increment and printCounter are called asynchronously, the order of execution may vary.
>    ```

> 2. **Deadlocks**: Happen when two or more tasks are waiting for each other to complete, causing neither to ever complete.
> >
>    ```javascript
>    // Example of a deadlock situation
> // Function representing Task A
> function taskA() {
>     return new Promise((resolve, reject) => {
>         console.log("Task A started");
>
>         // Simulate Task A waiting for Task B to complete
>         taskB().then(() => {
>             console.log("Task A continues");
>             resolve("Task A completed");
>         }).catch(reject);
>     });
> }
>
> // Function representing Task B
> function taskB() {
>     return new Promise((resolve, reject) => {
>         console.log("Task B started");
>
>         // Simulate Task B waiting for Task A to complete
>         taskA().then(() => {d
>             console.log("Task B continues");
>             resolve("Task B completed");
>         }).catch(reject);
>     });
> }
>
> // Start Task A
> taskA().catch((error) => {
>     console.error("Error:", error.message);
> });
>
> // Start Task B
> taskB().catch((error) => {
>     console.error("Error:", error.message);
> });
>    // Task A waits for Task B, and Task B waits for Task A
>    ```
>
>3. **Increased Complexity**: Asynchronous code can be harder to read and maintain, leading to potential bugs and maintenance challenges.
>    ```javascript
>    // Example using Promises that can become complex
>    fetch('https://api.example.com/data')
>        .then(response => response.json())
>        .then(data => console.log(data))
>        .catch(error => console.error(error));
>    ```
>
>
>
</details>

### In-class Exercise #3

<details open>
<summary>Exercise: QUIZ - multitasking in code</summary>

>Create a function that fetches data from an API and logs the result, but also logs "Fetching data..." immediately when called. This demonstrates asynchronous behavior.
>
>```javascript
>function fetchData() {
>    console.log("Fetching data...");
>    fetch('https://api.example.com/data')
>        .then(response => response.json())
>        .then(data => console.log(data))
>        .catch(error => console.error("Error:", error));
>}
>
>fetchData();
>// Output:
>// Fetching data...
>// (data from API)
>// or Error: (error message)
>```
>
>
>
</details>


---

## ⏳ Async vs Synchronous

<details open>
<summary>Javascript is not “multithreaded”.</summary>

>JavaScript is single-threaded, meaning it executes code in a single sequence. However, JavaScript can handle asynchronous operations, allowing it to manage tasks that don't block the main thread. This is achieved through mechanisms like callbacks, promises, and async/await, which enable the execution of non-blocking operations.
>
>```javascript
>// Example of synchronous code
>console.log("Start");
>console.log("End");
>// Output:
>// Start
>// End
>
>// Example of asynchronous code
>console.log("Start");
>setTimeout(() => {
>    console.log("This runs after 2 seconds");
>, 2000);
>console.log("End");
>// Output:
>// Start
>// End
>// This runs after 2 seconds
>```
>
>
>
</details>

<details open>
<summary>Solution: Event Loops & Webworkers</summary>

>The event loop is a mechanism that allows JavaScript to perform non-blocking operations by managing asynchronous callbacks. When an asynchronous operation completes, the callback is pushed to the event loop, which handles its execution.
>
>Web Workers allow for running scripts in background threads, providing a way to run code in parallel with the main execution thread, thus enabling true multitasking in JavaScript.
>
>```javascript
>// Example of event loop with setTimeout
>console.log("Start");
>setTimeout(() => {
>    console.log("Callback executed");
>, 1000);
>console.log("End");
>// Output:
>// Start
>// End
>// Callback executed
>
>// Example of Web Workers
>// worker.js
>self.onmessage = function(e) {
>    const result = e.data[0] * e.data[1];
>    self.postMessage(result);
>}
>
>// main.js
>const worker = new Worker('worker.js');
>worker.onmessage = function(e) {
>    console.log('Result: ' + e.data);
>}
>worker.postMessage([10, 20]);
>```
>
>
>
</details>

### In-class Exercise #4

<details open>
<summary>Exercise: async code (easy) </summary>

>Create a function that logs "Hello" immediately, and "World" after 1 second.
>
>```javascript
>function sayHello() {
>    console.log("Hello");
>    setTimeout(() => {
>        console.log("World");
>    }, 1000);
>}
>
>sayHello();
>// Output:
>// Hello
>// World (after 1 second)
>```
>
>
>
</details>

### In-class Exercise #5

<details open>
<summary>Exercise: async code (medium) </summary>

>Create a function that fetches user data from an API and logs the user's name. Log "Fetching data..." immediately when called.
>
>```javascript
>async function fetchUser() {
>    console.log("Fetching data...");
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await response.json();
>        console.log(user.name);
>    } catch (error) {
>        console.error("Error:", error);
>    }
>}
>
>fetchUser();
>// Output:
>// Fetching data...
>// Leanne Graham (example user name from API)
>```
>
>
>
</details>

### In-class Exercise #6

<details open>
<summary>Exercise: async code (hard) </summary>

>Create a function that fetches data from two APIs sequentially. Log the combined result after both fetch operations are complete.
>
>```javascript
>async function fetchSequentialData() {
>    try {
>        const response1 = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        const post = await response1.json();
>
>        const response2 = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await response2.json();
>
>        const combinedResult = {
>            post: post,
>            user: user
>        };
>        
>        console.log(combinedResult);
>    } catch (error) {
>        console.error("Error:", error);
>    }
>}
>
>fetchSequentialData();
>// Output:
>// { post: {...}, user: {...} }
>```
>
>
>
</details>

---

## 🌀 Promises

<details open>
<summary>javaScript Promises to the rescue</summary>

>JavaScript Promises provide a way to handle asynchronous operations more easily and avoid callback hell. A Promise represents the eventual completion or failure of an asynchronous operation and its resulting value.
>
>```javascript
>// Example of a simple Promise
>const myPromise = new Promise((resolve, reject) => {
>    setTimeout(() => {
>        resolve("Promise resolved");
>    }, 2000);
>});
>
>myPromise.then((result) => {
>    console.log(result);
>}).catch((error) => {
>    console.error(error);
>});
>```
>
>
>
</details>

<details open>
<summary>javaScript Promises to the rescue</summary>

>JavaScript Promises provide a way to handle asynchronous operations more easily and avoid callback hell. A Promise represents the eventual completion or failure of an asynchronous operation and its resulting value.
>
>```javascript
>// Example of a simple Promise
>const myPromise = new Promise((resolve, reject) => {
>    setTimeout(() => {
>        resolve("Promise resolved");
>    }, 2000);
>});
>
>myPromise.then((result) => {
>    console.log(result);
>}).catch((error) => {
>    console.error(error);
>});
>```
>
>
>
</details>

### In-class Exercise #7

<details open>
<summary>Exercise: promises (easy) </summary>

>Create a function that returns a Promise which resolves after 3 seconds and logs "Promise resolved" when resolved.
>
>```javascript
>function myEasyPromise() {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            resolve("Promise resolved");
>        }, 3000);
>    });
>}
>
>myEasyPromise().then((result) => {
>    console.log(result);
>});
>// Output:
>// Promise resolved (after 3 seconds)
>```
>
>
>
</details>

### In-class Exercise #8

<details open>
<summary>Exercise: promises (medium) </summary>

>Create a function that returns a Promise which resolves with a random number after 2 seconds, or rejects with an error message after 1 second. Log the result or error.
>
>```javascript
>function myMediumPromise() {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            const randomNumber = Math.random();
>            if (randomNumber < 0.5) {
>                resolve(randomNumber);
>            } else {
>                reject("Error: Random number too high");
>            }
>        }, 2000);
>    });
>}
>
>myMediumPromise().then((result) => {
>    console.log("Resolved:", result);
>}).catch((error) => {
>    console.error(error);
>});
>// Output:
>// Resolved: (random number after 2 seconds)
>// or Error: Random number too high (after 1 second)
>```
>
>
>
</details>

### In-class Exercise #9

<details open>
<summary>Exercise: promises (hard) </summary>

>Create a function that returns a Promise which resolves after 1 second, and another function that returns a Promise which resolves after 3 seconds. Use Promise.all to log "All promises resolved" when both promises are resolved.
>
>```javascript
>function promise1() {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            resolve("Promise 1 resolved");
>        }, 1000);
>    });
>}
>
>function promise2() {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            resolve("Promise 2 resolved");
>        }, 3000);
>    });
>}
>
>Promise.all([promise1(), promise2()]).then((results) => {
>    console.log("All promises resolved");
>});
>// Output:
>// All promises resolved (after 3 seconds)
>```
>
>
>
</details>


