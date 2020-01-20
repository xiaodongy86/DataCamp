# Matrix
## What's a matrix?

In R, a matrix is a collection of elements of the same data type (numeric, character, or logical) arranged into a fixed number of rows and columns. Since you are only working with rows and columns, a matrix is called two-dimensional.

You can construct a matrix in R with the matrix() function. Consider the following example:

matrix(1:9, byrow = TRUE, nrow = 3)
In the matrix() function:

The first argument is the collection of elements that R will arrange into the rows and columns of the matrix. Here, we use 1:9 which is a shortcut for c(1, 2, 3, 4, 5, 6, 7, 8, 9).
The argument byrow indicates that the matrix is filled by the rows. If we want the matrix to be filled by the columns, we just place byrow = FALSE.
The third argument nrow indicates that the matrix should have three rows.

# Construct a matrix with 3 rows that contain the numbers 1 up to 9
matrix(1:9, byrow = TRUE, nrow = 3)

## Analyze matrices, you shall

It is now time to get your hands dirty. In the following exercises you will analyze the box office numbers of the Star Wars franchise. May the force be with you!

In the editor, three vectors are defined. Each one represents the box office numbers from the first three Star Wars movies. The first element of each vector indicates the US box office revenue, the second element refers to the Non-US box office (source: Wikipedia).

In this exercise, you'll combine all these figures into a single vector. Next, you'll build a matrix from this vector.

**#Box office Star Wars (in millions!)**

new_hope <- c(460.998, 314.4)
empire_strikes <- c(290.475, 247.900)
return_jedi <- c(309.306, 165.8)

**#Create box_office**

box_office <- c(new_hope, empire_strikes, return_jedi)

**#Construct star_wars_matrix**

star_wars_matrix <- matrix(box_office, nrow = 3, byrow =T)

## Naming a matrix

To help you remember what is stored in star_wars_matrix, you would like to add the names of the movies for the rows. Not only does this help you to read the data, but it is also useful to select certain elements from the matrix.

Similar to vectors, you can add names for the rows and the columns of a matrix

rownames(my_matrix) <- row_names_vector
colnames(my_matrix) <- col_names_vector
We went ahead and prepared two vectors for you: region, and titles. You will need these vectors to name the columns and rows of star_wars_matrix, respectively.


**#Construct star_wars_matrix**

box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
star_wars_matrix <- matrix(box_office, nrow = 3, byrow = TRUE,
                           dimnames = list(c("A New Hope", "The Empire Strikes Back", "Return of the Jedi"), 
                                           c("US", "non-US")))
**#The worldwide box office figures**

worldwide_vector <- rowSums(star_wars_matrix)


Adding a column for the Worldwide box office

In the previous exercise you calculated the vector that contained the worldwide box office receipt for each of the three Star Wars movies. However, this vector is not yet part of star_wars_matrix.

You can add a column or multiple columns to a matrix with the cbind() function, which merges matrices and/or vectors together by column. For example:

big_matrix <- cbind(matrix1, matrix2, vector1 ...)


# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix <- cbind(star_wars_matrix,worldwide_vector)

## Adding a row

Just like every action has a reaction, every cbind() has an rbind(). (We admit, we are pretty bad with metaphors.)

Your R workspace, where all variables you defined 'live' (check out what a workspace is), has already been initialized and contains two matrices:

star_wars_matrix that we have used all along, with data on the original trilogy,
star_wars_matrix2, with similar data for the prequels trilogy.
Type the name of these matrices in the console and hit Enter if you want to have a closer look. If you want to check out the contents of the workspace, you can type ls() in the console.

**#Combine both Star Wars trilogies in one matrix**

all_wars_matrix <- rbind(star_wars_matrix,star_wars_matrix2)

## Selection of matrix elements

Similar to vectors, you can use the square brackets [ ] to select one or multiple elements from a matrix. Whereas vectors have one dimension, matrices have two dimensions. You should therefore use a comma to separate the rows you want to select from the columns. For example:

my_matrix[1,2] selects the element at the first row and second column.
my_matrix[1:3,2:4] results in a matrix with the data on the rows 1, 2, 3 and columns 2, 3, 4.
If you want to select all elements of a row or a column, no number is needed before or after the comma, respectively:

my_matrix[,1] selects all elements of the first column.
my_matrix[1,] selects all elements of the first row.
Back to Star Wars with this newly acquired knowledge! As in the previous exercise, all_wars_matrix is already available in your workspace.

**#all_wars_matrix is available in your workspace**

all_wars_matrix

**#Select the non-US revenue for all movies**

non_us_all <- all_wars_matrix[,2]
  
**#Average non-US revenue**

mean(non_us_all)
  
**#Select the non-US revenue for first two movies**

non_us_some <- all_wars_matrix[1:2,2]
  
**#Average non-US revenue for first two movies**

mean(non_us_some)

## A little arithmetic with matrices

Similar to what you have learned with vectors, the standard operators like +, -, /, *, etc. work in an element-wise way on matrices in R.

For example, 2 * my_matrix multiplies each element of my_matrix by two.

As a newly-hired data analyst for Lucasfilm, it is your job to find out how many visitors went to each movie for each geographical area. You already have the total revenue figures in all_wars_matrix. Assume that the price of a ticket was 5 dollars. Simply dividing the box office numbers by this ticket price gives you the number of visitors.

**#all_wars_matrix is available in your workspace**

all_wars_matrix

**#Estimate the visitors**

visitors <- all_wars_matrix/5
  
**#Print the estimate to the console**

print(visitors)


**#all_wars_matrix and ticket_prices_matrix are available in your workspace**

all_wars_matrix
ticket_prices_matrix

**#Estimated number of visitors**

visitors <- all_wars_matrix/ticket_prices_matrix

**#US visitors**

us_visitors <- visitors[,1]

**#Average number of US visitors**

mean(us_visitors)



























