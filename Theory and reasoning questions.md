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


**F, What is categorical data how is it handle? Use the terms nominal data, ordinal data, one-hot-encoding, dummy-variable-encoding and ordinal encoding in your answer.**

*Answer:* Categorical data is discrete qualitative categories rather than continous numerical values. 

Nominal data is data without any logical order, nominal comes from the Latin language but I can't remember which word lol. But essentially, it can be colors and colors don't have specific numbers. You can't say "Oh I want color 5". But using one-hot encoding, we can create binary 0/1 column for each category. 

Dummy variable encoding drops one category column to prevent multicollinearty.

Ordinal data are categories that have some type of meaningful ranking, it can be grapichs in a video. You can have "low settings", "medium settings" or "high settings". This can easily be converted into numerical rankings unlike nominal data (without using one-hot encoding.) Low = 1, medium = 2, high = 3 and ultra would be ....? Exactly, 4! 


**G, What is feature engineeering?**

*Answer:* The domain guided process of selecting, transforming, combining or creating new variables (features) from raw data to improve the predictive performance and interpretability of ML models.


**H, What does principle of parsimony mean?**

*Answer:* So if you have two competing models that are similar in performance, you should always choose the simpler model with fewer parameters, features or assumptions. Why? Because it's easier to interpret, easier to run on your computer/server and because it's less likely to suffer overfitting issues.


### 4. What is meant by "a model is a simplification of reality"?
*Answer:* Well, until we have and consider quantum compters as "boring" or "old", we can't really account for every possible variable or noise, nor can we predict the future. 

Machine learning can only give us a simplified, albeit usefull, general estimation of reality due to this.


### 5. What does a model being "overfitted" mean?
*Answer:* A model is considered overfitted if it learns both the underlying patterns and the random noise in the training dataset. Thus making it great at the training data, but terrible on new and unseen test data.

In other words, it's amazing at what we've already told it, but terrible at anything new.


### 6. Higher is better in scikit-learn scoring, what does that mean?
*Answer:* In sci-kit learn, all model evalution metrics are formatted so that larger numerical values represent superior performance. This allows internal optimization algorithms to consistently maximise the scoring metric. 

It's just a simpler and faster way to interpret the score of each model.

### 7. What is cross-sectional data, time series data and panel data? Give examples of when these categories can occour.
*Answer:* Cross-sectional data, multiple entities measured at a single point in time. An example of this is housing prices across different neighbourhoods in the same city of september 2026.

Time series data, a single entity measured over multiple time periods. Could be measuring how much one specific house has been worth throughout 20 years.

Panel data, multiple entites measured sequentially over multiple time periods. Could be how much a neighbourhood of houses have been worth from 2010 - 2020.

### **Reasoning Questions**

### 8. Give a few examples of real-world application areas within Machine Learning (ML). Feel free to search the web to answer the question.
*Answer:* Cars - Self-driving cars, driving assits, lane tracking etc

Enterprise: Will a customer churn? How many of our customers would buy this at this price? 

Social Media: Personalized algorithm to maximize user retention.

There are alot of areas where ML is useful and brings lots of value.

### 9. Generally speaking, higher is better in scikit-learn scoring, which is why, for example, scoring='neg_mean_squared_error' is used. Explain the logic behind this. That is, why we use 'negative' mean squared error.
*Answer:* Mean Squared Error is inherently a loss metric where lower values represent a batter model performance. The closer you get to zero, the better that model is. 

However, scikit-learn is hardcoded to always maximize the scoring function.
To make MSE and other loss function compatible with scikit-learn without rewriting the underlying algorithms, scikit-learn multiplies the loss value 
by -1. 

An MSE of 1.0 becomes -1.0, and MSE of 0.5 becomes -0.5.

-0.5 is more than -1.0. You "have" more money if you owe someone $50 than 
if you owe someone $100. 

If you owe someone $50, you only need $50 to be debt-free. Where as if you
someone $100, you need $100 to be debt-free. 
You can view the "debt" as the amount of "errors". You'd naturally select
the model with the least amount of debt/errors.





## ***Chapter 2***

### **Theory Question**

### 1. The chapter describes a checklist with 7 steps. Give a basic overview of those 7 steps. In reality, do you follow these steps to a T? Or do you jump around the steps to whichever is more suited at that moment? 
*Answer:* 

1. Define the problem and create an overview - Defining the project's goal.
2. Get access to the data - Focus on identifying and acquiring the necessary data.
3. EDA - Exploratory Data Analysis, explore the data, find errors, identify missing values, discover patterns etc. etc.
4. Process the data - Handle the missing values or remove incomplete rows found during EDA.
5. ML modeling - The part where you train, optimize and evalute the model against validation data to select the best model.
6. Present your solution to stakeholders - Show the result to the interested parties by using visualizations and tailoring the abstraction level to the target audience. 
7. Production deployment and monitoring - The final step is to deploy the model, creating unit tests to verify functionality and continuously monitor it's performance over time as models often need to retrain on newer relevant data to be viable.

In reality, you wouldn't follow these steps exactly as listed in our book, you'd do adapt to whatever is best for the time being. You'll more than likely end up jumping between certain steps becuase "oh no this went wrong" or "we didn't use the same .venv". There are many reasons why you'd need to jump in between them.

### 2. What is meant by putting a model into production? 
*Answer:* Putting a model into production means that it's actually been integrated into a project and that it's fulfilling it's intended purpose. Be it driving a car by itself, giving guesstimates of housing prices or predicting customer churn rates.


### 3. What is scikit-learn? The library follows a few central design principles, which ones are these? What are estimaters, predictors and transformers? 
*Answer:* Scikit-learn is an open-source machine learning library for Python. it provides tools for predictive data analysis and is built on top of scientific Python libraries such as NumPy, SciPy and Matplotlib. Hence the name, Scientific Kit Learn. 

Core design principles include consistency, inspection, non-proliferation of classes, composition and sensible defaults. 

Estimators - Any object capable of estimating parameters based on a dataset. The learning process is executed using the fix(x, y) method. 

Transformers - A type of estimator that can modify or filter a dataset. The modification is performed by the transform(X) method.

Predictors - A type of estimator capable of making predictions on new data, this uses the predict(x) method.

### 4. What is TensorFlow and Keras? 
*Answer:* TensorFlow is open-source meachine learning platform, but while it does support general machine learning. It's mainly designed for building training and scaling deep nerual networks. It's also very optimized allowing complex operations across different CPU's and GPU's.

Keras is a high-level deel learning API written in Python. It is designed to prioritize developer experience. It does this by abstracting the low-level complexities of neural network construction. Like our teacher said, we're programmers and not mathmaticians. It's also a part of TensorFlow and can be accessed by using "tf.keras".



### **Reasoning Questions**

### 5. Kalle and Stina discuss ML, Kalle says that "if I've trained a model and it doesn't perform well enough on the testdata, I'll have to adjust the model untill it does". Stina says: "It's a big mistake to do that, the only thing you'll achieve is that you'll be overfitting the testdata. The entire purpose of the testdata will be gone then". What do you think?
*Answer:* Stina is 100% correct since by doing what Kalle is planing on doing, you'll risk information leaks and overfitting. 

A dataset is supposed to be an unbiased proxy for unseen real-word data. The entire purpose is to give an honest, final statement of how well the model generalizes after training and hyperparameter runing are complete.


### 6. Many AI/ML projects don't accomplish their initial goals or even reach a prototype phase. Why do you think that is? 
*Answer:* I don't think that the high failure rate is because of bad mathmatics or bad algorithms, it more than likely is due to organizational issues and data-related challenges. 

If  you have you something or someone pushing for the fastest solution rather than the best solution, you might never get to see the true potential of the what could've been. 

Also, if you've missed something important in the data, lack the domain knowledge around that specific topic you're working with OR simply have bad data. Your output will still be sub-optimal since your output depends on your input. 

Bad input = bad output, no matter how well you actually trained the model. That's my take on it. 

So data analysis, data gathering and understanding the domain is crucial. 


## ***Chapter 3***

### **Theory Question**

### 1. What characterizes regression problems? Give some examples of application areas.
*Answer:* A reegression problem is a type of supervised learning task where the goal is to predict a continour numerical value (or a real number) based on one or more input features. 

### 2. Explain the evaluation metrics RMSE, MSE, and MAE.
*Answer:* MSE "punishes" or "peenalizes" larger errors because the error are squared in Mean Squared Error. It calculates the average of the squared differences between the predicted values and the actual values. 

Root Mean Squared Error (RMSE), is the square root of the MSE, so it "un-does" to squaring to make it easier to interpret. 

Mean Absolute Error (MAE), calculates the average of the absolute differences between predicted and actual values. It shows all errors propotionally isn't as sensitive to outliers as RMSE or MSE.

### 3. If we are to rank different models, does it matter whether RMSE or MSE is used? Why?
*Answer:* No it really doesn't matter since one is just squaring a number, and the other is "un-squaring" that squared number. So if we have to models, one model A and one model B. Model A can have a lower MSE than model B, which means that it'll also have a lower RMSE.

MSE = 3^2 = 3 * 3 = 9
RMSE = 9 squared = 3

### 4. Give a simple explination as to what gradient descent is.
*Answer:* Gradient Descent is an optimization algorithm used to minimize a model's cost function by iteratively tweaking its parameters.

### 5. What is the bias-variance trade-off? Why are more complex models not always better?
*Answer:* Bias happens from overly simplistic assumptions in the learning algorithm. High bias causes undefitting. 

Variance happens when the model is extremly sensitive to fluctions in the training dataset, it'll cause overfitting where the "line" perfectly tracks each data point instead of creating a more realistic overview. 

As a model becomes more and more complex, the bias decreases BUT the variance increases. So that is the bias-variance trade-off. You need to find a balance, or as we say in swedish, it needs to be "lagom" :D

### 6. Some commonly used models for regression problems are listed below. EGive a simple explination to how each model works. Also read through each model's documentation; note that you do not need to understand all the details from the documentation, but it is good to have read through it.

A, Linear regression -
*Answer:* Fits a linear equation to the data by finding feature
weights that minimize the residual sum of squares between predicted
and actual target values.

B, Ridge regression -
*Answer:* A linear regression variant that adds a penalty equal to 
the sum of squared feature weights to the cost function.

C, Lasso regression -
*Answer:* Another variant of linear regression that adds a penalty
equal to the sum of absolute feature weights. 

D, Elastic net -
*Answer:* A hybrid approach combining both Lasso and 
Ridge penalties.

E, Support vector machines -
*Answer:* Linear regression tries to minimize error, while SVR tries 
tries to fit as many data points as possible within a wide margin 
around the regression line.

F, Decision trees - 
*Answer:* Splits the dataset recursively into smaller regions based
on feature thresholds.

G, Ensemble learning -
*Answer:* Voting Regressor: Combines predictions from multiple 
distinct model type and averages their outputs.

Bagging Regressor: Trains multiple instances of the same base model 
on different random subsets of the training data.

H, Random forest -
*Answer:* Basically a bunch of Decision Trees trained using bagging
with an extra layor of random sprinkled ontop. Only considering a 
random subset of features at every split, it produces diverse trees
whose predictions are average.

### 7. What is meant by white box models and black box models?
*Answer:* 

### 8. What is the difference between bagging and pasting?
*Answer:*

### **Reasoning questions**

### 9. Explain how figure 3.1 on page 113 can be interpreted
*Answer:*

### 10. Explain how figure 3.13 on page 140 can be interpreted. How does it relate to figure 3.14 on page 141?
*Answer:*

### 11. We have learned the evaluation metrics RMSE, MSE, and MAE. Another evaluation metric is what is referred to as the coefficient of determination, or $R^2$. Explain what kind of metric this is.
*Answer:*