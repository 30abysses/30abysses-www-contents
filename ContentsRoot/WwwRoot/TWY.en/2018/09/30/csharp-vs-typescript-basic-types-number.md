# C# vs. TypeScript: Basic Types, Number


# C# Number

* Keywords: `sbyte`, `byte`, `char`, `short`, `ushort`, `int`, `uint`,
  `long`, `ulong`, `float`, `double`, `decimal`
* "The
  [System.Numerics](https://docs.microsoft.com/en-us/dotnet/api/system.numerics?view=netcore-2.1)
  namespace contains numeric types that complement the numeric
  primitives"; for example,
  [the `BigInteger` struct](https://docs.microsoft.com/en-us/dotnet/api/system.numerics.biginteger?view=netcore-2.1).


# TypeScript Number

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
