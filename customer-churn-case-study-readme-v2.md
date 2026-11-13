# Customer Churn Case Study.

1) Created two Measures.

The data we are dealing fictitious telecom service data named as Databel

Created two measures initially

1) *Number of customers = Count ( Customer ID )*

2) *Number of Unique Customers = Distinct Count ( Databel-data [Customer ID] )*

Compared both and created Card Visual according to requirement.

---

**Churn Rate is the factor why customer leave.**

Created a measure known as Number of Churned Customers by using Churn Label column.

*Number of churned customers =*  
*= Sumx( Dataleb-Data, if ( Databel-Data [Churn-label] = "Yes" , 1, 0))*

Based on the Number of customers and Number of churned Customers Calculated a measure called Churn Rate.

*Churn Rate = Divide ( Number of Churned customers , Number of customers)*

**Churn Rate = 26.86%**

---

Taken a visual bar chart to see the churn reasons

x - axis :- Number of customers  
y - axis :- Churn Reason

Made a change in visualization such that highest percentage of comes first like customers with more Churn Reasons comes at the top.

Created a map visual such that Location is taken from the state colum and Gives Churn Rate and did conditional formating and identified the state with highest Churn Rate.

**Identified CA => California with churn Rate as 63%.**

---

## Performed Analysis

Used DAX command if to and nested if and categorized the column measures into one column know as Demographics (add column)

*Demographics =*  
*= if ( databel-data [Senior] = "Yes", "Senior", if ( Databel-Data [Under 30] = "Yes" , "Under 30", "Other" )*

**Identified Seniors churn more then Others and Under 30 churn less compared to Seniors and then Others.**

**Churn Rates**  
**Seniors = 38.46%**  
**Others = 24.54%**  
**Under 30 = 23.00%**

Created a column chart with this Data as visual.

x axis :- Demographics  
y axis :- Churn Rate

---

Used Create Group to create bins for Age column where I specified

field : 'Age'  
Group type : bin  
Bin type : Size of bins  
Min value : 15  
Max value : 85  
Bin Size : 5

Created Line and Clustered Column Chart ( Combo chart )

X - axis :- Age(bins)  
Column y axis :- Number of customers  
Line y axis :- Churn Rate

---

## Inspecting groups

Monthly charges to currency.  
Created stacked column chart with line

Used formula

*Average ( Databel - Data [Monthly charges] )*

x - axis :- Number of customers  
Column y axis :- Average Monthly charges  
Line y axis :- Churn Rate  
Column Legend :- Group.

Created a Line and Stacked Column Chart

**Line & Stacked Column chart :- columns & line**  
**Line & Clustered Column chart : more bins .**

**Group Size : 6 have Lowest Churn Rate.**

---

There are different Contract types  
One Year, Two Year, Month to Month

One Year "Yearly"  
Two Year "Yearly"  
Month to Month "Monthly"

Created a Switch DAX for understanding the and categorizing the contract types

*= Switch ( Databel-Data [Contract Type],*  
*"One Year" , "Yearly"*  
*"Two Years" , "Yearly"*  
*"Month to Month" , "Monthly" )*

Used Clustered Column Chart for Categorizing Yearly & Monthly Contract types with category Gender & Churn Rate as in y axis.

x axis :- Contract Category  
y axis :- Churn Rate  
Legend :- Gender.

**Identified churn rates for two categories Monthly and Yearly**

**Churn Rate**  
**Monthly :- 46.29%**  
**Yearly :- 6.62%**

**Found that Yearly Churn Rate is significantly lower than monthly Churn Rate which indicates Monthly costs are higher and people prefer to churn out more than Yearly**

So action that need to be taken is promotions or discount should be given monthly subscribers or convert them into yearly subscribers to by promoting offers.

---

## Unlimited Data Plan

Created a column known as Grouped Consumption

*= If ( Databel - Data ' [Average Monthly GB Download] < 5 , "Less than 5 GB" ,*  
*If ( Databel - Data [Average Monthly GB Download] < 10 , "Between 5 and 10 GB",*  
*"10 or more GB" ))*

Added these to clustered column chart

Y axis - Grouped Consumption  
X axis - Churn Rate  
Legend - Unlimited Data Plan.

**It is identified less than 5GB plan who churn out more also with Unlimited Data plan and 5GB plan less than 5GB who don't have unlimited Data Plan churn out less compared to all Data plans.**

---

## International active customers

Taken map visual with location as state and Bubble Size as Churn Rate applied filter Intl Active Yes and International plan Yes No

**and identified churn rate as 72% which is in California which highest among all states.**

**The Churn Rate decrease with account Length (in months)**

Also made a line chart with Churn Rate Account length (in months) and Contract Type.

**Also identified number of customers with direct debit are more than Credit Card & Check**

# 1) Dashboard building - Overview Dashboard

Created a Dashboard with Card visuals  
1. Churn Rate  
2. Number of Customers  
3. Churned customers

Also added to the Dashboard bar chart with

Y axis :- Churn Rate Reason  
X axis :- Grand total % of Customers in a Group.

Also added to dashboard Churn Category along with Churn Label count Yes -> percentage of people who churned out in each category with pie chart.

**Count of Customers with Contract Type and identified Monthly to Month have more customers followed by Two Year Contract type followed by One Year Contract type.** Add this to overview dashboard.

**Identified through Month to Month Contract type churn rate percentage in California state is 79%** also added to the dashboard as a map visual.

---

## 2) Key finding About Dashboard Named as Age Group

Line and column clustered chart is taken with Age Group Bins along with slicer Account length. Also added Number of customers in a Group, along with Churn Rate, Average Monthly Charge, and Column legend group.

In this dashboard we can find out Customer churn for the customer group who are of particular Age group & slice along with the Account length.

**for Example :- Churn rate for customer who are not in group plan that belongs to age group of 50 and who have account length of 12 month or less is 50.67%**

---

## 3) Payment and Contract Dashboard

Created two measures known as

*Average Customer Service Call = Sum([Customer Service Calls]) / total num of customers*

In same dashboard created Contract type and Account length and turn it into a Scatter plot. Created a measure Average Account length for it.

Added a slicer to filter contract Category - those are Monthly & Yearly  
added another slicer for payment method field which acts as dual level slicer for -> Credit Card, Debit Direct and paper check payment methods for both Yearly and monthly.

The Dashboard is used for average number of customer service calls for customers who are on a monthly Contract (Contract Category) and pay by direct debit (payment method) and also it displays churn rate for those customers.

---

## 4) Extra Charge Dashboard

Created two measures called Average Extra International Charges and Average Extra Data Charges

Created a card visuals for the both charges.  
Also added Churn Rate by Grouped Consumption and Unlimited Data plan visual

This Dashboard is used for average extra data charge for the customers who are not on a unlimited data plan and consumed 10 or more gigabytes (Data Consumption)

---

## State Insight Dashboard

Card Visuals  
1) Customer Service Calls  
2) Average Extra International Charges  
3) Average Customer Service Calls  
4) Average Extra Data Charges

Taken a line Chart for representing Churn Label (Yes or No) and the Churn Rate as lines in the visuals

Took map visual did conditional formating using rule with custom colors

**The dashboard tells which state wise highest churn rate & yet lower sum of customer service calls and number of customer service calls**


