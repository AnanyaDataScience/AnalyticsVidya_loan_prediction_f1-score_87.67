# AnalyticsVidya_loan_prediction_recall_100-
Dream Housing Finance company deals in all kinds of home loans. They have presence across all urban, semi urban and rural areas. Customer first applies for home loan and after that company validates the customer eligibility for loan. Company wants to automate the loan eligibility process (real time) based on customer detail provided while filling online application form. These details are Gender, Marital Status, Education, Number of Dependents, Income, Loan Amount, Credit History and others. To automate this process, they have provided a dataset to identify the customers segments that are eligible for loan amount so that they can specifically target these customers. 
Variable	Description
Loan_ID	Unique Loan ID
Gender	Male/ Female
Married	Applicant married (Y/N)
Dependents	Number of dependents
Education	Applicant Education (Graduate/ Under Graduate)
Self_Employed	Self employed (Y/N)
ApplicantIncome	Applicant income
CoapplicantIncome	Coapplicant income
LoanAmount	Loan amount in thousands
Loan_Amount_Term	Term of loan in months
Credit_History	credit history meets guidelines
Property_Area	Urban/ Semi Urban/ Rural
Loan_Status	(Target) Loan approved (Y/N)

# Train size: 614,13
# Test size:367,12

Steps:
## Missing value analysis:
## EDA (https://public.tableau.com/profile/ananya8013#!/vizhome/loanapproval/educationvsapplicantincome?publish=yes) you can also find it in the githib repository
mode imputation for categorical variables (gender, married, dependents, self-employed, credit history), median imputation for continuous variables.
## Chi-square Analysis
To understand the dependence between the input categorical variables and the input variables and the target variable
First did label encoding for the categorical variables, then performed chi-square analysis between the variables.
Ho: variables are not dependent
H1: variables are dependent
If p<0.05, we reject the H0
Gender is correlated with married and dependent, married is correlated with dependent. So, I am dropping gender and dependent
Credit history is the most correlated with loan status.
## Loan ID is dropped
## pd.get_dummies is used to get binary values for the categorical variable
## Standardization
For continuous predictor variables, It brings down the scales of the numerical variables with different ranges
## Then data frame is converted to array, to make sure numerical values are going into the models.
## RF, GBM, XGB and Naive Bayes used. RF n estimator is taken as 500 and criterion is taken as gini and entropy for grid search. GBM and XGB: 'learning_rate': [0.01,0.05,0.1],'max_depth': [3,4,5],'n_estimators': [500]
## Cross validation: We predict accuracy, recall for all the models. We did k fold cv where k=5 
## So we get the best recall score of 100% with gbm!!! as we need to correctly predict the "1" points

