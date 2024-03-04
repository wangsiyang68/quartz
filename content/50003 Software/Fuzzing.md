# Fuzzing
---
Fuzzing is one of the implementations of the Test Generation
It is is an automated software testing technique that involves providing **invalid, unexpected, or random data** as inputs to a computer program
- Previously, we were only looking at valid input. Now, we are looking at unexpected input in fuzzing

## Test components
---
**Inputs**
1. Naive Fuzzer
	- Random monke input generator to generate totally nonsensical random input
	- However, most software today have an input validation at the start to remove random input
		- e.g. Check all array bounds, apply bounds on program inputs, check all return values of a fucntion, not trusting third party inputs
2. Mutated Fuzzing
	- Start with a valid set of inputs, then apply some mutations (a la gene mutation) to create invalid inputs
		- Mutations include: chopping off input at random indexes, flipping a random bit of a randomly selected byte, swapping characters, inserting characters
	- Capture valid inputs by a grammar
	- Can use regex for fuzzing
	- However, the current fuzzing methods only allow us to discover inputs within the neighbourhood of expected input
3. Create valid inputs by grammar: 
	- create valid input by ensuring that mutations happen along the syntax as provided (e.g. think of the expected inputs for a calculator)
4. Generational Fuzzing/Feedback-based fuzzing
	- Made up of 3 parts: 
		1. collect feedback (a relatively easier problem!)
		2. generate new test cases (a hard problem!)
		3. carry out the test cases (covered earlier!)
	- **Collect feedback**: **collect data about branch coverage** through Code instrumentation/instrumentation tool
		- Print stuff to figure out branch coverage?
		- Existing tools for systematic code instrumentation (e.g. Soot)
		- There is a consideration of overhead? what is the overhead -- is it the printing of statements to show code coverage
			- Only need to introduce a print statement on one of the two if else branches -- if it doesnt appear, it menas that it went onto the other branch, for sure
	- **Collect feedback: Crash Detection**
		- Method 1: attach a debugger
		- Runtime monitoring thru code instrumentation
		- Timeout to know whether a deadlock or infinite loop has been triggered

**Idea**: Genetic algorithm converts testing problem into an optimization problem
- e.g. Maximize the branch coverage, # of memory allocated but not freed (finding memory leak), maximize buffer overflow bug finding through # array, buffer, string copy executed

**Connection of genetics with software testing?**
- inputs = population
- Consider 1 byte to be one gene, 1 sequence of genes/a chromosome to be one input (n byte)
- Fitness depends on the objective, need to think about this carefully
	- For coverage-based testing, fitter mens test inputs obtain more coverage
- To generate new population, swap some bytes/genes between two test inputs to create an offspring
	- Generate fitter offspring by selecting **two best performing test cases** in a sub population and perform crossover on them
	- Mutate a random gene in a test case: however, mutation frequency is very low
- You can stop the iteration after:
	- A fixed number of iterations
	- A fixed time
	- When the fitness(i) - fitness(i-1) < epsilon (marginal increase in fitness) (also the best case)

**Test oracle**
The test oracle for fuzzing are usually not expected output. What we are trying to check is if it will (at a simplified level):
	1. No hang
	2. No crash
	3. No unhandled exception
	4. No memory corruption
- If any of the above happens, then test fails. Otherwise, test pass.
- The first three could lead to denial of service attack (availability), while the last one leads to unauthorized access to confidential info

**Challenges**
- crashing test cases may be difficult to analyse -- not clear how problem occurs and hence how to fix
- complex inputs require more work to create a smart enough fuzzer to attain sufficient code coverage

**Extra information**
"sans top 25 software errors" is a list of the top bugs that are exploited, many are unintended input
#testing 