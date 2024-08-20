# Exno:1 Data Cleaning Process using Python 

Reg No: 212222110008    
DATE: 20/08/2024

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
```py
import pandas as pd
df= pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/aa145d57-0ae8-498c-9729-a4bf072f39fe)

```py
df. head(5)
```
![image](https://github.com/user-attachments/assets/71bf4e43-c040-4451-80a4-eb4e8fb7fb1f)

```py
df.tail(5)
```
![image](https://github.com/user-attachments/assets/80d9f593-546e-41c9-9508-aa33c7ff93d4)

```py
df.isnull()
```
![image](https://github.com/user-attachments/assets/c4f51819-30a5-4f7f-9da1-a99dbd0e9cb2)

```py
df.notnull()
```
![image](https://github.com/user-attachments/assets/ec96c7af-6ebe-46c5-b73a-c10962b9214b)

```py
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/4fbe8ccc-9c99-462b-8cfd-6e02517e0748)

```py
df.dropna(axis=1)
```
![image](https://github.com/user-attachments/assets/7149c7e8-730b-41d8-a239-013beae0cff7)
```py
df.fillna(100)
```
![image](https://github.com/user-attachments/assets/567bf650-edf5-465e-9f1c-b666358fa58f)
```py
print(df.shape)
```
![image](https://github.com/user-attachments/assets/e144af6c-19e7-41ab-81bc-9729b48ec36a)
```py
df.describe()
```
![image](https://github.com/user-attachments/assets/69037935-9878-46e3-b556-a6d74c18d6f6)
```py
import pandas as pd
import seaborn as sns
ir=pd.read_csv('/content/iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/2807150d-17ba-45b4-b92c-f922648cc5fa)

```py
ir.describe()
```
![image](https://github.com/user-attachments/assets/5579f7b7-2de8-4128-b3ff-7b2b67ac2355)

```py
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/e9e258fb-c9af-4a51-bea2-b277842781ee)

```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/a8f650fd-af75-46a7-93ae-1445338de182)

```py
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3-1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/4e787a90-36cb-4993-b316-7a239cd2a4a7)

```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3-1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/dfaa9ac1-1989-47db-a0ca-8972f8e127d9)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/97d39152-f4f2-4bd9-a0b1-8abd5266465a)
```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

ds=pd.read_csv("/content/heights.csv")
ds
```
![image](https://github.com/user-attachments/assets/d2d6abe7-6645-431f-869a-07b0dd9bd691)
```py
q1=ds['height'].quantile(0.25)
q2=ds['height'].quantile(0.5)
q3=ds['height'].quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/1bcb4a65-7b00-4ede-89cb-973e4d666ae9)

```py
low=q1-1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/f010745c-9f1a-46ad-99a7-6265cf6259da)
```py
high = q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/77dae2ca-469e-48c0-b596-21a454236804)

```py
ds1 =ds[((ds['height']>=low)&(ds['height']<=high))]
ds1
```
![image](https://github.com/user-attachments/assets/4416e3be-8cd3-42fd-aa6c-f81b5737efae)

```py
z=np.abs(stats.zscore(ds['height']))
z
```
![image](https://github.com/user-attachments/assets/51ac9adf-db51-4cf4-a35b-2914416bf578)


```py
ds1=ds[z<3]
ds1
```
![image](https://github.com/user-attachments/assets/a84811f0-6d62-4c57-9f9a-e129e4e27149)


# Result
Hence the data was cleaned , outliers were detected and removed.

