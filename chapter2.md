--- 
title_meta  : Chapter 1
title       : Summary statistics and tabulation
description : "How to get to know your data? In this chapter you will learn how to look at some basic aspects of your data."
 
--- type:NormalExercise lang:r xp:0 skills:1 key:exercise1_1
## What is my dataset like?
 
When you first start to work with a dataset, it is good to get a good look at it. You can check how many observations you have, how many variables and what are they like. Are there any missing values? 

Depending on the type of your variable, you can either look at the summary statistics or you can tabulate the values. These are both called descriptive statistics. 

Let's first start with the very basics of checking the size of your dataset and what are the names of the variables it contains.



 
*** =instructions
 - The name of your dataset is cardiac. Check the list of variable names in this dataset.
 - How many variables are in your dataset? 
 - How many observations (people, in this case) are in your dataset? 

*** =hint
Look at the sample code and try inserting the name of your dataset.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Example: Check the list of variable names in diabetes-dataset
names(diabetes)
 
# Example: Check how many variables and observations are in diabetes dataset
dim(diabetes)
 
# Check the list of variable names in cardiac-dataset.

 
# Check how many variables and observations are in cardiac-dataset.
 

```
 
*** =solution
```{r}
# Example: Check the list of variable names in diabetes-dataset
names(diabetes)
 
# Example: Check how many variables are in diabetes dataset
dim(diabetes)
 
# Check the list of variable names in cardiac-dataset.
names(cardiac)
 
# Check how many variables and observations are in cardiac-dataset.
dim(cardiac)
```
 
*** =sct
```{r}
test_output_contains(""gender"", incorrect_msg = "Make sure to use names() command and insert the name of the dataset requested.")
test_output_contains("36", incorrect_msg = "Make sure that you have understood how the dim()-function works.")
success_msg("Awesome! This clearly was a piece of cake to you! Now let's move on to the next exercise.")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:exercise1_2
## Descriptive statistics for continuous variables
Continuous variable is 

Summary statistics contain minimum and maximum values, upper and lower quartiles and mean and median. When you have a continuous variable, this is usually a good approach to get a better idea about the variable and its distribution. You can obtain the summary statistics in R by typing summary() and inserting the name of your variable into brackets. Summary statistics also reveal how many missing values are in your variable.

In addition to that, also standard deviation is often checked. This can be done with sd() command. 

*** =instructions

- Check the minimum, maximum, mean, median, and standard deviation of variable
- How many missing values are in this variable?
- What is the standard deviation of the variable? (Notice that if there are missing values, you have to type na.rm=TRUE in the brackets so that R knows that it can ignore them.)

*** =hint
Checking the dimensions of the dataset is a good way to find out how many observations there ar.
Also, when looking at the standard deviation, make sure you have not forgot to take care of the missing values.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}

 

```
 
*** =solution
```{r}
# Calculate the arithmetic mean of these numbers: 1, 3, 8, 10, 12
mean(c(1, 3, 8, 10, 12))
 
# Calculate the standard deviation of these numbers: 1, 3, 8, 10, 12
sd(c(1, 3, 8, 10, 12))

# Calculate the arithmetic mean of the ejectiofraction
mean(c(64,57,52,37,57,62,60,57, 57 ,37))
 
# Calculate the standard deviation of the ejectiofraction
sd(c(64,57,52,37,57,62,60,57, 57 ,37))
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
## Descriptive statistics for discrete variables 
A discrete variable is.

When dealing with a discrete variable it is good to check how many observations there are in each class of the variable. That is information that is often reported and it can be crucial to know in order to perform any further analysis for the data.


*** =instructions
 - Make a table of a variable

*** =hint
Remember to connect variables to the dataset with a '$' sign.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
 
 
```
 
*** =solution
```{r}

 
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
cor(cardiac$maxhr, cardiac$sbp)
-0.04567112
```
 
*** =sct
```{r}
test_student_typed("barplot(table(diabetes$gender))", not_typed_msg = "Make sure that you have added the table-command inside the barplot-command.")
test_student_typed("hist(cardiac$age)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("hist(cardiac$bhr)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("boxplot(diabetes$chol~diabetes$gender)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("plot(cardiac$maxhr,cardiac$sbp)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_output_contains("-0.04567112", incorrect_msg = "Make sure that you have checked the correlation coefficient.")

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




