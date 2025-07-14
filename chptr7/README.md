This chapter is about overfitting, underfitting, and choosing between different predictive models.

How accurate a model is, is related to how uncertain the posterior is. The uncertainty in a probability distribution is captured by the information entropy equation:
H(X) = -Σ p(x) log₂ p(x)
This equation is described as the average log probability.

H(X) = -Σ p(x)<sub>1</sub>(log₂p<sub>1</sub>(x)-log₂p<sub>2</sub>(x))
