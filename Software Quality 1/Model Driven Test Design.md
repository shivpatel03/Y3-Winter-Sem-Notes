	artifact -> model -> test requirements -> refined requirements/test specs -> input vales -> test cases -> test scripts -> test results -> pass/fail

- use the node to indicate the branches that show up in the code
	- if/else statements break up into two nodes (two new branches) where the first node is the if statement, and the second node is the else statement

# While Loops
```
x = 0
while (x <  y) {
	y = f(x,y);
	x= x + 1
}
return(x)
```

the graph for this would look like this (as described)
- start at node 1, x = 0
- go to node 2, which is the while loop
- node 2 points to two nodes
	- 3 is if the while loop keeps running (`x < y`, and it runs whatever is in the while loop), and loops back to node 3
	- another node node 4, which is triggered when `x >= y`, and just returns

- in theory, you could join 1 and 2 but if you think about it, in the code, we are not setting x = 0 at every iteration of the while loop

# For Loops
```
for (x=0;x<y;x++){
	y = f(x,y);
}
return(x)
```

![[Pasted image 20240227190019.png]]
- this is basically the same as the while loop, and the code itself does the same thing as the while loop as well. 
- also we are incrementing `x=x+1` because at every iteration, the for loop increments by 1

# Do-While
```
x = 0;
do {
	y = f(x,y)
	x = x+1
} while (x<y);
return(y)
```

![[Pasted image 20240227190503.png]]
# Switch Statement 
![[Pasted image 20240227190454.png]]

# What do we do with these nodes in the context of testing? 
- focus more on the nodes where there are branches (if statements and while loops)


- Lets say we have a particular test case
	- it is an input and expected output
	- we will write Junit code for that test case
	- how can we model the execution of that test case code?
		- for every test case, look at the nodes from the graph and see which nodes we would like to test (how we want to go through the tree)
		- for every test case, we might follow another path
		- generally, for the test case, you start from the starting point, and you get to the final point
			- all the logic is somewhere between these two points in the graph
	- a "test-case path" is a connection between the starting point and the end point
		- and it connects nodes between them (depending on the test case)

- we need to have test cases such that all the possible paths in the graph have been visited
- how do we select the test cases?
- THIS IS WHAT TESTING-REQUIREMENTS IS
- if you are testing all the nodes, you are technically testing all the lines of code
	- this is something that you have to do for testing purposes

- the most error-prone type of nodes are the branches
	- so we have to visit the nodes and heavily test them
- another error-prone type of branch is the branches that come with loops, etc.

- come up with a design table
	- write that "this set of inputs will cover 20% of the nodes"
	- you should write enough tests where this number is 100% (they are added)
	- this is a design table

- the whole point of this model is to create a formulated way of getting the test cases for a specific program
	- it gets more rigorous than this, this is just scratching the surface
	- there could be an algorithm to convert code into a tree


# Edges in the Graph 
- a "graph" is made up of nodes and edges
- edges are the connections between nodes


# Testing with the graph
- once you make a graph, there are many ways to go about using it to create test cases
	- you can go through every possible edge
	- you can go to every node

- despite having all of these ways of doing it, this is the algorithm that we use:

1. Analyze source to derive flow graph
2. compute graph's Cyclomatic Complexity (C)
3. Select C test (basis) path to achieve required coverage
4. Evaluate test conditions to achieve each path 
5. Propose input and output values based on the conditions
6. Create test case for each basis with

- Cyclomatic complexity:
	- looking at the complexity of the code based on how many cycles (loops)
	- the more the cycles, the more paths you have to test in the long run
	- when you see a loop, you have to test every possibility of that loop
		- or branch
	- however, even though a graph that is more complex does not have the most cycles, that doesn't mean it's less complex
		- a smaller graph that has 2 cycles vs. a much larger graph with no cycles


$C=\text{MIN NUMBER TEST CASES for path coverage}$
the minimum number of independent, non-looping paths (called basis paths) required to achieve 100% PATH COVERAGE
to compute cyclomatic complexity C:
	$\text{C = edges - nodes + 2}$
	or, $\text{C = P + 1}$: where P is the number of binary decisions (predicate) in a flow diagram
	a binary decision has two edges flowing out
		P is a predicate node, which means that is it an IF statement (takes in one edge, and outputs two edges)

- although more branches = more complex, sometimes you can't avoid it
	- therefore, you must try to minimize it, NOT remove it completely
	- otherwise you will get inefficient code that is, in some cases, even more complex

- we are not looking for every single possibility in every single node, instead we are just looking for a way to formalize these things
- if there is a cyclomatic complexity C of 4, we need 4 test paths. this gives an idea of how many paths we need for a specific application depending on the complexity of a program


- we are trying to select a number of paths, but not ALL possible combinations
- that is why using C number of paths is useful, as it does not require us to use EVERY single possible path. 

# CFG - Control Flow Graph
- these are the graphs that we have been taking about the entire time

- this is called control flow because it goes through every single flow in the program
	- the arrows are very important, because it tells you how the code is going to flow
	- with a value P of 6
	- and 19 nodes
	- and 24 edges
		- difference of 5
	- C = 24 - 19 + 2
		- gives you cyclomatic complexity of 7
	- this is just the equation $C = \text{branches} - \text{nodes} + 2$
	- there is another equation: $C =  P + 1$
		- where $P$ is the number of predicates
			- notice that they are the same in this example (7 on both)
- we started with the notion that we should start with the simplest path
	- however, that changed to the "base" path
	- what is the base path? 
		- choose the most common/logical case
		- this is done by looking at the code, there is no formulated way to do it
		- it's the path that is most likely to be done
	- the second path is then something that is a little bit of a deviation from the first one
		- it visits most of the nodes that are in the first one, but changes a small section of the path 
	- we do not always deviate from the first path
	- if the branch deviates to the point where it cannot follow the first branch by much, it then finds another "most common path" in another branch
	- once you have done most/all of the possibilities of the first path (the base path), you then deviate from the second path that we made
	- using this approach, you would still have to use more branches than if you were to use the minimum number of tests that we covered earlier (using cyclomatic complexity)
- 