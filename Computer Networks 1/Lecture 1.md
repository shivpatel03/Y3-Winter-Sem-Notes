## Introduction 
- gathering information, processing it, and distributing it are key technologies today
- as the ability to do the following grows, the demand for specific information processing becomes higher
- merging of computers and communications has had a big impact on the way computer systems are organized
	- from computer center to computer networks


## Uses of Computer Networks
- collection of autonomous computers interconnected by a single technology: example: the internet
- many uses
	- business applications
		- resource sharing, information sharing, voice over internet protocol (VOIP)
	- home applications
	- mobile users
- These uses raise social issues

### Business Applications
- companies use networks of computers for resource sharing with the client-server model
	- other uses are communication (email, VoIP, e-commerce)

### Home Applications
- contain many networked devices (computers, TVs) all connected to the internet
- home users communicate (social networks, content consumption, etc.)
- some applications use the peer-to-peer model in which there are no fixed clients or servers
	- all users are interacting with one another

### Mobile users 
- Tablets, laptops, and smart phones are popular devices
- communicate, consume content, and use sensors (GPS for example)
- wireless and mobile are related but different


### Social Issues
- network neutrality - no network restrictions 
	- communications that are not differentiated by their content or source who is providing the content
- content ownership
	- pirated music and movies
- anonymity and censorship
	- web browsers store cookies on users' computers and these companies can track the users' activities
- privacy
- theft of information
	- botnets: a bunch of machines whose main purpose is to send spams
	- phishing


## Network Hardware
- networks can be classified by: 
	- transmission technology: 
		- point-to-point: connect individual pairs of machines (Unicast)
		- broadcast: the communication channel is shared by all machines on the network
	- network scale

| Scale | Type |
| ------ | ------ |
|Vicinity | PAN (Personal Area Network) |
|Building | LAN (Local Area Network) |
|City | MAN (Metropolitan Area Network) |
|Country | WAN (Wide Area Network) |
|Planet | The internet (network of all networks)
- an 'internetwork' is any network comprised of smaller networks. The Internet (apparently the capital I is important) is the set of all connected networks


### Personal Area Network (PAN)
- connect devices over the range of a person
	- Bluetooth for example

### Local Area Network (LAN)
- Connect devices in a home or office building
- if used in a company, it is called 'enterprise network'


### Metropolitan Area Networks (MAN)
- connect devices over a metropolitan area (city)
- example: MAN based on cable TV network:
	- also delivers Internet

### Wide Area Networks (WAN)
- Connects devices over a country
- Example: 
	- WAN connecting three branch offices by using leased line
- An ISP (internet service provider) network is also a WAN
- Customers buy connectivity from the ISP to use it
- a VPN is a WAN built from virtual links that run on top of the Internet

### Internetworks 
- collection of interconnected networks
	- networks are connected through devices (called gateways) that provide the necessary translation, both in terms of hardware and software
	- gateways are distinguished by the layer at which they operate in the protocol hierarchy:
		- using too low-level gateway, will prevent from making connections between different kinds of networks
		- using too high-level gateway, the connection will only work for particular applications
		- The level in the middle is ideal, often called the Network Layer. And a Router is a gateway that switches packets at the network layer

# Internet 
- Before the Internet there was the ARPANET (Advanced Research Projects Agency Network), which was a decentralized, packet-switched network based on Baran's ideas 

- the early internet used NSFNET (National Science Foundation Network) as its backbone, universities that were connected had access to the internet

- modern internet is more complex
	- ISP networks serve as the Internet backbone
		- They connect or peer to exchange traffic at Internet eXchange Points (IXP - where ISPs connect their networks to exchange traffic)
		- within each network, routers switch packets
		- between networks, traffic exchange is set by business agreements
		- customers connect at the edge by many means
			- cable, DSL, fiber-to-the-home, dialup, etc.
	- Data centers concentrate many servers ("the cloud")
	- most traffic is content from data centers
	- The architecture continues to evolve

## What's the Internet? 
- millions of connected computing devices
	- hosts = end systems
	- running network apps
	- ex. PC, smartphone
- communication links
	- fiber, copper, radio, satellite
	- transmission rate: bandwidth
- packet switches
	- forward packets (chunks of data)
	- routers and switches
- Internet: "network of networks"
	- interconnected ISPs
- Protocols:
	- control sending and receiving of messages
	- example: TCP, IP, HTTP, Skype
- Internet Standards
	- RFC: request for comments
	- IETF: Internet engineering task force

## Internet Architecture
- internet structure: network of networks 
	- end systems connect to the Internet using access ISPs (Internet Service Providers)
		- Residential, company, and university ISPs
	- Access ISPs in turn must be interconnected
		- so that any two hosts can send packets to each other
	- Resulting network of networks is very complex
		- Evolution was driven by economics and national politics

- question: given millions of access ISPs, how do we connect them together? 
	- option: connect each access ISP to every other access ISP
		- connecting each access ISP to each other directly doesn't scale well: O(n^2) connections
	- option: connect each access ISP to a global transit ISP? customer and provider ISPs have economic agreement
		- but if one global ISP is a good business, there will be more competition, which must also be interconnected (using IXPs - internet exchange point)
		- and regional networks may arise to connect access points to ISPs
		- and content provider networks (Google, Microsoft, Akamai, etc.), may run their own network to bring services and content closer to end users
![[Pasted image 20240108192024.png]]

STOPPED HERE AT SLIDE 29


## Internet Architecture
- network of networks 
	- small number of well-connected large networks
		- "tier-1" commercial ISPs (such as Level 3, Spring, AT&T, etc.), which give national or international coverage
		- content provider network (such as Google), private network that connects its data centers to Internet, often by passing tier-1, regional ISPs


## Internet
- Network service provider (NSP)
	- provides the backbone (WAN) connections over large geographical area





## Cloud Computing
- large format of servers, that are available to deliver services for customers 
- sometimes they give you free services to work with or sometimes some other software to work with as well
- sometimes you can build your own servers as they provide a platform
- 'hardware on the cloud' instead of owning hardware
- also gives networking capabilities to connect many servers together
	- can think of building networks within a cloud


## Network Security 
- many hackers try to steal information from your machine
- sometimes will not allow you to run your business
- they can put malware into your computer using the Internet 
	- virus: self-replicating infection by receiving/executing object (e.x. an email attachment)
	- worm: self-replicating infection by passively receiving object that can execute itself
- sometimes they may use your computer as a bot in a botnet 
- infected host can be enrolled in a botnet, and then used for spam

- it is also possible for attackers to get your data
- especially on a public network
- if you send your data to your server, or even through the internet, there is a chance of it getting intercepted which leads to the hacker getting your information


- ID Spoofing 
	- send packet with false source address
	- they use fake addresses, in order to fool the people who track this traffic
	- they don't use their own IP or mac addresses


## Wireless Networks
- they use WiFi, which is the IEEE802.11 network
- they use the ISM bands
	- they are reserved for free use
	- 902-928 MHz
	- 2.4-2.5GHz
	- and one more 
	- these are the frequencies that we can use for free

- signals in the ISM band vary in strength 
	- sometimes because of multipath fading because of reflections
- when you can't get a wifi signal, that usually  means that all the signals are bouncing off each other
	- if you  move a little bit and get a better signal, that means that the signal got better
- the longer the distance, the worse the signal 
	- this distance where you are still able to get a strong signal is called a 'radius' or 'range'

## RFID and Sensor Networks
- passive UHF RFID networks every objects
	- tags are placed on objects
	- they generate a small electric force in that tage 
	- when something comes into that force (fixing a circuit) it sends the tag id to the reader, so they can communicate
	- this means that you can share information by tapping two objects together (for example, tap-to-pay)
- Sensor networks:
	- communicate with other devices as well


## Metric Units 
- the power of 10 when talking about rates 
	- 1 Mbps = 1,000,000 bps 
- use powers of 2 for storage 
	- 1 KB 

