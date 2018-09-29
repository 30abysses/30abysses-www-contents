# TypeScript "Hello, World!"

```TypeScript
console.log("Hello, World!");
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


# Debugging

Enable the `sourceMap` option when compiling TypeScript source code.
Then debugging TypeScript *just works automagically* in the following
environments:

* Visual Studio Code + Node.js
* Google Chrome


# Static analysis

https://palantir.github.io/tslint/


# TypeScript documentation

https://www.typescriptlang.org/docs/home.html (also available on Github:
https://github.com/Microsoft/TypeScript-Handbook )

TypeScript language specification:
https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md
