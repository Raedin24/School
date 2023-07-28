**Inheritance** is an attribute of OOP that allows for a definition of a child class that reuses, extends, or modifies the behaviour of a parent class
- Only applies to **class** and **interface** types
- Members which are not inherited are **static constructors**, **instance constructors**, and **finalizers**.
- Derived classes can *override* inherited members by providing an alternate implementation. 
- To override, the member in the base class must be marked with  the `virtual` keyword. By default, base class members are not marked as virtual and cannot be overridden
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