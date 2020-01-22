## The if statement

Before diving into some exercises on the if statement, have another look at its syntax:

if (condition) {
  expr
}
Remember your vectors with social profile views? Let's look at it from another angle. The medium variable gives information about the social website; the num_views variable denotes the actual number of views that particular medium had on the last day of your recordings. Both these variables have already been defined in the editor.

**#Variables related to your last day of recordings**

medium <- "LinkedIn"

num_views <- 14

**#Examine the if statement for medium**

if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
}

**#Write the if statement for num_views**

if (num_views > 15){
print("You are popular!")
  }

## Add an else

You can only use an else statement in combination with an if statement. The else statement does not require a condition; its corresponding code is simply run if all of the preceding conditions in the control structure are FALSE. Here's a recipe for its usage:

if (condition) {
  expr1
} else {
  expr2
}

**It's important that the else keyword comes on the same line as the closing bracket of the if part!**

Both if statements that you coded in the previous exercises are already available in the editor. It's now up to you to extend them with the appropriate else statements!

#Variables related to your last day of recordings
medium <- "LinkedIn"
num_views <- 14

**#Control structure for medium**

if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else {
  print("Unknown medium")
}

**#Control structure for num_views**

if (num_views > 15) {
  print("You're popular!")
} else {
  print("Try to be more visible!")
}

## Customize further: else if

The else if statement allows you to further customize your control structure. You can add as many else if statements as you like. Keep in mind that R ignores the remainder of the control structure once a condition has been found that is TRUE and the corresponding expressions have been executed. Here's an overview of the syntax to freshen your memory:

if (condition1) {
  expr1
} else if (condition2) {
  expr2
} else if (condition3) {
  expr3
} else {
  expr4
}

Again, It's important that the else if keywords comes on the same line as the closing bracket of the previous part of the control construct!


**#Variables related to your last day of recordings**

medium <- "LinkedIn"
num_views <- 14

**#Control structure for medium**

if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else if (medium == "Facebook") {
  print("Showing Facebook information")
} else {
  print("Unknown medium")
}

**#Control structure for num_views**

if (num_views > 15) {
  print("You're popular!")
} else if (num_views <= 15 & num_views > 10) {
  print("Your number of views is average")
} else {
  print("Try to be more visible!")
}

## Else if 2.0

You can do anything you want inside if-else constructs. You can even put in another set of conditional statements. Examine the following code chunk:

if (number < 10) {
  if (number < 5) {
    result <- "extra small"
  } else {
    result <- "small"
  }
} else if (number < 100) {
  result <- "medium"
} else {
  result <- "large"
}
print(result)
Have a look at the following statements:

If number is set to 6, "small" gets printed to the console.
If number is set to 100, R prints out "medium".
If number is set to 4, "extra small" gets printed out to the console.
If number is set to 2500, R will generate an error, as result will not be defined.








