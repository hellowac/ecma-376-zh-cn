# lxml

原文: <https://lxml.de/index.html>

## 前言

=== "中文"

    lxml XML 工具包是 C 库 [libxml2](http://xmlsoft.org/) 和 [libxslt](http://xmlsoft.org/XSLT/) 的 Pythonic 绑定。 它的独特之处在于它将这些库的速度和 XML 功能完整性与本机 Python API 的简单性相结合，大部分兼容但优于众所周知的 [ElementTree API](http://effbot.org/zone/element-index.htm)。 最新版本适用于从 2.7 到 3.9 的所有 CPython 版本。 有关 lxml 项目的背景和目标的更多信息，请参阅[简介](https://lxml.de/intro.html)。 [常见问题解答](https://lxml.de/FAQ.html)中回答了一些常见问题。

=== "英文"

    Introduction

    The lxml XML toolkit is a Pythonic binding for the C libraries [libxml2](http://xmlsoft.org/) and libxslt. It is unique in that it combines the speed and XML feature completeness of these libraries with the simplicity of a native Python API, mostly compatible but superior to the well-known [ElementTree](http://effbot.org/zone/element-index.htm) API. The latest release works with all CPython versions from 2.7 to 3.9. See the [introduction](https://lxml.de/intro.html) for more information about background and goals of the lxml project. Some common questions are answered in the [FAQ](https://lxml.de/FAQ.html).

## 支持本项目

=== "中文"

    参考原文: <https://lxml.de/index.html#support-the-project>

=== "英文"

    **Support the project**

    参考原文: <https://lxml.de/index.html#support-the-project>

## 文档

=== "中文"

    本网站的 HTML 文档是正常的 [源代码下载](https://lxml.de/index.html#download) 的一部分.

    - 教程:
        - [用于 XML 处理的 lxml.etree 教程](https://lxml.de/tutorial.html)
        - John Shipman 的教程: [使用 lxml 进行 Python XML 处理](http://www.nmt.edu/tcc/help/pubs/pylxml/)
        - Fredrik Lundh 的 [ElementTree 教程](http://effbot.org/zone/element.htm)
    - ElementTree:
        - [ElementTree API](http://effbot.org/zone/element-index.htm#documentation)
        - [兼容性](https://lxml.de/compatibility.html) 以及 lxml.etree 的差异
        - [ElementTree 性能特点](https://lxml.de/performance.html)及比较
    - lxml.etree:
        - [lxml.etree 特定 API](https://lxml.de/api.html) 文档
        - [生成的 API 文档](https://lxml.de/api/index.html) 作为参考
        - [解析](https://lxml.de/parsing.html) 和 [校验](https://lxml.de/validation.html) XML
        - [XPath 和 XSLT](https://lxml.de/xpathxslt.html) 支持
        - 针对Xpath和XSLT 的 Python [XPath 扩展函数](https://lxml.de/extensions.html)
        - 针对自定义XML API 的 [自定义xml元素类](https://lxml.de/element_classes.html)  (参考 [EuroPython 2008 演讲](https://lxml.de/s5/lxml-ep2008.html))
        - 用于与其他 XML 工具连接的 [SAX 兼容 API](https://lxml.de/sax.html)
        - 用于与外部 C/Cython 模块连接的 [C 级 API](https://lxml.de/capi.html)
    - lxml.objectify:
        - [lxml.objectify](https://lxml.de/objectify.html) API 文档
        - [objectify 和 etree] 的简要比较(https://lxml.de/FAQ.html#what-is-the-difference-between-lxml-etree-and-lxml-objectify)

    lxml.etree 尽可能遵循 ElementTree API，将其构建在本机 libxml2 树之上。 如果您是 ElementTree 的新手，请从 lxml.etree XML 处理教程开始。 另请参阅 ElementTree 兼容性概述以及将 lxml 与原始 ElementTree 和 cElementTree 实现进行比较的 ElementTree 性能页面。

    Right after the lxml.etree tutorial for XML processing and the ElementTree documentation, the next place to look is the lxml.etree specific API documentation. It describes how lxml extends the ElementTree API to expose libxml2 and libxslt specific XML functionality, such as XPath, Relax NG, XML Schema, XSLT, and c14n (including c14n 2.0). Python code can be called from XPath expressions and XSLT stylesheets through the use of XPath extension functions. lxml also offers a SAX compliant API, that works with the SAX support in the standard library.

    在了解 XML 处理的 lxml.etree 教程和 ElementTree 文档之后，下一个要查看的地方是 lxml.etree 特定的 API 文档。 它描述了 lxml 如何扩展 ElementTree API 以公开 libxml2 和 libxslt 特定的 XML 功能，例如 XPath、Relax NG、XML Schema、XSLT 和 c14n（包括 c14n 2.0）。 通过使用 XPath 扩展函数，可以从 XPath 表达式和 XSLT 样式表调用 Python 代码。 lxml 还提供了符合 SAX 的 API，可与标准库中的 SAX 支持配合使用。
    
    有一个单独的模块 lxml.objectify 在 lxml.etree 之上实现数据绑定 API。 请参阅 objectify 和 etree FAQ 条目进行比较。
    
    除了 ElementTree API 之外，lxml 还具有用于自定义 XML 元素类的复杂 API。 这是在 lxml 之上编写任意 XML 驱动的 API 的简单方法。 lxml.etree 还具有 C 级 API，可用于在外部 C 模块中高效扩展 lxml.etree，包括快速自定义元素类支持。

=== "英文"

    **Documentation**

    The HTML documentation from this web site is part of the normal [source download](https://lxml.de/index.html#download).

    - Tutorials:
        - the [lxml.etree tutorial for XML processing](https://lxml.de/tutorial.html)
        - John Shipman's tutorial on [Python XML processing with lxml](http://www.nmt.edu/tcc/help/pubs/pylxml/)
        - Fredrik Lundh's [tutorial for ElementTree](http://effbot.org/zone/element.htm)
    - ElementTree:
        - [ElementTree API](http://effbot.org/zone/element-index.htm#documentation)
        - [compatibility](https://lxml.de/compatibility.html) and differences of lxml.etree
        - [ElementTree performance](https://lxml.de/performance.html) characteristics and comparison
    - lxml.etree:
        - [lxml.etree specific API](https://lxml.de/api.html) documentation
        - the [generated API documentation](https://lxml.de/api/index.html) as a reference
        - [parsing](https://lxml.de/parsing.html) and [validating](https://lxml.de/validation.html) XML
        - [XPath and XSLT](https://lxml.de/xpathxslt.html) support
        - Python [XPath extension functions](https://lxml.de/extensions.html) for XPath and XSLT
        - [custom XML element classes](https://lxml.de/element_classes.html) for custom XML APIs (see [EuroPython 2008 talk](https://lxml.de/s5/lxml-ep2008.html))
        - a [SAX compliant API](https://lxml.de/sax.html) for interfacing with other XML tools
        - a [C-level API](https://lxml.de/capi.html) for interfacing with external C/Cython modules
    - lxml.objectify:
        - [lxml.objectify](https://lxml.de/objectify.html) API documentation
        - a brief comparison of [objectify and etree](https://lxml.de/FAQ.html#what-is-the-difference-between-lxml-etree-and-lxml-objectify)
    
    lxml.etree follows the [ElementTree](http://effbot.org/zone/element-index.htm) API as much as possible, building it on top of the native libxml2 tree. If you are new to ElementTree, start with the [lxml.etree tutorial for XML processing](https://lxml.de/tutorial.html). See also the ElementTree [compatibility](https://lxml.de/compatibility.html) overview and the [ElementTree performance](https://lxml.de/performance.html) page comparing lxml to the original [ElementTree](http://effbot.org/zone/element-index.htm) and [cElementTree](http://effbot.org/zone/celementtree.htm) implementations.

    Right after the [lxml.etree tutorial for XML processing](https://lxml.de/tutorial.html) and the [ElementTree](http://effbot.org/zone/element-index.htm) documentation, the next place to look is the [lxml.etree specific API](https://lxml.de/api.html) documentation. It describes how lxml extends the ElementTree API to expose libxml2 and libxslt specific XML functionality, such as [XPath](https://www.w3.org/TR/xpath/), [Relax NG](https://relaxng.org/), [XML Schema](https://www.w3.org/XML/Schema), [XSLT](https://www.w3.org/TR/xslt), and [c14n](https://www.w3.org/TR/xml-c14n) (including [c14n 2.0](https://www.w3.org/TR/xml-c14n2)). Python code can be called from XPath expressions and XSLT stylesheets through the use of [XPath extension functions](https://lxml.de/extensions.html). lxml also offers a [SAX compliant API](https://lxml.de/sax.html), that works with the SAX support in the standard library.
    
    There is a separate module [lxml.objectify](https://lxml.de/objectify.html) that implements a data-binding API on top of lxml.etree. See the [objectify and etree](https://lxml.de/FAQ.html#what-is-the-difference-between-lxml-etree-and-lxml-objectify) FAQ entry for a comparison.
    
    In addition to the ElementTree API, lxml also features a sophisticated API for [custom XML element classes](https://lxml.de/element_classes.html). This is a simple way to write arbitrary XML driven APIs on top of lxml. lxml.etree also has a [C-level API](https://lxml.de/capi.html) that can be used to efficiently extend lxml.etree in external C modules, including fast custom element class support.

## 下载

=== "中文"

    下载 lxml 的最佳方法是访问 Python 包索引 (PyPI) 上的 lxml。 它具有在各种平台上编译的源代码。 源发行版使用此密钥进行签名。

    最新版本是lxml 4.9.2，于2022年12月13日发布（4.9.2的更改）。 下面列出了旧版本。
    
    请看一下安装说明！
    
    这个完整的网站（包括生成的 API 文档）是源代码分发的一部分，因此如果您想下载文档以供离线使用，请获取源存档并将 doc/html 目录复制到源代码树中。
    
    最新的可安装开发人员源可从 Github 获取。 还可以使用如下命令直接从 Github 查看 lxml 的最新开发版本：

    ```shell
    git clone https://github.com/lxml/lxml.git lxml
    ```

    您可以通过网络浏览源存储库及其历史记录。 请首先阅读如何从源代码构建 lxml。 还可以访问开发人员版本的最新更改。 您可以在那里检查您发现的错误是否已修复，或者您想要的功能是否已在最新的主干版本中实现。

=== "英文"

    **Download**

    The best way to download lxml is to visit [lxml at the Python Package Index](http://pypi.python.org/pypi/lxml/) (PyPI). It has the source that compiles on various platforms. The source distribution is signed with [this key](https://lxml.de/pubkey.asc).

    The latest version is [lxml 4.9.2](https://lxml.de/files/lxml-4.9.2.tgz), released 2022-12-13 ([changes for 4.9.2](https://lxml.de/changes-4.9.2.html)). [Older versions](https://lxml.de/index.html#old-versions) are listed below.
    
    Please take a look at the [installation instructions](https://lxml.de/installation.html) !
    
    This complete website (including the generated API documentation) is part of the source distribution, so if you want to download the documentation for offline use, take the source archive and copy the doc/html directory out of the source tree.
    
    The latest [installable developer sources](https://github.com/lxml/lxml/archive/master.zip) are available from Github. It's also possible to check out the latest development version of lxml from Github directly, using a command like this:

    ```shell
    git clone https://github.com/lxml/lxml.git lxml
    ```

    You can browse the [source repository](https://github.com/lxml/lxml/) and its history through the web. Please read [how to build lxml from source](https://lxml.de/build.html) first. The [latest CHANGES](https://github.com/lxml/lxml/blob/master/CHANGES.txt) of the developer version are also accessible. You can check there if a bug you found has been fixed or a feature you want has been implemented in the latest trunk version.

## 邮件列表

=== "中文"

    问题？ 建议？ 贡献代码？ 我们有一个[邮件列表](https://lxml.de/mailinglist/).
    
    您还可以[搜索档案](https://mail.python.org/archives/list/lxml@python.org/) 查找过去的问题和讨论。

=== "英文"

    **Mailing list**

    Questions? Suggestions? Code to contribute? We have a [mailing list](https://lxml.de/mailinglist/).
    
    You can also [search the archive](https://mail.python.org/archives/list/lxml@python.org/) for past questions and discussions.

## 问题追踪

=== "中文"

    lxml 使用启动板错误跟踪器。 如果您确定在 lxml 中发现了错误，请在那里提交错误报告。 如果您不确定 lxml 的某些意外行为是否是错误，请先检查文档并在邮件列表中询问。 不要忘记搜索档案！

=== "英文"

    **Bug tracker**

    lxml uses the [launchpad bug tracker](https://launchpad.net/lxml/). If you are sure you found a bug in lxml, please file a bug report there. If you are not sure whether some unexpected behaviour of lxml is a bug or not, please check the documentation and ask on the [mailing list](https://lxml.de/mailinglist/) first. Do not forget to [search the archive](https://mail.python.org/archives/list/lxml@python.org/)!

## 许可

=== "中文"

    lxml 库是在 BSD 许可证下提供的。 libxml2 和 libxslt2 本身是根据 MIT 许可证提供的。 因此，在代码库中使用 lxml 应该没有任何障碍。

=== "英文"

    The lxml library is shipped under a BSD license. libxml2 and libxslt2 itself are shipped under the MIT license. There should therefore be no obstacle to using lxml in your codebase.

## 过时版本列表

参考原文: <https://lxml.de/index.html#old-versions>

## 项目收入报告

=== "中文"

    lxml 在 PyPI 上每月的下载量超过 5000 万次。

    - 2021年项目总收入：4890.37欧元（407.53欧元/月）
        - Tidelift: EUR 4066.66
        - Paypal: EUR 223.71
        - 其他: EUR 600.00
    - 2020年项目总收入：6065.86欧元（506.49欧元/月）
        - Tidelift: EUR 4064.77
        - Paypal: EUR 1401.09
        - 其他: EUR 600.00
    - 2019年项目总收入：717.52欧元（59.79欧元/月）
        - Tidelift: EUR 360.30
        - Paypal: EUR 157.22
        - 其他: EUR 200.00

=== "英文"

    **Project income report**

    lxml has [more than 50 million downloads](https://pypistats.org/packages/lxml) per month on PyPI.

    - Total project income in 2021: EUR 4890.37 (407.53 € / month)
        - Tidelift: EUR 4066.66
        - Paypal: EUR 223.71
        - other: EUR 600.00
    - Total project income in 2020: EUR 6065,86 (506.49 € / month)
        - Tidelift: EUR 4064.77
        - Paypal: EUR 1401.09
        - other: EUR 600.00
    - Total project income in 2019: EUR 717.52 (59.79 € / month)
        - Tidelift: EUR 360.30
        - Paypal: EUR 157.22
        - other: EUR 200.00

## 捐赠法律声明

=== "中文"

    您对 lxml 项目的任何捐赠都是自愿的，并非任何服务、商品或优势的费用。 通过向 lxml 项目捐款，您承认我们有权以任何合法方式和我们认为合适的任何合法目的使用您捐赠的资金，除非需要，我们没有义务向任何一方披露方式和目的 根据适用法律。 尽管 lxml 是免费软件，但据我们所知，lxml 项目不具有任何免税状态。 lxml项目既不是在任何国家注册的非营利公司，也不是注册的慈善机构。 您的捐款可能可以免税，也可能不能免税； 请就此问题咨询您的税务顾问。 未经您的同意，我们不会公布或披露您的姓名和/或电子邮件地址，除非适用法律要求。 您的捐款不可退还。

=== "英文"

    **Legal Notice for Donations**

    Any donation that you make to the lxml project is voluntary and is not a fee for any services, goods, or advantages. By making a donation to the lxml project, you acknowledge that we have the right to use the money you donate in any lawful way and for any lawful purpose we see fit and we are not obligated to disclose the way and purpose to any party unless required by applicable law. Although lxml is free software, to the best of our knowledge the lxml project does not have any tax exempt status. The lxml project is neither a registered non-profit corporation nor a registered charity in any country. Your donation may or may not be tax-deductible; please consult your tax advisor in this matter. We will not publish or disclose your name and/or e-mail address without your consent, unless required by applicable law. Your donation is non-refundable.
