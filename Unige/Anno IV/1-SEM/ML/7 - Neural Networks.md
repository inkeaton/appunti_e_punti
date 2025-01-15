#18/11/24 #20/11/24

+ We now introduce another method of machine learning, called **Neural Networks**
+ The idea is based on imitating the inner workings of the human brain
+ As such, its base concept is the **Artificial Neuron** (Perceptron)
	+ It's a node which receives a series of inputs, and computes their sum. 
	+ If the value is superior to a certain threshold, the neuron activates (binary output)
+ This model is cool, but it cannot solve non linear problems. So, we modify it as follows:
	+ We add **weights** for the sum of the elements. We may add a base weight for the value q of the function
		+ We could instead standardize the data by subtracting the mean value from the input
	+ Instead of a threshold, we use a **non-linear activation function**
		+ The most used are 
			+ Sigmoid
			+ Tanh
			+ Relu
			+ Leaky Relu
+ This makes us model the non linearity in both input and weights (different from features maps!)
---
+ Now that we have defined a neuron, let's imagine multiple of them! (**Dense Neural Networks**)
+ We could stack them in layers, called **hidden layers**, where they will receive the same inputs, with different weights, computing different features of the data
+ Each neuron could have a different activation function
+ If we use **multiple layers**, each neuron would receive the outputs of the previous layer, with new weights
+ In the end, the outputs of the last layer will have to be "reunited" by a last neuron in the output layer
+ To train the model, we will have to train the value of the weights. To do so, we can use the usual techniques: Gradient Descent and Cross Validation
	+ We call **forward propagation** the computation of the gradient loss
	+ We call **back propagation** the computation of the new weights, based on the new gradient loss
---
+ This model is cool, but we still have some limitations:
	+ **Each neuron** is connected to the others, and as such **influences the whole system**
	+ As the number of neurons and layers grow, the **number of weights** needed **grows** at an alarming rate
+ Here comes a type of network built for avoiding these problems, in particular in the case in which we are working with images: **Convolutional Neural Networks**
+ It has the following properties:
	+ It processes data in a grid like manner
	+ It has **sparse interactions**: Each neuron is connected to a smaller window of k other neurons, in a filter, and the weights of the filter are reused for multiple windows of neurons
		+ This reduces the number of weights to learn and the number of computations needed to train the model
+ This changes the way in which the process goes:
	+ First, we have the **convolution** with the $k \times k$ filter and our inputs
	+ Then, we use the **activation function**
	+ After that we have the **pooling**, in which our data is reshapen in a smaller form, in which each new value is a summary statistic of nearby outputs
		+ This further reduces the dimensionality of the data and adds tolerance to smaller variations of our data
	+ We can repeat these previous steps multiple times, to further learn
	+ In the end, we apply **flattening**, to use the data with dense neuron nodes and "reunite" the output