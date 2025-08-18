Difference between early and late binding:
1. Early binding can flag errors at compile time. With late binding there is a risk of run time exceptions.
2. Early binding is much better for performance and should always be preferred over late binding. Use late binding only when working with onjects that are not available at compile time.

Example of early binding:

```
using System;
using System.Collections.Generic;

public class Program 
{
   private static void Main()
   {
    Customer C1 = new Customer();
    string FullName = C1.GetFullName("Pragim" , "Tech");
    Console.WriteLine("Full name = {0}", FullName);
   }
}


public class Customer
{
  public string GetFullName(string FirstName, string LastName)
  {
    return FirstName + " " + LastName;
  }
}
```

Example of late binding:

```
using System;
using System.Reflection;
namespace Pragim
{
    public class MainClass
    {
        private static void Main()
        {
            // Load the current executing assembly as the Customer class is present in it.
            Assembly executingAssembly = Assembly.GetExecutingAssembly();
            // Load the Customer class for which we want to create an instance dynamically
            Type customerType = executingAssembly.GetType("Pragim.Customer");
            // Create the instance of the customer type using Activator class 
            object customerInstance = Activator.CreateInstance(customerType);
            // Get the method information using the customerType and GetMethod()
            MethodInfo getFullName = customerType.GetMethod("GetFullNames");
            // Create the parameter array and populate first and last names
            string[] methodParameters = new string[2];
            methodParameters[0] = "Pragim"; //FirstName
            methodParameters[1] = "Tech";     //LastName
            // Invoke the method passing in customerInstance and parameters array
            string fullName = (string)getFullName.Invoke(customerInstance, methodParameters);
            Console.WriteLine("Full Name = {0}", fullName);
        }
    }
    public class Customer
    {
        public string GetFullName(string FirstName, string LastName)
        {
            return FirstName + " " + LastName;
        }
    }
}
```
