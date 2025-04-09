# 08A: OOP Design Patterns

#### [Table of Contents](#table-of-contents)
  + Introduction
  + A-P-I-E
  + History of Patterns
  + Importance of Learning Patterns
  + Learning Patterns Criticisms
  + Types of Patterns

## Introduction
<div style="text-align:center">
<img src="https://static.wixstatic.com/media/353803_56f4babad5cc4a0faae91bb5e72808eb~mv2.jpg" width="300" />
</div>

<details open>
<summary>What is Design Patterns?</summary>
  
> Design patterns are typical solutions to commonly occurring problems in software design. They are like pre-made blueprints that you can customize to solve a recurring design problem in your code.

> You can’t just find a pattern and copy it into your program, the way you can with off-the-shelf functions or libraries. The pattern is not a specific piece of code, but a general concept for solving a particular problem. You can follow the pattern details and implement a solution that suits the realities of your own program.

> Patterns are often confused with algorithms, because both concepts describe typical solutions to some known problems. While an algorithm always defines a clear set of actions that can achieve some goal, a pattern is a more high-level description of a solution. The code of the same pattern applied to two different programs may be different.

> An analogy to an algorithm is a cooking recipe: both have clear steps to achieve a goal. On the other hand, a pattern is more like a blueprint: you can see what the result and its features are, but the exact order of implementation is up to you.

> Design patterns provide reusable, tested solutions to common software design challenges. Rather than offering rigid, cookie-cutter approaches, they are flexible templates that can be adapted to the specific problem developers face. These patterns are essential for building scalable, maintainable systems, especially when working within object-oriented paradigms.

> Before we dive into design patterns, let's revisit the four pillars of object-oriented programming (OOP): abstraction, polymorphism, inheritance, and encapsulation (often remembered by the acronym A-P-I-E). These principles form the foundation on which many design patterns are built.

> ### Abstraction:
> This concept focuses on simplifying complex realities by modeling entities in terms of their essential characteristics while hiding unnecessary details. For example, a car can be abstracted to its essential components—engine, wheels, and steering—without needing to detail every inner mechanism. Abstraction helps manage complexity and promotes cleaner, more understandable designs.

> ### Polymorphism:
> The ability of objects to take on many forms. For example, a parent class Shape can have different forms such as Circle or Rectangle, each implementing the same interface but behaving differently. Polymorphism underpins flexibility in OOP, enabling objects to respond to the same method call in different ways, which supports several design patterns.

> ### Inheritance:
> A way for one class to acquire the properties and behaviors of another. For instance, a Bird class might inherit from a Animal class, inheriting common attributes like eat() or sleep() while introducing new methods such as fly(). Inheritance promotes code reusability and helps eliminate redundancy.

> ### Encapsulation:
> This principle involves bundling data (attributes) and methods (behaviors) into a single unit (class) and restricting direct access to some of the object's components. For example, a BankAccount class might expose methods for depositing and withdrawing funds while keeping the balance variable private. Encapsulation protects the integrity of the object's data and ensures controlled interactions. 

</details>

## A-P-I-E

<details open>
<summary>The case for design patterns</summary>
  
> A-P-I-E is foundational, but the software engineering realm often requires more nuanced solutions. This is where design patterns come into play. They complement A-P-I-E, bridging the gap between basic OOP concepts and complex challenges. Built upon the SOLID design principles, design patterns are like evolved strategies that are tried, tested, and shared by the developer community. Instead of a lengthy walkthrough, just naming a known design pattern can bring everyone on the same page. It streamlines collaboration and boosts efficiency.

> Think of it this way: while constructing a building, understanding the basics like bricks, cement, and steel (A-P-I-E in our context) is crucial. But, it's the architectural blueprints and patterns that ensure the building stands tall, is functional, aesthetic, and safe. Similarly, while A-P-I-E sets the groundwork, design patterns are those architectural blueprints for software, ensuring it’s resilient, scalable, and maintainable.

> One might wonder, why not just reinvent solutions when faced with new challenges? Well, consistently trying to reinvent the wheel for recurrent software challenges can be a resource drain. Instead of investing time in crafting a new solution from scratch, leveraging a design pattern that's already been through the rigors of multiple real-world tests can save both time and effort. Plus, it brings with it the wisdom of countless developers who have refined and endorsed it.

</details>

## History of Patterns

<details open>
<summary>History of Patterns</summary>
  
> Patterns are typical solutions to common problems in object-oriented design. When a solution gets repeated over and over in various projects, someone eventually puts a name to it and describes the solution in detail. That’s basically how a pattern gets discovered.

> A Pattern Language: Towns, Buildings, Construction written by Christopher Alexander and his colleagues is a work in architecture and urban design published in 1977. The book presents a comprehensive system of design principles, or "patterns," that can be applied to create functional, beautiful, and human-centered environments. These patterns range from broad concepts like the design of towns and neighborhoods to detailed aspects of individual buildings and spaces.

> The book focus is on creating environments that enhance the quality of life. It provides a "language" of interconnected patterns that guide the design of spaces at every scale, from cities and towns to individual rooms and gardens. Each pattern addresses a specific design problem and offers a solution based on years of observation and research. The idea is that by combining these patterns, designers and architects can create environments that are both aesthetically pleasing and responsive to human needs.

> The ideas was picked up by four authors: Erich Gamma, John Vlissides, Ralph Johnson, and Richard Helm then 1994, published "Design Pattersn: Elements of Reusable Object-Oriented Software, in which they applied the concept of design patters to programming. This book features 23 patterns solving various problems of object-oriented design. Since then other object-oriented patterns have been discovered.

</details>

## Importance of Learning Patterns

<details open>
<summary>Why learning patterns is important?</summary>
  
> The truth is you might already be implementing some patterns without even knowing it. Design patterns are a toolkit of tried and tested solutions to common problems in software design. Even if you never encounter these problems, knowing patterns is still useful because it teaches you how to solve all sorts of problems using principles of object-oriented design.

</details>

## Criticisms for Learning Patterns

<details open>
<summary>Learning Patterns Criticisms</summary>
  
> Overuse and Misapplication: Some critics argue that the emphasis on patterns can lead to overengineering. Developers might be tempted to apply patterns even when they are unnecessary or inappropriate, resulting in overly complex and rigid code.

> Copy-Paste Mentality: Patterns can sometimes encourage a "cookie-cutter" approach, where developers focus on reusing patterns without fully understanding the underlying problem or the specific context. This can lead to solutions that are not well-suited to the actual problem at hand.

> Lack of Innovation: Relying too heavily on established patterns might stifle creativity and innovation. By focusing on existing solutions, developers may overlook novel approaches that could be more effective in solving unique or new problems.

> Pattern Proliferation: The proliferation of patterns can lead to confusion, as there are often many patterns that solve similar problems in slightly different ways. This can make it difficult for developers to choose the most appropriate pattern for a given situation.

> Formalism and Complexity: Some critics believe that the formal structure of pattern descriptions can be too rigid or complex, making them difficult for developers to understand and apply effectively, particularly for those who are less experienced.

> Context-Dependency: Patterns are often context-dependent, meaning they work well in specific situations but may not be easily adaptable to others. This can limit their usefulness in more dynamic or evolving environments.

> Evolving Technologies: As technology evolves, some patterns may become outdated or less relevant, especially with the advent of new programming paradigms, tools, or frameworks that offer more modern solutions to common problems.

</details>

## Types of Patterns

<details open>
<summary>Types of patterns</summary>
  
> 1. Behavioral patterns: These patterns are concerned with algorithms and the assignment of responsibilities between objects.

> 2. Creational patterns: These patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.

> 3. Structural patterns: These patterns explain how to assemble objects and classes into larger structures while keeping these structures flexible and efficient.

</details>
