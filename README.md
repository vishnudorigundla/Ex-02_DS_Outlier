# Ex-02_DS_Outlier

# AIM :-
To detect and remove the outliers in the given data set and save the final data.

# EXPLANATION :-
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM :-
 
STEP 1:

Import the pandas package.

STEP 2:

Read the given file.

STEP 3:

Convert the file into a dataframe and get information of the data.

STEP 4 :

Remove the non numerical data columns using drop() method.

STEP 5:

Detect the outliers in the data set using z scores method.

STEP 6:

Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

STEP 7:

Check if the outliersare removed from data set using graphical methods.

STEP 8:

Save the final data set into the file.

# PROGRAM:

```
Developed by: D.Vishnu vardhan reddy
Register number:212221230023


import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data file
df.to_csv('weight.csv', index=False)

```
# OUTPUT :
![o](https://user-images.githubusercontent.com/94175324/161602392-95a29979-cd04-44dc-a143-a04c4e65aa84.png)
![o1](https://user-images.githubusercontent.com/94175324/161602441-6b6edcc4-baf5-4d11-9808-1b081d77e408.png)
![o2](https://user-images.githubusercontent.com/94175324/161602485-99fe90c0-ce85-418b-b520-c2ceaef8865a.png)
![o3](https://user-images.githubusercontent.com/94175324/161602519-e7b74973-e14e-4d10-a37d-8761ba1f815a.png)
![o4](https://user-images.githubusercontent.com/94175324/161602602-70fc063b-1ad8-4bc2-b24b-9de12ac7500d.png)
![o5](https://user-images.githubusercontent.com/94175324/161602643-5b314447-65d7-4aca-974a-3de0d911d08a.png)
![o6](https://user-images.githubusercontent.com/94175324/161602676-9bc722b4-4898-4a1d-8982-a6647c929850.png)
![o7](https://user-images.githubusercontent.com/94175324/161602714-2dcbda8b-f434-4016-a207-38822ea37bc6.png)
![o8](https://user-images.githubusercontent.com/94175324/161602760-a571667a-51e6-4019-8fc8-a588a66083be.png)


# RESULT :
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
