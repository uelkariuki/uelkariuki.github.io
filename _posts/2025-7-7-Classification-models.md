---
layout: post
title: A Report on Supervised Machine Learning Classification Models
date: 2025-07-07 20:25:00 +0300
categories: [Machine Learning, Machine Learning Models, Classification, Model building, Model Evaluation]
tags: [Machine Learning, Machine Learning Models, Classification, Model Building, Data preparation, Model Evaluation]
description: "A report taking a deep dive into Supervised Machine Learning Classification Models through building and evaluating various models"
---


1. ## **Introduction**

   In this assignment, I was to apply my understanding of supervised machine learning classification models by building and evaluating various models. Using the Wine dataset from scikit-learn, I explored and visualized the data, and trained six different models: Logistic Regression, Decision Tree, Random Forest, k-Nearest Neighbors (KNN), Naive Bayes, and Support Vector Machine (SVM). My goal was to compare their performance using standard evaluation metrics and confusion matrices and to interpret which model works best and why.

   This assignment helped me understand how to train models and how to assess and compare their performance on the same dataset under similar conditions.

2. ## **Tasks to be completed**
   1. ### **Load the dataset**

   The first task was to import the required libraries that were to be used to facilitate the classification of models. This was followed by loading the wine dataset and converting it to a dataframe, and this was done using the commands

   ``` python
   wine = load_wine()
   X = pd.DataFrame(wine.data, columns=wine.feature_names)
   y = pd.Series(wine.target, name='target')
   X
   ```


   From the screenshots below, it can be seen that the wine dataset has 178 rows × 13 columns, and with this visual representation, we have successfully loaded the wine dataset.

   ![][image1] *Figure 1: Importing of required libraries*

   ![][image2] *Figure 2: Loading of the wine dataset*

   2. ### **Explore the Dataset:**

      The next step was to explore the dataset by performing exploratory data analysis (EDA), and this helped me understand feature relationships and class distributions. Here I followed some steps.


      1. #### **Check the number of rows and columns**

      This was done using the commands below

	  ``` python
	  # Get an overview of the data
	  # Check the number of samples(rows) and features(columns)
	  print(X.shape, y.shape)
	  ```

	  ![][image3] *Figure 3: Check for the number of rows and columns*
	  We see that there are 178 rows and 13 columns for the independent

         variables, and 178 corresponding samples, where for every set of

         In X, there must be a corresponding target value in y.

      2. #### **Sanity check**

         A quick sanity check was performed by checking the first few rows and column names, and this was done using the commands

		 ``` python
		 print(X.head())
		 print(X.columns)
		 ```

         ![][image4] *Figure 4: Quick sanity check*

      3. ### **Check for missing values.**

         A check for missing values was done using the commands below, and there were no missing values.

		 ``` python
		 # check for missing values*
		 print(X.isnull().sum())
		 ```

		 ![][image5] *Figure 5: Check for missing values*

      4. ### **Check the target variable distribution.**

         This check informed me of the distribution and balance of the target variable, showing me the absolute count of each unique value present in the target variable y, and the percentage of each unique value in the target variable y.

		 ![][image6] *Figure 6: Check the target variable distribution*

      5. ### **Check for the spread of the features.**
         This was done using the describe() method in pandas to provide a summary of a DataFrame or Series.

		 ![][image7] *Figure 7: Check for the spread of the features*

      6. ### **Skewness check**

         Skewness is the measure of the asymmetry of the distribution. This tells whether the data is evenly distributed on both sides of the mean(symmetrical) or it leans more to one side(skewed).

		 ![][image8] *Figure 8: Skewness check*
		 ![][image9] *Figure 9: Skewness check continued*


      7. ### **Correlation heatmap to understand feature relationships**

         Heatmaps organize data in a grid, with different colors or shades indicating different levels of the data magnitude. A correlation heatmap shows how each variable in the dataset is correlated to the others. With \-1 signifying zero correlation and 1 signifying a perfect correlation.

         ![][image10] *Figure 10: Correlation heatmap*
		 ![][image11] *Figure 11: Correlation heatmap continued*

   3. ## **Data Preparation**

      In the data preparation stage, I checked if there were any missing values and then split the dataset into training and test sets.
      There were no missing values in the dataset.

      ![][image12] *Figure 12: No missing values in the dataset*


      After that, I split the dataset into training and test sets.

      ![][image13] *Figure 13: Splitting the dataset*

   4. ## **Building the Models**

      In this stage, I built the following classification models: Logistic Regression, Decision Tree, Random Forest, k-Nearest Neighbors (KNN), Naive Bayes, and Support Vector Machine (SVM).
      This was done by first creating a dictionary where each key is the name of a model, like Logistic Regression, and each value is another dictionary containing:  model, which is the actual scikit-learn model like Logistic Regression, data: a tuple containing the training data, testing data that the specific model should use. This was followed by using a for loop to iterate through each item in the dictionary, then I extracted the actual model object from model\_info and then extracted the training and testing data for the specific model.
      This was followed by training the model where the fit method teaches the model to find patterns in the training data(X\_train\_data) and also to predict the target labels (y\_train), this was followed by making predictions using the predict method that uses the trained model to predict the target labels for the unseen data (X\_test\_data).

	  ![][image14] *Figure 14: Building the models*
	  ![][image15] *Figure 15: Building the models continued*


   5. ## **Models Evaluation**

      In this next stage, I evaluated the models using the following evaluation parameters: Accuracy score, Classification report (precision, recall, F1-score), Confusion matrix (with visual plots)
      **Accuracy score**: Calculates the overall proportion of correct predictions
      **Classification report**: Produces a detailed report (precision, recall, F1-Score) for each class

	  ![][image16] *Figure 16: Models evaluation*
	  ![][image17] *Figure 17: Logistic regression model evaluation*
	  ![][image18] *Figure 18: Decision tree model evaluation*

      ![][image19] *Figure 19: Random  forest model evaluation*
	  ![][image20] *Figure 20: K-Nearest Neighbors(KNN) model evaluation*
	  ![][image21] *Figure 21: Naive Bayes (GaussianNB) model evaluation*
	  ![][image22] *Figure 22: Support Vector Machines (SVM) model evaluation*


   6. ## **Models Comparison**

      In this stage, I analyzed the results to determine which performed better.

	  ![][image23] *Figure 23: Models comparison*

      As seen from the screenshot above, Naive Bayes and Random Forest performed the best when compared with the other models, this is indicated by their perfect scores of 1.000000 across the evaluation metrics, namely accuracy, precision, recall, and F1-score.


   7. ## **Sharing the work**

      ### **Link to Google Colab notebook**

      [Uel Kariuki Google Colab Notebook](https://colab.research.google.com/drive/1UNKofoYL28na_mf3_L26hZ61V7qcYWjY?usp=sharing)



3. # **Conclusion** {#conclusion}

   This project on the classification of supervised machine learning models was a valuable hands-on experience, going from loading the dataset, exploring the dataset, and performing exploratory data analysis, data preparation, model building, and model evaluation, and finally comparing the results of the models led to me gaining a lot of insights. This project expanded my knowledge on how to train machine learning models, assess, and compare their performance while using the same dataset under similar conditions. The skills gained from this project will improve my skillset and enhance my portfolio for future Data and AI opportunities.

[image1]: /assets/images/Projects/screenshots_classification_models/1.1_classifcation_models.png
[image2]: /assets/images/Projects/screenshots_classification_models/1.2_classification_models.png
[image3]: /assets/images/Projects/screenshots_classification_models/1.3_classification_models.png
[image4]: /assets/images/Projects/screenshots_classification_models/1.4_classiication__models.png
[image5]: /assets/images/Projects/screenshots_classification_models/1.5_classification.png
[image6]: /assets/images/Projects/screenshots_classification_models/1.6_classification.png
[image7]: /assets/images/Projects/screenshots_classification_models/1.7_classification.png
[image8]: /assets/images/Projects/screenshots_classification_models/1.8_classification.png
[image9]: /assets/images/Projects/screenshots_classification_models/1.9_classification.png
[image10]: /assets/images/Projects/screenshots_classification_models/2.0_classification.png
[image11]: /assets/images/Projects/screenshots_classification_models/2.1_classification.png
[image12]: /assets/images/Projects/screenshots_classification_models/2.2_classification.png
[image13]: /assets/images/Projects/screenshots_classification_models/2.3_classification.png
[image14]: /assets/images/Projects/screenshots_classification_models/2.4_classification.png
[image15]: /assets/images/Projects/screenshots_classification_models/2.5_classification.png
[image16]: /assets/images/Projects/screenshots_classification_models/2.6_classification.png
[image17]: /assets/images/Projects/screenshots_classification_models/2.7_classification.png
[image18]: /assets/images/Projects/screenshots_classification_models/2.8_classification.png
[image19]: /assets/images/Projects/screenshots_classification_models/2.9_classification.png
[image20]: /assets/images/Projects/screenshots_classification_models/3.0_classifcation.png
[image21]: /assets/images/Projects/screenshots_classification_models/3.1_classification.png
[image22]: /assets/images/Projects/screenshots_classification_models/3.2_classification.png
[image23]: /assets/images/Projects/screenshots_classification_models/3.3_classification.png





















