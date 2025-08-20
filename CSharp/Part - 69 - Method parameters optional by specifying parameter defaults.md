**Optional parameters must appear after all required parameters.**

```
public class Program 
{
   private static void Main()
   {
      AddNumbers(10,20, new object[]{30,40,50});
      AddNumbers(10,20, null);
   }

   public static void AddNumbers(int firstNumber, int secondNumber, params object[] restOfNumbers = null)
    {
      int result = firstNumber + secondNumber;
      if (restOfNumbers != null)
      {
        foreach(int i in restOfNumbers)
        {
          result += i;
        }
      }
      Console.WriteLine("Sum = " + result.ToString());
    }
}
```

Another example:

```
public class Program 
{
   private static void Main()
   {
     Test(1,c:2);
    // try this Test(1,2);
   }

   public static void Test(int a, int b = 10, int c=20)
    {
     Console.WriteLine("a = ", a);
     Console.WriteLine("b = ", b);
     Console.WriteLine("c = ", c);
    }
}
```
