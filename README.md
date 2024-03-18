# Support-Vector-Machine - Predict customer churn for Credit Card Business

In a nutshell I am going to use CRISP-DM (Cross Industry Standard Process for Data Mining) process for data preparation wherein we will go through the following stages within Crisp-DM

STAGES OF CRISPDM <br>
<b>Business understanding</b> – What does the business need?<br>
<b>Data understanding</b>  – What data do we have / need? Is it clean?<br>
<b>Data preparation</b>  – How do we organize the data for modeling?<br>
<b>Modeling</b>  – What modeling techniques should we apply?<br>
<b>Evaluation</b>  – Which model best meets the business objectives?<br>
<b>Deployment</b>  – How do stakeholders access the results?<br>

<b>I. Business Understanding</b>

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

Next Step in DATA PREPARATION WOULD BE TO DIVIDE THE DataSet.<br>
Dividing the dataset into input (feature) and output (labels)<br>
x=data2.drop(['Attrition_Flag'],axis=1) ==> Features<br>
y=data2['Attrited Customer']              ==> LABELS

Then we will be SCALING the data. WE USE StandardScaler().fit_transform() from python's SKLEARN's > PREPROCESSING Box by removing any variance.

After scaling, we perform Data splitting (label column) which we use the function from sklearn library model_selection > import train_test_split()

NOW WE BALANCE THE DATA: <br>
Implementing Oversampling/ downsampling to balance the dataset. To do this we use SMOTE from imblearn > over_sampling box

<b>What is a SMOTE? - </b>
<sub>
<b>SMOTE (Synthetic Minority Over-sampling Technique)<b> is a technique used in machine learning to address the class imbalance problem, particularly in classification tasks. Class imbalance occurs when one class (the minority class) is underrepresented in the dataset compared to the other classes (the majority class or classes). This imbalance can lead to biased models that perform poorly in predicting the minority class.

<p align="center">
Data Reading for Bank Data - To Predict Customer Churn for Credit Card Business. <br/>
<img src="https://i.imgur.com/1fFdCmL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

From the output of the above Data PREPARATION PART WE CAN SEE THAT THERE ARE 6237 Non-Null DATA and all have been successfully
converted to Numerical DATA

After the DATA PREPARATION PART within CRISP-DM Flow, we now need to perform DATA MODELING

<sub>Within this we need to select modeling techniques
Depending on the modeling approach we then split the data into Training, Testing and Validation sets.
We then build the model. In this case we are using two Models - 1. Random Forest Technique and 2. support vector classifier.
We then need to assess the model to determine which one we can use the best model as.




