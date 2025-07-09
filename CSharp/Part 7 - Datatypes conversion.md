### Implicit

```
 int i = 100;

        // float is bigger datatype than int. So, no loss of
        // data and exceptions. Hence implicit conversion
        float f = i;

        Console.WriteLine(f);

result is 100
```
### Explicit

```
 float f = 100.25F;
 //float f = 12341313349394394934939434.25F;  we can also try with much bigger number than integer can receive

        // Cannot implicitly convert float to int.
        // Fractional part will be lost. Float is a
        // bigger datatype than int, so there is
        // also a possiblity of overflow exception
        // int i = f;

        // Use explicit conversion using cast () operator
        int i = (int)f;

        // OR use Convert class
        // int i = Convert.ToInt32(f);
        // cast() doesnt throw any exception while Convert class does throw

        Console.WriteLine(i);
result is 100
```

### Difference betweeen Parse and tryParse

If the number is in a string format you have 2 options - Parse() and TryParse()

Parse() method throws an exception if it cannot parse the value, whereas TryParse() returns a bool indicating wheather it succeeded or failed.

Use Parse() if you are sure the value will be valid, otherwise use TryParse().

Parse (Convert String to integer)

```
using System;


public class Program
{
    public static void Main()
    {
        string number = "234";

        try
        {
            int i = int.Parse(number);
            Console.WriteLine("The number is {0}" , i);

        }
        catch(FormatException){
             Console.WriteLine("The input string is not in the correct format.");
        }

    }   
}


BUT if we assign value to number 100TH we will get exception, and here we need TryParse
```

**TryParse**

```
using System;


public class Program
{
    public static void Main()
    {
        string strNumber = "92329";
        //we can also try some logical numberlike 1234

            int Result = 0;
            bool isConversionSuccessful = int.TryParse(strNumber, out Result);

            if (isConversionSuccessful)
            {
            Console.WriteLine(Result);
            }
            else
            {
            Console.WriteLine("Please enter the correct number ");
            }
    }   
}
```

Explanation:

- int.Parse: This method is straightforward and throws an exception if the input string is not a valid integer.
- int.TryParse: This method is safer as it does not throw an exception and returns true if the conversion is successful and false otherwise. The converted integer is stored in the out parameter.
