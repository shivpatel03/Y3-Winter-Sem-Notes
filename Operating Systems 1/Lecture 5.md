
- cooperating process: process that affects or can be affected by other processes in the system
	- share logical address space (code and data)
	- they can share data only through files or messages
- processes execute in parallel or concurrently
	- can be interrupted, stopping execution
	- data inconsistency (because of access to shared data)

# Race Condition 
- consider a producer-consumer problem, where there is a counter that holds the number of buffers that are full (starts at 0). when a producer produces a buffer, counter goes up. when the consumer consumes a buffer, counter goes down by one. 
- the problem: when many processes access the data concurrently, the outcome depends on the order that the access took place. called a race condition

# Critical Section Problem
- consider n processes in a system
- each process has a critical section segment of code
	- when one process is in the critical section, no other process is allowed to be in that critical section
- critical section problem is to design a protocol to solve that issue
	- process must request permission to enter its critical state in the **entry section**, and may follow the **critical section** with **exit section**, then the **remainder section**
	- the general structure of the process:
```
do {
	entry section
	critical section
	exit section
	remainder section
} while (true);
```
- the solution to a critical section problem must satisfy the three requirements
1. mutual exclusion: if process P is executing in the critical section, another process cannot execute in their critical sections
2. progress: if no process is executing in its critical section, only processes that are NOT in the critical section can participate to decide which will enter its critical section first
3. bounded waiting: a bound must be set on how many times a process is allowed to enter their critical sections after a process has made a request to enter its critical section and before the request is granted

# Critical Section Handling
- kernel code of OS subject to race conditions
	- data structure for maintaining list of all open files in the system, memory allocation, process list, interrupt handling
- two approaches are used to handles CS in OS
	- preemptive kernel: allows preemption of process when running in kernel mode
	- non-preemptive kernel: the process runs until it exits the kernel mode, blocks, or voluntarily yields the CPU
		- free of race conditions on kernel data structures, as only one process is active in the kernel at a time
- why use preemptive kernel?
	- more responsive, less risk that kernel-mode process will run for long period before leaving CPU to other processes
	- more suitable to real-time programming

# Peterson's Solution 
- software based solution to CS problem
- restricted to two processes that alternate execution between critical sections and remainder sections
	- assume load and store machine-language instructions are atomic; that is, cannot be interrupted
	- solution requires two processes share two variables:
		-  `int turn` and `Boolean flag[2]`
	- variable `turn` indicates whose turn to enter the critical section
		- `turn = i` -> process $P_{i}$ is allowed to execute in its CS
	- `flag` array is used to indicate if a process is ready to enter critical section
		- `flag[i]=true` -> implies that $P_{i}$ is ready

- solution:
	- to enter the CS, process $P_{i}$ sets `flag[i]=true` and `turn=j`
		- gives other process $P_{j}$ precedence if it was 
		- notice that for $P_{i}$, it sets `flag[i]` to true to indicate that it is allowed to access the critical section
			- it sets `turn=j` which indicates that $P_{j}$ is ready to enter, which will allow it to access it once $P_{i}$ is done
			- while `j` is allowed to access the CS, and `j` wants to access next, the CS for `i` is accessed
			- once done with the CS, `i` no longer is allowed to access the CS because `j` will. so `flag[i]` set to false
![[Pasted image 20240310172028.png]]



# Synchronization Hardware
- systems give locks to implement critical section code
- CS problem is easy in single-processor systems
	- uniprocessors can disable interrupts while a shared variable is being modified
	- this is inefficient in multiprocessor systems. it is time consuming
		- message has to be passed to all processors before entering critical section
		- OS using this is not very scalable
- modern machines have atomic hardware instructions (non-interruptible)
- instruction to test and modify content of a memory word (`test_and_set`)
- or instruction to swap contents of two memory words atomically

- using `test_and_set` executed atomically
	- if two of these instructions are executed together, they will be executed in arbitrary order
	- returns the original value of the passed parameter
	- sets the new value of the passed parameter to "TRUE"

- using `compare_and_swap` instruction
	- executed atomically
	- returns the original value of the passed in value `value`
	- set the variable "value" to the value of the passed parameter `new_value` but only if `value == expected`
		- swap only takes place under this condition

- using `compare_and_swap` instruction to introduce `lock` initialized to 0
- solution:
```
do {
	while(compare_and_swap(&lock, 0, 1) != 0) {
		// do nothing
		// critical section
		lock = 0;
		// remainder section
	}
} while (true);
```

- while `lock = 1`, it means the critical section is not available
- when `lock = 0` it means the critical section is available
- you swap to 1 right before the process goes into critical section (meaning that you can't let another process into it)
	- and then put it back to 0 when it is done
	- this swap from 0 to 1 is done atomically.

- does this follow the critical section requirements?
	- mutual exclusion (yes): global variable `lock` starts at 0. the first process that invokes `compare_and_swap()` will set `lock = 1` to access its critical section
	- every other call to `compare_and_swap()` will not succeed because lock = 1 and that does not equal to 0
	- when process exits critical section, allows another process to enter critical section (progress is followed)
	- what about bounded delay? no it doesn't

## Bounded-Waiting Mutual Exclusion with `test_and_set`
- although these algorithms satisfy the mutual exclusion requirement, they do not satisfy the bounded-waiting requirement
![[Pasted image 20240311112858.png]]
- set `waiting[i]` to true indicating `i` is waiting to go into critical section
- `key = true` to indicate that the process is trying to go into critical section
- bounded waiting while loop, to see if `i` is waiting to go into CS
	- key will be set to true if `test_and_set(&lock);` returns true, indicating that another process is in the critical section `i` cannot go into its
- once that is done, it looks through the waiting array to see if there is another value that is set to 'true' indicating that it wants to go into the critical section. if `j==i` that means there is no other process that wants to go into the critical section 


# Mutex Locks 
- hardware-based solutions are complicated and mostly hard to use for application programmers
- OS designers build software to solve the critical value problem such as mutex locks
	- the lock has a Boolean variable indicating if the lock is available or not
	- they are used to protect critical regions and prevent race conditions
	- process must acquire() lock before critical section and release() it when it exits the critical section
- but this solution suffers from busy waiting
	- while a process is in its critical section, any other process that tries to enter its critical section must loop continuously to acquire()
- therefore, this lock is called a spinlock

```
acquire() {
	while (!available) {
		// busy waiting until it is available
	}
	available = false;
}
```
```
release() {
	available = true;
}
```
both of these must be atomic. mutex locks are often implemented as hardware mechanisms

- question:
	- using a struct that just holds an integer called `available`
	- when available = 0, lock is available. if value is 1, lock is unavailable
	- using this struct and `test_and_set()` and `compare_and_swap()`, implement acquire and release
		- `void acquire(lock *mutex)`
		- `void release(lock *mutex)`
![[Pasted image 20240311114458.png]]

# Semaphores
- synch tool that provides better ways for processes to synch activities
- Semaphores $S$ is an integer variable that can only be accessed via two atomic operations
	- wait() and signal()
		- originally called P() and V()
- when one process changes the semaphore value, no other process can change it at the same time

# Semaphores Usage
- if the value of the Semaphore is 3, that means there are three units of resource that are available for use. three processes can concurrently acquire and use the resource by using the `wait` operation
- every process that wants to use a resource performs a `wait()` operation (decrementing the count)
- when a process releases a resource, it performs a `signal()` (incrementing the count)

Binary semaphore: integer value that can only range between 0 and 1


# Semaphores Implementation
- must guarantee that no two processes (wait and signal) on the same semaphore at the same time
- the previous definitions of wait() and signals() semaphore operations suffer from busy waiting as well
	- when a process executes `wait()` operation and finds that the semaphores value is not positive, it must wait by engaging in busy waiting
	- instead, if the process can block itself by placing itself in a waiting queue associated with the semaphore, and the state of the process is switched to the waiting state

# Semaphore Implementation with no Busy Waiting 
- every semaphore has `int` value and an associated waiting queue
- each entry in the waiting queue is a PCB that has a pointer to next record in the list
	- need two operations as system calls
		- block() - places the process invoking the operation on the appropriate waiting queue
		- wakeup() - removes one of processes from the waiting queue and place it in the ready queue
![[Pasted image 20240311120159.png]]
- if semaphore value is negative, magnitude of the number of processes that are waiting on that semaphore
- semaphore operations must be executed atomically
	- must guarantee that no two processes can execute wait() and signal() at the same time


# Deadlock and Starvation
- deadlock: two or more processes are waiting indefinitely for an event that can be caused by only one of the waiting processes
	- imagine $P_{o}$ and $P_{1}$, each accessing semaphores $S$ and $Q$ set to value of 1
- starvation: another problem with deadlocks
	- a process may never be removed from semaphore queue in which it is suspended (when the queue associated with the semaphore is implemented as LIFO)

# Priority Inversion 
- problems when lower priority process holds a lock needed by higher priority process
- solved using 'priority-inheritance protocol'
	- process that is accessing a resource that is needed by a higher priority process will inherit the higher priority until it is finished with the resource in question

# Classic Problems with Synch
 - bounded-buffer problem
 - readers and writers problem
 - dining-philosophers problem

# Bounded Buffer Problem
- producer and consumer processes share the following data structures:
	- `n` buffers, each holding one item
	- `mutex` semaphores provides mutual exclusion for accessing the buffer pool
	- `full` and `empty` semaphores count the number of empty and full buffers
	- initialization
```
int n;
semaphore mutex = 1 // provides mutual exclusion to access buffer
sempahore empty = n // initially we have n empty buffers
semaphore full = 0; // intially we have zero full buffers
```

![[Pasted image 20240311122244.png]]
- producer removes 1 from empty semaphore (one less buffer because it is producing something)
	- also removes one from the mutex indicating that the mutex is being used (mutual exclusion)
	- also then adds to the mutex again and one to the full to indicate there is one full buffer
- the consumer removes one of the full because it reads it
	- mutex lock = 0 for mutual exclusion
	- adds to the empty again because the full one is no longer full

# Readers-Writers Problem 
- assume that dB is shared among several concurrent processes
	- readers: processes only read data; do not perform any update 
	- writers: processes that can both read and write to DB
- problem: if write rand some processes (either reader or writer) access database at same time, we don't exactly know what will happen
	- writers should have exclusive access to database while writing to it
	- all possible solutions are involving some form of priorities
	- readers-writers problem variations
		- First reader-writer problem: no reader kept waiting unless a write has permission to use a shared object (no reader should wait for other readers to finish because a writer is waiting) -> writers may starve
		- Second reader-writer problem: once a writer is ready, it should perform the writing as soon a possible


# Monitors  
- problems with semaphores
	- incorrect use of a semaphore can result in timing errors that are difficult to detect:
		- correct execution of a semaphore is as: `wait(mutex) critical section signal(mutex)`
		- but if by mistake the order was executed as:
			- `signal(mutex) critical section wait(mutex)`
				- more than one process are simultaneously active in their critical section
			- `wait(mutex) critical section wait(mutex)`
				- deadlock happens
			- omitting of `wait(mutex)` or `signal(mutex)` or both
				- mutual exclusion is violated or deadlock will occur
		- to combat this, researchers created monitors

- monitor usage
	- high level abstraction that provides a convenient and effective mechanism for process synchronization
	- monitor type is an abstract data type (ADT) that includes a set of programmer defined operations and variables that are provided with mutual exclusion within the monitor
	- only one process can be active within the monitor at all times
	- not powerful enough to model some synchronization schemes