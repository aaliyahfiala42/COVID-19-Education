# Analysis of COVID-19 and Education in Essex County, New Jersey
### Aaliyah Hänni 
### December 14th, 2021
### Project Dashboard: https://public.tableau.com/views/TheImpactofCOVID-19onEducation


## Project Overview
In Essex County, New Jersey effective March 18th, 2020 all schools in the State of New Jersey were closed for the remaining school year (School responses in New Jersey to the coronavirus (COVID-19) pandemic). The impacts of school closures on the students who now have a gap in their education is still largely unknown and unresearched.

For my analysis, I would like to first explore how the COVID-19 pandemic impacted Essex County, New Jersey and then focus on looking at how this then affected students of the public education system in this county. This is important to know how students were impacted, to know what obstacles they need to overcome, and for educators who are going to be working with this group of students in the future. The results of thai analysis can be used to guide educators and education administrators in making the decisions on how to deal with students who have been impacted, and how to handle events like this in the future.

I initially began by looking at how COVID-19 affected the entire county. I created a visualization to show the cumulative count of all confirmed COVID-19 cases in Essex County, New Jersey.  To better show the rate of the number of confirmed cases, I then created another graph to show the number of new daily cases in Essex County, New Jersey. This allowed me to begin to understand how COVID-19 impacted the entire county, and what the overall infection rate was like. I then used this information to help motivate and design how this large spike in cases impacted the educational system.

To tackle my research question of analyzing the impact of the COVID-19 pandemic on the public education system, I planned to utilize 3 key metrics of education: school enrollment, test scores, and graduation rates. Comparing the enrollment rates over the last three gives a sense of how many students are actually going to school. Looking at test scores allows us to gauge how students are performing and if their learning has been impacted by the absence of education. Graduation rates show the overall school completion, and if students are still completing on time. I plan to use these three metrics to assist in answering the high-level question of how students were impacted and obtain a sense of in what way in regards to these selected metrics.


## Data Sources
### Data Source #1: New Jersey State School Performance Report
Data Source: https://rc.doe.state.nj.us/

This data source was published by the New Jersey Department of Education and contains the public education metrics for all K-12 public schools in New Jersey, labeled by county. These reports are open to to the public and the policy posted on their website states that they can be freely "... used as a tool to help evaluate whether all students have equitable access to high quality education. We encourage you to use these reports to learn more, start conversations, and engage."

The data sets that I used in my analysis are the 2017-2018 Database_School Detail (Database_SchoolDetail17-18.xlsx), 2018-2019 Database_School Detail (Database_SchoolDetail18-19.xlsx), and the 2019-2020 Database_School Detail (Database_SchoolDetail19-20.xlsx). I imported these datasets in a notebook (notebooks/Education Data EDA & Merge.ipynb) and gathered and formatted the data that I needed for my final analysis. Although many school metrics were available, I decided to narrow my focus and only extract the school enrollments, test scores, and graduation rates for all school in Essex County, New Jersey. I then extracted these into a final dataset labeled, "education_data.csv", as well as three subsets for each metric of interest, to allow users to focus on only one metric, if interested. 


#### Education Data (education_data.csv)
This is the final dataset used for analysis, it is the cleaned and merged dataset resulting from the aggregation of the raw public education extracts. The columns of this dataset are: 

#### Enrollment Data (enrollment.csv)
This is the final average enrollment dataset, that contains the aggregated average enrollments by grade for all public schools in Essex County, New Jersey. The columns of this dataset are: 
1. Grade; This is the grade that we are looking at, options range from Preschool (GradePK) up to Grade 12. There is also an option for Total, which shows the total average enrollment for all grades.
2. 2018AvgEnrollment; This columns is a floating point value that displays the average enrollment for each grade in the 2017-2018 school year.
3. 2019AvgEnrollment; This columns is a floating point value that displays the average enrollment for each grade in the 2018-2019 school year.
4. 2020AvgEnrollment; This columns is a floating point value that displays the average enrollment for each grade in the 2019-2020 school year.

#### Test Scores Data (testScores.csv)
This is the final average high school test score dataset, that contains the aggregated average high school test score for all public schools in Essex County, New Jersey. The columns of this dataset are: 
1. TestType; This is a text column that cotains the  type of test, it includes options: 'ACT', 'SAT, or 'PSAT'.
2. TestSubject; This is a text column that contains the test subject, it includes options: 'Math', 'Reading', 'Science', or 'Reading and Writing'.
4. SchoolAverage; This is a floating point column that contains the average score for schools in Essex County, New Jersey.
5. StateAverage; This is a floating point column that contains the average score for the state of New Jersey.
6. TestYear; This is a year date column that contains the year the tests were taken.

#### Graduation Data (graduationRates.csv)
This is the final graduation rates dataset, this contains the percentage of highschool graduation aggregated to show the total percentage of graduation for all schools in Essex County, New Jersey for students in the 4 and 5 -year cohorts. 
1. GraduationCohortYear; This is a year date column that ranges from 2016-2020.
2. GraduationRateType; This is a text column that displays the cohort type (4-Year Rate or 5-Year Rate).
3. GraduationRate; This is a floating point column that displays the average graduation rate.

### COVID-19 Data
I initially began by looking at how COVID-19 affected the entire county. To find out how the county was impacted I reviewed the number of confirmed cases, and the number of new daily cases in Essex County, New Jersey. I also looked at the timeline of policys that were put in place such as masking mandates, and how often they were worn, to view any correlations between how the entire country was impacted. There were several datasets that I used for this analysis.

#### COVID-19 Data From John Hopkins University (RAW_us_confirmed_cases.csv)
The cumulative confirmed case counts for where gathered from the Kaggle repository of John Hopkins University COVID-19 raw United States confirmed cases dataset.
Data Source: https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv

#### U.S. State and Territorial Public Mask Mandates From April 10, 2020 through August 15, 2021 by County by Day (mask-use-by-county.csv)
The data for masking mandates was sourced from the CDC dataset of masking mandates by county.
Data Source: https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i.

#### Mask-Wearing Survey Data by Josh Katz, Margot Sanger-Katz and Kevin Quealy
The data from this survey was gathered from a large number of online surveys conducted by the survey firm Dynata where participants answered about how often they wear a mask in public when within six feet of another person, selecting from the following options: always, frequently, sometimes, rarely, and never. The survey includes responses from 250,000 global users in July 2020.
Data Source: https://github.com/nytimes/covid-19-data/tree/master/mask-use

## Findings
Visualizing the number of confirmed COVID-19 cases and the new daily case count in Essex County, New Jersey, we can see that the number of cases is exceedling high. There is a large spike in the number of cases of COVID-19 in March 2020, which helps to explain the motivation for educators to make the hard decision of closing all schools for the remainder of  the year. We can see that after a steep decline during the summer, there is yet another spike in the number of new cases when schools reopen in the fall of 2020.
![image](https://user-images.githubusercontent.com/73403238/145731234-9b57cf92-9f23-4e9a-a9e8-68a52b1f4099.png)
Figure 1: COVID-19 Confirmed Cases and New Daily Case Count in Essex County, New Jersey

#### Student Enrollment
Reviewing student enrollment, on average there was not a significant change between grades for the varying school years. The three grades that displayed the most change were grades 3, 6, and 7. When comparing the 2018-2019 and 2019-2020 school years, Grade 3 displayed an average decrease of 7 students per school, Grade 6 had an average decrease of 2 students per school, and Grade 7 actually had an average increase of 1 student per school. Overall, these results did not show any significant change in the average school enrollment over the last 3 school years, and COVID-19 does not seem to have an impact on the 2019-2020 average school enrollment.
![image](https://user-images.githubusercontent.com/73403238/145731236-91f99247-71f2-4537-a571-02a2e7d5440e.png)
Figure 2: Student Enrollment by Grade
This visualization is filtered to display the grades with the greatest change in average school enrollment, grades 3, 6, and 7.

#### Test Scores
Overall, there does not appear to be any significant change in average school test scores for schools in Essex County, New Jersey. When comparing the 2019-2020 COVID-19 impacted school year to the previous two school years, there weren't really any clear distinctions. The group with the largest change in test score was the math subject. When comparing average test scores for 2018-2019 and 2019-2020, I found that the average ACT score decreased by 0.29, the average SAT score decreased by 5.09, while the average PSAT actually increased by 1.99.
![image](https://user-images.githubusercontent.com/73403238/145731240-e80cf955-9189-454f-b7d1-614426652139.png)
Figure 3: Average Math Test Scores by School Year

#### Graduation Rates
Overall, graduation rates show a steady upward trend over the last 5 years. The 2019-2020 COVID-19 pandemic impacted school year did not appear to disrupt this trend. Comparing the 2019 and 2020 graduation rates, the data shows a slight increase of 0.7% in average graduation rate for schools in Essex County, New Jersey.
![image](https://user-images.githubusercontent.com/73403238/145731247-d7c69e25-82b2-4ec0-81c4-59e05b8b45f0.png)
Fig 4: Graduation Rates for 4-Year and 5-Year Cohorts, 2016-2020.

Accumulating all of the above metrics into a final dashboard, there does not appear to be any significant change in the education when comparing previous school years to the 2019-2020 COVID-19 impacted school year. 

![image](https://user-images.githubusercontent.com/73403238/145729838-d7c05b1a-f563-49eb-ad2c-91cab57c9121.png)
Figure 5: Final Dashboard, 'Impact of COVID-19 on Education in Essex County, New Jersey' that is published on Tableau Public: https://public.tableau.com/views/TheImpactofCOVID-19onEducationinEssexCountyNewJersey


## Discussion/Implications
The analysis that I performed above is significant because it is important for educators and education policymakers to understand the impacts of school closures, to help them with  better decision making in the future. This also helps guide educators and education policy makers to understand what efforts will be needed in order to help students reach their benchmarks after a leave of absence, such as more assistance and tutoring fors specific subjects or investment in helping student graduation.  
Although I was not able to find any significant results in the impact of COVID-19 on education, when comparing the 2019-2020 school year to previous years, the analysis that I performed can be applied in the future, as more data becomes available. Incorporating the 2020-2021 and future academic years into my dashboard would allow users to investigate the long term impacts of school closures and pandemics. 


## Limitations
There were many potential issues and limitations to the dataset that I used. Due to the COVID-19 pandemic, there were cancellations of several tests and changes in testing requirements. Unfortunately, this was not well documented and varied significantly between schools. Another known issue in the dataset is delays in graduation and changes in graduation requirements due to COVID-19. This is also not well documented, and varies greatly between school, and individuals. Overally, schools administered different policies when it came to how they handled the pandemic, and it is difficult to take into account these variances when aggregating to an average level for the county.
Ideally this analysis would contain data from the 2020-2021 school year and beyond, to review how COVID-19 continues to impact education. Currently, the only data publicly available goes up to the 2019-2020 school year. Another limitation to the data is this only reviews the public school data, as private and homeschooled students do not have their data so easily available.


## References
2021 building a grad nation report. America's Promise. (n.d.). Retrieved December 10, 2021, from https://www.americaspromise.org/report/2021-building-grad-nation-report.
Centers for Disease Control and Prevention. (n.d.). U.S. state and territorial public mask mandates from April 10, 2020 through August 15, 2021 by County by day. Centers for Disease Control and Prevention. Retrieved December 10, 2021, from https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i.
Chatterji, P., & Li, Y. (2021, May 7). Effects of covid-19 on school enrollment. Economics of Education Review. Retrieved December 10, 2021, from https://www.sciencedirect.com/science/article/pii/S0272775721000479.
Kuhfeld, M., Soland, J., Tarasawa, B., Johnson, A., Ruzek, E., & Lewis, K. (2020, December 3). How is covid-19 affecting student learning? Brookings. Retrieved December 10, 2021, from https://www.brookings.edu/blog/brown-center-chalkboard/2020/12/03/how-is-covid-19-affecting-student-learning/.
School responses in New Jersey to the coronavirus (COVID-19) pandemic. Ballotpedia. (n.d.). Retrieved December 10, 2021, from https://ballotpedia.org/School_responses_in_New_Jersey_to_the_coronavirus_(COVID-19)_pandemic#Timeline_by_school_year. 
