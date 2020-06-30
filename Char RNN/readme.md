# Character Level RNN (Char RNN)
These are the most basic form of recurrent neural networks and we have implemented them from scratch. Also, we have used the RNN, LSTM and GRU layers available in PyTorch for comparison.

All the models are  trained on the [*Dino_Names.txt*](https://github.com/IvLabs/Natural-Language-Processing/raw/master/Datasets/Dino_Names.txt) dataset which contains 1536 dinosaur names. Data splitting and training parameters are mentioned below.

<center>

| Training Parameter |      Value      |
| ------------------ |:---------------:|
| Training Set       | 98% (1506/1536) |
| Validation Set     |  2% (30/1536)   |
| Number of Epochs   |       50        |
| Learning Rate      | 10<sup>-3</sup> |
| Hidden Dimensions  |       32        |

</center>

## Dinosaur Names from Scratch [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1N01IvqI0yxK1CAKi0cfwRTcgvR-_YukL?authuser=1#forceEdit=true&sandboxMode=true)
This notebook implements a vanilla RNN, right from scratch using only basic linear layers and activation functions. This notebook aims at deepening the understanding and general implementation paradigm for recurrent nerual networks. It covers every step, right from data preprocessing to sampling from the trained model, using only basic Python and PyTorch functionalities.
