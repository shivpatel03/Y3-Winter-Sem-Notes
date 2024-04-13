$RE = \text{probability of a risk happening}*\text{cost of that risk}$
- probability is a number between 0 and 1

$\text{Risk Reduction Leverage (RRL)}=(RE_{before}-RE_{after})/\text{cost of risk reduction}$
- if $\text{RRL}>1.00$ it is worth doing.
- check if it is worth doing after a potential fix

# PERT 
- $\text{Optimistic time (a) is the best-case scenario for finishing the task}$
- $\text{Most likely time (m) the average-case scenario for finishing this task}$
- $\text{Pessimistic time (b) is the worst-case scenario for finishing this task}$

- $\text{The expected time of this project would be: }t_{e}=(a+4m+b)/6$
- $\text{Standard deviation (S) = }(b-a)/6$
- $\text{Standard deviation of multiple tasks added together (A, B, C) = }\sqrt{ A^2+B^2+c^2 }$
- $\text{Z value = }(T-t_{e})/S$
	- $\text{where T is the target time for completing}$

# Earned Value Analysis 
- $\text{Planned Value (PV): Authorized budget assigned for the work}$
- $\text{Earned Value (EV): Measure of work that is already done}$
- $\text{Actual Cost (AC): Realized cost incurred for the work performed on an activity}$
- $\text{schedule variance (SV)} = EV-PV$
	- resources used on the work that is done - total resources available
- $\text{schedule performance indicator}=EV/PV$
	- ratio between resources used on work that is done and total resources available
	- SV < 0 or SPI < 1.00 means project is behind schedule

- $\text{cost variance (CV)}=EV-AC$
- $\text{cost peformance indicator (CPI)}=EV/AC$
- CV>0 or CPI > 1.00 -> project is within budget

- $\text{schedule variance=earned value - present value}$
- $\text{cost variance=earned value - actual cost}$
- $\text{schedule performance indicator=earned value / planned value}$
- $\text{cost performance indicator=earned value / actual cost}$


- assume you have some risk before, that has some chance of happening. that risk will have some cost when it happens
- and you have some risk after some mitigation, which has some chance of happening and will have some cost when it happens
- RRL = (chance of first * cost if first happens - chance of second * cost if second happens) / cost to implement second
	- if you had 1% chance of a 200k fire happening, you could mitigate it to 0.5% and it would cost 500. this would be the equation:
	- (200k * 1% - 200k * 0.5%)/500