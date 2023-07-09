Q1.

a) The .NET Framework provides a runtime environment for executing applications and a set of libraries and services for building software. C# is one of the primary languages used for developing applications on the .NET platform. The .NET Framework includes the necessary tools and libraries to compile, run, and manage C# code.

b) The key components of the .NET Framework include:

- Common Language Runtime (CLR)

- Base Class Library (BCL)


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

c) In C#, there are two main categories of types.

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

        Rectangle joinedRectangle = rectangle1 + rectangle2;
        double joinedArea = joinedRectangle.CalculateArea();

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
        if (FuelLevel > 0)
        {
            Console.WriteLine("Car is driving.");
            FuelLevel--;
        }
        else
        {
            throw new OutOfFuelException("Out of fuel!");
        }
    }
}

class Motorcycle : Vehicle
{
    public int FuelLevel { get; set; }

    public override void Drive()
    {
        if (FuelLevel > 0)
        {
            Console.WriteLine("Motorcycle is driving.");
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
        Motorcycle motorcycle = new Motorcycle { Make = "Honda", Model = "CBR500R", Year = 2021, FuelLevel = 0 };

        try
        {
            car.Drive();
            motorcycle.Drive();
        }
        catch (OutOfFuelException ex)
        {
            Console.WriteLine(ex.Message);
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
            new Student("Alice", 20),
            new Student("Bob", 22),
            new Student("Charlie", 19)
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

In the example above, the `Student` record is created with properties for name and age. The record implements the `IComparable<Student>` interface, which allows comparing students based on their ages. The `CompareTo` method is overridden to compare the ages. The `ToString` method is also overridden to display the name and age of a student.

An array of `Student` records is created, and the `Array.Sort` method is used to sort the array based on the students' ages. If any exception occurs during sorting, it is caught in a `catch` block, and an appropriate error message is displayed.