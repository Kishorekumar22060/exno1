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

```py
# Developed By: KISHORE KUMAR U
# Register Number: 212222233003
```
<table>
  <tr>
    <td width=50%>


### 1) Read and display DataFrame
```Python
import pandas as pd
df=pd.read_csv('/content/SAMPLEDS.csv')
df
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/13c8033c-7cdb-4b51-bcce-1bf186ca33a7)
</td>
</tr>
<tr>
  <td width=50%>
              
### 2) Display head
```Python
df.head()
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/7e8163c1-7aff-42aa-a9d9-a9be834b0125)
</td>
</tr>
<tr>
  <td width=50%>

### 3) Display tail
```Python
df.tail()
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/31eb0ada-9761-499d-8cf2-31e043eac8e0)
</td>
</tr>
<tr>
  <td width=50%>

### 4) Info of datafram
```Python
df.info()
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/22cd4eee-0b3f-4a2f-9ff7-c5fea86d5703)
</td>
</tr>
<tr>
  <td width=50%>

### 5) Describe about the dataframe
```Python
df.describe()
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/28cfed13-f10d-4062-8b88-3da61848e96c)
</td>
</tr>
<tr>
  <td width=50%>

### 6) Shape of the datafram
```Python
df.shape
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/5814ae95-6244-4dd0-bb1b-43bf0bd5583b)
</td>
</tr>
<tr>
  <td width=50%>

### 7) Checking tha NUll values
```Python
df.isnull().sum()
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/1c352767-c32d-4d18-9fce-3e600d7af552)
</td>
</tr>
<tr>
  <td width=50%>

### 8) Drop the Null values
```Python
x=df.dropna(how='any')
x
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/fdff72dd-a19b-4c72-b492-6fed41b35f54)
</td>
</tr>
<tr>
  <td width=50%>

### 9) Drop the Null values in Total
```Python
tot=df.dropna(subset=['TOTAL'],how='any')
tot
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/d21f329a-35aa-4cd7-912f-99fe36f258b7)
</td>
</tr>
<tr>
  <td width=50%>

### 10) FIll the Null values
```Python
df.fillna(0)
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/8d35ac83-889f-451e-bc63-78fbcf44fb04)
</td>
</tr>
<tr>
  <td width=50%>

### 11) Finding the mean value
```Python
mn=df.TOTAL.mean()
mn
```
  </td>
  <td>
              
#### OUTPUT:

![image](https://github.com/LATHIKESHWARAN/exno1/assets/119393556/489a50a1-eb88-449c-8d7e-bff5e42c5af0)

</td>
</tr>
<tr>
  <td width=50%>

### 12) Fill Null value with Mean value
```Python
df.head()
```
  </td>
  <td>

### IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
ir.describe()
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/5e010ab3-595c-4b9b-9071-97fe8efac859)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/2a607393-798c-4dab-bee2-b559993f435a)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/4c533f9d-99f3-4388-ac0c-dffcbbcda86c)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/38d2c94c-d961-4880-b0a9-fd30d969b8b1)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/91f04cb5-2373-4a33-b59b-8ec01d59d51d)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Kishorekumar22060/exno1/assets/141472136/4acc33ab-b56f-47c2-87ef-5fe0b62fd99c)

### Z Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/080b6095-73da-4bee-a763-08c7a0b81a07)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/ffb0b515-5964-4405-9e0b-6d2c986c3308)


```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/b68f4b97-1246-4747-9aff-06e058c94f44)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/da8aa517-c1de-4e43-91d6-ec677f8beaa5)


```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/5444510b-6eb1-4fdd-a65f-02c85bd685d4)


```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/PSriVarshan/exno1/assets/114944059/02efcb16-a37a-4313-8111-7396dbd21f2e)

```py
df1 = df[z<3]
df1
```

![image](https://github.com/PSriVarshan/exno1/assets/114944059/fbfd480f-960d-4d51-8695-71718cc8a342)

<hr>
              
#### OUTPUT:
![Screenshot 2024-02-23 090324](https://github.com/MAHESWARAN2004/Expno1/assets/119478181/a0a06f86-f464-4d33-935a-a00fbd2d3ef4)
</td>
</tr>
<tr>
  <td width=50%>



# Result
The data clearning has beeen done successfully.
