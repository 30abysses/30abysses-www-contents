# C# vs. TypeScript: Basic Types


# Boolean


## C# Boolean

* Keywords: `bool`; `true`, `false`
* No conversion between `bool` and any other types.


## TypeScript Boolean

* Keywords: `boolean`; `true`, `false`
* Use `===` and `!==`.
* Use `==` and `!=` if and only if you know exactly what you are doing
  and why you are doing it.

Some implicit conversions supported in JavaScript may require explicit
conversions in TypeScript; for example:

```TypeScript
// This statement prints `true`.
console.log((true
    // && ((false == 0)        === true)    // rejected in TypeScript
    // && ((false === 0)       === false)   // rejected in TypeScript
    && ((false == Boolean(0))  === true)
    && ((false === Boolean(0)) === true)
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
* "The System.Numerics namespace contains numeric types that complement
  the numeric primitives"; for example, `BigInteger`.


## TypeScript Number

* Keywords: `number`; `NaN`
* `number` implements the
  [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754)
  [double-precision floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format).
* `number` can safely store integer values between
  `Number.MIN_SAFE_INTEGER` (2^53-1) and `Number.MAX_SAFE_INTEGER`
  (-2^53+1).
* `Number("")` is equivalent to `0`.
* As of 2018-09-29, `BigInt` is
  [still under reivew](https://github.com/tc39/proposal-bigint);
  however, it is already available in
  [Google Chrome](https://developers.google.com/web/updates/2018/05/bigint).


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


## TypeScript String

* Keywords: `string`, `$`, `"`, `'`, `` ` ``, `\`
* Immutable
* UTF-16 encoding
* Use `"` or `'` to mark the beginning and the end of string literals.
* [Template literals (Template strings) (`` ` ``) support](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
* [Long literal (`\`) support](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Long_literal_strings)
* [Distinction between string primitives and String objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Distinction_between_string_primitives_and_String_objects)


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
