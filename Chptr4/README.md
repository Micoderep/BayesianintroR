Here I am using splines to model some MET data to see how the temperature varies over time.

Using B-splines, these are simple functions that exist in a limited part of the parameter space but link up to contribute to an overall function. The edges of these functions are called "knots", atleast two functions overlap with some turning "on" and the others turning "off" as knots are reached and passed. 

Using the command: read.table("C:/Users/miles/Desktop/oxjune.csv"), I could read a txt file which I have stored the June temperatures of Oxford in from the years 1853 to 2024 into a data frame in R. Then I used precis(dataframe) to make sure that I had uploaded the data correctly. (precis() is in library(rethinking))

> d2 <- d[complete.cases(d$V2), ]
> 
> num_knots <- 15
> 
> knot_list <- quantile(d2$V1, probs=seq(0,1,length.out=num_knots))

The above code creates a new dataframe d2 and puts complete data into it, then knots are defined with more knots placed where more data is.

> library(splines)
>
> B <- bs(d2$V1,knots=knot_list[-c(1,num_knots)],degree=3,intercept=TRUE)

This code creates a matrix where each row is a year, and each column is a basis function. degree = 3 means that at any point along the x axis there are 4 basis functions being added together. (The -c(1,num_knots) excludes the first and last knot from the list), (I think that this bs function automatically makes cubic splines as default).

> m4.7 <- quap(alist(D~dnorm(mu,sigma),mu <- a + B %*% w, a ~ dnorm(100,10), w ~ dnorm(0,10), sigma ~ dexp(1)), data=list(D = d2$V2 ,B=B), start=list( w=rep( 0 , ncol(B) ) ) )

This code fits the model to the data with the quadratic approximation method, using an exponential distribution as a prior for sigma which is beneficial as sigma is always positive and we have an idea that smaller values are more likely than larger ones.

> mu <- link(m4.7)
> 
> mu_PI <- apply(mu,2,PI,0.97)
>
> mu.mean <- apply(mu,2,mean)

link function takes the quadratic approximation: m4.7, samples from the posterior distribution and calculates mu for each case in the data (in this case each data is each year and corresponding temperature) and then samples from that posterior distribution. (This is a distribution from the sheer number of points sampled from the inital posterior)
Resulting in a matrix containing a series temperature values for each year due to the sampling of the posterior of different parameters. The next lines summarise the distribution, "Read apply(mu,2,mean) as compute the mean of each column (dimension 2) of the matrix mu.".

> plot(d2$V1, d2$V2, col=col.alpha(rangi2,0.3), pch=16, xlab="Year", ylab="Tmax (degC)", mtext("Max temperature in June at Oxford"))
> 
> shade(mu_PI,d2$V1,col=col.alpha("black",0.5))
> 
> lines(d2$V1,mu.mean)

![ojtvt](https://github.com/user-attachments/assets/549f0101-bddf-4360-863c-b442e9663c8d)


This image shows the mean spline and the shaded 97% of the posterior weight values. The graph shows that the overall Oxford temperature increases from about the 1990s onwards setting new records when considering the previous data.
