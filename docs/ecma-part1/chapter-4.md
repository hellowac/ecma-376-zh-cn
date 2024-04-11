# 4. 术语和定义

=== "中文"

    就本文件而言，适用以下术语和定义。 其他术语在以斜体出现的位置、语法规则的左侧或特定语言语法的子条款内进行定义（[第 17.16 节]和[第 18.17 节]）。 ECMA-376 本部分中明确定义的术语不应被假定为隐含地指其他地方定义的类似术语。

    !!! note info "注意"

        本部分使用 OPC 相关术语，这些术语在 ECMA-376-2 中定义。

    **application** — 消费者或生产者。

    **behavior** — 外在表现或动作。

    **behavior, implementation-defined** — 未指定的行为，其中每个实现都期望记录该行为，从而提高任何给定实现中的可预测性和可重复性。 （该术语有时称为“应用程序定义的行为”(application-defined behavior)。）
    
    **behavior, locale-specific** — 行为取决于当地的国籍、文化和语言习俗。
    
    **behavior, unspecified** — ECMA-376 未提出建议的行为。 (该术语有时称为“应用程序相关行为”(application-dependent behavior)。) 

    !!! note info "注意"
    
        要添加扩展，实现者必须使用 ECMA-376 描述的扩展性机制，而不是尝试通过赋予其他未指定行为以含义来实现此目的。
    
    **byte** — 8 位序列被视为一个单元。
    
    **comment** — 附加到文档内容的注释。 尽管消费者可能选择显示评论，但它们不被视为文档正文的一部分。 评论可能包括注释文本、评论作者的姓名和缩写、创建日期等。

    **consumer** — 通过包实现者读取包的软件或设备。 消费者通常被设计为仅消费特定物理包格式的包。

    **content type** — 描述存储在部件中的内容。 内容类型定义媒体类型、子类型和可选参数集，如 RFC 2616 中所定义。

    **document category** — Office Open XML 文档的三类之一：文字处理、电子表格和演示文稿，定义如下：

        * 其包关系项包含与主文档部件 ([§11.3.10]) 的关系的文档是字处理类别的文档。
        * 其包关系项包含与工作簿部件 ([§12.3.23]) 的关系的文档是电子表格类别的文档。
        * 其包关系项包含与演示部件 ([§13.3.6]) 的关系的文档是演示类别的文档。

    Office Open XML 文档可以包含一个或多个嵌入式 Office Open XML 包 ([§15.2.11])，每个嵌入式包具有三个文档类别中的任意一个。 然而，这些嵌入包的存在不会改变文档的类别。

    **DrawingML** — 用于指定 Office Open XML 文档中绘图元素的位置和外观的一组约定。

    **extension** — 任何未明确包含在 ECMA-376 中但使用 ECMA-376 描述的可扩展性机制的 XML 元素、XML 属性、关系或部件。

    **id** — 在一些 XML 相关技术中，术语 id 暗示使用 `xsd:ID` 数据类型。 在本国际标准中，该术语用于指代各种不同的识别方案。 请参阅唯一标识符。

    **ODBC** – ISO/IEC 9075-3:2008 “信息技术 - 数据库语言 - SQL - 第 3 部分：调用级接口 (SQL/CLI)” 或基于 SQL/CLI 的数据库连接 API 的实现。 广泛使用的基于 SQL/CLI 的数据库连接 API 的一个示例是开放数据库连接 (ODBC) API。

    **Office Open XML document** — 使用文字处理、电子表格或演示 ML 及其相关 ML 格式化的数据流的再现，如 ECMA-376-1 和 ECMA-376-4 中所述。 此类文档表示为 ECMA-376-2 中描述的包。

    **OLE** – 本文中的 OLE 并不指任何特定技术； 相反，它指的是在文档中嵌入和链接对象的广义抽象。

    **package** — 符合 ECMA-376-2 中定义的开放打包约定规范的 ZIP 存档。
    
    **package, embedded** — 已作为嵌入包关系 ([§15.2.11]) 的目标存储在 Office Open XML 文档中的包

    **PresentationML** — 用于表示类别演示文稿的 Office Open XML 文档的一组约定。
    
    **producer** — 通过包实现者编写包的软件或设备。 生产者通常被设计为根据特定的物理包格式规范来生产包。

    **relationship** — 包中源部件和目标部件之间的连接类型。 关系使部件之间的联系可以直接发现，无需查看部件内容，也无需更改部件本身。 （另请参阅包关系。）

    **relationships part** — 包含关系的 XML 表示的部件。

    **relationship, explicit** — 一种关系，其中使用关系标记的 Id 属性从源部件的 XML 引用资源。

    **relationship, implicit** — 一种不明确的关系。
    
    **SpreadsheetML** — 用于表示电子表格类别的 Office Open XML 文档的一组约定。
    
    **unique identifier** — 在一些 XML 相关技术中，术语“唯一标识符”意味着使用 `xsd:ID` 数据类型。 在本国际标准中，该术语用于指代各种不同的识别方案。 参见 id。
    
    **WordprocessingML** — 用于表示 Wordprocessing 类别的 Office Open XML 文档的一组约定。

=== "英文"

    **Terms and Definitions**

    For the purposes of this document, the following terms and definitions apply. Other terms are defined where they appear in italic typeface, on the left side of a syntax rule, or within subclauses of language-specific grammars ([§17.16] and [§18.17]). Terms explicitly defined in this Part of ECMA-376 are not to be presumed to refer implicitly to similar terms defined elsewhere.

    !!! note info "Note"

        This Part uses OPC-related terms, which are defined in ECMA-376-2.

    **application** — A consumer or producer.

    **behavior** — External appearance or action.

    **behavior, implementation-defined** — Unspecified behavior where each implementation is expected to document that behavior, which would thereby promote predictability and reproducibility within any given implementation. (This term is sometimes called “application-defined behavior”.)
    
    **behavior, locale-specific** — Behavior that depends on local conventions of nationality, culture, and language.
    
    **behavior, unspecified** — Behavior where ECMA-376 makes no recommendations. (This term is sometimes called“application-dependent behavior”.) [Note: To add an extension, an implementer must use the extensibility mechanisms described by ECMA-376 rather than trying to do so by giving meaning to otherwise unspecified behavior. end note]
    
    **byte** — A sequence of 8 bits treated as a unit.
    
    **comment** — A note attached to content in a document. Although a consumer might choose to display comments, they are not considered part of the body of the document. A comment might include the text of the note, the comment author's name and initials, and date of creation, among other things.

    **consumer** — A piece of software or a device that reads packages through a package implementer. A consumer is often designed to consume packages only for a specific physical package format.

    **content type** — Describes the content stored in a part. Content types define a media type, a subtype, and an optional set of parameters, as defined in RFC 2616.

    **document category** — One of the three categories of Office Open XML documents: Wordprocessing, Spreadsheet, and Presentation, defined as follows:
        
        *  A document whose package-relationship item contains a relationship to a Main Document part ([§11.3.10]) is a document of category Wordprocessing.
        * A document whose package-relationship item contains a relationship to a Workbook part ([§12.3.23]) is a document of category Spreadsheet.
        * A document whose package-relationship item contains a relationship to a Presentation part ([§13.3.6]) is a document of category Presentation.

    An Office Open XML document can contain one or more embedded Office Open XML packages ([§15.2.11]) with each embedded package having any of the three document categories. However, the presence of these embedded packages does not change the category of the document.

    **DrawingML** — A set of conventions for specifying the location and appearance of drawing elements in an Office Open XML document.

    **extension** — Any XML element, XML attribute, relationship, or part not explicitly included in ECMA-376, but that uses the extensibility mechanisms described by ECMA-376.

    **id** — In some XML-related technologies, the term id implies use of the xsd:ID data type. In this international standard, this term is used to refer to a variety of different identification schemes. See unique identifier.

    **ODBC** – An implementation of ISO/IEC 9075-3:2008 “Information technology -- Database languages -- SQL – Part 3: Call-Level Interface (SQL/CLI)” or SQL/CLI-based database connectivity API. An example of a broadly used SQL/CLI-based database connectivity API is the Open Database Connectivity (ODBC) API.

    **Office Open XML document** — A rendition of a data stream formatted using the wordprocessing, spreadsheet, or presentation ML and its related MLs as described in ECMA-376-1 and ECMA-376-4. Such a document is represented as a package as described in ECMA-376-2.

    **OLE** – OLE in this context does not refer to any specific technology; instead, it refers to the generalized abstraction of embedding and linking objects within a document.

    **package** — A ZIP archive that conforms to the Open Packaging Conventions specification defined in ECMA-376-2. 
    
    **package, embedded** — A package that has been stored as the target of an Embedded Package relationship ([§15.2.11]) in an Office Open XML document

    **PresentationML** — A set of conventions for representing an Office Open XML document of category Presentation.
    
    **producer** — A piece of software or a device that writes packages through a package implementer. A producer is often designed to produce packages according to a particular physical package format specification.

    **relationship** — The kind of connection between a source part and a target part in a package. Relationships make the connections between parts directly discoverable without looking at the content in the parts, and without altering the parts themselves. (See also Package Relationships.)

    **relationships part** — A part containing an XML representation of relationships.

    **relationship, explicit** — A relationship in which a resource is referenced from a source part’s XML using the Id attribute of a Relationship tag.

    **relationship, implicit** — A relationship that is not explicit. 
    
    **SpreadsheetML** — A set of conventions for representing an Office Open XML document of category Spreadsheet. 
    
    **unique identifier** — In some XML-related technologies, the term unique identifier implies use of the xsd:ID data type. In this international standard, this term is used to refer to a variety of different identification schemes. See id. 
    
    **WordprocessingML** — A set of conventions for representing an Office Open XML document of category Wordprocessing.
