# Several initialization methods

## 1. Latin Hypercube Sampling
It creates a grid in the search space by dividing each dimension into equal interval segments, and then generates some random points within some interval.  In the LHS, a set of samples are distributed so that they can sparsely distribute in the search space so as to effectively avoid the problem of over aggregation of sampling points.

But it does not show a distinct advantage for higher-dimensional problems.

Here is a code example:

```python
    import numpy as np

    def LHS(lower_bounds,upper_bounds,n_samples):
        dim=len(lower_bounds)
        samples=np.zeros((n_samples.dim))

        for d in range(dim):
            bounds=np.linspace(lower_bounds[d],upper_bounds[d],n_samples+1)
            temp=np.random.uniform(bounds[:-1],bounds[1:],size=n_samples)
            np.random.shuffle(temp)
            samples[:,d]=temp

        return samples
```

## 2. Beta Distribution
A beta distribution is a continuous probability distribution over the interval (0,1). Its probability density function (PDF) is given by

$$
f(x;a,b)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}
$$

This distribution has two shape parameters ($a>0,b>0$) that essentially control the shape of the distribution. Its notation is usually written as $X~Be(a,b)$. Its expected value is $\mu=\frac{a}{a+b}$ and its variance is $\frac{ab}{(a+b)(a+b+1)}$.

## 3. Uniform Distribution
Its probability density function is given by
$$
f(x) = 
\begin{cases}
    \frac{1}{b-a}, & \text{if } x \in (a,b) \\
    0, & otherwise
\end{cases}
$$

## 4. Normal Distribution
Its probability density function is given by
$$
f(x)=\frac{1}{\sqrt{2 \pi} \sigma} e^{-\frac{(x-\mu)^2}{2 \sigma^2}}
$$

## 5. Logarithmic Normal Distribution
Its probability density function is given by
$$
f(x)=\frac{1}{x\sigma\sqrt{2 \pi}} e^{-\frac{(ln(x)-\mu)^2}{2 \sigma^2}}
$$

## 6. Exponential Distribution

Its probability density function is given by ($\lambda>0$)
$$
f(x)=
\begin{cases}
    \lambda e^{-\lambda x}, & \text{if } x \geq 0 \\
    0, & \text{if } x<0
\end{cases}
$$

## 7. Rayleigh Distribution
Its probability density function is given by
$$
f(x)=\frac{x}{\sigma^2} e^{-\frac{x^2}{2 \sigma^2}}, x>0
$$
Its expected value is $\sqrt{\frac{\pi}{2}}$ and its variance is $\frac{4-\pi}{2}\sigma^2$.

## 8. Weibull Distribution
Its probability density function is given by
$$
f(x;\lambda,k)=
\begin{cases}
\frac{k}{\lambda}(\frac{x}{\lambda})^{k-1}e^{-(\frac{x}{\lambda})^k}, & \text{if } x\geq 0 \\
0, & \text{if } x<0
\end{cases}
$$

# Numerical Experiments

## Table 1: Basic Benchmark Functions
|Name|Function|Search Range|$x^{\mathrm{opt}}$|Opt|
|-|-|-|-|-|
|Rosenbrock|$f_1(X) = \sum_{i=1}^{D-1} \left[ 100(x_{i+1} - x_i^2)^2 + (x_i - 1)^2 \right]$|$[-5, 5]^D$|$(1, 1, \cdots, 1)$|0|
|Ackley|$f_2(X) = -20 \exp\left(-0.2\sqrt{\frac{1}{D} \sum_{i=1}^{D} x_i^2}\right) - \exp\left(\frac{1}{D} \sum_{i=1}^{D} \cos(2\pi x_i)\right) + 20 + e$|$[-10, 10]^D$|$(0, 0, \cdots, 0)$|0|
|Sphere|$f_3(X) = \sum_{i=1}^{D} x_i^2$|$[-5, 5]^D$|$(0, 0, \cdots, 0)$|0|
|Rastrigin|$f_4(X) = \sum_{i=1}^{D} \left[ x_i^2 - 10 \cos(2\pi x_i) \right] + 10$|$[-5.12, 5.12]^D$|$(0, 0, \cdots, 0)$|0|
|Griewank|$f_5(X) = \frac{1}{4000} \sum_{i=1}^{D} x_i^2 - \prod_{i=1}^{D} \cos\left(\frac{x_i}{\sqrt{i}}\right) + 1$|$[-600, 600]^D$|$(0, 0, \cdots, 0)$|0|
|Zakharov|$f_6(X) = \sum_{i=1}^{D} x_i^2 + \left(\frac{1}{2} \sum_{i=1}^{D} i x_i\right)^2 + \left(\frac{1}{2} \sum_{i=1}^{D} i x_i\right)^4$|$[-100, 100]^D$|$(0, 0, \cdots, 0)$|0|
|Alpine|$f_7(X) = \sum_{i=1}^{D} \left[ x_i \sin(x_i) + 0.1 x_i \right]$|$[-10, 10]^D$|$(0, 0, \cdots, 0)$|0|
|Easom|$f_8(X) = \left[ -\prod_{i=1}^{D} \cos(x_i) \right] \exp\left(-\sum_{i=1}^{D} (x_i - \pi)^2\right)$|$[-100, 100]^D$ | $(\pi, \pi, \cdots, \pi)$|-1|
|Schwefel|$f_9(X) = 418.98288727243369 \times D - \sum_{i=1}^{D} x_i \sin(\sqrt{\|x_i\|})$|$[-500, 500]^D$|$(420.96857, \cdots, 420.96857)$|0|

# Conclusions
We can draw some conclusions:

1. When the number of iterations is multiplied by the population size as a fixed value, a larger population size is required for PSO-w 

2. The PSO-w performs differently for different initialization methods, and the most appropriate initialization methods are random, beta distribution, and LHS.

3. The average distance between the initial population and the real optimal solution does not have any significant correlation with the quality of the nal solution for the algorithms. That is to say, the final solutions obtained are not usually a effcted by the locality of the optimal solutions. Thus, as long as the diversity of the population is high and the number of iterations is large, all these algorithms are capable of finding the optimal solutions.