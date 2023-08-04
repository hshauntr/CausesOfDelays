# Predicting and Analyzing Causes of Delay for Flight Departures : Project Overview

## Abstract

Paired with a growing population is a demand for travel. In my study, I closely examined airline
departure times by comparing their scheduled and actual departure times. I considered a delay to be any
difference of 15 minutes or more and recorded the cause of the delay. To ensure a fair assessment of each
airline’s performance, I collected data from a single airport every day for 10 years. By applying the
knowledge I acquired in class, I used R to employ linear regression, trained a mathematical model and
optimized it with least squares to create training and testing sets. By utilizing mathematical analysis
through T values, P values, and R-squared values, my results offer valuable insights into airline
performance regarding flight departures. My model can be used to predict future performance and analyze
past data to identify the most common causes of delay in departure statistics. A valuable resource that can
help both airline companies and consumers. This is proven when I practiced my model on departing
flights from Delta Airlines at the San Francisco International Airport from January 2013 until 2023, and
recognized that flight carrier delay and late arriving aircraft were the biggest causes of delays, suggesting
that it is well within an airline’s control to improve their on-time performance.

![](img/delays.jpg)

## Introduction
There is a growing interest in understanding and quantifying flight delays, as evidenced by the
increasing number of studies on this topic. These studies have utilized various statistical methods to
analyze arrival delays at airports and compare the performance of airlines and airports. For example, one
study analyzed ground delays and air holding at Entebbe International Airport over a five-year period and
generated daily probabilities for aircraft departure and arrival delays(Wesonga, Nabugoomu, & Jehopio,
2012). This study established a method for comparing both mean delay and extreme events among
airlines and airports, identifying a power-law decay of large delays. In other words, these studies
examined the factors contributing to flight delays in 2016 using data from the Bureau of Transportation
Statistics. Through reading other reports, I pinpointed that researchers employed machine learning
techniques and statistical models to create a predictive modeling engine capable of identifying delays in
advance. This indicated that various statistical methods were utilized in order to predict future data, and I
found this intriguing. Such research offers valuable insights into the causes of flight delays and serves as
inspiration for further investigation in this area. With this in mind, my team had a solid foundation with a
scope of what I wanted to pursue. I wanted to utilize the knowledge I acquired in class and apply that to
such a relevant issue. Through conducting this literature review, I had the opportunity to recognize that
various reports covered this relevant issue in their own approach. In hopes that I would be able to provide
further insight into the underlying issues behind flight delays, I found myself growing with curiosity on
how I would approach my model.

When coming up with my model, I wanted to examine a growing issue and how it personally
relates to us. So, I decided to focus on travel as we have all experienced the frustration and inconvenience
caused by a flight delay. In recent years, the global population growth has led to an unprecedented demand for air travel for various purposes such as business, leisure, and family. This increase in demand
necessitates the scheduling of more flights, raising concerns about the ability of airline companies to
maintain on-time performance. Flight delays can negatively impact customer loyalty.

Initially, I aimed to model the primary concerns of frequent air travelers by analyzing the air
travel consumer report, which details the most common consumer complaints for each airline company
such as lost luggage, refunds, etc. However, this approach only allowed me to analyze said data as a
whole and identify the most significant factors on a yearly basis. Specifically, I used this approach with
Markov Chains, but weren’t able to define transition matrices that would portray information that would
be valuable as time passes. For example, the probability of a number of complaints for a specific airline
based on a certain amount of time. I instead wanted to be able to have a more detailed approach on a
specific issue so I shifted my focus to one of the leading causes of consumer complaints - flight delays.
That is why I instead set my sights on a mathematical model that would be done through linear regression.
Once I examined closely at the statistics regarding flight delays in recent years, I distinguished that there
was merely a 79.96% statistic of on-time flights for major U.S. carriers in November 2022(Bureau of
Transportation). This data is publicly available information from a government resource, the bureau of
transportation, and this is what certainly propelled my motivation for building my model. My interest was
piqued and I began to get curious about the underlying patterns and trends. Why are flights not departing
on time? What’s the biggest cause and if so, is there a relationship? How could this be
addressed/improved?

As I was consuming information of detailed statistics on departures, I aimed towards
constructing a mathematical model that would offer valuable insights to both airline companies and
consumers on their departure performance. By evaluating performance of airline companies, this indicates
that they would gain the ability to discern the factors that impact their on-time performance. For example,
this would allow a company to be able to justify investing more of their time and resources into
improving specific issues. To improve their evaluation on timeliness on departing flights, if their largest
contributing factor to delayed flights are problems revolving around the crew and scheduling flights, they would know where to focus on. Furthermore, this model’s significance goes hand in hand with customers
as well. If an airline’s performance were to be improved, then customers would have a more confident
choice in being able to choose an airline that has a good performance record. Over time, this would build
customer loyalty and benefit both the company and the consumer.

So in order to address this issue, I decided to examine the overall causes of delays by reporting
operating carriers. By examining data from major U.S. flight carriers, there were a myriad of reasoning
behind each delay. Air carrier delay would be due to circumstances within the airline’s control and this
could be related to maintenance or crew problems, etc. Extreme weather delay is due to significant
weather conditions that in the judgment of the carrier, delays the operation of the flight. National Aviation
System Delay is caused by non-extreme weather conditions, such as airport operations, heavy air traffic
volume, etc. Security delay is caused by security issues such as evacuation situations, security breaches,
long lines at screening areas,etc. Lastly, late arriving aircraft delay which suggests that a previous flight
arrived late, forcing the present flight to depart late. This is why the assumptions for my model will be
that I will be predicting flight departure times, based on these causes of delays as my only predictors for
my model. To make the assumptions for my model more fair, I utilized data on the same airport. By
choosing to only take into account flights that departed from the San Francisco International Airport, for
every day from January 2013 to January 2023, I would be able to determine weather delays as a more fair
assessment. I also chose San Francisco International Airport due to how it has abundant flights departing
everyday, so I could input plenty of data.

Furthermore, in order to predict departure data based on historical flight performance, I wanted
to focus on evaluating an air carrier that performed well in departing flights on-time. This is why I wanted
to concentrate my model around Delta Airlines. Based on the data from the Bureau of Transportation
from 2022, Delta Airlines had one of the highest total records of flights in the U.S. paired with
consistently departing on time, at an impressive rate of 89.91%(Bureau of Transportation). Once my
model is utilized, it would be extremely significant as it would have the ability to accurately assess the
performance of Delta Airlines, predict future performance, and identify the biggest factors that contribute to flight delays. By identifying these factors, I can recognize if Delta Airlines has room for even further
improvement. Hence, my mathematical model holds considerable importance for both the airline and its
customers in improving the flying experience

## Approach to the Mathematical Model

In the realm of predicting flight delays, the primary goal of my mathematical model was to develop a predictive tool that could efficiently capture the underlying patterns in the dataset and establish a clear relationship between the input features and the output (departure delay). The choice of the appropriate mathematical model was crucial to ensure accurate predictions and to gain valuable insights into the factors influencing flight delays. Drawing inspiration from the principles outlined in CSE 176's (Introduction to Machine Learning) Chapter 1, I sought a model that could effectively learn from the available data and make informed predictions about future flight delays.

### Choosing Supervised Learning and Regression Model

After carefully considering the nature of the available data, I opted for a supervised learning approach, as I had access to both input features (predictors) and corresponding output labels (departure delay). Within the realm of supervised learning, there were two fundamental types of models: classification and regression. Classification models are suitable for dealing with qualitative outcomes, while regression models are more appropriate for quantitative predictions based on historical data.

Given that my objective was to predict the departure delay (a quantitative outcome) and explore relationships between input features and the label, I chose a regression model. Regression models allow for the interpretation of the model's coefficients, which would facilitate answering my research questions and achieving my project's objectives.

### Parametric v.s. Non-Parametric Model

Next, I had to decide between a parametric and a non-parametric regression model. A parametric model assumes a specific function form, such as a linear equation, logistic function, or Gaussian distribution, while a non-parametric model is more flexible and does not rely on explicit function forms. In my case, I decided to use a parametric model over a non-parametric one for several reasons.
Firstly, with a parametric model, I could explicitly assume the function form for my regression model, making it easier to interpret and understand the underlying relationships between the input features and departure delays. This interpretability was vital for addressing my research questions effectively.

Secondly, non-parametric models tend to be computationally expensive and memory-intensive, particularly when dealing with high-dimensional datasets. I had concerns about the "Curse of Dimensionality," where data points tend to be sparsely distributed in higher dimensions, reducing their informativeness. To prevent overfitting and ensure sufficient data points for accurate predictions, I decided to avoid the complexities associated with non-parametric models.

### Considering Bias-Variance Tradeoff

The bias-variance tradeoff played a crucial role in selecting the appropriate model complexity. Simple models, with high bias and low variance, tend to underfit the data, while complex models, with low bias and high variance, may overfit and capture noise in the data. Striking the right balance was essential to achieve accurate predictions and generalize well to new data.

After considering this tradeoff, I decided to employ multiple linear regression models. Despite their simplicity, multiple linear regression models could still capture the underlying relationships between input features and departure delays. Moreover, they were robust to random noise, making them suitable for handling real-world datasets with inherent variability.

### Multiple Linear Regression Modell

In developing my mathematical model, I started with a linear-based approach, assuming that the parametric function form was linear. Consequently, I adopted a multiple linear regression model to accommodate multiple input features, representing the linear combination of X and the error term. The mathematical representation of the multiple linear regression model was expressed as:

Y = β₀ + β₁X₁ + β₂X₂ + ... + βᵣXᵣ + ε

Where:

- Y represented the departure delay (the dependent variable).
- X₁, X₂, ..., Xᵣ represented the input features (independent variables).
- β₀, β₁, β₂, ..., βᵣ were the coefficients of the model, representing the impact of each input feature on the departure delay.
- ε represented the error term, accounting for the variability not explained by the model.

### Least Square Method for Coefficient Estimation

To make predictions using the multiple linear regression model, I needed to determine the values of the coefficients (β₀, β₁, β₂, ..., βᵣ). For this purpose, I employed the Least Square Method, a popular technique used to estimate the coefficients in linear regression models.

The Least Square Method aimed to minimize the sum of squared differences between the predicted outcomes (y_hat) and the actual departure delays. The objective function E(X; β) was formulated as follows:

E(X; β) = ∑ (y_hat - Y)²

Here, y_hat represented the predicted departure delay based on the multiple linear regression model.

By minimizing the error function, I could find the set of coefficients (β₀, β₁, β₂, ..., βᵣ) that yielded the best-fitted line to the data. These optimized coefficients would ensure that the model's predictions were as close as possible to the actual departure delays.

### Uniqueness of Optimizer and Convexity

In this context, the optimization process sought to find the values of coefficients that minimized the error function. While it was essential to ensure that the model was performing at its best, it was equally important to determine whether this minimum point was a global minimum or a local minimum.

From MATH 140's (Mathematical Optimization) lecture notes, I learned that if the objective function (E(X; β) in this case) was a convex function, then the optimizer (the set of coefficients β) was the global minimizer. In the case of a convex function, there was only one unique set of coefficients (β₀, β₁, β₂, ..., βᵣ) that provided a unique solution to the optimization problem.

In the context of my multiple linear regression model, the error function E(X; β) was indeed a quadratic function, making it convex and ensuring the uniqueness of the optimizer. This property was crucial in guaranteeing a robust and reliable solution for predicting departure delays.

### Overview on Approach

In conclusion, my approach to the mathematical model focused on using a supervised learning method, specifically multiple linear regression, to predict flight delays. The choice of a parametric model allowed for interpretability and computational efficiency, while the Least Square Method provided a way to estimate the coefficients and optimize the model's predictions. The convexity of the error function ensured the uniqueness of the solution, giving me confidence in the accuracy and reliability of my predictions.

By employing this approach, I aimed to create a powerful tool for predicting flight delays accurately and gaining valuable insights into the factors influencing departure times. The model's ability to approximate the data with high performance would pave the way for informed decision-making and improved efficiency in the aviation industry.

## Analysis & Results

Before commencing the analysis, it is essential to reiterate the underlying assumption of the study: the aim is to predict the accuracy of flight departure times solely using the listed delays as predictors. The hypothesis postulates that all predictors are significant in the model, which will be tested in the subsequent analysis.

The analysis was conducted using the R programming language, wherein 80% of the data was allocated to training the model, while 20% was reserved for testing. The selection of an 80/20 split was to strike a balance between overfitting and underfitting the model, ensuring generalization to new data.

Figure 5 presents a graph of the model's predictions using all the predictors. The subsequent summary of the linear model (Figure 6) showcases the departure delay as the outcome variable, and the five types of delays as predictor variables.

![Figure 5](img/figure5.png)




# Complete R Markdown Documentation & Code used to create Report in .pdf 
[View Here](https://github.com/hshauntr/CausesOfDelays/blob/main/R%20Markdown%20PDF.pdf)
