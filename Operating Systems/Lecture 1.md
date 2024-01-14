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
	- The concept of modes can be extended beyond two modes 
		- better CPUs support the use of multi-mode operations 
		- CPU uses more than one bit to set and test the mode 
		- example:
			- CPUs that support virtualization frequently, have a separate mode to indicate when the virtual machine manager and the virtualization management software is in control of the system
			- in this mode, the VMM has more privileges than user processes but fewer than the kernel

# Operating System Operations
- Transition from User to Kernel Mode
	- to ensure that the operating system maintains control over the CPU, times are used
	- Timer is used to prevent the user program to get stuck in an infinite loop or processes hogging resources
		- timer is set to interrupt to computer after some period of time 
		- keeps a counter that is decremented by the clock
		- operating system set the counter
		- when it reaches zero, it generates an interrupt 
		- set up before scheduling process to regain control or terminate program that exceeds allocated time 
# Process Management 
- A process is a program in execution. it is a unit of work inside of the system
	- program is a passive entity, process is an active entity
- process needs resources
	- CPU, memory, I/O, files 
	- initialization data
- process termination requires reclaim of any reusable resources
- single-threaded process has one program counter specifying the location of the next instruction to execute
	- process executes instructions sequentially, until completion
- multi-threaded process has one program counter per thread
- typically, a system has many processes, some user, some operating system running concurrently on one or more CPUs
	- concurrency by multiplexing the CPU among the processes/threads
## Process Management Activities
- The operating system is responsible for the following activities for process management
	- scheduling processes and threads on the CPUs
	- creating and deleting user and system processes
	- suspending and resuming processes
	- providing mechanisms for process synchronization and communication
	- providing mechanisms for deadlock handling

- To execute a program, all (or only a part) of the instructions have to be in memory
- all of the data needed for that process to run must also be in memory
- memory management determines what is in memory and when
	- optimizing CPU utilization
- creates the need for memory management
	- memory management keeps track of which parts of memory are currently being used and by who
	- deciding which processes and data to move in and out of memory
	- allocating and deallocating memory space as needed

# Storage Management 
- Operating systems provide a uniform, logical view of information storage
	- abstracts physical properties to logical storage unit - files
	- each medium is controlled by a device
		- varying properties include access speed, capacity, data-transfer rate, access method (etc.)
- File Management system
	- one of the most visible components of an OS
	- files usually in directories
	- access control on most systems to determine who can access what 
	- operating system activities include: 
		- creating and deleting files and directories
		- support primitives to manipulate files and directories
		- mapping files onto secondary storage
		- backup files on the stable storage media
## Mass-Storage Management 
- Usually, disks used to store data that does not it in main memory or data that must be kept for a "long" period of time 
- proper management is needed
- the speed of the computer depends heavily on the disk subsystem and algorithms
- operating system is responsible for:
	- free-space management
	- storage allocation
	- disk scheduling
- some storage need not be fast 
	- tertiary storage includes optical storage (CDs and DVDs), magnetic tape
		- still managed by OS or applications
		- varies between (write-once, read-many-times) and (read-write) formats (WORM and RW, respectively)
## Caching 
- Information normally kept in main memory, but when it is used it is copied into a faster storage system, called the cache, temporarily 
- cache management is an important design problem
	- cache size and the replacement policy can result in greatly increased performance
- main memory can be viewed as fast cache for secondary storage 

## Cache Coherency 
- in a hierarchical storage structure, the same data may appear in different levels of the storage system
- example:
	- going from Disk to Register:
	- goes from hard disk, to main memory, to cache, and then to hardware register
	- it is important for multitasking environments to careful to use the most recent value, no matter where it is stored in the storage hierarchy 
	- multiprocessor environment must provide cache coherency in hardware so that all CPUs have the most recent value in their cache
	- distributed environment situation is more complex 
		- several copies of data can e kept in different computers
		- distributed systems must ensure that, when a replica is updated in one place, all other replicas are brought up to date

## I/O Systems
- one purpose of the Operating System is to hide specifics of the hardware devices from the user
- I/O subsystems have many components 
	- memory management of I/O (buffering - storing data temporarily while it is being transferred), (caching - storing parts oft data in faster storage for performance), (spooling - the overlapping of output of one job with input of their jobs)
	- general device-driver interface
	- drivers for specific hardware devices
- only the device driver knows the specifics of the device that it is assigned to



# Protection and Security
- protection: any mechanism for controlling access of processor or users to resources defined by the Operating System (can be thought of as internal affairs)
- security: defense of the system against internal and external attacks (can be thought of as external affairs)
	- large range, including worms, viruses, etc,. 
- systems generally first distinguish among users, to determine who can do what 
	- user identities include name, associated number, one per use
	- user ID associated with all files, processes of that user to determine access control
	- group ID allow set of users to be defined and controls managed
	- privilege escalation allows user to change to effective ID with more rights

# Kernel Data Structures
- lists, stacks, and queues
	- an array is a simple data structure
		- main memory is constructed as an array, for example 
	- list is the most fundamental data structure in computer science 
		- must be accessed in a particular order 
		- linked list is the most common method for implementing it
		- lists are used for constructing more powerful data structures, such as stacks and queues
- Stacks: 
	- sequentially ordered, uses last in first out (LIFO) principle 
- Queues: 
	- sequentially ordered, uses first in first out (FIFO)
- Tree:
	- DS that can be used to represent data hierarchically 
	- data values in the tree structure are linked through parent child relationships 
	- binary tree: parent can only have at most two children
	- binary search tree: the left child is going to be less than the part of this child, and the right child will be greater than the parent of this child 
		- search performance is O(n)
	- an algorithm can be used to create a balanced binary search tree: 
		- a tree that has n items has at most log_2(n) levels 
		- search performance is O(log_2(n))


STOPPED AT SLIDE 45 OF THE SLIDESHOW