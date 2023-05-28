# Classes and Objects
- Almost everything in Python is an object
- A class is an object constructor, a blueprint for creating objects
##  \_\_init\_\_()
- All classes have an `__init__()`, which is executed when the class is initiated
- It's used to assign values to object properties
```Python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age

p1 = Person("Kofi", 19)
```
- `self` is used to refer to the 

## Methods
- Objects can contain methods. Methods are functions that belong to the object.
```Python
class Person:
	def __init__(self, name, age):
		self.name = name
		self.age = age
		
	def myfunc(self):
		print("Hello, my name is " + self.name)

p1 = Person("Kofi", 19)
p1.myfunc()
```

# Containers and Built in Functions
num
check if num modulo 2 is 0
if yes, print num
if no, ans = num * 2
print ans

index c = 0
string output = ""
while c < length of max(word1, word2):
	add word1[c] to output
	add word2[c] to output
only works if len(word1 == word2)
if c = len(word1):
	add rest of word2
elif c = len(word2):
	add rest