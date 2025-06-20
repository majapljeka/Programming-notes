Function overloading and Method overloading terms are used interchangeable.

Method overloading allows a class to have multiple methods with the same name, but with a different signature. So in C# functions can be overloaded based on the number, type (int, float, etc) and kind (Value, Ref or Out) of parameters.

The signature of a method consist of the name of the method and the type, kind (value, ref or output) and the number or its formal parameters. The signature of a method does not include the return type and the params notifier. So, it is not possible to overload function, just based on the return type or params modifier

> **_NOTE:_** If you want to know about different kinds of methods parameters, please check Part 17 - Method Parameters.


**static mean without object**

```
using System;


public class Program
{
    public static void Add(int FN, int SN)
{
    Console. WriteLine("Sum of {0}", FN + SN);
}
public static void Add(float FN, float SN)
{
     Console. WriteLine("Sum of {0}", FN + SN);
}

public static void Add(int FN, float SN)
{
     Console. WriteLine("Sum of {0}", FN + SN);
}

public static void Add(int FN, float SN, out int Sum)
{
     Console. WriteLine("Sum of {0}", FN + SN);
     Sum = FN + SN;
}
    
    public static void Main()
    {
      Add(something, something);
    }
}
```
