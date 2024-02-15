# The Physical Layer
- foundation for other layers
	- properties of wire, fiber, and wireless define what the network can do
	- determines throughput, latency, error rate of network communication link
- key problem is to send bits using only analog signals
	- this is called modulation

# Theoretical Basis for Data Communication 
- information can be transmitted on wires by varying some physical property such as current, voltage, frequency, or phase
## Bandwidth
- to electrical engineers, bandwidth is a quantity measured in Hz
- to computer scientists, digital bandwidth is the maximum data rate of a channel, in bps

## Fourier Analysis 
- time varying signals can be represented by infinite number if sines and cosines
- signal period is T, so fundamental frequency is f = 1/T
![[Pasted image 20240214120018.png]]
## Bandwidth-Limited Signals
- consider the transmission of "b" = "01100010"
- having less bandwidth, we loose some of the harmonics
	- degrades the received signal
- having less harmonics harmonics gives us a much less accurate message of "b"
	- with 8 harmonics:
![[Pasted image 20240214120159.png]]
- with 4 harmonics
![[Pasted image 20240214120218.png]]
- with harmonics
![[Pasted image 20240214120238.png]]

# Guided Transmission media (Wires and Fiber)
- Media have different properties, performance is in terms of bandwidth, delay, cost, ease of installation, maintenance
- Two groups
	- Guided media
		- Copper wire
			- twisted pairs
			- coaxial cable
			- power lines
		- fiber optics 
			- single mode
			- multimode
	- unguided media
		- terrestrial wireless
		- satellite
		- lasers through air

## Wires - Twisted Pairs
- two wires
	- twists lower interference
	- signal carried as difference in voltage between two wires
	- bandwidth depends on wire thickness and distance travelled
	- comes in several categories:
		- Cat 5: 4 twisted pairs grouped together:
			- 100Mbps ethernet uses two of the four pairs
			- 1-Gbps ethernet uses all four pairs in both directions together
		- Cat 6: 10gbps, has more stringent specifications for crosstalk and system noise, up to 100m
			- UTP (unshielded twisted pair)
		- Cat 7: STP (shielded twisted pair)
## Link Terminology
- Full duplex
	- used for transmission in both directions at the same time
	- example: use different twisted pairs for each direction
- half-duplex
	- both directions, but not at same time
	- example: senders take turns on a wireless channel
- simplex:
	- only one fixed direction at all times, not common

## Wires - Coaxial Cable ("Co-ax")
- two concentric copper conductors
- common but expensive than twisted pair
- better shielding for long distances
- common uses are cable TV because it needs larger bandwidth
- bidirectional, broadband (multiple channels on cable)
- two types: 
	- 50-ohm: used for digital transmission
	- 75-ohm: used for analogue transmission (TV cable)
		- now used for digital and analog

## Wires - Power Lines 
- household wiring is example of wires
	- convenient, but bad for sending data
	- electricity is at 50-60Hz
	- Data is much higher frequency

## Wires - Fiber Optics Cable 
- Glass fiber carrying light pulses, each pulse is a bit
	- pulse of light is 1, absence of light is 0 bit 
- used for high speed point-to-point transmission (10s-100s Gpbs)
- low error rate, so repeaters spaced far apart
	- light immune to electromagnetic noise
- common for high data rates and long distances
	- long distance ISP links and fiber-to-the-home 
	- light carried in very long thin strand of glass 
- has three components: light source, transmission medium, and detector
	- the detector generates a pulse light falls on it 


- single mode: 
	- core so narrow that light cannot bounce around at all 
		- used with lasers for long distances (100km)
- multi mode: 
	- core diameter is bigger
	- light can bounce, each ray above the critical indent is said to have a different mode
	- used with LED's for cheaper and shorter distance links

^ THE CORE IS THE GLASS STRAND FROM EARLIER
# Network Topology 
- how are so many computers connected together? 
	- three various configs
		- bus topology: nodes are connected to single communication line
			- simple, low cost
			- a single cable needed (called a trunk)
			- only one computer can send messages at a time 
			- passive topology, computer only listen for, not regenerate data
			- ![[Pasted image 20240214121902.png]]
		- star topology: centers around one node, and all others are connected through which all messages are sent 
			- each computer has a cable to a single point
			- more cabling, higher cost 
			- transmission done through hub (switch)
				- if that switch goes down, entire network goes down
			- depending on intelligence of hub, two or more computers may send messages at the same time
			- ![[Pasted image 20240214122016.png]]
		- ring topology: config that connects all nodes in a closed loop, messages only travel one direction
		- every computer is a repeater to boost signals
		- typical way to send data is Token passing
			- only computer who gets the token can send data
		- cons: 
			- if one computer fails, whole network fails
			- harder to add more computers
			- more expensive

# Network Hardware
 - network interface cards: 
	 - network adapter
	 - connects node to media
	 - unique machine access code (MAC address)
		 - 6 bytes long 
 - network linking devices
	 - connect devices in a network
	 - cable runs from node to device 
	 - crossover cable connects two computers together 
	 - hub: 
		 - center of star network
		 - all nodes receive transmitted packets
		 - slow, insecure
	 - switches
		 - replacement for hubs
		 - only intended node gets the transmission 
		 - fast and secure 
	 - router
		 - connects two or more LAN's together
		 - packets sent to remote LAN will cross
		 - network segmented by IP addresses
		 - connect internal networks to Internet
		 - need to be configured before installation 
	 - gateway
		 - connects two different networks
		 - connects coax to twisted pair 
		 - most gateways contained in other devices 

# Wireless Transmission 
- electromagnetic spectrum
	- signal carried in electromagnetic spectrum
	- number of oscillations per second is called frequency (F) measured in Hz
	- time between two consecutive maxima (or minima) called period T (T=1/f)
	- distance between two consecutive maxima or minima called wavelength $\lambda$
	- electromagnetic waves travel at speed of light $c=3*10^8\text{m/s}$
	- relationship between $f$ $\lambda$ and $c$ (in a vacuum) is $\lambda=\frac{c}{f}$
	- 
- radio transmission
- microwave transmission
- light transmission
- wireless vs. wires/Fiber
	- wireless:
		- + easy and cheaper
		- + naturally supports mobility 
		- + naturally supports broadcast
		- - transmission interference must be managed
		- - signal strengths hence data rates vary greatly
	- wires/fiber
		- + easy to engineer a fixed rate over point to point links
		- - expensive, especially over details
		- - doesn't readily support mobility or broadcast

- wireless access networks
	- shared access networks across end system to router 
	- Wireless LANs
		- within building (100ft)
		- 802.11g/n/ac (WiFi): 54/300/1000 Mbps transmission rate
	- Wide area wireless access
		- Provided by telecom (cellular) operation, 10's of Km 
		- between 1 and 100 Mbps and more
		- 3G, 4G: LTE


# Digital Modulation and Multiplexing
- Digital Modulation 
	- process of converting data bits into signals that networks can send and understand
	- baseband transmission 
		- signal uses frequencies of 0 to maximum
		- common for wires 
	- passband transmission
		- regulate phase, amplitude, frequency of carrier signals to convey bits
		- occupies a band of frequencies around the frequency of the carrier signal
			- common for wireless and optical channels 

## Baseband Transmission 
- NRZ (Non Return to Zero):
	- uses positive voltage to represent 1 and negative to represent 0
	- can use more levels of voltages, then the symbol carries more bits (symbol rate = baud rate)
- Manchester encoding:
	- mixes clock signals wit the digital signal using XOR
		- XOR's them together
	- when the clock is XORed the 0 level makes a low-to-high transition -> a logical 0
	- when XORed with the 1 level, it is inverted and makes a high-to-low transmission -> a logical 1
- NRZI (non return to zero inverted)
	- uses same as NRZ but positive represents 0 and negative 1

- 4B/5B coding scheme
	- used to limit the number of consecutive 0s or consecutive 1s
	- every 4 bits is mapped into a 5bit pattern with a fixed translation table
- 4B is the "data" and 5B is the "codeword"


# Public Switched Telephone Network 
- Local Loop: Digital Subscriber Lines
	-  DSL broadband sends data over the local loop to the local office using frequencies that are not used for POTS
	- uses telephone line to central office DSLAM (DLS access multiplexer)
		- data over digital subscriber lines phone line goes to Internet and voice goes to telephone network
		- < 2.5 Mbps upstream transmission rate
		- < 24 Mbps downstream transmission rate
		- OFDM used up to 1.1 MHz for ADSL2
- Local Loop: Fiber-to-the-Home (FTTH)
	- relies on deployment of fiber optic cables to give high data rates to customers
		- one wavelength shared by many houses
		- fiber is passive
		- up to 100Mbps
		- uses an optical splitter/combiner to share it to separate houses
	![[Pasted image 20240214132322.png]]

# Cable Television 
- Internet over Cable 
	- internet over cable reuses the cable television plant
	- data sent on shared cable from head-end, not dedicated line per subscriber (like DLS)
	- frequency division multiplexing (FDM): different channels transmitted in different frequency bands 


# Enterprise access networks: (Ethernet):
- used in companies, universities, etc.
- 10 Mbps, 100Mbps, 1Gbps, 10Gbps transmission rates 
- today, end end systems usually connect to ethernet switch
![[Pasted image 20240214132542.png]]


# Physical Media
- Host: sends packets of data
- host sending function 
	- takes application message 
	- breaks into chunks (packets), of length L bits 
	- transmits packet into access network at transmission rate R
		- link transmission rate, aka link capacity, aka link bandwidth
		- the transmission delay is the time it takes for the host to send the bits to the access network
	- $\text{Packet Transmission Delay = } \frac{\text{L in bits}}{\text{Rate in bits/sec}}$

- packet switching: store and forward
	- takes L/R seconds to transmit an L-bit packet to a link at R bps
	- store and forward: entire packet must arrive at router before it can be transmitted at next link 
	- end-end delay: 2L/R (assuming no propagation delay)
		- one hop numerical example: 
			- L = 7.5 Mbits 
			- R = 1.5 Mbps
			- one-hop transmission delay = 5 sec
		- $\text{End-to-end delay = }2*\frac{L}{R}$
			- assuming no propagation delay


- packet switching: queuing delay, loss 
	- if arrival rate (in bits) to link exceeds transmission rate of link for a period of time 
		- packets will queue, and wait to be transmitted on the link
		- packets can be dropped (lost) if memory buffer fills up
			- if they are being transmitted slower than they are filling up the buffer, the packet that is coming in will then be dropped because the queue is full
	![[Pasted image 20240214133456.png]]

# Network-Core Functions 
- Two key network-core functions
- Routing: determines source-destination route taken by packets
	- routing algorithms
- Forwarding: move packets from router's input to appropriate router output
	- uses the "local forwarding table" that the router creates which describes which the order in which it should go through machines to get to the final destination address the quickest
	- ![[Pasted image 20240214133702.png]]

- alternative core: circuit switching 
	- end-end resource are allocated and reserved for "call" between source and destination
	- considering this diagram:![[Pasted image 20240214133848.png]]
	- in this diagram, each link gets 4 circuits
		- call gets 2nd circuit in the top link and 1st in the right link
	- circuit segment idle if not used by call (no sharing is being done)
	- commonly used in old telephone networks
# Circuit vs. Packet Switching
- Switching:
	- circuit switching requires call setup before data can flow smoothly
		- and teardown at the end
	- packet switching treats message independently
		- no setup, but variable queueing delay at routers

- packet switching allows for more networks
	- example: 
		- 1 Mb/s link 
		- each user:
			- 100kb/s when "active"
			- active 10% of the time
- circuit switching: 
	- 10 users

- packet switching:
	- with 35 users , probability of having more than 10 active users at the same time is less than 0.0004

- packet switching: 
	- good for "bursty" data
		- resources sharing, and it's simpler with no setup
	- excessive congestion possible: packet delay and loss
		- protocols needed for reliable transfer, congestion control
- how do we provide circuit-like behavior? 
	- bandwidth guarantees needed for audio/video apps


# Delay, Loss, Throughput in Networks 
- How does loss happen? 
	- packets queue in router buffers
		- when a packet arrival rate to link exceeds output link capacity
	- packets queue, waiting for turn

- there are four sources of packet delay
- $d_{proc}: \text{nodal processing}$
	- check bit errors
	- determine output link
	- typically < ms
- $d_{queue}:\text{queuing delay}$
	- time waiting at output link for transmission
	- depends on congestion level of router
- $d_{transmission}: \text{transmission delay}$
	- L: packet length (in bits)
	- R: link bandwidth (in bps)
	- $d_{transmission}=\frac{L}{R}$
- $d_{prop} = \text{propogation delay}$
	- d: length of physical link
	- s: propagation speed in medium: $\text{approx } 2*10^8\text{m/s}$
	- $d_{prop} = \frac{d}{s}$
- $d_{nodal} = d_{proc} +d_{queue}+d_{trans}+d_{prop}$

Queuing delay: 
- R: link bandwidth (bps)
- L: packet length (bits)
- a: average packet arrival rate

- La/R ~ 0: queuing delay is small
- La/R -> 1: average queueing delay increases
- La/R > 1: more "work" arriving that can be serviced, and the average delay may approach infinity

# Delay, Loss, Throughput in Networks
- "Real" Internet delays and routes
- what do "real" Internet delay and loss look like?
	- `traceroute` program provides delay measurements rom source to router along end-end Internet path towards destination, for all i:

- Packet loss;
	- queue (buffer) preceding in buffer has finite capacity
	- packet arriving in full queue will be dropped (lost)
	- lost packet may be retransmitted by the previous node, by source end system or not at all

- Throughput
	- 