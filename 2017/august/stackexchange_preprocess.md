# SQL

```sql
select * from Posts;
```

from https://data.stackexchange.com/datascience/query/new

# drop rows without tags

pandas.dropna(subset=['Tags'])

# extract tags

example: 

- input: `"<machine-learning><r><predictive-modeling>"` 
- output:  `['machine-learning', 'r', 'predictive-modeling']`

using regular expression: `<(.+?)>`

# filter out infrequent tags and rows without valid tags

`qs[mask]` requires `mask` and `qs` have the **same** index

re-index using `qs.index = mask.index`

# remove html entities

```python
class MLStripper(HTMLParser):
    def __init__(self):
        self.reset()
        self.strict = False
        self.convert_charrefs= True
        self.fed = []

    def handle_data(self, d):
        self.fed.append(d)

    def get_data(self):
        return ''.join(self.fed)


def strip_tags(html):
    s = MLStripper()
    s.feed(html)
    return s.get_data()
```

faster than using `beautiful_soup` (x10 times)