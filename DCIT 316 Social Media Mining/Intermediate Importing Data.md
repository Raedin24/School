**urllib** package
- Provides interface for fetching data across the web
- `urlopen()` accepts URLs instead of file names
```Python
from urllib.request import urlretrieve
url = 'http://archive.ics.uci.edu/ml/machine-learning-databases/wine/wine-quality/winequality-white.csv'
urlretrieve(url, 'whinequality-white.csv')
```
- Can use `pandas` to directly read a csv from a website without first saving the file
```Python
url = 
```