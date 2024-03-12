# Equivalence and Repeated Cash Flows


# Uniform Series Compound Interest Formulas
- uniform series (A) is defined as:
	- an end-of-period cash receipt or disbursement in a uniform series, continuing for n-periods
	- the entire series equivalent to $P$ or $F$ at an interest rate $i$
- YOU ONLY USE UNIFORM SERIES IF YOU ARE PUTTING IN/GETTING MONEY EVERY COMPOUNDING PERIOD
	- if you are saving for something, you put in some money every month, you use uniform series
	- if you put money into an account every year, and that gets compounded, you use uniform series
	- basically think of repeated payments/money

- $F=A\left[ \frac{(1+i)^n-1}{i} \right]$
	- where
	- F = Final amount
	- A = initial amount
	- $i$ = interest rate
	- $n$ = number of compound cycles

## Example:
- you deposit $500 in a credit union at the end of each year for five years. Credit union pays 5% interest, compounded annually. How much do you have in your account after the 5th deposit?

- given :
	- $A = \$500, n=5,i=0.05,F=unknown$
	- plugging into the equation:
	- $\$500(5.526) = \$2763$

- solving for A with that equation:
	- $A = F\left[ \frac{i}{(1+i)^n-1} \right]$
	- essentially, just swap the A and F and take the reciprocal of the fraction in the brackets
	- this is called the *uniform series sinking fund factor*
## Example with solving for A
- Jim wants to buy electric equipment for $1000. He decided to save a uniform amount at the  end of each month so that he would have the required $1000 at the end of one year. The local credit union pays 6% compounded monthly. how much would Jim have to deposit each month?
- solution:
	- $F = 1000, n = 12, i = 0.5\%$
	- $A = \$1000\left( \frac{A}{F}, 0.5\%,12 \right)=\$1000(0.0811) = \$81.10$
	- the $i = 0.5\%$ because it compounds every month for a year. so 6%/12 months
		- which gives 0.5
		- you do this only for the uniform series

- calculating how much it takes to recover funds:
- $A=P\left[ \frac{i(1+i)^n}{(1+i)^n-1} \right]$
	- where
	- P is initial cost
	- `i` is interest rate
	- n is number of times it compounds 
- formally known as *uniform series capital recovery factor*

## Example solving for uniform series capital recovery factor
- an energy-efficient machine costs $5000 and has a half life of five years. If the interest rate is 8%, how much will it have to save every year in order for the initial capital to be recovered?
- $P=\$5000, n=5,i=8\%,A=unknown$
- $A=P\left( \frac{A}{P},8\%,5 \right)=5000(0.2505)=1252$
- the required annual saving to recover capital is 1252


- solving the above formula for P:
- $P=A\left[ \frac{(1+i)^n-1}{i(1+i)^n} \right]$
- notation: $P=A\left( \frac{P}{A},i\%,n \right)$
- formally called *uniform series present worth formula*

## Example for uniform series present worth formula
- an investor holds time-payment purchase contracts for tools. The contract calls for the payment of $140 at the end of each month for a five-year period. The first payment is due in one month. He offers to sell you the contract for $6800 cash today. If you can otherwise make 1% per month on your money, would you accept or reject the offer?
- solution:
	- find out how much money you can make if you do 1% per month on your money. If it is lower than the amount that is offered by the investor, you are going to be paying more than you are going to receive from this trade, therefore it is not worth it. If you are going to make more than 6800 in total, you are going to pay less to the investor and make more money from sales (1% sales)
	- $P=A\left( \frac{P}{A}, 1\%,60 \right)$
	- $=140(44.955)$
	- $=6293.70$
- Since we are going to make about 6.2k, it is not really worth spending more than that on this machine. Because of this, we are better off rejecting this offer. 


# Uniform Series Formula Problem 1
- Joe wants to be able to purchase his dream car for about 19k on Jan 1 2004. Joe has a part time job and started making deposits of 275 each month into an account that pays 9% compounded monthly beginning with the first deposit on 1 Feb 1999. The last deposit is to be made on 1 January 2004. Determine how much money he would have saved to buy the car. Will he be able to buy the car? 
- monthly payment of (A) = 275
- n = 60 months (from 2/1999 - 1/2004)
- `i` = 0.09/12 because monthly = 0.75%
- use the first equation
- this would mean he has about 20k so he can afford it

# Uniform Series Formula Problem 2 
- You are repaying debt of 10k with equal payments made at the end of four equal periods. If the interest rate is 10% per period, how much of the original 10k principle will be paid in the second payment?
- `i` = 10%
- n = 4
- you have F, want to find P
- $P=10k[0.3155]$
	- using the third equation