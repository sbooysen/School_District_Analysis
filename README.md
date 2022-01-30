# School_District_Analysis
## By: Stacey Booysen
### Challenge Summary
For this challenge we were tasked with finding overall average test scores for both reading and math for 15 different schools. The goal was to return these calculations to the school board to assist them in determining future budgeting needs.
### Data Analysis
However, there was an issue encountered when the school board became suspicious that there was academic dishonesty in a particular set. The ninth-grade student scores for Thomas High School were suspected to have been altered, and so, along with our regular calculations, we needed to remove those scores from consideration by replacing them with “NaN”.

![Exampl](https://github.com/sbooysen/School_District_Analysis/blob/main/NaN%20replacements.png)

*	With the ninth-grade scores for Thomas High school removed, the overall average for the district is altered and not representative of the true overall scores.
*	The school summary specifically is now completely incorrect as it isn’t accounting for an entire grade. 
*	Due to the missing elements, it is impossible to say if the school’s overall averages would be close to the 90% passing rate it is currently projecting. Significantly lower scores in the ninth-grade section, could drop their score. 
*	The replacement of the ninth-grade scores alters the below aspects of the data:
    *	The math and reading scores by grade are now skewed when calculating all the schools to represent the entire district.
    * By removing an entire grade, we are also removing the number of students representing that grade. This changes the budget to make it appear less than it might actually be and creates an illusion that the school is spending less than it actually is.
    *	Scores by school size can indicate if  there’s a large number of students doing poorly in a particular school, relative to other schools.
    *	Scores by school type makes it appear as though all Charter schools fall within a passing rate above 70%, however, if the dishonesty came as a result of much lower scores for the ninth-graders, then it’s safe to assume that Thomas High School could fall below the general charter school average.

### Overall Summary
39,171 of the total student count was reduced by 461 due to the removal of the ninth-graders from Thomas High School, bringing the new total to 38,709.

When using the below code, we retrieved the updated data without the ninth-graders:
```
# Step 12. Replace the passing math percent for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc[["Thomas High School"], ["% Passing Math"]] = ths_math_pass_percentage
# Step 13. Replace the passing reading percentage for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc[["Thomas High School"], ["% Passing Reading"]] = ths_reading_pass_percentage
# Step 14. Replace the overall passing percentage for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc[["Thomas High School"], ["% Overall Passing"]] = overall_passing_percentage
per_school_summary_df
```
The results produced showed the overall passing math and reading scores for Thomas High School went from:
Math: 
66.911315%	to	93.185690%
Reading: 
69.663609%	to	97.018739%	

THis process removed an entire grade from the total students in Thomas High School, altering the data available for the code to analyze means properly. Thanks to this, it also threw off the calculations for the ninth-grade set for all schools total, as well as throwing off the calculations for the district as a whole. As shown in the huge jump in the above listed scores, this is creating a very skewed outcome for the data provided. In general, it would be better to calculate the data again once the appropriate scores for Thomas high School's ninth-grade classes are available. For the time being, unless we are to remove the entire school from the list, their incorrect data will alter the numbers a bit too much to be overlooked. 
