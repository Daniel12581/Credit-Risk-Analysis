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

## Preprocess
The data is first split into a training and testing set (80-20 split). The train seingt is preprocessed by imputing missing values and removing outliers. Then, each numerical features is split into 6 bins. These binned features are used to compute the Weight of Evidence (WoE) and Information Value (IV) for each feature, which are what we use for the initial feature selection. Finally, we apply the preprocessing steps we used on the training set onto the testing set.
