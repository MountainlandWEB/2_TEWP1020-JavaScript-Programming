# 03: Data Types
## 1 - STRING

<details open>
<summary>What is a string?</summary>

> A string is a piece of text… it is a "String" of characters
>
> Wrap the value with Double (") or Single Quotes ('). Or you can use backticks ( ` ) [these are called <i>template strings</i>]
>
> ```javascript
> let greeting = "Hello, world!";
> let name = 'John';
> let message = `Welcome, ${name}!`;
> ```
>

</details>

<details open>
<summary>Where do we most see strings in real life?</summary>

> In the modern era, strings are prevalent across various digital platforms, shaping our experiences in social media, movies, and games.
>
> **Social Media**: Strings are ubiquitous on social media platforms like Facebook, Twitter, and Instagram, where they form the foundation of posts, comments, messages, and user profiles. Whether it's sharing thoughts, uploading photos, or commenting on friends' posts, strings enable communication and interaction among users in the digital space.
>
> **Movies**: In the film industry, strings are essential for scriptwriting, dialogue delivery, and subtitles. They contribute to storytelling, character development, and narrative immersion. Moreover, strings play a crucial role in movie marketing, from catchy taglines to promotional campaigns, influencing audience engagement and perception.
>
> **Games**: Strings are integral to video games, driving in-game dialogue, instructions, character names, and narrative elements. From immersive role-playing games to casual mobile apps, strings enhance gameplay, guide players through challenges, and enrich storytelling. Additionally, strings are central to user interfaces, menus, and in-game communication features, fostering player engagement and community interaction.
>
> In essence, strings permeate modern digital experiences, enriching social interactions, entertainment, and storytelling across social media, movies, and games.
>

</details>


![alt text](https://upload.wikimedia.org/wikipedia/commons/6/6b/String_example.png)

<details open>
<summary>Concatenate Strings</summary>

> In JavaScript, concatenating strings means joining multiple strings together to create a single string.
>
> You can concatenate strings using the `+` operator, or by using template literals (enclosed in backticks) with placeholders for variables.
>
> Here are three common examples of string concatenation:
>
> ```javascript
> // Using the + operator
> let greeting = "Hello, ";
> let name = 'John';
> let message = greeting + name + "!"; // Result: "Hello, John!"
> ```
>
> ```javascript
> // Using template literals
> let city = "New York";
> let country = "USA";
> let location = `I live in ${city}, ${country}.`; // Result: "I live in New York, USA."
> ```
>
> ```javascript
> // Concatenating multiple strings
> let sentencePart1 = "JavaScript is ";
> let sentencePart2 = "awesome!";
> let sentence = sentencePart1 + sentencePart2; // Result: "JavaScript is awesome!"
> ```
>

</details>

### String Methods

<i>Let's quickly go over the importance of the words "method" and "function".</i>

<details open>
<summary>What is a method? Difference between a method and a function</summary>

> Imagine you have a smartphone. Your smartphone can do many things like making calls, sending texts, and taking photos. Now, think of each of these actions your smartphone can perform as a method. So, a method is like a built-in action that an object (like your smartphone) can perform.
>
>![alt text](https://prerender.io/wp-content/uploads/2022/12/Screen-Shot-2022-12-01-at-14.55.26-1024x537.jpg)
>
> Now, let's talk about the difference between a method and a function. A **function** is a block of code that performs a specific task. It can be standalone or attached to an object. 
> 
> <i>When a function is attached to an object</i>, it's called a **method**. So, in simpler terms, a method is just a function that belongs to an object.
>
> Here's an example in JavaScript:
>
> ```javascript
> // Function example
> function add(a, b) {
>   return a + b;
> }
>
> let result = add(3, 5); // Result: 8
>
> // Method example
> let person = {
>   name: 'Alice',
>   greet: function() {
>     return `Hello, ${this.name}!`;
>   }
> };
>
> let greeting = person.greet(); // Result: "Hello, Alice!"
> ```
>
> In the example above, `add` is a function that adds two numbers, while `greet` is a method attached to the `person` object, which returns a personalized greeting.
>

</details>

<details open>
<summary>Top 10 most used string methods</summary>

> <details>
> <summary>"charAt()"</summary>
> > Returns the character at a specified index in a string.
> 
> > ```javascript
> > let str = "hello";
> > let char = str.charAt(0); // Returns: "h"
> > ```
>
> </details>
>
> <details>
> <summary>"charCodeAt()"</summary>
> > Returns the Unicode of the character at a specified index in a string.
> 
> > ```javascript
> > let str = "hello";
> > let unicode = str.charCodeAt(0); // Returns: 104
> > ```
>
> </details>
>
> <details>
> <summary>"concat()"</summary>
> > Joins two or more strings and returns a new string.
> 
> > ```javascript
> > let str1 = "Hello, ";
> > let str2 = "world!";
> > let greeting = str1.concat(str2); // Returns: "Hello, world!"
> > ```
>
> </details>
>
> <details>
> <summary>"indexOf()"</summary>
> > Returns the index within the calling string of the first occurrence of a specified value.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let index = str.indexOf("world"); // Returns: 7
> > ```
>
> </details>
>
> <details>
> <summary>"slice()"</summary>
> > Extracts a section of a string and returns it as a new string.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let substr = str.slice(7); // Returns: "world!"
> > ```
>
> </details>
>
> <details>
> <summary>"substring()"</summary>
> > Returns the substring between two specified indices of a string.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let substr = str.substring(7, 12); // Returns: "world"
> > ```
>
> </details>
>
> <details>
> <summary>"toLowerCase()"</summary>
> > Returns the calling string converted to lowercase.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let lowerCaseStr = str.toLowerCase(); // Returns: "hello, world!"
> > ```
>
> </details>
>
> <details>
> <summary>"toUpperCase()"</summary>
> > Returns the calling string converted to uppercase.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let upperCaseStr = str.toUpperCase(); // Returns: "HELLO, WORLD!"
> > ```
>
> </details>
>
> <details>
> <summary>"trim()"</summary>
> > Removes whitespace from both ends of a string.
> 
> > ```javascript
> > let str = "   Hello, world!   ";
> > let trimmedStr = str.trim(); // Returns: "Hello, world!"
> > ```
>
> </details>
>
> <details>
> <summary>"split()"</summary>
> > Splits a string into an array of substrings based on a specified separator.
> 
> > ```javascript
> > let str = "Hello, world!";
> > let parts = str.split(", "); // Returns: ["Hello", "world!"]
> > ```
>
> </details>
>
</details>



<details open>
<summary>String Method Video Sources</summary>

> <a href="https://youtu.be/VRz0nbax0uI?si=2qNC7jyNuvx7MSuh">20 String Methods</a> - Freecodecamp
>
> <a href="https://youtu.be/09BwruU4kiY?si=F8dHu_jjQg1KZaDb">JavaScript Strings Explained</a> - Programming with Mosh
>
> <a href="https://youtu.be/LiuzigJldNo?si=8imMYt48T-CgZMR9">JavaScript String Methods and Properties</a> - Dave Gray
>
> <a href="https://youtube.com/shorts/rgMokYx1w60?si=m9g3FKVwiXBVzSDS">Functions vs Methods</a> - VickyMei


</details>

### In-Class Excercise #1

<details open>
<summary>In-class Exercise #1:Strings and String Methods</summary>

> Start by opening your browser's developer tools as before.
>
> Navigate to the "Console" tab in the developer tools.
>
> Now, let's explore some string manipulation using JavaScript. You can perform various operations on strings using built-in string methods.
>
> Here's an example of how you can use string methods to manipulate a string:
>
> ```javascript
> // Define a sample string
> let str = "Hello, world!";
>
> // Use string methods to manipulate the string
> let upperCaseStr = str.toUpperCase(); // Convert the string to uppercase
> let slicedStr = str.slice(7); // Extract a substring starting from index 7
> let replacedStr = str.replace("world", "everyone"); // Replace a substring within the string
>
> // Output the results to the console
> console.log("Original String:", str);
> console.log("Uppercase String:", upperCaseStr);
> console.log("Sliced String:", slicedStr);
> console.log("Replaced String:", replacedStr);
> ```
>
> After typing the JavaScript code in the console, press Enter to execute it. You'll see the results logged in the console.
>
> Experiment with other string methods such as `charAt()`, `indexOf()`, `concat()`, `trim()`, etc., to perform different operations on strings.
>
</details>


### In-Class Excercise #2

<details open>
<summary>In-class Exercise #2: Let's make it a little more difficult</summary>

> Let's test your knowledge of JavaScript string methods! Complete the following tasks by writing JavaScript code in your browser's developer console.
>
> 1. **Task 1: Find the Index**
>    - Define a string variable named `str` with the value `"Hello, world!"`.
>    - Use the appropriate string method to find the index of the first occurrence of the substring `"world"` within the string.
>    - Log the index to the console.
>
> 2. **Task 2: Extract Substring**
>    - Use the `str` variable defined in Task 1.
>    - Use the appropriate string method to extract the substring starting from the 7th character to the end of the string.
>    - Log the extracted substring to the console.
>
> 3. **Task 3: Uppercase Conversion**
>    - Define a string variable named `str2` with the value `"javascript is awesome!"`.
>    - Use the appropriate string method to convert the entire string to uppercase.
>    - Log the uppercase string to the console.
>
> 4. **Task 4: Concatenation**
>    - Use the `str` and `str2` variables defined in previous tasks.
>    - Use the appropriate string method to concatenate `str` and `str2` with a space in between.
>    - Log the concatenated string to the console.
>
> 5. **Task 5: Replace**
>    - Use the `str2` variable defined in Task 3.
>    - Use the appropriate string method to replace the substring `"awesome"` with `"fantastic"`.
>    - Log the modified string to the console.
>
> 6. **Task 6: Trim**
>    - Define a string variable named `str3` with the value `"   Hello, world!   "`.
>    - Use the appropriate string method to remove leading and trailing whitespace from `str3`.
>    - Log the trimmed string to the console.
>
> 7. **Task 7: Splitting**
>    - Use the `str3` variable defined in Task 6.
>    - Use the appropriate string method to split `str3` into an array of substrings separated by the comma and space `, `.
>    - Log the resulting array to the console.
>
> Complete each task, then press Enter after typing the JavaScript code in the console to execute it. Check the console output for the results of each task.
>
> > <details>
> > <summary>ANSWERS</summary>
> >
> > ```javascript
> > // Task 1: Find the Index
> > let str = "Hello, world!";
> > let index = str.indexOf("world");
> > console.log("Index of 'world':", index);
> >
> > // Task 2: Extract Substring
> > let extractedSubstring = str.slice(6);
> > console.log("Extracted Substring:", extractedSubstring);
> >
> > // Task 3: Uppercase Conversion
> > let str2 = "javascript is awesome!";
> > let uppercaseStr2 = str2.toUpperCase();
> > console.log("Uppercase String:", uppercaseStr2);
> >
> > // Task 4: Concatenation
> > let concatenatedStr = str.concat(" ", str2);
> > console.log("Concatenated String:", concatenatedStr);
> >
> > // Task 5: Replace
> > let replacedStr2 = str2.replace("awesome", "fantastic");
> > console.log("Replaced String:", replacedStr2);
> >
> > // Task 6: Trim
> > let str3 = "   Hello, world!   ";
> > let trimmedStr3 = str3.trim();
> > console.log("Trimmed String:", trimmedStr3);
> >
> > // Task 7: Splitting
> > let splittedStr3 = str3.split(", ");
> > console.log("Splitted Array:", splittedStr3);
> > ```
> >
> > </details>
</details>
