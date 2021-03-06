---
title:  "What is Dirichlet Distribution?"
search: false
---

Intuition, Definition, Derivation, and Parameters...

We have discussed [Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)
in our previous post. If customers had called a call center for only two
reasons, then Beta distribution would have been enough to formulate the
probability of a call to be associated with a certain topic. However, 
a call (or any text such as a news, an article, a book, or an 
e-mail ...) can be related to multiple topics. It may be associated with
paying a bill, updating an account information, and ordering a new item 
at the same time. 

Suppose after counting the number of words associated with each topic 
in a call, we find out that there are 500 words in the call transcript. 
Out of these, 250 words are associated with paying a bill, 150
of them is associated with updating an account information and the 
remaining 100 is associated with ordering a new item. By normalizing the 
word counts of each topic (i.e., dividing word count of each topic by 
the total number of words in the call transcript), we may have
probability distribution of the topics as $\bf{P}$ = 
(250, 150, 100)/100 = (0.5, 0.3, 0.2). However, variability
is inevitable in a call (or in any text). It is possible to get calls, 
which is related to the three topics considered, but with different 
probability distributions as in the table below.

|                  |   Call 1  |         | | |   Call 2  |         | | |   Call 3  |         |
| :-------------   | :-------: | :-----: | | | :-------: | :-----: | | | :-------: | :-----: |
| **Topic**        |**words**|  $\bf{P}$ | | |**words**|  $\bf{P}$ | | |**words**|  $\bf{P}$ |
| Bill Payment     |   250   |   0.500   | | |   264   |   0.480   | | |   264   |   0.550   |  
| Account Update   |   150   |   0.300   | | |   187   |   0.340   | | |   132   |   0.275   |
| Order a new Item |   100   |   0.200   | | |    99   |   0.180   | | |    84   |   0.175   |
| =====
|                  | **500** | **1.000** | | | **550** | **1.00**  | | | **480** | **1.00**  |

In that case, we need a generalized model, which considers the 
uncertainty in the probabilities $\bf{P}$ = ($p_1, p_2,...,p_k$) of a
given set of $k$ events (topics). Dirichlet distribution, which is a 
generalization of the Beta distribution into multiple dimensions, can 
be used to describe the probability density of all possible probability 
values of $\bf{P}$. 

> Dirichlet distribution is the multivariate generalization of the 
>[Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)!

> Dirichlet distribution is used to model the probability distributions 
> of non-negative probability vectors $\bf{P}$ = ($p_1$, $p_2$,...,$p_k$), 
> whose elements are sums to 1.
 
## 1 How is Dirichlet Distribution defined?

Dirichlet distribution is parameterized by a positive real-valued vector 
$\bf{\alpha}$ = ($\alpha_1$, $\alpha_2$,...,$\alpha_k$), where each
parameter $\alpha_i$ is corresponding to an event (topic).  

Using the notation below, Dirichlet distribution provides the 
probability density function (PDF) of random values (probabilities) 
$\bf{P}$.

Notation:

* $\bf{\Gamma(n):}$ Gamma function, which is defined by
 
$$
\begin{equation}
\Gamma(n) = \int_{0}^{\inf} x^{n-1} exp^{-x} dx
\end{equation}
$$

* $\bf{\alpha}$ = ($\alpha_1$, $\alpha_2$,...,$\alpha_k$): Positive 
real-valued vector of parameters. Concentration parameter $\alpha_i$ is the 
effective number of observations associated with the event (topic) $p_i.$

* $\bf{B(\bf{\alpha})}$: Beta function, which has a constant value 
for given $\bf{\alpha}$, is defined by

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

Since probability $p_i$ cannot be negative and the sum of the 
probabilities must be equal to one, $\sum_{i=1}^kp_i =1$, one 
probability can be determined by deducting the remaining $k-1$ 
probabilities from 1. As a result, all possible values of the probability 
vector $\bf{P}$ can be defined by the $(k-1)-$dimensional 
polytope (convex hull of $k$ vertices). Technically, 
this $(k-1)-$dimensional polytope is known as $(k-1)-$simplex and 
called the `support` of the Dirichlet distribution. For example, 
for $k=3$ events, the figure below shows the 2-dimensional simplex, 
which is a triangle and consists of all possible probability values 
for 3 events.     

![](/images/dirichlet-distribution/2Simplex.png){: .align-center height="50%" width="50%"}

Beta distribution is a special case of Dirichlet distribution for $k=2$ 
events. By replacing $\alpha_1 \rightarrow \alpha$, $\alpha_2 \rightarrow \beta$, 
$p_1 \rightarrow p,$ and $p_2 \rightarrow (1-p),$ we get [Beta Distribution](https://elifilkegokce.github.io/beta-distribution/), 
$B(\alpha,\beta)$. 

As you may observe in the PDF of Dirichlet distribution, numerator
$\prod_{i=1}^kp_i^{\alpha_i-1}$ weighs the probability of each event 
$p_i$. Each parameter $\alpha_i$ can be thought as the number of 
observations (calls) associated with the event (topic) $i$. If the value 
of $\alpha_i$ is higher than the other parameters, then larger weight 
is assigned to $p_i$ and probability density is shift towards the 
probabilities that give a higher probability to that event (topic). 
However, the function $\prod_{i=1}^kp_i^{\alpha_i-1}$ , as PDF by 
itself, does not guarantee that the area under the curve of the PDF 
to be 1. In order to ensure that the total probability is 1, 
it is normalized by dividing a constant $\bf{B(\bf{\alpha})}.$ 


## 2 Let's Derive the PDF of Dirichlet Distribution!

Process used to derive the PDF of Dirichlet distribution is very similar to
that of Beta distribution. Similarly, since the area under the curve of 
the PDF should be equal to 1, from

$$
\begin{align}
\int_{0}^{1} f(\bf{P}|\bf{\alpha}) dp &= \frac{1}{\bf{B(\bf{\alpha})}} 
\int_{0}^{1} \prod_{i=1}^kp_i^{\alpha_i-1} dp \\\\
& = \int_{p_{k-1}=0}^{1} \int_{p_{k-2}=0}^{1}... \int_{p_1=0}^{1} \frac{1}{\bf{B(\bf{\alpha})}} 
\bigg(\prod_{i=1}^{k-1}p_i^{\alpha_i-1} \bigg) \\\\
& \bigg( 1- \sum_{i=1}^{k-1} p_i \bigg)^{(\alpha_k-1)} dp_1dp_2...dp_{k-1}\\\\
& = \frac{1}{\bf{B(\bf{\alpha})}} \int_{p_{k-1}=0}^{1} \int_{p_{k-2}=0}^{1}... \int_{p_1=0}^{1}  
\bigg(\prod_{i=1}^{k-1}p_i^{\alpha_i-1} \bigg) \\\\
& \bigg( 1- \sum_{i=1}^{k-1} p_i \bigg)^{(\alpha_k-1)} dp_1dp_2...dp_{k-1}\\\\
& = 1,
\end{align}
$$

we have

$$
\begin{align}
\bf{B(\bf{\alpha})} & =  \int_{p_{k-1}=0}^{1} \int_{p_{k-2}=0}^{1}... \int_{p_1=0}^{1}  
\bigg(\prod_{i=1}^{k-1}p_i^{\alpha_i-1} \bigg) \\\\
& \bigg( 1- \sum_{i=1}^{k-1} p_i \bigg)^{(\alpha_k-1)} dp_1dp_2...dp_{k-1}\\\\
\end{align}
$$


We start with calculating $\prod_{i=1}^{k} \Gamma(\alpha_i)$,

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
\int_{v_{k-1}=0}^{1}...\int_{v_1=0}^{1} \\\\
&\bigg( \prod_{i=1}^{k-1} v_i^{\alpha_i-1} \bigg)
\bigg(1- \sum_{i=1}^{k-1}v_i\bigg)^{\alpha_k-1} dv_1 dv_2...dv_{k-1}\\\\
& = \Gamma\bigg(\sum_{i=1}^k\alpha_i\bigg)
\int_{v_{k-1}=0}^{1}...\int_{v_1=0}^{1} \\\\
&\bigg( \prod_{i=1}^{k-1} v_i^{\alpha_i-1} \bigg)
\bigg(1- \sum_{i=1}^{k-1}v_i\bigg)^{\alpha_k-1} dv_1 dv_2...dv_{k-1}\\\\
& = \Gamma\bigg(\sum_{i=1}^k\alpha_i\bigg) \bf{B(\bf{\alpha})} \\\\
\end{align}
$$

Finally, from the last equation, we have

$$
\begin{equation}
\bf{B(\bf{\alpha})} =\frac{\prod_{i=1}^{k} \Gamma(\alpha_i)}{\Gamma(\sum_{i=1}^{k} \alpha_i)}
\end{equation}
$$


## 3 Parameters of Dirichlet Distribution

Parameter $\bf{\alpha}$ = $(\alpha_1, \alpha_2,...,\alpha_k)$ is 
known as the concentration parameter and, as its name implies, it 
determines how concentrated the distribution is around its mean 
$(\hat{\alpha_1}, \hat{\alpha_2},...,\hat{\alpha_k})$, where
$\hat{\alpha_i} = \alpha_i / \sum_{j=1}^k \alpha_j$ . Smaller 
values of the parameters favors more sparsely distributed 
distributions where greater amount of probability values allocated 
to a few events (topics) and the remaining events (topics) have a 
probability value close to 0. Larger values of the concentration 
parameters results in more evenly distributed distributions among 
all events (topics).

Plots in the following figures show how Dirichlet distributions 
change by different combination of $\alpha_i$ values for $k=3$ 
events (topics). Each point on the plots represents the probability 
mixture of the three events such as (0.8, 0.2, 0.0) or 
(0.2, 0.4, 0.4). 

*Dirichlet distributions with $\alpha_1=\alpha_2=\alpha_3 \le 1$:* 
Plots start with $\alpha_i$ values equal to 0.1 and then gradually 
increased to 1. For $\alpha_i$ values closer to 0, distribution
concentrates on the corners and along the boundaries of the simplex. 
In that case, it has this nice property that distributions are 
dominated by one of the events (topics). This means that if 
you want to associate each text (call transcript, article, news, 
e-mail) with a single topic, you should choose $\alpha_i$
values that are closer to 0. However, any topic can be dominated to
others, since all $\alpha$ values are equal. When $\alpha_i$ values 
increases, central points becomes more and more attractive. Finally, 
for the case $\alpha=(1,1,1)$, all possible distributions becomes 
equally likely (Dirichlet has uniform distribution). It is equally 
likely that a text may have a single topic, mixture of all topics, 
or something in between.

![](/images/dirichlet-distribution/alpha_le_1_eq.png){: .align-center height="100%" width="100%"}

*Dirichlet distributions with $\alpha_i \le 1$ and 
$\alpha_i \neq \alpha_j$ for some $i,j = 1,2,3$:* Plots start with 
$\bf{\alpha}$ = (0.9,0.5,0.2). Similar to the previous case, distribution
concentrates on the corners and along the boundaries
of the simplex. However, in that case, probability distributions 
concentrates more on the corner associated with the first event 
(topic 1) since $\alpha_1$ is greater than $\alpha_2$ and $\alpha_3$. 
This becomes more clear in the second plot, where $\alpha_1$ value
is increased to 5. If one $\alpha_i$ value is greater than the others,
then the probability distributions that provides a higher probability
to that event is more probable. In the the third and forth plots, 
$\alpha_2$ value is increased to 0.9 and 2, respectively. Increasing
$\alpha_2$ moves the probability distributions towards the boundary
associated with the first and the second events (topics 1 and 2). 
Probability distributions which provides higher probability also to
the second event becomes more favorable. When $\alpha_2$ becomes 
equal to $\alpha_1$ in the last plot, probability distribution 
concentrates in the center of the boundary associated with the 
first and the second events.

![](/images/dirichlet-distribution/alpha_le_1.png){: .align-center height="100%" width="100%"}

*Dirichlet distributions with $\alpha_1=\alpha_2=\alpha_3 > 1$:*
Plots start with $\bf{\alpha}$ = (2,2,2) and then values are increased
to 500. As $\alpha_i$ increases, distribution becomes more tightly 
concentrated around the center of the simplex. As 
$\alpha_i \rightarrow \inf$, it is equally likely that each text 
(transcript) contains each topic. 

![](/images/dirichlet-distribution/alpha_ge_2_eq.png){: .align-center height="100%" width="100%"}

*Dirichlet distributions with $\alpha_1=\alpha_2=\alpha_3 > 1$ 
and $\alpha_i \neq \alpha_j$ for some $i,j = 1,2,3$:* Plots start 
with $\bf{\alpha}$ = (5.0,2.0,2.0) and then values are gradually 
increased. In the first and the second plots, distribution is 
concentrated around the corner associated with the first event 
(topic 1) since $\alpha_1$ is greater that the others. When the 
value of $\alpha_2$ is increased in the the third and fourth plots,
distribution tends towards the the boundary of the first and the
second events (topics 1 and 2) making the distributions, which 
also provides higher probability to the second event, more 
favorable. With the increased $\alpha_3$ value in the last plot, 
distribution moves towards the center of the simplex favoring 
the distributions with higher probability for topic 3 as well. 

![](/images/dirichlet-distribution/alpha_ge_2.png){: .align-center height="100%" width="100%"}

Parameter $\bf{\alpha}$ determines the probability mixture of each 
event (topic) for any given text (call transcript, news, e-mail 
and so on). For low $\alpha_i$ values, texts will likely to be a 
mixture of a few topics. When $\alpha_i$ values increase, texts 
will likely to be a mixture of more topics. In order to increase 
the probability of a text with some certain topic  (e.g., with a 
higher probability for topic 1), higher value should be assigned to
to that topic ($\alpha_1)$.

**Note:** You can find the code that I use to generate the Dirichlet 
distribution plots in my github repository.

## 5 One Last Note!

Dirichlet distribution is favorable distribution in modeling the 
PDF of probability vectors since it makes the calculation of 
posterior distributions more convenient and faster. Dirichlet 
distribution is the conjugate prior for Categorical distribution 
and Multinomial distribution. If Dirichlet distribution is used to 
model the prior distribution of the probability parameters in these 
distributions, then the resulting posterior distribution of parameters
is also Dirichlet distribution. This provides closed form expression 
for the posterior distribution, making the calculation of the posterior 
distribution 
easy!

Given the probability of $k$ topics $\bf{P}$ 
= ($\hat{p}_1$, $\hat{p}_2$, ...,$\hat{p}_k$), likelihood function 
of having $(n_1, n_2,...,n_k)$ calls associated with each topic in 
$N$ calls is the Multinomial distribution given by

$$
f((n_1, n_2,...,n_k)|N, \bf{P}) = \binom{N}{n_1, n_2, ...,n_k} \prod_{i=1}^{k}\hat{p}_i^{n_i}
$$

Using the Dirichlet distribution, prior distribution for the probability of
$k$ call topics is given by

$$
f(\bf{P}|\bf{\alpha})=\frac{1}{\bf{B(\bf{\alpha})}} \prod_{i=1}^k\hat{p}_i^{\alpha_i-1}
$$

Given the number of calls $\bf{\hat{N}}$ = $(n_1, n_2,...,n_k)$ 
associated with each topic in $N = \sum_{i=1}^k n_i$ calls. Combining 
the likelihood and prior distribution, we get the posterior 
distribution of the probability vector of $k$ topics as follows:

$$
\begin{align}
f(\bf{P}| \text{N}, \bf{\hat{N}}) &  \\
& = \frac{\binom{N}{n_1,n_2,...,n_k} \prod_{i=1}^{k}\hat{p}_i^{n_i}
\frac{1}{\bf{B(\bf{\alpha})}} \prod_{i=1}^k\hat{p}_i^{\alpha_i-1}
}{\int_{0}^{1} \binom{N}{n_1,n_2,...,n_k} \prod_{i=1}^{k}x_i^{n_i}
\frac{1}{\bf{B(\bf{\alpha})}} \prod_{i=1}^kx_i^{\alpha_i-1}\bf{dx}} \\
& = \frac{\binom{N}{n_1,n_2,...,n_k} \prod_{i=1}^{k}\hat{p}_i^{n_i+\alpha_i-1}
\frac{1}{\bf{B(\bf{\alpha})}} 
}{\int_{0}^{1} \binom{N}{n_1,n_2,...,n_k} \prod_{i=1}^{k}x_i^{n_i+\alpha_i-1}
\frac{1}{\bf{B(\bf{\alpha})}} \bf{dx}} \\
& = \frac{\binom{N}{n_1,n_2,...,n_k} \prod_{i=1}^{k}\hat{p}_i^{n_i+\alpha_i-1}
\frac{1}{\bf{B(\bf{\alpha})}} 
}{\binom{N}{n_1,n_2,...,n_k} \frac{\bf{B(\bf{\alpha+\hat{N}})}}{\bf{B(\bf{\alpha})}}
\int_{0}^{1} \prod_{i=1}^{k}x_i^{n_i+\alpha_i-1}
\frac{1}{\bf{B(\bf{\alpha+\hat{N}})}} \bf{dx}} \\
\end{align} 
$$

Since $\int_{0}^{1} \prod_{i=1}^{k}x_i^{n_i+\alpha_i-1}
\frac{1}{\bf{B(\bf{\alpha+\hat{N}})}} \bf{dx}$ = 1 from the PDF of 
Dirichlet distribution, we will have the posterior distribution for 
the probability vector as

$$
\begin{align}
f(\bf{P}| \text{N}, \bf{\hat{N}}) = \frac{\prod_{i=1}^{k}\hat{p}_i^{n_i+\alpha_i-1}}{\bf{B(\bf{\alpha+\hat{N}})}}, \\
\end{align} 
$$

which is the Dirichlet distribution with parameters 
$\bf{\alpha+\hat{N}}$ = ($\alpha_1+n_1$, $\alpha_2+n_2$,..., $\alpha_k+n_k$).

If we use Dirichlet distribution as a prior in modelling the 
probability vector of events, then we will also have Dirichlet
distribution as posterior. This makes the computations easy while 
updating the model as more data comes in. Parameters for the 
updated posterior distribution can be calculated by simply adding the 
number of newly observed event $i$ to the parameter $\alpha_i$ 
corresponding to that event.
 
---
REFERENCES
---

[Dirichlet Distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution)

[On the Dirichlet Distribution](https://mast.queensu.ca/~communications/Papers/msc-jiayu-lin.pdf)

[Visualizing Dirichlet Distribution](http://blog.bogatron.net/blog/2014/02/02/visualizing-dirichlet-distributions/)



