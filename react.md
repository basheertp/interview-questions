# react-question

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
#  Difference between const, let, var 
#  How to define a value array and it can’t be modified 
const myArray = Object.freeze([1, 2, 3]); 
#  How to define a value object and it can’t be modified, example 
#  Const employee = {id: 1, name: “basheer”}  
Above object can modify the value but should not add any new properties 
#  Difference between map and filter 
#  Difference between map and for loop 
#  What is event delegation 
#  Difference between node version 18 to 22 in react app 
#  Error handling in react 
# Difference between in error boundary and try catch 
# How to update a div content using vanilla javascipt 
# Difference between normal function and jsx function 
