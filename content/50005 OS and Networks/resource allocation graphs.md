# Resource Allocation Graph

Used to identify a deadlock
- No cycle = No deadlock
- Got at least one cycle:
	- All resources have exactly one instance
	- All resources in cycle have only one instance
	- Use common sense to cycle ur way through the graph. Check if theres anyone that can complete with time (i.e. not waiting for anyone to give up resource)

if requesting lock, arrow head must **stop outside** the box
if own lock, arrow should originate from the **circle/dot** inside the box

Similar concept: Graph traversal algorithms
#os