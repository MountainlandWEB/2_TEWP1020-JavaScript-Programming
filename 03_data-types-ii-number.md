# 03: Data Types
## 2 - NUMBER
## NUMBER 
![alt text](https://as2.ftcdn.net/v2/jpg/03/15/11/81/1000_F_315118105_ld6nWZl5CXLyv5rIEHuPNtVjXFcJCfXn.jpg)
<details open>
<summary>JavaScript Numbers</summary>

> JavaScript numbers are used to represent numeric values in code. They can be integers or floating-point numbers.
>
> Here are three common coding examples involving JavaScript numbers:
>
> 1. **Defining Numbers:**
>    ```javascript
>    let num1 = 10; // Integer
>    let num2 = 3.14; // Floating-point number
>    ```
>
> 2. **Arithmetic Operations:**
>    ```javascript
>    let sum = num1 + num2; // Addition
>    let difference = num1 - num2; // Subtraction
>    let product = num1 * num2; // Multiplication
>    let quotient = num1 / num2; // Division
>    ```
>
> 3. **Mathematical Functions:**
>    ```javascript
>    let radius = 5;
>    let area = Math.PI * Math.pow(radius, 2); // Calculating the area of a circle
>    let squareRoot = Math.sqrt(16); // Finding the square root of a number
>    ```

</details>


### Number Methods
<details open>
<summary>Common Number Methods</summary>

> JavaScript provides several built-in methods for performing operations on numbers. Here are some of the top number methods along with examples and explanations:
>
> 1. **toFixed():**
>    - This method formats a number using fixed-point notation.
>    ```javascript
>    let num = 10.12345;
>    let formattedNum = num.toFixed(2); // Result: 10.12
>    ```
>
> 2. **toPrecision():**
>    - This method formats a number to a specified length.
>    ```javascript
>    let num = 123.456789;
>    let formattedNum = num.toPrecision(4); // Result: 123.5
>    ```
>
> 3. **toString():**
>    - This method converts a number to a string.
>    ```javascript
>    let num = 42;
>    let strNum = num.toString(); // Result: "42"
>    ```
>
> 4. **parseInt():**
>    - This method parses a string and returns an integer.
>    ```javascript
>    let strNum = "10";
>    let intNum = parseInt(strNum); // Result: 10
>    ```
>
> 5. **parseFloat():**
>    - This method parses a string and returns a floating-point number.
>    ```javascript
>    let strNum = "3.14";
>    let floatNum = parseFloat(strNum); // Result: 3.14
>    ```
>
> 6. **isNaN():**
>    - This method checks if a value is NaN (Not a Number).
>    ```javascript
>    isNaN(10); // Result: false
>    isNaN("hello"); // Result: true
>    ```
>

</details>


### In-Class Exercise #3
<details open>
<summary>In-Class Exercise #3: Number Methods</summary>

> Task 1: Fixed-Point Notation
> Define a number variable named num1 with the value 123.456.
> Use the toFixed() method to format num1 to two decimal places.
> Log the formatted number to the console.
>
> Task 2: Number Precision
> Define a number variable named num2 with the value 1234.56789.
> Use the toPrecision() method to format num2 to three significant digits.
> Log the formatted number to the console.
>
> Task 3: Convert to String
> Define a number variable named num3 with the value 42.
> Use the toString() method to convert num3 to a string.
> Log the converted string to the console.
>
> Task 4: Parse Integer
> Define a string variable named strNum1 with the value "10".
> Use the parseInt() method to parse strNum1 and convert it to an integer.
> Log the parsed integer to the console.
>
> Task 5: Parse Float
> Define a string variable named strNum2 with the value "3.14".
> Use the parseFloat() method to parse strNum2 and convert it to a floating-point number.
> Log the parsed floating-point number to the console.
>
> Task 6: Check NaN
> Use the isNaN() method to check if the value "hello" is NaN (Not a Number).
> Log the result to the console.
>
> Task 7: Check Finite
> Use the isFinite() method to check if the value Infinity is a finite number.
> Log the result to the console.
>
> Complete each task, then press Enter after typing the JavaScript code in the console to execute it. Check the console output for the results of each task.
>
> > // Task 1: Fixed-Point Notation
> > let num1 = 123.456;
> > let formattedNum1 = num1.toFixed(2);
> > console.log("Formatted Number:", formattedNum1);
> >
> > // Task 2: Number Precision
> > let num2 = 1234.56789;
> > let formattedNum2 = num2.toPrecision(3);
> > console.log("Formatted Number:", formattedNum2);
> >
> > // Task 3: Convert to String
> > let num3 = 42;
> > let strNum3 = num3.toString();
> > console.log("Converted String:", strNum3);
> >
> > // Task 4: Parse Integer
> > let strNum1 = "10";
> > let parsedInt = parseInt(strNum1);
> > console.log("Parsed Integer:", parsedInt);
> >
> > // Task 5: Parse Float
> > let strNum2 = "3.14";
> > let parsedFloat = parseFloat(strNum2);
> > console.log("Parsed Float:", parsedFloat);
> >
> > // Task 6: Check NaN
> > let checkNaN = isNaN("hello");
> > console.log("Is 'hello' NaN:", checkNaN);
> >
> > // Task 7: Check Finite
> > let checkFinite = isFinite(Infinity);
> > console.log("Is Infinity finite:", checkFinite);

</details>
