---
layout: post
title:      "How to Use 'Scope' in Javascript "
date:       2021-02-25 16:27:08 +0000
permalink:  how_to_use_scope_in_javascript
---

While working on my javascript assessment I seemed to have overlooked the power of ‘scope’. I’d like to clarify and reiterate the importance of scope as this concept is commonly used in javascript, and if use correctly it can keep your code clean and bug free. When used improperly, it can potentially cause errors in the application. 	

The main benefit of scope is that the variables can be accessed from only a certain area of the program. Using scope, we can avoid unintended modifications to the variables from other parts of the program.

So we will first define scope and then we will provide a few examples that will help us remember the use cases in each situation.


Global Scope - A variable that is not inside any function or block and is accessible from anywhere in the program. 
_______________
Example: 

var username = ‘Shay’;

function sayUsername() {
  console.log(username);
}

sayUsername();
// Prints ’Shay
_______________

Function (Local) Scope - A variable that is declared inside a function is within the local scope. The variable can only be accessed within that function and cannot be accessed from anywhere outside the code. 
_______________
Example:

function sayUsername() {
  var username = ‘Shay’;
  console.log(username);
}

username();
// Uncaught ReferenceError: username is not defined
console.log(username);
_______________

Block Scope  - Introduced in ES6, let and const variables declared inside curly braces can only be accessed from within the block of code. 
_______________
Example:
{
  let username = ‘Shay’;
  var lang = 'English';
  console.log(username); // Prints ‘Shay’
}

console.log(lang);
// Prints 'English'

console.log(username);
// Uncaught ReferenceError: username is not defined
_______________

Lexical Scope 

In a nested group of functions, the inner functions have access to the variables and other resources of their parent scope. This means that the child functions are lexically bound to the execution context of their parents. Lexical scope is sometimes also referred to as Static Scope.
_______________
Example: 

function grandfather() {
    var name = ‘Shayan’;
    // likes is not accessible here

    function parent() {
        // name is accessible here
        // likes is not accessible here

        function child() {
            // Innermost level of the scope chain
            // name is also accessible here
            var likes = 'Coding';
        }
    }
}
_______________


Declaration Styles

Var - var and let are very similar in the fact that you can reassign a value later on. The main difference between the two though is that let deals with block scope whereas var deals with global scope or function scope depending on where it’s declared. As long as your variable isn’t declared within any function, var can be used again anywhere else in your code.

_______________
Example:

Var numOfCameras = 25;
Var numOfCameras = 100;

console.log(numOfBananas); // Prints 100
_______________


Const - when you assign a value to a variable when using const, it means that you cannot give that variable another value later on. In other words, if you try to change a const variable, you will get an error thrown back at you. If you set a const statement inside of a block, however, it will only remain inside of that block.

_______________
Example:

const x = 20; 
const y = 'boy';
const z = 'developer';
_______________

const x; // SyntaxError: missing initializer
_______________

Changing const: 

const name = 'chris';

name = 'john'; // Uncaught TypeError: Assignment to constant variable.

_______________

const person = {};

person.name = 'chris'; // no error
_______________




Let - Similar to const, let also works in terms of block scope. However, it is also similar to var in the fact that let does allow you to change its value later on in your code.

Examples:

let numOfCameras = 50;
numOfCameras = 100;

console.log(numOfCameras); // Prints 100
__________________________

let numOfApples = 50;
let numOfApples = 100; 

console.log(numOfApples); // Prints SyntaxError: Identifier 'numOfApples' has already been declared
____________________________

let numOfApples = 50;
{ let numOfApples = 100;

console.log(numOfApples);} // Prints 100 again
}



Note: let, const and var are all hoisted. This means that their logical position of definition is the top of their enclosing scope (block or function). Variables declared using let and const cannot be read or assigned to until control has passed the point of declaration in the source code. The interim period is known as the temporal dead zone.

Context is used to refer to the value of this in some particular part of your code. Scope refers to the visibility of variables and context refers to the value of this in the same scope.

Rules to Remember:

* JavaScript has global scope and local scope.
* Variables declared and initialized outside any function become global variables.
* Variables declared and initialized inside function becomes local variables to that function.
* Variables declared without var keyword inside any function becomes global variables automatically.
* Global variables can be accessed and modified anywhere in the program.
* Local variables cannot be accessed outside the function declaration.
* Global variable and local variable can have same name without affecting each other.
* JavaScript does not allow block level scope inside { } brackets.

With these rules in mind, it gives you the tools to become a successful developer. Explicitly defining the variable as a ‘const’ or ‘let’ seems to be the best practice to clean the code legible for other developers, helping them to better understand your intentions in the program. Hopefully this article has provided you with the entire scope of ‘scope’. 
The content of your blog post goes here.
