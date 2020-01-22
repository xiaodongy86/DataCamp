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



