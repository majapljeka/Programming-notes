In C#, an enum (short for enumeration) is a value type that defines a set of named constants. It provides a way to group related integral constants under a single name, making code more readable, maintainable, and less prone to errors compared to using raw numeric values directly
Enums are strongly typed constants.

1. Enums are enumerations.
2. Enums are strongly typed constants. Hence, an explicit cast is needed to convert from enum type to an integral type and vice versa. Also, an enum of one type cannot be implicitly assigned to an enum of another type even though the underlying value of their members are the same.
3. The default underlying type of an enum is int.
4. The default value for first element is ZERO and get incremented by 1.
5. It is possible to customize the underlying type and values.
6. Enums are value types.
7. Enum keyword (small letters) is used to create enumerations, where as Enum class, contains static GetValues() and GetNames() methods which can be used to list Enum underlying type value and Names.

If a program uses set of integral numbers, consider replacing them with enums. Otherwise the program become less:
Readable
Maintanable

```
enum DanUSedmici
{
    Ponedeljak,
    Utorak,
    Sreda,
    Cetvrtak,
    Petak,
    Subota,
    Nedelja
}

DanUSedmici danas = DanUSedmici.Petak;

if (danas == DanUSedmici.Petak)
{
    Console.WriteLine("Vikend se približava!");
}
```


```
using System;

public class Program 
{
   public static void Main()
   {
    Customer[] customers = new Customer[3];
    customer[0] = new Customer
    {
      Name = "Mark",
      Gender = 1
    };
    customer[1] = new Customer
    {
      Name = "Mary",
      Gender = 2
    };
    customer[2] = new Customer
    {
      Name = "Same",
      Gender = 0
    };

    foreach (Customer customer in customers)
    {
      Console.WriteLine("Name = {0} && Gender = {1}", customer.Name, GetGender(customer.Gender));
    }
   }
   public static string GetGender(int gender)
   {
    switch(gender)
    {
      case 0:
        return "Unknwown";
      case 1:
        return "Male";
      case 2:
        return "Female";
      default:
        return "Invalid data detected";
    }
   }
}

// 0 - unknown
// 1 - Male
// 2 - Female
public class Customer
{
  public string Name {get; set;}
  public int Gender {get; set;}
}
```

### Enums Example

```
using System;

public class Program 
{
   public static void Main()
   {
    Customer[] customers = new Customer[3];
    customer[0] = new Customer
    {
      Name = "Mark",
      Gender = Gender.Male
    };
    customer[1] = new Customer
    {
      Name = "Mary",
      Gender = Gender.Female
    };
    customer[2] = new Customer
    {
      Name = "Same",
      Gender = Gender.Unknown
    };

    foreach (Customer customer in customers)
    {
      Console.WriteLine("Name = {0} && Gender = {1}", customer.Name, GetGender(customer.Gender));
    }
   }
   public static string GetGender(Gender gender)
   {
    switch(gender)
    {
      case Gender.Unknown:
        return "Unknwown";
      case Gender.Male:
        return "Male";
      case Gender.Female:
        return "Female";
      default:
        return "Invalid data detected";
    }
   }
}

public enum Gender
{
  Unknown,
  Male,
  Female
}

// 0 - unknown
// 1 - Male
// 2 - Female
public class Customer
{
  public string Name {get; set;}
  public Gender Gender {get; set;}
}
```

### Enums

```
using System;

public class Program 
{
   public static void Main()
   {
    short[] Values = (short[])Enum.GetValues(typeof(Gender));
    foreach (short value in Values)
    {
      Console.WriteLine(value);
    }

    string[] Names = Enum.GetNames(typeof(Gender));
    foreach (string Name in Names)
    {
      Console.WriteLine(Name);
    }
   }
}

public enum Gender : short
{
  Unknown = 1,
  Male = 5,
  Female = 23
}
```


```
using System;

public class Program 
{
   public static void Main()
   {
      Gender gender = (Gender)Season.winter;
   }
}

public enum Gender 
{
  Unknown = 1,
  Male = 5,
  Female = 23
}


public enum Season
{
  Unknown = 1,
  Male = 5,
  Female = 23
}
```


