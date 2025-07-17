This chapter is about overfitting, underfitting, and choosing between different predictive models.

(When we acquire data the uncertainty in something reduces, if we can define the uncertainty we can define "a baseline measure of how hard it is to predict, as well as how much improvement is possible". (The definition of information is the reduction of uncertainty when we learn an outcome) The uncertainty in a probability distribution is captured by the information entropy equation:

H(X) = -Σ p<sub>i</sub>(x) log p<sub>i</sub>(x)

This equation is described as the average log probability of an event.

The divergence (Kullback-Leibler/KL divergence):

H(X) = -Σ p(x)<sub>1</sub>(log p<sub>1</sub>(x)-log p<sub>2</sub>(x))

This finds the additional uncertainty induced by using the probabilities of one distribution (p(x)<sub>2</sub>) to describe another (i.e. the true data producing mechanism (model)) (p(x)<sub>1</sub>).

Since we do not know the true data generating process the KL divergence is useless, now here comes deviance which is the difference between two KL divergences of different models. This eliminates the term only in terms of p(x)<sub>1</sub>, leaving the difference between the cross-sections. The deviance tells us how much closer one model is compared to another in predicting the true data generation, however it does not tell us how close this is or whether the model correct.

S(q) = Σ log(q<sub>i</sub>)

This log probability score is "the gold standard way to compare the predictive accuracy of different models".
LOG-POINTWISE-PREDICTIVE-DENSITY (lppd). - Calculates the log probability score of a posterior distribution.

lppd(y,θ) = Σlog (1/S)Σp(y<sub>i</sub>|θ<sub>s</sub>)

You want to test the model on data that it is not trained on in order to see how it generalizes. This removes the false models with large numbers of predictive variables as they tend to always fit better to the training data (overfitting). In general the lppd score from the testing data should be worse than that calculated for the training as the model is better fit to the training data. The model with the best lppd for the testing data is the one that has the best predictive capabilities. You should always be careful with the data as any sample might not be representative and there might not be enough data for the best model to fit properly to.

Regularization is defined as using skeptical priors. This reduces the learning rate of the model reducing overfitting making models with more parameters perform better.

Predicting predictive accuracy:
Strategies for predicting out of sample accuracy of a model, Cross-validation, information criteria.

For cross-validation you divide the sample (data) into folds, the model is trained on all other folds except one which is then predicted, then average over "the score for each fold to get an estimate of out of sample accuracy". Leave out one CV is used frequently (where one data point is put into each fold). Computing CV can be quite computationally taxing so an approximation called Pareto-Smoothed Importance Sampling Cross-Validation is used. The PSIS uses the idea that observations that go against expectation more are more important than those that are already consistant with the models predictions.

Information criteria:

Using an equation it is possible to predict the out of sample deviance, this equation is called the Widely Applicable Information Criterion (WAIC).

p_WAIC = Σ[i=1 to n] Var_s( log p(y_i | θ^s) )
       = Σ[i=1 to n] (1/(S-1)) Σ[s=1 to S] ( log p(y_i | θ^s)
         - (1/S) Σ[s=1 to S] log p(y_i | θ^s) )^2
