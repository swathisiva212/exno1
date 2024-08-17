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
~~~
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
~~~
![Screenshot 2024-08-17 133731](https://github.com/user-attachments/assets/b1cbacc0-0f7a-43ef-9e85-ef72797ee042)
```
df.head(6)
```
![Screenshot 2024-08-17 134240](https://github.com/user-attachments/assets/4d527b58-809c-4bb9-9564-1bc90ab36a7f)
~~~
df.tail(6)
~~~
![tail](https://github.com/user-attachments/assets/a42a919b-9ad9-4bb5-9cc9-f50b54cc3526)
~~~
df.isnull()
~~~
![null](https://github.com/user-attachments/assets/4651e847-13ff-454a-ad14-6cfd71d9b985)
~~~
df.notnull()
~~~
![Screenshot 2024-08-17 134448](https://github.com/user-attachments/assets/236a7d9f-3551-4f6d-9176-b7f1128d4038)

~~~
df.dropna(axis=0)
~~~
![Screenshot 2024-08-17 134455](https://github.com/user-attachments/assets/86a150fb-a742-4580-b1f5-43782f062184)
~~~
df.fillna(0)
~~~
![Screenshot 2024-08-17 134510](https://github.com/user-attachments/assets/03b83136-dea5-4824-abe2-a2ea66c164ff)
~~~
print(df.shape)
~~~
![Screenshot 2024-08-17 134518](https://github.com/user-attachments/assets/8fd5d9d6-06f8-4dc3-8089-076c47b8d20d)
~~~
df.describe()
~~~
![Screenshot 2024-08-17 134600](https://github.com/user-attachments/assets/832427ba-9a92-4105-a180-1b3f8d531915)
# IQR:
~~~
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
~~~
![Screenshot 2024-08-17 134610](https://github.com/user-attachments/assets/e63f896a-8f97-4b28-875c-27ad7b3b19f9)
~~~
ir.describe()
~~~
![Screenshot 2024-08-17 134619](https://github.com/user-attachments/assets/8ef8ed5a-dfa6-4087-a5dc-d3bc2eec0302)
~~~
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
~~~
![Screenshot 2024-08-17 134627](https://github.com/user-attachments/assets/ee55a266-e105-4417-984b-6f31fb6d93c7)
~~~
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
~~~
![Screenshot 2024-08-17 134638](https://github.com/user-attachments/assets/417615b6-b710-48dd-bc0a-4fd444ed16ba)
~~~
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
~~~
![Screenshot 2024-08-17 134645](https://github.com/user-attachments/assets/425cef6d-cd8e-45a5-b21b-c0ad113a8002)
~~~
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
~~~
![Screenshot 2024-08-17 134653](https://github.com/user-attachments/assets/11c04a31-a571-4b06-acca-20d4d48ca429)
~~~
sns.boxplot(x='sepal_width',data=delid)
~~~
![Screenshot 2024-08-17 134659](https://github.com/user-attachments/assets/2fc13aea-8934-45ac-bb3a-bd8f209bd7f4)
# Z-SCORE
~~~
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv('/content/heights.csv')
dataset
~~~
![Screenshot 2024-08-17 134706](https://github.com/user-attachments/assets/b244041b-da3b-4fce-91a7-3b3179b3a2f0)
~~~
df=pd.read_csv('/content/heights.csv')
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)

iqr=q3-q1
iqr
~~~
![Screenshot 2024-08-17 134712](https://github.com/user-attachments/assets/d54639ac-fcda-4ac9-a987-5d4e69d1a228)
~~~
low=q1-1.4*iqr
low
~~~
![Screenshot 2024-08-17 134717](https://github.com/user-attachments/assets/bf609cba-fcbd-498f-a9c1-1654c92a2926)
~~~
high=q3+1.5*iqr
high
~~~
![Screenshot 2024-08-17 134724](https://github.com/user-attachments/assets/2a8e87c6-fa56-496b-ad49-e79e34ed4898)
~~~
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
~~~
![Screenshot 2024-08-17 134729](https://github.com/user-attachments/assets/1b5addd2-825c-487f-be73-d674e843c8cc)
~~~
z=np.abs(stats.zscore(df['height']))
z
~~~
![Screenshot 2024-08-17 134737](https://github.com/user-attachments/assets/2381afe9-604c-4c42-861e-2a70f7d15321)
~~~
df1=df[z<3]
df
~~~
![Screenshot 2024-08-17 134745](https://github.com/user-attachments/assets/ff944025-0b51-4b58-863d-caa02148c45c)

# Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.       
