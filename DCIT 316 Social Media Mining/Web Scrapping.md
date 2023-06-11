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
	 '@' - used to refer to attributes
	 - xpath = '/html/body/\*'
	 Selects all children of the `body` element
- *contains* - can be used to select a all substrings which contain an expression
	 contains(@attribute-name, "string_expression")
	 xpath = '//\*[contains(@class, "class-1")]'
		 Will also choose \<p class="class-1 2">...\</p>, since "class-1" is a substring of "class-1 2"
	 xpath = '//\*[(@class, "class-1")]'
		 Will only choose if entire attribute is equal