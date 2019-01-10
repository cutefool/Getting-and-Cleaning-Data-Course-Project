# Getting and Cleaning Data Project

This is for indicating all the variables and summaries calculated, along with unite, and any other relevant information.

### Source Data

The information about how the experiment conducted and how the original data collected can be found in the [zip file](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).

### Introduction to the analysis on the original data

- "X_train.txt", "y_train.txt" and "subject_train.txt" contain information about training data.
- "X_test.txt", "y_test.txt" and "subjuect_test.txt" contain information about testing data.
- "features.txt" contains names of all measurements.

### Structures of the data and the idea of naming variables

1. Values of Variable `Activity` consist of data from “Y_train.txt” and “Y_test.txt”
2. values of Variable `Subject` consist of data from “subject_train.txt” and subject_test.txt"
3. Values of Variables `Features` consist of data from “X_train.txt” and “X_test.txt”
4. Names of Variables `Features` come from “features.txt”
5. levels of Variable `Activity` come from “activity_labels.txt”

So we use `Activity`, `Subject` and `Features` as part of descriptive variable names for data in data frame. 

### Variables after merging the training and the test sets

1. `dataSubject` consists of `dataSubjectTrain` and `dataSubjectTest`
2. `dataActivity` consists of `dataActivityTrain` and `dataActivityTest`
3. `dataFeatures` consists of `dataFeaturesTrain` and `dataFeaturesTest` 

### Variables after labelling the data set with descriptive variable names

In the former part, variables activity and subject and names of the activities have been labelled by descriptive names. In this part, Names of Feteatures will labelled by descriptive variable names.

- prefix t is replaced by time
- Acc is replaced by Accelerometer
- Gyro is replaced by Gyroscope
- prefix f is replaced by frequency
- Mag is replaced by Magnitude
- BodyBody is replaced by Body

### Introduction to the code submitted

- Using `download.file()` together with `unzip()` function to download the zip file from website to my compute.
- Using `read.table()` function to load "X_train.txt", "y_train", "subject_train" in train directory and "X_test", "y_test", "subject_test" into R.
- Using `rbind()` and `cbind()` functions to merge all train and test data together.
- Using `read.table()` function to load "features.txt" into R.
- Using `grep()` function to find the indexes with "mean()" and "sd()".
- select all relevant columns and set the columns name using the selected features name.
- Using `read.table()` function to load "activity_labels.txt" into R.
- Using `factor()` function with arguments "levels = " and "labels = " to replace the numbers to activity names.
- Using `gsub()` function to replace all characters I think they are needed to replace.
- Using `aggregate` and `order` functions in `plyr` package to calculate all means for each activity and each subject.