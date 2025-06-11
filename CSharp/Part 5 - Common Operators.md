[Common Operators](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/)

```
 // Assignment Operator example
            // Single = is the assignment operator
            int i = 10;
            bool b = true;

            // For dividing 2 numbers we can use either
            // % or / operators
            int numerator = 10;
            int denominator = 2;

            // Arithmentic operator / returns quotient
            int quotient = numerator / denominator;
            Console.WriteLine("Quotient = {0}", quotient);

            // Arithmentic operator % returns remainder
            int remainder = numerator % denominator;
            Console.WriteLine("Remainder = {0}", remainder);

            // To compare if 2 numbers are
            // equal use comparison operator ==
            int number = 10;
            if (number == 10)
            {
                Console.WriteLine("Number is equal to 10");
            }

            // To compare if 2 numbers are not
            // equal use comparison operator !=
            if (number != 5)
            {
                Console.WriteLine("Number is not equal to 5");
            }

            // When && operator is used all the conditions must
            // be true for the code in the "if" block to be executed
            int number1 = 10;
            int number2 = 20;

            if (number1 == 10 && number2 == 20)
            {
                Console.WriteLine("Both conditions are true");
            }

            // When || operator is used the code in the "if" block
            // is excuted if any one of the condition is true
            number1 = 10;
            number2 = 21;

            if (number1 == 10 || number2 == 20)
            {
                Console.WriteLine("Atleast one of the condition is true");
            }
```

```
The example below is not using the ternary operator. Look at the amount of code we have to write to check if a number is equal to 10, and then initialise a boolean variable to true or false depending on whether the number is equal to 10 or not.

using System;
namespace ConsoleApplication1
{
    class Program
    {
        public static void Main()
        {
            int number = 10;

            bool isNumber10;

            if (number == 10)
            {
                isNumber10 = true;
            }
            else
            {
                isNumber10 = false;
            }

            Console.WriteLine("Number == 10 is {0}", isNumber10);
        }
    }

}
```

**Ternary operator example** : We have rewritten the above program using ternary operator. Notice the amount of code we have to write is greatly reduced.

```
using System;
namespace ConsoleApplication1
{
    class Program
    {
        public static void Main()
        {
            int number = 10;

            // Ternary operator example
            bool isNumber10 = number == 10 ? true : false;

            Console.WriteLine("Number == 10 is {0}", isNumber10);
        }
    }
}

```
