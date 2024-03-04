# Information Flow
---
Need to prove whether something can or cannot happen
- Useful skill to prove the safety of a code, especially code written for cases that need high accuracy

Information flow policies define the way information moves throughout a system.
We can design information flow policies to prevent

Key idea: **non-interfering**

Examples:
1. does my coordinates info to map app being transmitted to untrusted third parties afterwards?
2. can my data be altered, violating integrity?
3. can my data be leaked, violating confidentiality?

Example of flowing to unauthorized flow: Given a state diagram, the system must not reach an unauthorized state from an authorized state

**Functions**:
- State transition function: describe effect of executing command c in state sigma
- Output function: output of machine 
- Initial state is little sigma

Example: Holly has high clearance, so holly can read both high and low bit info
info. Lucy can only read low bit info

## Projection:
intuition: removing outputs that s cannot see (kind of like vector projection onto plane)
1. Firstly do the output function
2. Then remove stuff that user cannot see

## Purge 
intuition: filter/restrict command history ($c_s$)
context: G is a group of subjects, A is a set of commands
You can either purge for subjects, commands or subjects performing commands
Example: purge commands for group G: means remove commands performed by ppl in G
Note that this action does not alter actual history, just filter

## Non-interference
Intuition: 
- Set of outputs Lucy can see corresponsds to set of inputs that she can see, there is no interference.
- Whatever is done in high bit, does not leak to low bit (low bit does not know of high bit action)
what lucy can see does not change, whether holly exists in the system/issues any commands
Result: In essence, a system is secure if groups of subjects are non-interfering with one another

projection(s,cs,states) = projection(s, purged cs, states)

## Information Flow Definition
information flows from an object x to an object y if the application of a sequence of commands c causes the information initially in x to affect the information in y.

Key idea: **Entropy**
Definitions:
- c is a sequence of commands taking a system from state s to state t
- x and y are objects in the system; $x_s$ and $y_s$ are values at state s 

Intuition: c causes a flow of information if entropy increases? #todo try rigorous practice

Key idea: **Implicit Flow of Information**
Implicit flows are information flows from x to y without an explicit assignment of the form y := f(x)
#todo how are the examples demonstrating information flow?

## Policy Violation measures
To detect and stop flow of information that violate policy
3 ways to calculate information leak:
Recap: Information is the "decrease" in uncertainty gained after knowing it
- A probability concept

$$H(X) = –Σ_iP(X = x_i) lg P(X =x_i)$$

- An interesting brain teaser: how many rats do you need to find the poison 
	- $log_2(n)$
	- if no rats die, means that vial 0 contains the poison
	- Key idea: entropy can be thought of: how many bits needed to represent all states

- **Entropy calculation**
$$H(x_s | y_t) < H(x_s |y_s)$$
	- If given a observation of y state in later (ys to yt), there is a decrease in entropy, means there is a decrease in uncertainty, so there is an increase in information about x gained by person observing the y state
	- above equation means that information flow from x to y #todo check with above contradictory statement
	- information flow is akin to a transfer (so flow from x to y means x's state depends more on y now)
- An object x has at most n states $H(x) <= log(n)$
	- Uniform distribution has the highest entropy (i.e. $log(n)$)

**FOR WORKING:** Refer to OneNote Info Flow 2 notes

Instead of calculating math, there are some **rule-based checks** that we can perfrom
- **Compiler-based mechanisms**
	- An example policy statement: 
		- x < y
			- means information can flow from an element in class of x to an element in class of y
			- x (underscored) refers to the security class of x deined by the policy
	- Analysis is not precise, but secure
		- I.e. can have false positive, but no unauth path along which information could flow remains undetected. #todo what is an example of a false positive?
	- An action that follows the above rule means that it will be **Certified**

	#todo conditional, array statements
	- Conditional Statements
		- If a = b:
			- then b < a
		- If d = b * c -x
			- then max(b, c, x) < d
	- Iterative statements #todo
	- Loop statements
		- need to consider infinite loops


- **Execution-based mechanisms**
	- Done at run time, not compile time
	- Checck if each flow of information violated policy
	- What about implicit flows?
		- A problem as they may be incorrectly certified
		- #todo what is an implicit flow? is it branches that are not explicitly stated (i.e. missing else case)
- #todo what are the differences?

#foc 


