- for the triangle program, an example of categories for the output could be:
	- `output = {ERROR, NULL, ISO, EQU, SCA, RIGHT, etc.}`
	- these are all categories (types/groups/partitions)
- you can also make partitions for the inputs, these are some examples for the same triangle program
	- `s1, s2, s3 = {invalid, valid numbers, int max, -0, etc.}`
	- these are all possible input categories for s1 s2 and s3

# Input Domains
- the input domain for a program contains all the possible inputs to the program
- for even small programs, there is an input domain, and it can be so large that it may as well be infinite
- testing is fundamentally about choosing finite sets of values from the input domain
- input parameters defines the scope of the input domain
	- parameters to a method
	- data read from a file
	- global variables
	- user level inputs

# Testing 
- black-box or white-box testing, there is also gray-box

## Black Box
- You don't really care what's inside, you just care about the output and whether you get the right output or not
- we don't have access to the code
- in the example of the triangle program
	- we don't have access to the methods themselves, only care about the inputs and outputs
- WE AN

## White Box
- You do care about the code that is inside the method
- you can see the code, you have access to it
- you can model the code as the graph


Back to the triangle program example
- with the three different input variables, there is essentially an infinite number of input combinations that we can think about

- select a particular test case (test case is a set of any input values mapped to an expected output)
- we should make our partitions for inputs in such a way that if you choose any test case from that partition, you will get a set of input values such that they will represent the rest of the partition
	- any value selected from a partition should be chosen in a way such that any value in the partition would cause the program to behave the same exact way
		- if you choose a random test case from partition A, it should be a test case that is representative of the rest of the partition
	- for the triangle program
		- if you give it `1, 1, 1`, and it gives you an equilateral triangle
		- you can assume that you don't have to give it `2, 2, 2` to check if it's an equilateral triangle
		- this reduces the need for redundant tests
		- keep in mind that something like `0, 0, 0` would not be in this `equilateral triangle` partition in the first place, it would be in the `error inputs` partition (for example)
- there are different ways of partitioning inputs 
	- example
		- in the first way, you partition in to 15 groups
		- in the second way, you partition into 50 groups
		- in the third way, you partition into 100 groups 
		- it does not matter, as long as you can make sure it complies with the above statement


## Black Box Testing
1. Analyze input and output and partition them
2. Select one input combination from each partition and calculate the expected output (this is your test case). you do this in a way where 1 partition is equal to 1 test case (one test case represents the entire partition)
	1. divide the input and output into classes. select the class such that the behavior of the program for any input from the class is the same/equivalent