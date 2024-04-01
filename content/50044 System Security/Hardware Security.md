Detect if cannot prevent
TPM = Trusted Platform Module

Minimize TCB and isolation of secure apps
TCG = Trusted Computing Group (More of a commercial thing, Intel and ARM are part of it)

Verify recursively, until there is only hardware left to trust, so that you don't have to trust the OS

Core Root of Trust Management (CRTM) 
- Tamper Resistant
- Computes $m_{BIOS}$ 
- Append = hash(last hash value in PCR + existing hash)
	- `+` as in concatenate

PCR = Platform Configuration Register
- Where you store the hashes calculated by the BIOS/Boot Loader on the downstream Boot Loader
- When the OS is booted for the first time, the hashes of the BIOS and Boot Loader is stored inside the PCR table.

TPM advantages
- Cheap
- Introduced hardware security to mainstream

Disadvantages
- Slow
- Does not guarantee it is safe, just not modified
- Not flexible for OS updates

Bootloader, BIOS, hardware = Part of Ring -1 in the [[Ring Diagram]]

![[Pasted image 20240325144043.png]]
**ARM TrustZone**
- Idea: Minimize TCB and isolate secure apps
	- Isolate the secure memory part from the non-secure parts (physically in the hardware
	- Then those who have the correct non secure (NS) bit (0) will be able to access the secure part
	- Secure Transition
	- There are other ways to access other non secure part by secure parts, by using TPM (in the case of, lets say secure app need more memory)

![[Pasted image 20240325144101.png]]
**Intel SGX**
- Note that trusted OS not needed
- Memory is also encrypted, unlike ARM TrustZone in the plaintext
- TCB = SGX Micro Code, Memory Encryption Engine


- PRM = Processor reserved Memory
- EPC = Enclave Page Cache
Normal process goes to normal cache
Enclave process goes to EPC via the EADD instruction

Only Trusted set of firmware can work with firmware
During multithreading, cpu should clean up the cache, or else data will be leaked
#ss
