Here are the commands to set up the workspace for doing the Bayesian Statistics:

es("rstan", repos = c('https://stan-dev.r-universe.dev', getOption("repos")))

install.packages(c("coda","mvtnorm","devtools","dagitty"))

install.packages("Rcpp", dependencies = TRUE)

install.packages("usethis")

library(usethis)

library(devtools)

install.packages("cmdstanr")

av <- available.packages(filters=list())

av[av[, "Package"] == cmdstanr, ]

av[av[, "Package"] == "cmdstanr", ]

remotes::install_github("stan-dev/cmdstanr")

devtools::install_github("rmcelreath/rethinking")

q()
