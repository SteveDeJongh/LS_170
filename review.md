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

Lesson 4 notes in notion.
Examples of bash files in /bash_basics

HTTP project in /simple_http_server

Lesson 5 notes in notion - Transport Layer Security (TLS)

Lesson 6 Notes in Notion

###### Assessement prep #####

Test, approx 22 questions, 3 hour time limit.

#### Study Guide ####

Videos series on Networks/The internet (EP 28,29,30):
https://www.youtube.com/watch?v=3QhU9jd03a0

The Internet
-Have a broad understanding of what the internet is and how it works

The internet at it's most basic form can be thought of as a network of networks. It's a distributed packet-switched network.

-Understand the characteristics of the physical network, such as latency and bandwidth

Latency is a measure of the time it takes for some data to get from one point in a network to another point a network. There are many delay factors that contribute to overall latency, these include: proprogation delay, transmission delay, processing delay, and queuing delay.
Bandwidth is the amount of data that can sent in a particular unit of time (typically a second)

-Have a basic understanding of how lower level protocols operate



-Know what an IP address is and what a port number is

The PDU for the Internet Protocol Suite is called a packet.
IP Addresses are logical in nature. This means they are not tied to a specific devies, but can be assigned as required to devices as they join the network. IPv4 address are 32 bits in lengnth and are dvided into four sections fo eight bits each. When converted from binary to decimal, it may look soemthing like `120.123.106.57`.

A port number in simple terms is an identifier for a specific process running a host. This identifier is an integer in teh range of 0-65535. The port number is added on to the network IP address to create a socket. The combination of IP address and port number information can be thought of as defining a communication end-point (`120.123.105.57:52883`). Source port and destination port numbers are included in the PDU for the transport layer.

Data from the application layer is encapsulated as the data payload in this PDU for the transport layer, which contains destination and source port numbers. This entire PDU is then encapsulated as the data payload in an IP packet on the internet layer and can be used to direct data from one host to another.

-(SD) What is a socket?
A socket is the combination of IP address and port number that provide a communication end-point. This is sometimes called a network socket. At an implementation level it can refer to a socket object that is used to create connections between applicationts.

-Have an understanding of how DNS works

The domain name system is a distributed database which maps a domain name such as www.google.com to an IP address. When we enter a domain name into a client browser, the request is passed to DNS server and the DNS returns the IP address of that server.

DNS resolves domain names to IP addresses.

Sequence of events:
Enter domain into web browser, if the web browser or OS can't resolve the domain.
Sends query to next level (recursive name server (RNS)) ISP level checks own cache memory if it cant...
Root server is at the top level of a DNS heirarchy ( 13 ), manage the request for top level domains.
Request is then sent to the appropriate top level domain server
Will then contact authoratatize name servers that contain the list of domain names and IP addresses.
Once IP address is retreived, its sent back to the RNS and your own computer.


-Understand the client-server model of web interactions, and the role of HTTP as a protocol within that model

TCP & UDP
-Have a clear understanding of the TCP and UDP protocols, their similarities and differences

Transmission control protocol (TCP) and UDP (user datagram protocol) and both protocols at the transport layer. TCP is a connection oriented protocol while UDP is a connectionless oriented protocol.

One of the key characteristics of TCP is the fact that it provides reliable data transfer. TCP provides; data integrity, de-duplication, in-order deliver, and restransmission of lost data for the application layer.

Reliability is the corner stone of TCP, but this reliability does come at the cost of performance. TCP provides data encapsulation and multiplexing through the use of TCP segments. With TCP, there is an entire round-trip of latency before any application data can be exchanged.

TCP implements flow-control (done via the WIDNOW field of the TCP header) and congestion avoidance (by using data loss feedback).

Disadvantages of TCP:
TCP has overhead latency due to the three way handshake used to establish a TCPm connection.
Another potential issue with TCP is head-of-line block (HOL). This can occur due to TCPs in order delviery of segemtns. If one of the segments that goes missing comes early in a sequence the segments that come after it in squence can't be processed and will need to be buffered until retransmission has occured.
Advantages of TCP:
Provides for a reliable transportation of data.

UDP on the otherhand does not provide for any of the following; message delivery, message delivery order, built in congestion avoidance or flow control, connection state tracking. UDP PDU's are known as Datagram and is made up of four parts: Source port, destination port, length, and checksum. The checksum port is even optional depending on if were using IPv4 or IPv6 at the network layer. The case for UDP is it's speed and flexibility. The UDP protocol can be great for something like voice or video calling, where the occasional pirce of dropped data leading to a sketchy glitchy call might not matter in relation to the trade off of speed.

Disadvantages of UDP:
Unreliable protocol due to the lack of reliability, no inorder delivery, and no congestion avoidance or flow contorl.
Advantages of UDP:
Speed and flexibility

-Have a broad understanding of the three-way handshake and its purpose
TCP establishes a connection via what's known as a Three-way Handshake and is where the SYN and ACK flags come into play.

The three-way handshake process looks like:
1) Sender sends a SYN message
2) receiver receives SYN segment, responds with SYN ACK segement
3) sender receives SYN ACK segement, responds with ACK segement. Once ACK segment is sent, sender can immediaitely begin sending application data.
Receiver receives ACK segement and connection is now established.

-Have a broad understanding of flow control and congestion avoidance

TCP implements Flow control to prevent the sender from overwhelming the receiver with too much data at once. TCP implements this by tell the other side of the connection how much data it is willing to accept via the WINDOW field in the TCP header. The number can change throughout the connection, as data loads will change.

TCP implements congestion avoidance by listening to the data loss feedback. If lots of messages are requiring retransmission, TCP takes this as a sign the network is congested and reduces the size of the transmission window.

-(SD) Multiplexing and demultiplexing
Multiplexing and demultiplexing provides the ability to trasnmit multiple signals over a single channel.

URLs
-Be able to identify the components of a URL, including query strings
URLs are made of 5 components: `http://wwww.example.com:88/home?item=book`
`http` - This the scheme and always comes before the colon and two forward slashes. It tells the client how to access the resource.
`www.example.com` - This is the host. It tell the client where the resource is hosted or located.
`:88` - This is the port number. IT is only required if you want to use a port other than the default.
`/home` - This is the path. It shows what local resource is being requested. This part of the url is optional.
`?item=book` - This is a query string, which is made up of query parameters. IT is uses to send data to the server. This part is also optional.

-Be able to construct a valid URL



-Have an understanding of what URL encoding is and when it might be used
URL Encoding is done using a `%` symbol and the UTF-8 code to include the character in the url. This is done when the character is not part of the 128-character ASCII character set, or when the character being used is a reserved or unsafe ASCII character.

Characters must be encoed if:
They have no correspdoning character within the standard aSCII character set.
The use fot he character is unsafe since it may be misinterpreted or modifed by some systems.
The character is reserverd for special use within the URL scheme (ie: / ? : @ and &)

HTTP and the Request/Response Cycle
-Be able to explain what HTTP requests and responses are, and identify the components of each
-Be able to describe the HTTP request/response cycle
-Be able to explain what status codes are, and provide examples of different status code types
-Understand what is meant by 'state' in the context of the web, and be able to explain some techniques that are used to simulate state
-Explain the difference between GET and POST, and know when to choose each

Security
-Have an understanding of various security risks that can affect HTTP, and be able to outline measures that can be used to mitigate against these risks
-Be aware of the different services that TLS can provide, and have a broad understanding of each of those services