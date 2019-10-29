---
title:  "What is Dirichlet Distribution?"
search: false
---

Customers connect to contact center of a bank for a variety of reasons. 
One of the main contact reasons involves fraud. Suppose that you are trying to
predict the possibility of a fraud call on a certain day. Since a call can be
associated with more than one reason or call center agents usually enter very 
general descriptions as call intentions, we need to listen to call records to
determine call intentions accurately. However, number of calls coming to 
a contact center during a day is very high and it is not possible to listen 
all calls. One way is to listened t


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