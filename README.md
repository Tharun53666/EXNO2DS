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

#code:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
```


#output:


<img width="1583" height="707" alt="image" src="https://github.com/user-attachments/assets/39b5541e-1a10-4e0b-a78d-19820ab14351" />


#code:
```
df.info()
```


#output:


<img width="712" height="492" alt="image" src="https://github.com/user-attachments/assets/fec5f6b0-7e85-400f-8c05-ee715574a56c" />



#code:
```
df.describe()
```


#output:


<img width="921" height="436" alt="image" src="https://github.com/user-attachments/assets/45273d6a-a359-414f-8afb-e51b9f2230b9" />




#code:
```
df.dtypes
```



#output:



<img width="762" height="638" alt="image" src="https://github.com/user-attachments/assets/01ec7fbf-c423-499c-a784-4b5168879f5f" />



#code:
```
df.shape
```

#output:



<img width="563" height="107" alt="image" src="https://github.com/user-attachments/assets/1f11f9da-6510-462e-af02-12139a51cfe3" />



#code:
```
df.value_counts()
```



#output:



<img width="1657" height="662" alt="image" src="https://github.com/user-attachments/assets/0416fffe-7e6a-41fe-8fe6-6fd073985c2c" />




#code:
```
df['Age'].value_counts()
```



#output:


<img width="827" height="655" alt="image" src="https://github.com/user-attachments/assets/634a8a98-7a81-42e0-81dd-4be09ffe4781" />




#code:
```
df.set_index("PassengerId", inplace=True)
df
```



#output:



<img width="1533" height="647" alt="image" src="https://github.com/user-attachments/assets/c70abe3b-a1b2-44c1-b8dc-335a0d9c961f" />



#code:
```
df.nunique()
```


#output:


<img width="533" height="588" alt="image" src="https://github.com/user-attachments/assets/1e402309-9231-41bc-aff0-5385ca3cf7d1" />



#code:
```
sns.countplot(data=df,x='Survived')
```


#output:




<img width="986" height="647" alt="image" src="https://github.com/user-attachments/assets/382781d4-82bb-4f09-943e-f477a6baf710" />



#code:
```
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```



#output:



<img width="1512" height="697" alt="image" src="https://github.com/user-attachments/assets/bd4a46ce-ceb2-4722-b1fd-d36fd9e358a8" />



#code:
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```



#output:



<img width="1052" height="727" alt="image" src="https://github.com/user-attachments/assets/8d012b99-9bc3-4ee6-9117-24a491303625" />



#code:
```
df.boxplot(column="Age",by="Survived")
```


#output:



<img width="992" height="688" alt="image" src="https://github.com/user-attachments/assets/9081208c-e06b-4117-ba32-0eb78956cde2" />



#code:
```
sns.scatterplot(x=df["Age"],y=df["Fare"])
```



#output:



<img width="921" height="642" alt="image" src="https://github.com/user-attachments/assets/59efa80d-5537-44ab-b6d3-ad771708cf8d" />



#code:
```
fig, axl=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=axl,x='Pclass',y='Age',hue='Gender',data=df)
```



#output:



<img width="1026" height="662" alt="image" src="https://github.com/user-attachments/assets/cdbae84e-e3de-47e0-845f-ca246dea393e" />




#code:
```
plt=sns.boxplot(x='Pclass',y='Age',hue='Gender',data=df)
```



#output:



<img width="947" height="620" alt="image" src="https://github.com/user-attachments/assets/bf4ac603-0883-4052-b89d-55a3f53491b4" />



#code:
```
import seaborn as sns
sns.catplot(x='Pclass',y="Age",hue="Gender",col="Survived",kind="box",data=df)
```



#output:



<img width="1487" height="740" alt="image" src="https://github.com/user-attachments/assets/556320e3-6b35-40ef-ade0-af92d5099830" />




#code:
```
sns.catplot(data=df,col="Survived",x="Gender",hue='Pclass',kind="count")
```



#output:


<img width="1447" height="707" alt="image" src="https://github.com/user-attachments/assets/0b77fdf7-7c01-4ab2-9fb2-98187a30d5cb" />




#code:
```
corr=df.corr(numeric_only=True)
sns.heatmap(corr,annot=True)
```



#output:



<img width="873" height="658" alt="image" src="https://github.com/user-attachments/assets/815f63d5-0808-46a8-9af9-0f5f3eb17483" />




#code:
```
corr=df.select_dtypes(include=np.number).corr()
sns.heatmap(corr,annot=True)
```


#output:



<img width="825" height="638" alt="image" src="https://github.com/user-attachments/assets/ed37460f-8a8d-44f9-9cba-3cb11ad5a926" />



# RESULT:
Thus the programs are executed successfully.
