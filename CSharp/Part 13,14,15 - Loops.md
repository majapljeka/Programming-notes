Task: The client is asked to write number and based on that number the program will write below even numbers until user number. 
(ex. if 10 is written answer will be 0 2 4 6 8 10)

### WHILE loop

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

