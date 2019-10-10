# Reproduce some Machine Learning Models

## Introduction:

In this file, all models will be implemented in Tensorflow Framework rather than with Scikit-Learn, because model.fit() is really boring and you can learn nothing from it. 

In Tensorflow, you will have a brief intuition how does the model actually work and thus figure out its mechanism.

But they are still TOYS (Doge/)

TF Version : 1.14.0

----
#### IF YOU CANNOT OPEN THE .IPYNB FILE, YOU CAN USE [LINK](https://nbviewer.jupyter.org/) TO OPEN IT.  
 How: copy the link of .ipynb from Github and paste it into the above shown website.

----

1. Random Forest [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/RandomForrest.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
> ##### Some used TF methods:  
> params = tf.contrib.tensor_forest.python.tensor_forest.ForestHParams [SourceCode](https://github.com/tensorflow/tensorflow/tree/r1.14/tensorflow/contrib/tensor_forest)    
&ensp;(num_classes=2, num_features=10, regression=False,  
&ensp;num_trees=50, max_nodes=1000)
> - `num_classes`: The number of classes in a classification problem, or the number of dimensions in the output of a regression problem.
> - `num_features`: The number of input features.
> - `num_trees`: The number of trees to create. Defaults to 100. There usually isn't any accuracy gain from using higher values.
2. GBDT[Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/GBDT.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
3. KMeans[Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/K-Means.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
> ##### Some used TF methods:
> KMeans.training_graph() : [TF API training_graph()](https://www.tensorflow.org/versions/r1.14/api_docs/python/tf/contrib/factorization/KMeans)
>> Generate a training graph for kmeans algorithm.  
Returns:
A tuple consisting of:
>> - `all_scores`: A matrix (or list of matrices) of dimensions (num_input, num_clusters) where the value is the distance of an input vector and a cluster center.  
>> - `cluster_idx`: A vector (or list of vectors). Each element in the vector corresponds to an input row in 'inp' and specifies the cluster id corresponding to the input.  
>> - `scores`: Similar to cluster_idx but specifies the distance to the assigned cluster instead.  
>> - `cluster_centers_initialized`: scalar indicating whether clusters have been initialized.  
>> - `init_op`: an op to initialize the clusters.  
>> - `training_op`: an op that runs an iteration of training.  

-----
# Keep Updating
