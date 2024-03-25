Functions start with prologs & epilogs. These are the admin stuff that makes the stack expand and grow correctly

## Prolog

```
//prolog
push ebp
mov	ebp, esp
sub	esp, N
```
Meaning:
1. add saved ebp -> Setting return address
2. move ebp to esp (copy value of esp into ebp) -> create new stack
3. grow stack by moving esp to a lower place  -> create the top of new stack

Read this [website](https://manybutfinite.com/post/journey-to-the-stack/) for a graphical description of how the prolog creates the stack in a frame
## Epilogue
```
mov	esp, ebp
pop	ebp
ret
```
Meaning:
1. move esp to ebp (copy value of ebp into esp) -> remove the stack
2. remove top the stack, get the value and set it to be the value of ebp
	1. pop `<address>` means to send the value of the the top of the stack into the value in `<address>`
	2. So we are resetting the ebp
	3. note that the saved ebp is also removed, so now we just looking at the return address
3. ret pops the top of the stack (return address), and then jumps to the contents inside the top of the stack
Therefore, everything is set back to normal.

Note: leave = first two instructions, a built in instruction to the x86 architecture

## Case Study:
Using Return to Lib C and gadgets to unlink a specific file, and that address is mentioned at the start of the stack
![[IMG000.jpg]]

#ss 
