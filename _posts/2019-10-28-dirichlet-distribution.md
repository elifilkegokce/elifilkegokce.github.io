---
title:  "What is Dirichlet Distribution?"
search: false
---

Customers connect to contact center of a bank for a variety of reasons. 
One of the main contact reasons involves reporting a suspicious transaction. 
Suppose that you are trying to predict the possibility of such a call in a 
certain time period. A naive approach may be to use the ratio of calls reporting 
a suspicious transaction as the possibility of a call to be associated with 
a suspicious transaction. However, this may not be a good predictor especially 
at the start of the period when there is only small number of calls. Ratio of 
suspicious call depends on the time of the day. There may be a few suspicious 
transaction related calls during midnight. In that case, does it mean that 
the possibility of a customer to report a suspicious transaction is close to 0?
On the other hand, more calls may be expected during day time - increasing the 
possibility. Using the prior expectations based on the past data, the best way 
to predict the proportions and probabilities is with Beta distribution. 


`Beta distribution is used to predict proportions 
and probabilities.`

 
 
 The standard $Beta$ distribution gives the probability density of
a value $x$ on the interval (0,1):
 
\begin{equation}
Beta(\alpha,\beta):\,\, prob(x|\alpha,\beta)=\frac{x^{\alpha-1}(1-x)^{\beta-1}}{B(\alpha,\beta)}\label{eq:BetaDensity}
\end{equation}
where $B$ is the beta function
\[
B(\alpha,\beta)=\int_{0}^{1}t^{\alpha-1}(1-t)^{\beta-1}dt
\]


 There are two parameters which work together to determine
if the distribution has a mode in the interior of the unit interval
and whether it is symmetrical.







```yaml
search: false
```

c

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