Attributes allow you to add declarative information to your program. This information then can be queried at runtime using reflection.

There are several pre-Defined Attributes provided by .NET. It is possible to create your own Custom Attributes.

A few pre-defined attributes within the .NET framework:
1. Obsolete => Marks types and type members outdated
2. WebMethod => To expose method as an XML Web Service method
3. Serializable => Indicates that a class can be serizalized

It is possible to customize the attribute using parameters.

An Attribute is an class that inherits from Syste.Attributes base class.

```
using System;
using System.Collections.Generic;

public class Program 
{
   private static void Main()
   {
    Calculator.Add(10,20);
   }
}


public class Calculator
{
  [Obsolete]
  public static int Add(int FirstNumber, int SecondNumber)
  {
    return FirstNumber + SecondNumber;
  }

  public static int Add(List<int> Numbers)
  {
    int Sum = 0;

    foreach (int Number in Numbers)
    {
      Sum = Sum + Number;
    }
    return Sum;
  }
}
```

This is fine, but if we want to explicitely say that Obsolete attribut should not use (int, int method) we can add in Customized message:

`[Obsolete("Use Add(List<int> Numbers Method")]`

After build, if we hover Add(int,int) method we should see results.

At the end we can add: `Calculator.Add(new List<int>(){10,20,40});` if we want to use Add List method.
