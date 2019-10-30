---
title:  "What is Dirichlet Distribution?"
search: false
---

Customers connect to contact center of a bank for a variety of reasons. 
One of the main contact reasons involves reporting a suspicious transaction. 
Suppose that you are trying to predict the possibility of such a call on a 
certain day. Since a call can be associated with more than one reason or 
call center agents usually enter very general descriptions as call intentions,
one way to determine call intentions accurately is to listen to a sample of 
calls. Then, the naive approach may be to use the ratio of calls reporting 
a suspicious transaction as the possibility of a call to be associated with 
a suspicious transaction. However, this may not be a good predictor. More than 
100K calls are handled at a contact center during the day and the available 
capacity for call listening is very limited to a sample size of about 500 
calls. There may not be any suspicious transaction related calls in such a 
small sample of calls. In that case, does it mean that the possibility of a 
customer to report a suspicious transaction is 0? Using the prior expectations 
based on the past data, the best way to predict the proportions or
 probabilities is with Beta distribution:
 
 \begin{equation}
Z = WX + b
\end{equation}

```yaml
search: false
```

**Note:** `search: false` only works to exclude posts when using **Lunr** as a search provider.
{: .notice--info}

To exclude files when using **Algolia** as a search provider add an array to `algolia.files_to_exclude` in your `_config.yml`. For more configuration options be sure to check their [full documentation](https://community.algolia.com/jekyll-algolia/options.html).

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