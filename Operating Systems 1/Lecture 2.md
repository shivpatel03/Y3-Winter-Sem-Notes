# Operating System Services 
- provide environment for execution of programs
- can study:
	- the services that it provides
	- the interface that the OS provides to users/programmers
	- OS components and interconnections

1. User Interface: almost all of them have a UI,
	1. command line, graphics user interface, batch interface (commands entered into files to be executed)
2. program execution: system must load program into memory, run that program and then end execution
3. I/O Operations: program may need IO, which may need a file or an IO device
4. file system manipulation: programs need to read/write files into/out of directories,
	1. also search, delete, create, list information, etc.
5. communications: processes need to send information to each other. can do this by shared memory or message passing
6. error detection: OS needs to be aware of possible errors
	1. can occur in CPU or memory hardware, OS should take proper action to ensure correct computing
	2. debugging helps users and programmers use the system more efficiently
7. resource allocation: when many users or jobs are running at once, resources have to be allocated to each
8. accounting: keep track of how many and what resources are being used by a user
9. protection and security:
	1. protection: controlling access to system resources
	2. security: securing the system from outsiders, adds user authentication, defending external IO devices from invalid access attempts

# User and Operating System Interface
- command interpreters
	- CLI: direct command entry (terminal)
		- sometimes in kernel, sometimes by system program
		- many versions called "shells"
		- in UNIX and Linux, many shells:
			- Bourne
			- C Shell
			- Bourne-again Shell
			- Korn shell
- Graphical User Interface (GUI)
	- user friendly desktop metaphor interface
		- uses mouse, keyboard, monitor
		- icons represent files
	- many systems now include a CLI and a GUI
		- Windows
		- Mac
		- Unix
- Touchscreen:
	- require different interfaces than normal PC
		- mouse not possible
		- gestures
		- virtual keyboard
	- voice commands

# System Calls
- allow kernel services to be made by an OS
- usually used by programmers through Application Programming Interface (API)
	- library, called `libc` in UNIX/Linux
- 3 most common APIs:
	- Win32 API for Windows
	- POSIX API for POSIX-based systems
	- Java API for JVM (Virtual machine)

## Example: 
- if you want to copy the contents of one file into another this is a line of system calls that you would probably have to make:
	- ***get input name***
	- write prompt to screen
	- accept input
	- ***acquire output file name***
	- write prompt
	- accept input
	- ***open the input file***
	- check for error in opening
	- ***create output file***
	- check for error in opening
	- ***loop***
	- read from input file
	- write to output file
	- ***until read fails
	- ***close output file
	- ***write completion message to screen
	- ***terminate normally***

- System call implementation
	- usually a number is associated with the system call
		- **System call interface** is a table that is indexed by these numbers
	- interface invokes the corresponding call in OS kernel, returns status of the system call
	- caller needs to know nothing about how the system call is implemented
		- abstraction
		- just needs to understand what the output would be and obey the API
- Can think of a system call as a way to bridge the gap between user and kernel modes

## System Call Parameter Passing 
- sometimes need more information than just the call itself
- three general methods used to pass parameters
	- passing parameters in registers
		- simplest, but may need more parameters than registers
	- parameters stores in a block or table, in memory, and address of the block is passed as a parameter in a register
	- parameters placed, or pushed onto the stack by the program
		- when the OS uses it, it is popped off
	- block and stack methods do not limit the number or size of parameters being passed in

# Types of System Calls 
- Six major categories
	- process control 
		- create process, end process
		- debugger ford determining bugs, or single step execution
		- locks for managing access to shared data between processes
			- `acquire_lock() and release_lock()`
	- file manipulation
		- create, delete, open, close, read, write, get, set, etc.
	- device manipulation
		- may need many resources to execute such as main memory, disk drives, access to files
	- information maintenance
		- needed for transferring information between user program and OS
			- get time/date, set time/date
			- get system data, set system data
			- get and set process, file, or device attributes
	- communications
		- create, delete communication connection
		- two common methods of communication
			- message-passing: exchange smaller amounts of data
				- send/receive message to host or process name
			- shared-memory model: for communication on the same computer
				- create and gain access to shared memory regions
	- protection
		- control access to the resources
			- get and set permissions
			- allow and deny user access

# System Programs
 - provide convenient environment for program development and execution
 - some programs are user interfaces to system calls
 - some are more complex
 - divided into :
	 - file management
		 - create, delete, copy, rename, etc.
		 - manipulate files and directories
	 - status information
		 - programs that ask system date/time/amount of available memory/disk space/number of users
		 - formatted and printed to terminal
		 - some systems have registry which is used to store and receive configuration information
	 - file modification
		 - text editors to create/modify files
	 - programming language support
		 - compilers, assemblers, etc.
	 - program loading and execution
		 - provide loaders, linkage editors, etc.
	 - communications
		 - provide creation of virtual connections among processes, users, and computer systems
			 - allow users to send messages to one another's screens, browse web, etc.
	 - background services
		 - launched at boot time
			 - some create system startup, and then die
			 - some work from boot to shutdown (a.k.a. daemons or services)
				 - run in user context
				 - known as services, subsystems, daemons
	 - application programs
		 - don't pertain to the system
		 - not considered part of the OS
		 - run by command line, mouse click, or tap on a screen

# Operating System Design and Implementation
- creative task for software engineering
- principles for designing an OS:
1. design goals
	1. internal structure of OS can vary
	2. defining the goals and specifications is a good way to start
		1. choice of hardware, type of system, etc.
	3. requirements are hard to find but can be of the two:
		1. user goals
		2. designer goals
2. Separation of mechanisms and policies
	1. policy: what will be done? 
	2. mechanism: how to do it?
3. Implementation
	1. variation; 
		1. early OS written in assembly
	2. mix of languages
		1. lowest levels in assembly
		2. main body in C
		3. systems programs us C and scripting languages like PERL, Python, shell scripts 
	3. more high level language is easier to port to other hardware
		1. but is slower and increase storage requirements

# Operating Systems Structure 
- general purpose OS is a large program, must be made carefully
- partition task into small modules
- various ways to structure OS
	- Simple structure
	- more complex like UNIX
	- layered - an abstraction
	- microkernel - Mach

- Simple structure MS-DOS
	- written to give the most functionality in the least space
		- not mode into modules
		- interfaces and levels are not well separated
			- makes system more vulnerable to malicious programs and crashes
- Traditional UNIX 
	- not simple and not fully layered
	- original was limited by hardware, had limited structuring
	- consists of two separate parts:
		- system programs
		- the kernel
			- has everything we know about the system-call interface
			- provides file system, CPU scheduling, etc.
- Traditional UNIX System Structure
	- beyond simple but not fully layered
![[Pasted image 20240210204420.png]]
- Layered Approach
	- OS divided into layers
		- Bottom layer is the hardware (layer 0)
		- highest layer is user interface (layer N)
	- layers are selected in a way that each one only uses functions and services of only the lower-level layers
- Microkernel System Structure 
	- moves all nonessential components from kernel and implements them as system and user-level programs
	- communications take place between user modules using **message passing**
	- pros: 
		- easy to extend (add features)
		- easy to port OS to new architectures
		- more reliable, scure
			- less code running in kernel mode
	- cons: 
		- performance overhead of user space to kernel space communication
	- Basically, the application programs, file system, and device drivers are not all in the kernel mode anymore, they are in the user mode
		- they do not lie in the kernel anymore
- modules
	- many OS now use loadable kernel modules
		- object oriented -> each component is separate
			- each talks to each other using known interfaces
			- each is loadable as needed within the kernel
	- similar to layers but with more flexibility
	- Solaris Modular Approach 
		- organized around a core kernel with seven types of loadable kernel modules
	![[Pasted image 20240210204926.png]]
- Hybrid Systems 
	- most OS's now are not just one system
	- examples:
		- Linux and Solaris kernels are monolithic, plus modular for dynamic loading of functionality
		- windows mostly monolithic, plus microkernel for different subsystem known as **personalities**
	- Mac OS X is hybrid, layered, using Aqua UI plus Cocoa programming environment
	- android
		- open sourced
		- similar to iOS in layered architecture
		- based on Linux kernel modified by Google for power management, device-driver management, and process management
		- includes a set of libraries and Dalvik virtual machine 

# Operating System Debugging 
- finding errors and fixing them (definition of Debugging )
- OS generate log files which include information about errors
	- generate **core dump** in the event of an **application failure**
	- **operating systems** failing will generate **crash dump**
- performance tuning can be used to optimize system performance
	- profiling is periodic sampling of instruction pointer to look for statistical trends
- performance tuning
	- improve performance by removing bottlenecks
	- OS gives a way to compute and display measurements of system behavior
		- `top` in UNIX is a command that will show processes that are using resources
		- windows task manager shows information about current processes, apps, etc.

# Operating System Generation
- designed to run on any class of machine
- system must be configured for each computer site
- `system generation SYSGEN` is a program that gets information about hardware configuration of the machine that it is on
	- determines components that are on the machine
		- does this by either reading a file or asks operator about the hardware system, or even checks the hardware directly
	- the following kinds of information are needed;
		- what CPU
		- how will the boot disk be formatted
		- how much memory available
		- what operating system options are desired, or what parameter values are to be used?

# System Boot 
- when power is initialized on a system, executions starts at a fixed memory location
- operating system must be made available to hardware so hardware can start it
	- small piece of code - bootstrap loader stored in ROM or EEPROM locaters the kernel, and loads it into memory, and starts it
	- sometimes boot block at a fixed location will be loaded by ROM code, which loads the bootstrap loader from disk, which will load the kernel
- GRUB is a common bootstrap loader in Linux, allows selection for kernel from multiple disks, versions, kernel options
- when the kernel is loaded, the system is said to be "running"


# iOS vs. Android
- same: 
	- both are based on existing kernels (Linux and Mac OS X)
	- both have architecture that are software stacks
	- both provide frameworks for developers
- differences: 
	- iOS close sourced, Android open
	- iOS applications are developed in Objective-C, android in Java
	- Android uses a VM, iOS executed code natively