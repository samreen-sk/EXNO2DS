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

![366008055-a19ac75f-2598-4a78-8028-f51d3d167448](https://github.com/user-attachments/assets/7c66ec1a-c5f4-4134-81fa-b2d8eea95fb5)
```
df.info()
```
![366008556-a4cff9be-b822-44d9-b860-b93958c6f46d](https://github.com/user-attachments/assets/9729dd0c-935a-4887-bf68-8297dcf08c0f)
```
df.shape
```
![366008791-1d5d6409-28ad-4170-8c4e-9ca136fbf975](https://github.com/user-attachments/assets/09ba2ba0-bec0-4193-9539-63e70dcbc22b)
```
df.set_index("PassengerId",inplace=True)
df.describe()
```
![366009009-7517f446-2232-4354-bacf-3588627c9681](https://github.com/user-attachments/assets/209aef82-ec3c-41b9-af36-179e4389d84f)
```
df.shape
```
![366009285-099f3b28-ff0e-4562-bfa6-29ee683d390a](https://github.com/user-attachments/assets/39a910b7-cddd-42c8-96f9-8718d83d30b4)
```
df.nunique()
```
![366009479-9161a28b-ab1e-44fe-8e83-7d86420102ae](https://github.com/user-attachments/assets/c6b973f8-1c60-405c-8249-09438d98f7ae)
```
df["Survived"].value_counts()
```
![366009707-079c8360-d6f2-4aae-8b90-fd4f5117d925](https://github.com/user-attachments/assets/824d2a9b-749d-4139-8e89-2d43c175121d)

```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![366009889-4465d3e3-aa63-4aec-9811-5cdae6578329](https://github.com/user-attachments/assets/758f2b2a-9ff5-494f-8dae-6c7e965fb1bc)

```
sns.countplot(data=df,x="Survived")
```
![366010095-c0cf2836-37f2-4375-8c23-4683bb745434](https://github.com/user-attachments/assets/a4d2f7e7-864d-4734-936c-31d5b45c1f93)
```
df
```
![366072870-21973863-d4ef-4d5f-8b3e-b9a8bf6d6ac2](https://github.com/user-attachments/assets/5cd8b4a7-cd1a-4479-ae08-e89aebf2d0ba)

```
df.Pclass.unique()
```
![366073242-f885d8c6-8853-4b1a-8e78-7f6067cb479c](https://github.com/user-attachments/assets/fc3f3f9f-0539-4746-bb00-4888a9fb697d)
```
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```
![366073593-3d3614e7-1832-4802-8fca-d70a86df9369](https://github.com/user-attachments/assets/de541b7b-dc7e-4e94-9d8f-a7423074b7e4)


## Bivariate Analysis
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![366073956-c8b44162-3a88-431b-b21f-29b467e3ecbc](https://github.com/user-attachments/assets/12df2735-66ce-464a-b550-c00fad1f68aa)

```
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![366074496-3abf2cac-ad2d-416d-8fa4-b6323a2b08fd](https://github.com/user-attachments/assets/9d8b9b4c-68ea-44da-bc84-5cdf0ad2451f)

```
df.boxplot(column="Age",by="Survived")
```
![366074811-42095543-8ea8-44cd-bb87-00896d5d65ae](https://github.com/user-attachments/assets/48353af4-7cc6-4dca-b30e-d7c8a14b7173)
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```
![366075170-be003743-cb0f-40df-b419-167c37da8b0e](https://github.com/user-attachments/assets/cfe04f29-354d-4a25-bbe7-72d47b726026)

```
sns.jointplot(x="Age",y="Fare",data=df)
```

![366075601-9bc1238d-accf-4719-b6bc-f0d22508491e](https://github.com/user-attachments/assets/084eea18-5ebb-4a62-8526-20e8deed22db)

## Multivariate Analysis
```
fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
```

![366077214-e8ae7471-ddf7-43f6-a837-e2fe2a51f3f0](https://github.com/user-attachments/assets/6d06e954-2859-40a5-92a1-5d7123454cd2)

```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")

```


![366077992-3342116c-1702-434a-aadd-994dfc55974b](https://github.com/user-attachments/assets/4b05be99-bed6-43a4-bb80-3579211d515d)


## Co-relation
```
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![366078406-c2a9c49e-efb9-4232-900a-936c347ab084](https://github.com/user-attachments/assets/c8efd5d3-4fbb-4084-ab7e-f27451f916e8)


```
sns.pairplot(df)
```

![366078866-c8a2e266-a4d2-4929-b52b-bf8109d5edd4](https://github.com/user-attachments/assets/1f2d2734-43d7-414b-ba52-8fdd2cc266e8)





# RESULT
        
Exploratory Data Analysis on the given data set successfully.
