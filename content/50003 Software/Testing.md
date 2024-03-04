# Testing
1. Test generation (How to automatically come up with tests?)
	1.  [[Fuzzing]]
		1. Random
		2. Mutation
		3. Feedback
2. Test Design (What kind of inputs to give?)
	1. Black box
	2. White box
	3. Fault-based
3. Test Execution (How to run tests?)
	- Junit (unit), Selenium (web system)

Test oracle definition:
- can tell you whether your test has passed or failed
- it contains the "expected outcome" and the "compare with actual outcome" component
- Ideally, it should not hardcode the answer. This is because that is more similar to machine learning, where we will not know expected output for unseen input

Web app testing ideas:
- check if the links are working

How to reduce bugs:
- Adopt [[Good Coding Practices]]

## Software Mini Testing Campaign
[[Week 9 Deliverables]]

## Black-box testing
Each test case should be related to at least one requirement

Equivalence Class Partitioning:
- Divide inputs conditions into groups (correct, incorrect, boundary)
- Then take one of each group to test, assuming that behaviour of that one test case will represent the rest of the test cases in its group

## [[White box testing]]
Different types of coverage in increasing comprehensiveness: Statement, branch, condition, paths, function, custom
- Statement Coverage < Branch Coverage
	- If achieve statement coverage, does not mean achieve branch coverage
	- If achieve branch coverage, means achieve statement coverage
- Control flow graph 
	- An arrow refers to a branch, and a box refers to a statement

- Statement coverage:
	- How many boxes can you reach, given your set of inputs?
	- Coverage can be quantified by the % of boxes out of all total boxes traversed

- Branch coverage:
	- Ignore branches that cannot be reached

- Path coverage:
	- A path can be unique even though it has the same set of statements, as long it has a different sequence that is traversable
	- However, some paths are infeasible depending on the paths (e.g. a 2nd condition that contradicts an earlier condition)
	- For such paths that cannot be executed, must disregard them
	- If the code is rather complicated, do the following:
		- Draw control flow graph first
		- Enumerate all "possible" paths within a loop first (disregard the statement)
		- Write out all the if conditions in CNF format and check if they make sense
		- If told to ignore paths that never terminate within N iterations, need to check they can end execution within N iterations
	- Branch coverage does not mean path coverage, as the branch coverage only guarantees a set of branches are present, not the **sequence**

**Path Coverage IRL**  
Examples: Microsoft SAGE, successful in finding bugs through executing exotic paths
Drawback: Takes a long time to execute

#testing 