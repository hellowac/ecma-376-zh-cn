# 17.5 自定义标记

**Custom Markup**

=== "中文"

    在WordprocessingML文档中，除了ECMA-376规定的演示信息外，还可以提供语义信息。【例如：发票文档可能希望指定特定文字句作为客户名称，以便可以轻松从文档中提取该信息，而无需使用正则表达式匹配或类似方法解析文本。结束示例】
    
    有三种不同形式可将额外标准的语义插入到WordprocessingML文档中，每种形式都有其特定的预期用途：
    
    - 智能标记
    - 自定义XML标记
    - 结构化文档标记（内容控件）
    
    描述定义每种形式的元素和属性的详细条款如下。

=== "英文"
    
    Within a WordprocessingML document, semantic information may be supplied beyond the presentation information specified by ECMA-376. [Example: An invoice document might wish to specify that a particular sentence of text is a customer name, in order for that information to be easily extracted from the document without the need to parse the text using regular expression matching or similar. end example]
    
    There are three distinct forms in which extra-standard semantics can be inserted into a WordprocessingML document, each with their own specific intended usage:
    
    - Smart tags
    - Custom XML markup
    - Structured document tags (content controls)
    
    The elements and attributes which define each of these forms is described in the following clauses.

## TOC

- [17.5 自定义标记](#175-自定义标记)
    - [TOC](#toc)
    - [17.5.1 自定义 XML 和智能标签](#1751-自定义-xml-和智能标签)
        - [17.5.1.1 attr (自定义 XML 属性)](#17511-attr-自定义-xml-属性)
        - [17.5.1.2 attr (智能标签属性)](#17512-attr-智能标签属性)
        - [17.5.1.3 customXml (内联级自定义 XML 元素)](#17513-customxml-内联级自定义-xml-元素)
        - [17.5.1.4 customXml (单元格级自定义 XML 元素)](#17514-customxml-单元格级自定义-xml-元素)
        - [17.5.1.5 customXml (行级自定义 XML 元素)](#17515-customxml-行级自定义-xml-元素)
        - [17.5.1.6 customXml (块级自定义 XML 元素)](#17516-customxml-块级自定义-xml-元素)
        - [17.5.1.7 customXmlPr (自定义 XML 元素属性)](#17517-customxmlpr-自定义-xml-元素属性)
        - [17.5.1.8 placeholder (自定义 XML 元素占位符文本)](#17518-placeholder-自定义-xml-元素占位符文本)
        - [17.5.1.9 smartTag (内联级智能标签)](#17519-smarttag-内联级智能标签)
        - [17.5.1.10 smartTagPr (智能标签属性)](#175110-smarttagpr-智能标签属性)
    - [17.5.2 结构化文档标签](#1752-结构化文档标签)
        - [17.5.2.1 alias (友好名称)](#17521-alias-友好名称)
        - [17.5.2.2 bibliography (参考目录结构化文档标签)](#17522-bibliography-参考目录结构化文档标签)
        - [17.5.2.3 calendar (日期选择器日历类型)](#17523-calendar-日期选择器日历类型)
        - [17.5.2.4 citation (引文结构化文档标签)](#17524-citation-引文结构化文档标签)
        - [17.5.2.5 comboBox (组合框结构化文档标签)](#17525-combobox-组合框结构化文档标签)
        - [17.5.2.6 dataBinding (XML映射)](#17526-databinding-xml映射)
        - [17.5.2.7 date (日期结构化文档标签)](#17527-date-日期结构化文档标签)
        - [17.5.2.8 dateFormat (日期显示水印)](#17528-dateformat-日期显示水印)
        - [17.5.2.9 docPart (文档部件参考)](#17529-docpart-文档部件参考)
        - [17.5.2.10 docPartCategory (文档部件类别过滤器)](#175210-docpartcategory-文档部件类别过滤器)
        - [17.5.2.11 docPartGallery (文档部件图库过滤器)](#175211-docpartgallery-文档部件图库过滤器)
        - [17.5.2.12 docPartList (文档部件图库结构化文档标签)](#175212-docpartlist-文档部件图库结构化文档标签)
        - [17.5.2.13 docPartObj (内置文档部件结构化文档标签)](#175213-docpartobj-内置文档部件结构化文档标签)
        - [17.5.2.14 docPartUnique (内置文档部件)](#175214-docpartunique-内置文档部件)
        - [17.5.2.15 dropDownList (下拉列表结构化文档标签)](#175215-dropdownlist-下拉列表结构化文档标签)
        - [17.5.2.16 equation (方程结构化文档标签)](#175216-equation-方程结构化文档标签)
        - [17.5.2.17 group (分组结构化文档标签)](#175217-group-分组结构化文档标签)
        - [17.5.2.18 id (唯一ID)](#175218-id-唯一id)
        - [17.5.2.19 label (结构化文档标签label)](#175219-label-结构化文档标签label)
        - [17.5.2.20 lid (日期选择器语言 ID)](#175220-lid-日期选择器语言-id)
        - [17.5.2.21 listItem (组合框列表项)](#175221-listitem-组合框列表项)
        - [17.5.2.22 listItem (下拉列表项)](#175222-listitem-下拉列表项)
        - [17.5.2.23 lock (锁定设置)](#175223-lock-锁定设置)
        - [17.5.2.24 picture (图片结构化文档标签)](#175224-picture-图片结构化文档标签)
        - [17.5.2.25 placeholder (结构化文档标签占位符文本)](#175225-placeholder-结构化文档标签占位符文本)
        - [17.5.2.26 richText (富文本结构化文档标签)](#175226-richtext-富文本结构化文档标签)
        - [17.5.2.27 rPr (结构化文档标签内容的运行(run)属性)](#175227-rpr-结构化文档标签内容的运行run属性)
        - [17.5.2.28 rPr (结构化文档标记结束字符运行(run)属性)](#175228-rpr-结构化文档标记结束字符运行run属性)
        - [17.5.2.29 sdt (块级结构化文档标签)](#175229-sdt-块级结构化文档标签)
        - [17.5.2.30 sdt (行级结构化文档标签)](#175230-sdt-行级结构化文档标签)
        - [17.5.2.31 sdt (内联级结构化文档标签)](#175231-sdt-内联级结构化文档标签)
        - [17.5.2.32 sdt (单元格级结构化文档标签)](#175232-sdt-单元格级结构化文档标签)
        - [17.5.2.33 sdtContent (单元格级结构化文档标签内容)](#175233-sdtcontent-单元格级结构化文档标签内容)
        - [17.5.2.34 sdtContent (块级结构化文档标签内容)](#175234-sdtcontent-块级结构化文档标签内容)
        - [17.5.2.35 sdtContent (行级结构化文档标签内容)](#175235-sdtcontent-行级结构化文档标签内容)
        - [17.5.2.36 sdtContent (内联级结构化文档标签内容)](#175236-sdtcontent-内联级结构化文档标签内容)
        - [17.5.2.37 sdtEndPr (结构化文档标签结束字符属性)](#175237-sdtendpr-结构化文档标签结束字符属性)
        - [17.5.2.38 sdtPr (结构化文档标签属性)](#175238-sdtpr-结构化文档标签属性)
        - [17.5.2.39 showingPlcHdr (当前内容是占位符文本)](#175239-showingplchdr-当前内容是占位符文本)
        - [17.5.2.40 storeMappedDataAs (自定义 XML 数据日期存储格式)](#175240-storemappeddataas-自定义-xml-数据日期存储格式)
        - [17.5.2.41 tabIndex (结构化文档标签导航顺序索引)](#175241-tabindex-结构化文档标签导航顺序索引)
        - [17.5.2.42 tag (程序化标签)](#175242-tag-程序化标签)
        - [17.5.2.43 temporary (编辑内容时删除结构化文档标签)](#175243-temporary-编辑内容时删除结构化文档标签)
        - [17.5.2.44 text (纯文本结构化文档标签)](#175244-text-纯文本结构化文档标签)

## 17.5.1 自定义 XML 和智能标签

**Custom XML and Smart Tags**

=== "中文"
    
    WordprocessingML文档中可以嵌入的第一种额外标准的语义形式由智能标记表示。实现可以建立智能标记集，允许在文档中的任意运行或一组运行周围添加语义标签，以提供有关所含数据类型的信息。
    
    [示例：考虑WordprocessingML文档中以下文本，其中将智能标记放在股票代码“CNTS”周围：
    
    ```text
        This is a stock symbol: CNTS
    ```
    
    该文本将转换为以下WordprocessingML标记：
    
    ```xml 
    <w:p w:rsidR="00672474" w:rsidRDefault="00672474">
        <w:r>
            <w:t xml:space="preserve">This is a stock symbol: </w:t>
        </w:r>
        <w:smartTag w:uri="http://www.example.com"
            w:element="stockticker">
            <w:r>
                <w:t>CNTS</w:t>
            </w:r>
        </w:smartTag>
    </w:p>
    ```
    
    如上所示，智能标记由smartTag元素界定，该元素围绕包含智能标记一部分的运行（或多个运行）。结束示例]
    
    smartTag元素具有两个必需属性：
    
    - uri属性用于指定术语所属的命名空间，即词汇或分类方案。[示例：在上面的示例中，智能标记指定了http://www.example.com以标识分类方案。结束示例]
    - element属性与uri属性结合使用，指定此智能标记的分类。[示例：在上面的示例中，智能标记从已识别的命名空间中指定分类术语stockticker。结束示例]
    
    可以嵌入在WordprocessingML文档中的第二种额外标准的语义形式是自定义XML标记。自定义XML标记允许将任何模式语法（XML Schema、NVDL等）中定义的XML元素应用于WordprocessingML文档的内容，位置分为两种类型：围绕一个段落或一组段落（块级别）；或者围绕文档中的任意运行或一组运行（内联级别）以为内容提供语义，这在相关模式定义所定义的上下文和结构中。
    
    自定义XML标记与智能标记的区别在于自定义XML标记基于模式，可以使用attachedSchema元素（[§17.15.1.5]）指定。因此，自定义XML元素可以根据模式进行验证。此外，如下所示，自定义XML标记既可用于块级别，也可用于内联（运行）级别。
    
    [示例：考虑一个简单的XML Schema，定义了两个元素：一个名为invoice的根元素，和一个名为customerName的子元素 - 第一个定义了该文件的内容是一个发票，第二个指定了所包含文本作为客户姓名：
    
    ![123](./imgs/Image8513.png)
    
    该输出将转换为以下WordprocessingML标记：
    
    ```xml
    <w:customXml w:uri="http://www.example.com/2006/invoice" w:element="invoice">
        <w:p>
            <w:r>
                <w:t>This is an invoice.</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t xml:space="preserve">And this is a customer name: </w:t>
            </w:r>
            <w:customXml w:uri="http://www.example.com/2006/invoice"
                w:element="customerName">
            <w:r>
                <w:t>Tristan Davis</w:t>
            </w:r>
            </w:customXml>
        </w:p>
    </w:customXml>
    ```
    
    如上所示，来自所提供XML模式的每个XML元素在文档输出中表示为一个customXml元素。结束示例]
    
    文档中的自定义XML元素具有两个必需属性。
    
    - 第一个是uri属性，其内容指定文档中自定义XML元素的命名空间。在上面的示例中，每个元素都属于http://www.example.com/2006/invoice命名空间。
    - 第二个是element属性，其内容指定文档中此位置的自定义XML元素的名称。在上面的示例中，根元素称为invoice，子元素称为customerName。
    
    除了上述规定的必需信息外，自定义XML元素还可以在元素上指定任意数量的属性（如在相关XML Schema中指定）。要添加此信息，customXmlPr（自定义XML元素上的属性）指定一个或多个attr元素。
    
    [示例：使用上面的示例，我们可以给customerName元素添加一个type属性，如下所示：
    
    ```xml
    <w:customXml w:uri="http://www.example.com/2006/invoice"
        w:element="customerName">
        <w:customXmlPr>
            <w:attr w:uri="http://www.example.com/2006/invoice" w:name="type"
                w:val="individual"/>
        </w:customXmlPr>
        <w:r>
            <w:t>Tristan Davis</w:t>
        </w:r>
    </w:customXml>
    ```
    
    如上所示，生成的XML简单地添加了一个attr元素，该元素指定了自定义XML元素的属性。结束示例]…

=== "英文"
    
    The first form of extra-standard semantics that can be embedded in a WordprocessingML document is represented by smart tags. Implementations can establish sets of smart tags that allow semantic labels to be added around an arbitrary run or set of runs within a document to provide information about the type of data contained within.
    
    [Example: Consider the following text in a WordprocessingML document, with a smart tag around the stock symbol 'CNTS':
    
    ```text
        This is a stock symbol: CNTS
    ```
    
    This text would translate to the following WordprocessingML markup:
    
    ```xml 
    <w:p w:rsidR="00672474" w:rsidRDefault="00672474">
        <w:r>
            <w:t xml:space="preserve">This is a stock symbol: </w:t>
        </w:r>
        <w:smartTag w:uri="http://www.example.com"
            w:element="stockticker">
            <w:r>
                <w:t>CNTS</w:t>
            </w:r>
        </w:smartTag>
    </w:p>
    ```
    
    As shown above, the smart tag is delimited by the smartTag element, which surrounds the run (or runs) which contain the text which is part of the smart tag. end example]
    
    The smartTag element has two required attributes:
    
    - The uri attribute is used to specify the namespace, in terms of a vocabulary or classification scheme, of which the term specified for this smart tag is a member. [Example: In the above example, the smart tag specifies http://www.example.com to identify the classification scheme. end example]
    - The element attribute, in combination with the uri attribute, specifies the classification for this smart tag. [Example: In the above example, the smart tag specifies the classification term stockticker from the identified namespace. end example]
    
    The second form of extra-standard semantics that can be embedded in a WordprocessingML document is custom XML markup. Custom XML markup allows the application of the XML elements defined in any schema syntax (XML Schema, NVDL, etc.) to be applied to the contents of a WordprocessingML document in two types of location: around a paragraph or set of paragraphs (at the block level); or around an arbitrary run or set of runs within a document (at the inline level) to provide semantics to that content within the context and structures defined by the associated schema definition.
    
    The distinction between custom XML markup and smart tags is that custom XML markup is based on a schema, which may be specified using the attachedSchema element ([§17.15.1.5]). As a result, the custom XML elements can be validated against the schema. Also, as shown below, custom XML markup can be used at the block-level as well as on the inline (run) level.
    
    [Example: Consider a simple XML Schema which defines two elements: a root element of invoice, and a child element of customerName - the first defining that this file's contents are an invoice, and the second specifying that the enclosed text as a customer's name:

    ![123](./imgs/Image8513.png)
    
    This output would translate to the following WordprocessingML markup:
    
    ```xml
    <w:customXml w:uri="http://www.example.com/2006/invoice" w:element="invoice">
        <w:p>
            <w:r>
                <w:t>This is an invoice.</w:t>
            </w:r>
        </w:p>
        <w:p>
            <w:r>
                <w:t xml:space="preserve">And this is a customer name: </w:t>
            </w:r>
            <w:customXml w:uri="http://www.example.com/2006/invoice"
                w:element="customerName">
            <w:r>
                <w:t>Tristan Davis</w:t>
            </w:r>
            </w:customXml>
        </w:p>
    </w:customXml>
    ```
    
    As shown above, each of the XML elements from the supplied XML schema is represented within the document output as a customXml element. end example]
    
    A custom XML element in a document has two required attributes.
    
    - The first is the uri attribute, whose contents specify the namespace of the custom XML element in the document. In the example above, the elements each belong to the http://www.example.com/2006/invoice namespace.
    - The second is the element attribute, whose contents specify the name of the custom XML element at this location in the document. In the example above, the root element is called invoice and the child element is called customerName.
    
    As well as the required information specified above, custom XML elements can also specify any number of attributes (as specified in the associated XML Schema) on the element. To add this information, the customXmlPr (properties on the custom XML element) specify one or more attr elements.
    
    [Example: Using the example above, we can add a type attribute to the customerName element as follows:
    
    ```xml
    <w:customXml w:uri="http://www.example.com/2006/invoice"
        w:element="customerName">
        <w:customXmlPr>
            <w:attr w:uri="http://www.example.com/2006/invoice" w:name="type"
                w:val="individual"/>
        </w:customXmlPr>
        <w:r>
            <w:t>Tristan Davis</w:t>
        </w:r>
    </w:customXml>
    ```
    
    The resulting XML, as seen above, simply adds an attr element which specifies the attribute for the custom XML element. end example]…


### 17.5.1.1 attr (自定义 XML 属性)

**attr (Custom XML Attribute)**

=== "中文"

    此元素指定一个自定义XML属性，该属性应位于通过customXml元素（[§17.5.1.4]；[§17.5.1.5]；[§17.5.1.3]；[§17.5.1.6]）指定的父自定义XML元素上。uri属性可以指定自定义XML属性的命名空间，而name属性应指定自定义XML属性的本地名称。对于任何一组兄弟attr元素，所有的命名空间和本地名称对都应是唯一的。
    
    [示例：考虑一个具有以下属性的自定义XML元素：
    
    ```xml
    <w:customXmlPr>
        <w:attr w:name="companyName" … />
        <w:attr w:name="companySymbol" … />
    </w:customXmlPr>
    ```
    
    这组自定义XML属性指定父自定义XML元素必须有两个与之关联的属性，第一个名称为companyName，第二个名称为companySymbol。结束示例]
    
    ??? abstract "属性"
    
        **name**（名称）
        
        :   指定当前自定义XML属性或智能标签属性的名称。
            
            [示例：考虑一个必须名为companyName的自定义XML属性。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXmlPr>
                <w:attr w:name="companyName" … />
            </w:customXmlPr>
            ```
            
            name属性指定此属性的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
    
        **uri**（命名空间）
        
        :   指定当前自定义XML属性或智能标签属性的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个必须具有命名空间URI为http://schemas.openxmlformats.org/2006/example的智能标签属性。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            ```
            
            uri属性指定此属性的命名空间必须为http://schemas.openxmlformats.org/2006/example。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
        
        **val**（值）
        
        :   指定当前自定义XML属性或智能标签属性的值。
        
            [示例：考虑一个必须具有值为propertyValue的智能标签属性。
            
            此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:smartTagPr>
                <w:attr … w:val="propertyValue" />
            </w:smartTagPr>
            ```
            
            val属性指定此属性的值必须为propertyValue。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Attr) is located in §A.1. end note]

=== "英文"

    This element specifies a custom XML attribute which shall be located on the parent custom XML element specified via the customXml element ([§17.5.1.4];[§17.5.1.5];[§17.5.1.3]; [§17.5.1.6]). The uri attribute can specify the Namespace of the custom XML attribute, and the name attribute shall specify the local name of the custom XML attribute. For any set of sibling attr elements, all the pairs of Namespace and local name shall be distinct.

    [Example: Consider a custom XML element with the following properties:
    
    ```xml
    <w:customXmlPr>
        <w:attr w:name="companyName" … />
        <w:attr w:name="companySymbol" … />
    </w:customXmPr>
    ```
    
    This set of custom XML properties specifies that the parent custom XML element must have two attributes associated with it, he first with a name of companyName, and the second with a name of companySymbol. end example]
    
    ??? abstract "Attributes"
    
        **name** (Name)
    
        :   Specifies the name of the current custom XML attribute or smart tag property.
            
            [Example: Consider a custom XML attribute which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXmlPr>
                <w:attr w:name="companyName" … />
            </w:customXmlPr>
            ```
            
            The name attribute specifies that the name for this property must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        uri (Namespace)
    
        :   Specifies the namespace URI of the current custom XML attribute or smart tag property.
    
            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a smart tag property which must have a namespace URI of http://schemas.openxmlformats.org/2006/example. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            
            The uri attribute specifies that the namespace for this property must be http://schemas.openxmlformats.org/2006/example. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        **val** (Value)
    
        :   Specifies the value of the current custom XML attribute or smart tag property.
    
            [Example: Consider a smart tag property which must have a value of propertyValue.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:smartTagPr>
                <w:attr … w:val="propertyValue" />
            </w:smartTagPr>
            ```
            
            The val attribute specifies that the value for this property must be propertyValue. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Attr) is located in §A.1. end note]

### 17.5.1.2 attr (智能标签属性)

**attr (Smart Tag Property)**

=== "中文"

    此元素指定一个单独的智能标签属性，该属性应位于通过smartTag元素（[§17.5.1.9]）指定的父智能标签上。此元素的属性应用于指定智能标签属性的内容。
    
    [示例：考虑一个具有以下属性的智能标签：
    
    ```xml
    <w:smartTagPr>
        <w:attr w:name="attributeOne" … />
        <w:attr w:name="attributeTwo" … />
    </w:smartTagPr>
    ```
    
    此属性包指定父智能标签必须具有两个与之关联的属性，第一个名称为attributeOne，第二个名称为attributeTwo。结束示例]。
    
    ??? abstract "属性"
    
        **name**（名称）
        
        :   指定当前自定义XML属性或智能标签属性的名称。
            
            [示例：考虑一个必须名为companyName的自定义XML属性。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXmlPr>
                <w:attr w:name="companyName" … />
            </w:customXmlPr>
            ```
            
            name属性指定此属性的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
    
        **uri**（命名空间）
        
        :   指定当前自定义XML属性或智能标签属性的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个必须具有命名空间URI为http://schemas.openxmlformats.org/2006/example的智能标签属性。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            ```
            
            uri属性指定此属性的命名空间必须为http://schemas.openxmlformats.org/2006/example。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
        
        **val**（值）
        
        :   指定当前自定义XML属性或智能标签属性的值。
        
            [示例：考虑一个必须具有值为propertyValue的智能标签属性。
            
            此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:smartTagPr>
                <w:attr … w:val="propertyValue" />
            </w:smartTagPr>
            ```
            
            val属性指定此属性的值必须为propertyValue。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Attr) is located in §A.1. end note]

=== "英文"

    This element specifies a single smart tag property which shall be located on the parent smart tag, specified via the smartTag element ([§17.5.1.9]). The attributes on this element shall be used to specify the contents of smart tag property.

    [Example: Consider a smart tag with the following properties:
    
    ```xml
    <w:smartTagPr>
    <w:attr w:name="attributeOne" … />
    <w:attr w:name="attributeTwo" … />
    </w:smartTagPr>
    ```
    
    This property bag specifies that the parent smart tag must have two properties associated with it, the first with a name of attributeOne, and the second with a name of attributeTwo. end example].
    
    ??? abstract "Attributes"
    
        **name** (Name)
    
        :   Specifies the name of the current custom XML attribute or smart tag property.
            
            [Example: Consider a custom XML attribute which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXmlPr>
                <w:attr w:name="companyName" … />
            </w:customXmlPr>
            ```
            
            The name attribute specifies that the name for this property must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        uri (Namespace)
    
        :   Specifies the namespace URI of the current custom XML attribute or smart tag property.
    
            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a smart tag property which must have a namespace URI of http://schemas.openxmlformats.org/2006/example. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            
            The uri attribute specifies that the namespace for this property must be http://schemas.openxmlformats.org/2006/example. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        **val** (Value)
    
        :   Specifies the value of the current custom XML attribute or smart tag property.
    
            [Example: Consider a smart tag property which must have a value of propertyValue.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:smartTagPr>
                <w:attr … w:val="propertyValue" />
            </w:smartTagPr>
            ```
            
            The val attribute specifies that the value for this property must be propertyValue. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Attr) is located in §A.1. end note]

### 17.5.1.3 customXml (内联级自定义 XML 元素)

**customXml (Inline-Level Custom XML Element)**

=== "中文"

    此元素指定一个自定义XML元素在一个段落内围绕一个或多个内联级结构（文本运行、图像、字段等）的存在。此元素的属性用于指定当前自定义XML元素的名称和命名空间URI。
    
    [示例：考虑一个名称为firstName的自定义XML元素，它必须位于一个WordprocessingML文档中的两个文本运行周围。此需求在WordprocessingML中如下指定：
    
    ```xml
    <w:p>
        <w:customXml w:element="firstName" … >
            <w:r>
                …
            </w:r>
            <w:r>
                …
            </w:r>
        </w:customXml>
        …
    </w:p>
    ```
    
    customXml元素指定自定义XML元素的名称为firstName，并且自定义XML元素包含两个文本运行（它是一个内联级元素）。结束示例]
    
    ??? abstract "属性"
    
        **element**（元素名称）
        
        :   指定文档中当前自定义XML元素或智能标签的名称。
        
            [示例：考虑一个名称必须为companyName的自定义XML元素。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            element属性指定此元素的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
        
        **uri**（自定义XML标记命名空间）
        
        :   指定当前自定义XML元素或智能标签的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个命名空间URI必须为urn:customXmlExample的自定义XML元素。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            ```
            
            uri属性指定此元素的命名空间必须为urn:customXmlExample。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlRun) is located in §A.1. end note]

=== "英文"

    This element specifies the presence of a custom XML element around one or more inline level structures (runs, images, fields, etc.) within a paragraph. The attributes on this element shall be used to specify the name and namespace URI of the current custom XML element.
    
    [Example: Consider a custom XML element with the name firstName that must be located around a two text runs in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:

    ```xml
    <w:p>
        <w:customXml w:element="firstName" … >
            <w:r>
                …
            </w:r>
            <w:r>
                …
            </w:r>
        </w:customXml>
        …
    </w:p>
    ```
    
    The customXml element specifies that the name of the custom XML element is firstName, and the custom XML element contains a two text runs (it is an inline-level element). end example]
    
    ??? abstract "Attributes"
    
        **element** (Element name)
    
        :   Specifies the name of the current custom XML element or smart tag within the document.

            [Example: Consider a custom XML element which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            The element attribute specifies that the name for this element must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        **uri** (Custom XML Markup Namespace)
    
        :   Specifies the namespace URI of the current custom XML element or smart tag.

            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a custom XML element which must have a namespace URI of urn:customXmlExample. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:smartTagPr>
                <w:attr w:uri="http://schemas.openxmlformats.org/2006/example" … />
            </w:smartTagPr>
            
            The uri attribute specifies that the namespace for this element must be urn:customXmlExample. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlRun) is located in §A.1. end note]

### 17.5.1.4 customXml (单元格级自定义 XML 元素)

**customXml (Cell-Level Custom XML Element)**

=== "中文"

    此元素指定在单个表格单元格周围存在一个自定义XML元素。此元素的属性用于指定当前自定义XML元素的名称和命名空间URI。
    
    [示例：考虑一个名称为company的自定义XML元素，它必须位于一个WordprocessingML文档中的单个表格单元格周围。此需求在WordprocessingML中如下指定：
    
    ```xml
    <w:tr>
        <w:customXml w:element="company" … >
            <w:tc>
                …
            </w:tc>
        </w:customXml>
        …
    </w:tr>
    ```
    
    customXml元素指定自定义XML元素的名称为company，并且自定义XML元素包含一个表格单元格（它是一个单元格级别的元素）。结束示例]
    
    ??? abstract "属性"
    
        **element**（自定义XML元素名称）
        
        :   指定文档中当前自定义XML元素或智能标签的名称。
        
            [示例：考虑一个名称必须为companyName的自定义XML元素。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            element属性指定此元素的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
        
        **uri**（自定义XML元素命名空间）
        
        :   指定当前自定义XML元素或智能标签的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个命名空间URI必须为urn:customXmlExample的自定义XML元素。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
                …
            </w:customXml>
            ```
            
            uri属性指定此元素的命名空间必须为urn:customXmlExample。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlCell) is located in §A.1. end note]

=== "英文"

    This element specifies the presence of a custom XML element around a single table cell. The attributes on this element shall be used to specify the name and namespace URI of the current custom XML element.
    
    [Example: Consider a custom XML element with the name company that must be located around a single table cell in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:

    ```xml
    <w:tr>
        <w:customXml w:element="company" … >
            <w:tc>
                …
            </w:tc>
        </w:customXml>
        …
    </w:tr>
    ```
    
    The customXml element specifies that the name of the custom XML element is company, and the custom XML element contains a single table cell (it is a cell-level element). end example]
    
    ??? abstract "Attributes"
    
        **element** (Custom XML Element Name)
    
        :   Specifies the name of the current custom XML element or smart tag within the document.

            [Example: Consider a custom XML element which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            The element attribute specifies that the name for this element must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        **uri** (Custom XML Element Namespace)
    
        :   Specifies the namespace URI of the current custom XML element or smart tag.

            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a custom XML element which must have a namespace URI of urn:customXmlExample. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
            …
            </w:customXml>
            ```
            
            The uri attribute specifies that the namespace for this element must be urn:customXmlExample. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlCell) is located in §A.1. end note]

### 17.5.1.5 customXml (行级自定义 XML 元素)

**customXml (Row-Level Custom XML Element)**

=== "中文"

    此元素指定在单个表格行周围存在一个自定义XML元素。此元素的属性用于指定当前自定义XML元素的名称和命名空间URI。
    
    [示例：考虑一个名称为invoiceItem的自定义XML元素，它必须位于一个WordprocessingML文档中的单个表格行周围。此需求在WordprocessingML中如下指定：
    
    ```xml
    <w:tbl>
        <w:customXml w:element="invoiceItem" … >
            <w:tr>
                …
            </w:tr>
        </w:customXml>
        …
    </w:tbl>
    ```
    
    customXml元素指定自定义XML元素的名称为invoiceItem，并且自定义XML元素包含一个表格行（它是一个行级别的元素）。结束示例]
    
    ??? abstract "属性"
    
        **element**（自定义XML元素名称）
        
        :   指定文档中当前自定义XML元素或智能标签的名称。
        
            [示例：考虑一个名称必须为companyName的自定义XML元素。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            element属性指定此元素的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
        
        **uri**（自定义XML元素命名空间）
        
        :   指定当前自定义XML元素或智能标签的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个命名空间URI必须为urn:customXmlExample的自定义XML元素。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
                …
            </w:customXml>
            ```
            
            uri属性指定此元素的命名空间必须为urn:customXmlExample。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlRow) is located in §A.1. end note]

=== "英文"

    This element specifies the presence of a custom XML element around a single table row. The attributes on this element shall be used to specify the name and namespace URI of the current custom XML element.
    
    [Example: Consider a custom XML element with the name invoiceItem that must be located around a single table row in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:

    ```xml
    <w:tbl>
        <w:customXml w:element="invoiceItem" … >
            <w:tr>
                …
            </w:tr>
        </w:customXml>
        …
    </w:tbl>
    ```
    
    The customXml element specifies that the name of the custom XML element is invoiceItem, and the custom XML element contains a single table row (it is a row-level element). end example]
    
    ??? abstract "Attributes"
    
        **element** (Custom XML Element Name)
    
        :   Specifies the name of the current custom XML element or smart tag within the document.

            [Example: Consider a custom XML element which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            The element attribute specifies that the name for this element must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        **uri** (Custom XML Element Namespace)
    
        :   Specifies the namespace URI of the current custom XML element or smart tag.

            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a custom XML element which must have a namespace URI of urn:customXmlExample. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
            …
            </w:customXml>
            ```
            
            The uri attribute specifies that the namespace for this element must be urn:customXmlExample. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlRow) is located in §A.1. end note]

### 17.5.1.6 customXml (块级自定义 XML 元素)

**customXml (Block-Level Custom XML Element)**

=== "中文"

    此元素指定在一个或多个块级结构（段落、表格等）周围存在一个自定义XML元素。此元素的属性用于指定当前自定义XML元素的名称和命名空间URI。
    
    [示例：考虑一个名称为address的自定义XML元素，它必须位于一个WordprocessingML文档中的单个段落周围。此需求在WordprocessingML中如下指定：
    
    ```xml
    <w:body>
        <w:customXml w:element="address" … >
            <w:p>
                …
            </w:p>
        </w:customXml>
        …
    </w:body>
    ```
    
    customXml元素指定自定义XML元素的名称为address，并且自定义XML元素包含一个段落（它是一个块级元素）。结束示例]
    
    ??? abstract "属性"
    
        **element**（自定义XML元素名称）
        
        :   指定文档中当前自定义XML元素或智能标签的名称。
                        
            [示例：考虑一个名称必须为companyName的自定义XML元素。
            
            这种需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            element属性指定此元素的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
        
        **uri**（自定义XML元素命名空间）
        
        :   指定当前自定义XML元素或智能标签的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个命名空间URI必须为urn:customXmlExample的自定义XML元素。此需求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
                …
            </w:customXml>
            ```
            
            uri属性指定此元素的命名空间必须为urn:customXmlExample。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlBlock) is located in §A.1. end note]

=== "英文"

    This element specifies the presence of a custom XML element around one or more block level structures (paragraphs, tables, etc.). The attributes on this element shall be used to specify the name and namespace URI of the current custom XML element.
        
    [Example: Consider a custom XML element with the name address that must be located around a single paragraph in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:

    ```xml
    <w:body>
        <w:customXml w:element="address" … >
            <w:p>
                …
            </w:p>
        </w:customXml>
        …
    </w:body>
    ```
    
    The customXml element specifies that the name of the custom XML element is address, and the custom XML element contains a single paragraph (it is a block-level element). end example]
    
    ??? abstract "Attributes"
    
        **element** (Custom XML Element Name)
    
        :   Specifies the name of the current custom XML element or smart tag within the document.
                    
            [Example: Consider a custom XML element which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            The element attribute specifies that the name for this element must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        **uri** (Custom XML Element Namespace)
    
        :   Specifies the namespace URI of the current custom XML element or smart tag.

            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a custom XML element which must have a namespace URI of urn:customXmlExample. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
            …
            </w:customXml>
            ```
            
            The uri attribute specifies that the namespace for this element must be urn:customXmlExample. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlBlock) is located in §A.1. end note]

### 17.5.1.7 customXmlPr (自定义 XML 元素属性)

**customXmlPr (Custom XML Element Properties)**

=== "中文"

    此元素指定将应用于父自定义XML元素的一组属性。
    
    [示例：考虑一个具有以下指定属性的自定义XML元素：
    
    ```xml
    <w:customXmlPr>
        <w:placeholder w:val="[Fill in your name]"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:customXmlPr>
    ```
    
    这个自定义XML元素指定了两个属性：通过placeholder元素（[§17.5.1.8]）设置的占位符文本和通过attr元素（[§17.5.1.1]）设置的单个自定义XML属性。结束示例]

    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlPr) is located in §A.1. end note]

=== "英文"

    This element specifies the set of properties which shall be applied to the parent custom XML element.

    [Example: Consider a custom XML element with the following properties specified:
    
    ```xml
    <w:customXmlPr>
        <w:placeholder w:val="[Fill in your name]"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:customXmlPr>
    ```
    
    This custom XML element specifies two properties: the presence of placeholder text via the placeholder element ([§17.5.1.8]) and a single custom XML attribute via the attr element ([§17.5.1.1]). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomXmlPr) is located in §A.1. end note]

### 17.5.1.8 placeholder (自定义 XML 元素占位符文本)

**placeholder (Custom XML Element Placeholder Text)**

=== "中文"

    此元素指定占位符文本，当此自定义XML元素的内容为空时（即当前自定义XML元素内没有文本运行时），将显示该占位符文本。如果此自定义XML元素确实包含运行内容，则不会显示此文本。
    
    val属性存储将作为占位符文本显示的字符串。此字符串可以以宿主应用程序所需的任何字体和大小显示。
    
    [示例：考虑一个具有以下指定属性的自定义XML元素：
    
    ```xml
    <w:customXmlPr>
        <w:placeholder w:val="[Fill in your name]"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:customXmlPr>
    ```
    
    placeholder元素指定，当父自定义XML元素内没有运行内容时，该自定义XML元素必须显示文本内容[Fill in your name]。例如，如果自定义XML元素如下指定：
    
    ```xml
    <w:customXml>
        <w:customXmlPr>
            <w:placeholder w:val="[Fill in your name]"/>
        </w:customXmlPr>
        <w:p/>
    </w:customXml>
    ```
    
    此自定义XML元素没有运行内容，占位符文本将被显示。然而，如果存在运行内容，如下所示：
    
    ```xml
    <w:customXml>
        <w:customXmlPr>
            <w:placeholder w:val="[Fill in your name]"/>
        </w:customXmlPr>
        <w:p>
            <w:r>
                <w:t>Name</w:t>
            </w:r>
        </w:p>
    </w:customXml>
    ```
    
    此自定义XML元素现在包含运行内容，不会显示占位符文本。结束示例]
    
    ??? abstract "属性"
    
        **val** (字符串值)
        
        :   指定其内容包含一个字符串。
        
            该字符串的内容根据父XML元素的上下文进行解释。
        
            [示例：考虑以下WordprocessingML片段：
            
            ```xml
            <w:pPr>
            <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val属性的值是关联段落样式的styleId的ID。
            
            然而，考虑以下片段：
            
            ```xml
            <w:sdtPr>
            <w:alias w:val="SDT Title Example" />
            …
            </w:sdtPr>
            ```
            
            在这种情况下，val属性中的字符串是最近的祖先结构化文档标签的标题。在每种情况下，该值都是在父元素的上下文中解释的。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"

    This element specifies the placeholder text which shall be displayed in place of this custom XML element when the contents of this custom XML markup are empty (i.e. there are no runs of text within the current custom XML element). If this custom XML element does contain run content, then this text shall not be displayed.
    
    The val attribute stores the string of text which shall be displayed as the placeholder text. This string can be displayed in any font face/size desired by the hosting application.
    
    [Example: Consider a custom XML element with the following properties specified:
    
    ```xml
    <w:customXmlPr>
        <w:placeholder w:val="[Fill in your name]"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:customXmlPr>
    ```
    
    The placeholder element specifies that this custom XML element must display the text contents [Fill in your name] whenever there is no run content within the parent custom XML element. For example, if the custom XML element was specified as follows:
    
    
    ```xml
    <w:customXml>
        <w:customXmlPr>
            <w:placeholder w:val="[Fill in your name]"/>
        </w:customXmlPr>
        <w:p/>
    </w:customXml>
    ```
    
    
    This custom XML element has no run content and the placeholder text would be displayed. However, if there is run content, as follows:
    
    
    ```xml
    <w:customXml>
        <w:customXmlPr>
            <w:placeholder w:val="[Fill in your name]"/>
        </w:customXmlPr>
        <w:p>
            <w:r>
                <w:t>Name</w:t>
            </w:r>
        </w:p>
    </w:customXml>
    ```
    
    
    This custom XML element now contains run content, and the placeholder text must not be displayed. end example]
    
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

### 17.5.1.9 smartTag (内联级智能标签)

**smartTag (Inline-Level Smart Tag)**

=== "中文"

    此元素指定在段落内的一个或多个内联结构（文本运行、图像、字段等）周围存在一个智能标签。此元素的属性用于指定当前智能标签的名称和命名空间URI。
    
    [示例：考虑一个名称为firstName的智能标签，必须位于WordprocessingML文档中的两个文本运行周围。此需求在WordprocessingML中如下指定：
    
    ```xml
    <w:p>
        <w:smartTag w:element="firstName" … >
            <w:r>
                …
            </w:r>
            <w:r>
                …
            </w:r>
        </w:smartTag>
        …
    </w:p>
    ```
    
    smartTag元素指定智能标签的名称为firstName，并且该智能标签包含两个文本运行（它是一个内联级别的智能标签）。结束示例]
    
    ??? abstract "属性"
    
        **element**（智能标签名称）
        
        :   指定文档中当前自定义XML元素或智能标签的名称。
        
            [示例：考虑一个必须具有名称为companyName的自定义XML元素。
            
            这种要求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            element属性指定此元素的名称必须为companyName。结束示例]
            
            此属性的可能值由ST_XmlName简单类型定义（[§22.9.2.21]）。
        
        **uri**（智能标签命名空间）
        
        :   指定当前自定义XML元素或智能标签的命名空间URI。
        
            如果省略此属性，则假定URI为空（没有关联的URI）。
            
            [示例：考虑一个必须具有命名空间URI为urn:customXmlExample的自定义XML元素。
            
            这种要求可以使用以下WordprocessingML指定：
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
                …
            </w:customXml>
            ```
            
            uri属性指定此元素的命名空间必须为urn:customXmlExample。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_SmartTagRun) is located in §A.1. end note]

=== "英文"

    This element specifies the presence of a smart tag around one or more inline structures (runs, images, fields, etc.) within a paragraph. The attributes on this element shall be used to specify the name and namespace URI of the current smart tag.
    
    [Example: Consider a smart tag with the name firstName that must be located around a two text runs in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:p>
        <w:smartTag w:element="firstName" … >
            <w:r>
                …
            </w:r>
            <w:r>
                …
            </w:r>
        </w:smartTag>
        …
    </w:p>
    ```
    
    The smartTag element specifies that the name of the smart tag is firstName, and the smart tag contains a two
    text runs (it is an inline-level smart tag). end example]
    
    ??? abstract "Attributes"
    
        **element** (Smart Tag Name)
    
        :   Specifies the name of the current custom XML element or smart tag within the document.
    
            [Example: Consider a custom XML element which must have a name of companyName.
            
            This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml w:element="companyName" … >
                …
            </w:customXml>
            ```
            
            The element attribute specifies that the name for this element must be companyName. end example]
            
            The possible values for this attribute are defined by the ST_XmlName simple type ([§22.9.2.21]).
    
        **uri** (Smart Tag Namespace)
    
        :   Specifies the namespace URI of the current custom XML element or smart tag.
    
            If this attribute is omitted, the URI shall be assumed to be null (no associated URI).
            
            [Example: Consider a custom XML element which must have a namespace URI of urn:customXmlExample. This requirement would be specified using the following WordprocessingML:
            
            ```xml
            <w:customXml … w:uri="urn:customXmlExample" >
                …
            </w:customXml>
            ```
            
            The uri attribute specifies that the namespace for this element must be urn:customXmlExample. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_SmartTagRun) is located in §A.1. end note]


### 17.5.1.10 smartTagPr (智能标签属性)

**smartTagPr (Smart Tag Properties)**

=== "中文"

    该元素指定应用于父智能标签的属性集合。
    
    [示例：考虑一个具有以下属性的智能标签：
    
    ```xml
    <w:smartTagPr>
        <w:attr w:name="date" w:val="01/01/2006"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:smartTagPr>
    ```
    
    该智能标签指定了两个属性：通过attr元素（[§17.5.1.2]）指定的两个智能标签属性。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SmartTagPr) is located in §A.1. end note]

=== "英文"

    This element specifies the set of properties which shall be applied to the parent smart tag.

    [Example: Consider a smart tag with the following properties specified:
    
    ```xml
    <w:smartTagPr>
        <w:attr w:name="date" w:val="01/01/2006"/>
        <w:attr w:name="status" w:val="draft"/>
    </w:smartTagPr>
    ```
    
    This smart tag specifies two properties: the presence of two smart tag properties via the attr element ([§17.5.1.2]). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SmartTagPr) is located in §A.1. end note]


## 17.5.2 结构化文档标签

**Structured Document Tags**

=== "中文"
        
    WordprocessingML文档中可以嵌入的最终形式的额外标准语义由结构化文档标记（SDTs）表示。
    
    如上所示，智能标记和自定义XML标记各自提供了一种将额外标准语义嵌入文档的方法：智能标记通过为文档中的运行或一组运行提供基本的命名空间/名称的能力；自定义XML标记通过使用任何XML Schema文件指定的XML元素和属性为文档打标签。
    
    然而，尽管这些技术各自提供了添加所需语义信息的方式，但它们都没有提供一种影响文档内部呈现或交互的方式。为了弥合这两个领域，结构化文档标记允许同时指定额外标准语义以及影响文档中数据呈现的能力。
    
    这意味着实现可以定义标记的语义和上下文，然后使用丰富的预定义属性来定义其在WordprocessingML文档呈现中的行为和外观。
    
    ![123](./imgs/Image8573.png)
    
    [示例：考虑一个应该标记为“生日”的区域，用户可以在文档中输入其出生日期。理想情况下，该区域还应使用日期选择器，以允许用户从日历中选择日期：
    
    以下内容将使用以下WordprocessingML指定：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:alias w:val="Birthday"/>
            <w:id w:val="8775518"/>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22479095"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:date>
                <w:dateFormat w:val="M/d/yyyy"/>
                <w:lid w:val="EN-US"/>
            </w:date>
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:rPr>
                        <w:rStyle w:val="PlaceholderText"/>
                    </w:rPr>
                    <w:t>Click here to enter a date…</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    ```
    
    结束示例]
    
    如上所示，WordprocessingML文件中的每个结构化文档标记都使用sdt元素表示。
    
    在结构化文档标记内部，有两个子元素包含此SDT的定义和内容。第一个是sdtPr元素，它包含为此结构化文档标记指定的一组属性。第二个是sdtContent元素，它包含所有包含在此结构化文档标记中的内容。

=== "英文"
    
    The final form of extra-standard semantics that can be embedded in a WordprocessingML document is represented by structured document tags (SDTs).
    
    As shown above, smart tags and custom XML markup each provide a facility for embedding extra-standard semantics into the document: smart tags, via the ability to provide a basic namespace/name for a run or set of runs within a documents; and custom XML markup, via the ability to tag the document with XML elements and attributes specified by any XML Schema file.
    
    However, each of these techniques, while they each provide a way to add the desired semantic information, does not provide a way to affect the presentation or interaction within the document. To bridge these two worlds, structured document tags allow both the specification of extra-standard semantics as well as the ability to influence the presentation of that data in the document.
    
    This means that the implementation can define the semantics and context of the tag, but can then use a rich set of pre-defined properties to define its behavior and appearance within the WordprocessingML document's presentation.
    
    ![123](./imgs/Image8573.png)
    
    [Example: Consider a region which should be tagged with the semantic of "birthday", for the user to enter their date or birth into the document. Ideally, this region would also utilize a date picker to allow the user to enter the date from a calendar:
    
    This content would be specified using the following WordprocessingML:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:alias w:val="Birthday"/>
            <w:id w:val="8775518"/>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22479095"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:date>
                <w:dateFormat w:val="M/d/yyyy"/>
                <w:lid w:val="EN-US"/>
            </w:date>
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:rPr>
                        <w:rStyle w:val="PlaceholderText"/>
                    </w:rPr>
                    <w:t>Click here to enter a date…</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    ```
    
    end example]
    
    As shown above, each of the structured document tags in the WordprocessingML file is represented using the sdt element.
    
    Within a structured document tag, there are two child elements which contain the definition and the content of this SDT. The first of these is the sdtPr element, which contains the set of properties specified for this structured document tag. The second is the sdtContent element, which contains all the content which is contained within this structured document tag.

### 17.5.2.1 alias (友好名称)

**alias (Friendly Name)**

=== "中文"
    
    该元素指定与当前结构化文档标签关联的友好名称。表示友好名称的字符串将存储在此元素的val属性上。
    
    如果省略此元素，则不会将友好名称与给定的结构化文档标签关联起来。
    
    [示例：考虑一个结构化文档标签上的以下属性：
    
    ```xml
    <w:sdtPr>
        <w:alias w:val="Birthday"/>
        …
    </w:sdtPr>
    ```
    
    通过alias元素指定的属性集合说明了最近的祖先结构化文档标签的友好名称必须是Birthday。结束示例]
    
    ??? abstract "属性"
    
        **val**（字符串值）
        
        :   指定其内容包含一个字符串。
        
            此字符串的内容根据父XML元素的上下文进行解释。
            
            [示例：考虑以下WordprocessingML片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val属性的值是关联段落样式的styleId的ID。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val属性中的十进制数是最近的祖先结构化文档标签的标题。在每种情况下，该值都是在父元素的上下文中解释的。结束示例]
            
            此属性的可能值由ST_String简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the friendly name associated with the current structured document tag. The string representing the friendly name shall be stored on this element's val attribute.
    
    If this element is omitted, then no friendly name shall be associated with the given structured document tag.
    
    [Example: Consider the following properties on a structured document tag:
    
    ```xml
    <w:sdtPr>
        <w:alias w:val="Birthday"/>
        …
    </w:sdtPr>
    ```
    
    This set of properties specifies via the alias element that the friendly name for the nearest ancestor structured document tag must be Birthday. end example]
    
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

### 17.5.2.2 bibliography (参考目录结构化文档标签)

**bibliography (Bibliography Structured Document Tag)**

=== "中文"
    
    该元素指定最近的祖先结构化文档标签应为参考文献类型。
    
    该设置不要求或暗示结构化文档标签的内容必须仅包含类型为BIBLIOGRAPHY的字段，它只用于指定结构化文档标签是这种类型，可以由应用程序根据需要使用。
    
    [示例：考虑以下结构化文档标签：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:bibliography/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    该结构化文档标签的属性中的bibliography元素指定了结构化文档标签的类型为参考文献。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be of type bibliography.
    
    This setting does not require or imply that the contents of the structured document tag shall contain only a field of type BIBLIOGRAPHY, it shall only be used to specify that the structured document tag is of this kind, which can be used by an application as desired.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:bibliography/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The bibliography element in this structured document tag's properties specify that the type of structured document tag is bibliography. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

### 17.5.2.3 calendar (日期选择器日历类型)

**calendar (Date Picker Calendar Type)**

=== "中文"
    
    该元素指定了当前日期选择器结构化文档标签应显示的日历，如果有用户界面用于该结构化文档标签。日历信息存储在该元素的val属性中。
    
    如果省略了该元素，则日历将为公历。
    
    [示例：考虑以下结构化文档标签的属性：
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:calendar w:val="gregorian"/>
        </w:date>
    </w:sdtPr>
    ```
    
    calendar元素指定了在文档中可能显示的日历信息必须采用公历格式（gregorian）。结束示例]
    
    
    ??? abstract "Attributes"
    
        **val**（日历类型值）
    
        :   指定一种日历类型，其使用由父 XML 元素确定。
    
            如果省略了此属性，则日历类型应为公历。
    
            [示例：考虑包含结构化文档标签的文档的以下 WordprocessingML：
    
            ```xml
            <w:sdtPr>
                <w:date … >
                    <w:calendar w:val="japan"/>
                </w:date>
            </w:sdtPr>
            ```
    
            日历元素的val属性值为japan，指定应使用日本天皇纪元日历；在此示例中，它用于为日期结构化文档标签显示的日历。结束示例]
    
            此属性的可能值由ST_CalendarType简单类型定义([§22.9.2.1])。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CalendarType) is located in §A.1. end note]

=== "英文"
    
    This element specifies the calendar which shall be displayed for the current date picker structured document tag, if a user interface is present for the structured document tag. The calendar information is stored on this element's val attribute.
    
    If this element is omitted, then the calendar shall be gregorian.
    
    [Example: Consider the following structured document tag properties:
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:calendar w:val="gregorian"/>
        </w:date>
    </w:sdtPr>
    ```
    
    The calendar element specifies that the calendar information for a calendar which might be displayed in the document must be the Gregorian calendar format (gregorian). end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Calendar Type Value)
    
        :   Specifies a type of calendar, the use of which is determined by the parent XML element.
    
            If this attribute is omitted, then the calendar type shall be gregorian.
    
            [Example: Consider the following WordprocessingML for a document containing a structured document tag:
    
            ```xml
            <w:sdtPr>
                <w:date … >
                    <w:calendar w:val="japan"/>
                </w:date>
            </w:sdtPr>
            ```
            
            The val attribute value of japan specifies that the Japanese Emperor Era calendar must be used; in this case, it is used for the calendar displayed for a date structured document tag. end example]
            
            The possible values for this attribute are defined by the ST_CalendarType simple type ([§22.9.2.1]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CalendarType) is located in §A.1. end note]

### 17.5.2.4 citation (引文结构化文档标签)

**citation (Citation Structured Document Tag)**

=== "中文"

    该元素指定了最近的祖先结构化文档标签应为引用类型。
    
    此设置不要求或暗示结构化文档标签的内容必须仅包含类型为引用的字段，它只是用于指定结构化文档标签为此类型，应用程序可根据需要使用。
    
    [示例：考虑以下结构化文档标签：
    
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:citation/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    该结构化文档标签的属性中的citation元素指定了结构化文档标签的类型为引用。结束示例]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]
    
=== "英文"

    This element specifies that the nearest ancestorstructured document tag shall be of type citation.
    
    This setting does not require or imply that the contents of the structured document tag shall contain only a field of type CITATION, it shall only be used to specify that the structured document tag is of this type, which can be used by an application as desired.
    
    [Example: Consider the following structured document tag:
    
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:citation/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    The citation element in this structured document tag's properties specify that the type of structured document tag is citation. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]



### 17.5.2.5 comboBox (组合框结构化文档标签)

**comboBox (Combo Box Structured Document Tag)**

=== "中文"
    
    
    该元素指定最近的祖先结构化文档标签在文档中显示时应为组合框。
    
    此设置指定了此结构化文档标签的行为应如下：
    
    - 此元素的子元素指定应呈现给用户的选项
    - 应用于此结构化文档标签内容的任何部分的格式设置应适用于其整个内容
    
    此外，结构化文档标签应满足以下限制，否则文档将被视为不符合规范：
    
    - 内容应仅包含单个运行（一个格式属性集）
    - 内容不得包含多个段落或表格单元格，不得包含表行或表
    
    [示例：考虑以下结构化文档标签：
    
    
    ```xml
    
    <w:sdt>
        <w:sdtPr>
            …
            <w:comboBox>
                …
            </w:comboBox>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    该结构化文档标签的comboBox元素指定了结构化文档标签的类型为组合框。结束示例]
    
    
    ??? abstract "属性"
    
        **lastValue** (组合框上次保存的值)
        
        :   指定与当前组合框结构化文档标签的显示文本关联的值。
        
            如果此结构化文档标签未使用dataBinding元素（[§17.5.2.6]）映射到 XML，则应忽略此属性。如果此结构化文档标签已映射到 XML，则应使用该属性来确定打开文档时是否应保留组合框结构化文档标签中的当前显示文本，方法如下：
            
            - 创建 XML 映射时，检索自定义 XML 数据中的内容。
            - 如果此内容具有关联的列表项（与其value属性匹配），则应在结构化文档标签中显示相应的显示文本。
            - 如果不存在列表项，则应将此内容与lastValue属性值进行匹配。如果值匹配，则应保留当前的显示文本。如果值不匹配，则当前自定义 XML 数据内容应成为新的显示文本（因为组合框列表项中不存在匹配项）。
            
            [示例：考虑以下定义的组合框结构化文档标签：

            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dataBinding … />
                    <w:comboBox w:lastValue="2"/>
                </w:sdtPr>
                <w:sdtContent>
                    <w:r>
                        <w:t>Hello, world</w:t>
                    </w:r>
                </w:sdtContent>
            </w:sdt>
            ```
            
            结构化文档标签的当前运行内容为“Hello, world”。当打开此文档时，如果关联的自定义 XML 数据的当前值为2，则匹配的lastValue属性指定了组合框的内容必须继续是组合框的当前显示文本，即使没有 listItem 的值为2（通常情况下，结构化文档标签的内容将设置为2）。基本上，该属性指定一个 listItem，其值为2，其显示文本为“Hello, world”（当前结构化文档标签的内容）。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtComboBox) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies that the nearest ancestor structured document tag shall be a combo box when displayed in the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - The child elements of this element specify choices which shall be presented to the user
    - Formatting applied to any part of this structured document tag's contents shall apply to its entire contents
    
    As well, the structured document tag shall satisfy the following restraints or the document shall be considered non-conformant:
    
    - The contents shall only be contain a single run (one set of formatting properties)
    - The contents shall not contain more than a single paragraph or table cell and shall not contain a table row or table
    
    [Example: Consider the following structured document tag:
    
    
    ```xml
    
    <w:sdt>
        <w:sdtPr>
            …
            <w:comboBox>
                …
            </w:comboBox>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The comboBox element in this structured document tag's properties specify that the type of structured document tag is a combo box. end example]
    
    
    ??? abstract "Attributes"
    
        **lastValue** (Combo Box Last Saved Value)
        
        :   Specifies the value associated with the current display text for the combo box structured document tag.
    
            If this structured document tag is not mapped to XML using the dataBinding element ([§17.5.2.6]), then this attribute shall be ignored. If this structured document tag is mapped to XML, it shall be used to determine whether the current display text in the combo box structured document tag shall be retained when the document is opened, as follows:
            
            - When the XML mapping is created, the content in the custom XML data is retrieved
            - If this content has an associated list item (matching its value attribute), then the corresponding display text shall be displayed in the structured document tag
            - If no list item exists, this content shall be matched against the lastValue attribute value. If the values match, the current display text shall be retained. If the values do not match, the current custom XML data content shall be the new display text (since no match exists in the combo box list items)
            
            [Example: Consider a combo box structured document tag defined as follows:
            
            ```xml
            <w:sdt>
            <w:sdtPr>
            <w:dataBinding … />
            <w:comboBox w:lastValue="2"/>
            </w:sdtPr>
            <w:sdtContent>
            <w:r>
            <w:t>Hello, world</w:t>
            </w:r>
            </w:sdtContent>
            </w:sdt>
            ```
            
            The current run content of the structured document tag reads Hello, world. When this document is opened, if the current value of the associated custom XML data is 2, the matching lastValue attribute specifies that the contents of the combo box must continue to be the current display text of the combo boxeven though there is no listItem whose value is 2 (and normally, the content of the structured document tag would be set to 2. Essentially, this attribute specifies a listItem whose value is 2 and whose displayText is Hello, world (the current structured document tag contents). end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtComboBox) is located in §A.1. end note]


### 17.5.2.6 dataBinding (XML映射)

**dataBinding (XML Mapping)**

=== "中文"
    
    这个元素指定了用于在当前WordprocessingML文档中的Custom XML Data部分中的XML元素与最近的祖先结构化文档标签之间建立映射的信息。
    
    如果省略此元素，则不会将XML映射与当前的结构化文档标签关联起来。如果最近的祖先结构化文档标签是富文本或文档部件库类型，则将忽略此属性。
    
    如果存在此元素且最近的祖先结构化文档标签不是富文本类型，则结构化文档标签的当前值将通过查找由此元素的属性确定的XML元素（如果有的话）来确定。如果此信息未导致XML元素，则应用程序可以使用任何所需的算法来查找最接近的可用匹配项。如果此信息导致XML元素，则该元素的内容将用于替换文档中当前的运行内容。
    
    [示例：考虑以下结构化文档标签：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:dataBinding w:xpath="/root/name/first" … />
            <w:text/>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>old text</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    这个结构化文档标签指定它只包含普通文本，通过文本元素，并且它必须映射到第一个Custom XML Data部分中包含与XPath表达式/root/name/first匹配的元素。当定位到该元素时，其内容必须替换文档中现有的运行内容（例如，如果其内容是新文本，则在显示文档时，此结构化文档标签的运行内容必须是新文本。结束示例]
    
    
    ??? abstract "属性"
    
        **prefixMappings**（XML命名空间前缀映射）
    
        :   指定在评估XPath表达式时应用于当前文档中的自定义XML数据部分的XML命名空间前缀映射集。
    
            该属性的值应使用以下语法指定：xmlns:prefix='namespace'，其中prefix是要映射的命名空间前缀，namespace是要映射到当前前缀的命名空间。属性内容中的每个前缀映射应由一个或多个空白字符分隔。
            
            如果省略了此属性，则将使用每个自定义XML数据部分本身指定的前缀映射来评估给定的XPath表达式。
            
            [示例：考虑以下结构化文档标签属性：
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:prefixMappings="xmlns:ns0=
                    'http://example.com/example'"/>
                <w:text/>
            </w:sdtPr>
            ```
            
            这个结构化文档标签指定它包含一个XML映射，并且映射的prefixMapping属性必须表示要用于评估xpath属性值的命名空间前缀映射集是xmlns:ns0='http://example.com/example'。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
        **storeItemID**（自定义XML数据存储标识符）
    
        :   指定用于评估给定XPath表达式的自定义XML数据部分的自定义XML数据标识符。使用数据存储项元素（[§22.5.2.1]）上的storeItemID属性在自定义XML数据属性部分中指定的自定义XML数据标识符是一个字符串，唯一标识WordprocessingML文档中的特定自定义XML数据部分（因为多个部分可以具有相同的根元素命名空间）。
    
            如果指定了，则xpath属性上指定的XPath表达式应仅针对具有匹配自定义XML数据标识符的属性部分的自定义XML数据部分进行评估。如果不存在具有匹配标识符的自定义XML数据部分，则不应连接XML映射。
            
            如果省略，则应该逐个对每个自定义XML数据部分评估给定的XPath表达式，直到给定的XPath表达式解析为XML元素为止。
            
            [示例：考虑以下结构化文档标签属性：
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:storeItemID="testXmlPart"
                    />
                <w:text/>
            </w:sdtPr>
            ```
            
            这个结构化文档标签指定它包含一个XML映射，并且该映射必须仅针对标识符等于testXmlPart的自定义XML部分进行评估（如果存在）。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
        
        **xpath**（XPath）
        
        :   指定将评估的XPath表达式，以查找映射到最近祖先结构化文档标记的自定义XML节点。此XPath表达式应使用XML路径语言（XPath）版本1.0规范中定义的语法来指定（有关参考文献信息，请参见附件A）。
        
            [示例：考虑以下结构化文档标签属性：
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:prefixMappings="xmlns:ns0=
                    'http://example.com/example'"/>
                <w:text/>
            </w:sdtPr>
            ```
            
            此结构化文档标签指定它包含一个XML映射，并且该映射的xpath属性必须表示要评估的XPath表达式必须是//ns0:book。因为还指定了prefixMapping属性，因此必须使用这些前缀映射来评估此XPath表达式。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DataBinding) is located in §A.1. end note]

=== "英文"
    
    This element specifies the information that shall be used to establish a mapping between the nearest ancestor structured document tag and an XML element stored within a Custom XML Data part in the current WordprocessingML document.
    
    If this element is omitted, then no XML mapping shall be associated with the current structured document tag. If the nearest ancestor structured document tag is of type rich text or document part gallery, then this property shall be ignored.
    
    If this element is present and the nearest ancestor structured document tag is not of a rich text type, then the current value of the structured document tag shall be determined by finding the XML element (if any) which is determined by the attributes on this element. If this information does not result in an XML element, then the application can use any algorithm desired to find the closest available match. If this information does result in an XML element, then the contents of that element shall be used to replace the current run content within the document.
    
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:dataBinding w:xpath="/root/name/first" … />
            <w:text/>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>old text</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    
    This structured document tag specifies that it contains only plain text via the text element, and that it must be mapped to the element in the first Custom XML Data part which contains an element that matches the XPath expression /root/name/first. When that element is located, its contents must replace the existing run content in the document (for example, if its contents are new text, then the contents of the run for this structured document tag must be new text when the document is displayed. end example]
    
    
    ??? abstract "Attributes"
    
        **prefixMappings** (XML Namespace Prefix Mappings)
    
        :   Specifies the set of prefix mappings which shall be used to interpret the XPath expression specified on the xpath attribute when the XPath expression is evaluated against the custom XML data parts in the current document.
    
            This attribute's value shall be specified using the following syntax: xmlns:prefix='namespace', where prefix is the namespace prefix to be mapped, and namespace is the namespace to be mapped to the current prefix. Each prefix mapping shall be delimited by one or more whitespace characters in the attribute's contents.
            
            If this attribute is omitted, then the prefix mappings specified on each of the custom XML data parts itself shall be used to evaluate the given XPath expression.
            
            [Example: Consider the following structured document tag properties:
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:prefixMappings="xmlns:ns0=
                    'http://example.com/example'"/>
                <w:text/>
            </w:sdtPr>
            ```
            
            This structured document tag specifies that it contains an XML mapping, and that mapping's prefixMapping attribute must signify that the set of namespace prefix mappings to be used to evaluate the xpath attribute value must be xmlns:ns0='http://example.com/example'. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        **storeItemID** (Custom XML Data Storage ID)
    
        :   Specifies the custom XML data identifier for the custom XML data part which shall be used to evaluate the given XPath expression. The custom XML data identifier, specified using the storeItemID attribute of the dataStoreItem element ([§22.5.2.1]) on the Custom XML Data Properties part is a string that uniquely identifies a particular custom XML data part in a WordprocessingML document (as multiple parts can have the same namespace for their root element).
    
            If specified, then the XPath expression specified on the xpath attribute shall only be evaluated against the custom XML data part whose properties part has a matching custom XML data identifier. If no custom XML data part exists with a matching identifier, then the XML mapping shall not be connected.
            
            If omitted, then the XPath expression shall be evaluated against each custom XML data part in turn until the given XPath expression is resolved to an XML element.
            
            [Example: Consider the following structured document tag properties:
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:storeItemID="testXmlPart"
                    />
                <w:text/>
            </w:sdtPr>
            ```
            
            This structured document tag specifies that it contains an XML mapping, and that mapping must only be evaluated against the custom XML part whose identifier is equal to testXmlPart (if one exists). end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
        **xpath** (XPath)
    
        :   Specifies the XPath expression that shall be evaluated to find the custom XML node that is mapped to the nearest ancestor structured document tag. This XPath expression shall be specified using the syntax defined in the XML Path Language (XPath) Version 1.0 specification (see Annex A for bibliographic reference information).
    
            [Example: Consider the following structured document tag properties:
            
            ```xml
            <w:sdtPr>
                <w:dataBinding w:xpath="//ns0:book"
                    w:prefixMappings="xmlns:ns0=
                    'http://example.com/example'"/>
                <w:text/>
            </w:sdtPr>
            ```
            
            This structured document tag specifies that it contains an XML mapping, and that mapping's xpath attribute must signify that the XPath expression to be evaluated must be //ns0:book. Because the prefixMapping attribute is also specified, those prefix mappings must be used to evaluate this XPath expression. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DataBinding) is located in §A.1. end note]

### 17.5.2.7 date (日期结构化文档标签)

**date (Date Structured Document Tag)**

=== "中文"
    
    这个元素指定，最近的祖先结构化文档标记在文档中显示时应该是一个日期选择器。
    
    这个设置指定了这个结构化文档标记的行为如下：
    
    - 此元素的子元素指定了在任何映射到自定义XML数据的日期在该结构化文档标记中如何存储，并在文档中显示。
    - 应用于结构化文档标记内容的任何部分的格式应该适用于其整个内容。
    
    此外，结构化文档标记应满足以下限制，否则文档将被视为不符合规范：
    
    - 内容只能包含一个运行（一个格式属性集）
    - 内容不能包含多个段落或表格单元，并且不能包含表行或表格单元
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:date>
                …
            </w:date>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    该结构化文档标记的属性中的date元素指定了结构化文档标记的类型为日期选择器。结束示例】
    
    ??? abstract "属性"
    
        **fullDate**（XML模式DateTime格式中的最后已知日期）
    
        :   指定使用标准XML模式DateTime语法最后输入到最近祖先结构化文档标记中的完整日期和时间。
    
            [注意：使用此缓存的原因是存储在dateFormat元素（[§17.5.2.8]）上的日期显示掩码可能不包含日期的所有信息，如果稍后更改了日期显示掩码，则可能需要这些信息。结束注意]
            
            如果指定了此属性，则当前fullDate属性应通过dateFormat元素中指定的日期显示掩码来填充最近祖先结构化文档标记的运行内容（如果存在）。
            
            如果省略了此属性，则在显示文档时将维护当前显示文本。
            
            【示例：考虑以下结构化文档标记属性：
            
            ```xml
            <w:sdtPr>
                …
                <w:date w:fullDate="2006-01-01T05:30:00Z">
                    …
                </w:date>
            </w:sdtPr>
            ```
            
            当前结构化文档标记的完整XML模式DateTime格式通过fullDate属性值指定为2006-01-01T05:30:00Z。结束示例】
            
            此属性的可能值由ST_DateTime简单类型（[§17.18.9]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDate) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be a date picker when displayed in the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - The child elements of this element specify how the dates in this structured document tag shall be stored in any mapped custom XML data and displayed in the document
    - Formatting applied to any part of this structured document tag's contents shall apply to its entire contents
    
    As well, the structured document tag shall satisfy the following restraints or the document shall be considered non-conformant:
    
    - The contents shall only be contain a single run (one set of formatting properties)
    - The contents shall not contain more than a single paragraph or table cell and shall not contain a table row or table cell
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:date>
                …
            </w:date>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The date element in this structured document tag's properties specifies that the type of structured document tag is a date picker. end example]
    
    ??? abstract "Attributes"
    
        **fullDate** (Last Known Date in XML Schema DateTime Format)
    
        :   Specifies the full date and time last entered into the nearest ancestorstructured document tag using the standard XML Schema DateTime syntax.
    
            [Note: This cache is used because the date display mask stored on the dateFormat element ([§17.5.2.8]) might not contain all of the information about the date, which might be needed if the date display mask is later changed. end note]
            
            If this attribute is specified, then the current fullDate attribute shall be used to populate the run content of the nearest ancestor structured document tag by filtering it through the date display mask specified in the dateFormat element, if one is present.
            
            If this attribute is omitted, then the current display text shall be maintained when the document is displayed.
            
            [Example: Consider the following structured document tag properties:
            
            ```xml
            <w:sdtPr>
                …
                <w:date w:fullDate="2006-01-01T05:30:00Z">
                    …
                </w:date>
            </w:sdtPr>
            ```
            
            The full XML Schema DateTime format for the current structured document tag is specified via the fullDate attribute value as 2006-01-01T05:30:00Z. end example]
            
            The possible values for this attribute are defined by the ST_DateTime simple type ([§17.18.9]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDate) is located in §A.1. end note]

### 17.5.2.8 dateFormat (日期显示水印)

**dateFormat (Date Display Mask)**

=== "中文"

    该元素指定了在显示之前用于格式化输入到最近祖先结构化文档标记中的任何日期的显示格式，该日期以完整的DateTime格式输入[示例：通过用户界面（日期选择器），或通过与该结构化文档标记相关联的自定义XML数据，通过数据绑定(dataBinding)元素（ [§17.5.2.6] ）来输入。结束示例]。
    
    如果省略了此元素，则将使用语言ID元素（[§17.5.2.20]）上指定的语言ID的标准日期显示掩码进行格式化，如果存在的话，否则使用运行内容的语言ID。
    
    val属性中指定的日期显示掩码应根据 [§17.16.4.1] 中指定的语义进行解释。
    
    【示例：考虑以下结构化文档标记属性：
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:dateFormat w:val="MM-YYYY"/>
        </w:date>
    </w:sdtPr>
    ```
    
    当前结构化文档标记的完整XML模式DateTime格式通过fullDate属性值指定为2006-01-01T06:30:00Z，并且日期显示掩码是MM-YYYY，因此文档中显示的结果日期必须为01-2006（从完整日期值中分别取出月份和长年份）。结束示例】
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父XML元素的上下文进行解释。
            
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
            
            在这种情况下，val属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，该值都是根据父元素的上下文进行解释的。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    The element specifies the display format that shall be used to format any date entered into the nearest ancestor structured document tag in full DateTime format [Example: Through a user interface (a date picker), or through custom XML data associated with this structured document tag via the dataBinding element ( [§17.5.2.6] ). end example] before displaying it in the structured document tag's run content.
    
    If this element is omitted, then the date shall be formatted using the standard date display mask for the language ID specified on the lid element ([§17.5.2.20]) if present, or the language ID of the run contents otherwise.
    
    The date display mask specified in the val attribute shall be interpreted using the semantics specified in [§17.16.4.1].
    
    [Example: Consider the following structured document tag properties:
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:dateFormat w:val="MM-YYYY"/>
        </w:date>
    </w:sdtPr>
    ```
    
    The full XML Schema DateTime format for the current structured document tag is specified via the fullDate attribute value as 2006-01-01T06:30:00Z, and the date display mask is MM-YYYY, therefore the resulting date displayed in the document must be 01-2006 (the month and long year from the full date value, respectively). end example]
    
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

### 17.5.2.9 docPart (文档部件参考)

**docPart (Document Part Reference)**

=== "中文"
    
    该元素指定了在其运行内容为空时，应显示在最近祖先结构化文档标记中的文档部件的名称。如果指定了此元素，则将定位一个命名过的文档部件（[§17.12.12]）其名称与此元素的值匹配，并且属于 bbPlcHdr 样式，以用作最近祖先结构化文档标记的占位符文本。
    
    如果未找到与此元素指定的条件匹配的文档部件，则将使用五个不间断空格作为默认占位符文本。
    
    【示例：考虑以下定义的结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22610170" />
            </w:placeholder>
            …
        </w:sdtPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    通过docPart元素，此结构化文档标记指定其占位符文本必须在样式为bbPlcHdr且名称为DefaultPlaceholder_22610170的文档部件中指定。结束示例】
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父XML元素的上下文进行解释。
            
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
            
            在这种情况下，val属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，该值都是根据父元素的上下文进行解释的。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the name of the document part that shall be displayed in the nearest ancestor structured document tag when its run contents are empty. If this element is specified, then a document part whose name element ([§17.12.12]) specifies a name matching the value of this element, and which belongs to the bbPlcHdr style shall be located to be used as the placeholder text for the nearest ancestorstructured document tag.
    
    If no document part is located matching the criteria specified by this element, then five non-breaking spaces shall be used as the default placeholder text.
    
    [Example: Consider a structured document tag defined as follows:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22610170" />
            </w:placeholder>
            …
        </w:sdtPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    This structured document tag specifies through the docPart element that its placeholder text must be specified in the document part of style bbPlcHdr whose name is equal to DefaultPlaceholder_22610170 . end example]
    
    
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

### 17.5.2.10 docPartCategory (文档部件类别过滤器)

**docPartCategory (Document Part Category Filter)**

=== "中文"
    
    该元素指定了在确定显示哪些文档部件以供插入到最近祖先结构化文档标记中时，应使用的文档部件类别过滤器。文档部件类别是给定文档部件库中的一个子分类，可用于进一步对给定库中的部件进行分类。【示例：库custom1可能具有法律条款、一致性条款等类别。结束示例】。应用程序存储在此元素的val属性中的类别作为过滤器。
    
    如果省略了此元素，则最近祖先结构化文档标记将显示指定库中的所有文档部件，而不考虑其指定的类别。如果存在此元素，但应用程序未找到指定库和类别组合的文档部件，则不会显示任何文档部件（即，应用程序不会回退到显示指定库中所有类别的文档部件）。
    
    【示例：考虑以下结构化文档标记的属性：
    
    ```xml
    <w:sdtPr>
        <w:docPartList>
            <w:docPartGallery w:val="custom1"/>
            <w:docPartCategory w:val="Legal Clauses"/>
        </w:docPartList>
    </w:sdtPr>
    ```
    此结构化文档标记指定它必须通过docPartList元素（[§17.5.2.12]）提供要插入的文档部件的选择，而这些文档部件必须仅通过docPartType元素（[§17.5.2.11]）位于custom1库中，并且在该库中，仅通过此元素位于名为Legal Clauses的类别中的文档部件。结束示例】
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父XML元素的上下文进行解释。
        
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
            
            在这种情况下，val属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，该值都是根据父元素的上下文进行解释的。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the category of document parts that shall be used as the filter when determining the possible choices of document parts that are displayed for insertion into the nearest ancestor structured document tag. A document part category is a sub-classification within a given document part gallery which can be used to further categorize the parts in a given gallery. [Example: Gallery custom1 might have categories of Legal Clauses, Conformance Clauses, etc. end example]. The category which shall be used as a filter is stored in this element's val attribute.
    
    If this element is omitted, then the nearest ancestor structured document tag shall display all document parts in the specified gallery regardless their specified category. If this element is present, but no document parts of the specified gallery and category combination are located by the application, then no document parts shall be displayed (i.e. the application shall not fall back to showing document parts in all categories in the specified gallery).
    
    [Example: Consider the following properties for a structured document tag:
    
    ```xml
    <w:sdtPr>
        <w:docPartList>
            <w:docPartGallery w:val="custom1"/>
            <w:docPartCategory w:val="Legal Clauses"/>
        </w:docPartList>
    </w:sdtPr>
    ```
    This structured document tag specifies that it must present a selection of document parts for insertion via the docPartList element ([§17.5.2.12]) , and those document parts must only be the parts which are in the custom1 gallery via the docPartType element ([§17.5.2.11]), and within that gallery, only the document parts which are in a category called Legal Clauses via this element. end example]
    
    
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

### 17.5.2.11 docPartGallery (文档部件图库过滤器)

**docPartGallery (Document Part Gallery Filter)**

=== "中文"
    
    该元素指定了在确定显示哪些文档部件以供插入到最近祖先结构化文档标记中时，应使用的文档部件库作为过滤器。文档部件库是文档部件的分类，可能会进一步细分为类别。【示例：一个名称为custom1的库可能具有法律条款、一致性条款等类别。结束示例】。将要使用的库存储在此元素的val属性中。
    
    如果省略了此元素，则最近祖先结构化文档标记将显示其默认库中的所有文档部件。如果存在此元素，但应用程序未找到指定库中的文档部件，则将显示默认库中的文档部件（即，应用程序将表现得好像省略了值）。
    
    【示例：考虑以下结构化文档标记的属性：
    
    ```xml
    <w:sdtPr>
        <w:docPartList>
            <w:docPartGallery w:val="custom1"/>
        </w:docPartList>
    </w:sdtPr>
    ```
    
    
    此结构化文档标记指定它必须通过docPartList元素（[§17.5.2.12]）提供要插入的文档部件的选择，并且这些文档部件必须仅通过此元素位于custom1库中。结束示例】
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
            
            此字符串的内容根据父XML元素的上下文进行解释。
            
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
            
            在这种情况下，val属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，该值都是根据父元素的上下文进行解释的。结束示例]
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies the gallery of document parts that shall be used as the filter when determining the possible choices of document parts that are displayed for insertion into the nearest ancestor structured document tag. A document part gallery is a classification of document parts, which might then be subdivided into categories. [Example: A gallery with a name of custom1 might have categories of Legal Clauses, Conformance Clauses, etc. end example]. The gallery which shall be used is stored in this element's val attribute.
    
    If this element is omitted, then the nearest ancestor structured document tag shall display all document parts in its default gallery. If this element is present, but no document parts of the specified gallery are located by the application, then document parts in the default gallery shall be displayed (i.e. the application shall behave as if the value was omitted).
    
    [Example: Consider the following properties for a structured document tag:
    
    
    ```xml
    <w:sdtPr>
        <w:docPartList>
            <w:docPartGallery w:val="custom1"/>
        </w:docPartList>
    </w:sdtPr>
    ```
    
    
    This structured document tag specifies that it must present a selection of document parts for insertion via the docPartList element ([§17.5.2.12]), and those document parts must only be the parts which are in the custom1 gallery via this element. end example]
    
    
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


### 17.5.2.12 docPartList (文档部件图库结构化文档标签)

**docPartList (Document Part Gallery Structured Document Tag)**

=== "中文"

    该元素指定最近祖先结构化文档标记应为文档部件库类型。
    
    此设置不要求或暗示结构化文档标记的内容必须仅包含当前计算机上存在的指定库和类别的文档部件的确切内容，它仅用于指定结构化文档标记是此类的，应用程序将使用它来呈现插入到最近祖先结构化文档标记中的可能选择列表。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartList>
                …
            </w:docPartList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的docPartList元素指定了结构化文档标记的类型为文档部件库。如果有的话，子元素必须为此列表指定库和类别过滤器。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDocPart) is located in §A.1. end note]

=== "英文"

    This element specifies that the nearest ancestor structured document tag shall be of a document part gallery type.
    
    This setting does not require or imply that the contents of the structured document tag shall contain only the exact contents of a document part of the specified gallery and category which is present on the current machine, it shall only be used to specify that the structured document tag is of this kind, which shall be used by an application to present the possible list of choices for insertion into the nearest ancestor structured document tag.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartList>
                …
            </w:docPartList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The docPartList element in this structured document tag's properties specifies that the type of structured document tag is a document part gallery. The child elements must specify the gallery and category filters for this list, if any. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDocPart) is located in §A.1. end note]

### 17.5.2.13 docPartObj (内置文档部件结构化文档标签)

**docPartObj (Built-In Document Part Structured Document Tag)**

=== "中文"
    
    该元素指定最近祖先结构化文档标记应为文档部件类型。
    
    此设置不要求或暗示结构化文档标记的内容必须仅包含当前计算机上存在的指定库和类别的文档部件的确切内容，它仅用于指定结构化文档标记是此类的，应用程序将使用它来呈现插入到最近祖先结构化文档标记中的可能选择列表。
    
    该元素与docPartList元素（[§17.5.2.12]）不同之处在于，它可用于在WordprocessingML文档中语义标记一组块级对象，而无需通过用户界面指定可与之交换的对象的类别和库。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartObj>
                …
            </w:docPartObj>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的docPartObj元素指定了结构化文档标记的类型为文档部件。如果有的话，子元素必须为此部分指定库和类别语义。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDocPart) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be of a document part type.
    
    This setting does not require or imply that the contents of the structured document tag shall contain only the exact contents of a document part of the specified gallery and category which is present on the current machine, it shall only be used to specify that the structured document tag is of this kind, which shall be used by an application to present the possible list of choices for insertion into the nearest ancestor structured document tag.
    
    This element differs from the docPartList element ([§17.5.2.12]) in that it can be used to semantically tag a set of block-level objects in a WordprocessingML document without requiring the ability to specify a category and gallery of objects which can be swapped with it via the user interface.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartObj>
                …
            </w:docPartObj>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    The docPartObj element in this structured document tag's properties specify that the type of structured document tag is a document part. The child elements must specify the gallery and category semantics for this part, if any. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDocPart) is located in §A.1. end note]

### 17.5.2.14 docPartUnique (内置文档部件)

**docPartUnique (Built-In Document Part)**

=== "中文"
    
    该元素指定此结构化文档标记用于封装内置文档部件（即，此元素出现为docPartObj元素的子元素）。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartObj>
                …
                <w:docPartUnique/>
            </w:docPartObj>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的docPartUnique元素指定了结构化文档标记的类型为文档部件的容器。结束示例】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies that this structured document tag is being used to encapsulate a built-in document part (i.e. this element appears as a child element of the docPartObj element).
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:docPartObj>
                …
            <w:docPartUnique/>
            </w:docPartObj>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The docPartUnique element in this structured document tag's properties specify that the type of structured document tag is a container for a document part. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].


### 17.5.2.15 dropDownList (下拉列表结构化文档标签)

**dropDownList (Drop-Down List Structured Document Tag)**

=== "中文"

    该元素指定在文档中显示时，最近的祖先结构化文档标记将是下拉列表。
    
    此设置指定此结构化文档标记的行为应如下：
    
    - 无论锁定设置如何，由主机应用程序显示时，内容都不可编辑。
    - 该元素的子元素指定应以标准下拉列表格式显示的选项。
    
    此外，结构化文档标记必须满足以下约束条件，否则将视为不符合规范：
    
    - 内容只能包含一个运行（一个格式属性集）
    - 内容不能包含多个段落或表格单元，也不能包含表格行或表格单元格
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:dropDownList>
                …
            </w:dropDownList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的dropDownList元素指定了结构化文档标记的类型为下拉列表。结束示例】
    
    ??? abstract "属性"
    
        **lastValue**（下拉列表上次保存的值）
    
        :   指定与下拉列表结构化文档标记的当前显示文本相关联的值。
    
            如果此结构化文档标记未使用dataBinding元素（[§17.5.2.6]）映射到 XML，则应忽略此属性。如果此结构化文档标记已映射到 XML，则应使用它来确定是否应保留文档打开时下拉列表结构化文档标记中的当前显示文本，如下所示：
            
            - 创建 XML 映射时，检索自定义 XML 数据中的内容。
            - 如果此内容具有关联的列表项（匹配其值属性），则应在结构化文档标记中显示相应的显示文本。
            - 如果不存在列表项，则应将此内容与lastValue属性值进行匹配。如果值匹配，则应保留当前显示文本。如果值不匹配，则当前自定义 XML 数据内容将成为新的显示文本（因为在下拉列表的列表项中不存在匹配项）。
            
            【示例：考虑定义如下的下拉列表结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dataBinding … />
                    <w:dropDownList w:lastValue="2"/>
                </w:sdtPr>
                <w:sdtContent>
                    <w:r>
                        <w:t>Hello, world</w:t>
                    </w:r>
                </w:sdtContent>
            </w:sdt>
            ```
            
            结构化文档标记的当前运行内容为“Hello, world”。当打开此文档时，如果关联的自定义 XML 数据的当前值为2，则匹配的lastValue属性指定下拉列表的内容必须继续是下拉列表的当前显示文本，即使没有值为2的listItem（通常，结构化文档标记的内容将被设置为2）。基本上，此属性指定值为2且displayText为“Hello, world”（当前结构化文档标记内容）的listItem。结束示例】
            
            此属性的可能值由ST_String简单类型（[§22.9.2.13]）定义。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDropDownList) is located in §A.1. end note]

=== "英文"

    This element specifies that the nearest ancestor structured document tag shall be a drop-down list when displayed in the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - The contents shall not be editable when displayed by a hosting application regardless of the locking settings
    - The child elements of this element specify choices which shall be displayed in a standard drop-down list format
    
    As well, the structured document tag shall satisfy the following restraints or the document shall be considered non-conformant:
    
    - The contents shall only be contain a single run (one set of formatting properties)
    - The contents shall not contain more than a single paragraph or table cell and shall not contain a table row or table
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:dropDownList>
                …
            </w:dropDownList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The dropDownList element in this structured document tag's properties specify that the type of structured
    document tag is a drop-down list. end example]
    
    
    ??? abstract "Attributes"
    
        **lastValue** (Drop-down List Last Saved Value)
    
        :   Specifies the value associated with the current display text for the drop-down list structured document tag.
    
            If this structured document tag is not mapped to XML using the dataBinding element ([§17.5.2.6]), then this attribute shall be ignored. If this structured document tag is mapped to XML, it shall be used to determine whether the current display text in the combo box structured document tag shall be retained when the document is opened, as follows:
            
            - When the XML mapping is created, the content in the custom XML data is retrieved
            - If this content has an associated list item (matching its value attribute), then the corresponding display text shall be displayed in the structured document tag
            - If no list item exists, this content shall be matched against the lastValue attribute value. If the values match, the current display text shall be retained. If the values do not match, the current custom XML data content shall be the new display text (since no match exists in the combo box list items)
            
            [Example: Consider a drop-down list structured document tag defined as follows:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dataBinding … />
                    <w:dropDownList w:lastValue="2"/>
                </w:sdtPr>
                <w:sdtContent>
                    <w:r>
                        <w:t>Hello, world</w:t>
                    </w:r>
                </w:sdtContent>
            </w:sdt>
            ```
            
            The current run content of the structured document tag reads Hello, world. When this document is opened, if the current value of the associated custom XML data is 2, the matching lastValue attribute specifies that the contents of the combo box must continue to be the current display text of the combo boxeven though there is no listItem whose value is 2 (and normally, the content of the structured document tag would be set to 2. Essentially, this attribute specifies a listItem whose value is 2 and whose displayText is Hello, world (the current structured document tag contents). end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDropDownList) is located in §A.1. end note]

### 17.5.2.16 equation (方程结构化文档标签)

**equation (Equation Structured Document Tag)**

=== "中文"
    
    该元素指定最近的祖先结构化文档标记应为等式类型。
    
    此设置不要求或暗示结构化文档标记的内容只能包含等式或相关的占位文本，它只用于指定结构化文档标记为此类型，可以由应用程序根据需要使用。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:equation/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的equation元素指定了结构化文档标记的类型为等式。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be of type equation.
    
    This setting does not require or imply that the contents of the structured document tag shall contain only an equation or associated placeholder text, it shall only be used to specify that the structured document tag is of this kind, which can be used by an application as desired.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:equation/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The equation element in this structured document tag's properties specify that the type of structured document tag is equation. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

### 17.5.2.17 group (分组结构化文档标签)

**group (Group Structured Document Tag)**

=== "中文"
    
    该元素指定最近的祖先结构化文档标记在文档中显示时应为受限制的分组。
    
    此设置指定了此结构化文档标记的行为如下：
    
    - 当由托管应用程序显示时，该结构化文档标记的内容将无法编辑，无论锁定设置如何。每个结构化文档标记都可以覆盖此限制，因为每个结构化文档标记都会为其自身的内容指定锁定属性。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:group/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记中的group元素指定结构化文档标记的类型为受限制的分组。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies that the nearest ancestor structured document tag shall be a restricted grouping when displayed in the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - The contents of this structured document tag shall not be editable when displayed by a hosting application regardless of the locking settings. This restriction can be superseded by any structured document tag contained within the group, as each structured document tag specifies the locking properties for its own content.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:group/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    The group element in this structured document tag's properties specify that the type of structured document tag is a restricted group. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

### 17.5.2.18 id (唯一ID)

**id (Unique ID)**

=== "中文"
    
    该元素为最近的祖先结构化文档标记指定了唯一的数字ID。此ID应在多个会话中保持不变（即一旦指定，就不应更改）。
    
    如果多个结构化文档标记为id属性指定相同的十进制数值，则文档中的第一个结构化文档标记将保留此原始ID，并且当文档打开时，所有后续的结构化文档标记都将被分配新的标识符。
    
    如果省略此元素，则最近的祖先结构化文档标记在文档打开时将被分配新的唯一标识符。
    
    【示例：考虑以下结构化文档标记属性：
    
    ```xml
    <w:sdtPr>
        <w:id w:val="8775518"/>
        …
    </w:sdtPr>
    ```
    
    通过id元素上的val属性，此属性集指定了父结构化文档的ID必须为8775518（当然，受上述冲突管理和解析的影响）。结束示例】
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
    
        :   指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父XML元素的上下文进行解释。
            
            【示例：考虑以下简单类型ST_DecimalNumber的数值WordprocessingML属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例】
            
            此属性的可能值由ST_DecimalNumber简单类型定义（[§17.18.10]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies a unique numerical ID for the nearest ancestor structured document tag. This ID shall be persisted through multiple sessions (i.e. shall not be changed once specified).
    
    If multiple structured document tags specify the same decimal number value for the id attribute, then the first structured document tag in the document shall maintain this original ID, and all subsequent structured document tags shall have new identifiers assigned to them when the document is opened.
    
    If this element is omitted, then the nearest ancestor structured document tag shall have a new unique identifier assigned to it when the document is opened.
    
    [Example: Consider the following structured document tag properties:
    
    ```xml
    <w:sdtPr>
        <w:id w:val="8775518"/>
        …
    </w:sdtPr>
    ```
    
    This set of properties specifies via the val attribute on the id element that the ID for the parent structured document must be 8775518 (subject, of course, to the conflict management and resolution discussed above). end example]
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

### 17.5.2.19 label (结构化文档标签label)

**label (Structured Document Tag Label)**

=== "中文"
        
    该元素指定了与当前结构化文档标记关联的标签标识符。表示标签的标识符将存储在此元素的val属性上，并用于引用结构化文档标记的唯一标识符值。通过特定唯一标识符解析的结构化文档标记的内容将用作引用该特定唯一标识符的结构化文档标记的标签内容。如果存在多个标签元素的实例，则所引用的标签按从最通用到最特定的顺序排序。【示例：用于指定国家名称的表单元素可能引用这三个项目的标签（顺序为）：“发送方”，“家庭地址”和“国家”。结束示例】
    
    如果省略此元素或无法解析标签标识符的值，则不会将标签与给定的结构化文档标记相关联。
    
    【示例：考虑以下两个结构化文档标记，其中一个结构化文档标记将另一个结构化文档标记作为标签引用：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="6" />
            <w:label w:val="5" />
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    标签元素指定具有标识符值为6的结构化文档标记将使用具有标识符值为5的结构化文档标记的内容作为标签来源。在此示例中，标签内容为“Name”。结束示例】
    
    ??? abstract "Attributes"
    
        **val**（十进制数值）
    
        :   指定此属性的内容包含一个十进制数。
    
            此十进制数的内容根据父XML元素的上下文进行解释。
            
            【示例：考虑以下简单类型ST_DecimalNumber的数值WordprocessingML属性：
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            val属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例】
            
            此属性的可能值由ST_DecimalNumber简单类型定义（[§17.18.10]）。
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the label identifier associated with the current structured document tag. The identifier representing the label shall be stored on this element’s val attribute and is used to reference the unique identifier value of a structured document tag. The contents of the structured document tag resolved by a specific unique identifier shall be used as the label content for the structured document tag that references that specific unique identifier of the structured document tag. If multiple instances of the label element are present, the labels referenced are ordered from most general to most specific. [Example: A form element for specifying country name might reference the label for these three items (in order): “Sender”, “Home Address”, and “Country”. end example]
    
    If this element is omitted or the value of the label identifier cannot be resolved, then no label shall be associated with the given structured document tag.
    
    [Example: Consider the following two structured document tags where one structured document tag references another structured document tag as a label:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="6" />
            <w:label w:val="5" />
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The label element specifies that the structured document tag with an identifier value of 6 uses the contents of the structured document tag with an identifier value of 5 as a label source. In this example, the label contents are “Name”. end example]
    
    
    ??? abstract "Attributes"
    
        **val** (Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a decimal number.
    
            The contents of this decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of simple type ST_DecimalNumber:
            
            ```xml
            <… w:val="1512645511" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_DecimalNumber simple type ([§17.18.10]).
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DecimalNumber) is located in §A.1. end note]


### 17.5.2.20 lid (日期选择器语言 ID)

**lid (Date Picker Language ID)**

=== "中文"
    
    
    该元素指定用于显示当前日期选择器结构化文档标记的日历的语言标识符，如果有用户界面用于结构化文档标记。
    
    如果省略此元素，则语言标识符将是最近的祖先结构化文档标记的运行内容的语言标识符。
    
    【示例：考虑以下结构化文档标记属性：
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:lid w:val="ja-JP"/>
        </w:date>
    </w:sdtPr>
    ```
    
    在文档中显示的日历语言标识符必须是日语（日本）语言格式（ja-JP）的默认日历格式。结束示例】
    
    ??? abstract "属性"
    
        **val**（语言代码）
        
        :   指定特定语言的标识符。
    
            此代码在父XML元素的上下文中解释。
            
            【示例：考虑必须指定英语（加拿大）语言的对象。该对象将使用en-CA作为标识符来指定此语言。结束示例】
            
            此属性的可能值由ST_Lang简单类型定义（[§22.9.2.6]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lang) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies the language ID that shall be used for displaying a calendar for the current date picker structured document tag, if a user interface is present for the structured document tag.
    
    If this element is omitted, then the language ID shall be the language ID of the run contents of the nearest ancestor structured document tag.
    
    [Example: Consider the following structured document tag properties:
    
    ```xml
    <w:sdtPr>
        <w:date w:fullDate="2006-01-01T06:30:00Z">
            <w:lid w:val="ja-JP"/>
        </w:date>
    </w:sdtPr>
    ```
    
    
    The calendar language ID for a calendar which can be displayed in the document must be the default calendar format for the Japanese (Japan) language format (ja-JP). end example]
    
    ??? abstract "Attributes"
    
        **val** (Language Code)
        
        :   Specifies an identifier for a specific language.
    
            This code is interpreted in the context of the parent XML element.
            
            [Example: Consider an object which must specify the English(Canada) language. That object would use an identifier of en-CA to specify this language. end example]
            
            The possible values for this attribute are defined by the ST_Lang simple type ([§22.9.2.6]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lang) is located in §A.1. end note]

### 17.5.2.21 listItem (组合框列表项)

**listItem (Combo Box List Item)**

=== "中文"
    
    该元素指定父级组合框结构化文档标记中的单个列表项。每个列表项将显示在最近的祖先结构化文档标记的列表中（如果存在用户界面）。
    
    【示例：考虑以下组合框结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:comboBox>
                <w:listItem w:displayText="Zero" w:value="0"/>
                <w:listItem w:displayText="One" w:value="1"/>
            </w:comboBox>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    comboBox 元素内的每个 listItem 元素指定单个列表项条目，在本例中导致父级组合框结构化文档标记中有两个列表项。结束示例】
    
    ??? abstract "属性"
    
        **displayText**（列表项显示文本）
    
        :   指定要在运行内容（以及任何提供的用户界面）中显示的文本，以代替该下拉列表条目的 value 属性内容。
    
            该值将按以下方式使用：
            
            - 如果最近的祖先结构化文档标记映射到自定义 XML 元素，则该自定义 XML 元素中的值将映射到 value 属性的内容，并且显示的 displayText 属性值（如果存在）将显示在运行内容中。如果不存在 displayText 属性，则将显示值。
            - 如果通过用户界面选择相应的条目，则此值将存储在文档中父元素的运行内容中（这是将显示在文档的 WordprocessingML 内容中的值）。
            
            如果省略此属性，则将使用 value 属性的内容作为当前列表项条目的显示文本。
            
            【示例：考虑以下下拉列表结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dropDownList>
                        <w:listItem w:displayText="The Letter A" w:value="a"/>
                        <w:listItem w:displayText="The Letter B" w:value="b"/>
                    </w:dropDownList>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            第一个条目的 displayText 属性值是 The Letter A，第二个是 The Letter B，因此，如果最近的祖先结构化文档标记映射到自定义 XML 数据的自定义 XML 数据部分中，则使用这些值来确定显示文本。结束示例】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
        
        **value**（列表项值）
    
        :   指定当前列表项条目的值。
    
            该值将按以下方式使用：
            
            - 如果最近的祖先结构化文档标记映射到自定义 XML 元素，则该自定义 XML 元素中的值将映射到此值，并且显示的 displayText 属性值（如果存在）将显示在运行内容中。如果不存在 displayText 属性，则将显示值。
            - 如果通过用户界面选择相应的条目，则此值将存储在父元素的 listItem 属性值中。
            
            【示例：考虑以下组合框结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:comboBox>
                        <w:listItem w:displayText="Zero" w:value="0"/>
                        <w:listItem w:displayText="One" w:value="1"/>
                    </w:comboBox>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            第一个条目的 value 属性是 0，第二个是 1，因此，如果最近的祖先结构化文档标记映射到自定义 XML 数据的自定义 XML 数据部分中，则使用这些值来确定显示文本。结束示例】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtListItem) is located in §A.1. end note]

=== "英文"
    
    This element specifies a single list item within the parent combo box structured document tag. Each list item shall be displayed in the list displayed for the nearest ancestor structured document tag (if a user interface is present).
    
    [Example: Consider the following combo box structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:comboBox>
                <w:listItem w:displayText="Zero" w:value="0"/>
                <w:listItem w:displayText="One" w:value="1"/>
            </w:comboBox>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    Each listItem element within the comboBox element specifies a single list item entry, in this case resulting in two list items within the parent combo box structured document tag. end example]
    
    ??? abstract "Attributes"
    
        **displayText** (List Entry Display Text)
    
        :   Specifies the text to display in the run content (as well as any supplied user interface) in place of the value attribute contents for this drop-down list entry.
    
            This value shall be used as follows:
            
            - If the nearest ancestor structured document tag is mapped to a custom XML element, the value in that custom XML element shall be mapped the content of the value attribute, and the resulting displayText attribute value (if one is present) shall be displayed in the run content. If no displayText attribute is present, then the value shall be displayed.
            - If the corresponding entry is selected via a user interface, this value shall be stored in the parent element's run content in the document (this is the value that shall be shown in the document's WordprocessingML content).
            
            If this attribute is omitted, then the content of the value attribute shall be used as the
            display text for the current list item entry.
            
            [Example: Consider the following drop-down list structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dropDownList>
                        <w:listItem w:displayText="The Letter A" w:value="a"/>
                        <w:listItem w:displayText="The Letter B" w:value="b"/>
                    </w:dropDownList>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            The displayText attribute for the first entry is The Letter A and the second is The Letter B, therefore, these values are used to determine the display text if the nearest ancestor structured document tag is mapped to custom XML data in a custom XML data part. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
        
        **value** (List Entry Value)
    
        :   Specifies the value for the current list item entry.
    
            This value shall be used as follows:
            
            - If the nearest ancestor structured document tag is mapped to a custom XML element, the value in that custom XML element shall be mapped to this value, and the resulting displayText attribute value (if one is present) shall be displayed in the run content. If no displayText attribute is present, then the value shall be displayed.
            - If the corresponding entry is selected via a user interface, this value shall be stored in the parent element's listItem attribute value.
            
            [Example: Consider the following combo box structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:comboBox>
                        <w:listItem w:displayText="Zero" w:value="0"/>
                        <w:listItem w:displayText="One" w:value="1"/>
                    </w:comboBox>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            The value attribute for the first entry is 0 and the second is 1, therefore, these values are used to determine the display text if the nearest ancestor structured document tag is mapped to custom XML data in a custom XML data part. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtListItem) is located in §A.1. end note]


### 17.5.2.22 listItem (下拉列表项)

**listItem (Drop-Down List Item)**

=== "中文"
    
    该元素指定父级下拉列表结构化文档标记中的单个列表项。每个列表项将显示在最近的祖先结构化文档标记的列表中（如果存在用户界面）。
    
    【示例：考虑以下组合框结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:dropDownList>
                <w:listItem w:displayText="The Letter A" w:value="a"/>
                <w:listItem w:displayText="The Letter B" w:value="b"/>
            </w:dropDownList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    下拉列表元素内的每个 listItem 元素指定单个列表项条目，在本例中导致父级下拉列表结构化文档标记中有两个列表项。结束示例】
    
    ??? abstract "属性"
        
        **displayText**（列表项显示文本）
    
        :   指定要在运行内容（以及任何提供的用户界面）中显示的文本，以代替该下拉列表条目的 value 属性内容。
    
            该值将按以下方式使用：
            
            - 如果最近的祖先结构化文档标记映射到自定义 XML 元素，则该自定义 XML 元素中的值将映射到 value 属性的内容，并且显示的 displayText 属性值（如果存在）将显示在运行内容中。如果不存在 displayText 属性，则将显示值。
            - 如果通过用户界面选择相应的条目，则此值将存储在文档中父元素的运行内容中（这是将显示在文档的 WordprocessingML 内容中的值）。
            
            如果省略此属性，则将使用 value 属性的内容作为当前列表项条目的显示文本。
            
            【示例：考虑以下下拉列表结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dropDownList>
                        <w:listItem w:displayText="The Letter A" w:value="a"/>
                        <w:listItem w:displayText="The Letter B" w:value="b"/>
                    </w:dropDownList>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            第一个条目的 displayText 属性值是 The Letter A，第二个是 The Letter B，因此，如果最近的祖先结构化文档标记映射到自定义 XML 数据的自定义 XML 数据部分中，则使用这些值来确定显示文本。结束示例】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
        
        **value**（列表项值）
    
        :   指定当前列表项条目的值。
    
            该值将按以下方式使用：
            
            - 如果最近的祖先结构化文档标记映射到自定义 XML 元素，则该自定义 XML 元素中的值将映射到此值，并且显示的 displayText 属性值（如果存在）将显示在运行内容中。如果不存在 displayText 属性，则将显示值。
            - 如果通过用户界面选择相应的条目，则此值将存储在父元素的 listItem 属性值中。
            
            【示例：考虑以下组合框结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:comboBox>
                        <w:listItem w:displayText="Zero" w:value="0"/>
                        <w:listItem w:displayText="One" w:value="1"/>
                    </w:comboBox>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            第一个条目的 value 属性是 0，第二个是 1，因此，如果最近的祖先结构化文档标记映射到自定义 XML 数据的自定义 XML 数据部分中，则使用这些值来确定显示文本。结束示例】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtListItem) is located in §A.1. end note]

=== "英文"
    
    This element specifies a single list item within the parent drop-down list structured document tag. Each list item shall be displayed in the list displayed for the nearest ancestor structured document tag (if a user interface is present).
    
    [Example: Consider the following combo box structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:dropDownList>
                <w:listItem w:displayText="The Letter A" w:value="a"/>
                <w:listItem w:displayText="The Letter B" w:value="b"/>
            </w:dropDownList>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    Each listItem element within the dropDownList element specifies a single list item entry, in this case resulting in two list items within the parent drop-down list structured document tag. end example]
    
    
    ??? abstract "Attributes"
        
        **displayText** (List Entry Display Text)
    
        :   Specifies the text to display in the run content (as well as any supplied user interface) in place of the value attribute contents for this drop-down list entry.
    
            This value shall be used as follows:
            
            - If the nearest ancestor structured document tag is mapped to a custom XML element, the value in that custom XML element shall be mapped the content of the value attribute, and the resulting displayText attribute value (if one is present) shall be displayed in the run content. If no displayText attribute is present, then the value shall be displayed.
            - If the corresponding entry is selected via a user interface, this value shall be stored in the parent element's run content in the document (this is the value that shall be shown in the document's WordprocessingML content).
            
            If this attribute is omitted, then the content of the value attribute shall be used as the
            display text for the current list item entry.
            
            [Example: Consider the following drop-down list structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:dropDownList>
                        <w:listItem w:displayText="The Letter A" w:value="a"/>
                        <w:listItem w:displayText="The Letter B" w:value="b"/>
                    </w:dropDownList>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            The displayText attribute for the first entry is The Letter A and the second is The Letter B, therefore, these values are used to determine the display text if the nearest ancestor structured document tag is mapped to custom XML data in a custom XML data part. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
        
        **value** (List Entry Value)
    
        :   Specifies the value for the current list item entry.
    
            This value shall be used as follows:
            
            - If the nearest ancestor structured document tag is mapped to a custom XML element, the value in that custom XML element shall be mapped to this value, and the resulting displayText attribute value (if one is present) shall be displayed in the run content. If no displayText attribute is present, then the value shall be displayed.
            - If the corresponding entry is selected via a user interface, this value shall be stored in the parent element's listItem attribute value.
            
            [Example: Consider the following combo box structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:comboBox>
                        <w:listItem w:displayText="Zero" w:value="0"/>
                        <w:listItem w:displayText="One" w:value="1"/>
                    </w:comboBox>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            The value attribute for the first entry is 0 and the second is 1, therefore, these values are used to determine the display text if the nearest ancestor structured document tag is mapped to custom XML data in a custom XML data part. end example]
            
            The possible values for this attribute are defined by the ST_String simple type ([§22.9.2.13]).
    
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtListItem) is located in §A.1. end note]

### 17.5.2.23 lock (锁定设置)

**lock (Locking Setting)**

=== "中文"
    
    该元素指定了在应用程序（无论是通过用户界面还是直接）编辑文档内容时，应用于最近祖先结构化文档标记内容的行为集合。通过关联的 val 属性的值来指定应用于结构化文档标记的锁定类型。
    
    如果省略此元素，则应用于结构化文档标记的锁定设置应如下：
    
    - 如果结构化文档标记通过 group 元素（[§17.5.2.17]）指定为组，则结构化文档标记的内容可编辑，但整个标记可以被删除。
    - 对于所有其他类型，不会对结构化文档标记应用任何锁定设置。
    
    【示例：考虑以下纯文本结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:lock w:val="sdtLocked"/>
                …
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    这个纯文本结构化文档标记的属性包含一个 lock 元素，指定了结构化文档标记的锁定行为。由于锁定 val 属性的值为 sdtLocked，因此此锁定设置必须指定结构化文档标记的内容可编辑，但结构化文档标记本身不得从文档中删除。结束示例】
    
    ??? abstract "属性"
    
        **val**（锁定类型）
    
        :   指定应用于最近祖先结构化文档标记的锁定类型。
    
            如果省略此属性，则假定其值为未锁定（使用上述默认值）。
            
            【示例：考虑以下纯文本结构化文档标记属性：
            
            ```xml
            <w:sdtPr>
                <w:lock w:val="contentLocked"/>
                …
                <w:text/>
            </w:sdtPr>
            ```
            
            val 属性值为 contentLocked，因此此锁定设置将指定结构化文档标记的内容不可编辑，但结构化文档标记本身可以从文档中删除。结束示例】
            
            此属性的可能值由 ST_Lock 简单类型定义（[§17.18.49]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lock) is located in §A.1. end note]

=== "英文"
    
    This element specifies the set of behaviors that shall be applied to the contents of the nearest ancestor structured document tag when the contents of this document are edited by an application (whether through a user interface or directly). The type of locking applied to the structured document tag is specified via the value of the associated val attribute.
    
    If this element is omitted, then the locking settings implied for the structured document tag shall be as follows:
    
    - If the structured document tag specifies that it is a group via the group element ([§17.5.2.17]), then the contents of the structured document tag shall be editable, but the entire tag can be deleted.
    - For all other kinds, no locking settings shall be applied to the structured document tag.
    
    
    [Example: Consider the following plain text structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:lock w:val="sdtLocked"/>
                …
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    
    This plain text structured document tag's properties contain a lock element, specifying locking behaviors for the structured document tag. Since the locking val attribute value is sdtLocked, this locking setting must specify that the contents of the structured document tag can be edited, but the structured document tag itself must not be deleted from the document. end example]
    
    ??? abstract "Attributes"
    
        **val** (Locking Type)
    
        :   Specifies the type of locking which shall be applied to the nearest ancestor structured document tag.
    
            If this attribute is omitted, this its value shall be assumed to be unlocked (using the defaults stated above).
            
            [Example: Consider the following plain text structured document tag properties:
            
            ```xml
            <w:sdtPr>
                <w:lock w:val="contentLocked"/>
                …
                <w:text/>
            </w:sdtPr>
            ```
            
            The val attribute value is contentLocked, therefore this locking setting shall specify that the contents of the structured document tag must not be edited, but the structured document tag itself can be deleted from the document. end example]
            
            The possible values for this attribute are defined by the ST_Lock simple type ([§17.18.49]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Lock) is located in §A.1. end note]


### 17.5.2.24 picture (图片结构化文档标签)

**picture (Picture Structured Document Tag)**

=== "中文"
    
    该元素指定了在文档中显示时，最近祖先结构化文档标记应为图片。
    
    此设置指定了此结构化文档标记的行为应如下：
    
    - 内容应始终限制为单个图片，使用 DrawingML（[§20.1]）语法。
    
    此外，结构化文档标记应满足以下限制，否则文档将被视为不符合规范：
    
    - 内容应仅为单个图片，使用 DrawingML（[§20.1]）语法。
    - 内容不得包含多个段落或表格单元，也不得包含表格行或表格。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:picture/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的 picture 元素指定了结构化文档标记的类型为图片。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be a picture when displayed in
    the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - The contents shall always be restricted to a single picture using the DrawingML ([§20.1]) syntax
    
    As well, the structured document tag shall satisfy the following restraints or the document shall be considered
    non-conformant:
    
    - The contents shall only be a single picture using the DrawingML ([§20.1]) syntax
    - The contents shall not contain more than a single paragraph or table cell and shall not contain a table row or table
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:picture/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The text element in this structured document tag's properties specify that the type of structured document tag is a picture. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

### 17.5.2.25 placeholder (结构化文档标签占位符文本)

**placeholder (Structured Document Tag Placeholder Text)**

=== "中文"
    
    该元素指定了当该结构化文档标记的运行内容为空时应显示的占位文本，如通过 dataBinding 元素（[§17.5.2.6]）或 structured document tag 属性中设置的 showingPlcHdr 元素（[§17.5.2.39]）指定的映射 XML 元素为空。应显示的占位文本是通过子元素 docPart 指定的。
    
    如果省略此元素，则默认占位文本为五个不间断空格。
    
    【示例：考虑一个定义如下的结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22610170" />
            </w:placeholder>
            …
        </w:sdtPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    此结构化文档标记通过 placeholder 元素指定，其占位文本必须在类型为 bbPlcHdr 且名称等于 DefaultPlaceholder_22610170 的文档部分中指定。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Placeholder) is located in §A.1. end note]

=== "英文"
    
    This element specifies the placeholder text which should be displayed when this structured document tag's run contents are empty, the associated mapped XML element is empty as specified via the dataBinding element ([§17.5.2.6]) or the showingPlcHdr element ([§17.5.2.39]) is set in the structured document tag's properties. The placeholder text which shall be shown is itself specified via the child element docPart.
    
    If this element is omitted, then five non-breaking spaces shall be used as the default placeholder text for this structured document tag.
    
    [Example: Consider a structured document tag defined as follows:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="DefaultPlaceholder_22610170" />
            </w:placeholder>
            …
        </w:sdtPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    This structured document tag specifies through the placeholder element that its placeholder text must be specified in the document part of type bbPlcHdr whose name is equal to DefaultPlaceholder_22610170 . end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Placeholder) is located in §A.1. end note]


### 17.5.2.26 richText (富文本结构化文档标签)

**richText (Rich Text Structured Document Tag)**

=== "中文"
    
    该元素指定了在文档中显示时，最近的祖先结构化文档标记应为富文本框。
    
    如果未指定类型元素（父 sdtPr 元素的 XML Schema 片段中的 xsd:choice 块），则最近的祖先结构化文档标记应为 richText 类型。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:richText/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    此结构化文档标记的属性中的 richText 元素指定了结构化文档标记的类型为富文本框。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies that the nearest ancestor structured document tag shall be a rich text box when displayed in the document.
    
    If no type element (the xsd:choice block in the XML Schema fragment for the parent sdtPr element) is specified, then the nearest ancestor structured document tag shall be of type richText.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
        <w:richText/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The richText element in this structured document tag's properties specify that the type of structured document tag is a rich text box. end example].
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.1. end note]

### 17.5.2.27 rPr (结构化文档标签内容的运行(run)属性)

**rPr (Run Properties For Structured Document Tag Contents)**

=== "中文"
    
    该元素指定了应用于替换占位符文本的最近祖先结构化文档标记中输入文本的一组运行属性。当结构化文档标记中存在占位符文本时，其格式通常与所需的基础格式不同，该元素指定了在初始添加到控件中的非占位符文本内容所使用的格式。
    
    如果未提供此元素，则插入的文本与任何其他文本一样未格式化 - 它不会继承占位符文本的属性。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="TestPlaceholderDocPart"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:rPr>
                <w:rStyle w:val="UserName"/>
            </w:rPr>
            …
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="PlaceholderText"/>
                </w:rPr>
                <w:t>[Type Your Name Here]</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    此结构化文档标记通过 showingPlcHdr 元素指定了其当前内容为占位符文本，并且该文本应用了 PlaceholderText 字符样式。
    
    现在，假设该样式创建了灰色阴影文本（典型的占位符文本）。这种格式显然不适用于输入到结构化文档标记中的任何文本。因此，当添加此文本时，sdtPr 中的 rPr 元素用于存储结果文本的格式。
    
    在这个示例中，最初填充控件的文本将使用 UserName 字符样式进行格式化。结束示例】
    
    该元素的内容模型（CT_RPr）的 W3C XML Schema 定义位于 §A.1。上表中的每个子元素不得多于一次出现。【注意：由于 W3C XML Schema 语言的限制，此限制未反映在元素的内容模型中。结束注意】

=== "英文"
    
    This element specifies the set of run properties that shall be applied to the text entered into the nearest ancestor structured document tag in replacement of placeholder text. When placeholder text is present in a structured document tag, its formatting is often different than the desired underlying formatting, and this element specifies the formatting which shall be used for non-placeholder text contents when they are initially added to the control.
    
    If this element is not present, the inserted is unformatted, as with any other run of text - it shall not inherit the properties of the placeholder text.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="TestPlaceholderDocPart"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:rPr>
                <w:rStyle w:val="UserName"/>
            </w:rPr>
            …
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:rPr>
                    <w:rStyle w:val="PlaceholderText"/>
                </w:rPr>
                <w:t>[Type Your Name Here]</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    This structured document tag specifies that its current contents are placeholder text via the showingPlcHdr element ([§17.5.2.39]), and that text has the PlaceholderText character style applied to it.
    
    Now, assume that that style created grey shaded text (typical for placeholder text). This formatting would clearly not be desirable for any text entered into the structured document tag. Therefore, when this text is added, the rPr element in the sdtPr is used to store the formatting on the resulting text.
    
    In this example, the text which initially populates the control shall be formatted with the UserName character style. end example]
    
    The W3C XML Schema definition of this element’s content model (CT_RPr) is located in §A.1. Each child element from the above table shall not occur more than once. [Note: This restriction is not reflected in the element's content model due to limitations of W3C XML Schema language. end note]

### 17.5.2.28 rPr (结构化文档标记结束字符运行(run)属性)

**rPr (Structured Document Tag End Character Run Properties)**

=== "中文"
    
    该元素指定应用于用于标识结构化文档标记内容结束的字符的一组运行属性。当应用这些属性时，它们将额外应用于通过标记的主属性容器中存储的 rPr 元素（[§17.5.2.27]）指定的整个结构化文档标记的运行属性。
    
    如果不存在此元素，则插入的闭合标记将与起始标记具有相同的格式。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="TestPlaceholderDocPart"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:rPr>
                <w:rStyle w:val="UserName"/>
            </w:rPr>
            …
        </w:sdtPr>
        <w:sdtEndPr>
            <w:rPr>
                <w:b/>
                <w:i/>
            </w:rPr>
        </w:sdtEndPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    标记属性下的 rPr 元素指定了该结构化文档标记的起始字符必须具有字符样式 UserName 的格式，并且结束字符必须具有字符样式 UserName 以及粗体和斜体的直接格式化。结束示例】
    
    该元素的内容模型（CT_RPr）的 W3C XML Schema 定义位于 §A.1。上表中的每个子元素不得多于一次出现。【注意：由于 W3C XML Schema 语言的限制，此限制未反映在元素的内容模型中。结束注意】

=== "英文"
    
    This element specifies the set of run properties which shall be applied to the character present to delimit the end of the structured document tag's contents. When these properties are applied, they shall be applied in addition to the run properties specified for the entire structured document tag via the rPr element ([§17.5.2.27]) stored in the tag's main property container.
    
    If this element is not present, the inserted closing tag shall be formatting identically to the start tag.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:placeholder>
                <w:docPart w:val="TestPlaceholderDocPart"/>
            </w:placeholder>
            <w:showingPlcHdr/>
            <w:rPr>
                <w:rStyle w:val="UserName"/>
            </w:rPr>
            …
        </w:sdtPr>
        <w:sdtEndPr>
            <w:rPr>
                <w:b/>
                <w:i/>
            </w:rPr>
        </w:sdtEndPr>
        <w:sdtContent>
            …
        </w:sdtContent>
    </w:sdt>
    ```
    
    The rPr elements under the tag's properties specify that this structured document tag specifies that its start character must have formatting in the character style UserName, and that the end character must have the formatting in the character style UserName as well as bold and italic direct formatting. end example]
    
    The W3C XML Schema definition of this element’s content model (CT_RPr) is located in §A.1. Each child element from the above table shall not occur more than once. [Note: This restriction is not reflected in the element's content model due to limitations of W3C XML Schema language. end note]

### 17.5.2.29 sdt (块级结构化文档标签)

**sdt (Block-Level Structured Document Tag)**

=== "中文"
    
    该元素指定一个结构化文档标记，围绕一个或多个块级结构（段落、表格等）。
    
    该元素的两个子元素应通过 sdtPr 和 sdtContent 元素分别用于指定当前结构化文档标记的属性和内容。
    
    【示例：考虑一个友好名称为 "address" 的结构化文档标记，必须位于 WordprocessingML 文档中的单个段落周围。在 WordprocessingML 中，可以如下指定该要求：
    
    ```xml
    <w:body>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="address"/>
            </w:sdtPr>
            <w:sdtContent>
            <w:p>
                …
            </w:p>
            </w:sdtContent>
        </w:sdt>
        …
    </w:body>
    ```
    
    sdt 元素指定了结构化文档标记，子 sdtPr 元素包含了 friendly name 属性，其值为 address，而 sdtContent 元素包含了一个段落（这是一个块级结构化文档标记）。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtBlock) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a structured document tag around one or more block-level structures (paragraphs, tables, etc.). The two child elements of this element shall be used to specify the properties and content of the current structured document tag via the sdtPr and sdtContent elements, respectively.
    
    [Example: Consider a structured document tag with the friendly name address that must be located around a single paragraph in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:body>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="address"/>
            </w:sdtPr>
            <w:sdtContent>
            <w:p>
                …
            </w:p>
            </w:sdtContent>
        </w:sdt>
        …
    </w:body>
    ```
    
    The sdt element specifies the structured document tag, the child sdtPr element contains the friendly name property set to address, and the sdtContent element contains a single paragraph (it is a block-level structured document tag). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtBlock) is located in §A.1. end note]


### 17.5.2.30 sdt (行级结构化文档标签)

**sdt (Row-Level Structured Document Tag)**

=== "中文"
    
    该元素指定了围绕单个表格行的结构化文档标记的存在。该元素的两个子元素将用于通过 sdtPr 和 sdtContent 元素指定当前结构化文档标记的属性和内容，分别是 sdtPr 和 sdtContent 元素。
    
    【示例：考虑一个在 WordprocessingML 文档中围绕单个表格行的友好名称为 "invoiceItem" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:tbl>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="invoiceItem"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tr>
                    …
                </w:tr>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tbl>
    ```
    
    在这个示例中，sdt 元素指定了结构化文档标记，子元素 sdtPr 包含了 friendly name 属性设置为 invoiceItem，而 sdtContent 元素包含了一个表格行（即一个行级结构化文档标记）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtRow) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a structured document tag around a single table row. The two child elements of this element shall be used to specify the properties and content of the current structured document tag via the sdtPr and sdtContent elements, respectively.
    
    [Example: Consider a structured document tag with the friendly name invoiceItem that must be located around a single table row in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:tbl>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="invoiceItem"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tr>
                    …
                </w:tr>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tbl>
    ```
    
    The sdt element specifies the structured document tag, the child sdtPr element contains the friendly name property set to invoiceItem, and the sdtContent element contains a single table row (it is a row-level structured document tag). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtRow) is located in §A.1. end note]

### 17.5.2.31 sdt (内联级结构化文档标签)

**sdt (Inline-Level Structured Document Tag)**

=== "中文"
    
    该元素指定了围绕当前段落中一个或多个内联级结构（例如运行、DrawingML 对象、字段等）的结构化文档标记的存在。该元素的两个子元素将用于通过 sdtPr 和 sdtContent 元素指定当前结构化文档标记的属性和内容。
    
    【示例：考虑一个在 WordprocessingML 文档中围绕两个运行的友好名称为 "firstName" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:p>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="firstName"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:r>
                    …
                </w:r>
                <w:r>
                    …
                </w:r>
            </w:sdtContent>
        </w:sdt>
        …
    </w:p>
    ```
    
    在这个示例中，sdt 元素指定了结构化文档标记，子元素 sdtPr 包含了 friendly name 属性设置为 firstName，而 sdtContent 元素包含了两个运行（即一个内联级结构化文档标记）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtRun) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a structured document tag around one or more inline-level structures (runs, DrawingML objects, fields, etc.) in the current paragraph. The two child elements of this element shall be used to specify the properties and content of the current structured document tag via the sdtPr and sdtContent elements, respectively.
    
    [Example: Consider a structured document tag with the friendly name firstName that must be located around two runs in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:p>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="firstName"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:r>
                    …
                </w:r>
                <w:r>
                    …
                </w:r>
            </w:sdtContent>
        </w:sdt>
        …
    </w:p>
    ```
    
    
    The sdt element specifies the structured document tag, the child sdtPr element contains the friendly name property set to firstName, and the sdtContent element contains two runs (it is an inline-level structured document tag). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtRun) is located in §A.1. end note]

### 17.5.2.32 sdt (单元格级结构化文档标签)

**sdt (Cell-Level Structured Document Tag)**

=== "中文"
    
    该元素指定了围绕单个表格单元格的结构化文档标记的存在。该元素的两个子元素将用于通过 sdtPr 和 sdtContent 元素指定当前结构化文档标记的属性和内容。
    
    【示例：考虑一个在 WordprocessingML 文档中围绕单个表格单元格的友好名称为 "company" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:tr>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="company"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tc>
                    …
                </w:tc>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tr>
    ```
    
    在这个示例中，sdt 元素指定了结构化文档标记，子元素 sdtPr 包含了 friendly name 属性设置为 company，而 sdtContent 元素包含了一个单个表格单元格（即一个单元格级结构化文档标记）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtCell) is located in §A.1. end note]

=== "英文"
    
    This element specifies the presence of a structured document tag around a single table cell. The two child elements of this element shall be used to specify the properties and content of the current structured document tag via the sdtPr and sdtContent elements, respectively.
    
    [Example: Consider a structured document tag with the friendly name company that must be located around a single table cell in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:tr>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="company"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tc>
                    …
                </w:tc>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tr>
    ```
    
    The sdt element specifies the structured document tag, the child sdtPr element contains the friendly name property set to company, and the sdtContent element contains a single table cell (it is a cell-level structured document tag). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtCell) is located in §A.1. end note]

### 17.5.2.33 sdtContent (单元格级结构化文档标签内容)

**sdtContent (Cell-Level Structured Document Tag Content)**

=== "中文"
        
    该元素指定了围绕单个表格单元格的结构化文档标记的最后已知内容。该元素的内容应被视为结构化文档标记中要显示的内容的缓存，原因如下：
    
    - 如果结构化文档标记通过 dataBinding 元素（[§17.5.2.6]）指定了 XML 映射，则应根据需要反映在结构化文档标记中的自定义 XML 数据部分的更改
    - 如果结构化文档标记的内容是通过 showingPlcHdr 元素（[§17.5.2.39]）设置的占位符文本，则此内容可以使用存储在术语表文档部分中的占位符文本进行更新
    
    【示例：考虑一个在 WordprocessingML 文档中围绕单个表格单元格的友好名称为 "company" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:tr>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="company"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tc>
                    …
                </w:tc>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tr>
    ```
    
    sdtContent 元素包含了一个单个表格单元格（即一个单元格级结构化文档标记内容容器）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentCell) is located in §A.1. end note]

=== "英文"
    
    This element specifies the last known contents of a structured document tag around a single table cell. This element's contents shall be treated as a cache of the contents to be displayed in the structured document tag for the following reasons:
    
    - If the structured document tag specifies an XML mapping via the dataBinding element ([§17.5.2.6]), changes to the custom XML data part shall be reflected in the structured document tag as needed
    - If the contents of the structured document tag are placeholder text via the showingPlcHdr element ([§17.5.2.39]), then this content can be updated with the placeholder text stored in the Glossary Document part
    
    [Example: Consider a structured document tag with the friendly name company that must be located around a single table cell in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:tr>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="company"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tc>
                    …
                </w:tc>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tr>
    ```
    
    The sdtContent element contains a single table cell (it is an cell-level structured document tag content container). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentCell) is located in §A.1. end note]

### 17.5.2.34 sdtContent (块级结构化文档标签内容)

**sdtContent (Block-Level Structured Document Tag Content)**

=== "中文"
    
    该元素指定了围绕一个或多个块级结构（段落、表格等）的结构化文档标记的最后已知内容。该元素的内容应被视为结构化文档标记中要显示的内容的缓存，原因如下：
    
    - 如果结构化文档标记通过 dataBinding 元素（[§17.5.2.6]）指定了 XML 映射，则应根据需要反映在结构化文档标记中的自定义 XML 数据部分的更改
    - 如果结构化文档标记的内容是通过 showingPlcHdr 元素（[§17.5.2.39]）设置的占位符文本，则此内容可以使用存储在术语表文档部分中的占位符文本进行更新
    
    【示例：考虑一个在 WordprocessingML 文档中围绕单个段落的友好名称为 "address" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:body>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="address"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:p>
                    …
                </w:p>
            </w:sdtContent>
        </w:sdt>
        …
    </w:body>
    ```
    
    sdtContent 元素包含了一个单个段落（即一个块级结构化文档标记内容容器）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentBlock) is located in §A.1. end note]

=== "英文"
    
    This element specifies the last known contents of a structured document tag around one or more block-level structures (paragraphs, tables, etc.). This element's contents shall be treated as a cache of the contents to be displayed in the structured document tag for the following reasons:
    
    - If the structured document tag specifies an XML mapping via the dataBinding element ([§17.5.2.6]), changes to the custom XML data part shall be reflected in the structured document tag as needed
    - If the contents of the structured document tag are placeholder text via the showingPlcHdr element ([§17.5.2.39]), then this content can be updated with the placeholder text stored in the Glossary Document part
    
    [Example: Consider a structured document tag with the friendly name address that must be located around a single paragraph in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:body>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="address"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:p>
                    …
                </w:p>
            </w:sdtContent>
        </w:sdt>
        …
    </w:body>
    ```
    
    The sdtContent element contains a single paragraph (it is a block-level structured document tag content container). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentBlock) is located in §A.1. end note]

### 17.5.2.35 sdtContent (行级结构化文档标签内容)

**sdtContent (Row-Level Structured Document Tag Content)**

=== "中文"

    该元素指定了围绕单个表格行的结构化文档标记的最后已知内容。
    
    【注意：与其他类型的结构化文档标记不同，这种类型的结构化文档标记不能显示占位符文本或具有映射的 XML 数据，因此它永远不是一个缓存。】
    
    【示例：考虑一个在 WordprocessingML 文档中围绕单个表格行的友好名称为 "invoiceItem" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:tbl>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="invoiceItem"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tr>
                    …
                </w:tr>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tbl>
    ```
    
    sdtContent 元素包含了一个单个表格行（即一个行级别结构化文档标记内容容器）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentRow) is located in §A.1. end note]

=== "英文"

    
    This element specifies the last known contents of a structured document tag around a single table row.
    
    [Note: Unlike other types of structured document tags, this type of structure document tag cannot show placeholder text or have mapped XML data, therefore it is never a cache. end note]
    
    [Example: Consider a structured document tag with the friendly name invoiceItem that must be located around a single table row in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:tbl>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="invoiceItem"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:tr>
                    …
                </w:tr>
            </w:sdtContent>
        </w:sdt>
        …
    </w:tbl>
    ```
    
    The sdtContent element contains a single table row (it is an row-level structured document tag content container). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentRow) is located in §A.1. end note]

### 17.5.2.36 sdtContent (内联级结构化文档标签内容)

**sdtContent (Inline-Level Structured Document Tag Content)**

=== "中文"

    该元素指定了围绕一个或多个内联级别结构（例如运行、DrawingML 对象、字段等）的结构化文档标记的最后已知内容。该元素的内容应被视为结构化文档标记中要显示的内容的缓存，原因如下：
    
    - 如果结构化文档标记通过 dataBinding 元素（[§17.5.2.6]）指定了 XML 映射，则自定义 XML 数据部分的更改应根据需要反映在结构化文档标记中。
    - 如果结构化文档标记的内容是通过 showingPlcHdr 元素（[§17.5.2.39]）作为占位符文本，则此内容可以使用存储在词汇表文档部分中的占位符文本进行更新。
    
    【示例：考虑一个在 WordprocessingML 文档中围绕两个运行的友好名称为 "firstName" 的结构化文档标记。该需求可以在 WordprocessingML 中如下指定：
    
    ```xml
    <w:p>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="firstName"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:r>
                    …
                </w:r>
                <w:r>
                    …
                </w:r>
            </w:sdtContent>
        </w:sdt>
        …
    </w:p>
    ```
    
    sdtContent 元素包含了两个相邻的运行（即一个内联级别的结构化文档标记内容容器）。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentRun) is located in §A.1. end note]

=== "英文"

    
    This element specifies the last known contents of a structured document tag around one or more inline-level structures (runs, DrawingML objects, fields, etc.). This element's contents shall be treated as a cache of the contents to be displayed in the structured document tag for the following reasons:
    
    - If the structured document tag specifies an XML mapping via the dataBinding element ([§17.5.2.6]), changes to the custom XML data part shall be reflected in the structured document tag as needed
    - If the contents of the structured document tag are placeholder text via the showingPlcHdr element ([§17.5.2.39]), then this content can be updated with the placeholder text stored in the Glossary Document part
    
    [Example: Consider a structured document tag with the friendly name firstName that must be located around two runs in a WordprocessingML document. This requirement would be specified as follows in the WordprocessingML:
    
    ```xml
    <w:p>
        <w:sdt>
            <w:sdtPr>
                <w:alias w:val="firstName"/>
            </w:sdtPr>
            <w:sdtContent>
                <w:r>
                    …
                </w:r>
                <w:r>
                    …
                </w:r>
            </w:sdtContent>
        </w:sdt>
        …
    </w:p>
    ```
    
    
    The sdtContent element contains two adjacent runs (it is an inline-level structured document tag content container). end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtContentRun) is located in §A.1. end note]

### 17.5.2.37 sdtEndPr (结构化文档标签结束字符属性)

**sdtEndPr (Structured Document Tag End Character Properties)**

=== "中文"

    该元素指定应用于结构化文档标记结束符的物理字符的属性。
    
    【示例：考虑一个具有以下属性的结构化文档标记的结束标记：
    
    ```xml
    <w:sdtEndPr>
        <w:rPr>
            …
        </w:rPr>
    </w:sdtEndPr>
    ```
    
    此结构化文档标记在 sdtEndPr 元素中指定了其结束字符的属性。】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtEndPr) is located in §A.1. end note]

=== "英文"

    
    This element specifies the properties which shall be applied to the physical character which delimits the end of a structured document tag.
    
    [Example: Consider a structured document tag with the following properties specified for the end tag:
    
    ```xml
    <w:sdtEndPr>
        <w:rPr>
            …
        </w:rPr>
    </w:sdtEndPr>
    ```
    
    
    This structured document tag specifies properties for its end character within the sdtEndPr element. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtEndPr) is located in §A.1. end note]

### 17.5.2.38 sdtPr (结构化文档标签属性)

**sdtPr (Structured Document Tag Properties)**

=== "中文"

    此元素指定应用于最近的祖先结构化文档标记的属性集。
    
    【示例：考虑具有以下属性的结构化文档标记：
    
    ```xml
    <w:sdtPr>
        <w:alias w:val="Birthday"/>
        <w:id w:val="8775518"/>
        <w:date>
            <w:dateFormat w:val="M/d/yyyy"/>
            <w:lid w:val="EN-US"/>
        </w:date>
    </w:sdtPr>
    ```
    
    此结构化文档标记指定了三个属性：通过别名(alias)元素（[§17.5.2.1]）指定了友好名称为Birthday，通过ID(id)元素（[§17.5.2.18]）指定了唯一ID为8775518，通过日期(date)元素（[§17.5.2.7]）指定了日期选择器类型的结构化文档标记，日期元素本身具有一组日期特定的属性。结束示例】
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtPr) is located in §A.1. end note]

=== "英文"

    
    This element specifies the set of properties that shall be applied to the nearest ancestor structured document tag.
    
    [Example: Consider a structured document tag with the following properties specified:
    
    ```xml
    <w:sdtPr>
        <w:alias w:val="Birthday"/>
        <w:id w:val="8775518"/>
        <w:date>
            <w:dateFormat w:val="M/d/yyyy"/>
            <w:lid w:val="EN-US"/>
        </w:date>
    </w:sdtPr>
    ```
    
    This structured document tag specifies three properties: the a friendly name of Birthday via the alias element ([§17.5.2.1]), a unique ID of 8775518 via the id element (【§17.5.2.18), and a structured document tag type of date picker via the date element (【§17.5.2.7) which itself has a set of date-specific properties. end example]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtPr) is located in §A.1. end note]

### 17.5.2.39 showingPlcHdr (当前内容是占位符文本)

**showingPlcHdr (Current Contents Are Placeholder Text)**

=== "中文"

    该元素指定了最近祖先结构化文档标记的sdtContent元素（[§17.5.2.34]; [§17.5.2.33]; [§17.5.2.35]; [§17.5.2.36]）的内容是否应被解释为此结构化文档标记的占位符文本（而不是结构化文档标记内的常规文本内容）。如果存在此元素并设置为true，则在打开此文档时应继续此状态（显示占位符文本）。
    
    如果省略此元素，则在显示文档时不应解释为显示占位符文本的结构化文档标记。
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:showingPlcHdr/>
            …
            <w:richText/>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>[在此处输入您的姓名]</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    此结构化文档标记具有运行内容，读取[在此处输入您的姓名]，通常会被解释为结构化文档标记的当前内容。然而，由于在结构化文档标记的属性中指定了showingPlcHdr元素，因此必须将此内容解释为结构化文档标记的占位符文本。结束示例】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"

    
    This element specifies whether the content of the sdtContent element ([§17.5.2.34]; [§17.5.2.33]; [§17.5.2.35]; [§17.5.2.36]) for the nearest ancestor structured document tag shall be interpreted to contain placeholder text for this structured document tag (as opposed to regular text contents within the structured document tag). If this element is present and set to true, this state shall be resumed (showing placeholder text) upon opening this document.
    
    
    If this element is omitted, then the structured document tag shall not be interpreted to be showing placeholder text when the document is displayed.
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:showingPlcHdr/>
            …
            <w:richText/>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>[Type your name here]</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    
    This structured document tag has run contents which read [Type your name here], which would typically be interpreted as the current contents of the structured document tag. However, since the showingPlcHdr element has been specified in the structured document tag's properties, this content must instead be interpreted as the placeholder text for the structured document tag. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

### 17.5.2.40 storeMappedDataAs (自定义 XML 数据日期存储格式)

**storeMappedDataAs (Custom XML Data Date Storage Format)**

=== "中文"
    
    
    该元素指定在将当前内容保存到关联的自定义 XML 数据时，在日期选择器结构化文档标记中显示的日期上执行的翻译。此操作通过 dataBinding 元素（[§17.5.2.6]）执行。
    
    如果省略此元素，则关联的自定义 XML 元素的值将直接放入自定义 XML 数据部分，不进行任何翻译。
    
    【示例：考虑以下日期选择器结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:date w:fullDate="01-01-2006T06:30:00Z">
                <w:storeMappedDateAs w:val="text"/>
                …
            </w:date>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>January 1</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
    
    storeMappedDateAs 元素的属性值为 text，因此当前的运行内容必须以原样发送到映射的 XML 元素，不进行任何翻译（在此情况下，值必须为 January 1）。结束示例】
    
    ??? abstract "属性"
    
        **val**（日期存储类型）
    
        :   指定将应用于父日期选择器结构化文档标记的日期翻译。
    
            如果省略此属性，则假定其值为 text。
            
            【示例：考虑以下日期选择器结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:date … >
                        <w:storeMappedDateAs w:val="date"/>
                        …
                    </w:date>
                </w:sdtPr>
                <w:sdtContent>
                    <w:r>
                        <w:t>January 1</w:t>
                    </w:r>
                </w:sdtContent>
            </w:sdt>
            ```
            
            val 属性的值为 text，则当前的运行内容必须在翻译为 xsd:date 格式后发送到映射的 XML 元素（在此情况下，值必须为 01-01-2006）。结束示例】
            
            此属性的可能值由 ST_SdtDateMappingType 简单类型定义（[§17.18.76]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDateMappingType) is located in §A.1. end note]

=== "英文"
    
    
    This element specifies the translation which shall be performed on the displayed date in a date picker structured document tag when the current contents are saved into the associated custom XML data via the dataBinding element ([§17.5.2.6]).
    
    If this element is omitted, then the value of the associated custom XML element shall be placed into the custom XML data part with no translation.
    
    [Example: Consider the following date picker structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:date w:fullDate="01-01-2006T06:30:00Z">
                <w:storeMappedDateAs w:val="text"/>
                …
            </w:date>
        </w:sdtPr>
        <w:sdtContent>
            <w:r>
                <w:t>January 1</w:t>
            </w:r>
        </w:sdtContent>
    </w:sdt>
    ```
     
    The value of the storeMappedDateAs element's attribute value is text, therefore the current run contents must be sent to the mapped XML element without any translation (in this case, the value must be January 1). end example]
    
    ??? abstract "Attributes"
    
        **val** (Date Storage Type)
    
        :   Specifies the date translation which shall be applied to the parent date picker structured document tag.
    
            If this attribute is omitted, this its value shall be assumed to be text.
            
            [Example: Consider the following date picker structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    <w:date … >
                        <w:storeMappedDateAs w:val="date"/>
                        …
                    </w:date>
                </w:sdtPr>
                <w:sdtContent>
                    <w:r>
                        <w:t>January 1</w:t>
                    </w:r>
                </w:sdtContent>
            </w:sdt>
            ```
            
            The value of the val attribute is text, therefore the current run contents must be sent to the mapped XML element after being translated into xsd:date format (in this case, the value must be 01-01-2006). end example]
            
            The possible values for this attribute are defined by the ST_SdtDateMappingType simple type ([§17.18.76]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtDateMappingType) is located in §A.1. end note]

### 17.5.2.41 tabIndex (结构化文档标签导航顺序索引)

**tabIndex (Structured Document Tag Navigation Order Index)**

=== "中文"
    
    该元素指定当前结构化文档标记在文档中使用的导航（Tab）顺序中的位置。索引将存储在此元素的 val 属性上，类似于 HTML 中的 tabIndex 属性。
    
    支持 Tab 键索引的对象将由消费者按以下顺序进行导航：
    
    - XML 指定非零 tabIndex 值的对象首先进行导航。导航从具有最低解析值的 tabIndex 的元素开始，到具有最高解析值的 tabIndex 的元素结束。
        - 指定相同的解析 tabIndex 值的对象按照它们在底层 WordprocessingML 中出现的词法顺序进行导航。
    - XML 不指定索引的对象或 XML 指定解析 tabIndex 值为 0 的对象最后进行导航。这些对象按照它们在底层 WordprocessingML 中出现的词法顺序进行导航。
    
    【示例：考虑以下两个结构化文档标记，其中每个结构化文档标记都指定了一个 tab 索引：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
            <w:tabIndex w:val="1" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>First Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="6" />
            <w:tabIndex w:val="2" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>Last Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    ```
    
    tabIndex 元素指定了具有标识值为 5 的结构化文档标记必须是通过 Tab 键到达的第一个内容，而具有标识值为 6 的结构化文档标记必须是通过 Tab 键到达的第二个内容。结束示例】
    
    ??? abstract "属性"
    
        **val**（正十进制数值）
    
        :   指定此属性的内容包含一个正十进制数。
    
            此正十进制数的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑类型为 ST_UnsignedDecimalNumber 的以下数值 WordprocessingML 属性：
            
            ```xml
            <… w:val="15" />
            ```
            
            val 属性的值是一个十进制数，其值必须根据父元素的上下文进行解释。结束示例】
            
            此属性的可能值由 ST_UnsignedDecimalNumber 简单类型定义（[§22.9.2.16]）。
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_UnsignedDecimalNumber) is located in §A.1. end note]

=== "英文"
    
    This element specifies the position of the current structured document tag in the navigation (tab) order used in the document. The index shall be stored on this element’s val attribute and is analogous to the tabIndex attribute in HTML.
    
    Objects that support tab index shall be navigated by consumers in the following order:
    
    - Objects for which the XML specifies a non-zero tabIndex value are navigated first. Navigation proceeds with the element with the lowest resolved value of tabIndex to the element with the highest resolved value of tabIndex.
        - Objects that specify identical resolved values of tabIndex is navigated in the lexical order in which the elements appear in the underlying WordprocessingML.
    - Objects for which the XML does not specify an index or objects for which the XML specifies a resolved tabIndex value of 0 are navigated last. These objects are navigated in the lexical order in which they appear in the underlying WordprocessingML.
    
    [Example: Consider the following two structured document tags where each structured document tag specifies a tab index:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="5" />
            <w:tabIndex w:val="1" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>First Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    …
    <w:sdt>
        <w:sdtPr>
            <w:id w:val="6" />
            <w:tabIndex w:val="2" />
        </w:sdtPr>
        <w:sdtContent>
            <w:p>
                <w:r>
                    <w:t>Last Name</w:t>
                </w:r>
            </w:p>
        </w:sdtContent>
    </w:sdt>
    ```
    
    The tabIndex element specifies that the structured document tag with an identifier value of 5 must be the first content to be reached via tabbing, whereas the structured document tag with an identifier value of 6 must be the second content to be reached via tabbing. end example]
    
    ??? abstract "Attributes"
    
        **val** (Positive Decimal Number Value)
    
        :   Specifies that the contents of this attribute contains a positive decimal number.
    
            The contents of this positive decimal number are interpreted based on the context of the parent XML element.
            
            [Example: Consider the following numeric WordprocessingML property of type ST_UnsignedDecimalNumber:
            
            ```xml
            <… w:val="15" />
            ```
            
            The value of the val attribute is a decimal number whose value must be interpreted in the context of the parent element. end example]
            
            The possible values for this attribute are defined by the ST_UnsignedDecimalNumber simple type ([§22.9.2.16]).
            
    [Note: The W3C XML Schema definition of this element’s content model (CT_UnsignedDecimalNumber) is located in §A.1. end note]


### 17.5.2.42 tag (程序化标签)

**tag (Programmatic Tag)**

=== "中文"
    
    该元素指定与当前结构化文档标记关联的编程标记。编程标记是一个任意的字符串，应用程序可以将其与结构化文档标记相关联，以便在不提供可见友好名称的情况下对其进行识别。表示编程标记的字符串将存储在此元素的 val 属性上。
    
    如果省略此元素，则不会将编程标记与给定的结构化文档标记关联起来。
    
    【示例：考虑结构化文档标记的以下属性：
    
    ```xml
    <w:sdtPr>
        <w:tag w:val="Clause_3246"/>
        …
    </w:sdtPr>
    ```
    
    通过 tag 元素，此属性集指定了最近祖先结构化文档标记的编程标记必须为 Clause_3246。然后，应用程序可以根据需要使用此信息。结束示例】
    
    ??? abstract "属性"
    
        **val**（字符串值）
    
        :   指定其内容包含一个字符串。
    
            此字符串的内容根据父 XML 元素的上下文进行解释。
            
            【示例：考虑以下 WordprocessingML 片段：
            
            ```xml
            <w:pPr>
                <w:pStyle w:val="Heading1" />
            </w:pPr>
            ```
            
            val 属性的值是关联段落样式的 styleId 的 ID。
            
            但是，考虑以下片段：
            
            ```xml
            <w:sdtPr>
                <w:alias w:val="SDT Title Example" />
                …
            </w:sdtPr>
            ```
            
            在这种情况下，val 属性中的十进制数是最近祖先结构化文档标记的标题。在每种情况下，该值都是根据父元素的上下文进行解释的。结束示例】
            
            此属性的可能值由 ST_String 简单类型定义（[§22.9.2.13]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_String) is located in §A.1. end note]

=== "英文"
    
    This element specifies a programmatic tag associated with the current structured document tag. A programmatic tag is an arbitrary string which applications can associate with a structured document tag in order to identify it without providing a visible friendly name. The string representing the programmatic tag shall be stored on this element's val attribute.
    
    If this element is omitted, then no programmatic tag shall be associated with the given structured document tag.
    
    [Example: Consider the following properties on a structured document tag:
    
    ```xml
    <w:sdtPr>
        <w:tag w:val="Clause_3246"/>
        …
    </w:sdtPr>
    ```
    
    
    This set of properties specifies via the tag element that the programmatic tag for the nearest ancestor structured document tag must be Clause_3246. This information can then be used as needed by applications. end example]
    
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


### 17.5.2.43 temporary (编辑内容时删除结构化文档标签)

**temporary (Remove Structured Document Tag When Contents Are Edited)**

=== "中文"
    
    该元素指定在其内容被修改时，最近祖先结构化文档标记是否应该从 WordprocessingML 文档中移除。
    
    【注：此设置主要用于创建仅用于一次性占位文本的结构化文档标记，一旦替换为内容，就不应再返回。结束注】
    
    如果省略此元素，则在其内容被修改时，最近祖先结构化文档标记不会被自动移除。
    
    【示例：考虑以下纯文本结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:temporary/>
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    该纯文本结构化文档标记的属性包含一个 temporary 元素，指定只要其内容首次被修改，结构化文档标记本身必须从文档中删除。结束示例】
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

=== "英文"
    
    This element specifies whether the nearest ancestor structured document tag shall be removed from the WordprocessingML document when the its contents are modified.
    
    [Note: This setting is primarily intended for creating structured document tags whose sole purpose is one-time placeholder text, and which should not return once replaced with content. end note]
    
    If this element is omitted, then the nearest ancestor structured document tag shall not be automatically removed when its contents are modified.
    
    [Example: Consider the following plain text structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            <w:temporary/>
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    This plain text structured document tag's properties contain a temporary element, specifying that the structured document tag itself must be deleted from the document whenever its contents are first modified. end example]
    
    This element’s content model is defined by the common boolean property definition in [§17.17.4].

### 17.5.2.44 text (纯文本结构化文档标签)

**text (Plain Text Structured Document Tag)**

=== "中文"
    
    该元素指定，在文档中显示时，最近祖先结构化文档标记将是一个纯文本框。
    
    此设置指定了此结构化文档标记的行为应如下：
    
    - 应用于此结构化文档标记内容的任何部分的格式应该应用于其整个内容
    此外，结构化文档标记应满足以下限制，否则文档将被视为非符合性的：
    
    - 内容只能包含单个运行（一组格式属性），但可以通过此元素上的 multiLine 属性包含软换行符
    - 内容不能包含多个段落或表格单元格，并且不能包含表行或表
    
    【示例：考虑以下结构化文档标记：
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    该结构化文档标记的属性中的 text 元素指定结构化文档标记的类型为纯文本框。结束示例】
    
    ??? abstract "属性"
    
        **multiLine**（允许软换行）
    
        :   指定在修改文档时是否可以向此结构化文档标记的内容添加软换行符。此设置不应影响结构化文档标记显示现有软换行符的能力（应予保留），并且只应在应用程序修改文档时影响添加换行符的能力。
    
            如果省略此属性，则父级纯文本结构化文档控件将不允许在其内容中添加软换行符。
            
            【示例：考虑以下结构化文档标记：
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    …
                    <w:text w:multiLine="true"/>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            此结构化文档标记的属性中的 text 元素上的 multiLine 属性指定应用程序可以向结构化文档标记的运行内容添加软换行符。结束示例】
            
            此属性的可能值由 ST_OnOff 简单类型定义（[§22.9.2.7]）。
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtText) is located in §A.1. end note]

=== "英文"
    
    This element specifies that the nearest ancestor structured document tag shall be a plain text box when displayed in the document.
    
    This setting specifies that the behavior for this structured document tag shall be as follows:
    
    - Formatting applied to any part of this structured document tag's contents shall apply to its entire
    contents
    As well, the structured document tag shall satisfy the following restraints or the document shall be considered non-conformant:
    
    - The contents shall only be contain a single run (one set of formatting properties) with exceptions for soft carriage returns via the multiLine attribute on this element
    - The contents shall not contain more than a single paragraph or table cell and shall not contain a table row or table
    
    [Example: Consider the following structured document tag:
    
    ```xml
    <w:sdt>
        <w:sdtPr>
            …
            <w:text/>
        </w:sdtPr>
        …
    </w:sdt>
    ```
    
    The text element in this structured document tag's properties specify that the kind of structured document tag is a plain text box. end example]
    
    ??? abstract "Attributes"
    
        **multiLine** (Allow Soft Line Breaks)
    
        :   Specifies whether soft line breaks can be added to the contents of this structured document tag when this document is modified. This setting shall not affect the ability of the structured document tag to display existing soft line breaks (which shall be preserved) and shall only affect the ability to add line breaks when the document is modified by an application.
    
            If this attribute is omitted, then the parent plain text structured document control shall not allow soft line breaks to be added to its contents.
            
            [Example: Consider the following structured document tag:
            
            ```xml
            <w:sdt>
                <w:sdtPr>
                    …
                    <w:text w:multiLine="true"/>
                </w:sdtPr>
                …
            </w:sdt>
            ```
            
            The multiLine attribute on the text element in this structured document tag's properties specify that an application can allow soft line breaks to be added to the run contents of the structured document tag. end example]
            
            The possible values for this attribute are defined by the ST_OnOff simple type ([§22.9.2.7]).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SdtText) is located in §A.1. end note]

[§17.5.1]: #1751-自定义-xml-和智能标签
[§17.5.1.1]: #17511-attr-自定义-xml-属性
[§17.5.1.2]: #17512-attr-智能标签属性
[§17.5.1.3]: #17513-customxml-内联级自定义-xml-元素
[§17.5.1.4]: #17514-customxml-单元格级自定义-xml-元素
[§17.5.1.5]: #17515-customxml-行级自定义-xml-元素
[§17.5.1.6]: #17516-customxml-块级自定义-xml-元素
[§17.5.1.7]: #17517-customxmlpr-自定义-xml-元素属性
[§17.5.1.8]: #17518-placeholder-自定义-xml-元素占位符文本
[§17.5.1.9]: #17519-smarttag-内联级智能标签
[§17.5.1.10]: #175110-smarttagpr-智能标签属性
[§17.5.2]: #1752-结构化文档标签
[§17.5.2.1]: #17521-alias-友好名称
[§17.5.2.2]: #17522-bibliography-参考目录结构化文档标签
[§17.5.2.3]: #17523-calendar-日期选择器日历类型
[§17.5.2.4]: #17524-citation-引文结构化文档标签
[§17.5.2.5]: #17525-combobox-组合框结构化文档标签
[§17.5.2.6]: #17526-databinding-xml映射
[§17.5.2.7]: #17527-date-日期结构化文档标签
[§17.5.2.8]: #17528-dateformat-日期显示水印
[§17.5.2.9]: #17529-docpart-文档部件参考
[§17.5.2.10]: #175210-docpartcategory-文档部件类别过滤器
[§17.5.2.11]: #175211-docpartgallery-文档部件图库过滤器
[§17.5.2.12]: #175212-docpartlist-文档部件图库结构化文档标签
[§17.5.2.13]: #175213-docpartobj-内置文档部件结构化文档标签
[§17.5.2.14]: #175214-docpartunique-内置文档部件
[§17.5.2.15]: #175215-dropdownlist-下拉列表结构化文档标签
[§17.5.2.16]: #175216-equation-方程结构化文档标签
[§17.5.2.17]: #175217-group-分组结构化文档标签
[§17.5.2.18]: #175218-id-唯一id
[§17.5.2.19]: #175219-label-结构化文档标签label
[§17.5.2.20]: #175220-lid-日期选择器语言-id
[§17.5.2.21]: #175221-listitem-组合框列表项
[§17.5.2.22]: #175222-listitem-下拉列表项
[§17.5.2.23]: #175223-lock-锁定设置
[§17.5.2.24]: #175224-picture-图片结构化文档标签
[§17.5.2.25]: #175225-placeholder-结构化文档标签占位符文本
[§17.5.2.26]: #175226-richtext-富文本结构化文档标签
[§17.5.2.27]: #175227-rpr-结构化文档标签内容的运行run属性
[§17.5.2.28]: #175228-rpr-结构化文档标记结束字符运行run属性
[§17.5.2.29]: #175229-sdt-块级结构化文档标签
[§17.5.2.30]: #175230-sdt-行级结构化文档标签
[§17.5.2.31]: #175231-sdt-内联级结构化文档标签
[§17.5.2.32]: #175232-sdt-单元格级结构化文档标签
[§17.5.2.33]: #175233-sdtcontent-单元格级结构化文档标签内容
[§17.5.2.34]: #175234-sdtcontent-块级结构化文档标签内容
[§17.5.2.35]: #175235-sdtcontent-行级结构化文档标签内容
[§17.5.2.36]: #175236-sdtcontent-内联级结构化文档标签内容
[§17.5.2.37]: #175237-sdtendpr-结构化文档标签结束字符属性
[§17.5.2.38]: #175238-sdtpr-结构化文档标签属性
[§17.5.2.39]: #175239-showingplchdr-当前内容是占位符文本
[§17.5.2.40]: #175240-storemappeddataas-自定义-xml-数据日期存储格式
[§17.5.2.41]: #175241-tabindex-结构化文档标签导航顺序索引
[§17.5.2.42]: #175242-tag-程序化标签
[§17.5.2.43]: #175243-temporary-编辑内容时删除结构化文档标签
[§17.5.2.44]: #175244-text-纯文本结构化文档标签


[§17.3.1.19]: ./03paragraphs.md#173119-numpr-编号定义实例参考

[§17.12.12]: ./12glossary.md#171212-name-分类关联的条目

[§17.15.1.5]: ./15settings.md#171515-attachedschema-附加自定义-xml-架构

[§17.16.4.1]: ./16fields.md#171641-日期和时间格式

[§17.17.4]: ./17miscellaneous.md#17174-布尔属性-ct_onoff


[§17.18.10]: ./18simpletypes.md#171810-st_decimalnumber-十进制数值
[§17.18.49]: ./18simpletypes.md#171849-st_lock-锁定类型
[§17.18.76]: ./18simpletypes.md#171876-st_sdtdatemappingtype-日期存储格式类型

[§20.1]: ../chapter20/main/index.md

[§22.9.2.1]: ../chapter22/sharedsimpletypes.md#22921-st_calendartype-日历类型
[§22.9.2.4]: ../chapter22/sharedsimpletypes.md#22924-st_guid-128-bit-guid
[§22.9.2.6]: ../chapter22/sharedsimpletypes.md#22926-st_lang-语言参考
[§22.9.2.7]: ../chapter22/sharedsimpletypes.md#22927-st_onoff-开关值
[§22.9.2.8]: ../chapter22/sharedsimpletypes.md#22928-st_panose-panose-1整数
[§22.9.2.9]: ../chapter22/sharedsimpletypes.md#22929-st_percentage-带符号的百分比值
[§22.9.2.13]: ../chapter22/sharedsimpletypes.md#229213-st_string-字符串
[§22.9.2.14]: ../chapter22/sharedsimpletypes.md#229214-st_twipsmeasure-以二十分之一点为单位的测量
[§22.9.2.16]: ../chapter22/sharedsimpletypes.md#229216-st_unsigneddecimalnumber-无符号十进制数值
[§22.9.2.18]: ../chapter22/sharedsimpletypes.md#229218-st_xalign-水平对齐位置
[§22.9.2.20]: ../chapter22/sharedsimpletypes.md#229220-st_yalign-垂直对齐位置
[§22.9.2.21]: ../chapter22/sharedsimpletypes.md#229221-st_xmlname-xml-名称