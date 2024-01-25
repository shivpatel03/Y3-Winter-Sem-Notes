# Searching

# Key Terms and Concepts 
- solutions: sequence of actions 
- search tree: 
	- good question: why search tree and not search graph? 
		- we turn every problem into a tree because it does not have any cycles
			- this makes it generally easier to find a solution more efficiently
	- a search tree:
		- root = initial state
		- branch (edges) = actions
		- nodes = states
	- goal state: the first step is always the goal test:
		- am I in the goal state?
	- expanding the current state
		- meaning applying each legal action to the current state
	- generating: expanding the current state will generate a set of new states
	- Frontier (open list): the set of all leaf nodes available for expansion
		- the process of expanding frontier list continues until we reach a goal state (in one of the goal testing steps), or if there is no node available for expansion, indicating an unsuccessful search

## 3 Steps of Search Process 
- good question: does it matter to know which state/node to expand next? 

- search strategy: to choose which state to expand next
- repeated state/loopy paths:
	- definition of solution (sequence of actions)
	- path cost:
		- past cost without loopy path < path cost with loopy path
	- if the repeated state way on the path to the goal, previous time would reach us to the goal
- redundant paths: when there is more than one path from one state to another state
	- loopy paths are a special type of redundant path
	- when expanding, any avoidable redundant (already visited state), must be avoided
	- then there are unavoidable redundant states
- separation: frontier list separates visited from unvisited states 

- state, state space and state space search
	- one of the most revolutionary ideas in modern science and engineering
	- another reductionist model in addition to filter theory
	- definition: a physical configuration or its representation
- node: only an abstraction of the state
- search strategy: what state to expand next:
	- expansion choice will form with frontier list

the general form is: 
- start with the search strategy -> goes into the frontier -> and you get data structures as an output
	- the search strategy dictates the data structure that we will need for that frontier


# Key Terms
- goal
- goal formulation
- problem formulation
- search
- solution
- execution
- (formulation, search, execution)

## Goals:
- to rule out/filter out nonrelevant objectives
- example: 
	- you are trying to figure out what to do next weekend
	- you have many options but you realize that you have a deadline on Monday
	- this is a goal that now filters out your options

## Goal Formulation (first step to solving a problem)
- where the status/situation of the agent in relation to its goal
- the first step to solving a problem

- example, consider a graph
	- you are at node A and your goal is node F
	- you need to know where you want to go before you start making moves
- in the example above, if the agent has the map, they will know not to go to specific nodes as they definitely don't lead to the goal destination (informed search)
	- however, if there is no map, they have to explore every possibility, including those that are definitely not going to lead to the goal destination (un-informed search)
## Problem Formulation
- The way we model, represent, and implement the actions of an agent to reach the goal

## Search (second step to solving a problem)
- the sequence of actions that agents take to reach the goal
- this sequence can have many options, and is not just locked to one in particular


	- generally this is how it goes:
		- you are given a problem, and you use a search algorithm to get a solution
		- this solution is given as a sequence of actions

## Execution
- when a solution is found, agent executes the solution
- question: what happens if the agent ignores the percepts?


# More Key Terms: 
- initial state
- transition model
	- a description of what each action does
- state space:
	- {initial state}x{actions}x{transition model}
- graph -> state space form a directed graph
- path -> a sequence of states connected by a sequence of actions
- goal test: to examine of the current state of the agent is the goal
	- used so that the agent doesn't run forever
	- must stop when the goal is found
- path cost 
- solution
- optimal solution:
	- the solution with the minimum path cost

# Node: action vs. outcome
percept -> agent -> action -> governing law of environment -> outcome



# Types of Problems
- Deterministic, fully observable -> single-state problem
	- agent knows exactly which state it will be in, solution is a sequence
	- single state means that the agent knows where it is (in terms of its position in problem solving) and where it is going (the target)
- Non-observable -> conformant problem
	- agent may have no idea where it is, solution (if any) is a sequence


# Single State Problem Formulation
- example: chess, tic tac toe
- a problem is defined through four items:
	- initial state
	- successor function `S(x) = set of action-state pairs`
	- goal test
		- can be explicit or implicit
		- explicit: example: `x = "At Bucharest"`
		- implicit: example: `NoDirt(x)`
	- path cost (additive)
		- additive means that every action you take has a cost, and you have to add the sum of the every cost to get the final cost
			- when going from point A to point B, you will have a cost for every intermediate step, each with their own cost 
			- additive means that each of these costs will be added up to get the final cost
		- e.g. sum of differences, number of actions executed, etc.
		- `c(x,a,y)` is the step cost, assumed to be >= 0
	- a solution is a sequence of actions, leading from initial state to the goal state

- Example: 
	-  in a vacuum, what is the goal?
		- to clean the floor
	- in chess, what is the goal?
		- to beat the opponent
- at the beginning of a search strategy, we don't talk about the cost instantly, we said 

- the real world is extremely complex
	- state space must be abstracted for problem solving
- (abstract) state = set of real states
- (abstract) action = complex combination of real actions
	- example: `"Arad -> Zerind"` represents a complex set of all possible routes, detours, rest stops, etc.
- for guaranteed realizability, any real state `"in Arad"` must get some real state `"in Zerind"` 
- (abstract) solution

# Depth First Search
- if you have a map, you are able to choose more wisely
	- this is informed search 
- if you don't have a map, you have to check every possibility
	- this is uninformed search

- Breadth first search
	- based on exploration
		- "explore all branches that you have in one state all the way through"
		- in one state you try all the actions and look at the outcome
		- also create new states
	- complete: guaranteed that you search from the top and you complete every state
		- the number of actions that you can take is indefinite, you can't use breadth first search
	- in what situation do we say that the search algorithm is complete? 
		- if there is a solution, we are guaranteed to find it
	- if the search algorithm is able to find the optimal solution
		- if there is just one solution, the algorithm has to be able to find it in the most efficient way possible
	- the things we look for in searches:
		- time complexity
		- optimal
		- completeness
	- B -> number of branches
	- D -> depth of solution
	- both the space and time comp of breadth first search is exponential
		- at least they guarantee that you will find the answer
- Depth first search
	- has better space complexity
	- it guarantees that it can reduce the space used in an algorithm
	- this is the alternative to BFS
	- instead of exploring all branches first, go all the way to the bottom and work up from there
	- uses LIFO
		- stack data structure
- question in the exam: 
	- given the tree, use different algorithms (BFS, DFS, and some other ones)
		- 