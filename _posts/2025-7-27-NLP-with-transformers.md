---
layout: post
title: "Semantic Similarity with Transformers: A Practical Guide to BERT Embeddings"
date: "2025-07-27 20:56:29 +0300"
tags: [NLP, Transformers, BERT, Deep Learning, Sentence Similarity, Semantic Search, Python, Hugging Face, Data Science, Machine Learning, Embeddings, Cosine Similarity, Text Analysis]
category: [Natural Language Processing, Deep Learning, Transformers, BERT, Model Evaluation, Text Embeddings]
description: "A hands-on project exploring semantic sentence similarity using pre-trained BERT models. Learn to generate contextual embeddings, apply cosine similarity, and evaluate model performance for understanding linguistic nuances."
comments: True
slug: "semantic-similarity-bert-transformers-nlp"
---


1. ## **Introduction**
   In this assignment, I applied my understanding of Natural Language Processing, which is a field at the intersection of linguistics, artificial intelligence, and computer science that focuses on enabling computers to understand, interpret, and generate human language in ways that are both meaningful and useful.

   The objectives of this assignment were:
   1. Applying a pre-trained BERT model for sentence encoding using Hugging Face Transformers.
   2. Extracting token-level contextual embeddings.
   3. Demonstrating how BERT captures word meaning based on context (polysemy).
   4. Computing and interpreting cosine similarity between token embeddings.
   5. Explaining the importance of contextual embeddings in contrast to static word vectors.

2. ## **Tasks to be completed**

   1. ### **Loading the pre-trained BERT tokenizer and BERT model**

      The first step in this project was to import the required libraries, which were essential for the project's completion. The code below initialized the fundamental components for working with BERT (Bidirectional Encoder Representations from Transformers), which is a powerful pre-trained language model from Google, made accessible through the Hugging Face Transformers library. I used the command `tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')` to load a pre-trained tokenizer designed for the BERT model, which is responsible for converting raw text into numerical inputs(like word IDs and attention masks) that the model can understand, ensuring consistency with how the original model was trained.
      I also used the command `bert_model = TFBertModel.from_pretrained('bert-base-uncased')` that was used to load the actual pre-trained BERT neural network model itself, configured for TensorFlow(`TF` prefix) and specifically the `"base"` version that handles `"uncased"`(lowercase) English text. This step provides a powerful, pre-trained representation of language that can be leveraged for various downstream natural language processing tasks, such as calculating sentence similarity without needing to train the vast model from scratch.

      ![][image1]
      *Figure 1: Importing required libraries*

      ![][image2]
      *Figure 2: Load pre-trained BERT tokenizer and BERT model*



   2. ### **Adding sentence pairs**

      The code below defines a Python list named `sentence_pairs`. Each element within this list is a tuple, and each tuple contains two distinct sentences. The purpose of creating this list is to serve as a specific dataset for the program to analyze; the subsequent code will iterate through each of these 10 sentence pairs to calculate their semantic similarity using the pre-trained BERT model, allowing for a comparison of the model's prediction against a set of expected outcomes.

      ![][image3]
      *Figure 3: Adding 10 sentence pairs*


   3. ### **Ground truth similarity labels**

      The code below creates a Python list named `labels`. In this context, this list serves as the "ground truth"  or "true labels" for the `sentence_pairs` data. Each number in this list corresponds directly to a pair of sentences in the `sentence_pairs` list, indicating whether that pair is similar (1) or not similar(0) according to the manual judgement. This labels list is crucial because it provides the correct answers against which the model’s predictions will be compared to calculate its accuracy. Without these ground truth labels, it would be impossible to evaluate how well the BERT-based similarity model performs.

      ![][image4]
      *Figure 4: Ground truth similarity labels*

   4. ### **Function to get the BERT \[CLS\] embedding for a sentence**

      The Python function `get_sentence_embedding(sentence)` serves as a crucial component for converting a raw sentence into a numerical vector representation, known as an embedding, utilizing a pre-trained BERT model. The process begins by tokenizing and encoding the input sentence into a format BERT understands, including adding special tokens and handling varying sentence lengths through padding and truncation. These prepared inputs are then fed into the `bert_model`, which processes them through its layers to produce contextualized token embeddings. Finally, the function extracts the embedding corresponding to the special \[CLS\] token (usually the first token in a BERT input sequence) from the model’s last hidden state, as this token’s embedding is commonly used to represent the overall semantic meaning of the entire sentence. The resulting TensorFlow tensor is then converted to a NumPy array before being returned, making it suitable for subsequent numerical operations like similarity calculations.

      ![][image5]
      *Figure 5: Function to get the BERT \[CLS\] embedding for a sentence*


   5. ### **Calculate cosine similarity for each pair**
      The code below demonstrates the core logic for evaluating the semantic similarity of each sentence pair. It initializes an empty list. predictions, to store the binary similarity results. Then, it iterates through every `(sent1, sent2)` tuple in the `sentence_pairs` list. For each pair, it first obtains a numerical vector representation (embedding) for `sent1` and `sent2` by calling the `get_sentence_embedding` function, which leverages a pre-trained BERT model. Next, it computes the `cosine_similarity` between these two high-dimensional embeddings. This `sim_score` quantifies how similar the sentences are in meaning, with a value closer to 1 indicating higher similarity. Based on a predefined threshold of 0.7, it then makes a binary prediction (`pred`), classifying the pair as `1` (similar) if the score exceeds `0.7` or `0` (not similar) otherwise. Finally, this prediction is appended to the `predictions` list, and the sentences, their calculated similarity score, and the resulting prediction are printed to the console for immediate feedback.

      ![][image6]
      *Figure 6: Calculate cosine similarity for each pair*

      ![][image7]
      *Figure 7: Calculate cosine similarity for each pair continued*

      ![][image8]
      *Figure 8: Calculate cosine similarity for each pair continued*

	  Upon executing the code with the `0.7` similarity threshold, the model consistently produced cosine similarities well above this value for all ten sentence pairs, resulting in every pair being uniformly classified as `'similar' (1)`. This behaviour, while confirming BERT’s ability to identify semantic relatedness, indicates that the bert-based-uncased model’s [CLS] embeddings, when subjected to this specific threshold, interpret `'similarity'` very broadly. Even pairs manually labelled as dissimilar, such as `'What is AI'` vs `'How to cook pasta'`(`0.8811 similarity`)  or  `'I love to read books'` vs `'I enjoy watching movies'` (`0.9744 similarity`), yielded high scores.

	  This suggests a mismatch between the inherent semantic relatedness captured by this general-purpose BERT model at the [CLS] token level and the more stringent definition of `'similarity'` implied by the ground truth labels for this task. Consequently, under the constraint of a `0.7` threshold, the current model configuration is unable to effectively differentiate truly dissimilar sentence pairs, leading to a suboptimal performance for binary classification on this dataset.

   6. ### **Accuracy evaluation**

      The code below calculates the accuracy of the sentence similarity model. It begins by initializing a variable `correct` to 0. Then, it iterates through the `predictions` list (which contains the model’s `0` or `1` similarity judgments) and accesses the corresponding `labels` list (which holds the manually assigned true `0` or `1` similarity judgments). In each iteration, it compares the model’s `prediction(predictions[i])` with the ground truth label (`labels[i]`). If they match(meaning the model made a correct prediction for that sentence pair), the `correct` counter is incremented by one. Finally, after checking all pairs, the `correct` variable will hold the total count of accurately classified sentence pairs, which is the numerator needed for the final accuracy calculation.

      ![][image9]
      *Figure 9: Accuracy evaluation*


   7. ### **Final accuracy calculation**

      The code below determines the total number of sentence pairs by getting the length of the `labels` list (which represents the ground truth instances). Then, it calculates the accuracy by dividing the `correct` count by the `total` number of pairs. Finally, it prints the calculated accuracy to the console, formatted as a percentage with two decimal places. This provides an easy-to-understand metric that summarizes the model’s performance by indicating the proportion of predictions it got right across the entire dataset.

      ![][image10]
      *Figure 10: Final Accuracy calculation*

	  Following the prediction process, the model’s performance was quantitatively evaluated. With the `correct` count at `7` out of `total` of 10 sentence pairs, the final `accuracy` achieved was `70.00 %`. This accuracy figure directly reflects the observations from step 6. While the model correctly identified `7` of the `10` pairs according to the ground truth, its uniform classification of `'similar'` for many dissimilar pairs significantly impacted overall performance. This outcome further underscores that, given the `0.7` similarity threshold and the general semantic capturing capabilities of the bert-base-uncased model’s [CLS] embeddings, the model struggled to effectively distinguish between genuinely similar and truly dissimilar sentences as defined by the provided labels, leading to a notable number of false positives.

   8. ### **How does BERT differ from traditional NLP approaches like Bag of Words or TF-IDF?**

      Unlike Bag of Words or TF-IDF, which treat words independently and ignore order or context, BERT is a deep learning model that understands language by considering word order and generating contextual embeddings. It is pre-trained on vast text, capturing deeper semantic meaning.



   9. ### **What is the role of the encoder in the BERT model, and how is it used in this assignment?**

      BERT’s encoder processes input sentences, learning rich representations. In this assignment, it takes tokenized text and transforms it into numerical embeddings that capture the meaning of sentences.


   10. ### **What are contextual embeddings? How are they generated and used in this code?**

       These are numerical representations of words that change based on their surrounding words in a sentence, reflecting their specific meaning in context. They are generated by BERT’s multi-layered processing, providing a nuanced understanding of sentences for tasks like similarity.


   11. ### **Why is the \[CLS\] token used for sentence similarity in this code?**

       The \[CLS\] token’s final embedding (the first token in BERT’s input ) is used as the sentence’s overall representation because BERT is pre-trained to aggregate sentence-level information into this token, making it a suitable summary vector for the entire sequence.


   12. ### **What is cosine similarity, and why is it useful in comparing embeddings?**

       This metric measures the similarity between two vectors by computing the cosine of the angle between them( ranging from \-1 to 1). It is useful for comparing embeddings because it focuses on the direction (semantic meaning) of the vectors rather than their magnitude, making it effective in high-dimensional spaces to quantify conceptual closeness.


   13. ### **Sharing the work**

       ### **Link to Google Colab notebook**

       [Uel Kariuki Google Colab Notebook](https://colab.research.google.com/drive/1nFqpwONN6UNgnlYIBU6meW_O8Ju24Vos?usp=sharing)


3. ## **Conclusion**

   This project provided a hands-on experience in building and evaluating an NLP model for semantic sentence similarity utilizing transformers. From data loading and preprocessing, which involved tokenization and generating BERT embeddings, to computing cosine similarity and making predictions. I gained practical insights into advanced language understanding. The process extended to post-prediction analysis,  including accuracy calculation and a deeper understanding of contextual embeddings and the \[CLS\] token’s role. This entire workflow,  from text representation to model assessment, enhanced my understanding of how to develop, evaluate, and manage robust NLP solutions with transformers, greatly strengthening my foundation for future Data and AI endeavors.


[image1]: /assets/images/Projects/nlp_images/nlp_1.1.png
[image2]: /assets/images/Projects/nlp_images/nlp_1.2.png
[image3]: /assets/images/Projects/nlp_images/nlp_1.3.png
[image4]: /assets/images/Projects/nlp_images/nlp_1.4.png
[image5]: /assets/images/Projects/nlp_images/nlp_1.5.png
[image6]: /assets/images/Projects/nlp_images/nlp_1.6.png
[image7]: /assets/images/Projects/nlp_images/nlp_1.7.png
[image8]: /assets/images/Projects/nlp_images/nlp_1.8.png
[image9]: /assets/images/Projects/nlp_images/nlp_1.9.png
[image10]: /assets/images/Projects/nlp_images/nlp_2.0.png
