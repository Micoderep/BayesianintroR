Here I am using splines to model some MET data to see how the temperature varies over time.

Using the command: read.table("C:/Users/miles/Desktop/oxjune.csv"), I could read a txt file which I have stored the June temperatures of Oxford in from the years 1853 to 1913 into a data frame in R. Then I used precis(dataframe) to make sure that I had uploaded the data correctly. (precis() is in library(rethinking))

> d2 <- d[complete.cases(d$V2), ]
> 
> num_knots <- 15
> 
> knot_list <- quantile(d2$V1, probs=seq(0,1,length.out=num_knots))
> 
> B <- bs(d2$V1,knots=knot_list[-c(1,num_knots)],degree=3,intercept=TRUE)
> 
> m4.7 <- quap(alist(D~dnorm(mu,sigma),mu <- a + B %*% w, a ~ dnorm(100,10), w ~ dnorm(0,10), sigma ~ dexp(1)), data=list(D = d2$V2 ,B=B), start=list( w=rep( 0 , ncol(B) ) ) )
> 
> mu <- link(m4.7)
> 
> mu_PI <- apply(mu,2,PI,0.97)
> 
> plot(d2$V1, d2$V2, col=col.alpha(rangi2,0.3), pch=16)
> 
> shade(mu_PI,d2$V1,col=col.alpha("black",0.5))
> 
> mu.mean <- apply(mu,2,mean)
> 
> lines(d2$V1,mu.mean)

![ojtvt](https://github.com/user-attachments/assets/549f0101-bddf-4360-863c-b442e9663c8d)


This images shows the mean spline and the shaded 97% of the posterior weight values. The graph shows that the Oxford temperature over these years fluctuates quite a bit with not a clear trend other than the temperature fluctuations becoming weaker and perhaps less frequent.
