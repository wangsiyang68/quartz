- Idea 1: One way of doing so is via **Restricted Instructions**
	- Safe, dangerous and hard to make safe assembly instructions
	- To rewrite:
		- To avoid weird jumps into a middle and creating wrong instructions
			- Align to a block (e.g. 32 bytes)
			- Assuming that safe software only goes to each of the start of the 32 bit block, not at the middle
				- e.g. and 0x...e0 `*eax`
		- To avoid jumps outside of the application, use a mask 
			- if 256 B, then set the 8th bit and beyond of a mask to be 0
- Idea 2: Controlled Interaction
	- Like using the interrupt table

Web apps
- Start with base 0
- Length of 256 MB?

- Segmentation
	- Segment selector > descriptor table > main memory
	- `>` : points to
	- Segment selector is an index into the Local Descriptor Table (LDT)
#ss