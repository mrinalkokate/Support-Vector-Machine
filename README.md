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

<p align="center">
Using Ensemble to find out Important Features. <br/>
<img src="https://i.imgur.com/3DwkKjt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<sub>With what we were initially predicting looking at the Data set was maybe the top 2 or 3 parameters would be
Months_Inactive, Months_on_Book and a small part as to what Credit_Limit. However, from the 1st Iteration of
Random Forest Method we are nearing the imp features to be Total_Trans_Ct, Total_Trans_Amt and Total_Revolving_Bal.

Hyperparameters in Random Forest:

<sub>Random Forest is a versatile ensemble learning algorithm that combines multiple decision trees to create a more robust and accurate model. However, it has several hyperparameters that need to be set before training the model. Some of the key hyperparameters in Random Forest include

<b>n_estimators:</b><br>
<sub>Parameter determines the number of decision trees to be used in the forest. Increasing the number of trees generally improves the performance of the model, but it also increases computational cost.

<b>max_depth:</b> <br>
<sub>Specifies the maximum depth of each decision tree in the forest. Deeper trees can capture more complex relationships in the data, but they are also more prone to overfitting.

<b>min_samples_split: </b><br>
<sub>The minimum number of samples required to split an internal node. Increasing this parameter can help prevent overfitting by ensuring that each split contains a minimum number of samples.

<b>min_samples_leaf: </b><br>
<sub>The minimum number of samples required to be at a leaf node. Similar to min_samples_split, increasing this parameter can help control the size of the tree and prevent overfitting.

<b>max_features:</b><br> 
<sub>The number of features to consider when looking for the best split. Setting this parameter to a lower value can help reduce the variance of the model and prevent overfitting.

<b>bootstrap: </b><br>
<sub>Specifies whether bootstrap samples (sampling with replacement) should be used when building trees. Setting this parameter to True enables bootstrapping, which is the default behavior in Random Forest.


<b>There are 2 hyperparameters in RandomForest which are :</b><br>

<sub>1. The number of trees which we are using to evaluate<br>
2. The number of features which gets used to create different random forest.

I will be concentrating on using the hyperparameter of the best number of trees as you can that STILL LOOKS LIKE THE ANSWER LIES BETWEEN 380 - 400 forests.
AS THE RESULTS WHICH WE RECEIVED WAS BETTER FOR 400 Forest with 96.12% RECALL (RESOLVED DOWN THE PAGE.)


<b> 3. Choice of Evaluation Metric (Which metric would be suitable for model evaluation and why?)</b><br>
    
<sub> Recall is prioritized when it's crucial to capture as many positives as possible, ensuring minimal false negatives.
 IN terms of the current data set we intend to capture if the customer will be retained by the bank or not for their credit card business or not.
In order to apply the model, we need to reduce the False Negatives wherein we are reducing the number of predictions about
identifying the customers who we identify as NOT BEING CHURNING, but they end up churning. This is what we need to
reduce the "False Negatives".
Recall is a metric that measures how often a machine learning model correctly identifies positive instances (true positives) from all the actual positive samples in the dataset.


5. Overfitting avoidance mechanism (Which mechanism (feature Selection/ regularization) would you use and why?)<br>
   
<sub>First Let us talk about overfitting and why it occurs: Overfitting is caused if we get 100% accuracy using the test data set and model is unable to generalize.
The results would not be true if a new data set for validation is provided.

There are different methods with which we can overcome overfitting. 

1. Ensemble
2. Cross-Validation(K-Folds)
3. Feature Selection 
4. Regularization.

Ensemble: <br>
<sub>Out of these we are using Ensemble which is prominent in building multiple models by selecting random feature sets to improve performance and generalization.
Cross-Validation : By splitting the data into multiple data sets and then training the model of these datasets. Also keeping one data set for validation.


<p align="center">
USED GRID SEARCH METHOD TO DETERMINE BEST No. of FORESTS. <br/>
<img src="https://i.imgur.com/7qxne37.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
Here is the Outcome <br/>
<img src="https://i.imgur.com/mF6G5H3.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Using Best Number of Forests we determined best Features. <br/>
<img src="https://i.imgur.com/s4iIaYV.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Found the best features. <br/>
<img src="https://i.imgur.com/zclPLcQ.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
We then used Grid search with Best Features.<br/>
<img src="https://i.imgur.com/IqcDAIR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
The Result shows <br/>
<img src="https://i.imgur.com/moMD5t7.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
AGAIN REPEATING THE METHOD TO IDENTIFY THE BEST FOREST POSSIBLE <br/>
<img src="https://i.imgur.com/TEDH0Mb.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
The Result shows <br/>
<img src="https://i.imgur.com/LsAG0im.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />

STILL LOOKS LIKE THE ANSWER LIES BETWEEN 380 - 400 forests.
AS THE RESULTS WHICH WE RECEIVED WAS BETTER FOR 400 Forest with 96.12% RECALL
<sub>(Recall is prioritized when it's crucial to capture as many positives as possible, ensuring minimal false negatives.)
NOW Lets use the pipeline method


What is from imblearn.pipeline import Pipeline method<br>
<sub>The Pipeline method from the imblearn.pipeline module is a tool provided by the imbalanced-learn library (imblearn) in Python. It allows users to create pipelines for machine learning workflows, specifically designed for handling imbalanced datasets.

<b>Pipeline:</b><br> 
<sub>A pipeline is a sequence of data processing steps that are chained together, where the output of one step is used as the input to the next step. This is commonly used in machine learning workflows to streamline data preprocessing, feature engineering, model training, and evaluation.


<b>imblearn:</b><br>
<sub>The imbalanced-learn library (imblearn) is a Python library specifically designed for handling imbalanced datasets, where one class is significantly more prevalent than the others. It provides various techniques for resampling and adjusting class distributions to address issues caused by class imbalance.

<b>from imblearn.pipeline import Pipeline: </b><br>
<sub>This line of code imports the Pipeline class from the imblearn.pipeline module. With this method, you can create a pipeline that includes both data preprocessing steps (e.g., scaling, feature selection) and machine learning algorithms (e.g., classifiers) while also integrating imbalanced data handling techniques provided by imbalanced-learn.

<p align="center">
Using PIPELINE Method.<br/>
<img src="https://i.imgur.com/won9SYx.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
The Result shows <br/>
<img src="https://i.imgur.com/jLjwezR.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />

Support Vector Machine<br>

A Support Vector Machine (SVM) is a supervised machine learning algorithm used for classification and regression tasks. Here's a simple explanation of how it works for classification:

-   <b>Data Representation:</b> SVM works by representing data points as points in space. Each data point is plotted as a point in an n-dimensional space (where n is the number of features in the dataset), with the value of each feature corresponding to a particular coordinate.

-   <b>Finding the Hyperplane:</b> SVM's primary objective is to find the best hyperplane that separates the data into different classes with the largest possible margin. A hyperplane is a line or plane that divides the feature space into two parts.

-   <b>Maximizing Margin:</b> The margin is the distance between the hyperplane and the nearest data point from either class. SVM aims to find the hyperplane that maximizes this margin, meaning it tries to find the hyperplane that is farthest from the nearest data points of any class.

-   <b>Support Vectors: </b>The data points that lie closest to the hyperplane are known as support vectors. These are the critical data points that determine the position and orientation of the hyperplane. SVM only relies on these support vectors to make decisions, which makes it memory-efficient and computationally efficient.

-   <b>Kernel Trick:</b> SVM can efficiently handle non-linear decision boundaries by transforming the input features into a higher-dimensional space using a kernel function. This allows SVM to find a linear hyperplane in the transformed feature space, which corresponds to a non-linear decision boundary in the original feature space.

<sub>In summary, Support Vector Machine is a powerful algorithm that finds the optimal hyperplane to separate data points of different classes while maximizing the margin between them. It is widely used for classification tasks due to its effectiveness in handling both linear and non-linear decision boundaries.

<p align="center">
When using SVM : Support Vector Machine<br/>
<img src="https://i.imgur.com/pCnT1zh.png" height="90%" width="90%" alt="Disk Sanitization Steps"/>
<br />

CONCLUSION: <br>
Results analysis<br>
a). Which of the two models (random forest or support vector classifier) would you recommend for deployment in the real-world?<br>

b). Is any model underfitting? If yes, what could be the possible reasons?

Answer: A : I would recommend to use Random Forest than Support Vector Machine as from the above results it implies that the "RECALL" Metric is higher for 
Random Forest than Support Vector Machine. This inturn favours so that we can achieve high rate of True Positives and reduce "False Negatives".<br>


Answer B: No the Model doesn't at all looks like underfitting as we are using proper mechanisms and ensemble to use permutations and combinations of various 
features and preparing multiple different models with more features.






