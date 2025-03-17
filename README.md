# 🐶 The Golden Retriever

## Project Overview

The Golden Retriever is an information retrieval system combined with a personalized recommender system. It is designed to retrieve the most relevant answers from the **SE-PQA (StackExchange - Personalised Question Answering)** dataset, which contains around one million questions and two million associated answers.

The retrieval process follows a hybrid approach, leveraging both **content-based filtering (CBF)** and **collaborative filtering (CF)** techniques. The goal is to enhance search results using:

- **BM-25** as the baseline fast-ranking model.
- **MiniLM** as a neural re-ranker to improve ranking precision.
- **Query expansion** to refine recommendations based on user browsing history.

## User Similarity Computation

The system personalizes search results by analyzing **user similarities** based on **tags**: users who ask questions are compared with users who answer them on the grounds of tags associated with their previous activity. A **similarity matrix** is thus constructed, where the rows represent users, the columns represent different question tags, and the values indicate past interactions with specific tags. 

Given a user's tag history (questions they asked), we intersect it with the tags of users who previously answered similar questions. The **similarity score** is computed as:

<img align="center" width="350" src="latex-formula.png" />

Higher scores indicate greater similarity, allowing us to rank answers accordingly.

## Environment Setup & Running the Project

The project is fully developed on **Google Colab**, and since the dataset is too large to be stored in this repository, it is hosted on Google Drive. If you are also running the script in Colab, it will be automatically downloaded and processed via `gdown`.  

Alternatively, the project can also be run **locally**, but make sure you have `gdown` installed (`pip install gdown`), and that you also install the **required dependencies**:
```
pip install -r requirements.txt.
```
**⚠️ GPU Required:**

The project leverages **Microsoft/Phi-3-mini-4k-instruct** for query expansion, which requires CUDA. Ensure that a **CUDA-compatible GPU** is available for execution.
