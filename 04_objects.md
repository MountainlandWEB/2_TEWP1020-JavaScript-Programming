
# 04: Objects

#### [Table of Contents](#table-of-contents)

- [Intro](#intro)
- [Object Basics](#object-basics)
  - [structure](#structure)
  - [Notation](#notation)
  - ["this" and Constructors](#this-and-constructors)
  - [In-class Exercise #1](#in-class-exercise-1)
- [Object Prototypes](#object-prototypes)
  - [Prototype Chain](#prototype-chain)
  - [Shadowing Properties](#shadowing-properties)
  - [In-class Exercise #2](#in-class-exercise-2)
- [Classes and Instances](#classes-and-instances)
  - [In-class Exercise #3](#in-class-exercise-3)
- [Inheritance](#inheritance)
  - [In-class Exercise #4](#in-class-exercise-4)
- [Encapsulation](#encapsulation)
  - [In-class Exercise #5](#in-class-exercise-5)

# Intro 

![alt text](https://media.giphy.com/media/e7C2wQpE2UwvqZCdzh/giphy.gif?cid=ecf05e474bsf3ssi2sw7of7qmcya4e1l3vd5cvwjsbz9af0h&ep=v1_gifs_search&rid=giphy.gif&ct=g)

<i>Great Job on getting this far in your coding journey. As we dive deeper into javaScript, it will get more challenging and you might feel like the guy above.<i>

<i>But keep pushing forward and learn from your mistakes. And ENJOY THE JOURNEY. This will help you improve tremendously.<i>

<i>Objects are extremely important in programming. Truly understanding this lesson will create a foundation that will separate you from your peers in the future.<i>

# Object Basics 

## structure

![alt text](https://i.pinimg.com/originals/49/48/dc/4948dc62ca7fc8fc4783ee14ef47a5af.jpg)

<details open>
<summary>What is an object's structure\</summary>

> An object in JavaScript is a collection of key-value pairs, where each key is a string (or symbol) and each value can be any data type. The structure of an object is defined using curly braces `{}`. Inside the curly braces, you can define properties and methods of the object.
>
> Properties are defined using the syntax `key: value`, where the key is a string and the value can be any valid JavaScript expression. Methods are defined as functions assigned to a key.
>
> Here is an example of an object with two properties and one method:
>
>```javascript
> // Example 1: Object with properties
> const example1 = {
>     name: "John", // Property: name with value "John"
>     age: 25, // Property: age with value 25
> };
> 
> // Example 2: Object with nested properties
> const example2 = {
>     name: "Jane", // Property: name with value "Jane"
>     age: 30, // Property: age with value 30
>     address: { // Property: address with nested object
>         street: "123 Main St", // Nested property: street with value "123 Main St"
>         city: "New York", // Nested property: city with value "New York"
>         country: "USA", // Nested property: country with value "USA"
>    },
> };
> 
> // Example 3: Object created using constructor function
> function Person(name, age) {
>     this.name = name; // Property: name with value passed as argument
>     this.age = age; // Property: age with value passed as argument
> }
> 
> const example3 = new Person("Mike", 35); // Object created using Person constructor
>```

</details>

<details open>
<summary>objects vs arrays</summary>

> Objects and arrays are both data structures in JavaScript, but they have some key differences.
>
>![alt text](https://images.pexels.com/photos/1080882/pexels-photo-1080882.jpeg?auto=compress&cs=tinysrgb&w=800)
>
> Imagine you have a sports league with different teams. Each team has a name, players, and achievements. 
>
> If we represent each team as an object, we can define properties like `name`, `players`, and `achievements` for each team. For example:
>
> ```javascript
> const team1 = {
>     name: "Lakers",
>     players: ["LeBron James", "Anthony Davis", "Russell Westbrook"],
>     achievements: ["NBA Championships", "Conference Titles"],
> };
> 
> const team2 = {
>     name: "Warriors",
>     players: ["Stephen Curry", "Klay Thompson", "Draymond Green"],
>     achievements: ["NBA Championships", "Regular Season Records"],
> };
> ```

> On the other hand, if we represent the teams as an array, we can store multiple teams in a single data structure. For example:

> ```javascript
> const teams = [team1, team2];
> ```
> On the other hand, if we represent the teams as an ARRAY, we can store multiple teams in a single data structure. For example:

> ```javascript
> const teams = [team1, team2];
> ```

</details>

## Notation

<details open>
<summary>What is notation and why do we need it in objects</summary>

> Notation in objects allows us to access and manipulate the properties and methods of an object. 
>
>It provides a way to interact with the data stored within an object and perform operations on it. Without notation, we wouldn't be able to effectively work with objects in JavaScript.
>

</details>

<details open>
<summary>Bracket vs Dot Notation:</summary>

> 
> Bracket notation and dot notation are two ways to access and modify the properties of an object in JavaScript.
> 
> Dot notation is the most common and straightforward way to access object properties. It uses the dot operator (`.`) followed by the property name. For example:
> 
> ```javascript
> const person = {
>     name: "John",
>     age: 25,
> };
> 
> console.log(person.name); // Output: "John"
> ```
> 
> Bracket notation, on the other hand, uses square brackets (`[]`) to access object properties. It allows us to use dynamic property names or property names that contain special characters. For example:
> 
> ```javascript
> const person = {
>     name: "John",
>     age: 25,
> };
> 
> console.log(person["name"]); // Output: "John"
> ```
> 
> Both notation methods are valid and can be used interchangeably in most cases. However, bracket notation is necessary when working with dynamic property names or property names that are not valid JavaScript identifiers. For example:
> 
> ```javascript
> const propertyName = "name";
> console.log(person[propertyName]); // Output: "John"
> ```
> 
> It's important to note that dot notation is generally preferred for its simplicity and readability, while bracket notation is more flexible in certain scenarios.
> 
> Here are some coding examples for each notation:
> 
> ```javascript
> const person = {
>     name: "John",
>     age: 25,
> };
> 
> // Dot notation
> console.log(person.name); // Output: "John"
> 
> // Bracket notation
> console.log(person["age"]); // Output: 25
> 
> // Using dynamic property names
> const propertyName = "name";
> console.log(person[propertyName]); // Output: "John"
> ```
>
</details>

## "this" and Constructors

<details open>
<summary>what is "this"? why do we need it?</summary>

> The "this" keyword in JavaScript refers to the object that is currently being executed or accessed. It allows us to access and manipulate the properties and methods of the object within its own context.
> 
> Imagine you are a chef in a restaurant. You have a recipe book with various recipes, each represented as an object. Each recipe has its own set of ingredients and cooking instructions. When you are following a recipe, you need to refer to the specific recipe you are working on. In this scenario, the recipe you are currently working on is equivalent to the object, and the "this" keyword represents that specific recipe.
>
>![alt text](https://images.pexels.com/photos/7128599/pexels-photo-7128599.jpeg?auto=compress&cs=tinysrgb&w=800)
> 
> The "this" keyword is useful because it allows us to write reusable code. Instead of hard-coding specific values or references, we can use "this" to refer to the current object dynamically. This makes our code more flexible and adaptable, as it can work with different objects without needing to modify the code itself.
> 
> Here is an example to illustrate the usage of the "this" keyword:
> 
> ```javascript
> const recipe = {
>     name: "Chocolate Cake",
>     ingredients: ["flour", "sugar", "cocoa powder", "eggs", "butter"],
>     instructions: function() {
>         console.log("Recipe: " + this.name);
>         console.log("Ingredients: " + this.ingredients.join(", "));
>         console.log("Instructions: Follow the steps below...");
>         // More code here
>     }
> };
> 
> recipe.instructions(); // Output: Recipe: Chocolate Cake, Ingredients: flour, sugar, cocoa powder, eggs, butter, Instructions: Follow the steps below...
> ```
> 
> In the example above, the "instructions" method uses the "this" keyword to access the properties of the "recipe" object. By using "this.name" and "this.ingredients", we can dynamically refer to the specific recipe's name and ingredients, regardless of the object's name or ingredients.
> 
> Overall, the "this" keyword is essential in object-oriented programming as it allows us to work with objects in a more dynamic and flexible manner.
>
</details>


<details open>
<summary>What are constructors? why are they important?</summary>

>
> Constructors in JavaScript are connected to the "this" keyword in the sense that they use "this" to refer to the object being created by the constructor.
>
> Let's connect this to the parable of the chef and recipes. Imagine you are a chef who wants to create multiple recipe objects using a recipe template. The recipe template can be seen as the constructor function. When you create a new recipe object using the constructor, the "this" keyword inside the constructor refers to the specific recipe object being created.
> 
> 
> In the parable, the chef is the constructor function, and the recipes are the objects created using that constructor. When the chef follows a recipe, they need to refer to the specific recipe they are working on. Similarly, when the constructor function is called to create a new object, the "this" keyword inside the constructor refers to that specific object.
>
> ![alt text](https://i.pinimg.com/originals/a5/1d/40/a51d40b47e2b5e8eaa447b9171cfadd1.jpg)
> 
> Here's an example to illustrate this connection:
> 
> ```javascript
> function Recipe(name, ingredients) {
>     this.name = name;
>     this.ingredients = ingredients;
> }
> 
> const recipe1 = new Recipe("Chocolate Cake", ["flour", "sugar", "cocoa powder", "eggs", "butter"]);
> console.log(recipe1.name); // Output: "Chocolate Cake"
> console.log(recipe1.ingredients); // Output: ["flour", "sugar", "cocoa powder", "eggs", "butter"]
> ```
> 
> In the example above, the Recipe function is the constructor. When we create a new recipe object using `new Recipe(...)`, the `this` keyword inside the constructor refers to the newly created object. We use `this.name` and `this.ingredients` to set the properties of the object based on the arguments passed to the constructor.
> 
> So, in summary, constructors in JavaScript are connected to the "this" keyword because they use "this" to refer to the object being created by the constructor. This allows us to set the properties of the object dynamically during its creation.
>
>
>

</details>

## In-class Exercise #1

<details open>
<summary>Exercise: Object Basics</summary>

>1. Create an object named car with properties make, model, and year. Use dot notation to add a color property to the car object.
>2. Create a method inside the car object that returns a string in the format "This car is a [color] [make] [model] from [year]". Use the this keyword to reference the object's properties within the method.
>3. Create a Person object with properties firstName and lastName. Add a method getFullName that returns the full name of the person using the this keyword.
>4. Create a Book constructor function that takes title, author, and year as parameters and assigns them to the object's properties. Create an instance of Book and print its properties.
>5. Add a getSummary method to the Book constructor that returns a string in the format "The book [title] was written by [author] in [year]". Use the this keyword to reference the object's properties within the method. Create an instance of Book and call the getSummary method.
>
>
><details>
><summary>ANSWERS</summary>
>
> 1. Create an object named car with properties make, model, and year. Use dot notation to add a color property to the car object.
> 
> ```javascript
> const car = {
>     make: "Toyota",
>     model: "Camry",
>     year: 2022,
> };
> 
> car.color = "blue";
> ```
> 
> 2. Create a method inside the car object that returns a string in the format "This car is a [color] [make] [model] from [year]". Use the this keyword to reference the object's properties within the method.
> 
> ```javascript
> car.getDescription = function() {
>     return `This car is a ${this.color} ${this.make} ${this.model} from ${this.year}.`;
> };
> 
> console.log(car.getDescription());
> ```
> 
> 3. Create a Person object with properties firstName and lastName. Add a method getFullName that returns the full name of the person using the this keyword.
> 
> ```javascript
> const person = {
>     firstName: "John",
>     lastName: "Doe",
>     getFullName: function() {
>         return `${this.firstName} ${this.lastName}`;
>     },
> };
> 
> console.log(person.getFullName());
> ```
> 
> 4. Create a Book constructor function that takes title, author, and year as parameters and assigns them to the object's properties. Create an instance of Book and print its properties.
> 
> ```javascript
> function Book(title, author, year) {
>     this.title = title;
>     this.author = author;
>     this.year = year;
> }
> 
> const book1 = new Book("The Great Gatsby", "F. Scott Fitzgerald", 1925);
> console.log(book1);
> ```
> 
> 5. Add a getSummary method to the Book constructor that returns a string in the format "The book [title] was written by [author] in [year]". Use the this keyword to reference the object's properties within the method. Create an instance of Book and call the getSummary method.
> 
> ```javascript
> Book.prototype.getSummary = function() {
>     return `The book ${this.title} was written by ${this.author} in ${this.year}.`;
> };
> 
> console.log(book1.getSummary());
> ```
></details>
>

</details>

# Object Prototypes

>In JavaScript, every object has a prototype. 
>
>The prototype is an object from which the object inherits properties and methods. It acts as a blueprint or template for creating other objects.

>Prototypes enable object-oriented programming features like *inheritance* and *code reuse*. 

>By defining properties and methods in a prototype, you can create multiple objects that share those properties and methods, reducing code duplication and improving maintainability.

![alt text](https://www.ssla.co.uk/wp-content/uploads/2020/08/prototype.png)


## Prototype Chain

<details open>
<summary>parable of the Prototype Chain</summary>

>Imagine a family tree where each generation inherits traits from their ancestors. 

>In JavaScript, objects are like family members, and the prototype chain is their lineage. When an object needs a property or method not found within itself, it looks up the chain to its ancestors until it finds what it's looking for. 

![alt text](https://t4.ftcdn.net/jpg/02/74/47/11/360_F_274471161_XyH7ZxJrhfbtN8X7cNdczZj2ocLUALuY.jpg)

>This allows objects to share and inherit properties and methods, creating a dynamic network of relationships that powers JavaScript's powerful inheritance model.

</details>

<details open>
<summary>What is the Prototype Chain? Why is it important</summary>

> The prototype chain is the mechanism by which JavaScript objects inherit properties and methods from their prototype.
> 
> When accessing a property or method on an object, JavaScript first checks if the object itself has that property or method.
> 
> If not, it looks up the prototype chain to find the property or method in the object's prototype.
> 
> If the property or method is still not found, it continues to look up the prototype chain until it reaches the top-level object, which is usually the Object.prototype.
>

>```javascript
> 
> // Example:
> const person = {
>     name: "John",
>     age: 25,
> };
> 
> console.log(person.hasOwnProperty("name")); // Output: true
> console.log(person.hasOwnProperty("toString")); // Output: false
> 
> // In the example above, the person object has its own property "name", so person.hasOwnProperty("name") returns true.
> // However, person does not have its own property "toString", so person.hasOwnProperty("toString") returns false.
> // Instead, person inherits the "toString" method from the Object.prototype through the prototype chain.
> 
> // Shadowing Properties
> // Shadowing occurs when a property with the same name exists both in an object and its prototype.
> // When accessing the property, JavaScript first checks if the property exists in the object itself.
> // If it does, it uses the object's property and does not look up the prototype chain.
> // This behavior allows objects to override properties inherited from their prototype.
> 
> // Example:
> const vehicle = {
>     color: "blue",
> };
> 
> const car = Object.create(vehicle);
> car.color = "red";
> 
> console.log(car.color); // Output: red
> 
> // In the example above, the car object has its own property "color" with the value "red".
> // When accessing car.color, JavaScript finds the property in the car object itself and uses that value.
> // It does not look up the prototype chain to find the "color" property in the vehicle object.
> 
> // Classes and Instances
> // Classes in JavaScript are a syntactical sugar over the prototype-based inheritance model.
> // They provide a more familiar and structured way to define objects and their behavior.
> // An instance of a class is an object created from that class, which inherits properties and methods from the class's prototype.
> 
> // Example:
> class Person {
>     constructor(name, age) {
>         this.name = name;
>         this.age = age;
>     }
> 
>     sayHello() {
>         console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
>     }
> }
> 
> const john = new Person("John", 25);
> john.sayHello(); // Output: Hello, my name is John and I'm 25 years old.
> 
> // In the example above, the Person class defines a constructor and a method.
> // The constructor is called when creating a new instance of the class, and it sets the name and age properties.
> // The sayHello method is defined on the class's prototype and can be accessed by instances of the class.
> 
> // Inheritance
> // Inheritance allows objects to inherit properties and methods from a parent object or class.
> // It promotes code reuse and allows for creating more specialized objects based on a common blueprint.
> 
> // Example:
> class Animal {
>     constructor(name) {
>         this.name = name;
>     }
> 
>     speak() {
>         console.log(`${this.name} makes a sound.`);
>     }
> }
> 
> class Dog extends Animal {
>     constructor(name, breed) {
>         super(name);
>         this.breed = breed;
>     }
> 
>     speak() {
>         console.log(`${this.name} barks.`);
>     }
> }
> 
> const dog = new Dog("Buddy", "Labrador");
> dog.speak(); // Output: Buddy barks.
> 
> // In the example above, the Animal class defines a constructor and a speak method.
> // The Dog class extends the Animal class using the extends keyword.
> // It also defines its own constructor and speak method, which overrides the ones inherited from Animal.
> // The super keyword is used in the Dog constructor to call the parent class's constructor and set the name property.
> 
> // Encapsulation
> // Encapsulation is the practice of bundling data and methods that operate on that data into a single unit, called an object.
> // It allows for better organization, modularity, and abstraction of code.
> 
> // Example:
> class Counter {
>     constructor() {
>         this.count = 0;
>     }
> 
>     increment() {
>         this.count++;
>     }
> 
>     decrement() {
>         this.count--;
>     }
> 
>     getCount() {
>         return this.count;
>     }
> }
> 
> const counter = new Counter();
> counter.increment();
> counter.increment();
> counter.decrement();
> console.log(counter.getCount()); // Output: 1
> 
> // In the example above, the Counter class encapsulates the count data and methods that operate on it.
> // The count property is initialized in the constructor and can be accessed and modified through the increment, decrement, and getCount methods.
> // The getCount method provides a way to retrieve the current count value without directly accessing the count property.
> 
> // These are some examples of object-oriented concepts in JavaScript. They demonstrate how to use prototypes, classes, inheritance, and encapsulation to create and work with objects.
> ```
>

</details>

## Shadowing Properties

<details open>
<summary>parable of Shadowing Properties</summary>

>shadowing properties refers to the concept where an object inherits a property from its prototype, but then defines its own property with the same name, effectively overshadowing the inherited one. 

>This allows the object to have its own version of the property, distinct from that of its prototype. 

>Similarly, in life, we often inherit traits and knowledge from our predecessors but have the opportunity to develop and express our unique qualities, thus shadowing the influence of our ancestors while still acknowledging their impact on our journey.
>
>
</details>

<details open>
<summary>Coding examples of Shadowing Properties</summary>

>```javascript
> // Example of shadowing properties
> // In this example, we have two constructor functions: Animal and Dog.
> // Animal has a property "name" and a method "speak".
> // Dog extends Animal and adds its own property "breed" and overrides the "speak" method.
> // When we create an instance of Dog and call the "speak" method, it uses the overridden method in Dog instead of the one inherited from Animal.
> 
> function Animal(name) {
>     this.name = name;
> }
> 
> Animal.prototype.speak = function() {
>     console.log(`${this.name} makes a sound.`);
> };
> 
> function Dog(name, breed) {
>     Animal.call(this, name);
>     this.breed = breed;
> }
> 
> Dog.prototype = Object.create(Animal.prototype);
> Dog.prototype.constructor = Dog;
> 
> Dog.prototype.speak = function() {
>     console.log(`${this.name} barks.`);
> };
> 
> const dog = new Dog("Buddy", "Labrador");
> dog.speak(); // Output: Buddy barks.
> ```
</details>

## In-class Exercise #2

<details open>
<summary>Exercise: Prototypes</summary>

>```javascript
>// Create a prototype method for the Book constructor that returns the title, author, and year in a formatted string.
>
>Book.prototype.getInfo = function() {
>    return `Title: ${this.title}\nAuthor: ${this.author}\nYear: ${this.year}`;
>};
>
>const book1 = new Book("The Great Gatsby", "F. Scott Fitzgerald", 1925);
>console.log(book1.getInfo());
>
> // Exercise 1: Create a prototype method for the Book constructor that returns the number of pages in the book.
> Book.prototype.getNumberOfPages = function() {
>     return this.pages;
> };
> 
> const book1 = new Book("The Great Gatsby", "F. Scott Fitzgerald", 1925, 218);
> console.log(book1.getNumberOfPages());
> 
> // Exercise 2: Create a prototype method for the Book constructor that checks if the book is a classic (published before 1950).
> Book.prototype.isClassic = function() {
>     return this.year < 1950;
> };
> 
> const book2 = new Book("Pride and Prejudice", "Jane Austen", 1813, 432);
> console.log(book2.isClassic());
> 
> // Exercise 3: Create a prototype method for the Book constructor that calculates the average rating of the book based on an array of ratings.
> Book.prototype.calculateAverageRating = function() {
>     if (this.ratings.length === 0) {
>         return "No ratings available.";
>     }
>     
>     const sum = this.ratings.reduce((total, rating) => total + rating, 0);
>     return sum / this.ratings.length;
> };
> 
> const book3 = new Book("To Kill a Mockingbird", "Harper Lee", 1960, 281);
> book3.ratings = [4, 5, 4.5, 3.5];
> console.log(book3.calculateAverageRating());
> 
> // Exercise 4: Create a prototype method for the Book constructor that adds a new genre to the book's genres array.
> Book.prototype.addGenre = function(genre) {
>     this.genres.push(genre);
> };
> 
> const book4 = new Book("1984", "George Orwell", 1949, 328);
> book4.genres = ["Dystopian", "Science Fiction"];
> book4.addGenre("Political Fiction");
> console.log(book4.genres);
</details>

# Classes and Instances

<details open>
<summary>parable of Classes & Instances</summary>

>imagine a bakery that produces different types of cakes. The bakery itself represents a class, which is like a blueprint or a template for creating cakes.

>the bakery produces a specific cake called "Vanilla Cake". Each individual cake is based on the bakery's blueprint is an instance of the class. These instances have their own unique characteristics, such as size, flavor, and decoration.

![alt text](https://media4.giphy.com/media/l2JhIAxlJE0421wVq/giphy.gif?cid=6c09b952zzyvpiav8ukwg2g3530b6u1dz0ewrtath2h9obk2&ep=v1_internal_gif_by_id&rid=giphy.gif&ct=g)

>In JavaScript, classes and instances work in a similar way. A *class* defines the structure and behavior of an object, while an *instance* is a specific object created from that class. The class serves as a blueprint, providing the properties and methods that each instance will have.

>By using classes and instances, we can create multiple objects with similar characteristics and behaviors, without having to rewrite code
</details>

<details open>
<summary></summary>

>```javascript
> // Example 1: Simple Class and Instance
> // Create a class called Rectangle that represents a rectangle shape.
> // The class has properties for width and height, and a method to calculate the area.
> 
> class Rectangle {
>     constructor(width, height) {
>         this.width = width;
>         this.height = height;
>     }
> 
>     calculateArea() {
>         return this.width * this.height;
>     }
> }
> 
> const rectangle1 = new Rectangle(5, 10);
> console.log(rectangle1.calculateArea()); // Output: 50
> 
> // Example 2: Inheritance
> // Create a class called Square that extends the Rectangle class.
> // The Square class has an additional property for side length and overrides the calculateArea method.
> 
> class Square extends Rectangle {
>     constructor(sideLength) {
>         super(sideLength, sideLength);
>         this.sideLength = sideLength;
>     }
> 
>     calculateArea() {
>         return this.sideLength ** 2;
>     }
> }
> 
> const square1 = new Square(5);
> console.log(square1.calculateArea()); // Output: 25
> 
> // Example 3: Complex Class Hierarchy
> // Create a class called Shape that represents a generic shape.
> // The Shape class has a property for color and a method to print the color.
> 
> class Shape {
>     constructor(color) {
>         this.color = color;
>     }
> 
>     printColor() {
>         console.log(`The color of the shape is ${this.color}.`);
>     }
> }
> 
> // Create a class called Circle that extends the Shape class.
> // The Circle class has an additional property for radius and overrides the printColor method.
> 
> class Circle extends Shape {
>     constructor(color, radius) {
>         super(color);
>         this.radius = radius;
>     }
> 
>     printColor() {
>         console.log(`The color of the circle is ${this.color}.`);
>     }
> 
>     calculateArea() {
>         return Math.PI * this.radius ** 2;
>     }
> }
> 
> // Create a class called Cylinder that extends the Circle class.
> // The Cylinder class has an additional property for height and overrides the calculateArea method.
> 
> class Cylinder extends Circle {
>     constructor(color, radius, height) {
>         super(color, radius);
>         this.height = height;
>     }
> 
>     calculateArea() {
>         const baseArea = super.calculateArea();
>         const lateralArea = 2 * Math.PI * this.radius * this.height;
>         return 2 * baseArea + lateralArea;
>     }
> }
> 
> const cylinder1 = new Cylinder("blue", 3, 5);
> cylinder1.printColor(); // Output: The color of the circle is blue.
> console.log(cylinder1.calculateArea()); // Output: 150.79644737231007
>```
</details>

## In-class Exercise #3

<details open>
<summary>Exercise: Classes & Instances</summary>

>```javascript
> // Challenge 1: Create a class called Person with properties for name and age. Implement a method to introduce the person.
> class Person {
>     constructor(name, age) {
>         this.name = name;
>         this.age = age;
>     }
> 
>     introduce() {
>         console.log(`Hi, my name is ${this.name} and I am ${this.age} years old.`);
>     }
> }
> 
> const person1 = new Person("John", 25);
> person1.introduce();
> 
> // Challenge 2: Create a class called BankAccount with properties for account number and balance. Implement methods to deposit and withdraw money from the account.
> class BankAccount {
>     constructor(accountNumber, balance) {
>         this.accountNumber = accountNumber;
>         this.balance = balance;
>     }
> 
>     deposit(amount) {
>         this.balance += amount;
>     }
> 
>     withdraw(amount) {
>         if (amount <= this.balance) {
>             this.balance -= amount;
>         } else {
>             console.log("Insufficient funds.");
>         }
>     }
> }
> 
> const account1 = new BankAccount("123456789", 1000);
> account1.deposit(500);
> account1.withdraw(200);
> console.log(account1.balance);
> 
> // Challenge 3: Create a class called ShoppingCart with properties for items and total. Implement methods to add items to the cart, remove items from the cart, and calculate the total price.
> class ShoppingCart {
>     constructor() {
>         this.items = [];
>         this.total = 0;
>     }
> 
>     addItem(item) {
>         this.items.push(item);
>         this.total += item.price;
>     }
> 
>     removeItem(item) {
>         const index = this.items.indexOf(item);
>         if (index !== -1) {
>             this.items.splice(index, 1);
>             this.total -= item.price;
>         }
>     }
> 
>     calculateTotal() {
>         return this.total;
>     }
> }
> 
> const cart1 = new ShoppingCart();
> const item1 = { name: "Item 1", price: 10 };
> const item2 = { name: "Item 2", price: 20 };
> cart1.addItem(item1);
> cart1.addItem(item2);
> cart1.removeItem(item1);
> console.log(cart1.calculateTotal());
>```
</details>

# Inheritance

<details open>
<summary>parable of Inheritance</summary>

>Inheritance is akin to a torch passed down through generations. Just as a flame illuminates the darkness, inheritance empowers objects to carry forward the traits and capabilities of their predecessors. 

>Like a lineage of torchbearers, each object inherits the wisdom of its ancestors, enabling it to navigate the complexities of code with clarity and purpose. 

>![alt text](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWRhem1maXZiN2VpY280ZXhsaGhxdWtvNGpidm51eHowMTIwMDU0eSZlcD12MV9naWZzX3NlYXJjaCZjdD1n/wofUBtNDIGwYJ0FaPL/100.webp)

>Through inheritance, JavaScript objects forge a timeless connection to their past, lighting the way toward innovation and progress in the ever-evolving landscape of programming.
>

</details>

<details open>
<summary></summary>

>```javascript
> // Create a parent class called Animal with a property for name.
> class Animal {
>     constructor(name) {
>         this.name = name;
>     }
> 
>     speak() {
>         console.log(`${this.name} makes a sound.`);
>     }
> }
> 
> // Create a child class called Dog that extends the Animal class.
> // The Dog class has an additional property for breed and overrides the speak method.
> class Dog extends Animal {
>     constructor(name, breed) {
>         super(name);
>         this.breed = breed;
>     }
> 
>     speak() {
>         console.log(`${this.name} barks.`);
>     }
> }
> 
> const dog = new Dog("Buddy", "Labrador");
> dog.speak(); // Output: Buddy barks.
>```

</details>

## In-class Exercise #4

<details open>
<summary>Exercise: Inheritance</summary>

>```javascript
> // Create a parent class called Vehicle with properties for make and model.
> class Vehicle {
>     constructor(make, model) {
>         this.make = make;
>         this.model = model;
>     }
> 
>     getInfo() {
>         return `Make: ${this.make}\nModel: ${this.model}`;
>     }
> }
> 
> // Create a child class called Car that extends the Vehicle class.
> // The Car class has an additional property for year and overrides the getInfo method.
> class Car extends Vehicle {
>     constructor(make, model, year) {
>         super(make, model);
>         this.year = year;
>     }
> 
>     getInfo() {
>         return `${super.getInfo()}\nYear: ${this.year}`;
>     }
> }
> 
> const car1 = new Car("Toyota", "Camry", 2022);
> console.log(car1.getInfo());
>```

</details>

# Encapsulation

<details open>
<summary>What is Encapsulation? (parable time)</summary>

>Encapsulation serves as the guardian of knowledge, shielding the inner workings of objects from external interference. 

>Like a treasure chest locked tight, encapsulation safeguards the integrity of data and functionality within each object, allowing it to operate independently and securely. 

>![alt text](https://media3.giphy.com/media/OE9hKAfUkurx44b5cE/giphy.webp?cid=ecf05e47fqbo9z4zvah8er1tjm9l0g3edpaa7tx597jgnaba&ep=v1_gifs_search&rid=giphy.webp&ct=g)

>Through encapsulation, JavaScript objects maintain a veil of privacy, revealing only what is necessary while concealing the intricacies beneath the surface. 

>Thus, encapsulation empowers objects to uphold their sovereignty in the digital realm, fostering a realm where information flows freely within, yet remains protected from external forces.

</details>

<details open>
<summary>Encapsulation Coding Example #1</summary>

>```javascript
> // Create a class called Counter with a private count variable and public methods to increment and get the count.
> class Counter {
>     constructor() {
>         let count = 0; // Private variable
> 
>         this.increment = function() {
>             count++;
>         };
> 
>         this.getCount = function() {
>             return count;
>         };
>     }
> }
> 
> const counter = new Counter();
> counter.increment();
> console.log(counter.getCount()); // Output: 1
</details>

<details open>
<summary>Encapsulation Coding Example #2</summary>

>```javascript
> // Create a class called BankAccount with private properties for account number and balance.
> class BankAccount {
>     constructor(accountNumber, initialBalance) {
>         let accountNum = accountNumber; // Private property
>         let balance = initialBalance; // Private property
> 
>         this.deposit = function(amount) {
>             balance += amount;
>         };
> 
>         this.withdraw = function(amount) {
>             if (amount <= balance) {
>                 balance -= amount;
>             } else {
>                 console.log("Insufficient funds.");
>             }
>         };
> 
>         this.getAccountNumber = function() {
>             return accountNum;
>         };
> 
>         this.getBalance = function() {
>             return balance;
>         };
>     }
> }
> 
> const account = new BankAccount("123456789", 1000);
> account.deposit(500);
> account.withdraw(200);
> console.log(account.getAccountNumber()); // Output: 123456789
> console.log(account.getBalance()); // Output: 1300
>```

</details>

## In-class Exercise #5


<details open>
<summary>Exercise: Encapsulation</summary>

>```javascript
> // Create a class called Employee with private properties for name and salary.
> // Implement public methods to get the name and salary, and a method to give a raise to the employee.
> class Employee {
>     constructor(name, salary) {
>         let employeeName = name; // Private property
>         let employeeSalary = salary; // Private property
> 
>         this.getName = function() {
>             return employeeName;
>         };
> 
>         this.getSalary = function() {
>             return employeeSalary;
>         };
> 
>         this.giveRaise = function(amount) {
>             employeeSalary += amount;
>         };
>     }
> }
> 
> const employee = new Employee("John Doe", 50000);
> console.log(employee.getName()); // Output: John Doe
> console.log(employee.getSalary()); // Output: 50000
> employee.giveRaise(10000);
> console.log(employee.getSalary()); // Output: 60000
>```

</details>
