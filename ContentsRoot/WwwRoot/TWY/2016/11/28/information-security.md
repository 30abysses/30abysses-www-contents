> http://www.30abysses.com/TWY/2016/11/28/information-security.md
> by TW Yang <twy@30abysses.com> 2016-11-28 CC-BY-4.0

# **淺談**  資訊安全

一位網友對《[C# System.Valuetype.GetHashCode() 潛在效能、安全問題]》[1]
提出了個問題：

> james732 @ptt.cc
>
> 不過有可能從標準實作算出的hash去倒推特定的資料嗎？

[1]: http://www.30abysses.com/TWY/2016/11/21/c_sharp-gethashcode-valuetype.html

也許、大概、應該不太可能，然而，資訊安全([information security][2]) 是個
很複雜、反直覺的題目，每個系統的威脅模型([threat model][3]) 不同，很難從
單一弱點([attack vector][4] 來評估；但是，通常透露給攻擊者的資訊是愈少愈
好。

[2]: https://en.wikipedia.org/wiki/Information_security
[3]: https://en.wikipedia.org/wiki/Threat_model
[4]: https://en.wikipedia.org/wiki/Vector_(malware)

以下將討論一個理論上的例子，與一個實際上的例子。
