# Predicting Seasonal Flu and Novel Pandemic Vaccinations

As COVID-19 continues to wreak havoc on the world, it is becoming more and more important to target our vaccination efforts so that they result in the most possible vaccinations within the population. Ideally, with progressing medical technology and better aimed public health efforts, we can slow future pandemics and better deal with endemic viruses.

With the following data I was able to generate a machine learning model with good accuracy and an impressive roc_auc score of 0.8658. This means it could have a large impact on public health efforts, vaccination campaigns and medicince in general with only a few survery questions.


## I. Data

The data came from entering a contest listed on [DrivenData.org](https://www.drivendata.org/competitions/66/flu-shot-learning/page/210/). The data was in the form of survey answers from roughly 28,000 respondents. The survey consisted of 35 questions: 13 yes/no questions about behaviors, health and demographics, 8 opinion questions rated 0-5 and 14 demographic questions with categorical answers. There were also labels included for half of the respondents that indicated whether or not they were vaccinated for seasonal flu or H1N1 swine flu. Using these labels we were able to train a model to predict the probability of vaccination for each of the flus.


## II. Data Cleaning

The data was relatively clean but for missing information, the mode of each column was used to input new data. This was the case for all but 3 features, which were missing close to half of the data. For these 3, an additional category, "unknown" was created so that they could still be useful without making too bold of assumptions.


## III. EDA

Exploratory data analysis was relatively unremarkable. Very few strong correlations seen between data features and target variables or between data features themselves. Many of the stonger correlations seen were not surprising in their nature either.


## IV. Machine Learning

All models tested were relatively similar but GradientBoostingClassifier had the highest scores on the various metrics used to compare performances. This model was used for contest as it had the highest roc_auc_score and this was the metric used for the contest. CPU time was not a consideration here, otherwise a LogisticRegression model would have been better, giving only slightly less accurate results in a much faster fashion.


## V. Future Improvements

If this were to actually be implemented by health officials, it would likely be more useful to eliminate certain survey questions, while using a simpler/faster ML model. This would result in faster data gathering as well as much faster prediction results. For example, if we were to use a random forest classifier, we could eliminate close to 50 columns in the final dataframe, use the exact same model for both predictions and make predictions faster at the cost of only a small amount accuracy lost.