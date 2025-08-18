To understand the difference consider the example below. The ToString() method, expects the instance on which you are invoking to be NOT NULL. If the object is NULL, **you get a NULL Reference exception.**

```
using System;
public class MainClass
{
    public static void Main()
    {
        Customer C1 = null;
        Console.WriteLine(C1.ToString());
    }
}
public class Customer
{
    public string Name { get; set; }
}
```

On the other hand, Convert.ToString() returns an empty string if the object is **NULL**.

```
using System;
public class MainClass
{
    public static void Main()
    {
        Customer C1 = null;
        Console.WriteLine(Convert.ToString(C1));
    }
}
public class Customer
{
    public string Name { get; set; }
}
```

So in summary, Convert.ToString() handles null, while ToString() doesn't, and throws a NULL Reference exception. Depending on the type of the application, architecture and what you are trying to achieve, you choose one over the other.
