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
url = 'https://assets.datacamp.com/production/course_1606/datasets/winequality-red.csv'
df = pandas.read_csv(url, sep=';')
```

```Python
import pandas as pd

# Assign url of file: url
url = 'https://assets.datacamp.com/course/importing_data_into_r/latitude.xls'

# Read in all sheets of Excel file: xls
xls = pd.read_excel(url, sheet_name=None)

# Print the sheetnames to the shell
print(xls.keys())

# Print the head of the first sheet (using its name, NOT its index)
print(xls['1700'].head())
```

- `urlretrive()` performs a GET request and saves the data locally
**GET requests using urllib**
```Python
from urllib.request imoprt urlopen, Request
url = "https://www.wikipedia.org/"
request = Request(url)
response = urlopen(request) # Returns an HTTP Response object
html = response.read() # Apply read method of Response object. Returns HTML as a string
response.close()
```