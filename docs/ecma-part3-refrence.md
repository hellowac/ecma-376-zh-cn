# ECMA-376-3

ECMA-376-3, 5

第三版

Office Open XML 文件格式 — 标记

兼容性和扩展性

## 前言

=== "中文"

    为了使本第 5 版标准与 ISO/IEC 29500-3:2015 保持一致，对第 4 版标准进行了修改。本第 5 版和 ISO/IEC 29500-3:2015 均参照第 1 版。因此，第 5 版并未取消或取代第 1 版。然而，第 5 版取消并取代了第 4 版。

    ECMA-376 由以下部分组成：
    
    - Part 1: 基础知识和标记语⾔参考
    - Part 2: 开放式包装约定
    - Part 3: 标记兼容性和可扩展性
    - Part 4: 过渡性迁移功能
    
    附录 A 和 B 仅供参考。

=== "英文"

    Foreword

    Changes from the 4th edition were made to align this 5th edition Standard with ISO/IEC 29500-3:2015. Both this 5th edition and ISO/IEC 29500-3:2015 refer to the 1st edition. As such, this 5th edition does not cancel or replace the 1st edition. This 5th edition does, however, cancel and replace the 4th edition.

    ECMA-376 consists of the following parts:
    
    - Part 1: Fundamentals and Markup Language Reference
    - Part 2: Open Packaging Conventions
    - Part 3: Markup Compatibility and Extensibility
    - Part 4: Transitional Migration Features
    
    Annexes A and B are for information only.

## 简介 

=== "中文"

    ECMA-376 规定了一系列 XML 方案（schema），统称为 Office Open XML，定义了文字处理、电子表格和演示办公文档的 XML 词汇表，以及符合这些方案的办公文档打包。
    
    其目标是使最广泛的工具和平台能够实施 Office Open XML 格式，促进办公自动化应用程序和业务系统之间的互操作性，以及支持和加强文档的归档和保存，所有这些都与现有的 Microsoft® Office 文档库完全兼容。

        "COPYRIGHT NOTICE
        
        © 2015 Ecma International
        
        This document may be copied, published and distributed to others, and certain derivative works of it may be prepared, copied, published, and distributed, in whole or in part, provided that the above copyright notice and this Copyright License and Disclaimer are included on all such copies and derivative works. The only derivative works that are permissible under this Copyright License and Disclaimer are:
        
        (i) works which incorporate all or portion of this document for the purpose of providing commentary or explanation (such as an annotated version of the document),
        
        (ii) works which incorporate all or portion of this document for the purpose of incorporating features that provide accessibility,
        
        (iii) translations of this document into languages other than English and into different formats and
        
        (iv) works by making use of this specification in standard conformant products by implementing (e.g. by copy and paste wholly or partly) the functionality therein.
        
        However, the content of this document itself may not be modified in any way, including by removing the copyright notice or references to Ecma International, except as required to translate it into languages other than English or into a different format.
        
        The official version of an Ecma International document is the English language version on the Ecma International website. In the event of discrepancies between a translated version and the official version, the official version shall govern.
        
        The limited permissions granted above are perpetual and will not be revoked by Ecma International or its successors or assigns.
        
        This document and the information contained herein is provided on an "AS IS" basis and ECMA INTERNATIONAL DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE."

=== "英文"

    Introduction

    ECMA-376 specifies a family of XML schemas, collectively called Office Open XML, that define the XML vocabularies for word-processing, spreadsheet, and presentation office documents, as well as the packaging of office documents that conform to these schemas.
    
    The goal is to enable the implementation of the Office Open XML formats by the widest set of tools and platforms, fostering interoperability across office productivity applications and line-of-business systems, as well as to support and strengthen document archival and preservation, all in a way that is fully compatible with the existing corpus of Microsoft® Office documents.

        "COPYRIGHT NOTICE
        
        © 2015 Ecma International

        This document may be copied, published and distributed to others, and certain derivative works of it may be prepared, copied, published, and distributed, in whole or in part, provided that the above copyright notice and this Copyright License and Disclaimer are included on all such copies and derivative works. The only derivative works that are permissible under this Copyright License and Disclaimer are:
        
        (i) works which incorporate all or portion of this document for the purpose of providing commentary or explanation (such as an annotated version of the document),
        
        (ii) works which incorporate all or portion of this document for the purpose of incorporating features that provide accessibility,
        
        (iii) translations of this document into languages other than English and into different formats and
        
        (iv) works by making use of this specification in standard conformant products by implementing (e.g. by copy and paste wholly or partly) the functionality therein.
        
        However, the content of this document itself may not be modified in any way, including by removing the copyright notice or references to Ecma International, except as required to translate it into languages other than English or into a different format.
        
        The official version of an Ecma International document is the English language version on the Ecma International website. In the event of discrepancies between a translated version and the official version, the official version shall govern.
        
        The limited permissions granted above are perpetual and will not be revoked by Ecma International or its successors or assigns.
        
        This document and the information contained herein is provided on an "AS IS" basis and ECMA INTERNATIONAL DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE."

## 1 范围  

=== "中文"

    ECMA-376 的本部分定义了一套标记规范向前兼容性的约定，不仅适用于本标准第 1 部分和第 4 部分所述的 Office Open XML 规范，也适用于其他标记规范。这些约定使较晚版本的应用程序或扩展程序所创建的 XML 文档能够被较早版本的应用程序所处理。

=== "英文"

    Scope

    This Part of ECMA-376 defines a set of conventions for forward compatibility of markup specifications, applicable not only to Office Open XML specifications as described in Parts 1 and 4 of this Standard, but also to other markup specifications. These conventions allow XML documents created by applications of later versions or extensions to be handled by applications of earlier versions.

## 2 规范性引用文件 

=== "中文"

    下列参考标准对本标准的应用不可或缺。对于注明日期的参考标准，仅适用所引用的版本。对于未注明日期的参考文献，适用参考标准的最新版本（包括任何修订）。
    
    XML，Tim Bray、Jean Paoli、Eve Maler、C. M. Sperberg-McQueen 和 François Yergeau（编辑）。可扩展标记语言（XML）1.0，第五版。万维网联盟。2008.
    
    http://www.w3.org/TR/2008/PER-xml-20080205/. [Note: ECMA-376 本部分的实现不需要支持第五版引入的 XML 特性。 end note]
    
    XML Base, Marsh, Jonathan. XML Base. 万维网联盟。2009. http://www.w3.org/TR/2009/RECxmlbase-20090128/
    
    XML 信息集》，John Cowan 和 Richard Tobin（编辑）。XML 信息集（第二版）》，2004 年 2 月 4 日。万维网联盟。 http://www.w3.org/TR/2004/REC-xml-infoset-20040204/
    
    XML Namespaces, Tim Bray, Dave Hollander, Andrew Layman, and Richard Tobin (editors). Namespaces in XML 1.0 (Third Edition), 8 December 2009. World Wide Web Consortium. http://www.w3.org/TR/2009/REC-xmlnames-20091208/

=== "英文"

    Normative References  

    The following referenced standards are indispensable for the application of this standard. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced standard (including any amendments) applies.
    
    XML, Tim Bray, Jean Paoli, Eve Maler, C. M. Sperberg-McQueen, and François Yergeau (editors). Extensible Markup Language (XML) 1.0, Fifth Edition. World Wide Web Consortium. 2008.
    
    http://www.w3.org/TR/2008/PER-xml-20080205/. [Note: Implementations of this Part of ECMA-376 are not required to support features of XML introduced by the Fifth Edition. end note]
    
    XML Base, Marsh, Jonathan. XML Base. World Wide Web Consortium. 2009. http://www.w3.org/TR/2009/RECxmlbase-20090128/
    
    XML Information Set, John Cowan and Richard Tobin (editors). XML Information Set (Second Edition), 4 February 2004. World Wide Web Consortium. http://www.w3.org/TR/2004/REC-xml-infoset-20040204/
    
    XML Namespaces, Tim Bray, Dave Hollander, Andrew Layman, and Richard Tobin (editors). Namespaces in XML 1.0 (Third Edition), 8 December 2009. World Wide Web Consortium. http://www.w3.org/TR/2009/REC-xmlnames-20091208/

## 3 术语和定义 

=== "中文"

    For the purposes of this standard, the following terms and definitions apply:

    **3.1**

    **application configuration**

    可理解的命名空间的名称集

    **3.2**

    **application-defined extension element**
    
    由标记规范定义的元素，其属性和内容不得由 MCE 处理器处理

    **3.3**
    
    **markup configuration**
    
    应用程序定义的扩展元素的扩展名称集
    
    **3.4**
    
    **markup specification**
    
    基于 XML 的格式规范，允许使用 MCE 名称空间中的元素和属性
    
    **3.5**
    
    **MCE processor**
    
    用于处理包含 MCE 元素和属性的 XML 文档的软件
    
    **3.6**
    
    **mismatch**
    
    MCE 元素和属性指定的约束与应用程序配置指定的命名空间不兼容

    **3.7**
    
    **understood namespace**
    
    命名空间，消费应用程序能够处理其中的元素和属性

=== "英文"

    Terms and Definitions 

    For the purposes of this standard, the following terms and definitions apply:

    **3.1**

    **application configuration**

    set of names of understood namespaces

    **3.2**

    **application-defined extension element**
    
    element defined by a markup specification, the attributes and content of which are not to be processed by an MCE processor

    **3.3**
    
    **markup configuration**
    
    set of expanded names of application-defined extension elements
    
    **3.4**
    
    **markup specification**
    
    XML-based format specification that allows the use of elements and attributes in the MCE namespace
    
    **3.5**
    
    **MCE processor**
    
    software used to process XML documents containing MCE elements and attributes
    
    **3.6**
    
    **mismatch**
    
    incompatibility between the constraints specified by MCE elements and attributes, and the namespaces specified by an application configuration

    **3.7**
    
    **understood namespace**
    
    namespace, the elements and attributes of which a consuming application is able to process

## 4 符号定义

=== "中文"

    ECMA-376 中使用了以下排版约定：
    
    1) 首次出现的新术语用斜体书写。例如 ECMA-376 中的文本分为规范类和信息类。 示例结束] 2) XML 元素的标记名使用不同的样式和字体。
    2) XML 元素的标记名使用不同的样式和字体书写。[示例：bookmarkStart 和 bookmarkEnd 元素指定...... 示例结束］
    3) XML 属性的名称使用不同的样式和字体书写。[示例：dropCap 属性指定...... 示例结束］
    4) XML 属性的值使用恒定宽度样式书写。[示例：auto 属性值指定...... 示例结束］
    
    除了被确定为信息性的整个条款或附件外，包含在规范性文本中的信息性文本以下列方式表示：
    
    1) [示例：代码片段，可能有一些叙述......示例结束］
    2) [说明：叙述......结束说明］
    3) [理由：叙述......理由结束］
    4) [指导：叙述......结束指导］

=== "英文"

    Notational Conventions

    The following typographical conventions are used in ECMA-376:
    
    1) The first occurrence of a new term is written in italics. [Example: The text in ECMA-376 is divided into normative and informative categories. end example]
    2) The tag name of an XML element is written using a distinct style and typeface. [Example: The bookmarkStart and bookmarkEnd elements specify … end example]
    3) The name of an XML attribute is written using a distinct style and typeface. [Example: The dropCap attribute specifies … end example]
    4) The value of an XML attribute is written using a constant-width style. [Example: The attribute value of auto specifies … end example]
    
    Except for whole clauses or annexes that are identified as being informative, informative text that is contained within normative text is indicated in the following ways:
    
    1) [Example: code fragment, possibly with some narrative … end example]
    2) [Note: narrative … end note]
    3) [Rationale: narrative … end rationale]
    4) [Guidance: narrative … end guidance]

## 5 概述 

=== "中文"

    ECMA-376 的本部分分为以下子部分：

    - Front matter (Clauses 1–5);
    - Overview (Clause 6);
    - Main body (Clauses 7–9);
    - Annexes

    举例说明了所述结构的可能形式。参考文献用于引用相关条款。注释用于向实施者或程序员提供建议或指导。

    以下内容构成 ECMA-376 本部分的规范部分：
    
    - Clauses 1–4, and 7–9
    
    以下内容构成了 ECMA-376 本部分的信息内容：
    
    - Foreword
    - Introduction
    - Clauses 5 and 6
    - All annexes
    - All notes and examples

=== "英文"

    General Description 

    **This clause is informative**

    This Part of ECMA-376 is divided into the following subdivisions:

    - Front matter (Clauses 1–5);
    - Overview (Clause 6);
    - Main body (Clauses 7–9);
    - Annexes

    Examples are provided to illustrate possible forms of the constructions described. References are used to refer     to related clauses. Notes are provided to give advice or guidance to implementers or programmers.

    The following form the normative pieces of this Part of ECMA-376:
    
    - Clauses 1–4, and 7–9
    
    The following make up the informative pieces of this Part of ECMA-376:
    
    - Foreword
    - Introduction
    - Clauses 5 and 6
    - All annexes
    - All notes and examples
    
    **End of informative text**

## 6 概览

=== "中文"
    
    ECMA-376 的这一部分描述了一组 XML 元素和属性，称为 MCE 元素和属性，其目的是使生产应用程序能够指导消费应用程序处理消费应用程序不理解的命名空间中的任何 XML 元素和属性。
    
    MCE 元素和属性的目的是使制作应用程序能够在制作新文档时使用新版本或扩展标记规范中添加的功能，但这些功能仍可与不理解这些功能的消费应用程序互操作。制作应用软件在文档中包含 MCE 元素和属性，是为了向消费应用软件说明如何调整文档内容，以排除那些与其所理解的标记规范版本不兼容的功能，同时允许理解这些功能的消费应用软件充分利用这些功能。
    
    MCE 元素和属性定义了特定类型的兼容性和扩展结构，概述如下:
    
    - 命名空间可以被声明为可忽略的，这表明这些命名空间中的所有元素和属性都可以被消费应用程序忽略，就好像它们不存在于输入文档中一样，从而实现文档功能的优雅降级。这样，实现者就可以将某些标记识别为不是文档内容的核心。
    - 可对不可忽略命名空间中的元素进行标记，以便对其内容进行处理，否则这些内容将被忽略。这样，当消费应用程序不理解可忽略命名空间中的元素，但理解嵌套内容的命名空间时，生产应用程序就可以防止嵌套在可忽略命名空间中元素的内容丢失。
    - 可以声明消费应用程序必须理解的命名空间，以便处理文档。这样，生产应用程序就可以为消费应用程序设定最低兼容性要求。
    - 可指定文档内容的替代表示法。这样，生产应用软件就可以为消费应用软件提供内容替代方案，这些应用软件具有不同的命名空间和相应的功能。
    - 应用程序定义的扩展元素使生产应用程序能够为标记规范定义的特定元素引入附加功能。消费应用程序可以保留应用程序定义的扩展元素，即使它们不以任何其他方式处理这些元素。
    
    从概念上讲，消费应用程序并不直接处理包含 MCE 元素和属性的输入文档，而是使用 MCE 处理器生成消费应用程序能够理解的输出文档。
    
    有关使用 MCE 元素和属性的输入文档示例，以及 MCE 处理器将生成的输出文档，请参见附录 A。

=== "英文"

    Overview

    This clause is informative
    
    This Part of ECMA-376 describes a set of XML elements and attributes, called MCE elements and attributes, the purpose of which is to enable producing applications to guide consuming applications in their handling of any XML elements and attributes in namespaces not understood by the consuming applications.
    
    MCE elements and attributes are intended to enable producing applications to use features added in new versions or extensions of a markup specification in the production of new documents, which nevertheless remain interoperable with consuming applications that do not understand these features. A producing application includes MCE elements and attributes in documents to indicate to a consuming application how it can adjust the content of the document to exclude those features that are not compatible with the version of the markup specification that it understands, while at the same time allowing consuming applications that do understand these features to make full use of them.
    
    MCE elements and attributes define particular types of compatibility and extension constructs, as summarized
    below:
    
    - Namespaces can be declared to be ignorable, indicating that all elements and attributes in those namespaces can be disregarded by consuming applications as if they were not present in the input document, enabling graceful degradation of the document functionality. This allows implementations to identify some markup as not core to the document content.
    - Elements in ignorable namespaces can be marked for their content to be processed that would otherwise be ignored. This allows producing applications to prevent loss of content nested within an element in an ignorable namespace when processed by consuming applications that do not understand that namespace but do understand the namespace(s) of the nested content.
    - Namespaces can be declared that must be understood by consuming applications in order to process the document. This allows producing applications to set minimum compatibility requirements for consuming applications.
    - Alternative representations of document content can be specified. This allows producing applications to include content alternatives for consuming applications with differing sets of understood namespaces and corresponding capabilities.
    - Application-defined extension elements enable producing applications to introduce additional features scoped to particular elements defined by a markup specification. Consuming applications might preserve application-defined extension elements even if they do not process them in any other way.
    
    Conceptually, a consuming application does not directly process input documents containing MCE elements and attributes but rather uses an MCE processor to produce an output document understood by the consuming application.
    
    See Annex A for examples of input documents using MCE elements and attributes, and output documents that would be produced by an MCE processor.
    
    End of informative text

## 7 MCE 元素和属性

    MCE Elements and Attributes

### 7.1 简介 

=== "中文"

    本子条款规定了所有 MCE 元素和属性的语法定义，这些元素和属性应属于标记兼容性命名空间：

        <http://schemas.openxmlformats.org/markup-compatibility/2006>

    [Guidance: 外部 DTD 子集不应指定 Markup Compatibilitynamespace 中属性的默认值，因为某些非验证 XML 处理器不使用此类默认值。 end guidance]

    Markup Compatibility 命名空间内的属性可出现在任何 XML 元素上，包括 Markup Compatibility 元素。
    
    标记兼容命名空间内的元素不得包含 XML 命名空间内的属性 http://www.w3.org/XML/1998/namespace.

=== "英文"

    Introduction

    This subclause specifies the syntactic definitions of all MCE elements and attributes, which shall be in the Markup Compatibility namespace:

        <http://schemas.openxmlformats.org/markup-compatibility/2006>

    [Guidance: External DTD subsets should not specify default values for attributes in the Markup Compatibilitynamespace, as some non-validating XML processors do not use such default values. end guidance]

    Attributes within the Markup Compatibility namespace may occur on any XML element, including Markup Compatibility elements.
    
    Elements within the Markup Compatibility namespace shall not contain attributes within the XML namespace http://www.w3.org/XML/1998/namespace.

### 7.2 可忽略的属性 

=== "中文"

    Ignorable 属性是标记兼容命名空间中的一个属性，本地名称为 "Ignorable"。其值应是一个以空白为分隔符的列表，其中包含零个或多个命名空间前缀，可选择带前缀和/或尾缀空白。对于列表中的每个命名空间前缀，都必须有一个范围内命名空间与之绑定，且该前缀不得是标记兼容命名空间。该范围内命名空间可通过 Ignorable 属性声明为可忽略。

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
         <foo mce:Ignorable="i1"
             xmlns:i1="http://www.example.com/i1"
             xmlns:i2="http://www.example.com/i2">
         <bar mce:Ignorable="i2">…</bar>
         </foo>
    </example>
    ```
    
    foo 元素和 bar 元素各有一个 Ignorable 属性。foo 的 Ignorable 属性指定了前缀 "i1"，该前缀绑定到范围内命名空间 "http://www.example.com/i1"。bar 的 Ignorable 属性指定了前缀 "i2"，它与范围内命名空间 "http://www.example.com/i2 "绑定。因此，这些命名空间被声明为可忽略。 end example]

=== "英文"

    Ignorable Attribute 

    An Ignorable attribute shall be an attribute in the Markup Compatibility namespace with local name “Ignorable”. Its value shall be a whitespace-delimited list of zero or more namespace prefixes, optionally having leading and/or trailing whitespace. For each namespace prefix in the list, there shall be an in-scope namespace to which that prefix is bound, and it shall not be the Markup Compatibility namespace. This inscope namespace is said to be declared as ignorable by this Ignorable attribute.

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
         <foo mce:Ignorable="i1"
             xmlns:i1="http://www.example.com/i1"
             xmlns:i2="http://www.example.com/i2">
         <bar mce:Ignorable="i2">…</bar>
         </foo>
    </example>
    ```
    
    The foo element and the bar element each have an Ignorable attribute. The Ignorable attribute of foo specifies the prefix “i1”, which is bound to the in-scope namespace “http://www.example.com/i1”. The Ignorable attribute of bar specifies the prefix “i2”, which is bound to the in-scope namespace “http://www.example.com/i2”. Thus, these namespaces are declared as ignorable. end example]

### 7.3 ProcessContent 属性 

=== "中文"

    ProcessContent 属性应是标记兼容命名空间中的一个属性，本地名称为 "ProcessContent"。其值应是一个以空白为分隔符的列表，包含零个或多个标记，可选择带前空白和/或尾部空白。每个标记都是命名空间前缀，后跟": "或本地名称或 "*"。对于列表中的每个标记，都应有一个范围内命名空间，标记的命名空间前缀部分与之绑定。该范围内命名空间不应是标记兼容性命名空间，并应通过同一元素或祖先元素上的 Ignorable 属性声明为可忽略。该标记中的该范围内命名空间与本地部分或 "*"的对称谓由该 ProcessContent 属性声明为 processcontent 名称对。
    
    如果 (n1，l1) 是元素的命名空间名和本地名对，则该元素在下列情况下匹配进程-内容名对 (n2，l2) 
    
    1) n1 和 n2 是相同的字符序列，并且
    2) Either
        
        a) l1 和 l2 是相同的字符序列，或
        b) l2 is “*”
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
         <foo1 mce:Ignorable="i1"
             mce:ProcessContent="i1:bar1"
             xmlns:i1="http://www.example.com/i1"
             xmlns:i2="http://www.example.com/i2">
             <foo2 mce:Ignorable="i2"
             mce:ProcessContent="i2:*">…</foo2>
             <foo3 mce:ProcessContent="i1:bar2">…</foo3>
         </foo1>
    </example>
    ```
    
    foo1、foo2 和 foo3 元素都有 ProcessContent 属性。foo1 元素的 ProcessContent 属性有一个标记 "i1:bar1"，其中 "i1 "是与范围内命名空间 "http://www.example.com/i1 "绑定的命名空间前缀，该命名空间在该元素中被声明为不可忽略。foo2 元素的前缀是 "i2:*"，其中 "i2 "是与范围内命名空间 "http://www.example.com/i2 "绑定的命名空间前缀，该命名空间在该元素中被声明为不可忽略。foo3 元素有一个标记 "i1:bar2"，其中 i1 是一个与范围内命名空间 "http://www.example.com/i1 "绑定的命名空间前缀，在父元素 foo1 中被声明为可忽略。 end example]

=== "英文"

    ProcessContent Attribute 

    A ProcessContent attribute shall be an attribute in the Markup Compatibility namespace with local name “ProcessContent”. Its value shall be a whitespace-delimited list of zero or more tokens, optionally having leading and/or trailing whitespace. Each token shall be a namespace prefix followed by “:” followed either by a local name or by “*”. For each token in the list, there shall be an in-scope namespace to which the namespace prefix part of the token is bound. This in-scope namespace shall not be the Markup Compatibility namespace and shall be declared as ignorable by an Ignorable attribute at the same element or an ancestor element. The pair of this in-scope namespace and the local part or “*” in this token is said to be declared as a processcontent name pair by this ProcessContent attribute.
    
    If (n1, l1) is the namespace-name and local-name pair of an element, that element matches a process-content name pair (n2, l2) if 
    
    1) n1 and n2 are the same sequence of characters, and
    2) Either
        
        a) l1 and l2 are the same sequence of characters, or
        b) l2 is “*”
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
         <foo1 mce:Ignorable="i1"
             mce:ProcessContent="i1:bar1"
             xmlns:i1="http://www.example.com/i1"
             xmlns:i2="http://www.example.com/i2">
             <foo2 mce:Ignorable="i2"
             mce:ProcessContent="i2:*">…</foo2>
             <foo3 mce:ProcessContent="i1:bar2">…</foo3>
         </foo1>
    </example>
    ```
    
    The foo1, foo2, and foo3 elements have ProcessContent attributes. That of the foo1 element has a token "i1:bar1", where "i1" is a namespace prefix bound to an in-scope namespace "http://www.example.com/i1", which is declared as ignorable at this element. That of the foo2 element has a token "i2:*", where i2 is a namespace prefix bound to an in-scope namespace "http://www.example.com/i2", which is declared as ignorable at this element. That of the foo3 element has a token "i1:bar2", where i1 is a namespace prefix bound to an in-scope namespace "http://www.example.com/i1", which is declared as ignorable at the parent foo1 element. end example]

### 7.4 MustUnderstand 属性  

=== "中文"

    MustUnderstand 属性是标记兼容命名空间中的一个属性，本地名称为 "MustUnderstand"。其值应是一个以空白为分隔符的列表，其中包含零个或多个命名空间前缀，可选择带前缀和/或尾缀空白。对于列表中的每个命名空间前缀，都必须有一个范围内命名空间名称与之绑定，且该命名空间不得是标记兼容命名空间。该范围内命名空间可通过此 MustUnderstand 属性声明为必须理解的命名空间。
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com/"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:n1="http://www.example.com/n1"
         mce:MustUnderstand="n1">
    </example>
    ```
    
    在本例中，根元素有一个 MustUnderstand 属性。其值包含 n1，与范围内命名空间名称 "http://www.example.com/n1 "绑定。 end example]

=== "英文"

    MustUnderstand Attribute  

    A MustUnderstand attribute shall be an attribute in the Markup Compatibility namespace with local name “MustUnderstand”. Its value shall be a whitespace-delimited list of zero or more namespace prefixes optionally having leading and/or trailing whitespace. For each namespace prefix in the list, there shall be an inscope namespace name to which that prefix is bound, and this namespace shall not be the Markup Compatibility namespace. This in-scope namespace is said to be declared as a must-understand namespace by this MustUnderstand attribute.
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com/"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:n1="http://www.example.com/n1"
         mce:MustUnderstand="n1">
    </example>
    ```
    
    In this example, the root element has a MustUnderstand attribute. The value contains n1, which is bound to an in-scope namespace name "http://www.example.com/n1". end example]

### 7.5 AlternateContent 元素 

=== "中文"

    AlternateContent 元素应是本地名称为 "AlternateContent "的 "标记兼容 "命名空间中的一个元素。AlternateContent 元素不得有非限定属性，但可以有限定属性。每个限定属性的命名空间要么是标记兼容命名空间，要么是该 AlternateContent 元素或其某个祖先的 Ignorable 属性声明为可忽略的命名空间。
    
    替代内容（AlternateContent）元素应包含一个或多个 "选择"（Choice）子元素，可选择在其后添加一个 "回退"（Fallback）子元素。标记兼容命名空间中的其他元素不得作为子元素出现。其他命名空间中的元素可以作为前面、中间或后面的子元素出现，但这种子元素的命名空间应声明为不可忽略。

    [Note: 允许将不可忽略元素作为 AlternateContent 的子元素，以便将来对该构造进行扩展。如果指定 AlternateContent 只包含来自标记兼容命名空间（§7.5）的选择和回退元素，这将会阻止使用其他标记兼容元素，而这些元素将允许在未来版本的 MCE 中扩展 AlternateContent。任何 MCE 处理器在遇到 AlternateContent 的子元素属于 MCE 未来预期扩展的命名空间时，只要该子元素的命名空间是可忽略的，就不会无法处理该文档，因为它将丢弃可忽略命名空间中所有无法理解的元素，然后再在剩余的 Choice 和 Fallback 元素中做出选择。 end note]
    
    [Note: AlternateContent 元素可以作为标记文档的根元素出现。 end note]
    
    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:n1="http://www.example.com/n1"
     xmlns:n2="http://www.example.com/n2">
     <mce:AlternateContent mce:MustUnderstand="n1">
     <mce:Choice Requires="n2">…</mce:Choice>
     <mce:Fallback>…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```
    
    在这个例子中，AlternateContent 元素有一个 MustUnderstand 属性，没有其他属性。AlternateContent 元素有一个 Choice 元素，后面跟着一个 Fallback 元素。 end example]

=== "英文"

    AlternateContent Element 

    An AlternateContent element shall be an element in the Markup Compatibility namespace with local name “AlternateContent”. An AlternateContent element shall not have unqualified attributes, but may have qualified attributes. The namespace of each qualified attribute shall be either the Markup Compatibility namespace or a namespace declared as ignorable by the Ignorable attribute of this AlternateContent element or one of its ancestors.
    
    An AlternateContent element shall contain one or more Choice child elements, optionally followed by a single Fallback child element. No other elements in the Markup Compatibility namespace shall appear as child elements. Elements in other namespaces may appear as preceding, intervening, or trailing child elements, but the namespace of such a child element shall be declared as ignorable.

    [Note: Ignorable elements are allowed as child elements of AlternateContent to allow for future extensions to this construct. If AlternateContent were specified to contain only Choice and Fallback elements from the Markup Compatibility namespace (§7.5), this would prevent the use of other Markup Compatibility elements that would allow extension of AlternateContent in future versions of MCE. Any MCE processor that encounters a child element of AlternateContent that is in the namespace of an intended future extension of MCE will not fail to process the document, provided the namespace of this child element is ignorable, because it will discard all elements in ignorable namespaces that are not understood before making a selection between the remaining Choice and Fallback elements. end note]
    
    [Note: The AlternateContent element can appear as the root element of a markup document. end note]
    
    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:n1="http://www.example.com/n1"
     xmlns:n2="http://www.example.com/n2">
     <mce:AlternateContent mce:MustUnderstand="n1">
     <mce:Choice Requires="n2">…</mce:Choice>
     <mce:Fallback>…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```
    
    In this example, the AlternateContent element has a MustUnderstand attribute and no other attributes. The AlternateContent element has a Choice element followed by a Fallback element. end example]

### 7.6 Choice 元素 

=== "中文"

    选择 "元素应是本地名称为 "选择 "的 "标记兼容 "命名空间中的一个元素。选择 "元素的父元素应是 "替代内容"（AlternateContent）元素。选择 "元素必须有一个本地名称为 "Requires "的非限定属性，且不得有其他非限定属性。Requires 属性的值应是一个或多个命名空间前缀的以空白为分隔符的列表，可选择带前导和/或尾部空白。
    
    [Note: 除了空列表外，与 Requires 属性相关的语法限制与与 MustUnderstand 属性相关的语法限制相同。 end note]
    
    选择元素可以有限定属性。每个限定属性的命名空间必须是标记兼容命名空间或已声明为可忽略的命名空间。

    [Example:
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:i1="http://www.example.com/i1"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="i1" >
     <mce:Choice Requires="n1" i1:foo="">…</mce:Choice>
     </mce:AlternateContent>
    </example>
    ```

    在本例中，Choice 元素指定了 i1:foo 属性。该属性的命名空间在父级 AlternateContent 元素中被声明为可忽略。该文档符合要求，但如果 i1 命名空间不是可忽略的，则不符合要求。 end example]

=== "英文"

    Choice Element 

    A Choice element shall be an element in the Markup Compatibility namespace with local name “Choice”. Parent elements of Choice elements shall be AlternateContent elements. A Choice element shall have an unqualified attribute with local name “Requires” and shall have no other unqualified attributes. The value of the Requires attribute shall be a whitespace-delimited list of one or more namespace prefixes, optionally having leading and/or trailing whitespace.
    
    [Note: With the exception of empty lists, the syntactical constraints associated with the Requires attribute are the same as those associated with the MustUnderstand attribute. end note]
    
    A Choice element may have qualified attributes. The namespace of each qualified attribute shall be either the Markup Compatibility namespace or a namespace declared as ignorable.
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:i1="http://www.example.com/i1"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="i1" >
     <mce:Choice Requires="n1" i1:foo="">…</mce:Choice>
     </mce:AlternateContent>
    </example>
    ```
    
    In this example, the Choice element specifies the i1:foo attribute. The namespace of this attribute is declared as ignorable at the parent AlternateContent element. This document is conformant, but would be nonconformant if the i1 namespace was not ignorable. end example]

### 7.7 Fallback 元素

=== "中文"

    回退元素应是本地名称为 "回退 "的 "标记兼容 "命名空间中的一个元素。回退元素的父元素应为 AlternateContent 元素。
    
    回退元素不得有非限定属性。回退元素可以有限定属性。每个限定属性的命名空间必须是 "标记兼容 "命名空间或已声明为可忽略的命名空间。
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:i1="http://www.example.com/i1"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="i1" >
     <mce:Choice Requires="n1" >…</mce:Choice>
     <mce:Fallback i1:foo="">…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```
    
    在本例中，Fallback 元素指定了 i1:foo 属性。在父 AlternateContent 元素中，该属性的命名空间被声明为可忽略。该文档符合规范，但如果 i1 命名空间不是可忽略的，则不符合规范。 end example]

=== "英文"

    Fallback Element

    A Fallback element shall be an element in the Markup Compatibility namespace with local name “Fallback”. Parent elements of Fallback elements shall be AlternateContent elements.
    
    A Fallback element shall not have unqualified attributes. A Fallback element may have qualified attributes. The namespace of each qualified attribute shall be either the Markup Compatibility namespace or a namespace declared as ignorable.
    
    [Example:
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:i1="http://www.example.com/i1"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="i1" >
     <mce:Choice Requires="n1" >…</mce:Choice>
     <mce:Fallback i1:foo="">…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```
    
    In this example, the Fallback element specifies the i1:foo attribute. The namespace of this attribute is declared as ignorable at the parent AlternateContent element. This document is conformant but would be non-conformant if the i1 namespace were not ignorable. end example]

## 8 应用程序定义的扩展元素

=== "中文"

    使用 MCE 元素和属性的标记规范可能会将其定义的命名空间中的一个或多个元素指定为应用程序定义的扩展元素。如第 9 节所述，在这些元素的内容中，MCE 处理实际上是暂停的，它们被传递到 MCE 处理器生成的输出文档中。标记兼容命名空间中的任何元素都不得被指定为应用程序定义的扩展元素。

    [Rationale: 该机制旨在（但不限于）被标记规范用于在标记规范中创建可扩展点。 end rationale]
    
    [Note: 如果标记规范包含模式，扩展元素可能会受到模式的限制，只能出现在特定的标记上下文中。 end note]
    
    [Note: 应用程序定义的扩展元素的内容可能包含使用 MCE 元素和属性的标记。消费应用程序可能会调用 MCE 处理器来处理由 MCE 处理器构建的输出文档中包含的应用程序定义的扩展元素的内容。 end note]
    
    [Example:
   
    ```xml
    <example xmlns="http://www.example.com"
         xmlns:n1="http://www.example.com/n1"
         xmlns:unknown="http://www.example.com/unknown">
         <n1:extensionElement>
             <unknown:foo/>
         </n1:extensionElement>
    </example>
    ```
    
    在本例中，extensionElement 元素包含 unknown:foo 元素。假设 MCE 处理器的标记配置包含扩展名称（"http://www.example.com/n1", "extensionElement"），而其应用程序配置不包含 "http://www.example.com/unknown"。那么，n1:extensionElement 元素就是应用程序定义的扩展元素。虽然 unknown:foo 元素不属于可理解或可忽略的命名空间，但根据第 9 节中的语义定义，MCE 处理器不会将该元素的存在作为错误报告。 end example]
    
    [Example:

    ```xml
    <example xmlns="http://www.example.com"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:i1="http://www.example.com/i1"
         xmlns:n1="http://www.example.com/n1">
         <extensionElement>
             <foo1 mce:Ignorable="i1"
                 mce:ProcessContent="i1:bar1"
                 mce:MustUnderstand="n1">
             </foo1>
             <mce:AlternateContent mce:Ignorable="i1" >
             <mce:Choice Requires="n1" >…</mce:Choice>
             <mce:Fallback i1:foo="">…</mce:Fallback>
             </mce:AlternateContent>
         </extensionElement>
    </example>
    ```
    
    在本例中，MCE 元素和属性出现在 extensionElement 元素中，它是根元素示例的唯一子元素。假设 MCE 处理器被配置为保留扩展名称的扩展元素（"http://www.example.com/n1", "extensionElement"）。那么，MCE 处理器就会保留 extensionElement 元素。因此，输出文档中会出现 MCE 元素及其属性 mce:Ignorable="i1"、mce:ProcessContent="i1:bar1"、mce:MustUnderstand="n1"、mce:AlternateContent、mce:Choice 和 mce:Fallback。 end example]

=== "英文"

    Application-Defined Extension Elements

    A markup specification using MCE elements and attributes might designate one or more elements in the namespaces it defines as application-defined extension elements. As described in §9, MCE processing is effectively suspended within the content of these elements and they are passed through to the output document generated by the MCE processor. No elements within the Markup Compatibility namespace shall be designated as application-defined extension elements.

    [Rationale: This mechanism is intended to, but not limited to, be used by markup specifications to create extensibility points within the markup specification. end rationale]
    
    [Note: If the markup specification includes a schema, an extension element might be constrained by the schema to occur only in specific markup contexts. end note]
    
    [Note: The content of an application-defined extension element might contain markup that uses MCE elements and attributes. A consuming application might invoke an MCE processor to process the content of applicationdefined extension elements contained in an output document constructed by an MCE processor. end note]
    
    [Example:
   
    ```xml
    <example xmlns="http://www.example.com"
         xmlns:n1="http://www.example.com/n1"
         xmlns:unknown="http://www.example.com/unknown">
         <n1:extensionElement>
             <unknown:foo/>
         </n1:extensionElement>
    </example>
    ```
    
    In this example, the extensionElement element contains the unknown:foo element. Suppose that an MCE processor’s markup configuration contains the expanded name ("http://www.example.com/n1", "extensionElement") and its application configuration does not contain "http://www.example.com/unknown". Then, the element n1:extensionElement is an application-defined extension element. Although the unknown:foo element does not belong to an understood or ignorable namespace, according to the semantic definitions in §9, the MCE processor does not report the existence of that element as an error. end example]
    
    [Example:

    ```xml
    <example xmlns="http://www.example.com"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:i1="http://www.example.com/i1"
         xmlns:n1="http://www.example.com/n1">
         <extensionElement>
             <foo1 mce:Ignorable="i1"
                 mce:ProcessContent="i1:bar1"
                 mce:MustUnderstand="n1">
             </foo1>
             <mce:AlternateContent mce:Ignorable="i1" >
             <mce:Choice Requires="n1" >…</mce:Choice>
             <mce:Fallback i1:foo="">…</mce:Fallback>
             </mce:AlternateContent>
         </extensionElement>
    </example>
    ```
    
    In this example, MCE elements and attributes occur within the extensionElement element, which is the only child of the root element example. Suppose that an MCE processor is configured to preserve extension elements of an expanded name ("http://www.example.com/n1", "extensionElement"). Then, the MCE processor preserves the extensionElement element. Therefore, MCE elements and attributes within it, mce:Ignorable="i1", mce:ProcessContent="i1:bar1", mce:MustUnderstand="n1", mce:AlternateContent, mce:Choice, and mce:Fallback, appear in the output document. end example]

## 9 语义定义和参考处理模型 

Semantic Definitions and Reference Processing Model 

### 9.1 概述 

=== "中文"

    本条款定义了 MCE 处理器在输入文档、标记配置和应用配置的情况下创建的输出文档。MCE 处理器使用标记配置和应用程序配置进行初始化。标记配置表示一组扩展名称，这些名称将被视为应用程序定义的扩展元素的名称。应用程序配置代表一组命名空间，这些命名空间将被视为可理解的命名空间。

    本条款进一步规定了 MCE 处理器应发出信号的给定输入文档、标记配置和应用程序配置之间的不匹配条件；但并未明确规定何时或如何发出此类不匹配信号。如果 MCE 处理器检测到不匹配，它应向消费应用发出信号，然后继续正常的 MCE 处理。[注：如果消费应用能够处理不在命名空间中的元素和属性，则必须由应用配置指定。请实施者注意，不在命名空间中的元素和属性没有命名空间名称，建议实施者在设计 MCE 处理器时应考虑到这一点。 end note]
    
    本条款通过描述抽象处理模型来定义语义，包括以下三个步骤：
    
    1) 步骤 1 定义了哪些元素和属性被标记为忽略或未封装。该定义考虑了 Ignorable 和 ProcessContent 属性，但没有考虑 MustUnderstand 属性或 AlternateContent、Choice 或 Fallback 元素。应用程序定义的扩展元素内的元素或属性不会被标记为忽略或未封装。
    2) 步骤 2 定义了 AlternateContent 元素的语义。它规定了每个 AlternateContent 元素的选择或回退元素。该定义考虑了 AlternateContent、Choice 和 Fallback 元素，但没有考虑 Ignorable、ProcessContent 或 MustUnderstand 属性。应用程序定义的扩展元素内的选择或回退元素不会被标记为选中。
    3) 步骤 3 应用步骤 1 和 2 的结果来构建输出文档，同时检查 MustUnderstand 属性，除非它们位于应用程序定义的扩展元素内。
    
    不过，MCE 处理器并不需要执行这些步骤。只要根据给定的输入文档、标记配置和应用配置创建的输出文档和发出的不匹配信号与这些步骤创建和发出的信号一致，MCE 处理器就符合标准。
    
    [Note: 由于 Markup Compatibility 处理不在应用程序定义的扩展元素内执行，因此在应用 Markup Compatibility 处理后，输出文档可能仍包含 Markup Compatibility 命名空间中的元素和属性。 end note]
    
    如果 MCE 处理器检测到文档不符合要求，MCE 处理器应将不符合要求的情况告知消费应用程序。

=== "英文"

    Overview

    This clause defines the output document that shall be created by the MCE processor given an input document, markup configuration, and application configuration. The MCE processor is initialized with the markup and application configurations. The markup configuration represents the set of expanded names that are to be treated as those of application-defined extension elements. The application configuration represents the set of namespaces that are to be treated as understood.

    This clause further specifies the mismatch conditions among a given input document, markup configuration, and application configuration that shall be signaled by the MCE processor; however, it does not specify exactly when or how such mismatches are to be signaled. If an MCE processor detects a mismatch, it shall signal this mismatch to the consuming application and it may continue normal MCE processing. [Note: If a consuming application is able to process elements and attributes that are in no namespace, this must be specified by the application configuration. Implementers are reminded that there is no namespace name for elements and attributes that are in no namespace, and are advised that they should take this into account when designing MCE processors. end note]
    
    This clause defines the semantics through the description of an abstract processing model, which has the following three steps:
    
    1) Step 1 defines which elements and attributes are marked as ignored or unwrapped. This definition takes into consideration Ignorable and ProcessContent attributes, but does not take into consideration MustUnderstand attributes or AlternateContent, Choice, or Fallback elements. Elements or attributes inside application-defined extension elements are not marked as ignored or unwrapped.
    2) Step 2 defines the semantics of AlternateContent elements. It specifies which Choice or Fallback element of each AlternateContent element is selected. This definition takes into consideration AlternateContent, Choice, and Fallback elements, but does not take into consideration Ignorable, ProcessContent, or MustUnderstand attributes. Choice or Fallback elements inside applicationdefined extension elements are not marked as selected.
    3) Step 3 applies the results from Steps 1 and 2 to construct the output document and also examines MustUnderstand attributes unless they are inside application-defined extension elements.
    
    However, MCE processors are not required to carry out these steps. MCE processors are conformant as long as output documents created and mismatches signaled from given input documents, markup configurations, and application configurations are consistent with those created and signaled by these steps.
    
    [Note: Because Markup Compatibility processing is not performed inside application-defined extension elements, an output document might still contain elements and attributes in the Markup Compatibility namespace after Markup Compatibility processing has been applied. end note]
    
    If an MCE processor detects that a document is non-conformant, the MCE processor should indicate this nonconformance to the consuming application.

### 9.2 Step 1: 处理 Ignorable 和 ProcessContent 属性 

=== "中文"

    如果满足以下所有条件，一个元素将被标记为忽略：

    1) 该元素的命名空间被该元素或其祖先元素的 Ignorable 属性声明为可忽略；
    2) 该元素的命名空间未包含在给定的应用程序配置中；
    3) 该元素不匹配由该元素或某个祖先声明的任何流程-内容名称对；以及
    4) 该元素既不是应用程序定义的扩展元素，也不是应用程序定义的扩展元素的后代。

    如果满足以下所有条件，属性将被标记为忽略：

    5) 该属性的命名空间由具有该属性的元素或其祖先元素的 Ignorable 属性声明为可忽略；
    6) 该属性的命名空间未包含在给定的应用程序配置中；以及
    7) 该属性不属于应用程序定义的扩展元素或应用程序定义的扩展元素的子元素

    如果满足以下所有条件，一个元素将被标记为非包裹元素：

    8) 此元素的命名空间被此元素或其祖先元素的 Ignorable 属性声明为可忽略；
    9) 该元素的命名空间未包含在给定的应用程序配置中；
    10) 该元素匹配由该元素或某个祖先声明的流程-内容名称对；以及
    11) 该元素既不是应用程序定义的扩展元素，也不是应用程序定义的扩展元素的后代。

    标记为未封装的元素不得具有 xml:base、xml:lang 或 xml:space 属性。

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
        xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:i1="http://www.example.com/i1"
        mce:Ignorable="i1"
        mce:ProcessContent="i1:bar"
        i1:foo="">
        <i1:foo><fooChild/></i1:foo>
        <i1:bar><barChild/></i1:bar>
        <i1:baz i1:baz=""><i1:bazChild/></i1:baz>
    </example>
    ```

    命名空间 "http://www.example.com/i1 "被声明为可忽略。一对（"http://www.example.com/i1", bar）被声明为进程-内容名称对。假设给定的标记配置是一个包含（"http://www.example.com/i1", baz）的单例，而给定的应用程序配置不包含 "http://www.example.com/i1"。那么，i1:foo 属性和 i1:foo 元素被标记为忽略，i1:bar 元素被标记为未封装。但是，i1:baz 元素既没有被标记为忽略，也没有被标记为解包，因为它是应用程序定义的扩展元素。同样，i1:baz 属性和 i1:bazChild 元素都没有被标记。虽然 fooChild 和 barChild 的父元素被标记为忽略或未包裹，但它们都没有被标记为忽略或未包裹。 end example]

=== "英文"

    Step 1: Processing the Ignorable and ProcessContent Attributes 

    An element shall be marked as ignored if all of the following conditions are satisfied:

    1) The namespace of this element is declared as ignorable by an Ignorable attribute of this element or of an ancestor element;
    2) The namespace of this element is not included in the given application configuration;
    3) This element does not match any process-content name pairs declared by this element or some ancestor; and
    4) This element is neither an application-defined extension element nor a descendant of an applicationdefined extension element.

    An attribute shall be marked as ignored if all of the following conditions are satisfied:

    5) The namespace of this attribute is declared as ignorable by an Ignorable attribute of the element having this attribute or of an ancestor element;
    6) The namespace of this attribute is not included in the given application configuration; and
    7) This attribute does not belong to an application-defined extension element or a descendant of an application-defined extension element

    An element shall be marked as unwrapped if all the following conditions are satisfied:

    8) The namespace of this element is declared as ignorable by an Ignorable attribute of this element or of some ancestor element;
    9) The namespace of this element is not included in the given application configuration;
    10) This element matches a process-content name pair declared by this element or some ancestor; and
    11) This element is neither an application-defined extension element nor a descendant of an applicationdefined extension element.

    An element marked as unwrapped shall not have an xml:base, xml:lang or xml:space attribute.

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
        xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:i1="http://www.example.com/i1"
        mce:Ignorable="i1"
        mce:ProcessContent="i1:bar"
        i1:foo="">
        <i1:foo><fooChild/></i1:foo>
        <i1:bar><barChild/></i1:bar>
        <i1:baz i1:baz=""><i1:bazChild/></i1:baz>
    </example>
    ```

    The namespace "http://www.example.com/i1" is declared as ignorable. A pair ("http://www.example.com/i1", bar) is declared as a process-content name pair. Suppose that a given markup configuration is a singleton containing ("http://www.example.com/i1", baz) and that a given application configuration does not contain "http://www.example.com/i1". Then, the i1:foo attribute and the i1:foo element are marked as ignored, and the i1:bar element is marked as unwrapped. However, the i1:baz element is not marked as either ignored or unwrapped, as it is an application-defined extension element. Likewise, neither the i1:baz attribute nor the i1:bazChild element are marked. Neither fooChild nor barChild are marked as ignored or unwrapped although their parents are marked as ignored or unwrapped. end example]

### 9.3 Step 2: 处理 AlternateContent, Choice 和 Fallback 元素 

=== "中文"

    如果满足以下条件，选择元素将被标记为 "已选择"：

    1) 该元素的 Requires 属性所指定的每个命名空间都包含在给定的应用程序配置中；
    2) 前面的同级 "选择 "元素均未标记为选中；以及
    3) 该元素不是应用程序定义的扩展元素的后代。
    
    如果满足以下条件，回退元素将被标记为 "已选"：
    
    1) 前面的同级 "选择 "元素均未标记为选中；以及
    2) 该元素不是应用程序定义的扩展元素的后代。

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:n1="http://www.example.com/n1"
         xmlns:n2="http://www.example.com/n2"
         xmlns:n3="http://www.example.com/n3">
         <mce:AlternateContent>
             <mce:Choice Requires="n1 n2"> <!-- Choice #1 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="n3">...</mce:Choice> <!-- Choice #1-1 -->
                     <mce:Fallback>...</mce:Fallback> <!-- Fallback #1-1 -->
                 </mce:AlternateContent>
             </mce:Choice>
             <mce:Choice Requires="n1"> <!-- Choice #2 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="n3">...</mce:Choice> <!-- Choice #2-1 -->
                     <mce:Fallback>...</mce:Fallback> <!-- Fallback #2-1 -->
                 </mce:AlternateContent>
             </mce:Choice>
             <mce:Fallback>...</mce:Fallback> <!-- Fallback #1 -->
         </mce:AlternateContent>
    </example>
    ```

    根元素的子元素是 AlternateContent 元素。假设应用程序配置包含三个命名空间："http://www.example.com/n1"、"http://www.example.com/n2 "和 http://www.example.com/n3。那么选择 #1、选择 #1-1 和选择 #2-1 被标记为选中，而选择 #2、回退 #1、回退 #1-1 和回退 #2-1 没有被标记为选中。请注意，标记为选中的选择 #2-1 出现在未选中的选择 #2 下方。

    假设应用程序配置包含两个命名空间 "http://www.example.com/n1 "和 "http://www.example.com/n2"，但不包含 "http://www.example.com/n3"。那么，选择 #1、回退 #1-1 和回退 #2-1 被标记为已选。 end example]

=== "英文"

    Step 2: Processing the AlternateContent, Choice and Fallback Elements 

    A Choice element shall be marked as selected if the following conditions are satisfied:

    1) Each of the namespaces specified by the Requires attribute of this element is included in the given application configuration;
    2) No preceding sibling Choice element is marked as selected; and
    3) The element is not a descendant of an application-defined extension element.
    
    A Fallback element shall be marked as selected if the following conditions are satisfied:
    
    1) No preceding sibling Choice element is marked as selected; and
    2) The element is not a descendant of an application-defined extension element.

    [Example:

    ```xml
    <example xmlns="http://www.example.com/"
         xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
         xmlns:n1="http://www.example.com/n1"
         xmlns:n2="http://www.example.com/n2"
         xmlns:n3="http://www.example.com/n3">
         <mce:AlternateContent>
             <mce:Choice Requires="n1 n2"> <!-- Choice #1 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="n3">...</mce:Choice> <!-- Choice #1-1 -->
                     <mce:Fallback>...</mce:Fallback> <!-- Fallback #1-1 -->
                 </mce:AlternateContent>
             </mce:Choice>
             <mce:Choice Requires="n1"> <!-- Choice #2 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="n3">...</mce:Choice> <!-- Choice #2-1 -->
                     <mce:Fallback>...</mce:Fallback> <!-- Fallback #2-1 -->
                 </mce:AlternateContent>
             </mce:Choice>
             <mce:Fallback>...</mce:Fallback> <!-- Fallback #1 -->
         </mce:AlternateContent>
    </example>
    ```

    The child of the root element is an AlternateContent element. Suppose that an application configuration contains three namespaces, “http://www.example.com/n1”, “http://www.example.com/n2”, and http://www.example.com/n3. Then Choice #1, Choice #1-1, and Choice #2-1 are marked as selected, and Choice #2, Fallback #1, Fallback #1-1, and Fallback #2-1 are not. Note that Choice #2-1, which is marked as selected, appears under Choice #2, which is not.

    Suppose that an application configuration contains two namespaces, “http://www.example.com/n1” and “http://www.example.com/n2”, but not “http://www.example.com/n3”. Then, Choice #1, Fallback #1-1, and Fallback #2-1 are marked as selected. end example]


### 9.4 Step 3: 处理 MustUnderstand 属性并创建输出文档

=== "中文"

    输出文档应从根元素开始，按以下步骤修改输入文档。

    对于输入文档中的每个元素，如果该元素是
    
    1) 标记为忽略:
    
        a) 删除该元素及其属性和内容。
    
    2) 标记为未包装:
    
        a) 检查该元素的每个 MustUnderstand 属性。如果该属性声明的任何命名空间不在应用程序配置中，则发出不匹配信号。
        b) 用该元素的内容替换该元素。[注意：此元素的属性将丢失。 end note.] 
        c) 对该元素的每个子元素递归应用步骤 3 的程序。
    
    3) 不是应用程序定义的扩展元素后代的 AlternateContent 元素：
        
        a) 如果该 AlternateContent 元素的任何子元素既不是选择元素，也不是回退元素，且未标记为忽略，则发出不匹配信号。
        b) 如果没有一个子代 "选择 "或 "后备 "元素被标记为 "选中"，则删除此 "替代内容 "元素及其内容。如果一个子选择或后备元素被标记为选中，则用标记为选中的选择或后备元素的内容替换此 AlternateContent 元素。
        c) 检查此 AlternateContent 元素和标记为 "选择 "或 "回退 "元素（如果有）的每个 MustUnderstand 属性。如果这些属性声明的命名空间不在应用程序配置中，则发出不匹配信号。
        d) 对标记为 "选择 "或 "后备 "元素的每个子元素（如果有）递归应用步骤 3 的操作步骤。
    
    4) 应用程序定义的扩展元素：
        
        a) 不更改元素或其内容，并将其包含在输出文档中。
    
    5) 否则:
        
        a) 移除 Ignorable、ProcessContent 和 MustUnderstand 属性以及标记为忽略的属性。
        b) 对该元素的每个子元素递归应用步骤 3 的程序。
    
    [Note: 如果选择或回退元素的任何祖先元素被忽略，或任何祖先选择或回退元素未被选择，则该元素的内容不会出现在输出文档中。 end note]
    
    [Note: 输出文档可能包含应用程序配置中未包含的命名空间中的属性或元素。 end note]
    
    [Note: 除应用程序定义的扩展元素外，标记兼容命名空间中的元素和属性不会出现在输出文档中。 end note]

    [Example:

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar"
     mce:Ignorable="foo bar"
     mce:ProcessContent="foo:unwrapped">
     <mce:AlternateContent>
         <mce:Choice Requires="foo"> <!-- Choice #1 -->
             <foo:foo/> <!-- Foo #1 -->
             <bar:bar> <!-- Bar #1 -->
             <mce:AlternateContent>
             <mce:Choice Requires="bar"> <!-- Choice #1-1 -->
             <Choice1-1/>
             </mce:Choice>
             <mce:Fallback> <!-- Fallback #1-1 -->
             <Fallback1-1/>
             </mce:Fallback>
             </mce:AlternateContent>
             </bar:bar>
         </mce:Choice>
         <mce:Choice Requires="bar"> <!-- Choice #2 -->
             <bar:bar/> <!-- Bar #2 -->
             <foo:unwrapped> <!-- Foo #2 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="foo"> <!-- Choice #2-1 -->
                     <Choice2-1/>
                     </mce:Choice>
                 <mce:Fallback> <!-- Fallback #2-1 -->
                     <Fallback2-1/>
                 </mce:Fallback>
                 </mce:AlternateContent>
             </foo:unwrapped>
         </mce:Choice>
     </mce:AlternateContent>
    </example>
    ```

    假设应用程序配置包含命名空间 http://www.example.com/foo。在步骤 1 中，条形图 #1 和条形图 #2 被标记为忽略。在步骤 2 中，选择 #1、回退 #1-1 和选择 #2-1 被标记为已选择。但是，在步骤 3 中，由于条形图 #1 被标记为忽略，因此回退条形图 #1-1 的内容将被丢弃。同样，选择 #2-1 的内容也会被丢弃，因为选择 #2 没有被标记为选中。在步骤 3 中，条形码 #1 及其内容（包括回退条形码 #1-1）被丢弃。这样，就生成了以下输出文档。

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <foo:foo/>
    </example>
    ```

    假设应用程序配置包含命名空间 http://www.example.com/bar。在步骤 1 中，Foo #1 被标记为忽略，Foo #2 被标记为未封装。在步骤 2 中，选择 #1-1、选择 #2 和回退 #2-1 被标记为已选择。但是，在步骤 3 中，由于选择 #1 没有被标记为选中，因此选择 #1-1 的内容将被丢弃。由于 Foo #2 被标记为解包，所以回退 #2-1 的内容不会被丢弃。这样，就生成了以下输出文档。
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <bar:bar/>
     <Fallback2-1/>
    </example>
    ```

    假设应用程序配置包含两个命名空间 http://www.example.com/foo 和 http://www.example.com/bar。在步骤 1 中，没有元素或属性被标记为忽略或未封装。在步骤 2 中，选择 #1、选择 #1-1 和选择 #2-1 被标记为已选择。但是，在步骤 3 中，由于选择 #2 没有被标记为选中，因此选择 #2-1 的内容将被丢弃。这样，就生成了以下输出文档。

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <foo:foo/>
     <bar:bar>
     <Choice1-1/>
     </bar:bar>
    </example>
    ```

    end example]

=== "英文"

    Step 3: Processing the MustUnderstand Attribute and Creating the Output Document

    The output document shall be constructed by modifying the input document with the following procedure, beginning with the root element.

    For each element in the input document, if the element is:
    
    1) Marked as ignored:
    
        a) Remove this element and its attributes and contents.
    
    2) Marked as unwrapped:
    
        a) Examine each MustUnderstand attribute of this element. If any of the namespaces declared by this attribute are not in the application configuration, signal a mismatch. 
        b) Replace this element with the content of this element. [Note: The attributes of this element will be lost. end note.] 
        c) Recursively apply the Step 3 procedure to each child of this element.
    
    3) An AlternateContent element that is not a descendant of an application-defined extension element:
        
        a) If any child element of this AlternateContent element is neither a Choice nor a Fallback element, and is not marked as ignored, signal a mismatch.
        b) If none of the child Choice or Fallback elements is marked as selected, remove this AlternateContent element and its contents. If a child Choice or Fallback element is marked as selected, replace this AlternateContent element with the content of the Choice or Fallback element marked as selected.
        c) Examine each MustUnderstand attribute of this AlternateContent element and of the Choice or Fallback element marked as selected, if any. If any of the namespaces declared by these attributes are not in the application configuration, signal a mismatch.
        d) Recursively apply the Step 3 procedure to each child element of the Choice or Fallback element marked as selected, if any.
    
    4) An application-defined extension element:
        
        a) Make no changes to the element or its contents, and include them in the output document.
    
    5) Otherwise:
        
        a) Remove Ignorable, ProcessContent, and MustUnderstand attributes as well as attributes marked as ignored.
        b) Recursively apply the Step 3 procedure to each child of this element.
    
    [Note: The content of a selected Choice or Fallback element does not appear in the output document if any ancestor of this element is ignored or any ancestor Choice or Fallback element is not selected. end note]
    
    [Note: Output documents might contain attributes or elements in namespaces that are not contained in the application configuration. end note]
    
    [Note: With the exception of those within application-defined extension elements, elements and attributes in the Markup Compatibility namespace do not appear in the output document. end note]

    [Example:

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar"
     mce:Ignorable="foo bar"
     mce:ProcessContent="foo:unwrapped">
     <mce:AlternateContent>
         <mce:Choice Requires="foo"> <!-- Choice #1 -->
             <foo:foo/> <!-- Foo #1 -->
             <bar:bar> <!-- Bar #1 -->
             <mce:AlternateContent>
             <mce:Choice Requires="bar"> <!-- Choice #1-1 -->
             <Choice1-1/>
             </mce:Choice>
             <mce:Fallback> <!-- Fallback #1-1 -->
             <Fallback1-1/>
             </mce:Fallback>
             </mce:AlternateContent>
             </bar:bar>
         </mce:Choice>
         <mce:Choice Requires="bar"> <!-- Choice #2 -->
             <bar:bar/> <!-- Bar #2 -->
             <foo:unwrapped> <!-- Foo #2 -->
                 <mce:AlternateContent>
                     <mce:Choice Requires="foo"> <!-- Choice #2-1 -->
                     <Choice2-1/>
                     </mce:Choice>
                 <mce:Fallback> <!-- Fallback #2-1 -->
                     <Fallback2-1/>
                 </mce:Fallback>
                 </mce:AlternateContent>
             </foo:unwrapped>
         </mce:Choice>
     </mce:AlternateContent>
    </example>
    ```

    Suppose that an application configuration contains the namespace http://www.example.com/foo. In Step 1, Bar #1 and Bar #2 are marked as ignored. In Step 2, Choice #1, Fallback #1-1, and Choice #2-1 are marked as selected. However, in Step 3, the content of Fallback #1-1 is discarded, since Bar #1 is marked as ignored. Likewise, the content of Choice #2-1 is discarded, since Choice #2 is not marked as selected. In Step 3, Bar #1 and its contents, including Fallback #1-1, are discarded. Thus, the following output document is constructed.

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <foo:foo/>
    </example>
    ```

    Suppose that an application configuration contains the namespace http://www.example.com/bar. In Step 1, Foo #1 is marked as ignored and Foo #2 is marked as unwrapped. In Step 2, Choice #1-1, Choice #2, and Fallback #2-1 are marked as selected. However, in Step 3, the content of Choice #1-1 is discarded, since Choice #1 is not marked as selected. Since Foo #2 is marked as unwrapped, the content of Fallback #2-1 is not discarded. Thus, the following output document is constructed.
    
    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <bar:bar/>
     <Fallback2-1/>
    </example>
    ```

    Suppose that an application configuration contains two namespaces, http://www.example.com/foo and http://www.example.com/bar. In Step 1, no elements or attributes are marked as ignored or unwrapped. In Step 2, Choice #1, Choice #1-1, and Choice #2-1 are marked as selected. However, in Step 3, the content of Choice #2-1 is discarded, since Choice #2 is not marked as selected. Thus, the following output document is constructed.

    ```xml
    <example xmlns="http://www.example.com"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:foo="http://www.example.com/foo"
     xmlns:bar="http://www.example.com/bar">
     <foo:foo/>
     <bar:bar>
     <Choice1-1/>
     </bar:bar>
    </example>
    ```

    end example]


## Annex A (informative) 示例 

Annex A (informative) Examples 

### A.1 语法示例 

Syntactic Examples 

#### A.1.1 概述 

=== "中文"

    本条款提供的示例进一步展示了 MCE 元素和属性的语法。

=== "英文"

    General

    This clause provides examples further demonstrating the syntax of MCE elements and attributes.

#### A.1.2 Ignorable 属性: 绑定到命名空间的多个前缀 

=== "中文"

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo mce:Ignorable="i1"
     xmlns:i1="http://www.example.com/i1"
     xmlns:i2="http://www.example.com/i2">
     <bar mce:Ignorable="i2">…</bar>
     <bar mce:Ignorable="i1 i2">…</bar>
     <bar mce:Ignorable="i1alias i2"
     xmlns:i1alias="http://www.example.com/i1">…</bar>
     </foo>
    </example>
    ```

    第一个 bar 元素的 Ignorable 属性将命名空间 "http://www.example.com/i2 "声明为不可忽略。第二个 bar 元素的 Ignorable 属性将 "http://www.example.com/i1 "和 "http://www.example.com/i2 "都声明为不可忽略，但前者已经被父 foo 元素的 Ignorable 属性声明。第三个 bar 元素的 Ignorable 属性也将这两个命名空间声明为可忽略，不过命名空间前缀是 i1alias 而不是 i1。因此，虽然词法值不同，但就 MCE 处理而言，这三个 Ignorable 属性使每个 bar 元素的内容得到同等对待。

=== "英文"

    Ignorable Attribute: Multiple Prefixes Bound to a Namespace 

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo mce:Ignorable="i1"
     xmlns:i1="http://www.example.com/i1"
     xmlns:i2="http://www.example.com/i2">
     <bar mce:Ignorable="i2">…</bar>
     <bar mce:Ignorable="i1 i2">…</bar>
     <bar mce:Ignorable="i1alias i2"
     xmlns:i1alias="http://www.example.com/i1">…</bar>
     </foo>
    </example>
    ```

    The Ignorable attribute of the first bar element declares the namespace “http://www.example.com/i2” as ignorable. The Ignorable attribute of the second bar element declares both “http://www.example.com/i1” and “http://www.example.com/i2” as ignorable, but the former is already declared by the Ignorable attribute of the parent foo element. The Ignorable attribute of the third bar element also declares these two namespaces as ignorable, although the namespace prefix is i1alias rather than i1. Therefore, although the lexical values are different, these three Ignorable attributes cause the content of each bar element to be treated equally as far as MCE processing is concerned.

#### A.1.3 Ignorable 属性: 不符合规定使用 

=== "中文"

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo1 mce:Ignorable="i1">
     <foo2 xmlns:i1="http://www.example.com/i1">…</foo2>
     </foo1>
     <foo3 mce:Ignorable="i2">…</foo3>
     <foo4 xmlns:i2="http://www.example.com/i2"/>
    </example>
    ```

    该文件不符合规范有两个原因： 首先，foo1 元素有一个 Ignorable 属性，但其值 i1 并未绑定到范围内命名空间。其次，foo3 元素也有一个 Ignorable 属性，但其值 i2 也没有绑定到范围内命名空间。

=== "英文"

    Ignorable Attribute: Non-conformant Use 

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo1 mce:Ignorable="i1">
     <foo2 xmlns:i1="http://www.example.com/i1">…</foo2>
     </foo1>
     <foo3 mce:Ignorable="i2">…</foo3>
     <foo4 xmlns:i2="http://www.example.com/i2"/>
    </example>
    ```

    This document is non-conformant for two reasons: First, the foo1 element has an Ignorable attribute, but the value i1 is not bound to an in-scope namespace. Second, the foo3 element also has an Ignorable attribute, but the value i2 is not bound to an in-scope namespace either.

#### A.1.4 ProcessContent 属性: 绑定到命名空间的多个前缀 

=== "中文"

    ```xml
    <example xmlns=http://www.example.com
     xmlns:mce=http://schemas.openxmlformats.org/markup-compatibility/2006
     xmlns:n1="http://www.example.com/n1"
     xmlns:n1alias=http://www.example.com/n1
     mc:Ignorable="n1alias"
     mc:ProcessContent="n1:foo" >
     <n1alias:foo>
     <bar/>
     </n1alias:foo>
    </example>
    ```

    命名空间 "http://www.example.com/n1 "被声明为可忽略。该命名空间和本地名称 foo 这一对被 ProcessContent 属性声明为进程-内容名称对。n1alias:foo 元素与这一对匹配，因为 n1 和 n1alias 共享相同的命名空间名称。

=== "英文"

    ProcessContent Attribute: Multiple Prefixes Bound to a Namespace 

    ```xml
    <example xmlns=http://www.example.com
     xmlns:mce=http://schemas.openxmlformats.org/markup-compatibility/2006
     xmlns:n1="http://www.example.com/n1"
     xmlns:n1alias=http://www.example.com/n1
     mc:Ignorable="n1alias"
     mc:ProcessContent="n1:foo" >
     <n1alias:foo>
     <bar/>
     </n1alias:foo>
    </example>
    ```

    The namespace "http://www.example.com/n1" is declared as ignorable. The pair of this namespace and a local name foo is declared as a process-content name pair by the ProcessContent attribute. The n1alias:foo element matches this pair, because n1 and n1alias share the same namespace name.

#### A.1.5 ProcessContent 属性: 不符合规定使用 

=== "中文"

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo1 xmlns:i2="http://www.example.com/i2">
     <foo2 mce:ProcessContent="i2:*">…</foo2>
     </foo1>
    </example>
    ```

    foo2 元素有一个 ProcessContent 属性。其值是一个标记 "i2:*"，其中 i2 是与范围内命名空间 "http://www.example.com/i2 "绑定的命名空间前缀。但是，该命名空间并未声明为可忽略。因此，本示例不符合规范。

=== "英文"

    ProcessContent Attribute: Non-conformant Use 

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <foo1 xmlns:i2="http://www.example.com/i2">
     <foo2 mce:ProcessContent="i2:*">…</foo2>
     </foo1>
    </example>
    ```

    The foo2 element has a ProcessContent attribute. The value is a token "i2:*", where i2 is a namespace prefix bound to an in-scope namespace "http://www.example.com/i2". However, this namespace is not declared as ignorable. As such, this example is non-conformant.

#### A.1.6 MustUnderstand 属性: 不符合规定使用 

=== "中文"

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:n1="http://www.example.com/n1">
     <foo mce:MustUnderstand="n1 n2"/>
    </example>
    ```

    元素 foo 的 MustUnderstand 属性包含 n1 和 n2。虽然 n1 与范围内命名空间名称 "http://www.example.com/n1 "绑定，但 n2 并非如此。因此，该文件不符合规范。

=== "英文"

    MustUnderstand Attribute: Non-conformant Use 

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:n1="http://www.example.com/n1">
     <foo mce:MustUnderstand="n1 n2"/>
    </example>
    ```

    The MustUnderstand attribute of the element foo contains n1 and n2. Although n1 is bound to an in-scope namespace name "http://www.example.com/n1", n2 is not. As such, this document is non-conformant.

#### A.1.7 AlternateContent 元素: 功能可扩展性

=== "中文"

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:mce2="http://www.example.com/markup-compatibility/v2"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="mce2" mce2:foo="">
     <mce2:NewChoice … />…</mce2:NewChoice>
     <mce:Choice Requires="n1">…</mce:Choice>
     <mce:Fallback>…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```

    AlternateContent 元素有一个 Ignorable 属性。AlternateContent 元素的子元素有来自同一命名空间的 Choice 元素和 Fallback 元素，以及来自另一命名空间的 NewChoice 元素。由于 NewChoice 元素的命名空间（可能是《标记兼容与扩展》未来假设版本的一部分）被声明为可忽略，因此本文档符合要求。如果 NewChoice 元素的命名空间未声明为可忽略，则该文档将不符合标准。

=== "英文"

    AlternateContent Element: Future Extensibility

    ```xml
    <example xmlns="http://www.example.com/"
     xmlns:mce="http://schemas.openxmlformats.org/markup-compatibility/2006"
     xmlns:mce2="http://www.example.com/markup-compatibility/v2"
     xmlns:n1="http://www.example.com/n1">
     <mce:AlternateContent mce:Ignorable="mce2" mce2:foo="">
     <mce2:NewChoice … />…</mce2:NewChoice>
     <mce:Choice Requires="n1">…</mce:Choice>
     <mce:Fallback>…</mce:Fallback>
     </mce:AlternateContent>
    </example>
    ```

    The AlternateContent element has an Ignorable attribute. The AlternateContent element has as children a Choice element and a Fallback element from the same namespace and a NewChoice element from another namespace. Because the namespace of the NewChoice element, which might be part of a hypothetical future version of Markup Compatibility and Extensibility, is declared as ignorable, this document is conformant. If the namespace of the NewChoice element were not declared as Ignorable, the document would be nonconformant.

### A.2 语义示例 

Semantic Examples 

#### A.2.1 概述 

=== "中文"

    本条款提供了在不同的标记配置和应用配置下，处理支持使用 MCE 的标记规范中的输入文档以及由 MCE 处理器生成的相应输出文档的示例。

=== "英文"

    This clause provides examples of processing input documents in a markup specification that supports the use of MCE and the corresponding output documents generated by an MCE processor, given different markup configurations and application configurations.

#### A.2.2 Ignorable 属性 

=== "中文"

    本示例展示了如何使用 Ignorable 属性定义可忽略命名空间，以及具有不同应用程序配置的 MCE 处理器如何处理示例输入文档。

    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"
     v3:Luminance="13"/>
    <Circles>
    ```

    这份文档中有三个命名空间，“http://www.example.com/Circles/v1”，“http://www.example.com/Circles/v2”和“http://www.example.com/Circles/v3”，分别对应一个标记规范的三个版本。版本1引入了版本1的命名空间中的Circle元素。版本2引入了版本2的命名空间中的Opacity属性。版本3引入了版本3的命名空间中的Luminance属性。在这份文档中，版本2和版本3的命名空间都被声明为可忽略的。
    
    首先，假设应用程序配置包含版本1、2和3的命名空间。那么，输出文档将包含Opacity和Luminance属性。输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"
     v3:Luminance="13"/>
    </Circles>
    ```

    第二，假设应用程序配置包含版本1和2的命名空间，但不包含版本3的命名空间。那么，输出文档包含不透明度属性，但不包含亮度属性。
    
    输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
    </Circles>
    ```

    第三，假设应用程序配置包含版本 1 的命名空间，但不包含版本 2 或 3 的命名空间。在这种情况下，输出文档既不包含不透明度属性也不包含亮度属性。
    
    输出文档：
    
    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
     <Circle Center="0,0" Radius="20" Color="Blue"/>
    </Circles>
    ```

=== "英文"

    Ignorable Attribute 

    This example shows how to use the Ignorable attribute to define ignorable namespaces and how MCE processors with different application configurations process the example input document.

    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"
     v3:Luminance="13"/>
    <Circles>
    ```

    Three namespaces in this document, “http://www.example.com/Circles/v1”, “http://www.example.com/Circles/v2”, and “http://www.example.com/Circles/v3” capture three versions of a markup specification. Version 1 introduces Circle elements of the namespace for version 1. Version 2 introduces the Opacity attribute of the namespace for version 2. Version 3 introduces the Luminance attribute of the namespace for version 3. In this document, both the namespace for version 2 and that for version 3 are declared as ignorable.

    First, suppose that the application configuration contains the namespaces for versions 1, 2, and 3. Then, the output document contains the Opacity and Luminance attributes. Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"
     v3:Luminance="13"/>
    </Circles>
    ```

    Second, suppose that the application configuration contains the namespaces for versions 1 and 2 but not the one for version 3. Then, the output document contains the Opacity attribute but does not contain the Luminance attribute.
    
    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
    </Circles>
    ```

    Third, suppose that the application configuration contains the namespace for version 1 but not those for versions 2 or 3. In this case, the output document contains neither the Opacity attribute nor the Luminance attribute.
    
    Output document:
    
    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
     <Circle Center="0,0" Radius="20" Color="Blue"/>
    </Circles>
    ```

#### A.2.3 Ignorable 和 ProcessContent 属性

=== "中文"

    这个例子展示了如何使用ProcessContent属性来处理可忽略元素内的子元素，以及具有不同应用配置的MCE处理器如何处理示例输入文档。
    
    输入文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2"
     mc:ProcessContent="v2:Blink">
     <v2:Watermark Opacity="v0.1">
     <Circle Center="0,0" Radius="20" Color="Blue"/>
     </v2:Watermark>
     <v2:Blink>
     <Circle Center="13,0" Radius="20" Color="Yellow"/>
     </v2:Blink>
    </Circles>
    ```

    这份文档中有两个命名空间，“http://www.example.com/Circles/v1” 和 “http://www.example.com/Circles/v2”，分别代表一个标记规范的两个版本。版本1引入了版本1的命名空间中的 Circles 和 Circle 元素。版本2引入了版本2的命名空间中的 Watermark 和 Blink 元素。版本2的命名空间被声明为可忽略的，而 Blink 元素匹配了在根元素处声明的一个过程内容名称对（“http://www.example.com/Circles/v2”, Blink）。
    
    首先，假设一个应用配置包含了版本1和版本2的命名空间。那么，输出文档将包含输入文档中的所有元素。
    
    输出文档:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <v2:Watermark Opacity="v0.1">
         <Circle Center="0,0" Radius="20" Color="Blue"/>
     </v2:Watermark>
     <v2:Blink>
         <Circle Center="13,0" Radius="20" Color="Yellow"/>
     </v2:Blink>
    </Circles>
    ```

    第二，假设一个应用程序配置包含版本1的命名空间，但不包含版本2的命名空间。那么，输出文档不包含版本2的命名空间中的Watermark和Blink元素。然而，Blink元素的内容会被保留，因为该元素与一个声明的process-content名称对匹配。

    输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
         <Circle Center="13,0" Radius="20" Color="Yellow"/>
    </Circles>
    ```

=== "英文"

    Ignorable and ProcessContent Attributes

    This example shows how to use the ProcessContent attribute to process child elements within ignorable elements and how MCE processors with different application configurations process the example input document.

    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2"
     mc:ProcessContent="v2:Blink">
     <v2:Watermark Opacity="v0.1">
     <Circle Center="0,0" Radius="20" Color="Blue"/>
     </v2:Watermark>
     <v2:Blink>
     <Circle Center="13,0" Radius="20" Color="Yellow"/>
     </v2:Blink>
    </Circles>
    ```

    Two namespaces in this document, “http://www.example.com/Circles/v1” and “http://www.example.com/Circles/v2”, represent two versions of a markup specification. Version 1 introduces Circles and Circle elements of the namespace for version 1. Version 2 introduces Watermark and Blink elements of the namespace for version 2. The namespace for version 2 is declared as ignorable and the Blink element matches a process-content name pair (“http://www.example.com/Circles/v2”, Blink) declared at the root element.

    First, suppose that an application configuration contains the namespaces for Versions 1 and 2. Then, the output document contains all elements in the input document.

    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <v2:Watermark Opacity="v0.1">
         <Circle Center="0,0" Radius="20" Color="Blue"/>
     </v2:Watermark>
     <v2:Blink>
         <Circle Center="13,0" Radius="20" Color="Yellow"/>
     </v2:Blink>
    </Circles>
    ```

    Second, suppose that an application configuration contains the namespace for version 1 but not the one for version 2. Then, the output document does not contain the Watermark and Blink elements, which are of the namespace for version 2. However, the content of the Blink element is retained, since this element matches a declared process-content name pair.

    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
         <Circle Center="13,0" Radius="20" Color="Yellow"/>
    </Circles>
    ```

#### A.2.4 Non-Ignorable 和 Non-Understood 命名空间  

=== "中文"

    不可忽略和不可理解的命名空间
    
    这个例子展示了MCE处理器在不同配置下对命名空间的基本处理。
    
    输入文档:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5" />
    </Circles>
    ```

    这份文档中有两个命名空间，“http://www.example.com/Circles/v1” 和 “http://www.example.com/Circles/v2”，分别代表一个标记规范的两个版本。版本1引入了版本1的命名空间中的 Circles 和 Circle 元素。版本2引入了版本2的命名空间中的 Opacity 属性。
    
    首先，假设一个应用程序配置包含版本1和版本2的命名空间。那么，输出文档与输入文档相同，可能会省略标记兼容性命名空间的声明。
    
    其次，假设一个应用程序配置包含版本1的命名空间，但不包含版本2的命名空间。那么，在第3步（§9.4）检查 Opacity 属性时，MCE 处理器将报告不匹配情况。

=== "英文"

    Non-Ignorable and Non-Understood Namespace  

    This example shows the basic handling of namespaces by MCE processors with different configurations.

    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5" />
    </Circles>
    ```

    Two namespaces in this document, “http://www.example.com/Circles/v1” and “http://www.example.com/Circles/v2”, represent two versions of a markup specification. Version 1 introduces Circles and Circle elements of the namespace for version 1. Version 2 introduces an Opacity attribute of the namespace for version 2.
    
    First, suppose that an application configuration contains the namespaces for versions 1 and 2. Then, the output document is identical to the input document, with the possible exception of omitting the declaration of the Markup Compatibility namespace.
    
    Second, suppose that an application configuration contains the namespace for version 1 but not the one for version 2. Then, the MCE processor will report a mismatch when the Opacity attribute is examined in Step 3 (§9.4).

#### A.2.5 MustUnderstand 属性 

=== "中文"

    这个例子展示了如何使用MustUnderstand属性来要求处理命名空间，以及具有不同应用程序配置的MCE处理器如何处理示例输入文档。
    
    输入文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:MustUnderstand="v2">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5" />
    </Circles>
    ```

    这份文档与之前的示例类似。唯一的区别是在根元素中添加了MustUnderstand属性。

    MCE处理器的行为相同，唯一的区别是如果应用程序配置中不包含命名空间"http://www.example.com/Circles/v2"，则会发出不匹配的信号。

=== "英文"

    MustUnderstand Attribute 

    This example shows how to use the MustUnderstand attribute to require handling of namespaces and how MCE processors with different application configurations process the example input document. 
    
    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:MustUnderstand="v2">
     <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5" />
    </Circles>
    ```

    This document is similar to the previous example. The only difference is the addition of the MustUnderstand attribute at the root element.

    The MCE processor behaves the same, except that a mismatch is signaled if the application configuration does not contain the namespace "http://www.example.com/Circles/v2".

#### A.2.6 AlternateContent 元素 

=== "中文"

    这个例子展示了如何使用AlternateContent、Choice和Fallback元素来指定内容的替代表示，以及具有不同应用程序配置的MCE处理器如何处理示例输入文档。
    
    输入文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
     <mc:AlternateContent>
         <mc:Choice Requires="v3">
             <v3:Circle Center="0,0" Radius="20" Color="Blue" Opacity="0.5"
             Luminance="13"/>
         </mc:Choice>
             <mc:Fallback>
             <LuminanceFilter Luminance="13">
                 <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
             </LuminanceFilter>
         </mc:Fallback>
     </mc:AlternateContent>
    </Circles>
    ```

    这份文档中有三个命名空间，"http://www.example.com/Circles/v1"，"http://www.example.com/Circles/v2"和"http://www.example.com/Circles/v3"，分别对应一个标记规范的三个版本。版本1引入了LuminanceFilter和Circle元素，属于版本1的命名空间。版本2引入了版本2的命名空间的Opacity属性。版本3引入了版本3的命名空间的Circle元素。版本2和版本3的命名空间都声明为可忽略的。
    
    首先，假设应用程序配置包含版本1、2和3的命名空间。然后，由于选择了Choice元素，输出文档包含版本3的命名空间的Circle元素，但不包含LuminanceFilter元素。
    
    输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
         <v3:Circle Center="0,0" Radius="20" Color="Blue" Opacity="0.5" Luminance="13"/>
    </Circles>
    ```
    
    第二，假设应用程序配置包含版本1和2的命名空间，但不包含版本3的命名空间。然后，由于选择了Fallback元素，输出文档包含版本1的命名空间的LuminanceFilter和Circle元素，但不包含版本3的Circle元素。不会移除Opacity属性，因为应用程序配置包含版本2的命名空间。
    
    输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <LuminanceFilter Luminance="13">
         <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
     </LuminanceFilter>
    </Circles>
    ```

    第三，假设应用程序配置包含版本 1 的命名空间，但不包含版本 2 或 3 的命名空间。那么，由于选择了 Fallback 元素，输出文档包含版本 1 的 LuminanceFilter 元素和 Circle 元素，但不包含版本 3 的 Circle 元素。此外，由于应用程序配置不包含版本 2 的命名空间，Opacity 属性被移除。
    
    输出文档：

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
     <LuminanceFilter Luminance="13">
         <Circle Center="0,0" Radius="20" Color="Blue"/>
     </LuminanceFilter>
    </Circles>
    ```

=== "英文"

    AlternateContent Element 

    This example shows how to use AlternateContent, Choice and Fallback elements to specify alternate representations of content and how MCE processors with different application configurations process the example input document.
    
    Input document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
     <mc:AlternateContent>
         <mc:Choice Requires="v3">
             <v3:Circle Center="0,0" Radius="20" Color="Blue" Opacity="0.5"
             Luminance="13"/>
         </mc:Choice>
             <mc:Fallback>
             <LuminanceFilter Luminance="13">
                 <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
             </LuminanceFilter>
         </mc:Fallback>
     </mc:AlternateContent>
    </Circles>
    ```

    Three namespaces in this document, "http://www.example.com/Circles/v1", "http://www.example.com/Circles/v2", and "http://www.example.com/Circles/v3" capture three versions of a markup specification. Version 1 introduces LuminanceFilter and Circle elements of the namespace for version 1. Version 2 introduces the Opacity attribute of the namespace for version 2. Version 3 introduces Circle elements of the namespace for version 3. Both the namespace for version 2 and that for version 3 are declared as ignorable.

    First, suppose that the application configuration contains the namespaces for versions 1, 2, and 3. Then, since the Choice element is selected, the output document contains Circle elements of the namespace for version 3 but does not contain the LuminanceFilter element.

    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2"
     xmlns:v3="http://www.example.com/Circles/v3"
     xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     mc:Ignorable="v2 v3">
         <v3:Circle Center="0,0" Radius="20" Color="Blue" Opacity="0.5" Luminance="13"/>
    </Circles>
    ```
    
    Second, suppose that the application configuration contains the namespaces for versions 1 and 2 but not the one for version 3. Then, since the Fallback element is selected, the output document contains the LuminanceFilter and Circle elements of the namespace for version 1 but does not contain Circle elements of that for version 3. The Opacity attribute is not removed, since the application configuration contains the namespace for version 2.
    
    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1"
     xmlns:v2="http://www.example.com/Circles/v2">
     <LuminanceFilter Luminance="13">
         <Circle Center="0,0" Radius="20" Color="Blue" v2:Opacity="0.5"/>
     </LuminanceFilter>
    </Circles>
    ```

    Third, suppose that the application configuration contains the namespace for version 1 but not those for versions 2 or 3. Then, since the Fallback element is selected, the output document contains the LuminanceFilter element and Circle elements of the namespace for version 1 but does not contain Circle elements of that for version 3. Furthermore, since the application configuration does not contain the namespace for version 2, the Opacity attribute is removed.

    Output document:

    ```xml
    <Circles xmlns="http://www.example.com/Circles/v1">
     <LuminanceFilter Luminance="13">
         <Circle Center="0,0" Radius="20" Color="Blue"/>
     </LuminanceFilter>
    </Circles>
    ```

#### A.2.7 应⽤程序定义的扩展元素内可忽略的内容

=== "中文"

    这个例子展示了如何在应用程序定义的扩展元素中使用可忽略内容，以进一步扩展现有的扩展。

    ChrisOffice v1 是 ECMA-376 的一个假设实现，允许将声音效果应用于现有的 SpreadsheetML 条件格式。这些数据存储在应用程序定义的扩展元素中，以便其他符合 ECMA-376 标准的应用程序可以往返传输这些数据，在 SpreadsheetML 中，一个应用程序定义的扩展元素（extLst）已经在 conditionalFormattingElements 元素下定义。
    
    ChrisOffice v2 添加了使用视频以及音频的功能。为了让 ChrisOffice v1 能够理解除视频以外的所有内容，必须使用不同的命名空间，以避免 ChrisOffice 在已理解的命名空间中发现未知内容。在这个例子中，ChrisOffice v1 没有自己的扩展元素在扩展元素内部，因此额外的内容是可忽略的，以便 ChrisOffice v1 在加载时丢弃它。
    
    输入文档:
    
    ```xml
    …
    <conditionalFormattingElements>
        <extLst>
            <ext uri="myurl" xmlns:co1="http://chrisoffice/v1">
                <co1:soundeffect mc:Ignorable="co2" xmlns:co2="http://chrisoffice/v2">
                    <co1:sourceFile>moo.mp3</co1:sourceFile>
                    <co2:sourceVideo>cow.mpg</co2:sourceFile>
                </co1:soundeffect>
            </ext>
        </extLst>
    </conditionalFormattingElements>
    …
    ```
    
    ChrisOffice v1在读取文件时会丢弃视频。由于不允许在应用程序定义的扩展元素内处理MCE结构，因此不理解原始音效结构的应用程序将不会不必要地丢弃整个扩展元素，包括新的视频内容。由于ChrisOffice v1理解扩展元素，并且该扩展元素的格式已知包含进一步的MCE结构，ChrisOffice随后将调用MCE处理器来处理该扩展元素的内容，并在读取文件时丢弃视频，因为co2命名空间被声明为可忽略的。
    
    输出文档（ChrisOffice v1）：
    
    ```xml
    …
    <conditionalFormattingElements>
         <extLst>
         <ext uri="myurl" xmlns:co1="http://chrisoffice/v1">
             <co1:soundeffect mc:Ignorable="co2" xmlns:co2="http://chrisoffice/v2">
                 <co1:sourceFile>moo.mp3</co1:sourceFile>
             </co1:soundeffect>
         </ext>
     </extLst>
    </conditionalFormattingElements>
    …
    ```

=== "英文"

    Ignorable Content Inside Application-Defined Extension Elements

    This example shows how to use ignorable content in application-defined extension elements in order to further extend an existing extension.
    
    ChrisOffice v1 is a hypothetical implementation of ECMA-376 that allows sound effects to be applied to existing SpreadsheetML conditional formatting. This data is stored inside application-defined extension elements in order that other ECMA-376-conformant applications can round-trip that data, and in SpreadsheetML, an application-defined extension element (extLst) is already defined under the conditionalFormattingElements element.
    
    ChrisOffice v2 adds the ability to use video as well as audio. To allow ChrisOffice v1 to understand everything except the video, a different namespace must be used to avoid ChrisOffice discovering unknown content in understood namespaces. In this example, ChrisOffice v1 doesn’t have its own extension elements within extension elements, so the extra content is ignorable in order that ChrisOffice v1 discards it upon load.
    
    Input document:
    
    ```xml
    …
    <conditionalFormattingElements>
        <extLst>
            <ext uri="myurl" xmlns:co1="http://chrisoffice/v1">
                <co1:soundeffect mc:Ignorable="co2" xmlns:co2="http://chrisoffice/v2">
                    <co1:sourceFile>moo.mp3</co1:sourceFile>
                    <co2:sourceVideo>cow.mpg</co2:sourceFile>
                </co1:soundeffect>
            </ext>
        </extLst>
    </conditionalFormattingElements>
    …
    ```
    
    ChrisOffice v1 will discard the video when it reads the file. Because processing of MCE constructs is not permitted inside application-defined extension elements, applications that do not understand the original sound effect construct will not needlessly throw away the entire extension element including the new video content. Because the extension element is understood by ChrisOffice v1, and the format of that extension element is known to contain further MCE constructs, ChrisOffice will subsequently invoke an MCE processor to process the content of that extension element and discard the video when it reads the file since the co2 namespace is declared as ignorable.
    
    Output document (ChrisOffice v1):
    
    ```xml
    …
    <conditionalFormattingElements>
         <extLst>
         <ext uri="myurl" xmlns:co1="http://chrisoffice/v1">
             <co1:soundeffect mc:Ignorable="co2" xmlns:co2="http://chrisoffice/v2">
                 <co1:sourceFile>moo.mp3</co1:sourceFile>
             </co1:soundeffect>
         </ext>
     </extLst>
    </conditionalFormattingElements>
    …
    ```

## Annex B (informative) 使用NVDL进行验证

=== "中文"

    基于命名空间的验证调度语言（NVDL）允许将文档分解为验证候选项，每个候选项都可以独立验证。
    
    标记文档可以满足本部分的要求，而不必是 Office Open XML 文档。以下 NVDL 脚本检查给定文档是否正确使用了 ECMA-376 的本部分定义的属性和元素。
    
    此 NVDL 脚本首先提取标记兼容性命名空间中的元素和属性，然后根据适当的 RELAX NG 模式对其进行验证。
    
    请注意，AlternateContent、Choice 和 Fallback 元素允许具有外部元素和属性。

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <rules xmlns="http://purl.oclc.org/dsdl/nvdl/ns/structure/1.0">
     <namespace match="attributes" ns="http://schemas.openxmlformats.org/markup-
     compatibility/2006">
     <validate schemaType="application/relax-ng-compact-syntax">
     <schema>
     namespace mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     nsList = list { xsd:NCName* }
     qnameList = list { (xsd:QName | xsd:string {pattern = "\i\c*:\*" })*}
     start = element * {
     attribute mc:Ignorable { nsList }?,
     attribute mc:ProcessContent { qnameList }?,
     attribute mc:MustUnderstand { nsList }?
     }
     </schema>
     </validate>
     </namespace>
     <namespace match="elements" ns="http://schemas.openxmlformats.org/markup-
     compatibility/2006">
     <validate schemaType="application/relax-ng-compact-syntax">
    <schema>
     default namespace ="http://schemas.openxmlformats.org/markup-compatibility/2006"
     nsList = list { xsd:NCName* }
     qnameList = list { (xsd:QName | xsd:string {pattern = "\i\c*:\*" })*}
     start = element AlternateContent {choice+,fallback?}
     choice = element Choice {attribute Requires { nsList }, text}
     fallback = element Fallback {text}
     </schema>
     </validate>
     </namespace>
     <namespace ns="" match="attributes">
     <attach/>
     </namespace>
     <anyNamespace match="elements attributes">
     <allow/>
     </anyNamespace>
    </rules>
    ```
    
    上述NVDL脚本中嵌入的两个RELAX NG模式可以用类似的XML Schema形式重写。

=== "英文"

    Annex B (informative) Validation Using NVDL

    Namespace-based Validation Dispatching Language (NVDL) allows documents to be decomposed into validation candidates, each of which can be validated independently.
    
    A markup document can satisfy requirements of this Part without being an Office Open XML document. The following NVDL script examines whether a given document correctly uses the attributes and elements as defined by this Part of ECMA-376.
    
    This NVDL script first extracts elements and attributes in the Markup Compatibility namespace, and then validates them against the appropriate RELAX NG schemas.
    
    Note that AlternateContent, Choice and Fallback elements are allowed to have foreign elements and attributes.
    
    
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <rules xmlns="http://purl.oclc.org/dsdl/nvdl/ns/structure/1.0">
     <namespace match="attributes" ns="http://schemas.openxmlformats.org/markup-
     compatibility/2006">
     <validate schemaType="application/relax-ng-compact-syntax">
     <schema>
     namespace mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
     nsList = list { xsd:NCName* }
     qnameList = list { (xsd:QName | xsd:string {pattern = "\i\c*:\*" })*}
     start = element * {
     attribute mc:Ignorable { nsList }?,
     attribute mc:ProcessContent { qnameList }?,
     attribute mc:MustUnderstand { nsList }?
     }
     </schema>
     </validate>
     </namespace>
     <namespace match="elements" ns="http://schemas.openxmlformats.org/markup-
     compatibility/2006">
     <validate schemaType="application/relax-ng-compact-syntax">
    <schema>
     default namespace ="http://schemas.openxmlformats.org/markup-compatibility/2006"
     nsList = list { xsd:NCName* }
     qnameList = list { (xsd:QName | xsd:string {pattern = "\i\c*:\*" })*}
     start = element AlternateContent {choice+,fallback?}
     choice = element Choice {attribute Requires { nsList }, text}
     fallback = element Fallback {text}
     </schema>
     </validate>
     </namespace>
     <namespace ns="" match="attributes">
     <attach/>
     </namespace>
     <anyNamespace match="elements attributes">
     <allow/>
     </anyNamespace>
    </rules>
    ```
    
    The two RELAX NG schemas embedded in the above NVDL script can be rewritten in the analogous XML Schema form.

## 参考书目 

=== "中文"

    除了规范性参考文献外，以下是这个国际标准的实施者和使用者有用的参考文献：
    
    - ECMA-376-1:2012, Information technology — Document description and processing languages — Office Open XML File Formats, Part 1: Fundamentals and Markup Language Reference.
    - ECMA-376-4:2012, Information technology — Document description and processing languages — Office Open XML File Formats, Part 4: Transitional Migration Features.
    - ISO/IEC 19757-2:2008, Information technology — Document Schema Definition Language (DSDL) — Part 2: Regular-grammar-based validation — RELAX NG
    - ISO/IEC 19757-4:2006, Information technology — Document Schema Definition Languages (DSDL) — Part 4: Namespace-based Validation Dispatching Language (NVDL).
    - XML Schema Part 0: Primer (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-0/
    - XML Schema Part 1: Structures (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-1/
    - XML Schema Part 2: Datatypes (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-2/

=== "英文"

    Bibliography

    In addition to the Normative References, the following are useful references for implementers and users of this International Standard:
    
    - ECMA-376-1:2012, Information technology — Document description and processing languages — Office Open XML File Formats, Part 1: Fundamentals and Markup Language Reference.
    - ECMA-376-4:2012, Information technology — Document description and processing languages — Office Open XML File Formats, Part 4: Transitional Migration Features.
    - ISO/IEC 19757-2:2008, Information technology — Document Schema Definition Language (DSDL) — Part 2: Regular-grammar-based validation — RELAX NG
    - ISO/IEC 19757-4:2006, Information technology — Document Schema Definition Languages (DSDL) — Part 4: Namespace-based Validation Dispatching Language (NVDL).
    - XML Schema Part 0: Primer (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-0/
    - XML Schema Part 1: Structures (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-1/
    - XML Schema Part 2: Datatypes (Second Edition), W3C Recommendation 28 October 2004, http://www.w3.org/TR/xmlschema-2/
