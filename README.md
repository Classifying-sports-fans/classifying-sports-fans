# classifying-sports-fans

A repository of code for the Erdos Institute's May 2024 Data Science Bootcamp

## **Project Title: Classifying Sports Fans**
Members: Mariah Warner, Deepisha Solanki, Rudy Perkins, Ryan Moruzzi, Sujoy Upadhyay, and Jacob Kepes
Project Mentor: Mohammad Noorandisoot

## Background 
#### Research Questions/Problem: 
Based on self-described fandom alone, some groups may represent an untapped market that is currently overlooked. Can we, therefore, better predict different fan activities by considering self-reported fandom and various demographic variables? The goal is to identify and anticipate the populations engaging in these activities to develop more targeted marketing strategies.

#### Stakeholders:
Streaming Services (Hulu, Roku, Amazon, etc.), TV Networks (Fox, ABC/ESPN), Gambling Companies (DraftKings, FanDuel, Fanatics), Sports Teams, and Sports Organizations (NFL, NHL, NBA, etc.) 

## Data
#### Description of the Dataset: 
The data for these analyses come from multiple original surveys used in the writing of Fans Have More Friends, a 2022 book by Ben Valenta and David Sikorjak. The surveys were administered by Prodege, an online marketing, consumer polling, and market research company, between February 2021-January 2022 with a purposeful goal of achieving a representative sample of U.S. adults for each survey. Following data cleaning, which included dropping rows for which the columns of interest were entirely null, the data had N=10,362 respondents/surveys with over 100 variables.

#### Preprocessing
Our data set includes survey participants demographic information such as Age [S2], Household Income [D4], Gender (Categorical) [S1], Employment Status (Categorical) [D5] , Educational Attainment (Categorical) [D6] , Race/Ethnicity (Categorical) [Hid_Ethnicity_Bucket]. 

There is also self-reported fandom [S15] that asks participants how much of a fan they are in 11 sports. Respondents are able to give a score from 1 - “Not a Fan” up to 6 - “Obsessed Fan of this Sport”. From these questions, we created a Fan magnitude variable, named fan_magnitude, which is the Euclidean norm of a participant's response.
Similar to the self-reported fan score, there is a question asked about how often a respondent watches top five self-chosen teams in the National Football League [TEAM6r1-r32]. Respondents were able to choose values 4: Every week, 3: most weeks, 2: some weeks, 1: only if it’s a big game, (reversed scale from 1: every week to 4: only if in survey). We formed a team magnitude variable, called Team6_magnitude, that was formed similar to the fan magnitude score. 

## Models
#### KPIs
We will measure the accuracy of predicting various fan activities using the following categorical variables against a baseline model of a random coin toss. 

#### Outputs of interest
VL1 - Thinking of the last year, which of the following activities have you done in conjunction with the sports you follow? These variables are answered either 0 = No or 1 =  Yes, making it a nominal binary variable.

[VL1r1] Went to a game 
[VL1r10] Talked about games online
[VL1r2] Watched a game at a sports bar
[VL1r11] Played in a fantasy sports league
[VL1r4] Place a bet
[VL1r12] Purchased a multi-game ticket page
[VL1r5] Listened to sports radio
[VL1r13] Bet in a group pool
[VL1r7] Wore my team’s jersey
[VL1r14] Plated daily fantasy

#### EDA / Model Selection
We are interested in making predictions for [VL1] questions based on the inputs described above. Our Exploratory Data Analysis (EDA) consisted of examining the features relationships with one another using histograms and pairplots stratified by a categorical variable. These analyses suggested that S2 (Age), D4 (Income Bracket), and Fan Magnitude would play an important role in each of the outputs we were considering.

We considered several classification algorithms including Logistic Regression, K Nearest Neighbors (KNN), Random Trees, AdaBoost, XGBoost, and Neural Network (NN). We compared their performance on our training data using KFold cross-validation with 5 fold splits, and all performed similarly well with respect to our outputs of interest, with KNN performing the worst. We ultimately decided on Adaboost, as it had a slight advantage overall. 

## Final Model Choice and Performance
Having selected AdaBoost as our algorithm of choice and after tuning the parameters, we trained it on our training data and ran predictions on our test data. The accuracies are as follows:

VL1: Thinking of the last year, which of the following activities have you done in conjunction with the sports you follow?

##### Prediction accuracy, Feature importance ([Age, Income, Fan Magnitude])

`VL1r1: went to a game`, 65.60%, [0.2229, 0.0457, 0.7314]

`'VL1r2: watched a game at a sports bar`, 64.06%, [0.3467, 0.1822, 0.4711]

`VL1r4: placed a bet through a sportsbook/etc`, 78.39%, [0.3857, 0.1486, 0.4657]

`VL1r5: listened to sports talk radio`, 63.48%, [0.2109, 0.0145, 0.7745]

`VL1r7: wore my team’s jersey`, 59.14%, [0.3707, 0.0185, 0.6108]

`VL1r10: talked about games online`, 72.12%, [0.3333, 0.1867 0.48])

`VL1r11: played in a fantasy sports league`, 76.51%, [0.30 , 0.32, 0.38]

`VL1r12: Purchased multi-game tickets`, 92.76%, [0.332, 0.288, 0.38 ]

`VL1r13: Bet in a group pool`, 79.31%, [0.2733, 0.06, 0.6667]

`VL1r14: Played daily fantasy`, 83.36%, [0.416, 0.16 , 0.424]

## Future Directions:
In an effort to whittle our features down to those most relevant for predicting the fan activities of interest, we focussed our analyses on Age, Income Bracket, and Fan Magnitude, as described above. On many outputs, we were able to make predictions more accurately than a random coin flip. Currently, our model can predict with 65% accuracy whether or not a given person will go to a sports game based on Age, Income Bracket, and Fan Magnitude alone. Moving forward, it would be interesting to incorporate more demographic information, like race and gender, to test whether our model’s accuracy remains consistent or when our model is restricted to just men or just women. Finally, with the rise of sports betting and time spent online, companies likely collect all sorts of information beyond basic demographics, and modeling approaches with these data could become very specific, which would be of interest to us.

