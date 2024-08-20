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
## Data Cleaning:
```PYTHON
import pandas as pd
df=pd.read_csv('/content/SAMPLEIDS.csv')
print(df)
```
![image](https://github.com/user-attachments/assets/b566bda3-f39d-4436-a1ee-1b06d208a906)
```
r.isnull().any()
```
![image](https://github.com/user-attachments/assets/8165c566-c040-4771-8e46-b9d0290ef582)
```
r.isnull().sum()
```
![image](https://github.com/user-attachments/assets/937f3f3b-7813-4e30-ba39-94aedf410eff)
```
r.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/c5730797-8771-4382-8b9a-fca18898c060)
```
r.fillna(5)
```
![image](https://github.com/user-attachments/assets/07a00cfb-885f-4aea-a807-09babe7915e9)
```
r.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/559871be-d372-46c4-90e7-6a151bda9a84)
```
r.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/b5cf0881-181f-4274-ae4e-0656ee721df8)
```
r_dropped = r.dropna()
r_dropped
```
![image](https://github.com/user-attachments/assets/d0c8e5c7-dbb7-452c-a388-374f402cc46a)
```
r.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/cb7e878a-4d60-49dd-beb0-cef0104879e5)

## IQR(Inter Quartile Range)
```
import pandas as pd
r=pd.read_csv('/content/iris.csv')
r
```
![image](https://github.com/user-attachments/assets/2f08b572-6a04-4339-8f17-db1c3ebaa0a4)
```
r.describe()
```
![image](https://github.com/user-attachments/assets/dceeb701-dc12-4ba8-9846-15399d8bd197)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=r)
```
![image](https://github.com/user-attachments/assets/0da16272-c97d-4bed-8a54-ccbd436d4192)

```
q1=r.sepal_width.quantile(0.25)
q3=r.sepal_width.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/1f5c45bd-d85b-4a7c-a68d-6fce11dffbe4)
```
rid=r[((r.sepal_width<(q1-1.5*iqr))|(r.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/df50a16c-8ee2-44f0-92e3-4af0c27a1fc2)
```
delid = r[~((r.sepal_width < (q1 - 1.5 * iqr)) | (r.sepal_width > (q3 + 1.5 * iqr)))]
delid
```
![image](https://github.com/user-attachments/assets/65c498a6-1aac-49e4-99d6-a440bead2c04)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/3f150606-2175-4327-9d0b-f2ebf86bc016)
## Z SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/027848ed-b12e-47a0-b2ae-4ba1df69731c)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/dfce01c6-e71e-434f-8bde-4da12862fb89)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/002edcd8-f292-4a8d-b9d7-129f37bc8ab2)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/41b9a2e4-5dee-4795-ac2b-953b1474fa77)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/4da22d25-57bc-4402-b34e-590e2a7f4539)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/2688136e-96db-4d9b-a857-e17ea33ca376)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/7c4842a7-f6e5-4a82-ad36-3918a3706363)
  
# Result
Thus we have cleaned the data and remove the outliers by detection using IQR and Z-score method.
