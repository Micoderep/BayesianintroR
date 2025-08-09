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
HMC has a high acceptance of proposals, the ones that dont get accepted are those that dont conserve energy.
There are Leap frog steps and step size, determining the number of steps between proposals, and step size's meaning is intuitively clear. If the posterior is symmetrical then HMC can become inefficient due to bad choices of leap frog steps and step size, if poorly chosen then the path can wrap around and be likely to end up near the starting parameter set leading to a reduction in the exploration of the posterior and more correlation between proposals. (known as the U-turn problem) can be solved by a warm up phase in which the algorithm chooses better values of these parameters from testing.

N_eff is a crude estimate of the numbers of independent samples you manage to get.
Rhat_4 is an indicator of convergence of the Markov chains to the target distribution (should approach 1).

If Markov chain is defined correctly it is guaranteed to converge to the target/posterior distribution.
HMC Markov chains have a warmup period initially where the step size and step number are tuned to efficiently sample the region.

Trace plot is a graph with the value of a sample of a particular parameter vs the sample number. If these plots have good stationarity, mixing, and convergence then the Markov chain is considered to be healthy. Stationarity is that the mean of the variation in the parameter values over the samples stays relatively constant. Good mixing means that the chain rapidly explores the full region. Convergence refers to multiple chains sticking to the same region of high probability.

Trace Rank or Trank plot assigns an integer to different markov chain sample values (for 1 parameter), with 1 being assigned to the smallest value. Then the samples with the same integer/value are put into a box making a histogram looking the frequency of different values. These histograms from different chains are then plotted onto the same graph with different colours distinguishing them. If the chains are exploring the same space efficiently then the histograms should be similar to one another largely overlapping with neither histogram spending too much time above another.

N_eff: Markov Chains are typically autocorrelated so the samples gleaned from it are not completly independent, which is what we want, this autocorrelation reduces the exploration effiency of the chain in the posterior distribution. The effective number of samples is an estimate of the independent number of samples from the posterior distribution, autocorrelation reduces this value. One consequence of the definition is that N_eff can be larger than the number of samples from a chain provided that sequential samples are anti-correlated in some way.

Wild chains, with very little data and flat priors the chains can easily take on unreasonable values and not explore the posterior region quickly (Divergent transitions: These warnings arise when the numerical simulation that HMC uses is inaccurate).

Non-identifiable parameters problem from chapter 6 where you have highly correlated predictors and so you end up inferring the combination of them in the model. This problem is exaserbated by using weak/flat priors as there are many possible parameter combinations with high probability.

Flat prior sampling takes longer than weak.
