# Process Synchronization

- cooperating process - one that can affect or be affected by other processes
	- can directly share address space
	- can share data through files or messages
- processes can execute concurrently or in parallel


# Race Condition 
- if several processes access the same data concurrently, and the outcome depends on the order of which the access takes place, this is called a race condition

# Critical Section Problem
- consider system of n processes $P_{o}, P_{1}\dots P_{n-1}$
- each process has a critical section segment of code
	- when one process is in it's critical section, no other processes are allowed in that critical section
- critical section problem is to design a protocol to solve this issue
	- each process must request permission to enter its critical section in the **entry section**, may follow the **critical section** with exit section, then remainder section
	- general structure of P
```
do {
	entry section
	critical section
	exit section
	remainder section
} while (true);
```


- the solution to critical section must satisfy:
1. mutual exclusion: if process P is in the critical section, no other processes can be executing in their critical section
2. progress: if no process is in critical section, and some process wants to get into it, only the processes that are not executing in the remainder sections can participate in deciding which will enter its critical section next, and this selection cannot be postponed forever
3. bounded waiting: bound must exist on the number of times that processes are allowed to enter the critical section after a process has made a request to enter its critical section and before that request is granted

- assume that each process executes at a non-zero speed
- no assumption concerning the relative speed of the n processes

# Critical Section Handling in OS 
- kernel subject to race conditions
	- data structure for maintaining a list of open files in the system, memory allocation, process lists, interrupt handling
- two approaches to handle critical sections in OS 
	- preemptive kernel: allows preemption of process when running in Kernel
	- non-preemptive kernel: process runs until it exits kernel mode, blocks, or voluntarily yields to the CPU (no preemption)
		- free of race conditions
- why use preemptive kernel?
	- more responsive, less risk that kernel-mode process will run for long period of time before leaving CPU to other processes
	- suitable for real-time programming 

# Peterson's Solution 
- software-based solution to critical-section problem
- restricted two processes (Pi, Pj) that alternate execution between their critical and remainder sections

- assume the load and store machine-language instructions are atomic (cannot be interrupted)
- solution requires that two processes share two variables:
```
int turn;
Boolean flag[2];
```
- `turn` indicates whose turn to enter the critical section:
```
turn = i // means process P_i is allowed to execute its critical section
```
- `flag` used to indicate if a process is ready to enter critical section
```
flag[i] = true // implies that process P_i is ready
```

- solution: 
	- enter the critical section, process $P_{i}$ first sets `flag[i]=true` and `turn=j`
		- gives the other process ($P_{j}$) precedence if it was ready
		- if both processes tried to set turn at the same time, then only one of these assignments will last
for process $P_{i}$
```
do {
	flag[i] = true; // i is ready
	turn = j; // j is allowed to execute in its critical section
	while (flag[j] && turn == j) { // if both of those are met, execute in CS
		critical section
	}
	flag[i] = false; // i is no longer ready
		remainder section
} while (true);
```
- the reason that `turn = j` is because we want to give $P_{j}$ precedence while $P_{i}$ is in the critical section

for process $P_{j}$
```
do {
	flag[j] = true; // j is ready
	turn = i; // i is allowed to execute in its critical section
	while (flag[i] && turn == i) { // if both of those are met, execute in CS
		critical section
	}
	flag[j] = false; // j is no longer ready
		remainder section
} while (true);
```

- these satisfy all three of those requirements for Critical Section problem


# Synchronization Hardware
- hardware support for implementing critical section code using `locks`
- CS problem easy to solve in single-processor system
	- disable interrupts while shared variable was being modified
	- generally, too inefficient in multiprocessor systems
		- disabling interrupts in multiprocessor system is time consuming: message that it has happened has to be sent to every processor
		- OS doing this is not scalable
- modern machines provide special atomic hardware instructions
	- atomic = non-interruptible
		- bit-band operation in ARM processor
	- instruction to: 

- using `test_and_set` instruction
- instruction is executed atomically
	- if two of these instructions are run at once, they will be executed sequentially in some arbitrary order
- returns original value of passed parameter
- set new value of passed parameter to TRUE



- using `compare_and_swap` to change the value of a variable atomically
- in the example of locks, this is how we can use this to create a critical section solution:

```
do {
	while(compare_and_swap(&lock, 0, 1) != 0) {
		; // do nothing
		// critical section
		lock = 0;
		// remainder section
	}
} while (true);
```
- does it satisfy the requirements?
	- mutual exclusion
		- yes
		- the global variable `lock` is initialized to 0. the first process that invokes this method will set `lock = 1` and then enter its critical section, because `lock = 0`
# Mutex Locks 
- previous hardware-based solution is complex (inaccessible to application programmers)
- OS designers built software tools to solve CS problem such as mutex lock
	- Boolean variable that indicates whether lock is available or not
	- used to protect Critical Regions and prevent race conditions
	- process must acquire() the lock before entering CS and release() once it's done

```
do{
	acquire lock
	// critical section
	release lock
	// remainder section
} while(true);
```

```
acquire() {
	while(!available)
	; // busy, so wait until it's available
	available = false; // once it is available, we get it, so another process cannot
}
```

```
release() {
	available = true;
}
```

- acquire and release must be atomic, mutex locks are often implemented as hardware mechanisms
- solution suffers from busy waiting
	- while process is in CS, any other process has to loop continuously in acquire()
- therefore, this lock is called a spinlock
- 