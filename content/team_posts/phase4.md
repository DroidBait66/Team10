---
title: "Project - Phase IV"
date: 2025-06-12
draft: false
description: "FinalPost"
slug: "phase4post"
tags: ["project", "Setup"]
authors:
    - "alpberrak"
    - "elianne_mejia"
    - "JessicaPoblete"
    - "mahika_modi"
showAuthorsBadges: true
---

# Project Updates
As a result of our phase 3 feedback we have made some updates to our app. To start we changed the way we check assumptions for our logistic regression model (shown below). We also connected the lawyer user to the refugee user. We added a user profile page on the refugee screen so that the user can see their application status and if a lawyer has accepted their case. Then on the lawyer screen we added a see pro bono opportunities page, where the lawyer can see all user applications and accept applications, and in turn it changes the refugee profile page to update their status/lawyer assigned. We also connected the lawyer to the commissioner. There is now a request funding page on the lawyers screen where they can request funding to the commissioner, and a view pending funding page on the commissioner page where the commissioner can accept or reject the funding and it updates the lawyers funding application page. We also fixed the asylum acceptance probability page to round the percentages and create a heat map to display the data. Overall we added more visualizations and completed the pages for the lawyer and commissioner.


# ML Models

## Supervised Model: Logistic Regression
Our first ML model is a logistic regression model that uses the data from our Eurostat API. This model predicts the acceptance rate of an asylum given the country of origin, sex, age of the asylum, as well as the geo (country to). After the user input their demographics the model returns a value between 0 and 1 that corresponds with a country (geo), and then gets converted into a percentage for easy evaluation. In order to train our model we used gradient descent while adjusting the alpha and max iterations of our model until we got the highest R^2 possible. In our case we were able to get an R^2 of 0.65 which although isn't the best, is slightly explained because our data was aggregated.

The following plots check the assumptions for the logistic regression model. The histogram proves the assumption of normality since the data follows a normal distribution around 0 and stays between -1 and 1. The residual plot versus index proves no autocorrelation since the residuals maintain the same/similar throughout all indexes of the data. The log-odds scatter plot proves the assumption for linearity of log-odds. The graph shows a linear trend between the log-odds and acceptance rates. Since the model passes these assumptions the model takes every assumption into account. 

![Histogram](/updatedHistogram.png)
![Residual_vs_index](/Residual_vs_index.png)
![LogOddsScatter](/LogOdds.png)

To implement this model into our app we stored a weights table and we called sql to get the weights and column names (country names). We then used the column names to create a dataframe with the columns as the country names. Then we called our predict_acceptance function and passed in the users age, sex, citizenship, geo(country to), the dataframe with the country names, and the weights. This then calculated the probability of acceptance for each country, and we displayed the 3 countries with the top predicted acceptances. Finally we created a heat map of Europe with the predicted acceptances for all the countries.

## Supervised Model: Time Series Regression

# Software Architecture

OpenPort is implemented using a three tiered architecture. We utilizied Streamlit to develop the front end UI which is connected to our backend REST API. The REST API pulls data from our database that has been implemented in MySQL. 

# Database Model
In order to establish a connection between the Lawyer and Refugee persona, we have added an IsActive attribute to the LegalAidApplication table. This is set to false when a lawyer assigns themselves to a refugee's case. We added the FundApp table to establish a connection between the Lawyer and Commissioner personas. Lawyers submit applications for funding to assist with cases which are then accepted or denied by commissioners. We also generated mock data for all of our tables using Mockaroo. We deleted several tables that did not end up getting used for our final web app implementation: ProBonoOpportunity and Spending. 