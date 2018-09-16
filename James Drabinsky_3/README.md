# Distinguishing Between Cordcutters and Piracy Subreddits


### The Opener

In recent years traditional cable and satellite TV have been in decline as viewers transition to consuming content from Subscription Video on Demand (SVoD) services like Netflix and Hulu.  This trend will likely continue as the number of cord-cutters in the U.S. (consumers who have ever cancelled traditional pay-TV service and do not resubscribe) will rise to 33 million adults this year.  Along with this rise in cord-cutters, there has also been an increase in subscriptions to illicit streaming services.  Worldwide, users made a total of 300 billion visits to internet piracy sites in 2017.

### The Need

Given the shift in consumers viewing habits and the proliferation of pirated streaming content, a study and comparison of the piracy and cordcutters subreddits could provide SVoD companies insight into the type of content that is being pirated from their services.  An evaluation of the intersecting and divergent elements between the two subreddits could potentially influence future content delivery methods and programming decisions these media companies..  Taking all this into account, I will build a machine learning model predicting whether a given post comes from either the piracy or cordcutter subreddits.  Using this model, streaming services can look at the overlapping features of these two subreddits and potentially discover reasons why consumers are pirating content and what type of content they are watching.   

### Outline
1. Data collection/Processing
	> I obtained 933 posts from the cordcutters subreddit and 634 posts from the piracy subreddit. The posts were dumped into a Data folder as json files.  I converted the json files into dataframes and concatenated the two subreddit dataframes. I then created a boolean column in which all cordcutter posts were assigned a 1 and all piracy posts were assigned a 0.  The 'title' and 'selftextxt' columns were cleaned using regex to remove any numbers, punctuation and notation and all text was made lower case.  
2. EDA
    	> I put the text through a count vectorizer since the models require all the inputs to be numeric. During vectorization, I also removed stop words and punctation 	by adding a custom list with 258 stop words to the parameters.  I then plotted the top 20 words in each subreddit and the top 20 overlapping words grouped by the 	sum of the terms in each subreddit.  I then conducted a hypothesis test to get a list of the statistically significant words that occur in both classes and, finally, I plotted the distributions of the highest frequency overlapping words.
3. Modeling
	> I trained four classifiers to predict which subreddit a given post came from : Multinomial Naive Bayes, Logistic Regression, Decision Tree, and Random Forest. 	To compare model strength, I used 2 metrics: test score and ROC AUC:


### Results

| Model                   | Test Score |  ROC AUC 
|-------------------------|------------|----------
| Multinomial NB          | 0.936      | 0.988       
| Logistic Regression     | 0.946      | 0.987        
| Random Forest           | 0.911      | 0.978        
| Random Forest           | 0.842      | 0.880       
   

4. Summary and Conclusions
	> I chose the Logistic Regression Model because of its high test and ROC AUC score.  My analysis recognizes the intersecting words between the two subreddits and identifies the statistically significant words in both classes. This would benefit a SVoD company because using this data it can draw links between what cordcutters are watching and what is being pirated and adjust their decision-making accordingly.  
