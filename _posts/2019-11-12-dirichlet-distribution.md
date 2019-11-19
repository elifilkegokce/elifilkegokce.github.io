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
become $\bf{P} = (250, 150, 100)/100 = (0.5, 0.3, 0.2).$ Because of the inevitable
variability in the call process, it is possible to get calls which is 
related to these three topics, but with different probability distributions
as in the table below.

|                |   Call 1  |         | | |   Call 2  |         | | |   Call 3  |         |
| :------------- | :-------: | :-----: | | | :-------: | :-----: | | | :-------: | :-----: |
| **Topic**      |**words**|  $\bf{P}$ | | |**words**|  $\bf{P}$ | | |**words**|  $\bf{P}$ |
| Bill Payment   |   250   |   0.500   | | |   264   |   0.480   | | |   264   |   0.550   |  
| Account Update |   150   |   0.300   | | |   187   |   0.340   | | |   132   |   0.275   |
| Check Order    |   100   |   0.200   | | |    99   |   0.180   | | |    84   |   0.175   |
| =====
|                | **500** | **1.000** | | | **550** | **1.00**  | | | **480** | **1.00**  |

In that case, we need a generalized model, which describe the uncertainty in 
the probabilities $\bf{P}.$ Dirichlet distribution, which is the generalization of
the Beta distribution into multiple dimensions, and provides the probability 
density of all possible probability values of $\bf{P}=(p_1, p_2,...,p_k)$ for 
a given set of $k$ events (i.e., call topics). 

> Dirichlet distribution is the multivariate generalization of the 
>[Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)!

 
## 1 How is Dirichlet Distribution defined?

Dirichlet distribution is parameterized by the vector $\bf{\alpha} = 
(\alpha_1, \alpha_2,...,\alpha_k) $ with $\alpha_i >0$ for $i=1,2, ..k$, 
which has the same number of events $, k,$ as $P.$ Dirichlet
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
\bf{B(\bf{\alpha})}=\frac{\prod_{i=1}^{k} \Gamma(\alpha_i)}{\Gamma(\sum_{i=1}^{k} \alpha_i)}
\end{equation}
$$

Finally, for $\alpha_i>0$ and $i=1,2,...,k,$ we define the PDF of Dirichlet 
distribution by 

$$
\begin{equation}
\bf{Dir(\bf{\alpha})} \rightarrow f(\bf{P}|\bf{\alpha})=\frac{1}{\bf{B(\bf{\alpha})}} \prod_{i=1}^kp_i^{\alpha_i-1},
\end{equation}
$$

where $\sum_{i=1}^kp_i =1$ and $p_i \ge 0$ for $i=1,2,...,k.$

Since the sum of the probabilities must be equal to one, 
$\sum_{i=1}^kp_i =1,$ and none of the probability, $p_i,$ can be negative,
all possible values of the probability vector, $\bf{P},$ is defined by the 
$(k-1)-$dimensional polytope, which is the convex hull of $k$ vertices. Since
one probability can be determined by deducting the remaining $k-1$ 
probabilities from 1, one degree of freedom is lost. Technically, this
$(k-1)-$dimensional polytope is known as $(k-1)-$simplex and it is called 
the `support` of the Dirichlet distribution. For example, for $k=3$ events, 
the figure below shows the 2-dimensional simplex, which is a triangle and 
consists of all possible probability values for 3 events.     

![](/images/dirichlet-distribution/2Simplex.png){: .align-center height="50%" width="50%"}

Beta distribution is a special case of Dirichlet distribution for$k=2$ 
events. By replacing $\alpha_1 \rightarrow \alpha$, $\alpha_2 \rightarrow \beta$, 
$p_1 \rightarrow p,$ and $p_2 \rightarrow (1-p),$ we get [Beta Distribution](https://elifilkegokce.github.io/beta-distribution/), 
$B(\alpha,\beta)$. 

As you may observe in the PDF of Dirichlet distribution, 
$\prod_{i=1}^kp_i^{\alpha_i-1}$ weighs the probability of each event $p_i.$ 
In our case, each event is a call topic. However, the function 
$\prod_{i=1}^kp_i^{\alpha_i-1}$ , as PDF by itself, does not guarantee 
that the area under the curve of the PDF to be 1. In order to ensure 
that the total probability is 1, it is normalized by dividing by the 
constant $\bf{B(\bf{\alpha})}.$ 

## 2 Let's Derive the PDF of Dirichlet Distribution!


Process used to derive the PDF of Dirichlet distribution is very similar to
that of Beta distribution. Similarly, since the area under the curve of 
the PDF should be equal to 1, from

$$
\begin{equation}
\int_{0}^{1} f(\bf{P}|\bf{\alpha}) dp = \frac{1}{\bf{B(\bf{\alpha})}} 
\int_{0}^{1} \prod_{i=1}^kp_i^{\alpha_i-1} dp = 1,
\end{equation}
$$

we have

$$
\begin{equation}
\bf{B(\bf{\alpha})} = \int_{0}^{1} \prod_{i=1}^kp_i^{\alpha_i-1} dp 
 =\frac{\prod_{i=1}^{k} \Gamma(\alpha_i)}{\Gamma(\sum_{i=1}^{k} \alpha_i)}
\end{equation}
$$


We start with calculating $\Gamma(\alpha)\Gamma(\beta),$

$$
\begin{align}
\prod_{i=1}^{k} \Gamma(\alpha_i) & =  \prod_{i=1}^k \int_{0}^{\inf} 
\exp^{-x_i}x^{\alpha_i-1}dx_i 
 \\\\
& = \int_{x_k=0}^{\inf} \int_{x_{k-1}=0}^{\inf} ... \int_{x_1=0}^{\inf} 
\prod_{i=1}^k(\exp^{-x_i}x_i^{\alpha_i-1}) dx_1 dx_2...dx_k \\\\
& = \int_{x_k=0}^{\inf} \int_{x_{k-1}=0}^{\inf} ... \int_{x_1=0}^{\inf} 
\exp^{-\sum_{i=1}^kx_i} \prod_{i=1}^k x_i^{\alpha_i-1} dx_1 dx_2...dx_k 
\end{align}
$$


First, we set $u_k=\sum_{i=1}^kx_i$. This results in $x_k=u_k-\sum_{i=1}^{k-1}x_i$ 
and $dx_k=du_k.$ Since $0 \le x_k$, we have $0 \le u_k-\sum_{i=1}^{k-1}x_i$ 
and, from $0 \le x_i,$ we get $0 \le x_i \le u_k$ for $i=1,2,...,(k-1).$

$$
\begin{align}
\prod_{i=1}^{k} \Gamma(\alpha_i) & = \int_{u_k=0}^{\inf} \int_{x_{k-1}=0}^{u_k}
... \int_{x_1=0}^{u_k} \exp^{-u_k} \prod_{i=1}^{k-1} x_i^{\alpha_i-1} (u_k - 
\sum_{i=1}^{k-1}x_i)^{\alpha_k-1} dx_1 dx_2...dx_{k-1}du_k 
\end{align}
$$

Then, we set $x_i = u_kv_i$ for $i=1,2,...,(k-1)$, where $dx_i=u_kdv_i.$ 
Since $0 \le x_i \le u_k,$ $0\le u_kv_i \le u_k$ and $0 \le v_i \le 1$ for $u_k > 0$.

$$
\begin{align}
\prod_{i=1}^{k} \Gamma(\alpha_i) & = \int_{u_k=0}^{\inf} \int_{x_{k-1}=0}^{u_k}
... \int_{x_1=0}^{u_k} \exp^{-u_k} \prod_{i=1}^{k-1} (u_kv_i)^{\alpha_i-1} 
(u_k - \sum_{i=1}^{k-1}(u_kv_i))^{\alpha_k-1} u_k^{k-1} dv_1 dv_2...dv_{k-1}du_k 
\end{align}
$$

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



