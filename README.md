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
       # INCLUDE YOUR CODING AND OUTPUT SCREENSHOTS HERE

import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

<img width="584" height="552" alt="Screenshot 2025-12-27 201731" src="https://github.com/user-attachments/assets/7aa0b610-7942-44bb-90a9-8ba98ebfbe71" />

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])

<img width="287" height="294" alt="Screenshot 2025-12-27 201741" src="https://github.com/user-attachments/assets/fce4913b-4d57-4e29-aae7-f51ffa3b7877" />

df['bo2']=e1.fit_transform(df[["ord_2"]])
df

<img width="519" height="544" alt="Screenshot 2025-12-27 201752" src="https://github.com/user-attachments/assets/2aa4df28-ea33-4d93-b9e3-4ec64b02e8fe" />

le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc

<img width="594" height="532" alt="Screenshot 2025-12-27 202040" src="https://github.com/user-attachments/assets/98eee1e0-47b1-4f07-a4a9-3a5aef44c92a" />

from sklearn.preprocessing import OneHotEncoder
import pandas as pd

ohe = OneHotEncoder(sparse_output=False)   # use sparse_output instead of sparse
df2 = df.copy()
enc = pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]),
                   columns=ohe.get_feature_names_out(["nom_0"]))  # add column names
df2 = pd.concat([df2, enc], axis=1)
df2

<img width="991" height="548" alt="Screenshot 2025-12-27 202101" src="https://github.com/user-attachments/assets/26807997-9efc-4ff3-96b4-4c130bc16a4e" />

pd.get_dummies(df2,columns=["nom_0"])

<img width="1016" height="406" alt="Screenshot 2025-12-27 202118" src="https://github.com/user-attachments/assets/147563fd-0815-47a0-88e5-8e7fa94b266d" />

from category_encoders import BinaryEncoder
import pandas as pd

df = pd.read_csv("data.csv")
be = BinaryEncoder()
nd = be.fit_transform(df[['Ord_2']])   # Pass as DataFrame, not Series
dfb = pd.concat([df, nd], axis=1)
dfb

<img width="981" height="488" alt="Screenshot 2025-12-27 202127" src="https://github.com/user-attachments/assets/1a92781a-69d8-495c-8f28-507d591960a0" />

from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC


<img width="865" height="558" alt="Screenshot 2025-12-27 202137" src="https://github.com/user-attachments/assets/356ccffc-8f63-48fb-9687-15b6da4d556d" />

import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
df


<img width="927" height="672" alt="Screenshot 2025-12-27 202149" src="https://github.com/user-attachments/assets/ef994966-6c20-4029-815d-e71b1a0945f0" />

df.skew()

<img width="452" height="301" alt="Screenshot 2025-12-27 202158" src="https://github.com/user-attachments/assets/f4827c23-3fce-4bcb-9760-81e93f9d783e" />

np.log(df["Highly Positive Skew"])

<img width="409" height="698" alt="Screenshot 2025-12-27 202210" src="https://github.com/user-attachments/assets/de18b825-cdd4-44bd-a076-d70b06894e36" />

np.reciprocal(df["Moderate Positive Skew"])

<img width="456" height="695" alt="Screenshot 2025-12-27 202223" src="https://github.com/user-attachments/assets/679cc682-f0c4-405c-8d9b-332c43c2cbc2" />

np.sqrt(df["Highly Positive Skew"])

<img width="389" height="685" alt="Screenshot 2025-12-27 202234" src="https://github.com/user-attachments/assets/b4777680-9353-47d0-adcb-110e843e42d8" />

np.square(df["Highly Positive Skew"])

<img width="392" height="689" alt="Screenshot 2025-12-27 202244" src="https://github.com/user-attachments/assets/5a8d6426-be45-4133-8bbf-8935723e3c93" />

df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df

<img width="897" height="697" alt="Screenshot 2025-12-27 202254" src="https://github.com/user-attachments/assets/ae673e32-62c4-4bc1-b84b-98d2d143e096" />

df.skew()

<img width="497" height="344" alt="Screenshot 2025-12-27 202305" src="https://github.com/user-attachments/assets/3e3a6054-dd4e-4036-8412-5940dabce7e1" />

df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()

<img width="577" height="415" alt="Screenshot 2025-12-27 202314" src="https://github.com/user-attachments/assets/bc66f78b-8a70-446e-987b-ec451b2ca069" />

from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df

<img width="1035" height="326" alt="Screenshot 2025-12-27 202325" src="https://github.com/user-attachments/assets/3d8e6779-8eb8-453a-9996-2f8adb805f2d" />

import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()

<img width="899" height="676" alt="Screenshot 2025-12-27 202338" src="https://github.com/user-attachments/assets/dcaf7182-facc-4e3c-a774-ea3d771d7c84" />

sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()

<img width="894" height="673" alt="Screenshot 2025-12-27 202349" src="https://github.com/user-attachments/assets/aa9cb076-0294-4406-be6f-a60bf41f3db9" />

from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()

<img width="879" height="665" alt="Screenshot 2025-12-27 202359" src="https://github.com/user-attachments/assets/c3084e6b-2b90-46f8-8130-acc7b5cf29b0" />

df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()

<img width="880" height="667" alt="Screenshot 2025-12-27 202410" src="https://github.com/user-attachments/assets/8dede879-70f6-466d-833c-94ec0348ee3b" />

dt=pd.read_csv("titanic_dataset.csv")
dt
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45')
plt.show()

<img width="862" height="668" alt="Screenshot 2025-12-27 202419" src="https://github.com/user-attachments/assets/7a83742b-f6d8-4192-b1f6-6b0759d47f6c" />

sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()

<img width="882" height="663" alt="Screenshot 2025-12-27 202429" src="https://github.com/user-attachments/assets/01f0e2f9-be39-4289-af77-2fd53234a28e" />



# RESULT:

Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.



       
