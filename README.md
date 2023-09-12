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
# (1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe
```
Developed by: Vishnupriya R
Roll number: 212222110054

import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("/content/bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)

q1 = df['price_per_sqft'].quantile(0.25)
q3 = df['price_per_sqft'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df1 =df[((df['price_per_sqft']>=ll)&(df['price_per_sqft']<=ul))]
df1

df1.shape

sns.boxplot(x="price_per_sqft",data=df1)
```

# (3)Examine price_per_sqft column and use zscore of 3 to remove outliers
```
from scipy import stats
z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
```

# (4)(i) For the data set height_weight.csv detect weight outliers using IQR method
```
df3 = pd.read_csv("height_weight.csv")
df3

df3.head()

df3.info()

df3.describe()

df3.isnull().sum()

df3.shape

sns.boxplot(x="weight",data=df3)

q1 = df3['weight'].quantile(0.25)
q3 = df3['weight'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df4 =df3[((df3['weight']>=ll)&(df3['weight']<=ul))]
df4

df4.shape

sns.boxplot(x="weight",data=df4)
```

# (4)(ii) For the data set height_weight.csv detect height outliers using IQR method
```
sns.boxplot(x="height",data=df3)
q1 = df3['height'].quantile(0.25)
q3 = df3['height'].quantile(0.75)
print("First Quantile =",q1,"\nSecond Quantile =",q3)

IQR = q3-q1
ul = q3+1.5*IQR
ll = q1-1.5*IQR

df5 =df3[((df3['height']>=ll)&(df3['height']<=ul))]
df5

df5.shape

sns.boxplot(x="height",data=df5)
```
# OUTPUT:
# (1)(2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe.
# Dataset:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/2619e47d-2f11-46e6-be46-cf11ae2e4013)

# Dataset Head:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/7e84607a-24d3-4f84-8d10-37a0b78db882)

# Dataset info:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/3a3ff149-9a08-401d-9232-201d74796e9c)

# Dataset describe:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/867f5a20-0f8c-4a5a-8801-c32ceb9c56d0)

# Null values:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/8655d297-328d-4714-95da-ad546b909edb)

# Dataset shape:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/6056b804-448e-420a-9ea2-7168d6161cbe)

# Box plot of price_per_sqft column with outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/56e3e8ee-aad8-4f3c-8764-d47089eeaf40)

# price_per_sqft - Dataset after removing outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/63bfadea-da0d-41cf-a01a-2020f7f5f06e)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/dc3fc493-82ef-4022-808c-baf02fcdbb49)

# price_per_sqft - Shape of Dataset after removing outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/713051ac-c9c5-40ef-8ada-f72df08c88b6)

# Box Plot of price_per_sqft column without outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/476c84c2-423d-4249-9cca-9959ad3bad3d)

# (3) Examine price_per_sqft column and use zscore of 3 to remove outliers
# Dataset after removal of outlier using z score:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/c7802db9-fbb7-4ffd-a212-992368294b02)

# Shape of Dataset after removal of outlier using z score:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/80146c54-dc15-478d-9539-b31d35c06404)

# (4) For the data set height_weight.csv detect weight and height outliers using IQR method:
# Dataset:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/94dfff6c-300d-4ea1-bffe-352776ae443e)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/7ea6dd84-ed9d-4975-9bd0-3799b90cb74a)

# Dataset head:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/a2fb1930-1a19-4133-8dc9-cb30be0d0913)

# Dataset info:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/c5928efd-7d3a-4ac8-b94f-5865e70eaebe)

# Dataset describe:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/e40b34f9-ff64-4a53-90e7-4c7aeb835bc2)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/2dbc2bef-163e-4478-9edc-0e0cde039431)

# Null values:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/a41c3716-2efa-4253-96c9-84b854b76da0)

# Data set Shapes:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/c2532e04-3369-4c14-a687-36efa384209d)

# Weight - with outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/a3e45816-a325-4b61-9a84-f50bacb45613)

# Weight - Dataset after removing Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/289ba950-8543-49a6-827f-ba9c721f3d6f)

# Weight - Shape of Dataset after removing Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/ed952c68-3419-4bd8-a369-a0148291f008)

# Weight - Without Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/eb2e9daa-d777-4379-8368-87e7febe92cd)

# Height - With outliers:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/049b2e40-c2bc-4370-8e5c-89d406b6396a)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/4a20a7b4-5649-4288-8d9a-de34188f14de)

# Height - Dataset after removing Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/ef0b07ac-3a53-48fb-9b3c-931a6dc287f3)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/2d4a8504-cab2-4588-8f5b-3a313cdda8eb)

# Height - Shape of Dataset after removing Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/f6bc5c1e-d181-4841-a493-abfbb7289cf0)

# Height - Without Outliers using IQR method:
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/39015549-4fd0-413b-a00f-02038c856b8e)
![image](https://github.com/vishnupriyaramesh17/ODD2023---Datascience---Ex-02/assets/119393589/184cec00-1518-4311-a9d8-d4d18ad0d53d)

# Result:
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.













