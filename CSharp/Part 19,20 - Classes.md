We will learn what is:

1. What is the class?
2. Purpose of a class constructor.
3. Overloading class contructor. (when we have two constructors and they are initiated in main method.)
4. Understanding **this** constructor.
5. Destructors



- Class consists of data and behavior. Class data is represented by its fields and behavior is represented by its methods.
- Purpose of a class constructor is to initialize class fields. A clas contructor is automatically called when an instance of a class is created. Constructors do not have return values and always have the same name as the class. 

Constructors are not mandatory. If we do not privide constructors, a default parameter less constructor is automatically provided.
Constructors can be overloaded by the number and type of parameters.

- Desctructors - has the same name as class and tilda sign ~, They dont take any params and they do not return any value. Destructors are places where you could put code to relase any resources your class was holding during its lifetime. 
They are normally called when the C# garbage collector decides to clean your object from memory.

```
using System;

class Customer
{

    String _firstName;
    String _lastName;

    // if we want to make default constructor without parameters in main method


    /*
    public Customer()
        : this("No FN provided", "No Last name provided")
    {
    } 
     */

    // Constructor will call automaticaly when we call the class. They are used to initialize class fields.
    public Customer(String FirstName, string LastName)
    { 
    
        this._firstName = FirstName; //this make reference object of this class
        this._lastName = LastName;
    }

    public void PrintFullName()
    {
        Console.WriteLine("Full name = {0}", this._firstName + " " + this._lastName);   
    }

    /* Destructors called automatically by garbage collector */
    ~Customer()
    { 
    }
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Customer C1 = new Customer("Sasa","Technologies"); /* If we forget to make constructors, C# compiler
            will do automatically but it will be empty */
            C1.PrintFullName();
        }
    }
}
```

###  Static and instance class members

When a class member includes a static modifies, the member is called as static member.
When no static modifier is present the is called as **non static member or instance member**.

**Static members** are invoked using class name, where as **instance members** are invoked using instances (objects) of the class.

An **instance memeber** belongs to specific instance (objects) of a class. If i create 3 objects of a class, i will have 3 sets of instance members in the memory, where as there will ever be only one copy of a **static member**, no matter how many instances of a class are created.

> **_NOTE:_** Class members = fields, methods, properties, events, indexers, constructors

```
class Circle
{
    static float _PI;
    int _Radius;

    static Circle()
    {
        Console.WriteLine("Static Constructor Called");
        Circle._PI = 3.141F;    
    }

    public Circle(int Radius)
    {
        Console.WriteLine("Instance Constructor Called");
        this._Radius = Radius;
    }

    public float CalculateArea()
    { 
    return Circle._PI * this._Radius * this._Radius;
        //Additional1: if we on the beginning _PI will be static, we will have return name of the Class -> Circle._PI * this._Radius * this._Radius;
    }
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            //both are instance fields, variables define on the beginning are shared
            Circle C1 = new Circle(5);
            float Area = C1.CalculateArea();
            Console.WriteLine("Area = {0}" , Area);

            Circle C2 = new Circle(6);
            float Area1 = C2.CalculateArea();
            Console.WriteLine("Area1 = {0}", Area1);
        }
    }
}
```

##### Static contructors

**Static constructor are used to initialize static fields in a class.**

You declare a static contructor by using the keyword static in front of the contructor name.

**Static contructors is called only once, no matter how many instances you create.**

**Static contructors are called before instance contructors.**

```
class Circle
{
    public static float _PI;
    int _Radius;

    static Circle()
    {
        Console.WriteLine("Static Constructor Called");
        Circle._PI = 3.141F;
    }

    public Circle(int Radius)
    {
        Console.WriteLine("Instance Constructor Called");
        this._Radius = Radius;
    }

    public float CalculateArea()
    { 
    return Circle._PI * this._Radius * this._Radius;
        //Additional1: if we on the beginning _PI will be static, we will have return name of the Class -> Circle._PI * this._Radius * this._Radius;
    }
}

namespace IntroductionToCSharp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Circle._PI);
        }
    }
}
```
