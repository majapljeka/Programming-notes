### WHILE loop

The while loop:

1. While loop checks the conditions first.
2. If the condition is true, statements with in the loop are executed.
3. This process is repeated as long as the condition evaluates to true.

Note: Dont forget to update the variable participating in the condition,so the loop end, at some point.

Task: The client is asked to write number and based on that number the program will write below even numbers until user number. 
(ex. if 10 is written answer will be 0 2 4 6 8 10)

```
int[] Numbers = new int[3];

Numbers[0] = 101;
Numbers[1] = 102;
Numbers[2] = 103;

int j = 0;
while (j < Numbers.Length)
{
   Console.WriteLine(Numbers[j]);
   j++;
}
```



```
Console.WriteLine("Please enter your target");
int userTarget = int.Parse(Console.ReadLine());

int Start = 0;

while (Start <= userTarget)
{
   Console.Write(Start); //not WriteLine because we would like have all in one line
   Start = Start + 2;
} 
```

### DO

Do While loop

1. A do loop checks its conditions at the end of the loop.
2. This means that the do loop is guaranted to execute at least one time.
3. Do loops are used to present a menu to the user.

```
 string userChoice = "";

 do
 {
     Console.WriteLine("Please enter your target");
     int userTarget = int.Parse(Console.ReadLine());

     int Start = 0;

     while (Start <= userTarget)
     {
         Console.Write(Start + " "); //not WriteLine because we would like have all in one line
         Start = Start + 2;
     }
     do
     {
         Console.WriteLine("Do you want to continue - Yes or No");

         userChoice = Console.ReadLine().ToUpper();
         if (userChoice != "YES" && userChoice != "NO")
         {
             Console.WriteLine("Invalid choice, please say Yes or No");

         }
     } while (userChoice != "YES" && userChoice != "NO");

 } while (userChoice == "YES");

 /* Recommendation is to avoid goto statement - label - due to debugging. We have that case in coffee purchasing program in 13.lesson*/
```

### FOR

The for loop

A for loop is very similar to while loop. In a while loop we do the initialization at one place, condition check at another place, and modifying the variable at another place, where as for loop has all of these at one place.

Example for loop with **break**

```
for (int i = 0; i <= 20; i++)
{
    Console.WriteLine(i);
    if (i == 10)
        break;

}
```
If the task is to only print even number until 20, just change for loop statement:
for (int i = 0; i <= 20; **i = i + 2** )

#### Continue in for loop
It will print even numbers in loop only - Solution #3

```
 for (int i = 0; i <= 20; i = i + 2 )
 {
      if (i % 2 == 1)
      continue;

      Console.WriteLine(i);

 }
```

Another example of FOR loop:
```
int[] Numbers = new int[3];

Numbers[0] = 101;
Numbers[1] = 102;
Numbers[2] = 103

for (int i = 0; i < Numbers.Length; i++)
{
    Console.WriteLine(Numbers[i]); 
}
```

### FOREACH

A foreach loop is user to iterate through the items in a collection. For example, foreach loop can be used with arrays or collections such as ArrayList, HashTable and Generics. 

```
int[] Numbers = new int[3];

Numbers[0] = 101;
Numbers[1] = 102;
Numbers[2] = 103

//If we have collection of something (ArrayList, HashTable, Generics)
foreach (int k in Numbers)
{
   Console.WriteLine(k);
}
```

#### Difference between while and do loop

**While** first check conditions. if condition is true loop is running until conditions evaluates True. Loops should end at some point!
**Do** loops check condition at the end of loop, which mean will be executed at least one time.
Do loops are used when we want to present some kind of menu to the user.

