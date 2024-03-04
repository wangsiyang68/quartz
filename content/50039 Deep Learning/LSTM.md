6 New operations!!
## Components
1. Forget Gate
2. Input Gate
3. Output Gate
4. Hidden State
## New cell state
$$ c_t = f_t * c_{t-1} + i_t *tanh(W_c * x_t + U_c * h_{t-1} + b_c)$$
- first term: how much of history does model want to remember?
- second term: how much of new input does model want to remember?
- Memory is tracked in different places @ $c_t$ and $h_t$,
	- $c_t$ cell state is memory that retains long term information over time
	- $h_t$ captures the shorter term dependencies of the data

#dl