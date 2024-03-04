## Expected behaviour
- Fstrings take in a value from somewhere in the stack

## Exploit
- Use `printf` on a statement that has `%` and then not provide anything.
	- `printf("100% dude\n)`
- If sensitive data is in the top of the stack, then 
	- Where is the stack location?
	- How to input secret into the top of the stack without actually knowing the contents?