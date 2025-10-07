<img width="680" height="437" alt="image" src="https://github.com/user-attachments/assets/e6db1b2a-e67f-4e1f-8416-0b183f4a0b49" />## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
import pandas as pd
ds=pd.read_csv("Encoding Data.csv")
ds
```
<img width="382" height="438" alt="image" src="https://github.com/user-attachments/assets/7b2e438f-99c4-4694-bb07-9299a55c72b8" />

```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
a=['Hot','Warm','Cold']
a1=OrdinalEncoder(categories=[a])
a1.fit_transform(ds[["ord_2"]])
```
<img width="227" height="244" alt="image" src="https://github.com/user-attachments/assets/62414a9d-ae74-4a3b-ab87-5a36c2de2a45" />

```
ds['bo2']=a1.fit_transform(ds[["ord_2"]])
ds
```
<img width="398" height="445" alt="image" src="https://github.com/user-attachments/assets/944c8ff5-ffbd-49d7-a00c-1a9a8dbc3cdc" />

```
l=LabelEncoder()
dfc=ds.copy()
dfc['ord_2']=l.fit_transform(dfc['ord_2'])
dfc
```
<img width="386" height="440" alt="image" src="https://github.com/user-attachments/assets/6ba6130a-2894-4ac9-9e4d-0763203c628f" />

```
from sklearn.preprocessing import OneHotEncoder
oh=OneHotEncoder(sparse_output=False)
ds2=ds.copy()
enc=pd.DataFrame(oh.fit_transform(ds2[["nom_0"]]))
ds2=pd.concat([ds2,enc],axis=1)
ds2
```
<img width="524" height="442" alt="image" src="https://github.com/user-attachments/assets/52927266-95a5-4fab-a109-e75be90e4c09" />

```
pd.get_dummies(ds2,columns=["nom_0"])
```
<img width="803" height="443" alt="image" src="https://github.com/user-attachments/assets/874f0682-77de-4ae4-a360-dbe7f5236a75" />

```
pip install --upgrade category_encoders
```
<img width="1468" height="417" alt="image" src="https://github.com/user-attachments/assets/07bfbb42-80fe-4946-ad02-4e1847c250c2" />

```
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df
```
<img width="586" height="448" alt="image" src="https://github.com/user-attachments/assets/9c3de1b7-e62a-48e0-b912-a586cbc197dd" />

```
b=BinaryEncoder()
nd=b.fit_transform(df['Ord_2'])
df
```
<img width="576" height="439" alt="image" src="https://github.com/user-attachments/assets/16101e17-e371-49cc-9fa7-ed2f7d4ac24a" />

```
db=pd.concat([df,nd],axis=1)
db
```
<img width="827" height="444" alt="image" src="https://github.com/user-attachments/assets/e44d8e0c-04ac-45d5-993b-2825828cb3fd" />

```
from category_encoders import TargetEncoder
t=TargetEncoder()
CC=df.copy()
new=t.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
<img width="680" height="437" alt="image" src="https://github.com/user-attachments/assets/9c24753b-a1f6-4294-ae72-ff9efdfd65b4" />

```
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
df
```
<img width="941" height="514" alt="image" src="https://github.com/user-attachments/assets/2f81615c-9a05-4fa7-9d4b-5089e19f54eb" />

```
df.skew()
```
<img width="358" height="249" alt="image" src="https://github.com/user-attachments/assets/baba7fa5-d00f-40ef-963c-94bd517c5394" />












# RESULT:
       # INCLUDE YOUR RESULT HERE

       
