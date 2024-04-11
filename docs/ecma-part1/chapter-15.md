# 15. 共享

=== "中文"

    **Shared**

    本节中定义的关系项和部件由 WordprocessingML (§11)、SpreadsheetML (§12) 和 PresentationML (§13) 环境中的一个或多个使用。

=== "英文"

    The relationship items and parts defined in this clause are used by one or more of WordprocessingML (§11), SpreadsheetML (§12), and PresentationML (§13) environments. 

## 15.1 共享术语词汇表

=== "中文"

    - **array** — 数学元素（“e”）数组垂直堆叠在单个数学区域中。
    - **build down** — 将数学文本从实现的专业形式转换为实现的构建形式的过程。
    - **build up** — 将数学文本从实现的构建形式转换为实现的专业形式的过程。
    - **built-down form** — 一种特定于实现的线性格式，除了另一种纯文本线性格式（例如 TeX）或 Unicode 技术说明 28 中定义的线性格式之外，可能包含也可能不包含附加的丰富格式。
    - **built-up form** — 参见专业形式。
    - **control** — Office Open XML 文档中的活动内容区域。
    - **display equation** — 处于显示模式的方程，因此是显示数学区域的一部分。 （显示方程的替代名称为：“显示表达式(display expression)”、“显示公式(display formula)”和“显示数学(display math)”。）
    - **display mode** — 当数学文本（即一个或多个 oMath 块中的文本）包含在显示数学区域（即 oMathPara 块）中时，oMath 块中表示的数学文本处于显示模式。
    - **equation array** — 方程组。 参见数组。
    - **inline equation** — 位于内联数学区域中的方程。 （内联方程的替代名称是：“内联表达式(inline expression)”、“内联公式(inline formula)”和简单的“内联数学(inline math)”。）
    - **instance of mathematical text** — 由单个 oMath 块和该 oMath 块内的 OMML 元素表示的数学文本的单个连续组合。
    - **linear format** — 数学文本的特定于实现的纯文本一维表示。
    - **math accent** — ECMA-376 指定可接受用作重音字符的字符。
    - **math alphanumerics** — 具有特定数学样式的字符，如 Unicode 标准 5.0 中所定义。
    - **math paragraph** — 处于显示模式的一个或多个 oMath 元素（数学文本实例）。
    - **math zone** — 一个孤立的文本区域，在该区域内使用数学文本，在该区域之外不使用数学文本。
    - **mathematical text** — 旨在通过 OMML 传达数学含义的任何文本。
    - **n-ary operator** — 展开时涉及 n 项的运算符。 例如，以下示例使用 Unicode (ISO 10646) 求和符号 (U+2211)，其正式名称为“N-ARY SUMMATION”。
    
    $$
    \sum_{j=1}^{n}a_j \equiv a_1 + a_2 +a_3\cdots + a_n
    $$

    - **oMath container** — oMath 模块是显示数学区域的一部分，但其本身并不是数学区域。
    - **OMML** — Office 数学标记语言，ECMA-376 的共享 ML。
    - **professional form** — 特定于实现的数学文本的二维表示。 （也称为“组合形式(built-up form)”。）

=== "英文"

    **Glossary of Shared Terms**

    - **array** — An array of mathematical elements (“e”) stacked vertically in a single math zone.
    - **build down** — The process of converting mathematical text from an implementation’s professional form to an implementation’s built-down form.
    - **build up** — The process of converting mathematical text from an implementation’s built-down form to animplementation’s professional form.
    - **built-down form** — An implementation-specific linear format that may or may not include additional rich formatting in addition to another plain-text linear format (such as TeX) or the linear format defined in Unicode Technical Note 28.
    - **built-up form** — See professional form.
    - **control** — A region of active content within an Office Open XML document.
    - **display equation** — An equation that is in display mode, and thus is part of a display math zone. (Alternative names for display equation are: “display expression”, “display formula”, and “display math”.)
    - **display mode** — When mathematical text (i.e., text in one or more oMath blocks) is contained in a display math zone (i.e., an oMathPara block), the mathematical text represented in the oMath block(s) is in display mode.
    - **equation array** — An array of equations. See array.
    - **inline equation** — An equation that is in an inline math zone. (Alternative names for inline equation are: “inline expression”, “inline formula”, and simply “inline math”.)
    - **instance of mathematical text** — A single continuous combination of mathematical text represented by a single oMath block and the OMML elements within that oMath block.
    - **linear format** — An implementation-specific plain-text 1-dimensional representation of mathematical text.
    - **math accent** — A character that is specified as acceptable for use as an accent character by ECMA-376.
    - **math alphanumerics** — Characters with specific math styles, as defined in the Unicode Standard 5.0.
    - **math paragraph** — One or more oMath elements (instances of mathematical text) that are in display mode.
    - **math zone** — An isolated region of text within which mathematical text is used and outside of which mathematical text is not used.
    - **mathematical text** — Any text meant to convey mathematical meaning through OMML. 
    - **n-ary operator** — An operator that involves n terms when expanded. For instance, the following example uses the Unicode (ISO 10646) summation sign (U+2211) which has the official name “N-ARY SUMMATION”.
    
    $$
    \sum_{j=1}^{n}a_j \equiv a_1 + a_2 +a_3\cdots + a_n
    $$

    - **oMath container** — An oMath block that is part of a display math zone but is not itself a math zone.
    - **OMML** — Office Math Markup Language, a Shared ML of ECMA-376.
    - **professional form** — Implementation-specific 2-D representation of mathematical text. (Also referred to as "built-up form".)

## 15.2 部件概览

=== "中文"

    **部件概览**

    从属于该子章节的详细描述了每种共享部件类型。

    !!! info "Note"

        为方便起见，下表总结了这些子章节(约定)的信息：

        <table>
            <thead>
                <tr>
                    <th> **Part** </th>
                    <th> **Relationship Target of** </th>
                    <th> **Root Element** </th>
                    <th> **Ref.** </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td> Additional Characteristics </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Characteristics </td>
                    <td> [§15.2.1] </td>
                </tr>
                <tr>
                    <td> Audio </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.2] </td>
                </tr>
                <tr>
                    <td> Bibliography </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Sources </td>
                    <td> [§15.2.3] </td>
                </tr>
                <tr>
                    <td> Custom XML Data Storage </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.4] </td>
                </tr>
                <tr>
                    <td> Custom XML Data Storage Properties </td>
                    <td> 
                        Custom XML Data Storage
                    </td>
                    <td> datastoreItem </td>
                    <td> [§15.2.6] </td>
                </tr>
                <tr>
                    <td> Digital Signature Origin </td>
                    <td> 
                        WordprocessingML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML Package parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.7] </td>
                </tr>
                <tr>
                    <td> Digital Signature XML Signature</td>
                    <td> 
                        Digital Signature Origin
                    </td>
                    <td> Signature </td>
                    <td> [§15.2.8] </td>
                </tr>
                <tr>
                    <td> Embedded Control Persistence</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.9] </td>
                </tr>
                <tr>
                    <td> Embedded Object</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.10] </td>
                </tr>
                <tr>
                    <td> Embedded Package</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.11] </td>
                </tr>
                <tr>
                    <td> File Properties, Extended</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> Properties </td>
                    <td> [§15.2.12.3] </td>
                </tr>
                <tr>
                    <td> File Properties, Core</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> coreProperties </td>
                    <td> [§15.2.12.1] </td>
                </tr>
                <tr>
                    <td> File Properties, Custom</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> properties </td>
                    <td> [§15.2.12.2] </td>
                </tr>
                <tr>
                    <td> Font </td>
                    <td> 
                        WordprocessingML Font <br/>  
                        Table part, PresentationML  <br/>  
                        Presentation part
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.13] </td>
                </tr>
                <tr>
                    <td> Image </td>
                    <td> 
                        Numerous PresentationML,  <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.14] </td>
                </tr>
                <tr>
                    <td> Printer Settings </td>
                    <td> 
                        SpreadsheetML Chartsheet,  <br/>  
                        Dialogsheet, Worksheet parts,  <br/>  
                        WordprocessingML Main  <br/>  
                        Document or Glossary  <br/>  
                        Document parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.15] </td>
                </tr>
                <tr>
                    <td> Thumbnail </td>
                    <td> 
                        WordprocessingML,  <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML package 
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.16] </td>
                </tr>
                <tr>
                    <td> Video part </td>
                    <td> 
                        Numerous PresentationML  <br/>  
                        and WordprocessingML parts
                    </td>
                    <td> 不适用 </td>
                    <td> [§15.2.17] </td>
                </tr>
            </tbody>
        </table>

=== "英文"

    **Part Summary**

    The subclauses subordinate to this one describe in detail each of the shared part types.

    !!! info "Note"

        For convenience, information from those subclauses is summarized in the following table:

        <table>
            <thead>
                <tr>
                    <th> **Part** </th>
                    <th> **Relationship Target of** </th>
                    <th> **Root Element** </th>
                    <th> **Ref.** </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td> Additional Characteristics </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Characteristics </td>
                    <td> [§15.2.1] </td>
                </tr>
                <tr>
                    <td> Audio </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.2] </td>
                </tr>
                <tr>
                    <td> Bibliography </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Sources </td>
                    <td> [§15.2.3] </td>
                </tr>
                <tr>
                    <td> Custom XML Data Storage </td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.4] </td>
                </tr>
                <tr>
                    <td> Custom XML Data Storage Properties </td>
                    <td> 
                        Custom XML Data Storage
                    </td>
                    <td> datastoreItem </td>
                    <td> [§15.2.6] </td>
                </tr>
                <tr>
                    <td> Digital Signature Origin </td>
                    <td> 
                        WordprocessingML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML Package parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.7] </td>
                </tr>
                <tr>
                    <td> Digital Signature XML Signature</td>
                    <td> 
                        Digital Signature Origin
                    </td>
                    <td> Signature </td>
                    <td> [§15.2.8] </td>
                </tr>
                <tr>
                    <td> Embedded Control Persistence</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.9] </td>
                </tr>
                <tr>
                    <td> Embedded Object</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.10] </td>
                </tr>
                <tr>
                    <td> Embedded Package</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.11] </td>
                </tr>
                <tr>
                    <td> File Properties, Extended</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> Properties </td>
                    <td> [§15.2.12.3] </td>
                </tr>
                <tr>
                    <td> File Properties, Core</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> coreProperties </td>
                    <td> [§15.2.12.1] </td>
                </tr>
                <tr>
                    <td> File Properties, Custom</td>
                    <td> 
                        Numerous PresentationML, <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML parts
                    </td>
                    <td> properties </td>
                    <td> [§15.2.12.2] </td>
                </tr>
                <tr>
                    <td> Font </td>
                    <td> 
                        WordprocessingML Font <br/>  
                        Table part, PresentationML  <br/>  
                        Presentation part
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.13] </td>
                </tr>
                <tr>
                    <td> Image </td>
                    <td> 
                        Numerous PresentationML,  <br/>  
                        SpreadsheetML, and  <br/>  
                        WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.14] </td>
                </tr>
                <tr>
                    <td> Printer Settings </td>
                    <td> 
                        SpreadsheetML Chartsheet,  <br/>  
                        Dialogsheet, Worksheet parts,  <br/>  
                        WordprocessingML Main  <br/>  
                        Document or Glossary  <br/>  
                        Document parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.15] </td>
                </tr>
                <tr>
                    <td> Thumbnail </td>
                    <td> 
                        WordprocessingML,  <br/>  
                        SpreadsheetML, or  <br/>  
                        PresentationML package 
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.16] </td>
                </tr>
                <tr>
                    <td> Video part </td>
                    <td> 
                        Numerous PresentationML  <br/>  
                        and WordprocessingML parts
                    </td>
                    <td> Not applicable </td>
                    <td> [§15.2.17] </td>
                </tr>
            </tbody>
        </table>

### 15.2.1 附加特性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://schemas.openxmlformats.org/officeDocument/2006/additionalCharacteristics</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://schemas.openxmlformats.org/officeDocument/2006/relationships/customXml</td>
        </tr>
    </table>

    当无法使用 ECMA-376 定义的元素指定这些特征时，此部件类型的实例包含有关生成文档的生产者的附加特征的信息。

    !!! info "Note"

        这部分内容纯粹是提供信息，对文档的后续使用不构成任何要求。 然而，它们的目的是提供有关文档制作者能力的详细信息，从而允许在后续处理过程中考虑这些能力。 例如，支持 100,000 列电子表格的应用程序可能会选择将其输出限制为 10,000 列，当呈现的文档的特征表明该文档是由具有该限制的应用程序生成时，为了防止引入不支持的内容。 原始制作者（因为将来可能会使用该应用程序来处理此文档）。 此标记由 ECMA-376 提供，以便提供存储此信息的可互操作方式。

    包允许包含**零个或一个**附加特征部件，并且每个此类部件应是 WordprocessingML 包中主文档 ([§11.3.10]) 部件的隐式关系的目标； SpreadsheetML 包中的工作簿 ([§12.3.23]) 部件； 或讲义母版 ([§13.3.3])、笔记母版 ([§13.3.4])、笔记幻灯片 ([§13.3.5])、演示文稿 ([§13.3.6])、幻灯片 ([§13.3.8])、幻灯片布局 ([§13.3.9])，或 PresentationML 包中的 Slide Master ([§13.3.10]) 部件。

    !!! info "Example"

        以下主文档部件关系项包含与附加特征部件的关系，该附加特征部件存储在 ZIP 项 `../customXML/item2.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlData" Target="../customXML/item2.xml"/>
        </Relationships>
        ```
    
    附加特征部件应位于包含关系部件的包内（从语法上表达，关系元素的 `TargetMode` 属性应为 `Internal`）。

    附加特性部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * 自定义 XML 数据存储属性 ([§15.2.6])
    
    附加特性部件不得与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Additional Characteristics Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://schemas.openxmlformats.org/officeDocument/2006/additionalCharacteristics</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://schemas.openxmlformats.org/officeDocument/2006/relationships/customXml</td>
        </tr>
    </table>

    An instance of this part type contains information about additional characteristics of the producer that generated the document, when those characteristics cannot be specified using elements defined by ECMA-376.

    !!! info "Note"

        The contents of this part are purely informational, and do not place any requirements on subsequent consumption of the document. They are, however, intended to provide detailed information about the capabilities of the document’s producer, allowing those capabilities to be factored in during subsequent processing. For example, an application which supports 100,000 spreadsheet columns might choose to limit its output to 10,000 columns when presented with a document whose characteristics indicate that it was produced by an application with that limitation, in order prevent the introduction of content which is unsupported by the original producer (as that application might be used in the future to process this document). This markup is provided by ECMA-376 in order to provide an interoperable way of storing this information. 

    A package is permitted to contain zero or one Additional Characteristics parts, and each such part shall be the target of an implicit relationship from a Main Document (§11.3.10) part in a WordprocessingML package; a Workbook (§12.3.23) part in a SpreadsheetML package; or a Handout Master (§13.3.3) , Notes Master (§13.3.4), Notes Slide (§13.3.5), Presentation (§13.3.6), Slide (§13.3.8), Slide Layout (§13.3.9), or Slide Master (§13.3.10) part in a PresentationML package.

    !!! info "Example"

        The following Main Document part-relationship item contains a relationship to an Additional Characteristics part, which is stored in the ZIP item ../customXML/item2.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlData" Target="../customXML/item2.xml"/>
        </Relationships>
        ```
    
    An Additional Characteristics part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    An Additional Characteristics part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Custom XML Data Storage Properties (§15.2.6)
    
    An Additional Characteristics part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 15.2.2 音频部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>任何支持的音频类型。</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>不适用</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/audio</td>
        </tr>
    </table>

    Content Type: 

    !!! info "Note， 关于内容类型"

        一些示例内容类型是:

        - audio/aiff http://developer.apple.com/documentation/QuickTime/INMAC/SOUND/imsoundmgr.30.htm
        - audio/midi http://www.midi.org/about-midi/specinfo.shtml
        - audio/ogg http://xiph.org/vorbis/doc/Vorbis_I_spec.html
        - audio/mpeg ISO/IEC 11172-3

    此部件类型的实例应包含一个音频文件。

    允许 PresentationML 包包含零个或多个音频部件，每个部件都应是讲义母版（[§13.3.3]）、笔记幻灯片（[§13.3.5]）、笔记母版（[§13.3.4]）中关系的目标、幻灯片 ([§13.3.8])、幻灯片布局 ([§13.3.9]) 或幻灯片母版 ([§13.3.10]) 部件的关系项。
    
    !!! info "Example"
    
        以下幻灯片部件关系项包含与声音部件的关系，该部件存储为文件 `E:\Beethoven's Symphony No. 9.wma`：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/audio/x-ms-wma"
                Target="file:///E:/Beethoven's%20Symphony%20No.%209.wma"
                TargetMode="External"/>
        </Relationships>
        ```

    音频部件可以位于包含关系部件的包的内部或外部（从语法上表达，关系元素的 TargetMode 属性可以是Internal或External）。
    
    音频部件不存储为 XML； 相反，它涉及一个关系目标，即音频剪辑文件。
    
    音频部件不应与 ECMA-376 定义的其他部件有隐式或显式的关系。
    
    想要互操作性的生产者应该使用以下标准格式：
    
    * audio/mpeg ISO/IEC 11172-3

=== "英文"

    **Audio Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported audio type. </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/audio</td>
        </tr>
    </table>

    !!! info "Note， about content type:"

        Some example content types are:

        - audio/aiff http://developer.apple.com/documentation/QuickTime/INMAC/SOUND/imsoundmgr.30.htm
        - audio/midi http://www.midi.org/about-midi/specinfo.shtml
        - audio/ogg http://xiph.org/vorbis/doc/Vorbis_I_spec.html
        - audio/mpeg ISO/IEC 11172-3

    An instance of this part type contains an audio file. 

    A PresentationML package is permitted to contain zero or more Sound parts, each of which shall be the target of a relationship in a Handout Master (§13.3.3), Notes Slide (§13.3.5), Notes Master (§13.3.4), Slide (§13.3.8), Slide Layout (§13.3.9), or Slide Master (§13.3.10) part-relationship item. 
    
    !!! info "Example"
    
    
        The following Slide partrelationship item contains a relationship to a Sound part, which is stored as the file E:\Beethoven's Symphony No. 9.wma:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/audio/x-ms-wma"
                Target="file:///E:/Beethoven's%20Symphony%20No.%209.wma"
                TargetMode="External"/>
        </Relationships>
        ```

    An Audio part can be located within or external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element can be Internal or External).
    
    An Audio part is not stored as XML; instead, it involves a relationship target that is an audio clip.
    
    An Audio part shall not have implicit or explicit relationships to other parts defined by ECMA-376.
    
    A producer that wants interoperability should use the following standard format:
    
    * audio/mpeg ISO/IEC 11172-3

### 15.2.3 参考文献部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/bibliography</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/customXml</td>
        </tr>
    </table>

    此部件类型的实例包含当前包的书目数据。
    
    一个包允许包含零个或一个参考书目部件，并且每个此类部件应是 WordprocessingML 包中主文档 ([§11.3.10]) 部件中隐式关系的目标； SpreadsheetML 包中的工作簿 ([§12.3.23]) 部件； 或讲义母版 ([§13.3.3])、笔记母版 ([§13.3.4])、笔记幻灯片 ([§13.3.5])、幻灯片 ([§13.3.8])、幻灯片布局 ([§ 13.3.9])，或PresentationML包中的幻灯片母版（[§13.3.10]）部件。
    
    !!! info "Example"
    
    
        以下主文档部件关系项包含与参考书目部件的关系，该部件存储在 ZIP 项 ‵./customXML/bib1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXml" Target="../customXML/bib1.xml"/>
        </Relationships>
        ```

    参考书目部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为Internal）。

    参考书目部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * 自定义 XML 数据存储属性 ([§15.2.6])
    
    参考书目部件不应与 ECMA-376 定义的任何其他部件有隐式或显式的关系。

=== "英文"

    **Bibliography Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/bibliography</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/customXml</td>
        </tr>
    </table>

    An instance of this part type contains bibliographic data for the current package.
    
    A package is permitted to contain zero or one Bibliography part, and each such part shall be the target of an implicit relationship in a Main Document ([§11.3.10]) part in a WordprocessingML package; a Workbook ([§12.3.23]) part in a SpreadsheetML package; or a Handout Master ([§13.3.3]) , Notes Master ([§13.3.4]), Notes Slide ([§13.3.5]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part in a PresentationML package.
    
    !!! info "Example"
    
    
        The following Main Document part-relationship item contains a relationship to a Bibliography part, which is stored in the ZIP item `../customXML/bib1.xml`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXml" Target="../customXML/bib1.xml"/>
        </Relationships>
        ```

    A Bibliography part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Bibliography part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Custom XML Data Storage Properties (§15.2.6)
    
    A Bibliography part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 15.2.4 内容部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                Any supported XML content. <br/> <br/>
                Note: 一些示例内容类型是:<br/> <br/>
                - image/svg+xml: http://www.w3.org/TR/SVG11/<br/> <br/>
                - application/smil: http://www.w3.org/TR/REC-smil/<br/> <br/>
                - text/xml: http://www.w3.org/TR/MathML2/<br/> <br/>
                如果特定 XML 格式不存在显式 MIME 类型，则应使用 text/xml。 读取 text/xml 值的消费者应通过该部件内容的根命名空间来确定内容。
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>
                多种多样，由所使用的内容类型定义。<br/> <br/>
                例如: <br/> <br/>
                MathML 的根命名空间为 `http://www.w3.org/1998/Math/MathML`。
            </td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customXml`</td>
        </tr>
    </table>

    此部件类型的实例可以包含 ECMA-376 未定义的格式的 XML 标记。 包允许包含零个或多个内容部件，并且每个此类部件应成为
    
    - 注释 ([§11.3.2])、
    - 尾注 ([§11.3.4])、
    - 页脚 ([§11.3.6])、
    - 脚注（[§11.3.7]）、
    - 术语表文档（[§11.3.8]）、
    - 标题([§11.3.9]), 或
    - WordprocessingML 包中主文档（[§11.3.10]）部件、
    - SpreadsheetML 包中的绘图 ([§12.3.8]) 部件； 或
    - 讲义母版 ([§13.3.3])、
    - 笔记幻灯片 ([§13.3.5])、
    - 笔记母版 ([§13.3.4])、
    - 幻灯片 ([§13.3.8])、
    - 幻灯片布局([§ 13.3.9])，或
    - PresentationML包中的幻灯片母版（[§13.3.10]）
    
    等等这些部件的显式关系的目标

    !!! info "Example"

        以下主文档部件关系项包含与包含 SVG 标记的内容部件的关系，该内容存储在 ZIP 项 `svg1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXml" Target="../customXML/svg1.xml"/>
        </Relationships>
        ```
    
    内容部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal）。
    
    内容部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。
    
    如果想要互操作性的生产者支持方程式，则应使用以下标准格式之一：
    
    * Office Open XML Math ([§22.1])
    * W3C MathML 2.0
    
    如果想要互操作性的生产者支持墨迹注释(ink annotations)，则应按照以下参考标准格式在此元素中使用墨迹注释(ink annotations)：

    * InkML http://www.w3.org/TR/inkregs

=== "英文"

    **Content Part**

    Content Type: Any supported XML content.

    !!! info "Note"

        Some example content types are

        - image/svg+xml http://www.w3.org/TR/SVG11/
        - application/smil http://www.w3.org/TR/REC-smil/
        - text/xml http://www.w3.org/TR/MathML2/

    If no explicit MIME type exists for a specific XML format, text/xml shall be used. Consumers who read a value of text/xml should determine the contents by the root namespace of the contents of the part.
    
    Root Namespace: Various, as defined by the content type used.

    !!! info "Example"

        MathML has a root namespace of http://www.w3.org/1998/Math/MathML. 
    
    Source Relationship: http://purl.oclc.org/ooxml/officeDocument/relationships/customXml

    An instance of this part type can contain XML markup of a format not defined by ECMA-376. A package is permitted to contain zero or more Content parts, and each such part shall be the target of an explicit relationship from a Comments ([§11.3.2]), Endnotes ([§11.3.4]), Footer ([§11.3.6]), Footnotes ([§11.3.7]), Glossary Document ([§11.3.8]), Header ([§11.3.9]), or Main Document ([§11.3.10]) part in a WordprocessingML package; a Drawings ([§12.3.8]) part in a SpreadsheetML package; or a Handout Master ([§13.3.3]), Notes Slide ([§13.3.5]), Notes Master ([§13.3.4]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or a Slide Master ([§13.3.10]) part in a PresentationML package.

    !!! info "Example"

        The following Main Document part-relationship item contains a relationship to a Content part containing SVG markup, which is stored in the ZIP item svg1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXml" Target="../customXML/svg1.xml"/>
        </Relationships>
        ```
    
    A Content part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Content part shall not have implicit or explicit relationships to any other part defined by ECMA-376.
    
    If a producer that wants interoperability supports equations, it should use one of the following standard formats:
    
    * Office Open XML Math ([§22.1])
    * W3C MathML 2.0
    
    If a producer that wants interoperability supports ink annotations, it should use an ink annotation in this element in the following reference standard format:

    * InkML http://www.w3.org/TR/inkregs

### 15.2.5 自定义XML数据存储部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>any XML allowed</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customXml`</td>
        </tr>
    </table>

    该部件类型的实例可以包含任意 XML。 因此，此部件的实例可用于通过此包往返任意自定义 XML 数据。
    
    包允许包含一个或多个自定义 XML 数据存储部件，并且每个此类部件应是 WordprocessingML 包中主文档 ([§11.3.10]) 部件中隐式关系的目标； SpreadsheetML 包中的工作簿 ([§12.3.23]) 部件； 或讲义母版 ([§13.3.3])、笔记母版 ([§13.3.4])、笔记幻灯片 ([§13.3.5])、演示文稿 ([§13.3.6])、幻灯片([§13.3.8])、幻灯片布局（[§13.3.9]）或 PresentationML 包中的幻灯片母版（[§13.3.10]）部件。

    !!! info "Example"

        以下主文档部件关系项包含与自定义 XML 数据存储部件的关系，该部件存储在 ZIP 项 `../customXML/item1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlData" Target="../customXML/item1.xml"/>
        </Relationships>
        ```
    
    自定义 XML 数据存储部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal ）。
    
    自定义 XML 数据存储部件允许与 ECMA-376 定义的以下部件具有隐式关系：
    
    * 自定义 XML 数据存储属性 (§15.2.6)

    自定义 XML 数据存储部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Custom XML Data Storage Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>any XML allowed</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customXml`</td>
        </tr>
    </table>

    An instance of this part type can contain arbitrary XML. As such, an instance of this part can be used to roundtrip arbitrary custom XML data with this package.
    
    A package is permitted to contain one or more Custom XML Data Storage parts, and each such part shall be the target of an implicit relationship in a Main Document ([§11.3.10]) part in a WordprocessingML package; a Workbook ([§12.3.23]) part in a SpreadsheetML package; or a Handout Master ([§13.3.3]) , Notes Master ([§13.3.4]), Notes Slide ([§13.3.5]), Presentation ([§13.3.6]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part in a PresentationML package.

    !!! info "Example"

        The following Main Document part-relationship item contains a relationship to a Custom XML Data Storage part, which is stored in the ZIP item ../customXML/item1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlData" Target="../customXML/item1.xml"/>
        </Relationships>
        ```
    
    A Custom XML Data Storage part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Custom XML Data Storage part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Custom XML Data Storage Properties (§15.2.6)

    A Custom XML Data Storage part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 15.2.6 自定义 XML 数据存储属性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.customXmlProperties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/customXmlDataProps</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customXmlProps`</td>
        </tr>
    </table>

    此部件类型的实例包含为此自定义 XML 数据指定的属性集。 这些属性由存储的唯一 ID 以及有关此自定义 XML 数据存储所使用的 XML Schema 集的信息组成。

    包允许包含零个或多个自定义 XML 数据存储属性部件，并且每个此类部件应是自定义 XML 数据存储（[§15.2.4]）部件的隐式关系的目标。

    !!! info "Example"

        以下自定义 XML 数据存储部件关系项包含与自定义 XML 数据存储属性部件的关系，该部件存储在 ZIP 项 `itemProps1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlProps" Target="itemProps1.xml"/>
        </Relationships>
        ```

    此内容类型的一部件的根元素应为 `datastoreItem`

    !!! info "Example"

        ```xml
        <ds:datastoreItem ds:itemID="{D85…53A}" xmlns:ds="…"/> \
        ```

    自定义 XML 数据存储属性部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal ）。
    
    自定义 XML 数据存储属性部件不应与 ECMA-376 定义的其他部件有隐式或显式关系。

=== "英文"

    **Custom XML Data Storage Properties Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.customXmlProperties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/customXmlDataProps</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customXmlProps`</td>
        </tr>
    </table>

    An instance of this part type contains the set of properties which are specified for this custom XML data. These properties consist of a unique ID for the storage, as well as information on the set of XML schemas used by this custom XML data storage.

    A package is permitted to contain zero or more Custom XML Data Storage Properties parts, and each such part shall be the target of an implicit relationship from a Custom XML Data Storage ([§15.2.4]) part.

    !!! info "Example"

        The following Custom XML Data Storage part-relationship item contains a relationship to a Custom XML Data Storage Properties part, which is stored in the ZIP item itemProps1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/customXmlProps" Target="itemProps1.xml"/>
        </Relationships>
        ```

    The root element for a part of this content type shall be datastoreItem

    !!! info "Example"

        ```xml
        <ds:datastoreItem ds:itemID="{D85…53A}" xmlns:ds="…"/> \
        ```

    A Custom XML Data Storage Properties part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Custom XML Data Storage Properties part shall not have implicit or explicit relationships to other parts defined by ECMA-376. 

### 15.2.7 数字签名起源部件

=== "中文"

    该部件在 [ECMA-376-2](../ecma-part2-refrence.md) 的 [§13.2.1] “数字签名来源部件”中定义。

    !!! info "译注"

        该部件内容设计数字签名，目前未涉及，且章节应为第二部分的[§10.4.2](../ecma-part2-refrence.md#10-数字签名) 节，详细信息参考原文档/文件.

=== "英文"

    **Digital Signature Origin Part**

    This part is defined in [§13.2.1], “Digital Signature Origin Part”, of ECMA-376-2.

### 15.2.8 数字签名 XML 签名部件

=== "中文"

    该部件定义于 ECMA-376-2 的 §13.2.2 节。 “Digital Signature XML Signature Part”.

    !!! info "译注"

        该部件内容设计数字签名，目前未涉及，且章节应为第二部分的[§10.4.3](../ecma-part2-refrence.md#10-数字签名) 节，详细信息参考原文档/文件.

=== "英文"

    **Digital Signature XML Signature Part**

    The part is defined in §13.2.2, “Digital Signature XML Signature Part”, of ECMA-376-2.

### 15.2.9 嵌入式控制持久化部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                任何支持的音频类型.</br> </br>
                注意: 有多种可能的控制类型。 潜在控件类型的一个示例是 Active X 控件，它将使用以下内容类型：“application/vnd.ms-office.activeX+xml”。
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/control`</td>
        </tr>
    </table>

    该部件的实例包含有关包中嵌入控件的信息。 当要求保留时，此信息由指定的控件提供。
    
    !!! info "Example"
        
        应用程序可以利用嵌入式对象服务器技术 KParts 或 Bonobo 来使用该部件存储嵌入式对象。
    
    一个包允许包含一个或多个嵌入式控制持久性部件，并且每个此类部件应成为 WordprocessingML 包中的
    
    - 尾注 ([§11.3.4])、
    - 页脚 ([§11.3.6])、
    - 脚注 ([§11.3.7])、
    - 标题 ([§11.3.9]) 或
    - 主文档 ([§11.3.10]) 等等部件中显式关系项的目标； 
    
    或者 SpreadsheetML 包中的
    
    - 工作表部件 ([§12.3.24])； 
    
    或者 PresentationML 包中的

    - 讲义母版 ([§13.3.3])、
    - 笔记幻灯片 ([§13.3.5])、
    - 笔记母版 ([§13.3.4])、
    - 幻灯片 ([§13.3.8])、
    - 幻灯片布局 ([§13.3.9])、
    - 幻灯片母版 ([§13.3.10]) 等等部件的关系项。
    
    该部件的内容类型决定了嵌入控件的格式和内容。
    
    !!! info "Example"
    
        以下示例显示了可用于嵌入式控件的持久性，该控件是 WordprocessingML 文档中的 Java 小程序（为简洁起见，省略了提供控件静态图像表示的绘图对象，当 Java 小程序本身不可用时使用）：

        ```xml
        <w:p>
            <w:r w:rsidR="005810E1">
                <w:object w:dxaOrig="1440" w:dyaOrig="1440">
                    <w:drawing>
                        …
                    </w:drawing>
                    <w:control r:id="rId5" w:name="CommandButton1" w:shapeid="1027" />
                </w:object>
            </w:r>
        </w:p>
        ```

        `rId5` 的关系类型是: `http://purl.oclc.org/ooxml/officeDocument/relationships/control`
    
        rId5 引用的部件的 XML 内容可以是:

        ```xml
        <applet xlink:href="../../../../Program%20Files/Application" 
                xlink:type="simple" 
                xlink:show="embed" 
                xlink:actuate="onLoad" 
                code="CalculateApplet.class" 
                mayscript="false"/>
        ```
    
    !!! info "Example"
    
        以下示例显示可用于嵌入控件（ WordprocessingML 文档中的 ActiveX 控件）的持久性（为简洁起见，在 ActiveX 控件本身不可用时使用的提供控件静态图像表示的绘图对象已被省略）：

        ```xml
        <w:p>
            <w:r w:rsidR="005810E1">
                <w:object w:dxaOrig="1440" w:dyaOrig="1440">
                    <w:drawing>
                        …
                    </w:drawing>
                    <w:control r:id="rId5" w:name="CommandButton1" w:shapeid="1027" />
                </w:object>
            </w:r>
        </w:p>
        ```

        `rId5` 的关系类型是: `http://purl.oclc.org/ooxml/officeDocument/relationships/control`
    
        `rId5` 引用的部件的内容类型可以是: `application/vnd.ms-office.activeX+xml`
    
        rId5 引用的部件的 XML 内容可以是:

        ```xml
        <ax:ocx ax:classid="{D7053240-CE69-11CD-A777-00DD01143C57}"
                ax:persistence="persistPropertyBag"
                xmlns:ax="http://schemas.microsoft.com/office/2006/activeX">
            <ax:ocxPr ax:name="Caption" ax:value="CommandButton1" />
            <ax:ocxPr ax:name="Size" ax:value="2540;847" />
            <ax:ocxPr ax:name="FontName" ax:value="Calibri" />
            <ax:ocxPr ax:name="FontHeight" ax:value="225" />
            <ax:ocxPr ax:name="FontCharSet" ax:value="0" />
            <ax:ocxPr ax:name="FontPitchAndFamily" ax:value="2" />
            <ax:ocxPr ax:name="ParagraphAlign" ax:value="3" />
        </ax:ocx>
        ```
    
    嵌入式控制持久性部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    嵌入式控制持久性部件不应与 ECMA-376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Embedded Control Persistence Part**

    Content Type: Any supported audio type. 

    !!! info "Note"

        There are a number of possible control types. One example of a potential control type would be an Active X control, which would use the following content type: `application/vnd.ms-office.activeX+xml`.

    Root Namespace: not applicable

    Source Relationship: http://purl.oclc.org/ooxml/officeDocument/relationships/control

    An instance of this part contains information about an embedded control in the package. This information is
    provided by the specified control when asked to persist. 
    
    !!! info "Example"
        
        An application might utilize the embedded object server technology KParts or Bonobo to store an embedded object using this part.
    
    A package is permitted to contain one or more Embedded Control Persistence parts, and each such part shall be
    the target of an explicit relationship in an Endnotes (§11.3.4), Footer (§11.3.6), Footnotes (§11.3.7), Header
    (§11.3.9), or Main Document (§11.3.10) part-relationship item in a WordprocessingML package; a Worksheet
    part (§12.3.24) in a SpreadsheetML package; or a Handout Master (§13.3.3), Notes Slide (§13.3.5), Notes Master
    (§13.3.4), Slide (§13.3.8), Slide Layout (§13.3.9), Slide Master (§13.3.10) part-relationship item in a
    PresentationML package.
    
    The content type of this part shall determine the format and contents of the embedded control.
    
    !!! info "Example"
    
        The following example shows the persistence that could be used for an embedded control which is a Java applet within a WordprocessingML document (the drawing object which provides a static image representation of the control, used when the Java applet itself is unavailable, has been omitted for brevity):

        ```xml
        <w:p>
            <w:r w:rsidR="005810E1">
                <w:object w:dxaOrig="1440" w:dyaOrig="1440">
                    <w:drawing>
                        …
                    </w:drawing>
                    <w:control r:id="rId5" w:name="CommandButton1" w:shapeid="1027" />
                </w:object>
            </w:r>
        </w:p>
        ```

        The relationship type for rId5 is: `http://purl.oclc.org/ooxml/officeDocument/relationships/control`
    
        The XML content of the part referenced by rId5 could be:
    
        ```xml
        <applet xlink:href="../../../../Program%20Files/Application" 
                xlink:type="simple" 
                xlink:show="embed" 
                xlink:actuate="onLoad" 
                code="CalculateApplet.class" 
                mayscript="false"/>
        ```
    
    !!! info "Example"
    
        The following example shows the persistence that could be used for an embedded control which is an ActiveX control within a WordprocessingML document(the drawing object which provides a static image representation of the control, used when the ActiveX control itself is unavailable, has been omitted for brevity):

        ```xml
        <w:p>
            <w:r w:rsidR="005810E1">
                <w:object w:dxaOrig="1440" w:dyaOrig="1440">
                    <w:drawing>
                        …
                    </w:drawing>
                    <w:control r:id="rId5" w:name="CommandButton1" w:shapeid="1027" />
                </w:object>
            </w:r>
        </w:p>
        ```

        The relationship type for rId5 is: `http://purl.oclc.org/ooxml/officeDocument/relationships/control`
    
        The content type of the part referenced by rId5 could be: application/vnd.ms-office.activeX+xml
    
        The XML content of the part referenced by rId5 could be:
    
        ```xml
        <ax:ocx ax:classid="{D7053240-CE69-11CD-A777-00DD01143C57}"
                ax:persistence="persistPropertyBag"
                xmlns:ax="http://schemas.microsoft.com/office/2006/activeX">
            <ax:ocxPr ax:name="Caption" ax:value="CommandButton1" />
            <ax:ocxPr ax:name="Size" ax:value="2540;847" />
            <ax:ocxPr ax:name="FontName" ax:value="Calibri" />
            <ax:ocxPr ax:name="FontHeight" ax:value="225" />
            <ax:ocxPr ax:name="FontCharSet" ax:value="0" />
            <ax:ocxPr ax:name="FontPitchAndFamily" ax:value="2" />
            <ax:ocxPr ax:name="ParagraphAlign" ax:value="3" />
        </ax:ocx>
        ```
    
    An Embedded Control Persistence part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    An Embedded Control Persistence part shall not have any implicit or explicit relationships to other parts defined by ECMA-376.

### 15.2.10 嵌入对象部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                任何支持的音频类型.
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/oleObject`</td>
        </tr>
    </table>

    此部件类型的实例可以包含由任何嵌入对象服务器生成的嵌入对象.

    包允许包含零个或多个嵌入式对象部件，并且每个此类部件可能是 WordprocessingML 包中

    - 注释 ([§11.3.2])、
    - 尾注 ([§11.3.4])、
    - 页脚 ([§11.3.6])、
    - 脚注 ([§11.3.7])、
    - 页眉 ([§11.3.9])、
    - 主文档 ([§11.3.10]) 等等部件； 
    
    或 SpreadsheetML 包中的
    
    - 工作表 ([§12.3.24])部件； 
    
    或 PresentationML 包中的
    
    - 讲义母版 ([§13.3.3])、
    - 笔记幻灯片 ([§13.3.5])、
    - 笔记母版 ([§13.3.4])、
    - 幻灯片 ([§13.3.8])、
    - 幻灯片布局 ([§13.3.9])、
    - 幻灯片母版 ([§13.3.10])部件。

    等的显示关系目标（target of an explicit relationship）。
    
    WordprocessingML 文档包允许包含零个或多个嵌入对象部件，每个部件都应是主文档部件关系项中关系的目标。 每个嵌入对象部件应有一个关联的图像，该图像作为相应嵌入对象的占位符出现在文档中。
    
    !!! info "Example"
    
        考虑这样一种情况：WordprocessingML 文档中嵌入了一个视频对象和一个音频对象。 以下主文档部件关系项包含与两个嵌入部件（视频和音频各一个）的关系，这些部件存储在 ZIP 项 `embeddings/embeddedObjectN.bin` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/oleObject" Target="embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId7"
                Type="http://…/oleObject" Target="embeddings/embeddedObject2.bin"/>
            <Relationship Id="rId4"
                Type="http://…/image" Target="media/image1.png"/>
            <Relationship Id="rId6"
                Type="http://…/image" Target="media/image2.png"/>
        </Relationships>
        ```
    
    SpreadsheetML 文档包允许包含零个或多个嵌入式对象部件，每个部件都应是工作表部件关系项中关系的目标。
    
    !!! info "Example"
    
        考虑这样一种情况：SpreadsheetML 文档在一个工作表中嵌入了一个视频对象和一个音频对象，而另一个工作表中嵌入了另一个音频对象。 以下工作表文档部件关系项包含与两个嵌入对象部件（视频和音频各一个）的关系，这些部件存储在 ZIP 项 `../embeddings/embeddedObjectN.bin` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/oleObject" Target="../embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId3"
                Type="http://…/oleObject" Target="../embeddings/embeddedObject2.bin"/>
        </Relationships>
        ```

    允许 PresentationML 文档包包含零个或多个嵌入式对象部件，每个部件都应是幻灯片部件关系项中关系的目标。 

    !!! info "Example"

        考虑这样一种情况：PresentationML 文档在一张幻灯片上嵌入了一个视频对象和一个音频对象，并在另一张幻灯片上嵌入了另一个音频对象。 以下幻灯片部件关系项包含与两个嵌入式对象部件（视频和音频各一个）的关系，这些部件存储在 ZIP 项目 `../embeddings/embeddedObjectN.bin` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http://…/oleObject"
                Target="../embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId7"
                Type="http://…/oleObject"
                Target="../embeddings/embeddedObject2.bin"/>
        </Relationships>
        ```

    嵌入式对象部件可以位于包含关系部件的包的内部或外部（从语法上表达，Relationship 元素的 TargetMode 属性可以是 Internal 或 external）。
    
    嵌入对象部件允许与 ECMA376 定义的以下部件有显式关系：
    
    * Hyperlink ([§15.3])
    
    嵌入对象部件不应与 ECMA376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Embedded Object Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                Any supported audio type.
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/oleObject`</td>
        </tr>
    </table>

    An instance of this part type can contain an embedded object produced by any embedded object server.

    A package is permitted to contain zero or more Embedded Object parts, and each such part shall be the target of an explicit relationship from a Comments (§11.3.2), Endnotes (§11.3.4), Footer (§11.3.6), Footnotes (§11.3.7), Header (§11.3.9), or Main Document (§11.3.10) part in a WordprocessingML package; a Worksheet part (§12.3.24) in a SpreadsheetML package; or a Handout Master (§13.3.3), Notes Slide (§13.3.5), Notes Master (§13.3.4), Slide (§13.3.8), Slide Layout (§13.3.9), Slide Master (§13.3.10) part in a PresentationML package.
    
    A WordprocessingML document package is permitted to contain zero or more Embedded Object parts, each of which shall be the target of a relationship in a Main Document part-relationship item. Each Embedded Object part shall have an associated image, which appears in the document as a placeholder for the corresponding embedded object.
    
    !!! info "Example"
    
        : Consider the case in which a WordprocessingML document has embedded in it one video object and one audio object. The following Main Document part-relationship item contains relationships to two Embedded parts (one each for the video and audio), which are stored in the ZIP items embeddings/embeddedObjectN.bin:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/oleObject" Target="embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId7"
                Type="http://…/oleObject" Target="embeddings/embeddedObject2.bin"/>
            <Relationship Id="rId4"
                Type="http://…/image" Target="media/image1.png"/>
            <Relationship Id="rId6"
                Type="http://…/image" Target="media/image2.png"/>
        </Relationships>
        ```
    
    A SpreadsheetML document package is permitted to contain zero or more Embedded Object parts, each of which shall be the target of a relationship in a Worksheet part-relationship item. 
    
    !!! info "Example"
    
        Consider the case in which a SpreadsheetML document has embedded in it one video object and one audio object on one worksheet, and another audio object embedded in another worksheet. The following Worksheet Document part-relationship item contains relationships to two Embedded Object parts (one each for the video and audio), which are stored in the ZIP items ../embeddings/embeddedObjectN.bin:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/oleObject" Target="../embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId3"
                Type="http://…/oleObject" Target="../embeddings/embeddedObject2.bin"/>
        </Relationships>
        ```

    A PresentationML document package is permitted to contain zero or more Embedded Object parts, each of which shall be the target of a relationship in a Slide part-relationship item. 

    !!! info "Example"

        Consider the case in which a PresentationML document has embedded in it one video object and one audio object on one slide, and another audio object embedded on another slide. The following Slide partrelationship ite contains relationships to two Embedded Object parts (one each for the video and audio), which are stored in the ZIP items ../embeddings/embeddedObjectN.bin:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http://…/oleObject"
                Target="../embeddings/embeddedObject1.bin"/>
            <Relationship Id="rId7"
                Type="http://…/oleObject"
                Target="../embeddings/embeddedObject2.bin"/>
        </Relationships>
        ```

    An Embedded Object part can be located within or external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element can be Internal or External).
    
    An Embedded Object part is permitted to have an explicit relationship to the following parts defined by ECMA376:
    
    * Hyperlink (§15.3)
    
    An Embedded Object part shall not have any implicit or explicit relationships to other parts defined by ECMA376.

### 15.2.11 嵌入包部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any content type is allowed </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/package`</td>
        </tr>
    </table>

    此部件类型的实例包含完整的包。 例如，WordprocessingML 文档可能包含 SpreadsheetML 或PresentationML 文档，在这种情况下，WordprocessingML 文档包将包含定义该 SpreadsheetML 或 PresentationML 文档的嵌入包部件。

    包允许包含零个或多个嵌入式包部件，并且每个此类部件应是如下部件的显式关系的目标，包括：

    WordprocessingML 包中的

    - Chart ([§14.2.1]), 
    - Comments ([§11.3.2]), 
    - Endnotes ([§11.3.4]), 
    - Footer ([§11.3.6]), 
    - Footnotes ([§11.3.7]), 
    - Header ([§11.3.9]), 或 
    - Main Document ([§11.3.10]) 部件；

    SpreadsheetML 包中的

    - Chart ([§14.2.1])
    - Worksheet ([§12.3.24]) 部件;

    PresentationML 包中的

    - Chart ([§14.2.1]), 
    - Handout Master ([§13.3.3]), 
    - Notes Slide ([§13.3.5]), 
    - Notes Master ([§13.3.4]), 
    - Slide ([§13.3.8]), 
    - Slide Layout ([§13.3.9]), 
    - Slide Master ([§13.3.10]) 部件; 
    
    !!! info "Example"

        以下演示部件关系项包含与两个嵌入包部件的关系：
        一个是 SpreadsheetML 包，存储在 ZIP 项 `embeddings/Worksheet1.xlsx` 中，
        另一个是PresentationML 包，存储在 ZIP 项 `embeddings/Presentation2.pptx`中。
        如果消费者无法处理嵌入的包类型，则图像文件将用作文档显示占位符：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/image" Target="media/image1.emf"/>
            <Relationship Id="rId5"
                Type="http:package" Target="embeddings/Worksheet1.xlsx"/>
            <Relationship Id="rId6"
                Type="http://…/image" Target="media/image2.emf"/>
            <Relationship Id="rId7"
                Type="http://…/package" Target="embeddings/Presentation2.pptx"/>
        </Relationships>
        ```

    嵌入式包部件可以位于包含关系部件的包的内部或外部（从语法上表达，关系元素的 TargetMode 属性可以是Internal 或External）。

    嵌入式包部件允许与 ECMA376 定义的以下部件有显式关系：
    
    * Hyperlink ([§15.3])
    
    嵌入式包部件不应与 ECMA376 定义的其他部件有任何隐式或显式关系。

=== "英文"

    **Embedded Package Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any content type is allowed </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/package`</td>
        </tr>
    </table>

    An instance of this part type contains a complete package. For example, a WordprocessingML document might contain a SpreadsheetML or PresentationML document, in which case, the WordprocessingML document package would contain an embedded package part that defined that SpreadsheetML or PresentationML document. 

    A package is permitted to contain zero or more Embedded Package parts, and each such part shall be the target of an explicit relationship from a Chart ([§14.2.1]), Comments ([§11.3.2]), Endnotes ([§11.3.4]), Footer ([§11.3.6]), Footnotes ([§11.3.7]), Header ([§11.3.9]), or Main Document ([§11.3.10]) part in a WordprocessingML package; a Chart ([§14.2.1]), or Worksheet part ([§12.3.24]) in a SpreadsheetML package; or a Chart ([§14.2.1]), Handout Master ([§13.3.3]), Notes Slide ([§13.3.5]), Notes Master ([§13.3.4]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), Slide Master ([§13.3.10]) part in a PresentationML package.

    !!! info "Example"

         The following Presentation part-relationship item contains relationships to two Embedded Package parts: one is a SpreadsheetML package, which is stored in the ZIP item embeddings/Worksheet1.xlsx, the other is a PresentationML package, which is stored in the ZIP item embeddings/Presentation2.pptx. The image files are used as document display placeholders if the consumer cannot handle the embedded package type:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/image" Target="media/image1.emf"/>
            <Relationship Id="rId5"
                Type="http:package" Target="embeddings/Worksheet1.xlsx"/>
            <Relationship Id="rId6"
                Type="http://…/image" Target="media/image2.emf"/>
            <Relationship Id="rId7"
                Type="http://…/package" Target="embeddings/Presentation2.pptx"/>
        </Relationships>
        ```

    An Embedded Package part can be located within or external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element can be Internal or External).

    An Embedded Package part is permitted to have an explicit relationship to the following parts defined by ECMA376:
    
    * Hyperlink (§15.3)
    
    An Embedded Package part shall not have any implicit or explicit relationships to other parts defined by ECMA376.

### 15.2.12 文件属性部件

=== "中文"

    文件属性分为三种：核心(core)、自定义(custom)和扩展(extended)。 包的核心文件属性使用户能够从该包内发现、获取和设置常见的属性集，无论它是 WordprocessingML、SpreadsheetML 还是PresentationML 包。 扩展文件属性特定于 Office Open XML 包，而自定义文件属性由用户定义，每个自定义文件属性都具有名称(name)、值(value)和类型(type)。

=== "英文"

    **File Properties**

    There are three kinds of file properties: core, custom, and extended. The core file properties of a package enable users to discover, get, and set common sets of properties from within that package, regardless of whether it’s a WordprocessingML, SpreadsheetML, or PresentationML package. Extended file properties are specific to Office Open XML packages, while custom file properties are defined by the user, with each custom file property having a name, a value, and a type.

#### 15.2.12.1 核心文件属性部件

=== "中文"

    该部件和相关的 OPC 部件在 ECMA-376-2 的第 11 节 “核心属性” 中定义。


    !!! info "译注"

        较新版的关于核心属性的内容在第二部分的[第8章](../ecma-part2-refrence.md#8-核心属性)中定义。

=== "英文"

    **Core File Properties Part**

    This part and the related OPC part is defined in §11, “Core Properties”, of ECMA-376-2.

#### 15.2.12.2 自定义文件属性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.custom-properties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/customProperties</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customProperties`</td>
        </tr>
    </table>

    此部件的实例包含适用于包的自定义文件属性的名称、它们的值以及这些值的类型。 自定义文件属性可能是为其准备文档的客户的名称、发生某些事件的日期/时间、文档编号或某些布尔状态标志。
    
    一个包最多应包含一个自定义文件属性部件，并且该部件应是文档的包关系项中关系的目标。

=== "英文"

    **Custom File Properties Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.custom-properties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/customProperties</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/customProperties`</td>
        </tr>
    </table>

    An instance of this part contains the names of custom file properties that apply to the package, their values, and the types of those values. A custom file property might be the name of the client for whom the document was prepared, a date/time on which some event happened, a document number, or some Boolean status flag.
    
    A package shall contain at most one Custom File Properties part, and that part shall be the target of a relationship in the package-relationship item for the document.

#### 15.2.12.3 扩展文件属性部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.custom-properties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/extendedProperties</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/extendedProperties`</td>
        </tr>
    </table>

    该部件的实例包含特定于 Office Open XML 文档的属性。
    
    !!! info "Example"
        
        PresentationML 文档指定制作者上次保存时演示文稿中幻灯片的数量。

    一个包最多应包含一个扩展文件属性部件，并且该部件应是文档的包关系项(/_rels/.rels)中关系的目标。
    
    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/extended-properties" Target="docProps/app.xml"/>
        </Relationships>
        ```
    
    该内容类型的部件的根元素应是`Properties`。
    
    !!! info "Example"

        以下是 WordprocessingML 文档中的一些内容标记：

        ```xml
        <Properties …>
            <Template>Normal.dotm</Template>
            <TotalTime>0</TotalTime>
            <Pages>1</Pages>
            <Words>3</Words>
            <Characters>22</Characters>
            <Application>Sample Producer</Application>
            <DocSecurity>0</DocSecurity>
            <Lines>1</Lines>
            <Paragraphs>1</Paragraphs>
            …
            <AppVersion>12.0000</AppVersion>
        </Properties>
        ```

        以下是 SpreadsheetML 文档中的一些内容标记：

        ```xml
        <Properties …>
            <Application>Sample Producer</Application>
            <HeadingPairs>
            …
            </HeadingPairs>
            <TitlesOfParts>
            …
            </TitlesOfParts>
            <Company>Consultant</Company>
            …
        </Properties>
        ```

        以下是来自 PresentationML 文档的一些内容标记：

        ```xml
        <Properties …>
            <Template>ppt_template_sdwest05</Template>
            <TotalTime>3166</TotalTime>
            <Words>37</Words>
            <Application>Sample Producer</Application>
            <PresentationFormat>On-screen Show</PresentationFormat>
            <Paragraphs>15</Paragraphs>
            <Slides>2</Slides>
            <Notes>2</Notes>
            …
            <HeadingPairs>
            …
            </HeadingPairs>
            <TitlesOfParts>
            …
            </TitlesOfParts>
            …
        </Properties>
        ```

    扩展文件属性部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    扩展文件属性部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Extended File Properties Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.custom-properties+xml</td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/extendedProperties</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/extendedProperties`</td>
        </tr>
    </table>

    An instance of this part contains properties specific to an Office Open XML document. 
    
    !!! info "Example"
        
        A PresentationML document specifies the number of slides in this presentation when last saved by a producer.

    A package shall contain at most one Extended File Properties part, and that part shall be the target of a relationship in the package-relationship item for the document.
    
    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/extended-properties" Target="docProps/app.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be Properties.
    
    !!! info "Example"

        Here's some content markup from a WordprocessingML document:

        ```xml
        <Properties …>
            <Template>Normal.dotm</Template>
            <TotalTime>0</TotalTime>
            <Pages>1</Pages>
            <Words>3</Words>
            <Characters>22</Characters>
            <Application>Sample Producer</Application>
            <DocSecurity>0</DocSecurity>
            <Lines>1</Lines>
            <Paragraphs>1</Paragraphs>
            …
            <AppVersion>12.0000</AppVersion>
        </Properties>
        ```

        here's some content markup from a SpreadsheetML document:

        ```xml
        <Properties …>
            <Application>Sample Producer</Application>
            <HeadingPairs>
            …
            </HeadingPairs>
            <TitlesOfParts>
            …
            </TitlesOfParts>
            <Company>Consultant</Company>
            …
        </Properties>
        ```

        and here's some content markup from a PresentationML document:

        ```xml
        <Properties …>
            <Template>ppt_template_sdwest05</Template>
            <TotalTime>3166</TotalTime>
            <Words>37</Words>
            <Application>Sample Producer</Application>
            <PresentationFormat>On-screen Show</PresentationFormat>
            <Paragraphs>15</Paragraphs>
            <Slides>2</Slides>
            <Notes>2</Notes>
            …
            <HeadingPairs>
            …
            </HeadingPairs>
            <TitlesOfParts>
            …
            </TitlesOfParts>
            …
        </Properties>
        ```

    A Extended File Properties part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    An Extended File Properties part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 15.2.13 字体部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/x-fontdata </br>
                application/x-font-ttf </br>
                application/vnd.openxmlformats-officedocument.obfuscatedFont
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/font`</td>
        </tr>
    </table>

    此部件类型的实例包含直接嵌入到文档中的给定字体。 （当使用自定义字体或未广泛分发的字体时，这非常有用。）

    存储在 Font 部件中的字体可以以下列格式之一存储，由关联的内容类型标识：

    - `application/x-fontdata` 指定字体应以 `http://www.w3.org/Submission/2008/SUBM-EOT-20080305` 的嵌入式 OpenType 格式存储
    -` application/x-font-ttf` 指定字体应以符合 ISO/IEC 14496-22:2008 `§3.5` 中定义的开放字体结构的格式存储。 
        
        !!! info "Note"
    
            无法使用 ISO/IEC 14496-22:2008 `§3.6` 中定义的 TrueType 集合格式(TrueType Collection format)。
    
    - `application/vnd.openxmlformats-officedocument.obfuscatedFont` 指定使用字体嵌入（[§17.8.1]）指定的算法对字体进行混淆。 源字体应以符合 ISO/IEC 14496-22:2008 `§3.5` 中定义的开放字体结构的格式存储。
        
        !!! info "Note"
    
            无法使用 ISO/IEC 14496-22:2008 `§3.6` 中定义的 TrueType 集合格式(TrueType Collection format)。
            
        仅允许 WordprocessingML 类型的包引用此内容类型。

    如果字体以 ISO/IEC 14496-22:2007 格式存储，则只能在作为单独字体存储时使用。

    !!! info "Note"

        在使用此部件嵌入字体集合之前，应将其转换为单独的字体。
    
    包应包含零个或多个字体部件，对于每个存在的部件，该部件应是字体表(Font Table)（[§11.3.5]）或演示（[§13.3.6]）部件中显式关系的目标 。

    Font 部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。

    字体部件不应与 ECMA-376 定义的其他部件有隐式或显式的关系。

=== "英文"

    **Font Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/x-fontdata </br>
                application/x-font-ttf </br>
                application/vnd.openxmlformats-officedocument.obfuscatedFont
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/font`</td>
        </tr>
    </table>

    An instance of this part type contains a given font embedded directly into the document. (This is useful when using custom fonts or fonts that are not widely distributed.)

    Fonts stored in a Font part can be stored in one of the following formats, identified by the associated content type:

    - application/x-fontdata specifies that the font shall be stored in the Embedded OpenType Format of http://www.w3.org/Submission/2008/SUBM-EOT-20080305
    - application/x-font-ttf specifies that the font shall be stored in a format conforming to Open Font Structure defined in ISO/IEC 14496-22:2008 §3.5. 
        
        !!! info "Note"
    
            The TrueType Collection format defined in ISO/IEC 14496-22:2008 §3.6 cannot be used. \

    - application/vnd.openxmlformats officedocument.obfuscatedFont specifies that the font is obfuscated using the algorithm specified by Font Embedding (§17.8.1). The source font shall be stored in a format conforming to Open Font Structure defined in ISO/IEC 14496-22:2008 §3.5. [Note: The TrueType Collection format defined in ISO/IEC 14496-22:2008 §3.6 cannot be used. end note] Only packages of type WordprocessingML are permitted to reference this content type.

    If a font is stored in the ISO/IEC 14496-22:2007 format, it shall only be used when stored as an individual font. 

    !!! info "Note"

        Font collections should be converted into individual fonts before they are embedded using this part.
    
    A package shall contain zero or more Font parts, and for each that exists, that part shall be the target of an explicit relationship in the Font Table ([§11.3.5]), or Presentation ([§13.3.6]) part.

    A Font part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Font part shall not have implicit or explicit relationships to other parts defined by ECMA-376.

### 15.2.14 图片部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported image type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>image/gif</td>
                        <td>http://www.w3.org/Graphics/GIF/spec-gif89a.txt</td>
                    </tr>
                    <tr>
                        <td>image/png</td>
                        <td>ISO/IEC 15948:2003 http://www.libpng.org/pub/png/spec/</td>
                    </tr>
                    <tr>
                        <td>image/tiff</td>
                        <td>http://partners.adobe.com/public/developer/tiff/index.html#spec</td>
                    </tr>
                    <tr>
                        <td>image/pict</td>
                        <td>http://developer.apple.com/documentation/mac/QuickDraw/QuickDraw2.html</td>
                    </tr>
                    <tr>
                        <td>image/jpeg</td>
                        <td>http://www.w3.org/Graphics/JPEG/</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/image`</td>
        </tr>
    </table>

    图像可以作为 ZIP 项存储在包中。 图像 ZIP 项应通过**图像部件关系**和适当的**内容类型**来标识。

    一个包允许包含零个或多个图像部件，并且每个此类部件应成为以下部件的显示关系目录, 如下:
    
    WordprocessingML 包中的

    - Comments ([§11.3.2]), 
    - Endnotes ([§11.3.4]),
    - Footer ([§11.3.6]), 
    - Footnotes ([§11.3.7]), 
    - Header ([§11.3.9]), 
    - Drawing ([§12.3.8]),
    - Main Document ([§11.3.10]) 
    
    PresentationML 包中的
    
    - Handout Master ([§13.3.3]), 
    - Notes Slide ([§13.3.5]), 
    - Notes Master ([§13.3.4]), 
    - Slide ([§13.3.8]), 
    - Slide Layout ([§13.3.9]), 
    - Slide Master ([§13.3.10]).
    
    !!! info "Example"
    
        以下 PresentationML 的包关系项包含一个关系，用于存储在ZIP `item ../media/image1.jpeg` 中的幻灯片模板jpeg图像：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId8"
                Type="http://…/image" Target="../media/image1.jpeg"/>
        </Relationships>
        ```

    图像部件可以位于包含关系部件的包的内部或外部（从语法上表达，关系元素的 TargetMode 属性可以是 Internal 或 External）。

    图像部件不应与 ECMA-376 定义的其他部件有隐式或显式关系。
    
    想要互操作性的生产者应该使用以下标准格式之一：
    
    - image/png ISO/IEC 15948:2003, <http://www.libpng.org/pub/png/spec/>
    - image/jpeg, <http://www.w3.org/Graphics/JPEG>

=== "英文"

    **Image Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported image type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>image/gif</td>
                        <td>http://www.w3.org/Graphics/GIF/spec-gif89a.txt</td>
                    </tr>
                    <tr>
                        <td>image/png</td>
                        <td>ISO/IEC 15948:2003 http://www.libpng.org/pub/png/spec/</td>
                    </tr>
                    <tr>
                        <td>image/tiff</td>
                        <td>http://partners.adobe.com/public/developer/tiff/index.html#spec</td>
                    </tr>
                    <tr>
                        <td>image/pict</td>
                        <td>http://developer.apple.com/documentation/mac/QuickDraw/QuickDraw2.html</td>
                    </tr>
                    <tr>
                        <td>image/jpeg</td>
                        <td>http://www.w3.org/Graphics/JPEG/</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/image`</td>
        </tr>
    </table>

    An image can be stored in a package as a ZIP item. Image ZIP items shall be identified by an image part relationship and the appropriate content type.

    A package is permitted to contain zero or more Image parts, and each such part shall be the target of an explicit relationship from a Comments ([§11.3.2]), Endnotes ([§11.3.4]), Footer ([§11.3.6]), Footnotes ([§11.3.7]), Header ([§11.3.9]), Drawing ([§12.3.8]), or Main Document ([§11.3.10]) part in a WordprocessingML package or a Handout Master ([§13.3.3]), Notes Slide ([§13.3.5]), Notes Master ([§13.3.4]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part in a PresentationML package.
    
    !!! info "Example"
    
        The following PresentationML's package-relationship item contains one relationship, for the slide template jpeg image stored in the ZIP `item ../media/image1.jpeg`:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId8"
                Type="http://…/image" Target="../media/image1.jpeg"/>
        </Relationships>
        ```

    An Image part can be located within or external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element can be Internal or External).

    An Image part shall not have implicit or explicit relationships to other parts defined by ECMA-376.
    
    A producer that wants interoperability should use one of the following standard formats:
    
    - image/png ISO/IEC 15948:2003, `http://www.libpng.org/pub/png/spec/`
    - image/jpeg, `http://www.w3.org/Graphics/JPEG`

### 15.2.15 打印机设置部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.spreadsheetml.printerSettings (in SpreadsheetML documents) </br></br>
                application/vnd.openxmlformats-officedocument.wordprocessingml.printerSettings (in WordprocessingML documents) </br></br>
                application/vnd.openxmlformats-officedocument.presentationml.printerSettings (in PresentationML documents)
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/printerSettings`</td>
        </tr>
    </table>

    此部件类型的实例包含有关打印机或显示设备的初始化和环境的信息。 该信息的布局是应用程序定义的。

    !!! info "Note"
        
        建议打印机设置部件包含详细记录的 XML 内容，以提高互操作性； 然而，对打印机设置部件中包含的内容的格式没有要求。

    !!! info "Example"

        Windows 上的 Office Open XML 生成器可能存储此处定义的 DEVMODE 结构：http://msdn.microsoft.com/library/default.asp?url=/library/en-us/gdi/prntspol_8nle.asp，
        
        而 Mac OS 上的应用程序可能会选择存储此处定义的打印记录：http://developer.apple.com/documentation/Printing/index.html。
    
    SpreadsheetML 包允许每个图表(Chartsheet)、对话框表(Dialogsheet)或工作表(Worksheet)部件最多包含一个打印机设置部件，并且该部件应是图表(Chartsheet) ([§12.3.2])、、对话框表(Dialogsheet) ([§12.3.7]) 或工作表(Worksheet) ([§12.3.24]) 部件中隐式关系的目标。

    
    WordprocessingML 包允许包含零个或多个打印机设置部件，每个 `sectPr` 元素(Element)一个，每个部件都是来自主文档 ([§11.3.10]) 或词汇表文档 ([§11.3.8]) 部件的显式关系的目标 。
    
    一个 PresentationML 包最多允许包含一个打印机设置部件，并且该部件应是来自 Presentation ([§13.3.6]) 部件的隐式关系的目标。

    ??? info "译注:关系详情"

        参考: [9.2 Office Open Xml 中的关系](../ecma-part1/chapter-9.md#92-office-open-xml-中的关系){target="_bank"}

    !!! info "Example"
        
        以下 SpreadsheetML 工作表部件关系项包含与打印机设置部件的关系，该部件存储在 ZIP 项 `../printerSettings/printerSettings1.xml` 中：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/printerSettings"
                Target="../printerSettings/printerSettings1.xml"/>
        </Relationships>
        ```
    
        其中 `PrinterSettings1.xml` 的内容包含以下 XML：

        ```xml
        <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
        <PrinterSettings xmlns="…">
            <PrinterSetting name="PropertyName" value="PropertyValue" />
        </PrinterSettings>
        ```
    
    打印机设置部件应位于包含关系部件的包内（从语法上表达，关系元素的 TargetMode 属性应为 Internal ）。

    打印机设置部件不应与 ECMA-376 定义的任何其他部件有隐式或显式关系。

=== "英文"

    **Printer Settings Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>application/vnd.openxmlformats-officedocument.spreadsheetml.printerSettings (in SpreadsheetML documents) </br></br>
                application/vnd.openxmlformats-officedocument.wordprocessingml.printerSettings (in WordprocessingML documents) </br></br>
                application/vnd.openxmlformats-officedocument.presentationml.printerSettings (in PresentationML documents)
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/printerSettings`</td>
        </tr>
    </table>

    An instance of this part type contains information about the initialization and environment of a printer or a display device. The layout of this information is application-defined.

    !!! info "Note"
        
        It is recommended that a Printer Settings Part contain well documented XML content for improved interoperability; however, there is no requirement on the format of the content contained in a Printer Settings Part.

    !!! info "Example"

        An Office Open XML producer on Windows might store the DEVMODE structure defined here: http://msdn.microsoft.com/library/default.asp?url=/library/en-us/gdi/prntspol_8nle.asp, while an application on the Mac OS might choose to store the print record defined here: http://developer.apple.com/documentation/Printing/index.html.

    
    A SpreadsheetML package is permitted to contain at most one Printer Settings part per Chartsheet, Dialogsheet, or Worksheet part, and that part shall be the target of an implicit relationship from a Chartsheet ([§12.3.2]), Dialogsheet ([§12.3.7]), or Worksheet ([§12.3.24]) part. 
    
    A WordprocessingML package is permitted to contain zero or more Printer Settings parts, one per sectPr element, each a target of an explicit relationship from a Main Document ([§11.3.10]) or Glossary Document ([§11.3.8]) part. 
    
    A PresentationML package is permitted to contain at most one Printer Settings part, and that part shall be the target of an implicit relationship from a Presentation ([§13.3.6]) part.

    !!! info "Example"
        
        The following SpreadsheetML Worksheet part-relationship item contains a relationship to a Printer Settings part, which is stored in the ZIP item ../printerSettings/printerSettings1.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId4"
                Type="http://…/printerSettings"
                Target="../printerSettings/printerSettings1.xml"/>
        </Relationships>
        ```
    
        where the contents of PrinterSettings1.xml contains the following XML:

        ```xml
        <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
        <PrinterSettings xmlns="…">
            <PrinterSetting name="PropertyName" value="PropertyValue" />
        </PrinterSettings>
        ```
    
    A Printer Settings part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Printer Settings part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 15.2.16 缩略图部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported image type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>image/gif</td>
                        <td>http://www.w3.org/Graphics/GIF/spec-gif89a.txt</td>
                    </tr>
                    <tr>
                        <td>image/png</td>
                        <td>ISO/IEC 15948:2003 http://www.libpng.org/pub/png/spec/</td>
                    </tr>
                    <tr>
                        <td>image/tiff</td>
                        <td>http://partners.adobe.com/public/developer/tiff/index.html#spec</td>
                    </tr>
                    <tr>
                        <td>image/pict</td>
                        <td>http://developer.apple.com/documentation/mac/QuickDraw/QuickDraw2.html</td>
                    </tr>
                    <tr>
                        <td>image/jpeg</td>
                        <td>http://www.w3.org/Graphics/JPEG/</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/metadata/thumbnail`</td>
        </tr>
    </table>

    为了帮助最终用户识别包的各个部件或整个包，可以将称为缩略图的图像存储在该包中。 每个缩略图图像均由包制作者生成，并作为 ZIP 项目存储在包中。 生成的缩略图的大小没有限制，应用程序可以根据需要自由缩放图像。

    缩略图 ZIP 项应由包关系项目或部件关系项来标识。 包不得包含多个与整个包关联的缩略图关系，或者每个包部件不得包含多个缩略图关系。

    !!! info "Example"
        
        以下 PresentationML 的包关系项包含一种关系，用于存储在ZIP项 `thumbnail.wmf`中的元文件图像：

        ```xml
        <Relationships xmlns="…">
         <Relationship Id="rId2"
         Type="http://…/thumbnail" Target="docProps/thumbnail.wmf"/>
        </Relationships>
        ```

    缩略图部件应位于包含关系部件的包内（从语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。

    缩略图部件不应与 ECMA-376 定义的其他部件有隐式或显式关系。

=== "英文"

    **Thumbnail Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported image type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>image/gif</td>
                        <td>http://www.w3.org/Graphics/GIF/spec-gif89a.txt</td>
                    </tr>
                    <tr>
                        <td>image/png</td>
                        <td>ISO/IEC 15948:2003 http://www.libpng.org/pub/png/spec/</td>
                    </tr>
                    <tr>
                        <td>image/tiff</td>
                        <td>http://partners.adobe.com/public/developer/tiff/index.html#spec</td>
                    </tr>
                    <tr>
                        <td>image/pict</td>
                        <td>http://developer.apple.com/documentation/mac/QuickDraw/QuickDraw2.html</td>
                    </tr>
                    <tr>
                        <td>image/jpeg</td>
                        <td>http://www.w3.org/Graphics/JPEG/</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/metadata/thumbnail`</td>
        </tr>
    </table>

    To help end-users identify parts of a package or the package as a whole, images, called thumbnails, can be stored in that package. Each thumbnail image is generated by the package producer and is stored in the package as a ZIP item. There are no limitations on the size or dimensions of the thumbnail produced, and applications are free to scale the images as desired.

    Thumbnail ZIP items shall be identified by either a package-relationship item or a part-relationship item. Packages shall not contain more than one thumbnail relationship associated with the package as a whole, or more than one thumbnail relationship per package part.

    !!! info "Example"
        
        The following PresentationML's package-relationship item contains one relationship, for the metafile image stored in the ZIP item thumbnail.wmf:

        ```xml
        <Relationships xmlns="…">
         <Relationship Id="rId2"
         Type="http://…/thumbnail" Target="docProps/thumbnail.wmf"/>
        </Relationships>
        ```

    A Thumbnail part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Thumbnail part shall not have implicit or explicit relationships to other parts defined by ECMA-376.

### 15.2.17 视频部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported video type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>video/avi</td>
                        <td>http://www.the-labs.com/Video/odmlff2-avidef.pdf</td>
                    </tr>
                    <tr>
                        <td>video/mpg </td>
                        <td>ISO/IEC 13818</td>
                    </tr>
                    <tr>
                        <td>video/mpeg</td>
                        <td>ISO/IEC 13818</td>
                    </tr>
                    <tr>
                        <td>video/ogg</td>
                        <td>http://www.theora.org/doc/Theora.pdf</td>
                    </tr>
                    <tr>
                        <td>video/quicktime</td>
                        <td>http://developer.apple.com/documentation/QuickTime/</td>
                    </tr>
                    <tr>
                        <td>video/vc1</td>
                        <td>http://tools.ietf.org/html/rfc4425</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/video`</td>
        </tr>
    </table>

    此部件类型的实例包含视频文件。

    PresentationML 包允许包含零个或多个视频部件，每个部件都应是
    
    - Handout Master ([§13.3.3]), 
    - Notes Slide ([§13.3.5]), 
    - Notes Master ([§13.3.4]), 
    - Slide ([§13.3.8]), 
    - Slide Layout ([§13.3.9]), 
    - Slide Master ([§13.3.10]) 
    
    等等部件的显式关系的目标. 

    WordprocessingML 包允许包含零个或多个视频部件，每个部件都应是

    - Comments ([§11.3.2]), 
    - Endnotes ([§11.3.4]), 
    - Footer ([§11.3.6]), 
    - Footnotes ([§11.3.7]), 
    - Header ([§11.3.9]),  
    - Main Document ([§11.3.10]) 
    
    等等部件的显式关系的目标. 

    !!! info "Example"
        
        以下幻灯片部件关系项包含与视频部件的关系，该视频部件存储为文件 `E:\Video demo.avi`：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/video"
                Target="file:///E:\Video%20demo.avi" TargetMode="External"/>
        </Relationships>
        ```

    视频部件不存储为 XML； 相反，它涉及一个关系目标，即视频剪辑文件。
    
    视频部件可以位于包含关系部件的包的内部或外部（从语法上表达，关系元素的 TargetMode 属性可以是Internal或External）。

    视频部件不应与 ECMA-376 定义的其他部件有隐式或显式关系。
    
    想要互操作性的生产者应该使用以下标准格式：
    
    - video/mpeg ISO/IEC 13818

=== "英文"

    **Video Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>Any supported video type. </br></br>
                Note: Some example content types are: </br>
                <table border=1>
                    <tr>
                        <td>video/avi</td>
                        <td>http://www.the-labs.com/Video/odmlff2-avidef.pdf</td>
                    </tr>
                    <tr>
                        <td>video/mpg </td>
                        <td>ISO/IEC 13818</td>
                    </tr>
                    <tr>
                        <td>video/mpeg</td>
                        <td>ISO/IEC 13818</td>
                    </tr>
                    <tr>
                        <td>video/ogg</td>
                        <td>http://www.theora.org/doc/Theora.pdf</td>
                    </tr>
                    <tr>
                        <td>video/quicktime</td>
                        <td>http://developer.apple.com/documentation/QuickTime/</td>
                    </tr>
                    <tr>
                        <td>video/vc1</td>
                        <td>http://tools.ietf.org/html/rfc4425</td>
                    </tr>
                </table>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/video`</td>
        </tr>
    </table>

    An instance of this part type contains a video file. 

    A PresentationML package is permitted to contain zero or more Video parts, each of which shall be the target of an explicit relationship in a Handout Master ([§13.3.3]), Notes Slide ([§13.3.5]), Notes Master ([§13.3.4]), Slide ([§13.3.8]), Slide Layout ([§13.3.9]), or Slide Master ([§13.3.10]) part. A WordprocessingML package is permitted to contain zero or more Video parts, each of which shall be the target of an explicit relationship from a Comments ([§11.3.2]), Endnotes ([§11.3.4]), Footer ([§11.3.6]), Footnotes ([§11.3.7]), Header ([§11.3.9]), or Main Document ([§11.3.10]) part.

    !!! info "Example"
        
        The following Slide part-relationship item contains a relationship to a Video part, which is stored as the file E:\Video demo.avi:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/video"
                Target="file:///E:\Video%20demo.avi" TargetMode="External"/>
        </Relationships>
        ```

    A Video part is not stored as XML; instead, it involves a relationship target that is a video clip.
    
    A Video part can be located within or external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element can be Internal or External).

    A Video part shall not have implicit or explicit relationships to other parts defined by ECMA-376.
    
    A producer that wants interoperability should use the following standard format:
    
    - video/mpeg ISO/IEC 13818

## 15.3 超链接

=== "中文"

=== "英文"

    **Hyperlinks**

    <table border=1>
        <tr>
            <td>**Source Relationship**:</td>
            <td>`http://purl.oclc.org/ooxml/officeDocument/relationships/hyperlink`</td>
        </tr>
    </table>

    超链接可以作为关系存储在包中。 超链接应通过包含指定给定超链接的目的地的目标来标识。

    !!! info "Example"
    
        以下 WordprocessingML 脚注部件的关系部件包含一个关系，用于超链接`http://schemas.openxmlformats.org/wordprocessingml/`：

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/hyperlink"
                Target="http://schemas.openxmlformats.org/wordprocessingml/"
                TargetMode="External"/>
        </Relationships>
        ```

    超链接目标可以位于包含关系部件的包内部或外部（从语法上表达，关系元素的 TargetMode 属性可以是Internal或External）。

<!--链接定义-->
[§13.3.1]: ./chapter-13.md#1331-评论作者部件
[§13.3.2]: ./chapter-13.md#1332-评论部件
[§13.3.3]: ./chapter-13.md#1333-讲义母板部件
[§13.3.4]: ./chapter-13.md#1334-笔记母版部件
[§13.3.5]: ./chapter-13.md#1335-笔记幻灯片部件
[§13.3.6]: ./chapter-13.md#1336-演示部件
[§13.3.7]: ./chapter-13.md#1337-演示属性部件
[§13.3.8]: ./chapter-13.md#1338-幻灯片部件
[§13.3.9]: ./chapter-13.md#1339-幻灯片布局部件
[§13.3.10]: ./chapter-13.md#13310-幻灯片母版部件
[§13.3.11]: ./chapter-13.md#13311-幻灯片同步数据部件
[§13.3.12]: ./chapter-13.md#13312--用户已定义标签部件
[§13.3.13]: ./chapter-13.md#13313-视图属性部件

[§14]: ./chapter-14.md#14-drawingml
[§14.1]: ./chapter-14.md#141-drawingml-特定术语词汇表
[§14.2]: ./chapter-14.md#142-部件概览
[§14.2.1]: ./chapter-14.md#1421-图表部件
[§14.2.2]: ./chapter-14.md#1422-图表绘制部件
[§14.2.3]: ./chapter-14.md#1423-绘制颜色部件
[§14.2.4]: ./chapter-14.md#1424-绘制数据部件
[§14.2.5]: ./chapter-14.md#1425-绘制布局定义部件
[§14.2.6]: ./chapter-14.md#1426-绘制样式部件
[§14.2.7]: ./chapter-14.md#1427-主题部件
[§14.2.8]: ./chapter-14.md#1428-主题覆盖部件
[§14.2.9]: ./chapter-14.md#1429-表格样式部件

[§15]: #15-共享
[§15.1]: #151-共享术语词汇表
[§15.2]: #152-部件概览
[§15.2.1]: #1521-附加特性部件
[§15.2.2]: #1522-音频部件
[§15.2.3]: #1523-参考文献部件
[§15.2.4]: #1524-内容部件
[§15.2.5]: #1525-自定义xml数据存储部件
[§15.2.6]: #1526-自定义-xml-数据存储属性部件
[§15.2.7]: #1527-数字签名起源部件
[§15.2.8]: #1528-数字签名-xml-签名部件
[§15.2.9]: #1529-嵌入式控制持久化部件
[§15.2.10]: #15210-嵌入对象部件
[§15.2.11]: #15211-嵌入包部件
[§15.2.12]: #15212-文件属性部件
[§15.2.12.1]: #152121-核心文件属性部件
[§15.2.12.2]: #152122-自定义文件属性部件
[§15.2.12.3]: #152123-扩展文件属性部件
[§15.2.13]: #15213-字体部件
[§15.2.14]: #15214-图片部件
[§15.2.15]: #15215-打印机设置部件
[§15.2.16]: #15216-缩略图部件
[§15.2.17]: #15217-视频部件
[§15.3]: #153-超链接
