# XHR

**XMLHttpRequest (XHR)** is a JavaScript API that allows you to send HTTP or HTTPS requests to a web server and receive responses in various formats such as JSON, XML, or plain text. It is an essential part of web development that allows you to build dynamic and interactive web pages that can communicate with web servers in real-time.

In this tutorial, we will cover the following topics related to XMLHttpRequest:

1. Creating an XHR Object

2. Sending an XHR Request

3. Handling XHR Responses

4. Handling XHR Errors

5. XHR Methods and Properties

6. Cross-Origin Resource Sharing (CORS)

7. Creating an XHR Object
   
*To use the XHR API, you first need to **create an XHR object**. You can do this by calling the XMLHttpRequest() constructor:*

```
var xhr = new XMLHttpRequest();
```

This creates a new instance of the XHR object that you can use to send HTTP or HTTPS requests.

## Sending an XHR Request

After creating an XHR object, you can use it to send a request to a web server. To do this, you need to call the open() method to specify the type of request you want to send, the URL of the web server, and any optional parameters. Then, you can call the send() method to send the request.

```
xhr.open('GET', 'https://example.com/api/data', true);
xhr.send();
```

In this example, we are sending a GET request to the URL https://example.com/api/data with the async parameter set to true. This means that the XHR request is asynchronous and will not block the main thread of the browser.

## Handling XHR Responses

Once the XHR request is sent, you need to handle the response from the web server. To do this, you can use the onload event handler to get the response data and any HTTP status codes.

```
xhr.onload = function() {
  if (xhr.status === 200) {
    console.log(xhr.responseText);
  }
};
```

In this example, we are checking if the HTTP status code is 200, which means that the request was successful. If it is, we print the response text to the console.

## Handling XHR Errors

In addition to handling successful responses, you also need to handle errors that can occur during the XHR request. To do this, you can use the onerror event handler to detect any network errors or server errors.

```
xhr.onerror = function() {
  console.log('An error occurred during the XHR request.');
};
```

In this example, we are simply printing an error message to the console if the XHR request encounters an error.

## XHR Methods and Properties

The XHR API provides several methods and properties that you can use to customize the XHR request and handle responses and errors. Some of the most commonly used methods and properties are:

- **open(method, url[, async[, user[, password]]])**
    - Opens a new XHR request with the specified HTTP method, URL, and optional parameters.
- **send([body])**
    - Sends the XHR request with an optional request body.
- **setRequestHeader(name, value)**
    - Sets an HTTP header for the XHR request.
- **getResponseHeader(name)**
    - Returns the value of an HTTP header from the XHR response.
- **getAllResponseHeaders()**
    - Returns all the HTTP headers from the XHR response as a string.
- **abort()**
    - Cancels the XHR request.
- **status**
    - Returns the HTTP status code from the XHR response.
- **statusText**
    - Returns the HTTP status text from the XHR response.
- **responseText**
    - Returns the response body as text from the previous tutorial on XHR.

## Cross-Origin Resource Sharing (CORS)

One important concept to understand when using XHR is Cross-Origin Resource Sharing (CORS). CORS is a security feature that prevents web pages from making requests to web servers that are not on the same domain as the web page. This is done to prevent malicious scripts from accessing sensitive data on other web servers.

To enable CORS on a web server, you need to set the Access-Control-Allow-Origin header to the domain of the web page that is making the XHR request. For example, if you have a web page at (https://example.com) and you want to make XHR requests to a web server at (https://api.example.com), you need to set the Access-Control-Allow-Origin header to (https://example.com).

If the web server does not set the Access-Control-Allow-Origin header correctly, the XHR request will fail with a CORS error. To handle this error, you can use the onerror event handler as described above.

## Conclusion

In this tutorial, we covered the basics of using XHR to send HTTP or HTTPS requests to a web server and receive responses in various formats such as JSON, XML, or plain text. We also discussed how to handle XHR responses and errors, use XHR methods and properties, and enable Cross-Origin Resource Sharing (CORS). XHR is a powerful tool that allows you to build dynamic and interactive web pages that can communicate with web servers in real-time.