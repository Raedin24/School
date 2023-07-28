**Inheritance** is an attribute of OOP. It allows one class (called the derived or subclass) to inherit properties and behaviors from another class (called the base or superclass). The derived class can then extend or override the functionality of the base class while also adding its own unique features.
- Only applies to **class** and **interface** types
- Members which are not inherited are **static constructors**, **instance constructors**, and **finalizers**.
- Derived classes can *override* inherited members by providing an alternate implementation. 
- To override, the member in the base class must be marked with  the `virtual` keyword. By default, base class members are *not* marked as virtual and cannot be overridden
```csharp
public class SimpleMath
{
	public virtual int Add()
	{
		// Some math action
	}
}

public class ComplexMath : SimpleMath
{
	public override int Add()
	{
		// Some other math action
	}
}
```

In the .NET type system, all types implicitly inherit from the `Object` class or a type derived from it. This concept is known as "implicit inheritance" or "default inheritance."

1. **Object Class**: In .NET, the `Object` class is the root class for all other classes. It is defined in the `System` namespace and serves as the base class for almost all types in the .NET Framework. The `Object` class provides fundamental methods and properties that are inherited by all other classes in the .NET type system.

2. **Single Inheritance**: In .NET (and many other programming languages like C#), classes can have only one direct base class. This is known as single inheritance. In other words, a class can inherit from only one other class, which ensures a clear hierarchical relationship among classes.

4. **Implicit Inheritance from Object**: When a new class is created in .NET and the base class is not explicitly specified (via the `: BaseClassName` syntax), the new class will implicitly inherit from the `Object` class by default. This means that even if you don't write `class MyClass : Object`, the compiler treats it as if you did.

Here's a simple example to illustrate this concept:

```csharp
// Implicitly inherits from Object
class MyClass
{
    // Class implementation here
}
```

In the example above, the `MyClass` implicitly inherits from the `Object` class. As a result, `MyClass` will have access to methods and properties defined in the `Object` class, such as `ToString()`, `Equals()`, and `GetHashCode()`, among others.

This implicit inheritance from `Object` ensures that all types in .NET share some common characteristics and can be treated in a uniform way. For instance, you can use a variable of type `Object` to hold any object, regardless of its actual type, allowing for greater flexibility and polymorphism in .NET applications.

- The `abstract` keyword enables the creation of classes and class members that are incomplete and must be implemented in a derived class
```csharp
public abstract class A
{
	public abstract void SomeAction(int i);
}
```

- An interface defines a contract i.e. members that any class implementing it must have.
- When a class/struct implements an interface, they provide concrete implementations for all the members declared in the interface, hence adhering to the contract.
- An interface may inherit multiple base interfaces
- A class or struct may implement multiple interfaces
`Interfaces begin with `
```csharp
interface I
```