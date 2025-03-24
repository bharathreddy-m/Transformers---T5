# Transformers --- T5
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

## 🔍 Methods and Models Used
### **1️⃣ Embedding Models**
- **SBERT (all-MiniLM-L6-V2)** - Used initially for sentence embeddings in the Q&A system.
- **SBERT (all-mpnet-base-v2)** - Later adopted for improved retrieval accuracy.

### **2️⃣ Search Models**
- **Cosine Similarity** - First retrieval method, had limitations in accuracy.
- **FAISS (Facebook AI Similarity Search)** - Used for faster and more precise semantic search.

### **3️⃣ Transformer Models**
- **T5-small** - Used for text summarization and early Q&A testing.
- **Flan-T5-Base** - Final Q&A model that provided better context-aware answers.

## 📌 Implementation Details

### **Text Summarization**
1. **Data Cleaning & Preprocessing:**
   - Removed unwanted sections and cleaned text.
   - Tokenized sentences and applied necessary text transformations.
2. **Chunking Strategy:**
   - The book was split into **293 meaningful chunks** for better summarization.
   - Overlapping chunks were used to preserve context.
3. **Model Selection:**
   - We selected **T5-small**, a pre-trained sequence-to-sequence transformer model.
4. **Summarization Process:**
   - Each chunk was fed into **T5-small** to generate a condensed summary.
   - The model was fine-tuned to maintain key information.
5. **Storage of Summarized Data:**
   - The generated summaries were stored in **summarized_text.txt** for later retrieval in the Q&A model.

### **Question Answering System**
1. **Using Summarized Data:**
   - Instead of processing the full book, we used the **summarized_text.txt** file for efficient retrieval.
2. **Embedding Models:**
   - First, we embedded the summarized text using **SBERT (all-MiniLM-L6-V2)**.
   - Later, we switched to **SBERT (all-mpnet-base-v2)** for improved performance.
3. **Search Models:**
   - Initially, **Cosine Similarity** was used but had limited retrieval accuracy.
   - We then implemented **FAISS**, a scalable nearest-neighbor search method.
4. **Retrieval Process:**
   - A user query is embedded using the same SBERT model.
   - FAISS retrieves the **top-k most relevant chunks** based on similarity.
5. **Answer Generation:**
   - Initially, **T5-small** was used for answer generation.
   - Finally, **Flan-T5-Base** was adopted, providing more detailed and accurate responses.

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

