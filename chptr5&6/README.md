Many variables:

"Every pair of variables has a statistically discernable non-zero correlation.". Correlations however do not translate to causation, thus it is necessary to find ways to "distinguish mere association from evidence of causation".

Directed Acyclic Graph (DAG), unlike a statisical model a DAG will give you an idea of what happens when you change a variable.

![Untitled (1)](https://github.com/user-attachments/assets/7abd3a52-c24f-4959-ae92-7cbbc3eaf36b)

The left image implies that all the variables depend on A and are all linked in someway. In the right it suggests that D is not dependent on M conditional on A. You can do an experiment to distinguish between these two DAG's by checking if D ⫫ M|A is true or not. Seeing correlations/associations is not enough because variables dependent on one can effect each other due to their dependence on said variable. "Knowing a cause in statistics means being able to correctly predict the consequences of an intervention."

Multi-variable regression can help reveal spurious correlations and reveal important correlations hidden (masked) by unknown correlations with other variables.
Conditional independencies are statements for "which variables should be associated with one another (or not) in the data", and "which variables become dis-asociated when we condition on someother set of variables".

Multiple regression addresses the question: "Is there any additional value in knowing a variable, once I already know all of the other predictor variables?".

Interpretive plots: Posterior prediction plots, and Counterfactual plots.
Former uses model predictions against the corresponding data used to make the predictions. This shows how well a model fits to the data. The latter (an inferential plot) displays the causal implications of the model. Basically you simulate results that may not even occur in reality, your oen sequence of inputs for a particular input variable. This also allows you to test different DAG's as variables not independent can be made independent.

counterfactual for this book "indicates some computation that makes use of the structural causal model, going beyond the posterior distribution".

Multiple regression can reveal relationships between multiple predictor variables that might not be apparent on their own. For example if you increase a variable but do not account for a variable that has an opposite effect that is also varied, then the effect of the variable that you are measuring wont be as pronounced.

Catagorical variables are, variables that incorporate discreate things into our model, like whether or not someone has a particular ethinicity. You can do this by adding a term to your calculation of the mean that has a parameter that you infer with the catagorical variable being 1 or 0. The second method is to use what is called an "index variable" which is basically a list of (the same) prior distributions roled into one, but which are selected depending on the value of the catagorical variable.

Can calculate the difference between catagorical distributions, called a contrast (by subtracting simultated values using the model and posterior distributions).

Chapter 6 stuff:

The act of adding a predictor variable to a model induces statistical selection.

Note: adding predictors to a model automatically conditions on them when fitting the model. The issues in chapter 6 tell you when to not add a variable into a model in order to "arrive at valid inferences".



