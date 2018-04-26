# Dividend Growth Investment Data

<p align="center">
  <img src="banner.jpg"/ width=70%>
</p>

Dividend growth investing has been around for ages and has always been a widely appreciated way of receiving passive income. As with any other investment, an elaborated decision needs to be made which stocks to pick. Also as with any other investment: the higher the risk, the higher the potential reward. This dataset should support the decision for a portfolio selection driven by data.

The [notebook](https://github.com/jonnylangefeld/dividend-data-download/blob/master/download-dividend-data.ipynb) will download all relevant data from robinhood.com and dividend.com for dividend investors.    
The idea is to calculate a most realistic risk/reward score.    

### Use the Data

The dataset is stored in both, `instruments.p` and `instruments.json`. The pickle file is a pandas DataFrame object. The benefit of the pickle file is, that the data is already classified properly. Load it with `pandas.read_pickle('instruments.p')`   
It can be merged with any other financial data set based on the symbol.  

### Approach

The approach is to download everything from robinhood.com, filter for only tradable stocks that pay dividend, then add their fundamental data, add ratings that robinhood.com offer (including the text for a rating itself), add popularity (basically how often this stock is in portfolios of robinhood users and add news that are displayed on robinhood.com. Lastly go through each stock symbol and look for a corresponding page on dividend.com. It turns out that only 7% of the robinhood dividend paying stocks can be found on dividend.com.

### Content

If you load a pandas DataFrame with `pandas.read_pickle('instruments.p')`, you get the following columns:

| Column Name | dtype | Description |Example|
| --- |---| ---|---|
symbol|object|Unique symbol name as received from robinhood|STM
name|object|Long name|STMicroelectronics N.V.
simple_name|object|Short Name|Stmicroelectronics
ceo|        object|CEO|Carlo Bozotti
description|object|Description|STMicroelectronics NV designs, develops, manufactures and markets products, which offers discrete and standard commodity components, application-specific integrated circuits, full custom devices and semi-custom devices for analog...
id|         object|Unique identifier on robinhood|67d7bb04-8c2e-4338-b72a-18857809ec8d
instrument| object|API URL to robinhood for this instrument|https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/
instrument_id|object|Unique identifier on robinhood|67d7bb04-8c2e-4338-b72a-18857809ec8d
bloomberg_unique|object|Unique identifier on bloomberg|EQ0015391600001003
fundamentals| object|API URL to robinhood to fundamentals of this instrument|https://api.robinhood.com/fundamentals/STM/
splits|     object|API URL to robinhood to splits of this instrument|https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/splits/
quote|      object|API URL to robinhood to quotes of this instrument|https://api.robinhood.com/quotes/STM/
url|        object|API URL to robinhood for this instrument|https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/
country|  category|Listed country for instrument|CH
state|    category|Active or passive on robinhood|active
headquarters_state|category|State of Headquarters|Geneve (Geneva)
headquarters_city| category|City of Headquarters|Plan-Les-Ouates
market|   category|API URL to robinhood to market of this instrument|https://api.robinhood.com/markets/XNYS/
exchange| category|Exchange on which this instrument is listed on|NYSE
sector|   category|Sector|Electronic Technology
industry| category|Industry|Semiconductor - Broad Line
type|     category|Type of instrument|nyrs
tradability|category|Tradability on robinhood (should always be tradable)|tradable
tradeable|category|Tradability on robinhood (should always be true)|True
price|     float64|Price at time of download|20.96
open|      float64|Open price at time of download|21.65
high|      float64|Highest price of day at time of download|21.74
low|       float64|Lowest price of day at time of download|20.89
high_52_weeks|  float64|Highest price within last 52 weeks|25.3
low_52_weeks|float64|Lowest price within last 52 weeks|14.07
percent_off_52_week_high|float64|Percentual difference to 52 weeks high|-17.15
volume|    float64|Trade volume at time of download|1827183.0
average_volume| float64|Average volume at time of download|3869267.0797
average_volume_2_weeks|  float64|Average volume for last two weeks at time of download|2478449.0
dividend_yield| float64|Percentual dividend yield from robinhood.com|0.9341
div_yield| float64|Percentual dividend yield from dividend.com|0.97
div_growth|float64|Amount of years in which dividends grew|1.0
annual_payout|  float64|Absolute dividend payouts withing last year|0.2
payout_ratio|float64|Payout ratio|15.2
num_employees|  float64|Number of employees|45468.0
year_founded|float64|Year in which the fund was founded|1987.0
shares_outstanding| float64|Number of outstanding shares|896590286.0
market_cap|float64|Market capitalization|19276691100.0
num_buy_ratings|float64|Absolute numnber of buy ratings on robinhood.com|12.0
num_hold_ratings|   float64|Absolute number of hold ratings on robinhood.com|10.0
num_sell_ratings|   float64|Absolute number of sell ratings on robinhood.com|4.0
percent_buy_ratings|float64|Percentage of all buy ratings `(num_buy_ratings/(num_hold_ratings+num_sell_ratings))`|0.46153846153846156
percent_sell_ratings|    float64|Percentage of all sell ratings `(num_sell_ratings/(num_hold_ratings+num_buy_ratings))`|0.15384615384615385
num_open_positions|   int64|Amount of accounts on robinhood.com that hold this position|5562
day_trade_ratio|float64|Day trade ratio|0.25
maintenance_ratio|  float64|Mainenance ratio|0.25
margin_initial_ratio|    float64|Margin initial ratio|0.5
pe_ratio|  float64|PE ratio|22.349
min_tick_size|  float64|Minimum tick size|nan
list_date|   datetime64[ns]|List Date|1994-12-07 00:00:00
recent_pay_date|  datetime64[ns]|Date of recent or closest dividend pay date|2018-03-27 00:00:00
news|       object|**Struct:** This is a list object. It contains a list of all news that were found on robinhood.com|[{'api_source': 'yahoo_finance', 'author': '', 'instrument': 'https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/', 'num_clicks': 8, 'preview_image_url': 'https://robinhood-prism-storage.s3.amazonaws.com/feed-images/28c95f29-1528-4b82-90a9-c89551709712', 'preview_image_width': 635, 'preview_image_height': 423, 'published_at': '2018-04-23T20:14:00Z', 'relay_url': 'https://news.robinhood.com/a26ec160-c0d9-3c34-bb0b-3934505561e7/', 'source': 'Yahoo Finance', 'summary': 'Taiwan Semiconductor Manufacturing Co Ltd TSM hit the entire technology industry hard after the company reported Q1 results on Apr 19 before market open.', 'title': '4 ETF Areas Under Watch on Waning Smartphone Demand', 'updated_at': '2018-04-23T21:34:59.894886Z', 'url': 'https://finance.yahoo.com/news/4-etf-areas-under-watch-184506323.html', 'uuid': 'a26ec160-c0d9-3c34-bb0b-3934505561e7', 'currency_id': 'None'}, {'api_source': 'seeking_alpha', 'author': '', 'instrument': 'https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/', 'num_clicks': 41, 'preview_image_url': '', 'preview_image_width': None, 'preview_image_height': None, 'published_at': '2018-04-23T18:59:00Z', 'relay_url': 'https://news.robinhood.com/4d2f466e-131d-3c6b-af13-4b14e689c65b/', 'source': 'Seeking Alpha', 'summary': 'A system such as this one can be a valuable tool to make smart investing decisions by focusing on hard quantified data as opposed to subjective opinions.', 'title': 'By The Numbers: Value And Quality Stocks In Technology', 'updated_at': '2018-04-23T19:34:55.156456Z', 'url': 'https://seekingalpha.com/article/4164921-numbers-value-quality-stocks-technology', 'uuid': '4d2f466e-131d-3c6b-af13-4b14e689c65b', 'currency_id': 'None'}, {'api_source': 'marketwatch', 'author': '', 'instrument': 'https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/', 'num_clicks': 279, 'preview_image_url': 'https://robinhood-prism-storage.s3.amazonaws.com/feed-images/a99fe583-cedd-4bf0-8466-5cb31b7128f1', 'preview_image_width': 1320, 'preview_image_height': 742, 'published_at': '2018-04-03T09:44:00Z', 'relay_url': 'https://news.robinhood.com/e475fea2-767e-3a33-b3dc-d6a7883c4c98/', 'source': 'MarketWatch', 'summary': 'Worries about global trade war, tech weakness persist into second quarter\n\nEuropean stocks were losing ground Tuesday, beginning the second quarter of 2018 dogged by the same technology-sector and trade-war worries that hurt equity markets during the first quarter.\n\nThe moves were tracking a selloff ......', 'title': 'European stocks slump, as techs follow U.S. lead lower', 'updated_at': '2018-04-03T13:34:22.470578Z', 'url': 'https://www.marketwatch.com/story/european-stocks-slump-as-techs-follow-us-lead-lower-2018-04-03', 'uuid': 'e475fea2-767e-3a33-b3dc-d6a7883c4c98', 'currency_id': 'None'}, {'api_source': 'seeking_alpha', 'author': '', 'instrument': 'https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/', 'num_clicks': 106, 'preview_image_url': '', 'preview_image_width': None, 'preview_image_height': None, 'published_at': '2018-04-02T19:17:00Z', 'relay_url': 'https://news.robinhood.com/320cc6aa-eefd-3860-8670-6d7e28437180/', 'source': 'Seeking Alpha', 'summary': 'Thus, new shares are not a commitment to success; they are a commitment by Microvision against current shareholders.\n\nThis article discusses whether there is a reason or need for Microvision (MVIS) shareholders to approve the proposal for the authorization of 50 million new shares at the upcoming ......', 'title': "Microvision's Annual Shareholder Meeting: Authorization For 50 Million New Shares Is Not In Shareholders' Interest", 'updated_at': '2018-04-05T00:36:19.396795Z', 'url': 'https://seekingalpha.com/article/4160601-microvisions-annual-shareholder-meeting-authorization-50-million-new-shares-shareholders', 'uuid': '320cc6aa-eefd-3860-8670-6d7e28437180', 'currency_id': 'None'}, {'api_source': 'marketwatch', 'author': '', 'instrument': 'https://api.robinhood.com/instruments/67d7bb04-8c2e-4338-b72a-18857809ec8d/', 'num_clicks': 287, 'preview_image_url': 'https://robinhood-prism-storage.s3.amazonaws.com/feed-images/b78da218-8799-4d0a-a3ae-05b10426c39a', 'preview_image_width': 1320, 'preview_image_height': 742, 'published_at': '2018-03-28T09:35:00Z', 'relay_url': 'https://news.robinhood.com/3092d15f-03b6-3811-ae3d-a003dbed9474/', 'source': 'MarketWatch', 'summary': 'European tech stocks index down the most since early February\n\nEuropean equities took a sharp hit on Wednesday, with chip stocks losing the most in a tech-driven selloff that also left U.S. stocks in the red in the previous session.\n\nHow markets are moving\n\nThe Stoxx Europe 600 index SXXP, -1.15% ......', 'title': 'European stocks slide more than 1% as tech stocks are hit hard ', 'updated_at': '2018-03-28T13:34:52.297330Z', 'url': 'https://www.marketwatch.com/story/european-stocks-slide-more-than-1-as-tech-stocks-are-hit-hard-2018-03-28', 'uuid': '3092d15f-03b6-3811-ae3d-a003dbed9474', 'currency_id': 'None'}]
recent_payment|  timedelta64[ns]|Difference in days from recent_pay_date to data of download (positive days means pay date is in the future, negative means it is in the past)|-28 days +00:00:00
ratings|    object|**Struct:** This is a list object. It contains a list of all ratings that were found on robinhood.com|[{'type': 'buy', 'text': 'Chipmakers with heavy automotive exposure, like ST, should profit from the secular trend toward more advanced electronics content in cars over the next few years.'}, {'type': 'sell', 'text': 'Despite being one of the largest chipmakers (by revenue) in the world, ST has not developed a massive scale advantage, as its gross margins and operating profits are below those of other successful pure-play analog chipmakers.'}, {'type': 'buy', 'text': 'ST has made some tough decisions, such as discontinuing the future development of certain digital chip products, but we think these moves will lead to improved profitability for all of ST.'}, {'type': 'sell', 'text': 'ST does not have a strong record of generating excess returns on capital, although it is on pace to significantly improve on this metric.'}, {'type': 'sell', 'text': 'We are concerned about ST’s ownership by the French and Italian governments, which raises doubts as to whether it is truly focused on operating efficiency.'}, {'type': 'buy', 'text': 'ST made some good moves to shed lower-margin businesses, like the ST-Ericsson wireless joint venture and stakes in two low-margin memory chipmakers, in recent years.'}]
payout_history|  object|**Struct:** This is a DataFrame object. It contains a DataFrame of all payouts that were found on dividend.com|Payout Amount Declared Date Ex-Dividend Date Record Date Pay Date ▼  <br/> 0          0.0510           NaT       2018-03-19  2018-03-20 2018-03-27    
