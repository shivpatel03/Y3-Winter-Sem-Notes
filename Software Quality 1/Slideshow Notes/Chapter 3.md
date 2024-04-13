# test automation 
- does the execution of tests, compares them, etc.
- reduces cost, human error, variance, and cost of regression testing

# software testability
- how hard it is to find faults in the system
- dominated by two problems: 
	- how to provide test values
	- how to observe the results

# observability and controllability 
- observability: how easy it is to observe the behavior of the program (outputs, effects of environment, etc.)
	- software that affects hardware devices, database, remote files have low observability
- controllability: how easy it is to provide a program with needed inputs
	- easy to control inputs from keyboard
	- inputs from hardware sensor or distributed software are harder
- data abstraction reduces controllability and observability

# components of a test case 
- test case values
	- inputs needed to complete execution of software under test
- expected results
	- result that will be produced IF the software works correctly
	- test oracle uses expected results to decide whether a test passed or failed
- prefix values
	- inputs needed to put software into appropriate state to receive test values
- postfix values
	- inputs that need to be sent to software after test case values are sent
	- verification values: values needed to see the results of the test case values
	- exit values: values needed to terminate program or return to "stable state"
- test case
	- values, prefix, postfix values, and expected results necessary for complete execution and evaluation of software under test
- test set
	- set of test cases
- executable test script
	- test case that is prepared in a form to be executed automatically on the test software and produce a report
- test automation framework
	- set of assumptions, concepts, tools, that support test automation

# what is JUnit
- open sourced, used to make repeatable automated tests
- features:
	- assertions for testing expected results
	- test feature for common test data
	- test suites for easily organizing and running tests
	- graphical and textual test runners
- widely used 
- can be used as stand-alone java programs, or within an IDE (Eclipse)

# JUnit tests 
- can be used to test:
	- entire object
	- part of an object - method or some interacting methods
	- interaction between several objects
-  intended for unit and integration testing, not system testing
- each test = one method

# writing tests for JUnit 
- each test will check a condition (assertion) and reports the test runner whether the test failed or succeeded
- test runner uses result to report to user or update display
- all methods return void


# JUnit test fixtures
  - state of the test
	  - objects and variables that are used by more than one test
	  - initializations (prefix values)
	  - reset values (postfix values)
  - different tests can use the same initialized objects without sharing state
  - objects used in test fixtures  should be declared as instance variables
  - they should be initialized in a @Before method
  - can be deallocated or rest using @After method

- think of using the `@Before` to create a list, that will be used for some tests in the file
- and then using the `@After` to delete that list and free up memory space

# data-driven tests 
- problem: you want to test a function multiple times with similar values
- simple example: adding two numbers
	- adding a given pair of numbers is just like adding any other pair, and you only really want to write one test
- data-driven unit tests will call a constructor for each collection of test values
	- same tests are then run on each set of data values
	- collection of data values are defined by method tagged with `@Parameters` annotation
- done with this:

```
@RunWith
public class DataDrivenCalcTest {
	public int a, b, sum;
}

public DataDrivenCalcTest (int v1, int v2, int expected) {
	this.a = v1;
	this.b = v2;
	this.sum = expected;
}

@Parameters
public static Collection<Object[]> parameters() {
	return Arrays.asList(new Object[][]{{1,1,2}, {2,3,5}});
	// the first test will have a=1, b=1, expected=2
	// second test will have a=2, b=3, expected=5
}

@Test
public void additionTest() {
	assertTrue("Addition Test", sum == Calc.add(a,b));
}
```

# tests with parameters: JUnit Theories 
- unit tests cannot have actual parameters
- contract model: assume, act, assert
	- assumptions (done before): limit values appropriately
	- action performs activity under security
	- assertions (done after): check result