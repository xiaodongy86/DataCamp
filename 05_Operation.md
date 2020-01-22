## Equality

The most basic form of comparison is equality. Let's briefly recap its syntax. The following statements all evaluate to TRUE (feel free to try them out in the console).

3 == (2 + 1)

"intermediate" != "r"

TRUE != FALSE

"Rchitect" != "rchitect"

Notice from the last expression that R is case sensitive: "R" is not equal to "r". Keep this in mind when solving the exercises in this chapter!

**#Comparison of logicals**

TRUE == FALSE

**#Comparison of numerics**

-6*14 != 17-101

**#Comparison of character strings**

"useR" == "user"

**#Compare a logical with a numeric**

TRUE == 1

Awesome! Since TRUE coerces to 1 under the hood, TRUE == 1 evaluates to TRUE. Make sure not to mix up == (comparison) and = (assignment), == is what need to check the equality of R objects.

## Greater and less than

Apart from equality operators, Filip also introduced the less than and greater than operators: < and >. You can also add an equal sign to express less than or equal to or greater than or equal to, respectively. Have a look at the following R expressions, that all evaluate to FALSE:

(1 + 2) > 4

"dog" < "Cats"

TRUE <= FALSE

Remember that for string comparison, R determines the greater than relationship based on alphabetical order. Also, keep in mind that 
TRUE is treated as 1 for arithmetic, and FALSE is treated as 0. Therefore, FALSE < TRUE is TRUE.

**#Comparison of numerics**
-6 * 5 + 2 > -10 + 1

**#Comparison of character strings**
"raining"  <= "raining dogs"

**#Comparison of logicals**
TRUE > FALSE

## Compare vectors

You are already aware that R is very good with vectors. Without having to change anything about the syntax, R's relational operators also work on vectors.

Let's go back to the example that was started in the video. You want to figure out whether your activity on social media platforms have paid off and decide to look at your results for LinkedIn and Facebook. The sample code in the editor initializes the vectors linkedin and facebook. Each of the vectors contains the number of profile views your LinkedIn and Facebook profiles had over the last seven days.

**#The linkedin and facebook vectors have already been created for you**

linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)

**#Popular days On which days did the number of LinkedIn profile views exceed 15?**

linkedin > 15

**#Quiet days When was your LinkedIn profile viewed only 5 times or fewer?**

linkedin <= 5

**#LinkedIn more popular than Facebook**

**#When was your LinkedIn profile visited more often than your Facebook profile?**

linkedin > facebook

## Compare matrices

R's ability to deal with different data structures for comparisons does not stop at vectors. Matrices and relational operators also work together seamlessly!

Instead of in vectors (as in the previous exercise), the LinkedIn and Facebook data is now stored in a matrix called views. The first row contains the LinkedIn information; the second row the Facebook information. The original vectors facebook and linkedin are still available as well.

**#The social data has been created for you**

linkedin <- c(16, 9, 13, 5, 2, 17, 14)

facebook <- c(17, 7, 5, 16, 8, 13, 14)

views <- matrix(c(linkedin, facebook), nrow = 2, byrow = TRUE)

**#When does views equal 13?**

views == 13

**#When is views less than or equal to 14?**

views <= 14

## & and |

Before you work your way through the next exercises, have a look at the following R expressions. All of them will evaluate to TRUE:

TRUE & TRUE

FALSE | TRUE

5 <= 5 & 2 < 3

3 < 4 | 7 < 6

Watch out: 3 < x < 7 to check if x is between 3 and 7 will not work; you'll need 3 < x & x < 7 for that.

In this exercise, you'll be working with the last variable. This variable equals the last value of the linkedin vector that you've worked with previously. The linkedin vector represents the number of LinkedIn views your profile had in the last seven days, remember? Both the variables linkedin and last have already been defined in the editor.

**#The linkedin and last variable are already defined for you**

linkedin <- c(16, 9, 13, 5, 2, 17, 14)

last <- tail(linkedin, 1)

**#Is last under 5 or above 10?**

last <5 | last >10

**#Is last between 15 (exclusive) and 20 (inclusive)?**

last > 15 & last <= 20 

## & and | (2)

Like relational operators, logical operators work perfectly fine with vectors and matrices.

Both the vectors linkedin and facebook are available again. Also a matrix - views - has been defined; its first and second row correspond to the linkedin and facebook vectors, respectively. Ready for some advanced queries to gain more insights into your social outreach?


**#The social data (linkedin, facebook, views) has been created for you**

**#linkedin exceeds 10 but facebook below 10**

linkedin > 10 & facebook < 10

**#When were one or both visited at least 12 times?**

linkedin >= 12 | facebook >= 12

**#When is views between 11 (exclusive) and 14 (inclusive)?**

views > 11 & views <= 14


## Blend it all together

With the things you've learned by now, you're able to solve pretty cool problems.

Instead of recording the number of views for your own LinkedIn profile, suppose you conducted a survey inside the company you're working for. You've asked every employee with a LinkedIn profile how many visits their profile has had over the past seven days. You stored the results in a data frame called li_df. This data frame is available in the workspace; type li_df in the console to check it out.











