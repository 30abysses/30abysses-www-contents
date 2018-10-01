# C# vs. TypeScript: Basic Types


# Boolean


## C# Boolean

* Keywords: `bool`; `true`, `false`
* No conversion between `bool` and any other types.

```CSharp
int i = 0;
if (i) {}               // error CS0029: Cannot implicitly convert type 'int' to 'bool'
if (0) {}               // error CS0029: Cannot implicitly convert type 'int' to 'bool'

string s = "";
if (s) {}               // error CS0029: Cannot implicitly convert type 'string' to 'bool'
if ("") {}              // error CS0029: Cannot implicitly convert type 'string' to 'bool'

object o = null;
if (o) {}               // error CS0266: Cannot implicitly convert type 'object' to 'bool'. An explicit conversion exists (are you missing a cast?)
if (null) {}            // error CS0037: Cannot convert null to 'bool' because it is a non-nullable value type

float f = float.NaN;
if (f) {}               // error CS0029: Cannot implicitly convert type 'float' to 'bool'
if (float.NaN) {}       // error CS0029: Cannot implicitly convert type 'float' to 'bool'

double d = double.NaN;
if (d) {}               // error CS0029: Cannot implicitly convert type 'double' to 'bool'
if (double.NaN) {}      // error CS0029: Cannot implicitly convert type 'double' to 'bool'
```

* C# compiler warns about potential misuses of `=` for `==`.

```CSharp
bool b;
if (b = true) {} // warning CS0665: Assignment in conditional expression is always constant; did you mean to use == instead of = ?
if (false)    {} // no warning
```


## TypeScript Boolean

* Keywords: `boolean`; `true`, `false`
* Use `===` and `!==`.
* Use `==` and `!=` if and only if you know exactly what you are doing
  and why you are doing it.

Some implicit conversions supported in JavaScript may require explicit
conversions in TypeScript; for example:

```TypeScript
if (0         ==  true) {} // error TS2367: This condition will always return 'false' since the types '0' and 'true' have no overlap.
if (0         === true) {} // error TS2367: This condition will always return 'false' since the types '0' and 'true' have no overlap.
if (1         ==  true) {} // error TS2367: This condition will always return 'false' since the types '1' and 'true' have no overlap.
if (1         === true) {} // error TS2367: This condition will always return 'false' since the types '1' and 'true' have no overlap.
if (""        ==  true) {} // error TS2367: This condition will always return 'false' since the types '""' and 'true' have no overlap.
if (""        === true) {} // error TS2367: This condition will always return 'false' since the types '""' and 'true' have no overlap.
if (NaN       ==  true) {} // error TS2367: This condition will always return 'false' since the types 'number' and 'boolean' have no overlap.
if (NaN       === true) {} // error TS2367: This condition will always return 'false' since the types 'number' and 'boolean' have no overlap.
if (0         ==  "0")  {} // error TS2367: This condition will always return 'false' since the types '0' and '"0"' have no overlap.
if (0         === "0")  {} // error TS2367: This condition will always return 'false' since the types '0' and '"0"' have no overlap.
if ([]        ==  true) {} // error TS2367: This condition will always return 'false' since the types 'never[]' and 'boolean' have no overlap.
if ([]        === true) {} // error TS2367: This condition will always return 'false' since the types 'never[]' and 'boolean' have no overlap.
if ([0]       ==  true) {} // error TS2367: This condition will always return 'false' since the types 'number[]' and 'boolean' have no overlap.
if ([0]       === true) {} // error TS2367: This condition will always return 'false' since the types 'number[]' and 'boolean' have no overlap.
if ({}        ==  true) {} // error TS2367: This condition will always return 'false' since the types '{}' and 'boolean' have no overlap.
if ({}        === true) {} // error TS2367: This condition will always return 'false' since the types '{}' and 'boolean' have no overlap.
if (undefined ==  true) {} // no error
if (undefined === true) {} // no error
if (null      ==  true) {} // no error
if (null      === true) {} // no error

// This statement prints `true`.
console.log((true
    && ((Boolean(0) ==  false)  === true)
    && ((Boolean(0) === false)  === true)
) === true);
```

Also, expect the unexpected.

```TypeScript
// This statement prints `true`.
console.log((true
    && (Boolean(new Boolean(false))             === true)

    && (Boolean("")                             === false)
    && (Boolean(new String(""))                 === true)
    && (Boolean(String(new String("")))         === false)

    && (Boolean(null)                           === false)
    && (Boolean(new Object(null))               === true)
    && (Boolean(Object(new Object(null)))       === true)

    && (Boolean(undefined)                      === false)
    && (Boolean(new Object(undefined))          === true)
    && (Boolean(Object(new Object(undefined)))  === true)

    && (Boolean(0)                              === false)
    && (Boolean(new Number(0))                  === true)
    && (Boolean(Number(new Number(0)))          === false)

    && (Boolean(-0)                             === false)
    && (Boolean(new Number(-0))                 === true)
    && (Boolean(Number(new Number(-0)))         === false)

    && (Boolean(NaN)                            === false)
    && (Boolean(new Number(NaN))                === true)
    && (Boolean(Number(new Number(NaN)))        === false)

    && (Boolean([])                             === true)
    && (Boolean([0])                            === true)
    && (Boolean([1])                            === true)
    && (Boolean({})                             === true)

    && (("" == new String(""))                  === true)
    && (("" === new String(""))                 === false)
    && (("" === String(new String("")))         === true)
    && (("" === new String("").valueOf())       === true)

    && (("0" == String(0))                      === true)
    && (("0" == new String(0))                  === true)
    && (("0" === String(0))                     === true)
    && (("0" === new String(0))                 === false)
    && (("0" === String(new String(0)))         === true)
    && (("0" === new String(0).valueOf())       === true)

    && ((undefined == false)                    === false)
    && ((null == false)                         === false)
    && ((null == undefined)                     === true)
    && ((null === undefined)                    === false)

    && ((NaN == NaN)                            === false)
    && ((NaN === NaN)                           === false)
) === true);
```


# Number


## C# Number

* Keywords: `sbyte`, `byte`, `char`, `short`, `ushort`, `int`, `uint`,
  `long`, `ulong`, `float`, `double`, `decimal`
* "The
  [System.Numerics](https://docs.microsoft.com/en-us/dotnet/api/system.numerics?view=netcore-2.1)
  namespace contains numeric types that complement the numeric
  primitives"; for example,
  [the `BigInteger` struct](https://docs.microsoft.com/en-us/dotnet/api/system.numerics.biginteger?view=netcore-2.1).


## TypeScript Number

* Keywords: `number`; `NaN`
* `number` implements the
  [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754)
  [double-precision floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format).
* `number` can safely store integer values between
  `Number.MIN_SAFE_INTEGER` (2^53-1) and `Number.MAX_SAFE_INTEGER`
  -(2^53-1).
* `Number("")` is equivalent to `0`.
* As of 2018-09-29, `BigInt` is
  [still under reivew](https://github.com/tc39/proposal-bigint);
  however, it was already made available in
  [Google Chrome 67](https://developers.google.com/web/updates/2018/05/bigint).


# String


## C# String

* Keywords: `string`, `@`, `$`, `"`
* Immutable; use `System.Text.StringBuilder` when frequent modification
  is necessary.
* UTF-16 encoding
* Use `"` to mark the beginning and the end of string literals.
* [Verbatim (`@`) support](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/verbatim)
* [String interpolation (`$`) support](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated)
* [Formatting Types in .NET](https://docs.microsoft.com/en-us/dotnet/standard/base-types/formatting-types)
  * [Formatting numeric results table](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/formatting-numeric-results-table)

```CSharp
string world = "World";
System.Console.WriteLine($"Hello, {world}!");           // prints `Hello, World!`
System.Console.WriteLine(@"C:\Windows");                // prints `C:\Windows`
decimal twoCents = 0.02m;
System.Console.WriteLine($"This is my {twoCents:C}.");  // prints `This is my $0.02.`
```

## TypeScript String

* Keywords: `string`, `$`, `"`, `'`, `` ` ``, `\`
* Immutable
* UTF-16 encoding
* Use `"` or `'` to mark the beginning and the end of string literals.
* [Template literals (Template strings) (`` ` ``) support](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
* [Long literal (`\`) support](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Long_literal_strings)
* [Distinction between string primitives and String objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Distinction_between_string_primitives_and_String_objects)

```TypeScript
let hello: string = "Hello";
let world: string = 'World';
console.log(`${hello}, ${world}!`); // prints `Hello, World!`
```

---
# Array
# Tuple
# Enum
# Any
# Void
# Null
# Undefined
# Never
# Object
---
# Type assertion
# Type casting
