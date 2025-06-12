---
title: "Project - Phase III"
date: 2025-06-05
draft: false
description: "Our Idea"
slug: "phase3post"
tags: ["project", "Setup"]
authors:
    - "alpberrak"
    - "elianne_mejia"
    - "JessicaPoblete"
    - "mahika_modi"
showAuthorsBadges: true
---
# Project Updates
As a result of feedback we recieved during our mock presentation, we have decided to change our Diplomat persona to a European Commissioner persona since we want this persona not be tied to a specific country but rather be able to allocate EU funding towards member countries based on how much money they already spend on social programs and the amount of refugees they are acceptin. 
# Data Models 
We stored data from the API along with the weight vectors for our logsitic regression ML model into two new tables, AverageAcceptanceRates and Weights. In addition to this, we populated our EducationLevel and Education tables with some mock data for all of the countries in our Country table. As of now, each country in our database associated values for each education level: primary, secondary, and tertiary. We also changed some of the attribute names for our other tables so that they make more sense according to the values they represent. For example, LegalAidApplication previously had a UserID attribute which was a foreign key referencing an ApplicantID for an entry in the AsylumSeeker table. We changed this to also be called ApplicationID so it's easier to understand what this value represents. 

# Routes 
<iframe 
  src="https://docs.google.com/spreadsheets/d/e/2PACX-1vT6aAyMz747kqhiRaR1dB4uw8S8n5M3bPqAU4DttqdiKApRwsWaEuF8rghtzfgw84GzTnQ64HPGJPcf/pubhtml?widget=true&amp;headers=false"
  width="1000" 
  height="600">
</iframe>

# Web App Pages
## Refugee Persona
### Acceptance Probability Screen
![AcceptanceProbScreen](/acceptance_prob_screen.png)
This screen uses the route that calls the logistic regression model. Here, refugees can see their predicted acceptance probability for their top three countries. 
![LegalAidApplication](/legal_aid_app_screen.png)
This screen shows where refugees can apply for legal aid. Their application gets addded to our database which lawyers will be able to see on their dashboard (this will be implemented in the future)

## EU Commissioner Persona 
![ProjectSubmission](/aid_top.png)
![ProjectSubmission2](/aid_bot.png)
This screen shows where EU commissioners can submit suggestions for new humanitarian aid projects. 

![LowAcceptanceRateViaPop](/lowaccptrate.png)
This screen shows EU commissioners which countries are accepting the most and the least refugees proportional to their population.

# Machine Learning Models 

## Logistic Regression Model

For our logistic regression model we used the geo (country to), age, sex, and citizenship as the features. We picked these features because if we were to remove one or more of these features the model would have less data to work off of. In our case we had the users input the age, sex, and citizenship, and then gave them 3 options of countries to pick from.

![Predicted vs actual](/predvsactual.png)


This model shows the actual vs predicted acceptance rates using the logistic regression model. Using the plot it shows that the logistic regression model is accurately working for the majority of the data. For example as the actual acceptance rate increases, so does the predicted acceptance rate. Yet there is some data that isn’t correctly being read causing the plot to have segments of data that doesn’t fit the positive linear trend. The correlation of the model is around 0.645 which is above average, while it could still be improved the model still provides accurate information for the most time.

## Time Series Forecasting 

Our second machine learning model is our time series forecasting model. Our dataset includes the EU countries and the percentage of their GDP that goes towards social spending from 2011-2022. Our model forecasts out 5 years into the future, so we included 5 lag columns in our X matrix. We also had a COVID column to account for increased social spending during COVID years. This machine learning model will be primarily used my the EU Commissioner persona to be able to allocate funds strategically since the model will show them how much countries will spend on social programs in future years. The proof-of-concept model is fully finished, but we still need to cross validate and implement it into the actual app. As seen by the plots below, the time series model performs fairly well.

![Actual vs Predicted Scatterplot](/actual_vs_predicted.png)
This scatter plot shows how close the model's predictions are to the actual values. Since most of the points fall pretty close to the diagonal line, it means the model is doing a good job predicting. There's a clear upward trend, which tells us the model has captured the general pattern in the data really well.
![Histogram of Residuals ](/histogram_of_residuals.png)
This histogram shows the residuals which are basically how far off each prediction was from the actual value. The shape is pretty centered around zero and looks kind of like a bell curve, which is what we want. It means the errors are spread out evenly and there’s no major bias in the model’s predictions. There is an outlier on the far left that we explore in the future, but besides that the bars indicate a normal distribution. 

