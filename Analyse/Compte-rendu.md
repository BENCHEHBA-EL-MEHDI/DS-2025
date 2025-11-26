# -*- coding: utf-8 -*-
import warnings
warnings.filterwarnings('ignore')

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib
matplotlib.use('Agg')
import matplotlib.pyplot as plt
plt.switch_backend('Agg')

sns.set(style='whitegrid', palette='muted', color_codes=True)

print(f'pandas version: {pd.__version__}')
print(f'numpy version: {np.__version__}')
print(f'seaborn version: {sns.__version__}')
print(f'matplotlib version: {matplotlib.__version__}')

df = pd.read_csv('/kaggle/input/myanimelist-2025/mal_anime.csv', encoding='utf-8')

print('Shape of the dataset:', df.shape)
print('Columns in the dataset:', df.columns.tolist())
print(df.head())

print('Unique values in Episodes column sample:', df['Episodes'].dropna().unique()[:10])
print('Unique values in Premiered column sample:', df['Premiered'].dropna().unique()[:10])

df['Episodes_clean'] = pd.to_numeric(df['Episodes'], errors='coerce')
episodes_missing = df['Episodes_clean'].isnull().sum()
print('Missing numeric Episodes after conversion:', episodes_missing)

def extract_year(premiered_str):
    try:
        return int(premiered_str[-4:])
    except:
        return np.nan

df['Premiered_Year'] = df['Premiered'].dropna().apply(extract_year)
df['Premiered_Year'] = df['Premiered_Year'].combine_first(df['Released_Year'])

for col in ['Popularity', 'Members', 'Favorites']:
    df[col + '_num'] = pd.to_numeric(df[col], errors='coerce')

print(df[['Episodes', 'Episodes_clean', 'Premiered', 'Premiered_Year',
          'Popularity_num', 'Members_num', 'Favorites_num']].head())

plt.figure(figsize=(10, 6))
sns.histplot(df['Score'], kde=True, bins=30, color='skyblue')
plt.title('Distribution of Anime Scores')
plt.xlabel('Score')
plt.ylabel('Frequency')
plt.tight_layout()
plt.show()

plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='Type', palette='viridis')
plt.title('Count of Anime Types')
plt.xlabel('Type')
plt.ylabel('Count')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

plt.figure(figsize=(10, 6))
sns.boxplot(x=df['Score'], color='lightgreen')
plt.title('Box Plot of Anime Scores')
plt.xlabel('Score')
plt.tight_layout()
plt.show()

numeric_df = df[['Episodes_clean', 'Premiered_Year', 'Popularity_num',
                 'Members_num', 'Favorites_num', 'Score']].dropna()

if numeric_df.shape[1] >= 2:
    sns.pairplot(numeric_df)
    plt.show()

if numeric_df.shape[1] >= 4:
    plt.figure(figsize=(10, 8))
    corr = numeric_df.corr()
    sns.heatmap(corr, annot=True, fmt='.2f', cmap='coolwarm')
    plt.title('Correlation Heatmap of Numeric Features')
    plt.tight_layout()
    plt.show()

from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score

features = ['Episodes_clean', 'Premiered_Year']
target = 'Score'

model_data = df[features + [target]].dropna()

X = model_data[features]
y = model_data[target]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

lr_model = LinearRegression()
lr_model.fit(X_train, y_train)

y_pred = lr_model.predict(X_test)

mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print('Mean Squared Error:', mse)
print('R2 Score:', r2)

plt.figure(figsize=(8, 6))
plt.scatter(y_test, y_pred, alpha=0.6, color='coral')
plt.xlabel('Actual Score')
plt.ylabel('Predicted Score')
plt.title('Actual vs Predicted Anime Scores')
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], color='blue', lw=2)
plt.tight_layout()
plt.show()

