# Credit-Risk-Analysis

## Dataset
The data is from an old Kaggle competition (https://www.kaggle.com/code/nishchalpandey/give-me-some-credit-project). It contains 15000 rows and 10 features. The features are:
- RevolvingUtilizationOfUnsecuredLines: Total balance on credit cards and personal lines of credit except real estate and no installment debt like car loans divided by the sum of credit limits
- age: Age of borrower in years
- NumberOfTime30-59DaysPastDueNotWorse: Number of times borrower has been 30-59 days past due but no worse in the last 2 years.
- DebtRatio: Monthly debt payments, alimony,living costs divided by monthy gross income
- MonthlyIncome: Monthly income
- NumberOfOpenCreditLinesAndLoans: Number of Open loans (installment like car loan or mortgage) and Lines of credit (e.g. credit cards)
- NumberOfTimes90DaysLate: Number of times borrower has been 90 days or more past due.
- NumberRealEstateLoansOrLines: Number of mortgage and real estate loans including home equity lines of credit
- NumberOfTime60-89DaysPastDueNotWorse: Number of times borrower has been 60-89 days past due but no worse in the last 2 years.
- NumberOfDependents: Number of dependents in family excluding themselves (spouse, children etc.)

## Preprocessing Data
The data is first split into a training and testing set (80-20 split). The training set is preprocessed by imputing missing values and removing outliers. Then, each numerical features is split into 6 bins. These binned features are used to compute the Weight of Evidence (WoE) and Information Value (IV) for each feature, which are what we use for the initial feature selection. Finally, we apply the preprocessing steps we used on the training set onto the testing set.

Before we begin modelling with logistic regression using the preprocess data, we perform a multicollinearity check to ensure the features do not have multicollinarity. This is done by removing features with a VIF of greater than 5.

## Modelling
A logistic model is fitted onto the training data. By checking the p-value of each coefficient, it can be seen that some coefficients are not statistically significant, in which case they are removed and another model is fit. All the coefficients of the second model are statistically significant, so we can use it and evaluate it using the test set (that has not been seen by the model yet).

## Results
The model have a pretty high ROC-AUC of 0.80, meaning it is much better than a random guess. However, unfortunately it is not very precise and has a very low recall. Specifically, it has a precision of 0.516 and a recall of 0.047 when predicting class 1 (i.e. default). That means when the model is predicting class 1, 51.6% of the time it is right, and out of 1000 true class 1 predictions, it only captures 47 of those. 

