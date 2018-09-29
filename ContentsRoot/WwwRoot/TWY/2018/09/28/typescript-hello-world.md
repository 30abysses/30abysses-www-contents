# TypeScript "Hello, World!"

```TypeScript
console.log("Hello, World!");
```


# 專案設定

> https://www.typescriptlang.org/docs/handbook/tsconfig-json.html
>
> The presence of a tsconfig.json file in a directory indicates that the
> directory is the root of a TypeScript project.

可以用以下指令產生一份全新的 tsconfig.json:

```
tsc --init
```

以下 TypeScript 手冊章節解釋 tsconfig.json  技術層面的東西：

* [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
* [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
* [Project References](https://www.typescriptlang.org/docs/handbook/project-references.html)


## tsconfig.json schema

http://json.schemastore.org/tsconfig

這也可以在
https://schemastore.azurewebsites.net/schemas/json/tsconfig.json  取得（
參考 issue
[Add HTTPS support](https://github.com/SchemaStore/schemastore/issues/12) 
。）


# 除錯

在編譯 TypeScript 時啟動 `sourceMap`  選項， TypeScript 除錯模式在以下環
境裡就 *很奇妙地* 能正常使用：

* Visual Studio Code + Node.js
* Google Chrome


# 靜態分析

https://palantir.github.io/tslint/


# TypeScript  文件

https://www.typescriptlang.org/docs/home.html （也可從 Github 取得： 
https://github.com/Microsoft/TypeScript-Handbook  ）

TypeScript  言語規格書： 
https://github.com/Microsoft/TypeScript/blob/master/doc/spec.md
