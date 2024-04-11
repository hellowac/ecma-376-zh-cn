# 22.5 自定义 XML Data 属性

=== "中文"

    此命名空间定义可与 Office Open XML 文档中的一个或多个自定义 XML 部分关联的一组属性。 自定义 XML 部件是 Office Open XML 文档中的一部分，它包含不一定由 ECMA-376 定义的任意自定义 XML 标记，并且独立于包内的特定于表示的标记。

    [基本原理: 通常需要在 Office Open XML 文档中包含自定义 XML 语义，以便将一组复杂的属性（例如文档管理系统的元数据）与文件一起存储。 此机制允许此自定义 XML 以独立于文档类型且与表示标记分离的方式存储在文档中 — 只有自定义 XML 存储在该部件中。 ]
    
    可应用于自定义 XML 部件的属性有：
    
    - 部件ID
    - (可选) 一个或多个关联的自定义 XML Schemas

=== "英文"

    **Custom XML Data Properties**

    This namespace defines the set of properties that can be associated with one or more custom XML parts within an Office Open XML document. A custom XML part is a part within an Office Open XML document, that contains arbitrary custom XML markup not necessarily defined by ECMA-376, and which is kept independent from the presentation-specific markup within the package.

    [Rationale: It is often necessary to include custom XML semantics with an Office Open XML document, to store a complex set of properties (e.g., a document management system's metadata) along with the file. This mechanism allows this custom XML to be stored in the document in a way that is independent of the type of document and separate from the presentation markup—only the custom XML is stored in this part. end rationale]
    
    The properties that can be applied to a custom XML part are:
    
    - A part ID
    - (optionally) One or more associated custom XML schemas

## 22.5.1 目录

This subclause is informative.

- 22.5.2 Elements
- 22.5.2.1 datastoreItem (Custom XML Data Properties)
- 22.5.2.2 schemaRef (Associated XML Schema)
- 22.5.2.3 schemaRefs (Set of Associated XML Schemas)

End of informative text.

### 22.5.2 元素

=== "中文"

    以下信息描述了该命名空间中的元素:

=== "英文"

    **Elements**
    
    The following information describes the elements in this namespace:

### 22.5.2.1 datastoreItem (自定义XML数据属性)

=== "中文"

    此元素指定 Office Open XML 文档内单个自定义 XML 部分的属性。 此元素中指定的属性集附加到指定与此部分的关系的自定义 XML 部分。
    
    !!! info "Example"
    
        对于自定义 XML 部件属性部件，请考虑以下内容:
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        datastoreItem 元素包含引用它的自定义 XML 部分的属性； 具体来说，部件 ID 为 `A67AC88A-A164-4ADE-8889-8826CE44DE6E`，以及对目标命名空间为 `http://www.example.com/exampleSchema` 的架构的单个 XML 架构引用
    
    
    <table border=1>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>itemID (自定义 XML 数据 ID) </td>
                <td>
                    指定**全局唯一标识符** (GUID)，用于唯一标识 Office Open XML 文档中的单个自定义 XML 部分. <br/><br/>
                    每个 itemID 值在本文档中的所有自定义 XML 数据部分中应是唯一的。 如果文档包含重复的 itemID 值，则应保留第一个值，并重新分配后续值.<br/><br/>
                    [Example: 对于自定义 XML 部件属性部件，请考虑以下内容: <br/><br/>
                    `<w:datastoreItem w:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">`<br/>
                    `…`<br/>
                    `</w:datastoreItem>`<br/><br/>
                    itemID 属性指定与父级的自定义 XML 部件关联的 ID 为 A67AC88A-A164-4ADE-8889-8826CE44DE6E。 end example] <br/><br/>
                    该属性的可能值由 ST_Guid 简单类型定义 (§22.9.2.4).
                </td>
            </tr>
        </tbody>
    </table>

    !!! info "Note"

        该元素内容模型 (CT_DatastoreItem) 的 W3C XML 架构定义位于 [§A.6.5] 中。

=== "英文"

    **datastoreItem (Custom XML Data Properties)**

    This element specifies the properties for a single custom XML part inside of an Office Open XML document. The set of properties specified within this element are attached to the custom XML part that specifies a relationship to this part.
    
    !!! info "Example"
    
        Consider the following content for a custom XML part properties part:
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        The datastoreItem element contains the properties for the custom XML part that referenced it; specifically, a part ID of A67AC88A-A164-4ADE-8889-8826CE44DE6E, and a single XML Schema reference to a schema with a target namespace of http://www.example.com/exampleSchema. 
    
    
    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>itemID (Custom XML Data ID) </td>
                <td>
                    Specifies a globally unique identifier (GUID) that uniquely identifies a single custom XML part within an Office Open XML document. <br/><br/>
                    Each itemID value shall be unique among all custom XML data parts in this document. If a document contains duplicate itemID values, then the first value should be persisted, and subsequent values should be reassigned.<br/><br/>
                    [Example: Consider the following content for a custom XML part properties part: <br/><br/>
                    `<w:datastoreItem w:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">`<br/>
                    `…`<br/>
                    `</w:datastoreItem>`<br/><br/>
                    The itemID attribute specifies that the ID associated with the parent custom XML part is A67AC88A-A164-4ADE-8889-8826CE44DE6E. end example] <br/><br/>
                    The possible values for this attribute are defined by the ST_Guid simple type (§22.9.2.4).
                </td>
            </tr>
        </tbody>
    </table>

    !!! info "Note"

        The W3C XML Schema definition of this element’s content model (CT_DatastoreItem) is located in §A.6.5. 

### 22.5.2.2 schemaRef (关联的XML模式)

=== "中文"

    此元素指定与自定义 XML 数据部分关联的单个 XML 架构。 该 XML 模式使用其目标名称空间进行标识，并且可以通过处理该文件内容的应用程序可用的任何方式进行定位。
    
    如果自定义 XML 部分在打开时无法使用指定的 XML 架构进行验证，则在随后保存文件时可以忽略此引用。
    
    !!! info "Example"
    
        对于自定义 XML 部件属性部件，请考虑以下内容:
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        schemaRef 元素包含对目标名称空间为 `http://www.example.com/exampleSchema` 的模式的单个 XML 模式引用, 然后，应用程序可以使用任何可用的方式找到并利用该名称空间的模式。
    
    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>uri (关联 XML 模式的目标命名空间) </td>
                <td>
                    指定与此架构引用关联的 XML 架构的目标命名空间. <br/><br/>
                    [Example: 对于自定义 XML 部件属性部件，请考虑以下内容: <br/><br/>
                    `…`<br/>
                    `<w:schemaRef w:uri="http://www.example.com/schema1" />`<br/>
                    `<w:schemaRef w:uri="http://www.example.com/schema2" />`<br/>
                    `…`<br/><br/>
                    uri 属性指定每个 XML 模式引用的目标命名空间: <br/><br/>
                    <ul>
                        <li>http://www.example.com/schema1</li>
                        <li>http://www.example.com/schema2</li>
                    </ul>
                    然后，应用程序可以使用任何可用的方式找到并利用这些命名空间的模式。 end example]<br/><br/>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_DatastoreSchemaRef) 的 W3C XML 模式定义位于 [§A.6.5] 中。 end note]

=== "英文"

    **schemaRef (Associated XML Schema)**

    This element specifies a single XML schema that is associated with the custom XML data part. This XML schema is identified using its target namespace, and can be located via any means available to an application processing the contents of this file.
    
    If the custom XML part cannot be validated using the specified XML schema when it is opened, then this reference can be omitted when the file is subsequently saved.
    
    !!! info "Example"
    
        Consider the following content for a custom XML part properties part:
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        The schemaRef element contains a single XML Schema reference to a schema with a target namespace of http://www.example.com/exampleSchema. Applications can then locate and utilize a schema for this namespace using any means available.
    
    
    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>uri (Target Namespace of Associated XML Schema) </td>
                <td>
                    Specifies the target namespace for the XML Schema associated with this schema reference. <br/><br/>
                    [Example: Consider the following content for a custom XML part properties part: <br/><br/>
                    `…`<br/>
                    `<w:schemaRef w:uri="http://www.example.com/schema1" />`<br/>
                    `<w:schemaRef w:uri="http://www.example.com/schema2" />`<br/>
                    `…`<br/><br/>
                    The uri attribute specifies the target namespace of each XML schema reference: <br/><br/>
                    <ul>
                        <li>http://www.example.com/schema1</li>
                        <li>http://www.example.com/schema2</li>
                    </ul>
                    Applications can then locate and utilize a schema for these namespaces using any means available. end example]<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_DatastoreSchemaRef) is located in [§A.6.5]. end note]

### 22.5.2.3 schemaRefs (关联的 XML 模式集)

=== "中文"

    此元素指定与父自定义 XML 部件关联的 XML 模式(Schema)集。 可以引用任意数量的 XML 模式，然后使用该模式集合来验证相应自定义 XML 部件的内容。 
    如果存在此元素，则应使用其中提供的一组 XML 模式来验证相应自定义 XML 部件的内容（包括明确不存在任何子元素，以指定不应使用任何自定义 XML 模式，即使其中一个是预置的）。
    
    如果省略此元素，则应用程序可以使用任何所需的方式确定用于验证此部分内容的 XML 模式集
    
    !!! info "Example"
    
        请考虑自定义 XML 部件属性部件的以下内容：
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        schemaRefs 元素包含一组可用于验证此部件内容的 XML 模式引用。
    
    [Note: 该元素内容模型 (CT_DatastoreSchemaRefs) 的 W3C XML 模式定义位于 [§A.6.5] 中。 end note]

=== "英文"

    **schemaRefs (Set of Associated XML Schemas)**

    This element specifies the set of XML schemas that are associated with the parent custom XML part. Any number of XML schemas can be referenced, and this collection of schemas shall then be used to validate the contents of the corresponding custom XML part. If this element is present, then the set of XML schemas provided within should be used to validate the contents of the corresponding custom XML part (including the explicit presence of no child elements to specify that no custom XML schemas should be used even if one is present).
    
    If this element is omitted, then applications can determine the set of XML schemas to be used to validate the contents of this part using any desired means
    
    !!! info "Example"
    
        Consider the following content for a custom XML part properties part:
    
        ```xml
        <ds:datastoreItem ds:itemID="{A67AC88A-A164-4ADE-8889-8826CE44DE6E}">
            <ds:schemaRefs>
                <ds:schemaRef ds:uri="http://www.example.com/exampleSchema" />
            </ds:schemaRefs>
        </ds:datastoreItem>
        ```
        
        The schemaRefs element contains the set of XML Schema references that can be used to validate the contents of this part. 
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_DatastoreSchemaRefs) is located in [§A.6.5]. end note]
