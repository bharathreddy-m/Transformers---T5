# Transformers---T5

# Text Summarization and Question Answering using Transformers

## 📌 Project Overview
This project implements **text summarization** and **question-answering (Q&A)** using transformer models. The system processes a **real-world book** (not a generated dataset) to summarize content and answer user queries. Various models, embedding strategies, and retrieval techniques were explored to enhance accuracy and efficiency.

## 📖 Dataset Information
- The dataset is sourced from **'Large Scale Machine Learning with Python'** by **Packt Publishing**.
- The text was extensively preprocessed before applying transformer models.

## 🏗️ Project Workflow
### 1️⃣ Data Preprocessing
- **Removed unnecessary sections**, including the **Table of Contents** and irrelevant text.
- **Converted text to lowercase** to maintain consistency.
- **Removed special characters, numbers, and extra whitespace** to clean the dataset.
- **Tokenized text into sentences and words** for structured processing.
- **Applied stopword removal** to enhance focus on meaningful words.
- **Performed stemming and lemmatization** to standardize word forms.
- **Split the text into chunks** to optimize summarization and retrieval.

## 📌 Implementation Details

### **Text Summarization**
1. **Data Cleaning & Preprocessing:** The book text was cleaned using the above preprocessing steps.
2. **Chunking Strategy:** The text was split into **293 meaningful chunks** for efficient summarization.
3. **Model Selection:** We used the **T5-small** transformer model for text summarization.
4. **Summarization Process:** Each chunk was passed through the **T5-small** model to generate summaries.
5. **Storage of Summarized Data:** The generated summaries were saved in **summarized_text.txt** for later use in the Q&A system.

### **Question Answering System**
1. **Using Summarized Data:** Instead of using raw text, we utilized the **summarized_text.txt** file for better retrieval and generation.
2. **Embedding Models:**
   - Initially used **SBERT (all-MiniLM-L6-V2)** to create embeddings for text retrieval.
   - Later, switched to **SBERT (all-mpnet-base-v2)** for improved accuracy.
3. **Search Models:**
   - **Cosine Similarity** was tested first but had limitations in retrieval.
   - Replaced with **FAISS (Facebook AI Similarity Search)** to enhance search speed and relevance.
4. **Transformer Models for Q&A:**
   - Initially used **T5-small** for generating answers.
   - Upgraded to **Flan-T5-Base**, which provided more contextually accurate responses.
5. **Retrieval + Answer Generation Pipeline:**
   1. User query is embedded using **SBERT**.
   2. **FAISS** retrieves the **top-k most relevant chunks**.
   3. The **Flan-T5-Base** model generates an answer based on retrieved content.

## 📊 Results
Example Q&A system responses:

### **Question 1:** How does Python help with big data processing?
**🤖 Generated Answer:** Python has minimal memory footprint and excellent memory management. It can scale out by leveraging multiple machines into a cluster and using frameworks like Hadoop and H2O.

### **Question 2:** What are some key Python libraries for machine learning?
**🤖 Generated Answer:** MLlib (Spark's machine learning library), Scikit-learn (data processing and model selection), XGBoost, and H2O are widely used for machine learning applications.

### **Question 3:** What is the role of gradient descent in optimization?
**🤖 Generated Answer:** Gradient descent finds the optimal parameters by iteratively updating values in the direction of the negative gradient. It is widely used in machine learning to minimize error functions.

## 🚀 Future Work
- **Enhancing Retrieval:** Experiment with **hybrid search (BM25 + embeddings)**.
- **Conversational Responses:** Extend the Q&A system to handle human-like dialogue interactions.
- **Larger Models:** Fine-tune **Flan-T5-Large** for even better performance.

## 📂 Repository Structure
```
|-- data/                     # Contains the original book and processed text chunks
|-- notebooks/                 # Jupyter notebooks for text summarization & Q&A
|-- models/                    # Trained models and FAISS indexes
|-- summarized_text.txt        # Summarized text used for Q&A
|-- README.md                  # This README file
```

## 📝 Conclusion
This project successfully implemented text summarization and Q&A using **multiple transformer models, embedding techniques, and retrieval methods**. We experimented with **different embeddings (MiniLM, MPNet), search models (Cosine, FAISS), and transformer models (T5-small, Flan-T5-Base)** to optimize performance. The approach balances efficiency and accuracy while ensuring responses are contextually relevant.

---

**🔗 Connect & Contribute:** If you find this project useful, feel free to fork, experiment, and contribute! 🚀

