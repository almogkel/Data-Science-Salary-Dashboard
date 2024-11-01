# Data Science Salary Dashboard

Introduction
This Data Science Salary Dashboard was created to help job seekers explore salary trends across various data-related roles. It provides an interactive overview of salaries and other job features to ensure candidates are well-informed when assessing job opportunities.

Dashboard File

Key Excel skills utilized to build this dashboard include:
📊 Charts: Used bar and map charts for visual analysis.
🧮 Formulas and Functions: Calculated median salaries and job counts.
❎ Data Validation: Restricted inputs for fields like Job Title, Country, and Type.

Data Jobs Dataset
The data, sourced from 2023 job listings, includes real-world information on:
👨‍💼 Job Titles
💰 Salaries
📍 Locations
🔗 Job Types and Platforms
🛠️ Skills

Dashboard Interaction Guide
Users can interact with the dashboard by selecting different filters for job title, country, job type, and degree requirements. 
This allows them to dynamically explore the data and view specific insights tailored to their interests, such as comparing median salaries for different job titles in a specific country or analyzing job types that offer remote work.

Dashboard Components
Job Title Analysis
A bar chart shows the median salary for each job title, sorted in descending order based on selected variables (excluding job type). Higher salaries tend to be seen in engineering and senior positions.

Country and Job Type
A map displays median salaries by country, highlighting regions with the highest and lowest wages. Job types are categorized to illustrate median salaries for each type (e.g., Full-time, Contractor).

Remote Work and Degree Requirements
Visualizations show the differences in median salary between roles that allow remote work and those that don’t, as well as between jobs that mention degree requirements and those that do not.

Summary Statistics
Median Salary: Displays the median salary for the selected job title.
Top Hiring Country: Shows the country with the highest job count based on selected dashboard variables (excluding the country variable).
Remote Job Percentage: Indicates the share of roles that allow remote work, accounting for other selected variables.
Excel Features and Techniques
Bar Charts: Used for comparing salaries across job titles.
Map Chart: Displays salary distribution by country.
Formulas: Employed to calculate median salaries and filter data by multiple criteria.
Data Validation: Restricted entries for interactive filtering, ensuring data consistency.

Special Functions Used

1. SUMPRODUCT(
    (jobs[job_title_short] = title) *
    (jobs[job_country] = country) *
    (ISNUMBER(SEARCH(type, jobs[job_schedule_type]))) *
    (jobs[job_no_degree_mention] = degree) *
    (jobs[job_work_from_home] = A3) *
    (jobs[salary_year_avg] <> 0)
) /
SUMPRODUCT(
    (jobs[job_title_short] = title) *
    (jobs[job_country] = country) *
    (ISNUMBER(SEARCH(type, jobs[job_schedule_type]))) *
    (jobs[job_no_degree_mention] = degree) *
    (jobs[salary_year_avg] <> 0)
):
Calculated the percentage of job listings that allow remote work based on all selected criteria, providing insight into the flexibility of job opportunities.

2. MEDIAN(
  IF(
    (jobs[job_title_short] = A2) *
    (jobs[job_country] = country) *
    (ISNUMBER(SEARCH(type, jobs[job_schedule_type]))) *
    (jobs[job_no_degree_mention] = degree) *
    (jobs[job_work_from_home] = home) *
    (jobs[salary_year_avg] <> 0),
    jobs[salary_year_avg] )):
Computed the median salary for filtered job roles according to the user-selected criteria, ensuring an accurate representation of salary distributions.

3. XLOOKUP(title,$D$2:$D$11,$E$2:$E$11):
Retrieved data based on the user-selected variable, such as median salary for a specific role or job count in a specific country, enhancing the dashboard's interactivity.

4. INDEX(A2#, MATCH(MAX(C2:C112),C2:C112, 0)):
Identified the country with the highest number of job postings according to the user's selected variables, highlighting regions with the most opportunities.

5. SUBSTITUTE(D2,"via ",""):
Displayed the job site name without the word "via," streamlining the presentation of job listings.

Conclusion
This dashboard provides a comprehensive view of salary trends across 
The dashboard provides an overview of salary trends in data-related fields, showing that geographic location, job type, and flexibility (such as remote work) significantly impact salary levels. These insights can help job seekers consider their next career steps and make data-driven decisions.
