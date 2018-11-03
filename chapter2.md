--- 
title_meta  : Chapter 1
title       : Summary statistics and tabulation
description : "How to get to know your data? In this chapter you will learn how to look at some basic aspects of your data."
 
--- type:NormalExercise lang:r xp:0 skills:1 key:exercise2_1
## What is my dataset like?
 
When you first start to work with a dataset, it is good to get a good look at it. You can check how many observations you have, how many variables and what are they like. Are there any missing values? 

Depending on the type of your variable, you can either look at the summary statistics or you can tabulate the values. These are both called descriptive statistics. 

Let's first start with the very basics of checking the dimensions of your dataset and what are the names of the variables it contains.

 
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
dim(diabetes) # We can see that there are 25 variables and 403 observations.
 
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
test_student_typed("names(cardiac)", not_typed_msg = "Make sure to use names() command and insert the name of the dataset requested.")
test_student_typed("dim(cardiac)", not_typed_msg = "Make sure that you have understood how the dim()-function works.")
success_msg("Awesome! This clearly was a piece of cake to you! Now let's move on to the next exercise.")
```

--- type:NormalExercise lang:r xp:0 skills:1 key:exercise2_2
## Descriptive statistics for continuous variables
Continuous variable is basically a variable that can have any values in a certain range. For example height or weight are continuous variables, as well as blood pressure and cholesterol.

Summary statistics contain minimum and maximum values, upper and lower quartiles and mean and median. When you have a continuous variable, this is usually a good approach to get a better idea about the variable and its distribution. You can obtain the summary statistics in R by typing summary() and inserting the name of your variable into brackets. Summary statistics also reveal how many missing values are in your variable.

In addition to that, also standard deviation is often checked. You can study more about standard deviation in [here](http://davidmlane.com/hyperstat/A16252.html) for example. In R standard deviation can be checked with sd() command. 

*** =instructions

- Check the minimum, maximum, mean, median, and standard deviation of variable maxhr (maximum heart rate) in cardiac-dataset
- How many missing values are in this variable?
- What is the standard deviation of the variable? (Notice that if there are missing values, you have to type na.rm=TRUE in the brackets so that R knows that it can ignore them.)

*** =hint
Checking the dimensions of the dataset is a good way to find out how many observations there are.
Also, when looking at the standard deviation, make sure you have not forgot to take care of the missing values.
If you don't use the with-function, remember to connect variables to the dataset with a '$' sign.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Look at the summary statistics of bmi in diabetes-dataset
summary(diabetes$bmi)

# Look at the standard deviation of bmi in diabetes-dataset
sd(diabetes$bmi, na.rm = TRUE)

# Look at the summary statistics of maxhr in diabetes-dataset


# Look at the standard deviation of bmi in diabetes-dataset 


```
 
*** =solution
```{r}
# Look at the summary statistics of bmi in diabetes-dataset
summary(diabetes$bmi)

# Look at the standard deviation of bmi in diabetes-dataset
sd(diabetes$bmi, na.rm = TRUE)

# Look at the summary statistics of maxhr in diabetes-dataset
summary(cardiac$maxhr)

# Look at the standard deviation of bmi in diabetes-dataset 
sd(cardiac$maxhr, na.rm = TRUE) 
```

 
*** =sct
```{r}
test_output_contains("120", incorrect_msg = "Make sure that you have put the correct variable name inside summary-function.")
test_output_contains("21.9", incorrect_msg = "Make sure that you have put the correct variable name inside sd-function.")
test_student_typed("summary(", not_typed_msg = "Make sure you used summary()- function.")
test_student_typed("sd(", not_typed_msg = "Make sure you used sd()- function.")
success_msg("Super! Now let's move on to the next exercise.")
```


--- type:NormalExercise lang:r xp:0 skills:1 key:exercise2_3
## Descriptive statistics for discrete variables 
A discrete variable is a variable that can only have a limited number of values. They can also be values that cannot be put into order. For example person's favorite color, diabetes status and gender are discrete variables.

When dealing with a discrete variable it is good to check how many observations there are in each class of the variable. That is information that is often reported and it can be crucial to know in order to perform any further analysis for the data.


*** =instructions
 - Make a table of variable gender in diabetes-dataset.
 - Are there any missing values? Hint: Missing values don't appear by using the table-function. You can use summary-function for this purpose.

*** =hint
Remember to connect variables to the dataset with a '$' sign.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Make a table of a variable gender in cardiac-dataset
table(cardiac$gender)

# Are there any missing values in variable gender in cardiac-dataset?
summary(cardiac$gender)

# Make a table of a variable gender in diabetes-dataset


# Are there any missing values in variable gender in diabetes-dataset?


 
```
 
*** =solution
```{r}
# Make a table of a variable gender in cardiac-dataset
table(cardiac$gender)

# Are there any missing values in variable gender in cardiac-dataset?
summary(cardiac$gender)

# Make a table of a variable gender in diabetes-dataset
table(diabetes$gender)

# Are there any missing values in variable gender in diabetes-dataset?
summary(diabetes$gender)
 
```
 
*** =sct
```{r}
test_student_typed("table(", not_typed_msg = "Make sure that you are using the right function for the table.")
test_student_typed("summary(", not_typed_msg = "Have you used summary-function to check for the missing values?")

success_msg("Great! You're such a master at R! ")
```

--- type:NormalExercise lang:r xp:0 skills:1 key:exercise1_4
## Crosstabulating variables
 
When checking out your data, the good next step is to see how the variables might be related to each other. If you want to check for example how many females smoke and how many males smoke, you could crosstabulate these two discrete variables to take a look at the numbers. Crosstabulation can be done like a simple table, but instead of inserting just one variable name inside the table-function, you can insert two variables.

When crosstabulating, it is more sophisticated to use with-function than to just write table(data$variable). Look at the example to see the reason why.
 
*** =instructions
 - Crosstabulate variables gender and death in cardiac dataset. 
 
 - Crosstabulate variables location and cholcat in diabetes dataset. 
 


*** =hint
Try following the example code but use the variables given in the instructions.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Crosstabulate variables gender and location in diabetes dataset.
table(diabetes$gender, diabetes$location)
with(diabetes, table(gender, location)) # See the difference in the output?

# Crosstabulate variables anyevent and smoking in cardiac dataset.
with(cardiac, table(anyevent, smoking)) 

# Crosstabulate variables gender and death in cardiac dataset.

 
# Crosstabulate variables location and cholcat in diabetes dataset.

 
```
 
*** =solution
```{r}
# Crosstabulate variables gender and location in diabetes dataset.
table(diabetes$gender, diabetes$location)
with(diabetes, table(gender, location)) # See the difference in the output?

# Crosstabulate variables anyevent and smoking in cardiac dataset.
with(cardiac, table(anyevent, smoking)) 

# Crosstabulate variables gender and death in cardiac dataset.
with(cardiac, table(gender, death))
 
# Crosstabulate variables anyevent and death in cardiac dataset.
with(cardiac, table(anyevent, death))

```
 
*** =sct
```{r}
test_student_typed("table(", not_typed_msg = "Make sure that you have used the table-command to crosstabulate.")
test_student_typed("cholcat", not_typed_msg = "Make sure that you used the categorized cholesterol variable.")
test_student_typed("death", not_typed_msg = "Make sure that you used the death-variable.")
test_student_typed("cardiac", not_typed_msg = "Make sure that you used the right dataset.")

success_msg("Awesome! You are such a pro with crosstabulation!")
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




