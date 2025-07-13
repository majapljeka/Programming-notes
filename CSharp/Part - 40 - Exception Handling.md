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
        Console.WriteLine("Please check if the file {0} exists" , ex.FileName);
      }
      finally
      {
      if(streamReader != null)
      {
      streamReader.Close();
      }
      Console.WriteLine("Finally Block");
      }
   }
}
```

Releasing System Resources

We can use try, catch and finally blocks fo exception handling:
**try** - The code that can possible cause an exeption will be in the try block.
**catch** - Handles the exception.
**finally** - Clean and free resources that the class was holding onto during the program execution. Finally block is optional.

**Note** It is a good practice to always release resources in the finally block, because finally block is guaranteed to execute, irrespective of wheather there is an exception or not

Specific exceptions will be caught before the base general exception, so specific exception blocks should always be on top fo the base exception block.
Otherwise, you will encounter a compile error.
