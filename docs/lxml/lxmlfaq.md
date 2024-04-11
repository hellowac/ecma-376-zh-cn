# lxml 常见问题解答

lxml FAQ - Frequently Asked Questions

Frequently asked questions on lxml. See also the notes on compatibility to ElementTree.

=== "中文"

    有关 lxml 的常见问题。 另请参阅有关 [ElementTree](http://effbot.org/zone/element-index.htm) [兼容性](./elementtreecompatibilityoflxmletree.md)的说明。
    
    内容

    - 一般问题
        - 有教程吗?
        - 在哪里可以找到有关 lxml 的更多文档?
        - lxml执行什么标准?
        - 谁使用lxml?
        - lxml.etree 和 lxml.objectify 之间有什么区别?
        - 如何让我的应用程序运行得更快?
        - 序列化元素上的尾随文本怎么样?
        - 如何确定某个元素是评论还是 PI?
        - 如何将 XML 树映射到字典的字典中?
        - 为什么 lxml 有时会返回 Python 2 中文本的“str”值?
        - 为什么我在某些系统上会遇到 XInclude 或 DTD 查找失败的情况，而在其他系统上却不会?
        - 命名空间在 lxml 中如何工作?
    - 安装
        - 我应该使用或需要哪个版本的 libxml2 和 libxslt?
        - 二进制版本在哪里?
        - 为什么在安装 lxml 时出现缺少 UCS4 符号的错误?
        - 我的 C 编译器在安装时崩溃
    - 贡献
        - 为什么 lxml 不是用 Python 编写的？
        - 我怎样才能做出贡献?
    - 问题
        - 我的应用程序崩溃了!
        - 我的应用程序在 MacOS-X 上崩溃!
        - 我想我在 lxml 中发现了一个错误。 我应该怎么办?
        - 我如何知道错误确实存在于 lxml 中而不是 libxml2 中?
    - 线程
        - 我可以使用线程并发访问lxml API吗?
        - 如果我使用线程，我的程序运行得更快吗?
        - 如果我关闭线程，我的单线程程序会运行得更快吗?
        - 为什么我不能在其他线程中重用 XSLT 样式表?
        - 我的程序在使用 mod_python/Pyro/Zope/Plone/... 运行时崩溃
    - 解析和序列化
        - 为什么 Pretty_print 选项不重新格式化我的 XML 输出?
        - 为什么 lxml 无法从 unicode 字符串解析我的 XML?
        - lxml 可以解析以 unicode/text 模式打开的文件对象吗?
        - str(xslt(doc)) 和 xslt(doc).write() 有什么区别 ?
        - 为什么我不能在 iterparse() 中删除父节点或清除根节点?
        - 如何在 XML 文本中输出空字符?
        - lxml 是否容易受到 XML 炸弹的攻击?
        - 如何安全地使用 lxml 作为 Web 服务端点?
        - 如何对属性进行排序?
    - XPath 和 文档 相关
        - Element(Tree) 上的 findall() 和 xpath() 方法是什么?
        - 为什么 findall() 不支持完整的 XPath 表达式?
        - 如何找出文档中使用了哪些命名空间前缀?
        - 如何为 XPath 表达式指定默认命名空间?
        - 如何在迭代过程中修改树?

    下面的代码示例使用`lxml.etree`模块：

    ```pycon
    >>> from lxml import etree
    ```

    更多参考原文: <https://lxml.de/FAQ.html>

=== "英文"

    有关 lxml 的常见问题。 另请参阅有关 ElementTree 兼容性的说明。
    
    Contents

    - General Questions
        - Is there a tutorial?
        - Where can I find more documentation about lxml?
        - What standards does lxml implement?
        - Who uses lxml?
        - What is the difference between lxml.etree and lxml.objectify?
        - How can I make my application run faster?
        - What about that trailing text on serialised Elements?
        - How can I find out if an Element is a comment or PI?
        - How can I map an XML tree into a dict of dicts?
        - Why does lxml sometimes return 'str' values for text in Python 2?
        - Why do I get XInclude or DTD lookup failures on some systems but not on others?
        - How do namespaces work in lxml?
    - Installation
        - Which version of libxml2 and libxslt should I use or require?
        - Where are the binary builds?
        - Why do I get errors about missing UCS4 symbols when installing lxml?
        - My C compiler crashes on installation
    - Contributing
        - Why is lxml not written in Python?
        - How can I contribute?
    - Bugs
        - My application crashes!
        - My application crashes on MacOS-X!
        - I think I have found a bug in lxml. What should I do?
        - How do I know a bug is really in lxml and not in libxml2?
    - Threading
        - Can I use threads to concurrently access the lxml API?
        - Does my program run faster if I use threads?
        - Would my single-threaded program run faster if I turned off threading?
        - Why can't I reuse XSLT stylesheets in other threads?
        - My program crashes when run with mod_python/Pyro/Zope/Plone/...
    - Parsing and Serialisation
        - Why doesn't the pretty_print option reformat my XML output?
        - Why can't lxml parse my XML from unicode strings?
        - Can lxml parse from file objects opened in unicode/text mode?
        - What is the difference between str(xslt(doc)) and xslt(doc).write() ?
        - Why can't I just delete parents or clear the root node in iterparse()?
        - How do I output null characters in XML text?
        - Is lxml vulnerable to XML bombs?
        - How do I use lxml safely as a web-service endpoint?
        - How can I sort the attributes?
    - XPath and Document Traversal
        - What are the findall() and xpath() methods on Element(Tree)?
        - Why doesn't findall() support full XPath expressions?
        - How can I find out which namespace prefixes are used in a document?
        - How can I specify a default namespace for XPath expressions?
        - How can I modify the tree during iteration?

    The code examples below use the 'lxml.etree` module:

    ```pycon
    >>> from lxml import etree
    ```

    更多参考原文: <https://lxml.de/FAQ.html>
