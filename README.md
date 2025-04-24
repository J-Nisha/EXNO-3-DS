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
df=pd.read_csv("Encoding Data.csv")
df
```
![436853846-47391cc9-2ae1-4374-b6f3-9bdda6fb1a9d](https://github.com/user-attachments/assets/3274e0ac-7433-469b-a08a-1a17b5b318fe)
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![436853994-e84b9bb5-9e3d-4586-bd17-c90b4893a92a](https://github.com/user-attachments/assets/60dfb504-7dc5-4991-852b-3fb8272b2007)
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![436854205-63b08a90-7212-4dc7-b505-3f3dad20c4ab](https://github.com/user-attachments/assets/a37f33d5-0077-45ec-81e3-b68eb4ba6380)
```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![436854327-55295efa-cb26-4026-bf98-5081461ebaec](https://github.com/user-attachments/assets/82e7b7f6-8305-4e71-a924-717febe588a3)
```
from sklearn.preprocessing import OneHotEncoder
df
```
![436854449-b94d74b5-f9af-49a6-ad05-f6515455d3c9](https://github.com/user-attachments/assets/625be959-14ea-4780-9a01-072bdd2d5a0f)
```
ohe=OneHotEncoder(sparse_output=False)
df=df.copy()

enc=pd.DataFrame(ohe.fit_transform(df[['nom_0']]))
enc
```
![436854653-298f7678-2a06-4ddb-ba56-b82789a6477f](https://github.com/user-attachments/assets/2a93ad87-8377-44ce-8a35-f64464c86f57)
```
df2=pd.concat([df,enc],axis=1)
df2
```
![436854920-15540fca-f4a2-4b94-98b7-249c0569320f](https://github.com/user-attachments/assets/076f5d86-d6f0-47ea-914e-ac7ba56f3f63)
```
from category_encoders import BinaryEncoder
df=pd.read_csv(r"C:\Users\admin\Downloads\data (1).csv")
df
```
![436855058-0c8bcc9c-82a0-4d9f-9714-dabd6abcb3c4](https://github.com/user-attachments/assets/ed35273c-79ce-4e29-a5ec-797cb0dcd56a)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```
![436855320-4e727019-2647-44a4-b670-81a4fbc77558](https://github.com/user-attachments/assets/36f3dc44-4241-4bab-8bf5-864f426e9862)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```
![436855445-a1484c9c-add9-4011-967b-811304bc647d](https://github.com/user-attachments/assets/5b0e0d18-dcd5-4541-9d00-c996475a936c)
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv(r"C:\Users\admin\Downloads\Data_to_Transform.csv")
df.skew()
```
![436855616-22a7fbab-66eb-4358-ae34-a0d72380a880](https://github.com/user-attachments/assets/c7358de0-07a8-4cc2-9249-47019cf2019e)
```
np.log(df["Highly Positive Skew"])
```
![436855746-3c403ff1-90ea-461f-8643-bd96c020992f](https://github.com/user-attachments/assets/df822b80-eb19-44f7-bc2d-38f2d94cc91d)
```
np.reciprocal(df["Highly Positive Skew"])
```
![436855943-89e3c66d-7b87-4f75-94dd-86b1b7e8834e](https://github.com/user-attachments/assets/3b5a5cb1-8a9f-4650-a19c-0c97abe2bc41)
```
np.square(df["Highly Positive Skew"])
```
![436855943-89e3c66d-7b87-4f75-94dd-86b1b7e8834e](https://github.com/user-attachments/assets/619aedac-cd26-4a6a-97e7-4a2868a32aab)
```
df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![436856157-eafc031b-9f3d-4855-9b0d-2e1914d3c346](https://github.com/user-attachments/assets/e916996c-7721-4a84-b35c-6670e944ca6a)
```
df["Highly Positive Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![436856268-6d53194a-4c56-4598-bad8-d386a4429a01](https://github.com/user-attachments/assets/8e24fb4b-8634-4bec-a198-80796a9d4afb)
```
df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df['Moderate Negative Skew'])
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
![436856409-00b27c1d-fa97-4110-8476-e80b5bca7192](https://github.com/user-attachments/assets/5a91beea-4f5c-44da-9b0b-6e6d37ea5045)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![436856510-f4343f78-2dd6-4890-860d-7807a34f2523](https://github.com/user-attachments/assets/62128dce-00dc-4e0c-84a6-90017260167a)
```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
![436856593-a1fae4e3-3a7f-40df-8583-61051228abb4](https://github.com/user-attachments/assets/7b1a4b8a-b61f-48b0-b392-5089eefee718)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![436856785-a5bfdfae-6118-4458-91eb-c9971c072a09](https://github.com/user-attachments/assets/65cc08b7-1830-433a-a448-7800270aea69)
# RESULT:
Thus the code for Data Transformation is executed successfully.
      

       
