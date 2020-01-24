## Use lapply with a built-in R function

Before you go about solving the exercises below, have a look at the documentation of the **lapply()** function. The Usage section shows the following expression:
```r
lapply(X, FUN, ...)
```
To put it generally, lapply takes a vector or list X, and applies the function FUN to each of its members. If FUN requires additional arguments, you pass them after you've specified X and FUN (...). The output of lapply() is a list, the same length as X, where each element is the result of applying FUN on the corresponding element of X.

Now that you are truly brushing up on your data science skills, let's revisit some of the most relevant figures in data science history. We've compiled a vector of famous mathematicians/statisticians and the year they were born. Up to you to extract some information!


Have a look at the **strsplit()** calls, that splits the strings in pioneers on the : sign. The result, split_math is a list of 4 character vectors: the first vector element represents the name, the second element the birth year.

Use **lapply()** to convert the character vectors in split_math to lowercase letters: apply tolower() on each of the elements in split_math. Assign the result, which is a list, to a new variable split_low.
Finally, inspect the contents of split_low with str().
```r
# The vector pioneers has already been created for you
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")

# Split names from birth year
split_math <- strsplit(pioneers, split = ":")

# Convert to lowercase strings: split_low
split_low <- lapply(split_math,tolower)

# Take a look at the structure of split_low
str(split_low)
```
## Use lapply with your own function

As Filip explained in the instructional video, you can use **lapply()** on your own functions as well. You just need to code a new function and make sure it is available in the workspace. After that, you can use the function inside **lapply()** just as you did with base R functions.

In the previous exercise you already used **lapply()** once to convert the information about your favorite pioneering statisticians to a list of vectors composed of two character strings. Let's write some code to select the names and the birth years separately.

The sample code already includes code that defined **select_first()**, that takes a vector as input and returns the first element of this vector.
```r
# Code from previous exercise:
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)

# Write function select_first()
select_first <- function(x) {
  x[1]
}

# Apply select_first() over split_low: names
names <- lapply(split_low, select_first)

# Write function select_second()
select_second <- function(x) {
  x[2]
}

# Apply select_second() over split_low: years
years <- lapply(split_low,select_second)
```
## lapply and anonymous functions

Writing your own functions and then using them inside lapply() is quite an accomplishment! But defining functions to use them only once is kind of overkill, isn't it? That's why you can use so-called anonymous functions in R.

Previously, you learned that functions in R are objects in their own right. This means that they aren't automatically bound to a name. When you create a function, you can use the assignment operator to give the function a name. It's perfectly possible, however, to not give the function a name. This is called an anonymous function:
```r
# Named function
triple <- function(x) { 3 * x }

# Anonymous function with same implementation
function(x) { 3 * x }

# Use anonymous function inside lapply()
lapply(list(1,2,3), function(x) { 3 * x })
split_low is defined for you.
```
```r
# split_low has been created for you
# Transform: use anonymous function inside lapply
names <- lapply(split_low, function(x) {x[1]})

# Transform: use anonymous function inside lapply
years <- lapply(split_low, function(x) {x[2]})
```

## Use lapply with additional arguments

In the video, the **triple()** function was transformed to the **multiply()** function to allow for a more generic approach. **lapply()** provides a way to handle functions that require more than one argument, such as the **multiply()** function:
```r
multiply <- function(x, factor) {
  x * factor
}
lapply(list(1,2,3), multiply, factor = 3)
```
On the right we've included a generic version of the select functions that you've coded earlier: **select_el()**. It takes a vector as its first argument, and an index as its second argument. It returns the vector's element at the specified index.

```r
# Definition of split_low
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)

# Generic select function
select_el <- function(x, index) {
  x[index]
}

# Use lapply() twice on split_low: names and years
names <- lapply(split_low,select_el,index = 1)
years <- lapply(split_low,select_el,index = 2)
```
## How to use sapply

You can use sapply() similar to how you used lapply(). The first argument of sapply() is the list or vector X over which you want to apply a function, FUN. Potential additional arguments to this function are specified afterwards (...):

sapply(X, FUN, ...)
In the next couple of exercises, you'll be working with the variable temp, that contains temperature measurements for 7 days. temp is a list of length 7, where each element is a vector of length 5, representing 5 measurements on a given day. This variable has already been defined in the workspace: type str(temp) to see its structure.
```r
# Use lapply() to find each day's minimum temperature
lapply(temp,min)

# Use sapply() to find each day's minimum temperature
sapply(temp,min)

# Use lapply() to find each day's maximum temperature
lapply(temp,max)

# Use sapply() to find each day's maximum temperature
sapply(temp,max)
```
## sapply with functions that return NULL

You already have some apply tricks under your sleeve, but you're surely hungry for some more, aren't you? In this exercise, you'll see how sapply() reacts when it is used to apply a function that returns NULL over a vector or a list.

A function print_info(), that takes a vector and prints the average of this vector, has already been created for you. It uses the cat() function.
```r
# Definition of print_info()
print_info <- function(x) {
  cat("The average temperature is", mean(x), "\n")
}

# Apply print_info() over temp using sapply()
sapply(temp,print_info)

# Apply print_info() over temp using lapply()
lapply(temp,print_info)
```
Notice here that, quite surprisingly, sapply() does not simplify the list of NULL's. That's because the 'vector-version' of a list of NULL's would simply be a NULL, which is no longer a vector with the same length as the input. 



