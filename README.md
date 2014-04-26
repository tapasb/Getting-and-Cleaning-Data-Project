
### Running the script

- Run `Rscript <path to>/run_analysis.R`
- The tidy dataset should get created in the current directory as `tidy.txt`


### Assumptions

- The training and test data are available in folders named `train` and `test` respectively.
- For each of these data sets:
    - Measurements are present in `X_<dataset>.txt` file
    - Subject information is present in `subject_<dataset>.txt` file
    - Activity codes are present in `y_<dataset>.txt` file
- All activity codes and their labels are in a file named `activity_labels.txt`.
- Names of all measurements taken are present in file `features.txt` ordered and indexed as they appear in the `X_<dataset>.txt` files.
- All columns representing means contain `...mean()` in them.
- All columns representing standard deviations contain `...std()` in them.


### Data Preparation Steps

1. For each of the training and test datasets, 
    1. Read the `X` values
    2. Take a subset of the columns representing only the mean and standard deviation values. Subsetting is done early on to conserve memory.
    3. Associate additional columns to represent activity IDs and subject IDs read from `y_<dataset>.txt` and `subject_<dataset>.txt` files respectively.
    4. Assign column names by manipulating the measurement names in `features.txt` to remove spaces and convert them to camel case.
2. Merge the training and the test sets, read as in step 1 to create one data set.
3. Associate an additional column with descriptive activity names as specified in `activity_labels.txt`.
4. Melt the dataset by specifying activity ID, name and subject ID as the only ID variables.
5. Re cast the melted dataset with activity name and subject id as the only IDs and `mean` as the aggregator function.
6. Save the resultin re-casted dataset as `tidy.txt`

