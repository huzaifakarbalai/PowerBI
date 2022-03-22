# PowerBI

POWER BI ANALYSIS ON PAKISTAN'S LARGEST ECOMMERCE DATA
Link to Data Set: https://www.kaggle.com/zusmani/pakistans-largest-ecommerce-dataset/code

Problem Statement: Analysis of Customer Segments based on completed transactions. 

## Data Transformation
1.	Deleting the completely null 4 columns at the end, itemID, increment id, sales_commission_code
2.	Remove Item ID, Increment ID
3.	Rename columns MV, Category_name_1, working date, Bi status, customer since, sku, qty_ordered
4.	Change data type of customer ID
5.	Trimmed sku, category
6.	Replace cashatdoorstep with cod
7.	Removed 464051 rows with blank values in all columns.
8.	There are a lot of labels for 'status' column. Need to check if any relationship exists between 'status' and 'BI Status' columns

## Observations:
1.	All transactions marked as either 'complete' or 'closed', fall in the 'Net' category for 'BI Status'
2.	All transactions marked as 'received', 'paid', 'cod', 'exchanged' or something related to refund are marked in 'Valid' category
3.	All transactions marked as either 'canceled' or something to do with incomplete transaction are marked in 'Gross' category
4.	#REF!' looks an erroneous label.
5.	164 transactions have blank values and 7850 have ‘\N’ in category column
6.	20 rows have blank values in Sku aka Product_Name column.

## Replacing:

### In Status Column
1.	'complete','closed','received','paid','cod',’2660’,’999’,’2800’, will belong to category 'Completed'
2.	'order_refunded','refund', 'exchange' will belong to category 'Refund'
3.	'pending','payment_review','processing','holded','pending_paypal','\N' will belong to 'Pending'
4.	'canceled' will belong to 'Cancelled'
5.	'fraud' will belong to 'Fraud' Also replace the '#REF!'' entry to 'Net' in 'BI status'

### In BI Status Column
6.	‘#REF!’,’3’,’4’,’5’,’7’,’8’,’ ‘, with Net.

### In Category Column
7.	Blanks and \N with ‘Unknown’

### In Sku Product_Name Column
8.	Blanks with ‘Missing’

### Combining some options for the payment method column to reduce the labels for this column
10.	Easypay_MA, with Easypay
11.	marketingexpense','financesettlement','productcredit', 'internetbanking', 'mygateway', 'mcblite', 'ublcreditcard', 'apg', ‘ 2660’, ‘ 999’, ‘ 2800’, and blanks with Others.

## Customer Segmentation according to Grand_Total(Sales):
- Very Low Sales Segment (Grand_Total<1900)
- Low Sales Segment (Grand_Total>1900 & Grand_Total<5750)
- Medium Sales Segment (Grand_Total>5750 & Grand_Total<23000)
- High Sales Segment (Grand_Total>23000)

## KPI’S: 
1.	Grand_Total
2.	Cumulative Grand_Total according to customer ID(Sales)
3.	Repeating and Non Repeating Customers based on frequency of customer IDs.

## Dimensions:
1.	Customer_Id
2.	Status
3.	Category
4.	Created At
5.	Sales Segments

## Visualizations
1.	Top customers visualization is made to understand the variance of customers present in the data based on their spendings, the visualization is limited to top 10 to identify top customers and categorize them in Gold Category and offer incentives to them.
2.	The second sales segment Pie Chart is made to understand the various segments of customers in the data and how many customers belong to each segment so we can develop and scale strategies for each segment.
3.	The third stacked column chart of customer segments according to sales is to understand which segments give the most revenue and then develop strategies to improve the lower revenue segments.

## Then I have visualized each Customer Segments (Very low, Low, Medium and High) with 3 Visualizations:

1.	First the stacked bar chart of top selling categories of each segment. The purpose is to understand the needs of customers in each segment, then use this to offer more sku’s in the popular categories and develop strategies to improve sales in those categories by offering deals.

2.	Second Purchasing periods/times of each segment. This is done to visualize when did we receive the most sales throughout the time and understand the reasons for sales at that time. Like events or Black Friday deals and this helps us evaluate the performance of each marketing promotions and deals. 

3.	Third the Repeating vs Non Repeating Customers in each segment. This is done to understand the customer churn in each segment and identify opportunities to decrease customer churn/ increase repeating customers in each segment by identifying needs of each segment and offering deals in desired categories.

