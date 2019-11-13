# Http Protocol
__Hypertext Transfer Protocol (HTTP)__ is an application-layer protocol for transmitting hypermedia documents, such as HTML. 
It was designed for communication between web browsers and web servers,
 but it can also be used for other purposes. 
 HTTP follows a classical client-server model, with a client opening a connection to make a request, 
 then waiting until it receives a response. HTTP is a stateless protocol,
  meaning that the server does not keep any data (state) between two requests. 

Resources: 
* [Learn JS](https://javascript.info/network)
* [HTTP(mdn)](https://developer.mozilla.org/en-US/docs/Web/HTTP)
* [Headers(mdn)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
* [Headers](https://www.twilio.com/blog/a-http-headers-for-the-responsible-developer)
* [CORS(mdn)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
* [HTTP response status codes(mdn)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
* [How does an Internet work](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)

Сontents:
* [Request methods](https://github.com/purumvisum/interview/blob/master/theoretical-basis/http.md#request-methods )
* [Headers](https://github.com/purumvisum/interview/blob/master/theoretical-basis/http.md#headers)
* [CORS](https://github.com/purumvisum/interview/blob/master/theoretical-basis/http.md#CORS)
* [HTTP Responce Status codes](https://github.com/purumvisum/interview/blob/master/theoretical-basis/http.md#http-response-status-codes)

## Request methods 
* *GET*
    * GET requests remain in the browser history
    * GET requests can be bookmarked
    * GET requests should never be used when dealing with sensitive data
    * GET requests have length restrictions
    * GET requests are only used to request data (not modify)
    
* *HEAD*

    The HEAD method asks for a response identical to that of a GET request, 
    but without the response body.
    HEAD requests are useful for checking what a GET request will return before actually making 
    a GET request - like before downloading a large file or response body.
* *POST* 

    The data sent to the server with POST is stored in the request body of the HTTP request:
    The POST method is used to submit an entity to the specified resource, 
    often causing a change in state or side effects on the server.
    
    * POST requests are never cached
    * POST requests do not remain in the browser history
    * POST requests cannot be bookmarked
    * POST requests have no restrictions on data length
* *PUT*

    PUT is used to send data to a server to create/update a resource.
    Calling the same PUT request multiple times will always produce the same result. In contrast, 
    calling a POST request repeatedly have side effects of creating the same resource multiple times.
* *DELETE*

    The DELETE method deletes the specified resource.
* *CONNECT*

    The CONNECT method establishes a tunnel to the server identified by the target resource.
* *OPTIONS*

    The OPTIONS method is used to describe the communication options for the target resource.
* *TRACE*

    The TRACE method performs a message loop-back test along the path to the target resource.
* *PATCH*

    The PATCH method is used to apply partial modifications to a resource.
    
    
## Headers

* *General headers*
     apply to both requests and responses, but with no relation to the data transmitted in the body.
* *Request headers*
     contain more information about the resource to be fetched, or about the client requesting the resource.
* *Response headers*
     hold additional information about the response, like its location or about the server providing it.
* *Entity headers*
     contain information about the body of the resource, like its content length or MIME type.
     
   
```
Cache-Control: max-age=31536000, public, immutable
```
By setting proper Cache-Control data transfer is saved, and files can be used from 
the browser cache for a certain amount of seconds (max-age). Browsers should revalidate 
cached resources after the time span is over.

Immutable – never request a resource twic

---

```
Accept-Encoding: gzip, deflate, br
``` 
In request.
This header tells the server what compression algorithms it understands. 

---
```
Content-Encoding: gzip
```
In response
The Content-Encoding entity header is used to compress the media-type. 

---
```
Accept: image/webp, image/apng, image/*,*/*;q=0.8
```

---
``` 
Authorization: Basic YWxhZGRpbjpvcGVuc2VzYW1l (<type> <credentials>)
``` 
The HTTP Authorization request header contains the credentials to authenticate a user agent with a server

---
``` 
Access-Control-Allow-Origin: *
Access-Control-Allow-Origin: <origin>
Access-Control-Allow-Origin: null
``` 
The Access-Control-Allow-Origin response header indicates whether the response can be shared with requesting code from the given origin.

## CORS
__*Cross-Origin Resource Sharing (CORS)*__  is a mechanism that uses additional HTTP headers to tell browsers
 to give a web application running at one origin, access to selected resources from a different origin.
  A web application executes a cross-origin HTTP request when it requests a resource that has a 
  different origin (domain, protocol, or port) from its own.

An example of a cross-origin request: the front-end JavaScript code served from 
https://domain-a.com uses XMLHttpRequest to make a request for https://domain-b.com/data.json.

For security reasons, browsers restrict cross-origin HTTP requests initiated from scripts. 
For example, XMLHttpRequest and the Fetch API follow the same-origin policy. This means that a web 
application using those APIs can only request resources from the same origin the application was loaded 
from, unless the response from other origins includes the right CORS headers.

## HTTP response status codes

https://httpstatuses.com/ 

* Informational responses (100–199),
* Successful responses (200–299),
* Redirects (300–399),
* Client errors (400–499),
* Server errors (500–599).
