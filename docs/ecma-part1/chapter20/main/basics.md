
# 20.1.2 基础

=== "中文"

    本节描述与 DrawingML 框架相关的所有基本常见元素。

=== "英文"

    **Basics**

    This section describes all the basic common elements associated with the DrawingML framework.

## 20.1.2.1 测量单位 EMU

=== "中文"

    在整个 ECMA-376 中，EMU 用作长度测量单位。 EMU的定义如下：

    1 emu $=\frac{1}{914400}$ US 英尺(inch) $=\frac{1}{360000}$ 厘米(cm)

    !!! info "Rationale"
        
        EMU 的创建是为了能够均匀划分英制和公制单位，以避免计算过程中的舍入错误。 EMU 的使用还促进了使用不同测量单位的不同区域之间更加无缝的系统切换和互操作性。 EMU 定义了一个基于整数的高精度坐标系。

=== "英文"

    **EMU Unit of Measurement**

    Throughout ECMA-376, the EMU is used as a unit of measurement for length. An EMU is defined as follows:

    1 emu $=\frac{1}{914400}$ US inch $=\frac{1}{360000}$ cm

    [Rationale: The EMU was created in order to be able to evenly divide in both English and Metric units, in order to avoid rounding errors during the calculation. The usage of EMUs also facilitates a more seamless system switch and interoperability between different locales utilizing different units of measurement. EMUs define an integer based, high precision coordinate system. end rationale]

## 20.1.2.2 核心绘图对象信息

=== "中文"

    在 DrawingML 中，存在核心绘图元素的概念。 这些元素对于 DrawingML 框架至关重要且很常见。 这些元素表示 DrawingML 文档结构中最完整的部分，因此是使用最广泛的元素之一。
    
    !!! info "Note"
        
        测量单位 - 长度单位必须以与设备无关的物理单位表示： 英制公制单位 (EMU)、点(points)、派卡(pica)和英寸(inche)。 不得使用与设备相关的单位，例如像素。

=== "英文"

    **Core Drawing Object Information**

    Within DrawingML, there is the notion of core drawing elements. These are elements that both are vital to and common across the DrawingML framework. These elements denote the most integral pieces of the DrawingML document structure and thus are among the most widely used.
    
    [Note: Measurement Units - Length units must be expressed in device-independent physical units: English Metric units (EMUs), points, picas, and inches. Device-dependent units such as pixels must not be used. end note]

### 20.1.2.2.1 bldChart (构建图表)

=== "中文"

    该元素指定如何构建图表的动画。
    
    !!! info "Example"
    
        考虑以下示例，其中图表被指定为按类别而不是作为一个实体进行动画处理。 因此，bldChart 元素应按如下方式使用：

        ```xml
        <p:bdldLst>
            <p:bldGraphic spid="4" grpId="0">
                <p:bldSub>
                    <a:bldChart bld="category"/>
                </p:bldSub>
            </p:bldGraphic>
        </p:bldLst>
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
                    animBg (动画背景)
                </td>
                <td>
                    指定图表背景元素是否也应设置动画.</br>
                    [Note: 背景元素的示例是网格线和图表图例. end note]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    bld (建造)
                </td>
                <td>
                    指定图表的构建方式。 动画按照此属性定义的特定顺序对容器中的子元素进行动画处理.</br></br>
                    此属性的可能值由 ST_AnimationChartBuildType 简单类型 (§20.1.10.5) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AnimationChartBuildProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **bldChart (Build Chart)**

    This element specifies how to build the animation for a diagram.
    
    !!! info "Example"
    
        Consider the following example where a chart is specified to be animated by category rather than as one entity. Thus, the bldChart element should be used as follows:

        ```xml
        <p:bdldLst>
            <p:bldGraphic spid="4" grpId="0">
                <p:bldSub>
                    <a:bldChart bld="category"/>
                </p:bldSub>
            </p:bldGraphic>
        </p:bldLst>
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
                    animBg (Animate Background)
                </td>
                <td>
                    Specifies whether or not the chart background elements should be animated as well.</br>
                    [Note: An example of background elements are grid lines and the chart legend. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    bld (Build)
                </td>
                <td>
                    Specifies how the chart is built. The animation animates the sub-elements in the container in the particular order defined by this attribute.</br></br>
                    The possible values for this attribute are defined by the ST_AnimationChartBuildType simple type (§20.1.10.5).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AnimationChartBuildProperties) is located in §A.4.1. end note]

### 20.1.2.2.2 bldDgm (构建图)

=== "中文"

    该元素指定如何构建图表的动画。
    
    !!! info "Example"
    
        考虑让图表显示为实体而不是部分。 bldDgm 元素应按如下方式使用：

        ```xml
        <p:bdldLst>
            <p:bldGraphic spid="4" grpId="0">
                <p:bldSub>
                    <a:bldDgm bld="one"/>
                </p:bldSub>
            </p:bldGraphic>
        </p:bldLst>
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
                    bld (建造)
                </td>
                <td>
                    指定图表的构建方式。 动画按照此属性定义的特定顺序对容器中的子元素进行动画处理.</br></br>
                    此属性的可能值由 ST_AnimationDgmBuildType 简单类型 (§20.1.10.7) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    rev (Reverse Animation)
                </td>
                <td>
                    指定该图中对象的动画是否应该反转。 如果未指定此属性，则假定值为 false. </br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 这个元素的内容模型（CT_AnimationDgmBuildProperties）的 W3C XML Schema定义位于§A.4.1。 end note]

=== "英文"

    **bldDgm (Build Diagram)**

    This element specifies how to build the animation for a diagram.
    
    !!! info "Example"
    
        Consider having a diagram appear as on entity as opposed to by section. The bldDgm element should be used as follows:

        ```xml
        <p:bdldLst>
            <p:bldGraphic spid="4" grpId="0">
                <p:bldSub>
                    <a:bldDgm bld="one"/>
                </p:bldSub>
            </p:bldGraphic>
        </p:bldLst>
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
                    bld (Build)
                </td>
                <td>
                    Specifies how the chart is built. The animation animates the sub-elements in the container in the particular order defined by this attribute.</br></br>
                    The possible values for this attribute are defined by the ST_AnimationDgmBuildType simple type (§20.1.10.7).
                </td>
            </tr>
            <tr>
                <td>
                    rev (Reverse Animation)
                </td>
                <td>
                    Specifies whether the animation of the objects in this diagram should be reversed or not. If this attribute is not specified, a value of false is assumed. </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AnimationDgmBuildProperties) is located in §A.4.1. end note]

### 20.1.2.2.3 chart (图表动画)

=== "中文"

    该元素指定了在幻灯片动画序列中应该被动画的图表的引用。除了作为对图表的引用之外，还定义了动画构建步骤。

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
                    bldStep (动画构建步骤)
                </td>
                <td>
                    指定使用哪个步骤来构建图表的这一部分。例如，图表可以作为一个整体构建，这意味着它将作为一个单一的图形进行动画。另外，图表也可以进行动画，或者作为单独的部分构建。.</br></br>
                    这个属性的可能取值由ST_ChartBuildStep简单类型（§20.1.10.13）定义。
                </td>
            </tr>
            <tr>
                <td>
                    categoryIdx (类别索引) 
                </td>
                <td>
                    指定应在相应图表中进行动画处理的类别索引。  </br></br>
                    此属性的可能值由 W3C XML Schema int 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    seriesIdx (系列索引)
                </td>
                <td>
                    指定应设置动画的相应图表中的系列索引.   </br></br>
                    此属性的可能值由 W3C XML Schema int 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AnimationChartElement) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **chart (Chart to Animate)**

    This element specifies a reference to a chart that should be animated within a sequence of slide animations. In addition to simply acting as a reference to a chart there is also animation build steps defined.

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
                    bldStep (Animation Build Step)
                </td>
                <td>
                    Specifies which step this part of the chart should be built using. For instance the chart can be built as one object meaning it is animated as a single graphic. Alternatively the chart can be animated, or built as separate pieces.</br></br>
                    The possible values for this attribute are defined by the ST_ChartBuildStep simple type (§20.1.10.13).
                </td>
            </tr>
            <tr>
                <td>
                    categoryIdx (Category Index) 
                </td>
                <td>
                    Specifies the index of the category within the corresponding chart that should be animated.  </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema int datatype.
                </td>
            </tr>
            <tr>
                <td>
                    seriesIdx (Series Index)
                </td>
                <td>
                    Specifies the index of the series within the corresponding chart that should be animated.   </br></br>
                    The possible values for this attribute are defined by the W3C XML Schema int datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AnimationChartElement) is located in §A.4.1. end note]

### 20.1.2.2.4 cNvCxnSpPr (非可视连接器形状绘图属性)

=== "中文"

    此元素指定连接器形状的非可视绘图属性。 这些非视觉属性是生成应用程序在渲染幻灯片表面时将使用的属性。
    
    [Note: 该元素内容模型 (CT_NonVisualConnectorProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvCxnSpPr (Non-Visual Connector Shape Drawing Properties)**

    This element specifies the non-visual drawing properties for a connector shape. These non-visual properties are properties that the generating application would utilize when rendering the slide surface.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualConnectorProperties) is located in §A.4.1. end note]

### 20.1.2.2.5 cNvGraphicFramePr (非可视图形框架绘图属性)

=== "中文"

    该元素指定图形框架的非可视绘图属性。 这些非视觉属性是生成应用程序在渲染幻灯片表面时将使用的属性。

    [Note: 该元素内容模型 (CT_NonVisualGraphicFrameProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvGraphicFramePr (Non-Visual Graphic Frame Drawing Properties)**

    This element specifies the non-visual drawing properties for a graphic frame. These non-visual properties are properties that the generating application would utilize when rendering the slide surface.

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualGraphicFrameProperties) is located in §A.4.1. end note]

### 20.1.2.2.6 cNvGrpSpPr (非可视组形状绘图属性)

=== "中文"

    此元素指定组形状的非可视绘图属性。 这些非视觉属性是生成应用程序在渲染幻灯片表面时将使用的属性。

    [Note: 此元素内容模型 (CT_NonVisualGroupDrawingShapeProps) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cNvGrpSpPr (Non-Visual Group Shape Drawing Properties)**

    This element specifies the non-visual drawing properties for a group shape. These non-visual properties are properties that the generating application would utilize when rendering the slide surface.

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualGroupDrawingShapeProps) is located in §A.4.1. end note]

### 20.1.2.2.7 cNvPicPr (非视觉绘图属性)

=== "中文"

    该元素指定图片画布的非视觉属性。 生成应用程序将使用这些属性来确定如何更改所讨论的图片对象的某些属性。

    !!! info "Example"

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
                    preferRelativeResize (首选相对调整大小)
                </td>
                <td>
                    指定用户界面是否应根据图片的当前大小或其原始大小显示图片的大小调整。 如果此属性设置为 true，则缩放相对于原始图片大小而不是当前图片大小.</br></br>
                    [Example: 考虑这样的情况：文档中的图片大小已调整，现在是原始插入图片大小的 50%。 现在，如果用户选择稍后在生成应用程序中调整该图片的大小，则应检查该属性的值.</br></br>
                    如果此属性设置为 true，则显示值 50%。 同样，如果此属性设置为 false，则应显示 100% 的值，因为图片尚未从其当前（较小）尺寸调整大小. end example]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_NonVisualPictureProperties) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **cNvPicPr (Non-Visual Picture Drawing Properties)**

    This element specifies the non-visual properties for the picture canvas. These properties are to be used by the generating application to determine how certain properties are to be changed for the picture object in question.

    !!! info "Example"

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
                    preferRelativeResize (Relative Resize Preferred)
                </td>
                <td>
                    Specifies if the user interface should show the resizing of the picture based on the picture's current size or its original size. If this attribute is set to true, then scaling is relative to the original picture size as opposed to the current picture size.</br></br>
                    [Example: Consider the case where a picture has been resized within a document and is now 50% of the originally inserted picture size. Now if the user chooses to make a later adjustment to the size of this picture within the generating application, then the value of this attribute should be checked.</br></br>
                    If this attribute is set to true then a value of 50% is shown. Similarly, if this attribute is set to false, then a value of 100% should be shown because the picture has not yet been resized from its current (smaller) size. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualPictureProperties) is located in §A.4.1. end note]

### 20.1.2.2.8 cNvPr (非可视绘图属性)

=== "中文"

    该元素指定非可视画布属性。 这允许存储不影响图片外观的附加信息。

    !!! info "Example"
        
        考虑以下 DrawingML。

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
                    descr (对象的替代文本)
                </td>
                <td>
                    指定当前 DrawingML 对象的替代文本，供不显示当前对象的辅助技术或应用程序使用.</br></br>
                    如果省略此元素，则父对象不存在替代文本.</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `<… descr="A picture of a bowl of fruit">`</br>
                    descr 属性包含可替代实际 DrawingML 对象的替代文本. end example]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    hidden (隐藏)
                </td>
                <td>
                    指定是否显示此 DrawingML 对象。 当 DrawingML 对象在文档中显示时，该对象可以隐藏（即存在，但不可见）. </br></br>
                    该属性决定对象是渲染还是隐藏。 [Note：应用程序可以具有允许查看此对象的设置. end note]</br></br>
                    如果省略此属性，则应显示父 DrawingML 对象（即不隐藏）.</br></br>
                    [Example: 考虑一个必须隐藏在文档内容中的内联 DrawingML 对象。 该设置将指定如下:</br></br>
                    `<… hidden="true" />`</br>
                    hide 属性的值为 true，它指定 DrawingML 对象是隐藏的，并且在显示文档时不显示. end example]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    id (唯一标识符)
                </td>
                <td>
                    指定当前文档中当前 DrawingML 对象的唯一标识符。 该 ID 可用于帮助唯一标识该对象，以便文档的其他部分可以引用它.</br></br>
                    如果同一文档中的多个对象共享相同的 id 属性值，则该文档应被视为不合格.</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `<… id="10" … >`</br>
                    id 属性的值为 10，这是此 DrawingML 对象的唯一标识符. end example]</br></br>
                    此属性的可能值由 ST_DrawingElementId 简单类型 (§20.1.10.21) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    name (名称)
                </td>
                <td>
                    指定对象的名称. [Note: 通常，这用于存储图片对象的原始文件名. end note] </br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `< … name="foo.jpg" >`</br>
                    name 属性的值为 foo.jpg，这是此 DrawingML 对象的名称. end example]</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    title (标题)
                </td>
                <td>
                    指定当前 DrawingML 对象的标题 (caption).  </br></br>
                    如果省略此属性，则父对象不存在标题文本.</br></br>
                    [Example: 考虑定义如下的 DrawingML 对象:</br></br>
                    `<… title="Process Flow Diagram">`</br>
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
                    descr (Alternative Text for Object)
                </td>
                <td>
                    Specifies alternative text for the current DrawingML object, for use by assistive technologies or applications which do not display the current object.</br></br>
                    If this element is omitted, then no alternative text is present for the parent object.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… descr="A picture of a bowl of fruit">`</br>
                    The descr attribute contains alternative text which can be used in place of the actual DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    hidden (Hidden)
                </td>
                <td>
                    Specifies whether this DrawingML object is displayed. When a DrawingML object is displayed within a document, that object can be hidden (i.e., present, but not visible). </br></br>
                    This attribute determines whether the object is rendered or made hidden. [Note: An application can have settings which allow this object to be viewed. end note]</br></br>
                    If this attribute is omitted, then the parent DrawingML object shall be displayed (i.e., not hidden).</br></br>
                    [Example: Consider an inline DrawingML object which must be hidden within the document's content. This setting would be specified as follows:</br></br>
                    `<… hidden="true" />`</br>
                    The hidden attribute has a value of true, which specifies that the DrawingML object is hidden and not displayed when the document is displayed. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    id (Unique Identifier)
                </td>
                <td>
                    Specifies a unique identifier for the current DrawingML object within the current document. This ID can be used to assist in uniquely identifying this object so that it can be referred to by other parts of the document.</br></br>
                    If multiple objects within the same document share the same id attribute value, then the document shall be considered non-conformant.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… id="10" … >`</br>
                    The id attribute has a value of 10, which is the unique identifier for this DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the ST_DrawingElementId simple type (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    name (Name)
                </td>
                <td>
                    Specifies the name of the object. [Note: Typically, this is used to store the original file name of a picture object. end note] </br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `< … name="foo.jpg" >`</br>
                    The name attribute has a value of foo.jpg, which is the name of this DrawingML object. end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    title (Title)
                </td>
                <td>
                    Specifies the title (caption) of the current DrawingML object.  </br></br>
                    If this attribute is omitted, then no title text is present for the parent object.</br></br>
                    [Example: Consider a DrawingML object defined as follows:</br></br>
                    `<… title="Process Flow Diagram">`</br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualDrawingProps) is located in §A.4.1. end note]

### 20.1.2.2.9 cNvSpPr (非视觉形状绘图属性)

=== "中文"

    该元素指定形状的非可视绘图属性。 生成应用程序将使用这些属性来确定如何处理形状

    !!! info "Example"
        
        考虑应用了形状锁定的形状。

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

        该形状锁存储在该形状的非可视绘图属性中。

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
                    txBox (文本框)
                </td>
                <td>
                    指定相应的形状是文本框，因此生成应用程序应将其视为文本框。 如果省略此属性，则假定相应的形状不是特定的文本框.</br></br>
                    [Note: 由于形状未指定为文本框，并不意味着它不能附加文本。 文本框只是具有特定属性的特殊形状. end note]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_NonVisualDrawingShapeProps) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **Non-Visual Shape Drawing Properties**

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
                    txBox (Text Box)
                </td>
                <td>
                    Specifies that the corresponding shape is a text box and thus should be treated as such by the generating application. If this attribute is omitted then it is assumed that the corresponding shape is not specifically a text box.</br></br>
                    [Note: Because a shape is not specified to be a text box does not mean that it cannot have text attached to it. A text box is merely a specialized shape with specific properties. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_NonVisualDrawingShapeProps) is located in §A.4.1. end note]

### 20.1.2.2.10 cxnSp (连接形状)

=== "中文"

    该元素指定用于连接两个 sp 元素的连接形状。 使用 cxnSp 指定连接后，生成应用程序将确定连接器采用的确切路径。
    
    也就是说，连接器路由算法由生成的应用程序决定，因为所需的路径可能会根据应用程序的特定需求而有所不同。

    ![111](./imgs/20dml-1.png)

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

    [Note: 该元素内容模型 (CT_GvmlConnector) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **cxnSp (Connection Shape)**

    This element specifies a connection shape that is used to connect two sp elements. Once a connection is specified using a cxnSp, it is left to the generating application to determine the exact path the connector takes.
    
    That is the connector routing algorithm is left up to the generating application as the desired path might be different depending on the specific needs of the application.

    ![111](./imgs/20dml-1.png)

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

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlConnector) is located in §A.4.1. end note]

### 20.1.2.2.11 cxnSpLocks (连接形状锁)

=== "中文"

    该元素指定连接形状的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改。

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
                    noAdjustHandles (禁止显示调整手柄)
                </td>
                <td>
                    指定生成应用程序不应显示相应连接形状的调整手柄。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (禁止箭头更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的箭头。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (禁止形状类型更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状类型。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints (禁止形状点编辑)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状点。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状分组)
                </td>
                <td>
                    指定生成应用程序不应允许对相应连接形状进行形状分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止形状移动)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的位置更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的尺寸。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (禁止形状旋转)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的形状旋转更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定生成应用程序不应允许选择相应的连接形状。 这还意味着，如果指定了此属性，则无法选择附加到此连接形状的图片、形状或文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ConnectorLocking) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **cxnSpLocks (Connection Shape Locks)**

    This element specifies all locking properties for a connection shape. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noAdjustHandles (Disallow Showing Adjust Handles)
                </td>
                <td>
                    Specifies that the generating application should not show adjust handles for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (Disallow Arrowhead Changes)
                </td>
                <td>
                    Specifies that the generating application should not allow arrowhead changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema booleandatatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (Disallow ShapeType Change)
                </td>
                <td>
                    Specifies that the generating application should not allow shape type changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints (Disallow Shape Point Editing)
                </td>
                <td>
                    Specifies that the generating application should not allow shape point changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the generating application should not allow shape grouping for the corresponding connection shape. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Shape Movement)
                </td>
                <td>
                    Specifies that the generating application should not allow position changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resize)
                </td>
                <td>
                    Specifies that the generating application should not allow size changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (Disallow Shape Rotation)
                </td>
                <td>
                    Specifies that the generating application should not allow shape rotation changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of the corresponding connection shape. That means also that no picture, shapes or text attached to this connection shape can be selected if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ConnectorLocking) is located in §A.4.1. end note]

### 20.1.2.2.12 dgm (图表动画)

=== "中文"

    此元素指定对应在幻灯片动画序列中进行动画处理的图表的引用。

    除了简单地充当图表的参考之外，还定义了动画构建步骤。

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
                    bldStep (动画构建步骤)
                </td>
                <td>
                    指定应使用哪个步骤来构建图的这一部分。 例如，图表可以构建为一个对象，这意味着它可以作为单个图形进行动画处理。 或者，图表可以是动画的，或者构建为单独的部分.</br></br>
                    此属性的可能值由 ST_DgmBuildStep 简单类型 (§20.1.10.20) 定义。
                </td>
            </tr>
            <tr>
                <td>
                    id (标识符)
                </td>
                <td>
                    指定动画中此构建步骤的形状的 GUID.</br></br>
                    该属性的可能值由 ST_Guid 简单类型定义 (§22.9.2.4).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_AnimationDgmElement) 的 W3C XML 架构定义位于 §A.4.1. end note]

=== "英文"

    **dgm (Diagram to Animate)**

    This element specifies a reference to a diagram that should be animated within a sequence of slide animations.
    
    In addition to simply acting as a reference to a diagram there is also animation build steps defined.

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
                    bldStep (Animation Build Step)
                </td>
                <td>
                    Specifies which step this part of the diagram should be built using. For instance the diagram can be built as one object meaning it is animated as a single graphic. Alternatively the diagram can be animated, or built as separate pieces.</br></br>
                    The possible values for this attribute are defined by the ST_DgmBuildStep simple type (§20.1.10.20).
                </td>
            </tr>
            <tr>
                <td>
                    id (Identifier)
                </td>
                <td>
                    Specifies the GUID of the shape for this build step in the animation.</br></br>
                    The possible values for this attribute are defined by the ST_Guid simple type (§22.9.2.4).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_AnimationDgmElement) is located in §A.4.1. end note]

### 20.1.2.2.13 endCxn (连接结束)

=== "中文"

    该元素指定应由相应连接器形状形成的结束连接。 这会将连接器的尾部连接到最终目标形状。

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
                    id (标识符)
                </td>
                <td>
                    指定要进行最终连接的形状的 id.</br></br>
                    该属性的可能值由 ST_DrawingElementId 简单类型定义 (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    idx (索引)
                </td>
                <td>
                    指定最终连接形状的连接站点表的索引。 即一个形状上有很多连接点，需要指定对应的连接器形状应该连接到哪个连接点.</br></br>
                    此属性的可能值由 W3C XML 架构 unsignedInt 数据类型定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Connection) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **endCxn (Connection End)**

    This element specifies the ending connection that should be made by the corresponding connector shape. This connects the end tail of the connector to the final destination shape.

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
                    id (Identifier)
                </td>
                <td>
                    Specifies the id of the shape to make the final connection to.</br></br>
                    The possible values for this attribute are defined by the ST_DrawingElementId simple type (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    idx (Index)
                </td>
                <td>
                    Specifies the index into the connection site table of the final connection shape. That is there are many connection sites on a shape and it shall be specified which connection site the corresponding connector shape should connect to.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Connection) is located in §A.4.1. end note]

### 20.1.2.2.14 ext (扩展)

=== "中文"

    此元素指定用于将来对 DrawingML 当前版本进行扩展的扩展。 这允许将来指定当前未知的元素，用于生成应用程序的更高版本。

    [Note: 该元素无意将过渡模式重新引入严格一致性类别. end note]

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
                    uri (统一资源标识符)
                </td>
                <td>
                    指定表示存储在该标签下的数据的 URI 或统一资源标识符。 URI 用于识别可以处理此标签内容的正确“服务器”.</br></br>
                    此属性的可能值由 W3C XML 架构token数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 此属性的可能值由 W3C XML 架构令牌数据类型定义。 end note]

=== "英文"

    **ext (Extension)**

    This element specifies an extension that is used for future extensions to the current version of DrawingML. This allows for the specifying of currently unknown elements in the future that is used for later versions of generating applications.

    [Note: This element is not intended to reintroduce transitional schema into the strict conformance class. end note]

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
                    uri (Uniform Resource Identifier)
                </td>
                <td>
                    Specifies the URI, or uniform resource identifier that represents the data stored under this tag. The URI is used to identify the correct 'server' that can process the contents of this tag.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema token datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_OfficeArtExtension) is located in §A.4.1. end note]

### 20.1.2.2.15 extLst (扩展列表)

=== "中文"

    该元素指定扩展列表，在其中定义元素类型 ext 的所有未来扩展。 扩展列表以及相应的未来扩展用于扩展 DrawingML 框架的存储功能。 这允许各种新类型的数据本地存储在框架内。

    [Note: 此元素的内容模型 (CT_OfficeArtExtensionList) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **extLst (Extension List)**

    This element specifies the extension list within which all future extensions of element type ext is defined. The extension list along with corresponding future extensions is used to extend the storage capabilities of the DrawingML framework. This allows for various new types of data to be stored natively within the framework.

    [Note: The W3C XML Schema definition of this element’s content model (CT_OfficeArtExtensionList) is located in §A.4.1. end note]

### 20.1.2.2.16 graphic (图形对象)

=== "中文"

    该元素指定单个图形对象的存在。 当文档作者希望保留某种图形对象时，应该引用此元素。 该图形对象的规范完全由文档作者提供，并在 GraphicData 子元素中引用.
    
    [Note: 该元素内容模型 (CT_GraphicalObject) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **graphic (Graphic Object)**

    This element specifies the existence of a single graphic object. Document authors should refer to this element when they wish to persist a graphical object of some kind. The specification for this graphical object is provided entirely by the document author and referenced within the graphicData child element.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_GraphicalObject) is located in §A.4.1. end note]

### 20.1.2.2.17 graphicData (图形对象数据)

=== "中文"

    该元素指定对文档中图形对象的引用。 该图形对象完全由选择将此数据保留在文档中的文档作者提供。
    
    [Note: 根据所使用的图形对象的类型，并非每个支持 OOXML 框架的生成应用程序都能够呈现图形对象. end note]
    
    [Note: 该元素无意将过渡模式重新引入严格一致性类别. end note]

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
                    uri (统一资源标识符)
                </td>
                <td>
                    指定表示存储在该标签下的数据的 URI 或统一资源标识符。 URI 用于识别可以处理此标签内容的正确“服务器”.</br></br>
                    此属性的可能值由 W3C XML 架构令牌数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GraphicalObjectData) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **graphicData (Graphic Object Data)**

    This element specifies the reference to a graphic object within the document. This graphic object is provided entirely by the document authors who choose to persist this data within the document.
    
    [Note: Depending on the kind of graphical object used not every generating application that supports the OOXML framework has the ability to render the graphical object. end note]
    
    [Note: This element is not intended to reintroduce transitional schema into the strict conformance class. end note]

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
                    uri (Uniform Resource Identifier)
                </td>
                <td>
                    Specifies the URI, or uniform resource identifier that represents the data stored under this tag. The URI is used to identify the correct 'server' that can process the contents of this tag.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema token datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GraphicalObjectData) is located in §A.4.1. end note]

### 20.1.2.2.18 graphicFrame (图框)

=== "中文"

    该元素指定图形框架的存在。 该框架包含由外部源生成的图形，并且需要一个容器来在幻灯片表面上显示。

    [Note: 该元素内容模型 (CT_GvmlGraphicalObjectFrame) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **graphicFrame (Graphic Frame)**

    This element specifies the existence of a graphics frame. This frame contains a graphic that was generated by an external source and needs a container in which to be displayed on the slide surface.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlGraphicalObjectFrame) is located in §A.4.1. end note]

### 20.1.2.2.19 graphicFrameLocks (图形框架锁)

=== "中文"

    该元素指定图形框架的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改.

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
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应图形框架的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noDrilldown (禁止选择子形状)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of objects within the corresponding graphic frame but allow selecting of the graphic frame itself. If this attribute is not specified, then a value of false is assumed.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状分组)
                </td>
                <td>
                    指定生成应用程序不应允许对相应图形框架进行形状分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止形状移动)
                </td>
                <td>
                    指定对应的图形框不能移动。 驻留在图形框架内的对象仍然可以移动，除非它们也已被锁定。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应图形框架的大小。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定生成应用程序不应允许选择相应的图片。 这还意味着，如果指定了此属性，则无法选择附加到此图片的任何图片、形状或文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GraphicalObjectFrameLocking) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **graphicFrameLocks (Graphic Frame Locks)**

    This element specifies all locking properties for a graphic frame. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding graphic frame. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noDrilldown (Disallow Selection of Child Shapes)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of objects within the corresponding graphic frame but allow selecting of the graphic frame itself. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the generating application should not allow shape grouping for the corresponding graphic frame. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Shape Movement)
                </td>
                <td>
                    Specifies that the corresponding graphic frame cannot be moved. Objects that reside within the graphic frame can still be moved unless they also have been locked. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resize)
                </td>
                <td>
                    Specifies that the generating application should not allow size changes for the corresponding graphic frame. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of the corresponding picture. That means also that no picture, shapes or text attached to this picture can be selected if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GraphicalObjectFrameLocking) is located in §A.4.1. end note]

### 20.1.2.2.20 grpSp (组合形状)

=== "中文"

    该元素指定一个组形状，表示组合在一起的许多形状。 该形状应被视为规则形状，但不是由单个几何形状来描述，而是由其中包含的所有形状几何形状组成。 在组形状中，组成该组的每个形状都按照通常的方式指定。 然而，对元素进行分组的想法是，单个变换可以同时应用于多个形状。

    !!! info "Example"

        考虑以下组合形状。

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

    [Note: 该元素内容模型 (CT_GvmlGroupShape) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **grpSp (Group shape)**

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

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlGroupShape) is located in §A.4.1. end note]

### 20.1.2.2.21 grpSpLocks (组合形状锁)

=== "中文"

    该元素指定连接形状的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改。

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
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状组合)
                </td>
                <td>
                    指定对应的组形状无法分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止移动形状)
                </td>
                <td>
                    指定对应的图形框不能移动。 驻留在图形框架内的对象仍然可以移动，除非它们也已被锁定。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定对应的组形状不能调整大小。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (禁止形状旋转)
                </td>
                <td>
                    指定相应的组形状无法旋转 驻留在组内的对象仍然可以旋转，除非它们也已被锁定。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定对应的组形状的任何部分都不能被选择。 这意味着如果指定了此属性，则无法选择图片、形状或附加文本。 如果未指定此属性，则假定值为 false.</br></br>
                    [Note: 该属性由子元素继承，因此当该属性设置为 true 时，无法选择组形状内的所有形状. end note]</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noUngrp (禁止形状取消组合)
                </td>
                <td>
                    指定生成应用程序不应显示相应连接形状的调整手柄。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GroupLocking) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **grpSpLocks (Group Shape Locks)**

    This element specifies all locking properties for a connection shape. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the corresponding group shape cannot be grouped. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Moving Shape)
                </td>
                <td>
                    Specifies that the corresponding graphic frame cannot be moved. Objects that reside within the graphic frame can still be moved unless they also have been locked. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resizing)
                </td>
                <td>
                    Specifies that the corresponding group shape cannot be resized. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (Disallow Shape Rotation)
                </td>
                <td>
                    Specifies that the corresponding group shape cannot be rotated Objects that reside within the group can still be rotated unless they also have been locked. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the corresponding group shape cannot have any part of it be selected. That means that no picture, shapes or attached text can be selected either if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    [Note: This property is inherited by sub-elements and thus all shapes within the group shape cannot be selected when this attribute is set to a value of true. end note]</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noUngrp (Disallow Shape Ungrouping)
                </td>
                <td>
                    Specifies that the generating application should not show adjust handles for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupLocking) is located in §A.4.1. end note]

### 20.1.2.2.22 grpSpPr (视觉组形状属性)

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
                    bwMode (黑白模式)
                </td>
                <td>
                    指定应仅使用黑色和白色来渲染组形状. </br></br>
                    也就是说，在渲染相应形状时，组形状的颜色信息应转换为黑色或白色.</br></br>
                    渲染该图像时不使用灰色，仅使用纯黑和纯白.</br></br>
                    [Note: 这并不意味着组形状本身仅存储有黑白颜色信息。 该属性设置渲染时形状使用的渲染模式. end note]</br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型 (§20.1.10.10) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_GroupShapeProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **grpSpPr (Visual Group Shape Properties)**

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
                    bwMode (Black and White Mode)
                </td>
                <td>
                    Specifies that the group shape should be rendered using only black and white coloring. </br></br>
                    That is the coloring information for the group shape should be converted to either black or white when rendering the corresponding shapes.</br></br>
                    No gray is to be used in rendering this image, only stark black and stark white.</br></br>
                    [Note: This does not mean that the group shapes themselves are stored with only black and white color information. This attribute instead sets the rendering mode that the shapes use when rendering. end note]</br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_GroupShapeProperties) is located in §A.4.1. end note]

### 20.1.2.2.23 hlinkHover (悬停的超链接)

=== "中文"

    该元素指定当用户鼠标悬停在相应对象上时要激活的超链接信息。 超链接的操作是当用户的鼠标悬停在对象上时激活指定的动作。 激活此操作后，可以使用附加属性来指定应与该操作一起执行的其他任务。

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
                    action (动作设定)
                </td>
                <td>
                    指定激活此超链接时要执行的操作。 这可用于指定要导航到的幻灯片或要运行的代码脚本.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    endSnd (结束声音)
                </td>
                <td>
                    指定相关 URL 是否应在单击该 URL 时停止正在播放的所有声音.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    highlightClick (突出显示单击)
                </td>
                <td>
                    指定此属性是否已在本文档中使用。 也就是说，当超链接已被访问时，将利用该属性，以便生成应用程序可以确定该文本的颜色。 如果省略此属性，则隐含值 0 或 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    history (添加超链接到页面历史记录)
                </td>
                <td>
                    指定导航到此 URI 时是否将此 URI 添加到历史记录中。 这允许观看该演示文稿而无需在观看机器上存储历史信息。 如果省略此属性，则假定值为 1 或 true.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    id (绘图对象超链接目标)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定在此幻灯片关系文件中查找时包含此超链接目标的关系 ID。 该属性不能省略.</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    invalidUrl (无效的网址)
                </td>
                <td>
                    当生成应用程序确定 URL 无效时指定该 URL。 也就是说，生成应用程序仍然可以存储 URL，但已知该 URL 不正确.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    tgtFrame (目标框架)
                </td>
                <td>
                    指定打开此超链接时要使用的目标框架。 当超链接被激活时，该属性用于确定是否启动新窗口以供查看或是否可以使用现有窗口。 如果省略此属性，则会打开一个新窗口.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    tooltip (超链接工具提示)
                </td>
                <td>
                    指定当鼠标悬停在超链接文本上时应显示的工具提示。 如果省略该属性，则可以显示超链接文本本身.</br></br>
                    此属性的可能值由 W3C XML 架构字符串数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Hyperlink) 的 W3C XML 模式定义位于 §A.4.1 中。 end note]

=== "英文"

    **hlinkHover (Hyperlink for Hover)**

    This element specifies the hyperlink information to be activated when the user's mouse is hovered over the corresponding object. The operation of the hyperlink is to have the specified action be activated when the mouse of the user hovers over the object. When this action is activated then additional attributes can be used to specify other tasks that should be performed along with the action.

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
                    action (Action Setting)
                </td>
                <td>
                    Specifies an action that is to be taken when this hyperlink is activated. This can be used to specify a slide to be navigated to or a script of code to be run.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    endSnd (End Sounds)
                </td>
                <td>
                    Specifies if the URL in question should stop all sounds that are playing when it is clicked.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    highlightClick (Highlight Click)
                </td>
                <td>
                    Specifies if this attribute has already been used within this document. That is when a hyperlink has already been visited that this attribute would be utilized so the generating application can determine the color of this text. If this attribute is omitted, then a value of 0 or false is implied.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    history (Add Hyperlink to Page History)
                </td>
                <td>
                    Specifies whether to add this URI to the history when navigating to it. This allows for the viewing of this presentation without the storing of history information on the viewing machine. If this attribute is omitted, then a value of 1 or true is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    id (Drawing Object Hyperlink Target)</br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the relationship id that when looked up in this slides relationship file contains the target of this hyperlink. This attribute cannot be omitted.</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1).
                </td>
            </tr>
            <tr>
                <td>
                    invalidUrl (Invalid URL)
                </td>
                <td>
                    Specifies the URL when it has been determined by the generating application that the URL is invalid. That is the generating application can still store the URL but it is known that this URL is not correct.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    tgtFrame (Target Frame)
                </td>
                <td>
                    Specifies the target frame that is to be used when opening this hyperlink. When the hyperlink is activated this attribute is used to determine if a new window is launched for viewing or if an existing one can be used. If this attribute is omitted, than a new window is opened.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
            <tr>
                <td>
                    tooltip (Hyperlink Tooltip)
                </td>
                <td>
                    Specifies the tooltip that should be displayed when the hyperlink text is hovered over with the mouse. If this attribute is omitted, than the hyperlink text itself can be displayed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Hyperlink) is located in §A.4.1. end note]

### 20.1.2.2.24 ln (大纲)

=== "中文"

    此元素指定可应用于许多不同对象（例如形状和文本）的轮廓样式。 该线允许指定许多不同类型的轮廓，包括甚至线虚线和斜角。

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
                    algn (笔画对齐)
                </td>
                <td>
                    指定用于下划线描边的对齐方式. </br></br>
                    该属性的可能值由 ST_PenAlignment 简单类型定义 (§20.1.10.39).
                </td>
            </tr>
            <tr>
                <td>
                    cap (线端盖类型)
                </td>
                <td>
                    指定应用于该行的结束大写。 [注：上限类型的示例有圆形、扁平等。尾注] 如果省略此属性，则假定值为 square . </br></br>
                    该属性的可能值由 ST_LineCap 简单类型定义 (§20.1.10.31).
                </td>
            </tr>
            <tr>
                <td>
                    cmpd (复合线型)
                </td>
                <td>
                    指定用于下划线描边的复合线类型。 如果省略此属性，则假定值为 sng. </br></br>
                    该属性的可能值由 ST_CompoundLine 简单类型定义 (§20.1.10.15).
                </td>
            </tr>
            <tr>
                <td>
                    w (线宽)
                </td>
                <td>
                    指定用于下划线描边的宽度。 如果省略该属性，则假定值为 0. </br></br>
                    该属性的可能值由 ST_LineWidth 简单类型定义 (§20.1.10.35).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_LineProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **ln (Outline)**

    This element specifies an outline style that can be applied to a number of different objects such as shapes and text. The line allows for the specifying of many different types of outlines including even line dashes and bevels.

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
                    algn (Stroke Alignment)
                </td>
                <td>
                    Specifies the alignment to be used for the underline stroke. </br></br>
                    The possible values for this attribute are defined by the ST_PenAlignment simple type (§20.1.10.39).
                </td>
            </tr>
            <tr>
                <td>
                    cap (Line Ending Cap Type)
                </td>
                <td>
                    Specifies the ending caps that should be used for this line. [Note: Examples of cap types are rounded, flat, etc. end note] If this attribute is omitted, than a value of square is assumed. </br></br>
                    The possible values for this attribute are defined by the ST_LineCap simple type (§20.1.10.31).
                </td>
            </tr>
            <tr>
                <td>
                    cmpd (Compound Line Type)
                </td>
                <td>
                    Specifies the compound line type to be used for the underline stroke. If this attribute is omitted, then a value of sng is assumed. </br></br>
                    The possible values for this attribute are defined by the ST_CompoundLine simple type (§20.1.10.15).
                </td>
            </tr>
            <tr>
                <td>
                    w (Line Width)
                </td>
                <td>
                    Specifies the width to be used for the underline stroke. If this attribute is omitted, then a value of 0 is assumed. </br></br>
                    The possible values for this attribute are defined by the ST_LineWidth simple type (§20.1.10.35).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_LineProperties) is located in §A.4.1. end note]

### 20.1.2.2.25 nvCxnSpPr (连接形状的非视觉属性)

=== "中文"

    该元素指定连接形状的所有非视觉属性。 该元素是与连接形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响连接形状外观的附加信息。

    [Note: 该元素内容模型 (CT_GvmlConnectorNonVisual) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **nvCxnSpPr (Non-Visual Properties for a Connection Shape)**

    This element specifies all non-visual properties for a connection shape. This element is a container for the nonvisual identification properties, shape properties and application properties that are to be associated with a connection shape. This allows for additional information that does not affect the appearance of the connection shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlConnectorNonVisual) is located in §A.4.1. end note]

### 20.1.2.2.26 nvGraphicFramePr (图形框架的非视觉属性)

=== "中文"

    该元素指定图形框架的所有非视觉属性。 该元素是与图形框架关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响图形框架的外观的附加信息。
    
    [Note: 该元素内容模型 (CT_GvmlGraphicFrameNonVisual) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **nvGraphicFramePr (Non-Visual Properties for a Graphic Frame)**

    This element specifies all non-visual properties for a graphic frame. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a graphic frame. This allows for additional information that does not affect the appearance of the graphic frame to be stored.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlGraphicFrameNonVisual) is located in §A.4.1. end note]

### 20.1.2.2.27 nvGrpSpPr (组合形状的非视觉属性)

=== "中文"

    该元素指定组形状的所有非视觉属性。 该元素是与组形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响组形状外观的附加信息。

    [Note: 该元素内容模型 (CT_GvmlGroupShapeNonVisual) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **nvGrpSpPr (Non-Visual Properties for a Group Shape)**

    This element specifies all non-visual properties for a group shape. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a group shape. This allows for additional information that does not affect the appearance of the group shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlGroupShapeNonVisual) is located in §A.4.1. end note]

### 20.1.2.2.28 nvPicPr (图片的非视觉属性)

=== "中文"

    该元素指定图片的所有非视觉属性。 该元素是与图片关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响图片外观的附加信息。
    !!! info "Example"

        考虑以下PresentationML。

        ```xml
        <p:pic>
            …
            <p:nvPicPr>
                …
            </p:nvPicPr>
            …
        </p:pic>
        ```

    [Note: 该元素内容模型 (CT_GvmlPictureNonVisual) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **nvPicPr (Non-Visual Properties for a Picture)**

    This element specifies all non-visual properties for a picture. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a picture. This allows for additional information that does not affect the appearance of the picture to be stored.

    !!! info "Example"

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

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlPictureNonVisual) is located in §A.4.1. end note]

### 20.1.2.2.29 nvSpPr (形状的非视觉属性)

=== "中文"

    该元素指定形状的所有非视觉属性。 该元素是与形状关联的非视觉识别属性、形状属性和应用程序属性的容器。 这允许存储不影响形状外观的附加信息。

    [Note: 该元素内容模型 (CT_GvmlShapeNonVisual) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **nvSpPr (Non-Visual Properties for a Shape)**

    This element specifies all non-visual properties for a shape. This element is a container for the non-visual identification properties, shape properties and application properties that are to be associated with a shape. This allows for additional information that does not affect the appearance of the shape to be stored.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlShapeNonVisual) is located in §A.4.1. end note]

### 20.1.2.2.30 pic (图片)

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

    [Note: 该元素内容模型 (CT_GvmlPicture) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

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

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlPicture) is located in §A.4.1. end note]

### 20.1.2.2.31 picLocks (图片锁)

=== "中文"

    该元素指定图形框架的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改。

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
                    noAdjustHandles(禁止显示调整手柄)
                </td>
                <td>
                    指定生成应用程序不应显示相应连接形状的调整手柄。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (禁止箭头更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的箭头。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (禁止形状类型更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状类型。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noCrop (禁止裁减变化)
                </td>
                <td>
                    指定生成应用程序不应允许裁剪相应的图片。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(禁止形状点编辑)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状点。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状组合)
                </td>
                <td>
                    指定生成应用程序不应允许对相应连接形状进行形状分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止形状移动)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的位置更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的尺寸。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (禁止形状旋转)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的形状旋转更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定生成应用程序不应允许选择相应的连接形状。 这还意味着，如果指定了此属性，则无法选择附加到此连接形状的图片、形状或文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
        </tbody>
    </table>

=== "英文"

    **picLocks (Picture Locks)**

    This element specifies all locking properties for a graphic frame. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noAdjustHandles(Disallow Showing Adjust Handles)
                </td>
                <td>
                    Specifies that the generating application should not show adjust handles for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (Disallow Arrowhead Changes)
                </td>
                <td>
                    Specifies that the generating application should not allow arrowhead changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (Disallow Shape Type Change)
                </td>
                <td>
                    Specifies that the generating application should not allow shape type changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noCrop (Disallow Crop Changes)
                </td>
                <td>
                    Specifies that the generating application should not allow cropping for the corresponding picture. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(Disallow Shape Point Editing)
                </td>
                <td>
                    Specifies that the generating application should not allow shape point changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the generating application should not allow shape grouping for the corresponding connection shape. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Shape Movement)
                </td>
                <td>
                    Specifies that the generating application should not allow position changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resize)
                </td>
                <td>
                    Specifies that the generating application should not allow size changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (Disallow Shape Rotation)
                </td>
                <td>
                    Specifies that the generating application should not allow shape rotation changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of the corresponding connection shape. That means also that no picture, shapes or text attached to this connection shape can be selected if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

### 20.1.2.2.32 snd (超链接声音)

=== "中文"

    该元素指定激活文档中的超链接时要播放的声音。 该声音是从父超链接元素中指定的。

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
                    embed (嵌入音频文件关系 ID) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    指定嵌入音频文件的标识信息。 该属性用于指定本地驻留在文件内的对象的位置. [Note: §15.2.2. 中提供了建议的音频类型列表  end note]</br></br>
                    该属性的可能值由 ST_RelationshipId 简单类型定义 (§22.8.2.1)
                </td>
            </tr>
            <tr>
                <td>
                    name (声音名称)
                </td>
                <td>
                    指定相应声音的原始名称或给定的短名称。 如果用户需要在 UI 中的其他声音中识别该声音，则可以通过为附加声音提供人类可读的名称来区分该声音与其他声音.</br></br>
                    该属性的可能值由 W3C XML Schema string 类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_EmbeddedWAVAudioFile) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **snd (Hyperlink Sound)**

    This element specifies a sound to be played when a hyperlink within the document is activated. This sound is specified from within the parent hyperlink element.

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
                    embed (Embedded Audio File Relationship ID) </br></br>
                    Namespace: http://purl.oclc.org/ooxml/officeDocument/relationships
                </td>
                <td>
                    Specifies the identification information for an embedded audio file. This attribute is used to specify the location of an object that resides locally within the file. [Note: A list of suggested audio types is provided in §15.2.2. end note]</br></br>
                    The possible values for this attribute are defined by the ST_RelationshipId simple type (§22.8.2.1)
                </td>
            </tr>
            <tr>
                <td>
                    name (Sound Name)
                </td>
                <td>
                    Specifies the original name or given short name for the corresponding sound. This is used to distinguish this sound from others by providing a human readable name for the attached sound should the user need to identify the sound among others within the UI.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema string datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_EmbeddedWAVAudioFile) is located in §A.4.1. end note]

### 20.1.2.2.33 sp (形状)

=== "中文"

    该元素指定单个形状的存在。 形状可以是使用 DrawingML 框架定义的预设几何图形或自定义几何图形。 除了几何形状之外，每个形状还可以附加视觉和非视觉属性。 文本和相应的样式信息也可以附加到形状。 该形状与形状树或组形状元素中的所有其他形状一起指定。

    [Note: 形状是在幻灯片上指定文本的首选机制. end note]

    [Note: 该元素内容模型 (CT_GvmlShape) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **sp (Shape)**

    This element specifies the existence of a single shape. A shape can either be a preset or a custom geometry, defined using the DrawingML framework. In addition to a geometry each shape can have both visual and nonvisual properties attached. Text and corresponding styling information can also be attached to a shape. This shape is specified along with all other shapes within either the shape tree or group shape elements.

    [Note: Shapes are the preferred mechanism for specifying text on a slide. end note]

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlShape) is located in §A.4.1. end note]

### 20.1.2.2.34 spLocks (形状锁)

=== "中文"

    该元素指定形状的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改.

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
                    noAdjustHandles(禁止显示调整手柄)
                </td>
                <td>
                    指定生成应用程序不应显示相应连接形状的调整手柄。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (禁止箭头更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的箭头。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (禁止形状类型更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状类型。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(禁止形状点编辑)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状点。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状组合)
                </td>
                <td>
                    指定生成应用程序不应允许对相应连接形状进行形状分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止形状移动)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的位置更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的尺寸。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (禁止形状旋转)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的形状旋转更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定生成应用程序不应允许选择相应的连接形状。 这还意味着，如果指定了此属性，则无法选择附加到此连接形状的图片、形状或文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
            <tr>
                <td>
                    noTextEdit(禁止形状文本编辑)
                </td>
                <td>
                    指定生成应用程序不应允许编辑相应形状的形状文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema 布尔数据类型.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ShapeLocking) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **spLocks (Shape Locks)**

    This element specifies all locking properties for a shape. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noAdjustHandles(Disallow Showing Adjust Handles)
                </td>
                <td>
                    Specifies that the generating application should not show adjust handles for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (Disallow Arrowhead Changes)
                </td>
                <td>
                    Specifies that the generating application should not allow arrowhead changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (Disallow Shape Type Change)
                </td>
                <td>
                    Specifies that the generating application should not allow shape type changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(Disallow Shape Point Editing)
                </td>
                <td>
                    Specifies that the generating application should not allow shape point changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the generating application should not allow shape grouping for the corresponding connection shape. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Shape Movement)
                </td>
                <td>
                    Specifies that the generating application should not allow position changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resize)
                </td>
                <td>
                    Specifies that the generating application should not allow size changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (Disallow Shape Rotation)
                </td>
                <td>
                    Specifies that the generating application should not allow shape rotation changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of the corresponding connection shape. That means also that no picture, shapes or text attached to this connection shape can be selected if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noTextEdit(Disallow Shape Text Editing)
                </td>
                <td>
                    Specifies that the generating application should not allow editing of the shape text for the corresponding shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeLocking) is located in §A.4.1. end note]

### 20.1.2.2.35 spPr (形状属性)

=== "中文"

    该元素指定可应用于形状的视觉形状属性.

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
                    指定应仅使用黑色和白色来渲染组形状. </br></br>
                    也就是说，在渲染相应形状时，组形状的颜色信息应转换为黑色或白色.</br></br>
                    渲染该图像时不使用灰色，仅使用纯黑和纯白.</br></br>
                    [Note: 这并不意味着组形状本身仅存储有黑白颜色信息。 该属性设置渲染时形状使用的渲染模式. end note]</br></br>
                    该属性的可能值由 ST_BlackWhiteMode 简单类型定义 (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ShapeProperties) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **spPr (Shape Properties)**

    This element specifies the visual shape properties that can be applied to a shape.

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
                    Specifies that the group shape should be rendered using only black and white coloring. </br></br>
                    That is the coloring information for the group shape should be converted to either black or white when rendering the corresponding shapes.</br></br>
                    No gray is to be used in rendering this image, only stark black and stark white.</br></br>
                    [Note: This does not mean that the group shapes themselves are stored with only black and white color information. This attribute instead sets the rendering mode that the shapes use when rendering. end note]</br></br>
                    The possible values for this attribute are defined by the ST_BlackWhiteMode simple type (§20.1.10.10).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeProperties) is located in §A.4.1. end note]

### 20.1.2.2.36 stCxn (连接开始)

=== "中文"

    该元素指定应由相应连接器形状建立的起始连接。 这将连接器的头部连接到第一个形状。

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
                    id (标识符)
                </td>
                <td>
                    指定要进行最终连接的形状的 id.</br></br>
                    该属性的可能值由 ST_DrawingElementId 简单类型定义 (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    idx (索引)
                </td>
                <td>
                    指定最终连接形状的连接站点表的索引。 即一个形状上有很多连接点，需要指定对应的连接器形状应该连接到哪个连接点.</br></br>
                    该属性的可能值由 W3C XML Schema unsignedInt 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Connection) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **stCxn (Connection Start)**

    This element specifies the starting connection that should be made by the corresponding connector shape. This connects the head of the connector to the first shape.

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
                    id (Identifier)
                </td>
                <td>
                    Specifies the id of the shape to make the final connection to.</br></br>
                    该属性的可能值由 ST_DrawingElementId 简单类型定义 (§20.1.10.21).
                </td>
            </tr>
            <tr>
                <td>
                    idx (Index)
                </td>
                <td>
                    Specifies the index into the connection site table of the final connection shape. That is there are many connection sites on a shape and it shall be specified which connection site the corresponding connector shape should connect to.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Connection) is located in §A.4.1. end note]

### 20.1.2.2.37 style (形状样式)

=== "中文"

    该元素指定形状的样式信息.

    [Note: 该元素内容模型 (CT_ShapeStyle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **style (Shape Style)**

    This element specifies the style information for a shape.

    [Note: The W3C XML Schema definition of this element’s content model (CT_ShapeStyle) is located in §A.4.1. end note]

### 20.1.2.2.38 sx (水平比例)

=== "中文"

    该元素指定在缩放计算中使用的水平比例.

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
                    d (分母/Denominator)
                </td>
                <td>
                    指定方程中使用的分母.</br></br>
                    该属性的可能值由 W3C XML Schema long 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    n (分子/Numerator)
                </td>
                <td>
                    指定方程中使用的分子.</br></br>
                    该属性的可能值由 W3C XML Schema long 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Ratio) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **sx (Horizontal Ratio)**

    This element specifies the horizontal ratio for use within a scaling calculation.

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
                    d (Denominator)
                </td>
                <td>
                    Specifies the denominator to be used within the equation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema long datatype.
                </td>
            </tr>
            <tr>
                <td>
                    n (Numerator)
                </td>
                <td>
                    Specifies the numerator to be used within the equation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema long datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Ratio) is located in §A.4.1. end note]

### 20.1.2.2.39 sy (垂直比例)

=== "中文"

    该元素指定在缩放计算中使用的垂直比例.

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
                    d (Denominator)
                </td>
                <td>
                    指定方程中使用的分母.</br></br>
                    该属性的可能值由 W3C XML Schema long 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    n (Numerator)
                </td>
                <td>
                    指定方程中使用的分子.</br></br>
                    该属性的可能值由 W3C XML Schema long 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Ratio) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **sy (Vertical Ratio)**

    This element specifies the vertical ratio for use within a scaling calculation.

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
                    d (Denominator)
                </td>
                <td>
                    Specifies the denominator to be used within the equation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema long datatype.
                </td>
            </tr>
            <tr>
                <td>
                    n (Numerator)
                </td>
                <td>
                    Specifies the numerator to be used within the equation.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema long datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Ratio) is located in §A.4.1. end note]

### 20.1.2.2.40 txBody (形状文本正文)

=== "中文"

    该元素指定相应形状中是否存在要包含的文本。 所有可见文本和可见文本相关属性都包含在此元素内。 可以有多个段落，段落内可以有多个文本段.

    [Note: 该元素内容模型 (CT_TextBody) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **txBody (Shape Text Body)**

    This element specifies the existence of text to be contained within the corresponding shape. All visible text and visible text related properties are contained within this element. There can be multiple paragraphs and within paragraphs multiple runs of text.

    [Note: The W3C XML Schema definition of this element’s content model (CT_TextBody) is located in §A.4.1. end note]

### 20.1.2.2.41 txSp (文本形状)

=== "中文"

    该元素指定父形状中是否存在文本形状。 此文本形状专门用于显示文本，因为它仅具有与文本相关的子元素.

    [Note: 该元素内容模型 (CT_GvmlTextShape) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **txSp (Text Shape)**

    This element specifies the existence of a text shape within a parent shape. This text shape is specifically used for displaying text as it has only text related child elements.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlTextShape) is located in §A.4.1. end note]

### 20.1.2.2.42 useSpRect (使用形状文本矩形)

=== "中文"

    此元素指定父形状中的文本矩形应用于此文本形状。 如果指定了此属性，则文本矩形或文本边界框（也称为文本边界框）应与此文本形状所在的父形状的文本边界框具有相同的尺寸.

    [Note: 该元素内容模型 (CT_GvmlUseShapeRectangle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **useSpRect (Use Shape Text Rectangle)**

    This element specifies that the text rectangle from the parent shape should be used for this text shape. If this attribute is specified then the text rectangle, or text bounding box as it is also called should have the same dimensions as the text bounding box of the parent shape within which this text shape resides.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GvmlUseShapeRectangle) is located in §A.4.1. end note]

### 20.1.2.2.43 cpLocks (内容部分锁)

=== "中文"

    该元素指定内容部分的所有锁定属性。 这些属性向生成应用程序通知先前已锁定的特定属性，因此不应更改.

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
                    noAdjustHandles(禁止显示调整手柄)
                </td>
                <td>
                    指定生成应用程序不应显示相应连接形状的调整手柄。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (禁止箭头更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的箭头。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (禁止更改宽高比)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的纵横比。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (禁止形状类型更改)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状类型。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(禁止形状点编辑)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的形状点。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (禁止形状分组)
                </td>
                <td>
                    指定生成应用程序不应允许对相应连接形状进行形状分组。 也就是说，它不能与其他形状组合以形成一组形状。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (禁止形状移动)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的位置更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (禁止调整形状大小)
                </td>
                <td>
                    指定生成应用程序不应允许更改相应连接形状的尺寸。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (禁止形状旋转)
                </td>
                <td>
                    指定生成应用程序不应允许相应连接形状的形状旋转更改。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (禁止选择形状)
                </td>
                <td>
                    指定生成应用程序不应允许选择相应的连接形状。 这还意味着，如果指定了此属性，则无法选择附加到此连接形状的图片、形状或文本。 如果未指定此属性，则假定值为 false.</br></br>
                    该属性的可能值由 W3C XML Schema boolean 数据类型定义.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ContentPartLocking) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **cpLocks (Content Part Locks)**

    This element specifies all locking properties for a content part. These properties inform the generating application about specific properties that have been previously locked and thus should not be changed.

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
                    noAdjustHandles(Disallow Showing Adjust Handles)
                </td>
                <td>
                    Specifies that the generating application should not show adjust handles for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeArrowheads (Disallow Arrowhead Changes)
                </td>
                <td>
                    Specifies that the generating application should not allow arrowhead changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeAspect (Disallow Aspect Ratio Change)
                </td>
                <td>
                    Specifies that the generating application should not allow aspect ratio changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noChangeShapeType (Disallow Shape Type Change)
                </td>
                <td>
                    Specifies that the generating application should not allow shape type changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noEditPoints(Disallow Shape Point Editing)
                </td>
                <td>
                    Specifies that the generating application should not allow shape point changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noGrp (Disallow Shape Grouping)
                </td>
                <td>
                    Specifies that the generating application should not allow shape grouping for the corresponding connection shape. That is it cannot be combined within other shapes to form a group of shapes. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noMove (Disallow Shape Movement)
                </td>
                <td>
                    Specifies that the generating application should not allow position changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noResize (Disallow Shape Resize)
                </td>
                <td>
                    Specifies that the generating application should not allow size changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noRot (Disallow Shape Rotation)
                </td>
                <td>
                    Specifies that the generating application should not allow shape rotation changes for the corresponding connection shape. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
            <tr>
                <td>
                    noSelect (Disallow Shape Selection)
                </td>
                <td>
                    Specifies that the generating application should not allow selecting of the corresponding connection shape. That means also that no picture, shapes or text attached to this connection shape can be selected if this attribute has been specified. If this attribute is not specified, then a value of false is assumed.</br></br>
                    The possible values for this attribute are defined by the W3C XML Schema boolean datatype.
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ContentPartLocking) is located in §A.4.1. end note]

## 20.1.2.3 颜色

=== "中文"

    鉴于在 DrawingML 基础知识中拥有自己的部分，颜色是 DrawingML 框架的一个组成部分。 几乎每个对象都使用颜色来帮助描述其在屏幕上渲染时的外观。 由于并非每个生成应用程序都希望以相同的方式表示颜色，因此可以通过多种不同的方式指定颜色。

=== "英文"

    **Colors**

    Given its own section within DrawingML Basics, colors are an integral part of the DrawingML framework. Colors are used in virtually every object to help describe it's appearance when it is rendered on the screen. Since not every generating application wishes to represent color in the same manner, it is possible to specify color in a number of different ways. 

### 20.1.2.3.1 alpha (阿尔法)

=== "中文"

    该元素使用特定的不透明度指定其输入颜色，但其颜色保持不变。

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
                    val (Value)
                </td>
                <td>
                    指定以百分比值表示的不透明度.</br></br>
                    [Example: 下面代表了 50% 不透明的绿色实心填充</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alpha val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_PositiveFixedPercentage 简单类型定义 (§20.1.10.45).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositiveFixedPercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **alpha (Alpha)**

    This element specifies its input color with the specific opacity, but with its color unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the opacity as expressed by a percentage value.</br></br>
                    [Example: The following represents a green solid fill which is 50% opaque</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alpha val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_PositiveFixedPercentage simple type (§20.1.10.45).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PositiveFixedPercentage) is located in §A.4.1. end note]

### 20.1.2.3.2 alphaMod (阿尔法调制)

=== "中文"

    该元素指定其输入颜色的或多或少不透明的版本。 Alpha 调制永远不会将 Alpha 值增加到超过 100%。 200% Alpha 调制使输入颜色的不透明度是以前的两倍。 50% Alpha 调制使输入颜色的不透明度减半。

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
                    val (值)
                </td>
                <td>
                    指定不透明度，以相对于输入颜色的百分比表示.</br></br>
                    [Example: 下面代表了 50% 不透明的绿色实心填充</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alphaMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_PositivePercentage 简单类型定义 (§20.1.10.46).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositivePercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **alphaMod (Alpha Modulation)**

    This element specifies a more or less opaque version of its input color. An alpha modulate never increases the alpha beyond 100%. A 200% alpha modulate makes an input color twice as opaque as before. A 50% alpha modulate makes an input color half as opaque as before.

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
                    val (Value)
                </td>
                <td>
                    Specifies the opacity as expressed by a percentage relative to the input color.</br></br>
                    [Example: The following represents a green solid fill which is 50% opaque</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alphaMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_PositivePercentage simple type (§20.1.10.46).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PositivePercentage) is located in §A.4.1. end note]

### 20.1.2.3.3 alphaOff (阿尔法偏移)

=== "中文"

    该元素指定其输入颜色的或多或少不透明的版本。 按指定的百分比偏移量增加或减少输入 Alpha 百分比。 10% 的 Alpha 偏移会将 50% 的不透明度增加到 60%。 -10% Alpha 偏移会将 50% 的不透明度降低到 40%。 转换后的 alpha 值限制在 0 到 100% 的范围内。 对 100% 不透明对象增加 10% Alpha 偏移仍会导致 100% 不透明度。

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
                    val (Value)
                </td>
                <td>
                    指定不透明度，以相对于输入颜色的偏移增加或减少的百分比表示。 增加永远不会将不透明度增加到超过 100%，减少永远不会将不透明度降低到 0% 以下。</br></br>
                    [Example: 下面代表了 90% 不透明的绿色实心填充</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alphaOff val="-10%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_FixedPercentage 简单类型定义 (§20.1.10.24).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_FixedPercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **alphaOff (Alpha Offset)**

    This element specifies a more or less opaque version of its input color. Increases or decreases the input alpha percentage by the specified percentage offset. A 10% alpha offset increases a 50% opacity to 60%. A -10% alpha offset decreases a 50% opacity to 40%. The transformed alpha values are limited to a range of 0 to 100%. A 10% alpha offset increase to a 100% opaque object still results in 100% opacity.

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
                    val (Value)
                </td>
                <td>
                    Specifies the opacity as expressed by a percentage offset increase or decrease to theinput color. Increases never  increase the opacity beyond 100%, decreases never decrease the opacity below 0%.</br></br>
                    [Example: The following represents a green solid fill which is 90% opaque</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:alphaOff val="-10%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_FixedPercentage simple type (§20.1.10.24).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_FixedPercentage) is located in §A.4.1. end note]

### 20.1.2.3.4 blue (蓝色的)

=== "中文"

    该元素指定具有特定蓝色分量的输入颜色，但红色和绿色分量不变。

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
                    val (值)
                </td>
                <td>
                    指定蓝色分量的值。 分配的值指定为百分比，0% 表示最小蓝色，100% 表示最大蓝色.</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, FF, FF)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:blue val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **blue (Blue)**

    This element specifies the input color with the specific blue component, but with the red and green color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the value of the blue component. The assigned value is specified as a percentage with 0% indicating minimal blue and 100% indicating maximum blue.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, FF, FF) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:blue val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.5 blueMod (蓝色调制)

=== "中文"

    该元素指定输入颜色，其蓝色分量按给定百分比调制。 50% 蓝色调制将蓝色分量减少一半。 200% 蓝色调制使蓝色分量加倍。

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
                    val (值)
                </td>
                <td>
                    指定蓝色分量，以相对于输入颜色分量的百分比表示。 增加永远不会将蓝色分量增加到超过 100%，减少永远不会将蓝色分量减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, 00, FF) 更改为值 RRGGBB= (00, 00, 80)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:blueMod val=""50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **blueMod (Blue Modulation)**

    This element specifies the input color with its blue component modulated by the given percentage. A 50% blue modulate reduces the blue component by half. A 200% blue modulate doubles the blue component.

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
                    val (Value)
                </td>
                <td>
                    Specifies the blue component as expressed by a percentage relative to the input color component. Increases never increase the blue component beyond 100%, decreases never decrease the blue component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, 00, FF) to value RRGGBB= (00, 00, 80) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:blueMod val=""50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.6 blueOff (蓝色偏移)

=== "中文"

    该元素指定输入颜色，其蓝色分量发生偏移，但红色和绿色分量不变。

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
                    val (值)
                </td>
                <td>
                    指定蓝色分量，以相对于输入颜色分量的偏移增加或减少的百分比表示。 增加永远不会将蓝色分量增加到超过 100%，减少永远不会将蓝色分量减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, 00, FF) 更改为值 RRGGBB= (00, 00, CC) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:blueOff val=""-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **blueOff (Blue Offset)**

    This element specifies the input color with its blue component shifted, but with its red and green color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the blue component as expressed by a percentage offset increase or decrease to the input color component. Increases never increase the blue component beyond 100%, decreases never decrease the blue component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, 00, FF) to value RRGGBB= (00, 00, CC)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:blueOff val=""-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.7 comp (补充)

=== "中文"

    该元素指定渲染的颜色应该是其输入颜色的补色，补色是这样定义的。 如果两种颜色混合时产生灰色阴影，则称为互补色。 例如，红色的补色是 RGB (255, 0, 0)，而青色是 RGB (0, 255, 255)。

    原色和间色通常以这种方式配对：

    - 红色和青色（其中青色是绿色和蓝色的混合物）
    - 绿色和洋红色（其中洋红色是红色和蓝色的混合物）
    - 蓝色和黄色（其中黄色是红色和绿色的混合物）

    !!! info "Example"

        下式表示红色的补码：

        ```xml
        <a:solidFill>
            <a:srgbClr val="FF0000">
                <a:comp/>
            </a:srgbClr>
        </a:solidFill>
        ```

    [Note: 该元素内容模型 (CT_ComplementTransform) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **comp (Complement)**

    This element specifies that the color rendered should be the complement of its input color with the complement being defined as such. Two colors are called complementary if, when mixed they produce a shade of grey. For instance, the complement of red which is RGB (255, 0, 0) is cyan which is RGB (0, 255, 255).

    Primary colors and secondary colors are typically paired in this way:

    - red and cyan (where cyan is the mixture of green and blue)
    - green and magenta (where magenta is the mixture of red and blue)
    - blue and yellow (where yellow is the mixture of red and green)

    !!! info "Example"

        The following represents the complement of red:

        ```xml
        <a:solidFill>
            <a:srgbClr val="FF0000">
                <a:comp/>
            </a:srgbClr>
        </a:solidFill>
        ```

    [Note: The W3C XML Schema definition of this element’s content model (CT_ComplementTransform) is located in §A.4.1. end note]

### 20.1.2.3.8 gamma (伽玛)

=== "中文"

    该元素指定生成应用程序渲染的输出颜色应该是输入颜色的 sRGB gamma 偏移。
    
    [Note: 该元素内容模型 (CT_GammaTransform) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **gamma (Gamma)**

    This element specifies that the output color rendered by the generating application should be the sRGB gamma shift of the input color.
    
    [Note: The W3C XML Schema definition of this element’s content model (CT_GammaTransform) is located in §A.4.1. end note]

### 20.1.2.3.9 gray (灰色)

=== "中文"

    该元素指定其输入颜色的灰度，考虑红、绿、蓝原色的相对强度.

    [Note: 该元素内容模型 (CT_GrayscaleTransform) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **gray (Gray)**

    This element specifies a grayscale of its input color, taking into relative intensities of the red, green, and blue primaries.

    [Note: The W3C XML Schema definition of this element’s content model (CT_GrayscaleTransform) is located in §A.4.1. end note]

### 20.1.2.3.10 green (绿色)

=== "中文"

    该元素指定具有指定绿色分量的输入颜色，但其红色和蓝色分量不变。

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
                    val (Value)
                </td>
                <td>
                    指定绿色分量的值。 分配的值指定为百分比，0% 表示最小绿色，100% 表示最大绿色.</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, 00, FF) 更改为值 RRGGBB= (00, FF, FF) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:green val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **green (Green)**

    This elements specifies the input color with the specified green component, but with its red and blue color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the value of the green component. The assigned value is specified as a percentage with 0% indicating minimal green and 100% indicating maximum green.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, 00, FF) to value RRGGBB= (00, FF, FF)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:green val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.11 greenMod (绿色调制)

=== "中文"

    该元素指定输入颜色，其绿色分量按给定百分比调制。 50% 绿色调制将绿色成分减少一半。 200% 绿色调制使绿色成分加倍.

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
                    val (值)
                </td>
                <td>
                    指定绿色分量，以相对于输入颜色分量的百分比表示。 增加绝不会将绿色成分增加到超过 100%，减少绝不会将绿色成分减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, 80, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:greenMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **greenMod (Green Modulation)**

    This element specifies the input color with its green component modulated by the given percentage. A 50% green modulate reduces the green component by half. A 200% green modulate doubles the green component.

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
                    val (Value)
                </td>
                <td>
                    Specifies the green component as expressed by a percentage relative to the input color component. Increases never increase the green component beyond 100%, decreases never decrease the green component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, 80, 00)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:greenMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.12 greenOff (绿色偏移)

=== "中文"

    该元素指定输入颜色，其绿色分量发生偏移，但红色和蓝色分量不变。

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
                    val (值)
                </td>
                <td>
                    指定绿色分量，以相对于输入颜色分量的偏移增加或减少的百分比表示。 增加绝不会将绿色成分增加到超过 100%，减少绝不会将绿色成分减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, CC, 00)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:greenOff val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **greenOff (Green Offset)**

    This element specifies the input color with its green component shifted, but with its red and blue color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the green component as expressed by a percentage offset increase or decrease to the input color component. Increases never increase the green component beyond 100%, decreases never decrease the green component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, CC, 00)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="0000FF">`</br>
                    `        <a:greenOff val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.13 hslClr (色相、饱和度、亮度颜色模型)

=== "中文"

    该元素使用 HSL 颜色模型指定颜色。 假设感知伽玛值为 2.2。

    色调是指颜色的主波长，饱和度是指其色调的纯度，亮度是指其明度或暗度。
    
    与所有颜色一样，使用 HSL 颜色模型定义的颜色可以应用颜色变换。

    !!! info "Example"

        具有 RGB 值 RRGGBB = (00, 00, 80) 的蓝色调当于

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
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
                    hue (色调/Hue) 
                </td>
                <td>
                    指定描述波长的角度值.</br></br>
                    该属性的可能值由 ST_PositiveFixedAngle 简单类型定义 (§20.1.10.44).
                </td>
            </tr>
            <tr>
                <td>
                    lum (亮度/Luminance)
                </td>
                <td>
                    指定指颜色的明度或暗度的亮度。 以百分比表示，0% 表示最大暗（黑色），100% 表示最大白色.</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    sat (饱和度/Saturation)
                </td>
                <td>
                    指定指色调纯度的饱和度。 以百分比表示，0% 指灰色，100% 指最纯粹的色调。</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_HslColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **hslClr (Hue, Saturation, Luminance Color Model)**

    This element specifies a color using the HSL color model. A perceptual gamma of 2.2 is assumed.

    Hue refers to the dominant wavelength of color, saturation refers to the purity of its hue, and luminance refers to its lightness or darkness.
    
    As with all colors, colors defined with the HSL color model can have color transforms applied to it.

    !!! info "Example"

        The color blue having RGB value RRGGBB = (00, 00, 80) is equivalent to

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
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
                    hue (Hue) 
                </td>
                <td>
                    Specifies the angular value describing the wavelength.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveFixedAngle simple type (§20.1.10.44).
                </td>
            </tr>
            <tr>
                <td>
                    lum (Luminance)
                </td>
                <td>
                    Specifies the luminance referring to the lightness or darkness of the color. Expressed as a percentage with 0% referring to maximal dark (black) and 100% referring to maximal white.</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    sat (Saturation)
                </td>
                <td>
                    Specifies the saturation referring to the purity of the hue. Expressed as a percentage with 0% referring to grey, 100% referring to the purest form of the hue.</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_HslColor) is located in §A.4.1. end note]

### 20.1.2.3.14 hue (色相)

=== "中文"

    该元素指定具有指定色调的输入颜色，但其饱和度和亮度不变。

    !!! info "Example"

        以下两个实体填充是等效的。

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="0" sat="100%" lum="50%">
                <a:hue val="14400000"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (值)
                </td>
                <td>
                    指定要与输入颜色的色调分量一起使用的实际角度值.</br></br>
                    该属性的可能值由 ST_PositiveFixedAngle 简单类型定义 (§20.1.10.44).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositiveFixedAngle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **hue (Hue)**

    This element specifies the input color with the specified hue, but with its saturation and luminance unchanged.

    !!! info "Example"

        The following two solid fills are equivalent.

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="0" sat="100%" lum="50%">
                <a:hue val="14400000"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    Specifies the actual angle value to be used with the input color's hue component.</br></br>
                    The possible values for this attribute are defined by the ST_PositiveFixedAngle simple type (§20.1.10.44).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PositiveFixedAngle) is located in §A.4.1. end note]

### 20.1.2.3.15 hueMod (色相调制)

=== "中文"

    该元素指定输入颜色，其色调按给定百分比调制。 50% 色调调制会将角度色调值减少一半。 200% 色调调制使角度色调值加倍。

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
                    val (值)
                </td>
                <td>
                    指定色调，以相对于输入颜色的百分比表示.</br></br>
                    [Example: 以下操作将填充颜色从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB = (FF, FF, 00)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:hueMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_PositivePercentage 简单类型定义 (§20.1.10.46).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositivePercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **hueMod (Hue Modulate)**

    This element specifies the input color with its hue modulated by the given percentage. A 50% hue modulate decreases the angular hue value by half. A 200% hue modulate doubles the angular hue value.

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
                    val (Value)
                </td>
                <td>
                    Specifies the hue as expressed by a percentage relative to the input color.</br></br>
                    [Example: The following manipulates the fill color from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB = (FF, FF, 00)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:hueMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_PositivePercentage simple type (§20.1.10.46).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PositivePercentage) is located in §A.4.1. end note]

### 20.1.2.3.16 hueOff (色相偏移)

=== "中文"

    该元素指定输入颜色，其色调发生变化，但饱和度和亮度不变。

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
                    val (Value)
                </td>
                <td>
                    指定平移的实际角度值。 平移的结果应在 0 到 360 度之间。 导致角度值小于 0 的平移将被视为 0。导致角度值大于 360 的平移将被视为 360.</br></br>
                    [Example: 下面将色调角度值增加10度.</br></br>
                    `<a:solidFill>`</br>
                    `    <a:hslClr hue="0" sat="100%" lum="50%"/>`</br>
                    `    <a:hueOff val="600000"/>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Angle 简单类型定义 (§20.1.10.3).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Angle) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **hueOff (Hue Offset)**

    This element specifies the input color with its hue shifted, but with its saturation and luminance unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the actual angular value of the shift. The result of the shift shall be between 0 and 360 degrees. Shifts resulting in angular values less than 0 are treated as 0. Shifts resulting in angular values greater than 360 are treated as 360.</br></br>
                    [Example: The following increases the hue angular value by 10 degrees.</br></br>
                    `<a:solidFill>`</br>
                    `    <a:hslClr hue="0" sat="100%" lum="50%"/>`</br>
                    `    <a:hueOff val="600000"/>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Angle simple type (§20.1.10.3).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Angle) is located in §A.4.1. end note]

### 20.1.2.3.17 inv (逆向)

=== "中文"

    该元素指定其输入颜色的反色。

    !!! info "Example":

        红色 (1, 0, 0) 的逆色是青色 (0, 1, 1 )。

        以下代表青色，红色的反色：

        ```xml
        <a:solidFill>
            <a:srgbClr val="FF0000">
                <a:inv/>
            </a:srgbClr>
        </a:solidFill>
        ```

    [Note: 该元素内容模型 (CT_InverseTransform) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **inv (Inverse)**

    This element specifies the inverse of its input color. 

    !!! info "Example":

        The inverse of red (1, 0, 0) is cyan (0, 1, 1 ).

        The following represents cyan, the inverse of red: 

        ```xml
        <a:solidFill>
            <a:srgbClr val="FF0000">
                <a:inv/>
            </a:srgbClr>
        </a:solidFill>
        ```

    [Note: The W3C XML Schema definition of this element’s content model (CT_InverseTransform) is located in §A.4.1. end note]

### 20.1.2.3.18 invGamma (逆向伽玛)

=== "中文"

    该元素指定生成应用程序渲染的输出颜色应该是输入颜色的逆 sRGB gamma 偏移。

    [Note: 该元素内容模型 (CT_InverseGammaTransform) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **invGamma (Inverse Gamma)**

    This element specifies that the output color rendered by the generating application should be the inverse sRGB gamma shift of the input color.

    [Note: The W3C XML Schema definition of this element’s content model (CT_InverseGammaTransform) is located in §A.4.1. end note]

### 20.1.2.3.19 lum (亮度)

=== "中文"

    该元素指定具有指定亮度的输入颜色，但其色调和饱和度保持不变。 通常亮度值落在 [0%, 100%] 范围内。

    !!! info "example"

        以下两个实体填充是等效的：

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="0%">
                <a:lum val="50%"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (值)
                </td>
                <td>
                    指定亮度值。 分配的值指定为百分比，0% 表示最小亮度，100% 表示最大亮度。</br></br>
                    [Example：以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, 66, 00)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lum val="20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **lum (Luminance)**

    This element specifies the input color with the specified luminance, but with its hue and saturation unchanged. Typically luminance values fall in the range [0%, 100%].

    !!! info "example"

        The following two solid fills are equivalent: 

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="0%">
                <a:lum val="50%"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    Specifies the value of the luminance. The assigned value is specified as a percentage with 0% indicating minimal luminance and 100% indicating maximum luminance.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, 66, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lum val="20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.20 lumMod (亮度调制)

=== "中文"

    该元素指定输入颜色，其亮度按给定百分比调制。 50% 亮度调制会将亮度降低一半。 200% 亮度调制使亮度加倍。

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
                    val (Value)
                </td>
                <td>
                    指定以相对于输入颜色的百分比表示的亮度。 增加绝不会将亮度增加到超过 100%，减少绝不会将亮度降低到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, 75, 00)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lumMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **lumMod (Luminance Modulation)**

    This element specifies the input color with its luminance modulated by the given percentage. A 50% luminance modulate reduces the luminance by half. A 200% luminance modulate doubles the luminance.

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
                    val (Value)
                </td>
                <td>
                    Specifies the luminance as expressed by a percentage relative to the input color. Increases never increase the luminance beyond 100%, decreases never decrease the luminance below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, 75, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lumMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.21 lumOff (亮度偏移)

=== "中文"

    该元素指定亮度发生变化但色调和饱和度不变的输入颜色。

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
                    val (Value)
                </td>
                <td>
                    指定以相对于输入颜色的偏移增加或减少的百分比表示的亮度。 增加绝不会将亮度增加到超过 100%，减少绝不会将亮度降低到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, 99, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lumOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **lumOff (Luminance Offset)**

    This element specifies the input color with its luminance shifted, but with its hue and saturation unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the luminance as expressed by a percentage offset increase or decrease to the input color. Increases never increase the luminance beyond 100%, decreases never decrease the luminance below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, 99, 00)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:lumOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.22 prstClr (预设颜色)

=== "中文"

    该元素指定绑定到预定义颜色集合之一的颜色。

    !!! info "Example"

        下面定义了绑定到“黑色(black)”预设颜色的实心填充。

        ```xml
        <a:solidFill>
            <a:prstClr val="black">
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    指定实际预设颜色值.</br></br>
                    该属性的可能值由 ST_PresetColorVal 简单类型定义 (§20.1.10.48).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PresetColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **prstClr (Preset Color)**

    This element specifies a color which is bound to one of a predefined collection of colors.

    !!! info "Example"

        The following defines a solid fill bound to the "black" preset color.

        ```xml
        <a:solidFill>
            <a:prstClr val="black">
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    Specifies the actual preset color value.</br></br>
                    The possible values for this attribute are defined by the ST_PresetColorVal simple type (§20.1.10.48).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PresetColor) is located in §A.4.1. end note]

### 20.1.2.3.23 red (红色)

=== "中文"

    该元素指定具有指定红色分量的输入颜色，但其绿色和蓝色分量不变。

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
                    val (值)
                </td>
                <td>
                    指定红色分量的值。 分配的值指定为百分比，其中 0% 表示最小红色，100% 表示最大红色.</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (FF, FF, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:red val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **red (Red)**

    This element specifies the input color with the specified red component, but with its green and blue color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the value of the red component. The assigned value is specified as a percentage with 0% indicating minimal red and 100% indicating maximum red.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (FF, FF, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:red val="100%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.24 redMod (红色调制)

=== "中文"

    该元素指定输入颜色，其红色分量按给定百分比调制。 50% 红色调制将红色分量减少一半。 200% 红色调制使红色分量加倍。

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
                    val (Value)
                </td>
                <td>
                    指定红色分量，以相对于输入颜色分量的百分比表示。 增加永远不会将红色分量增加到超过 100%，减少永远不会将红色分量减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (FF, 00, 00) 更改为值 RRGGBB= (80, 00, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:redMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **redMod (Red Modulation)**

    This element specifies the input color with its red component modulated by the given percentage. A 50% red modulate reduces the red component by half. A 200% red modulate doubles the red component.

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
                    val (Value)
                </td>
                <td>
                    Specifies the red component as expressed by a percentage relative to the input color component. Increases never increase the red component beyond 100%, decreases never decrease the red component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (FF, 00, 00) to value RRGGBB= (80, 00, 00)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:redMod val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.25 redOff (红色偏移)

=== "中文"

    该元素指定输入颜色，其红色分量发生偏移，但绿色和蓝色分量不变。

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
                    val (Value)
                </td>
                <td>
                    指定红色分量，以相对于输入颜色分量的偏移增加或减少的百分比表示。 增加永远不会将红色分量增加到超过 100%，减少永远不会将红色分量减少到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (FF, 00, 00) 更改为值 RRGGBB= (CC, 00, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:redOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **redOff (Red Offset)**

    This element specifies the input color with its red component shifted, but with its green and blue color components unchanged.

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
                    val (Value)
                </td>
                <td>
                    Specifies the red component as expressed by a percentage offset increase or decrease to the input color component. Increases never increase the red component beyond 100%, decreases never decrease the red component below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (FF, 00, 00) to value RRGGBB= (CC, 00, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:redOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.26 sat (饱和度)

=== "中文"

    该元素指定具有指定饱和度的输入颜色，但其色调和亮度不变。 通常饱和度值落在 [0%, 100%] 范围内。

    !!! info "Example"

        以下两个实体填充是等效的：

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="14400000" sat="0%" lum="50%">
            <a:sat val="100000"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    指定饱和度的值。 分配的值指定为百分比，其中 0% 表示最小饱和度，100% 表示最大饱和度。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (40, C0, 40) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:sat val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **sat (Saturation)**

    This element specifies the input color with the specified saturation, but with its hue and luminance unchanged. Typically saturation values fall in the range [0%, 100%].

    !!! info "Example"

        The following two solid fills are equivalent: 

        ```xml
        <a:solidFill>
            <a:hslClr hue="14400000" sat="100%" lum="50%">
        </a:solidFill>
        <a:solidFill>
            <a:hslClr hue="14400000" sat="0%" lum="50%">
            <a:sat val="100000"/>
            <a:hslClr/>
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    Specifies the value of the saturation. The assigned value is specified as a percentage with 0% indicating minimal saturation and 100% indicating maximum saturation.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (40, C0, 40)  </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:sat val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.27 satMod (饱和度调制)

=== "中文"

    该元素指定输入颜色，其饱和度按给定百分比调制。 50% 饱和度调制可将饱和度降低一半。 200% 饱和度调制使饱和度加倍。

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
                    val (Value)
                </td>
                <td>
                    指定饱和度，以相对于输入颜色的百分比表示。 增加永远不会将饱和度增加到超过 100%，减少永远不会将饱和度降低到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (66, 99, 66) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:satMod val="20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **satMod (Saturation Modulation)**

    This element specifies the input color with its saturation modulated by the given percentage. A 50% saturation modulate reduces the saturation by half. A 200% saturation modulate doubles the saturation.

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
                    val (Value)
                </td>
                <td>
                    Specifies the saturation as expressed by a percentage relative to the input color. Increases never increase the saturation beyond 100%, decreases never decrease the saturation below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (66, 99, 66) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:satMod val="20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.28 satOff (饱和度偏移)

=== "中文"

    该元素指定饱和度发生变化但色调和亮度不变的输入颜色。 20% 饱和度偏移 10% 会产生 30% 饱和度。

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
                    val (值)
                </td>
                <td>
                    指定饱和度，以输入颜色的偏移增加或减少百分比表示。 增加永远不会将饱和度增加到超过 100%，减少永远不会将饱和度降低到 0% 以下。</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (19, E5, 19)</br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:satOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_Percentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **satOff (Saturation Offset)**

    This element specifies the input color with its saturation shifted, but with its hue and luminance unchanged. A 10% offset to 20% saturation yields 30% saturation.

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
                    val (Value)
                </td>
                <td>
                    Specifies the saturation as expressed by a percentage offset increase or decrease to the input color. Increases never increase the saturation beyond 100%, decreases never decrease the saturation below 0%.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00)to value RRGGBB= (19, E5, 19) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:satOff val="-20%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_Percentage) is located in §A.4.1. end note]

### 20.1.2.3.29 schemeClr (方案颜色)

=== "中文"

    该元素指定与用户主题绑定的颜色。 与定义颜色的所有元素一样，可以将颜色变换列表应用于定义的基色。

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
                    val (值)
                </td>
                <td>
                    指定所需的方案.</br></br>
                    [Example: 以下代表与“lt1”主题颜色绑定的颜色</br></br>
                    `<a:solidFill>`</br>
                    `    <a:schemeClr val="lt1"/>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_SchemeColorVal 简单类型定义 (§20.1.10.54).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SchemeColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **schemeClr (Scheme Color)**

    This element specifies a color bound to a user's theme. As with all elements which define a color, it is possible to apply a list of color transforms to the base color defined.

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
                    val (Value)
                </td>
                <td>
                    Specifies the desired scheme.</br></br>
                    [Example: The following represents a color bound to the "lt1" theme color</br></br>
                    `<a:solidFill>`</br>
                    `    <a:schemeClr val="lt1"/>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_SchemeColorVal simple type (§20.1.10.54).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SchemeColor) is located in §A.4.1. end note]

### 20.1.2.3.30 scrgbClr (RGB 颜色模型 - 百分比变体)

=== "中文"

    该元素使用红、绿、蓝 RGB 颜色模型指定颜色。 每个分量（红色、绿色和蓝色）均表示为 0% 到 100% 的百分比。 假设线性伽马为 1.0。

    指定红色级别，以相对于输入颜色的偏移增加或减少百分比表示。

    !!! info "Example"

        以下代表相同颜色

        ```xml
        <a:solidFill>
            <a:scrgbClr r="50%" g="50%" b="50%"/>
        </a:solidFill>
        <a:solidFill>
            <a:srgbClr val="BCBCBC"/>
        </a:solidFill>
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
                    b (Blue)
                </td>
                <td>
                    指定蓝色的百分比.</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    g (Green) 
                </td>
                <td>
                    指定绿色的百分比.</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    r (Red)
                </td>
                <td>
                    指定红色的百分比.</br></br>
                    该属性的可能值由 ST_Percentage 简单类型定义 (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_ScRgbColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **scrgbClr (RGB Color Model - Percentage Variant)**

    This element specifies a color using the red, green, blue RGB color model. Each component, red, green, and blue is expressed as a percentage from 0% to 100%. A linear gamma of 1.0 is assumed.

    Specifies the level of red as expressed by a percentage offset increase or decrease relative to the input color.

    !!! info "Example"

        The following represent the same color

        ```xml
        <a:solidFill>
            <a:scrgbClr r="50%" g="50%" b="50%"/>
        </a:solidFill>
        <a:solidFill>
            <a:srgbClr val="BCBCBC"/>
        </a:solidFill>
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
                    b (Blue)
                </td>
                <td>
                    Specifies the percentage of blue.</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    g (Green) 
                </td>
                <td>
                    Specifies the percentage of green.</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
            <tr>
                <td>
                    r (Red)
                </td>
                <td>
                    Specifies the percentage of red.</br></br>
                    The possible values for this attribute are defined by the ST_Percentage simple type (§20.1.10.40).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_ScRgbColor) is located in §A.4.1. end note]

### 20.1.2.3.31 shade (阴影)

=== "中文"

    该元素指定其输入颜色的较暗版本。 10% 阴影是输入颜色的 10% 与 90% 黑色的组合。

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
                    val (Value)
                </td>
                <td>
                    指定以百分比值表示的阴影.</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (00, BC, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:shade val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_PositiveFixedPercentage 简单类型定义 (§20.1.10.45).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositiveFixedPercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **shade (Shade)**

    This element specifies a darker version of its input color. A 10% shade is 10% of the input color combined with 90% black.

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
                    val (Value)
                </td>
                <td>
                    Specifies the shade as expressed by a percentage value.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (00, BC, 00) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="FF0000">`</br>
                    `        <a:shade val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_PositiveFixedPercentage simple type (§20.1.10.45).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositiveFixedPercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

### 20.1.2.3.32 srgbClr (RGB 颜色模型 - 十六进制变体)

=== "中文"

    该元素使用红、绿、蓝 RGB 颜色模型指定颜色。 红色、绿色和蓝色表示为十六进制数字序列 RRGGBB。 使用 2.2 的感知伽玛。

    指定红色级别，以相对于输入颜色的偏移增加或减少百分比表示。

    !!! info "Example":

        以下代表相同颜色

        ```xml
        <a:solidFill>
            <a:scrgbClr r="50%" g="50%" b="50%"/>
        </a:solidFill>
        <a:solidFill>
            <a:srgbClr val="BCBCBC"/>
        </a:solidFill>
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
                    val (值)
                </td>
                <td>
                    实际颜色值。 表示为十六进制数字 RRGGBB 序列。</br></br>
                    该属性的可能值由 ST_HexColorRGB 简单类型定义 (§22.9.2.5).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SRgbColor) is located in §A.4.1. end note]

=== "英文"

    **srgbClr (RGB Color Model - Hex Variant)**

    This element specifies a color using the red, green, blue RGB color model. Red, green, and blue is expressed as sequence of hex digits, RRGGBB. A perceptual gamma of 2.2 is used.

    Specifies the level of red as expressed by a percentage offset increase or decrease relative to the input color.

    !!! info "Example":

        The following represent the same color

        ```xml
        <a:solidFill>
            <a:scrgbClr r="50%" g="50%" b="50%"/>
        </a:solidFill>
        <a:solidFill>
            <a:srgbClr val="BCBCBC"/>
        </a:solidFill>
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
                    val (Value)
                </td>
                <td>
                    The actual color value. Expressed as a sequence of hex digits RRGGBB.</br></br>
                    The possible values for this attribute are defined by the ST_HexColorRGB simple type (§22.9.2.5).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SRgbColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

### 20.1.2.3.33 sysClr (系统颜色)

=== "中文"

    该元素指定绑定到预定义操作系统元素的颜色。

    !!! info "Example":

        以下表示用于在窗口中显示文本的默认颜色。

        ```xml
        <a:solidFill>
            <a:sysClr val="windowText"/>
        </a:solidFill>
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
                    lastClr (最后的颜色)
                </td>
                <td>
                    指定生成应用程序最后计算的颜色值</br></br>
                    该属性的可能值由 ST_HexColorRGB 简单类型定义 (§22.9.2.5).
                </td>
            </tr>
            <tr>
                <td>
                    val (值)
                </td>
                <td>
                    指定系统颜色值.</br></br>
                    该属性的可能值由 ST_SystemColorVal 简单类型定义 (§20.1.10.58).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_SystemColor) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **sysClr (System Color)**

    This element specifies a color bound to predefined operating system elements.

    !!! info "Example":

        The following represents the default color used for displaying text in a window.

        ```xml
        <a:solidFill>
            <a:sysClr val="windowText"/>
        </a:solidFill>
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
                    lastClr (Last Color)
                </td>
                <td>
                    Specifies the color value that was last computed by the generating application</br></br>
                    The possible values for this attribute are defined by the ST_HexColorRGB simple type (§22.9.2.5).
                </td>
            </tr>
            <tr>
                <td>
                    val (Value)
                </td>
                <td>
                    Specifies the system color value.</br></br>
                    The possible values for this attribute are defined by the ST_SystemColorVal simple type (§20.1.10.58).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_SystemColor) is located in §A.4.1. end note]

### 20.1.2.3.34 tint (色调)

=== "中文"

    该元素指定其输入颜色的较浅版本。 10% 色调是输入颜色的 10% 与 90% 白色调结合。

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
                    val (Value)
                </td>
                <td>
                    指定以百分比值表示的色调.</br></br>
                    [Example: 以下操作将填充从 RGB 值 RRGGBB = (00, FF, 00) 更改为值 RRGGBB= (BC, FF, BC) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:tint val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    该属性的可能值由 ST_PositiveFixedPercentage 简单类型 (§20.1.10.45) 定义。
                </td>
            </tr>
        </tbody>
    </table>

    [Note: 该元素内容模型 (CT_PositiveFixedPercentage) 的 W3C XML 架构定义位于 §A.4.1 中。 end note]

=== "英文"

    **tint (Tint)**

    This element specifies a lighter version of its input color. A 10% tint is 10% of the input color combined with 90% white.

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
                    val (Value)
                </td>
                <td>
                    Specifies the tint as expressed by a percentage value.</br></br>
                    [Example: The following manipulates the fill from having RGB value RRGGBB = (00, FF, 00) to value RRGGBB= (BC, FF, BC) </br></br>
                    `<a:solidFill>`</br>
                    `    <a:srgbClr val="00FF00">`</br>
                    `        <a:tint val="50%"/>`</br>
                    `    </a:srgbClr>`</br>
                    `</a:solidFill>`</br></br>
                    end example]</br></br>
                    The possible values for this attribute are defined by the ST_PositiveFixedPercentage simple type (§20.1.10.45).
                </td>
            </tr>
        </tbody>
    </table>

    [Note: The W3C XML Schema definition of this element’s content model (CT_PositiveFixedPercentage) is located in §A.4.1. end note]
