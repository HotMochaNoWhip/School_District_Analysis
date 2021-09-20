# School_District_Analysis

---
## Deliverables for analysis of school district
- A high-level snapshot of the district's key metrics, presented in a table format
- An overview of the key metrics for each school, presented in a table format
- Tables presenting each of the follwing metrics
    - Top 5 and bottom 5 performing schools, based on the overall passing rate
    - The average math schore received by students in each grade level
    - The average reading score received by students in each grade level at each school
    - School performance based on the budget per student
    - School performance based on the school size
    - School performance based on the type of school
---
## Overview of the school district analysis
There is a potential issue with the 9th grade data from Thomas high school. In belief that it could have been tampered with we will be removing the data from our dataframe and recalculating our results to compare the data. 

---
## Results
After we removed the 9th grade data we determined the following changes to our analysis:
- District Summary - Very slight drop in all passing percentage between 0.1% and 0.5%
- School Summary - Again very slight changes, increase in math by less than 0.1% and slight drop in others by 0.1%
- School Standing - Still second place with a max change of 0.3%
- Detailed stats:
    - Math & Reading by grade - all 9th grade data removed, same scores for other grades.
    - Scores by school spending - the "$630-644" range looks exactly the same after formating since all data was less than 1% in change
    - Scores by school size - Since the overall change was less than 0.1% again we have no change once data is formatted 
    - Scores by school type - The change here overall for charter schools is 0.04%!! It is so small that again when formatted we see no change

---
## Summary

We needed to remove all of the grades for 9th graders at Thomas High. To do this we used a new method called the '.loc' method. This allowed us to locate specific data within a dataframe that we can then do a multitude of different things with. For example to replace that data with NaN values we used the following code:

```
student_data_df.loc[((student_data_df["grade"] == "9th") & (student_data_df["school_name"] == "Thomas High School")), ["reading_score"]] = np.nan

student_data_df.loc[((student_data_df["grade"] == "9th") & (student_data_df["school_name"] == "Thomas High School")), ["math_score"]] = np.nan
```

The changes we noticed in all of the data was VERY small. Even with the grades removed, once data was formatted we were not seeing any changes. When we look deeper we see that the highest percentage change was for the district summary and that was around 0.5%! Since the schools standing stayed the same and we notice very litle change we can infer 2 possible results 

A) The grades were not tampered with and the school is very consistent.
  
B) Since the values are so miniscule a detailed investigation should be held to look into the potentail tampering of data, since we would expect a decent change of more than 1% in each category.
test