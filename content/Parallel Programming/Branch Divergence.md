To avoid branch divergence, schedule all the threads such that an entire warp takes the same branch. 

An example is by dividing the threadID.x with the warp size. Then when you mod the result by 2, each thread in the warp will run the same branch 
#pp 