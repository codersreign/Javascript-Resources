# Debouncing

Debouncing is a technique used to prevent an action from being triggered multiple times in a short period. For instance, if a user repeatedly clicks a button, it could cause multiple requests to be sent to the server or trigger multiple events. Debouncing ensures that only one action is executed, even if the event is triggered multiple times.

In JavaScript, debouncing can be implemented in several ways. One way is to use the setTimeout() function to delay the execution of the function. Another way is to use the requestAnimationFrame() method, which schedules the function to run during the next animation frame.

*Here's an example of how to implement debouncing using the setTimeout() method:*

```
function debounce(func, delay) {
  let timeoutId;
  return function() {
    const context = this;
    const args = arguments;
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => func.apply(context, args), delay);
  };
}
```

In this example, the debounce function takes two arguments: func is the function that needs to be debounced, and delay is the amount of time to wait before executing the function. The timeoutId variable is used to store the ID of the timeout that is set using setTimeout().

The return statement returns a new function that wraps the original function func. When the new function is called, it clears any previously set timeout using clearTimeout(). Then, it sets a new timeout using setTimeout() with the specified delay. The new timeout calls the original function func with the apply() method, passing in the context and args arguments.

*Here's an example of how to use the debounce function to debounce a button click event:*

```
const button = document.querySelector('button');
function handleClick() {
  console.log('Button clicked');
}
const debouncedClick = debounce(handleClick, 1000);
button.addEventListener('click', debouncedClick);
```

In this example, the handleClick function is debounced using the debounce function with a delay of 1000 milliseconds. The debounced function is then added as an event listener for the click event on the button element.

# Enhanced Debouncing

Now, let's talk about enhanced debouncing. Enhanced debouncing is an improvement over the basic debouncing technique that ensures that the function is executed at least once, even if the delay time has not passed.

*Here's an example of how to implement enhanced debouncing using the setTimeout() method:*

```
function enhancedDebounce(func, delay, immediate) {
  let timeoutId;
  return function() {
    const context = this;
    const args = arguments;
    const callNow = immediate && !timeoutId;
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => {
      timeoutId = null;
      if (!immediate) func.apply(context, args);
    }, delay);
    if (callNow) func.apply(context, args);
  };
}
```
In this example, the enhancedDebounce function takes three arguments: func is the function that needs to be debounced, delay is the amount of time to wait before executing the function, and immediate is a boolean value that determines whether the function should be executed immediately or after the delay time has passed.

The timeoutId variable is used to store the ID of the timeout that is set using setTimeout().

The return statement returns a new function that wraps the original function func. When the new function is called, it clears any previously set timeout using clearTimeout().

The callNow variable is used to determine whether the function should be executed immediately. If immediate is true and timeoutId is not set (meaning the delay time has not passed yet), then callNow is set to true.

The new function sets a new timeout using setTimeout() with the specified delay. The new timeout calls the original function func with the apply() method, passing in the context and args arguments.

If immediate is true and timeoutId is not set, then the original function func is called immediately with the apply() method, passing in the context and args arguments.

*Here's an example of how to use the enhancedDebounce function to debounce a button click event:*

```
const button = document.querySelector('button');
function handleClick() {
  console.log('Button clicked');
}
const enhancedDebouncedClick = enhancedDebounce(handleClick, 1000, true);
button.addEventListener('click', enhancedDebouncedClick);
```

In this example, the handleClick function is enhanced-debounced using the enhancedDebounce function with a delay of 1000 milliseconds and immediate set to true. The enhanced debounced function is then added as an event listener for the click event on the button element.

In summary, debouncing and enhanced debouncing are techniques used to prevent an action from being triggered multiple times in a short period. Debouncing delays the execution of the function until a specified amount of time has passed, while enhanced debouncing ensures that the function is executed at least once, even if the delay time has not passed. Both techniques can be implemented using the setTimeout() method or the requestAnimationFrame() method.