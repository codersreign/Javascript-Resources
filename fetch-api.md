# Fetch API

## Introduction:

The Fetch API provides a simple interface for fetching resources asynchronously across the network. It is a modern replacement for XMLHttpRequest (XHR). The Fetch API can be used in both web browsers and Node.js. In this tutorial, we will cover the basics of the Fetch API, including making requests, handling responses, and error handling.

## Making a Basic Fetch Request:
The Fetch API uses the fetch() method to make requests. The fetch() method takes a URL as its parameter and returns a Promise that resolves to the response object.

```
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In the above example, we are making a GET request to the JSONPlaceholder API to get a todo item with an id of 1. We are using the then() method to parse the response body as JSON and log it to the console. We are also using the catch() method to handle any errors that may occur during the request.

## Sending Data in a Fetch Request:

The Fetch API can also be used to send data in a request. To send data in a request, we need to specify the HTTP method (POST, PUT, etc.) and the data to send in the request body.

```
const requestOptions = {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ title: 'foo', body: 'bar', userId: 1 })
};

fetch('https://jsonplaceholder.typicode.com/posts', requestOptions)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In the above example, we are sending a POST request to the JSONPlaceholder API to create a new post. We are specifying the HTTP method as POST, setting the Content-Type header to application/json, and sending a JSON object as the request body.

## Handling Responses:

The response object returned by the fetch() method contains a number of properties and methods that we can use to handle the response. The most commonly used properties and methods are:

**status:** the HTTP status code of the response

**ok:** a Boolean indicating whether the response was successful (status code in the range 200-299)

**headers:** a Headers object containing the response headers

**text():** a method that returns a Promise that resolves to the response body as text

**json():** a method that returns a Promise that resolves to the response body as JSON

```
fetch('https://jsonplaceholder.typicode.com/todos/1')
  .then(response => {
    console.log(response.status);
    console.log(response.ok);
    console.log(response.headers.get('Content-Type'));
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In the above example, we are logging the status code, ok property, and Content-Type header of the response. We are also parsing the response body as JSON and logging it to the console.

## Error Handling:

The Fetch API uses the catch() method to handle errors that occur during a request. We can use the catch() method to handle network errors, server errors, and other types of errors that may occur during a request.

```
fetch('https://jsonplaceholder.typicode.com/todos/100000')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In the above example, we are making a request to a non-existent endpoint on the JSONPlaceholder API to simulate a 404 error. We are then using the catch() method to handle the error and log it to the console.

Handling Request and Response Headers:
The Fetch API provides a Headers class that can be used to manipulate request and response headers. The Headers class provides methods for setting, getting, and deleting headers.

```
const headers = new Headers();
headers.append('Content-Type', 'application/json');

const requestOptions = {
  method: 'POST',
  headers: headers,
  body: JSON.stringify({ title: 'foo', body: 'bar', userId: 1 })
};

fetch('https://jsonplaceholder.typicode.com/posts', requestOptions)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

In the above example, we are creating a new Headers object, setting the Content-Type header to application/json, and then using it in the request options.

Using Fetch with Async/Await:
The Fetch API can also be used with async/await syntax for more concise and readable code.

```
async function getTodo() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

getTodo();
```

In the above example, we are using the async keyword to define an asynchronous function that uses await to wait for the response and data to be returned before logging it to the console.

## Conclusion:

In this tutorial, we covered the basics of the Fetch API, including making requests, sending data, handling responses, error handling, headers, and using it with async/await syntax. The Fetch API is a powerful and modern way to handle network requests in JavaScript, and it is recommended to use it over the older XMLHttpRequest (XHR) API.




