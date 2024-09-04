# 17.17 杂项主题

**Miscellaneous Topics**


=== "中文"
    
    本节涵盖了在WordprocessingML文档中其他地方未涵盖的主题。

=== "英文"
    
    This section covers topics not covered elsewhere within the WordprocessingML documentation.

## 17.17.1 子文档

**Subdocuments**

=== "中文"

    在WordprocessingML文档中，有时需要将一个大型文档拆分为两个或多个单独的WordprocessingML文档文件，以便每个文件可以独立地分发、编辑和处理。

    [示例：一本书可能由五章组成，每一章由不同的作者编辑。因此，书籍的编辑者希望创建六个WordprocessingML文档 - 每个作者都可以在其章节上进行工作，并创建一个主文档，该文档适当地整合了五章的内容。示例结束]
    
    当一个WordprocessingML文档以这种方式由其他WordprocessingML文档组成时，生成的文档称为主文档及其子文档。
    
    - 子文档是一个WordprocessingML文档 - 文档中没有特定的信息将其分类为子文档，除非它被合并到另一个文档中。
    - 主文档是一个将一个或多个子文档（以及可选的WordprocessingML内容）合并起来创建较大文档的文档。
    
    [示例：考虑一个用于编写书籍的WordprocessingML文档：
    
    ![123](./imgs/Image11624.png)
    
    为了让多个作者共同编写该文档，书中的每一章都放在一个单独的文件中（下面突出显示的部分）：
    
    ![123](./imgs/Image11626.png)
    
    结果是三个WordprocessingML文档：
    
    - 一个主文档（包含书籍的标题、第一段落以及每一章的子文档的引用）
    - 两个子文档（每个章节一个）示例结束]

=== "英文"

    Within a WordprocessingML document, it is sometimes necessary to break a large document into two or more separate WordprocessingML document files, allowing each of these files to be distributed, edited, and handled independently.

    [Example: A book might consist of five chapters, each edited by a separate author. The editor for the book would therefore desire to create six WordprocessingML documents - one for each author to work on their chapter, and a main document which collates the content of the five chapters appropriately. end example]
    
    When a WordprocessingML document is comprised of other WordprocessingML documents in this way, the
    resulting documents are called a master document and its subdocuments.
    
    - A subdocument is a WordprocessingML document - there is no specific information in a document which classifies it as such, other than that it is incorporated into another document.
    - A master document is a document which incorporates one or more subdocuments (as well as optional WordprocessingML content) to create a larger document
    
    [Example: Consider a WordprocessingML document which is being used to write a book:
    
    ![123](./imgs/Image11624.png)

    To allow this document to be written by multiple authors, each chapter in the book is placed in a separate file (the sections highlighted in red below):

    ![123](./imgs/Image11626.png)

    The result is three WordprocessingML documents:

    - A master document (containing the title of the book, the first paragraph, and references to the subdocuments for each chapter)
    - Two subdocuments (one for each chapter)

    end example]

### 17.17.1.1 subDoc (子文档位置的锚点)

**subDoc (Anchor for Subdocument Location)**

=== "中文"
    
    该元素指定主文档中的位置，用于插入指定子文档的内容。指定的子文档内容应根据需要显示在主文档中的指定位置，但应保留为子文档位置指定的独立文件的一部分。子文档的位置应由其Id属性与此元素上的id属性匹配的关系来指定。
    
    如果此元素指定的关系的关系类型不是 http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument ，不存在或没有TargetMode属性值为External，则应将文档视为不符合规范。
    
    当子文档在主文档中指定的位置显示时，以下逻辑确定了如何处理子文档和相关主文档的样式和格式：
    
    - 子文档中的所有直接格式将被保留。
    - 对于每个子文档中的样式：
        - 如果在主文档中存在具有相同styleId属性值的样式，则使用主文档中的样式显示子文档的内容。
        - 否则，将样式导入主文档并使用原始样式显示内容。
        - 如果后续的子文档也包含具有相同styleId属性值的样式，则忽略后者的样式，并使用导入到主文档的样式版本显示内容。
    
    [示例：考虑由三章组成的书，其中两章已被分成以下子文档（红色矩形表示每个子文档内容的边界）：
    
    ![123](./imgs/Image11626.png)
    
    生成的主文档将包括其自己的WordprocessingML内容以及适当位置的子文档锚点：
    
    ```xml
    <w:body>
        <w:p>
            …
            <w:r>
                <w:t>My Book</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Once upon a time…</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:subDoc r:id="subDocRel1" />
        </w:p>
        <w:p>
            <w:subDoc r:id="subDocRel2" />
        </w:p>
        <w:sectPr>
            …
        </w:sectPr>
    </w:body>
    ```
    
    两个subDoc元素指定了与id为subDocRel1和subDocRel2的关系对应的子文档必须在第一和第二段内容之后按顺序导入。检查相应关系部分项目的内容，我们可以看到这些关系的目标：
    
    ```xml
    <Relationships … >
        …
        <Relationship Id="subDocRel1" TargetMode="External"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument"
            Target="Chapter1.docx" />
        <Relationship Id="subDocRel2" TargetMode="External"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument"
            Target="Chapter2.docx" />
        …
    </Relationships>
    ```
    
    相应的关系部分项目显示，要导入的两个文件位于与当前文件相同的位置，分别命名为Chapter1.docx和Chapter2.docx。示例结束]
    
    ??? abstract "Attributes"
    
        **id**（关系到部件）
        
        :   命名空间：http://purl.oclc.org/ooxml/officeDocument/relationships
        
            指定到指定部件的关系ID。
        
            指定的关系应与父元素所需的关系类型相匹配：
            
            - 对于contentPart元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/customXml
            - 对于footerReference元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/footer
            - 对于headerReference元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/header
            - 对于embedBold、embedBoldItalic、embedItalic或embedRegular元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/font
            - 对于printerSettings元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/printerSettings
            - 对于longDesc或hyperlink元素，关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/hyperlink
            
            [示例：考虑一个具有以下id属性的XML元素：
            
            ```xml
            <… r:id="rId10" />
            ```
            
            该标记指定与关系ID rId1相关联的关系部件，其中包含父XML元素的相应关系信息。示例结束]
            
            The possible values for this attribute are defined by the ST_RelationshipId simple type ([§22.8.2.1]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Rel) is located in §A.1. end note]

=== "英文"
    
    This element specifies a location within a master document for the insertion of the contents of a specified subdocument. The specified subdocument's contents should appear at the specified location within the master document as needed, but shall remain part of the separate file specified by the subdocument location. The location of the subdocument shall be specified by the relationship whose Id attribute matches the id attribute on this element.
    
    If the relationship type of the relationship specified by this element is not http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument, is not present, or does not have a TargetMode attribute value of External, then the document shall be considered non-conformant.
    
    When a subdocument is displayed at the specified location within the master document, the following logic determines how the styles and formatting of the subdocument and associated master document shall be handled:
    
    - All direct formatting in the subdocument is retained.
    - For each style in each subdocument:
        - If a style with the same styleId attribute value exists in the master document, display the contents of the subdocument using the style in the master document.
        - Otherwise, import the style into the master document and display the content using the original style.
        - If a subsequent subdocument also contains a style with the same styleId attribute value, the latter’s style is ignored and the content is displayed using the version of the style imported into the master document.
    
    [Example: Consider a book consisting of three chapters, two of which have been divided into subdocuments as follows (the red rectangle indicates the bounds of each subdocument's contents):
    
    ![123](./imgs/Image11626.png)
    
    The resulting master document would consist of its own WordprocessingML content as well as subdocument anchors in the appropriate locations:
    
    ```xml
    <w:body>
        <w:p>
            …
            <w:r>
                <w:t>My Book</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Once upon a time…</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:subDoc r:id="subDocRel1" />
        </w:p>
        <w:p>
            <w:subDoc r:id="subDocRel2" />
        </w:p>
        <w:sectPr>
            …
        </w:sectPr>
    </w:body>
    ```
    
    The two subDoc elements specify that the subdocuments targeted by the relationships with an ID of subDocRel1 and subDocRel2 must be imported in that order after the content of the first two paragraphs of content. Examining the contents of the corresponding relationship part item, we can see the targets for those relationships:
    
    ```xml
    <Relationships … >
        …
        <Relationship Id="subDocRel1" TargetMode="External"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument"
            Target="Chapter1.docx" />
        <Relationship Id="subDocRel2" TargetMode="External"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/subDocument"
            Target="Chapter2.docx" />
        …
    </Relationships>
    ```
    
    The corresponding relationship part item shows that the two files to be imported are located in the same location as the current file and name Chapter1.docx and Chapter2.docx respectively. end example]
    
    ??? abstract "Attributes"
    
        **id** (Relationship to Part)
    
        :   Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
        
            Specifies the relationship ID to a specified part.
    
            The specified relationship shall match the relationship type required by the parent element:
            
            - http://purl.oclc.org/ooxml/officeDocument/relationships/customXml for the contentPart element
            - http://purl.oclc.org/ooxml/officeDocument/relationships/footer for the footerReference element
            - http://purl.oclc.org/ooxml/officeDocument/relationships/header for the headerReference element
            - http://purl.oclc.org/ooxml/officeDocument/relationships/font for the embedBold, embedBoldItalic, embedItalic, or embedRegular elements
            - http://purl.oclc.org/ooxml/officeDocument/relationships/printerSettings for the printerSettings element
            - http://purl.oclc.org/ooxml/officeDocument/relationships/hyperlink for the longDesc or hyperlink element
            
            [Example: Consider an XML element which has the following id attribute:
            
            ```xml
            <… r:id="rId10" />
            ```
            
            The markup specifies the associated relationship part with relationship ID rId1 contains the corresponding relationship information for the parent XML element. end example]
            
            The possible values for this attribute are defined by the ST_RelationshipId simple type ([§22.8.2.1]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Rel) is located in §A.1. end note]

## 17.17.2 替代格式导入

**Alternative Format Import **

=== "中文"

    在生成WordprocessingML文档时，有时需要在文档中包含现有的文档内容（以下简称外部内容）。通常包含外部内容是因为它存储的格式不是ECMA-376定义的WordprocessingML格式。
    
    如[§11.3.1]所述，符合规范的生产者不得创建利用此机制的WordprocessingML包。
    
    为了在无需将外部内容转换为先决条件的情况下包含这些内容，WordprocessingML提供了一个功能，使应用程序能够实现任何格式的外部内容作为WordprocessingML文档的一部分进行导入。这个功能称为外部内容导入，允许在WordprocessingML包中包含任意内容类型的内容，当包被理解该内容类型的应用程序使用时，将其打开并合并到主文档中。
    
    [示例：考虑一个基于以下现有HTML内容创建的WordprocessingML文档：

    ```html
    <html … >
        <body style="margin-left:200px;margin-top:50px">
            <p>Paragraph one.</p>
            <blockquote style="border:5px solid #00FFFF">Paragraph in a
            blockquote.</blockquote>
            <p>Paragraph two.</p>
        </body>
    </html>
    ```
    
    此内容可以使用ECMA-376定义的XML语法转换为其WordprocessingML等价物，或者一个更基本的工具可以使用外部内容导入功能将HTML文档包含在WordprocessingML包中，从而允许该内容的后续使用者导入生成的HTML。
    
    当打开生成的WordprocessingML包时，必须读取HTML文档（如果这是一个被使用的应用程序理解的替代格式），并迁移到主WordprocessingML文档中的适当位置。示例结束]

=== "英文"

    When generating WordprocessingML documents, it is sometimes necessary to include existing document content (henceforth called external content) within the document. External content in a document is typically included because it was stored in a format other than the WordprocessingML format defined by ECMA-376.

    As described in [§11.3.1], conforming producers shall not create WordprocessingML packages which utilize this mechanism.
    
    In order to facilitate the inclusion of such content without requiring its conversion as a prerequisite to its inclusion in a document, WordprocessingML includes the facility for applications to implement the import of external content in any format as part of a WordprocessingML document. This functionality, called external content import, allows the inclusion of content of an arbitrary content type within the WordprocessingML package, which shall then be opened and merged into the main document when the package is consumed by applications which understand that content type.
    
    [Example: Consider a WordprocessingML document which is being created based on the following existing HTML content:
    
    ```html
    <html … >
        <body style="margin-left:200px;margin-top:50px">
            <p>Paragraph one.</p>
            <blockquote style="border:5px solid #00FFFF">Paragraph in a
            blockquote.</blockquote>
            <p>Paragraph two.</p>
        </body>
    </html>
    ```
    
    This content could be converted to its WordprocessingML equivalents using the XML syntax defined by ECMA- 376, or a more basic tool can use the external content import to include the HTML document within a WordprocessingML package, allowing a subsequent consumer of that content to import the resulting HTML.
    
    When the resulting WordprocessingML package is opened, the HTML document must be read (if it is an alternate format understood by the consuming application) and migrated into the appropriate location in the main WordprocessingML document. end example]

### 17.17.2.1 altChunk (导入外部内容的锚点)

**altChunk (Anchor for Imported External Content)**

=== "中文"
    
    此元素指定文档中的一个位置，用于插入包含外部内容的指定文件的内容，这些内容将被导入到主WordprocessingML文档中。指定文件的内容应出现在文档中的指定位置，从此之后可以作为常规WordprocessingML内容进行处理，而无需区分其来源。要导入的外部内容的位置应由其关系的Id属性与此元素的id属性匹配的关系来指定。
    
    如果此元素指定的关系的关系类型不是 http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk，或者不存在，或者没有TargetMode属性值为Internal，那么该文档应被视为不符合规范。如果应用程序无法处理由目标部分指定的内容类型的外部内容，则它应忽略指定的备用内容，但继续处理文件。如果可能，还应提供某种指示，说明未导入未知内容。
    
    [示例：考虑一个WordprocessingML文档，其内容必须从以下HTML文档中导入：
    
    ```HTML
    <html … >
        <body style="margin-left:200px;margin-top:50px">
            <p>第一段。</p>
            <blockquote style="border:5px solid #00FFFF">块引用中的段落。</blockquote>
            <p>第二段。</p>
        </body>
    </html>
    ```
    
    生成的WordprocessingML主文档将包含其自身的WordprocessingML内容以及在适当位置的外部内容导入锚：
    
    ```xml
    <w:body>
        <w:altChunk r:id="altChunk1" />
        <w:p/>
        <w:sectPr>
        …
        </w:sectPr>
    </w:body>
    ```
    
    altChunk元素指定由ID为altChunk1的关系目标的外部内容必须在文档开头导入。检查相应的关系部分项的内容，我们可以看到该关系的目标：
    
    ```xml
    <Relationships … >
        …
        <Relationship Id="altChunk1" TargetMode="Internal"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk" Target="import.htm"
            />
        …
    </Relationships>
    ```
    
    相应的关系部分项显示要导入的文件位于主文档旁边，名称为import.htm。结束示例]

    ??? abstract "Attributes"
        
        **id**（与部分的关系）
        
        :   命名空间：http://purl.oclc.org/ooxml/officeDocument/relationships
        
            指定包含备用内容以供导入的指定部分的关系ID。
            
            如果指定的关系与父元素要求的关系类型不匹配，则此文档应被视为不符合规范。
        
            [示例：考虑一个具有以下id属性的XML元素：
            
            ```xml
            <… r:id="rId10" />
            ```
            
            该标记指定了关联的关系部分，其关系ID为rId10，包含父XML元素的相应关系信息。结束示例]
            
            如果省略此属性，则应忽略父元素。
            
            此属性的可能值由ST_RelationshipId简单类型定义（[§22.8.2.1]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AltChunk) is located in §A.1. end note]

=== "英文"

    This element specifies a location within a document for the insertion of the contents of a specified file containing external content to be imported into the main WordprocessingML document. The specified file's contents should appear at the specified location within the document, and can henceforth be emitted as regular WordprocessingML without distinction to its origin. The location of the external content to be imported shall be specified by the relationship whose Id attribute matches the id attribute on this element.

    If the relationship type of the relationship specified by this element is not http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk, is not present, or does not have a TargetMode attribute value of Internal, then the document shall be considered non-conformant. If an application cannot process external content of the content type specified by the targeted part, then it should ignore the specified alternate content but continue to process the file. If possible, it should also provide some indication that unknown content was not imported.
    
    [Example: Consider a WordprocessingML document consisting of contents which must be imported from the following HTML document:

    ```HTML
    <html … >
        <body style="margin-left:200px;margin-top:50px">
            <p>Paragraph one.</p>
            <blockquote style="border:5px solid #00FFFF">Paragraph in a
            blockquote.</blockquote>
            <p>Paragraph two.</p>
        </body>
    </html>
    ```
    
    The resulting WordprocessingML host document would consist of its own WordprocessingML content as well as an external content import anchor in the appropriate location:

    ```xml
    <w:body>
        <w:altChunk r:id="altChunk1" />
        <w:p/>
        <w:sectPr>
        …
        </w:sectPr>
    </w:body>
    ```
    
    The altChunk element specifies that the external content targeted by the relationship with an ID of altChunk1 must be imported at the beginning of the document. Examining the contents of the corresponding relationship part item, we can see the targets for that relationship:

    ```xml
    <Relationships … >
        …
        <Relationship Id="altChunk1" TargetMode="Internal"
            Type="http://purl.oclc.org/ooxml/officeDocument/relationships/aFChunk" Target="import.htm"
            />
        …
    </Relationships>
    ```
    
    The corresponding relationship part item shows that the file to be imported is located next to the main document and is named import.htm. end example]

    ??? abstract "Attributes"

        **id** (Relationship to Part)

        :   Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships

            Specifies the relationship ID to a specified part containing alternate content for import.
            
            If the specified relationship does not match the relationship type required by the parent element, then this document shall be considered to be non-conformant.

            [Example: Consider an XML element which has the following id attribute:
            
            ```xml
            <… r:id="rId10" />
            ```
            
            The markup specifies the associated relationship part with relationship ID rId1 contains the corresponding relationship information for the parent XML element. end example]
            
            If this attribute is omitted, the parent element shall be ignored.
            
            The possible values for this attribute are defined by the ST_RelationshipId simple type ([§22.8.2.1]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AltChunk) is located in §A.1. end note]


### 17.17.2.2 altChunkPr (外部内容导入属性)

**altChunkPr (External Content Import Properties)**

=== "中文"
    
    此元素指定要应用于父altChunk元素指定的外部内容导入的一组属性。在ECMA-376标准中，仅指定了一项属性。
    
    [示例：考虑一个包含在适当位置具有外部内容导入锚点的WordprocessingML文档：
    
    ```xml
    <w:body>
        <w:altChunk r:id="altChunk1">
            <w:altChunkPr>
                <w:matchSrc w:val="false" />
            </w:altChunkPr>
        </w:altChunk>
        <w:p/>
        <w:sectPr>
            …
        </w:sectPr>
    </w:body>
    ```
    
    altChunkPr 元素指定在导入指定内容时应用于外部内容导入的一组属性。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AltChunkPr) is located in §A.1. end note]

=== "英文"

    This element specifies the set of properties which shall be applied to the import of the external content specified by the parent altChunk element. Within ECMA-376, only one property is specified.
    
    [Example: Consider a WordprocessingML document consisting of contents which contains an external content import anchor in the appropriate location:

    ```xml
    <w:body>
        <w:altChunk r:id="altChunk1">
            <w:altChunkPr>
                <w:matchSrc w:val="false" />
            </w:altChunkPr>
        </w:altChunk>
        <w:p/>
        <w:sectPr>
            …
        </w:sectPr>
    </w:body>
    ```
    
    The altChunkPr element specifies the set of properties applied to the external content import when importing the specified content. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_AltChunkPr) is located in §A.1. end note]
    

### 17.17.2.3 matchSrc (导入时保持源格式)

**matchSrc (Keep Source Formatting on Import)**

=== "中文"
    
    此元素指定导入内容中存在的任何样式定义是否应被主WordprocessingML文档中存在的相同样式覆盖。如果此元素的val属性为true，则在导入内容和主文档中同时存在的任何样式应通过重新定义样式名称和/或ID以保持在导入内容上的样式。相反，如果此元素的val属性为false，则在导入内容和主文档中同时存在的任何样式应应用主文档中的样式来替换导入内容中的样式。
    
    如果省略此元素，则主文档中的样式应覆盖导入内容中的相同样式。
    
    [示例：考虑一个包含在适当位置具有外部内容导入锚点的WordprocessingML文档：
    
    ```xml
    <w:body>
        <w:altChunk r:id="altChunk1">
            <w:altChunkPr>
                <w:matchSrc w:val="true" />
            </w:altChunkPr>
        </w:altChunk>
        <w:p/>
        <w:sectPr>
            …
        </w:sectPr>
    </w:body>
    ```
    
    matchSrc元素的val属性值为true，这指定了在导入指定内容时必须保留冲突的样式。例如，如果在两个地方都定义了“标题 1”样式，则应用程序必须确保生成的文档不会丢失任何实例的格式。结束示例]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"

    This element specifies if any style definitions present in the imported content shall be overridden by identical styles present in the host WordprocessingML document. If this element's val attribute is true, then any style exists in both the imported content and main document shall be maintained on the imported content by redefining the style name and/or ID as needed. Conversely, if this element's val attribute is false, any style which exists in both the imported content and main document shall apply the style form the main document in place of the style in the imported content.

    If this element is omitted, then styles from the main document shall override identical styles from the imported content.
    
    [Example: Consider a WordprocessingML document consisting of contents which contains an external content
    import anchor in the appropriate location:
    
    ```xml
    <w:body>
    <w:altChunk r:id="altChunk1">
    <w:altChunkPr>
    <w:matchSrc w:val="true" />
    </w:altChunkPr>
    </w:altChunk>
    <w:p/>
    <w:sectPr>
    …
    </w:sectPr>
    </w:body>
    
    The matchSrc element has a val attribute value of true, which specifies that conflicting styles must be maintained when importing the specified content. For example, if the Heading 1 style was defined in both places, then applications must ensure that the resulting document does not lose either instance of its formatting as appropriate. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].


## 17.17.3 往返替代内容

**Roundtripping Alternate Content**

=== "中文"

    WordprocessingML未定义一组位置，应用程序应在这些位置尽可能尝试存储和往返所有在备用内容块中未选择的选项。因此，这种行为由应用程序定义。有关备用内容块的进一步讨论，请参见[§L.1.18.4]。

=== "英文"

    WordprocessingML does not define a set of locations where applications should, whenever possible, attempt to store and roundtrip all non-taken choices in alternate content blocks. This behavior is therefore application-defined. For further discussion of alternate content blocks see [§L.1.18.4].

## 17.17.4 布尔属性 (CT_OnOff)

**Boolean Property (CT_OnOff)**

=== "中文"

    此通用复杂类型指定了在整个 WordprocessingML 中使用的布尔属性。
    
    ??? abstract "属性"
    
        **val**（开/关值）
        
        :   指定由父 XML 元素定义的属性的二进制值。
        
            值为 1 或 true 表示该属性应被明确应用。这是此属性的默认值，并在父元素存在但未指定此属性时被隐含应用。
        
            值为 0 或 false 表示该属性应被明确关闭。
        
            [示例：例如，考虑以下开/关属性：
        
            ```xml
            <… w:val="false"/>
            ```
        
            val 属性明确声明该属性为 false。end example]
        
            此属性的可能值由 ST_OnOff 简单类型定义（[§22.9.2.7]）。
    
    [Note: The W3C XML Schema definition of this complex type’s content model (CT_OnOff) is located in §A.1. end note]

=== "英文"

    This common complex type specifies a boolean attribute used throughout WordprocessingML.

    ??? abstract "Attributes"

        **val** (On/Off Value)

        :   Specifies a binary value for the property defined by the parent XML element.

            A value of 1 or true specifies that the property shall be explicitly applied. This is the default value for this attribute, and is implied when the parent element is present, but this attribute is omitted.
            
            A value of 0 or false specifies that the property shall be explicitly turned off.
            
            [Example: For example, consider the following on/off property:
            
            ```xml
            <… w:val="false"/>
            ```
            
            The val attribute explicitly declares that the property is false. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
    [Note: The W3C XML Schema definition of this complex type’s content model (CT_OnOff) is located in §A.1. end note]

[§17.17.1]: #17171-子文档
[§17.17.1.1]: #171711-subdoc-子文档位置的锚点
[§17.17.2]: #17172-替代格式导入
[§17.17.2.1]: #171721-altchunk-导入外部内容的锚点
[§17.17.2.2]: #171722-altchunkpr-外部内容导入属性
[§17.17.2.3]: #171723-matchsrc-导入时保持源格式
[§17.17.3]: #17173-往返替代内
[§17.17.4]: #17174-布尔属性-ct_onoff

[§11.3.1]: ../chapter-11.md#1131-替代格式导入部件

[§17.17.4]: ./17miscellaneous.md#17174-布尔属性-ct_onoff

[§22.8.2.1]: ../chapter22/officedocumentrelationships.md#22821-st_relationshipid-显式关系-id

[§22.9.2.7]: ../chapter22/sharedsimpletypes.md#22927-st_onoff-开关值