# 02: DOM (Document Object Model)

#### [Table of Contents](#table-of-contents)

  - [DOM](#dom)
    - [Document Object Model](#document-object-model)
    - [In-Class Excercise #1](#in-class-excercise-1)
  - [Debugging](#debugging)
    - [In-Class Excercise #3](#in-class-excercise-3)
  - [Errors](#errors)
    - [Most Common Errors](#most-common-errors)
  - [Devtools](#devtools)
  - [Console](#console)
    - [Why is the Console Important?](#why-is-the-console-important)
    - [Key features of the Console](#key-features-of-the-console)
  - [Overview](#overview)


---

## DOM

### Document Object Model

![alt text](https://www.freecodecamp.org/news/content/images/2024/01/JavaScript--2-.png)

<details open>
<summary>What is the DOM?</summary>

> Everything in your browser can be represented as **an Object**
>
> The DOM, or Document Object Model, is that object. It is like a **blueprint** for web pages.
>
> It's a way for browsers to <u>understand and organize all the different elements</u> of a webpage, like paragraphs, images, and buttons.
>
> with the DOM, we can use languages like JavaScript to interact with and change these elements, making dynamic and interactive websites.

</details>

<details open>
<summary>Why do we need the DOM?</summary>

> It's a way for <u>web developers to manipulate the content, structure, and style of web pages dynamically.</u>
>
> with the DOM, we can use languages like JavaScript to interact with and change these elements, making dynamic and interactive websites.
>
> ![alt text](https://images.pexels.com/photos/14692584/pexels-photo-14692584.jpeg?auto=compress&cs=tinysrgb&w=800)
>
> Imagine the internet is like a giant puzzle, with each webpage being a piece of that puzzle.
>
> It is like the map that shows you how all the pieces fit together. It allows us, like puzzle masters, to rearrange, add, or remove pieces to create new pictures, making the internet more interactive and fun to explore.
>
> So, just like how a map helps us navigate and explore new places, the DOM helps developers navigate and manipulate the content of web pages, making the internet a more dynamic and exciting place for everyone.

</details>

<details open>
<summary>How do you find the DOM as a dev?</summary>

> Remember, every website has a DOM. So you can go to any website and find it

</details>

### In-Class Excercise #1

<details open>
<summary>In-class Exercise #1: the DOM</summary>

> Go to any Wikipedia page in your web browser.
>
> Open the browser's developer tools by right-clicking on the page and selecting "Inspect" or by pressing Ctrl + Shift + I (on Windows/Linux) or Cmd + Option + I (on macOS).
>
> Navigate to the "Console" tab in the developer tools.
>
> In the console, you can use JavaScript to manipulate the page's content. For example, you can change the text of a heading by selecting it using its CSS selector and then modifying its textContent property. Here's an example:
>
> ```javascript
> // Select the heading element using its CSS selector
> let heading = document.querySelector("#firstHeading");
>
> // Change the text of the heading
> heading.textContent = "Hello Wikipedia!";
> ```
>
> Press Enter after typing the JavaScript code to execute it. You'll see the heading text on the Wikipedia page change to "Hello Wikipedia!" temporarily until you refresh the page.
>
> You can copy and paste this Markdown-formatted text into your Markdown file.

<details open>
<summary>Resource Videos</summary>

- [![Aaron Jack - the DOM]](http://www.youtube.com/watch?v=KShnPYN-voI)
  Description: This video provides an in-depth explanation of the Document Object Model (DOM).

- [Bro Code - What is the DOM?](https://www.youtube.com/watch?v=NO5kUNxGIu0)
  ![Bro Code - What is the DOM?](v)
  Description: This video explains the DOM in a simplified manner.

</details>


---

## Debugging

<p>Now that we can manipulate the DOM, there will be times where we will come across some <strong>"bugs"</strong> that will need <strong>debugging</strong> </p>

<details open>
<summary>What is debugging?</summary>

> identifying and fixing errors (or bugs) in your code.
>
> It involves using tools like browser developer tools (which we will cover in this lesson) or debugging features in code editors (vs code) to track down issues
>
> Syntax errors, logical errors, or unexpected behaviors in your JavaScript code arae examples of "bugs". Through debugging, developers can gain insights into how their code is executing and make necessary corrections to ensure its proper functionality.
>
> ![alt text](https://e7.pngegg.com/pngimages/748/403/png-clipart-insecticide-pest-control-biocide-disinfectants-mosquito-furniture-insects.png)

</details>

<details open>
<summary>Why is debugging important?</summary>

> Debugging is crucial for web developers because it helps identify and fix issues in their code, ensuring that websites function as intended.
>
> By debugging, developers can deliver a smoother and more reliable user experience, leading to increased customer satisfaction and trust in their products.
>
> > <h3>FUN FACT </h3>
> > Programmers report to spend on average 60-80% of their time debugging.

</details>

### In-Class Excercise #3

<details open>
<summary>In-class Exercise #3a: triangle</summary>

> This code should the area of a rectangle given its length and width. However, there is one bug in the code that you need to find and fix.
>
> ```javascript
> // Define variables for length and width
> let length = 5;
> let width = 3;
>
> // Calculate the area of the rectangle
> let area = length * width;
>
> // Display the area
> console.log("The area of the rectangle is: " + area);
> ```
>
> <details>
> <summary>Answer</summary>
>
> ```javascript
> // the calculation needed to be fixed
> let area = (length * width) / 2;
> ```
>
> </details>

</details>

<details open>
<summary>In-class Exercise #3b: average</summary>

> Write a program that calculates the average of two numbers. However, there are some bugs in the code that you need to find and fix.
>
> ```javascript
> // Define variables for the two numbers
> let num1 = 10;
> let num2 = 20;
>
> // Calculate the average of the two numbers
> let average = num1 + num2 / 2;
>
> // Display the average
> console.log("The average of the two numbers is: " + average);
> ```
>
> <details>
> <summary>Answer</summary>
>
> ```javascript
> // the calculation needed to be fixed
> let average = (num1 + num2) / 2;
> ```
>
> </details>

</details>

---

## Errors

<p>Now that we know how to debug, let's look at more common errors that we might get in our projects. </p>

![alt text](https://static.thenounproject.com/png/1496953-200.png)

### Most Common Errors

<details open>
<summary>Syntax Errors</summary>

> <i>the code violates the rules of the programming language, such as missing punctuation or using incorrect syntax.</i>
>
> ![alt text](https://github.com/MountainlandWEB/javascript/blob/main/images/image.png)
>
> Coding Example:
>
> ```javascript
> // Syntax Error: Missing closing parenthesis
> console.log("Hello, world!";
> ```
>
> ```javascript
> // Syntax Error: Mismatched curly braces
> function sayHello() {
>   console.log("Hello, world!");
> }
> ```

</details>

<details open>
<summary>Undefined Errors</summary>

> <i>This error often indicates a spelling error or a variable that is declared incorrectly.</i>
>
> ![alt text](https://github.com/MountainlandWEB/javascript/blob/main/images/image-1.png)
>
> ```javascript
> // Undefined variable
> let message = "Hello, world!";
> console.log(mesage);
> ```
>
> ```javascript
> // Undefined property
> let person = { name: "John" };
> console.log(person.age);
> ```

</details>

<details open>
<summary>UnExpected Token Errors</summary>

> <i>This error often occurs due to missing punctuation like a semicolon or an unclosed section of code, such as missing brackets.
> </i>
>
>![alt text](https://github.com/MountainlandWEB/javascript/blob/main/images/image-2.png)
>
>   ```javascript
> // Unexpected Token Error: Incorrect use of template literals
> let name = "John";
> let greeting = `Hello, ${name;}`; // Unexpected token ';'
>   ```

</details>

---

## Devtools
<p>Now that we know about the DOM and how to work on bugs, let's learn about the "toolbox" every developer uses to do these things</p>

<details open>
<summary>What are the devTools?</summary>

> Developer tools, commonly referred to as "DevTools," 
> 
> are a set of built-in browser features that allow developers to inspect, debug, and profile web pages or applications directly within the web browser. 
> 
> They provide a suite of powerful tools for web development, including:

</details>

<details open>
<summary>How do i find it?</summary>

> 1. **Open Your Web Browser**: Launch your preferred web browser (such as Google Chrome, Mozilla Firefox, Safari, or Microsoft Edge).
> ![alt text](https://github.com/MountainlandWEB/javascript/blob/main/images/image-3.png)

> 2. **Navigate to a Web Page**: Type the URL of the web page you want to inspect or debug into the address bar and press Enter.

> 3. **Open DevTools**: There are several ways to open DevTools:
>    - **Right-Click Method**: Right-click anywhere on the web page and select "Inspect" or "Inspect Element" from the context menu.
> - **Keyboard Shortcut Method**: Press Ctrl + Shift + I (Windows/Linux) or Cmd + Option + I (macOS) to open DevTools.
> 
>> | Shortcut Key                   | (Windows/Linux) | (macOS)     |
>> |--------------------------|------------------------------|--------------------------|
>> | Keyboard Shortcut Method | Ctrl + Shift + I             | Cmd + Option + I         |
>
>    - **Menu Method (Chrome and Firefox)**: Click on the menu icon (three vertical dots in Chrome, or three horizontal lines in Firefox) in the top-right corner of the browser window. Then, select "More tools" > "Developer tools" from the dropdown menu.
> ![alt text](https://github.com/MountainlandWEB/javascript/blob/main/images/image-4.png)
> 
>    - **Menu Method (Safari)**: Click on "Develop" in the menu bar, then select "Show Web Inspector".
>    - **Menu Method (Edge)**: Click on the menu icon (three horizontal dots) in the top-right corner, then select "More tools" > "Developer tools".

> 4. **Explore DevTools**: Once DevTools is open, you'll see a panel or window appear within the browser window. This is the DevTools interface, which typically consists of tabs or panels for inspecting HTML, CSS, JavaScript, network activity, and more. Explore the different tabs and panels to familiarize yourself with the various features and tools available.

> 5. **Close DevTools**: When you're done using DevTools, you can close it by clicking the close button (usually an "X" icon) in the top-right corner of the DevTools panel, or by pressing the same keyboard shortcut you used to open it (Ctrl + Shift + I or Cmd + Option + I).


</details>



---

## Console


<p>Although there are plenty of "tools" we can use in our browser devtools, we will be focusing on one tool that you will use a majority of the time: the Console.</p>

  <img src="https://png.pngtree.com/png-vector/20191018/ourmid/pngtree-design-illustrator-of-game-console-set-png-image_1794495.jpg" alt="alt text" style="width: 150px;">


### Why is the Console Important?

<details open>
<summary>Debugging</summary>

> The console allows developers to log messages, errors, and variables, helping them identify and fix issues in their code. By logging relevant information to the console, developers can gain insights into the behavior of their code and diagnose problems quickly.
> 
> ```javascript
> // Logging messages
> console.log("Hello, world!"); 
> 
> // Logging errors
> console.error("Oops! Something went wrong.");
> 
> // Logging variables
> let x = 5;
> console.log("The value of x is: " + x);
> ```
> 
</details>




<details open>
<summary>Testing and Experimentation</summary>


>
> The console provides a sandbox environment where developers can execute JavaScript code snippets and experiment with different functionalities of their web page or application. 
>
> <img src="https://cdn2.iconfinder.com/data/icons/devops-outline/60/Code-Testing-programming-coding-test-512.png" alt="alt text" style="width: 100px;">
>
> 
> This allows for rapid prototyping and testing without the need to modify the actual codebase.
> 
>
> ```javascript
> // Testing functionality
> console.log("Testing functionality...");
>
> // Experimenting with code snippets
> let result = 5 + 3;
> console.log("The result of 5 + 3 is: " + result);
> ```
> 
</details>




### Key features of the Console

<details open>
<summary>Logging Messages</summary>

> Developers can use console.log() to output messages, variables, or objects to the console, allowing them to track the flow of their code and inspect values during runtime.
> 
> ### Examples:
> 
> ```javascript
> // Logging messages
> console.log("Hello, world!"); 
> 
> // Logging variables
> let x = 5;
> console.log("The value of x is: " + x);
> ```
> 
</details>

<details open>
<summary>Error Handling</summary>

> console.error() and console.warn() are used to log errors and warnings, respectively, helping developers identify and address issues in their code.
> 
> ### Examples:
> 
> ```javascript
> // Logging errors
> console.error("Oops! Something went wrong.");
> 
> // Logging warnings
> console.warn("This is a warning message.");
> ```
> 
</details>

<details open>
<summary>Execution Timing</summary>

> Developers can use console.time() and console.timeEnd() to measure the execution time of code blocks, helping identify performance bottlenecks and optimize code efficiency.
> 
> ### Examples:
> 
> ```javascript
> // Start timing
> console.time("Operation");
> 
> // Perform operation
> for (let i = 0; i < 1000000; i++) {
>     // Some time-consuming operation
> }
> 
> // End timing and log duration
> console.timeEnd("Operation");
> ```
> 
</details>

---

## Overview

<details open>
<summary>Overall Quiz</summary>

> <details>
> <summary>What is the DOM?</summary>
>
> The DOM, or Document Object Model, is a programming interface for web documents. It represents the structure of a document as a tree of objects that can be manipulated to change the content, structure, and style of a webpage.
>
> </details>
>
> <details>
> <summary>Why is the DOM important?</summary>
>
> The DOM is important because it allows developers to dynamically interact with and manipulate web pages using scripting languages like JavaScript. It enables the creation of dynamic, interactive, and responsive web applications.
>
> </details>
>
> <details>
> <summary>How do you find the DOM as a developer?</summary>
>
> Developers can access and manipulate the DOM using scripting languages like JavaScript. They can use methods and properties provided by the browser's Document object to traverse, modify, and interact with elements in the DOM.
>
> </details>
>
> <details>
> <summary>What are devTools and where can you find it?</summary>
>
> DevTools, short for Developer Tools, are a set of web development and debugging tools built into modern web browsers. They allow developers to inspect and debug web pages, test performance, edit HTML and CSS in real-time, and analyze network activity. DevTools can typically be found in the browser's menu or by right-clicking on a webpage and selecting "Inspect" or "Inspect Element".
>
> </details>
>
> <details>
> <summary>What are the common commands to handle errors and bugs in the console?</summary>
>
> - `console.log()`: Outputs a message to the console.
>   ```javascript
>   console.log("This is a log message.");
>   ```
> - `console.error()`: Outputs an error message to the console.
>   ```javascript
>   console.error("This is an error message.");
>   ```
> - `console.warn()`: Outputs a warning message to the console.
>   ```javascript
>   console.warn("This is a warning message.");
>   ```
>
> </details>
>
> <details>
> <summary>How do I find out how long an operation takes in the console?</summary>
>
> Developers can measure the time taken by an operation using `console.time()` and `console.timeEnd()`. These methods allow developers to mark the beginning and end of a code block and measure the time elapsed between them.
>
> **Example:**
>
> ```javascript
> console.time("operation");
> // Perform the operation here
> console.timeEnd("operation");
> ```
>
> </details>
>
</details>
