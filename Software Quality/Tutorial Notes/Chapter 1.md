## Error Prone Constructs
- there are always more than one way to do things in code, but some provide more scope to introduce mistakes than others
- it is obviously very important to choose the right (or better) way to code then
- example: consider this code block

```
int calculateTotal (List<Integer> values) {
	int total = 0;
	for (int i = 0; i < values.size(); i++ ) {
		total += values.get(i);
	}
	return total;
}
```
- this code block is very error prone, as you have to check for the following:
	- making sure total is 0
	- making sure `i` starts at 0
	- making sure we use < instead of <= or == in the loop
	- etc.
- although these things are generally not a problem, the fact that they can be a problem is the problem


## Coupling and Cohesion
- in class design, coupling is the relationship between these two classes, while cohesion describes relationships between the methods in each one

### Low cohesion inside a class
- describes code that has many different ideas together within a single class (in the form of methods)
- combines too many responsibilities to one class
	- not good
	- hard to understand, because we are forced to understand many ideas at once
### High Coupling Between Classes
- describes when one class needs to connect to many others before it can be used
- hard to use in isolation
- cannot understand the use of a single class unless you understand every single interaction that it has, which can get difficult


## Decreasing Team Performance
- technical debt is used, rather than the words "bad code"
- technical debt refers to code that is shipping with known technical issues in order to meet a deadline 
- while bad code might have some of the same defects, but it lacks the redeeming quality of intentionality
- every minute we spend looking at code that does not make sense is costly, as you are losing money and time towards the final product
	- this happens very often 
- leaving bad code in will require us to have other workarounds for future features, which may even make the code worse to read for future developers
- this is, for obvious reasons, not wanted

## Diminishing Business Outcomes 
- not just development team that is affected by bad code, but also the business
- end users who bought the software doesn't work, or eat least not properly
- they don't care about the code itself, only whether the software that they bought works as intended or not
	- if not, their money was not worthwhile
- this is when the bad code is no longer bad code, but a commercial liability

- as we progress more and more in the stages of development, the cost to fix a problem if it arises increases exponentially