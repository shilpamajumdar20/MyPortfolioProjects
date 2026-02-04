# Exploratory Data Analysis (EDA) of Superstore Dataset using Julius AI 
Prompt Used: Determine which regions (e.g., West vs. Central) are most profitable and identify top/bottom-performing products.
## Load Superstore data, inspect, and compute profitability by region and product
import pandas as pd
from tqdm import tqdm

## Read CSV
superstore_df = pd.read_csv('Sample - Superstore.csv', encoding='ISO-8859-1')

print(superstore_df.head())

## Profit by region
profit_by_region = superstore_df.groupby('Region', as_index=False)['Profit'].sum().sort_values('Profit', ascending=False)
print(profit_by_region)

## Profit by product (Product Name)
profit_by_product = superstore_df.groupby('Product Name', as_index=False)['Profit'].sum()

# Top 10 and bottom 10 products by total profit
top_products = profit_by_product.sort_values('Profit', ascending=False).head(10)
bottom_products = profit_by_product.sort_values('Profit', ascending=True).head(10)

print(top_products)
print(bottom_products)
 This code snippet loads Superstore data, calculates total profit by region and product, and identifies the top and bottom 10 products based on profit.
- Load Superstore data from a CSV file
- Group data by region and sum profits, sorting in descending order
- Group data by product name and sum profits
- Identify top 10 products by profit
- Identify bottom 10 products by profit
