---
layout: post
title: "HR Dashboard: Comprehensive Data Visualization with Tableau"
date: 2025-06-17 02:20 +0300
categories: [Data Visualization, Tableau, HR Analytics]
tags: [data analysis, dashboard design, human resources, trends, insights, workforce analytics]
excerpt: "This project highlights hands-on experience in building comprehensive HR data visualizations using Tableau, transforming raw data into actionable insights and a published, interactive dashboard."
---

1. ## **Introduction** {#introduction}

   This week’s assignment focused on building data visualizations using
   Tableau. Tableau is a powerful data visualization tool used to represent
   information and data graphically, making it easy to understand trends,
   outliers in data. It transforms raw data into easily digestible visual
   formats like charts, graphs, and maps, enabling users to explore and
   analyze data effectively. Through this assignment, I developed hands-on
   experience putting together powerful visualizations using Tableau and
   have published my work on the cloud. The link for this project was
   sourced from [Tableau HR Project](%20https://www.datawithbaraa.com/tableau/tableau-hr-project-thank-you/%20)

   The purpose of the assignment was to gain hands-on practice:

   1. Understanding the business and client needs.
   2. Loading Data.
   3. Transforming Data.
   4. Creating Calculated Measures.
   5. Visualizing the dashboard.
   6. Publishing my project as part of my portfolio collection.

2. ## **Tasks to be completed** {#tasks-to-be-completed}

   1. ### **User Story-HR Dashboard** {#user-story-hr-dashboard}

      As an HR manager, I want a comprehensive dashboard to analyze human resources data, providing both summary views for high-level insights and detailed employee records for in-depth analysis.

	1. ### **Summary View** {#summary-view}

		The summary view should be divided into three main sections: Overview, Demographics, and Income Analysis.

		2. #### **Overview**  {#overview}

			The Overview section should provide a snapshot of the overall HR metrics, including
			* Display the total number of hired employees, active employees, and terminated employees.
			* Visualize the total number of hired and terminated employees over the years.
			* Present a breakdown of total employees by department and job titles.
			* Compare the total employees between the headquarters (HQ) and the branches (New York is the HQ)
			* Show the distribution of employees by city and state.


		3. #### **Demographics** {#demographics}

			The Demographics section should offer insights into the composition of the workforce, including:
			* Present the gender ratio in the company.
			* Visualize the distribution of employees across age groups and education levels.
			* Show the total number of employees within each age group.
			* Show the total number of employees within each education level.
			* Present the correlation between employees’ educational backgrounds and their performance ratings.

		4. #### **Income** {#income}

			The income analysis section should focus on salary-related metrics,
			Including:
			* Compare salaries across different education levels for both genders to identify any discrepancies or patterns.
			* Present how the age correlates with the salary for employees in each department.


	2. ### **Employee Records View** {#employee-records-view}

		* Provide a comprehensive list of all employees with necessary information such as name, department, position, gender, age, education, and salary.
		* Users should be able to filter the list based on any of the available columns.


3. ## **Dashboard design and implementation** {#dashboard-design-and-implementation}

   The HR dashboard is divided into distinct views to cater to different levels of analytical depth required by the HR manager. Each view is designed for clarity, interactivity, and effective communication of insights.


   1. ### **Summary View I: Overview Dashboard** {#summary-view-1:-overview-dashboard}

      The overview dashboard provides a snapshot of the essential HR metrics, offering quick insights into the overall state of the workforce.

		1. #### **Employee Headcount Summary** {#employee-headcount-summary}

			Displays the total number of currently active employees along with the total number of employees hired and terminated throughout the entire dataset. This provides a clear top-line view of workforce dynamics.
			![][image1]  *Figure 1. Employee Headcount*



		2. #### **Historical hiring and termination trends** {#historical-hiring-and-termination-trends}

			It visualises the evolution of hiring and termination activities year over year. This allows for the identification of patterns, periods of significant growth, or challenges in employee retention over time.
			![][image2]*Figure 2\. Historical hiring and termination trends*


		3. #### **Departmental and Job Title Breakdown** {#departmental-and-job-title-breakdown}

			Presents detailed breakdowns showing the number of employees within each department and across various job titles. This helps in understanding organizational structure and resource allocation.![][image3]*Figure 3\. Departmental and Job Title Breakdown*

		4. #### **Headquarters vs Branches comparison** {#headquarters-vs-branches-comparison}

			Provides a direct comparison of total employee counts between Nairobi and all other branches, highlighting the proportion of the staff present in Nairobi and those outside Nairobi.
			![][image4]*Figure 4\. Headquarters vs Branches comparison*


		5. #### **Geographic Employee Distribution** {#geographic-employee-distribution}

			Shows the employee spread across the different cities and states. This offers insights into regional workforce presence and potential talent pools.![][image5]*Figure 5\. Geographic Employee Distribution*

   2. ### **Summary view II: Demographics Dashboard** {#summary-view-2:-demographics-dashboard}

      This dashboard delves into the composition of the workforce, offering insights into diversity and employee characteristics.

      1. #### **Gender ratio** {#gender-ratio}

         The pie chart illustrates the gender balance within the company, providing a quick assessment of diversity.![][image6]*Figure 6\. Gender ratio*


      2. #### **Age group and educational level distribution** {#age-group-and-educational-level-distribution}

         Bar charts and the highlight table show the distribution of employees across various age groups and education levels, helping to understand workforce demographics.
         ![][image7]*Figure 7\. Age group and educational level distribution*


      3. #### **Education vs Performance correlation** {#education-vs-performance-correlation}

         The highlight table shows the relationship between employees’ educational backgrounds and their performance ratings, potentially revealing a correlation for talent management strategies.
         ![][image8]*Figure 8\. Education vs Performance correlation*



   3. ### **Summary View III: Income analysis dashboard** {#summary-view-3:-income-analysis-dashboard}

      This dashboard focuses on salary-related metrics, crucial for understanding compensation equity and patterns.

      1. #### **Salary comparison by education and gender** {#salary-comparison-by-education-and-gender}

			A barbell chart was used to compare salaries across different education levels for both genders. This was designed to identify potential discrepancies, pay gaps, and unique compensation patterns.![][image9]*Figure 9\. Salary comparison by education and gender*



	   2. #### **Age vs. Salary by Job Title Correlation** {#age-vs.-salary-by-job-title-correlation}
	   		A scatter plot was used to explore the correlation between age and salary for employees within each department, providing insights into career progression and salary structures.![][image10]*Figure 10\. Age vs. Salary by Job Title Correlation*



   4. ### **Employee Records View: HR Details Dashboard** {#employee-records-view:-hr-details-dashboard}

      To complement the summary dashboards, the employee records view provides the HR manager with comprehensive, detailed information about individual employees.

      1. #### **Comprehensive employee list** {#comprehensive-employee-list}

		A detailed table displays all employees, including essential information such as name, department, job title, gender, age, education, and salary.![][image11]*Figure 11\. Comprehensive employee list*



      2. #### **Interactive filtering** {#interactive-filtering}

         Users can dynamically filter this list based on any of the available filters, including demographics, role, geographics, salary, status, and length of employment, which enables quick access to specific subsets of employee data for in-depth analysis or human resource operations.![][image12]*Figure 12\. Interactive filters in action*

		 ![][image13] *Figure 13\. Interactive filters turned off*

4. ## **Key Learnings and Insights** {#key-learnings-and-insights}

   This project highlighted the power of data visualization in HR. Through the Tableau dashboards, essential insights were discovered, including:

   1. #### **Dashboard section: Overview** {#dashboard-section:-overview}

		* The company currently has 7950 active employees. The analysis of the total hired (8950 employees) vs terminated (1000 employees) indicates a significant net growth in the workforce.
		* The departments section inside the overview section of the dashboard shows the operations department with 2417 employees as being the largest department, followed by sales and customer service departments coming in second and third, respectively, showing a heavily customer-facing and operational business model
		* The hired vs terminated charts suggest consistent hiring activity across years.
		* Geographical distribution highlights the dominance of the Nairobi HQ branch with regard to employee concentration, confirming the HQ’s role in the organization’s operation and staffing.

    2. #### **Dashboard section: Demographics**  {#dashboard-section:-demographics}

		* The ratio of men to women percentage-wise is 54% men and 46% women, indicating that the male employees are slightly higher than the female employees in the organization.
		* The majority of employees' level of education is a Bachelor's degree, and they are in the 35 to 44 age group.
		* 50% of the employees across all educational backgrounds (High School, Bachelor's, Master's, PhD) achieved a Good performance rating.


	3. #### **Dashboard section: Income** {#dashboard-section:-income}

		* For employees who were hired with only a high school level as their highest educational background, they were paid almost similarly regardless of their gender. As for employees at the Bachelor’s and Master’s level of education, the male employees in this case had a slight advantage, but at the PhD level, women employees were paid significantly more than their male counterparts.
		* The scatter plot showed a positive correlation between employee age and salary, that is, as the employee gains more experience and seniority, their compensation tends to increase. However, there are some significant variations, including that Finance and IT managers are prominent outliers, showing high salaries as compared to the average.
		* The outliers indicate that the IT and Finance managerial positions are highly compensated positions.
		* Looking at the age group of HR assistants who are positioned at the lower end of the salary spectrum, as compared to the HR manager who commands a competitive salary even at a younger age, indicating that although age broadly influences salary, specific job functions and their market value play a more defining role in compensation levels.

5. ## **Link to Tableau Dashboard** {#link-to-tableau-dashboard}


	[Uel Kariuki Tableau Dashboard Link](https://public.tableau.com/views/HRdashboard_17501123868440/HRSummary?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)




6. ## **Conclusion** {#conclusion}

   This comprehensive data visualization project on HR analytics was an immensely valuable and hands-on experience, navigating the entire Tableau process from raw data to actionable insights. I gained extensive practical experience in connecting to and preparing diverse HR datasets, building a comprehensive suite of visualizations across multiple sheets, structuring them into cohesive dashboards, and designing a compelling and interactive user experience. This process revealed critical insights into workforce demographics, hiring and termination trends, departmental allocation, and compensation patterns within human resources, directly addressing the HR managers' needs and enabling informed decision making. This end-to-end development project has significantly enhanced my skills in Tableau, data preparation, advanced data visualization, interactive dashboard design, and translating business requirements into impactful data-driven solutions, thereby strengthening my portfolio for future data and AI opportunities.


[image1]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/1.1_employee_count.png
[image2]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/1.2%20trends%20hiring.png
[image3]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/1.3%20departmental.png
[image4]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/1.4%20location.png
[image5]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/1.5%20geographical.png
[image6]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/2.1%20gender%20ratio.png
[image7]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/2.2%20education%20and%20age.png
[image8]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/2.3%20education%20and%20performance.png
[image9]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/3.1%20education%20and%20gender.png
[image10]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/3.2%20age%20and%20salary.png
[image11]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/4.1%20comprehensive%20list.png
[image12]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/4.2%20filters%20in%20action.png
[image13]:/assets/images/Projects/HR-Dashboard/screenshots_tableau/4.2.1%20filters%20turned%20off.png











