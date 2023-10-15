# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them


# Aim
TO detect and remove the outliers in the given data set and save the final data.

# Algorithm:
### Step 1
Import the required packages(pandas,numpy,scipy)

### Step 2
Read the given csv file

### Step 3
Convert the file into a dataframe and get information of the data.

### Step 4
Remove the non numerical data columns using drop() method.

### Step 5
Detect the outliers in the data set using z scores method.

### Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7
Check if the outliersare removed from data set using graphical methods.

### Step 8
Save the final data set into the file.

# Program:
```
FOR BHP.CSV FILE

import pandas as pd
df=pd.read_csv("/bhp.csv")
df
df.info()
df.shape
import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)]
print(newdata)
newdata=df[(df['price_per_sqft']>=lower) | (df['price_per_sqft']<=upper)]
print(newdata)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

FOR HEIGHT_WEIGHT.CSV FILE

import pandas as pd
df=pd.read_csv("/height_weight.csv")
df
df.info()
df.shape
df.describe()
import seaborn as sns
sns.boxplot(x="height",data=df)
Q1=df['height'].quantile(0.25)
Q3=df['height'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata1=df[(df['height']>=lower) | (df['height']<=upper)]
print(newdata1)
newdata=df[(df['height']>=lower) & (df['height']<=upper)]
print(newdata)
sns.boxplot(x='height',data=newdata1)
```
# OUTPUT:
## Original data for bhp.csv file:
![265034788-e10bb3a9-b641-4ee7-9723-5d1d7984efdd](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/1c5d8545-947c-4ac7-af89-a5ba56a34362)

## Dataset information:
![265034880-38816f72-8267-4668-aebf-464ae59fd67d](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/ce93bb13-5f14-498c-8379-efce8d563b0b)

## Shape of a data:
![265034941-72a124a8-9cd1-4569-ad2a-175e705614bb](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/dc9ee8ac-1295-44a1-87d6-f9ff030a7259)


## Box Plot of price_per_sqft column without outliers:
![265035056-5d30f29b-5895-4283-8a15-e5911b4a5273](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/b1438172-6173-45df-96f8-af73c027e4a5)


## Removing the outlier for price_per_sqft column by using IRQ :
![265035157-3315b091-1878-4bf7-af46-22b902dac0a3](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/70d827c9-f712-4111-9665-70d458c85a46)
![265035253-08eb1088-795a-4faa-9326-ee538b403456](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/b98af739-e32d-43c4-b8f8-ac9fc86681a5)


## Box Plot of price_per_sqft column after IRQ:
![265035343-235388ed-c469-46d3-a453-49c7015f80c8](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/6a835d7b-d16d-4554-955a-d36ce4e05165)


## Removing the outlier for price_per_sqft column by using zscore of 3 :
![265035456-38140855-ea08-4740-93b0-5fd1d6930dd1](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/1e1dd40f-3b44-414c-9d88-ede376afaec7)
![265035518-567ca3e2-74cd-411f-abf7-24c3a9f482b7](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/f7f9ae82-34c8-4313-a81b-64a94508f9ce)

## Box Plot of price_per_sqft column after zscore of 3:
![265035583-06ff570b-b0db-47ae-a8ab-b5146da18ebd](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/480168b6-d443-4cd1-9baa-15e0d55efae7)

## Original data of height_weight.csv file for height:
![265041930-735932f9-58ed-446e-9d5a-5474a606af2c](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/1a8f2d56-1847-4a15-a210-d82b1e35e3a0)

## Dataset information:
![265042116-a6a5b7f0-56b6-4cd5-8472-271a755689c6](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/3c7b5f38-26d5-4833-b07d-3b51dc89b833)

## Shape of a dataset:
![265042347-c330aa96-2008-4a4a-ac91-9ae30cf84894](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/97fcc371-a2fa-4700-8cd0-632cd896974b)

## Box plot of height column without outlier:
![265042576-ecb98058-2e13-45ea-8a4c-e186beb1ac83](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/00825a5c-9343-40f8-a213-eda4eb7a0232)

## Removing the outlier for height column by using IRQ :
![265042871-9c8f342c-610f-48a7-8fa4-dbaf7880eeb3](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/df12c64f-9f69-429b-873c-5bc77305d4db)
![265042962-6f5e8c88-f43e-4e90-be5d-37e0d49580c1](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/bb1c85ff-69b2-470d-b71d-5d2f00fcd9b7)

## Box Plot of height column after IRQ:
![265043050-8169c62a-2ead-4ffd-99fd-9d8c5d6c6d06](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/58eb34f3-1a64-4345-8f22-0b3e31fb4a33)

## Original data of height_weight.csv file for weight:
![265178232-4a366a77-3856-4473-adbb-1417e92f92c9](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/cb87da7d-5108-41d5-b14e-31c87a856236)

## Dataset information:
![265178257-0300eb8e-8208-4339-a9b4-b71a93bf464b](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/096e9d35-8d06-4701-b080-c9c3abf402c7)

## Shape of a dataset:
![265178285-5ce6ea82-696b-4855-b8ff-45cf26de0644](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/0eb4a9e1-da77-4a6f-afa7-7394bb99bae1)

## Box plot weight column without outlier:
![265178341-30e09c44-6e26-4109-9ea9-08fa7b81363b](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/61c460e4-ddf4-45e7-800c-0034278e61b4)

## Removing the outlier for weight column by using IRQ :
![265178373-24f368e3-c310-4578-82c0-b2b2ab884715](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/0694731a-3986-4ba0-a988-fa7ac696c0ce)
![265178586-3ed556f5-eab2-4162-9f15-ef4d9cdca503](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/f09f43aa-b24b-4aa0-90c7-5e97c8a33c20)

## Box Plot of height column after IRQ:
![265178655-f5acbd89-2880-4067-ac9e-5a71ccb87493](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/de75625e-c8e1-4b50-9f7c-d950780e8414)

# Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
