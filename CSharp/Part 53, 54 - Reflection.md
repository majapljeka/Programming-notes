Reflection is the ability of inspecting an assemblies' metadata at runtime. It is used to find all types in an assembly and/or dynamically invoke methods in an assembly.

Uses of reflection:

1. When you drag and drop a button on a win forms or an asp.net app. The properties window uses reflection to show all the properties of the Button class. So, reflection is exensively used by IDE or a UI designers.
2. Late binding (Late binding in C#, also known as runtime binding or dynamic binding, refers to the process where the resolution of method calls, property access, or event handling is deferred until runtime, rather than being determined at compile time.) can be achieved by using reflection. You can use reflection to dynamically create an instance of a type, about which we dont have any information at compile time. So, reflection enables you to use code that is not available at compile time.
3. Consider an example where we have two alternative implementations of an interface. You want to allow the user to pick one or the other using a config file. With reflection , you can simply read the name of the class whose implementation you want to use from the config file, and instantiate an instance of the class. This is another exampple for late binding using reflection.


```
using System;
using System.Reflection;
namespace Pragim
{
    public class MainClass
    {
        private static void Main()
        {
            // Get the Type Using GetType() static method
            Type T = Type.GetType("Pragim.Customer");
            // Print the Type details
            Console.WriteLine("Full Name = {0}",T.FullName);
            Console.WriteLine("Just the Class Name = {0}",T.Name);
            Console.WriteLine("Just the Namespace = {0}", T.Namespace);
            Console.WriteLine();
            // Print the list of Methods
            Console.WriteLine("Methods in Customer Class");
            MethodInfo[] methods = T.GetMethods();
            foreach (MethodInfo method in methods)
            {
                // Print the Return type and the name of the method
                Console.WriteLine(method.ReturnType.Name + " " + method.Name);
            }
            Console.WriteLine();
            //  Print the Properties
            Console.WriteLine("Properties in Customer Class");
            PropertyInfo[] properties = T.GetProperties();
            foreach (PropertyInfo property in properties)
            {
                // Print the property type and the name of the property
                Console.WriteLine(property.PropertyType.Name + " " + property.Name);
            }
            Console.WriteLine();
            //  Print the Constructors
            Console.WriteLine("Constructors in Customer Class");
            ConstructorInfo[] constructors = T.GetConstructors();
            foreach (ConstructorInfo constructor in constructors)
            {
                Console.WriteLine(constructor.ToString());
            }
        }
    }
    public class Customer
    {
        public int Id { get; set; }
        public string Name { get; set; }

        public Customer(int ID, string Name)
        {
            this.Id = ID;
            this.Name = Name;
        }
        public Customer()
        {
            this.Id = -1;
            this.Name = string.Empty;
        }
        public void PrintID()
        {
            Console.WriteLine("ID = {0}", this.Id);
        }
        public void PrintName()
        {
            Console.WriteLine("Name = {0}", this.Name);
        }
    }
}
```

In this example to get the type of customer class we have used GetType() static method defined on the Type class. We pass in the fully qualified name of the type including the namespace as a parameter to the GetType() method.
`Type T = Type.GetType("Pragim.Customer");`


To get the type information we have the following 2 ways as well.
Use typeof keyowrd
`Type T = typeof(Customer);`


Use GetType() on the instance of the customer class. 
```
Customer C1 = new Customer();
Type T = C1.GetType();
```

To get the methods information, we use Type.GetMethods(), which returns MethodInfo[] array and along the same lines we use Type.GetProperties() to get properties information, but Type.GetProperties() returns PropertyInfo[] array.
