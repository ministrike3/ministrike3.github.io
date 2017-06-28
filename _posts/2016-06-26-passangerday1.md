---
layout: post
title: "Predicting Passenger Survival on the Titanic: Part 1"
tag: [Machine Learning, numpy, pandas, Python]
category: Machine Learning
---

Data Set Provided by Kaggle is about 1/3 of available dataset as .csv file

Each row represents a passenger on the Titanic, and some information about them. Let's take a look at the columns:

PassengerId -- A numerical id assigned to each passenger.
Survived -- Whether the passenger survived (1), or didn't (0). We'll be making predictions for this column.
Pclass -- The class the passenger was in -- first class (1), second class (2), or third class (3).
Name -- the name of the passenger.
Sex -- The gender of the passenger -- male or female.
Age -- The age of the passenger. Fractional.
SibSp -- The number of siblings and spouses the passenger had on board.
Parch -- The number of parents and children the passenger had on board.
Ticket -- The ticket number of the passenger.
Fare -- How much the passenger paid for the ticker.
Cabin -- Which cabin the passenger was in.
Embarked -- Where the passenger boarded the Titanic.

Step 1) Think

What might affect survival? Age-Children and grandparents? Sex- Women boarded lifeboats first? Passenger Class - First class is closer to the deck? Fare - Pay more, higher passenger class? Number of family - More people to help, or more people to think about saving? Embarked, ticket and name are less clear but may have an effect?

Step 2) Check Out the Data
import pandas
titanic = pandas.read_csv("titanic_train.csv")
print(titanic.describe())

The .describe method only lists numerical data; non numerical data can't be fed into an algorithm! We'll fix this in Step 4

Step 3) Clean the Data
The age column has 714 entries, to the rest of the columns 891. This means some passengers were missing ages.There are many strategies for cleaning up missing data, but a simple one is to just fill in all the missing values with the median of all the values in the column.We can select a single column by indexing the dataframe like a dictionary. This gives us a pandas series:
titanic["Age"]
The fillna method will replace any missing spots
titanic["Age"] = titanic["Age"].fillna(titanic["Age"].median())

Step 4) Converting Non-numeric data

Sex is binary - either male of female
the .loc finds all the instances in the titanic["sex"] column that match male; assign those to zero and female to 1
titanic.loc[titanic["Sex"] == "male", "Sex"] = 0
titanic.loc[titanic["Sex"] == "female", "Sex"] = 1

Embarked is either S,C,Q, or nan (missing). We need to clean the dataset before converting to digits 1-3. Since S was the most common embarkment port, we will assume everybody got on at S.
titanic["Embarked"] = titanic["Embarked"].fillna('S')
titanic.loc[titanic["Embarked"] == "S", "Embarked"] = 0
titanic.loc[titanic["Embarked"] == "C", "Embarked"] = 1
titanic.loc[titanic["Embarked"] == "Q", "Embarked"] = 2

Perhaps namelength has some value? Longer names are generally more aristocratic, pertaining to wealth! The .apply method creates a new feature (column). lambda x: means every time you find something, apply len() to it in line.

titanic["NameLength"] = titanic["Name"].apply(lambda x: len(x))

Maybe title? Perhaps more education, or being of the cloth, or a professional or something affected chances ? This is harder because title is within the name column, meaning we have to find it, then create a list of all avalible titles...
import re

# A function to get the title from a name.
def get_title(name):
# Use a regular expression to search for a title.  Titles always consist of capital and lowercase letters, and end with a period.
    title_search = re.search(' ([A-Za-z]+)\.', name)
    # If the title exists, extract and return it.
    if title_search:
        return title_search.group(1)
    return ""

# Get all the titles and print how often each one occurs.
titles = titanic["Name"].apply(get_title)
print(pandas.value_counts(titles))

# Map each title to an integer.  Some titles are very rare, and are compressed into the same codes as other titles.
title_mapping = {"Mr": 1, "Miss": 2, "Mrs": 3, "Master": 4, "Dr": 5, "Rev": 6, "Major": 7, "Col": 7, "Mlle": 8, "Mme": 8, "Don": 9, "Lady": 10, "Countess": 10, "Jonkheer": 10, "Sir": 9, "Capt": 7, "Ms": 2}
for k,v in title_mapping.items():
    titles[titles == k] = v
titanic["Title"] = titles

The last one is family size -- maybe having a larger family helped?

import operator

# A dictionary mapping family name to id
family_id_mapping = {}

# A function to get the id given a row
def get_family_id(row):
    # Find the last name by splitting on a comma
    last_name = row["Name"].split(",")[0]
    # Create the family id
    family_id = "{0}{1}".format(last_name, row["FamilySize"])
    # Look up the id in the mapping
    if family_id not in family_id_mapping:
        if len(family_id_mapping) == 0:
            current_id = 1
        else:
            # Get the maximum id from the mapping and add one to it if we don't have an id
            current_id = (max(family_id_mapping.items(), key=operator.itemgetter(1))[1] + 1)
        family_id_mapping[family_id] = current_id
    return family_id_mapping[family_id]

# Get the family ids with the apply method
family_ids = titanic.apply(get_family_id, axis=1)

# There are a lot of family ids, so we'll compress all of the families under 3 members into one code.
family_ids[titanic["FamilySize"] < 3] = -1

# Print the count of each unique id.
print(pandas.value_counts(family_ids))
titanic["FamilyId"] = family_ids

Step 5) Feature Selection
Theres a huge number of features we could use; a good way to choose the ones we want to use is univariate feature selection. This essentially goes column by column, and figures out which columns correlate most closely with what we're trying to predict

import numpy as np
from sklearn.feature_selection import SelectKBest, f_classif

predictors = ["Pclass", "Sex", "Age", "SibSp", "Parch", "Fare", "Embarked", "FamilySize", "Title", "FamilyId"]

# Perform feature selection
selector = SelectKBest(f_classif, k=5)
selector.fit(titanic[predictors], titanic["Survived"])

# Get the raw p-values for each feature, and transform from p-values into scores
scores = -np.log10(selector.pvalues_)

# Plot the scores.  See how "Pclass", "Sex", "Title", and "Fare" are the best?
plt.bar(range(len(predictors)), scores)
plt.xticks(range(len(predictors)), predictors, rotation='vertical')
plt.show()



Step 6) Cross Validation
Essentially, cross validation is splitting the dataset into parts, training the algorithm on some of them, and testing it on others. What this does is prevent "overfitting" of the data, whereby the model fits itself to the quirks of the dataset rather then to the full population.
Luckily, cross validation is a simple way to avoid overfitting. To cross validate, you split your data into some number of parts (or "folds"). Lets use 3 as an example. You then do this:

Combine the first two parts, train a model, make predictions on the third.

Combine the first and third parts, train a model, make predictions on the second.

Combine the second and third parts, train a model, make predictions on the first.


Scikit Learn contains a CrossValidation Function as well! It Generates cross validation folds for the titanic dataset, and returns the row indices corresponding to train and test.We set random_state to ensure we get the same splits every time we run this.
from sklearn.cross_validation import KFold
kf = KFold(titanic.shape[0], n_folds=3, random_state=1)


Now that we've got the data cleaned up, our final choices of features selected, and cross validation in place, we'll apply some machine learning algorithms on them, and see how accurate of a prediction we can get to using various models!
