---
title:  "What is Dirichlet Distribution?"
search: false
---

We have discussed [Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)
in our previous post. If customers had called the contact center for only two
reasons, then Beta distribution would have been enough to formulate the
probability of a call to be associated with a certain reason. However, calls
are usually related to multiple topics. A call may be associated with
bill payment, account information update and check order at the same time. 
Suppose after counting the number of words associated with each topic 
in the call transcript, we find out that there are 500 words in the 
transcript. Out of these, 250 words are associated with bill payment, 150
of them is associated with account information update and the remaining 
100 is associated with check order. The probability distribution of three 
topics can be obtained by normalizing the word counts of each topic; 
i.e., dividing word count of each topic by the number of total words in the
call transcript. Then, the probability distribution of topics
become $P = (250, 150, 100)/100 = (0.5, 0.3, 0.2).$ Because of the inevitable
variability in the call process, it is possible to get calls which is 
related to these three topics, but with different probability distributions
as in the table below.

|                |   Call 1  |         | | |   Call 2  |         | | |   Call 3  |         |
| :------------- | :-------: | :-----: | | | :-------: | :-----: | | | :-------: | :-----: |
| **Topic**      |**words**|  **$P$**  | | |**words**|  **$P$**  | | |**words**|  **$P$**  |
| Bill Payment   |   250   |   0.500   | | |   264   |   0.480   | | |   264   |   0.550   |  
| Account Update |   150   |   0.300   | | |   187   |   0.340   | | |   132   |   0.275   |
| Check Order    |   100   |   0.200   | | |    99   |   0.180   | | |    84   |   0.175   |
| =====
|                | **500** | **1.000** | | | **550** | **1.00**  | | | **480** | **1.00**  |

In that case, we need a generalized model, which describe the uncertainty in 
the probabilities $p.$ Dirichlet distribution, which is the generalization of
the Beta distribution into multiple dimensions, and provides the probability 
density of all possible probability values of $P={p_1, p_2,...,p_k}$ for 
a given set of $k$ elements (i.e., call topics). 

> Dirichlet distribution is the multivariate generalization of the 
>[Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)!

 
## 1 How is Dirichlet Distribution defined?

Dirichlet distribution is parameterized by the vector $\bf{\alpha} = 
(\alpha_1, \alpha_2,...,\alpha_k) $ with $\alpha_i >0$ for $i=1,2, ..k$, which has the same number of elements 
($k$) as $P,$ and it is defined on the interval $(0, 1).$ Dirichlet
distribution provides the probability density function (PDF) of a random 
values $P$ using the notation below.

Notation:

* $\bf{\Gamma(n):}$ Gamma function, which is defined by
 
$$
\begin{equation}
\Gamma(n) = \int_{0}^{\inf} x^{n-1} exp^{-x} dx
\end{equation}
$$

* $\bf{\alpha} = (\alpha_1, \alpha_2,...,\alpha_k):$ Vector of parameters of 
Dirichlet distribution. Each concentration parameter $\alpha_i$ is the 
effective number of observations associated with the element (i.e, call 
topic) $p_i.$

* $\bf{B(\bf{\alpha})}:$ Beta function, which has a constant value for given
$\bf{\alpha}.$ Using the parameters $\bf{\alpha}$ and the gamma function 
$\Gamma(n)$, it is defined by

$$
\begin{equation}
B(\alpha,\beta)=\frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}
\end{equation}
$$

 

## 2 Let's Derive the PDF of Dirichlet Distribution!


## 3 Parameters of Dirichlet Distribution


## 4 Example: Bayesian Updating


## 5 One Last Note!

Dirichlet distribution is the conjugate prior for categorical distribution 
and multinomial distribution. This means that 



---
REFERENCES
---

[Dirichlet Distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution)

[On the Dirichlet Distribution](https://mast.queensu.ca/~communications/Papers/msc-jiayu-lin.pdf)



