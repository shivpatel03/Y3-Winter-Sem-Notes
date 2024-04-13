- software market is much bigger, competitive, more users
- embedded control applications (things that have their own specific software)
- agile processes put increased pressure on the testers now 
	- unit testing is required, with no training or education
	- tests are key to function requirements, who makes those tests?


## faults, errors, failures 
- fault: static defect in software
- failure: wrong behavior with respect to requirements or other description of the expected behavior
- error: incorrect internal state that is the manifestation of some fault
- equivalent to design mistakes in hardware, software does not degrade

### examples:
- patient gives doctor list of symptoms
	- failures
- doctor tries to diagnose root cause
	- fault
- doctor may look for other internal conditions (such as high blood pressure, irregular heartbeat, etc.)
	- errors that led to these faults and failures


# bugs
- used informally
- speakers mean fault, error, or failure, it is used interchangeably

# software failures 
- NASA mars lander, failed due to integration faults
- THERAC-25 radiation machine, failed due to poor testing and killed 3 patients
- Airplane explosion: millions of dollars

# costly software failures
- because of bad software testing in 2002, it is cost between 22 and 59 billion dollars annually in the US
- huge losses because of web application failures
	- financial services, and credit card applications
- in Dec 2006, one of the offers on Amazon which was a buy-one-get-one-free offer turned into a double discount


# testing nowadays
- there is more safety critical, real-time software
- embedded software (in your phone, for example)
- enterprise applications mean better programs, more users
- free software increases our expectations
- security is now about software faults
	- more reliable software is more secure software
- web offers new deployable platform
	- more available, but also competitive
	- web apps are highly reliable
bad testing effects everyone, and the economy as well

- because of this, testing is getting more important in software nowadays


# validation and verification
- validation: evaluating software at the end of development to ensure compliance with intended usage (does what you want it to do)
- verification: determine whether the product of a given phase in the software development process fulfill requirements from pervious phase


# testing goals based on maturity 
- level 0
	- no difference between testing and debugging
- level 1
	- purpose of testing is to show correctness
- level 2
	- purpose of testing is to show software DOES NOT work
- level 3
	- not used to prove anything, but rather used to reduce the risk of using the software
- level 4
	- testing is a mental discipline that helps all IT professionals develop higher quality software

## level 0
- same as debugging, does not distinguish between behavior and mistakes in the program
- does not develop safe or reliable software

## level 1
 - show correctness, however it is not possible to achieve
 - no failures?
	 - does not really prove that it works and meets requirements
 - test engineers do not have:
	 - specific goal
	 - real stopping rule
	 - formal test technique
	 - test managers are powerless

## level 2
- look for negative activity, show only failures
- testers do not like developers
- what if no failures?

## level 3
- when we use software there is some element of risk
- that risk could be small, could be big
- testers and developers work to reduce this risk in this level

## level 4
- testing is one way to increase quality
- test engineers become technical leaders of project
- want to measure and improve software quality
- should help developers

# tactical goals? why each test?
- if you don't know the reason behind every test, conducting it is useless
- write out your test objectives and requirements
- what are your planned coverage levels
- how much testing is enough?
- common objective - spend the budget, test until ship-date
	- sometimes called the date-criterion

- if you don't start planning for each test when the functional requirements are FIRST FORMED, you will never know why you're conducting the test
- threshold reliability requirements?
- what fact does each test try to verify?
- requirements definition teams need testers

# cost of not testing
- poor managers will say "testing is too expensive"
- most time consuming and expensive part of the development process
- not testing is even more expensive
- the cost of testing increases as time goes on
	- if you don't do it early on you will regret it later
- planning for testing also expensive


# why test software?
- eliminate faults as early as possible
- improve quality, cost, and preserve customer satisfaction