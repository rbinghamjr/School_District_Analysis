# School_District_Analysis

## Overview

In this project, twp csv files were provided with 39,170 rows of student data and 15 rows of school data. 
The student data included the following:
- School ID
- Student name
- Gender
- Grade
- School name
- Reading score
- Math score
The school data included the following:
- School ID
- School name
- Type
- Size 
- Budget

Original analysis categorized mutliple facets of the data including creating bins for spending ranges per student, average scores per school size, and average scores per school type.
![image](https://user-images.githubusercontent.com/90691846/136838899-4f68fcd2-09cb-434a-99b8-127a89847dc6.png)

![image](https://user-images.githubusercontent.com/90691846/136838933-5bb2f9b2-30f6-41b3-91ca-ec07c986c858.png)

![image](https://user-images.githubusercontent.com/90691846/136838965-89c514ca-7b01-4b76-b266-99f34f895943.png)

After creating this analysis, it was found that academic dishonesty occured with the math and reading scores for Thomas High School. A new analysis was run to accomodate for the acadmeic dishonesty and to replace/remove these values from the overall analysis.

## Results
Th first noticeable difference between the old and new datasets is the total amount of students decreased from 39,170 to 38,709 which removes 461 students and their scores from the data. This was achieved by nulling out the 9th grade school with NaNs to remove the data for the ninth grade.
```
# Step 2. Use the loc method on the student_data_df to select all the reading scores from the 9th grade at Thomas High School and replace them with NaN.
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School")
                    & (student_data_df["grade"] == "9th"),"reading_score"] =np.nan

#  Step 3. Refactor the code in Step 2 to replace the math scores with NaN.
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School")
                    & (student_data_df["grade"] == "9th"),"math_score"] =np.nan

#  Step 4. Check the student data for NaN's. 
student_data_df.tail(10)
```

![image](https://user-images.githubusercontent.com/90691846/136840012-4aa9637f-c410-4163-9ba2-8da52773b5a6.png)

In the original District summatry, Thomas High School had an approximate 93.3% passing math, 97.3% Passing Reading, and an overall passing of 90.9%. After removing the ninth grade scores, these scores did decrease as seen below:

![image](https://user-images.githubusercontent.com/90691846/136844126-e1a0c8b0-5410-42eb-b53b-4b0dffc56dcb.png)

After removing the ninth graders, Thomas High School still remained in the top 5 high performing schools. Replacing the ninth grade scores had the following affect in these categories:
- Math and reading scores by grade: ninth grade now shows as a null or NaN value and is not calculated 
- Scores by school spending: Minimal impact due to small number of student size to the data
- Scores by school size: Minimal impact due to small number of student size to the data
- Scores by school type: Minimal impact due to small number of student size to the data

## Summary
There were minimal changes affecting the the overall impact after removing the ninth grade scores. 
- The average math score decreased from 83.418349 to 83.350937
- The average reading increased from 83.848930 to 83.896082
- % Passing match decreased from 93.272171 to 93.185690
- % Passing reading decreased from 97.308869 to 97.018739
- % Overall Passing decreased from 90.948012 to 90.630324
Although there was academic dishonesty the score variance had little affect and Thomas High School still remained the #2 performing school. It is still important to remove the data from the data set to count for the overall honest responses to reflect the correct data. 
