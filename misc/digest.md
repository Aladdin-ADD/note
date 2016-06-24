## 论面向组合子程序设计方法

http://www.blogjava.net/ajoo/articles/27846.html

前面几片文章，半懂不懂。
开始讲的 logger，感觉思路没错，但是没有太多其他感想。
中间讲的什么，不懂。
最后举的这个例子，一下子感觉豁然开朗。

`IfElse` 的出现，让我一下子想到了 scheme（所谓的手上锤子，满眼钉子……

业务上碰到过相同的问题，各种选项互斥，不过没有复杂到这种程度。
直接用各种 if 判断解决了。
业务上还碰到过类似的问题，同样是各种选项交叉，没想到能做这种抽象。

对于具体的需求中如何去整合，可以再在实践中去练习。
但是这种组合思想，非常有启发性。

---

## ISO 8601 真的适合作为传输类型么？

https://www.web-tinker.com/article/21323.html
https://tools.ietf.org/html/rfc3339
https://www.w3.org/TR/NOTE-datetime

> 我本来是希望 Web API 中的日期时间格式使用一种人类可读且不受时区影响的格式，
> 可是 ISO8601 中只有一部分是如此，甚至不带时区信息的 Y-m-d 的日期格式也是规范的一部分。

很早之前还为 ISO8601 还是 timestamp 和人争吵过。
当时坚持 ISO8601 主要是为了接口参数的可读性，timestamp 完全无法肉眼解析。

看了本文，才意识到这个问题，简单的 `YYYY-MM-DD` 没有定义出时区，并不完整。
简单假设东八区肯定是不对的……

使用 `YYYY-MM-DD` 的初衷，是 url 对普通修改更加友好。
如果不暴露在 url 上，纯粹的 API 参数，那么严格遵循 RFC3339 可能更好一些。
而暴露给用户的 url，如果用 RFC3339 感觉可读性更糟糕了。
要求时间准确的情况下，是否有比 timestamp 更具可读性的选择呢。