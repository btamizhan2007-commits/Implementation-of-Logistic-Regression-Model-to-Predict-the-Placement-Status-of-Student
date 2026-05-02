# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student
# NAME: TAMIZHAN B
# REF NO: 212225230283
## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Load the placement dataset using the Pandas library.

2.Create a copy of the dataset and remove unnecessary columns like serial number and salary.

3.Check the dataset for missing values and duplicate records.

4.Convert all categorical attributes into numerical form using Label Encoding.

5.Separate the dataset into independent features (X) and target variable (status).

6.Split the dataset into training and testing sets using an 80:20 ratio.

7.Initialize the Logistic Regression model with a suitable solver.

8.Train the model using the training dataset.

9.Predict the placement status using the test dataset.

10.Evaluate the model performance using accuracy score and classification report.

## Program:
```
/*
Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by: TAMIZHAN B
RegisterNumber: 212225230283

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression

# Load dataset
data = pd.read_csv("Placement_Data (1).csv")

# Drop salary column (contains missing values)
data = data.drop("salary", axis=1)

# Convert categorical data to numeric
data = pd.get_dummies(data, drop_first=True)

# Features and target
X = data.drop("status_Placed", axis=1)
y = data["status_Placed"]

# Split dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)

# Accuracy
print("Accuracy:", model.score(X_test, y_test))

# Use only ONE feature for plotting
X1 = X.iloc[:, 0].values.reshape(-1, 1)

# Train model on single feature
model_plot = LogisticRegression(max_iter=1000)
model_plot.fit(X1, y)

# Scatter plot
plt.scatter(X1, y, color='blue')

# Sigmoid curve
x_values = np.linspace(X1.min(), X1.max(), 100)
y_values = model_plot.predict_proba(x_values.reshape(-1,1))[:,1]

plt.plot(x_values, y_values)

plt.xlabel("Feature")
plt.ylabel("Probability")
plt.title("Logistic Regression Curve")
plt.show()

*/
```

## Output:
<img width="818" height="586" alt="image" src="https://github.com/user-attachments/assets/d2f181b9-c316-4188-aa80-caca6964d3b1" />

## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
