## Write a while loop

Let's get you started with building a **while** loop from the ground up. Have another look at its recipe:
```r
while (condition) {
  expr
}
```
Remember that the condition part of this recipe should become FALSE at some point during the execution. Otherwise, the while loop will go on indefinitely.

If your session expires when you run your code, check the body of your while loop carefully.

Have a look at the code on the right; it initializes the speed variables and already provides a while loop template to get you started.
```r
# Initialize the speed variable
speed <- 64

# Code the while loop
while (speed > 30 ) {
  print("Slow down!")
  speed <- speed-7
}

# Print out the speed variable
speed
```

## Throw in more conditionals

In the previous exercise, you simulated the interaction between a driver and a driver's assistant: When the speed was too high, "Slow down!" got printed out to the console, resulting in a decrease of your speed by 7 units.

There are several ways in which you could make your driver's assistant more advanced. For example, the assistant could give you different messages based on your speed or provide you with a current speed at a given moment.

A while loop similar to the one you've coded in the previous exercise is already available in the editor. It prints out your current speed, but there's no code that decreases the speed variable yet, which is pretty dangerous. Can you make the appropriate changes?
```r

# Initialize the speed variable
speed <- 64

# Extend/adapt the while loop
#If the speed is greater than 48, have R print out "Slow down big time!", and decrease the speed by 11.
#Otherwise, have R simply print out "Slow down!", and decrease the speed by 6.

while (speed > 30) {
  print(paste("Your speed is",speed))
  if (speed > 48 ) {
    print("Slow down big time!")
    speed<-speed-11
  } else {
    print("Slow down!")
    speed<-speed-6
  }
}
```
## Stop the while loop: break

There are some very rare situations in which severe speeding is necessary: what if a hurricane is approaching and you have to get away as quickly as possible? You don't want the driver's assistant sending you speeding notifications in that scenario, right?

This seems like a great opportunity to include the **break** statement in the **while** loop you've been working on. Remember that the 
**break** statement is a control statement. When R encounters it, the **while** loop is abandoned completely.
```r
# Initialize the speed variable
speed <- 88

while (speed > 30) {
  print(paste("Your speed is", speed))
  
  # Break the while loop when speed exceeds 80
  if (speed > 80 ) {
    break
  }
  
  if (speed > 48) {
    print("Slow down big time!")
    speed <- speed - 11
  } else {
    print("Slow down!")
    speed <- speed - 6
  }
}
```
## Build a while loop from scratch

The previous exercises guided you through developing a pretty advanced while loop, containing a break statement and different messages and updates as determined by control flow constructs. If you manage to solve this comprehensive exercise using a while loop, you're totally ready for the next topic: the for loop.


```r
#Finish the while loop so that it:
#prints out the triple of i, so 3 * i, at each run.
#is abandoned with a break if the triple of i is divisible by 8, but still prints out this triple before breaking.
# Initialize i as 1 
i <- 1

# Code the while loop
while (i <= 10) {
  print(3*i)
  if ( 3*i%%8 ==0 ) {
    break
  }
  i <- i + 1
}
```

## Loop over a vector

In the previous video, Filip told you about two different strategies for using the for loop. To refresh your memory, consider the following loops that are equivalent in R:
```r
primes <- c(2, 3, 5, 7, 11, 13)

# loop version 1
for (p in primes) {
  print(p)
}

# loop version 2
for (i in 1:length(primes)) {
  print(primes[i])
}
```
Remember our linkedin vector? It's a vector that contains the number of views your LinkedIn profile had in the last seven days. The linkedin vector has already been defined in the editor on the right so that you can fully focus on the instructions!

```r
Write a for loop that iterates over all the elements of linkedin and prints out every element separately. Do this in two ways: using the loop version 1 and the loop version 2 in the example code above.
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Loop version 1
for (item in linkedin){
  print(item)
}

# Loop version 2
for (i in 1:length(linkedin)){
   print(linkedin[i])  
}
```

## Loop over a list

Looping over a list is just as easy and convenient as looping over a vector. There are again two different approaches here:
```r
primes_list <- list(2, 3, 5, 7, 11, 13)

# loop version 1
for (p in primes_list) {
  print(p)
}

# loop version 2
for (i in 1:length(primes_list)) {
  print(primes_list[[i]])
}
```
**Notice that you need double square brackets - [[ ]]** - to select the list elements in loop version 2.

Suppose you have a list of all sorts of information on New York City: its population size, the names of the boroughs, and whether it is the capital of the United States. We've already prepared a list nyc with all this information in the editor (source: Wikipedia).
```r
# The nyc list is already specified
nyc <- list(pop = 8405837, 
            boroughs = c("Manhattan", "Bronx", "Brooklyn", "Queens", "Staten Island"), 
            capital = FALSE)

# Loop version 1
for (item in nyc){
  print(item)
}

# Loop version 2
for (i in 1:length(nyc)){
  print(nyc[[i]])
}
```

## Loop over a matrix

In your workspace, there's a matrix ttt, that represents the status of a tic-tac-toe game. It contains the values "X", "O" and "NA". Print out ttt in the console so you can have a closer look. On row 1 and column 1, there's "O", while on row 3 and column 2 there's "NA".

To solve this exercise, you'll need a for loop inside a for loop, often called a nested loop. Doing this in R is a breeze! Simply use the following recipe:
```r
for (var1 in seq1) {
  for (var2 in seq2) {
    expr
  }
}
```

```r
#Finish the nested for loops to go over the elements in ttt:
#The outer loop should loop over the rows, with loop index i (use 1:nrow(ttt)).
#The inner loop should loop over the columns, with loop index j (use 1:ncol(ttt)).
#Inside the inner loop, make use of print() and paste() to print out information in the following format: "On row i and column j the board #contains x", where x is the value on that position.
```r
# The tic-tac-toe matrix ttt has already been defined for you
ttt
# define the double for loop
for (i in 1:nrow(ttt)) {
  for (j in 1:ncol(ttt)) {
    #print(ttt[[i,j]])
    print(paste0("On row ", i ,"and column ",j," the board contains ",ttt[[i,j]]))
  }
}
```

## Mix it up with control flow

Let's return to the LinkedIn profile views data, stored in a vector linkedin. In the first exercise on for loops you already did a simple printout of each element in this vector. A little more in-depth interpretation of this data wouldn't hurt, right? Time to throw in some conditionals! As with the while loop, you can use the if and else statements inside the for loop.
```r
#Add code to the for loop that loops over the elements of the linkedin vector:
#If the vector element's value exceeds 10, print out "You're popular!".
#If the vector element's value does not exceed 10, print out "Be more visible!"
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Code the for loop with conditionals
for (li in linkedin) {
  if (li > 10 ) {
    print("You're popular!")
  } else {
    print("Be more visible!")
  }
  print(li)
}
```
## Next, you break it

In the editor on the right you'll find a possible solution to the previous exercise. The code loops over the linkedin vector and prints out different messages depending on the values of li.

In this exercise, you will use the **break** and **next** statements:

The break statement abandons the active loop: the remaining code in the loop is skipped and the loop is not iterated over anymore.
The next statement skips the remainder of the code in the loop, but continues the iteration.
```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Adapt/extend the for loop
for (li in linkedin) {
  if (li > 10) {
    print("You're popular!")
  } else {
    print("Be more visible!")
  }
   # Add if statement with break
  if (li > 16){
    print("This is ridiculous, I'm outta here!")
    break
    }
  # Add if statement with next
  if (li < 5){
    print("This is too embarrassing!")
    next
  }
  print(li)
}
```

## Build a for loop from scratch

This exercise will not introduce any new concepts on for loops.

In the editor on the right, we already went ahead and defined a variable rquote. This variable has been split up into a vector that contains separate letters and has been stored in a vector chars with the strsplit() function.

Can you write code that counts the number of r's that come before the first u in rquote?

```r
#Initialize the variable rcount, as 0.
#Finish the for loop:
#if char equals "r", increase the value of rcount by 1.
#if char equals "u", leave the for loop entirely with a break.
#Finally, print out the variable rcount to the console to see if your code is correct.
# Pre-defined variables
rquote <- "r's internals are irrefutably intriguing"
chars <- strsplit(rquote, split = "")[[1]]
# Initialize rcount
rcount <- 0
# Finish the for loop
for (char in chars) {
  if (char == "r"){
    rcount <-rcount+1
  }
  if (char == "u"){
    break
  }
}
# Print out rcount
print(rcount)
```





