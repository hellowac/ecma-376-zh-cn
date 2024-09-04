# L.7 其他主题

**Miscellaneous Topics**

## L.7.1 其他特性

**Additional Characteristics**

=== "中文"

    Office Open XML 提供了一种方式，允许生产者向消费者提供有关数据是如何创建的以及应该如何解释的信息。这些信息由一个或多个额外的特性提供。
    
    生成应用程序可以选择写入任意多或任意少的额外特性。
    
    消费应用程序可以选择对额外特性采取行动或忽略它们。额外特性存储在一个单独的XML部分，如下所示：
    
    ```xml
    <additionalCharacteristics>
        <characteristic name="特性名称"
            relation="定义良好的关系类型集合"
            val="字符串" vocabulary="uri"/>
    </additionalCharacteristics>
    ```
    
    例如，考虑numColumns作为特性名称，用于指定生成的SpreadsheetML应用程序支持的最大列数，以便消费应用程序可以理解如何明确区分单元格引用和变量。
    
    relation属性指定了应如何解释val属性。relation的可能值是：lt | le | eq | gt | ge，分别表示&lt;, &lt;=, =, &gt;=, &gt;，并分别用于数值比较和字符串排序的字母顺序比较。这些关系允许表达最大值、最小值、值等。
    
    vocabulary属性是一个URI，为name属性提供的特定特性名称提供命名空间。这允许在给定的应用领域内创建一个感兴趣的特性词汇，而不必担心词汇之间的名称冲突。
    
    另一个用例示例是，生产者通知消费者，用于计算SpreadsheetML公式中存储数字的计算使用了特定的数值精度，由尾数和指数表示。消费者可以可选地检查这些值，以确定是否应该重新计算这些值。表示这些特性的XML可能如下所示：
    
    ```xml
    <additionalCharacteristics>
        <characteristic name='precisionMantissa'
            relation='gt'
            val='-9007199254740992'/>
        <characteristic name='precisionMantissa'
            relation='lt' val='9007199254740992'/>
        <characteristic name='precisionExponent'
            relation='ge' val='-1075'/>
        <characteristic name='precisionExponent'
            relation='le' val='970'/>
    </additionalCharacteristics>
    ```

=== "英文"

    Office Open XML provides a way for a producer to provide information to consumers regarding how the data was created and how it should be interpreted. This information is provided by one or more additional characteristics.

    A producing application has the option of writing out as many or as few additional characteristics as desired.
    
    A consuming application has the option of acting on the additional characteristics or ignoring them The additional characteristics are stored in a separate XML part, as follows:
    
    ```xml
    <additionalCharacteristics>
        <characteristic name="name of characteristic"
            relation="well defined set of relation types"
            val="string" vocabulary="uri"/>
    </additionalCharacteristics>
    ```
    
    For example, consider the case in which numColumns is the characteristic name to specify the maximum number of columns supported by the producing SpreadsheetML application, so that the consuming application can understand how to distinguish cell references and variables unambiguously.
    
    The relation attribute specifies the way in which the val attribute should be interpreted. The possibl values for relation are: lt | le | eq | gt | ge, which mean &lt;, &lt;=, =, &gt;=, &gt;, respectively, and relate t numerical comparison for values and alphabetical comparison for ordering of strings. These relation permit expression of the maximum value, the minimum value, the value, and so on.
    
    The vocabulary attribute is a URI that provides a namespace for the specific characteristic name provided as values of the name attribute. This allows for the creation of a vocabulary of characteristic of interest within a given domain of application without concern for name conflict betwee vocabularies.
    
    Another example use case would be for a producer to inform the consumer that the computations used to calculate the stored numbers in the SpreadsheetML formulas have a particular numeric precision expressed by the mantissa and exponent. A consumer can optionally check those values to determine whether, for example, the values should be recalculated. The XML to represent these characteristics might look like the following:
    
    ```xml
    <additionalCharacteristics>
        <characteristic name='precisionMantissa'
            relation='gt'
            val='-9007199254740992'/>
        <characteristic name='precisionMantissa'
            relation='lt' val='9007199254740992'/>
        <characteristic name='precisionExponent'
            relation='ge' val='-1075'/>
        <characteristic name='precisionExponent'
            relation='le' val='970'/>
    </additionalCharacteristics>
    ```

## L.7.2 嵌入

**Embeddings**

=== "中文"

    Office Open XML 提供了在文档中嵌入任何对象的功能。例如，WordprocessingML 文档可能包含作为嵌入的 SpreadsheetML 文档的数据，而不是原生的 WordprocessingML 表格，以便允许该数据由 SpreadsheetML 计算引擎进行编辑和重新计算，而不是将其存储为静态数据表。
    
    Office Open XML 为嵌入对象提供了两类：
    
    - 嵌入包 - 一个嵌入的 Office Open XML 文档嵌入在另一个 Office Open XML 文档中，两个文档都存储在此 Office Open XML 规范定义的格式中。例如，一个嵌入在 SpreadsheetML 文档中的 PresentationML 文档就形成了一个嵌入包。
    - 嵌入对象 - 任何其他嵌入对象数据。存储在对象中的数据必须通过一个唯一的字符串来识别，称为其 ProgID。这个字符串必须用来确定数据的类型以及（如果有的话）用于加载和编辑嵌入对象数据的应用程序。
    
    Office Open XML 还允许与嵌入对象数据可选地关联一个图像，以供在嵌入对象应用程序和数据本身不被消费应用程序使用时使用（例如，当对象无法加载时 - 对象来自未知来源；对象已知，但应用程序出于性能原因选择不加载它等）。

=== "英文"

    Office Open XML provides facilities allowing the embedding of any object within a document. For example, a WordprocessingML document might include data as an embedded SpreadsheetML document rather than a native WordprocessingML table, in order to allow that data to be edited and recalculated by a SpreadsheetML calculation engine, rather than having it stored as a static table of data.
    
    Office Open XML provides for two classes of embedded objects:
    
    - Embedded Packages - An embedded Office Open XML document embedded within anothe Office Open XML document, with both documents stored in the format defined by this Offic Open XML specification. For example, a PresentationML document embedded within  SpreadsheetML document results in an embedded package.
    - Embedded Objects - Any other embedded object data. The data stored in the object must be identified by a unique string, referred to as its ProgID. This string must be used to determine both the type of data and the application (if any) that must be used to load and edit the embedded object data.
    
    Office Open XML also allows an image to be optionally associated with the embedded object data, for use when the embedded object application and data itself is not used by the consuming application (e.g. when the object cannot be loaded – the object is from an unknown source; the object is known, but the application has chosen not to load it for performance reasons, and so on).

### L.7.2.1 嵌入包

**Embedded Packages**

=== "中文"
    
    当Office Open XML文档作为嵌入对象存储时，这种嵌入必须被称为嵌入包。嵌入包必须是第一部分定义的“嵌入包关系”的目标：[http://purl.oclc.org/ooxml/officeDocument/relationships/package](http://purl.oclc.org/ooxml/officeDocument/relationships/package)。这是Office Open XML规范的一部分。

=== "英文"
    
    Whenever an Office Open XML document is stored as an embedded object, the embedding must be referred to as an embedded package. Embedded packages must be the target of the Embedded Package relationship defined in Part 1: http://purl.oclc.org/ooxml/officeDocument/relationships/package. this Office Open XML specification

### L.7.2.2 嵌入对象

**Embedded Objects**

=== "中文"
    
    对于所有其他嵌入，嵌入对象以由嵌入数据的应用程序定义的任意格式存储。这些通用的嵌入对象必须是“嵌入对象关系”的目标：http://purl.oclc.org/ooxml/officeDocument/relationships/oleObject。当解析嵌入对象部分中存储的数据时，应用程序必须使用对象的关联ProgID（其位置在以下子条款中描述）。

=== "英文"
    
    For all other embeddings, the embedded object is stored in an arbitrary format defined by the application whose data is being embedded. These generic embedded objects must be the target of the Embedded Object relationship: http://purl.oclc.org/ooxml/officeDocument/relationships/oleObject. When parsing the data stored in an embedded object part, an application must use the associated ProgID (whose location is described in the following subclauses) for the object.


### L.7.2.3 WordprocessingML文档中的嵌入

**Embeddings in a WordprocessingML Document**

=== "中文"

    当一个嵌入存储在WordprocessingML文档中时，它以以下方式之一存储：
    
    - 与文本同行 - 对象在常规文本流中显示（修改行高等以适应它）。
    - 浮动 - 对象在文档中绝对或相对定位，并且根据需要修改文本流以围绕它。
    
    每种情况都允许存储对象以及可选的图像表示，当宿主应用程序不使用对象数据时可以使用，如下所示：

=== "英文"

    When an embedding is stored in a WordprocessingML document, it is stored in one of the following ways:
    
    - In line with text - The object is displayed within the regular text stream (modifying line height and so on to accommodate it).
    - Floating – The object is positioned absolutely or relatively within the document and text flow is modified as needed around it.
    
    Each case permits the storage of both the object and the optional image representation that can be used when the object data is not used by the hosting application as follows:


#### L.7.2.3.1 与文本同步嵌入

**Embeddings In Line With Text**

=== "中文"

    当嵌入与文本同行时，它按照以下方式存储：
    
    - WordprocessingML 对象元素指定了与文本同行的嵌入对象的存在。
    - 子对象元素 objectEmbed 或 objectLink 必须指定有关嵌入本身的详细信息，包括对适当的嵌入包或嵌入对象部分的显式关系。
    - 子元素 inline 必须指定可以用来表示对象的图像。
    
    例如，如果我们在WordprocessingML文档中嵌入一个SpreadsheetML工作表，将会出现以下运行内容：
    
    ```xml
    <w:r>
        <w:object w:dxaOrig="7247" w:dyaOrig="2920">
            <w:objectEmbed drawAspect="content" r:id="rId7" progId="Excel.Sheet.8"
                shapeId="10"/>
            <w:drawing>
                <wp:inline> ... </wp:inline>
            </w:drawing>
        </w:object>
    </w:r>
    ```
    
    如果我们检查这个标记，可以看到：
    
    - 我们有一个内嵌对象，由对象元素定义。
    - objectEmbed 元素指定该对象存储为嵌入，它的 ProgID 是 Excel.Sheet.8（Microsoft Excel 工作表的 ProgID 代码）；它还指定当对象数据无法使用时，与 ID 为 10 的形状关联的图像存储在其中。
    - 与 ID 为 _x0000_i1026 的关联形状必须在对象未加载时代替对象使用 - 这个形状存储在与 objectEmbed 元素相同的对象元素中的 inline 元素内。这个形状指定了其期望的大小，并提供了与存储图像数据部分的显式关系。

=== "英文"

    When the embedding is present in line with text, it is stored as follows:

    - The WordprocessingML object element specifies the presence of an embedded object in line with text.
    - The child objectEmbed or objectLink element must specify the details about the embedding itself, including an explicit relationship to the appropriate Embedded Package or Embedded Object part.
    - The child inline element must specify the image which can be used to represent the object.

    For example, if we embed a SpreadsheetML worksheet in a WordprocessingML document, the following run content would be present:

    ```xml
    <w:r>
        <w:object w:dxaOrig="7247" w:dyaOrig="2920">
            <w:objectEmbed drawAspect="content" r:id="rId7" progId="Excel.Sheet.8"
                shapeId="10"/>
            <w:drawing>
                <wp:inline> ... </wp:inline>
            </w:drawing>
        </w:object>
    </w:r>
    ```

    If we examine this markup, it can be seen that:

    - We have an inline embedded object, as defined by the object element.
    - The objectEmbed element specifies that that object is stored as an embedding, and that its ProgID is Excel.Sheet.8 (the ProgID code for Microsoft Excel worksheets); it also specifies that the associated image (when the object data cannot be used) is stored in the shape with an ID of 10.
    - The associated shape with an ID of _x0000_i1026 must be used in place of the object whenever it is not loaded - this shape is stored in the inline element in the same object element as the objectEmbed element. This shape specifies its desired size and provides an explicit relationship to the part that stores the image data.


#### L.7.2.3.2 浮动嵌入

**Floating Embeddings**

=== "中文"

    当嵌入作为浮动对象存在时，它按照以下方式存储：
    
    - WordprocessingML 的 pict 元素指定了文档中浮动图像的存在。
    - 子对象元素 objectEmbed 或 objectLink 必须指定有关嵌入本身的详细信息，包括对适当的嵌入包或嵌入对象部分的显式关系。
    - 子元素 anchor 必须指定可以用来代替加载实际对象数据的对象的图像。
    
    例如，如果我们在WordprocessingML文档中作为浮动对象嵌入一个SpreadsheetML工作表，将会出现以下运行内容：
    
    ```xml
    <w:r>
        <w:object>
            <w:objectEmbed drawAspect="content" r:id="rId5" progId="Excel.Sheet.8" shapeId="18"/>
            <w:drawing>
                <wp:anchor> ... </wp:anchor>
            </w:drawing>
        </w:object>
    </w:r>
    ```
    
    如果我们检查这个标记，可以看到：
    
    - 我们有一个浮动图像，由 pict 元素定义。
    - objectEmbed 元素指定这个浮动图像实际上是一个存储为 Embed 的嵌入，它的 ProgID 是 Excel.Sheet.8（Microsoft Excel 工作表的 ProgID 代码）；它还指定当对象数据无法使用时，与 ID 为 18 的形状关联的图像存储在其中。
    - 与 ID 为 18 的关联形状必须在对象未加载时代替对象使用 - 这个形状存储在与相应 OLEObject 元素相同的对象元素中的 anchor 元素内。这个形状指定了其期望的大小，并提供了与存储图像数据部分的显式关系。

=== "英文"

    When the embedding is present as a floating object, it is stored as follows:
    
    - The WordprocessingML pict element specifies the presence of a floating image in th document.
    - The child objectEmbed or objectLink element must specify the details about the embedding itself, including an explicit relationship to the appropriate Embedded Package or Embedded Object part.
    - The child anchor element must specify the image that can be used to represent the object in place of loading the actual object data.
    
    For example, if we embed a SpreadsheetML worksheet in a WordprocessingML document as a floating object, the following run content would be present:
    
    ```xml
    <w:r>
        <w:object>
            <w:objectEmbed drawAspect="content" r:id="rId5" progId="Excel.Sheet.8" shapeId="18"/>
            <w:drawing>
                <wp:anchor> ... </wp:anchor>
            </w:drawing>
        </w:object>
    </w:r>
    ```
    
    If we examine this markup, it can be seen that:
    
    - We have a floating image, as defined by the pict element.
    - The objectEmbed element specifies that that floating image is actually an embedding that is stored as an Embed, and that its ProgID is Excel.Sheet.8 (the ProgID code for Microsoft Excel worksheets); it also specifies that the associated image (when the object data cannot be used) is stored in the shape with an ID of 18.
    - The associated shape with an ID of 18 must be used in place of the object whenever it is not loaded - this shape is stored in the anchor element in the same object element as the corresponding OLEObject element. This shape specifies its desired size and provides an explicit relationship to the part which stores the image data.

### L.7.2.4 SpreadsheetML文档中的嵌入

**Embeddings in a SpreadsheetML Document**

=== "中文"

    当嵌入存在于SpreadsheetML文档中时，它必须按照以下方式存储：
    
    - 在工作表中，oleObjects元素必须存储一个或多个oleObject子元素，每个嵌入在当前工作表中的元素都有一个。这些oleObject子元素还必须存储：对相关嵌入包或嵌入对象部分的显式关系、嵌入对象的ProgID，以及（可选地）相关形状的ID。[注：为了向后兼容，请注意，VML形状ID的形式是_x0000_s####，其中#指定一个单一的阿拉伯数字，并且只有最后四位数字被存储为ID。结束注]
    - 在工作表中，同级的objectPr元素必须包含一个显式关系，指向（可选地）包含可用作加载实际对象数据的替代图像数据的绘图部分。
    
    例如，如果我们在SpreadsheetML文档中嵌入一个示例测试对象（用于说明的示例），以下标记将存储在适当的工作表部分：
    
    ```xml
    <s:worksheet>
        …
        <s:oleObjects>
            <s:oleObject progId="Example.Test.1" shapeId="1025" r:id="rId5">
                <s:objectPr cf="pict" r:id="rId9"> ... </s:objectPr>
            </s:oleObject>
        </s:oleObjects>
    </s:worksheet>
    ```
    
    如果我们检查这个标记，可以看到：
    
    - oleObject元素指定我们在工作表上有一个嵌入对象。它的属性指定对象是Example.Test.1类型，并且嵌入对象的显式关系是rId5。
    - 子元素objectPr指定包含相关绘图数据的绘图部分位于关系ID为rId9的目标处。
    - 如果我们检查绘图部分的内容，我们将看到形状10，它包含了对象的替代图像。

=== "英文"

    When an embedding is present in a SpreadsheetML document, it must be stored as follows:
    
    - In the worksheet, the oleObjects element must store one or more oleObject child elements, one for each embedding within the current worksheet. Each of those oleObject child elements must also store: an explicit relationship to the associated Embedded Package or Embedded Object part, the ProgID for that embedded object, and (optionally) the ID for the associated shape. [Note: For backward compatibility, note that VML shape IDs are of the form _x0000_s####, where # specifies a single Arabic numeral, and only the last four digits are stored as the ID. end note]
    - In the worksheet, the sibling objectPr element must contain an explicit relationship to the Drawing part that (optionally) contains the image data which can be used in place of loading the actual object data.
    
    For example, if we embed a Example Test object (an example for illustration) in a SpreadsheetML document, the following markup would be stored in the appropriate Sheet part:
    
    ```xml
    <s:worksheet>
        …
        <s:oleObjects>
            <s:oleObject progId="Example.Test.1" shapeId="1025" r:id="rId5">
                <s:objectPr cf="pict" r:id="rId9"> ... </s:objectPr>
            </s:oleObject>
        </s:oleObjects>
    </s:worksheet>
    ```
    
    If we examine this markup, it can be seen that:
    
    - The oleObject element specifies that we have one embedded object on the worksheet. Its attributes specify that the object is of type Example.Test.1 and that the explicit relationship to the embedded object is rId5.
    - The child objectPr element specifies that the Drawing part which contains the associated drawing data is contained at the target of the relationship with an ID of rId9.
    - If we examine the Drawing part's contents, we'll see shape 10, which contains the alternate image for the object.

### L.7.2.5 PresentationML文档中的嵌入

**Embeddings in a PresentationML Document**

=== "中文"

    当嵌入存在于PresentationML文档中时，它必须按照以下方式存储：
    
    - 在幻灯片中，嵌入被存储为使用PresentationML中的graphicFrame元素的图形框架。
    - 框架的graphicData元素必须具有其内容的适当URI：[http://purl.oclc.org/ooxml/presentationml/ole](http://purl.oclc.org/ooxml/presentationml/ole)。它的子元素必须是PresentationML oleObj元素，该元素存储对相关嵌入包或嵌入对象部分的显式关系、嵌入对象的ProgID，以及（可选地）相关形状的形状ID。
    - oleObj元素应具有一个pic子元素，该元素（可选地）包含图像数据，以替代加载实际对象数据。
    
    例如，如果我们在PresentationML文档中嵌入Equation.3对象，以下标记将存储在适当幻灯片部分的形状树中：
    
    ```xml
    <p:graphicFrame>
        …
        <a:graphic>
            <a:graphicData
                uri="http://purl.oclc.org/ooxml/presentationml/ole"> 
                <p:oleObj spid="10" name="Equation" r:id="rId3"
                    imgW="320" imgH="272" progId="Equation.3">
                    <p:embed />
                    <p:pic>
                        …
                    </p:pic>
                </p:oleObj>
            </a:graphicData>
        </a:graphic>
    </p:graphicFrame>
    ```
    
    如果我们检查这个标记，可以看到：
    
    - graphicData元素上的uri属性是[http://purl.oclc.org/ooxml/presentationml/ole](http://purl.oclc.org/ooxml/presentationml/ole)，这表明这是一个嵌入对象。
    - 它包含一个oleObj元素，该元素指定了嵌入对象的属性。它的属性指定对象是Equation.3类型，并且嵌入对象的显式关系是rId3。
    - oleObj元素还可以包含定义形状ID为10（如果有的话）的DrawingML，该形状定义了对象的替代图像。
    

=== "英文"

    When an embedding is present in a PresentationML document, it must be stored as follows:
    
    - In the slide, the embedding is stored as a graphic frame using the graphicFrame element in PresentationML.
    - The graphicData element for the frame must have the appropriate URI for its contents: http://purl.oclc.org/ooxml/presentationml/ole. Its child element must be the PresentationML oleObj element, which stores an explicit relationship to the associated Embedded Package or Embedded Object part, the ProgID for that embedded object, and (optionally) the shape ID for the associated shape.
    - The oleObj element shall have a pic child element that (optionally) contains the image data t be used in place of loading the actual object data.
    
    For example, if we embed the Equation.3 object in a PresentationML document, the followin markup would be stored in the shape tree of the appropriate Slide part:
    
    ```xml
    <p:graphicFrame>
        …
        <a:graphic>
            <a:graphicData
                uri="http://purl.oclc.org/ooxml/presentationml/ole">
                <p:oleObj spid="10" name="Equation" r:id="rId3"
                    imgW="320" imgH="272" progId="Equation.3">
                    <p:embed />
                    <p:pic>
                        …
                    </p:pic>
                </p:oleObj>
            </a:graphicData>
        </a:graphic>
    </p:graphicFrame>
    ```
    
    If we examine this markup, it can be seen that:
    
    - The uri attribute on the graphicData element is http://purl.oclc.org/ooxml/presentationml/ole, which dictates that this is an embedded object
    - It contains an oleObj element that specifies the properties of the embedded object. Its attributes specify that the object is of type Equation.3 and that the explicit relationship to the embedded object is rId3.
    - The oleObj element can also contain DrawingML defining the shape with ID 10 (if present) which defines the alternate image.
    

## L.7.3 未来的可扩展性

**Future Extensibility**

=== "中文"

    这一条款提供了Office Open XML文档的可扩展性模型的高级概述，以及在DrawingML和PresentationML背景下的打包约定的描述。描述了两个主要的构建：应用程序定义的扩展元素（extLst）和替代内容块（AlternateContent）。
    
    为了说明某些点，许多示例引用了一个（虚构的）PresentationML消费者/生产者PML的不同版本。2003年版本称为PML 2003；2007年版本称为PML 2007；以此类推。

=== "英文"

    This clause provides a high-level overview of the extensibility model for Office Open XML documents, and a description of packaging conventions in the context of DrawingML and PresentationML. Two main constructs are described: application-defined extension elements (extLst) and alternate content blocks (AlternateContent).
    
    To illustrate certain points, a number of examples refer to versions of a (fictitious) PresentationML consumer/producer called PML. The 2003 version is called PML 2003; the 2007 version is called PML 2007; and so on.


### L.7.3.1 术语

**Terminology**

=== "中文"

    以下是一些在讨论未来可扩展性时有用的术语。
    
    - **双向兼容性**（Round tripping）指的是文档在不同的消费者/生产者之间，以及同一消费者/生产者的不同胞版本之间的交换。这些消费者/生产者可以在相同或不同的平台上。考虑这样一种情况：一个文档由PML 2007创建。然后这个文档被PML 2003打开，编辑并保存。编辑后的文档现在被PML 2007打开并使用。在这种情况下，最初由PML 2007创建的文档已经通过PML 2003进行了双向交换。同样，也可以将由PML 2003创建的文档通过PML 2007进行双向交换。
    
    - **低版本**（Downrev）消费者/生产者的版本指的是理解给定模式的较旧版本的一个。而**高版本**（Uprev）消费者/生产者的版本指的是理解给定模式的较新版本的一个。Downrev和Uprev这两个术语通常相对于彼此使用。例如，再次考虑两个消费者/生产者PML 2003和PML 2007，其中PML 2007在PML 2003之后发布，因此PML 2007理解DrawingML模式的新修订版，而PML 2003则不然。PML 2003被称为低版本，而PML 2007被称为高版本。通常认为，低版本的功能比高版本要少。

=== "英文"

    Here are some terms useful when discussing future extensibility.
    
    - *Round tripping* involves the interchange of documents between different consumers/producers, as well as between different versions of the same consumer/producer. The pair of consumers/producers can be on the same or different platforms. Consider the case in which a document is created by the PML 2007. This document is then opened by PML 2003, edited, and saved. The edited document is now opened and used by PML 2007. In this case, the document originally created by PML 2007 has been round-tripped through PML 2003. It is also possible to round-trip a document created by PML 2003 through PML 2007.
    - A *Downrev* (or down-level) version of a consumer/producer refers to one that understands an older version of a given schema. An Uprev (or up-level) version of a consumer/producer refers to one that understands a newer version of a given schema. The terms Downrev and Uprev are typically used in relative reference to one another. As an example, let's consider again, the two consumer/producer PML 2003 and PML 2007, where PML 2007 was released sometime after PML 2003, and, consequently, PML 2007 understands a newer revision of the DrawingML schema then does PML 2003. PML 2003 is referred to as the Downrev version while PML 2007 is referred to as the Uprev version. It is assumed that the Downrev version has less capability than the Uprev version.


### L.7.3.2 什么是未来的可扩展性?

**What is Future Extensibility**

=== "中文"

    未来可扩展性的主要目标是设计一个基础设施，允许文件格式被扩展，以表示给定消费者/生产者的将来版本的数据结构。
    
    表面上，这不难做到；可以在每个现有的模式元素中分配一个特殊的扩展位存储桶，任何未来的扩展都可以放在那里。然而，问题比这更复杂。该基础设施必须允许当前消费者/生产者和未来的消费者/生产者之间的文档互操作性，其中一些甚至还没有被设计或构建。也就是说，未来可扩展性涉及在文档基础设施中构建向前兼容性，同时保持与当前版本的兼容性。

=== "英文"

    The main objective of future extensibility is to design an infrastructure that allows the file format to be extended for representation of data structures in future versions of a given consumer/producer.
    
    On the surface, that isn’t hard to do; there could be a special extension bit bucket allocated across every existing schema element, and any future extension could be placed there. However, the problem is more complex than that. The infrastructure must allow document interoperability between current consumers/producers and future consumers/producers, some which have not yet even been designed or built. That is, future extensibility involves building forward compatibility into the document infrastructure while remaining compatible with the current version.

### L.7.3.3 未来的扩展要求

**Future Extensibility Requirements**

=== "中文"

    在设计未来可扩展性时，需要考虑以下三个设计目标：视觉保真度、可编辑性和安全性。
    
    - **视觉保真度**涉及两个不同消费者/生产者的用户希望看到视觉上相同的东西的愿望。这看起来像是一个简单的设计目标，但实际上并不容易实现。差异在于高版本（Uprev）和低版本（Downrev）消费者/生产者的能力。通常，高版本的消费者/生产者已被扩展以具有新的基础能力，这些能力在低版本的消费者/生产者中不存在。因此，低版本的客户端没有必要的基础元素来视觉上表达高版本消费者/生产者中引入的新能力。
    
      考虑这样一个案例：PML 2007具有用特定颜色突出显示文本的能力，而PML 2003则没有。鉴于希望PML 2007文档与PML 2003互操作的愿望，有必要让PML 2003以某种方式视觉上表达文本突出显示。例如，它可能会插入突出显示文本的图片，而不是插入文本本身，因为PML 2003知道如何处理图片。
    
    - **可编辑性**涉及两个消费者/生产者能够编辑相同内容的愿望。使用上面的突出显示文本示例，尽管PML 2003和PML 2007具有不同的能力，但我们仍然希望能够编辑突出显示的文本，无论使用哪个版本的PML。当消费者/生产者版本的底层能力不同时，这又变得困难。
    
    - **安全性**涉及希望同一数据的多个表现形式被同步的愿望。这种愿望被称为安全性，因为不同步的表现形式可能会产生严重后果。例如，可能有多个表现形式对于敏感信息，如社会安全号码。如果编辑了这个信息，保持所有替代表现形式的同步至关重要。如果该信息被完全删除怎么办？如果只删除了一个表现形式，而其他表现形式仍然存在，那么当意图是删除它时，文档中仍然可能包含敏感信息。
    
    一个尝试解决视觉保真度和可编辑性目标的解决方案是为相同的构建拥有两个等效的表现形式。在上面的突出显示文本示例中，突出显示文本的图片（也称为突出显示文本的光栅版本）是突出显示文本本身的等效表现形式。当底层消费者/生产者能够理解突出显示文本的表现形式时，可能会使用它；否则，将使用图片版本。
    
    显然，这些设计目标相互竞争。虽然文本的图片表现形式能够捕捉到扩展文本的完整视觉保真度，但显然该表现形式并不提供与文本本身相同的可编辑性属性。人们几乎不能像操作文本本身那样容易地操作文本的图片。
    
    这些设计特性的竞争性质要求选择一个可扩展性构建，它提供了最佳的特性组合。同时拥有视觉保真度、可编辑性和安全性并不总是可能的。

=== "英文"

    There are three design goals to be considered: visual fidelity, editability, and security.
    
    - *Visual fidelity* involves the desire for users of two consumers/producers to see visually the same thing. This seems like a simple design goal to meet, but, in practice, is not easy to achieve. The difference lies in the capabilities of an Uprev and Downrev consumer/producer. Typically, an Uprev consumer/producer has been extended to have new base capabilities that are not present in the Downrev consumer/producer. As such, the Downrev client does not have the base primitives necessary to express visually the new capability introduced in the Uprev consumer/producer.
    
        Consider the case in which PML 2007 has the capability to highlight text with a given color, while PML 2003 does not. Given the desire to have PML 2007 documents interoperate with PML 2003, it is necessary for PML 2003 to some way to express visually that text highlight. For example, it might insert a picture of the highlighted text instead of inserting the text itself, since PML 2003 does know how to deal with pictures.
    
    - *Editability* involves the desire for two consumers/producers to be able to edit the same content. Using the highlighted text example from above, despite the fact that PML 2003 and PML 2007 have different capabilities, one would still desire to edit highlighted text a regardless of which version of PML is in use. Again, this becomes difficult when the underlying capabilities of the consumer/producer versions are different.
    - *Security* involves the desire to have multiple representations of the same data synchronized. This desire is referred to as security for the reason that out-of-sync representation can have dire consequences. For example, there might be multiple representations for a sensitive piece of information such as a Social Security number. If this piece of information were edited, it would be critical to keep all alternate representations in sync. What if that information were deleted altogether? If only one representation was deleted but others remained, it would be possible for one to have sensitive information in a document when the intent was to have it deleted.
    
    One solution to try to solve the visual fidelity and editability goals is to have two equivalent representations for the same construct. In the highlighted text example above, a picture of the highlighted text (also called a rasterized version of the highlighted text) is an equivalent representation of the highlighted text itself. One might use the highlighted text representation when the underlying consumer/producer is capable of understanding it; otherwise, the picture version would be used.

    Clearly, these design goals compete with each other. While a picture representation of text is capable of capturing full visual fidelity of how extended text looks, obviously that representation doesn't offer the same editability properties of text. One can't manipulate a picture of text nearly as easily as the text itself.

    The competing nature of these design characteristics requires that one choose an extensibility construct that offers the best mix of desired characteristics. It is not always possible to have visual fidelity, editability, and security, at the same time.

### L.7.3.4 未来的可扩展构造

**Future Extensibility Constructs**

=== "中文"
    
    在OOXML（Office Open XML）模式中，用于表示扩展的两种可扩展性构建是：

=== "英文"
    
    The two extensibility constructs used to represent extensions in OOXML schemas are:

#### L.7.3.4.1 extLst

**extLst**

=== "中文"

    `extLst` 构建用于直接扩展现有的非视觉性质的模式。"直接"这个术语指的是有时扩展意味着细化现有构建的语义。在这样做的过程中，扩展有时会覆盖之前模式的含义。`extLst` 并不是为这种场景设计的。它不是覆盖现有的含义，而是纯粹地增加现有模式。增加的性质必须是不与现有模式构建中嵌入的任何语义重叠。
    
    考虑一个表示地址的模式，其中包含一个门牌号、街道名称、城市、州和邮政编码。一个直接扩展的例子是添加一个字段来描述这个地址是商业还是住宅位置。这是一个直接扩展，因为地址是商业还是住宅的概念并不与现有模式中嵌入的任何信息冲突。现在让我们考虑一下邮政服务将纯数字邮政编码替换为可以包含字母数字字符的情况。这样的变化将不是一个直接扩展，因为新的表现与同一数据的旧表现，即邮政编码，发生了冲突。
    
    一些扩展是视觉性质的。一个例子是扩展模式以表示已突出显示的文本。按定义，突出显示文本是视觉扩展。与添加商业或住宅分类的情况相对比，后者并不一定涉及数据呈现方式的任何视觉变化。
    
    `extLst` 构建用于非视觉性质的扩展。其使用限于这种情况的主要原因在于它没有提供创建相同数据的替代表现形式的能力。

=== "英文"

    The extLst construct is used for straight-up extension of existing schemas of a non-visual nature. The term straight up refers to the notion that sometimes extension means refining the semantics of existing constructs. In doing so, an extension sometimes overrides the meaning of previous schemas. extLst was not designed for this scenario. Instead of overriding existing meaning, this construct purely augments existing schemas. The nature of the augmentation must be such that it does not overlap any semantics embedded in existing schema constructs.
    
    Consider a schema that represents an address, which contain a house number, a street name, a city, a state, and a postal code. An example of a straight-up extension is the addition of a field that describes whether this address is a business or residential location. This is a straight-up extension because the notion of whether an address is business or residential does not conflict with any information that is embedded in the existing schema. Now let's consider the case in which the Postal Service replaces a purely numeric postal code with one that can contain alphanumeric characters. Such a change would not be a straight-up extension because the new representation conflicts with the old representation of the same data, namely the postal code.
    
    Some extensions are visual in nature. An example would be extending a schema to represent text that has been highlighted. By definition, highlighting text is a visual extension. Contrast that to the case of adding a business or residential classification. The latter does not necessarily involve any visual change to the way data is presented.
    
    The extLst construct is for extensions of a non-visual nature. The main reason its use is limited to this scenario lies in the fact that it does not offer the capability to create alternative representations of the same data.

##### L.7.3.4.1.1 extLst 语法

**extLst Syntax**

=== "中文"

    `extLst` 元素只能在 OOXML 模式中的特定位置放置。它的语法如下：
    
    ```xml
    <extLst mod="true">
        <ext uri="http://schemas.openformats.org/presentationml/someextensionpoint"> 
            <new:foo xmlns:new=
            "http://schemas.openformats.org/presentationml/2008/presentationml"> 
            ...
            </new:foo>
        </ext>
        <ext uri="http://schemas.somevendor.com/presentationml/someextensionpoint"> 
            <somevendor:bar xmlns:somevendor=
            "http://schemas.somevendor.com/V20/ournamespace"> 
            ...
            </somevendor:bar>
        </ext>
        ...
    </extLst>
    ```
    
    `extLst` 是一系列一个接一个放置的扩展块列表。每个扩展块都有一个 uri 属性，该属性作为标识符，用于指示在这里放置了哪种扩展。在遇到一个扩展块时，处理消费者会确定它是否知道如何处理与该 uri 属性匹配的扩展。如果消费者知道如何处理这样的扩展，那么该扩展块中包含的标记就会被处理。否则，只要通过 extLst 扩展的底层结构没有被删除，扩展块就会被保留。
    
    扩展块构造 `ext` 的数量没有限制。扩展块的顺序可以是任意的。
    
    `extLst` 上有一个可选的 modified 属性，mod。每当在扩展位置发生编辑时，就将此属性设置为 true。其存在是为了帮助高版本的客户端处理在低版本的消费者/生产者中编辑过的修改过的文档。

=== "英文"

    The extLst element can be placed only at specific locations within the OOXML schemas. Its syntax is as below:
    
    ```xml
    <extLst mod="true">
        <ext uri="http://schemas.openformats.org/presentationml/someextensionpoint">
            <new:foo xmlns:new=
            "http://schemas.openformats.org/presentationml/2008/presentationml">
            ...
            </new:foo>
        </ext>
        <ext uri="http://schemas.somevendor.com/presentationml/someextensionpoint">
            <somevendor:bar xmlns:somevendor=
            "http://schemas.somevendor.com/V20/ournamespace">
            ...
            </somevendor:bar>
        </ext>
        ...
    </extLst>
    ```
    
    An extLst is a list of extension blocks that are placed one after the other. Each extension block has a uri attribute, which serves as an identifier to indicate the kind of extension that has been placed here. Upon encountering an extension block, a processing consumer determines whether it knows how to process extensions matching that uri attribute. If the consumer knows how to process such an extension, the markup contained within that extension block is processed. Otherwise, the extension block is preserved so long as the underlying structure being extended by the extLst has not been deleted.
    
    There is no limit to the number of ext extension block constructs. The order of extension blocks can be arbitrary.
    
    An optional modified attribute, mod, is available on extLst. This attribute is set to true whenever an edit has occurred at the extended location. Its presence is to aid up-level clients that receive modified documents that have been edited in down-level consumers/producers.


##### L.7.3.4.1.2 扩展块的往返行为

**Round-Trip Behavior of ext Blocks**

=== "中文"
    
    当处理 `extLst` 时，一些消费者/生产者理解某些扩展，但不理解其他扩展。扩展块 (`ext` 块) 的保留模型是，只要被扩展的结构的底层模式仍然存在，未处理的扩展总是会被保留和维持。

=== "英文"
    
    When extLsts are processed, some consumers/producers understand some extensions but not others. The preservation model of ext blocks is that unprocessed extensions are always preserved and retained as long as the underlying schema extended by the structure remains.


##### L.7.3.4.1.3 样例

**Example**

=== "中文"

    考虑这样一种情况：每个形状都可以与给定的层相关联的概念将被添加。这个模式可能看起来像下面这样：
    
    ![123](./imgs/Image32210.png)
    
    `extLst` 块位于非视觉形状属性下（即 `p:nvSpPr`）。一个 `uri` 属性标识了扩展。
    
    现在考虑这种标记是如何被PML 2007和PML 2009处理的，其中PML 2009是PML 2007的高版本。
    
    PML 2007处理上述标记，并忽略 `ext` 块，因为它不理解这个扩展。然而，这个块被保留供任何其他能够理解它的消费者/生产者使用。
    
    PML 2009处理上述标记，并理解如何处理由 `uri` 指示的层扩展。spLayer扩展被返回，PML 2009处理这个扩展，并负责根据需要写出这个标记的任何更新。例如，层可能从1更改为2。
    
    注意，这个扩展是一个直接扩展，因为层信息与所有其他非视觉属性（如ID、名称和描述）是正交的。
    
    由于本质上是非视觉的，这个扩展中的信息不会直接影响形状的外观。

=== "英文"

    Consider the case in which the notion that each shape can be associated with a given layer, is to be added. The schema for this might look like the following:
    
    ![123](./imgs/Image32210.png)
    
    The extLst block is under the non-visual shape properties (i.e., p:nvSpPr). A uri attribute identifies the extension.
    
    Now consider how this markup is processed by PML 2007 and PML 2009, where PML 2009 is an up-level version of PML 2007.
    
    PML 2007 processes the above markup, and ignores the ext block because it doesn't understand this extension. However, this block is preserved for any other consumer/producer that can understand it.
    
    PML 2009 processes the above markup, and understands how to deal with layer extensions as indicated by the uri. The spLayer extension is returned, PML 2009 processes the extension and is responsible for writing out any updates to this markup, as required. For example, layer might be changed from 1 to 2.
    
    Note that the extension is a straight-up extension in that layer information is orthogonal to all other non-visual properties, such as the ID, name, and description.
    
    Being non-visual in nature, the information in this extension does not directly affect the appearance of the shape.

#### L.7.3.4.2 替代内容块

**AlternateContent Blocks**

=== "中文"
    
    关于这个主题的信息，请参考[ECMA-376-3]。

=== "英文"
    
    For information on this topic, refer to [ECMA-376-3].

[ECMA-376-3]: ../../ecma-part3-refrence.md