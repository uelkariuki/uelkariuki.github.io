---
layout: post
title: "A Guide to Retrieval-Augmented Generation (RAG) with LangChain and Hugging Face"
date: "2025-08-05 20:27:32 +0300"
tags: [RAG, LangChain, LLM, Python, Embeddings, FAISS, Transformers, Hugging Face, Google Flan-T5, Vector Store, NLP, Document Q&A]
category: [AI & Machine Learning, Natural Language Processing, LLM Development, RAG Systems, Python Projects]
description: "A hands-on guide to building an end-to-end RAG system. Learn how to load and chunk a PDF document, create a searchable vector store, and leverage a Large Language Model (LLM) to answer questions based on your own data."
comments: True
slug: "rag-guide-langchain-hugging-face"
---


1. ## **Introduction**

   In this assignment, I applied my understanding of **Generative AI** which is a type of artificial intelligence that creates new content, such as text, images, audio and video by learning from existing data and **Retrieval-Augmented Generation** (RAG) which refers to a technique that enhances the capabilities of large language models by combining them with an external knowledge base. I used this knowledge to build a practical pipeline that retrieves relevant document chunks and generates context-aware answers.
   The objectives of this assignment were:
   1. Applying generative AI concepts to synthesize answers from retrieved document content.
   2. Extracting key information from a PDF document by splitting it into chunks, embedding it using Sentence-Transformers, and storing it in a FAISS vector database for efficient retrieval.
   3. Demonstrating how retrieval improves generative question-answering by comparing answers generated from document-grounded context versus generic answers.
   4. Implementing a complete RAG pipeline in Python using LangChain, Hugging Face Transformers, and FAISS.
   5. Practicing prompt engineering to structure queries that guide the generative model for clearer and more detailed responses.

2. ## **Tasks to be completed** {#tasks-to-be-completed}

   1. ### **Importing libraries**

      The first step was to import the required libraries. The code block below is responsible for setting up the entire environment and importing the necessary tools to build a Retrieval-Augmented Generation (RAG) system. It begins by using \!pip install to install core Python packages, including langchain for the application framework, transformers for working with a large language model (LLM), sentence-transformers for creating high-quality text embeddings, faiss-cpu for efficient vector storage and search, and pypdf for handling PDF documents. Following the installation, the code imports specific classes and functions from these libraries, such as PyPDFLoader, RecursiveCharacterTextSplitter, HuggingFaceEmbeddings, and FAISS. These imports provide all the essential building blocks for the rest of the program, enabling it to load a document, process its text, create a searchable database of embeddings, and load an LLM for generating responses.

      ![][image1]
      *Figure 1: Importing required libraries*

   2. ### **Loading the PDF**

      The code block performs the crucial initial step of the RAG pipeline by loading the raw data from a PDF document. It begins by creating an instance of PyPDFLoader, a specialized tool from the langchain library that is designed to read and parse the text content of PDF files. The program is specifically directed to a file named "document.pdf". The subsequent line, docs \= loader.load() executes this loading process, which reads the entire PDF and extracts the text from each page. The output of this operation is not just raw text, but a structured list of Document objects. Each Document object contains the text content of a single page (page\_content) and, importantly, includes valuable metadata such as the page number and source file. This step is essential because it transforms the unstructured raw PDF file into a formatted, page-by-page collection of data, making it ready for the next processing stages, like splitting and embedding.

      ![][image2]
      *Figure 2: Loading the PDF*


   3. ### **Split documents into chunks**

      In this stage, it begins by creating an instance of RecursiveCharacterTextSplitter, a tool designed to intelligently break down large text documents. This splitter is configured with two key parameters: chunk\_size=500 and  chunk\_overlap=50. chunk\_size dictates that each text segment should have a maximum length of 500 characters, ensuring that chunks are small enough to fit within the context window of the language model without losing too much information. The chunk\_overlap parameter, set to 50, creates a small overlap of characters between consecutive chunks. This is a crucial technique for maintaining contextual continuity, as it prevents the model from losing important information that might be split between the end of one chunk and the beginning of the next. Finally,  splitter.split\_documents(docs) executes this process on the list of documents loaded in the previous step, transforming the raw page-by-page data into a list of semantically meaningful chunks that are ready to be converted into embeddings.

      ![][image3]
       *Figure 3: Split documents into chunks*


   4. ### **Create embeddings and vector score**

      In this step, the code block demonstrates the core RAG process, from converting text into searchable numerical representations to generating a coherent answer based on retrieved information. First, it initializes HuggingFaceEmbeddings using the sentence-transformers/all-MiniLM-L6-v2 model. This model is specifically chosen for its efficiency in converting text chunks into dense numerical vectors (embeddings) that capture the semantic meaning of the text. These embeddings are then used to build a FAISS vector store. FAISS(Facebook AI Similarity Search) is an optimized library for efficient similarity search and clustering of those high-dimensional vectors, allowing for rapid retrieval of relevant information. The vectorstore.as\_retriever() method then converts this vector store into a retriever, an essential component in angChain that can fetch documents most relevant to a given query.


      Next, the code sets up the Large Language Model (LLM) itself. It specifies google/flan-t5-large as the model\_name, a powerful pre-trained model capable of various text-to-text generation tasks. AutoTokenizer.from\_pretrained(model\_name) loads the appropriate tokenizer for this model, which is responsible for converting human-readable text into numerical tokens that the model can understand. AutoModelForSeq2SeqLM.from\_pretrained(model\_name) loads the actual pre-trained LLM. These two components are combined into a pipeline for “text2text-generation”, simplifying the process of interacting with the LLM.
      The heart of the RAG system is encapsulated in the query\_tag function. When a question is posed, the retriever.get\_relevant\_documents(question) step is executed. This is the “retrieval”  phase, where the system searches the FAISS vector store for the chunks of text that are most semantically similar to the user’s question. The retrieved relevant\_docs are then concatenated into a single context string. This context is then dynamically inserted into a prompt that is fed to the LLM. This is the “augmentation” part of RAG, where the LLM is explicitly instructed to “Answer the question using only the context”, thereby grounding its response in the provided document. The flan\_pipeline then generates the answer, with several parameters controlling the output: max\_new\_tokens limits the response length; temperature=0.9 introduces a degree of randomness, making the output more creative; top\_k=50 ensures sampling only occurs from the 50 most likely tokens; top\_p=0.9 (nucleus sampling) further refines this by considering tokens whose cumulative probability is below 0.9; and do\_sample=**True** enables these sampling strategies. Finally, the function returns the generated\_text from the LLM’s response. The last line, print(query\_rag("summarize the key points of this document in a paragraph of 200 words. ")), demonstrates the entire RAG pipeline in action by querying the system to summarize the loaded documents.

      ![][image4]
	  *Figure 4: Create embeddings and vector store*


      Upon executing the RAG pipeline with the query, “Summarize the key points of this document in a paragraph of 200 words”, the system produced a coherent and context-aware response. The pipeline successfully retrieved chunks of information from the document, which the flan-t5-large model then used to generate a summary. The resulting text highlights the core principles of using “the creative power of thought” to solve problems, emphasizing that a solution is often inherent to the problem itself. It also touches on the importance of assuming that an “infinite intelligence”  within the subconscious mind holds the answer and that a positive mental attitude can lead to a “happy solution”.


      ![][image5]
      *Figure 5: Create embeddings and vector store continued*

      ![][image6]
      *Figure 6: Create embeddings and vector store continued*

      ![][image7]
      *Figure 7: Create embeddings and vector store continued*

     ![][image8]
      *Figure 8: Create embeddings and vector store continued*

      ![][image9]
      *Figure 9: Create embeddings and vector store continued*

      ![][image10]
      *Figure 10: Create embeddings and vector store continued*


   5. ## **Sharing the work** {#sharing-the-work}

      ### **Link to Google Colab notebook** {#link-to-google-colab-notebook}



      [Uel Kariuki Google Colab Notebook](https://colab.research.google.com/drive/1hzbVwxmkoxWTLgQzVQCAICqe3WVO84Ov?usp=sharing)



3. ## **Conclusion** {#conclusion}


   This project provided a hands-on experience in building and evaluating a Retrieval-Augmented Generation (RAG) system for querying a custom document. From data loading and preprocessing, which involved splitting a PDF into manageable chunks and generating embeddings, to integrating a vector store and a large language model. I gained invaluable insights into modern LLM application development. The process culminated in creating an end-to-end RAG pipeline, which successfully retrieved relevant document context to ground the LLM’s response, preventing hallucinations, and demonstrating an effective method for question answering. This entire workflow, from data ingestion to model orchestration and context-aware generation, enhanced my understanding of how to develop, evaluate, and manage LLM solutions, greatly strengthening my foundation for future Data and AI endeavors.



[image1]: /assets/images/Projects/genai_images/g1.1.png
[image2]: /assets/images/Projects/genai_images/g1.2.png
[image3]: /assets/images/Projects/genai_images/g1.3.png
[image4]: /assets/images/Projects/genai_images/g1.4.png
[image5]: /assets/images/Projects/genai_images/g1.5.png
[image6]: /assets/images/Projects/genai_images/g1.6.png
[image7]: /assets/images/Projects/genai_images/g1.7.png
[image8]: /assets/images/Projects/genai_images/g1.8.png
[image9]: /assets/images/Projects/genai_images/g1.9.png
[image10]: /assets/images/Projects/genai_images/g2.0.png


