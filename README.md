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

## Top 10 and bottom 10 products by total profit
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
- From this:

From this I gathered:
Most profitable regions (by total profit):-
West: 108,418 total profit, highest and also highest average profit per order.
Least  profitable is:-
South: 46,749 total profit, moderate performance.
Central: 39,706 total profit, lowest total and lowest average profit per order.


Top-performing product (by total profit) :
(By summeing Profit by Product Name)

Canon imageCLASS 2200 Advanced Copier is the clear standout with ~25k profit.
High-margin, high-ticket office equipment and devices dominate the top
Various copiers/printers (Canon, HP, Zebra)
Binding machines, shredders, and wireless headset systems
These are likely key drivers of profitability and should be:

Protected on margin (avoid over-discounting).
Supported with inventory and sales focus.


Bottom-performing products (most unprofitable):

Cubify CubeX 3D Printer (Double/Triple Head) and Lexmark MX611dhe Monochrome Laser Printer are heavily negative:
Large absolute losses per product line (−8.9k and −4.6k).
Several conference tables, videoconferencing units, and some binding/letter-opening equipment are consistently unprofitable.
These products likely suffer from:

Deep discounting,
High cost vs selling price,
Or frequent returns/credits.
They are good candidates for:

Pricing review (reduce discounting or raise price),
Vendor renegotiation,
Or even rationalization (reduce focus or discontinue) if they cannot be made profitable.
Summary
Region winners: West and East, especially West, are your strongest profit centers.
Region laggard: Central is underperforming both in total and per-order profitability; worth a deeper dive into pricing, mix, and discounting there.
Product winners: High-end copiers/printers and some specialized office equipment drive a large share of profit.
Product losers: Certain 3D printers, printers, large meeting tables, and some specialty devices destroy value and should be investigated or deprioritized.
If you want, I can next:

Break product profitability down by region (e.g., which products lose money specifically in Central), or
Look at category/sub-category profitability to see if certain product types are systematically weak.
