# Notes and review for LS_170 course

Lesson 1 notes in notion.

Khan video series on the Internet.
https://www.khanacademy.org/partner-content/code-org/internet-works/v/the-internet-packet-routers-and-reliability

Lesson 2 notes in notion.

HTTP LS book: https://launchschool.com/books/http/read/introduction

Lesson 3 notes in notion, The application layer, HTTP and the web, HTTP book, background and diagrams, URLs

##### Practice Problems : URL Components

Question 1:

https://amazon.com/Double-Stainless-Commercial-Refrigerator/B60HON32?ie=UTF8&qid=142952676&sr=93&keywords=commercial+fridge

Identify the host: amazon.com
Identify the names of the query parameters: ie, qid, sr, keywords
Identify the values of the query paramters: UTF8, 142952676, 93, comercial+fridge
Identify the scheme: https
Identify the path: /double-stainless-commerical-refridgerator/b60h0n32
Identify the port: This URL does not contain a port. Most software will use port 443 by default when working with this URL due to it having a scheme of https, but that information is not contained within the URL.

Question 2:

Add the port 3000 to the following url:
http://amazon.com/products/B60HON32?qid=142952676&sr=93

http://amazon.com:3000/products/B60HON32?qid=142952676&sr=93

Question 3:
Given the following URL:
http://localhost:4567/todos/15

Identify teh query parameters: None
Identify the scheme: http
Identify the path: /todos/15
Identify the host: localhost
Identify the port: :4567

Question 4:
What are two different ways to encode a space in a query parameter?
1) +
2) %20

Question 5:
What character indicates the beginning of a URL's query parameter?
?

Question 6:
What character is used between the name and value of a query parameter?
=

Question 7:
What character is used between multiple query parameters?
&

##### The Request Response Cycles : Practice Problems

Question1:
What are the requried components of an HTTP Request? What are the additional option components?

Required: Method, Path
Optional: Parameters, all other headers, and message body are optional.

The HTTP method and the path are required, and form part of what is known as the start-line or request-line. As of HTTP 1.0, the HTTP version also forms part of the request-line. The Host header is a required component since HTTP 1.1. Parameters, all other headers, and message body are optional.

Technically speaking the 'path' portion of the request-line is known as the 'request-URI', and incorporates the actual path to the resource and the optional parameters if present. In practice, most people simply refer to this part of the request-line as the 'path'.

Question 2:
What are the required components of an HTTP response? What are the additional optional components?

Required: A status line with a status code is required.
Optional: Headers and body are optional.

Question 3:
What determines whether a request should use a `GET` or `POST` as its HTTP method?

GET requests should only retrieve content from the server. They can generally be thought of as "read only" operations, however, there are some subtle exceptions to this rule. For example, consider a webpage that tracks how many times it is viewed. GET is still appropriate since the main content of the page doesn't change.

POST requests involve changing values that are stored on the server. Most HTML forms that submit their values to the server will use POST. Search forms are a noticeable exception to this rule: they often use GET since they are not changing any data on the server, only viewing it.