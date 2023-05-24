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

The internet at its most basic form can be thought of as a network of networks. It's a distributed packet-switched network. It can be thought of as the infrastructure that enables inter-network communication, both in terms of the physical network and the lower-level protocols that control it use.

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
A socket is the combination of IP address and port number that provide a communication end-point. This is sometimes called a network socket. At an implementation level it can refer to a socket object that is used to create connections between applications.

-Have an understanding of how DNS works

The domain name system is a distributed database which maps a domain name such as www.google.com to an IP address. When we enter a domain name into a client browser, the request is passed to DNS server and the DNS returns the IP address of that server.

DNS resolves domain names to IP addresses.

Sequence of events:
Enter domain into web browser, if the web browser or OS can't resolve the domain.
Sends query to next level (recursive name server (RNS)) ISP level checks own cache memory if it cant...
Root server is at the top level of a DNS hierarchy ( 13 ), manage the request for top level domains.
Request is then sent to the appropriate top level domain server
Will then contact authoritative name servers that contain the list of domain names and IP addresses.
Once IP address is retrieved, its sent back to the RNS and your own computer.

-Understand the client-server model of web interactions, and the role of HTTP as a protocol within that model



TCP & UDP
-Have a clear understanding of the TCP and UDP protocols, their similarities and differences

Transmission control protocol (TCP) and UDP (user datagram protocol) and both protocols at the transport layer. TCP is a connection oriented protocol while UDP is a connectionless oriented protocol.

One of the key characteristics of TCP is the fact that it provides reliable data transfer. TCP provides; data integrity, de-duplication, in-order deliver, and retransmission of lost data for the application layer.

Reliability is the corner stone of TCP, but this reliability does come at the cost of performance. TCP provides data encapsulation and multiplexing through the use of TCP segments. With TCP, there is an entire round-trip of latency before any application data can be exchanged.

TCP implements flow-control (done via the WIDNOW field of the TCP header) and congestion avoidance (by using data loss feedback).

Disadvantages of TCP:
TCP has overhead latency due to the three way handshake used to establish a TCPm connection.
Another potential issue with TCP is head-of-line block (HOL). This can occur due to TCPs in order delivery of segments. If one of the segments that goes missing comes early in a sequence the segments that come after it in sequence can't be processed and will need to be buffered until retransmission has occurred.
Advantages of TCP:
Provides for a reliable transportation of data.

UDP on the other hand does not provide for any of the following; message delivery, message delivery order, built in congestion avoidance or flow control, connection state tracking. UDP PDU's are known as Datagram and is made up of four parts: Source port, destination port, length, and checksum. The checksum port is even optional depending on if were using IPv4 or IPv6 at the network layer. The case for UDP is it's speed and flexibility. The UDP protocol can be great for something like voice or video calling, where the occasional piece of dropped data leading to a sketchy glitchy call might not matter in relation to the trade off of speed.

Disadvantages of UDP:
Unreliable protocol due to the lack of reliability, no in order delivery, and no congestion avoidance or flow control.
Advantages of UDP:
Speed and flexibility

-Have a broad understanding of the three-way handshake and its purpose
TCP establishes a connection via what's known as a Three-way Handshake and is where the SYN and ACK flags come into play.

The three-way handshake process looks like:
1) Sender sends a SYN message
2) receiver receives SYN segment, responds with SYN ACK segment
3) sender receives SYN ACK segment, responds with ACK segment. Once ACK segment is sent, sender can immediately begin sending application data.
Receiver receives ACK segment and connection is now established.

-Have a broad understanding of flow control and congestion avoidance

TCP implements Flow control to prevent the sender from overwhelming the receiver with too much data at once. TCP implements this by tell the other side of the connection how much data it is willing to accept via the WINDOW field in the TCP header. The number can change throughout the connection, as data loads will change.

TCP implements congestion avoidance by listening to the data loss feedback. If lots of messages are requiring retransmission, TCP takes this as a sign the network is congested and reduces the size of the transmission window.

-(SD) Multiplexing and demultiplexing
Multiplexing and demultiplexing provides the ability to transmit multiple signals over a single channel.

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
They have no corresponding character within the standard aSCII character set.
The use of the character is unsafe since it may be misinterpreted or modified by some systems.
The character is reserved for special use within the URL scheme (ie: / ? : @ and &)

HTTP and the Request/Response Cycle
-Be able to explain what HTTP requests and responses are, and identify the components of each
-Be able to describe the HTTP request/response cycle
-Be able to explain what status codes are, and provide examples of different status code types
-Understand what is meant by 'state' in the context of the web, and be able to explain some techniques that are used to simulate state
-Explain the difference between GET and POST, and know when to choose each

Security
-Have an understanding of various security risks that can affect HTTP, and be able to outline measures that can be used to mitigate against these risks

What if someone steals my browser’s session id? What if i’m accessing a random website, can they peek into my Reddit or Facebook cookie where my session id information is stored?

Secure HTTP or HTTPS is used to combat this. With HTTPS every request/response cycle is encrypted before being transported on the network.

Same-Origin policy permits unrestricted interaction between resources originating from the same origin, but restricts certain interactions between resources originating from different origins.

Session Hijacking One popular way of solving session hijacking is by resetting sessions. With authentication system, this means a successful login must render an old session id invalid and create a new one. Most websites implement this by ensuring the user re-authenticates when entering any sensitive area, such as charging a credit card. Another useful solution is setting an expiration time on sessions. Finally, another approach is to use HTTP across the entire app to minimize the chance that an attacker can get to the session id.

Cross-Site Scripting (XSS) is a type fo attack that happens when you allow users to input HTML or JAvaScript that ends up being displayed by the site directly. For example, in a form that allows users to add comments. One way to prevent this attack is to sanitize user input, or escape all user input data when displaying it.

-Be aware of the different services that TLS can provide, and have a broad understanding of each of those services

############# Practice Questions ############

1. **What is a network?**
At the most basic level, a network is two devices connected in such a way that they can communicate or exchange data. A Network can rely on switches to bridge different devices.

2. **What is the Internet?**
We can imagine te internet as a vast number of these networks connected together, a network of networks.

3. **Is the Internet the same thing as a network?** 
No, as soon as we required inter-network communication we require the inclusion of a router. Routers enable inter-network comunicaiton.

4. **What is WEB (world wide web)**
The WEB is service that can be accessed via the internet. In simple terms, the WEB is a varst infomration sysmte comprised of resources which are navigable by means of a URL.

5. **What is the difference between network, Internet, and WEB?**
A network is a single network of connected devices, the internet is a network of interconnected networks, the WEB is service that can be accessed via the internet. In simple terms, the WEB is a varst infomration sysmte comprised of resources which are navigable by means of a URL.

6. **What are LAN and WLAN?**
LAN is Local Area Network, WLAN is Wireless Local Area Network.

7. **What is a protocol?**
In simple terms, we can think of a protocol as a system of rules. In relation to computer networks, a protocol is a set of rules that govern the exchange or transmission of data.

Protocols act as a system of rules for network communication.

8. **What is the role of protocols?** 
The role of a protocol is to govern the exchange or transmission of data.

9. **Why there are many different types of protocols?**
Different protocols were developed to address different aspects of network communication.
Different protocols were developed to address the same aspect of network communication but differently for a specific use case.

10. **What does it mean that a protocol is stateless?**
A stateless protocol refers to a protocol that does not retain any information about a previous request or response.

11. **Explain briefly what are OCI and TCP/IP models? What is the purpose of having models like that?** 
TCP/IP and OCP models are models of the layered system of network communications. The use of having these models is breaking down and modularizing the transmission of data for each step in the system.

The TCP/IP model divides it's layers in terms of the scope of communication within each layer, while the OSI model divides the layers in terms of the functions that each layer provides. These models are usuful for gainign a broad-bursh view of how a system works as a whole, and for modularziign different levels of responsibility within that system.

12. **What is PDU? What is its role?**
A PDU (protocol data Unit) is an amout or block of data transferred over a network. Different protocols or protocol layers refer to PRUs by different names.
Link/Data Link layer = Frame
Internet/Network layer= Packet
Transprot Layer = TCP segement, or UDP datagram.

13. **What is Data Payload?** 
The data payload portion of a PDU is simply the the data that we want to transport over the network.

14. **What is the relationship between PDU and Data Payload?** 
The entire PDU at one layer is set as the payload for the PDU at the layer below. For example, the payload for a TCP segement transport layer is the HTTP request at the application layer.

15. **Explain How lower-level protocols work in general?**
Protocols at one layer don't need to know anything about how a protocol at another layer is implemented in order for those protocols to interact. It can independently complete its specific communication task without information from other layers.

It creates a system wherby a lower layer effectives provides a 'service' to the layer above it.

16. **What is encapsulation in the context of networking?**
Encapsulation in the context of networking is essentially hiding data from one layer by encapsulating it within a data unit of the layer below.

17. **Why do we need encapsulation?** 
Encapsulation is useful as it allows the different layers to work completely independently of each other, allowing each protocol at each layer to do it's job without context from any other layer.

This seperation of layers provides a certain level of abstraction and allows us to use different protocols at a certain layer without having to worry about the layers below.

18. **What are the characteristics of a physical network?** 
The two main characteristics of a physical network are latency and bandwidth.

19. **How can we as developers deals with the limitations of physical network?**
There's really not much we can do as developpers about the limitations of the physical network. Our influence is limtied to the implementation of the application in terms of how we use the higher-level protocols.

20. **What is Latency?**
Latency is the amout of time it takes for some data to get from one point in a network to another point in a network.

21. **What is** **Bandwidth?**
Bandwidth is the amount of data that can be sent in a particular unit of time(typically a second).

22. **What are** **Network 'Hops'?**
Network hops are the number of journeys between nodes the data makes on it's journey from start point to end point. Nodes can be though of as routers that process data and forward it to the next node on the path.

23. **What is the relationship between network 'Hops' and latency?** 
Latency is the combination of time it takes for all of the hops to occur.

24. **What is a switch and what is it used for?**
25. **What is a hub and what is it used for?**
26. **What is a modem and what it is used for?**
27. **What is a router and what is it used for?**
28. **What is the difference between a switch, hub, modem, and router?**

29. **How does the Internet works?**
30. **What is a MAC address and what is its role in network communication?** 
A MAC address is a number of six two digit hexadecimal numbers. ie `00:40:96:9d:68:0a`.
Every network-enabled device is assigned a MAC Address when it is manufactured. This address is sometimes referred to as the physical address or burned in address.

31. **Give an overview of the Link/Data Layer**
We can think fo what happens at this layer as an interface between the workings of the physical network and the more logical layers above. This layer is most concerned with the identification of devices on the physical network and moving data over the phyiscal network between the devices that comprise it.

The most commonly used protocol at the link/Data link layer is the Ethernet protocol.

32. **What is included in an Ethernet frame?**
An Ethernet frame includes:
Source and destiniation MAC addresses
Length
DSAP, SSAP, control
Data payload
frame check sequence

33. **Give an overview of the Internet/Network Layer and it's role.**
34. **What is IP?**
35. **What is IP address?** 
36. **What are the components of IP addresses?** 
37. **What is a packet in computer networking?**
38. **Why do we need both MAC addresses and IP addresses?** 
39. **What is DNS and how does it work?**
40. **How do port numbers and IP addresses work together?**
41. **What is a checksum and what is it used for? How is it used?**
42. **Give an overview of the Transport Layer.** 
43. **What are the fundamental elements of reliable protocol?**
44. **What is pipe-lining protocols? What are the benefits of it?**
45. **What is a network port?**
46. **What is a port number?**
47. **What is a network socket?**
48. **Is TCP connectionless? Why?**
49. **How do sockets on the implementation level relate to the idea of protocols being connectionless or connection-oriented?** 
50. **What are sockets on implementation and on a theoretical level?** 
51. **What does it mean that the protocol is connection-oriented?**
52. **What is a three-way handshake? What is it used for?**
53. **What are the advantages and disadvantages of a Three-way handshake?** 
54. **What are multiplexing and demultiplexing?**
55. **How does TCP facilitate efficient data transfer?**
56. **What is flow control? How does it work and why do we need it?**
57. **How TCP prevents from receiver's buffer to get overloaded with data?**
58. **What is congestion avoidance?**
59. **What is network congestion?**
60. **How do transport layer protocols enable communication between processes?**
61. **Compare UDP and TCP. What are similarities, what are differences? What are pros and cons of using each one?** 
62. **What does it mean that network reliability is engineered?**
63. **Give an overview of the Application Layer.** 
64. **What is HTML?**
65. **What is a URL and what components does it have?**
66. **What is a Query string? What it is used for?**
67. **What URL encoding is and when it might be used for?**
68. **Which characters have to be encoded in the URL? Why?**
69. **What is www in the URL?** 
70. **What is URI?**
71. **What is the difference between scheme and protocol in URL?**
72. **What is HTTP?**
73. **What is the role of HTTP?**
74. **Explain the client-server model of web interactions, and the role of HTTP as a protocol within that model**
75. **What are HTTP requests and responses? What are the components of each?**
76. **Describe the HTTP request/response cycle.**
77. **What is a** s**tate in the context of the 'web'?**
78. **What is** s**tatelessness?**
79. **What is a stateful Web Application?**
80. **How can we mimic a stateful application?**
81. **What is the difference between stateful and stateless applications?**
82. **What does it mean that HTTP is a 'stateless protocol?** 
83. **Why HTTP makes it difficult to build a stateful application?**
84. **How the idea that HTTP is a stateless protocol makes the web difficult to secure?** 
85. **What is a `GET` request and how does it work?** 
86. **How is `GET` request initiated?**
87. **What is the HTTP response body and what do we use it for?**
88. **What are the obligatory components of HTTP requests?** 
89. **What are the obligatory components of HTTP response?**
90. **Which HTTP method would you use to send sensitive information to a server? Why?**
91. **Compare `GET` and `POST` methods.**
92. **Describe how would you send a `GET` request to a server and what would happen at each stage.**
93. **Describe how would you send `POST` requests to a server and what is happening at each stage.**
94. **What is a status code? What are some of the status codes types? What is the purpose of status codes?** 
95. **Imagine you are using an HTTP tool and you received a status code `302`. What does this status code mean and what happens if you receive a status code like that?** 
96. **How do modern web applications 'remember' state for each client?**
97. **What role does AJAX play in displaying dynamic content in web applications?**
98. **Describe some of the security threats and what can be done to minimize them?**
99. **What is the Same Origin Policy? How it is used to mitigate certain security threats?**  
100. **What determines whether a request should use `GET` or `POST` as its HTTP method?**
101. **What is the relationship between a scheme and a protocol in the context of a URL?**
102. **In what ways can we pass information to the application server via the URL?**
103. **How insecure HTTP message transfer looks like?**
104. **What services does HTTP provide and what are the particular problems each of them aims to address?**
105. **What is TLS Handshake?**
106. **What is symmetric key encryption? What is it used for?**
107. **What is asymmetric key encryption? What is it used for?**
108. **Describe SSL/TLS encryption process.**
109. **Describe the pros and cons of TLS Handshake**
110. **Why do we need digital TLS/SSL certificates?** 
111. **What is it CA hierarchy and what is its role in providing secure message transfer?**
112. **What is Cipher Suites and what do we need it for?**
113. **How does TLS add a security layer to HTTP?**
114. **Compare HTTP and HTTPS.**
115. **Does HTTPS use other protocols?** 
116. **How do you know a website uses HTTPS?**
117. **Give examples of some protocols that would be used when a user interacts with a banking website. What would be the role of those protocols?** 
118. **What is server-side infrastructure? What are its basic components?**
119. **What is a server? What is its role?** 
120. **What are optimizations that developers can do in order to improve performance and minimize latency?**