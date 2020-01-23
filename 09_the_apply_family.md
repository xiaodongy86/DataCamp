## Use lapply with a built-in R function

Before you go about solving the exercises below, have a look at the documentation of the **lapply()** function. The Usage section shows the following expression:
```r
lapply(X, FUN, ...)
```
To put it generally, lapply takes a vector or list X, and applies the function FUN to each of its members. If FUN requires additional arguments, you pass them after you've specified X and FUN (...). The output of lapply() is a list, the same length as X, where each element is the result of applying FUN on the corresponding element of X.

Now that you are truly brushing up on your data science skills, let's revisit some of the most relevant figures in data science history. We've compiled a vector of famous mathematicians/statisticians and the year they were born. Up to you to extract some information!
