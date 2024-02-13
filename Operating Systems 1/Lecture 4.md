- Process is a single thread of control
- Thread is unit of CPU utilization 
	- has: 
		- thread ID
		- program counter
		- register set
		- stack
	- shares with other threads that belong to same process; 
		- code section
		- data section
		- other OS resources such as open files and signals


# Single and Multithreaded Processes
 - if a process has multiple threads of control it can do more than one thing at a time


# Difference Between Process and Thread
| Processes | Threads |
| ---- | ---- |
| Heavy weight, resource intensive | Less resources needed than a process |
| more than one process cannot share the same memory | threads of same process share the same memory allocated on separate memory locations |
| Process creation and execution require time | Thread creation and execution are much faster |
| Loosely coupled, less amount of resource sharing is possible | As the threads of a process are tightly coupled, more resource sharing is possible |
| Communication between processes is difficult | Communication is much easier |

- Most modern applications are usually multithreaded
	- application has separate processes with many threads of control
	- example: many tasks in word processor can use threads
		- update display
		- get data
		- spell checking
		- answer a network request,
		- etc.
- process creation is heavy, thread creation is light 
	- threads can simplify code, increase efficiency
- Kernels are multithreaded
	- thread for every task,
		- managing devices, managing memory, interrupt handling

# Multithreaded Server Architecture
- Single application may need to have perform several similar tasks from different client requests
	- Web server:
		- if the web-server process is multithreaded, server will create separate thread that listens for client requests
		- when request comes in, instead of making an new process, server creates a new thread to service the request and resume listening for new requests

# Benefits
- four main categories: 
	- responsiveness: allow continued execution in part of the process is blocked
		- if user clicks on a button that results in performance of a time-consuming operation, if it is single threaded, then it will be unresponsive for a long time
	- resource sharing: threads share the resources that the process that they are in have access to, easier to share memory or passing messages between processes
	- economy: cheaper than process creation
	- scalability: takes advantage of multiprocessor architectures
		- may run in parallel

# Multicore Programming
- multithreaded programming provides a mechanism for more efficient use of the multiple computing cores and improved concurrency
- multicore or multiprocessor systems put pressure on programmers:
	- dividing activities into separate concurrent tasks
	- balance: ensure that the tasks perform equal work of equal value
	- data splitting
	- data dependency
- Difference between parallelism and concurrency: 
	- parallelism: implies that system can perform more than one task simultaneously
	- concurrency: supports more than one task to make progress through time sharing
		- system has a single processor or core, and the CPU schedulers are designed to provide illusion of parallelism by rapidly switching between processes'

- concurrency execution on single-core system
	- concurrency will run one task after another
- parallelism on multicore system
	- means that the threads can run in parallel, because the system is designed can assign a separate thread to each core

- Amdahl's Law
	-  identifies performance gains from adding additional cores to an application that has both serial and parallel components 
		- S = serial portion percentage
		- N = number of processing cores
		- $\text{speedup}\leq\frac{1}{s+\frac{1-S}{N}}$
		- if application is 75% parallel and 25% serial, moving from 1 to 2 cores will result in a speedup of 1.6 times
		- as $N\to \infty$ , speedup approaches $\frac{1}{S}$


## Types of Parallelism:
- data parallelism: distributes subsets of the same data across multiple cores, and performing the same operation on each core
	- example: summing the contents of an array of size N
		- Thread A (on core 0) will go to 0 -> halfway into the array
		- Thread B (on core 1) will go from halfway to end
- task parallelism: distributing threads across cores, each thread performing an operation on the same or different data
	- example: two operations on array of size N
		- Thread A (on core 0): sum the elements of the array
		- Thread B (on core 1): find the max of the elements in the array
- rarely any applications only follow one of these
	- the usually use both
- as the number of threads grows, the architectural support for threading grows too
	- CPUs have cores as well as hardware threads


## User Threads and Kernel Threads
 - Support for threads may be provided either at the user level or kernel level
	 - User Threads: management done by user-level threads library
		 - three primary libraries: POSIX Pthreads, Windows threads, Java threads
	 - Kernel Threads: OS managed threads
		 - supported by most modern OS's


- User level threads:
	- application is the one that manages threads and the Kernel is not aware of them
	- libraries contain code to create, destroy threads, passing messages/data between them, etc.
	- begins with single thread and begins running in that thread 
	- Advantages:
		- thread switching does not require Kernel mode privileges
		- user level threads run on any OS
		- scheduling can be application specific in user level threads
		- user level threads are fast to create and manage
	- Disadvantages
		- multithreaded application cannot take advantage of multiprocessing
		- in typical OS, most system calls are blocking
- Kernel level threads;
	- thread management done by Kernel only
	- Kernel maintains information about process as a whole
	- scheduling done on thread basis
	- kernel do thread creation, scheduling and management (it does everything)
	- Advantages:
		- can connect multiple threads from same process on different processors
		- if one thread in a process is blocked, Kernel can schedule another thread of the same process
		- kernel routines themselves cannot be multithreaded
	- Disadvantages: 
		- slower to create and manage
		- transfer of control from one thread to another in the same process require mode switch to Kernel

# Multithreading Models
- some OS give user level thread and kernel level thread facility mixed together 
	- Solaris
	- multiple threads within the same application can run in parallel on multiple processors
- relationship must exist between user threads and kernel threads
	- many to one
		- many user level threads mapped to one kernel level thread
		- one thread blocking causes all to block
		- 
	- one to one
		- each user level thread maps to kernel level thread
		- more concurrency
		- support multiple thread to execute in parallel on microprocessors
		- disadvantages: creating user-level thread needs creating a kernel thread
			- number of threads per process sometimes restricted because of overhead in creating kernel threads
	- many to many
		- many user threads to many kernel threads
		- OS can create sufficient number of Kernel threads
		- developers can create as many user threads as necessary
	- two level mode
		- similar to many-to-many
			- except allows user thread to be bound to kernel thread

# Thread Libraries: 
- provide programmer with API to create and manage threads
- two primary ways of implementing thread library: 
	- provide library entirely in user space with no kernel support
		- all code and DS for library are in user space
		- invoking a function in library results in a local function call in user space and not a system call
	- implement Kernel-level library supported by the OS
		- code and DS are in the kernel space
		- invoking a function in API results in system call to kernel
- Three main thread libraries: 
	- POSIX Pthreads: 
		- user level or kernel level library
	- Windows Threads:
		- kernel-level library
	- Java threads: 
		- allows threads to be created and managed in Java programs
		- because JVM runs on top of host OS, the Java thread API is implemented using thread library available on the host system


- two strategies for creating multiple threads:
	- asynchronous threading: 
		- once parent creates child thread, parent resumes execution, parent doesn't care when child dies
	- synchronous threading: 
		- when parent thread creates one or more children threads, and must wait for all children to die before it continues
		- called "fork-join" strategy
			- only after death of all children can the parent resume working
		- this type requires data sharing among threads
			- parent may want to combine results calculated by various children 

## Pthreads
- provided as either user-level or kernel-level
- refers to POSIX standard that defines API for thread creation and synchronization
	- specifies thread behavior, not implementation
- common in UNIX systems
- once you create a thread, the parent thread uses the function `pthread_join(tid,NULL);` to wait until the child thread is done executing


# Implicit Threading
- with more multicore processing, applications contain hundred/thousands of threads
- designing that is hard
	- a solution is to give the creation and management of threads to compilers and run-time libraries rather than programmers
		- this idea is called implicit threading
	- three methods: 
		- thread pools
		- OpenMP
		- Grand Central Dispatch 
	- other methods: Microsoft Threading Building Blocks (TBB), `java.util.concurrent.package`


## Thread Pools 
- create a number of threads on process start-up and place them into a pool
	- when server gets a request, gets a thread from this pool and passes it in to do the service
	- once the service of the thread is done, it returns to the pool and waits (does not die)
	- if pool empty, server waits for one becomes free
- advantages: 
	- faster to service a request using existing thread rather than creating a new one
	- allows number of threads in application to be bound to the size
	- separating the task to be performed from mechanics of creating the task allows different strategies for running the task
		- example: the task could be scheduled to execute after a time delay or to execute periodically
	- the number of threads in the pool can be set based:
		- number CPUs in the system
		- amount of physical memory
		- the expected number of concurrent client requests

# Threading Issues
- Some of the issues to consider when designing multithreaded programs 
	- `fork()` and `exec()` calls
	- signal handling 
		- synch and asynchronous 
	- thread cancellation and target thread
	- thread local storage
	- scheduler activations

- semantics of `fork()` and `exec()`
	- if one thread in a program calls `fork()`, does `fork()` duplicate only the calling thread or all threads? 
		- some UNIX systems have two versions of fork
			- one that duplicates all threads
			- another that duplicates only the thread that invoked the `fork()` system call\
	- `exec()` works as normal, the program that is specified in `exec()` will replace the entire process including all threads
	- which of the two versions of `fork()` to use:
		- if `exec()` is called right after forking, then duplicating all threads is not needed since the program that was specified in `exec()` will replace the process anyway
		- if the process does not call `exec()` after forking, the separate process should duplicate all threads

- Signal handling 
	- signals are external events (such as control + C) etc.
	- signals used in UNIX systems are used to notify the process that an event has occurred
	- all signals follow the same pattern
		- signal is generated by event
		- signal delivered to process
		- signals handled by one of two signal handlers
			- default signal handler
			- user-defined signal handler
	- every signal has a default handler that kernel runs
		- user defined signal can override the default

	- where should a signal be delivered for multi-threaded process? 
		- deliver the signal to thread to which the signal applies 
			- divide by zero signal should be sent to the causing thread
		- deliver the signal to every thread in the process
			- control + C should be sent to all threads
		- deliver the signal to certain threads in the process
			- to deliver a signal to a process use: 
				- `kill(pid_t pid, int signal)`
			- to deliver a signal to a thread (using `tid`) in Pthread, use
				- `pthread_kill(pthread_t tid, int signal)`
		- assign specific thread to receive all signals for the process

- Thread cancellation: 
	- killing a thread before it has completed
	- the thread to be cancelled is called the target thread
	- two general approach to cancel it: 
		- asynchronous cancellations terminates the target thread immediately
		- deferred calculation allows the target thread to periodically check a flag if it should be cancelled, and then safely cancel itself
	- Pthread code to create and cancel a thread: 

```
pthread_t tid;

// create the thread 
pthread.create(&tid, 0, worker, NULL);

// cancel the thread
pthread.cancel(tid);
```

- Thread cancellation: 
	- invoking thread cancellation requests cancellation, but actual cancellation depends on thread cancellation state
	- pthread supports three cancelations modes:
	
| Mode | Cancellation State | Types |  |
| ---- | ---- | ---- | ---- |
| Off | Disabled | -- |  |
| Deferred (default) | Enabled | Deferred |  |
| Asynchronous | Enabled  | Asynchronous |  |
- if the thread has cancellation disabled, cancellation remains pending until the thread enables it
- default type is deferred: cancellation only occurs when the thread reaches a cancellation point. can test that by invoking `pthread_testcancel()`
	- then cleanup handler is invoked to release all resources for that thread
- on Linux systems, thread cancellations are handled through signals


- Thread Local Storage
	- threads that belong to a process share the data of that process
	- but the thread-local-storage (TLS) allows each thread to have its own copy of its data
	- helpful when you don't have control over the thread creation process (when you use a thread pool, for example)
	- they are different from local variable 
		- local variables are only visible during single function invocation
		- TLS visible across function invocations
	- similar to static data
		- TLS is unique to each thread