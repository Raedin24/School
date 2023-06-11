**Pipeline
1. Setup
	1. Define objective
	2. Identify sources to help achieve result
2. Acquisition of data
	1. Access data
	2. Parsing and extracting data into useful structures
3. Processing

**XPath Notation**
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