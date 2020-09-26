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


# 第七周总结

1. 首先我用PCA的方法将上周获取的title matrix做了处理，让size统一为(3,50)。
2. 然后使用Keras的LSTM unit搭建了一个encoder-decoder模型，或者叫seq2seq模型。
3. 根据原有的citation关系，构建了训练集还有测试集。
4. 训练模型，将原有的title matrix，变成新的带有citation部分信息的predict matrix
5. 最后和之前一样，构建distance matrix，最后提取其中一篇论文，看效果如何。

## 存在的问题还有改进的方向

我构建LSTM模型的想法是，希望让原有的简单title matrix学习到citation的部分信息和单词之间的关联。最后用新的predict matrix构建了新的distance以后，我打算看看效果如何，结果发现使用新的distance，找到的和paper 2554最相关的10篇paper仍然和之前的差不太多，有些只是顺序稍微调整了一下。

这种现象说明了，原有词向量对最后结果的影响非常大，所以我打算下一次根据每一篇文章的abstract，训练新的词向量，这是目前我能想到的比较好的改进，同时这个方法可以解决之前有些单词没有对应词向量的情况。