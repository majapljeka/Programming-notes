**Marking the class fields public and exposing to the external world, as you will not have over what gets assigned and returned. Never exposed publicly variable values.**

```
public class Student
{
    public int ID;
    public string Name;
    public int PassMark;        
}

public class Program
{
    public static void Main()
    {
        Student C1 = new Student();
        C1.ID = -101;
        C1.Name = null;
        C1.PassMark = -100;
        Console.WriteLine("ID = {0} & Name = {1} && PassMark = {2}", C1.ID, C1.Name, C1.PassMark);
    }
```

### Getter and Setter Methods

Programming languages that does not have properties using getter and setter methods to encapsulate and protect fields.
Encapsulation is the one of primary pillars of OOO.
Now we can try mark all variables as private and try to change them through SetId method -> and we will get exception.

```
public class Student
{
    private int ID;
    private string Name;
    private int PassMark;


    public void SetId(int id)
    {
        if (id <= 0)
        {
            throw new Exception("Student ID cannot be negative");
        }
        this.ID = id;
    }

    public int GetId()
    {
        return this.ID;
    }
}

public class Program
{
    public static void Main()
    {
        Student C1 = new Student();
        C1.SetId(-101);       
    }
}
```

... and if we want to run normaly, chane main method, here is example:

```
  public static void Main()
  {
      Student C1 = new Student();
      C1.SetId(101);

      Console.WriteLine("Student Id = {0}", C1.GetId());  
  }
```

Lets now make getter and setter methods for the name:

```public class Student
{
    private int ID;
    private string Name;
    private int PassMark;

    public void SetName(string name)
    {
        if (string.IsNullOrEmpty(Name))
        {
            throw new Exception("Name cannot be null or empty");
        }
        this.Name = name;
    }

    public string GetName()
    {
        return string.IsNullOrEmpty(this.Name) ? "No name." : this.Name;

        /* 
        if (string.IsNullOrEmpty(this.Name))
        {
            return "No Name";
        }
        else {
            return this.Name;
        }*/
    }
}
```
