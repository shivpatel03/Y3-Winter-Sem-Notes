# The Data Link Layer 

# Where is the link layer implemented?
- The link layer implemented in the "adapter" (NIC) and OS driver
	- ethernet card
- combination of hardware software firmware 

# The Data Link Layer 
- uses physical layer services to give frames of information over a single link
- has functions:
	- takes data from IP layer and turns into a frame
	- handles transmission errors
	- regulates flow of data
	- provides service to network layer
		- sharing broadcast channel: multiple access
		- link layer addressing


- Frames:
	- this layer accepts packets from network layer, encapsulates into frames that sends using the physical layer to a physically adjacent node over a link
		- MAC addresses used in frame headers to identify source and destination
	- sending side: encapsulates the datagram into frame and adds error checking bits, flow control, etc.
	- receiving side: looks for errors, flow control, extracts datagram, passes to upper layer at receiving side 

- Framing methods:
	- data link breaks up bit stream into frames
		- compute a short token for each frame
		- attach to frame when transmitted
	- how to put bits into frames
		- byte count
		- flag bytes with byte stuffing
		- flag bits with bit stuffing
		- physical layer coding violations
			- use non-data symbol to indicate frame
			- such as 4B/5B system: use some unused symbols as a delimiter

	- Byte count:
		- uses a field in the header to store number of bytes
			- simple, difficult to resync after error
		- method is rarely used on it's own
	- Byte stuffing: 
		- special flag bytes delimit frames, used as both the starting and ending delimiter
			- two flag bytes indicate end of one frame and start of next
		- occurrences of flag itself in the data must be stuffed (escaped)
			- longer, easy to resynchronize
		- ![[Pasted image 20240214182555.png]]
		- ![[Pasted image 20240214182725.png]]
	- Bit stuffing 
		- done at bit level
			- frame flag has six consecutive 1s
			- on transmit, after five 1s in the data, a 0 is added
			- on receive, a 0 after five 1s is deleted
		- ![[Pasted image 20240214182839.png]]

# Synchronization 
- Bit (clock) synchronization
	- clock synch between transmitter and receiver required for receiver to extract data from received waveform
	- example

- Asynchronous Transmission 
	- not synched
	- one character at a time
	- stop and start bits used to provide bit and character synch
	- when start is read, read data until stop bit is seen 
- Synchronous Transmission
	- synched clocks
	- no start/stop
	- used in all high-speed transmission
- USB-2 (high speed transmission: 480 Mbps)
	- differential coding: 
		- 0 represented by rectangular pulse which has opposite polarity of previous pulse 
		- 1 represented by rectangular pulse which has the same polarity of previous pulse
- Clock and frame synch
	- K: negative polarity
	- J: positive polarity
	- sends 15 J-K pairs
	- and one KK pair 

- 