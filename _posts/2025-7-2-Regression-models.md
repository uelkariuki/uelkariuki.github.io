---
layout: post
title: "House Price Prediction: A Linear Regression Modeling Project"
date: 2025-07-02 18:10:00 +0300
categories: [Machine Learning, Data Science, Regression]
tags: [Linear Regression, Scikit-learn, Data Preprocessing, Model Evaluation, Python, Data Visualization]
description: "A comprehensive report detailing the process of building, evaluating, and visualizing simple and multi-variate linear regression models for house price prediction."
---

1. ## **Introduction**

   This week’s assignment focused on building a Linear Regression model using Python. A linear regression model refers to a statistical method that examines the relationship between a dependent variable and one or more independent variables by fitting a linear equation to observed data.I explored a dataset, trained and tested the model, and visualized the results. The required dataset was provided in the link [Linear Regression dataset](https://drive.google.com/drive/u/0/folders/1ljnoug9AkHvZu5YZME6nXay5w-noGyIg). The purpose of the assignment was to gain hands-on practice in:
	1. Exploring a real-world dataset
	2. Preparing and splitting data for training and testing
	3. Building a simple linear regression model
	4. Evaluating the model using key metrics
	5. Visualizing predictions and regression lines
	6. Publishing your project as part of your portfolio collection

   The objective is to predict an outcome (e.g., exam scores, house prices) based on a single feature (e.g., study hours, house area).

2. ## **Tasks to be completed**

   1. ### **Exploring the dataset**

      1. #### **Loading the data**

         In this first step, I explored the datasets, which first involved loading the data for the simple linear and multi-variate linear regression models. For the simple linear regression, it was loaded from *homeprices.csv*, and for the multi-variate linear regression, it was loaded from *homeprices-m.csv*.
		 ![][image1] *Figure 1: Loading data from homeprices.csv*
		 ![][image2] *Figure 2: Loading data from homeprices-m.csv*

      2. #### **Description of its structure** {#description-of-its-structure}

         For the simple and multi variate linear regression, through initial inspection from calling *df* and *dfm*, we see there are column names, namely *area* and *price* for the simple linear regression and *area, bedrooms, age,* and *price* for the multi- variate linear regression. Through this step, I was able to check the data types and identify missing values, which showed that in the *bedrooms* column in *dfm,* there is a *NaN* value, which was later imputed with its median to ensure data completeness for modeling.

      3. #### **Visualizing the dataset using scatter plots**

         Scatter plots were used to visually understand the relationships within the datasets.
         For the simple linear regression, a scatter plot of *area* versus *price* clearly illustrates a positive linear trend, indicating that larger *areas* generally correlate with higher prices.
         For multivariate linear regression, the model's overall prediction was plotted against a key feature, *‘area’*,
         overlaid on the actual *area* versus *price* data points. This plot effectively demonstrated how the model's output varied with changes in *area*.
		 ![][image3] *Figure 3: Visualizing simple linear regression data using scatter plots*
		 ![][image4] *Figure 4: Sample of multi-variate linear regression using scatter plots*

   2. ### **Preparing the Data**

   In this stage, I  handled missing values present either in the simple linear regression or the multivariate linear regression. In the simple linear regression, there were no missing values, but in the multi-variate linear regression, there was a missing value in the bedrooms column. The missing value was imputed using the median, and this ensured the data in the multivariate linear regression case was well prepared for the subsequent steps.

   ![][image5] *Figure 5: Imputation of missing values in the bedrooms column*

   To evaluate the model's ability to generalize to new, unseen data, both the simple and multivariate data sets were split into training and testing sets. This prevented data leaks and provided an unbiased assessment of model performance. The *train\_test\_split* function from Scikit-learn was used for this purpose, and we allocated 60% of the data for training and 40% for testing.

   ![][image6] *Figure 6: Splitting the linear regression model dataset*



	This split creates *x\_simple\_train, y\_simple\_train* for training and *x\_simple\_test, y\_simple\_test* for evaluation.

	![][image7] *Figure 7: Splitting the multivariate linear regression model dataset*

	This split creates *x\_multi\_train, y\_multi\_train* for training and *x\_multi\_test,  y\_multi\_test* for evaluation of the multi-variate linear regression model.

3. ### **Building the Model**
With the data prepared and split into training and testing sets, the next step involves constructing and training the linear regression model using Scikit-Learn. This process involves instantiating the LinearRegression estimator and fitting it to the respective training datasets.

   1. #### **Simple linear regression model**

	  In this case, a LinearRegression model was initialized and trained using the x\_simple\_train(area) and y\_simple\_train(price) datasets.
	  ![][image8] *Figure 8: Building the simple linear regression model*


      This step involves the model learning the single coefficient (slope) and the intercept that define the best-fitting line through the training data points, minimizing the sum of squared residuals between the actual and predicted prices based solely on the area feature. (The model is finding the straight line that gets as close as possible to all the actual data points, with an emphasis on reducing big prediction mistakes.)

    2. #### **Multi-variate linear regression model**
	For the multivariate analysis, a separate LinearRegression model was created and fitted using the x\_multi\_train(area, bedrooms, age) and y\_multi\_train(price) datasets.
	![][image9] *Figure 8: Building the multi variate linear regression model*
	In this case, the model learns multiple coefficients- one for each independent variable(area, bedrooms, age), along with an intercept. These coefficients represent the change in price for a one-unit increase in the respective feature, holding other features constant. The model effectively determines the best fitting hyperplane in a multi-dimensional space that minimizes the error in predicting house prices based on all three features simultaneously.

	After these steps, both the simple and multi-variate linear regression models are trained and ready for evaluation on their respective test sets.

4. ### **Evaluate the Model** {#evaluate-the-model}

	After training,  model performance was assessed using standard regression metrics like MAE, MSE, RMSE, and R² Score. These metrics quantify prediction accuracy and the proportion of variance explained.

	* **Mean Absolute Error(MAE)**: Refers to the average absolute difference between actual and predicted values and it is less sensitive to outliers.
	* **Mean Squared Error(MSE)**: Refers to the average squared difference. It penalizes larger errors more heavily and is sensitive to outliers.
	* **Root Mean Squared Error(RMSE)**: This is the square root of MSE, in the same units as the target variable.
	* **R-Squared(R^2 Score)**: Refers to the proportion of target variance explained by the model. A higher value closer to 1 indicates a better fit.
	1. #### **Model performance results**
	Models were evaluated on their respective test sets to ensure unbiased assessment.
	1. #### **Simple linear regression model**
	![][image10] *Figure 9: Simple linear regression model evaluation metrics*
	To take MAE as an example here, the model’s predictions are on average 16184.21 away from the actual selling price.
	2. #### **Multivariate linear regression model**
	![][image11] *Figure 10: Simple linear regression model evaluation metrics continued*
	![][image12] *Figure 11: Multivariate linear regression model evaluation metrics*
	![][image13] *Figure 12: Multivariate linear regression model evaluation metrics continued*
	To take MAE as an example here, the model’s predictions are on average 32547.57 away from the actual selling price of the houses in the test set.

5. ### **Visualize the Results**
	It is important to visualize the model’s performance to gain an understanding of its fit and predictive capabilities

	1. #### **Simple linear regression model**
	![][image14] *Figure 13: Visualizing the Simple linear regression model*
	![][image15]* *Figure 14: Visualizing the Simple linear regression model continued*
	The plot shows the actual house prices against the corresponding areas. The visualization clearly shows how well the straight line fits the observed data points, indicating the model’s ability to capture the positive trend between area and price.
	2. #### **Multivariate linear regression model**
	![][image16] *Figure 15: Visualizing the Multivariate linear regression model*
	![][image17] *Figure 16: Visualizing the Multivariate linear regression model continued*

	The visualization shows that the red crosses are close to the blue line, which indicates that the multivariate model is making accurate predictions. The predicted prices are very close to the actual observed prices for houses within the range of the area shown. With the blue line upward sloping, this indicates that the model predicts higher prices for larger prices, with everything being equal.

6. ### **Sharing of the work**

   #### **Link to Google Colab notebook**

   [Uel Kariuki Google Colab Notebook](https://colab.research.google.com/drive/1ZH1YrT9wnmQBRt4ZQPXl5VmNJplWkHRK?usp=sharing)

3. ## **Conclusion**

   This project on house price prediction was a valuable hands-on experience, going through the entire process from the raw data to predictive insights using linear regression. I gained practical experience in data preparation, model building, both the simple and multi-variate linear regression models using Scikit-Learn. By doing model evaluation using metrics like MAE, MSE, I got an understanding of model performance. Visualizing the regression lines against the actual data provided qualitative insights into the model’s fit. Through this project, I also learnt critical insights into the factors influencing house prices like area, age, and bedrooms, which showed how linear models can provide predictive capabilities in real-world scenarios. With the skills gained from this project, my portfolio for future data and AI opportunities has become stronger.

[image1]: /assets/images/Projects/regression_models_week_7_screenshots/1.1.png
[image2]: /assets/images/Projects/regression_models_week_7_screenshots/1.2.png
[image3]: /assets/images/Projects/regression_models_week_7_screenshots/1.3_regression.png
[image4]: /assets/images/Projects/regression_models_week_7_screenshots/1.4_regression.png
[image5]: /assets/images/Projects/regression_models_week_7_screenshots/1.4.1__regression.png
[image6]: /assets/images/Projects/regression_models_week_7_screenshots/1.5_regression.png
[image7]: /assets/images/Projects/regression_models_week_7_screenshots/1.6_regression.png
[image8]: /assets/images/Projects/regression_models_week_7_screenshots/1.7_regression.png
[image9]: /assets/images/Projects/regression_models_week_7_screenshots/1.8_regression.png
[image10]: /assets/images/Projects/regression_models_week_7_screenshots/1.9_regression.png
[image11]: /assets/images/Projects/regression_models_week_7_screenshots/2.0__regression.png
[image12]: /assets/images/Projects/regression_models_week_7_screenshots/2.1__regression.png
[image13]: /assets/images/Projects/regression_models_week_7_screenshots/2.2__regression.png
[image14]: /assets/images/Projects/regression_models_week_7_screenshots/2.3_regression.png
[image15]: /assets/images/Projects/regression_models_week_7_screenshots/2.4_regression.png
[image16]: /assets/images/Projects/regression_models_week_7_screenshots/2.5_regression.png
[image17]: /assets/images/Projects/regression_models_week_7_screenshots/2.6_regression.png
