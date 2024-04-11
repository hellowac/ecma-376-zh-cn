# 22.7 附加特性

=== "中文"

    为了允许 Office Open XML 的制作者描述创建文档的特定上下文条件，可以使用下面定义的语法在“附加特性”部件中提供附加特性。

    该组附加特性被设计为可扩展列表，并且可以为消费者提供有关如何解释文件的更多信息。 ECMA-376 定义了一组特性； 然而，可以创建额外的语法并通过词汇属性与唯一的 URI 关联。

=== "英文"

    **Additional Characteristics**

    In order to allow producers of Office Open XML to describe specific contextual conditions under which the document was created, additional characteristics can be provided within the Additional Characteristics part using the syntax defined below.

    The set of additional characteristics is designed to be an extensible list, and can provide a consumer with more information on how to interpret the file. ECMA-376 defines one set of characteristics; however, additional grammars can be created and associated with a unique URI via the vocabulary attribute.

## 22.7.1 目录

This subclause is informative.

- [22.7.2] Elements
    - [22.7.2.1] additionalCharacteristics (Set of Additional Characteristics)
    - [22.7.2.2] characteristic (Single Characteristic)
- [22.7.3] Simple Types
    - [22.7.3.1] ST_Relation (Characteristic Relationship Types)

End of informative text.

## 22.7.2 Elements

=== "中文"

    以下元素定义附加特性架构的内容：

=== "英文"

    **Elements**
    
    The following elements define the contents of the Additional Characteristics schema:

### 22.7.2.1 additionalCharacteristics (附加特性集)

=== "中文"

    此元素是“附加特性”部件的根元素，包含 Office Open XML 文档的附加特性列表。
    
    !!! info "Example"
    
        “附加特性”部件中的以下内容将指定生成的电子表格应用程序支持 0 到 10,000 列，并且应相应地解释列范围：
    
        ```xml
        <additionalCharacteristics>
            <characteristic name="numColumns" relation="le" val="10000"/>
            <characteristic name="numColumns" relation="ge" val="0"/>
        </additionalCharacteristics>
        ```
    
    !!! info "Note"
    
        该元素内容模型 (CT_AdditionalCharacteristics) 的 W3C XML 模式定义位于 [§A.6.7]。

=== "英文"

    **additionalCharacteristics (Set of Additional Characteristics)**
    
    This element is the root element of the Additional Characteristics part and contains the list of additional characteristics for an Office Open XML document.
    
    !!! info "Example"
    
        The following content in an Additional Characteristics part would specify that the producing spreadsheet application supports from 0 to 10,000 columns, and that column ranges should be interpreted accordingly:
    
        ```xml
        <additionalCharacteristics>
            <characteristic name="numColumns" relation="le" val="10000"/>
            <characteristic name="numColumns" relation="ge" val="0"/>
        </additionalCharacteristics>
        ```
    
    !!! info "Note"
    
        The W3C XML Schema definition of this element’s content model (CT_AdditionalCharacteristics) is located in [§A.6.7]. 

### 22.7.2.2 characteristic (单一特性)

=== "中文"

    该元素指定一个单一特性。 特性的类型由名称属性定义。
    
    !!! info "Example"
    
        生产者可以通知消费者，用于计算公式中存储的数字的计算属于由二进制尾数和指数的范围表示的值空间。 消费者可以选择检查这些特性以确定是否应该重新计算这些值。 其 XML 为：
    
        ```xml
        <additionalCharacteristics>
            <characteristic name='precisionMantissa' relation='gt' val='-9007199254740992' />
            <characteristic name='precisionMantissa' relation='lt' val='9007199254740992' />
            <characteristic name='precisionExponent' relation='ge' val='-1075' />
            <characteristic name='precisionExponent' relation='le' val='970' />
        </additionalCharacteristics>
        ```
    
    <table border=1>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>name (特性名称) </td>
                <td>
                    指定特性的名称。 name 属性的值没有限制，但每个名称应通过词汇属性与特定词汇相关联.<br/><br/>
                    ECMA-376 定义的值应与空词汇值相关联，如下所示:<br/><br/>
                    <table border=1>
                        <thead>
                            <tr>
                                <th>**名称 值**</th>
                                <th>**指定属性**</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>numColumns </td>
                                <td>
                                    电子表格生成器支持的列数
                                </td>
                            </tr>
                            <tr>
                                <td>numRows </td>
                                <td>
                                    电子表格生成器支持的行数.
                                </td>
                            </tr>
                            <tr>
                                <td>functionVersion </td>
                                <td>
                                    使用的功能规范的版本
                                </td>
                            </tr>
                            <tr>
                                <td>precisionMantissa </td>
                                <td>
                                    以 2 为基数表示时电子表格单元格/公式中数字尾数的允许值。
                                </td>
                            </tr>
                            <tr>
                                <td>precisionExponent </td>
                                <td>
                                    以 2 为基数表示时电子表格单元格/公式中数字的指数的允许值。
                                </td>
                            </tr>
                            <tr>
                                <td>numWorkbookColors </td>
                                <td>
                                    工作簿颜色数量
                                </td>
                            </tr>
                            <tr>
                                <td>numConditionalFormatConditions </td>
                                <td>
                                    工作簿单元格上的条件格式条件数
                                </td>
                            </tr>
                            <tr>
                                <td>nummaxSortLevels </td>
                                <td>
                                    范围或表的排序级别数
                                </td>
                            </tr>
                            <tr>
                                <td>numAutoFilterItems </td>
                                <td>
                                    自动筛选下拉列表中显示的项目数
                                </td>
                            </tr>
                            <tr>
                                <td>numDisplayCellChars </td>
                                <td>
                                    单元格中可显示的字符数
                                </td>
                            </tr>
                            <tr>
                                <td>numPrintCellChars </td>
                                <td>
                                    Excel 可以打印的每个单元格的字符数
                                </td>
                            </tr>
                            <tr>
                                <td>numUnqiueCellStyles </td>
                                <td>
                                    工作簿中唯一单元格样式的数量（所有单元格格式的组合）
                                </td>
                            </tr>
                            <tr>
                                <td>numFormulaLengthChars </td>
                                <td>
                                    公式长度（以字符为单位）
                                </td>
                            </tr>
                            <tr>
                                <td>numFormulaNestingLeve1 </td>
                                <td>
                                    公式嵌套层数
                                </td>
                            </tr>
                            <tr>
                                <td>numFunctionArguments </td>
                                <td>
                                    函数的参数数量
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableRows </td>
                                <td>
                                    数据透视表中的行数
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableColumns </td>
                                <td>
                                    数据透视表中的列数
                                </td>
                            </tr>
                            <tr>
                                <td>numUniquePivotFieldItems </td>
                                <td>
                                    数据透视字段中唯一项目的数量
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableMDXNameChars </td>
                                <td>
                                    数据透视表项目的 MDX 名称中的字符数
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableRelationChars </td>
                                <td>
                                    关系数据透视表的字符串长度
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableFieldLabelChars </td>
                                <td>
                                    数据透视表中字段标签的长度，包括标题长度限制
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableFields </td>
                                <td>
                                    数据透视表中的字段数
                                </td>
                            </tr>
                            <tr>
                                <td>numSheetXRefArrayFormulas </td>
                                <td>
                                    工作表中可以引用另一个（给定）工作表的数组公式的数量
                                </td>
                            </tr>
                        </tbody>
                    </table>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>relation (值与名称的关系) </td>
                <td>
                    指定应如何在此特性的上下文中解释值属性的内容. </br></br>
                    [Example: 以下内容将指定应用程序支持从 0 到 10,000 列，并且应相应地解释列范围:</br></br>
                    `<additionalCharacteristics>`</br>
                    `<characteristic name="numColumns" relation="le" val="10000"/>`</br>
                    `<characteristic name="numColumns" relation="ge" val="0"/>`</br>
                    `</additionalCharacteristics>`</br>
                    end example]</br></br>
                    该属性的可能值由 ST_Relation 简单类型 ([§22.7.3.1]) 定义。
                </td>
            </tr>
            <tr>
                <td>val (特性值) </td>
                <td>
                    指定特性的值.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.</br></br>
                </td>
            </tr>
            <tr>
                <td>vocabulary (特性语法) </td>
                <td>
                    指定一个 URI，该 URI 定义了用于解释名称属性值的特性语法.</br></br>
                    如果省略此属性，则应使用默认语法（如上面定义）.</br></br>
                    此属性的可能值由 W3C XML 架构 anyURI 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 该元素内容模型 (CT_Characteristic) 的 W3C XML 模式定义位于 [§A.6.7]。 end note]

=== "英文"

    **characteristic (Single Characteristic)**
    
    This element specifies a single characteristic. The type of characteristic is defined by the name attribute.
    
    !!! info "Example"
    
        A producer can inform the consumer that the computations used to calculate the stored numbers in the formulas belong to a value space expressed by ranges of the binary mantissa and exponent. A consumer can optionally check those characteristics to determine whether, for example, the values should be recalculated. The XML for this would be:
    
        ```xml
        <additionalCharacteristics>
            <characteristic name='precisionMantissa' relation='gt' val='-9007199254740992' />
            <characteristic name='precisionMantissa' relation='lt' val='9007199254740992' />
            <characteristic name='precisionExponent' relation='ge' val='-1075' />
            <characteristic name='precisionExponent' relation='le' val='970' />
        </additionalCharacteristics>
        ```
    
    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>name (Name of Characteristic) </td>
                <td>
                    Specifies the name of the characteristic. There are no constraints on the value of the name attribute, but each name shall be associated with a specific vocabulary via the vocabulary attribute.<br/><br/>
                    The values defined by ECMA-376 shall be associated with a null vocabulary value, and are as follows:<br/><br/>
                    <table border=1>
                        <thead>
                            <tr>
                                <th>**Name Value**</th>
                                <th>**Property Specified**</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>numColumns </td>
                                <td>
                                    Number of Columns supported by the spreadsheet producer
                                </td>
                            </tr>
                            <tr>
                                <td>numRows </td>
                                <td>
                                    Number of Rows supported by the spreadsheet producer.
                                </td>
                            </tr>
                            <tr>
                                <td>functionVersion </td>
                                <td>
                                    Version of the function specification used
                                </td>
                            </tr>
                            <tr>
                                <td>precisionMantissa </td>
                                <td>
                                    Allowed values of the mantissa of numbers within spreadsheet cells/formulas when expressed in base 2.
                                </td>
                            </tr>
                            <tr>
                                <td>precisionExponent </td>
                                <td>
                                    Allowed values of the exponent of numbers within spreadsheet cells/formulas when expressed in base 2.
                                </td>
                            </tr>
                            <tr>
                                <td>numWorkbookColors </td>
                                <td>
                                    Number of Workbook colors
                                </td>
                            </tr>
                            <tr>
                                <td>numConditionalFormatConditions </td>
                                <td>
                                    Number of condition format conditions on a workbook cell
                                </td>
                            </tr>
                            <tr>
                                <td>nummaxSortLevels </td>
                                <td>
                                    Number of level of sorting on a range or table
                                </td>
                            </tr>
                            <tr>
                                <td>numAutoFilterItems </td>
                                <td>
                                    Number of items shown in the Auto-filter dropdown
                                </td>
                            </tr>
                            <tr>
                                <td>numDisplayCellChars </td>
                                <td>
                                    Number of characters that can display in a cell
                                </td>
                            </tr>
                            <tr>
                                <td>numPrintCellChars </td>
                                <td>
                                    Number of characters per cell that Excel can print
                                </td>
                            </tr>
                            <tr>
                                <td>numUnqiueCellStyles </td>
                                <td>
                                    Number of unique cell styles in a workbook (combinations of all cell formatting)
                                </td>
                            </tr>
                            <tr>
                                <td>numFormulaLengthChars </td>
                                <td>
                                    Length of formulas in characters
                                </td>
                            </tr>
                            <tr>
                                <td>numFormulaNestingLeve1 </td>
                                <td>
                                    Number of levels of formula nesting
                                </td>
                            </tr>
                            <tr>
                                <td>numFunctionArguments </td>
                                <td>
                                    Number of arguments to a function
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableRows </td>
                                <td>
                                    Number of rows in a pivot table
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableColumns </td>
                                <td>
                                    Number of columns in a pivot table
                                </td>
                            </tr>
                            <tr>
                                <td>numUniquePivotFieldItems </td>
                                <td>
                                    Number of unique items in a pivot field
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableMDXNameChars </td>
                                <td>
                                    Number of characters in a MDX name for a pivot tableitem
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableRelationChars </td>
                                <td>
                                    String length for a relationship pivot table
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableFieldLabelChars </td>
                                <td>
                                    Length of field labels in PivotTable including caption length limitations
                                </td>
                            </tr>
                            <tr>
                                <td>numPivotTableFields </td>
                                <td>
                                    Number of fields in a pivot table
                                </td>
                            </tr>
                            <tr>
                                <td>numSheetXRefArrayFormulas </td>
                                <td>
                                    The number of array formulas in a worksheet that canrefer to another (given) worksheet
                                </td>
                            </tr>
                        </tbody>
                    </table>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>relation (Relationship of Value to Name) </td>
                <td>
                    Specifies how the contents of the value attribute should be interpreted in the context of this characteristic. </br></br>
                    [Example: The following would specify that the application supports from 0 to 10,000 columns, and that column ranges should be interpreted accordingly:</br>
                    `<additionalCharacteristics>`</br>
                    `<characteristic name="numColumns" relation="le" val="10000"/>`</br>
                    `<characteristic name="numColumns" relation="ge" val="0"/>`</br>
                    `</additionalCharacteristics>`</br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Relation simple type (§22.7.3.1).
                </td>
            </tr>
            <tr>
                <td>val (Characteristic Value) </td>
                <td>
                    Specifies the value of the characteristic.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.</br></br>
                </td>
            </tr>
            <tr>
                <td>vocabulary (Characteristic Grammar) </td>
                <td>
                    Specifies a URI defining the characteristic grammar with which the name attribute value shall be interpreted.</br></br>
                    If this attribute is omitted, then the default grammar (as defined above) shall be used.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema anyURI datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Characteristic) is located in [§A.6.7]. end note]

## 22.7.3 简单类型

=== "中文"

    这是专用于附加特性的简单类型的完整列表.

=== "英文"

    **Simple Types**
    
    This is the complete list of simple types dedicated to Additional Characteristics.

### 22.7.3.1 ST_Relation (特性关系类型)

=== "中文"

    这种简单类型指定特性的名称和值属性之间可能的关系.
    
    此简单类型的内容是 W3C XML Schema 字符串数据类型的限制.
    
    此简单类型仅限于下表中列出的值:
    
    <table border=1>
        <thead>
            <tr>
                <th>**枚举值**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>eq (Equal To) </td>
                <td>
                    等于
                </td>
            </tr>
            <tr>
                <td>ge (Greater Than or Equal to) </td>
                <td>
                    大于或等于。
                </td>
            </tr>
            <tr>
                <td>gt (Greater Than) </td>
                <td>
                    大于.
                </td>
            </tr>
            <tr>
                <td>le (Less Than or Equal To) </td>
                <td>
                    小于或等于。
                </td>
            </tr>
            <tr>
                <td>lt (Less Than) </td>
                <td>
                    小于.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 此简单类型的内容模型 (ST_Relation) 的 W3C XML 模式定义位于 [§A.6.7] 中。 end note]

=== "英文"

    **ST_Relation (Characteristic Relationship Types)**

    This simple type specifies the possible relationships between a characteristic's name and value attributes.
    
    This simple type's contents are a restriction of the W3C XML Schema string datatype.
    
    This simple type is restricted to the values listed in the following table:
    
    <table border=1>
        <thead>
            <tr>
                <th>**Enumeration Value**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>eq (Equal To) </td>
                <td>
                    Equal to
                </td>
            </tr>
            <tr>
                <td>ge (Greater Than or Equal to) </td>
                <td>
                    Greater than or equal to.
                </td>
            </tr>
            <tr>
                <td>gt (Greater Than) </td>
                <td>
                    Greater than.
                </td>
            </tr>
            <tr>
                <td>le (Less Than or Equal To) </td>
                <td>
                    Less than or equal to.
                </td>
            </tr>
            <tr>
                <td>lt (Less Than) </td>
                <td>
                    Less than.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this simple type’s content model (ST_Relation) is located in [§A.6.7]. end note]
