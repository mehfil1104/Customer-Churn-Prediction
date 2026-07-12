# Customer Churn Prediction

This is my first machine learning project. The goal was to predict whether a telecom customer is going to churn (leave the service) based on their account info and usage behavior.

I'm a CS grad currently learning ML, so this project was mainly about understanding the full workflow — cleaning data, building models, and actually evaluating whether they work.

## Dataset

I used the [Customer Churn Dataset](https://www.kaggle.com/datasets/muhammadshahidazeem/customer-churn-dataset) from Kaggle. It comes with a training file and a testing file already split, around 505,000 rows combined.

Note: this data is generated, not from a real company. I found that out the hard way — more on that below.

## What I did

1. Loaded the data and checked for missing values / bad entries
2. Dropped `CustomerID` since it's just an identifier, not useful for predicting anything
3. Encoded the text columns (`Gender`, `Subscription Type`, `Contract Length`) into numbers so models can actually use them
4. Ran my first models and got weirdly bad, inconsistent results
5. Dug into it and found the provided train/test files didn't actually share the same patterns — a feature like Tenure was positively correlated with churn in one file and negatively correlated in the other. Combined both files myself and made my own proper 80/20 split
6. After that fix, results improved a lot and made way more sense

## Models I tried

|       Model         | Accuracy |
|---------------------|----------|
| Logistic Regression |    85%   |
| Decision Tree       |    92%   |
| Random Forest       |    94%   |

Random Forest performed best overall.

## What actually drives churn (feature importance)

According to the Random Forest model, the biggest churn indicators were:
- Support Calls
- Total Spend
- Age
- Payment Delay

Makes sense — customers calling support a lot or paying late are probably more frustrated/disengaged.

## What I learned

- Data cleaning and encoding takes way more thought than I expected
- Always check if train/test data are actually consistent before trusting your results — this cost me a lot of confusion until I figured it out
- Simple models (Logistic Regression) are a good baseline, but tree-based models handled this data much better

## Tools used

Python, pandas, scikit-learn, Jupyter Notebook

## Status

Core project done. Might explore hyperparameter tuning or deployment next.