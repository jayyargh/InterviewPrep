# C# Fundamentals Part 2: Primitives

As we continue our first chapter, C# Fundamentals, we will touch upon primitive data types. If you're curious about the answers for the previous section's quiz questions, the answers in this order are: `B, A, C`. I hope you did well! Now, onto the meat and potatoes!

## Variables and Constants

- Variable: a name given to a storage location in memory
- Constant: an immutable value

### Declaring Variables and Constants

When delaring, we start with the type, the name, assignment operator, the value and finally a semicolon. The identifiers (variable name) must not start with a number nor any whitespace. You should not use reserved keywords but you may by adding an '`@`' (ie: `@int`). Further etiquette stipulates using meaningful names, if you're declaring a `fullName` don't just call it `fn` or `x`.

> C# developers use camelCase for local variables and PascalCase for constants.

```C#
int number; // an integer between -2 billion and 2 billion
int Number = 1; // you can declare with or without a variable
const float Pi = 3.14f; // declare a constant with const, data type, name, and initialized value
```

### Primitive Types

| C# Type | .NET Type | Bytes |            Range            |
| :-----: | :-------: | :---: | :-------------------------: |
|  byte   |   Byte    |   1   |          0 to 255           |
|  short  |   Int16   |   2   |      -32,768 to 32,767      |
|   int   |   Int32   |   4   |        -2.1B to 2.1B        |
|  long   |   Int64   |   8   |             ...             |
|  float  |  Single   |   4   | -3.4 x 10^38 to 3.4 x 10^38 |
| double  |  Double   |   8   |             ...             |
| decimal |  Decimal  |  16   | -7.9 x 10^28 to 7.9 x 10^28 |
|  char   |   Char    |   2   |     Unicode Characters      |
|  bool   |  Boolean  |   1   |         True/False          |

Notice how C# keywords are always lowercase. When you run your code, the compiler will automatically convert these types to their .NET equivalents. The bytes column is organized by smallest to largest based on their types. The top four are integral types, the middle three are real numbers, character for char, and boolean for bool. The more bytes, the larger the numbers they can store.

### Real Numbers

By default, declared numbers default to a `double` when using real numbers. If you want to use a float instead, you can tell the compiler this by writing your declaration like this:

```C#
float number = 1.2f; // the f is added to indicate that it is indeed a float
decimal number = 1.2m; // the m is used for decimal
```

### Overflowing

```C#
byte number = 255;

number = number + 1; // 0
```

C# by default does not check for overflow. To check for it, you'd need to use the `checked` keyword. It would look something like this:

```C#
checked {
  byte number = 255;

  number = number + 1;
}
```

In this situation you would be better off using a `short` data-type if you're worried about overflow instead.

### Scope

```C#
{
  byte a = 1;
  {
    byte b = 2;
    {
      byte c = 3;
    }
  }
}
```

In this code block, `a` can be accessed anywhere, however outside of the block, it doesn't exist. The same with `b`, it can be accessed within its block and its children, but outside it would simply be undefined.

### Type Conversion

In this section we will go over implicit type conversion, explicit type conversion (casting) and conversion between non-compatible types. Let's begin with an example of implicit type conversion!

```C#
byte b = 1; // 00000001
int i = b; // 000000000 00000000 00000000 000000001
```

As you know, a byte only takes 1 byte of memory, therefore it can easily be set inside of an int. This means there is no data loss and the compiler converts them "implicitly". Let's see what happens when the reverse occurs!

```C#
int i = 1;
byte b = i; // won't compile
```

This is where **explicit type conversion** comes in handy! Let's see what that would look like:

```C#
int i = 1;
byte b = (byte)i;
```

_or_...

```C#
float f = 1.0f;
int i = (int)f;
```

Sometimes though, we encounter what are called **non-compatible types**. A specific situation of that might look like this:

```C#
string s = "1";
int i = (int)s; // won't compile
```

In this situation, you would either use the `Convert` class or a `Parse()` method. The above niche situation would be solved this way:

```C#
string s = "1";
int i = Convert.ToInt32(s); // part of .NET framework in System namespace, this class methods all seem to start with To
int j = int.Parse(s); // all of our primitive types have a parse method
```

### Operators

- Let's take a look at 5 different types of operators in C#.

**Arithmetic operators**

| Operator | Description                                                 | Example      |
| -------- | ----------------------------------------------------------- | ------------ |
| +        | Adds two operands                                           | A + B = 30   |
| -        | Subtracts second operand from the first                     | A - B = -10  |
| \*       | Multiplies both operands                                    | A \* B = 200 |
| /        | Divides numerator by de-numerator                           | B / A = 2    |
| %        | Modulus Operator and remainder of after an integer division | B % A = 0    |
| ++       | Increment operator increases integer value by one           | A++ = 11     |
| --       | Decrement operator decreases integer value by one           | A-- = 9      |

**Relational/comparison operators**

| Operator | Description                                                                                                                     | Example               |
| -------- | ------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| ==       | Checks if the values of two operands are equal or not, if yes then condition becomes true.                                      | (A == B) is not true. |
| !=       | Checks if the values of two operands are equal or not, if values are not equal then condition becomes true.                     | (A != B) is true.     |
| >        | Checks if the value of left operand is greater than the value of right operand, if yes then condition becomes true.             | (A > B) is not true.  |
| <        | Checks if the value of left operand is less than the value of right operand, if yes then condition becomes true.                | (A < B) is true.      |
| >=       | Checks if the value of left operand is greater than or equal to the value of right operand, if yes then condition becomes true. | (A >= B) is not true. |
| <=       | Checks if the value of left operand is less than or equal to the value of right operand, if yes then condition becomes true.    | (A <= B) is true.     |

**Assignment Operators**

| Operator | Description                                                                                                               | Example                                 |
| -------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| =        | Simple assignment operator, Assigns values from right side operands to left side operand                                  | C = A + B assigns value of A + B into C |
| +=       | Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand              | C += A is equivalent to C = C + A       |
| -=       | Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand  | C -= A is equivalent to C = C - A       |
| \*=      | Multiply AND assignment operator, It multiplies right operand with the left operand and assign the result to left operand | C _= A is equivalent to C = C _ A       |
| /=       | Divide AND assignment operator, It divides left operand with the right operand and assign the result to left operand      | C /= A is equivalent to C = C / A       |
| %=       | Modulus AND assignment operator, It takes modulus using two operands and assign the result to left operand                | C %= A is equivalent to C = C % A       |
| <<=      | Left shift AND assignment operator                                                                                        | C <<= 2 is same as C = C << 2           |
| >>=      | Right shift AND assignment operator                                                                                       | C >>= 2 is same as C = C >> 2           |
| &=       | Bitwise AND assignment operator                                                                                           | C &= 2 is same as C = C & 2             |
| ^=       | bitwise exclusive OR and assignment operator                                                                              | C ^= 2 is same as C = C ^ 2             |
| `|=`     | bitwise inclusive OR and assignment operator                                                                              | C                                       | = 2 is same as C = C | 2 |

**Logical Operators**

| Operator | Description                                                                                                                                      | Example            |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------ |
| &&       | Called Logical AND operator. If both the operands are non zero then condition becomes true.                                                      | (A && B) is false. |
| `||`     | Called Logical OR Operator. If any of the two operands is non zero then condition becomes true.                                                  | (A                 |  | B) is true. |
| !        | Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true then Logical NOT operator will make false. | !(A && B) is true. |

**Bitwise Operators**

| Operator | Description                                                                                                                                                                                                                                                     |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| &        | The bitwise-AND operator compares each bit of its first operand to the corresponding bit of its second operand. If both bits are 1, the corresponding result bit is set to 1. Otherwise, the corresponding result bit is set to 0.                              |
| ^        | The bitwise-exclusive-OR operator compares each bit of its first operand to the corresponding bit of its second operand. If one bit is 0 and the other bit is 1, the corresponding result bit is set to 1. Otherwise, the corresponding result bit is set to 0. |
|          |                                                                                                                                                                                                                                                                 | The bitwise-inclusive-OR operator compares each bit of its first operand to the corresponding bit of its second operand. If either bit is 1, the corresponding result bit is set to 1. Otherwise, the corresponding result bit is set to 0. |

### Comments

Comments are text that we use to document our code to improve readability and maintainability. In C# specifically, we have two primary ways to write our comments: single line and multi-line.

```C#
// here is a single line comment
int val = 1;
```

```C#
/*
  here is a multi-line
  comment
*/
int val = 1;
```

Only use comments when required, ie: to explain whys, hows, contraints, etc., not what the code is doing. Your code should be self evident and a comment in that situation would be redundant.
