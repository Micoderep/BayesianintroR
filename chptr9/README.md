Markov Chain Monte Carlo (MCMC):
It is a stocastic baysian method that allows the computation of a non gaussian posterior.

Good King Markov:
King Markov rules over an archipelago of 10 islands, islands 1-10 have populations which are multiples of island 1 (by their corresponding number). The islands are set adjacent to eachother forming a circle with island 10 next to 1. The problem to be solved is how to get Markov to visit all the islands such that his time spent on one island is proportional to its population and he can only move to adjacent islands.

The algorithm is:
Markov flips a coin every week, the result tells him whether to consider moving to island heads or island tails. He collects a number of shells reprenting the magnitude (relative to island 1) of the population of the island he is considering moving to, then he collects a number of stones corresponding to the current islands population. If there are more shells than stones he moves automatically to the next island, if there are less he subtracts the number of stones by shells then puts the remaining stones with the total number of shells in a bag and selects one, the item he pulls out determines his movement. This part of the coin flip favours moving to smaller adjacent islands (unless Markov is on island 10 considering island 1, with the probability of movement reducing for smaller island numbers) with a probability of staying on the current island.

The above algorithm in the limit will visit all islands with the weight of visits tied to the population of the different islands. The algorithm is known as the Metropolis Algorithm (MA) and the Markov explaintion of it is a special case. 

In statistics, the islands are the parameter values, the population sizes are the posterior probabilities at each parameter set, the weeks are samples taken from the joint posterior of the parameters in the model, you can move to any set of parameter values (with symmetric probabilities attributed to each pair of parameter sets).

Gibbs sampling is the metropolis algorithm but with an algorithm for more savvy parameter proposals using knowledge of conjugate pairs which have analytical solutions for an individual parameter. Makes it easier to handle parameters that have boundaries at 0, and allows for more efficient exploration of the posterior distribution (acquire good description of posterior with few samples atleast when compared to the MA).
