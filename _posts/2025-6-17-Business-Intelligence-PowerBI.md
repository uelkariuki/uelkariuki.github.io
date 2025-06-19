---
layout: post
title: "Business Intelligence in Hotel Management: A Power BI Project"
date: 2025-06-17 01:38 +0300
categories: [Data Analysis, Business Intelligence, Power BI, Hotel Management]
tags: [data visualization, data modeling, DAX, Power Query, hospitality, analytics]
description: "A comprehensive Business Intelligence project focusing on hotel management, utilizing Power BI to transform raw data into actionable insights and a compelling interactive dashboard."
---


## **Introduction**

This week’s assignment focused on Business Intelligence using Power BI, which refers to the practice of utilizing Microsoft Power BI as the primary platform and set of tools to implement business intelligence processes within an organization. Through this assignment, I gained hands-on experience in Business Intelligence using Power BI for hotel management and published my work on the cloud. The link to the [Hospitality Domain Data Analyst Project](https://codebasics.io/resources/end-to-end-data-analyst-project%20%20).

The purpose of this assignment was to gain hands-on practice in:

1. Understanding the Hotel business and client needs
2. Loading Data
3. Transforming Data
4. Building DAX
5. Visualizing the Dashboard
6. Publishing the project as part of my portfolio collection

## **Tasks completed**

1. ### **Data Loading and Transformation**

   The first step was to bring in the raw data, and for it to be usable for analysis, it needed to be thoroughly cleaned and shaped. At this stage, the focus was on ensuring data quality and consistency, which laid a solid foundation for the entire project.
   I loaded the various CSV files into Power BI Desktop, which included *dim\_date, dim\_rooms, dim\_hotels, fact\_bookings,* and *fact\_aggregated\_bookings*. Once loaded, the Power BI query editor became the primary tool for data transformation. Here, I focused on crucial steps, including standardizing the data types, where I made sure each column had the correct data type to prevent calculation errors and ensure accurate interpretation.
   I also cleaned and shaped the data, which involved removing unnecessary columns, renaming fields for clarity. By applying these steps, the raw data was transformed into a clean, structured, and reliable format ready for the next phase of data modeling.![][image1]



2. ### **Data Model Design (Star Schema)**

   After data transformation, a robust data model was built using the star schema design, and it was chosen for its efficiency and clarity. The model centers around *fact\_bookings* as the primary fact table, supplemented by *fact\_aggregated\_bookings* for summarized analysis. Surrounding these are key dimension tables: including d*im\_hotel, dim\_rooms,* and *dim\_dat*e.
   Relationships were established to connect these tables effectively, for instance, *dim\_hotel* links to both *fact\_bookings* and *fact\_aggregated bookings* via  *property\_id*. *dim\_rooms* connects to *fact\_bookings* using *room\_category*, which maps to *room\_id* in *dim\_rooms*. Crucially, *dim\_dates* links to *fact\_bookings* via *check\_in\_date*, and also connects to *fact\_aggregated\_bookings* through its *check\_in\_date*. All these relationships are active and defined as one-to-many, ensuring correct data propagation and filtering across the model.
   This star schema is fundamental to Power BI's performance, as it optimizes how data is filtered and aggregated, ensuring efficient query execution. It also ensures that all subsequent DAX calculations provide accurate and reliable results by correcting propagating filters across related tables.
   ![][image2]![][image3]


3. ### **Data Analyisis Expressions(DAX)**

   With the robust data model established, the next step involves leveraging Data Analysis Expressions (DAX) to create powerful custom calculations. These new measures and calculated columns were essential for extending the analytical capabilities of the model, enabling deeper insights tailored to specific hotel business needs and driving effective visualization.
   A comprehensive suite of around 26 DAX measures was developed. These were instrumental in transforming raw data into actionable key performance indicators and detailed analytical metrics. The measures broadly fell into several categories designed to address core hotel business operations:
	* Core performance indicators: Measures like *ADR*(Average Daily Rate), *Revenue*, *Total bookings*, *Occupancy%* , and *RevPAR* (Revenue Per Available Room) were created to provide a high-level overview of operational and financial health.
	* Rate and ratio analysis: DAX was used to derive critical percentages such as *Booking % by Platform*, *Cancellation %*, *No show rate %*, and *Realization %*, offering insights into efficiency and specific operational areas.
	* Time intelligence and trend analysis: A significant portion of the DAX focused on time-based comparisons, including *ADR WoW change %*, *Revenue WoW change %*, *Occupancy WoW change %*, and *Revpar WoW change %*, enabling week-over-week performance tracking and trend identification.
	* Operational volume metrics: Measures like *DBRN*, *DSRN,* and *DURN* provided insights into daily booked, sold, and used room nights, respectively.

	![][image4]

	* Occupancy%: Occupancy means the total successful bookings that happened to the total rooms available(capacity)

	![][image5]

	* ADR(Average Daily Rate): It is the ratio of revenue to the total rooms booked/sold. It is the measure of the average paid for rooms sold in a given period.![][image6]
	* DSRN: (Daily Sellable Room Nights): This metric tells, on average, how many rooms are ready to sell for a day, considering a time period.

	![][image7]

	* Revenue: To get the total revenue realized.
	![][image8]



	This comprehensive set of measures forms the analytical backbone of the dashboard, allowing for dynamic calculations and personalized insights essential for data-driven decision making.

4. ### **Dashboard Design and Visualization**

   The ultimate objective of this project was to translate complex data analysis into a compelling and interactive dashboard report, designed to provide clear, actionable insights for strategic decision-making in the hotel business. The dashboard was meticulously crafted to ensure both visual appeal and high functionality, empowering users to intuitively explore the data and understand key performance drivers.
   The dashboard's clean layout and intuitive design prioritize quick insights. Prominent slices at the top allow users to dynamically filter data by city, room type, and specific date ranges, for instance, May 25, June 25, July 25, and week numbers (W19-W31), enabling highly personalized exploration.
   The core of the dashboard's immediate value lies in a strategic arrangement of visuals:
	* Key performance indicators (KPI): the **top left** section features prominently displayed card visuals for crucial metrics such as Revenue,  RevPAR, DSRN,  Occupancy %, ADR, and Realization %. Each KPI also includes a clear week-on-week change indicator, providing an immediate understanding of recent performance shifts.

	![][image9]

	* Revenue segmentation: the donut chart ‘revenue by category’ on the **right** clearly illustrates the percentage contribution of different booking categories, for instance, Luxury and Business, allowing for quick assessment of revenue distribution.

	![][image10]



	* Performance trends: below the category breakdown, the line chart trend by key metrics visualizes RevPAR and occupancy % over selected weeks. This visual is essential for identifying seasonal patterns, performance growth, or declines over time.

	![][image11]

	* Platform performance analysis: the combined bar and line chart for realization % and ADR by platform (bottom left) provides a detailed comparison of performance across various booking platforms, for instance, logtrip, direct online, and tripster. This helps in evaluating channel effectiveness and optimizing market strategies.

	![][image12]

	* Detailed property breakdown: a comprehensive table titled ‘property by key matrix’ (bottom-right) presents granular data for each property\_id, including Revenue, Total bookings,  RevPAR, Occupancy %, and various DBRN or DSRN, or DURN metrics. This detailed view supports in-depth analysis and specific property management decisions.

	![][image13]

	* Daytime performance: a smaller table within the left panel breaks down key metrics by Day type, for instance, weekday, weekend, offering additional insights into operational patterns.

	![][image14]

	Ultimately, this interactive dashboard serves as a powerful tool for hotel management, enabling them to quickly identify performance drivers, understand booking behaviors, monitor key operational metrics, and make data-driven decisions that can lead to optimized revenue, improved guest satisfaction, and enhanced operational efficiency across their properties and booking platforms.

	![][image15]

5. ### **Publication and Sharing**

   The final step involved publishing and sharing the interactive dashboard. This phase is crucial as it transitions the analysis from a development environment to a live,  accessible platform, ensuring that the insights generated are available to relevant stakeholders for data-driven decision-making.

6. ### **Link to Power BI Dashboard**

	[Uel Kariuki PowerBI Dashboard link](https://drive.google.com/file/d/1gjHLdk3S59w0-qycTwo5QTGYIETzz9v8/view?usp=drive_link)


7. ## **Conclusion**

This comprehensive Business Intelligence project on hotel management was an immensely valuable and hands-on experience, navigating the entire Power BI pipeline from raw data to actionable insights. I gained extensive practical experience in data loading and rigorous transformation using Power Query, building a robust star schema data model, developing a wide array of DAX expressions to derive key business metrics, and designing a compelling and interactive dashboard. This process successfully revealed critical insights into booking trends, platform performance, revenue drivers, and operational efficiencies within the hotel business, directly addressing client needs and informed decision making. This end-to-end development journey has significantly enhanced my skills in Power BI, data modeling, advanced DAX,  data visualization, and translating business requirements into impactful analytical solutions, thereby strengthening my portfolio for future data and AI opportunities.

[image1]: /assets/images/Projects/Business-Intelligence-PowerBI/1.1__power_bi_query_editor.png
[image2]:/assets/images/Projects/Business-Intelligence-PowerBI/1.2_data_model_relationshiops_1.png
[image3]: /assets/images/Projects/Business-Intelligence-PowerBI/1.3_data_model_relationships_2.png
[image4]: /assets/images/Projects/Business-Intelligence-PowerBI/1.4_sample_dax.png
[image5]: /assets/images/Projects/Business-Intelligence-PowerBI/1.5_4_dax.png
[image6]: /assets/images/Projects/Business-Intelligence-PowerBI/1.6.1_1_dax.png
[image7]: /assets/images/Projects/Business-Intelligence-PowerBI/1.7.2_2_dax.png
[image8]: /assets/images/Projects/Business-Intelligence-PowerBI/1.8_dax.png
[image9]: /assets/images/Projects/Business-Intelligence-PowerBI/1.8.1.1_revenue_and_revpar.png
[image10]: /assets/images/Projects/Business-Intelligence-PowerBI/2.1_%25_revenue_by_category.png
[image11]: /assets/images/Projects/Business-Intelligence-PowerBI/2.2_trend_by_key_metrics.png
[image12]: /assets/images/Projects/Business-Intelligence-PowerBI/2.3_realisation_%25_and_ADR_by_platform.png
[image13]: /assets/images/Projects/Business-Intelligence-PowerBI/2.4_property_by_key_metrics.png
[image14]: /assets/images/Projects/Business-Intelligence-PowerBI/2.5_day_type.png
[image15]: /assets/images/Projects/Business-Intelligence-PowerBI/2.6_final_dashboard.png
