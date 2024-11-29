# project_03
**Documentation for the Diwali Sales Data Analysis Project**
--------------------------------------------------------

#### Overview
This project entails analyzing a dataset called **"Diwali Sales Data"** using Python libraries including NumPy, Pandas, Matplotlib, Seaborn, and Statistics. The objective is to deduce insights from the sales data, visualize trends, and perform exploratory data analysis (EDA).

--------------------------------------------------------

#### Dataset Information
- Total Rows: 11,251  
- Total Columns: 15 (after eliminating unnecessary columns)

##### Important Columns:
1. **User_ID**: Unique identifier for every customer.
2. **Cust_name**: The customer's name.
3. **Product_ID**: Unique identifier for every product.
4. **Gender**: Customer gender (M/F).
5. **Age Group**: The age group category of the customer. Example: 18-25.
6. **Age**: Actual age of the customer.
7. **Marital_Status**: Married status, 0 means the customer is single and 1 indicates that the customer is married.
8. **State**: State.
9. **Zone**: The zone corresponding to the state.
10. **Occupation**: The customer's occupation.
11. **Product_Category**: The product category purchased.
12. **Orders**: Number of orders placed.
13. **Amount**: Total amount spent.

---
### Steps and Analysis

1. **Data Cleaning and Preprocessing**:
   Dropped columns `Status` and `unnamed1` as they had no useful data.
   Checked for missing values using `pd.isnull().sum()`:
     12 missing values in the `Amount` column.
   Removed rows with missing data using `dropna()`.
- Made `Amount` column to `int` for uniformity.

2. **Data Summary**:
    - Applied `.describe()` to fetch the statistical information
    - Age ranged from 12 to 92 years
    - Average number of orders per customer is 2.49
    - Average amount spent ~9,454

3. **Column Rename**
    - Renamed `Marital_Status` to `Shaadi` for easier understanding.

4. **Descriptive Statistics**:
   - Mean, median, and mode for `User_ID`:
     - Mean: 1,003,004.49
     - Median: 1,003,065
     - Mode: 1,001,680

---

#### **Visualizations**

##### 1. **Gender Analysis**:
- **Count of Transactions by Gender**:
  - `sns.countplot()` was used to plot the count of transactions for each gender.
- **Sales by Gender**:
  - Bar plot of total sales amount by gender:
- **Count by gender**: Women sold more than men in total transactions.

2. **Distribution of Transactions Across Age Group:**
- **Transaction Counts Across Age Groups**:
  - Grouped by gender to understand the patterns in buying by age.
- **Sales by Age**:
  - Bar graph indicating total sales by age.
    - **Observation**: The highest sales from transaction count were made by individuals belonging to the 26-35 age group.

3. **State Analysis**:
- **Top 10 States by Orders**:
  - Bar plot showing the number of orders by state.
- **Top 10 States by Sales**:
  - Bar plot showing the total sales amount by state:
    - **Observation**: Maharashtra and Uttar Pradesh were top contributors.

##### 4. **Marital Status Analysis**:
- **Count of Transactions by Marital Status**:
  - Count plot showing transactions based on marital status.
- **Sales by Marital Status and Gender**:
  - Bar plot of sales distribution by marital status and gender:
    Married females spent the most.

##### 5. **Occupation Analysis**:
- **Transactions Count by Occupation**:
  Count plot of the distribution of transactions by occupation.
- **Sales by Occupation**:
  Bar plot of total sales by occupation:
- **Observation**: Health care is the biggest winner in sales.

###### 6. **Product Category Analysis**:
- **Number of Transactions per Product Category**:
  Count plot showing number of transactions for each product category.
- **Sales per Product Category**:
  Bar plot showing top 10 categories with the highest sales:
    - **Observation**: Products under the "Auto" category sold the most revenue.

###### 7. **Top Products by Orders**
- **Bar Plot**:
  - Displayed the top 10 products with the highest number of orders using `groupby` and `nlargest()`.

***

#### **Code Example for a Key Insight**
**Sales by Gender**
```python
sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Gender', y='Amount', data=sales_gen)
```
 Bar chart showing females contributed more to sales.

***

#### **Observations and Insights**
1. **Demographics**:
  Females and the 26-35 age group were the contributors to sales.
2. **Geography**:
- Western (for instance, Maharashtra) and Central (for instance, Uttar Pradesh) regions were the strongest across both orders and sales.
3. **Products**:
    - The "Auto" category was the largest in sales, followed by "Healthcare."
4. **Marital Status**:
    - Married shoppers, especially females, also spent much more.

-----

#### **Conclusion**
This project demonstrates how EDA can uncover insights about the sales and behavior of customers. It emphasizes the role played by data cleaning, preprocessing, and visualization techniques in enabling data-driven decisions.

#### Future Enhancements
1. **Time Analysis:**
   Analyze trends based on months or days, which will indicate peak hours for sales.
2. **Customer Segmentation**
   Segment customers based on spend patterns to target them for campaigns.
3. **Predictive Modeling:**
Predict future sales trends by using machine learning.
