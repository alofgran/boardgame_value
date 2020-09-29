# Boardgame Values

## __Purpose & Data__
This repo serves as a demonstration of my work with a unique, little-analyzed dataset.  Data has been secured from the BoardGameGeek.com (BGG) API via the [boardgamegeek](https://pypi.org/project/boardgamegeek/) package.

This repo pulls data from BoardGameGeek.com and MiniatureMarket with the goal of developing some sort of valuation around board games.  The features of the dataset are quite skewed, have a high kurtosis, and are heteroskedastic.  I employed my understanding of statistical methods and research of machine learning algorithms to develop an in depth analysis of the data, and developing a machine learning pipeline that can handle the identified hurdles.  The `predict_bgg_rating` notebook goes much deeper into this analysis of the BGG dataset.

## __Business Cases__
### __Game Rating Prediction__
Because this analysis involves so many potential criteria, its value is easily relatable to many game designers.  This model allows users to create a theoretical boardgame based on hundreds of criteria (e.g. which categories and mechanics it employs, suggested age ranges, specific designers/artists, etc.) and then determine what rating such a game may have with (currently) very high accuracy.  A game with a high rating will appear higher on BGG's lists, developing organic marketing efforts (this notebook shows a clear correlation between individuals owning/reviewing/rating a game and individuals wanting/wishing for the game).  While approaching game design from this point of view isn't as artistic as one may like, I suggest it could be a viable business strategy due to the strong correlation between

### __Game Valuation and Price Prediction__
While not yet completed, game valuation will be drawn by a simple (price/rating) calculation.  Consumers and producers alike could derive value from such a model.  Consumers will be able to more accurately evaluate their perception of value in a game, and determine if the value justifies the cost (or if their perception is unrealistic!). Producers, on the other hand, would be able to see where their price fits in the market to determine if it's viable to compete.  They would also be able to determine if their 

This method of valuation allows me to determine the marginal value ("points" per dollar of cost), and is ideal for regression-type problems (especially in causal analysis).  The rating, as with the game-rating model, will be a bayesian average to provide an accurate reflection of games with very few ratings (I'll re-calculate this with the `user_ratings` (count) value in the BGG dataset.  Price data will come from BoardGameAtlas.com, which aggregates data from a variety of retailers on a daily basis.  An SQL database will be built to retrieve the data, and I'll automate the collection by setting up a cron-job to run the collection script regularly.

Once I collect enough price data, I'll be able to use the standard deviation of historical prices for each game as a scale (e.g. 1 std. dev. above the mean=='okay price', 3 std. dev. below the mean=='incredible price', etc.).  The categorization will serve as a reference point for consumers and producers, enabling a clear interpretation of price predictions.

Ideally, the end result will allow users to modify criteria to define their own value (by filtering the data) and deriving predictions for filtered games.

## __Related Efforts__
* https://github.com/garrettseward/boardgame-sentiment
* https://github.com/romulofff/BoardGameGeekAnalysis (note: this is in Portuguese)
* https://github.com/Laurencewm/BoardGamePriceAnalysis
* https://github.com/natc79/BoardGameReviews (linear regression of similar data)
