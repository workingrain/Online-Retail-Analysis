# Online Retail Insights using Multiple Linear Regression and Clustering Analysis on Retail Dataset

## Statement of the Problem and Hypothesis
The core objective of this analysis is to determine whether a multiple linear regression model can accurately predict customer purchasing behavior in an online retail environment. This is essential for businesses seeking to optimize marketing strategies and improve customer satisfaction by identifying key drivers behind purchasing behavior. 
The research question is: Can a multiple linear regression model be constructed based on the retail dataset?
To test this, the following hypotheses were formulated:
    Null Hypothesis (H₀): There are no significant factors influencing customer purchasing behavior in an online retail environment, and any observed patterns are due to random variation. 
    Alternate Hypothesis (Hₐ): There are significant factors, such as customer demographics, purchase frequency, and transaction value, that influence customer purchasing behavior in an online retail environment with an Adjusted R-squared value of >0.65.
The outcome of this research seeks to quantify the relationships between customer attributes and total purchase values. This analysis aims to provide actionable insights for businesses in optimizing customer segmentation and marketing strategies. 

## Data Analysis Process
The data for this analysis is sourced from the Online Retail II dataset, which contains over 1 million rows and eight columns, including variables like InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, and Country (Chen, 2019). To prepare the data for analysis, several preprocessing steps were followed: 
	Data Cleaning: Rows with missing CustomerID were removed, as imputing these values could introduce inaccuracies. Duplicated and canceled orders were filtered out. 
	Feature Engineering: A new column, Total_purchase, was computed by multiplying UnitPrice and Quantity to represent the total value of each transaction. This was done to create a more comprehensive measure of customer spending. Date-related features, such as day of the week and month, were extracted and one-hot encoded for modeling purposes, as these features can potentially influence customer purchasing behavior. 
	Outlier Detection: Outliers were identified using the interquartile range (IQR) rule and IsolationForest model, ensuring that the dataset was free from extreme values that could skew the analysis. 
	Transformation and Scaling: Variables were log-transformed to address skewness in the data. However, even after the transformation, the Shapiro-Wilk test indicated that the data did not follow a normal distribution. 

## Outline of the Findings
### Multiple Linear Regression
The regression model aimed to explain the variance in TotalPurchase using various customer and transaction attributes. The analysis yielded an Adjusted R-squared of 0.167. This means the model explains 16.7% of the variance in customer purchases. This result suggests that the independent variables used in the model do not account for most of the factors driving purchasing behavior. The p-value of 0.00 indicates that the model is statistically significant, but its predictive power is limited.
Using the coefficients from the OLS output, this is the MLR equation formed:
total_purchase =2.0021+0.5577(price)-0.5255(is_UK)+0.2040(Monday)+0.2390(Tuesday)+0.2279(Wednesday)+0.2493(Thursday)+0.2662(Friday)+0.8543(Saturday)-0.0386(Sunday)-0.0610(January)-0.0700(February)- 0.0808(March)-0.0464(April)-0.0286(May)-0.0866(July)-0,0231(August)-0.1063(October)-0.2065(November)-0.1708(December) 
	Intercept (2.0021): This is the baseline value for total purchases when all other variables are 0.
	Price (0.5577): For every unit increase in price, total purchase increases by 0.5577 units, holding all other factors constant. 
	Is_UK (-0.5255): If the customer is from the UK, total purchases decrease by 0.5255 units, all else being equal. 
	Days of the week: These coefficients show how total purchases change relative to a baseline day. For example, Friday increases total purchases by 0.2662 units compared to the baseline. 
	Months: Similar to days of the week, these coefficients show how purchases vary by month relative to the omitted baseline month.
### Cluster Analysis
	Cluster count (out of 10,000)	Median for total_purchase	Mean for price	Proportion of customers who live in the UK
Cluster 0	3807	0.713623	-0.514771 	0.865511
Cluster 1	3131	0.712062	1.215699	0.912476
Cluster 2	3062	-1.183804 		-0.562995	0.979559
The clustering analysis identified three distinct customer segments.
	Cluster 0: Customers in this group have the highest total purchases but tend to buy lower-priced items. This segment likely consists of frequency buyers who prioritize cost-effective purchases
	Cluster 1: These customers have high total purchases and tend to buy higher-priced items. This group is a valuable segment for premium offerings. 
	Cluster 2: Customers in this segment make low total purchases and buy lower-priced items. They represent infrequent buyers who may need targeted promotions to increase engagement. 

## Limitations of the Techniques and Tools Used
While Python’s power libraries were leveraged for data handling, visualization, and modeling, there are some inherent limitations in the techniques used:
	Multiple Linear Regression: This technique assumes linear relationships between variables, which may not fully capture the complexity of customer behavior. Furthermore, the failure to achieve normality, despite applying log transformations, indicates that a linear model may not be the most appropriate tool for this dataset. 
	Cluster Analysis: While the clustering technique was helpful in segmenting customers, the complexity of interpreting clusters in large datasets can be a challenge. The choice of variables and the clustering algorithm also influence the results. 
	Data Limitations: The dataset lacks detailed demographic information such as age, income, and gender. This limits the ability to analyze how these factors influence purchasing behavior. Additionally, the data only covers two years, making capturing long-term trends or seasonal variations challenging. 

## Summary of Proposed Actions
Based on the analysis, the following actions are recommended to enhance business strategy:
Segment-Specific Marketing
Leverage the insights from the cluster analysis to develop a targeted marketing campaign. 
	Cluster 0: (high total purchase, low-priced items), focus on loyalty programs and bulk-purchase promotions to encourage frequent buyers
	Cluster 1: (high total purchase, high-priced items), offer exclusive deals and personalized recommendations to retain high-value customers
	Cluster 2: (low total purchase, low-priced items), engage these customers with promotions and discounts to boost their spending and encourage repeat purchases
Data Enhancement
Future studies should aim to include additional variables that can better explain customer behavior, such as seasonal trends, product returns, and more detailed demographic information. Collecting customer preferences, purchase frequency, and recency data would also provide a more comprehensive understanding of purchasing behavior.
Advanced Modeling
Given the limitations of the linear regression model, exploring non-linear models, such as Random Forests or neural networks, could improve predictive accuracy by capturing complex relationships between variables. Time series analysis could also investigate the role of seasonality and other time-based factors in purchasing behavior.

## Expected Benefits of the Study
The key benefits of this study are:
### Improved Customer Segmentation: 
The cluster analysis provides a precise segmentation of customers based on their purchasing behavior. This allows businesses to tailor marketing strategies to different customer segments. This is expected to lead to improved customer retention and higher conversion rates. 
	Cluster 0: This group represents 38.07% of the customer base with the most consistent purchasing behavior. Given their large size, increasing their purchasing frequency by even 10% could have a meaningful impact on overall revenue.
	Cluster 1: This cluster comprises 31.31% of high-value buyers who prefer premium products. Since this cluster shows a higher mean price of 1.22, retaining 5-10% more of this segment could lead to a noticeable increase in revenue as they tend to buy higher-priced items. 
	Cluster 2: This group represents 30.62% of buyers that can be engaged with cost-effective promotions. Even increasing their purchase activity by a small margin of 5-10% can still yield meaningful gains, given the size of this group.
	Increased Revenue: Businesses can maximize revenue opportunities by focusing on targeted promotions for each customer segment. For example, loyalty programs and bulk purchase incentives for Cluster 0 customers are expected to increase their purchase frequency, while exclusive offers for Cluster 1 customers will help retain high-value buyers. 
### Better Resource Allocation:
Understanding customer behavior through segmentation enables more efficient resource allocation, such as focusing marketing efforts on high-value segments (Cluster 1) while using cost-effective strategies to engage low-value segments (Cluster 2). 
### Enhanced Predictive Capabilities: 
While the current regression model has limited predictive power, future improvements could enhance its accuracy. This enables businesses to predict purchasing behavior better and optimize inventory management and customer engagement strategies. 
 
Sources
Chen, D. (2019). Online Retail II. UCI Machine Learning Repository. https://doi.org/10.24432/C5CG6D. 
