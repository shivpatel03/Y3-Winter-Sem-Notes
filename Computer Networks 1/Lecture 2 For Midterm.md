# Network Software 


# Protocol Layers
- protocol layering is structuring method used to divide network functionality
	- each protocol instance talks virtually to its peer
	- layer communicates with only the one below 
	- lower layer accessed by interface
	- at bottom, messages are carried by medium

- each layer at different protocol has different purpose
- each layer adds its own information (in the form of a header) to the message that will be sent above
	- above message will remove it
- layers may also split and join messages


- each layer solves specific problem
- must include mechanisms to address a set of recurring design issues

- layers offer two types of service to the layer above:
	- connection oriented: connection must be setup and then torn down after
	- connectionless: messages handled separately -> the message carries some type of target address
- each service can be characterized by its reliability
	- reliability is measured in the fact that the message is acknowledged


# Service Primitives 
- services provided to the layer above is known as primitives (operations)
- if a protocol stack is located in the OS, these operations are usually *system calls*
- examples of service primitives that may provide a reliable bye stream (in a connection-oriented) service

| Primitive | Meanings |
| ---- | ---- |
| LISTEN | block waiting for incoming connection |
| CONNECT | establish a connection with a waiting peer |
| ACCEPT | accept an incoming connection from a peer |
| RECEIVE | block waiting for an incoming message |
| SEND | send a message to a peer |
| DISCONNECT | terminate a connection |


# Relationship of Services to Protocols 
- service is a set of operations that layer provides to the layer above it
	- a layer provides a service to the one above it (vertically)
- a protocol is a set of rules that control the format and meaning of the packets
	- layer talks to the peer using protocol (horizontally)
![[Pasted image 20240213230707.png]]

# Reference Models 
- describe layers in the network architecture
	- OSI (open systems interconnection) reference model 
		- developed by ISO (international standard organization)
	- TCP/IP reference model
	- Model used for this text

# OSI 
- a principled, international standard, seven layer model to connect different systems
	- these are the layers

goes from 7-1
- Application: provides function needed by users
- Presentation: converts different representations
- Session: manages task dialogs
- Transport: provides end-to-end delivery
- Network: sends packets over multiple links
- Data link: sends frames of information
- Physical: sends bits as signals over the channel

- Physical layer: 
	- determines the specs for all physical components
		- cabling
		- interconnected methods
		- data encoding 
		- electrical properties
	- What are the physical layer components on computer
		- network interface card
		- has a MAC address or physical address of a computer 
- Data Link Layer:
	- data transfer between neighboring network elements
		- moves frames from one hop to another
	- provides error detection/correction
	- control access to shared channel
	- Sub layers of the Data Link Layer
		- MAC
			- gives data to NIC
		- LLC (logical link layer)
			- manages the data link interface
			- can detect transmission errors using Cyclic Redundancy Check (CRC)
				- if bad package, LLC will request the sender to resend it
- Network Layer:
	- controls the operation of the subnet
	- provides network-wide addressing and a mechanism to move packets between networks (routing)
		- routing diagrams (packets) from source to destination
- Transport Layer: 

# Better Explanation of OSI 
1. Physical Layer: deals with physical connection between devices including transmission of raw data over a physical medium such as cables or wireless signals. defines electrical, mechanical and procedural specifications for connecting devices
2. Data link layer: provides error detection and data framing. makes sure that the connection between devices on the same network is good
3. Network layer: responsible for routing packets across different networks. determines best path for packets to destination
	1. destination is defined by IP addresses or network conditions
4. Transport layer: ensures reliable end-to-end communication between hosts. splits up the data, controls the flow of the data, the error recovery, and provides mechanisms for breaking big pieces of data to smaller ones and reassemble them at the destination
5. Session layer: establishes communication between applications. Handle session setup, synchronization and teardown, allowing for dialogue control between different applications
6. Presentation layer: responsible for data translation, encryption, and compression. ensures that the data passed between applications is in a format that each of them can understand
7. Application layer: provides network services directly to end users. 

## How do all layers work together? 
- Each layer has a Protocol Data Unit (PDU)
	- used for peer to peer contact 
	- data is handled by the top three layers
	- network layer places it into packets and the Data Link frames the packet for transmission
	- physical layer converts it to bits and sends it out over the media
	- the receiving computer reverses the process using the information contained in the PDU
![[Pasted image 20240213234352.png]]

Host A wants to send something to Host B, and each layer for each host is connected and sending information to one another
![[Pasted image 20240213234500.png]]

# TCP/IP reference model
- Derived from experimentation
	- omits some OSI layers and uses the IP as the network Layer

- Application
	- provides network services to end-users
	- various protocols
	- HTTP protocol for web browsing
	- interact with underlying layers to transmit and receive data over the network
- Transport
	- provides end-to-end communication with devices on a network
	- ensures reliable data delivery, flow control, error handling
	- most common is TCP and UDP
	- TCP: reliable, connection oriented
	- UDP: connectionless, fast, but unreliable data transmission
		- TCP requires handshakes to work (connection-oriented)
			- `connection.request` -> requests connection to other machine
			- `connection.acknowledgement` -> other machine acknowledges request
			- `acknowledge` -> first machine acknowledges again before sending required data
		- UDP (connectionless)
			- can perform
- Internet
	- addressing and breaking up data packets that are going to be transmitted
	- primary protocol is the Internet Protocol (IP) which provides addressing (IP addresses) for devices and shows how data packets are sent between networks
	- ensures data packets can go through different networks and reach their destination
	- ICMP for error reporting (internet control message passing) and ARP (address resolution protocol) for mapping IP addresses to MAC addresses
- Link
	- lowest layer
	- responsible for physical transmission of data
	- has protocols that define how data is formatted
	- deals with hardware addressing (MAC addresses)
	- Ethernet and point to point protocols operate at this layer

# IP vs. MAC Address 
- IP is a label given to any device that uses the Internet Protocol for communication
- MAC address is a unique identifier assigned to network interfaces.


# Socket Programming: TCP 
- Server programming
1. Socket Creation
`int sockfd = socket(domain, type, protocol)`
`sockfd`: socket descriptor, an integer (like a file handle)
`domain` : integer that specifies communication domain
	`AF_LOCAL`: used for communications on the same host
	`AF_INET`: used for communications between different hosts connected by IPV4
	`AF_INET6`: used for communications between different devices connected by IPV6
`type`: communication type:
	`SOCK_STREAM`: TCP(reliable, connection-oriented)
	`SOCK_DGRAM`: UDP(unreliable, connectionless)
`protocol`: protocol value for Internet Protocol, which is 0

2. Bind: connects socket to address and port number in `addr`. you can use `INADDR_ANY` to use any IP address on the server to create new clients
`int bind(int sockfd, const struct sockaddr * addr, socklen_t addrlen)`

3. Listen: puts server socket in passive mode, waits for client
`int listen (int sockfd, int backlog)`
- `backlog` is the max length of the queue of pending connections

4. Accept
`int new_socket = accept(int sockfd, struct sockaddr * addr, socklen_t * addrlen)`
 - gets first connection request in the queue of connections from the listening socket `sockfd`
 - creates a new connected socket and returns a new file descriptor referring to that socket
 - connections between client and server is made
 - close connection when done using `close(sockfd)`


- Client Programming
1. Socket Creation
same as server: 
`int sockfd = socket(domain, type, protocol)`
2. Connect
`int connect(int sockfd, const struct sockaddr * addr, socklen_t addrlen)`
- `connect()` system call connects socket defined by the file descriptor `sockfd` to address `addr`
- to connect to a server, you put the server's address as `addr`
you can now send and receive data
close after use with `close(sockfd)`


# Socket Programming: UDP Server
- connectionless
- does not require handshaking to send/receive data

## Server Side
1. Create socket
	`int socket_desc = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP)`

2. Bind socket descriptor to server address
	`bind(socket_desc,(struct sockaddr*)&server_addr,sizeof(server_addr);`
	- unlike TCP, server side does not wait for a client to connect. so it does not receive client's address before sending and receiving data
	- rather, the server gets information about the client when it receives data using the `recvfrom()` method
3. send/receive data
	`recvfrom(socket_desc, client_message, sizeof(client_message),0,(struct sockaddr*)&client_addr, &client_struct_length);`
	- client's information stored in variable called `client_addr`
	`sendto(sock_desc, server_message, strlen(server_message),0,(struct sockaddr*)&client_addr, client_struct_lenght)`

4. close the socket to end the communication
	`close(socket_desc)`


## Client Side
im not writing the code but you need to specify the server's address every single time you want to send and receve
sending can be done with `sendto()` and receive can be done with `recvfrom()`