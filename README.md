# Week4_Project
Coursera Data Science Specialization - Getting &amp; Cleaning Data

##About this REPO

This repo is the work submitted for the "Peer-graded Assignment: Getting and Cleaning Data Course Project" on Coursera. 
The repo contains 3 files (i) The README document: README.Rmd (ii) The CodeBook: CodeBook.Rmd (iii) R script or Code for the assignment: run_analysis.R

## The README document

This is a R Markdown document for the README file. The README document explains the analysis of the R script written to create a tidy dataset. Refer to the CodeBook.Rmd file for details on the source dataset, variable names, and final output dataset.


## The R Script

Refer to the comments in the R script file run_analysis.R for step-by-step process to read the relevant data files, transform the files, install the R packages, and creating the final tidy dataset 

## R-packages used in the R Script
Use install.packages() to install the below packages

```{r}
install.packages()
```

1. stringr
2. data.table
3. dplyr
4. tidyr
5. rmarkdown

## Step 1 Getting the Data

(i) Download the Source Data for the Project

The link to the source data is provided below. Use this link to download the zip folder to the working directory . The description of the sub-folders and the files within it is provided in the CodeBook.Rmd

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

(ii) Read the data into R using read.table() to read .txt files

(iii) Use summary(), str() and dim() functions to explore the data files
  
## Step 2 Identify the mean and standard deviation variables 

We need to create two lists, one for column indexes and one for variable names, from the features.txt file. There are 561 variable names in the features.txt file. Of these, identify the variable names which have "mean" or "std" in the names. Use str_which() to get column indexes and use str_subset() to get column variable names. There should be 44 variable names that have "mean" or "std".

Clean/Modify the column variable names at this stage using str_replace_all()

## Step 3 Create subset of X_test and X_train with mean and std variables

Using fread function from the data.table package of R, read the X_test data file and select var_names for the columns to be selected

Using cbind function, append the subject_ID (from the subject_test datafile) and Activity ID (from the y_test datafile) columns to the dataset

Repeat the above step for X_train dataset

## Step 4 Combine the test and train datasets into one dataset

Using rbind function, combine the two datasets created in Step 3

## Step 5 Add column names for variables in the combined dataset

Using names() function, assign column names for Subject_ID, Activity_ID and variable names from the list of variable names created in Step 2

## Step 6 Add the Activity description column to the combined dataset

Using Merge() function, combine the two datasets - combined dataset from Step 5 and Activity description datafile activity_labels. Also add the column name for the newly added activity description column name in the above merged dataset

## Step 7 Reorder the column names in the merged dataset and sort by subject_ID and activity_ID

Reorder the columns using column indexes and then sort the tidy dataset by subject_ID and activity_ID

## Step 8 Create second dataset with the average of each variable for each activity and each subject

Using group_by() and summarize_each() create a summary dataset
