?Code Book

Raw data collection

Collection

Raw data are obtained from UCI Machine Learning repository. In particular we used the Human Activity Recognition Using Smartphones Data Set [1], that was used by the original collectors to conduct experiments exploiting Support Vector Machine (SVM) [2]. Activity Recognition (AR) aims to recognize the actions and goals of one or more agents from a series of observations on the agents' actions and the environmental conditions [3]. The collectors used a sensor based approach employing smartphones as sensing to...(line truncated)...

Signals The 3-axial time domain [5] signals from accelerometer and gyroscope were captured at a constant rate of 50 Hz [6]. Then they were filtered to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals using another filter. Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals [7]. Also the magnitude [8] of these three-dimensional signals were calculated using the Euclidean norm [9]. Finally a F...(line truncated)...

The set of variables that were estimated from these signals are: mean(): Mean value std(): Standard deviation mad(): Median absolute deviation max(): Largest value in array min(): Smallest value in array sma(): Signal magnitude area energy(): Energy measure. Sum of the squares divided by the number of values. iqr(): Interquartile range entropy(): Signal entropy arCoeff(): Autoregression coefficients with Burg order equal to 4 correlation(): Correlation coefficient between two signals maxInds(): Index of the...(line truncated)...

Data transformation

The raw data sets are processed with run_analisys.R script to create a tidy data set [12].

Merge training and test sets Test and training data (X_train.txt, X_test.txt), subject ids (subject_train.txt, subject_test.txt) and activity ids (y_train.txt, y_test.txt) are merged to obtain a single data set. Variables are labelled with the names assigned by original collectors (features.txt).

Extract mean and standard deviation variables From the merged data set is extracted and intermediate data set with only the values of estimated mean (variables with labels that contain "mean") and standard deviation (variables with labels that contain "std").

Use descriptive activity names A new column is added to intermediate data set with the activity description. Activity id column is used to look up descriptions in activity_labels.txt.

Label variables appropriately Labels given from the original collectors were changed: to obtain valid R names without parentheses, dashes and commas to obtain more descriptive labels

Create a tidy data set From the intermediate data set is created a final tidy data set where numeric variables are averaged for each activity and each subject. The tidy data set contains 10299 observations with 81 variables divided in: an activity label (Activity): WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING an identifier of the subject who carried out the experiment (Subject): 1, 3, 5, 6, 7, 8, 11, 14, 15, 16, 17, 19, 21, 22, 23, 25, 26, 27, 28, 29, 30 a 79-feature vector with ...(line truncated)...

Name Time domain Frequency domain Body Acceleration TimeDomain.BodyAcceleration.XYZ FrequencyDomain.BodyAcceleration.XYZ Gravity Acceleration TimeDomain.GravityAcceleration.XYZ
Body Acceleration Jerk TimeDomain.BodyAccelerationJerk.XYZ FrequencyDomain.BodyAccelerationJerk.XYZ Body Angular Speed TimeDomain.BodyAngularSpeed.XYZ FrequencyDomain.BodyAngularSpeed.XYZ Body Angular Acceleration TimeDomain.BodyAngularAcceleration.XYZ
Body Acceleration Magnitude TimeDomain.BodyAccelerationMagnitude FrequencyDomain.BodyAccelerationMagnitude Gravity Acceleration Magnitude TimeDomain.GravityAccelerationMagnitude Body Acceleration Jerk Magnitude TimeDomain.BodyAccelerationJerkMagnitude FrequencyDomain.BodyAccelerationJerkMagnitude Body Angular Speed Magnitude TimeDomain.BodyAngularSpeedMagnitude FrequencyDomain.BodyAngularSpeedMagnitude Body Angular Acceleration Magnitude TimeDomain.BodyAngularAccelerationMagnitude FrequencyDomain.BodyAngula...(line truncated)...

For variables derived from mean and standard deviation estimation, the previous labels are augmented with the terms "Mean" or "StandardDeviation".

The data set is written to the file tidydata.txt