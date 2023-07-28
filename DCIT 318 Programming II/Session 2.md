# Defining a class
```csharp
// Student.cs
using System;

namespace DCIT318
{
	public class Student
	{
		public Student() {}// This is the constructor of the class
	}
}
```

# Access Modifiers
1. *private* - Member is accessible inside the type only. Default
2. *internal* - Member is accessible inside the type and any type in the same assembly
3. *protected* - Member is accessible inside the type and any type that inherits it
4. *public* - Member is accessible everywhere
5. *internal protected* - Combines internal and protected
6. *private protected* - Member is accessible inside the type, *or* any type that inherits from the type and is in the same assembly. Only availabe from **C# 7.2**

# Class Members
This includes all members declared in the class (except *constructors* and *finalizers*), and all members declared in all classes in the inheritance hierarchy
- **Fields** - Variables declared at class scope. May be built-in numeric type or an instance of another class
- **Constants** - Fields whose value is set at compile time and cannot be changed
- **Methods** - Defines the actions a class can perform.
- **Properties** - Methods in a class that are accesses as though being fields in that class
- **Indexers** - Enable an object to be indexed similar to an array
- **Operators** - Refers to overloaded operators in a class
- **Events** - Provide notifications about occurences, such as button clicks, to other objects

## Fields
A class or struct may have *instance* fields, *static* fields, or both.
- Generally declared as *private* or *protected*
- Stores data that must be **accessible to more than one type method** (struct or class) and must be **stored for longer that the lifetime of a single method**.
- Begins with an underscore `_` by convention 
```csharp
// Student.cs
using System;

namespace DCIT318
{
	public class Student
	{
		//private field
		private int _id;
		
	// The following are optional methods
		// Method to access the private field
		public int GetID()
		{
			return _id
		}
		
		// Method to set the value of the field
		public int SetID(id)
		{
			_id = id
		}
	}
}
```
The private field cannot be accessed directly, hence a method is created to access it

```csharp
// Program.cs
namespace DCIT318
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Student student = new Student();
			
			student.SetID(5)
			Console.Writeline(student.GetID()) // Prints 5
		}
	}
}
```

## Constants
Immutable values which are known at compile time and do not change for the life of the program
- Can be marked as any member type (*public*, *private* etc)
```csharp
// Student.cs
using System;

namespace DCIT318
{
	public class Student
	{
		//public constant
		public const float PI = 3.142f
	}
}
```

```csharp
// Program.cs
namespace DCIT318
{
	internal class Program
	{
		static void Main(string[] args)
		{
			Student student = new Student();
			
			Console.Writeline(Student.PI) // Prints the value of PI. Note the difference in 'Student'
		}
	}
}
```
Since it's a constant, it has to be accessed using the Class itself, not the object.

## Properties
A member that provides a flexible mechanism to read, write, or compute the value of a private field.
- Can be used as public data members, but are special methods called accessors
- A *get* accessor is used to retuen the property value, and *set* is used to assign a new value.
- A property can be
	- **read-write** : Has both getter and setter
	- **read-only** : Has only getter
	- **write-only** - Has only setter
```csharp
using System

namespace DCIT318
{
	public class Student
	{
		public string Name { get; set; }
	}
}
```
Private