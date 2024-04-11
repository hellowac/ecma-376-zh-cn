# 20.1.6 共享样式表

=== "中文"

    DrawingML 中包含的共享样式表方面负责包含格式选项和样式，应用程序可以使用它们来定义文档的某种外观或感觉。 
    任何文档类别（[Note：例如，演示文稿]）都可以使用共享样式表来提取视觉信息，从而以某种方式或主题格式化文档。 共享样式表包含不特定于文档类别的信息。

=== "英文"

    **Shared Style Sheet**

    The shared style sheet aspects contained within DrawingML are responsible for containing formatting options and styles which can be used by applications to define a certain look or feel to documents. The shared style sheet can be used by any document category ([Note: For example, a presentation. end note]) to pull visual information from which formats the document in a certain way, or theme. The shared style sheet contains information that is not document-category specific.

## 20.1.6.1 clrMap (颜色映射)

=== "中文"

    该元素指定颜色映射层，允许用户定义背景和文本的颜色。 这允许交换背景和背景顶部文本的浅色/深色，以保持文本的可读性。
    在更深层次上，这准确指定了配色方案中前 12 个值引用的颜色。

    !!! info "Example"

        考虑以下使用中的颜色图示例：

        ```xml
        <clrMap bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1"
            accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5"
            accent6="accent6" hlink="hlink" folHlink="folHlink"/>
        ```
        
        在此示例中，我们看到 bg1 映射到 lt1，tx1 映射到 dk1，依此类推。

    <table border=1>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    accent1 (强调色 1)
                </td>
                <td>
                    指定与强调色 1 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent2 (强调色 2)
                </td>
                <td>
                    指定与强调色 2 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent3 (强调色 3)
                </td>
                <td>
                    指定与强调色 3 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent4 (强调色 4)
                </td>
                <td>
                    指定与强调色 4 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent5 (强调色 5)
                </td>
                <td>
                    指定与强调色 5 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent6 (强调色 6)
                </td>
                <td>
                    指定与强调色 1 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (背景色 1)
                </td>
                <td>
                    指定与背景色 1 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (背景色 2)
                </td>
                <td>
                    指定与背景色 2 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (已关注的超链接)
                </td>
                <td>
                    指定定义的颜色，该颜色与已关注超链接的颜色相关联.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    hlink (超链接)
                </td>
                <td>
                    指定与超链接颜色关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (文本 1)
                </td>
                <td>
                    指定与第一个文本颜色关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (文本 2) 
                </td>
                <td>
                    指定与第二个文本颜色关联的定义颜色.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ColorMapping) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **clrMap (Color Map)**

    This element specifics the color mapping layer which allows a user to define colors for background and text. This allows for swapping out of light/dark colors for backgrounds and the text on top of the background in order to maintain readability of the text On a deeper level, this specifies exactly which colors the first 12 values refer to in the color scheme.

    !!! info "Example"

        Consider the following example of a color map in use:

        ```xml
        <clrMap bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1"
            accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5"
            accent6="accent6" hlink="hlink" folHlink="folHlink"/>
        ```
        
        In this example, we see that bg1 is mapped to lt1, tx1 is mapped to dk1, and so on.

    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    accent1 (Accent 1)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 1 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent2 (Accent 2)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 2 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent3 (Accent 3)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 3 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 4)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 4 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 5)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 5 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 6)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 6 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (Background 1)
                </td>
                <td>
                    A color defined which is associated as the first background color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (Background 2)
                </td>
                <td>
                    Specifies a color defined which is associated as the second background color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (Followed Hyperlink)
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a followed hyperlink.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    hlink (Hyperlink)
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a hyperlink.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (Text 1)
                </td>
                <td>
                    Specifies a color defined which is associated as the first text color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (Text 2) 
                </td>
                <td>
                    Specifies a color defined which is associated as the second text color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorMapping) is located in §A.4.1. end note]

## 20.1.6.2 clrScheme (颜色方案)

=== "中文"

    该元素定义了一组颜色，称为配色方案。 配色方案负责定义十二种颜色的列表。 这十二种颜色包括六种强调色、两种深色、两种浅色以及每个超链接和已关注超链接的颜色。

    配色方案颜色元素按顺序出现。 以下列表显示了索引值和相应的颜色名称。

    <table border=1>
        <thead>
            <tr>
                <th>**序列索引**</th>
                <th>**元素 (颜色) 名称**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    0
                </td>
                <td>
                    dk1 (暗色 1)
                </td>
            </tr>
            <tr>
                <td>
                    1
                </td>
                <td>
                    lt1 (亮色 1)
                </td>
            </tr>
            <tr>
                <td>
                    2
                </td>
                <td>
                    dk2 (暗色 2)
                </td>
            </tr>
            <tr>
                <td>
                    3
                </td>
                <td>
                    lt2 (亮色 2)
                </td>
            </tr>
            <tr>
                <td>
                    4
                </td>
                <td>
                    accent1 (强调色 1)
                </td>
            </tr>
            <tr>
                <td>
                    5
                </td>
                <td>
                    accent2 (强调色 2)
                </td>
            </tr>
            <tr>
                <td>
                    6
                </td>
                <td>
                    accent3 (强调色 3)
                </td>
            </tr>
            <tr>
                <td>
                    7
                </td>
                <td>
                    accent4 (强调色 4)
                </td>
            </tr>
            <tr>
                <td>
                    8
                </td>
                <td>
                    accent5 (强调色 5)
                </td>
            </tr>
            <tr>
                <td>
                    9
                </td>
                <td>
                    accent6 (强调色 6)
                </td>
            </tr>
            <tr>
                <td>
                    10
                </td>
                <td>
                    hlink (超链接)
                </td>
            </tr>
            <tr>
                <td>
                    11
                </td>
                <td>
                    folHlink (已关注超链接)
                </td>
            </tr>
        </tbody>
    </table>

    !!! info "Example"

        考虑以下在 DrawingML 中定义的配色方案示例:

        ```xml
        <clrScheme name="sample">
            <dk1>
                <sysClr val="windowText" />
            </dk1>
            <lt1>
                <sysClr val="window" />
            </lt1>
            <dk2>
                <srgbClr val="04617B" />
            </dk2>
            <lt2>
                <srgbClr val="DBF5F9" />
            </lt2>
            <accent1>
                <srgbClr val="0F6FC6" />
            </accent1>
            <accent2>
                <srgbClr val="009DD9" />
            </accent2>
            <accent3>
                <srgbClr val="0BD0D9" />
            </accent3>
            <accent4>
                <srgbClr val="10CF9B" />
            </accent4>
            <accent5>
                <srgbClr val="7CCA62" />
            </accent5>
            <accent6>
                <srgbClr val="A5C249" />
            </accent6>
            <hlink>
                <srgbClr val="FF9800" />
            </hlink>
            <folHlink>
                <srgbClr val="F45511" />
            </folHlink>
        </clrScheme>
        ```

        在此示例中，定义了示例配色方案中的 12 种主题颜色.

    <table border=1>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    name (名称)
                </td>
                <td>
                    此配色方案的通用名称。 该名称可以显示在用户界面的配色方案列表中. </bar></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ColorScheme) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **clrScheme (Color Scheme)**

    This element defines a set of colors which are referred to as a color scheme. The color scheme is responsible for defining a list of twelve colors. The twelve colors consist of six accent colors, two dark colors, two light colors and a color for each of a hyperlink and followed hyperlink.

    The Color Scheme Color elements appear in a sequence. The following listing shows the index value and corresponding Color Name.

    <table border=1>
        <thead>
            <tr>
                <th>**Sequence Index**</th>
                <th>**Element (Color) Name**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    0
                </td>
                <td>
                    dk1 (Dark 1)
                </td>
            </tr>
            <tr>
                <td>
                    1
                </td>
                <td>
                    lt1 (Light 1)
                </td>
            </tr>
            <tr>
                <td>
                    2
                </td>
                <td>
                    dk2 (Dark 2)
                </td>
            </tr>
            <tr>
                <td>
                    3
                </td>
                <td>
                    lt2 (Light 2)
                </td>
            </tr>
            <tr>
                <td>
                    4
                </td>
                <td>
                    accent1 (Accent 1)
                </td>
            </tr>
            <tr>
                <td>
                    5
                </td>
                <td>
                    accent2 (Accent 2)
                </td>
            </tr>
            <tr>
                <td>
                    6
                </td>
                <td>
                    accent3 (Accent 3)
                </td>
            </tr>
            <tr>
                <td>
                    7
                </td>
                <td>
                    accent4 (Accent 4)
                </td>
            </tr>
            <tr>
                <td>
                    8
                </td>
                <td>
                    accent5 (Accent 5)
                </td>
            </tr>
            <tr>
                <td>
                    9
                </td>
                <td>
                    accent6 (Accent 6)
                </td>
            </tr>
            <tr>
                <td>
                    10
                </td>
                <td>
                    hlink (Hyperlink)
                </td>
            </tr>
            <tr>
                <td>
                    11
                </td>
                <td>
                    folHlink (Followed Hyperlink)
                </td>
            </tr>
        </tbody>
    </table>

    !!! info "Example"

        Consider the following example of a color scheme defined in DrawingML:

        ```xml
        <clrScheme name="sample">
            <dk1>
                <sysClr val="windowText" />
            </dk1>
            <lt1>
                <sysClr val="window" />
            </lt1>
            <dk2>
                <srgbClr val="04617B" />
            </dk2>
            <lt2>
                <srgbClr val="DBF5F9" />
            </lt2>
            <accent1>
                <srgbClr val="0F6FC6" />
            </accent1>
            <accent2>
                <srgbClr val="009DD9" />
            </accent2>
            <accent3>
                <srgbClr val="0BD0D9" />
            </accent3>
            <accent4>
                <srgbClr val="10CF9B" />
            </accent4>
            <accent5>
                <srgbClr val="7CCA62" />
            </accent5>
            <accent6>
                <srgbClr val="A5C249" />
            </accent6>
            <hlink>
                <srgbClr val="FF9800" />
            </hlink>
            <folHlink>
                <srgbClr val="F45511" />
            </folHlink>
        </clrScheme>
        ```

        In this example, are defined the 12 theme colors in the sample color scheme.

    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    name (Name)
                </td>
                <td>
                    The common name for this color scheme. This name can show up in the user interface in a list of color schemes. </bar></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorScheme) is located in §A.4.1. end note]

## 20.1.6.3 custClrLst (定制颜色列表)

=== "中文"

    该元素允许创建自定义调色板，并与其他配色方案一起显示。 例如，当有人想要维护公司调色板时，这可能非常有用。

    [Note: 该元素内容模型 (CT_CustomColorList) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **custClrLst (Custom Color List)**

    This element allows for a custom color palette to be created and which shows up alongside other color schemes. This can be very useful, for example, when someone would like to maintain a corporate color palette.

    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomColorList) is located in §A.4.1. end note]

## 20.1.6.4 extraClrScheme (额外的配色方案)

=== "中文"

    该元素定义了辅助配色方案，其中包括配色方案和颜色映射。 这主要用于向后兼容性问题和早期版本所需的往返信息。

    !!! info "Example"

        考虑以下在 DrawingML 中使用的额外配色方案示例：

        ```xml
        <extraClrScheme>
            <clrScheme name="extraColorSchemeSample">
                <dk1>
                    <sysClr val="windowText" />
                </dk1>
                <lt1>
                    <sysClr val="window" />
                </lt1>
                <dk2>
                    <srgbClr val="04617B" />
                </dk2>
                <lt2>
                    <srgbClr val="DBF5F9" />
                </lt2>
                <accent1>
                    <srgbClr val="0F6FC6" />
                </accent1>
                <accent2>
                    <srgbClr val="009DD9" />
                </accent2>
                <accent3>
                    <srgbClr val="0BD0D9" />
                </accent3>
                <accent4>
                    <srgbClr val="10CF9B" />
                </accent4>
                <accent5>
                    <srgbClr val="7CCA62" />
                </accent5>
                <accent6>
                    <srgbClr val="A5C249" />
                </accent6>
                <hlink>
                    <srgbClr val="FF9800" />
                </hlink>
                <folHlink>
                    <srgbClr val="F45511" />
                </folHlink>
            </clrScheme>
            <clrMap bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1" accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5" accent6="accent6" hlink="hlink" folHlink="folHlink" />
        </extraClrScheme>
        ```

        在此示例中，额外的配色方案包含一个配色方案和该配色方案的颜色图.

        [Note: 该元素内容模型 (CT_ColorSchemeAndMapping) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **extraClrScheme (Extra Color Scheme)**

    This element defines an auxiliary color scheme, which includes both a color scheme and color mapping. This is mainly used for backward compatibility concerns and roundtrips information required by earlier versions.

    !!! info "Example"

        Consider the following example of an extra color scheme in use in DrawingML:

        ```xml
        <extraClrScheme>
            <clrScheme name="extraColorSchemeSample">
                <dk1>
                    <sysClr val="windowText" />
                </dk1>
                <lt1>
                    <sysClr val="window" />
                </lt1>
                <dk2>
                    <srgbClr val="04617B" />
                </dk2>
                <lt2>
                    <srgbClr val="DBF5F9" />
                </lt2>
                <accent1>
                    <srgbClr val="0F6FC6" />
                </accent1>
                <accent2>
                    <srgbClr val="009DD9" />
                </accent2>
                <accent3>
                    <srgbClr val="0BD0D9" />
                </accent3>
                <accent4>
                    <srgbClr val="10CF9B" />
                </accent4>
                <accent5>
                    <srgbClr val="7CCA62" />
                </accent5>
                <accent6>
                    <srgbClr val="A5C249" />
                </accent6>
                <hlink>
                    <srgbClr val="FF9800" />
                </hlink>
                <folHlink>
                    <srgbClr val="F45511" />
                </folHlink>
            </clrScheme>
            <clrMap bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1" accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5" accent6="accent6" hlink="hlink" folHlink="folHlink" />
        </extraClrScheme>
        ```

        In this example, the extra color scheme contains a color scheme and a color map for that color scheme.

        [Note: The W3C XML Schema definition of this element’s content model (CT_ColorSchemeAndMapping) is located in §A.4.1. end note]

## 20.1.6.5 extraClrSchemeLst (额外配色方案列表)

=== "中文"

    该元素是文档中存在的额外配色方案列表的容器.

    [Note: 该元素内容模型 (CT_ColorSchemeList) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **extraClrSchemeLst (Extra Color Scheme List)**

    This element is a container for the list of extra color schemes present in a document.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorSchemeList) is located in §A.4.1. end note]

## 20.1.6.6 masterClrMapping (主颜色映射)

=== "中文"

    该元素是在文档中使用颜色映射的选择的一部分。 还定义了 overrideClrMapping (§20.1.6.8) 元素，当指定该元素时，将使用覆盖而不是主文件中定义的颜色映射。 如果指定了该元素，那么我们将专门使用 master.xml 中定义的颜色映射。
    
    [Note: 该元素内容模型 (CT_EmptyElement) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **masterClrMapping (Master Color Mapping)**

    This element is a part of a choice for which color mapping is used within the document. There is also defined an overrideClrMapping (§20.1.6.8) element which, when specified, the override is used rather than the color mapping defined in the master. If this element is specified, then we specifically use the color mapping defined in the master.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_EmptyElement) is located in §A.4.1. end note]

## 20.1.6.7 objectDefaults (对象默认属性)

=== "中文"

    该元素允许定义默认形状、线条和文本框格式属性。 应用程序可以在插入文档时使用此信息来格式化形状（或文本）。

    [Note: 该元素内容模型 (CT_ObjectStyleDefaults) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **objectDefaults (Object Defaults)**

    This element allows for the definition of default shape, line, and textbox formatting properties. An application can use this information to format a shape (or text) initially on insertion into a document.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ObjectStyleDefaults) is located in §A.4.1. end note]

## 20.1.6.8 overrideClrMapping (颜色映射覆盖)

=== "中文"

    此元素提供文档中颜色映射的覆盖。 定义后，此颜色映射将用于代替已定义的颜色映射或主颜色映射。 此颜色映射的定义方式与本文档中的其他映射相同。

    !!! info "Example"

        请考虑以下 DrawingML 中的覆盖颜色映射示例：

        ```xml
        <overrideClrMapping bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1"
            accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5"
            accent6="accent6" hlink="hlink" folHlink="folHlink"/>
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
                <td>
                    accent1 (强调色 1)
                </td>
                <td>
                    指定与强调色 1 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    accent2 (强调色 2)
                </td>
                <td>
                    指定与强调色 2 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    accent3 (强调色 3)
                </td>
                <td>
                    指定与强调色 3 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    accent4 (强调色 4)
                </td>
                <td>
                    指定与强调色 4 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    accent5 (强调色 5)
                </td>
                <td>
                    指定与强调色 5 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    accent6 (强调色 6)
                </td>
                <td>
                    指定与强调色 6 关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (背景色 1)
                </td>
                <td>
                    定义为第一个背景颜色的颜色.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (背景色 2)
                </td>
                <td>
                    指定与第二背景颜色关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (已关注超链接)
                </td>
                <td>
                    指定定义的颜色，该颜色与已关注超链接的颜色相关联.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    hlink (超链接)
                </td>
                <td>
                    指定与超链接颜色关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (文本 1)
                </td>
                <td>
                    指定与第一个文本颜色关联的颜色定义.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (文本 2) 
                </td>
                <td>
                    指定与第二个文本颜色关联的定义颜色.</br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型 (§20.1.10.14) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ColorMapping) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **overrideClrMapping (Override Color Mapping)**

    This element provides an override for the color mapping in a document. When defined, this color mapping is used in place of the already defined color mapping, or master color mapping. This color mapping is defined in the same manner as the other mappings within this document.

    !!! info "Example"

        Consider the following example of an override color mapping in DrawingML:

        ```xml
        <overrideClrMapping bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1"
            accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5"
            accent6="accent6" hlink="hlink" folHlink="folHlink"/>
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
                <td>
                    accent1 (Accent 1)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 1 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent2 (Accent 2)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 2 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent3 (Accent 3)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 3 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 4)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 4 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 5)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 5 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 6)
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 6 color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (Background 1)
                </td>
                <td>
                    A color defined which is associated as the first background color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (Background 2)
                </td>
                <td>
                    Specifies a color defined which is associated as the second background color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (Followed Hyperlink)
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a followed hyperlink.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    hlink (Hyperlink)
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a hyperlink.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (Text 1)
                </td>
                <td>
                    Specifies a color defined which is associated as the first text color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (Text 2) 
                </td>
                <td>
                    Specifies a color defined which is associated as the second text color.</br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorMapping) is located in §A.4.1. end note]

## 20.1.6.9 theme (主题)

=== "中文"

    该元素定义与共享样式表（或主题）关联的根级复杂类型。 该元素通过主题保存文档可用的所有不同格式选项，并定义在文档中使用主题对象时文档的整体外观和感觉。

    !!! info "Example"

        将下图视为应用于演示文稿的不同主题的示例:

        ![123](./imgs/20dml-17.png)

        在此示例中，我们了解主题如何影响演示文稿中不同对象的字体、颜色、背景、填充和效果。

    <table border=1>
        <thead>
            <tr>
                <th>**属性**</th>
                <th>**描述**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    name (名称)
                </td>
                <td>
                    指定主题的名称. </bar></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_OfficeStyleSheet) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **theme (Theme)**

    This element defines the root level complex type associated with a shared style sheet (or theme). This element holds all the different formatting options available to a document through a theme and defines the overall look and feel of the document when themed objects are used within the document.

    !!! info "Example"

        Consider the following image as an example of different themes in use applied to a presentation:

        ![123](./imgs/20dml-17.png)

        In this example, we see how a theme can affect font, colors, backgrounds, fills, and effects for different objects in a presentation.

    <table border=1>
        <thead>
            <tr>
                <th>**Attributes**</th>
                <th>**Description**</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    name (Name)
                </td>
                <td>
                    Specifies the name given to the theme. </bar></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_OfficeStyleSheet) is located in §A.4.1. end note]

## 20.1.6.10 themeElements (主题元素集)

=== "中文"

    该元素定义主题的主题格式选项，并且是主题的主力。 这是文档包含和使用大部分共享主题信息的地方。 此元素包含颜色方案、字体方案和格式方案元素，它们定义主题定义的不同格式方面。

    !!! info "Example"

        考虑以下在 DrawingML 中定义的主题元素示例：

        ```xml
        <themeElements>
            <clrScheme name="sample">
            …
            </clrScheme>
            <fontScheme name="sample">
            …
            </fontScheme>
            <fmtScheme name="sample">
                <fillStyleLst>
                …
                </fillStyleLst>
                <lnStyleLst>
                …
                </lnStyleLst>
                <effectStyleLst>
                …
                </effectStyleLst>
                <bgFillStyleLst>
                …
                </bgFillStyleLst>
            </fmtScheme>
        </themeElements>
        ```

        在这个例子中，我们看到了主题元素如何定义的基本结构，并省略了每个单独部分的真正内容以节省空间。 每个部分（颜色方案、字体方案、格式方案）均在 DrawingML 中的其他位置定义。

        [Note: 该元素内容模型 (CT_BaseStyles) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **themeElements (Theme Elements)**

    This element defines the theme formatting options for the theme and is the workhorse of the theme. This is where the bulk of the shared theme information is contained and used by a document. This element contains the color scheme, font scheme, and format scheme elements which define the different formatting aspects of what a theme defines.

    !!! info "Example"

        Consider the following example of a theme elements defined in DrawingML:

        ```xml
        <themeElements>
            <clrScheme name="sample">
            …
            </clrScheme>
            <fontScheme name="sample">
            …
            </fontScheme>
            <fmtScheme name="sample">
                <fillStyleLst>
                …
                </fillStyleLst>
                <lnStyleLst>
                …
                </lnStyleLst>
                <effectStyleLst>
                …
                </effectStyleLst>
                <bgFillStyleLst>
                …
                </bgFillStyleLst>
            </fmtScheme>
        </themeElements>
        ```

        In this example, we see the basic structure of how a theme elements is defined and have left out the true guts of each individual piece to save room. Each part (color scheme, font scheme, format scheme) is defined elsewhere within DrawingML.

        [Note: The W3C XML Schema definition of this element’s content model (CT_BaseStyles) is located in §A.4.1. end note]

## 20.1.6.11 themeManager (主题管理器)

=== "中文"

    主题文件的起始部件。

    [Note: 该元素内容模型 (CT_EmptyElement) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **themeManager (Theme Manager)**

    The starting part for a theme file.

    [Note: The W3C XML Schema definition of this element’s content model (CT_EmptyElement) is located in §A.4.1. end note]

## 20.1.6.12 themeOverride (主题覆盖)

=== "中文"

    此元素允许进行覆盖，仅更改单个对象（例如表格）的颜色、字体或效果。 目前，它仅用于控制演示文稿中非顶级母版的覆盖。

    [Note: 该元素内容模型 (CT_BaseStylesOverride) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **themeOverride (Theme Override)**

    This element allows for an override which changes just the colors, fonts, or effects of a single object, like a table for example. Currently it is used only to control overrides on the non-top-level masters within a presentation.

    [Note: The W3C XML Schema definition of this element’s content model (CT_BaseStylesOverride) is located in §A.4.1. end note]
