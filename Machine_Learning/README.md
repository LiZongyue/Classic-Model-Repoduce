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

Common used:  
`from __future__ import print_function` : To bring the print function from Pyhton3 to Python2.6+. `__future__` statements need to be near the top of the file because they change fundamental things about the language, and so the compiler needs to know about them from the beginning. 


### Catalog:  
1. Random Forest [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/RandomForrest.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
> #### Some used TF methods:  
> ##### 1. params = tf.contrib.tensor_forest.python.tensor_forest.ForestHParams [SourceCode](https://github.com/tensorflow/tensorflow/tree/r1.14/tensorflow/contrib/tensor_forest)    
> ##### &ensp;(num_classes=2, num_features=10, regression=False,  
> ##### &ensp;num_trees=50, max_nodes=1000)
> - `num_classes`: The number of classes in a classification problem, or the number of dimensions in the output of a regression problem.
> - `num_features`: The number of input features.
> - `num_trees`: The number of trees to create. Defaults to 100. There usually isn't any accuracy gain from using higher values.
2. GBDT [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/GBDT.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
3. KMeans [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/K-Means.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)
> #### Some used TF methods:
> ##### 1. KMeans.training_graph() : [TF API training_graph()](https://www.tensorflow.org/versions/r1.14/api_docs/python/tf/contrib/factorization/KMeans)
> Generate a training graph for kmeans algorithm.  
Returns:
A tuple consisting of:
> - `all_scores`: A matrix (or list of matrices) of dimensions (num_input, num_clusters) where the value is the distance of an input vector and a cluster center.  
> - `cluster_idx`: A vector (or list of vectors). Each element in the vector corresponds to an input row in 'inp' and specifies the cluster id corresponding to the input.  
> - `scores`: Similar to cluster_idx but specifies the distance to the assigned cluster instead.  
> - `cluster_centers_initialized`: scalar indicating whether clusters have been initialized.  
> - `init_op`: an op to initialize the clusters.  
> - `training_op`: an op that runs an iteration of training.    
4. Word2vec [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/Word2vec.ipynb) || DataSet: Wiki articles collection (Download in 3. cell)  
5. Word2Vec via U Stanford CS224n [Notebook](https://github.com/LiZongyue/Classic-Model-Reproduce/blob/master/Machine_Learning/exploring_word_vectors.ipynb) || DataSet: Files from the specified Reuter's category.  
6. Convolutional Neural Network [Notebook](https://github.com/LiZongyue/Classic-Models-Reproduce-in-Tensorflow/blob/master/Machine_Learning/CNN.ipynb) || DataSet : [MNIST](https://en.wikipedia.org/wiki/MNIST_database)  
> #### Some used TF methods and classes:  
> ##### 1. tf.estimator.EstimatorSpec(mode, prediction, loss, train_op, eval_metric_ops) : [TF API EstimatorSpec](https://www.tensorflow.org/api_docs/python/tf/estimator/EstimatorSpec?hl=fi)  
> Generate a model object run by Estimator().  
Returns:  
A EstimatorSpec object.  
> Arguments:  
> - `mode`: A ModeKeys. Specifies if this is training, evaluation or prediction.  
> - `prediction`:  Predictions Tensor or dict of Tensor. Simply: Do prediction.  
> - `loss`:  Predictions Tensor or dict of Tensor.  
> - `train_op`: Op for the training step.  
> - `eval_metrics_ops`: Dict of metric results keyed by name. The values of the dict can be one of the following: (1) instance of Metric class. (2) Results of calling a metric function, namely a (metric_tensor, update_op) tuple. metric_tensor should be evaluated without any impact on state (typically is a pure computation results based on variables.). For example, it should not trigger the update_op or requires any input fetching.  
> ##### 2. tf.estimator.Estimator()  [TF API Estimator()](https://www.tensorflow.org/api_docs/python/tf/estimator/Estimator)  
> The Estimator object wraps a model which is specified by a `model_fn`, which, given inputs and a number of other parameters, returns the ops necessary to perform training, evaluation, or predictions.  
> - `model_fn` as defined in the script, it is mainly to define `train_op`, `loss`, `optimizer` for training; `loss`, `acc_op` for evaluation; `prediction` for prediction.   

> Returns:  
> a wraped model. For training, model.train will automatically assign the value `tf.estimator.ModeKeys.TRAIN` to the mode parameter. At the same, `tf,estimator.ModeKeys.PREDICT` and `tf.estimator.ModeKeys.EVAL` will also be assigned to `mode` if model.predict and tf.model.evaluate are called.  
-----
# Keep Updating
