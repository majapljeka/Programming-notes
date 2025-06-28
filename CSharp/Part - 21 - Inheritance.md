Pillars of OOO:
1. Inheritance
2. Encapsulation
3. Abstraction
4. Polymorphism

Inheritance

1. Inheritance is one of the primary pillars of OOO.
2. It allows code reuse.
3. Code reuse can reduce time and errors.

> **_NOTE:_** You will specify all the common fields, properties, methods in the base class which allows reusability. In the derived class you will only have fields, properties and methods, that are specific to them.

```
public class Employee
{

    public string FirstName;
    public string LastName;
    public string Email;

    public void PrintFullName()
    {
        Console.WriteLine(FirstName+ " " + LastName);
    }
}

public class FullTimeEmployee : Employee
{
    public float YearlySalary;
}

public class PartTimeEmployee : Employee
    //Specialization of Employee class 
{
    public float HourlyRate;
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
           
            FullTimeEmployee FTE = new FullTimeEmployee();
            FTE.FirstName = "Sasa";
            FTE.LastName = "Jezd";
            FTE.YearlySalary = 5000;
            FTE.PrintFullName();

            PartTimeEmployee PTE = new PartTimeEmployee();
            PTE.FirstName = "Part";
            PTE.LastName = "PartLastname";
            PTE.PrintFullName();
        }
    }
}
```

1. In this example DerivedClass inherits from ParentClass.
2. C# supports only single class inheritance, it does not support multiple class inheritance. Part 34. This ambiguity is called as Diamond problem.
3. C# supports multiple interface inheritance.
4. Child class is a specialization of base class.
5. Base classess are automatically insantiated before derived classes.
6. Parent Class constructor executes before Child Class constructor.

#### case 2. example
```
public class ParentClass
{	
	// Parent class Implementation
}

public class DerivedClass : ParentClass
{
	
	// Child class Implementation
}
It is possible
class A : DerivedClass
{}
This is 2. is possible with all available variables from parent class:
```


#### case 6 example
```
public class ParentClass
{ 
    public ParentClass()
    {

        Console.WriteLine("ParentClass Constructor called");
    }
}

public class ChildClass : ParentClass
{
    public ChildClass()
    {
        Console.WriteLine("ChildClass Constructor called");
    }
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ChildClass CC = new ChildClass();
        }
    }
}
```

and here we add second contructor which can be called with String parameter:

```
public class ParentClass
{ 

    public ParentClass()
    {

        Console.WriteLine("ParentClass Constructor called");
    }

    //Second contructor with parameter
    public ParentClass(string message)
    { 
        Console.Write(message);
    }
}

public class ChildClass : ParentClass
{

    public ChildClass() : base("Message Derive class controlling Parent class")
    {
        Console.WriteLine("ChildClass Constructor called");
    }
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ChildClass CC = new ChildClass();

        }
    }
}
```
