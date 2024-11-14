# Wine Quality Analysis

<p style="font-family: 'Times New Roman', Times, serif;">
The first dataset, from Bender et al. (2024), includes data from 824k reviews of wines from the Vivino platform. The reviews for wine include a picture of the label, a rating from the user on a scale of 1 to 5, and an explanation of the rating or any comments regarding the flavor of the wine. Some of the more commonly used words in these reviews include taste, palate, nose, hint, fruity, full-bodied, drink, and sweet. Upon first glance, these words appear to be neutral to positive in sentiment, so we then investigated what kind of rating these reviews are associated with. The distribution of ratings ranges from 3 to 4.6, with an average rating of approximately 4.6. The positive sentiment of the most frequently used words were reflected in average ratings close to 5. 
</p>

<iframe src="wine.html" width=800 height=600 frameBorder=0></iframe>

<p style="font-family: 'Times New Roman', Times, serif;">
Each review is associated with a label, which contains a wealth of information including the origin of the wine, the year it was bottled, the alcohol content, and other attributes. To get an idea of any areas with relatively higher or lower ratings, we looked into the ratings by country and alcohol content. The ratings ranged from 4 to 4.3, with the highest ratings coming from South Africa [4.3, NA%] and Argentina [4.25, 13.23%], and the lowest coming from the United States [3.99, 13.99%],  and Portugal [4, 14.61%].  It is worth noting that the lower rated wines appear to have slightly higher alcohol content. However, the data from these reviews give no indication regarding the origin of the reviewer, and are ultimately subjective. It could be the case that people in the lower rating countries tend to rate things lower, but we cannot know from this dataset.
</p>
<iframe src="globe_map.html" width=800 height=600 frameBorder=0></iframe>

<iframe src="year_scroll.html" width=800 height=600 frameBorder=0></iframe>

<iframe src="bar_grape.html" width=800 height=600 frameBorder=0></iframe>

<p style="font-family: 'Times New Roman', Times, serif;">
Thus, we found another dataset with more specific wine properties and quality ratings. Each wine sample was evaluated by certified wine experts, who assessed these various sensory characteristics. This dataset has 12 sensory/chemical properties and a quality score measured from 6,497 wines from Portugal. Of the 6,497 wines, 1599 of them were red and 4898 were white. They were rated on a quality score from 1 - 9. In a similar approach to the larger reviews dataset, we first looked at the distribution of scores across both the red and white wines. Though there were many more white than red wines in this dataset, the distribution of the scores between the two colors were similar. The average quality score for white wines was 5.89 and the average quality score for red wines was 5.63. Given these averages, we wanted to separately assess which sensory-chemical qualities were the most influential in determining these scores.

	
The dataset was divided by wine type, with separate feature matrices (Xred and Xwhite) for red and white wines. The features in the dataset were physiochemical attributes relevant to wine quality: alcohol, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, and sulfates. The target variable for both wine types was the quality score assigned by expert ratings. 

 
A Decision Tree Regressor model was chosen to analyze feature importance. The decision tree algorithm was selected for its interpretability and ability to capture nonlinear relationships without requiring extensive parameter tuning. The models calculate the feature importance by assessing the contribution of each feature in reducing mean squared error across splits in the tree structure. The Decision Tree Regressor models were trained on the red and white wine datasets independently. After training, the feature importance for each physicochemical attribute was extracted, feature importance is typically calculated based on the sum of reductions in mean squared error attributed to each feature. The greater the reduction in error when a feature is used in a split, the higher its importance score. The feature importances for each wine type were then compiled into one dataframe and visualized to highlight key differences in predictors of quality between red and white wines. 
	

An interactive bar chart was generated to facilitate comparison of feature importances between red and white wines. This visualization displays the relative significance of each feature, providing insights on how these properties differentially influence quality ratings by wine type. By training separate models and plotting feature importance for each wine type, we can interpret specific drivers of quality in red versus white wines, thereby informing production and quality assessment practices based on physiochemical characteristics. This visualization highlights how certain attributes, like alcohol content, may contribute differently to the perceived quality in red versus white wines. 
</p>

<iframe src="feature_quality.html" width=800 height=600 frameBorder=0></iframe>

https://python-graph-gallery.com/

https://archive.ics.uci.edu/dataset/186/wine+quality

https://thoranna.github.io/learning_to_taste/
