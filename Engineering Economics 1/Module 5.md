# Equivalence and Repeated Cash Flows


# Uniform Series Compound Interest Formulas
- uniform series (A) is defined as:
	- an end-of-period cash receipt or disbursement in a uniform series, continuing for n-periods
	- the entire series equivalent to $P$ or $F$ at an interest rate $i$
- YOU ONLY USE UNIFORM SERIES IF YOU ARE PUTTING IN/GETTING MONEY EVERY COMPOUNDING PERIOD
	- if you are saving for something, you put in some money every month, you use uniform series
	- if you put money into an account every year, and that gets compounded, you use uniform series
	- basically think of repeated payments/money

# Uniform Series Compound Amount Factor
- Used when you have the value that you are putting in consistently, want to find the amount of money you will have later on (with some interest rate)
- formula is: $F=A\left[ \frac{(1+i)^n-1}{i} \right]$
- Where F is the final amount, and A is the amount that you are putting in per period

## Example using Compound Amount Factor
- You deposit $500 at the end of each year for 5 years. The credit union pays 5% interest compounded annually. How much do you have in your account immediately after that fifth deposit?
- A = 500, want F, $i$ = 0.05, n = 5
- using the first equation: you get 500(5.526) = $2763 after the fifth payment

# Uniform Series Sinking Fund Factor
- Used when you want to find how much money you have to put in some period to get a final value in a given time with a given interest rate 
- $A=F\left[ \frac{i}{(1+i)^n-1} \right]$
- A is the amount of money per period
- F is the final amount of money that you'll have
- $i$ is the interest
- $n$ is the number of periods you will pay for

## Example using Sinking Fund Factor
- Jim wants to buy some equipment for $100. Decides to save a uniform amount at the end of each month, so that he would have $1000 at the end of one year. The local credit union pays 6% interest, compounded annually. How much would Jim have to deposit each month?
- n = 12
- The interest given is for a year, so you have to divide by 12:
	- 6%/12 = 0.5% monthly
- F = 1000
- A = ?
- using the equation (where $i=0.005$):
	- $F=(1000)(0.0811) = \$81.10\text{ monthly payments}$

# Uniform Series Capital Recovery Factor
- used when you want to find out how much money you should put in every period to make the initial investment money back.
- $A=P\left[ \frac{i(1+i)^n}{(1+i)^n-1} \right]$
- where P is the initial investment
- A is how much you are putting in

## Example using Capital Recovery Factor
- A machine costs $5000 and has a life of five years. If the interest rate is 8%, how much will it have to save the buyer every year to recover the initial capital?
- $P=\$5000,n=5,i=8\%,A=unknown$
- This gives: $5000(0.2505)=1252$
	- this means that you would have to make 1252 yearly to make up the price of the item itself

# Uniform Series Present Worth Factor 
- used when you are given a value to pay per period, and you want to figure out how much of an investment you must make to get that value (given A, want P)
- $P=A\left[ \frac{(1+i)^n-1}{i(1+i)^n} \right]$
	- where P is the initial value
	- and A is the monthly payments that you are giving 

## Example using Present Worth Factor
- Investor holds a time-payment purchase contract on some machine. Contract calls for $140 at the end of every month for 5 years. The first payment is due in one month. Offers to sell contract at $6800 cash today. If you can otherwise make 1% per month on your money, would you accept the offer?
- want want to figure out how much we will make if we get 1% of our money, and how much of an initial investment we can afford using that information
	- so $A=140, i=0.01,n=60,P=unknown$
- equation: $140(44.955)=6293.70$
	- if we are to spend 140 every month, can assume that we will pay off about 6.2k of that money per month. 6800 > 6.2k which means that we would not break even if we took this contract. therefore, reject
# Uniform Series Formula Problem 1
- Joe wants to be able to purchase his dream car for about 19k on Jan 1 2004. Joe has a part time job and started making deposits of 275 each month into an account that pays 9% compounded monthly beginning with the first deposit on 1 Feb 1999. The last deposit is to be made on 1 January 2004. Determine how much money he would have saved to buy the car. Will he be able to buy the car? 
	- Monthly payment of A = 275
	- $i = \frac{0.09}{12}=0.0075$ (assuming that the question says compounded yearly because 9% monthly is insane)
	- F = unknown
	- n = 60 months
- You have the deposits per month, you want to find out how much money he has now. this means you use the first equation (compound amount factor)
	- $275(69.770)=20741.6$
	- yes he would have saved enough money in that time to buy the car

# Uniform Series Formula Problem 2 
- You are repaying debt of 10k with equal payments made at the end of four equal periods. If the interest rate is 10% per period, how much of the original 10k principle will be paid in the second payment?
- you already paid 10k so P = 10000
- want to find out how much you will pay per period (which can be done with A)
- want A 
- i = 0.1
- n = 4
- use the equation that solves for A with P (last one) gives 3154.71

- for the amount that is due, in the first period that would be $10,000*1.1 = 11000$
	- since you pay 3154.71 in every period, you would have paid $11000 - 3154.71=7845$
- in the second period, the 10% will accrue on the outstanding amount that you currently have (7845): $7845*1.1=8629.50$
	- since you pay 3154.71 in every period, would have have paid $8629.50-3154.71=5475.79$
	- you have $5475.79 left to pay still. 
HELP
***********************************************

# Relationships Between Compound Interest Factors 
- Single Payment 
	- compound amount factor = 1/present worth factor
	- $(F/P, i, n)=1/(P/F,i,n)$
- Uniform Series



# Uniform Series that use P/A and A/P
- The uniform series that use these two variables are one of the two:
	1. Cash flow occurs in consecutive interest periods
	2. Cash flow amount is the same in each interest period

![[Pasted image 20240312111751.png]]
- left side: you paid some unknown value once and you are now making money uniformly to get that money back. can use this to find out if you afford to pay that first value (P is the initial investment)
- right side: you a given value once (invested, so P), and now you figure out how much money you need to make every period to pay that money off (A is not given)


# Uniform Series that use F/A and A/F
- The uniform series factors that involve F and A are derived as follows:
	1. Cash flow occurs in consecutive interest periods
	2. Last cash flow occurs in same period as F
![[Pasted image 20240312112007.png]]
left side: putting in some value of money every month and then seeing how much money you will have at the end of it
right side: seeing how much money you have to put in every month to get a final value that is given (F is final, A is the amount of money you put in every period)

# Arithmetic Gradient
- a uniformly increasing series of two components 
	- series component (A)
	- gradient component (G)
![[Pasted image 20240312112323.png]]
- Therefore:
	- $P=A(P/A, i\%, n)+G(P/G, i\%,n)$

## Example using Arithmetic Gradient:
- on a piece of equipment, the maintenance costs look something like this:
- ![[Pasted image 20240312112911.png]]
- what is the equivalent uniform annual maintenance cost for the machine if 6% interest is used?
- Answer:
	- ![[Pasted image 20240312112940.png]]
	- since the 100 is constant, we can use this equation:
	- $100+100\left( \frac{1}{0.06} -\frac{4}{(1+0.06)^4-1}\right)=242.72$
	- the stuff inside the bracket is known as the *arithmetic gradient uniform series factor*
		- which just means it is how much is changing in very period (by the factor of the gradient)
	- the first 100 is for the constant
	- the 100 multiplies the gradient (which is increasing by 100 every time)

- you can have other gradients as well
	- A would be the uniform cost
	- G would be the annual gradient
	- g would be the uniform annual rate of increase
	- depending on the question, you would use one of two equations:
		- if $i\neq g$
			- ![[Pasted image 20240312114053.png]]
			- where $A_{1}$ is the first monthly payment without any g or G
		- if $i=g$
			- ![[Pasted image 20240312114123.png]]
			- where $A_{1}$ is the first monthly payment without any g or G
	- ![[Pasted image 20240312114143.png]]
	- $g$ in this case is 10% and the interest rate is 8%
		- so you use the $g\neq i$ equation
# When the Compounding Period and Payment Period Differ
- adjustment is required when this happens
- done by:
	1. Computing the equivalent payment amounts for each compounding period and applying the interest rate
	2. computing an effective interest rate for payment periods

![[Pasted image 20240312114442.png]]
if you ever see "nominal interest", that means you use one of these equations. instead of $i$ use $r$
![[Pasted image 20240312114604.png]]
- $r=0.05 \text{ because we want to check if the nominal interest was 5\%}$
- $A=500 \text{ still because the value of the monthly payments do not change}$
- 