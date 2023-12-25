---
layout: post
title: Machine Learning Concepts
published: false
---

Machine Learning Concepts

## Bag of Words

* Dot product of columns of a matrix, the greater the dot products the more likely are the rows.
* cosine similarity: Similar to dot product except $$\cos(\theta) = \frac{{\bf a} \cdot {\bf b}}{\vert \vert {\bf a} \vert \vert \cdot \vert \vert {\bf b} \vert \vert}$$ is used.

## TF-IDF
<!-- (Reference: Part 07-Module 01-Lesson 01_Introduction to NLP) -->

* Limitations of bag of word is that it treats every word to be equally important. Cost and Price are common terms for example in a one file.
* In TF-IDF, we can add final row called document frequency. If the same header of one column appears 3 times, the we divide every row in that column by 3. This highlights words that are more unique to the document than others, for example if one column have only one word we get $$1/1 = 1$$ if another column have 3 words we get $$1/3$$ which is less, so it is easier to characterize the words that have 1.
* We have the TF-IDF transform: $$tfidf(t,d,D) = tf(t,d) \cdot idf(t,D)$$. The first term $$tf(t,d)$$ is called term frequency, the second one $$idf(t,D)$$ is called inverse document frequency.
* Term frequency: $$tf(t,d) \rightarrow count(t,d) / \vert d \vert$$.
* Inverse document frequency: $$\log(\vert D \vert / \vert \{d \in D \, : \, t \in d\})$$

## One-Hot Encoding

* Treat each word as a class

## Word Embeddings

## Word 2 Vec

* One of the most popular examples in word embeddings.
* Model that is able to predict a given word giving neighbouring words or viseversa. Predict neighboring words for a given word is likely to capture the contextual meaning of words very well.
* Continuous bag of words (CBoW)
* Continuous Skip-gram
* Skip-gram model
* * Convert any word and convert it into a one hard coded vector $$w_t$$ and feed it into a neural network or other probabilistic model that is designed to predict the surrounding words ($$w_{t-2}$$, $$w_{t-1}$$, $$w_{t+1}$$...).
* * Word vector can be a hidden layer in the neural network.
* * Robust and distributed through out each vector, size of the word vector is up to you (independent of vocabulary), once we pretrain large set of word vectors, they can be used efficiently without having to transform again and again and again just store the training data in a lookuptable. It is ready to be used in a deep learning architecture. It can be used as an input vector into neural nets. It is also possible to use RNNs to learn even better word embeddings. Also possible to use hierarchical softmax, sparse cross entropy

## GloVe (Global Vectors for Word Representation)

* $$P(j \vert i)$$ which means p of j given i
* We can have word i and word j, either is word i next to j or further away.
* We normalize the count to get probability
* We have random vectors for rows and columns. Random row vectors called context and random column vectors called target.
* For any pair of i j we want the dot product of their word vectors $$w_i$$ and $$w_j$$ to be equal to their cooccurance probability. Using this and a loss function, we can itteratively optimize these word vectors, the result should be a set of vectors that capture the similarity and differences between individual word.
* We are actually factorizing the main matrix into two matrices.

Why co-occurence probability?

Consider two context words and two target words.

* Better to use log

## Embedding for Deep Learning

* Distributional Hypothesis: woman - man + king = queen
* Tea and Coffee are very similar words in a way thay are used very often in similar sentences.
* Words can be close in one dimension but sepparated in another dimension.

## Modeling

* About designing a statistical or machine learning model, fitting the parameters to a training data using an optimization procedure, then using it to make predictions about unseen data.
* The nice thing about working with numerical feature is it allows you to utilize almost any maachine learning model.
* * Support Vector machines
* * Decision trees
* * Neural networks
* Its up to you how you use it.

