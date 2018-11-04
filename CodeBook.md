The run_analysis.R script performs the following steps 



1. Download the dataset
*	Dataset downloaded from the specified URL and extracted under the folder called UCI HAR Dataset

2. Load data to variables
*	activities <- activity_labels.txt : 6 rows, 2 columns 
List of activities performed when the corresponding measurements were taken and its codes (labels)
*	features <- features.txt : 561 rows, 2 columns 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
*	
*	subject_test <- test/subject_test.txt : 2947 rows, 1 column 
contains test data of 9/30 volunteer test subjects being observed
*	X_test <- test/X_test.txt : 2947 rows, 561 columns 
contains recorded features test data
*	Y_test <- test/y_test.txt : 2947 rows, 1 columns 
contains test data of activities’code labels
*	
*	subject_train <- test/subject_train.txt : 7352 rows, 1 column 
contains train data of 21/30 volunteer subjects being observed
*	X_train <- test/X_train.txt : 7352 rows, 561 columns 
contains recorded features train data
*	Y_train <- test/y_train.txt : 7352 rows, 1 columns 
contains train data of activities’code labels

3. Merges the training and the test sets to create one data set
*	
*	ALLX (10299 rows, 561 columns) is created by merging X_train and X_test using rbind() function
*	ALLY (10299 rows, 1 column) is created by merging Y_train and Y_test using rbind() function
*	Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
*	Finally Merged_Data (10299 rows, 563 column) is created by merging Subject,  ALLY  and  ALLX  using  cbind() function

4. Extracts only the measurements using  the mean and standard deviation for each measurement

*	TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data. The data is subsetted by  selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

5. Tidy the acitvity names for the activities in the data set
*	Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

6. Set appropriate labels (descriptive variable names) for the columns in the datatable
*	code column in TidyData renamed into activities
*	All Acc in column’s name replaced by Accelerometer
*	All Gyro in column’s name replaced by Gyroscope
*	All BodyBody in column’s name replaced by Body
*	All Mag in column’s name replaced by Magnitude
*	All start with character f in column’s name replaced by Frequency
*	All start with character t in column’s name replaced by Time

7. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
*	FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
*	Export FinalData into FinalData.txt file.
