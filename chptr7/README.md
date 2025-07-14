This chapter is about overfitting, underfitting, and choosing between different predictive models.

(When we acquire data the uncertainty in something reduces, if we can define the uncertainty we can define "a baseline measure of how hard it is to predict, as well as how much improvement is possible". (The definition of information is the reduction of uncertainty when we learn an outcome) The uncertainty in a probability distribution is captured by the information entropy equation:

H(X) = -Σ p<sub>i</sub>(x) log p<sub>i</sub>(x)

This equation is described as the average log probability of an event.

The divergence (Kullback-Leibler/KL divergence):

H(X) = -Σ p(x)<sub>1</sub>(log₂p<sub>1</sub>(x)-log₂p<sub>2</sub>(x))

This finds the additional uncertainty induced by using the probabilities of one distribution (p(x)<sub>2</sub>) to describe another (i.e. the true data producing mechanism (model)) (p(x)<sub>1</sub>).

Since we do not know the true data generating process the KL divergence is useless, now here comes deviance which is the difference between two KL divergences of different models. This eliminates the term only in terms of p(x)<sub>1</sub>, leaving the difference between the cross-sections. The deviance tells us how much closer one model is compared to another in predicting the true data generation, however it does not tell us how close this is or whether the model correct.

S(q) = Σ log(q<sub>i</sub>)


