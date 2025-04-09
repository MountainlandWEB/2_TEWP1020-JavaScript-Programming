# 10: Async/Await and Regular Expressions

### [📄 Table of Contents](#-table-of-contents)

  - [🔄 Async](#-async)
    - [In-Class Exercise #1](#in-class-exercise-1)
    - [In-Class Exercise #2](#in-class-exercise-2)
  - [⏳ Await](#-await)
    - [In-Class Exercise #3](#in-class-exercise-3)
    - [In-Class Exercise #4](#in-class-exercise-4)
    - [In-Class Exercise #5](#in-class-exercise-5)
  - [⚠️ Error Handling](#️-error-handling)
    - [In-Class Exercise #6](#in-class-exercise-6)
    - [In-Class Exercise #7](#in-class-exercise-7)
  - [🔍 REGEX](#-regex)
    - [In-Class Exercise #8](#in-class-exercise-8)
    - [In-Class Exercise #9](#in-class-exercise-9)

---
## 🔄 Async

<details open>
<summary>Basics of async functions in javascript</summary>

>Async functions in JavaScript provide a cleaner way to work with asynchronous code using the `async` and `await` keywords. An async function always returns a Promise, and the `await` keyword is used to pause the execution of the function until the Promise is resolved.
>
>```javascript
>// Example of an async function
>async function fetchData() {
>    try {
>        let response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        let data = await response.json();
>        console.log(data);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchData();
>// Output:
>// { userId: 1, id: 1, title: "Sample Title", body: "Sample body text" }
>
>// Using async/await with a simple function
>function delay(ms) {
>    return new Promise(resolve => setTimeout(resolve, ms));
>}
>
>async function greet() {
>    console.log('Hello');
>    await delay(2000);
>    console.log('World');
>}
>
>greet();
>// Output:
>// Hello
>// (waits 2 seconds)
>// World
>```
>
>
>
</details>

<details open>
<summary>Why are async functions important in javascript. small parable</summary>

>Imagine a chef in a busy restaurant. If the chef had to personally prepare each ingredient, cook every dish, and serve every meal before starting the next, the kitchen would be very slow. 
>
>![alt text](https://images.pexels.com/photos/2544829/pexels-photo-2544829.jpeg?cs=srgb&dl=pexels-reneasmussen-2544829.jpg&fm=jpg)
>
>Instead, the chef delegates tasks like chopping vegetables or stirring a pot to assistants. This way, the chef can focus on cooking multiple dishes simultaneously, ensuring that meals are prepared efficiently.
>
>Similarly, async functions allow JavaScript to handle multiple operations efficiently. By using `async` and `await`, you can delegate time-consuming tasks (like fetching data from an API) without blocking the main thread. This results in a smoother, more responsive user experience.
>
>Async functions in JavaScript provide a cleaner way to work with asynchronous code using the `async` keyword. An async function always returns a Promise.
>
>```javascript
>// Example of an async function
>async function fetchData() {
>    return fetch('https://jsonplaceholder.typicode.com/posts/1')
>        .then(response => response.json())
>        .then(data => {
>            console.log(data);
>            return data;
>        })
>        .catch(error => {
>            console.error('Error:', error);
>        });
>}
>
>fetchData();
>// Output:
>// { userId: 1, id: 1, title: "Sample Title", body: "Sample body text" }
>
>// Using async with a simple function
>async function greet() {
>    console.log('Hello');
>    const delay = new Promise(resolve => setTimeout(resolve, 2000));
>    delay.then(() => console.log('World'));
>}
>
>greet();
>// Output:
>// Hello
>// (waits 2 seconds)
>// World
>```
>
>
>
</details>


### In-Class Exercise #1

<details open>
<summary>Exercise: async functions (easy)</summary>

>Create an async function that fetches user data from an API and logs the user's name. Use Promises and `then` to handle the asynchronous operation.
>
>```javascript
>async function fetchUserData() {
>    fetch('https://jsonplaceholder.typicode.com/users/1')
>        .then(response => response.json())
>        .then(user => {
>            console.log(`User Name: ${user.name}`);
>        })
>        .catch(error => {
>            console.error('Error:', error);
>        });
>}
>
>fetchUserData();
>// Output:
>// User Name: Leanne Graham (or the name of the user with id 1)
>```
>
>
>
</details>

### In-Class Exercise #2

<details open>
<summary>Exercise: async functions (hard)</summary>

>Create an async function that simulates a sequence of tasks: fetch user data, fetch user posts, and log the results. Ensure each task waits for the previous one to complete using Promises and `then`.
>
>```javascript
>async function fetchUserData() {
>    return fetch('https://jsonplaceholder.typicode.com/users/1')
>        .then(response => response.json());
>}
>
>async function fetchUserPosts() {
>    return fetch('https://jsonplaceholder.typicode.com/posts?userId=1')
>        .then(response => response.json());
>}
>
>async function fetchAndLogData() {
>    console.log('Fetching user data...');
>    fetchUserData().then(user => {
>        console.log(`User Name: ${user.name}`);
>        
>        console.log('Fetching user posts...');
>        fetchUserPosts().then(posts => {
>            console.log(`User has ${posts.length} posts.`);
>        }).catch(error => {
>            console.error('Error fetching posts:', error);
>        });
>    }).catch(error => {
>        console.error('Error fetching user:', error);
>    });
>}
>
>fetchAndLogData();
>// Output:
>// Fetching user data...
>// User Name: Leanne Graham (or the name of the user with id 1)
>// Fetching user posts...
>// User has 10 posts (or the number of posts the user has)
>```
>
>
>
</details>


---
## ⏳ Await 

<details open>
<summary>basics of adding "await" to async functions in javascript</summary>

>The `await` keyword can only be used inside an `async` function. It makes JavaScript wait until the Promise resolves and returns its result. This simplifies working with Promises by allowing you to write asynchronous code in a synchronous style.
>
>```javascript
>async function fetchData() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        const data = await response.json();
>        console.log(data);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchData();
>// Output:
>// { userId: 1, id: 1, title: "Sample Title", body: "Sample body text" }
>```
>
>
>
</details>

<details open>
<summary>Most common uses for async await in javascript</summary>

>Async/await is commonly used for:
>
>1. **Fetching Data from APIs**: Simplifies fetching data from REST APIs.
>    ```javascript
>    async function getUserData() {
>        const response = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await response.json();
>        console.log(user);
>    }
>
>    getUserData();
>    ```
>
>2. **Handling Multiple Promises**: Making multiple asynchronous requests sequentially or concurrently.
>    ```javascript
>    async function getUserAndPosts() {
>        const userResponse = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await userResponse.json();
>
>        const postsResponse = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${user.id}`);
>        const posts = await postsResponse.json();
>
>        console.log(user);
>        console.log(posts);
>    }
>
>    getUserAndPosts();
>    ```
>
>3. **Error Handling**: Using try/catch for handling errors in asynchronous code.
>    ```javascript
>    async function fetchData() {
>        try {
>            const response = await fetch('https://jsonplaceholder.typicode.com/invalid-url');
>            const data = await response.json();
>            console.log(data);
>        } catch (error) {
>            console.error('Error:', error);
>        }
>    }
>
>    fetchData();
>    ```
>
>
>
</details>

<details open>
<summary>Before Async/Await, this was the less effective way to do it in javascript</summary>

>Before `async/await`, handling asynchronous operations often involved chaining multiple `then` calls, leading to callback hell or less readable code.
>
>```javascript
>// Fetching user data and posts without async/await
>function getUserData() {
>    return fetch('https://jsonplaceholder.typicode.com/users/1')
>        .then(response => response.json());
>}
>
>function getUserPosts(userId) {
>    return fetch(`https://jsonplaceholder.typicode.com/posts?userId=${userId}`)
>        .then(response => response.json());
>}
>
>function fetchUserAndPosts() {
>    getUserData()
>        .then(user => {
>            console.log(user);
>            return getUserPosts(user.id);
>        })
>        .then(posts => {
>            console.log(posts);
>        })
>        .catch(error => {
>            console.error('Error:', error);
>        });
>}
>
>fetchUserAndPosts();
>// Output:
>// { userId: 1, id: 1, name: "Leanne Graham", ... }
>// [{ userId: 1, id: 1, title: "Sample Title", ... }, ...]
>```
>
>With `async/await`, the same code becomes more readable and easier to manage:
>
>```javascript
>async function fetchUserAndPosts() {
>    try {
>        const userResponse = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await userResponse.json();
>        console.log(user);
>
>        const postsResponse = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${user.id}`);
>        const posts = await postsResponse.json();
>        console.log(posts);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchUserAndPosts();
>// Output:
>// { userId: 1, id: 1, name: "Leanne Graham", ... }
>// [{ userId: 1, id: 1, title: "Sample Title", ... }, ...]
>```
>
>
>
</details>

### In-Class Exercise #3

<details open>
<summary>Exercise: async/await (easy)</summary>

>Create an async function named `fetchPostTitle` that fetches a single post from the JSONPlaceholder API and logs the post title.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function fetchPostTitle() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        const post = await response.json();
>        console.log(post.title);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchPostTitle();
>// Output:
>// (Title of the post)
>```
>
></details>
</details>


### In-Class Exercise #4

<details open>
<summary>Exercise: promises (medium)</summary>

>Modify the async functions we made in class to use promises instead of calling “callbacks”. Functions must return promises. Functions must set a timeout to simulate async behavior. Must render the resulting array after it has been modified.
>
><details>
><summary>Answer</summary>
>
>```javascript
>function fetchUser() {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            fetch('https://jsonplaceholder.typicode.com/users/1')
>                .then(response => response.json())
>                .then(user => resolve(user))
>                .catch(error => reject(error));
>        }, 1000);
>    });
>}
>
>function fetchAlbums(userId) {
>    return new Promise((resolve, reject) => {
>        setTimeout(() => {
>            fetch(`https://jsonplaceholder.typicode.com/albums?userId=${userId}`)
>                .then(response => response.json())
>                .then(albums => resolve(albums))
>                .catch(error => reject(error));
>        }, 1000);
>    });
>}
>
>fetchUser()
>    .then(user => {
>        console.log(user);
>        return fetchAlbums(user.id);
>    })
>    .then(albums => {
>        console.log(albums);
>    })
>    .catch(error => {
>        console.error('Error:', error);
>    });
>// Output:
>// (User details)
>// (Array of albums for the user)
>```
>
></details>
</details>

### In-Class Exercise #5

<details open>
<summary>Exercise: async/await (hard)</summary>

> Create an async function named `fetchUserAndAlbums` that fetches a user and their albums from the JSONPlaceholder API. Log both the user and their albums.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function fetchUserAndAlbums() {
>    try {
>        const userResponse = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        const user = await userResponse.json();
>        console.log(user);
>
>        const albumsResponse = await fetch(`https://jsonplaceholder.typicode.com/albums?userId=${user.id}`);
>        const albums = await albumsResponse.json();
>        console.log(albums);
>    } catch (error) {
>        console.error('Error:', error);
>    }
>}
>
>fetchUserAndAlbums();
>// Output:
>// (User details)
>// (Array of albums for the user)
>```
>
></details>
</details>

---
## ⚠️ Error Handling

<details open>
<summary>Basics of Error Handling in JavaScript</summary>

>Error handling in JavaScript is primarily done using `try`, `catch`, and `finally` blocks. The `try` block contains the code that may throw an error, the `catch` block contains the code that executes if an error occurs, and the `finally` block contains code that will run regardless of whether an error occurred or not.
>
>```javascript
>try {
>    // Code that may throw an error
>    let result = riskyFunction();
>    console.log(result);
>} catch (error) {
>    // Code that runs if an error occurs
>    console.error('An error occurred:', error.message);
>} finally {
>    // Code that runs regardless of an error
>    console.log('This will run no matter what.');
>}
>```
>
>
>
</details>

<details open>
<summary>Using Error Handling with async/await</summary>

>When using `async/await`, error handling is done using `try` and `catch` blocks. This allows you to handle errors in asynchronous code in a similar way to synchronous code.
>
>```javascript
>async function fetchData() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        if (!response.ok) {
>            throw new Error('Network response was not ok');
>        }
>        const data = await response.json();
>        console.log(data);
>    } catch (error) {
>        console.error('Fetch error:', error.message);
>    }
>}
>
>fetchData();
>```
>
>
>
</details>

### In-Class Exercise #6

<details open>
<summary>Exercise: Error Handling (easy)</summary>

>Create a function named `safeFetchPost` that fetches a single post from the JSONPlaceholder API and handles any errors that occur during the fetch operation.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function safeFetchPost() {
>    try {
>        const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
>        if (!response.ok) {
>            throw new Error('Network response was not ok');
>        }
>        const post = await response.json();
>        console.log(post);
>    } catch (error) {
>        console.error('Error fetching post:', error.message);
>    }
>}
>
>safeFetchPost();
>// Output:
>// (Post details or error message)
>```
>
></details>
</details>

### In-Class Exercise #7

<details open>
<summary>Exercise: Error Handling (hard)</summary>

>Create a function named `fetchUserAndAlbumsSafely` that fetches a user and their albums from the JSONPlaceholder API, handling any errors that occur during either fetch operation.
>
><details>
><summary>Answer</summary>
>
>```javascript
>async function fetchUserAndAlbumsSafely() {
>    try {
>        const userResponse = await fetch('https://jsonplaceholder.typicode.com/users/1');
>        if (!userResponse.ok) {
>            throw new Error('Network response was not ok for user');
>        }
>        const user = await userResponse.json();
>        console.log(user);
>
>        const albumsResponse = await fetch(`https://jsonplaceholder.typicode.com/albums?userId=${user.id}`);
>        if (!albumsResponse.ok) {
>            throw new Error('Network response was not ok for albums');
>        }
>        const albums = await albumsResponse.json();
>        console.log(albums);
>    } catch (error) {
>        console.error('Error fetching user or albums:', error.message);
>    }
>}
>
>fetchUserAndAlbumsSafely();
>// Output:
>// (User details, albums, or error message)
>```
>
></details>
</details>


--- 
## 🔍 REGEX

<details open>
<summary>What are Regular Expressions and why are they important?</summary>

>Regular Expressions (regex or regexp) are patterns used to match character combinations in strings. 
>
>They are important because they provide a powerful way to <strong>search, replace, and manipulate</strong> text. Regex is used in various programming languages, including JavaScript, to validate input, search and replace text, and perform complex string manipulations.
>
>Example:
>```javascript
>const regex = /hello/;
>const str = 'hello world';
>console.log(regex.test(str)); // true
>```
>
</details>

<details open>
<summary>What're Regex Patterns? Special characters?</summary>

>Regex patterns are sequences of characters that define a search pattern. Special characters in regex have specific meanings and allow for more complex and powerful string matching.
>
>Some common special characters:
>- `.`: Matches any single character except newline.
>- `*`: Matches 0 or more occurrences of the preceding element.
>- `+`: Matches 1 or more occurrences of the preceding element.
>- `?`: Matches 0 or 1 occurrence of the preceding element.
>- `^`: Matches the beginning of the string.
>- `$`: Matches the end of the string.
>- `\`: Escapes a special character.
>
>Example:
>```javascript
>const regex = /^h.llo$/;
>const str = 'hello';
>console.log(regex.test(str)); // true
>```
>
>
>
</details>

<details open>
<summary>Creating Regular Expression in JavaScript with 5 most common regex methods</summary>

>1. `test()`: Tests for a match in a string. Returns `true` or `false`.
>    ```javascript
>    const regex = /hello/;
>    const str = 'hello world';
>    console.log(regex.test(str)); // true
>    ```
>
>2. `exec()`: Tests for a match in a string. Returns the first match as an array or `null`.
>    ```javascript
>    const regex = /hello/;
>    const str = 'hello world';
>    console.log(regex.exec(str)); // ['hello']
>    ```
>
>3. `match()`: Searches a string for a match and returns an array of results or `null`.
>    ```javascript
>    const str = 'hello world';
>    console.log(str.match(/hello/)); // ['hello']
>    ```
>
>4. `search()`: Searches for a match and returns the index of the match or `-1`.
>    ```javascript
>    const str = 'hello world';
>    console.log(str.search(/hello/)); // 0
>    ```
>
>5. `replace()`: Searches for a match and replaces the matched substring with a new substring.
>    ```javascript
>    const str = 'hello world';
>    console.log(str.replace(/hello/, 'hi')); // 'hi world'
>    ```
>
>
>
</details>

### In-Class Exercise #8

<details open>
<summary>Exercise: Regex (easy)</summary>

>Create a regex pattern that matches an email address and test it against a sample email address.
>
><details>
><summary>Answer</summary>
>
>```javascript
>const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
>const email = 'test@example.com';
>console.log(emailRegex.test(email)); // true
>```
>
></details>
</details>

### In-Class Exercise #9

<details open>
<summary>Exercise: Regex (hard)</summary>

>Create a regex pattern that matches a URL and extract the domain name from a sample URL.
>
><details>
><summary>Answer</summary>
>
>```javascript
>const urlRegex = /^(https?:\/\/)?(www\.)?([a-zA-Z0-9.-]+)\.[a-zA-Z]{2,}(\/.*)?$/;
>const url = 'https://www.example.com/path';
>const match = url.match(urlRegex);
>if (match) {
>    const domain = match[3];
>    console.log(domain); // 'example.com'
>} else {
>    console.log('No match found');
>}
>```
>
></details>
</details>
