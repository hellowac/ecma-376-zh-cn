# 19.3 Slides

=== "中文"

    PresentationML 框架的幻灯片部分存储与各种幻灯片类型的幻灯片相关的所有信息。 这些幻灯片类型和相应的部分可以分为三个不同的部件，即幻灯片(Slides)、嵌入对象(Embedded Objects)和可编程标签(Programmable Tags)。

=== "英文"

    **Slides**

    The Slides portion of the PresentationML framework stores all information pertaining specifically to slides of various slide types. These slide types and corresponding parts can be broken down into three distinct parts, namely slides, embedded objects, and programmable tags.

## 19.3.1 幻灯片

=== "中文"

    作为PresentationML 这一部分的主要部件，幻灯片元素包含幻灯片中要包含的所有数据。 考虑幻灯片的最佳方式是容纳该幻灯片上所有数据的容器。 幻灯片中的具体形状、图像和关系在这里不发挥作用。 这里的元素涉及可以在PresentationML中描述的六种不同的幻灯片类型，即**幻灯片**、**幻灯片布局**、**幻灯片母版**、**讲义母版**、**笔记母版**和**笔记幻灯片**。

=== "英文"

    **Slides**

    Being the main segment of this section of PresentationML, the slides elements encompass all data that is to be contained within a slide. The best way to think of a slide is a container for all data that is to be on that slide. The specific shapes, images and relations within a slide do not come into play here. The elements here pertain to the six different slide types that can be described within PresentationML, namely slide, slide layout, slide master, handout master, notes master and notes slide.

### 19.3.1.1 bg (幻灯片背景)

=== "中文"

    此元素指定幻灯片的背景外观信息。 幻灯片背景覆盖整个幻灯片，在不存在对象的情况下可见，并作为透明对象的背景。

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
                    bwMode (黑白模式)
                </td>
                <td>
                    指定应仅使用黑色和白色来渲染背景。 也就是说，在渲染图片时，背景的颜色信息应该转换为黑色或白色. </br></br>
                    [Note: 渲染此背景时不使用灰色，仅使用纯黑和纯白. end note] </br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型定义 (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Background) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **bg (Slide Background)**
    
    This element specifies the background appearance information for a slide. The slide background covers the entire slide and is visible where no objects exist and as the background for transparent objects.

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
                    bwMode (Black and White Mode)
                </td>
                <td>
                    Specifies that the background should be rendered using only black and white coloring. That is, the coloring information for the background should be converted to either black or white when rendering the picture. </br></br>
                    [Note: No gray is to be used in rendering this background, only stark black and stark  white. end note] </br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Background) is located in §A.3. end note]

### 19.3.1.2 bgPr (背景属性)

=== "中文"

    该元素指定用于渲染幻灯片背景的视觉效果。 这包括构成幻灯片背景的任何填充、图像或效果。

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
                    shadeToTitle (阴影到标题)
                </td>
                <td>
                    指定幻灯片的背景是否为标题背景类型的阴影。 这种渐变填充位于幻灯片背景上，并根据幻灯片标题占位符的位置而变化。 一个例子如下所示. </br></br>
                    ![asdf](./imgs/19pml-2.png)</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_BackgroundProperties) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **bgPr (Background Properties)**

    This element specifies visual effects used to render the slide background. This includes any fill, image, or effects that are to make up the background of the slide.

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
                    shadeToTitle (Shade to Title)
                </td>
                <td>
                    Specifies whether the background of the slide is of a shade to title background type. This kind of gradient fill is on the slide background and changes based on the placement of the slide title placeholder. An example is shown below. </br></br>
                    ![asdf](./imgs/19pml-2.png)</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_BackgroundProperties) is located in §A.3. end note]

### 19.3.1.3 bgRef (背景样式参考)

=== "中文"

    该元素指定幻灯片背景使用样式矩阵中定义的填充样式。 idx 属性指的是背景填充样式或演示文稿样式矩阵中的填充样式的索引，由 fmtScheme 元素定义。 值 0 或 1000 表示无背景，值 1-999 指 fillStyleLst 元素内的填充样式的索引，值 1001 及以上指 bgFillStyleLst 元素内的背景填充样式的索引。 值 1001 对应于第一个背景填充样式，1002 对应于第二个背景填充样式，依此类推。

    !!! info "Example"

        ```xml
        <p:bgRef idx="2">
            <a:schemeClr val="bg2"/>
        </p:bgRef>
        ```
        
        上面的代码指示使用配色方案的第二背景颜色的样式的第二填充样式的幻灯片背景。

    !!! info "Example"

        ```xml
        <p:bgRef idx="1001">
            <a:schemeClr val="bg2"/>
        </p:bgRef>
        ```
        
        上面的代码指示幻灯片背景具有样式的第一个背景填充样式，使用配色方案的第二个背景颜色。

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
                    idx (风格矩阵索引)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定所引用样式的样式矩阵索引. </br></br>
                    此属性的可能值由 ST_StyleMatrixColumnIndex 简单类型定义 (§20.1.10.57).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_StyleMatrixReference) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **bgRef (Background Style Reference)**

    This element specifies the slide background is to use a fill style defined in the style matrix. The idx attribute refers to the index of a background fill style or fill style within the presentation's style matrix, defined by the fmtScheme element. A value of 0 or 1000 indicates no background, values 1-999 refer to the index of a fill style within the fillStyleLst element, and values 1001 and above refer to the index of a background fill style within the bgFillStyleLst element. The value 1001 corresponds to the first background fill style, 1002 to the second background fill style, and so on. 

    !!! info "Example"

        ```xml
        <p:bgRef idx="2">
            <a:schemeClr val="bg2"/>
        </p:bgRef>
        ```
        
        The above code indicates a slide background with the style's second fill style using the second background color of the color scheme. 

    !!! info "Example"

        ```xml
        <p:bgRef idx="1001">
            <a:schemeClr val="bg2"/>
        </p:bgRef>
        ```
        
        The above code indicates a slide background with the style's first background fill style using the second background color of the color scheme. 

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
                    idx (Style Matrix Index)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the style matrix index of the style referred to. </br></br>
                    The possible values for this attribute are defined by the ST_StyleMatrixColumnIndex simple type (§20.1.10.57).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_StyleMatrixReference) is located in §A.4.1. end note]

### 19.3.1.4 blipFill (图片填充)

=== "中文"

    该元素指定图片对象具有的图片填充类型。 由于默认情况下图片已具有图片填充，因此可以为图片对象指定两种填充。 下面显示了一个示例。

    !!! info "Example"

        考虑下面应用了斑点填充的图片。 用于填充该图片对象的图像具有透明像素而不是白色像素。

        ```xml
        <p:pic>
            …
            <p:blipFill>
                <a:blip r:embed="rId2"/>
                <a:stretch>
                    <a:fillRect/>
                </a:stretch>
            </p:blipFill>
            …
        </p:pic>
        ```

        ![19pml-3.png](./imgs/19pml-3.png)
        
        上面的图片对象显示为该填充类型的示例. 

    !!! info "Example"

        现在考虑相同的图片对象，但在图片的形状属性部分应用了额外的渐变填充。

        ```xml
        <p:pic>
            …
            <p:blipFill>
                <a:blip r:embed="rId2"/>
                <a:stretch>
                    <a:fillRect/>
                </a:stretch>
            </p:blipFill>
            <p:spPr>
                <a:gradFill>
                    <a:gsLst>
                        <a:gs pos="0">
                            <a:schemeClr val="tx2">
                                <a:shade val="50000"/>
                            </a:schemeClr>
                        </a:gs>
                        <a:gs pos="39999">
                            <a:schemeClr val="tx2">
                                <a:tint val="20000"/>
                            </a:schemeClr>
                        </a:gs>
                        <a:gs pos="70000">
                            <a:srgbClr val="C4D6EB"/>
                        </a:gs>
                        <a:gs pos="100000">
                            <a:schemeClr val="bg1"/>
                        </a:gs>
                    </a:gsLst>
                </a:gradFill>
            </p:spPr>
            …
        </p:pic>
        ```

        ![19pml-4.png](./imgs/19pml-4.png)
        
        上面的图片对象显示为这种双重填充类型的示例。

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
                    dpi (DPI Setting)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the DPI (dots per inch) used to calculate the size of the blip. If not present or zero, the DPI in the blip is used. </br></br>
                    [Note: This attribute is primarily used to keep track of the picture quality within a document. There are different levels of quality needed for print than on-screen viewing and thus a need to track this information. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype .
                </td>
            </tr>
            <tr>
                <td>
                    rotWithShape(Rotate With Shape)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies that the fill should rotate with the shape. That is, when the shape that has been filled with a picture and the containing shape (say a rectangle) is transformed with a rotation then the fill is transformed with the same rotation. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_BlipFillProperties) is located in §A.4.1. end note]

=== "英文"

    **blipFill (Picture Fill)**

    This element specifies the kind of picture fill that the picture object has. Because a picture has a picture fill already by default, it is possible to have two fills specified for a picture object. An example of this is shown below.

    !!! info "Example"

        Consider the picture below that has a blip fill applied to it. The image used to fill this picture object has transparent pixels instead of white pixels.

        ```xml
        <p:pic>
            …
            <p:blipFill>
                <a:blip r:embed="rId2"/>
                <a:stretch>
                    <a:fillRect/>
                </a:stretch>
            </p:blipFill>
            …
        </p:pic>
        ```

        ![19pml-3.png](./imgs/19pml-3.png)
        
        The above picture object is shown as an example of this fill type. 

    !!! info "Example"

        Consider now the same picture object but with an additional gradient fill applied within the shape properties portion of the picture.

        ```xml
        <p:pic>
            …
            <p:blipFill>
                <a:blip r:embed="rId2"/>
                <a:stretch>
                    <a:fillRect/>
                </a:stretch>
            </p:blipFill>
            <p:spPr>
                <a:gradFill>
                    <a:gsLst>
                        <a:gs pos="0">
                            <a:schemeClr val="tx2">
                                <a:shade val="50000"/>
                            </a:schemeClr>
                        </a:gs>
                        <a:gs pos="39999">
                            <a:schemeClr val="tx2">
                                <a:tint val="20000"/>
                            </a:schemeClr>
                        </a:gs>
                        <a:gs pos="70000">
                            <a:srgbClr val="C4D6EB"/>
                        </a:gs>
                        <a:gs pos="100000">
                            <a:schemeClr val="bg1"/>
                        </a:gs>
                    </a:gsLst>
                </a:gradFill>
            </p:spPr>
            …
        </p:pic>
        ```

        ![19pml-4.png](./imgs/19pml-4.png)
        
        The above picture object is shown as an example of this double fill type. 

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
                    dpi (DPI Setting)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the DPI (dots per inch) used to calculate the size of the blip. If not present or zero, the DPI in the blip is used. </br></br>
                    [Note: This attribute is primarily used to keep track of the picture quality within a document. There are different levels of quality needed for print than on-screen viewing and thus a need to track this information. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype .
                </td>
            </tr>
            <tr>
                <td>
                    rotWithShape(Rotate With Shape)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies that the fill should rotate with the shape. That is, when the shape that has been filled with a picture and the containing shape (say a rectangle) is transformed with a rotation then the fill is transformed with the same rotation. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_BlipFillProperties) is located in §A.4.1. end note]

### 19.3.1.5 bodyStyle (幻灯片母版正文文本样式)

=== "中文"

    此元素指定母版幻灯片中所有正文文本的文本格式样式。 此格式适用于与该母版相关的演示文稿幻灯片中的所有正文文本。 文本格式是通过利用 DrawingML 框架来指定的，就像在常规演示幻灯片中一样。 在 bodyStyle 元素中可以定义许多不同的样式类型，因为幻灯片正文中存储了不同类型的文本。
    
    [Note: 该元素内容模型 (CT_TextListStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **bodyStyle (Slide Master Body Text Style)**

    This element specifies the text formatting style for all body text within a master slide. This formatting is used on all body text within presentation slides related to this master. The text formatting is specified by utilizing the DrawingML framework just as within a regular presentation slide. Within the bodyStyle element there can be many different style types defined as there are different kinds of text stored within the body of a slide.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_TextListStyle) is located in §A.4.1. end note]

### 19.3.1.6 clrMap (配色方案图)

=== "中文"

    此元素指定将一种颜色方案定义转换为另一种颜色方案定义的映射层。 每个属性代表一个在这个master中可以引用的颜色名称，其值为主题中对应的颜色。

    !!! info "Example"

        考虑以下适用于幻灯片母版的颜色映射：

        ```xml
        <p:clrMap bg1="dk1" tx1="lt1" bg2="dk2" tx2="lt2" accent1="accent1"
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
                    accent1 (强调色 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 1 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (强调色 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 2 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (强调色 3)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 3 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (强调色 4)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 4 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (强调色 5)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 5 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (强调色 6)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与强调 6 颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (Background 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    定义为第一个背景颜色的颜色. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (Background 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    定义为第二个背景颜色的颜色. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (Followed Hyperlink)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定定义的颜色，该颜色与后续超链接的颜色相关联. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    hlink (Hyperlink)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与超链接颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (Text 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与第一个文本颜色关联的颜色定义. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (Text 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定与第二个文本颜色关联的定义颜色. </br></br>
                    该属性的可能值由 ST_ColorSchemeIndex 简单类型定义 (§20.1.10.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ColorMapping) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **clrMap (Color Scheme Map)**

    This element specifies the mapping layer that transforms one color scheme definition to another. Each attribute represents a color name that can be referenced in this master, and the value is the corresponding color in the theme.

    !!! info "Example"

        Consider the following mapping of colors that applies to a slide master:

        ```xml
        <p:clrMap bg1="dk1" tx1="lt1" bg2="dk2" tx2="lt2" accent1="accent1"
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
                    accent1 (Accent 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 1 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 2 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 3)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 3 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 4)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 4 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 5)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 5 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    accent1 (Accent 6)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the accent 6 color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg1 (Background 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    A color defined which is associated as the first background color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    bg2 (Background 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the second background color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    folHlink (Followed Hyperlink)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a followed hyperlink. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    hlink (Hyperlink)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the color for a hyperlink. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx1 (Text 1)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the first text color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
            <tr>
                <td>
                    tx2 (Text 2)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a color defined which is associated as the second text color. </br></br>
                    The possible values for this attribute are defined by the ST_ColorSchemeIndex simple type (§20.1.10.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorMapping) is located in §A.4.1. end note]

### 19.3.1.7 clrMapOvr (配色方案地图覆盖)

=== "中文"

    该元素提供了一种机制，用于覆盖 ClrMap 元素中列出的颜色方案。 如果 masterClrMapping 元素存在，则使用 master 定义的配色方案。 如果 overrideClrMapping 元素存在，它将定义特定于父笔记幻灯片、演示文稿幻灯片或幻灯片布局的新配色方案。
    
    [Note: 该元素内容模型 (CT_ColorMappingOverride) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **clrMapOvr (Color Scheme Map Override)**

    This element provides a mechanism with which to override the color schemes listed within the ClrMap element. If the masterClrMapping element is present, the color scheme defined by the master is used. If the overrideClrMapping element is present, it defines a new color scheme specific to the parent notes slide, presentation slide, or slide layout.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_ColorMappingOverride) is located in §A.4.1. end note]

### 19.3.1.8 cNvCxnSpPr (非可视连接器形状绘图属性)

=== "中文"

    此元素指定特定于连接器形状的非可视绘图属性。 这包括指定连接器形状所连接的形状的信息。
    
    [Note: 该元素内容模型 (CT_NonVisualConnectorProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvCxnSpPr (Non-Visual Connector Shape Drawing Properties)**

    This element specifies the non-visual drawing properties specific to a connector shape. This includes information specifying the shapes to which the connector shape is connected.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualConnectorProperties) is located in §A.4.1. end note]

### 19.3.1.9 cNvGraphicFramePr (非可视图形框架绘图属性)

=== "中文"

    该元素指定图形框架的非可视绘图属性。 这些非视觉属性是生成应用程序在渲染幻灯片表面时将使用的属性。

    [Note: 该元素内容模型 (CT_NonVisualGraphicFrameProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvGraphicFramePr (Non-Visual Graphic Frame Drawing Properties)**

    This element specifies the non-visual drawing properties for a graphic frame. These non-visual properties are properties that the generating application would utilize when rendering the slide surface.

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualGraphicFrameProperties) is located in §A.4.1. end note]

### 19.3.1.10 cNvGrpSpPr (非可视组合形状绘图属性)

=== "中文"

    此元素指定组形状的非可视绘图属性。 这些非视觉属性是生成应用程序在渲染幻灯片表面时将使用的属性。
    
    [Note: 此元素内容模型 (CT_NonVisualGroupDrawingShapeProps) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)**

    This element specifies the non-visual drawing properties for a group shape. These non-visual properties are properties that the generating application would utilize when rendering the slide surface.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualGroupDrawingShapeProps) is located in §A.4.1. end note]

### 19.3.1.11 cNvPicPr (非视觉绘图属性)

=== "中文"

    该元素指定图片画布的非视觉属性。 生成应用程序将使用这些属性来确定如何更改所讨论的图片对象的某些属性。

    !!! info "Example"

        考虑以下 DrawingML。

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                <p:cNvPr id="4" name="Lilly_by_Lisher.jpg"/>
                <p:cNvPicPr>
                    <a:picLocks noChangeAspect="1"/>
                </p:cNvPicPr>
                <p:nvPr/>
            </p:nvPicPr>
            …
        </p:pic>
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
                    preferRelativeResize (首选相对调整大小)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定用户界面是否应根据图片的当前大小或其原始大小显示图片的大小调整。 如果此属性设置为 true，则缩放是相对于原始图片大小而不是当前图片大小。</br></br>
                    [Example: 考虑这样的情况：文档中的图片大小已调整，现在是原始插入图片大小的 50%。 现在，如果用户选择稍后在生成应用程序中调整该图片的大小，则应检查该属性的值.</br></br>
                    如果此属性设置为 true，则显示值 50%。 同样，如果此属性设置为 false，则应显示 100% 的值，因为图片尚未从其当前（较小）尺寸调整大小。 end example]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 该元素内容模型 (CT_NonVisualPictureProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvPicPr (Non-Visual Picture Drawing Properties)**

    This element specifies the non-visual properties for the picture canvas. These properties are to be used by the generating application to determine how certain properties are to be changed for the picture object in question.

    !!! info "Example"

        Consider the following DrawingML.

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                <p:cNvPr id="4" name="Lilly_by_Lisher.jpg"/>
                <p:cNvPicPr>
                    <a:picLocks noChangeAspect="1"/>
                </p:cNvPicPr>
                <p:nvPr/>
            </p:nvPicPr>
            …
        </p:pic>
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
                    preferRelativeResize (Relative Resize Preferred)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies if the user interface should show the resizing of the picture based on the picture's current size or its original size. If this attribute is set to true, then scaling is relative to the original picture size as opposed to the current picture size. </br></br>
                    [Example: Consider the case where a picture has been resized within a document and is now 50% of the originally inserted picture size. Now if the user chooses to make a later adjustment to the size of this picture within the generating application, then the value of this attribute should be checked.</br></br>
                    If this attribute is set to true then a value of 50% is shown. Similarly, if this attribute is setto false, then a value of 100% should be shown because the picture has not yet been resized from its current (smaller) size. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualPictureProperties) is located in §A.4.1. end note]

### 19.3.1.12 cNvPr (非可视绘图属性)

=== "中文"

    该元素指定非可视画布属性。 这允许存储不影响图片外观的附加信息。

    !!! info "Example"

        考虑以下 DrawingML.

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                <p:cNvPr id="4" name="Lilly_by_Lisher.jpg"/>
            </p:nvPicPr>
            …
        </p:pic>
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
                    descr (对象的替代文本)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定当前 DrawingML 对象的替代文本，供不显示当前对象的辅助技术或应用程序使用. </br></br>
                    如果省略此元素，则父对象不存在替代文本.</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    ‵<… descr="A picture of a bowl of fruit">‵</br></br>
                    descr 属性包含可替代实际 DrawingML 对象的替代文本. end example]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    hidden (隐藏)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定是否显示此 DrawingML 对象。 当 DrawingML 对象在文档中显示时，该对象可以被隐藏（即存在，但不可见）。 该属性决定对象是渲染还是隐藏。 [Note: 应用程序可以具有允许查看该对象的设置。 end note]</br></br>
                    如果省略此属性，则应显示父 DrawingML 对象 (比如, 不隐藏).</br></br>
                    [Example: 考虑一个必须隐藏在文档内容中的内联 DrawingML 对象。 该设置将指定如下:</br></br>
                    `<… hidden="true" />`</br></br>
                    hide 属性的值为 true，它指定 DrawingML 对象是隐藏的，并且在显示文档时不显示。 end example]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    id (唯一标识符)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定当前文档中当前 DrawingML 对象的唯一标识符。 该 ID 可用于帮助唯一标识该对象，以便文档的其他部分可以引用它.</br></br>
                    如果同一文档中的多个对象共享相同的 id 属性值，则该文档应被视为不合格.</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `<… id="10" … >`</br></br>
                    id 属性的值为 10，这是此 DrawingML 对象的唯一标识符。 end example]</br></br>
                    该属性的可能值由 ST_DrawingElementId 简单类型定义 (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    name (名称)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定对象的名称。 [注：通常，这用于存储图片对象的原始文件名. end note]</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `< … name="foo.jpg" >`</br></br>
                    name 属性的值为 foo.jpg，这是此 DrawingML 对象的名称. end example]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    title (标题)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定当前 DrawingML 对象的标题 (caption). </br></br>
                    如果省略此属性，则父对象不存在标题文本.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… title="Process Flow Diagram">`</br></br>
                    end example]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_NonVisualDrawingProps) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvPr (Non-Visual Drawing Properties)**

    This element specifies non-visual canvas properties. This allows for additional information that does not affect the appearance of the picture to be stored.

    !!! info "Example"

        Consider the following DrawingML.

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                <p:cNvPr id="4" name="Lilly_by_Lisher.jpg"/>
            </p:nvPicPr>
            …
        </p:pic>
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
                    descr (Alternative Text for Object)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies alternative text for the current DrawingML object, for use by assistive technologies or applications which do not display the current object. </br></br>
                    If this element is omitted, then no alternative text is present for the parent object.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    ‵<… descr="A picture of a bowl of fruit">‵</br></br>
                    The descr attribute contains alternative text which can be used in place of the actual DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    hidden (Hidden)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies whether this DrawingML object is displayed. When a DrawingML object is displayed within a document, that object can be hidden (i.e., present, but not visible). This attribute determines whether the object is rendered or made hidden. [Note: An application can have settings which allow this object to be viewed. end note]</br></br>
                    If this attribute is omitted, then the parent DrawingML object shall be displayed (i.e., not hidden).</br></br>
                    [Example: Consider an inline DrawingML object which must be hidden within the document's content. This setting would be specified as follows:</br></br>
                    `<… hidden="true" />`</br></br>
                    The hidden attribute has a value of true, which specifies that the DrawingML object is hidden and not displayed when the document is displayed. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    id (Unique Identifier)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a unique identifier for the current DrawingML object within the current document. This ID can be used to assist in uniquely identifying this object so that it can be referred to by other parts of the document.</br></br>
                    If multiple objects within the same document share the same id attribute value, then the document shall be considered non-conformant.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… id="10" … >`</br></br>
                    The id attribute has a value of 10, which is the unique identifier for this DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the ST_DrawingElementId simple type (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    name (Name)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the name of the object. [Note: Typically, this is used to store the original file name of a picture object. end note]</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `< … name="foo.jpg" >`</br></br>
                    The name attribute has a value of foo.jpg, which is the name of this DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    title (Title)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the title (caption) of the current DrawingML object. </br></br>
                    If this attribute is omitted, then no title text is present for the parent object.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… title="Process Flow Diagram">`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualDrawingProps) is located in §A.4.1. end note]

### 19.3.1.13 cNvSpPr (形状的非可视绘图属性)

=== "中文"

    该元素指定形状的非可视绘图属性。 生成应用程序将使用这些属性来确定如何处理形状

    !!! info "Example"

        考虑应用了形状锁定的形状.

        ```xml
        <p:sp>
            <p:nvSpPr>
                <p:cNvPr id="2" name="Rectangle 1"/>
                <p:cNvSpPr>
                    <a:spLocks noGrp="1"/>
                </p:cNvSpPr>
            </p:nvSpPr>
            …
        </p:sp>
        ```

        此形状锁存储在该形状的非可视绘图属性中.

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
                    txBox (文本框)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定相应的形状是文本框，因此生成应用程序应将其视为文本框。 如果省略此属性，则假定相应的形状不是特定的文本框. </br></br>
                    [Note: 由于形状未指定为文本框，并不意味着它不能附加文本。 文本框只是具有特定属性的特殊形状. end note]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_NonVisualDrawingShapeProps) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvSpPr (Non-Visual Drawing Properties for a Shape)**

    This element specifies the non-visual drawing properties for a shape. These properties are to be used by the generating application to determine how the shape should be dealt with 

    !!! info "Example"

        Consider the shape that has a shape lock applied to it.

        ```xml
        <p:sp>
            <p:nvSpPr>
                <p:cNvPr id="2" name="Rectangle 1"/>
                <p:cNvSpPr>
                    <a:spLocks noGrp="1"/>
                </p:cNvSpPr>
            </p:nvSpPr>
            …
        </p:sp>
        ```

        This shape lock is stored within the non-visual drawing properties for this shape.

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
                    txBox (Text Box)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies that the corresponding shape is a text box and thus should be treated as such by the generating application. If this attribute is omitted then it is assumed that the corresponding shape is not specifically a text box. </br></br>
                    [Note: Because a shape is not specified to be a text box does not mean that it cannot have text attached to it. A text box is merely a specialized shape with specific properties. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualDrawingShapeProps) is located in §A.4.1. end note]

### 19.3.1.14 contentPart (内容部分)

=== "中文"

    此元素指定对 XML 内容的引用，其格式未由 ECMA-376 定义。 
    
    !!! info "Note"
        
        这部分允许本机使用其他常用的交换格式，例如：

        - MathML (http://www.w3.org/TR/MathML2/)
        - SMIL (http://www.w3.org/TR/REC-smil/)
        - SVG (http://www.w3.org/TR/SVG11/)
    
    此元素指定的显式关系的关系类型应为 http://purl.oclc.org/ooxml/officeDocument/relationships/customXml，并且 TargetMode 属性值为 Internal。 如果应用程序无法处理目标部分指定的内容类型的内容，则它应该继续处理该文件。 如果可能的话，它还应该提供一些指示，表明未导入未知内容。

    [Note: 为了更好的互操作性，应仅使用标准 XML 格式. end note]
    
    !!! info "Example"
        
        考虑一个 PresentationML 文档，其中在名为smil1.xml 的部件中包含以下 SMIL 标记:

        ```xml
        <!--
            Copyright: Copyright 1998-2001 W3C (MIT, INRIA, Keio), All Rights
        Reserved.
        See http://www.w3.org/Consortium/Legal/.
        Author: Aaron Cohen (Intel)
            Version: February 7, 2001
            Module: Animation Module
            Feature: animation
            File Name: animation-add-BE-05.smil
            Media Components: none
        Expected Behavior: Nine red rectangles numbered 1 to 9 shrink to squares
            over 2s as follows:
            at 2s #1 shrinks.
            at 5s #2 shrinks, 1s after #1 completes
            at 8s #3 shrinks.
            #4 shrinks when it is clicked on.
            #5 shrinks 1s after it is clicked on.
            #6 shrinks 2s after it is clicked on.
            #7 shrinks when the accesskey '1' is pressed.
            #8 should be shrunk from 0s since it's wallclock time is in
        the past.
            #9 will not shrink unless a DOM call causes it to begin.
        -->
        <smil xmlns="http://www.w3.org/2001/SMIL20/Language">
            <head>
                <layout>
                    <root-layout width="640" height="480" backgroundColor="white" />
                    <region id="whole" width="640" height="480" z-index="0" />
                    <region id="rect1" top="50px" left="90px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect2" top="50px" left="234px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect4" top="160px" left="90px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect5" top="160px" left="234px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect6" top="160px" left="380px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect7" top="270px" left="90px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect8" top="270px" left="234px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect9" top="270px" left="380px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                </layout>
            </head>
            <!-- Copyright 1998-2001 W3C (MIT, INRIA, Keio), All Rights Reserved.
        See http://www.w3.org/Consortium/Legal/. -->
            <body>
                <par dur="indefinite">
                    <img src="../images/animation-timing-BE-05.jpg" region="whole" />
                    <animate id="anim1" targetElement="rect1" attributeName="height" from="50" to="25" begin="2s" dur="2s" fill="freeze" />
                    <animate id="anim2" targetElement="rect2" attributeName="height" from="50" to="25" begin="anim1.end+1s" dur="2s" fill="freeze" />
                    <brush id="brush4" color="red" region="rect4" height="50px" width="30px" />
                    <animate id="anim4" targetElement="brush4" attributeName="height" from="50" to="25" begin="brush4.activateEvent" dur="2s" fill="freeze" />
                    <brush id="brush5" color="red" region="rect5" height="50px" width="30px" />
                    <animate id="anim5" targetElement="brush5" attributeName="height" from="50" to="25" begin="brush5.activateEvent+1s" dur="2s" fill="freeze" />
                    <brush id="brush6" color="red" region="rect6" height="50px" width="30px" />
                    <animate id="anim6a" targetElement="brush6" attributeName="width" repeatCount="3" from="30" to="30" begin="brush6.activateEvent" dur="1s" fill="freeze" />
                    <animate id="anim6b" targetElement="brush6" attributeName="height" from="50" to="25" begin="anim6a.repeat(2)" dur="2s" fill="freeze" />
                    <animate id="anim7" targetElement="rect7" attributeName="height" from="50" to="25" begin="accesskey(1)" dur="2s" fill="freeze" />
                    <animate id="anim8" targetElement="rect8" attributeName="height" from="50" to="25" begin="wallclock(2000-01-01T00:00:00Z)" dur="2s" fill="freeze" />
                    <animate id="anim9" targetElement="rect9" attributeName="width" from="30" to="30" begin="indefinite" dur="1s" fill="freeze" />
                </par>
            </body>
        </smil>
        ```

        幻灯片部件将引用此内容，如下所示:

        ```xml
        <p:spTree>
            …
            <p:contentPart r:id="smil01"/>
            …
        </p:spTree>
        ```

        contentPart 元素指定ID 为 smil01 的关系所针对的内容是 PresentationML 文档的一部分。 检查相应关系部分项的内容，我们可以看到该关系的目标：

        ```xml
        <Relationships … >
            …
            <Relationship Id="smil01" TargetMode="Internal"
        Type="http://purl.oclc.org/ooxml/officeDocument/relationships/customXml"
        Target="smil1.xml" />
            …
        </Relationships>
        ```

        对应的关系部件项显示SMIL内容位于幻灯片旁边并且被命名为 smil1.xml。

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
                    id (与部件的关系)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定内容部件的关系 ID. </br></br>
                    [Example: 考虑一个具有以下 id 属性的 XML 元素:</br></br>
                    `<… r:id="rId1" />`
                    该标记指定关联关系 ID 为 rId1 的关联关系部分包含父 XML 元素的对应关系信息. end example]</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Rel) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **contentPart (Content Part)**

    This element specifies a reference to XML content in a format not defined by ECMA-376. 
    
    !!! info "Note"
        
        This part allows the native use of other commonly used interchange formats, such as: 

        - MathML (http://www.w3.org/TR/MathML2/)
        - SMIL (http://www.w3.org/TR/REC-smil/)
        - SVG (http://www.w3.org/TR/SVG11/)
    
    The relationship type of the explicit relationship specified by this element shall be http://purl.oclc.org/ooxml/officeDocument/relationships/customXml and have a TargetMode attribute value of Internal. If an application cannot process content of the content type specified by the targeted part, then it should continue to process the file. If possible, it should also provide some indication that unknown content was not imported.

    [Note: For better interoperability, only standard XML formats should be used. end note]
    
    !!! info "Example"
        
        Consider a PresentationML document which includes the following SMIL markup in a part named smil1.xml:

        ```xml
        <!--
            Copyright: Copyright 1998-2001 W3C (MIT, INRIA, Keio), All Rights
        Reserved.
        See http://www.w3.org/Consortium/Legal/.
        Author: Aaron Cohen (Intel)
            Version: February 7, 2001
            Module: Animation Module
            Feature: animation
            File Name: animation-add-BE-05.smil
            Media Components: none
        Expected Behavior: Nine red rectangles numbered 1 to 9 shrink to squares
            over 2s as follows:
            at 2s #1 shrinks.
            at 5s #2 shrinks, 1s after #1 completes
            at 8s #3 shrinks.
            #4 shrinks when it is clicked on.
            #5 shrinks 1s after it is clicked on.
            #6 shrinks 2s after it is clicked on.
            #7 shrinks when the accesskey '1' is pressed.
            #8 should be shrunk from 0s since it's wallclock time is in
        the past.
            #9 will not shrink unless a DOM call causes it to begin.
        -->
        <smil xmlns="http://www.w3.org/2001/SMIL20/Language">
            <head>
                <layout>
                    <root-layout width="640" height="480" backgroundColor="white" />
                    <region id="whole" width="640" height="480" z-index="0" />
                    <region id="rect1" top="50px" left="90px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect2" top="50px" left="234px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect4" top="160px" left="90px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect5" top="160px" left="234px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect6" top="160px" left="380px" height="50px" width="30px" backgroundColor="transparent" z-index="1" />
                    <region id="rect7" top="270px" left="90px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect8" top="270px" left="234px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                    <region id="rect9" top="270px" left="380px" height="50px" width="30px" backgroundColor="red" z-index="1" />
                </layout>
            </head>
            <!-- Copyright 1998-2001 W3C (MIT, INRIA, Keio), All Rights Reserved.
        See http://www.w3.org/Consortium/Legal/. -->
            <body>
                <par dur="indefinite">
                    <img src="../images/animation-timing-BE-05.jpg" region="whole" />
                    <animate id="anim1" targetElement="rect1" attributeName="height" from="50" to="25" begin="2s" dur="2s" fill="freeze" />
                    <animate id="anim2" targetElement="rect2" attributeName="height" from="50" to="25" begin="anim1.end+1s" dur="2s" fill="freeze" />
                    <brush id="brush4" color="red" region="rect4" height="50px" width="30px" />
                    <animate id="anim4" targetElement="brush4" attributeName="height" from="50" to="25" begin="brush4.activateEvent" dur="2s" fill="freeze" />
                    <brush id="brush5" color="red" region="rect5" height="50px" width="30px" />
                    <animate id="anim5" targetElement="brush5" attributeName="height" from="50" to="25" begin="brush5.activateEvent+1s" dur="2s" fill="freeze" />
                    <brush id="brush6" color="red" region="rect6" height="50px" width="30px" />
                    <animate id="anim6a" targetElement="brush6" attributeName="width" repeatCount="3" from="30" to="30" begin="brush6.activateEvent" dur="1s" fill="freeze" />
                    <animate id="anim6b" targetElement="brush6" attributeName="height" from="50" to="25" begin="anim6a.repeat(2)" dur="2s" fill="freeze" />
                    <animate id="anim7" targetElement="rect7" attributeName="height" from="50" to="25" begin="accesskey(1)" dur="2s" fill="freeze" />
                    <animate id="anim8" targetElement="rect8" attributeName="height" from="50" to="25" begin="wallclock(2000-01-01T00:00:00Z)" dur="2s" fill="freeze" />
                    <animate id="anim9" targetElement="rect9" attributeName="width" from="30" to="30" begin="indefinite" dur="1s" fill="freeze" />
                </par>
            </body>
        </smil>
        ```

        A Slide Part would reference this content as follows:

        ```xml
        <p:spTree>
            …
            <p:contentPart r:id="smil01"/>
            …
        </p:spTree>
        ```

        The contentPart element specifies that the content targeted by the relationship with an ID of smil01 is part of the PresentationML document. Examining the contents of the corresponding relationship part item, we can see the targets for that relationship:

        ```xml
        <Relationships … >
            …
            <Relationship Id="smil01" TargetMode="Internal"
        Type="http://purl.oclc.org/ooxml/officeDocument/relationships/customXml"
        Target="smil1.xml" />
            …
        </Relationships>
        ```

        The corresponding relationship part item shows that the SMIL content is located next to the slide and is named smil1.xml.

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
                    id (Relationship to Part)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the relationship ID to a content part. </br></br>
                    [Example: Consider an XML element which has the following id attribute:</br></br>
                    `<… r:id="rId1" />`
                    The markup specifies the associated relationship part with relationship ID rId1 contains the corresponding relationship information for the parent XML element. end example]</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Rel) is located in §A.3. end note]

### 19.3.1.15 controls (控件列表)

=== "中文"

    该元素指定相应幻灯片的嵌入控件列表。 自定义嵌入控件可以嵌入到幻灯片上。
    
    [Note: 该元素内容模型 (CT_ControlList) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **controls (List of controls)**

    This element specifies a list of embedded controls for the corresponding slide. Custom embedded controls can be embedded on slides.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_ControlList) is located in §A.3. end note]

### 19.3.1.16 cSld (通用幻灯片数据)

=== "中文"

    此元素指定与所有幻灯片类型相关的幻灯片信息的容器。 所有幻灯片共享一组独立于幻灯片类型的通用属性； 任何特定幻灯片的这些属性的描述都存储在幻灯片的 cSld 容器中。 特定于父元素指示的幻灯片类型的幻灯片数据存储在其他地方。

    [Note: cSld 中的实际数据仅描述特定的父幻灯片； 它只是所有幻灯片中通用的存储信息类型。 end note]

    !!! info "Example"

        考虑下面的PresentationML幻灯片

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                …
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

        如上面的示例所示，幻灯片的形状树 (spTree) 是 cSld 的子元素，因为所有幻灯片类型都可以包含形状树。 特定于幻灯片类型的其他幻灯片属性（例如 sld 幻灯片的过渡）在其他地方指定。 

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
                    name (名称)
                </td>
                <td>
                    指定幻灯片名称属性，该属性用于进一步标识公共幻灯片数据的这种唯一配置。 这可能用于帮助区分不同的幻灯片布局或各种其他幻灯片类型. </br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.</br></br>
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_CommonSlideData) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **cSld (Common Slide Data)**

    This element specifies a container for slide information that is relevant to all of the slide types. All slides share a common set of properties that is independent of the slide type; the description of these properties for any particular slide is stored within the slide's cSld container. Slide data specific to the slide type indicated by the parent element is stored elsewhere.

    [Note: The actual data in cSld describe only the particular parent slide; it is only the kind of information stored that is common across all slides. end note]

    !!! info "Example"

        Consider the following PresentationML slide

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                …
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

        As the above example shows, the shape tree of a slide (spTree) is a child element of cSld because all slide types can contain a shape tree. Other slide properties specific to the slide type (such as transitions for sld slides) are specified elsewhere. 

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
                    Specifies the slide name property that is used to further identify this unique configuration of common slide data. This might be used to aid in distinguishing different slide layouts or various other slide types. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_CommonSlideData) is located in §A.3. end note]

### 19.3.1.17 custData (客户数据)

=== "中文"

    该元素指定客户数据，允许在演示文稿中指定和保留客户特定数据.

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
                    id (关系ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    该属性指定用于引用当前PresentationML文件范围之外的其他资源的关系ID.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型 (第 22.8.2.1 节) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_CustomerData) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **custData (Customer Data)**

    This element specifies customer data which allows for the specifying and persistence of customer specific data within the presentation.

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
                    id (Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    This attribute specifies the relationship id for referencing other resources outside the scope of the current PresentationML file.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomerData) is located in §A.3. end note]

### 19.3.1.18 custDataLst (客户资料清单)

=== "中文"

    该元素允许在PresentationML 框架内指定客户定义的数据。 可以在此列表中定义对自定义数据或标签的引用。
    
    [Note: 该元素内容模型 (CT_CustomerDataList) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **custDataLst (Customer Data List)**

    This element allows for the specifying of customer defined data within the PresentationML framework. References to custom data or tags can be defined within this list.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_CustomerDataList) is located in §A.3. end note]

### 19.3.1.19 cxnSp (连接形状)

=== "中文"

    该元素指定用于连接两个 sp 元素的连接形状。 使用 cxnSp 指定连接后，生成应用程序将确定连接器采用的确切路径。 也就是说，连接器路由算法由生成的应用程序决定，因为所需的路径可能会根据应用程序的特定需求而有所不同。

    ![11](./imgs/19pml-5.png)

    !!! info "Example"

        考虑以下连接两个常规形状的连接器形状。

        ```xml
        <p:spTree>
            …
            <p:sp>
                <p:nvSpPr>
                    <p:cNvPr id="1" name="Rectangle 1"/>
                    <p:cNvSpPr/>
                    <p:nvPr/>
                </p:nvSpPr>
                …
            </p:sp>
            <p:sp>
                <p:nvSpPr>
                    <p:cNvPr id="2" name="Rectangle 2"/>
                    <p:cNvSpPr/>
                    <p:nvPr/>
                </p:nvSpPr>
                …
            </p:sp>
            <p:cxnSp>
                <p:nvCxnSpPr>
                    <p:cNvPr id="3" name="Elbow Connector 3"/>
                    <p:cNvCxnSpPr>
                        <a:stCxn id="1" idx="3"/>
                        <a:endCxn id="2" idx="1"/>
                    </p:cNvCxnSpPr>
                    <p:nvPr/>
                </p:nvCxnSpPr>
                …
            </p:cxnSp>
        </p:spTree>
        ```

    [Note: 该元素内容模型 (CT_Connector) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **cxnSp (Connection Shape)**

    This element specifies a connection shape that is used to connect two sp elements. Once a connection is specified using a cxnSp, it is left to the generating application to determine the exact path the connector takes. That is the connector routing algorithm is left up to the generating application as the desired path might be different depending on the specific needs of the application.

    ![11](./imgs/19pml-5.png)

    !!! info "Example"

        Consider the following connector shape that connects two regular shapes.

        ```xml
        <p:spTree>
            …
            <p:sp>
                <p:nvSpPr>
                    <p:cNvPr id="1" name="Rectangle 1"/>
                    <p:cNvSpPr/>
                    <p:nvPr/>
                </p:nvSpPr>
                …
            </p:sp>
            <p:sp>
                <p:nvSpPr>
                    <p:cNvPr id="2" name="Rectangle 2"/>
                    <p:cNvSpPr/>
                    <p:nvPr/>
                </p:nvSpPr>
                …
            </p:sp>
            <p:cxnSp>
                <p:nvCxnSpPr>
                    <p:cNvPr id="3" name="Elbow Connector 3"/>
                    <p:cNvCxnSpPr>
                        <a:stCxn id="1" idx="3"/>
                        <a:endCxn id="2" idx="1"/>
                    </p:cNvCxnSpPr>
                    <p:nvPr/>
                </p:nvCxnSpPr>
                …
            </p:cxnSp>
        </p:spTree>
        ```

    [Note: The W3C XML Schema definition of this element’s content model (CT_Connector) is located in §A.3. end note]

### 19.3.1.20 extLst (带有修改标志的扩展列表)

=== "中文"

    该元素指定具有修改能力的扩展列表，其中定义了元素类型 ext 的所有未来扩展。 扩展列表以及相应的未来扩展用于扩展PresentationML框架的存储功能。 这允许各种新类型的数据本地存储在框架内。

    [Note: 使用此 extLst 元素允许生成应用程序存储此扩展属性是否已被修改. end note]

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
                    mod (修改/Modify)
                </td>
                <td>
                    此属性指定此元素中包含的数据是否已被修改，因此应由生成应用程序再次处理.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ExtensionListModify) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **extLst (Extension List with Modification Flag)**

    This element specifies the extension list with modification ability within which all future extensions of element type ext are defined. The extension list along with corresponding future extensions is used to extend the storage capabilities of the PresentationML framework. This allows for various new kinds of data to be stored natively within the framework.

    [Note: Using this extLst element allows the generating application to store whether this extension property has been modified. end note]

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
                    mod (Modify)
                </td>
                <td>
                    This attribute specifies whether the data contained within this element has been modified and should thus be processed again by the generating application.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ExtensionListModify) is located in §A.3. end note]

### 19.3.1.21 graphicFrame (图框)

=== "中文"

    该元素指定图形框架的存在。 该框架包含由外部源生成的图形，并且需要一个容器来在幻灯片表面上显示。

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
                    bwMode (黑白模式)</br></br>
                    Namespace: .../drawingml/2006/main
                </td>
                <td>
                    指定如何使用颜色、黑色或白色或灰度来渲染图形对象. </br></br>
                    [Note: 这并不意味着图形对象本身仅存储黑白或灰度信息。 该属性设置图形对象使用的渲染模式. end note] </br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型定义 (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GraphicalObjectFrame) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **graphicFrame (Graphic Frame)**

    This element specifies the existence of a graphics frame. This frame contains a graphic that was generated by an external source and needs a container in which to be displayed on the slide surface.

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
                    bwMode (Black and White Mode)</br></br>
                    Namespace: .../drawingml/2006/main
                </td>
                <td>
                    Specifies how the graphical object should be rendered, using color, black or white, or grayscale. </br></br>
                    [Note: This does not mean that the graphical object itself is stored with only black and white or grayscale information. This attribute instead sets the rendering mode that the graphical object uses. end note] </br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GraphicalObjectFrame) is located in §A.3. end note]

### 19.3.1.22 grpSp (组合图形)

=== "中文"

    该元素指定一个组形状，表示组合在一起的许多形状。 该形状应被视为规则形状，但不是由单个几何形状来描述，而是由其中包含的所有形状几何形状组成。 在组形状中，组成该组的每个形状都按照通常的方式指定。 然而，对元素进行分组的想法是，单个变换可以同时应用于多个形状。

    !!! info "Example"

        考虑以下组形状。

        ```xml
        <p:grpSp>
            <p:nvGrpSpPr>
                <p:cNvPr id="10" name="Group 9"/>
                <p:cNvGrpSpPr/>
                <p:nvPr/>
            </p:nvGrpSpPr>
            <p:grpSpPr>
                <a:xfrm>
                    <a:off x="838200" y="990600"/>
                    <a:ext cx="2426208" cy="978408"/>
                    <a:chOff x="838200" y="990600"/>
                    <a:chExt cx="2426208" cy="978408"/>
                </a:xfrm>
            </p:grpSpPr>
            <p:sp>
                …
            </p:sp>
            <p:sp>
                …
            </p:sp>
            <p:sp>
                …
            </p:sp>
        </p:grpSp>
        ```

    在上面的示例中，我们看到在单个组中指定了三个形状。 这三个形状的位置和大小都被指定，就像它们通常在形状树中一样。 生成应用程序应在计算出组形状的边界框后应用转换。

    [Note: 该元素内容模型 (CT_GroupShape) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **grpSp (Group Shape)**

    This element specifies a group shape that represents many shapes grouped together. This shape is to be treated just as if it were a regular shape but instead of being described by a single geometry it is made up of all the shape geometries encompassed within it. Within a group shape each of the shapes that make up the group are specified just as they normally would. The idea behind grouping elements however is that a single transform can apply to many shapes at the same time.

    !!! info "Example"

        Consider the following group shape.

        ```xml
        <p:grpSp>
            <p:nvGrpSpPr>
                <p:cNvPr id="10" name="Group 9"/>
                <p:cNvGrpSpPr/>
                <p:nvPr/>
            </p:nvGrpSpPr>
            <p:grpSpPr>
                <a:xfrm>
                    <a:off x="838200" y="990600"/>
                    <a:ext cx="2426208" cy="978408"/>
                    <a:chOff x="838200" y="990600"/>
                    <a:chExt cx="2426208" cy="978408"/>
                </a:xfrm>
            </p:grpSpPr>
            <p:sp>
                …
            </p:sp>
            <p:sp>
                …
            </p:sp>
            <p:sp>
                …
            </p:sp>
        </p:grpSp>
        ```

    In the above example we see three shapes specified within a single group. These three shapes have their position and sizes specified just as they normally would within the shape tree. The generating application should apply the transformation after the bounding box for the group shape has been calculated. 

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupShape) is located in §A.3. end note]

### 19.3.1.23 grpSpPr (组合图形属性)

=== "中文"

    该元素指定相应组内所有形状所共有的属性。 如果组形状属性和单个形状属性之间存在任何冲突属性，则应优先考虑单个形状属性。

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
                    bwMode (黑白模式)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定应仅使用黑色和白色来渲染组形状。 也就是说，在渲染相应形状时，组形状的颜色信息应转换为黑色或白色. </br></br>
                    [Note: 这并不意味着组形状本身仅存储有黑白颜色信息。 该属性设置形状在渲染时使用的渲染模式。 end note]</br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型定义 (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GroupShapeProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **grpSpPr (Group Shape Properties)**

    This element specifies the properties that are to be common across all of the shapes within the corresponding group. If there are any conflicting properties within the group shape properties and the individual shape properties then the individual shape properties should take precedence.

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
                    bwMode (Black and White Mode)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies that the group shape should be rendered using only black and white coloring. That is the coloring information for the group shape should be converted to either black or white when rendering the corresponding shapes. </br></br>
                    [Note: This does not mean that the group shapes themselves are stored with only black and white color information. This attribute instead sets the rendering mode that the shapes use when rendering. end note]</br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupShapeProperties) is located in §A.4.1. end note]

### 19.3.1.24 handoutMaster (讲义母板)

=== "中文"

    此元素指定讲义母版幻灯片的实例。 讲义母版幻灯片中包含描述讲义幻灯片中的对象及其相应格式的所有元素。 在讲义母版幻灯片中，cSld 元素指定常见的幻灯片元素，例如形状及其附加的文本正文。 讲义母版幻灯片中还有其他属性，但 cSld 涵盖了讲义母版幻灯片的大部分预期用途。

    [Note: 该元素内容模型 (CT_HandoutMaster) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **handoutMaster (Handout Master)**

    This element specifies an instance of a handout master slide. Within a handout master slide are contained all elements that describe the objects and their corresponding formatting for within a handout slide. Within a handout master slide the cSld element specifies the common slide elements such as shapes and their attached text bodies. There are other properties within a handout master slide but cSld encompasses the majority of the intended purpose for a handoutMaster slide.

    [Note: The W3C XML Schema definition of this element’s content model (CT_HandoutMaster) is located in §A.3. end note]

### 19.3.1.25 hf (幻灯片母版的页眉/页脚信息)

=== "中文"

    此元素指定幻灯片的页眉和页脚信息。 页眉和页脚由文本占位符组成，这些文本应在所有幻灯片和幻灯片类型中保持一致，例如日期和时间、幻灯片编号以及自定义页眉和页脚文本。 

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
                    dt (日期/时间占位符)
                </td>
                <td>
                    指定是否为此母版启用日期/时间占位符。 如果未指定此属性，则生成应用程序应假定值为 true. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    ftr (页脚占位符)
                </td>
                <td>
                    指定是否为此母版启用页脚占位符。 如果未指定此属性，则生成应用程序应假定值为 true. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    hdr (标题占位符)
                </td>
                <td>
                    指定是否为此母版启用标头占位符。 如果未指定此属性，则生成应用程序应假定值为 true. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    sldNum (幻灯片编号占位符)
                </td>
                <td>
                    指定是否启用幻灯片编号占位符。 如果未指定此属性，则生成应用程序应假定值为 true. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_HeaderFooter) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **hf (Header/Footer information for a slide master)**

    This element specifies the header and footer information for a slide. Headers and footers consist of placeholders for text that should be consistent across all slides and slide types, such as a date and time, slide numbering, and custom header and footer text. 

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
                    dt (Date/Time Placeholder)
                </td>
                <td>
                    Specifies whether the Date/Time placeholder is enabled for this master. If this attribute is not specified, a value of true should be assumed by the generating application. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    ftr (Footer Placeholder)
                </td>
                <td>
                    Specifies whether the Footer placeholder is enabled for this master. If this attribute is not specified, a value of true should be assumed by the generating application. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    hdr (Header Placeholder)
                </td>
                <td>
                    Specifies whether the Header placeholder is enabled for this master. If this attribute is not specified, a value of true should be assumed by the generating application. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    sldNum (Slide Number Placeholder)
                </td>
                <td>
                    Specifies whether the slide number placeholder is enabled. If this attribute is not specified, a value of true should be assumed by the generating application. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_HeaderFooter) is located in §A.3. end note]

### 19.3.1.26 notes (笔记幻灯片)

=== "中文"

    该元素指定注释幻灯片及其相应数据的存在。 注释幻灯片中包含所有常见的幻灯片元素以及特定于注释元素的附加属性。

    !!! info "Example"

        考虑下面的PresentationML笔记幻灯片

        ```xml
        <p:notes>
            <p:cSld>
                …
            </p:cSld>
            …
        </p:notes>
        ```

        在上面的示例中，注释元素指定了笔记幻灯片及其所有部件的存在。 请注意 cSld 元素，它指定可以出现在任何幻灯片类型上的通用元素，然后任何元素指定此注释幻灯片的其他非通用属性。

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
                    showMasterPhAnim (显示母板占位符动画)
                </td>
                <td>
                    指定是否在母版幻灯片的占位符上显示动画. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterSp(显示母板形状)
                </td>
                <td>
                    指定主幻灯片上的形状是否应显示在幻灯片上. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_NotesSlide) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **notes (Notes Slide)**

    This element specifies the existence of a notes slide along with its corresponding data. Contained within a notes slide are all the common slide elements along with addition properties that are specific to the notes element.

    !!! info "Example"

        Consider the following PresentationML notes slide

        ```xml
        <p:notes>
            <p:cSld>
                …
            </p:cSld>
            …
        </p:notes>
        ```

        In the above example a notes element specifies the existence of a notes slide with all of its parts. Notice the cSld element, that specifies the common elements that can appear on any slide type and then any elements specify additional non-common properties for this notes slide.

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
                    showMasterPhAnim (Show Master Placeholder Animations)
                </td>
                <td>
                    Specifies whether or not to display animations on placeholders from the master slide. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterSp(Show Master Shapes)
                </td>
                <td>
                    Specifies if shapes on the master slide should be shown on slides or not. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NotesSlide) is located in §A.3. end note]

### 19.3.1.27 notesMaster (笔记母板)

=== "中文"

    此元素指定注释母版幻灯片的实例。 注释主幻灯片中包含描述注释幻灯片中的对象及其相应格式的所有元素。 在注释母版幻灯片中，cSld 元素指定常见的幻灯片元素，例如形状及其附加的文本正文。 笔记母版幻灯片中还有其他属性，但 cSld 涵盖了笔记母版幻灯片的大部分预期用途。
    
    [Note: 该元素内容模型 (CT_NotesMaster) 的 W3C XML 模式定义位于 §A.3 中。 end note]

=== "英文"

    **notesMaster (Notes Master)**

    This element specifies an instance of a notes master slide. Within a notes master slide are contained all elements that describe the objects and their corresponding formatting for within a notes slide. Within a notes master slide the cSld element specifies the common slide elements such as shapes and their attached text bodies. There are other properties within a notes master slide but cSld encompasses the majority of the intended purpose for a notesMaster slide.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NotesMaster) is located in §A.3. end note]

### 19.3.1.28 notesStyle (笔记文本样式)

=== "中文"

    此元素指定注释幻灯片中所有其他文本的文本格式样式。 此格式适用于相应注释幻灯片中的所有文本。 文本格式是通过利用 DrawingML 框架来指定的，就像在常规演示幻灯片中一样。 在notesStyle元素中可以定义许多不同的样式类型，因为注释幻灯片中存储了不同类型的文本。
    
    [Note: 该元素内容模型 (CT_TextListStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **notesStyle (Notes Text Style)**

    This element specifies the text formatting style for the all other text within a notes slide. This formatting is used on all text within the corresponding notes slides. The text formatting is specified by utilizing the DrawingML framework just as within a regular presentation slide. Within the notesStyle element there can be many different style types defined as there are different kinds of text stored within a notes slide.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_TextListStyle) is located in §A.4.1. end note]

### 19.3.1.29 nvCxnSpPr (连接形状的非视觉属性)

=== "中文"

    该元素指定连接形状的所有非视觉属性。 该元素是与连接形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响连接形状外观的附加信息。

    [Note: 该元素内容模型 (CT_ConnectorNonVisual) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **nvCxnSpPr (Non-Visual Properties for a Connection Shape)**

    This element specifies all non-visual properties for a connection shape. This element is a container for the nonvisual identification properties, shape properties and application properties that are to be associated with a connection shape. This allows for additional information that does not affect the appearance of the connection shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ConnectorNonVisual) is located in §A.3. end note]

### 19.3.1.30 nvGraphicFramePr (图形框架的非视觉属性)

=== "中文"

    该元素指定图形框架的所有非视觉属性。 该元素是与图形框架关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响图形框架的外观的附加信息。

    [Note: 该元素内容模型 (CT_GraphicalObjectFrameNonVisual) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **nvGraphicFramePr (Non-Visual Properties for a Graphic Frame)**

    This element specifies all non-visual properties for a graphic frame. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a graphic frame. This allows for additional information that does not affect the appearance of the graphic frame to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GraphicalObjectFrameNonVisual) is located in §A.3. end note]

### 19.3.1.31 nvGrpSpPr (组合形状的非视觉属性)

=== "中文"

    该元素指定组形状的所有非视觉属性。 该元素是与组形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响组形状外观的附加信息。

    [Note: 该元素内容模型 (CT_GroupShapeNonVisual) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **nvGrpSpPr (Non-Visual Properties for a Group Shape)**

    This element specifies all non-visual properties for a group shape. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a group shape. This allows for additional information that does not affect the appearance of the group shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupShapeNonVisual) is located in §A.3. end note]

### 19.3.1.32 nvPicPr (图片的非视觉属性)

=== "中文"

    该元素指定图片的所有非视觉属性。 该元素是与图片关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响图片外观的附加信息。

    !!! inf "Example"
    
        考虑以下 PresentationML。

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                …
            </p:nvPicPr>
            …
        </p:pic>
        ```

    [Note: 该元素内容模型 (CT_PictureNonVisual) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **nvPicPr (Non-Visual Properties for a Picture)**

    This element specifies all non-visual properties for a picture. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a picture. This allows for additional information that does not affect the appearance of the picture to be stored.

    !!! inf "Example"
    
        Consider the following PresentationML.

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                …
            </p:nvPicPr>
            …
        </p:pic>
        ```

    [Note: The W3C XML Schema definition of this element’s content model (CT_PictureNonVisual) is located in §A.3. end note]

### 19.3.1.33 nvPr (非视觉属性)

=== "中文"

    该元素指定对象的非视觉属性。 这些属性包括与对象相关联的多媒体内容以及指示如何在不同上下文中使用或显示该对象的属性。

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
                    isPhoto (是否为相册)
                </td>
                <td>
                    指定图片是否属于相册，因此在生成应用程序中编辑相册时应将其包含在内. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    userDrawn (是否为用户绘制的)
                </td>
                <td>
                    指定相应的对象是否已由用户绘制，因此不应被删除。 这允许标记包含用户绘制数据的幻灯片. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此元素内容模型 (CT_ApplicationNonVisualDrawingProps) 的 W3C XML 架构定义位于 §A.3. end note]

=== "英文"

    **nvPr (Non-Visual Properties)**

    This element specifies non-visual properties for objects. These properties include multimedia content associated with an object and properties indicating how the object is to be used or displayed in different contexts.

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
                    isPhoto (Is a Photo Album)
                </td>
                <td>
                    Specifies whether the picture belongs to a photo album and should thus be included when editing a photo album within the generating application. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    userDrawn (Is User Drawn)
                </td>
                <td>
                    Specifies if the corresponding object has been drawn by the user and should thus not be deleted. This allows for the flagging of slides that contain user drawn data. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ApplicationNonVisualDrawingProps) is located in §A.3. end note]

### 19.3.1.34 nvSpPr (形状的非视觉属性)

=== "中文"

    该元素指定形状的所有非视觉属性。 该元素是与形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响形状外观的附加信息。

    [Note: 该元素内容模型 (CT_ShapeNonVisual) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **nvSpPr (Non-Visual Properties for a Shape)**

    This element specifies all non-visual properties for a shape. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a shape. This allows for additional information that does not affect the appearance of the shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeNonVisual) is located in §A.3. end note]

### 19.3.1.35 otherStyle (幻灯片母版其他文本样式)

=== "中文"

    此元素指定母版幻灯片中所有其他文本的文本格式样式。 此格式适用于相关演示文稿幻灯片中 titleStyle 或 bodyStyle 元素未涵盖的所有文本。 文本格式是通过利用 DrawingML 框架来指定的，就像在常规演示幻灯片中一样。 在 otherStyle 元素中，可以定义许多不同的样式类型，因为幻灯片中存储了不同类型的文本。
    
    [Note: otherStyle 元素用于指定幻灯片形状内而非文本框中文本的文本格式。 文本框样式是在 bodyStyle 元素内处理的. end note]
    
    [Note: 该元素内容模型 (CT_TextListStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **otherStyle (Slide Master Other Text Style)**

    This element specifies the text formatting style for the all other text within a master slide. This formatting is used on all text not covered by the titleStyle or bodyStyle elements within related presentation slides. The text formatting is specified by utilizing the DrawingML framework just as within a regular presentation slide. Within the otherStyle element there can be many different style types defined as there are different kinds of text stored within a slide.
    
    [Note: The otherStyle element is to be used for specifying the text formatting of text within a slide shape but not within a text box. Text box styling is handled from within the bodyStyle element. end note]
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_TextListStyle) is located in §A.4.1. end note]

### 19.3.1.36 ph (占位符形状)

=== "中文"

    该元素指定相应的形状应由生成应用程序表示为占位符。 当生成应用程序将形状视为占位符时，它可以具有特殊属性来提醒用户可以将内容输入到形状中。 允许使用不同的占位符类型，并且可以使用此元素的占位符类型属性来指定不同的占位符类型。

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
                    hasCustomPrompt (占位符有自定义提示)
                </td>
                <td>
                    指定相应的占位符是否应该有自定义提示. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    idx (占位符索引)
                </td>
                <td>
                    指定占位符索引。 在应用模板或更改布局以将一个模板/母版上的占位符与另一个模板/母版上的占位符匹配时使用此选项. </br></br>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    orient (占位符方向)
                </td>
                <td>
                    指定占位符的方向.</br></br>
                    该属性的可能值由 ST_Direction 简单类型定义 (§19.7.2).
                </td>
            </tr>
            <tr>
                <td>
                    sz (占位符大小)
                </td>
                <td>
                    指定占位符的大小.</br></br>
                    该属性的可能值由 ST_PlaceholderSize 简单类型定义 (§19.7.9).
                </td>
            </tr>
            <tr>
                <td>
                    type (占位符类型)
                </td>
                <td>
                    指定占位符要包含的内容类型.</br></br>
                    该属性的可能值由 ST_PlaceholderType 简单类型定义 (§19.7.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Placeholder) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **ph (Placeholder Shape)**

    This element specifies that the corresponding shape should be represented by the generating application as a placeholder. When a shape is considered a placeholder by the generating application it can have special properties to alert the user that they can enter content into the shape. Different placeholder types are allowed and can be specified by using the placeholder type attribute for this element.

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
                    hasCustomPrompt (Placeholder has custom prompt)
                </td>
                <td>
                    Specifies whether the corresponding placeholder should have a custom prompt or not. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    idx (Placeholder Index)
                </td>
                <td>
                    Specifies the placeholder index. This is used when applying templates or changing layouts to match a placeholder on one template/master to another. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
            <tr>
                <td>
                    orient (Placeholder Orientation)
                </td>
                <td>
                    Specifies the orientation of a placeholder.</br></br>
                    The possible values for this attribute are defined by the ST_Direction simple type (§19.7.2).
                </td>
            </tr>
            <tr>
                <td>
                    sz (Placeholder Size)
                </td>
                <td>
                    Specifies the size of a placeholder.</br></br>
                    The possible values for this attribute are defined by the ST_PlaceholderSize simple type (§19.7.9).
                </td>
            </tr>
            <tr>
                <td>
                    type (Placeholder Type)
                </td>
                <td>
                    Specifies what content type a placeholder is intended to contain.</br></br>
                    The possible values for this attribute are defined by the ST_PlaceholderType simple type (§19.7.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Placeholder) is located in §A.3. end note]

### 19.3.1.37 pic (图片)

=== "中文"

    该元素指定文档中是否存在图片对象。

    !!! info "Example"

        考虑下面的PresentationML，它指定文档中是否存在图片。 该图片可以具有非视觉属性、图片填充以及附加的形状属性。

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="4" name="lake.JPG" descr="Picture of a Lake" />
                <p:cNvPicPr>
                    <a:picLocks noChangeAspect="1"/>
                </p:cNvPicPr>
                <p:nvPr/>
            </p:nvPicPr>
            <p:blipFill>
                …
            </p:blipFill>
            <p:spPr>
                …
            </p:spPr>
        </p:pic>
        ```

    [Note: 该元素内容模型 (CT_Picture) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **pic (Picture)**

    This element specifies the existence of a picture object within the document.

    !!! info "Example"

        Consider the following PresentationML that specifies the existence of a picture within a document. This picture can have non-visual properties, a picture fill as well as shape properties attached to it.

        ```xml
        <p:pic>
            <p:nvPicPr>
                <p:cNvPr id="4" name="lake.JPG" descr="Picture of a Lake" />
                <p:cNvPicPr>
                    <a:picLocks noChangeAspect="1"/>
                </p:cNvPicPr>
                <p:nvPr/>
            </p:nvPicPr>
            <p:blipFill>
                …
            </p:blipFill>
            <p:spPr>
                …
            </p:spPr>
        </p:pic>
        ```

    [Note: The W3C XML Schema definition of this element’s content model (CT_Picture) is located in §A.3. end note]

### 19.3.1.38 sld (演示幻灯片)

=== "中文"

    此元素是幻灯片部件 (§13.3.8) 的根元素，并指定幻灯片的实例。 幻灯片中包含描述演示文稿幻灯片中的对象及其相应格式的所有元素。 子元素描述常见的幻灯片元素，例如形状及其附加的文本主体、特定于该幻灯片的过渡和时间以及特定于该幻灯片的颜色信息。

    !!! info "Example"

        考虑下面的基本幻灯片。

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                …
                </p:spTree>
            </p:cSld>
            <p:clrMapOver>
                …
            </p:clrMapOver>
            <p:transition>
                …
            </p:transition>
            <p:timing>
                …
            </p:timing>
        </p:sld>
        ```

    此示例显示了一张幻灯片，其内容位于形状树中、本地颜色映射覆盖以及带有关联计时信息的幻灯片过渡。

=== "英文"

    **sld (Presentation Slide)**

    This element is the root element of a Slide part (§13.3.8) and specifies an instance of a slide. Within a slide are contained all elements that describe the objects and their corresponding formatting within a presentation slide. Child elements describe the common slide elements such as shapes and their attached text bodies, transition and timing specific to this slide and color information specific to this slide.

    !!! info "Example"

        Consider the following basic slide.

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                …
                </p:spTree>
            </p:cSld>
            <p:clrMapOver>
                …
            </p:clrMapOver>
            <p:transition>
                …
            </p:transition>
            <p:timing>
                …
            </p:timing>
        </p:sld>
        ```

    This example shows a slide with its content in the shape tree, a local color mapping override and a slide transition with associated timing information.

### 19.3.1.39 sldLayout (幻灯片布局/版式)

=== "中文"

    该元素指定幻灯片布局的实例。 幻灯片布局实质上包含可应用于任何现有幻灯片的模板幻灯片设计。 当应用于现有幻灯片时，所有相应的内容都应映射到新的幻灯片布局。

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
                    matchingName (匹配名称)
                </td>
                <td>
                    指定用于代替 cSld 元素中的 name 属性的名称。 这用于布局匹配以响应布局更改和模板应用. </br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    preserve (保留幻灯片布局)
                </td>
                <td>
                    指定当删除遵循该布局的所有幻灯片时是否删除相应的幻灯片布局。 如果未指定此属性，则生成应用程序应假定值为 false。 这意味着如果演示文稿中没有与该幻灯片相关的幻灯片，该幻灯片实际上会被删除。</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterPhAnim (显示母板占位符动画)
                </td>
                <td>
                    指定是否在母版幻灯片的占位符上显示动画.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterSp (显示主形状)
                </td>
                <td>
                    指定主幻灯片上的形状是否应显示在幻灯片上.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    type (幻灯片布局类型)
                </td>
                <td>
                    指定此幻灯片使用的幻灯片布局类型.</br></br>
                    该属性的可能值由 ST_SlideLayoutType 简单类型定义 (§19.7.15).
                </td>
            </tr>
            <tr>
                <td>
                    userDrawn (是否用户绘制的)
                </td>
                <td>
                    指定相应的对象是否已由用户绘制，因此不应被删除。 这允许标记包含用户绘制数据的幻灯片.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SlideLayout) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **sldLayout (Slide Layout)**

    This element specifies an instance of a slide layout. The slide layout contains in essence a template slide design that can be applied to any existing slide. When applied to an existing slide all corresponding content should be mapped to the new slide layout.

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
                    matchingName (Matching Name)
                </td>
                <td>
                    Specifies a name to be used in place of the name attribute within the cSld element. This is used for layout matching in response to layout changes and template applications. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    preserve (Preserve Slide Layout)
                </td>
                <td>
                    Specifies whether the corresponding slide layout is deleted when all the slides that follow that layout are deleted. If this attribute is not specified then a value of false should be assumed by the generating application. This would mean that the slide would in fact be deleted if no slides within the presentation were related to it. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterPhAnim (Show Master Placeholder Animations)
                </td>
                <td>
                    Specifies whether or not to display animations on placeholders from the master slide.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    showMasterSp (Show Master Shapes)
                </td>
                <td>
                    Specifies if shapes on the master slide should be shown on slides or not.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    type (Slide Layout Type)
                </td>
                <td>
                    Specifies the slide layout type that is used by this slide.</br></br>
                    The possible values for this attribute are defined by the ST_SlideLayoutType simple type (§19.7.15).
                </td>
            </tr>
            <tr>
                <td>
                    userDrawn (Is User Drawn)
                </td>
                <td>
                    Specifies if the corresponding object has been drawn by the user and should thus not be deleted. This allows for the flagging of slides that contain user drawn data.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideLayout) is located in §A.3. end note]

### 19.3.1.40 sldLayoutId (幻灯片布局 ID)

=== "中文"

    此元素指定幻灯片母版中使用的每个幻灯片布局的关系信息。 幻灯片母版具有内部使用的关系标识符来确定应使用的幻灯片布局。 然后，为了确定这些幻灯片布局应该是什么，请使用 sldLayoutIdLst 中的 sldLayoutId 元素。

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
                    id (ID Tag) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定生成应用程序可用于解析在创建幻灯片时使用哪种幻灯片布局的关系 ID 值。 此关系 ID 在主幻灯片的关系文件中使用，以公开演示文稿中相应布局文件的位置. </br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    id (ID Tag)
                </td>
                <td>
                    指定在演示文稿文件中唯一标识此幻灯片布局的标识号. </br></br>
                    该属性的可能值由 ST_SlideLayoutId 简单类型定义 (§19.7.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此元素的内容模型 (CT_SlideLayoutIdListEntry) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **sldLayoutId (Slide Layout Id)**

    This element specifies the relationship information for each slide layout that is used within the slide master. The slide master has relationship identifiers that it uses internally for determining the slide layouts that should be used. Then, to resolve what these slide layouts should be the sldLayoutId elements in the sldLayoutIdLst are utilized.

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
                    id (ID Tag) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the relationship id value that the generating application can use to resolve which slide layout is used in the creation of the slide. This relationship id is used within the relationship file for the master slide to expose the location of the corresponding layout file within the presentation. </br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    id (ID Tag)
                </td>
                <td>
                    Specifies the identification number that uniquely identifies this slide layout within the presentation file. </br></br>
                    The possible values for this attribute are defined by the ST_SlideLayoutId simple type (§19.7.14).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideLayoutIdListEntry) is located in §A.3. end note]

### 19.3.1.41 sldLayoutIdLst (幻灯片布局列表)

=== "中文"

    该元素指定幻灯片布局标识列表是否存在。 此列表包含在幻灯片母版中，用于确定幻灯片母版文件中正在使用哪些布局。 幻灯片布局列表中的每个布局都有其自己的标识号和关系标识符，它们在演示文稿文档和使用它的特定主幻灯片中唯一地标识它。

    [Note: 该元素内容模型 (CT_SlideLayoutIdList) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **sldLayoutIdLst (List of Slide Layouts)**

    This element specifies the existence of the slide layout identification list. This list is contained within the slide master and is used to determine which layouts are being used within the slide master file. Each layout within the list of slide layouts has its own identification number and relationship identifier that uniquely identifies it within both the presentation document and the particular master slide within which it is used.

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideLayoutIdList) is located in §A.3. end note]

### 19.3.1.42 sldMaster (幻灯片母版)

=== "中文"

    此元素指定幻灯片母版幻灯片的实例。 幻灯片母版幻灯片中包含描述演示文稿幻灯片中的对象及其相应格式的所有元素。 幻灯片母版幻灯片中有两个主要元素。 cSld 元素指定常见的幻灯片元素，例如形状及其附加的文本主体。 然后 txStyles 元素指定每个形状中文本的格式。 幻灯片母版幻灯片中的其他属性指定演示文稿幻灯片中的其他属性，例如颜色信息、页眉和页脚，以及所有相应演示文稿幻灯片的计时和过渡信息。

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
                    preserve (保留幻灯片母版)
                </td>
                <td>
                    指定当删除遵循该布局的所有幻灯片时是否删除相应的幻灯片布局。 如果未指定此属性，则生成应用程序应假定值为 false。 这意味着如果演示文稿中没有与该幻灯片相关的幻灯片，该幻灯片实际上会被删除。 </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SlideMaster) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **sldMaster (Slide Master)**

    This element specifies an instance of a slide master slide. Within a slide master slide are contained all elements that describe the objects and their corresponding formatting for within a presentation slide. Within a slide master slide are two main elements. The cSld element specifies the common slide elements such as shapes and their attached text bodies. Then the txStyles element specifies the formatting for the text within each of these shapes. The other properties within a slide master slide specify other properties for within a presentation slide such as color information, headers and footers, as well as timing and transition information for all corresponding presentation slides. 

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
                    preserve (Preserve Slide Master)
                </td>
                <td>
                    Specifies whether the corresponding slide layout is deleted when all the slides that follow that layout are deleted. If this attribute is not specified then a value of false should be assumed by the generating application. This would mean that the slide would in fact be deleted if no slides within the presentation were related to it. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideMaster) is located in §A.3. end note]

### 19.3.1.43 sp (图形)

=== "中文"

    该元素指定单个形状的存在。 形状可以是使用 DrawingML 框架定义的预设几何图形或自定义几何图形。 除了几何形状之外，每个形状还可以附加视觉和非视觉属性。 文本和相应的样式信息也可以附加到形状。 该形状与形状树或组形状元素中的所有其他形状一起指定。

    [Note: 形状是在幻灯片上指定文本的首选机制. end note]

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
                    useBgFill (使用背景填充)
                </td>
                <td>
                    指定形状填充应设置为幻灯片背景表面的形状填充. </br></br>
                    [Note: 此属性不会将形状的填充设置为透明，而是将其设置为用直接位于其后面的幻灯片背景部分进行填充. end note] </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Shape) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **sp (Shape)**

    This element specifies the existence of a single shape. A shape can either be a preset or a custom geometry, defined using the DrawingML framework. In addition to a geometry each shape can have both visual and nonvisual properties attached. Text and corresponding styling information can also be attached to a shape. This shape is specified along with all other shapes within either the shape tree or group shape elements.

    [Note: Shapes are the preferred mechanism for specifying text on a slide. end note]

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
                    useBgFill (Use Background Fill)
                </td>
                <td>
                    Specifies that the shape fill should be set to that of the slide background surface. </br></br>
                    [Note: This attribute does not set the fill of the shape to be transparent but instead sets it to be filled with the portion of the slide background that is directly behind it. end note] </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Shape) is located in §A.3. end note]

### 19.3.1.44 spPr (图形属性)

=== "中文"

    此元素指定可应用于形状的视觉形状属性。 这些属性包括形状填充、轮廓、几何形状、效果和 3D 方向。

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
                    bwMode (黑白模式) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定仅使用黑白颜色渲染图片。 即渲染图片时应将图片的颜色信息转换为黑色或白色. </br></br>
                    渲染该图像时不使用灰色，仅使用纯黑和纯白. </br></br>
                    [Note: 这并不意味着存储在文件中的图片本身一定是黑白图片。 该属性设置渲染时图片所应用的渲染模式. end note]</br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型 (§20.1.10.10) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ShapeProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **spPr (Shape Properties)**

    This element specifies the visual shape properties that can be applied to a shape. These properties include the shape fill, outline, geometry, effects, and 3D orientation.

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
                    bwMode (Black and White Mode) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies that the picture should be rendered using only black and white coloring. That is the coloring information for the picture should be converted to either black or white when rendering the picture. </br></br>
                    No gray is to be used in rendering this image, only stark black and stark white. </br></br>
                    [Note: This does not mean that the picture itself that is stored within the file is necessarily a black and white picture. This attribute instead sets the rendering mode that the picture has applied to when rendering. end note]</br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeProperties) is located in §A.4.1. end note]

### 19.3.1.45 spTree (图形树)

=== "中文"

    此元素指定可以在给定幻灯片上引用的所有基于形状的对象（无论是否分组）。 由于幻灯片中的大多数对象都是形状，因此这代表了幻灯片中的大部分内容。 文本和效果附加到 spTree 元素中包含的形状。

    !!! info "Example"

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                    <p:nvGrpSpPr>
                        …
                    </p:nvGrpSpPr>
                    <p:grpSpPr>
                        …
                    </p:grpSpPr>
                    <p:sp>
                        …
                    </p:sp>
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

        在上面的示例中，形状树指定了该幻灯片的所有形状属性。 

    形状树中的每个基于形状的对象，无论是否分组，都应代表幻灯片上唯一的 zordering 级别。 每个基于形状的对象的 z 顺序应由形状树中每个基于形状的对象的词汇顺序确定：第一个基于形状的对象应具有最低的 z 顺序，而最后一个基于形状的对象应具有最低的 z 顺序。 具有最高的 z 顺序。

    形状树中基于形状的对象的 z 顺序还应确定基于形状的对象的导航（选项卡）顺序：具有最低 z 顺序的基于形状的对象（词汇顺序中的第一个形状）应在导航顺序中位于第一个，对象按升序 z 顺序进行导航。

    !!! info "Example"

        考虑以下具有两种形状的PresentationML幻灯片

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                    …
                    <p:sp>
                        <p:nvSpPr>
                            <p:cNvPr id="5" name="Oval 4" />
                            …
                        </p:nvSpPr>
                        …
                    </p:sp>
                    <p:sp>
                        <p:nvSpPr>
                            <p:cNvPr id="4" name="Isosceles Triangle 3" />
                            …
                        </p:nvSpPr>
                        …
                    </p:sp>
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

    在上面的示例中，名称为 Oval 4 的形状具有最低的 z 顺序值，因为该形状是形状树中的第一个形状。 Oval 4 也是导航顺序中的第一个形状。 名为 Isosceles Triangle 3 的形状具有最高的 z 定位值，因为该形状是形状树中的最后一个形状。 Isosceles Triangle 3 也是导航顺序中的最后一个形状。

    [Note: 该元素内容模型 (CT_GroupShape) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **spTree (Shape Tree)**

    This element specifies all shape-based objects, either grouped or not, that can be referenced on a given slide. As most objects within a slide are shapes, this represents the majority of content within a slide. Text and effects are attached to shapes that are contained within the spTree element.

    !!! info "Example"

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                    <p:nvGrpSpPr>
                        …
                    </p:nvGrpSpPr>
                    <p:grpSpPr>
                        …
                    </p:grpSpPr>
                    <p:sp>
                        …
                    </p:sp>
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

        In the above example the shape tree specifies all the shape properties for this slide. 

    Each shape-based object within the shape tree, whether grouped or not, shall represent one unique level of zordering on the slide. The z-order for each shape-based object shall be determined by the lexical ordering of each shape-based object within the shape tree: the first shape-based object shall have the lowest z-order, while the last shape-based object shall have the highest z-order. 

    The z-ordering of shape-based objects within the shape tree shall also determine the navigation (tab) order of the shape-based objects: the shape-based object with the lowest z-order (the first shape in lexical order) shall be first in navigation order, with objects being navigated in ascending z-order. 

    !!! info "Example"

        Consider the following PresentationML slide with two shapes

        ```xml
        <p:sld>
            <p:cSld>
                <p:spTree>
                    …
                    <p:sp>
                        <p:nvSpPr>
                            <p:cNvPr id="5" name="Oval 4" />
                            …
                        </p:nvSpPr>
                        …
                    </p:sp>
                    <p:sp>
                        <p:nvSpPr>
                            <p:cNvPr id="4" name="Isosceles Triangle 3" />
                            …
                        </p:nvSpPr>
                        …
                    </p:sp>
                </p:spTree>
            </p:cSld>
            …
        </p:sld>
        ```

    In the above example the shape with name Oval 4 has the lowest z-order value since that shape is the first shape in the shape tree. Oval 4 is also the first shape in navigation order. The shape with name Isosceles Triangle 3 has the highest z positioning value since that shape is the last shape in the shape tree. Isosceles Triangle 3 is also the last shape in navigation order.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupShape) is located in §A.3. end note]

### 19.3.1.46 style (图形样式)

=== "中文"

    该元素指定形状的样式信息。 这用于根据主题的样式矩阵定义的预设样式来定义形状的外观。

    !!! info "Example"

        ```xml
        <p:style>
            <a:lnRef idx="3">
                <a:schemeClr val="lt1"/>
            </a:lnRef>
            <a:fillRef idx="1">
                <a:schemeClr val="accent3"/>
            </a:fillRef>
            <a:effectRef idx="1">
                <a:schemeClr val="accent3"/>
            </a:effectRef>
            <a:fontRef idx="minor">
                <a:schemeClr val="lt1"/>
            </a:fontRef>
        </p:style>
        ```

        上述代码的父形状是具有使用主题定义的第三种线条样式的轮廓，使用方案定义的第一种填充，并使用主题定义的第一种效果进行渲染。 形状内的文本将使用主题定义的小字体。

    [Note: 该元素内容模型 (CT_ShapeStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **style (Shape Style)**

    This element specifies the style information for a shape. This is used to define a shape's appearance in terms of the preset styles defined by the style matrix for the theme.

    !!! info "Example"

        ```xml
        <p:style>
            <a:lnRef idx="3">
                <a:schemeClr val="lt1"/>
            </a:lnRef>
            <a:fillRef idx="1">
                <a:schemeClr val="accent3"/>
            </a:fillRef>
            <a:effectRef idx="1">
                <a:schemeClr val="accent3"/>
            </a:effectRef>
            <a:fontRef idx="minor">
                <a:schemeClr val="lt1"/>
            </a:fontRef>
        </p:style>
        ```

        The parent shape of the above code is to have an outline that uses the third line style defined by the theme, use the first fill defined by the scheme, and be rendered with the first effect defined by the theme. Text inside the shape is to use the minor font defined by the theme.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeStyle) is located in §A.4.1. end note]

### 19.3.1.47 tags (客户数据标签)

=== "中文"

    该元素以标签的形式指定客户数据的存在。 这允许在PresentationML框架内存储客户数据。 虽然这与 ext 标签类似，可以用来存储信息，但该标签主要侧重于引用演示文稿文档的其他部件。 这是通过所有指定标签所需的关系标识属性来完成的。

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
                    id (关系ID/Relationship ID)
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    该属性指定客户数据标签的关系标识符。 这允许链接到当前 XML 文档外部但仍包含在演示文稿文档中的资源.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_TagsData) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **tags (Customer Data Tags)**

    This element specifies the existence of customer data in the form of tags. This allows for the storage of customer data within the PresentationML framework. While this is similar to the ext tag in that it can be used store information, this tag mainly focuses on referencing to other parts of the presentation document. This is accomplished via the relationship identification attribute that is required for all specified tags.

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
                    id (Relationship ID)
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    This attribute specifies the relationship identifier for the customer data tag. This allows for a link to a resource that is external from the current XML document but still contained within the presentation document.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_TagsData) is located in §A.3. end note]

### 19.3.1.48 timing (幻灯片布局的幻灯片计时信息)

=== "中文"

    此元素指定处理相应幻灯片中所有动画和定时事件的计时信息。 该信息通过计时元素内的时间节点进行跟踪。 有关这些时间节点的细节以及如何定义它们的更多信息可以在PresentationML框架的动画部分中找到。

    [Note: 该元素内容模型 (CT_SlideTiming) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **timing (Slide Timing Information for a Slide Layout)**

    This element specifies the timing information for handling all animations and timed events within the corresponding slide. This information is tracked via time nodes within the timing element. More information on the specifics of these time nodes and how they are to be defined can be found within the Animation section of the PresentationML framework.

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideTiming) is located in §A.3. end note]

### 19.3.1.49 titleStyle (幻灯片母版标题文本样式)

=== "中文"

    此元素指定母版幻灯片中标题文本的文本格式样式。 此格式适用于相关演示文稿幻灯片中的所有标题文本。 文本格式是通过利用 DrawingML 框架来指定的，就像在常规演示幻灯片中一样。 在标题样式中可以定义许多不同的样式类型，因为幻灯片标题中存储了不同类型的文本。
    
    [Note: 该元素内容模型 (CT_TextListStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **titleStyle (Slide Master Title Text Style)**

    This element specifies the text formatting style for the title text within a master slide. This formatting is used on all title text within related presentation slides. The text formatting is specified by utilizing the DrawingML framework just as within a regular presentation slide. Within a title style there can be many different style types defined as there are different kinds of text stored within a slide title.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_TextListStyle) is located in §A.4.1. end note]

### 19.3.1.50 transition (幻灯片布局的幻灯片过渡)

=== "中文"

    此元素指定用于从上一张幻灯片过渡到当前幻灯片的幻灯片过渡类型。 也就是说，转换信息存储在转换完成后出现的幻灯片上。

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
                    advClick (单击前进)
                </td>
                <td>
                    指定鼠标单击是否使幻灯片前进。 如果未指定此属性，则假定值为 true.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    advTm (时间过后前进 / Advance after time) 
                </td>
                <td>
                    指定转换应开始的时间（以毫秒为单位）。 此设置可以与 advClick 属性结合使用。 如果未指定此属性，则假定不会发生自动前进. </br></br>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    spd (过渡速度)
                </td>
                <td>
                    指定从当前幻灯片过渡到下一张幻灯片时要使用的过渡速度.</br></br>
                    该属性的可能值由 ST_TransitionSpeed 简单类型定义 (§19.7.54).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SlideTransition) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **transition (Slide Transition for a Slide Layout)**

    This element specifies the kind of slide transition that should be used to transition to the current slide from the previous slide. That is, the transition information is stored on the slide that appears after the transition is complete.

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
                    advClick (Advance on Click)
                </td>
                <td>
                    Specifies whether a mouse click advances the slide or not. If this attribute is not specified then a value of true is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    advCladvTm (Advance after time)
                </td>
                <td>
                    Specifies the time, in milliseconds, after which the transition should start. This setting can be used in conjunction with the advClick attribute. If this attribute is not specified then it is assumed that no auto-advance occurs. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
            <tr>
                <td>
                    spd (Transition Speed)
                </td>
                <td>
                    Specifies the transition speed that is to be used when transitioning from the current slide to the next.</br></br>
                    The possible values for this attribute are defined by the ST_TransitionSpeed simple type (§19.7.54).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideTransition) is located in §A.3. end note]

### 19.3.1.51 txBody (形状文本正文)

=== "中文"

    该元素指定相应形状中是否存在要包含的文本。 所有可见文本和可见文本相关属性都包含在此元素内。 可以有多个段落，并且段落内可以有多个文本段。

    [Note: 该元素内容模型 (CT_TextBody) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **txBody (Shape Text Body)**

    This element specifies the existence of text to be contained within the corresponding shape. All visible text and visible text related properties are contained within this element. There can be multiple paragraphs and within paragraphs multiple runs of text.

    [Note: The W3C XML Schema definition of this element’s content model (CT_TextBody) is located in §A.4.1. end note]

### 19.3.1.52 txStyles (幻灯片母版文本样式)

=== "中文"

    此元素指定幻灯片母版中的文本样式。 该元素内包含标题文本、正文文本和其他幻灯片文本的样式信息。 该元素仅在幻灯片母版中使用，因此可以设置相应演示文稿幻灯片的文本样式。

    !!! info "Example"

        考虑这样的情况：我们想要指定母版幻灯片的标题文本。

        ```xml
        <p:txStyles>
            <p:titleStyle>
                <a:lvl1pPr algn="ctr" rtl="0" latinLnBrk="0">
                    <a:spcBef>
                        <a:spcPct val="0"/>
                    </a:spcBef>
                    <a:buNone/>
                    <a:defRPr sz="4400" kern="1200">
                        <a:solidFill>
                            <a:schemeClr val="tx1"/>
                        </a:solidFill>
                        <a:latin typeface="+mj-lt"/>
                        <a:ea typeface="+mj-ea"/>
                        <a:cs typeface="+mj-cs"/>
                    </a:defRPr>
                </a:lvl1pPr>
            </p:titleStyle>
        </p:txStyles>
        ```

        在上面的示例中，标题文本是根据演示文稿中所有相关幻灯片的上述格式设置的。
    
    [Note: 该元素内容模型 (CT_SlideMasterTextStyles) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **txStyles (Slide Master Text Styles)**

    This element specifies the text styles within a slide master. Within this element is the styling information for title text, the body text and other slide text as well. This element is only for use within the Slide Master and thus sets the text styles for the corresponding presentation slides.

    !!! info "Example"

        Consider the case where we would like to specify the title text for a master slide.

        ```xml
        <p:txStyles>
            <p:titleStyle>
                <a:lvl1pPr algn="ctr" rtl="0" latinLnBrk="0">
                    <a:spcBef>
                        <a:spcPct val="0"/>
                    </a:spcBef>
                    <a:buNone/>
                    <a:defRPr sz="4400" kern="1200">
                        <a:solidFill>
                            <a:schemeClr val="tx1"/>
                        </a:solidFill>
                        <a:latin typeface="+mj-lt"/>
                        <a:ea typeface="+mj-ea"/>
                        <a:cs typeface="+mj-cs"/>
                    </a:defRPr>
                </a:lvl1pPr>
            </p:titleStyle>
        </p:txStyles>
        ```

        In the above example the title text is set according to the above formatting for all related slides within the presentation. 
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_SlideMasterTextStyles) is located in §A.3. end note]

### 19.3.1.53 xfrm (图形框架的 2D 变换)

=== "中文"

    该元素指定要应用于相应图形框架的变换。 此变换应用于图形框架，就像应用于形状或组形状一样。

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
                    flipH (水平翻转)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    这指定水平翻转。 当为 true 时，此属性定义形状围绕其边界框的中心水平翻转.</br></br>
                    [Example: 下图说明了水平翻转的效果.</br></br>
                    ![img](./imgs/19pml-6.png)</br></br>
                    end example]</br></br> 
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    flipV (垂直翻转)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定垂直翻转。 当为 true 时，此属性定义组围绕其边界框的中心垂直翻转.</br></br>
                    [Example: 下图说明了垂直翻转的效果.</br></br>
                    ![img](./imgs/19pml-6-1.png)</br></br>
                    end example]</br></br> 
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    rot (旋转)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    指定图形框架的旋转。 指定此属性的单位驻留在下面引用的简单类型定义中.</br></br>
                    该属性的可能值由 ST_Angle 简单类型 (§20.1.10.3) 定义。
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: 该元素内容模型 (CT_Transform2D) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **xfrm (2D Transform for Graphic Frame)**

    This element specifies the transform to be applied to the corresponding graphic frame. This transformation is applied to the graphic frame just as it would be for a shape or group shape.

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
                    flipH (Horizontal Flip)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    ThisSpecifies a horizontal flip. When true, this attribute defines that the shape is flipped horizontally about the center of its bounding box.</br></br>
                    [Example: The following illustrates the effect of a horizontal flip.</br></br>
                    ![img](./imgs/19pml-6.png)</br></br>
                    end example]</br></br> The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    flipV (Vertical Flip)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies a vertical flip. When true, this attribute defines that the group is flipped vertically about the center of its bounding box.</br></br>
                    [Example: The following illustrates the effect of a vertical flip.</br></br>
                    ![img](./imgs/19pml-6-1.png)</br></br>
                    end example]</br></br> The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    rot (Rotation)
                    Namespace: http://purl.oclc.org/ooxml/drawingml/main
                </td>
                <td>
                    Specifies the rotation of the Graphic Frame. The units for which this attribute is specified in reside within the simple type definition referenced below.</br></br>
                    The possible values for this attribute are defined by the ST_Angle simple type (§20.1.10.3).
                </td>
            </tr>
        </tbody>
    </table>
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_Transform2D) is located in §A.4.1. end note]

## 19.3.2 嵌入对象

=== "中文"

    在PresentationML 的幻灯片部分中，有嵌入的元素。 这些是可以嵌入幻灯片中的对象。 当我们将幻灯片定义为容器时，可以看出它不仅包含形状、图片和文本，还包含嵌入的对象，这些对象不一定是PresentationML 平台原生的。

=== "英文"

    **Embedded Objects**

    Within the slides portion of PresentationML, there are the embedded elements. These are objects that can be embedded within a slide. As we defined a slide to be a container it can be seen that it does not just contain shapes, pictures and text but embedded objects as well that are not necessarily native to the PresentationML platform.

### 19.3.2.1 control (嵌入式控制)

=== "中文"

    此元素指定幻灯片中是否存在嵌入式控件。

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
                    id (关系ID)
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定用于在幻灯片中标识此嵌入对象的关系 ID。</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    imgH (图像高度)
                </td>
                <td>
                    指定嵌入控件的高度.</br></br>
                    该属性的可能值由 ST_PositiveCooperative32 简单类型定义 (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    imgW (图像宽度)
                </td>
                <td>
                    指定嵌入控件的宽度.</br></br>
                    该属性的可能值由 ST_PositiveCooperative32 简单类型定义 (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    name (嵌入对象名称)
                </td>
                <td>
                    指定脚本语言使用的标识名称类。 该名称还用于构造剪贴板名称.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    showAsIcon (将嵌入对象显示为图标)
                </td>
                <td>
                    指定嵌入对象是显示为图标还是使用其本机表示形式.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Control) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **control (Embedded Control)**

    This element specifies the existence of an embedded control in the slide.

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
                    id (Relationship ID)
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the relationship id that is used to identify this Embedded object from within a slide.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    imgH (Image Height)
                </td>
                <td>
                    Specifies the height of the embedded control.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveCoordinate32 simple type (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    imgW (Image Width)
                </td>
                <td>
                    Specifies the width of the embedded control.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveCoordinate32 simple type (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    name (Embedded Object Name)
                </td>
                <td>
                    Specifies the identifying name class used by scripting languages. This name is also used to construct the clipboard name.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    showAsIcon (Show Embedded Object As Icon)
                </td>
                <td>
                    Specifies whether the Embedded object shows as an icon or using its native representation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Control) is located in §A.3. end note]

### 19.3.2.2 embed (嵌入对象或控件)

=== "中文"

    此元素指定嵌入在演示文稿中的嵌入对象或控件。

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
                    followColorScheme (嵌入对象的配色方案属性)
                </td>
                <td>
                    指定所指定的相应嵌入对象的配色方案属性.</br></br>
                    此属性的可能值由 ST_OleObjectFollowColorScheme 简单类型定义 (§19.7.6).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_OleObjectEmbed) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **embed (Embedded Object or Control)**

    This element specifies an Embedded object or Control that is embedded within the presentation.

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
                    followColorScheme (Color Scheme Properties for Embedded object)
                </td>
                <td>
                    Specifies the Color Scheme Properties for the corresponding Embedded object being specified.</br></br>
                    The possible values for this attribute are defined by the ST_OleObjectFollowColorScheme simple type (§19.7.6).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_OleObjectEmbed) is located in §A.3. end note]

### 19.3.2.3 link (链接对象或控件)

=== "中文"

    该元素指定到外部嵌入对象或控件的链接。

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
                    updateAutomatic (自动更新链接的嵌入对象)
                </td>
                <td>
                    此属性确定打开或打印演示文稿时是否自动更新链接的嵌入对象.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_OleObjectLink) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **link (Linked Object or Control)**

    This element specifies a link to an external Embedded object or Control.

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
                    updateAutomatic (Update Linked Embedded Objects Automatically)
                </td>
                <td>
                    This attribute determines if linked embedded objects are automatically updated when the presentation is opened or printed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_OleObjectLink) is located in §A.3. end note]

### 19.3.2.4 oleObj (嵌入式对象和控件的全局元素)

=== "中文"

    该元素指定用于嵌入对象和控件的全局元素。
    
    当 oleObject 元素包含 pic 子元素时，在决定使用哪个标识符时，应忽略 pic/nvPicPr/cNvPr@id 属性指定的标识符，并使用 GraphicFrame/nvGraphicFramePr/cNvPr@id 属性指定的标识符 OLE 对象。

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
                    id (关系ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定用于在幻灯片中识别此嵌入对象的关系 ID.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    imgH (图像高度)
                </td>
                <td>
                    指定嵌入控件的高度.</br></br>
                    该属性的可能值由 ST_PositiveCooperative32 简单类型定义 (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    imgW (Image Width)
                </td>
                <td>
                    指定嵌入控件的宽度.</br></br>
                    该属性的可能值由 ST_PositiveCooperative32 简单类型定义 (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    name (嵌入对象名称)
                </td>
                <td>
                    指定脚本语言使用的标识名称类。 该名称还用于构造剪贴板名称.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    progId (嵌入对象 ProgID)
                </td>
                <td>
                    指定嵌入对象的 progid. </br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    showAsIcon (将嵌入对象显示为图标)
                </td>
                <td>
                    指定嵌入对象是显示为图标还是使用其本机表示形式.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_OleObject) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **oleObj (Global Element for Embedded objects and Controls)**

    This element specifies a global element to be used for an Embedded object and Control. 
    
    When the oleObject element contains a pic child element, the identifier specified by the pic/nvPicPr/cNvPr@id attribute shall be ignored and the identifier specified by the graphicFrame/nvGraphicFramePr/cNvPr@id attribute shall be used when deciding which identifier to use for the OLE object.

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
                    id (Relationship ID)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the relationship id that is used to identify this Embedded object from within a slide.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    imgH (Image Height)
                </td>
                <td>
                    Specifies the height of the embedded control.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveCoordinate32 simple type (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    imgW (Image Width)
                </td>
                <td>
                    Specifies the width of the embedded control.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveCoordinate32 simple type (§20.1.10.43).
                </td>
            </tr>
            <tr>
                <td>
                    name (Embedded Object Name)
                </td>
                <td>
                    Specifies the identifying name class used by scripting languages. This name is also used to construct the clipboard name.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    progId (Embedded Object ProgID)
                </td>
                <td>
                    Specifies the progid for an Embedded object. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    showAsIcon (Show Embedded Object As Icon)
                </td>
                <td>
                    Specifies whether the Embedded object shows as an icon or using its native representation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_OleObject) is located in §A.3. end note]

## 19.3.3 可编程标签

=== "中文"

    在PresentationML 的幻灯片部分内有标签元素。 这些是可扩展性名称和值，有助于存储旧文件格式中的遗留变量。

=== "英文"

    **Programmable Tags**

    Within the slides portion of PresentationML there are the tag elements. These are extensibility names and values that assist in the storage of legacy variables from older file formats.

### 19.3.3.1 tag (可编程扩展性标签)

=== "中文"

    该元素指定用于存储遗留变量的可编程扩展性标签。

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
                    name (名称)
                </td>
                <td>
                    指定与该特定可编程标签关联的名称.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
            <tr>
                <td>
                    val (值)
                </td>
                <td>
                    指定与该特定可编程标签关联的值.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_StringTag) 的 W3C XML 架构定义位于 §A.3 中。 end note]

=== "英文"

    **tag (Programmable Extensibility Tag)**

    This element specifies a programmable extensibility tag to be used for storage of legacy variables.

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
                    Specifies the name associated with this specific programmable tag.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    val (Value)
                </td>
                <td>
                    Specifies the value associated with this specific programmable tag.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_StringTag) is located in §A.3. end note]

### 19.3.3.2 tagLst (可编程选项卡列表)

=== "中文"

    此元素指定用于存储旧文件格式变量的可编程扩展性标记的列表。

    [Note: 该元素内容模型 (CT_TagList) 的 W3C XML 模式定义位于 §A.3 中。 end note]

=== "英文"

    **tagLst (Programmable Tab List)**

    This element specifies the list of programmable extensibility tags that are used to store variables from legacy file formats.

    [Note: The W3C XML Schema definition of this element’s content model (CT_TagList) is located in §A.3. end note]
