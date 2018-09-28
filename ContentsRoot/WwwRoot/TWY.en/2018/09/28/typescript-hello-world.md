# TypeScript "Hello, World!"

```TypeScript
console.log("Hello, World!");
```


## C#-style TypeScript "Hello, World!"

```TypeScript
namespace HelloWorld {
    export class Program {
        static main(): void {
            console.log("Hello, World!")
        }
    }
}

HelloWorld.Program.main();
```


# Project configuration

> https://www.typescriptlang.org/docs/handbook/tsconfig-json.html
>
> The presence of a tsconfig.json file in a directory indicates that the
> directory is the root of a TypeScript project.

A fresh copy of tsconfig.json can be generated with this command:

```
tsc --init
```

The following TypeScript handbook sections further explain the technical
aspects of tsconfig.json:

* [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
* [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
* [Project References](https://www.typescriptlang.org/docs/handbook/project-references.html)


## tsconfig.json schema

http://json.schemastore.org/tsconfig

It is also available at
https://schemastore.azurewebsites.net/schemas/json/tsconfig.json (see
issue
[Add HTTPS support](https://github.com/SchemaStore/schemastore/issues/12)
for more information.)


# TypeScript documentation

https://www.typescriptlang.org/docs/home.html


## TypeScript language specification

https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md
