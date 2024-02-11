# Problems to be Solved by Computers
- Easy
	- arithmetic
	- sorting lists of numbers
- solved after a lot of effort
	- playing simple board games
	- playing chess
	- recognizing faces in pictures
	- usable automated translation
	- playing Go
	- usable real-time translation of spoken words
- Real progress (not solved yet)
	- driverless cars
	- automatically providing captions for pictures
	- understanding story and answering questions about it
	- human level automation translation
	- interpreting what is going on in a photograph
- Nowhere near solved
	- writing interesting stories
	- interpreting a work of art
	- human-level general intelligence

- The history of AI is entangled with the history of computers


# What is AI
- Symbolic AI - tries to emulate consciousness
- Machine AI and everything else are non-symbolic AI
	- most of the material in this course is non-symbolic AI
- one of the biggest problems is in 'large language models' is 'hallucination', and they are a symbolic AI
	- this does not happen with non-symbolic AI

- systems that think like humans
- systems that think rationally
- systems that act like humans
- systems that act rationally

- suppose we have two dimensions of AI
	- the other is whether they think or act
	- one of them is whether they think/act rationally or more like humans
- the combination of these dimensions results in the four systems above

# Goals of AI

- AI is the attempt to reach two goals: 
	- to know how "natural intelligence" works
		- not as successful the next one
	- to build an "intelligent entity or agent"
		- this is the one where we had more research than the first one
	- the research in previous years has shown that the second goal has been further reached than the first

## Goal 1 
- we didn't really get far on this goal, instead most of the research was focused on the next one
## Goal 2
- What is an "intelligent agent?"
	- define agent/entity: a system that takes input and generates output (like all other systems) EXCEPT it also interacts with the environment (it is not in a "vacuum")
	- an intelligent agent example is the Turing Test
		- focused on: how can you make an agent seem like a human instead of what is an intelligent agent?
		- 'how can you make an agent seem like a human'
			- thinks more about the function of the agent
		- 'what is an intelligent agent?'
			- characteristics and behaviour of the agent
- we cannot prove that you have consciousness

### Example:
- Automobile Airplane
	- before we had airplanes, we wanted to create something that works as a bird. and because of this, we were trying flaps and things alike, but that didn't work
		- this killed many people 
		- the Wright brothers came around and tried something different, but still to FUNCTION the same way as a bird (i.e. flying)
	- before talking about intelligent agent, lets talk about "agent"
		- similar to the airplane, AI isn't supposed to BE humans, but instead act like humans through perhaps a different mean of understanding information
		- agent is something that is able to interact with ITS environment (not THE environment)
		- this agent also reduces some of the information that it gets in order to learn faster
			- similar to engineers. when they research something they don't check everything, instead they reduce things that they care about and research about that
		- the behavior of an agent is then reduced to a chain of inputs and a chain of outputs
			- this differs from humans as humans do not work this way
		- agent: mapping chain of inputs to a chain of outputs
			- HOWEVER: it also reduces this chain of inputs and outputs
	- agent is an entity that is able to interact with it's environment
		- why not "the" environment
			- because every agent has its own environment. this environment has many words in textbooks: 'world', 'universe', 'environment', but they are all the same
			- this is also seen in philosophy, where every person has their own environment
- Imagine a vacuum robot:
	- the environment of this robot is ONLY the floor of your house
	- this does not include anything else inside of this house 
		- the wall, ceiling, closets, etc. are not seen by this robot at all
	- therefore, this agents' environment is ONLY the floor and not the rest of the house

- Key concepts of definition of Agent:
	- Perceiving
		- understanding input
	- Acting
		- doing something to get the output
	- Agent's Environment (world or universe)
		- raises a question: can an agent change the environment?
			- YES, that is the whole point of AI 
			- example: in chess, when you move, the environment changes and the agent has to adapt to it

### How does an agent perceive and act
- assume a system that has sensors and actuators
- this system takes in an input and produces an output
- this output goes through the environment and comes back in as an input
- this system with the sensors and actuators is the agent itself


- Think about another view:
	- you take in inputs x_1 to x_n, which goes into a function F, and outputs y_1 to y_n
	- white box: agent program
		- meaning you care and know about the specifics about the program and how it converted the inputs into outputs
	- black box: agent function
		- meaning you don't really care about the specifics about the agent's code or exactly how it works, you only care about the output

## Four Possible AI Scenarios:
- Two dimensions:
	- human-like or not
	- capability of thinking or acting
	- results in this chart:
![[img/Pasted image 20240112143612.png]]
- somewhere on this spectrum is an AI
- think humanly: 
	- have morals, empathy, etc.
- act humanly:
	- the Turing Test
	- it's behavior is not differentiable from a human function (such as ChatGPT, DALL-E, etc.)
- act rationally: 
	- in this course, we want to design rational agents
	- we don't know how rational thinking is, 

- Two questions: 
	- q1. what does it do? 
		- "act" vs. "think"
		- Act: function for example: function of flying object (airplane) (choose this one)
		- Think: 
	- q2. how does it do it?
		- Rationally vs. Humanly=
		- Rationally: making the best possible output from the inputs given (choose this one)

- An agent is anything that can be viewed as perceiving its environment through its sensors an acting upon that environment through actuators
	- in ChatGPT: the actuator is the text output and the screen
	- very abstract concept
- Robots vs. Agents: 
	- robots have some type of physical presence
	- while agents are just a system (ChatGPT as an example again)

- Question, why don't we use "input" instead of "percept"?
	- Answer: because we want to emphasize on the "agent's uptake, understanding, and perception of the world"


## Vacuum Cleaner World 
- has two partitions
- ![[img/Pasted image 20240112145039.png]]
- A and B are the environments, and it will 'percept' whether it is clean or dirty: 
	- A-Dirty, B-Dirty
	- A-Clean, B-Clean
- also has cations: Left, Right, Such, NoOperation


This is a general question that might show up on an exam; 

Why is a calculator not an agent? 
- In AI we are interested in agents that have these two major characteristics
	- agent uses significant computational resources
	- the agent environment requires nontrivial decision making


- For the vacuum cleaner, this is the perception and action (input and output):
![[img/Pasted image 20240112145430.png]]
- take the first one.
	- vacuum is at the A condition above, and it is clean. So you go right and look for the next dirty area

```
function REFLEX-VACUUM-AGENT([location, status]) returns an action
	if status = Dirty then return Suck
	else if location = A then return Right
	else if location = B then return Left
```


## Rationality
- Fixed performance measure evaluates the environment sequence 
	- one point per square cleaned 