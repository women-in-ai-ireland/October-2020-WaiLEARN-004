WAI-LEARN-Online-Retail-DS
==============================

Cohort Analysis and customer segmentation 



Online Retail Data Project
WAI Learn | April 2021

# Introduction:
Nowadays e-commerce companies are becoming more and more popular, the pandemic of Covid-19 just proved how organizations need to move online to keep their business alive. 
The internet makes shopping easy, fast, and handy for customers that have the convenience to choose among a ton of stores without leaving the sofa, however, such amazing freedom brings a huge challenge to companies to be more innovative in order to attract new customers and keep the old customers engaged. Hence, it is safe to say that a company’s capability to enlarge its number of clients has a significant relationship to its growth of sales. Nevertheless, just expanding the customer base is not enough since it would not meet its ability to drive sales. Furthermore, it's crucial to understand customer's behavior in order to make actionable decisions and support your business to grow, keep, and acquire the right consumers.

# Getting Started:
In this project, we are going to use a UCI data set (Taken from Kaggle [1]) that contains sales transactions of an online retail store based in the UK occurring between December 2010 and December 2011, the customer base of the company is mainly wholesale retailers. 
First, we are going to have a look at the data and see if we will need to perform any transformation in the data set as well as to get some insights from our customer base.


#####  Insights
- The data set contains 8 columns and 541,909 rows.
- The variables CustomerId and Description are the ones with the highest number of missing values.
- Around 75% of the products cost  4.13 pounds or less and the most expensive product cost 38,970 pounds.

### Data Cleaning

As we can see above the variable CustomerID need to be converted into character and the missing values needs to be handled, for this project we are going to drop all the rows which contain missing values, but bear in mind that you might need to solve them in another way depending on the purpose and impact of your project.
 
<img width="416" alt="Screenshot 2021-05-09 at 12 19 13" src="https://user-images.githubusercontent.com/38282927/117570076-c62d5080-b0c0-11eb-9042-01f7fc901e7c.png">
<img width="227" alt="Screenshot 2021-05-09 at 12 19 59" src="https://user-images.githubusercontent.com/38282927/117570112-e0ffc500-b0c0-11eb-915e-5186f1559dc7.png">


### Data Exploration

<img width="499" alt="Screenshot 2021-05-09 at 12 17 52" src="https://user-images.githubusercontent.com/38282927/117570062-aac24580-b0c0-11eb-8d01-0707b603e6d0.png">


<img width="421" alt="Screenshot 2021-05-09 at 12 31 54" src="https://user-images.githubusercontent.com/38282927/117570559-8b2c1c80-b0c2-11eb-8727-cfe8775473a8.png">

<img width="710" alt="Screenshot 2021-05-09 at 12 28 48" src="https://user-images.githubusercontent.com/38282927/117570467-1d7ff080-b0c2-11eb-9e5d-e2fe5b553929.png">

Top 10 Countries with the Highest Volume of Purchases:

<img width="538" alt="Screenshot 2021-05-09 at 12 32 49" src="https://user-images.githubusercontent.com/38282927/117570608-b3b41680-b0c2-11eb-8bed-4d010d8c7fd3.png">

##### Insights
- We can observe that sales have been increased at the end of the year, this can be explained by the holiday season, where the demand for gift products is higher due to Christmas.
-  World War 2 gliders are the most sold product.
- The majority of the purchases are made in the UK, which makes sense since the product supplies reach faster and products’ deliveries are reliable within the same region.


# Cohort Analysis: 
A cohort can be defined as a group of people that have similar characteristics.
Cohort analysis is a behavioral analysis where you group your customers based on their similarities to better understand their activities. Cohort analysis enables businesses to reduce churn and improve revenue by asking more precise questions and making data-driven decisions.
For the purpose of this project we are looking to answer the following questions:
- Who are the customers engaging with the store throughout the year and who isn’t?
- When do they churn? Can we identify/predict it?
- What are the actions we can take to minimize customers chun?

For cohort analysis, we are going to add 3 extra columns to the dataset: (see [2] for more details)
- Invoice Month: A representation of the month and year of the transaction
- Cohort Month: A month and year of a customer’s first purchase. This will be the same across all invoices for a particular customer.
- Cohort Index: A representation of a customer's stage in its “lifetime”. This number describes how many months have passed since their first purchase.

<img width="1004" alt="Screenshot 2021-05-09 at 12 47 28" src="https://user-images.githubusercontent.com/38282927/117571028-b879ca00-b0c4-11eb-816c-4c6ffdda5201.png">



This will enable us to build a retention table that will answer our initial questions and help us to understand how customers are throughout the year.

<img width="835" alt="Screenshot 2021-05-09 at 12 48 02" src="https://user-images.githubusercontent.com/38282927/117571054-ccbdc700-b0c4-11eb-8183-149d19b34262.png">
<img width="629" alt="Screenshot 2021-05-09 at 12 49 22" src="https://user-images.githubusercontent.com/38282927/117571100-fe369280-b0c4-11eb-8223-8e3fcb16dbd5.png">


As we can see above this store is having some issues keeping their customers, on the next steps we will look at some techniques to help companies to identify valuable customers and take actions to prevent churn.

# Customer segmentation using RFM (Recency, Frequency, Monetary) analysis.

##  What is FRM?
RFM model combines three different customer attributes to rank customers: Recency, Frequency, Monetary. It can be used for behavioral segmentation, grouping the customers based on their previous purchase.

Behavioral segmentation helps managers to identify valuable customers who are more profitable for the business. For example, which customers are buying expensive products but only one time and which are buying more frequently. Based on these findings, managers can decide which marketing campaign will be more effective for each group of customers.

In this dataset, we noticed that most of the customers are located in the UK, therefore, we decide only segmen UK customers.

<img width="681" alt="Screenshot 2021-05-09 at 12 52 58" src="https://user-images.githubusercontent.com/38282927/117571222-83ba4280-b0c5-11eb-8a82-c47139f8c2cd.png">                                                                                                                                                                                                                                           
##### Columns required 
We only needed 5 columns for this analysis; CustomerID, InvoiceDate, InvoiceNo, Quantity, and UnitPrice described as:

- CustomerId: is needed to uniquely define the customer, 
- InvoiceDate: helped to calculate recency of purchase,
- InvoiceNo: we could count the number of time transaction were performed(frequency), 
- Quantity: purchased in each transaction 
- UnitPrice: of each unit purchased by the customer helped us to calculate the total purchased amount.

#####  RFM Analysis 
We have used the following definitions in order to calculate recency, Frequency, and  Monetary values for each customer.
Recency — Calculate the number of days between the current date and date of last purchase each customer
Frequency —Calculate the number of transactions made over a given period for each customer
Monetary — Calculate the sum of money spent over a given period of time for each customer

<img width="329" alt="Screenshot 2021-05-09 at 12 55 16" src="https://user-images.githubusercontent.com/38282927/117571284-d0058280-b0c5-11eb-82a9-efc8f205b75e.png">


#####  Apply RFM Scores:
Once we have RFM values from the purchase history, we assign a score from one to four to recency, frequency, and monetary values individually for each customer, this rank can be used to segment the customers into different groups. For this analysis, we used Quintiles as a method of ranking the RFM values on a scale of 1 to 4. 


<img width="583" alt="Screenshot 2021-05-09 at 12 55 47" src="https://user-images.githubusercontent.com/38282927/117571293-e27fbc00-b0c5-11eb-85e9-0639e0c7701b.png">


Customers with the lowest recency, highest frequency and monetary amounts considered as top customers.

<img width="635" alt="Screenshot 2021-05-09 at 12 56 01" src="https://user-images.githubusercontent.com/38282927/117571303-ea3f6080-b0c5-11eb-9f73-f1331a23eb3e.png">


These scores are then used as inputs for clustering algorithms in order to group customers.








## Business recommendation:
Here are some suggestions for business managers based on the RFM score and some possible actions they might take into account:




<img width="656" alt="Screenshot 2021-05-09 at 12 57 10" src="https://user-images.githubusercontent.com/38282927/117571341-135ff100-b0c6-11eb-8492-caf9080dc80c.png">

# Refrences:

[1] Data: https://www.kaggle.com/jihyeseo/online-retail-data-set-from-uci-ml-repo

[2] Notebooks: https://www.kaggle.com/mahmoudelfahl/cohort-analysis-customer-segmentation-with-rfm

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
