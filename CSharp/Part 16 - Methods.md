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
         Program.EvenNumbers();
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
