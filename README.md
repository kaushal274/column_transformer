<div align="center">

# 🚀 Column Transformer in Machine Learning

### Transform Different Columns Using Different Preprocessing Techniques

<img src="https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikitlearn&logoColor=white" />
<img src="https://img.shields.io/badge/Machine-Learning-green" />
<img src="https://img.shields.io/badge/Status-Learning-success" />

</div>

---

## 📌 Introduction

**Column Transformer** is a powerful tool provided by Scikit-learn that allows us to apply different preprocessing techniques to different columns of a dataset.

In machine learning, datasets often contain numerical and categorical features. Numerical data may require scaling, while categorical data may require encoding.

Instead of preprocessing every column separately, we can use `ColumnTransformer` to apply multiple transformations in a single step.

## 🎯 Objectives

* Understand the concept of Column Transformer.
* Apply different transformations to different columns.
* Perform one-hot encoding on categorical data.
* Apply standardization to numerical data.
* Prepare a dataset for machine learning.
* Learn how to use `ColumnTransformer` without a Pipeline.

## 🛠️ Technologies Used

* **Python** — Programming language
* **Pandas** — Data manipulation
* **NumPy** — Numerical operations
* **Scikit-learn** — Machine learning and preprocessing

## 📦 Installation

Install the required libraries using pip:

```bash
pip install pandas numpy scikit-learn
```

## 📚 What Is Column Transformer?

`ColumnTransformer` allows us to apply different preprocessing transformations to selected columns of a dataset.

### Syntax

```python
from sklearn.compose import ColumnTransformer

ct = ColumnTransformer(
    transformers=[
        ('name', transformer, columns)
    ],
    remainder='drop'
)
```

### Parameters

| Parameter      | Description                                                        |
| -------------- | ------------------------------------------------------------------ |
| `transformers` | Specifies the transformations to apply.                            |
| `name`         | Name assigned to a transformation.                                 |
| `transformer`  | Preprocessing method, such as `StandardScaler` or `OneHotEncoder`. |
| `columns`      | Columns on which the transformation is applied.                    |
| `remainder`    | Determines what happens to columns that are not specified.         |

* `remainder='drop'`: Drops unspecified columns.
* `remainder='passthrough'`: Keeps unspecified columns without transforming them.

## 💻 Example: Column Transformer Without Pipeline

In this example, we will apply:

* `StandardScaler` to numerical columns.
* `OneHotEncoder` to categorical columns.

### Python Code

```python
import pandas as pd
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder

# Create a dataset
df = pd.DataFrame({
    'Age': [22, 25, 30, 35, 40],
    'Salary': [25000, 30000, 45000, 60000, 80000],
    'City': ['Delhi', 'Mumbai', 'Delhi', 'Pune', 'Mumbai']
})

print("Original Dataset:")
print(df)

# Define numerical and categorical columns
numerical_columns = ['Age', 'Salary']
categorical_columns = ['City']

# Create Column Transformer
ct = ColumnTransformer(
    transformers=[
        ('scaler', StandardScaler(), numerical_columns),
        ('encoder', OneHotEncoder(), categorical_columns)
    ]
)

# Fit and transform the dataset
result = ct.fit_transform(df)

# Display the transformed data
print("\nTransformed Data:")
print(result)
```

## 📊 Expected Output

```text
Original Dataset:
   Age  Salary    City
0   22   25000   Delhi
1   25   30000  Mumbai
2   30   45000   Delhi
3   35   60000    Pune
4   40   80000  Mumbai

Transformed Data:
[[-1.414... -1.0...  1.  0.  0.]
 [-0.919... -0.8...  0.  1.  0.]
 [-0.093... -0.1...  1.  0.  0.]
 [ 0.732...  0.5...  0.  0.  1.]
 [ 1.694...  1.4...  0.  1.  0.]]
```

**Note:** The numerical values are abbreviated for readability. The exact values depend on the dataset. The encoded columns are ordered alphabetically by default: `Delhi`, `Mumbai`, and `Pune`.

## 🔍 How Does It Work?

**Step 1:** Create a dataset using Pandas.

**Step 2:** Identify numerical and categorical columns.

**Step 3:** Apply `StandardScaler` to numerical columns.

**Step 4:** Apply `OneHotEncoder` to categorical columns.

**Step 5:** Use `fit_transform()` to learn the transformations and transform the data.

**Step 6:** Use the transformed data for machine learning.

## 🧠 Important Functions

| Function                  | Purpose                                          |
| ------------------------- | ------------------------------------------------ |
| `fit()`                   | Learns the required transformation parameters.   |
| `transform()`             | Applies the learned transformations.             |
| `fit_transform()`         | Learns and applies transformations in one step.  |
| `get_feature_names_out()` | Retrieves the names of the transformed features. |

### Getting Transformed Feature Names

```python
print(ct.get_feature_names_out())
```

Example output:

```text
['scaler__Age' 'scaler__Salary'
 'encoder__City_Delhi'
 'encoder__City_Mumbai'
 'encoder__City_Pune']
```

## ⚡ Advantages of Column Transformer

* Applies multiple transformations to different columns.
* Reduces repetitive preprocessing code.
* Supports numerical and categorical data.
* Helps maintain consistent preprocessing.
* Integrates with Scikit-learn machine learning workflows.
* Can be used with or without a Pipeline.

## 📂 Project Structure

```text

│
├── README.md
├──covid_toy.csv
├──t.ipynb
├──t2.ipynb
└──ctt.csv
```

## 🚀 Applications

Column Transformer is commonly used for:

* Data preprocessing.
* Feature scaling.
* Categorical encoding.
* Machine learning model preparation.
* Handling mixed-type datasets.
* Building classification and regression workflows.

## 📖 Conclusion

Column Transformer is an important preprocessing tool in Scikit-learn. It allows us to apply different transformations to different columns of a dataset efficiently.

By combining techniques such as `StandardScaler` and `OneHotEncoder`, we can prepare numerical and categorical features for machine learning without writing separate transformation code for every column.

Learning Column Transformer is an important step toward building effective machine learning models.

---

<div align="center">

### 💡 Learn • Practice • Build • Grow

**Made with Python 🐍 and Scikit-learn**

</div>
