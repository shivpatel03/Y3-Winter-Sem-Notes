
# Selection of Project Approaches 
- choosing right approach to particular project
	- called technical planning, project analysis, method engineering, methods tailoring
- in house: the methods to be used are dictated by organizational standards
	- developers and clients belong to same organization
- suppliers: need for tailoring as different customers have different needs

# Build or Buy? 
- in-house development means you build 
- outsourcing means you can either build or buy

# Advantages of Off-the-shelf (OTF) software
- cheaper, supplier can spread development costs over large number of customers
- software already exists
	- no delay while being developed
	- can be trialed by potential customer
- when there have been previous users of this software, most bugs and issues have been seen by them and have been fixed

# Disadvantages of OTF Software
- customers that have the same application don't have an advantage in the market
	- however, the way that this software is to be used also can give an advantage 
- customer may need to change the way that they work in order to fit in with the OTF software
- customer does not own the code to change anything if needed
- dangers of over-reliance on a single supplier

# Choosing Technologies
- outcome of project analysis is the appropriate selection of most appropriate methodologies and technologies
	- methodologies include technologies like OO dev.
	- structured systems and design methodology (SSADM) - set of standards for systems analysis and application design
- while technologies include mobile dev use knowledge-bae system tools

# Analysis Other Project Characteristic
- Some questions to ask before starting with a project
	- is it data-oriented or control oriented system?
	- is the software that is going to be produced going to be a general package or application specific?
	- is the system safety-critical?
	- what is the nature of the hardware/software environment in which the system will operate?

# General Approach
- Look at risks and uncertainties
	- are requirements well understood?
	- are technologies to be used well understood?
- look at the type of application being built
	- information system? embedded system?
- client's own requirements
	- need to use a particular method

# Structure vs. Speed of Delivery 
- structured approach:
	- "heavyweight" approaches
	- step-by-step method where each and intermediate product is carefully defined
		- "intermediate product" can be a prototype or just something to show for the amount of work that has been done so far
	- Emphasis on quality on the first iteration
	- example; use of UML (universal modelling language) and USDP (unified software development process)
	- future vision: model-driven architecture (MDA). UML supplemented by Object Constraint Language, press the button and application code generated from the UML/OCL model

# Life of the Unified Process 
- there are many cycles that have to be created
	- these usually go:
		- planning
		- analysis
		- design
		- implementation
		- maintenance
- within each cycle, there are four parts
	- inception: idea for development is good enough that it warrants going to the next part (elaboration phase)
	- elaboration: architecture is defined
	- construction: software brought from architectural baseline to the point where it is ready to be transitioned to the user community
	- transition: software turned over the community
- keep in mind: all of these parts can have any number of iterations
![[Pasted image 20240224121114.png]]

# Characteristics of Unified Process 
- architectural-based
	- the architecture sits at the heart of the project team's effort to shape the system
- iterative and incremental
- consists of the four Ps (People, process, product, and project)
- focus on risk
	- requires project team to focus on addressing the higher risks early in the project life cycle

## Iterative Development:
![[Pasted image 20240224121321.png]]
- represents the amount of effort that is going to be required at whichever portion of each iteration (deployment only happens mostly between C4 and T1, which is construction -> transition)

# Advantages of a Structured Approach 
- project risks that are related to changing requirements are resolved
- integration requires less time because it is carried out through the entire life cycle of the software
- because components are reusable, development phase consumes less time
- focuses on accurate documentation, so it can be considered "complete"

# Disadvantages of Structured Approach 
- complex, disorganized process
- reusability impossible to a project that incorporates a new technology
- needs expert team members
- having heavy documentation is expensive
- issues may arise at testing phase due to too many integrations

- customers are not interested in this approach

# Structured vs. Speed of Delivery 
- agile methods:
	- emphasis on speed rather than documentation
	- RAD (rapid application development) used to quickly develop prototypes
	- JAD (joint application development): requirements are identified and agreed through workshops with users
		- "hot-houses"

# Joint Application Development
- also known as "joint application design"
- used for requirement elicitation
- group oriented
- workshop sessions to share ideas

## JAD Team Roles
- Sponsor: 
	- one or more people
- facilitator: 
	- can only be one
- participant
	- multiple people based on scope and complexity of project
- scribe:
	- one individual

# What is Agile Methodology?
- idea of breaking projects into small goals, and aiming for these goals while adding new goals
	- individuals and interactions over processes and tools that are to be used on the project
	- working software over comprehensive documentation
	- customer collaboration (contract negotiation)
	- responding to change over following a plan

## Agile Methods 
- hothouse combines lean principles across different disciplines ![[Pasted image 20240224123133.png]]
- follows Lean Startup's "Build-Measure-Lean" loop
	- broken up into two "splits": creative sprint and design review
- the idea is that you get an idea (could be a problem to solve) (starting with the creative sprint to)
	- build something that demonstrates how you would solve that problem
	- then create a product mockup
	- team demos their solution and gets feedback (this is the measure stage)
	- at the start of the next "sprint" (the design review) the team decides whether they would like to persevere or pivot
	- feedback from judges in previous step is used as Data for critical learning
	- these learnings serve to generate new ideas to drive the next work for the next Creative Sprint
	- ![[Pasted image 20240224125029.png]]
## Sample day for a 2-Day Hothouse 
![[Pasted image 20240224125141.png]]

# Choice of Process Models 
- "waterfall" aka "one-shot" or "once-through"
- incremental delivery
- evolutionary development
- also use of "agile methods", example: extreme programming: mainly a particular way of doing incremental and evolutionary development

# Waterfall:
- literally just do one thing at a time, one after another
- if required, go back to the previous step
- ![[Pasted image 20240224125405.png]]

## Waterfall Advantages 
- classic model
- easy to understand/use
- gives structure to project
- works effectively once requirements are well understood
- easy to manage, no overlap between phases
- every stage needs to be checked and signed off
- BUT:
	- limited scope for iteration
- V-Model approach is extension of waterfall where testing phases are used to check the quality of development phases
	- testing and development are done side-by-side
# Prototyping (evolutionary):
- start
	- get requirements
	- create a quick design using those requirements
	- build a prototype
	- show to customer to evaluate
	- refine prototype
		- if required, go back to the quick design that was made earlier and fix it
	- if good, engineer product
	- stop
![[Pasted image 20240224125852.png]]
# Evolutionary Delivery: Prototyping
 - 'iterative process of creating quick and inexpensive live and working models to test out requirements and assumptions' - Sprague and McNurlin
 - major prototyping approaches: 
	 - "throw away" prototypes
	 - evolutionary prototypes
 - what is being prototyped?
	 - human-computer interface
	 - functionality

## Reasons for Prototyping:
- learning by doing
- improved communication
- improved user involvement
- feedback look established between developer and customers
- reduce need for documentation
- reduce maintenance costs
- can be used for producing expected results

## Prototyping: some dangers 
- users may misunderstand the role of prototype
- lack of project control and standards possible
- additional expense of building prototypes
- focus on user-friendly interface could be at expense of machine efficiency

## Other ways of categorizing prototyping:
- what is being learnt?
	- organizational prototype
	- hardware/software prototype ('experimental')
	- application prototype ('exploratory')
- to what extent
	- mock-ups
	- simulated interaction
	- partial working models: vertical versus horizontal

# Incremental Delivery 
- design -> build -> install -> evaluate
	- each incremental delivery does this to create increments and adds to the delivered system
![[Pasted image 20240224130403.png]]
## Incremental Process 
- first, create an incremental delivery plan 
	- identify system objectives
	- create an open technology plan
	- pan the increments that are going to be made
- then (these are done for each increment)
	- design increment
	- build increment
	- implement increment
	- evaluate results
		- use the feedback to either fix this increment, or go back to the delivery plan and change something
			- or both

## Incremental Process Benefits:
- feedback from early stages used in developing later ones
- shorter development thresholds
	- important when requirements are going to change
- user gets some benefits earlier, may assist cash flow
- project may be put aside temporarily: more urgent jobs may occur
- reduces "gold-plating" which are features that are requested but no used

## Incremental Process Disadvantages 
- some costs may be repeated
- "software breakage": later increments may change earlier ones

## example of incremental approach: 
- someone took on a project that was too big 
- they only account for half the effort that would actually be needed
- project was then re-planned to divide into 10 increments, each one should give something of use to the customer
- even though it was not EXACTLY what the customer needed, it still met the requirements that they requested, also within the delivery date
	- customer was happy

## Outline Incremental Plan
- used to figure out which increments to to start with
	- assuming increments are what solve a specific task (step)
		- this task has some value to customers and cost to developers
		- take ratio
- steps ideally from 1% to 5% of total project
- non-computer steps included 
- ideal if one step takes one month or less
	- not more than three months
- each step should deliver something useful to user
- some steps physically dependent on others

## Which step to use first? 
- some steps will have to come first because of dependencies
- others may be any order
- value to cost ratios are used
	- V/C where
		- V is a score 1-10 representing value to customer
		- C is score between 0-10 representing cost to developers

## V/C Rations: Example:

| step | Value | Cost | Ratio | Order |
| ---- | ---- | ---- | ---- | ---- |
| Profit reports | 9 | 1 | 9 | 2nd |
| online database | 1 | 9 | 0.11 | 5th |
| ad hoc enquiry | 5 | 5 | 1 | 4th |
| purchasing plans | 9 | 4 | 2.25 | 3rd |
| profit-based pay for managers | 9 | 0 | infinity | 1st |
higher number gets higher order

# "Agile" Methods 
- structured development has disadvantages
	- produce lots of documentation which can be largely unread
	- documentation has to be kept up-to-date
	- division into specialist groups and need to follow procedure
	- users can be excluded from decision process
- Answer is agile methodologies

# Atern/Dynamic System Development Method (DSDM)
- UK-based consotium
- DSDM can be seen as a replacement for SSADM (arguably)
- updated version of DSDM is called "Altern"

## 6 Core Principles of DSDM 
1. focus on business need
2. delivery on time 
3. collaboration
4. never compromise quality
5. deliver iteratively by using prototype
6. build incrementally
![[Pasted image 20240224132750.png]]
### Altern: Time Boxing
- fixed deadline by which something has to be delivered
- typically two to six weeks
- MoSCoW priorities
	- must have - essential
	- should have - very important, but system could operate without
	- could have
	- want - but probably won't get


# Extreme Programming
- increments of one to three weeks
	- customer can suggest improvement at any point
- argued that distinction between design and building of software artificial (face to face communication)
- code to be developed to meet current needs only
- frequent re-factoring to keep code structured

- developers work in pairs
- test cases and expected results are created **before** software design
- after testing of increment, test cases added to consolidated set of test cases

## Limitations of Extreme Programming
- need really good developers
- need personal knowledge about the software - after development, knowledge of software may decay making future developments harder
- rationale for decisions may be lost: example - which test cases checks a particular requirement
- reuse of existing code less likely

# Micro and Macro Processes 
- micro process is something within a macro process
- macro process: 
	- includes iterating through a micro process over and over again until a goal is reached
	- sends that to a "stop/checkpoint", which will then send that result to the next macro process
	- ![[Pasted image 20240224133415.png]]

# Combination of Approaches 
|  | one-shot | incremental | evolutionary |
| ---- | ---- | ---- | ---- |
| one-shot | yes  | yes | no |
| incremental | incremental | yes | no |
| evolutionary | yes  | yes | yes |
- horizontal is installation
- vertical is construction

- one-shot or incremental installation : any construction approach is possible
- evolutionary installation implies evolutionary construction
- I DON'T GET THIS, REVISIT LATER

# General rules of thumb about approach that is to be used
- if uncertainty is HIGH
	- use evolutionary approach

- if complexity higher but uncertainty not
	- use incremental approach

- if uncertainty and complexity both low
	- use one-shot

- if schedule is tight
	- use evolutionary or incremental

# as a summary
- evolutionary: prototyping 
	- refinement of previous prototypes
- incremental: one thing after another
	- one increment must solve one problem and show something to the user
	- once one thing is done, the next can start
	- hence, one after another
- one-shot: done in one single iteration (like waterfall)