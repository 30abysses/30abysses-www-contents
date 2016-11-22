> http://www.30abysses.com/TWY/2016/11/21/c_sharp-gethashcode.md
> by TW Yang <twy@30abysses.com> 2016-11-21 CC-BY-4.0

# C# GetHashCode()

[`GetHashCode()`][1]  這個方法(method)有著《魔偶馬戲團》中
「[四大元老][2]」 （[最古の四人][3]） 的地位，直屬 [`System.Object`][4]
類別(class) ，棲身於 `mscorlib` 此組件(assembly)中。

網路上是可以找到些關於 `GetHashCode()`  的零碎討論，但這篇文章將從最有
權威性(authoritative) 的資料來源重新出發，再逐步探討細節。

[1]: https://msdn.microsoft.com/en-us/library/system.object.gethashcode.aspx
[2]: https://zh.wikipedia.org/zh-tw/%E5%82%80%E5%84%A1%E9%A6%AC%E6%88%B2%E5%9C%98%E8%A7%92%E8%89%B2%E5%88%97%E8%A1%A8#.E5.9B.9B.E5.A4.A7.E5.85.83.E8.80.81
[3]: https://ja.wikipedia.org/wiki/%E3%81%8B%E3%82%89%E3%81%8F%E3%82%8A%E3%82%B5%E3%83%BC%E3%82%AB%E3%82%B9%E3%81%AE%E7%99%BB%E5%A0%B4%E4%BA%BA%E7%89%A9#.E6.9C.80.E5.8F.A4.E3.81.AE.E5.9B.9B.E4.BA.BA.EF.BC.88.E3.83.AC.E3.83.BB.E3.82.AD.E3.83.A3.E3.83.88.E3.83.AB.E3.83.BB.E3.83.94.E3.82.AA.E3.83.8D.E3.83.BC.E3.83.AB.EF.BC.89
[4]: https://msdn.microsoft.com/en-us/library/system.object.aspx


##  資料來源

* [MSDN `GetHashCode()`  官方文件][1] （[官方機器翻譯版本][5]）
* [`coreclr` 原始碼(source code)][6]
* "[Guidelines and rules for GetHashCode][7]" by _le_ **Eric Lippert**

[5]: https://msdn.microsoft.com/zh-tw/library/system.object.gethashcode.aspx
[6]: https://github.com/dotnet/coreclr
[7]: https://blogs.msdn.microsoft.com/ericlippert/2011/02/28/guidelines-and-rules-for-gethashcode/

微軟(Microsoft)除了開源 `.NET Core` ，目前也有釋出其他版本的
`.NET Framework`  參考用原始碼如下。

* https://github.com/Microsoft/referencesource/
* https://referencesource.microsoft.com/

經過大略的比對後，就 `GetHashCode()`  看起來是幾乎完全相同的；在此以
`coreclr` 版本為主。



# `GetHashCode()` 簡單來說就是……

在試著理解 `GetHashCode()`  的功能前，得先理解它要解決的問題：

> 比較兩個物件(object)是否「相同」

更完整的說法是：

> 有一物件甲，有一物件乙，試問：「甲、乙是否『相同』？」

所謂「相同」在此是個很抽象的觀念，在不同的場合有不同的解釋。

例如，假設甲、乙是「書」，那麼通常來說，如果它們的
[國際標準書號][8]([ISBN][9])相同，那我們就可以說甲、乙是兩本書是
「相同的書」。相對的，如果甲、乙這兩本書的國際標準書號不同，我們就會說甲
、乙是「不同的書」。

[8]: https://zh.wikipedia.org/zh-tw/%E5%9C%8B%E9%9A%9B%E6%A8%99%E6%BA%96%E6%9B%B8%E8%99%9F
[9]: https://en.wikipedia.org/wiki/International_Standard_Book_Number

然而，視場合不同，對「相同」在定義上嚴謹度的要求也不同；例如，就算甲、乙
兩本書有一樣的國際標準書號，其內容仍有可能相異（書有可能缺頁、被塗改）。
如果是在鑑定書籍，那就可能要逐字逐頁考證；可以想像，那將是很費功夫的事。

易言之：

* 如果兩本書的國際標準書號不同，那幾乎可以 100% 安全地決定「完全不需要花
  功夫去逐字逐頁比對」。
* 如果兩本書的國際標準書號相同，那就必須進一步考量「是否需要花功夫去逐字
  逐頁比對」。

再進一步說：

* 即使兩本書的國際標準書號相同，最後比對的結果仍可能發現這兩本書並不
  100%  相同（缺頁、被塗改）。

反過來說：

* 兩本事實上並不 100% 相同的書（缺頁、被塗改），仍有可能有相同的國際標準
  書號。


##  所以說，那個醬汁^H^H `GetHashCode()`  就是……

在 C# 程式的領域中， `GetHashCode()`  的作用就像上述例子中的
「國際標準書號」，提供一個快速篩選物件的作法；從其簽章(signature)

```
    public virtual int GetHashCode()
```

可以看出，它的設計是傳回一個 `int`  來代表該物件；而 `int`  的好處之一，
就是可以快速簡單地比較出異同。

易言之，與上述的「書、國際標準書號」的例子對應起來，就會是這個樣子：

* 如果兩個物件由 `GetHashCode()`  傳回值不同，那就不需要進一步比對。
* 如果兩個物件由 `GetHashCode()`  傳回值相同，那就有需要進一步比對。
* 即使兩個物件由 `GetHashCode()`  傳回值相同，最後比對的結果仍可能發現這
  兩個物件並不 100% 相同。
* 兩個事實上不 100% 相同的物件，其 `GetHashCode()`  傳回值仍有可能相同。

對應到[官方文件][1] 的話，就是這段：

> Two objects that are equal return hash codes that are equal. However,
> the reverse is not true: equal hash codes do not imply object
> equality, because different (unequal) objects can have identical hash
> codes.

[官方機器翻譯][5] ：

> 等於傳回雜湊程式碼是相等的兩個物件。 不過，反向並不成立︰ 相等的雜湊程
> 式碼不一定代表物件是否相等，因為不同 （相等） 的物件可以有相同的雜湊碼
> 。

我的手動釋譯：

> 相同的物件傳回相同的雜湊(hash)值。然而，這不代表「傳回相同雜湊值的都是
> 相同的物件」；因為相異的物件仍可能傳回相同的雜湊值。

用邏輯來說就是無法從「Ｐ→Ｑ」得出「Ｑ→Ｐ」；也就是 **無法** 從

> Ｐ(相同物件) → Ｑ(傳回相同雜湊值)

得到

> Ｑ(傳回相同雜湊值) → Ｐ(相同物件)


## `GetHashCode()`  如何知道該怎麼判斷／計算其傳回值？

簡單地說：「施主，這個問題你應該要問你自己。」

`GetHashCode()` 只有定義其傳回值的規則，真正的實作是取決於使用
`GetHashCode()` 這個架構的人。反過來說，製定 `GetHashCode()`  架構的人無
法事先預知在各種不同場合中對各種不同物件種類判定異同的規則，是故，他只能
在抽象層面上定義傳回值代表的意義以及說明 .NET Framework 會如何使用
`GetHashCode()` 的傳回值。

通常來說，除非你遇到要處理相等性(equality)及其沿生出的東西，例如
`Dictionary`, `HashSet`, `Hashtable`, **`LINQ`**, 不然，通常來說並不用特
別煩惱 `GetHashCode()`  的問題；常用的基本資料型態，例如 `int`,
`string`, `double`, 等等，都已有內建的 `GetHashCode()`  ，應該能應付一般
的使用情形。


##  為什麼「相異的物件仍可能傳回相同的雜湊值」？

簡單地說，[鴿巢原理][10]([Pigeonhole principle][11])。

[10]: https://zh.wikipedia.org/zh-tw/%E9%B4%BF%E5%B7%A2%E5%8E%9F%E7%90%86
[11]: https://en.wikipedia.org/wiki/Pigeonhole_principle

思考一下：

> 在十進位系統裡，若只使用一位數，能表示出最多幾種獨特(unique)的編號？

答案是 10 種，也就是 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 。

進一步思考：

> 在十進位系統裡，若只使用一位數為 11 個物件編號，是否有可能讓每個物件都
> 有其獨一無二的編號？

答案是不可能。因為為前 10 個物件編號時，就會用完僅有的 10 個獨特編號，而
最後一個物件就 **必須** 挑一個數字重覆使用。

這就是[鴿巢原理][10]說的：

> 若有n個籠子和n+1隻鴿子，所有的鴿子都被關在鴿籠裡，那麼至少有一個籠子有
> 至少2隻鴿子。

回頭來看 `GetHashCode()`  ，其傳回的 `int`  是一個 32 位元的數字，最多只
能表示大約 42.9 億種獨特的狀態，也就是 -2147483648, -2147483647,
-2147483646, ... -1, 0, 1, ... 2147483645, 2147483646, 2147483647  這
4294967295  種狀態。

如果有一種物件具有超過 42.9 億種獨特的狀態，那麼在為前 42.9 億種獨特狀態
編號之後，就會把每個 `int`  能代表的數字都會用過一次，接下來，在數學邏輯
上無法避免的，必須重覆使用之前用過的數字來編號，也就是所謂的
[碰撞][12]([collision][13]) 。

[12]: https://zh.wikipedia.org/zh-tw/%E7%A2%B0%E6%92%9E_(%E8%A8%88%E7%AE%97%E6%A9%9F%E7%A7%91%E5%AD%B8)
[13]: https://en.wikipedia.org/wiki/Collision_(computer_science)

### 超過 42.9 億種獨特狀態的物件真的存在嗎？

`long`, 64  位元的數字，可以表示大約 18.4 艾種狀態；一艾是 10 的 18 次方
，也就是是一億（10  的 8  次方）的一百億倍（10  的 10 次方）。

參考資料與官方機器翻譯：

* `int`
  * https://msdn.microsoft.com/zh-tw/library/5kzh1b5w.aspx
  * https://msdn.microsoft.com/en-us/library/5kzh1b5w.aspx
* `long`
  * https://msdn.microsoft.com/en-us/library/ctetwysk.aspx
  * https://msdn.microsoft.com/zh-tw/library/ctetwysk.aspx
