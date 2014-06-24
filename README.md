Windows-C_Sharp-Coding-Style
============================

Radya Labs C# Coding Style


## Introduction
This document is describe guidelines and recommendations when developing application using C# language. Our main goal is to define a consistent format and style for every source code produced by all Radya Labs developer.
 
##	Scope
This coding guideline only apply to C# suage and .NET framework common type system. C# is go-to language choice for every project developed by Radya Labs. 


## Naming Convention
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


General Guide : 

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
