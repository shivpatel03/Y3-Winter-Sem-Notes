# Processes

# The concept of processes
- OS executes many programs, these are what we call all of the CPU activities
	- batch system: executes jobs (programs) on a computer without manual intervention
	- time-shared systems: executes user programs or tasks at the same time
- "job" and "process" are used interchangeably

- process: program in execution
- the process has multiple parts:
	- code (aka text section)
	- current activity including program counter
	- stack -> contains temporary data
	- data section -> contains global variables
	- heap -> contains memory dynamically allocated during run time
- passive entity stored on disk
	- active with the program counter pointing to the next instruction to be executed
	- program becomes a process when its executable file is loaded into memory
- execution done through GUI or command line entry of it's name
- one program can be of many processes
	- consider many users executing the same program

## Process state
- as the execution of a process continues, the state changes
- may be one of the following states
	- new: process being created 
	- running: instructions are being executed
	- waiting: processes is waiting for some event to occur
	- ready: process waiting to be assigned to a processor
	- terminated: process finished execution

## Process control block
- each process represented by process control block (PCB) that contains: 
	- process state
	- program counter
	- CPU registers
	- CPU scheduling information
	- Memory management information
	- Accounting information: amount of CPU used, time limits, etc.
	- I/O Status information: list of I/O devices allocated to the process

## Threads 
- so far a process is a program that performs a single thread of execution
- most OS's allow for more than one threads of execution to perform more than one task at a time
	- better in multicore systems where multiple threads can run in parallel
	- consider having multiple program counters per process
		- then multiple locations can execute at once
			- multiple threads of control -> **threads**
		- PCB is expanded to include information about every thread
## Process Representation in Linux 
- represented by the C structure `task_struct` stored in `<linux/sched.h>` that has many fields

# Process Scheduling 
- objective of multiprogramming is to have some processes running at all times
- "time sharing" is the idea of switching the CPU among processes
- for a single processor system, you can never run more than one process at a time
- Process Scheduler selects among the available processes for next execution on CPU
	- maintains scheduling queues of processes
		- Job queue: set of all processes in the system
		- Ready queue: set of all processes in main memory, that are ready to execute
		- Device queues: set of processes waiting for an I/O device
			- each device has it's own device queue
- Queuing Diagram: common representation of process scheduling
	- each rectangular box represents a queue
	- circles show resources that serve the queue
	- arrows indicate the flow of processes in the system
- a new process is put into the "ready queue". waits there until selected for execution, one of many things can happen while executing: 
	- processes issues I/O request, placed in I/O queue 
	- process creates a new child process, waits for child's termination
	- process removed from the CPU, as a result of an interrupt 

- Schedulers 
	- short-term scheduler: selects from ready processes to see which is executed next and allocates GPU
		- sometimes the only scheduler in the system
		- invoked frequently (ms) -> must be fast
	- long-term scheduler: selects which process should be put into the ready queue
		- invoked less frequently (seconds, minutes) -> may be slow
		- controls the degree of multiprogramming, which is the number of processes in memory
	- can be either: 
		- I/O bound processes: spends more time doing I/O than computations
		- CPU bound processes: spends more time doing computations
	- long term scheduler should choose a good mix of I/O bound and CPU-bound processes

- some OS's, time sharing systems, may have some other level of scheduling
	- Medium-term scheduler
		- can be added if degree of multiple programming needs to decrease
		- remove process from memory, store onto disk, bring it back from disk to continue executions
			- called swapping
		- may be necessary to improve mix, or the memory is been overused

- Context switch
	- when CPU goes to another process, the system must save the state of the old process, and load the saved state for the new process using a **context switch**
	- context is a processes represented in its PCB
	- context-switch time is an overhead, system does no useful work while switching
		- the more complex the OS and PCB, the longer switching time
	- time dependent on hardware support
		- some hardware provides multiple sets of registers per CPU -> context switch requires changing the pointer to the current register set
	![[Pasted image 20240211131032.png]]
	the idle time on the right is wasted time

- Multitasking in mobile systems
	- some mobile systems only allow one process at a time
	- Apple now has some form of multitasking on user applications
		- single foreground process -> controlled through UI
		- multiple background processes -> in memory, running, but not displayed
	- Android runs foreground and background with fewer limits
		- background processes use a service to perform tasks
		- service can keep running even if background process is suspended
		- service has no user interface, so small memory usage

# Operations on Processes
- OS must provide the ability to:
	- create processes
	- terminate processes
- processes in most systems can execute concurrently, and they may be created and deleted dynamically


## Process Creation
- parent process create children process, which in turn create other processes, which creates a tree of processes
- each process has a process identifier (`pid`)
- tree of processes;
	- `init` process (has `pid=1`) is root parent process for all users
	- use command `ps -el` to list all active processes in the system

- resource sharing options
	- child process may obtain resources directly from the OS
	- child process may use a few of parent's resources
		- prevents any processes from overloading the system by having too many child processes
- when process creates new one, two possibilities for execution exist 
	1. parent continues to execute concurrently with children
	2. parent waits until some or all children have terminated
- there are also two address-space possibilities for the new process:
	1. child process is duplicate of the parent (same program and data as parent)
	2. child process has a new program

- UNIX Examples:
	- `fork()` system call for creating new process
		- new process consists of copy of the address space of the original process
		- both child and parent continue execution after `fork()` line
			- except the return code for the `fork()` is `pid=0` for new child process
			- return code for the `fork()` is the PID of the new child process for the parent process, so can use `pid>0` for the parent
	- `exec()` system call that is used after `fork()` to replace process's memory space with a new program
		- so the two processes are able to communicate and then go their separate ways
		- parent can then have more children, or, if it may want to, issue a `wait()` system call to move itself off the ready queue until the termination of the child
		- 
## Process Termination 
- once the last statement is executed, it then asks the OS to delete it using the `exit()` system call
	- returns data from child to parent (via `wait()`)
	- process's resources are deallocated by the operating system
- parent may terminate the execution of children using `abort()`
	- reasons why it may want to: 
		- child exceeded allocated resources
		- task assigned to child is no longer required
		- parent is exiting and the OS does not allow child to continue if parent is dead
- some OS's do not allow for the child to continue if the parent is terminated
	- termination initiated by OS and called cascading termination
- parent process may wait for termination of the child using `wait()` system call. all returns status information and the `pid` of the terminated process
	- `pid = wait(&status)`
- when process is killed, resources are deallocated from OS
- but entry in process table must remain there until the parent calls `wait()`
	- if the parent did not invoke `wait()`, process is called a zombie
		- does not return to anything
	- if parent terminated without invoking `wait()`, process is an orphan
		- `init` process becomes parent and issues `wait()` periodically to clear orphan processes

# Interprocess Communication
- processes within a system may be independent or cooperating
	- independent: cannot affect or be affected by execution of another
	- cooperating (sharing data with other processes) can be effected/effect others
		- reasons for using cooperating:
			- information sharing
			- computational speedup (break tasks into multiple tasks)
			- modularity: divide system functions into separate processes or threads
			- convenience: user may work on many tasks at the same time
- communication models
	- two ways of interprocess communication (IPC) are available to cooperating processes to allow them to exchange data and information
		- shared memory
			- system calls only needed for creating shared memory -> fast
		- message passing 
			- system calls are needed for every exchanged message -> slow

- shared-memory systems: 
	- area of memory shared among processes that wish to communicate
		- there is space allocated for shared memory in the address space of a process
			- other processes can attach to this shared memory space 
		- communication is under the control of users processes and not the OS
			- system calls are only required to establish the shared memory locations
		- major issue is to provide a mechanism that will allow the user to synch their actions when they access the shared memory

- shared-memory systems: producer-consumer problem
	- it is a common paradigm for cooperating process
		- producer process produces info that is consumed by a consumer process
		- for example: a compiler may produce assembly code that is consumed by an assembler
		- to allow producer and consumer processes to run concurrently, we must have available buffer of items that can be filled by the producer and emptied by the consumer
		- two types of buffers 
			- unbounded buffer: places no practical limit on the size of buffer
			- bounded buffer: assumed that there is a fixed buffer size 
				- consumer must wait if buffer is empty, and producer must wait if buffer is full
- Bounded buffer - Shared memory solution
	-  implemented in circular array with logical in and out
	- variables that are in the region of memory shared by consumer and producer process
		- `in` points to next free position in the buffer, `out` points to the first full position in the buffer
		- `empty` when `in == out`
		- full when `((in+1) % BUFFER_SIZE) == out`

- Producer code:
```
item next_produced;
while (true){
	while (((in+1)%BUFFER_SIZE)==out) {
		// do nothing
	}
	buffer[in] = next_produced;
	in = (in+1)%BUFFER_SIZE;
}
```

- consumer code:
```
item next_consumed;
while(true) {
	while(in==out) {
	 // do nothing
	}
	next_consumed = buffer[out];
	out = (out+1)%BUFFER_SIZE;
}
```


# Example of Interprocess Communication - POSIX
- several mechanisms are available for POSIX systems
	- shared memory and message passing 
- POSIX shared memory is organized using memory mapped files, associate the region of shared memory with a file
- POSIX shared memory
	- process first creates shared open segment
	- `shm_fd = shm_open(name, O_CREAT | ORDWR, 0666`;
		- also used to open an existing segment to share it
	- set the size of the object to 4k
		- `ftrunicate(shm_fid, 4096)`
	- now the process should write to shared memory:
		- `sprintf(shared_memorym, "writing to shared memory")`


## Message-Passing Systems 
- mechanism given by the OS for processes to communicate and synch their actions without sharing the same address space
- useful in distributed environment 
	- Internet Chat program 
- message system: processes communicate with each other without resorting to shared variables
	- problem: slow since all messages should go through the kernel
	- preferable in multicore systems since it does not suffer from cache coherency problem
- message-passing facility provides two operations
	- `send(message)`
	- `receive(message)`
- message size is either fixed or variable

- if process `P` and `Q` want to communicate, they need to establish
	- communication link between them
	- exchange messages using send/receive operations
- implementation issues 
	- how are linked established? 
	- can a link be associated with more than two processes? 
	- how many likes can there be between every pair of communicating processes? 
	- what is capacity of the link? 
	- is size of a message that the link can accommodate fixed or variable? 
	- is linked unidirectional or bi-directional
- implementation of communication link: 
	- physical implementation
		- shared memory
		- hardware bus
		- network
	- logical implementation issues: 
		- direct/indirect communication
		- synchronous or asynchronous communication
		- automatic or explicit buffering
	- so solve these issues, OS gives way to naming process, synchronizing their actions, and buffering
- Naming: 
	- processes that want to communicate must have a way to identify one another
		- direct communication: 
			- processes name-drop the other one
				- `send(P, message)` to send a message to P
				- `receive(Q, message)` to receive a message from Q
			- properties in communication link in this scheme: 
				- links are established automatically, each process needs to know only each other's identity to communicate
				- link is associated with exactly one pair of communicating processes
				- between each pair there exists exactly one link
				- the link may be unidirectional, but is usually bi-directional
		- indirect communication:
			- messages are sent and received from mailboxes (aka ports)
				- each port/mailbox has unique id
				- processes can communicate if they share a mailbox
			- the `send()` and `receive()` primitives are as follows:
				- `send(A, message)` sends a message to mailbox A
				- `receive(A, message)` receives a message from mailbox A
			- properties:
				- link established only if processes share this mailbox 
				- link may be associated with many processes
				- each pair of processes may share several communication links, with each link corresponding to one mailbox
				- link may be unidirectional or bi-directional
- a mailbox that is owned by the OS is independent and not attached to any processes
- OS must provide mechanism to do the following: 
	- Create a new mailbox (port)
	- Send and receive messages through mailbox
	- delete a mailbox
- process that creates mailbox is the owner, and is the only one that can receive messages through that mailbox 
	- ownership and receiving privilege may be passed to other process through proper system calls

- mailbox sharing: 
	- suppose that we have processes $P_{1}$ $P_{2}$ $P_{3}$ that share a mailbox $A$
	- $P_{1}$  sends; and $P_{2}$ and $P_{3}$ receive
	- who will get this message: 
		- depends on which of the following is implemented: 
			- allow a link to be associated with at most two procesess
			- allow only one process at a time to execute a receive operation
			- allow the system to select the receiver arbitrarily. sender is notified who the receiver was
- Synchronization: 
	- many design options for using `send()` and `receive()` primitives:
	- message passing can be blocking or non-blocking 
		- blocking considered synchronous 
			- blocking send: sender is blocked until message is received
			- blocking receive: receiver is blocked until a message is available
		- non-blocking considered asynchronous
			- non-blocking send: sender sends the message and continues operation
			- non-blocking receive: the receiver receives either a valid message or null message
		- different combination of the two are possible
			- if both send and receive are blocking, we have a rendezvous between the sender and receiver
- Buffering: 
	- regardless if communication is direct or indirect, messages exchanged by communicating processes are in a temporary queue. They can be implemented in three ways 
		- zero capacity: no message are queued on a link 
			- sender must wait (block) for receiver to receive (rendezvous)
		- bounded capacity: queue has finite length `n` messages
			- sender must wait if link is full, otherwise can resume operation
		- unbounded capacity: queue with infinite length
			- sender never waits (blocks)

# Communications in Client-Server Systems
- shared memory and passing messages are used again in client-server systems
- other strategies for communication in client-server systems
	- sockets
	- remote procedure calls
	- pipes 
	- remote method invocation (java)


## Sockets
- defined as an endpoint for communication
- pair of processes over a network employs a pair of sockets
- identified as a concatenation of IP address and port which is a number included at start of message packet to differentiate differentiate network services
	- The socket 161.25.19.8:1625 refers to port 1625 on host 161.25.19.8
- communications consist between a pair of sockets
	- all connections must be unique
- all ports below 1024 are well known, used for standard services
- special IP address 127.0.0.1 to refer to a system on which the process is running

- sockets use client-server architecture: server waits for incoming client requests by listening on a port
- when client process initiates request for communication, it is assigned a port (>1024) by its host computer


### Sockets in Java 
- three types: 
	- Connection-oriented (TCP): implemented with `Socket` class
	- Connectionless (UDP): uses `DatagramSocket` class
		- `MulticastSocket` class: is a subclass of `DatagramSocket` class
			- allows data to be sent to multiple recipients
	- example: 
		- date server that uses connection-oriented TCP sockets
			- the operation allows clients to request the current date and time from the server


## Remote Procedure Call (RPC)
- RPC abstracts procedure calls between processes on networked systems 
	- uses ports for service differentiation
	- each message is addressed to an RPC daemon listening on that port
- port is a number included at the start of a message packet
	- system has one IP address and many ports
- RPC allows client to invoke procedure on remote hose as it would locally 
- RPC system hides details that allow communication to take place by providing a stub on the client side
	- when client invokes remote procedure 

# Communication in Client-Server Systems 
- pipes:
	- allows two processes to communicate
	- when implementing a pipe, four issues must be considered
		- unidirectional or bidirectional?
		- if two way, is it half or full-duplex
		- does there have to be a relationship (such as parent-child) between the processes
		- can the pipes be used over a network?
	- two types of pipes on UNIX and Windows systems
		- ordinary pipes: cannot be accessed from outside the process that created it.
			- usually the parent process creates the pipe to communicate with the child process
		- named pipes: can be accessed without a parent-child relationship

## Ordinary Pipes 
- allow communication in producer-consumer style
	- producer writes to one end of the pipe
		- write-end of the pipe
	- consume reason from the other end
		- read-end of the pipe
- therefore they are unidirectional
- if two way communication is required, you must have two pipes
- require parent-child relationship between the processes
	- so these pipes can only be used for processes on the same machine
	- they will be deleted from the system if their processes are terminated
- windows calls these pipes anonymous pipes


- on UNIX systems, ordinary pipes are made using `pipe(int fd[])`
	- creates a pipe that is accessed through `fd[]` file descriptors: `fd[0]` is the read-end and `fd[1]` is the write end
	- accessed by `read()` and `write()` system calls just like files


## Named Pipes 
- more powerful
- bidirectional
- no parent-child relationship necessary
- many processes can use named pipe
- provided on UNIX and Windows systems


- on UNIX;
	- FIFO's
	- will appear as typical file in the file system
	- a FIFO is created with `mkfifo()` system call
		- manipulated using `open()`, `read()`,  `write()`, `close()`
	- half duplex, for full use two FIFOs
	- can be used on the same machine only
	- example: `ls | more`
		- setting up a pipe between `ls` and `more` commands (which are running as individual processes)
		- the `ls` command is the producer and the output is consumed by the `more` command

- on Windows
	-  full-duplex communication is allowed, and communicating processes may be on same or different machines
	- created with the `CreateNamedPipe()` function, and a client can connect using `ConnectNamedPipe()`
	- communication over named pipe can done using `ReadFile()` or `WriteFile()`
	- example: `dir | more`
	- 