# Predicting-Catalog-Demand
Project 1.2 : The company sent out its first print catalog last year and now its planning to send again print catalog to new 250 customers from their mailing list. Determine how much profit can company expect to earn from this. Management does not want to send the catalog out to these new customers unless the expected profit contribution exceeds $10,000. So the task is to predict the estimated profit if catalog is sent to new customers.
- Details
- The costs of printing and distributing is $6.50 per catalog.
- The average gross margin (price - cost) on all products sold through the catalog is 50%.
- Make sure to multiply your revenue by the gross margin first before you subtract out the $6.50 cost when calculating your profit.
- Write a short report with your recommendations outlining your reasons why the company should go with your recommendations to your manager.

# Project 1: Predicting Catalog Demand
# Step 1: Business and Data Understanding
# Key Decisions:
1.	What decisions needs to be made?
* Predicting the estimated profit if a catalog was sent to new customers and then on the basis of profit, decide whether the catalog should be sent or not?
 
2.	What data is needed to inform those decisions?
-	Data about the sales occurred last year when company sent out its first print catalog. (Given)
-	Probability that a new customer will buy a catalog and purchase items? (Given)
-	Information about current customers, shopping behavior, location etc. (Given)
-	Profit Margin (Given 50%)
-	Cost structure (Cost for catalog is given)
- Since, we have the past data about sales, we can predict the sales for current year. And then multiplying the sales by probability that a new customer will respond to a catalog and make a purchase (Score_Yes), we get the sales for current year.
On the basis of which profit can be calculated and then a decision could be taken if the catalog should be sent or not.

 
# Step 2: Analysis, Modeling, and Validation
Important: Use the p1-customers.xlsx to train your linear model.
 
1.	How and why did you select the predictor variables (see supplementary text) in your model? You must explain how your continuous predictor variables you’ve chosen have a linear relationship with the target variable. Please refer to this lesson to help you explore your data and use scatterplots to search for linear relationships. You must include scatterplots in your answer.
In the given variables, only few variables seem to be a good fit to predict the average sales for the current year. Some variables are not significant like Name, Customer_Id, Address, State (Same for all) etc. Why these variables are not a good fit ?
- Name : Since sales doesn’t depend on a user’s name.
- Customer_Id : Customer id is a unique id assigned to a customer. It doesn’t change avg sales.
- Address : Its too detailed, instead of it we can use other variables like city or zip

- Analyzed the scatterplot between numerical predictors and target variable.
Avg_Sales – ZIP (Not linear)

![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/AvgSalesZip.PNG)

-	Avg_Sales – Store_No (Not linear)
![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/AvgSales_StoreNo.PNG)

-	Avg_Sales – Avg_Number_Of_Products_Sold (Not so strong Linear relationship)
![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/AvgSales_AvgNoProd_Pur.PNG)

-	Avg_Sales - #_Of_Years_As_Customer (Not Linear)
![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/AvgSales_NoOfYear.PNG)

- Out of the linear variables, only Avg_Number_Of_Products_Sold seems linearly related with target variable.
- Used “Avg_Number_Of_Products_Sold”, “Customer_Segment” and “City” to build linear model. As per the model created “City” was not significant at all, so removed city and again created a model using only two predictors.

- On the basis of p-values, “Avg_Number_Of_Products_Sold”, “Customer_Segment”, both are significant.

2.	Explain why you believe your linear model is a good model. You must justify your reasoning using the statistical results that your regression model created. For each variable you selected, please justify how each variable is a good fit for your model by using the p-values and R-squared values that your model produced.
![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/LinearModel.PNG)

-	For both the predictor variables, we used in our linear model creation, p-value (probability that the coefficient is going to be 0) is very less. Hence, both the predictors are significant in deciding the target variable.
-	This model is strong since the R-value is very high (0.8366)
- R Square equals 1- SSE/SST
- SSE – sum of squares of residuals (actual value – predicted value) using Predictive Model
- SST – sum of squares of residuals (actual value – predicted value) using Baseline Model

- SSE is always less than SST, hence R Square value lies in range 0-1. Higher the R Square means : SSE is very very small (Predicted values are very close to actual values) which leads to smaller (SSE/SST), hence higher R Square.

3.	What is the best linear regression equation based on the available data? Each coefficient should have no more than 2 digits after the decimal (ex: 1.28)
Avg_Sales = 303 – 149.36*Loyalty_Club_Only + 281.84*Loyalty_Club_And_Credit_Card – 245.42*Store_Mailing_List + 0*Credit_Card_Only + 66.98*Avg_Number_Products_Purchased

# Step 3: Presentation/Visualization
Use your model results to provide a recommendation. (500 word limit)
 
At the minimum, answer these questions:
 
1.	What is your recommendation? Should the company send the catalog to these 250 customers?
Yes, Company should send the catalog to these customers. Since the condition was that if the profit exceeds $10000, and it actually exceeds as calculated using linear regression model, hence catalog should be sent.
 
2.	How did you come up with your recommendation? (Please explain your process so reviewers can give you feedback on your process)
-	Calculated Avg_Sales using linear regression model.
Score_Yes : Probability that a customer will respond to catalog and make a purchase
-	Created a new column (Avg_Probable_Sales = Avg_Sales * Score_Yes)
Given profit margin is 50%, and cost for each catalog is $6.50, hence for all 250 customers
-	Calculated the profit = Avg_Probable_Sales*0.5-(6.50*250)


 
3.	What is the expected profit from the new catalog (assuming the catalog is sent to these 250 customers)?
-	Profit equals $21987.43

# Alteryx Flow
![alt_text](https://github.com/nisha1992/Predicting-Catalog-Demand/blob/master/PredictCatalogDemandAlteryxFlow.PNG)





