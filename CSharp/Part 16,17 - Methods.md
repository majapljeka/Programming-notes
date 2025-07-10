## Methods

### Structure of methods

```
[attributes]
access-modifiers return-type method-name (parameters)
{
Method Body
}
```

Methods = Functions, are extremely useful because they alow you to define your logic once, and use it in many places.

### Difference between static and instance methods

In C#, instance methods are associated with a specific instance (object) of a class, while static methods belong to the class itself

Method static main belongs **class** itself,  while Even numbers in instance method. If you want call EvenNumbers() in Main method you have always to make instance of the class program:

```
 internal class Program
 {
     static void Main(string[] args)
     {
        Program p = new Program();
        p.EvenNumbers();
     }

     public void EvenNumbers() {

         int Start = 0;
         while (Start <= 20) {

             Console.WriteLine(Start);
             Start = Start + 2;  
         }

     
     }
 }
```

If we change EvenNumbers() to to **static** return type, cannot be accessed with instance reference.

```
  internal class Program
  {
      static void Main(string[] args)
      {
         Program.EvenNumbers(); // OR just EvenNumbers(); since we are in the same class
      }

      public static void EvenNumbers() {

          int Start = 0;
          while (Start <= 20) {

              Console.WriteLine(Start);
              Start = Start + 2;  
          }
     
      }
  }
```

### How to pass parameters

Allow client to make even numbers until 30.

```
 internal class Program
 {
     static void Main(string[] args)
     {
        Program.EvenNumbers(30);
     }

     public static void EvenNumbers(int clientTarget) {

         int Start = 0;
         while (Start <= clientTarget) {

             Console.WriteLine(Start);
             Start = Start + 2;  
         }

     
     }
 }
```

We are adding new function Add() which calculates values:

```
 internal class Program
 {
     static void Main(string[] args)
     {
        Program.EvenNumbers(30);
        Program p = new Program();
        int sum = p.Add(10, 20);
        Console.WriteLine("The Sum is {0}", sum);
     }

     public static void EvenNumbers(int clientTarget) {

         int Start = 0;
         while (Start <= clientTarget) {

             Console.WriteLine(Start);
             Start = Start + 2;  
         }
     
     }

     public int Add(int FN, int SN) { 
     return FN + SN;
     }
 }
```

## Different types of methods parameters

There are the four types of method parameters:

1. Value parameters
2. Reference parameters
3. Output Parameters
4. Parameter Arrays 





1. Passing Parameter by Value example:

```
 internal class Program
 {
     static void Main(string[] args)
     {
         int i = 0;
         SimpleMethod(i);
         Console.WriteLine(i);
     }

     public static void SimpleMethod(int j) 
     {
         j = 101;
     }
 }

RESULT is 0!
```

2. Passing Parameter by reference example (**ref**):

```
 internal class Program
 {
     static void Main(string[] args)
     {
         int i = 0;
         SimpleMethod(ref i);
         Console.WriteLine(i);
     }

     public static void SimpleMethod(ref int j) 
     {
         j = 101;
     }
 }

RESULT is 101!
```

3. Output parameters **out** (Simple f-ction which add two numbers and written their sum)

```
internal class Program
{
    static void Main(string[] args)
    {
        int Total = 0;
        int Product = 0;
        Calculate(10, 20, out Total, out Product);
        Console.WriteLine("Sum = {0} && Product = {1}", Total,Product);
    }

    public static void Calculate(int FN, int SN, out int Sum, out int Product) 
    {
        Sum = FN + SN;
        Product = FN * SN;
    }
}
```

4. Parameter Arrays - **params**
   It is worth to mention that params should be on last place in method params and only can be one params parameter!

```
 internal class Program
 {
     static void Main(string[] args)
     {
         int[] Numbers = new int[3];

         Numbers[0] = 100;
         Numbers[1] = 101;
         Numbers[2] = 102;

         ParamsMethod();
         ParamsMethod(Numbers);
         ParamsMethod(1,2,3,4,5);
     }

     public static void ParamsMethod(params int[] Numbers) 
     {
         Console.WriteLine("There are {0} elements", Numbers.Length);
         foreach (int i in Numbers)
         { 
         Console.WriteLine(i);
         }
     }
 }
```


##### Method parameters VS Method Arguments
