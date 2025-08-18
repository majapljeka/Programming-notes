If we run:

```
using System;
using System.Collections.Generic;

public class Program 
{
   private static void Main()
   {
    int Number = 10;
    Console.WriteLine(Number.ToString());

    Customer C1 = new Customer();
    C1.FirstName = "Simon";
    C1.LastName = "Tan";

    Console.WriteLine(C1.ToString());
   }
}


public class Customer
{
 public string FirstName { get; set; }
 public string LastName { get; set;}
}
```

Our output is 10 and Class Customer.

There are two ways how you can override:

First change Customer class:

```
public class Customer
{
 public string FirstName { get; set; }
 public string LastName { get; set;}
}

public override string ToString()
{
  return this.LastName + ", " + this.FirstName;
}
```

Second way is to edit ` Console.WriteLine(C1.ToString());` in main class and leave instead ` Console.WriteLine(Convert.ToString(C1));`
