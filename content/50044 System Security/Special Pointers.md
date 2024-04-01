## Fat Pointers
copy from onenote

## Baggy Pointers
Understand that:
- It allocates some space in the memory
- It saves information about where this space is in the metadata table, which is located in main memory
	- The key is the slot number, the value is the size of the memory as the power of 2
	- Therefore, we save the information ($\log_2(\text{number of slots})$) with the **slot number**
- **Base slot number** of **the allocated memory** defined as the actual address in memory divided by the total memory allocated/total number of slots?
	- E.g. if 8 slots allocated, then we have base address / 256 ($2^8$) = base slot pointer
	- Or: shift the given **slot number** by 8 digits
		- Why?
- The base slot numbers of **following slots** will increase with slot size (i.e. slot size is 16 bytes, so next slot number is **base slot pointer** + $0x00000010$)
- **Slot size** defined as $2^n$, where n is a value given
- You can read stuff beyond the allocated size, up to the baggy range
- But you cannot write in the baggy range

3 special points about baggy pointers:
- The number of slots must be a power of 2
- There are excess baggy stuff on both sizes with size of (slot size)/2 (I call that the baggy range)
#ss