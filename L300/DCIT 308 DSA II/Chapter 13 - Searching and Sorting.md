**Searching** is the process of finding a designated *target element* within a group of items, or determining that the target does not exit within the group
- The group of items to be searched is called the *search pool*
- In **Java**, the comparison process can be done using the `Comparable` interface.
	- Contains the method `compareTo` , which return whether the object is less, equal to, or greater than that being compared with
	- Allows an algorithm to be implemented without regard to a particular class(alias *polymorphism*)

# Searching
## Linear Search
- Starts at the beginning of the list and compares each value to the target element.
- Accepts an array of elements and the target item
- Does not require the elements in the search pool to be in a particular order
## Binary Search
- Requires the search pool to be sorted
- Starts in the middle of the list
	- If target is found, terminates
	- If not, compares whether midpoint is higher or lower than target
	- Eliminates other half of the list based on comparison.
	- Repeats until target is found or there are no more comparisons to make

# Sorting
## Selection Sort
 - Sorts a list of values by repetitively putting a particular value into its sorted position.
 - Scans the entire list to find the smallest value
	 - Exchange with value in first position
	 - Scan the rest of the list (excluding the first) for the smallest value
	 - Exchange with value in second position
	 - Repeat until sorted
 - Uses 2 loops to sort the array
	 - Outer loop controls position where the next smallest value will be stored
	 - Inner loop finds the smallest value by scanning all positions greater than or equal to index in outer loop
- Sorted array is in ascending order since the smallest element is found first. Can be switched to largest element for descending order
## Insertion Sort
- Sorts a list of values by repetitively inserting a particular value into a subset of the list that has already been sorted.
- Each unsorted element is inserted at the appropriate position until the list is sorted
- Sort the first 2 values in the list
	- Insert the 3rd value in the sorted position relative to the first 2 sorted