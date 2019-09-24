# basic Seq2Seq Model
-------
## Tensorflow version 1.14.0

Original INPUT: zhengjiapengniubi  

Source  
  Word Num.:    [25, 9, 24, 18, 17, 26, 7, 4, 8, 24, 18, 17, 18, 7, 5, 12, 7]  
  Input Words: z h e n g j i a p e n g n i u b i  

Target  
  Word Num.:       [4, 12, 24, 17, 9, 7, 7, 26, 7, 18, 18, 8, 8, 5, 25, 3]  
  Response Words: a b e g h i i j i n n p p u z <EOS>
  
 # xswl, zheng jia peng niu bi!
 -------------------
 
 Introduce to some used Tensorflow class and/or methods:
 
 1. TrainingHelper  
 [tensorflow Document](https://www.tensorflow.org/api_docs/python/tf/contrib/seq2seq/TrainingHelper)  
  It's a strategy of Teacher Forcing. It means that by training decoder we don't        feed output of t-1 to the input of t in decoder, but use target as the input of decoder.  
  Return object helper, which could be the paramter as BasicDecoder.
 
 2. GreedyEmbeddingHelper  
 [tensorflow Document](https://www.tensorflow.org/api_docs/python/tf/contrib/seq2seq/GreedyEmbeddingHelper)  
 Different from TrainingHelper, it feeds the output of t-1 to the input of t in decoder.
 
![image](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Seq2Seq/Images/v2-162d4ff280e1261544de57920eeab6e0_hd.jpg)
> [Image Source](https://zhuanlan.zhihu.com/p/47929039)  
知乎用户：王岳王院长
