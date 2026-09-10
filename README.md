# sentiment-analysis-nlp-comparison

# Sentiment Analysis – NLP Model Comparison

## Project Overview

This project evaluates and compares three different Natural Language Processing (NLP) approaches for binary sentiment classification of movie reviews.

The objective is to determine which approach provides the best balance of predictive performance, training efficiency, computational cost, and suitability for deployment.

Three approaches were evaluated on the same dataset and identical test set:

1. TF-IDF + Logistic Regression
2. Embeddings + BiLSTM
3. Pretrained VADER

The final recommendation is to use **TF-IDF + Logistic Regression** for this use case.

---

## Problem Statement

Movie reviews contain opinions that can be classified as either positive or negative.

The goal of this project is to build and compare different sentiment analysis approaches and determine which model is most appropriate for a practical production scenario.

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Training time

---

## Dataset

The project uses the **NLTK Movie Reviews dataset**.

### Dataset Details

- Total reviews: 2,000
- Positive reviews: 1,000
- Negative reviews: 1,000
- Training data: 80%
- Testing data: 20%

The same test set was used to evaluate all three approaches, enabling a fair comparison.

---

## Text Preprocessing

The following preprocessing steps were applied to the movie reviews:

- Lowercasing
- Punctuation removal
- Number removal
- Stop-word removal
- Tokenization

The preprocessing pipeline was applied consistently before model evaluation.

---

## Methodology

### 1. TF-IDF + Logistic Regression

The first approach represents reviews using **TF-IDF (Term Frequency–Inverse Document Frequency)** and uses Logistic Regression for binary sentiment classification.

**Pipeline:**

Movie Reviews → Text Preprocessing → TF-IDF Vectorization → Logistic Regression → Positive / Negative

This approach achieved the strongest overall performance.

---

### 2. Embeddings + BiLSTM

The second approach uses word embeddings followed by a **Bidirectional Long Short-Term Memory (BiLSTM)** neural network.

**Pipeline:**

Movie Reviews → Text Preprocessing → Word Embeddings → BiLSTM → Positive / Negative

The BiLSTM approach required significantly more training time than Logistic Regression and performed worse on this dataset.

---

### 3. Pretrained VADER

The third approach uses **VADER**, a pretrained sentiment analysis model.

Unlike the other two approaches, VADER does not require model training on the movie-review dataset.

**Pipeline:**

Movie Review → VADER → Sentiment Score → Positive / Negative

VADER provides rapid predictions but its performance was lower than the best-performing trained model.

---

## Results

All three approaches were evaluated on the same test set.

| Model | Accuracy | F1 Score | Training Time |
|---|---:|---:|---:|
| **TF-IDF + Logistic Regression** | **85.00%** | **0.8500** | **~0.1 sec** |
| BiLSTM | 61.75% | 0.6222 | 17.16 sec |
| VADER | 63.50% | 0.6933 | No training |

### Best Performing Model

**TF-IDF + Logistic Regression** achieved:

- Accuracy: **85.00%**
- F1-score: **0.85**
- Training time: **~0.1 seconds**

It provided the best overall combination of predictive performance and computational efficiency.

---

## Key Findings

- TF-IDF + Logistic Regression achieved the highest accuracy and F1-score.
- BiLSTM required significantly more computational effort but underperformed on this relatively small dataset.
- VADER required no model training and provided immediate predictions.
- Model selection should consider dataset size, domain, computational requirements, and deployment constraints.
- A more complex model is not necessarily the best production solution.

---

## Production Recommendation

### Recommended: TF-IDF + Logistic Regression

TF-IDF + Logistic Regression is recommended for this use case because it provides the best balance of:

- Predictive performance
- Training speed
- Computational efficiency
- Ease of maintenance

### Alternative: VADER

VADER can be useful when:

- Rapid deployment is required
- No labelled training dataset is available
- A lightweight pretrained approach is preferred

### When to Consider BiLSTM

BiLSTM may become more appropriate when substantially larger labelled datasets are available and the additional computational cost is justified.

---

## Technologies Used

- Python
- Natural Language Processing (NLP)
- TF-IDF
- Logistic Regression
- BiLSTM
- Word Embeddings
- VADER
- NLTK
- Jupyter Notebook

---

## Project Structure

sentiment-analysis-nlp-comparison/
│
├── NLP_Sentiment_Analysis.ipynb
├── NLP_Sentiment_Analysis.pptx
├── README.md
├── LICENSE
└── .gitignore

### Files

**NLP_Sentiment_Analysis.ipynb**

Contains the implementation of the sentiment analysis pipelines, preprocessing, model evaluation, and comparison.

**NLP_Sentiment_Analysis.pptx**

Contains the project presentation, results, findings, and final recommendation.

**README.md**

Contains project documentation, methodology, results, and recommendations.

---

## Evaluation Metrics

### Accuracy

Measures the proportion of correctly classified reviews.

### Precision

Measures how reliable the positive predictions are.

### Recall

Measures how many positive reviews were correctly identified.

### F1-score

Combines precision and recall into a single metric and provides a balanced measure of classification performance.

---

## Conclusion

This project demonstrates that model complexity does not always translate into better performance.

On the NLTK Movie Reviews dataset, **TF-IDF + Logistic Regression** significantly outperformed both BiLSTM and VADER while requiring substantially less training time.

Therefore, Logistic Regression is recommended as the production solution for this specific use case.
