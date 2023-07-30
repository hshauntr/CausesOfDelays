# Predicting and Analyzing Causes of Delay for Flight Departures : Project Overview

## Introduction

### Literature Review
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

### Motivation
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
contributing factor to delayed flights are problems revolving around the crew and scheduling flights, they
would know where to focus on. Furthermore, this model’s significance goes hand in hand with customers
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
performance of Delta Airlines, predict future performance, and identify the biggest factors that contribute
to flight delays. By identifying these factors, I can recognize if Delta Airlines has room for even further
improvement. Hence, my mathematical model holds considerable importance for both the airline and its
customers in improving the flying experience.


## Methods

### Approach to the Mathematical Model
When I decided which types of mathematical model to apply, I expected that the model could
capture the pattern of the dataset and explain the relationship between input and output. Moreover,
according to the note from CSE 176 (Introduction to Machine Learning) chapter 1, such a mathematical
model needed the data to predict outcome and somehow gain knowledge. In other words, the model was a
compressed version of the dataset and I could extract insight on flight delay while approximating the data
with high performance (Carreira-Perpiñán, 2019, pg.1). Machine learning models would be adequate to be
my choice of model as I had enough data for the model to make inference about flight delay. Machine
learning models could be broken into supervised, unsupervised and semi-supervised learning models,
where it required both inputs and labels data, only required input data and it required both input data and
labels data for some data point, respectively. I was feeding my both input and label data into the model
with all the data points; therefore, I chose supervised learning methods. Supervised learning models were
further broken down into classification and regression models, where the differences between were on the
label/outcome and the purpose of the models. Classification models were used to separate data points into
different categories and outcome were qualitative while regression models are used to make predictions
based on historical data and outcome are quantitative. The objective of my project was to use the
supervised model to make predictions in the future time and answer my second research question - to
make inference about the biggest cause and possible relationships between input and label, based on my
given historical data. In addition, the label “Departure Delay” was quantitative data, and I was confident
that choosing a regression model could answer my research question. There were two more considerations
to choose a specific regression model. One was whether the method should be parametric or
non-parametric and another one was complexity of the model according to the bias-variance tradeoff. For
the parametric/non-parametric models, according to note from on CSE 176 (Introduction to Machine
Learning) chapter 8, parametric model had explicit function form such as Gaussian distribution, logistic
function or linear function whereas non-parametric model did not (Carreira-Perpiñán, 2019, pg. 31). I
decided to use a parametric model over another because I wanted to have assumed the function form for
my regression model. Choosing a parametric model came with several advantages on the complexity and
dataset itself. As I had an explicit function form for my model, it would be easier to interpret my model to
address my research questions and achieve my objectives. Contrary to the non-parametric model, as it was
assumed to accept any function types, the training was purely based on the dataset itself. The training
process became more computationally expensive. According to slides from MATH 180 (Modern Applied
Statistics) lecture 3, non-parametric model suffered from the problem of “Curse of Dimensionality”,
which referred to the fact that the data points tended to stay far away from each other in higher
dimensions, which the data points tended to be less informative (Rube, 2022). I needed much more data
just to make the data points to be concentrated and prevent overfitting, which increased the memory
space. However, according to CSE 176 chapter 8 note, non-parametric models would out-perform
parametric models by being capable of learning complex/nonlinear relationships between input and output
data (Carreira-Perpiñán, 2019, pg. 32). This disadvantage of the parametric model led me to consider the
effect of bias-variance tradeoff. Based on the MATH 180 lecture, simple models tended to have high bias
and underfit but it was robust to random noise, whereas flexible models could capture nonlinearity but
easy to overfitting, which they included the random noise during the training and tended to have high
variance (Rube, 2022). Regarding this consideration, I decided to apply multiple linear regression models.
However, the thought process behind choosing this specific model would be addressed in the next part as
it’s more relevant to be mentioned.

### Multiple Linear Regression Model
MATH 150 (Mathematical Modeling) lecture slides 22 introduced a general regression model
which is polynomial based. However, I started off with a regression model which is linear based. In other
words, I assumed that the parametric function form is linear. Therefore, I had a multiple linear regression
model as my assume was that the input had more than one feature, which was the linear combination of
𝑋 and . The formula for both multiple polynomial and linear regression models was demonstrated in
𝑛
β
𝑛
Figure 1. I wanted to start off with the simplest regression model to see if this model was enough to
explain the relationship between predictors and response variables. If the model was not enough to predict
well about the dataset, I would start to consider a more flexible model such as a polynomial regression
model.





## Conclusion
