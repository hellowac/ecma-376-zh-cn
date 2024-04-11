# 22.3 自定义属性

=== "中文"

    自定义属性使用户能够通过一组定义良好的数据类型来定义自定义元数据属性。
    
    自定义属性由存储在自定义文件属性部分中的属性元素 ([§22.3.2.2]) 表示，其中：

    - Source Relationship: http://purl.oclc.org/ooxml/officeDocument/relationships/customProperties
    - Content Type: application/vnd.openxmlformats-officedocument.custom-properties+xml
    
    自定义属性元素是不可重复的，可以为空或省略。 如果省略所有自定义属性元素，则可以从文档中排除自定义属性部分。
    
    自定义属性的类型和值由文件属性变体类型命名空间中的子 XML 元素指定（在 [§22.4] 中详细讨论）。 用户定义的属性通过属性元素的名称属性进行唯一标识。 自定义属性可以通过 `fmtid` 和 `pid` 属性与 OLE 文档属性关联。

    !!! info "Example"
    
        字符串类型的自定义 OLE 编辑器属性可以定义如下：

        ```xml
        <property fmtid="{D5CDD505-2E9C-101B-9397-08002B2CF9AE}" pid="2"
            name="Editor">
            <vt:lpwstr>John Smith</vt:lpwstr>
        </property>
        ```

=== "英文"

    **Custom Properties**

    Custom properties enable users to define custom metadata properties through a set of well-defined data types.
    
    Custom properties are represented by property elements ([§22.3.2.2]) stored in the Custom File Properties part
    with:

    - Source Relationship: http://purl.oclc.org/ooxml/officeDocument/relationships/customProperties
    - Content Type: application/vnd.openxmlformats-officedocument.custom-properties+xml
    
    Custom property elements are non-repeatable and can be empty or omitted. If all custom property elements are omitted then the custom properties part can be excluded from a document.
    
    The type and value of custom properties are specified by child XML elements in the File Properties Variant Types namespace (discussed in detail in [§22.4]). User defined properties are uniquely identified through the name attribute of the property element. Custom properties can be associated with OLE document properties through the fmtid and pid attributes.

    !!! info "Example"
    
        A custom OLE Editor property of type string can be defined as follows:

        ```xml
        <property fmtid="{D5CDD505-2E9C-101B-9397-08002B2CF9AE}" pid="2"
            name="Editor">
            <vt:lpwstr>John Smith</vt:lpwstr>
        </property>
        ```

## 22.3.1 目录

This subclause is informative.

- 22.3.2 Elements
- 22.3.2.1 Properties (Custom File Properties)
- 22.3.2.2 property (Custom File Property)

End of informative text.

## 22.3.2 元素

=== "中文"

    本子条款指定定义此命名空间的元素集:

=== "英文"

    **Elements**

    This subclause specifies the set of elements that define this namespace:

### 22.3.2.1 Properties (自定义文件属性)

=== "中文"

    自定义文件属性部分的父元素.
    
    !!! info "Note"

        该元素内容模型 (CT_Properties) 的 W3C XML 模式定义位于 §A.6.3 中。

=== "英文"

    **Properties (Custom File Properties)**
    
    Parent element for the custom file properties part.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Properties) is located in §A.6.3. end note]

### 22.3.2.2 property (Custom File Property)

=== "中文"

    该元素指定单个自定义文件属性。 自定义文件属性类型是通过文件属性变体类型命名空间中的子元素定义的。 
    可以通过设置适当的变体类型子元素值来设置自定义文件属性值。
    
    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>fmtid (格式ID) </td>
                <td>
                    将自定义属性与 OLE 属性唯一关联。<br/><br/>
                    该属性的值是一个全局唯一标识符，其形式为 {HHHHHHHHHHHH-HHHH-HHHH-HHHHHHHH}，其中每个 H 都是十六进制。<br/><br/>
                    该属性的可能值由 ST_Guid 简单类型定义 ([§22.9.2.4]).
                </td>
            </tr>
            <tr>
                <td>linkTarget (书签链接目标) </td>
                <td>
                    指定当前文档中书签的名称（对于 WordprocessingML），或者表或命名单元格（对于 SpreadsheetML），应从中提取此自定义文档属性的值。<br/><br/>
                    如果存在此属性，则此元素下的任何值都应被视为缓存，并在保存时替换为此书签的值（如果存在）。 如果书签不存在，则该链接应被视为已损坏，并且应保留缓存的值.<br/><br/>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>name (自定义文件属性名称) </td>
                <td>
                    指定此自定义文件属性的名称.<br/><br/>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>pid (属性 ID) </td>
                <td>
                    将自定义属性与 OLE 属性唯一关联.<br/><br/>
                    此属性的可能值由 W3C XML Schema int 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>
    
    !!! info "Note"

        该元素内容模型 (CT_Property) 的 W3C XML 模式定义位于 §A.6.3 中。

=== "英文"

    **property (Custom File Property)**

    This element specifies a single custom file property. Custom file property type is defined through child elements in the File Properties Variant Type namespace. Custom file property value can be set by setting the appropriate Variant Type child element value.
    
    <table>
        <thead>
            <tr>
                <th>Attributes</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>fmtid (Format ID) </td>
                <td>
                    Uniquely relates a custom property with an OLE property.<br/><br/>
                    The value of this attribute is a Globally Unique Identifier in the form of {HHHHHHHHHHHH-HHHH-HHHH-HHHHHHHH} where each H is a hexidecimal.<br/><br/>
                    The possible values for this attribute are defined by the ST_Guid simple type ([§22.9.2.4]).
                </td>
            </tr>
            <tr>
                <td>linkTarget (Bookmark Link Target) </td>
                <td>
                    Specifies the name of a bookmark in the current document (for WordprocessingML), or a table or named cell (for SpreadsheetML) from which the value of this custom document property should be extracted.<br/><br/>
                    If this attribute is present, then any value under this element shall be considered a cache and replaced with the value of this bookmark (if present) on save. If the bookmark is not present, then this link shall be considered broken and the cached value shall be retained.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>name (Custom File Property Name) </td>
                <td>
                    Specifies the name of this custom file property.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>pid (Property ID) </td>
                <td>
                    Uniquely relates a custom property with an OLE property.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema int datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Property) is located in §A.6.3. end note]
