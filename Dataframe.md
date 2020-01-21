# Dataframe

## What's a data frame?

You may remember from the chapter about matrices that all the elements that you put in a matrix should be of the same type. Back then, your data set on Star Wars only contained numeric elements.

When doing a market research survey, however, you often have questions such as:

'Are you married?' or 'yes/no' questions (logical)
'How old are you?' (numeric)
'What is your opinion on this product?' or other 'open-ended' questions (character)
...
The output, namely the respondents' answers to the questions formulated above, is a data set of different data types. You will often find yourself working with data sets that contain different data types instead of only one.

A data frame has the variables of a data set as columns and the observations as rows. This will be a familiar concept for those coming from different statistical software packages such as SAS or SPSS.

## Quick, have a look at your data set

Wow, that is a lot of cars!

Working with large data sets is not uncommon in data analysis. When you work with (extremely) large data sets and data frames, your first task as a data analyst is to develop a clear understanding of its structure and main elements. Therefore, it is often useful to show only a small part of the entire data set.

So how to do this in R? Well, the function head() enables you to show the first observations of a data frame. Similarly, the function tail() prints out the last observations in your data set.

Both head() and tail() print a top line called the 'header', which contains the names of the different variables in your data set.

## Have a look at the structure

Another method that is often used to get a rapid overview of your data is the function str(). The function str() shows you the structure of your data set. For a data frame it tells you:

The total number of observations (e.g. 32 car types)
The total number of variables (e.g. 11 car features)
A full list of the variables names (e.g. mpg, cyl ... )
The data type of each variable (e.g. num)
The first observations
Applying the str() function will often be the first thing that you do when receiving a new data set or data frame. It is a great way to get more insight in your data set before diving into the real analysis.

## Creating a data frame

Since using built-in data sets is not even half the fun of creating your own data sets, the rest of this chapter is based on your personally developed data set. Put your jet pack on because it is time for some space exploration!

As a first goal, you want to construct a data frame that describes the main characteristics of eight planets in our solar system. According to your good friend Buzz, the main features of a planet are:

The type of planet (Terrestrial or Gas Giant).
The planet's diameter relative to the diameter of the Earth.
The planet's rotation across the sun relative to that of the Earth.
If the planet has rings or not (TRUE or FALSE).
After doing some high-quality research on Wikipedia, you feel confident enough to create the necessary vectors: name, type, diameter, rotation and rings; these vectors have already been coded up on the right. The first element in each of these vectors correspond to the first observation.

You construct a data frame with the data.frame() function. As arguments, you pass the vectors from before: they will become the different columns of your data frame. Because every column has the same length, the vectors you pass should also have the same length. But don't forget that it is possible (and likely) that they contain different types of data.

**#Definition of vectors**

name <- c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune")

type <- c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
          "Terrestrial planet", "Gas giant", "Gas giant", "Gas giant", "Gas giant")

diameter <- c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)

rotation <- c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)

rings <- c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

**#Create a data frame from the vectors**

planets_df <- data.frame(name,type,diameter,rotation,rings)

   name               type   diameter rotation rings

1 Mercury Terrestrial planet    0.382    58.64 FALSE

2   Venus Terrestrial planet    0.949  -243.02 FALSE

3   Earth Terrestrial planet    1.000     1.00 FALSE

4    Mars Terrestrial planet    0.532     1.03 FALSE

5 Jupiter          Gas giant   11.209     0.41  TRUE

6  Saturn          Gas giant    9.449     0.43  TRUE

7  Uranus          Gas giant    4.007    -0.72  TRUE

8 Neptune          Gas giant    3.883     0.67  TRUE

## Creating a data frame (2)

The planets_df data frame should have 8 observations and 5 variables. It has been made available in the workspace, so you can directly use it.
**#Check the structure of planets_df**
str(planets_df)
'data.frame':	8 obs. of  5 variables:

 $ name    : Factor w/ 8 levels "Earth","Jupiter",..: 4 8 1 3 2 6 7 5

$ type    : Factor w/ 2 levels "Gas giant","Terrestrial planet": 2 2 2 2 1 1 1 1

$ diameter: num  0.382 0.949 1 0.532 11.209 ...

$ rotation: num  58.64 -243.02 1 1.03 0.41 ...

$ rings   : logi  FALSE FALSE FALSE FALSE TRUE TRUE ...

## Selection of data frame elements

Similar to vectors and matrices, you select elements from a data frame with the help of square brackets [ ]. By using a comma, you can indicate what to select from the rows and the columns respectively. For example:

my_df[1,2] selects the value at the first row and second column in my_df.
my_df[1:3,2:4] selects rows 1, 2, 3 and columns 2, 3, 4 in my_df.
Sometimes you want to select all elements of a row or column. For example, my_df[1, ] selects all elements of the first row. Let us now apply this technique on planets_df!

**#The planets_df data frame from the previous exercise is pre-loaded**
head(planets_df)
**#Select first 5 values of diameter column**
planets_df[1:5,3]

## Only planets with rings

You will often want to select an entire column, namely one specific variable from a data frame. If you want to select all elements of the variable diameter, for example, both of these will do the trick:

planets_df[,3]
planets_df[,"diameter"]
However, there is a short-cut. If your columns have names, you can use the $ sign:

planets_df$diameter

## Only planets with rings (2)

You probably remember from high school that some planets in our solar system have rings and others do not. Unfortunately you can not recall their names. Could R help you out?

If you type rings_vector in the console, you get:

[1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
This means that the first four observations (or planets) do not have a ring (FALSE), but the other four do (TRUE). However, you do not get a nice overview of the names of these planets, their diameter, etc. Let's try to use rings_vector to select the data for the four planets with rings.

## Only planets with rings but shorter

So what exactly did you learn in the previous exercises? You selected a subset from a data frame (planets_df) based on whether or not a certain condition was true (rings or no rings), and you managed to pull out all relevant data. Pretty awesome! By now, NASA is probably already flirting with your CV ;-).

Now, let us move up one level and use the function subset(). You should see the subset() function as a short-cut to do exactly the same as what you did in the previous exercises.

subset(my_df, subset = some_condition)
The first argument of subset() specifies the data set for which you want a subset. By adding the second argument, you give R the necessary information and conditions to select the correct subset.

The code below will give the exact same result as you got in the previous exercise, but this time, you didn't need the rings_vector!

subset(planets_df, subset = rings)

**#Select planets with diameter < 1**

subset(planets_df,subset= diameter <1)


## Sorting

Making and creating rankings is one of mankind's favorite affairs. These rankings can be useful (best universities in the world), entertaining (most influential movie stars) or pointless (best 007 look-a-like).

In data analysis you can sort your data according to a certain variable in the data set. In R, this is done with the help of the function order().

order() is a function that gives you the ranked position of each element when it is applied on a variable, such as a vector for example:

> a <- c(100, 10, 1000)
> order(a)
[1] 2 1 3
10, which is the second element in a, is the smallest element, so 2 comes first in the output of order(a). 100, which is the first element in a is the second smallest element, so 1 comes second in the output of order(a).

This means we can use the output of order(a) to reshuffle a:

> a[order(a)]
[1]   10  100 1000




















