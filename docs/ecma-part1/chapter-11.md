# 11. WordprocessingML

=== "中文"

    本条款包含特定于 WordprocessingML 的关系项和部件的规范。 [§15.2] 中指定了可能出现在 WordprocessingML 文档中但不是 WordprocessingML 特定的部件。 除非明确说明，否则本条款中对关系项目、内容类型项目和部件的所有引用均指 WordprocessingML ZIP 项目。

=== "英文"

    **WordprocessingML**

    This clause contains specifications for relationship items and parts that are specific to WordprocessingML. Parts that can occur in a WordprocessingML document, but are not WordprocessingML-specific, are specified in [§15.2]. Unless stated explicitly, all references to relationship items, content-type items, and parts in this clause refer to WordprocessingML ZIP items.

## 11.1 WordprocessingML特定术语表

**Glossary of WordprocessingML-Specific Terms**

=== "中文"

    在WordprocessingML文档的上下文中使用以下术语：
    
    **文档设置(document setting)** —— 影响给定文档处理的文档级属性，影响当前文档的外观和行为，以及存储的文档级状态。
    
    **文档构建块(document building block)** —— 模板中可重用的元素。[注：此类元素包括样板文本、封面页、方程、页脚、页眉、表格、文本框和水印等。]
    
    **词汇表文档** —— 用于存储可重用的富WordprocessingML内容片段的附加WordprocessingML文档故事。它被称为词汇表文档，因为这个故事包含一个或多个可以通过名称索引和提取的片段，就像词汇表中的条目一样。
    
    **主文档(master document)** —— 一个或多个子文档的父文档。[注：主文档可用于管理多部件文档，如拥有多个章节的书籍。在这种情况下，主文档可能包含封面页、前言、目录和交叉引用索引，而每一章和附录则分别位于自己的子文档中。]
    
    **节(section)** —— 文档的一个部件，在其中可以设置某些页面格式选项。[注：创建新节是为了更改行编号、列数或页眉和页脚等属性。]
    
    **子文档(subdocument)** —— 主文档的一部件。[注：在一本书中，一章或附录可能是一个子文档。]
    
    **补充文档存储位置(supplementary document storage location)** —— WordprocessingML文档中的一个部件，WordprocessingML内容的片段可以存储在此处，与打印页面分开。另请参见词汇表文档
    
    **模板(template)** —— 用于创建其他文档的文档模式。模板可以包含文本、格式设置和图形等内容，使得基于它的文档自动可以访问这些元素。

=== "英文"
    
    The following terms are used in the context of a WordprocessingML document:
    
    **document setting** — A document-level property that affects the handling of a given document, and influences the appearance and behavior of the current document, as well as the stored document-level state.
    
    **document building block** — A reusable element in a template. [Note: Such elements include boilerplate text, cover pages, equations, footers, headers, tables, text boxes, and watermarks. end note]
    
    **glossary document** — An additional WordprocessingML document story used to store reusable fragments of rich WordprocessingML content. It is called the glossary document as this story contains one or more fragments that can be indexed and extracted by name, like items in a glossary.
    
    **master document** — A document that is the parent of one or more subdocuments. [Note: A master document can be used to manage a multipart document, such as a book having several chapters. In such as case, the master document might contain the cover page, front matter, table of contents, and cross-reference index, while each chapter and appendix resides in its own subdocument. end note]
    
    **section** — A portion of a document in which certain page formatting options can be set. [Note: A new section is created to change such properties as line numbering, number of columns, or headers and footers. end note] 
    
    **subdocument** — A piece of a master document. [Note: A chapter or appendix might be a subdocument in a book. end note]
    
    **supplementary document storage location** — A part within a WordprocessingML document in which fragments of WordprocessingML content can be stored separate from the printed page. See also glossary document 
    
    **template** — A document that is a pattern for creating other documents. A template can contain text, formatting, and graphics, among other things, such that documents based on it automatically have access to hese elements.

## 11.2 包结构

**Package Structure**

=== "中文"

    WordprocessingML打包应包含一个包关系项和一个内容类型项。包关系项应与以下类型的靶标隐含关系：
    
    - 一个主文档部件（[§11.3.10]）
    
    包关系项允许与以下类型的靶标有隐含关系：
    
    - 数字签名源（[§15.2.7]）
    - 文件属性部件（[§15.2.12]）（应用定义的文件属性、核心文件属性和自定义文件属性），视情况而定。
    - 缩略图（[§15.2.16]）。
    
    部件之间的必需和可选关系在§16.1及其下属条款中定义。
    
    [示例：以下包代表了ECMA-376定义的最小符合要求的WordprocessingML包：
    
    首先，必须定义关系部件和主文档部件（唯一必需的部件）的内容类型（物理上位于包中的/[Content_Types].xml）：
    
    ```xml
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
        <Default Extension="rels"
            ContentType="application/vnd.openxmlformats-package.relationships+xml"/>
        <Override PartName="/document.xml" 
            ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml"/>
    </Types>
    ```
    
    接下来，必须定义单一必需的关系（指向主文档部件的包级关系）（物理上位于包中的/_rels/.rels）：
    
    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId1"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument"
            Target="document.xml"/>
    </Relationships>
    ```
    
    最后，必须定义主文档部件的最小内容（物理上位于包中的/document.xml）：
    
    ```xml
    <w:document xmlns:w="...">
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    示例结束]

    [示例: 设想一个WordprocessingML文档是ECMA-376标准的早期草案。下面是一个示例，展示了该文档的ZIP包中可能使用的分层文件夹结构。如图所示，其中一个部件——主文档（存储在ZIP项/word/document.xml中）拥有自己的关系项:

    ```text
    /[Content_Types].xml             Content-type item
    /_rels/.rels                     Package-relationship item
    /docProps/app.xml                Application-Defined File Properties part
    /docProps/core.xml               Core File Properties part
    /word/document.xml               Main Document part
    /word/_rels/document.xml.rels    Part-relationship item
    /word/comments.xml               Comment part
    /word/endnotes.xml               Endnotes part
    /word/fontTable.xml              Font Table part
    /word/footer1.xml                Footer parts
    /word/footer2.xml
    /word/footer3.xml
    /word/footer4.xml
    /word/footnotes.xml              Footnotes part
    /word/header1.xml                Header parts
    /word/header2.xml
    /word/header3.xml
    /word/header4.xml
    /word/header5.xml
    /word/header6.xml
    /word/numbering.xml              Numbering Definitions part
    /word/settings.xml               Document Settings part
    /word/styles.xml                 Style Definitions part
    /word/theme/theme1.xml           Theme part
    ```

    包关系项的内容如下所示:

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId3"
            Type="http://…/extended-properties" Target="docProps/app.xml"/>
        <Relationship Id="rId2"
            Type="http://…/core-properties" Target="docProps/core.xml"/>
        <Relationship Id="rId1"
            Type="http://…/officeDocument" Target="word/document.xml"/>
    </Relationships>
    ```

    end example]

=== "英文"

    A WordprocessingML package shall contain a package-relationship item and a content-type item. The packagerelationship item shall have implicit relationships with targets of the following type:

    - One Main Document part ([§11.3.10])

    The package-relationship item is permitted to have implicit relationships with targets of the following type:

    - Digital Signature Origin ([§15.2.7])
    - File Property parts ([§15.2.12])(Application-Defined File Properties, Core File Properties, and Custom File Properties), as appropriate.
    - Thumbnail ([§15.2.16]).
    
    The required and optional relationships between parts are defined in §16.1 and its subordinate clauses.

    [Example: The following package represents the minimal conformant WordprocessingML package as defined by ECMA-376:
    
    First, the content type for relationship parts and the Main Document part (the only required part) must be defined (physically located at /[Content_Types].xml in the package):

    ```xml
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
        <Default Extension="rels"
            ContentType="application/vnd.openxmlformats-package.relationships+xml"/>
        <Override PartName="/document.xml" 
            ContentType="application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml"/>
    </Types>
    ```

    Next, the single required relationship (the package-level relationship to the Main Document part) must be defined (physically located at /_rels/.rels in the package):

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument"
            Target="document.xml"/>
    </Relationships>
    ```

    Finally, the minimum content for the Main Document part must be defined (physically located at /document.xml in the package):
    
    ```xml
    <w:document xmlns:w="…">
        <w:body>
            <w:p/>
        </w:body>
    </w:document>
    ```
    
    end example]

    [Example: Consider a WordprocessingML document that is an early draft of ECMA-376. Here’s an example of the hierarchical folder structure that might be used for the ZIP items in the package for that document. As shown, one part, Main Document (stored in the ZIP item /word/document.xml), has its own relationship item:

    ```text
    /[Content_Types].xml             Content-type item
    /_rels/.rels                     Package-relationship item
    /docProps/app.xml                Application-Defined File Properties part
    /docProps/core.xml               Core File Properties part
    /word/document.xml               Main Document part
    /word/_rels/document.xml.rels    Part-relationship item
    /word/comments.xml               Comment part
    /word/endnotes.xml               Endnotes part
    /word/fontTable.xml              Font Table part
    /word/footer1.xml                Footer parts
    /word/footer2.xml
    /word/footer3.xml
    /word/footer4.xml
    /word/footnotes.xml              Footnotes part
    /word/header1.xml                Header parts
    /word/header2.xml
    /word/header3.xml
    /word/header4.xml
    /word/header5.xml
    /word/header6.xml
    /word/numbering.xml              Numbering Definitions part
    /word/settings.xml               Document Settings part
    /word/styles.xml                 Style Definitions part
    /word/theme/theme1.xml           Theme part
    ```

    The package-relationship item contains the following:

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId3"
            Type="http://…/extended-properties" Target="docProps/app.xml"/>
        <Relationship Id="rId2"
            Type="http://…/core-properties" Target="docProps/core.xml"/>
        <Relationship Id="rId1"
            Type="http://…/officeDocument" Target="word/document.xml"/>
    </Relationships>
    ```

    end example]

## 11.3 部件概览

=== "中文"

    从属于该子条款的子条款详细描述了特定于 WordprocessingML 的每个部件类型。
    
    !!! note info "注意"
    
        为方便起见，下表总结了这些子章节的信息：

        | 部件(Part)                              | 关系目标                                                        | 根节点           | 参考.      |
        | --------------------------------------- | --------------------------------------------------------------- | ---------------- | ---------- |
        | 替代格式导入(Alternative Format Import) | Comments, Endnotes, Footer, Footnotes, Header, or Main Document | Not applicable   | [§11.3.1]  |
        | 注释(Comments)                          | 主文档的术语表文档(Glossary Document)                           | comments         | [§11.3.2]  |
        | 文档设置(Document Settings)             | 主文档的术语表文档(Glossary Document)                           | settings         | [§11.3.3]  |
        | 尾注(Endnotes)                          | 主文档的术语表文档(Glossary Document)                           | endnotes         | [§11.3.4]  |
        | 字体表(Font Table)                      | 主文档的术语表文档(Glossary Document)                           | fonts            | [§11.3.5]  |
        | 页脚(Footer)                            | 主文档的术语表文档(Glossary Document)                           | ftr              | [§11.3.6]  |
        | 脚注(Footnotes)                         | 主文档的术语表文档(Glossary Document)                           | footnotes        | [§11.3.7]  |
        | 术语表文档(Glossary Document)           | 主文档(Main Document)                                           | glossaryDocument | [§11.3.8]  |
        | 标头(Header)                            | 主文档的术语表文档(Glossary Document)                           | hdr              | [§11.3.9]  |
        | 主文档(Main Document)                   | WordprocessingML 包                                             | document         | [§11.3.10] |
        | 编号定义(Numbering Definitions)         | 主文档的术语表文档(Glossary Document)                           | numbering        | [§11.3.11] |
        | 样式定义(Style Definitions)             | 主文档的术语表文档(Glossary Document)                           | styles           | [§11.3.12] |
        | 网页设置(Web Settings)                  | 主文档的术语表文档(Glossary Document)                           | webSettings      | [§11.3.13] |

=== "英文"

    **Part Summary**

    The subclauses subordinate to this one describe in detail each of the part types specific to WordprocessingML.
    
    !!! note info "注意"
    
        For convenience, information from those subclauses is summarized in the following table:

        | Part                      | Relationship Target of                                          | Root Element     | Ref.       |
        | ------------------------- | --------------------------------------------------------------- | ---------------- | ---------- |
        | Alternative Format Import | Comments, Endnotes, Footer, Footnotes, Header, or Main Document | Not applicable   | [§11.3.1]  |
        | Comments                  | Glossary Document or Main Document                              | comments         | [§11.3.2]  |
        | Document Settings         | Glossary Document or Main Document                              | settings         | [§11.3.3]  |
        | Endnotes                  | Glossary Document or Main Document                              | endnotes         | [§11.3.4]  |
        | Font Table                | Glossary Document or Main Document                              | fonts            | [§11.3.5]  |
        | Footer                    | Glossary Document or Main Document                              | ftr              | [§11.3.6]  |
        | Footnotes                 | Glossary Document or Main Document                              | footnotes        | [§11.3.7]  |
        | Glossary Document         | Main Document                                                   | glossaryDocument | [§11.3.8]  |
        | Header                    | Glossary Document or Main Document                              | hdr              | [§11.3.9]  |
        | Main Document             | WordprocessingML package                                        | document         | [§11.3.10] |
        | Numbering Definitions     | Glossary Document or Main Document                              | numbering        | [§11.3.11] |
        | Style Definitions         | Glossary Document or Main Document                              | styles           | [§11.3.12] |
        | Web Settings              | Glossary Document or Main Document                              | webSettings      | [§11.3.13] |

### 11.3.1 替代格式导入部件

=== "中文"

    **替代格式导入部件**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                    任何基于文本的内容，其支持方式由应用程序定义。[注：可能支持的格式示例包括：<br/>
                    . Text = text/plain<br/>
                    . HTML = text/html<br/>
                    . WordprocessingML=application/vnd.openxmlformats-officedocument.wordprocessingml.document<br/>
                    . XHTML = application/xhtml+xml<br/>
                    end note]
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>不适用</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk</td>
        </tr>
    </table>

    替代格式导入部件允许将在上述指定的替代格式中指定的内容直接嵌入到WordprocessingML文档中，以便将该内容迁移到WordprocessingML格式。
    
    任何允许包含p元素的文档部件也可以包含一个altChunk元素，其id属性引用一个关系。该关系应指向包中的一个部件，该部件包含要导入到此WordprocessingML文档中的内容。
    
    一个包可以包含零个或多个替代格式导入部件，每个部件都应有一个对应的替代格式文件，该文件是从Comments（[§11.3.2]）、Endnotes（[§11.3.4]）、Footer（[§11.3.6]）、Footnotes（[§11.3.7]）、Header（[§11.3.9]）或Main Document（[§11.3.10]）部件中的一个显式关系的目标。此关系应在源部件中使用适当的XML语法（即在altChunk元素的id属性中）明确引用其关系ID，并且在没有此类引用的情况下存在此关系将被视为不符合规范。
    
    ECMA-376没有指定如何创建包含替代格式导入关系和altChunk元素的WordprocessingML包。
    
    对于此部件，应用程序需要满足以下要求：
    
    - 仅作为符合规范的消费者的应用程序不得拒绝包含一个或多个此部件实例的文档。
    - 既是符合规范的消费者又是生产者的应用程序不得拒绝包含此部件实例的文档，并且在充当生产者之前应将此部件的任何实例转换/删除。
    - 仅作为符合规范的生产者的应用程序不得创建包含替代格式导入关系和元素的WordprocessingML包。
    
    [注：替代格式导入机制提供了一次性转换功能。生产者可以具有一个扩展，允许其生成包含这些关系和元素的包，但在符合模式下运行时不会这样做。结束注]
    
    [示例：以下Main Document部件关系项包含对替代格式导入部件的关系：
    
    ```xml
    <Relationships xmlns="…">
    <Relationship Id="rId5"
        Type="http://…/aFChunk" Target="Demo.html"
        TargetMode="Internal"/>
    </Relationships>
    ```
    
    Main Document部件包含以下XML片段：
    
    ```xml
    <w:body>
    …
    <w:p/>
    <w:altChunk r:id="rId5"/>
    <w:p/>
    …
    </w:body>
    ```
    
    这将导致Demo.html的全部内容被转换并带入文档的该位置（假设应用程序支持此WordprocessingML文件中的Demo.html的内容类型）。结束示例]
    
    替代格式导入部件应位于包含关系部件的包中（在语法上表达，关系元素的TargetMode属性应为Internal）。
    
    替代格式导入部件不得与ECMA-376定义的任何部件具有显式或隐式的关系。
    
    希望实现互操作性的生产者应使用以下标准格式之一：
    
    - **HTML** - application/text/html
    - **TEXT** - application/text/plain（UTF-16）

=== "英文"

    **Alternative Format Import Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                    <p>Any text-based content, support for which is application-defined. [Note: Some examples of formats which might be supported include:</p>
                    <p>. Text = text/plain</p>
                    <p>. HTML = text/html</p>
                    <p>. WordprocessingML=application/vnd.openxmlformats-officedocument.wordprocessingml.document</p>
                    <p>. XHTML = application/xhtml+xml</p>
                    <p>end note]</p>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>not applicable</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk</td>
        </tr>
    </table>
    
    An alternative format import part allows content specified in an alternate format specified above to be embedded directly in a WordprocessingML document in order to allow that content to be migrated to the WordprocessingML format.
    
    Any document part that permits a p element can also contain an altChunk element, whose id attribute refers to a relationship. That relationship shall target a part within the package, which contains the content to be imported into this WordprocessingML document.
    
    A package is permitted to contain zero or more Alternative Format Import parts, each of which shall have a corresponding alternate format file that is the target of an explicit relationship from a Comments ([§11.3.2]), Endnotes ([§11.3.4]), Footer ([§11.3.6]), Footnotes ([§11.3.7]), Header ([§11.3.9]), or Main Document ([§11.3.10]) part. This relationship shall be explicitly referenced using its relationship ID in the source part using the appropriate XML syntax (i.e.; in the id attribute on the altChunk element), and the presence of this relationship without such a reference shall be considered non-conformant.
    
    ECMA-376 does not specify how one might create a WordprocessingML package that contains Alternative Format Import relationships and altChunk elements.
    
    The following requirements are applied to applications with respect to this part:
    
    - An application that is solely a conforming consumer shall not reject documents containing one or more instances of this part
    - An application that is both a conforming consumer and producer shall not reject documents containing instances of this part and shall convert/remove any instances of this part before acting as producer.
    - An application that is solely a conforming producer shall not create a WordprocessingML package that contains Alternative Format Import relationships and elements.
    
    [Note: The Alternative Format Import machinery provides a one-time conversion facility. A producer could have an extension that allows it to generate a package containing these relationships and elements, yet when run in conforming mode, does not do so. end note]
    
    [Example: The following Main Document part-relationship item contains a relationship to an Alternative Format Import part:
    
    ```xml
    <Relationships xmlns="…">
    <Relationship Id="rId5"
        Type="http://…/aFChunk" Target="Demo.html"
        TargetMode="Internal"/>
    </Relationships>
    ```
    
    The Main Document part contains the following XML fragment:
    
    ```xml
    <w:body>
    …
    <w:p/>
    <w:altChunk r:id="rId5"/>
    <w:p/>
    …
    </w:body>
    ```
    
    which results in the entire contents of Demo.html being converted and brought into the document at that point (assuming that the content type of Demo.html is supported by the application consuming this WordprocessingML file). end example]
    
    An Alternative Format Import part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    An Alternative Format Import part shall not have any explicit or implicit relationships to parts defined by ECMA-376.
    
    A producer that wants interoperability should use one of the following standard formats:
    
    - **HTML** - application/text/html
    - **TEXT** - application/text/plain (UTF-16)


### 11.3.2 注释部件

=== "中文"
    
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.comments+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/comments</td>
        </tr>
    </table>

    该部件类型的一个实例包含文档中每个注释的信息。
    
    一个包不应包含超过两个注释部件。如果存在，该部件的一个实例应是主文档（[§11.3.10]）部件的隐式关系对象，另一个部件应是词汇表文档（[§11.3.8]）部件的隐式关系对象。
    
    [示例：以下的主文档部件关系项包含对作为 ZIP 项 comment.xml 存储的 Contents 部件的关系：
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId93"
            Type="http://…/comments" Target="comments.xml"/>
    </Relationships>
    ```
    
    结束示例]
    
    注释部件的根元素应为 comments。
    
    [示例：
    
    ```xml
    <w:comments … >
        <w:comment>
            …
        </w:comment>
        …
    </w:comments>
    ```
    
    结束示例]
    
    主文档部件中注释的 XML 标记使用 commentReference 元素。
    
    [示例：考虑以下情况，主文档部件中包含文本“…在标准中。”，并且在句号后立即插入注释：
    
    ```xml
    <w:p …>
        …
        <w:r>
            <w:t>…在标准中。</w:t>
        </w:r>
        <w:r>
            <w:commentReference w:id="1"/>
        </w:r>
    </w:p>
    ```
    
    结束示例]
    
    每个注释在注释部件中都有一个对应的注释元素，其中包含注释的文本。
    
    [示例：注释的文本为“This is my comment.”：
    
    ```xml
    <w:comments xmlns:w="…">
        <w:comment w:id="1">
            <w:p>
                <w:r>
                    <w:t>This is my comment.</w:t>
                </w:r>
            </w:p>
        </w:comment>
    </w:comments>
    ```
    
    结束示例]
    
    注释部件应位于包含关系部件的包中（在语法上表达，关系元素的 TargetMode 属性应为 Internal）。
    
    注释部件允许包含到 ECMA-376 所定义的以下部件的显式关系：
    
    - 备用格式导入（[§11.3.1]）
    - 图表（[§14.2.1]）
    - 内容部件（[§15.2.4]）
    - 图表：图表颜色([§14.2.3])、图表数据([§14.2.4])、图表布局定义([§14.2.5]) 和 图表样式([§14.2.6])
    - 内嵌控件持久性（[§15.2.9]）
    - 内嵌对象（[§15.2.10]）
    - 内嵌包（[§15.2.11]）
    - 超链接（[§15.3]）
    - 图片（[§15.2.14]）
    - 视频（[§15.2.17]）
    
    注释部件不得对任何其他由 ECMA-376 定义的部件具有隐式或显式关系。

=== "英文"

    **Comments Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.comments+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/comments</td>
        </tr>
    </table>
        
    An instance of this part type contains the information about each comment in the document.
    
    A package shall contain no more than two Comments parts. If it exists, one instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.
    
    [Example: The following Main Document part-relationship item contains a relationship to the Contents part, which is stored as the ZIP item comment.xml:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId93"
            Type="http://…/comments" Target="comments.xml"/>
    </Relationships>
    ```
    
    end example]
    
    The root element for a Comment part shall be comments.
    
    [Example:
    
    ```xml
    <w:comments … >
        <w:comment>
            …
        </w:comment>
        …
    </w:comments>
    ```
    
    end example]
    
    The XML markup for a comment in a Main Document part uses the commentReference element.
    
    [Example: Consider the case in which the Main Document part contains the text "… in the Standard.", and there is an comment inserted immediately after the period:
    
    ```xml
    <w:p …>
        …
        <w:r>
            <w:t>… in the Standard.</w:t>
        </w:r>
        <w:r>
            <w:commentReference w:id="1"/>
        </w:r>
    </w:p>
    ```
    
    end example]
    
    Each comment has a corresponding comment element in the Comments part, which contains the text of the comment.
    
    [Example: The text of the comment is "This is my comment.":
    
    ```xml
    <w:comments xmlns:w="…">
        <w:comment w:id="1">
            <w:p>
                <w:r>
                    <w:t>This is my comment.</w:t>
                </w:r>
            </w:p>
        </w:comment>
    </w:comments>
    ```
    
    end example]
    
    A Comments part shall be located within the package containing the relationships part (expressed syntactically,
    the TargetMode attribute of the Relationship element shall be Internal).
    
    A Comments part is permitted to contain explicit relationships to the following parts defined by ECMA-376:
    
    - Alternative Format Import ([§11.3.1])
    - Chart ([§14.2.1])
    - Content Part ([§15.2.4])
    - Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5]) and Diagram Styles ([§14.2.6])
    - Embedded Control Persistence ([§15.2.9])
    - Embedded Object ([§15.2.10])
    - Embedded Package ([§15.2.11])
    - Hyperlinks ([§15.3])
    - Images ([§15.2.14])
    - Video ([§15.2.17])
    
    A Comments part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.


### 11.3.3 文档设置部件

=== "中文"
    
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/settings</td>
        </tr>
    </table>

    该部件类型的实例包含了文档的所有属性设置。
    
    一个包中不得包含超过两个文档设置部件。如果存在，其中一个实例应该是主文档（[§11.3.10]）部件隐式关系的目标，另一个实例应该是词汇表文档（[§11.3.8]）部件隐式关系的目标。
    
    【示例：下面的主文档部件关系项包含了与存储在ZIP项settings.xml中的文档设置部件的关系：
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId4"
            Type="http://…/settings" Target="settings.xml"/>
    </Relationships>
    ```
    
    
    示例结束】
    
    这种内容类型的部件的根元素应该是settings。

    【示例：
    
    ```xml
    <w:settings … >
        …
        <w:defaultTabStop w:val="360"/>
        <w:footnotePr>
            …
        </w:footnotePr>
        <w:endnotePr>
            …
        </w:endnotePr>
        <w:rsids>
            …
        </w:rsids>
        …
    </w:settings>
    ```
    
    示例结束】
    
    文档设置部件应该位于包含关系部件的包中（在语法上表达，关系元素的TargetMode属性应该是Internal）。
    
    文档设置部件可以包含对以下由ECMA-376定义的部件的显式关系：
    
    - 文档模板（[§11.4]）
    - 邮件合并数据源（[§11.7]）
    - 邮件合并标题数据源（[§11.8]）
    - XSL转换（[§11.9]）
    
    文档设置部件不得与ECMA-376定义的任何其他部件具有隐式或显式关系。

=== "英文"

    **Document Settings Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.settings+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/settings</td>
        </tr>
    </table>
        
    An instance of this part type contains all the document's properties.
    
    A package shall contain no more than two Document Settings parts. If it exists, one instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.
    
    [Example: The following Main Document part-relationship item contains a relationship to a Document Settings part, which is stored in the ZIP item settings.xml:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId4"
            Type="http://…/settings" Target="settings.xml"/>
    </Relationships>
    ```
    
    
    end example]
    
    The root element for a part of this content type shall be settings.
    
    [Example:
    
    ```xml
    <w:settings … >
        …
        <w:defaultTabStop w:val="360"/>
        <w:footnotePr>
            …
        </w:footnotePr>
        <w:endnotePr>
            …
        </w:endnotePr>
        <w:rsids>
            …
        </w:rsids>
        …
    </w:settings>
    ```
    
    
    end example]
    
    A Document Settings part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Document Settings part is permitted to contain explicit relationships to the following parts defined by ECMA-376:
    
    - Document Template ([§11.4])
    - Mail Merge Data Source ([§11.7])
    - Mail Merge Header Data Source ([§11.8])
    - XSL Transformation ([§11.9])
    
    A Document Settings part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.4 尾注部件

=== "中文"
    
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.endnotes+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/endnotes</td>
        </tr>
    </table>

    该部件类型的实例包含了文档中的所有尾注。
    
    一个包中不得包含超过两个尾注部件。如果存在，其中一个实例应该是主文档（[§11.3.10]）部件隐式关系的目标，另一个实例应该是词汇表文档（[§11.3.8]）部件隐式关系的目标。
    
    !!! info "示例"
        
        以下主文档部件关系项包含了与尾注部件的关系，该关系以ZIP项endnotes.xml的形式存储：
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http://…/endnotes" Target="endnotes.xml"/>
        </Relationships>
        ```
    
    尾注部件的根元素应为endnotes。
    
    !!! info "示例"
        
        ```xml
        <w:endnotes xmlns:w="…" …>
            <w:endnote …>
                …
            </w:endnote>
            <w:endnote …>
                …
            </w:endnote>
        </w:endnotes>
        ```
    
    主文档部件中的尾注使用endnoteReference元素进行XML标记。
    
    !!! info "Example"

        考虑这样一种情况，主文档部件包含文本“…在标准中。”，并且在句号之后立即插入了一个尾注：

        ```xml
        <w:p …>
            …
            <w:r>
                <w:t>… in the Standard.</w:t>
            </w:r>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="EndnoteReference"/>
                </w:rPr>
                <w:endnoteReference w:id="5"/>
            </w:r>
        </w:p>
        ```
    
    每个尾注在尾注部件都有对应的尾注元素，其中包含尾注的文本和尾注引用元素。
    
    !!! info "Example"

        尾注的文本是可以从“http://www.aabbcc.com/index.html”下载。 其中 "http://www.aabbcc.com/index.html"被标记为超链接。

        ```xml
        <w:endnotes xmlns:w="…">
            <w:endnote w:id="5">
                <w:p>
                    <w:r>
                        <w:rPr>
                            <w:rStyle w:val="EndnoteReference" />
                        </w:rPr>
                        <w:endnoteRef />
                    </w:r>
                    <w:r>
                        <w:t xml:space="preserve">This can be downloaded from </w:t>
                    </w:r>
                    <w:hyperlink r:id="rId2">
                        <w:r>
                            <w:rPr>
                                <w:rStyle w:val="Hyperlink" />
                            </w:rPr>
                            <w:t>http://www.aabbcc.com/index.html</w:t>
                        </w:r>
                    </w:hyperlink>
                    <w:r>
                        <w:t>.</w:t>
                    </w:r>
                </w:p>
            </w:endnote>
        </w:endnotes>
        ```

    一个尾注部件应位于包含关系部件的包内（在语法上表达，关系元素的TargetMode属性应为Internal）。
    
    尾注部件可以包含对以下由ECMA-376定义的部件的显式关系：
    
    * 替代格式导入(Alternative Format Import)（[§11.3.1]）
    * 图表(Chart)（[§14.2.1]）
    * 内容部件(Content Part)（[§15.2.4]）
    * 图表(Diagrams)：图表颜色(Diagram Colors)（[§14.2.3]）、图表数据(Diagram Data)（[§14.2.4]）、图表布局定义(Diagram Layout Definition)（[§14.2.5]）和图表样式(Diagram Styles)（[§14.2.6]）
    * 嵌入控件持久性(Embedded Control Persistence)（[§15.2.9]）
    * 嵌入对象(Embedded Object)（[§15.2.10]）
    * 嵌入包(Embedded Package)（[§15.2.11]）
    * 超链接(Hyperlinks)（[§15.3]）
    * 图像(Images)（[§15.2.14]）
    * 视频(Video)（[§15.2.17]）
    
    尾注部件不得与ECMA-376定义的任何其他部件具有隐式或显式的关系。

=== "英文"

    **Endnotes Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.endnotes+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/endnotes</td>
        </tr>
    </table>

    An instance of this part type contains all the endnotes for the document.

    A package shall contain no more than two Endnotes parts. If it exists, one instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.
    
    !!! info "Example"

        The following Main Document part-relationship item contains a relationship to the Endnotes part, which is stored as the ZIP item endnotes.xml:
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId6"
                Type="http://…/endnotes" Target="endnotes.xml"/>
        </Relationships>
        ```

    The root element for an Endnotes part shall be endnotes.

    !!! info "Example"
        ```xml
        <w:endnotes xmlns:w="…" …>
            <w:endnote …>
                …
            </w:endnote>
            <w:endnote …>
                …
            </w:endnote>
        </w:endnotes>
        ```

    The XML markup for an endnote in a Main Document part uses the endnoteReference element.
    
    !!! info "Example"
        Consider the case in which the Main Document part contains the text "… in the Standard.", and there is an endnote inserted immediately after the period:

        ```xml
        <w:p …>
            …
            <w:r>
                <w:t>… in the Standard.</w:t>
            </w:r>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="EndnoteReference"/>
                </w:rPr>
                <w:endnoteReference w:id="5"/>
            </w:r>
        </w:p>
        ```
    
    Each endnote has a corresponding endnote element in the Endnotes part, which contains the text of the endnote, and the endnoteRef element.
    
    !!! info "Example"

        The text of the endnote is "This can be downloaded from http://www.aabbcc.com/index.html." where "http://www.aabbcc.com/index.html" is marked as a hyperlink:

        ```xml
        <w:endnotes xmlns:w="…">
            <w:endnote w:id="5">
                <w:p>
                    <w:r>
                        <w:rPr>
                            <w:rStyle w:val="EndnoteReference" />
                        </w:rPr>
                        <w:endnoteRef />
                    </w:r>
                    <w:r>
                        <w:t xml:space="preserve">This can be downloaded from </w:t>
                    </w:r>
                    <w:hyperlink r:id="rId2">
                        <w:r>
                            <w:rPr>
                                <w:rStyle w:val="Hyperlink" />
                            </w:rPr>
                            <w:t>http://www.aabbcc.com/index.html</w:t>
                        </w:r>
                    </w:hyperlink>
                    <w:r>
                        <w:t>.</w:t>
                    </w:r>
                </w:p>
            </w:endnote>
        </w:endnotes>
        ```
    An Endnotes part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
        
    An Endnotes part is permitted to contain explicit relationships to the following parts defined by ECMA-376:

    * Alternative Format Import ([§11.3.1])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5])and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlinks ([§15.3])
    * Images ([§15.2.14])
    * Video ([§15.2.17])

    An Endnotes part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.
        
### 11.3.5 字体表部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.fontTable+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/fontTable</td>
        </tr>
    </table>
    

    此部件类型的一个实例包含文档中每个使用的字体的信息。当使用者阅读一个 WordprocessingML 文档时，应该使用此信息来确定在消费者的系统上指定的字体不可用时，要使用哪些字体来显示文档。
    
    一个包不应包含多于两个 Font Table 部件。如果存在，该部件的一个实例应该成为 Main Document（[§11.3.10]）部件中隐式关系的目标，而另一个实例应该成为 Glossary Document（[§11.3.8]）部件的隐式关系的目标。
    
    !!! info "示例"
    
        以下是 Main Document 部件关系项，其中包含一个与 Font Table 部件的关系，该关系以 fontTable.xml 作为 ZIP 项存储：
    
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/fontTable" Target="fontTable.xml"/>
        </Relationships>
        ```
    
    此内容类型的部件的根元素应该是 fonts。
    
    !!! info "示例"
    
        ```xml
        <w:fonts … >
            <w:font w:name="Calibri">
                <w:panose1 w:val="020F0502020204030204"/>
                <w:charset w:val="00"/>
                <w:family w:val="swiss"/>
                <w:pitch w:val="variable"/>
                <w:sig w:usb0="A00002EF" w:usb1="4000207B" w:usb2="00000000"
                    w:usb3="00000000" w:csb0="0000009F" w:csb1="00000000"/>
            </w:font>
        </w:fonts>
        ```
    
    Font Table 部件应该位于包含关系部件的包中（在语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    Font Table 部件可以包含到由 ECMA-376 定义的以下部件的显式关系：
    
    * 字体(Fonts)（[§15.2.13]）
    
    Font Table 部件不应该有任何与由 ECMA-376 定义的其他部件的隐式或显式关系。


=== "英文"

    **Font Table Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.fontTable+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/fontTable</td>
        </tr>
    </table>
    
    An instance of this part type contains information about each of the fonts used by content in the document. When a consumer reads a WordprocessingML document, it shall use this information to determine which fonts to use to display the document when the specified fonts are not available on the consumer’s system.

    A package shall contain no more than two Font Table parts. If it exists, one instance of that part shall be the target of an implicit relationship in the part-relationship item for the Main Document ([§11.3.10]) part, and the other instance shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.
    
    !!! info "Example"

        The following Main Document part-relationship item contains a relationship to the Font Table part, which is stored as the ZIP item fontTable.xml:

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId1"
                Type="http://…/fontTable" Target="fontTable.xml"/>
        </Relationships>
        ```
    
    The root element for a part of this content type shall be fonts.
    
    !!! info "Example"

        ```xml
        <w:fonts … >
            <w:font w:name="Calibri">
                <w:panose1 w:val="020F0502020204030204"/>
                <w:charset w:val="00"/>
                <w:family w:val="swiss"/>
                <w:pitch w:val="variable"/>
                <w:sig w:usb0="A00002EF" w:usb1="4000207B" w:usb2="00000000"
                    w:usb3="00000000" w:csb0="0000009F" w:csb1="00000000"/>
            </w:font>
        </w:fonts>
        ```

    A Font Table part shall be located within the package containing the relationships part (expressed syntactically,
    the TargetMode attribute of the Relationship element shall be Internal).

    A Font Table part is permitted to contain explicit relationships to the following parts defined by ECMA-376:

    * Fonts ([§15.2.13])
    
    A Font Table part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.6 页脚部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.footer+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/footer</td>
        </tr>
    </table>
    
    此部件类型的一个实例包含一个或多个部件所显示的页脚的信息。一个包允许为文档中每个部件的每种类型的页脚（第一页、奇数页或偶数页）包含零个或一个页脚部件。每个页脚部件应该是 Main Document（[§11.3.10]）部件或 Glossary Document（[§11.3.8]）部件的 part-relationship 项中的一个显式关系的目标。
    
    !!! info "示例"
    
        Main Document 部件的 part-relationship 项包含一个关系，用于奇数页页脚部件，该关系存储为 ZIP 项 footer3.xml：
    
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId91"
                Type="http://…/footer" Target="footer3.xml"/>
        </Relationships>
        ```
    
    页脚部件的根元素应该是 ftr。
    
    !!! info "示例"
    
        ```xml
        <w:ftr xmlns:w="…" …>
            …
        </w:ftr>
        ```
    
    在 Main Document 部件的某个节中，页脚的 XML 标记涉及到 sectPr 元素中的 footerReference 元素，该元素显式引用了页眉的关系。
    
    !!! info "示例"
    
        考虑一个情况，Main Document 部件的一个节包含奇数页和偶数页的页眉，以及一个奇数页的页脚：
    
        ```xml
        <w:document xmlns:w="…">
            …
            <w:sectPr>
                <w:footerReference w:val="rId89" w:type="default"/>
                <w:footerReference w:val="rId90" w:type="even"/>
                <w:footerReference w:val="rId91" w:type="first"/>
                <w:type w:val="oddPage"/>
                <w:pgSz w:w="11909" w:h="16834" w:code="9"/>
                <w:pgMar w:top="1440" w:right="1152" w:bottom="1440"
                    w:left="1152" w:header="720" w:footer="720" w:gutter="0"/>
                <w:lnNumType w:countBy="1"/>
                <w:pgNumType w:numFmt="lowerRoman"/>
                <w:cols w:space="720"/>
            </w:sectPr>
        </w:document>
        ```
    
    每个页脚都有一个对应的 ftr 元素在页脚部件中，其中包含页脚的文本。
    
    !!! info "示例"
    
        这是与上面示例对应的奇数页页脚。它将页码居中显示，并使用小写罗马数字（由上面的 pgNumType 元素设置）：
    
        ```xml
        <w:ftr xmlns:w="…">
            <w:p>
                <w:pPr>
                    <w:pStyle w:val="Centered"/>
                </w:pPr>
                <w:fldSimple w:instr="PAGE">
                    <w:r>
                        <w:rPr>
                            <w:noProof/>
                        </w:rPr>
                        <w:t>i</w:t>
                    </w:r>
                </w:fldSimple>
            </w:p>
        </w:ftr>
        ```
    
    页脚部件应该位于包含关系部件的包中（在语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    页脚部件可以有显式关系到由 ECMA-376 定义的以下部件：
    
    * Alternative Format Import（[§11.3.1]）
    * 图表（[§14.2.1]）
    * 内容部件（[§15.2.4]）
    * 图表：图表颜色（[§14.2.3]）、图表数据（[§14.2.4]）、图表布局定义（[§14.2.5]）和图表样式（[§14.2.6]）
    * 嵌入控件持久性（[§15.2.9]）
    * 嵌入对象（[§15.2.10]）
    * 嵌入包（[§15.2.11]）
    * 超链接（[§15.3]）
    * 图像（[§15.2.14]）
    * 视频（[§15.2.17]）
    
    页脚部件不应该有任何与由 ECMA-376 定义的其他部件的隐式或显式关系。

=== "英文"

    **Footer Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.footer+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/footer</td>
        </tr>
    </table>

    An instance of this part type contains the information about a footer displayed for one or more sections. A package is permitted to contain zero or one Footer part for each kind of footer (first page, odd page, or even page) in each section of the document. Each Footer part shall be the target of an explicit relationship in the part-relationship item for the Main Document ([§11.3.10]) part, or the Glossary Document ([§11.3.8]) part.

    !!! info "Example"

        The Main Document part-relationship item contains one relationship, for the odd footer part, which is stored as the ZIP item footer3.xml:
    
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId91"
                Type="http://…/footer" Target="footer3.xml"/>
        </Relationships>
        ```
    
    The root element for a Footer part shall be ftr.

    !!! info "Example"

        ```xml
        <w:ftr xmlns:w="…" …>
            …
        </w:ftr>
        ```
    
    The XML markup for a footer in a section of a Main Document part involves the footerReference element in that section's sectPr element which explicitly references the relationship for the header.
    
    !!! info "Example"

        Consider the case in which a section in the Main Document part contains odd and even headers, and an odd footer:
    
        ```xml
        <w:document xmlns:w="…">
            …
            <w:sectPr>
                <w:footerReference w:val="rId89" w:type="default"/>
                <w:footerReference w:val="rId90" w:type="even"/>
                <w:footerReference w:val="rId91" w:type="first"/>
                <w:type w:val="oddPage"/>
                <w:pgSz w:w="11909" w:h="16834" w:code="9"/>
                <w:pgMar w:top="1440" w:right="1152" w:bottom="1440"
                    w:left="1152" w:header="720" w:footer="720" w:gutter="0"/>
                <w:lnNumType w:countBy="1"/>
                <w:pgNumType w:numFmt="lowerRoman"/>
                <w:cols w:space="720"/>
            </w:sectPr>
        </w:document>
        ```

    Each footer has a corresponding ftr element in a Footer part, which contains the text of the footer.

    !!! info "Example"

        Here is the odd footer corresponding to the example above. It has the page number centered and displayed using lowercase Roman numerals (as set by the pgNumType element above):
    
        ```xml
        <w:ftr xmlns:w="…">
            <w:p>
                <w:pPr>
                    <w:pStyle w:val="Centered"/>
                </w:pPr>
                <w:fldSimple w:instr="PAGE">
                    <w:r>
                        <w:rPr>
                            <w:noProof/>
                        </w:rPr>
                        <w:t>i</w:t>
                    </w:r>
                </w:fldSimple>
            </w:p>
        </w:ftr>
        ```

    A Footer part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Footer part is permitted to have explicit relationships to the following parts defined by ECMA-376:

    * Alternative Format Import ([§11.3.1])
    * Chart ([§14.2.1])  
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5])and
    * Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlinks ([§15.3])
    * Images ([§15.2.14])
    * Video ([§15.2.1])
    
    A Footer part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.7 脚注部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.footnotes+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/footnotes</td>
        </tr>
    </table>

    此部件类型的一个实例包含文档中的所有脚注。
    
    一个包不应包含多于两个 Footnotes 部件。如果存在，该部件的一个实例应该成为 Main Document（[§11.3.10]）部件的隐式关系的目标，而另一个实例应该成为 Glossary Document（[§11.3.8]）部件的隐式关系的目标。
    
    !!! info "示例"
    
        Main Document 部件的 part-relationship 项包含一个关系，用于 Footnotes 部件，该关系存储为 ZIP 项 footnotes.xml：
    
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/footnotes" Target="footnotes.xml"/>
        </Relationships>
        ```
    
    Footnotes 部件的根元素应为 footnotes。
    
    !!! info "示例"
    
        ```xml
        <w:footnotes xmlns:w="…" …>
            <w:footnote …>
                …
            </w:footnote>
            <w:footnote …>
                …
            </w:footnote>
        </w:footnotes>
        ```
    
    在 Main Document 部件的一个脚注的 XML 标记涉及到 footnoteReference 元素。
    
    !!! info "示例"
    
        考虑一种情况，Main Document 部件包含文本 "… in the Standard."，并且在句点后立即插入了一个脚注：
    
        ```xml
        <w:p …>
            …
            <w:r>
                <w:t>… in the Standard.</w:t>
            </w:r>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="FootnoteReference"/>
                </w:rPr>
                <w:footnoteReference w:id="5"/>
            </w:r>
        </w:p>
        ```
    
    每个脚注在 Footnotes 部件中有一个对应的脚注元素，其中包含脚注的文本和 footnoteRef 元素。
    
    !!! info "示例"
    
        脚注的文本为 "This can be downloaded from http://www.aabbcc.com/index.html."，其中 "http://www.aabbcc.com/index.html" 被标记为一个超链接：
    
        ```xml
        <w:footnotes xmlns:w="…"
            <w:footnote w:id="5">
                <w:p>
                    <w:r>
                        <w:rPr>
                            <w:rStyle w:val="FootnoteReference"/>
                        </w:rPr>
                        <w:footnoteRef/>
                    </w:r>
                    <w:r>
                        <w:t xml:space="preserve">This can be downloaded from </w:t>
                    </w:r>
                    <w:hyperlink r:id="rId2" w:history="1">
                        <w:r>
                            <w:rPr>
                                <w:rStyle w:val="Hyperlink"/>
                            </w:rPr>
                            <w:t>http://www.aabbcc.com/index.html</w:t>
                        </w:r>
                    </w:hyperlink>
                    <w:r>
                        <w:t>.</w:t>
                    </w:r>
                </w:p>
            </w:footnote>
        </w:footnotes>
        ```
    
    Footnotes 部件应位于包含关系部件的包中（在语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    Footnotes 部件允许有显式关系到由 ECMA-376 定义的以下部件：
    
    * Alternative Format Import（[§11.3.1]）
    * 图表（[§14.2.1]）
    * 内容部件（[§15.2.4]）
    * 图表：图表颜色（[§14.2.3]）、图表数据（[§14.2.4]）、图表布局定义（[§14.2.5]）和图表样式（[§14.2.6]）
    * 嵌入控件持久性（[§15.2.9]）
    * 嵌入对象（[§15.2.10]）
    * 嵌入包（[§15.2.11]）
    * 超链接（[§15.3]）
    * 图像（[§15.2.14]）
    * 视频（[§15.2.17]）
    
    Footnotes 部件不得有任何与由 ECMA-376 定义的其他部件的隐式或显式关系。
    

=== "英文"

    **Footnotes Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.footnotes+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/footnotes</td>
        </tr>
    </table>
    
    An instance of this part type contains all the footnotes for the document.
    
    A package shall contain no more than two Footnotes parts. If it exists, one instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.
    
    !!! info "Example"
    
        The Main Document part-relationship item contains a relationship to the Footnotes part, which is stored as the ZIP item footnotes.xml:
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId5"
                Type="http://…/footnotes" Target="footnotes.xml"/>
        </Relationships>
        ```
    
    The root element for a Footnotes part shall be footnotes.
    
    !!! info "Example"
    
        ```xml
        <w:footnotes xmlns:w="…" …>
            <w:footnote …>
                …
            </w:footnote>
            <w:footnote …>
                …
            </w:footnote>
        </w:footnotes>
        ```
    
    The XML markup for a footnote in a Main Document part involves the footnoteReference element.
    
    !!! info "Example"
    
        Consider the case in which the Main Document part contains the text "… in the Standard.", and there is a footnote inserted immediately after the period:
    
        ```xml
        <w:p …>
            …
            <w:r>
                <w:t>… in the Standard.</w:t>
            </w:r>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="FootnoteReference"/>
                </w:rPr>
                <w:footnoteReference w:id="5"/>
            </w:r>
        </w:p>
        ```
    
    Each footnote has a corresponding footnote element in the Footnotes part, which contains the text of the footnote and the footnoteRef element.
    
    !!! info "Example"
    
        The text of the footnote is "This can be downloaded from http://www.aabbcc.com/index.html." where "http://www.aabbcc.com/index.html" is marked as a hyperlink:
    
        ```xml
        <w:footnotes xmlns:w="…"
            <w:footnote w:id="5">
                <w:p>
                    <w:r>
                        <w:rPr>
                            <w:rStyle w:val="FootnoteReference"/>
                        </w:rPr>
                        <w:footnoteRef/>
                    </w:r>
                    <w:r>
                        <w:t xml:space="preserve">This can be downloaded from </w:t>
                    </w:r>
                    <w:hyperlink r:id="rId2" w:history="1">
                        <w:r>
                            <w:rPr>
                                <w:rStyle w:val="Hyperlink"/>
                            </w:rPr>
                            <w:t>http://www.aabbcc.com/index.html</w:t>
                        </w:r>
                    </w:hyperlink>
                    <w:r>
                        <w:t>.</w:t>
                    </w:r>
                </w:p>
            </w:footnote>
        </w:footnotes>
        ```
    
    A Footnotes part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Footnotes part is permitted to have explicit relationships to the following parts defined by ECMA-376:
    
    * Alternative Format Import ([§11.3.1])
    * Chart ([§14.2.1]) 
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5])and
    * Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlinks ([§15.3])
    * Images ([§15.2.14])
    * Video ([§15.2.17])
    
    A Footer part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.8 术语表部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.document.glossary+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/glossaryDocument</td>
        </tr>
    </table>
    
    此部件类型的一个实例是一个附加文档存储位置，用于存储将来要插入和/或使用的内容的定义和内容，但这些内容不应在主文档内容中可见。[示例：一个法律合同模板可能包含一个或多个可选条款，在用户操作明确插入这些条款之前，这些条款不会出现在文档中。为了存储这些可选条款直到被插入，它们的内容被放置在词汇表文档部件中。结束示例]
    
    [注：此部件用于存储可选的 "文档片段"，通常用于执行文档组装。使用词汇表这个词是指这些条目每个都是历史上的第一个单词的引用，就像传统词汇表中术语的定义一样。结束注释]
    
    此内容类型的部件的根元素应为 glossaryDocument。
    
    [示例：以下部件包含两个构建块。第一个块名为 "彩虹颜色"，属于名为 "Misc" 的类别，属于名为 "docParts" 的图库，并包含文本 "The colors … and violet." 第二个块的详细信息已省略：
    
    ```xml
    <w:glossaryDocument xmlns:w="…" >
        <w:docParts>
            <w:docPart>
                <w:docPartPr>
                    <w:name w:val="rainbow colors"/>
                    <w:style w:val="Normal"/>
                    <w:category>
                        <w:name w:val="Misc"/>
                        <w:gallery w:val="docParts"/>
                    </w:category>
                </w:docPartPr>
                <w:docPartBody>
                    <w:p>
                        <w:r>
                            <w:t>The colors of the rainbow are red, orange, yellow,
                                green, blue, indigo, and violet.</w:t>
                        </w:r>
                    </w:p>
                </w:docPartBody>
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    结束示例]
    
    一个包应最多包含一个 Glossary Document 部件，该部件应是从 Main Document（[§11.3.10]）部件的隐式关系的目标。
    
    [示例：以下是 Main Document 部件的 part-relationship 项，包含与 Glossary Document 部件的关系，该部件存储在 ZIP 项 glossary/document.xml 中：

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId4"
            Type="http://…/glossaryDocument" Target="glossary/document.xml"/>
    </Relationships>
    ```
    
    结束示例]
    
    Glossary Document 部件应位于包含关系部件的包中（在语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    Glossary Document 部件允许与 ECMA-376 定义的以下部件之间存在隐式关系：
    
    * Comments（[§11.3.2]）
    * Document Settings（[§11.3.3]）
    * Endnotes（[§11.3.4]）
    * Font Table（[§11.3.5]）
    * Footnotes（[§11.3.7]）
    * Numbering Definitions（[§11.3.11]）
    * Style Definitions（[§11.3.11]）
    
    Glossary Document 部件允许与 ECMA-376 定义的以下部件之间存在显式关系：
    
    * Alternative Format Import（[§11.3.1]）
    * Chart（[§14.2.1]）
    * Content Part（[§15.2.4]）
    * Diagrams：Diagram Colors（[§14.2.3]）、Diagram Data（[§14.2.4]）、Diagram Layout Definition（[§14.2.5]）和 Diagram Styles（[§14.2.6]）
    * Embedded Control Persistence（[§15.2.9]）
    * Embedded Object（[§15.2.10]）
    * Embedded Package（[§15.2.11]）
    * Footer（[§11.3.6]）
    * Header（[§11.3.9]）
    * Hyperlinks（[§15.3]）
    * Images（[§15.2.14]）
    * Printer Settings（[§15.2.15]）
    * Video（[§15.2.17]）
    
    Glossary Document 部件不得与由 ECMA-376 定义的任何其他部件存在隐式或显式关系。

=== "英文"

    **Glossary Document Part**

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.document.glossary+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/glossaryDocument</td>
        </tr>
    </table>

    An instance of this part type is a supplementary document storage location which stores the definition and content for content that shall be carried with the document for future insertion and/or use, but which shall not be visible within the contents of the main document story. [Example: A legal contract template might include one or more optional clauses that shall not appear in the document until those clauses are inserted explicitly via a user action. To store these optional clauses until they are inserted, their contents are placed in the glossary document part. end example]
    
    [Note: This part is intended for storage of optional "document fragments" which are often used to perform document assembly. The use of the word glossary is a reference to the fact that each of these entries was historically referenced by its first word in legacy word processing applications, like definitions of terms in a traditional glossary. end note]

    The root element for a part of this content type shall be glossaryDocument.
    
    [Example: The following part contains two building blocks. The first block is named "rainbow colors", belongs to a category called "Misc", belongs to a gallery called "docParts", and contains the text "The colors … and violet." The details of the second block have been omitted:

    ```xml
    <w:glossaryDocument xmlns:w="…" >
        <w:docParts>
            <w:docPart>
                <w:docPartPr>
                    <w:name w:val="rainbow colors"/>
                    <w:style w:val="Normal"/>
                    <w:category>
                        <w:name w:val="Misc"/>
                        <w:gallery w:val="docParts"/>
                    </w:category>
                </w:docPartPr>
                <w:docPartBody>
                    <w:p>
                        <w:r>
                            <w:t>The colors of the rainbow are red, orange, yellow,
                                green, blue, indigo, and violet.</w:t>
                        </w:r>
                    </w:p>
                </w:docPartBody>
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```

    end example]

    A package shall contain at most one Glossary Document part, and that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part.
    
    [Example: The following Main Document part-relationship item contains a relationship to a Glossary Document part, which is stored in the ZIP item glossary/document.xml:

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId4"
            Type="http://…/glossaryDocument" Target="glossary/document.xml"/>
    </Relationships>
    ```

    end example]
    
    A Glossary Document part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Glossary Document part is permitted to have implicit relationships to the following parts defined by ECMA-376:

    * Comments ([§11.3.2])
    * Document Settings ([§11.3.3])
    * Endnotes ([§11.3.4])
    * Font Table ([§11.3.5])
    * Footnotes ([§11.3.7])
    * Numbering Definitions ([§11.3.11])
    * Style Definitions ([§11.3.11])

    A Glossary Document part is permitted to have explicit relationships to the following parts defined by ECMA-376:

    * Alternative Format Import ([§11.3.1])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors ([§14.2.3]), Diagram Data ([§14.2.4]), Diagram Layout Definition ([§14.2.5])and
    * Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Footer ([§11.3.6])
    * Header ([§11.3.9])
    * Hyperlinks ([§15.3])
    * Images ([§15.2.14])
    * Printer Settings ([§15.2.15])
    * Video ([§15.2.17])

    A Glossary Document part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.9 头部部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.header+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/header</td>
        </tr>
    </table>
        
    此部件类型的一个实例包含关于一个或多个章节显示的页眉的信息。一个包应该对于文档中每个部件的每种类型的页眉（第一页、奇数页或偶数页）包含零个或一个 Header 部件。每个 Header 部件应该是来自 Main Document（[§11.3.10]）部件或 Glossary Document（[§11.3.8]）部件的显式关系的目标。
    
    [示例：Main Document 部件的 part-relationship 项包含两个关系：一个是偶数页页眉部件（存储为 ZIP 项 header2.xml），另一个是奇数页页眉部件（存储为 ZIP 项 header3.xml）：
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId89" Type="http://…/header" Target="header2.xml"/>
        <Relationship Id="rId90" Type="http://…/header" Target="header3.xml"/>
    </Relationships>
    ```
    
    结束示例]
    
    Header 部件的根元素应为 hdr。
    
    [示例：
    
    ```xml
    <w:hdr xmlns:w="…" …>
        …
    </w:hdr>
    ```
    
    结束示例]
        
    在 Main Document 部件的一个章节中的页眉的 XML 标记涉及到该章节的 sectPr 元素中的 headerReference 元素。
    
    [示例：考虑这样一个情况，Main Document 部件的一个章节包含奇数页和偶数页页眉，以及一个奇数页页脚：
    
    ```xml
    <w:body>
        …
        <w:sectPr w:rsidR="00363F31" w:rsidSect="008D4B40">
            <w:headerReference w:val="rId89" w:type="default"/>
            <w:headerReference w:val="rId90" w:type="even"/>
            <w:headerReference w:val="rId91" w:type="first"/>
            <w:type w:val="oddPage"/>
            <w:pgSz w:w="11909" w:h="16834" w:code="9"/>
            <w:pgMar w:top="1440" w:right="1152" w:bottom="1440"
                w:left="1152" w:header="720" w:footer="720" w:gutter="0"/>
            <w:lnNumType w:countBy="1"/>
            <w:pgNumType w:fmt="lowerRoman"/>
            <w:cols w:space="720"/>
        </w:sectPr>
    </w:body>
    ```
    
    结束示例]
    
    每个页眉在 Header 部件中有一个对应的 hdr 元素，其中包含页眉的文本。
    
    [示例：以下是与上述示例对应的偶数页页眉：
    
    ```xml
    <w:hdr xmlns:w="…">
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Header"/>
            </w:pPr>
            <w:r>
                <w:t>My Test Document</w:t>
            </w:r>
        </w:p>
    </w:hdr>
    ```
    
    以下是与上述示例对应的奇数页页眉：

    ```xml
    <w:hdr xmlns:w="…">
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Header"/>
            </w:pPr>
            <w:r>   
                <w:tab/>
                <w:t>Table of Contents</w:t>
            </w:r>
        </w:p>
    </w:hdr>
    ```

    结束示例]
    
    Header 部件应位于包含关系部件的包中（在语法上表达，Relationship 元素的 TargetMode 属性应为 Internal）。
    
    Header 部件允许与 ECMA-376 定义的以下部件之间存在显式关系：
    
    * Alternative Format Import（[§11.3.1]）
    * 图表（[§14.2.1]）
    * 内容部件（[§15.2.4]）
    * 图表：图表颜色（[§14.2.3]）、图表数据（[§14.2.4]）、图表布局定义（[§14.2.5]）和 图表样式（[§14.2.6]）
    * 嵌入控件持久性（[§15.2.9]）
    * 嵌入对象（[§15.2.10]）
    * 嵌入包（[§15.2.11]）
    * 超链接（[§15.3]）
    * 图像（[§15.2.14]）
    * 视频（[§15.2.17]）
    
    Header 部件不得具有 ECMA-376 定义的任何其他部件的隐式或显式关系。
    

=== "英文"

    **Header Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.header+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/header</td>
        </tr>
    </table>
    
    An instance of this part type contains the information about a header displayed for one or more sections. A package shall contain zero or one Header part for each kind of header (first page, odd page, or even page) in each section of the document. Each Header part shall be the target of an explicit relationship from the Main Document ([§11.3.10]) part or the Glossary Document ([§11.3.8]) part.
    
    [Example: The Main Document part-relationship item contains two relationships: one for the even header part (which is stored as the ZIP item header2.xml) and one for the odd header part (which is stored as the ZIP item header3.xml):

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId89" Type="http://…/header" Target="header2.xml"/>
        <Relationship Id="rId90" Type="http://…/header" Target="header3.xml"/>
    </Relationships>
    ```

    end example]
    
    The root element for a Header part shall be hdr.
    
    [Example:

    ```xml
    <w:hdr xmlns:w="…" …>
        …
    </w:hdr>
    ```

    end example]
        
    The XML markup for a header in a section of a Main Document part involves the headerReference element in that section's sectPr element.
    
    [Example: Consider the case in which a section in the Main Document part contains odd and even headers, and an odd footer:

    ```xml
    <w:body>
        …
        <w:sectPr w:rsidR="00363F31" w:rsidSect="008D4B40">
            <w:headerReference w:val="rId89" w:type="default"/>
            <w:headerReference w:val="rId90" w:type="even"/>
            <w:headerReference w:val="rId91" w:type="first"/>
            <w:type w:val="oddPage"/>
            <w:pgSz w:w="11909" w:h="16834" w:code="9"/>
            <w:pgMar w:top="1440" w:right="1152" w:bottom="1440"
                w:left="1152" w:header="720" w:footer="720" w:gutter="0"/>
            <w:lnNumType w:countBy="1"/>
            <w:pgNumType w:fmt="lowerRoman"/>
            <w:cols w:space="720"/>
        </w:sectPr>
    </w:body>
    ```

    end example]
    
    Each header has a corresponding hdr element in a Header part, which contains the text of the header.
    
    [Example: Here is the even header corresponding to the examples above:

    ```xml
    <w:hdr xmlns:w="…">
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Header"/>
            </w:pPr>
            <w:r>
                <w:t>My Test Document</w:t>
            </w:r>
        </w:p>
    </w:hdr>
    ```

    Here is the odd header corresponding to the examples above:

    ```xml
    <w:hdr xmlns:w="…">
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Header"/>
            </w:pPr>
            <w:r>
                <w:tab/>
                <w:t>Table of Contents</w:t>
            </w:r>
        </w:p>
    </w:hdr>
    
    end example]

    A Header part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Header part is permitted to have explicit relationships to the following parts defined by ECMA-376:

    * Alternative Format Import ([§11.3.1)
    * Chart ([§14.2.1)
    * Content Part ([§15.2.4)
    * Diagrams: Diagram Colors([§14.2.3), Diagram Data([§14.2.4), Diagram Layout Definition([§14.2.5])and
    * Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Hyperlinks ([§15.3]).
    * Images ([§15.2.14])
    * Video ([§15.2.17])
    
    A Header part shall not have any implicit or explicit relationships to other parts defined by ECMA-376.

### 11.3.10 主文档部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                <p>application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml</p>
                <p>application/vnd.openxmlformats-officedocument.wordprocessingml.template.main+xml</p>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument</td>
        </tr>
    </table>

    该部件类型的一个实例包含文档的正文。
    
    一个包应该包含一个 Main Document（[§11.3.10]）部件。Main Document 部件应该是 package-relationship 项中的一个关系的目标。
    
    这种内容类型的部件的根元素应该是 document。
    
    [示例：给定以下 package-relationship 项的摘录：
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://…/officeDocument" Target="word/document.xml"/>
    </Relationships>
    ```
    
    /word/document.xml" 包含以下内容：
    
    ```xml
    <w:document …>
        <w:body>
            …
        </w:body>
    </w:document>
    ```
    
    结束示例]
    
    Main Document 部件应该位于包含关系部件的包内（在语法上表达，关系元素的 TargetMode 属性应该是 Internal）。
    
    Main Document 部件允许与 ECMA-376 定义的以下部件之间存在隐式关系：
    
    * 附加特性(Additional Characteristics)（[§15.2.1]）
    * 参考文献(Bibliography)（[§15.2.3]）
    * 注释(Comments)（[§11.3.2]）
    * 自定义 XML 数据存储(Custom XML Data Storage)（[§15.2.4]）
    * 文档设置(Document Settings)（[§11.3.3]）
    * 尾注(Endnotes)（[§11.3.4]）
    * 字体表(Font Table)（[§11.3.5]）
    * 脚注(Footnotes)（[§11.3.7]）
    * 词汇表文档(Glossary Document)（[§11.3.8]）
    * 编号定义(Numbering Definitions)（[§11.3.11]）
    * 样式定义(Style Definitions)（[§11.3.12]）
    * 主题(Theme)（[§14.2.7]）
    * 缩略图(Thumbnail)（[§15.2.16]）
    
    Main Document 部件允许与 ECMA-376 定义的以下部件之间存在显式关系：
    
    * 替代格式导入(Alternative Format Import)（[§11.3.1]）
    * 图表(Chart)（[§14.2.1]）
    * 内容部件(Content Part)（[§15.2.4]）
    * 图表(Diagrams)：图表颜色(Diagram Colors)（[§14.2.3]）、图表数据(Diagram Data)（[§14.2.4]）、图表布局定义(Diagram Layout Definition)（[§14.2.5]）和图表样式(Diagram Styles)（[§14.2.6]）
    * 嵌入控件持久性(Embedded Control Persistence)（[§15.2.9]）
    * 嵌入对象(Embedded Object)（[§15.2.10]）
    * 嵌入包(Embedded Package)（[§15.2.11]）
    * 页脚(Footer)（[§11.3.6]）
    * 页眉(Header)（[§11.3.9]）
    * 超链接(Hyperlinks)（[§15.3]）
    * 图像(Images)（[§15.2.14]）
    * 打印机设置(Printer Settings)（[§15.2.15]）
    * 子文档(Subdocument)（[§11.6]）
    * 视频(Video)（[§15.2.17]）
    
    Main Document 不得具有与 ECMA-376 定义的任何其他部件的隐式或显式关系。
    

=== "英文"

    **Main Document Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                <p>application/vnd.openxmlformats-officedocument.wordprocessingml.document.main+xml</p>
                <p>application/vnd.openxmlformats-officedocument.wordprocessingml.template.main+xml</p>
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/officeDocument</td>
        </tr>
    </table>

    An instance of this part type contains the body of the document.
    
    A package shall contain a Main Document part ([§11.3.10]) part. The Main Document part shall be the target of a relationship in the package-relationship item.
    
    The root element for a part of this content type shall be document.
    
    [Example: Given the following package-relationship item excerpt:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://…/officeDocument" Target="word/document.xml"/>
    </Relationships>
    ```
    
    /word/document.xml" contains the following:
    
    ```xml
    <w:document …>
        <w:body>
            …
        </w:body>
    </w:document>
    ```
    
    end example]
    
    A Main Document part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).
    
    A Main Document part is permitted to have implicit relationships to the following parts defined by ECMA-376:
    
    * Additional Characteristics ([§15.2.1])
    * Bibliography ([§15.2.3])
    * Comments ([§11.3.2])
    * Custom XML Data Storage ([§15.2.4])
    * Document Settings ([§11.3.3])
    * Endnotes ([§11.3.4])
    * Font Table ([§11.3.5])
    * Footnotes ([§11.3.7])
    * Glossary Document ([§11.3.8])
    * Numbering Definitions ([§11.3.11])
    * Style Definitions ([§11.3.12])
    * Theme ([§14.2.7])
    * Thumbnail ([§15.2.16])
    
    A Main Document part is permitted to contain explicit relationships to the following parts defined by ECMA-376:
    
    * Alternative Format Import ([§11.3.1])
    * Chart ([§14.2.1])
    * Content Part ([§15.2.4])
    * Diagrams: Diagram Colors([§14.2.3]), Diagram Data([§14.2.4]), Diagram Layout Definition([§14.2.5])and Diagram Styles ([§14.2.6])
    * Embedded Control Persistence ([§15.2.9])
    * Embedded Object ([§15.2.10])
    * Embedded Package ([§15.2.11])
    * Footer ([§11.3.6])
    * Header ([§11.3.9])
    * Hyperlinks ([§15.3])
    * Images ([§15.2.14])
    * Printer Settings ([§15.2.15])
    * Subdocument ([§11.6])
    * Video ([§15.2.17])
    
    A Main Document shall not have implicit or explicit relationships to any other part defined by ECMA-376.

### 11.3.11 编号定义部件

=== "中文"

    **编号定义部件**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.numbering+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/numbering</td>
        </tr>
    </table>


    该部件类型的一个实例包含该文档中每个唯一编号定义的结构定义。
    
    [示例：如果一组段落被添加到文档中，并且在第一级使用圆点符号，第二级使用方块符号，第三级使用勾号符号，如下所示：
    
    • 第一级
    
    &nbsp;&nbsp;&nbsp;&nbsp;□ 第二级

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;✔ 第三级
    
    编号定义部件包含每个级别的定义（它们的符号样式、缩进等），即使第二级和第三级在文档中实际上没有使用。结束示例]
    
    一个包不应包含超过两个编号定义部件。如果存在，则该部件的一个实例应是从主文档（[§11.3.10]）部件的隐式关系的目标，另一个实例应是从词汇表文档（[§11.3.8]）部件的隐式关系的目标。

    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/numbering" Target="numbering.xml"/>
        </Relationships>
        ```
    
    列表使用的 XML 标记涉及通过 numPr 元素的子元素引用编号定义。
    
    !!! info "示例"
    
        这里我们有一个使用样式 Text 的段落集，后面是一组使用段落样式 ListBullet 的事物列表，然后是另一个使用样式 Text 的段落集：

        ```xml
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Text"/>
            </w:pPr>
            <w:r>
                <w:t>The kinds of fruit needed are:</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                </w:numPr>
            </w:pPr>
            <w:r>
                <w:t>Apples</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                </w:numPr>
            </w:pPr>
            <w:r>
                <w:t>Oranges</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Text"/>
            </w:pPr>
            <w:r>
                <w:t>Other items may be needed too.</w:t>
            </w:r>
        </w:p>
        ```

    编号定义部件的根元素应为 numbering，每个编号定义由 abstractNum 元素定义。

    !!! info "Example"

        ```xml
        <w:numbering xmlns:w="…">
            <w:abstractNum w:numId="11">
                <w:nsid w:val="394E2425"/>
                <w:multiLevelType w:val="hybridMultilevel"/>
                <w:tmpl w:val="F628E89A"/>
                <w:lvl w:ilvl="0" w:tplc="151C4798">
                    <w:start w:val="1"/>
                    <w:numFmt w:val="bullet"/>
                    <w:pStyle w:val="ListBullet"/>
                    <w:lvlText w:val="…"/>
                    <w:lvlJc w:val="start"/>
                    <w:pPr>
                        <w:tabs>
                            <w:tab w:val="num" w:pos="720"/>
                        </w:tabs>
                        <w:ind w:start="720" w:hanging="360"/>
                    </w:pPr>
                    <w:rPr>
                        <w:rFonts w:ascii="Symbol" w:hAnsi="Symbol" w:hint="default"/>
                    </w:rPr>
                </w:lvl>
                …
            </w:abstractNum>
        </w:numbering>
        ```
    
    编号定义部件应位于包含关系部件的包内（在语法上表达，关系元素的 TargetMode 属性应该是 Internal）。
    
    编号定义部件允许包含对由 ECMA-376 定义的以下部件的显式关系：
    
    * 图像(Images)（[§15.2.14]）
    
    编号定义部件不得具有与 ECMA-376 定义的任何其他部件的隐式或显式关系。
    

=== "英文"

    **Numbering Definitions Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.numbering+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/numbering</td>
        </tr>
    </table>
    
    An instance of this part type contains a definition for the structure of each unique numbering definition in this document.
    
    [Example: If a set of paragraphs are added to a document which have a circle bullet at the first level, a square bullet at the second level, and a checkmark bullet at the third level, such as the following:
    
    &#8226; First level

    &nbsp;&nbsp;&nbsp;&nbsp;&#9633; Second level

    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10003; Third level
    
    The numbering definition part contains the definition for each of these levels (their bullet style, indent, etc.) even if the second and third levels are not actually used in the document end example]

    A package shall contain no more than two Numbering Definitions parts. If they exist, one instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.

    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId2"
                Type="http://…/numbering" Target="numbering.xml"/>
        </Relationships>
        ```

    The XML markup for a list usage involves a reference to a numbering definition via the child elements of the numPr element.

    !!! info "Example"

        Here we have a paragraph set using the style Text, followed by a list of things which have the paragraph style ListBullet, followed by another paragraph set using the style Text:

        ```xml
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Text"/>
            </w:pPr>
            <w:r>
                <w:t>The kinds of fruit needed are:</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                </w:numPr>
            </w:pPr>
            <w:r>
                <w:t>Apples</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:ilvl w:val="0" />
                    <w:numId w:val="5" />
                </w:numPr>
            </w:pPr>
            <w:r>
                <w:t>Oranges</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:pPr>
                <w:pStyle w:val="Text"/>
            </w:pPr>
            <w:r>
                <w:t>Other items may be needed too.</w:t>
            </w:r>
        </w:p>
        ```

    The root element for a Numbering Definition part shall be numbering, with each numbering definition being defined by an abstractNum element.

    !!! info "Example"

        ```xml
        <w:numbering xmlns:w="…">
            <w:abstractNum w:numId="11">
                <w:nsid w:val="394E2425"/>
                <w:multiLevelType w:val="hybridMultilevel"/>
                <w:tmpl w:val="F628E89A"/>
                <w:lvl w:ilvl="0" w:tplc="151C4798">
                    <w:start w:val="1"/>
                    <w:numFmt w:val="bullet"/>
                    <w:pStyle w:val="ListBullet"/>
                    <w:lvlText w:val="…"/>
                    <w:lvlJc w:val="start"/>
                    <w:pPr>
                        <w:tabs>
                            <w:tab w:val="num" w:pos="720"/>
                        </w:tabs>
                        <w:ind w:start="720" w:hanging="360"/>
                    </w:pPr>
                    <w:rPr>
                        <w:rFonts w:ascii="Symbol" w:hAnsi="Symbol" w:hint="default"/>
                    </w:rPr>
                </w:lvl>
                …
            </w:abstractNum>
        </w:numbering>
        ```

    A Numbering Definitions part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Numbering Definitions part is permitted to contain explicit relationships to the following parts defined by ECMA-376:

    * Images ([§15.2.14])

    A Numbering Definitions part shall not have any implicit or explicit relationships to any other part defined by ECMA-376.
    
    
### 11.3.12 样式定义部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.styles+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/styles</td>
        </tr>
    </table>

    该部件类型的一个实例包含了该文档中使用的一组样式的定义。
    
    一个包最多应包含两个样式定义部件。其中一个部件的一个实例应该是从主文档（[§11.3.10]）部件的隐式关系的目标，另一个应该是从词汇表文档（[§11.3.8]）部件的隐式关系的目标。
    
    !!! info "示例"
        
        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/styles" Target="styles.xml"/>
        </Relationships>
        ```
    
    样式定义部件的根元素应该是 styles，它是一个包含一个或多个样式元素的容器。
    
    [示例：这是 ListBullet 样式（在§11.3.10中的主文档部件中使用）：
    
    ```xml
    <w:styles xmlns:w="…" … xml:space="preserve">
        <w:style w:type="paragraph" w:styleId="ListBullet">
            <w:name w:val="List Bullet"/>
            <w:basedOn w:val="Text"/>
            <w:autoRedefine/>
            <w:rsid w:val="00081289"/>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:numId w:val="1"/>
                </w:numPr>
                <w:tabs>
                    <w:tab w:val="clear" w:pos="360"/>
                </w:tabs>
                <w:ind w:start="648"/>
            </w:pPr>
        </w:style>
    </w:styles>
    ```
    
    结束示例]
    
    样式定义部件应位于包含关系部件的包内（在语法上表达，关系元素的 TargetMode 属性应该是 Internal）。
    
    样式定义部件不得具有与 ECMA-376 定义的任何其他部件的隐式或显式关系。


=== "英文"

    **Style Definitions Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.styles+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/styles</td>
        </tr>
    </table>

    An instance of this part type contains the definition for a set of styles used by this document.

    A package shall contain at most two Style Definitions parts. One instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship in from the Glossary Document ([§11.3.8]) part.

    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/styles" Target="styles.xml"/>
        </Relationships>
        ```

    The root element for a Styles Definition part shall be styles, which is a container for one or more style elements.

    [Example: Here is the style ListBullet (which is used in a Main Document Part in §11.3.10):

    ```xml
    <w:styles xmlns:w="…" … xml:space="preserve">
        <w:style w:type="paragraph" w:styleId="ListBullet">
            <w:name w:val="List Bullet"/>
            <w:basedOn w:val="Text"/>
            <w:autoRedefine/>
            <w:rsid w:val="00081289"/>
            <w:pPr>
                <w:pStyle w:val="ListBullet"/>
                <w:numPr>
                    <w:numId w:val="1"/>
                </w:numPr>
                <w:tabs>
                    <w:tab w:val="clear" w:pos="360"/>
                </w:tabs>
                <w:ind w:start="648"/>
            </w:pPr>
        </w:style>
    </w:styles>
    ```

    end example]

    A Style Definitions part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Style Definitions part shall not have implicit or explicit relationships to any part defined by ECMA-376.

### 11.3.13 web设置部件

=== "中文"

    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.webSettings+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/webSettings</td>
        </tr>
    </table>
    
    该部件类型的一个实例包含了文档中使用的特定于网络的设置的定义。
    
    一个包最多应包含两个网页设置部件。其中一个部件的一个实例应该是从主文档（[§11.3.10]）部件的隐式关系的目标，另一个应该是从词汇表文档（[§11.3.8]）部件的隐式关系的目标。
    
    !!! info "示例"
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId3"
            Type="http://…/webSettings" Target="webSettings.xml"/>
    </Relationships>
    ```
    
    网页设置部件的根元素应该是 webSettings。
    
    !!! info "示例"
    
    ```xml
    <w:webSettings …>
        <w:frameset>
            …
            <w:frame>
                <w:sz w:val="216" />
                <w:name w:val="Frame2" />
                <w:sourceFileName r:id="rId1" />
            </w:frame>
            <w:frame>
                <w:name w:val="Frame1" />
                <w:sourceFileName r:id="rId2" />
            </w:frame>
        </w:frameset>
    </w:webSettings>
    ```
    
    网页设置部件应位于包含关系部件的包内（在语法上表达，关系元素的 TargetMode 属性应该是 Internal）。
    
    网页设置部件允许包含对由 ECMA-376 定义的以下部件的显式关系：
    
    * 框架集(Frameset)（[§11.5]）
    
    网页设置部件不得具有与 ECMA-376 定义的任何其他部件的隐式或显式关系。

=== "英文"

    **Web Settings Part**
    <table border=1>
        <tr>
            <td>**Content Type**:</td>
            <td>
                application/vnd.openxmlformats-officedocument.wordprocessingml.webSettings+xml
            </td>
        </tr>
        <tr>
            <td>**Root Namespace**:</td>
            <td>http://purl.oclc.org/ooxml/wordprocessingml/main</td>
        </tr>
        <tr>
            <td>**Source Relationship**:</td>
            <td>http://purl.oclc.org/ooxml/officeDocument/relationships/webSettings</td>
        </tr>
    </table>

    An instance of this part type contains the definition for web-specific settings used by this document.

    A package shall contain at most two Web Settings parts. One instance of that part shall be the target of an implicit relationship from the Main Document ([§11.3.10]) part, and the other shall be the target of an implicit relationship from the Glossary Document ([§11.3.8]) part.

    !!! info "Example"

        ```xml
        <Relationships xmlns="…">
            <Relationship Id="rId3"
                Type="http://…/webSettings" Target="webSettings.xml"/>
        </Relationships>
        ```

    The root element for a Web Settings part shall be webSettings.
    
    !!! info "Example"

        ```xml
        <w:webSettings …>
            <w:frameset>
                …
                <w:frame>
                    <w:sz w:val="216" />
                    <w:name w:val="Frame2" />
                    <w:sourceFileName r:id="rId1" />
                </w:frame>
                <w:frame>
                    <w:name w:val="Frame1" />
                    <w:sourceFileName r:id="rId2" />
                </w:frame>
            </w:frameset>
        </w:webSettings>
        ```

    A Web Settings part shall be located within the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be Internal).

    A Web Settings part is permitted to contain explicit relationships to the following parts defined by ECMA-376:
    
    * Frameset ([§11.5])
    
    A Web Settings part shall not have implicit or explicit relationships to any other part defined by ECMA-376.

## 11.4 文档模板

**Document Template**

=== "中文"

    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/attachedTemplate`

    文档模板可以通过WordprocessingML包的一个实例来表示，其中包含了样式、编号定义等元素，这些元素在基于该模板编辑文档时可供使用。WordprocessingML文档可以通过包含一个文档设置部件（[§11.3.3]）来引用另一个文档作为其文档模板，该部件使用附加模板元素的id属性显式指定了所需文档模板的文件位置。
    
    [示例：考虑一个指定位于`c:\template.docx`的文档模板的文档：
    
    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId1"
            Type="http://.../attachedTemplate" Target="file:///c:\template.docx"
            TargetMode="External"/>
    </Relationships>
    ```
    
    文档的“文档设置”部件包含一个`attachedTemplate`元素，它显式引用了这个关系：
    
    ```xml
    <w:settings ...>
        <w:attachedTemplate r:id="rId1"/>
    </w:settings>
    ```
    
    示例结束]

=== "英文"

    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/attachedTemplate`

    A document template can be represented by an instance of a WordprocessingML package, and contains styles, numbering definitions, and so on that are made available when documents based on that template are edited. A WordprocessingML document can refer to another document as its document template, by having a Document Settings part ([§11.3.3])that contains an explicit relationship to the file location of the necessary document template using the id attribute on the attachedTemplate element.

    [Example: Consider a document specifying a document template located at c:\template.docx:

    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://…/attachedTemplate" Target="file:///c:\template.docx"
            TargetMode="External"/>
    </Relationships>
    ```

    The document’s Document Settings part contains an attachedTemplate element that explicitly references this relationship:
    
    ```xml
    <w:settings … >
    <w:attachedTemplate r:id="rId1"/>
    </w:settings>
    ```
    
    end example]

## 11.5 框架集

**Framesets**

=== "中文"

    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/frame`
    
    框架集(frameset)是一个WordprocessingML文档，用于指定其他WordprocessingML文档（在该上下文中称为框架）的位置和布局。框架集应由一个WordprocessingML文档的实例表示，该文档包含一个网页设置(Web Settings)部件（[§11.3.13]），其关系项指向该框架集的每个框架。
    
    [示例：考虑一个包含两个框架的框架集文档。该框架集的网页设置部件-关系项包含以下内容，其中`frame1.docx`和`frame2.docx`是包含相应框架的包：
    
    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId1"
            Type="http://.../frame" Target="frame1.docx" TargetMode="External"/>
        <Relationship Id="rId2"
            Type="http://.../frame" Target="frame2.docx" TargetMode="External"/>
    </Relationships>
    ```
    
    框架集(frameset)文档的网页设置(Web Settings)部件包含一个框架集(frameset)元素，该元素引用其框架：
    
    ```xml
    <w:webSettings ...>
        <w:frameset>
            ...
            <w:frame>
                <w:sz w:val="216" />
                <w:name w:val="Frame2" />
                <w:sourceFileName r:id="rId1" />
            </w:frame>
            <w:frame>
                <w:name w:val="Frame1" />
                <w:sourceFileName r:id="rId2" />
            </w:frame>
        </w:frameset>
    </w:webSettings>
    ```
    
    示例结束]
    
    框架应由WordprocessingML包的一个实例表示。
    
    框架应位于包含关系部件的包外部（语法上表达，即 Relationship元素 的 TargetMode属性 应为 External ）。

=== "英文"
    
    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/frame`
    
    A frameset is a WordprocessingML document which specifies the location and placement of other WordprocessingML documents (which, when used in this context, are referred to as frames). A frameset shall be represented by an instance of a WordprocessingML document with a Web Settings part ([§11.3.13]) whose relationship item targets each of that frameset's frames.
    
    [Example: Consider a frameset document having two frames. The frameset's Web Settings part-relationships item contains the following, in which frame1.docx and frame2.docx are packages containing the corresponding frames:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://…/frame" Target="frame1.docx" TargetMode="External"/>
        <Relationship Id="rId2"
            Type="http://…/frame" Target="frame2.docx" TargetMode="External"/>
    </Relationships>
    ```
    
    The frameset document’s Web Settings part contains a frameset element that references its frames:
    
    ```xml
    <w:webSettings …>
        <w:frameset>
            …
            <w:frame>
                <w:sz w:val="216" />
                <w:name w:val="Frame2" />
                <w:sourceFileName r:id="rId1" />
            </w:frame>
            <w:frame>
                <w:name w:val="Frame1" />
                <w:sourceFileName r:id="rId2" />
            </w:frame>
        </w:frameset>
    </w:webSettings>
    ```
    
    end example]
    
    A frame shall be represented by an instance of a WordprocessingML package.
    
    A frame shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

## 11.6 主文档和子文档

**Master Documents and Subdocuments**

=== "中文"
    
    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument`

    主文档(master document)应由一个WordprocessingML文档的实例表示，其主文档（[§11.3.10]）部件指向该主文档的每个子文档。
    
    [理由：有时，将文档作为一系列片段来处理会比较方便，特别是当这些片段可能由协作组中的不同作者编辑时。也许将一本书视为章节的集合而不是一个大文档更有意义。通过拥有一个或多个子文档的主文档来将文档拆分成这样的片段是可以实现的。理由结束]
    
    [示例：考虑一个主文档，其三个子文档分别称为Start、Middle和End。主文档的主文档部件(Main Document part)具有一个相应的关系部件，其中包含以下内容，其中Start.docx、Middle.docx和End.docx分别是包含相应子文档的包：

    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId5"
            Type="http://.../subDocument"
            Target="Start.docx" TargetMode="External"/>
        <Relationship Id="rId6"
            Type="http://.../SubDocument"
            Target="Middle.docx" TargetMode="External"/>
        <Relationship Id="rId7"
            Type="http://.../SubDocument"
            Target="End.docx" TargetMode="External"/>
    </Relationships>
    ```
    
    主文档的主文档部件包含引用其子文档的subDoc元素：

    ```xml
    <w:document xmlns:r="..." xmlns:w="..." ...>
        <w:body>
            <w:p ...>
                <w:pPr>
                ...
                </w:pPr>
            </w:p>
            <w:subDoc r:id="rId5"/>
            ...
            <w:subDoc r:id="rId6"/>
            ...
            <w:subDoc r:id="rId7"/>
            ...
        </w:body>
    </w:document>
    ```
    
    示例结束]
    
    子文档应由WordprocessingML包的一个实例表示。
    
    子文档应位于包含关系部件的包外部（句法上表示为，Relationship元素的TargetMode属性应为External）。

=== "英文"
    
    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument`

    A master document shall be represented by an instance of a WordprocessingML document whose Main Document ([§11.3.10]) part targets each of that master document’s subdocuments.
    
    [Rationale: Sometimes, it is convenient to deal with a document as a collection of pieces, especially when those pieces might be edited by different authors in a collaborative group. Perhaps it simply makes sense to think about a book as a collection of chapters rather than as one big document. The breaking-up of a document into such pieces can be achieved by having a master document with one or more subdocuments. end rationale]
    
    [Example: Consider a master document, whose three subdocuments are called Start, Middle, and End, respectively. Master’s Main Document part has a corresponding relationships part that contains the following, in which Start.docx, Middle.docx, and End.docx are packages containing the corresponding subdocuments:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId5"
            Type="http://…/subDocument"
            Target="Start.docx" TargetMode="External"/>
        <Relationship Id="rId6"
            Type="http://…/SubDocument"
            Target="Middle.docx" TargetMode="External"/>
        <Relationship Id="rId7"
            Type="http://…/SubDocument"
            Target="End.docx" TargetMode="External"/>
    </Relationships>
    ```
    
    
    The master document’s Main Document part contains subDoc elements that reference its subdocuments:
    
    ```xml
    <w:document xmlns:r="…" xmlns:w="…" …>
        <w:body>
            <w:p …>
                <w:pPr>
                …
                </w:pPr>
            </w:p>
            <w:subDoc r:id="rId5"/>
            …
            <w:subDoc r:id="rId6"/>
            …
            <w:subDoc r:id="rId7"/>
            …
        </w:body>
    </w:document>
    ```
    
    
    end example]
    
    A subdocument shall be represented by an instance of a WordprocessingML package.
    
    A subdocument shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

## 11.7 邮件合并数据源

**Mail Merge Data Source**

=== "中文"

    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/mailMergeSource`

    一个存储有关邮件合并操作信息的文档可以包含一个文档设置部件（[§11.3.3]），其关系项使用此关系目标指向所需数据源的文件位置。
    
    [示例：考虑一个指定数据源位于http://www.openxmlformats.org/data.txt的邮件合并文档：
    
    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId1"
            Type="http://.../mailMergeSource"
            Target="http://www.openxmlformats.org/data.txt"
            TargetMode="External"/>
    </Relationships>
    ```
    
    文档的文档设置部件包含一个明确引用此关系的数据源元素：
    
    ```xml
    <w:settings ...>
        <w:mailMerge>
            ...
            <w:dataSource r:id="rId1" />
            ...
        </w:mailMerge>
    </w:settings>
    ```
    
    示例结束]
    
    邮件合并数据源应位于包含关系部件的包外部（句法上表示为，Relationship元素的TargetMode属性应为External）。


=== "英文"

    **Source Relationship**: `http://purl.oclc.org/ooxml/officeDocument/relationships/mailMergeSource`

    A document that stores information about a mail merge operation is permitted to contain a Document Settings part ([§11.3.3])whose relationship item targets the file location of the necessary data source using this relationship.
    
    [Example: Consider a document specifying a mail merge whose data source is located at http://www.openxmlformats.org/data.txt:
        
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId1"
            Type="http://…/mailMergeSource"
            Target="http://www.openxmlformats.org/data.txt"
            TargetMode="External"/>
    </Relationships>
    ```
    
    
    The document’s Document Settings part contains a dataSource element that explicitly references this relationship:
    
    ```xml
    <w:settings …>
        <w:mailMerge>
            …
            <w:dataSource r:id="rId1" />
            …
        </w:mailMerge>
    </w:settings>
    ```
    
    
    end example]
    
    A mail merge data source shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

## 11.8 邮件合并标头数据源

**Mail Merge Header Data Source**

=== "中文"

    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/mailMergeHeaderSource`

    一个存储有关邮件合并操作信息的文档可以包含一个文档设置部件（[§11.3.3]），其关系项通过此关系指向必要标题数据源的文件位置。
    
    [示例：考虑一个指定标题数据源位于<http://www.openxmlformats.org/header.txt>的邮件合并文档：

    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId2"
            Type="http://.../mailMergeHeaderSource"
            Target="http://www.openxmlformats.org/header.txt"
            TargetMode="External"/>
    </Relationships>
    ```
    
    文档的文档设置部件包含一个明确引用此关系的headerSource元素：

    ```xml
    <w:settings ...>
        <w:mailMerge>
            ...
            <w:headerSource r:id="rId2" />
            ...
        </w:mailMerge>
    </w:settings>
    ```
    
    示例结束]
    
    邮件合并标题数据源应位于包含关系部件的包外部（句法上表示为，Relationship元素的TargetMode属性应为External）。

=== "英文"

    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/mailMergeHeaderSource`
    
    A document that stores information about a mail merge operation is permitted to contain a Document Settings part ([§11.3.3])whose relationship item targets the file location of the necessary header data source using this relationship.
    
    [Example: Consider a document specifying a mail merge whose header data source is located at http://www.openxmlformats.org/header.txt:
    
    ```xml
    <Relationships xmlns="…">
        <Relationship Id="rId2"
            Type="http://…/mailMergeHeaderSource"
            Target="http://www.openxmlformats.org/header.txt"
            TargetMode="External"/>
    </Relationships>
    ```
    
    
    The document’s Document Settings part contains a headerSource element that explicitly references this relationship:
    
    ```xml
    <w:settings …>
        <w:mailMerge>
            …
            <w:headerSource r:id="rId2" />
            …
        </w:mailMerge>
    </w:settings>
    ```
    
    end example]
    
    A mail merge header data source shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).

## 11.9 XSL 转换

**XSL Transformation**


=== "中文"

    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/transform`
    
    文档可以存储关于XSL转换的信息，该转换可能在文档以单个文件格式输出时（例如，作为XML或HTML）应用。这些信息存储在一个文档设置部件（[§11.3.3]）中，其部件关系项包含使用此关系到XSL转换文件位置的显式关系。[注意：关于此关系如何使用（结合saveThroughXslt元素）的完整描述，请参阅**[§17.15.1.76]**。]
    
    [示例：考虑一个指定XSL转换位于<http://www.openxmlformats.org/test.xsl>的文档：

    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId8" Type="http://.../transform"
                      Target="http://www.openxmlformats.org/test.xsl"
                      TargetMode="External"/>
    </Relationships>
    ```
    
    文档的文档设置部件包含一个显式引用此关系的saveThroughXslt元素：

    ```xml
    <w:settings …>
        …
        <w:saveThroughXslt r:id="rId8" />
        …
    </w:settings>
    ```
    
    示例结束]
    
    XSL转换应当位于包含关系部件的包外部（句法上表达为，Relationship元素的TargetMode属性应为External）。

=== "英文"

    Source Relationship: `http://purl.oclc.org/ooxml/officeDocument/relationships/transform`
    
    A document can store information about an XSL Transformation which might be applied when the document is output as a single file (e.g. as XML or HTML).That information is stored in a Document Settings part ([§11.3.3])whose part relationship item contains an explicit relationship to the file location of the XSL Transformation using this relationship. [Note: A full description of how this relationship is used (in conjunction with the saveThroughXslt element) is provided in **[§17.15.1.76]**. end note]
    
    [Example: Consider a document specifying an XSL Transformation located at http://www.openxmlformats.org/test.xsl:

    ```xml
    <Relationships xmlns="...">
        <Relationship Id="rId8" Type="http://.../transform"
                      Target="http://www.openxmlformats.org/test.xsl"
                      TargetMode="External"/>
    </Relationships>
    ```
    
    The document’s Document Settings part contains a saveThroughXslt element that explicitly references this relationship:

    ```xml
    <w:settings …>
        …
        <w:saveThroughXslt r:id="rId8" />
        …
    </w:settings>
    ```
    
    end example]
    
    An XSL transformation shall be located external to the package containing the relationships part (expressed syntactically, the TargetMode attribute of the Relationship element shall be External).


[§11.1]: #111-wordprocessingml特定术语表
[§11.2]: #112-包结构
[§11.3]: #113-部件概览
[§11.3.1]: #1131-替代格式导入部件
[§11.3.2]: #1132-注释部件
[§11.3.3]: #1133-文档设置部件
[§11.3.4]: #1134-尾注部件
[§11.3.5]: #1135-字体表部件
[§11.3.6]: #1136-页脚部件
[§11.3.7]: #1137-脚注部件
[§11.3.8]: #1138-术语表部件
[§11.3.9]: #1139-头部部件
[§11.3.10]: #11310-主文档部件
[§11.3.11]: #11311-编号定义部件
[§11.3.12]: #11312-样式定义部件
[§11.3.13]: #11313-web设置部件
[§11.4]: #114-文档模板
[§11.5]: #115-框架集
[§11.6]: #116-主文档和子文档
[§11.7]: #117-邮件合并数据源
[§11.8]: #118-邮件合并标头数据源
[§11.9]: #119-xsl-转换

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

[§15]: ./chapter-15.md#15-共享
[§15.1]: ./chapter-15.md#151-共享术语词汇表
[§15.2]: ./chapter-15.md#152-部件概览
[§15.2.1]: ./chapter-15.md#1521-附加特性部件
[§15.2.2]: ./chapter-15.md#1522-音频部件
[§15.2.3]: ./chapter-15.md#1523-参考文献部件
[§15.2.4]: ./chapter-15.md#1524-内容部件
[§15.2.5]: ./chapter-15.md#1525-自定义xml数据存储部件
[§15.2.6]: ./chapter-15.md#1526-自定义-xml-数据存储属性部件
[§15.2.7]: ./chapter-15.md#1527-数字签名起源部件
[§15.2.8]: ./chapter-15.md#1528-数字签名-xml-签名部件
[§15.2.9]: ./chapter-15.md#1529-嵌入式控制持久化部件
[§15.2.10]: ./chapter-15.md#15210-嵌入对象部件
[§15.2.11]: ./chapter-15.md#15211-嵌入包部件
[§15.2.12]: ./chapter-15.md#15212-文件属性部件
[§15.2.12.1]: ./chapter-15.md#152121-核心文件属性部件
[§15.2.12.2]: ./chapter-15.md#152122-自定义文件属性部件
[§15.2.12.3]: ./chapter-15.md#152123-扩展文件属性部件
[§15.2.13]: ./chapter-15.md#15213-字体部件
[§15.2.14]: ./chapter-15.md#15214-图片部件
[§15.2.15]: ./chapter-15.md#15215-打印机设置部件
[§15.2.16]: ./chapter-15.md#15216-缩略图部件
[§15.2.17]: ./chapter-15.md#15217-视频部件
[§15.3]: ./chapter-15.md#153-超链接