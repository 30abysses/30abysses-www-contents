# HTML5 void elements: to `<br/>`, or not to `<br />`, or just `<br>`?

The question: how to write
[the `br` element](https://www.w3.org/TR/2017/REC-html52-20171214/textlevel-semantics.html#the-br-element)?

The top contenders are:

```HTML
<br>
<br/>
<br />
```

Syntactically speaking, they all conforms to the
[HTML 5.2 specification](https://www.w3.org/TR/2017/REC-html52-20171214/)
as section
[8.1.2.1. Start tags](https://www.w3.org/TR/html5/syntax.html#start-tags)
states:

> Start tags must have the following format:
> 1. The first character of a start tag must be a U+003C LESS-THAN SIGN
>    character (<).
> 2. The next few characters of a start tag must be the element’s tag
>    name.
> 3. If there are to be any attributes in the next step, there must
>    first be one or more space characters.
> 4. Then, the start tag may have a number of attributes, the syntax for
>    which is described below. Attributes must be separated from each
>    other by one or more space characters.
> 5. After the attributes, or after the tag name if there are no
>    attributes, there may be one or more space characters. (Some
>    attributes are required to be followed by a space. See §8.1.2.3
>    Attributes below.)
> 6. Then, if the element is one of the void elements, or if the element
>    is a foreign element, then there may be a single U+002F SOLIDUS
>    character (/). This character has no effect on void elements, but
>    on foreign elements it marks the start tag as self-closing.
> 7. Finally, start tags must be closed by a U+003E GREATER-THAN SIGN
>    character (>).

And section
[8.1.2. Elements](https://www.w3.org/TR/html5/syntax.html#writing-html-documents-elements),
lists `br` as one of the
[void elements](https://www.w3.org/TR/html5/syntax.html#void-elements):

* `area`
* `base`
* `br`
* `col`
* `embed`
* `hr`
* `img`
* `input`
* `link`
* `meta`
* `param`
* `source`
* `track`
* `wbr`

> Void elements only have a start tag; end tags must not be specified
> for void elements.
>
> Void elements can’t have any contents (since there’s no end tag, no
> content can be put between the start tag and the end tag).

Therefore, it comes down to HTML5 authors' preferences.
