# C# vs. TypeScript: Basic Types, Number


# C# Number

* 關鍵字： `sbyte`, `byte`, `char`, `short`, `ushort`, `int`, `uint`,
  `long`, `ulong`, `float`, `double`, `decimal`, `l`, `L`, `f`, `F`,
  `d`, `D`, `m`, `M`
* [System.Numerics](https://docs.microsoft.com/en-us/dotnet/api/system.numerics?view=netcore-2.1) 
  此 namespace  下有多種補完 numeric primitives 的工具；例如： 
  [the `BigInteger` struct](https://docs.microsoft.com/en-us/dotnet/api/system.numerics.biginteger?view=netcore-2.1).
* C#  支援
  [overloadable operators](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators).


# TypeScript Number

* 關鍵字： `number`, `NaN`, `Infinity`
* `number`  遵從 
  [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754)
  [double-precision floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format) 
  規格。
* `number`  可以正常儲存以下範圍內的整數： 
  `Number.MIN_SAFE_INTEGER` (2^53-1) and `Number.MAX_SAFE_INTEGER`
  -(2^53-1).
* `Number("")`  等同於 `0`  。
* 在 2018-09-29 ， `BigInt` 規格書仍在審核中
  ( https://github.com/tc39/proposal-bigint ) ；但在 
  [Google Chrome 67](https://developers.google.com/web/updates/2018/05/bigint) 
  及其之後的版本裡已可開始使用。
