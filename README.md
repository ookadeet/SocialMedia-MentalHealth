# Social Media and Mental Health

## Executive Summary

This project seeks to explore if time spent online per day and number of social media platforms in use can predict outcomes on measures of ADHD, anxiety, depression, and self-esteem. Data was sourced from Kaggle, with data cleaning and analysis done via linear regression in Python. The analysis found that total number of social media platforms used was not a significant predictor of outcomes for ADHD, anxiety, depression, or self-esteem, while hours spent online was. When run against test data however, the predictive power of the model was limited. If repeated, other known influencers of mental health should be explored alongside hours spent online so the full extent of the role of social media can be assessed. Limitations should be noted, as the questions used to assess outcomes do not come from diagnostic tools so their efficacy in assessing ADHD, anxiety, depression, or self-esteem cannot be confirmed.

## Introduction
Social media often feels like a mainstay of life today, with 59.4% of the population actively engaging with it in some way (*The Changing World of Digital In 2023*, 2023). Social media use has seen increase from 1 hour 37  minutes in 2013 to 2 hours and 31 minutes in 2022 (*The Changing World of Digital In 2023*, 2023), while experience of a mental health condition has seen a 13% increase over the same timeframe (WHO, 2023). This has led some researchers to explore whether the two are connected, with varying results.

One literature review found social media offered the opportunity to build and maintain relationships for individuals who may struggle to do so face-to-face due to serious mental health conditions and, in that sense, acts as a protective factor against the known negative impacts of loneliness and isolation (Naslund *et al.*, 2020). Conversely, increased social media usage is linked to reduced face-to-face interaction, which is a behaviour often indicative of addiction (Kuss and Griffiths, 2011). This has led some to question the ethics of companies utilising psychological techniques and adaptive algorithms to essentially make social media addictive so as to fuel the attention economy (Bhargava and Velasquez, 2021).

This project uses a publicly available dataset to explore what impacts, if any, social media use has on several mental health, and ADHD, measures. It also looks at whether social media usage can be used to predict mental health outcomes, both in terms of platforms used and time spent online.

## Methodology
Raw data was sourced from Kaggle (<a href="https://www.kaggle.com/datasets/souvikahmed071/social-media-and-mental-health?select=smmh.csv">source</a>). The data was collected via a survey asking about social media use and experience of ADHD, anxiety, depression, and self-esteem. These questions were rated on a five-point Likert scale (Joshi *et al.*, 2015) to quantify symptom severity. Analysis was done via linear regression, using hours spent online and total platforms in use as predictors of scores on ADHD, depression, anxiety, and self-esteem measures. Cleaning, exploration, and analysis of the data was done via Python in Colab, and the full code including reasoning for decisions made can be accessed <a href="https://github.com/ookadeet/SocialMedia-MentalHealth/blob/main/Social_Media_%26_Mental_Health.ipynb">here</a>. 

## Exploratory Data Analysis
### Respondent Make-Up
#### Age
80% of respondents are between 15 and 30 years old.

<img align="center" src="img/Age.png" height=300>

#### Gender
Most respondents identify as female.

<img align="center" src="img/Gender.png" height=300>

#### Occupation
72% of respondents are students, either in University or School.

<img align="center" src="img/Work2.png" height=300>

### Social Media Use
#### Hours Online
40% of respondents spend between 2-4 hours online a day. Most respondents use between 3 and 5 platforms regularly.

<img align="center" src="img/Hours Online2.png" height=300><img align="center" src="img/No of Platforms.png" height=300>

#### Platforms Used
YouTube and Facebook are sites most often in use, with Instagram a close third.

<img align="center" src="img/Platforms.png" height=300>

### Mental Health Outcomes
#### Anxiety and Depression
Responses showed a normal distribution for both anxiety and depression, with depression skewing more severe and anxiety less so. Please note, both were measured on a five-point scale (as was ADHD) with a response of 1 meaning no symptoms experienced, and 5 meaning symptoms experienced often. As there were three questions about depression and two for anxiety, an average rather than a total scored was used for both to make comparison easier.

<img align="center" src="img/Anx and Dep2.png" height=300>

#### ADHD
Answers are normally distributed, though skew towards the more severe responses (anything over 10 in this case).

<img align="center" src="img/ADHD2.png" height=300>

#### Self-esteem
Self-esteem was scored differently with a score of three meaning no impact to self-esteem, one meaning very negative impact, and 5 meaning very positive. Respondents tend to skew negative here.

<img align="center" src="img/Self Esteem2.png" height=300>

## Hypotheses

For each of the dependent variables (scores on ADHD, anxiety, depression, and self-esteem measures), hypotheses were as follows:

**H1** - Scores are influenced by time spent online and/or number of platforms used.

**H0** - Scores are not influenced by either time spent online or number of platforms used.

## Results

For ADHD, anxiety, depression, and self-esteem, no significant influence of total number of platforms used was found as p-values for each exceeded the 0.05 tolerance. Hours online was found to have a significant influence. The regression analysis was re-run for each using only hours spent online and retained significance. Analysis outputs are detailed below, including R-square, Mean Absolute Error, Mean Square Error, and Root Mean Square Error:

| Measure | p-Value | Intercept | Coefficient | R2 | MAE | MSE | RMSE |
| :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: | :-------------: |
| ADHD | <0.01 | 9.86 | 1.09 | 20.39% | 2.84 | 12.73 | 3.57 |
| Anxiety | <0.01 | 4.28 | 0.55 | 22.49% | 1.65 | 3.79 | 1.95 |
| Depression | <0.01 | 7.46 | 0.65 | 13.05% | 2.59 | 10.03 | 3.17 |
| Self-esteem | 0.01 | 7.40 | 0.21 | 6.74% | 1.97 | 6.22 | 2.49 |

The null hypothesis (H0) can be rejected for ADHD, anxiety, depression, and self-esteem.

## Conclusion

While hours online were found to be a significant predictor of ADHD, anxiety, depression, and self-esteem, the low R-squared figure for each (especially depression and self-esteem) indicates it does not explain much of the variance in scores. High MAE, MSE, and RMSE for ADHD, depression and self-esteem indicate little predictive power of hours spent online on scores. Anxiety shows a slightly more accurate output, though the low R2 figure implies that hours online alone is not a good predictor of scores. Other variables known to impact mental health should be explored alongside, such as sleep quality, drug and alcohol use, and family history of mental health issues (Mayo Clinic, 2018; 2022) so the full extent of the influence of social media on mental health can be assessed. 

### Limitations

The <a href="https://github.com/ookadeet/SocialMedia-MentalHealth/blob/main/Questions.csv">questions</a> used to assess ADHD, anxiety, depression, and self-esteem were created by the author of the dataset and often specifically called out the use of social media as a contributing factor which could be seen to lead respondents to a particular response. The use of peer-reviewed diagnostic tools such as the Adult ADHD Self-Report Scale V1.1 (ASRS; Kessler *et al.*, 2005), the Anxiety Symptoms Questionnaire (ASQ, Baker *et al.*, 2019), the Beck Depression Inventory (BDI-II, Beck *et al.*, 1996), and the Rosenberg Self-Esteem Scale (RSES, Rosenberg, 1965) would result in more accurate measures of each and removes the risk of leading questions.

## References
