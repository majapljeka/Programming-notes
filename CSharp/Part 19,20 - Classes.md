We will learn what is:

1. What is the class?
2. Purpose of a class constructor.
3. Overloading class contructor. (when we have two constructors and they are initiated in main method.)
4. Understanding **this** constructor.
5. Destructors



1. Class consists of data and behavior. Class data is represented by its fields and behavior is represented by its methods.
2. Purpose of a class constructor is to initialize class fields. A clas contructor is automatically called when an instance of a class is created. Constructors do not have return values and always have the same name as the class. \

Constructors are not mandatory. If we do not privide constructors, a default parameter less constructor is automatically provided.
Constructors can be overloaded by the number and type of parameters.


5. Desctructors - has the same name as class and tilda sign ~, They dont take any params and they do not return any value. Destructors are places where you could put code to relase any resources your class was holding during its lifetime. 
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
