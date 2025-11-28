# Data-visualization---

### 🚕 NYC Taxi Data Analysis — Data Cleaning, Exploration & Visualization

This project performs real–world data analysis using the Seaborn Taxis dataset, demonstrating essential skills in data cleaning, handling missing values, grouping, statistics, and data visualization using Matplotlib and Seaborn.

📦 Dataset Used

We load the taxis dataset using:

df = sns.load_dataset("taxis")


This includes features like:

pickup & dropoff time

distance

fare

tip

tolls

total amount

boroughs & zones

🧹 Part 1 — Data Cleaning & Missing Value Handling
missing = df.isnull().sum()

df['tip'] = df['tip'].fillna(df['tip'].median())
df['distance'] = df['distance'].fillna(df['distance'].median())
df['pickup_borough'] = df['pickup_borough'].fillna(df['pickup_borough'].mode()[0])
df['payment'] = df['payment'].fillna(df['payment'].mode()[0])

df.dropna(subset=['fare', 'pickup'], inplace=True)

print(df.isnull().sum())


✔ Numerical values imputed using median
✔ Categorical values imputed using mode
✔ Rows removed if missing essential keys

📈 Part 2 — Data Visualization
🔹 1. Fare over Time (Time Series)
plt.plot(df_sorted['pickup'], df_sorted['fare'])

🔹 2. Total Fare by Pickup Borough (Bar Chart)
fare_by_borough = df.groupby('pickup_borough')['fare'].sum()
fare_by_borough.plot(kind='bar')

🔹 3. Payment Method Distribution (Pie Chart)
payment_counts = df['payment'].value_counts()
payment_counts.plot.pie()

🔹 4. Trip Distance Distribution (Histogram)
plt.hist(df['distance'], bins=30)

🔹 5. Tip Amount by Pickup Borough (Box Plot)
df.boxplot(column='tip', by='pickup_borough')

🔹 6. Trip Count by Pickup Borough & Payment Type (Count Plot)
sns.countplot(data=df, x='pickup_borough', hue='payment')

🔹 7. Distance vs Fare Relationship (Scatter Plot)
sns.scatterplot(data=df, x='distance', y='fare', hue='pickup_borough')

🔹 8. Correlation Heatmap
sns.heatmap(corr_matrix, annot=True)

🔹 9. Pairwise Feature Relationships (Pair Plot)
sns.pairplot(df_pair, hue='pickup_zone')

🔹 10. Fare Distribution by Payment Method (Violin Plot)
sns.violinplot(data=df, x='payment', y='fare')

🎯 Key Insights

✔ Manhattan dominates trip volume and total fare revenue
✔ Distance strongly correlates with fare
✔ Tip amount varies significantly by borough
✔ Credit card payments dominate transactions
✔ Several visualizations reveal temporal, geographic & monetary patterns

🧠 Skills Demonstrated

✔ DataFrame handling
✔ Missing data treatment
✔ GroupBy operations
✔ Statistical reasoning
✔ Seaborn & Matplotlib visualization
✔ Multi-feature exploratory analysis
✔ Real-world EDA workflow

👤 Author

Riswana Haris

If you want, I can also create:
✔ a summary conclusions section
✔ a Jupyter Notebook version
✔ export cleaned dataset
✔ add project badges & license
✔ create GitHub Pages documentation

