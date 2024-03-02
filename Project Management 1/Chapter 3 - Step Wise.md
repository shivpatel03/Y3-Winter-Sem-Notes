- An approach to planning software projects

# Aspirations for Step-Wise 
- Practicality 
	- tries to answer the question of what to do next
- Scalability
	- useful for small and larger projects
- Range of application
- Accepted techniques:
	- borrowed from PRINCE etc.
	- Project in Controlled Environment (PRINCE)

- the idea of Step Wise is that it gives a sequence of activities to work on when working on a project
- some of them are done together, while others are done one after another

![[Pasted image 20240223091357.png]]

# Project Scenario: Bright-mouth College Payroll 
- Brightmouth College currently has payroll processing that is done by a service company
- is expensive, and does not allow for analysis of personnel data to be carried out
- decision is made to start doing payroll "in-house" by getting an "off-the-shelf" application
- the use of this off the shelf system will require a new (internal) payroll office to be setup
- need to develop software "add-ons": one will take payroll data and combine it with the time-table data to calculate the staff costs for each course offered in the college
- project manger for this is Brigette


## Step 1: Establish a Project Scope and Objectives
- 1.1 Identify objectives and measures of effectiveness
	- answer the question of "how do we know that we have succeeded"
- 1.2 Establish a project authority
	- answer the question of "who is the boss"
- 1.3 Identify all stakeholders in the project and their interests
	- answer the question of "who will affected/involved in this project"
- 1.4 Modify objectives in light of stakeholder analysis
	- answer the question "do we need to do things to win over stakeholders? Why?"
- 1.5 Establish methods of communications with all parties
	- answer the question of "how do we keep in contact?"

## Back to the Scenario 
- Project authority
	- Brigette considers that she has two clients: finance department, and personnel office (HR)
	- a vice principles agrees to be an official client, and monthly meetings are chaired by the VP and attended by Brigette and the heads of both departments mentioned above
	- meetings would help overcome communication barriers as well
- Stakeholders
	- personnel office (HR) would supply details of new staff, leavers, and changes
	- to motivate cooperation, Brigette might make sure that the new payroll system produces reports that are useful to the personnel staff.

## Step 2: Establish Project Infrastructure 
- 2.1 Establish a link between project and strategic plan (such as enterprise architecture)
	- answer the question of "why did they want the project"
- 2.2 Identify installation standards and procedures
	- answer the question of "what standards did we have to follow"
- 2.3 Identify project team organization
	- answer "where do I fit in?"

## Step 3: Analysis of Project Characteristics
- 3.1 decide whether the project is objective or produced-based
	- are there more than one ways to achieve success?
- 3.2 analyze other project characteristics
	- is it information system, process control, an embedded system, etc.
	- what is different about this project?
- Identify high level project risks
	- Risks: operational, development, nature of project
	- "what could go wrong?"
	- "what can we do to stop it?"
- Consider user requirements that will effect implementation
	- Organization may have to mandate particular methodology or development process
- Select general life cycle approach (covered in Chapter 4)
	- waterfall? increments? prototypes?
- Review overall resource estimates
	- "does all this increase the cost?"

## Back to the scenario
- Objective vs. products
	- objective-based approach is adopted 
- Some risks
	- there may not be an off-the-shelf product that caters to the way that this college has done payroll until now
- Answer? 
	- Brigette decides to get further details on how the off-the-shelf packages in consideration work as soon as possible. also agreement is made that necessary processes will be changed to fit in with the new system

## Step 4: Identify Project Products and Activities
- 4.1 identify and describe products - 'what do we have to produce?'
	- there is no product without activities
![[Pasted image 20240223093053.png]]
- this is a Product Breakdown Structure (PBS)

# Product
- What is a product?
	- the result of an activity
	- could be (among other things)
		- physical thing ('installed PC')
		- a document ('logical data structure')
		- a person ('trained user')
		- a new version of an old product ('updated software')
- The following are not normally products
	- activities (example; "training")
	- events (example: "interviews completed")
	- resources and actors (example: "Software developer") - this may have exceptions
- Products can be deliverables or intermediates

# Product Description 
- Product identity/name 
- Description: what is it? 
- Derivation: what is it based on? 
	- the predecessor product that are needed from which this particular product is derived
- Composition: what does it contain? 
- Format (form of the product)
	- example: a4 or letter if the product is a document, or hard cover or paper-back if it is a book
- Relevant standards
- Quality criteria 

## PD for a Bicycle 
- Descripion
	- lightweight vehicle mounted on two wire-spoked wheels one behind the other. having a seat, handlebars for steering, brakes, and two pedals or a small rotor by which it is driven
- Format:
	- street/mountain bike
- Composition: what does it contain?
	- lists out all the parts that are present in a bike

## Step 4 of of Case Study (continued)
- 4.2 document generic product flows
![[Pasted image 20240223093853.png]]
	- this is a product flow diagram (PFD)
	- Does it mean that we don't have any loops in product development?

- 4.3: recognize product instances
	- The PBS ad PFD will probably have identified genetic products (such as software modules)
	- might be possible to identify specific instances, example: "module A", "module B"
	- but in many cases, this will have to be left for later, more detailed planning
- 4.4 Product ideal activity network
	- choose activities needed to create product in PFD
	- multiple activities might be needed to create a product
	- hint: identify activities by verb + noun but avoid "product ... -" because it is to vague

### An Ideal Activity 
- if you need an activity, you can go one of two ways
	- analyze an existing system
		- leads to obtain user requirements
			- use these requirements to create test cases, plan office layout, and calculate volumes
			- once office layout is planned and calculating volumes is done, we can draft a letter to tender
				- and then issue that invitation
			- if we go straight to test cases, that is our final activity being complete
	- survey potential suppliers
		- leads issuing invitation to the tender
![[Pasted image 20240223094619.png]]
- the reason that this is considered "ideal" is because we are assuming no resource limitations during any of these steps

- 4.5 Add check points if needed ![[Pasted image 20240223094737.png]]
	- this image for example, in order to design the system, you break it into three concurrent smaller processes
		- however, this is not the best solution because although it is more efficient, it may not be as high quality as everyone is just working on their own
		- instead, having checkpoints are more beneficial ![[Pasted image 20240223094925.png]]

## Step 5: Estimate Effort for each Activity 
- 5.1 Carry out bottom-up estimates
	- differentiate between effort and elapsed time
		- example: a task requires three developers in two days. Determine the effort and elapsed time for this activity:
			- $\text{Effort = } 3*2 = 6\text{ days}$
			- $\text{Elapsed Time = 2 days}$
- 5.2 Revise plan to create controllable activities
	- break up long activities into smaller ones
	- bundle up the very short activities (create a check list?)

## Step 6: Identify Activity Risks 
- What is risk?
	- we live, work, and do projects based on some assumptions (could be our culture, context, environment, beliefs, knowledge, ignorance, information, emotions, etc.)
	- possibility that an assumption is wrong is a risk
		- especially if the plan is based on the assumption
	- main reason for risk is uncertainty
	- the usual effect of a risk is that it makes the task longer and more costly 

- 6.1 Identify and quantify the risks for activities 
	- what is the damage if the risk happens?
		- measure in time lost or money
	- what is the probability of it happening? 
- 6.2 Plan risk reduction and contingency measures 
	- risk reduction: activity to stop the risk from occurring
	- contingency: action if risk happens 
- 6.3 Change plans and estimates so if a risk happens they will be accounted for
	- example: add new activities that reduce the risks associated with other activities:
		- example: training, pilot trials, information gathering, etc.

## Step 7: Allocate Resources
- 7.1 identify and allocate resources to activities
- 7.2 changes plans and estimates to take into account resource contraints
	- example: staff may not be available until a later date due to something else
	- or any non-project activities

### Gantt Charts 
- used for showing activities (tasks or events) displayed against time
- this one also includes the people that should be involved in each activity![[Pasted image 20240223095917.png]]


## Step 8: Review/Publicize plan
- 8.1 Review quality aspects of the project plan 
- 8.2 Document plan and obtain agreement

## Step 9 and 10: Execute plans and create lower level plans 


# Key Points
- establish your objectives
- think about all characteristics within the project
- discover/set infrastructure to support the project (including standards)
- identify products to be created and the activities that will create them
- allocate resources
- set up quality processes
