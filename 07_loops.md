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



