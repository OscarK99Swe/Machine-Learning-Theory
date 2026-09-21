## ***Chapter 1***

### **Theory Question**

### 1. How is AI, ML and DL connected?
*Answer:* DL is a part of ML, and ML combined with DL is a part of AI, they are nested subsets within computer science. 

### 2. What are the four "problem categories" in ML?
*Answer:* Supervised learning (classification and regression), Unsupervised learning (clustering and dimensionality reduction), Semi-supervised learning and reinforcement learning. 


### 3. Explain the following: 

**A, What is the purpose of dividing up data in trainingdata, validationdata and testdata?** 

*Answer:* Training data is used directly by the algorithm to learn parameters, validation data i used during model development to tune hyperparamters and compare different model architectures without being biased in the final evaluation. Test data is used in the very end to provide an unbiased estimate of how well the final model generalizes to brand new unseen real-world data.


**B, What is k-split crossvalidation?** 

*Answer:* A resampling validation technique where the dataset is randomly partitioned into K equal sized folds. The model is trained K separate times, in each iteration, K-1 is used as the training data and the remaining fold is used as validation data. Averaging the performance across all K runs gives a decent performance estimate that minimzes data differences.


**C, What is root mean squared error (RMSE)?**

*Answer:* A standard regression metric that measures the square root of the average squared differences between predicted values (Y^) and actual target values (Y). (It's supposed to be have the little triangle ^above the Y-letter itself but you know what I mean).


**D, What is a hyperparameter? What is a parameter?**

*Answer:* A parameter is what the model learns from the data, while hyperparameters are HOW the model learns given the settings defined by us before running the model.


**E, What is gridsearch and how are the words "grid" and "search" connected with the process that takes place. The hyperparameter has refit as a default value, what does this mean?**

*Answer:* Grid search is a technique used for hyperparameter tuning. "Grid" refers to the multi-dimensional grid formed by taking all combinations of hyperparameter values. "Search" refers to evaluating model performance across every coordinate point in this grid via cross-validation to find the best combination.

refit=true: Once the best hyperparameter set is found, scikit-learn automatically retrains (refits) the model on the entire dataset using the new best settings.


**F, What is categorical data how is how it handle? Use the terms nominal data, ordinal data, one-hot-encoding, dummy-variable-encoding and ordinal encoding in your answer.**

*Answer:* Categorical data is discrete qualitative categories rather than continous numerical values. 

Nominal data is data without any logical order, nominal comes from the Latin language but I can't remember which word lol. But essentially, it can be colors and colors don't have specific numbers. You can't say "Oh I want color 5". But using one-hot encoding, we can create binary 0/1 column for each category. 

Dummy variable encoding drops one category column to prevent multicollinearty.

Ordinal data are categories that have some type of meaningful ranking, it can be grapichs in a video. You can have "low settings", "medium settings" or "high settings". This can easily be converted into numerical rankings unlike nominal data (without using one-hot encoding.) Low = 1, medium = 2, high = 3 and ultra would be ....? Exactly, 4! 


**G, What ir feature engineeering?**

*Answer:* 


**H, What does principle of parsimony mean?**

*Answer:*


### 4. What is meant by "a model is a simplification of reality"?
*Answer:*


### 5. What does a model being "overfitted" mean?
*Answer:*


### 6. Higher is better in scikit-learn scoring, what does that mean?
*Answer:*

### 7. What is cross-sectional data, time series data and panel data? Give examples of when these categories can occour.
*Answer:*

### **Reasoning Questions**

### 8. Give a few examples of real-world application areas within Machine Learning (ML). Feel free to search the web to answer the question.
*Answer:*

### 9. Generally speaking, higher is better in scikit-learn scoring, which is why, for example, scoring='neg_mean_squared_error' is used. Explain the logic behind this. That is, why we use 'negative' mean squared error.
*Answer:*