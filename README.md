Windows-C_Sharp-Coding-Style
============================

Radya Labs C# Coding Style


## Introduction
This document is describe guidelines and recommendations when developing application using C# language. Our main goal is to define a consistent format and style for every source code produced by all Radya Labs developer.
 
##	Scope
This coding guideline only apply to C# suage and .NET framework common type system. C# is go-to language choice for every project developed by Radya Labs. 


## Naming Convention

###Overview
* Project File 	: 	PascalCase
* Source Files	:	PascalCase
* Other Files		:	PascalCase
* Namespace		:	PascalCase
* Class or Struct	:	PascalCase
* Interface		:	PascalCase
* Method			:	PascalCase
* Field			:	PascalCase, _PascalCase in private
* Constant		:	PascalCase, _PascalCase in private
* Static Field	:	PascalCase, _PascalCase in private
* Enum			:	PascalCase
* Event			:	PascalCase
* Inline Variable	:	camelCase
* Parameter		:	camelCase


###General Guide

1.  Always use PascalCase and camelCase for name of entity
2.  Avoid All CAPS and all lowercase for name
3.  Never declare variables using only case letter difference. Give meaningful name
4.  Never use name with numeric prefix
5.  Avoid use numeric suffix in name or identifier
6.  Always use meaningful and specific name
7.  Variables and properties should describe an entity, not type or measurement
8.  Avoid Hungarian Notation!. For example : strName or iCount
9.  Avoid using abbreviation
10. Abbreviation only for common term and widely accepted
11. Never use C# keyword for identifier
12. Avoid use name that will be potentially conflict with .NET namespace or type
13. Avoid redundant prefix or suffix that does not explain more about an identifier. 

E.g : 

```csharp
public enum ColorsEnum { }
public class CVehicle { }
public struct RectangleStruct { }
```

14. Avoid use parent class name in a property

```csharp
Customer.Name not Customer.CustomerName
```

15. Try to add "Can","Is","Has" prefix to boolean variable
16. Add "Average,Count,Sum,Min,Max" in a certain variable that reflect aggregation

###Name and Syntax

**Project File**

Always use PascalCase that match root namespace name
RadyaLabs.csproject -> RadyaLabs.dll -> RadyaLabs

**Source File**

Always use PascalCase that match class name with file name. Avoid declare several class,enum or delegate in one file. Use descriptive name.

MyClass.cs become
```csharp
public class MyClass
    { }

```

**Resource or Embedded File**

Always use PascalCase and descriptive name.

**Namespace**

Try use PascalCase and name that match project title.

**Class**

Try use PascalCase. Use noun or noun phrase for class. Add suffix or part of parent class for child class

```csharp
	private class MyClass { }
    internal class SpecializedAtribute : Attribute { }
    public class CustomerCollection : CollectionBase { }
    public class CustomEventArgs : EventArgs { }
    private struct ApplicationSettings { }
```

**Interface**

Try use PascalCase. Always use 'i' prefix for name.

```csharp
	public interface ICustomer
    { }
```

**Method**

Try use PascalCase. Always use 'i' prefix for name.

```csharp
	public interface ICustomer
    { }
```

**Property**

Try use PascalCase. Property name should represent an entity. Do not use property name with 'Get' or 'Set' prefix.

```csharp
	  public string Name
        {
            get { }
            set { }
        }

```

In specific case when property is part of bindable class and an implementation of INotifyPropertyChanged or child class of ModelBase. Always PascalCase, if the API return different format, do formatting with decoration function of JSON.NET

```csharp
	 private string _Name;
        [JsonProperty(PropertyName = "NAME")]
        public string Name
        {
            get { return _Name; }
            set { _Name = value; NotifyPropertyChanged("Name"); }
        }
```

**Field (Public,Protected, or Internal)**

Try use PascalCase. Avoid non-private field. Use property instead.

```csharp
	public string Name;
	protected IList InnerList;
```

**Field (Private)**

Try use PascalCase with underscore (_) prefix.

```csharp
	private string _Name;
```

**Constant or static field**

Same as field

**Enum**

Try use PascalCase

```csharp
	public enum CustomerTypes
        { 
            Consumer,
            Commercial
        }

```

**Variables (inline)**

Always camelCase.Avoid use single character like 'X' or 'Y' except in loop-block. Avoid using variables name that indicate an order, like text1,text2 or text3

**Variables (inline)**

Always camelCase

```csharp
	public void Execute(string commandText, int iterations) { }
```

##Coding Style##

###Formatting###
1. Never declare more than 1 namespace in a file
2. Avoid write more than 1 class in a file
3. Always use {} in conditional statement except for one line statement code
4. Declare variable separately. Do not declare in one line statement
5. Place 3rd library using "using" statement in the beginning of the file
6. Group class implementation region according to this order :
    a. Member
	b. Constructor
	c. Nested enums,struct
	d. Properties
	e. Methods
7. Declare identifier according to this order :
    a. Private
	b. Internal
	c. Protected
	d. Public
8. Group interface implementation using #region directive
9. Declare property in different line. This also apply to assembly, method, member and parameter

###Code Commenting###
1. All comments should be in same language and include punctuation mark
2. Use // or ////
3. Do not use "flower box" to mark a comment block
```csharp
		public void Execute(string commandText, int iterations) { }
```
4. Use inline comment to explain assumption, issue or an algorithm
5. Do not use inline comment to explain obvious code. It should be self-documentted
6. Add comment using certain keyword to classify to-do task to ease the reader
```csharp
		//TODO : Please database code here
        //UNDONE : Remove this function due to errors
        //HACK : Temporary fix until able to refactor

```
7. Always use /// to describe a method
```csharp
	/// <summary>
    /// 
	/// </summary>
```

##Language Usage##
###General###
1. Do not omit the access modifier. Declare identifier explicitly.
```csharp
	//Bad!
	void WriteEvent(string message) { }

	//Good!
	private void WriteEvent(string message) { }
```

###Variables & Types###
1. Try to initialize variable when it is declared
2. Always choose the simplest of data type
3. Always use built-in C# if it is available
```csharp
	short NOT System.Int16
	int NOT System.Int32
	long NOT System.Int64
	string NOT System.String
```
4. Always declare member variable as private. Use property for access
5. Try to use int type for non-float value
6. Only use long for variable that potentially  more than the int size
7. Try to use double for fractional numeric to ensure decimal precision
8. Only use float for numeric fractional that not match with double and decimal
9. Only use float if we know the consecuence
10. Try to use decimal if we need fractional number that rounded for math. 
11. Avoid sbyte,short,uint and ulong usage except it is used for interoperability (P/Invoke) with native library
12. Avoid numeric usage for magical value for reference. Use constant isntead
13. Avoid string usage, use string that come from Resource, cosntant, configuration file and registry
14. Only declare constant for simple data type, not for complex type
15. Avoid direct casting for object. Use "as" operator and check for null value
16. Always to choose generic collection that provided by language feature
17. Try to use String.Format() or StringBuilder instead of concatenation operation
18. Do not concatenate in a loop
19. Do not compare string using String.Empty or "" or use String.Lenght == 0

###Flow Control###
1. Avoid recursive function
2. Do not modify item in foreach statement
3. Avoid boolean validatoin using true or false value

  ```csharp
	 //bad
	is (isvalid == true)
	{}


	//good
	if (isvalid)
	{}
  ```
  
4. Avoid assignment in conditional statement
5. Use swith/case statement for simple operation
6. Use nested if/else instead of switch/case for complex operation
7. Try to use polimorphism instead of swich/case

###Other###
1. Avoid method usage with more than 5 parameters
2. Change parameter methods that more than 5 parameters into object type

##XAML Usage##
1. Always use control name that represent its value
  
  ```xml
	<TextBlock x:Name="TextBlockRoomField" Text="ROOMS" FontSize="42"></TextBlock>
      	<TextBox x:Name="TextBoxRoomValue"/>
  ```
  
2. Alwayse use method/event handler na me with prefix “On<nama kontrol><nama method>”.
  
  ```xml
	<TextBlock Tap="OnTextBlockRoomFieldTapped" x:Name="TextBlockRoomField" Text="ROOMS" FontSize="42"></TextBlock>
  ```







