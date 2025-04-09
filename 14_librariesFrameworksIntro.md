# 14: Intro to Libraries and Frameworks

### [📄 Table of contents](#-table-of-contents)

  - [📰 Intro](#-intro)
  - [📚 Libraries](#-libraries)
  - [🏗️ Frameworks](#️-frameworks)
   
---

## 📰 Intro
The concept behind frameworks and libraries is to provide reusable code that you can use to perform everyday tasks so that developers don’t have to write all of the code from scratch for every project.

Frameworks and libraries are designed to be modular and reusable, meaning they can be used in multiple projects without needing to rewrite the code. This can save developers a significant amount of time and effort and also help to improve the reliability and maintainability of the code.

In addition to providing reusable code, frameworks and libraries can offer a set of best practices and conventions for structuring and organizing code, which can help developers build more scalable and maintainable applications.

A library is a group of operations that programmers can call at a whim and still have complete control over the software application’s flow. The actions that libraries are expected to take are stated carefully and precisely.

An application describes the substance of the action by requesting the developer to fill in the blanks in a framework, which is a structure. The developer specifies the functionality with the end-user in mind, while a framework establishes the notion using a set of libraries or tools to accomplish the task.

## 📚 Libraries
What are libraries?

A library is a collection of pre-written code that you can use to perform specific tasks. Libraries are often used to reduce the amount of code a programmer needs to write by providing reusable functions or classes that can be called upon as needed.

All libraries are shared into two classifications. All libraries are either Static or Dynamic.

Dynamic libraries: Dynamic libraries are loaded at runtime rather than linked with a program at compile time. This allows programs to use the library without having to be re-compiled if the library is updated. In addition, dynamic libraries are often used to provide platform-specific functionality or to allow multiple programs to share a single copy of the library in memory.
Static libraries: These are compiled into a program’s executable code, making it self-contained and independent of external changes. Static libraries are linked with a program at compile time, resulting in a single executable file that includes all of the code from the library. As a result, static libraries are often used to improve the performance of a program by avoiding the overhead of loading a library at runtime.
You can write libraries in most programming languages, and they can be used by programs written in that same language or a different language. For example, a library written in C++ could be used by a program written in Python.

While there are two main classifications of libraries, there are many different types of libraries, including:

Standard libraries: These are libraries that are included with a programming language by default. These libraries provide a set of standard functions and utilities that are useful for many applications. For example, the C standard library includes functions for input/output, string manipulation, memory allocation, and mathematical operations.

Third-party libraries: These libraries are developed by organizations or individuals other than the creators of the programming language. These libraries can provide additional functionality that is not included in the standard library and may be distributed as open-source or commercial products.
Libraries can perform various tasks, such as file input and output, data manipulation, network communication, and more. They can also provide access to system resources, such as the file system or hardware devices.

## 🏗️ Frameworks
A framework is a set of libraries or tools that provide a structure for building applications. It typically includes code libraries, templates, and guidelines for how to use the libraries to develop applications.

Frameworks can be useful for developers because they provide a standardized way to build and organize code, which can help streamline the development process and make it easier to build and maintain complex applications. They can also help developers to build applications that are more reliable and scalable, as the framework provides a set of best practices and conventions to follow.

Frameworks are used in various programming sectors like:
Web development: This employs a variety of languages, including JavaScript (Angular), Python (Django), and PHP (CodeIgniter, Laravel).
Popular artificial intelligence frameworks include Tensorflow, Accord.Net, etc.
Development of mobile apps: Native Script, React Native, and Flutter is a few of the well-liked frameworks. 
These are many different types of frameworks available, ranging from web application frameworks to game development frameworks to mobile application frameworks. Some examples of popular frameworks include:
+ Ruby on Rails, a web application framework for the Ruby programming language
+ Angular, a JavaScript framework for building single-page web applications
+ Unity, a game development engine for building 2D and 3D games

Each framework has its own set of features and capabilities, and developers can choose the one that best meets their needs for a particular project.

## ✨Pros and Cons of Libraries
When choosing between frameworks and libraries, it is important to take into account all of their possibilities, advantages, and disadvantages.

### Pros of libraries
There are several benefits to using programming libraries:
+ Reusability: Programming libraries allow you to reuse code that has already been written and tested, saving you time and effort. This means you don’t have to reinvent the wheel whenever you want to perform a common task.
+ Quality: Programming libraries are typically well-tested and debugged, so you can be confident that the code is reliable and will work as intended.
+ Maintainability: Programming libraries can make maintaining your code easier over time. Since the library code is separate from your code, you can update or upgrade the library without affecting your codebase.
+ Community support: Many popular programming libraries have large user bases and active communities, so you can often find help or resources online if you have questions or run into issues.
+ Standardization: Programming libraries help ensure that your code is consistent and follows established best practices. This can make it easier for other developers to understand and work with your code.
+ Encapsulation: Ignores global state management issues like HTTP and routing in favor of concentrating directly on the functionality that the library implements.
+ Developer time: Lowers the cost of developing applications by providing pre-built solutions to handle random tasks.

### Cons of libraries
There are equally some potential drawbacks to using programming libraries:
+ Dependencies: Using programming libraries can introduce dependencies into your codebase. This means that if the library changes or is no longer supported, it could break your code or require you to make changes. This is particularly a problem with dynamic libraries.
+ Bloat: Depending on the size and complexity of the library, it could add unnecessary bloat to your codebase, which could impact the performance of your application.
+ Compatibility: Not all libraries are compatible with all programming languages or platforms. This means you may have to choose a different library or find a way to make it work with your technology stack.
+ Lack of control: When you use a programming library, you have to rely on its functionality. This means you may have less control over how a particular task is performed than writing your code from scratch.
+ Learning curve: Using a new programming library can take time to learn and understand. This can be a barrier for some developers, especially if the library has a steep learning curve or needs better documentation.
+ Performance: A wrapper is required when using a library in an unsupported environment, which slows the application.

## ✨Pros and Cons of Frameworks
### Pros of Frameworks
There are several benefits to using frameworks in programming:
+ Structure and organization: Frameworks provide structure and organization for your code, making it easier to develop and maintain common types of applications by bringing together the libraries and tools needed. This can be especially helpful for large or complex projects.
+ Reusability: Frameworks often include reusable components or libraries that can save you time and effort. This means you can write less code from scratch and offers quicker solutions for web development.
+ Best practices: Frameworks often embody established best practices and design patterns, which can help ensure that your code is well-designed and maintainable.
+ Community support: Many popular frameworks have large user bases and active communities, so you can often find help or resources online if you have questions or run into issues.
+ Scalability: Frameworks are often designed with scalability in mind, which means they can handle large requests or traffic without performance issues. This can be especially important for applications that are expected to grow or have high usage levels.
+ Encapsulation: The entire application is unaffected by a change to a single component.
+ Compatibility: Encourages the development of cross-platform applications.
+ Quality: Creates rich, dynamic content that offers a better user experience with less skill required.
+ Data binding: Because several JavaScript frameworks, like Angular, are built on a common architectural pattern called MVC.

### Cons of Frameworks
There are a few potential drawbacks to using frameworks in programming:
+ Complexity: Some frameworks can be complex and have a steep learning curve, which can be intimidating for beginner developers.
+ Limited flexibility: Frameworks often have a specific way of doing things, which can be inflexible if you want to do something outside the framework’s scope. Also, a framework’s ready-to-use features restrict programmers from fully knowing the programming language.
+ Performance overhead: Some frameworks can add a performance overhead, which can impact the speed of your application.
+ Dependency on the framework: If you build your application using a specific framework, you may become reliant on it, making it more challenging to switch to a different one.
+ Lock-in: Using a framework can also lead to lock-in, where you are tied to a specific set of technologies and unable to switch to alternatives easily.
+ Complexity: For example. in MVC, separating the presentation layer from the business logic might be challenging.
+ Compatibility: Only a browser environment that supports JavaScript can use JavaScript frameworks.
+ Unexpected consequences: As an example, if recommended framework guideline is not followed while developing, there is a chance of a security breach.

## ✨Libraries and frameworks: Similarities and differences
Libraries offer pre-set functions and classes to developers to streamline their work and speed up the development process. Contrarily, a framework is akin to the base upon which programmers create apps for specific platforms.

Both libraries and frameworks are collections of pre-written code that developers can utilize to speed up the creation of software programs. In addition, they offer several classes or functions that can carry out typical activities, such as communicating with databases, managing user input, or producing graphics.

### Similarities
There are several similarities between libraries and frameworks:
+ Both libraries and frameworks provide functions or classes that developers can use to perform everyday tasks.
+ Both libraries and frameworks are designed to be reusable, so developers do not have to write the same code repeatedly.
+ The process for installing libraries and frameworks is the same (e.g, installing the Numpy library and the TensorFlow framework on a computer can both be done using the pip package installer by running the command “pip install numpy” and “pip install tensorflow“, respectively, in the command line. The process for installing the library and the framework is the same, as both are done using the same package installer and the same type of command.). 
+ Both libraries and frameworks can save time and effort when building software applications.

One way to illustrate the similarities between libraries and frameworks is with an example. Suppose you are building a web application that needs to authenticate users and allow them to upload and download files. You can use multiple libraries or a more complete framework to provide the necessary functionality for these tasks. For example, you could use a library like “Authlib” to handle user authentication. This library provides a set of functions you can call in your code to handle tasks such as creating new user accounts, logging in and out, and verifying user credentials. Then get a different library for handling file transfers, or write your own.

On the other hand, you could use a framework like “Django” to handle both user authentication and file uploads/downloads. Django is a full-stack web framework with many out-of-the-box functionalities, including user authentication and file storage. When using Django, you would write your code within the structure provided by the framework, following its conventions and patterns.

Both libraries and frameworks can be valuable tools for building software applications, and the choice of which to use will depend on the specific needs of your project. However, both libraries and frameworks provide pre-written code that can save time and effort when building software, and they can be easily installed and used in a project.

### Differences
Differences
These are some key differences between libraries and frameworks which I will discuss further in the following sections.

Flexibility
Libraries are designed to be flexible and can be used in various ways. Developers can choose how to use a library and incorporate it into their code in any way that makes sense for their project. 

Consider the mathematical library.

In this example, the JavaScript Math library provides functions for performing various mathematical operations, such as calculating square roots, logarithms, and trigonometric functions. Developers can use these functions in any way they see fit. They can call any of the functions provided by the library and use the return values however they like. This demonstrates the flexibility of a library—it gives developers the tools, but they decide how and when to use them.

```
// Calculate the square root of a number
let x = 16;
let y = Math.sqrt(x);
console.log(y); 
// Output: 4

// Calculate the logarithm of a number with base 10
let z = Math.log10(100);
console.log(z); 
// Output: 2

// Calculate the sine of an angle in radians
let a = Math.sin(30 * Math.PI / 180); // Convert 30 degrees to radians
console.log(a); 
// Output: 0.49999999999999994
```
In contrast to libraries, frameworks tend to impose a specific structure or pattern that developers must follow. This means that developers must adhere to the system and conventions set by the framework when using it. Frameworks manage the flow of control and expect the developer to integrate their code into predefined structures.

Now consider a framework like Express.js in JavaScript. Express.js is a web application framework that provides functionality for handling routing, middleware, and server management. When using Express.js, developers must follow its conventions and structure. For example, they might write code like this:

```
const express = require('express');
const app = express();

app.get('/users/:id', function (req, res) {
  const userId = req.params.id;
  res.send(`User ID is: ${userId}`);
});

app.listen(3000, function () {
  console.log('Server is running on port 3000');
});
```
In this Express.js example, developers must follow the framework’s structure to define routes, handle requests, and start the server. While there is flexibility in how they write logic within those routes, the framework dictates the overall architecture and flow, unlike a library where developers have more freedom to use functions as needed.

This example illustrates the difference between a library and a framework. In a library (like the Math library), you call functions and control the flow. In a framework (like Express.js), the framework controls the flow, and you fill in the necessary parts.

## ✨Control Flow:
In a library, you are in control of when and how to use its functions.
In a framework, the control is inverted. The framework calls your code, meaning it dictates the flow, and you insert your logic where needed.
+ Reusability: Libraries offer reusable pieces of code for specific tasks. Frameworks provide reusable patterns and structures for building larger-scale applications.
+ Flexibility vs. Convention: Libraries provide flexibility—you can choose when and how to use them. Frameworks impose conventions that you must follow, helping you avoid "reinventing the wheel" by structuring your application in a standard way.

### ✨How do Libraries work in programming
Libraries consist of reusable code that you can import into your project to perform tasks like handling data structures, manipulating files, or making network requests.

Finding and installing libraries: Each programming language has a package manager that allows you to find, install, and update libraries.

JavaScript: npm is the package manager (e.g., npm install lodash).

### ✨How do Frameworks work in programming
Frameworks provide a structure for your project and often include built-in tools for handling routing, database queries, and security.

Understanding "Inversion of Control": In a framework, the control is reversed: rather than you calling functions from the framework, the framework calls your code. This structure dictates how you develop the application, but it can speed up development by providing ready-made components.


## Conclusion
An application can be quickly developed and deployed using a framework. By utilizing a framework, we may use resources to expedite the development and improve user experience. A library is used to increase an application’s functionality. We can use the functions from our library in a variety of applications.

Who controls the execution flow is the key technical distinction between a framework and a library. You decide when to call the library, if at all when using a library. However, while using a framework, you write code to fill in the framework’s gaps because the framework manages the execution flow. The code that’s written is called the framework.


### ⚛️ React
Visit official website: https://react.dev

### 🅰️ Angular
Visit offical website: https://angular.dev

### 🎩 Svelte
Visit official website: https://svelte.dev

### 🧮 Remix
Visit official website: https://remix.run
