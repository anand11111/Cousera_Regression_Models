Selection: 3
|                                                                                                       |   0%

| Least Squares Estimation. (Slides for this and other Data Science courses may be found at github
                             | https://github.com/DataScienceSpecialization/courses. If you care to use them, they must be downloaded as a
                             | zip file and viewed locally. This lesson corresponds to Regression_Models/01_03_ols. Galton data is from John
                             | Verzani's website, http://wiener.math.csi.cuny.edu/UsingR/)
                             
                             ...
                             
                             |=====                                                                                                  |   5%
                             | In this lesson, if you're using RStudio, you'll be able to play with some of the code which appears in the
                             | slides. If you're not using RStudio, you can look at the code but you won't be able to experiment with the
                             | function "manipulate". We provide the code for you so you can examine it without having to type it all out.
                             | In RStudio, when the edit window displays code, make sure your flashing cursor is back in the console window
                             | before you hit "Enter" or any keyboard buttons, otherwise you might accidentally alter the code. If you do
                             | alter the file, in RStudio, you can hit Ctrl z in the editor until all the unwanted changes disappear. In
                             | other editors, you'll have to use whatever key combination performs "undo" to remove all your unwanted
                             | changes.
                             
                             ...
                             
                             |===========                                                                                            |  11%
                             | Here are the Galton data and the regression line seen in the Introduction. The regression line summarizes the
                             | relationship between parents' heights (the predictors) and their children's (the outcomes).
                             
                             ...
                             
                             |================                                                                                       |  16%
                             | We learned in the last lesson that the regression line is the line through the data which has the minimum
                             | (least) squared "error", the vertical distance between the 928 actual children's heights and the heights
                             | predicted by the line. Squaring the distances ensures that data points above and below the line are treated
                             | the same. This method of choosing the 'best' regression line (or 'fitting' a line to the data) is known as
                             | ordinary least squares.
                             
                             ...
                             
                             |======================                                                                                 |  21%
                             | As shown in the slides, the regression line contains the point representing the means of the two sets of
                             | heights. These are shown by the thin horizontal and vertical lines. The intersection point is shown by the
                             | triangle on the plot. Its x-coordinate is the mean of the parents' heights and y-coordinate is the mean of the
                             | childrens' heights.
                             
                             ...
                             
                             |===========================                                                                            |  26%
                             | As shown in the slides, the slope of the regression line is the correlation between the two sets of heights
                             | multiplied by the ratio of the standard deviations (childrens' to parents' or outcomes to predictors).
                             
                             ...
                             
                             |=================================                                                                      |  32%
                             | Here we show code which demonstrates how changing the slope of the regression line affects the mean squared
                             | error between actual and predicted values. Look it over to see how straightforward it is.
                             
                             ...
                             
                             |======================================                                                                 |  37%
                             | What RStudio graphics package allows the user to play with the data to see the effects of the changes?
                             
                             1: abline
                             2: points
                             3: plot
                             4: manipulate
                             
                             Selection: 4
                             
                             | All that practice is paying off!
                             
                             |===========================================                                                            |  42%
                             | Now you can actually play with the code to use R's manipulate function and find the minimum squared error. You
                             | can adjust the slider with the left mouse button or use the right and left arrow keys to see how changing the
                             | slope (beta) affects the mean squared error (mse). If the slider disappears you can call it back by clicking
                             | on the little gear in the upper left corner of the plot window.
                             
                             ...
                             
                             |=================================================                                                      |  47%
                             | Which value of the slope minimizes the mean squared error?
                               
                               1: 5
                             2: .64
                             3: .70
                             4: .44
                             
                             Selection: 2
                             
                             | All that hard work is paying off!
                               
                               |======================================================                                                 |  53%
                             | What was the minimum mse?
                               
                               1: .64
                             2: 44
                             3: .66
                             4: 5.0
                             
                             Selection: 4
                             
                             | You are doing so well!
                               
                               |============================================================                                           |  58%
                             | Recall that you normalize data by subtracting its mean and dividing by its standard deviation. We've done this
                             | for the galton child and parent data for you. We've stored these normalized values in two vectors, gpa_nor and
                             | gch_nor, the normalized galton parent and child data.
                             
                             ...
                             
                             |=================================================================                                      |  63%
                             | Use R's function "cor" to compute the correlation between these normalized data sets.
                             
                             > cor(gpa_nor,gch_nor)
                             [1] 0.4587624
                             
                             | That's the answer I was looking for.
                             
                             |======================================================================                                 |  68%
                             | How does this correlation relate to the correlation of the unnormalized data?
                               
                               1: It is smaller.
                             2: It is the same.
                             3: It is bigger.
                             
                             Selection: 3
                             
                             | That's not the answer I was looking for, but try again.
                             
                             | Have you really changed anything?
                             
                             1: It is bigger.
                             2: It is the same.
                             3: It is smaller.
                             
                             Selection: 3
                             
                             | You almost had it, but not quite. Try again.
                             
                             | Have you really changed anything?
                             
                             1: It is smaller.
                             2: It is the same.
                             3: It is bigger.
                             
                             Selection: 2
                             
                             | Great job!
                             
                             |============================================================================                           |  74%
                             | Use R's function "lm" to generate the regression line using this normalized data. Store it in a variable
                             | called l_nor. Use the parents' heights as the predictors (independent variable) and the childrens' as the
                             | predicted (dependent). Remember, 'lm' needs a formula of the form dependent ~ independent. Since we've created
                             | the data vectors for you there's no need to provide a second "data" argument as you have previously.
                             
                             > l_nor <- lm(gpa_nor~gch_nor)
                             
                             | Not quite right, but keep trying. Or, type info() for more options.
                             
                             | Type "l_nor <- lm(gch_nor ~ gpa_nor)" at the R prompt.
                             
                             > l_nor <- lm(gch_nor ~ gpa_nor)
                             
                             | Perseverance, that's the answer.
                             
                             |=================================================================================                      |  79%
                             | What is the slope of this line?
                             
                             1: I have no idea
                             2: The correlation of the 2 data sets
                             3: 1.
                             
                             Selection: 2
                             
                             | You got it right!
                             
                             |=======================================================================================                |  84%
                             | If you swapped the outcome (Y) and predictor (X) of your original (unnormalized) data, (for example, used
                             | childrens' heights to predict their parents), what would the slope of the new regression line be?
  
  1: I have no idea
2: the same as the original
3: 1.
4: correlation(X,Y) * sd(X)/sd(Y)

Selection: 4

| That's the answer I was looking for.

|============================================================================================           |  89%
| We'll close with a final display of source code from the slides. It plots the galton data with three
| regression lines, the original in red with the children as the outcome, a new blue line with the parents' as
| outcome and childrens' as predictor, and a black line with the slope scaled so it equals the ratio of the
| standard deviations.

...

|==================================================================================================     |  95%
| Congrats! You've concluded this lesson on ordinary least squares which are truly extraordinary!

...

|=======================================================================================================| 100%
| Would you like to receive credit for completing this course on Coursera.org?

1: No
2: Yes

Selection: Yes
What is your email address? kakrishnaanand@gmail.com
What is your assignment token? kej7DN52TQBRV4eS
Grade submission failed.
Press ESC if you want to exit this lesson and you
want to try to submit your grade at a later time.

| That's not exactly what I'm looking for. Try again.

| 

1: Yes
2: No

Selection: Yes