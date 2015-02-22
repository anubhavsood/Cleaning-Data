# Cleaning-Data-Project Steps

Please Note: make sure that the 'UCI HAR Dataset' dataset provided as part of the project is unzipped in your working directory folder.<br />
After this has been done, please run the Run_Analysis.R file in the R-Studio with command source("*path*\Run_Analysis.R"); where *path* denotes the path where Run_Analysis.R file has been placed by you.<br />

##How the code works.

*Step1: Get the current working directory and set this in 'workdir' variable.<br />
*Step2: Create variables workdir1,workdir2,workdir3,workdir4,workdir5,workdir6,workdir7,workdir8 and assign the paths of the following files in the specified order (with the help of variable 'workdir' created in Step1).<br />
		1)workdir1= workdir +"/UCI HAR Dataset/test/X_test.txt"<br />
		2)workdir2= workdir +"/UCI HAR Dataset/test/y_test.txt" <br />
		3)workdir3= workdir +"/UCI HAR Dataset/test/subject_test.txt" <br />
		4)workdir4= workdir +"/UCI HAR Dataset/train/X_train.txt" <br />
		5)workdir5= workdir +"/UCI HAR Dataset/train/y_train.txt" <br />
		6)workdir6= workdir +"/UCI HAR Dataset/train/subject_train.txt" <br />
		7)workdir7= workdir +"/UCI HAR Dataset/activity_labels.txt" <br />
		8)workdir8= workdir +"/UCI HAR Dataset/features.txt" <br />
*Step3: Create data frames 'testx','testy','testsub','trainx','trainy','trainsub','activity_lab' and 'feature' and populate data into them using read.table command from file paths stored in variables described in Step2 respectively.<br />
*Step4: Create new data frame 'test' and assign data to it by column binding data frames 'testx','testy' and 'testsub'.<br />
*Step5: Create new data frame 'train' and assign data to it by column binding data frames 'trainx','trainy' and 'trainsub'.<br />
*Step6: Create new data frame 'bind' and assign data to it by row binding data frames test and train created in Step 4 and Step5 respectively.<br />
*Step7: Assign column names "subject" and "activityid" to first 2 columns of data frame 'bind' created in Step6.<br />
*Step8: Assign column names to columns 3-563 of data frame 'bind' using the data frame 'feature' created in Step3.<br />
*Step9: Using the grep command, extract the column indexes from data frame 'bind' where column names match words 'mean()' or 'std()'. Store this extracted data in new variable 'index'.<br />
*Step10: Create new data frame 'dataset' which contains only column indexes 1,2 and 'index'(created in Step9) from data frame 'bind'.<br />
*Step11: Assign column names "activityid" and "activity" to data frame 'activity_lab' created in Step3.<br />
*Step12: Load package 'dplyr' using the library command.<br />
*Step13: Inner join data frames 'activity_lab' and 'dataset' (created in Step3 and Step10 respectively) on column "activityid". Store the resultant dataset into variable 'data'.<br />
*Step14: Exclude the first column from data frame 'data'.<br />
*Step15: Finally, using the summarise_each() function, calculate and display the mean of all columns in data frame 'data'.<br />