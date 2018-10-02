# C# vs. TypeScript: Basic Types, Array


# C# Array

# TypeScript Array

`[]`
`Array<>`

```TypeScript
const foo: string[] = [];

const foo:string[] = new Array(3).fill('');

// what's the full signature of `interface Array<T>`?
//The declaration of the 'Array' interface includes a property 'length' and a numeric index signature for the element type, along with other members:

interface Array<T> {  
    length: number;  
    [x: number]: T;  
    // Other members  
}

var a = [1, 2];                          // number[]  
var b = ["hello", true];                 // (string | boolean)[]  
var c: [number, string] = [3, "three"];  // [number, string]
When the output target is ECMAScript 3 or 5, array literals containing spread elements are rewritten to invocations of the concat method. For example, the assignments

var a = [2, 3, 4];  
var b = [0, 1, ...a, 5, 6];
are rewritten to

var a = [2, 3, 4];  
var b = [0, 1].concat(a, [5, 6]);


When union, intersection, function, or constructor types are used as array element types they must be enclosed in parentheses. For example:

(string | number)[]  
(() => string)[]
Alternatively, array types can be written using the 'Array<T>' notation. For example, the types above are equivalent to

Array<string | number>  
Array<() => string>
```

[3.3.2 Array Types](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md#332-array-types)
[3.8.4 Array Type Literals](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md#384-array-type-literals)
[4.6 Array Literals](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md#46-array-literals)

A type is said to be an array-like type if it is assignable (section 3.11.4) to the type any[].
[3.11.4 Assignment Compatibility](https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md#3114-assignment-compatibility)

