### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
from google.colab import files
uploaded = files.upload()

import pandas as pd
df = pd.read_csv(list(uploaded.keys())[0])

X = df[["Age", "Income"]]

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

from sklearn.cluster import KMeans
kmeans = KMeans(n_clusters=3, random_state=42)
df["Cluster"] = kmeans.fit_predict(X_scaled)

df[["Age", "Income", "Cluster"]]
```
### Output:
<img width="1740" height="729" alt="image" src="https://github.com/user-attachments/assets/8317b925-9fa7-423e-b44a-7fcda0b11e2d" />

### Visualization:
```python
def classify_age(age):
    if age <= 30:
        return "Young"
    elif age < 50:
        return "Middle"
    else:
        return "Old"

df["Age_Group"] = df["Age"].apply(classify_age)
import matplotlib.pyplot as plt

labels = ["Young", "Middle", "Old"]
counts = [
    (df["Age_Group"] == "Young").sum(),
    (df["Age_Group"] == "Middle").sum(),
    (df["Age_Group"] == "Old").sum()
]

plt.figure(figsize=(8, 6))
plt.bar(labels, counts)
plt.xlabel("Age Groups")
plt.ylabel("Number of Visitors")
plt.title("Visitor Distribution Across Age Groups")
plt.show()
```
### Output:
<img width="933" height="700" alt="image" src="https://github.com/user-attachments/assets/87cadb39-f507-47ec-bcc5-3bae214e2156" />

### Result:
Implementation of Cluster and Visitor Segmentation for navigation patterns was executed successfully.
