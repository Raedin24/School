# Scrapping and Parsing
### **urllib** package
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
# Package the request
request = Request(url)
# Returns an HTTP Response object
response = urlopen(request) 
# Apply read method of Response object. Returns HTML as a string
html = response.read() 
# Close request
response.close()
```

### **requests** package
- The higher level `requests` library can be used to package, send the request, and catch a response with a single function
```Python
import requests
url = "http://www.datacamp.com/teach/documentation"
# Packages the request, send the request and catch the response
r = requests.get(url)
# Extract the response using the 'text' attribute
text = r.text
```

## *BeautifulSoup* package

```Python
# Import packages
import requests
from bs4 import BeautifulSoup

# Specify url: url
url = 'https://www.python.org/~guido/'

# Package the request, send the request and catch the response: r
r = requests.get(url)

# Extracts the response as html: html_doc
html_doc = r.text

# Create a BeautifulSoup object from the HTML: soup
soup = BeautifulSoup(html_doc)

# Prettify the BeautifulSoup object: pretty_soup
pretty_soup = soup.prettify()

# Print the response
print(pretty_soup)
```
+ Using `find_all()` to get a particular tag
```Python
soup = BeautifulSoup(html_doc)

# Find all 'a' tags
a_tags = soup.find_all('a')

# Print URLs in a_tags
for link in a_tags:
	print(link.get('href'))
```

# Intro to APIs and JSONs
**API** = Application Programming Interface
- A set of protocols and routines for building and interacting with software applications
- Basically allows 2 software programs to communicate
## Connecting to an API
```Python
import requests
url = 'http://www.omdbapi.com/?t=hackers'
r = requests.get(url)
json_data = r.json()
for key, value in json_data.items():
	print(key + ':', value)
```
`?...` is known as a *Query String*. They are parts of URLs that do not fit into the conventional path structure
- The part after the question mark is the query being made to the API
**JSON** = JavaScript Object Notation
- Standard form for transferring data between APIs
## Loading JSONs in Python
1. From a local directory
```Python
import json

with open('snakes.json', 'r') as json_file:
	json_data = json.load(json_file)
```

# Using Tweepy
## Setup 
```Python
# Authentication
import tweepy, json
access_token = "..."
access_token_secret = "..."
consumer_key = "..."
consumer_secret = "..."

# Create Streaming object
stream = tweepy.Stream(consumer_key, consumer_secret, access_token, access_token_secret)
# Apply filter method to stream tweets containing keywords
stream.filter(track=['apples', 'oranges'])
```

## Load and explore data
```Python
# Import package
import json

# String of path to file: tweets_data_path
tweets_data_path = 'tweets.txt'

# Initialize empty list to store tweets: tweets_data
tweets_data = []

# Open connection to file
tweets_file = open(tweets_data_path, "r")

# Read in tweets and store in list: tweets_data
for line in tweets_file:
	tweet = json.loads(line)
	tweets_data.append(tweet)

# Close connection to file
tweets_file.close()

# Print the keys of the first tweet dict
print(tweets_data[0].keys())
```

## Twitter data to DataFrame
```Python
import pandas as pd

# Build DataFrame of tweet texts and languages
df = pd.DataFrame(tweets_data, columns=['text', 'lang'])

# Print head of DataFrame
print(df.head())
```