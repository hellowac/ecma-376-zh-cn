# 22.2 扩展属性

=== "中文"

    扩展属性(Extended properties)是一组预定义的元数据属性，适用于 Office Open XML 文档。 这些属性扩展了第 2 部分中定义的核心属性集：“开放包装约定”，这些属性对所有包都是通用的。
    
    扩展属性存储在扩展文件属性部件中：

    <table border=1>
        <tr>
            <td>Source Relationship</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/extendedProperties</td>
        </tr>
        <tr>
            <td>Content Type</td>
            <td>application/vnd.openxmlformats-officedocument.extended-properties+xml</td>
        </tr>
    </table>

    每个扩展属性都表示为扩展属性部件中的一个元素。 扩展属性元素是不可重复的，可以为空或省略。 如果省略所有扩展属性元素，则可以从文档中排除扩展属性部件。


    !!! info "Example"
    
        扩展文件属性部件示例：

        ```xml
        <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
        <Properties xmlns="http://…/extended-properties"
            xmlns:vt="http://…/docPropsVTypes">
        ..<Template>Sales Report.dotm</Template>
        ..<TotalTime>0</TotalTime>
        ..<Pages>1</Pages>
        ..<Words>166</Words>
        ..<Characters>948</Characters>
        ..<Application>Microsoft Office Word</Application>
        ..<DocSecurity>0</DocSecurity>
        ..<Lines>7</Lines>
        ..<Paragraphs>2</Paragraphs>
        ..<ScaleCrop>false</ScaleCrop>
        ..<Company>Northwind Traders</Company>
        ..<LinksUpToDate>false</LinksUpToDate>
        ..<CharactersWithSpaces>1112</CharactersWithSpaces>
        ..<SharedDoc>false</SharedDoc>
        ..<HyperlinksChanged>false</HyperlinksChanged>
        ..<AppVersion>12.0000</AppVersion>
        </Properties> 
        ```

=== "英文"

    **Extended Properties**

    Extended properties are a predefined set of metadata properties that are applicable to Office Open XML documents. These properties extend the set of core properties defined in Part 2: "Open Packaging Conventions" which are common to all packages.
    
    Extended properties are stored within an Extended File Properties part with:

    <table border=1>
        <tr>
            <td>Source Relationship</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/extendedProperties</td>
        </tr>
        <tr>
            <td>Content Type</td>
            <td>application/vnd.openxmlformats-officedocument.extended-properties+xml</td>
        </tr>
    </table>

    Each extended property is represented as an element in the extended properties part. Extended properties elements are non-repeatable and can be empty or omitted. If all extended property elements are omitted then the extended properties part can be excluded from a document.


    !!! info "Example"
    
        A sample extended file properties part:

    ```xml
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <Properties xmlns="http://…/extended-properties"
        xmlns:vt="http://…/docPropsVTypes">
    ..<Template>Sales Report.dotm</Template>
    ..<TotalTime>0</TotalTime>
    ..<Pages>1</Pages>
    ..<Words>166</Words>
    ..<Characters>948</Characters>
    ..<Application>Microsoft Office Word</Application>
    ..<DocSecurity>0</DocSecurity>
    ..<Lines>7</Lines>
    ..<Paragraphs>2</Paragraphs>
    ..<ScaleCrop>false</ScaleCrop>
    ..<Company>Northwind Traders</Company>
    ..<LinksUpToDate>false</LinksUpToDate>
    ..<CharactersWithSpaces>1112</CharactersWithSpaces>
    ..<SharedDoc>false</SharedDoc>
    ..<HyperlinksChanged>false</HyperlinksChanged>
    ..<AppVersion>12.0000</AppVersion>
    </Properties> 
    ```

## 22.2.1 概览

This subclause is informative.

- [22.2.2] Elements
- [22.2.2.1] Application (Application Name)
- [22.2.2.2] AppVersion (Application Version)
- [22.2.2.3] Characters (Total Number of Characters)
- [22.2.2.4] CharactersWithSpaces (Number of Characters (With Spaces))
- [22.2.2.5] Company (Name of Company)
- [22.2.2.6] DigSig (Digital Signature)
- [22.2.2.7] DocSecurity (Document Security)
- [22.2.2.8] HeadingPairs (Heading Pairs)
- [22.2.2.9] HiddenSlides (Number of Hidden Slides)
- [22.2.2.10] HLinks (Hyperlink List)
- [22.2.2.11] HyperlinkBase (Relative Hyperlink Base)
- [22.2.2.12] HyperlinksChanged (Hyperlinks Changed)
- [22.2.2.13] Lines (Number of Lines)
- [22.2.2.14] LinksUpToDate (Links Up-to-Date)
- [22.2.2.15] Manager (Name of Manager)
- [22.2.2.16] MMClips (Total Number of Multimedia Clips)
- [22.2.2.17] Notes (Number of Slides Containing Notes)
- [22.2.2.18] Pages (Total Number of Pages)
- [22.2.2.19] Paragraphs (Total Number of Paragraphs)
- [22.2.2.20] PresentationFormat (Intended Format of Presentation)
- [22.2.2.21] Properties (Application Specific File Properties)
- [22.2.2.22] ScaleCrop (Thumbnail Display Mode)
- [22.2.2.23] SharedDoc (Shared Document)
- [22.2.2.24] Slides (Slides Metadata Element)
- [22.2.2.25] Template (Name of Document Template)
- [22.2.2.26] TitlesOfParts (Part Titles)
- [22.2.2.27] TotalTime (Total Edit Time Metadata Element)
- [22.2.2.28] Words (Word Count)

End of informative text.

## 22.2.2 元素

=== "中文"

    以下元素指定此命名空间的内容：

=== "英文"

    **Elements**

    The following elements specify the contents of this namespace:

### 22.2.2.1 Application (应用名称)

=== "中文"

    该元素指定创建该文档的应用程序的名称。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **Application (Application Name)**

    This element specifies the name of the application that created this document.

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.2 AppVersion (应用版本)

=== "中文"

    该元素指定生成该文档的应用程序的版本。

    该元素的内容应采用 XX.YYYY 的形式，其中 X 和 Y 代表数值，否则该文档应被视为不合格。

    !!! info "Note"

        该元素的内容并不代表绝对值，而是限定Application元素的内容以区分同一生产者的不同版本。 应用程序应仅以提供信息的方式使用此信息（作为文档元数据）。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **AppVersion (Application Version)**

    This element specifies the version of the application which produced this document.

    The content of this element shall be of the form XX.YYYY where X and Y represent numerical values, or the document shall be considered non-conformant.

    [Note: The contents of this element do not represent absolute values, but rather qualify the contents of the Application element to differentiate between different versions of the same producer. Applications should use this information in an informative manner only (as document metadata). end note]

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.3 Characters (字符总数)

=== "中文"

    该元素指定文档中的字符总数。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Characters (Total Number of Characters)**


    This element specifies the total number of characters in a document.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.4 CharactersWithSpaces (字符数（带空格）)

=== "中文"

    该元素指定本文档中字符数（包括空格）的最后计数。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **CharactersWithSpaces (Number of Characters (With Spaces))**

    This element specifies the last count of the number of characters (including spaces) in this document.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.5 Company (公司名称)

=== "中文"

    该元素指定与文档关联的公司名称。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **Company (Name of Company)**

    This element specifies the name of a company associated with the document.

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.6 DigSig (数字签名)

=== "中文"

    该元素包含数字签名文档的签名。

    !!! info "Note"

        此属性是遗留文档用来存储其二进制表示的数字签名的机制，应避免使用第 2 部分中定义的明确定义的机制。此属性的任何使用都应仅用于遗留兼容性，并且是 应用程序定义的。

    !!! info "Note"

        该元素内容模型 (CT_DigSigBlob) 的 W3C XML 架构定义位于 [§A.6.2] 中。

=== "英文"

    **DigSig (Digital Signature)**

    This element contains the signature of a digitally signed document.

    [Note: This property is a mechanism used by legacy documents to store the digital signature of its binary representation, and should be avoided in favor of the well-defined mechanism defined in Part 2. Any use of this property should be for legacy compatibility only, and is application-defined. end note]

    [Note: The W3C XML Schema definition of this element’s content model (CT_DigSigBlob) is located in §A.6.2. end note]

### 22.2.2.7 DocSecurity (文档安全)

=== "中文"

    该元数据元素将文档的安全级别指定为数值。 文档安全性定义为：

    <table>
        <thead>
            <tr>
                <th>**文档安全**</th>
                <th>**安全级别**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>文档受密码保护。</td>
            </tr>
            <tr>
                <td>2</td>
                <td>建议以只读方式打开文档。</td>
            </tr>
            <tr>
                <td>3</td>
                <td>文档强制以只读方式打开。</td>
            </tr>
            <tr>
                <td>4</td>
                <td>文档已锁定以进行注释。</td>
            </tr>
        </tbody>
    </table>

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **DocSecurity (Document Security)**

    This metadata element specifies the security level of a document as a numeric value. Document security is defined as:

    <table>
        <thead>
            <tr>
                <th>**DocSecurity**</th>
                <th>**Security Level**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>Document is password protected.</td>
            </tr>
            <tr>
                <td>2</td>
                <td>Document is recommended to be opened as read-only.</td>
            </tr>
            <tr>
                <td>3</td>
                <td>Document is enforced to be opened as read-only.</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Document is locked for annotation.</td>
            </tr>
        </tbody>
    </table>

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.8 HeadingPairs (标题对)

=== "中文"

    **标题对**(Heading pairs)指示文档部件的分组以及每组中的部件数量。 这些部件不是文档部件，而是文档部件的概念表示。

    !!! info "Example"

        由三张具有应用主题的幻灯片组成的演示文稿可以具有以下 HeadingPairs 表示形式：

        ```xml
        <HeadingPairs>
            <vt:vector size="4" baseType="variant">
                <vt:variant>
                    <vt:lpstr>Theme</vt:lpstr>
                </vt:variant>
                <vt:variant>
                    <vt:i4>1</vt:i4>
                </vt:variant>
                <vt:variant>
                    <vt:lpstr>Slide Titles</vt:lpstr>
                </vt:variant>
                <vt:variant>
                    <vt:i4>3</vt:i4>
                </vt:variant>
            </vt:vector>
        </HeadingPairs>
        ```

    !!! info "Note"

        该元素内容模型 (CT_VectorVariant) 的 W3C XML 模式定义位于 [§A.6.2] 中。

=== "英文"

    **HeadingPairs (Heading Pairs)**

    Heading pairs indicates the grouping of document parts and the number of parts in each group. These parts are not document parts but conceptual representations of document sections.

    !!! info "Example"

        A presentation composing of three slides with an applied theme can have the following HeadingPairs representation:

        ```xml
        <HeadingPairs>
            <vt:vector size="4" baseType="variant">
                <vt:variant>
                    <vt:lpstr>Theme</vt:lpstr>
                </vt:variant>
                <vt:variant>
                    <vt:i4>1</vt:i4>
                </vt:variant>
                <vt:variant>
                    <vt:lpstr>Slide Titles</vt:lpstr>
                </vt:variant>
                <vt:variant>
                    <vt:i4>3</vt:i4>
                </vt:variant>
            </vt:vector>
        </HeadingPairs>
        ```

        !!! info "Note"

            The W3C XML Schema definition of this element’s content model (CT_VectorVariant) is located in [§A.6.2].

### 22.2.2.9 HiddenSlides (隐藏幻灯片数量)

=== "中文"

    此元素指定演示文稿文档中隐藏幻灯片的数量。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **HiddenSlides (Number of Hidden Slides)**

    This element specifies the number of hidden slides in a presentation document.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.10 HLinks (超链接列表)

=== "中文"

    该元素指定上次保存时文档中的超链接集。

    !!! info "Note"

        该元素内容模型 (CT_VectorVariant) 的 W3C XML 架构定义位于 [§A.6.2] 中。

=== "英文"

    **HLinks (Hyperlink List)**

    This element specifies the set of hyperlinks that were in this document when last saved.

    [Note: The W3C XML Schema definition of this element’s content model (CT_VectorVariant) is located in §A.6.2. end note]

### 22.2.2.11 HyperlinkBase (相对超链接基础)

=== "中文"

    该元素指定用于评估本文档中的相对超链接的基本字符串。
    
    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **HyperlinkBase (Relative Hyperlink Base)**

    This element specifies the base string used for evaluating relative hyperlinks in this document.
    
    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.12 HyperlinksChanged (超链接已更改)

=== "中文"

    该元素指定该部件中的一个或多个超链接是由生产者在该部件中专门更新的。 下一个打开本文档的制作者应使用本部件规定的新超链接来更新超链接关系。
    
    该元素的可能值由 W3C XML 架构布尔数据类型定义。

=== "英文"

    **linksChanged (Hyperlinks Changed)**
    
    This element specifies that one or more hyperlinks in this part were updated exclusively in this part by a producer. The next producer to open this document shall update the hyperlink relationships with the new hyperlinks specified in this part.
    
    The possible values for this element are defined by the W3C XML Schema boolean datatype.

### 22.2.2.13 Lines (行数)

=== "中文"

    该元素指定合格生产者最后一次保存文档时的总行数（如果适用）。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Lines (Number of Lines)**

    This element specifies the total number of lines in a document when last saved by a conforming producer if applicable.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.14 LinksUpToDate (最新链接)

=== "中文"

    该元素指示文档中的超链接是否是最新的。 将此元素设置为 TRUE 以指示超链接已更新。 将此元素设置为 FALSE 以指示超链接已过时。

    该元素的可能值由 W3C XML 架构布尔数据类型定义。

=== "英文"

    **LinksUpToDate (Links Up-to-Date)**

    This element indicates whether hyperlinks in a document are up-to-date. Set this element to TRUE to indicate that hyperlinks are updated. Set this element to FALSE to indicate that hyperlinks are outdated.

    The possible values for this element are defined by the W3C XML Schema boolean datatype.

### 22.2.2.15 Manager (主管姓名)

=== "中文"

    该元素指定与文档关联的主管的姓名。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **Manager (Name of Manager)**

    This element specifies the name of a supervisor associated with the document.

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.16 MMClips (多媒体剪辑总数)

=== "中文"

    此元素指定文档中存在的声音或视频剪辑的总数。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **MMClips (Total Number of Multimedia Clips)**

    This element specifies the total number of sound or video clips that are present in the document.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.17 Notes (包含注释/笔记的幻灯片数量)

=== "中文"

    此元素指定演示文稿中包含注释的幻灯片的数量。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Notes (Number of Slides Containing Notes)**

    This element specifies the number of slides in a presentation containing notes.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.18 Pages (总页数)

=== "中文"

    该元素指定文档的总页数（如果适用）。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Pages (Total Number of Pages)**

    This element specifies the total number of pages of a document if applicable.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.19 Paragraphs (段落总数)

=== "中文"

    该元素指定文档中找到的段落总数（如果适用）。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Paragraphs (Total Number of Paragraphs)**

    This element specifies the total number of paragraphs found in a document if applicable.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.20 PresentationFormat (演示文稿的预期格式)

=== "中文"

    该元素指定演示文稿文档的预期格式。 例如，打算在视频上显示的演示具有 PresentationFormat “Vedio”。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **PresentationFormat (Intended Format of Presentation)**

    This element specifies the intended format for a presentation document. For example, a presentation intended to be shown on video has PresentationFormat "Video".

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.21 Properties (应用程序特定的文件属性)

=== "中文"

    该元素指定文档的应用程序属性。 对于字符串类型的属性，NCR 转义格式 (`_xHHHH_`) 用于任何无效的 XML 字符。

    [Note: 该元素内容模型 (CT_Properties) 的 W3C XML 模式定义位于 [§A.6.2] 中。 end note]

=== "英文"

    **Properties (Application Specific File Properties)**

    This element specifies the application properties of a document. For properties of type string, NCR escape format (_xHHHH_) is used for any invalid XML characters.

    [Note: The W3C XML Schema definition of this element’s content model (CT_Properties) is located in §A.6.2. end note]

### 22.2.2.22 ScaleCrop (缩略图显示模式)

=== "中文"

    该元素指示文档缩略图的显示模式。 将此元素设置为 TRUE 可缩放文档缩略图以适应显示。 将此元素设置为 FALSE 可以裁剪文档缩略图，从而仅显示适合显示屏的部分。

    该元素的可能值由 W3C XML 架构布尔数据类型定义。

=== "英文"

    **ScaleCrop (Thumbnail Display Mode)**

    This element indicates the display mode of the document thumbnail. Set this element to TRUE to enable scaling of the document thumbnail to the display. Set this element to FALSE to enable cropping of the document thumbnail to show only sections that fits the display.

    The possible values for this element are defined by the W3C XML Schema boolean datatype.

### 22.2.2.23 SharedDoc (共享文档)

=== "中文"

    该元素指示该文档当前是否在多个生产者之间共享。 如果此元素设置为 TRUE，则生产者在更新文档时应小心。

    该元素的可能值由 W3C XML 架构布尔数据类型定义。

=== "英文"

    **SharedDoc (Shared Document)**

    This element indicates if this document is currently shared between multiple producers. If this element is set to TRUE, producers should take care when updating the document.

    The possible values for this element are defined by the W3C XML Schema boolean datatype.

### 22.2.2.24 Slides (幻灯片元数据元素)

=== "中文"

    此元素指定演示文档中幻灯片的总数。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **Slides (Slides Metadata Element)**

    This element specifies the total number of slides in a presentation document.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.25 Template (文档模板名称)

=== "中文"

    此元素指定外部文档模板的名称，该模板包含用于创建当前文档的格式和样式信息。

    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **Template (Name of Document Template)**

    This element specifies the name of an external document template containing format and style information used to create the current document.

    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.2.2.26 TitlesOfParts (部件标题)

=== "中文"

    该元素指定每个文档的标题。 这些部件不是文档部件，而是文档部件的概念表示。

    !!! info "Example"

        由应用主题“货币(Currency)”的三张幻灯片组成的演示文稿可以具有以下 TitlesofParts 表示形式：

        ```xml
        <TitlesofParts>
            <vt:vector size="4" baseType="lpstr">
                <vt:lpstr>Currency</vt:lpstr>
                <vt:lpstr>Slide 1</vt:lpstr>
                <vt:lpstr>Slide 2</vt:lpstr>
                <vt:lpstr>Slide 3</vt:lpstr>
            </vt:vector>
        </TitlesofParts>
        ```

    !!! info "Note"

        该元素内容模型 (CT_VectorLpstr) 的 W3C XML 架构定义位于 §A.6.2 中。

=== "英文"

    **TitlesOfParts (Part Titles)**

    This element specifies the title of each document. These parts are not document parts but conceptual representations of document sections.

    !!! info "Example"

        A presentation composing of three slides with an applied theme "Currency" can have the following TitlesofParts representation:

        ```xml
        <TitlesofParts>
            <vt:vector size="4" baseType="lpstr">
                <vt:lpstr>Currency</vt:lpstr>
                <vt:lpstr>Slide 1</vt:lpstr>
                <vt:lpstr>Slide 2</vt:lpstr>
                <vt:lpstr>Slide 3</vt:lpstr>
            </vt:vector>
        </TitlesofParts>
        ```

    !!! info "Note"

        The W3C XML Schema definition of this element’s content model (CT_VectorLpstr) is located in §A.6.2. 

### 22.2.2.27 TotalTime (总编辑时间元数据元素)

=== "中文"

    编辑文档的总时间。 默认时间单位是分钟。

    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **TotalTime (Total Edit Time Metadata Element)**

    Total time that a document has been edited. The default time unit is minutes.

    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.2.2.28 Words (字数)

=== "中文"

    该元素指定上次保存时文档中包含的总字数。

    此元素的可能值由 W3C XML Schema int 数据类型定义

=== "英文"

    **Words (Word Count)**

    This element specifies the total number of words contained in a document when last saved.

    The possible values for this element are defined by the W3C XML Schema int datatype
