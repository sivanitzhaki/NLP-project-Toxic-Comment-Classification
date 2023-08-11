# NLP-project-Toxic-Comment-Classification

In recent years, there has been a growing prevalence of online bullying and violence, capturing our attention. This project is dedicated to addressing this critical concern by delving into the analysis and categorization of user comments. The primary objective is to detect and classify various forms of toxic comments.

Within the scope of this modest endeavor, I will employ an LSTM architecture to categorize online comments based on their degrees of toxicity. Further details can be found below.

## Data
Upon exploration, I came across pertinent data on Kaggle. This data was originally released as part of a challenge centered around the classification of noxious comments. The dataset encompasses 159,571 instances of comments extracted from Wikipedia. These comments have been meticulously annotated by human evaluators to pinpoint instances of harmful conduct. The categories of toxicity encompass:

* Toxic
* Severe-toxic
* Obscene
* Threat
* Insult
* Identity-hate


## Preprocessing
The following operations were conducted to cleanse the dataset:

* Conversion of letters to lowercase.
* Removal of text enclosed in brackets, special characters, newline characters, and excessive spaces.
* Elimination of stopwords.
* Implementation of lemmatization using Spacy.
  
Following the data cleansing process, I employed a function for performing a train-test-validation split. This function is grounded in an algorithm outlined in an academic article titled 'On the Stratification of Multi-Label Data' by Sechidis K., Tsoumakas G., and Vlahavas I. (2011). This algorithm adeptly handles scenarios involving multi-label datasets, effectively incorporating both shuffling and stratification. Consequently, the resulting train-test-validation split is optimized to faithfully represent the original data distribution.

## The flow

Contemplating the project from a product perspective, we have established the subsequent workflow:

1. The user submits a comment.
1. The comment undergoes classification into either toxic or non-toxic categories - a binary classification.
1. In the event of toxicity, an assessment of the specific type of toxicity present in the comment is conducted - introducing a multilabel aspect to the problem.


## The tested models

1. 1st stage models: Binary Classification - toxic / not toxic
   * Random Forest Classifier
   * 	1D CNN
1. 2nd stage models: Classification toxicity level
   * CNN dedicated to multi-label classification problem
   * NN LSTM model

## Results

 * 1st stage models:
   ![result 1st stage models](https://github.com/sivanitzhaki/NLP-project-Toxic-Comment-Classification/assets/85245749/ffe28153-a907-42a1-a0fd-9f6674c5c386)
   

