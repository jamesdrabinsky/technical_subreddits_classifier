# Distinguishing Between Cordcutters and Piracy Subreddits
_By James Drabinsky_


### The Opener

In recent years traditional cable and satellite TV have been in decline as viewers transition to consuming content from Subscription Video on Demand (SVoD) services like Netflix and Hulu.  This trend will likely continue as the number of cord-cutters in the U.S. (consumers who have ever cancelled traditional pay-TV service and do not resubscribe) will rise to 33 million adults this year.  Along with this rise in cord-cutters, there has also been an increase in subscriptions to illicit streaming services.  Worldwide, users made a total of 300 billion visits to internet piracy sites in 2017.

### The Need

Given the shift in consumers viewing habits and the proliferation of pirated streaming content, a study and comparison of the piracy and cordcutters subreddits could provide SVoD companies insight into the type of content that is being pirated from their services.  An evaluation of the intersecting and divergent elements between the two subreddits could potentially influence future content delivery methods and programming decisions of these media companies.  Taking all this into account, I will build a machine learning model predicting whether a given post comes from either the piracy or cordcutter subreddits.  Using this model, streaming services can look at the overlapping features of these two subreddits and potentially discover reasons why consumers are pirating content and what type of content they are watching.   

### Outline
1. [Data Acquisition/Processing](./Notebooks/1_Data_Acquisition_Processing.ipynb)
	> I obtained 932 posts from the cordcutters subreddit and 718 posts from the piracy subreddit. The posts were dumped into a Data folder as json files.  I converted the json files into dataframes and concatenated the two subreddit dataframes. I then created a boolean column in which all cordcutter posts were assigned a 1 and all piracy posts were assigned a 0.  The 'title' and 'selftext' columns were cleaned using regex to remove any numbers, punctuation and notation and all text was made lower case.  
2. [EDA](./Notebooks/2_EDA.ipynb)
	> I put the text through a count vectorizer since the models require all the inputs to be numeric. During vectorization, I also removed stop words and punctation by adding a custom list with 258 stop words to the parameters.  I then plotted the top 20 words in each subreddit and the top 20 overlapping words grouped by the sum of the terms in each subreddit.  I then conducted a hypothesis test to get a list of the statistically significant words that occur in both classes and, finally, I plotted the distributions of the highest frequency overlapping words.
3. [Modeling/Analysis](./Notebooks/3_Modeling_Analysis.ipynb)
	> I trained four classifiers to predict which subreddit a given post came from : Multinomial Naive Bayes, Logistic Regression, Decision Tree, and Random Forest.  I used gridsearch to configure optimal parameters for each model and I plotted out different combinations of parameters to get a visual sense of how the parameters were affecting the scores. To compare model strength, I used 2 metrics: accuracy and ROC AUC -



### Results

| Model                   | Accuracy   | ROC AUC 
|-------------------------|------------|----------
| Multinomial NB          | 0.939      | 0.988      
| Logistic Regression     | 0.932      | 0.983       
| Random Forest           | 0.886      | 0.959        
| Decision Tree           | 0.809      | 0.895      
   


4. Summary and Conclusions
	> I would choose between the logistic regression model and the naive Bayes model.  Both have high accuracy and ROC-AUC scores, but the logistic regression model was more computationally taxing because of its gridsearch parameters.  

	> By looking at the coefficients and feature importance after vectorization, and by finding the statistically significant words with a t-test, I was able to identify lists of words which were suggestive of one class or the other.  I was able to use these lists in my analysis to better understand why the models were misclassifying certain posts.  This would benefit SVoD companies because through the use of this data they can draw links between the content that cordcutters are watching and what is being pirated.  With this knowledge they can make better-informed decision and adjust their future business strategy.