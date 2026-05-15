# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
train = pd.read_csv("titanic_dataset.csv")
train.head()
train.isnull()
#visuvaisation of null values
sns.heatmap(train.isnull(),yticklabels=False,cbar=False,cmap='viridis')
#visuvalisation of survivors
sns.set_style('whitegrid')
sns.countplot(x='Survived',data=train)
#visuvalisation of survivors wt respect to gender
sns.set_style('whitegrid')
sns.countplot(x="Survived",hue='Sex', data=train)
#visuvalisation of survivors wt respect to class
sns.set_style('whitegrid')
sns.countplot(x='Survived',hue='Pclass',data=train,palette='rainbow')
#visuvalisation of distribution of age 
train['Age'].hist(bins=30,alpha =0.3)
#visuvalisation of survivors who has sibbling or sprouse 
sns.countplot(x='SibSp',data=train)
#visuvalisation the relationship bw class and age
plt.figure(figsize=(12,7))
sns.boxplot(x='Pclass',y='Age',data=train,palette='winter')
#fillinf null values wt mean
train['Age'] = train['Age'].fillna(train['Age'].mean())
sns.heatmap(train.isnull(),yticklabels=False,cbar=False,cmap='viridis')
train.drop('Cabin',axis=1,inplace=True)
train.head()
train.dropna(inplace=True)
train.info()
pd.get_dummies(train['Embarked'],drop_first=True).head()
sex= pd.get_dummies(train['Sex'],drop_first=True)
embark= pd.get_dummies(train['Embarked'],drop_first=True)
train = pd.concat([train,sex,embark],axis=1)
train.head()


# OUTPUT
<img width="1026" height="596" alt="image" src="https://github.com/user-attachments/assets/3a3225f3-cef9-4edf-b298-c88e37cedeb6" />
<img width="623" height="498" alt="image" src="https://github.com/user-attachments/assets/a00b983c-4e8b-412e-be4b-866341e28931" />
<img width="672" height="449" alt="image" src="https://github.com/user-attachments/assets/55258141-8088-4b72-b2a9-7dc2616d474c" />
<img width="770" height="440" alt="image" src="https://github.com/user-attachments/assets/0f8f1a82-3778-468e-831f-e4886b978345" />

<img width="702" height="436" alt="image" src="https://github.com/user-attachments/assets/83f0ce8a-40dd-4948-9c0d-7c8110518da7" />

<img width="720" height="434" alt="image" src="https://github.com/user-attachments/assets/fe9d67fd-818c-44c9-8a45-0b6b5b4477b5" />

<img width="773" height="440" alt="image" src="https://github.com/user-attachments/assets/51a0b153-5de4-431d-adcb-4a405bddf6d7" />

<img width="1050" height="605" alt="image" src="https://github.com/user-attachments/assets/abc57c37-15d1-4007-b5ac-db479c52514a" />

<img width="594" height="549" alt="image" src="https://github.com/user-attachments/assets/248a325e-4589-4cb1-9c1e-4d5866e7977c" />

# RESULT

The Exploratory Data Analysis (EDA) on the Titanic dataset was successfully performed.
