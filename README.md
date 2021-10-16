---
page_type: 
- Complete Solution
languages:
- Python
products:
- Azure Machine Learning | Azure Blob Storage
description: 
- Scrub the stock related news and do sentiment analysis on top of that.
urlFragment: "https://github.com/RajdeepBiswas/Stock_Sentiment_Analysis"
---

# STOCK MARKET SENTIMENT ANALYSIS
![MainPic](images/MainPic.JPG)

## Executive Summary

  The core purpose of this project is to predict the market sentiment of a given stock. This can be then augmented with a timeseries, quant and fundamentals-based stock trading algorithm to make more informed decision whether a stock can yield profit or not. In broad terms, rising prices indicate bullish market sentiment, while falling prices indicate bearish market sentiment (marketsentiment).
Disclaimer: This work should not be used to make any financial decision and it is purely academic in nature. 

## Contents
| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `notebook`        | Python Notebooks.                          |
| `data`            | S&P 500 stock news data.                        |
| `images`          | Sample images used for documentation.      |
| `.gitignore`      | Define what to ignore at commit time.      |
| `CHANGELOG.md`    | List of changes to the sample.             |
| `CONTRIBUTING.md` | Guidelines for contributing to the sample. |
| `README.md`       | This README file.                          |
| `LICENSE`         | The license for the sample.                |

## Data
High-quality financial data is expensive to acquire and is therefore rarely shared for free. My goal is to make the following dataset free of errors and make it available to everyone at no cost.
For this project, I am extracting the daily news data for the companies that comprise the S&P 500 (sp-500) from the Yahoo Finance news RSS feeds for an input ticker. The S&P 500 Index, or the Standard & Poor's 500 Index, created in 1957 is widely regarded as the best single gauge of large-cap US equities. It is a market-capitalization-weighted index of the 500 largest publicly traded companies in the U.S and covers approximately 80% of available market capitalization. It is not an exact list of the top 500 U.S. companies by market capitalization because there are other criteria to be included in the index (sp500).
Codebook Location: https://github.com/RajdeepBiswas/Stock_Sentiment_Analysis/blob/main/notebook/get_snp500_news.ipynb
**Data Sources and Description:**  
1.	Daily Stock News 
Source: Yahoo Finance news RSS feeds 
File Name Format: snp500_news_gold.csv 
Link: https://github.com/RajdeepBiswas/Stock_Sentiment_Analysis/tree/main/data/gold

**Research Questions:**  
*	How is the sentiment for a particular stock based on current news? The labels are positive, negative, and neutral.
*	Does Opinion Mining or Aspect-based Sentiment Analysis on Stock market news give us some clues for market movement?

**Why analyze these data?**  
	I think the answer boils down to why invest in stock. There is a lot of literature out there on this but for me below would be the top 3 reasons (why-invest-in-stocks).  
1.	Potentially beat the inflation: The ability to protect your wealth from inflation, as the returns often significantly outpace the rate of inflation.
2.	Liquidity: The ease of buying and selling, which makes stocks a more liquid investment compared to other options like real estate.
3.	Low Startup Cost: The ability to start small. Thanks to $0 commissions and the ability to buy fractional shares with many online brokers, investors can begin purchasing stocks with a little bit of money.

## What Method?  
Before going into the methods, I would like to call out that the research will have at the very least embody the following principles (responsible-ai):  
* Fair - AI must maximize efficiencies without destroying dignity and guard against bias.
* Accountable - AI must have algorithmic accountability.
* Transparent - AI systems must be transparent and understandable.
* Ethical - AI must assist humanity and be designed for intelligent privacy.

The news datasets are extraordinarily rich in nature and a lot of interesting data science and exploratory  data analytics analysis can be done using it. For this project I plan to address the following topics before diving into the prediction section.:
•	Raw data extraction for the file, API based and web datasets. Let us call this Bronze Layer.
•	Data transformation using python from Raw to Processed stage. We will call this Silver Layer.
•	Finally store the processed data and optionally flatten it by joining using standard taxonomy in a serving layer. We will call this Gold Layer since this will be the single source of truth for the applications and the visualizations. 
•	In depth EDA across multiple facets of the stock news datasets
•	Visualizations on the datasets showing various aspects of the data
•	Find answers for the research questions using the below mentioned methodologies.
1.	Sentiment Analysis which applies sentiment labels to text, which are returned at a sentence level, with a confidence score for each. The labels are positive, negative, and neutral. Confidence scores can range from 1 to 0. Scores closer to 1 indicate a higher confidence in the label's classification, while lower scores indicate lower confidence. For each document or each sentence, the predicted scores associated with the labels (positive, negative, and neutral) add up to 1.
2.	Opinion Mining or Aspect-based Sentiment Analysis also known as Aspect-based Sentiment Analysis in Natural Language Processing (NLP) (aspect-based). This feature provides more granular information about the opinions related to attributes of products or services in text. The API surfaces opinions as a target (noun or verb) and an assessment (adjective).
3.	We have done the sentiment analysis of the unlabeled dataset using both commercial and open-source offerings. 
Commercial: The Text Analytics API is a cloud-based service that provides advanced natural language processing over raw text, and includes four main functions: sentiment analysis, key phrase extraction, named entity recognition, and language detection. We have used the Free Tier which can do sentiment analysis for 5k text records free per month (pricing). 
Open Source: a. VADER Sentiment Analysis. VADER (Valence Aware Dictionary and sEntiment Reasoner) is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media and works well on texts from other domains.
b. TextBlob is a Python (2 and 3) library for processing textual data. It provides a consistent API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, and more (textblob).
c. Dictionary based sentiment analyzer. It did give great results as we will illustrate below.

## Potential Issues?  
The challenge in terms of the prediction is best described by the following long-standing hypothesis:  
**The Efficient Market Hypothesis (EMH):**  
The efficient market hypothesis (EMH), alternatively known as the efficient market theory, is a hypothesis that states that share prices reflect all information and consistent alpha generation is impossible.
According to the EMH, stocks always trade at their fair value on exchanges, making it impossible for investors to purchase undervalued stocks or sell stocks for inflated prices. Therefore, it should be impossible to outperform the overall market through expert stock selection or market timing, and the only way an investor can obtain higher returns is by purchasing riskier investments.  
**The Random Walk Hypothesis:**  
Random walk theory suggests that changes in stock prices have the same distribution and are independent of each other. Therefore, it assumes the past movement or trend of a stock price or market cannot be used to predict its future movement. In short, random walk theory proclaims that stocks take a random and unpredictable path that makes all methods of predicting stock prices futile in the long run.  
Random walk theory believes it is impossible to outperform the market without assuming additional risk. It considers technical analysis undependable because chartists only buy or sell a security after an established trend has developed. Likewise, the theory finds fundamental analysis undependable due to the often-poor quality of information collected and its ability to be misinterpreted.  
This is a remarkably interesting project and many people have pursued this as their PhD thesis.  If I do not strike a balance on the data analysis vs predictions vs the different type of features, I would like to expose, it can quickly go off schedule. Also, I need to draw boundaries on the MSE or other performance indicators. Hyperparameter tuning would be part of the project, but I would also like to try out as many models as possible.  
Another potential issue I am thinking of is Contrarian Investing (Contrarian_investing). This is an investment strategy that is characterized by purchasing and selling in contrast to the prevailing sentiment of the time. A contrarian believes that certain crowd behavior among investors can lead to exploitable mispricing in securities markets. For example, widespread pessimism about a stock can drive a price so low that it overstates the company's risks and understates its prospects for returning to profitability. Identifying and purchasing such distressed stocks, and selling them after the company recovers, can lead to above-average gains. Conversely, widespread optimism can result in unjustifiably high valuations that will eventually lead to drops, when those high expectations do not pan out. Avoiding (or short selling) investments in over-hyped investments reduces the risk of such drops. These general principles can apply whether the investment in question is an individual stock, an industry sector, or an entire market or any other asset class.  

## Concluding Remarks
The project not yet finished.  I want to build out a multi-model system which can generate real time alerts. And integrate news and social media sentiment scoring with the stock prediction. I am enjoying the process and it is turning out to be a very satisfying and humbling option.  

**What it is not:**  
* Should not be used as a basis for any financial decision.
* We are not trying to produce a new algorithm to beat the market.

### Disclaimer: This research should not be used to make any financial decision and it is purely academic in nature. 

## References  
ai/responsible-ai. (n.d.). Retrieved from microsoft.com: https://www.microsoft.com/en-us/ai/responsible-ai  
aspect-based. (n.d.). Retrieved from tisane.ai: https://tisane.ai/knowledgebase/what-is-aspect-based-sentiment-analysis-absa/  
automated-ml. (n.d.). Retrieved from docs.microsoft.com: https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml#time-series-forecasting  
cognitive-services. (n.d.). Retrieved from https://docs.microsoft.com: https://docs.microsoft.com/en-us/azure/cognitive-services/  
concept-automated-ml. (n.d.). Retrieved from docs.microsoft.com: https://docs.microsoft.com/en-us/azure/machine-learning/concept-automated-ml#how-automated-ml-works  
consume-web-service. (n.d.). Retrieved from docs.microsoft.com: https://docs.microsoft.com/en-us/azure/machine-learning/how-to-consume-web-service?tabs=python#request-data  
container-instances. (n.d.). Retrieved from docs.microsoft.com: https://docs.microsoft.com/en-us/azure/container-instances/container-instances-overview  
Contrarian_investing. (n.d.). Retrieved from wikipedia.org: https://en.wikipedia.org/wiki/Contrarian_investing  
differences-between-forward-pe-and-trailing-pe. (n.d.). Retrieved from www.investopedia.com: https://www.investopedia.com/articles/investing/041013/differences-between-forward-pe-and-trailing-pe.asp  
Efficient-market_hypothesis. (n.d.). Retrieved from en.wikipedia.org: https://en.wikipedia.org/wiki/Efficient-market_hypothesis  
kubernetes-service. (n.d.). Retrieved from azure.microsoft.com: https://azure.microsoft.com/en-us/services/kubernetes-service/  
marketsentiment. (n.d.). Retrieved from investopedia.com: https://www.investopedia.com/terms/m/marketsentiment.asp  
pricing. (n.d.). Retrieved from https://azure.microsoft.com: https://azure.microsoft.com/en-us/pricing/details/cognitive-services/text-analytics/  
Shah, V. H. (n.d.). default. Retrieved from https://bigquant.com: https://bigquant.com/community/uploads/default/original/1X/5c6d3b9959a8556a533a58e0ac4568dfc63d6ff4.pdf  
sp500. (n.d.). Retrieved from www.investopedia.com: https://www.investopedia.com/terms/s/sp500.asp  
sp-500. (n.d.). Retrieved from www.spglobal.com: https://www.spglobal.com/spdji/en/indices/equity/sp-500/#overview  
Stock_market_prediction. (n.d.). Retrieved from en.wikipedia.org: https://en.wikipedia.org/wiki/Stock_market_prediction  
text-analytics. (n.d.). Retrieved from https://docs.microsoft.com: https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/  
textblob. (n.d.). Retrieved from https://textblob.readthedocs.io: https://textblob.readthedocs.io/en/dev/quickstart.html  
vaderSentiment. (n.d.). Retrieved from https://github.com: https://github.com/cjhutto/vaderSentiment  
why-invest-in-stocks. (n.d.). Retrieved from www.fool.com: https://www.fool.com/investing/how-to-invest/stocks/why-invest-in-stocks/  
