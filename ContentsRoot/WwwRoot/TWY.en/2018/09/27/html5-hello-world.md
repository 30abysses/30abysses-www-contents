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


## Minimum HTML5 "Hello, World!"

```HTML
<!DOCTYPE html>
<title>Hello, World!</title>
```

The above is the syntactically minimum HTML5 "Hello, World!" according
to the [HTML 5.2 specification][1], section
[8.1. Writing HTML documents](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#writing-html-documents):

> Documents must consist of the following parts, in the given order:
> 1. Optionally, a single U+FEFF BYTE ORDER MARK (BOM) character.
> 2. Any number of comments and space characters.
> 3. A `DOCTYPE`.
> 4. Any number of comments and space characters.
> 5. The document element, in the form of an `html` element.
> 6. Any number of comments and space characters.

In addition, as described in section
[8.1.2.4. Optional tags](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#optional-tags),
elements like `html`, `head`, `body` can be omitted under specific
conditions (while the `title` element cannot.)

Therefore, although it may look unorthodox, the minimum HTML5
"Hello, World!" demo above actually conforms to the HTML 5.2
specification.


## Minimum HTML5 "Hello, World!" accepted by web browsers.

Web browsers (and the rendering engines they use) may accept invalid
HTML inputs.  For example, Google Chrome 69.0.3497.100 accepts the
following input:

```HTML
Hello, World!
```

and interprets it as the following:

```HTML
<html><head></head><body>Hello, World!</body></html>
```

Error tolerance and handling mechanisms are further discussed in:

* "How Browsers Work: Behind the scenes of modern web browsers", section
  [3.2.9 Browser error tolerance](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/#Browsers_error_tolerance)
* HTML5 specification, section
  [8.2.8. An introduction to error handling and strange cases in the parser](https://www.w3.org/TR/2017/REC-html52-20171214/syntax.html#an-introduction-to-error-handling-and-strange-cases-in-the-parser)


# W3C HTML specification

https://www.w3.org/TR/html/ (as of 2018-09-27, it automatically
redirects to [HTML 5.2][1].)


# HTML validation

The [Nu Html Checker](https://validator.github.io/)


[1]: https://www.w3.org/TR/2017/REC-html52-20171214/
