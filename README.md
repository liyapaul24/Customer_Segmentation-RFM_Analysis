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
- **Handling missing values:** Rows with missing Customer IDs were dropped, as this field is critical for analysis.
- **Removing duplicates:** Ensured unique transaction records.
- **Filtering out garbage or irrelevant data:** Enhanced data quality.

After the cleaning process, the dataset was reduced to **797,885** rows and **8** columns. This refined dataset served as the foundation for feature engineering and analysis.
     
#### Feature Engineering 
Feature engineering was a critical step to derive meaningful insights and facilitate RFM analysis. The following new features were created:
- **Total Spend:** Calculated as "Quantity * Price" for each transaction. This metric provided a measure of the monetary value of each purchase.
- **Recency:** Measured as the number of days since the customer’s last purchase, providing insights into their engagement recency.
- **Frequency:** Represented the total number of unique purchases made by each customer, indicating their shopping frequency.
- **Monetary Value:** Aggregated as the total spend for each customer across all transactions, highlighting their overall contribution.
  
These features were aggregated into a new dataframe with **5,942** unique customers and the following columns: **Customer ID, Recency, Frequency, and Monetary.**
   
#### Outlier Detection and Removal
Outliers were detected in the Recency, Frequency, and Monetary features using **boxplots** and statistical methods like the **Interquartile Range (IQR)**. Specifically:
- Recency Outliers: Customers with excessively high recency values were identified as inactive and excluded to focus on engaged customers.
- Frequency and Monetary Outliers: Extreme values were capped to avoid skewing the clustering process while retaining the integrity of the data.

This ensured a robust dataset for segmentation, minimizing the impact of anomalies.

#### Clustering and RFM Scoring   

**Clustering**  
The **Elbow Method** was employed to determine the optimal number of clusters, resulting in 3 distinct groups. **K-means clustering** was then applied, yielding the following segments:
- **Cluster 0 (Low-Value):** Customers with high recency, low frequency, and low monetary value.
- **Cluster 1 (Mid-Value):** Customers with moderate recency, frequency, and monetary value.
- **Cluster 2 (High-Value):** Customers with low recency, high frequency, and high monetary value.

![image](https://github.com/user-attachments/assets/4025a00a-e30f-4006-999e-5ebaaf8a2bdf)  

![image](https://github.com/user-attachments/assets/588b5a2f-f8d7-4afb-ad9a-7318e3dd13ba)


**Cluster Averages**  

![image](https://github.com/user-attachments/assets/9e254c38-470e-4a8e-8a6a-6597eb7ea9db)

**RFM Scoring**  
Customers were assigned RFM scores based on quartile distributions:
- **R_Score:** Recency scores were assigned such that higher values indicated more recent purchases.
- **F_Score:** Frequency scores reflected the number of purchases, with higher values for frequent buyers.
- **M_Score:** Monetary scores captured total spend, rewarding high-value customers.

An overall RFM_Score was computed as the sum of R, F, and M scores, facilitating a comprehensive view of customer behavior.

#### Customer Segmentation

**Customer Segments**  
Based on clustering and RFM scores, customers were categorized as follows:  
- VIP: RFM Score ≥ 10.
- Loyal: RFM Score ≥ 7 and < 10.
- At Risk: RFM Score ≥ 4 and < 7.
- Lost: RFM Score < 4.

**Customer Characteristics**  
VIP customers exhibited the lowest recency, highest frequency, and monetary value. Loyal customers displayed moderate levels across all metrics, representing steady engagement. At Risk customers showed infrequent purchases with higher recency values, while Lost customers had the least engagement and spending.

**Customer Counts**  

![image](https://github.com/user-attachments/assets/e27c2a1e-8e93-45fa-8527-075f0a5bf88a)


**Average RFM Scores by Segments**  

![image](https://github.com/user-attachments/assets/9e424a60-db93-4578-b907-738fb8c1339f)  

### Key Insights

1. **VIP Customers**: Comprising **28%** of the total customer base (1,683 out of 5,942), VIPs generate an average monetary value of **$3,467.16**, contributing significantly to overall revenue. They exhibit the lowest recency (avg **35 days**) and highest frequency (avg **12 purchases**), highlighting consistent and high-value engagement.  
2. **Loyal Customers:** Comprising **27%** of the customer base (1,597 customers), loyal customers generate an average monetary value of **$1,268.11**. Their moderate recency (avg **131 days**) and frequency (avg **5 purchases**) make them ideal candidates for upselling and loyalty programs.  
3. **At Risk Customers:** The largest segment, **33%** with 1,957 customers, contributing an average monetary value of **$465.24**. Their relatively high recency (avg **278 days**) and low frequency (avg **2 purchases**) indicate a critical need for re-engagement strategies.
4. **Lost Customers:** Representing **12%** of the customer base (705 customers), this group contributes a minimal average monetary value of **$111.91**. However, they present an opportunity to analyze reasons for disengagement and implement targeted revival campaigns.
5. **Monetary Value Distribution:** Across all segments, there is a clear distinction in spending patterns. High-Value customers dominate with **$4,044.40** average monetary value, whereas At Mid-Value and Low-Value customers represent areas for growth with **$950.24** and **$493.72**, respectively.

### Recommendations  

1. **Retain High-Value Customers:** Offer personalized rewards, VIP-only events, and early access to new products to sustain their loyalty and high spending levels.  
2. **Re-engage At Risk Customers:** Develop tailored email campaigns, discounts, and incentives to encourage repeat purchases. Highlight products or services aligned with their purchase history.  
3. **Revive Lost Customers:** Conduct surveys or outreach campaigns to understand reasons for disengagement. Offer reactivation discounts or limited-time offers to reignite their interest.  
4. **Enhance Loyalty Programs:** Reward consistent engagement among loyal customers with points-based systems, tiered rewards, and exclusive benefits to strengthen long-term relationships.  
5. **Leverage Data-Driven Insights:** Continuously monitor and evaluate customer segments to refine marketing strategies and improve customer lifetime value (CLV).  
   
### Challenges and Limitations
1. The analysis relied solely on transactional data, excluding external factors such as market trends or seasonal effects.  
2. Missing values and outliers required significant cleaning efforts, which may have led to the exclusion of potentially valuable data.  
3. Clustering results are influenced by the choice of features and scaling methods.  
   
### Future Work
1. Incorporate additional data sources such as customer demographics or social media interactions to enrich the analysis.  
2. Explore advanced clustering techniques or machine learning models for improved segmentation.  
   
### Appendices
Code Snippets
Visualizations
