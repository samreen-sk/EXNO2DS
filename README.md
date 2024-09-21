# EXNO2DS
### NAME: SHAIK SAMREEN
### REG NO: 212223110047
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
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns 
df=pd.read_csv("titanic_dataset.csv")
df
```
![366008055-a19ac75f-2598-4a78-8028-f51d3d167448](https://github.com/user-attachments/assets/c753f56b-eb4f-43fb-8314-018caa860970)
```
df.info()
```
![366008556-a4cff9be-b822-44d9-b860-b93958c6f46d](https://github.com/user-attachments/assets/b6383727-5ed6-4335-9669-65089eacb1f2)

```
df.shape
```
![366008791-1d5d6409-28ad-4170-8c4e-9ca136fbf975](https://github.com/user-attachments/assets/1f8f0361-615a-4bc3-bd0a-2e002439120b)
```
df.set_index("PassengerId",inplace=True)
df.describe()
```
![366009009-7517f446-2232-4354-bacf-3588627c9681](https://github.com/user-attachments/assets/ce2bb032-1f25-49f3-8991-61349f454e3a)
```
df.shape
```
![366009285-099f3b28-ff0e-4562-bfa6-29ee683d390a](https://github.com/user-attachments/assets/7c5898ca-2796-441c-ac5c-5bb04f9d4c5a)
```
df.nunique()
```
![366009479-9161a28b-ab1e-44fe-8e83-7d86420102ae](https://github.com/user-attachments/assets/3f730d02-03c3-4ef3-b67e-f2293b6642e9)
```
df["Survived"].value_counts()
```
![366009707-079c8360-d6f2-4aae-8b90-fd4f5117d925](https://github.com/user-attachments/assets/536643d4-1171-47cd-8474-322f0af692ea)

```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![366009889-4465d3e3-aa63-4aec-9811-5cdae6578329](https://github.com/user-attachments/assets/3adbe69f-aab1-4da5-8d04-720b97702ae1)
```
sns.countplot(data=df,x="Survived")
```
![366010095-c0cf2836-37f2-4375-8c23-4683bb745434](https://github.com/user-attachments/assets/59508487-5926-48ea-bba2-f23376dab282)
```
df
```
![366072870-21973863-d4ef-4d5f-8b3e-b9a8bf6d6ac2](https://github.com/user-attachments/assets/c763bb6a-f763-4417-a9df-48fec544d148)
```
df.Pclass.unique()
```
![366073242-f885d8c6-8853-4b1a-8e78-7f6067cb479c](https://github.com/user-attachments/assets/ac953fd8-6533-4887-b851-4c58d282fc56)
```
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```
![366073593-3d3614e7-1832-4802-8fca-d70a86df9369](https://github.com/user-attachments/assets/32d17d6b-f9c8-41e3-9efd-2d2d347dbdb3)
## Bivariate Analysis
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![366073956-c8b44162-3a88-431b-b21f-29b467e3ecbc](https://github.com/user-attachments/assets/726d58c3-8552-4245-84ad-00182a89c685)
```
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![366074496-3abf2cac-ad2d-416d-8fa4-b6323a2b08fd](https://github.com/user-attachments/assets/34e8d2c5-e2a6-4696-8e2d-b7460995214d)
```
df.boxplot(column="Age",by="Survived")
```
![366074811-42095543-8ea8-44cd-bb87-00896d5d65ae](https://github.com/user-attachments/assets/1862b474-f0e4-451e-8824-41247dcd7b30)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![366075170-be003743-cb0f-40df-b419-167c37da8b0e](https://github.com/user-attachments/assets/aafd3103-b319-4f73-93fb-4d1c05489e62)
```
sns.jointplot(x="Age",y="Fare",data=df)
```
![366075601-9bc1238d-accf-4719-b6bc-f0d22508491e](https://github.com/user-attachments/assets/99d5bb3b-b71a-47e1-801c-771b6be2ed15)

## Multivariate Analysis
```
fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
```
![366077214-e8ae7471-ddf7-43f6-a837-e2fe2a51f3f0](https://github.com/user-attachments/assets/22c7750c-5535-4b84-8ea9-3e95d7800628)
```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")

```
![366077992-3342116c-1702-434a-aadd-994dfc55974b](https://github.com/user-attachments/assets/80bcf904-4c59-4bc5-b037-ac8067d1edfb)

## Co-relation
```
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![366078406-c2a9c49e-efb9-4232-900a-936c347ab084](https://github.com/user-attachments/assets/28182dd8-5fe1-4ffd-9f2a-6b5b8fbedd9e)
```
sns.pairplot(df)
```

![366078866-c8a2e266-a4d2-4929-b52b-bf8109d5edd4](https://github.com/user-attachments/assets/92aedf26-8df4-4aff-ab1a-b772c41dd97e)



# RESULT
Exploratory Data Analysis on the given data set successfully.
