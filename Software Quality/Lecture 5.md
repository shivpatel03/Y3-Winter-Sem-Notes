What are some of the artifacts that we create when designing code?
- software source code
- use cases
- UML diagrams
- documentation


When we are developing software requirement specifications, we also develop: 
- user acceptance test cases
- acceptance test cases

so we start with an artifact called "user requirement", and from it, we generate "user acceptance test cases". How do we do this? 

## The Model-Driven Test Design
- the V-model is a process
	- with every artifact that you generate, you have a part of the V Model that is specifically for testing
	- to determine the test cases, we use the model-driven test design
		- you are using the model driven test design to design test cases (as the name suggests)
- we will learn how to take a software artifact, follow an algorithm, and get the test-case to test for that artifact

- Build a model, and use it to drive your test design
	- white-box testing:
		- in the white-box, you have access to the code
		- we will learn how to create this piece of code into a graph
		- method 1 calls 2, 2 calls 3, 3 calls back to 2, 2 back to 1, 1 to 4, 1 to 5, 5 to 2, etc.
			- this just means that you're going to create a directed graph that shows the relationships between diagrams
		- once you convert the code into a graph, you have nodes, arcs, and numbers
			- from this graph we have to be able to get use cases out of that
```
main() {
	...
	...
}
```

- going back to the model drive test design:
	- you will get code (the artifact)
	- turn into a model (the graph we talked about)
	- tested requirements (found requirements from that model)
	- etc. we continue the flow


## The Triangle Method
- started with English text (software artifact), even though it is not code it is still considered the software artifact
- we were still able to design test cases for something based on the English requirements


## Testing Design
- usually has either black or white box testing
	- white box: has given code (the code is your software artifact, and that is used to create test case table)
	- black box: does not have given code (what we did in class to create the test case table)

# Does TDD slow development? 
- no 
- because the time you spent designing your tests would be pretty much the same
- TDD enhances the quality of the produced code, but are we developing faster or slower
- for the test design, you will use the Model-Driven Test Design
	- whether you were doing Model-Driven Test Design before or after code development, the time it takes to *create* the tests
- if it is a bigger project, finding a bug is a lot more costly, simply because localization is going to be much more difficult
- with TDD, even with large projects, TDD is going to allow you to localize very fast
- time it takes to design tests is the same before or after tests
	- however, designing the test first will help understand the problem faster, which helps code faster
	- also designing the test first will help localize code and make debugging faster as well

- TDD: 
	- design tests
	- take a subset of these tests
	- write corresponding code for these tests
		- make sure that this corresponding code passes these tests
	- we don't go to the next subset of tests until the code from the previous subset passes the tests
	- done in iteration
	- improves localization 
		- and you have very high confidence in the code that you write, and only then do you go to the next set of code
	- you spend more time thinking about the problem rather than solving it
		- the more you think about the problem, the more thorough your understanding of the problem will be, which ends up leading to more thorough code (that solves every part of the problem more efficiently)

## The Capability Maturity Model 
- level system that gradually increases better practices in developing software
- the higher you go, the more optimized the code is, and the more documented the code is and the more structured the development process is
- if you have a serious client (governments, secret shit), unless you have a very defined process, they will not hire you 
	- at least level 4 CMM
- if you work for a startup, you may be getting projects, but your clients will not be super serious about their software
	- a startup generally does not have a level above 3 on the CMM scale

- name a few companies that typically take software projects from the government
	- Boeing
	- IBM 
	- Oracle
- What is the difference between these companies and those that are just starting in Oshawa?
	- the companies mentioned above generally has a higher CMM model, and they are trusted to create good, high quality software for the government, as that is something that the government looks for
	- 