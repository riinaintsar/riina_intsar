# Here are examples of my Python projects

## Data analysis from Titanic dataset 
```py
# Load DataSet into a Pandas DataFrame
import pandas as pd
titanic_df = pd.read_csv('/content/train.csv')

# Display the first few rows
titanic_df.head(n=3)

# Number of rows and columns
rows, columns = titanic_df.shape
print(f"Number of rows: {rows}")
print(f"Number of columns: {columns}")

# Identify missing values
titanic_df_info = titanic_df.info()
missing_values = titanic_df.isnull().sum()
titanic_df_info, missing_values[missing_values > 0]

# Mean, median, mix, max for age
mean_age = titanic_df['Age'].mean()
median_age = titanic_df['Age'].median()
min_age = titanic_df['Age'].min()
max_age = titanic_df['Age'].max()

print(f"Mean age: {mean_age}")
print(f"Median age: {median_age}")
print(f"Minimum age: {min_age}")
print(f'Maximum age: {max_age}')

# Mean, median, mix, max for fare
mean_fare = titanic_df['Fare'].mean()
median_fare = titanic_df['Fare'].median()
min_fare = titanic_df['Fare'].min()
max_fare = titanic_df['Fare'].max()
print(f"Mean ticket price: {mean_fare}")
print(f"Median ticket price: {median_fare}")
print(f"Minimum ticket price: {min_fare}")
print(f'Maximum ticket price: {max_fare}')

# Value counts for "Sex"
titanic_df['Sex'].value_counts()

# Value counts for "Embarked"
titanic_df['Embarked'].value_counts()

# Pie chart for "Age"
import matplotlib.pyplot as plt
import pandas as pd

titanic_df_clean = titanic_df.dropna(subset=['Age']).copy()  # drop non-integar values

age_bins = [0, 18, 35, 55, 75, 100]
age_labels = ['0-18', '19-35', '36-55', '56-75', '76+']

titanic_df_clean['AgeGroup'] = pd.cut(titanic_df_clean['Age'], bins=age_bins, labels=age_labels, right=False) # create new agegroup

age_distribution = titanic_df_clean['AgeGroup'].value_counts().sort_index()
plt.pie(age_distribution.values, labels=age_distribution.index, autopct='%1.1f%%')
plt.title('Age Distribution of Titanic Passengers')
plt.show()
```

![image](https://github.com/user-attachments/assets/7595f133-262e-43ab-8453-81005054e243)



