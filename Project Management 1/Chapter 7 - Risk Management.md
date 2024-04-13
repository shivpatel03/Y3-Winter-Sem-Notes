
# definitions of risk 
- "an uncertain event or condition that has positive or negative effect on a projects' objective."
	- possible future problems, not current ones
	- possible cause and its effect, example: developer leaves -> task is delayed
- risk identification is part of the Step-Wise project planning process


# categories for risk
- actors
	- involves those that are involved in the project
	- risk could be high staff turnover leads to important information of the project being lost
- technology
	- risk could be that the selected technologies are not appropriate for the project
- structure
	- management procedures
	- example: some people on the team do not know the process of carrying out this project because they are not part of the communication network
- tasks
	- work to be carried out
	- typical risk is that the amount of effort needed to carry out the task is underestimated

# dealing with risk 
planning for risk:
1. risk identification - what risks might be there?
2. risk analysis and prioritization - which risks are more serious?
3. risk planning - what are we going to do about them?
4. risk monitoring - what is the current state of the risk?

## risk identification 
- use of checklists 
- brainstorming - getting knowledgeable stakeholders together to pool concerns
- causal mapping - identifying possible chains of cause and effect
- here are some common risks identified by project managers as well as some mitigation techniques:
	- personnel shortfalls: staffing with top talent; job matching; team building; training and career development; early scheduling of key personnel, etc.
	- unrealistic time and cost estimates: design to cost; incremental development; recording and analysis of previous projects; standardization of projects
	- there are more.
## risk analysis and prioritization 
- Risk Exposure = (potential damage) x (probability of occurrence)
	- potential damage = money value if the risk actually happened
	- probability = 0 - 1 chance of it happening
- Risk probability: qualitative descriptors:
	- for probability
		- managers would be happier identifying an approximate range instead of a precise probability
		- high = more than 50%
		- significant = 30-50%
		- moderate = 10-29%
		- low = less than 10%
	- for cost:
		- high = greater than 30% above budgeted expenditure
		- significant = 20-20% above
		- moderate = 10-19% above
		- low = lower than 10%

## risk planning
- can be dealt with
	- risk acceptance
		- cost of avoiding might be higher than actual damage cost
		- allow a risk that is not too expensive
	- risk avoidance
		- avoid environment where the risk occurs
		- example: buying an off-the-shelf product, would avoid a lot of the risks that we would have if we started from scratch
	- reduction
		- risk accepted, actions are taken to reduce its likelihood
		- example: prototypes to reduce the risk of incorrect requirements
	- transfer
		- risk transferred to another person in the company
	- mitigation
		- reduce the impact of the risk if it does occur
		- taking backups to allow rapid recovery if something goes down


# risk reduction leverage 
- insurance company might reduce the fire insurance premium from 2k to 1k on condition that fire alarm is installed. insured customer would save 1k per year by investing 500 so it would be worth doing
- not every risk reduction is cost effective
	- this is why we accept the risk
- check RE (the equation above) before and after the risk reduction

$\text{Risk Reduction Leverage=}RE_{before}-RE_{after}/\text{cost of risk reduction}$
- if RRL is greater than 1, it is worth the cost of the risk reduction


# evaluating risk to schedule 
- when we can't get a money value associated with the risk, we use effort as a replacement for financial loss
- use PERT to evaluate the effects of uncertainty

- PERT used to find out how much time it will take to finish a project

- PERT uses three estimates 
	- a - optimistic time
	- m - most likely time
	- b - pessimistic time
	- expected time = $t_{e}=(a+4m+b)/6$
	- activity standard deviation = $S = (b-a)/6$
## likelihood of meeting targets 
- calculate the standard deviation for each project event
- calculate the z-values for each event that has a target date
- Z is the number of standard deviation between task expected time and target time
- convert Z values to probabilities

![[Pasted image 20240412111434.png]]
- the standard deviation of A+B+C would be $\sqrt{ (1^2+1^2+3^2) }=3.32$
- and the expected time for the three tasks overall would be $12.66+10.33+25.66=48.65$
- assume that the target completing time for the tasks is 52 days
- $z=(T-t_{e})/s$
	- $z=(52-48.65)/3.32=1.01$
	- 