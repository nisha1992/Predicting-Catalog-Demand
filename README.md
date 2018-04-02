# Predicting-Catalog-Demand
Project 1.2 : The company sent out its first print catalog last year and now its planning to send again print catalog to new 250 customers from their mailing list. Determine how much profit can company expect to earn from this. Management does not want to send the catalog out to these new customers unless the expected profit contribution exceeds $10,000. So the task is to predict the estimated profit if catalog is sent to new customers.
- Details
- The costs of printing and distributing is $6.50 per catalog.
- The average gross margin (price - cost) on all products sold through the catalog is 50%.
- Make sure to multiply your revenue by the gross margin first before you subtract out the $6.50 cost when calculating your profit.

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
Avg_Sales – ZIP (Not linear)Write a short report with your recommendations outlining your reasons why the company should go with your recommendations to your manager.

