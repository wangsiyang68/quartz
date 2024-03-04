Summary:
Return-oriented programming (ROP) is a clever technique used in computer security, particularly in exploiting buffer overflow vulnerabilities. Imagine you're trying to execute some malicious code, but traditional methods like injecting your own code might be blocked. ROP comes to the rescue by utilizing existing code snippets, known as "gadgets," already present in the program's memory.

Context: 
1. Stack buffer overflow cannot run malicious code if stack is not executable (just storing values). Reasons include:
	- **Data Execution Prevention (DEP):** DEP is a security feature that prevents the execution of code in certain regions of memory that should only contain data. If you try to inject code into a non-executable region, the operating system will raise an exception, thwarting your attempt.
    
	- **Address Space Layout Randomization (ASLR):** ASLR randomizes the memory addresses of key system components and executable files. This makes it challenging for attackers to predict the exact location of code or data they want to manipulate or exploit.
    
	- **Code Signing:** Some systems use code signing to ensure that only authorized and signed code is executed. If you inject unsigned code, it won't pass the verification process, and the system will prevent its execution.
    
	- **Stack Canaries:** Stack canaries are values placed on the stack before the return address. If an overflow occurs and the canary is altered, it indicates a potential attack, triggering the system to terminate the program.
	- Usually there won't be a backdoor in the user code, how to call exploits?
2.  Use existing libraries (e.g. `libc/system()`)
3. Return function is a communicator between the snacks
	1. The stack would be popped when the return function is called, moving the stack pointer up by 1 word
How to carry out?
- Find interesting code snippets
- Must end with return instruction

TO KNOW
actions (e.g. pop) that refer to the sp, on the contrary, move the esp up first, then enter the value in the new esp into the esp
- because esp is self referencing?

RET: go to the return address, which is the value of the esp, and then move up the esp
POP: push the value of esp into the desired register