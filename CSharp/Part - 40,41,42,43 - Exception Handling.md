An exception is an unforeseen error that occurs when a program is running.

Examples:
Trying to read from a file that does not exist, throws FileNotFoundException.
Trying to read from a database table that does not exist, throws a SqlException.

Showing actual unhandled exceptions to the end user is bad for two reasons:

1. Users will be annoyed as they are cryptic and does not make much sense to the end users.
2. Exception contain information, that can be used for hacking into your application.

An exception is actually a class that derivess from System.Exception class. The System.Exception class has several useful properties, that provide valuable information about the exception.

Message: Gets a message that describes the current exception
Stack Trace: Provides the call stack to the line number in the method where the exception occurred.

```

public class Program 
{
   public static void Main()
   {
      try
      {
      StreamReader streamReader = new StreamReader(@"C:\Data.txt");
      Console.WriteLine(streamReader.ReadToEnd());
      streamReader.Close();
      }
      catch (Exception ex)
      {
         ex.FileName
         Console.WriteLine(ex.Message);
         Console.WriteLine(ex.StackTrace);
      }
   }
}
```

Example for checking database connection and similar:

```
catch (FileNotFoundException ex)
      {
        Console.WriteLine("Please check if the file {0} exists" , ex.FileName);
      }
```

Finally:

```
public class Program 
{
   public static void Main()
   {
      try
      {
      StreamReader streamReader = new StreamReader(@"C:\Data.txt");
      Console.WriteLine(streamReader.ReadToEnd());
      }
      catch (FileNotFoundException ex)
      {
         //Login details for DB
        Console.WriteLine("Please check if the file {0} exists" , ex.FileName);
      }
      finally
      {
      if(streamReader != null)
      {
      streamReader.Close(); // if we dont have finally, this would never perform
      }
      Console.WriteLine("Finally Block");
      }
   }
}
```

Control + i in visual studio = we can see all exceptions

Releasing System Resources

We can use try, catch and finally blocks fo exception handling:
**try** - The code that can possible cause an exeption will be in the try block.
**catch** - Handles the exception.
**finally** - Clean and free resources that the class was holding onto during the program execution. Finally block is optional.

**Note** It is a good practice to always release resources in the finally block, because finally block is guaranteed to execute, irrespective of wheather there is an exception or not

Specific exceptions will be caught before the base general exception, so specific exception blocks should always be on top fo the base exception block.
Otherwise, you will encounter a compile error.

### Inner Exceptions

The innerException property return the Exception instance that caused the current exception.

To retain the original exception pass it as a parameter to the constructor, of the current exception.

Always check if inner exception is not null before accessing any property of the inner exception object, else, you may get Null Reference Exception.

**To get the type of InnerException use GetType() method.** Really valuable for useful information in Debugging.

```
using System;
using System.IO;


public class Program 
{
   public static void Main()
   {
     Console.WriteLine("Enter First Number");
     int FN = Convert.ToInt32(Console.ReadLine());

     Console.WriteLine("Enter Second Number");
     int SN = Convert.ToInt32(Console.ReadLine());

     int Result = FN / SN;

     Console.WriteLine("Result is = {0}", Result);
   }
}
```

In above code if we add characters or big numbers we will get exception. This will solve partially problem.

```
using System;
using System.IO;

public class Program 
{
   public static void Main()
   {
      try{
         Console.WriteLine("Enter First Number");
     int FN = Convert.ToInt32(Console.ReadLine());

     Console.WriteLine("Enter Second Number");
     int SN = Convert.ToInt32(Console.ReadLine());

     int Result = FN / SN;

     Console.WriteLine("Result is = {0}", Result);
      }
      catch (Exception ex)
      {
         string filePath = @"C:\Users\blabla\log.txt"; //if we want to login errors and exception
         if (File.Exist(filePath))
         {
         StreamWriter sw = new StreamWriter(filePath);
         Console.WriteLine("There is a problem, please try later");
         sw.Write(ex.GetType().Name); //Choose what will be written in file
         sw.WriteLine();
         sw.Write(ex.Message);
         sw.Close();
         }
         else
         {
            throw new FileNotFoundException(filePath + " is not present", ex)
         }      
      }
   }
}
```

Additional protections:

```
using System;
using System.IO;


public class Program 
{
   public static void Main()
   {
      try{
               try{
               Console.WriteLine("Enter First Number");
               int FN = Convert.ToInt32(Console.ReadLine());

         Console.WriteLine("Enter Second Number");
         int SN = Convert.ToInt32(Console.ReadLine());

         int Result = FN / SN;

         Console.WriteLine("Result is = {0}", Result);
            }
            catch (Exception ex)
            {
               string filePath = @"C:\Users\blabla\log.txt"; //if we want to login errors and exception
               if (File.Exist(filePath))
               {
               StreamWriter sw = new StreamWriter(filePath);
               Console.WriteLine("There is a problem, please try later");
               sw.Write(ex.GetType().Name); //Choose what will be written in file
               sw.WriteLine();
               sw.Write(ex.Message);
               sw.Close();
               }
               else
               {
                  throw new FileNotFoundException(filePath + " is not present", ex)
               }
               
            }
      }
      catch (Exception exception)
      {
         Console.WriteLine("Current Exception = {0}", exception.GetType().Name);
         if (exception.InnerException != null)
         {
            Console.WriteLine("Current Exception = {0}", exception.InnerException.GetType().Name);
         }
      }  
   }
}
```

### Custom Exceptions

To understand custom exceptions, you should have good undestanding of
Part 21 - Inheritance
Part 40 - Exception Handling Basics
Part 41 - Inner Exception

When do you usually go for creating your own custom exceptions?
If none of the already existing dotnet exceptions adequately describes the problem.

Example:

1. I have an asp.net web applicaiton
2. The application should allow the user to have only one logged in session.
3. If the users is already logged in, and if he opens another browser windows and tries to login again, the application should throw an error stating he is already logged in another browser window.

With in the .NET framework we dont have any exception, that adequately describes this problem. So this scenario is one of the examples where you want to create a custom exception.

ON HOLD

### Exception handling abuse

Exception are unforeseen errors that occur when a program is running. For example, when an application is executing a query, the DB connection is lost. Exception handling is generally used to handle these scenarios.

Using exception handling to implement program logical flow is bad and is termed as exception handling abuse.

```
using System;
using System.IO;

public class Program 
{
   public static void Main()
   {
   try{
       Console.WriteLine("Please enter Numerator");
     int Numerator = Convert.ToInt32(Console.ReadLine()); 

     Console.WriteLine("Please enter Denominator");
     int Denominator = Convert.ToInt32(Console.ReadLine());  

     int Result = Numerator / Denominator;

     Console.WriteLine("Result is {0}", Result); 
   }
   catch (FormatException)
   {
      Console.WriteLine("Please enter a number");
   }
   catch (OverflowException)
   {
      Console.WriteLine("Only numbers between {0} && {1} are alowed", Int32.MinValue,Int32.MaxValue);
   }
    catch(DivideByZeroException)
    {
      Console.WriteLine("Denominator cant be a zero");
    }
    catch(Exception ex)
    {
      Console.WriteLine(ex.Message);
    }
   }
}
```

ABOVE is WRONG!!!

### Prevention Exception handling abuse


