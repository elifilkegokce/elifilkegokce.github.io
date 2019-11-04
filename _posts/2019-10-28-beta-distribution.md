---
title:  "What is Beta Distribution?"
search: false
---

## 1 Why do we need Beta Distribution?

Customers connect to contact center of a bank for a variety of reasons. 
One of the main contact reasons involves reporting a suspicious transaction. 
Suppose that you are trying to predict the probability of a call to be 
associated with a suspicious transaction. A naive approach may be to use 
the ratio of calls reporting a suspicious transaction in a certain time 
period. However, this may not be a good predictor especially when small 
number of calls are considered. Ratio of suspicious call depends on the 
time of the day and the day of the week. There may be a few suspicious 
transaction related calls during midnight. In that case, does it mean that 
the possibility of a customer to report a suspicious transaction is close to 0?
On the other hand, more calls may be expected during day time - increasing the 
possibility. Using the prior expectations based on the past data, the best way 
to predict the proportions and probabilities is with Beta distribution. 

> Beta distribution is used to predict proportions and probabilities!
 
## 2 How is Beta Distribution defined?
 
Beta distribution has two parameters $\bf{\alpha}$ and $\bf{\beta}$ and,
similar to probabilities, it is defined on the interval $(0, 1).$  
Beta distribution provides the probability density function (PDF) of 
a random value $p$ using the notation below.

Notation:

* $\bf{\Gamma(n):}$ Gamma function, which is defined by
 
$$
\begin{equation}
\Gamma(n) = \int_{0}^{\inf} x^{n-1} exp^{-x} dx
\end{equation}
$$

* $\bf{\alpha}:$ The first parameter of Beta distribution. Effective number of
observations of $p$ (i.e., event), which is the calls associated with 
suspicious transactions in our case.
* $\bf{\beta}:$ The second parameter of Beta distribution. Effective number
of observations of $(1-p)$ (i.e., no-event), which is the calls that don't 
involve suspicious transaction related topics in our case.
* $\bf{B(\alpha, \beta)}:$ Beta function, which has a constant value for given
$\alpha$ and $\beta.$ Using the parameters $\alpha$ 
and $\beta$, and the gamma function $\Gamma(n)$, it is defined by

$$
\begin{equation}
B(\alpha,\beta)=\frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}
\end{equation}
$$

Finally, for $\alpha>0$ and $\beta>0$, we define the PDF of Beta 
distribution by 

$$
\begin{equation}
f(p|\alpha,\beta)=\frac{1}{B(\alpha,\beta)} p^{\alpha-1}(1-p)^{\beta-1}
\end{equation}
$$

As you may observe in PDF of Beta distribution, $p^{\alpha-1}(1-p)^{\beta-1}$
weighs the probability of an event $p$ and the probability of no-event $(1-p)$. 
In our case, event occurs if a call involves a suspicious transaction. 
However, the function $p^{\alpha-1}(1-p)^{\beta-1}$, as PDF by itself, does 
not guarantee that the area under the curve of the PDF to be 1. In order to 
ensure that the total probability is 1, it is normalized by dividing by the
constant $B(\alpha,\beta).$

## 3 Let's Derive the Beta Function!

Since the area under the curve of the PDF should be equal to 1, from

$$
\begin{equation}
\int_{0}^{1} f(p|\alpha,\beta) dp = \frac{1}{B(\alpha,\beta)} 
\int_{0}^{1} p^{\alpha-1}(1-p)^{\beta-1} dp = 1,
\end{equation}
$$

we have

$$
\begin{equation}
 B(\alpha,\beta) = \int_{0}^{1} p^{\alpha-1}(1-p)^{\beta-1} dp 
 = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}
\end{equation}
$$

We start with calculating $\Gamma(\alpha)\Gamma(\beta),$

$$
\begin{align}
\Gamma(\alpha)\Gamma(\beta) & =  \int_{0}^{\inf} \exp^{-x}x^{\alpha-1}dx 
\int_{0}^{\inf} \exp^{-y}y^{\beta-1}dy \\\\
& = \int_{0}^{\inf} \int_{0}^{\inf} \exp^{-x}x^{\alpha-1} 
\exp^{-y}y^{\beta-1} dx dy \\\\
& = \int_{0}^{\inf} \int_{0}^{\inf} \exp^{-(x+y)} 
x^{\alpha-1}y^{\beta-1} dx dy 
\end{align}
$$

First, we set $u=x+y$. This results in $y=u-x$ and $dy=du.$ Since $0 \le y$, 
we have $0 \le u-x $ and, from $0 \le x,$ we get $0 \le x \le u.$

$$
\begin{align}
\Gamma(\alpha)\Gamma(\beta)&  =  \int_{0}^{\inf} \int_{0}^{u} \exp^{-u} 
x^{\alpha-1}(u-x)^{\beta-1} dx du \\
 &  =  \int_{0}^{\inf} \exp^{-u} 
\bigg(\int_{0}^{u} x^{\alpha-1}(u-x)^{\beta-1} dx \bigg) du \\
\end{align} 
$$

Then, we set $x = uv$, where $dx=udv.$ Since $0 \le x \le u,$ 
$0\le uv \le u$ and $0 \le v \le 1$ for $u > 0$.

$$
\begin{align}
\Gamma(\alpha)\Gamma(\beta) & = 
\int_{0}^{\inf} \exp^{-u} \bigg(\int_{0}^{1} (uv)^{\alpha-1}
(u-uv)^{\beta-1} udv \bigg) du \\
& = 
\int_{0}^{\inf} \exp^{-u} \bigg((u)^{\alpha+\beta-1} \int_{0}^{1} v^{\alpha-1}
(1-v)^{\beta-1} dv \bigg) du \\
& = \bigg(
\int_{0}^{\inf} (u)^{\alpha+\beta-1} \exp^{-u} du \bigg) \bigg( \int_{0}^{1} v^{\alpha-1}
(1-v)^{\beta-1} dv \bigg) \\
& = \Gamma(\alpha+\beta)B(\alpha,\beta)
\end{align} 
$$

Finally, from the last equation, we have

$$
\begin{equation}
 B(\alpha,\beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}
\end{equation} 
$$

## 4 Parameter of Beta Distribution

Probability density function of the Beta distribution

test

![](/images/beta-distribution/beta_a_equal_b.png){: .align-center} 


<style type="text/css">
  p {
    .width-half {width: 30%}
  }
</style>

![](/images/beta-distribution/beta_a_b_less1.png){: .align-right .width-half} | ![](/images/beta-distribution/beta_a_less1_b_ge1.png){: .align-right .width-half} 


![](/images/beta-distribution/beta_a_1_b_ge1.png){: .align-right .width-half} | ![](/images/beta-distribution/beta_a_g1_b_1.png){: .align-right .width-half} 


![](/images/beta-distribution/beta_a_g1_b_less1.png){: .align-right .width-half} | ![](/images/beta-distribution/beta_a_b_ge1.png){: .align-right .width-half} 


To exclude files when using **Algolia** as a search provider add an array to
 `algolia.files_to_exclude` in your `_config.yml`. For more configuration options be sure to check their [full documentation](https://community.algolia.com/jekyll-algolia/options.html).

```yaml
algolia:
  # Exclude more files from indexing
  files_to_exclude:
    - index.html
    - index.md
    - excluded-file.html
    - 2019-10-27-hello.md
    - subdirectory/*.html
```
---
REFERENCES
---

http://varianceexplained.org/statistics/beta_distribution_and_baseball/