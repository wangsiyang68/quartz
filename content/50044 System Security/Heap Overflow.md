## Structure
- Chunks
- Backward pointer and forward pointer
- Previous chunk size and current chunk size are stored in the preceding two words before the forward and backward pointers
	- Last three bits of the "previous size" is always set to 0 so that the size allocated is a multiple of 8
	- If previous chunk is not free, then it should be set to 0

## Exploit
- How does the free and combining chunks help to overwrite...what??