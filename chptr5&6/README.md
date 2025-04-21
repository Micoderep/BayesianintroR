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

Multicollinearity: When two predictor variables are highly correlated with eachother, they give similar information which translates to many combinations of these predictor variables predicting a particular bit of data, this inflates the uncertainty of the posterior of these variables. The model will predict just fine, however these parameters will never become more certain. Apparently just dropping highly correlated pairs of variables is a mistake, it is the "conditional associations - not correlations - that matter".

A parameter being non-identifyable means that the structure of the data and mode do not make it possible to estimate the uncertainty.

Post-treatment bias: when you include in a model priors where a chosen predictor variable depends completely on another when causing a variable of interest, because regressions ask the question what is the value of knowing a variable when I know the others, knowing a variable that depends on another in the model provides no new information to the model. This moves the posterior of the independent variable to zero.

Collider bias: A collider is a variable that depends on at least two other variables that are independent of eachother. If you model one of these causing variables with both the collider and another causation variable non physical statistical associations will be caused leading to incorrect inference. These causing variables should be independent so if you regress one on the other no association should exist. A more indepth reason would be that the causation variable considers the collider variable, in the marriage, age and happiness example given in the book, including marriage (the collider variable) in the regression of happiness vs age leads to a statistical association as because as time goes on the mean happiness decreases as more people get married in the groups of the nonmarried and the married if marriage was not considered then the mean happiness would be constant as the data was generated to be.

Confounding: "any context in which the association between an outcome Y and a predictor of interest X is not the same as it would be, if we had experimentally determined the values of X". This leads to the fact that we can detact a variable and make it independent in a DAG by changing it manually.

There are four different DAG structures outlined in the book; the fork, the pipe, the collider, and the decendent.

The fork: a variable causing two other variables.

The pipe: a variable which causes a variable which causes another that is independent to the first variable.

The collider: two causing variables effect the same variable.

The decendent: it is "a variable influenced by another variable. Conditioning on a decendent partially conditions on its parent". In the book the parent is part of a collider, which means that the collider opens up and lets some information through.

When deciding what variables to include in a regression so that you do not get any non causal associations you need to find the path that connects a variable of interest to the outcome variables. Since these paths contain causal information you need to make sure they are open so condition on the right variables. There are other paths called backdoor which transfers statistical association information if left open so you must condition or remove variables from a model accordingly as before.

With the data, your DAG and no physical model/theory you can use conditional independencies to check if the DAG that is being used is correct.


