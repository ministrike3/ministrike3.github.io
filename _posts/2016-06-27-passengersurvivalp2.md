---
layout: post
title: "Predicting Passenger Survival on the Titanic: part 2"
tag: [Machine Learning, numpy, pandas, Python]
category: Machine Learning
---

Step 6) Does a Linear Regression work?

What if we tried to create a linear formula that looks at all values and tries to discover if this passenger was likely to survive or not? SciKit Learn contains a linear regression function:

from sklearn.linear_model import LinearRegression

Identify the predictors
predictors = ["Pclass", "Sex", "Age", "SibSp", "Parch", "Fare", "Embarked"]

predictions = []
for train, test in kf:
    # The predictors we're using the train the algorithm.  Note how we only take the rows in the train folds.
    train_predictors = (titanic[predictors].iloc[train,:])
    # The target we're using to train the algorithm.
    train_target = titanic["Survived"].iloc[train]
    # Training the algorithm using the predictors and target.
    alg.fit(train_predictors, train_target)
    # We can now make predictions on the test fold
    test_predictions = alg.predict(titanic[predictors].iloc[test,:])
    predictions.append(test_predictions)

# The predictions are in three separate numpy arrays.  Concatenate them into one.
# We concatenate them on axis 0, as they only have one axis.
predictions = numpy.concatenate(predictions, axis=0)

# Map predictions to outcomes (only possible outcomes are 1 and 0)
predictions[predictions > .5] = 1
predictions[predictions <=.5] = 0
accuracy = sum(predictions[predictions == titanic["Survived"]]) / len(predictions)

A Linear regression using these predictors provides an accuracy of 78.3%, which is not all that great.

Step 7) Logistic Regression
Output values between 0 and 1.

One good way to think of logistic regression is that it takes the output of a linear regression, and maps it to a probability value between 0 and 1. The mapping is done using the logit function. Passing any value through the logit function will map it to a value between 0 and 1 by "squeezing" the extreme values. This is perfect for us, because we only care about two outcomes.

Sklearn has a class for logistic regression that we can use. We'll also make things easier by using an sklearn helper function to do all of our cross validation and evaluation for us. This specific test run has an accuracy of 0.787878787879.

from sklearn import cross_validation

# Initialize our algorithm
alg = LogisticRegression(random_state=1)
# Compute the accuracy score for all the cross validation folds.  (much simpler than what we did before!)
scores = cross_validation.cross_val_score(alg, titanic[predictors], titanic["Survived"], cv=3)
# Take the mean of the scores (because we have one for each fold)
print(scores.mean())


Step 8) Decision Tree's,RandomForest, and Gradient Boosting
Step 9)Ensembling
Step 10) Matching and Predicting on the Test Set


