# Network Software

You need software to run networks
- every device has it's own 'stack' of software
- networks are built on a layered architecture
- pros and cons
	- a big pro:
		- can change anything in the layer without the need to change anything on another layer
	- the main con: 
		- it's relatively slow
			- to go to another layer, you have to go through another layer in one direction (it's more of a stack, and you can't really work concurrently)
- network software is divided into 7 layers 
	- each layer communicates only with the one below 
	- lower layer services are accessed through an interface
	- at the bottom, messages are carried by the medium
	- so you start at the bottom, and then you move down 
		- once you get all the way down


- suppose there are tow hosts and they both have 5 layers, each layer in each host is going to communicate with each other

## Protocol Layers
- each protocol at different layers serves a different purpose
- each lower layer adds its own header to the message to transmit and removes it on receive
- layers may also split and join messages
- we have a protocol for EVERY LAYER in the SOFTWARE stack of a network
- what is a protocol:
	- a set of rules
	- example: if you want to communicate with another student, you have to speak the same language. the two software that are involved within the stack must understand each other, this language can be seen as a protocol
- each lower layer adds its own header to the message to transmit and removes it on the receive
- layers may also split and join messages


# Design Issues for the Layers 
- each layer solves a specific problem but must also include a way to address a set of recurring design issues

| Issue | Example mechanisms at different layers |
| ---- | ---- |
| Reliability despite failures | Codes for error detection |
| Network growth and evolution | Addressing and naming protocol layering |
| Allocation of resources like bandwidth | Multiple access and congestion control |
| Security against various threats | Confidentiality of messages and authentication of communicating parties |

# Connection-Oriented vs. Connectionless
- layers can give two types of services to the layers above them:
	- connected oriented: connection must be setup for use (and then torn down after), example: phone call
	- connectionless: messages are handled separately. example: postal delivery (each message contains the full target address and is routed independently)
		- there is no direct connection
- each kind of service can further be characterized by it's reliability 
	- by reliability, it means how often the message is acknowledged by the above layer


# Services Primitives
- A service is provided to the layer above as primitives (operations)
- if the protocol stack is located in the operating system, as it usually is, the primitives are normally system calls
	- these calls cause a trap to kernel mode, which then turns control of the machine over to the operating system to send the necessary packets
- hypothetical example of service primitives that may be help provide a reliable byte stream (connection-oriented) service

| Primitive | Meaning |
| ---- | ---- |
| LISTEN | Block waiting for an incoming connection |
| CONNECT | Establish a connection with a waiting peer |
| ACCEPT | Accept an incoming connection from a peer |
| RECEIVE | Block waiting for an incoming message |
| SEND | Send a message to the peer |
| DISCONNECT | Terminate a connection |
- assume you have a client machine connecting to a server machine
	- in this system, the client machine will have a protocol stack and the server machine will have one of its own
	- the client will use this protocol stack (located in the operating system) to send system calls to it, and the protocol stack also has the ability to send it to the client process as well
	- through this protocol stack, it can send messages/commands/actions to the server machine in order to accomplish a task
	- ![[img/Pasted image 20240118105215.png]]

# Relationship of Services to Protocols
- A service is a set of primitives (operations) that a layer provides to the layer above it
	- a layer provides a "service" to the layer above it -> vertical
- A protocol is a set of rules governing the format and meaning of the packets, or messages that are exchanged by the peer entities within a layer
	- a layer talks to its peer using a protocol -> horizontal\


# Reference Models
- Reference models describe the layers in a network architecture
	- OSI
		- open systems interconnection
		- developed by ISO
	- TCP/IP reference model
	- etc.

# OSI Reference Model
- includes seven layers to connect different systems
- international model
7. Application
6. Presentation
5. Session
4. Transport
3. Network
2. Data link
1. Physical

## The layers: 
- Physical Layer:
	- bits "on the wire"
	- determine the specs for all physical components
		- Cabling: Twisted pair, fiber optic, coax cable
		- interconnection methods
		- data encoding
		- electrical properties
		- example:
			- ethernet
			- token ring 
			- wireless
	- what are the Physical Layer components on computer?
		- NIC: network interface card
		- It has a MAC address/physical address of a computer
- Link Layer:
	- Data transfer between neighboring network elements
		- moving frames from one node to another
	- Provides error detection/correction capability
		- using acknowledgement
		- FEC (Forward Error Correction)
	- Control access to shared channel
		- MAC: Medium Access Control sublayer
	- Sublayers of the Data Link Layer:
		- MAC (Media Access Control)
			- Gives data to INC
			- Controls access to the media through
				- Carrier sense multiple access/collision detection
				- token passing
			- LLC (Logical Link Layer)
				- manages the data link interface
				- can detect some transmission errors using cyclic redundancy check
					- if the packet is bad the LLC will request the sender to resend it
- Network Layer
	- Controls the operation of the subnet
		- provides network-wide addressing and a mechanism to move packets between networks (routing)
			- routing of datagrams (packets) from source to destination
		- handling congestion in conjunction with higher levels
		- Examples: IP, routing protocols
- Transport Layer
	- process-process data transfer
	- provides reliable data delivery
	- receives info from upper layers and segments it into packets
	- provides end-to-end upper control and flow control
	- Examples: TCP, UDP
	- Differences between data-link and transport layers in terms of Error Control
- Session Layer
	- Allows applications to maintain an ongoing session
	- synchronization, checkpointing to allow users to pick up where they left off in the event of a crash
	- Examples: 
		- operating systems, scheduling
		- remote procedure call (RPC)
- Presentation Layer
	- allows applications to interpret the meaning of data, example: encryption, compression, machine-specific conventions
	- examples:
		- ASCII, EBCDIC, JPEG, MP3
	- why presentation layer?
		- Example: what is the value of 10010001?
		- depends on how you want to interpret it
			- if it is unsigned, 45
			- if it is signed: -111
			- if it is interpreted as ASCII (odd parity): H
- Application Layer
	- Supporting network applications
		- gives end-user applications access to network resources
		- usually on Workstation or Server Service in Microsoft Windows
	- Examples:
		- FTP, SMTP, HTTP, Telnet, VoIP, Secure Shell 

- How all layers work together
	- Each layer contains a Protocol Data Unit (PDU)
		- used for peer-to-peer contact between corresponding layers
		- Data is handled by the top three layers, then Segmented by the Transport layer
		- The network layer places it into packets and the Data link frames the packets for transmission
		- Physical layer converts it to bits and sends it over the media
		- the receiving computer reverses the process under the information contained in the PDU
![[img/Pasted image 20240118112148.png]]



# TCP/IP Reference Model 
- A four-layer model derived from experimentation
	- omits some of the OSI layers and uses the IP for the network layer
- The link layer describes what links such as serial lines and classic Ethernet must do to meet the needs of the connectionless internet layer
- the internet layer defines two protocols
	- IP (Internet Protocol)
	- ICMP (Internet Control Message Protocol) to help the IP
- The job of the internet layer is to deliver IP packets where they are supposed to go

- The transport layer allows peer entities on the source and destination hosts to carry on a conversation
	- defines two protocols: 
		- TCP (Transmission Control Protocol)
			- It is a reliable connection-oriented protocol
			- It handles flow control to make sure a faster sender cannot swamp a slow receiver
		- UDP (User Datagram Protocol)
			- an unreliable, connectionless protocol
			- also widely used for its one-shot, client-server-type request-reply queries and applications in which prompt delivery is more important than accurate deliver, such as transmitting speech or video
				- you care much less about the quality of the audio/video and more about the fact that you're even getting any video at all

# TCP: Transmission Control Protocol 
- TCP - Connection and Error Control Mechanism Overview
	- Applications using TCP need to establish a TCP connection before data can be transferred
	- ![[img/Pasted image 20240118124217.png]]
	- need handshake protocols before data can be requested/sent

# UDP: User Datagram Protocol 
- Connectionless, data can be transferred without requiring connection establishment
- UDP can perform error detection but not error recovery
	- if something goes wrong, it can tell you what went wrong but not fix it


# Socket Programming: TCP
## Server Programming
1. Socket Creation: 
```
int sockfd = socket(domain,type,protocol)
```
- `sockfd`: socket descriptor, and integer (like file handler)
- `domain`: socket descriptor, specifies communication domain:
		```
		AF_LOCAL: used for communication between processes on the same host
		AF_INET: used for communication between processses on different hosts connected by IPV4
		AF_INET6: used for communication betweetn processes on differetn hosts connected by IPV6
		```
	- `type`: communication type:
```
SOCK_STREAM: TCP (reliable and connection oriented)
SOCK_DGRAM: UDP (unreliable and connectionless)
```
`protocol`: Protocol value for Internet Protocol (IP), which is 0
2. Bind: binds the socket to the address and port number specified in `addr`. you can use `INADDR_ANY` to use any IP address on the server to receive new clients
`int bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen);`
3. Listen: it puts the server socket in a passive mode, where it waits for clients to approach the server to make a connection
`int listen(int sockfd, int backlog);`
4. Accept
`int new_socket=accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);`
- extracts the first connection request on the queue of pending connections on the listening socket `sockfd`, creates a new connected socket and returns a new file descriptor referring to that socket
- at this point, the connection between the client and server is set, and they are ready to transfer data
you can send and receive data, once that is done, you can close the connection:
`close(sockfd);`

## Client Programming
1. Socket Creation: same as the one for server
`int sockfd=socket(domain,type,protocol);`
1. Connect
`int connect(int sockfd,const struct sockaddr *addr, socklen_t addrlen);`
- the connect() system call connects the socket referred to by the file descriptor `sockfd` to the address specified by `addr`
- server's address and port is specified in `addr`

you can now send and receive data to/from the server, once finished, close the connection with `close(sockfd)`


# Socket Programming: UDP Server 
- Connectionless
- does not require any handshaking

1. Create a socket
`int socket_desc = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);`
2. Bind socket descriptor to the server address
`bind(socket_desc,(struct sockaddr*)&server_addr,sizeof(server_addr);`
- unlike TCP, the server-side does not wait for a client to connect and, therefore, does not receive the client's address prior to sending the receiving data
- instead, the server receives information about the client when it receives data using the `recvfrom()` function.
3. Send/receive data
- `recvfrom(socket_desc,client_message,sizezof(client_message),0,(struct sockaddr*)&client_addr,client_struct_length);`
4. Close the socket to end the communication
`close(socket_desc);`

# Socket Programming: UDP Client
1.  Create a socket, and initialize the server's address information in a variable of type `sockaddr_in`
`int socket_desc = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);`
2. Send and receive data: 
- unlike TCP, when the client sends and receives data using `sendto()` and `recvfrom()`, the server's information has to be given every single time
`sendto(socket_desc, client_message, strlen(client_message), 0, (struct sockaddr*)&server_addr, server_struct_length);`

`recvfrom(socket_desc, server_message, sizeof(server_message), 0, (struct sockaddr*)&server_addr, &server_struct_length);`

# TCP/IP Reference Model 
- The application layer contains all the higher-level protocols:
	- TELNET: to provide a bidirectional interactive text-oriented communication facility using a virtual terminal connection
	- TCP (File Transfer Protocol)
	- SMTP (Simple Mail Transfer Protocol), for electronic mail
	- DNS (Domain Name System), for mapping host names onto their network address
	- HTTP (Hyper Text Transferee Protocol), for fetching pages on the World Wide Web
	- RTP (Real Time Protocol): for delivering real-time media such as voice or movies
	- 
# Note on Protocols within Layers:
	each layer has a protocol, and those protocols are used to interact with the layers above them. this means that every layer has a set of its own protocols that will be used to accomplish it's own specific task