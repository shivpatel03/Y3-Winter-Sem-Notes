# benefits of input domain modelling 
- fewer tests
- no implementation knowledge needed, only the input space is needed

# input domains 
- input domain: all possible inputs to program
- input parameters: scope of input domain
- partition input domains into regions (blocks)
- choose one value to test from each block: 
Example: 
```
input domain: Alphabetic letters (all of the inputs are alphabetic letters)
characteristic: case of the letter
	includes block 1 and block 2
	block 1 may have lowercase and block 2 may have uppercase letters
```

- partition is within a domain of inputs
	- these partitions must have no overlap, and also cover the domain D (complete)

# what is a characteristic? 
- feature or quality belonging to person, place, thing to identify it
- input: people
- characteristic: hair color, major
- blocks: 
	- A=(red, black, brown, blonde, other)
	- B=(cs, swe, ce, math, other)

# example
- characteristics: 
	- whether X is null
	- order of list F
	- min separation between two aircraft
	- input device
	- hair color, height, major, age
- partition characteristic into blocks
	- single-value or set of values
	- each value in block should be equally useful for testing 
- each abstract test has one block from each characteristic

# choosing partitions 
- partitions is not hard, it's just easy to get wrong
- consider the "order of elements in list F"
```
b1 = sorting in ascending order
b2 = sorted in descending order
b3 = sorted in arbitrary order
```
- however, every single block within this characteristic will have the same element in it 
	- that means the "disjoint rule" is not followed
	- so to fix this, you can create two new characteristics:
		- C1 = list F sorted ascending
		- C2 = list F sorted descending
			- and then the blocks would just be true and false for b1 and b2 respectively for C1
			- the possible values for b1 and b2 become only true or false
# modeling the input domain
1. identify functions to test
2. find all inputs, parameters, characteristics 
3. model input domain
4. apply test criterion to choose combination of values
5. refine combinations of blocks into test inputs

# example input domain model 
- `triang()` takes three sides, returns the type of triangle it is
- IDM:
	- characteristic: relation of side with zero
	- blocks: negative, positive, zero
- another IDM:
	- characteristic: type of triangle
	- blocks: scalene, isosceles, equilateral, invalid

from the above steps: 
- step 2: inputs, characteristics, parameters
	- characteristics based on syntax
		- "list is null" (b1 = true, b2 = false)
		- "list is empty" (b1 = true, b2 = false)
	- characteristics based on behavior:
		- "number of occurrences in list" (b1 = 0, b2 = 1, b3 = greater than 1)
		- "element occurs first in list" (b1 = true, b2 = false)
		- "element occurs last in list" (b1 = true, b2 = false)
		- "type of triangle" (b1 = equilateral, b2 = scalene, b3 = isosceles, b4 = invalid)
			- can also change this to four characteristics, each with b1 = true, b2 = false

# IDM hints 
- more characteristics = more tests
- more blocks = more tests
- do not use program source
- want more characteristics with fewer blocks
	- less mistakes, less tests
- choose values strategically 
	- valid, invalid, special values
	- explore boundaries
	- balance number of blocks in characteristics

# all combinations criterion
- when characteristics and blocks are created, the tests are made by taking one block from each characteristic 
- this makes sure that you go through every single combination and cover every possibility


# example: 
- input: students
- characteristics: level, mode, major, classification
- blocks:
	- level: (grad, undergrad)
	- mode: (full-time, part-time)
	- major: (cs, swe, other)
	- classification: (in-state, out-of-state)
- abstract input domain model
	- A = [ a1, a2 ]
	- B = [ b1, b2 ]
	- C = [ c1, c2, c3 ]
	- D = [ d1, d2 ]
- combinations: 2 x 2 x 3 x 2


# ISP criteria - each choice
- in test cases, you should at try at least one value from each block
- this means that you will use one block for each characteristic in at least one test case, which assumes you checked that ever part of the program works (with all input values)

# above example but with each choice criteria
- it needs max(2, 2, 3, 2) = 3 tests
- as it does not have to cover every single combination, just have to go through every value in each block at least once
```
a1 b1 c1 d1
a2 b2 c2 d2
a1 b1 c3 d1
```
- not every combination is done, but all elements in those blocks have been covered 

# base choice
- each choice is simple, but very few tests
- takes into account that some blocks are more important than others
- uses more diverse combinations to make testing better
- base choice coverage (BCC): choose a block from the characteristic (base choice). 

- all tests are done while keeping one block constant throughout

- base test must be feasible
	- all base choices must be compatible

## for the above example: 
- number of tests: 1(base) + 1 + 1 + 2 + 1 = 6
```
base test = a1 b1 c1 d1
test A = a2 b1 c1 d1
test B = a1 b2 c1 d1
test C = a1 b1 c2 d1
test D = a1 b1 c1 d2
```