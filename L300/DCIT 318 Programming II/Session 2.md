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
6. *private protected* - Member is accessible inside the type, *or* any type that inherits from the type and is in the same assembly. Only available from **C# 7.2**

# Class Members
This includes all members declared in the class (except *constructors* and *finalizers*), and all members declared in all classes in the inheritance hierarchy
- **Fields** - Variables declared at class scope. May be built-in numeric type or an instance of another class
- **Constants** - Fields whose value is set at compile time and cannot be changed
- **Methods** - Defines the actions a class can perform.
- **Properties** - Methods in a class that are accesses as though being fields in that class
- **Indexers** - Enable an object to be indexed similar to an array
- **Operators** - Refers to overloaded operators in a class
- **Events** - Provide notifications about occurrences, such as button clicks, to other objects
---
- **Constructors** - Methods that are called when the object is first created

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
- Begins with a capital letter by convention.
```csharp
// Student.cs
using System

namespace DCIT318
{
	public class Student
	{
		public string Name { get; set; }
		// Can also be simply written as
		public string Name;
		// read-only
		public string Name { get; }
		// write-only
		public string Name { set; }

		// Can be combined with a backing field
		private int _id;
		public int ID 
		{
			get
			{
				return _id * 10
			}
			set
			{
				_id = value
			}
		}
	}
}
```
**Properties** are similar to **Fields** in their creation. The difference b/n the two is that, since fields use *private* or *protected*, they do not have a default `get` or `set` accessor. Once *public* is used, there is a default getter and setter, allowing it to be a property. Note that in the field, there has to be other methods created to access the field and set it to a value.

From **C# 11**, a `required` member can be added to force initialization of a field or property
```csharp
// Course.cs
public class Course
{
	public required string CourseName { get; set; }
	public required string CourseCode; // Same thing
	
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
			Course course = new Course() {CourseName = "Programming II", CourseCode="DCIT318"}
		}
	}
}
```

## Methods
A code block that contains a series of statements
- Begins with an uppercase by convention
```csharp
// SimpleMath.cs
public class SimpleMath
{
	public int AddTwoNumbers(int num1, int, num2)
	{
		return num1 + num2
	}
	public int SquareANumber(int num)
	{
		return num ** 2
	}
}
```
Methods can be *overloaded* by having two or more methods in a class with the same name but different numbers, types, or order of parameters
```csharp
// SimpleMath.cs
public class SimpleMath
{
	public int AddNumbers(int num1, int, num2)
	{
		return num1 + num2
	}
	
	public int AddNumbers(int num1, int num2, int num3)
	{
		return num1 + num2 + num3
	}
	
	public int SquareANumber(int num)
	{
		return num ** 2
	}
}
```

## Constructors
Called whenever an instance of a class or struct is created
- A class or struct may have multiple constructors that take different arguements.
```csharp
// Student.cs
using System

namespace DCIT318
{
	private string name;
	private int id;

	public Student( string Name, int StudentID)
	{
		Name = name;
		StudentID = id;
	}
}
```
A private constructor is a special instance constructor used in classes which contain only static members. If a class has no public constructors and only private constructors, other classes cannot create instances of the class. Exception to this are nested classes
```csharp
// SimpleMath.cs
class NLog
{
	// Private Constructor
	private NLog(){}
	
	public static double e = Math.E;
}
```