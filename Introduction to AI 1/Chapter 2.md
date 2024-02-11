AI Agents are a subclass of Agents 

want to categorize different environments and different agents 


# Different Environments
## Observability vs Non-observable Environments
- What is the difference between chess and a card game
	- In chess everything is known, 
	- In poker everything is hidden 
	- the point is that in chess, no matter how complicated the environment is, the whole board is fully known (we can see the other opponents game/strategy)
		- this is called "fully observable environment"
	- in poker, you're not entirely sure the strategy or the other person's hand
		- this is called "unobservable environment"
	- these two are the first attribute of an environment
	- another example: 
		- a self-driving car is deterministic and partially observable
## Deterministic vs Stochastic Environments
- deterministic means: 
	- next state of the environment is dependent on the previous states of the environment
	- example: chess
		- the next move will depend on the current environment, etc.
	- in backgammon, the next state depends on the present state as well as an element of chance
- stochastic means: 
	

## Competitive vs Collaborative
- an agent is said to be in a competitive environment when it competes against another agent to optimize the output
- the game of chess is competitive against other agents
- an agent is said to be collaborative when multiple agents work together for one target
	- when multiple self driving cars are found on the road, they work together to not crash

## Single agent vs. Multi agent 
- an environment consisting of only one agent is said to be a single-agent environment 
	- person left alone in a maze to find a way out is an example of a single-agent system
- an environment involving more than one agent is a multi-agent environment
	- the game of football is a multi-agent system as it involves 11 agents working together 

## Dynamic vs Static 
- environment that changes often: dynamic 
	- roller coaster is dynamic because it is set in motion and the environment is changing often 
- idle environment with no change: static
	- empty house is static because no change in the surroundings when an agent enters 

- in reality sometimes the agent themselves change the environment itself, but we have to simplify and not take this into consideration

## Discrete vs. Continuous
- If an environment contains of a finite number of actions that can be deliberated in the environment to obtain the output. it is said to be a discrete environment 
	- game of chess is discrete as it is only a finite number of moves
- the environment in which the actions are performed cannot be numbered is continuous
	- self-driving cars are an example of continuous environments as their actions are driving, parking, etc. which cannot be given a discrete number (therefore, continuous)

## Episodic vs. Sequential 
- in an Episodic task environment, each of the agent's actions are divided into atomic incidents or episodes. there is no dependency between current and previous incidents. in each incident the agent receives input from the environment 
- CONTINUE FROM THE NOTES, THIS IS NOT EVERYTHNIG 

## Known vs. Unknown
- in a known environment, the output for all probable actions is given. Obviously, in case of unknown environment, for an agent to make a decision, it has to gain knowledge about how the environment works


- in unknown, we cannot calculate the outcome beforehand
	- example: the mars Rover, when it was sent to Mars for the first time, we had no idea what the environment would be like, and we were not able to figure out how we'd go about exploring that environment beforehand


# Agent types: 
will start from very simple to complicated 


## Simple reflex agent
- has a mechanism, you give an input, it does something based on whatever your input was and preprogrammed logic, and then gives an output
	- senses input from environment (using sensors)
	- asks 'what is the world like now?'
	- and then asks "what should I do now?"
		- also takes in condition-action rules to make this decision
	- sends to actuators which outputs back into environment

## Simple reflex agent with state
- instead of just taking input and checking it every single time, it will only check it and do something with it based on the current state
	- the state changes with previous inputs that have come in before 

## Goal based agent 
- you define a goal, the agent will reduce its state from the goals that are defined
	- lets say, you define that the road should be clean 
	- you want to reach this goal now, so every step will be dedicated towards reaching the goal 


## Utility-based agent 
- not only do we want to reach a goal, while minimizing costs

- Example: map that wants to go from A to B 
	- B is goal obviously 
	- you have map()
	- and you have origin
	- this may seem like a goal-based agent, but you would like to minimize cost while maximizing speed

## Learning agent
- all of the previous ones that we just look at, we as humans have to come up with rules, and how to act based on certain inputs 
- from learning agents, agents try to learn those rules on their own
- not all learning agents are machine learning
	- we should give that knowledge as semantic information
	- however the most famous types of learning agents are machine learning




# Goal based agents 
- you have agents that have tools to collect environmental information (sensors)
	- agent can collect knowledge from environment 
- the idea is that the agent wants to do some actions to determine some goal
- lets say you want to design an agent to reach from point A to point B
	- we need a map, because we have to find a structure in the environment that is given 
	- which is given in the form of a map
		- the map of Romania for example
- when you want to solve a problem using search, you have to find the structure of the problem first
	- almost always, the structure of the problem comes in the form of a graph
	- we don't always assume that agents are moving geographically
		- instead, we get something in the form of a graph so it can be used more universally 
- so to learn the map of Romania, the structure of the environment would be the roads that are within the map of Romania
- you are always going to solve a problem based on the structure

## States: 
- agents also have states, and so does the goal-based agent 
- an example of a state is shown in addition carry-overs
	- the fact that there is a carry-over is based on a bit that represents whether there is a carry or not
		- two states: one state means that there is a carryover, and the other means that there is not a carryover
- ChatGPT has a state

- we define the state as kind of a representation of the environment