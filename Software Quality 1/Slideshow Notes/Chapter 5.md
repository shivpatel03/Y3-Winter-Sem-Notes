- old view of testing is that each development phase is very different than one another
	- unit, module, integration, system, etc.
- the new view is in terms of structures and criteria
	- input space, graphs, logical expressions, syntax
- test design is same at each phase
	- creating model is different
	- choosing values and automating them is different
- we use the criteria to give us test requirements

# new: test coverage criteria 
- testers job: define a model of the software, then find ways to cover it
- test requirements: specific part in the software (known as an artifact) that the test must cover
- coverage criterion: rules that impose test requirements on a test set

# structures 
- structures extracted from software artifacts
	- graphs: extracted from UML use case, finite state machines, source code, etc.
	- logical expressions can be extracted from decisions in program source, guards on transitions, conditionals in use cases, etc.
- not the same as "model based testing", which creates tests from a model that describes some aspect of the system under a test
	- model describes part of the behavior
	- source not considered a model

# coverage 
- you must have at least one test for every test requirement within a set of test requirements
	- you must have a test for every single test requirement and make sure that it covers that particular problem to test
- infeasible test requirements: requirements that cannot have any tests run to test them
	- therefore, 100% coverage is impossible, in practice 


# coverage level 
- number of test requirements that are satisfied : number of test requirements overall

# two ways to use test criteria
1. create test cases to satisfy these criteria
	1. test cases are made with criteria in mind
	2. the default and most obvious way to use criteria
2. generate test cases externally and measure against the criteria
	1. test cases are made without criteria in mind

- test criteria are sometimes called "metrics"

# generators and recognizers
- generator: procedure that creates values to satisfy criteria
- recognizer: procedure that chooses whether a set of values satisfies a criteria
- easier to recognize than to generate
- coverage analysis tools are helpful

# criteria vs. subsumption
- criteria subsumption: a test criterion $C_{1}$ subsumes $C_{2}$  $\iff$ every set of test cases that satisfies criteria $C_{1}$ also satisfies $C_{2}$
- must be true for EVERY SET of test cases


# pros of  criteria-based test design
- criteria maximize the "bang-for-the-buck"
	- requires fewer tests that are more effective in finding faults
- minimal overlap between tests
- traceability
- "stopping-rule" is defined, knowledge of when to stop and how many tests are needed is clear
- easier to automate

# good criteria-coverage criterion
1. should be easy to compute tests requirements automatically 
2. efficient to generate test values 
3. results should reveal as many faults as possible

- subsumption is only a rough approximation of fault revealing capability
- we need more data on how to compare coverage criteria

# test coverage criteria 
- traditional testing expensive and labor-intensive
- formal coverage criteria used to decide which test inputs to use
- more likely that tester will find problems 
- more assurance of high quality and reliability
- stopping rule for testing is clear
- criteria makes it efficient and effective


# improving testing 
- testers need better software tools 
- use practices and techniques that lead to efficient and effective testing 
- testing teams need more technical expertise 
	- developer expertise is needed
- testing teams need to specialize more

# issues with adoption of a new process
1. lack of test education
2. necessity to change process 
	1. using a new testing technique may require major changes in existing development processes
3. usability of tools
4. weak and ineffective tools

# what we need from researchers
1. isolate:
	1. invent processes and techniques that isolate the theory from most test practitioners
2. disguise:
	1. discover engineering techniques, standards, and frameworks that disguise the theory
3. embed:
	1. theoretical ideas in tools
4. experiment:
	1. show that there is some economic value of criteria-based testing
5. integrate high-end testing with development

# what we have to teach
1. disguise theory from engineers in classes 
2. omit theory when not needed
3. restructure everything to teach more than test design and theory
	1. teach more test automation, test evaluation, human-based testing, TDD

# changes we must make in practice 
1. reorganize QA teams to make good use of everyone's abilities
2. retrain tests and QA teams to use a process like MDTD
3. encourage researchers to embed and isolate
4. get involved in the design of courses through industrial advisory boards

# summary
- many companies still use old methods of testing
	- no automation, can miss a lot of requirements and criteria
- some companies automate human-designed tests
- but it is best if
	- companies use both automation and criteria-based testing 