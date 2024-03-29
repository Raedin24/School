Q1.

a) The.NET Framework offers a runtime environment for running programs as well as a collection of libraries and services for creating software. C# is one of the languages available for creating apps on the .NET framework. The framework contains the tools and libraries required to create, run, and maintain C# programs.

b) The key components of the .NET Framework include:

- Common Language Runtime (CLR) 

- Class Library 


c) i. The .NET Framework compiler converts source code into Microsoft Intermediate Language. The intermediate language can then be executed by the CLR. The CLI defines the rules and specifications for how different .NET languages should interoperate, allowing code written in one language to call and use code written in another language.

ii.  C# code can interact with code written in other .NET languages. Since all .NET languages share the common runtime environment and adhere to the CLI standards, they can interoperate seamlessly. 

Q2.

a) The basic syntax and structure of a C# program:

- Namespace declaration:  Used to organize classes and types into logical groups.

- Class declaration: C# programs consist of one or more classes. A class is a blueprint for creating objects and defines the properties, methods, and events associated with those objects.

- Main method: Serves as the entry point for the program. The execution of the program starts from the Main method.

- Statements and expressions: Define the logic and behavior of the program. Statements perform actions, while expressions produce values.

b) i. A class is a blueprint for creating objects and defines the properties, methods, and events associated with those objects. Classes provide a way to create objects, which are instances of a class. Objects have their own data and methods, and can interact with other objects.

ii. To define a class in C#,  use the `class` keyword followed by the class name:

```csharp
public class Trial
{
	...
}
```

To create objects from a class,  use the `new` keyword followed by the class name and any necessary arguments for the constructor (if defined):

```csharp
Trial trial = new Trial();
```

c) Difference between Value and Reference types:

- Value types: Value types store their data directly and are allocated on the stack. They include primitive types such as `int`, `float`, `bool`, `char`, and `structs`. When a value type is assigned to a new variable , a copy of the value is made. When the new variable is modified, the original data is not affected.

- Reference types: Reference types store memory addresses references to the actual data and are allocated on the heap. They include classes, interfaces,  and strings. When a reference type is assigned to a new variable, a copy of the reference is made, pointing to the same original data. When the new variable is modified, the original data is also changed.




Q3.

```csharp
using System;

interface IMeasurable
{
    double CalculateArea();
}

struct Rectangle : IMeasurable
{
    public double Width { get; set; }
    public double Height { get; set; }

    public double CalculateArea()
    {
        return Width * Height;
    }

    public static Rectangle operator +(Rectangle r1, Rectangle r2)
    {
        return new Rectangle
        {
            Width = r1.Width + r2.Width,
            Height = r1.Height + r2.Height
        };
    }
}

class Program
{
    static void Main()
    {
        Rectangle rectangle1 = new Rectangle { Width = 5, Height = 3 };
        Rectangle rectangle2 = new Rectangle { Width = 2, Height = 4 };

        double area1 = rectangle1.CalculateArea();
        double area2 = rectangle2.CalculateArea();

        Rectangle combinedRectangle = rectangle1 + rectangle2;
        double combinedArea = combinedRectangle.CalculateArea();

        Console.WriteLine("Area of rectangle 1: " + area1);
        Console.WriteLine("Area of rectangle 2: " + area2);
        Console.WriteLine("Area of combined rectangle: " + combinedArea);
    }
}
```

Q4.

```csharp
using System;

class OutOfFuelException : Exception
{
    public OutOfFuelException(string message) : base(message)
    {
    }
}

class Vehicle
{
    public string Make { get; set; }
    public string Model { get; set; }
    public int Year { get; set; }

    public virtual void Drive()
    {
        throw new OutOfFuelException("Out of fuel!");
    }
}

class Car : Vehicle
{
    public int FuelLevel { get; set; }

    public override void Drive()
    {
		while (FuelLevel > 0){
			Console.WriteLine("Driving car.");
			FuelLevel--;
		}
		throw new OutOfFuelException("out of fuel!");
    }
}

class Motorcycle : Vehicle
{
    public int FuelLevel { get; set; }

    public override void Drive()
    {
        if (FuelLevel > 0)
        {
            Console.WriteLine("Riding motorcycle.");
            FuelLevel--;
        }
        else
        {
            throw new OutOfFuelException("Out of fuel!");
        }
    }
}

class Program
{
    static void Main()
    {
        Car car = new Car { Make = "Toyota", Model = "Camry", Year = 2022, FuelLevel = 2 };
        
        Motorcycle motorcycle = new Motorcycle { Make = "Kawasaki", Model = "Ninja H2R", Year = 2023, FuelLevel = 0 };

        try
        {
            car.Drive();
        }
        catch (OutOfFuelException ex)
        {
            Console.WriteLine("Car " + ex.Message);
        }
		        try
        {
            motorcycle.Drive();
        }
        catch (OutOfFuelException ex)
        {
            Console.WriteLine("Motorcycle " + ex.Message);
        }
    }
}
```

Q5.

```csharp
using System;
using System.Collections.Generic;

record Student(string Name, int Age) : IComparable<Student>
{
    public int CompareTo(Student other)
    {
        return Age.CompareTo(other.Age);
    }

    public override string ToString()
    {
        return $"Name: {Name}, Age: {Age}";
    }
}

class Program
{
    static void Main()
    {
        Student[] students = {
            new Student("Kwame Appiah", 20),
            new Student("Bob Marley", 25),
            new Student("Alexander IV", 19)
        };

        try
        {
            Array.Sort(students);
            foreach (var student in students)
            {
                Console.WriteLine(student);
            }
        }
		
        catch (Exception ex)
        {
            Console.WriteLine("An error occurred during sorting: " + ex.Message);
        }
    }
}
```

