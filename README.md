# Ex02-Outlier:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

## (1) Remove outliers using IQR

## (2) After removing outliers in step 1, you get a new dataframe.

## (3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

## (4) for the data set height_weight.csv find the following

## (i) Using IQR detect weight outliers and print them

## (ii) Using IQR, detect height outliers and print them 

## Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set. An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out).Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.Most machine learning algorithms do not work well in the presence of outlier. So it is desirable to detect and remove outliers.Outliers are highly useful in anomaly detection like fraud detection where the fraud transactions are very different from normal transactions.

# ALGORITHM:
# STEP 1:
Read the given Data

# STEP 2:
Get the information about the data

# STEP 3:
Detect the Outliers using IQR method and Z score

# STEP 4:
Remove the outliers

# STEP 5:
Plot the datas using Box Plot

# Program:

(1) & (2) Examine price_per_sqft column and use IQR to remove outliers and create new dataframe:
```
import pandas as pd
import numpy as np
import seaborn as sns

df = pd.read_csv("bhp.csv")
df

df.head()

df.describe()

df.info()

df.isnull().sum()

df.shape

sns.boxplot(x="price_per_sqft",data=df)
```
```
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
(3) Examine price_per_sqft column and use zscore of 3 to remove outliers.
from scipy import stats

z = np.abs(stats.zscore(df['price_per_sqft']))
df2 = df[(z<3)]
df2

print(df2.shape)
sns.boxplot(x="price_per_sqft",data=df2)
(4)(i) For the data set height_weight.csv detect weight outliers using IQR method
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
(4)(ii) For the data set height_weight.csv detect height outliers using IQR method
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
# Output:
# DATASET NULL VALUES(BHP)
![DATASET NULL VALUES(BHP)](https://user-images.githubusercontent.com/121115650/227604362-c751ae65-828c-48cc-98df-78a3ad5555c4.png)
# DATASET SHAPE WITH OUTLIERS(BHP)
![DATASET SHAPE WITH OUTLIERS(BHP)](https://user-images.githubusercontent.com/121115650/227604390-bd291108-4638-4aff-b918-58ef7152a966.png)
# DATASET BOXPLOT WITH OUTLIERS(BHP)
![DATASET BOXPLOT WITH OUTLIERS(BHP)](https://user-images.githubusercontent.com/121115650/227604413-a7257840-b59b-4129-a155-ff18b51d06cb.png)
# DATASET WITHOUT OUTLIERS(BHP)
![DATASET WITHOUT OUTLIERS(BHP)](https://user-images.githubusercontent.com/121115650/227604428-d9d491d4-761a-4c39-a76b-f7d84a406d36.png)

![DATASET WITHOUT OUTLIERS(BHP) 2](https://user-images.githubusercontent.com/121115650/227604494-2ef4979f-2d03-46a1-acb4-b37fd62be767.png)

![DATASET SHAPE WITHOUT OUTLIERS(BHP)](https://user-images.githubusercontent.com/121115650/227604515-9270cba9-0a15-4c2b-864b-6db28dac8c2b.png)

![DATASET BOXPLOT WITHOUT OUTLIERS(BHP)](https://user-images.githubusercontent.com/121115650/227604534-01a3955f-bc0a-4089-bb20-df9dc09f54e5.png)

![DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP](https://user-images.githubusercontent.com/121115650/227604561-3905291e-9e20-4abf-bc99-a6bcf8c9ac49.png)

![DATASET SHAPE AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)](https://user-images.githubusercontent.com/121115650/227604587-8c22c03c-78e7-4840-aa58-3c6d15f564ec.png)

![DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)](https://user-images.githubusercontent.com/121115650/227604612-b5ea79da-3349-4dba-9f91-dccaa50ba276.png)

![DATASET FOR WEIGHT_HEIGHT_CSV](https://user-images.githubusercontent.com/121115650/227604634-c47241b0-bd14-4229-ab37-6cf3d520529a.png)

![DATASET HEAD(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604663-16a690b4-899c-4a56-9b74-a225bc3b882a.png)

![DATASET INFO(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604680-435b750a-207d-48ff-9bbe-aa24f6136661.png)

![DATASET DESCRIBE(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604702-530f9c48-58cd-4632-9797-d0fe9c20b456.png)

![DATASET NULL VALUES(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604728-3465c5c6-0c00-4a89-8c01-b07a7cb7b9ff.png)

![DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604744-9213e5a4-453b-4633-a755-fb9ffdce1dd9.png)

![DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604767-75682474-5f5b-476e-bff7-8eb8afd2200c.png)

![DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT) 2](https://user-images.githubusercontent.com/121115650/227604784-39b7887e-e920-4e9b-8a49-2daad2a109f9.png)

![DATASET SHAPE(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604801-928afdaf-7ed1-4ffe-8ec0-8ecb1f11b833.png)

![DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)](https://user-images.githubusercontent.com/121115650/227604840-6df0dc5f-e6f5-4809-9bbc-e9c6b00b9269.png)


# Result
DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT).
