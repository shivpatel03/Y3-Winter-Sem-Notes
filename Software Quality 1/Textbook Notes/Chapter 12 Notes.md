- developers want tests to become "real" as soon as possible
	- allows for immediate feedback
- this section explains technical problems that arise during implementation of test cases

- software programs have many pieces of software (many sizes as well)
- programmers responsible for testing the lowest level components
	- after that is done, the testing must be done to see how these components collaborate
- **Integration Testing**: testing of incompatibilities and interfaces between otherwise correctly working components. testing needed to assure correct integration of subcomponents into a bigger working component. 
	- often done without a complete system
	- tester may just want to see how only two components in the system work

- a **component** in this context is a piece of software that can be tested independently. therefore, classes, modules, methods, packages, and even code fragments can be considered to be components.

# 12.1 Integration Order
- components depend on each other in many ways
	- one class may use methods and variables defined in another one
	- class may inherit from another one
	- one class may aggregate objects from another one
- if class A uses methods that are defined in class B, and B is not available, then we need to test doubles for methods to test A. therefore, it would make more sense to test B first, and then A after (instead of test doubles)
- this is called the Class Integration Test Order Problem (CITO), but it applies to components more than it does it classes
	- the general goal of CITO is to integrate and test classes in an order which will require the least scaffolding or additional software (because creating test doubles is considered a large cost in integration testing)
- if the dependencies between classes do not have any cycles, the order of the integration testing is said to be quite simple
- classes that are not dependent on any other ones are tested first
	- then, they are integrated with classes that do depend on something else
- if classes are represented in a "dependency graph", where every node is a class, and edges are dependencies, this approach follows a *topological sorting* of the graph
- gets more difficult when the graph has cycles, because then we will get to a class that depends on another one that has not yet been integrated or tested
- "stubbing" is required
	- lets say A depends on B, B depends on C, C depends on A
		- the tester must break this loop by choosing which one to test/integrate first
- cycles are generally something that is recommended against, they make testing much more difficult and expensive
	- however, it is not possible to completely ignore them
	- sometimes throughout design processes, you have to add functionalities, which will inevitably lead to some issues

# 12.2 Test Doubles 
- think about the movies, "doubles" refers to stand-in actors for a specific scene
- test doubles replace software components that cannot be used during testing
- sometimes these components have not been written yet, sometimes they do something that we can't afford to happen during testing, etc.
- **test double**: software component (method, class, or collection of classes) that implements partial functionality and is used in place of the "real" software component during testing
- help solve problems of controllability and testability
- four reasons to use a test double;
	- component has still not been implemented. creates problems during testing if the components' functionality is required for for the other parts of the system to run
	- some components implement unrecoverable actions. although these actions are needed in practice, they are not during test. Examples: exploding a bomb, carrying out a trade in a financial system, or sending an email in a messaging system
	- many systems interact with unreliable or unpredictable resources such as network connections. if the test uses the resource incidentally, rather than testing the resource, using a double can avoid problems that occur if the resource fails or behaves in an unexpected way
	- some tests run very slowly.
- writing doubles takes time + effort, and they can also be incorrect. double must be built, and then tools can be used to make it possible for the test engineer to quickly and easily generated he needed functionality. 
## 12.2.1 Stubs and Mocks: Variations of Test Doubles 
- sometimes when testing, developers and testers need extra software components, which is called scaffolding
	- test doubles
	- and test drivers
		- software component or tool that takes care of the control and/or the calling of a software component. (example: JUnit)
- the traditional way of making a test double is by making a test stub
	- skeletal or special purpose implementation of a software component
	- used to develop or test a component that calls a stub or depends on it
	- replace a called component
- responsibility of test stub
	- return value to a calling component
	- these return values are usually not the same as the ones that would come from the typical component, otherwise we would not need the stub
- an example of as test stub:
	- basic action is to assign constant values for the outputs
	- can return `null` or some type of hand-crafted values, depending on the application

- there are some more sophisticated tools that are used to find the components that require stubs

- recently, stub has evolved into a mock
	- and then eventually led to test doubles
- mock is a special purpose class that includes behavior verification to check that a class under test made the correct calls to the mock. Java mocking tools generate mocks from an object or interface using a Java reflection.
- these tools allow engineers to specify, rather than program, limiting behavior including return values - a key enabler for interaction-based testing.
- interaction based testing defines success by how objects communicate with each other as opposed to what the objects do. That is, interaction-based testing does not ask whether an object did the job correctly, but whether it was asked to do it's job.

- messaging system that sends email messages to consumers
	- with some software, we need to look at the values of certain variables after the test finishes (state-based testing)
	- in this messaging system example, we need to make sure that the mailer actually sends out a specific message
	- the idea is not to check that the message is sent out, but rather to verify that a call was made to the messaging system to send a message (interaction-based testing)