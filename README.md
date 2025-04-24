# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/69715827-699d-41bc-afc1-e722d0bb659e)
```
df.info()
```
![image](https://github.com/user-attachments/assets/6a3d9d59-a2bc-4c3d-9616-e98f92effe66)
```
df.shape()
```
![image](https://github.com/user-attachments/assets/9420ca43-84bc-4bce-bf50-2faf11368a3b)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/de8ae9c2-cb78-4a43-9df7-dabaab6f42d3)
```
df.head(11)
```
![image](https://github.com/user-attachments/assets/d0309798-5288-4129-aa1c-edda614d0f84)
```
df.tail(11)
```
![image](https://github.com/user-attachments/assets/a9e7612b-ba7d-4a0e-89ae-6ab7509a1d41)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/7e3a29a0-c429-4a10-87e5-e7d5faedd93a)
```
df.dropna(how="any").shape
```
![image](https://github.com/user-attachments/assets/01f30522-f76a-450c-a412-be93427edf33)
```
df.shape()
```
![image](https://github.com/user-attachments/assets/6d4febbf-79f5-4d64-ad98-f35968e6da4f)
```
x=df.dropna(how="any")
x
```
![image](https://github.com/user-attachments/assets/5ab7474d-d59c-4e51-87f7-c19e0d050e02)
```
h=df.TOTAL.mean()
h
```
![image](https://github.com/user-attachments/assets/52aff081-e46b-4793-bca3-10a9b2ea9750)
```
df.TOTAL.fillna(h,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/3287dfcc-5af0-4450-bfa3-d1181fc45e75)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/bdb13840-9990-4d2d-9e8e-fc7c579abcc6)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/815564c0-8334-43cf-b85c-963d34c4c67e)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/ba3950cf-b1af-4ba0-aa72-25419e4cf4b1)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/9d73ea80-41ec-4991-b825-570691837165)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/6fc506fc-e0e1-4b11-a13c-60003b524bdf)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/c26f2e38-6350-4d13-b949-5b532dcba2ad)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/776690c3-709c-430a-8256-65f1a08719f4)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/47cac97f-13f0-477a-a516-ae20524c89fe)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/16c9ddbc-ee80-4a2d-a8a2-562dc6d30a83)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/92ff3438-ddef-4c2f-85c1-fd3c8f512cca)
```
df['DOB']
```
![image](https://github.com/user-attachments/assets/c4bf4bbd-90a0-4c09-993a-3c91fb618a66)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/a97ec547-b641-4a21-9849-78e751f6e570)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/017179ff-f4ba-423b-b099-a8da641d9b0a)
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/8089ee9b-bb02-40bd-abc3-1979c4648492)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/b226c6d0-a4de-4423-8ba8-f401c3785285)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/2be65047-77d5-4cb3-a393-dd87e806548f)
```
q1=df.quantile(0.25)
q2=df.quantile(0.50)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/099d7450-55ee-4a09-a0eb-009dc51cbd23)
```
import numpy as np
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![image](https://github.com/user-attachments/assets/0815cc2b-c3aa-4371-aa35-b16578f8f5d0)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![image](https://github.com/user-attachments/assets/ef174a99-7a62-4890-89e4-8efb108b8b19)
```
upper_bound
```
![image](https://github.com/user-attachments/assets/bcd09de2-bf09-4880-8f5f-79102890abca)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/56052237-1e15-48ea-bc79-14251dcbfc53)
```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/83893c47-66ba-4d3f-886f-59e94b477b2e)
```
df=df.dropna()
df
```
![image](https://github.com/user-attachments/assets/ea5d27d2-020e-4a57-98aa-4cf49042b3c2)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/2b9447c9-e5b7-46dd-ad07-b795b17bd76c)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/e7ec194d-26a7-48b6-ba68-c017bad440d1)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)

```
![image](https://github.com/user-attachments/assets/47293da9-6801-4b23-a06f-db94ad0a9f2b)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/152d9dfe-c7a4-47ff-a2ce-48d0ea9344bc)
```
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/75cc71b8-ff45-4002-8331-dcc87d141ff6)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

```
![image](https://github.com/user-attachments/assets/69ec8c7f-8e09-4346-8306-3bfb407bddb5)

# Result
Thus the above program has been executed successfully
