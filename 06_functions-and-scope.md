# 06: Functions and Scope

#### [Table of Contents](#table-of-contents)

  - [Functions](#intro)
  - [Structure](#structure)
  - [In Class Exercise #1](#in-class-exercise-1)
  - [Scope](#scope)
    - [Global Scoope](#global-scope)
    - [Local Scoope](#local-scope)

  - [Arrow Functions](#arrow-functions)

## Intro

<details open>
<summary>What is a function? Why is it important?</summary>

> Imagine a function as a librarian in a vast library, ready to assist patrons with various requests. Just like a librarian organizes and retrieves books based on specific criteria, a function in programming organizes and executes a set of instructions based on specific input parameters.
>
> ![alt text](https://media.istockphoto.com/id/1455947949/photo/latin-female-librarian-in-50s-serving-a-costumer.webp?b=1&s=170667a&w=0&k=20&c=KAXhRhW7nBu7XSe-ARzcx9vhX7r_HMI3loJTdxQS290=)
>
> - **Function as a Librarian**: In a library, a librarian acts as a function. When a reader asks for a book, the librarian retrieves it based on the title or author's name provided. Similarly, a function takes input parameters (like the book's title) and performs certain actions or calculations accordingly.
>
> - **Organization and Efficiency**: Functions help organize code by breaking it into manageable and reusable chunks, much like how a librarian categorizes books by genre or subject matter. This modularity enhances code readability and maintainability.
>
> - **Code Reusability**: Just as a librarian can assist multiple readers with the same book, a function can be called multiple times with different inputs, allowing for code reuse and reducing redundancy.
>
> In essence, functions are the building blocks of programs, enabling developers to write efficient, organized, and reusable code, much like how librarians facilitate the smooth operation of a library.

</details>

## Structure

<details open>
<summary>What 5 things does a function consist of?</summary>

> <details>
> <summary><h3>Function Declaration</h3></summary>
>   ```javascript
>   function functionName(parameter1, parameter2) {
>   ```
>   - The function declaration starts with the `function` keyword, followed by the name of the function (`functionName` in this example).
>   - Parameters may be includedd inside the parentheses. These are optional, and a function may have zero or more parameters.
>
> </details>
>
> <details>
> <summary><h3>Function Body</h3></summary> 
>   ```javascript
>   {
>     // Code to be executed
>   }
>   ```
>   - The body of the function contains the code that defines the behavior of the function.
>   - It consists of one or more statements enclosed within curly braces `{}`.
> </details>
>
> <details>
> <summary><h3>Parameters</h3></summary>
>
> ```javascript
> function functionName(parameter1, parameter2) {
> ```
>
> - Parameters are placeholders for values that the function will receive when it's called.
> - They are optional, and a function can have zero or more parameters.
> - Parameters are separated by commas and listed inside the parentheses.
>
> </details>
>
> <details>
> <summary><h3>Return Statement</h3></summary>
>
> ```javascript
> return result;
> ```
>
> - The `return` statement specifies the value that the function will return when it's called.
> - It is optional, and a function may or may not have a return statement.
> - If a function doesn't have a return statement, it implicitly returns `undefined`.
> - Execution of the function stops once a return statement is encountered.
> </details>
>
> <details>
> <summary><h3>Function Call</h3></summary>
>
> ```javascript
> functionName(argument1, argument2);
> ```
>
> - To execute a function, you need to call it by its name followed by parentheses.
> - Arguments are the actual values passed to the function when it's called. These correspond to the parameters defined in the function declaration.
> - Arguments are optional, and a function call may have zero or more arguments.
>
> - **Function Expression**:
>
>   ```javascript
>   const functionName = function (parameter1, parameter2) {
>     // Code to be executed
>   };
>   ```
>
>   - Alternatively, you can define a function using a function expression.
>   - This involves assigning an anonymous function to a variable (`functionName` in this example).
>   - Function expressions can also have parameters and a function body, similar to function declarations.
>
> Understanding these components helps in creating and utilizing functions effectively in JavaScript.

</details>

### In-Class Exercise #1

<details open>
<summary>Exercise #1: Function Practice</summary>

> 1. Define a function named greet that takes no parameters and prints "Hello, world!" to the console when called.
> 2. Create a function named addNumbers that takes two parameters num1 and num2, and returns the sum of the two numbers.
> 3. Write a function named multiply that accepts three parameters num1, num2, and num3, and returns the product of the three numbers.
> 4. Declare a function called sayName that takes one parameter name and prints "Your name is: " followed by the provided name.
> 5. Define a function named calculateArea that takes two parameters width and height, and returns the area of a rectangle (width \* height).
>
> <details>
> <summary>Answers</summary>
>
> Define a function named greet that takes no parameters and prints "Hello, world!" to the console when called.
>
> ```javascript
> function greet() {
>   console.log("Hello, world!");
> }
> ```
>
> Create a function named addNumbers that takes two parameters num1 and num2, and returns the sum of the two numbers.
>
> ```javascript
> function addNumbers(num1, num2) {
>   return num1 + num2;
> }
> ```
>
> Write a function named multiply that accepts three parameters num1, num2, and num3, and returns the product of the three numbers.
>
> ```javascript
> function multiply(num1, num2, num3) {
>   return num1 * num2 * num3;
> }
> ```
>
> Declare a function called sayName that takes one parameter name and prints "Your name is: " followed by the provided name.
>
> ```javascript
> function sayName(name) {
>   console.log("Your name is: " + name);
> }
> ```
>
> Define a function named calculateArea that takes two parameters width and height, and returns the area of a rectangle (width \* height).
>
> ```javascript
> function calculateArea(width, height) {
>   return width * height;
> }
> ```

> </details>

</details>

## Scope

<details>
<summary>What is Scope? (three main principles)</summary>

> Imagine JavaScript scope as a vast library, each principle akin to a section guiding how you access and interact with books.
>
> - **Global Scope: Library's Grand Hall**
>
>   - Just as books placed in the grand hall of a library are accessible from anywhere within the library, variables declared outside any function belong to the global scope. They are readily available throughout your entire JavaScript program.
>   - ![alt text](https://images.pexels.com/photos/4318445/pexels-photo-4318445.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1)
>
> - **Local Scope: Reading Room**
>
>   - Inside a library's reading room, you have access to books located within that space only. Similarly, variables declared within a function are confined to its local scope. They are accessible only from within that function, providing a secluded environment for specific tasks.
>   - ![alt text](https://lits.mtholyoke.edu/sites/default/files/images/Reading%20Room%20Nook.png)
>
> - **Closure: The Library's Secrets**
>   - Imagine stumbling upon a hidden chamber within the library, containing ancient tomes accessible only to those who find it. Similarly, closures in JavaScript grant functions access to variables from their containing scope, even after the function has finished executing. They encapsulate secrets of their origin, enabling powerful programming patterns.
>   - ![alt text](https://hiddendoorstore.com/wp-content/uploads/2019/12/secret-home-library-bookcases.jpg)

</details>

### Global Scope

<details open>
<summary>What and Why is Global Scope important?</summary>

> Global Scope:
>
> Global scope refers to the accessibility of variables and functions throughout the entire program, making them available from any part of the codebase. It is important because it allows essential data and functionalities to be accessed and utilized across different components and modules without the need for passing them as arguments or returning them from functions. This facilitates code organization, modularity, and reusability.
>
> In JavaScript, variables declared outside of any function or block have global scope. For example:
>
> ```javascript
> let globalVar = "I am a global variable";
>
> function myFunction() {
>   console.log(globalVar); // Accessing globalVar from within a function
> }
>
> myFunction(); // Output: "I am a global variable"
> ```
>
> In this coding example, `globalVar` is declared outside any function, making it accessible globally. The `myFunction` function can access and use `globalVar` without needing to pass it as an argument, showcasing the importance of global scope in JavaScript programming.

</details>

### Local Scope

<details open>
<summary>Why is Local Scope important</summary>

> Local Scope:
>
> Local scope refers to the accessibility of variables within a specific function or block, making them available only within that function or block. It is important because it allows variables to be confined to specific areas of code, preventing unintended interactions and ensuring encapsulation.
>
> In JavaScript, variables declared using `let` or `const` within a function or block have local scope, meaning they are accessible only within that function or block. For example:
>
> ```javascript
> function myFunction() {
>   let localVar = "I am a local variable";
>   console.log(localVar); // Accessing localVar within the function
> }
>
> myFunction(); // Output: "I am a local variable"
>
> console.log(localVar); // Error: localVar is not defined outside the function
> ```
>
> In this coding example, `localVar` is declared inside the `myFunction` function, making it accessible only within that function. Attempting to access `localVar` outside the function results in an error because it is out of scope. This demonstrates how local scope restricts the visibility of variables to specific parts of the code.
>
> Local scope is connected to global scope in that variables declared globally can be accessed within any function or block, including those nested within other functions. However, variables declared locally within a function or block are not accessible outside of that function or block, creating a hierarchy of scope levels where local scope takes precedence over global scope within its boundaries. This distinction ensures that variables are appropriately scoped and minimizes potential conflicts or unintended side effects in complex codebases.

</details>

![alt text](https://miro.medium.com/v2/resize:fit:1400/1*naPPWUJjDMmKXZzsWopOqQ.jpeg)


## Arrow Functions

---

<details open>
<summary>Basics of Arrow Functions</summary>

> Arrow functions are a concise way to write function expressions in JavaScript, introduced in ES6. They provide a more compact syntax compared to traditional function declarations and expressions, making code cleaner and easier to read.

> 1. **Simple Arrow Function:**
> 
> ```javascript
> // Traditional function declaration
> function greet(name) {
>     return "Hello, " + name + "!";
> }
> 
> // Equivalent arrow function
> const greet = (name) => {
>     return "Hello, " + name + "!";
> };
> ```
>
> Arrow functions eliminate the need for the `function` keyword and use a concise `=>` syntax to denote the function. They are especially useful for short, single-expression functions.

> 2. **Implicit Return:**
> 
> ```javascript
> // Traditional function declaration
> function double(num) {
>     return num * 2;
> }
> 
> // Equivalent arrow function with implicit return
> const double = (num) => num * 2;
> ```
>
> Arrow functions with a single expression can have an implicit return, where the return keyword and curly braces are omitted. This further reduces code verbosity and enhances readability.

> 3. **Lexical `this` Binding:**
> 
> ```javascript
> // Traditional function declaration
> function Counter() {
>     this.count = 0;
> 
>     setInterval(function() {
>         this.count++; // Incorrect, `this` refers to the global object
>         console.log(this.count);
>     }, 1000);
> }
> 
> // Arrow function with lexical `this` binding
> function Counter() {
>     this.count = 0;
> 
>     setInterval(() => {
>         this.count++; // Correct, `this` refers to the Counter object
>         console.log(this.count);
>     }, 1000);
> }
> ```
>

Arrow functions offer syntactic sugar and improved scoping behavior, making them a preferred choice for many JavaScript developers. They streamline code, enhance readability, and mitigate common issues associated with traditional function expressions.

</details>

<details open>
<summary>Pros and Cons of Using Arrow Functions</summary>

>**Pros:**
>
> - **Concise Syntax**: Arrow functions provide a shorter syntax compared to traditional function expressions, especially for simple, single-line functions.
> - **Lexical `this` Binding**: Arrow functions lexically bind the value of `this`, meaning they inherit the `this` value from the surrounding code at the time they are defined. This can help avoid confusion and errors related to the `this` keyword in nested functions and event handlers.
> - **Implicit Return**: Arrow functions automatically return the result of the expression without needing an explicit `return` statement when the function body consists of a single expression. This can make the code more readable and reduce boilerplate.
> - **Ideal for Callbacks**: Arrow functions are well-suited for use as callbacks or in higher-order functions due to their concise syntax and lexical `this` binding.
>
>**Cons:**
>
> - **No `arguments` Object**: Arrow functions do not have their own `arguments` object. If you need to access the arguments passed to an arrow function, you have to rely on the `arguments` of a surrounding non-arrow function.
> - **No `new` Keyword**: Arrow functions cannot be used as constructor functions. They do not have their own `this` binding, so attempting to use them with the `new` keyword will result in an error.
> - **Limited Function Scope**: Since arrow functions do not have their own `this` context, they cannot be used as methods in objects. Additionally, they cannot be dynamically bound to a different `this` value using `bind`, `call`, or `apply`.
> - **Not Suitable for Prototypes**: Arrow functions are not suitable for use as prototype methods, as they do not have their own `this` context and cannot be used with `new`.
> - **Potential for Confusion**: While lexical `this` binding can be beneficial, it can also lead to confusion if developers are not familiar with the concept. It's essential to understand how `this` behaves in arrow functions compared to traditional functions.

Despite these limitations, arrow functions are widely used in modern JavaScript codebases due to their simplicity and readability, especially for handling callbacks and working with arrays and iterators.


</details>


---

<details open>
<summary></summary>

>
>
>
>
>
>

</details>

