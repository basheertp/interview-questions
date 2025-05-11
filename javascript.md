# Javascript questions

## What is hoisting 
Hoisting in JavaScript is a behavior where variable and function declarations are moved to the top of their scope before code execution. This allows you to use functions and variables before they are declared in the code. However, it's important to note that only declarations are hoisted, not initializations
```console.log(myVar); // Output: undefined
var myVar = 10;
console.log(myVar); // Output: 10
```
## console.log(console.log('hello')); what will be the output 
```console.log(console.log('hello'));
hello
undefined
```
## console.log('test',console.log('hello')); what will be the output 
```
console.log('test',console.log('hello'));
hello
test undefined
```
## Given array remove a number 
Example  
const numbers = [2,4,5,7,1,3];
Remove 4 
```
numbers.filter(num => num !== 4)
output: [2,5,7,1,3]
```
# How many types of variable declaration are in js  
var, let, const
#  Difference between const, let, var 
#  How to define a value array and it can’t be modified 
``` const myArray = Object.freeze([1, 2, 3]);
```
#  How to define a value object and it can’t be modified, example 
```
const myObject = Object.freeze({
  name: 'John',
  age: 30
});

// Attempting to modify the properties
myObject.name = 'Jane';  // This will not change the name
myObject.age = 35;       // This will not change the age

console.log(myObject); // Output: { name: 'John', age: 30 }

```
#  Difference between map and filter 
map():
Transforms each element in an array and returns a new array with the transformed values.
Does not change the original array.
filter():
Filters elements in an array based on a condition and returns a new array with only those elements that pass the test.
Does not change the original array
#  What is event delegation 
Event delegation is a technique in JavaScript where you attach a single event listener to a parent element rather than individual child elements. This takes advantage of event bubbling, which is the process by which events propagate from the target element up through its ancestors in the DOM.
Let's say you have a list of items, and you want to handle the click event for each list item. Instead of adding an event listener to each <li> element, you can add one event listener to the parent <ul> element.
```
<ul id="item-list">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
  <li>Item 4</li>
</ul>

<script>
  const itemList = document.getElementById('item-list');

  // Add a single event listener to the parent element
  itemList.addEventListener('click', function(event) {
    // Check if the clicked element is an <li>
    if (event.target.tagName.toLowerCase() === 'li') {
      console.log(`You clicked on ${event.target.textContent}`);
    }
  });
</script>

```
Benefits of Event Delegation:
Improved Performance: Instead of attaching event listeners to every ```<li>```, you attach one listener to the parent ```<ul>```.

Works with Dynamically Added Elements: If new list items are added to the ```<ul>```, they will automatically have the event listener without needing to reattach the event listener to each new element.

#  Difference between node version 18 to 22 in react app 
#  Error handling in react 
Handling Errors in Components (using Error Boundaries)
Handling Errors in Asynchronous Code
try...catch
# Difference between in error boundary and try catch 
### Error Boundary:
Specifically designed for handling errors in React components, including rendering, lifecycle methods, and constructors. It provides a way to catch JavaScript errors in React component trees.
### try...catch:
A general-purpose JavaScript mechanism to handle synchronous errors within code blocks.
# How to update a div content using vanilla javascipt 
```
document.getElementById('myDiv');
```
# Difference between normal function and jsx function 
### Normal JavaScript Function:
A normal function in JavaScript is simply a standard function declaration or expression that executes some code, returns a value, and can be used in your JavaScript code to perform various tasks.
### JSX Function (React Component):
A JSX function in React refers to a React component that returns JSX elements. JSX is a syntax extension for JavaScript, and it allows you to write HTML-like code inside JavaScript. JSX functions (React components) are used to render UI in a React app.


### Array some vs every
some(): This method tests whether at least one element in the array passes the
provided function's test. It returns true if it finds an element that satisfies the
condition and false otherwise. The some() method stops iterating through the array
as soon as it finds a matching element.
``` const numbers = [1, 5, 7, 9, 2];
const hasEvenNumber = numbers.some(number => number % 2 === 0);
console.log(hasEvenNumber); // Output: true
```
every(): This method tests whether all elements in the array pass the provided function's test. It
returns true only if all elements satisfy the condition and false otherwise. The every() method
stops iterating through the array as soon as it finds an element that does not satisfy the
condition.
``` const numbers = [2, 4, 6, 8, 10];
const allEvenNumbers = numbers.every(number => number % 2 === 0);
console.log(allEvenNumbers); // Output: true
```
