- lets say that a Tesla vehicle crashed while in autopilot
	- the first thing they would do is try to settle it with the victim through settlements before they get sued
	- this way, they don't destroy their company and reputation

- imagine a triangle with three sides: 
	- cost
	- scope
	- quality
- if you want to fix something that is within this triangle, you can adjust the other corners of it 
	- if you find that something is too expensive, you can decrease the scope or decrease the quality of the project at hand

# Software Engineering Design Process
1. requirement gathering
2. analysis
3. design
4. coding
5. testing
6. maintenance

How much do you think each of these steps of the process contribute to the total cost of the project?
- if you put all the steps on the x-axis of a graph, where the y-axis is the cost, it will be exponential
- remember that the only constant in software engineering is "change"
	- this is an explanation that means that even after the maintenance stage, the cost of it will continue to rise
- lets say you are trying to make a big change in a software, you might have to refactor code from the very beginning, therefore it might take a lot longer than you might expect
- as a software engineer, your main enemy is "change"

- the reason that you now use modules and functions in code is because you make it easier to test for bugs and debug your program
	- when everything was written in assembly language, everything was one module, and so if it came time to make a change or debug something, it was very expensive
	- dividing into smaller modules make it easier to test, change, and debug code as they are broken up into pieces of code
	- with the introduction of C, we were given the ability to make functions
	- and with C++, we were given the ability to make objects, which makes functions and modules even smaller than before
		- in the context of making changes, this is much better
		- object oriented programming languages are generally better in this context as well
	- in classes, you can have interfaces, and it's much nicer to have concrete interfaces, which make it easier to update and change code 
## Why is object oriented programming good? 
- every object has a template, and that is a class
- if you have many many objects, if you want to change something universally for all of them, you can do this by simply changing something in the class
- also, encapsulation
	- encapsulation means that you associate the data and methods in a capsule, and the data is preferred to be `private`. so that it does not get access outside the class or any class outside the code does not get access to it
	- why is this good? 
		- localizing where the change is going to occur, because you're not doing anything externally, you are only working in and within the class itself
- let us assume this case
	- something is wrong with your code, and you assume that your problem is due to a global variable
		- because of this, you have to go through every single module
		- so you basically have to go through every single line of code in your program
	- if you're doing something in object oriented programming
		- you don't have any global variables
		- they're all private or protected
		- having public variables in classes are not recommended
		- for you to make a change, you really can just localize the change to the number of lines within the class

- the context behind this whole thing is if you are going to make a change in your program
- finding where you want to make a change to your program is very costly, and this is done easily using object oriented programming (at least easier than going through every line one by one)


- maintenance is the most costly because it requires you to make many changes
	- this may require you to change something in a large codebase, and finding where to make this change is a lot of money


why is the requirements step the cheapest
- because you are simply asking your customer for their requirements
- because of this, it is not worth coding without knowing anything about the requirements or anything of that sort
	- the fact that you have something to work off of makes the cost of general development very easy and cheaper, rather than going in blind
- if you are implementing your software and it is a fairly large size and fairly changing environment, and you are using the waterfall methodology, it is going to be very expensive
	- because of this, you are much better off using the Agile methodology
- if you do not do requirements, analysis, and design, your "cost-curve" will not be under control, and it might get very expensive
	- so to combat this, you should use the agile methodology and do the requirements, analysis, and design sections of it


- lets say you develop software for a full year, and you reach the goal and create project `P1` with requirements `R1`. when you go to show the customer if they're okay with it, they say no, an they want a another product `P2` with requirements `R2`. Now you just wasted a whole year
	- instead of this, make the end goal smaller, but with the scope of a month
	- every month, check with the customer to see if what you've developed so far is what they want
	- this means that if something changes, you are only losing, at most, a month's effort


- the cost of a debug or change in a software project will always exponential with respect to the software development process (requirements, design, coding, testing, maintenance) 
	- if you use the software development process explained above, the cost of the development will be under control
- it is much easier to fix a bug in the requirement phase vs fixing something in the maintenance phase
	- hence, this curve is the main justification for the skills that we are going to be taught in this course


# SOLID Principles 
- single responsibility
	- one class, one responsibility
	- when you are debugging, you can analyze the bug and trace it back to a specific class
	- if a class has a single responsibility, and you understand everything about your software 
	- someone comes to you and says that they would like to make a change
		- can you come up with a list of responsibilities that need to be changed? 
			- if you have classes that only do one task, you can do this much easier
TDD is testing driven development (i think)
- this is to lower the cost in the software design process


# Testing Goals Based on Test Process Maturity
- level 0: no difference between testing and debugging
	- a lot of people start here, but it's not the case
- level 1: purpose of testing is to show correctness
	- you simply can never prove that a software program is 100% correct, so you would never be able to know when to stop testing
	- example: windows fails all the time
	- are there programs that do not fail ever? no
	- proving a program works is very subjective
- level 2: purpose of testing is to show that the software doesn't work
- level 3: purpose of testing is not to prove anything specific, but to reduce the risk of using the software
- level 4: testing is a mental discipline that helps all IT professional develop higher quality software
	- this is the right attitude that yields the best software

# Verification vs. Validation 
- Verification: the process of evaluating software at the end of development to ensure that it matches the intended usage (ensure you build the product right)




# V Diagram
we've seen it before. we have to use the V-Diagram method of development for the design project 