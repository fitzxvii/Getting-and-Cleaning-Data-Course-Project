# Code Book
### The following tasks below are the contents of run_analysis.R script: 

### 1. Download the dataset

- Dataset downloaded and extracted under the folder called UCI HAR Dataset

### 2. Assign each data to variables

- `features` <- features.txt : 561 rows, 2 columns

  - The features come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

- `activities` <- activity_labels.txt : 6 rows, 2 columns

  - List of activities was done when the corresponding assessment were taken and its coded labels

- `subject_test` <- test/subject_test.txt : 2947 rows, 1 column

  - contains test data of 9/30 volunteer test subjects that were observed

- `x_test` <- test/X_test.txt : 2947 rows, 561 columns

  - contains the noted features test data

- `y_test` <- test/y_test.txt : 2947 rows, 1 columns

  - contains test data of activities’ coded labels

- `subject_train` <- test/subject_train.txt : 7352 rows, 1 column

  - contains train data of 21/30 volunteer subjects that were observed

- `x_train` <- test/X_train.txt : 7352 rows, 561 columns

  - contains note features train data

- `y_train` <- test/y_train.txt : 7352 rows, 1 columns

  - contains train data of activities’code labels

### 3. Merges the training and the test sets to create one data set
- `x_set` (10299 rows, 561 columns) is created by merging `x_train` and `x_test` using `rbind()` function
- `y_set` (10299 rows, 1 column) is created by merging `y_train` and `y_test` using `rbind()` function
- `subject_set` (10299 rows, 1 column) is created by merging `subject_train` and `subject_test` using `rbind()` function
- `data_set` (10299 rows, 563 column) is created by merging `subject_set`, `y_set` and `x_set` using `cbind()` function

### 4. Extracts only the measurements on the mean and standard deviation for each measurement
- `tidy_data` (10299 rows, 88 columns) is created by subsetting `data_set`; selecting the columns of subject, code, the mean and the standard deviation for each data

### 5. Uses descriptive activity names to name the activities in the data set
- The whole data in code column of `tidy_data` is replaced with the corresponding `activity` that taken from the second column of `activities` variable.

### 6. Appropriately labels the data set with descriptive variable names
- The code columns in `tidy_data` are renamed into `activities`
  - All column named *Acc* are replaced by **Accelerometer**
  - All column named *Gyro* are replaced by **Gyroscope**
  - All column named *BodyBody* are replaced by **Body**
  - All column named *Mag* are replaced by **Magnitude**
  - All column name *^f* are replaced by **Frequency**
  - All column name *^t* are replaced by **Time**
  - All column named *tBody* are replaced by **TimeBody**

### 7. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
- `final_data` (180 rows, 88 columns) is created by summarizing `tidy_data` through taking the mean for each variable, for each activity and for each subject, then they were group by subject and activity.
- The export `final_data` was made and named `IndependentTidyDataSets.txt`.
