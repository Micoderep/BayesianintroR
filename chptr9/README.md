Markov Chain Monte Carlo (MCMC):
It is a stocastic baysian method that allows the computation of a non gaussian posterior.

Good King Markov:
King Markov rules over an archipelago of 10 islands, islands 1-10 have populations which are multiples of island 1 (by their corresponding number). The islands are set adjacent to eachother forming a circle with island 10 next to 1. The problem to be solved is how to get Markov to visit all the islands such that his time spent on one island is proportional to its population and he can only move to adjacent islands.

The algorithm is:
Markov flips a coin every week, the result tells him whether to consider moving to island heads or island tails. He collects a number of shells reprenting the magnitude (relative to island 1) of the population of the island he is considering moving to, then he collects a number of stones corresponding to the current islands population. If there are more shells than stones he moves automatically to the next island, if there are less he subtracts the number of stones by shells then puts the remaining stones with the total number of shells in a bag and selects one, the item he pulls out determines his movement. This part of the coin flip favours moving to smaller adjacent islands (unless Markov is on island 10 considering island 1, with the probability of movement reducing for smaller island numbers) with a probability of staying on the current island.

The above algorithm in the limit will visit all islands with the weight of visits tied to the population of the different islands. The algorithm is known as the Metropolis Algorithm (MA) and the Markov explaintion of it is a special case. 

In statistics, the islands are the parameter values, the population sizes are the posterior probabilities at each parameter set, the weeks are samples taken from the joint posterior of the parameters in the model, you can move to any set of parameter values (with symmetric probabilities attributed to each pair of parameter sets).

Gibbs sampling is the metropolis algorithm but with an algorithm for more savvy parameter proposals using knowledge of conjugate pairs which have analytical solutions for an individual parameter. Makes it easier to handle parameters that have boundaries at 0, and allows for more efficient exploration of the posterior distribution (acquire good description of posterior with few samples atleast when compared to the MA).

Gibbs sampling has limitations beyond not using conjugate priors, for higher and higher number of parameters the more inefficient the fitting. This is because there are higher probability density regions away from the highest probability value (mode), leading to more sampling of a thin high dimensional (high probability) shell rather than the whole distribution. (This was also explained as some parameters being highly correlated)

Hamiltonian Monte Carlo:
MA and gibbs sampling are highly random procedures which try out new parameter sets (proposals) and sees how good they are compared to the current values.
There is an algorithm similar to gibbs sampling but makes better choices so more of the posterior is sampled (from giving better proposals) for fewer points albeit at a higher computational cost, overtime though the HMC algorithm shows is dominance.

King Monty has the same problem as king Markov but he lives on a continuous valley (1dimensional confined to north and south direction) where the population is inversely proportional to the height of the valley which is like a parabola with the bottom at the center of the valley.
The solution is to shoot the king in his carriage in a random direction (here up or down) at a random momentum, as the vehicle goes up hill it speed is reduced and eventually turns around to go back down again, after a fixed period of time the vehicle is stopped and the king beholds his subjects before beginning the process again. The autocorrelation for this method is low in comparison to the MA and gibbs sampling as the initial location has little bearing on the next.

HMC is conducted like a particle simulation where a coordinate vector is sent on a random trajectory with a random motion.
HMC has a high acceptance of proposals, the ones that dont get accepted are those that dont conserve energ
U turn issue.
