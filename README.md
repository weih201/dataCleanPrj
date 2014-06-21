# Introduction

The input data of the script were got form the original files:  
* 'train/X_train.txt': Training set
* 'train/y_train.txt': Training labels
* 'test/X_test.txt': Test set
* 'test/y_test.txt': Test labels
* 'features.txt': List of all features.
* 'activity_labels.txt': Links the class labels with their activity name.
* 'features_info.txt': Shows information about the variables used on the feature vector.
* 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 
* 'test/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

The output data files include:  
1. "mean_std.txt": Including the the mean and standard deviation for each measurement.  
2. "data_summary.txt": Including the data of the average of each variable for each activity and each subject


# Approach of the script
1. Combining the training set 'x_train.txt' and test set 'y_test.txt' into a single data set
2. Extracting the column index set which include mean() or std() from the 'features.txt' file
3. Subsetting the data set with the got columns index set
4. Combining 'y_train.txt' and 'y_test.txt' into a single training labels list
5. Combining 'train/subject_train.txt' and 'test/subject_train.txt' into a single subject list
6. Combining the data set 3,4,5 into one single data set
7. Labeling the column in dataset 6 with the activity name from 'activity_labels.txt' file. This includes the required mean and standard deviation for each measurement.
8. Outputing the dataset into a file
9. Calculating the mean for every activity and every subject for each measurement variable
10. Combining all variables' mean into a single data frame. This is the required tidy data set with the average of each variable for each activity and each subject.
11. Outputing the data set in 10 into a second file


# Data features information:
The data features appear in the output files "mean_std.txt" and "data_summary.txt" come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

The set of variables that were estimated from these signals are: 

mean(): Mean value
std(): Standard deviation

The complete list of variables of each feature vector is shown below:

1. "Subject": The subject who performed the activity for each window sample. Its range is from 1 to 30.
2. "Activity": The activity name, which including: WALKING, WALKING_UPSTAIRS,WALKING_DOWNSTAIRS,SITTING,STANDING,LAYING
3. "tBodyAcc-mean()-X":
4. "tBodyAcc-mean()-Y":
5. "tBodyAcc-mean()-Z":
6. "tBodyAcc-std()-X":
7. "tBodyAcc-std()-Y":
8. "tBodyAcc-std()-Z":
9. "tGravityAcc-mean()-X":
10. "tGravityAcc-mean()-Y":
11. "tGravityAcc-mean()-Z":
12. "tGravityAcc-std()-X":
13. "tGravityAcc-std()-Y":
14. "tGravityAcc-std()-Z":
15. "tBodyAccJerk-mean()-X":
16. "tBodyAccJerk-mean()-Y":
17. "tBodyAccJerk-mean()-Z":
18. "tBodyAccJerk-std()-X":
19. "tBodyAccJerk-std()-Y":
20. "tBodyAccJerk-std()-Z":
21. "tBodyGyro-mean()-X":
22. "tBodyGyro-mean()-Y":
23. "tBodyGyro-mean()-Z":
24. "tBodyGyro-std()-X":
25. "tBodyGyro-std()-Y":
26. "tBodyGyro-std()-Z":
27. "tBodyGyroJerk-mean()-X":
28. "tBodyGyroJerk-mean()-Y":
29. "tBodyGyroJerk-mean()-Z":
30. "tBodyGyroJerk-std()-X":
31. "tBodyGyroJerk-std()-Y":
32. "tBodyGyroJerk-std()-Z":
33. "tBodyAccMag-mean()":
34. "tBodyAccMag-std()":
35. "tGravityAccMag-mean()":
36. "tGravityAccMag-std()":
37. "tBodyAccJerkMag-mean()":
38. "tBodyAccJerkMag-std()":
39. "tBodyGyroMag-mean()":
40. "tBodyGyroMag-std()":
41. "tBodyGyroJerkMag-mean()":
42. "tBodyGyroJerkMag-std()":
43. "fBodyAcc-mean()-X":
44. "fBodyAcc-mean()-Y":
45. "fBodyAcc-mean()-Z":
46. "fBodyAcc-std()-X":
47. "fBodyAcc-std()-Y":
48. "fBodyAcc-std()-Z":
49. "fBodyAccJerk-mean()-X":
50. "fBodyAccJerk-mean()-Y":
51. "fBodyAccJerk-mean()-Z":
52. "fBodyAccJerk-std()-X":
53. "fBodyAccJerk-std()-Y":
54. "fBodyAccJerk-std()-Z":
55. "fBodyGyro-mean()-X":
56. "fBodyGyro-mean()-Y":
57. "fBodyGyro-mean()-Z":
58. "fBodyGyro-std()-X":
59. "fBodyGyro-std()-Y":
60. "fBodyGyro-std()-Z":
61. "fBodyAccMag-mean()":
62. "fBodyAccMag-std()":
63. "fBodyBodyAccJerkMag-mean()":
64. "fBodyBodyAccJerkMag-std()":
65. "fBodyBodyGyroMag-mean()":
66. "fBodyBodyGyroMag-std()":
67. "fBodyBodyGyroJerkMag-mean()":
68. "fBodyBodyGyroJerkMag-std()":
