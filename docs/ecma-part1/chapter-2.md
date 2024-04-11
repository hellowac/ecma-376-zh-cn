# 2. 一致性

**Conformance**

## 2.1 文档一致性

=== "中文"

    符合性类别 Office Open XML Strict 的文档应是符合性类别 OPC 的包，如 ECMA-376-2 中所指定，其中以下所有内容均应成立：

    * 该文档遵守 ECMA-376 本部分中指定的所有约束
    * 该文档属于文字处理、电子表格或演示文稿类别，如 [第 4 节] 中所定义
    * 对于[第 11.3 节]、[第 12.3 节]、[第 13.3 节]、[第 14.2 节]或[第 15.2 节]中列出的类型的文档的每个 OPC 部件，以下所有内容均应成立：

        1. 该部件可能包含 ECMA376-3 中指定的标记兼容性命名空间中的标记
        2. 按照 ECMA-376-3 中的规定，MCE 处理器删除任何扩展后，该部分根据严格的 W3C XML 架构（[附录 A]）有效

    ECMA-376 的本部分使用以下进一步术语来引用 Office Open XML Strict 一致性类别的文档：

    * WML 要求，如果文档属于字处理类别
    * SML 要求，如果文档属于电子表格类别
    * PML 要求，如果文档属于演示类别

=== "英文"

    **Document Conformance**

    A document of conformance class Office Open XML Strict shall be a package of conformance class OPC, as specified in ECMA-376-2, for which all the following shall hold:

    * The document obeys all constraints specified in this Part of ECMA-376
    * The document is of category Wordprocessing, Spreadsheet, or Presentation, as defined in [§4]
    * For each OPC Part of the document of the types listed in [§11.3], [§12.3], [§13.3], [§14.2] or [§15.2], all the following shall hold:

       1. The Part may contain markup in the Markup Compatibility namespace as specified in ECMA376-3
       2. After the removal of any extensions by an MCE processor as specified in ECMA-376-3, the part is valid against the strict W3C XML Schema ([Annex A])

    This Part of ECMA-376 uses the following further terms to refer to documents of conformance class Office Open XML Strict:

    * WML Strict, if the document is of category Wordprocessing
    * SML Strict, if the document is of category Spreadsheet
    * PML Strict, if the document is of category Presentation

## 2.2 应用程序一致性

=== "中文"

    应用程序一致性包含语法和语义：

    * 合格消费者不得拒绝至少一种文件一致性类别的任何合格文件。
    * 合格生产者应能够制作至少一个文件一致性类别的合格文件。
    * 符合要求的应用程序应以与 ECMA-376 中给出的语义定义一致的方式处理 Office Open XML 文档中的信息。 应用程序的预期行为不需要该应用程序处理 Office Open XML 文档中的所有信息。 然而，它处理的信息应以与 ECMA-376 中给出的语义定义一致的方式进行处理。

    !!! note info "注意"

        本注释说明了上面的第三个项目符号。 符合要求的应用程序可能具有多种功能。 示例包括查看器、编辑器和后端处理器。 以下说明了第三个项目符号如何应用于每个示例：

        * 如果符合标准的查看器支持给定功能，那么当它使用该功能显示信息时，它会尊重标准中描述的该功能的语义。
        * 如果符合标准的编辑器支持给定的功能，那么当它向用户提供使用该功能操作信息的界面时，它会尊重标准中描述的该功能的语义。
        * 如果符合标准的后端处理器支持给定的功能，那么当该处理器转换或组装涉及该功能的信息时，该处理器将遵循标准中描述的该功能的语义。

    ECMA-376 的这一部分定义了以下应用程序一致性类别：

    * WML 要求, 如果应用程序是符合性应用程序，并且是具有 WML Strict 一致性类别的文档的消费者或生产者。
    * SML 要求, 如果应用程序是符合性应用程序，并且是具有 SML Strict 一致性类别的文档的消费者或生产者。
    * PML 要求, 如果应用程序是符合性应用程序，并且是具有 PML Strict 一致性类别的文档的消费者或生产者。

=== "英文"

    **Application Conformance**

    Application conformance incorporates both syntax and semantics:

    * A conforming consumer shall not reject any conforming documents of at least one document conformance class.
    * A conforming producer shall be able to produce conforming documents of at least one document conformance class.
    * A conforming application shall treat the information in Office Open XML documents in a manner consistent with the semantic definitions given in ECMA-376. An application's intended behavior need not require that application to process all of the information in an Office Open XML document. However, the information that it does process shall be processed in a manner that is consistent with the semantic definitions given in ECMA-376.

    !!! note info "Note"

        This note illustrates the third bullet above. Conforming applications might serve various functions. Examples include a viewer, an editor, and a back-end processor. Here is an illustration of how the third bullet applies to each of those examples:

        * If a conforming viewer supports a given feature, then when it displays information using that feature, it respects the semantics of that feature as described in the Standard.
        * If a conforming editor supports a given feature, then when it provides its user with an interface for manipulating information using that feature, it respects the semantics of that feature as described in the Standard.
        * If a conforming back-end processor supports a given feature, then when that processor transforms or assembles information involving that feature, that processor respects the semantics of that feature as described in the Standard.

    This Part of ECMA-376 defines the following application conformance classes:

    * WML Strict, if the application is a conforming application that is a consumer or producer of documents having conformance class WML Strict.
    * SML Strict, if the application is a conforming application that is a consumer or producer of documents having conformance class SML Strict.
    * PML Strict, if the application is a conforming application that is a consumer or producer of documents having conformance class PML Strict.


    Conformance can also involve the use of application descriptions; see [§2.3] for details

## 2.3 应用程序描述

=== "中文"

    可以将应用程序定义为符合特定一致性类别中的零个或多个应用程序描述。

    ECMA-376 中定义的应用程序描述是：

    * Base
    * Full

    !!! note info "注意"

        这些应用程序描述不应被视为限制应用程序提供商创建创新应用程序的能力。 它们旨在作为标记应用程序的机制，而不是限制其功能。 目的是促进共享相同一致性类别的不同应用程序之间的互操作性。 应用程序描述与这些应用程序生成的文档的一致性是正交的。 例如，用于自动翻译文档的工具可能具有 “Base” 的应用程序描述，但仍会生成完全一致的文档。
    
    应用程序描述是根据应用程序对特定功能的语义理解来确定的。 语义理解的解释是应用程序应以与 ECMA-376 中给出的语义定义一致的方式处理 Office Open XML 文档中的信息。

    每个应用程序描述都由 URI 标识。

    应用程序描述在以下子条款中定义。

=== "英文"

    **Application Descriptions**

    An application can be defined as conforming to zero or more application descriptions in a particular conformance class.

    The application descriptions defined within ECMA-376 are:

    * Base
    * Full

    !!! note info "Note"

        These application descriptions should not be taken as limiting the ability of an application provider to create innovative applications. They are intended as a mechanism for labelling applications rather than for restricting their capabilities. The intention is to promote interoperability between different applications that share the same conformance class. Application descriptions are orthogonal to the conformance of the documents produced by those applications. For example, a tool used for automated translation of documents might have an application description of “Base” but will still produce fully conformant documents.

    The application descriptions are determined in terms of an application’s semantic understanding of particular features. Semantic understanding is to be interpreted in that an application shall treat the information in Office Open XML documents in a manner consistent with the semantic definitions given in ECMA-376.

    Each application description is identified by a URI.

    The application descriptions are defined in the following subclauses.

### 2.3.1 基础应用描述

=== "中文"

    URI 描述符: `http://purl.oclc.org/ooxml/descriptions/base`

    符合此描述的应用程序对其一致性类别中的至少一个功能具有语义理解。

    !!! note info "注意"

        此外，强烈建议包含用户界面的应用程序支持适合该用户界面的所有辅助功能。

=== "英文"

    **Base Application Description**

    Description URI: `http://purl.oclc.org/ooxml/descriptions/base`

    An application conforming to this description has a semantic understanding of at least one feature within its conformance class.

    !!! note info "Note"

        In addition, applications that include a user interface are strongly recommended to support all accessibility features appropriate to that user interface.

### 2.3.2 完整的应用描述

=== "中文"

    URI 描述符: `http://purl.oclc.org/ooxml/descriptions/full`

    符合此描述的应用程序对其一致性类别中的每个功能都有语义理解。

=== "英文"

    **Full Application Description**

    Description URI: `http://purl.oclc.org/ooxml/descriptions/base`

    An application conforming to this description has a semantic understanding of every feature within its conformance class.

### 2.3.3 附加应用描述

=== "中文"

    预计将在 ECMA376 的维护过程中定义其他应用程序描述。 还期望第三方可以定义自己的应用程序描述； 例如，为他们的采购决策提供信息，或处理可访问性等领域。

    !!! note info "注意"

        可能的应用程序描述将是文字处理应用程序的 “标准” 应用程序描述。 这可以通过综合使用常见文字处理应用程序（例如 Word 2000、OpenOffice 2、WordPerfect 和 iWork Pages）中可用的功能来创建。 此外，它还可以定义格式，例如需要支持的特定图像和视频格式，以符合描述。 可以为电子表格应用程序和演示应用程序创建类似的描述。 这样的描述将促进实现 OOXML 的应用程序之间的互操作性。 它还将促进实现 OOXML 的应用程序与实现其他文档格式（例如 ISO/IEC 26300）的应用程序之间的互操作性。

    应用程序描述不需要是彼此严格的子集。 一个应用程序可以同时符合多个应用程序描述。

    任何此类新创建的描述均应枚举与其一致所需的功能。 这样的描述应该提供机器可处理的模式，最好使用 ISO/IEC 19757 等标准。

    !!! note info "注意"

        如果符合描述的应用程序是文档使用者，则它应该能够使用遵循与描述相关联的这种模式的任何文档。 如果应用程序是文档生成器，则该应用程序生成的任何文档都应遵循描述的模式。

    任何此类描述都应使用 URI 进行标识，其方式与 ECMA-376 中用于应用程序描述的名称类似。

    !!! note info "注意"

        为了方便描述的用户，建议描述的创建者应在与描述 URI 相对应的 URL 上提供该描述的人类或机器可读形式。

=== "英文"

    **Additional Application Descriptions**

    It is expected that additional application descriptions will be defined within the maintenance process for ECMA376. It is also expected that third parties might define their own application descriptions; for example to inform their procurement decisions, or to deal with domains such as accessibility. 

    !!! note info "Note"

        A possible application description would be a “standard” application description for a wordprocessing application. This could be created by taking the intersection of the features available in common wordprocessing applications such as Word 2000, OpenOffice 2, WordPerfect, and iWork Pages. In addition, it could define formats such as specific image and video formats required to be supported to conform to the description. Similar descriptions could be created for spreadsheet applications and presentation applications. Such a description would promote interoperability between applications implementing OOXML. It would also promote interoperability between applications implementing OOXML and applications implementing other document formats such as ISO/IEC 26300.

    Application descriptions are not required to be strict subsets of each other. An application can simultaneously conform to multiple application descriptions.

    Any such newly created description shall enumerate the features that are required for conformance to it. Such a description should provide a machine-processable schema, preferably using a standard such as ISO/IEC 19757.

    !!! note info "Note"

         If the application conforming to a description is a document consumer, it should be able to consume any document that respects such a schema associated with the description. If the application is a document producer, any document produced by that application should respect the schema of the description.

    Any such description should be identified using a URI, in a similar manner to the names used for application descriptions within ECMA-376. 

    !!! note info "Note"

        For the convenience of users of the description, it is recommended that creators of a description should make a human- or machine-readable form of that description available at a URL corresponding to the description URI. 

### 2.3.4 文档中应用程序描述的表示

=== "中文"

    应用程序描述与应用程序相关，而不是与文档一致性相关。 因此，不存在用于在文档中表示应用程序描述的规范机制。

    !!! note info "注意"

        建议希望在文档中表示应用程序描述的实施者使用 Office Open XML 的标准元数据机制。

=== "英文"

    **Representation of Application Descriptions within Documents**

    An application description is related to applications, rather than to document conformance. Therefore, there is no normative mechanism for representing an application description within a document.

    !!! note info "Note"

        It is recommended that implementers wishing to represent an application description within a document use the standard metadata mechanism for Office Open XML.

## 2.4 互操作性指南

=== "中文"

    以下互操作性指南包含语义。

    为了使指南有意义，软件应用程序应附有描述其支持的 ECMA-376 子集的文档。 文档应突出显示在没有该文档的情况下可能违反文档 XML 元素语义的任何行为。 申请和文件应同时满足以下条件。

    1. 应用程序不需要对 ECMA-376 中定义的所有 XML 元素执行操作。 但是，如果它确实在给定 XML 元素上实现了操作，则该操作应该使用与 ECMA-376 一致的 XML 元素语义。
    2. 如果应用程序移动、添加、修改或删除 XML 元素实例，从而改变文档语义，则应在其文档中声明该行为。

    以下场景说明了这些准则。

    * 将预设形状几何“矩形(rect)”解释为椭圆(ellipse)的演示文稿编辑器不会遵守第一条准则，因为它实现了“矩形(rect)”，但语义不正确。
    * 即使最初使用的单元格包含公式，也仅保存计算值的批处理电子表格处理器可能满足第一个条件，但不会遵守第二个条件，因为公式的可编辑性是单元格语义的一部分。 要遵守第二条准则，其文档应描述行为。
    * 即使 ECMA-376 不建议这种行为，读取字处理文档并在保存之前以“标题”样式反转每个段落中文本字符顺序的批处理工具也可能符合要求。 该工具的行为是将标题“Office Open XML” 转换为 “LMX nepO eciffO”。 其文件应声明其对此类段落的影响。

    [第 2.1 节] 中的规范性要求意味着符合要求的生产者不得编写未转义的非 XML 字符。 作为实现指南，符合标准的生产者也不应该编写转义的非 XML 字符。 这样做会损害与现有基于 XML 的标准（例如 SOAP 和 RDF）的互操作性。 例如，实施者可以拒绝创建包含此类字符的文档，或者警告用户包含此类字符会损害其文档的可重用性。

=== "英文"

    **Interoperability Guidelines**

    The following interoperability guidelines incorporate semantics.

    For the guidelines to be meaningful, a software application should be accompanied by documentation that describes what subset of ECMA-376 it supports. The documentation should highlight any behaviors that would, without that documentation, appear to violate the semantics of document XML elements. Together, the application and documentation should satisfy the following conditions.

    1. The application need not implement operations on all XML elements defined in ECMA-376. However, if it does implement an operation on a given XML element, then that operation should use semantics for that XML element that are consistent with ECMA-376.
    2. If the application moves, adds, modifies, or removes XML element instances with the effect of altering document semantics, it should declare the behavior in its documentation.

    The following scenarios illustrate these guidelines.

    * A presentation editor that interprets the preset shape geometry “rect” as an ellipse does not observe the first guideline because it implements “rect” but with incorrect semantics.
    * A batch spreadsheet processor that saves only computed values even if the originally consumed cells contain formulas, might satisfy the first condition, but does not observe the second because the editability of the formulas is part of the cells’ semantics. To observe the second guideline, its documentation should describe the behavior.
    * A batch tool that reads a word-processing document and reverses the order of text characters in every paragraph with “Title” style before saving it can be conforming even though ECMA-376 does not recommend this behavior. This tool’s behavior would be to transform the title “Office Open XML” into “LMX nepO eciffO”. Its documentation should declare its effect on such paragraphs.


    The normative requirements in [§2.1] imply that a conforming producer shall not write unescaped non-XML characters. As an implementation guideline, a conforming producer additionally should not write escaped nonXML characters. Doing so damages interoperability with existing XML-based standards such as SOAP and RDF. For example, implementers could either refuse to create documents including such characters, or warn users that including such characters compromises the re-usability of their documents. 
