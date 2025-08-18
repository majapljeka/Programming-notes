1. A partial class or a struct can contain **partial methods.**
2. **A partial methods is created using the partial keyword.**
3. A partial method declaration consists of two parts.
   I)The definition (only the method signature)
   II)the implementation
   **These may be in separate parts of a partial class, or in the same part.**
4.**The implementaion for partial methods is optional**. If we dont provide the implementation, the compiler removes the signature and all calls to the method.
5. **Partial methods are private by default**, and it is a compile time error to include any access modifiers, including private.
6. **It is a compile time error, to include declaration and implementation** at the same time for partials method.
7. A partial method **return type must be avoid.**Including any other return type is compile time error.
8. **Signature of the partial declaration**, must match with the signature of the implementation.
9. **A partial method must be declared within a partial class or partial struct**. A non partial class or struct cannot include partial methods.
10. **A partial method can be implemented only once.** Trying to implement a partial method more than once, raises a compile time error.


```
using System;
using System.Collections.Generic;

public class Program 
{
   private static void Main()  //this can be divided in another .cs program file
   {
    SamplePartialClass SPC = new SamplePartialClass();
    SPC.PublicMethod();
   }
}


public partial class SamplePartialClass
{
  partial void SamplePartialMethod();

  partial void SamplePartialMethod()  //this can divided in another file/class
  {
    Console.WriteLine("SAmplePartial Method Invoked");
  }

  public void PublicMethod()
  {
     Console.WriteLine("Public Method Invoked");
     SamplePartialMethod();
  }
}

```

