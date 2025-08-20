What are Indexers?

Indexers allow instances of a class to be indexed just like arrays.

Indexers in asp.NET

```
Session["Session1"] = "Session 1 Data";
Session["Session2"] = "Session 2 Data";

Response.Write("Session 1 Data = " + Session[0].ToString());

Response.Write("Session 2 Data = " + Session[Session2].ToString());
```


Indexers

```
public class Employee
    {
      public int EmployeeID { get; set; } 
      public string Name { get; set; }  
      public string Gender { get; set; }
    }

    public class Company
    {
      private List<Employee> listEmployees;

      public Company()
      {
        listEmployees = new List<Employee>();
        listEmployees.Add(new Employee() { EmployeeID = 1, Name  = "Mike", Gender = "Male"  });
        listEmployees.Add(new Employee() { EmployeeID = 2, Name  = "Pam", Gender = "Female"  });
        listEmployees.Add(new Employee() { EmployeeID = 2, Name  = "John", Gender = "Male"  });
      }

    public string this[int EmployeeID]
    {
      get
      {
        return listEmployees.FirstOrDefault(emp => emp.EmployeeID == EmployeeID).Name;
      }

      set
      {
        listEmployees.FirstOrDefault(emp => emp.EmployeeID == EmployeeID).Name = value;
      }
    }

```
