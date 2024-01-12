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

- 