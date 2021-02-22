# Customer Segmentation and Customer Churn Analysis
## Small Business | Tax Office Insights

** Author: Miguel Santana**
* Blog post: [Medium](https://msantana269.medium.com/clustering-customer-churn-time-series-b51c9f59d691)

## Abstract

Through data exploration and analysis of clientele data over a three-year period, recommendations for business development are provided below. The three sections of our analysis are provided in the following notebooks: [Data_Cleaning.ipynb](/notebooks/Data_Cleaning.ipynb), [Clustering.ipynb](/notebooks/Clustering.ipynb) and [Customer_Churn.ipynb](/notebooks/Customer_Churn.ipynb). The most significant loss for the office occurs in clients between the ages of 25 and 35 coming from single income households. Our analysis outlines strategies for targeted marketing and customer retention. 

The contents of this repository detail the analysis of a tax office’s client base for targeted marketing and customer retention. Three years of tax data were provided for customer analysis. 

### Business problem:
A small tax office is looking to understand their client base and prepare for the upcoming tax season. Small businesses depend on face-to-face interactions in order to build long lasting relationships with their customer base. COVID-19 has taken a toll on businesses nationwide and the tax office is looking to prepare for the upcoming year by understanding customer retention and leveraging targeted marketing. 

## Executive Dashboard
![graph1](/images/Dashboard.png)
**Data Overview**

The dashboard is available via [google data studio.](https://datastudio.google.com/reporting/20efa577-3f3f-448c-a11b-0ccbba069500)

## Framework
![graph2](/images/OSEMN.png)
**The OSEMN Framework was used to analyze the data**

## Data Cleaning

**Choices**

* The project was focused on E-Filing customers per the owner’s request. E-Filing customers are denoted by complete demographic information and an E-File transmission date. Clients missing values in the mentioned categories were dropped as they represented invalid tax returns. 
* Merging tax year files 2016, 2017 and 2018.
* Filling demographic information from year to year to accurately represent each unique client over a three year period. 
* After processing, dropping clients with null values present in demographic information (Family Size, Tax Payer Age, Residential Zip Code).
* Updating preparer codes with names (provided by the owner).
**Lastly, differentiating customers who left, stayed, came back and were new.**

The methodology is provided below:

• 1) Customer Lost | 2016 - 2017 - (n/a)

• 2) Return Customer | 2016 - (n/a) - 2018

• 3) Customer Retained | 2016 - 2017 - 2018

• 4) Customer Retained | (n/a) - 2017 - 2018

• 5) Customer Lost | (n/a) - 2017 - (n/a)

• 6) New Customer | (n/a) - (n/a) - 2018

## Exploratory Data Analysis | New vs Return Customers

**Adjusted Gross Income**
![graph3](/images/newreturnincome.png)

**Age**
![graph4](/images/newreturnage.png)

**Household Income, Family Size**
![graph5](/images/newreturnhousefamsize.png)

## Modeling

### Clustering | 3 Cluster Segmentation

**Selecting & Visualizing Number of Clusters**
![graph6](/images/elbow.png)
![graph7](/images/clusters.png)

**Visualizing Clusters Numerically**
![graph8](/images/clustervals.png)

### Customer Churn Analysis | Sklearn, Tensorflow, Pycaret

**Sklearn | Gradient Boosting Classifier**

![graph9](/images/sklearnresults.png)

**Tenserflow | Neural Network - Summary & Results**

![graph10](/images/neuralnetsummary.png)

![graph11](/images/neuralnetresults.png)

**Pycaret Multi-Model Analysis**

![graph12](/images/modelcompare.png)

### Final Gradient Boosting Classifier Results**

![graph13](/images/ROCAUC.png)

![graph14](/images/confusion.png)

## Interpret Results

**Feature Importance**

![graph15](/images/featureimportance.png)

**SHAP Assessment**

![graph16](/images/shap.png)

## Results

The top features influencing customer churn are Federal Tax Owed, Paid, Last AG-Income, Age, Last Day (Wednesday & Thursday), Last Month (March & April) and Preparer.

**Federal Tax Owed, Adjusted Gross Income and Family Size**
![graph17](/images/taxAGIfamsize.png)

**Federal Tax Owed: The most significant customer churn occurs in customers that owe the federal government between 0-2000 dollars as a result of their tax preparation.**

**Adjusted Gross Income & Family Size: The most significant customer churn occurs in customers that have an adjusted gross income of 0-20,000 dollars. Family size is being observed because the number of dependents a family has directly influences adjusted gross income through additional tax breaks (more tax free income, lowering the adjusted gross income value directly).**

* Note: Dependent tax break values vary from year to year but a value 5,000 dollars per dependent child is an appropriate estimate. This leads me to include the 20,000-30,000 adjusted gross income bin as 'significant churn'.

**Age, Month and Day**
![graph18](/images/agedaymonth.png)

**Age: The most significant customer churn occurs in customers that are between 20 and 30 years of age.**

**Last Time in Office | Day & Month: The highest traffic days are Monday, Tuesday and Friday. The most significant customer churn occurs on Wednesday and Thursday. The highest customer traffic occurs in February. The most significant customer churn occurs during March.**

**Amount Paid for Service**
![graph19](/images/paid.png)

**Paid: The most significant customer churn occurs when customers pay between 100-150 dollars for services.**

### Conclusions | Clustering (Customer Segmentation)

The dataset offered various consumer trends and illustrated multiple areas of opportunity. Please see our jupyter notebook 'Clustering.ipynb' for additional analysis.

Three Clusters

The three segment group offered additional insight into customer trends. Cluster (1) represented the highest customer churn with client features that include:

* Smaller family sizes, mid-range age
* Male and female, single income households
* Preparation completed by only preparers
* Mid-range tax and (AGI) income
* Pays slightly lower than the fees listed
* Processed mid-week, typically in late February

This demographic is should be highly represented when creating any targeted marketing campaigns in the new year. 

### Conclusions | Customer Churn

* Customers that owe the government between 0 and 1000 dollars as a result of their tax preparation represent the most significant customer churn with respect to tax owed.
* Customers that file with an adjusted gross income (taxable income) of 0-30,000 dollars represent the most significant churn with respect to AGI. Note: family size has a direct impact on taxable income.
* The most significant customer churn occurs in clients between the ages of 20 and 30.
* Of clients who leave the office, the majority of them have their last transaction during the month of February. Ratio-wise the month of March illustrates the most significant customer loss with approximately 38 percent customer churn.
* Customer churn is closely distributed across every day of the week with the exception of Sunday. Sunday illustrates no customer churn but reveals a dramatic decrease in the number of transactions completed.
* Customers that pay between 100 and 150 dollars for services represent the most significant customer churn with respect to fees paid for services.

# Business Recommendations

**Recommendation 1** 

The tax office needs to target younger consumers, specifically those that are between 20-30 years old and live in single income households. To help build rapport with the younger demographic, the Tax office should begin offering financial wellness checks to those that are interested. A simple check of finances, plans for retirement and other provided resources can go along way when looking to build trust with a client base.

**Recommendation 2**

In addition, the office should invest in video conferencing software such as Zoom, GoToMeeting or Google Meet in order to offer alternative methods of tax preparation to their client base and offer a user friendly approach to their younger demographic.

**Recommendation 3**

The office should attempt to redistribute its client flow with an emphasis on clients that do business in March. The customer segmentation analysis illustrated customer churn occurring in clients that are mid-range age and live in single income households. This leads me to believe that the younger, single income dependent demographic is electing to physically wait in the office for services and are processed by the first preparer available as opposed to having an administrative representative complete the return and scheduling a follow up call with a seasoned preparer after review. This process currently exists in the office but is not practiced on this demographic and is reserved for high profile clients who choose to not spend hours waiting in the office. Implementing this practice on the younger demographic should yield positive results as these individuals may be impatient or frustrated from taking significant time away from work for this transaction.

**Recommendation 4**

Sundays should be leveraged to redistribute a significant portion of the tax season traffic. Whether its an outreach program to redistribute clients or a day set for only video conferencing based preparations, Sunday should be leveraged to implement the first two recommendations above.


**Recommendation 5**

Lastly, the office should reclassify its fees. The most amount of churn occurs at paid values of 100-150 dollars and from conversations held with the owner, this range is held for returns that are more complicated than a standard return but not complicated enough to merit higher prices which are reserved for returns with specific qualities (businesses, multiple state, large investments, estate preparations, etc). Breaking out this general (not simple) category into preparations that hold specific qualities and pricing based on these updates may give the owner some clarity on what merits a higher price and what doesn't. Transparency with the client may help them understand why they are paying a certain fee and a breakdown may offer opportunities for price discounts in some of these returns that are classified as not simple but are not complicated, yielding lower individual prices for many of the clients that fall into this category.

## Limitations

Unfortunately, the tax office maintains poor record keeping practices and as a result potentially significant features were unusable. An example of this was the occupation feature which maintained an enormous number of unique features as a result of misspelling, mislabeling or simply not including the information. In addition, this analysis was limited by the missing 2020 tax year returns which were not provided.

## Future Work

Future work should include a more comprehensive amount of data per client. This data is normally provided by clients but was not provided by the owner due to the sensitivity of the information. Examples include, number of jobs worked, a breakdown of earnings further than adjusted gross income (taxable wages, earnings on investments, etc.), as well as a health care status (having vs. not having). There are a significant number of public resources that the office can provide their clients in order to build rapport and earn new business through referrals. This can even lead to additional income as Medicare (health insurance for those over 65) is a profitable endeavor with peak months occurring from October - December (during the offices slowest months).

### Further Information
Please review the narrative of our in the following jupyter notebooks: [Data Cleaning](/notebooks/Data_Cleaning.ipynb), [Clustering](/notebooks/Clustering.ipynb), [Customer Churn](/notebooks/Customer_Churn.ipynb) or review our [presentation](./presentation.pdf)

For any additional questions, please reach out via email at santana2.miguel@gmail.com, on [LinkedIn](https://www.linkedin.com/in/miguel-angel-santana-ii-mba-51467276/) or on [Twitter.](https://twitter.com/msantana_ds)

##### Repository Structure:

```

├── README.md               <- The top-level README for reviewers of this project.
├── notebooks     <- narrative documentation of analysis in jupyter notebooks
├── presentation.pdf        <- pdf version of project presentation

```

