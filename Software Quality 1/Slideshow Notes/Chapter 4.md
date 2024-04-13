# Testing First 

# the increased emphasis on testing now
- you want to reveal problems as early as possible 
- this is good because the cost of fixing something further in the life-cycle of the software is an exponential curve

# traditional assumptions 
1. modelling and analysis can identify potential problems early in development 
2. savings implied by the cost-of-change curve justify the cost of modelling and analysis over the life of the project
- these are true, only if the requirements are not changing at all
- however, requirements change
- therefore, use Agile methodologies 

# why Agile? 
- these methods recognize that neither assumption is valid for many current projects
	- software engineers are not good at developing requirements
	- do not anticipate change
	- many of the changes that we do anticipate are not even needed
- requirements tend to go out of date very quickly
	- we don't take time to update them
	- projects now change continuously
- agile methods start small and evolve over time
	- embraces software evolution

# limited view on correctness
- traditionally, we define all correct behavior completely at the beginning
	- what is correctness?
	- people are very bad at completely defining correctness
- in agile methods, correctness is relative to a specific set of tests
	- if software behaves as it should on the tests it is "correct"
	- instead of defining all behavior, we demonstrate them (run and show them through a test)

# test harnesses verify correctness
- test harness runs all automated tests efficiently and reports results to developers
- tests must be automated
	- automation is a prerequisite to test driven development (TDD)
- every test must have a test oracle that can evaluate whether or not that test is executed correctly
- tests replace requirements
- tests must be high quality, and run quickly
- run tests every time codebase is changed

# continuous integration
- agile methods are best when current version of software can be run against all tests at any time
- continuous integration server rebuilds the system, returns, and reverifies tests whenever any update is made to the repository
- mistakes caught earlier
- other developers are made aware of changes earlier
- rebuild and verify must happen asap
	- tests need to execute quickly
- continuous integration doesn't just run tests, but also decides if a modified system is still correct

# system tests in agile methods
- generally, testers make tests based on requirements
- but what if there are no official requirements documents?

# user stories
- user story is a few sentences that capture what the user will do with the software
- in the language of the end user
- small scale, few details, not archived

# adding tests to existing systems 
- a lot of software now is legacy
	- there is no legacy tests
	- legacy requirements are very outdated
	- designs, even if documented, are lost
- companies choose not to change software because of the fear of failure
	- how can you apply TDD to legacy software that does not have tests? 
- create an entire new set of tests? expensive.

# incremental TDD
- when change is made, TDD tests are used just for that change
	- refactor
- as project progresses, collection of TDD tests continue to grow
- eventually the software will have strong TDD tests

# testing shortfall
- do TDD tests test the software well? 
	- they do not achieve good coverage
	- they do not find most of the faults
	- even if tests pass, is software reliable? no
- why not? 
	- agile tests focus on "happy paths"
		- what should happen under normal use
	- often miss:
		- confused-user paths, creative-user paths, malicious-user paths
- to overcome this: 
	- design good tests
	1. user a human-based approach
		1. create user stories that describe paths where the user is not happy
		2. how do you know when you're finished?
		3. some people are very good at this, others are bad
	2. use modelling and criteria
		1. model input domain to test cases
		2. model software behavior with graphs
		3. a built-in sense of completion
		4. much easier to teach
		5. requires discrete math knowledge

# summary
- more companies putting testing first
- decrease cost, increase quality
- different view on "correctness"
- embraces evolutionary design
- TDD not test automation
	- test automation is prerequisite to TDD
- agile tests are not enough, though