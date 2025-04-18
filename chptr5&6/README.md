Many variables:

"Every pair of variables has a statistically discernable non-zero correlation.". Correlations however do not translate to causation, thus it is necessary to find ways to "distinguish mere association from evidence of causation".

Directed Acyclic Graph (DAG), unlike a statisical model a DAG will give you an idea of what happens when you change a variable.

![Untitled (1)](https://github.com/user-attachments/assets/7abd3a52-c24f-4959-ae92-7cbbc3eaf36b)

The left image implies that all the variables depend on A and are all linked in someway. In the right it suggests that D is not dependent on M conditional on A. You can do an experiment to distinguish between these two DAG's by checking if D ⫫ M|A is true or not. Seeing correlations/associations is not enough because variables dependent on one can effect each other due to their dependence on said variable. "Knowing a cause in statistics means being able to correctly predict the consequences of an intervention."

Multi-variable regression can help reveal spurious correlations and reveal important correlations hidden (masked) by unknown correlations with other variables.
Conditional independencies are statements for "which variables should be associated with one another (or not) in the data", and "which variables become dis-asociated when we condition on someother set of variables".

Multiple regression addresses the question: "Is there any additional value in knowing a variable, once I already know all of the other predictor variables?".

Interpretive plots: Posterior prediction plots, and Counterfactual plots.
Former uses model predictions against the corresponding data used to make the predictions. This shows how well a model fits to the data. The latter

counterfactual for this book "indicates some computation that makes use of the structural causal model, going beyond the posterior distribution".
