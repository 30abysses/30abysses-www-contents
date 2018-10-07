# C# vs. TypeScript: Basic Types, Object


# C# Object

* 關鍵字： `object`
* C# `object` 是 `System.Object`  的別名；所有的 C# type  都直接或間接繼
  承 `System.Object`  。
* C# `System.ValueType` 繼承 `System.Object`  且被所有 value type 繼承。
* 參考 
  [Boxing and Unboxing](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/boxing-and-unboxing) 
  以取得更多關於 value type 與 reference type 之間轉換的資訊。


# TypeScript Object

* 關鍵字： `object`, `{`, `}`
* TypeScript `object` 代表非 `boolean`, `number`, `string`, `symbol`  的
  數值；例如： array, tuple, function 。
