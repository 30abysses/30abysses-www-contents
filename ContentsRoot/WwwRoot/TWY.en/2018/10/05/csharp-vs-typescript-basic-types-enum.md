# C# vs. TypeScript: Basic Types, Enum


# C# Enum

* Keyword: `enum`
* C# enum underlying types can be: `byte`, `sbyte`, `short`, `ushort`,
  `int`, `uint`, `long`, `ulong`.
* The `System.Enum` class is the base class for all C# enums and provide
  enum operation methods.
* C# enums can support bit flag operations.

```CSharp
enum E1
{
    A,
    B = 1,
    C = 2,

}

E1 e = E1.B;
System.Console.WriteLine(e);                                                            // prints `B`
e = (E1)0;
System.Console.WriteLine(e);                                                            // prints `A`
e = E1.B | E1.C;
System.Console.WriteLine(e);                                                            // prints `3`

[System.Flags]
enum E2
{
    None = 0,
    Readable = 0b0001,
    Writable = 0b0010,
    Deletable = 0b0100,
}

E2 p = E2.Readable | E2.Writable;
System.Console.WriteLine(p);                                                            // prints `Readable, Writable`
System.Console.WriteLine(p.HasFlag(E2.Readable));                                       // prints `True`
System.Console.WriteLine(p.HasFlag(E2.Deletable));                                      // prints `False`
p = (E2)0b0111;
System.Console.WriteLine(p);                                                            // prints `Readable, Writable, Deletable`
p ^= E2.Readable;
System.Console.WriteLine(p);                                                            // prints `Writable, Deletable`

System.Console.WriteLine($"[{string.Join(", ", System.Enum.GetNames(typeof(E2)))}]");   // prints `[None, Readable, Writable, Deletable]`
```


# TypeScript Enum

* Keyword: `enum`
* TypeScript enum members can be `number` or `string`.
* TypeScript enum declarations (of the same types) are merged.
* TypeScript enums can be declared to be `const` so they are inlined in
  the compiled JavaScript.

```TypeScript
enum E1 {
    A,
    B = 3.14,
    C = 1 << 2,
    D = 1 << 3,
}

let e: E1 = E1.A;
console.log(e);                 // prints `0`
console.log(E1[e]);             // prints `A`

e = 3.14;
console.log(e);                 // prints `3.14`
console.log(E1[e]);             // prints `B`

console.log(E1[8]);             // prints `D`

e = E1.C | E1.D;
console.log(e);                 // prints `12`
console.log(E1[e]);             // prints `undefined`

enum E1 {
    E = 1 << 4,
    F = D | E
}

e = E1.D | E1.E;
console.log(e);                 // prints `24`
console.log(E1[e]);             // prints `F`

enum E2 {
    Good = "Situation Normal",
    Bad = "All Fucked Up"
}

let m: E2 = E2.Good;
console.log(m);                 // prints `Situation Normal`
// console.log(E2[m]);          // error TS7015: Element implicitly has an 'any' type because index expression is not of type 'number'.
// console.log(E2["foo"]);      // error TS7015: Element implicitly has an 'any' type because index expression is not of type 'number'.
```
