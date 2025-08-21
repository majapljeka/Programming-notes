1. A dictionary is a collection of (key, value) pairs.
2. Dictionary class is present in System.Collections.Generic namespace.
3. When creating a dictionary, we need to specify the type for key and value.
4. Dictionary provides fast lookups for values using keys.
5. Keys in the dictionary must be unique.



```
using System;
using System.Collections.Generic;
using System.Runtime.InteropServices;

public class Program 
{
   private static void Main()
   {
      Customer customer1 = new Customer()
      {
        ID = 101,
        Name = "Mark",
        Salary = 5000
      };

       Customer customer2 = new Customer()
      {
        ID = 104,
        Name = "Sam",
        Salary = 3000
      };

       Customer customer3 = new Customer()
      {
        ID = 107,
        Name = "Pat",
        Salary = 7000
      };

      Dictionary<int, Customer> dictionaryCustomer = new Dictionary<int, Customer>();
      dictionaryCustomer.Add(customer1.ID, customer1);
      dictionaryCustomer.Add(customer2.ID, customer2);
      dictionaryCustomer.Add(customer3.ID, customer3);

      Customer customer1111 = dictionaryCustomer[107]; //[107 je customer3 ID]
      //Console.WriteLine("ID = {0}, Name = {1}, Salary = {2}", customer1111.ID, customer1111.Name, customer1111.Salary );


      // moze i na ovaj nacin da se napise foreach      foreach(var customerKeyValuePair in dictionaryCustomer)
      foreach(KeyValuePair<int,Customer> customKeyValuePair in dictionaryCustomer)
      {
        Console.WriteLine("Key = {0}", customKeyValuePair.Key);
        Customer cust = customKeyValuePair.Value;
        Console.WriteLine("ID = {0}, Name = {1} , Salary = {2}", cust.ID,cust.Name, cust.Salary);
        Console.WriteLine("----------------------------------------------------------------------");
      }
   }
}

public class Customer
{
  public int ID { get; set; }
  public string Name { get; set; }
  public int Salary{ get; set; }
}
```
