```Python
# Single input
n = int(input())

# Take 2 inputs
n, m = map(int, input().split)

# Taka an array of integers as input
arr = list(map(int, input().split()))

# To loop over a list, accessing the elements themselves
for element in arr:
	print(element)

# To loop over a list, using the indexs
for i in range(len(arr)):
	print(arr[i])

# Conver
element = set(arr)

# To iterate over a dictionary
for key, values in store.items():
	print("key=", key)
	print("value", values)

# To iterate over a dictionary using the keys
for key in store:
	print(key)
```