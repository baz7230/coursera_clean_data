CODEBOOK
=================

Much of this material is taken directly from the original authors, and is at this site:
  http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
	[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. 
	Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine.
	International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

There are four columns in the tidy dataset

ACTIVITY: There are 6 activities measured: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
  The variables were measured during these different activities
  
SUBJECTS: There were 30 subjects in the experiment, anonymously referred to as subject 1 through 30

VARIABLE: There are 66 mean variables that were measured and captured, the means of which were calculated for this tidy dataset.
  The variables prefixed with 't' are time measurements, those prefixed with 'f' are frequency signals

MEAN: The average (mean) of each of the variables was calculated, broken out by subject and the activity performed
  The units for the original variables have been normalized by the range of the variables, therefore the
  means are similarly unit-less; they are means of ratios

"The features selected come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz.
Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise.
Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using
  another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ).
 Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ,
 fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

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
mad(): Median absolute deviation 
max(): Largest value in array
min(): Smallest value in array
sma(): Signal magnitude area
energy(): Energy measure. Sum of the squares divided by the number of values. 
iqr(): Interquartile range 
entropy(): Signal entropy
arCoeff(): Autorregresion coefficients with Burg order equal to 4
correlation(): correlation coefficient between two signals
maxInds(): index of the frequency component with largest magnitude
meanFreq(): Weighted average of the frequency components to obtain a mean frequency
skewness(): skewness of the frequency domain signal 
kurtosis(): kurtosis of the frequency domain signal 
bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean"

The complete list of variables in the tidy dataset is below. They are all of the means and standard deviations.
I chose to omit the meanFreq() variable.

 "tBodyAcc_mean___X"          
 "tBodyAcc_mean___Y"           "tBodyAcc_mean___Z"           "tBodyAcc_std___X"           
 "tBodyAcc_std___Y"            "tBodyAcc_std___Z"            "tGravityAcc_mean___X"       
 "tGravityAcc_mean___Y"        "tGravityAcc_mean___Z"        "tGravityAcc_std___X"        
 "tGravityAcc_std___Y"         "tGravityAcc_std___Z"         "tBodyAccJerk_mean___X"      
 "tBodyAccJerk_mean___Y"       "tBodyAccJerk_mean___Z"       "tBodyAccJerk_std___X"       
 "tBodyAccJerk_std___Y"        "tBodyAccJerk_std___Z"        "tBodyGyro_mean___X"         
 "tBodyGyro_mean___Y"          "tBodyGyro_mean___Z"          "tBodyGyro_std___X"          
 "tBodyGyro_std___Y"           "tBodyGyro_std___Z"           "tBodyGyroJerk_mean___X"     
 "tBodyGyroJerk_mean___Y"      "tBodyGyroJerk_mean___Z"      "tBodyGyroJerk_std___X"      
 "tBodyGyroJerk_std___Y"       "tBodyGyroJerk_std___Z"       "tBodyAccMag_mean__"         
 "tBodyAccMag_std__"           "tGravityAccMag_mean__"       "tGravityAccMag_std__"       
 "tBodyAccJerkMag_mean__"      "tBodyAccJerkMag_std__"       "tBodyGyroMag_mean__"        
 "tBodyGyroMag_std__"          "tBodyGyroJerkMag_mean__"     "tBodyGyroJerkMag_std__"     
 "fBodyAcc_mean___X"           "fBodyAcc_mean___Y"           "fBodyAcc_mean___Z"          
 "fBodyAcc_std___X"            "fBodyAcc_std___Y"            "fBodyAcc_std___Z"           
 "fBodyAccJerk_mean___X"       "fBodyAccJerk_mean___Y"       "fBodyAccJerk_mean___Z"      
 "fBodyAccJerk_std___X"        "fBodyAccJerk_std___Y"        "fBodyAccJerk_std___Z"       
 "fBodyGyro_mean___X"          "fBodyGyro_mean___Y"          "fBodyGyro_mean___Z"         
 "fBodyGyro_std___X"           "fBodyGyro_std___Y"           "fBodyGyro_std___Z"          
 "fBodyAccMag_mean__"          "fBodyAccMag_std__"           "fBodyBodyAccJerkMag_mean__" 
 "fBodyBodyAccJerkMag_std__"   "fBodyBodyGyroMag_mean__"     "fBodyBodyGyroMag_std__"     
 "fBodyBodyGyroJerkMag_mean__" "fBodyBodyGyroJerkMag_std__"
