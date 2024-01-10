Syllabus overview


# Introduction
## What is an operating system? 
- program that works in between the user of a computer and the computer hardware
- operating system goals: 
	- execute user programs
	- make system convenient
	- use computer hardware efficiently
- some operating systems are meant to be more convenient, while some are meant to be more efficient (mobile OS vs mainframe OS), and others are some combination of these two

## Computer System Structure
- contains 4 components
	- Hardware gives basic computing resources
	- Operating System
		- controls the use of hardware among application and users
	- Program Applications:
		- define the ways that system resources are going to be used to solve a users' problem
	- Users
		- people, machines, other computers

## What Operating Systems Do
- Explore the operating systems from two viewpoints
1. User View;
	- want ease of use, convenience, performance
		- don't care about resource utilization
	- users of dedicated systems such as workstations have dedicated resources but frequently used shared resources from servers
	- handheld computers (phones) are resource-poor, optimized for battery life and usability
	- some computers have very little user interface, such as embedded systems in cars
2. System View 
	- OS is the program that most intimately involved with the hardware
	- can see OS as a:
		- resource allocator: 
			- manages all resources
			- decides between conflicting requests for efficient and fair resource use
		- control program
			- controls the execution of user programs to prevent errors and improper use of the computer

## What is an Operating System? 
- no universally accepted definition
- "everything a vendor ships when you order an operating system"
- since hardware on its own is not easy to use, it application programs are created
- programs require operations, for example using I/O devices
- the function of controlling and allocating resources are brought together into one piece of software, called the operating system
- Definition:
	- Kernel: the one program running at all times on the computer
	- and two other types of programs:
		- system program (comes with operating system)
		- an application program

## Computer System Organization 
- Computer system operation:
	- one or more CPUs: 
		- there is a device controller for every CPU
		- device controllers through common bus that provide access to shared memory
	- the CPU and the device controllers can execute in parallel, competing for memory cycles

	- I/O devices and the CPU can execute concurrently
	- each device controller is in charge of particular device type 
	- each device controller has a local buffer
	- CPU from data from/to main memory from local buffers
	- I/O is the from the device to local buffer of controller
	- device controller informs CPU that it has finished its operation by causing an interrupt

	- for a computer to start running, you need an initial program to run
	- Bootstrap program is loaded at power-up or reboot
		- usually stored in ROM or EEPROM
		- loads operating system kernel and starts execution
		- initialize all aspects of the system
		- some services are not stored in the kernel
			- by system programs that are loaded into memory at boot type to become system processes, that run the entire time that the kernel is running
			- basically a code in the kernel that runs other services that are not in the kernel
				- when the kernel stops, this code also ends and you are no longer getting these programs

	- operating system is interrupt driven
		- event signaled by an interrupt, from either the hardware or the software
			- hardware triggers interrupt by sending a signal to the CPU
			- software triggers interrupt by executing a special operation called a system call
		- interrupt transfers control to the interrupt service routine generally, through the interrupt vector, which contains the addresses of all service routines
		- a trap or execution is a software-generated interrupt caused either by an error or a user request


	- interrupt handling 
		- OS saves the state of the CPU by storing registers and the program counter
		- OS determines which type of interrupt was used
			- polling
			- vectored interrupt system
		- separate segments of code determine what action should be taken for a type of interrupt

	- storage structure
		- main memory: large media that the CPU can access directly, random access, usually volatile
		- secondary storage: extension of main memory that gives more non-volatile storage
		- hard disks: glass platters covered in magnetic recording material
			- each disk surface divided into tracks, which is also subdivided into sectors 
			- one disk controller determines the logical interaction between the device and computer
		- solid state drives
			- various technologies
			- more popular
			
	- Storage Hierarchy
		- storage systems can be organized in a hierarchy according to speed and cost
		- organized hierarchy differs in speed, cost, and volatility
		
	- caching 
		- copying information into faster storage system
		- performed at many levels in a computer
		- info is copied from slower to faster memory
			- faster storage is checked first to see if it's already there
			- if not, data is copied to cache and used there
		- cache is much smaller than the storage that is being cached
			- cache management is important design problem
		
	- Storage definition and notation review
		- basic unit of computer: bit 
		- byte = 8 bits
		- word (native unit of data).  made up of one or more bytes
		- computer storage is is generally measured and manipulated in bytes and collections of bytes

	- I/O Structure
		- general purpose computer system has CPUs and many device controllers
		- each device controller in charge of specific devices
		- OS have a device driver for each device controller to manage I/O
	
		- interrupt driven I/O is good for moving small amounts of data
			- loads appropriate registers in the device controller
			- device controller decides the action to take
			- when device controller informs the devices to local buffer
		- not good for lots of data because of high overhead
			- direct memory access is used (DMA)
	
	- Direct memory access Structure
		- used for high-speed I/O devices
		- device controller blocks of data from buffer storage directly to main memory without CPU intervention
			- sent in groups (blocks), faster
			- rather than sending checking byte by byte, which is bad for faster I/O devices
	
	- Single Processor Systems
		- most systems use a single general-purpose processor
			- most systems have special-purpose processors as well
				- for keyboards, disks
	- Multiprocessor systems growing in use
		- known as parallel or multicore systems
		- have two or more processors in communication, sharing resources
		- advantages:
			- increased throughput: does more in less time
			- economy of scale: costs less
			- increased reliability: graceful degradation and fault tolerance
	
	- multiple processor systems are of two types:
		- asymmetric multiprocessing: each processor has one task
			- boss-worker relationship 
				- boss processor schedules and allocates work to worker processors
		- symmetric multiprocessing (SMP)
			- most common
			- all processors are peers, each processor performs all tasks
			- symmetric multiprocessing architecture

	- multi-core CPUs
		- more efficient than multiple chips with single cores
			- on-chip communication faster than between-chip communication 
		- uses less power than single-core chips

	- clustered systems
		- like multiprocessor systems, except multiple systems are working together
		- share storage using a storage-area-network (SAN)
		- some clusters for high performance computing 

- important aspects of operating systems
	- multiprogramming: needed for efficiency
		- single user cannot keep CPU, I/O devices busy at all times
		- multiprogramming organizes jobs so CPU always has one to execute
		- subset of total jobs in system is kept in memory
		- one job selected and run via job scheduling
		- when it must wait, OS switches to another job
	- timesharing is a logical extension to multiprogramming
		- CPU switches jobs so that frequently users can interact with each job while it is running, creating interactive computing 
		- response time should be less than 1 second
		- each user has at least one program executing in memory -> process
		- if several jobs ready to run at the same time -> CPU scheduling
		- if processes don't fit in memory, swapping moves them in and out to run
		- virtual memory allows execution of programs that are larger than actual physical memory

- Modern operating systems are interrupt driven
	- if there are no processes, no I/O devices, and no users to respond to, the OS will sit and do nothing until an interrupt occurs
	- interrupt driven by hardware or software
		- hardware interrupt from one of the devices
		- software interrupt (trap or exception) such as:
			- software error (division by 0)
			- request for operating system service
			- other process problems (infinite loop, processes modifying each other, or even OS itself)

- Dual-mode and multi-mode operation
	- to make sure we get the proper execution of the OS, must be able to distinguish between execution of operating system code and user-defined code
	- therefore, computer systems provide hardware bit to differentiate among various modes of execution
	- dual mode operation allows OS to protect itself and other system components
		- user mode and kernel mode (called supervisor, system, or privileged mode)
		- mode bit provided by hardware (kernel 0, user 1)
			- differentiates between system code and user code
			- come instructions are designated as privileged, only executable in kernel mode (such as switch mode, I/O control, timer management, and interrupt management instructions)
	- transition from user to kernel mode
		- system call changes mode to kernel, return from call resets it to user
	![[Pasted image 20240109210847.png]]
	