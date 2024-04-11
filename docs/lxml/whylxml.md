# 为何选择lxml

## 座右铭

=== "中文"

    “没有陌生感的刺激”

    解释一下座右铭：
    
    "使用 libxml2 编程就像拥抱异国情调的陌生人一样令人兴奋。 它似乎有可能实现你最疯狂的梦想，但你脑海中的某个地方有一个唠叨的声音警告你，你即将以最糟糕的方式被搞砸。" (马克·皮尔格林的一句话)
    
    Mark Pilgrim 特别描述了 Python 程序员在处理 libxml2 时的经历。 libxml2 的默认 Python 绑定快速、令人兴奋、功能强大，并且您的代码可能会以某种可怕的方式失败，而您在编写 Python 代码时实际上不必担心。 lxml 结合了 libxml2 的强大功能和 Python 的易用性。

=== "英文"

    **Motto**
    
    To explain the motto:

    "Programming with libxml2 is like the thrilling embrace of an exotic stranger. It seems to have the potential to fulfill your wildest dreams, but there's a nagging voice somewhere in your head warning you that you're about to get screwed in the worst way." ([a quote by Mark Pilgrim](https://web.archive.org/web/20110902041836/http://diveintomark.org/archives/2004/02/18/libxml2))
    
    Mark Pilgrim was describing in particular the experience a Python programmer has when dealing with libxml2. The default Python bindings of libxml2 are fast, thrilling, powerful, and your code might fail in some horrible way that you really shouldn't have to worry about when writing Python code. lxml combines the power of libxml2 with the ease of use of Python.

## 目标

=== "中文"

    C 库 [libxml2](http://www.xmlsoft.org/) 和 [libxslt](http://xmlsoft.org/XSLT) 有巨大的好处：

    - 符合标准的 XML 支持。
    - 支持（损坏的）HTML。
    - 功能齐全。
    - 由 XML 专家积极维护。
    - fast. fast! FAST!
    
    这些库已经附带了 Python 绑定，但这些 Python 绑定模仿了 C 级接口。 这会产生许多问题：
    
    - 非常低的水平和 C-ish（不是 Pythonic）。
    - 记录不足且规模庞大，您会迷失其中。
    - API 中的 UTF-8，而不是 Python unicode 字符串。
    - 很容易导致 Python 出现段错误。
    - 需要手动内存管理！
    
    lxml 是 libxml2 和 libxslt 的新 Python 绑定，完全独立于这些现有的 Python 绑定。 其目标：
    
    - Pythonic API.
    - 文档化的.
    - 在 API 中使用 Python unicode 字符串。
    - 安全（无段错误）。
    - 无需手动内存管理！
    
    lxml 旨在通过尽可能遵循 ElementTree API 来提供 Pythonic API。 我们试图避免发明太多新的 API，或者您必须学习新东西 —— XML 已经足够复杂了。

=== "英文"

    **Aims**

    The C libraries [libxml2](http://www.xmlsoft.org/) and [libxslt](http://xmlsoft.org/XSLT) have huge benefits:

    - Standards-compliant XML support.
    - Support for (broken) HTML.
    - Full-featured.
    - Actively maintained by XML experts.
    - fast. fast! FAST!
    
    These libraries already ship with Python bindings, but these Python bindings mimic the C-level interface. This yields a number of problems:
    
    - very low level and C-ish (not Pythonic).
    - underdocumented and huge, you get lost in them.
    - UTF-8 in API, instead of Python unicode strings.
    - Can easily cause segfaults from Python.
    - Require manual memory management!
    
    lxml is a new Python binding for libxml2 and libxslt, completely independent from these existing Python bindings. Its aims:
    
    - Pythonic API.
    - Documented.
    - Use Python unicode strings in API.
    - Safe (no segfaults).
    - No manual memory management!
    
    lxml aims to provide a Pythonic API by following as much as possible the ElementTree API. We're trying to avoid inventing too many new APIs, or you having to learn new things -- XML is complicated enough.
