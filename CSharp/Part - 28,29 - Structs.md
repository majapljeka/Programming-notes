```
public class Student
{
    private int _id;
    private string _name;

  we can right click on variable and choose refactoring Property which will generate Encapsulate field Property for us.


.......
    public int Id { get => _id; set => _id = value; }
    public string Name { get => _name; set => _name = value; }
}
```

Just like classes structs can have

1. Private Fields
2. Public Properties
3. Constructors
4. Methods

Object initializer syntax, introduced in c# 3.0 can be used to initialize either struct or a class.

Note: There are several differences between classes and structs which we will be looking 

```
public struct Student
{
    private int _id;
    private string _name;

    public int Id { get => _id; set => _id = value; }
    public string Name { get => _name; set => _name = value; }

    public Student(int Id, string Name)
    {
        this._id = Id;
        this._name = Name;
    }

    public void PrintDetails()
    {
        Console.WriteLine("Id = {0} && Name = {1}", this._id, this._name);
    }
}

public class Program
{
    public static void Main()
    {
        Student S1 = new Student(101, "Mark"); // Here we pass parameters directly
        S1.PrintDetails();

        Student S2 = new Student();
        S2.Name = "John";
        S2.Id = 234;
        S2.PrintDetails();

        // Object initializer syntax

        Student S3 = new Student
        {
            Id = 103,
            Name = "Bob"
        };
    }
```

### Differences between Structs and Classes

A structs is a value type (int, string, enum, boolean) where as a class is reference type (Classess, Interfaces, Delegates).

All the differences that are appplicable to value types and reference types are also applicable to classess and structs.

Structs are stored on stack, where as classess are stored on the heap.

Value types hold their values in memory where they are declared, but reference types hold a reference to an object in memory.

Value types are destroyed immediately after the scope is lost, whre as for reference types only the reference variable is destroyed after the scope is lost. The object is later destroyed by garbage collector. 

**When you copy a struct into another struct**, a new copy of that struct gets created and modifications on one struct will not affect the values contained by other struct.

**When you copy a class into another class**, we only get a copy of the reference variable. Both the reference variables point to the same object on the heap. So, operations on one variable will affect the values contained by the other reference variable.

Structs cant have destructors, but classes can have destructors.

Structs cannot have explicit parameter-less constructor where as a class can.

Struct cant injerit from another calss where as class can, Both structs and classess can inherit from an interface

![StackAndHeap](https://github.com/majapljeka/Programming-notes/blob/main/CSharp/images/stackAndHeap.png)

Examples of structs in the .NET framework - **int (System.Int32), double(System.Double)**

Note 1: A class or a struct cannot inherit from another struct. Struct are sealed types.
Note 2: How do you prevent a class from being inherited? or What is the significance of sealed keyword?

`public sealed class Blabla` -> cannot act as a Parent type.

```
public class Student
{
    public int ID { get; set; }
    public string Name { get; set; }
}

public class Program
{
    public static void Main()
    {
        int i = 10;
        int j = i;
        j = j + 1;

        Console.WriteLine("i = {0} && j = {1}", i, j);

        Student S1 = new Student();
        S1.ID = 101;
        S1.Name = "Mark";

        Student S2 = S1;

        S2.Name = "Mary";

        Console.WriteLine("S1.Name = {0} && S2.Name = {2}", S1.Name, S2.Name);

        /* result isL i = 10 && j = 11
        S1.Name = Mary && S2.Name = Mary
        */
    }
```
