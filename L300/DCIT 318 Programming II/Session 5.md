# Exceptions
Provide a structured, uniform, type-safe way of handling system level and application-level errors
- All exceptions are types derived from *System.Exception*
- If no exception handler is present, the program stops executing with an error message
- A `try` block is put around the statements that might throw exceptions
- A `catch` block defines an exception variable. Can be used to obtain more information about the type of exception that occured
- A `throw`	 keyword is can be used to explicitly generate program exceptions

### System.Exception class
The base type of all exceptions
Properties:
1. **Message** - A read-only property that contains a human-readable description of the cause of the exception. Of type *string*
2. **InnerException** - A read-only property. If value is non-null, it refers to the exception that caused the current exception. Of type *Exception*

### Exception Handling
- A `try` block is used to partition code that might be affected by an exception
- A `catch` block is used to handle any resulting exceptions
- A `finally` block contains code that is run whether or not an exception is thrown in the `try` block
```csharp
try
{
	// Some code
}

catch (SomeException ex)
{
	// Code to handle the exception
}

finally
{
	// Some code
}
```

`Never catch the base class System.Exceptions without rethrowing it at the end of the catch block`

### Creating and Throwing Exceptions
Exception classes can be created by deriving from `Exception`
- The derived class should define 3 main constructuors
	- One *parameterless* constructor
	- One that sets the *message* property
	- One that sets both the *Message* and *InnerException* properties
- When a new property is added, the `ToString()` method should be overriden to return the added information
```csharp
[Serializable] // Saves the object in a string format, from which it can be recreated
public class NewException : Exception
{
	public NewException() : base(){} // Parameterless
	
	public NewException(string message) : base(message){} // Sets message property
	
	public NewException(string message, Exception inner) : base(message, inner){}
} // Sets message and inner exception property
```

`Exceptions can be system-generated or compiler-generated`

### Throwing Exceptions
- Do not use exceptions to change the flow of a program
- Exceptions should not be returned as a return value or parameter instead of being thrown
- Do not throw these exceptions intentionally
	- System.Exception
	- System.SystemException
	- System.NullReferenceException
	- System.IndexOutOfRangeException