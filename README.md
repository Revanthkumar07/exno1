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
DONE BY B V REVANTH KUMAR
REG NO: 212224240023
```            
```
import numpy as np
import pandas as pd
df = pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="1275" height="864" alt="image" src="https://github.com/user-attachments/assets/51ff2dd3-fc52-42de-a3d4-70da87485b49" />


```
df.head()
```
<img width="1040" height="252" alt="image" src="https://github.com/user-attachments/assets/5015c2d9-6859-4e07-8b74-07e83f31a643" />


```
df.tail()
```
<img width="1083" height="276" alt="image" src="https://github.com/user-attachments/assets/0534bf8c-d397-4b5d-8ce1-6d75603da2b7" />


```
df.isnull()
```
<img width="1023" height="856" alt="image" src="https://github.com/user-attachments/assets/264f2e09-58c9-4f71-a0c5-01c8fab061cc" />


```
df.isnull().sum()
```
<img width="336" height="584" alt="image" src="https://github.com/user-attachments/assets/1b4ef06f-e6e8-4c1d-b3e6-a870a0b93b66" />


```
df.isnull().any()
```
<img width="405" height="572" alt="image" src="https://github.com/user-attachments/assets/77237597-b6d0-4783-b1fa-195d664619d8" />


```
df.dropna()
```
<img width="1194" height="568" alt="image" src="https://github.com/user-attachments/assets/cf83006a-ff73-46a1-8010-9caec92d0a2a" />



```
df.dropna(axis=1)
```
<img width="499" height="850" alt="image" src="https://github.com/user-attachments/assets/c4c5953e-6060-4c00-abc7-fa12e9edbdbc" />

```
df.fillna(5)
```
<img width="1227" height="852" alt="image" src="https://github.com/user-attachments/assets/dc581e48-5bf9-4e47-8c3a-c56c36f84fc8" />


```

df.fillna(method = 'ffill')
```
<img width="1094" height="848" alt="image" src="https://github.com/user-attachments/assets/16086396-bedd-4187-b5d3-7343bd681f1e" />


```
df.fillna(method = 'bfill')
```
<img width="1110" height="844" alt="image" src="https://github.com/user-attachments/assets/7bed128e-dce3-4546-945c-baf911318734" />


```
df.fillna({'NAME':"JAI",'DOB':'23-12-2006','GENDER':'MALE','M1':100,'M2':100,'M3':100,'M4':100,'TOTAL':400,'AVG':100})
```
<img width="1149" height="861" alt="image" src="https://github.com/user-attachments/assets/f72708da-586a-43dc-b2e6-302dd8b8d8c8" />


```
df1=pd.read_csv("/content/iris.csv")
df1
```
<img width="829" height="487" alt="image" src="https://github.com/user-attachments/assets/18e483e9-4df9-4b91-b8a1-79f54689f4f4" />


```
df1.describe()
```
<img width="749" height="387" alt="image" src="https://github.com/user-attachments/assets/34d9430e-9850-458f-aecb-c354f0b980dc" />


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=df1)
```
<img width="845" height="575" alt="image" src="https://github.com/user-attachments/assets/fd19d362-5523-4e68-9b2c-a4c57bada81c" />



```
q1=df1.sepal_width.quantile(0.25)
q3=df1.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="522" height="165" alt="image" src="https://github.com/user-attachments/assets/fe83f45c-bd80-4efc-b81b-6cea24bddcb6" />



```
new=df1[(df1.sepal_width>(q1-1.5*iqr))& (df1.sepal_width<(q3+1.5*iqr))]
new
```
<img width="856" height="511" alt="image" src="https://github.com/user-attachments/assets/83990680-eabc-4b61-92d7-a712f1303a95" />



```
sns.boxplot(x='sepal_width',data=new)
```
<img width="914" height="577" alt="image" src="https://github.com/user-attachments/assets/51318c8f-4e11-4dc2-a1ff-6c9360923b69" />

```
import numpy as np
import scipy.stats as st
z=np.abs(st.zscore(df1.sepal_width))
print(z)
```
<img width="860" height="548" alt="image" src="https://github.com/user-attachments/assets/9b76366c-38a3-401e-bdec-1c79efad4af4" />

```
dfff=df1[z<3]
dfff
```
<img width="818" height="522" alt="image" src="https://github.com/user-attachments/assets/fb04637b-1dbf-4faa-901b-a175ba991723" />



# Result
Thus to read the given data and perform data cleaning and save the cleaned data to a file done successfully.


