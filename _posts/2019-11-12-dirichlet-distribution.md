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
become $\bf{P}$ = (250, 150, 100)/100 = (0.5, 0.3, 0.2). Because of 
the inevitable variability in the call process, it is possible to get calls 
which is related to these three topics, but with different probability 
distributions as in the table below.

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
density of all possible probability values of $\bf{P}$ =($p_1$, $p_2$,...,$p_k$) for 
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
effective number of observations associated with the outcome (i.e, call 
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
... \int_{x_1=0}^{u_k} \\\\
& \exp^{-u_k} \bigg(\prod_{i=1}^{k-1} x_i^{\alpha_i-1}\bigg)
\bigg(u_k - \sum_{i=1}^{k-1}x_i\bigg)^{\alpha_k-1} dx_1 dx_2...dx_{k-1}du_k 
\end{align}
$$

Then, we set $x_i = u_kv_i$ for $i=1,2,...,(k-1)$, where $dx_i=u_kdv_i.$ 
Since $0 \le x_i \le u_k,$ $0\le u_kv_i \le u_k$ and $0 \le v_i \le 1$ for $u_k > 0$.

$$
\begin{align}
\prod_{i=1}^{k} \Gamma(\alpha_i) & = \int_{u_k=0}^{\inf} \int_{v_{k-1}=0}^{1}
...\int_{v_1=0}^{1} \exp^{-u_k} \bigg(\prod_{i=1}^{k-1} (u_kv_i)^{\alpha_i-1} \bigg) \\\\
& \bigg(u_k - \sum_{i=1}^{k-1}(u_kv_i)\bigg)^{\alpha_k-1} u_k^{k-1} dv_1 dv_2...dv_{k-1}du_k \\\\
& = \int_{u_k=0}^{\inf} \exp^{-u_k} u_k^{\sum_{i=1}^k\alpha_i-k}\int_{v_{k-1}=0}^{1}
... \int_{v_1=0}^{1} \\\\
& \bigg( \prod_{i=1}^{k-1} v_i^{\alpha_i-1} \bigg)
\bigg(1- \sum_{i=1}^{k-1}v_i\bigg)^{\alpha_k-1} u_k^{k-1} dv_1 dv_2...dv_{k-1}du_k \\\\
& = \int_{u_k=0}^{\inf} \exp^{-u_k} u_k^{\sum_{i=1}^k \alpha_i-1} du_k
\int_{x_{k-1}=0}^{1}...\int_{x_1=0}^{1} \\\\
&\bigg( \prod_{i=1}^{k-1} v_i^{\alpha_i-1} \bigg)
\bigg(1- \sum_{i=1}^{k-1}v_i\bigg)^{\alpha_k-1} dv_1 dv_2...dv_{k-1}\\\\
& = \Gamma\bigg(\sum_{i=1}^k\alpha_i\bigg)
\int_{x_{k-1}=0}^{1}...\int_{x_1=0}^{1} \\\\
&\bigg( \prod_{i=1}^{k-1} v_i^{\alpha_i-1} \bigg)
\bigg(1- \sum_{i=1}^{k-1}v_i\bigg)^{\alpha_k-1} dv_1 dv_2...dv_{k-1}\\\\
\end{align}
$$

## 3 Parameters of Dirichlet Distribution

Parameter $\bf{\alpha} = (\alpha_1, \alpha_2,...,\alpha_k)$ is known as
the concentration parameter and determines which part of the $(k-1)$ 
simplex has the higher probability. There is a value $\alpha_i$ for
each outcome $i$ (i.e., call topic $i$). Each of these $\alpha_i$ values
represents the effective number of observations (i.e, pseudocounts) 
associated with the outcome $i$ and weight the probability $p_i$. 
Plots in the figures below show how Dirichlet distributions change
by different combination of $\alpha_i$ values for 3 call topics. Each 
point on the plots represents the probability mixture of the three call 
topics such as (0.8, 0.2, 0.0) or (0.2, 0.4, 0.4). 

Plots below show the Dirichlet distributions, where 
$\alpha_1=\alpha_2=\alpha_3 \le 1.$ Plots start with $\alpha_i$ 
values equal to 0.1 and then values are gradually increased to 1. 
For $\alpha_i$ values that are closer to 0, distribution concentrates 
on the corners (i.e., call topics) and along the boundaries of the simplex 
and it has this nice property that distributions are dominated by one of 
the outcomes (i.e., call topics). This means if you want to associate
each call transcript with a single topic, you should choose $\alpha_i$
values that are closer to 0. However, any topic can be dominated, 
since all $\alpha$ values are equal. When $\alpha_i$ values increases, 
central points becomes more and more attractive. Finally, for the case, 
$\alpha=(1,1,1),$  all possible distributions becomes equally likely 
(i.e., Dirichlet has uniform distribution). For each call transcript, 
it is equally likely that a call may be associated with a single topic, 
mixture of all the topics, or something in between.

![](/images/dirichlet-distribution/alpha_le_1_eq.png){: .align-center height="100%" width="100%"}

Plots below show the Dirichlet distributions, where $\alpha_i \le 1$ 
and $\alpha_i \neq \alpha_j$ for some $i,j = 1,2,3$. Plots start with 
$\bf{\alpha} = (0.9,0.5,0.2)$.  Similar to the previous case, distribution
concentrates on the corners (i.e., call topics) and along the boundaries
of the simplex. However, in that case, probability distributions 
concentrates more on the corner associated with outcome 1 (i.e., call
topic 1) since $\alpha_1$ is greater than $\alpha_2$ and $\alpha_3$. 
This becomes more clear in the second plot, where $\alpha_1$ value
is increased to 5. If one $\alpha_i$ value is greater than the others,
then the probability distributions that provides a higher probability
to that outcome is more probable. In the the third and forth plots, 
$\alpha_2$ value is increased to 0.9 and 2, respectively. Increasing
$\alpha_2$ moves the probability distributions towards the boundary
associated with outcome 1 and 2 (i.e., call topics 1 and 2). Probability 
distributions which provides higher probability to outcome 2 becomes
more favorable. When $\alpha_2$ becomes equal to $\alpha_3$ in the last 
plot, probability distribution concentrates in the center of the boundary
associated with the outcomes 1 and 2.

![](/images/dirichlet-distribution/alpha_le_1.png){: .align-center height="100%" width="100%"}

Plots below show the Dirichlet distributions, where
$\alpha_1=\alpha_2=\alpha_3 > 1$. Plots start with 
$\bf{\alpha} = (2,2,2)$ and then $\alpha_i$ values are increased to 500. 
As $\alpha_i$ increases, distribution becomes more tightly concentrated
around the center of the simplex. In the context of our example, as 
$\alpha_i \rightarrow \inf$, each transcript contains each topic
equally likely. 

![](/images/dirichlet-distribution/alpha_ge_2_eq.png){: .align-center height="100%" width="100%"}

Plots below show the Dirichlet distributions, where
$\alpha_1=\alpha_2=\alpha_3 > 1$ and $\alpha_i \neq \alpha_j$ 
for some $i,j = 1,2,3$. Plots start with $\bf{\alpha} = (5.0,2.0,2.0)$
and then values are gradually increased. In the first and the second plots,
distribution is concentrates around the corner associated with the outcome 1
(i.e., call topic 1) since the $\alpha_1$  value is greater that the other 
two values. When $\alpha_2$ is increased in the the third and fourth plots,
distribution tends towards the the boundary of outcomes 1 and 2 (i.e., call
topics 1 and 2) making the distributions, which provides higher probability 
to topic 2, more favorable. With the increased $alpha_3$ value in the last 
plot, distribution moves towards the center of the simplex making the 
distributions, which provides higher probability to topic 3, more likely. 

![](/images/dirichlet-distribution/alpha_ge_2.png){: .align-center height="100%" width="100%"}

Parameter $\bf{\alpha}$ determines the probability mixture of each outcome 
(i.e., each topic) for any given event (i.e., call transcript). For
low $\alpha_i$ values, transcripts will likely to be a mixture of a few 
topics. When $\alpha_i$ values increase, transcripts will likely to be
a mixture of more topics. In order to increase the probability of a
transcripts with some certain topic  (e.g., with a higher probability
for topic 1), higher value for $\alpha_1$ should be given.

**Note:** You can find the code that I use to generate the Dirichlet 
distribution plots in my github repository.

## 5 One Last Note!

Dirichlet distribution is the conjugate prior for categorical distribution 
and multinomial distribution. This means that 



---
REFERENCES
---

[Dirichlet Distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution)

[On the Dirichlet Distribution](https://mast.queensu.ca/~communications/Papers/msc-jiayu-lin.pdf)



