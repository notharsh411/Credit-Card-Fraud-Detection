# Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)
![Pandas](https://img.shields.io/badge/pandas-1.3.3-blue)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-0.24.2-orange)
![License](https://img.shields.io/badge/License-MIT-green.svg)

An end-to-end machine learning project focused on identifying fraudulent credit card transactions from a highly imbalanced dataset. This repository contains a Python notebook that walks through the entire process, from data exploration and preprocessing to model training and evaluation.

---

## 📋 Table of Contents
* [Overview](#-overview)
* [Dataset](#-dataset)
* [Project Workflow](#-project-workflow)
* [Key Techniques & Results](#-key-techniques--results)
* [How to Run](#-how-to-run)
* [Dependencies](#-dependencies)

---

## 🎯 Overview

The primary goal of this project is to build a reliable classification model that can accurately distinguish between legitimate and fraudulent credit card transactions. Due to the sensitive nature of fraud detection, the model is optimized for high **recall** on the fraud class, ensuring that the maximum number of fraudulent transactions are identified, even at the cost of some false positives.

---

## 🗂️ Dataset

This project utilizes the **Credit Card Fraud Detection** dataset available on Kaggle.

* **Source:** [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
* **Content:** The dataset contains transactions made by European cardholders in September 2013.
* **Size:** It features 284,807 transactions, of which only 492 (0.172%) are fraudulent.
* **Features:**
    * `Time` and `Amount` are the only raw features.
    * `V1` through `V28` are the result of a PCA transformation, used to protect user privacy.
    * `Class` is the target variable (1 for fraud, 0 for legitimate).

The most significant challenge presented by this dataset is its **extreme class imbalance**.

![Class Imbalance](https://i.imgur.com/3l2e4E5.png)

---

## ⚙️ Project Workflow

The project is structured into a clear, step-by-step process within a single Jupyter/Colab notebook:

1.  **Data Loading & Exploration:** The dataset is loaded using Pandas, and an initial analysis is performed to understand its structure, statistics, and data types.
2.  **Data Visualization:** Seaborn and Matplotlib are used to visualize the class imbalance and the distributions of the `Time` and `Amount` features.
3.  **Data Preprocessing:**
    * **Scaling:** The `Time` and `Amount` features are scaled using `StandardScaler` to bring them to a comparable range with the PCA features.
    * **Handling Imbalance:** **Random Under-Sampling** is employed to create a new, balanced dataset. This involves taking all 492 fraudulent samples and randomly selecting 492 non-fraudulent samples.
4.  **Model Training:** A **Logistic Regression** model is trained on the balanced dataset. This simple yet effective model serves as a strong baseline.
5.  **Model Evaluation:** The trained model's performance is evaluated on a held-out test set using:
    * **Accuracy Score**
    * **Confusion Matrix**
    * **Classification Report** (Precision, Recall, F1-Score)

---

## 💡 Key Techniques & Results

### Random Under-Sampling
To combat the class imbalance, we create a perfectly balanced dataset. This prevents the model from becoming biased towards the majority class and allows it to learn the patterns of fraudulent transactions effectively.

![Balanced Dataset](https://i.imgur.com/JbYgY8k.png)

### Model Performance
The Logistic Regression model, when trained on the balanced data, achieves excellent results on the test set.

* **Accuracy:** ~94%
* **Precision (Fraud):** ~97%
* **Recall (Fraud):** ~91%

The high recall for the fraud class is particularly important, as it indicates that our model successfully identifies over 90% of all actual fraudulent transactions.

![Confusion Matrix](https://i.imgur.com/kYwZ6Jt.png)

The detailed classification report confirms the model's strong performance across all key metrics for both classes.

---

## ▶️ How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/credit-card-fraud-detection.git](https://github.com/your-username/credit-card-fraud-detection.git)
    cd credit-card-fraud-detection
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Download the dataset:**
    * Download `creditcard.csv` from the [Kaggle link](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud).
    * Place the `creditcard.csv` file in the root directory of the project.
4.  **Run the notebook:**
    * Open and run the `credit_card_fraud_detection.ipynb` notebook in a Jupyter environment or Google Colab.

---

## 📦 Dependencies

* `pandas`
* `numpy`
* `scikit-learn`
* `matplotlib`
* `seaborn`
