# Data Science Salary Dashboard
![image](https://github.com/user-attachments/assets/2ee35b3a-dbe3-43ca-8daf-b5cad316bf05)

## Introduction 

This Data Science Salary Dashboard was created to help job seekers explore salary trends across various data-related roles. It provides an interactive overview of salaries and other job features to ensure candidates are well-informed when assessing job opportunities.

## Dashboard File

### Key Excel skills utilized to build this dashboard include:

📊 Charts: Used bar and map charts for visual analysis.

🧮 Formulas and Functions: Calculated median salaries and job counts.

❎ Data Validation: Restricted inputs for fields like Job Title, Country, and Type.

## Data Jobs Dataset

### The data, sourced from 2023 job listings, includes real-world information on:

👨‍💼 Job Titles

💰 Salaries

📍 Locations

🔗 Job Types and Platforms

🛠️ Skills

## Dashboard Interaction Guide

Users can interact with the dashboard by selecting different filters for job title, country, job type, and degree requirements. 
This allows them to dynamically explore the data and view specific insights tailored to their interests, such as comparing median salaries for different job titles in a specific country or analyzing job types that offer remote work.

## Excel Features and Techniques
### Bar Charts: 
Used for comparing salaries across job titles.

### Map Chart: 
Displays salary distribution by country.

### Formulas: 
Employed to calculate median salaries and filter data by multiple criteria.

### Data Validation: 
Restricted entries for interactive filtering, ensuring data consistency.

## Dashboard Components

### Job Title Analysis
![image](https://github.com/user-attachments/assets/a2caee0d-e93b-48ff-9c56-7ac128fc1dfc)

A bar chart shows the median salary for each job title, sorted in descending order based on selected variables (excluding job type). Higher salaries tend to be seen in engineering and senior positions.

### Country and Job Type

A map displays median salaries by country, highlighting regions with the highest and lowest wages. Job types are categorized to illustrate median salaries for each type (e.g., Full-time, Contractor).

### Remote Work and Degree Requirements
![image](https://github.com/user-attachments/assets/d87fcecb-0628-41b8-82d6-222ba613bd3a)

Visualizations show the differences in median salary between roles that allow remote work and those that don’t, as well as between jobs that mention degree requirements and those that do not.

## Summary Statistics

### Median Salary: 
Displays the median salary for the selected job title.

### Top Hiring Country: 
![image](https://github.com/user-attachments/assets/6af810bc-ba0c-4e22-9626-33143a5e5d1b)

Shows the country with the highest job count based on selected dashboard variables (excluding the country variable).

### Remote Job Percentage: 
![image](https://github.com/user-attachments/assets/aef16c70-4bf7-43f4-80b2-f2e31dcfc8a1)

Indicates the share of roles that allow remote work, accounting for other selected variables.

## Special Functions Used

### SUMPRODUCT: 
	SUMPRODUCT(
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
	) 
Calculated the percentage of job listings that allow remote work based on all selected criteria, providing insight into the flexibility of job opportunities.

### MEDIAN: 
	MEDIAN(
  	IF(
    (jobs[job_title_short] = A2) *
    (jobs[job_country] = country) *
    (ISNUMBER(SEARCH(type, jobs[job_schedule_type]))) *
    (jobs[job_no_degree_mention] = degree) *
    (jobs[job_work_from_home] = home) *
    (jobs[salary_year_avg] <> 0),
    jobs[salary_year_avg] ))
Computed the median salary for filtered job roles according to the user-selected criteria, ensuring an accurate representation of salary distributions.

![image](https://github.com/user-attachments/assets/1f08e1ce-3feb-4d16-a5a7-86dd8b603700)


### XLOOKUP:
	XLOOKUP(title,$D$2:$D$11,$E$2:$E$11)
Retrieved data based on the user-selected variable, such as median salary for a specific role or job count in a specific country, enhancing the dashboard's interactivity.

![image](https://github.com/user-attachments/assets/19861512-05ac-4582-ac74-5f6c58701b85)


### INDEX and MATCH: 
	INDEX(A2#, MATCH(MAX(C2:C112),C2:C112, 0))
Identified the country with the highest number of job postings according to the user's selected variables, highlighting regions with the most opportunities.

### SUBSTITUTE
	SUBSTITUTE(D2,"via ",""):
Displayed the job site name without the word "via," streamlining the presentation of job listings.

![image](https://github.com/user-attachments/assets/b6efe588-4411-4bde-b875-9c82baee8d30)


## Conclusion
The dashboard provides an overview of salary trends in data-related fields, showing that geographic location, job type, and flexibility (such as remote work) significantly impact salary levels.

These insights can help job seekers consider their next career steps and make data-driven decisions.


##### This Dashboard inspired by "Excel for Data Analytics" by Luke Barousse, enhances the original concept by incorporating additional variables, graphs, and KPIs
