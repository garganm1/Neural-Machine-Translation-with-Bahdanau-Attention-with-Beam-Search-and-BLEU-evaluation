# Neural Machine Translation with Bahdanau Attention

In this repo, we will deal with Translation of languages, specifically English to French. An Encoder-Decoder model using LSTM layers combined with Bahdanau Attention Mechanism will be implemented for training (along with Teacher Forcing - feeding the translation in a sequential manner to the decoder). Teacher Forcing can be compared to spoon-feeding wherein we ask the decoder model to spit out the next word when fed with the previously translated word(s) as well as the complete sequence of input language words (weighted with attention)

After the model gets trained, we will look at two inference algorithms viz. Greedy Search and Beam Search and discuss about each. For model's evaluation, we propose the BLEU metric to know how good the model can translate (albeit the metric having its own limitations)

Machine Translation models have been in existence for a long time. They are composed of Encoder-Decoder linked models. Encoder model's primary objective is to encode and learn the sequences of the source language while the Decoder Model's objective is to translate it to a target language. While these models have worked good, Bahdanau et. al. in circa 2014 came up with an Attention Mechanism that helps the decoder to focus on some words from the source language while translating and spitting out each word. This led to remarkable improvements in the model's performance and now Attention is being implemented to several applications apart from translation work in domains such as Computer Vision, etc.

In this notebook, we need to have tensorflow (2.4) installed in order to run it. Some knowledge on Deep NN Models is assumed as well as knowledge on RNN-LSTM networks

Source Language:- English
Target Language:- French

The dataset is provided by an organization through the below link:
Link for getting data - http://www.manythings.org/bilingual/

The notebook is segmented into following sections:

Section 1: Data Processing <br>
Section 2: Data Tokenization <br>
Section 3: Defining the Model <br>
Section 4: Training the Model <br>
Section 5: Inference from the Model (Greedy & Beam Search) <br>
Section 6: Data Processing


## Section 1: Data Processing

The data consists of english phrases/sentences and their french translations.

1. All special characters are removed
2. Sentence-ending symbols (. , ? !) are given spaces
3. Add 'start' at the start of the sentence and 'end' at the end of the sentence (to signal the model the start and end of any phrase/sentence)

As this notebook is for presentation purpose, we limit the data to the first 50,000 english-french data points. This number can be manipulated as per the user's needs

We end up with data that contains information like this-

| ENG_processed | FRA_processed |
| ------------- | ------------- |
| <start> tom lied to all of us . <end> | <start> tom nous a a tous menti . <end> |
| <start> tom lied to everybody . <end> | <start> tom a menti a tout le monde . <end> |
| <start> tom liked what he saw . <end> | <start> tom a aime ce qu il a vu . <end> |

and so on...

## Section 2: Data Tokenization

The tensorflow's tokenizer and padding functionalities will tokenize the processed text.

This means that for two texts in the corpus -

S1:- I am here <br>
S2:- He is here right now

The tokenized form would be -

S1:- [1, 2, 3, 0, 0]
S2:- [4, 5, 3, 6, 7]

Basically, the tokenized form would replace the word with a unique number that would represent that word.

- Notice the padding done at the end of sentence 1 (two 0's added). This will be done based on the maximum length of a sentence in a particular language
- Notice the repetiton of 3 in both tokenized forms which represent the word 'here' being repeated

Two separate tokenizers for each language will fit onto the each language's corpus to be tokenized. Besides this, we need two other values for each language for building the model architecture viz. maximum length of all sentences and vocabulary (count of unique words)

For Source Language (English)
 - Max Length = 11
 - Vocab Size = 5886

For Target Language (French)
  - Max Length = 19
  - Vocab Size = 10214

The tokenized text will be pickle stored finally to train the model with

## Section 3: Building the Model


## Section 4: Training the Model


## Section 5: Inference from the Model (Greedy & Beam Search)



## Section 6: Data Processing
