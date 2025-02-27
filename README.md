# Kaggle-Titanic-

This repository is my submission of the https://www.kaggle.com/c/titanic. In this competition, the goal is to perform a 2-label classification problem: predict which passengers survived the tragedy. 

The challenge offers two datasets one for training and one for testing. The goal is to submit a file with our prediction labels. 

## __Train Data Dictionary__

The train dataset has 891 rows and 12 columns

| Variable  | Definition                             | Key                                   |
|-----------|----------------------------------------|---------------------------------------|
| survival  | Survival                              | 0 = No, 1 = Yes                      |
| pclass    | Ticket class                          | 1 = 1st, 2 = 2nd, 3 = 3rd             |
| sex       | Sex                                   |                                       |
| Age       | Age in years                          |                                       |
| sibsp     | # of siblings / spouses aboard       |                                       |
| parch     | # of parents / children aboard       |                                       |
| ticket    | Ticket number                         |                                       |
| fare      | Passenger fare                        |                                       |
| cabin     | Cabin number                          |                                       |
| embarked  | Port of Embarkation                   | C = Cherbourg, Q = Queenstown, S = Southampton |

## __Test Data Dictionary__
The test dataset structure is  identical without the survival column. 


The train dataset has 418 rows and 11 columns 

## Main Challenge 
To design an algorithm to predict whether a  person with different features can survive the Titanic disaster.

This is a multi-label classification, with 2 labels:

0: passenger did not survive

1: passenger survived

Goal: For each passenger, predict the label (0 or 1).

# Project Framework

- Exploratory Data Analysis(EDA) 
- Data Preprocessing
- Feature Engineering
- Model Training
- Model Evaluation


## Exploratory Data Analysis(EDA) 

Train Data null Values 
![Alt Text](/Users/ansari/Desktop/a4fd8f94-2916-4ef9-a314-2748dad7e10a.png)

Test data Null Values 



## Post EDA Conclusion



### Categorical & Integer Numerical Features

Exploratory analysis revealed:

- Pclass: Passenagers from classes had a higher chance of survival, Pclass should be used as a direct preditor
- SibSp and Parach: Both had a measurable impact on the chances of survival. Rather than using both as separate predictors they should be combined (_Feature engineering required_)
- Fare: Initial analysis suggests there is a direct positive relation between the  fare paid and survival chance. Hence Fare should be used directly as a predictor
- Sex: Direct correlation between gender and survival chance. Therefore should be used directly(_Hot one encoding required_)
- Embarked: Some Correlation between port of Embarkation and survival rate
- Age Young and Old People survived but people of Middle Ages did not. Should be used as a predictor. Age is skewed and Fare is highly skewed -> Box-Cox Transformation is required

### Text Features

For this type of features, we don't directly do analysis. A first transformation is needed. The observed features are:

- Cabin
- Name 

<u>Engineering:</u>
- Cabin: We can extract two informations: 
	- if a passenger has a cabin 
	- what is the letter of the cabin deck and so we have an estimate of the position of the passenger in the boat
- Name: We can extract one information:
	- the title of the passenger
	- Group the title to reduce the number of categories

## Feature Engineering 

### New Features Implemented 
-  Family_size:  Column that combines the number of siblings, parents, and spouses
-  age_transformed: I used Box-Cox transformation to normalize the data since age was highly skewed.
-  Has_Cabin: Classifies passenger based on whether they have a cabin or not( 0 - No Cabin, 1 - Has a Cabin)
-  Title: Extracted  the titles from the names column.
- Cabin_Deck: If the passengers have a cabin, saves the cabin number
  
### Possible Features
- Sex
- family_members
- Has_Cabin
- Title
- Cabin_Deck
- Embarked
- age_transformed
- Pclass
- Ticket_Group_Size
- Fare

## Model Training 













