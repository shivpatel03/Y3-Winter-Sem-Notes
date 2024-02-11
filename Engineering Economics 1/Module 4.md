# Computing cash flows
 - benefits and costs are receipts (cash flowing in)
 - disbursements (cash flowing out)
 - foundation of engineering econ analysis are techniques that compare the value of money at different dates

# Time value of Money
- when monetary consequences occur in a considerable period, we can't just add up the money
- money
	- has value over time
	- valuable asset, people are willing to pay to have it available to use
	- can be "rented" 
		- just like an apartment
		- this "rent" is actually just interest
- having money now vs. money in the future (depends on the person)
	- this has nothing to do with inflation
- bank accounts for time value by publishing an interest rate


- simple interest
	- interest that is computed only on the original sum and not an accrued interest
		- total interest earned: `P x i x i = Pin`
			- P = present sum 
			- i = interest rate/period
			- n = # of periods
		- total interest after n periods `(F) = P + Pin` or `F = P(1+in)`
			- where F = future sum
	- Example of simple interest
		- you have agreed to lend a friend $5000 @ interest rate of 8%/year. How much interest will you receive from the loan. How much interest will your friend pay you at the end of the five years
		- total interest earned: (5000)(0.08)(5) = $2000
			- (present sum)(interest rate)(number of periods)
		- amount due at the end of the loan = 5000 + 2000 = $7000
- compound interest
	- usually in the real world, interest is determined using the compound interest method
	- simple interest normally not used
	- interest calculated on the accumulated amount, not original amount
		- interest on top of interest
	- example: consider a $25000 loan at 10%/year

| Year "n" | Total in year "n" | Interest Accumulated at the end of year "n" | Amount accumulated at the end of year "n" |
| ---- | ---- | ---- | ---- |
| 1 | 25000 | 2500 | 27500 |
| 2 | 27500 | 2750 | 30250 |
| 3 | 30250 | 3025 | 33275 |
| 4 | 33275 | 3327.5 | 36602.50 |
- notice that the third column is 10% of the second column
	- meaning that the 10% is 10% from the accumulated amount, not the starting amount
- repaying a debt
	- there are many ways that debt are repaid, these are three plans
		1. constant principal
		2. interest only
		3. constant payments

# Equivalence 
- sum of money in one period of time may have the same "value" as a sum of money at a different period (with respect to interest rate)
- example: 
	- $1000 now is equivalent to
		- 1100 on year from now at 10% per year
		- 1050 on year from now at 5% per year
		- 1210 two years from now at 10% per year
		- 1102 two years from now at 5% per year
- equivalence dependent on interest rate
- useful when:
	- cash flows (positive or negative) over an amount of time that need to be compared
	- there are alternative comparisons of multiple cash flows
		- alternative projects with cash flows over "n" time periods


# Single-Payment Compound Interest Formulas
- Notation:
	- `i` = interest rate per interest period
	- `n` = number of interest periods
	- `P` = present sum of money
	- `F` = future sum of money at the end of the `nth` interest period, which is equivalent to `P` at the interest rate `i`

- if the interest rate's period is in years:
	- after one year, the future amount at the end of the year will be:
		- `F = P(1+i)`
	- after two years, the future amount at the end of year two would be the additional interest on year one's total
		- `F = P(1+i) + i*P(1+i)`
	- by rearranging, we get: 
		- `F = P(1+i)(1+i) or P(1+i)^2`
	- generalizing: 
		- `F = P(1+i)^n`
	- this formula is the "single payment compound amount formula,", which is written in functional notation as: `F=P(F/P,i,n)`
		- this notation means that the future sum `F` given present sum `P` at interest rate `i` per interest period for `n` periods


# Simple and Compound Interest Problem 
- How much would you owe at the end of 4 years using: 
	- simple interest at 9% per year
	- compound interest at 9% per year
- if you borrowed 150000 now


- simple interest:
	- F = P + Pin = 150000 + 150000(0.09)(4)
		- = 204000
	- F = P(1+i)^n
		- = 150000(1.09)^4
		- = 211737.24
	- 211737.24 - 204000 = 7737.24
		- you would owe 7737.24 more if you used the compound interest arrangement

# Single Payment Compound Interest: Problem 
- $3000 deposited in a bank account at 7% per year interest would be how much after 4 years?
- solution:
	- `F = P(F/P, 7%, 4)` -> this is the functional notation
	- `F = 3000(1+0.07)^4`
	- `F = 3932.39`
- suppose you want to find an equivalent value now for a future value
	- move the equation around 
		- F = P(1+i)<sup>n</sup>`
		- P = F(1/(1+i)<sup>n</sup>
		- P = F(1+i)<sup>-n</sup>
	- notation becomes
		- `P = F(P/F,i,n)`
- If you want to have 3000 in the bank after four years at 7% per  year interest, what should you deposit now?
	- solution:
		- `P = F(P/f, 7%, 4`
		- P = 3000(1+0.07)<sup>-4</sup>
		- 2288,68 should be deposited now 

# Single Payment Factors (F/P and P/F)
![[Pasted image 20240206113406.png]]
![[Pasted image 20240206113415.png]]

# Nominal and Effective Interest
 - when specifying an interest rate, we indirectly mention two time periods
	 - we pay the interest rate if `i` per *time_period1*, compounded every *time_period2*
 - Effective interest rate: when these time periods are the same
 - Nominal interest rate: when these time periods are not the same


# Interest Rate Statements
- the terms "nominal" and "effective" are only considered when the interest period is LESS THAN ONE YEAR
- new time-based definitions (REMEMBER THESE)
	- interest period (t) = period of time where interest is expressed
		- example: 1% **per month**
	- compounding period (CP) = shortest time unit over which interest is charged or earned
		- example: 10% per year, **compounded monthly**
	- compounding frequency (m) = number of compounding occurs inside the interest period `t`

# Understanding Interest Rate Terminology
- nominal interest rate (r): obtained by multiplying interest rate over a short period of time by the number of compounding periods in a longer period of time
	- r = interest rate per period * number of compounding periods
		- example: if `i=1% per month`, then nominal rate per year is:
			- `r=(1)(12) = 12% per year`
			- there are 12 months in a year, the "number of compounding periods" would be the number of times that it raises 1% (which is 12 in this case because we want the nominal rate **per year**)
- effective interest rates (`i`) take compounding into account
- NOTE: nominal interest rates are essentially simple interest rates. Therefore, they can never be used in interest formulas
	- effective rates must always be used hereafter in all interest formulas


# More about Interest Rate Terminology
Three ways to express interest rates:

| Statement | Comment |
| ---- | ---- |
| `i = 2% per month`<br>`i = 12% per year` | When no compounding period is given, the rate is *effective* |
| `i = 10% per year, compounded semiannually`<br>`i = 3% per quarter, compounded monthly` | When compounding period is given and IT IS NOT THE SAME as interest period, it is *nominal* |
| `i = effective 9.4%/year, comp'd semiannually`<br>`i = effective 4%/quarter, comp'd monthly` | When compounding period is given and rate is specified as effective, the rate is *effective* over stated period |

# Effective Annual Interest Rates
- nominal rates are converted into effective annual rates via this equation: 
$$i_a = (1+\frac{r}{m})^m - 1$$
	$$i_a = (1+i)^m-1$$
- where:
	- $i_{a}=\text{effective annual interest rate}$
	- $i = \text{effective rate for one compounding period}$
	- $m=\text{number times interest is compounded in a year}$
- example: 
	- For a nominal interest rate of 12% per year, determine the nominal and effective rates per year for a) quarterly and b) monthly compounding
- solution:
	- a) $\text{Nominal r/year} = 12\%\text{ per year}$
		- $\text{Nominal r/quarter} = \frac{12}{4} = 3.0\% \text{ per quarter}$
		- $Effective \frac{i}{year} = (1+0.03)^4 - 1 = 12.55\% \text{ per year}$
	- b) $\text{Nominal r/month} = \frac{12}{12} = 1.0\% \text{ per month}$
		- $\text{Effective i/year} = (1+0.01)^{12} -1 = 12.68\% \text{ per year}$

# Continuous Compounding 
- The number of compounding periods depends on the number of subdivisions
- a nominal interest rate of $12\% \text{ per year}$ compounded:
	- $m =1:\text{yearly} \text{ equals 12\% effectively yearly}$
	- $m=2 \text{ : semi annually equals 12.360\% effectiv yearly}$
	- $m=4 \text{ : quarterly equls 12.551\% effective yearly}$
	- $m=52 \text{ : weekly equals 12.734\% effective yearly}$
	- $m=365\text{ : daily equals 12.747\% effective yearly}$
	- $m=525600\text{ : hourly equals 12.749\% effective yearly}$
- note: there is a limit
- for infinite compounding periods (continuously compounded)
	- $i_{-a}=(e^r)-1$
- to find compound amount and present worth for continuous compounding and single payment, we write:
	- compound amount $F=P(e^{rn}) = P[F/P, r, n]$
	- present worth $P =F(e^{-rn}) = F[P/F, r, n]$
	- square brackets around the factors show continuous compounding

# Equivalence and Sustainability 
- The formulas and methods here give reasonable results when applied to time spans that are less than a century, but they are misleading for anything further than that
- many of the problems that humanity currently faces requires us to plan on a time scale of centuries or longer
