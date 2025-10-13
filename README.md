## EXNO-3-DS

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

```
np.log(df["Highly Positive Skew"])
```
<img width="306" height="565" alt="image" src="https://github.com/user-attachments/assets/8ca48100-7e4a-4748-b6b3-9657a341cc44" />

```
np.reciprocal(df["Moderate Positive Skew"])
```
<img width="311" height="556" alt="image" src="https://github.com/user-attachments/assets/dcf7a6f2-9d47-4c4b-b5db-30b569ff4b12" />

```
np.sqrt(df["Highly Positive Skew"])
```
<img width="372" height="702" alt="image" src="https://github.com/user-attachments/assets/aa959fd2-3917-4640-bec1-65ea2bcd565d" />

```
np.square(df["Highly Positive Skew"])
```
<img width="360" height="698" alt="image" src="https://github.com/user-attachments/assets/a33ee4b6-5bff-49cb-b5d4-7a38ac13c80c" />

```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
<img width="1579" height="642" alt="image" src="https://github.com/user-attachments/assets/ec8f7399-2475-44b8-ad84-6da4ac3a02c2" />

```
df.skew()
```
<img width="495" height="356" alt="image" src="https://github.com/user-attachments/assets/7346d382-74d1-41d7-8093-82ce77b12fb6" />

```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```
<img width="531" height="422" alt="image" src="https://github.com/user-attachments/assets/7d71204e-18cf-4ca6-9ce6-f8bd3e72ab9c" />

```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
<img width="1720" height="532" alt="image" src="https://github.com/user-attachments/assets/424498be-1c84-4557-9148-02346c634dc0" />

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="728" height="549" alt="image" src="https://github.com/user-attachments/assets/fc295671-8576-4bc8-8863-97a9691eccb1" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
<img width="737" height="546" alt="image" src="https://github.com/user-attachments/assets/10720d85-365f-41af-be78-c577b258ace0" />

```
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
<img width="735" height="549" alt="image" src="https://github.com/user-attachments/assets/8a884eb7-ddeb-455d-be71-d1017f53d35f" />

```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```
<img width="725" height="548" alt="image" src="https://github.com/user-attachments/assets/11c5f89e-030e-4018-9edb-5c1e7a51336d" />

```
df1=pd.read_csv("titanic_dataset.csv")
df1
```
<img width="1458" height="512" alt="image" src="https://github.com/user-attachments/assets/3f3eea40-6420-4fe2-92a9-607ab39b952f" />

```
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df1["Age_1"]=qt.fit_transform(df1[["Age"]])
sm.qqplot(df1['Age'],line='45')
plt.show()
```
<img width="721" height="552" alt="image" src="https://github.com/user-attachments/assets/5f7c17ca-c192-456d-a5fd-b7cc7c496f6e" />

```
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```
<img width="720" height="548" alt="image" src="https://github.com/user-attachments/assets/535bfeff-09f8-4df0-93b7-d8392ec6f9f8" />



























# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
