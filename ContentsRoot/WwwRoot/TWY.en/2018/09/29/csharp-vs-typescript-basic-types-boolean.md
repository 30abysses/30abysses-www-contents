# C# vs. TypeScript: Basic Types, Boolean


# C# Boolean

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


# TypeScript Boolean

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
