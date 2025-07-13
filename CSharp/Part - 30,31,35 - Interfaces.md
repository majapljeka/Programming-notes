Interface present what class needs to do, but dont how to do.

We create interfaces using interface keyword. Just like classes interfaces also contains properties, methids, delegates or events, but only declaration and no implementations.

**Interfaces can only have declarations and no have definitation or implementations.**

It is compile time error to provide implementations for any interface member.

Interface members are public by default, and they dont allow explicit access modifiers.

**Interfaces cannot contain fields (ex. int ID;).**

If a class or a struct inherits from an interface, it must provide implementation for all interface members. Otherwise, we get a compiler error.

**A class or a struct inherit from more than one interface at the same time, but where as, a class cannot inherit from more than once class at the same time.**

Iterfaces can inherit from other interfaces. A class that inherits this interface must provide implementation for all interface members in the entire interface inheritance chain.

**We cannot create an instance of an interface, but an interface reference variable can point to a derived class object.**

Interface naming convention: Interface names are prefixed with capital I.

```
interface ICustomer
{
    void Print();
}

interface I2
{
    void Method2();
}
public class Customer : ICustomer, I2
{
    public void Print()
    {
        Console.WriteLine("Interface Print Method");
    }

    public void Method2()
        {
            Console.WriteLine("Interface Method2");
        }
}

public class Program
{
    public static void Main()
    {
        Customer C1 = new Customer();
        C1.Print();
    }
}
```

In case of interface Inheritance, we cant have only Print2 implementation and avoid Print1. We must have and Print1() implementation. Let see example here:

```
interface ICustomer1
{
    void Print1();
}

interface ICustomer2 : ICustomer1
{
    void Print2();
}
class Customer : ICustomer2
{

    public void Print2()
    {
        Console.WriteLine("Interface Print Method2");
    }

    // We cant have only Print2 implementation, compailer says that we must have and Print1() implementation!!
    public void Print1()
    {
        Console.WriteLine("Interface Print Method1");
    }
}

public class Program
{
    public static void Main()
    {
        Customer C1 = new Customer();
        C1.Print1();
        C1.Print2();
    }
}
```

reference on Interface is only available like this:

```
 public static void Main()
    {
        ICustomer1 I1 = new Customer();
        I1.Print1();
;
```

### Explicit interfaces implementation

In code we can see two Interfaces with the same InterfaceMethod. Question now is which one is implemented? The interesting this is that we will not have compiler errors.

```
interface I1
{
    void InterfaceMethod();
}

interface I2
{
    void InterfaceMethod();
}

public class Program : I1, I2
{
    void I1.InterfaceMethod()  // We can mark which interface we want to implement
    {
        Console.WriteLine("I1 Interface Method");
    }

    public static void Main()
    {
        Program P = new Program();
        P.InterfaceMethod();
    }
}
```

Question in Main method is which method we are calling? we can solve this in Main method by casting and point to the Interface:

```
 public static void Main()
 {
     Program P = new Program();
     ((I1)P).InterfaceMethod();
 }
```

```
// Access modifiers are not allowed on explicitly implemented interface members.

interface I1
{
    void InterfaceMethod();
}

interface I2
{
    void InterfaceMethod();
}


// We are using Explicit Interface implementation technique to solve this problem
public class Program : I1,I2
{

    // When a class explicitly implements, an interface member, the interface member can no logner be accessed thru class reference variable, but only thru the interface reference varible.

    void I1.InterfaceMethod()
    {
        Console.WriteLine("I1 Interface Method");
    }

    void I2.InterfaceMethod()
    {
        Console.WriteLine("I2 Interface Method");

    }
    public static void Main()
    {
        Program P = new Program();
        ((I1)P).InterfaceMethod();
        ((I2)P).InterfaceMethod();

     /* We can access on this way as well apart from cast
         I1 i1 = new Program();
         I2 i2 = new Program();
        
         i1.InterfaceMethod();
         i2.InterfaceMethod();
     */
    }
```

Also we can have situation where one Interface can implemented by default and another one explicitely:

```
interface I1
{
    void InterfaceMethod();
}

interface I2
{
    void InterfaceMethod();
}

public class Program : I1,I2
{
    public void InterfaceMethod()  // I1 is default Interface
    {
        Console.WriteLine("I1 Interface Method");
    }

    void I2.InterfaceMethod()  // T2 is explicit Interface
    {
        Console.WriteLine("I2 Interface Method");

    }
    public static void Main()
    {
        Program P = new Program();
        P.InterfaceMethod();
        ((I2)P).InterfaceMethod();     
    }
```

### Multiple class inheritance using interfaces

```
interface IA
{
    void AMethod();
}
class A : IA
{
    public void AMethod()
    {
        Console.WriteLine("A");
    }
}
interface IB
{
    void BMethod();
}
class B : IB
{
    public void BMethod()
    {
        Console.WriteLine("B");
    }
}

class AB : IA, IB
{ 
    A a = new A();
    B b = new B();
    public void AMethod()
    {
        a.AMethod();
    }
    public void BMethod()
    { 
        b.BMethod();
    }
}
public class Program
{
    public static void Main()
    {
        AB ab = new AB();   
        ab.AMethod();
        ab.BMethod();
    }
}
```

