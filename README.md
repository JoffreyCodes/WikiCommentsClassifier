# WikiCommentsClassifier

- [Video Presentation](#video-presentation)
- [Questions](#questions)

# Video Presentation

https://user-images.githubusercontent.com/78377396/184251882-e704ae35-073b-4937-a5ff-fb2a314fd936.mp4

# Questions

a. What text cleaning methods did you try? Which are the ones you included in the final code?

- Filter out stop words via TfidfVectorizer(stop_words='english')
- Lowercase all text
- Remove numbers
- Remove punctuations

b. What are the features you considered using? Which features did you use in the final code?

- Tried Unigrams, Bigrams, Both; analyzing words
- chars with ngram 1-5 but memory filled up; author suggested this was the best approach but I was not able to reproduce results.
- Stop words via TfidfVectorizer(stop_words='english')

c. How did you decide to use the ‘attack’ information from different annotators? Did you average them, or use a number threshold, or did you use some other method to use this information?

- Manipulating the labels mean() to be less than majority or greater than majority effected the f1 scores such that further deviation away from labels mean() > 0.5 resulted in decreasing the f1-score for correctly classifying nasty comments. However, increasing the threshold improves the f1-score for correctly classifying nice comments as "false" and ultimately improved thed weighted average f1 score. Therefore, I felt it more appropriate to maximize the correct classification for nast comments as this is more of the general purpose for this classifier.

d. What optimizations did you add in your code, if any?

- Removed comments before 2003, there were no recorded attacks; approximately 8 comments, did not significantly affect results whatsoever - Use of stopwords

e. What are the ML methods you tried out, and what were your best results with each method? Which was the best ML method you saw before tuning hyperparameters?

- LogisticRegression (Second best)
- MultinomialNB (Naieve Bayes)
- LinearSVC(Best results)
  Tuning hyperparameters for LinearSVC did not significantly improve my results.

f. What hyper-parameter tuning did you do, and by how many percentage points did your accuracy go up because of hyper-parameter tuning?

- A slight increase of 1% is seen in our True precision, but this could be from a randomized state computation of our data. Accuracy did not change from 0.94 overall.

g. What did you learn from the different metrics? Did you try cross-validation?

- From the metrics, it seems that our data strongly supports classifying nice comments. This makes sense since supporting comments(30k) are about 7x more evident than nasty comments(4k) in our processed and pipelined dataset. I was unable to try cross-validation, but I did try to implement a train_test_split using test = 0.3 and complimentary train = 0.7. The accuracy started at 0.91

h. What are your best final Result Metrics? What is the increase in accuracy compared to the strawman figure? Which model gave you this performance?

- My best final result metric was getting the True f1-score above 0.7 which started from the strawman True f1-score of 0.63. This was acchieved using LinearSVC with default parameters

i. What is the most interesting thing you learned from doing the report?

- I really enjoyed working in jupyter. It's particularly interesting how reports in jupyter literally feels like reading a journal entry or report, rather than code structures formatted in an IDE.

j. What was the hardest thing to do?

- Reading all the documentation for sklearn libraries. Theres so much to learn and improve!



