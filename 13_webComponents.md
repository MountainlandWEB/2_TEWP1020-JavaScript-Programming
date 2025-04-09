# 13: Web Components

### [📄 Table of contents](#-table-of-contents)

  - [📰 Intro](#-intro)
  - [🛠️ Custom Elements](#️-custom-elements)
    - [In-Class Exercise #1](#in-class-exercise-1)
    - [In-Class Exercise #2](#in-class-exercise-2)
    - [In-Class Exercise #3](#in-class-exercise-3)
  - [🍪 HTML Templates](#-html-templates)
    - [In-Class Exercise #4](#in-class-exercise-4)
    - [In-Class Exercise #5](#in-class-exercise-5)
  - [🏗️ Modules \& ES6 Imports](#️-modules--es6-imports)
    - [In-Class Exercise #6](#in-class-exercise-6)
    - [In-Class Exercise #7](#in-class-exercise-7)
    
---

## 📰 Intro

<details open>
<summary>Why are Web Components important?</summary>

>Web Components are a set of web platform APIs that allow developers to create reusable and encapsulated custom HTML elements. This approach promotes code reuse, modularization, and maintainability.
>
>![alt text](https://images.pexels.com/photos/2138126/pexels-photo-2138126.jpeg)
>
>Imagine building a house using pre-fabricated parts. Instead of crafting each door, window, or tile from scratch, you can use ready-made components that fit perfectly and function reliably. This not only speeds up the construction process but also ensures consistency and quality.
>
>**Real World Example**: 
>- **Pre-fabricated House Parts**: Similar to how builders use pre-fabricated parts to construct houses efficiently, developers use Web Components to build complex web applications quickly and consistently.
>- **Gmail**: Google's Gmail uses Web Components to modularize its interface, enabling the development team to update or replace parts of the interface without affecting the whole application.
>> ![alt text](https://images.pexels.com/photos/193003/pexels-photo-193003.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500)

</details>

## 🛠️ Custom Elements

<details open>
<summary>Why use Custom Elements?</summary>

>Custom Elements allow developers to define new HTML tags, implementing custom behavior and style encapsulated within the element. This leads to improved code organization, easier maintenance, and better reusability across different projects.
>
>**Benefits**:
>- **Encapsulation**: Custom Elements can encapsulate their internal structure, styles, and behavior, preventing conflicts with other parts of the application.
>- **Reusability**: Once created, custom elements can be reused across different applications or within the same application, reducing redundancy.
>- **Maintainability**: Encapsulated components are easier to maintain and update, as changes in one component do not affect others.

</details>

<details open>
<summary>Creating Custom Elements (give 3 examples, one more complex than the last)</summary>

>**Example 1: Simple Button Component**
>```javascript
>class SimpleButton extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.shadowRoot.innerHTML = `
>            <button><slot></slot></button>
>            <style>
>                button {
>                    background-color: #6200ea;
>                    color: white;
>                    border: none;
>                    padding: 10px;
>                    border-radius: 5px;
>                }
>            </style>
>        `;
>    }
>}
>customElements.define('simple-button', SimpleButton);
>```
>
>**Example 2: Toggled Content Component**
>```javascript
>class ToggledContent extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.shadowRoot.innerHTML = `
>            <div>
>                <button>Toggle Content</button>
>                <div class="content"><slot></slot></div>
>            </div>
>            <style>
>                .content {
>                    display: none;
>                }
>                .content.show {
>                    display: block;
>                }
>            </style>
>        `;
>        this.button = this.shadowRoot.querySelector('button');
>        this.content = this.shadowRoot.querySelector('.content');
>        this.button.addEventListener('click', () => {
>            this.content.classList.toggle('show');
>        });
>    }
>}
>customElements.define('toggled-content', ToggledContent);
>```
>
>**Example 3: Custom Modal Dialog**
>```javascript
>class CustomModal extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.shadowRoot.innerHTML = `
>            <div class="modal">
>                <div class="modal-content">
>                    <span class="close">&times;</span>
>                    <slot></slot>
>                </div>
>            </div>
>            <style>
>                .modal {
>                    display: none;
>                    position: fixed;
>                    z-index: 1;
>                    left: 0;
>                    top: 0;
>                    width: 100%;
>                    height: 100%;
>                    overflow: auto;
>                    background-color: rgb(0,0,0);
>                    background-color: rgba(0,0,0,0.4);
>                }
>                .modal-content {
>                    background-color: #fefefe;
>                    margin: 15% auto;
>                    padding: 20px;
>                    border: 1px solid #888;
>                    width: 80%;
>                }
>                .close {
>                    color: #aaa;
>                    float: right;
>                    font-size: 28px;
>                    font-weight: bold;
>                }
>                .close:hover,
>                .close:focus {
>                    color: black;
>                    text-decoration: none;
>                    cursor: pointer;
>                }
>            </style>
>        `;
>        this.modal = this.shadowRoot.querySelector('.modal');
>        this.closeButton = this.shadowRoot.querySelector('.close');
>        this.closeButton.addEventListener('click', () => this.hide());
>    }
>
>    show() {
>        this.modal.style.display = 'block';
>    }
>
>    hide() {
>        this.modal.style.display = 'none';
>    }
>}
>customElements.define('custom-modal', CustomModal);
>```

</details>

### In-Class Exercise #1
<details open>
<summary>Exercise: Custom Elements (Easy)</summary>

>Create a custom element called `my-paragraph` that displays a styled paragraph of text.
>
><details>
><summary>Answer</summary>
>
>```javascript
>class MyParagraph extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.shadowRoot.innerHTML = `
>            <p><slot></slot></p>
>            <style>
>                p {
>                    font-size: 18px;
>                    color: #333;
>                }
>            </style>
>        `;
>    }
>}
>customElements.define('my-paragraph', MyParagraph);
>```
>
></details>

</details>

### In-Class Exercise #2

<details open>
<summary>Exercise: Custom Elements (Medium)</summary>

>Create a custom element called `counter-button` that displays a button and a count that increments each time the button is clicked.
>
><details>
><summary>Answer</summary>
>
>```javascript
>class CounterButton extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.count = 0;
>        this.shadowRoot.innerHTML = `
>            <button>Click me: <span>${this.count}</span></button>
>            <style>
>                button {
>                    padding: 10px;
>                    font-size: 16px;
>                }
>            </style>
>        `;
>        this.button = this.shadowRoot.querySelector('button');
>        this.span = this.shadowRoot.querySelector('span');
>        this.button.addEventListener('click', () => this.increment());
>    }
>
>    increment() {
>        this.count++;
>        this.span.textContent = this.count;
>    }
>}
>customElements.define('counter-button', CounterButton);
>```
>
></details>

</details>

### In-Class Exercise #3
<details open>
<summary>Exercise: Custom Elements (Hard)</summary>

>Create a custom element called `color-picker` that allows the user to pick a color and displays the selected color.
>
><details>
><summary>Answer</summary>
>
>```javascript
>class ColorPicker extends HTMLElement {
>    constructor() {
>        super();
>        this.attachShadow({ mode: 'open' });
>        this.shadowRoot.innerHTML = `
>            <input type="color" />
>            <div class="color-display"></div>
>            <style>
>                .color-display {
>                    width: 100px;
>                    height: 100px;
>                    border: 1px solid #000;
>                    margin-top: 10px;
>                }
>            </style>
>        `;
>        this.input = this.shadowRoot.querySelector('input');
>        this.display = this.shadowRoot.querySelector('.color-display');
>        this.input.addEventListener('input', () => this.updateColor());
>    }
>
>    updateColor() {
>        const color = this.input.value;
>        this.display.style.backgroundColor = color;
>    }
>}
>customElements.define('color-picker', ColorPicker);
>```
>
></details>

</details>


## 🍪 HTML Templates

<details open>
<summary>Why use HTML Templates?</summary>

>HTML templates provide a way to define reusable chunks of HTML that are not rendered immediately when the page loads. This can help in creating more modular and maintainable code.
>
>**Parable**: Think of HTML templates like cookie cutters. Instead of baking individual cookies one by one, you can use a cookie cutter to create multiple cookies from a single template, ensuring consistency and saving time.
>
>![alt text](https://images.pexels.com/photos/13512284/pexels-photo-13512284.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1)
>
>**Benefits**:
>- **Reusability**: Templates can be reused throughout the application, reducing redundancy.
>- **Separation of Concerns**: Templates help separate the structure of the content from the logic that controls its behavior.
>- **Efficiency**: They allow for dynamic content creation without the need for duplicating HTML code.

</details>

<details open>
<summary>Create HTML Template</summary>

>**Example 1: Simple List Template**
>```html
><template id="simple-list-template">
>    <ul>
>        <li>Item 1</li>
>        <li>Item 2</li>
>        <li>Item 3</li>
>    </ul>
></template>
>
><script>
>    const template = document.getElementById('simple-list-template');
>    const clone = document.importNode(template.content, true);
>    document.body.appendChild(clone);
></script>
>```
>
>**Example 2: Complex Card Template**
>```html
><template id="card-template">
>    <div class="card">
>        <img src="" alt="Avatar" class="card-image">
>        <div class="container">
>            <h4><b></b></h4>
>            <p></p>
>        </div>
>    </div>
></template>
>
><script>
>    const template = document.getElementById('card-template');
>    const clone = document.importNode(template.content, true);
>    clone.querySelector('.card-image').src = 'avatar.png';
>    clone.querySelector('h4 b').textContent = 'John Doe';
>    clone.querySelector('p').textContent = 'Web Developer';
>    document.body.appendChild(clone);
></script>
>```

</details>

### In-Class Exercise #4
<details open>
<summary>Exercise HTML Template (Easy)</summary>

>Create an HTML template for a simple button with text "Click Me" and append it to the body.
>
><details>
><summary>Answer</summary>
>
>```html
><template id="button-template">
>    <button>Click Me</button>
></template>
>
><script>
>    const template = document.getElementById('button-template');
>    const clone = document.importNode(template.content, true);
>    document.body.appendChild(clone);
></script>
>```
>
></details>

</details>

### In-Class Exercise #5
<details open>
<summary>Exercise HTML Template (Hard)</summary>

>Create an HTML template for a profile card with placeholders for an image, name, and description. Use JavaScript to fill in these details and append the card to the body.
>
><details>
><summary>Answer</summary>
>
>```html
><template id="profile-card-template">
>    <div class="profile-card">
>        <img src="" alt="Profile Picture" class="profile-image">
>        <div class="profile-info">
>            <h2 class="profile-name"></h2>
>            <p class="profile-description"></p>
>        </div>
>    </div>
></template>
>
><script>
>    const template = document.getElementById('profile-card-template');
>    const clone = document.importNode(template.content, true);
>    clone.querySelector('.profile-image').src = 'profile.png';
>    clone.querySelector('.profile-name').textContent = 'Jane Doe';
>    clone.querySelector('.profile-description').textContent = 'Software Engineer';
>    document.body.appendChild(clone);
></script>
>```
>
></details>

</details>

## 🏗️ Modules & ES6 Imports

<details open>
<summary>Why use Modules? ES6 Imports?</summary>

>Modules and ES6 imports allow developers to break down their code into smaller, reusable pieces. This helps in managing dependencies and maintaining a clean and organized codebase.
>
>>**Parable**: Imagine building a house. Instead of constructing the entire house at once, you break the project into smaller tasks: building the foundation, framing the walls, installing the roof, and so on. Each task is handled separately by specialized teams, making the process more efficient and manageable. 
>>
>>Similarly, in software development, modules allow you to break down your code into smaller, specialized pieces, making it easier to build, maintain, and scale.
>>
>>![alt text](https://images.pexels.com/photos/534220/pexels-photo-534220.jpeg?cs=srgb&dl=pexels-pixabay-534220.jpg&fm=jpg)
>
>
>**Benefits**:
>- **Modularity**: Code can be separated into distinct modules, each handling a specific functionality.
>- **Reusability**: Modules can be reused across different parts of an application or in different projects.
>- **Maintainability**: Smaller, self-contained modules are easier to maintain and debug.
>- **Namespace Management**: Modules help prevent global namespace pollution by encapsulating code within their scope.

</details>

<details open>
<summary>Real-Life code examples of JavaScript Modules and ES6 Imports</summary>

>**Example 1: Basic Module Export and Import**
>```javascript
>// math.js
>export function add(a, b) {
>    return a + b;
>}
>
>// main.js
>import { add } from './math.js';
>console.log(add(2, 3)); // Output: 5
>```
>
>**Example 2: Exporting and Importing Multiple Functions**
>```javascript
>// utils.js
>export function greet(name) {
>    return `Hello, ${name}!`;
>}
>
>export function farewell(name) {
>    return `Goodbye, ${name}!`;
>}
>
>// main.js
>import { greet, farewell } from './utils.js';
>console.log(greet('Alice')); // Output: Hello, Alice!
>console.log(farewell('Bob')); // Output: Goodbye, Bob!
>```
>
>**Example 3: Default Export and Import**
>```javascript
>// logger.js
>export default function log(message) {
>    console.log(message);
>}
>
>// main.js
>import log from './logger.js';
>log('This is a default export example.'); // Output: This is a default export example.
>```

</details>

### In-Class Exercise #6
<details open>
<summary>Exercise: Modules</summary>

>Create a module that exports a function to calculate the area of a rectangle and import this function into another file to use it.
>
><details>
><summary>Answer</summary>
>
>```javascript
>// area.js
>export function calculateArea(width, height) {
>    return width * height;
>}
>
>// main.js
>import { calculateArea } from './area.js';
>console.log(calculateArea(5, 10)); // Output: 50
>```
>
></details>

</details>

### In-Class Exercise #7
<details open>
<summary>Exercise: ES6 Imports</summary>

>Create a module that exports a default function to calculate the circumference of a circle and import this function into another file to use it.
>
><details>
><summary>Answer</summary>
>
>```javascript
>// circumference.js
>export default function calculateCircumference(radius) {
>    return 2 * Math.PI * radius;
>}
>
>// main.js
>import calculateCircumference from './circumference.js';
>console.log(calculateCircumference(7)); // Output: 43.982297150257104
>```
>
></details>

</details>
