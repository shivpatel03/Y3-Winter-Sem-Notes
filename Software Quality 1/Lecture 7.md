- Now that we have learned more about Junit, any testing framework requires two types of functionality
	- observability
		- how easy it is to observe the behavior of a program in terms of its outputs, effects on the environment, and other hardware and software components
		- `@Tag`
		- `@DisplayNames`
		- example of annotations that help with controllability of the test
			- `@BeforeAll`
			- `@AfterAll`
			- `@Test`
		- This is all very useful when considering TDD
			- in TDD, we make a large table of tests (called a test table). from there, we take a subset of these tests and try to solve them
			- Sometimes these subsets can be a small part or feature of the program
			- we divide into "groups" or "suites" of tests
			- a row of these "suites" is equal to a test
			- a row/test case is executable by `@Test`
	- controllability
		- How easy it is to provide a program with the needed inputs, in terms of values, operations, and behaviors

# Some annotations
```
@RepeatedTest(3)
void math_add_4(RepetitionInfo repetitionInfo){
	System.out.println("Rep number: " + repetitionInfo.getCurrentRepetition());
	assertEquals(3, repetitionInfo.getTotalRepetition())

}
```
- this repeats this test 3 times, as defined by the header

## `@DisplayName`
- can be used to create a name for a subset of tests


# Red-Green Refactoring
- When you initially have a test case, you will not have any code to test, therefore you will get a red, indicating a failure
- When you write some code, and pass it, and it becomes green
- You then move on to the next test case in the subset
	- This will obviously give you a red test (indicating a fail)
- You refactor the code you had before, then you should be able to get a green test case
- This is just a cycle that results in code that passes all test cases in the subset of tests