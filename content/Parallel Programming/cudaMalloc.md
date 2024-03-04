**Purpose**: To allocate the memory in GPU before the program copies the data over to it. Can't copy any data without having allocated memory in the first place

**Funfact**: GPU data space is not actually utilized until [[cudaMemcpy]] has been called! This is somewhat similar to the C Malloc function, which allocates the data without first initializing it (meaning allocated data is not set to 0, is whatever state it was in at that point)

#pp

