## Dividend Growth Investment Data

Dividend growth investing has been around for ages and has always been a widely appreciated way of receiving passive income. As with any other investment, an elaborated decision needs to be made which stocks to pick. Also as with any other investment: the higher the risk, the higher the potential reward. This dataset should support the decision for a portfolio selection driven by data.

This notebooke will download all relevant data from robinhood.com and dividend.com for dividend investors.    
The idea is to calculate a most realistic risk/reward score.    
It can be merged with any other data set based on the symbol.   

The approach is to download everything from robinhood.com, filter for only tradable stocks that pay dividend, then add their fundamental data, add ratings that robinhood.com offer (including the text for a rating itself), add popularity (basically how often this stock is in portfolios of robinhood users and add news that are displayed on robinhood.com. Lastly go through each stock symbol and look for a corresponding page on dividend.com. It turns out that only 7% of the robinhood dividend paying stocks can be found on dividend.com.