# ECMA-376-1:2016 - Part 2

Office 开放 XML 文件格式 -- 开放封装约定

Office Open XML File Formats -- Open Packaging Conventions

相关python包参考: <https://github.com/python-openxml/python-opc>

**概要目录**

- [1. 适用范围](#1-适用范围)
- [2. 规范性引用文件](#2-规范性引用文件)
- [3. 术语和定义](#3-术语和定义)
    - [3.1 Basics](#31-basics)
    - [3.2 抽象包模型](#32-抽象包模型)
    - [3.3 物理包模型](#33-物理包模型)
    - [3.4 数字签名和缩略图](#34-数字签名和缩略图)
    - [3.5 具体时线](#35-实现)
    - [3.6 核心属性](#36-核心属性)
- [4. 一致性](#4-一致性)
- [5. 概述](#5-概述)
- [6. 抽象封装模型](#6-抽象封装模型)
    - [6.1 常规](#61-常规)
    - [6.2 部件](#62-部件)
    - [6.3 部件寻址](#63-部件寻址)
    - [6.4 解决相关引用](#64-解决相关引用)
    - [6.5 关系](#65-关系)
- [7. 物理封装模型](#7-物理封装模型)
    - [7.1 General](#71-general)
    - [7.2 物理映射指南](#72-物理映射指南)
    - [7.3 映射到 ZIP 文件](#73-映射到-zip-文件)
- [8. 核心属性](#8-核心属性)
    - [8.1 常规](#81-常规)
    - [8.2 核心属性部件](#82-核心属性部件)
    - [8.3 核心属性标记](#83-核心属性标记)
- [9. 缩略图](#9-缩略图)
- [10. 数字签名](#10-数字签名)
    - [10.1 General](#101-general)
- [附录 A (informative) 生成相对引用的预处理](#annex-a-informative-生成相对引用的预处理)
- [附录 B (normative) 使用 ZIP 功能的限制和说明](#annex-b-normative-使用-zip-功能的限制和说明)
- [附录 C (normative) W3C XML Schema](#annex-c-normative-w3c-xml-schema)
- [附录 D (informative) Schemas - RELAX NG](#annex-d-informative-schemas---relax-ng)
- [附录 E (normative)](#annex-e-normative-标准命名空间和媒体类型)
- [附录 F (informative) 物理包模型设计考虑因素](#annex-f-informative-物理包模型设计考虑因素)
- [附录 G (informative) ECMA-376-2021 和 ECMA-376:2006 之间的差异](#annex-g-informative-ecma-376-2021-和-ecma-3762006-之间的差异)
- [附录 H (Informative) 包示例](#annex-h-informative-包示例)

## 前言

=== "中文"

    该版本取消并取代了经过技术修订的前一版本（ECMA-376-2:2012）。
    
    与上一版相比主要变化如下：

    - 在适当的情况下，规范性参考已更新为使用未注明日期或更新版本的其他标准。
    - 第 3 条（术语和定义）经过修订，删除了任何规范性条款中未使用的术语，然后将术语重新分组。
    - 图表注释的子条款（之前版本中的 5.1）已被删除，因为核心属性现在是由散文和模式而不是图表定义的。
    - 首字母缩写词和缩写词的条款（先前版本中的第 6 条）已被删除，因为 ISO/IEC 标准定义“ISO”和“IEC”没有意义。
    - 第 6 条（抽象包模型，上一版本中的第 8 条）已完全重写。 特别是，(1) 包 IRI 已在本条款中定义，而不是在附录中，(2) 添加了新的子条款“解析相关引用”； (3) 区分了部件关系部件和包关系部件； (4) 基础 IRI 已明确定义； (5) 在 RFC 3987 的基础上澄清了部件名称中非 ASCII 字符的处理。
    - 媒体类型为空字符串的选项已被删除，因为这与 RFC 2046 中媒体类型的定义以及 C.2 引用的模式中定义的现有正则表达式相冲突。
    - 第7条（物理封装模型，上一版第9条）略有修改。 交错是在逻辑项名称之前引入的。 非 ASCII 字符的百分比编码和非百分比编码已在 [7.3.4] 和 [7.3.5] 中明确引入。
    - 第 8 条（核心属性，上一版本中的第 10 条）已使用散文和模式而不是图表进行了重写。
    - 第 10 条（数字签名，上一版本的第 12 条）已彻底修订。 特别是，该条款现在明确了签名和摘要方法算法选择的约定，这反映了自本文档第一版以来算法的持续发展。
    - 附录 A 已提供信息。
    - 定义包 IRI 的规范性附录（之前版本中的附录 B）已被删除。 Pack IRI 现在在第 6 条中定义。
    - 附录C和附录D（之前版本中的附录D和E）不再定义模式(Schema)，而是引用外部定义的模式。
    - 满足一致性要求的指南（之前版本中的附录 H）已被删除。
    - 关于流媒体消费的要求已被放弃。
    - 只要有可能，对程序的要求就被重写为对数据的要求。
    - 添加了附录 H 来描述示例包。
    - 索引（前版中的附录 J）已被删除。
    - 添加了参考书目(Bibliography)。

=== "英文"

    **Foreword**
    
    This edition cancels and replaces the previous edition (ECMA-376-2:2012), which has been technically revised.
    
    The main changes compared to the previous edition are as follows:

    - Where appropriate, normative references have been updated to use undated or more recent versions of other standards.
    - Clause 3 (Terms and definitions) has been revised by removing terms not used by any normative clauses and then reorganizing terms into groups.
    - The subclause for diagram notes (5.1 in the preceding editions) has been removed, since core properties are now defined by prose and schemas rather than by diagrams.
    - The clause for acronyms and abbreviations (Clause 6 in the preceding editions) has been removed, since it does not make sense for an ISO/IEC standard to define "ISO" and "IEC".
    - Clause 6 (Abstract package model, Clause 8 in the previous edition) has been completely rewritten. In particular, (1) pack IRIs have been defined in this clause rather than in an annex, (2) a new subclause, "Resolving relative references", has been added; (3) part Relationships parts and package Relationships parts have been distinguished; (4) base IRIs have been clearly defined; and (5) handling of non-ASCII characters in part names has been clarified on the basis of RFC 3987.
    - The option for media type to be an empty string has been removed, as this conflicts with the definition of media type in RFC 2046 and the existing regular expression defined in the schema referenced by C.2.
    - Clause 7 (Physical package model, Clause 9 in the previous edition) has been slightly revised. Interleaving has been introduced before logical item names. Percent-encoding and un-percent encoding of non-ASCII characters have been explicitly introduced in 7.3.4 and 7.3.5.
    - Clause 8 (Core properties, Clause 10 in the previous edition) has been rewritten by using prose and schemas rather than diagrams.
    - Clause 10 (Digital signatures, Clause 12 in the previous edition) has been thoroughly revised. In particular, this clause now makes clear a convention for the choice of algorithms for signature and digest methods, which reflects the ongoing development of algorithms since the first edition of this document.
    - Annex A has been made informative.
    - The normative annex that defined pack IRIs (Annex B in the preceding editions) has been dropped. Pack IRIs are now defined in Clause 6.
    - Annex C and Annex D (Annexes D and E in the preceding editions) no longer define schemas but reference externally defined schemas.
    - Guidelines for meeting conformance requirements (Annex H in the preceding editions) have been dropped.
    - Requirements around streaming consumption have been dropped.
    - Wherever possible, requirements on programs have been rewritten as those on data.
    - Annex H has been added to depict an example package.
    - The Index (Annex J in the preceding editions) has been deleted.
    - Bibliography has been added.

## 简介

=== "中文"

    ECMA-376（所有部件）指定了一系列 XML 模式，统称为 Office Open XML，它定义了文字处理、电子表格和演示文稿文档的 XML 词汇表，以及符合这些模式（Schema）的文档的打包。

    目标是通过最广泛的工具和平台实现 Office Open XML 格式，促进办公生产力应用程序和业务线系统之间的互操作性，并支持和加强文档归档和保存，所有这些都在 一种与现有的`Microsoft® Office 文档`语料库完全兼容的方式。

    !!! info "`Microsoft® Office 文档`"

        提供此信息是为了方便本文档的用户，并不构成 Ecma 对指定产品的认可。 如果可以证明可以产生相同的结果，则可以使用等效产品。
    
    本文件包括两个附录（[附录 C] 和[附录 D]），涉及以电子形式提供的数据文件。

    本文档定义的文档表示格式与 ECMA-376:2006 相应部分中定义的格式不同。 一些差异反映在架构更改中，如[附录 G] 所示。
    
    第五版保留了所有以前的功能，并且没有添加新功能。

=== "英文"

    **Introduction**

    ECMA-376 (all Parts) specifies a family of XML schemas, collectively called Office Open XML, which define the XML vocabularies for word-processing, spreadsheet, and presentation documents, as well as the packaging of documents that conform to these schemas.

    The goal is to enable the implementation of the Office Open XML formats by the widest set of tools and platforms, fostering interoperability across office productivity applications and line-of-business systems, as well as to support and strengthen document archival and preservation, all in a way that is fully compatible with the existing corpus of `Microsoft® Office documents`.

    !!! info "Microsoft® Office documents"

        This information is given for the convenience of users of this document and does not constitute an endorsement by Ecma of the product named. Equivalent products may be used if they can be shown to lead to the same results.
    
    This document includes two annexes (Annex C and Annex D) that refer to data files provided in electronic form.
    
    The document representation formats defined by this document are different from the formats defined in the corresponding Part of ECMA-376:2006. Some of the differences are reflected in schema changes, as shown in Annex G.
    
    This fifth edition preserves all previous functionality and adds no new functionality.

## 1. 适用范围

=== "中文"

    本文档定义了一组用于将一个或多个相互关联的字节流（部分）打包为单个资源（包）的约定。 这些约定不仅适用于 ECMA-376-1 和 ECMA-376-4 中描述的 Office Open XML 规范，而且还适用于其他标记规范。

=== "英文"

    **Scope**

    This document defines a set of conventions for packaging one or more interrelated byte streams (parts) as a single resource (package). These conventions are applicable not only to Office Open XML specifications as described in ECMA-376-1 and ECMA-376-4, but also to other markup specifications.

## 2. 规范性引用文件

=== "中文"

    正文中引用下列文件时，其部分或全部内容构成本文件的要求。 对于注明日期的参考文献，仅引用的版本适用。 对于未注明日期的参考文献，适用参考文件的最新版本（包括任何修订）。
    
    ANSI/INCITS 4-1986 [R2017] - 信息系统 - 编码字符集 - 基于7-Bit的美国国家信息交换标准代码 (7 Bit ASCII)，美国国家标准协会 (ANSI)。 2017年
    
    FIPS 186-4, 数字签名标准 (Digital Signature Standard - DSS), 美国商务部国家标准与技术研究院，2013 年 7 月
    
    ECMA-376-3, 信息技术 — 文档描述和处理语言 — Office Open XML File Formats, 第 3 部分：标记兼容性和可扩展性
    
    ISO/IEC 9594-8/ITU-T Rec. X.509, 信息技术 — 开放系统互联 — Part 8 — 目录: 公钥和属性证书框架
    
    ISO 15836-1, 信息和文档 — 都柏林核心元数据元素集 — Part 1: 核心要素
    
    ISO 15836-2, 信息和文档 — 都柏林核心元数据元素集 — Part 2: DCMI 属性和类
    
    RFC 2046, 多用途 Internet 邮件扩展 (MIME) 第二部分: 媒体类型，互联网协会，1996 年 11 月，N. Freed 和 N. Borenstein。 地址: <https://www.rfc-editor.org/info/rfc2046> 
    
    RFC 3986, 统一资源标识符(Uniform Resource Identifier) (URI): 通用语法, 互联网协会, 2005年1月, BernersLee, T., R. Fielding, 和 L. Masinter. 地址: <https://www.rfc-editor.org/info/rfc3986>
    
    RFC 3987, 国际化资源标识符 (IRIs), 互联网协会, 2005年1月, Duerst, M. 和 M. Suignard. 地址: <https://www.rfc-editor.org/info/rfc3987>
    
    RFC 5234, 语法规范的增强 BNF: ABNF, 互联网协会, 2008年1月, D. Crocker and P.Overell, (editors). 地址: <https://www.rfc-editor.org/info/rfc5234>
    
    RFC 6931, 附加 XML 安全统一资源标识符 (URIs), 互联网协会, 2013年4月, D. Eastlake 3rd. 地址: <https://www.rfc-editor.org/info/rfc6931>
    
    RFC 7231, 超文本传输协议(Hypertext Transfer Protocol) (HTTP/1.1): 语义和内容, 互联网协会, 2014年6月, R. Fielding 和 J. Reschke. 地址: <https://www.rfc-editor.org/info/rfc7231>

    Unicode, 统一编码标准, 统一编码联盟. 地址: <http://www.unicode.org/standard/standard.html>
    
    XML 1.0 规范, 可扩展标记语言 (XML) 1.0，第四版。 万维网联盟，2006 年， Tim Bray, Jean Paoli, Eve Maler, C. M. Sperberg-McQueen, 和 François Yergeau (editors). 地址: <http://www.w3.org/TR/2006/REC-xml-20060816/>

    !!! info "Note"

        当本文档也对其进行规范性引用并且也依赖于 XML 的相关参考规范（例如 XML 命名空间和 XML 库）全部一致时，需要对 XML 的规范性引用进行进一步更正，以引用第五版。
    
    XML 命名空间, XML 1.0 中的命名空间（第三版）, 2009 年 12 月 8 日. 万维网联盟, Tim Bray, Dave Hollander, Andrew Layman, 和 Richard Tobin (editors). 地址: <http://www.w3.org/TR/2009/REC-xml-names-20091208/>

    XML 库, XML 库 (第二版), 万维网联盟 , 2009 年 1 月 28 日. Jonathan Marsh 和 Richard Tobin (editors). 地址: <https://www.w3.org/TR/2009/REC-xmlbase-20090128/>
    
    W3C XML Schema 结构, XML Schema 第1部分: 结构 (第二版), 万维网联盟, 2004 年 10 月 28 日, Henry Thompson, David Beech, Murray Maloney 和 Noah Mendelsohn (editors). 地址: <https://www.w3.org/TR/xmlschema-1/>
    
    W3C XML Schema 数据类型, XML Schema 第2部分: 数据类型 (第二版), 万维网联盟, 2004 年 10 月 28 日, Paul Biron 和 Ashok Malhotra (editors). 地址: <https://www.w3.org/TR/xmlschema-2/>
    
    XML-签名语法和处理, 万维网联盟, 2002 年 2 月 12 日, Donald Eastlake, Joseph Reagle 和 David Solo (editors). 地址: <http://www.w3.org/TR/2002/REC-xmldsig-core20020212/>
    
    ZIP Appnote, ZIP 文件格式规范版本 6.2.0, PKWARE Inc., 2004年. 地址: <http://www.pkware.com/documents/APPNOTE/APPNOTE_6.2.0.txt>

=== "英文"

    **Normative references**

    The following documents are referred to in the text in such a way that some or all of their content constitutes requirements of this document. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.
    
    ANSI/INCITS 4-1986 [R2017] - Information Systems - Coded Character Sets - 7-Bit American National Standard Code For Information Interchange (7-Bit ASCII), American National Standards Institute (ANSI). 2017
    
    FIPS 186-4, Digital Signature Standard (DSS), National Institute of Standards and Technology, US Department of Commerce, July 2013
    
    ECMA-376-3, Information technology — Document description and processing languages — Office Open XML File Formats, Part 3: Markup Compatibility and Extensibility
    
    ISO/IEC 9594-8/ITU-T Rec. X.509, Information technology — Open systems interconnection — Part 8— The Directory: Public-key and attribute certificate frameworks
    
    ISO 15836-1, Information and documentation — The Dublin Core metadata element set — Part 1: Core elements
    
    ISO 15836-2, Information and documentation — The Dublin Core metadata element set — Part 2: DCMI Properties and classes
    
    RFC 2046, Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types, The Internet Society, November 1996, N. Freed and N. Borenstein. Available at <https://www.rfc-editor.org/info/rfc2046>
    
    RFC 3986, Uniform Resource Identifier (URI): Generic Syntax, The Internet Society, January 2005, BernersLee, T., R. Fielding, and L. Masinter. Available at <https://www.rfc-editor.org/info/rfc3986>
    
    RFC 3987, Internationalized Resource Identifiers (IRIs), The Internet Society, January 2005, Duerst, M. and M. Suignard. Available at <https://www.rfc-editor.org/info/rfc3987>
    
    RFC 5234, Augmented BNF for Syntax Specifications: ABNF, The Internet Society, January 2008, D. Crocker and P.Overell, (editors). Available at <https://www.rfc-editor.org/info/rfc5234>
    
    RFC 6931, Additional XML Security Uniform Resource Identifiers (URIs), The Internet Society, April 2013, D. Eastlake 3rd. Available at <https://www.rfc-editor.org/info/rfc6931>
    
    RFC 7231, Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content, The Internet Society, June 2014, R. Fielding and J. Reschke. Available at <https://www.rfc-editor.org/info/rfc7231>

    Unicode, The Unicode Standard, The Unicode Consortium. Available at <http://www.unicode.org/standard/standard.html>
    
    The XML 1.0 specification, Extensible Markup Language (XML) 1.0, Fourth Edition. World Wide Web Consortium, 2006, Tim Bray, Jean Paoli, Eve Maler, C. M. Sperberg-McQueen, and François Yergeau (editors). Available at <http://www.w3.org/TR/2006/REC-xml-20060816/>

    !!! info "Note"

        A further correction of the normative reference to XML to refer to the 5th Edition will be necessary when the related Reference Specifications to which this document also makes normative reference, and which also depend upon XML, such as XML Namespaces and XML Base, are all aligned with the 5th Edition.
    
    XML Namespaces, Namespaces in XML 1.0 (Third Edition), 8 December 2009. World Wide Web Consortium, Tim Bray, Dave Hollander, Andrew Layman, and Richard Tobin (editors). Available at <http://www.w3.org/TR/2009/REC-xml-names-20091208/>

    XML Base, XML Base (Second Edition), World Wide Web Consortium , 28 January 2009. Jonathan Marsh and Richard Tobin (editors). Available at <https://www.w3.org/TR/2009/REC-xmlbase-20090128/>
    
    W3C XML Schema Structures, XML Schema Part 1: Structures (Second Edition), World Wide Web Consortium, 28 October 2004, Henry Thompson, David Beech, Murray Maloney and Noah Mendelsohn (editors). Available at <https://www.w3.org/TR/xmlschema-1/>
    
    W3C XML Schema Datatypes, XML Schema Part 2: Datatypes (Second Edition), World Wide Web Consortium, 28 October 2004, Paul Biron and Ashok Malhotra (editors). Available at <https://www.w3.org/TR/xmlschema-2/>
    
    XML-Signature Syntax and Processing, World Wide Web Consortium, 12 February 2002, Donald Eastlake, Joseph Reagle and David Solo (editors). Available at <http://www.w3.org/TR/2002/REC-xmldsig-core20020212/>
    
    ZIP Appnote, ZIP File Format Specification Version 6.2.0, PKWARE Inc., 2004. Available at <http://www.pkware.com/documents/APPNOTE/APPNOTE_6.2.0.txt>

## 3. 术语和定义

=== "中文"

    就本文件而言，适用以下术语和定义。

=== "英文"

    **Terms and definitions**

    For the purposes of this document, the following terms and definitions apply.

### 3.1 Basics

=== "中文"

    **字节**(byte)
    : 8 位序列被视为一个单元

    **字节流**(stream)
    : 线性有序的字节(byte)序列

=== "英文"

    **byte**
    : sequence of 8 bits treated as a unit

    **stream**
    : linearly ordered sequence of bytes (3.1.1)

### 3.2 抽象包模型

=== "中文"

    **部件**(part)
    : 具有名称、MIME 媒体类型和关联公共属性的流(stream)
    
    **抽象包**(abstract package)
    : 包含部件 (Part) 和关系 (Relationship) 集合的逻辑实体
    
    **关系**(relationship)
    : 包关系（package relationship）或部件关系（part relationship）
    
    **包关系**(package relationship)
    : 从包到同一包中的特定部件或外部资源的连接
    
    **部件关系**(part relationship)
    : 从包中的部件 (part) 到同一包中的另一个部件或外部资源的连接
    
    **源**(source)
    : 通过关系 (relationship) 建立连接的部件 (Part) 或包(Package)
    
    **目标**(target)
    : 通过关系 (relationship) 建立连接的部件 (Part) 或外部资源
    
    **关系类型**(relationship type) 
    : 用于指定关系(relationship)角色的绝对 IRI 
    
    **关系部件**(Relationships part)
    : 包含关系 (relationship) 的 XML 表示的部件 (part) 
    
    **抽象包模型**(abstract package model)
    : 定义抽象包(abstract package)的抽象模型
    
    **成长提示**(growth hint)
    : 建议为部件 (part) 保留的字节数 (bytes) 以就地增长 
    
    **打包方案**(pack schema)
    : URI 方案允许将 IRI 用作对包内的各个部件 (part) 进行寻址的统一机制
    
    **打包IRI**(pack IRI)
    : 符合打包方案(pack schema)的IRI
    
    **部件名称**(part name)
    : 唯一标识包内部件 (3.2.1) 的字符串
    
    **关系标识符**(relationship identifier)
    : 由 XML 名称字符组成的字符串，唯一标识来自同一源 (source) 的关系 (relationship)
    
    **目标模型**(target mode)
    : 目标(target)相对引用的解析模式 (3.2.7)
    
    **国际化段**(I18N segment)
    : 部件名称(part name)中的 Unicode 字符串

    !!! info "Note 1"

        当在 [6.2.2.2] 中使用该术语时，应说明对 Unicode 字符串值的限制。

=== "英文"

    **Abstract package model**

    part
    : stream (3.1.2) with a name, a MIME media type and associated common properties
    
    abstract package
    : logical entity that holds a collection of parts (3.2.1) and relationships (3.2.3)
    
    relationship
    : package relationship (3.2.4) or part relationship (3.2.5)
    
    package relationship
    : connection from a package to a specific part (3.2.1) in the same package, or to an external resource
    
    part relationship
    : connection from a part (3.2.1) in a package to another part in the same package, or to an external resource
    
    source
    : part (3.2.1) or package from which a connection is established by a relationship (3.2.3)
    
    target
    : part (3.2.1) or external resource to which a connection is established by a relationship (3.2.3)
    
    relationship type
    : absolute IRI for specifying the role of a relationship (3.2.3)
    
    Relationships part
    : part (3.2.1) containing an XML representation of relationships (3.2.3)
    
    abstract package model
    : abstract model that defines abstract packages (3.2.2)
    
    growth hint
    : suggested number of bytes (3.1.1) to reserve for a part (3.2.1) to grow in place
    
    pack scheme
    : URI scheme that allows IRIs to be used as a uniform mechanism for addressing parts (3.2.1) within a package
    
    pack IRI
    : IRI that conforms to the pack scheme (3.2.12)
    
    part name
    : string that uniquely identifies a part (3.2.1) within a package
    
    relationship identifier
    : string that consists of XML name characters and uniquely identifies a relationship (3.2.3) among those from the same source (3.2.6)
    
    target mode
    : mode of resolution of relative references to targets (3.2.7)
    
    I18N segment
    : Unicode string in a part name (3.2.14)

    Note 1 to entry: The constraints on the value of the Unicode string shall be stated when the term is used in 6.2.2.2.

### 3.3 物理包模型

=== "中文"

    **物理格式**(physical format)
    : 特定文件格式，或其他持久性或传输机制
    
    **物理包**(physical package)
    : 将抽象包（abstract package）映射到物理格式（physical format）的结果
    
    **物理包模型**(physical package model)
    : 物理格式 (physical format) 以及抽象包模型 (abstract package model) 和该物理格式之间的映射对
    
    **部分**(piece)
    : 部件(part)的一部分
    
    **逻辑项**(logical item)
    : 非交错部分 (non-interleaved part)、非交错媒体类型流 (non-interleaved Media Types stream)、交错部分片段 (piece) 或交错媒体类型流片段
    
    **物理包项**(physical package item)
    : 物理包(physical package)中的原子数据集
    
    **ZIP项**(ZIP item)
    : ZIP 文件 (ZIP file) 中的原子数据集，当存档解压缩时，将成为单个文件
    
    **ZIP文件**(ZIP file)
    : ZIP Appnote 中定义的文件
    
    **简单排序**(simple ordering)
    : 定义了在包中布置部件 (parts) 的顺序，其中组成每个部件的所有位都连续存储
    
    **交错排序**(interleaved ordering)
    : 定义了在一个包中放置部件 (parts) 的顺序，其中部件被分成部分 (pieces) 并与其他部件的部分“混合”

    **ASCII 不区分大小写的匹配**(ASCII case-insensitive matching)
    : 比较代码点序列，就好像 0x41 到 0x5A（A 到 Z）范围内的所有 ASCII 代码点都映射到 0x61 到 0x7A（a 到 z）范围内的相应代码点
    
    !!! info "Note": 
    
        ASCII 代码点应由 ANSI/INCITS 4-1986 定义。
    
    **媒体类型流**(Media Types stream)
    : 物理包 (physical package) 中的流 (stream) 表示 XML 文档，该文档指定包中每个部件 (part) 的媒体类型

=== "英文"

    **Physical package model**

    
    physical format
    : specific file format, or other persistence or transport mechanism
    
    physical package
    : result of mapping an abstract package (3.2.2) to a physical format (3.3.1)
    
    physical package model
    : pair of a physical format (3.3.1) and a mapping between the abstract package model (3.2.10) and that physical format
    
    piece
    : portion of a part (3.2.1)
    
    logical item
    : non-interleaved part (3.2.1), non-interleaved Media Types stream (3.3.12), piece (3.3.4) of an interleaved part, or piece of an interleaved Media Types stream
    
    physical package item
    : atomic set of data in a physical package (3.3.2)
    
    ZIP item
    : atomic set of data in a ZIP file (3.3.8) that becomes a file when the archive is uncompressed
    
    ZIP file
    : file as defined in the ZIP Appnote
    
    simple ordering
    : defined ordering for laying out the parts (3.2.1) in a package in which all the bits comprising each part are stored contiguously
    
    interleaved ordering
    : defined ordering for laying out the parts (3.2.1) in a package in which parts are broken into pieces (3.3.4) and “mixed-in” with pieces from other parts

    ASCII case-insensitive matching
    : comparing a sequence of code points as if all ASCII code points in the range 0x41 to 0x5A (A to Z) were mapped to the corresponding code points in the range 0x61 to 0x7A (a to z)
    
    Note 1 to entry: The ASCII code points shall be as defined by ANSI/INCITS 4-1986.
    
    Media Types stream
    : stream (3.1.2) in a physical package (3.3.2) representing an XML document that specifies the media type of each part (3.2.1) in the package

### 3.4 数字签名和缩略图

=== "中文"

    **签名策略**(signature policy)
    : 规范签名中包含哪些部件(Part)和关系（relationship）以及生成和验证签名需要哪些附加行为
    
    **缩略图**(thumbnail)
    : 小图像，是部件(Part)或整个包(Package)的图形表示

=== "英文"

    **Digital signature and thumbnail**

    signature policy
    : specification of what parts (3.2.1) and relationships (3.2.3) are included in a signature and what additional behaviors are required for generating and validating signatures
    
    thumbnail
    : small image that is a graphical representation of a part (3.2.1) or the package as a whole

### 3.5 具体实现

=== "中文"

    **包实现者**(package implementer)
    : 根据本文档的要求和建议对包实现物理输入输出操作的软件

=== "英文"

    **Implementations**

    package implementer
    : software that implements physical input-output operations on a package according to the requirements and recommendations of this document

### 3.6 核心属性

=== "中文"

    **核心属性**(core property)
    : 一个包(package)的属性

=== "英文"

    **Core properties**

    
    **core property**
    : property of a package

## 4. 一致性

=== "中文"

    如果一个包遵守本文档中指定的所有语法约束，则该包属于 OPC 一致性类。 OPC 一致性纯粹是语法上的。

=== "英文"

    **Conformance**

    A package is of conformance class OPC if it obeys all syntactic constraints specified in this document. OPC conformance is purely syntactic.

## 5. 概述

=== "中文"

    本文档描述了一个抽象包模型（[第 6 条]）和一个物理包模型（[第 7 条]），用于使用 XML、Unicode、ISO/IEC 10646（参见参考文献[^7]）、ZIP 以及其他相关技术和规范来组织包(package)内文档的内容和资源。 包结构旨在支持各种应用程序和内容类别的组成资源的组织。 [附录 H] 中显示了一个示例包。
    
    抽象包模型是包含部件和关系的集合的包抽象。 这些部件根据一组规则进行组合、处理和保存。 部件可以与其他部件或外部资源有关系，并且包作为一个整体可以与其包含的部件或外部资源有关系。 部件具有 MIME 媒体类型，并使用本文档中提供的明确定义的命名规则进行唯一标识。
    
    物理包模型定义了抽象包模型的组件到特定物理格式（即ZIP文件）的特征的映射。
    
    本文档还描述了其他功能，包括包元数据的核心属性、包图形表示的缩略图以及包内容的数字签名。 本文档依赖于 ECMA-376-3 来允许 OPC 的未来扩展，而不会引入兼容性问题。
    
    本文件规定了包的要求。 本文档中明确了一致性要求。 [第 4 条]给出了正式的一致性声明。

=== "英文"

    **Overview**

    This document describes an abstract package model (Clause 6) and a physical package model (Clause 7) for the use of XML, Unicode, ISO/IEC 10646 (see Reference [^7]), ZIP, and other relevant technologies and specifications to organize the content and resources of a document within a package. The package structure is intended to support the organization of constituent resources for various applications and categories of content. An example package is shown in Annex H.
    
    The abstract package model is a package abstraction that holds a collection of parts and relationships. The parts are composed, processed, and persisted according to a set of rules. Parts can have relationships to other parts or external resources, and the package as a whole can have relationships to parts it contains or to external resources. Parts have MIME media types and are uniquely identified using the well-defined naming rules provided in this document.
    
    The physical package model defines the mapping of the components of the abstract package model to the features of a specific physical format, namely a ZIP file.
    
    This document also describes other features, including core properties for package metadata, a thumbnail for graphical representation of a package, and digital signatures of package contents. This document relies on ECMA-376-3 to allow future extensions of OPC without introducing compatibility problems.
    
    This document specifies requirements for packages. Conformance requirements are identified throughout this document. A formal conformance statement is given in Clause 4.

## 6. 抽象封装模型

**Abstract package model**

### 6.1 常规

=== "中文"

    本节介绍了部件（[6.2]）和关系（[6.5]）方面的抽象包。 它还介绍了打包方案（pack scheme）（[6.3.2]）。
    
    抽象包的目的是将文档（或其他类型的内容）的组成部分聚合到单个对象中。 例如，保存带有图片的文档的抽象包可以包含表示文档文本的 XML 标记部分和表示图片的另一部分。

    [H.2] 中显示了一个示例抽象包。

=== "英文"

    **General**

    This clause introduces abstract packages in terms of parts (6.2) and relationships (6.5). It also introduces the pack scheme (6.3.2).

    The purpose of an abstract package is to aggregate constituent components of a document (or other type of content) into a single object. For example, an abstract package holding a document with a picture can contain an XML markup part representing the text of the document and another part representing the picture.

    An example abstract package is shown in H.2.

### 6.2 部件

**Parts**

#### 6.2.1 常规

=== "中文"

    部件类似于文件系统中的文件或 HTTP 服务器上的资源。

=== "英文"

    A part is analogous to a file in a file system or to a resource on an HTTP server.

#### 6.2.2 部件名称

**Part names**

##### 6.2.2.1 常规

=== "中文"

    部件应具有部件名称(part name)，该名称应唯一标识(uniquely identify)抽象包中的部件。

=== "英文"

    **General**
    
    A part shall have a part name, which shall uniquely identify a part within an abstract package. 

##### 6.2.2.2 Syntax

=== "中文"

    部件名称(part name)应是 Unicode 字符串，与 RFC 5234 中定义的 ABNF 语法中的以下产生规则相匹配

    ```text
    part_name = 1*( "/" isegment-nz )
    isegment-nz = <isegment-nz, see RFC3987, Section 2.2>
    ```

    并且进一步满足下面列出的约束，其中 I18N 段是与非终结符 `isegment-nz` 匹配的 Unicode 字符串，并且百分比编码表示由百分比字符“`%`”后跟两个十六进制数字组成的字符，如指定的 在 RFC 3986 中
    
    - I18N 段不得包含百分比编码的正斜杠（“/”）或反斜杠（“\”）字符。
    - I18N 段不得包含与 RFC 3987 中的非终结符 `iunreserved` 匹配的百分比编码字符。
    - I18N 段不得以点（“`.`”）字符结尾。

    应保留([6.5.2.2])部件名称(part name)“`/_rels/.rels`”(6.5.2.2)。 倒数第二个 I18N 段相当于“`_rels`”且最后一个段相当于任何以“.rels`”结尾的字符串的部分名称应被保留（[6.5.2.3]）。

    !!! info "EXAMPLE 1"
    
        部件名称 “`/hello/world/doc.xml`” 包含三个路径段，即“`hello`”、“`world`”和“`doc.xml`”。
    
    !!! info "EXAMPLE 2"
    
        部分名称“`/é`”包含路径段“`é`”，其中 é 是“**LATIN SMALL LETTER E WITH ACUTE**”(U+00E9)。
    

    !!! Note "Note"

        路径段(Path segments)在抽象包模型中没有明确表示为文件夹，并且抽象包模型(abstract package model)中不存在文件夹目录。
    
    包实现者(package implementer)不需要支持非 ASCII 部分名称，但建议这样做。

=== "英文"

    **Syntax**

    A part name shall be a Unicode string that matches the following production rules in the ABNF syntax defined in RFC 5234

    ```text
    part_name = 1*( "/" isegment-nz )
    isegment-nz = <isegment-nz, see RFC3987, Section 2.2>
    ```

    and that further satisfies the constraints listed below, where an I18N segment is a Unicode string that
    matches the non-terminal `isegment-nz` and percent-encoding represents a character by the percent
    character "%" followed by two hexadecimal digits, as specified in RFC 3986
    
    - No I18N segments shall contain percent-encoded forward slash (“/”), or backward slash (“\”) characters.
    - No I18N segments shall contain percent-encoded characters that match the non-terminal `iunreserved` in RFC 3987.
    - No I18N segments shall end with a dot (“.”) character.

    The part name "`/_rels/.rels`" shall be reserved (6.5.2.2). Part names in which the second-to-last I18N segment is equivalent to "`_rels`" and the final segment is equivalent to any string ending with "`.rels`" shall be reserved ([6.5.2.3]).

    EXAMPLE 1 The part name "`/hello/world/doc.xml`" contains three path segments, namely, "`hello`", "`world`", and "`doc.xml`".
    
    EXAMPLE 2 The part name "`/é`" contains a path segment "`é`" where é is '*LATIN SMALL LETTER E WITH ACUTE*' (U+00E9).
    
    NOTE Path segments are not explicitly represented as folders in the abstract package model, and no directory of folders exists in the abstract package model.
    
    A package implementer is not required to support non-ASCII part names, although doing so is recommended.

##### 6.2.2.3 抽象包中的部件名称等效性和完整性

=== "中文"

    部件名称的等效性应通过 ASCII 不区分大小写的匹配来确定。 此类匹配会比较代码点序列，就好像 0x41–0x5A (A–Z) 范围内的所有 ASCII 代码点都映射到 0x61–0x7A (a–z) 范围内的相应代码点一样。 参见参考文献[^1]。

    抽象包(abstract package)中两个不同部件(part)的名称不应相同。

    !!! info "EXAMPLE 1"

        如果抽象包中包含名为“`/a`”的部分，则该抽象包中的其他部分的名称不能为“`/a`”或“`/A`”。

    对于每个部件名称 N 和字符串 S ，将 N、正斜杠和S连接的结果表示为 N[S] 。 如果对于某个字符串 S，N1 等于 N2[S]，则称部件名称 N1 可从另一个部件名称 N2 派生。

    !!! info "EXAMPLE 2"
    
        “`/a/b`”可以从“`/a`”导出，其中 N 是“`/a`”，S 是“`b`”。

    一个部件的名称不得源自另一个部件的名称。

    !!! info "EXAMPLE 3"
        
        假设抽象包包含名为“`/segment1/segment2/…/segmentn`”的部分。 为了使其不可导出，该抽象包中的其他部分不能具有诸如“`/segment1`”、“`/SEGMENT1`”、“`/segment1/segment2`”、“`/segment1/SEGMENT2`”之类的名称， 或“`/segment1/segment2/…/segmentn-1`”。

    本子条款进一步介绍了建议，以便部件名称的 Unicode 规范化形式 C (NFC) 和 Unicode 规范化形式 D (NFD) 不会导致部件名称冲突。 请注意，目录结构的某些实现始终应用 NFD 规范化。

    对抽象包中两个不同部分的名称应用 NFC 或 NFD 标准化不应产生等效的字符串。

    如果摘要包包含名为“`/é`”的部分，其中 é 是“LATIN SMALL LETTER E”(U+0065)，后跟 “COMBINING ACUTE ACCENT”(U+0301)，即该摘要中另一个部件的名称，包不应该是“`/é`”，其中 é 是“LATIN SMALL LETTER E WITH ACUTE”(U+00E9)，或“`/É`”，其中 É 是“**LATIN CAPITAL LETTER E WITH ACUTE**” '（U+00C9）。
    
    如果抽象包包含名为“`/Å`”的部分，其中 Å 是 '**ANGSTROM SIGN**' (U+212B)，则该抽象包中另一个部分的名称不应为“`/Å`” 其中 Å 是“**拉丁文大写字母 A，上面有环**”(U+00C5)，因为 U+212B 和 U+00C5 已标准化为相同的字符序列。

    如果对于某些字符串 S，将 NFC 或 NFD 应用到 N1 的结果等于将 NFC 或 NFD 应用到 N2[S] 的结果，则称部件名称 N1 可从另一个部件名称 N2 弱推导。

    !!! info "EXAMPLE 4"
    
        考虑一个部件名称“`/é`”，其中 é 是“**LATIN SMALL LETTER E WITH ACUTE**”(U+00E9)。 另一个部分名称“`/é/a`”，其中 é 是“**LATIN SMALL LETTER E**”(U+0065)，后跟“**COMBINING ACUTE ACCENT**”(U+0301)，可以从以下弱派生 “`/é`”。 另一个部件名称“`/É/a`”，其中 É 是“**LATIN CAPITAL LETTER E**”(U+0045)，后跟“**COMBINING ACUTE ACCENT**”(U+0301)，也是弱可推导的。

    一个部件的名称不应该是从另一个部件的名称弱推导出来的。

    假设抽象包包含名为“`/é/Å/foo`”的部分，其中 é 是“LATIN SMALL LETTER E WITH ACUTE”(U+00E9)，Å 是“ANGSTROM SIGN”(U+212B)。 为了使其不具有弱可导性，该抽象包中的其他部分不应具有诸如“`/É`”和“`/É/Å`”之类的名称，其中 É 是“LATIN CAPITAL LETTER E”(U+0045) 后跟“COMBINING ACUTE ACCENT”(U+0301)，Å 是“LATIN CAPITAL LETTER A WITH RING ABOVE”(U+00C5)。

=== "英文"

    **Part name equivalence and integrity in an abstract package**

    Equivalence of part names shall be determined by ASCII case-insensitive matching. Such matching compares a sequence of code points as if all ASCII code points in the range 0x41–0x5A (A–Z) were mapped to the corresponding code points in the range 0x61–0x7A (a–z). See Reference [^1].

    The names of two different parts within an abstract package shall not be equivalent.

    EXAMPLE 1 If an abstract package contains a part named "`/a`", the name of another part in that abstract package cannot be "`/a`" or "`/A`".

    For each part name N and string S, let the result of concatenating N, the forward slash, and S be denoted by N[S]. A part name N1 is said to be derivable from another part name N2 if, for some string S, N1 is equivalent to N2[S].

    EXAMPLE 2 "`/a/b`" is derivable from "`/a`", where N is "`/a`" and S is "`b`".

    The name of a part shall not be derivable from the name of another part.

    EXAMPLE 3 Suppose that an abstract package contains a part named "`/segment1/segment2/…/segmentn`". For it not to be derivable, other parts in that abstract package cannot have names such as "`/segment1`", "`/SEGMENT1`", "`/segment1/segment2`", "`/segment1/SEGMENT2`", or "`/segment1/segment2/…/segmentn-1`".

    This subclause further introduces recommendations, so that Unicode Normalization Form C (NFC) and Unicode Normalization Form D (NFD) of part names do not cause part-name collisions. Note that some implementations of directory structures always apply NFD normalization.

    The application of NFC or NFD normalization to the names of two different parts within an abstract package should not yield equivalent strings.

    If an abstract package contains a part named "`/é`", where é is 'LATIN SMALL LETTER E' (U+0065) followed by 'COMBINING ACUTE ACCENT' (U+0301), the name of another part in that abstract package should not be "`/é`", where é is 'LATIN SMALL LETTER E WITH ACUTE' (U+00E9), or "`/É`", where É is '**LATIN CAPITAL LETTER E WITH ACUTE**'(U+00C9).

    If an abstract package contains a part named "`/Å`", where Å is '**ANGSTROM SIGN**' (U+212B), the name of another part in that abstract package should not be "`/Å`" where Å is '**LATIN CAPITAL LETTER A WITH RING ABOVE**' (U+00C5) because U+212B and U+00C5 are normalized to the same character sequence.

    A part name N1 is said to be weakly derivable from another part name N2 if, for some string S, the result of applying NFC or NFD to N1 is equivalent to the result of applying NFC or NFD to N2[S].

    EXAMPLE 4 Consider a part name "`/é`", where é is '**LATIN SMALL LETTER E WITH ACUTE**' (U+00E9). Another part name "`/é/a`", where é is '**LATIN SMALL LETTER E**' (U+0065) followed by '**COMBINING ACUTE ACCENT**' (U+0301) is weakly derivable from "`/é`". Another part name "`/É/a`", where É is '**LATIN CAPITAL LETTER E**' (U+0045) followed by '**COMBINING ACUTE ACCENT**' (U+0301) is also weakly derivable.

    The name of a part should not be weakly derivable from the name of another part.

    Suppose that an abstract package contains a part named "`/é/Å/foo`", where é is 'LATIN SMALL LETTER E WITH ACUTE' (U+00E9) and Å is 'ANGSTROM SIGN' (U+212B). For it not to be weakly derivable, no other parts in that abstract package should have names such as "`/É`" and "`/É/Å`", where É is 'LATIN CAPITAL LETTER E' (U+0045) followed by 'COMBINING ACUTE ACCENT' (U+0301) and Å is 'LATIN CAPITAL LETTER A WITH RING ABOVE' (U+00C5).

#### 6.2.3 媒体类型

=== "中文"

    每个部件(part)应具有一个 MIME 媒体类型（如 RFC 2046 中定义），以标识该部分中的内容类型，由顶级媒体类型和子类型组成，可选地由一组参数限定。 本文档中定义的 OPC 特定部分的媒体类型不应包含参数。
    
    本文档中定义的部件的媒体类型列于[附录 E] 中。

=== "英文"

    **Media types**

    Each part shall have a MIME media type, as defined in RFC 2046, to identify the type of content in that part, consisting of a top-level media type and a subtype, optionally qualified by a set of parameters. Media types of OPC-specific parts defined in this document shall not contain parameters.
    
    Media types for parts defined in this document are listed in Annex E.

#### 6.2.4 成长提示

=== "中文"

    某个部件(part)可能有成长提示。

    有时，物理封装中的某个部件会被修改并需要变得更大。 对于某些物理格式，创建包含较大部分的新物理包是一项昂贵的操作。 为了允许该部分在适当的位置增长，移动尽可能少的字节，可以使用增长提示来保留映射到特定物理格式的空间。

=== "英文"

    **Growth hint**

    A part may have a growth hint.

    Sometimes a part in a physical package is modified and needs to become larger. For some physical formats, creating a new physical package that contains the larger part is an expensive operation. To allow the part to grow in place, moving as few bytes as possible, the growth hint may be used to reserve space in a mapping to a particular physical format.

#### 6.2.5 XML的使用

=== "中文"

    本文档中定义的部件(part)和流（具体来说，**媒体类型流**(Media Types stream)、**核心属性部件**(Core Properties part)、**数字签名 XML 签名部件**(Digital Signature XML Signature parts)和**关系部件**(Relationships parts)）中的 XML 内容应符合以下要求：

    a) XML 内容应使用 UTF-8 或 UTF-16 进行编码。 如果任何部分包含编码声明（如 XML 1.0 规范 4.3.3 中所定义），则该声明不得命名除 UTF-8 或 UTF-16 之外的任何编码。

    b) XML 1.0 规范允许使用文档类型定义 (DTD)，这通常会通过使用内部实体扩展技术来实现拒绝服务攻击。 为了缓解这种潜在威胁，DTD 声明不应在本文档定义的 XML 标记中使用。

    c) XML 文档应符合 XML 命名空间。

    d) 根据 **W3C XML Schema 结构** 和 **W3C XML Schema 数据类型** 的定义，相对于本文档[附录 C] 中定义的相应 XSD Schema，XML 内容应是模式(schema)有效的。 特别是，XML 内容不应包含从相应 XSD 模式中未明确定义的名称空间提取的元素或属性，除非 XSD 模式允许从任何名称空间提取的元素或属性出现在 XML 标记中的特定位置。

    e) XML 内容不得包含从“`xml`”或“`xsi`”命名空间提取的元素或属性，除非它们在 XSD 架构中或通过本文档中描述的其他方式明确定义。

=== "英文"

    **XML usage**

    XML content in parts and streams defined in this document (specifically, the Media Types stream, the Core Properties part, Digital Signature XML Signature parts, and Relationships parts) shall conform to the following:

    a) XML content shall be encoded using either UTF-8 or UTF-16. If any part includes an encoding declaration, as defined in 4.3.3 of the XML 1.0 specification, that declaration shall not name any encoding other than UTF-8 or UTF-16.

    b) The XML 1.0 specification allows for the usage of Document Type Definitions (DTDs), which enable Denial of Service attacks, typically through the use of an internal entity expansion technique. As mitigation for this potential threat, DTD declarations shall not be used in the XML markup defined in this document.

    c) XML documents shall conform to XML Namespaces.

    d) XML content shall be schema-valid, as defined by W3C XML Schema Structures and W3C XML Schema Datatypes, with respect to the corresponding XSD schema defined in Annex C of this document. In particular, the XML content shall not contain elements or attributes drawn from namespaces that are not explicitly defined in the corresponding XSD schema unless the XSD schema allows elements or attributes drawn from any namespace to be present in particular locations in the XML markup.

    e) XML content shall not contain elements or attributes drawn from “xml” or “xsi” namespaces unless they are explicitly defined in the XSD schema or by other means described in this document.

### 6.3 部件寻址

**Part addressing**

#### 6.3.1 常规

=== "中文"

    本文档提供包方案作为使用 IRI (RFC 3987) 引用包内部件资源的一种方式。
    
    方案在 IRI 中由冒号之前的前缀表示。 一个众所周知的例子是“http”。

    !!! info "EXAMPLE" 
    
        包方案中的 IRI 示例如下：

        "`pack://http%3c,,www.openxmlformats.org,my.container/a/b/foo.xml`"
    
    双斜杠和第一个单斜杠之间的子字符串表示包的 http 方案中的 IRI，经过转换以允许嵌入包方案中的 IRI。

    来自包外部的引用是包方案的绝对 IRI，而来自包内部的引用是相对 IRI，它们被解析为该方案的绝对 IRI。

=== "英文"

    **General**

    This document provides the pack scheme as a way to use IRIs (RFC 3987) to reference part resources inside a package.

    Schemes are represented in an IRI by the prefix before the colon. A well-known example is "http".

    EXAMPLE An example of an IRI in the pack scheme is:

    "`pack://http%3c,,www.openxmlformats.org,my.container/a/b/foo.xml`"
    
    The substring between the double slash and the first single slash represents an IRI in the http scheme for a package, transformed to allow embedding within an IRI in the pack scheme.

    References from outside of a package are absolute IRIs of the pack scheme, while those from inside are relative IRIs, which are resolved to absolute IRIs of this scheme.

#### 6.3.2 打包方案

=== "中文"

    本文档定义了用于引用包中部件的特定方案：pack 方案。 使用 Pack 方案的 IRI 称为 Pack IRI。

    Pack IRI 的语法在 EBNF（参见 RFC 5234）中定义如下：

    ```text
    pack_IRI    = "pack://" iauthority [ "/" | ipath ]
    iauthority  = *( iunreserved | sub-delims | pct-encoded )
    ipath       = 1*( "/" isegment )
    isegment    = 1*( ipchar )
    ipchar      = <ipchar, see [RFC3987], Section 2.2>
    iunreserved = <iunreserved, see [RFC3987], Section 2.2>
    sub-delims  = <sub-delims, see [RFC3986], Section 2.2>
    pct-encoded = <pct-encoded, see [RFC3986], Section 2.1>
    ```

    权限组件 (iauthority) 包含指向包的嵌入式 IRI。 （有关转换包的 IRI 以允许将 IRI 作为权限组件嵌入到包中的过程，请参见[第 6.3.4 节]。）权限组件不应引用嵌入到另一个包中的包(package)。

    !!! note "NOTE" 
    
        权限组件的定义要求将冒号字符 (:) 转义为 `%3c`。 然而，在提议的包方案注册中，错误地使用了未转义的冒号 (:) 字符。 由于这个错误，临时包方案被 IANA 注册为历史方案。 可以在 IANA 维护的方案注册表中检查包方案（请参阅参考文献 [^8]）。

    可选路径组件 (ipath) 标识包中的特定部分。 当路径组件丢失时，包 IRI 标识的资源是整个包。

    Pack IRI 可以有一个查询组件（如 RFC 3986 中指定）。 将 IRI 解析为部件时，不使用包 IRI 中的查询组件。

    Pack IRI 可以具有片段组件（如 RFC 3986 中指定）。 如果存在，则此片段适用于包 IRI 标识的任何资源。

    !!! info "EXAMPLE 1: 使用包 IRI 来识别部件" 

        以下 IRI 标识 “http://www.openxmlformats.org/my.container” 包资源中的 “/a/b/foo.xml” 部分：

        "pack://http%3c,,www.openxmlformats.org,my.container/a/b/foo.xml"

    !!! info "EXAMPLE 2: 等效包 IRI" 

        以下包 IRI 是等效的：

        "pack://http%3c,,www.openxmlformats.org,my.container"
        
        "pack://http%3c,,www.openxmlformats.org,my.container/"

    !!! info "EXAMPLE 3: 带有百分比编码字符的 IRI 包"

        以下 IRI 标识 “http://myalias:pswr@www.my.com/containers.aspx?my.container” 包中的 “/c/d/bar.xml” 部分：
    
        "pack://http%3c,,myalias%3cpswr%40www.my.com,containers.aspx%3fmy.container/c/d/bar.xml"

=== "英文"

    **Pack scheme**

    This document defines a specific scheme used to refer to parts in a package: the pack scheme. An IRI that uses the pack scheme is called a pack IRI.

    The syntax of pack IRIs is defined in EBNF (see RFC 5234) as follows:

    ```text
    pack_IRI = "pack://" iauthority [ "/" | ipath ]
    iauthority = *( iunreserved | sub-delims | pct-encoded )
    ipath = 1*( "/" isegment )
    isegment = 1*( ipchar )
    ipchar = <ipchar, see [RFC3987], Section 2.2>
    iunreserved = <iunreserved, see [RFC3987], Section 2.2>
    sub-delims = <sub-delims, see [RFC3986], Section 2.2>
    pct-encoded = <pct-encoded, see [RFC3986], Section 2.1>
    ```

    The authority component (iauthority) contains an embedded IRI that points to a package. (See 6.3.4 for the procedure for transforming the IRI for the package to permit embedding in the pack IRI as the authority component.) The authority component shall not reference a package embedded in another package.

    NOTE The definition of the authority component requires that the colon character (:) be escaped as %3c. However, in the proposed registration of the pack scheme, an unescaped colon (:) character was mistakenly used. Due to this mistake, the provisional pack scheme was registered by IANA as a historical scheme. The pack scheme can be inspected in the IANA-maintained registry of schemes (see Reference [^8]).

    The optional path component (ipath) identifies a particular part within the package. When the path component is missing, the resource identified by the pack IRI is the package as a whole.

    A pack IRI can have a query component (as specified in RFC 3986). A query component in a pack IRI is not used when resolving the IRI to a part.

    A pack IRI can have a fragment component (as specified in RFC 3986). If present, this fragment applies to whatever resource the pack IRI identifies.

    EXAMPLE 1 Using the pack IRI to identify a part

    The following IRI identifies the "/a/b/foo.xml" part within the "http://www.openxmlformats.org/my.container" package resource:

        "pack://http%3c,,www.openxmlformats.org,my.container/a/b/foo.xml"

    EXAMPLE 2 Equivalent pack IRIs

    The following pack IRIs are equivalent:

        "pack://http%3c,,www.openxmlformats.org,my.container"
        "pack://http%3c,,www.openxmlformats.org,my.container/"

    EXAMPLE 3 A pack IRI with percent-encoded characters

    The following IRI identifies the "/c/d/bar.xml" part within the "http://myalias:pswr@www.my.com/containers.aspx?my.container" package:

    "pack://http%3c,,myalias%3cpswr%40www.my.com,containers.aspx%3fmy.container/c/d/bar.xml"

#### 6.3.3 将包 IRI 解析为资源

=== "中文"

    应使用以下算法将包 IRI 解析为资源（包或部件）：
    
    a) 将包 IRI 解析为可能的三个组件：方案(scheme)、权限(authority)、路径(path)以及任何片段标识符(fragment identifier)。 
    
    b) 在权限(authority)组件中，将所有逗号（“,”）替换为正斜杠（“/”）。
    
    c) 在生成的权限组件中取消对 ASCII 字符进行百分比编码。
    
    d) 生成的权限组件应是整个包的有效 IRI。 如果不是，则包 IRI 无效。
    
    e) 如果路径组件为空，则包 IRI 将解析为整个包，并且解析过程完成。
    
    f) 非空路径组件应是有效的部件名称。 如果不是，则包 IRI 无效。
    
    g) Pack IRI 解析为由权威组件标识的包中具有该部件名称的部件。

    !!! info "EXAMPLE: 将包 IRI 解析为资源"

        给定包 IRI:
        
            "pack://http%3c,,www.my.com,packages.aspx%3fmy.package/a/b/foo.xml"
    
        组件:
        
            "<authority>= http%3c,,www.my.com,packages.aspx%3fmy.package"
            "<path>= /a/b/foo.xml"
    
        转换为IRI包：
        
            "http://www.my.com/packages.aspx?my.package"
    
        和路径:
            
            "/a/b/foo.xml"
    
        因此，此 IRI 引用以下 IRI 处的包中名为“/a/b/foo.xml”的部件：
        
            "http://www.my.com/packages.aspx?my.package".

=== "英文"

    **Resolving a pack IRI to a resource**

    The following algorithm shall be used to resolve a pack IRI to a resource (either a package or a part):
    
    a) Parse the pack IRI into the potential three components: scheme, authority, path, as well as any fragment identifier.
    
    b) In the authority component, replace all commas (“,”) with forward slashes (“/”).
    
    c) Un-percent-encode ASCII characters in the resulting authority component.
    
    d) The resultant authority component shall be a valid IRI for the package as a whole. If it is not, the pack IRI is invalid.
    
    e) If the path component is empty, the pack IRI resolves to the package as a whole and the resolution process is complete.
    
    f) A non-empty path component shall be a valid part name. If it is not, the pack IRI is invalid.
    
    g) The pack IRI resolves to the part with this part name in the package identified by the authority component.

    EXAMPLE Resolving a pack IRI to a resource

    Given the pack IRI:
    
        "pack://http%3c,,www.my.com,packages.aspx%3fmy.package/a/b/foo.xml"
    
    The components:
    
        "<authority>= http%3c,,www.my.com,packages.aspx%3fmy.package"
        "<path>= /a/b/foo.xml"
    
    are converted to the package IRI:
    
        "http://www.my.com/packages.aspx?my.package"
    
    and the path:
        
        "/a/b/foo.xml"
    
    Therefore, this IRI refers to a part named "/a/b/foo.xml" in the package at the following IRI: 
    
    "http://www.my.com/packages.aspx?my.package".

#### 6.3.4 编写 IRI 包

=== "中文"

    应使用以下算法从整个包的绝对 IRI 和部件名称组成包 IRI：

    a) 从绝对包 IRI 中删除片段标识符（如果存在）。
    
    b) 对包 IRI 中的所有百分号 (“%”)、问号 (“?”)、@ 符号 (“@”)、冒号 (“:”) 和逗号 (“,”) 进行百分比编码。
    
    c) 将结果字符串中的所有正斜杠（“/”）替换为逗号（“,”）。
    
    d) 将生成的字符串附加到字符串“pack://”。
    
    e) 将正斜杠（“/”）附加到结果字符串中。 构造的字符串表示具有空白路径组件的包 IRI。
    
    f) 使用此构造的字符串作为基本 IRI 并将部件名称作为相对引用，应用 RFC 3986 中定义的规则来解析针对基本 IRI 的相对引用。
    
    !!! info "EXAMPLE: 编写 IRI 包"

        给定包 IRI:
        
            "http://www.my.com/packages.aspx?my.package"
    
        和部件名称:
            
            "/a/foo.xml"
    
        该包是 IRI:
        
            "pack://http%3c,,www.my.com,packages.aspx%3fmy.package/a/foo.xml"

=== "英文"

    **Composing a pack IRI**

    The following algorithm shall be used to compose a pack IRI from the absolute IRI of an entire package and a part name:

    a) Remove the fragment identifier from the absolute package IRI, if present.
    
    b) Percent-encode all percent signs (“%”), question marks (“?”), at signs (“@”), colons (“:”) and commas (“,”) in the package IRI.
    
    c) Replace all forward slashes (“/”) with commas (“,”) in the resulting string.
    
    d) Append the resulting string to the string "pack://".
    
    e) Append a forward slash (“/”) to the resulting string. The constructed string represents a pack IRI with a blank path component.
    
    f) Using this constructed string as a base IRI and the part name as a relative reference, apply the rules defined in RFC 3986 for resolving relative references against the base IRI.
    
    EXAMPLE Composing a pack IRI

    Given the package IRI:
    
        "http://www.my.com/packages.aspx?my.package"
    
    and the part name:
        
        "/a/foo.xml"
    
    The pack IRI is:
    
        "pack://http%3c,,www.my.com,packages.aspx%3fmy.package/a/foo.xml"

#### 6.3.5 等效性

=== "中文"

    在以下情况下，两个包 IRI 应被视为等效：

    a) 方案组成部分在都转换为小写后是逐个八位组相同的； 和
    
    b) 按照 [6.3.3] 中所述从权限组件中解码的 IRI 是等效的（方案(schema)的等效规则），如 RFC 3986 中指定的； 和
    
    c) 路径组件是等效的部件名称，如 [6.2.2] 中所指定。
    
    !!! note "NOTE" 
    
        在某些场景中，例如缓存或将部件写入包中，需要确定两个包 IRI 是否等效而不解析它们。

=== "英文"

    **Equivalence**

    Two pack IRIs shall be treated as equivalent if:
    
    a) The scheme components are octet-by-octet identical after they are both converted to lowercase; and
    
    b) The IRIs, decoded as described in 6.3.3 from the authority components, are equivalent (the equivalency rules by scheme), as specified in RFC 3986; and
    
    c) The path components are equivalent part names, as specified in 6.2.2.
    
    NOTE In some scenarios, such as caching or writing parts to a package, it is necessary to determine if two pack IRIs are equivalent without resolving them.

### 6.4 解决相关引用

    **Resolving relative references**

#### 6.4.1 常规

=== "中文"

    部件中的相对引用应按照 RFC 3986（5 引用解析）中的规定进行解析，并在 RFC 3987（6.5 相对 IRI 引用）中进行扩展。

    本文件没有对解析程序进行任何更改，但[附录 A] 介绍了建议的用于生成相关参考的预处理方法。

=== "英文"

    **General**

    Relative references in parts shall be resolved as specified in RFC 3986 (5 Reference Resolution), as extended in RFC 3987 (6.5 Relative IRI References).

    This document introduces no changes to the resolution procedure, but Annex A introduces a suggested preprocessing method for generating relative references.

#### 6.4.2 基础 IRI

=== "中文"

    本节定义了确定基本 IRI 的过程，以解析包中部件内的相对引用。

    !!! note "NOTE" 
    
        RFC 3986，5.1 建立基本 URI，按照优先顺序提供了四种通用方法，用于建立基本 IRI 以解析相对引用。 本节中的过程提供了与第二个通用方法（RFC 3986，5.1.2 来自封装实体的基本 URI）相对应的 OPC 特定方法。

    基本 IRI 取决于该引用在包中出现的位置。 本小节涵盖了相对引用出现在不是关系部件的部件中的情况。 [6.5.2] 涵盖了关系部分中出现相对引用的情况。

    基本 IRI 应是根据包的 IRI 和发生相对引用的部分的名称创建的包 IRI。

    考虑位于以下​​位置的包中的一部件: `/a/b/foo.xml`
    
    "`http://www.mysite.com/my.package`"

    基本 IRI 是
    
    "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"

=== "英文"

    **Base IRIs**

    This subclause defines a procedure for determining base IRIs for resolving relative references within parts
    in packages.

    NOTE RFC 3986, 5.1 Establishing a Base URI, provides four general methods, in order of precedence, for establishing base IRIs for resolving relative references. The procedure in this subclause provides an OPC-specific method corresponding to the second general method (RFC 3986, 5.1.2 Base URI from the Encapsulating Entity).

    The base IRI depends on where that reference occurs within the package. This subclause covers the case where a relative reference occurs in a part that is not a Relationships part. 6.5.2 covers the case where a relative reference occurs in a Relationships part.

    The base IRI shall be the pack IRI created from the IRI of the package and the name of the part within which the relative reference occurs. 

    Consider a part /a/b/foo.xml in a package located at
    
    "`http://www.mysite.com/my.package`"

    The base IRI is
    
    "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"

#### 6.4.3 例子

**Examples**

##### 6.4.3.1 常规

=== "中文"

    本小节显示了解析相对引用的示例。 对于每个示例，本节考虑三种情况。
    
    情况 1：基础 IRI 是一个包 IRI，“`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`”，它是由绝对 IRI 构造而成封装和部件名称。
    
    情况 2: 基本 IRI 是一个包 IRI，“`pack://http%3c,,www.mysite.com,my.package/`”，它是根据包的绝对 IRI 创建的。
    
    情况 3: 基本 IRI 是包 “`http://www.mysite.com/my.package`” 的绝对 IRI。

=== "英文"

    **General**

    This subclause shows examples of resolving relative references. For each example, this subclause considers three cases.
    
    Case 1: the base IRI is a pack IRI, "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`", which is constructed from an absolute IRI of the package and a part name.
    
    Case 2: the base IRI is a pack IRI, "`pack://http%3c,,www.mysite.com,my.package/`", which is created from an absolute IRI of the package.
    
    Case 3: the base IRI is the absolute IRI of the package, "http://www.mysite.com/my.package".

##### 6.4.3.2 前导斜线: "/b/bar.xml"

=== "中文"

    情况 1：基本 IRI 为“`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`”。
    
    由于此相对引用以斜杠字符开头，因此 RFC 3986 5.2.2 中的算法会忽略基本 IRI (“/a/b/foo.xml”) 的路径组件。生成的 IRI 的方案和权限与基础包 IRI 的相同。 因此，得到的 IRI 为：
    
    "`pack://http%3c,,www.mysite.com,my.package/b/bar.xml`"
    
    情况 2: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/`"
    
    同样，基本 IRI 的路径部分（“/”）也被忽略。 其余的都是一样的。
    
    情况 3: 基本 IRI 是 "`http://www.mysite.com/my.package`"
    
    同样，基本 IRI 的路径部分（“/my.package”）将被忽略。 因此，得到的 IRI 为：
    
    "`http://www.mysite.com/b/bar.xml`"

=== "英文"

    **Leading slash: "`/b/bar.xml`"**

    Case 1: The base IRI is "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`".
    
    Since this relative reference begins with the slash character, the path component of the base IRI ("/a/b/foo.xml") is ignored by the algorithm in 5.2.2 of RFC 3986. The scheme and authority of the resulting IRI are the same as those of the base pack IRI. Thus, the resulting IRI is:
    
    "`pack://http%3c,,www.mysite.com,my.package/b/bar.xml`"
    
    Case 2: The base IRI is "`pack://http%3c,,www.mysite.com,my.package/`"
    
    Likewise, the path component of the base IRI ("/") is ignored. The rest is the same.
    
    Case 3: The base IRI is "`http://www.mysite.com/my.package`"
    
    Likewise, the path component of the base IRI ("/my.package") is ignored. Thus, the resulting IRI is:
    
    "`http://www.mysite.com/b/bar.xml`"

##### 6.4.3.3 没有前导斜杠: "bar.xml"

=== "中文"

    情况 1: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"

    由于此相对引用不以斜杠字符开头，因此基本 IRI 的路径组件（“`/a/b/foo.xml`”）和相对引用的路径组件（“`bar.xml`”）将被合并。 RFC 3986 的 5.2.3 中的合并例程首先从基本 IRI 的路径组件中删除“foo.xml”，并发出“/a/b/bar.xml”。 因此，得到的 IRI 为：
    
    "`pack://http%3c,,www.mysite.com,my.package/a/b/bar.xml`"

    情况 2: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/`"

    同样，基本 IRI 的路径组件（“`/`”）和相对引用的路径组件（“`bar.xml`”）也被合并。 合并例程发出“`/bar.xml`”。 因此，得到的 IRI 为：

    "pack://http%3c,,www.mysite.com,my.package/bar.xml"

    情况 3: 基本 IRI 是 "`http://www.mysite.com/my.package`"

    同样，基本 IRI 的路径组件（“`/my.package`”）和相对引用的路径组件（“`bar.xml`”）也被合并。 合并例程首先从基本 IRI 的路径组件中删除“`my.package`”，并发出“`/bar.xml`”。 因此，得到的 IRI 为：
    
    "`http://www.mysite.com/bar.xml`"

=== "英文"

    **No leading slash: "bar.xml"**

    Case 1: The base IRI is "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"

    Since this relative reference does not begin with the slash character, the path component of the base IRI ("/a/b/foo.xml") and that of the relative reference ("bar.xml") are merged. The merge routine in 5.2.3 of RFC 3986 first removes "foo.xml" from the path component of the base IRI, and emits "/a/b/bar.xml". Thus, the resulting IRI is:
    
    "`pack://http%3c,,www.mysite.com,my.package/a/b/bar.xml`"

    Case 2: The base IRI is "`pack://http%3c,,www.mysite.com,my.package/`"

    Likewise, the path component of the base IRI ("/") and that of the relative reference ("bar.xml") are merged. The merge routine emits "/bar.xml". Thus, the resulting IRI is:

    "`pack://http%3c,,www.mysite.com,my.package/bar.xml`"

    Case 3: The base IRI is "`http://www.mysite.com/my.package`"

    Likewise, the path component of the base IRI ("/my.package") and that of the relative reference ("bar.xml") are merged. The merge routine first removes "my.package" from the path component of the base IRI, and emits "/bar.xml". Thus, the resulting IRI is:
    
    "`http://www.mysite.com/bar.xml`"

##### 6.4.3.4 点段: "./bar.xml"

=== "中文"

    情况 1: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"
    
    与 [6.4.3.3] 中一样，合并例程从基本 IRI 的路径组件中删除“`foo.xml`”，并发出“`/a/b/./bar.xml`”。 但是 RFC 3986 的 5.2.4 中的 `remove_dot_segments` 例程删除了“`./`”并发出“`/a/b/bar.xml`”。 因此，得到的 IRI 为：
    
    "`pack://http%3c,,www.mysite.com,my.package/a/b/bar.xml`"
    
    情况 2: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/`"
    
    合并例程发出“`/./bar.xml`”，但`remove_dot_segments`例程删除“`./`”并发出“`/bar.xml`”。 因此，得到的 IRI 为：
    
    "`pack://http%3c,,www.mysite.com,my.package/bar.xml`"
    
    情况 3: 基本 IRI 是 "`http://www.mysite.com/my.package`"
    
    同样，基本 IRI 的路径组件（“`/my.package`”）和相对引用的路径组件（“`./bar.xml`”）也被合并。 合并例程首先从基本 IRI 的路径组件中删除“`my.package`”，并发出“`/./bar.xml`”。 但 `remove_dot_segments` 例程会删除“`./`”并发出“`/bar.xml`”。 因此，得到的 IRI 为：
    
    "`http://www.mysite.com/bar.xml`"

=== "英文"

    **Dot segment: "./bar.xml"**

    Case 1: The base IRI is "pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml"
    
    As in 6.4.3.3, the merge routine removes "foo.xml" from the path component of the base IRI, and emits "/a/b/./bar.xml". But the remove_dot_segments routine in 5.2.4 of RFC 3986 removes "./" and emits "/a/b/bar.xml". Thus, the resulting IRI is:
    
    "pack://http%3c,,www.mysite.com,my.package/a/b/bar.xml"
    
    Case 2: The base IRI is "pack://http%3c,,www.mysite.com,my.package/"
    
    The merge routine emits "/./bar.xml" but the remove_dot_segments routine removes "./" and emits "/bar.xml". Thus, the resulting IRI is:
    
    "pack://http%3c,,www.mysite.com,my.package/bar.xml"
    
    Case 3: The base IRI is "http://www.mysite.com/my.package"
    
    Likewise, the path component of the base IRI ("/my.package") and that of the relative reference ("./bar.xml") are merged. The merge routine first removes "my.package" from the path component of the base IRI, and emits "/./bar.xml". But the remove_dot_segments routine removes "./" and emits "/bar.xml". Thus, the resulting IRI is:
    
    "http://www.mysite.com/bar.xml"

##### 6.4.3.5 点段: "../bar.xml"

=== "中文"

    情况 1: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`" 合并例程发出 "`/a/b/../bar.xml`" 但 `remove_dot_segments` 例程删除了“`b/..`”。 因此，得到的 IRI 为：

    "`pack://http%3c,,www.mysite.com,my.package/a/bar.xml`"
    
    情况 2: 基本 IRI 是 "`pack://http%3c,,www.mysite.com,my.package/`"
    
    合并例程发出“`/../bar.xml`”，但 `remove_dot_segments` 例程将“`/../`”替换为“`/`”。 因此，得到的 IRI 为：
    
    "`pack://http%3c,,www.mysite.com,my.package/bar.xml`"
    
    情况 3: 基本 IRI 是 "`http://www.mysite.com/my.package`"
    
    同样，基本 IRI 的路径组件（“`/my.package`”）和相对引用的路径组件（“`../bar.xml`”）也被合并。 合并例程首先从基本 IRI 的路径组件中删除“`my.package`”，并发出“`/../bar.xml`”。 `remove_dot_segments` 例程将“`/../`”替换为“`/`”并发出“`/bar.xml`”。 由此产生的 IRI 为：
    
    "`http://www.mysite.com/bar.xml`"

=== "英文"

    **Dot segment: "../bar.xml"**

    Case 1: The base IRI is "pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml" The merge routine emits "/a/b/../bar.xml" but the remove_dot_segments routine removes "b/..". Thus, the resulting IRI is:

    "pack://http%3c,,www.mysite.com,my.package/a/bar.xml"
    
    Case 2: The base IRI is "pack://http%3c,,www.mysite.com,my.package/"
    
    The merge routine emits "/../bar.xml", but the remove_dot_segments routine replaces "/../" by "/". Thus, the resulting IRI is:
    
    "pack://http%3c,,www.mysite.com,my.package/bar.xml"
    
    Case 3: The base IRI is "http://www.mysite.com/my.package"
    
    Likewise, the path component of the base IRI ("/my.package") and that of the relative reference ("../bar.xml") are merged. The merge routine first removes "my.package" from the path component of the base IRI, and emits "/../bar.xml". The remove_dot_segments routine replaces "/../" by "/" and emits "/bar.xml". The resulting IRI is:
    
    "http://www.mysite.com/bar.xml"

### 6.5 关系

**Relationships**

#### 6.5.1 常规

=== "中文"

    部件可能包含对包中其他部件以及包外资源的引用。 这些引用在引用部分内以特定于该部分的媒体类型的方式表示，即以任意标记或应用程序定义的编码。 这有效地向不了解包含此类引用的部件的媒体类型的应用程序隐藏了部件之间的链接。

    本文档引入了一种间接机制来描述部件对其他部件或外部资源的引用，即关系。 关系(Relationships)表示从源部件或源包到目标部件或目标资源的连接。 来自部件的关系称为部件关系，来自包的关系称为包关系。 关系使连接可以直接发现，而无需查看部件内容，因此它们独立于特定于内容的模式，并且可以快速解析。

    有两种目标模式(target modes)可以解析对目标的相对引用。 内部目标模式(internal target mode)下的分辨率提供部件，外部目标模式(external target mode)下的分辨率提供外部资源。

    关系具有关系标识符(relationship identifiers)。 这些标识符允许相互区分关系。 通过在该点嵌入关系标识符，标识符还可用于将关系的目标与源部件中的特定点相关联（例如，表示一个超链接）。

    关系具有关系类型(relationship type)。

    关系在关系部件(Relationships parts)中以 XML 形式表示。 如果包本身或包中的任何部件是一个或多个关系的源，则存在关联的关系部件。 该部件保存源的关系列表。 本文档中定义的各部件的关系命名空间和关系类型列于[附录 E] 中。

    关系还有第二个重要功能：提供有关部件的附加信息而不修改其内容。 请注意，某些情况需要将信息附加到现有部件而不修改该部件，例如，因为该部件已加密且无法解密，或者因为它经过数字签名，更改它会使签名无效。

=== "英文"

    **General**

    Parts may contain references to other parts in the package and to resources outside of the package. These references are represented inside the referring part in ways that are specific to the media type of the part, that is, in arbitrary markup or an application-defined encoding. This effectively hides the links between parts from applications that do not understand the media types of the parts containing such references.

    This document introduces an indirect mechanism to describe references from parts to other parts or external resources, namely, relationships. Relationships represent connections from a source part or source package to a target part or target resource. Relationships from parts are called part relationships, while those from packages are called package relationships. Relationships make the connection directly discoverable without looking at the part contents, so they are independent of content-specific schemas and are quick to resolve.

    There are two target modes to resolve relative references to targets. Resolution in the internal target mode provides parts and that in the external target mode provides external resources.

    Relationships have relationship identifiers. These identifiers allow relationships to be distinguished from one another. An identifier can also be used to associate the target of a relationship with a specific point in a source part (for example, to represent a hyperlink), by embedding the relationship identifier at that point.

    A relationship has a relationship type.

    Relationships are represented in XML in Relationships parts. If the package itself or any part in the package is the source of one or more relationships, there is an associated Relationships part. This part holds the list of relationships for the source. The Relationships namespace and relationship types for parts defined in this document are listed in Annex E.

    Relationships have a second important function: providing additional information about parts without modifying their content. Note that some scenarios require information to be attached to an existing part without modifying that part, for example, because the part is encrypted and cannot be decrypted, or because it is digitally signed and changing it would invalidate the signature.

#### 6.5.2 关系部件

**Relationships part**

##### 6.5.2.1 关系部件

=== "中文"

    - **媒体类型**: "application/vnd.openxmlformats-package.relationships+xml"
    - **根命名空间**: "http://schemas.openxmlformats.org/package/2006/relationships"

    共享公共源的每组关系都由关系部件表示。 关系部件不应有任何关系。

    关系部件应是包关系部件（[6.5.2.2]）或部件关系部件（[6.5.2.3]）。

=== "英文"

    **Relationships part**

    - **Media Type**: "application/vnd.openxmlformats-package.relationships+xml"
    - **Root Namespace**: "http://schemas.openxmlformats.org/package/2006/relationships"

    Each set of relationships sharing a common source is represented by a Relationships part. There shall be no relationships from or to a Relationships part.

    A Relationships part shall be either a package Relationships part ([6.5.2.2]) or a part Relationships part ([6.5.2.3]).

##### 6.5.2.2 包关系部件

=== "中文"

    包关系部件(package Relationships part)应是包含包关系且不包含其他关系的关系部件。
    
    包关系部件的名称应为“`/_rels/.rels`”。

    当包关系部分中出现相对引用时，基本 IRI 取决于关系的目标模式(target mode)。 如果目标模式是外部(external)，则基本 IRI 应为包的绝对 IRI(absolute IRI)。 如果目标模式是内部模式(internal)，则基本 IRI 应为从包的绝对 IRI 创建的包 IRI(pack IRI)。

    示例 考虑位于以下位置的包的包关系部件(package Relationships part)：
    
    "http://www.mysite.com/my.package".
    
    如果目标模式为外部(external)，则基本 IRI 为:
    
    "http://www.mysite.com/my.package"
    
    如果目标模式是内部(internal)，则基本 IRI 为
    
    "pack://http%3c,,www.mysite.com,my.package/"

=== "英文"

    **Package Relationships part**

    A package Relationships part shall be a Relationships part containing package relationships and no other relationships.
    
    The name of a package Relationships part shall be "`/_rels/.rels`".

    When a relative reference occurs in a package Relationships part, the base IRI depends on the target mode of the relationship. If the target mode is external, the base IRI shall be the absolute IRI of the package. If the target mode is internal, the base IRI shall be the pack IRI created from the absolute IRI of the package.

    EXAMPLE Consider the package Relationships part for a package located at
    
    "http://www.mysite.com/my.package".
    
    If the target mode is external, the base IRI is
    
    "http://www.mysite.com/my.package"
    
    If the target mode is internal, the base IRI is
    
    "pack://http%3c,,www.mysite.com,my.package/"

##### 6.5.2.3 部件关系部件

=== "中文"

    部件关系部件(part Relationships part)应是包含来自同一源部件的部件关系且不包含其他关系的关系部件。

    部件关系部件(part Relationships part)的名称应根据源部件的名称构建，方法是将“`.rels`”添加到最后一个 I18N 段的末尾，并在最后一个 I18N 段之前插入一个 I18N 段“`_rels`”。

    !!! info "EXAMPLE 1" 
    
        如果源部件名称为“`/foo`”，则关系部件名称为“`/_rels/foo.rels`”。 相反，如果部件的名称是“`/_rels/foo.rels`”，则它是源部件“`/foo`”的部件关系部件。 如果源部件名称为“`/foo/bar.xml`”，则关系部件名称为“`/foo/_rels/bar.xml.rels`”。 相反，如果部件的名称是“`/foo/_rels/bar.xml.rels`”，则它是源部件“`/foo/bar.xml`”的部件关系部件。

    当相对引用出现在部件关系部件中时，基本 IRI 取决于关系的目标模式(target mode)。 如果目标模式是外部(external)，则基本 IRI 应为包的绝对 IRI(absolute IRI)。 如果目标模式是内部模式(internal)，则基本 IRI 应是根据包的绝对 IRI 和源部分名称创建的包 IRI(pack IRI)。

    !!! info "EXAMPLE 2" 
        
        考虑位于包中的关系部件 “`/a/b/_rels/foo.xml.rels`”

        "`http://www.mysite.com/my.package`"
    
        如果目标模式为外部(external)，则基本 IRI 为
    
        "`http://www.mysite.com/my.package`"
    
        如果目标模式是内部(internal)，则基本 IRI 为
    
        "pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml"

=== "英文"

    **Part Relationships part**

    A part Relationships part shall be a Relationships part containing part relationships from the same source part and no other relationships.

    The name of a part Relationships part shall be constructed from the name of the source part by adding ".rels" to the end of the last I18N segment and inserting an I18N segment “_rels” immediately before the last I18N segment.

    EXAMPLE 1 If the source part name is "/foo", the part Relationships part name is "/_rels/foo.rels". Conversely, if the name of a part is "/_rels/foo.rels", it is a part Relationships part for the source part "/foo". If the source part name is "/foo/bar.xml", the part Relationships part name is "/foo/_rels/bar.xml.rels". Conversely, if the name of a part is "/foo/_rels/bar.xml.rels", it is a part Relationships part for the source part "/foo/bar.xml".

    When a relative reference occurs in a part Relationships part, the base IRI depends on the target mode of the relationship. If the target mode is external, the base IRI shall be the absolute IRI of the package. If the target mode is internal, the base IRI shall be the pack IRI created from the absolute IRI of the package and the source part name.

    EXAMPLE 2 Consider a part Relationships part "`/a/b/_rels/foo.xml.rels`" in a package located at

    "`http://www.mysite.com/my.package`"

    If the target mode is external, the base IRI is

    "`http://www.mysite.com/my.package`"

    If the target mode is internal, the base IRI is

    "`pack://http%3c,,www.mysite.com,my.package/a/b/foo.xml`"

#### 6.5.3 关系标记

**Relationship markup**

##### 6.5.3.1 常规

=== "中文"

    关系部件(Relationships part)的内容应为 XML 文档。 在 MCE 处理器按照 ECMA-376-3 的规定删除任何扩展后，关系部件应是针对 `opc-relationships.xsd` ([C.5]) 的架构有效的 XML 文档。 对于此 MCE 处理，标记配置应为空，并且应用程序配置应仅包含关系命名空间(Relationships namespace)。

    关系部件(Relationships part)的任何 MCE 处理产生的输出文档不应包含 XML Base 指定的 `xml:base` 属性。

=== "英文"

    **General**

    The content of a Relationships part shall be an XML document. After the removal of any extensions by an MCE processor as specified in ECMA-376-3, a Relationships part shall be a schema-valid XML document against opc-relationships.xsd (C.5). For this MCE processing, the markup configuration shall be empty and the application configuration shall contain the Relationships namespace only.

    The output document resulting from any MCE processing of the Relationships part shall not contain an `xml:base` attribute, as specified by XML Base.

##### 6.5.3.2 支持版本控制和可扩展性

=== "中文"

    关系部件(Relationships part)可以使用 ECMA-376-3 中定义的版本控制和可扩展性机制来合并从其他 XML 名称空间提取的元素和属性。

=== "英文"

    **Support for versioning and extensibility**

    Relationships parts may use the versioning and extensibility mechanisms defined in ECMA-376-3 to incorporate elements and attributes drawn from other XML namespaces.

##### 6.5.3.3 关系的元素表示

=== "中文"

    `Relationships` 元素是关系部件(Relationships part)的根元素。 它是零个或多个`Relationship`元素的容器。 它没有属性。 该元素内容模型的 W3C XML schema 定义是复杂类型 `CT_Relationships`，它在模式 `opc-relationships.xsd` ([C.5]) 中定义。

=== "英文"

    **Relationships element**

    A `Relationships` element is the root element of a Relationships part. It is the container for zero or more `Relationship` elements. It has no attributes. The W3C XML Schema definition of this element’s content model is the complex type `CT_Relationships`, which is defined in the schema opc-relationships.xsd (C.5).

##### 6.5.3.4 关系元素

=== "中文"

    关系元素(Relationship element)应表示一种关系。 关系的源(source of a relationship)应是包含此关系元素的关系部分与之关联的包或部件。

    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>**TargetMode**</td>
                <td>
                    该属性指定关系的目标模式(target mode)。<br/> <br/>
                    该属性是可选的(optional)，默认值为`Internal`。<br/> <br/>
                    此属性的可能值为 `Internal` 和 `External`，由简单类型 `ST_TargetMode` 定义，<br/>
                    该类型在模式(schema) `opcrelationships.xsd`([C.5]) 中定义。
                </td>
            </tr>
            <tr>
                <td>**Target**</td>
                <td>
                    该属性指定关系的目标(target)。 <br/> <br/>
                    该属性是必需的(required)。  <br/> <br/>
                    如果 `TargetMode` 属性的值为 `Internal`，则 `Target` 属性应是对部件的相对引用。 <br/>
                    如果 `TargetMode` 属性的值为 `External`，则 `Target` 属性应为相对引用或绝对IRI。 <br/>
                    用于解析相对引用的基本 IRI 在 [6.4] 中定义。<br/><br/>
                    该属性的值范围应由 W3C XML Schema数据类型的 `xsd:anyURI` 简单类型定义。
                </td>
            </tr>
            <tr>
                <td>**Type**</td>
                <td>
                    该属性指定关系的关系类型(relationship type)。 <br/> <br/>
                    该属性是必需的(required)。  <br/> <br/>
                    可以比较关系类型以确定两个关系元素(Relationship elements)是否属于同一类型。 <br/>
                    此比较的执行方式与比较标识 XML 命名空间的 URI 时的方式相同：<br/>
                    两个 URI 被视为字符串，并且当且仅当字符串具有相同的字符序列时才被视为相同。<br/> 
                    比较区分大小写，并且不会进行或撤消转义。<br/><br/>
                    EXAMPLE 1 <br/>
                    Type="`http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/signature`" <br/><br/>
                    该属性的值范围应由 W3C XML Schema 数据类型的 `xsd:anyURI` 简单类型定义。
                </td>
            </tr>
            <tr>
                <td>**Id**</td>
                <td>
                    该属性指定关系的标识符(identifier)。 Id 属性的值在关系部件中应该是唯一的(unique)。<br/> <br/>
                    该属性是必需的(required)。  <br/> <br/>
                    EXAMPLE 2 <br/>
                    Id="`A5FFC797514BC`" <br/><br/>
                    该属性的值范围应由 W3C XML Schema数据类型的`xsd:ID`简单类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    该元素内容模型的 W3C XML Schema定义是复杂类型`CT_Relationship`，它在模式 `opc-relationships.xsd` 中定义（[C.5]）。

=== "英文"

    **Relationship element**

    A Relationship element shall represent a relationship. The source of a relationship shall be either a package or part with which the Relationships part containing this Relationship element is associated.

    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>**TargetMode**</td>
                <td>
                    This attribute specifies the target mode of a relationship. <br/> <br/>
                    This attribute is optional, and the default value is `Internal`.  <br/> <br/>
                    The possible values for this attribute are `Internal` and `External`, as defined by <br/>
                    the simple type `ST_TargetMode`, which is defined in the schema opcrelationships.xsd ([C.5]). 
                </td>
            </tr>
            <tr>
                <td>**Target**</td>
                <td>
                    This attribute specifies the target of a relationship. <br/> <br/>
                    This attribute is required.  <br/> <br/>
                    If the value of the TargetMode attribute is Internal, the Target attribute shall <br/>
                    be a relative reference to a part. If the value of the TargetMode attribute is <br/>
                    External, the Target attribute shall be a relative reference or an absolute IRI. <br/>
                    Base IRIs for resolving relative references are defined in 6.4. <br/><br/>
                    The range of values for this attribute shall be as defined by the xsd:anyURI<br/>
                    simple type of W3C XML Schema Datatypes.
                </td>
            </tr>
            <tr>
                <td>**Type**</td>
                <td>
                    This attribute specifies the relationship type of a relationship. <br/> <br/>
                    This attribute is required.  <br/> <br/>
                    Relationship types can be compared to determine whether two Relationship <br/>
                    elements are of the same type. This comparison is conducted in the same way as <br/>
                    when comparing URIs that identify XML namespaces: the two URIs are treated as <br/>
                    strings and considered identical if and only if the strings have the same sequence of <br/>
                    characters. The comparison is case-sensitive, and no escaping is done or undone. <br/><br/>
                    EXAMPLE 1 <br/>
                    Type="`http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/signature`" <br/><br/>
                    The range of values for this attribute shall be as defined by the xsd:anyURI simple type of W3C XML Schema Datatypes.
                </td>
            </tr>
            <tr>
                <td>**Id**</td>
                <td>
                    This attribute specifies the identifier of a relationship. The value of the Id attribute shall be unique within the Relationships part. <br/> <br/>
                    This attribute is required.  <br/> <br/>
                    EXAMPLE 2 <br/>
                    Id="`A5FFC797514BC`" <br/><br/>
                    The range of values for this attribute shall be as defined by the `xsd:ID` simple type of W3C XML Schema Datatypes.
                </td>
            </tr>
        </tbody>
    </table>

    The W3C XML Schema definition of this element’s content model is the complex type `CT_Relationship`, which is defined in the schema opc-relationships.xsd ([C.5]).

#### 6.5.4 示例

**Examples**

##### 6.5.4.1 与整个包关联的关系部件

=== "中文"

    考虑位于“`http://www.example.com/ex.opc`”的包。 假设该包包含关系部件“`/_rels/.rels`”。 该关系部件是包关系部件(package Relationships part)，它与整个包相关联。

    另外，假设该**包关系部件**(package Relationships part)的内容是如下所示的XML文档：

    ```xml
    <Relationships
         xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
         <Relationship
             Target="a.xml"
             Id="IDI1"
             Type="http://example.com/relTypeInt1"/>
         <Relationship
             Target="a.xml"
             TargetMode="External"
             Id="IDE1"
             Type="http://example.com/relTypeExt1"/>
    </Relationships>
    ```

    此**包关系部件**(package Relationships part)中的两个关系元素(Relationship element)指定两个关系。 每个关系的来源都是包(package)。
    
    第一个关系(relationship):

    - 目标模式是内部(`Internal`)（默认）。 因此，用于解析`a.xml`的基本 IRI 是根据包("`http://www.example.com/ex.opc`")的 IRI 创建的包 IRI（“`pack://http%3c,,www.example.com,ex.opc`”）。
    - 解析 “`a.xml`” 的结果是 “`pack://http%3c,,www.example.com,ex.opc/a.xml`”。 因此，该关系的目标是该包中的 “`/a.xml`” 部分。
    - 该关系的关系类型是 “`http://example.com/relTypeInt1`”。 
    - 该关系的标识符(identifier)是“`IDI1`”。
    
    第二个关系(relationship):
        
    - 目标模式是外部(`External`). 因此，解析“`a.xml`”的基本 IRI 是包的 IRI（“http://www.example.com/ex.opc”）。
    - 因此，此关系的目标是“`http://www.example.com/a.xml`”处的资源。 
    - 该关系的关系类型是“`http://example.com/relTypeExt1`”。 
    - 该关系的标识符(identifier)是“`IDE1`”。 

=== "英文"

    **Relationships part associated with the entire package**

    Consider a package located at "`http://www.example.com/ex.opc`". Suppose that the package contains a Relationships part "`/_rels/.rels`". This Relationships part is a package Relationships part, which is associated with the entire package.

    Also, suppose that the content of this package Relationships part is the XML document shown below:
    
    ```xml
    <Relationships
         xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
         <Relationship
             Target="a.xml"
             Id="IDI1"
             Type="http://example.com/relTypeInt1"/>
         <Relationship
             Target="a.xml"
             TargetMode="External"
             Id="IDE1"
             Type="http://example.com/relTypeExt1"/>
    </Relationships>
    ```

    The two Relationship elements in this package Relationships part specify two relationships. The source of each relationship is the package.
    
    The first relationship:

    - The target mode is Internal (default). Thus, the base IRI for resolving "a.xml" is the pack IRI ("`pack://http%3c,,www.example.com,ex.opc`") created from the IRI of the package ("`http://www.example.com/ex.opc`").
    - The result of resolving "`a.xml`" is "`pack://http%3c,,www.example.com,ex.opc/a.xml`". The target of this relationship is thus the part "`/a.xml`" in this package.
    - The relationship type of this relationship is "`http://example.com/relTypeInt1`".
    - The identifier of this relationship is "IDI1".
    
    The second relationship:
        
    - The target mode is External. Thus, the base IRI for resolving "a.xml" is the IRI ("`http://www.example.com/ex.opc`") of the package.
    - The target of this relationship is thus the resource at "`http://www.example.com/a.xml`".
    - The relationship type of this relationship is "`http://example.com/relTypeExt1`".
    - The identifier of this relationship is "IDE1".

##### 6.5.4.2 与部件关联的关系部件

=== "中文"

    考虑位于“`http://www.example.com/ex.opc`”的包。 假设该包包含关系部件“`/foo/_rels/test.xml.rels`”。 该**关系部件**(Relationships part)是**部件关系部件**(part Relationships part)，其来源是“`/foo/test.xml`”部分。
    
    另外，假设该**部件关系部件**(part Relationships part)的内容是如下所示的XML文档：

    ```xml
    <Relationships
         xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
         <Relationship
             Target="b.xml"
             Id="IDI2"
             Type="http://example.com/relTypeInt2"/>
         <Relationship
             Target="b.xml"
             TargetMode="External"
             Id="IDE2"
             Type="http://example.com/relTypeExt2"/>
    </Relationships>
    ```

    本**部件关系部件**(part Relationships part)中的两个“`Relationship`”元素指定了两个关系。 每个关系的来源是“`/foo/test.xml`”部件。

    第一个关系(relationship):

    - 第一个关系的模式是内部(`Internal`)（默认）。因此，基本 IRI ("`pack://http%3c,,www.example.com,ex.opc/foo/test.xml`") 是根据包的 IRI ("`http://www.example.com/ex.opc`") 和部件名称“`/foo/test.xml`”创建的包 IRI。
    - 解析 “`b.xml`” 的结果是 “`pack://http%3c,,www.example.com,ex.opc/foo/b.xml`”。 因此，该关系的目标(target)是该包中的 “`/foo/b.xml`” 部分。
    - 该关系的关系类型(relationship type)是“`http://example.com/relTypeInt2`”。
    - 该关系的标识符(identifier)是"`IDI2`".

    第二个关系(relationship):

    - 第二个关系的目标模式是外部(`External`). 因此，解析“`a.xml`”的基本 IRI 是包的 IRI（“http://www.example.com/ex.opc”）。
    - 因此，此关系的目标是“`http://www.example.com/b.xml`”处的资源。
    - 该关系的关系类型(relationship type)是 "`http://example.com/relTypeExt2`".
    - 该关系的标识符(identifier)是 "`IDE2`".

=== "英文"

    **Relationships part associated with a part**

    Consider a package located at "`http://www.example.com/ex.opc`". Suppose that the package contains a Relationships part "`/foo/_rels/test.xml.rels`". This Relationships part is a part Relationships part, the source of which is a part "`/foo/test.xml`".
    
    Also, suppose that the content of this part Relationships part is the XML document shown below:

    ```xml
    <Relationships
         xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
         <Relationship
             Target="b.xml"
             Id="IDI2"
             Type="http://example.com/relTypeInt2"/>
         <Relationship
             Target="b.xml"
             TargetMode="External"
             Id="IDE2"
             Type="http://example.com/relTypeExt2"/>
    </Relationships>
    ```

    The two `Relationship` elements in this part Relationships part specify two relationships. The source of each relationship is the part "`/foo/test.xml`".

    The first relationship:

    - The mode of the first relationship is Internal (default). Thus, the base IRI ("`pack://http%3c,,www.example.com,ex.opc/foo/test.xml`") is the pack IRI created from the IRI ("`http://www.example.com/ex.opc`") of the package and the part name "`/foo/test.xml`".
    - The result of resolving "`b.xml`" is "`pack://http%3c,,www.example.com,ex.opc/foo/b.xml`". The target of this relationship is thus the part "`/foo/b.xml`" in this package.
    - The relationship type of this relationship is "`http://example.com/relTypeInt2`".
    - The identifier of this relationship is "IDI2".

    The second relationship:

    - The mode of the second relationship is External. Thus, the base IRI is the IRI ("`http://www.example.com/ex.opc`") of the package.
    - The target of this relationship is thus the resource at "`http://www.example.com/b.xml`".
    - The relationship type of this relationship is "`http://example.com/relTypeExt2`".
    - The identifier of this relationship is "IDE2".

##### 6.5.4.3 与数字签名标记相关的关系部件

=== "中文"

    数字签名源部件(Digital Signature Origin part) ([10.4.2]) 以包关系(package relationship)为目标，该关系存储在包关系部分“`/_rels/.rels`”中。

    !!! info "Example 1"
        
        表示与数字签名来源部件的包关系的关系元素(Relationship element)：

        ```xml
        <Relationship Id="rId4"
            Type="http://schemas.openxmlformats.org/package/2006/relationships/
            digital-signature/origin"
            Target="_xmlsignatures/origin.sigs"/>
        ```

        从数字签名源到数字签名 XML 签名部件的连接由部件关系表示，该关系存储在**部件关系部件**(part Relationships part) “`/_xmlsignatures/_rels/origin.sigs.rels`”中。

    !!! info "Example 2"

        表示“`/_xmlsignatures/_rels/origin.sigs.rels`”内容的 XML 文档：

        ```xml
        <Relationships
            xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
            <Relationship
                Target="sig1.xml"
                Id="rId1"
                Type="http://schemas.openxmlformats.org/package/2006/relationships/
                     digital-signature/signature"/>
        </Relationships>
        ```

=== "英文"

    **Relationships parts related to digital signature markup**

    The Digital Signature Origin part (10.4.2) is targeted by a package relationship, which is stored in the package Relationships part, "`/_rels/.rels`".

    !!! info "Example 1"
        
        A Relationship element representing the package relationship to the Digital Signature Origin part:

        ```xml
        <Relationship Id="rId4"
            Type="http://schemas.openxmlformats.org/package/2006/relationships/
            digital-signature/origin"
            Target="_xmlsignatures/origin.sigs"/>
        ```

        The connection from the Digital Signature Origin to the Digital Signature XML Signature part is represented by a part relationship, which is stored in a part Relationships part, "`/_xmlsignatures/_rels/origin.sigs.rels`".

    !!! info "Example 2"

        An XML document representing the content of "`/_xmlsignatures/_rels/origin.sigs.rels`":

        ```xml
        <Relationships
            xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
            <Relationship
                Target="sig1.xml"
                Id="rId1"
                Type="http://schemas.openxmlformats.org/package/2006/relationships/
                    digital-signature/signature"/>
        </Relationships>
        ```

##### 6.5.4.4 针对外部资源的关系

=== "中文"

    关系可以将包外部的绝对位置的资源以及相对于包的当前位置定位的资源作为目标。 以下关系部件指定将包或部件连接到外部绝对位置的 `pic1.jpg` 以及相对于包位置的外部位置的 `my_house.jpg` 的关系：

    ```xml
    <Relationships
        xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
        <Relationship
            TargetMode="External"
            Id="A9EFC627517BC"
            Target="http://www.example.com/images/pic1.jpg"
            Type="http://www.example.com/external-resource" />
        <Relationship
            TargetMode="External"
            Id="A5EFC797514BC"
            Target="images/my_house.jpg"
            Type="http://www.example.com/external-resource"/>
    </Relationships>
    ```

=== "英文"

    **Relationships targeting external resources**

    Relationships can target resources outside the package at an absolute location and resources located relative to the current location of the package. The following Relationships part specifies relationships that connect a package or part to pic1.jpg at an external absolute location, and to my_house.jpg at an external location relative to the location of the package:

    ```xml
    <Relationships
        xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
        <Relationship
            TargetMode="External"
            Id="A9EFC627517BC"
            Target="http://www.example.com/images/pic1.jpg"
            Type="http://www.example.com/external-resource" />
        <Relationship
            TargetMode="External"
            Id="A5EFC797514BC"
            Target="images/my_house.jpg"
            Type="http://www.example.com/external-resource"/>
    </Relationships>
    ```

##### 6.5.4.5 具有相同目标的多个关系

=== "中文"

    以下关系部件(Relationships part)包含两个关系，每个关系都使用唯一的 `Id` 值。 这些关系共享相同的目标，但具有不同的关系类型(relationship types)。

    ```xml
    <Relationships
        xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
            <Relationship
                Target="Signature.xml"
                Id="A5FFC797514BC"
                Type="http://schemas.openxmlformats.org/package/2006/
                relationships/digital-signature/signature"/>
            <Relationship
                Target="Signature.xml"
                Id="B5F32797CC4B7"
                Type="http://www.example.com/internal-resource"/>
    </Relationships>
    ```

=== "英文"

    **Multiple relationships that have the same target**

    The following Relationships part contains two relationships, each using a unique Id value. The relationships share the same Target, but have different relationship types.

    ```xml
    <Relationships
        xmlns="http://schemas.openxmlformats.org/package/2006/relationships">
            <Relationship
                Target="Signature.xml"
                Id="A5FFC797514BC"
                Type="http://schemas.openxmlformats.org/package/2006/
                relationships/digital-signature/signature"/>
            <Relationship
                Target="Signature.xml"
                Id="B5F32797CC4B7"
                Type="http://www.example.com/internal-resource"/>
    </Relationships>
    ```

## 7. 物理封装模型

**Physical package model**

### 7.1 General

=== "中文"

    本节根据物理格式（例如ZIP格式）以及从抽象包模型到该物理格式的映射来介绍**物理包模型**(physical package model)。 有关物理包模型设计注意事项的更多讨论，请参阅[附录 F]。

    本节进一步规定了物理包模型的一般准则和通用机制，并定义了基于 ZIP 的物理包模型。 交织机制(interleaving mechanism)（参见[7.2.4]）就是这样一种常见的机制。

    [H.3]中描述了一个示例物理包。

=== "英文"

    **General**

    This clause introduces a physical package model in terms of a physical format (such as the ZIP format) and a mapping from the abstract package model to this physical format. See [Annex F] for additional discussion of physical package model design considerations.

    This clause further specifies general guidelines and common mechanisms for physical package models and defines a ZIP-based physical package model. The interleaving mechanism (see [7.2.4]) is such a common mechanism.

    An example physical package is described in [H.3].

### 7.2 物理映射指南

**Physical mapping guidelines**

#### 7.2.1 使用物理格式的特征

=== "中文"

    许多物理格式具有与抽象包模型中的组件部分匹配的功能。 从抽象包模型到物理格式的映射应该利用抽象包模型和物理格式之间功能上的任何相似性，同时使用映射层来提供物理格式中固有不存在的附加功能。 例如，某些物理格式将部件存储为文件系统中的单独文件，在这种情况下，**将许多部件名称直接映射到相应的物理文件名称是有利的**。

=== "英文"

    **Using features of physical formats**

    Many physical formats have features that partially match components in the abstract package model. A mapping from the abstract package model to a physical format should take advantage of any similarities in capabilities between the abstract package model and the physical format while using layers of mapping to provide additional capabilities not inherently present in the physical format. For example, some physical formats store parts as individual files in a file system, in which case, it is advantageous to map many part names directly to corresponding physical file names.

#### 7.2.2 映射组件

=== "中文"

    需要物理包模型来表示**包**、**部件**（包括**关系部件**）、**部件名称**和**部件媒体类型**，但不需要表示增长提示(growth hint)。

=== "英文"

    **Mapped components**

    A physical package model is required to represent packages, parts (including Relationships parts), part names, and part media types, but is not required to represent a growth hint.

#### 7.2.3 将媒体类型映射到部件

**Mapping media types to parts**

##### 7.2.3.1 常规

=== "中文"

    物理格式可以具有用于将媒体类型与部件相关联的本机机制(native mechanism)。 例如，MIME 实体标头中的 Content-Type 字段将媒体类型与该 MIME 实体相关联。 对于这样的物理格式，来自抽象包模型的映射应该使用本机机制。

    对于所有其他物理格式，包应包含 XML 流，在本文档中称为**媒体类型流**(Media Types stream)。 媒体类型流不应代表一部件。 该流不应是 URI 可寻址的。 然而，它可以使用与交错部件(interleaving parts)相同的机制在物理包中交错。

=== "英文"

    **General**

    A physical format can have a native mechanism for associating media types with parts. For example, the Content-Type field in the header of a MIME entity associates a media type with that MIME entity. For such a physical format, mappings from the abstract package model should use the native mechanism.

    For all other physical formats, the package shall include an XML stream that is referred to in this document as the Media Types stream. The Media Types stream shall not represent a part. This stream shall not be URI-addressable. However, it may be interleaved in the physical package using the same mechanisms used for interleaving parts.

##### 7.2.3.2 媒体类型流标记

**Media Types stream markup**

###### 7.2.3.2.1 常规

=== "中文"

    媒体类型流的内容应是针对 `opccontentTypes.xsd` ([C.2]) 的架构有效的 XML 文档。 该 XML 文档应具有顶级 `Types` 元素，以及一个或多个`Default`和`Override`子元素。 `Default`元素应定义从部分名称的扩展名到媒体类型的默认映射。 `Override`元素应指定默认映射未覆盖或不一致的部分的媒体类型。 请注意，`Default`元素可用于减少零件上`Override`元素的数量。

    对于除关系部件(Relationships parts) ([6.5.2]) 之外的包的所有部分，**媒体类型流**(Media Types stream)应指定：
    
    - 一个匹配的`Default`元素，或
    - 一个匹配的`Override`元素，或
    - 同时匹配的 `Default` 元素和匹配的`Override`元素，在这种情况下，`Override`元素优先。

    对于任何给定的扩展(extension)，不得有超过一个`Default`元素，并且对于任何给定的部件名称，不得有超过一个`Override`元素。

    媒体类型流中`Default` 和 `Override` 元素的顺序并不重要。
    
    媒体类型流(Media Types stream)可以定义 `Default` 元素，即使没有部件使用它们。

=== "英文"

    **General**

    The content of the Media Types stream shall be a schema-valid XML document against opccontentTypes.xsd (C.2). This XML documen shall have a top-level `Types` element, and one or more `Default` and `Override` child elements. `Default` elements shall define default mappings from the extensions of part names to media types. `Override` elements shall specify media types on parts that are not covered by, or are not consistent with, the default mappings. Note that `Default` elements can be used to reduce the number of `Override` elements on a part.

    For all parts of the package other than Relationships parts (6.5.2), the Media Types stream shall specify either:
    
    - One matching `Default` element, or
    - One matching `Override` element, or
    - Both a matching `Default` element and a matching `Override` element, in which case, the `Override` element takes precedence.

    There shall not be more than one `Default` element for any given extension, and there shall not be more than one `Override` element for any given part name.

    The order of `Default` and `Override` elements in the Media Types stream shall not be significant.
    
    The Media Types stream may define `Default` elements even though no parts use them.

###### 7.2.3.2.2 支持版本控制和可扩展性

=== "中文"

    媒体类型流(Media Types stream)不得使用 ECMA-376-3 中定义的版本控制和可扩展性机制。

=== "英文"

    **Support for versioning and extensibility**

    The Media Types stream shall not use the versioning and extensibility mechanisms defined in ECMA-376-3.

###### 7.2.3.2.3 `Types`元素

=== "中文"

    `Types` 元素应是媒体类型流中包含的 XML 文档的根元素。
    
    该元素不应有任何属性。

    该元素内容模型的 W3C XML Schema 定义是复杂类型 `CT_Types`，它在模式 `opc-contentTypes.xsd` 中定义（[C.2]）。

=== "英文"

    **Types element**

    A Types element shall be the root element of the XML document contained in the Media Types stream. 
    
    This element shall have no attributes.

    The W3C XML Schema definition of this element’s content model is the complex type `CT_Types`, which is defined in the schema opc-contentTypes.xsd ([C.2]).

###### 7.2.3.2.4 `Default`元素

=== "中文"

    `Default` 元素应指定从部分名称的扩展名到媒体类型的默认映射。

    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>`Extension`</td>
                <td>
                    该属性指定一个字符串作为文件扩展名。</br></br>
                    该属性是必需的(required)。</br></br>
                    `Default` 元素应匹配名称以句点（“.”）结尾的任何部分，后跟该属性的值。</br></br>
                    该属性的可能值由简单类型 [`ST_Extension`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_Extension.html) 定义，</br>
                    该类型在模式 `opc-contentTypes.xsd` ([C.2]) 中定义。
                </td>
            </tr>
            <tr>
                <td>`ContentType`</td>
                <td>
                    该属性使用 RFC 7231, 3.1.1.1 中定义的语法指定媒体类型(media type)。</br></br>
                    该属性是必需的(required)。</br></br>
                    指定的媒体类型应适用于任何匹配的部分（除非被`Override`元素覆盖）。</br></br>
                    该属性的可能值由简单类型 [`ST_ContentType`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_ContentType.html)定义， </br> 
                    该类型在模式 `opc-contentTypes.xsd` ([C.2]) 中定义。
                </td>
            </tr>
        </tbody>
    </table>

    该元素内容模型的 W3C XML 架构定义是复杂类型 [`CT_Default`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_CT_Default.html)，它在架构 `opc-contentTypes.xsd` ([C.2]) 中定义。

=== "英文"

    **Default element**

    A `Default` element shall specify the default mappings from the extensions of part names to media types.

    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>`Extension`</td>
                <td>
                    This attribute specifies a string as a file extension.</br></br>
                    This attribute is required.</br></br>
                    A `Default` element shall match any part whose name ends with a period (“.”) followed by the value of this attribute. </br></br>
                    The possible values for this attribute are defined by the simple type</br>
                    [`ST_Extension`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_Extension.html), which is defined in the schema opc-contentTypes.xsd ([C.2]). 
                </td>
            </tr>
            <tr>
                <td>`ContentType`</td>
                <td>
                    This attribute specifies a media type using the syntax defined in RFC 7231, 3.1.1.1.</br></br>
                    This attribute is required.</br></br>
                    The specified media type shall apply to any matching parts (unless overridden by `Override` elements). </br></br>
                    The possible values for this attribute are defined by the simple type</br>
                    [`ST_ContentType`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_ContentType.html), which is defined in the schema opc-contentTypes.xsd ([C.2]).
                </td>
            </tr>
        </tbody>
    </table>

    The W3C XML Schema definition of this element’s content model is the complex type [`CT_Default`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_CT_Default.html), which is defined in the schema opc-contentTypes.xsd ([C.2]).

###### 7.2.3.2.5 Override元素

=== "中文"

    `Override`元素应为默认映射未覆盖或不一致的部分指定媒体类型。

    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>`ContentType`</td>
                <td>
                    该属性使用 RFC 7231, 3.1.1.1 中定义的语法指定媒体类型。</br></br>
                    该属性是必需的(required)。</br></br>
                    指定的媒体类型应适用于属性 `PartName` 中命名的部分。 </br></br>
                    该属性的可能值由简单类型 [`ST_Extension`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_ContentType.html) 定义，该类型在模式 `opc-contentTypes.xsd` ([C.2]) 中定义。
                </td>
            </tr>
            <tr>
                <td>`PartName`</td>
                <td>
                    该属性指定部件名称。</br></br>
                    该属性是必需的(required)。</br></br>
                    `Override`元素应匹配名称等于该属性值的部分。</br></br>
                    该属性的值范围应由 W3C XML 模式数据类型的 `xsd:anyURI` 简单类型定义。 </br>
                </td>
            </tr>
        </tbody>
    </table>

    该元素内容模型的 W3C XML 架构定义是复杂类型 [`CT_Override`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_CT_Override.html) ，它在模式 `opc-contentTypes.xsd` ([C.2]) 中定义。

=== "英文"

    **Override element**

    An `Override` element shall specify a media type for a part that is not covered by, or is not consistent with, the default mappings.

    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>`ContentType`</td>
                <td>
                    This attribute specifies a media type using the syntax defined in RFC 7231, 3.1.1.1.</br></br>
                    This attribute is required.</br></br>
                    The specified media type shall apply to the part named in the attribute `PartName`. </br></br>
                    The possible values for this attribute are defined by the simple type</br>
                    [`ST_Extension`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_ST_ContentType.html), which is defined in the schema opc-contentTypes.xsd ([C.2]).
                </td>
            </tr>
            <tr>
                <td>`PartName`</td>
                <td>
                    This attribute specifies a part name.</br></br>
                    This attribute is required.</br></br>
                    An `Override` element shall match a part whose name is equal to the value of this attribute. </br></br>
                    The range of values for this attribute shall be as defined by the `xsd:anyURI` </br>
                    simple type of W3C XML Schema Datatypes.
                </td>
            </tr>
        </tbody>
    </table>

    The W3C XML Schema definition of this element’s content model is the complex type [`CT_Override`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-contentTypes/opc-contentTypes_CT_Override.html), which is defined in the schema opc-contentTypes.xsd ([C.2]).

##### 7.2.3.3 媒体类型流标记示例

=== "中文"

    !!! info "EXAMPLE: 媒体类型流标记"

        ```xml
        <Types
            xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
            <Default Extension="txt" ContentType="text/plain" />
            <Default Extension="jpeg" ContentType="image/jpeg" />
            <Default Extension="picture" ContentType="image/gif" />
            <Override PartName="/a/b/sample4.picture" ContentType="image/jpeg" />
        </Types>
        ```

    `Types`元素是包中使用的媒体类型的容器。

    以下是部分及其相应媒体类型的示例列表，如上面的媒体类型流标记所定义。

    | **部件名称**         | **媒体类型** |
    | -------------------- | ------------ |
    | /a/b/sample1.txt     | text/plain   |
    | /a/b/sample2.jpg     | image/jpeg   |
    | /a/b/sample3.picture | image/gif    |
    | /a/b/sample4.picture | image/jpeg   |

=== "英文"

    **Media Types stream markup example**

    EXAMPLE Media Types stream markup

    ```xml
    <Types
        xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
        <Default Extension="txt" ContentType="text/plain" />
        <Default Extension="jpeg" ContentType="image/jpeg" />
        <Default Extension="picture" ContentType="image/gif" />
        <Override PartName="/a/b/sample4.picture" ContentType="image/jpeg" />
    </Types>
    ```

    The `Types` element is a container for media types used within the package.

    The following is a sample list of parts and their corresponding media types as defined by the Media Types stream markup above.

    | **Part name**        | **Media type** |
    | -------------------- | -------------- |
    | /a/b/sample1.txt     | text/plain     |
    | /a/b/sample2.jpg     | image/jpeg     |
    | /a/b/sample3.picture | image/gif      |
    | /a/b/sample4.picture | image/jpeg     |

##### 7.2.3.4 在媒体类型流中设置部分媒体类型⭐

=== "中文"

    当向包添加新部件时，包实现者应确保在媒体类型流中指定该部件的媒体类型(media type)。 包实现者应执行以下步骤来执行此操作：

    1. 通过从最右边的段中获取最右边出现的点字符 (“.”) 右侧的子字符串来获取部件名称的扩展名(extension)。
    2. 如果部件名称没有扩展名，则应将相应的`Override`元素添加到媒体类型流(Media Types stream)中。
    3. 将生成的扩展与为媒体类型流中`Default`元素的`Extension`属性指定的值进行比较。 比较应为 ASCII 不区分大小写的匹配。
    4. 如果存在具有匹配的 `Extension`属性的 `Default`元 素，则新部分的媒体类型应与 `ContentType` 属性的值进行比较。 比较应不区分大小写，并包括每个字符，无论它在 RFC 7231 的内容类型语法中扮演什么角色。

        1. 如果媒体类型(media types)匹配，则无需采取进一步操作。
        2. 如果媒体类型(media types)不匹配，则应将新的`Override`元素添加到媒体类型流中。

    5. 如果不存在具有匹配的`Extension`属性的`Default`元素，则应将新的`Default`元素或`Override`元素添加到媒体类型流中。

=== "英文"

    **Setting a part media type in the Media Types stream**

    When adding a new part to a package, the package implementer shall ensure that a media type for that part is specified in the Media Types stream. The package implementer shall perform the following steps to do so:

    a) Get the extension from the part name by taking the substring to the right of the rightmost occurrence of the dot character (“.”) from the rightmost segment.

    b) If a part name has no extension, a corresponding `Override` element shall be added to the Media Types stream.
    
    c) Compare the resulting extension with the values specified for the `Extension` attributes of the `Default` elements in the Media Types stream. The comparison shall be ASCII case-insensitive matching.

    d) If there is a `Default` element with a matching `Extension` attribute, then the media type of the new part shall be compared with the value of the `ContentType` attribute. The comparison shall be case-insensitive and include every character regardless of the role it plays in the content-type grammar of RFC 7231.

      1) If the media types match, no further action is required.
      2) If the media types do not match, a new `Override` element shall be added to the Media Types stream.

    e) If there is no `Default` element with a matching `Extension` attribute, a new `Default` element or `Override` element shall be added to the Media Types stream.

##### 7.2.3.5 从媒体类型流中确定部件媒体类型

=== "中文"

    要获取部件的媒体类型，包实现者应执行以下步骤：
    
    1. 将部件名称与为`Override`元素的`PartName`属性指定的值进行比较。 比较应为 ASCII 不区分大小写的匹配。
    2. 如果存在具有匹配的`PartName`属性的`Override`元素，则返回其`ContentType`属性的值。 不需要采取进一步行动。
    3. 如果没有具有匹配的`PartName`属性的`Override`元素，则
        
        1. 通过从最右边的段中获取最右边出现的点字符 (“.”) 右侧的子字符串来获取部件名称的扩展名。
        2. 检查媒体类型流的`Default`元素，将扩展名与`Extension`属性的值进行比较。 比较应为 ASCII 不区分大小写的匹配。
    
    4. 如果存在具有匹配的`Extension`属性的`Default`元素，则返回其`ContentType`属性的值。 不需要采取进一步行动。

    !!! info "NOTE" 
    
        给定一个一致的包，要么通过步骤 2 找到 `Override` 元素，要么通过步骤 3 找到 `Default` 元素

=== "英文"

    **Determining a part media type from the Media Types stream**

    To get the media type of a part, the package implementer shall perform the following steps:
    
    a) Compare the part name with the values specified for the `PartName` attribute of the `Override` elements. The comparison shall be ASCII case-insensitive matching.

    b) If there is an `Override` element with a matching `PartName` attribute, return the value of its `ContentType` attribute. No further action is required.

    c) If there is no `Override` element with a matching `PartName` attribute, then
    
        1) Get the extension from the part name by taking the substring to the right of the rightmost occurrence of the dot character (“.”) from the rightmost segment.
        2) Check the `Default` elements of the Media Types stream, comparing the extension with the value of the `Extension` attribute. The comparison shall be ASCII case-insensitive matching.
    
    d) If there is a `Default` element with a matching `Extension` attribute, return the value of its `ContentType` attribute. No further action is required.

    NOTE Given a conformant package, either an Override element is found by step b) or a Default element is found by
    step c)

#### 7.2.4 交错

=== "中文"

    当将抽象包映射到物理包时，一部分的数据流或媒体类型流可能被分成多个片段(pieces)。 每个片段(piece)应代表一个数据流，该数据流可以为空。 稍后可以根据片段名称将片段连接在一起，形成原始流，如[7.2.5.2]中所指定。

    物理包可能包含交错部件(interleaved parts)和非交错部件(non-interleaved parts)。 交错的部件应为破碎成片段(pieces)的部件。 非交错部件应是未破碎成片段(pieces)的部件。

    **片段**(Pieces)仅存在于物理封装中，并且在抽象封装模型中不可寻址。 片段应按其**自然片段编号顺序**(natural piece-number order)出现，并且可以与其他部件或非交错部件交错。
    
    由于它提供的性能优势，包实现者应该支持交错(interleaving)，但不要求这样做。

    有关交错性能优势的进一步讨论，请参阅[F.3]。

=== "英文"

    **Interleaving**

    When mapping an abstract package to a physical package, the data stream of a part or the Media Types stream may be broken into pieces. Each piece shall represent a data stream, which may be empty. Pieces can later be joined together, forming the original stream, based on piece names, as specified in [7.2.5.2].

    A physical package may contain both interleaved parts and non-interleaved parts. Interleaved parts shall be parts broken into pieces. Non-interleaved parts shall be parts not broken into pieces.

    Pieces shall exist only in the physical package and shall not be addressable in the abstract package model. Pieces shall occur in their natural piece-number order and may be interleaved with pieces of other parts or with non-interleaved parts.
    
    Because of the performance benefits it provides, package implementers should support interleaving but are not required to do so.
    
    For further discussion of performance benefits of interleaving see [F.3].

#### 7.2.5 将部件名称映射到物理包项目名称

**Mapping part names to physical package item names**

##### 7.2.5.1 常规

=== "中文"

    从抽象包到物理包的映射应使用逻辑项作为中间对象，以便允许交错（[7.2.4]）。 如果一个部件或媒体类型流是交错的，则由它构成的每个片段都应是一个逻辑项； 否则，该部件或媒体类型流应为逻辑项。 参见图 1。

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-7-1.png)
      <figcaption>图 1 — 将部件名称映射到逻辑项名称</figcaption>
    </figure>

=== "英文"

    **General**

    A mapping from an abstract package to a physical package shall use logical items as intermediate objects in order to permit interleaving ([7.2.4]). If a part or the Media Types stream is interleaved, each piece constructed from it shall be a logical item; otherwise, the part or Media Types stream shall be a logical item. See Figure 1.

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-7-1-en.png)
      <figcaption>Figure 1 — Mapping Part names to logical item names</figcaption>
    </figure>

##### 7.2.5.2 逻辑项目名称

=== "中文"

    逻辑项(logical items)的名称应为 Unicode 字符串。 不需要非 ASCII 字符的支持。
    
    如果逻辑项是一个片段(piece)，则其名称应具有以下语法的后缀(suffixes)：

    ```text
    SuffixName   = "/" "[" PieceNumber "]" [".last"] ".piece"
    PieceNumber  = "0" | NonZeroDigit [1*Digit]
    Digit        = "0" | NonZeroDigit
    NonZeroDigit = "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" 
    ```

    逻辑项名称(logical item name)的前缀是从逻辑项名称中删除后缀（如果有）的结果。

    前缀和后缀的等效性应通过 ASCII 不区分大小写的匹配来确定。 如果前缀和后缀相等，则逻辑名称应相等。 物理包不得包含等效的逻辑项名称。
    
    使用后缀名称的逻辑项名称应形成完整序列当且仅当：

    a) 序列中所有逻辑项名称的前缀名称是等效的，并且
    
    b) 序列的后缀名称以“`/[0].piece`”开头，以“/`[n].last.piece`”结尾，并且当片段编号为 `0` 到 `n` 之间的每个片段编号时，包括一个片段，没有间隙。 解释为十进制整数值。

=== "英文"

    **Logical item names**

    Names of logical items shall be Unicode strings. The support of non-ASCII characters is not required.
    
    If a logical item is a piece, its name shall have suffixes of the following syntax:

    ```text
    SuffixName   = "/" "[" PieceNumber "]" [".last"] ".piece"
    PieceNumber  = "0" | NonZeroDigit [1*Digit]
    Digit        = "0" | NonZeroDigit
    NonZeroDigit = "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" 
    ```

    The prefix of a logical item name is the result of removing a suffix, if any, from the logical item name.

    Equivalence of prefixes, and of suffixes shall be determined by ASCII case-insensitive matching. Logical names shall be equivalent if their prefixes and suffixes are equivalent. A physical package shall not contain equivalent logical item names. 

    Logical item names that use suffix names shall form a complete sequence if and only if:

    a) the prefix names of all logical item names in the sequence are equivalent, and
    
    b) the suffix names of the sequence start with "/[0].piece" and end with "/[n].last.piece" and include a piece for every piece number between 0 and n, without gaps, when the piece numbers are interpreted as decimal integer values.

##### 7.2.5.3 将部件名称映射到逻辑项目名称

=== "中文"

    非交错部件的名称应映射到具有等效前缀但无后缀的逻辑项名称。 

    交错部件的名称应映射到具有等效前缀的逻辑项名称的完整序列。

=== "英文"

    **Mapping part names to logical item names**

    Names of non-interleaved parts shall be mapped to logical item names that have an equivalent prefix and no suffix.

    Names of interleaved parts shall be mapped to the complete sequence of logical item names with an equivalent prefix.

##### 7.2.5.4 映射逻辑项名称和物理包项名称

=== "中文"

    逻辑项名称和物理包项名称的映射应特定于特定的物理包。

=== "英文"

    **Mapping logical item names and physical package item names**

    The mapping of logical item names and physical package item names shall be specific to the particular physical package. 

##### 7.2.5.5 将逻辑项名称映射到部件名称

=== "中文"

    没有后缀的逻辑项名称应映射到具有等效前缀的部件名称，前提是前缀名称符合部件名称语法。

    逻辑项名称的完整序列应映射到部件名称(part name)，该部件名称等于具有后缀“`/[0].piece`”的逻辑项名称的前缀，前提是前缀名称符合(conforms)部件名称语法 。

    物理包可能包含无法映射到部件名称的逻辑项名称和逻辑项名称的完整序列，因为逻辑项名称不遵循部件命名语法。 此类逻辑项或逻辑项的完整序列不应映射到部件。

    !!! info "EXAMPLE" 
    
        逻辑项名称“`/[trash]/0000.dat`”无法映射到部件项。 因此，该逻辑项并不代表部件。

=== "英文"

    **Mapping logical item names to part names**

    A logical item name without a suffix shall be mapped to a part name with an equivalent prefix, provided that the prefix name conforms to the part name syntax.

    A complete sequence of logical item names shall be mapped to the part name that is equal to the prefix of the logical item name having the suffix "`/[0].piece`", provided that the prefix name conforms to the part name syntax.

    A physical package may contain logical item names and complete sequences of logical item names that cannot be mapped to a part name because the logical item name does not follow the part naming grammar. Such logical items or complete sequences of logical items shall not be mapped to parts.

    EXAMPLE A logical item name "`/[trash]/0000.dat`" cannot be mapped to a part item. Thus, this logical item does not represent a part.

### 7.3 映射到 ZIP 文件

**Mapping to a ZIP file**

#### 7.3.1 常规🌟

=== "中文"

    本文档定义了 ZIP 文件格式的映射。

    代表物理包的 ZIP 文件应满足[附录 B] 的要求，并应遵循 [附录 B] 的建议(recommendations)。

    ZIP 文件的物理包项目应为 ZIP 项目。 请注意，当用户解压缩基于 ZIP 的包时，他们会看到一组文件和文件夹，这些文件和文件夹反映了包中的各个部分及其分层命名结构。

    表 1 显示了**抽象包模型**(abstract package model)的各个组件及其在 ZIP 文件中相应的物理表示。

    表 1 — 抽象包模型组件及其物理表示

    <table>
        <thead>
            <tr>
                <th> **抽象包模型组件** </th>
                <th> **物理表示** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> 包</br>(Package) </td>
                <td> ZIP文件</br>(ZIP file) </td>
            </tr>
            <tr>
                <td> 部件</br>(Part) </td>
                <td> ZIP项</br>(ZIP item) </td>
            </tr>
            <tr>
                <td> 部件名称</br>(Part name) </td>
                <td> 存储在项标头(item header)（以及适当的 ZIP 中央目录）中。 </br>
                     转换规则见[7.3.4]。
                </td>
            </tr>
            <tr>
                <td> 部件媒体类型</br>(Part media type) </td>
                <td> 存储在包含[7.2.3.2]中描述的媒体类型流的ZIP项中。  </br> 有关 ZIP 项名称的详细信息，请参阅[7.3.7]。
                </td>
            </tr>
            <tr>
                <td> 成长提示</br>(Growth hint) </td>
                <td> 项目前面的本地标头中的 ZIP扩展字段中保留的填充。 数据结构的详细描述参见[7.3.8]
                </td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **General**

    This document defines a mapping for the ZIP file format.

    A ZIP file representing a physical package shall satisfy the requirements of Annex B and should follow the recommendations of [Annex B].

    Physical package items of ZIP files shall be ZIP items. Note that when users unzip a ZIP-based package, they see a set of files and folders that reflects the parts in the package and their hierarchical naming structure.

    Table 1 shows the various components of the abstract package model and their corresponding physical representation in a ZIP file.

    Table 1 — Abstract package model components and their physical representations

    <table>
        <thead>
            <tr>
                <th>
                    **Abstract package** </br>
                    **model** </br>
                    **component** </br>
                </th>
                <th> **Physical representation** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> Package </td>
                <td> ZIP file </td>
            </tr>
            <tr>
                <td> Part </td>
                <td> ZIP item </td>
            </tr>
            <tr>
                <td> Part name </td>
                <td> Stored in item header (and ZIP central directory as appropriate). See </br>
                     [7.3.4] for conversion rules.  
                </td>
            </tr>
            <tr>
                <td> Part media type </td>
                <td> Stored in the ZIP item containing the Media Types stream described in </br>
                     [7.2.3.2]. See [7.3.7] for details about the ZIP item name. </td>
            </tr>
            <tr>
                <td> Growth hint </td>
                <td> Padding reserved in the ZIP Extra field in the local header that </br>
                     precedes the item. See [7.3.8] for a detailed description of the data </br>
                     structure </td>
            </tr>
        </tbody>
    </table>

#### 7.3.2 映射部件数据

=== "中文"

=== "英文"

    **Mapping part data**

    每个非交错部件应表示为单个 ZIP 项(ZIP item)。 如[7.2.4]中所述，交错部件的每一块应表示为单个 ZIP 项(ZIP item)。

#### 7.3.3 ZIP项名称

=== "中文"

    ZIP 项目名称应符合 ZIP `Appnote`。 从抽象包到 ZIP 文件的映射应仅使用 ASCII ZIP 项目名称。 ZIP 项目名称在给定 ZIP 文件中应是唯一的。

    !!! info "EXAMPLE" 
    
        ZIP 文件中的以下 ZIP 项名称映射到部件碎片和整个部件： 

        ```text
        "spine.xml/[0].piece"
        "pages/page0.xml"
        "spine.xml/[1].piece"
        "pages/page1.xml"
        "spine.xml/[2].last.piece"
        "pages/page2.xml"
        ```

=== "英文"

    **ZIP item names**

    ZIP item names shall conform to the ZIP `Appnote`. A mapping from an abstract package to a ZIP file shall only use ASCII ZIP item names. ZIP item names shall be unique within a given ZIP file.

    EXAMPLE The following ZIP item names in a ZIP file are mapped to part pieces and whole parts:

    ```text
    "spine.xml/[0].piece"
    "pages/page0.xml"
    "spine.xml/[1].piece"
    "pages/page1.xml"
    "spine.xml/[2].last.piece"
    "pages/page2.xml"
    ```

#### 7.3.4 将逻辑项目名称映射到 ZIP 项目名称

=== "中文"

    对于每个逻辑项，将逻辑项名称映射到 ZIP 项名称的过程应按顺序涉及以下步骤：

    1. 从逻辑项名称中删除前导正斜杠（“/”），或者在交错部件的情况下，从完整序列中的每个逻辑项名称中删除前导斜杠（“/”）。
    2. 对每个非 ASCII 字符进行**百分比编码**(Percent-encode)。

=== "英文"

    **Mapping logical item names to ZIP item names**

    For each logical item, the process of mapping of logical item names to ZIP item names shall involve the following steps, in order:

    a) Remove the leading forward slash (“/”) from the logical item name or, in the case of interleaved parts, from each of the logical item names within the complete sequence.
    
    b) Percent-encode every non-ASCII character.

#### 7.3.5 将 ZIP 项目名称映射到逻辑项目名称

=== "中文"

    所有 ZIP 项的名称都应映射到逻辑项名称，不代表文件的项除外。
    
    !!! info "NOTE" 
    
        对于某些文件系统(file systems)，`ZIP Appnote` 提供了有关被识别为文件的 ZIP 项目的更多信息。
    
    对于每个 ZIP 项目，将 ZIP 项目名称映射到逻辑项名称的过程应按顺序涉及以下步骤：
    
    1. 对每个非 ASCII 字符进行取消百分比编码(Percent-encode)。
    2. 添加正斜杠（“/”）。

=== "英文"

    **Mapping ZIP item names to logical item names**

    The names of all ZIP items shall be mapped to logical item names, except for items that do not represent files.
    
    NOTE For some file systems, the ZIP Appnote provides further information on ZIP items that are recognized as files.
    
    For each ZIP item, the process of mapping of ZIP item names to logical item names shall involve the following steps, in order:
    
    a) Un-percent-encode every non-ASCII character.
    
    b) Add a forward slash (“/”). 

#### 7.3.6 ZIP 包限制

=== "中文"

    本文档要求 ZIP 文件内的**中央目录结构**(central directory structure)中的文件头不得超过 65 535 字节（请参阅 ZIP 应用说明中的 “F. 中央目录结构” ）。 每个文件头包含一个 zip 项名称、额外字段（包括表示 [6.2.4] 中指定的增长提示的字节）、文件注释以及表示其他字段的 42 个字节。

    包实现者(Package implementers)在命名要存储为 ZIP 项目的部件时，应限制部件命名以适应文件系统限制。

    !!! info "EXAMPLE"
        
        这些限制的例子是:

       - 在 `MS Windows®` 文件系统上，不支持星号 (“`*`”)，因此用此字符命名的部分无法成功解压缩。
       - 在 `MS Windows®` 文件系统上，许多程序只能处理少于 256 个字符的文件名（包括完整路径）； 一旦解压部件，他们就无法处理名称较长的部件。
    
    基于 ZIP 的包不得包含 ZIP 应用说明中所述的加密。
    
    基于 ZIP 的包不得使用除 DEFLATE 之外的压缩算法，如 ZIP Appnote 说明中所述。

=== "英文"

    **ZIP package limitations**

    This document requires that a file header in the central directory structure within a ZIP file shall not exceed 65 535 bytes (see "F. Central directory structure" in the ZIP Appnote). Each file header contains a zip item name, Extra field (including bytes representing growth hint as specified in 6.2.4), File Comment, and 42 more bytes representing miscellaneous fields.

    Package implementers should restrict part naming to accommodate file system limitations when naming parts to be stored as ZIP items.

    EXAMPLE Examples of these limitations are:
    
    - On MS Windows® file systems, the asterisk (“*”) is not supported, so parts named with this character do not unzip successfully.
    - On MS Windows® file systems, many programs can handle only file names that are less than 256 characters including the full path; they cannot handle parts with longer names once the parts are unzipped.
    
    ZIP-based packages shall not include encryption as described in the ZIP Appnote.
    
    ZIP-based packages shall not use compression algorithms except DEFLATE, as described in the ZIP Appnote.

#### 7.3.7 映射媒体类型流

=== "中文"

    在 ZIP 文件中，媒体类型流应存储在名称为`[Content_Types].xml`的项目中，或者在交错的情况下，存储在 ZIP 项目`[Content_Types].xml/[0].piece`” 、“`[Content_Types].xml/[1].piece`”、… 和 “`[Content_Types].xml/[n].last.piece`” 的完整序列中。 

    !!! info "NOTE" 
    
        专门选择中括号字符“`[`”和“`]`”作为媒体类型流名称(Media Types stream name)，因为这些字符违反了部件命名语法，从而强化了这样的要求：从媒体类型流构建的 ZIP 项名称始终可以与从部件名称构建的 ZIP 项目名称区分开。

=== "英文"

    **Mapping the Media Types stream**

    In ZIP files, the Media Types stream shall be stored in an item with the name "`[Content_Types].xml`" or, in the interleaved case, in the complete sequence of ZIP items "`[Content_Types].xml/[0].piece`", "`[Content_Types].xml/[1].piece`", …, and "`[Content_Types].xml/[n].last.piece`".

    NOTE Bracket characters "[" and "]" were chosen for the Media Types stream name specifically because these characters violate the part naming grammar, thus reinforcing the requirement that the ZIP item names constructed from the Media Types stream are always distinguishable from those constructed from part names.

#### 7.3.8 映射增长提示

=== "中文"

    增长提示(growth hint)建议的额外空间存储在 `Extra` 字段中，如 `ZIP Appnote` 中所定义。 如果增长提示用于交错部件，则填充将存储在表示该部件第一部分的 ZIP 项的 `Extra` 字段中。

    当用于增长提示时，ZIP 项目的 `Extra` 字段的格式如表 2 所示。
    
    表 2 — 增长提示 `Extra` 字段的结构

    <table>
        <thead>
            <tr>
                <th> **字段组件** </th>
                <th> **大小** </th>
                <th> **值** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> 标头 ID(Header ID) </td>
                <td> 2 字节(2 bytes) </td>
                <td> 0xA220 </td>
            </tr>
            <tr>
                <td> 额外字段的长度(Length of Extra field) </td>
                <td> 2 字节(2 bytes) </td>
                <td> 
                    剩余部分的长度（以字节为单位） </br>
                    Extra 字段的组成部分: 签名 </br>
                    元件长度 + 填充初始长度 </br>
                    元件长度 + 填充组件长度 </br>
                </td>
            </tr>
            <tr>
                <td> 签名（用于验证） </td>
                <td> 2 字节(2 bytes) </td>
                <td> 0xA028 </td>
            </tr>
            <tr>
                <td> 填充初始长度 </td>
                <td> 2 字节(2 bytes) </td>
                <td> 
                     创建项目时包实现者设置的 填充组件的长度（以字节为单位）
                </td>
            </tr>
            <tr>
                <td> 填充(Padding) </td>
                <td> 变量(variable) </td>
                <td> 填充`0x00`字节 </td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **Mapping the growth hint**

    The additional space suggested by growth hint is stored in the Extra field, as defined in the ZIP Appnote. If the growth hint is used for an interleaved part, the padding is stored in the Extra field of the ZIP item representing the first piece of the part.

    The format of the ZIP item's Extra field, when used for growth hints, is shown in Table 2.
    
    Table 2 — Structure of the Extra field for growth hints

    <table>
        <thead>
            <tr>
                <th> **Field component** </th>
                <th> **Size** </th>
                <th> **Value** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> Header ID </td>
                <td> 2 bytes </td>
                <td> 0xA220 </td>
            </tr>
            <tr>
                <td> Length of Extra field </td>
                <td> 2 bytes </td>
                <td> 
                    The length in bytes of the remaining </br>
                    components of the Extra field: Signature </br>
                    component length + Padding Initial Length </br>
                    component length + Padding component length </br>
                </td>
            </tr>
            <tr>
                <td> Signature (for verification) </td>
                <td> 2 bytes </td>
                <td> 0xA028 </td>
            </tr>
            <tr>
                <td> Padding Initial Length </td>
                <td> 2 bytes </td>
                <td> 
                     The length in bytes of the Padding component </br>
                     set by a package implementer when the item is created  </br>
                </td>
            </tr>
            <tr>
                <td> Padding </td>
                <td> variable </td>
                <td> Filled with 0x00 bytes </td>
            </tr>
        </tbody>
    </table>

## 8. 核心属性

**Core properties**

### 8.1 常规

=== "中文"

    用户可以将核心属性与包关联起来。 这些核心属性使用户能够获取和设置众所周知的常见属性元数据集到包中。 核心属性和描述它们的格式如表 3 所示：

    表 3 — 核心属性

    <table>
        <thead>
            <tr>
                <th> **Property** </th>
                <th> **Specification** </th>
                <th> **Description** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> category </td>
                <td> OPC </td>
                <td> 该包内容的分类。 </td>
            </tr>
            <tr>
                <td> contentStatus </td>
                <td> OPC </td>
                <td> 内容的状态。  </td>
            </tr>
            <tr>
                <td> created </td>
                <td> DCMI 元数据术语 </td>
                <td> 资源的创建日期。 </td>
            </tr>
            <tr>
                <td> creator </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> 主要负责制作资源内容的实体。 </td>
            </tr>
            <tr>
                <td> description </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> 对资源内容的解释。 </td>
            </tr>
            <tr>
                <td> identifier </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> 在给定上下文中对资源的明确引用。  </td>
            </tr>
            <tr>
                <td> keywords </td>
                <td> OPC </td>
                <td> 用于支持搜索和索引的一组分隔关键字。 </br> 
                     这通常是属性中其他地方不可用的术语列表。  </td>
            </tr>
            <tr>
                <td> language </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> 资源知识内容的语言。 </br> 
                     请注意，IETF RFC 3066 提供了有关编码来表示语言的指南。 </td>
            </tr>
            <tr>
                <td> lastModifiedBy </td>
                <td> OPC </td>
                <td> 执行最后一次修改的用户。 识别是特定于环境的。  </td>
            </tr>
            <tr>
                <td> lastPrinted </td>
                <td> OPC </td>
                <td> 上次打印的日期和时间。 </td>
            </tr>
            <tr>
                <td> modified </td>
                <td> DCMI 元数据术语 </td>
                <td> 更改资源的日期。 </td>
            </tr>
            <tr>
                <td> revision </td>
                <td> OPC </td>
                <td> 修订号。  </td>
            </tr>
            <tr>
                <td> subject </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> The topic of the content of the resource.  </td>
            </tr>
            <tr>
                <td> title </td>
                <td> 都柏林核心元数据元素集 </td>
                <td> The name given to the resource.  </td>
            </tr>
            <tr>
                <td> version </td>
                <td> OPC </td>
                <td> 修订号。  </td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **General**

    Users can associate core properties with packages. Such core properties enable users to get and set wellknown and common sets of property metadata to packages. The core properties and the specifications that describe them are shown in Table 3:

    Table 3 — Core properties

    <table>
        <thead>
            <tr>
                <th> **Property** </th>
                <th> **Specification** </th>
                <th> **Description** </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td> category </td>
                <td> Open Packaging Conventions </td>
                <td> A categorization of the content of this package. </td>
            </tr>
            <tr>
                <td> contentStatus </td>
                <td> Open Packaging Conventions </td>
                <td> The status of the content.  </td>
            </tr>
            <tr>
                <td> created </td>
                <td> DCMI Metadata Terms </td>
                <td> Date of creation of the resource. </td>
            </tr>
            <tr>
                <td> creator </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> An entity primarily responsible for making the content of the resource. </td>
            </tr>
            <tr>
                <td> description </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> An explanation of the content of the resource. </td>
            </tr>
            <tr>
                <td> identifier </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> An unambiguous reference to the resource within a given context.  </td>
            </tr>
            <tr>
                <td> keywords </td>
                <td> Open Packaging Conventions </td>
                <td> A delimited set of keywords to support searching and indexing. </br> 
                     This is typically a list of terms that are not available elsewhere in the properties.  </td>
            </tr>
            <tr>
                <td> language </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> The language of the intellectual content of the resource. </br> 
                     Note that IETF RFC 3066 provides guidance on encoding to represent languages. </td>
            </tr>
            <tr>
                <td> lastModifiedBy </td>
                <td> Open Packaging Conventions </td>
                <td> The user who performed the last modification. The identification is environment-specific.  </td>
            </tr>
            <tr>
                <td> lastPrinted </td>
                <td> Open Packaging Conventions </td>
                <td> The date and time of the last printing. </td>
            </tr>
            <tr>
                <td> modified </td>
                <td> DCMI Metadata Terms </td>
                <td> Date on which the resource was changed. </td>
            </tr>
            <tr>
                <td> revision </td>
                <td> Open Packaging Conventions </td>
                <td> The revision number.  </td>
            </tr>
            <tr>
                <td> subject </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> The topic of the content of the resource.  </td>
            </tr>
            <tr>
                <td> title </td>
                <td> Dublin Core Metadata Element Set </td>
                <td> The name given to the resource.  </td>
            </tr>
            <tr>
                <td> version </td>
                <td> Open Packaging Conventions </td>
                <td> The revision number.  </td>
            </tr>
        </tbody>
    </table>

### 8.2 核心属性部件

=== "中文"

    一个包最多应包含一个**核心属性部件**(Core Properties part)。
    
    包内的核心属性部件应由包中的核心属性关系引用，如[附录 E] 中所列。 一个包最多应包含一个核心属性关系(core properties relationship)。

    核心属性部分的媒体类型应为**核心属性部件媒体类型**(Core Properties part media type)，如[附录 E]中所定义。

=== "英文"

    **Core Properties part**

    A package shall contain at most one Core Properties part.
    
    A Core Properties part within the package shall be referenced by a core properties relationship from the package, as listed in [Annex E]. A package shall contain at most one core properties relationship.

    The media type of a Core Properties part shall be the Core Properties part media type, as defined in [Annex E].

### 8.3 核心属性标记

**Core properties markup**

#### 8.3.1 常规

=== "中文"

    核心属性部分的内容应是针对 `opccoreProperties.xsd` ([C.3]) 的架构有效的 XML 文档。
    
    除非另有规定，表示核心属性部分的元素应属于[附录 E] 中定义的命名空间。
    
    EXAMPLE
    
    核心属性部件的示例如下所示。

    ```xml
    <coreProperties
        xmlns="http://schemas.openxmlformats.org/package/2006/metadata/
            core-properties"
        xmlns:dcterms="http://purl.org/dc/terms/"
        xmlns:dc="http://purl.org/dc/elements/1.1/"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dc:creator>Alan Shen</dc:creator>
        <dcterms:created xsi:type="dcterms:W3CDTF">
            2005-06-12
        </dcterms:created>

        <dc:title>OPC Core Properties</dc:title>
        <dc:description>Spec defines the schema for OPC Core Properties and
                        their location within the package</dc:description>
        <dc:language>eng</dc:language>
        <version>1.0</version>
        <lastModifiedBy>Alan Shen</lastModifiedBy>
        <dcterms:modified xsi:type="dcterms:W3CDTF">2005-11-23</dcterms:modified>
        <contentStatus>Reviewed</contentStatus>
        <category>Specification</category>
    </coreProperties>
    ```

    在本示例中 `dc:creator`, `dcterms:created`, `dc:title`, `dc:description`, `dc:language`, `version`, `lastModifiedBy`, `dcterms:modified`, `contentStatus`, 和 `category` 都是核心属性元素.

=== "英文"

    **General**

    The content of the Core Properties part shall be a schema-valid XML document against opccoreProperties.xsd (C.3).
    
    Unless specified otherwise, elements representing a Core Properties part shall be of the namespace as defined in Annex E.
    
    EXAMPLE
    
    An example of a Core Properties part is shown below.

    ```xml
    <coreProperties
        xmlns="http://schemas.openxmlformats.org/package/2006/metadata/
            core-properties"
        xmlns:dcterms="http://purl.org/dc/terms/"
        xmlns:dc="http://purl.org/dc/elements/1.1/"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dc:creator>Alan Shen</dc:creator>
        <dcterms:created xsi:type="dcterms:W3CDTF">
            2005-06-12
        </dcterms:created>

        <dc:title>OPC Core Properties</dc:title>
        <dc:description>Spec defines the schema for OPC Core Properties and
                        their location within the package</dc:description>
        <dc:language>eng</dc:language>
        <version>1.0</version>
        <lastModifiedBy>Alan Shen</lastModifiedBy>
        <dcterms:modified xsi:type="dcterms:W3CDTF">2005-11-23</dcterms:modified>
        <contentStatus>Reviewed</contentStatus>
        <category>Specification</category>
    </coreProperties>
    ```

    In this example `dc:creator`, `dcterms:created`, `dc:title`, `dc:description`, `dc:language`, `version`, `lastModifiedBy`, `dcterms:modified`, `contentStatus`, and `category` are core property elements.

#### 8.3.2 支持版本控制和可扩展性

=== "中文"

    核心属性部件(Core Properties part)不应包含 ECMA-376-3 中定义的标记兼容性命名空间的元素或属性。

    !!! info "NOTE" 
    
        版本控制和可扩展性功能是通过创建新部件并使用与新类型的关系从核心属性部件指向新部件来实现的。 本文档不为用于扩展核心属性的新部件或关系类型提供任何要求或指南。 ISO/IEC TR 30114-1（参见参考文献[^4]）提供了这样的指南。

=== "英文"

    **Support for versioning and extensibility**

    A Core Properties part shall not contain elements or attributes of the Markup Compatibility namespace as defined in ECMA-376-3.

    NOTE Versioning and extensibility functionality is accomplished by creating a new part and using a relationship with a new type to point from the Core Properties part to the new part. This document does not provide any requirements or guidelines for new parts or relationship types that are used to extend core properties. ISO/IEC TR 30114-1 (see Reference [^4]) provides such a guideline.

#### 8.3.3 `coreProperties`元素

=== "中文"

    A `coreProperties` element is the root element of a Core Properties part.

    该元素不应有任何属性。

    该元素的子元素应为核心属性元素，如[8.3.4]中所定义。

    该元素的内容由复杂类型 [`CT_CoreProperties`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_CoreProperties.html) 定义，该类型在schema `opc-coreProperties.xsd` ([C.3]) 中定义。

=== "英文"

    **`coreProperties` element**

    A `coreProperties` element is the root element of a Core Properties part.

    This element shall have no attributes.

    Children of this element shall be core property elements, as defined in [8.3.4].
    
    The content of this element is defined by the complex type [`CT_CoreProperties`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_CoreProperties.html), which is defined in the schema opc-coreProperties.xsd ([C.3]).

#### 8.3.4 核心属性元素

**Core property elements**

##### 8.3.4.1 常规

=== "中文"

    核心属性元素应当是代表核心属性的元素。 核心属性元素是不可重复的。 它们可以为空或省略。

=== "英文"

    **General**

    Core property elements shall be elements representing core properties. Core property elements are nonrepeatable. They can be empty or omitted.

##### 8.3.4.2 ISO 15836-1 定义的核心属性元素

=== "中文"

    该文档允许创建者、描述、标识符、语言、主题和标题元素作为核心属性元素。 如果包含任何这些元素，则它们应符合 ISO 15836-1 的规定。

    NOTE 这些元素属于命名空间 "`http://purl.org/dc/elements/1.1/`".

    这些元素不应有子元素，也不应具有 `xsi:typ`e 属性或 `xml:lang` 属性。
    
    EXAMPLE
    
    [8.3.1] 中的示例包含 ISO 15836-1 中的四个元素。

    ```xml
    <dc:creator>Alan Shen</dc:creator>
    <dc:title>OPC Core Properties</dc:title>
    <dc:description>Spec defines the schema for OPC Core Properties and their
    location within the package</dc:description>
    <dc:language>eng</dc:language>
    ```

=== "英文"

    **Core property elements as defined by ISO 15836-1**

    This document allows creator, description, identifier, language, subject, and title elements as core property elements. If any of these elements are included, they shall be as specified by ISO 15836-1.

    NOTE These elements belong to the namespace "`http://purl.org/dc/elements/1.1/`".

    These elements shall not have child elements and shall not have the `xsi:typ`e attribute or the `xml:lang` attribute.
    
    EXAMPLE
    
    The example in 8.3.1 contains four elements from ISO 15836-1.

    ```xml
    <dc:creator>Alan Shen</dc:creator>
    <dc:title>OPC Core Properties</dc:title>
    <dc:description>Spec defines the schema for OPC Core Properties and their
    location within the package</dc:description>
    <dc:language>eng</dc:language>
    ```

##### 8.3.4.3 ISO 15836-2 定义的核心属性元素

=== "中文"

    本文档允许创建和修改的元素作为核心属性元素。 如果包含其中一个或两个元素，则它们应符合 ISO 15836-2 的规定。

    NOTE 这些元素属于命名空间 "http://purl.org/dc/terms/".
    
    本文档提出了进一步的要求。 这些元素不应有子元素，也不应具有 `xml:lang` 属性。 这些元素应具有 `xsi:type` 属性，其值为`dcterms:W3CDTF`（请参阅参考文献 [^2]），并且 `dcterms` 应声明为 Dublin Core 命名空间的前缀“`http://purl.org/dc/terms/`”。

    EXAMPLE

    [8.3.1] 中的示例包含 DCMI 元数据术语中的两个元素。

    ```xml
    <dcterms:created xsi:type="dcterms:W3CDTF">2005-06-12</dcterms:created>
    <dcterms:modified xsi:type="dcterms:W3CDTF">2005-11-23</dcterms:modified>
    ```

=== "英文"

    **Core property elements as defined by ISO 15836-2**

    This document allows created and modified elements as core property elements. If either or both of these elements are included, they shall be as specified by ISO 15836-2.

    NOTE These elements belong to the namespace "http://purl.org/dc/terms/".
    
    This document introduces further requirements. These elements shall not have child elements and shall not have the xml:lang attribute. These elements shall have the xsi:type attribute whose value is "dcterms:W3CDTF" (see Reference [^2]) and dcterms shall be declared as the prefix of the Dublin Core namespace "http://purl.org/dc/terms/".

    EXAMPLE

    The example in 8.3.1 contains two elements from DCMI Metadata Terms.

    ```xml
    <dcterms:created xsi:type="dcterms:W3CDTF">2005-06-12</dcterms:created>
    <dcterms:modified xsi:type="dcterms:W3CDTF">2005-11-23</dcterms:modified>
    ```

##### 8.3.4.4 本文档中定义的核心属性元素

**Core property elements defined in this document**

###### 8.3.4.4.1 `category`元素

=== "中文"

    `category` 元素指定包内容的类别。

    该元素可以具有“简历(Resume)”、“信函(Letter)”、“财务预测(Financial Forecast)”、“提案(Proposal)”和“技术演示(Technical Presentation)”等值。 该元素不应有任何属性。

    该元素的内容由`xsd:string`简单类型定义。
    
    该元素的 W3C XML 架构定义位于架构`opc-coreProperties.xsd`（[C.3]）中。
    
    EXAMPLE
    
    类别元素如 [8.3.1] 中的示例所示。

    ```xml
    <category>Specification</category>
    ```

=== "英文"

    **category element**

    A `category` element specifies the category of the content of the package.
    
    This element can have values such as “Resume”, “Letter”, “Financial Forecast”, “Proposal”, and “Technical Presentation”. This element shall have no attributes.

    The content of this element is defined by the `xsd:string` simple type.
    
    The W3C XML Schema definition of this element is in the schema `opc-coreProperties.xsd` ([C.3]).
    
    EXAMPLE
    
    A category element is in the example in [8.3.1].

    ```xml
    <category>Specification</category>
    ```

###### 8.3.4.4.2 `contentStatus`元素

=== "中文"

    `contentStatus`元素指定包内容的状态。

    该元素可以具有 “Draft”、“Reviewed” 和 “Final” 等值。该元素不应有任何属性。
    
    该元素的内容由 `xsd:string` 简单类型定义。
    
    该元素的 W3C XML 架构定义位于架构 `opc-coreProperties.xsd`（[C.3]）中。
    
    EXAMPLE

    [8.3.1]中的例子包含

    ```xml
    <contentStatus>Reviewed</contentStatus>
    ```

=== "英文"

    **contentStatus element**

    A `contentStatus` element specifies the status of the content of the package.
    
    This element can have values such as “Draft”, “Reviewed”, and “Final”.This element shall have no attributes.
    
    The content of this element is defined by the `xsd:string` simple type.
    
    The W3C XML Schema definition of this element is in the schema `opc-coreProperties.xsd` ([C.3]).
    
    EXAMPLE

    The example in [8.3.1] contains

    ```xml
    <contentStatus>Reviewed</contentStatus>
    ```

###### 8.3.4.4.3 `keywords`元素

=== "中文"

    `keywords` 元素指定包内容的关键字。
    
    `keywords` 元素应具有可选属性 `xml:lang`，如 XML 1.0 所定义。 `keywords` 元素具有混合内容模型，使得每个关键字都可以由具有`xml:lang`属性的值元素单独包装。
    
    EXAMPLE 以下 `keywords` 元素的实例包含英语（加拿大）、英语（美国）和法语（法国）的关键字：

    ```xml
    <keywords xml:lang="en-US">
         color
         <value xml:lang="en-CA">colour</value>
         <value xml:lang="fr-FR">couleur</value>
    </keywords>
    ```
    
    此元素的内容模型(content model)由 W3C XML Schema 的复杂类型 [`CT_Keywords`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_Keywords.html) 定义，在 Schema `opc-coreProperties.xsd` ([C.3]) 中定义。

=== "英文"

    **keywords element**

    A `keywords` element specifies the keywords for the content of the package.
    
    A keywords element shall have an optional attribute `xml:lang`, as defined by XML 1.0. A `keywords` element has a mixed content model such that each keyword can be wrapped by a value element having an `xml:lang` attribute individually.
    
    EXAMPLE The following instance of the keywords element has keywords in English (Canada), English (U.S.), and French (France):

    ```xml
    <keywords xml:lang="en-US">
         color
         <value xml:lang="en-CA">colour</value>
         <value xml:lang="fr-FR">couleur</value>
    </keywords>
    ```

    The W3C XML Schema definition of this element's content model in the complex type [`CT_Keywords`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_Keywords.html), which is defined in the schema opc-coreProperties.xsd ([C.3]).

###### 8.3.4.4.4 `value`元素

=== "中文"

    `value` 元素指定包内容的关键字。
    
    `value` 元素应具有可选属性 `xml:lang`，如 XML 1.0 规范所定义。
    
    此元素的内容模型(content model)由 W3C XML Schema 的复杂类型 [`CT_Keywords`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_Keywords.html) 定义，在 Schema `opc-coreProperties.xsd` ([C.3]) 中定义。

=== "英文"

    **value element**

    A `value` element specifies a keyword for the content of the package.
    
    A `value` element shall have an optional attribute `xml:lang`, as defined by the XML 1.0 specification.
    
    The W3C XML Schema definition of this element's content model is the complex type [`CT_Keyword`](https://sc34wg4.github.io/OOXMLSchemas/documentation/Part2/opc-coreProperties/opc-coreProperties_CT_Keyword.html), which is defined in the schema opc-coreProperties.xsd ([C.3]).

###### 8.3.4.4.5 `lastModifiedBy`元素

=== "中文"

    `lastModifiedBy`元素指定谁修改了包的内容。
    
    EXAMPLE 1 姓名、电子邮件地址或员工 ID。

    该元素不应有任何属性。
    
    该元素的内容由 `xsd:string` 简单类型定义。

    该元素的 W3C XML Schema定义是Schema `opc-coreProperties.xsd` ([C.3])。
    
    EXAMPLE 2 [8.3.1] 中的示例包含

    ```xml
    <lastModifiedBy>Alan Shen</lastModifiedBy>
    ```

=== "英文"

    **lastModifiedBy element**

    A `lastModifiedBy` element specifies who modified the content of the package.
    
    EXAMPLE 1 A name, email address, or employee ID.

    This element shall have no attributes.
    
    The content of this element is defined by the `xsd:string` simple type.

    The W3C XML Schema definition of this element is the schema opc-coreProperties.xsd ([C.3]).
    
    EXAMPLE 2 The example in 8.3.1 contains

    ```xml
    <lastModifiedBy>Alan Shen</lastModifiedBy>
    ```

###### 8.3.4.4.6 `lastPrinted`元素

=== "中文"

    `lastPrinted` 元素 指定上次打印包的内容的时间。

    该元素不应有任何属性。
    
    该元素的内容由 `xsd:dateTime` 简单类型定义。

    该元素的 W3C XML Schema定义是Schema `opc-coreProperties.xsd` ([C.3])。
    
    EXAMPLE 1 [8.3.1]中的例子包含

    ```xml
    <lastPrinted>2017-01-01</lastPrinted>
    ```

    EXAMPLE 2

    ```xml
    <lastPrinted>2017-04-17T14:20:10+09:00</lastPrinted>
    ```

=== "英文"

    **lastPrinted element**

    A `lastPrinted` element specifies when the content of the package was printed last time.
    
    This element shall have no attributes.
    
    The content of this element is defined by the `xsd:dateTime` simple type.
    
    The W3C XML Schema definition of this element is the schema opc-coreProperties.xsd ([C.3]).
    
    EXAMPLE 1 The example in [8.3.1] contains

    ```xml
    <lastPrinted>2017-01-01</lastPrinted>
    ```

    EXAMPLE 2

    ```xml
    <lastPrinted>2017-04-17T14:20:10+09:00</lastPrinted>
    ```

###### 8.3.4.4.7 `revision`元素

=== "中文"

    `revision` 元素指定包内容的修订号。
    
    该元素不应有任何属性。
    
    该元素的内容由 `xsd:string` 简单类型定义。

    该元素的 W3C XML Schema定义是Schema `opc-coreProperties.xsd` ([C.3])。
    
    EXAMPLE

    ```xml
    <revision>4</revision>
    ```

=== "英文"

    **revision element**

    A `revision` element specifies the revision number of the content of the package
    
    This element shall have no attributes.
    
    The content of this element is defined by the `xsd:string` simple type.

    The W3C XML Schema definition of this element is the schema opc-coreProperties.xsd (C.3).
    
    EXAMPLE

    ```xml
    <revision>4</revision>
    ```

###### 8.3.4.4.8 `version`元素

=== "中文"

    `version` 元素指定包内容的版本。
    
    该元素不应有任何属性。
    
    该元素的内容由`xsd:string`简单类型定义。

    该元素的 W3C XML Schema定义是Schema `opc-coreProperties.xsd` ([C.3])。

    EXAMPLE

    ```xml
    <version>1.0</version>
    ```

=== "英文"

    **version element**

    A `version` element specifies the version of the content of the package.

    This element shall have no attributes.
    
    The content of this element is defined by the `xsd:string` simple type.
    
    The W3C XML Schema definition of this element is the schema opc-coreProperties.xsd ([C.3]).

    EXAMPLE

    ```xml
    <version>1.0</version>
    ```

## 9. 缩略图

=== "中文"

    缩略图部件应是由部件关系或包关系标识的图像部件。 该关系应具有缩略图部件的关系类型(relationship type)，如[附录 E] 中所定义。
    
    NOTE 缩略图部件可用于帮助最终用户识别包的各个部件或整个包。

=== "英文"

    **Thumbnails**

    Thumbnail parts shall be image parts identified by either a part relationship or a package relationship. This relationship shall have a relationship type for Thumbnail parts, as defined in [Annex E].
    
    NOTE Thumbnail parts can be used to help end-users identify parts of a package or a package as a whole.

## 10. 数字签名

**Digital signatures**

### 10.1 General

=== "中文"

    包可以包括指定包的某些部件已被签名的标记。 本节描述 OPC 如何在构建此标记时应用 W3C 建议“XML 签名语法和处理”。

=== "英文"

    **General**

    A package may include markup specifying that parts of a package have been signed. This clause describes how OPC applies the W3C Recommendation “XML-Signature Syntax and Processing” in the construction of this markup.

其他目录:

参考原文:

- 10.2 Overview of OPC-specific restrictions and extensions to “XML-Signature Syntax and Processing”
- 10.3 Choosing content to sign
- 10.4 Digital signature parts
    - 10.4.1 General
    - 10.4.2 Digital Signature Origin part
    - 10.4.3 Digital Signature XML Signature part
    - 10.4.4 Digital Signature Certificate part
- 10.5 Digital signature markup
    - 10.5.1 Genera
    - 10.5.2 Support for versioning and extensibility
    - 10.5.3 Signature element
    - 10.5.4 SignedInfo element
    - 10.5.5 CanonicalizationMethod element
    - 10.5.6 SignatureMethod element
    - 10.5.7 Reference element
        - 10.5.7.1 Genera
        - 10.5.7.2 Reference element as a child of a SignedInfo element
        - 10.5.7.3 Reference element as a child of a Manifest element
    - 10.5.8 Transform element
        - 10.5.8.1 General
        - 10.5.8.2 Transform element representing a Relationships transform
    - 10.5.9 RelationshipReference element
    - 10.5.10 RelationshipsGroupReference element
    - 10.5.11 DigestMethod element
    - 10.5.12 Object element
        - 10.5.12.1 General
        - 10.5.12.2 OPC-specific Object element
        - 10.5.12.3 Application-Defined Object element
    - 10.5.13 Manifest element
    - 10.5.14 SignatureProperty element
    - 10.5.15 SignatureTime element
    - 10.5.16 Format element
    - 10.5.17 Value element
    - 10.5.18 XPath element
- 10.6 Relationships transform algorithm
- 10.7 Digital signature example
- 10.8 Generating signatures
- 10.9 Validating signatures

## Annex A (informative) 生成相对引用的预处理

=== "中文"

    相对引用可用于引用部件。 类似于但不是严格相对引用的 Unicode 字符串也用于引用部件。 例如，“\a.xml” 不是相对引用，因为 RFC 3986 或 RFC 3987 中不允许使用反斜杠字符。
    
    一些实现提供了对此类 Unicode 字符串的预处理，以将它们替换为相对引用。 此预处理可能涉及（但不限于）以下一些操作：

    - 对每个左括号（“`[`”）和右括号（“`]`”）进行百分比编码。
    - 对每个空格字符进行百分比编码 (U+0020)。
    - 对后面不跟有八位字节值的十六进制表示法的每个百分号 (“%”) 字符进行百分比编码。
    - 对每个百分比编码的非保留字符进行取消百分比编码。
    - 对每个正斜杠（“/”）和反斜杠（“\”）进行取消百分比编码。
    - 将所有反斜杠转换为正斜杠。
    - 如果存在于包含非点 (“.”) 字符的段中，请从每个段中删除尾随点 (“.”) 字符。
    - 将每次出现的多个连续正斜杠 (“/”) 替换为单个正斜杠。
    - 如果存在单个尾随正斜杠 (“/”)，请删除该尾随正斜杠。
    - 删除由三个或更多点组成的完整线段。

    转换为相对引用的 Unicode 字符串示例如下所示：

    | **Unicode string** | **Relative reference** |
    | -------------- | -----------------|
    | /A B.xml | /A%20B.xml |
    | /%41/%61.xml | /A/a.xml |
    | /%25XY.xml | /%25XY.xml |
    | /%XY.xml | /%25XY.xml |
    | /%2541.xml | /%2541.xml |
    | /%2e/%2e/a.xml | /a.xml |
    | \a.xml | /a.xml |
    | \%41.xml | /A.xml |
    | /%D1%86.xml | /%D1%86.xml |
    | \%2e/a.xml | /a.xml |

=== "英文"

    **Preprocessing for generating relative references**

    Relative references are available for referencing parts. Unicode strings that are similar to but are not strictly relative references are also used to reference parts. For example, "\a.xml" is not a relative reference since the backslash character is disallowed in RFC 3986 or RFC 3987.
    
    Some implementations provide preprocessing of such Unicode strings to replace them with relative references. This preprocessing can involve some of (but is not limited to) the following actions:

    - Percent-encode each open bracket (“`[`”) and close bracket (“`]`”).
    - Percent-encode each space character (U+0020).
    - Percent-encode each percent (“%”) character that is not followed by a hexadecimal notation of an octet value.
    - Un-percent-encode each percent-encoded unreserved character.
    - Un-percent-encode each forward slash (“/”) and back slash (“\”).
    - Convert all back slashes to forward slashes.
    - If present in a segment containing non-dot (“.”) characters, remove trailing dot (“.”) characters from each segment.
    - Replace each occurrence of multiple consecutive forward slashes (“/”) with a single forward slash.
    - If a single trailing forward slash (“/”) is present, remove that trailing forward slash.
    - Remove complete segments that consist of three or more dots.

    Examples of Unicode strings converted to relative references are shown below:

    | **Unicode string** | **Relative reference** |
    | -------------- | -----------------|
    | /A B.xml | /A%20B.xml |
    | /%41/%61.xml | /A/a.xml |
    | /%25XY.xml | /%25XY.xml |
    | /%XY.xml | /%25XY.xml |
    | /%2541.xml | /%2541.xml |
    | /%2e/%2e/a.xml | /a.xml |
    | \a.xml | /a.xml |
    | \%41.xml | /A.xml |
    | /%D1%86.xml | /%D1%86.xml |
    | \%2e/a.xml | /a.xml |

## Annex B (normative) 使用 ZIP 功能的限制和说明

**Constraints and clarifications on the use of ZIP features**

### B.1 常规

=== "中文"

    本附录规定了 ZIP 格式功能的要求和建议。 代表物理包的 ZIP 文件应满足指定的要求，并且还应遵循指定的建议。
    
    本附录与选择使用 ZIP 表示物理包的（消费、生产或传递）物理包实现者特别相关。

=== "英文"

    **General**

    This annex specifies requirements and recommendations on features of the ZIP format. A ZIP file representing a physical package shall satisfy the specified requirements and should also follow the specified recommendations.
    
    This annex is of particular relevance to (consuming, producing, or pass-through) physical package implementers that choose to use ZIP to represent physical packages.

### B.2 归档文件头一致性

=== "中文"

    描述存储在档案中的文件的数据在本地文件头和数据描述符以及中央目录记录内的文件头中基本上是重复的。 
    对于要成为包的物理层的 ZIP 文件，包实现者应确保 ZIP 文件在中央目录内的每个文件头以及相应的本地文件头和数据描述符对的适当字段中保存相同的值，
    当数据描述符存在，除了表 B.5 中针对通用位标志位 3 所描述的情况之外。

=== "英文"

    **Archive file header consistency**

    Data describing files stored in the archive is substantially duplicated in the Local File Headers and Data Descriptors, and in the File headers within the Central Directory Record. For a ZIP file to be a physical layer for a package, the package implementer shall ensure that the ZIP file holds equal values in the appropriate fields of every File Header within the Central Directory and the corresponding Local File Header and Data Descriptor pair, when the Data Descriptor exists, except as described in Table B.5 for bit 3 of generalpurpose bit flags.

### B.3 数据描述符签名

=== "中文"

    包可能在数据描述符的开头、crc-32 字段之前包含一个 4 字节签名值 0x08074b50。 包实现者应该能够读取包，无论签名是否存在。

=== "英文"

    **Data descriptor signature**

    Packages may contain a 4-byte signature value 0x08074b50 at the beginning of Data Descriptors, immediately before the crc-32 field. Package implementers should be able to read packages, whether or not a signature exists.

### B.4 包实现者的要求

**Requirements on package implementers**

参考原文档

## Annex C (normative) W3C XML Schema

### C.1 常规

=== "中文"

    本文档附带一系列使用“W3C XML 模式结构”和“W3C XML 模式数据类型”中指定的语法定义的模式。 
    此规范附带一个名为 `OpenPackagingConventionsXMLSchema.zip` 的 ZIP 文件，其中包含所有架构。

=== "英文"

    **General**

    This document is accompanied by a family of schemas defined using the syntax specified in “W3C XML Schema Structures” and “W3C XML Schema Datatypes.” A ZIP file called `OpenPackagingConventionsXMLSchema.zip` containing all schemas accompanies this specification.

### C.2 媒体类型流

**Media Types stream**

See file `opc-contentTypes.xsd`.

### C.3 核心属性部件

**Core Properties part**

See file `opc-coreProperties.xsd`.

### C.4 数字签名 XML 签名标记

**Digital signature XML signature markup**

See file `opc-digSig.xsd`.

### C.5 关系部件

**Relationships part**

See file `opc-relationships.xsd`.

## Annex D (informative) Schemas - RELAX NG

### D.1 General

=== "中文"

    本文档附带一系列使用 RELAX NG 语法定义的模式。 本规范附带一个名为 “OpenPackagingConventions-RELAXNG.zip” 的 ZIP 文件，其中包含所有Schema。
    
    如果架构的 RELAX NG 版本与其相应的 XSD 架构之间存在差异，则 XSD 架构是最终版本。

=== "英文"

    **General**

    This document is accompanied by a family of schemas defined using the RELAX NG syntax. A ZIP file called `OpenPackagingConventions-RELAXNG.zip` containing all schemas accompanies this specification.
    
    If discrepancies exist between the RELAX NG version of a schema and its corresponding XSD Schema, the XSD Schema is the definitive version.

### D.2 媒体类型流

**Media Types stream**

See file opc-contentTypes.rnc.

### D.3 核心属性部件

**Core Properties part**

See file `opc-coreProperties.rnc`.

The schema is available at: <http://standards.iso.org/iso-iec/29500/-2/ed4/en/OpenPackagingConventions-RELAXNG/opc-coreProperties.rnc>.

### D.4 数字签名 XML 签名标记

**Digital signature XML signature markup**

See files `opc-digSig.rnc` and `security_any.rnc`。

### D.5 关系部件

**Relationships part**

See file `opc-relationships.rnc`.

This schema is available at: <http://standards.iso.org/iso-iec/29500/-2/ed4/en/OpenPackagingConventions-RELAXNG/opc-relationships.rnc>.

### D.6 其他资源

Additional resources

#### D.6.1 XML

See file `xml.rnc`.

#### D.6.2 XML数字签名核心

**XML digital signature core**

See file `xmldsig-core-schema.rnc`.

## Annex E (normative) 标准命名空间和媒体类型

=== "中文"

    表 E.1 列出了包中可用的命名空间。
    
    表 E.1 — 包范围的命名空间

    <table>
        <thead>
            <tr>
                <th>**描述**</th>
                <th>**命名空间 URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>媒体类型流</br>(Media Types stream)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/content-types"</td>
            </tr>
            <tr>
                <td>核心属性(Core Properties)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/metadata/core-properties"</td>
            </tr>
            <tr>
                <td>数字签名</br>(Digital Signatures)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/digitalsignature"</td>
            </tr>
            <tr>
                <td>关系</br>(Relationships)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships"</td>
            </tr>
        </tbody>
    </table>

    表 E.2 列出了本文档中定义的部件的媒体类型。
    
    表 E.2 — 包范围的媒体类型(media types)

    <table>
        <thead>
            <tr>
                <th>**描述**</th>
                <th>**命名空间 URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>核心属性部件</br>(Core Properties part)</td>
                <td>"application/vnd.openxmlformats-package.coreproperties+xml"</td>
            </tr>
            <tr>
                <td>数字签名证书部件</br>(Digital Signature Certificate part)</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-certificate"</td>
            </tr>
            <tr>
                <td>数字签名起源部件</br>(Digital Signature Origin part)</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-origin"</td>
            </tr>
            <tr>
                <td>数字签名 XML 签名部件</br>(Digital Signature XML Signature part)</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-xmlsignature+xml"</td>
            </tr>
            <tr>
                <td>关系部件</br>(Relationships part)</td>
                <td>"application/vnd.openxmlformatspackage.relationships+xml"</td>
            </tr>
        </tbody>
    </table>

    表 E.3 列出了包中可用的关系类型。
    
    表 E.3 — 包范围的关系类型(relationship types)

    <table>
        <thead>
            <tr>
                <th>**描述**</th>
                <th>**命名空间 URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>核心属性</br>(Core Properties)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/metadata/core-properties"</td>
            </tr>
            <tr>
                <td>数字签名</br>(Digital Signature)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/signature"</td>
            </tr>
            <tr>
                <td>数字签名证书</br>(Digital Signature Certificate)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/certificate"</td>
            </tr>
            <tr>
                <td>数字签名起源</br>(Digital Signature Origin)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/origin"</td>
            </tr>
            <tr>
                <td>缩略图</br>(Thumbnail)</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/metadata/thumbnail"</td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **Standard namespaces and media types**

    The namespaces available for use in a package are listed in Table E.1.
    
    Table E.1 — Package-wide namespaces

    <table>
        <thead>
            <tr>
                <th>**Description**</th>
                <th>**Namespace URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Media Types stream</td>
                <td>"http://schemas.openxmlformats.org/package/2006/content-types"</td>
            </tr>
            <tr>
                <td>Core Properties</td>
                <td>"http://schemas.openxmlformats.org/package/2006/metadata/coreproperties"</td>
            </tr>
            <tr>
                <td>Digital Signatures</td>
                <td>"http://schemas.openxmlformats.org/package/2006/digitalsignature"</td>
            </tr>
            <tr>
                <td>Relationships</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships"</td>
            </tr>
        </tbody>
    </table>

    The media types for the parts defined in this document are listed in Table E.2.
    
    Table E.2 — Package-wide media types

    <table>
        <thead>
            <tr>
                <th>**Description**</th>
                <th>**Namespace URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Core Properties part</td>
                <td>"application/vnd.openxmlformats-package.coreproperties+xml"</td>
            </tr>
            <tr>
                <td>Digital Signature Certificate part</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-certificate"</td>
            </tr>
            <tr>
                <td>Digital Signature Origin part</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-origin"</td>
            </tr>
            <tr>
                <td>Digital Signature XML Signature part</td>
                <td>"application/vnd.openxmlformats-package.digitalsignature-xmlsignature+xml"</td>
            </tr>
            <tr>
                <td>Relationships part</td>
                <td>"application/vnd.openxmlformatspackage.relationships+xml"</td>
            </tr>
        </tbody>
    </table>

    The relationship types available for use in a package are listed in Table E.3.
    
    Table E.3 — Package-wide relationship types

    <table>
        <thead>
            <tr>
                <th>**Description**</th>
                <th>**Namespace URI**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Core Properties</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/metadata/core-properties"</td>
            </tr>
            <tr>
                <td>Digital Signature</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/signature"</td>
            </tr>
            <tr>
                <td>Digital Signature Certificate</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/certificate"</td>
            </tr>
            <tr>
                <td>Digital Signature Origin</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/digital-signature/origin"</td>
            </tr>
            <tr>
                <td>Thumbnail</td>
                <td>"http://schemas.openxmlformats.org/package/2006/relationships/metadata/thumbnail"</td>
            </tr>
        </tbody>
    </table>

## Annex F (informative) 物理包模型设计考虑因素

**Physical package model design considerations**(考虑因素)

### F.1 General

=== "中文"

    物理包模型定义了包的生产和消费方式。 该模型基于三个组件：生产者、消费者以及它们之间的管道，如图 F.1 所示。

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-f-1.png)
      <figcaption>Figure F.1 — 物理封装模型的组成部分</figcaption>
    </figure>

    生产者是编写包的软件或设备。 消费者是读取包的软件或设备。设备是硬件，例如执行单个功能或一组功能的打印机或扫描仪。数据通过管道从生产者传送到消费者。

    在本地访问中，管道将数据直接从生产者传送到单个设备上的消费者。

    在网络访问中，消费者和生产者通过协议相互通信。 该管道的重要通信特征是速度和请求延迟。 例如，这种通信可以跨进程边界或在服务器和台式计算机之间发生。

    为了最大限度地提高性能，物理格式的设计者会考虑访问方式、布局方式和通信方式。

=== "英文"

    **General**

    The physical package model defines the ways in which packages are produced and consumed. This model is based on three components: a producer, a consumer, and a pipe between them, as shown in Figure F.1.

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-f-1.png)
      <figcaption>Figure F.1 — Components of the physical package model</figcaption>
    </figure>

    A producer is software or a device that writes packages. A consumer is software or a device that reads packages. A device is hardware, such as a printer or scanner that performs a single function or set of functions. Data is carried from the producer to the consumer by a pipe.

    In local access, the pipe carries data directly from a producer to a consumer on a single device.

    In networked access the consumer and the producer communicate with each other over a protocol. The significant communication characteristics of this pipe are speed and request latency. For example, this communication can occur across a process boundary or between a server and a desktop computer.

    In order to maximize performance, designers of physical formats consider access style, layout style, and communication style.

### F.2 访问方式

**Access styles**

#### F.2.1 常规

=== "中文"

    进行本地访问或网络访问的访问方式决定了处理和输入输出操作之间可能的同时性。

=== "英文"

    **General**

    The access style in which local access or networked access is conducted determines the simultaneity possible between processing and input-output operations.

#### F.2.2 直接访问消费

=== "中文"

    直接访问消费允许消费者请求所需的包的特定部分，而无需顺序处理包的前面部分。 例如，字节范围请求。 这是最常见的访问方式。

=== "英文"

    **Direct access consumption**

    Direct access consumption allows consumers to request the specific portion of the package desired, without sequentially processing the preceding parts of the package. For example, a byte-range request. This is the most common access style.

#### F.2.3 流式消费

=== "中文"

    流式消费允许消费者在整个包裹到达之前开始处理部件。 物理格式的设计应允许消费者在数据包的所有位通过管道传送之前开始解释和处理他们接收到的数据。

    本文档的早期版本定义了流媒体消费的要求。 这个版本放弃了它们，因为 OPC 的不同应用对流消耗(streaming consumption)有不同的要求。

    然而，为了允许流式消费，建议媒体类型流没有`Default`元素，并且应该为包中的每个部件都有一个`Override`元素。 每个`Override`元素应出现在其对应的部件之前或附近

=== "英文"

    **Streaming consumption**

    Streaming consumption allows consumers to begin processing parts before the entire package has arrived. Physical formats should be designed to allow consumers to begin interpreting and processing the data they receive before all of the bits of the package have been delivered through the pipe.

    The earlier editions of this document defined requirements for streaming consumption. This edition dropped them since different applications of OPC impose different requirements on streaming consumption.

    However, to allow streaming consumption, it is recommended that the Media Types stream have no `Default` elements and should have one `Override` element for each part in the package. Each `Override` element should appear before or in close proximity to the part to which it corresponds.

#### F.2.4 流式创建

=== "中文"

    流式创建允许生产者开始将部件写入包，而无需提前知道要写入的所有部件。 例如，当应用程序开始构建打印假脱机文件包时，它并不总是知道该包包含多少页。 同样，生成报告的程序最初并不总是知道报告有多长或有多少张图片。

    为了支持流式创建，包实现者应该允许生产者在添加其他部件之后添加部件。 消费者不得要求生产者说明他们在开始编写时将创建多少部件。 包实现者应该允许生产者在不知道该部件的最终长度的情况下开始编写该部件的内容。

=== "英文"

    **Streaming creation**

    Streaming creation allows producers to begin writing parts to the package without knowing in advance all of the parts that are to be written. For example, when an application begins to build a print spool file package, it does not always know how many pages the package contains. Likewise, a program that is generating a report does not always know initially how long the report is or how many pictures it has.

    In order to support streaming creation, the package implementer should allow a producer to add parts after other parts have already been added. A consumer shall not require a producer to state how many parts they will create when they start writing. The package implementer should allow a producer to begin writing the contents of a part without knowing the ultimate length of the part.

#### F.2.5 同时创建和消费

=== "中文"

    同时创建和消费允许流式创建和流式消费在包上同时发生。 由于可以在使用它的流水线架构中实现的好处，包实现者应该支持在物理包中同时创建和使用。

=== "英文"

    **Simultaneous creation and consumption**

    Simultaneous creation and consumption allows streaming creation and streaming consumption to happen at the same time on a package. Because of the benefits that can be realized within pipelined architectures that use it, the package implementer should support simultaneous creation and consumption in the physical package.

### F.3 布局样式

**Layout styles**

#### F.3.1 常规

=== "中文"

    包内部件排序的样式称为布局样式。 部件可以按两种样式之一排列：简单排序或交错排序。

=== "英文"

    **General**

    The style in which parts are ordered within a package is referred to as the layout style. Parts can be arranged in one of two styles: simple ordering or interleaved ordering. 

#### F.3.2 简单排序

=== "中文"

    通过简单排序，部件可以连续排列。 当按顺序传送包时，第一部分的所有字节首先到达，然后是第二部分的所有字节，依此类推。 当这样的包使用简单排序时，每个部分的所有字节都是连续存储的。

    EXAMPLE 简单排序的性能瓶颈

    图 F.2 包含两部分：描述页面内容的页面部分 (`markup/page.xml`) 和引用出现在页面上的图像的图像部分 (`images/picture.jpeg`)。 通过简单的排序，页面部分的所有字节都在图像部件的字节之前传递。

    图 F.2 说明了这种情况。 在接收到整个页面部件和图像部件之前，无法显示图像。 在某些情况下，例如高速网络上的小包裹，这可能是可以接受的。 在其他情况下，必须通读所有 `markup/page.xml` 才能获取图像会导致性能不可接受或产生不合理的内存需求。

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-f-3.png)
      <figcaption>Figure F.3 — 简单排序的字节传送顺序</figcaption>
    </figure>

=== "英文"

    **Simple ordering**

    With simple ordering, parts are arranged contiguously. When a package is delivered sequentially, all of the bytes for the first part arrive first, followed by all of the bytes for the second part, and so on. When such a package uses simple ordering, all of the bytes for each part are stored contiguously.

    EXAMPLE Performance bottleneck with simple ordering

    Figure F.2 contains two parts: a page part (markup/page.xml) describing the contents of a page, and an image part (images/picture.jpeg) referring to an image that appears on the page. With simple ordering, all of the bytes of the page part are delivered before the bytes of the image part.

    Figure F.2 illustrates this scenario. The image cannot be displayed until the entire page part and the image part have been received. In some circumstances, such as small packages on a high-speed network, this might be acceptable. In others, having to read through all of markup/page.xml to get to the image results in unacceptable performance or places unreasonable memory demands.

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-f-3.png)
      <figcaption>Figure F.3 — Delivery order of bytes with simple ordering</figcaption>
    </figure>

#### F.3.3 交错排序

=== "中文"

    通过交错排序，各个部件交错排列，从而在某些情况下实现最佳性能。 例如，交错排序提高了多媒体播放的性能，其中视频和音频同时传送，并且内联资源引用（其中对图像的引用出现在标记内）。

    通过将部件分解成片段并交错这些片段，可以优化性能，同时允许轻松重建原始连续部件。
    
    由于它提供的性能优势，包实现者应该支持物理包中的交错。 物理文件中被分成多个部分的部分被视为一个逻辑部分； 这些部件本身不是部件，并且不可寻址。

=== "英文"

    **Interleaved ordering**

    With interleaved ordering, pieces of parts are interleaved, allowing optimal performance in certain scenarios. For example, interleaved ordering improves performance for multi-media playback, where video and audio are delivered simultaneously and inline resource referencing, where a reference to an image occurs within markup.

    By breaking parts into pieces and interleaving those pieces, it is possible to optimize performance while allowing easy reconstruction of the original contiguous part. 
    
    Because of the performance benefits it provides, package implementers should support interleaving in the physical package. A part that is broken into multiple pieces in the physical file is considered one logical part; the pieces themselves are not parts and are not addressable.

### F.4 沟通方式

**Communication styles**

#### F.4.1 常规

=== "中文"

    包及其部件由生产者交付或由消费者访问的风格称为通信风格。 通信可以基于部件的顺序交付或随机访问。 使用的通信方式取决于管道和物理格式的功能。

=== "英文"

    **General**

    The style in which a package and its parts are delivered by a producer or accessed by a consumer is referred to as the communication style. Communication can be based on sequential delivery of or random access to parts. The communication style used depends on the capabilities of both the pipe and the physical format. 

#### F.4.2 顺序交付

=== "中文"

    通过顺序传送，包中的所有物理位都按照它们在包中出现的顺序传送。 一般情况下，所有管道都支持顺序传送。

=== "英文"

    **Sequential delivery**

    With sequential delivery, all of the physical bits in the package are delivered in the order they appear in the package. Generally, all pipes support sequential delivery.

#### F.4.3 随机访问

=== "中文"

    随机访问允许消费者请求不按顺序物理顺序交付部件。 某些管道基于可以启用随机访问的协议，例如支持字节范围的 HTTP 1.1。 为了最大限度地提高性能，包实现者应该支持管道和物理包中的随机访问。 在缺乏这种支持的情况下，消费者需要等待他们需要的部件按顺序交付。

=== "英文"

    **Random access**

    Random access allows consumers to request the delivery of a part out of sequential physical order. Some pipes are based on protocols that can enable random access, for example, HTTP 1.1 with byte-range support. In order to maximize performance, the package implementer should support random access in both the pipe and the physical package. In the absence of this support, consumers need to wait until the parts they need are delivered sequentially.

## Annex G (informative) ECMA-376-2021 和 ECMA-376:2006 之间的差异

**Differences between ECMA-376-2021 and ECMA-376:2006**

### G.1 General

=== "中文"

    本附录记录了本文档中定义的开放包装公约版本与 ECMA-376:2006 之间的语法差异（请参阅参考文献 [^5]）。

=== "英文"

    **General**

    This annex documents the syntactic differences between the versions of the Open Packaging Conventions defined in this document and ECMA-376:2006 (see Reference [^5]).

### G.2 XML元素

=== "中文"

    以下 XML 元素包含在本文档中，但未包含在 ECMA-376:2006 中：
    
    - `value` 元素 ([8.3.4.4.4])
    
    以下 XML 元素包含在 ECMA-376:2006 中，但未包含在本文档中：
    
    - `contentType` 元素

=== "英文"

    **XML elements**

    The following XML element is included in this document but are not included in ECMA-376:2006:
    
    - The value element ([8.3.4.4.4])
    
    The following XML element is included in ECMA-376:2006 but are not included in this document:
    
    - The contentType element

### G.3 XML属性

**XML attributes**

No changes.

### G.4 XML枚举值

**XML enumeration values**

No changes.

### G.5 XML simple types

**XML simple types**

No changes.

### G.6 部件名称

=== "中文"

    本文档允许使用非 ASCII 部件名称，但 ECMA-376:2006 不允许使用非 ASCII 部分名称。

=== "英文"

    **Part names**

    Non-ASCII part names are allowed by this document but are disallowed by ECMA-376:2006.

## Annex H (Informative) 包示例

=== "中文"

=== "英文"

**Package example**

### H.1 概述

=== "中文"

    本附录描述了代表 Microsoft® Office 文档的抽象包和物理包。

=== "英文"

    **General**

    This annex depicts an abstract package and a physical package representing a `Microsoft® Office document`.

### H.2 抽象包

=== "中文"

    这个抽象包包含5个部件: `/_rels/.rels`, `/docProps/core.xml`, `/word/_rels/document.xml.rels`, `/word/document.xml`, and `/word/settings.xml`. 见图 H.1

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-h-1.png)
      <figcaption>图 H.1 — 抽象封装示例</figcaption>
    </figure>

    其中两个(`/_rels/.rels` 和 `/word/_rels/document.xml.rels`)是关系部件，三个(`/word/document.xml`, `/docProps/core.xml`, `/word/settings.xml`)是非关系部件，其中 `_rels/.rels` 是包关系部分，`/word/_rels/document.xml.rels`是与`/word/document.xml`关联的关系部分。封装的关系部件包含从包到`/docProps/core.xml`和`/word/document.xml`的两个关系。 关系部件包含从`/word/document.xml`到`/word/settings.xml`的关系。

=== "英文"

    **Abstract package**

    This abstract package contains five parts: `/_rels/.rels, /docProps/core.xml`, `/word/_rels/document.xml.rels`, `/word/document.xml`, and `/word/settings.xml`. See Figure H.1

    <figure markdown>
      ![Alt text](./imgs/openxml-ref-2-h-1.png)
      <figcaption>Figure H.1 — An example abstract package</figcaption>
    </figure>

    Two of these parts are Relationships parts (`/_rels/.rels` and `/word/_rels/document.xml.rels`) and three of them are non-Relationships parts (`/word/document.xml`, `/docProps/core.xml`, and `/word/settings.xml`), where `_rels/.rels` is a package Relationships part and `/word/_rels/document.xml.rels` is a part Relationships part associated with `/word/document.xml`. The package Relationships part contains two relationships from the package to `/docProps/core.xml` and `/word/document.xml`, respectively. The part Relationships part contains a relationship from `/word/document.xml` to `/word/settings.xml`.

### H.3 物理包

=== "中文"

    该物理包 (empty.docx) 是一个 ZIP 文件。 此 ZIP 文件中的 ZIP 项目为`_rels/.rels`、`docProps/core.xml`、`word/_rels/document.xml.rels`、`word/document.xml`和`word/settings.xml` 和 `[Content_Types].xml`。

    除了`[Content_Types].xml`之外，这些 ZIP 项目代表部件。 请注意，部件名称的第一个字符是“/”。 `[Content_Types].xml` 表示媒体类型流。

=== "英文"

    **Physical package**

    This physical package (empty.docx) is a ZIP file. The ZIP items in this ZIP file are `_rels/.rels`, `docProps/core.xml`, `word/_rels/document.xml.rels`, `word/document.xml`, and `word/settings.xml`, and `[Content_Types].xml`.

    With the exception of `[Content_Types].xml`, these ZIP items represent parts. Note that part names have `/` as the first character. `[Content_Types].xml` represents the Media Types stream.

## 参考书目

**Bibliography**

[^1]: Character Model for the World Wide Web: String Matching, W3C Working Group Note, 04 February 2019, available at <https://www.w3.org/TR/2019/NOTE-charmod-norm-20190204/>
[^2]: Date and Time Formats, W3C NOTE 19980827, 1997, available at <http://www.w3.org/TR/1998/NOTEdatetime-19980827>
[^3]: XML Security RELAX NG Schemas, W3C Working Group Note 11 April 2013, available at <https://www.w3.org/TR/xmlsec-rngschema/>
[^4]: ISO/IEC TR 30114-1, Information technology -- Extensions of Office Open XML file formats -- Part 1: Guidelines, available at <https://standards.iso.org/ittf/PubliclyAvailableStandards/index.html>
[^5]: ECMA-376:2006 Office Open XML File Formats, 1st edition (December 2006), available at <https://www.ecma-international.org/publications-and-standards/standards/ecma-376/>
[^6]: NIST SP 800-56A Rev. 3, Recommendation for Pair-Wise Key-Establishment Schemes Using Discrete Logarithm Cryptography, available at <https://doi.org/10.6028/NIST.SP.800-56Ar3>, April 2018
[^7]: ISO/IEC 10646, Information technology — Universal coded character set (UCS), available at <https://standards.iso.org>
[^8]: Uniform Resource Identifier (URI) Schemes, available at <https://www.iana.org/assignments/urischemes/uri-schemes.xhtml>

<!--锚点-->

[1]: #1-适用范围
[2]: #2-规范性引用文件
[3]: #3-术语和定义
[3.1]: #31-basics
[3.2]: #32-抽象包模型
[3.3]: #33-物理包模型
[3.4]: #34-数字签名和缩略图
[3.5]: #35-具体实现
[3.6]: #36-核心属性
[4]: #4-一致性
[5]: #5-概述
[6]: #6-抽象封装模型
[6.1]: #61-常规
[6.2]: #62-部件
[6.2.1]: #621-常规
[6.2.2]: #622-部件名称
[6.2.2.1]: #6221-常规
[6.2.2.2]: #6222-syntax
[6.2.2.3]: #6223-抽象包中的部件名称等效性和完整性
[6.2.3]: #623-媒体类型
[6.2.4]: #624-成长提示
[6.2.5]: #625-xml的使用
[6.3]: #63-部件寻址
[6.3.1]: #631-常规
[6.3.2]: #632-打包方案
[6.3.3]: #633-将包-iri-解析为资源
[6.3.5]: #634-编写-iri-包
[6.3.5]: #635-等效性
[6.4]: #64-解决相关引用
[6.4.1]: #641-常规
[6.4.2]: #642-基础-iri
[6.4.3]: #643-例子
[6.4.3.1]: #6431-常规
[6.4.3.2]: #6432-前导斜线-bbarxml
[6.4.3.3]: #6433-没有前导斜杠-barxml
[6.4.3.4]: #6434-点段-barxml
[6.4.3.5]: #6435-点段-barxml
[6.5]: #65-关系
[6.5.1]: #651-常规
[6.5.2]: #652-关系部件
[6.5.2.1]: #6521-关系部件
[6.5.2.2]: #6522-包关系部件
[6.5.2.3]: #6523-部件关系部件
[6.5.3]: #653-关系标记
[6.5.3.1]: #6531-常规
[6.5.3.2]: #6532-支持版本控制和可扩展性
[6.5.3.3]: #6533-关系的元素表示
[6.5.3.4]: #6534-关系元素
[6.5.4]: #654-示例
[6.5.4.1]: #6541-与整个包关联的关系部件
[6.5.4.2]: #6542-与部件关联的关系部件
[6.5.4.3]: #6543-与数字签名标记相关的关系部件
[6.5.4.4]: #6544-针对外部资源的关系
[6.5.4.5]: #6545-具有相同目标的多个关系
[7]: #7-物理封装模型
[7.1]: #71-general
[7.2]: #72-物理映射指南
[7.2.1]: #721-使用物理格式的特征
[7.2.2]: #722-映射组件
[7.2.3]: #723-将媒体类型映射到部件
[7.2.3.1]: #7231-常规
[7.2.3.2]: #7232-媒体类型流标记
[7.2.3.2.1]: #72321-常规
[7.2.3.2.2]: #72322-支持版本控制和可扩展性
[7.2.3.2.3]: #72323-types元素
[7.2.3.2.4]: #72324-default元素
[7.2.3.2.5]: #72325-override元素
[7.2.3.3]: #7233-媒体类型流标记示例
[7.2.3.4]: #7234-在媒体类型流中设置部分媒体类型
[7.2.3.5]: #7235-从媒体类型流中确定部件媒体类型
[7.2.4]: #724-交错
[7.2.5]: #725-将部件名称映射到物理包项目名称
[7.2.5.1]: #7251-常规
[7.2.5.2]: #7252-逻辑项目名称
[7.2.5.3]: #7253-将部件名称映射到逻辑项目名称
[7.2.5.4]: #7254-映射逻辑项名称和物理包项名称
[7.2.5.5]: #7255-将逻辑项名称映射到部件名称
[7.3]: #73-映射到-zip-文件
[7.3.1]: #731-常规
[7.3.2]: #732-映射部件数据
[7.3.3]: #733-zip项名称
[7.3.4]: #734-将逻辑项目名称映射到-zip-项目名称
[7.3.5]: #735-将-zip-项目名称映射到逻辑项目名称
[7.3.6]: #736-zip-包限制
[7.3.7]: #737-映射媒体类型流
[7.3.8]: #738-映射增长提示
[8]: #8-核心属性
[8.1]: #81-常规
[8.2]: #82-核心属性部件
[8.3]: #83-核心属性标记
[8.3.1]: #831-常规
[8.3.2]: #832-支持版本控制和可扩展性
[8.3.3]: #833-coreproperties元素
[8.3.4]: #834-核心属性元素
[8.3.4.1]: #8341-常规
[8.3.4.2]: #8342-iso-15836-1-定义的核心属性元素
[8.3.4.3]: #8343-iso-15836-2-定义的核心属性元素
[8.3.4.4]: #8344-本文档中定义的核心属性元素
[8.3.4.4.1]: #83441-category元素
[8.3.4.4.2]: #83442-contentstatus元素
[8.3.4.4.3]: #83443-keywords元素
[8.3.4.4.4]: #83444-value元素
[8.3.4.4.5]: #83445-lastmodifiedby元素
[8.3.4.4.6]: #83446-lastprinted元素
[8.3.4.4.7]: #83447-revision元素
[8.3.4.4.8]: #83448-version元素
[9]: #9-缩略图
[10]: #10-数字签名
[10.1]: #101-general
[Annex A]: #annex-a-informative-生成相对引用的预处理
[Annex B]: #annex-b-normative-使用-zip-功能的限制和说明
[B.1]: #b1-常规
[B.2]: #b2-归档文件头一致性
[B.3]: #b3-数据描述符签名
[B.4]: #b4-包实现者的要求
[Annex C]: #annex-c-normative-w3c-xml-schema
[C.1]: #c1-常规
[C.2]: #c2-媒体类型流
[C.3]: #c3-核心属性部件
[C.4]: #c4-数字签名-xml-签名标记
[C.5]: #c5-关系部件
[Annex D]: #annex-d-informative-schemas---relax-ng
[D.1]: #d1-general
[D.2]: #d2-媒体类型流
[D.3]: #d3-核心属性部件
[D.4]: #d4-数字签名-xml-签名标记
[D.5]: #d5-关系部件
[D.6]: #d6-其他资源
[D.6.1]: #d61-xml
[D.6.2]: #d62-xml数字签名核心
[Annex E]: #annex-e-normative-标准命名空间和媒体类型
[Annex F]: #annex-f-informative-物理包模型设计考虑因素
[F.1]: #f1-general
[F.2]: #f2-访问方式
[F.2.1]: #f21-常规
[F.2.2]: #f22-直接访问消费
[F.2.3]: #f23-流式消费
[F.2.4]: #f24-流式创建
[F.2.5]: #f25-同时创建和消费
[F.3]: #f3-布局样式
[F.3.1]: #f31-常规
[F.3.2]: #f32-简单排序
[F.3.3]: #f33-交错排序
[F.4]: #f4-沟通方式
[F.4.1]: #f41-常规
[F.4.2]: #f42-顺序交付
[F.4.3]: #f43-随机访问
[Annex G]: #annex-g-informative-ecma-376-2021-和-ecma-3762006-之间的差异
[G.1]: #g1-general
[G.2]: #g2-xml元素
[G.3]: #g3-xml属性
[G.4]: #g4-xml枚举值
[G.5]: #g5-xml-simple-types
[G.6]: #g6-部件名称
[Annex H]: #annex-h-informative-包示例
[H.1]: #h1-概述
[H.2]: #h2-抽象包
[H.3]: #h3-物理包

[附录 A]: #annex-a-informative-生成相对引用的预处理
[附录 B]: #annex-b-normative-使用-zip-功能的限制和说明
[附录 C]: #annex-c-normative-w3c-xml-schema
[附录 D]: #annex-d-informative-schemas---relax-ng
[附录 E]: #annex-e-normative
[附录 F]: #annex-f-informative-物理包模型设计考虑因素
[附录 G]: #annex-g-informative-ecma-376-2021-和-ecma-3762006-之间的差异
[附录 H]: #annex-h-informative-包示例
[第 4 条]: #4-一致性
[第 6 条]: #6-抽象封装模型
[第 7 条]: #7-物理封装模型
