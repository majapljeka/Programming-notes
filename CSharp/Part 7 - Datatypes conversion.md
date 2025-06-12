### Implicit

```
 int i = 100;

        // float is bigger datatype than int. So, no loss of
        // data and exceptions. Hence implicit conversion
        float f = i;

        Console.WriteLine(f);

result is 100
```
### Explicit

```
 float f = 100.25F;
 //float f = 12341313349394394934939434.25F;  we can also try with much bigger number than integer can receive

        // Cannot implicitly convert float to int.
        // Fractional part will be lost. Float is a
        // bigger datatype than int, so there is
        // also a possiblity of overflow exception
        // int i = f;

        // Use explicit conversion using cast () operator
        int i = (int)f;

        // OR use Convert class
        // int i = Convert.ToInt32(f);
        // cast() doesnt throw any exception while Convert class does throw

        Console.WriteLine(i);
result is 100
```

### Difference betweeen Parse and tryParse

Parse (Convert String to integer)

```
string number = "1234";
int i = i.Parse(number);
Console.WriteLine(i);


BUT if we assign value to number 100TH we will get exception, and here we need TryParse
```

TryParse

```
string strNumber = "200t";
//we can also try some logical numberlike 1234

int result = 0;
bool isConversionSuccessful = int.TryParse(strNumber, out result);

if (isConversionSuccessful)
{
Console.WriteLine(result);
}
else
{
Console.WriteLine("please enter the correct number " + r);
}
```
