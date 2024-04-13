# v-model
- for every layer (requirements, system requirements, global design, detailed design), you do the planning, but also create test cases for the corresponding types of tests
	- while finding requirements, prepare test cases for acceptance testing
	- while finding system requirements, prepare test cases for system testing
	- while planning global design, prepare test cases for integration testing
	- etc.
- to get better software quality, you should follow something


# average cost for fixing bugs
- the curve is exponential
- the further into the development process, the higher the cost for fixing bugs gets
- the later you're trying to solve a bug, the more costly that fix will be
	- you as an engineer are focused on bringing the best software designs

# TDD process
- red + green refactoring
- start with designing test cases, list them in test case table
	- then go to a continuous loop of testing, writing code, enhancing it, repeat
	- write tests, then write code to pass the test (green)
		- if it passes, then refactor
		- then add more testing
- puts testing first
- makes people think more about quality and testing
- helps write better code, faster time
# automation
- the job of a test engineer
	- design test cases
	- execute test cases
	- evaluate result of test cases
	- job is to find bugs/errors/failures in the system. report these to the software developer. help the software developer debug the system. 
- Junit 
	- parameterized test:
		- allows to run one method (written once)
		- but that method can be run with tests that are in an external .csv file
- CI/CD
	- continuous integration + continuous deployment
	- plan, code, building code, testing, releasing (release management), deploy system, operate, monitor (find bugs or add enhancements), then plan how to fix these bugs, repeat
	- tools:
		- Docker
		- Git
		- Maven
		- Jenkins
		- etc. (plugins)
# test case design 
- created in a formalized manner
- using well-known algorithms
- not in an ad-hoc manner

- model driven test design
	- software artifact
		- requirement, design, development phase
		- can be code, specification of code, sequence diagram, etc.
	- create a model of it
	- understand requirements associated with that model
	- you will eventually get some test cases
	- and then put those test cases into a test case design table
	- create scripts (Junit)
	- get the results
	- evaluate test cases
- in the test case design table that you created, you will have some test cases that are found through the CFG, some found through boundary value analysis, etc.
	- you then create automated tests for them
	- some of these artifacts require seeing the code and some of the other ones do not (white box vs. black box)

# black box testing
- no access to code
- have some input, you get output
- you only care about input and output

- start by identifying different possible outputs from the program
- and then identify all possible input domains that go into the program
- partition the inputs into different areas
	- inputs of partition 1 should result in some output 1
	- inputs of partition 2 should result in some output 2
	- inputs of partition 3 should result in some output 3
	- etc.
- these partitions can have a discrete number of input values, or continuous
	- selecting any of the inputs from the partition into the program will result in the same result as if you chose another input from that partition

test case table: 

| pre-conditions | inputs | expected outputs | post-conditions |
| -------------- | ------ | ---------------- | --------------- |
|                |        |                  |                 |
- for the inputs, you can have the following tests:
	- take all possible input combinations
		- if one set has 3 and another set has 2, then you will have 6 test cases
		- this will provide the most robust testing, very high quality
	- "each choice" coverage
	- "pair-wise" coverage
		- 20% effort/time/money, 80% money
		- if you think that the number of test cases is too small, you can increase the number of test cases to get a more robust set of test cases
	- "base-choice" coverage
	- "multiple-base choice" coverage
	- boundary coverage is important because it tests the edge-cases of every test case
		- testing negative inputs, testing inputs just at the boundary, etc.

# white box testing 
- test input -> application code -> test case output
- get code -> model as CFG -> calculate cyclomatic complexity -> make set of paths -> create test cases
	- cyclomatic complexity:
		- how many times nodes branch (loops and if statements)
	- make set of paths
		- can be done using path testing algorithm
	- create test cases
		- done with path sensitization
		- create algebraic equation, use Kmaps
		- example: $\bar{A}C+AD$ etc.
		- 