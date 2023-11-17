# Predicting  NBA Player Points with Regression Models

Andrew Hendricks

The legalization of sports betting in the USA has made gambing on sports increasingly commonplace: tens of millions of Americans now enjoy wagering on the outcomes of games each year. In this project, I web scrape player, team, and opponent data from nba.com and use regression models to predict how many points a player will score in an NBA game with a mean absolute error of about 4.4 points and an r squared of over 50%. My goal is to provide useful information to the many individuals like me who enjoy betting on the NBA.

![Brrok_Lopez](https://github.com/ahendricks2/Capstone/assets/141271148/d6a069e0-afb8-4bb1-a7b7-9455d051f837)

This file is licensed under the Creative Commons Attribution-Share Alike 2.0 Generic license.


## Repository Navigation
In this repository, I store the final notebook and non-technical presentation in the main repository and the more detailed notebooks in the notebooks folder.

[Non-Technical Presentation](https://github.com/ahendricks2/Capstone/blob/main/Non_Technical_Presentation.pdf)

[Notebook 1](https://github.com/ahendricks2/Capstone/blob/main/1_Data_Collection.ipynb): Data Classification
[Notebook 2](https://github.com/ahendricks2/Capstone/blob/main/2_Data_Cleaning.ipynb): Data Cleaning
[Notebook 3a](): Feature Additions for Current Game
[Notebook 3b](https://github.com/ahendricks2/Capstone/blob/main/3b_Feature_Addition_Upcoming_Game.ipynb): Feature Additions for Upcoming Game
[Notebook 4](https://github.com/ahendricks2/Capstone/blob/main/4_Modeling.ipynb): Iterative Modeling Process
[Notebook 5](https://github.com/ahendricks2/Capstone/blob/main/5_Final_Model_Evaluation.ipynb): Final Model Evaluation Notebook


## Business Understanding and Data Understanding
In [an article](https://www.usatoday.com/story/sports/sports-betting/2023/05/25/sports-betting-popularity-creates-gambling-addiction-concerns/70228634007/) from USA Today published in May of 2023, the author, Chris Bumbaca, shares two statistics that frame the popularity of sports betting: according to the American Gaming Association, 39.2 million people bet on sports the last 12 months preceding the article's publication, and a Harris Poll from November 2022 revealed that 71% of sports gamblers bet on sports at least once a week, with 20% of people betting on sports at least once a day.

I am a fan of the NBA, and like millions of Americans, I occasionally enjoy wagering on games. The legalization of sports betting in the USA  and the rise in online sports betting platforms that resulted from it have made gambling on games increasingly accessible for fans like me. In general, I bet for fun and do not take it seriously, but my fandom and the popularity of sports betting inspired me to take on this project and build a regression model to predict how many points NBA players will score in their upcoming games. 

The stakeholders for this project include myself and the millions like me who could benefit from having more information to use when placing bets. All forms of gambling are inherently uncertain, and gambling on sports is no exception. My goal for this project is to provide context to understand the nature of that uncertainty in reference to NBA player scoring and also to hopefully reduce that uncertainty as much as possible. Given that goal, my two most important metrics are mean absolute error and r squared.

To build my models, I collect hundreds of thousands of player box scores, team box scores, and player bios by web scraping nba.com. I begin with player box score records from the 2015-16 season to the 2022-23 season, which I use as a cut off because most teams had already adapted core features of modern basketball at that point. 

Because the records I collect contain only single game performances for players and teams, I create rolling and expanding averages to provide the model with more stable information to use when making predictions. I also create features for known information about upcoming games, like the number of days of rest each team will have going into the game and where the game will be played.

As any NBA fan knows, player scoring on a night to night basis fluctuates substantially for all kinds of reasons, which the following visualization of Mikal Bridges' night to night scoring demonstrates. Whether using my model or not, individuals who are interested in gambling on night to night player scoring should taking the variability of the data into account when placing bets.

# BRIDGES SCORING GRAPHIC



## Modeling and Evaluation
Over the course of the project, I iterate through 13 models, including linear regression models, ensemble models, boosting models, and an LSTM neural network. The best performing in terms of both mean absolute error and r-squared is the gradient boosting regressor. On unseen data, the final model has an MAE of around 4.6 points and an r-squared of about 54%, which substantially outperforms the dummy.

![image](https://github.com/ahendricks2/Capstone/assets/141271148/014331b3-500a-4ae7-aad3-cfce49688a9e)

For the final iteration of the model that includes all of the data, the metrics improve to an MAE of around 4.4 points and an 4-squared of about 55%. The MAE is highest for players with higher scoring totals and lowest for players with lower scoring totals. The median absolute error is nearly a full point lower than the mean, which suggests that very wrong predictions have a big pull on the calculation of the mean, and the model performs about equally well at all points of the season.

![image](https://github.com/ahendricks2/Capstone/assets/141271148/0b487e44-3e26-4d0c-aa3f-4c072369d371)

## Conclusion
One of the best uses for my model would be to contextualize the inherent randomness in betting on night to night player scoring outcomes. Even with access to hundreds of features and hundreds of thousands of box score records, my model cannot account for 45% of the variation in night to night player scoring outcomes. One of the major factors that my model does not take into account is the availability of teammates and opposing playeres, which can have a big influence on a player's minutes and usage on a given night. That would explain some of the 45%. Additionally, though, there is a substantial amount of randomness involved, so it would be a great idea not to gamble more than you are willing and able to lose on a given outcome. 

If anyone does use this model to place bets, please understand that this is a data science project. It is not financial advice, and it is not telling you how you should or should not gamble. Its main purpose is to maximize performance.

For those who understand the risk and still want to make bets on night to night player scoring, I would recommend choosing scoring lines where the model's predictions are at least 3.5 points above or below the line so that it is outside the median absolute error. I would also recommend choosing games where the player availability is mostly stable so that the tendencies the model uses to make prediction reflect the conditions when entering the game.


## Reproduction instructions
All of the data for this project comes from web scraping nba.com using the [nba api package](https://github.com/swar/nba_api). My data collection notebook provides code and markdown to show how I got the data, and the code is reproducible using the Python in my notebooks.

The environment requirements can be found [here](https://github.com/ahendricks2/Capstone/blob/main/requirements.txt).
