There are 5 different access modifiers in C#.
**Affects on variables**


1. Private
2. Protected
3. Internal
4. Protected Internal
5. Public


Private members are available only with in the containing type, where as public members are available anywhere without restriction.

Protected members are available, with in the containing type and to the types tha derive from the containing type.

Private => Only with in the containing class
Public => Anywhere
Protected => With in the containing types and the types derived from the containing type


**Private Protected and Internal**

```
using System;

public class Program 
{
   public static void Main()
   {
      Customer C1 = new Customer();
      //Console.WriteLine(C1.ID);  not gonna work because is not deriving from containing class. Lets implement CorporateCustomer class
}

public class Customer
{
  protected int ID;
}

public class CorporateCustomer : Customer
{
  public void ID()
  {
    CorporateCustomer CC = new CorporateCustomer();
    CC.ID = 101;
    base.ID; //this is also possible when is defived containing class.
  }
}
```

**Internal & Protected Internal**

A member with internal access modifier is available anywhere with in the containing assembly. Its a compile time error to access, an internal member from outside the containing assembly.

Protected internal members can be accessed by any code in the assembly in which it is declared, or from within a derived class in another assembly. It is a compination of protected and internal. If you have understood protected and internal, this should be easy to follow.

Private => Only with in the containing class
Public => Anywhere
Protected => With in the containing types and the types derived from the containing type
Internal => Anywhere with in the containing assembly. Internal modifier is **only available in the same project**
Protected Internal => Anywhere with in the containing assembly, and from within a derived class in any another assembly. (base)


**In order to access from (AssemblyTwo) project to another project class member int ID = something (in AssemblyOne project- class AssemblyOneClass), you have to make reference to that project.AND add on the top using AssemblyOne; It is similar like Console which we are often used in console app.**

---

#### Access modifiers for types (affects classes)


You can use all the 5 access modifiers for type members, but type allows only **Internal and Public** access modifiers.
It is a compile error to use private, protected and protected internal access modifiers with types.




