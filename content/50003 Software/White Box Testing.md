# White Box Testing
---
## Key Idea
Given that the entire code is known, systematically test the code to ensure bug absence

## Hierarchy of coverage
There is an idea of a "hierarchy of things" to test, in increasing scope:
1. Statements (statements & statements within if branch)
2. Branch
	- Do not consider statements that cannot be reached.
	- However, in real life, it is often difficult to estimate whether a statement can be reached. Therefore, we can only give an estimate/ballpark figure
	- Branch coverage means statement coverage
	- However, branch coverage does not reveal all the bugs as there may be specific values that will result in failure
3. Condition
	- Different from branch coverage.
	- First, breakdown boolean statements into atomic statemennts. Then, need to make sure that each condition of the atomic statement has been traversed (i.e. check scenario of both True and False of all atomic statement)
	- Condition = Branch coverage when all statements will be 
4. Path
5. Functions
6. Custom stuff 

Now, we also have White-Box Fuzzing
- Language specific

Idea: [[Symbolic Execution]]
- Intuition: Run satisfiability check for branches to check whether branch will be actually generated
- Rather than executing a program with concrete input value, execute it with symbolic variables representing the inputs
- An interpreter follows the program, **assuming symbolic values (retain variable names) for inputs** rather than obtaining actual inputs as normal execution of the program would. It thus arrives at expressions in terms of those symbols for expressions and variables in the program, and constraints in terms of those symbols for the possible outcomes of each conditional branch. Finally, the possible inputs that trigger a branch can be determined by solving the constraints.
	- so basically symbolic testing is turn every branch into a sat statement (each statement combine with previous with AND operator), then check if it is satisfiable
	- if branch is not satisfiable:
		- can stop exploding that branch
	- if branch is satisfiable:
		- IF POSSIBLE, set the constraints of the statement in branch (i.e. divisor cannot be == 0) into the sat statement 
		- SAT tries to make the statement satisfiable. Therefore, it checks if y can be 0. If the whole statement is satisfied then, y can be 0 which then means you should throw error.
- Symbolic execution will ensure **path coverage**, because if there are multiple loops, the if branch statements will be added to the SAT statements

**Problems**
1. Path Explosion problem = infinite loop cause the solver to never end i guess
2. Incompleteness = only work for linear integer arithmetic, bit vectors, string, not great for non-linear data types 
	- Example: `if (x*x*x*x + y*y*y < z*z) //jesus christ`
#testing 