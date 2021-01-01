# Project-Programming
Repository for Programming Project 2020

## Problem Statement
For this project you must create a data set by simulating a real-world phenomenon of your choosing. You may pick any phenomenon you wish – you might pick one that is
of interest to you in your personal or professional life. Then, rather than collect data related to the phenomenon, you should model and synthesise such data using Python.
We suggest you use the numpy.random package for this purpose.

Specifically, in this project you should:
• Choose a real-world phenomenon that can be measured and for which you could collect at least one-hundred data points across at least four different variables.
• Investigate the types of variables involved, their likely distributions, and their relationships with each other.
• Synthesise/simulate a data set as closely matching their properties as possible.
• Detail your research and implement the simulation in a Jupyter notebook – the data set itself can simply be displayed in an output cell within the notebook.

## Solution

### Description
I chose a phenomenon which is very current at the moment and has been in the forefront of the news over the last few days with the introduction of the third lockdown for the beginning of January - the Pandemic Unemployment Payment or the PUP as i will refer to it from now on. A dataset of one hundred data points and eight different variables was created. The variables are:
- Employees name
- Gender, Gender of the person
- Age, Age of the person
- Tenure, the number of years the person has been employed by the company
- Job Sector, Job sector in which the person is employed
- Province, Province in which the individual works
- PUP Amount, Weekly amount the person receives in the Pandemic Unemployment Payment
- Days, the number of days in which the person was in receipt of the PUP.

There are three categorical variables (Gender, Job_sector, Province) and four numerical variables (Age, Tenure, PUP Amount, Days receiving payment) of which age and tenure are continuous.

### Research

The UC Irvine [1] and Vincent Arel Bundocks [2] datasets were analysed as part of the process to identify a suitable subject matter to conduct the project on. There are a wide range of datasets in the repositories of varying sizes and data. It was very interesting to view some of the diverse range of topics that were analysed. There were a number of ideas i considered for the project but in the end i decided to base the project about the pandemic Unemployment Payment having seen a dataset in the Vincent Arel Bundocks reporitory about German Unemployment rates.

I consulted [7] and [12] to understand how to manufacture or synthesis fake data to populate variables such as age and tenure which was not available in any of the Government publications relating to the payment. [12] went throught the various distribution used to generate the random data required. I identified which distribution would be the most appropriate to populate both variables from these publications.

There are many recent publications on the Covid 19 pandemic, the lockdown measures introduced to combat its spread and the social welfare payments which were introduced by the Government to provide relief to employees. These payments were necessary as many sectors of the economy were forced to close forcing thousands into temporary unemployment. The Citizens Information [4] website contains useful information on the rules of the payment, who is eligible, four weekly payment rates and how to cancel when returning to work. The Central Statistics Office and the Gov.ie [5] websites contain valuable information on chnages to the payment since March and the various stages of the payment and more imnportantly statistics on the participation of employees in the PUP and demographic breakdown of applicants. Based on this data in the appendix of [8] i was able to populate the Gender, Province, PUP Amount and Job Sector variables of the dataset. From the job sector variable i populated the Days receiving PUP variable as the different job sectors returned to work and came off the payment on a particular date when the lockdown measures were eased for some parts of the economy. There was no data relating to the remaining two variables (age, tenure). Data for these two variables was synthised/modelled using numpy.random functions to populate the variables in the dataset.

The uniform distribution was used to populate the age variable of the 100 records. The uniform distribution is very useful in the generation of random numbers as the probability of each number been selected is equal. The function was used between the start parameter of 18 and the end parameter of 66 as payment is applicable to people between these ages. The resulting data was used to populate the age variable. 

The tenure variable was populated using the exponential distribution. Most employees would stay in a job for a short period of time before changing to another company in particular younger employees whereas there would be less employees stay in a the same job for a longer period of time. The exponential distribution would be a good measure of this phenomenon as it concerned with the amount of time that a certain event occurs. In the exponential distribution there are fewer larger values and many smaller values [9] which fits nicely with the distribution required to populate tenure. The output from the exponential distributiuon function was used as the data for the tenure variable.

### Code

Uniform distribution code to populate the age variable in the dataset:

-import libraries
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

-use random.uniform distribution to get the age values. 18 and 66 are the lower and upper parameters and size is set to 100 
x = sns.displot(np.random.uniform(18, 66, size = 100))

-add title and x label to chart
plt.title("Uniform distribution of age")
plt.xlabel("Age")
-show plot
plt.show();

Exponential distribution code to populate the tenure variable in the dataset:

-import libraries
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

-set n equal to the number of records
n = 100

-seaborn distplot of exponential distribution
x=sns.distplot(random.exponential(5, size = n))

-Add title and x label to plot
plt.title("Exponential distribution of tenure")
plt.xlabel("Tenure")
print(x);


### References
[1]-UCI: Machine Learning Repository; https://archive.ics.uci.edu/ml/datasets.php
[2]-Vincent Arel Bundock: Available datasets; https://vincentarelbundock.github.io/Rdatasets/articles/data.html
[3]-wikihow: How to Create a CSV File; https://www.wikihow.com/Create-a-CSV-File
[4]-Citizens Information: COVID-19 Pandemic Unemployment Payment; https://www.citizensinformation.ie/en/social_welfare/social_welfare_payments/unemployed_people/covid19_pandemic_unemployment_payment.html#
[5]- Gov.ie: COVID-19 Pandemic Unemployment Payment Rates until April 2021; https://www.gov.ie/en/publication/0b0fc-covid-19-pandemic-unemployment-payment-rates-from-17-september-2020/
[6]-365DataScience: Examples of Numerical and Categorical Variables; https://365datascience.com/numerical-categorical-data/
[7]-Alteryx.com: Synthesizing Fake Data for Fun and Profit; https://community.alteryx.com/t5/Data-Science/Synthesizing-Fake-Data-for-Fun-and-Profit/ba-p/427345
[8]-gov.ie: COVID-19 Pandemic Unemployment Payment; https://www.gov.ie/en/press-release/34be6-update-on-payments-awarded-for-covid-19-pandemic-unemployment-payment-and-enhanced-illness-benefit/
[9]-LibreTexts: The Exponential Distribution; https://stats.libretexts.org/Bookshelves/Introductory_Statistics/Book%3A_Introductory_Statistics_(OpenStax)/05%3A_Continuous_Random_Variables/5.04%3A_The_Exponential_Distribution#:~:text=For%20example%2C%20the%20amount%20of%20time%20%28beginning%20now%29,of%20time%2C%20in%20months%2C%20a%20car%20battery%20lasts.
[10]-stackoverflow: How do I change the figure size for a seaborn plot?; https://stackoverflow.com/questions/31594549/how-do-i-change-the-figure-size-for-a-seaborn-plot
[11]-pythoncharts: Rotating Axis Labels in Matplotlib; https://www.pythoncharts.com/2019/05/17/rotating-axis-labels/
[12]-Stack Abuse: Generating synthetic data with Numpy and Scikit-Learn; https://stackabuse.com/generating-synthetic-data-with-numpy-and-scikit-learn/
