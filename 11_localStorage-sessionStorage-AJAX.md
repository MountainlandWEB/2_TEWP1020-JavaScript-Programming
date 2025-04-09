# 11: Local Storage, Session Storage, and AJAX

### 📄 Table of Contents

- [💾 Storage](#-storage)
  - [In-Class Exercise #1](#in-class-exercise-1)
  - [In-Class Exercise #2](#in-class-exercise-2)
  - [In-Class Exercise #3](#in-class-exercise-3)
- [🔄 AJAX](#-ajax)
- [📄 JSON](#-json)
  - [In-Class Exercise #4](#in-class-exercise-4)
  - [In-Class Exercise #5](#in-class-exercise-5)
  - [In-Class Exercise #6](#in-class-exercise-6)
---

>In both a warehouse and data storage in the browser, items are stored for later retrieval. Just as a warehouse holds physical goods until they are needed, the browser stores various types of data, including cookies, local storage, session storage, and IndexedDB, to be accessed by web applications when necessary.

>Understanding data storage in the browser is crucial for web developers because it enables them to create more efficient and dynamic web applications. By learning about the different storage mechanisms and their capabilities, developers 


![alt text](https://www.empirecommercialstaffing.com/wp-content/uploads/2020/12/Picture1-3-1024x682.jpg)

## 💾 Storage 

<details open>
<summary>What are Cookies?</summary>

>Cookies are small pieces of data stored on the user's device by the web browser while browsing a website. They are used to remember information about the user, such as login status, preferences, and tracking information.
>
>![alt text](https://media.istockphoto.com/id/1201896353/photo/cookie-on-the-keyboard.jpg?s=612x612&w=0&k=20&c=zAhcSlVfWuhVrUHi2eteq0V0BzY0aopGOOIWfyNvXqc=)
>
>Example:
>```javascript
>document.cookie = "username=John Doe; expires=Fri, 31 Dec 2021 23:59:59 GMT; path=/";
>```
>
>
>
</details>

<details open>
<summary>Why are Cookies important?</summary>

>Cookies are important because they allow websites to maintain stateful information over the stateless HTTP protocol. They are used for:
>- Session management (e.g., logins, shopping carts)
>- Personalization (e.g., user preferences, themes)
>- Tracking (e.g., analytics, advertising)
>
>Example:
>```javascript
>document.cookie = "theme=dark; expires=Fri, 31 Dec 2021 23:59:59 GMT; path=/";
>console.log(document.cookie); // "username=John Doe; theme=dark"
>```
>
>
>
</details>

<details open>
<summary>localStorage vs. sessionStorage</summary>

>Both `localStorage` and `sessionStorage` are part of the Web Storage API, providing a way to store key-value pairs in the browser. They are similar but have key differences:
>
>- `localStorage`: Data persists even after the browser is closed and reopened.
>- `sessionStorage`: Data persists only for the duration of the page session (until the browser or tab is closed).
>
>Example:
>```javascript
>// localStorage
>localStorage.setItem('key', 'value');
>console.log(localStorage.getItem('key')); // 'value'
>localStorage.removeItem('key');
>
>// sessionStorage
>sessionStorage.setItem('key', 'value');
>console.log(sessionStorage.getItem('key')); // 'value'
>sessionStorage.removeItem('key');
>```
>
>
>
</details>

<details open>
<summary>indexedDB. pros and cons compared to the other two.</summary>

>IndexedDB is a low-level API for client-side storage of large amounts of structured data, including files/blobs. It is more powerful than `localStorage` and `sessionStorage`, allowing for complex queries and transactions.
>
>Pros:
>- Supports storing large amounts of data
>- Supports transactions for reliability
>- Can store complex data types (objects, files)
>
>Cons:
>- More complex API than `localStorage` and `sessionStorage`
>- Asynchronous operations require handling with Promises or async/await
>
>Example:
>```javascript
>const request = indexedDB.open('myDatabase', 1);
>
>request.onupgradeneeded = function(event) {
>    const db = event.target.result;
>    const objectStore = db.createObjectStore('myObjectStore', { keyPath: 'id' });
>    objectStore.transaction.oncomplete = function() {
>        const store = db.transaction('myObjectStore', 'readwrite').objectStore('myObjectStore');
>        store.add({ id: 1, name: 'John Doe' });
>    };
>};
>
>request.onsuccess = function(event) {
>    const db = event.target.result;
>    const transaction = db.transaction('myObjectStore');
>    const objectStore = transaction.objectStore('myObjectStore');
>    const getRequest = objectStore.get(1);
>    
>    getRequest.onsuccess = function() {
>        console.log(getRequest.result); // { id: 1, name: 'John Doe' }
>    };
>};
>```
>
>
>
</details>



### In-Class Exercise #1

<details open>
<summary>Exercise: (easy)</summary>

>Create a function that sets a cookie with a given name and value. Then, create another function that retrieves the value of a cookie by its name.
>
><details>
><summary>Answer</summary>
>
>```javascript
>function setCookie(name, value, days) {
>    let expires = "";
>    if (days) {
>        const date = new Date();
>        date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
>        expires = "; expires=" + date.toUTCString();
>    }
>    document.cookie = name + "=" + (value || "") + expires + "; path=/";
>}
>
>function getCookie(name) {
>    const nameEQ = name + "=";
>    const ca = document.cookie.split(';');
>    for(let i = 0; i < ca.length; i++) {
>        let c = ca[i];
>        while (c.charAt(0) === ' ') c = c.substring(1, c.length);
>        if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length, c.length);
>    }
>    return null;
>}
>
>setCookie('username', 'John Doe', 7);
>console.log(getCookie('username')); // 'John Doe'
>```
>
></details>
>
>
>
</details>

### In-Class Exercise #2

<details open>
<summary>Exercise: (medium)</summary>

>Create a function that uses `localStorage` to store a user's theme preference (e.g., 'dark' or 'light'). Create another function to retrieve the stored theme and apply it to the document's body.
>
><details>
><summary>Answer</summary>
>
>```javascript
>function setTheme(theme) {
>    localStorage.setItem('theme', theme);
>    document.body.className = theme;
>}
>
>function applyTheme() {
>    const theme = localStorage.getItem('theme');
>    if (theme) {
>        document.body.className = theme;
>    }
>}
>
>setTheme('dark'); // Set theme to dark
>applyTheme(); // Apply the stored theme
>```
>
></details>
>
>
>
</details>

### In-Class Exercise #3

<details open>
<summary>Exercise: (hard)</summary>

>Create a function that uses `indexedDB` to store user settings (e.g., username, theme). Create another function to retrieve and log the stored settings.
>
><details>
><summary>Answer</summary>
>
>```javascript
>function openDatabase() {
>    return new Promise((resolve, reject) => {
>        const request = indexedDB.open('userSettingsDB', 1);
>
>        request.onupgradeneeded = (event) => {
>            const db = event.target.result;
>            db.createObjectStore('settings', { keyPath: 'id' });
>        };
>
>        request.onsuccess = (event) => {
>            resolve(event.target.result);
>        };
>
>        request.onerror = (event) => {
>            reject(event.target.error);
>        };
>    });
>}
>
>function saveSettings(settings) {
>    return openDatabase().then((db) => {
>        return new Promise((resolve, reject) => {
>            const transaction = db.transaction('settings', 'readwrite');
>            const store = transaction.objectStore('settings');
>            store.put(settings);
>
>            transaction.oncomplete = () => {
>                resolve();
>            };
>
>            transaction.onerror = (event) => {
>                reject(event.target.error);
>            };
>        });
>    });
>}
>
>function getSettings(id) {
>    return openDatabase().then((db) => {
>        return new Promise((resolve, reject) => {
>            const transaction = db.transaction('settings', 'readonly');
>            const store = transaction.objectStore('settings');
>            const request = store.get(id);
>
>            request.onsuccess = (event) => {
>                resolve(event.target.result);
>            };
>
>            request.onerror = (event) => {
>                reject(event.target.error);
>            };
>        });
>    });
>}
>
>const userSettings = { id: 1, username: 'JohnDoe', theme: 'dark' };
>saveSettings(userSettings).then(() => {
>    getSettings(1).then((settings) => {
>        console.log(settings);
>    });
>});
>```
>
></details>
>
>
>
</details>

## 🔄 AJAX

<details open>
<summary>What is AJAX? Why is it important?</summary>

>AJAX (Asynchronous JavaScript and XML) is a technique used to create asynchronous web applications. With AJAX, web pages can be updated asynchronously by exchanging small amounts of data with the server behind the scenes. This means that it is possible to update parts of a web page, without reloading the whole page.
>
>Importance of AJAX:
>- **Improved User Experience**: AJAX allows for smoother and more responsive user interfaces.
>- **Efficient Data Loading**: Only the necessary data is fetched, reducing the amount of data transferred.
>- **Asynchronous Operations**: AJAX operations do not block the user interface, allowing users to interact with the web page while data is being fetched.
>
>Example:
>```javascript
>const xhr = new XMLHttpRequest();
>xhr.open('GET', 'https://jsonplaceholder.typicode.com/posts/1', true);
>xhr.onload = function () {
>    if (xhr.status === 200) {
>        console.log(JSON.parse(xhr.responseText));
>    }
>};
>xhr.send();
>```
>
>
>
</details>

<details open>
<summary>XMLHttpRequest: older way of doing asynchronous requests.</summary>

>XMLHttpRequest (XHR) is a JavaScript API that allows the browser to make HTTP requests to servers asynchronously. It is the older way of making asynchronous requests before the Fetch API was introduced.
>
>Example:
>```javascript
>const xhr = new XMLHttpRequest();
>xhr.open('GET', 'https://jsonplaceholder.typicode.com/posts/1', true);
>xhr.onreadystatechange = function () {
>    if (xhr.readyState === 4 && xhr.status === 200) {
>        console.log(JSON.parse(xhr.responseText));
>    }
>};
>xhr.send();
>```
>
>Steps to use XMLHttpRequest:
>1. Create a new `XMLHttpRequest` object.
>2. Configure it: `open(method, URL, async)`.
>3. Set up a function to handle the response data.
>4. Send the request using `send()`.
>
>
>
</details>

<details open>
<summary>Fetch API: modern way</summary>

>The Fetch API is a modern replacement for XMLHttpRequest. It provides a more powerful and flexible feature set for making HTTP requests. Fetch is based on Promises, making it simpler to use and read.
>
>Example:
>```javascript
>fetch('https://jsonplaceholder.typicode.com/posts/1')
>    .then(response => {
>        if (!response.ok) {
>            throw new Error('Network response was not ok ' + response.statusText);
>        }
>        return response.json();
>    })
>    .then(data => console.log(data))
>    .catch(error => console.error('There was a problem with the fetch operation:', error));
>```
>
>Advantages of Fetch API:
>- **Promise-Based**: Cleaner and easier to read than the callback-based XMLHttpRequest.
>- **Streamlined Syntax**: Shorter and more concise code.
>- **More Features**: Supports features like streaming and more complex request and response handling.
>
>
>
</details>


## 📄 JSON

<details open>
<summary>What is JSON? Why is it important?</summary>

>JSON (JavaScript Object Notation) is a lightweight data-interchange format that is easy for humans to read and write and easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language and is used primarily to transmit data between a server and a web application.
>
>JSON is important because it is language-independent and can be used with many different programming languages. It is widely used in web development for APIs and configuration files due to its simplicity and readability.
>
>Here is an example of a JSON object:
>
>```json
>{
>    "name": "John",
>    "age": 30,
>    "city": "New York"
>}
>```
>
>JSON has become the standard for data exchange on the web, replacing XML in many cases due to its more straightforward syntax.
>
></details>

<details open>
<summary>What is XML? Why does it matter?</summary>

>XML (eXtensible Markup Language) is a markup language like. It is used to describe and transport data, allowing for the definition of custom tags and structures.
>
>XML matters because it was widely used for data interchange and storage before JSON became popular. It is still used in various applications, particularly where document markup and data validation are important.
>
>Here is an example of an XML document:
>
>```xml
><person>
>    <name>John</name>
>    <age>30</age>
>    <city>New York</city>
></person>
>```
>
>XML is more verbose than JSON, which can make it harder to read and write. However, it has strong support for namespaces, schema validation, and other features that make it suitable for complex data structures.
>
></details>

<details open>
<summary>Handling API Responses, Parse JSON</summary>

>When working with APIs, it is common to receive responses in JSON format. Parsing JSON allows you to convert the JSON string into a JavaScript object that can be easily manipulated.
>
>Here is an example of how to fetch data from an API and parse the JSON response:
>
>```javascript
>fetch('https://jsonplaceholder.typicode.com/posts/1')
>    .then(response => response.json())
>    .then(data => {
>        console.log(data);
>    })
>    .catch(error => {
>        console.error('Error:', error);
>    });
>```
>
>This example uses the Fetch API to make an HTTP request to an API endpoint. The `response.json()` method is called to parse the JSON string into a JavaScript object.
>
></details>

### In-Class Exercise #4

<details open>
<summary>Exercise: Parse JSON (easy)</summary>

>Create a function that fetches user data from an API and logs the user's name and email.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function fetchUserData() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await response.json();
>        console.log(`Name: ${user.name}, Email: ${user.email}`);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchUserData();
>// Output:
>// Name: Leanne Graham, Email: Sincere@april.biz
>```
>
></details>
</details>

### In-Class Exercise #5

<details open>
<summary>Exercise: Convert Object to JSON (medium)</summary>

>Write a function that converts a JavaScript object into a JSON string and logs it to the console.
>
><details>
><summary>Answer</summary>
>
>```javascript
>function convertObjectToJson(obj) {
>    const jsonString = JSON.stringify(obj);
>    console.log(jsonString);
>}
>
>const person = {
>    name: 'John',
>    age: 30,
>    city: 'New York'
>};
>
>convertObjectToJson(person);
>// Output:
>// {"name":"John","age":30,"city":"New York"}
>```
>
></details>
</details>

### In-Class Exercise #6

<details open>
<summary>Exercise: Parse JSON Array (hard)</summary>

>Write a function that fetches a list of posts from an API and logs the titles of all the posts.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function fetchPostTitles() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
>        const posts = await response.json();
>        posts.forEach(post => {
>            console.log(post.title);
>        });
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchPostTitles();
>// Output:
>// Title of post 1
>// Title of post 2
>// ...
>```
>
></details>
</details>
