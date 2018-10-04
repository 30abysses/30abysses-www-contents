# C# vs. TypeScript: Basic Types, Array


# C# Array

* Keywords: `[`, `]`, `{`, `}`
* C# arrays' sizes are established when they are created.
* The `System.Array` class is the base class for all C# arrays and
  provides array operation methods.
* In addition to single-dimensional arrays, C# also supports
  multidimensional and jagged arrays.

```CSharp
int[] s = { 1, 2, 3 };
System.Console.WriteLine(s[1]);                 // prints `2`

int[,] m = { { 1, 2 }, { 3, 4 } };
System.Console.WriteLine(m[1, 1]);              // prints `4`

int[][] j = { new[] { 1, 2 }, new[] { 3, 4 } };
System.Console.WriteLine(j[1][1]);              // prints `4`
```

* C# arrays are 0-indexed by default.  However, it is possible to create
  arrays that are not.

```CSharp
var a = Array.CreateInstance(typeof(int), new[] { 3 }, new[] { 2 });
System.Console.WriteLine(a.Rank);              // prints `1`
System.Console.WriteLine(a.GetType());         // prints `System.Int32[*]`
System.Console.WriteLine(a.GetLength(0));      // prints `3`
System.Console.WriteLine(a.GetLowerBound(0));  // prints `2`
System.Console.WriteLine(a.GetUpperBound(0));  // prints `4`
// System.Console.WriteLine(a.GetValue(0));    // throws `System.IndexOutOfRangeException`: "Index was outside the bounds of the array."
// System.Console.WriteLine(a.GetValue(1));    // throws `System.IndexOutOfRangeException`: "Index was outside the bounds of the array."
System.Console.WriteLine(a.GetValue(2));       // prints `0`
System.Console.WriteLine(a.GetValue(3));       // prints `0`
System.Console.WriteLine(a.GetValue(4));       // prints `0`
// System.Console.WriteLine(a.GetValue(5));    // throws `System.IndexOutOfRangeException`: "Index was outside the bounds of the array."
```

* For more information, see
  * [The `System.Array` class](https://docs.microsoft.com/en-us/dotnet/api/system.array?view=netcore-2.1)
  * [Arrays](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/)


# TypeScript Array

* Keywords: `[`, `]`, `Array<T>`, `...`

```TypeScript
let strings: string[] = ["foo", "bar"];
let numbers: Array<number> = [1, 2, 3];
let mixed: (string | number)[] = [...strings, ...numbers];
console.log(mixed);                                         // prints `["foo", "bar", 1, 2, 3]`
```

* TypeScript arrays implement the `Array<T>` interface.
  * https://github.com/Microsoft/TypeScript/blob/release-3.1/lib/lib.es2015.core.d.ts#L21-L65
  * https://github.com/Microsoft/TypeScript/blob/release-3.1/lib/lib.es2015.iterable.d.ts#L50-L68
  * https://github.com/Microsoft/TypeScript/blob/release-3.1/lib/lib.es5.d.ts#L1135-L1285
* TypeScript arrays are mutable.

```TypeScript
let numbers: Array<number | string> = [0, 1, 2, 3, 4];
console.log(numbers);           // prints `[0, 1, 2, 3, 4]`

numbers.splice(2, 1);
console.log(numbers);           // prints `[0, 1, 3, 4]`

numbers.splice(2, 0, "foo");
console.log(numbers);           // prints `[0, 1, "foo", 3, 4]`

numbers.shift();
console.log(numbers);           // prints `[1, "foo", 3, 4]`

numbers.pop();
console.log(numbers);           // prints `[1, "foo", 3]`

numbers.unshift("lol", "wut");
console.log(numbers);           // prints `["lol", "wut", 1, "foo", 3]`

numbers.push("bar", "baz");
console.log(numbers);           // prints `["lol", "wut", 1, "foo", 3, "bar", "baz"]`
console.log(numbers.length);    // prints `7`

numbers[10] = 9000;
console.log(numbers);           // prints `["lol", "wut", 1, "foo", 3, "bar", "baz", …, 9000]`
console.log(numbers.length);    // prints `11`

numbers.length = 3;
console.log(numbers);           // prints `["lol", "wut", 1]`
```
