+ In this note, i will try to summarize the most important concepts of the **Machine Learning** class.
---
# TO DO
+ look at blind spots in previous sections
+ Look at test exams
+ Look at kinks of specific approaches: **when they work, when they don't, why**
# 1 - General Concepts
+ We will call $S_n$ the **training set**, composed of $n$ tuples $(x_i, y_i)$, where:
	+ $x_i \in X \subseteq \mathbb{R}^d$ , l'**input**
	+ $y_i \in Y$ , l'**output**. La sua dimensione e forma varia a seconda del problema
+ Our objective is to find a function $f$ such that:
	+ $f(x_i) \approxeq y_i$ (**fitting** property)
	+ $f(x_{new}) \approxeq y_{new}$ (**generalization** property)
+ To find it, we must first assume the following statement:
	1. The set of $x_i$ has been sampled **independently and identically** by a probability distribution $P_x(x)$
	2. The pairs in $S_n$ have been sampled from a **joint probability** $P(x, y) = P_x(x) \cdot P(y | x)$
		+ Those probabilities are related to the components of a supervised learning system:
			+ **Generator**:  Generates $x_i$
			+ **Supervisor**: generates $y_i$ from $x_i$
			+ **Learning Machine**: given the pairs $(x_i, y_i)$ finds $f(x)$
+ To find $f$ we need to have a way to quantify its quality
+ That is the **loss function**, which tells how much we lose from an approximation
	+ $l(y_i, f(x_i)) \to [0, + \infty)$
	+ *Many variants are used, one popular one is the square loss*
+ Using it we can compute the **expected loss** given by a function:
	+ $\varepsilon(f) = \mathbb{E}(x) = \int_Y \int_{X} P(x, y) l(y_i, f(x_i)) dx dy$
+ As such, the **best function** $f$ is:
	+ $f^* = \arg \min_{f \in H} \varepsilon (f)$
---
+ Sadly, there are **two caveats**:
	+ We do not know the probabilities
	+ We do not have all the space for computing the integral
+ **Then**, we need to reason in **empirical terms**:
	+ $\widehat{\varepsilon(f)} = \cfrac{1}{n} \sum^{n}_{i=1} l(y_i, f(x_i))$
	+ $\hat{f} \arg \min_{f \in H} \widehat{\varepsilon (f)}$
---
+ It is important to choose wisely the size of the hypothesis space $H$ to ensure the quality of the solution:
	+ It should not be too small, causing **underfitting**
	+ It should not be too big, causing **overfitting** and instability
## Cross-Validation
+ How do we find the ideal value of a hyper-argument $k$?
+ A simple idea is the **Hold Out Cross Validation**:
	+ We split the given set in two, training and **validation** set. The function will be constructed using the first, and tested for accuracy on the second. Th value of $k$ will be chosen on whatever one is more accurate to the actual values
+ How should we choose the values?
	+ We should take them **randomly**, to avoid problems derived from the vicinity of sequential points
+ Which ratio should we use for splitting?
	+ The percentage $\pi$ of training set should be always superior to 50%. The exact value depends on the quantity of data that we have
	+ On smaller datasets, often is useful to put almost alla data in the training set (**Leave-One-Out**)
		+ This method is the most precise, but the most expansive and less scalable
+ An idea is to repeat the sampling **multiple $q$ times** on different training subsets
+ We will get various values of $k$. How do we combine them?
	+ We choose the $k$ with the **best performance on every subset**:
		+ $\hat{k} = \arg_k \min (\text{avg}_{n = 1, \cdots, q} (\varepsilon_{v, n}(k)))$
+ How do we find the optimal number of repetition?
	+ We continue to cycle until the value of $k$ stabilizes
---
+ To avoid to choose random values for every split, we could just take another section of the same randomly sorted array (**Q-fold**)
# 2 - Main Methods
## K-Nearest Neighbours (K-NN)
+ This idea assume **locality**, that similar inputs have similar outputs
+ Basically we'll **predict** the **mean** value from the nearest k inputs

```python
## K-Nearest Neighbours
# O(n * d + n*log n)

X_tr, Y_tr, X_new, k # Input
n = len(Y_tr)
dist = zeroes(1, n)

for i in (1, n)
	dist[i] = distance(x_new, x_tr[i,:])
	
(s_dist, s_idx) = sort(dist)

if is regression_problem:
	return 1/k * sum(1 to k, Y_tr[s_idx[k]])

if is binary_classification_problem:
	return sign(sum(1 to k, Y_tr[s_idx[k]]))
```

+ The **complexity** is $O(nd + n\log{n})$, **similar** to before, it is **added** the **cost of sorting** the algorithm
---
+ We can imagine the function generated by $KNN$ as a piece-wise continuous function. As $k$ grows, the number of pieces increases, making it more similar to the original function (kinda like an integral), but it is obvious that **we need lots of data**
+ So, when we have **few data**, $KNN$ is **not really efficient**
## Regularized Least Squares (RLS)
+ This algorithm works **globally**
+ The idea is: We search for a function, a line in this case, which minimizes the error on our dataset, and as such is able to describe it and predict future values (Empirical Risk Minimization)
+ To compute the error, we use the following empirical loss function: (**Least Square Minimization**)$$\hat{L}(w) = \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2$$
+ To minimize it, we can compute its **gradient**, and put it equal to 0. In some cases this isn't possible to compute, and as such we slightly modify the problem by adding a **Regularization Parameter** $\lambda$ $$\hat{L}_\lambda(w) = \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2 + \lambda ||w||^2$$
+ After computing the gradient, the solution becomes: $$\hat{w} = (\hat{C} + n\lambda I)^{-1}\hat{h}$$
```python
def regularizedLSTrain(Xtr, Ytr, lam):

    C = Xtr.T @ Xtr

    A = C + lam * len(Xtr) * np.eye(Xtr.T.shape[0])

    h = Xtr.T @ Ytr

    inv = np.linalg.inv(A)

    w = inv @ h

    return w
    
def regularizedLSTest(w, Xte):

    return Xte @ w 
```

+ The **time complexity** is in $O(nd^2)$ for training, and $O(d)$ for testing
## Regularized Logistic Regression (RLR)
+ We can apply the same idea of RLS on **binary classification** problems, using the **Logistic/ Cross Entropy Loss**: $$l(f(x), y) = \log{(1 + e^{-y f(x)})}$$
+ Sadly, its gradient is **not linear** in $w$, meaning we **can't solve as before** to find the optimal $w$ $$\bigtriangledown (\hat{\varepsilon}(w) + \lambda ||w||^2) = \frac{1}{n} \sum^n_{i=1} \cfrac{-y_i x_i}{1 + e^{y_i w^T x_i}} + 2 \lambda w$$
+ The solution is a method called **Gradient Descent**
+ It is an **iterative method**, with each iteration we get closer and closer to the optimal solution $$w_0 = 0, \qquad w_{t+1} = w_t - \gamma_t \bigtriangledown (\hat{\varepsilon}(w_t) + \lambda ||w_t||^2)$$
 ```python
def gradient(Xtr, Ytr, w, n):
    exponent =  Ytr * np.dot(Xtr, w)
    division = -Ytr / (1 + np.exp(exponent))
    sigma    =  (1/n) * np.dot(Xtr.T, division)
    gradient = sigma + (2 * reg_par * w)
    return gradient
    
def train_logreg_gd(Xtr, Ytr, reg_par, maxiter=100):
    # Epsilon is a criterion for early stopping
    epsilon = 1e-6

    # size of the input in the training
    n, D = np.shape(Xtr)

    # initialization of the vector w
    w = np.zeros((D, 1))

    # Set the learning rate optimally
    gamma = optimal_gd_learning_rate(Xtr, reg_par)

    # initialization of some supporting variables
    j=0

    loss_old = 0

    loss = float("inf")

    training_losses = np.zeros(maxiter + 1)

    Ytr = Ytr.reshape(-1, 1)  # Convert from shape n, to shape n, 1

    while j < maxiter and abs(loss - loss_old) >= epsilon:

        loss_old = loss

        w = w - (gamma * gradient(Xtr, Ytr, w, n))

        # Compute the loss

        loss = (1/n * np.sum(np.log(1 + np.exp(-Ytr * (np.dot(Xtr, w))))) + (reg_par * np.dot(w.T, w)))[0][0]

        # Store the loss

        training_losses[j] = loss

        j += 1

    return w, training_losses[:j]

def predict_logreg(weights, X):

    ypred = np.dot(X, weights)
    
    return ypred.reshape(-1)
```

+ The gradient descent method can be **costly**
+ Another solution is the **Stochastic Gradient Descent** method:
	+ As before, but we compute the gradient only on $b$ samples
	+ This way we reduce the computation costs. The convergence will be **noisier**, **but** comparatively **quicker** 
+ *Take a look at how you find $\gamma$*
## Support Vector Machines (SVM) ?
+ *See if it needs to be seen...*
# 3 - Improvements
## Non-Linear Cases
+ The models we have seen are useful, but they can only work with linear models
+ What if we wanted to predict a **non-linear** model?
### Feature Maps
+ Our objective is to avoid rewriting all of the code and ideas we implemented
+ A simple first idea is to use a **Feature Map** $\Phi$ able to translate our problems in another space $\in \mathbb{R}^p$ where the problem becomes linear
	+ An example is using polynomials, as linear combinations of monomials
+ The problem though is that, as **dimensions grow**, the number $p$ grows as well, making computations more and **more complex**
+ We want a method able to remain efficient even as the number of dimensions grows to **infinity**
+ To achieve better performance, we change the way we compute our solutions
### Kernel Maps
+ We take the RLS case as an example
+ We can rewrite the following (**Representer Theorem**): $$w_\lambda = \sum^n \phi(x_i)c_i, \qquad c= \left[\Phi \Phi^T + \lambda n I\right]Y$$And the solution becomes:$$f_\lambda = \sum \phi(x_i)^T\phi(x_i)c_i$$
+ We can see that we do not need to compute $w$ to solve the problem, we just need a **Kernel Map** $K(x, \hat{x})$, a matrix such that: $$\left[K(x, \hat{x})\right]_{ij} = \sum^p_{k=1} \phi_k(x) \phi_k(\hat{x})$$
+ *List the type of kernels we saw...*

```python
def krls_train(x, y, reg_par, kernel_type, kernel_par):
    K = kernel_matrix(x, x, kernel_type, kernel_par)
    A = K + (reg_par * x.shape[0] * np.eye(x.shape[0]))
    w = np.linalg.solve(A, y)
    return 

def krls_predict(x_ts, x_tr, w, kernel_type, kernel_par):
    K = kernel_matrix(x_ts, x_tr, kernel_type, kernel_par)
    return np.dot(K, w) 
```
## Bayesian Learning
+ We've always assumed a **Frequentist** point of view on our probabilities, as "random", unknowable values
+ We switch to the **Probabilistic** (Bayesian) approach.
+ For example, let's imagine we have some data $Z : \{z_1, z_2, \cdots, z_n\}$, all sampled i.i.d by the same probability distribution $P$
+ We assume $P$ to be parameterized, as $P_\theta$. We want to find the best value of $\theta$, such that $$ \max_{\theta} \underbracket{P^n_\theta(Z)}_{\text{joint probability}} = \max_{\theta} \prod^n_i P_\theta(z_i)$$
+ This is the most probable value of $\theta$. We call $P^n_\theta(Z)$ the likelihood of $\theta$. $\max_{\theta} P^n_\theta(Z)$ is the **Maximum Likelihood** $\hat{L}(\theta)$ 
+ **Maximum Likelihood Estimation** (MLE) is the process of finding the best value of $\theta$
	+ Often, when working with exponential, we take the logarithm and compute the **Maximum Log Likelihood**
+ We can see that the processes of computing it for common problems (KNN, RLS, RLR) results in solutions similar to the ones we found using the frequentist approach
---
+ Can we implement **regularization** in this system?
+ Yes!
+ Let's assume our parameter $\theta$ is generated from another distribution, that we call **Prior** $\Pi$, which is centered on the true $\theta$. This distribution is **chosen**, it's a sort of hyper-parameter
+ For Bayes, we have that:$$\underbracket{P(\theta | Z)}_{\text{posterior}} = \cfrac{P(Z, \theta)}{P(Z)} = \cfrac{P(\theta) P(Z|\theta)}{P(Z)} = \cfrac{\overbracket{\Pi(\theta)}^{\text{prior}} \overbracket{P(Z|\theta)}^{\text{likelihood}}}{\underbracket{P(Z)}_{\text{marginal likelihood}}} $$
+ $P(Z)$ does not depend on $\theta$, so we can treat it as a **constant**
+ As such, we can say $$P(\theta | Z) \propto \Pi(Z) P(Z| \theta)$$
+ By maximizing that quantity, we can maximize the probability of $\theta$. This is **Maximum at Priori** (MAP)
+ Using this process on regression problems, it is possible to trace back to Ridge Regression as the MAP estimate for linear regression
## Explainable AI
+ In many practical situations, beyond predictions it is important to obtain interpretable results. 
+ **Interpretability** is often related to detecting which factors have determined our prediction
+ An example is **Variable Selection**
	+ Given a $n$ dimensional input and its output, we want to find **which** of those dimensions are **important** for predictions, or what do they mean
	+ We assume that the best prediction rule is **sparse**, that is only few of the coefficients in are different from zero.
+ A first approach is **brute-force**, trying all possibile combinations of variables and see how they fare
	+ But it is **too** computationally **expansive**
+ Maybe we can improve it
### Matching Pursuit
+ It is a **greedy** method, which means which it does not find the optimal solution, but a valid one, in an acceptable time
+ The idea is the following:
	+ We begin by initializing a value called **residual**
	+ We then select the variable such that the corresponding column best explains the the output vector, the residual.
	+ We add such variable to a **Index Set**
	+ We then update the variable vector and residual, and repeat
	+ In the end, the variable vector will contain non-zero values only where we found the better performing variables
+ A variant is **Orthogonal Matching Pursuit**, in which we test each time only with the good columns

```python
def OMatchingPursuit(X, Y, T):
    N, D = np.shape(X)

    # 1. Initialization of residual, coefficient vector and index set I
    r = Y
    w = np.zeros(D)
    I = []

    for i in range(T):
        I_tmp = range(D)

        # 2. Select the column of X which coefficients most "explains" the residual
        a_max = -1
        for j in I_tmp:
            a_tmp = pow(np.dot(r.T,  X[:, j]), 2) / pow(np.linalg.norm(X[:, j]), 2)
            if a_tmp > a_max:
                a_max = a_tmp
                j_max = j
                
        # 3. Add the index to the set of indexes
        if j_max not in I:
            I.append(j_max)
            
        # Compute the M matrix
        M_I = np.zeros((D, D))
        for j in I:
            M_I[j, j] = 1
            
        A = M_I.dot(X.T).dot(X).dot(M_I)
        B = M_I.dot(X.T).dot(Y)

        # 4. Update estimated coefficients
        w = np.dot(np.linalg.pinv(A), B)
        
        # 5. Update the residual
        r = Y - np.dot(X, w)
    return w, r, I
```
### Iterative Soft Thresholding (LASSO)
+ This is not a greedy method
+ It too is an **iterative method**, which uses **gradient descent** to update at each step the variable vector, suppressing each time each time the smaller values
+ The rule for RLS is:$$\begin{align} w_{t+1} &=S_{\lambda \eta}(w_t - \eta \triangledown||\hat{x}w - \hat{y}||^2)\\ S_{\lambda \eta} &=\begin{cases} w^j - \lambda \theta \qquad w^j > \lambda \eta \\ 0 \qquad \qquad  \; \;  |w|^j < \lambda \eta \\  w^j + \lambda \theta \qquad w^j < \lambda \eta\end{cases}\end{align}$$
+ It's a **convex relaxation** method

## Partition Based Function Estimators
+ An idea for estimators is to work in partitions, separate sections of the input space
+ An example would be to predict for each partition the mean output value. Or solve a least square problem individually for each partition
+ The choice of partitions is important. An idea is **adaptive partitioning**: We continue partitioning a section until all partitions have an error inferior to a certain threshold. This will give us partitions of differing sizes
+ The **greedy approach** iterates multiple times, trying to minimize the loss on a specific parameter at each step 
## Unsupervised Learning
### PDF Estimations
+ Let's assume we have some data $X : \{x_1, x_2, \cdots, x_n\}$ and that we want to **estimate** the **probability distribution** from which they were sampled.
	+ If we knew it, we could think of using it to **generate new data**
	+ An example could be an image generator. We feed it lot's mof cat pictures, estimate the PDF and based on that, sample a new cat image as the more probable value
	+ The estimated PDF won't have only one peak though, i mean, there probably would be lot's of local peaks. This could be a problem
+ How do we go about estimating the PDF?
#### Partition Based Estimator
+ A simple idea is using partition based estimators, as before
+ We separate in $h$ bins, and for each bin we count how much of our data is in it, and normalize it
+ The problem is choosing the value of $h$: We cannot cross-validate, we do not have the outputs
+ We can still improve this
#### Local Kernel Density Estimator (Local KDE)
+ The idea is similar to the one before, but with two major differences
	+ **Each point** will start with **its bin**, which will be then computed
	+ The "vote" cast by a point in a bin is now **weighted**, using its **distance** from the bin's point as a weight. A point will go in a bin only if the distance from the main point is smaller than a threshold (hyper-parameter)
	+ Moreover, we can use a **kernel** function to add some custom weights
+ As such, values with lots of neighbours will have bigger values, and viceversa
### Clustering
+ The problem of clustering is quite complex, since the concept itself of cluster is nebulous
+ For our purposes, a cluster is a group of near data, which ideally shares common properties 
+ An important step is also knowing how many clusters we have to find. Usually we cannot know in advance, we have to try, using it as an hyper-parameter
#### Agglomerative Clustering
+ The idea is to start with a single cluster per data point
+ After that, we unite the two nearest between em
+ Step by step, we reduce the number of cluster, making the remaining bigger and bigger.
+ We obtain a family of **hierarchical clusters**
+ This process can be well described by a **Dendrogram**
+ This approach can be used with lots of different data, we just need to find a way to compute meaningful distances. an example are binary strings, using the Hamming distance
#### K-Means
+ K-means is not really an algorithm, but a **concept**, one which has been developed in various actual algorithms, as Lloyd's and K-Means++
	+ The idea is to choose a number of clusters $k$. After that we choose $k$ points in our dataset which will be the center of the clusters. 
	+ We add points to a specific cluster when its center is the nearest
	+ To find the best center we could use ERM, computing the gradient, but it is quite difficult, so we'll use a greedy method
	+ After computing the cluster, we move the centers to be at the actual center of the cluster, and we re-compute the cluster.
	+ After some iterations, the clusters will stop moving, and we will stop
+ The main problem of this algorithm is **choosing the starting position** of the clusters
+ A first idea could be randomly, but we risk having two clusters near each other, which is not ideal
+ One is to choose each time the **farthest** data point from the previous chosen clusters
+ This idea is refined in **K-Means++**

```python

## find cluster centers
def kmeanspp(X, k):

    n, d = X.shape

    IdxC = np.random.permutation(n)
    centers = np.zeros((k, d))

    # Select a random point in the dataset as the starting point
    centers[0, :] = X[IdxC[0], :]

    for i in range(1, k):
        D = all_distances(centers[:i, :], X)
        Ds = np.min(D, axis=0)  # This is the distance to 
						        # the closest existing center

        # Probability of choosing new points as centers is weighted as 
        # the squared distance to the closest existing center.
        D2 = Ds ** 2
        P = np.divide(D2, np.sum(D2))
        
        # Simply pick the point with the highest probability
        newcpos = np.argmax(P)
        centers[i,:] = X[newcpos, :]

    return centers

## compute clusters
def lloyd(X, centers, maxiter):
    # X: n x d
    # centers : k x d

    n, d = X.shape
    k = centers.shape[0]

    for i in range(maxiter):
        # Compute Squared Euclidean distance (i.e. the squared distance)
        # between each cluster centre and each observation
        dist =  all_distances(X, centers)
        
        # Assign data to clusters:
        # for each point, find the closest center 
        # in terms of euclidean distance
        c_asg = np.argmin(dist, axis=1)

        # Update cluster center
        for c in range(k):
            points_in_cluster = X[c_asg == c]
            if len(points_in_cluster) > 0:
                centers[c] = np.mean(points_in_cluster, axis=0)

    return c_asg, centers
```
# 4 - Neural Networks
+ We now introduce another method of machine learning, called **Neural Networks**
+ The idea is based on imitating the inner workings of the human brain
+  As such, its base concept is the **Artificial Neuron** (Perceptron)
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
## Dense Networks (DNN)
+ Now that we have defined a neuron, let's imagine multiple of them! (**Dense Neural Networks**)
+ We could stack them in layers, called **hidden layers**, where they will receive the same inputs, with different weights, computing different features of the data
+ Each neuron could have a different activation function
+ If we use **multiple layers**, each neuron would receive the outputs of the previous layer, with new weights
	+ The **depth** is the amount of hidden layers, the **width** is the amount of neurons for layer
+ In the end, the outputs of the last layer will have to be "reunited" by a last neuron in the output layer
+ To train the model, we will have to train the value of the weights. To do so, we can use the usual techniques: Gradient Descent and Cross Validation
	+ We call **forward propagation** the computation of the gradient loss
	+ We call **back propagation** the computation of the new weights, based on the new gradient loss
## Convolutional Networks (CNN)
+ The previous model is cool, but we still have some limitations:
	+ **Each neuron** is connected to the others, and as such **influences the whole system**
	+ As the number of neurons and layers grow, the **number of weights** needed **grows** at an alarming rate
+ Here comes a type of network built for avoiding these problems, in particular in the case in which we are working with images: **Convolutional Neural Networks**
+  It has the following properties:
	+ It processes data in a **grid like manner**
	+ It has **sparse interactions**: Each neuron is connected to a smaller window of k other neurons, in a filter, and the weights of the filter are reused for multiple windows of neurons
		+ This reduces the number of weights to learn and the number of computations needed to train the model
+ The process becomes **learning the best filter** to convolve with our data
---
+ This changes the way in which the process goes:
	+ First, we have the **convolution** with the $k \times k$ filter and our inputs
	+ Then, we use the **activation function**
	+ After that we have the **pooling**, in which our data is reshapen in a smaller form, in which each new value is a summary statistic of nearby outputs
		+ This further reduces the dimensionality of the data and adds tolerance to smaller variations of our data
	+ We can repeat these previous steps multiple times, to further learn
	+ In the end, we apply **flattening**, to use the data with dense neuron nodes and "reunite" the output