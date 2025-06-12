### if statement

- if statement
- if else statement
- difference between && and &
- difference between || and |

|| - mean if any of conditions is True dont check further (checking one condition)
| - mean even if one of conditions is True, go further and check (checking both conditions)

&& - mean both conditions has to be True, if one is False dont checking further (checking only one)
& - even if one conditions is False checking further (checking both conditions)

```
Console.WriteLine("Enter Your Number");
int Usernumber = int.Parse(Console.ReadLine());
if (Usernumber==1)
{
Console.WriteLine("Dear User Your Number is 1");
}
else if (Usernumber == 2)
{
Console.WriteLine("Dear User Your Number is 2");
}
else if (Usernumber == 3)
{
Console.WriteLine("Dear User Your Number is 3");
}
else if (Usernumber == 4)
{
Console.WriteLine("Dear User Your Number is 4");
}
else if (Usernumber == 5)
{
Console.WriteLine("Dear User Your Number is 5");
}
else
{
Console.WriteLine("Dear User Your Number is Not Between 1-5");
}
```

### Switch statement

Multiple if statements can be replaced with Switch statement

```
Console.WriteLine("Please Enter a number");
int userNumber = int.Parse (Console.ReadLine());
switch (userNumber)
{
    case 10:
        Console.WriteLine("Your number is 10");
        break;

    case 20:
        Console.WriteLine("Your number is 20");
        break;

    case 30:
        Console.WriteLine("Your number is 30");
        break;

    default:
        Console.WriteLine("Your number is not 10,20 or 30");
        break;

}
```

Also, it can be written on this way:

```
Console.WriteLine("Please Enter a number");
int userNumber = int.Parse (Console.ReadLine());
switch (userNumber)
{
    case 10:
    case 20:
    case 30:
        Console.WriteLine("Your number is {0}", userNumber);
        break;

    default:
        Console.WriteLine("Your number is not 10,20 or 30");
        break;

}
```

### Coffee Purchase program

Start is label in the program where you can jump.

```
 int totalCoffeeCost = 0;
 Start:
 Console.WriteLine("Please select your coffe size: 1 small , 2 - Medium, 3 - Large");
 int userChoice = int.Parse(Console.ReadLine());


 switch (userChoice)
 {
     case 1:
         totalCoffeeCost += 1;
         break;
     case 2:
         totalCoffeeCost += 2;
         break;
     case 3:
         totalCoffeeCost += 3;
         break;

     default:
         Console.WriteLine("Your choice is invalid {0}", userChoice);
         goto Start;

 }

 Decide:
 Console.WriteLine("Do yo want to buy another coffee - Yes or No?");
 string userDecision = Console.ReadLine();
 
 switch (userDecision.ToUpper()) {

     case "YES":
         goto Start;
     case "NO":
         break;
     default:
         Console.WriteLine("Your choice is invalid {0}. Please try again.... ", userDecision);
         goto Decide;

 }

 Console.WriteLine("Thank you for shopping with us");
 Console.WriteLine("The total bill amount is {0}", totalCoffeeCost);
```
