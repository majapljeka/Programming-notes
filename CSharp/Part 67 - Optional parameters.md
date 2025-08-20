**A parameter array must be the last parameter in a formal parameter list. The following function will not compile.**

```
public class Program 
{
   private static void Main()
   {
      AddNumbers(10,20);
   }

   public static void AddNumbers(int firstNumber, int secondNumber, params object[] restOfNumbers)
    {
      int result = firstNumber + secondNumber;
      if (restOfNumbers != null)
      {
        foreach(int i in restOfNumbers)
        {
          result += i;
        }
      }
      Console.WriteLine("Sum = " + result);
    }

}
```

This is without params parameter which is optional in this case, we can also initialize more than one value for restOfNumbers params like this:

`AddNumbers(10,20, new object[]{30,40,50});`

And also like this, where 30, 40 and 50 are assigned to restOfNumbers parameter automatically:

`AddNumbers(10,20, 30,40,50);`
