# HTML5 charset: `utf-8`  的寫法

題目：「在設定 HTML5 charset  時，該如何寫 `utf-8`  ？」

其變形包括：

```
utf-8
UTF-8
utf8
UTF8
```

答案： `utf-8`  ；下面是如何從 W3C  的文件裡得到答案：

1. HTML 5.2 specification, section
   [2.6.5. Extracting character encodings from meta elements](https://www.w3.org/TR/2017/REC-html52-20171214/infrastructure.html#extracting-character-encodings-from-meta-elements)
2. HTML 5.2 specification, section
   [4.2.5. The meta element](https://www.w3.org/TR/2017/REC-html52-20171214/document-metadata.html#the-meta-element)
3. HTML 5.2 specification,
   [Character encoding declaration](https://www.w3.org/TR/2017/REC-html52-20171214/document-metadata.html#character-encoding-declaration)
4. HTML 5.2 specification,
   [Character encoding](https://www.w3.org/TR/2017/REC-html52-20171214/infrastructure.html#character-encoding)
5. [Encoding](https://www.w3.org/TR/2018/CR-encoding-20180327/)
6. Encoding, section
   [4.2. Names and labels](https://www.w3.org/TR/encoding/#names-and-labels)

> Authors must use the UTF-8 encoding and must use the ASCII
> case-insensitive "utf-8" label to identify it.
>
> New protocols and formats, as well as existing formats deployed in new
> contexts, must use the UTF-8 encoding exclusively. If these protocols
> and formats need to expose the encoding’s name or label, they must
> expose it as "utf-8".
