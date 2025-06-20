- Overriding virtual method
- Polymorphism

Polymorphism is one of the primary pillars of OOO.

Polymorphism allows you to invoke derived class methods through a base class reference during runtime.

In the base class the method is declared virtual, and in the derived class we override the same method.

The virtual keyword indicates, the method can be overridden in any derived class.

Simple example:

```
public class Employee
{
    public string FirstName = "FN";
    public string LastName = "LN";

    public void PrintFullName()
    {  
    Console.WriteLine(FirstName + " " + LastName);
    }    
}

public class PartTimeEmployee : Employee
{   
}

public class FullTimeEmployee : Employee
{
}

public class TemporaryTimeEmployee : Employee
{
}

public class Program
{
    public static void Main()
    {
        Employee[] employees = new Employee[4];

        employees[0] = new Employee();
        employees[1] = new PartTimeEmployee();
        employees[2] = new FullTimeEmployee();
        employees[3] = new TemporaryTimeEmployee();

        foreach (Employee e in employees)
        {
            e.PrintFullName();
        }
    }
}
```

Now if we want to add for every FN & LN additional title we can do that simply (added override and virtual keyword due to hidding methods):

```
public class Employee
{
    public string FirstName = "FN";
    public string LastName = "LN";

    public virtual void PrintFullName()
    { 
    Console.WriteLine(FirstName + " " + LastName);
    }    
}

public class PartTimeEmployee : Employee
{
    public override void PrintFullName()
    {
        Console.WriteLine(FirstName + " " + LastName + "- Part time");
    }
}

public class FullTimeEmployee : Employee
{
    public override void PrintFullName()
    {
        Console.WriteLine(FirstName + " " + LastName + "- Full time");
    }
}

public class TemporaryTimeEmployee : Employee
{
    public override void PrintFullName()
    {
        Console.WriteLine(FirstName + " " + LastName +  "- temporary");
    }
}

public class Program
{
    public static void Main()
    {
        Employee[] employees = new Employee[4];

        employees[0] = new Employee();
        employees[1] = new PartTimeEmployee();
        employees[2] = new FullTimeEmployee();
        employees[3] = new TemporaryTimeEmployee();

        foreach (Employee e in employees)
        {
            e.PrintFullName();
        }
    }
}
```

