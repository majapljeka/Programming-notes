```
using System.Runtime.InteropServices;

{
   private static void Main()
   {
      AddNumbers(10,20, new int[]{30,40,50});
      AddNumbers(10,20, null);
   }

   public static void AddNumbers(int firstNumber, int secondNumber, [Optional] int[] restOfNumbers)
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
