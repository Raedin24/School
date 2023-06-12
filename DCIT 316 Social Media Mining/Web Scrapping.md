**Pipeline
1. Setup
	1. Define objective
	2. Identify sources to help achieve result
2. Acquisition of data
	1. Access data
	2. Parsing and extracting data into useful structures
3. Processing

## XPath Notation
- Can be used to traverse html tags
- Similar to a directory
	- xpath = '/html/body/div[2]'
	 Single forward slash looks forward one generation
	 [2] is used to refer to the second `div` element
	 - xpath = '//table'
	 Double forward slash '//' used to look for all future generations instead of a single generation
	 The above navigates to all `table` elements instead of a single one
	 - xpath = '/html/body/div[2]//table'
	 Restricts the search to all `table` elements in the second `div`;
	 - xpath = '//div[@class="div-class"]'
	 Specifically looks for all `div` elements that have `class` attribute to be "div-class"
	 '@' - used to refer to attributes
	 - xpath = '/html/body/\*'
	 Selects all children of the `body` element
- *contains* - can be used to select a all substrings which contain an expression
	 contains(@attribute-name, "string_expression")
	 xpath = '//\*[contains(@class, "class-1")]'
		 Will also choose \<p class="class-12">...\</p>, since "class-1" is a substring of "class-12"
	 xpath = '//\*[(@class, "class-1")]'
		 Will only choose if entire attribute is equal
- **attributes**
	 To get to a specific attribute, first direct to the element containing the attribute
	 xpath = '/html/body/div/p[2]/@class' - Selects class attribute from all the paragraph children 
	 Create an xpath to the href attribute
	 xpath = '//p[@id="p2"]/a/@href'

**Scrappy Selector**
- Using an `xpath` call within a `Selector` creates a new `Selector` s of specific elements
	- Returns a `SelectorList` of `Selector` objects
- Use `extract()` to obtain the information from the selector/selectorlist
- Use `extract_first()` to obtain the information from the selector/selectorlist

## CSS Locators
**Rosetta CSStone**
- `/` replaced by `>` (except first character)
	XPath: /html/body/div
	CSS Locator: html > body > div
-  `//` replaced by a blank space (except first character)
	XPath: //div/span//p
	CSS Locator : div > span p
- `[N] `replaced by `:nth-of-type(N)`
	XPath: //div/p[2]
	CSS Locator: div > p:nth-of-type(2)
```CSS
xpath = '/html/body//div/p[2]'
css = 'html > body  div > p:nth-of-type(2)'
```
- `@class` replaced by `.`
	 Xpath = '/html/body/div/p[@class="class-1"]'
	 CSS = 'html > body > div > p.class-1
- `@id` replaced by `#`
	 Xpath = '/html/body/div/p[@id="uid"]'
	 CSS = 'html > body > div > p#uid
-  `@attribute` replaced by `::`
	Xpath = '//p[@id="p2"]/a/@href'
	CSS Locator = 'p#p2 > a::attr(href)'
- Text Extraction
	sel.xpath('//p[@id="p-example"]/text()').extract() - All text within the current generation
	sel.xpath('//p[@id="p-example"]//text()').extract() - All text within current and future generations
	sel.css('p#p-example::text').extract() - All text within the current generation
	sel.css('p#p-example ::text').extract() - All text within current and future generations. Note the space before `::`

## Spiders
**Steps**
1. Required imports
```Python
import scrapy
from scrapy.crawler import CrawlerProcess
```
2.  Create Spider
```Python
class SpiderClassName(scrapy.Spider):
	name = "spider_name"
	# Code for spider
	...
```
3. Run Spider
```Python
# Initiate a CrawlerProcess
process = CrawlerProcess()

# Tel process which spider to use
process.crawl(YourSpider)

# Start crawling
process.start()
```

```Python
import scrapy
from scrapy.crawler import CrawlerProcess

class SpiderClassName(scrapy.Spider):
	name = "spider_name"
	
	# start_requests method
	def start_requests(self):
		urls = ["https://www.datacamp.com", "https://scrapy.org"]
		for url in urls:
			yield url
	
	# parse method
	def parse(self, response):
		pass
```
