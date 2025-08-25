List is one of the generic collection classes present in System.Collections.Generic namespace. There are several
generic collection classes in System.Collections.Generic namespace listed below.

1. Dictionary 
2. List
3. Stack
4. Queue etc

**A List class can be used to create a collection of any type.**

For example. we can create a list of Integers, Strins, and even complex types.

**The objects stored in the list can be accessed by index.**

Unlike arrays, list can grow in size automatically.

This class also provides methods to search, sort and manipulate lists.

```
using System;
using System.Collections.Generic;
using System.Runtime.InteropServices;

public class Program 
{
   private static void Main()
   {
      Customer customer1 = new Customer()
      {
        ID = 101,
        Name = "Mark",
        Salary = 5000
      };

       Customer customer2 = new Customer()
      {
        ID = 104,
        Name = "Sam",
        Salary = 3000
      };

       Customer customer3 = new Customer()
      {
        ID = 107,
        Name = "Pat",
        Salary = 7000
      };

 
   }
}

public class Customer
{
  public int ID { get; set; }
  public string Name { get; set; }
  public int Salary{ get; set; }
}
```
