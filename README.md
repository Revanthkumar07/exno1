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
df = pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="893" height="555" alt="image" src="https://github.com/user-attachments/assets/19587096-6ac8-4499-9c35-0991f9f7a1d1" />

```
df.head( )
```
<img width="853" height="169" alt="image" src="https://github.com/user-attachments/assets/04e44603-a32b-4bdb-9488-3555a22e3e13" />

```
df.tail( )
```
<img width="896" height="166" alt="image" src="https://github.com/user-attachments/assets/fbcbc846-36e9-4f28-aeff-e54127cd9b55" />


```
df.isnull( )
```
<img width="815" height="537" alt="image" src="https://github.com/user-attachments/assets/750802fc-c2ab-4e00-910d-1c7e04437ce0" />

```
df.notnull( )
```
<img width="646" height="552" alt="image" src="https://github.com/user-attachments/assets/6510b77c-f0aa-4715-85e3-27afffbb90c2" />

```
df.isnull().sum()
```
<img width="237" height="212" alt="image" src="https://github.com/user-attachments/assets/4bcd560d-a676-46fe-b7ee-672cdedd1017" />

```
df.isnull().any()
```
<img width="241" height="214" alt="image" src="https://github.com/user-attachments/assets/fdb5bdd7-56a1-4cd4-ad07-84c236a2c36b" />

```
df.dropna(axis=0)
```
<img width="666" height="338" alt="image" src="https://github.com/user-attachments/assets/447ddaaf-08df-4295-8384-b3bccb52e0ff" />

```
df.dropna(axis=1)
```
<img width="295" height="542" alt="image" src="https://github.com/user-attachments/assets/5fbb3fdd-f75a-49b6-8e9d-9bac70185dcf" />

```
df.dropna()
```
<img width="730" height="358" alt="image" src="https://github.com/user-attachments/assets/0a8045e6-b162-4c43-a32f-57874e0df317" />

```
df.fillna(0)
```
<img width="699" height="556" alt="image" src="https://github.com/user-attachments/assets/a63e013c-8ceb-45b9-b329-a03a3a5f5497" />

```
df.fillna(2)
```
<img width="720" height="559" alt="image" src="https://github.com/user-attachments/assets/512dcb19-427f-4121-af12-dc2b84d17c48" />

``` 
df.ffill()
```
<img width="722" height="546" alt="image" src="https://github.com/user-attachments/assets/1505f4f4-c3ca-49b5-8f49-fae6ef48eebc" />

```
df.bfill()
```
<img width="705" height="547" alt="image" src="https://github.com/user-attachments/assets/cba91f7e-8f0e-4ccc-9dfd-cc8f3e778b77" />

```
df.fillna({'GENDERE':'MALE','NAME':'SRI','ADDRESS':'CHENNAI','M1':89.0,'M2':99.0,'M3':77.9,'M4':98.9})
```
<img width="727" height="549" alt="image" src="https://github.com/user-attachments/assets/50ad797a-e2f7-4dfa-ad91-676f90953bd3" />

```
ir = pd.read_csv('iris.csv')
ir
```
<img width="469" height="336" alt="image" src="https://github.com/user-attachments/assets/141a89ea-c7ea-4acb-832a-c505dc3dacf6" />

```
ir.head()
```
<img width="416" height="163" alt="image" src="https://github.com/user-attachments/assets/ebd7d141-635f-4ac4-99e1-4489851e7ba3" />

```
ir.describe()
```
<img width="385" height="246" alt="image" src="https://github.com/user-attachments/assets/1ce7ef00-5ab0-45af-8cf5-1e36d87194a0" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="675" height="436" alt="image" src="https://github.com/user-attachments/assets/606bb6f6-fd54-4800-8787-b37c67bf4682" />
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="916" height="102" alt="image" src="https://github.com/user-attachments/assets/bf52c535-f423-453d-a1e7-adc733e50aaf" />

```
rid = ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width'] 
```
<img width="903" height="97" alt="image" src="https://github.com/user-attachments/assets/d160cac3-ec91-4594-820b-6267e69717e4" />

```
delid = ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid     
```
<img width="423" height="350" alt="image" src="https://github.com/user-attachments/assets/fd1af2c6-e97f-465b-8362-58c6476fcf93" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="694" height="433" alt="image" src="https://github.com/user-attachments/assets/4c6b4b6a-090e-483d-a6b3-008d94684e0d" />

```
import numpy as np
import scipy.stats as stats 
z = np.abs (stats.zscore(delid['sepal_width']))
z
```
<img width="597" height="202" alt="image" src="https://github.com/user-attachments/assets/539e0f1d-a4dd-4095-9c0f-1efeb5b9a29a" />

```
delid = delid[z<3]
delid
```
<img width="453" height="336" alt="image" src="https://github.com/user-attachments/assets/582924cf-0c38-4546-8df4-fe9b19365a8f" />



## Result
The given data has been successfully read, cleaned by handling duplicates and missing values.
