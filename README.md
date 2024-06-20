# Big Mart Sales Prediction using XGBoost🚀

## Project Overview
This project focuses on predicting sales of products in Big Mart outlets across different locations. The dataset is used for cleaning, feature engineering, and training an XGBoost model to predict sales.

## Dataset Overview
The dataset consists of the following columns:

| Column Name       | Description                                           |
|-------------------|-------------------------------------------------------|
| Item_Identifier   | Unique product ID                                     |
| Item_Weight       | Weight of the product                                 |
| Item_Fat_Content  | Whether the product is low fat or regular             |
| Item_Visibility   | Percentage of total display area of all products in the store allocated to the particular product |
| Item_Type         | Category of the product                               |
| Item_MRP          | Maximum Retail Price (price charged for the product)   |
| Outlet_Identifier | Unique store ID                                       |
| Outlet_Establishment_Year | Year of establishment of the store               |
| Outlet_Size       | Size of the store                                    |
| Outlet_Location_Type | Type of city where the store is located (Tier 1, Tier 2, or Tier 3) |
| Outlet_Type       | Grocery store or supermarket                         |
| Item_Outlet_Sales | Sales of the product in the particular store (target variable) |

## Data Cleaning and Preprocessing
- **Handling Missing Values**: Filled missing values in `Item_Weight` using the mean weight per item type. For `Outlet_Size`, filled missing values with mode.
- **Handling Categorical Variables**: Converted categorical variables (`Item_Fat_Content`, `Item_Type`, `Outlet_Size`, `Outlet_Location_Type`, `Outlet_Type`) into numerical(one hot encoding) by using column transformer.
- **Feature Engineering**: Created new features such as `Broader_item_type`(16 categories narrowed down to 3) and `Outlet_Years` to improve model performance.
  
-**Outlier removal** : Removed Rows with item_visibility = 0 as it is not at all possible to have 0 visibility.
-**Distribution** : Transformed Item_visibility and Item_Outlet using log transform as there were right skewed. 
## Model Training with XGBoost🚀
- **Model Training**:  Identified the best model parameters by using gridsearch and 10 cross validation folds. 
## Results✅
 ### Trends Observed:
    - Less sales in the year 1998
    - Food category was the most sold followed by drinks and non consumable items
    - Snack foods, fruits and vegetables, canned foods were the top 3 most sold food items
    - Item_MRP has a high correlation with Item_Outlet_Sales
    - Tier 3 outlets had the highest sales
    - Super Market Type 1 dominated among other outlet types
    - Low Fat Foods were sold more
High Sales indicates higher number of transactions and not the total Item_outlet_sales value
- Achieved an MSE score of 0.271.
- The best parameters are learning rate - 0.1, Tree maximum depth of 3 and a subsample rate of 0.5


