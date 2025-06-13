Namespaces are used to organize our programs.They are not corespond to file, directory or assembly names.
They could be written in separate files and / or separate assemblies and still belongs to the same namespace.

If we want to reference our main project to other project in Solution explorer or other project at all, we can go:
right click on our project -> add Reference -> mark external project and we can user their namespaces and classes!

Namespaces can be nested in 2 ways.

```
using System;
//also we can use namespace aliases like using PATA = ProjectA.TeamA;
PATB = ProjectA.TeamB;

 internal class Program
 {
     static void Main(string[] args)
     {
        ProjectA.TeamA.classA.Print(); // OR we can use it without ProjectA.TeamA but we have to define them as use System;
        ProjectA.TeamB.classA.Print();
        // PATA.classA.Print();
     }
 }
 namespace ProjectA {
     namespace TeamA
     {   
     class classA 
         {
             public static void Print() {
                 Console.WriteLine("Team A print method");  
             }
         }
     }

namespace ProjectA {
     namespace TeamB
     {   
     class classA 
         {
             public static void Print() {
                 Console.WriteLine("Team B print method");  
             }
         }
     }
```
