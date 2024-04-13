# responsibilities 
- details about the progress of the project have to come from the people that are doing the work
	- and then that information has to be fed up through the management structure
- information overload
	- each management level will have some level of summarization and commentary before passing information up to the higher levels
	- meaning there could be "information overload" when passing information up

# assessing progress
- checkpoints: times when progress is checked
	- event-driven: check happens when a particular event has been achieved
	- time-driven: check happens when a date is reached
- frequency of reporting 
	- higher management levels -> longer gaps between checkpoints
# categories of reporting
- oral formal regular
- oral formal ad hoc
	- end-of-stage reviews. mostly oral there will most likely be written reports
- written formal regular
	- job sheets, progress reports
- written formal ad hoc
	- exception reports, change reports
- oral informal ad hoc
	- just social interaction
	- often provides early warning, must be backed up by formal reporting

# collecting progress details
- need
	- achievements
	- costs
- problem: how to deal with partial completions
- possible solutions:
	- control of products, not activities
	- subdivide into lots of sub-activities

# red/green/amber reporting 
- identify key tasks
- break down into sub-tasks
- assess subtasks as: 
	- green - on target
	- amber - not on target but recoverable
	- red - not on target and recoverable but very difficult to recover
- status of "critical tasks" are important
	- critical tasks are those that are on the critical path and/or reliant on critical resources

# slip charts
- activities that are shaded in are complete and the ones that are not, are not (right side is not complete)
- ![[Pasted image 20240412131240.png]]
- the more jagged the lines, the more it means that there are some activities that are lagging behind in terms of completion
- very jagged line means that you can go back and re-plan and more resources from those activities that are ahead to those that are behind
	- assign someone else to work on lagging projects

# cost monitoring 
- project could be late because staff as not deployed
- in this case, the project will be behind time, but also underbudget
- a project  could be on time only because addition resources were added, therefore overbudget
- need to monitor achievements and costs

# earned value analysis 
- planned value (PV): authorized budget to work with 
- earned value (EV): value of work performed expressed in terms of budget authorized for that work
- actual cost (AC): cost incurred for the work performed on an activity during a specific time period

# accounting conventions 
- earned values for works started but not done are assigned by:
	- 50/50: half allocated at start, other half on completion. doesn't necessarily have to be 50/50
	- milestone: current value depends on milestones achieved
	- units processed
- can use money values, or staff effort

# earned value, an example:
 - tasks: 
	 - specify module | 5 days
	 - code module | 8 days
	 - test module | 6 days
 - at beginning of day 20, PV = 19 days
 - if everything but testing completed, EV = 13 days
 - schedule variance = EV-PV = 13-19 = -6
 - schedule performance indicator (SPI) = EV/PV = 13/19 = 0.68
 - SV<0 or SPI<1.00 -> project behind the schedule

# earned value, actual cost 
- actual cost (AC) = actual cost of work performed
- in previous example, if
	- "specify module" actually took 3 days
	- "code module" actually took 4 days
- actual cost = 7 days
- cost variance (CV) = EV-AC = 13-7 = 6 days
- cost performance indicator (CPI) = EV/AC = 13/7 = 1.86
- CV>0 or CPI>1 -> project within budget

# earned value analysis - actual costs
- cost performance indicator can be used to produce a new cost estimate
- budget at completion (BAC) (or current budget allocated to total costs of project)
- estimate at completion (or updated estimate = BAC/CPI)
	- lets say that BAC = 19k and CPI is 1.86
	- this means that the work is being completed faster than normal
	- which means that EAC would be a bit lower than 19k, indicating that work is being done faster and in less time

# time variance 
- difference between time when specified EV should have been reached and time it actually was
- example: 
	- assume EV = 19k, should have been reached by the 1st of April
	- instead, it was reached on 1st of July. Then TV = -3 months, as it was completed 3 months late


# prioritization monitoring 
- might want to focus more on critical path activities
	- by definition, if these are late, the project as a whole will be delayed
- activities with no free float - if delayed later, dependent activities are delayed
- activities with less than a specified float
	- projects when being executed can be very dynamic, where some will take longer than estimated and others will take less. could lead to critical shifting
	- activities with small floats are the most likely to find themselves turned into activities on the critical path if their floats get eroded
- high risk activities: standard deviation is large for this activity. meaning there is a lot of uncertainty of how long it will take to finish this project
- activities using critical resources
	- some resources may only be available for limited period of time

# getting back on track 
- renegotiate the deadline
	- divide deliverables into "tranches", and deliver those that are most valuable to the client on or before the deadline, but delaying less valuable ones
- if that is not possible, you can try and shorten the critical path
	- get things done quicker by adding more staff
- reconsider activity dependencies
	- allow activities to overlap, which increases quality shortfalls
	- overlap so that start of one activity does not wait for completion of the second one
	- split activities

# exception planning 
- changes could accept 
	- users
	- business case (costs increasing, therefore less profit)
- changes could be to 
	- delivery date
	- scope
	- cost
- exception report is needed

- first stage
	- write exception report for sponsors (through project board)
		- explaining problems
		- setting out options for resolution
- second stage
	- sponsor selects option (or identifies other option)
	- project manager produced exception plan implementing selected option
	- exception plan reviewed by sponsors

# Example:

find planned value PV at the end of Tuesday
![[Pasted image 20240412135607.png]]
- the planned value is the value that is planned (what is on this image) for the completed/partially completed tasks
	- in this case, A will be 100% complete, B will be 100% complete, C will be 50% complete
	- so $PV=(1.0*\$50)+(1.0*\$100)+(0.5*\$200) = 250$
	- this value is assuming that these are all completed in terms of the allocated resources

what is the earned value EV at the end of Tuesday given the actual percentages completed (at the end of Tuesday)
![[Pasted image 20240412135929.png]]
- $EV=(1.0*50)+(0.8*100)+(0.2*200)=170$

what is the actual cost AC at the end of Tuesday given the amount of money that had to be spent to complete that percentage at the end of Tuesday
![[Pasted image 20240412140124.png]]

- $AC=60+110+30=200$
- 200 dollars have been spent out of the 250 that were "budgeted" for the end of Tuesday
![[Pasted image 20240412140241.png]]