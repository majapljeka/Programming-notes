- Boolean type - Only true or false
- Integral Types = sbyte, byte, short, ushort, int, uint, long, ulong, char
- Floating Types - float and double
- Decimal Types
- String Types


[Built-in types (C# reference)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/built-in-types)


```
int i = 0;
Console.WriteLine("Min = {0}", int.MinValue);
Console.WriteLine("Min = {0}", int.MaxValue);
```

### Strings

[Escape Sequences](https://learn.microsoft.com/en-us/cpp/c-language/escape-sequences?view=msvc-170)

```
string Name = "\"Name";
string Name2 = "C:\\Pragim\\DotNet\\Training\\Csharp"
Console.WriteLine(Name);
Console.WriteLine(Name2);
```

[Verbatim literals](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/verbatim)
```
 string filename1 = @"c:\documents\files\u0066.txt";
 string filename2 = "c:\\documents\\files\\u0066.txt";

 Console.WriteLine(filename1);
 Console.WriteLine(filename2);
```
