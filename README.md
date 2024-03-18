# Support-Vector-Machine - Predict customer churn for Credit Card Business

In a nutshell I am going to use CRISP-DM (Cross Industry Standard Process for Data Mining) process for data preparation wherein
I need to understand The below steps:
I. Business Understanding

<sub><b>1. What does the Business Need?</b>
   
<sub>To Answer this question: We are analyzing the Banks Data.
The bank wants to use a classification model that can predict customer churn for Credit Card Business. The resources available for us to identify
the same is in form of CSV wherein we have details of the customer mentioning about the below:

<sub>Number of Instances: 6237<br>
Number of Attributes: 15 independent variables + 1 target variable<br>
Independent Variables:<br>
Customer_Age – Customer age in years<br>
Gender – M = Male, F = Female<br>
Dependent_count – Number of dependents<br>
Education_Level – Highest education level of the customer<br>
Marital_Status – Married, Single, Divorced<br>
Income_Category – Annual income category of the customer<br>
Card_Category – Type of card. Platinum cards offer more reward points than gold cards, which
offersmore reward pointsthan silver cards. Blue cards offerthe least number ofreward points
on purchases.<br>
Months_on_book – Period of relationship (in months) with bank.<br>
Total_Relationship_Count – Total number of products held by the customer (e.g., Saving
account, Car loan, Credit Card, etc.)<br>
Months_Inactive - Number of months inactive in the last 12 months<br>
Contacts_Count – Number of customer service contacts in the last 12 months<br>
Credit_Limit – credit limit on the credit card<br>
Total_Revolving_Bal – Total revolving balance on the credit card (the portion of credit card
spending that goes unpaid at the end of a billing cycle)<br>
Total_Trans_Amt – Total transaction amount in the last 12 months<br>
Total_Trans_Ct – Total transaction count in the last 12 months<br>

<sub><b>Our Target feature is Attrition_Flag – Two labels - ‘Existing Customer’, ‘Attrited Customer’ (Customer who has
churned)</b>

<sub><b>II- DATA UNDERSTANDING</b>
Next Phase under CRISP-DM is to understand the data. From the initial looks in order to achieve the banks task whether the
customer will churn or not would highly depend on Months_Inactive, Months_on_Book and a small part as to what Credit_Limit
the customer carries. However there could be multiple other reasons as to why the customer would churn, which we will
analyze using Random Forest Method applying to the above data set.

<sub><b>III - DATA PREPARATION:</b>

<sub>Out of this we have 6 categorical data and 10 Numerical Data. So in order to analyse the data we want to convert the
categorical values to Numerical Values.<br>
<b>1. SELECT DATA-</b> So in this case we have 15 datasets to achieve 1 outcome of whether the customer will be retained or churned.<br>
<b>2. Clean Data -</b> We will identify if there are any garbage data or which is not correct or has any errorneous values.<br>
<b>3. Data ENCODING-</b> We will be using One-Hot Encoding as well as Converting Categorical features into Numerical
Binary values.

6 Categorical Data are as Below :<br>

Since below 2 data sets are of Binary Nature we will convert them using Dictionary method {}<br>
<sub>1. Attrition_Flag<br>
2. Gender<br>

The Rest 4 data sets as below we will use One-Hot Encoding:<br>

<sub>3. Education_Level<br>
4. Marital_Status<br>
5. Income_Category<br>
6. Card_Category<br>



