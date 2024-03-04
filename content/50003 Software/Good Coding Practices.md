# Characteristics:
---
- No code smells
	- Avoid unvalidated input
		- Example: SQL injection whereby SQL code snippets are placed into the username and and password entry to attack the software
			- Solution 1: Hash the username/passwordo
			- Solution 2: Treat the whole username/password as a string input
		- Example: XML injection
		- Example: XSS injection:
			- Was expecting some string but received code
			- forbid `<script>` tags in place where we are not expecting code input

	- Object orientation
		- idea of private and public methods/attribute
		- Not so simple, need to consider whether a private attribute can be edited outside the class because it was instantiated by passing a reference, which exists outside
			- Solution: Create a copy (deepcopy library or by getting the content and sending it to a new object)
		- Sometimes u want smth to be final, but you only make the outside part to be final. But the inisde not final.
			- Solution: make sure the method is private
			- In addition, only return a copy of the attribute when asked to get something

	- Also related to dedlocks, in terms of bad code
- follow comments guidelines
- little repeated code
- no long method
	- prefer to have a single, clear objective
	- ideally, should not have alot of responsibilities.
		- If have, can delegate that to another function, and focus on what that function is really supposed to do
- BlackHole classes/ god code
	- usually results from many people adding features onto an existing project, because it is easier to add a new feature to the main class (all the rights to access variables are available)
- No data class
	- opposite of black hole; so little responsibility that it only contains data
- No data clumps (opp of above)
- No feature envy
- No long message chains
- No speculative Generality
- No refused bequest
- No long parameters
- no shotgun surgery

#todo How is SQL/XML injection related to coding practices?
#todo what are the measures that we can take to avoid these bad characteristics?

#testing 