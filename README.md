Tidy-Data-R
===========

Tidy dataset for the Cleaning Data R Class on Coursera.org 

#Read in 8 datasets
> train.x<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/train/X_train.txt")
> train.y<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/train/y_train.txt")
> test.x<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/test/X_test.txt")
> activity.lables<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/activity_labels.txt")
> features<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/features.txt")
> Subject.test<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/test/subject_test.txt")
> test.y<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/test/y_test.txt")
> Subject.train<-read.table("/Users/scdavis6/Desktop/UCI HAR Dataset/train/subject_train.txt")
> 
#Q1 Merge datasets
> merged.x <- rbind(test.x,train.x)
> 
#Q2 Extracts only the measurements on the mean and standard deviation for each measurement
> colnames(merged.x) <- c(as.character(features[,2]))
> Mean <- grep("mean()", colnames(merged.x), fixed = TRUE)
> Stan.Dev <- grep("std()", colnames(merged.x), fixed = TRUE)
#Create subset
> MeanStan.Dev <- merged.x[,c(Mean,Stan.Dev)]
> 
#Q3 Uses descriptive activity names to name the activities in the data set
#Combine datasets
> merged.y <- rbind(train.y, test.y)
#Combine objects
> activity1 <- cbind(merged.y, MeanStan.Dev)
#Get column names and make into object
> colnames(activity1)[1] <- "Activity"
> 
#Q4 Appropriately labels the data set with descriptive variable names
#Subset activity_lables dataset
> activity_lables[,2] <- as.character(activity_lables[,2])
#Run loop to label data
> for(i in 1:length(activity1[,1])){
+     activity1[i,1]<-activity_lables[activity1[i,1],2]
+ }
> 
#Q5 Creates a second, independent tidy data set with the average of 
#each variable for each activity and each subject
#Combine subjects datasets
> Subject.all <- rbind(Subject_train, Subject_test)
#Combine objects
> Subject1 <- cbind(Subject.all, activity1)
#Get column names of Subject1 object
> colnames(Subject1)[1] <- "Subject"
#Create tidy dataset
> Tdata <- aggregate(Subject1[,3] ~ Subject+Activity, data = Subject1, FUN <- "mean")
#Create loop for calculating mean of each variable
> for(i in 4:ncol(Subject1)){
+     Tdata[,i] <- aggregate(Subject1[,i] ~ Subject+Activity, data = Subject1, FUN <- "mean" )[,3]
+ }
#Get column names of Tdata dataset
> colnames(Tdata)[3:ncol(Tdata)] <- colnames(MeanStan.Dev)
> 
#Create tidy dataset table
> write.table(Tdata, file = "FinalData.txt")
