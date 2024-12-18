<style>
  body {
    font-family: 'Times New Roman', Times, serif;
  }
	 h1 {
    text-align: center;
  }
</style>


# Wine Quality Analysis

## Contents 
I. Introduction \
II. Objectives \
III. Methods* \
IV. Conclusions \
V. References \
*All code can be found in Methods_final.pdf

## I. Introduction

Wine is one of the world’s most beloved beverages, enjoyed worldwide for its rich variety of flavors, cultural value, and presence in social and culinary experiences. The market offers an expansive range of wines, from cabernet sauvignon to merlot and from Portuguese to French varieties, each distinct in its characteristics. As consumers, we each have our own tastes and preferences, continually seeking the best quality wine within our budget. But what defines a wine’s quality, and how can we identify the best options available?
For our data analysis project, we sourced datasets from the University of California, Irvine, including data on red and white vinho verde wines from northern Portugal. Our objective is to model wine quality based on physicochemical tests, aiming to understand how specific chemical properties contribute to wine quality ratings in different regions. By examining these datasets, we hope to uncover the role of chemical factors in determining a wine’s quality, helping consumers make informed choices about the wines they select.


## II. Objectives

Aim 1: **Utilize Dataset A to identify the relationship between chemical properties and quality scores in wines**

1.1. Summarize the chemical composition of wines to establish wine classes based on background data

1.2. Develop a classifier to categorize wines into chemical classes and examine their relationship with quality scores


Aim 2: **Compare wine quality between Dataset A and Dataset B**

2.1. Generalize the chemical composition of wines in Dataset B to align with the wine classes defined in Dataset A

2.2. Use the classifier from Dataset A to predict the potential quality scores of wines in Dataset B

<iframe src="assets/wine4.html" width=800 height=600 frameBorder=0></iframe>


## III. Methods



### A. Word Cloud


The first dataset, from Bender et al. (2024), includes data from 824k reviews of wines from the Vivino platform. The dataset was contains a variety of information regarding multiple types of wine, such as year, region, rating, alcohol percentage, price, grape composition, and reviews. In addition to this dataset, the researchers conducted an in-person wine ranking study with 256 participants. However, for the purposes of this project, we focused exclusively on the Vivino data.

Each wine review includes a photo of the label, a user rating on a scale of 1 to 5, and a written explanation or comments on the wine’s flavor. Commonly used terms in these reviews include "taste," "palate," "nose," "hint," "fruity," "full-bodied," "drink," and "sweet" [Methods 1A]. At first glance, these terms seem to carry a neutral to positive sentiment, so we investigated their association with ratings. The distribution of ratings within this dataset ranges from 3.0 to 5.0, with an average rating of approximately 4.6 [Methods 1B]. The positive sentiment reflected in the most frequently used words is consistent with the high average ratings, which tend to cluster around 4.5 to 5.0.


<iframe src="assets/wine.html" width=800 height=600 frameBorder=0></iframe>


### B. Average Wine Ratings by Country


Each review is associated with a label, which contains a wealth of information including the origin of the wine, the year it was bottled, the alcohol content, and other attributes. To get an idea of any areas with relatively higher or lower ratings, we looked into the ratings by country and alcohol content. The ratings ranged from 4 to 4.3, with the highest ratings coming from South Africa [4.3, NA%] and Argentina [4.25, 13.23%], and the lowest coming from the United States [3.99, 13.99%],  and Portugal [4, 14.61%].  It is worth noting that the lower rated wines appear to have slightly higher alcohol content [Methods 1C]. However, the data from these reviews give no indication regarding the origin of the reviewer, and are ultimately subjective. It could be the case that people in the lower rating countries tend to rate things lower, but we cannot know from this dataset. Other potential reasons for the lower ratings of higher-alcohol wines could include price (since higher alcohol content often correlates with more expensive wines) or the overpowering presence of alcohol, which may disrupt the balance and harmony of the wine’s flavors.


<iframe src="assets/globe_map.html" width=800 height=600 frameBorder=0></iframe>


### C. Wine Price and Alcohol Content Bubble Chart by Region with Year Filter


One reason for the lower rating for wines higher in alcohol content could be that wines higher in alcohol content are higher in price. We visualized the relationship between alcohol content and price overtime, and did not see any noticeable trends [Methods 1D].  Interestingly, wines with higher alcohol content and lower ratings generally had average prices, suggesting that the lower ratings may be attributed to other factors affecting the wine's quality, rather than price alone.


<iframe src="assets/year_scroll.html" width=800 height=600 frameBorder=0></iframe>


### D. Count of Wines by Country and Grape Type


Another area of interest we investigated is the grape varietals across different countries. We went about this through creating a stacked bar chart with the count of the grape varietals included in the dataset [Methods 1E]. Italy had the most wines in the dataset and many of them were the varietal Sangiovese. There were also many Shiraz wines from Spain represented in the dataset. An interesting avenue of investigation would be taking the written reviews from the dataset and performing natural language processing to determine if there is a noted difference in the language used to describe these different wines. However, we decided to seek out another dataset with chemical properties of wine to more specifically address our aims. 

<iframe src="assets/bar_grape.html" width=800 height=600 frameBorder=0></iframe>

### E. Feature Importance Comparison for Red and White Wine

Thus, we found another dataset with more specific wine properties and quality ratings. Each wine sample was evaluated by certified wine experts, who assessed these various sensory characteristics. This dataset has 12 sensory/chemical properties and a quality score measured from 6,497 wines from Portugal. Of the 6,497 wines, 1599 of them were red and 4898 were white. They were rated on a quality score from 1 - 9. In a similar approach to the larger reviews dataset, we first looked at the distribution of scores across both the red and white wines. Though there were many more white than red wines in this dataset, the distribution of the scores between the two colors were similar. The average quality score for white wines was 5.89 and the average quality score for red wines was 5.63 [Methods 2A]. Given these averages, we wanted to separately assess which sensory-chemical qualities were the most influential in determining these scores.

	
The dataset was divided by wine type, with separate feature matrices (Xred and Xwhite) for red and white wines. The features in the dataset were physiochemical attributes relevant to wine quality: alcohol, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, and sulfates. The target variable for both wine types was the quality score assigned by expert ratings. 

 
A Decision Tree Regressor model was chosen to analyze feature importance. The decision tree algorithm was selected for its interpretability and ability to capture nonlinear relationships without requiring extensive parameter tuning. The models calculate the feature importance by assessing the contribution of each feature in reducing mean squared error across splits in the tree structure. The Decision Tree Regressor models were trained on the red and white wine datasets independently. After training, the feature importance for each physicochemical attribute was extracted, feature importance is typically calculated based on the sum of reductions in mean squared error attributed to each feature. The greater the reduction in error when a feature is used in a split, the higher its importance score. The feature importances for each wine type were then compiled into one dataframe and visualized to highlight key differences in predictors of quality between red and white wines [Methods 2B]. 
	

An interactive bar chart was generated to facilitate comparison of feature importances between red and white wines. This visualization displays the relative significance of each feature, providing insights on how these properties differentially influence quality ratings by wine type. By training separate models and plotting feature importance for each wine type, we can interpret specific drivers of quality in red versus white wines, thereby informing production and quality assessment practices based on physiochemical characteristics. This visualization highlights how certain attributes, like alcohol content, may contribute differently to the perceived quality in red versus white wines. 


<iframe src="assets/feature_quality.html" width=800 height=600 frameBorder=0></iframe>

## IV. Conclusion

This study provides a comprehensive understanding of the factors influencing wine ratings, including regional variations, grape varietals, and chemical compositions. Our analysis shows that commonly used descriptors like "taste," "palate," and "fruity" are linked to higher ratings, with most reviews falling between 3 and 4.6, averaging close to 4.6. Additionally, regional trends suggest that wines with higher alcohol content, particularly from the United States and Portugal, tend to receive lower ratings than those from regions like South Africa and Argentina, hinting at a preference for wines with moderate alcohol levels.

Examining grape varietals reveals distinct national associations, such as Italy’s focus on Sangiovese and Spain’s on Shiraz. This observation opens possibilities for future research on how review language may reflect cultural or regional biases associated with specific varieties. Using a Decision Tree Regressor model on a dataset of chemical properties, we further explored how characteristics like alcohol content, acidity, and sugar levels affect quality scores in red versus white wines. This model-based approach confirms the significance of chemical properties in quality assessment and identifies distinct predictors for each wine type, particularly highlighting the role of alcohol.

These findings underscore the complexity of wine quality assessment by integrating consumer reviews with chemical analysis. Combining both perspectives, this research offers practical insights for producers, marketers, and wine enthusiasts, presenting data-driven recommendations to enhance wine quality and consumer satisfaction.

## V. References

Citations generated using ChatGPT
Data Packages
Pandas
McKinney, W. (2010). Data Structures for Statistical Computing in Python. Proceedings of the 9th Python in Science Conference, 51–56. DOI: 10.25080/Majora-92bf1922-00a

NumPy
Harris, C. R., Millman, K. J., van der Walt, S. J., et al. (2020). Array Programming with NumPy. Nature, 585(7825), 357–362. DOI: 10.1038/s41586-020-2649-2

SciPy
Virtanen, P., Gommers, R., Oliphant, T. E., et al. (2020). SciPy 1.0: Fundamental Algorithms for Scientific Computing in Python. Nature Methods, 17, 261–272. DOI: 10.1038/s41592-019-0686-2

Statsmodels
Seabold, S., & Perktold, J. (2010). Statsmodels: Econometric and Statistical Modeling with Python. Proceedings of the 9th Python in Science Conference, 92–96. DOI: 10.25080/Majora-92bf1922-011

Scikit-learn
Pedregosa, F., Varoquaux, G., Gramfort, A., et al. (2011). Scikit-learn: Machine Learning in Python. Journal of Machine Learning Research, 12, 2825–2830. URL: http://jmlr.org/papers/v12/pedregosa11a.html

Seaborn
Waskom, M. L. (2021). Seaborn: Statistical Data Visualization. Journal of Open Source Software, 6(60), 3021. DOI: 10.21105/joss.03021

Plotly
Plotly Technologies Inc. (2015). Collaborative Data Science. Montreal, QC. URL: https://plotly.com

Matplotlib
Hunter, J. D. (2007). Matplotlib: A 2D Graphics Environment. Computing in Science & Engineering, 9(3), 90–95. DOI: 10.1109/MCSE.2007.55

API Data-Pulling and Miscellaneous
Ucimlrepo
Ucimlrepo. GitHub Repository. URL: https://github.com/amitkaps/ucimlrepo

Pillow (PIL)
Clark, A. (2015). Pillow (PIL Fork) Documentation. URL: https://pillow.readthedocs.io

WordCloud
Mueller, A. (2012). WordCloud. GitHub Repository. URL: https://github.com/amueller/word_cloud

Warnings (Standard Library)
Python Software Foundation. (2023). Python Standard Library - warnings. URL: https://docs.python.org/3/library/warnings.html

OS (Standard Library)
Python Software Foundation. (2023). Python Standard Library - os. URL: https://docs.python.org/3/library/os.html
https://python-graph-gallery.com/

P. Cortez, A. Cerdeira, F. Almeida, T. Matos and J. Reis. Modeling wine preferences by data mining from physicochemical properties. In Decision Support Systems, Elsevier, 47(4):547-553, 2009.

Bender, T., Sørensen, S. M., Kashani, A., Hjorleifsson, K. E., Hyldig, G., Hauberg, S., Belongie, S., & Warburg, F. (2024). Learning to Taste: A Multimodal Wine Dataset. arXiv. https://arxiv.org/abs/2308.16900


