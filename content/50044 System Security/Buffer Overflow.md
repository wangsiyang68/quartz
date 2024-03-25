Some QnA:
Registers cant point to each other (e.g. ebx cannot point to ecx)

## running gdb
- add the -g
	- `gcc <script.c> -o <executable name> -g`
- to add a break point to a specific line, `gdb break <linenumber>` or `gdb breakpoint +<offset>` from the current breakpoint
- `x/50x $sp` print out the 50 words? after 3the stack pointer
- `run` to run the program
- `run $(python ...)` to run the program with some cmd line code
- `b main` to insert a breakpoint at main
- `b 2` to insert a breakpoint at line 2
- `b +2` to insert a breakpoint offset of 2 lines from the current stopped position
	- [source](https://stackoverflow.com/questions/34190596/setting-a-breakpoint-in-a-specific-line-inside-a-function-with-gdb)
- `b *<addr>` to insert a breakpoint at a specific address in the memory
- `p $sp` to print the address of the stack pointer
- `p &buffer` to print the address of the variable buffer
- `info frame` to get some data about the registers, mainly `rip` and whats saved in the `rip`
- `info registers` to get whats stored in each register
- `info locals` to get information about local data stored in the stack
- `list` to show code with line numbers -- good for debugging at specific line
- `disas <function name>` to show the assembly version of the function
- `backtrace` to see the frame stack
- `select-frame <index>` to move the current frame we are tracking to selected frame `<index>`. 
## other useful commands
- pipe hex outputs into a file with `echo -e '\x90\x90' > hex`, then call `./<function> < hex` to send the hex contents into the gets input function
	- [source](https://stackoverflow.com/questions/28925811/provide-hex-value-as-an-input-to-gets-in-c) 
- get the number of bytes in a file with `wc payload`. The output is line, words, bytes
	- [source](https://www.ibm.com/docs/en/aix/7.1?topic=af-counting-words-lines-bytes-in-files-wc-command)
## reading the stack
- saved eip/rip is the instruction pointer. It points towards the address of the instruction that is being processed right now
- return address is also next to the instruction pointer
- ebp is the bottom of stack

## some assembly knowledge
- refer to [[Assembly]]
## questions
- Why is the result of `p $rip` give me the address of the exact line that we are running, but `info frame` says rip is some where near the `$sp`?
	
- whats the space between the `$rip` and `$sp` ? I just know that theres a return pointer about 2 words down 
	- actually that means theres nothing then innit
- The direction still confuses me...why is it when i increase length of input, the address size also increase? shouldnt it be decrease?
- Why segfault when copying? what does it mean to be unaligned? why is the hex not in the buffer? Is it because i segfault when i copy? ![[Pasted image 20240202000232.png]]

## Successful hacks:
1. Hack gets input function to enter another function into the return address:
	1. first, find the address of the function that you intend to overwrite into the return address
	![[Pasted image 20240201222225.png]] 
	2. Overwrite the char buffer (has 14 bytes worth of space) by first creating a file and then piping the hex file to the program
		 `echo -e '\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x57\x05\x40 > hex`
		 `func-pointer-new < hex` 
#ss