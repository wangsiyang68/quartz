## Fat Pointers
- A regular pointer contains just the address
- A fat pointer goes further by storing the metadata together with the real pointer, such as the start and the end of the memory block
- Implemented in Java and Go

## Baggy Pointers
Great concept, but not implemented in C.
It allows for bounds checking without much time overhead or space storage. Just that have some constraints on space storage
Also note that this is backwards compatible, since metadata is not stored with the pointer, but elsewhere in a metadata table

**Characteristics**  
3 special points about baggy pointers:
- The number of slots must be a power of $2^b$
	- b is usually given
	- Therefore, here are the valid memory block sizes: $2^4$, $2^5 \ldots 2^{(b+x)}$ bytes 
- Allocate each memory block to the the $2^{(b+x)}$ boundary
	- This allows us to quickly get to the base address of the memory block
- Allow slack for out of bound
	- **If out of bound distance < slotsize/2 on EITHER SIDE, allow read, but not write**. So you can read stuff beyond the allocated size, up to the baggy range, but you cannot write in the baggy range
		- For example: 
			- line 2 in the below code is okay because the allocated slot is of 256 bytes, and the result pointer is **read** 44 bytes past the end, which is less than the slot_size/2 = 128 (assuming here that slot_size = 256)
			- However, the fifth line will fail, because it is an out-of bounds **write**
		```
		char *q = malloc(256)
		char *r = q + 300
		char *s = r - 100
		char a = *s
		*r = a
		```

**Setup**  
- Slot size is defined as $2^{(b)}$ bytes
- There is a metatable elsewhere in the memory
	- The key is the slot number, the value is the size of the memory as the power of 2
	- Therefore, we save the information ($\log_2(\text{number of slots})$) as the value of the **slot number**

Example Metatable

| Slot Number | power |
| ----------- | ----- |
| 12345       | 5     |
| 12344       | 5     |
| 12343       | 5     |
| 12342       | 5     |
| 12341       | 5     |
| 12340       | 5     |

**How to check if pointer is within allocated memory block?**  
Given a valid pointer p in an allocated memory block, and $2^b$ slot size, where b = 4 
- Find the slot number by 
	- Dividing it with $2^4$
	- **Address in bits**, shift right by b **bits**
		- so if b = 4, remove the last digit (since in hex address, each digit would take up 4 bits)
	- Repeat this process in reverse to go from address from slot number
- Find the slot size 
	- `metatable[slot_number]`
- Find size of memory block p is in
	- `1 << metatable[slot_number]`
	- Same thing as raising the value in metatable to power of 2
- Find p's base address
	- `p & ~(size-1)`
	- size -1 will give something like 255, which is 0x000000FF
	- Not size-1 will give 0xFFFFFF00
	- The base slot numbers of **following slots** will increase with slot size (i.e. slot size is 16 bytes, so next slot number is **base slot pointer** + $0x00000010$)
- Find p's memory block boundary
	- base address + size
- Check new pointer p' if in bounds:
	- check if `p' >= base` and
	- `p' < base + size`
	- Or a one liner: `p^p' >> table[p>>4] == 0`. If return 0, valid. If return anything else, not valid


#ss