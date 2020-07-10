# Character Level RNN (Char RNN)
The fundamental basis of any language is its alphabet. Hence character level RNN(s) are the most basic form of recurrent neural networks and we have implemented them from scratch. Also, we have used the RNN, LSTM and GRU layers available in PyTorch for comparison.

All the models are  trained on the [*Dino_Names.txt*](https://github.com/IvLabs/Natural-Language-Processing/raw/master/datasets/Dino_Names.txt) dataset which contains 1536 dinosaur names. Data splitting and training parameters are mentioned below.


| Parameter         |       Value        |
| ----------------- |:------------------:|
| Training Set      |  95% (1460/1536)   |
| Testing Set       |    3% (46/1536)    |
| Validation Set    |    2% (30/1536)    |
| Number of Epochs  |         40         |
| Learning Rate     | 4x10<sup>-4</sup>  |
| Hidden Dimensions |         64         |
| Loss Function     | Cross Entropy Loss |
| Optimizer         |       AdamW        |

<br>

## General Pipeline
1. Every character in the vocabulary(including the delimiter ".") is embedded using One-Hot vector representation.
2. A sequence of embeddings is fed to the model. This typically contains embeddings of all the characters of a word, except the delimiter.
3. The output of the model is validated against the ground truth, i.e. a sequence of embeddings of all the characters of the word (including the delimiter) except the first.
4. The training and validation losses are calculated and stochastic optimization is applied. 
5. This is repeated for every word in the corpus.
6. The cumilitive training and validation losses for each epoch are recorded and plotted.

<br>

## Architectures:
### 1. Char RNN from Scratch [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1N01IvqI0yxK1CAKi0cfwRTcgvR-_YukL?authuser=1#forceEdit=true&sandboxMode=true)
This notebook implements a vanilla RNN, right from scratch using only basic linear layers and activation functions. This notebook aims at deepening the understanding and general implementation paradigm for recurrent nerual networks. It covers every step, right from data preprocessing to sampling from the trained model, using only basic Python and PyTorch functionalities.

### 2. Char RNN using Vanilla RNN Layer [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1POL4Hjr-jATbmJLEhfGqcUhKNB6XYHHp?authuser=1#scrollTo=I9-KnRCAkFWj&forceEdit=true&sandboxMode=true)
This architecture employs the Vanilla RNN Layer available in PyTorch instead of writing the entire RNN model from scratch. This makes the model atleast 4 times faster owing to the optimized data-flow design of PyTorch's inbuilt layers. The increment in performance, is quite nominal due to the general drawbacks of Vanilla RNN models like vanishing gradients and short temporal memory spans.

### 3. Char RNN using LSTM Layer [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1lj7S2NaPa55rS-3X4yWlMj3-dy1EPEne?authuser=1#forceEdit=true&sandboxMode=true)
In this notebook, we implement a single layered Long Short Term Memory (LSTM) network using PyTorch's inbuilt LSTM Layer. This network has more than 3 times more parameters than the Vanilla RNN. The final convergent loss does not change a lot but the results of sampling seem to make a lot more sense, i.e. appear to be closer to natural language and sound more sensible or natural.

### 4. Char RNN using GRU Layer [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1KHngbDPUXEpSyl1HfbIFeNwkun5ssZsK?authuser=1#scrollTo=aIQUjAXtmFRD&forceEdit=true&sandboxMode=true)
The final notebook in the comparison, uses Gated Recurrent Units (GRU) which are a more computationally efficient version of the LSTM units. The number of trainable parameters is almost 2.5 times that of the equivalent Vanilla RNN, but the performance is often at par with the LSTM network. This makes them a friendlier choice for large scale deployment.

<br>

## Summary
Below is a table, summarising the number of parameters and the convergent loss achieved by each model.

  | Architecture     | No. of Learnable Parameters | Training Loss | Validation Loss | Test Loss |
  | ---------------- |:---------------------------:|:-------------:|:---------------:| :-------: |
  | RNN from scratch |            10856            |    2.0110     |     1.8492      |  1.7026   |
  | Vanilla RNN      |            7707             |    1.8576     |     1.6835      |  1.5294   |
  | LSTM             |            25563            |    1.7426     |     1.6065      |  1.4923   |
  | GRU              |            19611            |    1.7202     |     1.5082      |  1.3935   |


<br>

## Plots
<p align="center">
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/char_rnns/plots/Dino_Names_Scratch.jpeg?raw=true"/>
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/char_rnns/plots/Dino_Names_RNN.jpeg?raw=true"/> 
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/char_rnns/plots/Dino_Names_LSTM.jpeg?raw=true"/>
  <img src = "https://github.com/IvLabs/Natural-Language-Processing/blob/master/char_rnns/plots/Dino_Names_GRU.jpeg?raw=true"/>
</p>

<br>

### Note:
In the notebooks (all except RNN from scratch), a parameter named "NUM_LAYERS" can be changed to change the number of stacked layers in the model. However, keeping in mind the miniscule amount of data available and the meagrely small objective at hand, using multi-layer architectures seems futile as the trade-off between performance and required computation, tilts more towards the computationally heavy side.
