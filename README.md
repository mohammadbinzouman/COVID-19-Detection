# COVID-19-Detection
Subset of the work I've done in my graduation project.


## Laboratory Based Datasets Description


### 1. Albert Einstein Hospital, Brazil Dataset <br>

The Albert Einstein Hospital dataset consisted of 5644 samples and 111 variables. The variables are divided into 4 dependent variables and 107 independent variables. The dependent variables are: ‘SARS-Cov-2 exam result’, ‘Patient admitted to regular ward’, ‘Patient admitted to semi-intensive unit’ and ‘Patient admitted to intensive care unit’. In our implementation, we only used 1 dependent variable, ‘SARS-Cov-2 exam result’ to predict COVID-19 infection.

➡️ **Handling Missing Values** <br>

Other than ‘Patient Age quantile’ and ‘SARS-Cov-2 exam result’, all other features have missing values. The least feature with missing values is 76.01% empty, that is 1354 out of 5644. Our approach into dealing with missing values is: **1)** we first shrunk the dataset approximately to the least feature with missing values, ‘Parainfluenza 1’ which results in a 1352 sample dataset. **2)** Then we dropped features with more than 75% missing values, which leaves us a new dataset with 1352 samples and 32 features. **3)** Finally, we used KNN imputation with k = 2 to fill in the missing values.

➡️ **Handling Zero Variance Features** <br>

There was only 1 feature with 1 unique value, ‘Parainfluenza 2’ (zero-variance feature), which we dropped.

➡️ **Handling Categorical Features** <br>

16 of the 31 features are categorical and have no missing values. We transformed categorical features using dummy encoding, which doubled the number of categorical 
features from 16 to 32.

➡️ **Feature Scaling** <br>

We standardized all features to have a mean of 0 and a variance of 1. This is important for algorithms such as SVM and KNN, where the distance between data points is critical.

➡️ **Imbalanced Target Variable** <br>

The shape of the dataset after the above preprocessing now has 1352 samples and 47 features. The target variable has a class distribution of 1240 negative samples and 112 positive samples, which is very imbalanced, and training a model on a highly imbalanced set will only lead to a model that predicts the minority class poorly or simply a biased model. <br> 
So, to solve this issue, we created 11 splits of the dataset. Each set has all the 112 positive samples and a unique set of 112 negative samples. We ran 7 classifiers and used 5-fold cross validation to test and train the models. Each model is trained and tested on each split of the dataset, and every split produces 5 results using 5-fold cross validation. From the 5 results, we take the average, which then gives us the average result for one split. This is done for every split, which means 11 results will be there. We take the average of the 11 splits to produce the finale result for a specific classifier.

➡️ **Feature Selection** <br>

Selected features were those with fewer than 75% missing values. There are two independent features, “Hemoglobin” and “Hematocrit” who had high correlation, and therefore the one with lowest feature importance score, “Hemoglobin,” was dropped.

<br>

### 2. Italian Society of Medical Radiology Dataset (SIRM) <br>

The SIRM dataset has 130 samples and 18 variables, 1 dependent variable ‘Decision label’ and 16 independent variables if you exclude sample id ‘Number’. Out of the 130 samples, 68 of them were COVID-19 positive and the remaining 62 were Flu positive, so we set the 68 COVID-19 cases as positive or ‘1’ and the 62 Flu cases as negative or ‘0’.
<br>
The people who constructed the dataset assigned missing values with a star symbol '✶' instead of leaving them empty. To see how many missing values we are dealing with, we replaced every '✶' with a NaN value. 

➡️ Handling Missing Values. <br>

Features with more than 50% missing values were dropped. We used Simple Imputer with a mean strategy to fill in the missing values. 

➡️ Handling Zero Variance Features <br>

There was 1 feature, ‘High risk zone’ which has only 1 unique value and therefore dropped.

➡️ Handling Categorical Features <br>

6 of the 8 features are categorical, so we manually transformed them into numerical features.

➡️ Feature Scaling <br>

We standardized all features to have a mean of 0 and a variance of 1.

➡️ Feature Selection <br>

Selected features were those with less than 50% missing values.


