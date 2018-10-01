# C# vs. TypeScript: Basic Types, String


# C# String

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
System.Console.WriteLine(@"C:\Users" + "\\Public");     // prints `C:\Users\Public`
decimal twoCents = 0.02m;
System.Console.WriteLine($"This is my {twoCents:C}.");  // prints `This is my $0.02.`
```


# TypeScript String

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
