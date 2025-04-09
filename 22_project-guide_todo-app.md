# Project Guide: ToDo App

#### [Table of Contents](#table-of-contents)
  - Overview
  - UI
  - Model
  - Functions
  - Events
  - Animations
  - Local Storage
  - Tips

> <details open>
> <summary>Resources</summary>
>
> - [YouTube Video - Build a Todo list app in HTML, CSS & JavaScript in 2024](https://youtu.be/MkESyVB4oUw?si=TLR_06z8DAn9TxfE)
> - [YouTube Video - How to Code A Better To-Do List](https://www.youtube.com/watch?v=W7FaYfuwu70)
> - [W3Schools JavaScript Reference](https://www.w3schools.com/jsref/)
>   - More beginner-friendly -- but less comprehensive documentation site
> - [W3Schools JavaScript Examples](https://www.w3schools.com/js/js_examples.asp)
> - [javascript.info](https://javascript.info)
>   - Gold standard of JavaScript education
>
> </details>

## Overview
> The purpose of this guide is to provide you with a good structure to follow when building your Todo app. If you follow this pattern, you will find it a lot easier to complete the project. This guide will not spell everything out but rather will give you a good guidance and help you avoid pitfalls.

## UI
>  A big part of this app is making stuff appear on the screen and to make it interactable. All good apps have a good UI. UI stands for user interface. In this guide this means the HTML and CSS you will write.

<details open>
<summary>Step 1: UI</summary>
Create a good container div that will hold both the left menu and the right todo list display. I recommend using the bootstrap grid for this. It gives you a simple and easy way to arrange things in your HTML. I use that along with flexbox and keep things simple. Here is an example of an overall layout you would need to create a list like this.

```
 <div class="outer">
 <nav class="navbar">
     <!-- navbar not needed but looks cool -->
 </nav>
 <div class="container-fluid">
    <div class="row">
      <div class="col-3">
        <!-- list of todo lists go here -->
      </div>
      <div class="col-8">
        <!-- current todo list name goes here -->
        <!-- current todo list goes here -->
      </div>
    </div>
   </div>
  </div>
```
</details>

<details open>
<summary>Step 2: UI</summary>
Create an input and a list on the left part of the UI. The cleanest look would be to have an input box on the left and underneath have the list of todo lists. While the list will be generated dynamically with JS, you can create a dummy list so you can get some of the formatting done. Look to the bootstrap list group for this. It is a good clean look. Remember to give the input an id so you can then reference it in JS and get the value of it. Use flexbox to make the input have the width of the column.

</details>

<details open>
<summary>Step 3: UI</summary>
Create a container that will hold a title and the to-dos of the current list. You have a decision to make here, and that is, how are you going to let the user input more to-dos? The easiest way would be to have an input box and an “Add” button, when the user clicks the add button your JS will create a new to-do and make it appear in the list below the input.
</details>

<details open>
<summary>Model</summary>
This is a very important part of the app. In this part is where you create the way data will be represented in your app. If you do this part right, the rest of the app will be a lot easier. Spend some time understanding how you are going to represent the list or object that will contain the to-do lists. The main concerns you will be faced with in this app are: 
+ How to keep track of each list and each to-do in each list
+ How to relate a user input (i.e. button) with the lists or to-dos
+ How will I save and retrieve the lists

</details>

<details open>
<summary>Step 1: UI</summary>
Create the data structure that you are going to use for your list of lists. In class we are going to go over classes and you are welcome to do that but if you want to make things easier for this first app a well thought out and executed object will do the trick. For the list that will contain the list you could create an array, however, if you make it an object, you will save yourself some headaches. So what would be the key in the object? Remember that objects have key-value pairs. The value is clearly the list but what about the key? You are right, an “id” of some sort. So it would look something like this:

```
 const lists = {
 1: {name: 'Shopping list'},
 2: {name: 'Honey do list'},
 ...
}
```
</details>

<details open>
<summary>Step 2: Model</summary>
Create the data structure for a list. Now, let’s think about this. How easy will life be if you keep all the data about a list inside an object? That’s what objects are there for right? So what would you put in there? The name of the list of course, what else? The to-do’s duh! It could look something like this:

```
const currentList = {
 name: "Shopping list",
 todos: [
 ]
}
```
</details>

<details open>
<summary>Step 3: Model</summary>
Create the data structure for a todo. Now, the todo will have a text or value right? Something that someone has todo. But it also needs another field. A way for you to know or set whether or not that todo has been completed. This field will likely be represented as a checkbox but in code it should be boolean. This here is a good start:

```
todos: [
   {
     text: 'bananas',
     completed: false
   },
   {
     text: '1 lbs ground turkey',
     completed: false
   }
 ]
```
</details>

<details open>
<summary>Step 4: Model</summary>
Putting it all together. Here is what it would all look like. Again, this is a start. You may need more fields. You can create this as a testing object as you start to create the rest of the application. If you are not quite sure what’s going on with this code, take some time to understand it before you continue. Ask questions!

```
const lists = {
 1: {
   name: "Shopping list",
   todos: [
     {
       text: 'bananas',
       completed: false
     },
     {
       text: '1 lbs ground turkey',
       completed: false
     }
   ]
 },
}
const currentList = lists[0];
```
</details>

<details open>
<summary>Functions</summary>
Ok, we are now getting to the fun part of the project. This is the part where we make things happen! With our functions and logic our goal is simple, make it do what we want with the simplest approach. There are many, in fact, infinitely many ways to write this app but we are going to strive for simplicity. Why? Because by doing so, it will keep us from banging our heads on the keyboard too much trying to figure out what in the world is going on. We want to have a main function that does most of the heavy lifting and then other functions that react to user input.
</details>

<details open>
<summary>Step 1: Functions</summary>
Create a render function. This is the function that will do the heavy lifting. It will be in charge of rendering all of the content in the page. Creating one function to do it all rather than handling it in different functions has the benefit that it can be called anytime changes are made to the data. For example, someone adds a to-do, you add the to-do to the correct list and then call the render function. Your render function can look something like this: 

```
function render() {
 // this will hold the html that will be displayed in the sidebar
 let listsHtml = '<ul class="list-group">';

 // iterate through the lists to get their names
 lists.forEach((list) => {
   listsHtml += `<li class="list-group-item">${list.name}</li>`;
 });
 listsHtml += '</ul>';

 // print out the lists
 document.getElementById('lists').innerHTML = listsHtml;

 // print out the name of the current list
 document.getElementById('current-list-name').innerText = currentList.name;

 // iterate over the todos in the current list

 let todosHtml = '<ul class="list-group-flush">';
 currentList.todos.forEach((list) => {
   todosHtml += `<li class="list-group-item">${todo.text}</li>`;
 });

 // print out the todos
 document.getElementById('current-list-todos').innerHTML = todosHtml;
}

```
</details>

<details open>
<summary>Steps 2: Functions</summary>
Step 2: Add functions to react to user input. So the user can do many things in your application right? From creating new lists to marking a todo as complete. You have to write a function for each of these actions. Here is one example but the most important thing here is that your functions should modify the model (data) and then call the render function. You should avoid modifying html in your function. So, here is an example of a function you would use. A user tries to add a todo. You set up a button for this and have an input where they can type their todo.  

```
function addTodo() {
 // get the todo text from the todo input box
 const text = document.getElementById('todo-input-box').value;
 if(text) {
   currentList.todos.push({
     text: text,
     completed: false
   })
   render();
 }
}
```
</details>

<details open>
<summary>Steps 3: Functions</summary>
Here is a list of functions you will probably need:
  
  - addList
  - removeList
  - addTodo
  - removeTodo
  - markTodoAsCompleted
  - removeAllTodosCompleted
    
</details>

<details open>
<summary>Events</summary>
Ok, so now you have some functions that update the model and render the new html. What we need to do now is tie those functions to html events. Most of those will be clicks. In this example we tie into the onclick dom event. Inside the addList function we get the value from the input next to the button, create a new list, and add it to the object of lists.

```
  <div>
    <input id="new-list-name-input">
    <button class="btn btn-primary" onclick="addList()"></button>
  </div>
```
</details>

<details open>
<summary>Animations</summary>
Animations are not necessary in an app but when used correctly can provide valuable feedback to the user as well as make your app feel polished. As with the rest of the app we want to keep things simple when it comes to animations. Luckily for us, UI animations have been around for a while so there are some dead simple to use libraries out there. One of my favorites is animate css. All you need to do is add the library to your project and then add or remove a class to an html element to make it animate. You can find it here animate.css
</details>

<details open>
<summary>More on Animations</summary>
Let’s try an animation. Here is the recipe for animating a the removal of completed todo. Three basic steps. All super simple. This would be inside your deleteTodo or deleteCompleted functions:

```
 // get element by the id
 const todoElement = document.getElementById(todoId);
 // step 1, add the animated class and the animation class you want
 todoElement.classList.add('animated', 'fadeOutRight');
 // step 2, remove the todo from the list
 currentList.todos = currentList.todos.filter(todo => todo == todoId)
 // step 3, set a timer so that after the animation
 // the html renders again and the
 setTimeout(render, 650);

```
</details>

<details open>
<summary>Local Storage</summary>
Local storage is dead simple. Well, it can be if you used the model similar to the one described on this guide. Really all you have to do is create a save function that will save the state of the app. So you will save your lists and currentList objects to local storage and then retrieve them at the start of your main javascript file. You will want to call your save function every time you call your render function. That way you save anytime there are changes. Your save function will look something like this:
  
```
  function save() {
    localStorage.setItem('currentList', JSON.stringify(currentList)); 
    localStorage.setItem('lists', JSON.stringify(lists));
  }
```
</details>

<details open>
<summary>Local Storage</summary>
Here are some tips that will help you succeed building this app:
Work with ids. Give each list an id and give each todo an id. That way you can easily refer to them in the html. You will want to create a way for ids to be unique. I would make a function that creates a random 16 character id and then call that function every time I need a new id. You can google that and find many ideas on stack overflow. That way when you have to bind a click or a checkbox to a todo you can do so by the id. Something like, 
  
```
  <input type="checkbox" id="${'todo-' + todo.id}" onclick="completeTodo(${todo.id})">
```
</details>
