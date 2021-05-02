# Paragraph generation (Language modelling)

Model was trained over Book 1 - Philosopher's stone.txt which is 1st edition of Harry Potter franchise.

Text consists of
5978 distinct words (vocabilary size)
3275 usable paragraphs


> It is observed that model trained with nn.RNN is unable to form long term dependencies. Paragraphs formed were very short.
Meaning of sentence is lost just in 3-4 words . Although it is able to recognise end of paragraph. Model is wise enough to choose proper punctuation marks. For example- double quotes are closed in almost every trial.

> Whereas , model trained with nn.LSTM is able to form long term dependencies. Even next sentence formed after one shows some context shared. LSTM shows better results that RNN and GRU. Sentences and paragraphs are ended at proper position and proper meaning than other two.

> GRU Gives somewhat similar results like LSTM. Sentences show some what meaning and shared context. But next sentence formed looses previous context. Sentence ending and paragraph ending is done properly. Punctuations are also maintained. Also you can observe that , length of sequence formed decreases. 


GRU Loss function


![](https://github.com/AjinkyaDeshpande39/Natural-Language-Processing/blob/master/word_rnn/paragraph%20generation%20loss%20gru.png)

#embedding = 128
#hidden_size = 256
#num_layers = 4
#learning_rate = 0.0006
#epochs = 25
#3,782,234 trainable parameters

LSTM Loss function


![](https://github.com/AjinkyaDeshpande39/Natural-Language-Processing/blob/master/word_rnn/paragraph%20generation%20loss%20lstm.png)

#embedding = 128
#hidden_size = 256
#num_layers = 4
#learning_rate = 0.0006
#epochs = 25
#4,275,802 trainable parameters

RNN Loss function

![](https://github.com/AjinkyaDeshpande39/Natural-Language-Processing/blob/master/word_rnn/paragraph%20generation%20loss%20rnn.png)

#embedding = 150
#hidden_size = 400
#num_layers = 3
#learning_rate = 0.0006
#epochs = 25
#4,156,278 trainable parameters
> Since RNN has no cell states or gates those help in remembering details from previous inputs, we have increased size of hidden layer and embedding layer. Increment in number of parameters show better results.







**Results** - 

![](https://github.com/AjinkyaDeshpande39/Natural-Language-Processing/blob/master/word_rnn/ezgif.com-gif-maker.gif)

## LSTM

1. testing2('“ i tell you , we’re going to win that')
- “ i tell you , we’re going to win that in the summer - year waffle , something that he is to die — dumbledore says nothing about it , i’ll therefore nicolas ‘ rude with all with a fifty - points - points points that year , you were steamrollered ! ”

2. testing2('there was a very good chance they were going to get caught')
- 'there was a very good chance they were going to get caught some point \\ ”'


3. testing2('they pulled on their bathrobes , picked up their wands ,')
- 'they pulled on their bathrobes , picked up their wands , insisting themselves , and snape into the slytherin table . “ aren’t you ? ” screeched dumbledore , but she passed , but mr . dursley was , mysterious a long bite with broad soon .'

4. testing2('“ i am scared ”')
- '“ i am scared ” . . . for the soul . “ i can knew it , ” said dumbledore , grinning , grinning down the mom , “ mom , mom . ” '

5. testing2('hermione took out a list of subjects and titles she had')
- 'hermione took out a list of subjects and titles she had found talking to the ceiling . harry found a quiver again at the barrier , but the whisperers bear the platform as dressed there , too .'

## GRU

1. testing2('“ i tell you , we’re going to win that')
- '“ i tell you , we’re going to win that , ” said harry .'

2. testing2('there was a very good chance they were going to get caught')
- 'there was a very good chance they were going to get caught the fact . some and its common families and fifty trolls in the air ; it turned on the note .'

3. testing2('they pulled on their bathrobes , picked up their wands ,')
- 'they pulled on their bathrobes , picked up their wands , stone - green - muggle words . the same thing was still around at quirrell’s mouth , a purple hand , and a still screamed of books into the ceiling , and a same same through the same one ; the last last time in harry’s hand , reached into the same wall . the rest of the first thing they were talking and down , and waving into the table and winked , it was a terrible nostrils in'

4. testing2('“ i am scared ”')
- '“ i am scared ” . . . weasley face at harry . “ i said it , however , i thought . . . ”'

5. testing2('hermione took out a list of subjects and titles she had')
- 'hermione took out a list of subjects and titles she had already passed at the table , and she looked forward to herself to be allowed to be looking at them . she looked very high , she looked at them .'


## RNN

1. testing2('“ i tell you , we’re going to win that')
- “ i tell you , we’re going to win that hole . ”'

2. testing2('there was a very good chance they were going to get caught')
- 'there was a very good chance they were going to get caught the whole day .'

3. testing2('they pulled on their bathrobes , picked up their wands ,')
'they pulled on their bathrobes , picked up their wands , and fell into blackness .'

4. testing2('“ i am scared ”')
- '“ i am scared ” gasped . . . . ”'

5. testing2('hermione took out a list of subjects and titles she had')
- 'hermione took out a list of subjects and titles she had to say .'
