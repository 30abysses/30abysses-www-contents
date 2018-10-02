# HTML5 void elements: `<br/>`, `<br />`, 還是  `<br>`  ？

題目：「該如何使用 HTML5  的 
[`br` 成員](https://www.w3.org/TR/2017/REC-html52-20171214/textlevel-semantics.html#the-br-element)
？」

前幾名的候選答案是：

```HTML
<br>
<br/>
<br />
```

就語法上來說，那些候選答案都符合 
[HTML 5.2 規格](https://www.w3.org/TR/2017/REC-html52-20171214/)；如第 
[8.1.2.1. Start tags](https://www.w3.org/TR/html5/syntax.html#start-tags)
章節所述：

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

而第 
[8.1.2. Elements](https://www.w3.org/TR/html5/syntax.html#writing-html-documents-elements)
章節將 `br` 列為 
[void elements](https://www.w3.org/TR/html5/syntax.html#void-elements)之
一：

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

是故，這題目最後取決於 HTML5  寫作者的個人偏好。


# XHTML empty elements

[XHTML 1.0 規格書](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/)制定
了不同的規則。章節 
[4.6. Empty Elements](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#h-4.6) 
說明了：

> Empty elements must either have an end tag or the start tag must end
> with />. For instance, `<br/>` or `<hr></hr>`.

且， XHTML 1.0  規格書的 
[C. HTML Compatibility Guidelines](https://www.w3.org/TR/2018/SPSD-xhtml1-20180327/#guidelines) 
章節建議：

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

是故，在 XHTML  中， `br` 這類的 empty element  必須要有 end tag  或是 
self-closing  ；並且，因為相容性的原因，最好在 self-closing 的結尾 `/>` 
前加入空白字元。
