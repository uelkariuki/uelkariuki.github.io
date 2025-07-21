---
layout: post
title: "Deep Learning for Image Classification: Building and Evaluating an ANN with MNIST"
date: "2025-07-21 15:16:00 +0300"
tags: [Deep Learning, Neural Networks, ANN, Image Classification, MNIST, TensorFlow, Keras, Python, Data Science, Machine Learning, Regularization, Dropout, Confusion Matrix, Classification Report]
category: [Deep Learning, Neural Networks, Keras, TensorFlow, Python, Image Classification, MNIST Dataset, Model Evaluation, Data Preprocessing]
description: "Explore an end-to-end deep learning workflow for classifying handwritten digits using the MNIST dataset, covering data preprocessing, Artificial Neural Network (ANN) construction, training, and performance evaluation."
comments: True
slug: "deep-learning-mnist-ann-classification"
---

1. ## **Introduction**

   In this assignment, I applied my understanding of artificial neural networks and TensorFlow/ Keras to build, train, evaluate, and document an image classification model using the **MNIST dataset**. **MNIST** stands for Modified National Institute of Standards and Technology dataset. It is a benchmark dataset widely used in training and testing machine learning and deep learning models for **handwritten digit recognition**.


	| Item | Description |
	| :---- | :---- |
	| **Images**  | 70,000 grayscale images of digits (0–9) |
	| **Size** | Each image is 28×28 pixels (784 total) |
	| **Labels** | 10 classes (digits 0 to 9\) |
	| **Split** | 60,000 training images, 10,000 test images  |



	The objectives of this assignment were:
	1. Preprocessing and exploring image data
	2. Designing and building the ANN architecture
	3. Compiling, Training, and Validating the deep learning model
	4. Evaluating the model on the test set and reporting the final test accuracy
	5. Visualizing the model training history
	6. Saving and loading trained models using the modern Keras format

2. ## **Tasks to be completed**

   1. ### **Loading the dataset**

      The first step was to import the required libraries, which were essential for this task to be accomplished. I used the command (X\_train, y\_train), (X\_test, y\_test) \= mnist.load\_data() to load the MNIST dataset.  It divides the dataset into two primary sets (X\_train, y\_train) for model training, which comprises the images and their corresponding true labels, and (X\_test, y\_test) for model evaluation, containing images and labels reserved for assessing the trained model’s performance on unseen data.

      ![][image1] *Figure 1: Importing the Libraries*

      ![][image2] *Figure 2: Loading the dataset*



   2. ### **Data preprocessing**

      In this stage,  using the code below I performed data preprocessing steps on the dataset to prepare it for the neural network training. First, it normalizes the pixel values of both the training(X\_train) and testing(X\_test) images by dividing them byu 255.0. This scales the original pixel intensity range of 0-255 down to a \[0, 1\] range, which benefits neural networks training by improving convergence and stability.
      After normalization, the code one-hot encodes the labels for both training (y\_train\_cat) and testing(y\_test\_cat) sets using to\_categorical. This transforms integer labels, ie, 5, into a binary vector representation like \[0,0,0,0,0,1,0,0,0,0\] suitable for multi-class classification with a softmax output layer and categorical\_crossentropy loss. Finally, it prints the shapes and value ranges of the preprocessed data, along with a comparison of original and one-hot encoded sample labels, to confirm the transformations were applied correctly.

      *![][image3]* *Figure 3: Data preprocessing*

      *![][image4]* *Figure 4: Data preprocessing continued*


   3. ### **Plotting some digits from the dataset**

      The code below is responsible for visualizing a selection of handwritten digits from the training dataset. It begins by defining selected\_indices, a list of specific index numbers corresponding to the images to be displayed. A matplotlib figure is then created to serve as a canvas for the plots. Inside the loop, it iterates through the chosen indices. For each index, it creates a subplot within a 3 \* 3 grid, displaying the grayscale image (X\_train\[idx\]) and sets a title indicating both the true digit label (y\_train\[idx\]) and its original index. Axis labels are hidden for a cleaner presentation.plt.tight\_layout() adjusts subplot parameters for optimal spacing, and plt.show() renders the complete visualization.This provides a quick visual inspection of the dataset’s content and verifies the integrity of the image-label pricing.


      ![][image5] *Figure 5: Plotting some digits from the dataset*

      ![][image6] *Figure 6: Plotting some digits from the dataset continued*


   4. ### **Building the ANN model**

      In the next stage, the code constructs an Artificial Neural Network (ANN) using Keras’ Sequential model, defining its layer-by-layer architecture. It begins with an Input layer to specify the 28 \* 28 pixel input layers, followed by a Flatten layer that reshapes these 2D images into a 1D vector of 784 features. The core of the network consists of two Dense(fully connected) hidden layers, with 128 and 64 neurons respectively, both employing the ReLU activation function to introduce non-linearity. To prevent overfitting, Dropout layers with a 30% rate are placed after each hidden layer. The model finishes in a final Dense output layer with 10 neurons, corresponding to the 10 digit classes, and a softmax activation function to produce probability distributions for classification. After defining this structure, model.summary() is invoked to display a concise table detailing each layer’s characteristics, including its type, output shape, and the count of trainable parameters.


      ![][image7] *Figure 7: Building the ANN model*

      ![][image8] *Figure 8: Building the ANN model continued*


   5. ### **Compiling the model**

      In this step, the code below configures the learning process for the defined neural network model using the model.compile() method. It specifies three essential components for training: the optimizer, which is set to 'adam' (Adaptive model estimation), a robust algorithm for adjusting the model’s internal weights to minimize loss; the loss function, chosen as 'categorical\_crossentropy', which is suitable for multi-class classification problems with one-hot encoded labels and quantifies the error predicted and true probability distributions; and the metrics to monitor during training, which is set to \['accuracy'\] to track the proportion of correctly classified samples. This step prepares the model to begin its training phase.

      ![][image9] *Figure 9: Compiling the model*


   6. ### **Training the model**

      In this stage, the training process of the neural network model is initiated. The model.fit() method is called with the normalized training images (X\_train) and their one-hot encoded labels (y\_train\_cat). Training will proceed for 10 full passes over the entire dataset (epochs), with the data processed in mini-batches of 128 samples (batch\_size) before weight updates. Crucially, a validation\_split of 0.1 (10%) automatically reserves a portion of the training data to serve as a validation set, allowing the model’s performance on unseen data to be monitored at the end of each epoch, which is vital for detecting and preventing overfitting. The history object returned captures metrics like loss and accuracy for both training and validation sets across all epochs, providing a record of the learning progress.

      ![][image10] *Figure 10: Training the model*


   7. ### **Model evaluation**

      In this stage, the code performs the final evaluation of the trained model on the dedicated and previously unseen test set. The model.evaluate() method computes the model’s performance by comparing its predictions for X\_test with the true one-hot encoded labels (y\_test\_cat). This process results in two primary metrics: test\_loss(the calculated categorical cross-entropy) and test\_accuracy(the proportion of correctly classified samples). These results are then printed, formatted to 4 decimal places, providing an unbiased measure of the model’s generalization capability on new data.

      ![][image11] *Figure 11: Model  evaluation*


   8. ### **Visualize training history**

      In this step, we visualize the model’s performance during training by plotting its accuracy over epochs. It retrieves the training accuracy (history.history\['accuracy'\]) and validation accuracy (history.history\['val\_accuracy'\]) recorded during the model.fit() process. These two sets of data are then plotted on a graph, with 'Epoch' on the x-axis and 'Accuracy' on the y-axis. The plot is titled 'Model accuracy', includes a legend to differentiate between training and validation curves, and is finally displayed, allowing for an immediate visual assessment of the model’s learning process and potential overfitting.

      ![][image12] *Figure 12: Visualizing training history: Accuracy*

      ![][image13] *Figure 13: Visualizing training history continued: Accuracy*

      ![][image14] *Figure 14: Visualizing training history: Loss*

      ![][image15] *Figure 15: Visualizing training history continued: Loss*


   9. ### **Confusion matrix**

      This section focuses on evaluating the model’s performance beyond simple accuracy by generating and visualizing a confusion matrix. First, it uses the trained model to make predictions on the unseen X\_test dataset, resulting in y\_pred (probability distributions for each class). np.argmax converts these probabilities into concrete class predictions (y\_pred\_classes). A confusion matrix is subsequently computed, comparing these y\_pred\_classes against the actual y\_test labels. Finally, this confusion matrix (cm) is visualized as a heatmap using seaborn.heatmap, with numerical annotations, a 'Blues' colormap, and clearly labeled axes ('Predicted' and 'True') and title, providing a detailed breakdown of correct classifications and misclassifications for each digit.

      ![][image16] *Figure 16: Confusion matrix*

      ![][image17] *Figure 17: Confusion matrix continued*


   10. ### **Classification report**

       In this step, we generate and print a detailed classification report, providing an evaluation of the model’s performance on the test set. It takes the true labels (y\_test)  and the model’s predicted class labels(y\_pred\_classes) as input. The report outputs key metrics for each class (digits 0-9), including precision, recall, f1-score, and support(number of true instances) for each class. It also includes overall averages such as macro avg (unweighted average) and weighted avg (support-weighted average) for these metrics, offering a more nuanced understanding of the model’s strengths and weaknesses.

       ![][image18] *Figure 18: Classification report*

   11. ### **Saving and reloading the model**

       In this stage, the code below shows the process of persisting a trained neural network model and then reloading it. The model.save("mnist\_ann\_model.h5") command saves the entire state of the model (including the architecture, learned weights, and optimizer state) to a file named mnist\_ann\_model.h5 in the HDF5 format. In addition to that, **from** tensorflow.keras.models **import** load\_model imports the necessary function, and reloaded\_model \= load\_model("mnist\_ann\_model.h5") then loads this saved model back into memory, creating an identical reloaded\_model object. Finally, reloaded\_model.evaluate(X\_test, y\_test\_cat) is executed to verify that the loaded model performs identically to the original model on the test set, confirming the integrity of the saving and loading process for future deployment or continued use.

       ![][image19] *Figure 19: Saving and reloading the model*



   12. ### **Sharing the work**

       ### **Link to Google Colab notebook**

       [Uel Kariuki Google Colab Notebook](https://colab.research.google.com/drive/1YbWYrYh-1UcRGcyKa5bQakXoA3294AIg?usp=sharing)


3. ## **Conclusion**

   This project provided a hands-on experience in building and evaluating a deep learning model for image classification using the MNIST dataset. From the initial stages of dataset loading and preprocessing, to building and training of a sequential Artificial Neural Network, I gained invaluable practical insights. The process extended to post-training analysis, encompassing training history visualization, evaluation on test set, confusion matrix generation and a classification report. The entire workflow, from data preparation to model assessment and persistence, enhanced my understanding of how to develop, evaluate, and manage deep learning solutions, greatly strengthening my foundation for future Data and AI endeavours.

[image1]: /assets/images/Projects/deep_learning_images/dl_1.1.png
[image2]: /assets/images/Projects/deep_learning_images/dl_1.2.png
[image3]: /assets/images/Projects/deep_learning_images/dl_1.3.png
[image4]: /assets/images/Projects/deep_learning_images/dl_1.4.png
[image5]: /assets/images/Projects/deep_learning_images/dl_1.5.png
[image6]: /assets/images/Projects/deep_learning_images/dl_1.6.png
[image7]: /assets/images/Projects/deep_learning_images/dl_1.7.png
[image8]: /assets/images/Projects/deep_learning_images/dl_1.8.png
[image9]: /assets/images/Projects/deep_learning_images/dl_1.9.png
[image10]: /assets/images/Projects/deep_learning_images/dl_2.0.png
[image11]: /assets/images/Projects/deep_learning_images/dl_2.1.png
[image12]: /assets/images/Projects/deep_learning_images/dl_2.2.png
[image13]: /assets/images/Projects/deep_learning_images/dl_2.3.png
[image14]: /assets/images/Projects/deep_learning_images/dl_2.4.png
[image15]: /assets/images/Projects/deep_learning_images/dl_2.5.png
[image16]: /assets/images/Projects/deep_learning_images/dl_2.6.png
[image17]: /assets/images/Projects/deep_learning_images/dl_2.7.png
[image18]: /assets/images/Projects/deep_learning_images/dl_2.8.png
[image19]: /assets/images/Projects/deep_learning_images/dl_2.9.png















