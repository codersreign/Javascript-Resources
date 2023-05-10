# PROMISES IN JAVASCRIPT

# Introduction:

In JavaScript, Promises are a way to handle asynchronous operations. It is a design pattern that allows you to write asynchronous code in a synchronous style. Promises have become an essential part of modern JavaScript, and it's important for any JavaScript developer to understand how they work.

In this tutorial, we'll cover everything you need to know about Promises in JavaScript, including what they are, how they work, and how to use them.

## What is a Promise?

A Promise is an object that represents the eventual completion or failure of an asynchronous operation and its resulting value. It allows you to handle asynchronous operations in a more elegant and concise way than using callbacks.

*Promises have three states:*

**Pending:** The initial state, when a Promise is created.

**Fulfilled:** The state when a Promise is resolved successfully with a result value.

**Rejected:** The state when a Promise is rejected with a reason for the failure.


## Creating a Promise:

To create a Promise, you can use the Promise constructor. The Promise constructor takes a function called the "executor" function as its argument. The executor function takes two parameters: resolve and reject.

*Here's an example of creating a Promise:*

```
const myPromise = new Promise((resolve, reject) => {
  // Async operation
  const result = 42;
  
  if (result) {
    resolve(result);
  } else {
    reject("Error");
  }
});
```

In the example above, we've created a Promise that resolves with the value 42 if the async operation is successful and rejects with the string "Error" if the async operation fails.

## Using a Promise:

Once you've created a Promise, you can use the then and catch methods to handle the resolved value or the rejected reason, respectively.

The then method takes a callback function that will be called with the resolved value when the Promise is fulfilled. The catch method takes a callback function that will be called with the rejected reason when the Promise is rejected.

*Here's an example of using a Promise:*

```
myPromise
  .then((result) => {
    console.log(result); // 42
  })
  .catch((error) => {
    console.log(error); // Error
  });
```

In the example above, we're using the then method to log the resolved value and the catch method to log the rejected reason.

## Chaining Promises:

Promises can also be chained together using the then method. This allows you to perform multiple async operations in sequence.

*Here's an example of chaining Promises:*

```
const myPromise1 = new Promise((resolve) => {
  setTimeout(() => {
    resolve(10);
  }, 1000);
});

const myPromise2 = (result) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(result * 2);
    }, 1000);
  });
};

myPromise1
  .then(myPromise2)
  .then((result) => {
    console.log(result); // 20
  });
```

In the example above, we're creating two Promises. The first Promise resolves with the value 10 after a delay of 1 second. The second Promise takes the resolved value from the first Promise and multiplies it by 2 before resolving with the result.

We're then chaining the two Promises together using the then method. The result of the first Promise is passed to the second Promise, and the result of the second Promise is logged to the console.

## Handling Promises by Consumer

When using Promises, the consumer of the Promise (i.e., the code that calls the function that returns a Promise) can handle the Promise in several ways.

**Using then() and catch() methods:** The consumer can use the then() method to handle the Promise when it is fulfilled and the catch() method to handle the Promise when it is rejected.

*For example:*

```
somePromiseFunction()
  .then((result) => {
    console.log('Promise fulfilled with result:', result);
  })
  .catch((error) => {
    console.log('Promise rejected with error:', error);
  });
```
In this example, somePromiseFunction() returns a Promise that can either be fulfilled with a result or rejected with an error. The then() method is used to handle the fulfilled Promise, and the catch() method is used to handle the rejected Promise.

**Using async/await syntax:** The consumer can use async/await syntax to handle Promises in a more synchronous-looking way.

*For example:*

```
async function someFunction() {
  try {
    const result = await somePromiseFunction();
    console.log('Promise fulfilled with result:', result);
  } catch (error) {
    console.log('Promise rejected with error:', error);
  }
}
```

In this example, someFunction() is an asynchronous function that calls somePromiseFunction() and waits for it to be fulfilled or rejected using the await keyword. If the Promise is fulfilled, the result is logged to the console. If the Promise is rejected, the error is caught in the catch block.

**Using Promise.all():** The consumer can use Promise.all() to wait for multiple Promises to be fulfilled.

*For example:*

```
Promise.all([somePromiseFunction1(), somePromiseFunction2(), somePromiseFunction3()])
  .then((results) => {
    console.log('All Promises fulfilled with results:', results);
  })
  .catch((error) => {
    console.log('At least one Promise rejected with error:', error);
  });
```
In this example, Promise.all() takes an array of Promises as input and waits for all of them to be fulfilled. If all Promises are fulfilled, an array of results is logged to the console. If any of the Promises are rejected, the error is caught in the catch block.

These are some of the ways that a consumer can handle Promises in JavaScript. The choice of method depends on the specific use case and the preference of the developer.

## The .finally() Promise Handler

The .finally() method is a Promise handler that is called regardless of whether a Promise is fulfilled or rejected. It allows the developer to execute some code after the Promise is settled (i.e., either fulfilled or rejected).

The .finally() method takes a single function as its argument. This function is called after the Promise is settled and receives no arguments.

*For example:*

```
somePromiseFunction()
  .then((result) => {
    console.log('Promise fulfilled with result:', result);
  })
  .catch((error) => {
    console.log('Promise rejected with error:', error);
  })
  .finally(() => {
    console.log('This code is executed regardless of whether the Promise was fulfilled or rejected.');
  });
```

In this example, the .finally() method is used to log a message to the console after the Promise is settled, indicating that the code inside the .finally() block will be executed regardless of whether the Promise was fulfilled or rejected.

The .finally() method is useful for cleaning up resources, such as closing a database connection or releasing a lock, that were opened or acquired during the execution of the Promise. This method can also be used to perform some final operations that are common to both fulfilled and rejected Promises.

It's important to note that the value returned from the .finally() method is ignored. Therefore, the .finally() method is not recommended for performing side-effects that depend on the value of the Promise. Instead, use the .then() or .catch() methods to handle the fulfillment or rejection of the Promise respectively.


## Conclusion

Promises are an essential part of modern JavaScript, and they allow you to handle asynchronous operations in a more elegant and concise way than using callbacks. They have three states: Pending, Fulfilled, and Rejected, and they can be created using the Promise constructor. Promises can be used with the then and catch methods to handle the resolved value or the rejected reason, respectively. Promises can also be chained together using the then method, allowing you to perform multiple async operations in sequence.

It's important to note that Promises are not a replacement for callbacks, but rather a more modern and convenient way to handle asynchronous operations. It's also important to handle errors properly when using Promises, as unhandled errors can cause unexpected behavior in your code.

In addition to the Promise constructor, there are also several built-in methods that return Promises, such as fetch and setTimeout. These methods can be used with Promises to perform common asynchronous tasks.

Overall, Promises are a powerful tool for handling asynchronous operations in JavaScript, and they're worth taking the time to learn and understand. By mastering Promises, you'll be able to write more elegant and maintainable asynchronous code in your JavaScript applications.