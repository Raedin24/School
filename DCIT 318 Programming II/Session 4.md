# Collections
There are 2 ways to group object
- By creating an array of objects
- By creating a collection of objects
- Arrays are used when working with a fixed number of *strongly typed objects* (objects whose types are known from inception)
- A collection is a class and can grow and shrink dynamically
- If the collection contains elements of only one data type, one of the classes in the **System.Collections.Generic** namespace can be used
- There are *3* kinds of collections
	1. **System.Collections.Generic** classes
	2. **System.Collections.Concurrent** classes
	3. **System.Collections** classes

---
Classes in System.Collections do not store elements as specific types, but as objects of type *Object*. eg ArrayList, Hashtable, Queue, Stack
1. *ArrayList* 
	- Implements the **IList** interface. 
	- Not guaranteed to be sorted. 
	- Not recommended for new development, use generic **List<T\>** class
```csharp
ArrayList myAL = new ArrayList();
myAL.Add("Hello");

Console.WriteLine()
```
2. *Hashtable* 
	- Represents a collection of key/value pairs. 
	- Each element (ie. the pair) is stored in a **DictionaryEntry** object. 
	- Each entry is organised based on a hash code placed into a bucket.
	- Searches are made with the hash code only in a particular bucket, improving efficiency.
	-  Not recommended for new development, use generic **Dictionary<TKey, TValue>** class
3.  *Queue*
	- Represents a collection of FIFO objects
	- Implements a queue as a circular array
	- Three main operations can be performed
		- Enqueue - Adds an element to the end of the queue
		- Dequeue - Removes the oldest element from the start of the queue
		- Peek - Returns the oldest element without removing it from the queue
	-  Not recommended for new development, use generic **Queue<T\>** class 
4. *Stack*
	- Represents a LIFO non-generic collection of objects
	- Three main operations can be performed
		- Push - Inserts an element at the top of the stack
		- Pop - Removes the top element of the stack
		- Peek - Returns the element at the top of the stack without removing it.
	-  Not recommended for new development, use generic **Stack<T\>** class 

## Disadvantages of Non-generic Collections
1. Error prone: Requires frequent casting between object and the desired type. Easier to put the wrong type in the collection since the compiler can't check for type consistency
2. Lower performance: Non-generic collections require value types to be boxed as objects, unlike generic collections

# Generics
They are classes, structs, interfaces, and methods that have placeholders / type parameters for one or more of the types they use
- Classes can be created once, and then have the type specified using the generic approach
- Allow you to tailor a method, class, structure or interface to the precise data type it acts upon.
- Benefits include increased code reusability and type safety
```csharp
public class SimpleGenericClass<T>
{
	public T Field;
}

SimpleGenericClass<string> g = new SimpleGenericClass<string>();
```
### Generic Methods
A method with two parameter lists:
- A list of generic type parameters
- A list of formal parameters
```csharp
T GenMethod <T> (T arg) //<T> is the list of generic type parameters, (T arg) is the list of formal parameters
{
	T a = b;
	//...
	return a;
}

T NonGenMethod (T arg) // Non-generic even though it uses generic type of class
{
	T a = b
	//...
	return a;
}
```
`Methods in a generic class can be generic or non-generic`

**Advantages of Generics**
- Type safety
- Less code
- Increased code reusability
- Better performance (for value types)

**Disadvantages of Generics**
- Enumerations cannot have generic type parameters
- Lightweight dynamic methods cannot be generic
- A nested type that is enclosed in a generic type cannot be instantiated unless types have been assigned to the type parameters of all enclosing types

### Generic Collections
Useful when every item in the collection has the same data type.
- Enforces strong typing by allowing only the desired type to be added
1. *Dictionary<TKey, TValue>* class
	- A collection of keys and values
	- **Tkey, Tvalue** - The type of keys and values in the dictionary respectively
	- Can alternatively use *SortedDictionary<TKey, TValue>*
```csharp
Dictionary<string, string> myDict = new Dictionary<string, string>();
```
  
2. *List<T\>* class
	- List of objects that can be accessed by index
	- Provides methods to search, sort and manipulate lists
	- Not sorted by default
```csharp
List<string> someList = new List<string>();
```

3. *Queue<T\>* class
	- Has same 3 main operations seen earlier
```csharp
Queue<string> someQueue = new Queue<string>();
```

4. *SortedList<TKey, TValue>* class
	- A sorted collection of key/value pairs. Sorted by key
	- Based on the *IComparer<T\> implementation
	- Requires a comparer implementation to sort and perform comparisions
```csharp
SortedList<string, string> myList = new SortedList<string, string>();
```

5. *Stack<T\>* class
	- Represents a LIFO collection of instances of a specified type
	- Implemented as an array
	- Useful when information needs to be accessed in reverse order
`Stacks and queues are useful for temporary storage of information`
```csharp
Stack<string\> numbers = new Stack<string\>();
```
