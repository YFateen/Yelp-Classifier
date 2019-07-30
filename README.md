# Predicting Yelp Review Ratings with Spark

Used the MapReduce programming paradigm to parallelize a simple Naive Bayes classifier with a Bag of Words model in Spark to predict Yelp review ratings.

This was achieved in three main stages.

### Training 
I calculated the likelihood of a word occuring in reviews of each possible number of stars: 
P(word | num_stars) = (1 + # of times word appears in reviews with num_stars) / (1 + # of words total in reviews with num_stars) I did this for every word that occurs in the group of reviews with num_stars, for all possible number of stars.

### Training 2
I calculated the prior probability of a review with num_stars occuring, for all possible numbers of stars: P(num_stars) = # of reviews with num_stars / # of reviews total.

### Classification
Given a review (word1, word2, word3,...), for all possible numbers of stars, I calculated the joint probability P(num_stars, word1, word2, word3...) = P(num_stars) P(word1|num_stars) P(word2|num_stars) P(word3|num_stars).... The prediction for the number of stars for the review is then the num_stars that has the highest joint probability.
