## About the project
This is an Application that implements an algorithmic trading strategy that uses machine learning to automate trade decisions.

* Built With
* Python
* Python conda
* Python JupyterLab
* Python CSV Reading/Writing
* Python pandas
* Python scikit-learn

# Evaluation Report

* Summary of analysis

The purpose of the analysis is to train a model that uses machine learning to automate trade decisions.

* Establishing a Baseline Performance.

In this section, I run the provided starter code to establish a baseline performance for the trading algorithm using historical OHLC price data from an emerging market asset. 

I used a simple moving average SMA as a baseline performance which is a technical indicator that can aid in determining if an asset price will continue or if it will reverse a bull or bear trend.

The Baseline Strategy performance didn't yield good results considering that it is predicting an outcome solely based on a cross of two moving averages that have been shifted forward by one period (one day in this model) to predict a future crossing point.

![Screenshot](https://github.com/alghalia/challenge_14/blob/main/Images/Baseline%20strategy.png))

* Training and testing data using support Vector Classifier SVC
  
I used Support Vector Classifier SVC from SKLearn's to fit the training data and make predictions based on the testing data. Review the predictions, SVC is a supervised machine learning algorithm typically used for classification tasks. SVC works by mapping data points to a high-dimensional space and then finding the optimal hyperplane that divides the data into two classes.


The variables that is being predicted is the signals_df['Signal'] column which is calculated based on the cross of two moving averages used as a trigger. The moving averages are assigned to the X variable: X = signals_df[['SMA_Fast', 'SMA_Slow']], and the y variable is assigned the value of signals_df['Signal'] for the model.

Rules :
When the SMA_Slow crosses the SMA_Fast from a lower to a higher price it sends a 1 to the y (signal) variable
When the SMA_Slow crosses the SMA_Fast from a higher to a lower price it sends a -1 to the y (signal) variable

A 1=Buy and -1=Sell.

Assumption This model assumes that the trader is able to consistently enter and exit the market at the previous day close whenever the Signal is generated. It assumes 100% accuracy and 100% success in the price of the market execution for the Actual Returns calculation. 

A more realistic and accurate entry strategy will be needed in order to fine-tune a profit strategy, but this was beyond the scope of this analysis. Understanding the risks and assumptions of the model proves this to be a good model since the machine learning aspect of the analysis was proven and it is profitable.

**Support Vector Machine Strategy performance**

The Support Vector Machine Strategy performed well despite the volatility in the market. The Strategy Returns have better results than the Actual Returns column for this strategy almost consistently. This model attempts to establish a relationship based on the geometrical properties of data. It tries to find the distance that separates the distance between the classes - in this case, the classes are the classifications into the signals_df['Signal'] column as 1 or -1.

![Screenshot](https://github.com/alghalia/challenge_14/blob/main/Images/Support%20vector%20machine%20startegy%20.png)

**Tune the training algorithm by adjusting the size of the training dataset**

 When I  increased  the training window to 12 months the returns decreased as shown in the screenshot below where you can see that the Actual Returns line matches the Strategy Returns line.
 ![Screenshot](https://github.com/alghalia/challenge_14/blob/main/Images/12%20.png)
 
 When I decrease the training window to 1 month the return performs better than the actual return as shown below.

 ![Screenshot](https://github.com/alghalia/challenge_14/blob/main/Images/1.png)


**Evaluate a New Machine Learning Classifier**

**A LogisticRegression Strategy model**

Logistic regression is a statistical analysis method to predict a binary outcome, such as yes or no, based on prior observations of a data set. A logistic regression model predicts a dependent data variable by analyzing the relationship between one or more existing independent variables.

The LogisticRegression Strategy performance was worse in comparison and seemed to stop working after some time. It attempts to establish a dependent type of relationship between the two moving averages which is not the best approach for this model. Predicting a dependency between the SMA_Slow and the SMA_Fast creates a fragile relationship vulnerable to overfitting, which the model exposed

Changing the SMA_Slow to a larger number increased the overall performance slightly but still has catastrophic results in the end.

 ![Screenshot](https://github.com/alghalia/challenge_14/blob/main/Images/LRS.png)## Summary


**RECOMMENDATION** - The Support Vector Machine Strategy is the best strategy for this model and asset. Markets have geometrical properties of data, as well as unstructured and semi-structured properties of data and this is the best approach for the strategy of predicting two crossing moving averages.



---
## Contributors
By AlGhalia Alsammak
Email:galsammak@gmail.com
## License
CU

