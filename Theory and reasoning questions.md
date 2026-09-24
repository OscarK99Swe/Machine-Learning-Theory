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
*Answer:* White box models interpret models whose internal mechanics,
rules and parameter weights can be easily inspeceted and understood
by humans.

Meanwhile, black box models are way more accurate but almost 
impossible for humans to understand.

### 8. What is the difference between bagging and pasting?
*Answer:* Bagging is when sampling is performed with replacement, 
meaning that a single training instance can be sampled multiple times
for the same sub model.

Pasting is when sampling is performed without replacement. Each 
training instance can only appear once in a given suo-model's 
dataset.

### **Reasoning questions**

### 9. Explain how figure 3.1 on page 113 can be interpreted
*Answer:* Figure 3.1 shows a linear regression model trying to
predict values generated based on age.

The black dots represent the actual data poitnts we have
in the datset. 

The solid blue line represents the predicted values
generated by the gression model's equations. 

The parameters O^0 and O^1, represent the line's intercept and slope.
By interecept, I mean where the line crosses the y-axis.

The red vertical lines show the residuals, which visualize the 
errors by showing the exact difference between the actual data points
and the models predicted values. 

So essentially, it's showing us what the model thinks is right, 
what is actually right and how far off the model was.

### 10. Explain how figure 3.13 on page 140 can be interpreted. How does it relate to figure 3.14 on page 141?
*Answer:* So figure 3.13 displays the logical flowchart of a 
decision tree regressor.

Each node displays a splitting condition, the current squared error,
the number of samples in that node and the predicted continous value
for that subset of data.

Data points are routed down the left branch if the condition is true 
and the right branch if false.

And figure 3.14 maps the lgoical splits from 3.13 onto a 2D geometric
space, allowing us to interpret it easier. 

The first split in the root node (X2 <= 0.438) corresponds to the
main horizontal black line in figure 3.14, dividing the entire plot
into upper and lower sections.

Second split on the "True" branch and the "False" branch, act as 
boundary lines, dividing the space into four distinct rectangular 
regions. 

These four regions correspond exactly the the four leaf nodes at the
bottom of the tree.

The colors themselves do actually have some sort of meaning, the 
saturated blue region represents the lowest predicted value (-62.9)
and the saturated red region represents the highest (62.8).


### 11. We have learned the evaluation metrics RMSE, MSE, and MAE. Another evaluation metric is what is referred to as the coefficient of determination, or $R^2$. Explain what kind of metric this is.
*Answer:* R^2, otherwise known as "the coefficient of 
determination", is an evaluation metric that measures the proportion
of variance in the dependent variable, the target, that can be 
explained by the independent variables, features, in the model.

Mainly, R^2 is a scale-free relative metric unlike: RMSE, MSE and MAE.

If you get an R^2 score of 1.0, it means that your model's 
predictions perfectly match the actual data.

If you get an R^2 score of 0.0, it indicates that the model performs
exactly as well as a naive baseline model that always predicts that
mean value of the target variable.

A negative R^2 score however, indicates that the model performs worse
than a simple baseline that predicts the mean. Meaning that the 
regression line fits the data exceptionally poorly. Time to create a
new model! 


## ***Chapter 4***

### **Theory Question**

### 1. What characterizes classification problems? Give some examples of application areas.
*Answer:* A classification problem is a type of supervised learning 
task where the target variable consists of discrete categories or 
class labels rather than continuous numbers. There's Binary 
classification, true or false, and there's multiclass classification,
more than two mutually exclusive classes.

You can use classification for: 

* Customer analysis - will a customer churn? 
* Healthcare - Does the patient have a certain condition or not?
* Image recognition - Does the image contain this, that or what? 

Some of the captcha's we used to have to do back in the day were 
essentially classification.


### 2. Explain how the OvR and OvO algorithms work
*Answer:* OvR and OvO, are binary classifiers the handle multiclass
problems. Not owls.

***OvR or One-vs-Rest, trains *N* binary classifiers for an *N*-class 
problem.*** 

Classifier *i* is trained to distinguish Class *i* against all 
remaining *N* - 1 classes combined. 

To predict a new instance, all *N* classifiers run, and the class
whose classifier outputs the highest confidence score or probability
is choosen. 

Essentially, it checks if a certain datapoint/data entry belongs to
a certain Class or not.

***The Owl, OvO or One-vs-One***

Trains a separate binary classifier for every pair of classes, 
resulting in **(*N* x (*N* - 1))/2** classifiers. 

If we have four classes, A, B, C and D. It'll train 6 different models.


A vs B | A vs C | A vs D 

B VS C | B vs D 

and 

C vs D

What we see is that it essentially keeps going "right" or 
"next-in-line" untill it reaches the end.

To predict a new instance, it runs all models through a 
"duel system" (or an epic battle of math), where each model casts a 
vote for one class. The class with the most votes wins.


### 3. Explain the following evaluation metrics:
*Answer:* 

***A, Confusion matrix -*** A matrix of four counts that visualizes how well a model 
performs by comparing the true values and predicted values. 

Each row represents the true class while each column represents 
the predicted class. 

True Positive (TP): Actual positive correctly predicted as positive

True Negative (TN): Actual negative correctly predicated as negative.

False Positive (FP): Actual negative incorrectly preddict as positive.

False Negative (FN): Actual positive incorrectly predicted as negative.

***B, Accuracy*** - Overall proportion of correct predictions 
out of total prediction made. 

*TP + TN / TP + TN + FP + FN*

***C, Precision*** - Proportion of positive predictions that were 
actually correct 

*TP / TP + FP*

***D, Recall*** - Proportion of actual positive instance that the 
model successfully caught. 

*TP / TP + FN* 

***E, $F_1$-score*** - The "harmonic mean" of precision and recall.

*2TP / 2TP + FP + FN*

***F, ROC curve*** - The Receiver Operating Characteristic (ROC) curve is similiar to the precision-recall
curve, but instead of visualizing the correlation between pricision and recall, 
it visualizes the correlation between True Poristive Rate (TPR) and False Positive Rate (FPR). 



### 4. What is the precision-recall tradeoff?
*Answer:* Classification models output probability scores between 
0 and 1, a default threshold (ex. 0.5) converts these probablities
into final class predictions. 

The precision-recall tradeoff says the increasing precision typically
decreases recall and vice versa. So it'll all about the balance yet
again, similiar to the bias-variance trade off from chapter 2.



### 5. Some commonly used models for classification problems are listed below. Give a simple explination as to how each model works. Also read through each model's documentation; note that you do not need to understand all the details from the documentation, but it is good to have read through it.
*Answer:* 

***A, Logistic regression*** - It calculates a weighted linear combination
of input features and passes the result through the sigmoid function.

This maps any real value to a probility between 0 and 1. If the 
probability exceeds the threshold, the istance is assigned to the 
positive class.

***B, Support vector machines*** - Finds the optimal decision boundary (hyperplane) 
that seperates classes with the maximum margin. Maximum marging is the distance between
the boundary and the closest data points of any class, AKA support vectors.

It uses kernel tricks such as "polynominal", among others, to map complex non-linear data 
into higher deminsions where it becomes linearly separable.


***C, Decision trees*** - Recursively partitions data into smaller subgroups by picking features
and thresholds that best segregate classes. The final product is a tree structure 
where leaf nodes assign class labels based on majority vote.

***D, Ensemble learning*** - Ensemble Learning entails two ways of going about things. 
You've got: 

* *Voting Classifier* - Which combines predictions from multiple distinct algorithms,
could be logistic regression + svc + decision tree as an example. It can then use "Hard Voting"
which is majority rule or "soft voting" which averages predicited probablities, to make it's 
own classification.

* *Bagging Classifier* - Which trains multiple instances of the same base estimator on 
different bootstrap samples, random subsets drawn with replacement, of the training set.
This aggregats predictions via majority vote.


***E, Random forest*** - A collection of many Decision Trees trained using bagging,
with an extra layer of randomness. When choosing splits at each node, it only considers
a random subset of featues. This decorrelates the individual trees which reduces variance
without increasing bias. Very smart, very sigma, very nice.

***F, Extra trees*** - An extension of Random Forests that indroduces even more randomness.
Instead of searching for the mathematically optimal split threshold for each feature, it 
selects random thresholds for each feature candidate and picks the best of those options.
This increases training speed and lowers the model variance even more. 


### 6. What does it mean that we can look at feature importance using tree models such as decision trees or random forests?
*Answer:* Tree based models calculates feature importance by meassuring how much each 
eature contributes to reducing impurity across all nodes and tress in the model. 

This essentially makes the model easier to interpret and helps with identifying what
actually drivs the predictions AND! It also allows for feature selection by removing
irrelevant features to simply the model.


### **Reasoning questions**

### 7. Stina says to Kalle during a lunch conversation, "I want the highest possible precision for our classification model." Kalle thinks for a while and says, "But what happens to recall then?" What would you have answered? In what cases might you want as high a precision as possible? In what cases could that be bad? If we consider the justice system where a final verdict can lead to prison, what can we say about the precision-recall tradeoff?
*Answer:* If you set a model to only make predictions when it's 100% correct,
you'll end up free falling recall due to the precision-recall trade off. 

You'd only want to maximize precision if the false alarm can have huge negative
consequences. A dramatic comparision would be in the theater of war. Your AI-piloted
drone has spotted a heat signature matching a vehicle. With high precision, 
it might deviate and refuse to engage due to not being 100% certain of a PID 
(positive Identification). While on the other hand with low precision, your
AI drone just commited a war crime by engaging a civilian trying to flee. 

Now this example is really dark, but situations like this are actually happening
right now.

Our justice system in Sweden would much rather let a guilty man walk than
to jail an innocent man. But if we use a 100% precision driven classification 
model, it would mean that most guilty men walk free and justice would never be
delievered. 

A lower precision and higher recall would risk sending an innocent man
to prison. 

Statistically speaking, there more than likely is an innocent man in 
prison right now. It might sound cruel but that's reality. 

Regarding the precision-recall trade off. You've got to pick 
what you're most comfortable, it has to be a balance of the two. 
Neither or can be exclusive.



### 8. Explain how Figure 4.8 on page 175 can be interpreted.
*Answer:* Figure 4.8 visualizes the decision boundaries and predicted
probabilities of a lgostic regression model perfoming binary classification.

The y-axis shows the probality for two classes, 0 for purple and 1 for yellow.
The datapoints are mapped in a scatter plot display with induvidual observations
from the dataset. They are also color coded according to which class they've
been to classified to. 

Regarding the background colors, the top left part is purple and the plots 
within this color range belong to class 0. The bottom right part is yellow 
and the plots within this part belong to class 1. 

Interesting thing to note is the different colors, gradient, in the middle. 
That is the decision boundary which illustrate the linear nature of logistic regression. 
These diagonalm different colored lines, are near the 0.5 probability for class 1 
and acts as the berlin wall (sorry, the border) in which the model shifts it's prediction.



### 9. On page 209 it says, "on the training data we use .fit_transform(), on the validation data and the test data we only use .transform()." Explain the logic behind this.
*Answer:* The logic behind this is to both prevent data leakage and ensure consistent scaling which
are fundamental principles in machine learning. 

.fit_transform on training data is used because with the first part, ".fit", that allows
the preprocessor to learn the underyling data such as the minimum, maximum, mean
or standard deviation. It then takes this and applies the transformation to the training set.
This sets the "standard" or the "foundation" for your model and how it views data.

.transform() is used on the validation and test data to reapply what the model learnt from 
the training data, to new unseen data.

If we used the .fit() on the test data, it would disrupt the "simulation" of new unseen real-word
data since the information of the test set's overall distrbution, including mean or max values,
would leak into the modeling process. That would give the model an unfair advantage and it'll 
lead to too optimistic performance scores that wouldn't work well in the final produciton.

On the point of consistent scale, if we gave the the test data a new scaler, the data 
would be transformed based on a different mean and variance. By only using .transform(),
we can force the test data into the exact same scale as the training data and thus ensuring
a consistent scale. 


## ***Chapter 5***

### **Theory Question**

### 1. What is meant by the curse of dimensionality?
*Answer:*


### 2. What is dimensionality reduction and why is it done?
*Answer:*


### 3. Give a simple explination of how PCA works. Use figure 5.4 on page 224 in your explanation.
*Answer:*


### **Reasoning questions**

### 5. Stina claims that in machine learning, you always want models that make the best possible predictions. Kalle claims that this is not entirely true because time is also an important aspect, both for the model training itself and for the actual predictions. What do you say?
*Answer:*



### 6. After we have performed a PCA, what happens to the interpretation of the variables?
*Answer:*



## ***Chapter 6***

### **Theory Question**

### 1. What is clustering? Give some examples of application areas.
*Answer:*


### 2. Give a simple explination how K-means works. Use figure 6.3 (page 238) and figure 6.4 (page 239) in your explanation.
*Answer:*


### **Reasoning questions**


### 3. How can you choose the number of clusters to use for a K-means model? Use inertia, silhouette score, and silhouette diagrams in your answer.
*Answer:*



### 4. If you look at figure 6.10 on page 247, how many clusters would you have chosen and why? Is choosing the number of clusters an "exact science"?
*Answer:*



### 5. How does one interpret figure 6.13 on page 251?
*Answer:*
