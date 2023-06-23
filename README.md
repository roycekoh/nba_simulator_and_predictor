# NBA Monte Carlo Simulation and Betting Predictor

This project attempts to project the outcomes of NBA games by using historical data to generate many iterations of a Monte Carlo simulator and uses the outcome to assert a bet to place given the current betting spreads pulled from Draftkings. We have opted to use a Monte Carlo simulation to accurately project the scores of games as the sheer complexity in potential outcomes pushes us to parallelly leverage a model that considers a large magnitude of outcomes. Moreover, I was interested in this project simply because I love basketball and am constantly fascinated by Vegas' ability to project uncannily accurate score spreads.

We utilize a number of datasets, namely team data, game outcomes, player statlines, and daily rankings of teams in the NBA from 2004 to 2020 pulled from the official [NBA stats website](https://www.nba.com/stats) via their frontend API. Furthermore, we also use [Sports Database's API](https://sportsdatabase.com/) to poll the market spread on basketball games to pinpoint potentially profitable bets across a number of sportsbooks. We pull and store all historical statistics for both the NBA and betting odds to use as inputs.

# Running the Simulation:

The best way to run the simulation is through `nba-wins-prediction.ipynb` which involves the parsing and storage of historical information, cleaning and scaling of data, training and testing of models using monte-carlo validation, and testing the posited predictions on historical betting spreads. Various regression functions (linear, logistic, lasso, SVM) were tested to find the optimal combination in making predictions as well as features selected from team and player statistics.

# Model and Prediction:

As we leverage historical data from 2004-2020 in the training of our model to generate simulation iterations, we also found that both the predicted win totals and relative seeding of teams were very accurate, even when predicting future years (2022, 2023) where all metrics were not as thoroughly available. The average [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance) in predicted vs. actual end-of-year pre-playoff seeding was found to be around 4.613 from 2015-2020, a remarkably accurate hypothesis especially given the volatility in seeding of lower-ranked playoff teams with the introduction of the play-in tournament. Additionally, win totals were predicted with an accuracy of just over 92%.

These metrics were then used to conjecture potential bets on over/under win total betting spreads, and playoff odds taken from 3 different sports betting websites (Draftkings, Fanduel, BetMGM). Various levels of risk tolerance were also tested, quantified by betting on a varying number of predicted playoff teams (higher seeded teams are stronger favorites while lower ranked teams were deemed a higher risk bet).
