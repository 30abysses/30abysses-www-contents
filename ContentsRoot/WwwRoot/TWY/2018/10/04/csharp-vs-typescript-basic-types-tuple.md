# C# vs. TypeScript: Basic Types, Tuple


# C# Tuple

* Keywords: `(`, `)`
* `System.Tuple` class  家族
  * 屬於 reference  種類
  * 固定 property 名稱（例如 `Item1`, `Item2` ）
  * Immutable

```CSharp
var t1 = System.Tuple.Create("It's over", 9000);
System.Console.WriteLine(t1.Item1);                                                 // prints `It's over`
System.Console.WriteLine(t1.Item2);                                                 // prints `9000`
// t1.Item1 = "foo";                                                                // error CS0200: Property or indexer 'Tuple<string, int>.Item1' cannot be assigned to -- it is read only

System.Tuple<string, decimal> t2 = new System.Tuple<string, decimal>("USD", 0.02m);
System.Console.WriteLine(t2.Item1);                                                 // prints `USD`
System.Console.WriteLine($"{t2.Item2:C}");                                          // prints `$0.02`
```

* `System.ValueTuple` struct  家族
  * 屬於 value  種類
  * 有語義的 field  名稱
  * Mutable

```CSharp
var t1 = ("It's over", 9000);
System.Console.WriteLine(t1.Item1);                     // prints `It's over`
System.Console.WriteLine(t1.Item2);                     // prints `9000`

var t2 = (name: "John", age: 18);
System.Console.WriteLine(t2.name);                      // prints `John`
System.Console.WriteLine(t2.age);                       // prints `18`

(string currency, decimal amount) t3 = ("USD", 0.02m);
System.Console.WriteLine(t3.currency);                  // prints `USD`
System.Console.WriteLine($"{t3.amount:C}");             // prints `$0.02`
t3.amount = decimal.Zero;
System.Console.WriteLine($"{t3.amount:C}");             // prints `$0.00`

string team = "Blue";
int score = 12;
var t4 = (team, score);
System.Console.WriteLine(t4.team);                      // (requires C# 7.1 or later) prints `Blue`
System.Console.WriteLine(t4.score);                     // (requires C# 7.1 or later) prints `12`

var t5 = (team: "Blue", score: 12);
System.Console.WriteLine(t4 == t5);                     // (requires C# 7.3 or later) prints `True`

(string, int) t6 = ("Blue", 12);
System.Console.WriteLine(t4 == t6);                     // (requires C# 7.3 or later) prints `True`
```


# TypeScript Tuple

* Keywords: `[`, `]`
* TypeScript tuple  *幾乎*  就像是固定長度的 array  。

```TypeScript
let t1: [string, number] = ["It's over", 9000];
console.log(t1["0"]);                           // prints `It's over`
console.log(t1["1"]);                           // prints `9000`
console.log(t1[0]);                             // prints `It's over`
console.log(t1[1]);                             // prints `9000`
console.log(t1.length);                         // prints `2`
console.log(t1);                                // prints `["It's over", 9000]`

// t[0] = 0;                                    // error TS2322: Type '0' is not assignable to type 'string'.
// t["0"] = 0;                                  // error TS2322: Type '0' is not assignable to type 'string'.
t1[0] = "The answer is";
t1["1"] = 42;
console.log(t1);                                // prints `["The answer is", 42]`

let t2: [string, number] = ["The answer is", 42];
console.log(t2);                                // prints `["The answer is", 42]`
console.log(t1 == t2);                          // prints `false`
console.log(t1 === t2);                         // prints `false`

// t[2] = "foo";                                // error TS2733: Index '2' is out-of-bounds in tuple of length 2.
t1.splice(2, 0, "foo");
console.log(t1.length);                         // prints `3`
console.log(t1);                                // prints `["The answer is", 42, "foo"]`

// t.length = 0;                                // error TS2322: Type '0' is not assignable to type '2'.
t1.splice(0, 3);
console.log(t1.length);                         // prints `0`
console.log(t1);                                // prints `[]`
```
