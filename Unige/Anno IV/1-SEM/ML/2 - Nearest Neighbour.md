+ Let's now take a look at one of the first and simpler machine learning algorithms, **Nearest Neighbour**, used both in **regression** and **classification** problems
+ The idea is very simple: given a new input $x_{\text{new}}$ we will assign it the output of the nearest input of the training set
	+ $i^* = \arg \min_{i = 1, \cdots, n} || x_\text{new} - x_i ||$
	+ $y_{\text{new}} = \hat{f}(x_\text{new}) = y_{i^*}$
+ In code, we would have something as follows:

```python
## Nearest Neighbour
# O(n * d)

X_tr, l Y_tr, X_new, # Input
n = len(Y_tr)
dist = zeroes(1, n)

for i in (1, n)
	dist[i] = distance(x_new, x_tr[i,:])
	
(min_val, min_idx) = min(dist)

return Y_tr[min_idx]
```

+ The **complexity** of the algorithm in $O(nd)$, where $n$ and $d$ are the dimensions of input $X_{tr}$. Indeed this value derives from the for loop
---
+ This algorithm is cool, but it is **subject to errors** in the case of a **noisy training set**
+ The solution is very simple: instead of using only the nearest input, we could use **$k$ nearest inputs**:

```python
## K-Nearest Neighbours
# O(n * d + n*log n)

X_tr, l Y_tr, X_new, k # Input
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

+ The complexity is $O(nd + n\log{n})$, **similar** to before, it is **added** the **cost of sorting** the algorithm
+ The choice of the value of $k$ determines the stability of the function and its quality. It is called an **Hyper-Argument**. We'll see in the future how do we find the ideal value for any situation