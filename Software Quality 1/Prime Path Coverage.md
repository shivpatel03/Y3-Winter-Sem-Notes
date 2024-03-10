- Done using graphs

- in the 70s, there was a general way of executing loops
	- execute it once
- in the 90s, now we execute loop zero times, once, or more than once (informal description)
	- however, this is obviously not enough for the very complex software that we build today
- 2000s: prime paths (touring, side-trips, and detours)

# Simple Paths and Prime Paths 
- simple path: path from one node to another is simple if no node appears more than once, except possibly the first and last nodes are the same
	- no internal loops
	- a loop is a simple path
- prime path: a simple path that does not appear as a proper sub-path of any other simple path

- paths can range in length, even 1 is possible
	- a prime path is one that does not show up in another path
- if you have a path that is just 1,2, and that 1,2 shows up in another path, that means that the path "1,2" is not a prime path
	- so for an example where there are a maximum of four node combinations, paths that are 1, 2 and 3 in length are not prime, because they are used in the paths that have 4 elements