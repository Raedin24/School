# Intro to .NET
- The **.NET Framework** is an integrated software development environment that provides programmers a single platform to develop Windows and Web applications
**Core Components**
1. Common Language Runtime (CLR)
2. Common Type System (CTS)
3. Common Language Specification (CLS)
4. Base Class Library (.NET Framework Class Library)
5. ASP.NET and ASP.NET Ajax
6. ADO.NET
7. WPF and WCF
8. Windows Forms
**Advantages**
1. *Consistent Programming Model* - Different tasks such as Database Connectivity, Reading and Writing to files can be performed with just this model
2. *Language Interoperability* - Code written in one language can be used in another language
3. *Automatic Management of Resources* - Garbage Collection(part of CLR) allocates and de-allocates all resources such as files and database connections automatically
4. *Ease of Deployment* - Deployments are done in the form of assemblies which are single, logical deployment units. Hence, registers do not need to store info about components and applications.

## .NET Framework
![[Pasted image 20230727203108.png]]
### CLR
- Provides essential runtime services such as automatic memory management and error handling
- Performs just-in-time compilation
- Manages memory, thread execution, type safety verification and garbage collection
- Uses the *CTS*  to define a standard set of types, and rules for creating new types
- Converts source code into Microsoft Intermediate Language(MSIL). The intermediate language can then be executed by the CLR. The CLI defines the rules and specifications for how different .NET languages should interoperate, allowing code written in one language to call and use code written in another language.

 An **assembly** consists of
 - Manifest - Is a catalog of component metadata. Contains *assembly name, version, assembly file list, type references, scope*
 - Module - Refers to a binary (EXE or DLL). Contains *type definitions* such as classes, interfaces and structures
	 - Metadata
	 - MSIL
`MSIL code cannot be executed without a Manifest associated with it`

# C\#
- A type-safe, OOP language that exploits XML-based Web sevices on the .NET platform
- Features
	- Simplicity
	- Type safety
	- Version Control
	- Compatibility
	- Object Orientation
- **Key Features**
	- Nullable value type
	- Enumerations
	- Delegates
	- Direct memory access
	- Lambda expressions
![[Pasted image 20230727205730.png]]
**Program Structure**
- *Namespace* - Contains types and other namespaces
- *Type Declaration*
	- **Class** - provides a template for creating instances (objects) that share the same structure and behavior defined within the class.
	- **Struct**
	- **Interface** - A contract that defines a set of method and property signatures. It does not contain any implementation for these members; instead, it declares what methods and properties a class implementing the interface should have. An interface defines the "what" but not the "how" of an object's behavior.
	- **Delegate**
	- **Enum**
- *Members* - Constants, fields, methods, events, constructors, destructors
**Type System**
1. *Value Type* - Directly contains data. Cannot be null. When a value type is assigned to a new variable, a copy of the value is made. When the new variable is modified, the original data is not affected. Includes **primitives**, **enums**, **structs**.
2. *Reference Type* - Contains references to objects. May be null. When a reference type is assigned to a new variable, a copy of the reference is made, pointing to the same original data. When the new variable is modified, the original data is also changed. Includes **classes**, **interfaces**, **arrays**, **delegates**

### Classes
- Single inheritance
- Multiple interface implementation
- Members: Constants, fields, methods, events, operators etc.
- Member access: **protected**, **public**, **internal**, **private**.
### Structs
- No inheritance
- Stored in-line, not heap allocated
- Assignment copies data, not reference
- Includes: **int**, **float**, **double** etc.
Structs have more efficient use of memory than classes. Also, there is less garbage collector pressure as there is no heap allocation
