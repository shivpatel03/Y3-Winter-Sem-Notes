# Medium Access Control Local Area Networks (LANs)
- There are two types of links
	- point to point
	- broadcast (shared wire or medium)


# The MAC Sublayer (Medium Access Control)
- MAC sublayer is responsible for deciding who sends next on a multi-access link
- important part of the link layer, especially for LANs


# what is LAN? 
- network that connects many computers in small area
- ethernet is most common wired LAN technology


# local area network
- ethernet
	- broadcast network
		- a frame is sent from one station and received by all other connected ones
		- Medium Access Control (MAC) protocol used to control access of common transmission
		- two basic physical topologies: Bus and Star
- bus: 
	- one station can transmit at a time
	- all workstations are connected to each other in a line
	- CSMA/CD protocol used to reduce probability of collision
- star:
	- common transmission medium is a hub (repeater)
	- CSMA/CD protocol used to lower chance of collision
	- all devices are connected to a hub

- switched networks 
	- a switch only sends frames to the intended workstation (broadcast does not do that, it just sends it to everyone)
		- allows for simultaneous transmissions

- mixed networks 
	- combination of broadcast and switched networks


# channel allocation problem 
- MAC protocols: taxonomy
- three broadcast classes
	- channel partitioning (static)
		- divide channel into smaller parts
		- allocate a piece to every node for exclusive one
	- random access (dynamic)
		- channel is not divided, allows for collisions to happen
		- we need to "recover" from collisions
	- "taking turns" (based on a predefined order)
		- nodes take turns to use the channel, but nodes with more data to send can take longer turns

## static allocation
- fixed channel and traffic from N users
	- divide up the bandwidth from FDM, TDM, CDMA, etc.
	- this is a static allocation, example FM radio
- static allocation performs poorly for busty traffic
	- allocation to a user will sometimes go unused
- TDMA: time division multiple access
	- access to channel in "rounds"
	- each station gets fixed length slots ("length" as in packet transmission time) in each round
	- unused slots go idle
- example:
	- 6-station LAN, 1,3,4 have packets to send, slots 2,5,6 are idle

- FDMA: frequency division multiple access
	- channel spectrum is divided into frequency bands
	- each station is assigned a fixed frequency band
	- unused transmission time in frequency bands go idle

- dynamic channel allocation 
	- gives the channel to the user when they need it
	- when a node has a packet to send
		- it will transmit at full channel data rate R
		- there is no prior coordination among nodes
	- two transmission nodes result in collisions
	- random access mac protocol specifies
		- how to detect collisions
		- how to recover from collisions