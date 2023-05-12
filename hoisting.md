# Hoisting

## Introduction

In JavaScript, hoisting is a behavior that allows the declaration of variables and functions to be lifted to the top of their respective scopes during the execution of the code. This means that you can use variables or functions before they are actually declared in your code. Understanding how hoisting works is crucial to writing effective and efficient JavaScript code. In this tutorial, we will cover the basics of hoisting and explain how it works in JavaScript.

## Variables Hoisting

When a variable is declared using the var keyword, it is automatically hoisted to the top of its respective scope. This means that you can use the variable before it is actually declared in the code. However, the variable will have an initial value of undefined until it is assigned a value.

*For example:*

```
console.log(x); // undefined
var x = 10;
```
In the code above, the variable `x` is declared using the `var` keyword, but it is used before it is actually declared. When the code is executed, `x` will be hoisted to the top of the scope and have an initial value of `undefined`. The `console.log` statement will output `undefined`.

## Function Hoisting

When a function is declared using either function declaration or function expression, the entire function is hoisted to the top of its respective scope. This means that you can use the function before it is actually declared in the code.

## Function Declaration

```
hello(); // "Hello, World!"
function hello() {
  console.log("Hello, World!");
}
```

In the code above, the function `hello` is declared using function declaration syntax. When the code is executed, the entire function is hoisted to the top of the scope and can be called before it is actually declared. The `hello()` function call will output `"Hello, World!"`.

## Function Expression

```
hello(); // TypeError: hello is not a function
var hello = function() {
  console.log("Hello, World!");
}
```

In the code above, the function `hello` is declared using function expression syntax. When the code is executed, the variable `hello` is hoisted to the top of the scope and assigned a value of `undefined`. The `hello()` function call will throw a `TypeError` because `hello` is not yet a function.

## Hoisting in Block Scope

ES6 introduced the `let` and `const` keywords for declaring variables in block scope. Unlike variables declared with `var`, variables declared with `let` and `const` are not hoisted to the top of their respective scope. This means that you cannot use these variables before they are declared in the code.

*For example:*

```
console.log(x); // ReferenceError: x is not defined
let x = 10;
```

In the code above, the variable `x` is declared using the `let` keyword. When the code is executed, `x` is not hoisted to the top of the scope, and the `console.log` statement will throw a `ReferenceError`.

## Conclusion

In this tutorial, we have covered the basics of hoisting in JavaScript. We have learned that variables and functions declared with `var` and function declaration syntax are hoisted to the top of their respective scopes, and can be used before they are actually declared. We have also learned that variables declared with `let` and `const` are not hoisted to the top of their respective scopes, and cannot be used before they are declared in the code. Understanding how `hoisting` works in JavaScript is essential to writing efficient and effective code.