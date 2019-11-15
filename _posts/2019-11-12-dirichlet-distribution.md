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
become $(250, 150, 100)/100 = (0.5, 0.3, 0.2)$
 
||Call 1||||Call 2||
|:--------|:-------:|--------:||:--------|:-------:|--------:|
|Topic|words|probability|||words|probability|
|:--------|:-------:|--------:|||words|probability|
|Bill Payment|250| 0.50|||264|0.48|
|Account Update|150|0.30|||187|0.34|
|Check Order|100|0.10|||99|0.18|
|=====
||500| 1.00|||550|1.00| 

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3


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


