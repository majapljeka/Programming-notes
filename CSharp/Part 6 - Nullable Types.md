In C# we are divided two broad categories:

- Value Types = int, float, double, structs, enums, etc
- Reference types = Interface, Class, delegates, arrays, etc

```
 String name = null;
 int i = 0; // NO

 int? i = null;  // if you want to make your value nullable just put ?
```


```
  bool? AreYouMajor = null;
  if (AreYouMajor == true)
  {
      Console.WriteLine("User is Major=result is True");
  }
  else if (AreYouMajor == false)
  {
      Console.WriteLine("User is not Major=result is False");
  }
  else
  {
      Console.WriteLine("User doesnt answer=result=null");
  }
```

#### Null coalescing operator

```
int? TicketsOnSale = null;
int AvailableTickets;

int TicketsOnSale == 100;
AvailableTickets = TicketsOnSale ?? 0; // this line exchange if lines of codes below:

if (TicketsOnSale = null)
{
 AvailableTickets = 0;
}
else
{
 AvailableTickets = (int)TicketsOnSale;
}



Console.WriteLine("AvailableTickets = {0}", AvailableTickets);
```
