
# Design and Automation

- To design tests, you can use a test design table
- You can then use this table to create coded tests

## JUNIT
- `assertEquals(param1,param2)`
	- checks if the first input is the same as the second input
	- the first input is generally the expected output and the second is the actual output
- `assertNotEqual(param1,param2)`
	- same idea, just checks if the inputs are not the same
- why would you use this library instead of just simple print statements for testing
	- because you can automate these results



| Test # | Input | Expected Output |
| ---- | ---- | ---- |
|  |  |  |
- each row includes some code block, and you go through these rows by simply using a for loop, which is a lot easier 
- this is much more useful when there are many more test to be run
- JUNIT is just a java library that allows us to take the test design table and turn it into code
	- and then automate it 
	- and then immediately tells us which tests passed and which tests failed
- in order for a test to pass, that means that the `assertEquals()` function ran and returned 1 (true)
- you can convert your very large table or rows into code, and then JUNIT runs all the tests for you and gives you a green or red
	- if you get green, your code passes all tests in that section
	- if you get red, your code failed at least one test in that section

- when uploading to GitHub, you would have another directory in the root folder that clearly indicates that this repository has the testing methods in it (shown in class)

## The Difference between Testing and Debugging 
- Coming up with the design table and running these tests is called testing
- Debugging is fixed those tests that were wrong

- lets say you debug something that was wrong before, and you fix it using debugging. now once you're done debugging you have to go back and test everything

- there is also a tool for automated table creation 

## Jenkins 
- looks at whatever code is new in the GitHub repo immediately, and tests the new code that has been pushed
- then you can view what your new updated code can look at
- Jenkins sends this code from JUNIT
	- this process repeats until JUNIT returns only green (the most recent code on GitHub passes all tests)
- Jenkins is open-sourced
	- you can configure it to do something if the tests are not passed



### Should we design the test cases before or after the development process? 
- both before and after adds to your understanding of the problem
	- your code solves a problem
	- you would never be able to get very high quality code unless you actually understand the problem that you are trying to solve
- example: 
	- this example that we went over with the triangle program:
- for you to have a better understanding of the problem, do you write the test case table before or after? 
	- depends on the process
		- you have to consider the level of testing
		- if you are testing a small unit, the requirement of that small unit is not going to change very much
		- the requirement of the whole unit would change relatively often 
	- why do we gather requirements? before 
		- because we have to have a lot of work done to understand the problem, and then possibly while you write the code you get that you don't understand some part of the problem, so you update the requirements
	- designing the test case table before would help understand the problem better
		- while writing the code, you might end up not understanding something, and you could maybe go and update the design of the test case table again 
		- however, the majority of the test cases are designed before the development begins
	- this idea of creating test cases is called `Test-Driven Development (TDD)`
	- will be covered the most in tutorials
		- and also in the course project we are expected to use TDD
	- TDD is one of the fundamental ideas behind the Agile methodology of development
		- ultimately leads to better quality software 

- Testing is about ensuring quality, not really about debugging 
	- adopting a methodology such as TDD helps you create better quality software
	- with TDD,
		- design the table
		- take a subset of tests (column in the table)
		- convert them into JUNIT
		- write enough code such that it passes these subsets of tests
	- you repeat these steps until all the test cases are passed
	- this leads to a much better quality of software as you are completing all the testing requirements that you had from before
		- remember that these tests are from the requirements of the solution