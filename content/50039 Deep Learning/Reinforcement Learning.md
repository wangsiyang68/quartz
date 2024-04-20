## Context
- There are situations where we cannot have a dataset, or good enough one to complete the task
	- Examples: Weiqi -- existing games are not good as training data because we are not the best at the game

## Definitions
- Policy
	- The function which returns an action amongst possible actions
- Reward function
	- Find the best policy that maximises the return
- Reward hypothesis
- Exploation
	- Phase where the model tries out all the possible actions, even if some of them are sub-optimal, to collect information
	- Too much exploration however would lead to wasted time, too little may result in making a choice of the wrong type
- Agent
	- Renamed from the word model, same meaning
- State
	- Current understanding of the model
- Regret
	- Cost of knowledge
		- Amount of candies we have to waste to obtain information about the hidden probabilities
	- Cannot be zero without perfect knowledge
## Strategies
The first problem that is often discussed for RL is the **multi-armed bandit problem**
1. Naive random strategy
2. Deterministic strategy
3. Perfect Knowledge Strategy
	1. Provides the upper bound performance 
4. e-first strategy
	1. For the first few coins, gather information (exploration)
	2. Then for the remaining coins, act on the information to select the best machine (exploitation)
	3. Note that e is a hyperparameter. If e is too large, there will be high regret during exploration phase
	4. If not, there will be high regret during the exploitation phase
	5. **Variant: with softmax exploration**
		1. Phase 1: Exploration is optimized by instead of using a standardized constant probability of selecting a machine, using a softmax distribution 
	6. **Variant: e-greedy strategy**
		1. Change the value e from a constant to one which decreases over time. 
		2. Similar to the LR scheduling
5. Upper Confidence Bound Strategy

A second problem that is often discussed is the **maze problem**
- given a maze and no information on the existing maze, map out a maze path 
	- **State** = position on the board
	- **Action** = move up/down/left/right
	- **Reward** = set to -1 per legal move
- **Value function V** (happens alot, very important!) which tells user the estimation of the current and future rewards 
	- It also takes in a parameter to give an importance to future rewards

**State action function Q**
- used to quantify the goodness of taking an action at, in state st at time t, according to our policy. Sum up the immediate and expected reward in the future
- immediate reward = Rt 
- expected reward, what we will get in the future 

**Bellman Principle of optimality**
- Just means that you can utilise the functions for Q and V to calculate each other
- The policy can be derived from Q
- **For a simple problem like the maze problem**, given that there is a finite set of actions, maintain a table (Q-table) and update it with the results after playing it 
	- After each round of exploring the maze, we have a finite history of actions, states and rewards.
- We then update the table with a function that is similar to gradient descent
	- Old value + learning rate * reward + discount factor * estimate of optimal future value*
	- Also known as Q-learning
	- learning rate lower = more focus on the short term reward
	- 

## Further Problems:
Multi-armed bandit problem is a stationary problem, where the hidden probabilities of each machine do not change
- Another variant is such that the machine's probability change over time
Maze Problem, but without all of the possible states to write inside of the Q-table. 
- There are too many states to calculate. How?
Evenutally, in deep Q-learning, you cannot have their Q functions calculated efficiently
- I.e. how do you tell the goodness or badness of taking an action at a certain state, especially at the starting phase where its hard to tell?
Actor-critic models
- similar to the GANs
SARSA
- For use in turn based games like Go
#dl
