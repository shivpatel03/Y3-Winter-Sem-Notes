These are notes that were taken directly from chapter 1 of the textbook

# 1.1 When Software goes Bad 
- can result costly software, mundane software, and worst of all, loss of lives
- difference between faults, errors, and failures
	- software fault: static defect on software
	- software error: an incorrect internal state that is the manifestation of a fault
	- software failure: external, incorrect behavior in terms of the requirements or another description of the expected behavior
- good way of understanding it: 
	- when you walk into a doctor's office, the patient tells the doctor failures (symptoms)
	- the doctor is then tasked with finding the fault (the root cause of all these failures)
		- they may do this with tests, including high blood pressure, etc. 
	- software differs from this because the faults come from design issues (a decision made by a human)
- software faults can never be eliminated


- another example of a fault that they give is a method that is meant to count the number of zeros in a given list 
	- they do this by using a for loop with the header `for (int i=1; i<x.length;i++)` and then iterating through every index using `i`
	- however, one oversight is that it is not checking the 'zero-eth' element in the list because `i` starts at 1. this is a fault
	- given a list `[2, 7, 0]`, this one will not result in a wrong answer, but it will still result in an error
	- given a list `[0, 7, 2]` this one will result in a wrong answer (failure) and will result in an error

- the term 'bug' is used to interchangeably describe any of the three
	- this textbook does not use the word bug, rather they actually use fault, error, or failure to describe something that is wrong 

- one failure is the Mars landing in September 1999
	- using a miscommunication of units between two software groups
	- one module computed in metric units and the other in English units
	- typical integration fault

- another failure: Therac-25 radiation therapy machine
	- three deaths because of excessive radiation

- Ariane 5 Rocket
	- exploded 37 seconds after liftoff in 1996
	- because of unhandled floating-point conversion exception in inertial guidance system
	- could never encounter the unhandled exception when on the rocket
	- came from wanting to use this same system from Ariane 4, but no one re-checked the software
	- expensive failure

- Pentium Bug
	- early alarm of needing better testing, especially unit testing 
	- Intel made the chip and a mathematician showed that it gave incorrect results to some floating-point division calculations
	- would have been a very easy fault to find if unit testing was done


- great northeast blackout of 2003
	- powerline brushed overgrown trees and shut down
		- considered a fault in power industry
	- the software alarm did not notify the local power company
		- system operators did not know how any of this happened
	- this blackout then spread to some parts of Canada and 8 states

- some software faults cause embarrassment to companies
	- 2011, Korean system to calculate grades miscalculated for 29000 middle school students


- in 1999, a study was done, and it concluded that the current base of science and technology is not enough for building systems to control critical software infrastructure

- software faults do not only lead to functional failures. faulty software can also lead to vulnerabilities, which can enable common attacks to users of that software

- public and expensive software faults are more common nowadays
- we are using more safety critical, real-time software now



# 1.2 Goals of Testing Software
- separate validation and verification
	- verification: process of determining whether the products of a phase of the software development process fulfill the requirements established during the previous phase
	- validation: process of evaluating software at the end of the development to ensure everything works as needed
- verification generally needs more technical knowledge about individual software artifacts, requirements, and specification
- validation only needs knowledge about what the software was supposed to do

- The term "IV&V" stands for "Independent Verification and Validation"
	- independent means that it is done by non-developers
- sometimes the IV&V team is in the same project, sometimes same company, and sometime entirely external 
	- since it is independent, sometimes this process is not started until after the software has been developed
	- this means that the validation is sometimes given more weight than verification

- Beizer sets goals for testing in terms of "Test process maturity levels" of an organization
- these levels are characterized by tester's goals, and there are five levels, and the lowest level is not worthy of having a number; 
	- level 0: no difference between testing and debugging
		- view that testing is the same as debugging
		- model does not distinguish between a program's incorrect behavior and a mistake in the program, doesn't help make the software reliable or safe
	- level 1: purpose of testing is to show correctness
		- correctness is virtually impossible to show or demonstrate or even achieve
		- lets say we ran tests and found no failures. we don't know if we have good software or bad tests
		- these types of testers generally are not able to answer the question "how many tests do we have left to run"
		- they have no way to evaluate or express their work
	- level 2: purpose of testing is to show that software does not work`
		- testers may want to find a problem but developers are the opposite
		- if our goal is to find failures, we don't know what to do if we don't find any... is our work done? 
		- having confidence when testing is important for testers
		- this level currently dominates the industry
	- level 3: purpose of testing is not to prove anything specific, but to reduce the risk of using the software
		- realization that testing can show the presence, but not the absence of failures
		- when we use software we incur some risk 
		- in this level, both testers and developers work together to reduce risk
		- we see more and more companies going to this level every year
	- level 4: testing is a mental discipline that helps all IT professionals developer higher-quality software
		- testers and developers can be thought of on the same "team"
		- analogy: spell checker: 
			- we often think that the purpose a spell checker is to check for misspelled words
			- but in fact the best purpose of the spell checker is to improve our ability to spell the word correctly
			- the spell checker is the 'expert' on spelling quality 
			- level 4 testing means that the purpose of testing is to improve the ability of developers to produce high-quality software
			- testers should be the experts who train developers 
- although level 4 is rare, it's becoming more common
- as a reader of this book, you will probably start at level 0, 1, or 2
- these considerations help us figure out why we test
- we want to know why each test is present
- if you don't know why you are conducting a test, why are you doing it? 
- when the test manager goes to meetings, they should be able to explain clearly how much testing is enough and when the testing will be complete


- testing earlier is better than testing later

- putting level 4 from above into simple terms: 
	- the goal of testing is to eliminate faults as early as possible
	- we can never be perfect, but every time we eliminate a fault during unit testing, we save money and time
	- the rest of this book is meant to teach you how to do that.