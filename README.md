
# Customer Value Maximization & Churn Analysis 

## Intro

Nile, an E-commerce store, hired me as a data Analyst for churn impact analysis to enable targeted, data-driven retention strategies that reduce churn and support sustainable growth.

In B2C companies, a small proportion of customers often contributes a disproportionately large share of revenue, making customer retention and understanding behavior critical. Analyzing customer data, such as purchasing patterns, price sensitivity, and order history, helps businesses optimize operations, predict future sales, and improve decision-making.

Customer retention is 6x more cost-effective than acquisition, and even small improvements can significantly boost profitability.

---

## Objective

- Most organizations allocate 80% of their marketing budget to filling the funnel (Acquisition), while allowing 30-50% of acquired assets to churn due to generic, non-personalized retention strategies.
- The Profitability Lever: A mere 5% increase in retention correlates to a 25% to 95% increase in net profitability (Bain & Co).

Evaluating current customers in order to enhance their lifetime value becomes a critical factor to decide the success or failure of a business. Our objectives are:

1. Customer Segmentation  
2. Customer Lifetime Value Prediction  
3. Churn Prediction  
4. Predicting Next Purchase Day  
5. Predicting Sales  

---

## Data Structure & Initial Checks

The analysis utilizes the Online Retail II dataset (UCI Machine Learning Repository), a robust collection of over 1 million rows of transaction data from a UK-based retailer between 2009 and 2011.

Dataset - https://www.kaggle.com/mashlyn/online-retail-ii-uci

- Dataset Size: 1,067,371 rows × 8 columns.
- Time Period: 01/12/2009 – 09/12/2011.
- Key Features: Customer ID, Invoice Date, Quantity, Unit Price, Country.
- Dataset Link: https://www.kaggle.com/mashlyn/online-retail-ii-uci
<img width="602" height="484" alt="Picture1" src="https://github.com/user-attachments/assets/4078c727-4397-4704-a56a-636345277512" />

---

## KPIs

Data Integrity Strategy: Prior to modeling, a rigorous cleaning process was applied to ensure the "North Star Metric" 'Revenue', was calculated accurately.

**Lifetime Value** = ( Total Gross Revenue ) - ( Total Cost )  
**Revenue** = Active Customers × Order Count × Avg Revenue per Order  

Other metrics we will be considering are:

- Monthly Revenue Growth Rate  
- Monthly Active Customers  
- Monthly Order Count  
- Average Revenue per Order  
- New Customer Ratio  
- Monthly Retention Rate  
- Cohort based Retention Rate  

---

## Analytical Framework

The project follows a structured, production-ready pipeline:

1. Metric discovery & North Star definition  
2. RFM clustering & customer segmentation  
3. Lifetime Value prediction  
4. Churn modeling  
5. Next purchase day prediction  
6. Sales forecasting & business validation  

---

## Flowchart / Architecture
<img width="602" height="580" alt="Picture2" src="https://github.com/user-attachments/assets/7bfb1fa3-35c0-4bea-a5e5-b180c6e9595c" />

---

### Monthly Revenue Trend (2009-2011)

Establishing the baseline for analysis.

<img width="495" height="261" alt="Picture3" src="https://github.com/user-attachments/assets/b64b53c8-e636-4973-b047-f49d11a28de6" />

36.5% growth in November. This graphic is showing us that from August onwards the revenue is growing.

To figure out the reasons for this we consider a few other metrics. Other metrics to be considered are:

### 1. Monthly Growth Rate
<img width="398" height="239" alt="Picture4" src="https://github.com/user-attachments/assets/929ef6bc-d267-40eb-89ae-f256583757f8" />

- High volatility: Monthly growth swings sharply between positive and negative values, indicating an unstable growth pattern rather than steady expansion. This suggests revenue or customer activity is sensitive to short-term factors (promotions, seasonality, market changes).

---

### 2. Monthly Active Customers

In April the monthly active customer numbers were drawn by around 10% here we are able to see a similar kid of trend for the number order numbers as well
<img width="396" height="232" alt="Picture5" src="https://github.com/user-attachments/assets/acb02d83-5932-4a38-8777-f5fd738b2d68" />

---

### 3. Monthly Order Count
<img width="380" height="237" alt="Picture6" src="https://github.com/user-attachments/assets/1480c9da-83a3-41e4-97b1-02b09ab3fbb1" />

Here we have seen that the number of others have gone down. Now as we can see that the active customer count directly is affecting the order count decrease. hence we can check or average revenue for an order as well.

---

### Average Revenue per Order
<img width="284" height="291" alt="Picture7" src="https://github.com/user-attachments/assets/cddb8388-59f1-4d53-a3c6-0d3de0200280" />

---

### New Customer Ratio
<img width="387" height="231" alt="Picture8" src="https://github.com/user-attachments/assets/f1ff2a90-3cc3-46b1-9cf5-421b3ee405fc" />

New Customer ratio is a good way to know if we are losing our already available loyal customers we are not able to gain new customers.

---

### 5. Monthly Retention Rate
<img width="752" height="400" alt="Picture9" src="https://github.com/user-attachments/assets/477098cd-c569-47b1-88be-3bf8b4f8bc38" />

Counting monthly retention rates in order to check how well is our product market fit and how sticky our product is.

Monthly Retention Rate = ( Retained Customers From Previous Month ) / ( Active Customers Total )

We can observe that the Monthly Rate of Retention increased from October to December and went to levels previous levels afterwards

---

## Insights Deep Dive

### 1. The High-Value Customer Discovery (RFM Segmentation)

Using K-Means clustering on Recency, Frequency, and Monetary (RFM) data, we identified three distinct customer personas that require unique handling:

- High Value (The VIPs): High revenue, high frequency, low inactivity.
- Mid Value (The Movable Middle): Moderate revenue, fairly frequent. This segment represents the biggest growth opportunity.
- Low Value (The Drifters): Less active, low/negative revenue.

This segmentation moves the business from a single marketing calendar to three distinct, targeted workflows.
<img width="503" height="253" alt="Picture10" src="https://github.com/user-attachments/assets/4350c883-4fb0-4c20-aad4-cda08cb96a30" />
<img width="500" height="259" alt="Picture11" src="https://github.com/user-attachments/assets/c823a648-3a39-426d-a663-49b24a1d6dd7" />
<img width="520" height="249" alt="Picture12" src="https://github.com/user-attachments/assets/4844d739-4451-4d17-ac48-1222283939d7" />


---

### 2. The 84% Reliability Factor (LTV Prediction)

Lifetime Value = ( Total Gross Revenue ) - ( Total Cost )

We developed a machine learning model to predict Customer Lifetime Value (LTV).

- Methodology: Used 3 months of historical data to predict the subsequent 6 months of value.
- Performance: The model achieved 84% accuracy.
- Business Impact: This allows the finance and marketing teams to forecast Q3 and Q4 revenue with high confidence based solely on Q1 and Q2 behavior, enabling better inventory planning and cash flow management.

<img width="500" height="255" alt="Picture13" src="https://github.com/user-attachments/assets/e9835de4-ceaf-46dd-bfad-688b04f44e05" />


LTV Correlation

Validating that higher RFM scores accurately predict higher long-term profitability.

---

### 3. The Retention Warning System (Churn Prediction)

Churn is often silent until it is too late. This module uses XGBoost to classify customers as "Likely to Churn" or "Safe".

- Inputs: Recency of last purchase, frequency trends, and deviations from typical buying patterns.
- Application: This generates a daily "At-Risk" list. Marketing can instantly deploy "We Miss You" coupons only to this list, saving margin by not discounting customers who were going to stay anyway.

---

### 4. Timing the Market (Next Purchase Day)

Using XGBoost with hyperparameter tuning, we predicted the specific Next Purchase Day for individual customers.

- The Opportunity: Instead of emailing a customer every day (leading to fatigue/unsubscribes), we can email them 3 days before their predicted purchase date.
- Result: Higher open rates, higher conversion, and lower marketing annoyance.
<img width="489" height="237" alt="Picture14" src="https://github.com/user-attachments/assets/3d66ed79-ab82-4598-bf6b-8d5c8c30c5a9" />

- Model Performance - Actual vs. Predicted Sales demonstrating alignment with market reality.

---

## Strategic Recommendations

### 1. Discount for Those at Risk

Use the Churn Model to find the specific customers who are about to leave. Only send the discount coupons to them. This saves profit margins while still stopping customers from quitting.

---

### 2. Offer the Right Product at the Right Time
 
Use the "Next Purchase Day" predictions. If the data says a customer buys coffee in the first week of the month, send them a coffee email three days before. Don't send them tea offers. Sell them what they need, exactly when they are ready to buy it.

---

### 3. Predictive Stocking: Order Inventory Before It Runs Out

Running out of a popular item loses money. Having too much stock sitting in a warehouse means wasted money.

Connect the Sales Prediction model to the warehouse team. If the model predicts a spike in sales for next month, order the stock now. This ensures you always have products available for customers without hoarding too much inventory.

---

### 4. Separate the Wholesalers from the Shoppers

Create a special "Wholesale Portal" for the big bulk buyers. Give them bulk pricing and a personal sales rep. Keep the regular website simple for the everyday shoppers.

---

### 5. The VIP Lane

Treat your top "High Value" customers like VIPs. Give them priority shipping (ship their orders first) and early access to new products. 


---

### 2. The Upsell Campaign

The "Mid Value" segment is active but not maximizing their wallet share.

- Action: Implement a dynamic bundling strategy. If they usually buy Item A, offer "Item A + Item B" for a 15% discount.
- Goal: Increase Average Order Value (AOV) of this segment to migrate them into the High Value cluster.

---

## Key Performance Indicators

### 1. North Star Metric: Monthly Revenue

Formula: Active Customer Count × Order Count × Average Revenue per Order  
Target: Consistent Month-over-Month growth.

### 2. Retention Rate (Product-Market Fit)

Formula: ((End Customers - New Customers) / Start Customers) × 100  
Target: Increase retention rate by 5% to drive 25%+ profitability growth.

### 3. Model Accuracy (LTV)

Current Performance: 84%  
Target: Maintain >80% to ensure marketing spend remains efficient.

---

## Assumptions and Caveats

- Seasonality: The dataset covers Dec 2009 – Dec 2011. Seasonal peaks (Christmas) are present, but long-term trends may require more data to fully stabilize.
- Wholesaler Bias: The dataset includes wholesalers. Their purchasing behavior (high volume, bulk orders) is different from typical B2C customers and may skew the "High Value" cluster averages if not filtered.
- Prediction Window: The LTV model assumes 3 months of history is sufficient to predict 6 months of future value. Drastic changes in market conditions could impact this reliability.
