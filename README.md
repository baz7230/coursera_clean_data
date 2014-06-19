coursera_clean_data
===================
The getting and cleaning script does the following, as noted in the comments embedded within the script below.

There is only one script which covers all of the basic steps.

# Step 1: Retrieve the data from the web
# First go to the web side to download the zip directory and dataset descriptions

# Step 2: run the run_analysis.R script
  Script below, with comments about each step

# Read the .txt files that hold the test data and training data. 

HARtest <- read.table("./data/X_test.txt")
testLabels <- read.table("./data/y_test.txt")
HARtrain <- read.table("./data/X_train.txt")
trainLabels <- read.table("./data/y_train.txt")
# get the labels for each dataset, apply them to the original data
col_names <- read.table("./data/features.txt")
# remove oddball characters so the column names are handle-able in R
# the following replaces "," ")" "(" and "-", all with "_"
colnames<- 
    gsub(pattern="\\,",replacement="_",
     x=gsub(pattern="\\)",replacement="_",
            x=gsub(pattern="\\(",replacement="_",
                   x=gsub(pattern="-",replacement="_",x=col_names$V2))))
# then rename the test and training columns
names(HARtest) <- colnames
names(HARtrain) <- colnames
# get the 6 types of activities, and rename the columns
activity_labels <- read.table("./data/activity_labels.txt")
names(activity_labels) <- c("act_label","activity")
# rename the columns in the test and train label dataframes to match the activity labels
names(testLabels)<-"act_label"
names(trainLabels)<-"act_label"
# get the subjects for each dataset, rename column, apply them to the original data
HARtestSubjects <- read.table("./data/subject_test.txt") 
HARtrainSubjects <- read.table("./data/subject_train.txt")
names(HARtestSubjects) <- "subjects"
names(HARtrainSubjects) <- "subjects"
# create data frames with subject, activity, and original data
HARtestdf <- cbind(subjects=HARtestSubjects$subjects,activities=testLabels,HARtest)
HARtraindf <- cbind(subjects=HARtrainSubjects$subjects,activities=trainLabels,HARtrain)
# merge the two datasets
HARdatadf <- rbind(HARtestdf,HARtraindf)
# pick the columns with only "mean" and "std" : original mean(), std()
# replace the original colnames with the new column names
colnames <- names(HARdatadf)
# create new column names for the subjects and activities
colsubject<-data.frame(colnum=1,stringsAsFactors=FALSE)
colactivity<-data.frame(colnum=2,stringsAsFactors=FALSE)
# get all the column numbers for standard deviation, then all for mean
# then combine all of the column numbers (using rbind) to select them out of the
# original dataframe. Note: must add 2 to the selected column numbers because 2
# new columns are being prepended to the data.frame
colstd<-data.frame(colnum=grep("std__",colnames,fixed=TRUE),stringsAsFactors=FALSE)
colmean<-data.frame(colnum=grep("mean__",colnames,fixed=TRUE),stringsAsFactors=FALSE)
neededcols<-rbind(colsubject,colactivity,colstd+2,colmean+2)
# this selects only those columns with means and std, plus the subject and activity label
# this generates 10,299 observations of 678 variables
HARselected <- HARdatadf[neededcols[order(neededcols$colnum),]]
# load data manipulation package(s); take the mean of each mean and std column
library(plyr)
library(reshape2)
# roll all of the variables into one column
HARmelt <- melt(HARselected,id=c("subjects","act_label")
                ,measure.vars=names(HARselected)[3:66])
# summarize the variables by taking the mean across subjects and activities
tidy_data<-ddply(HARmelt, c("subjects","act_label","variable"), summarise,
      mean = mean(value))
# add the correct activity names and remove the activity label column
activity_labels[,2]<-as.character(activity_labels[,2])
tidy_data<-merge(activity_labels,tidy_data,by.x="act_label",by.y="act_label",all=TRUE)
tidy_data <- subset(tidy_data, select = -c(act_label))
# see a sample of the tidy dataset in a user-selected order
tidy_data[order(tidy_data[,3],tidy_data[,1],tidy_data[,2]),][1:40,]
# write out the new dataset
write.table(tidy_data,"./data/tidy_data.txt",dec=".",row.names=FALSE)
# or write the data in an interesting order: by measurement, then activity, then who did the activity
write.table(tidy_data[order(tidy_data[,3],tidy_data[,1],tidy_data[,2]),],"./data/tidy_data.txt",dec=".",row.names=FALSE)
