Use the new keyword to hide a base class member. You will get a compiler warning, if you miss the new keyword.

Different ways to invoke a hidden case class member from derived class

1. Use base keyword
2. Cast child type to parent type and invoke hidden member
3. ParentClass PC = new childClass()
	PC.HiddenMethod()

```
public class Employee
{
    public string FirstName;
    public string LastName;

    public void PrintFullName()
    {
        Console.WriteLine(FirstName + " " + LastName);
    }
}

public class PartTimeEmployee : Employee
{
    public void PrintFullName()    // here we need to add new before void due to hiding methods into the same name method in Class Employee
    {
        // base.PrintFullName(); 1. First way if we want to call Employee method PrintFullName() without hiding
        Console.WriteLine(FirstName + " " + LastName + " - Contractor");
    }
}

public class FullTimeEmployee : Employee
{
}

public class Program
{
    public static void Main()
    {
        FullTimeEmployee FTE = new FullTimeEmployee();
        FTE.FirstName = "Fulltime Sasa";
        FTE.LastName = "Employee";
        FTE.PrintFullName();

        PartTimeEmployee PTE = new PartTimeEmployee();
        // Employee PTE = new PartTimeEmployee();  3. Third way to call method from Employee class without hiding
        PTE.FirstName = "Parttime Sasa";
        PTE.LastName = "Employee";
        PTE.PrintFullName();
        // ((Employee)PTE).PrintFullName()   2.Second way to call method from Employee class without hiding
    }
}
```
