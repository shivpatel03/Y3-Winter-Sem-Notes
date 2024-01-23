# Using TDD to Create Good Code
## Designing Good Quality Code 
- not easy, requires many thoughts about the code that you are writing
- TDD does not design your code for you
	- TDD only gives you a structured way to develop your code
	- as the engineer, you should still be able to use your creative input to create code that meets the requirements of the software
- TDD is something that allows you to get quick feedback on design changes
- good code is: 
	- readability
	- optimizing for clarity
	- want to be kind to my future self and colleagues who are going to be looking at the code
- basics of writing good code: 
	- "Say what you mean, mean what you say"
	- "Take care of the details in private"
	- "Avoid accidental complexity"

## Say what you mean, mean what you say
- experiment:
	- write a piece of code in any language, and replace all the language-specific syntax with `???` and see if you can figure out what the code is trying to accomplish
```
public boolean ??? (int ???) {
	if (??? > ???) {
		return ???;
	}
	return ???;
}
```

- names are very important in code
- two guidelines to figure out good names: 
	- Method names: say what it does. what is the outcome? why should I call this? 
	- Variable names: say what it contains. why would I access this?
- common mistake with method naming: describing how it works internally
- classic mistake with variable names is just naming it the data structure that it is 
	- example: `String string`
## Take Care of the Details in Private
- abstraction and information hiding
- abstraction can be thought of hiring an electrician to fix something at home
	- you know you have to fix something but you want to figure out how, or get the tools. rather you call the electrician that comes over and does that for you. he hides the information about the problem, but when you call him, the problem gets fixed through his solution
	- simple request will lead to a complex problem. this is the basic idea behind abstraction
- when you make a detail less important, you have abstracted it
- splitting software into small parts, each of which that do something for us, a massive quality driver. leads to better code

## Avoid Accidental Complexity
- code that simply never needed to exist 
- goal for code is to be able to look at it, and at first sight, figure out what we are trying to solve
- as our code gets better at telling the story of the problem, it also becomes easier to write replacement components
- `cyclomatic complexity (CYC)` -> objective measure of how complex a piece of code is, based on the number of independent execution paths are possible in a section of code


## Revealing Design Flaws 
- first main benefit of TDD is that it makes us think about the design of a specific component 
	- we do that before we even think about implementing it 
- by doing it in this order, we are far less likely to design badly by mistake 
- the way we consider the design first is to think about the public interfaces of a component
	- about how that component will be used and how it will be called
	- "outside-in" thinking
- typically when we want to code something, we start by writing an implementation. and then ripple out whatever is needed in method signatures, without a thought about the call of the method itself
- outside-in lets us think about the perfect component for its users. we will bend the implementation to work with our desired code at the call site. Unfortunately, this is more important than the implementation itself. this is abstraction being used


- by writing tests first, we can can answer these questions that should be asked before designing the method
	- is it easy to set up? 
	- is it easy to ask to do something?
	- is the outcome easy to work with?
	- is it difficult to use in the wrong way? 
	- have we made any incorrect assumptions about it? 
- with tests, we decide how upfront we are going to set up our component, perhaps deciding on a clear constructor signature for an object
	- all of this leads to better code
- TDD does not do this for us, and it doesn't even force us to do a better job. we could still come up with terrible answers to these questions, and simply write a test to lock those poor answers into place
- TDD provides an early opportunity to reflect on our decisions. we are literally writing the first example of a working, executable call site for our code before we even think about how it will work
	- we are more interested in how it fits into the bigger picture of the software 
- test provides immediate feedback

## Analyzing the benefits of writing test code before production code
- you can write tests at three different times: before the code, after the code, or never
- writing code just after completing a small chunk of code is a much better option. we get faster feedback. our code isn't necessarily better though
- can lead to the some problems: 
	- missing tests
	- leaky abstractions

### Missing tests - undetected errors
- example: checking if someone is over the age of 18
	- you would instantly think about using `age > 18` but you would most likely forget about checking if `age` is `Null`. this is just something that happens when you're writing code and not thinking about specifics
	- however, when you're writing the test code for this type of code, you are more likely to remember that edge-case, and use that in your testing
		- this means that you will catch that error soon 

### Leaky Abstractions - exposing irrelevant details 
- when we focus so much on the inside of the method that we forget to think about our "dream call site"


# Preventing Logic Flaws
## Understanding the limits of manual testing
- when we focus on the bigger picture of the code, we often forget some of the nuances and critical details, and they go unnoticed
- manual testing often gets blamed for delayed shipping dates
	- however, sometimes the real cause is the development taking longer than it should

## Solving problems by automating the tests
- TDD has this covered
- in TDD, before you type any production code, you already have written a failing test. once you have your new code, you rerun the test. if you messed up some logic error or something, you will know right away
- the whole idea here is that you mess something up, you know right away
- this is 10 seconds of work vs. months of waiting to see if the code that you wrote is good or bad
- these unit tests are also generally extremely fast, much faster than manual

## Protecting against future defects
- once a test passes, don't delete it, keep it for later
- as we add more to the code base, keeping the tests passing shows that nobody accidentally broke something
- this is the idea behind agility, being able to quickly and confidently code things for the requirements
- having many tests running constantly is probably some of the biggest enabling practices that we have
- allows us to "move fast and not break things"

# Documenting our code
- the more separation between two related ideas, the more confusion they will bring
	- example: think of code that reads obscure file formats that no one remembers. all works well, as long as you are reading in that file format and nothing else
	- when you upgrade that application, the file is no longer supported and everything breaks. the files didn't change, but the code did
- same idea with documentation
	- the worst documentation often contains the glossiest productions. 