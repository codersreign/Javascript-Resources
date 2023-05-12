# Clousure

Closures are a powerful concept in computer programming, and they are often used in functional programming languages like JavaScript, Python, and Ruby. In this tutorial, we'll explore what closures are, how they work, and why they're useful.

## What is a Closure?

A closure is a function that has access to variables from an outer or enclosing function. In other words, a closure is a function that "closes over" or "captures" variables from its surrounding environment.

*Consider the following code:*

```
function outer() {
  var x = 10;

  function inner() {
    console.log(x);
  }

  return inner;
}

var closure = outer();
closure(); // Output: 10
```

In this example, `outer()` defines a variable `x` and a function `inner()`. `inner()` has access to the `x` variable through closure, even though `x` is defined in `outer()`. When `outer()` is called and returns `inner()`, `inner()` is able to log the value of `x` to the console.

## How Closures Work

When a function is defined, it creates a new execution context with its own set of variables. These variables are stored in memory along with the function code. When the function is called, the code is executed in the context of the current execution stack.

When a function returns, its execution context is destroyed, and any variables defined within the function are also destroyed. However, if an inner function "closes over" a variable from an outer function, that variable is kept alive in memory even after the outer function has returned.

This is because the inner function maintains a reference to the variable, and the variable is stored in memory as long as the inner function is in scope. This is how closures work - they allow inner functions to access and use variables from an outer function, even after the outer function has completed execution.

## Why Use Closures?

Closures are useful in many programming scenarios, especially in functional programming. Here are some reasons why you might use closures:

## Data privacy

One of the main benefits of closures is that they provide a way to create private variables in JavaScript. In the following example, we create a `counter` function that returns an object with two methods: `increment` and `getCount`. The `increment` method increments a private variable `count`, while the `getCount` method returns the current value of `count`.

```
function counter() {
  var count = 0;

  return {
    increment: function() {
      count++;
    },
    getCount: function() {
      return count;
    }
  };
}

var myCounter = counter();
myCounter.increment();
myCounter.increment();
console.log(myCounter.getCount()); // Output: 2
```

In this example, the `count` variable is private and cannot be accessed directly from outside the `counter()` function. However, the `increment` and `getCount` methods have access to the `count` variable through `closure`, allowing them to manipulate and retrieve its value.

## Callback functions

Closures are often used with callback functions, which are functions that are passed as arguments to other functions. In the following example, we create a forEach function that takes an array and a callback function as arguments. The forEach function iterates over the array and invokes the callback function for each element.

```
function forEach(arr, callback) {
  for (var i = 0; i < arr.length; i++) {
    callback(arr[i]);
  }
}

var arr = [1, 2, 3];
forEach(arr, function(element) {
  console.log(element);
});
```

In this example, the callback function passed to `forEach` has access to the `arr` array through `closure`, allowing it to access and manipulate the array elements.

## Memoization

Closures can also be used for memoization, which is a technique used to speed up function execution by caching the results of expensive function calls. In the following example, we create a memoize function that takes a function as an argument and returns a new function that caches the result of the original function.

```
function memoize(func) {
  var cache = {};

  return function() {
    var args = JSON.stringify(arguments);
    if (cache[args]) {
      return cache[args];
    }
    else {
      var result = func.apply(this, arguments);
      cache[args] = result;
      return result;
    }
  };
}

function fibonacci(n) {
  if (n === 0 || n === 1) {
    return n;
  }
  else {
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}

var memoizedFibonacci = memoize(fibonacci);
console.log(memoizedFibonacci(10)); // Output: 55
```

In this example, the `memoize` function creates a cache object that stores the results of function calls. The returned function checks if the arguments passed to it have been cached, and returns the cached result if they have. If not, it calls the original function, caches the result, and returns it.

## Conclusion

Closures are a powerful and versatile concept in computer programming. They allow inner functions to access and manipulate variables from outer functions, even after the outer functions have completed execution. Closures can be used for a variety of programming scenarios, including data privacy, callback functions, and memoization. By understanding closures, you can write more concise and efficient code in your programming projects.