# Neural Machine Translation

The machine translation task was traditionally performed using statistical methods. However, like most statistical paradigms, this Statistical Machine Translation (SMT) had large computational and memory overheads.

With the popularization of neural networks and deep learning, heavy research into Neural Machine Translation (NMT) and its successful employment has largely replaced SMT. This section contains implementations of papers that introduced some of those ground-breaking architectures in NMT.

All the models were trained on the [Multi30k](https://arxiv.org/abs/1605.00459) dataset which contains roughly 30 thousand English, German and French sentences, each sentence being 10-20 words long. We have trained and evaluated our models for translation from German to English.

Below is a table addressing some common data and optimization related parameters.

| Parameter      |       Value        |
| -------------- |:------------------:|
| Training Set   |    29000/31014     |
| Testing Set    |     1000/31014     |
| Validation Set |     1014/31014     |
| Loss Function  | Cross Entropy Loss |
| Optimizer      |       AdamW        |

## Architectures

### 1. [Sequence to Sequence Learning with Neural Networks](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Seq2Seq.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QaoSKUbLy4ViHnJsl3m3H6xEemDdowkL?usp=sharing)
This paper proposes the pioneering paradigm for neural machine translation using a simple yet applaudable encoder-decoder RNN pair. Although being the poorest of performers in this list, it earns a spot due to its novely.\
**<ins>Note:</ins>** A few changes have been made in order to improve performance.
1. Unlike the paper, reversing the input sequences resulted in a lower BLEU Score. Hence, the input sequences have not been reversed.
2. Further an additional parameter called ```teacher_forcing_ratio```, which is the probability of using the ground truth tokens as inputs while decoding has been introduced. It is usually set to 1 while training and 0 while sampling. However, setting it to 0.5 while training resulted in a better BLEU Score than setting it to 1.

### 2. [Neural Machine Translation by Jointly Learning to Align and Translate](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Seq2Seq_with_Attention.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1hOd2JFafWgOvdbeXWoSm1gIiMEQ64KbM?usp=sharing)
This paper presents a remarkable improvement in the Sequence to Sequence architecture by introducing a (soft)alignment metric called "attention". This metric induces a sense of similarity between tokens of the source and decoded sentences, which increases the BLEU score by almost 1.5 times and is much more robust with regards to the length of source and target sentences.\
**<ins>Note:</ins>** In this implementation, setting the ```teacher_forcing_ratio``` to 1 resulted in a better BLEU score (even with higher validation and test perplexities) than setting it to 0.5.

### 3. [Convolutional Sequence to Sequence Learning](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Conv_Seq2Seq.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/18uxa0ZMlck4f5fzTUdkze_cuKz-Hgx_o?usp=sharing)
Unlike the previous papers, this paper is the first paper to tackle language modelling without using Recurrent Neural Networks. However, it does provide an attention mechanism and outperforms the sequential attention based architecture while having almost similar training times. The validation and test perplexities are quite low and the BLEU score is much better than that of the previous paper.

### 4. [Attention Is All You Need](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Attention_Is_All_You_Need.ipynb) [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1RlDhclIlJWzcFC0iPqwbiFEuiCbYIJBG?usp=sharing)
This paper can be said to have revolutionized almost all of Natural Language Processing, all owing to its tremendous simplicity and efficiency which makes it the backbone of almost all present State Of The Art architectures. The proposed *Transformer* architecture introduces a novel metric called *Self-Attention* which induces a sense of (soft)alignment amongst the source sentence tokens too. Additionally architecture uses simple feed-forward layers which makes it almost 4 times lighter than the Convolutional Sequence to Sequence architecture, while attaining the highest BLEU score amongst all the above mentioned architectures.

## Summary
Below is a table, summarising the number of parameters and the BLEU scores achieved by each architecture.

| Architecture                        | No. of Trainable Parameters | BLEU Score |
| ----------------------------------- |:---------------------------:|:----------:|
| Sequence to Sequence                |         13,899,013          |   18.94    |
| Sequence to Sequence with Attention |         20,518,917          |   31.24    |
| Convolutional Sequence to Sequence  |         37,351,685          |   36.53    |
| Attention Is All You Need           |          9,038,853          |   37.50    |

<ins>**Note:**</ins>
1. The above BLEU scores may vary slightly upon training the models (even with fixed SEED).
2. The research paper notes for the above mentioned papers can be found [here](https://github.com/IvLabs/ResearchPaperNotes/tree/master/natural_language_processing).


### Reference(s):
* [PyTorch Seq2Seq by Ben Trevett](https://github.com/bentrevett/pytorch-seq2seq)
