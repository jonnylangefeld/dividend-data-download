# Dividend Growth Investment Data

Dividend growth investing has been around for ages and has always been a widely appreciated way of receiving passive income. As with any other investment, an elaborated decision needs to be made which stocks to pick. Also as with any other investment: the higher the risk, the higher the potential reward. This dataset should support the decision for a portfolio selection driven by data.

The [notebook](https://github.com/jonnylangefeld/dividend-data-download/blob/master/download-dividend-data.ipynb) will download all relevant data from robinhood.com and dividend.com for dividend investors.    
The idea is to calculate a most realistic risk/reward score.    

### Use the Data

The dataset is stored in both, `instruments.p` and `instruments.json`. The pickle file is a pandas DataFrame object. The benefit of the pickle file is, that the data is already classified properly. Load it with `pandas.load_pickle('instruments.p')`   
It can be merged with any other financial data set based on the symbol.  

### Approach

The approach is to download everything from robinhood.com, filter for only tradable stocks that pay dividend, then add their fundamental data, add ratings that robinhood.com offer (including the text for a rating itself), add popularity (basically how often this stock is in portfolios of robinhood users and add news that are displayed on robinhood.com. Lastly go through each stock symbol and look for a corresponding page on dividend.com. It turns out that only 7% of the robinhood dividend paying stocks can be found on dividend.com.