# 23. 自定义 XML Schema参考

=== "中文"

    此命名空间定义一组属性，这些属性定义与存储在 Office Open XML 文档内容中的一个或多个自定义 XML 架构关联的位置和属性。 与文档的自定义 XML 标记关联的一组架构统称为该文档的schema库。 然后，schema库存储文档的自定义 XML 标记中使用的一组唯一 XML 命名空间，并允许应用程序使用适当的元数据“标记(tag)”这些命名空间。

=== "英文"

    **Custom XML Schema References**

    This namespace defines the set of properties which define the location and properties associated with one or more custom XML schemas which have been stored within the contents of a Office Open XML document. Collectively, the set of schemas associated with a document's custom XML markup are referred to as that document's schema library. The schema library then stores the set of unique XML namespaces used within the document's custom XML markup, and allows applications to 'tag' these namespaces with appropriate metadata.

## 23.2 元素

=== "中文"

    以下信息描述了此命名空间中的元素：

=== "英文"

    **Elements**

    The following information describes the elements in this namespace:

### 23.2.1 schema (Custom XML Schema Reference)

=== "中文"

    该元素指定与单个 XML 命名空间关联的属性，应为其加载所有已知的 XML 模式，以便验证存储在该文档中的自定义 XML 标记。 可以适当地使用这些属性来定位与文档一起使用的自定义 XML 模式。 ECMA-376 不需要任何特定的 XML 模式语言。
    
    !!! info "Note"
    
        可用于实现自定义 XML 映射的 XML 架构语言的一些示例包括：

    - W3C XML Schema - http://www.w3.org/XML/Schema
    - RELAX NG – ISO/IEC 19757-2
    - Schematron – ISO/IEC 19757-3
    - NVDL – ISO/IEC 19757-4
  
    !!! info "Example"
    
        考虑一个在 http://www.example.com 命名空间中包含自定义 XML 标记的 WordprocessingML 文档。 文档的模式库数据中将显示以下内容：

        ```xml
        <sl:schemaLibrary>
            <sl:schema sl:uri="http://www.example.com" sl:schemaLocation="c:\example.xsd"
        />
        </sl:schemaLibrary>
        ```
        
        schema 元素包含此 XML 命名空间的属性：在本例中，命名空间 URI 为 http://www.example.com ，文件位置为 c:\example.xsd .
    
    [注意: 该元素无意将过渡模式重新引入严格一致性类。 ]

    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>manifestLocation(补充 XML 文件位置)</td>
                <td>
                    指定补充 XML 文件的位置，加载此文档时可以下载并解析该文件，以提供其他应用程序定义的功能。 该文件的内容是应用程序定义的. </br></br>
                    [例子: 考虑一个在 http://www.example.com 命名空间中包含自定义 XML 标记的 WordprocessingML 文档，该文档与位于 http://www.example.com/resource.xml 的资源文件关联。 文档的模式库数据中将显示以下内容：</br></br>
                    ```xml
                    <sl:schemaLibrary>
                        <sl:schema sl:uri="http://www.example.com"
                    sl:manifestLocation= "http://www.example.com/resource.xml" />
                    </sl:schemaLibrary>
                    ```
                    ManifestLocation 属性包含 http://www.example.com/resource.xml，它是使用此命名空间时可以下载使用的资源文件的位置。 ]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>schemaLanguage (Schema 语言)</td>
                <td>
                    指定模式语言的媒体类型或根命名空间.</br></br>
                    [Example:</br></br>
                    ```xml
                    <sl:schema …
                    schemaLanguage="http:/relaxng.org/ns/structure/1.0" />
                    ```
                    ]</br></br>
                    此属性的可能值由 W3C XML 架构令牌(token)数据类型定义。
                </td>
            </tr>
            <tr>
                <td>schemaLocation (自定义 XML 架构位置)</td>
                <td>
                    指定加载此文档时应下载和解析的 XML 架构文件的位置。</br></br>
                    [例子: 考虑一个 WordprocessingML 文档，该文档在 http://www.example.com 命名空间中包含自定义 XML 标记，该命名空间由位于 c:\example.xsd 的 XML 架构定义。 文档的模式库数据中将显示以下内容:</br></br>
                    ```xml
                    <sl:schemaLibrary>
                        <sl:schema sl:uri="http://www.example.com" sl:schemaLocation=
                    "c:\example.xsd" />
                    </sl:schemaLibrary>
                    ```
                    schemaLocation 属性包含 c:\example.xsd，它是使用此命名空间时使用的 XML 架构文件的位置. ]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>uri (Custom XML Schema Namespace)</td>
                <td>
                    指定与此架构引用关联的 XML 架构的目标命名空间.</br></br>
                    [例子: 对于自定义 XML 命名空间数据，请考虑以下内容:</br></br>
                    ```xml
                    …
                    <sl:schema w:uri="http://www.example.com/schema1" />
                    <sl:schema w:uri="http://www.example.com/schema2" />
                    …
                    ```
                    uri 属性指定每个 XML 模式引用的目标命名空间：</br></br>
                    - http://www.example.com/schema1</br>
                    - http://www.example.com/schema2</br>
                    然后，应用程序可以使用任何可用的方式找到并利用这些命名空间的架构. ]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>
    
    [注意: 该元素内容模型 (CT_Schema) 的 W3C XML 模式定义位于 [§A.7]. ]

=== "英文"

    **schema (Custom XML Schema Reference)**

    This element specifies the properties associated with a single XML namespace, for which all known XML schemas shall be loaded in order to validate the custom XML markup stored within this document. These properties can be used appropriately to locate custom XML schema(s) for use with the document. ECMA-376 does not require any particular XML schema language. 、
    
    [Note: Some examples of XML schema languages that might be used to implement Custom XML Mappings include:

    - W3C XML Schema - http://www.w3.org/XML/Schema
    - RELAX NG – ISO/IEC 19757-2
    - Schematron – ISO/IEC 19757-3
    - NVDL – ISO/IEC 19757-4
  
    !!! info "Example"
    
        Consider a WordprocessingML document which contains custom XML markup in the http://www.example.com namespace. The following content would be displayed in the document's schema library data:

        ```xml
        <sl:schemaLibrary>
            <sl:schema sl:uri="http://www.example.com" sl:schemaLocation="c:\example.xsd"
        />
        </sl:schemaLibrary>
        ```
        
        The schema element contains the properties for this one XML namespace: in this case, a namespace URI of http://www.example.com and a file location of c:\example.xsd. end example]
    
    [Note: This element is not intended to reintroduce transitional schema into the strict conformance class. end note]

    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>manifestLocation(Supplementary XML File Location)</td>
                <td>
                    Specifies the location of a supplementary XML file that can be downloaded and parsed when this document is loaded in order to provide additional application-defined capabilities. The contents of this file are application-defined. </br></br>
                    [Example: Consider a WordprocessingML document that contains custom XML markup in the http://www.example.com namespace, which is associated with a resource file located at http://www.example.com/resource.xml. The following content would be displayed in the document's schema library data:</br></br>
                    ```xml
                    <sl:schemaLibrary>
                        <sl:schema sl:uri="http://www.example.com"
                    sl:manifestLocation= "http://www.example.com/resource.xml" />
                    </sl:schemaLibrary>
                    ```
                    The manifestLocation attribute contains http://www.example.com/resource.xml which is the location of a resource file that can be downloaded for use when this namespace is used. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>schemaLanguage (Schema Language)</td>
                <td>
                    Specifies the media type or the root namespace of the schema language.</br></br>
                    [Example:</br></br>
                    ```xml
                    <sl:schema …
                    schemaLanguage="http:/relaxng.org/ns/structure/1.0" />
                    ```
                    end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema token datatype.
                </td>
            </tr>
            <tr>
                <td>schemaLocation (Custom XML Schema Location)</td>
                <td>
                    Specifies the location of the XML schema file which should be downloaded and parsed when this document is loaded.</br></br>
                    [Example: Consider a WordprocessingML document which contains custom XML markup in the http://www.example.com namespace, which is defined by an XML schema located at c:\example.xsd. The following content would be displayed in the document's schema library data:</br></br>
                    ```xml
                    <sl:schemaLibrary>
                        <sl:schema sl:uri="http://www.example.com" sl:schemaLocation=
                    "c:\example.xsd" />
                    </sl:schemaLibrary>
                    ```
                    The schemaLocation attribute contains c:\example.xsd which is the location of the XML schema file used when this namespace is used. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>uri (Custom XML Schema Namespace)</td>
                <td>
                    Specifies the target namespace for the XML Schema associated with this schema reference.</br></br>
                    [Example: Consider the following content for custom XML namespace data:</br></br>
                    ```xml
                    …
                    <sl:schema w:uri="http://www.example.com/schema1" />
                    <sl:schema w:uri="http://www.example.com/schema2" />
                    …
                    ```
                    The uri attribute specifies the target namespace of each XML schema reference:</br></br>
                    - http://www.example.com/schema1
                    - http://www.example.com/schema2
                    Applications can then locate and utilize a schema for these namespaces using any means available. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Schema) is located in [§A.7]. end note]

### 23.2.2 schemaLibrary (嵌入式自定义 XML schema补充数据)

=== "中文"

    此元素指定与当前 Office Open XML 文档中的自定义 XML 标记的内容关联的 XML 命名空间集。 文档中引用的每个唯一命名空间都可以在此元素中由单个模式元素引用，而不管构成该命名空间的组成 XML 模式的数量如何。

    !!! info "Example"
    
        考虑一个 WordprocessingML 文档，该文档在两个不同的命名空间中包含自定义 XML 标记：http://www.example.com 命名空间和 http://www.example2.com 命名空间。 如果第一个命名空间由单个 XML 模式定义，第二个命名空间由五个 XML 模式定义（使用适当的 XML 模式语法交叉引用），则以下内容将显示在文档的模式库 XML 中:

        ```xml
        <sl:schemaLibrary>
            <sl:schema … />
            <sl:schema … />
        </sl:schemaLibrary>
        ```
        
        尽管使用了六个 XML 模式，但 `schemaLibrary` 元素仅包含两个模式元素，因为只有两个不同的命名空间用于存储数据。

    [注意: 该元素内容模型 (CT_SchemaLibrary) 的 W3C XML 模式定义位于 [§A.7] 中。]

=== "英文"

    **schemaLibrary (Embedded Custom XML Schema Supplementary Data)**

    This element specifies the set of XML namespaces which have been associated with the contents of the custom XML markup within the current Office Open XML document. Each unique namespace which is referenced within the document can be referenced within this element by a single schema element, regardless of the number of constituent XML schemas which comprise that namespace.

    [Example: Consider a WordprocessingML document which contains custom XML markup in two distinct namespaces: the http://www.example.com namespace and the http://www.example2.com namespace. If the first namespace is defined by a single XML schema, and the second is defined by five XML schemas (which are cross-referenced using the appropriate XML Schema syntax), the following content would be displayed in the document's schema library XML:

    ```xml
    <sl:schemaLibrary>
        <sl:schema … />
        <sl:schema … />
    </sl:schemaLibrary>
    ```
    
    The schemaLibrary element contains only two schema elements even though there are six XML schemas in use, as there are only two distinct namespaces for which data is stored. end example]

    [Note: The W3C XML Schema definition of this element’s content model (CT_SchemaLibrary) is located in [§A.7]. end note]
