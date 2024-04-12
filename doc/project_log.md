## Problem 1: In the simulated example, density of GF-MH50 chain was too different from target density 1/2(N(4,1)+N(-2,1))
. Checked MH function with just RWMH -> no bugs
. Checked how Gibbs flow map transform samples from prior -> samples are moved to the 2 peaks 4 and -2 but overall density is still to different from target -> problem with the Gibbs flow function
. Doublechecked formulas in code -> no bugs
. Plotted transport map T1 as a function -> discovered severe numerical errors in certain parts of the map 
-> plotted T1 for the simpler target N(10,1) -> less severe errors -> distribution dependent problem
-> increased grid size M -> less severe error -> problem solved! (with the draw back of more running time)

## Problem 2: For real data, GF-MH chain did not move for very long
. Initial model from book maybe too complex? 
-> reduce to simpler model with only months of service as independent variable -> same problem occurred 
-> checked acceptance probability at each iterations -> many acceptance probabilities returned NA due to the transformed proposal being NA 
-> increased grid size like before -> problem still occurred in some runs when there is a jump to a region with low likelihood -> run GF chain with 1000 iterations instead of 10000 to reduce the time of having to rerun due to the NA problem
-> problem somewhat fixed but at the cost of much greater computation time
