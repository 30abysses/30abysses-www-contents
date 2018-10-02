# C# vs. TypeScript: Basic Types, Boolean


# C# Boolean

* Keywords: `bool`, `true`, `false`
* No implicit or explicit conversions between `bool` and any other basic
  types.
* C# does provide a built-in `Convert` class with basic type conversion
  methods.  See
  [Casting and Type Conversions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
  for more information.

```CSharp
// No implicit conversions between `bool` and other basic types.
if (0)                  {} // error CS0029: Cannot implicitly convert type 'int' to 'bool'
if ("")                 {} // error CS0029: Cannot implicitly convert type 'string' to 'bool'
if (null)               {} // error CS0037: Cannot convert null to 'bool' because it is a non-nullable value type
if (float.NaN)          {} // error CS0029: Cannot implicitly convert type 'float' to 'bool'
if (double.NaN)         {} // error CS0029: Cannot implicitly convert type 'double' to 'bool'
if (decimal.Zero)       {} // error CS0029: Cannot implicitly convert type 'decimal' to 'bool'

// No explicit conversions between `bool` and other basic types.
if ((bool)0)            {} // error CS0030: Cannot convert type 'int' to 'bool'
if ((bool)"")           {} // error CS0030: Cannot convert type 'string' to 'bool'
if ((bool)null)         {} // error CS0037: Cannot convert null to 'bool' because it is a non-nullable value type
if ((bool)float.NaN)    {} // error CS0030: Cannot convert type 'float' to 'bool'
if ((bool)double.NaN)   {} // error CS0030: Cannot convert type 'double' to 'bool'
if ((bool)decimal.Zero) {} // error CS0030: Cannot convert type 'decimal' to 'bool'

// `System.Conver`: "Converts a base data type to another base data type."
// This statement prints `True`.
System.Console.WriteLine(true
    && (System.Convert.ToBoolean(default(int))      == false)
    && (System.Convert.ToBoolean(default(long))     == false)
    && (System.Convert.ToBoolean(default(float))    == false)
    && (System.Convert.ToBoolean(default(double))   == false)
    && (System.Convert.ToBoolean(default(decimal))  == false)
    && (System.Convert.ToBoolean(default(string))   == false)
    && (System.Convert.ToBoolean(default(object))   == false)
    && (System.Convert.ToBoolean(0)                 == false)
    && (System.Convert.ToBoolean(0L)                == false)
    && (System.Convert.ToBoolean(0f)                == false)
    && (System.Convert.ToBoolean(0d)                == false)
    && (System.Convert.ToBoolean(decimal.Zero)      == false)
    && (System.Convert.ToBoolean((string)null)      == false)
    && (System.Convert.ToBoolean(null)              == false)

    && (System.Convert.ToBoolean(1)                 == true)
    && (System.Convert.ToBoolean(float.NaN)         == true)
    && (System.Convert.ToBoolean(double.NaN)        == true)
    && (System.Convert.ToBoolean(decimal.One)       == true)
    // && (System.Convert.ToBoolean(new object())   == true)  // throws `System.InvalidCastException`: "Unable to cast object of type 'System.Object' to type 'System.IConvertible'."
    // && (System.Convert.ToBoolean(new object[0])  == true)  // throws `System.InvalidCastException`: "Unable to cast object of type 'System.Object[]' to type 'System.IConvertible'."

    // && (System.Convert.ToBoolean("")             == false) // throws `System.FormatException`: "String was not recognized as a valid Boolean."
    && (System.Convert.ToBoolean("true")            == true)
    && (System.Convert.ToBoolean("FALSE")           == false)
== true);
```

* C# compiler warns about potential misuses of `=` for `==`.

```CSharp
bool b;
if (b = true) {} // warning CS0665: Assignment in conditional expression is always constant; did you mean to use == instead of = ?
```


# TypeScript Boolean

* Keywords: `boolean`, `true`, `false`
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
if (0)                  {} // no error
if ("")                 {} // no error
if (NaN)                {} // no error
if ([])                 {} // no error
if ({})                 {} // no error
if (undefined)          {} // no error
if (null)               {} // no error
if (Boolean(0))         {} // no error
if (Boolean(""))        {} // no error
if (Boolean(NaN))       {} // no error
if (Boolean([]))        {} // no error
if (Boolean({}))        {} // no error
if (Boolean(undefined)) {} // no error
if (Boolean(null))      {} // no error
```

Also, expect the unexpected.

```TypeScript
// This statement prints `true`.
console.log((true
    && (Boolean(new Boolean(false))             === true)

    && (Boolean("")                             === false)
    && (Boolean(new String(""))                 === true)
    && (Boolean(new String("").valueOf())       === false)
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

    && (Boolean("0")                             === true)
    && (Boolean(new String("0"))                 === true)
    && (Boolean(new String("0").valueOf())       === true)
    && (Boolean(String(new String("0")))         === true)

    && (Boolean(NaN)                            === false)
    && (Boolean(new Number(NaN))                === true)
    && (Boolean(Number(new Number(NaN)))        === false)

    && (Boolean(Infinity)                       === true)

    && (Boolean([])                             === true)
    && (Boolean([0])                            === true)
    && (Boolean([1])                            === true)
    && (Boolean({})                             === true)

    && (("" == new String(""))                  === true)
    && (("" === new String(""))                 === false)
    && (("" === String(new String("")))         === true)
    && (("" === new String("").valueOf())       === true)

    && (("0" == String(0))                      === true)
    && (("0" === String(0))                     === true)
    && (("0" == new String(0))                  === true)
    && (("0" === new String(0))                 === false)
    && (("0" === String(new String(0)))         === true)
    && (("0" === new String(0).valueOf())       === true)

    && ((null == true)                          === false)
    && ((null === true)                         === false)
    && ((null == false)                         === false)
    && ((null === false)                        === false)
    && ((undefined == true)                     === false)
    && ((undefined === true)                    === false)
    && ((undefined == false)                    === false)
    && ((undefined === false)                   === false)
    && ((null == undefined)                     === true)
    && ((null === undefined)                    === false)
) === true);
```
