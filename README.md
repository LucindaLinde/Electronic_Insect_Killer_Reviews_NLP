# Electronic_Insect_Killer_Reviews_NLP
Product Reviews contain valuable information about which product flaws cause negative reviews. Natural Language Processing of these reviews reveals patterns based on thousands of reviews and results in a prioritized list. Product managers can therefore spend their scarce resources fixing the most impactful problems.

A recent McKinsey article shows that improving product ratings from 3 stars to 4 stars can raise revenues between 20 to 70% across product categories 1.

Bad product reviews contain valuable information about which product failings cause 1, 2 and 3 star reviews.   Applying Natural Language Processing (NLP) machine learning to thousands of reviews can yield a prioritized list of product attributes to fix.

During a recent project, I applied NLP to the Amazon Reviews for a company’s product. To illustrate the insights, this article uses instead, the massive publicly available reviews data set updated by Jainmo Ni (https://nijianmo.github.io/amazon/index.html#subsets ) which contains over 233 million reviews across product categories from 2000 to 2018 2.

To narrow things down, I looked at the Lawn Patio Garden category and specifically at one Electronic Insect Killer product that had an average rating of 4.1 stars across 8166 reviews. There were 6252 Positive Reviews (4 or 5-star ratings) and 1914 Negative Reviews (1, 2 or 3-star ratings). 

Summary of NLP Approach

For Data Scientists, here’s the approach taken:
•	Model built using Python 3 and scikit-learn, NLTK packages
•	Load and merge the two product data sets for the Electronic Insect Killer product
•	Keep only the ‘review’, ‘summary’ and ‘rating’ columns
•	Preprocess the text 
    o	Combine the review and summary text fields
    o	Make text lower case, take out common words (like ‘the’), take out words with 3 or fewer characters, ignore special characters, tokenize the words
•	Use TFIDF vectorizer to make the words processable by machine learning algorithms 
•	Look at groups of 2, 3 and 4 consecutive words (n-grams); not single words
•	Apply Random Forest algorithm to predict if the review is a Positive Review (4 or 5 stars) or a Negative Review (1, 2 or 3 stars)
    o	Train model on 75% of the data, have model make predictions on 25% of the data 
    o	Model predicted pretty well; AUC = 0.86, overall accuracy = 0.82.
    o	Recall of predicting a Positive Review was 0.99 but Recall of predicting a Negative Review was only 0.27.  
•	Look at the 200 most influential word groups that are predictive of a positive or negative review. 
    o	Manually pick out the groups of words that look like they deal with product flaws. For this article, I focused on the bulb because it showed up 4 times within the top 26 word-combinations.
    o	Manually scan the subset of reviews that deal with the bulb to understand more about the context. 
•	Put together cross-functional action plan to address the product attribute that makes customers so unhappy. 
