# basic Seq2Seq Model

![Seq2Seq](https://github.com/LiZongyue/Classic-Models-Reproduce-in-Tensorflow/blob/master/Deep_Learning/Seq2Seq/Images/seq2seq.png)
This Model is implemented in Tensorflow version 1.14.0    

 -------------------
 __Important Hints: IF YOU CANNOT OPEN THE .IPYNB FILE, YOU CAN USE [LINK](https://nbviewer.jupyter.org/) TO OPEN IT.__  
 How: copy the link of .ipynb from Github and paste it into the above shown website.
 
 --------   
 
## Table of Contents:  
- [Introduction](#introduction)  
- [Basic Knowledge to Seq2Seq](#basic-knowledge-to-seq2seq)
- [Introduction to some used Tensorflow classes or methods](#introduction-to-some-used-tensorflow-classes-or-methods)  


## Introduction:  
 Give a word as input, it will output a sequence which contains all characters of input in alphabetical order.  
 
 
 
A simple Instance of Prediction:  
Original INPUT: zhengjiapengniubi  

Source  
  Word Num.:    [25, 9, 24, 18, 17, 26, 7, 4, 8, 24, 18, 17, 18, 7, 5, 12, 7]  
  Input Words: z h e n g j i a p e n g n i u b i  

Target  
  Word Num.:       [4, 12, 24, 17, 9, 7, 7, 26, 7, 18, 18, 8, 8, 5, 25, 3]  
  Response Words: a b e g h i i j i n n p p u z <EOS>
  

 
 ## Basic Knowledge to Seq2Seq:  
 
 0. RNN(LSTM) Structure:    
 Explanation :  
 - `Time Step`: In this example, the input of each time step is a single character. One LSTMCell represents one time step.  
 - `Units in a Cell`: In Image RNN Cell Expansion, an unit is painted in purple. One Cell contains several units, whose input is word embediing.  
 - `Word Embedding`: A way to represent a word in a vector. In this example, Word Embedding is a way to represent a character in a vector.
 ![RNN](https://github.com/LiZongyue/Classic-Model-Reproduce-in-Tensorflow/blob/master/Deep_Learning/Seq2Seq/Images/rnn.png)   
 ![RNN_Cell](https://github.com/LiZongyue/Classic-Model-Reproduce-in-Tensorflow/blob/master/Deep_Learning/Seq2Seq/Images/cell.png)  
 ![RNN_Cell_Expansion](https://github.com/LiZongyue/Classic-Model-Reproduce-in-Tensorflow/blob/master/Deep_Learning/Seq2Seq/Images/cellexpansion.png)  
 1. Seq2Seq Model Structure:  
 ![Seq2Seq](https://github.com/LiZongyue/Classic-Models-Reproduce-in-Tensorflow/blob/master/Deep_Learning/Seq2Seq/Images/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20191015204836.png)  
 The above showed image illustrates a Seq2Seq Model for machine translation.  In each Seq2Seq Model, there are 2 parts which are `Encoder` and `Decoder`.  
 - `Encoder` : left side of the hidden state arrow  
 - `Decoder` : right side of the hidden state arrow
 
 ## Introduction to some used Tensorflow classes or methods:  
 0. tf.contrib.layers.embed_sequence(input_data, source_vocab_size, encoding_embedding_size)  
 [tensorflow Document](https://www.tensorflow.org/versions/r1.14/api_docs/python/tf/contrib/layers/embed_sequence?hl=eo)   
 It returns a Tensor of [input_data_size, source_vocab_size, encoding_embedding_size] with embedded sequences.
 1. tf.contrib.rnn.LSTMCell(rnn_size, initializer = tf.random_uniform_initializer(-0.1, 0.1, seed = 2))  
 [tensorflow Document](https://www.tensorflow.org/versions/r1.14/api_docs/python/tf/nn/rnn_cell/LSTMCell)  
 In this example, rnn_size indicates the number of units.  
 2. tf.nn.dynamic_rnn(cell, encoder_embed_input, sequence_length = source_sequence_length, dtype = tf.float32)  
 [tensorflow Document](https://www.tensorflow.org/versions/r1.14/api_docs/python/tf/nn/dynamic_rnn)   
 - `cell`: LSTM (could be GRU in other cases)    
 - `inputs`: encoder_embed_input is the word embedding
 - `sequence_length`: the length of each input sequence  
 It returns A tuple (outputs, state).
 - `state`: For LSTM, shape(state) = (2, num_input_sentence, num_output).   
 Its' shape will be changed if GRU used. For tf.nn.dynamic_rnn, the returned state may be different when the sequence(sequence_length) is shorter. The state h == output(last row) if there is no Padding. If there is a Padding, the state h is a convenient tensor that holds the last actual RNN state, ignoring the zeros. It means the state h will still equal to the last row in output that doesn't consider padding‘s result as output.    
 
   
 3. TrainingHelper  
 [tensorflow Document](https://www.tensorflow.org/api_docs/python/tf/contrib/seq2seq/TrainingHelper)  
  It's a strategy of Teacher Forcing. It means that by training decoder we don't        feed output of t-1 to the input of t in decoder, but use target as the input of decoder.  
  Return object helper, which could be the paramter as BasicDecoder.
 
 4. GreedyEmbeddingHelper  
 [tensorflow Document](https://www.tensorflow.org/api_docs/python/tf/contrib/seq2seq/GreedyEmbeddingHelper)  
 Different from TrainingHelper, it feeds the output of t-1 to the input of t in decoder.
 
![image](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Deep_Learning/Seq2Seq/Images/v2-162d4ff280e1261544de57920eeab6e0_hd.jpg)  
> Difference between using Teacher Forceing and not using.  



