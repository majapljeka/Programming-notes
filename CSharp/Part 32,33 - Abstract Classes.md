The abstract keyword is used to create abstract classes.

**An abstract class is incomplete and hence cannot be instantiated.**

An abstract class can only be used as base class.

An abstract class cannot be sealed.

An abstract class may contain abstract members (methods, properties, indexers and events) but not mandatory.

```
public abstract class Customer
{
    public void Print()
    {
        Console.WriteLine("Print Method");
    }
}

public class Program : Customer
{
    //public override void Print()
    //{
    //    Console.WriteLine("Print Method");
    //}
    public static void Main()
    {       
        //Program P = new Program(); // Customer P = new Program(); is also possible
        //P.Print();        
    }
}
```
**A non-abstract class derived from an abstract class must provide implementations for all inherited abstract members.**

If a class inherits an abstract class, there are 2 options available for that class:

Option 1: Provide implementation for all the abstract members inherited from the base abstract class.

Options 2: If the class does not wish to provide implementation for all the abstract members inherited from the abstract class, then the class has to be marked as abstract.

```
public abstract class Customer
{
    public abstract void Print();
}

public class Program : Customer
{
    public override void Print()
    {
        Console.WriteLine("Print Method");
    }
    public static void Main()
    {      
        Program P = new Program(); // Customer P = new Program(); is also possible
        P.Print();   
    }
}
```

### Difference between abstract classes and interfaces

Abstract classess can have implementations for some of its members (Methods), but the interface cannot have implementation for any of its members.

```
public abstract class Customer
{
    public void Print()
    {
        Console.WriteLine("Print Method");
    }
}

public interface ICustomer
{
    public void Print()
    {
        Console.WriteLine("Something");
    }
}

public class Program
{
    public static void Main()
    {
        
    }
}

We will get here compiler error!!!
```

**Abstract class member are private by default.**

**Interfaces cannot have fields where as an abstract class can have fields (ex. int ID).**

An interface can inherit from another interface only and cannot inherit from an abstract classs, where as an abstract class can inherit from another abstract class or another interface.

**A class can inherit from multiple interfaces at the same time, where as a class cannot inherit from multiple classes at the same time.**

Abstract class members can haave access modifiers where as interface members cannot have acceess modifiers.
