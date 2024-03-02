# Scheduling
- 'time is nature's way of stopping everything happening at once'
- having:
	- worked out a method of doing a project
	- identified the tasks to be carried
	- assessed the time needed to do each task
- need to allocate dates/times for the start and end of each activity

# Activity Networks 
- help:
	- assess feasibility of the estimated completion date of the project
	- identify when resources will be deployed to activities
	- calculate when costs will come in
- also helps coordination between the team 

# Defining Activities 
- activity networks based on some assumptions:
	- project is: 
		- comprised of multiple activities
		- may start when at least one of its activities is ready to start
		- completed when all activities are completed
## An activity:
- must have clear start/end points
- must have resource requirements
	- assumed to be constant throughout the project
- must have a duration
- may be dependent on other activities completed first (precedence networks)


# Identifying Activities 
1. Work-based: draw-up a Work Breakdown Structure listing the work items needed
2. Product-based approach
	1. list deliverable and intermediate products of project
	2. identify the order in which products have to be created
	3. work out the activities needed to create products

# Hybrid Approach 
3. the IBM MITP approach suggests the following 5 levels:
	1. project
	2. deliverables
	3. components: which are key work items needed to produce the deliverables
	4. work packages: groups of tasks needed to produce components
	5. tasks


- final outcome of these activities is a project plan
	- in the form of a bar chart
	- we have done two things with the bar chart:
		- sequencing: by considering dependencies between tasks
		- scheduling: by considering the availability of developers and staff
	- however, right now they are combined, and we would like to separate them
		- done by introducing network planning models

# Network Planning Models
- show project activities and relationships
- in the network, time flows from left to right
- Critical Path Method (CPM)
- Program Evaluation Review Technique (PERT)
- In industry, almost all network planning models are called CPM (critical path method)

## PERT
- created to support development of Polaris
- activity-on-node notation - 'nodes' are boxes which represent activities
- original PERT is activity-on-arrow (like CPM)

## CPM
- uses activity-on-arrow notation where arrows are the activities

![[Pasted image 20240226115849.png]]

# Drawing a PERT diagram 
- no loping back
	- deal with iterations by hiding them in a single activity
- milestones - "activities" such as start and end of projects, indicate transition points. have 0 duration

## Lagged Activities
- when there is a fixed delay between activities, example: seven days notice has too be given to users that a new release has been signed off and is to be installed
![[Pasted image 20240226120028.png]]

## Types of Links between Activities
- finish to start
	- the following activity starts when the previous one has been finished
		- testing starts only once code has been completed

- start to start/finish to finish
	- start to start: when one activity starts another has to start as well
		- when prototyping starts, amendment documentation has to start as well
- finish to finish
	- when one activity finishes, the other must finish too
		- example: when testing of the prototype is completed, so is the documentation of any amendments
	- you could use these with lags, example; 
		- documentation of the changes to the prototype starts 1 day after the testing and finishes 2 days after testing has been completed
- ![[Pasted image 20240226120426.png]]

# Adding time to the Network Model (start and finish times)
- activity: 'write report software'
- earliest start (ES)
- earliest finish (EF) = ES + duration
- latest finish (LF) = latest task can be finished without affecting project end
- latest start (LS) = LF - duration

## Example: 
- earliest start = day 5
- latest finish = day 30
- duration = 10 days

- earliest finish = ??
- latest start = ??
	- float = LF - ES - duration

- earliest finish would be day 5 + 10 day duration = day 15
- latest start would be day 30 - 10 day duration = day 20
- the float would be 30-5-10 = 15 days
- could also 