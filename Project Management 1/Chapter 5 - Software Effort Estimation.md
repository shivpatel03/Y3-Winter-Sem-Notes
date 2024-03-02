# Step-Wise
- step 6 is "estimate effort for activity"
	- this is done for each activity
	- we have to do this effectively


# What makes a successful project? 
 - Delivering
 - agreed functionality
 - on time
 - created with the agreed upon cost
 - with the required quality
 - stages:
	 - set targets
	 - attempt to achieve those targets
 - but what if the targets are not achievable?

# Cost Estimation Model 
- used to calculate effort and schedule of a project
- these models give an easy way to reduce project risks and prepare the plan for building the project
- calculated using cost drivers
- cost drivers are critical features that have a direct impact on the project

# Problems with Estimating
- subjective nature of estimating
	- may be difficult to give evidence behind your target
- political pressures
	- managers may want to reduce estimated cost to get more support/acceptance on the project
- changing technologies 
	- bring uncertainties, especially in the earlier days of development when there is a "learning curve" for the developers 
- projects differ
	- experience on one project may not be useful in another

# Source Line of Code Technique 
- SLOC technique - objective method of estimating or calculating size of the project
- project size helps determine resources, cost, effort, duration required to complete project
- also used to directly calculate the effort needed for a project
- can use it when the programing language and technology to be used are predefined
- technique includes calculations of lines of codes (LOC), documentation of pages, inputs, outputs, components in a software program


# Exercise 5-1
- calculate the productivity, SLOC per work month, of each of the projects in the following table, and also for the organization as a whole
- if the project leads for project "a" and "d" had estimated the source number of lines of code (SLOC) and then used the average productivity of the organization to calculate the effort needed to complete the project, how far off would their estimate have been from their actual effort?
- table of effort per work month: ![[Pasted image 20240225190525.png]]
- table of productivity rates ![[Pasted image 20240225190537.png]]
	- in this image, we are getting the "productivity" of each project by dividing the total amount of effort needed by the number of months it will take to complete the task
	- to get the overall productivity of the entire company, the average of each productivity is taken
- because of this, we can now decide the estimated amount of work that will be done based on this productivity that we created:

| project | estimated work-month | actual | difference |
| ------- | -------------------- | ------ | ---------- |
| a       | 6050/617             | 16.7   | 6.9        |
estimated work-month is effort needed for that project (aka SLOC)/average productivity of company


# Over and Under-estimating
- Parkinson's Law: "Work expands to fill the time available"
- Brook's Law: "putting more people on a late job makes it later"
	- because you have to teach them stuff and get them up-to-date with the project 
- An over-estimate likely to cause project to take longer than it would otherwise
- Weinberg's Zeroth Law of reliability: 'a software project that does not have to meet a reliability requirement can meet any other requirement'
	- under-estimated projects may not make it in time or budget but they are done in a short amount of time
	- this leads to bad quality

## Example of bad estimate:
- a project that was estimated to be done in 9 months, ACTUALLY finished after 3 years
	- to make matters worse, every single time they extended, they only extended by 1 month which happened often
	- so every month, there was some type of extension that happened
	- this is a bad estimate, and this project is used as an example of a bad estimate from now on
- another project was done, and they quoted 3 years to finish, and instead they finished 2 months early.
	- since they held their promise and in fact, finished earlier than it, they were seen in good light
# Over and Under Estimating
- motivation and morale and enhanced when targets are achievable
	- chasing something that is unachievable is not good for developers mentally 
- several unsuccessful attempt and unattainable targets reduce motivation
- when people succeed, they claim it
	- but when failed, they blame it on the organization

# Basis for Successful Estimating
- information about past projects
	- get information from last projects to get an idea of how long it might take 
	- check the following of that old project though: how big was it? and how much time/effort did they need? 
- need to be able to measure the amount of work that is involved
	- traditional size of measurement is "lines of code" but this can have problems

# Taxonomy of Estimating Models
- bottom-up - activity based, analytical
- parametric or algorithmic models, example: function points
- expert opinion - just guessing?
- analogy - case-based, comparative
- Parkinson and 'price to win'


# Bottom-up vs. Top-down
- bottom-up:
	- identify all tasks that have to be done
		- time consuming
	- use when you have no data of previous projects
	- first top-down (in task level), so work breakdown schedule, and then bottom up
	- basically you start with no information so you do everything from scratch
- top-down:
	- produce overall estimate based on project cost drivers
	- based on past project data
	- divide overall estimate between jobs to be done
	- basically, you have information about previous projects that are similar so you can use that (use those to decide cost drivers)


## Bottom-up Estimating
1. break project into smaller and smaller components
2. stop when you get to components that can be done by a person in 1-2 weeks
3. estimate cost for lowest level activities
4. at each higher level, calculate estimate by adding estimates of lower levels
	1. if you have never done something before, you can imagine what you could do in about a week

## Top-down Estimating
- effort driver: critical feature of the project that have direct impact on project
- lets say you have a project that is estimated at 100 days
	- effort drivers could be:
		- Design (30%, so 30 days)
		- Code (30%, so 30 days)
		- Test (40%, so 40 days)


# Algorithmic/Parametric models
- Constructive Cost Model (COCOMO) (lines of code) and function points examples of these:
- in COCOMO, the model parameters are derived from fitting a regression formula using data from historical fprojects
	- ![[Pasted image 20240225192316.png]]

- problems with COCOMO 
	- input parameter of system size is based on lines of code. this is going to be the estimate at the starting of the project
- function points: count more features (not just lines of code) in a project to produce an **index number** which reflects the amount of information processing that will have to carry out. this can be somewhat equated to the amount of code that it will need

## Parametric Model - the need for previous data
- simplistic model for an estimate
	- estimated effort = (system size) / productivity
- example:
	- system size = lines of code (estimated)
	- productivity = lines of code per day (measured through previous projects)
- **productivity = (system size) / effort**
	- based on past projects
- this is analogous to calculating speed from distance and time

## Parametric Models 
- some model focus on task or system size: example: Function Points
- FPs originally used to estimate the lines of code, rather than effort
![[Pasted image 20240225192930.png]]
- uses some metric (in this case, the number of files and the number of input and output transaction types) that go into the model, outputs system size

- other models focus more on productivity, such as COCOMO
- lines of code (for FPs as an input)
![[Pasted image 20240225193044.png]]

# COCOMO
- originally based on size parameter of lines of code
	- actually "thousand of delivered source code instructions", or KDSI
- newer versions recognize use of functions as a size measure, but convert them into  a number called "equivalent lines of code" (ELOC)

# Getting the Initial Estimate Using COCOMO 
- known as the nominal estimate and nominal effort
- based on person-month:
	- $E_{i} = a * (\text{KLOC})^b$
	- where a and b are constants depending on the project type

## Project Types
- organic projects: organization has lots of experience in these types of projects, they are generally small and straightforward
- semi-detached projects: medium size, more complex (an operating system or complier project)
- embedded systems projects: stringent requirements, complex, organization has little to no experience in that area

## Example: 
Constants for the types of projects

| Project Type  | a value | b value |
| ------------- | ------- | ------- |
| Organic       | 3.2     | 1.05    |
| Semi-detached | 3.0     | 1.12    |
| Embedded      | 2.8     | 1.2     |
- Example 1:
	- if software product is *organic* and estimated to be 8000 LOC, initial effort is calculated as;
		- $E_{i} = 3.2*8^{1.05} = 28 \text{ person-months}$
- Example 2:
	- if software product is *embedded* and estimated 10000 LOC, nominal effort is:
		- $E_{i} = 2.8 * 10^{1.2} = 44 \text{ person-months}$

## COCOMO Duration Example:
- duration equation for COCOMO: $D = a * E^b$
- where E is estimated effort, and

| Project type  | a   | b    |
| ------------- | --- | ---- |
| organic       | 2.5 | 0.38 |
| semi-detached | 2.5 | 0.35 |
| embedded      | 2.5 | 0.32 |
- suppose that the overall size of an organic software is estimated at 20000
	- efforts: $E = 3.2*20^{1.05} = \text{75 person-months}$
	- duration: $D = 2.5 * 74^{0.38} \text{ = 13 months}$

# Expert Judgement 
- asking someone who is knowledgeable about the application area and technologies that are to be used
	- do this to get provide an estimate
- mostly appropriate when existing code is to be changed
- research shows that expert judgement in practice tends to be based on a strategy


# Stages: Identify:
- significant features of the project
- past projects with similar features 
- differences between current and past projects 
- possible reason for error (risks)
- measure to reduce uncertainty


# Machine assistance for source selection
$\text{Euclidean Distance = } \sqrt{ ((I_{t}-I_{s})^2 +(O_{t}-O_{s})^2)) }$
- where $I_{t} \text{ and } I_{s}$ are input of the target and input of the source respectively
- and $O_{t} \text{ and } O_{s}$ are output of target and and output of the source respectively
	- where the source is an old project and the target is the new one that we are trying to make

# in-class exercise 
- Say that the cases that are being matched on the basis of two parameters, the number of inputs to the number of outputs from the system to be built. The new project is known to need 7 inputs and 15 outputs. One of the past cases, Project A has 8 inputs and 17 outputs

1. What is the Euclidean distance between the source and Project A?
2. Project B has 5 inputs and 10 outputs. What would be Euclidean distance between this project and the new target project
3. Is project B a better analogy with the target than Project A?

## answer to 1
- use the equation
$\text{Euclidean Distance}=\sqrt{ (7-8)^2+(15-17)^2 }=2.24$

## answer to 2
- use the equation but with different numbers 
$\text{Euclidean Distance}=\sqrt{ (7-5)^2+(15-10)^2}=5.39$

## answer to 3
- a lower distance would mean less of a difference between the two projects, therefore B is not better than A in terms of being a comparison to the target project

# Function Points (FP)
- measures functionality of the application
- higher number = higher functionality
- allow for scaling 
- measure the size of requirements
- ![[Pasted image 20240225200000.png]]
- image explains how an application may work, user interacts with the application, triggering an external input
	- that external input could use some type of internal logical file (ILF)

# Parametric Model
- looking at 4 parametric models:
1. Albrecht/IFPUG function points
2. Symons/Mark II function points
3. COSMIC function points
4. COCOMO81 and COCOMO II

function points model system size, while COCOMO focuses on productivity factors


## Albrecht/IFPUG function points 
- worked at IBM and needed a way of measuring relative functionality of different programming languages
- need a way to measure size of application in a way that was not counting lines of code
- found five types of components or functionality in an information system
- counted how many times each type of functionality in order to get an indication of the size of the project

### The five function types: 
1. logical interface files (LIF) types - "data stored" in systems analysis terms. Created and accessed by the target system
2. external interface file types (EIF) - data retrieved from data store, actually maintained by different application. can think of DB
3. External input (EI) types - input transactions, which update internal computer files
4. external output (EO) types - transactions which extract and display data from internal computer files, involves creating reports
5. external inquiry types (EQ) - user initiated transactions which provide information but do not change local files. normally user inputs some data that guides the system to the information the user needs
complexity multipliers

| External User Types | Low Complexity | Medium Complexity | High Complexity |
| ------------------- | -------------- | ----------------- | --------------- |
| EI                  | 3              | 4                 | 6               |
| EO                  | 4              | 5                 | 7               |
| EQ                  | 3              | 4                 | 6               |
| LIF                 | 7              | 10                | 15              |
| EIF                 | 5              | 7                 | 10              |
Examples: 
- transactions to input, amend and delete employee details - EI that is rated at medium complexity
- transaction that calculates pay details from time sheet, which is the input - EI that is rated high complexity
- transaction of medium complexity that prints out pay-to-date details for each employee - EO 
- file of payroll details for each employee - medium complexity LIF
- personnel file maintained by another system, accessed for name and address details - simple EIF
what would be the FP counts?

- Medium EI = 4 FPs
- high complexity EI = 6 FPs
- medium complexity EO = 5 FPs
- medium complexity LIF = 10 FPs
- Simple IEF = 5 FPs
- Total = 30 FPs
	- if previous projects delivered 5 FPs/day, implementing above should take 30/5 = 6 days

# Development Factor Multipliers
- according to COCOMO, major productivity drivers are
	- product attributes: required reliability, database size, product complexity
	- computer attributes: execution time constraints, storage constraints, virtual machine volatility (VM)
	- personnel attributes: analyst capability, application experience, VM experience, programming language experience
	- project attributes: modern programming practices, software tools, schedule constraints

# COCOMO II
- updated version
- there are models for early design stage but also some for "post architecture stage" which is when the final system is implemented
	- we will focus on the early design stage
- core model is: $pm = A(size)^{sf} * (em_{1}) * (em_{2}) * (em_{3}) * \dots$
	- `pm` = person months
	- `A` = 2.94
	- `size` = number of thousands of lines of code
	- `sf` = scale factor
	- `em` = effort multiplier

## COCOMO II - Scale Factor
- based on five factors which appear to be particularly sensitive to system size
	- Precedentedness (PREC) - degree to which there are past examples that can be consulted
	- Development flexibility (FLEX) - degree to which flexibility that exists when implementing the project
	- Architecture/risk resolution (RESL) - degree of uncertainty about requirements
	- Team cohesion (TEAM)
	- Process maturity (PMAT) could be assessed by CMMI


## Scale Factor Values
![[Pasted image 20240225225539.png]]
the lower the scale factor, the better
- if you had a lower scale factor for TEAM (lets say 1.10), that means the team works well together 
- if you had a higher scale factor for PREC (lets say 4.96), that means that the team does not have very much prior information about the project at hand


## Example of Scale Factor
- in software development team is developing a project that is very similar to one that has been developed before (by them). PREC is very high (scale factor of 1.24)
	- "very high degree of similar projects in the past"
- a very precise engineering document lays down very strict requirements (FLEX is very low, factor of 5.07)
	- FLEX is the likely-hood of something changing, and in this case, there is not much
	- "very low likely-hood of something changing"
- tight requirements are unlikely to change (RESL high, factor of 2.83)
	- RESL - degree of uncertainty about requirements, they are not uncertain
- team is tightly knit (TEAM has a high score of 2.19)
	- "very high team cohesion"
- but processes are informal (PMAT is low, score of 6.24)
	- "very low process maturity"

## Scalar Factor Calculation
- Formula for `sf` is

$sf = B + 0.01 * \sum\text{scale factor values}$
$i.e. sf=0.91+0.01 * (1.24+5.07+2.83+2.19+6.24)$
$=1.0857$

if the system obtained 10kloc, then estimate would be $2.94*10^{1.0857}=35.8$
- which comes from $A(size)^{sf}$
	- a = 2.94
	- size = 10
	- sf = 1.0857


## Effort Multipliers
- there are scale factors, we also assess effort multipliers:
	- RCPX - product reliability and complexity
	- RUSE - reuse required
	- PDIF - platform difficulty
	- PERS - personnel capability
	- PREX - personal experience
	- FCIL - facilities available
	- SCED - schedule pressure
![[Pasted image 20240225235234.png]]
## Example:
- assume a new project is similar in most characteristics to those that an organization has been dealing with for a long time
	- except:
		- software that is going to be produced is more complex and will be used in a safety-critical system
		- software will interface with new operating system that is currently in beta
		- to deal with this, the team that has been given the job is really good, but do not have much experience in this type of software
- RCPX very high, 1.91
- PDIF very high 1.81
- PEFS extra high 0.5
- PREX nominal 
- all other factors are nominal
- say estimate is 35.8 person months
- with effort multipliers becomes $35.8*1.91*1.81*0.5=61.9$
	- the "person month" portion of this comes from the equation $A(size)^{sf}$
	- if you want to use the effort multipliers, they are added to them 


# Conclusions: how to review estimates? 
- ask the following questions about an estimate
	- what are the task size drivers? 
	- what productivity rates have been used? 
	- is there an example of a previous project of about the same size?
	- are there examples where productivity rates used to have actually been found?