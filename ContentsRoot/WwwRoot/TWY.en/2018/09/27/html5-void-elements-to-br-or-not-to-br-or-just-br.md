# HTML5 void elements: to `<br/>`, or not to `<br />`, or just `<br>`?

The question: how to write
[the `br` element](https://www.w3.org/TR/2017/REC-html52-20171214/textlevel-semantics.html#the-br-element)?

The top contenders are:

```HTML
<br>
<br/>
<br />
```

Syntactically speaking, they all conform to the
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
[8.1.2. Elements](https://www.w3.org/TR/html5/syntax.html#writing-html-documents-elements)
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

Therefore, it comes down to HTML5 authors' preferences


# XHTML empty elements

The
[XHTML 1.0 specification](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/)
imposes a different rule.  In section
[4.6. Empty Elements](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#h-4.6),
it states:

> Empty elements must either have an end tag or the start tag must end
> with />. For instance, `<br/>` or `<hr></hr>`.

In addition, XHTML 1.0 specification's section
[C. HTML Compatibility Guidelines](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#guidelines)
suggests:

> This appendix is informative.
>
> This appendix summarizes design guidelines for authors who wish their
> XHTML documents to render on existing HTML user agents. Note that this
> recommendation does not define how HTML conforming user agents should
> process HTML documents. Nor does it define the meaning of the Internet
> Media Type `text/html`. For these definitions, see
> [HTML4](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#ref-html4)
> and
> [RFC2854](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#ref-rfc2854)
> respectively.

> C.2. Empty Elements
>
> Include a space before the trailing / and > of empty elements, e.g.
> `<br />`, `<hr />` and `<img src="karen.jpg" alt="Karen" />`. Also,
> use the minimized tag syntax for empty elements, e.g. `<br />`, as the
> alternative syntax `<br></br>` allowed by XML gives uncertain results
> in many existing user agents.

> C.3. Element Minimization and Empty Element Content
>
> Given an empty instance of an element whose content model is not EMPTY
> (for example, an empty title or paragraph) do not use the minimized
> form (e.g. use `<p> </p>` and not `<p />`).

Therefore, in XHTML, empty elements like `br` must have an end tag or be
self-closing; and for compatibility reasons, it is suggested to include
a space character before the trailing `/>`.
