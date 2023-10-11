# Microsoft C\#

- Object-oriented language
- Similar in syntax to **C++** and **Java** 
```C#
namespace LectureOne
{
	internal class Program
	{
		static void Main(string[] args)
		{
		Console.WriteLine("Hello, World!");
		}
	}
}
```
`static` means that there should be only one copy of the method or variable in memory
In OO, it means that an object does not need to be created to call the method. ie. it can be called using `class.method`.
`namespace` is used to avoid name collision. ie. the same class name can be used as long as it's not in the same `namespace`
`class` is a blueprint of an object. It describes the methods
## Classes
- **C#** classes have a single inheritance
- Has multiple interface implementation
- An *interface* is a class-like structure that has methods that have not yet been implemented. It basically holds the base methods that all objects created out of that class should contain.
> In C#, add 'f' after a float to show that a variable is a float. 
> Add 'm' after a decimal to show that the variable type is decimal

```C#
switch:
	case 1:
```