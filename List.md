# Lists 
## Why would you need them?

Congratulations! At this point in the course you are already familiar with:

Vectors (one dimensional array): can hold numeric, character or logical values. The elements in a vector all have the same data type.
Matrices (two dimensional array): can hold numeric, character or logical values. The elements in a matrix all have the same data type.
Data frames (two-dimensional objects): can hold numeric, character or logical values. Within a column all elements have the same data type, but different columns can be of different data type.

## Lists, why would you need them? (2)

A list in R is similar to your to-do list at work or school: the different items on that list most likely differ in length, characteristic, and type of activity that has to be done.

A list in R allows you to gather a variety of objects under one name (that is, the name of the list) in an ordered way. These objects can be matrices, vectors, data frames, even other lists, etc. It is not even required that these objects are related to each other in any way.

You could say that a list is some kind super data type: you can store practically any piece of information in it!

## Creating a list

Let us create our first list! To construct a list you use the function list():

my_list <- list(comp1, comp2 ...)
The arguments to the list function are the list components. Remember, these components can be matrices, vectors, other lists, ...

**#Vector with numerics from 1 up to 10**

my_vector <- 1:10 

**#Matrix with numerics from 1 up to 9**

my_matrix <- matrix(1:9, ncol = 3)

**#First 10 elements of the built-in data frame mtcars**

my_df <- mtcars[1:10,]

**#Construct list with these different elements:**

my_list <-list(my_vector, my_matrix, my_df)

## Creating a named list

Well done, you're on a roll!

Just like on your to-do list, you want to avoid not knowing or remembering what the components of your list stand for. That is why you should give names to them:

my_list <- list(name1 = your_comp1, 
                name2 = your_comp2)
                
This creates a list with components that are named name1, name2, and so on. If you want to name your lists after you've created them, you can use the names() function as you did with vectors. The following commands are fully equivalent to the assignment above:

my_list <- list(your_comp1, your_comp2)
names(my_list) <- c("name1", "name2")


