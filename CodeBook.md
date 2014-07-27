Codebook

#Data origin: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

#Data Description on website:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. 
Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) 
wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 
3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been 
video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 
70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in 
fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, 
which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body 
acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a 
filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating 
variables from the time and frequency domain. 

#The dataset has 8 files:

features_info.txt

features.txt

activity_labels.txt

X_train.txt

y_train.txt

X_test.txt

y_test.txt

subject_train.txt

subject_test.txt


#Variables

10299 observations of 561 variables. 


#Transformations
Step 1: Merge test and training datasets into one. 
Step 2: Extracted mean and standard deviation measurements.
Step 3: Labeled columns with descriptive activities.
Step 4: Calculated average of each variable (column) per activity.
Step 5: Created dataset with the means and standard deviations. 






