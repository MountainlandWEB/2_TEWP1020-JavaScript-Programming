# 09: Classes, Data Modeling, and ES6 Modules

*Make sure to understand OOP in JavaScript before moving on to this lesson. It is crucial to understanding how data and modules work in JavaScript.*

*Although we've gone through classes last lesson, it is important to keep reviewing and practice classes.*

### [Table of Contents](#table-of-contents)

  - [📚 Review](#-review)
  - [🏷️ Classes](#️-classes)
    - [Creating and Constructing Classes](#creating-and-constructing-classes)
    - [Why Classes?](#why-classes)
    - [In-Class Exercise #1](#in-class-exercise-1)
    - [In-Class Exercise #2](#in-class-exercise-2)
  - [🏗️ Data Modeling](#️-data-modeling)
    - [In-Class Exercise #3](#in-class-exercise-3)
    - [In-Class Exercise #4](#in-class-exercise-4)
  - [📦 ES6 Modules](#-es6-modules)
    - [In-Class Exercise #5](#in-class-exercise-5)
    - [In-Class Exercise #6](#in-class-exercise-6)

---

## 📚 Review

<details open>
<summary><h4>OOP</h4></summary>

> In JavaScript, Object-Oriented Programming revolves around the concept of objects. One common approach is to use constructor functions and prototypes to create objects with shared methods. For example:
>
> ```javascript
> // Constructor function
> function Person(name, age) {
>   this.name = name;
>   this.age = age;
> }
> 
> // Prototype method
> Person.prototype.greet = function() {
>   return `Hello, my name is ${this.name} and I'm ${this.age} years old.`;
> };
> 
> // Creating an object
> const person1 = new Person("John", 30);
> console.log(person1.greet()); // Output: "Hello, my name is John and I'm 30 years old."
> ```
>
> Another widely used method is to utilize ES6 classes, which provide a more familiar syntax for creating objects and defining their behavior. Here's how it looks:
>
> ```javascript
> // ES6 Class
> class Person {
>   constructor(name, age) {
>     this.name = name;
>     this.age = age;
>   }
> 
>   // Method
>   greet() {
>     return `Hello, my name is ${this.name} and I'm ${this.age} years old.`;
>   }
> }
> 
> // Creating an object
> const person2 = new Person("Alice", 25);
> console.log(person2.greet()); // Output: "Hello, my name is Alice and I'm 25 years old."
> ```
>
> In both examples, we de
</details>

---

## 🏷️ Classes

<details open>
<summary>Introduction to Classes</summary>

>Classes are blueprints for creating objects in programming. They encapsulate data for the object and methods to manipulate that data. By defining classes, you can create multiple objects with shared behavior and structure, promoting code reuse and organization.
>
>```javascript
>// Example of a basic class in JavaScript
>class Dog {
>    constructor(name, age) {
>        this.name = name;
>        this.age = age;
>    }
>
>    bark() {
>        return `${this.name} says woof!`;
>    }
>}
>
>// Creating an instance of the Dog class
>const myDog = new Dog("Buddy", 3);
>console.log(myDog.bark());  // Output: Buddy says woof!
>```
>
>
>
</details>

### Creating and Constructing Classes

<details open>
<summary>Defining a Class and Its Constructor</summary>

>To define a class in JavaScript, you use the `class` keyword followed by the class name and a block of code. The class constructor is defined using the `constructor` method, which initializes the object's attributes.
>
>```javascript
>class Car {
>    constructor(make, model, year) {
>        this.make = make;
>        this.model = model;
>        this.year = year;
>    }
>
>    description() {
>        return `${this.year} ${this.make} ${this.model}`;
>    }
>}
>
>// Creating an instance of the Car class
>const myCar = new Car("Toyota", "Corolla", 2020);
>console.log(myCar.description());  // Output: 2020 Toyota Corolla
>```
>
>
>
</details>

### Why Classes?

<details open>
<summary>Benefits of Using Classes</summary>

>Classes help in organizing and managing code more efficiently by providing a clear structure. They enable encapsulation, inheritance, and polymorphism, which are the core principles of Object-Oriented Programming (OOP).
>
>1. **Encapsulation**: Bundling the data (attributes) and methods (functions) that operate on the data into a single unit.
>    ```javascript
>    class Account {
>        constructor(owner, balance = 0) {
>            this.owner = owner;
>            this.balance = balance;
>        }
>        
>        deposit(amount) {
>            this.balance += amount;
>            return this.balance;
>        }
>        
>        withdraw(amount) {
>            if (amount > this.balance) {
>                return "Insufficient funds";
>            }
>            this.balance -= amount;
>            return this.balance;
>        }
>    }
>    ```
>
>2. **Inheritance**: Creating new classes from existing ones to promote code reuse.
>    ```javascript
>    class Animal {
>        constructor(name) {
>            this.name = name;
>        }
>        
>        speak() {
>            throw new Error("Subclass must implement abstract method");
>        }
>    }
>
>    class Dog extends Animal {
>        speak() {
>            return `${this.name} says woof!`;
>        }
>    }
>    
>    class Cat extends Animal {
>        speak() {
>            return `${this.name} says meow!`;
>        }
>    }
>    ```
>
>3. **Polymorphism**: The ability to use a shared interface for different underlying forms (data types).
>    ```javascript
>    function animalSpeak(animal) {
>        console.log(animal.speak());
>    }
>
>    const dog = new Dog("Buddy");
>    const cat = new Cat("Whiskers");
>
>    animalSpeak(dog);  // Output: Buddy says woof!
>    animalSpeak(cat);  // Output: Whiskers says meow!
>    ```
>
>
>
</details>

### In-Class Exercise #1

<details open>
<summary>Exercise: Creating a Simple Class</summary>

>Create a class named `Book` that has attributes for title, author, and pages. Include a method to display information about the book.
>
>```javascript
>class Book {
>    constructor(title, author, pages) {
>        this.title = title;
>        this.author = author;
>        this.pages = pages;
>    }
>
>    getInfo() {
>        return `'${this.title}' by ${this.author}, ${this.pages} pages`;
>    }
>}
>
>// Create an instance of the Book class
>const myBook = new Book("1984", "George Orwell", 328);
>console.log(myBook.getInfo());  // Output: '1984' by George Orwell, 328 pages
>```
>
>
>
</details>

### In-Class Exercise #2

<details open>
<summary>Exercise: Extending a Class</summary>

>Create a class `Library` that contains a list of `Book` objects. Include methods to add a book, remove a book by title, and display all books in the library.
>
>```javascript
>class Library {
>    constructor() {
>        this.books = [];
>    }
>
>    addBook(book) {
>        this.books.push(book);
>    }
>
>    removeBook(title) {
>        this.books = this.books.filter(book => book.title !== title);
>    }
>
>    displayBooks() {
>        this.books.forEach(book => {
>            console.log(book.getInfo());
>        });
>    }
>}
>
>// Create instances of the Book class
>const book1 = new Book("1984", "George Orwell", 328);
>const book2 = new Book("To Kill a Mockingbird", "Harper Lee", 281);
>
>// Create an instance of the Library class and add books to it
>const myLibrary = new Library();
>myLibrary.addBook(book1);
>myLibrary.addBook(book2);
>myLibrary.displayBooks();
>// Output:
>// '1984' by George Orwell, 328 pages
>// 'To Kill a Mockingbird' by Harper Lee, 281 pages
>```
>
>
>
</details>



---
## 🏗️ Data Modeling

<details open>
<summary>Introduction to Data Modeling</summary>

>Data modeling is the process of creating a visual representation of either a whole information system or parts of it to communicate connections between data points and structures. It ensures that the data objects required by the database are accurately represented and helps in designing a database at the conceptual, logical, and physical levels.
>
>In object-oriented programming, classes can serve as data models, representing real-world entities with attributes and behaviors.
>
>```javascript
>// Example of a simple data model for a user
>class User {
>    constructor(username, email) {
>        this.username = username;
>        this.email = email;
>    }
>
>    getDetails() {
>        return `User: ${this.username}, Email: ${this.email}`;
>    }
>}
>
>// Creating an instance of the User class
>const user = new User("johndoe", "john@example.com");
>console.log(user.getDetails());  // Output: User: johndoe, Email: john@example.com
>```
>
>
>
</details>

<details open>
<summary>Data Modeling Process</summary>

>The data modeling process typically involves three stages:
>
>1. **Conceptual Data Model**: This is a high-level model that defines what the system contains. It is often created through stakeholder interviews and doesn't include detailed information about the data structures.
>
>    ```javascript
>    // Conceptual model example: A class to represent a Customer
>    class Customer {
>        constructor(name, contactInfo) {
>            this.name = name;
>            this.contactInfo = contactInfo;
>        }
>    }
>    ```
>
>2. **Logical Data Model**: This model adds more detail to the conceptual model, specifying data attributes and relationships without considering how they will be physically implemented.
>
>    ```javascript
>    // Logical model example: A class to represent a Product
>    class Product {
>        constructor(name, price, category) {
>            this.name = name;
>            this.price = price;
>            this.category = category;
>        }
>    }
>    ```
>
>3. **Physical Data Model**: This model maps the logical model to the physical storage mechanisms of the database, including tables, columns, indexes, etc.
>
>    ```javascript
>    // Physical model example: Mapping to a relational database table
>    CREATE TABLE Products (
>        id INT PRIMARY KEY,
>        name VARCHAR(255),
>        price DECIMAL(10,2),
>        category VARCHAR(100)
>    );
>    ```
>
>
>
</details>

### In-Class Exercise #3

<details open>
<summary>Exercise: Creating a Data Model</summary>

>Create a class `Product` to represent products in an e-commerce system. Each product should have attributes for name, price, and category. Implement a method to calculate the total price of a given quantity of the product.
>
>```javascript
>class Product {
>    constructor(name, price, category) {
>        this.name = name;
>        this.price = price;
>        this.category = category;
>    }
>
>    calculateTotalPrice(quantity) {
>        return this.price * quantity;
>    }
>}
>
>// Create an instance of the Product class
>const laptop = new Product("Laptop", 999, "Electronics");
>console.log(laptop.calculateTotalPrice(2));  // Output: 1998
>```
>
>
>
</details>

### In-Class Exercise #4

<details open>
<summary>Exercise: Modeling Relationships</summary>

>Create classes to represent a simple social media system. Each `User` should have a list of `Post` objects representing their posts. Implement methods to add a post, remove a post, and display all posts for a user.
>
>```javascript
>class Post {
>    constructor(content) {
>        this.content = content;
>        this.createdAt = new Date();
>    }
>}
>
>class User {
>    constructor(username) {
>        this.username = username;
>        this.posts = [];
>    }
>
>    addPost(content) {
>        const post = new Post(content);
>        this.posts.push(post);
>    }
>
>    removePost(index) {
>        this.posts.splice(index, 1);
>    }
>
>    displayPosts() {
>        this.posts.forEach((post, index) => {
>            console.log(`Post ${index + 1}: ${post.content}`);
>        });
>    }
>}
>
>// Create an instance of the User class and add/remove/display posts
>const user1 = new User("alice");
>user1.addPost("Hello world!");
>user1.addPost("This is my second post.");
>user1.displayPosts();
>// Output:
>// Post 1: Hello world!
>// Post 2: This is my second post.
>user1.removePost(0);
>user1.displayPosts();
>// Output:
>// Post 1: This is my second post.
>```
>
>
>
</details>



---
## 📦 ES6 Modules

<details open>
<summary>Introduction to ES6 Modules</summary>

>ES6 Modules provide a way to organize code into separate files and reuse it across multiple files or projects. Each file is treated as a separate module, and you can export functions, classes, or variables from one module and import them into another.
>
>```javascript
>// math.js
>export function add(a, b) {
>    return a + b;
>}
>
>// main.js
>import { add } from './math.js';
>
>console.log(add(5, 3));  // Output: 8
>```
>
>
>
</details>

<details open>
<summary>Exporting and Importing</summary>

>To export a function, class, or variable from a module, you use the `export` keyword followed by the name of the entity you want to export. To import it in another module, you use the `import` keyword followed by the entity name and the path to the module file.
>
>```javascript
>// Exporting from math.js
>export function multiply(a, b) {
>    return a * b;
>}
>
>// Importing into main.js
>import { multiply } from './math.js';
>
>console.log(multiply(5, 3));  // Output: 15
>```
>
>
>
</details>

### In-Class Exercise #5

<details open>
<summary>Exercise: Creating and Importing Modules</summary>

>Create two modules: one for a `Calculator` class with methods for addition, subtraction, multiplication, and division, and another for a `Main` script that imports the `Calculator` module and performs some calculations.
>
>```javascript
>// calculator.js
>export class Calculator {
>    add(a, b) {
>        return a + b;
>    }
>
>    subtract(a, b) {
>        return a - b;
>    }
>
>    multiply(a, b) {
>        return a * b;
>    }
>
>    divide(a, b) {
>        if (b === 0) {
>            throw new Error("Division by zero");
>        }
>        return a / b;
>    }
>}
>
>// main.js
>import { Calculator } from './calculator.js';
>
>const calc = new Calculator();
>console.log(calc.add(5, 3));       // Output: 8
>console.log(calc.subtract(5, 3));  // Output: 2
>console.log(calc.multiply(5, 3));  // Output: 15
>console.log(calc.divide(6, 3));    // Output: 2
>```
>
>
>
</details>

### In-Class Exercise #6

<details open>
<summary>Exercise: Using Named and Default Exports</summary>

>Create a module that exports multiple functions using named exports and a default export. Then, import both types of exports into another module and use them.
>
>```javascript
>// utils.js
>export function sum(a, b) {
>    return a + b;
>}
>
>export function subtract(a, b) {
>    return a - b;
>}
>
>export default function multiply(a, b) {
>    return a * b;
>}
>
>// main.js
>import multiply, { sum, subtract } from './utils.js';
>
>console.log(sum(5, 3));        // Output: 8
>console.log(subtract(5, 3));   // Output: 2
>console.log(multiply(5, 3));   // Output: 15
>```
>
>
>
</details>


