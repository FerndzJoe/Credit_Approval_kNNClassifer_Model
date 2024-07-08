### Problem Statement 

This module introduced both the K Nearest Neighbors model as well as a variety of different metrics for classification. It is important to select and understand the appropriate metric for your task. This exercise is meant to get practice considering the difference between these new classification metrics and accompanying evaluation tools. Specifically, explore datasets related to business from the UCI Machine Learning Repository here.

Select a dataset of interest and clearly state the classification task. Specifically, describe a business problem that could be solved using the dataset and a KNN classification model. Further, identify what you believe to be the appropriate metric and justify your choice. Build a basic model with the KNearestNeighbor and grid search to optimize towards your chosen metric. Share your results with your peers.

#### Credit Approval Dataset

After reviewing all the datasets, I decided to analyze the credit approval dataset. 

**Per UCI Repository**

This file concerns credit card applications.  All attribute names and values have been changed to meaningless symbols to protect confidentiality of the data.
  
This dataset is interesting because there is a good mix of attributes -- continuous, nominal with small numbers of values, and nominal with larger numbers of values.  There are also a few missing values.

Here's the link to the dataset: https://archive.ics.uci.edu/dataset/27/credit+approval

<img width="1290" alt="Screenshot 2024-07-07 at 5 24 24 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/7f5af764-2bc1-4cc3-a94a-d5206e780d46">

<img width="951" alt="Screenshot 2024-07-07 at 5 24 50 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/c61d2373-697e-40a4-93a4-0dd115390987">

<img width="383" alt="Screenshot 2024-07-07 at 5 25 35 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/88a5f203-45aa-4d90-b520-dbb482554404">

The dataset has the following information:
```
   name     role         type demographic description units missing_values
0   A16   Target  Categorical        None        None  None             no
1   A15  Feature   Continuous        None        None  None             no
2   A14  Feature   Continuous        None        None  None            yes
3   A13  Feature  Categorical        None        None  None             no
4   A12  Feature  Categorical        None        None  None             no
5   A11  Feature   Continuous        None        None  None             no
6   A10  Feature  Categorical        None        None  None             no
7    A9  Feature  Categorical        None        None  None             no
8    A8  Feature   Continuous        None        None  None             no
9    A7  Feature  Categorical        None        None  None            yes
10   A6  Feature  Categorical        None        None  None            yes
11   A5  Feature  Categorical        None        None  None            yes
12   A4  Feature  Categorical        None        None  None            yes
13   A3  Feature   Continuous        None        None  None             no
14   A2  Feature   Continuous        None        None  None            yes
15   A1  Feature  Categorical        None        None  None            yes
```
Sample data from the dataframe:

<img width="765" alt="Screenshot 2024-07-07 at 5 35 26 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/8e0f0c82-5e19-4925-b13f-313cae4f07ac">

### Exploratory Data Analysis (EDA)

There are a total of 690 records. Some of the data is missing. After fixing all the missing data, the final dataset for processing was 653 rows.

Plotting the numerical data, we find that the data is mostly skewed right.
![histogram_numerical_cols](https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/73dfdbc9-b089-4132-a5d8-21c351dffe00)

The target variable is spread at 45% positive credit approval and 55% negative credit approval.
<img width="653" alt="Screenshot 2024-07-07 at 5 42 02 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/b88edaa1-343a-4284-9f7f-2bcc16522e5f">

Pearson's Correlation on the numerical dataset gives:
![Pearsons Correlation - Numerical Data](https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/e4c7fd1f-a6cb-4190-b3dd-6e0c969cad9a)

### Model Selection and Validation
The exercise is to use kNNClassifier to perform analysis. Created a pipeline and ran the model against a few hyper parameters.

The Pipleine is as shown below:

<img width="653" alt="Screenshot 2024-07-07 at 5 38 36 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/7dc51522-e1e0-41f5-bfe5-c0850323c805">

Ran the kNNClassifier with n_neighbors = 5 (default value), 12 , 20, and 27.

The Model accuracy for k=5 is 80.15% and for k=12 is 87.02%. This is very clearly evident from the Confusion Matrix 

<img width="654" alt="Screenshot 2024-07-07 at 6 11 39 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/8c7a125c-1203-4262-bb92-ec0f62f95adf">

<img width="654" alt="Screenshot 2024-07-07 at 6 25 58 PM" src="https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/19505dac-da4b-4b00-90ef-f250e47817d2">

The Precision and Recall curve and the ROC curve for n_neigbhors = 12 are shown below.

![Precision_vs_Recall_kNN-12](https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/f2be769c-683f-45b2-9881-d9d524b3665a)

![ROC_Curve_kNN-12](https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/94250e86-d6f2-46d5-a13f-2e023f083d60)

The summary view of all the ROC curves is as shown below.

![roc_All_Inclusive](https://github.com/FerndzJoe/Credit_Approval_kNNClassifer_Model/assets/96799409/ccf85e8e-6cae-465c-98aa-ce2de12e68c8)

### Conclusion:
The kNNClassifier model with 12 nearest neighbors produces the highest model accuracy. However, with GridSearchCV, the results were for 27 nearest neighbors.
The model is able to reduce the false positives and false negatives as the nearest neighbors increase peaking at 12 and 27. 

### Opportunities
Learning more about the data would benefit the analyst / data scientist to expand the model and work with missing data. In this dataset, there isn't enough documentation about the attributes. This limits the analyst / data scientist to perform any further analysis on the missing data.

