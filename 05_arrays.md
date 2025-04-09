# 05: Arrays

#### [Table of Contents](#table-of-contents)

  - [Intro](#intro)
  - [Structure \& Use](#structure--use)
  - [Loops](#loops)
  - [In-Class Exercise #1](#in-class-exercise-1)
  - [In-Class Exercise #2](#in-class-exercise-2)
  - [In-Class Exercise #3](#in-class-exercise-3)
  - [In-Class Exercise #4](#in-class-exercise-4)
  - [In-Class Exercise #5](#in-class-exercise-5)

---

## Intro

<details open>
<summary>What is an Array and why is it important?</summary>

> An array is a data structure in JavaScript used to store multiple values in a single variable. It's like a container that can hold various items, such as numbers, strings, or even other arrays, in an <strong>ordered sequence.</strong> 
> 
> ![Array Image](https://images.pexels.com/photos/4218982/pexels-photo-4218982.jpeg?auto=compress&cs=tinysrgb&w=400)
> 
> An array is like stacking textbooks in your locker. You can easily add more textbooks on top of each other, and they're all the same size and shape. You know how many textbooks you have by counting them, and you can grab a specific one by remembering its position in the stack.
> 
> Arrays are important because they allow us to <strong>organize and manipulate collections of data efficiently </strong>. They provide a way to store and access multiple values using a single variable name, which helps simplify code and make it more manageable. With arrays, we can perform tasks like iterating over elements, sorting, filtering, and much more, making them a fundamental part of programming in JavaScript.

</details>

## Structure & Use

<details open>
<summary>Structure</summary>
 
> Arrays in JavaScript are used to store multiple values in a single variable. They have a straightforward structure and can contain elements of various data types, including numbers, strings, objects, or even other arrays.
> 
> Here's a simple explanation of the structure of a JavaScript array:
> 
> **Declaration and Initialization**: You can create an array by using square brackets `[]` and assigning it to a variable. Here's an example:
>    
>    ```javascript
>    let myArray = []; // Empty array
>    ```
> 
>    You can also initialize an array with elements:
> 
>    ```javascript
>    let fruits = ['Apple', 'Banana', 'Orange'];
>    ```
> 
> **Accessing Elements**: You can access individual elements of an array using square brackets `[]` with the index of the element you want to access. Remember, JavaScript arrays use zero-based indexing, meaning the first element is at index 0, the second element at index 1, and so on. For example:
> 
>    ```javascript
>    console.log(fruits[0]); // Output: 'Apple'
>    console.log(fruits[1]); // Output: 'Banana'
>    ```
> 
</details>


<details open>
<summary>Use & Access</summary>

> **Modifying Elements**: You can modify elements in an array by accessing them using their index and assigning a new value to them. For example:
> 
>    ```javascript
>    fruits[2] = 'Grapes'; // Modifying 'Orange' to 'Grapes'
>    console.log(fruits); // Output: ['Apple', 'Banana', 'Grapes']
>    ```
> 
> **Array Length**: You can determine the number of elements in an array using the `length` property. For example:
> 
>    ```javascript
>    console.log(fruits.length); // Output: 3
>    ```
> 
> **Adding and Removing Elements**: JavaScript arrays come with built-in methods to add and remove elements. For example:
> 
>    - **Adding Elements**:
>      ```javascript
>      fruits.push('Mango'); // Adds 'Mango' to the end of the array
>      console.log(fruits); // Output: ['Apple', 'Banana', 'Grapes', 'Mango']
>      ```
>    - **Removing Elements**:
>      ```javascript
>      fruits.pop(); // Removes the last element ('Mango') from the array
>      console.log(fruits); // Output: ['Apple', 'Banana', 'Grapes']
>      ```
> 
> Understanding these basics will help you work effectively with arrays in JavaScript.
> 

</details>

---

<i>Now that we know the setup and access of an array. Let's learn a common practice</i>

## Loops

<details open>
<summary>What is Looping and why do we need it? </summary>

> Looping is a fundamental concept in programming that allows us to execute a block of code repeatedly. It's like walking down the aisles of a library, scanning through each book one by one.
> 
> ![alt text](https://images.pexels.com/photos/1370298/pexels-photo-1370298.jpeg?cs=srgb&dl=pexels-element-digital-1370298.jpg&fm=jpg)
>
> Similarly, in programming, we often deal with collections of data, such as arrays, where we may need to perform operations on each element. Looping allows us to iterate over each item in the array, performing the desired action, whether it's accessing, modifying, or analyzing the data.
>

</details>

<details open>
<summary>Common ways to loop through an array</summary>

> <details open>
> <summary>Example 1: Using a for Loop</summary>
>
> > In this example, we use a traditional for loop to iterate through each element of the array and log each element to the console.
>
> ```javascript
> const array = [1, 2, 3, 4, 5];
>
> for (let i = 0; i < array.length; i++) {
>   console.log(array[i]);
> }
> ```
>
> > Explanation:
> > - We initialize a variable `i` to 0, representing the index of the first element in the array.
> > - The loop continues as long as `i` is less than the length of the array.
> > - Inside the loop, we access each element of the array using `array[i]` and log it to the console.
> > - After each iteration, `i` is incremented by 1 to move to the next element in the array.
>
> </details>
> -
> <details open>
> <summary>Example 2: Using forEach Method</summary>
>
> > In this example, we use the forEach method to iterate through each element of the array and perform a callback function on each element.
>
> ```javascript
> const array = [1, 2, 3, 4, 5];
>
> array.forEach((element) => {
>   console.log(element);
> });
> ```
>
> > Explanation:
> > - The forEach method iterates through each element of the array.
> > - For each element, it executes the callback function provided as an argument.
> > - In this case, the callback function logs each element to the console.
>
> </details>
>-
> <details open>
> <summary>Example 3: Using for...of Loop</summary>
>
> > In this example, we use the for...of loop to directly iterate through the values of the array.
>
> ```javascript
> const array = [1, 2, 3, 4, 5];
>
> for (const element of array) {
>   console.log(element);
> }
> ```
>
> > Explanation:
> > - The for...of loop iterates through the values of the array directly, without needing an index.
> > - In each iteration, the loop assigns the current element of the array to the variable `element`.
> > - We then log each element to the console within the loop.
>
> </details>

</details>




## In-Class Exercise #1

<details open>
<summary>Exercise #1: JavaScript common array operations</summary>

>```javascript
>  // Method to add elements to the array
>  addElement(element) {
>    // Write code here to add 'element' to the array
>    // Hint: Use the push method to add 'element' to 'this.array'
>  }
>
>  // Method to access elements by index
>  accessElement(index) {
>    // Write code here to access the element at 'index' in the array
>    // Hint: Use square brackets to access the element at 'index'
>  }
>
>  // Method to modify elements in the array
>  modifyElement(index, newValue) {
>    // Write code here to modify the element at 'index' with 'newValue'
>    // Hint: Use square brackets to access the element at 'index' and assign 'newValue' to it
>  }
>
>  // Method to get the length of the array
>  arrayLength() {
>    // Write code here to return the length of the array
>    // Hint: Use the length property of the array
>  }
>
>  // Method to remove the last element from the array
>  removeLastElement() {
>    // Write code here to remove the last element from the array
>    // Hint: Use the pop method to remove the last element
>  }
>
>  // Method to display the array
>  displayArray() {
>    // Write code here to display the contents of the array
>    // Hint: Use console.log to print the array
>  }
>  ```
>
>> <details>
>><summary><h2>Answers</h2></summary>
>>
>>```javascript
>>
>>// Add elements to the array at specific indices
>>advancedArray.addElementAtIndex('Apple', 0);
>>advancedArray.addElementAtIndex('Banana', 1);
>>advancedArray.addElementAtIndex('Orange', 2);
>>
>>// Remove an element from the array at a specific index
>>advancedArray.removeElementAtIndex(1);
>>
>>// Check if a value exists in the array
>>console.log(advancedArray.containsValue('Banana')); // Expected output: false
>>
>>// Find the index of a value in the array
>>console.log(advancedArray.findIndex('Orange')); // Expected output: 1
>>
>>// Reverse the order of elements in the array
>>advancedArray.reverseArray();
>>
>>// Sort the elements in the array
>>advancedArray.sortArray();
>>
>>// Perform custom sorting based on a specific property of objects in the array
>>advancedArray.customSort('name');
>>
>>// Filter elements in the array based on a condition
>>let filteredArray = advancedArray.filterArray(element => element % 2 === 0);
>>
>>// Map each element of the array to a new value
>>let mappedArray = advancedArray.mapArray(element => element * 2);
>>
>>// Reduce the array to a single value using a reducer function
>>let reducedValue = advancedArray.reduceArray((accumulator, currentValue) => accumulator + currentValue, 0);
>>```
>></details>
</details>

<h3>Keep practicing the above example until you feel like you understand how arrays are accessed and </h3>

## In-Class Exercise #2 

<details open>
<summary>class Exercise: Advanced JavaScript accessing</summary>

> ```javascript
>  // Method to add elements to the array at a specific index
>  addElementAtIndex(element, index) {
>    // Implement code to add 'element' at 'index' in the array
>    // Hint: Use splice method to insert 'element' at 'index'
>  }
>
>  // Method to remove an element from the array at a specific index
>  removeElementAtIndex(index) {
>    // Implement code to remove the element at 'index' from the array
>    // Hint: Use splice method to remove element at 'index'
>  }
>
>  // Method to check if a value exists in the array
>  containsValue(value) {
>    // Implement code to check if 'value' exists in the array
>    // Hint: Use indexOf method to check if 'value' is present in the array
>  }
>
>  // Method to find the index of a value in the array
>  findIndex(value) {
>    // Implement code to find the index of 'value' in the array
>    // Hint: Use indexOf method to find the index of 'value'
>  }
>
>  // Method to reverse the order of elements in the array
>  reverseArray() {
>    // Implement code to reverse the order of elements in the array
>    // Hint: Use reverse method to reverse the array
>  }
>
>  // Method to sort the elements in the array
>  sortArray() {
>    // Implement code to sort the elements in the array
>    // Hint: Use sort method to sort the array
>  }
>
>  // Method to perform a custom sorting based on a specific property of objects in the array
>  customSort(property) {
>    // Implement code to perform custom sorting based on 'property' of objects in the array
>    // Hint: Use sort method with a custom comparator function to sort based on 'property'
>  }
>
>  // Method to filter elements in the array based on a condition
>  filterArray(condition) {
>    // Implement code to filter elements in the array based on 'condition'
>    // Hint: Use filter method to filter elements based on 'condition'
>  }
>
>  // Method to map each element of the array to a new value
>  mapArray(mappingFunction) {
>    // Implement code to map each element of the array to a new value using 'mappingFunction'
>    // Hint: Use map method to map elements to new values based on 'mappingFunction'
>  }
>
>  // Method to reduce the array to a single value using a reducer function
>  reduceArray(reducerFunction, initialValue) {
>    // Implement code to reduce the array to a single value using 'reducerFunction' and 'initialValue'
>    // Hint: Use reduce method to reduce the array to a single value based on 'reducerFunction' and 'initialValue'
>  }
>```
>
><details>
><summary><h2>Answers</h2></summary>
>
>```javascript
>// Test your AdvancedArrayOperations class
>let advancedArray = new AdvancedArrayOperations();
>
>// Add elements to the array at specific indices
>advancedArray.addElementAtIndex('Apple', 0);
>advancedArray.addElementAtIndex('Banana', 1);
>advancedArray.addElementAtIndex('Orange', 2);
>
>// Remove an element from the array at a specific index
>advancedArray.removeElementAtIndex(1);
>
>// Check if a value exists in the array
>console.log(advancedArray.containsValue('Banana')); // Expected output: false
>
>// Find the index of a value in the array
>console.log(advancedArray.findIndex('Orange')); // Expected output: 1
>
>// Reverse the order of elements in the array
>advancedArray.reverseArray();
>
>// Sort the elements in the array
>advancedArray.sortArray();
>
>// Perform custom sorting based on a specific property of objects in the array
>advancedArray.customSort('name');
>
>// Filter elements in the array based on a condition
>let filteredArray = advancedArray.filterArray(element => element % 2 === 0);
>
>// Map each element of the array to a new value
>let mappedArray = advancedArray.mapArray(element => element * 2);
>
>// Reduce the array to a single value using a reducer function
>let reducedValue = advancedArray.reduceArray((accumulator, currentValue) => accumulator + currentValue, 0);
>```
></details>

</details>


## In-Class Exercise #3 

<details open>
<summary>class Exercise: for loop</summary>

> Calculate the sum of all numbers in the array.
> ```javascript
> const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
> // Task 1: Using a for Loop
>```
><details>
><summary><h2>answers</h2></summary>
>
>```javascript
> let sum = 0;
> for (let i = 0; i < numbers.length; i++) {
>   sum += numbers[i];
> }
> console.log("Sum using for loop:", sum);
>
>```
></details>

</details>


## In-Class Exercise #4 

<details open>
<summary>class Exercise: forEach method</summary>

> Find and log all numbers greater than 5 in the array.
> ```javascript
> const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
> // Task 2: Using forEach Method
>```
><details>
><summary><h2>answers</h2></summary>
>
>```javascript
> console.log("Numbers greater than 5 using forEach:");
> numbers.forEach((number) => {
>   if (number > 5) {
>     console.log(number);
>   }
> });
>```
></details>

</details>


## In-Class Exercise #5 

<details open>
<summary>class Exercise: for...of loop</summary>

> Count the total number of even numbers in the array.
> ```javascript
> const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
> // Task 3: Using for...of Loop
>```
><details>
><summary><h2>answers</h2></summary>
>
>```javascript
> let evenCount = 0;
> for (const number of numbers) {
>   if (number % 2 === 0) {
>     evenCount++;
>   }
> }
> console.log("Total even numbers:", evenCount);
>```
></details>

</details>
