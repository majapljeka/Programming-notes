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
