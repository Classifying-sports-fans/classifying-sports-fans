# classifying-sports-fans

A repository of code for the Erdos Institute's May 2024 Data Science Bootcamp

## **Project Title: Classifying Sports Fans**
Members: Mariah Warner, Deepisha Solanki, Rudy Perkins, Ryan Moruzzi, Sujoy Upadhyay, and Jacob Kepes
Project Mentor: Mohammad Noorandisoot

Description of the Dataset: The data for these analyses come from multiple original surveys used in the writing of Fans Have More Friends, a 2022 book by Ben Valenta and David Sikorjak. The surveys were administered by Prodege, an online marketing, consumer polling, and market research company, between February 2021-January 2022 with a purposeful goal of achieving a representative sample of U.S. adults for each survey. Following data cleaning, N=10,362 respondents/surveys.

Research Questions/Problem: Based on self-described fandom alone, some groups, like women, are potentially an untapped market that is not marketed towards. How can we predict different fan activities based on self-reported fandom and demographic variables? What is the likelihood of certain fan behaviors and activities based on self-described fandom and demographic variables? 

#### Stakeholders: 
Streaming Services (Hulu, Roku, Amazon, etc.), TV Networks (Fox, ABC/ESPN), Gambling Companies (DraftKings, FanDuel, Fanatics), Sports Teams, and Sports Organizations (NFL, NHL, NBA, etc.) 

#### Key Performance Indicators (KPIs):

The accuracy of our model predicting fan activites (going to a game, betting, etc.) based off particular demographic data and self-described fandom. 


### Modeling Approach:

We are attempting to identify people's likelihood of engaging in certain activities (VL1) based on their self-reported fandom (S15) and demographic information (S2, D4). From S15, we created an index of fan magnitude based on different types of sports fans. Our group is going to try several modeling approaches, based on a 20% training split, to see which stand out and perform better, including logistic regression and various classification models. From these models, we expect to be able to correctly identify someone’s likelihood of participating in various fan activities, including attending a sports game and other VL1 variables. We expect fan magnitude to be conditional on other variables, like income, race, age, and gender. We will then identify how accurate these models are.

Our group has decided on implementing the following classifying models and determining which is most accurate:
Logistic Regression
K-nearest Neighbors
Random Forest 
AdaBoost 
Gradient Boost
Xgboost
Neural networks


#### Independent Variables/Features

We will create an Index/Magnitude of Fandom based on:

-Fan Magniutde, based on [S15] - How much of a fan are you of the following sports?
1 - Not a fan of this sport : 6 - Obsessed fan of this sport
[S15r1]NFL
[S15r2]NBA
[S15r3]College Football
[S15r4]College Basketball
[S15r5]MLB
[S15r6]NHL
[S15r7]International Soccer
[S15r8]MLS
[S15r9]Combat Sports
[S15r10]NASCAR
[S15r11]Formula 1

-Team 6 Magnitude, based on [TEAM6] - Assuming games are available, how often will you watch the NFL games for the following teams. List teams with values 1: Every week, 2: most weeks, 3: some weeks, 4: only if its a big game,'TEAM6r1-32' are NFL teams.

#### Our outcome variables (KPI) will then be based on:

VL1 - Thinking of the last year, which of the following activities have you done in conjunction with the sports you follow? These variables are answered either 0 = No or 1 =  Yes, making it a nominal binary variable.
-[VL1r1] Went to a game 
-[VL1r2] Watched a game at a sports bar
-[VL1r3] Watched a game at a friend’s home
-[VL1r4] Place a bet
-[VL1r5] Listened to sports radio
-[VL1r6] Called into a sports radio show
-[VL1r7] Wore my team’s jersey
-[VL1r8] Watched games at home
-[VL1r9] Talked about games in person/over the phone
-[VL1r10] Talked about games online
-[VL1r11] Played in a fantasy sports league
-[VL1r12] Purchased a multi-game ticket page
-[VL1r13] Bet in a group pool
-[VL1r14] Plated daily fantasy

-[S12r3] Hours Watching Sports in a Typical Week (0-120 Hours)

-[NFL3] How often do you think you will bet on NFL games this NFL season?
-I will not bet on NFL Games this season, One or two weeks, Some weeks, Most Weeks, Every Week

-[NFL4] How many fantasy football leagues do you play in? (None, 1, 2, 3, 4 or more)

#### Potential Control Variables 

-[S1] Gender
-[S2]  Age
-[D4] Household Income (Categorical)
-[D5]  Employment Status
-[D6]  Educational Attainment
-[Hid_Ethnicity_Bucket] Race/Ethnicity



### Expectations and EDA:

Based on our initial Exploratory Data Analysis (EDA) we expect to be able to predict with some accuracy the following VL1** variables’ outcomes using a classification model. We expect Knn, RandomForests, or XGBoost to be among the best models for this problem. 

Based on the outcome VL1** variables, different variables appeared relevant. 

Here are some of our initial findings:

-Age, Household Income, and Fan Magnitude appeared to be related to whether a fan attended a game

-Age, Household Income, and Fan Magnitude appeared to be related to whether a fan watched a game at a sports bar

-Age, Household Income and Fan Magnitude appeared to be related to whether a fan placed a bet at a casino

-Household Income, Employment Status, and Fan Magnitude appeared to be related to whether a fan listened to sports talk radio

-Age and Fan Magnitude were related to whether a fan talked about games online

-Age, Household Income, and Fan Magnitude appeared to be related to whether a fan played in fantasy sports

-Age, Household Income, and Fan Magnitude appeared to be related to whether a fan purchased multi-game tickets

-Household Income, Team 6 Magnitude, and Interest in sports betting appeared to be related to whether a fan bet in a group pool

-Age and Fan Magnitude appeared to be related to whether a fan played daily fantasy




