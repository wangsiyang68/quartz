## Key Idea
![[Pasted image 20230524235818.png]]

## What is it?
Coalescing is the act of accessing the data from some global memory in an efficient manner. Since data is not grabbed one piece at a time (more like a set/word/cache line at a time), if the accesses made by multiple threads in the same warp are accessing the same cache line, then it reduces the amount of calls to the global memory that you need to make.

## How to visualize it?
Need to think in terms of multiple threads running together at a certain time, and them advancing together at the next time. 

Below is coalesced because although each thread goes through items in a column, at say time t=0, each thread is accessing items on the yellow row, which belong on the same cache line  
![[Pasted image 20230615114120.png]]

## How to implement it?
Sometimes you need to load stuff that are in a row into the Shared Memory. If each thread is responsible for loading each row, then the memory loading will not be coalesced. So each thread should read each row at a time by having them be responsible for loading each column in the tile.    

Conversely, if you are loading stuff in a column into the shared Memory, then each thread should take care of each column.  
- For example, in terms of matrix multiplication, the columns of a matrix are accessed by the col value, which is a multiple of the tile width added with the tx value. Since tx value is not multiplied, each thread acc 
#pp