# 22.4 变体类型

=== "中文"

    本子章节指定可以包含在接受变体类型结构的文件属性中的数据类型集。

=== "英文"

    **Variant Types**

    This subclause specifies the set of data types which can be included within file properties that accept variant type structures. 

## 22.4.1 目录

This subclause is informative

- 22.4.2 Elements
    - 22.4.2.1 array (Array)
    - 22.4.2.2 blob (Binary Blob)
    - 22.4.2.3 bool (Boolean)
    - 22.4.2.4 bstr (Basic String)
    - 22.4.2.5 clsid (Class ID)
    - 22.4.2.6 cy (Currency)
    - 22.4.2.7 date (Date and Time)
    - 22.4.2.8 decimal (Decimal)
    - 22.4.2.9 empty (Empty)
    - 22.4.2.10 error (Error Status Code)
    - 22.4.2.11 filetime (File Time)
    - 22.4.2.12 i1 (1-Byte Signed Integer)
    - 22.4.2.13 i2 (2-Byte Signed Integer)
    - 22.4.2.14 i4 (4-Byte Signed Integer)
    - 22.4.2.15 i8 (8-Byte Signed Integer)
    - 22.4.2.16 int (Integer)
    - 22.4.2.17 lpstr (LPSTR)
    - 22.4.2.18 lpwstr (LPWSTR)
    - 22.4.2.19 null (Null)
    - 22.4.2.20 oblob (Binary Blob Object)
    - 22.4.2.21 ostorage (Binary Storage Object)  
    - 22.4.2.22 ostream (Binary Stream Object)
    - 22.4.2.23 r4 (4-Byte Real Number)
    - 22.4.2.24 r8 (8-Byte Real Number)
    - 22.4.2.25 storage (Binary Storage)
    - 22.4.2.26 stream (Binary Stream)
    - 22.4.2.27 ui1 (1-Byte Unsigned Integer)
    - 22.4.2.28 ui2 (2-Byte Unsigned Integer)
    - 22.4.2.29 ui4 (4-Byte Unsigned Integer)
    - 22.4.2.30 ui8 (8-Byte Unsigned Integer)
    - 22.4.2.31 uint (Unsigned Integer)
    - 22.4.2.32 variant (Variant)
    - 22.4.2.33 vector (Vector)
    - 22.4.2.34 vstream (Binary Versioned Stream)
- 22.4.3 Simple Types
    - 22.4.3.1 ST_ArrayBaseType (Array Base Type Simple Type)
    - 22.4.3.2 ST_Cy (Currency Simple Type)
    - 22.4.3.3 ST_Error (Error Status Code Simple Type)
    - 22.4.3.4 ST_VectorBaseType (Vector Base Type Simple Type)

End of informative text.

## 22.4.2 元素

=== "中文"

    以下元素定义了该命名空间的内容：

=== "英文"

    **Elements**
    
    The following elements define the contents of this namespace:

### 22.4.2.1 array (数组)

=== "中文"

    数组元素定义数组变体类型。 数组内容应具有由 baseType 属性指定的统一类型。 数组的内容是使用适当变体类型的重复子元素来定义的。
    
    可以通过使用“,”分隔符在 lBound 和 uBound 属性中指定每个维度的长度来定义多维数组。 多维数组的子元素按照声明维度的顺序沿每个维度进行索引。

    换句话说，数组应填充如下：
    
    - 第一个索引应增加到其最大值 [Example: [0,0,0] 至 [max,0,0] end example]
    - 第二个索引应增加到其最大值 [Example: [0,1,0] 至 [0,max,0] endexample]
    - 应填充后续索引，直到添加所有提供的值
    - 数组中的所有其他值均应为空值 (i.e. 不应假定默认值).
    
    !!! info "Example"
    
        “i4”类型的 2x3 变体类型数组指定如下：
    
        ```xml
        <vt:array lBounds="0,0" uBounds="1,2" baseType="i4">
            <vt:i4>0</vt:i4>
            <vt:i4>1</vt:i4>
            <vt:i4>2</vt:i4>
            <vt:i4>3</vt:i4>
            <vt:i4>4</vt:i4>
        </vt:array>
        ```

        得到数组: [0,0] = 0, [1,0] = 1, [0,1] = 2, [1,1] = 3, [0,2] = 4. 
    
    <table>
        <thead>
            <tr>
                <th>属性</th>
                <th>描述</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>baseType (数组基本类型) </td>
                <td>
                    baseType 属性指定数组的基本变体类型.<br/><br/>
                    允许的值为：variant、i1、i2、i4、int、ui1、ui2、ui4、uint、r4、r8、decimal、bstr、date、bool、cy 和 error.<br/><br/>
                    该属性的可能值由 ST_ArrayBaseType 简单类型定义 ([§22.4.3.1]).
                </td>
            </tr>
            <tr>
                <td>lBounds (数组下限属性)</td>
                <td>
                    lBounds 属性以以下格式指定数组的下限：#, #, # … #，其中每个 # 代表一个整数。<br/><br/>
                    此属性的可能值由 W3C XML Schema int 数据类型定义。
                </td>
            </tr>
            <tr>
                <td>uBounds (数组上限属性)</td>
                <td>
                    uBounds 属性以以下格式指定数组的上限：#, #, # … #，其中每个 # 代表一个整数.<br/><br/>
                    此属性的可能值由 W3C XML Schema int 数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 该元素内容模型 (CT_Array) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **array (Array)**
    
    The array element defines the array variant type. Array contents shall be of uniform type as specified by the
    baseType attribute. The contents of an array are defined using repeated child elements of the appropriate
    variant type.
    
    Multi-dimensional arrays can be defined by specifying the length of each dimension in the lBound and uBound
    attributes through the use of the "," delimiter. Child elements of multi-dimensional arrays are indexed along
    each dimension in the order the dimensions are declared.
    
    In other words, the array shall be filled as follows:
    
    - The first index shall be incremented to its maximum value [Example: [0,0,0] to [max,0,0] end example]
    - The second index shall be incremented to its maximum value [Example: [0,1,0] to [0,max,0] endexample]
    - Subsequent indices shall be filled until all provided values have been added
    - All other values shall have null values within the array (i.e. no default value shall be assumed).
    
    !!! info "Example"
    
        A 2x3 variant type array of type "i4" is specified as follows:
    
        ```xml
        <vt:array lBounds="0,0" uBounds="1,2" baseType="i4">
            <vt:i4>0</vt:i4>
            <vt:i4>1</vt:i4>
            <vt:i4>2</vt:i4>
            <vt:i4>3</vt:i4>
            <vt:i4>4</vt:i4>
        </vt:array>
        ```
        The resulting array: [0,0] = 0, [1,0] = 1, [0,1] = 2, [1,1] = 3, [0,2] = 4. 
    
    <table>
        <thead>
            <tr>
                <th>Attributes</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>baseType (Array Base Type) </td>
                <td>
                    The baseType attribute specifies the base variant type of an array.<br/><br/>
                    The allowed values are: variant, i1, i2, i4, int, ui1, ui2, ui4, uint, r4, r8, decimal, bstr, date, bool, cy, and error.<br/><br/>
                    The possible values for this attribute are defined by the ST_ArrayBaseType simple type (§22.4.3.1).
                </td>
            </tr>
            <tr>
                <td>lBounds (Array Lower Bounds Attribute)</td>
                <td>
                    The lBounds attribute specifies the lower bound of an array in the format: #, #, # … # where each # represents an integer.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema int datatype.
                </td>
            </tr>
            <tr>
                <td>uBounds (Array Upper Bounds Attribute)</td>
                <td>
                    The uBounds attribute specifies the upper bound of an array in the format: #, #, # … # where each # represents an integer.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema int datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Array) is located in §A.6.4. end note]

### 22.4.2.2 blob (二进制Blob)

=== "中文"

    此元素指定 base64 二进制 blob 变体类型。
    
    该类型定义如下：DWORD 字节数，后跟相应数量的数据字节。 字节计数不包括计数本身长度的四个字节； 空 blob 成员的计数为零，后跟零字节。
    
    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义。

=== "英文"

    **blob (Binary Blob)**

    This element specifies a base64 binary blob variant type.
    
    This type is defined as follows: a DWORD count of bytes, followed by that many bytes of data. The byte count does not include the four bytes for the length of the count itself; an empty blob member would have a count of zero, followed by zero bytes.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.3 bool (Boolean)

=== "中文"

    该元素指定布尔变量类型。
    
    该元素的可能值由 W3C XML 架构布尔数据类型定义。

=== "英文"

    **bool (Boolean)**

    This element specifies a Boolean variant type.
    
    The possible values for this element are defined by the W3C XML Schema boolean datatype.

### 22.4.2.4 bstr (基本字符串)

=== "中文"

    该元素定义了一个二进制基本字符串变体类型，它可以存储任何有效的 Unicode 字符。 
    不能直接在 XML 中表示的 Unicode 字符（如 XML 1.0 规范所定义）应使用 Unicode 数字字符表示转义字符格式 _xHHHH_ 进行转义，其中 H 表示字符值中的十六进制字符。 [Example：XML 1.0 文档中不允许使用 Unicode 字符 8，因此应将其转义为 `_x0008_`。] 要存储转义序列的文字形式，初始下划线本身应被转义（即存储为 `_x005F_`）. [Example: 字符串文字` _x0008_` 将存储为 `_x005F_x0008_`。 end example]
    
    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **bstr (Basic String)**

    This element defines a binary basic string variant type, which can store any valid Unicode character. Unicode characters that cannot be directly represented in XML as defined by the XML 1.0 specification, shall be escaped using the Unicode numerical character representation escape character format _xHHHH_, where H represents a hexadecimal character in the character's value. [Example: The Unicode character 8 is not permitted in an XML 1.0 document, so it shall be escaped as _x0008_. end example] To store the literal form of an escape sequence, the initial underscore shall itself be escaped (i.e. stored as _x005F_). [Example: The string literal _x0008_ would be stored as _x005F_x0008_. end example]
    
    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.4.2.5 clsid (Class ID)

=== "中文"

    该元素指定类 ID 变体类型。 该值应为全局唯一标识符，格式为： {HHHHHHHH-HHHH-HHHH-HHHH-HHHHHHHH}.
    
    该元素的可能值由 ST_Guid 简单类型 ([§22.9.2.4]) 定义。

    [Note: 该元素内容模型 (ST_Guid) 的 W3C XML 架构定义位于 [§A.6.9]. end note]

=== "英文"

    **clsid (Class ID)**

    This element specifies a class ID variant type. The value shall be a Globally Unique Identifier with format: {HHHHHHHH-HHHH-HHHH-HHHH-HHHHHHHH}.
    
    The possible values for this element are defined by the ST_Guid simple type (§22.9.2.4).
    
    [Note: The W3C XML Schema definition of this element’s content model (ST_Guid) is located in §A.6.9. end note]

### 22.4.2.6 cy (货币)

=== "中文"

    该元素指定小数点后恰好四位数字的货币变体类型。
    
    该元素的可能值由 ST_Cy 简单类型 ([§22.4.3.2]) 定义。
    
    [Note: 该元素内容模型 (ST_Cy) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **cy (Currency)**

    This element specifies a currency variant type with exactly four digits after the decimal point.
    
    The possible values for this element are defined by the ST_Cy simple type (§22.4.3.2).
    
    [Note: The W3C XML Schema definition of this element’s content model (ST_Cy) is located in §A.6.4. end note]

### 22.4.2.7 date (日期和时间)

=== "中文"

    此元素指定 RFC 3339 中定义的日期时间类型的日期变体类型。
    
    此元素的可能值由 W3C XML 架构 dateTime 数据类型定义。

=== "英文"

    **date (Date and Time)**

    This element specifies a date variant type of type date-time as defined in RFC 3339.
    
    The possible values for this element are defined by the W3C XML Schema dateTime datatype.

### 22.4.2.8 decimal (十进制)

=== "中文"

    该元素指定十进制变体类型。
    
    此元素的可能值由 W3C XML 架构十进制数据类型定义。

=== "英文"

    **decimal (Decimal)**

    This element specifies a decimal variant type.
    
    The possible values for this element are defined by the W3C XML Schema decimal datatype.

### 22.4.2.9 empty (空)

=== "中文"

    该元素指定空变体类型。 不允许任何值或子元素。
    
    [Note: 该元素内容模型 (CT_Empty) 的 W3C XML 架构定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **empty (Empty)**

    This element specifies an empty variant type. No values or child elements are allowed.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Empty) is located in §A.6.4. end note]

### 22.4.2.10 error (错误状态代码)

=== "中文"

    错误元素指定 0xHHHHHHHH 形式的 32 位错误状态代码变量类型。 每个H代表一个十六进制数字。
    
    该元素的可能值由 ST_Error 简单类型（[§22.4.3.3]）定义。

    [Note: 该元素内容模型 (ST_Error) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **error (Error Status Code)**

    The error element specifies a 32-bit error status code variant type of the form 0xHHHHHHHH. Each H represents a hexadecimal digit.
    
    The possible values for this element are defined by the ST_Error simple type (§22.4.3.3).
    
    [Note: The W3C XML Schema definition of this element’s content model (ST_Error) is located in §A.6.4. end note]

### 22.4.2.11 filetime (文件时间)

=== "中文"

    此元素指定 RFC 3339 中定义的日期时间类型的文件时间变体类型。
    
    此元素的可能值由 W3C XML 架构 dateTime 数据类型定义。

=== "英文"

    **filetime (File Time)**

    This element specifies a file-time variant type of type date-time as defined in RFC 3339.
    
    The possible values for this element are defined by the W3C XML Schema dateTime datatype.

### 22.4.2.12 i1 (1-字节 有符号整数)

=== "中文"

    该元素指定 1 字节有符号整数变量类型。
    
    该元素的可能值由 W3C XML 模式字节数据类型定义。

=== "英文"

    **i1 (1-Byte Signed Integer)**

    This element specifies a 1-byte signed integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema byte datatype.

### 22.4.2.13 i2 (2-字节 有符号整数)

=== "中文"

    该元素指定 2 字节有符号整数变体类型。
    
    该元素的可能值由 W3C XML 模式短数据类型定义。

=== "英文"

    **i2 (2-Byte Signed Integer)**

    This element specifies a 2-byte signed integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema short datatype.

### 22.4.2.14 i4 (4-字节 有符号整数)

=== "中文"

    该元素指定 4 字节有符号整数变量类型。
    
    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **i4 (4-Byte Signed Integer)**

    This element specifies a 4-byte signed integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.4.2.15 i8 (8-字节 有符号整数)

=== "中文"

    该元素指定 8 字节有符号整数变体类型。
    
    该元素的可能值由 W3C XML 模式长数据类型定义。

=== "英文"

    **i8 (8-Byte Signed Integer)**

    This element specifies a 8-byte signed integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema long datatype.

### 22.4.2.16 int (整数)

=== "中文"

    该元素指定整数变体类型。
    
    该元素的可能值由 W3C XML Schema int 数据类型定义。

=== "英文"

    **int (Integer)**

    This element specifies an integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema int datatype.

### 22.4.2.17 lpstr (LPSTR)

=== "中文"

    该元素指定字符串变体类型。 对于 XML 1.0 规范定义的无法在 XML 中表示的所有字符，将使用 Unicode 数字字符表示转义字符格式 _xHHHH_ 对这些字符进行转义，其中 H 表示字符值中的十六进制字符。
    
    [Example: XML 1.0 文档中不允许使用 Unicode 字符 8，因此必须将其转义为 _x0008_。 end example]
    
    此元素的可能值由 W3C XML 架构字符串数据类型定义。

=== "英文"

    **lpstr (LPSTR)**

    This element specifies a string variant type. For all characters that cannot be represented in XML as defined by the XML 1.0 specification, the characters are escaped using the Unicode numerical character representation escape character format _xHHHH_, where H represents a hexadecimal character in the character's value.
    
    [Example: The Unicode character 8 is not permitted in an XML 1.0 document, so it must be escaped as _x0008_. end example]
    
    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.4.2.18 lpwstr (LPWSTR)

=== "中文"

    该元素指定字符串变体类型。 对于 XML 1.0 规范定义的无法在 XML 中表示的所有字符，将使用 Unicode 数字字符表示转义字符格式 _xHHHH_ 对这些字符进行转义，其中 H 表示字符值中的十六进制字符。
    
    [Example: XML 1.0 文档中不允许使用 Unicode 字符 8，因此必须将其转义为 _x0008_。 end example]
    
    The possible values for this element are defined by the W3C XML Schema string datatype.

=== "英文"

    **lpwstr (LPWSTR)**

    This element specifies a string variant type. For all characters that cannot be represented in XML as defined by the XML 1.0 specification, the characters are escaped using the Unicode numerical character representation escape character format _xHHHH_, where H represents a hexadecimal character in the character's value.
    
    [Example: The Unicode character 8 is not permitted in an XML 1.0 document, so it must be escaped as _x0008_. end example]
    
    The possible values for this element are defined by the W3C XML Schema string datatype.

### 22.4.2.19 null (Null)

=== "中文"

    该元素指定空变体类型。
    
    [Note: 该元素内容模型 (CT_Null) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **null (Null)**

    This element specifies a null variant type.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Null) is located in §A.6.4. end note]

### 22.4.2.20 oblob (二进制 Blob 对象)

=== "中文"

    此元素指定 base64 二进制 blob 对象变体类型。
    
    该类型定义如下：一个 blob 成员，包含一个序列化对象，其表示形式与 ostream 元素中出现的表示形式相同。 也就是说，DWORD 字节计数（其中字节计数不包括其本身的大小），其格式为类标识符后跟该类的初始化数据。

    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义。

=== "英文"

    **oblob (Binary Blob Object)**

    This element specifies a base64 binary blob object variant type.
    
    This type is defined as follows: A blob member that contains a serialized object in the same representation that would appear in the ostream element. That is, a DWORD byte count (where the byte count does not include the size of itself) which is in the format of a class identifier followed by initialization data for that class.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.21 ostorage (二进制存储对象)

=== "中文"

    该元素指定 Base64 二进制存储对象变体类型。
    
    该类型定义如下： 与存储元素相同，但指示指定存储应包含可加载对象。
    
    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义。

=== "英文"

    **ostorage (Binary Storage Object)**

    This element specifies a base64 binary storage object variant type.
    
    This type is defined as follows: Identical to the storage element, but indicates that the designated storage shall contain a loadable object.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.22 ostream (二进制流对象)

=== "中文"

    该元素指定二进制流对象变体类型。
    
    该类型定义如下： 与流元素的定义相同，但指示流包含一个序列化对象，它是一个 CLSID – 请参阅 ST_Guid 简单类型 ([§22.9.2.4]) – 后跟指定的初始化数据类。
    
    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义.

=== "英文"

    **ostream (Binary Stream Object)**

    This element specifies a binary stream object variant type.
    
    This type is defined as follows: Identical to the definition of the stream element, but indicates that the stream contains a serialized object, which is a CLSID – see the ST_Guid simple type (§22.9.2.4) – followed by initialization data for the specified class.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.23 r4 (4-字节 Real Number)

=== "中文"

    该元素指定 4 字节实数变量类型。
    
    该元素的可能值由 W3C XML 架构浮点数据类型定义。

=== "英文"

    **r4 (4-Byte Real Number)**

    This element specifies a 4-byte real number variant type.
    
    The possible values for this element are defined by the W3C XML Schema float datatype.

### 22.4.2.24 r8 (8-字节 Real Number)

=== "中文"

    该元素指定 8 字节实数变量类型。
    
    该元素的可能值由 W3C XML 模式双精度数据类型定义。

=== "英文"

    **r8 (8-Byte Real Number)**

    This element specifies a 8-byte real number variant type.
    
    The possible values for this element are defined by the W3C XML Schema double datatype.

### 22.4.2.25 storage (二进制存储)

=== "中文"

    该元素指定二进制存储变体类型。
    
    该类型定义如下： 包含用于结构化存储的 Base64 编码数据。
    
    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义。

=== "英文"

    **storage (Binary Storage)**

    This element specifies a binary storage variant type.
    
    This type is defined as follows: Contains the base64-encoded data for a structured storage.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.26 stream (二进制流)

=== "中文"

    该元素指定二进制流变体类型。
    
    该类型定义如下： 包含结构化存储流的 base64 编码数据。

    此元素的可能值由 W3C XML 架构 base64Binary 数据类型定义。

=== "英文"

    **stream (Binary Stream)**
    
    This element specifies a binary stream variant type.
    
    This type is defined as follows: Contains the base64-encoded data for a structured storage stream.
    
    The possible values for this element are defined by the W3C XML Schema base64Binary datatype.

### 22.4.2.27 ui1 (1-字节 无符号整数)

=== "中文"

    该元素指定 1 字节无符号整数变量类型。

    此元素的可能值由 W3C XML 架构 unsignedByte 数据类型定义。

=== "英文"

    **ui1 (1-Byte Unsigned Integer)**
    
    This element specifies a 1-byte unsigned integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema unsignedByte datatype.

### 22.4.2.28 ui2 (2-字节 无符号整数)

=== "中文"

    该元素指定 2 字节无符号整数变量类型。

    此元素的可能值由 W3C XML 架构 unsignedShort 数据类型定义。

=== "英文"

    **ui2 (2-Byte Unsigned Integer)**
    
    This element specifies a 2-byte unsigned integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema unsignedShort datatype.

### 22.4.2.29 ui4 (4-字节 无符号整数)

=== "中文"

    该元素指定 4 字节无符号整数变量类型。

    此元素的可能值由 W3C XML 架构 unsignedInt 数据类型定义。

=== "英文"

    **ui4 (4-Byte Unsigned Integer)**
    
    This element specifies a 4-byte unsigned integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema unsignedInt datatype.

### 22.4.2.30 ui8 (8-字节 无符号整数)

=== "中文"

    该元素指定 8 字节无符号整数变量类型。

    此元素的可能值由 W3C XML 架构 unsignedLong 数据类型定义。

=== "英文"

    **ui8 (8-Byte Unsigned Integer)**
    
    This element specifies a 8-byte unsigned integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema unsignedLong datatype.

### 22.4.2.31 uint (无符号整数)

=== "中文"

    该元素指定无符号整数变体类型。

    此元素的可能值由 W3C XML 架构 unsignedInt 数据类型定义。

=== "英文"

    **uint (Unsigned Integer)**
    
    This element specifies an unsigned integer variant type.
    
    The possible values for this element are defined by the W3C XML Schema unsignedInt datatype.

### 22.4.2.32 variant (变体)

=== "中文"

    该元素可以包含任意变体类型的 1 个子元素。 该元素仅作为向量或数组变体类型的子元素有效。
    
    !!! info "Example"
    
        A vector of variant types:
    
        ```xml
        <vt:vector baseType="variant">
            <vt:variant>
                <vt:i4>12</vt:i4>
            </vt:variant>
            <vt:variant>
                <vt:lpstr>WorkSheets</vt:lpstr>
            </vt:variant>
        </vt:vector>
        ```
    
    [Note: 该元素内容模型 (CT_Variant) 的 W3C XML 架构定义位于 [§A.6.4]. end note]

=== "英文"

    **variant (Variant)**
    
    This element can contain exactly 1 child element of any variant type. This element is only valid as a child element of a vector or array variant type.
    
    !!! info "Example"
    
        A vector of variant types:
    
        ```xml
        <vt:vector baseType="variant">
            <vt:variant>
                <vt:i4>12</vt:i4>
            </vt:variant>
            <vt:variant>
                <vt:lpstr>WorkSheets</vt:lpstr>
            </vt:variant>
        </vt:vector>
        ```
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Variant) is located in §A.6.4. end note]

### 22.4.2.33 vector (向量)

=== "中文"

    该元素定义向量变体类型。 矢量内容应具有由 baseType 属性指定的统一类型。 向量的内容是使用适当变体类型的重复子元素来定义的。
    
    !!! info "Example"
    
        lpstr 变体类型的向量:
    
        ```xml
        <vt:vector baseType="lpstr">
            <vt:lpstr>One</vt:lpstr>
            <vt:lpstr>Two</vt:lpstr>
            <vt:lpstr>Three</vt:lpstr>
        </vt:vector>
        ```
    
    <table>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>baseType (向量基类型)</td>
                <td>
                    baseType 属性指定向量的基本变体类型.<br/><br/>
                    允许的值为：variant、i1、i2、i4、i8、ui1、ui2、ui4、ui8、r4、r8、lpstr、lpwstr、bstr、date、filetime、bool、cy、error 和 clsid.<br/><br/>
                    该属性的可能值由 ST_VectorBaseType 简单类型定义 ([§22.4.3.4]).
                </td>
            </tr>
            <tr>
                <td>size (向量大小)</td>
                <td>
                    指定向量中的元素数量.<br/><br/>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 该元素内容模型 (CT_Vector) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **vector (Vector)**
    
    This element defines the vector variant type. Vector contents shall be of uniform type as specified by the baseType attribute. The contents of a vector are defined using repeated child elements of the appropriate variant type.
    
    !!! info "Example"
    
        A vector of lpstr variant types:
    
        ```xml
        <vt:vector baseType="lpstr">
            <vt:lpstr>One</vt:lpstr>
            <vt:lpstr>Two</vt:lpstr>
            <vt:lpstr>Three</vt:lpstr>
        </vt:vector>
        ```
    
    <table>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>baseType (Vector Base Type)</td>
                <td>
                    The baseType attribute specifies the base variant type of a vector.<br/><br/>
                    The allowed values are: variant, i1, i2, i4, i8, ui1, ui2, ui4, ui8, r4, r8, lpstr, lpwstr, bstr, date, filetime, bool, cy, error, and clsid.<br/><br/>
                    The possible values for this attribute are defined by the ST_VectorBaseType simple type (§22.4.3.4).
                </td>
            </tr>
            <tr>
                <td>size (Vector Size)</td>
                <td>
                    Specifies the number of elements in the vector.<br/><br/>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Vector) is located in §A.6.4. end note]

### 22.4.2.34 vstream (二进制版本化流)

=== "中文"

    该元素指定二进制版本化流变体类型。
    
    该类型定义如下：具有 GUID 版本（版本属性）的流元素内容。
    
    [Note: 该元素内容模型 (CT_Vstream) 的 W3C XML 模式定义位于 [§A.6.4] 中。 end note]

=== "英文"

    **vstream (Binary Versioned Stream)**
    
    This element specifies a binary versioned stream variant type.
    
    This type is defined as follows: A stream element's content with a GUID version (the version attribute).
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Vstream) is located in §A.6.4. end note]

## 22.4.3 简单类型

=== "中文"

    这是专用于变体类型的简单类型的完整列表。

=== "英文"

    **Simple Types**
    
    This is the complete list of simple types dedicated to Variant Types.

### 22.4.3.1 ST_ArrayBaseType (数组 基本类型 简单类型)

=== "中文"

    ST_ArrayBaseType 简单类型将数组的 baseType 属性的允许值定义为：variant、i1、i2、i4、int、ui1、ui2、ui4、uint、r4、r8、decimal、bstr、date、bool、cy 和 error。
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：
    
    <table>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>bool (布尔基本类型)</td>
                <td>
                    指定数组内容的变量类型应为 bool.
                </td>
            </tr>
            <tr>
                <td>bstr (基本字符串基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 bstr.
                </td>
            </tr>
            <tr>
                <td>cy (货币基础类型) </td>
                <td>
                    指定数组内容的变体类型应为 cy.
                </td>
            </tr>
            <tr>
                <td>date (日期和时间基础类型)</td>
                <td>
                    指定数组内容的变体类型应为 date.
                </td>
            </tr>
            <tr>
                <td>decimal (Decimal 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 decimal.
                </td>
            </tr>
            <tr>
                <td>error (错误状态代码基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 error.
                </td>
            </tr>
            <tr>
                <td>i1 (1-字节 有符号整数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 i1.
                </td>
            </tr>
            <tr>
                <td>i2 (2-字节 有符号整数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 i2.
                </td>
            </tr>
            <tr>
                <td>i4 (4-字节 有符号整数 基本类型) </td>
                <td>
                    指定数组内容的变体类型应为 i4.
                </td>
            </tr>
            <tr>
                <td>int (Integer 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 int.
                </td>
            </tr>
            <tr>
                <td>r4 (4-字节 实数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 r4.
                </td>
            </tr>
            <tr>
                <td>r8 (8-字节 实数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 r8.
                </td>
            </tr>
            <tr>
                <td>ui1 (1-字节 无符号整数 基本类型) </td>
                <td>
                    指定数组内容的变体类型应为 ui1.
                </td>
            </tr>
            <tr>
                <td>ui2 (2-字节 无符号整数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 ui2.
                </td>
            </tr>
            <tr>
                <td>ui4 (4-字节 无符号整数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 ui4.
                </td>
            </tr>
            <tr>
                <td>uint (无符号整数 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 uint.
                </td>
            </tr>
            <tr>
                <td>variant (Variant 基本类型)</td>
                <td>
                    指定数组内容的变体类型应为 variant.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 此简单类型的内容模型 (ST_ArrayBaseType) 的 W3C XML 架构定义位于 §A.6.4. end note]

=== "英文"

    **ST_ArrayBaseType (Array Base Type Simple Type)**
    
    The ST_ArrayBaseType simple type defines the allowed values for an array's baseType attribute as: variant, i1, i2, i4, int, ui1,ui2, ui4, uint, r4, r8, decimal, bstr, date, bool, cy, and error.
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    This simple type is restricted to the values listed in the following table:
    
    <table>
        <thead>
            <tr>
                <th>**Enumeration Value**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>bool (Boolean Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be bool.
                </td>
            </tr>
            <tr>
                <td>bstr (Basic String Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be bstr.
                </td>
            </tr>
            <tr>
                <td>cy (Curency Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a array shall be cy.
                </td>
            </tr>
            <tr>
                <td>date (Date and Time Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be date.
                </td>
            </tr>
            <tr>
                <td>decimal (Decimal Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be decimal.
                </td>
            </tr>
            <tr>
                <td>error (Error Status Code Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be error.
                </td>
            </tr>
            <tr>
                <td>i1 (1-Byte Signed Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be i1.
                </td>
            </tr>
            <tr>
                <td>i2 (2-Byte Signed Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be i2.
                </td>
            </tr>
            <tr>
                <td>i4 (4-Byte Signed Integer Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a array shall be i4.
                </td>
            </tr>
            <tr>
                <td>int (Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be int.
                </td>
            </tr>
            <tr>
                <td>r4 (4-Byte Real Number Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be r4.
                </td>
            </tr>
            <tr>
                <td>r8 (8-Byte Real Number Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be r8.
                </td>
            </tr>
            <tr>
                <td>ui1 (1-Byte Unsigned Integer Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a array shall be ui1.
                </td>
            </tr>
            <tr>
                <td>ui2 (2-Byte Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be ui2.
                </td>
            </tr>
            <tr>
                <td>ui4 (4-Byte Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be ui4.
                </td>
            </tr>
            <tr>
                <td>uint (Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be uint.
                </td>
            </tr>
            <tr>
                <td>variant (Variant Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a array shall be variant.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_ArrayBaseType) is located in §A.6.4. end note]

### 22.4.3.2 ST_Cy (货币简单类型)

=== "中文"

    ST_Cy 简单类型将 cy 元素定义为小数点后恰好四位数字的货币变体类型。
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    这个简单类型还指定了以下限制：
    
    - 该简单类型的内容应与以下正则表达式模式匹配: `\s*[0-9]*\.[0-9]{4}\s*`.
    
    [Note: 此简单类型的内容模型 (ST_Cy) 的 W3C XML 架构定义位于 [§A.6.4]. end note]

=== "英文"

    **ST_Cy (Currency Simple Type)**
    
    The ST_Cy simple type defines the cy element as a currency variant type with exactly four digits after the decimal point.
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    This simple type also specifies the following restrictions:
    
    - This simple type's contents shall match the following regular expression pattern: `\s*[0-9]*\.[0-9]{4}\s*`.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Cy) is located in §A.6.4. end note]

### 22.4.3.3 ST_Error (错误状态代码简单类型)

=== "中文"

    ST_Error 简单类型定义了 0xHHHHHHHH 形式的 32 位错误状态代码变体类型。 每个H代表一个十六进制。
    
    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    这个简单类型还指定了以下限制：
    
    - 该简单类型的内容应与以下正则表达式模式匹配: `\s*0x[0-9A-Zaz]{8}\s*`.
    
    [Note: 此简单类型的内容模型 (ST_Error) 的 W3C XML 架构定义位于 [§A.6.4]. end note]

=== "英文"

    **ST_Error (Error Status Code Simple Type)**

    The ST_Error simple type defines a 32-bit error status code variant type of the form 0xHHHHHHHH. Each H represents a hexadecimal.
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    This simple type also specifies the following restrictions:
    
    - This simple type's contents shall match the following regular expression pattern: `\s*0x[0-9A-Zaz]{8}\s*`.
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Error) is located in §A.6.4. end note]

### 22.4.3.4 ST_VectorBaseType (向量基类型简单类型)

=== "中文"

    ST_VectorBaseType 简单类型将向量的 baseType 属性的允许值定义为：variant、i1、i2、i4、i8、ui1、ui2、ui4、ui8、r4、r8、lpstr、lpwstr、bstr、date、filetime、bool、cy 、error和 clsid。

    此简单类型的内容是 W3C XML 架构字符串数据类型的限制。

    此简单类型仅限于下表中列出的值：
    
    <table>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>bool (Boolean 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 bool.
                </td>
            </tr>
            <tr>
                <td>bstr (基本字符串 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 bstr.
                </td>
            </tr>
            <tr>
                <td>clsid (Class ID 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 clsid.
                </td>
            </tr>
            <tr>
                <td>cy (Curency 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 cy.
                </td>
            </tr>
            <tr>
                <td>date (日期时间 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 date.
                </td>
            </tr>
            <tr>
                <td>error (错误状态代码 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 error.
                </td>
            </tr>
            <tr>
                <td>filetime (文件时间 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 filetime.
                </td>
            </tr>
            <tr>
                <td>i1 (1-字节 有符号整数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 i1.
                </td>
            </tr>
            <tr>
                <td>i2 (2-字节 有符号整数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 i2.
                </td>
            </tr>
            <tr>
                <td>i4 (4-字节 有符号整数 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 i4.
                </td>
            </tr>
            <tr>
                <td>i8 (8-字节 有符号整数 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 i8.
                </td>
            </tr>
            <tr>
                <td>lpstr (LPSTR 基本类型)  </td>
                <td>
                    指定向量内容的变体类型应为 lpstr.
                </td>
            </tr>
            <tr>
                <td>lpwstr (LPWSTR 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 lpwstr.
                </td>
            </tr>
            <tr>
                <td>r4 (4-字节 实数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 r4.
                </td>
            </tr>
            <tr>
                <td>r8 (8-字节 实数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 r8.
                </td>
            </tr>
            <tr>
                <td>ui1 (1-字节 无符号整数 基本类型) </td>
                <td>
                    指定向量内容的变体类型应为 ui1.
                </td>
            </tr>
            <tr>
                <td>ui2 (2-字节 无符号整数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 ui2.
                </td>
            </tr>
            <tr>
                <td>ui4 (4-字节 无符号整数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 ui4.
                </td>
            </tr>
            <tr>
                <td>ui8 (8-字节 无符号整数 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 ui8.
                </td>
            </tr>
            <tr>
                <td>variant (Variant 基本类型)</td>
                <td>
                    指定向量内容的变体类型应为 variant.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 此简单类型的内容模型 (ST_VectorBaseType) 的 W3C XML 架构定义位于 [§A.6.4]. end note]

=== "英文"

    **ST_VectorBaseType (Vector Base Type Simple Type)**
    
    The ST_VectorBaseType simple type defines the allowed values for a vector's baseType attribute as: variant, i1, i2, i4, i8, ui1, ui2, ui4, ui8, r4, r8, lpstr, lpwstr, bstr, date, filetime, bool, cy, error, and clsid.
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    This simple type is restricted to the values listed in the following table:
    
    <table>
        <thead>
            <tr>
                <th>**Enumeration Value**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>bool (Boolean Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be bool.
                </td>
            </tr>
            <tr>
                <td>bstr (Basic String Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be bstr.
                </td>
            </tr>
            <tr>
                <td>clsid (Class ID Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be clsid.
                </td>
            </tr>
            <tr>
                <td>cy (Curency Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be cy.
                </td>
            </tr>
            <tr>
                <td>date (Date and Time Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be date.
                </td>
            </tr>
            <tr>
                <td>error (Error Status Code Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be error.
                </td>
            </tr>
            <tr>
                <td>filetime (File Time Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be filetime.
                </td>
            </tr>
            <tr>
                <td>i1 (1-Byte Signed Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be i1.
                </td>
            </tr>
            <tr>
                <td>i2 (2-Byte Signed Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be i2.
                </td>
            </tr>
            <tr>
                <td>i4 (4-Byte Signed Integer Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be i4.
                </td>
            </tr>
            <tr>
                <td>i8 (8-Byte Signed Integer Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be i8.
                </td>
            </tr>
            <tr>
                <td>lpstr (LPSTR Base Type)  </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be lpstr.
                </td>
            </tr>
            <tr>
                <td>lpwstr (LPWSTR Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be lpwstr.
                </td>
            </tr>
            <tr>
                <td>r4 (4-Byte Real Number Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be r4.
                </td>
            </tr>
            <tr>
                <td>r8 (8-Byte Real Number Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be r8.
                </td>
            </tr>
            <tr>
                <td>ui1 (1-Byte Unsigned Integer Base Type) </td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be ui1.
                </td>
            </tr>
            <tr>
                <td>ui2 (2-Byte Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be ui2.
                </td>
            </tr>
            <tr>
                <td>ui4 (4-Byte Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be ui4.
                </td>
            </tr>
            <tr>
                <td>ui8 (4-Byte Unsigned Integer Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be ui8.
                </td>
            </tr>
            <tr>
                <td>variant (Variant Base Type)</td>
                <td>
                    Specifies that the variant type for the contents of a vector shall be variant.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_VectorBaseType) is located in §A.6.4. end note]
