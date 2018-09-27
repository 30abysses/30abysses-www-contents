# HTML5 "Hello, World!"

```HTML
<!DOCTYPE html>
<html lang="en-US">
    <head>
        <meta charset="utf-8">
        <title>Hello, World!</title>
    </head>
    <body></body>
</html>
```


## 最短的 HTML5 "Hello, World!"

```HTML
<!DOCTYPE html>
<title>Hello, World!</title>
```

上面是語法上最短的 HTML5 "Hello, World!"  。

根據 [HTML 5.2  規格][1]的 
[8.1. Writing HTML documents](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#writing-html-documents) 
章節：

> Documents must consist of the following parts, in the given order:
> 1. Optionally, a single U+FEFF BYTE ORDER MARK (BOM) character.
> 2. Any number of comments and space characters.
> 3. A `DOCTYPE`.
> 4. Any number of comments and space characters.
> 5. The document element, in the form of an `html` element.
> 6. Any number of comments and space characters.

且，如 
[8.1.2.4. Optional tags](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#optional-tags) 
章節所述，在特定條件下 `html`, `head`, `body` 這些成員可以省略（但
 `title`  不可以。）

是故，雖然看起來是非正統的寫法，但上面的最短 HTML5 "Hello, World!"  事實
上是符合 HTML 5.2 規格的。


## 被網頁瀏覽器所接受的最短 HTML5 "Hello, World!"

網頁瀏覽器（及其使用的繪製引擎）可能可以接受不正確的 HTML 輸入資料。例如
， Google Chrome 69.0.3497.100 就能接受以下輸入：

```HTML
Hello, World!
```

並以以下的方式解讀之：

```HTML
<html><head></head><body>Hello, World!</body></html>
```

對錯誤容忍、處理機制更進一步的討論：

* "How Browsers Work: Behind the scenes of modern web browsers", section
[3.2.9 Browser error tolerance](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/#Browsers_error_tolerance)
* HTML5 specification, section [8.2.8. An introduction to error handling and strange cases in the parser](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#an-introduction-to-error-handling-and-strange-cases-in-the-parser)


# W3C HTML  規格

https://www.w3.org/TR/html/ （在今日 2018-09-27,  這連結會自動導向 
[HTML 5.2][1] 。）


## HTML 驗證

The [Nu Html Checker](https://validator.github.io/)


[1]: https://www.w3.org/TR/2017/REC-html52-20171214/
