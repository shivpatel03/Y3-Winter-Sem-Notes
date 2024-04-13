# complexity of testing software 
- software is the most complex field of engineering
- "correctness" means nothing
- like other engineers, we use abstraction to manage complex items 
	- 'model drive test design' process
	- "model" meaning an abstract structure

# testing and debugging 
- testing: evaluating software by observing execution
- test failure: execution a test that results in a software failure 
- debugging: process of finding a fault given a failure (finding root cause given symptom)

# fault and failure model 
these four conditions necessary for a failure to be observed
1. reachability: location or locations in the program that contain the fault must be reached
2. infection: state of program must be correct
3. propagation: infected state must cause some output to be incorrect
4. reveal: tester must observe incorrect part of the program state

# software testing activities
- test engineer: professional in charge of one or more technical test activities
- test manager: in charge of one or more test engineers

# testing levels 
- acceptance testing: is software acceptable to user?
- system testing: test overall functionality of system
- integration testing: test interaction of modules
- module testing: test each class, file, module, component (done by developer)
- unit testing: test each unit individually (done by developer)

# object oriented testing levels 
- inter-class testing: test multiple classes together
- intra-class testing: test entire class with sequence of calls 
- inter-method testing: test pairs of methods in same class
- intra-method testing: test each method individually

# coverage criteria
- even small programs have too many inputs to test them all
- testers try to find the fewest inputs that will check for the most problems
- coverage criteria gives practical ways to search input space
	- removes overlap in the tests

## advantages:
- maximize "bang for the buck"
- provide traceability from software artifact to tests
- make regression testing easier
- gives testers an idea of when they can stop the tests
- can be supported with powerful tools

# test requirements and criteria
- test criterion: collection of rules and a process that defines test requirements
	- "cover each statement"
	- "cover every functional requirement"
- test requirements: specific things that must be satisfied or covered during testing

# old view: colored boxes 
- black box testing: looks only at external output, derives tests based on only that
- white-box testing: derive tests from source code internally in the software, includes branches, individual conditions, etc.
- model-based testing: derive tests from model the software

# model drive test design
- test design: process of designing input values that will effectively test software
	- one of the several activities for testing software
		- most mathematical, most technically challenging

# types of test activities
- testing broken up into four general activities:
	- test design
		- (a) criteria based: design test values to satisfy coverage criteria or other engineering goal
		- (b) human based: design test values based on knowledge of the program and human knowledge of testing (not really computer science degree, more biology, psychology, etc.)
	- test automation
		- embed test values into scripts that can be executed using code
	- test execution
		- run tests on the software
			- done by interns (lol)
	- test evaluation
		- evaluate results of the testing that has been done
- each requires different skills

- other activities: 
	- test management: sets policy, organizes teams, etc.
	- test maintenance: save tests for reuse as software evolves
	- test documentation: all parties are needed here
		- each test must have a "why"
		- ensure traceability through process
		- keep documentation in automated tests

# organizing the team 
- only needs one test designer, to work with several test automators, executors, and evaluators
- improved automation will reduce the number of executers (no need for manual labor)
- wrong people = inefficiency, low job satisfaction, low job performance
- test evaluators must have knowledge about the software and its domain, must be free to add tests that the engineers may not think about
- four tests activities are quite different
- many teams use the same people for all four activities

# applying test activities 
- to use our people effectively and to test efficiently we need a process that lets designers raise their level of abstraction

# using MDTD in practice
- lets one test designer do the math
- testers and programmers can do their part
	- find values, automate tests, run them, evaluate them

- you start with the software artifact (some piece of code, or method, class, anything)
	- create a model of it
	- create test requirements from it
	- refine the requirements and test specs
	- make input values
	- create test cases
	- create test scripts
	- check test results
	- pass/fail them
![[Pasted image 20240406141311.png]]
![[Pasted image 20240406141347.png]]