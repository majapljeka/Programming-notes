A delegate is a type safe function pointer. That is, it holds a reference (Pointer) to a function.

The signature of the delegate must watch the signature of the function, the delegate point to, otherwise you get a compiler error. This is the reason delegates are called as type safe function pointers.

A delegate is similar to a class. You can create an instance of it, and when you do so, you pass in the function name as a parameter to the delegate constructor, and it is to this function the delegate will point to.

**Tip to remember delegate syntax**: Delegates syntax look very much similar to a method with a delegate keyword.

```
using System;

public delegate void HelloDelegateFunction(string Message);

public class Program
{
    public static void Main()
    {
      HelloDelegateFunction hello = new HelloDelegateFunction(Hello);
      hello("Hello from Delegate!!");
      //A delegate is a type safe function pointer
    }

    public static void Hello(string strMessage)
    {
        Console.Write(strMessage);
    }
}
```

### Delegates in use I part

```
using System;
using System.Collections.Generic;



public class Program
{
    public static void Main()
    {
      List<Employee> empList = new List<Employee>();

        empList.Add(new Employee(){ID = 101 , Name = "Mike", Experience = 5, Salary = 4000});
        empList.Add(new Employee(){ID = 101 , Name = "Pera", Experience = 4, Salary = 3000});
        empList.Add(new Employee(){ID = 101 , Name = "Sasa", Experience = 5, Salary = 2000});
        empList.Add(new Employee(){ID = 101 , Name = "Milan", Experience = 3, Salary = 2000});

        Employee.PromoteEmployee(empList);
    }
}

class Employee
{
    public int ID {get; set;}
    public string Name {get; set;}
    public int Experience {get; set;}
    public int Salary {get; set;}

    public static void PromoteEmployee(List<Employee> employeeList)
    {
        foreach (Employee employee in employeeList)
        {
            if(employee.Experience >= 5){
                Console.WriteLine(employee.Name + " promoted!");
            }
        }
    }
}
```
**Pass function as a parameter**
Now if someone wants to reuse PromoteEmployee method and extend, pass method as parameter to antother method, we can use with delegates.
The problem for this method is hardcode logic for promoting employees, we want to be reusable.

### Delegates in use II part

```
using System;
using System.Collections.Generic;



public class Program
{
    public static void Main()
    {
        List<Employee> empList = new List<Employee>();

        empList.Add(new Employee() { ID = 101, Name = "Mike", Experience = 5, Salary = 4000 });
        empList.Add(new Employee() { ID = 101, Name = "Pera", Experience = 4, Salary = 3000 });
        empList.Add(new Employee() { ID = 101, Name = "Sasa", Experience = 5, Salary = 2000 });
        empList.Add(new Employee() { ID = 101, Name = "Milan", Experience = 3, Salary = 2000 });

        //Constructor of delegate
        IsPromotable IsPromotable = new IsPromotable(ProgramHelpers.Promote);

        Employee.PromoteEmployee(empList, IsPromotable); //Passing delegate as parameter
    }
}

delegate bool IsPromotable(Employee empl);

class Employee
{
    public int ID { get; set; }
    public string Name { get; set; }
    public int Experience { get; set; }
    public int Salary { get; set; }

    public static void PromoteEmployee(List<Employee> employeeList, IsPromotable isEligibleToPromote)
    {
        foreach (Employee employee in employeeList)
        {
            if (isEligibleToPromote(employee))
            {
                Console.WriteLine(employee.Name + " promoted!");
            }
        }
    }
}
```

+ ProgramHelper.cs class

```
internal static class ProgramHelpers
{
    //Delegate condition
    public static bool Promote(Employee emp)
    {
        if (emp.Experience >= 5)
        {
            return true;
        }
        else
        {
            return false;
        }
    }
}
```

Instead we can do also with Lambda expression in one line and get rid of delegates (condition).

```
using System;
using System.Collections.Generic;


public class Program
{
    public static void Main()
    {
        List<Employee> empList = new List<Employee>();

        empList.Add(new Employee() { ID = 101, Name = "Mike", Experience = 5, Salary = 4000 });
        empList.Add(new Employee() { ID = 101, Name = "Pera", Experience = 4, Salary = 3000 });
        empList.Add(new Employee() { ID = 101, Name = "Sasa", Experience = 5, Salary = 2000 });
        empList.Add(new Employee() { ID = 101, Name = "Milan", Experience = 3, Salary = 2000 });

        //Constructor of delegate

        Employee.PromoteEmployee(empList, emp => emp.Experience >= 5);
    }
}

delegate bool IsPromotable(Employee empl);

class Employee
{
    public int ID { get; set; }
    public string Name { get; set; }
    public int Experience { get; set; }
    public int Salary { get; set; }

    public static void PromoteEmployee(List<Employee> employeeList, IsPromotable isEligibleToPromote)
    {
        foreach (Employee employee in employeeList)
        {
            if (isEligibleToPromote(employee))
            {
                Console.WriteLine(employee.Name + " promoted!");
            }
        }
    }
}
```

### Multicast delegates

A Multicast delegate is a delegate that has references to more than one function. When you invoke a multicast delegate, all the functions the delegate is pointing to, are invoked.

```

```

There are 2 approaches to create multicast delegate. Depending on the approach you use
+ or += to register a method with the delegate
- or -= to un-register a method with the delegate

Note: A Multicast delegate, invokes the methods in the invocation list, in the same order in which they are added. 

If the delegate has a return type other than void and if the delegate is a multicast delegate, only the valie of the last invoked method will be returned. Along the same lines, if the delegate has an out parameter, the value of the output parameter, will be the value assigned by the last method.


Common interview question - Where do you use multicast delegates?
Multicast delegates makes implementation of observer design patter very simple. Observer patter is also called as publish/subscribe pattern.





