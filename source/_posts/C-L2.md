---
title: C# Study Note2
subtitle: Data Types and Variables
date: 2017-07-01 12:42:10
tags: C#
---
## Data Types :

The variables in C#, are categorized into the following types:
### Value types
  * derive from System.ValueType, contains data directly

Type|Represents|Range|Default Value
---|---|---|---
bool|Boolean value|True or False|False
byte|8-bit unsigned integer|0 to 255|0
char|16-bit Unicode character|U +0000 to U +ffff|'\0'
decimal|128-bit precise decimal values with 28-29 significant digits|(-7.9 x 10^28 to 7.9 x 10^28) / 100 to 28|0.0M
double|64-bit double-precision floating point type|(+/-)5.0 x 10^-324 to (+/-)1.7 x 10^308|0.0D
float|32-bit single-precision floating point type|-3.4 x 10^38 to + 3.4 x 10^38|0.0F
int|32-bit signed integer type|-2,147,483,648 to 2,147,483,647|0
long|64-bit signed integer type|-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807}0L
sbyte|8-bit signed integer type|-128 to 127|0
short|16-bit signed integer type|-32,768 to 32,767|0
uint|32-bit unsigned integer type|0 to 4,294,967,295|0
ulong|64-bit unsigned integer type|0 to 18,446,744,073,709,551,615|0
ushort|16-bit unsigned integer type|0 to 65,535|0

_Unsigned can hold a larger positive value, and no negative value. Unsigned uses the leading bit as a part of the value, while the signed version uses the left-most-bit to identify if the number is positive or negative. signed integers can hold both positive and negative numbers._ 
### Reference types
The reference types do not contain the actual data stored in a variable, but they contain a reference to the variables, that is, they refer to a memory location. Using multiple variables, the reference types can refer to a memory location. If the data in the memory location is changed by one of the variables, the other variable automatically reflects this change in value.

1. Object type
    * The object types can be assigned values of any other types, value types, reference types, predefined or user-defined types. 
    * __boxing__ and __unboxing__
    When a value type is converted to object type, it is called __boxing__ ; when an object type is converted to a value type, it is called __unboxing__.
    ```
    object obj;
    obj = 100;  // this is boxing```
2. Dynamic type
    * can store any type of value in the dynamic data type variable. 
    * Type checking for these types of variables takes place at run-time.
    ```
    dynamic d = 20;
    ```

    * Dynamic types are similar to object types except that _type checking_ for __object type variables takes place at compile time___, whereas that for __the dynamic type variables takes place at run time__.

3. String type
    * derive from object type-- System.String class
    * quoted VS unquoted string
    determine by final representation with quote or not
    ```
    String a = "AAA"; // unquoted string,
    String b = ""bbb"";// quoted string.
    ```
4. User-Defined reference type:
    * class
    * interface
    * delegate

### Pointer types
Pointer type variables store the memory address of another type. 

## Type conversion
Type conversion is converting one type of data to another type. It is also known as Type Casting. In C#, type casting has two forms:

* __Implicit type conversion__ - These conversions are performed by C# in a type-safe manner. For example, are conversions from smaller to larger integral types and conversions from derived classes to base classes.

* __Explicit type conversion__ - These conversions are done explicitly by users using the pre-defined functions. Explicit conversions require a cast operator.
  ```
    double d = 45.1234;
    int i = (int) d;
  ```


## Variables
A variable is __a name given to a storage area that our programs can manipulate__. Each variable in C# has a specific type, which determines the size and layout of the variable's memory the range of values that can be stored within that memory and the set of operations that can be applied to the variable.

The _basic value types_ provided in C# can be __categorized__ as:

Type| Example
---| ---
Integral types|sbyte, byte, short, ushort, int, uint, long, ulong, and char
Floating point types|float and double
Decimal types|decimal
Boolean types|true or false values, as assigned
Nullable types|Nullable data types
others| Enum and class
