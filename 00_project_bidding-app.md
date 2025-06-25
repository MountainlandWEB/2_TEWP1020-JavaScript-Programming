## 🎯 Objective
Build an interactive bidding web app that allows two users to input bids, stores them in the browser using localStorage, and displays all bids in real-time. This exercise is designed to reinforce ES6+ syntax, DOM manipulation, array methods, and data persistence in the browser.

## 📝 Project Summary
You're building a small web application that:
- Allows two users to place numerical bids via input fields.
- Stores the bids in localStorage so data persists after a refresh.
- Dynamically displays all current bids in a list.
- Teaches modern ES6+ techniques like:
- Template literals
- Arrow functions
- Object shorthand
- Array iteration with ```.forEach()```
- Destructuring (optional bonus)

## 📋 Requirements & Features
Students will create the HTML (index.html) file with:
- A <div> for displaying bids.
- Two input areas for Bidder 1 and Bidder 2.
- A button for each to submit a bid.
- They should not modify the HTML, but understand its role in the DOM interaction.

### Tasks:
- Create an array of bid objects
- Each object should have:

```
js
{
  amount: Number,
  user: String
}
```

### Use localStorage to persist bid history across page reloads:
- Implement a ```saveBids()``` function to store data.
- Implement a ```retrieveBids()``` function to load existing bids on page load.

### Render all bids to the DOM dynamically using:
- Array.prototype.forEach()
- Template literals (`...${}`)

### Use modern JS syntax:
- Object shorthand: ```{ user, amount }``` instead of ```{ user: user, amount: amount }```
- Arrow functions (optional for advanced students)
- Default parameters and ternary operators (optional enhancements)

### Add validation (Advanced students):
- Ensure that the input is a number.
- Do not allow empty submissions.
