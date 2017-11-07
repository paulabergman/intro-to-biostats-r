--- 
title_meta  : Chapter 1
title       : WEEK 1, Basics of R, summary statistics and tabulation (deadline 14.11. 23:59)
description : "In this chapter, you will get to know some basic features of R. You will also learn to check the summary statistics of continuous variables and draw some simple graphs."
 
--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_1
## WEEK 1 STARTS HERE: Let's get started
 
In the box below you can see the instructions for the exercise. On the right in the upper window you can type your code. That window is called editor. You can execute the code by pressing Ctrl+Enter (Cmd+Enter in Mac) when the cursor is on the same line with your command. If your command is on multiple lines you must select all those rows and then Ctrl+Enter or Cmd+Enter. When you run your commands, the results appear in the window under the editor. That window is called console.
 
You can use R as a calculator. You can run basic mathematical operations like this: 
 
- Addition: `+`
- Subtraction: `-`
- Multiplication: `*`
- Division: `/`
- Exponentiation: `^`
 
In order to understand better your own code, or in case you want to save it as an actual R script (It is possible if you have R installed in your computer.) it is good to comment on your code. That can be done by typing `#` at the beginning of the row. Any text you type on that row will be considered as a comment. For example _Calculate the mean of these numbers: 1, 3, 8, 10, 12_ in the editor window is a comment.
 
*** =instructions
 - Assume we have a sample of ten people from the cardiac-dataset. Their ejectionfractions (in percents) are 64, 57, 52, 37, 57, 62, 60, 57, 57 and 37. 
   - Calculate the mean of ejectionfraction for the sample. 
   - Calculate the standard deviation of ejectionfraction for the sample. 

*** =hint
Just revise the formulas of mean and standard deviation! Write the numbers on the console and run the lines.
 
*** =pre_exercise_code
```{r}
 # no pec
```
 
*** =sample_code
```{r}
# Example: Calculate the arithmetic mean of these numbers: 1, 3, 8, 10, 12
(1 + 3 + 8 + 10 + 12) / 5
 
# Example: Calculate the standard deviation of these numbers: 1, 3, 8, 10, 12
sqrt((((1 - 6.8)^2) + ((3 - 6.8)^2) + ((8 - 6.8)^2) + ((10 - 6.8)^2) + ((12 - 6.8)^2)) / (5 - 1))
 
# Calculate the arithmetic mean of the ejectiofraction as shown in example above:

 
# Calculate the standard deviation of the ejectiofraction as shown in example above:
 

```
 
*** =solution
```{r}
# Example: Calculate the arithmetic mean of these numbers: 1, 3, 8, 10, 12
(1 + 3 + 8 + 10 + 12) / 5
 
# Example: Calculate the standard deviation of these numbers: 1, 3, 8, 10, 12
sqrt((((1 - 6.8)^2) + ((3 - 6.8)^2) + ((8 - 6.8)^2) + ((10 - 6.8)^2) + ((12 - 6.8)^2)) / (5 - 1))

# Calculate the arithmetic mean of the ejectiofraction as shown in example above:
(64 + 57 + 52 + 37 + 57 + 62 + 60 + 57 + 57 + 37) /10 
 
# Calculate the standard deviation of the ejectiofraction as shown in example above:
sqrt((((64 - 54)^2) + ((57 - 54)^2) + ((52 - 54)^2) + ((37 - 54)^2) + ((57 - 54)^2) + ((62 - 54)^2) + ((60 - 54)^2) + ((57 - 54)^2) + ((57 - 54)^2) + ((37 - 54)^2)) / 9 )

```
 
*** =sct
```{r}
test_output_contains("54", incorrect_msg = "Make sure to add the values together and divide them by the sample size (10).")
test_output_contains("9.533", incorrect_msg = "Make sure that you have studied well the formula of standard deviation.")
success_msg("Awesome! This clearly was a piece of cake to you! Now let's move on to the next exercise.")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_2
## How to make these in a more simple way
In the previous exercise we calculated mean and standard deviation manually. R, however, has many equations already in it. For example, to calculate the mean of values 4, 6 and 7 you can just type mean(c(4,6,7)). Or to calculate the standard deviation of these numbers, just type sd(c(4,6,7))

*** =instructions

Calculate the mean and standard deviation for that same data set as in previous exercise using function mean() and sd(). You should get the same results as in previous exercise. As a reminder: the ejectionfractions (in percents) were as follow: : 64, 57, 52, 37, 57, 62, 60, 57, 57 and 37.

*** =hint
Make sure you have not forget to put those numbers in vector c()!
 
*** =pre_exercise_code
```{r}
 # no pec
```
 
*** =sample_code
```{r}
# Calculate the arithmetic mean of these numbers: 1, 3, 8, 10, 12
mean(c(1,3,8 ,10,12))
 
# Calculate the standard deviation of these numbers: 1, 3, 8, 10, 12
sd(c(1, 3, 8, 10, 12))
 
# Calculate the arithmetic mean of the ejectiofraction as shown in example above

 
# Calculate the standard deviation of the ejectiofraction as shown in example above
 

```
 
*** =solution
```{r}
# Calculate the arithmetic mean of the ejectiofraction
mean(c(64,57,52,7,57,62,60,57, 57 ,37))
 
# Calculate the standard deviation of the ejectiofraction
sd(c(64,57,52,7,57,62,60,57, 57 ,37))
```
 
*** =sct
```{r}
test_output_contains("54", incorrect_msg = "Make sure that you have put the correct values inside mean()-function.")
test_output_contains("9.533", incorrect_msg = "Make sure that you have put the correct values inside sd()-function.")
test_student_typed("mean(", not_typed_msg = "Make sure you used mean()- function.")
test_student_typed("sd(", not_typed_msg = "Make sure you used sd()- function.")
success_msg("Super! Now let's move on to the next exercise.")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_3
## Checking out the data! 
 
When you get a new data set, it is a good practice to first give it a quick overview: to check how many samples you have, how many variables you have, how many females / males, and what is the age distribution, for example. To get the number of samples and variables in your data, just type dim(data). For categorical variables, table() is a good way, and for continous variables use summary() to get an overview of that specific variable. If you need to know what variables you have in your data, just type colnames(data).
 
*** =instructions
 - Find out how many observations does the cardiac-data contain. 
 - Find out how many observations does the diabetes-data contain.
 - Find out how many females are in cardiac-data.
 - Find out how many female are in diabetes- data.
 - What is the age-range in cardiac-data?
 - What is the age-range in diabetes-data?

*** =hint
Checking the dimensions of the dataset is a good way to find out how many observations are there. 
Remember to connect variables to the dataset with a '$' sign. Remember also the table() and summary()- functions!
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Hint! You can refer to our data sets just by typing "cardiac" and "diabetes". To refer to any variable in that data just type it in the form data$variable, for example cardiac$gender.

# Fill in the sample sizes:
# Cardiac:
# Diabetes: 

# Females in cardiac-data:
# Females in diabetes-data: 
 
# Check age distribution in cardiac-data (summary of the variable age in cardiac-data):


# Chekc age distribution in diabetes-data (summary of the variable age in diabetes-data):
 
 
```
 
*** =solution
```{r}
# Fill in the sample sizes:
# Cardiac: 558
# Diabetes: 403

# Females in cardiac-data: 338
# Females in diabetes-data: 234
 
# Check age distribution in cardiac-data (summary of the variable 'age' in cardiac-data):
summary(cardiac$age)

# Chekc age distribution in diabetes-data (summary of the variable 'age' in diabetes-data):
summary(diabetes$age)
 
```
 
*** =sct
```{r}
test_student_typed("558", not_typed_msg = "Make sure that you have the right sample size for cardiac-data.")
test_student_typed("403", not_typed_msg = "Make sure that you have the right sample size for diabetes-data.")
test_student_typed("338", not_typed_msg = "Make sure that you have the right female number for cardiac-data.")
test_student_typed("234", not_typed_msg = "Make sure that you have the right female number for diabetes-data.")
test_student_typed("summary(cardiac$age)", not_typed_msg = "Make sure you checked the summary of the variable age in cardiac- dataset correctly.")
test_student_typed("summary(diabetes$age)", not_typed_msg = "Make sure you checked the summary of the variable age in diabetes- dataset correctly.")

success_msg("Great! You're such a master at R! ")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_4
## Basic plotting
 
When checking out your data, the good next step is to visualize the variables. This is how you get the first idea of their distributions and can spot the possible outliers (the kind of values that are very different from the other values.) Propably most commonly used plotting commands are hist() for histrogram, barplot() for barplot, plot() for scatter plot and boxplot() for boxplot. 
 
*** =instructions
 - Draw a barplot of the variable 'gender' in diabetes-dataset.
 
 - Draw a histogram of the variable 'age' in cardiac-dataset.
 
 - Draw a histogram of the variable 'bhr' (= "basal heart rate") in cardiac-dataset. Is there anything weird?
 
 - Draw a boxplot for cholesterol ('chol') in diabetes- data by gender.
 
 - Draw a scatter-plot for the variables maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data
 
 - Check also the correlation of maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data.


*** =hint
Make sure you have the right variable(s) in your plotting- command, and you have used the right plotting- command! Make also sure you have not made any spelling mistakes.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Example1: Draw a barplot of the variable 'gender' in cardiac-dataset
 barplot(table(cardiac$gender))
 
# Example2: Draw a histogram of the variable 'cholmmol' (cholesterol in mmol) in diabetes-dataset
 hist(diabetes$cholmmol)
 
# Draw a barplot of the variable 'gender' in diabetes-dataset

 
# Draw a histogram of the variable 'age' in cardiac-dataset


# Draw a histogram of the variable 'bhr' (="basal heart rate") in cardiac-dataset. Is there anything weird?

 
# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender.

# Draw a scatter-plot for the variables maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data 

# Check the correlation of maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data.

 
```
 
*** =solution
```{r}
# Example1: Draw a barplot of the variable 'gender' in cardiac-dataset
 barplot(table(cardiac$gender))
 
# Example2: Draw a histogram of the variable 'cholmmol' (cholesterol in mmol) in diabetes-dataset
 hist(diabetes$cholmmol)
 
# Draw a barplot of the variable 'gender' in diabetes-dataset
 barplot(table(diabetes$gender))
 
# Draw a histogram of the variable 'age' in cardiac-dataset
hist(cardiac$age)

# Draw a histogram of the variable 'bhr' (= "basal heart rate") in cardiac-dataset. Is there anything weird?
hist(cardiac$bhr)
 
# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender.
boxplot(diabetes$chol~diabetes$gender)
 
# Draw a scatter-plot for the variables maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data 
plot(cardiac$maxhr,cardiac$sbp)

# Check the correlation of maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data.
cor(cardiac$maxhr, cardiac$sb)
-0.04567112
```
 
*** =sct
```{r}
test_student_typed("barplot(table(diabetes$gender))", not_typed_msg = "Make sure that you have added the table-command inside the barplot-command.")
test_student_typed("hist(cardiac$age)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("hist(cardiac$bhr)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("boxplot(diabetes$chol~diabetes$gender)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("plot(cardiac$maxhr,cardiac$sbp)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("cor(cardiac$maxhr,cardiac$sbp)", not_typed_msg = "Make sure that you have checked the correlation coefficient.")

success_msg("Awesome! You old plotting wizard!")
```
--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_5

## Making plots more fancy
 
Plots are cooler with some colours in it. Title is a good way to tell people what the plot is about. One of R's best features is it wide range of colours, and easy wat of adjusting your plots to be exactly as you want. The basic colours, such as red and green can be gained by just typing 'red' or 'green'. To fin out more about colours in R, and their names, google colours in R and you are on your way to a super fancy plots!

*** =hint
Just add the title and colour options inside the plotting code, just like in the example.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
*** =instructions
- Draw a barplot of the variable 'gender' in diabetes-dataset. Add a title and colour to you plot. Don't be afraid to get creative!
- Draw a histogram of the variable 'age' in cardiac-dataset. Add a title and colour to you plot.
- Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. 
 
*** =sample_code
```{r}
# Draw a barplot of the variable 'gender' in cardiac-dataset. Add a title and colour to you plot.
 
barplot(table(cardiac$gender),main="Gender in cardiac-dataset",col="tomato")

# Draw a barplot of the variable 'gender' in diabetes-dataset. Add a title and colour to you plot.
 

# Draw a histogram of the variable 'age' in cardiac-dataset. Add a title and colour to you plot.


# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. Hint! use col=c("colour1","colour2")  
 
```
 
*** =solution
```{r}
# Draw a barplot of the variable 'gender' in diabetes-dataset
 
barplot(table(diabetes$gender),main="Title",col="red")
 
# Draw a barplot of the variable 'age' in cardiac-dataset
hist(cardiac$age,main="Title",col="red")

# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. 
boxplot(diabetes$chol~diabetes$gender, col=c("red", "blue"))

```
 
*** =sct
```{r}
test_function("barplot", incorrect_msg = "Did you enter both title and colour options?")
test_function("hist", incorrect_msg = "Did you enter both title and colour options?")
success_msg("Oh your plots look just fabulous!")
```




