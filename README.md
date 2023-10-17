# Homework 2: Considering Bias in Data

This repository contains the data files, code and results of Homework 2, for the course Data 512: Human Centered Data Science at the University of Washington's MS in Data Science program. 

## Goal of Assignment

The goal of this assignment is to explore the concept of bias in data using Wikipedia articles.

## Resources Used
- Editor used: VS Code
- Python version: 3.9.18
- Packages used: json, time, requests, urllib.parse, pandas, tqdm, numpy

## API Documentation
- [MediaWiki API documentation](https://www.mediawiki.org/wiki/API:Info)
- [MediaWiki ORES documentation](https://www.mediawiki.org/wiki/ORES)
- [Wikipedia: Content Assessment](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment)

## Project Organization

This project has the following structure:

```
.
├── data/
│   ├── data/NST-EST2022-POP.xlsx
│   ├── data/US States by Region - US Census Bureau.xlsx
│   ├── data/us_cities_by_state_SEPT.2023.csv
│   └── data/wp_scored_city_articles_by_state.csv
├── code/
│   ├── Analyzing Bias in Data.ipynb
├── LICENSE
└── README.md
```
## Steps to Reproduce This Research

1. Set up the required resources as listed in the Resources header above. 
2. Run the Analyzing Bias in Data.ipynb file. The results will be produced in the notebook. 
3. Analyze results.

## Data 

Source Files:
- [Articles List](data\us_cities_by_state_SEPT.2023.csv) This dataset contains a list of Wikipedia article pages about US cities from each state
- [Population](data\NST-EST2022-POP.xlsx) The US Census Bureau provides updated population estimates for every US state which can be found on their [website](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html).
- [Regional Information](data\US-States-by-Region-US-Census-Bureau.xlsx) Regional and divisional agglomerations as defined by the US Census Bureau. 
- [Sample API Notebook to obtain Revision ID](https://drive.google.com/file/d/15UoE16s-IccCTOXREjU3xDIz07tlpyrl/view?usp=drive_link). This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 14, 2023
- [Sample API Notebook to obtain ORES Score](https://drive.google.com/file/d/17C9xsmR9U3lJeD52UTbAedlHDetwYsxs/view?usp=drive_link). This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.2 - August 14, 2023

Final Dataset:
- [Scored City Articles by State](data\wp_scored_city_articles_by_state.csv) List of all US cities for which Wikipedia articles returned a Revision ID and ORES Score.

|Column|Description|
|---|---|
|`state`|the name of the US state|
|`regional_division`|the regional division the city belongs to e.g. New England|
|`population`|the population of each state"|
|`article_title`|the article(s) we want to retrieve data for|
|`revision_id`|the most current revision ID of the article page|
|`article_quality`|predicted quality score for each article|

Note: The article quality scoring used is called "Objective Revision Evaluation Service" or ORES. ORES is a machine learning tool that can provide estimates of Wikipedia article quality. The article quality estimates are, from best to worst:
- FA - Featured article
- GA - Good article (sometimes called A-class)
- B - B-class article
- C - C-class article
- Start - Start-class article
- Stub - Stub-class article

## Research Implications

1. What biases did you expect to find in the data (before you started working with it), and why?

    Overall in the US, the states in New England (i.e. Connecticut, Maine, Massachusetts, New Hampshire, Rhode Island and Vermont) have the highest educational attainment. Therefore I expected that article quality will be highest in this division. However, the results show that while New England did rank high in terms of high quality articles, it was not at the top of the list. 

2. What (potential) sources of bias did you discover in the course of your data processing and analysis?

    During the analysis, I discovered that the dataset did not contain any articles for the states of Connecticut (ranked 29 by population) and Nebraska (ranked 38 by population). Adding data for these states to the dataset could have potentially altered the ranking at state and division level. For the states that were present, articles for only two cities i.e. Bogart in Georgia and Salem Township in Pennsylvania,  were not found in the dataset which is a small number. 

3. What might your results suggest about (English) Wikipedia as a data source? 

    For this analysis, Wikipedia proved to be a useful source. It provides data on most US cities, their articles and associated metadata. Data is also available for the states that were not included in this analysis i.e. Connecticut and Nebraska. Wikipedia offers APIs such as MediaWiki that allow for more structured access to data even challenging aspects such as article quality.

4. How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?

    A researcher can add articles from the states of Connecticut and Nebraska to this dataset to improve the representation of states. This might also change the ranking of divisions. An interesting analysis would be to compare indicators of well-being such as socio-economic status or average educational attainment in states to the overall coverage and quality of articles. This information can be added to the dataset for a more nuanced analysis. 