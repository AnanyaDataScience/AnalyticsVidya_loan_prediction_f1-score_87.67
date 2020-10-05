# AnalyticsVidya_loan_prediction
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
mode imputation for categorical variables (gender, married, dependents, self-employed, credit history), median imputation for continuous variables.
## EDA (https://public.tableau.com/views/loanapproval/percentageofloaneligibiltybasedonloanamount?:language=en&:display_count=y&publish=yes&:origin=viz_share_link)
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
## Decision trees, KNN  Naive Bayes are used
## Cross validation: We predict accuracy, f1 score for all the models. We did k fold cv where k=5 
So we get the best f1 score of approx 87.67% with Decision Trees!!!

