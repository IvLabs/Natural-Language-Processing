# Sentiment Analysis and Text Classification

With the advent rise of digitization, the need to automate the analysis of the predominant method of interacting with the digital world, i.e. text, has exponentially risen for a variety of reasons and purposes.

Text classification is heavily used in tasks such as spam detection, news categorization, customer query tagging, and of course, sentiment analysis.

Sentiment analysis is the automated process of determining the polarity of a topic, given an input sentence.
It is used in tasks such as analyzing a product/company's public sentiment/word of mouth, customer feedback analysis, political analysis, etc.

We experiment with 4 architectures on two datasets. The IMDb dataset was to used to train the model for predicting the polarity of movie reviews. For text classification, the TREC dataset was used to train the model to predict one of six classes - `['ENTY', 'HUM', 'DESC', 'NUM', 'LOC', 'ABBR']`.


Below is a table addressing some common data and optimization related parameters.

| Parameter      |       Value        |
| -------------- |:------------------:|
| Training Set   |     17500          |
| Testing Set    |     25000          |
| Validation Set |     7500           |
| Loss Function  | Cross Entropy Loss |
| Optimizer      |       Adam         |

## Architectures

### [1. Long Short-Term Memory Networks](https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/LSTM.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/LSTM.ipynb)
RNNs were one of the first architectures for capturing sequential data on various tasks such as predicting parts of speech, sentiment analysis, text classification, etc. However, RNNs suffers from a vanishing gradient problem that make them unable to propagate useful gradient information, thereby causing the model not to learn from larger contexts. To overcome this problem, LSTMs were introduced, which are a modified form of the RNN.

### [2. Bag of Tricks for Efficient Text Classification](https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/FastText.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/FastText.ipynb)
This paper shows that tweaking baseline linear classifiers enables us to learn an efficient and accurate text classifier for a very large corpus with a large output space (whereas deep networks would be very slow). Sentences being represented by BoW and trained by improved linear models (like logistic regression or SVM) with a rank constraint and a fast loss approximation are shown to achieve performance on par with the state-of-the-art.

### [3. Convolutional Neural Networks for Sentence Classification](https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/CNN.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/CNN.ipynb)
CNNs trained on top of pre-trained word vectors for sentence-level classification tasks are shown to achieve excellent results on multiple benchmarks.
The underlying idea strengthened here is that feature extractors obtained from a pre-
trained deep learning model perform well on a variety of tasks—including tasks that are very different from the original task for which the feature extractors were trained.

### [4. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/BERT.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/IvLabs/Natural-Language-Processing/blob/master/text_classification/notebooks/BERT.ipynb)
BERT is designed to pre-train deep bidirectional representations from unlabeled text by jointly conditioning on both left and right context in all layers. As a result, the pre-trained BERT model can be fine-tuned with just one additional output layer to create state-of-the-art models for a wide range of tasks, without substantial task-specific architecture modifications.

## Summary
Below is a table, summarising the number of parameters and the train, test, validation accuracies.

| Architecture | No. of Learnable Parameters | Train Acc. (%) | Valid. Acc. (%) | Test Acc. (%) |
| ------------ | --------------------------- | -------------- | --------------- | ------------- |
| LSTM         | 4,810,857                   | 89.10          | 88.37           | 87.62         |
| FastText     | 2,500,301                   | 88.35          | 86.67           | 86.28         |
| CNN          | 843,906                     | 94.95          | 79.89           | 84.90         |
| BERT         | 110,468,609                 | 91.04          | 91.04           | 91.44         |

## Plots
<p align="center">
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/plots/LSTM.png?raw=true"/>
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/plots/FastText.png?raw=true"/> 
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/plots/CNN.png?raw=true"/>
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/text_classification/plots/BERT.png?raw=true"/>
</p>

## Reference(s)
* [PyTorch Sentiment Analysis by Ben Trevett](https://github.com/bentrevett/)

