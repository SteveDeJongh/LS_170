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
At the most basic level, a network is two devices connected in such a way that they can communicate or exchange data. A Network can rely on a hub or switches to bridge different devices or partition parts of the network, or have all devices connected on a single wire.

2. **What is the Internet?**
We can imagine te internet as a vast number of these networks connected together, a network of networks.

3. **Is the Internet the same thing as a network?** 
No, as soon as we require inter-network communication we require the inclusion of a router. Routers enable inter-network comunication, and it's the connection of different routers and networks that makes up the internet, the infrastructure allowing inter-network communication.

4. **What is WEB (world wide web)**
The WEB is service that can be accessed via the internet. In simple terms, the WEB is a vast information system comprised of resources which are navigable by means of a URL. We can think of the web as a library that is hosted on the internet, with individual webpages being the books that we can check out.

5. **What is the difference between network, Internet, and WEB?**
A network is a single network of connected devices, the internet is a network of interconnected networks, the WEB is a service that can be accessed via the internet. In simple terms, the WEB is a vast information system comprised of resources which are navigable by means of a URL.

6. **What are LAN and WLAN?**
LAN is Local Area Network, WLAN is Wireless Local Area Network. WAN is a Wide access network, and can be thought of as the networks at the core of the internet.

7. **What is a protocol?**
In simple terms, we can think of a protocol as a set of rules. In relation to computer networks, a protocol is a set of rules that govern the exchange or transmission of data.

Protocols act as a system of rules for network communication, and allows devices of all makes and models to follow a set of guidelines to in order to be able to communicate with other devices from other makes and models.

8. **What is the role of protocols?** 
The role of a protocol is to govern the exchange or transmission of data.

A Protocol is used to set the guidelines for communication and data transmission at a particular layer of a network.

9. **Why there are many different types of protocols?**
Different protocols were developed to address different aspects of network communication.
Different protocols were developed to address the same aspect of network communication but differently for a specific use case.

There's a need for so manny different protocols because of the different layers and styles of communication they need to deal with. For example, we can have mutliple different ways and rules we wish to transport data at the internet layer, and at the application layer, etc. For instance, some applications may care about missing data, while others might not be concerned with it and instead prefer a protocol that is the asbolute fastest for data transmission.

10. **What does it mean that a protocol is stateless?**
A stateless protocol refers to a protocol that does not retain any information about a previous request or response.

Stateless procotols treat each interaction between sender and receiver as a brand new request, with no recollection of past or future interactions. On each request, all the sender and receiver information needs to be transmitted. 

11. **Explain briefly what are OCI and TCP/IP models? What is the purpose of having models like that?** 
TCP/IP and OCP models are models of the layered system of network communications. The use of having these models is breaking down and modularizing the transmission of data for each step in the system.

The TCP/IP model divides it's layers in terms of the scope of communication within each layer, while the OSI model divides the layers in terms of the functions that each layer provides. These models are useful for gaining a bigger picture view of how the networking system works as a whole, and for breaking down different levels of responsibility within that system.

12. **What is PDU? What is its role?**
A PDU (protocol data Unit) is an amout or block of data transferred over a network. Different protocols or protocol layers refer to PRUs by different names.
Physical Layer = No PDU as the data is transported as bits along the physical medium.
Link/Data Link layer = Ethernet Frame
Internet/Network layer= IP Packet
Transport Layer = TCP segement, or UDP datagram.
Application Layer = HTTP Request/Response

13. **What is Data Payload?** 
The data payload portion of a PDU is simply the actual data that we want to transport over the network. The payload of one layer is tpyically the entire PDU of the layer above, this is how network communication enables encapsulation and abstracts one layer of communication from another.

14. **What is the relationship between PDU and Data Payload?** 
The entire PDU at one layer is set as the payload for the PDU at the layer below. For example, the payload for a TCP segment at transport layer is the HTTP request at the application layer, and the payload for a packet at the internet layer would be the TCP segement.

15. **Explain How lower-level protocols work in general?**
Protocols at one layer don't need to know anything about how a protocol at another layer is implemented in order for those protocols to interact. It can independently complete its specific communication task without information from other layers.

It creates a system whereby a lower layer effectively provides a 'service' to the layer above it.

16. **What is encapsulation in the context of networking?**
Encapsulation in the context of networking is essentially hiding data from one layer above by encapsulating it within a data unit of the layer below as payload.

17. **Why do we need encapsulation?** 
Encapsulation is useful as it allows the different layers to work completely independently of each other, allowing each protocol at each layer to do it's job without context from any other layer.

This seperation of layers provides a certain level of abstraction and allows us to use different protocols at a certain layer without having to worry about the layers below.

18. **What are the characteristics of a physical network?** 
The two main characteristics of a physical network are latency and bandwidth. Latency is the measure of time (in milliseconds) it takes for some chunk of data to get from a point on a network to some other point. Bandwidtch is the amount of data that can be sent in a particular chunk of time, often a second, and is measure in bits.

19. **How can we as developers deals with the limitations of physical network?**
There's really not much we can do as developpers about the limitations of the physical network. Our influence is limtied to the implementation of the application in terms of how we use the higher-level protocols.

20. **What is Latency?**
Latency is the amout of time it takes for some data to get from one point in a network to another point in a network.

21. **What is** **Bandwidth?**
Bandwidth is the amount of data that can be sent in a particular unit of time(typically a second).

22. **What are** **Network 'Hops'?**
Network hops are the number of journeys between nodes the data makes on it's journey from start point to end point. Nodes can be though of as routers that process data and forward it to the next node on the path.

Data will make many stops and come accross many intersections on it's journey from starting location to ending location. Each of these journeys between intersections can be thought of as a hop, where each intersection is a node (router) that directs the data on it's next journey to it's end destination.

23. **What is the relationship between network 'Hops' and latency?** 
Latency is the combination of time it takes for all of the hops to occur.

Latency is the total combination of all the time each individual hop takes. Latency can sometimes be reduced by improving network routing and reducing redundant hops, therefor decreasing the time spent to process and push the data back onto the network for travel.

24. **What is a switch and what is it used for?**
25. **What is a hub and what is it used for?**
26. **What is a modem and what it is used for?**
27. **What is a router and what is it used for?**
28. **What is the difference between a switch, hub, modem, and router?**
29. **How does the Internet works?**
The internet works by being a large interconnected network of devices. When we want to access a resource at a particular IP address, the request data works it's way down the various layered protocols from our application to the physical layer, makes it's various hops through routers to it's final server destination where the requested resource is stored. This then prompt the server to issue a response, which works it's way back through the networks various protocols.

30. **What is a MAC address and what is its role in network communication?** 
A MAC address is a number of six two digit hexadecimal numbers. ie `00:40:96:9d:68:0a`.
Every network-enabled device is assigned a MAC Address when it is manufactured. This address is sometimes referred to as the physical address or burned in address.

31. **Give an overview of the Link/Data Layer**
We can think fo what happens at this layer as an interface between the workings of the physical network and the more logical layers above. This layer is most concerned with the identification of devices on the physical network and moving data over the phyiscal network between the devices that comprise it.

The most commonly used protocol at the link/Data link layer is the Ethernet protocol, with uses frames as a PDU with fields for source and destination MAC addresses, identifying the particular device on the network to send the data to. Depeding on the model being used, the layer above is the Interne tor Network layer, while the layer below is the Physical layer in the OSI model.

32. **What is included in an Ethernet frame?**
An Ethernet frame includes:
Source and destiniation MAC addresses
Length
DSAP, SSAP, control
Data payload
frame check sequence

33. **Give an overview of the Internet/Network Layer and it's role.**
The primary function of the protocols at this layer is to facilitate communication between hosts (e.g. computer) on different networks. The IP protocol uses IP addresses, which are created in a logical manner and allowing network devices to direct the data in the right general direction even if it does not know of the exact location of the final address.

The IP (internet protocol) is the predominant protoocl used at this layer for itner-network communication. There are two version IPv4 and IPv6 currently in use. The two systems primary features are:
-Routing capabiliy via IP addressing
-Encapsulation of data into packets

34. **What is IP?**
IP stands for Internet Protocol and is the predominant protocol used at the internet/network layer.

35. **What is IP address?** 
An IP address using the IPv4 protocol is an address that is logical in nature. They are not tied to a specific device, but can be assigned as required to devices as they join a network. An IPv4 IP address is 32 bits in length and divided into 4 sections of eight bits each. When converted from binary to decimal, each of those sections provides a range of numbers from 0 to 255.

An IP address is a number constructed of a series of 4 `.` separated 8 bit numbers that are assigned to an individual network-compatible device as it connects to a network. These IP addresses are used to enable communcation between networks, allowing a device connected to some network in New York to connect to another device connected to to a different network elsewhere, say in Vancouver. The reason why IP addresses assist in the inter-network communication vs a MAC address is because the IP addresses are made up in a logical manner, with the series of 8 bit numbers gradually pointing towards a more specific address as we work from left to right.

36. **What are the components of IP addresses?** 
IPv4 addresses can be broken down into:
Country/network
Region/Network
Subnetwork
Device

37. **What is a packet in computer networking?**
A packet is the PDU for the IP Protocol at the Internet/network layer. Key headers in a packet are the Source address and destination address fields, each representing an IP address.

38. **Why do we need both MAC addresses and IP addresses?** 
MAC Addresses are concerned with connecting devices on the same network, IP addresses are concerned with communication between two networked devices anywhere in the world. A MAC address would used in the internet context for direction on each hop, with a new destination and source address being used for each hop. The MAC address would be retrive from that devices ARP table, linking destination MAC address to IP ranges. An IP address is used to direct the data from starting location to end location, providing the network device with a logical path to take.

In another example, an IP address can be thought of as street address, with a MAC address being the next town over that's heading in the right direction. Say we wanted to travel from an ip address in Vancouver to an ip address in San Fransisco. Leaving Vancouver, the vancouver terminal might not know where the destination San franscisco IP address is, but it knows that the general direction is south. The vancouver terminal will then look for the logical next stop going south (or that fits that IP range) and send it there. Let's say Seattle. This would continue until it gets to a general san fransisco router, where it has more infomration on the local streets and neighbourhoods and would have the required information to point it towards a neighbourhood, street, and house.

Ethernet on the physical layer is a protocol that enables communication between devices on a local network using MAC addresses and it's PDU is called a frame.
Internet Protocol on the internet/network layer is a protocol that enables communication between networks using IP addresses and it's PDU is called a packet.

39. **What is DNS and how does it work?**
DNS is the doman name system, and is a distributed database which maps a domain name such as www.whatever.com to the an IP Address.

A Domain name (web address ie www.google.ca) is just an alias for the servers IP address where the resource is located. Every time we enter a new domain name for an address that we have not already looked up, we need to discover the IP address for that respective address. The first step is to check with our ISP and it's DNS server. If that DNS server does not have that address logged, it will then forward the request up the chain of DNS servers until it finds the address of the given domain. After this initial hunt for the IP address, the browser will then cache that domain/ip information and use that cached information to access the site on the next request.

40. **How do port numbers and IP addresses work together?**
IP numbers address to a device on a network, while port numbers assign the PDU to a specfic application(chrome tab, chat window, email client, etc) running on that host.
Together, they form a socket or a socket object. 

41. **What is a checksum and what is it used for? How is it used?**
Checksum data as part of the header or trailer is used to test that the data transported hasn't become corrupt during it's journey.
The checksum procides error detection, and ensures that what was orginally sent by the sender is what was recevied by the receiving party.

42. **Give an overview of the Transport Layer.** 
The transport layer can be thought of as the concierge of an appartment building. Using port numbers, it directs the appropriate internet layer traffic to the correct application running on the host.

THe transport layer can be thought of as the director of traffic for the individual computer or device. This director digests the incoming traffic, deciphers what application the information is for, and sends it to the correct application.

43. **What are the fundamental elements of reliable protocol?**
The fundamental elements required for relaible data transfer are:
In-order dleivery, error detection, handling data loss, and handling duplication.

In order for a protocol to be deemed reliable, we need to ensure that the data is; received on the receiving end, received in order, retransmitted if required, and remove duplicated information.

44. **What is pipe-lining protocols? What are the benefits of it?**
Pipelining increases effeciency of data transfer.
Pipelining is the idea of sending multiple messages one after the other without waiting for acknowledgements.
The advantage of a pipelined approach is its more efficient use of available bandwitdth. Instead of wasting lots of time just waiting for acknowledgements, more time is spent actually transmitting data.

Pipelining is sending out a group of messages one after another, without delaying the transmission of data by waiting for a receipt acknowledgement first. This approach increases the use of available bandwidth, decreasing the length of time it may take to send a full file or large piece of data.

45. **What is a network port?**


46. **What is a port number?**
In simple terms a port is an identifier for a specific process running on a host. The identifier is an integer in the range of 0-65535.

47. **What is a network socket?**
At a conceptul level a socket is an abstration for an endpoint used for inter-process communication. At in implementation level it can be used to refer to different specific things:
-UNIX socket: a mechanism for communication between local processses running on the same machine
-Internet sockets (Such as TCP/IP socket): a mechanism for inter-process communication between networked processes.

48. **Is TCP connectionless? Why?**
TCP is a connection ortiented protocol. The transmission protocol does not start sending application data until a connection has been established using the TCP three way handshake.

49. **How do sockets on the implementation level relate to the idea of protocols being connectionless or connection-oriented?** 
In a connectionless system, we could assign 1 port to a particular process running on an that machine, and listen for all incoming traffic directed to that port.
In a connection based system, the receiving port would still listen for all incoming traffic to that port, but would then instantiate new socket objects for each chunk of data for each individual conversation. It would do this by ensuring that all 4 pieces of data would match, local ip and port number, along with the IP and port number of the process/host which sent the message.

50. **What are sockets on implementation and on a theoretical level?**
Sockets can be implemented as socket objects, further splitting the incoming informationt to further ports for multiple end points within a single application.

51. **What does it mean that the protocol is connection-oriented?**
When a protocol is connection ortiented, it means that we want to establish a realiable communication channel over which to send data before we start the transmission of data.

52. **What is a three-way handshake? What is it used for?**
The three-way handshake is the process which TCP uses to establish a connection between the sender and the receiver.

The three way handshake consists of the sender sending a SYN message to the receiver
The receiver responds to the syn message with a SYN ACK message
Once the sender rceives the servers SYN ACK, it responds with a ACK message and immediately starts sending data.

53. **What are the advantages and disadvantages of a Three-way handshake?** 
The advantages of the three way handshake is that it establishes a reliable communication channel, ensuring a connection is made before attempting to send data.

The disadvantages is performance. The three-way handshake requires a round trip of latency before the start of transmission of data.

54. **What are multiplexing and demultiplexing?**
Multiplexing and demultilexing is a general concept that can be applied in lots of contexts within communication networks and is the general idea of being able to enable multiple connections while only using a single channel.

Multiplexing and demultiplexing in the context of the transportation layer is that the inclusion of port numbers in the PDU for this layer allows for multiple applications to communicate over the same physical connection at the same time.

55. **How does TCP facilitate efficient data transfer?**
In order to help facilitate efficient data transfer once a connection is established, TCP provides mechanisms for flow control and congestion avoidance allowing sender and receiver to communicate how much data can be processed on either end of the connection. Both of these techniques use the WINDOW Size field to change the size of the transmission.

56. **What is flow control? How does it work and why do we need it?**
Flow control is a mechanism to prevent the sender from overwhelming the reveiver with too much data at once. It is required as the receiver will only be able to process a certain amount fo data in a particular time-frame due to buffer size. This is implemeneted using the WINDOW size field in the TCP segment and allows the receiver to communicate the amount of data it is capable of receiver to the sender.

57. **How TCP prevents from receiver's buffer to get overloaded with data?**
In order to not overwhelm the receivers buffer, each side of the connection can let the other side of the connection know how much data they are willing to accept via the WIDNOW size field of the TCP header. This number can change throughout the course of a connection depending on processing loads.

58. **What is congestion avoidance?**
Congestion avoidance is changing how much data is sent on the network at a particular time due to how much data is being lost. TCP reduces the amount of data it sends out based of data loss feedback and uses this data to detect and avoid network congestion by reducing TCP segment size.

59. **What is network congestion?**
Network congestions is a situation that occurs when there is more data being transmitted ont a network than there is network capacity to process and continue transmitting the data.

Congestion can be thought of as gridlock on a road network. However, instead of cars getting stuck standing still, excess cars are lost all together.

60. **How do transport layer protocols enable communication between processes?**
Transport layers use source and destination port numbers to direct the data to the correct processes on the host.

61. **Compare UDP and TCP. What are similarities, what are differences? What are pros and cons of using each one?** 
UDP and TCP are both transport layer protocols. TCP is a connection oriented protocol, while UDP is connectionless.

TCP and UDP both provide for data checking, and multiplexing.

However unlike TCP, UDP does not provide for any of the following:
No guarantee of message delivery
No guarantee of message delivery order
No built in congestion avoidance or flow-control
No connection state tracking

TCP provides for reliable transportation of data at the cost of speed.
UDP provides for speed and flexibility, at teh cost of reliability.

62. **What does it mean that network reliability is engineered?**
This means that network reliability is achieved through protocols that implement error checking, in order delivery, message delviery, etc. These are not underlying characteristics of the physical network, but the work of protocols at higher levels.

What we mean by network reliability being engineered it that the underlying physical network is inherently unreliable. Data can be lost or dropped, corrupted, or manipulated along it's trip from start point to end point. It takes higher level protocols like TCP to put transmission rules in place to ensure that all sent data arrives on the receiving end in the correct state, without being changed or affected along it's journey.

63. **Give an overview of the Application Layer.** 
Both TCP/IP and OSI models define an Application layer as the topmost layer in their resepctive layered system.
To be clear, the application layer is not the application itself, but the set of protocols which provide communication services to applications.
The protocols which exist at this layer are the ones with which the application most directly interacts. Application layer protocols rely on lower level protocols to ensure the message gets to where it is supposed to go, and focus instead on the structure of that message and the data that it should contain.

64. **What is HTML?**
HTML is an acronym for Hyptertext markup language, and can be thought of as the bones of a website. HTML consists of using tags in `<>` brackets such as `h1` for a header, or `<a>` for a link.

65. **What is a URL and what components does it have?**
A URL is a Uniform Resource Locator, and can be thought of as the the street address or phone number you need to visit or communicate with that resource.

The `http://www.example.com:88/home?item=book` URL consists of theses components:
https = The scheme
www.example.com = THe host
:88 = the port
/home = the path
?item=book = query string, made up of query parameters.

66. **What is a Query string? What it is used for?**
Query strings are started by the `?` character and are used to send data to the server. The query string consists of query parameters, key value pairs that send additional data to the server. The pairs are split with a `=` and multiple parameters are joined using the `&` symbol.

67. **What URL encoding is and when it might be used for?**
URL encoding serves the purpose of replacing non-conforming characters with a `%` symbol followed by the two hexademical digits that represent the equivalent UTF-8 character.

68. **Which characters have to be encoded in the URL? Why?**
Any character no within the 128-character ASCII character set need to be encoded, along with any reserved or unsade ASCII characters that are not being used for their intended prupose.

Characters must be incoded if:
They have no corresponding character within the ASCII character set.
The use of the character is unsafe since it may be misinterpreted or modified by some system.
THe character is reserved for special use within the URL scheme.

69. **What is www in the URL?** 
The `www` in a url stands for world wide web and is a service that can be accessed via the internet. In simple terms, it's a vast information system comprised of resources which are navigable by means of a URL.

70. **What is URI?**
A URI is a Uniform Resource Identifier, which specifies how resources are located. a URL is a type of URI.

71. **What is the difference between scheme and protocol in URL?**
The scheme is what tells the web client how to access the resource. It's what comes before the `://` in a URL. The connection between the scheme and the protocol is that the scheme can indicate which protocol should be used to access the resource.

72. **What is HTTP?**
HTTP is Hypertext transfer protocol and is the set of rules which provide uniformity to the way resources on the web are transferred between applications.

73. **What is the role of HTTP?**
The role of HTTP is to provide a set of rules to provide uniformity to the way resource on the web are transferred between applications.

74. **Explain the client-server model of web interactions, and the role of HTTP as a protocol within that model**
The client-server model of web interactions refers to the request-response cycle of the HTTP protocol, where everytime an action is requested by the client, the server issues a response.

75. **What are HTTP requests and responses? What are the components of each?**
HTTP Requests are requests that are generated by applications such as a browser, say when we enter a URL into our browser.
HTTP Responses are responses to our HTPT request generated by the destination server.

HTTP Requests consist of; request line, headers, and a optional message body.
HTTP Responses consist of; status lines, optional headers, and an optional message body.

76. **Describe the HTTP request/response cycle.**
The request response cycle occurs every time we refresh or try to get a resource from the web. The browser or http tool places a request with a request line, to a specific server. The server then responds with a status line, headers, and a request body of the data that is being requested.

77. **What is a state in the context of the 'web'?**
In the context of the web, state could reference the users log in status, prefilled information on a form, number of likes a post has, etc.

78. **What is statelessness?**
Statelessness in the context of a web protocol refers to how no lingering information is stored, or connection mainted with, on the server regarding the past interactions of a client.

79. **What is a stateful Web Application?**
A stateful web application is an application in which through the use of cookies, session ID's or refreshing only parts of a page via AJAX, the application appears to remember the state of the previously loaded webpage like if a user is logged in, or certain form feilds were filled out.

80. **How can we mimic a stateful application?**
We can mimic a stateful application through the use of cookies, session ID's, or AJAX, along with sending additional dataa to the server via query strings in the URL.

81. **What is the difference between stateful and stateless applications?**
As HTTP is a stateless protocol, each request/response cycle is independent of request and responses that came before or those that come after.

A sateful application is one which remembers things like user log in status, the application will use techniques like sessions IDs and cookies to remember information about the requesting party.
A stateless application is one which treats every request and response completeley independently, in other words, not using any additional techniques to make HTTP appear as if it remembers state.

82. **What does it mean that HTTP is a 'stateless protocol?** 
HTTP as a stateless protocol means that each request/response cycle is treated as independent of any request and responses that came before or those that come after.

83. **Why HTTP makes it difficult to build a stateful application?**
Because it is a stateles protocol. The means that on each client/server interaction, ALL required information about the clients state within the application needs to be sent.

84. **How the idea that HTTP is a stateless protocol makes the web difficult to secure?** 
In the same way that HTTP is made so difficult to control, it also makes it so difficult to secure. This is due to the same techniques used that make a application or webpage appear sateful also pose a serious security threat.

85. **What is a `GET` request and how does it work?** 
A GET request is an HTTP method used to ask to retrieve the resource at that address.

86. **How is `GET` request initiated?**
GET Requests are initiated by clicking a link on a webpage, entering a URL via the address bar of a browser, or via a HTTP request tool.

87. **What is the HTTP response body and what do we use it for?**
The HTTP response body is the actual data that is beign transmitted in a HTTP message. This can be any type of data, with the type of data typically being defined by a HTTP response header. 

88. **What are the obligatory components of HTTP requests?** 
The obligatory components of a HTTP request are the request line, and headers.

89. **What are the obligatory components of HTTP response?**
The obligatory components of a HTTP response is the status line.

90. **Which HTTP method would you use to send sensitive information to a server? Why?**
POST. POST allows us to send the information as part of the HTTP request body.

91. **Compare `GET` and `POST` methods.**
GET is mostly used to retrieve resources from a server, POST is used to send or submit information to that server.

92. **Describe how would you send a `GET` request to a server and what would happen at each stage.**
We can send a GET request to a server by entering a URL in our web browser. The request would then get sent to the server, where the server would issue a HTTP response with status line, optional headers, and optional response body.

93. **Describe how would you send `POST` requests to a server and what is happening at each stage.**
A POST Request sends information to a server through the HTTP request body. The server receives the request, makes the changes, and issues a response.

94. **What is a status code? What are some of the status codes types? What is the purpose of status codes?** 
Status codes are 3 digit numbers that the server sends back after receiving a request signifying the status of the request.
Some common status codes are 200 - OK, 302 - found, 404 - not found, 500 - internal server error.

95. **Imagine you are using an HTTP tool and you received a status code `302`. What does this status code mean and what happens if you receive a status code like that?** 
302- found means that the resource has been moved, and that the orignal URL has been re routed to a new URL. This kind of rerouting is called a `redirect`. When browswers see this response code, it knows the resource has been moved and will automatically follow the new re-routed URL in the location response header.

96. **How do modern web applications 'remember' state for each client?**
Modern web applications can employ a number of different techniques to simulate being a stateful application. This is most commonly done using Cookies, session IDs, and/or AJAX.

97. **What role does AJAX play in displaying dynamic content in web applications?**
AJAX is short of Asynchronous JavaScript and XML. It's main feature is that it allows browsers to issue requests and process responses without a full page refresh. This allows for for only parts of the webpage to refresh when a request/response cycle has occured from some user input, both saving resources and appearing as a stateful application.

98. **Describe some of the security threats and what can be done to minimize them?**
As HTTP is so difficult to control, this also makes it so difficult to secure. Some of the security threats of HTTP are session id theft, other apps browsing cookie history, users adding raw viewable HTML or JavaScript to a site via a comment tab, etc. In order to minimize these risks, we can emply tecniques like HTTPS, same-origin policy, and setting expiration times to active session IDs.

99. **What is the Same Origin Policy? How it is used to mitigate certain security threats?**  
The same origin policy permits unrestricted interactions between resources orginiating from the same origin, but restricts certain interactions between resources orginating from differents origins. By origin here we mean same scheme, host, and port. Same-origin policy does not restrict al cross-origin requests, but what it does restrict are cross-origin requests where resources are being accessed programmatically using APIs such as `XmlHttpRequeest` or `fetch`. The same origin policy is an important guard against session hijacking attacks and servers as a cornerstone of web application security.

100. **What determines whether a request should use `GET` or `POST` as its HTTP method?**
Requests using the GET method are used to retrive or ask for information from  a server.
To send or submit data to a server we use the POST HTTP method.

101. **What is the relationship between a scheme and a protocol in the context of a URL?**
The scheme identified in the url before the `://` identifies which protocol should be used.

102. **In what ways can we pass information to the application server via the URL?**
To pass information to the server via the URL, we can use the path and query parameters. Query parameters are the key value pairs that are seperated by `=`, joined by `&`, and begin after the `?` in a url. The path can indicate which page we wish to access direclty, rather than the hosts default home(root) page.

103. **How insecure HTTP message transfer looks like?**
HTTP requests and responses are sent as plain text, with no encryption to make the data transfer secure. In order for the request/response messages to be encrypted we need to use HTTPS witch uses TLS to encrpyt the data transfer.

104. **What services does HTTP provide and what are the particular problems each of them aims to address?**
HTTP gives users a way to interact with a web resources via its request-response cycle.

105. **What is TLS Handshake?**
The TLS(transport layer security) handshake is what TLS uses to set up an encrypted message exchange between host and server. It is a 4 step process where client and server exchange messages to enable encrypted communication using symmetric keys.

106. **What is symmetric key encryption? What is it used for?**
Symmetric key encryption is when both sender and receiver of a ciphertext message have a copy of the same key, which is responsible for both encrypting and decrypting the message.

107. **What is asymmetric key encryption? What is it used for?**
Asymmetric key encryption is when we use a public key and a private key. The public key is used to encrypt, and the private key is used to decrypt. Asymmetric key encription is intended to work in one directon only. This asymmetric key encryption is used for the transfer of the symmetric key in the TLS handshake.

108. **Describe SSL/TLS encryption process.**
The TLS encryption process revolves around the TLS handshake.

Steps of the TLS Handshake:
1. `ClientHello` message sent immediately after the TCP ACK message. This contains the maximum version of TLS protocol they support, and a list of Cipher Suites that the client is able to use.
2. Server responds with `ServerHello`, which sets the TSL protocol version and cipher suite. As part of the message the server also sends its certificate (which contains its public key), and a ServerHelloDone marker.
3. Once client receives the `ServerHelloDone` marker, it will initiate the key exchange process that ultimately enables both the client and server to security obtain a copy of the symmetric encryption key.
The steps are:
  -Client generates a `pre-master secret` encrypts it using the server's public key, send to server.
  -Server receives the encrypted `pre-master secret`, and decrypts it using its own private key.
  -Both client and server will use the `pre-master secret` along with some other pre-agreed parameters to generate the same symmetric key.
  -As part of the communication which includes `ClientKeyExchange` message, the client also sends a `ChangeCipherSpec` flag, which tells the server that encrypted communication should now start using the symmetric keys. Additionally this communication has a `Finished` flag to indicate the client is done with the TLS handshake.

4. The server also sends a message with `ChangeCipherSpec` and `Finished` flags. The client and server can now begin secure communication using the symmetric key.

109. **Describe the pros and cons of TLS Handshake**
The pros of the TLS handshake is that it enables encrypted transfer of HTTP request/response data, establishes a secure connection with the server, and verifies the server is who they say they are.

The downsides are performance, as the establsihed of a secure connection via the TLS handshake requires 2 roundtrips of latency in order to become established, there is an additional amount of time before data transfer can actually begin occuring.

110. **Why do we need digital TLS/SSL certificates?**
TLS certificates are used to verify that the server we are communicating with actually is the intended server of the site we are trying to reach. These certificates are issued to sites via a leveled certificate authoritie system, and rely on a chain of trust, trusting the reputation of the root CA that starts the chain.

111. **What is it CA hierarchy and what is its role in providing secure message transfer?**
CA (certificate authorities) are who issue digital certificates. There are three different levels of CA, site certificate, intermediate CA can be any company or body authorised by ROOT CAs. The purpose of this chain like strucuture is the level of security it provides. Ulatimately though, ROOT CA's are trusted because of their repurtaion and longevity.

112. **What is Cipher Suites and what do we need it for?**
A cipher suite is a group or set of ciphers that are used for cyryptohraphy. A cipher is a cryptographic algorithm; in other words they are sets or steps for performing encryption and decryption.

A cipher suite is used by TLS for different aspects of establishing and maintaining a secure connection.

113. **How does TLS add a security layer to HTTP?**
TLS adds a security layer to HTTP by establishing a secure connection for data transfer by ensuring the server is who they say they are, encrypting the data being sent back and forth, and ensuring the data sent back and forth has not been tampered with during transit.

114. **Compare HTTP and HTTPS.**
The biggest difference between HTTP and HTTPS is that HTTP does not use encryption to protect data between client and server.

115. **Does HTTPS use other protocols?** 
HTTPS is the combination of the HTTP and TLS protocols. This combination allows for safe encrypted data transfer and the establishment of secure connections between client and server.

116. **How do you know a website uses HTTPS?**
The `https` scheme will be visible in the URL, and this protocol combination will also require the use of site cerificates which can be viewed in most browsers.

117. **Give examples of some protocols that would be used when a user interacts with a banking website. What would be the role of those protocols?** 
HTTPS would be used to make the request to the server and have the server issue a response.
TLS would also be used to have an encrypted channel of communication between client and server, and authenticate that the server is actually the bank i'm trying to reach, lastly TLS would also be used to ensure that the data transferred has not been tampered with.
TCP would be used to establish a reliable connection between host and server
IP would be used to get the information from client to server and back again.
Ethernet would be used to direct the data at each hop along it's journey.

118. **What is server-side infrastructure? What are its basic components?**
The basic components of server-side infrastructure would be; web-server, application server, and a data store.
The web server is typically a server that responds to requests for static assets; files, images, css, javascript, etc.
THe application server, is typically where application and business logic resides, and is where more complicated requests are handled.
The data store, is often where the application layer will go to consult persistent data like a relational database, to retrive or create data.

119. **What is a server? What is its role?** 
A server is essentially a program or bit of software that someone wrote and their purpose is to serve webpages or application data.

120. **What are optimizations that developers can do in order to improve performance and minimize latency?**
The simplest of techniques is to consider whether every resource or dependency that your application uses is strictly necessary.

Another technique for improving performance is data compression, this is using bits of software to reduce file sizes, allowing for quicker data transfer.

Reusing TCP Connections. This allows the client-server interaction to keep a connection alive, and allows us to skip the TCP 3 way handshake on each new interaction.

DNS Optimizations
As every request to connect to a domain will involve a DNS lookup, this area is a prime candidate for optimization. The first way to improve this is by reducing the number of host names that need to be resolved. Another method is download any external resources and host them locally on the server that is hosting the web app, a third avenue is to use a faster DNS provider.

Caching
What we mean by caching for optimization is server-side. Caches are a seperate component from the host server and are essentially short-term memory banks. What they do is store content that was recently accessed by a user so that next time that content is request it can be delivered more quickly.

##### LS 170 SPOT Study Session #####

Test revisions, additional review, notes in notion. Seconds LS 170 review tab started.
