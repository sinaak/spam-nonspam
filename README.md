# spam-nonspam
spam non spam email classification


This assignment aims to predict for each email whether it is legitimate or spam. First thing to do is to read the data. Reading data is done in ”reading data.ipynb” file. All the 9688 spam emails are read, their subjects and bodies are separated and each listed in a list. Then a data frame is constructed with 3 columns: Subject, Body and Label.

## Preprocessing

In preprocess function, data is a bit cleaned for example ”’s”, ”/”,” -”, ”‘”, digits and punctu- ations except ”?” and ”!” are removed and the string is converted to the lower case.
Stop words are the words we want to filter out before training the classifier. These are usually high frequency words that are not giving any additional information to our labeling. In fact, they actually confuse our classifier. In English, they could be the, is, at, which, and etc.
Stemming is the process for reducing inflected words to their word stem (base form). As an example, the classifier does not understand that the verbs ”investing” and ”invested” are the same, and treats them as different words with different frequencies. By stemming them, it groups the frequencies of different inflection to just one term in this case, ”invest”. In stemming process only the word’s stem is left so it reduces the total variety of words. All the words are tokenized, and after the above changes, listed words are put in a sentence with a space between each. This preprocessing is done on both Subject and Body. Using English stop words for cleaning our data brought up the idea to observe the frequency of different languages in the emails. As shown below, most of the emails are in English.

## Features

The bag-of-words model is commonly used in methods of document classification where the
(frequency of) occurrence of each word is used as a feature for training a classifier. BoW is
one of the basic and most commonly used methods for document representation due to its
simplicity. It is essentially an algorithm that forms a vector by counting how many times each
word appears in the document. It is needless to mention that Bag-of-words suffers from several
limitations, for instance, it fails to capture relationships between words since it deals with
each word individually. It also suffers from high dimensionality of representation and sparsity.
A simple twist to BoW would be Tf-idf. Tf-idf stands for term frequency-inverse document
frequency. Tf-idf captures the importance of a word in a document so unlike BoW, it doesnt
emphasize a word more than its needed. The Tf-idf score (weight) of term t in plot p is given
by: wi,p = tfi,p × log N where tfi,p is the number of times i-th term has appeared in plot p. dfi
Since the naive representation of tfi,p causes bias towards long plots, as a given term has more chance to appear in longer plot, all wp values are normalized as ∥wp∥ = 1. dfi is the number of plots containing the i-th term and N is the total number of plots. We have also tried Tf-idf as a more sophisticated version of BoW.

We have a total amount of 102257 features. This high number of features is one of the downsides of using BoW. 102256 features are the unique words acquired from tf-idf and one column is for text length feature. 20 top features are depicted in the figure5. ”enron” has the most percentage then ”cc”, ”vinc” and ”hpl” respectively have more percent. Another feature that we looked into was the length of text. It appeared that spam emails are longer than non-spam emails.


## Training

The total number of emails including both inboxes and spams are 15766. We used 33% of it for test which will be 5203 emails. The remaining 77% of emails are used for training our model which will be 10563 emails. In logistic regression model we tuned various hyper parameters; c= 0.1, 1, 10, 30, 50. The accuracy of prediction with c=30 is the highest (0.978).
Prediction on our test dada has a high accuracy of 98%.


## Prediction

For three classes of 0 for non spam, 1 for spam and 2 for suspicious emails we want to predict the probability based on random Gaussian data.
