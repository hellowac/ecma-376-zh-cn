# 17.12 术语表文档

**Glossary Document**

=== "中文"
    
    一个WordprocessingML文件内，术语表文档是用于附加文档内容的补充存储位置，该内容将随文档一起传送，但在被特意添加到文档之前不会作为主要文档的一部分进行打印显示。
    
    术语表文档也将有一个单独的所有关系的实例，这些关系是在主文档部分提供的，意味着术语表文档将在WordprocessingML文档内拥有自己的样式定义、编号定义、注释、页眉、页脚等。
    
    【例如：考虑一个必须包括十个可选术语的文档，这些术语可以通过用户界面插入。很明显，在它们被明确插入之前不希望这十个术语出现在主文档内容中，因此它们每个都可以存储在术语表文档中，并在需要时通过用户界面插入。结束示例】
    
    在术语表文档中，文档内容的每个不同区域被称为术语表文档条目，并通过docPart元素（[§17.12.5]）进行定义。这些文档部分可以包含任何块级WordprocessingML元素，并且还可以通过术语表文档条目的属性应用一组分类和行为。
    
    【例如：考虑WordprocessingML文档中术语表文档部分内容的以下定义：
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                <w:docPartPr>
                    …
                </w:docPartPr>
                <w:docPartBody>
                    <w:p>
                        <w:r>
                            <w:t>样本条目。</w:t>
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
    
    术语表文档元素（[§17.12.10]）定义了术语表文档部分的内容。在术语表文档中，每个docPart元素包含一个术语表文档条目的定义：在这种情况下，术语表文档中有两个条目，第一个包含一个段落，其中只包含一个文本运行。结束示例】

=== "英文"
    
    Within a WordprocessingML file, the glossary document is a supplemental storage location for additional document content which shall travel with the document, but which shall not be displayed for printed as part of the main document until it is explicitly added to that document by deliberate action.
    
    The glossary document shall also be afforded a separate instance of all of the relationships which are provided on the main document part - this means that the glossary document shall have its own style definitions, numbering definitions, comments, headers, footers, etc. within the WordprocessingML document.
    
    [Example: Consider a document which must include ten optional clauses that can be inserted through a user interface. It is clearly not desirable to have these ten clauses appear in the main document story's contents before they are explicitly inserted, therefore each of them can be stored in the glossary document and inserted via the user interface as needed. end example]
    
    Within the glossary document, each distinct region of document content is referred to as a glossary document entry, and is defined via the docPart element ([§17.12.5]). These document parts can contain any block-level WordprocessingML element, and can also have a set of classifications and behaviors applied to them via the glossary document entry's properties.
    
    [Example: Consider the following definition for the contents of a glossary document part within a WordprocessingML document:
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                <w:docPartPr>
                    …
                </w:docPartPr>
                <w:docPartBody>
                    <w:p>
                        <w:r>
                            <w:t>Sample entry.</w:t>
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
    
    The glossaryDocument element ([§17.12.10]) defines the contents of the glossary document part. Within the glossary document, each docPart element contains the definition for one glossary document entry: in this case, there are two entries in the glossary document, the first of which contains a single paragraph with a single run of text. end example]

## 17.12.1 behavior (单个条目插入行为)

**behavior (Entry Insertion Behavior) **

=== "中文"

    此元素指定了当父词汇文档条目（[§17.12.5]）的内容被添加到WordprocessingML文档的主文档故事中时应应用的单个行为。这些行为应用于格式化插入周围的WordprocessingML，而不需要用户界面（即使是没有用户界面的应用程序也应使用这些设置）。
    
    [示例：考虑包含单个运行的词汇文档条目的WordprocessingML片段，定义如下：
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p"/>
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    behavior元素的值为p，这指定了当父词汇文档条目的内容被添加到文档的内容中时，必须将其插入到单独的段落中。如果要添加到的文档内容定义如下（并且该部分被添加在两个文本运行之间）：
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    此设置指定，尽管该部分通常会插入在段落中两个现有的运行之间，但该行为必须确保该部分被插入到其自己的段落中，结果为以下WordprocessingML：
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Sample entry.</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    结束示例]
    
    ??? abstract "Attributes"
    
        **val**（插入行为值）
        
        :   指定与当前词汇文档条目相关联的插入行为。
        
            [示例：考虑词汇文档条目属性的WordprocessingML片段，定义如下：
            
            ```xml
            <w:docPartPr>
                <w:behaviors>
                    <w:behavior w:val="content"/>
                </w:behaviors>
            </w:docPartPr>
            ```
            
            val属性值为content，这指定插入此词汇文档条目时必须仅包括内容（部分中的最后一个段落必须合并到文档中的当前段落中）。结束示例]
            
            此属性的可能值由ST_DocPartBehavior简单类型定义（[§17.18.15]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartBehavior) is located in §A.1. end note]

=== "英文"

    This element specifies a single behavior which shall be applied to the contents of the parent glossary document entry ([§17.12.5]) when it is added to the main document story of a WordprocessingML document. These behaviors shall be used to format the surrounding WordprocessingML around insertion, and do not require the presence of a user interface (i.e. applications without a user interface shall also utilize these settings).
    
    [Example: Consider the WordprocessingML fragment for a glossary document entry containing a single run,
    defined as follows:
    
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p"/>
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    
    
    The behavior element has a value of p, which specifies that the contents of the parent glossary document entry must be inserted in their own paragraph when they are added to the contents of a document. If the document content to which they are added is defined as follows (and the part is added between the two text runs):
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    This setting specifies that although the part would normally be inserted between the two existing runs in the paragraph, that behavior must ensure that the part is inserted into its own paragraph, resulting in the following WordprocessingML:
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Sample entry.</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    end example]
    
    ??? abstract "Attributes"
    
        **val** (Insertion Behavior Value)
    
        :   Specifies the insertion behavior which shall be associated with the current glossary document entry.
    
            [Example: Consider the WordprocessingML fragment for a glossary document entry's properties, defined as follows:
            
            ```xml
            <w:docPartPr>
                <w:behaviors>
                    <w:behavior w:val="content"/>
                </w:behaviors>
            </w:docPartPr>
            ```
            
            The val attribute value of content specifies that the insertion of this glossary document entry must include only the content (the last paragraph in the part must be merged into the current paragraph in the document). end example]
            
            The possible values for this attribute are defined by the ST_DocPartBehavior simple type ([§17.18.15]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartBehavior) is located in §A.1. end note]

## 17.12.2 behaviors (条目插入行为集合)

**behaviors (Entry Insertion Behaviors)**

=== "中文"
    
    该元素指定了当父级词汇文档条目（[§17.12.5]）被添加到WordprocessingML文档的主要内容部分时，应应用于其内容的一组行为。
    
    由于单个部分可以指定多个行为，因此插入父级条目到WordprocessingML文档内容时，将使用所有行为的总和。
    
    [示例：考虑包含单个运行的词汇文档条目的WordprocessingML片段，定义如下：
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p" />
                <w:behavior w:val="pg" />
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    behaviors元素包含一组在将此条目插入文档时必须应用的行为，在这种情况下：
    
    - 条目必须插入到文档中的独立段落中
    - 条目必须插入到文档的新页面上（即它必须前面有一个分页符）
    
    结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartBehaviors) is located in §A.1. end note]

=== "英文"
    
    This element specifies the set of behaviors which shall be applied to the contents of the parent glossary document entry ([§17.12.5]) when it is added to the main document story of a WordprocessingML document.
    
    Since multiple behaviors can be specified for a single part, the sum total of all behaviors shall be used to insert the parent entry into the contents of the WordprocessingML document.
    
    [Example: Consider the WordprocessingML fragment for a glossary document entry containing a single run, defined as follows:
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p" />
                <w:behavior w:val="pg" />
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    The behaviors element contains the set of behaviors which must be applied to this entry when it is inserted into the document, in this case:
    
    - The entry must be inserted into its own paragraph in the document
    - The entry must be inserted onto a new page in the document (i.e. it must be preceded by a page break)
    
    end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartBehaviors) is located in §A.1. end note]

## 17.12.3 category (条目分类)

**category (Entry Categorization)**

=== "中文"
    
    该元素指定了父级词汇文档条目的分类。此分类不暗示任何与条目相关的行为，仅用于在应用程序或用户界面中组织词汇文档条目集合（例如，用于区分具有相同条目名称的两个条目（[§17.12.13]））。
    
    [示例：考虑以下单个词汇文档条目属性的WordprocessingML片段：
    
    ```xml
    <w:docPartPr>
        <w:category>
            …
        </w:category>
        …
    </w:docPartPr>
    ```
    
    category元素指定应用于当前条目的分类，用于分类或用户界面排序等目的。结束示例]
    
    [注：此元素内容模型（CT_DocPartCategory）的W3C XML Schema定义位于§A.1。结束注释]

=== "英文"
    
    This element specifies the categorization for the parent glossary document entry. This categorization shall not imply any behaviors around the entry, and is only used to organize the set of glossary document entries within an application or user interface (i.e. to disambiguate between two entries with the same entry name ([§17.12.13])).
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        <w:category>
            …
        </w:category>
        …
    </w:docPartPr>
    ```
    
    The category element specifies the categorization applied to the current entry, for the purposes of classification or user interface  orting, for example. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartCategory) is located in §A.1. end note]

## 17.12.4 description (条目描述)

**description (Description for Entry)**

=== "中文"
    
    该元素为此词汇文档条目的内容指定了一个描述。此描述可以包含任何字符串内容，并允许在词汇文档条目的定义中包含附加信息。[注意：例如，此描述可以在用户界面中显示。结束注释]
    
    [示例：考虑以下单个词汇文档条目属性的WordprocessingML片段：
    
    ```xml
    <w:docPartPr>
        …
        <w:name w:val="Sample Entry" />
        <w:description w:val="This is an example of a glossary document entry for example purposes." />
        …
    </w:docPartPr>
    ```
    
    description元素指定与父条目相关的详细描述必须是This is an example of a glossary document entry for example purposes。此值可以根据需要由应用程序使用，例如，在用户界面中显示。结束示例]
    
    ??? abstract "Attributes"
    
        **val** (字符串值)
        
        :   指定其内容包含一个字符串。
        
            该字符串的内容根据父XML元素的上下文进行解释。
            
            [示例：考虑以下WordprocessingML片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val属性的值是关联段落样式的styleId。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val属性中的字符串是最近的祖先结构化文档标签的标题。在每种情况下，该值都在父元素的上下文中解释。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies a description for the contents of this glossary document entry. This description can contain any string content, and allows the entry to have additional information contained within the definition for this glossary document entry. [Note: This description can be surfaced in a user interface, for example. end note]
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        …
        <w:name w:val="Sample Entry" />
        <w:description w:val="This is an example of a glossary document entry for
        example purposes." />
        …
    </w:docPartPr>
    ```
    
    The description element specifies that the long description associated with the parent entry must be This is an example of a glossary document entry for example purposes. This value can be used as needed by an application, for example, to display in a user interface. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
            
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

## 17.12.5 docPart (术语文档条目)

**docPart (Glossary Document Entry)**

=== "中文"
    
    该元素指定文档中包含的单个词汇文档条目的详细信息。此词汇文档条目可以包含以下一项或两项内容：
    
    - 词汇文档条目的属性，定义其名称、分类和行为
    - 词汇文档条目的内容，包括一个或多个块级元素的WordprocessingML内容
    
    这两个组件中的每一个都由此元素的子元素指定，如下表中的子元素所示。
    
    [示例：考虑以下在WordprocessingML文档中的词汇文档部分的内容定义：
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    docPart元素唯一地定义了词汇文档部分中的一个词汇文档条目，因此在当前词汇文档部分示例中存储了两个唯一条目。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPart) is located in §A.1. end note]

=== "英文"
    
    This element specifies the details for a single glossary document entry contained in the document. This glossary document entry can consist of one or both of the following:
    
    - The glossary document entry's properties, which define its name, categorization, and behaviors
    - The glossary document entry's contents, which consists of one or more block-level elements of WordprocessingML content
    
    Each of these two components is specified by one of the child elements of this element, as seen in the child elements table below.
    
    [Example: Consider the following definition for the contents of a Glossary Document part within a WordprocessingML document:
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    The docPart element uniquely defines one glossary document entry within the glossary document part, therefore there are two unique entries stored in the current example of a glossary document part. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPart) is located in §A.1. end note]



## 17.12.6 docPartBody (术语文档条目内容)

**docPartBody (Contents of Glossary Document Entry)**

=== "中文"
    
    该元素指定父词汇文档条目（[§17.12.5]）的内容。这些内容应包含一个或多个块级元素，类似于当前文档的主文档故事的body元素（[§17.2.2]）。
    
    [示例：考虑包含单个运行的词汇文档条目的WordprocessingML片段，定义如下：
    
    ```xml
    <w:docPart>
        …
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    docPartBody元素指定了组成当前词汇文档条目内容的块级元素，在这种情况下，使用p元素（[§17.3.1.22]）创建了一个单独的段落。结束示例]
    
    当词汇文档条目的内容被添加到文档中时，样式、编号定义和所有其他相关部分将从词汇文档部分的关系中获取，而不是从主文档部分获取。当条目被添加到文档中时，这些引用将移动到它们在主文档中的对应项。
    
    当部分被插入时，应当插入得就像其最后的段落标记不存在一样（最后段落标记的内容将与此条目正在添加到的段落的内容合并）。
    
    [示例：考虑包含单个运行的词汇文档条目的WordprocessingML片段，定义如下：
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p"/>
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    如果将此条目插入到以下内容的文档中（部分添加在两个文本运行之间）：
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    此条目仅有一个段落，在插入之前将被移除，并且除非有特殊的插入行为（[§17.12.2]），否则只会插入文本运行，导致以下WordprocessingML：
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Sample entry.</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Body) is located in §A.1. end note]

=== "英文"
    
    This element specifies the contents of the parent glossary document entry ([§17.12.5]). These contents shall consist of one or more block-level elements, analogous to the body element ([§17.2.2]) of the main document story for the current document.
    
    [Example: Consider the WordprocessingML fragment for a glossary document entry containing a single run, defined as follows:
    
    ```xml
    <w:docPart>
        …
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    The docPartBody element specifies the block-level elements which comprise the contents of the current glossary document entry, in this case, a single paragraph using the p element ([§17.3.1.22]). end example]
    
    When the contents of a glossary document entry are added to a document, the styles, numbering definitions, and all other related parts for this entry shall be taken from the relationships from the Glossary Document part and not from the main document part. These references shall be moved to their main document equivalents when the entry is added to the document.
    
    When the part is inserted, it shall be inserted as though its last paragraph mark does not exist (the content of the final paragraph mark shall be merged with the contents of the paragraph into which this entry is being added).
    
    [Example: Consider the WordprocessingML fragment for a glossary document entry containing a single run, defined as follows:
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:behaviors>
                <w:behavior w:val="p"/>
            </w:behaviors>
            …
        </w:docPartPr>
        <w:docPartBody>
            <w:p>
                <w:r>
                    <w:t>Sample entry.</w:t>
                </w:r>
            </w:p>
        </w:docPartBody>
    </w:docPart>
    ```
    
    If this entry is inserted into document content to which is defined as follows (and the part is added between the two text runs):
    
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    This entry has only a single paragraph, which is removed before insertion, and barring any special insertion behaviors ([§17.12.2]), only the text run is inserted, resulting in the following WordprocessingML:
    
    ```xml
    <w:body>
        <w:p>
            <w:r>
                <w:t>After this text</w:t>
            </w:r>
            <w:r>
                <w:t>Sample entry.</w:t>
            </w:r>
            <w:r>
                <w:t>Before this text</w:t>
            </w:r>
        </w:p>
    </w:body>
    ```
    
    end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Body) is located in §A.1. end note]



## 17.12.7 docPartPr (术语文档条目属性)

**docPartPr (Glossary Document Entry Properties)**

=== "中文"
    
    该元素指定应用于父词汇文档条目的一组属性。这些属性定义了其名称、分类和行为。
    
    [示例：考虑包含单个运行的词汇文档条目的WordprocessingML片段，定义如下：
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:name w:val="Sample Entry" />
            …
        </w:docPartPr>
        …
    </w:docPart>
    ```
    
    docPartPr元素指定了已为父词汇文档条目指定的一组属性，上面唯一可见的是名称为"Sample Entry"的条目名称。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartPr) is located in §A.1. end note]

=== "英文"
    
    This element specifies the set of properties which shall be applied to the parent glossary document entry. These properties define its name, categorization, and behaviors.
    
    [Example: Consider the WordprocessingML fragment for a glossary document entry containing a single run, defined as follows:
    
    ```xml
    <w:docPart>
        <w:docPartPr>
            <w:name w:val="Sample Entry" />
            …
        </w:docPartPr>
        …
    </w:docPart>
    ```
    
    The docPartPr element specifies the set of properties which have been specified for the parent glossary document entry, the only one visible above being the entry's name of Sample Entry. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartPr) is located in §A.1. end note]

## 17.12.8 docParts (术语文档条目列表)

**docParts (List of Glossary Document Entries)**

=== "中文"
    
    该元素指定存储在当前词汇文档部分中的词汇文档条目集合。
    
    [示例：考虑WordprocessingML文档中词汇文档部分内容的以下定义：
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    docParts元素定义了存储在词汇文档部分中的条目集合。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocParts) is located in §A.1. end note]

=== "英文"
    
    This element specifies the collection of glossary document entries which are stored in the current Glossary Document part.
    
    [Example: Consider the following definition for the contents of a glossary document part within a WordprocessingML document:
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    The docParts element defines the set of entries which are stored in the glossary document part. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocParts) is located in §A.1. end note]



## 17.12.9 gallery (图库关联的条目)

**gallery (Gallery Associated With Entry)**

=== "中文"
    
    该元素指定当前词汇文档部分应归类到的预定义画廊。尽管其枚举值可以被解释为暗示父词汇文档条目内容的语义，但仅用于对该条目进行分类和排序（通过应用程序或用户界面）。
    
    [示例：考虑单个词汇文档条目属性的以下WordprocessingML片段：
    
    ```xml
    <w:docPartPr>
        <w:category>
            <w:name w:val="Internal Memo Covers" />
            <w:gallery w:val="coverPg" />
        </w:category>
        …
    </w:docPartPr>
    ```
    
    值为 coverPg 的 gallery 元素指定了应用于当前条目的画廊分类，用于分类或用户界面排序，将此条目放入封面页面分类。结束示例]
    
    
    ??? abstract "Attributes"
    
        **val**（画廊值）
    
        :   指定应与父词汇文档条目关联的画廊分类。
    
            [示例：考虑单个词汇文档条目的以下WordprocessingML片段：
            
            ```xml
            <w:gallery w:val="custom1" />
            ```
            
            值为 custom1 的 val 属性指定当前条目应用的画廊分类为自定义 1。结束示例]
            
            The possible values for this attribute are defined by the ST_DocPartGallery simple type ([§17.18.16]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartGallery) is located in §A.1. end note]

=== "英文"
    
    This element specifies the predefined gallery into which the current glossary document part shall be classified. This classification, although its enumeration values can be interpreted to imply semantics around the contents of the parent glossary document entry, shall only be used to classify and sort this entry (via an application or a user interface).
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document
    entry:
    
    ```xml
    <w:docPartPr>
        <w:category>
            <w:name w:val="Internal Memo Covers" />
            <w:gallery w:val="coverPg" />
        </w:category>
        …
    </w:docPartPr>
    ```
    
    The gallery element with a value of coverPg specifies that the gallery categorization applied to the current entry, for the purposes of classification or user interface sorting, puts this entry into the Cover Pages classification. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Gallery Value)
    
        :   Specifies the classification of gallery which shall be associated with the parent glossary document entry.
    
            [Example: Consider the following WordprocessingML fragment for a single glossary document entry:
            
            ```xml
            <w:gallery w:val="custom1" />
            ```
            
            The val attribute with a value of custom1 specifies that the gallery categorization applied to the current entry is the Custom 1 classification. end example]
            
            The possible values for this attribute are defined by the ST_DocPartGallery simple type ([§17.18.16]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartGallery) is located in §A.1. end note]


## 17.12.10 glossaryDocument (术语文档根元素)

**glossaryDocument (Glossary Document Root Element)**

=== "中文"
    
    该元素指定了 WordprocessingML 文档中词汇文档部分的根元素。词汇文档是 WordprocessingML 中的一个附加文档段落，应具有主文档部分的所有关系，例如：
    
    - 样式定义
    - 编号定义
    - 注释
    - 页眉/页脚
    - 等等
    
    存储在此部分中的条目应该将其所有隐式关系指向这些部分，而不是指向主文档部分之外的类似部分。
    
    [示例：考虑 WordprocessingML 文档中词汇文档部分的内容定义如下：
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    glossaryDocument 元素定义了词汇文档部分的内容。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_GlossaryDocument) is located in §A.1. end note]

=== "英文"
    
    This element specifies the root element for a glossary document part within a WordprocessingML document. A glossary document is an supplementary document story in a WordprocessingML that shall be afforded all of the relationships of the Main Document part, such as:
    
    - Style definitions
    - Numbering definitions
    - Comments
    - Headers/footers
    - Etc.
    
    The entries stored in this part shall have all of its implicit relationships target these parts, rather than their analogues stored off of the main document part.
    
    [Example: Consider the following definition for the contents of a glossary document part within a WordprocessingML document:
    
    ```xml
    <w:glossaryDocument>
        <w:docParts>
            <w:docPart>
                …
            </w:docPart>
            <w:docPart>
                …
            </w:docPart>
        </w:docParts>
    </w:glossaryDocument>
    ```
    
    The glossaryDocument element defines the contents of the glossary document part. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_GlossaryDocument) is located in §A.1. end note]
 
## 17.12.11 guid (条目ID)

**guid (Entry ID)**

=== "中文"
    
    该元素指定一个唯一标识符（使用 val 属性上存储的 128 位 GUID 指定），该标识符唯一标识此文档构建块。[注意：此唯一标识符可由应用程序使用，无论不同的命名如何，都可以唯一引用单个文档构建块，例如，当相同部分具有不同的本地化名称时。结束注意]
    
    [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
    
    ```xml
    <w:docPartPr>
        …
        <w:guid w:val="{00000000-5BD2-4BC8-9F70-7020E1357FB2}" />
        …
    </w:docPartPr>
    ```
    
    guid 元素指定与父条目关联的唯一标识符必须是 {00000000-5BD2-4BC8-9F70-7020E1357FB2}。此值可根据需要由应用程序使用，例如，无论名称如何，都可以唯一标识部分。结束示例]
    
    ??? abstract "Attributes"
    
        **val**（GUID 值）
    
        :   指定一个由下面引用的简单类型定义的 128 位全局唯一标识符（GUID）值。此 GUID 的内容应基于父 XML 元素的上下文进行解释。
    
            如果省略了此属性，则假定其值为空（即，不应将 GUID 与父 XML 元素关联起来）。
            
            [示例：考虑以下 WordprocessingML 元素：
            
            ```xml
            <… w:val="{6A9B8B6F-5BD2-4BC8-9F70-7020E1357FB2}"/>
            ```
            
            {6A9B8B6F-5BD2-4BC8-9F70-7020E1357FB2} 的 val 属性值必须与父 XML 元素的上下文关联。结束示例]
            
            The possible values for this attribute are defined by the ST_Guid simple type ([§22.9.2.4]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Guid) is located in §A.1. end note]

=== "英文"
    
    This element specifies a unique identifier (specified using a 128-bit GUID stored on the val attribute) that uniquely identifies this document building block.[Note: This unique identifier can be used by an application to uniquely reference a single document building block regardless of different naming, for example when the same part has different names for localization purposes. end note]
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        …
        <w:guid w:val="{00000000-5BD2-4BC8-9F70-7020E1357FB2}" />
        …
    </w:docPartPr>
    ```
    
    The guid element specifies that the unique identifier associated with the parent entry must be {00000000-5BD2-4BC8-9F70-7020E1357FB2}. This value can be used as needed by an application, for example, to uniquely identify a part regardless of its name. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (GUID Value)
    
        :   Specifies a 128-bit globally unique identifier (GUID) value as defined by the simple type referenced below. The contents of this GUID shall be interpreted based on the context of the parent XML element.
    
            If this attribute is omitted, its value shall be assumed to be null (i.e. no GUID shall be associated with the parent XML element).
            
            [Example: Consider the following WordprocessingML element:
            
            ```xml
            <… w:val="{6A9B8B6F-5BD2-4BC8-9F70-7020E1357FB2}"/>
            ```
            
            The val attribute value of {6A9B8B6F-5BD2-4BC8-9F70-7020E1357FB2} must be associated with the context of the parent XML element. end example]
            
            The possible values for this attribute are defined by the ST_Guid simple type ([§22.9.2.4]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Guid) is located in §A.1. end note]

## 17.12.12 name (分类关联的条目)

**name (Category Associated With Entry)**

=== "中文"
    
    该元素指定当前词汇文档部分应归类为的类别。该分类可以由其内容确定的任何字符串值组成，并且只能用于对该条目进行分类和排序（通过应用程序或用户界面）。
    
    [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
    
    ```xml
    <w:docPartPr>
        <w:category>
            <w:name w:val="Internal Memo Covers" />
            <w:gallery w:val="coverPg" />
        </w:category>
        …
    </w:docPartPr>
    ```
    
    值为 Internal Memo Covers 的 name 元素指定了应用于当前条目的分类分组，用于分类或用户界面排序，将此条目放入内部备忘录封面分类中。此类别可根据需要使用。结束示例]
    
    ??? abstract "Attributes"
    
        **val**（字符串值）
    
        :   指定其内容包含字符串。
    
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```        
            
            val 属性的值是相关段落样式的 styleId。
            
            但是，请考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近的祖先结构化文档标记的标题。在每种情况下，值都是根据父元素的上下文进行解释的。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the category into which the current glossary document part shall be classified. This classification can consist of any string value as determined by its contents, and shall only be used to classify and sort this entry (via an application or a user interface).
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        <w:category>
            <w:name w:val="Internal Memo Covers" />
            <w:gallery w:val="coverPg" />
        </w:category>
        …
    </w:docPartPr>
    ```
    
    The name element with a value of Internal Memo Covers specifies that the category grouping applied to the current entry, for the purposes of classification or user interface sorting, puts this entry into the Internal Memo Covers classification. This category can be used as desired. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (String Value)
    
        :   Specifies that its contents contain a string.
    
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```        
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
            
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

## 17.12.13 name (条目名称)

**name (Entry Name)**

=== "中文"
    
    该元素指定了该词汇文档条目的内容的名称。该名称可以包含任何字符串内容，并允许在此词汇文档条目的定义中包含友好的标识符。【注意：此名称可以在用户界面中显示，例如。】。
    
    [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
    
    ```xml
    <w:docPartPr>
        …
        <w:name w:val="Sample Entry" />
        <w:description w:val="This is an example of a glossary document entry for
            example purposes." />
        …
    </w:docPartPr>
    ```
    
    name 元素指定了与父条目关联的友好名称必须为 Sample Entry。
    
    这个值可以根据需要由应用程序使用，例如，在用户界面中显示。结束示例】
    
    ??? abstract "Attributes"
    
        **decorated**（内置条目）
    
        :   指定当前条目的名称是一个内置条目，不应在用户界面中显示。【注意：此信息可以根据需要由应用程序使用，例如，用于将条目与具有相同名称的条目区分开，确保应用程序可以唯一地识别内置条目。】
    
            如果省略此属性，则其值应假定为 false。
    
            [示例：考虑以下单个词汇文档条目名称的 WordprocessingML 片段：
            
            ```xml
            <w:name w:decorated="true" w:val=":-)" />
            ```
            
            decorated 属性指定父条目是一个内置条目，并且必须作为内置条目处理。结束示例]
            
            此属性的可能值由 ST_OnOff 简单类型（[§22.9.2.7]）定义。
    
        **val**（名称值）
    
        :   指定包含当前词汇文档条目名称的字符串值。
            
            [示例：考虑以下单个词汇文档条目名称的 WordprocessingML 片段：
            
            ```xml
            <w:name w:val="Sample Entry" />
            ```
            
            val 属性指定父条目的名称为 Sample Entry。结束示例]
    
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartName) is located in §A.1. end note]

=== "英文"
    
    This element specifies a name for the contents of this glossary document entry. This name can contain any string content, and allows the entry to have a friendly identifier contained within the definition for this glossary document entry. [Note: This name can be surfaced in a user interface, for example. end note]
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        …
        <w:name w:val="Sample Entry" />
        <w:description w:val="This is an example of a glossary document entry for
            example purposes." />
        …
    </w:docPartPr>
    ```
    
    The name element specifies that the friendly name associated with the parent entry must be Sample Entry.
    
    This value can be used as needed by an application, for example, to display in a user interface. end example]
    
    
    ??? abstract "Attributes"
    
        **decorated** (Built-In Entry)
    
        :   Specifies that the name for the current entry is a built-in entry which should not be displayed in the user interface. [Note: This information can be used by an application as needed, for example, to disambiguate an entry from one with the same name, ensuring that the built-in entry can be uniquely identified by the application. end note]
            
            If this attribute is omitted, its value shall be assumed to be false.
            
            [Example: Consider the following WordprocessingML fragment for the name of a single glossary document entry:
            
            ```xml
            <w:name w:decorated="true" w:val=":-)" />
            ```
            
            The decorated attribute specifies that the parent entry is a built-in entry, and must be treated as such. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
        **val** (Name Value)
    
        :   Specifies a string value which contains the name of the current glossary document entry.
            
            [Example: Consider the following WordprocessingML fragment for the name of a single glossary document entry:
            
            ```xml
            <w:name w:val="Sample Entry" />
            ```
            
            The val attribute specifies that the name of the parent entry is Sample Entry. end example]
    
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartName) is located in §A.1. end note]

## 17.12.14 style (关联段落样式名称)

**style (Associated Paragraph Style Name)**

=== "中文"
    
    该元素指定与当前词汇文档条目关联的段落样式的样式 ID。此段落样式关联不应暗示关于词汇文档条目的格式或内容的任何信息，只应用于过滤和/或排序此条目（通过应用程序或用户界面）。【注意：此元素提供的分类级别的一个示例是仅在段落格式与指定样式匹配时显示其为可用。】
    
    [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
    
    ```xml
    <w:docPartPr>
        <w:style w:val="Heading1" />
        …
    </w:docPartPr>
    ```
    
    带有 val 属性值为 Heading1 的 style 元素指定当前词汇文档条目关联的段落样式必须是其样式 ID 等于 Heading1 的样式。结束示例】
    
    ??? abstract "Attributes"
    
        val（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            [示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的样式 ID 的 ID。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数字是最近的祖先结构化文档标记的标题。在每种情况下，值都是根据父元素的上下文进行解释的。结束示例]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the style ID for a paragraph style which shall be associated with the current glossary document entry. This paragraph style associated shall not imply anything about the formatting or content of the glossary document entry, and shall only be used to filter and/or sort this entry (via an application or a user interface). [Note: One example of the level of classification offered by this element is to only show it as available when the formatting of the paragraph matches the specified style. end note]
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        <w:style w:val="Heading1" />
        …
    </w:docPartPr>
    ```
    
    The style element with a val attribute value of Heading1 specifies that the paragraph style associated with the current glossary document entry must be the style whose style ID is equal to Heading1. end example]
    
    
    ??? abstract "Attributes"
    
        val (String Value)
    
        :   Specifies that its contents contain a string.
    
            The contents of this string are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following WordprocessingML fragment:
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            The value of the val attribute is the ID of the associated paragraph style's styleId.
            
            However, consider the following fragment:
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            In this case, the decimal number in the val attribute is the caption of the nearest ancestor structured document tag. In each case, the value is interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]


## 17.12.15 type (条目类型)

**type (Entry Type)**

=== "中文"
    
    该元素指定应用于父词汇文档条目属性的条目类型（[§17.12.5]）。每个条目类型都可以根据其值影响父词汇文档条目的可见性和行为，这由相关的简单类型信息定义。
    
    [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
    
    ```xml
    <w:docPartPr>
        <w:types>
            <w:type w:val="bbPlcHdr" />
        </w:types>
        …
    </w:docPartPr>
    ```
    
    具有值为 bbPlcHdr 的 type 元素指定父词汇文档条目必须被视为文档中一个或多个结构化文档标记的占位符文本。结束示例]
    
    ??? abstract "Attributes"
    
        **val**（类型值）
    
        :   指定当前条目类型的值。
    
            [示例：考虑以下单个词汇文档条目属性的 WordprocessingML 片段：
            
            ```xml
            <w:type w:val="bbPlcHdr" />
            ```
            
            值为 bbPlcHdr 的 val 属性指定父词汇文档条目必须被视为文档中一个或多个结构化文档标记的占位符文本。结束示例]
            
            The possible values for this attribute are defined by the ST_DocPartType simple type ([§17.18.17]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartType) is located in §A.1. end note]

=== "英文"
    
    This element specifies an entry type which shall be applied to the properties of the parent glossary document entry ([§17.12.5]). Each of these entry types can, based on their values, influence the visibility and behavior of the parent glossary document entry as defined by the associated simple type information.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        <w:types>
            <w:type w:val="bbPlcHdr" />
        </w:types>
        …
    </w:docPartPr>
    ```
    
    The type element with a value of bbPlcHdr specifies that the parent glossary document entry must be treated as if it was the placeholder text for one or more structured document tags in the document. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Type Value)
    
        :   Specifies the value for the current entry type.
    
            [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
            
            ```xml
            <w:type w:val="bbPlcHdr" />
            ```
            
            The val attribute value of bbPlcHdr specifies that the parent glossary document entry must be treated as if it was the placeholder text for one or more structured document tags in the document. end example]
            
            The possible values for this attribute are defined by the ST_DocPartType simple type ([§17.18.17]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartType) is located in §A.1. end note]

## 17.12.16 types (条目类型合集)

**types (Entry Types)**

=== "中文"
        
    此元素指定了应应用于父词汇文档条目（[§17.12.5]）属性的一组条目类型。根据其值，每个条目类型都可以影响父词汇文档条目的可见性和行为。
    
    [示例：考虑以下用于单个词汇文档条目属性的WordprocessingML片段：
    
    ```xml
    <w:docPartPr>
        <w:types>
            …
        </w:types>
        …
    </w:docPartPr>
    ```
    
    types元素指定了必须与父词汇文档条目关联的一组条目类型。结束示例]
    
    
    ??? abstract "属性"
    
        **all**（条目属于所有类型）
        
        :   指定当前词汇文档属于所有条目类型。此属性将覆盖作为此元素子元素指定的任何信息，并确保当前条目与所有可用条目类型相关联。
        
            如果省略此属性，则默认值应视为false。
            
            [示例：考虑以下用于单个词汇文档条目属性的WordprocessingML片段：
            
            ```xml
            <w:docPartPr>
                <w:types w:all="true">
                    <w:type w:val="autoExp" />
                </w:types>
                …
            </w:docPartPr>
            ```
            
            types元素包含一个条目类型定义，但由于all属性的值为true，该条目类型被扩展为将父条目放入所有可能的条目类型中。结束示例]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartTypes) is located in §A.1. end note]

=== "英文"
    
    This element specifies the set of entry types which shall be applied to the properties of the parent glossary document entry ([§17.12.5]). Each of these entry types can, based on their values, influence the visibility and behavior of the parent glossary document entry.
    
    [Example: Consider the following WordprocessingML fragment for the properties of a single glossary document entry:
    
    ```xml
    <w:docPartPr>
        <w:types>
            …
        </w:types>
        …
    </w:docPartPr>
    ```
    
    The types element specifies the set of entry types which must be associated with the parent glossary document entry. end example]
    
    
    ??? abstract "Attributes"
    
        **all** (Entry Is Of All Types)
    
        :   Specifies that the current glossary document is all entry types. This attribute shall override any information specified as child elements of this element and shall ensure that the current entry is associated with all available entry types.
    
            If this attribute is omitted, then its default value shall be assumed to be false. 
            
            [Example: Consider the following WordprocessingML fragment for the properties of a
            single glossary document entry:
            
            ```xml
            <w:docPartPr>
                <w:types w:all="true">
                    <w:type w:val="autoExp" />
                </w:types>
                …
            </w:docPartPr>
            ```
            
            The types element contains a single entry type definition, but because the all attribute is present with a value of true, that entry type is augmented to place the parent entry into all possible entry types. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_DocPartTypes) is located in §A.1. end note]


[§17.12.1]: #17121-behavior-单个条目插入行为
[§17.12.2]: #17122-behaviors-条目插入行为集合
[§17.12.3]: #17123-category-条目分类
[§17.12.4]: #17124-description-条目描述
[§17.12.5]: #17125-docpart-术语文档条目
[§17.12.6]: #17126-docpartbody-术语文档条目内容
[§17.12.7]: #17127-docpartpr-术语文档条目属性
[§17.12.8]: #17128-docparts-术语文档条目列表
[§17.12.9]: #17129-gallery-图库关联的条目
[§17.12.10]: #171210-glossarydocument-术语文档根元素
[§17.12.11]: #171211-guid-条目id
[§17.12.12]: #171212-name-分类关联的条目
[§17.12.13]: #171213-name-条目名称
[§17.12.14]: #171214-style-关联段落样式名称
[§17.12.15]: #171215-type-条目类型
[§17.12.16]: #171216-types-条目类型合集


[§17.2.2]: ./02maindocment.md#1722-body-文档正文

[§17.3.1.22]: ./03paragraphs.md#173122-p-段落

[§17.18.15]: ./18simpletypes.md#171815-st_docpartbehavior-插入行为类型
[§17.18.16]: ./18simpletypes.md#171816-st_docpartgallery-条目画廊类型
[§17.18.17]: ./18simpletypes.md#171817-st_docparttype-条目类型
[§17.18.18]: ./18simpletypes.md#171818-st_docprotect-文档保护类型
[§17.18.19]: ./18simpletypes.md#171819-st_doctype-文档分类值
[§17.18.20]: ./18simpletypes.md#171820-st_dropcap-文本框架首字下沉位置


[§22.9.2.4]: ../chapter22/sharedsimpletypes.md#22924-st_guid-128-bit-guid
[§22.9.2.6]: ../chapter22/sharedsimpletypes.md#22926-st_lang-语言参考
[§22.9.2.7]: ../chapter22/sharedsimpletypes.md#22927-st_onoff-开关值
[§22.9.2.13]: ../chapter22/sharedsimpletypes.md#229213-st_string-字符串