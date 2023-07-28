# Defining a class
```csharp
// Test.cs
using System;

namespace DCIT318
{
	public class Test
	{
		public Test() {}// This is the constructor of the class
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

```