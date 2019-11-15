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
100 is associated with check order. The probability of each topic in the 
call becomes $(p_1, p_2, p_3) = (0.5, 0.3, 0.2)$
 
|Call Topic|Call 1||
||words|$p_t$|
|Bill Payment|250|0.5|

In that case, we need a generalized
model, which considers all possible call reasons. 

> Dirichlet distribution is the multivariate generalization of the 
>[Beta Distribution](https://elifilkegokce.github.io/beta-distribution/)!
 
## 1 How is Dirichlet Distribution defined?
 

## 2 Let's Derive the PDF of Dirichlet Distribution!


## 3 Parameters of Dirichlet Distribution


## 4 Example: Bayesian Updating


## 5 One Last Note!



---
REFERENCES
---

[Beta Distribution and Baseball](http://varianceexplained.org/statistics/beta_distribution_and_baseball/)

[On the Dirichlet Distribution](https://mast.queensu.ca/~communications/Papers/msc-jiayu-lin.pdf)

[Beta Distribution](https://en.wikipedia.org/wiki/Beta_distribution)


