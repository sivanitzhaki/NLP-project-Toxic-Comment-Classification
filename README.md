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

Contemplating the project from a product perspective, I have established the subsequent workflow:

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

   Both models achieved a high level of accuracy and exhibited close performance. However, the CNN model outperformed the random forest classifier with a superior score and significantly faster processing speed.

 * 2nd stage models:
![result 2nd stage models](https://github.com/sivanitzhaki/NLP-project-Toxic-Comment-Classification/assets/85245749/d8428615-d5a7-4a9e-ae73-3f9f6781ec95)

- Both models reached a high level of accuracy of more than 85%.
- The LSTM model, in particular, demonstrates a superior outcome.
- However, the outcomes reveal a shared challenge for both models in distinguishing between two specific levels of toxicity - threat and identity hate.

  
![train validation acc score per epoch](https://github.com/sivanitzhaki/NLP-project-Toxic-Comment-Classification/assets/85245749/206ec1a3-5558-42c4-a817-a32ca3f5883f)

- The CNN model seems to underfit - Probably because the imbalanced dataset.
- A possible solution for that would be to train for less epochs. But I decided that two epochs is not long enough to the learning stage.
- Both models learn quite fast, probably due to imbalanced dataset.

  ## User interface
  
  Finally, I created a user interface where a user could enter a comment and get its classification in real time.

  Here is an example:
  ![interface](https://github.com/sivanitzhaki/NLP-project-Toxic-Comment-Classification/assets/85245749/94f658f9-f92e-4f06-a9af-2845d66508a1)

## Further Work

1. To develope the model further I suggest to perform data augmenattion for the unrepersented labels.

1. Transformers & BERT - while examining different models, I experimented with BERT but had many issues implementing it due to computing power. I recommend trying to find a suitable BERT model and fine-tuning it in order to get better results.

1. Train the 2nd stage models on a data set that has major\only toxic comments and check if this solves the problem of identifying the levels of toxicity that the models failed to learn.

1. Additional evaluation metrics can be examined.

  
