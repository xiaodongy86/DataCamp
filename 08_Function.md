## Function documentation

Before even thinking of using an R function, you should clarify which arguments it expects. All the relevant details such as a description, usage, and arguments can be found in the documentation. To consult the documentation on the **sample()** function, for example, you can use one of following R commands:
```r
help(sample)
?sample
```
If you execute these commands in the console of the DataCamp interface, you'll be redirected to www.rdocumentation.org.

A quick hack to see the arguments of the **sample()** function is the **args()** function. Try it out in the console:
```r
args(sample)
```
In the next exercises, you'll be learning how to use the **mean()** function with increasing complexity. The first thing you'll have to do is get acquainted with the **mean()** function.


## Use a function

The documentation on the **mean()** function gives us quite some information:

The **mean()** function computes the arithmetic mean.
The most general method takes multiple arguments: x and ....
The x argument should be a vector containing numeric, logical or time-related information.
Remember that R can match arguments both by position and by name. Can you still remember the difference? You'll find out in this exercise!

Once more, you'll be working with the view counts of your social network profiles for the past 7 days. These are stored in the linkedin and facebook vectors and have already been defined in the editor on the right.

## Use a function (2)

Check the documentation on the **mean()** function again:
```
?mean
```
The Usage section of the documentation includes two versions of the mean() function. The first usage,
```
mean(x, ...)
```
is the most general usage of the mean function. The 'Default S3 method', however, is:
```r
mean(x, trim = 0, na.rm = FALSE, ...)
```
**The ... is called the ellipsis. It is a way for R to pass arguments along without the function having to name them explicitly. The ellipsis will be treated in more detail in future courses.**

For the remainder of this exercise, just work with the second usage of the mean function. Notice that both trim and na.rm have default values. This makes them **optional arguments**.
```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)

# Calculate the mean of the sum
avg_sum <- mean(linkedin +facebook)

# Calculate the trimmed mean of the sum
avg_sum_trimmed <- mean(linkedin +facebook, trim =0.2)

# Inspect both new variables
print(avg_sum)
print(avg_sum_trimmed)
```
## Use a function (3)

In the video, Filip guided you through the example of specifying arguments of the sd() function. The sd() function has an optional argument, na.rm that specified whether or not to remove missing values from the input vector before calculating the standard deviation.

If you've had a good look at the documentation, you'll know by now that the mean() function also has this argument, na.rm, and it does the exact same thing. By default, it is set to FALSE, as the Usage of the default S3 method shows:
```r
mean(x, trim = 0, na.rm = FALSE, ...)
```
Let's see what happens if your vectors linkedin and facebook contain missing values (NA).
```R
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, NA, 17, 14)
facebook <- c(17, NA, 5, 16, 8, 13, 14)

# Basic average of linkedin
mean(linkedin)

# Advanced average of linkedin
mean(linkedin, na.rm = T)
```
## Functions inside functions

You already know that R functions return objects that you can then use somewhere else. This makes it easy to use functions inside functions, as you've seen before:
```r
speed <- 31
print(paste("Your speed is", speed))
```
Notice that both the print() and paste() functions use the ellipsis - ... - as an argument. Can you figure out how they're used?
```r
#Use abs() on linkedin - facebook to get the absolute differences between the daily Linkedin and Facebook profile views. Place the call to #abs() inside mean() to calculate the Mean Absolute Deviation. In the mean() call, make sure to specify na.rm to treat missing values #correctly!
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, NA, 17, 14)
facebook <- c(17, NA, 5, 16, 8, 13, 14)

# Calculate the mean absolute deviation
mean(abs(linkedin - facebook), na.rm = T)
```

## Write your own function

Wow, things are getting serious... you're about to write your own function! Before you have a go at it, have a look at the following function template:
```r
my_fun <- function(arg1, arg2) {
  body
}
```
Notice that this recipe uses the assignment operator (<-) just as if you were assigning a vector to a variable for example. This is not a coincidence. Creating a function in R basically is the assignment of a function object to a variable! In the recipe above, you're creating a new R variable my_fun, that becomes available in the workspace as soon as you execute the definition. From then on, you can use the my_fun as a function.
```r
#Create a function pow_two(): it takes one argument and returns that number squared (that number times itself).
#Call this newly defined function with 12 as input.
#Next, create a function sum_abs(), that takes two arguments and returns the sum of the absolute values of both arguments.
#Finally, call the function sum_abs() with arguments -2 and 3 afterwards.

# Create a function pow_two()
pow_two <- function(x) {
  y=x*x
  print(y)
}
# Use the function
pow_two(12)

# Create a function sum_abs()
sum_abs <- function(x,y){
  print(sum(abs(x),abs(y)))
}
# Use the function
sum_abs(-2,3)
```
## Write your own function (2)

There are situations in which your function does not require an input. Let's say you want to write a function that gives us the random outcome of throwing a fair die:
```r
throw_die <- function() {
  number <- sample(1:6, size = 1)
  number
}

throw_die()
```
Up to you to code a function that doesn't take any arguments!
```r
Define a function, hello(). It prints out "Hi there!" and returns TRUE. It has no arguments.
Call the function hello(), without specifying arguments of course.

# Define the function hello()
hello <- function() {
  print("Hi there!")
  1==1
}
# Call the function hello()
hello()
```
## Write your own function (3)

Do you still remember the difference between an argument with and without default values? Have another look at the sd() function by typing ?sd in the console. The usage section shows the following information:
```r
sd(x, na.rm = FALSE)
```
This tells us that x has to be defined for the sd() function to be called correctly, however, na.rm already has a default value. Not specifying this argument won't cause an error.

You can define default argument values in your own R functions as well. You can use the following recipe to do so:
```r
my_fun <- function(arg1, arg2 = val2) {
  body
}
```
The editor on the right already includes an extended version of the pow_two() function from before. Can you finish it?
```r
#Add an optional argument, named print_info, that is TRUE by default.
#Wrap an if construct around the print() function: this function should only be executed if print_info is TRUE.
#Feel free to experiment with the pow_two() function you've just coded.
# Finish the pow_two() function
pow_two <- function(x, print_info = TRUE) {
  y <- x ^ 2
  if (print_info == TRUE){
  print(paste(x, "to the power two equals", y))
  }
  return(y)
}
pow_two(2,print_info =F)
pow_two(2)
```

## Function scoping

An issue that Filip did not discuss in the video is function scoping. It implies that variables that are defined inside a function are not accessible outside that function. Try running the following code and see if you understand the results:
```r
pow_two <- function(x) {
  y <- x ^ 2
  return(y)
}
pow_two(4)
y
x
```
y was defined inside the pow_two() function and therefore it is not accessible outside of that function. This is also true for the function's arguments of course - x in this case.

Which statement is correct about the following chunk of code? The function two_dice() is already available in the workspace.
```r
two_dice <- function() {
  possibilities <- 1:6
  dice1 <- sample(possibilities, size = 1)
  dice2 <- sample(possibilities, size = 1)
  dice1 + dice2
}
```










