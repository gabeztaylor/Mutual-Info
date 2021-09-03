# M-Dimensional Estimator For Mutual Information

This repo presents an extension for computing the estimator of mutual information between 2 random variables to m random variables. Sklearn has a function for such a 2-dimensional problem called `mutual_info_regression`. The source code is modified such that we can take a $p$ dimensional design matrix and estimate the mutual information between $m$ predictors and the target. The estimator can be found in the following paper: https://journals.aps.org/pre/pdf/10.1103/PhysRevE.69.066138

## Mutual Information of Two Random Variables

$$I(X;Y) = \int \int p_{X, Y}(x, y) \log \frac{p_{X, Y}(x, y)}{p_X(x)p_Y(y)}$$

Notice that this takes the shape of the [Kullback-Leibler Divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence). Also recall that if $X$ and $Y$ are completely independent, then the joint probability distribution is the product of the marginals. In this case, indepedent continuous random variables yield a mutual information of 0, which can be observed above.

### A 2-Dimensional Estimator of Mutual Information

$$I(X, Y) = \psi(k) + \psi(N) - \langle \psi(n_{x_1 + 1}) + \psi(n_{y + 1})\rangle$$

Suppose $Z = (X, Y)$

where

- $\psi(x)$ is the digamma function

- $k$ is the number of nearest neighbors

- $m$ is the number if dimensions

- $N$ is the number of samples

- $n_{x_i}$ is the number of points $x_j$ strictly less than the radius, where the radius is the distance from $z_i$ to its $k^{th}$ neighbor. 

As shown in the paper, the authors propose an estimator from a nearest-neighbor approach which diverges from the traditional binning approach. They then briefly mention an extension for an M-dimensional estiamtor, which is given below.

### An M-Dimensional Estimator of Mutual Information

$$I(X_1, X_2,...,X_m) = \psi(k) + (m-1)\psi(N) - \langle \psi(n_{x_1}) + \psi(n_{x_2}) + ... + \psi(n_{x_m}) \rangle$$

Suppose $Z = (X_1, X_2,...,X_m)$

where

- $\psi(x)$ is the digamma function

- $k$ is the number of nearest neighbors

- $m$ is the number if dimensions

- $N$ is the number of samples

- $n_{x_i}$ is the number of points $x_j$ strictly less than the radius, where the radius is the distance from $z_i$ to its $k^{th}$ neighbor. 