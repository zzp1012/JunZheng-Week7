# Keras LSTM

## Create Word Matrix

1. Using `Glove` algorithm to create word matrix for the titles of each paper
2. Then use `PCA` make every word matrix have the same size `(3,50)`

## Create Train/Validation Dataset

1. X and Y sets are created by citation relationship. if paper A is cited by paper B, then the X here is the word matrix of paper A and the Y is the word matrix of paper B.
2. Then we get X set with size `(5967, 3, 50)` and Y set with size `(5967, 3, 50)`.
3. Finaly, we shuffle the dataset and split the dataset into train set and validation set.

## Create Sequence Model

1. Use Keras LSTM to create a seq2seq model with input size `(batchsize, 3, 50) and the output size (batchsize, 3, 50)`

## Get Predict Matrix

1. We use our obtained train set and validation set to train the model.
2. Use the trained model to get a corresponding predict matrix for the word matrix of each paper, which have the size `(3,50)`. 

## Obtain Distance Matrix

1. Use the newly obtained predict matrix to create distance matrix as we do last week. 

## Performace of Word Embedding

- Select the 10 articles which has the most similar titles to paper `2554`
- Translate these titles of the 10 articles and compare their real meaning with the title of `2554`
- Find the articles which cited `2554` and articles which are cited by `2554`
- Compare these articles with the 10 articles
