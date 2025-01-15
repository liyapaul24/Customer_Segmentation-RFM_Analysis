# Customer_Segmentation-RFM_Analysis
Project to identify most valuable customer using RFM analysis

### Table of Contents
- [Executive Summary](#executive-summary)
- [Introduction](#Introduction)
- [Dataset Overview](#Dataset-Overview)
- [Dashboard Design](#Dashboard-Design)
- [Key Insights](#Key-Insights)
- [Recommendations](#Recommendations)
- [Challenges and Limitations](#Challenges-and-Limitations)
- [Future Work](#Future-Work)
- [Appendices](#Appendices)
  
### Executive Summary
This report provides a comprehensive analysis of customer segmentation using RFM (Recency, Frequency, Monetary) Analysis. By leveraging a dataset of customer transactions, we performed data cleaning, feature engineering, and clustering to classify customers into distinct categories based on their purchasing behavior. The insights derived from this analysis are instrumental in enhancing customer retention strategies, targeting high-value customers, and improving overall business performance.

### Introduction
**Objective:** The primary objective of this analysis is to segment customers based on their purchasing behavior using RFM Analysis, enabling data-driven decision-making for targeted marketing strategies and improved customer engagement.
**Audience:** This report is intended for business stakeholders, marketing teams, and data analysts who are focused on customer retention, loyalty programs, and revenue optimization.
**Scope:** The scope of this analysis includes cleaning and preprocessing the raw transaction data, engineering relevant features, performing RFM scoring, applying clustering techniques, and categorizing customers into actionable segments. The analysis excludes external factors such as market trends or competitor data.

### Dataset Overview 
The initial dataset comprised **1,067,371** rows and **8** columns, containing transactional information such as Invoice, StockCode, Description, Quantity, InvoiceDate, Price, Customer ID, and Country. The data underwent a thorough cleaning process to ensure accuracy and relevance for analysis.
Key steps in the cleaning process included:
- Handling missing values: Rows with missing Customer IDs were dropped, as this field is critical for analysis.
- Removing duplicates: Ensured unique transaction records.
- Filtering out garbage or irrelevant data: Enhanced data quality.

After the cleaning process, the dataset was reduced to **797,885** rows and **8** columns. This refined dataset served as the foundation for feature engineering and analysis.
     
## Feature Engineering 
Feature engineering was a critical step to derive meaningful insights and facilitate RFM analysis. The following new features were created:
- **Total Spend:** Calculated as "Quantity * Price" for each transaction. This metric provided a measure of the monetary value of each purchase.
- **Recency:** Measured as the number of days since the customer’s last purchase, providing insights into their engagement recency.
- **Frequency:** Represented the total number of unique purchases made by each customer, indicating their shopping frequency.
- **Monetary Value:** Aggregated as the total spend for each customer across all transactions, highlighting their overall contribution.
  
These features were aggregated into a new dataframe with **5,942** unique customers and the following columns: Customer ID, Recency, Frequency, and Monetary.
   
## Outlier Detection and Removal
Outliers were detected in the Recency, Frequency, and Monetary features using **boxplots** and statistical methods like the **Interquartile Range (IQR)**. Specifically:
- Recency Outliers: Customers with excessively high recency values were identified as inactive and excluded to focus on engaged customers.
- Frequency and Monetary Outliers: Extreme values were capped to avoid skewing the clustering process while retaining the integrity of the data.

This ensured a robust dataset for segmentation, minimizing the impact of anomalies.

## RFM Scoring and Clustering

# **RFM Scoring**
Customers were assigned RFM scores based on quartile distributions:
- **R_Score:** Recency scores were assigned such that higher values indicated more recent purchases.
- **F_Score:Frequency scores reflected the number of purchases, with higher values for frequent buyers.
- **M_Score:** Monetary scores captured total spend, rewarding high-value customers.

An overall RFM_Score was computed as the sum of R, F, and M scores, facilitating a comprehensive view of customer behavior.

# **Clustering**
### Key Insights

### Recommendations

   
### Challenges and Limitations
1. **Limited Scope**: The dashboards exclude external factors, such as market trends or competitor analysis.
2. **Lagging Indicators**: Metrics like activation rates and delinquency rates are historical and may not reflect real-time changes.
   
### Future Work
1. **Predictive Analytics**: Use machine learning models to forecast key metrics such as revenue, delinquency rates, and customer churn.
2. **Enhanced Visualizations**: Add drill-through functionality and advanced filtering options in dashboards.
   
### Appendices
