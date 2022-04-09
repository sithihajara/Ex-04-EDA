# Ex-04-EDA
## AIM
To perform EDA on the given data set.

## Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM
### STEP 1
Import the required packages(pandas,numpy,seaborn).

### STEP 2
Read and Load the Dataset

### STEP 3
Remove the null values from the data and remove the outliers.

### STEP 4
Remove the non numerical data columns using drop() method.

### STEP 5:
returns object containing counts of unique values using (value_counts()).

### STEP 6:
Plot the counts in the form of Histogram or Bar Graph.

### STEP 7:
find the pairwise correlation of all columns in the dataframe(.corr()).

### STEP 8:
Save the final data set into the file.

## CODE 
```
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df= pd.read_csv('supermarket.csv')
df.head()
df.info()
df.isnull().sum()
df.boxplot()
cols = ['Tax 5%', 'Total','gross margin percentage','Payment']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["Total"].value_counts()
plt.title('Grouped by Total')
sns.countplot(x="Total",data=df)
df["Payment"].value_counts()
plt.title('Grouped by Payment')
sns.countplot(x="Payment",data=df)
df["City"].value_counts()
plt.title('Grouped by City')
sns.countplot(x="City",data=df)
df["Product line"].value_counts()
plt.title('Grouped by Product line')
sns.countplot(x="Product line",data=df)
sns.displot(df["Quantity"])
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Total",hue="Customer type",data=df)
pd.crosstab(df["Total"],df["Payment"])
pd.crosstab(df["Quantity"],df["City"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```
## OUTPUT
![f1](https://user-images.githubusercontent.com/94219582/162558694-1896ea54-b52c-4d9d-b3ae-dc098f83334b.PNG)
![f2](https://user-images.githubusercontent.com/94219582/162558702-a7c03ecd-bb90-4bc2-8903-2ba45db70b88.PNG)
![f3](https://user-images.githubusercontent.com/94219582/162558710-f4b84be4-4237-48e2-9c3a-6cc797355cee.PNG)
![f4](https://user-images.githubusercontent.com/94219582/162558715-9d1d303a-7a1b-42d1-9dcb-2124715562f7.PNG)
![f5](https://user-images.githubusercontent.com/94219582/162558723-06a1bf4b-5f7c-4322-938f-fd9b822e02d8.PNG)
![f6](https://user-images.githubusercontent.com/94219582/162558727-40484e6f-93c0-47b4-9172-44902178a35b.PNG)
![f7](https://user-images.githubusercontent.com/94219582/162558734-696f5c46-3091-4470-815c-6f1016abd138.PNG)
![f8](https://user-images.githubusercontent.com/94219582/162558737-4d9f547e-08a3-4e9e-861b-b3264e4f5210.PNG)
![f9](https://user-images.githubusercontent.com/94219582/162558743-65ff4cbf-e8bf-484a-af42-6b6f4175713a.PNG)

## RESULT
The data has been cleaned, outlier has been removed and the EDA on the given data has been performed.
